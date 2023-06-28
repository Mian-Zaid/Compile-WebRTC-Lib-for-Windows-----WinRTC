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
    - Open the Windows terminal and paste the following command (Kindly verify the path on your device, you might have *Community* version. In that case replace the *Enterprise* with Your version)
    - **C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\VC\Auxiliary\Build\vcvars64.bat**

---

# Download the WebRTC Code base

After setting up the environment, now we have to acquire the WebRTC code base.
## Getting depot_tools

WebRTC uses Chromium's build tools named depot_tools. You can download it with curl that is now shipped with Windows. 

1. Download depot_tool.zip to the current folder.

```
curl https://storage.googleapis.com/chrome-infra/depot_tools.zip --output depot_tools.zip
```

2. unzip depot_tools in the root folder of the f: drive.

```
mkdir f:\depot_tools
tar -xf depot_tools.zip -C f:\depot_tools
```

3. delete the depot_tools.zip file.

```
del depot_tools.zip
```

4. Set the path environment variable to execute commands in the depot_tools folder.

```
set PATH=f:\depot_tools;%PATH%
```

5. Let's inform depot_tools that we don't have access to Google's internal tools.

```
set DEPOT_TOOLS_WIN_TOOLCHAIN=0
```

6. The GYP build tool must be informed about the version of the Visual Studio we're using.

```
set GYP_MSVS_VERSION=2019
```

7. Create the folder where the code base will be placed.

```
f:
mkdir f:\webrtc
cd f:\webrtc
```

## Downloading the bits

1. Tell to the gclient tool to initialize your local copy of the repos.
*You might get few errors here, you only need to reset the permission of folder 'webrtc' to 777*

```
gclient
```

2. Request the tools to fetch the WebRTC code base. The following command will take time. **Few Hours** Maybe, Depending upon your network speed, so be Patient :)

```
fetch --nohooks webrtc
```

3. After successfull cloning for source code. Change to the **branch-heads/4147 branch**. This is the commit that the UWP(Universal Windows Platform) patches (see below) are based on.

```
cd src
git checkout branch-heads/4147
```

4. Instruct the tools to bring the bits from all the sub repositories to your dev box. This may take a while.

```
gclient sync -D -r branch-heads/4147
```

## Apply the Patches

The [patchWebRTCM84.cmd](https://github.com/microsoft/winrtc/blob/master/patches_for_WebRTC_org/m84/patchWebRTCM84.cmd) batch file needs to locate the WebRTC code base in order to be patched. 

1. The environment variable **WEBRTCM84_ROOT** should contain the path for the WebRTC code base you've just downloaded.

```
set WEBRTCM84_ROOT=f:\webrtc\src
```

2. Now, you just need to run the batch file that will patch all the necessary repos that form the WebRTC code base.

```
f:\WinRTC\patches_for_WebRTC_org\m84\patchWebRTCM84.cmd
```

---

# Setting up and Building

## Setting up

.
.
.
.

## Building

.
.

### With Visual Studio 2019
.
.
.

### With command line

.
.
.

---

# Using the generated binaries

.
.
.
.







---

*[Microsoft's Guide to Setup WinRTC](https://learn.microsoft.com/en-us/winrtc/getting-started).*

