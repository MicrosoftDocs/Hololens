---
title: Share your HoloLens with multiple people
description: You can configure HoloLens to be shared by multiple Azure Active Directory accounts, or by multiple users that use a single account.
ms.prod: hololens
ms.sitesec: library
author: qianw211
ms.author: v-qianwen
ms.topic: article
ms.localizationpriority: medium
ms.date: 8/9/2021
ms.reviewer: 
manager: sean-kerawala
appliesto:
- HoloLens 2
---

# Share your HoloLens with multiple people

Sharing a HoloLens 2 device is a necessity in some work environments, like clean rooms, surgical suites, etc. This article will outline the two different scenarios when using a HoloLens in a shared environment, and some best practices when doing so.

## Shared device use cases

### Share with multiple people, each using their own account

This is the preferred and most secure identity use case for a HoloLens 2 user. When they use their own Azure Active Directory (Azure AD) accounts, multiple users can each keep their own user settings and user data on the device. Only one user can be signed in at a time. When a user signs in, HoloLens signs out the previous user.

To make sure that multiple people can use their own accounts on your HoloLens, follow these steps to configure it:

1. When you set up the device, select **My work or school owns it** and sign in by using an Azure AD account.
1. After you finish setup, make sure that the account settings (**Settings** > **Accounts**) includes **Other users**.

To use HoloLens, each user follows these steps:

1. If another user has been using the device, do one of the following:
   - Press the power button once to go to standby, and then press the power button again to return to the lock screen
   - Select the user tile from the Start menu or choose Sign out from the Power menu to sign out the current user.

1. Use your Azure AD account credentials to sign in to the device.  
    - If this is the first time you have used the device, it will ask you to [calibrate](hololens-calibration.md) the HoloLens to your own eyes. 
    - If you previously used the device:
        -  Windows Holographic, version 20H2, build 19041.1128 or higher, the display seamlessly adjusts for quality and a comfortable viewing experience. 
        - Previous builds will need manual calibration to adjust to your eyes.

To see a list of the device users or to remove a user from the device, go to **Settings** > **Accounts** > **Other users**.

### Best practices
- [Identity and Authentication](hololens-identity.md) - Azure AD accounts with all modes of authentication through [Windows Hello](/windows-hardware/design/device-experiences/windows-hello), including Iris and FIDO2 keys.
- [Device Management](hololens-csp-policy-overview.md) - manage device updates and configurations, including [device restrictions](hololens-common-device-restrictions.md) through MDM or provisioning packages.
- [Kiosk](hololens-kiosk.md) or [WDAC](windows-defender-application-control-wdac.md) to hide or restrict apps. 
- Physical Management - ensure devices are charging between shifts.

### Share with multiple people, all using the same account

Multiple users can also share a HoloLens device while using a single user account. Although it is preferred for HoloLens users to login to the device with their individual identities (Azure AD accounts), this is not an option in some organizations.

There are 2 shared device methods available:

- **Multiple end users sharing 1 device** - a HoloLens device is allocated to a designated space where any employee can use the device. Examples would be a clean room or surgical suite. 

- **Multiple end users sharing multiple devices** - HoloLens devices are in a shared storage space where employees can use any device. Examples would be an oil rig or an auto dealership/garage.


When a new user puts the device on their head for the first time (while keeping the same account signed in), the device prompts the new user to quickly calibrate and personalize the viewing experience. The device can store the calibration information so that in the future, the device can automatically optimize the quality and comfort of each user's viewing experience. The users do not need to calibrate the device again.

### Best practices
- [Identity and Authentication](hololens-identity.md) - device or local account with password or  PIN authentication.
- [Device Management](hololens-csp-policy-overview.md) - manage device updates and configurations, including [device restrictions](hololens-common-device-restrictions.md) through MDM or provisioning packages.
- [Kiosk](hololens-kiosk.md) or [WDAC](windows-defender-application-control-wdac.md) to hide or restrict apps. 
- Physical Management - separate management system or on-site manager to keep devices updated and compliant, ensure devices are charging between shifts.