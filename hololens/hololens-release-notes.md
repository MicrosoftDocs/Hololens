---
title: HoloLens 2 release notes
description: Learn about updates in each new HoloLens release.
author: scooley
ms.author: scooley
manager: laurawi
ms.prod: hololens
ms.sitesec: library
ms.topic: article
ms.localizationpriority: medium
ms.date: 06/9/2020
ms.custom: 
- CI 111456
- CSSTroubleshooting
audience: ITPro
appliesto:
- HoloLens 2

---

# HoloLens 2 release notes

To ensure you have a productive experience with your HoloLens devices, we continue to release feature, bug, and security updates. On this page, you can see what’s new for HoloLens each month. To get the latest HoloLens 2 Full Flash Update (FFU) to [flash your device via Advanced Recovery Companion](hololens-recovery.md#clean-reflash-the-device), [download it here](https://aka.ms/hololens2download). The download is kept up to date and provides the latest generally available build.

>[!NOTE]
> To read HoloLens Emulator release notes, [visit the archive](https://docs.microsoft.com/windows/mixed-reality/hololens-emulator-archive).

## Windows Holographic, version 2004 - August 2020 Update
- Build 19041.1111

Improvements and fixes in the update:

- Settings app will no longer follow the user into Iris Enrollment or Eye Tracking Calibration experiences.
- Fixed a bug where applying a provisioning package during OOBE that renames the device and performs other actions (such as connecting to a network) will fail to perform the other actions after the device reboot due to rename.
- Modified color scheme of initial device setup flows to improve visual quality.

## Windows Holographic, version 1903 - August 2020 Update
- Build 18362.1073

This monthly quality update doesn't contain any notable changes, we encourage you to try out our latest builds for Windows Holographic, version 2004.

## Windows Holographic, version 2004 - July 2020 Update
- Build 19041.1109

Improvements and fixes in the update:

- Developers can now choose between enabling or disabling having Device Portal require a secure connection.
- Reliability improved for application launches after OS updates.
- Changed default inbox brightness to 100 percent.
- Addressed an issue about HTTPS forwarding for the Windows Device Portal on HoloLens 2.

## Windows Holographic, version 1903 - July 2020 Update
- Build 18362.1071

Improvements and fixes in the update:

- Fixed an issue that could cause holograms to disappear in Unity applications when losing or regaining tracking.
- Fixed an issue that caused exclusive HoloLens apps to crash back to the shell while using the HoloLens Emulator with hardware acceleration on certain devices.
- Addressed an issue concerning HTTPS forwarding for the Windows Device Portal on HoloLens 2.

## Windows Holographic, version 2004 - June 2020 Update
- Build 19041.1106

Improvements and fixes in the update:

- Custom MRC recorders now have new default values for certain properties if they aren't specified.
  - On the *MRC Video Effect*:
    - PreferredHologramPerspective (1 PhotoVideoCamera)
    - GlobalOpacityCoefficient (0.9 (HoloLens) 1.0 (Immersive headset))
  - On the *MRC Audio Effect*:
    - LoopbackGain (the current "App Audio Gain" value on the Mixed Reality Capture page in Windows Device Portal)
    - MicrophoneGain (the current "Mic Audio Gain" value on the Mixed Reality Capture page in Windows Device Portal)
- Fixed a bug to improve audio quality in mixed reality capture scenarios. Specifically, this fix should eliminate audio glitching in the recording when the **Start** menu is displayed.
- Improved hologram stability in recorded videos.
- Resolved an issue where mixed reality capture couldn't record video after the device was left in standby state for multiple days.
- The HolographicSpace.UserPresence API is generally disabled for Unity applications. This behavior avoids an issue that caused some apps to pause when the visor was flipped up, even if the "run in the background" setting was enabled. The API is now enabled for Unity versions 2018.4.18 and later and 2019.3.4 and later.
- When you access Device Portal over a Wi-Fi connection, a web browser might prevent access to due to an invalid certificate. The browser might report an error such as "ERR_SSL_PROTOCOL_ERROR," even if the device certificate was previously trusted. In this case, you can't progress to Device Portal, as there's no option to ignore security warnings. This update resolved the issue. If the device certificate was previously downloaded and trusted on a PC to remove browser security warnings, and the SSL error occurs, the new certificate has to be downloaded and trusted to address browser security warnings.
- Enabled the ability to create a runtime provisioning package that can install an app by using MSIX packages.
- Added a setting in **Settings** > **System** > **Holograms** that allows users to automatically remove all holograms from Mixed Reality home when the device shuts down.
- Fixed an issue that caused HoloLens apps that change their pixel format to render black in the HoloLens emulator.
- Fixed a bug that caused a crash during Iris login.
- Fixed an issue about repeated store downloads for already-current apps.
- Fixed a bug to prevent immersive apps from opening Microsoft Edge repeatedly.
- Fixed an issue with launches of the Photos app in initial boots after updating from the 1903 release.
- Improved performance and reliability.

## Windows Holographic, version 1903 - June 2020 Update
- Build 18362.1064

Improvements and fixes in the update:

- Custom MRC recorders have new default values for certain properties if they aren't specified.
  - On the *MRC Video Effect*:
    - PreferredHologramPerspective (1 PhotoVideoCamera)
    - GlobalOpacityCoefficient (0.9 (HoloLens) 1.0 (Immersive headset))
  - On the *MRC Audio Effect*:
    - LoopbackGain (the current "App Audio Gain" value on the Mixed Reality Capture page in Windows Device Portal)
    - MicrophoneGain (the current "Mic Audio Gain" value on the Mixed Reality Capture page in Windows Device Portal)
- The HolographicSpace.UserPresence API is generally disabled for Unity applications. This behavior avoids an issue that causes some apps to pause when the visor is flipped up, even if the setting to run in the background is enabled. The API is now enabled for Unity versions 2018.4.18 and later, and 2019.3.4 and later.
- Fixed an issue that caused HoloLens apps that change their pixel format to render black in the HoloLens Emulator.
- Fixed an issue about launches of the Photos app in initial boots after updating from the 1903 release.

## Windows Holographic, version 2004  
- Build - 19041.1103

The May 2020 major software update for HoloLens 2, *Windows Holographic, version 2004* includes a host of exciting new capabilities, such as support for Windows Autopilot, app dark mode, USB Ethernet support for 5G/LTE hotspots, and much more. To update to the latest release, open the **Settings** app, go to **Update & Security**, and select the **Check for Updates** button. 

|             Feature                              |          Description                                                                                              |
|--------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
|       Windows Autopilot                          |          Pre-configure and seamlessly set up   new devices for production by using Windows AutoPilot                 |
|       FIDO 2 support                             |          Support for FIDO2 Security Keys to   enable fast and secure authentication for shared devices            |
|       Improved provisioning                      |          Seamlessly apply a provisioning   package from a USB drive to your HoloLens                              |
|       Application install status                 |          Check install status in the Settings app for apps have been pushed to HoloLens 2 via MDM               |
|       Configuration service providers   (CSPs)   |          Added new configuration service providers to enhance admin control capabilities                 |
|       USB 5G/LTE support                       |          Expanded USB Ethernet capability   enables support for 5G/LTE                                    |
|       Dark app mode                              |          Dark app mode available for apps that support both dark and light modes, improving the viewing experience        |
|       Voice commands                             |          Support for additional system voice   commands to control HoloLens hands-free                           |
|       Hand tracking improvements                 |          Hand tracking improvements make buttons and 2D slate interactions more accurate                        |
|       Quality improvements and fixes                 |          Various system performance and   reliability improvements across the platform                            |

### Support for Windows Autopilot

Windows Autopilot for HoloLens 2 lets the device sales channel pre-enroll HoloLens into your Intune tenant. When devices arrive, they’re ready to self-deploy as shared devices under your tenant. To take advantage of self-deployment, the device must connect to a network during the first screen in setup by using a USB-C-to-Ethernet or USB-C-to-LTE dongle.

After a user starts the Autopilot self-deploying process, the process completes the following steps:

1. Join the device to Azure Active Directory (Azure AD).
1. Use Azure AD to enroll the device in Microsoft Intune (or another MDM service).
1. Download the device-targeted policies, certificates, and networking profiles.
1. Provision the device.
1. Present the sign-in screen to the user.

Learn more from the [Windows Autopilot for HoloLens 2 evaluation guide](https://docs.microsoft.com/hololens/hololens2-autopilot).

*Contact your Account Manager to join the AutoPilot preview now. Autopilot-ready devices will begin shipping soon.*

### FIDO2 security key support

Some users share a HoloLens device with others in a work or school environment. So it's important that users can easily without typing long user names and passwords. Fast Identity Online (FIDO) lets anyone in your organization (Azure AD tenant) seamlessly sign-in to HoloLens without entering a user name or password.

FIDO2 security keys are an "unphishable" standards-based passwordless authentication method that can come in any form factor. FIDO is an open standard for passwordless authentication. It allows users and organizations to sign in to their resources without a user name or password. Instead they use an external security key or a platform key built into a device.

To get started, see [Enable passwordless security key sign-in](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-security-key).

### Improved MDM enrollment via provisioning package

Provisioning packages let you set HoloLens configuration through a config file rather than through the HoloLens out-of-box experience. Previously, provisioning packages had to be copied onto the HoloLens internal memory. Now they can be on a USB drive so they're easier to reuse on multiple HoloLens devices and you can provision devices in parallel. Provisioning packages now also support a field to enroll in device management so there's no manual setup after provisioning.

To try it out:

1. Download the latest version of the Windows Configuration Designer from the Windows store onto your PC.
1. Select **Provision HoloLens Devices** > **Provision HoloLens 2 devices**.
2. Build your configuration profile. Then copy all files that were created to a USB-C storage device.
3. Plug the USB-C device into any freshly flashed HoloLens. Then press the **volume down** + **power** buttons to apply your provisioning package.

### Line-of-business application install status

MDM app deployment and management for line of business apps is critical to HoloLens. Admins and users need to view app install status for auditing and diagnosis. In this release, we added more details in **Settings** > **Accounts** > **Access work or school** > **Click on your account** > **Info**.

### Additional CSPs and policies

A [configuration service provider (CSP)](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference?redirectedfrom=MSDN) is an interface to read, set, modify, or delete configuration settings on a device. In this release, we add support for more policies to increase the control administrators have over deployed HoloLens devices. For the list of CSPs supported by HoloLens, see [NetworkQoSPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp).

New in this release:

**Policy CSP** 

The Policy configuration service provider enables the enterprise to configure policies on Windows devices. In this release, we added new policies for HoloLens, which are listed here. To learn more, see [Policy CSPs supported by HoloLens 2](https://docs.microsoft.com/windows/client-management/mdm/policies-supported-by-hololens2).  

- LetAppsAccessCamera_ForceAllowTheseApps  
- LetAppsAccessCamera_ForceDenyTheseApps  
- LetAppsAccessCamera_UserInControlOfTheseApps 
- LetAppsAccessGazeInput 
- LetAppsAccessGazeInput_ForceAllowTheseApps 
- LetAppsAccessGazeInput_ForceDenyTheseApps 
- LetAppsAccessGazeInput_UserInControlOfTheseApps 
- LetAppsAccessMicrophone_ForceAllowTheseApps 
- LetAppsAccessMicrophone_ForceDenyTheseApps 
- LetAppsAccessMicrophone_UserInControlOfTheseApps 
- AllowWiFi 

**NetworkQoSPolicy CSP**

The NetworkQoSPolicy configuration service provider creates network quality-of-service (QoS) policies. A QoS policy performs a set of actions on network traffic based on a set of matching conditions. To learn more, see [NetworkQoSPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp).

### Expanded USB Ethernet support for 5G/LTE tethered devices

Support was added to enable certain mobile broadband devices, such as 5G/LTE phones and Wi-Fi hotpots, when they're tethered to the HoloLens 2 via USB. These devices are now displayed in **network settings** as another Ethernet connection. (Mobile broadband devices that require an external driver aren't supported.) This functionality enables high-bandwidth connections when Wi-Fi is not available and Wi-Fi tethering isn't performant enough. To learn more about supported USB devices, see [Connect to Bluetooth and USB-C devices](https://docs.microsoft.com/hololens/hololens-connect-devices).  

### Hand tracking improvements

This release includes several hand tracking improvements:

- **Pointing pose stability:** The system now resists bending the index finger when it gets occluded by the palm. This change improves the accuracy when you push buttons, type, scroll content, and more! 
- **Reduced accidental air taps:** We improved detection of the air tap gesture. There are now fewer accidental activations in several common scenarios, such as when you drop your hands to your sides.
- **User switch reliability:** The system is now faster and more reliable at updating the hand size when you share a device.
- **Reduced hand stealing:** We improved handling of cases where there are more than two hands in view of the sensors. If multiple people are working close together, there's now a much lower chance that the tracked hand will "jump" from the user to the hand of someone else in the scene.
- **System reliability:** Fixed an issue that caused hand tracking to stop working when the device is under high load.

### Dark mode

Many Windows apps now support both dark and light modes. HoloLens 2 users can choose the default mode for apps that support both. After the update, the default app mode is "dark," but you can easily change this setting: Navigate to **Settings** > **System** > **Colors** > **Choose your default app mode**. 

These "in-box" apps support dark mode: 

- Settings 
- Microsoft Store 
- Mail 
- Calendar 
- File Explorer 
- Feedback Hub 
- OneDrive 
- Photos 
- 3D Viewer 
- Movies & TV 

![Dark mode windows tiled](images/DarkMode.jpg)

### System voice commands

You can now use voice commands with any app on the device. For more information, see [Use your voice to operate HoloLens](https://docs.microsoft.com/hololens/hololens-cortana). Also see [Supported languages for HoloLens 2](https://docs.microsoft.com/hololens/hololens2-language-support).  

### Cortana updates

The updated app integrates with Microsoft 365 to help you get more done across your devices (currently in US-English only). On HoloLens 2, Cortana no longer supports certain device-specific commands, like adjusting volume or restarting. These options are now supported by the new system voice commands. Learn more about the new Cortana app in our [blog](https://blogs.windows.com/windowsexperience/2020/02/28/cortana-in-the-upcoming-windows-10-release-focused-on-your-productivity-with-enhanced-security-and-privacy/).

### Quality improvements and fixes

Improvements and fixes also in the update:  
- Introduced an active display calibration system. This feature improves the stability and alignment of holograms. They now stay in place when you move your head from side to side.
- Fixed a bug where Wi-Fi streaming to HoloLens got disrupted periodically. If an application indicates that it needs low latency streaming, implement the fix by calling the [SetSocketMediaStreamingMode function](https://docs.microsoft.com/windows/win32/api/socketapi/nf-socketapi-setsocketmediastreamingmode).
- Fixed a device hang that occurred during streaming in research mode.
- Fixed a bug where in some cases the right user wouldn't be displayed on the sign-in screen when resuming a session.
- Fixed an issue where users couldn't export MDM logs through **Settings**.
- Fixed an issue where the accuracy of eye tracking immediately following out-of-box setup could be lower than expected.
- Fixed an issue where the eye tracking subsystem failed to initialize or perform calibration under certain conditions.
- Fixed an issue where eye calibration would be prompted for an already-calibrated user.
- Fixed an issue where a driver would crash during eye calibration.
- Fixed an issue where repeated power button presses could cause a 60-second system timeout and shell crash.
- Improved stability for depth buffers.
- Added a **Share** button in the Feedback Hub so users can more easily share feedback.
- Fixed a bug where RoboRaid wan't installed correctly.

### Known issues

- An issue with the zh-CN system language prevents voice commands from taking a mixed reality capture or displaying the device IP address.
- An issue requires you to launch the Cortana app after starting the device to use "Hey Cortana" voice activation. If you updated from a 18362 build, you may also see a second app tile for the previous version of the Cortana app that no longer works in **Start**.

## Windows Holographic, version 1903 - May 2020 Update 
- Build 18362.1061

This monthly quality update doesn't contain any notable changes because the team was working on the Windows Holographic version 2004 May Update, as described earlier.

## Windows Holographic, version 1903 - April 2020 Update
- Build 18362.1059

**Dark mode for supported apps** 

Many Windows apps support both dark and light mode. HoloLens 2 customers can now choose the default mode for apps that support both color schemes. Based on customer feedback, we set the default app mode to "dark," but you can easily change this setting at any time: Navigate to **Settings > System > Colors** to find **"Choose your default app mode."**

These "in-box" apps support dark mode:
- Settings
- Microsoft Store
- Mail
- Calendar
- File Explorer
- Feedback Hub
- OneDrive
- Photos
- 3D Viewer
- Movies & TV

**Improvements and fixes also in the update:** 
- Ensured that shell overlays are included in mixed reality captures.
- Unreal developers can now use the 3D View page in Device Portal to test and debug their applications.
- Improved hologram stability in mixed reality capture when the *HolographicDepthReprojectionMethod DepthReprojection* algorithm is used.
- Fixed the "WinRT IStreamSocketListener API Class not registered" error on 32-bit ARM apps.

## Windows Holographic, version 1903 - March 2020 Update 
- Build 18362.1056

Improvements and fixes in the update:

- Improved hologram stability in mixed reality capture when the *HolographicDepthReprojectionMethod AutoPlanar* algorithm is used.
- Ensured that the coordinate system attached to a depth MF sample is consistent with public documentation.
- Improved developer productivity by enabling customers to paste large amounts of text through the device portal.

## Windows Holographic, version 1903 - February 2020 Update 
- Build 18362.1053

Improvements and fixes in the update:

- Temporarily disabled the HolographicSpace.UserPresence API for Unity applications. This change avoids an issue that caused some apps to pause when the visor was flipped up, even if the "run in the background" setting was enabled.
- Fixed a random HUP crash caused by hand tracking, in which the user noticed a UI freeze then back to shell after several seconds.
- Improved hand tracking so that when you poke with your index finger, the upper part of that finger is less likely to curl unexpectedly.
- Improved reliability of head tracking, spatial mapping, and other runtimes.

## Windows Holographic, version 1903 - January 2020 Update 
- Build 18362.1043
 
Improvements and fixes in the update:

- Improved stability for exclusive apps when working with the HoloLens 2 emulator.

## Windows Holographic, version 1903 - December 2019 Update 
- Build 18362.1042

Improvements and fixes in the update:

- Introduced last stage reproduction (LSR) fixes. Improved visual rendering of holograms to appear more stable and crisp by more accurately accounting for their depth. This symptom will be more noticeable after this update if apps don't set the depth of holograms correctly.
- Fixed stability of exclusive apps and navigation between exclusive apps.
- Resolved an issue where mixed reality capture couldn't record video after the device was in standby state for several days.
- Improved hologram stability.

## Windows Holographic, version 1903 - November 2019 Update 
- Build 18362.1039

Improvements and fixes in the update:

- Fixed functionality of **Select** voice commands during initial setup for en-CA and en-AU.
- Improved visual quality of objects placed far away in the latest Unity and Mixed Reality Toolkit (MRTK) versions.
- Fixed addressing issues with holographic applications getting stuck in a paused state on startup until the Start menu was opened and then closed.
- OpenXR runtime conformance fixes and improvements for HoloLens 2 and the emulator.
