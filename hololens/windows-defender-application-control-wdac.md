---
title: Windows Defender Application Control (WDAC)
description: Overview on what Windows Defender Application Control is and how to use it to manage HoloLens mixed reality devices.
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: v-evmill
ms.topic: article
ms.localizationpriority: medium
ms.date: 9/21/2021
ms.reviewer: 
manager: yannisle
appliesto:
- HoloLens 2
---

# Windows Defender Application Control - WDAC

## Overview

WDAC allows you to configure HoloLens to block the launch of apps. It's different from the Kiosk mode, where the UI hides the apps but they can still be launched. With WDAC, you can see the apps but they can’t be launched.

> [!NOTE]
> When end users attempt to launch an app that is blocked by WDAC on HoloLens, they won't be notified about not being able to launch the app.

A device may be assigned more than one WDAC policy. If multiple WDAC policies are set on a system, most restrictive ones take effect.

The following is a guide for users to learn how to [use WDAC and Windows PowerShell to allow or block apps on HoloLens 2 devices with Microsoft Intune](/mem/intune/configuration/custom-profile-hololens).

When users search for apps installed on their Windows 10 PC using the first example step, they may need to make a few attempts to narrow down the results.

```powershell
$package1 = Get-AppxPackage -name *<applicationname>*
```

If you don’t know the full name of the package, you may need to run ‘Get-AppxPackage -name \*YourBestGuess\*’ a few times to find it. Then once you have the name run ‘$package1 = Get-AppxPackage -name Actual.PackageName‘

For example running the following code for Microsoft Edge will return more than one result, but from that list you can identify that the full name you need is Microsoft.MicrosoftEdge.

```powershell
Get-AppxPackage -name *edge*
```

## Package Family Names for apps on HoloLens

In the guide linked above, you can manually edit newPolicy.xml and add rules for applications that are only installed on HoloLens with their package family names. Sometimes there are apps you may use to use that are not on your desktop PC that you wish to add to policy.

Here is a list of commonly used and In-Box apps for HoloLens 2 devices.

| App Name                   | Package Family Name                                |
|----------------------------|----------------------------------------------------|
| 3D Viewer                  | `Microsoft.Microsoft3DViewer_8wekyb3d8bbwe`          |
| App Installer              | `Microsoft.DesktopAppInstaller_8wekyb3d8bbwe` <sup>1</sup>         |
| Calendar                   | `microsoft.windowscommunicationsapps_8wekyb3d8bbwe`  |
| Camera                     | `HoloCamera_cw5n1h2txyewy`                          |
| Cortana                    | `Microsoft.549981C3F5F10_8wekyb3d8bbwe`              |
| Dynamics 365 Guides        | `Microsoft.Dynamics365.Guides_8wekyb3d8bbwe`         |
| Dynamics 365 Remote Assist | `Microsoft.MicrosoftRemoteAssist_8wekyb3d8bbwe`      |
| Feedback Hub               | `Microsoft.WindowsFeedbackHub_8wekyb3d8bbwe`         |
| File Explorer              | `c5e2524a-ea46-4f67-841f-6a9465d9d515_cw5n1h2txyewy` |
| Mail                       | `microsoft.windowscommunicationsapps_8wekyb3d8bbwe`  |
| Microsoft Store            | `Microsoft.WindowsStore_8wekyb3d8bbwe`               |
| Movies & TV                | `Microsoft.ZuneVideo_8wekyb3d8bbwe`                  |
| OneDrive                   | `microsoft.microsoftskydrive_8wekyb3d8bbwe`          |
| Photos                     | `Microsoft.Windows.Photos_8wekyb3d8bbwe`             |
| Settings                   | `HolographicSystemSettings_cw5n1h2txyewy`            |
| Tips                       | `Microsoft.HoloLensTips_8wekyb3d8bbwe`               |

- 1 - Blocking App Installer will only block the App Installer app, and not apps installed from other sources such as the Microsoft Store or from your MDM solution.

### Using WDAC to block new Microsoft Edge

For IT Admins looking to update their [WDAC policy](windows-defender-application-control-wdac.md) to block the [new Microsoft Edge app](hololens-new-edge.md), you'll need to add the following to your policy.

```xml
<Deny ID="ID_DENY_D_3_0" FriendlyName="C:\Data\Programs FileRule" PackageVersion="65535.65535.65535.65535" FileName="msedge.exe" />
```

### How to find a Package Family Name

If an app is not on this list, then a user may use Device Portal, connected to a HoloLens 2 that has installed the app wished to be blocked, to determine the PackageRelativeID and from there get the PackageFamilyName.

1. Install the app on your HoloLens 2 device.

1. Open Settings -> Updates & Security -> For developers, and enable **Developer mode** and then **Device portal**.

   For more more details and instructions, see [set up and use of device portal here](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).

1. Once Device Portal is connected, navigate to **Views** then **Apps**.

1. Within the Installed Apps panel, use the dropdown to select the installed app.

1. Locate the PackageRelativeID.

1. Copy app characters before the `!`, these characters will be your PackageFamilyName.
