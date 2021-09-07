---
title: Provisioning Package
description: Learn about app packaging, provisioning, deployment, and enterprise app deployment for HoloLens devices.
keywords: app, app deployment, enterprise app deployment, provisioning 
author: evmill
ms.author: v-evmill
ms.date: 6/22/2020
ms.prod: hololens
ms.sitesec: library
ms.topic: article
ms.localizationpriority: medium
audience: HoloLens
manager: yannisle
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Provisioning Package

Provisioning packages can be used to prepare and configure devices in an environment without access to endpoint management. They can also be deployed to a device regardless of identity of the user, enrollment status, during the Out of Box Experience (OOBE), or by [applying a provisioning package during setup](/hololens/hololens-provisioning##apply-a-provisioning-package-to-hololens-during-setup).

## Provisioning Packages considerations

* Non-Public apps
* USB side-load only
* No auto update (requires manual updates via PPKGs)

Apps installed via a provisioning package must be signed by a certificate in the local machine store. Provisioning packages can only install certificates to the device (local machine) store. Therefore an app and a certificate may be installed via the same provisioning package. If you are deploying your certificate from MDM or installing via the [Certificate Manager](certificate-manager.md), make sure to deploy the certificate to the local machine store to sign apps installed this way.

To learn the basics of creating a Provisioning Package for HoloLens devices, visit [HoloLens Provisioning](/hololens/hololens-provisioning). To deploy an app, you must start with advanced provisioning.

> [!NOTE]
> HoloLens (1st gen) has limited support installing apps (**UniversalAppInstall**) by using a provisioning package. HoloLens (1st gen) devices only support installing an app via PPKG only during OOBE and only with user context installs.

## Setup

Within [Windows Configuration Designer,](https://www.microsoft.com/store/productId/9NBLGGH4TX22) take following four steps.

1. Set ApplicationManagement/AllowAllTrustedApps To “Yes”. See: [ApplicationManagement/AllowAllTrustedApps](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowalltrustedapps).

2. Navigate to **UniversalAppInstall** > **UserContextApp** enter the **PackageFamilyName**. See [UniversalAppInstall](/windows/configuration/wcd/wcd-universalappinstall).

   You can use Device Portal on a device you have already installed your app to. Visit the Apps page, and look at the PackageRelativeID line, all the information before the "!" Is your **PackageFamilyName**.

3. You will then see that you have a new section, **ApplicationFile**. Use this area to upload your appx bundle.

4. Depending on if you have purchased your app or built your own LOB app, you will need to upload the license file or security certificate.

    - For license file: navigate to **UniversalAppInstall** > **UserContextAppLicence** and enter your license product ID. A new section <b>LicenseProductID:</b><i>yourlicenseproductid</i> will be created, select this new section and browse to the location of your license and upload it.
        - See [UserContextAppLicense](/windows/configuration/wcd/wcd-universalappinstall#usercontextapplicense).
    - For the security file, navigate to **Certificates** and select your certificate to install alongside your .appx bundle.

Make sure to save your project to a secure location. Then **Export** it as a **Provisioning Package**.  

See also: [Apply your provisioning package to HoloLens](/hololens/hololens-provisioning#apply-a-provisioning-package-to-hololens-during-setup).
