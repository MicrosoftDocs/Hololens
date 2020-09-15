---
title: Prepare certificates and network profiles for HoloLens 2
description: How to configure and use certitifcates for network on HoloLens 2 devices
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: aboeger
ms.topic: article
ms.localizationpriority: high
ms.date: 9/15/2020
ms.reviewer: v-evmill
audience: ITPro
manager: 
appliesto:
- HoloLens 2
---
# Prepare certificates and network profiles for HoloLens 2

Certificate-based authentication is a common requirement for customers using HoloLens 2. You might require certificates to access Wi-Fi, to connect to VPN solutions, or for accessing internal resources in your organization.

Because HoloLens 2 devices are typically joined to Azure Active Directory (Azure AD) and managed by Intune or other MDM provider, you will need to deploy such certificates by using a Simple Certificate Enrollment Protocol (SCEP) or Public Key Cryptography Standard (PKCS) certificate infrastructure that is integrated with your MDM solution.

## Certificate requirements
Root certificates are required to deploy certificates through a SCEP or PKCS infrastructure. Other applications and services in your organization might require root certificates to be deployed to your HoloLens 2 devices as well. 

## Wi-Fi connectivity requirements
To allow a device to be automatically provided with the required Wi-Fi configuration for your enterprise network, you will need a Wi-Fi configuration profile. You can configure Intune or other MDM provider to deploy these profiles to your devices. If your network security requires devices to be part of the local domain, you might also need to evaluate your Wi-Fi network infrastructure to make sure it's compatible with HoloLens 2 devices (HoloLens 2 devices are Azure AD-joined only).

## Deploy certificate infrastructure
If no SCEP or PKCS infrastructure already exists, you'll need to prepare one. 
To support the use of SCEP or PKCS certificates for authentication, Intune requires the use of a [certificate connector](https://docs.microsoft.com/mem/intune/protect/certificate-connectors).

> [!NOTE]
> When you use SCEP with a Microsoft CA, you must also configure the [Network Device Enrollment Service (NDES)](https://docs.microsoft.com/mem/intune/protect/certificates-scep-configure#set-up-ndes)

For more information, see [Configure a certificate profile for your devices in Microsoft Intune.](https://docs.microsoft.com/intune/certificates-configure)

## Deploy certificates and Wi-Fi/VPN profile
To deploy certificates and profiles, follow these steps:
1.	Create a profile for each of the Root and Intermediate certificates (see [Create trusted certificate profiles](https://docs.microsoft.com/intune/protect/certificates-configure#create-trusted-certificate-profiles).) Each of these profiles must have a description that includes an expiration date in DD/MM/YYYY format. **Certificate profiles without an expiration date will not be deployed.**
1.	Create a profile for each SCEP or PKCS certificates (see [Create a SCEP certificate profile or Create a PKCS certificate profile](https://docs.microsoft.com/intune/protect/certficates-pfx-configure#create-a-pkcs-certificate-profile)) Each of these profiles must have a description that includes an expiration date in DD/MM/YYYY format. **Certificate profiles without an expiration date will not be deployed.**

> [!NOTE]
> As the HoloLens 2 is considered for many to be a shared device, multiple users per device, it is recommended to deploy Device certificates instead of User certificates for Wi-Fi authentication where possible

3.	Create a profile for each corporate Wi-Fi network (see [Wi-Fi settings for Windows 10 and later devices](https://docs.microsoft.com/intune/wi-fi-settings-windows)). 
> [!NOTE]
> It is recommended that the Wi-Fi profile be [assigned](https://docs.microsoft.com/mem/intune/configuration/device-profile-assign) to Device groups rather than User groups where possible. 

> [!TIP]
> You also can export a working Wi-Fi profile from a Windows 10 PC on your corporate network. This export creates an XML file with all the current settings. Then, import this file into Intune, and use it as the Wi-Fi profile for your HoloLens 2 devices. See [Export and import Wi-Fi settings for Windows devices.](https://docs.microsoft.com/mem/intune/configuration/wi-fi-settings-import-windows-8-1)

4.	Create a profile for each corporate VPN (see [Windows 10 and Windows Holographic device settings to add VPN connections using Intune](https://docs.microsoft.com/intune/vpn-settings-windows-10)).




