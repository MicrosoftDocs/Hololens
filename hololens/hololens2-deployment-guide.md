---
title: Deployment Guide
description: Deployment guide for HoloLens 2 (with Remote assist as an example)
ms.prod: hololens
ms.sitesec: library
author: pawinfie
ms.author: pawinfie
ms.topic: article
ms.localizationpriority: medium
ms.date: 1/7/2021
ms.custom: 
ms.reviewer: 
manager: laurawi
appliesto:
- HoloLens 2
---

# Deploying HoloLens 2 to External Clients with Remote Assist

This document helps IT professions plan for and deploy HoloLens 2 devices with a focus on Remote Assist. [Learn more about Remote Assist](https://docs.microsoft.com/hololens/hololens2-cloud-connected-overview#learn-about-remote-assist).

## Scenario Description

For the purpose of this document, Contoso Company wants to ship a HoloLens 2 device to an external client's plant for short-term or long-term use. When the client needs assistance servicing machinery, the client will log into the HoloLens 2 device using credentials provided by Contoso Company and use Remote Assist to contact Contoso Company's experts.

### Requirements for this Scenario

1. Azure AD
1. MDM
1. Remote Assist License
    1. [Buy Remote Assist](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/buy-remote-assist)
    1. [Trial Remote Assist](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/try-remote-assist)

## Common Concerns

- [How to ensure that external clients do not have the ability to communicate with one another](#how-to-ensure-that-external-clients-do-not-have-the-ability-to-communicate-with-one-another)
- [How to ensure that clients do not have access to company resources](#how-to-ensure-that-clients-do-not-have-access-to-company-resources)
- [How to restrict apps](#how-to-restrict-apps)
- [How to manage passwords](#how-to-manage-passwords)
- [How to ensure that clients do not have access to chat history](#how-to-ensure-that-clients-do-not-have-access-to-chat-history)

### How to ensure that external clients do not have the ability to communicate with one another

Since Remote Assist HoloLens to HoloLens calls are not supported, clients are able to search for, but are unable to, communicate with one another. To further restrict who clients can search for and call,  [Information barriers](https://docs.microsoft.com/microsoft-365/compliance/information-barriers?view=o365-worldwide) can restrict who a client can communicate with. Another option to consider is using [Scoped Directory Search](https://docs.microsoft.com/MicrosoftTeams/teams-scoped-directory-search)

 > [!NOTE]
> Since single sign on is enabled, it is important to disable the browser using [**WDAC**](https://docs.microsoft.com/hololens/windows-defender-application-control-wdac). If an external client opens the browser and uses the web version of Teams, the client will have access to call/chat history.

### How to ensure that clients do not have access to company resources

There are two options to consider.

The first option is a multi-layer approach:

1. Only assign licenses that the user requires. If you do not assign OneDrive, Outlook, SharePoint, Yammer, etc. to the user, he/she will not have access to those resources. The only licenses the users will need is Remote Assist, Intune, and AAD licenses to begin.
1. Block apps (such as email) that you don’t want clients to access (See [How to restrict apps](#how-to-restrict-apps)).
1. Do NOT share usernames nor password with clients. To log into the HoloLens 2, an email and numerical PIN is required.

The second option is to create a separate tenant that hosts clients.

### How to restrict apps

[Kiosk Mode](https://docs.microsoft.com/hololens/hololens-kiosk) and/or [WDAC (Windows Defender Application Control)](https://docs.microsoft.com/hololens/windows-defender-application-control-wdac) are options for restricting applications.

### How to manage passwords

1. Remove password expiration. However, this increases the chance that that an account will be compromised. NIST password recommendation is change passwords every 30-90 days.
1. Extend the password expiration for HoloLens 2 devices to exceed 90 days.
1. The devices should be returned to Contoso to change the passwords. However, this can cause issues if the devices are expected to be in the client's plant for 90+ days.  
1. For devices that are sent to multiple clients, reset passwords before shipping the device to clients.

### How to ensure that clients do not have access to chat history

Remote Assist clears chat history after each session. However, the chat history will be available for the Microsoft Teams user.

> [!NOTE]
> Since single sign on is enabled, it is important to disable the browser using [**WDAC**](https://docs.microsoft.com/hololens/windows-defender-application-control-wdac). If a external client opens the browser and uses the web version of Teams, the client will have access to call/chat history.

## General Deployment Recommendations and Instructions

We recommend the following for HoloLens 2 deployment Steps:

1. Use the [latest HoloLens OS release](https://aka.ms/hololens2download) as your baseline build.
1. Assign user-based or device-based licenses:
    1. User-based and device-based licenses both follow the following steps:
        1. [Create a group in AAD and add members](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal#create-a-basic-group-and-add-members) for HoloLens/RA users.
        1. [Assign device-based or user-based licenses](https://docs.microsoft.com/azure/active-directory/enterprise-users/licensing-groups-assign#:~:text=In%20this%20article%201%20Assign%20the%20required%20licenses,3%20Check%20for%20license%20problems%20and%20resolve%20them) to this group.
        1. (Optional) You can target groups for MDM policies.

1. Devices should be AAD joined to your tenant, [Auto Enrolled](https://docs.microsoft.com/hololens/hololens-enroll-mdm#auto-enrollment-in-mdm), and configured through [Auto Pilot](https://docs.microsoft.com/hololens/hololens2-autopilot).
    1. Please note that the first user on the device will be the device owner.
    1. Please note that if the device is AAD joined, the user that performed the join is made device owner.
    1. For more, see [Device Owner](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).
1. [Tenant lock](https://docs.microsoft.com/hololens/hololens-release-notes#tenantlockdown-csp-and-autopilot) the device so that it can only joined your tenant.
    1. **Additional Link:** [Tenant lock CSP](https://docs.microsoft.com/windows/client-management/mdm/tenantlockdown-csp).
1. Configure kiosk using global assigned access to [here](https://docs.microsoft.com/hololens/hololens-global-assigned-access-kiosk).
1. We recommend disabling the follow (optional) capabilities:
    1. Ability to put the device into developer mode [here](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock).
    1. Ability to connect the HoloLens to a PC to copy date [disable USB](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity#connectivity-allowusbconnection).
       > [!NOTE]
        > If you don’t want to disable USB but want the ability to apply a provisioning package to the device using USB, follow the instructions listed [**here**](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-allowaddprovisioningpackage).

1. Use [WDAC](https://docs.microsoft.com/hololens/windows-defender-application-control-wdac) to allow or black apps on the HoloLens 2 device.
1. Update Remote Assist to the latest version as part of the setup. There are two options to do this:
    1. This can be done by going to Windows **Microsoft Store --> Remote Assist --> and Update App**.
    1. Another method is to leave the HoloLens 2 plugged in overnight for auto update.
1. [Disable all settings pages](https://docs.microsoft.com/hololens/settings-uri-list) except the network settings to allow users to connect to guest networks at client sites.
1. [Manage HoloLens Updates](https://docs.microsoft.com/hololens/hololens-updates)
    1. Option to [control OS updates](https://docs.microsoft.com/mem/intune/protect/windows-update-for-business-configure#create-and-assign-update-rings) or allow to flow freely.
1. [Common Device Restrictions](https://docs.microsoft.com/hololens/hololens-common-device-restrictions).
