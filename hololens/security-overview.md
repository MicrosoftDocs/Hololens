---
title: HoloLens security overview
description: Get started with an overview of security for HoloLens mixed reality devices. 
author: beelia
ms.author: v-beehanson
ms.reviewer: evmill
ms.date: 10/18/2021
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

You may be a security or IT professional, business decision-maker, or a member of an innovation team looking to adopt HoloLens within your organization. As you build from proof of concept to a scaled deployment, our security strategies will help you deploy HoloLens within your IT infrastructure safely.

The following security scenarios are the most common:

| Scenario | Topic | Description |
|---------|---------|---------|
| Ensure cloud application deployment readiness | [Azure operational security checklist](/azure/security/fundamentals/operational-checklist.md) | This checklist will help you determine if your application meets essential operational security recommendations. |
| Optimize my environment for Mobile Device Management with Intune | [Use security baselines to configure Windows 10 devices in Intune](/mem/intune/protect/security-baselines) | Intune's security baselines are pre-configured groups of Windows settings that will help you quickly apply the settings recommended for your users and devices. |
| Protect the device from untrusted apps, malware, viruses, or booting from removeable media | [State separation and isolation](security-state-separation-isolation.md) | Digital signing code ensures that only Signed Firmware updates are completed, preventing activities like Debug over USB from being installed. |
| Set up secure logins for multiple users | [Manage user identity and login for Hololens](hololens-identity.md) | When using AAD, users are required to use Windows Hello for Business and use a device PIN or biometric (iris) for login to the device. AAD identity information is not stored locally on the device.
| Authenticate users through an external authentication service | [Hybrid identity documentation](/azure/active-directory/hybrid/) | Single user identities for authentication and authorization can be created for all resources, regardless of location.
| Permanently delete sensitive data | [Restart, reset, or recover HoloLens](hololens-recovery.md#clean-reflash-the-device) | Any data stored on the unit must be cleared using a full device reset or reflash |
| Clear pictures and video with a full reset or reflash.  | [Holographic Data](holographic-data.md) | Sensitive data cannot be stored persistently.|
| Reconfigure login inactivity or auto-logoff and define user account passwords | [Policy CSP - DeviceLock](/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxinactivitytimedevicelock) | DeviceLock time periods can be reset. |
| Assign or restrict privilege levels | [Admin-less operating system](security-adminless-os.md) | DeviceLock inactivity time can be reset. |
| Reconfigure product security capabilities | [Page Settings Visibility](settings-uri-list.md) | PageVisibilityList policy can be reset to restrict the pages seen within the Settings app. |
| Apply patches to the device as they become available | [Page Settings Visibility](hololens-update-hololens.md) | Update types, scheduling, and tools for updating. |
| Install patches or other software remotely | [Update HoloLens 2](hololens-update-hololens.md) | Update automatically, check for updates, and roll back updates. |
| Back up to remote storage or removable media | [Find, open, and save files on HoloLens](holographic-data.md#onedrive-app) | Access, manage, and share your photos and videos with any device and with any user. |
| Protect the device from loss or unauthorized access | [Encryption and data protection](security-encryption-data-protection.md) | When the device is lost or stolen, encryption and data protection prevent unauthorized applications from accessing sensitive information. |
| Ensure the integrity of stored data | [Security overview and architecture](security-architecture.md) | The HoloLens 2 security architecture offers secure storage locations and advanced security elements. |
| Minimize the surface area for privilege escalation with better Administration | [Admin-less operating system](security-adminless-os.md) | HoloLens disabled support for the Administrators group and limits all third-party UWP application code.  |
| Use modern security and authentication methods | [Limiting password use](security-limiting-password-use.md) | HoloLens 2 enables strong, hardware-backed “password-less” credentials for device sign in. |
| Protect against threats before or during runtime | [Hardware-backed integrity and runtime attestation](security-hardware-backed-integrity.md) | Unified Extensible Firmware Interface (UEFI) Secure Boot detects and prevents attempts to tamper with firmware through bluetooth, wifi, or Ethernet. It includes strong encryption for Trusted Platform Modules (TPMs). |
| Protect data when devices are lost and/or stolen | [Encryption and data protection](security-encryption-data-protection.md) | Encryption and Data Protection prevents unauthorized applications from accessing sensitive information. |
| Remove network vulnerabilities and ensure secure/encrypted connectivity | [Network security](security-network-security.md) | With HoloLens 2, the firewall is always enabled, and there is no way to disable it, either programmatically or through the UI. |
| Ensure privacy and data protection for my customers (for example, GDPR) | [HoloLens 2 Privacy and Data Protection](hololens2-privacy.md) | HoloLens 2 security has been redesigned to provide advanced, innovative security and privacy protection, incorporating Microsoft’s approach to privacy and GDPR regulations.|
| Deploy HoloLens 2 at scale | [Common deployment scenarios](hololens-requirements.md) | Following all the steps to deploy devices will help you to achieve value for your mixed reality scenario.|
| Get in touch with Microsoft Security Engineering teams | [Security engineering](security-engineering.md) | Microsoft has several resources and teams devoted to optimizing the company’s engineering protocols, addressing compliance, and ensuring customer trust.|