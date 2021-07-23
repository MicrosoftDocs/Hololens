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

## Overview
This page provides a high-level overview of the licenses and accounts needed to deploy both managed and unmanaged HoloLens 2 devices in your organization. It also includes information for licensing of Dynamics 365 [Remote Assist](#dynamics-365-remote-assist) and [Guides](#dynamics-365-guides).

## HoloLens 2 license and account requirements

 
|       &nbsp;      | Managed HoloLens | Unmanaged HoloLens |
|-------------------|-----------------|---------------------|
| **Business Use Case** | | |
| [Deploy to cloud connected devices - proof of concept/pilot deployment](hololens-requirements.md#scenario-a-deploy-to-cloud-connected-devices)  | ✔️| |
| [Deploy inside your organization's network - deployment at scale](hololens-requirements.md#scenario-b-deploy-inside-your-organizations-network) | ✔️| |
| [Deploy in secure offline environment](hololens-requirements.md#scenario-c-deploy-in-secure-offline-environment) | | ✔️ |
| **Licenses** | | |
| Azure Active Directory | ✔️ | |
| MDM (Intune<sup>1</sup> or <sup>2</sup>) | ✔️  | |
| **Accounts** |  | |
| Azure AD Admin account | ✔️ |  |
| Azure AD User account | ✔️ | |
| [Microsoft Account (MSA)](/windows/security/identity-protection/access-control/microsoft-accounts)| | ✔️ |
| [Local Account](/windows/security/identity-protection/access-control/local-accounts)<sup>3</sup> | | ✔️ |
- <sup>1</sup> [Auto-enrollment](/mem/intune/enrollment/windows-enroll#enable-windows-10-automatic-enrollment) during initial device setup, which registers and joins Azure Active Directory and allows the device to be managed with Intune.
- <sup>2</sup> [Windows Autopilot for HoloLens 2](hololens2-autopilot.md) simplifies the provisioning experience for both IT admins and end users. IT admins can preconfigure HoloLens 2 policies, and upon first boot, devices will be deployed in business-ready state with zero end-user interaction.
- <sup>3</sup> This account must be [provisioned](hololens-provisioning.md#provisioning-package-hololens-wizard) ahead of time with Windows Configuration Designer (WCD).

> [!IMPORTANT]
> Active Directory (AD) cannot be used to manage HoloLens devices.
 
> [!WARNING]
> Multiple users are not supported for a device using either a MSA or local account.

## Dynamics 365 Licensing and Requirements

### Dynamics 365 Remote Assist 

#### Admin

- Azure AD account (required for purchasing the subscription and assigning licenses)
- [Remote Assist subscription](/dynamics365/mixed-reality/remote-assist/buy-and-deploy-remote-assist) (or [Remote Assist Trial](/dynamics365/mixed-reality/remote-assist/try-remote-assist))
    
#### Dynamics 365 Remote Assist user

- Azure AD account

- Remote Assist license 

  > [!NOTE]
  > Microsoft Teams is bundled with Remote Assist

- Network Connectivity

#### Microsoft Teams user

- Azure AD account

- Microsoft Teams or [Teams Freemium](https://products.office.com/microsoft-teams/free)

- Network connectivity

If you plan on implementing this [cross-tenant scenario](/dynamics365/mixed-reality/remote-assist/cross-tenant-overview#scenario-2-leasing-services-to-other-tenants), you may need an Information Barriers license. See [this article](/dynamics365/mixed-reality/remote-assist/cross-tenant-licensing-implementation#step-1-determine-if-information-barriers-are-necessary) to determine if an Information Barrier License is required.

### Dynamics 365 Guides 

#### Admin

1. Azure AD account (required for purchasing the subscription and assigning licenses)
2. Dynamics 365 [Guides subscription or free trial](/dynamics365/mixed-reality/guides/setup-step-one)

#### Guides Author

1. Azure AD account
1. [Dynamics 365 Guides license](/dynamics365/mixed-reality/guides/requirements)
1. Dynamics 365 Guides application installed on a PC or HoloLens
1. [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (used to view the Analytics dashboard)
1. Author role (for creating guides)
1. Network Connectivity

#### Guides User

1. Azure AD account
1. [Dynamics 365 Guides license](/dynamics365/mixed-reality/guides/requirements)
1. Dynamics 365 Guides app installed on a HoloLens
1. Operator role (for testing or using guides)
1. Network Connectivity
