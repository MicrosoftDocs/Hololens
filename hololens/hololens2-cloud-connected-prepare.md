---
title: Deployment Guide – Cloud connected HoloLens 2 deployment at scale with Remote Assist - Prepare
description: How to prepare to enroll HoloLens devices over a Cloud Connected network
keywords: HoloLens, management, cloud connected, Remote Assist, AAD, Azure AD, MDM, Mobile Device Management
author: evmill
ms.author: v-evmill
ms.reviewer: aboeger
ms.date: 12/04/2020
ms.prod: hololens
ms.topic: article
ms.sitesec: library
ms.localizationpriority: medium
audience: HoloLens
manager: yannisle
appliesto:
- HoloLens 2
---

# Prepare - Cloud connected Guide

By the end of this article you will have set up AAD, MDM, and understand more about using AAD accounts and network requirements. This section of the guide will help you and your organization get prepared to deploy HoloLens 2 to the cloud and use Dynamics 365 Remote Assist by going over the importance of each piece of your infrastructure as well as providing links to guides to help you set up those pieces as needed.

## Infrastructure Essentials

For both personal and corporate deployment scenarios, an MDM system is the essential infrastructure required to deploy and manage Windows 10 Holographic devices. An Azure AD premium subscription is recommended as an identity provider and required to support certain capabilities.

### Azure Active Directory

Azure AD is a cloud-based directory service that provides identity and access management. Organizations that use Microsoft Office 365 or Intune are already using Azure AD, which has three editions: Free, Premium P1, and Premium P2 (see [Azure Active Directory editions](https://azure.microsoft.com/documentation/articles/active-directory-editions).) All editions support Azure AD device registration, but Premium P1 is required to enable MDM auto-enrollment which we will be using in this guide later.

> [!IMPORTANT]
> It is essential to have an Azure Active Directory as HoloLens devices do not support on-premises AD join. If you don&#39;t already have an Azure Active Directory set up follow the instructions in this link to get started and [Create a new tenant in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).

## Identity Management

Employees can use only one account to initialize a device so it&#39;s imperative that your organization controls which account is enabled first. The account chosen will determine who controls the device and influence your management capabilities.

In this guide we have chosen that for the [Identity](https://docs.microsoft.com/hololens/hololens-identity) used we will use AAD accounts, or Azure Active Directory accounts. There are several benefits to AAD accounts we would like to use.

- Employees use their Azure AD account to register the device in Azure AD and automatically enroll it with the organization&#39;s MDM solution (AAD+MDM – requires Azure AD Premium).
- AAD accounts support [Single Sign On](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on). When a user signs into Remote Assist, their Identity from the signed in AAD user will be recognized and the user will be signed into the app for a streamlined experience.
- AAD accounts have additional [authentication options](https://docs.microsoft.com/hololens/hololens-identity) via [Windows Hello for Business](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification). In addition to Iris log-in users can sign in from another device or use FIDO security keys.

### Mobile Device Management

Microsoft [Intune](https://docs.microsoft.com/mem/intune/fundamentals/what-is-intune), part of the Enterprise Mobility + Security, is a cloud-based MDM system that manages devices connected to your tenant. Like Office 365, Intune uses Azure AD for identity management, so employees use the same credentials to enroll devices in Intune that they use to sign into Office 365. Intune also supports devices that run other operating systems, such as iOS and Android, to provide a complete MDM solution. For the purposes of this guide, we&#39;ll be focusing on using Intune for enabling a cloud deployment at scale with HoloLens 2.

> [!IMPORTANT]
> It is essential to have Mobile Device Management. If you don&#39;t already have it set up follow this guide and [Get started with Intune](https://docs.microsoft.com/mem/intune/fundamentals/free-trial-sign-up).

> [!NOTE]
> Multiple MDM systems support Windows 10 and most support personal and corporate device deployment scenarios. MDM providers that support Windows 10 Holographic currently include: AirWatch, MobileIron, and others. Most industry-leading MDM vendors already support integration with Azure AD. You can find the MDM vendors that support Azure AD in [Azure Marketplace](https://azure.microsoft.com/marketplace/).

## Network

In this setup, we anticipate HoloLens 2 devices connecting to the Internet from any available open Wi-Fi network. Since a user could need to change the network connection based on location, they should learn how to [connect HoloLens devices to Wi-Fi.](https://docs.microsoft.com/hololens/hololens-network)

For Dynamics 365 Remote Assist there are a variety of network conditions, including bandwidth, latency, jitter, and packet loss, that can impact your video calling experience. Although audio and video calls might be possible in environments with reduced bandwidth, you might experience feature degradation. When using Dynamics 365 Remote Assist on HoloLens here are the network requirements to keep in mind:

**Minimum** : 1.5 Mbps up/down is required for peer-to-peer HD quality video calling with resolution of HD 1080p at 30 fps.

**Optimal:** For peer-to-peer HD quality video calling with resolution of HD 1080p, 4-5 Mbps up/down should be expected.

More information:

- [Network requirements](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/requirements#network-requirements)
- [Network optimization recommendations](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/requirements#dynamics-365-remote-assist-hololens)

### Optional: Connect your HoloLens to VPN

The devices being connected into this guide are going to connect to the network via and external cloud network. It may be that to access company resources you&#39;ll need to connect your devices via VPN. There are several different ways to connect your devices to VPN, both where the end user can connect via using the device UI, or the devices can be managed and receive the VPN profile from either a PPKG or MDM. How to set up VPN won&#39;t be covered in this article, so if you&#39;d like to learn more about the different VPN protocols or ways to manage VPN visit [these guides for information on HoloLens and VPN.](https://docs.microsoft.com/hololens/hololens-network#vpn)

## Next step

> [!div class="nextstepaction"]
> [Cloud connected deployment - Configure](hololens2-cloud-connected-configure.md)
