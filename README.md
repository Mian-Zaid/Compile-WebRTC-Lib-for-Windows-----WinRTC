# WebRTC-Development-for-Windows---WinRTC

How to Setup WebRTC for Development on Windows? In this repo, I will explain its step-by-step process to you.

---

## Pre-requisites

- Windows 10 (build 19041) or later.
- At least 8GB of RAM (16GB of RAM is recommended).
- At least 15GB of disk space.
- SSD drive formatted with NTFS.
- [Visual Studio 2019 Community Edition](https://my.visualstudio.com/Downloads?q=visual%20studio%202019&wt.mc_id=o~msft~vscom~older-downloads).
- [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=en-us&gl=us&activetab=pivot%3Aoverviewtab) OR Command Prompt.

## Visual Studio Installations

In the Visual Studio Installer app, please verify if Visual Studio 2019 has the following **workloads** installed:
- Desktop development with C++.
- Universal Windows Platform development.

Switch to the **Individual Components** tab and Select the following:
- C++ MFC for latest v142 build tools (x86 & x64).
- C++ ATL for latest v142 build tools (x86 & x64).

If you want to build for **ARM/ARM64**, Select:
- C++ MFC for latest v142 build tools
- C++ ATL for latest v142 build tools
- C++ Universal Windows Platform support for v142 build tools

## Setup SDK Debugging Tools

Please go to:
- **Control Panel → Programs → Programs and Features → Select the most recent Windows Software Development Kit → Change → Change → Select Debugging Tools For Windows → Change.**

## Opening Developer Command Prompt

You'll need a command prompt configured for calling Visual Studio tools. we have 2 ways for that:

1. Using the shortcut in the start menu.
   - **Start Menu → Visual Studio 2019 → x64 Native Tools Command Prompt for VS 2019**
   - OR Search for **x64 Native Tools Command Prompt for VS 2019** in start menu.
   - **Run as an Admin**
2. Executing the batch file with the configuration
  - Open the Windows terminal and paste the following command
  - **C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\VC\Auxiliary\Build\vcvars64.bat**

---

# After setting up the environment now we have to Download the WebRTC Code base
## Getting depot_tools
gclient error: solve by adding permission 777

---

*[Microsoft's Guide to Setup WinRTC](https://learn.microsoft.com/en-us/winrtc/getting-started).*

