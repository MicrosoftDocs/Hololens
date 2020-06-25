---
title: Provisioning Package
description: app, app deployment, enterprise app demployment, provisioning 
keywords: app, app deployment, enterprise app demployment, provisioning 
author: v-jodben
ms.date: 6/22/2020
ms.prod: hololens
ms.topic: article
ms.sitesec: library
ms.topic: article
ms.localizationpriority: medium
audience: HoloLens
manager: yannisl
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Provisioning Package

Provisioning Packages can be used to manage CSP and Policies in an environment that does not have access to MDM. They can also be deployed to a device regardless of identity of the user, enrollment status, during the Out of Box Experience (OOBE), or by [applying a provisioning package during setup](https://docs.microsoft.com/hololens/hololens-provisioning##apply-a-provisioning-package-to-hololens-during-setup).

## Provisioning Packages have the following limitations:
* Non-Public apps
* USB side-load only
* No auto update (requires manual updates via PPKGs)

> [!NOTE] 
> To learn the basics of creating a Provisioning Package for HoloLens devices, visit [HoloLens Provisioning](https://docs.microsoft.com/hololens/hololens-provisioning). To deploy an app, you must start with advanced provisioning. 

## Setup

Within [Windows Configuration Designer](https://www.microsoft.com/store/productId/9NBLGGH4TX22) take following 4 steps.

1. Set ApplicationManagement/AllowAllTrustedApps To “Yes”. See: [ApplicationManagement/AllowAllTrustedApps](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowalltrustedapps)
2. Under **UniversalAppInstall** > **UserContextApp** please enter the **PackageFamilyName**. 
- If you don’t know this, you can use Device Portal on a device you have already installed your app to. Visit the Apps page, and look at the PackageRelativeID line, all the information before the "!" Is your **PackageFamilyName**.
3. You will then see that you have a new section, **ApplicationFile**. Use this area to upload your appx bundle. 
4. Depending on if you have purchased your app or built your own LOB app, you will need to upload the license file or security certificate. 
- For license file: Under **UniversalAppInstall** > **UserContextAppLience** and browse to the location of your license and upload it. 
- For security file navigate to **Certificates** and select your certificate to install alongside your .appx bundle. 

Make sure to save your project to a secure location. Then **Export** it as a **Provisioning Package**.  
    
See also: [Apply your provisiong package to HoloLens](https://docs.microsoft.com/hololens/hololens-provisioning#apply-a-provisioning-package-to-hololens-during-setup).
