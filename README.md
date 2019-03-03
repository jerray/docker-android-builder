# Docker Android Builder

![Docker Pulls](https://img.shields.io/docker/pulls/jerray/android-builder.svg)

Common Android application building environment with Docker.

## Usage

Download an image. Tag `gradle4.1-jdk8-27-27.0.0` means this image contains
gradle 4.1, JDK 8, Android version 27, Android build tools version 27.0.0.

```sh
docker pull jerray/android-builder:gradle4.1-jdk8-27-27.0.0
```

Chnage current directory to your project source root directory.
Run following command to start testing.

```sh
docker run --rm -it \
  -v $PWD:/src \
  -v $HOME/.gradle:/home/gradle/.gradle \
  jerray/android-builder:gradle4.1-jdk8-27-27.0.0 \
  gradle test
```

Replace `gradle test` command to any other you want gradle to run.
For example I use `gradle assembleRelease` command to build the `apk` release package.

Parameter `-v $HOME/.gradle:/home/gradle/.gradle` is used to share gradle cache between
host machine and docker container. Removing it will results in gradle downloading depedencies
every time.

## More tool versions

Feel free to make pull requests to add different tool versions. I will merge the pull requests
and make the image available on DockerHub as soon as possible.
