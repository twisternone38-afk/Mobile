.github/workflows/android.yml
name: Build Android APK

on:
  workflow_dispatch:
  push:
    branches:
      - main

permissions:
  contents: read

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Download project
        uses: actions/checkout@v4

      - name: Install Java 17
        uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: '17'

      - name: Install Android SDK
        uses: android-actions/setup-android@v3

      - name: Install SDK packages
        run: sdkmanager "platforms;android-35" "build-tools;35.0.0"

      - name: Install Gradle
        uses: gradle/actions/setup-gradle@v4
        with:
          gradle-version: '8.9'

      - name: Build APK
        run: gradle --no-daemon assembleDebug

      - name: Save APK
        uses: actions/upload-artifact@v4
        with:
          name: MobileGameEmulator-APK
          path: app/build/outputs/apk/debug/app-debug.apk
