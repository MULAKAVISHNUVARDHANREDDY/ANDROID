# Android OS
1.What is Android OS?
-
Android is an open-source operating system based on the Linux kernel, designed primarily for touchscreen mobile devices like smartphones and tablets. Developed by Google and maintained via the Android Open Source Project (AOSP), it powers billions of devices worldwide, including wearables, smart TVs, and cars.
1.First commercial release: Android 1.0 (2008)
2.Current version: Android 14 (API 34)
-

## Key Features of Android OS
1. Open-Source Foundation
Source code available under AOSP

Highly customizable by OEMs and developers

2. Linux Kernel-Based
Built on a modified version of the Linux kernel Handles low-level device interactions and system services

3. Android Runtime (ART)
Replaces the older Dalvik VM Uses ahead-of-time (AOT) compilation for better performance

4. Layered Architecture
Applications → Java/Kotlin Framework → ART → Native C/C++ Libraries → Linux Kernel

5. App Ecosystem
Supports millions of apps via Google Play Store Apps built using Java, Kotlin, and Jetpack libraries

6. Customizable UI/UX
OEMs create custom skins (e.g., One UI, OxygenOS, MIUI) Supports widgets, gestures, and dynamic themes

7. Security Features
App sandboxing (each app runs in its own process/UID) SELinux enforcement Regular monthly security patches Verified Boot & Google Play Protect

8. Multi-device Support
Scales across phones, tablets, TVs (Android TV), cars (Android Auto), and wearables (Wear OS)

9. Google Services Integration
Google Mobile Services (GMS): Maps, Gmail, Play Services (optional for OEMs)

10. Extensive Hardware Support
Supports multiple architectures (ARM, ARM64, x86) HAL (Hardware Abstraction Layer) allows interaction with various hardware types

# ANDROID
-----------
Android is a mobile operating system developed by Google, built on top of the Linux kernel. It is used in smartphones, tablets, smart TVs, and other smart devices. Android enhances the base Linux system with a full software stack including the Android Runtime (ART), system services, an application framework, and apps.

Key Android Features:
- Uses a modified Linux kernel
- Uses Bionic C library instead of glibc
- Employs Binder IPC (instead of System V IPC)
- Supports suspend/resume with Wake Locks
- Includes Low Memory Killer for aggressive memory management
- Uses Hardware Abstraction Layer (HAL) to isolate hardware dependencies
- Applications written in Java/Kotlin run on ART

-------------------------------------------
2. LINUX ARCHITECTURE
   
   ![Screenshot 2025-07-03 093438](https://github.com/user-attachments/assets/5f8ec587-7f29-4bfc-b6c6-060d55145d6d)

Linux follows a layered architecture with two main spaces:

A. USER SPACE:
- Applications: Programs like editors, terminals, browsers
- Services: Background daemons (e.g., cron, sshd)
- Libraries: Shared code (e.g., glibc) for system calls
- System Call Interface: Boundary between user space and kernel space

B. KERNEL SPACE:
- Linux Kernel: Controls CPU, memory, processes, I/O, and hardware
- Device Drivers: Interface between hardware and kernel
- Kernel Subsystems: MMU, VM, PM, IPC

Summary: Applications in user space communicate with the kernel using system calls. The kernel manages all the low-level operations.

-------------------------------------------

3. ANDROID ARCHITECTURE

   -Android is built on top of Linux and adds several mobile-specific layers:
   
![Screenshot 2025-07-03 095735](https://github.com/user-attachments/assets/638d7674-d79a-46ae-8b1a-3f58992bee51)



1. Applications
   - User-installed or system apps
2. Android Framework
   - Java APIs: ActivityManager, NotificationManager, etc.
3. Android Runtime (ART)
   - Runs apps written in Java/Kotlin (replaces Dalvik)
4. Native Libraries & Daemons
   - libc, WebKit, SurfaceFlinger, Media Framework
5. Hardware Abstraction Layer (HAL)
   - Interface between hardware drivers and Android system
6. Modified Linux Kernel
   - Base kernel with Android-specific features like Binder, Wake Locks
7. Binder IPC (Inter-Process Communication)
   - Android uses a custom IPC mechanism called Binder, which is built into the kernel.Apps and services use Binder IPC to safely communicate across processes.

🧠 Example:
   - Your messaging app communicates with the Telephony Service (running in System Server) via Binder to send an SMS.

8. Android apps use the framework and Binder IPC to talk to services. HAL allows OEMs to implement hardware features without changing upper layers.
-------------------------------
4. ANDROID BOOT PROCESS
 

The Android boot process includes the following stages:

1. Boot ROM
   - Code embedded in SoC (CPU); loads bootloader

2. Bootloader
   - Initializes hardware; verifies and loads kernel + ramdisk

3. Linux Kernel
   - Starts device drivers, mounts root file system

4. Init Process
   - First user-space process; reads init.rc files
   - Launches daemons and services

5. Zygote
   - Preloads core classes and forks new app processes

6. System Server
   - Starts Android system services: ActivityManager, PackageManager

7. System UI
   - Manages status bar, navigation, lock screen

8. Launcher
   - Displays home screen and app drawer

This layered boot ensures a secure, modular, and fast startup.


