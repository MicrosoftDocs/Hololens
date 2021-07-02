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

## HoloLens 2 Device (managed)

[Azure AD Account](https://docs.microsoft.com/azure/active-directory/)
> [!IMPORTANT]
> Active Directory (AD) cannot be used to manage HoloLens devices.

[Microsoft Intune](https://docs.microsoft.com/mem/intune/fundamentals/what-is-intune) or another MDM.
- [Windows Autopilot for HoloLens 2](https://docs.microsoft.com/hololens/hololens2-autopilot)- simplifies the provisioning experience for both IT admins and end users. IT admins can preconfigure HoloLens 2 policies, and upon first boot, devices will be deployed in business-ready state with zero end-user interaction. 
> [!NOTE]
> Windows Autopilot requires [Azure P1](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) and [Auto-enrollment](https://docs.microsoft.com/mem/intune/enrollment/windows-enroll#enable-windows-10-automatic-enrollment) to be configured first for the low-touch Autopilot flow and device deployment. 
### Business Use Case: 
- [Deployment Scenario A](hololens-requirements.md#scenario-a-deploy-to-cloud-connected-devices)
- [Deployment Scenario B](hololens-requirements.md#scenario-b-deploy-inside-your-organizations-network)

## HoloLens 2 Device-only (non-managed)

[Local Account](https://docs.microsoft.com/windows/security/identity-protection/access-control/local-accounts)
- This account must be [provisioned](hololens-provisioning.md#provisioning-package-hololens-wizard) ahead of time with Windows Configuration Designer (WCD).

[Microsoft Account (MSA)](https://docs.microsoft.com/windows/security/identity-protection/access-control/microsoft-accounts)

> [!WARNING]
> Multiple users are not supported for a device using either of these accounts.
### Business Use Case: 
- [Deployment Scenario C](hololens-requirements.md#scenario-c-deploy-in-secure-offline-environment)
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

- Azure AD account
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

