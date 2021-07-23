---
title: HoloLens kiosk reference information
description: Information and samples for kiosks on HoloLens devices. 
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: v-evmill
ms.topic: article
ms.localizationpriority: medium
ms.date: 7/22/2021
ms.reviewer: 
manager: yannisle
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# HoloLens Kiosk reference information

## Updates to Kiosk



## Troubleshooting Kiosk

Do not include Classic Windows applications (Win32). HoloLens does not support these applications.

### Kiosk and HoloLens (1st gen)

Kiosk mode is available only if the device has Windows Holographic for Business. All HoloLens 2 devices ship with Windows Holographic for Business and there are no other editions. Every HoloLens 2 devices is able to run Kiosk mode out of the box.

HoloLens (1st gen) devices need to be upgraded both in terms of OS build and OS edition. Here is more information on updating a HoloLens (1st gen) to [Windows Holographic for Business](hololens1-upgrade-enterprise.md) edition. To update a HoloLens (1st gen) device to use kiosk mode, you must first make sure that the device runs Windows 10, version 1803, or a later version. If you have used the Windows Device Recovery Tool to recover your HoloLens (1st gen) device to its default build, or if you have installed the most recent updates, your device is ready to configure.

### Kiosk deployment methods

- Microsoft Intune or other mobile device management (MDM) service
- Provisioning package
- Windows Device Portal

   > [!NOTE]  
   > Because Device Portal requires that Developer Mode be enabled on the device, we recommend that you use it only for demonstrations.

The following table lists the capabilities and benefits of each of the deployment methods.

| &nbsp; |Deploy by using Windows Device Portal |Deploy by using a provisioning package |Deploy by using MDM |
| --------------------------- | ------------- | -------------------- | ---- |
|Deploy single-app kiosks   | Yes           | Yes                  | Yes  |
|Deploy multi-app kiosks    | No            | Yes                  | Yes  |
|Deploy to local devices only | Yes           | Yes                  | No   |
|Deploy by using Developer Mode |Required       | Not required            | Not required   |
|Deploy by using Azure Active Directory (Azure AD)  | Not required            | Not required                   | Required  |
|Deploy automatically      | No            | No                   | Yes  |
|Deployment speed            | Fast       | Fast                 | Slow |
|Deploy at scale | Not recommended    | Recommended        | Recommended |

## HoloLens AUMIDs

For general information about how to choose kiosk apps, see [Guidelines for choosing an app for assigned access (kiosk mode)](/windows/configuration/guidelines-for-assigned-access-app).

If you use the Windows Device Portal to configure a single-app kiosk, you select the app during the setup process.  

If you use a Mobile Device Management (MDM) system or a provisioning package to configure kiosk mode, you use the [AssignedAccess Configuration Service Provider (CSP)](/windows/client-management/mdm/assignedaccess-csp) to specify applications. The CSP uses [Application User Model IDs (AUMIDs)](/windows/configuration/find-the-application-user-model-id-of-an-installed-app) to identify applications. The following table lists the AUMIDs of some in-box applications that you can use in a multi-app kiosk.

> [!IMPORTANT]
> Kiosk mode determines which apps are available when a user signs in to the device. However, kiosk mode is not a security method. It does not stop an "allowed" app from opening another app that is not allowed. Because we do not restrict this behavior, apps can still be launched from Edge, File explorer, and the Microsoft Store apps. If there are specific apps you don't want launched from a Kiosk, use [Windows Defender Application Control (WDAC) CSP](/windows/client-management/mdm/applicationcontrol-csp) to create appropriate policies.
>
> In addition, the Mixed Reality Home is not able to be set as a kiosk app.

<a id="aumids"></a>

|App Name |AUMID |
| --- | --- |
|3D Viewer |Microsoft.Microsoft3DViewer\_8wekyb3d8bbwe\!Microsoft.Microsoft3DViewer |
|Calendar |microsoft.windowscommunicationsapps\_8wekyb3d8bbwe\!microsoft.windowslive.calendar |
|Camera<sup>1, 2</sup> |HoloCamera\_cw5n1h2txyewy\!HoloCamera |
|Cortana<sup>3</sup> |Microsoft.549981C3F5F10\_8wekyb3d8bbwe\!App |
|Device Picker on HoloLens (1st gen) |HoloDevicesFlow\_cw5n1h2txyewy\!HoloDevicesFlow |
|Device Picker on HoloLens 2 |Microsoft.Windows.DevicesFlowHost\_cw5n1h2txyewy\!Microsoft.Windows.DevicesFlowHost |
|Dynamics 365 Guides |Microsoft.Dynamics365.Guides\_8wekyb3d8bbwe\!MicrosoftGuides |
|Dynamics 365 Remote Assist |Microsoft.MicrosoftRemoteAssist\_8wekyb3d8bbwe\!Microsoft.RemoteAssist |
|Feedback&nbsp;Hub |Microsoft.WindowsFeedbackHub\_8wekyb3d8bbwe\!App |
|File Explorer |c5e2524a-ea46-4f67-841f-6a9465d9d515_cw5n1h2txyewy!App |
|Mail |microsoft.windowscommunicationsapps_8wekyb3d8bbwe!microsoft.windowslive.mail |
|Old Microsoft Edge |Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge |
|New Microsoft Edge |Microsoft.MicrosoftEdge.Stable_8wekyb3d8bbwe!MSEDGE |
|Microsoft Store |Microsoft.WindowsStore_8wekyb3d8bbwe!App |
|Miracast<sup>4</sup> |&nbsp; |
|Movies & TV |Microsoft.ZuneVideo\_8wekyb3d8bbwe\!Microsoft.ZuneVideo |
|OneDrive |microsoft.microsoftskydrive\_8wekyb3d8bbwe\!App |
|Photos |Microsoft.Windows.Photos\_8wekyb3d8bbwe\!App |
|Old Settings |HolographicSystemSettings_cw5n1h2txyewy!App |
|New Settings |BAEAEF15-9BAB-47FC-800B-ACECAD2AE94B_cw5n1h2txyewy!App |
|Tips |Microsoft.HoloLensTips\_8wekyb3d8bbwe\!HoloLensTips |

> <sup>1</sup> To enable photo or video capture, you have to enable the Camera app as a kiosk app.  
> <sup>2</sup> When you enable the Camera app, be aware of the following conditions:
> - The Quick Actions menu includes the Photo and Video buttons.
> - You should also enable an app (such as Photos, Mail, or OneDrive) that can interact with or retrieve pictures.  
>  
> <sup>3</sup> Even if you do not enable Cortana as a kiosk app, built-in voice commands are enabled. However, commands that are related to disabled features have no effect.  
> <sup>4</sup> You cannot enable Miracast directly. To enable Miracast as a kiosk app enable the Camera app and the Device Picker app.


## Code Samples

