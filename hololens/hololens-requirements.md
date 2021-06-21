---
title: Planning HoloLens 2 deployment in a commercial environment
description: Learn more about deploying and managing HoloLens in enterprise environments, including infrastructure, Azure Active Directory, and mobile device management.
ms.prod: hololens
ms.sitesec: library
ms.assetid: 88bf50aa-0bac-4142-afa4-20b37c013001
author: bogenera
ms.author: bogenera
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
ms.date: 11/04/2020
appliesto:
- HoloLens 2
---

# Common Deployment Scenarios

## Overview

This page provides a high-level architecture overview for three common scenarios when deploying and managing Microsoft HoloLens 2 devices within the enterprise.

Deploying a new device used to be a hassle as you need to get all the right knowledge upfront. To solve this challenge and speed up the deployment process, we outlined common scenarios.

Often, how you manage your devices and access your organization's resources is largely determined by factors already in place. Based on your existing infrastructure, we invite you to review the common device management style (MDM) in the following scenarios.
Check [Planning HoloLens 2 deployments in a commercial environment](hololens-core-components.md) to better understand what is going on and choose which deployment method suits your needs the best. There are also three corresponding guides available to help you get started.

 1. [Scenario A: Cloud connected devices](hololens2-cloud-connected-overview.md)
     1. [Scenario A: Cloud connected devices (External Clients)](hololens2-deployment-guide.md)
 1. [Scenario B: Organization's network](hololens2-corp-connected-overview.md)
 1. [Scenario C: Offline secure environment](hololens-common-scenarios-offline-secure.md)

## Scenario A: Deploy to cloud connected devices

This scenario is comparable to deploying managed mobile devices within a company. HoloLens 2 is deployed for use primarily in environments external to a corporate network. Corporate resources aren't accessed or may be limited through VPN.

[![Scenario A diagram](images/deployment-guides-revised-scenario-a.png)](images/deployment-guides-revised-scenario-a.png#lightbox)

### When to use

Consider this deployment model for:

* External customer use cases
* Deploying Proof of Concept, Pilots and Field Services
* Deploying [Remote Assist](hololens2-options-remote-assist.md)

### Basic Common Configurations

* Wi-Fi networks are typically fully open to the Internet and Cloud services.
* Azure AD Join with Mobile Device Management (MDM) Auto Enrollment--MDM (Intune) Managed
* Users sign in with their own corporate account (Azure AD)
  * Single or multiple users per device supported
* Varying levels of device lockdown configurations are applied based on specific use cases, from Fully Open to Single App Kiosk.
* One or more applications are deployed via MDM

### Common Challenges

* Determining which MDM configurations to apply to the HoloLens 2 based on scenario requirements.

The corresponding Cloud connected guide covers how to enroll HoloLens 2 into your device management, apply licenses as needed, and validate that your end users are able to immediately use Remote Assist upon device setup.

> [!div class="nextstepaction"]
> [Cloud connected environment deployment guide](hololens2-cloud-connected-overview.md)

Use the External Clients guide to deploy devices to a remote site for short-term or long-term external use.

> [!div class="nextstepaction"]
> [Cloud connected environment (External Clients) deployment guide](hololens2-deployment-guide.md)

## Scenario B: Deploy inside your organization's network

This scenario is identical to a classic deployment for most Windows 10 PCs. HoloLens 2 is deployed for use primarily on the corporate network with access to internal corporate resources. Internet and cloud services may be limited. 

[![Scenario B1 diagram](images/deployment-guides-revised-scenario-b-01-1.png)](images/deployment-guides-revised-scenario-b-01-1.png#lightbox)

[![Scenario B2 diagram](images/deployment-guides-revised-scenario-b-02-1.png)](images/deployment-guides-revised-scenario-b-02-1.png#lightbox)

### When to use

Consider this deployment model for:

* Internal users
* Deploying at scale (Pilot and Production) within the corporate environment

### Basic Common Configurations

* Wi-Fi network is an internal corporate network with access to internal resources, and limited access to the internet or Cloud services.
* Azure AD Join with MDM Auto Enrollment
* MDM (Intune) Managed
* Users sign in with their own corporate account (Azure AD)
  * Single or multiple users per device supported
* Varying levels of device lockdown configurations are applied based on specific use cases, from Fully Open to Single App Kiosk.
* One or more applications are deployed via MDM

### Common Challenges

* HoloLens 2 doesn't support on premises AD join or SCCM. Only Azure AD join with MDM. Many companies today still deploy Windows 10 PCs in this scenario as on premises AD joined devices, managed by System Center Configuration Manager (SCCM) and may not have the infrastructure deployed/configured for managing internal Windows 10 devices via cloud-based MDM solutions.
* As HoloLens 2 is a cloud first device, it relies heavily on internet and cloud connected services for User authentication, OS updates, MDM management, and so on. When connecting to a corporate network, Proxy/Firewall rules will most likely need to be adjusted to enable access for HoloLens 2 and the applications that run on it.
* Corporate Wi-Fi connectivity typically requires certificates to authenticate the device or user to the network. The required infrastructure or settings to deploy certificates to Windows 10 devices through MDM can be challenging to configure.

The corresponding Corporate network guide instructs on how to enroll HoloLens 2 into your existing device management, apply licenses as needed, and validate that your end users are able to operate a Dynamics 365 Guide, as well as use custom line of business apps, after device set up.

> [!div class="nextstepaction"]
> [Corporate network deployment guide](hololens2-corp-connected-overview.md)

## Scenario C: Deploy in secure offline environment

This is a typical deployment for highly secure or confidential locations. HoloLens 2 is deployed for use primarily offline with no network or internet access.

[![Offline Secure diagram 1](images/deployment-guides-revised-scenario-c-01.png)](images/deployment-guides-revised-scenario-c-01.png#lightbox)

### When to use

Consider this deployment model for:

* Highly Secure environments where "data" needs to be retained in house
* "Experiences" where the public will be using the devices
* Internet connectivity issue in the remote area

### Basic Common Configurations

* Wi-Fi connectivity is disabled. Ethernet via USB may be enabled for LAN connectivity if necessary.
* Not Managed.
* Local user account for device sign-in.
  * HoloLens 2 supports only one local account.
* Varying levels of device lockdown configurations are applied via Provisioning Packages based on specific use cases. These configurations are typically restricted because of secure environment requirements.
* One or more applications are deployed via Provisioning Package

### Common Challenges

* There's a limited set of configurations available through Provisioning Packages
* Cloud services aren't able to be used, therefore limiting the HoloLens 2 capabilities.
* Higher administrative overhead since these devices have to be set up, configured, and updated manually.

The corresponding Offline secure guide provides instruction for applying a sample Provisioning Package that will lock down a HoloLens 2 for use in secure environments.

> [!div class="nextstepaction"]
> [Offline secure environment deployment guide](hololens-common-scenarios-offline-secure.md)
