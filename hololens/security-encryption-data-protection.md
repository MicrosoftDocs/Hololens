---
title: Encryption and Data Protection
description: Encryption and Data Protection
author: jbennett
ms.date: 6/30/2020
ms.topic: article
keywords: security, hololens, Encryption, Data Protection, BitLocker Device, BitLocker, bitlocker, bitlocker encryption, azure integration, 
ms.prod: hololens
ms.sitesec: library
ms.localizationpriority: high
ms.reviewer: 
manager: yannisl
appliesto:
- HoloLens 2
---

# Encryption and data protection

Encryption and Data Protection protects data when the device is lost or stolen and prevents unauthorized applications from accessing sensitive information.

## BitLocker device encryption

BitLocker is a full-volume encryption feature for integrity protection of Read Only (RO) media and privacy protection of writable media.  Since its inception, it has been an effective shield against unauthorized access to the data during offline attacks. HoloLens 2 enables Bitlocker Device Encryption (BDE) by default to protect data from any unauthorized physical access to the device. Always evolving to meet the needs of the future, Microsoft continues to invest and enhance this technology.

BDE is a data protection feature that employs AES-XTS-128 or AES-XTS-256 encryption on all volumes in the state-separated layout of the device. BDE provides device level encryption in a state-separated layout. BitLocker Device Encryption is enabled automatically on operating system and fixed data volumes and cannot be turned off, even by IT administrators, so that the device is always protected. Once a HoloLens 2 device is powered on, BDE encryption keys are released by the TPM preventing threats of data theft or exposure from lost, stolen or improperly decommissioned devices.

BDE encryption keys are then used to transparently decrypt binaries and the data required to boot the device. As the operating system volume is unlocked and a system is booting up, other volumes become accessible using a volume-specific version of the auto-unlock protector. No other protectors are available to maintain user privacy and the drive can only be unlocked on the same device. Read Only (RO) enforcement on required volumes is applied and enforced immediately, starting from the first boot.

## Azure integration 

HoloLens 2 enables customers to integrate their devices with Azure services. Communications between HoloLens 2 devices and Azure use TLS (Transport Layer Security) protocol to protect data traveling between itself and cloud services which delivers strong authentication, message privacy, and integrity. All Azure services fully support TLS 1.2 and any services where customers are using only TLS 1.2 only accept TLS 1.2 traffic. Services that currently accept TLS 1.0/1.1 traffic are currently continuing to support these protocol versions to ensure compatibility with existing applications. While Microsoft’s TLS 1.0 implementation has no known security vulnerabilities, it’s important to account for potential future protocol downgrade attacks and other TLS vulnerabilities. Microsoft continues to monitor the security landscape and reevaluates its position when appropriate. Azure’s encryption standards for data in transit are detailed in [Azure encryption overview](https://docs.microsoft.com/azure/security/fundamentals/encryption-overview). Visit the Azure documentation to learn more about [best practices for Azure data security and encryption](https://docs.microsoft.com/azure/security/fundamentals/data-encryption-best-practices). 

OneDrive, an example of cloud integration with HoloLens 2, has an auto upload feature where your files and documents can be automatically uploaded to the cloud when connected to the internet. Pausing automatic syncing of files cannot be turned off via policy but is directly configurable via the UX. 
