---
title: Share your HoloLens with multiple people
description: You can configure HoloLens to be shared by multiple Azure Active Directory accounts, or by multiple users that use a single account.
ms.prod: hololens
ms.sitesec: library
author: qianw211
ms.author: v-qianwen
ms.topic: article
ms.localizationpriority: medium
ms.date: 9/22/2021
ms.reviewer: anisgup
manager: sean-kerawala
appliesto:
- HoloLens 2
---

# Share your HoloLens with multiple people

## Overview

Businesses often invest in many shared HoloLens devices. It's common to share a HoloLens 2 device in some work environments such as clean rooms, surgical suites, etc. This article will outline the two different scenarios when using a HoloLens in a shared environment, and some best practices when doing so. How you use HoloLens is flexible across the board, depending on your individual requirements. Here’s an example of some multi-user experiences:

- Devices which are charged and have Dynamics 365 Guides and allow your employees to open the Settings app to make adjustments to Wi-Fi needed, but Page Settings Visibility policy is enabled to limit the amount pages available in the Settings app.
- Devices which are for Remote Assist, and your line of business app which are rented to other companies. These devices have Kiosks that include only your app and Remote Assist. WDAC is used to keep the Settings app and Microsoft Edge from launching. Included with the rental is a USB-C battery pack to keep the devices at full charge over multiple shifts.
- All your devices are set up for Autopilot and download all of your company apps. You've set up a few different Kiosk profiles, targeting different Azure AD groups. Each user logs into the HoloLens using FIDO2 keys and signing into their own Azure AD account, and is presented with a tailored experience.

## Best practices

When planning to share your devices, there are several topics to consider how to best share devices.

### [Identity and Authentication](hololens-identity.md)

If you're planning on having multiple accounts on a device, then you'll have Azure AD accounts with all modes of authentication. These authentication methods will be based on [Windows Hello](/windows-hardware/design/device-experiences/windows-hello), including Iris and FIDO2 keys.

- FIDO 2 Security keys are excellent if you have multiple devices, many users, or are constantly using new devices.
- If you have 10 or fewer users, Iris is a fast solution to sign in users who have previously signed into the same device.

### [Device Management](hololens-csp-policy-overview.md)

If devices are being shared between users, then you'll likely want to use device restrictions. By using device management you can set some policies to either better enable your users to use the device, manage updates, or limit what the device can do. It is recommended you review our [common device restrictions](hololens-common-device-restrictions.md), and see if these recommendations seem to fit with your organization. Once you know what policies you want to use, you can apply them through [Microsoft's Endpoint Manager (MDM)](hololens-mdm-configure.md) or provisioning packages.

### Advanced device management - [Kiosk](hololens-kiosk.md) and [WDAC](windows-defender-application-control-wdac.md)

In some cases, you may want to limit what applications can be accessed by the end users. You could be limiting what apps users are presented with on the start menu using [Kiosk mode](hololens-kiosk.md). Kiosk can be configured to present different start menus based on user, Azure groups, or special user types; such visitor or excluding device owners. You can choose multiple apps, or just a single app. A multi app kiosk doesn't stop one app from launching another, so if the store or another app is available users can still launch another app.

You may also want to completely stop the launching of apps or services using [Windows Defender Application Control (WDAC)](windows-defender-application-control-wdac.md) to restrict apps. WDAC is different that Kiosk, because it doesn't change the UI of HoloLens but instead does not allow a blocked app to launch.

[Page Settings Visibility](settings-uri-list) is another way to add restrictions to a device. In the event you need to grant users access to some pages in the Settings app, but not all you can use Page Settings Visibility to limit access. This is useful for example, if your users need to change the Wi-Fi, but you don't want them to access the Accounts page.

### Physical Management

When sharing the device between multiple users, there are some physical considerations.

- Ensure devices are charging between shifts.
- If a device is required for a shift, and needs to last multiple shifts consider using an external battery at the start of a shift while the device still has significant charge per the [managing heat directions](hololens2-charging.md#managing-heat).
- When storing devices keep them plugged in and connected to a network. This is the best way to ensure OS and app updates.
- Consider how you plan to [clean the device](hololens2-maintenance.md) between users.
- For a device with a single shared user if using a shared PIN/password for a single user, don't put the PIN/password on the side of the device.
- For multiple devices with a single shared user, use various PINs/passwords.

## Share with multiple people, each using their own account

Individual Azure Active Directory (Azure AD) accounts are the preferred and most secure identity use case for HoloLens 2 users. When using their own Azure AD accounts, multiple users can each keep their own user settings and user data on the device. Only one user can be signed in at a time. When a user signs in, HoloLens signs out the previous user.

To make sure that multiple people can use their own accounts on your HoloLens, follow these steps to configure it:

1. When you [set up the device](hololens2-start.md), select **My work or school owns it** and sign in by using an Azure AD account.
1. After you finish setup, make sure that the account settings (Settings > Accounts) include **Other users**.

> [!NOTE]
> If your device was not set up with an Azure AD account it need to be either [reset or reflashed](hololens-recovery.md) and set up properly.

To use HoloLens, each user follows these steps:

1. If another user has been using the device, choose one of the following options:
   - Press the power button once to go to standby, and then press the power button again to return to the lock screen
   - Select the user tile from the **Start menu** or choose sign out from the **Power menu** to sign out the current user.

1. Use your Azure AD account credentials to sign in to the device.  
    - If it's the first time you have used the device, it will ask you to [calibrate](hololens-calibration.md) the HoloLens to your own eyes.
    - If you previously used the device:
        - [Windows Holographic, version 20H2, build 19041.1128](hololens-release-notes.md#windows-holographic-version-20h2) or higher, the display seamlessly adjusts for quality and a comfortable viewing experience.
        - Previous builds will need manual calibration to adjust to your eyes.

> [!TIP]
> If a user hasn't signed into a device yet try one of these two methods for a faster login:
>
> - **FIDO 2 Security key** : Your FIDO2 security key will be automatically recognized and the user won't need to type in their user credentials or use MFA. This is the fastest method to sign in on a new device.
> - **Web authentication** : When you sign into a new device, you can select the link **Sign in from another device** which will generate a 9 character code you can use at [aka.ms/devicelogin](https://login.microsoftonline.com/common/oauth2/deviceauth) to either sign in as the user on the device, or type your user name and password using a keyboard for your convenience.

To see a list of the device users or to remove a user from the device, go to **Settings** > **Accounts** > **Other users**.

## Share with multiple people, all using the same account

Multiple users can also share a HoloLens device while using a single user account. Although it is preferred for HoloLens users to log in to the device with their individual identities (Azure AD accounts), this is not an option in some organizations.

There are two shared device methods available:

- **Multiple end users sharing 1 device** - a HoloLens device is allocated to a designated space where any employee can use the device. Examples would be a clean room or surgical suite.

- **Multiple end users sharing multiple devices** - HoloLens devices are in a shared storage space where employees can use any device. Examples would be an oil rig or an auto dealership/garage.

When a new user puts on the device for the first time while keeping the same account signed in, the device prompts the user to quickly calibrate and personalize the viewing experience. The device will store the calibration information to automatically optimize the quality and comfort of each user's viewing experience. Users won't need to calibrate the device again.
