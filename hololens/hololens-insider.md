---
title: Insider preview for Microsoft HoloLens
description: Learn how to get started with Insider builds and provide valuable feedback for our next major operating system update for HoloLens.
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: millerevan
manager: lolab
ms.reviewer: bryanth
ms.topic: article
ms.custom:
- CI 111456
- CSSTroubleshooting
audience: ITPro
ms.date: 5/25/2022
ms.localizationpriority:
appliesto:
- HoloLens 2
---

# Insider preview for Microsoft HoloLens

Welcome to the latest Insider Preview builds for HoloLens! It's simple to [get started](hololens-insider.md#start-receiving-insider-builds) and provide valuable feedback for our next major operating system update for HoloLens.

We recommend that for organizations that have moved, or are moving towards a scale production deployment, that a subset of test devices is kept on Insider builds to validate that new features and new builds work as expected.

## Windows Insider Release Notes

Looking for a new feature but don't see it? Check out the [release notes](hololens-release-notes.md) as many of our new features have been released as part of the main builds.

| Feature                                                | Description                                                                                                                            | User or Scenario |
|--------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|------------------|
| [New policies to speed up adding users](#policies-to-speed-up-adding-users)                          | New   policies we've enabled that allow IT Admins to skip for OOBE or adding new   users to devices                                    | IT   Admin       |
| [Autopilot restart](#autopilot-restart)                                 | Enabled   the Troubleshooter for Autopilot to work with HoloLens, and an option   to retry if it failed                         | IT   Admin       |
| [Clean up users on device](#clean-up-users-on-device)                                 | New   policies to manage when to clear out users on the device                                                                         | IT   Admin       |
| [New policy disable Wi-Fi auto recovery](#new-policy-disable-wi-fi-auto-recovery)                 | Turn off auto-reconnect to Wi-fi access points                                                                                                                         | IT   Admin       |
| [Captive portal on sign-in screen](#captive-portal-on-sign-in-screen)                       | New   policy that IT Admins can enable that allows the use of captive portals on   the sign-in screen to help connecting to Wi-Fi | IT   Admin       |
| [Clean up storage via MDM](#clean-up-storage-via-mdm)                               | Clean   up files via MDM                                                                                                               | IT   Admin       |
| [Fixes improvements](#fixes-improvements)                                    | Fixes and improvements for   HoloLens.                                                                                                 | All              |


### IT Admin Checklist

✔️ If you'd like to speed up new user sign-ons check out the new [new policies to speed up adding users](#policies-to-speed-up-adding-users). <br>
✔️ If you need to delete users from your HoloLens automatically then check out how to [manage users on device](#manage-users-on-device). <br>
✔️ If you need to keep your devices from auto-connecting to Wi-Fi access points then learn how to [disable Wi-Fi auto recovery](#new-policy-disable-wi-fi-auto-recovery). <br>
✔️ Trying to remotely troubleshoot a device, but don't have enough room to gather logs? Try to [clean up some storage space using MDM](#clean-up-storage-via-mdm).

### Policies to speed up adding users

As you scale deployment of your HoloLens devices across your enterprise, you can set up new users more quickly through these new policies that allow you to skip steps in your Out-of-Box-Experience (OOBE). There are four new areas you'll be able to by-pass. When combined these screens allow for someone adding a new Azure AD user to a device to be up and running faster than before. These new policies enable you to apply even more fine tuning across your device inventory.

The new policies and screens they skip are:

| Policy          | What's skipped                                                                    |  Screenshot |
|------------------|-----------------------------------------------------------------------------------|---|
| Skip Calibration | The calibration run during OOBE, which can later be run via the Settings app.      | <img src="images/07-adjust-eyes.png" width="200px" alt="Adjust for your eyes"> |
| Skip Training    | How to open and close the Start menu, which can later be learned via the Tips app. | <img src="images/26-02-startmenu-learning.png" width="200px" alt="Learn how to use the start gesture, image 2"> |
| Location Consent | This policy skips the location consent page if the policy has been set.                  | <img src="images/setup-location-services.png" width="200px" alt="Enable location services"> |
| Speech Consent   | This policy skips the speech consent page if the policy has been set.                    | <img src="images/22-do-more-with-voice.png" width="200px" alt="Enable Cortana"> |

The [OMA-URI](/troubleshoot/mem/intune/deploy-oma-uris-to-target-csp-via-intune) (Open Mobile Alliance Uniform Resource Identifier) of new policies:

- `./Device/Vendor/MSFT/Policy/Config/MixedReality/SkipCalibrationDuringFirstExperience`
- `./Device/Vendor/MSFT/Policy/Config/MixedReality/SkipTrainingDuringFirstExperience`
- `./Device/Vendor/MSFT/Policy/Config/Privacy/DisablePrivacyExperience`

- Bool value

For more info on how to increase your setup speed for new users, check out our [guide on how to quickly set up new users.](hololens2-new-user-optimize.md)

### Autopilot restart

In some cases, a user might experience an issue during Autopilot that prevents it from completing. For situations like this, we've enabled the restart button to allow the user to restart the autopilot flow. This new button will be available on the Enrollment Status Page that is shown during the Autopilot process. 

// NEEDS SCREENSHOT
![screenshotofthing](aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa)


### Clean up users on device

Organizations with scaled deployments of HoloLens 2 devices may encounter the 64-user limit on the device, which will prevent additional users from being able to use the device. To address this situation, we've added controls allow old users to be deleted from the device at controlled intervals (something you have may have used on Desktop). This can also be useful for other reasons, which include increased security be removing old accounts, or speeding up the Iris scanning processes on the sign-in screen (fewer users to match means a faster comparison.) We've enabled two methods to control when to clean up old users.

There are two triggers that can delete users:

- On a regular schedule determined by you.
- Delete the oldest user when you add more than your custom maximum number of users.

Here's how to get started:

1. Enable the process: **UserProfileManagement/EnableProfileManager**
    1. Bool value, set to **True**
1. Set the inactivity threshold: **UserProfileManagement/ProfileInactivityThreshold**
    1. This is the number of days until a user is deleted. 
        - Default value is 30.
1. Set the maximum users on device **UserProfileManagement/StorageCapacityStartDeletion**
    1. This determines how many users can be on the device. 
        - Default value is 25.
        - Maximum for HoloLens is 64.
1. Turn on the deletion policy **UserProfileManagement/DeletionPolicy**, and set it to **2**, which deletes for both threshold and inactive users.

To learn more about these policies, visit [AccountManagement CSP](/windows/client-management/mdm/accountmanagement-csp).

### New policy to disable Wi-Fi auto recovery

Wi-Fi auto recovery is enabled on HoloLens 2 by default. In some cases you may want your devices to not automatically reconnect. This may be because you have a preferred network you want to keep your devices on, you find yourself reconnecting to an access point that doesn't have internet, or you want to keep those devices offline in specific areas. For those cases we've enabled a new policy that you can opt to use to keep your devices from automatically reconnecting back to your access points.

The OMA-URI of new policies:
`./Device/Vendor/MSFT/Policy/Config/MixedReality/NEWPOLICYOMAURI`

- Bool value // DOUBLE CHECK THIS LATER

### Captive portal on sign-in screen, enter Wi-Fi credentials to help sign-in

Sometimes Wi-Fi connections require additional information to provide credentials to the access point. Previously users were only able to do this the first time the device was set up in OOBE, or in the Settings app once signed in. Previously, users couldn't adjust this configuration on the sign-in screen, which was sometimes tricky to work around. 

This new feature is an opt-in policy that IT Admins can enable to help with the setup of new devices in new areas or new users. When this policy is turned on it allows a [captive portal](/windows-hardware/drivers/mobilebroadband/captive-portals) on the sign-in screen, which allows a user to enter credentials to connect to the Wi-Fi access point. If enabled, sign in will implement similar logic as OOBE to display captive portal if necessary.

// NEEDS SCREENSHOT
![screenshotofthing](aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa)

MixedReality/AllowCaptivePortalBeforeSignIn

The OMA-URI of new policy:
`./Device/Vendor/MSFT/Policy/Config/MixedReality/AllowCaptivePortalBeforeSignIn`

- Bool value

### Clean up storage via MDM

	In some scenarios, a device may require more space, so we've enabled a new way to clean up your temporary files / data on a device. Some of these files can be logs, crash dumps, downloads, or other files no longer needed on the device. We've created a way for both users and IT admins to delete these files. Here's how:

#### End user cleanup

End users can find this button on their device in the Settings app.

//////////////////////
WIP STEPS UNTIL WE BUILD THE UI / FEATURE 

1. Open the Settings app
1.  // ......................... select the buttons and do the things

// NEEDS SCREENSHOT
![screenshotofthing](aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa)

#### IT Admin clean up

It admins can start the same process as end users. They can do it by:

1. // STEPS AND THINGS DEPENDING ON WHAT CSP WE END UP USING

END WIP
////////////////////////

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

To test with a flight signed `.ffu`, you first have to flight unlock your device prior to flashing the flight signed ffu.

1. On PC:
    1. Download `.ffu` to your PC from [https://aka.ms/hololenspreviewdownload](https://aka.ms/hololenspreviewdownload).

    1. Install ARC (Advanced Recovery Companion) from the Microsoft Store: [https://www.microsoft.com/store/productId/9P74Z35SFRS8](https://www.microsoft.com/store/productId/9P74Z35SFRS8).

1. On HoloLens - Flight Unlock: Open **Settings** > **Update & Security** > **Windows Insider Program** then sign up, reboot device.

1. Flash FFU - Now you can flash the flight signed FFU using ARC.

### Provide feedback and report issues

Please use [the Feedback Hub app](hololens-feedback.md) on your HoloLens to provide feedback and report issues. Using Feedback Hub ensures that all necessary diagnostics information is included to help our engineers quickly debug and resolve the problem.  Issues with the Chinese and Japanese version of HoloLens should be reported the same way.

> [!NOTE]
> Be sure to accept the prompt that asks whether you'd like Feedback Hub to access your Documents folder (select **Yes** when prompted).

## Note for developers

You're welcome and encouraged to try developing your applications using Insider builds of HoloLens.  Check out the [HoloLens Developer Documentation](https://developer.microsoft.com/windows/mixed-reality/development) to get started. Those same instructions work with Insider builds of HoloLens.  You can use the same builds of Unity and Visual Studio that you're already using for HoloLens development.

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
