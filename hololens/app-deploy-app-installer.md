---
title: How to side load and Install Apps via HoloLens 2 App Installer
description: Slide load and install apps via UI
keywords: app management, app, hololens, app installer
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

# Install Apps on HoloLens 2 via App Installer

Users can now install Apps via Appx Bundles now without the need to enable Developer Mode or use Device Portal. This experience is simple for installing Apps on local devices or sharing an app with someone else who is unfamiliar with other app install methods on HoloLens. 

> [!NOTE]
> For IT Admins who wish to disable this feature please use the following package family name as part of your [WDAC policy](windows-defender-application-control-wdac.md). This will only block the App Installer app, and not apps installed from other sources such as the Microsoft Store or from your MDM solution.
```
Microsoft.DesktopAppInstaller_8wekyb3d8bbwe
```

## Requirements
For your devices: This was added in [Windows Holographic, verison 2010](hololens-release-notes.md#windows-holographic-version-2010) for HoloLens 2 devices. Please ensure any devices using this method are [updated](hololens-update-hololens.md). 

For your apps: Your app’s Solution Configuration must be either **Master** or **Release** as the App Installer will use dependencies from the store. See more about [creating app packages](https://docs.microsoft.com/windows/msix/app-installer/create-appinstallerfile-vs).

1.	Ensure that your HoloLens 2 device is powered on and you are signed in.
1.	On your PC navigate to your custom app, and copy yourapp.appxbundle to yourdevicename\Internal Storage\Downloads. 
    After your finish copying your file you may disconnect your device and finish the install later.
1.	From your HoloLens 2 device Open the **Start Menu**, select **All apps** and launch the **File Explorer** app.
1.	Navigate to the Downloads folder. You may need to on the left panel of the app select **This device** first, then navigate to Downloads.
1.	Select the yourapp.appxbundle file. 
1.	The App Installer will launch. Select the **Install** button to install your app. 

The installed app will automatically launch upon the completion of installing. 

![Installing MRTK Examples via App Installer](images/hololens-app-installer-picture.jpg)

If your app failed to install check the following:
-	Your app is either a Master or Release build.
-	You are [connected to the internet](hololens-network.md).
-	Your [endpoints for the Microsoft Store](hololens-offline.md) are correctly configured.  
