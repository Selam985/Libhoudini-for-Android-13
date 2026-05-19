# Houdini v145 for Android 13 (x86_64)

This repository contains **Intel Houdini** libraries surgically extracted from the **ChromeOS v145 (Brya)** image. It is used to run ARM applications (Translation Layer) on x86_64 based Android systems.

## 🛠 Technical Details
- **Source:** ChromeOS Brya v145 (16552.53.0)
- **Android Version:** Android 13 (Tiramisu / API 33)
- **Processor Support:** Intel (12th, 13th and 14th Gen optimized) and AMD x86_64 processors.
- **Architecture:** x86_64 host -> ARM64 & ARM translation.

## 📁 Folder Structure
- `/bin`: Executable Houdini files.
- `/lib` & `/lib64`: Main translation libraries (`libhoudini.so`).
- `/arm` & `/arm64`: ARM compatibility libraries.

## 🚀 Installation
To download the ready-made package, download the `.zip` file from the **Releases** section on the right. Place it in your AOSP build or your device's `/vendor` directory as appropriate.

> **Note:** For educational purposes only.
