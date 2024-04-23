# Understand Jobs and Cron Jobs

- Kubernetes API Resources.
- Bookmarks:
    - https://kubernetes.io/docs/concepts/workloads/controllers/job/
    - https://kubernetes.io/docs/reference/kubernetes-api/workload-resources/job-v1/
    - https://kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/
    - https://kubernetes.io/docs/reference/kubernetes-api/workload-resources/cron-job-v1/

## Jobs

- Sets a number of pods to completion.
- Managed by the Job Controller.
    - Provides out of the box retries, restarts, clean and auto kill long-run jobs.
- Can run pods in parallel.
- `kind: Job`.

## Cron Jobs

- Much like Jobs but run on a schedule.
- `kind: CronJob`.

## Working with Jobs

- `kubectl apply -f <job-file>`.
- `kubectl get jobs`.
- `kubectl describe job <job-name>`.
- `kubectl logs <pod-name>`.
- `kubectl delete job <job-name>`.
    - Delete the job removes the pods too.
- `restartPolicy: Never` prevent the failed jobs to be cleaned.
- `activeDeadlineSeconds: 100` to limit the job run time.
- `ttlSecondsAfterFinished: 100` to clean the job after completion.

## Working with Cron Jobs

- The timezone comes from the Kubernetes API server.
- CronJobs check every 10 seconds for the next schedule.
- The controller tries with a max of 100 tasks.
- `startingDeadlineSeconds: 120`:
    - Looks for the missing tasks in the last two minutes.
    - It's also the time to wait for the job to start.
    - A value less than 10 some jobs will be ignored.
- `concurrencyPolicy: Allow` to run multiple jobs at the same time.
    - The other values are `Forbid` and `Replace`.
- `successfulJobsHistoryLimit: 3` to keep the history of successful jobs.
- `failedJobsHistoryLimit: 3` to keep the history of failed jobs.

## Exam Scenarios

- Migrate a Job to a CronJob.
    - Change the `kind` to `CronJob`.
    - Add the `schedule` field.
    - Add the `jobTemplate.spec` field with the spec content.
- Fix a CronJob without errors and missing some jobs.
    - Change the `startingDeadlineSeconds` to be higher than 10 seconds.
- Update an existing failing in an specific k8s namespace Job to have access to the logs.
    - Change the context `kubectl config set-context --current --namespace=NAMESPACE`.
    - Change `restartPolicy` to `Never`.

## Recap and Test

- Ensure that one or more pods complete successfully.
