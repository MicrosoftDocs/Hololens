---
title: Using Microsoft’s Endpoint Manager Intune to manage HoloLens devices
description: Learn how to use MDM to configure CSP, policy, and manage HoloLens mixed reality devices at scale using Intune. 
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: v-evmill
ms.topic: article
ms.localizationpriority: medium
ms.date: 9/9/2020
ms.reviewer: 
manager: yannisle
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Using Microsoft’s Endpoint Manager Intune to manage HoloLens devices

There are numerous different settings you can manage via MDM. Using Intune devices can be grouped together and configurations can be deployed to those groups of users or devices. Apps can also be deployed and managed, setting up devices to connect to your network, as well as configuring updates to occur at the time desired and on the update ring needed. 

## How to manage via Intune

### Device categories and groups
Using Intune, you can create device categories to automatically add devices to groups based on categories that you create, such as Engineering, Medical, Developers, and so on. The idea is to make it easier to manage your devices running Windows Holographic for Business.
Read more: [Categorize devices into groups](https://docs.microsoft.com/mem/intune/enrollment/device-group-mapping)

### Device configuration profiles
Intune includes settings and features that you can enable or disable on different devices within your organization. These settings and features are managed using profiles. For example, you can create a profile that enables Cortana, or uses Microsoft Defender Smart Screen on your devices running Windows Holographic for Business.
In your profiles, you can use OMA-URI to customize some settings, create device restrictions, and configure a virtual private network (VPN) and Wi-Fi.
[Get started with configuration profiles](https://docs.microsoft.com/mem/intune/configuration/device-profiles), and [profile overview](https://docs.microsoft.com/mem/intune/configuration/device-profile-create).

## Examples of what can be managed and configured

Using MDM to manage devices gives a wide array of items that can be selected. 

### Wi-Fi
[Wi-Fi settings](https://docs.microsoft.com/mem/intune/configuration/wi-fi-settings-configure) assigns wireless network settings to users and devices. When you assign a Wi-Fi profile, users get access to your corporate Wi-Fi without having to configure it themselves.
Learn more about [configuring your network for HoloLens](hololens-commercial-infrastructure.md)

### Certificates
Certificates help improve security by providing account authentication, Wi-Fi authentication, VPN encryption, and SSL encryption of web content. Although administrators can manage certificates on devices manually through provisioning packages, it’s a best practice to use your MDM system to manage those certificates throughout their entire lifecycle – from enrollment through renewal and revocation. Your MDM system can automatically deploy these certificates to the devices’ certificate stores after you enroll the device (as long as the MDM system supports the Simple Certificate Enrollment Protocol (SCEP) or Public Key Cryptography Standards #12 (PKCS#12)). MDM can also query and delete enrolled client certificates or trigger a new enrollment request before the current certificate is expired. 

### Proxy
Most corporate intranet networks leverage a proxy to manage internal traffic. With HoloLens 2 you can configure a proxy server for ethernet and Wi-Fi connections. These settings do not apply to VPN connections. 
For more details on proxy settings for Windows 10, see [NetworkProxy CSP](https://docs.microsoft.com/windows/client-management/mdm/networkproxy-csp).

### VPN
Organizations often use a VPN to control access to apps and resources on their company’s intranet. HoloLens 2 supports SSL VPN connections, which require a downloadable plugin from the Microsoft Store and are specific to the VPN vendor of your choice. 
- Read more about [VPN on HoloLens](hololens-network.md#vpn).
- For more details about VPN profiles, see the [VPNv2 CSP](https://docs.microsoft.com/windows/client-management/mdm/vpnv2-csp).

### Deploy and manage apps
Using Intune, you can add apps to your devices running Windows Holographic for Business. An MDM solution enables IT decision-makers and administrators to privately auto-install (push) their in-house, line-of-business apps, or purchase apps through the store for a group of users. There are many ways to deploy apps, including:
-	[Intune and Company Portal]( app-deploy-intune.md)
-	[Microsoft Store for Business]( app-deploy-store-business.md)

Learn more about app management through Intune.
-	[Add apps to Intune](https://docs.microsoft.com/mem/intune/apps/apps-add)
-	[Add Microsoft Store apps](https://docs.microsoft.com/mem/intune/apps/store-apps-windows)
-	[Add apps you create](https://docs.microsoft.com/mem/intune/apps/lob-apps-windows)
- [Assign apps to groups](https://docs.microsoft.com/mem/intune/apps/apps-deploy)

### Software updates
Intune includes a feature called update rings for Windows 10 devices. These update rings include a group of settings that determine how updates are installed. For example, you can create a maintenance window to install updates, or choose to restart after updates are installed. An update ring can be applied to multiple devices running Windows Holographic for Business.
Read more about how to [Manage HoloLens updates](hololens-updates.md) and [Manage software updates via Intune](https://docs.microsoft.com/mem/intune/protect/windows-update-for-business-configure).

### Configure kiosk mode
Using the shared or guest PC features available in Intune, you can configure Windows Holographic for Business devices to run as a kiosk. These devices can run one app (single-app kiosk mode), or run multiple apps (multi-app kiosk mode). Kiosk mode is a UI to control which identities have access to which apps by default.
Learn how to [set up HoloLens as a kiosk]( hololens-kiosk.md)

