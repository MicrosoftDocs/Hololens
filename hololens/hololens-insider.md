---
title: Insider preview for Microsoft HoloLens
description: Learn how to get started with Insider builds and provide valuable feedback for our next major operating system update for HoloLens.
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: millerevan
ms.topic: article
ms.custom:
- CI 111456
- CSSTroubleshooting
audience: ITPro
ms.date: 5/10/2022
ms.localizationpriority:
ms.reviewer: bryanth
manager: lolab
appliesto:
- HoloLens 2
---

# Insider preview for Microsoft HoloLens

Welcome to the latest Insider Preview builds for HoloLens! It's simple to [get started](hololens-insider.md#start-receiving-insider-builds) and provide valuable feedback for our next major operating system update for HoloLens.

We recommend that for organizations that have moved, or are moving towards a scale production deployment, that a subset of test devices are kept on Insider builds to validate that new features and new builds work as expected.

## Windows Insider Release Notes

Looking for a new feature but don't see it? Check out the [release notes](hololens-release-notes.md) as many of our new features have been released as part of the main builds.

| Feature                                                | Description                                                                                                                            | User or Scenario |
|--------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|------------------|
| [New policies to speed up adding users](#policies-to-speed-up-adding-users)                          | New   policies we've enabled that allow IT Admins to skip for OOBE or adding new   users to devices                                    | IT   Admin       |
| Autopilot improvements                                 | Enabled   the Troubleshooter for Autopilot to work with HoloLens, as well as an option   to retry if it failed                         | IT   Admin       |
| [Manage users on device](#manage-users-on-device)                                 | New   policies to manage when to clear out users on the device                                                                         | IT   Admin       |
| [Intune improvement - Mixed Reality policies](#intune-improvement---mixed-reality-policies)            | MR   policies are now shown in Settings picker                                                                                         | IT   Admin       |
| [Intune improvement - Settings picker policies](#intune-improvement---settings-picker-policies)          | The   Settings picker now allows for selecting HoloLens 2 and filtering policies   applicable to the device                            | IT   Admin       |
| [Intune improvement - Update Connectivity](#intune-improvement---update-connectivity)               | Added   functionality to use the Update Connectivity page with HoloLens, to   troubleshoot non-updating devices                        | IT   Admin       |
| [Intune improvement - New columns for device properties](#intune-improvement---new-columns-for-device-properties) | Added   new columns in Intune's device page to let you track groups, app versions,   and custom fields                                 | IT   Admin       |
| New policy disable Wi-Fi auto recovery                 | ??????????????                                                                                                                         | IT   Admin       |
| [Captive portal on sign-in screen](#captive-portal-on-sign-in-screen)                       | New   policy that IT Admins can enable that allows the use of captive portals on   the sign in screen to assist in connecting to Wi-Fi | IT   Admin       |
| Clean up storage via MDM                               | Clean   up files via MDM                                                                                                               | IT   Admin       |
| Improvements for Camera in severe expose environments  | Improvement   to recording and streaming in areas with intense lighting                                                                | End   Users      |
| [Fixes improvements](#fixes-improvements)                                    | Fixes and improvements for   HoloLens.                                                                                                 | All              |


### IT Admin Checklist

PUT STUFF HERE FOR EACH NEW POLICY

AND EACH NEW INTUNE THING





### Policies to speed up adding users

As more and more customers move to scale their deployment of HoloLens devices to their many users they find they'd like to be able to set up a new user quickly on a device. In order to aid with this we've added four new policies that each allow to skip a specific screen in OOBE. When combined these screens allow for someone adding a new Azure AD user to a device to be up and running faster than before. These policies also have the added benefit of being able to have more fine tuning of your devices.

The new policies and screens they skip are:

| Policy          | What's skipped                                                                    |  Screenshot |
|------------------|-----------------------------------------------------------------------------------|---|
| Skip Calibration | The calibration run during OOBE. This can later be run via the Settings app.      | <img src="images/07-adjust-eyes.png" width="200px" alt="Adjust for your eyes"> |
| Skip Training    | How to open and close the Start menu. This can later be learned via the Tips app. | <img src="images/26-02-startmenu-learning.png" width="200px" alt="Learn how to use the start gesture, image 2"> |
| Location Consent | This skips the location consent page if the policy has been set.                  | <img src="images/setup-location-services.png" width="200px" alt="Enable location services"> |
| Speech Consent   | This skips the speech consent page if the policy has been set.                    | <img src="images/22-do-more-with-voice.png" width="200px" alt="Enable Cortana"> |

The OMA-URI of new policies:
`./Device/Vendor/MSFT/Policy/Config/MixedReality/SkipCalibrationDuringFirstExperience`
`./Device/Vendor/MSFT/Policy/Config/MixedReality/SkipTrainingDuringFirstExperience`
`./Device/Vendor/MSFT/Policy/Config/Privacy/DisablePrivacyExperience`

- Bool value

For more info on how to increase your set up speed for new users, check out our [guide on how to quickly set up new users.](hololens2-new-user-optimize.md)

### Autopilot improvements

We've enabled some new improvements for folks using Autopilot.




### Manage users on device

For some organization, they are fully at scale and have tons of different users on their HoloLens 2 devices. Some of these devices can be used by so many people they even hit the 64 user limit on the device. For those who have reached that limit, we've added in controls over how to delete old users off the device at controlled intervals. This can also be useful for other reasons, which include increased security be removing old accounts, or speeding up the Iris scanning processes on the sign-in screen (less users to match means a faster comparison.) We've enabled two methods to control when to clean up old users.

- On a regular schedule determined by you.
- Delete the oldest user when you add more than your custom maximum number of users.

The OMA-URI of new policies:
`./Device/Vendor/MSFT/Policy/Config/MixedReality/NEWPOLICYOMAURI`
`./Device/Vendor/MSFT/Policy/Config/MixedReality/NEWPOLICYOMAURI`

- Int value   // DOUBLE CHECK THIS LATER

### Intune improvement - Mixed Reality policies

In Microsoft Intune's UI, when adding new device configuration policies for mixed reality policies, users typically had to first know about the new polices by reading release notes like these, and then add them as custom OMA-URI policies. We're happy to announce we've improved the discoverability and usability of our Mixed Reality policies.

// NEEDS STEPS

// NEEDS SCREENSHOT

### Intune improvement - Settings picker policies

In addition to making our Mixed Reality policies more usable with the Settings picker, there's more. Now when using the settings picker you can filter by device. We've updating the naming convention and refreshed the list of policies offered when selecting the HoloLens 2 filter. This should allow you to create new configurations for HoloLens 2 devices in a faster and more efficient manner without needing to reference documentation on what's supported.

// NEEDS STEPS

// NEEDS SCREENSHOT

### Intune improvement - Update Connectivity

We are making it easier for organizations to ensure that devices are on the right operating system, ensuring that devices are running the latest updates. As the number of devices you have grows, you'll need to know not just what OS version your HoloLens devices are on, but also why they aren't updating. We're adapting a new tool within Intune's UI that you can now use for HoloLens to help understand what may be blocking those devices from updating.

You can read the original blog post on [the Update Connectivity page](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/achieve-better-patch-compliance-with-update-connectivity-data/ba-p/3073356) and if you are ready, try it out yourself!

// NEEDS STEPS

// NEEDS SCREENSHOT

### Intune improvement - New columns for device properties

When using Intune, the best way to get a view of your devices at a glance is to use the "All devices" page. This page is customizable and allows you to pick which, which items you want to see for your devices. Including from OS version, last check-in, primary user, and plenty more to pick from. We are now adding a three new columns by popular demand.

| New field | Value | What it does |
|---|---|---|
| Included in Group X | Yes or No | Lets you select a group, and tells you if that device is included in that group |
| App version for app X | Returns app version of selected app | Let's you confirm that your devices are all updated across your primary apps. |
| Custom Fields | A string value you set manually per device | Let's you self tag devices however you like. |

// NEEDS STEPS

// NEEDS SCREENSHOT

### New policy disable Wi-Fi auto recovery



### Captive portal on sign-in screen

This new feature is an opt-in policy that IT Admins can enable to help with the set up of new devices / new users. When this policy is turned on it allows a captive portal on the sign-in screen, which allows a user to enter credentials to connect to the Wi-Fi access point. If enabled, sign in will implement similar logic as OOBE to display captive portal if required.

MixedReality/AllowCaptivePortalBeforeSignIn

The OMA-URI of new policy:
`./Device/Vendor/MSFT/Policy/Config/MixedReality/AllowCaptivePortalBeforeSignIn`

- Bool value

### Clean up storage via MDM



### Improvements for Camera in severe expose environments



### Fixes improvements

- Free storage space, SSID, BSSID values are now displayed on Intune's hardware page for devices.
- It will be possible to issue an app uninstall command in the device context using EnterpriseModernAppManagement CSP.

### Upcoming Fixes and Improvements

- In-box OpenXR code updated. This is to provide best out-of-box experience for customers without Microsoft store access.

## Start receiving Insider builds

1. If you haven’t updated recently, please reboot your device to update state and get the latest build.
   1. The “Reboot device” voice command works well.
   1. You can also choose the restart button in Settings/Windows Insider Program.
1. On a HoloLens 2 device go to **Settings** > **Update & Security** > **Windows Insider Program** and select **Get started**.
1. Link the account you used to register as a Windows Insider.

> [!TIP]
> Once you enroll a device into Insider builds it is highly suggested you keep a set of test devices enrolled in Insider builds. This allows your organization to more easily validate builds as they come out. This makes for an easier experience and helps incase your normal production devices are blocked from insider builds.

> [!NOTE]
> In order to enroll your device in Insider builds, you'll need to enable optional telemetry. If you have not done this already, open the Settings app and select **Privacy** > **Diagnostics & feedback** and then select **Optional diagnostics data**.

Windows insider is now moving to Channels. The **Fast** ring will become the **Dev Channel**, the **Slow** ring will become the **Beta Channel**, and the **Release Preview** ring will become the **Release Preview Channel**. Here’s what that mapping looks like:

![Windows Insider Channels explanation.](images/WindowsInsiderChannels.png)

For more information, see [Introducing Windows Insider Channels](https://blogs.windows.com/windowsexperience/2020/06/15/introducing-windows-insider-channels) on Windows Blogs.
Then, select **Active development of Windows**, choose whether you'd like to receive **Dev Channel** or **Beta Channel** builds, and review the program terms.
Select **Confirm > Restart Now** to finish up. After your device has rebooted, go to **Settings > Update & Security > Check for updates** to get the latest build.

### Update error 0x80070490 work-around

If you encounter an update error 0x80070490 when updating on the Dev or Beta channel, try the following short-term work-around. It involves moving your insider channel, picking up the update and then moving your Insider channel back.

#### Stage one - Release Preview

1. Settings, Update & Security, Windows Insider Program, select **Release Preview Channel**.

2. Settings, Update & Security, Windows Update, **Check for updates**. After the update, continue on to Stage two.

#### Stage two - Dev Channel

1. Settings, Update & Security, Windows Insider Program, select **Dev Channel**.

2. Settings, Update & Security, Windows Update, **Check for updates**.

## FFU download and flash directions

To test with a flight signed ffu, you first have to flight unlock your device prior to flashing the flight signed ffu.

1. On PC:
    1. Download ffu to your PC from [https://aka.ms/hololenspreviewdownload](https://aka.ms/hololenspreviewdownload).

    1. Install ARC (Advanced Recovery Companion) from the Microsoft Store: [https://www.microsoft.com/store/productId/9P74Z35SFRS8](https://www.microsoft.com/store/productId/9P74Z35SFRS8).

1. On HoloLens - Flight Unlock: Open **Settings** > **Update & Security** > **Windows Insider Program** then sign up, reboot device.

1. Flash FFU - Now you can flash the flight signed FFU using ARC.

### Provide feedback and report issues

Please use [the Feedback Hub app](hololens-feedback.md) on your HoloLens to provide feedback and report issues. Using Feedback Hub ensures that all necessary diagnostics information is included to help our engineers quickly debug and resolve the problem.  Issues with the Chinese and Japanese version of HoloLens should be reported the same way.

> [!NOTE]
> Be sure to accept the prompt that asks whether you'd like Feedback Hub to access your Documents folder (select **Yes** when prompted).

## Note for developers

You are welcome and encouraged to try developing your applications using Insider builds of HoloLens.  Check out the [HoloLens Developer Documentation](https://developer.microsoft.com/windows/mixed-reality/development) to get started. Those same instructions work with Insider builds of HoloLens.  You can use the same builds of Unity and Visual Studio that you're already using for HoloLens development.

## Stop receiving Insider builds

If you no longer want to receive Insider builds of Windows Holographic, you can opt out when your HoloLens is running a production build, or you can [recover your device](hololens-recovery.md) using the Advanced Recovery Companion to recover your device to a non-Insider version of Windows Holographic.

> [!CAUTION]
> There is a known issue in which users who un-enroll from Insider Preview builds after manually reinstalling a fresh preview build would experience a blue screen. Afterwards they must manually recover their device. For full details on if you would be impacted or not, please view more on this [Known Issue](hololens-troubleshooting.md#blue-screen-after-unenrolling-from-insider-preview-on-a-device-flashed-with-an-insider-build).

To verify that your HoloLens is running a production build:

1. Go to **Settings > System > About**, and find the build number.

1. [See the release notes for production build numbers](hololens-release-notes.md).

To opt out of Insider builds:

1. On a HoloLens running a production build, go to **Settings > Update & Security > Windows Insider Program**, and select **Stop Insider builds**.

1. Follow the instructions to opt out your device.
