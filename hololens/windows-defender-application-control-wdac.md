---
title: Windows Defender Application Control - WDAC
description: Overview on what WDAC is and how to use to manage HoloLens devices.
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: v-evmill
ms.topic: article
ms.localizationpriority: medium
ms.date: 09/16/2020
ms.reviewer: 
manager: yannisle
appliesto:
- HoloLens 2
---

# Windows Defender Application Control - WDAC

WDAC allows an IT Admin to configure their devices to block the launch of apps on devices. This is different than methods of device restriction such as Kiosk mode, where  the user is presented with a UI that hides the apps on the device but they can still be launched. While WDAC is implemented, the apps are still visible in the All Apps list but WDAC stops those apps and processes from being able to be launched by the device user.

> [!NOTE]
> When end users attempt to launch an app that is blocked by WDAC, on HoloLens they will not receive a notification about not being able to launch that app.

The following is a guide for users to learn how to [use WDAC and Windows PowerShell to allow or block apps on HoloLens 2 devices with Microsoft Intune](https://docs.microsoft.com/mem/intune/configuration/custom-profile-hololens).

When users search for apps installed on their Windows 10 PC using the first example step they may need to make a few attempts to narrow down the results.

```powershell
$package1 = Get-AppxPackage -name *<applicationname>*
``` 

If you don’t know the full name of the package, you may need to run ‘Get-AppxPackage -name \*YourBestGuess\*’ a few times to find it. Then once you have the name run ‘$package1 = Get-AppxPackage -name Actual.PackageName‘

For example running the following for Edge will return more than one result, but from that list you can identify that the full name you need is Microsoft.MicrosoftEdge. 

```powershell
Get-AppxPackage -name *edge*
``` 

## Package Family Names for apps on HoloLens

In the guide linked above, you can manually edit newPolicy.xml and add rules for applications which are only installed on HoloLens with their package family names. Sometimes there are apps you may use to use that are not on your desktop PC that you wish to add to policy. 

Here is a list of commonly used and In-Box apps for HoloLens 2 devices.

| App Name                   | Package Family Name                                |
|----------------------------|----------------------------------------------------|
| 3D Viewer                  | Microsoft.Microsoft3DViewer_8wekyb3d8bbwe          |
| App Installer              | Microsoft.DesktopAppInstaller_8wekyb3d8bbwe          |
| Calendar                   | microsoft.windowscommunicationsapps_8wekyb3d8bbwe  |
| Camera                     | HoloCamera_cw5n1h2txyewy                           |
| Cortana                    | Microsoft.549981C3F5F10_8wekyb3d8bbwe              |
| Dynamics 365 Guides        | Microsoft.Dynamics365.Guides_8wekyb3d8bbwe         |
| Dynamics 365 Remote Assist | Microsoft.MicrosoftRemoteAssist_8wekyb3d8bbwe      |
| Feedback Hub               | Microsoft.WindowsFeedbackHub_8wekyb3d8bbwe         |
| File Explorer              | c5e2524a-ea46-4f67-841f-6a9465d9d515_cw5n1h2txyewy |
| Mail                       | microsoft.windowscommunicationsapps_8wekyb3d8bbwe  |
| Microsoft Store            | Microsoft.WindowsStore_8wekyb3d8bbwe               |
| Movies & TV                | Microsoft.ZuneVideo_8wekyb3d8bbwe                  |
| OneDrive                   | microsoft.microsoftskydrive_8wekyb3d8bbwe          |
| Photos                     | Microsoft.Windows.Photos_8wekyb3d8bbwe             |
| Settings                   | HolographicSystemSettings_cw5n1h2txyewy            |
| Tips                       | Microsoft.HoloLensTips_8wekyb3d8bbwe               |

If an app is not on this list then a user may use Device Portal, connected to a HoloLens 2 that has installed the app wished to be blocked, to determine the PackageRelativeID and from there get the PackageFamilyName.

1. Install the app on your HoloLens 2 device. 
1. Open Settings -> Updates & Securtiy -> For developers, and enable **Developer mode** and then **Device portal**. 
    1. More more details instructions read more about [setup and use of device portal here](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).
1. Once Device Portal is connected, navigate to **Views** then **Apps**. 
1. Within the Installed Apps panel use the dropdown to select the installed app. 
1. Locate the PackageRelativeID. 
1. Copy app characters before the !, this will be your PackageFamilyName.

