---
title: How to install Apps via web Installer
description: Install apps via web installer for app installer
keywords: app management, app, hololens, app installer, web install
author: evmill
ms.author: v-evmill
ms.reviewer: qizho
ms.date: 10/13/2020
ms.prod: hololens
ms.topic: article
ms.sitesec: library
ms.localizationpriority: medium
audience: HoloLens
manager: yannisle
appliesto:
- HoloLens 2
---

# Installing apps from a web page

> [!NOTE]
> This was added in [Windows Holographic, verison 2010](hololens-release-notes.md#windows-holographic-version-2010) for HoloLens 2 devices.

Users can install an app directly from a web server. This takes use of the App Installer combined with an easy download and install distribution method. 

## How to set this up:
1.	Ensure your app is correctly configured to install.
1.	Follow these [steps to enable this on a web page](https://docs.microsoft.com/windows/msix/app-installer/installing-windows10-apps-web#how-to-enable-this-on-a-webpage). 
1.	Pick a certificate deployment method. 
    1.	[Provisioning Packages](hololens-provisioning.md) can be applied to local devices.
    1.	MDM can be used to [apply certificates with device configurations](https://docs.microsoft.com/mem/intune/protect/certificates-configure).
    1.	Use the on device [Certificate Manager](certificate-manager.md). 

## End User Experience:
1.	User receives and installs certificate to the device using a method previously chosen above. 
1.	User visits the URL created from the step above.

The app will now install to the device. To find the app open the **Start menu** and select the **All apps** button to find your app. 

-	For help troubleshooting this installation method please visit [troubleshoot app installer issues](https://docs.microsoft.com/windows/msix/app-installer/troubleshoot-appinstaller-issues). 

> [!NOTE]
> UI during the update process is not supported. So the ShowPrompt option on [this page](https://docs.microsoft.com/windows/msix/app-installer/update-settings) and related options are not supported.
