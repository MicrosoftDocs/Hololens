---
title: Configure CSPs and Device Management overview
description: Learn how to configure CSPs, policy, and device management using Mobile Device Management, provisioning packages, and kiosk modes. 
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: v-evmill
ms.topic: article
ms.localizationpriority: medium
ms.date: 09/16/2020
ms.reviewer: lavinds
manager: yannisle
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Configure CSPs and Device Management overview

IT Administrators can define and implement policy settings on HoloLens 2. What configuration settings you use will differ based on the deployment scenario, and corporate devices will offer IT the broadest range of control. In Windows 10, Configuration Service Providers (CSP)s are an interface to read, set, modify, or delete configuration settings on the device. These settings map to registry keys or files. Some configuration service providers support the WAP format, some support SyncML, and some support both.

For more information about Windows 10 Holographic device management CSPs, see the full list of [CSPs supported in HoloLens devices](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens).
IT Administrators can also manage Policy CSP on devices, see the full list of [Policy CSPs supported by HoloLens 2](https://docs.microsoft.com/windows/client-management/mdm/policy-csps-supported-by-hololens2).

## Configuration methods

### Configure with MDM

CSPs and Policies can be easily managed on any personal or corporate device enrolled in an MDM system. Once a device is enrolled in your MDM solution, you will be able to manage that device, or set of devices using device configurations. Learn more about how to [manage your HoloLens devices through MDM](hololens-mdm-configure.md).

### Configure with Provisioning Packages

HoloLens 2 also supports setting a limited set of CSP configurations for HoloLens 2 devices through custom Provisioning Packages. Provisioning Packages are typically leveraged for non-MDM managed devices and require to be manually applied to each device. Read information on building custom [Provisioning Packages for HoloLens](https://docs.microsoft.com/hololens/hololens-provisioning).

## Configurations

### Common device restrictions

Some device restrictions are as simple and disabling a functionality or connection to the device. To learn about these read more about [common device restrictions.](hololens-common-device-restrictions.md)

### Kiosk modes

Use Kiosk mode to control which identities have access to which apps by default. Kiosks can be used for a single app or multiple app UI experience. Kiosk configurations range from a single app for anyone using the device, to different selections of apps for different groups. Kiosk mode does not stop “allowed apps” from launching other apps and was not intended to ever. Learn more by [reading about Kiosk modes and how to use them](hololens-kiosk.md).

### Settings Page Visibility

Use Settings app policy to control which identities have access to settings by default. Using this policy the Settings app can be configured to either show only the select pages, or hide all selected pages. [Read about how to configure the pages available](settings-uri-list.md).

This feature is currently only available in [Windows Insider builds](hololens-insider.md). Ensure devices you intend to use this feature for are on build 19041.1349+.

### WDAC

Use WDAC configuration to control which apps / processes are allowed / disallowed to be launched irrespective of whether system is in kiosk mode or not.
[See our overview for WDAC.](windows-defender-application-control-wdac.md)
