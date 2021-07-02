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
- This account must be [provisioned](hololens-provisioning.md##provisioning-package-hololens-wizard) ahead of time with Windows Configuration Designer (WCD).

[Microsoft Account (MSA)](https://docs.microsoft.com/windows/security/identity-protection/access-control/microsoft-accounts)

> [!WARNING]
> Multiple users are not supported for a device using either of these accounts.


## HoloLens 2 Device (managed)

[Azure AD Account](https://docs.microsoft.com/azure/active-directory/)

[Microsoft Intune](https://docs.microsoft.com/mem/intune/fundamentals/what-is-intune)

## Mobile Device Management (MDM) Licenses Guidance

If you plan on managing your HoloLens devices, you will need Azure AD and an MDM. 
> [!IMPORTANT]
> Active Directory (AD) cannot be used to manage HoloLens devices.


If you are planning on or using an MDM other than Intune, an [Azure Active Directory License](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-whatis#what-are-the-azure-ad-licenses) is required.

If you are planning on using Intune as your MDM, read up on the [list of suites](https://docs.microsoft.com/intune/fundamentals/licenses) that include Intune licenses. **Please note that Azure AD is included in the majority of these suites.**

## Dynamics 365 Licensing and Requirements

### Dynamics 365 Remote Assist 

#### Admin
- Azure AD account (required for purchasing the subscription and assigning licenses)
- [Remote Assist subscription](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/buy-and-deploy-remote-assist) (or [Remote Assist Trial](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/try-remote-assist))
    
#### Dynamics 365 Remote Assist user

- Azure AD account
- Remote Assist license 
> [!NOTE]
> Microsoft Teams is bundled with Remote Assist
- Network Connectivity

#### Microsoft Teams user

- Microsoft Teams or [Teams Freemium](https://products.office.com/microsoft-teams/free).
- Network connectivity

If you plan on implementing this [cross-tenant scenario](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/cross-tenant-overview#scenario-2-leasing-services-to-other-tenants), you may need an Information Barriers license. See [this article](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/cross-tenant-licensing-implementation#step-1-determine-if-information-barriers-are-necessary) to determine if an Information Barrier License is required.

### Dynamics 365 Guides 

#### Admin
- Azure AD account (required for purchasing the subscription and assigning licenses)
- Dynamics 365 [Guides subscription or free trial](https://docs.microsoft.com/dynamics365/mixed-reality/guides/setup-step-one)

#### Guides Author
1. Azure AD account
1. Dynamics 365 Guides license
1. Dynamics 365 Guides application installed on a PC or HoloLens
1. [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (used to view the Analytics dashboard)
1. Author role (for creating guides)
1. Network Connectivity

#### Guides User

1. Azure AD account
1. Dynamics 365 Guides license
1. Dynamics 365 Guides app installed on a HoloLens
1. Operator role (for testing or using guides)
1. Network Connectivity

