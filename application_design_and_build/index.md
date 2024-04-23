# Application Design and Build

## Define, Build and Modify Container Images

### Image management

    - An image is a package containing Application code, Dependencies and Configuration.
    - Use Dockerfile to create images.
    - Also called OCI (Open Container Initiative) images.

### Managing images with Docker

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
    - `docker image rm REPO:TAG|IMAGE_ID` to delete an image.

### Managing images with other tools

### Exam scenarios

### Recap and Test

