---
title: Intune and Company Portal
description: intune, app management, app, company portal, portal
keywords: intune, app management, app, company portal, portal, hololens
author: v-jodben
ms.date: 6/22/2020
ms.prod: hololens
ms.custom: 
- CI 111456
- CSSTroubleshooting
ms.topic: article
ms.sitesec: library
ms.localizationpriority: medium
audience: HoloLens
manager: yannisl
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Intune & Company Portal

With Mobile Device Management (MDM), you can use your own custom apps through [Microsoft Intune](https://docs.microsoft.com/intune/windows-holographic-for-business) to deploy it directly to your HoloLens devices. Microsoft Intune is a cloud-based service that focuses on mobile device management (MDM) and mobile application management (MAM). Intune is included in Microsoft's [Enterprise Mobility + Security (EMS) suite](https://www.microsoft.com/microsoft-365/enterprise-mobility-security), and enables users to be productive while keeping your organization data protected. To learn more about Intune, please read [What is Intune](https://docs.microsoft.com/mem/intune/fundamentals/what-is-intune).

## Setup

1. Upload an app to a Line of Business, or upload a custom app to your Intune tenant. See also: [Enterprise app management](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management).

> [!NOTE] 
> When building your appx bundle make sure to account for including the architecture for the device(s) that you are deploying to. HoloLens 2 is ARM64, and HoloLens (1st Gen) is x86. You may include both in a single appx bundle if you plan on having a mixed devices environment.

2. [Assign your app to a group](https://docs.microsoft.com/mem/intune/apps/apps-deploy). Based on the assignment type you choose you can have the app delivered automatically or available to be readily pulled down if you have a selection of apps. 

## Assignment types

If you prefer your app to be automatically installed on the device after enrollment, you should select **Required** for that group(s).
If you prefer to make your app available for download to those enrolled through the company portal, select **Available for enrolled devices**.


## End User Experience

After you have set up configuration on Intune: 

Follow these steps to automatically get your app(s):
1. Enroll your device with your tenant. 
2. Once your device has completed enrollment, you should receive the app on your device. 
3. If you are not seeing you app immediately, go to **Settings** > **Accounts** > **Work or School** > **youraccount** Info, and scroll down to see information on installed app status.

How to get to apps through the Company Portal:
1. Open the **Start Menu** and select **Microsoft Store**. 
2. Search for **Company Portal** and download the app.
3. Sign into your account.
4. Select the app you wish to receive and download it.

> [!Tip]
> Learn more about [auto-installing the Company Portal](https://docs.microsoft.com/mem/intune/apps/company-portal-app) and [deploying and managing apps in Intune](https://docs.microsoft.com/mem/intune/fundamentals/windows-holographic-for-business#deploy-and-manage-apps).
