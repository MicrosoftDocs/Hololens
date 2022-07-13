---
title: Using Microsoft’s Endpoint Manager Intune to manage HoloLens devices
description: Learn how to use MDM to configure CSP, policy, and manage HoloLens mixed reality devices at scale using Microsoft Intune. 
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: millerevan
manager: lolab
ms.reviewer: lavinds
ms.topic: article
ms.localizationpriority:
ms.date: 6/28/2022
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Using Microsoft’s Endpoint Manager Intune to manage HoloLens devices

There are numerous different settings you can manage via Mobile Device Management (MDM). Using Microsoft Intune, devices can be grouped together and configurations can be deployed to those groups of users or devices. Apps can also be deployed and managed, setting up devices to connect to your network, as well as configuring updates to occur at the time desired and on the update ring needed.

## How to manage via Microsoft Intune

### Device categories and groups

Using Microsoft Intune, you can create device categories to automatically add devices to groups based on categories that you create, such as Engineering, Medical, based on location of your devices, development specific devices, and so on. Groups can be dynamic or manually managed, allowing for the level of control you need. Once a group is created, it can have policies, apps, and compliance profiles assigned to that group. A group can be used again and again to receive different configurations.

The idea is to make it easier to manage your devices running Windows Holographic for Business. By default all HoloLens 2 devices are running Windows Holographic for Business, but HoloLens (1st gen) devices can be upgraded with a license to be managed as well.  

Read more: [Categorize devices into groups](/mem/intune/enrollment/device-group-mapping)

### Device configuration profiles

Intune includes settings and features that you can enable or disable on different devices within your organization. These settings and features are managed using profiles. For example, you can create a profile that enables Kiosk, or uses Microsoft Defender Smart Screen on your devices running Windows Holographic for Business. Most of these can be modified via [CSPs](/windows/configuration/provisioning-packages/how-it-pros-can-use-configuration-service-providers) (Configuration service providers). You can also choose to enable sets of policies that are part of our [common device restrictions](hololens-common-device-restrictions.md).

You can also create custom profiles. You can [use OMA-URI](/troubleshoot/mem/intune/deploy-oma-uris-to-target-csp-via-intune) (Open Mobile Alliance - Uniform Resource Identifier) to customize some settings, create device restrictions, and configure a virtual private network (VPN) and Wi-Fi.

[Get started with configuration profiles](/mem/intune/configuration/device-profiles), and [profile overview](/mem/intune/configuration/device-profile-create).

## Examples of what can be managed and configured

Using MDM to manage devices gives a wide array of items that can be selected. Most of these items are configured via a CSP ([Configuration Service Providers](/windows/configuration/provisioning-packages/how-it-pros-can-use-configuration-service-providers)). These help get the proper policies, configurations, and files to your devices. Here's the [full list of policies supported on HoloLens 2](/windows/client-management/mdm/policies-in-policy-csp-supported-by-hololens2).

### Wi-Fi

[Wi-Fi settings](/mem/intune/configuration/wi-fi-settings-configure) assigns wireless network settings to users and devices. When you assign a Wi-Fi profile, users get access to your corporate Wi-Fi without having to configure it themselves.

Learn more about [configuring your network for HoloLens](hololens-commercial-infrastructure.md)

### Certificates

Certificates help improve security by providing account authentication, Wi-Fi authentication, VPN encryption, and SSL encryption of web content. Although administrators can manage certificates on devices manually through provisioning packages, it’s a best practice to use your MDM system to manage those certificates throughout their entire lifecycle – from enrollment through renewal and revocation. Your MDM system can automatically deploy these certificates to the devices’ certificate stores after you enroll the device (as long as the MDM system supports the Simple Certificate Enrollment Protocol (SCEP) or Public Key Cryptography Standards #12 (PKCS#12). MDM can also query and delete enrolled client certificates or trigger a new enrollment request before the current certificate is expired.

### Proxy

Most corporate intranet networks leverage a proxy to manage internal traffic. With HoloLens 2 you can configure a proxy server for ethernet and Wi-Fi connections. These settings don't apply to VPN connections.
For more details on proxy settings for Windows 10, see [NetworkProxy CSP](/windows/client-management/mdm/networkproxy-csp).

### VPN

Organizations often use a VPN to control access to apps and resources on their company’s intranet. HoloLens 2 supports SSL VPN connections, which require a downloadable plugin from the Microsoft Store and are specific to the VPN vendor of your choice.

- Read more about [VPN on HoloLens](hololens-network.md#vpn).
- For more information about VPN profiles, see the [VPNv2 CSP](/windows/client-management/mdm/vpnv2-csp).

### Deploy and manage apps

Using Intune, you can add apps to your devices running Windows Holographic for Business. An MDM solution enables IT decision-makers and administrators to privately auto-install (push) their in-house, line-of-business apps, or purchase apps through the store for a group of users. There are many ways to deploy apps, including:

- [Intune and Company Portal](app-deploy-intune.md)
- [Microsoft Store for Business](app-deploy-store-business.md)

Learn more about app management through Intune:

- [Add apps to Intune](/mem/intune/apps/apps-add)
- [Add Microsoft Store apps](/mem/intune/apps/store-apps-windows)
- [Add apps you create](/mem/intune/apps/lob-apps-windows)
- [Assign apps to groups](/mem/intune/apps/apps-deploy)

### Software updates

Intune includes a feature called update rings for Windows 10 devices. These update rings include a group of settings that determine how updates are installed. For example, you can create a maintenance window to install updates, or choose to restart after updates are installed. An update ring can be applied to multiple devices running Windows Holographic for Business.
Read more about how to [Manage HoloLens updates](hololens-updates.md) and [Manage software updates via Intune](/mem/intune/protect/windows-update-for-business-configure).

### Configure kiosk mode

Using the shared or guest PC features available in Intune, you can configure Windows Holographic for Business devices to run as a kiosk. These devices can run one app (single-app kiosk mode), or run multiple apps (multi-app kiosk mode). Kiosk mode is a UI to control which identities have access to which apps by default.
Learn how to [set up HoloLens as a kiosk]( hololens-kiosk.md)

## How MDM syncs work

When a device syncs to MDM, it communicates to see what it needs to be applied to the device; this is when policies are applied to the device.

### What happens during an MDM sync

- Policies are applied to the device
- The device is checked to be compliant with any [compliance profiles](/mem/intune/protect/device-compliance-get-started) you've created
- Access tokens are refreshed

### What doesn't happen during sync

Line of Business (LOB) App installation:

- Required LOB Apps are installed when setting up a device, after that LOB app updates are offered on a 24 hour check-in.
  - See [more about MDM app installs](app-deploy-intune.md#about-lob-app-updates).

### When does an MDM sync occur

Syncing with MDM occurs under the following conditions

- When the device is first enrolled with MDM
  - This includes [Autopilot](hololens2-autopilot.md) or adding the [first user to the device during OOBE](hololens-enroll-mdm.md#auto-enrollment-in-mdm), as well as [enrolling a local or MSA user](hololens-enroll-mdm.md#for-single-user-devices)
- When the user manually presses the sync button in the Settings app
- Regular check in intervals
  - On a regular 8 hour interval on established devices
  - On a more frequent interval during the first 24 hours
  - For specifics read [How long does it take for devices to get a policy, profile, or app after they're assigned?](/mem/intune/configuration/device-profile-troubleshoot#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)
- When a policy or profile is assigned

Read more at [What actions cause Intune to immediately send a notification to a device?](/mem/intune/configuration/device-profile-troubleshoot#what-actions-cause-intune-to-immediately-send-a-notification-to-a-device)
