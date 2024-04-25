# Utilize Persistent and Ephemeral Volumes

## Persistent and Ephemeral Volumes

- `StoreClass` kind
    - Has a provisioner.
    - Has a reclaim policy.
    - Has a storage class name.
    - Has a volume binding mode.
        - `waitForFirstConsumer` - volume is created only when a Pod using the PersistentVolumeClaim is created.
- `PersistentVolumeClaim` kind
    - Requests a PersistentVolume.
    - Has a storage class name.
    - Has a volume name and size.
    - Has a volume access mode.
        - `ReadWriteOnce` - volume can be mounted as read-write by a single node.
        - `ReadOnlyMany` - volume can be mounted as read-only by many nodes.
        - `ReadWriteMany` - volume can be mounted as read-write by many nodes.
- We can create a `Volumen` using a `Pod` with a volumen attach to the PVC. 

## Exam Scenarios

- Fix an existing app.
    - The PVC was not correct.
    - Use `emptyDir` ephemeral volume instead of a persistent one.
