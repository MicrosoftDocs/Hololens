---
title: Deployment Guide – Cloud connected HoloLens 2 deployment at scale with Remote Assist - Configure
description: Learn how to set up configurations to enroll HoloLens devices over a Cloud Connected network at scale with Remote Assist.
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

# Configure - Cloud connected Guide

In this section of the guide, we&#39;ll go over how to set up Auto Enrollment for your tenant, and how to apply licenses for both Intune and Remote Assist.

## Azure Users and Groups

Azure, and Intune by that extension, uses users and groups to help assign configurations and licenses. For the sake of validating this deployment flow and being able to make a Remote Assist call from one user to another you&#39;ll need two user accounts.

We can make a single user group for the purpose of assigning licenses. We can join both users to the same group and apply a license for Intune and Remote Assist to that group.

If you don&#39;t already have access to two Azure AD accounts in a user group you can use; here are the quick start guides for:

- [How to create a user](https://docs.microsoft.com/mem/intune/fundamentals/quickstart-create-user)
- [How to create a group](https://docs.microsoft.com/mem/intune/fundamentals/quickstart-create-group)
- [Add users to a group](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-members-azure-portal) – Add created users to create group
- [Configure Azure AD to allow a User Group to join devices](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan#configure-your-device-settings) – Ensure new user group has permission to enroll devices to Azure AD

## Auto Enrollment on HoloLens 2

In order to have a smooth and seamless experience, setting up Azure Active Directory Join (AADJ) and Auto Enrollment to Intune for HoloLens 2 devices is the way to go. This will allow users to input their organization log-in credentials during OOBE and automatically register with Azure AD and enroll the device into MDM.

By using [Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home), we can select services and navigate a few pages until we can select Get a Premium trial. You may notice there is Azure Active Directory Premium 1 and 2, for Automatic Enrollment P1 is sufficient. We can select Intune and select the user scope for automatic enrollment, and select the group that was previously created.

For full details and steps read the guide on [how to enable auto enrollment for Intune](https://docs.microsoft.com/mem/intune/enrollment/quickstart-setup-auto-enrollment).

## Application Licenses

An application license allows a user to either install company purchased Apps or upgrade from a free trial to the full version of an app. Application licenses can be applied to either users, user groups, or device groups. You&#39;ll need Remote Assist licenses for users in your organization to use Remote Assist. For the purpose of this guide we'll assign Remote Assist licenses to the user group we created above in [Azure Users and Groups](hololens2-cloud-connected-configure.md#azure-users-and-groups).

The requirements for licenses can be different depending on if the user will be making the Remote Assist call from a device or will be a remote collaborator from Microsoft Teams. By default the Remote Assist and Teams check boxes are both marked. For the purposes of this guide, we suggest leaving the default boxes checked.

1. Learn more about the different [Licensing and product requirements per role](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/requirements#licensing-and-product-requirements-per-role). There are a few different types of Remote Assist licenses so be sure to get the correct ones for your needs.
2. You&#39;ll need to [acquire the license](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/buy-remote-assist).
3. [Apply your licenses](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/deploy-remote-assist) to the group.

## Next step

> [!div class="nextstepaction"]
> [Cloud connected deployment - Deploy](hololens2-cloud-connected-deploy.md)