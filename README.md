# Docker Image with Android SDK + Flutter Beta

Based on openjdk:8-slim and the [Álvaro's Alpine Android](https://github.com/alvr/alpine-android).

### Bitbucket Pipelines
Here's an example `bitbucket-pipelines.yml`:

```
image: thenameisflic/flutter-beta-android-sdk:v1

pipelines:
  default:
    - step:
        caches:
          - gradle
          - gradlewrapper
          - flutter
        script:
          - echo "Building APK..."
          - flutter channel beta
          - flutter upgrade
          - yes | flutter doctor --android-licenses
          - flutter doctor
          - flutter -v build apk

definitions:
  caches:
    gradlewrapper: ~/.gradle/wrapper
    flutter: /opt/flutter
```