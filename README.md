# Docker Android Builder

Common Android application building environment with Docker.

## Usage

Download an image for example `docker pull jerray/gradle4.1-jdk8-27-27.0.0`.

Enter your project source root directory. Run following command to start testing.

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
