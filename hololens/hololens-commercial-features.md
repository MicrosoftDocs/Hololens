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
- HoloLens (1st gen)
- HoloLens 2
keywords: HoloLens, commercial, features, mdm, mobile device management, kiosk mode
---

# Commercial features

HoloLens includes features that make it easier for businesses to manage HoloLens devices.

Every HoloLens 2 device has commercial features available.

HoloLens (1st gen) came with two licensing options, the developer license and a commercial license. To unlock HoloLens's commercial capabilities, upgrade from the developer license to a commercial license. To purchase the Microsoft HoloLens Commercial Suite, contact your local Microsoft account manager.

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

## Key commercial features

- **Kiosk mode.** You can use HoloLens in demo or showcase experiences by using kiosk mode, to limit which apps can run.

  ![Using kiosk mode, HoloLens launches directly into the app of your choice.](images/201608-kioskmode-400px.png)

- **Mobile Device Management (MDM) for HoloLens.** Your IT department can manage multiple HoloLens devices simultaneously by using solutions such as Microsoft Intune. You can manage settings, select apps to install, and set security configurations that are tailored to your organization's needs.

  ![Mobile Device Management on HoloLens provides enterprise-grade device management across multiple devices.](images/201608-enterprisemanagement-400px.png)

- **Windows Update for Business.** Windows Update for Business provides controlled operating system updates to devices and support for the long-term servicing channel.
- **Data security.** BitLocker data encryption is enabled on HoloLens to provide the same level of security protection as any other Windows device.
- **Work access.** Anyone in your organization can remotely connect to the corporate network through virtual private network (VPN) on a HoloLens. HoloLens can also access Wi-Fi networks that require credentials.
- **Microsoft Store for Business.** Your IT department can also set up an enterprise private store, containing only your company's apps for your specific HoloLens usage. Securely distribute your enterprise software to selected group of enterprise users.

## Feature comparison between editions

|Features |HoloLens Development Edition |HoloLens Commercial Suite |HoloLens 2 |
|---|:---:|:---:|:---:|
|Device Encryption (BitLocker) | |✔️ |✔️ |
|Virtual Private Network (VPN) | |✔️ |✔️ |
|[Kiosk mode](hololens-kiosk.md) | |✔️ |✔️ |
|**Management and deployment** | | | |
|Mobile Device Management (MDM) | |✔️ |✔️ |
|Ability to block unenrollment | |✔️ |✔️ |
|Cert-based corporate Wi-Fi access | |✔️ |✔️ |
|Microsoft Store (Consumer) |Consumer |Filter by using MDM |Filter by using MDM |
|[Business Store Portal](https://docs.microsoft.com/microsoft-store/working-with-line-of-business-apps) | |✔️ |✔️ |
|**Security and identity** | | | |
|Sign in by using Azure Active Directory (Azure AD) account |✔️ |✔️ |✔️ |
|Sign in by using Microsoft Account (MSA) |✔️ |✔️ |✔️ |
|Next Generation Credentials with PIN unlock |✔️ |✔️ |✔️ |
|[Secure boot](https://docs.microsoft.com/windows-hardware/design/device-experiences/oem-secure-boot) |✔️ |✔️ |✔️ |
|**Servicing and support** | | | |
|Automatic system updates as they arrive |✔️ |✔️ |✔️ |
|[Windows Update for Business](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb) | |✔️ |✔️ |
|Long-Term Servicing Channel (LTSC) | |✔️ |✔️ |

## Enabling commercial features

Your organization's IT admin can set up commercial features such as Microsoft Store for Business, kiosk mode, and enterprise Wi-Fi access. The [Microsoft HoloLens](index.yml) documentation provides step-by-step instructions for enrolling devices and installing apps from Microsoft Store for Business.

## See also

- [Microsoft HoloLens](index.yml)
- [Kiosk mode](hololens-kiosk.md)
- [CSPs supported in HoloLens devices](/windows/client-management/mdm/configuration-service-provider-reference#csps-supported-in-hololens-devices)
- [Microsoft Store For Business and line of business applications](https://blogs.technet.microsoft.com/sbucci/2016/04/13/windows-store-for-business-and-line-of-business-applications/)
- [Working with line-of-business apps](/microsoft-store/working-with-line-of-business-apps)
