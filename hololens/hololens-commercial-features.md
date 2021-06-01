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

HoloLens includes features that make it easier for businesses to manage HoloLens devices. Some features are included with the device, while others can be enabled by MDM or WCD.

- [**Data security.**](security-overview.md) | BitLocker data encryption is enabled on HoloLens to provide the same level of security protection as any other Windows device.
- [**Work access.**](hololens-certificates-network.md#prepare-certificates-and-network-profiles-for-holoLens-2) Anyone in your organization can remotely connect to the corporate network through virtual private network (VPN) on a HoloLens. HoloLens can also access Wi-Fi networks that require credentials.

## Key commercial features

| Feature | Description | Set by MDM | Set by WCD | Use case |
|---------| ------------|------------|------------| ---------|
| [**Mobile Device Management (MDM) for HoloLens.**](hololens-mdm-configure.md) | Your IT department can manage multiple HoloLens devices simultaneously by using solutions, such as Microsoft Intune. You can manage settings, select apps to install, and set security configurations that are tailored to your organization's needs. | ✔️ | | |
[**Windows Update for Business.**](hololens-updates.md#managing-updates-by-using-windows-update-for-business) | Windows Update for Business provides controlled operating system updates to devices and support for the long-term servicing channel. | ✔️ | ✔️ | |
|[**Microsoft Store for Business.**](app-deploy-store-business.md#microsoft-store-for-business) | Your IT department can also set up an enterprise private store, containing only your company's apps for your specific HoloLens usage. Securely distribute your enterprise software to selected group of enterprise users. |✔️ | ✔️ | |
|[**Kiosk mode.**](hololens-kiosk.md) |You can use HoloLens in demo or showcase experiences by using kiosk mode, to limit which apps can run. |✔️ | ✔️ | |

  


## Enabling commercial features

Your organization's IT admin can set up commercial features, such as Microsoft Store for Business, kiosk mode, and enterprise Wi-Fi access. [Planning HoloLens 2 deployment in a commercial environment](hololens-core-components.md) documentation provides step-by-step instructions for enrolling devices and installing apps from Microsoft Store for Business.

>[!VIDEO https://channel9.msdn.com/Shows/IT-Ops-Talk/HoloLens-2-Deployment-Overview/player]

## See also

- [CSPs supported in HoloLens 2 devices](https://docs.microsoft.com/windows/client-management/mdm/policies-in-policy-csp-supported-by-hololens2)
- [Microsoft Store For Business and line of business applications](https://blogs.technet.microsoft.com/sbucci/2016/04/13/windows-store-for-business-and-line-of-business-applications/)
- [Working with line-of-business apps](/microsoft-store/working-with-line-of-business-apps)
