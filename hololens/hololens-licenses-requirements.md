---
title: License requirements
description: Keep up to date with all the licensing requirements and guidelines you need for mobile device management, HoloLens, and Remote Assist.
ms.prod: hololens
ms.sitesec: library
author: pawinfie
ms.author: pawinfie
audience: HoloLens
ms.topic: article
ms.localizationpriority: high
ms.date: 1/23/2020
ms.reviewer: 
manager: bradke
appliesto:
- HoloLens 2
---

# License requirements

## HoloLens 2 Device-only (non-managed)

[Local Account](https://docs.microsoft.com/windows/security/identity-protection/access-control/local-accounts)

[Microsoft Account (MSA)](https://docs.microsoft.com/windows/security/identity-protection/access-control/microsoft-accounts)

> [!WARNING]
> Multiple users are not supported for a device using either of these accounts.


## HoloLens 2 Device (managed)

[Azure AD Account](https://docs.microsoft.com/azure/active-directory/)

## Mobile Device Management (MDM) Licenses Guidance

If you plan on managing your HoloLens devices, you will need Azure AD and an MDM. 
> [!IMPORTANT]
> Active Directory (AD) cannot be used to manage HoloLens devices.


If you are planning on or using an MDM other than Intune, an [Azure Active Directory License](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) is required.

If you are planning on using Intune as your MDM, read up on the [list of suites](https://docs.microsoft.com/intune/fundamentals/licenses) that include Intune licenses. **Please note that Azure AD is included in the majority of these suites.**

## Identify the licenses needed for your scenario and products

### Remote Assist License Requirements

Make sure you have the required licensing and device, which you can check in the [requirements](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/requirements) documentation.

1. [Remote Assist License](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/buy-and-deploy-remote-assist)
    1. Or try a [Remote Assist trial](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/try-remote-assist)
1. [Teams Freemium/Teams](https://products.office.com/microsoft-teams/free)
1. [Azure Active Directory (Azure AD) License](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)

If you plan on implementing **[this cross-tenant scenario](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/cross-tenant-overview#scenario-2-leasing-services-to-other-tenants)**, you may need an Information Barriers license. Please see [this article](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/cross-tenant-licensing-implementation#step-1-determine-if-information-barriers-are-necessary) to determine if an Information Barrier License is required.

### Guides License Requirements

Check out the [updated licensing and device requirements](https://docs.microsoft.com/dynamics365/mixed-reality/guides/requirements).

1. [Azure Active Directory (Azure AD) License](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)
1. Dynamics 365 Guides applications PC and HoloLens
1. Dynamics 365 [Guides subscription]((https://docs.microsoft.com/dynamics365/mixed-reality/guides/setup))
    1. Microsoft Dataverse (included)
    1. Power Apps (included)
1. [Power BI Desktop](https://powerbi.microsoft.com/desktop/)
1. Network Connectivity
