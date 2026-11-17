name: Build APK

on:
  workflow_dispatch:
  push:
    branches: [ main, master ]

jobs:
  build:
    runs-on: ubuntu-24.04
    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-java@v5
        with:
          distribution: temurin
          java-version: 17

      - name: Descomprimir proyecto
        run: unzip -q -o CarMusic-project.zip

      - name: Compilar los dos APK
        working-directory: CarMusic
        run: |
          chmod +x ./gradlew
          ./gradlew assembleDebug --stacktrace

      - uses: actions/upload-artifact@v4
        with:
          name: CarMusic
          path: CarMusic/carmusic/build/outputs/apk/debug/CarMusic.apk

      - uses: actions/upload-artifact@v4
        with:
          name: CarMusic-Companion
          path: CarMusic/companion/build/outputs/apk/debug/CarMusic-Companion.apk
