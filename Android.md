# **Android OS**
1.What is Android OS?
```c
Android is an open-source operating system based on the Linux kernel, designed primarily for touchscreen mobile devices like smartphones and tablets.
Developed by Google and maintained via the Android Open Source Project (AOSP).
It powers billions of devices worldwide, including wearables, smart TVs, and cars.
1.First commercial release: Android 1.0 (2008)
2.Current version: Android 14 (API 34).
```

### **Key Features of Android OS**
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

# **ANDROID**
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
- Java
	Was the first main language for Android apps
	Apps run on Android Runtime (ART)
	Many Android features are still written in Java
- Kotlin
	In 2017, Google made Kotlin the recommended language for Android
	It's modern, safe, and shorter than Java
	You can mix Kotlin and Java in the same project
- C/C++
	Used for low-level tasks or when high speed is needed (like in games)
	Developers use the Android NDK to write code in C/C++.
-------------------------------------------
# **Android vs Linux Architecture**

| Layer                        | Android                                                       | Linux                                                      |
|-----------------------------|----------------------------------------------------------------|-------------------------------------------------------------|
| **Applications**            | User-installed apps (`.apk`)                                  | CLI tools, GUI apps (e.g., GNOME, KDE)                      |
| **Framework / APIs**        | Android Framework (ActivityManager, ContentProvider, etc.)    | No centralized framework, depends on distro and libraries   |
| **Runtime / VM**            | ART (Android Runtime) or older Dalvik VM                      | No VM by default, apps run natively or with interpreter     |
| **System Services**         | SystemServer services (e.g., PowerManager, WindowManager)     | System daemons (e.g., cron, dbus, udev)                     |
| **Hardware Abstraction Layer** | HAL modules for camera, GPS, Bluetooth, etc.              | Direct driver access or via user libraries                  |
| **Native Libraries / Daemons** | libc, OpenGL, SurfaceFlinger, media codecs, etc.          | glibc, libX11, PulseAudio, etc.                             |
| **IPC Mechanism**           | Binder IPC (Android-specific kernel driver)                   | System V IPC, POSIX message queues, pipes                   |
| **C Library**               | Bionic C                                                      | glibc, musl                                                 |
| **Kernel**                  | Modified Linux kernel (with Binder, wakelocks, LMK, etc.)     | Vanilla Linux kernel                                        |

# **LINUX ARCHITECTURE**
- Linux follows a layered architecture with two main spaces:
		![Screenshot 2025-07-03 093438](https://github.com/user-attachments/assets/5f8ec587-7f29-4bfc-b6c6-060d55145d6d)
  
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

# **ANDROID ARCHITECTURE**

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
# **ANDROID BOOT PROCESS**
- The Android startup process involves a sequence of steps, starting with the bootloader and culminating in a "boot complete" broadcast, enabling Android applications to run.
Here's a detailed breakdown of the process:

   	![chart2](https://github.com/user-attachments/assets/77df3146-5643-4ba1-9392-6480932158a5)


The Android boot process includes the following stages:

1. Boot ROM
   - Code embedded in SoC (CPU); loads bootloader.
     Example: Like BIOS in a PC
2. Bootloader
   -Initializes basic hardware (RAM, CPU, display, clocks)
   - Verifies the integrity of the boot partition (Verified Boot / AVB)
   - Loads the Linux kernel and the ramdisk from the `boot.img`.
   Example: Bootloader is the mall security guard checking everything before opening.
3.LINUX KERNEL
   - Kernel initializes device drivers
   - Mounts the root filesystem
   - Passes control to user space by starting `init`.
   Example: Kernel is the OS's brainstem keeps things alive, working, and controlled.
4. The Init Process:
   - Once the bootloader has booted the kernel, it starts the init process, which is the first Android operating system process.
   - This process has a Process ID (PID) of 1, indicating it is the initial process loaded by the bootloader.
   - The init process is responsible for loading various components and "demons" (background services) that run behind the scenes of the Android operating 		system. It also maintains all 	other processes.
   - The init process takes its configuration and settings from a specific file called init.rc.
   **The init.rc File:**
	   - The init.rc file is crucial for the init process and is present in the root system of all Android operating systems, regardless of whether they are 		64-bit or 32-bit.
	   - This file dictates how the init process operates and is responsible for mounting various file systems and loading kernel components.
	   - The content of the init.rc file is vendor-specific, meaning different vendors may have different settings within their respective init.rc files.It 		is strongly advised not to change any settings inside this file, as it can lead to significant security issues.
5. The Zygote Process:
   - After loading its components and configuration, the init process starts another critical process known as the zygote process.
   - The zygote process is a child of the init process. This can be verified by checking its Parent Process ID (PPID), which will be 1 (the PID of the init 		process).
   - The primary role of the zygote process is to load the Dalvik Virtual Machine (DVM).
   Example: Zygote is like a pre-heated oven ready to bake apps quickly
     	 - Zygote forks itself to create each new app process.
   	 - Saves memory via Copy-On-Write.
6. Dalvik Virtual Machine (DVM):
	- The DVM is essential because it is required to start and run any Android application. Android applications execute with the help of the Dalvik Virtual 	Machine.
7. System Server Starts Android system services:
   - Launched by Zygote
   - Hosts all system-level services:
        - ActivityManagerService
        - WindowManagerService
        - PackageManagerService
        - PowerManagerService
     Example: System Server is the brain of Androids logic and behavior
8. System UI
   - Provides visual components like:
   - Status bar
   - Navigation bar
   - Notification panel
   Example: System UI is the visual skin of Android
9. Launcher
   - Home screen is displayed
   - App icons, widgets, and user interaction starts
   - Boot is complete
     Example: Launcher is the front desk receptionist â€” hands you access to everything
This layered boot ensures a secure, modular, and fast startup.


