---
title: HoloLens security architecture
description: Security architecture
author: evmill
ms.author: v-evmill
ms.reviewer: tagran
ms.date: 6/30/2020
ms.topic: article
keywords: security, hololens, hololens 2, hololens2 security, security overview, security architecture, architecture, hololens 2 architecture
ms.prod: hololens
ms.sitesec: library
ms.localizationpriority: high
manager: yannisle
appliesto:
- HoloLens 2
---

# Security overview and architecture

The HoloLens 2 security architecture was designed and engineered from the ground up to be free from legacy security issues, while creating a minimized attack surface. This new, innovative architecture offers secure storage locations and advanced security elements, with mechanisms capable of shielding operating systems from potential threats and vulnerabilities.

HoloLens 2 combines hardware, software, networking, and services to deliver end-to-end security, while providing the user with an optimal experience. With HoloLens 2, a large majority of security features are now turned on automatically, minimizing the effort required to correctly set up and configure the operating system.

Windows HoloLens 2 and operating system architecture offers these innovative security features:

  * **State separation and isolation**:  This new architecture protects critical portions of the HoloLens 2 operating system from change - such as those required for the core operating system to boot into a trusted state. Isolation technology is used to confine untrusted apps in a sandbox area, ensuring that they cannot impact the system security. The entire operating system is segmented into secure sections, with each section shielded by a combination of different security technologies.
  
  * **Data Protection**: If a user’s device is lost or stolen, HoloLens 2 prevents unauthorized applications from reading sensitive information by relying on BitLocker encryption of data. 
  
  * **Password-less operating system**:  Older, password-based operating systems could inadvertently expose users to phishing threats and were often responsible for compromised accounts. Windows Holographic for Business eliminates the use of passwords for MSA and AAD sign-in and strengthens user-identity protection with Windows Hello™ and FIDO2 sign-in. 
  
    > [!NOTE]
    > To have FIDO2 support, the device must be on Build 19041 or higher. 

  * **Network security**: HoloLens 2 offers the user increased network security via improved protocols and default settings.
