---
title: Hardware backed integrity and runtime attestation
description: Hardware backed integrity and runtime attestation

ms.reviewer: tagran
ms.date: 6/30/2020
ms.prod: hololens
ms.topic: article
keywords: security, hololens, Hardware backed integrity, runtime attestation,	UEFI, UEFI secure boot, secure boot, TPM, threat protection, Windows Anti-Persistence Assurance, code integrity, code protection, 
ms.sitesec: library
ms.localizationpriority: high

appliesto:
- HoloLens 2
---

# Hardware-backed integrity and runtime attestation

Hardware-backed integrity and runtime attestation protects against threats that originate prior to the start of an operating system, during runtime, when the device uses hardware, and remote attestation services to ensure integrity is maintained at startup and throughout runtime duration.

## UEFI secure boot

HoloLens 2 enforces Unified Extensible Firmware Interface (UEFI) Secure Boot always, and UEFI only boots Windows Holographic for Business.
Secure Boot ensures that the entire boot chain is verified for integrity, and that Windows always boots with the correct security policies applied to it. Learn more about [Secure Boot](/windows-hardware/design/device-experiences/oem-secure-boot).

## TPM

The Trusted Platform Module (TPM) is a specialized chip on an endpoint device. HoloLens 2 uses a TPM 2.0, which provides hardware-enforced key isolation. Learn more about [TPM fundamentals](/windows/security/information-protection/tpm/tpm-fundamentals).

## Persistence Access Threat Protection

The goal of most cyberattacks is to maintain persistent access to a device. For cybercrime, maintaining this persistence enables a compromised Windows device to join a botnet, sell access to the device or other nefarious users, or to enable repeated data theft. In the world of targeted attacks, persistence is essential to a successful cyberattack – whether on a device or (more commonly), an entire network.  

In fact, targeted attacks are considered “advanced persistent threats”, due to their strategic need to maintain access to a target device or network. For this reason, Windows Holographic for Business considers defending against persistence absolutely crucial and uses anti-persistence technology to make an ironclad customer security promise.

## Code integrity protection

Code integrity (CI) is a key security property of a modern operating system. Enforcing CI enables sound security decisions, because it guarantees the provenance of code is transparent to both the user and operating system. Complete code integrity needs to extend past binary image signing and include runtime enforcement, such as control flow integrity and dynamic code restrictions. CI is critical to preventing multiple classes of attacks including socially engineered malware, such as ransomware, remote code execution exploits, and various other attack classes.
