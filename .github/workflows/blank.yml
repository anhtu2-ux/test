name: Build iOS/macOS Dylib

on:
  push:
    branches: [ "main" ]
  workflow_dispatch: # Cho phép bấm nút chạy thủ công

jobs:
  build:
    runs-on: macos-latest # Sử dụng máy chủ macOS của GitHub

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Compile dylib
        run: |
          # Biên dịch file C thành dylib (dành cho macOS/iOS Simulator)
          clang -dynamiclib -o libexample.dylib example.c
          
          # Nếu muốn biên dịch dylib dành cho iOS Arm64 (Thiết bị thật / Jailbreak):
          # xcrun -sdk iphoneos clang -dynamiclib -arch arm64 -o libexample_ios.dylib example.c

      - name: Upload Dylib Artifact
        uses: actions/upload-artifact@v4
        with:
          name: compiled-dylib
          path: "*.dylib"
