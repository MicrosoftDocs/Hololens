---
title: Prepare HoloLens 2 to deploy in a commercial environment
description: Learn more about preparing HoloLens to deploy in enterprise environments, including infrastructure, azure active directory, and mobile device management.
ms.prod: hololens
ms.sitesec: library
ms.assetid: 88bf50aa-0bac-4142-afa4-20b37c013001
author: bogenera
ms.author: bogenera
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
ms.date: 11/04/2020
appliesto:
- HoloLens 2
---

# Prepare for the enterprise deployment

As you prepare to deploy HoloLens 2 to your corporate enterprise environment, there are several considerations that should be reviewed and understood as you begin to plan for scale deployments of HoloLens 2.

## Infrastructure Essentials

For HoloLens 2 in a corporate enterprise deployment scenario, there are certain essential infrastructure services required to support the full set of capabilities. HoloLens 2 was built with [Modern Mobile Device Management](https://www.microsoft.com/itshowcase/managing-windows-10-devices-with-microsoft-intune) in mind for deployment and management. With Azure AD Join + MDM as the primary means of achieving that in an ever-increasing mobile workforce. The below topics provide a brief overview of each infrastructure component that should be considered in your deployment planning for HoloLens 2.

## Azure Active Directory
Azure AD is a cloud-based directory service that provides identity and access management. You can integrate it with existing on-premises directories to create a hybrid identity solution. Organizations that use Microsoft Office 365 or Intune are already using Azure AD, which has three editions: Free, Premium P1, and Premium P2 (see [Azure Active Directory editions](https://azure.microsoft.com/documentation/articles/active-directory-editions/)). All editions support Azure AD device registration, but Premium P1 is required to enable MDM auto-enrollment. HoloLens 2 requires Azure Active Directory Join to enable most enterprise level features and functionality.

> [!NOTE]
> On premises Active Directory Join is not supported on HoloLens 2.

## Mobile Device Management
HoloLens 2 is designed specifically to be managed by Mobile Device Management (MDM) systems in an enterprise environment. Microsoft [Intune](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/microsoft-intune), part of the Enterprise Mobility + Security, is a cloud-based MDM system that manages devices in the enterprise. Like Office 365, Intune uses Azure AD for identity management, so employees use the same credentials to enroll devices in Intune that they use to sign into Office 365. Multiple MDM systems support Windows 10 and most support personal and corporate device deployment scenarios. MDM systems can also manage application deployments and updates for the HoloLens 2 as well. Other MDM providers that support HoloLens 2 currently include: AirWatch, MobileIron, and others. All MDM system vendors have equal access to Windows 10 device management configuration service providers (CSP)s, giving IT organizations the freedom to select whichever system best fits their management requirements, whether Microsoft Intune or a third-party MDM product.

> [!NOTE]
> Traditional on premises PC management systems like System Center Configuration Manager are not supported on HoloLens 2.

## Windows Update for Business
Microsoft designed Windows Update for Business to provide IT administrators with additional Windows Update-centric management capabilities, such as the ability to deploy updates to groups of devices and to define maintenance windows for installing updates. See the [HoloLens updates](https://docs.microsoft.com/hololens/hololens-updates) documentation for details on managing HoloLens 2 updates.

## Certificates
HoloLens 2 supports deployment of certificates through MDM if your environment requires certificates for Corp Wi-Fi network authentication or access to other resources. Some MDM infrastructure configurations may be required to enable certificate deployments to HoloLens 2. Read about how to [prepare certificates and network profiles for HoloLens 2](https://docs.microsoft.com/hololens/hololens-certificates-network). If you're using Intune, check out the [certification configuration](https://docs.microsoft.com/mem/intune/protect/certificates-configure) details.

Get started by reviewing HoloLens 2 deployment requirements and scenarios across a range of IT infrastructure configurations.

> [!div class="nextstepaction"]
> [Common Deployment Scenarios](common-scenarios.md)
