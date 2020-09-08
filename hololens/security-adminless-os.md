---
title: security adminless os
description: adminless os and hololens security
author: evmill
ms.author: v-evmill
ms.date: 6/30/2020
ms.topic: article
keywords: security, hololens, adminless, admin-less, operating system, admin-less operating system, admin os, admin-less os, hololens 2, hololens2 security, 
ms.localizationpriority: high
ms.reviewer: 
manager: yannisle
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Admin-less operating system

HoloLens 2 minimizes the surface area for privilege escalation by disabling support for the Administrators group and limiting all third-party UWP application code to only execute as standard users within the AppContainer sandbox. This code is only granted access to those resources protected by capabilities explicitly manifested in the application for an unelevated user in addition to resources accessible to all AppContainers.
These application capabilities continue to have the three-tiered classification model:
  * General
  * Restricted
  * Windows

Windows components can also leverage the AppContainer sandbox through System UWPs. To learn more about Universal Windows Platform (UWP), see [UWP documentation](https://docs.microsoft.com/windows/uwp/). Additionally, Windows components with greater privilege reduction needs (e.g. browser content pages, parsers) use the Less Privileged AppContainer (LPAC) sandbox which cuts off access to the set of resources accessible to all AppContainers.

Finally, the execution of specific device-wide operations, such as joining the device to a tenant or user management, is only permitted for “device owners”. This group is populated by users on the device through one of the following steps:
  * The first user on the device is always designated an Owner. 
    * The exception to this rule is that if the device is AAD joined, the user that performed the join is made device owner. This is applicable, for example, if a device is AAD joined via Autopilot in which case the first user to sign into the device did not AAD join the device and therefore will not be made a device owner. To understand more about who is made a device owner on an AAD joined device, see [“Assign Local Admin” documentation](https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin) (but read ‘local admin’ as ‘device owner’ since admin does not exist on HoloLens).
  * When a user is promoted to be an Owner from Settings UX by another Owner on the device.
  * If the device owner is no longer available (e.g. leaves the company) and the device is AAD joined, the Tenant Admin can change the device owner to a new user in Azure Portal.
Global Administrators of an Azure AD tenant are implicitly signed in as Owners on the device without requiring either of the previous steps. 

IT administrators can manage what apps can access through [Privacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-privacy) policies. 
