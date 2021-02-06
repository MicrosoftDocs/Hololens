---
title: HoloLens 2 Compliance and GDPR
description: GDPR documentation
keywords: HoloLens, GDPR, privacy, PII
author: joyjaz
ms.author: v-jjaswinski
ms.reviewer: skerewala, evmiller
ms.date: 02/05/2021
ms.prod: hololens
ms.topic: article
ms.sitesec: library
ms.localizationpriority: medium
audience: HoloLens
manager: yannisle
appliesto:
- HoloLens 2
---

# HoloLens 2 Privacy Statement

One of the core elements of the GDPR is ‘data protection by design’. This concept especially applies to mobile devices, like the HoloLens 2, because of their portability, unlimited internet connections and open communication channels. Resultingly, the HoloLens 2’s [security](https://docs.microsoft.com/hololens/security-architecture) has been redesigned to provide advanced, innovative security and privacy protection, end-to-end, incorporating both Microsoft’s approach to [privacy and GDPR regulations](https://privacy.microsoft.com/).

 [!NOTE]
This document does not apply to HoloLens 1.

## Privacy Overview

HoloLens 2 is a self-contained Windows computer, running Windows Holographic, that runs apps and solutions in an immersive mixed reality environment. It can be used as a secure offline device or deployed as a [managed device](https://docs.microsoft.com/mem/intune/fundamentals/windows-holographic-for-business) within your organization. See the following links to understand how the HoloLens 2 and Microsoft uses and protects your data;
1. [Microsoft Privacy Statement - HoloLens](https://privacy.microsoft.com/privacystatement) – expand the **Enterprise and developer** section in the left navigation menu and select **Enterprise and developer software and appliances**. Go to the **HoloLens** section.
2.	[Windows 10 and your online services](https://privacy.microsoft.com/windows10privacy)
3.	[Windows 10 & Privacy Compliance Guide](https://docs.microsoft.com/windows/privacy/windows-10-and-privacy-compliance)
4.	[Privacy and personal data in Intune](https://docs.microsoft.com/mem/intune/protect/privacy-personal-data)

## Network Security
Following the HoloLens 2 [Common Deployment Scenarios](https://docs.microsoft.com/hololens/common-scenarios), your data will be protected by [Azure’s world-class compliance](https://docs.microsoft.com/azure/compliance/) along with legal/regulatory standards integration. (If you are new to Azure AD and Dynamics 365 Remote Assist, reference the [Azure and Dynamics 365 accountability readiness checklist for the GDPR](https://docs.microsoft.com/compliance/regulatory/gdpr-arc-azure-dynamics))

Furthermore, Windows Defender Firewall delivers critical functionality to secure device connectivity. With HoloLens 2, the firewall is always enabled and there are no ways to disable it programmatically or through the UI. When the HoloLens 2 is deployed as a managed device using [Intune](https://docs.microsoft.com/mem/intune/protect/device-compliance-get-started), more compliance functionality is available with integration for [Endpoint with Microsoft Intune](https://docs.microsoft.com/mem/intune/protect/advanced-threat-protection) as a Mobile Threat Defense solution.

Learn more about the HoloLens 2 [security and architecture](https://docs.microsoft.com/hololens/security-architecture).

## OS Security
Updates are done automatically (by default) so your HoloLens 2 is always up to date with the latest release of Windows Holographic and any installed apps. Other new security features are;
1. [State separation and isolation](https://docs.microsoft.com/hololens/security-state-separation-isolation)
1. [Admin-less operating system](https://docs.microsoft.com/hololens/security-adminless-os)
1. [Limiting password use](https://docs.microsoft.com/hololens/security-limiting-password-use)

## Physical Security
HoloLens 2 has internal memory (2-GB RAM and 64 GB Flash Memory) that is protected by [BitLocker encryption](https://docs.microsoft.com/hololens/security-encryption-data-protection). Your device, and its local data, can be flashed offline using [Advanced Recovery Companion](https://www.microsoft.com/p/advanced-recovery-companion/9p74z35sfrs8#activetab=pivot:overviewtab) or remotely wiped via MDM if it has been deployed as a managed device.

## Data Protection
[TPM and UEFI](https://docs.microsoft.com/hololens/security-hardware-backed-integrity) are enforced so the device only boots to Windows trusted platforms. Windows updates are run automatically (by default) and [Azure integration](https://docs.microsoft.com/azure/security/fundamentals/encryption-overview) protects data traveling between itself and the cloud. 

When deploying HoloLens 2 to external clients, [Dynamics 365 Remote Assist](https://docs.microsoft.com/hololens/hololens2-deployment-guide) ensures your sensitive company data and resources are both separate and safe. 

During the OOBE, the sharing of diagnostic data with Microsoft can be manually configured by the user. There are two choices: Full diagnostic data and Basic diagnostic data. (Some diagnostic data may contain PII) If Basic diagnostic data is originally chosen and then needs to be changed at a later time for troubleshooting purposes, the setting can be changed in **Settings | Privacy | Diagnostics & Feedback**. 

 [!Important]
Device diagnostic logs contain personally identifiable information (PII), such as about what processes or applications the user starts during typical operations. When multiple users share a HoloLens device (for example, users sign in to the same device by using different Microsoft Azure Active Directory (Azure AD) accounts) the diagnostic logs may contain PII information that applies to multiple users.

There are [several collection methods and data retention policies](https://docs.microsoft.com/hololens/hololens-diagnostic-logs) for gathering diagnostic data from the HoloLens 2.  For more information about how Microsoft collects and uses diagnostic data, see [Microsoft Privacy Statement - Diagnostics](https://privacy.microsoft.com/privacystatement) - expand **Windows** in the left navigation menu and select **Diagnostics**. Go to the **Diagnostics** section.
