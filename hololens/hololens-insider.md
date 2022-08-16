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
ms.date: 8/15/2022
ms.localizationpriority: high
appliesto:
- HoloLens 2
---

# Insider preview for Microsoft HoloLens

Welcome to the latest Insider Preview builds for HoloLens! It's simple to [get started](hololens-insider.md#start-receiving-insider-builds) and provide valuable feedback for our next major operating system update for HoloLens.

We recommend that for organizations that have moved, or are moving towards a scale production deployment, that a subset of test devices is kept on Insider builds to validate that new features and new builds work as expected.

## Windows Insider Release Notes

Looking for a new feature but don't see it? Check out the [release notes](hololens-release-notes.md) as many of our new features have been released as part of the main builds.

> [!NOTE]
> In order to receive these features on your devices they will need to be in the [Dev channel](#start-receiving-insider-builds).

> [!IMPORTANT]
> This next update is on a newer code base than what is currently generally available. Once you update a device to it, you won't be able to have your device update to our monthly releases until they catch up with the same codebase. Although if need be, you can still flash your device to go back.

| Feature   | Description  | User or Scenario | Available in build |
|-----------|--------------|------------------|---|
| [New policies to speed up adding users](#policies-to-speed-up-adding-users) | New policies we've enabled that allow IT Admins to skip for OOBE or adding new users to devices. | IT Admin | 10.0.22621.1008 |
| [Autopilot reset experience](#autopilot-reset-experience) | Improvements in Autopilot reset experience, to enable users to reset HoloLens 2 and restart Autopilot without requiring manual flashing.| IT Admin  | 10.0.22621.1006 |
| [Clean up users on device](#clean-up-users-on-device) | New policies to manage when to clear out users on the device.  | IT Admin  | 10.0.22621.1008 |
| [New policy to disable NCSI passive polling](#new-policy-to-disable-ncsi-passive-polling) | Turn off auto-reconnect to Wi-fi access points. | IT Admin       | 10.0.22621.1008 |
| [Captive portal on sign-in screen, enter Wi-Fi credentials to help sign-in](#captive-portal-on-sign-in-screen-enter-wi-fi-credentials-to-help-sign-in)  | New policy that IT Admins can enable that allows the use of captive portals on the sign-in screen to help connecting to Wi-Fi. | IT Admin | 10.0.22621.1006 |
| [Clean up storage via MDM](#clean-up-storage-via-mdm) | Clean up files via MDM.  | IT Admin | 10.0.22621.1008 |
| [Security Baseline](#security-baseline) | A list of security restrictions you can use. | IT Admin | 10.0.22621.1006 |
| [Fixes improvements](#fixes-improvements)  | Fixes and improvements for HoloLens.  | All   | 10.0.22621.1006 |

### IT Admin Checklist

✔️ If you'd like to speed up new user sign-ons check out the new [new policies to speed up adding users](#policies-to-speed-up-adding-users). <br>
✔️ If you need to delete users from your HoloLens automatically then check out how to [manage users on device](#clean-up-users-on-device). <br>
✔️ If you need to keep your devices from auto-connecting to Wi-Fi access points then learn how to [disable Wi-Fi auto recovery](#new-policy-to-disable-ncsi-passive-polling). <br>
✔️ Trying to remotely troubleshoot a device, but don't have enough room to gather logs? Try to [clean up some storage space using MDM](#clean-up-storage-via-mdm). <br>
✔️ If you need to have more security, are planning on vending out your devices, or need to check a box for a security review, check out the [security baseline](#security-baseline).

List of new or newly enabled policies:

- `MixedReality/AllowCaptivePortalBeforeSignIn`
- `MixedReality/SkipCalibrationDuringSetup`
- `MixedReality/SkipTrainingDuringSetup`
- `MixedReality/DisallowNetworkConnectivityPassivePolling`
- `Storage/AllowStorageSenseGlobal`
- `Storage/AllowStorageSenseTemporaryFilesCleanup`
- `Storage/ConfigStorageSenseCloudContentDehydrationThreshold`
- `Storage/ConfigStorageSenseDownloadsCleanupThreshold`
- `Storage/ConfigStorageSenseGlobalCadence`

### Policies to speed up adding users

As you scale deployment of your HoloLens devices across your enterprise, you can set up new users more quickly through these new policies that allow you to skip steps in your Out-of-Box-Experience (OOBE). There are two new areas you'll be able to by-pass. When combined these screens allow for someone adding a new Azure AD user to a device to be up and running faster than before. These new policies enable you to apply even more fine tuning across your device inventory.

The new policies and screens they skip are:

| Policy          | What's skipped                                                                    |  Screenshot |
|------------------|-----------------------------------------------------------------------------------|---|
| Skip Calibration | The calibration run during OOBE, which can later be run via the Settings app. <br> Using: `SkipCalibrationDuringSetup`      | <img src="images/07-adjust-eyes.png" width="200px" alt="Adjust for your eyes"> |
| Skip Training    | How to open and close the Start menu, which can later be learned via the Tips app. <br> Using: `SkipTrainingDuringSetup`  | <img src="images/26-02-startmenu-learning.png" width="200px" alt="Learn how to use the start gesture, image 2"> |

The [OMA-URI](/troubleshoot/mem/intune/deploy-oma-uris-to-target-csp-via-intune) (Open Mobile Alliance Uniform Resource Identifier) of new policies:

- `./Device/Vendor/MSFT/Policy/Config/MixedReality/SkipCalibrationDuringSetup`
- `./Device/Vendor/MSFT/Policy/Config/MixedReality/SkipTrainingDuringSetup`

- Int value
  - 0 : Keep the experience (default)
  - 1 : Skip

For more info on how to increase your setup speed for new users, check out our [guide on how to quickly set up new users.](hololens2-new-user-optimize.md)

### Autopilot reset experience

In certain Autopilot failure scenarios on HoloLens 2, if "Allow users to reset device if installation error occurs." setting in ESP configuration is set to "Yes", "Reset device" button will be displayed on HoloLens 2. If "Reset device" button is selected by the user, HoloLens 2 will automatically reboot, reset operating system and OOBE experience after delay of approximately 1 minute. This improvement will enable users to begin Autopilot experience again without requiring a manual flash of HoloLens 2 devices.

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

### New policy to disable NCSI passive polling

Windows Network Connectivity Status Indicator may get false positive Internet capable signal from passive polling. Which may result in unexpected Wi-Fi adapter reset when device connects to an intranet only access point. Enabling this policy would avoid unexpected network interruptions caused by false positive NCSI passive polling.

The OMA-URI of new policies:
`./Device/Vendor/MSFT/Policy/Config/MixedReality/DisallowNetworkConnectivityPassivePolling`

- Bool value

### Captive portal on sign-in screen, enter Wi-Fi credentials to help sign-in

Sometimes Wi-Fi connections require additional information to provide credentials to the access point. Previously users were only able to do this the first time the device was set up in OOBE, or in the Settings app once signed in. Previously, users couldn't adjust this configuration on the sign-in screen, which was sometimes tricky to work around.

This new feature is an opt-in policy that IT Admins can enable to help with the setup of new devices in new areas or new users. When this policy is turned on it allows a [captive portal](/windows-hardware/drivers/mobilebroadband/captive-portals) on the sign-in screen, which allows a user to enter credentials to connect to the Wi-Fi access point. If enabled, sign in will implement similar logic as OOBE to display captive portal if necessary.

MixedReality/AllowCaptivePortalBeforeSignIn

The OMA-URI of new policy:
`./Device/Vendor/MSFT/Policy/Config/MixedReality/AllowCaptivePortalBeforeSignIn`

- Bool value

### Clean up storage via MDM

[Storage Sense](/windows/manage-drive-space-with-storage-sense-654f6ada-7bfc-45e5-966b-e24aded96ad5) is available on HoloLens 2 today to manage cleanup of old files. IT admins can now also configure behavior of Storage Sense on HoloLens 2 with following MDM policies:

- [Storage/AllowStorageSenseGlobal](/windows/client-management/mdm/policy-csp-storage#storage-allowstoragesenseglobal)
  - Sets Storage sense to be enabled on the device and will run whenever reaching low storage.
- [Storage/AllowStorageSenseTemporaryFilesCleanup](/windows/client-management/mdm/policy-csp-storage#storage-allowstoragesensetemporaryfilescleanup)
  - When Storage Sense runs, it can delete the user’s temporary files that aren't in use.
- [Storage/ConfigStorageSenseCloudContentDehydrationThreshold](/windows/client-management/mdm/policy-csp-storage#storage-configstoragesensecloudcontentdehydrationthreshold)
  - When Storage Sense runs, it can dehydrate cloud-backed content that hasn’t been opened in a certain number of days. If you enable this policy setting, you must provide the minimum number of days a cloud-backed file can remain unopened before Storage Sense dehydrates it. Supported values are: 0–365.
- [Storage/ConfigStorageSenseDownloadsCleanupThreshold](/windows/client-management/mdm/policy-csp-storage#storage-configstoragesensedownloadscleanupthreshold)
  - When Storage Sense runs, it can delete files in the user’s Downloads folder if they haven’t been opened for more than a certain number of days. If you enable this policy setting, you must provide the minimum number of days a file can remain unopened before Storage Sense deletes it from the Downloads folder. Supported values are: 0-365.
- [Storage/ConfigStorageSenseGlobalCadence](/windows/client-management/mdm/policy-csp-storage#storage-configstoragesenseglobalcadence)
  - Storage Sense can automatically clean some of the user’s files to free up disk space. The following are supported options:
    - 1 – Daily
    - 7 – Weekly
    - 30 – Monthly
    - 0 – During low free disk space (Default)

### Security baseline

In some cases you may want to place some stronger restrictions on your devices. Whatever your need for security, we've written out two security baselines that you can use to add an extra layer of security to your device fleet.

Select this link to read the [security baselines](security-baseline.md).

### Fixes improvements

- It will be possible to issue an app uninstall command in the device context using EnterpriseModernAppManagement CSP.

### Upcoming Fixes and Improvements

- In-box OpenXR code updated. This is to provide best out-of-box experience for customers without Microsoft store access.
- Medical partners can access 90fps eye tracking via Extended ET API.

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
