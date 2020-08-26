---
title: Configure CSPs and Policy overview
description: How to configure CSPs and policy. 
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: v-evmill
ms.topic: article
ms.localizationpriority: medium
ms.date: 08/27/2020
ms.reviewer: 
manager: yannisle
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Configure CSPs and Policy overview

IT Administrators can define and implement policy settings on HoloLens 2. What configuration settings you use will differ based on the deployment scenario, and corporate devices will offer IT the broadest range of control. In Windows 10, Configuration Service Providers (CSP)s are an interface to read, set, modify, or delete configuration settings on the device. These settings map to registry keys or files. Some configuration service providers support the WAP format, some support SyncML, and some support both. For more information about Windows 10 Holographic device management CSPs, see the full list of [CSPs supported in HoloLens devices](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens). 
IT Administrators can also manage Policy CSP on devices, see the full list of [Policy CSPs supported by HoloLens 2](https://docs.microsoft.com/windows/client-management/mdm/policy-csps-supported-by-hololens2).

CSPs and Policies can be easily managed on any personal or corporate device enrolled in an MDM system. Once a device is enrolled in your MDM solution, you will be able to manage that device, or set of devices using device configurations. Learn more about how to [manage your HoloLens devices through MDM](hololens-mdm-configure.md).

HoloLens 2 also supports setting a limited set of CSP configurations for HoloLens 2 devices through custom Provisioning Packages. Provisioning Packages are typically leveraged for non-MDM managed devices and require to be manually applied to each device. Read information on building custom [Provisioning Packages for HoloLens](https://docs.microsoft.com/hololens/hololens-provisioning). 
