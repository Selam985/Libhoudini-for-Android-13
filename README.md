# Houdini v145 for Android 13 (x86_64)

This repository contains **Intel Houdini** libraries surgically extracted from the **ChromeOS v145 (Brya)** image. It is used to run ARM applications (Translation Layer) on x86_64 based Android systems.

## 🛠 Technical Details
- **Source:** ChromeOS Brya v145 (16552.53.0)
- **Android Version:** Android 13 (Tiramisu / API 33) (like BlissOS or Waydroid)
- **Processor Support:** Intel and AMD x86_64 processors.
- **Architecture:** ARM to X86_64

## 📁 Folder Structure
- `/bin`: Executable Houdini files.
- `/lib` & `/lib64`: Main translation libraries (`libhoudini.so`).
- `/arm` & `/arm64`: ARM compatibility libraries.

## 🚀 Installation
If you are installing on a pre-built system:

***Move the files under bin to system/bin***
Set permissions:

chmod 755 /system/bin/houdini

chmod 755 /system/bin/houdini64

chown root:shell /system/bin/houdini*

***Move the .so files from the lib and lib64 folders to system/lib and system/lib64***
Set Permissions:

chmod 644 /system/lib/libhoudini.so

chmod 644 /system/lib64/libhoudini.so

chown root:root /system/lib*/libhoudini.so

***You need to move everything inside the arm and arm64 folders to system/lib/arm and system/lib64/arm64 respectively.***

**To do this, while in the libhoudini folder, type the following:**

cp -r arm/* system/lib/arm

cp -r arm64/* system/lib64/arm64

Permissions:


chown -R root:root /system/lib/arm

chown -R root:root /system/lib64/arm64

chmod 755 /system/lib/arm

chmod 755 /system/lib64/arm64

chmod 644 /system/lib/arm/*.so

chmod 644 /system/lib64/arm64/*.so

***Go to the location of the files in the binfmt_misc folder and type the following commands:***

echo ':arm64_exe:M::\x7f\x45\x4c\x46\x02\x01\x01\x00\x00\x00\x00\x00\x00\x00\x00\x00\x02\x00\xb7::/system/bin/houdini64:P' > /proc/sys/fs/binfmt_misc/register

echo ':arm64_dyn:M::\x7f\x45\x4c\x46\x02\x01\x01\x00\x00\x00\x00\x00\x00\x00\x00\x00\x03\x00\xb7::/system/bin/houdini64:P' > /proc/sys/fs/binfmt_misc/register

echo ':arm_dyn:M::\x7f\x45\x4c\x46\x01\x01\x01\x00\x00\x00\x00\x00\x00\x00\x00\x00\x03\x00\x28::/system/bin/houdini:P' > /proc/sys/fs/binfmt_misc/register

echo ':arm_exe:M::\x7f\x45\x4c\x46\x01\x01\x01\x00\x00\x00\x00\x00\x00\x00\x00\x00\x02\x00\x28::/system/bin/houdini:P' > /proc/sys/fs/binfmt_misc/register

