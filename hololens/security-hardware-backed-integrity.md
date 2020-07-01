---
title: Hardware backed integrity, runtime attestation
description: limiting password use for holoLens 
author: jbennett
ms.date: 6/30/2020
ms.topic: article
keywords: security, hololens, Hardware backed integrity, runtime attestation,	UEFI, UEFI secure boot, secure boot, TPM, threat protection, Windows Anti-Persistence Assurance, code integrity, code protection, 
ms.prod: hololens
ms.sitesec: library
ms.localizationpriority: high
ms.reviewer: 
manager: yannisl
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Hardware-backed integrity, runtime attestation

Hardware-backed integrity and runtime attestation protects against threats that originate prior to the start of an operating system, during runtime, when the device uses hardware, and remote attestation services to ensure integrity is maintained at startup and throughout runtime duration.

## UEFI secure boot

HoloLens 2 enforces Unified Extensible Firmware Interface (UEFI) Secure Boot at all times, and UEFI only boots Microsoft trusted platforms.
Secure Boot ensures that the entire boot chain is verified for integrity, and that Windows always boots with the correct security policies applied to it. To learn more about Secure Boot go here.

## TPM

The Trusted Platform Module (TPM) is a specialized chip on an endpoint device. HoloLens 2 uses a TPM 2.0 which provides hardware-enforced key isolation.

## Secure boot 

HoloLens 2 enforces Unified Extensible Firmware Interface (UEFI) Secure Boot on all MainOS state. UEFI only boots Microsoft trusted platforms which ensures that the entire boot chain is verified for integrity, and that Windows always boots with the correct security policies applied to it. HoloLens 2 does not Secure Boot to be turned off, nor does it allow 3rd party boot loaders.

> [!Tip]
> Learn more about [Secure boot](https://docs.microsoft.com/windows-hardware/design/device-experiences/oem-secure-boot).

## Persistence access threat protection 

The goal of most cyberattacks is to maintain persistent access to a device. For cybercrime, maintaining this persistence enables a compromised Windows device to join a botnet, sell access to the device or other nefarious users, or to enable repeated data theft. In the world of targeted attacks, persistence is essential to a successful cyberattack – whether on a device or (more commonly), an entire network.  

In fact, targeted attacks are considered “advanced persistent threats”, due to their strategic need to maintain access to a target device or network. For this reason, Windows Holographic for Business considers defending against persistence absolutely crucial and uses anti-persistence technology to make an ironclad customer security promise.

### Windows Anti-Persistence Assurance

HoloLens 2 anti-persistence guarantees its users that even in the rare situation that a runtime compromise of the system were to ever occur – such as a remote exploit – such an event would be mitigated with all malicious code removed from the system simply by powering off the device. To further strengthen its anti-persistence, HoloLens 2 has added powerful integrity protection, and put read-only protections in place.

Persistence to operating system data in form of data or 3rd party device drivers is still possible, unless the user performs Push-button reset (PBR) of the device that wipes all mutable partitions. While persistence to immutable partitions is made much harder, the user needs to PBR the Hololens 2 to remove any possible threat-persistence from mutable parts.

## Code integrity protection 

Code integrity (CI) is a key security property of a modern operating system. Enforcing CI enables sound security decisions, because it guarantees the provenance of code is transparent to both the user and operating system. Complete code integrity needs to extend past binary image signing and include runtime enforcement, such as control flow integrity and dynamic code restrictions. CI is critical to preventing multiple classes of attacks including socially engineered malware, such as ransomware, remote code execution exploits, and various other attack classes.
