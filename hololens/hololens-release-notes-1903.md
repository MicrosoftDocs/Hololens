---
title: HoloLens 2 release notes for Windows Holographic, version 1903
description: Read through previous HoloLens 2 release notes.
author: evmill
ms.author: v-evmill
manager: ranjibb
ms.prod: hololens
ms.sitesec: library
ms.topic: article
ms.date: 11/19/2021
audience: ITPro
appliesto:
- HoloLens 2

---

# HoloLens 2 release notes - Version 1903

These are release notes for an older HoloLens servicing build. Windows Holographic, version 1903 is no longer being serviced, but these release notes are kept as a record of HoloLens 2 update history. You may also view the [most current release notes for HoloLens](hololens-release-notes.md).

## Windows Holographic, version 1903 - June 2021 Update

- Build 18362.1116

Improvements and fixes in the update:

- This monthly quality update doesn't contain any notable changes, we encourage you to try out our latest build, Windows Holographic, version 21H1.

>[!IMPORTANT]
> This build will no longer be serviced.

## Windows Holographic, version 1903 - May 2021 Update

- Build 18362.1110

Improvements and fixes in the update:

- This monthly quality update doesn't contain any notable changes. **This build will no longer be receiving monthly service updates**. We encourage you to try out our latest build, Windows Holographic, version 21H1.

## Windows Holographic, version 1903 - April 2021 Update

- Build 18362.1108

Improvements and fixes in the update:

- Addresses an issue where the Settings app crashes when attempting to change a password for a local account.

## Windows Holographic, version 1903 - March 2021 Update

- Build 18362.1102

Improvements and fixes in the update:

- Fix for a memory leak in Device Portal Service, the issue caused increased memory usage by the service that caused other applications to fail allocating memory.

## Windows Holographic, version 1903 - February 2021 Update

- Build 18362.1098

This monthly quality update doesn't contain any notable changes, we encourage you to try out our latest builds for Windows Holographic, version 2004.

## Windows Holographic, version 1903 - January 2021 Update

- Build 18362.1091

This monthly quality update doesn't contain any notable changes, we encourage you to try out our latest builds for Windows Holographic, version 2004.

## Windows Holographic, version 1903 – December 2020 Update

- Build 18362.1088

This monthly quality update doesn't contain any notable changes, we encourage you to try out our latest Windows Holographic, version 20H2 – December 2020 Update and the new App Installer feature added in the build.

## Windows Holographic, version 1903 - November 2020 Update

- Build 18362.1085

This monthly quality update doesn't contain any notable changes, we encourage you to try out our latest feature release build Windows Holographic, version 20H2.

## Windows Holographic, version 1903 - October 2020 Update

- Build 18362.1081

This monthly quality update doesn't contain any notable changes, we encourage you to try out our latest builds for Windows Holographic, version 2004.

## Windows Holographic, version 1903 - September 2020 Update

- Build 18362.1079

Improvements and fixes in the update:

- On most Windows Mixed Reality devices, the forward direction vector is parallel to the ground when the user's head is in a neutral position looking forward. However, earlier versions of HoloLens 2 aligned the vector to be perpendicular to the display panels instead, which is tilted downward a few degrees relative to the ideal orientation. Newer versions of HoloLens 2 have corrected this to ensure semantic consistency across form factors.
- Improved hand tracking robustness that will result in fewer tracking losses in specific scenarios.

## Windows Holographic, version 1903 - August 2020 Update

- Build 18362.1074

This monthly quality update doesn't contain any notable changes, we encourage you to try out our latest builds for Windows Holographic, version 2004.

## Windows Holographic, version 1903 - July 2020 Update

- Build 18362.1071

Improvements and fixes in the update:

- Fixed an issue that could cause holograms to disappear in Unity applications when losing or regaining tracking.
- Fixed an issue that caused exclusive HoloLens apps to crash back to the shell while using the HoloLens Emulator with hardware acceleration on certain devices.
- Addressed an issue concerning HTTPS forwarding for the Windows Device Portal on HoloLens 2.

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


