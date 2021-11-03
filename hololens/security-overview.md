---
title: HoloLens security overview
description: Get started with an overview of security for HoloLens mixed reality devices. 
author: beelia
ms.author: v-beehanson
ms.reviewer: evmill
ms.date: 11/03/2021
ms.topic: article
keywords: security, hololens, hololens 2, hololens2 security, security overview
ms.prod: hololens
ms.sitesec: library
ms.localizationpriority: high
manager: yannisle
appliesto:
- HoloLens 2
---

# Security overview

The HoloLens 2 security architecture has been designed to provide advanced, innovative security and privacy protection, end-to-end. Security capabilities of the HoloLens 2 meets the challenges of a modern threat landscape and its associated risks. Here, we answer common questions and share different ways to secure Microsoft HoloLens 2 devices.

With HoloLens 2, businesses and customers have a truly modern and cutting-edge operating system with a strong built-in security framework. This contemporary operating system allows developers to design, build, and deliver applications with an exceptional security strategy, that effectively combat a complex threat landscape and its associated risks. With HoloLens, you’ll use the built-in power and security of both Microsoft Azure and Microsoft Edge. HoloLens is designed and manufactured to mitigate exposure to any risks.

**HoloLens is a Windows device**. You’ll use the same and familiar processes and procedures of Windows Device Configuration Manager, mobile device management, and Azure Active Directory. You’ll find that you aren’t adding a bunch of new systems to what already exists.

Some of the familiar security features include: 

* **BitLocker** protects data from unauthorized access by encrypting your drive and requiring one or more factors of authentication before it will unlock it. 
* **TPM** enhances computer security and privacy through encryption and decryption, protecting authentication credentials and proving which software is running. 
* **Microsoft Defender SmartScreen** helps you identify reported phishing and malware websites and also helps you make informed decisions about downloads.

HoloLens integrates well with your ecosystem. As most corporate environments are hybrid, HoloLens works well for authentication and access management. 
 
HoloLens works in the way you intend. Microsoft has earned the trust of our clients for decades. You can be sure that HoloLens both protects confidentiality and doesn’t hamper information disclosure.

**HoloLens is an edge device**. The security requirements of the device inherit the security requirements of the environment in which it operates. In short, no matter how secure it is, it’s all for naught if the backend to its services is vulnerable. That’s why the HoloLens industrial edition is perfect for use in highly regulated industries.

The following security chapters present an overview of our evolving Windows HoloLens 2 security, which enables developers to successfully build more secure high-performance applications. These sections describe the Windows HoloLens 2 operating system security architecture, its secure locations, related security features, and mechanisms. Here are the security items to review for HoloLens:

| Scenario | Topic | Description |
|---------|---------|---------|
| Ensure the integrity of stored data | [Security overview and architecture](security-architecture.md) | The HoloLens 2 security architecture offers secure storage locations and advanced security elements. |
| Protect the device from untrusted apps, malware, viruses, or booting from removeable media | [State separation and isolation](security-state-separation-isolation.md) | Digital signing code ensures that only Signed Firmware updates are completed, preventing activities like Debug over USB from being installed. |
| Protect against threats before or during runtime | [Hardware-backed integrity and runtime attestation](security-hardware-backed-integrity.md) | Unified Extensible Firmware Interface (UEFI) Secure Boot detects and prevents attempts to tamper with firmware through bluetooth, wifi, or Ethernet. It includes strong encryption for Trusted Platform Modules (TPMs). |
| Minimize the surface area for privilege escalation with better administration | [Admin-less operating system](security-adminless-os.md) | HoloLens disabled support for the Administrators group and limits all third-party UWP application code. |
| Protect data when devices are lost and/or stolen | [Encryption and data protection](security-encryption-data-protection.md) | Encryption and Data Protection prevents unauthorized applications from accessing sensitive information. |
| Remove network vulnerabilities and ensure secure/encrypted connectivity | [Network security](security-network-security.md) | With HoloLens 2, the firewall is always enabled, and there is no way to disable it, either programmatically or through the UI. |

You may be a security or IT professional, business decision-maker, or a member of an innovation team looking to adopt HoloLens within your organization. As you build from proof of concept to a scaled deployment, our security strategies will help you deploy HoloLens within your IT infrastructure safely. The following security scenarios are the most common:

| Scenario | Topic | Description |
|---------|---------|---------|
| Apply critical security updates to the device as they become available | [Update HoloLens 2](hololens-update-hololens.md#types-of-updates) | Check for updates or apply them automatically. |
| Ensure privacy and data protection for my customers (for example, GDPR) | [HoloLens 2 Privacy and Data Protection](hololens2-privacy.md) | HoloLens 2 security has been redesigned to provide advanced, innovative security and privacy protection, incorporating Microsoft’s approach to privacy and GDPR regulations.|
| Permanently delete sensitive data | [Restart, reset, or recover HoloLens](hololens-recovery.md#clean-reflash-the-device) | Any data stored on the unit can be cleared using a full device reset or reflash. |
| Back up HoloLens to the cloud | [Find, open, and save files on HoloLens](holographic-data.md#sync-to-the-cloud) | Save HoloLens files and data to OneDrive. |
| Transmit data via wifi | [Encryption and data protection](security-encryption-data-protection.md#azure-integration) | Auto-upload to the cloud with OneDrive |
| Lock screen with auto-logoff | [Share HoloLens with multiple users](hololens-multiple-users)| Pressing headset power key invokes standby mode |
| Reconfigure product security capabilities | [Page Settings Visibility](settings-uri-list.md) | PageVisibilityList policy can be reset to restrict the pages seen within the Settings app. |
| Get in touch with Microsoft Security Engineering teams | [Security engineering](security-engineering.md) | Microsoft has several resources and teams devoted to optimizing the company’s engineering protocols, addressing compliance, and ensuring customer trust. |
| Use modern security and authentication methods | [Limiting password use](security-limiting-password-use.md) | HoloLens 2 enables strong, hardware-backed “password-less” credentials for device sign in. |
| Authenticate HoloLens users | [Manage user identity and login for HoloLens](hololens-identity.md) | When using AAD, users are required to use Windows Hello for Business and use a device PIN or biometric (iris) for login to the device. AAD identity information is not stored locally on the device.
| Authenticate users through an external authentication service | [Hybrid identity documentation](/azure/active-directory/hybrid/) | Single user identities for authentication and authorization can be created for all resources, regardless of location.
| Ensure cloud application deployment readiness | [Azure operational security checklist](/azure/security/fundamentals/operational-checklist) | This checklist will help you determine if your application meets essential operational security recommendations. |
| Optimize my environment for Mobile Device Management with Intune | [Use security baselines to configure Windows 10 devices in Intune](/mem/intune/protect/security-baselines) | Intune's security baselines are pre-configured groups of Windows settings that will help you quickly apply the settings recommended for your users and devices. |
| Reconfigure login inactivity or auto-logoff and define user account passwords | [Policy CSP - DeviceLock](/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxinactivitytimedevicelock) | DeviceLock time periods can be reset. |
