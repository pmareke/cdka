# Multi-container Pod Design Patterns

## Understanding Multi-container Pods

- Containers must run inside pods.
- Multiple containers can be inside the same Pod.
- Each container should have only one responsibility.
- Ambassador Pattern:
    - A sidecar container runs along side with the main one.
- Adapter Pattern:
    - A sidecar container runs with the main one adapting the main container outputs.
- Init containers:
    - Run before the main container starts.
    - Great to check another container dependecies.
    - Main container only starts after the init container finishes.
    - There is a specific field for init containers in the pod spec: `spec.initContainers`.-

## Working with Multi-container Pods

- Multiple containers inside the `spec`.
- Init container inside the `initContainers`.
- `kubectl logs POD_ID -c CONTAINER_NAME`

## Exam Scenarios

- Change the context `kubectl config set-context --current --namespace=NAMESPACE`.
- Update and existing app adding an init container.
- Update and existing adding a sidecar.

## Recap and Test

- Multiple containers can live inside the same Pod.
- All the containers share the Pod specs (network, storage, etc).
- Sidecars:
    - Run alongside the main container.
    - Augment the main container.
    - Separation of concerns.
- Init containers:
    - Run before the main container starts.
    - Main container only starts after the init container finishes.
    - Good for preparing the environment.

