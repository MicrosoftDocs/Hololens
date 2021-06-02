---
title: Commercial features
description: Learn about the Microsoft HoloLens Commercial Suite features that make it easier for businesses to manage HoloLens devices. 
author: scooley
ms.author: scooley
ms.date: 08/26/2019
ms.custom: 
- CI 111456
- CSSTroubleshooting
ms.topic: article
audience: ITPro
ms.prod: hololens
ms.sitesec: library
ms.localizationpriority: high
ms.reviewer: 
manager: jarrettr
appliesto:
- HoloLens 2
keywords: HoloLens, commercial, features, mdm, mobile device management, kiosk mode
---

# Commercial features

HoloLens includes features that make it easier for businesses to manage HoloLens devices. Some features are included with the device, while others can be enabled by [Mobile Device Management (MDM) for HoloLens](hololens-mdm-configure.md)  or through [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) using [Windows Configuration Designer](https://www.microsoft.com/store/productId/9NBLGGH4TX22).


## Key commercial features

| I want to ... | Feature | Description | Included |Set by MDM | Set by Provisioning Packages 
|---------| ------------|------------|------------|-------| ----- |
Manage how my end users sign in.| [**Identity**](hololens-identity.md) | HoloLens supports several kinds of user identities - Azure AD, MSA, and local accounts.  |✔️  | | |
| Encrypt user data | [**Data security**](security-overview.md) | BitLocker data encryption is enabled on HoloLens to provide the same level of security protection as any other Windows device. | ✔️| | |
Minimize setup time for new users and devices | [**Autopilot**](https://docs.microsoft.com/hololens/hololens2-autopilot) | Administrators can configure the out-of-box experience (OOBE) in Microsoft Endpoint Manager and enable end users to prepare devices for business use with little to no interaction. |  | ✔️ |  |
| Control OS updates for my devices | [**Windows Update for Business**](hololens-updates.md#managing-updates-by-using-windows-update-for-business) | Windows Update for Business provides controlled operating system updates to devices and support for the long-term servicing channel. |  | ✔️ | ✔️ |
| Allow specific and LOB apps to be downloaded |[**Microsoft Store for Business**](app-deploy-store-business.md#microsoft-store-for-business) | Your IT department can also set up an enterprise private store, containing only your company's apps for your specific HoloLens usage. Securely distribute your enterprise software to selected group of enterprise users. | | ✔️ | ✔️ |
| Only show certain apps to users |[**Kiosk mode**](hololens-kiosk.md) |You can use HoloLens in demo or showcase experiences by using kiosk mode, to limit which apps can run. | | ✔️ | ✔️ |
| Manage device security with rules for apps and processes | [**Windows Defender Application Control**](https://docs.microsoft.com/hololens/windows-defender-application-control-wdac) | IT Admins can configure their devices to block the launch of apps on devices. | | ✔️ | ✔️ | 
| Configure the Settings page to show certain customizations |[**Page Settings Visibility**](https://docs.microsoft.com/hololens/settings-uri-list) | IT Admins can prevent specific pages in the System Settings app from being visible or accessible, or to do so for all pages except those specified. |  | ✔️ | ✔️ | 
| Manage how a device connects to the internet | [**Work access**](hololens-certificates-network.md) |Anyone in your organization can remotely connect to the corporate network through virtual private network (VPN) on a HoloLens. HoloLens can also access Wi-Fi networks that require credentials. | ✔️  |  | |
  
## Enabling commercial features

Your organization's IT admin can set up commercial features, such as Microsoft Store for Business, kiosk mode, and enterprise Wi-Fi access. [Planning HoloLens 2 deployment in a commercial environment](hololens-core-components.md) documentation provides step-by-step instructions for enrolling devices and installing apps from Microsoft Store for Business.

>[!VIDEO https://channel9.msdn.com/Shows/IT-Ops-Talk/HoloLens-2-Deployment-Overview/player]

## Recommended Content

- [CSPs supported in HoloLens 2 devices](https://docs.microsoft.com/windows/client-management/mdm/policies-in-policy-csp-supported-by-hololens2)
- [Microsoft Store For Business and line of business applications](https://docs.microsoft.com/hololens/app-deploy-overview)
- [Working with line-of-business apps](/microsoft-store/working-with-line-of-business-apps)
