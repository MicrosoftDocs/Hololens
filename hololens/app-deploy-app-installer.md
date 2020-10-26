---
title: How to side load and Install Apps via HoloLens 2 App Installer
description: Slide load and install apps via UI
keywords: app management, app, hololens, app installer
author: evmill
ms.author: v-evmill
ms.reviewer: qizho
ms.date: 10/26/2020
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

In our Windows Insider release, we are **adding a new capability (App Installer) to allow you to install applications more seamlessly** on your HoloLens 2 devices.  You are now able to install Apps without needing to enable Developer Mode or using Device Portal.  Simply download (over USB or through Edge) the Appx Bundle to your device and navigate to the Appx Bundle in the File Explorer to be prompted to kick off the installation.  Alternatively, [initiate an install from a web page](https://docs.microsoft.com/windows/msix/app-installer/installing-windows10-apps-web).  Just like apps you install from the Microsoft Store or sideload using MDM’s LOB App deployment capability, apps need to be digitally signed with the [Sign Tool](https://docs.microsoft.com/windows/win32/appxpkg/how-to-sign-a-package-using-signtool) and the [certificate used to sign must be trusted](https://docs.microsoft.com/windows/win32/appxpkg/how-to-sign-a-package-using-signtool#security-considerations) by the HoloLens device before the app can be deployed.   

This update aligns with desktop where [Sideloading is Enabled by Default](https://blogs.windows.com/windows-insider/2019/08/07/announcing-windows-10-insider-preview-build-18956/)

> [!IMPORTANT]
> This feature is currently only avalible in Windows Insider builds 19041.1377+. [Learn more on how to enroll in Windows Insider builds](hololens-insider.md).

> [!NOTE]
> For IT Admins who wish to disable this feature please use the following package family name as part of your [WDAC policy](windows-defender-application-control-wdac.md). This will only block the App Installer app, and not apps installed from other sources such as the Microsoft Store or from your MDM solution.
```
Microsoft.DesktopAppInstaller_8wekyb3d8bbwe
```
> [!NOTE]
> It is recommended to use [WDAC policy](windows-defender-application-control-wdac.md) to control apps, however if you only want to allow Microsoft Store apps, devices configured to set the [ApplicationManagement/AllowAllTrustedApps](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowalltrustedapps) policy explicitly to “not allow” will only allow apps to be installed from the Microsoft Store. 

## Requirements

### For your devices: 
> This feature is currently only avalible in Windows Insider builds 19041.1377+. [Learn more on how to enroll in Windows Insider builds](hololens-insider.md).

### For your apps: 
Your app’s Solution Configuration must be either **Master** or **Release** as the App Installer will use dependencies from the store. See more about [creating app packages](https://docs.microsoft.com/windows/msix/app-installer/create-appinstallerfile-vs).

Apps that are installed via this method must be digitally signed. You'll need to use a certificate to sign the app. You can either get a certificate from the [MS Trusted CA List](https://ccadb-public.secure.force.com/microsoft/IncludedCACertificateReportForMSFT), in which case you won't need to take any additional action. Or you can sign your own certificate however that certificate will need to be pushed onto the device. 
- How to sign apps [using the Sign Tool.](https://docs.microsoft.com/windows/win32/appxpkg/how-to-sign-a-package-using-signtool)

**Certificate options:** 
- [MS Trusted CA List](https://ccadb-public.secure.force.com/microsoft/IncludedCACertificateReportForMSFT)

**Pick a certificate deployment method.** 
- [Provisioning Packages](hololens-provisioning.md) can be applied to local devices.
- MDM can be used to [apply certificates with device configurations](https://docs.microsoft.com/mem/intune/protect/certificates-configure).
- Use the on device [Certificate Manager](certificate-manager.md). 

## Installation method

1.	Ensure that your HoloLens 2 device is powered on and you are signed in.
1.	On your PC navigate to your custom app, and copy yourapp.appxbundle to yourdevicename\Internal Storage\Downloads. 
    After your finish copying your file you may disconnect your device and finish the install later.
1.	From your HoloLens 2 device Open the **Start Menu**, select **All apps** and launch the **File Explorer** app.
1.	Navigate to the Downloads folder. You may need to on the left panel of the app select **This device** first, then navigate to Downloads.
1.	Select the yourapp.appxbundle file. 
1.	The App Installer will launch. Select the **Install** button to install your app. 

The installed app will automatically launch upon the completion of installing. 

![Installing MRTK Examples via App Installer](images/hololens-app-installer-picture.jpg)

### Troubleshooting Installs
If your app failed to install check the following:
-	Your app is either a Master or Release build.
- Your device is updated to a build on which this feature is available. 
-	You are [connected to the internet](hololens-network.md).
-	Your [endpoints for the Microsoft Store](hololens-offline.md) are correctly configured.  

## Web Installer

Users can install an app directly from a web server. This takes use of the App Installer combined with an easy download and install distribution method. 

### How to set up web install:
1.	Ensure your app is correctly configured to install.
1.	Follow these [steps to enable this on a web page](https://docs.microsoft.com/windows/msix/app-installer/installing-windows10-apps-web#how-to-enable-this-on-a-webpage). 

### End user experience:
1. User receives and installs certificate to the device using a method previously chosen above. 
1. User visits the URL created from the step above.

The app will now install to the device. To find the app open the **Start menu** and select the **All apps** button to find your app. 

-	For help troubleshooting this installation method please visit [troubleshoot app installer issues](https://docs.microsoft.com/windows/msix/app-installer/troubleshoot-appinstaller-issues). 

> [!NOTE]
> UI during the update process is not supported. So the ShowPrompt option on [this page](https://docs.microsoft.com/windows/msix/app-installer/update-settings) and related options are not supported.

## Sample Apps

If you'd like to try this out with some sample apps please check out some of our available samples:
- [MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html)
- [Surfaces](https://docs.microsoft.com/windows/mixed-reality/develop/unity/sampleapp-surfaces)
- [UWP Sample Apps that can be used for testing](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples)
