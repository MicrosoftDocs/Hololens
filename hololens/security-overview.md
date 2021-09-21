---
title: HoloLens security overview
description: Get started with an overview of security for HoloLens mixed reality devices. 
author: evmill
ms.author: v-evmill
ms.reviewer: tagran
ms.date: 6/30/2020
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

Businesses and customers need a truly modern, cutting-edge operating system with a strong, built-in security framework that allows developers to design, build, and deliver applications to effectively combat a complex threat landscape and its associated risks. The HoloLens 2 security architecture has been completely redesigned to provide advanced, innovative security and privacy protection, end-to-end.

Here, we share different ways to secure Microsoft HoloLens 2 devices. You may be a business decision-maker, IT professional, or an innovation team looking to adopt HoloLens within your organization. As you build from proof of concept to a scaled deployment, our security strategies will help you deploy HoloLens within your IT infrastructure safely. 

The following security scenarios are the most common:

| Scenario | Topic | Description |
|---------|---------|---------|
| Ensure cloud application deployment readiness | [Azure operational security checklist](https://docs.microsoft.com/azure/security/fundamentals/operational-checklist) | This checklist will help you determine if your application meets essential operational security recommendations. |
| Optimize my environment for Mobile Device Management with Intune | [Use security baselines to configure Windows 10 devices in Intune](https://docs.microsoft.com/mem/intune/protect/security-baselines) | Intune's security baselines are pre-configured groups of Windows settings that will help you quickly apply the settings recommended for your users and devices. |
| Learn about HoloLens 2 device security architecture | [Security overview and architecture](https://docs.microsoft.com/hololens/security-architecture) | The HoloLens 2 security architecture offers secure storage locations and advanced security elements. |
| Protect critical portions of the HoloLens 2 OS from unwanted change | [State separation and isolation](https://docs.microsoft.com/hololens/security-state-separation-isolation) | Components required for booting into a trusted state and untrusted apps are moved to an isolated sandbox environment, which ensures that they do not affect system security. |
| Minimize the surface area for privilege escalation with better Administration | [Admin-less operating system](https://docs.microsoft.com/en-us/hololens/security-adminless-os) | HoloLens disablrd support for the Administrators group and limits all third-party UWP application code.  |
| Use modern security and authentication methods | [Limiting password use](https://docs.microsoft.com/hololens/security-limiting-password-use) | HoloLens 2 enables strong, hardware-backed “password-less” credentials for device sign in. |
| Protect against threats during runtime | [Hardware-backed integrity and runtime attestation](https://docs.microsoft.com/hololens/security-hardware-backed-integrity) | HoloLnes 2 security protects against threats that originate prior to the start of an operating system. |
| Protect data when devices are lost and/or stolen | [Encryption and data protection](https://docs.microsoft.com/hololens/security-encryption-data-protection) | Encryption and Data Protection prevents unauthorized applications from accessing sensitive information. |
| Remove network vulnerabilities and ensure secure connectivity | [Network security](https://docs.microsoft.com/hololens/security-network-security) | With HoloLens 2, the firewall is always enabled, and there is no way to disable it, either programmatically or through the UI. |
| Get in touch with Microsoft Security Engineering teams | [Security engineering](https://docs.microsoft.com/hololens/security-engineering) | Microsoft has several resources and teams devoted to optimizing the company’s engineering protocols, addressing compliance, and ensuring customer trust.|
| Ensure privacy and data protection for my customers (e.g. GDPR) | [HoloLens 2 Privacy and Data Protection](https://docs.microsoft.com/hololens/hololens2-privacy) | HoloLens 2 security has been redesigned to provide advanced, innovative security and privacy protection, incorporating Microsoft’s approach to privacy and GDPR regulations.|
| Deploy HoloLens 2 at scale | [Common deployment scenarios](https://docs.microsoft.com/hololens/hololens-requirements) | Following all the steps to deploy devices will help you to achieve value for your mixed reality scenario.|