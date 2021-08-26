---
title: Share your HoloLens with multiple people
description: You can configure HoloLens to be shared by multiple Azure Active Directory accounts, or by multiple users that use a single account.
ms.prod: hololens
ms.sitesec: library
author: qianw211
ms.author: v-qianwen
ms.topic: article
ms.localizationpriority: medium
ms.date: 08/26/2021
ms.reviewer: 
manager: sekerawa
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Share your HoloLens with multiple people

## Overview

Businesses often invest in many shared HoloLens devices. Security with HoloLens is flexible across the board, depending on your individual requirements. Here’s an example of a locked-down experience: 

- Workers can check out a HoloLens to perform a certain task. Thanks to Microsoft Intune and other provisioning profiles, you can be certain that a worker uses HoloLens only in the way it’s intended. For instance, they can use Remote Assist, but they can’t open Web browsers, games, Word, etc.

The results are impressive. Even in the most sensitive environments, information sharing and visuals are unique to the end user’s eyes, so collaboration can thrive. Imagine a trans-oceanic and real-time collaboration using Remote Assist. HoloLens sharing brings new interactions, without risking unwarranted information disclosure.

## Share with multiple people, each using their own account

**Prerequisite**: The HoloLens device must be running Windows 10, version 1803 or later.  HoloLens (1st gen) also need to be [upgraded to Windows Holographic for Business](hololens-upgrade-enterprise.md).

When they use their own Azure Active Directory (Azure AD) accounts, multiple users can each keep their own user settings and user data on the device.

To make sure that multiple people can use their own accounts on your HoloLens, follow these steps to configure it:

1. Make sure the device is running Windows 10, version 1803 or later.
   > [!IMPORTANT]
   > If you are using a HoloLens (1st gen) device, [upgrade the device to Windows Holographic for Business](hololens1-upgrade-enterprise.md).
1. When you set up the device, select **My work or school owns it** and sign in by using an Azure AD account.
1. After you finish setup, make sure that the account settings (**Settings** > **Accounts**) includes **Other users**.

To use HoloLens, each user follows these steps:

1. If another user has been using the device, choose one of the following options:
   - Press the power button once to go to standby, and then press the power button again to return to the lock screen
   - HoloLens 2 users may select the user tile from the Start menu to sign out the current user.

1. Use your Azure AD account credentials to sign in to the device.  
    If it's the first time that you have used the device, you have to [calibrate](hololens-calibration.md) HoloLens to your own eyes.

To see a list of the device users or to remove a user from the device, go to **Settings** > **Accounts** > **Other users**.

## Share with multiple people, all using the same account

Multiple users can also share a HoloLens device while using a single user account.

**On HoloLens 2**, when a new user puts the device on their head for the first time (while keeping the same account signed in), the device prompts the new user to quickly calibrate and personalize the viewing experience. The device can store the calibration information so that in the future, the device can automatically optimize the quality and comfort of each user's viewing experience. The users do not need to calibrate the device again.

**On HoloLens (1st gen)** users sharing an account will need to ask to recalibrate in the Settings app.  Read more about [calibration](hololens-calibration.md).