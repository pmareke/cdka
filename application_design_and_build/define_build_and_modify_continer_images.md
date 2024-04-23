# Define, Build and Modify Container Images

## Image management

    - An image is a package containing Application code, Dependencies and Configuration.
    - Use Dockerfile to create images.
    - Also called OCI (Open Container Initiative) images.

## Managing images with Docker

    - Exam environments are in Linux.
    - `docker image build -t REPO:TAG .`.
    - `docker image ls`.
    - `docker image pull TAG`.
    - Always check the build and pull commands with `ls`.
    - `docker save REPO:TAG --output image.tar`.
    - `docker save REPO:TAG | gzip > image.tar.gz`.
    - It's possible to create an image from a running container:
        - `docker commit CONTAINER REPO:TAG`.
    - `docker image tag OLD_TAG NEW_TAG` to retag an image.
    - `docker image rmi REPO:TAG|IMAGE_ID` to delete an image.

## Managing images with other tools

    - `buildah`:
        - Image management.
        - Creates and manages OCI images.
        - Only does images.
        - Doesn't need a Dockerfile.
        - Commands:
            - `buildah build -t REPO:TAG`.
            - `buildah commit CONTAINER REPO:TAG`.
            - `buildah tag OLD_TAG NEW_TAG` to retag an image.
            - `buildah rmi REPO:TAG|IMAGE_ID`
    - `podman`:
        - Image and Container management.
        - Creates and manages OCI images.
        - Manages entire containers lifecycle.
        - Supports Docker commands.
        - There is NO deamon running.
        - Uses `buildah` to create images.
        - Commands:
            - `podman image build -t REPO:TAG`.
            - `podman commit CONTAINER REPO:TAG`.
            - `podman image tag OLD_TAG NEW_TAG` to retag an image.
            - `podman rmi REPO:TAG|IMAGE_ID`
            - `podman save REPO:TAG | gzip > image.tar.gz`.

## Exam scenarios

- Build an OCI image from a directory in which the Dockerfile is not present.
    - Use the `docker build` command with the `-f` flag.
- Fix an image problem without pushing to the registry.
    - Use the `docker image tag OLD_TAG NEW_TAG`
- Create a tar file.
    - Use the `docker save REPO:TAG --output image.tar`.

## Recap and Test

- Build images from Doclkerfiles.
- Name and tag images.
- Save images as OCI archives.

