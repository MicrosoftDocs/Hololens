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

A device may be assigned more than one WDAC policy. If multiple WDAC policies are set on a system, most restrictive ones take effect. 

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
| App Installer              | Microsoft.DesktopAppInstaller_8wekyb3d8bbwe <sup>1</sup>         |
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

- 1 - Blocking App Installer will only block the App Installer app, and not apps installed from other sources such as the Microsoft Store or from your MDM solution.

### How to find a Package Family Name

If an app is not on this list then a user may use Device Portal, connected to a HoloLens 2 that has installed the app wished to be blocked, to determine the PackageRelativeID and from there get the PackageFamilyName.

1. Install the app on your HoloLens 2 device. 
1. Open Settings -> Updates & Security -> For developers, and enable **Developer mode** and then **Device portal**. 
    1. More more details instructions read more about [setup and use of device portal here](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).
1. Once Device Portal is connected, navigate to **Views** then **Apps**. 
1. Within the Installed Apps panel use the dropdown to select the installed app. 
1. Locate the PackageRelativeID. 
1. Copy app characters before the !, this will be your PackageFamilyName.

## Sample - Blocking App Installer

As an example you may wish to block the App Installer app. We have included some sample code for this example. Please download these [code samples for this example](https://aka.ms/HoloLensDocs-Sample-WDAC-App-Installer). In the zip file you'll find:

| File | Use |
|-|-|
| compiledPolicy.bin | [Created in Step 9, used in final Step 10.](https://docs.microsoft.com/mem/intune/configuration/custom-profile-hololens) |
| mergedPolicy.xml | [Created in Step 6.](https://docs.microsoft.com/mem/intune/configuration/custom-profile-hololens) |
| WDAC_Set.syncml | Not used in WDAC but can be used for for [EnterpriseModernAppManagement CSP](https://docs.microsoft.com/windows/client-management/mdm/enterprisemodernappmanagement-csp) |

If you would like to try immediately blocking an app, in this case the App Installer app, then use the compiledPolicy.bin file and skip to step 10 in the link above. This will allow you to test out the custom policy and ensure the group assignments and policy configuration is correct. 

If you would like to combine the WDAC policy for blocking App Installer with other apps from the list above, or any other app, then you may use the mergedPolicy.xml file and continue to merge new policies. As stated above WDAC policies are additive so this is not required. 

Since the App Installer app is launched via trying to open a file will be presented with a prompt. As stated above Apps blocked by WDAC do not present a prompt they are blocked, however since the user is attempting to open a file on their device they are presented with an error for opening the file. 

![App install blocked from WDAC](images\wdac-app-installer-no-launch.jpg)

If you do not wish to use WDAC, you may as an alternative use [EnterpriseModernAppManagement CSP](https://docs.microsoft.com/windows/client-management/mdm/enterprisemodernappmanagement-csp) to remove the App Installer UX, which is an app after all. The result of this is that the App Installer app will be uninstalled from the device. .appx, .msix, .msixbundle, and other file extensions as well as protocol for web-to-app launch will no longer be handled by the App Installer app. The user will get a prompt to search for a handler for the file extension/protocol in the store and they will not find the app because it’s not listed.

