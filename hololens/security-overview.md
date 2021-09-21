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

Figuring out how to deploy a new device while guarding against security breaches can be challenging when you're using it for the first time. Here, we share different ways to secure Microsoft HoloLens 2 devices.

You may be a business decision-maker, IT professional, or an innovation team looking to adopt HoloLens within your organization. As you build from proof of concept to a scaled deployment, our security strategies will help you deploy HoloLens within your IT infrastructure safely. The following security scenarios are the most common:

| Scenario | Topic | Description |
|---------|---------|---------|
| Ensure cloud application deployment readiness | https://docs.microsoft.com/en-us/azure/security/fundamentals/operational-checklist | Deploying an application on Azure is fast, easy, and cost-effective. Before deploying cloud applications in production, it's useful to have a checklist to assist in evaluating your application against a list of essential and recommended operational security actions for you to consider. |
| Optimize my environment for Mobile Device Management with Intune | https://docs.microsoft.com/en-us/mem/intune/protect/security-baselines | Use Intune's security baselines to help you secure and protect your users and devices. Security baselines are pre-configured groups of Windows settings that help you apply the security settings that are recommended by the relevant security teams. |
| Learn about HoloLens 2 device security architecture | https://docs.microsoft.com/en-us/hololens/security-architecture | The HoloLens 2 security architecture was designed and engineered from the ground up to be free from legacy security issues, while creating a minimized attack surface. This new, innovative architecture offers secure storage locations and advanced security elements, with mechanisms capable of shielding operating systems from potential threats and vulnerabilities. |
| Protect critical portions of the HoloLens 2 OS from unwanted change | https://docs.microsoft.com/en-us/hololens/security-state-separation-isolation | State separation and isolation protect critical portions of the Hololens 2 operating system from change – such as those components required for the operating system to boot into a trusted state. With isolation technology, untrusted apps are moved to an isolated sandbox environment, to ensure that they do not affect system security. |
| Minimize the surface area for privilege escalation with better Administration | https://docs.microsoft.com/en-us/hololens/security-adminless-os | HoloLens 2 minimizes the surface area for privilege escalation by disabling support for the Administrators group and limiting all third-party UWP application code to only execute as standard users within the AppContainer sandbox.  |
| Use modern security and authentication methods | https://docs.microsoft.com/en-us/hololens/security-limiting-password-use | Most computer systems today utilize user credentials as the basis for security making them dependent on reusable, user-created passwords. This system design has resulted in passwords also becoming the most common cause of account compromise and data breaches. |
| Protect against threats during runtime |https://docs.microsoft.com/en-us/hololens/security-hardware-backed-integrity | Hardware-backed integrity and runtime attestation protect against threats that originate prior to the start of an operating system, during runtime, when the device uses hardware, and remote attestation services to ensure integrity is maintained at startup and throughout runtime duration. |
| Protect data when devices are lost and/or stolen | https://docs.microsoft.com/en-us/hololens/security-encryption-data-protection | Encryption and Data Protection protects data when the device is lost or stolen and prevents unauthorized applications from accessing sensitive information. |
| Remove network vulnerabilities and ensure secure connectivity | https://docs.microsoft.com/en-us/hololens/security-network-security | HoloLens 2 has eliminated vulnerable NetBIOS-related code from the operating system, and The Windows Defender Firewall delivers critical functionality to secure device connectivity. With HoloLens 2, the firewall is always enabled and there are no ways to disable it programmatically or through the UI. |
| Get in touch with Microsoft Security Engineering teams | https://docs.microsoft.com/en-us/hololens/security-engineering | Microsoft has several resources and teams devoted to optimizing the company’s engineering protocols, addressing compliance, and ensuring customer trust. |
| Ensure privacy and data protection for my customers (e.g. GDPR) | https://docs.microsoft.com/en-us/hololens/hololens2-privacy | The HoloLens 2’s security has been redesigned to provide advanced, innovative security and privacy protection, end-to-end, incorporating both Microsoft’s approach to privacy and GDPR regulations. |
| Deploy HoloLens 2 at scale | https://docs.microsoft.com/en-us/hololens/hololens-requirements | You want solutions - deployed at scale. We want to get you there. Let's first talk about the steps to deploy devices, therefore holograms, to achieve value for your target mixed reality scenario. |