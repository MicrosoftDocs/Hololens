---
title: Common Infrastructure Deployment Scenarios
description: Learn about some of the most common deployment scenarios based on different infrastructure deployments for mixed reality.
ms.assetid: 651d0430-bfbc-4685-a4fd-db7c33ce9325
ms.date: 3/24/2021
keywords: hololens
manager: yannisle
ms.prod: hololens
ms.sitesec: library
author: scooley
ms.author: v-evmill
ms.topic: article
audience: ITPro
ms.localizationpriority: medium
appliesto:
- HoloLens 2
---

# Common Infrastructure Deployment Scenarios Overview

This following information provides a high-level architecture overview for three common scenarios when deploying and managing Microsoft HoloLens 2 devices within the enterprise. Often how you manage your devices and how to access your organization's resources is largely determined by factors already in place. Based on the existing infrastructure we invite you to review the common device management style in the following scenarios, and try out our guides for deploying in the scenario matching your needs.

## Scenarios

The diagram below represents two typical managed scenarios for HoloLens 2 deployments.
![Scenarios diagram](images/deployment-guides-revised-scenario-a-b.png) 

There is also third scenario that allows for offline secure deployments.
![Offline Secure diagram 1](images/deployment-guides-revised-scenario-c-01.png)


### Scenario A: Deploy to cloud connected devices

HoloLens 2 is deployed for use primarily in environments external to a corporate network. Corporate resources aren't accessed or may be limited through VPN. This  deployment is similar to managed mobile devices within a company.
 * Basic Common Configurations
   * Wi-Fi networks are typically fully open to the Internet and Cloud services.
   * Azure AD Join with Mobile Device Management (MDM) Auto Enrollment--MDM (Intune) Managed
   * Users sign in with their own corporate account (Azure AD)
     * Single or multiple users per device supported
   * Varying levels of device lockdown configurations are applied based on specific use cases, from Fully Open to Single App Kiosk.
   * One or more applications are deployed via MDM

* Common Challenges
   * Determining which MDM configurations to apply to the HoloLens 2 based on scenario requirements.

For a deployment guide that is similar to this scenario review our guide for [Cloud connected environment deployment guide](hololens2-cloud-connected-overview.md).

> [!div class="nextstepaction"]
> [Cloud connected environment deployment guide](hololens2-cloud-connected-overview.md)
> [!div class="nextstepaction"]
> [Cloud connected environment (External Clients) deployment guide](hololens2-deployment-guide.md)

### Scenario B: Deploy inside your organization's network

HoloLens 2 is deployed for use primarily on the corporate network with access to internal corporate resources. Internet and cloud services may be limited. This deployment is a typical deployment for most Windows 10 PCs.

 * Basic Common Configurations
   * Wi-Fi network is an internal corporate network with access to internal resources, and limited access to the internet or Cloud services.
   * Azure AD Join with MDM Auto Enrollment
   * MDM (Intune) Managed
   * Users sign in with their own corporate account (Azure AD)
     * Single or multiple users per device supported
   * Varying levels of device lockdown configurations are applied based on specific use cases, from Fully Open to Single App Kiosk.
   * One or more applications are deployed via MDM

 * Common Challenges
   * HoloLens 2 doesn't support on premises AD join or SCCM. Only Azure AD join with MDM. Many companies today still deploy Windows 10 PCs in this scenario as on premises AD joined devices, managed by System Center Configuration Manager (SCCM) and may not have the infrastructure deployed/configured for managing internal Windows 10 devices via cloud-based MDM solutions.
   * As HoloLens 2 is a cloud first device, it relies heavily on internet and cloud connected services for User authentication, OS updates, MDM management, and so on. When connecting to a corporate network, Proxy/Firewall rules will most likely need to be adjusted to enable access for HoloLens 2 and the applications that run on it.
   * Corporate Wi-Fi connectivity typically requires certificates to authenticate the device or user to the network. The required infrastructure or settings to deploy certificates to Windows 10 devices through MDM can be challenging to configure.

For a deployment guide that is similar to this scenario review our guide for [Corporate network deployment guide](hololens2-corp-connected-overview.md).

> [!div class="nextstepaction"]
> [Corporate network deployment guide](hololens2-corp-connected-overview.md)

### Scenario C: Deploy in secure offline environment

HoloLens 2 is deployed for use primarily offline with no network or internet access. This is a typical deployment for highly secure or confidential locations.
 * Basic Common Configurations
   * Wi-Fi connectivity is disabled. Ethernet via USB may be enabled for LAN connectivity if necessary.
   * Not Managed.
   * Local user account for device sign-in.
     * HoloLens 2 supports only one local account.
   * Varying levels of device lockdown configurations are applied via Provisioning Packages based on specific use cases. These configurations are typically restricted because of secure environment requirements.
   * One or more applications are deployed via Provisioning Package

 * Common Challenges
   * There's a limited set of configurations available through Provisioning Packages
   * Cloud services aren't able to be used, therefore limiting the HoloLens 2 capabilities.
   * Higher administrative overhead since these devices have to be set up, configured, and updated manually.

For a deployment guide that is similar to this scenario review our [Offline secure environment deployment guide](hololens-common-scenarios-offline-secure.md).

> [!div class="nextstepaction"]
> [Offline secure environment deployment guide](hololens-common-scenarios-offline-secure.md)
