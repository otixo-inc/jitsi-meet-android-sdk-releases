# jitsi-meet-android-sdk-releases

Maven repository distribution for Jitsi Meet Android SDK builds from the [otixo-inc/jitsi-meet](https://github.com/otixo-inc/jitsi-meet) fork.

## Usage

### 1. Add the Maven repository

In your project's `build.gradle` (or `settings.gradle` for newer Android projects), add the repository under `repositories`:

```groovy
repositories {
    maven { url "https://github.com/otixo-inc/jitsi-meet-android-sdk-releases/raw/main/releases" }
}
```

### 2. Add the dependency

In your app module's `build.gradle`, add the dependency:

```groovy
dependencies {
    implementation('org.jitsi.react:jitsi-meet-sdk:2.4.0') { transitive = true }
}
```

## Building the Jitsi Fork

### Prerequisites

Make sure the following dependencies are installed:

- [watchman](https://facebook.github.io/watchman/)
- [Node.js](https://nodejs.org/)
- npm

### Set up Android environment

Export the Android SDK path and tools before building:

```bash
export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/platform-tools
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
export PATH=$PATH:$ANDROID_HOME/emulator
```

### Build and publish

1. Set the target SDK version:

```bash
export OVERRIDE_SDK_VERSION=2.4.0
```

2. Run the release script, passing the path to the `releases/` directory of this repository as the destination:

```bash
./android/scripts/release-sdk.sh /path/to/jitsi-meet-android-sdk-releases/releases
```

For example:

```bash
./android/scripts/release-sdk.sh ~/StudioProjects/jitsi-meet-android-sdk-releases/releases
```

The script will build the SDK and output the Maven artifacts directly into the destination directory.

## Contributing

To publish a new SDK version to this distribution:

1. Build the Maven artifacts from the [otixo-inc/jitsi-meet](https://github.com/otixo-inc/jitsi-meet) fork.
2. Create a new branch (e.g. `version-x.y.z`).
3. Add the generated Maven repository artifacts (AAR, POM, and metadata files) under the `releases/` directory.
4. Open a pull request and merge the branch into `main`.

The new version will be available to consumers immediately after the merge.

## About

This repository hosts pre-built AAR artifacts and Maven metadata for the Jitsi Meet Android SDK, built from the custom fork at [otixo-inc/jitsi-meet](https://github.com/otixo-inc/jitsi-meet). It serves as a lightweight Maven repository that can be consumed directly by Android Gradle builds without publishing to a central repository.