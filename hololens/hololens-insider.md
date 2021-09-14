---
title: Insider preview for Microsoft HoloLens
description: Learn how to get started with Insider builds and provide valuable feedback for our next major operating system update for HoloLens.
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: v-evmill
ms.topic: article
ms.custom:
- CI 111456
- CSSTroubleshooting
ms.localizationpriority: medium
audience: ITPro
ms.date: 09/10/2021
ms.reviewer: 
manager: ranjibb
appliesto:
- HoloLens 2
---

# Insider preview for Microsoft HoloLens

Welcome to the latest Insider Preview builds for HoloLens! It's simple to [get started](hololens-insider.md#start-receiving-insider-builds) and provide valuable feedback for our next major operating system update for HoloLens.

## Windows Insider Release Notes

We're excited to start flighting new features to Windows Insiders again. New builds will be flighting to the Dev and Beta Channels for the latest updates. We will continue to update this page as we add more features and updates to our Windows Insider builds. Get excited and ready to mix these updates into your reality.

This one’s about the improved troubleshooting and device reports, some fixed bugs in kiosk mode and the certificate viewer, the expanded manageability surface and the increased update reliability. A new flagship feature of this feature update coming to HoloLens is our Moving Platform Mode. Check out all the new great features for HoloLens 2!

| Feature                 | Description                | User or Scenario | Build introduced |
|-------------------------|----------------------------|--------------|------------------|
| [Moving Platform Mode](#moving-platform-mode) | Introduces Moving Platform Mode beta, which when configured, enables the use of HoloLens 2 on large marine vessels experiencing low-dynamic motion. | All | 20348.1411 |
| [PFX file support for Certificate Manager](#pfx-file-support-for-certificate-manager) | Add PFX certs via Settings UI | End User | 20348.1405 |
| [View advanced diagnostic report in Settings on HoloLens](#view-advanced-diagnostic-report-in-settings-on-hololens) | View MDM diagnostic logs on device | Troubleshooting | 20348.1405 |
| [Offline Diagnostics notifications](#offline-diagnostics-notifications) | Audiovisual feedback for log collection | Troubleshooting | 20348.1405 |
| [Low storage log collection improvements](#low-storage-log-collection-improvements) | Improvements to log collection scenarios during low storage situations. | Troubleshooting | 20348.1412 |
| [CSP changes for reporting HoloLens details](#csp-changes-for-reporting-hololens-details) | New CSPs for to query data | IT Admins    | 20348.1403                 |
| [Auto login policy controlled by CSP](#auto-login-policy-controlled-by-csp) | Used to log in an account automatically | IT Admins | 20348.1405 |
| [Improved update restart detection and notifications](#improved-update-restart-detection-and-notifications) | New enabled policies and UX for updates. | IT Admins | 20348.1405 |
| [Smart Retry for app updates](#smart-retry-for-app-updates) | Allows IT Admins to scheduled retries to update apps. | IT Admins | 20348.1405 |
| [Use only private store apps only for Microsoft Store](#use-only-private-store-apps-for-microsoft-store) | Configure the store app to show only apps from organization | IT Admin | 20348.1408 |
| [Use WDAC and LOB apps](#use-wdac-and-lob-apps) | Allows IT Admins to use their own apps and still use WDAC to block other apps. | IT Admins | 20348.1405 |
| [Fixes and improvements](#fixes-and-improvements) | Fixes and improvements for HoloLens. | All | 20348.1411 |

### IT Admin Insider Feature Checklist

✔️ If you'd like to set a single Azure AD account to automatically log in, [configure this new CSP.](#auto-login-policy-controlled-by-csp) <br>
✔️ If you'd like configure your apps to automatically attempt to update after failing to update, [set this new CSP for smart retry.](#smart-retry-for-app-updates) <br>
✔️ If you'd like to have more control over OS updates, check out these [newly enabled Update policies.](#improved-update-restart-detection-and-notifications) <br>
✔️ If you need to get make your organization's apps available on the company store via the Microsoft Store, but want to only allow access to your organization's apps and not the full store, [set this policy.](#use-only-private-store-apps-for-microsoft-store) <br>
✔️ If you'd like to know the free storage space, SSID or BSSID of your HoloLens devices check out these [reporting CSPs.](#csp-changes-for-reporting-hololens-details) <br>
✔️ If you'd like to use WDAC to block apps or processes from launching, but also need to use your own line of bushiness apps, you can now [allow LOB in your WDAC policy](#use-wdac-and-lob-apps).

### Moving Platform Mode

As of **Insider build 20348.1411** we have added beta support for tracking on low-dynamic motion moving platforms on HoloLens 2. After installing the build and enabling Moving Platform Mode, you will be able to use your HoloLens 2 in previously inaccessible environments, like large ships and large marine vessels. Currently, the feature is targeted at enabling these specific moving platforms only. While nothing prevents you from attempting to use the feature in other environments, the feature is focused on adding support for these environments first.

To learn more about what is supported and how to enable this new feature, [visit the moving platform page.](hololens2-moving-platform.md)

### PFX file support for Certificate Manager

Introduced in Windows Insider build 20348.1405. We’ve added support to the [Certificate Manager](certificate-manager.md) to now use .pfx certificates. When users navigate to **Settings** > **Update & Security** > **Certificates**, and select **Install a certificate** the UI now supports .pfx certificate file.
Users can import .pfx certificate, with private key, to user store or machine store.

### View advanced diagnostic report in Settings on HoloLens

For managed devices when troubleshooting behavior, confirming that an expected policy configuration is applied is an important step. Previously to this new feature, viewing this information had to be done off device via MDM or near the device after exporting MDM diagnostic logs gathered via **Settings** -> **Accounts** > **Access work or school**, and select **Export your management logs** and viewed on a nearby PC.

Now the MDM Diagnostics can be viewed on device using the Edge browser. To more easily view the MDM Diagnostic report navigate to the Access work or school page, and select **View advanced diagnostic report**. This will generate and open the report in a new Edge window.

![View advanced diagnostic report in Settings app.](./images/view-advanced-diagnostic-report.jpg)

### Offline Diagnostics notifications

This an update for an existing feature called [Offline Diagnostics](hololens-diagnostic-logs.md#offline-diagnostics). Previously, there was no clear indicator to users that they had triggered diagnostic collection or it had completed.
Now added in Windows Insider builds, there are two forms of audiovisual feedback for Offline Diagnostics. The first being toasts notifications displayed for both when collection starts and completes. These will be displayed when the user is logged in and has visuals.

![Toast for collecting logs.](./images/logcollection1.jpg)

![Toast when log collection is complete.](./images/logcollection2.jpg)

Because users often use Offline Diagnostics as a fallback log gathering mechanism for when they don’t have access to a display, can’t log-in or are still in OOBE there will also be an audio cue played when logs are gathered. This sound will be played in addition to the toast notification.

This new feature will be enabled when your device updates, and doesn’t need to be enabled or managed. In any event that this new feedback cannot be displayed or heard, Offline Diagnostics will still be generated.

We hope with this newer addition of audiovisual feedback it is easier to gather diagnostic data, and more quickly be able to troubleshoot your problems.

### Low storage log collection improvements

In scenarios where a device seems to be low on disk space when diagnostic logs are collected, an additional report named **StorageDiagnostics.zip** will be created. The threshold of low storage is determined automatically by Windows [storage sense](https://support.microsoft.com/office/use-onedrive-and-storage-sense-in-windows-10-to-manage-disk-space-de5faa9a-6108-4be1-87a6-d90688d08a48).

### CSP changes for reporting HoloLens details

- Introduced in Windows Insider build, 20348.1403

The following CSPs have been updated with new ways to report information from your HoloLens devices.

#### DevDetail CSP - Free Storage

DevDetail CSP now also reports free storage space on HoloLens device. This should approximately match with the value shown in Settings App's Storage page. Following is the specific node containing this information.

- ./DevDetail/Ext/Microsoft/FreeStorage (GET operation only)

#### DeviceStatus CSP - SSID and BSSID

DeviceStatus CSP now also reports SSID and BSSID of Wi-Fi network with which HoloLens is actively connected. Following are the specific nodes containing this information.

- ./Vendor/MSFT/DeviceStatus/NetworkIdentifiers/*mac address of Wi-Fi adapter*/SSID
- ./Vendor/MSFT/DeviceStatus/NetworkIdentifiers/*mac address of Wi-Fi adapter*/BSSID

Example syncml blob (for MDM vendors) to query for NetworkIdentifiers

```xml
<SyncML>
<SyncBody>
	<Get>
        <CmdID>$CmdID$</CmdID>
        <Item>
            <Target>
            <LocURI>
                ./Vendor/MSFT/DeviceStatus/NetworkIdentifiers?list=StructData
			</LocURI>
            </Target>
        </Item>
    </Get>
    <Final/>
</SyncBody>
</SyncML>
```

### Auto login policy controlled by CSP

This new AutoLogonUser policy controls whether a user will be automatically logged on. Some customers want to set up devices that are tied to an identity but don't want any sign-in experience. Imagine picking up a device and using remote assist immediately. Or have a benefit of being able to rapidly  distribute HoloLens devices and enable their end users to expedite login.

When the policy is set to a non-empty value, it specifies the email address of the auto-logon user. The specified user must logon to the device at least once to enable auto-logon.

The OMA-URI of new policy `./Device/Vendor/MSFT/Policy/Config/MixedReality/AutoLogonUser`
String value

- User with the same email address will have auto logon enabled.

On a device where this policy is configured, the user specified in the policy will need to logon at least once. Subsequent reboots of the device after the first logon will have the specified user automatically logged on. Only a single auto-logon user is supported. Once enabled, the automatically logged on user will not be able to log out manually. To logon as a different user, the policy must first be disabled.

> [!NOTE]
>
> - Some events such as major OS updates may require the specified user to logon to the device again to resume auto-logon behavior.
> - Auto-logon is only supported for MSA and AAD users.

### Improved update restart detection and notifications

Between active hours and install time policies, it is possible to avoid rebooting HoloLens devices when they are in use. However, it would also delay the adoption of updates if reboots don’t occur to complete the installation of a required update. We’ve now added policies to allow IT to enforce deadlines and required reboots and ensure that the installation of an update is completed in a timely manner. Users can be notified prior to the reboot being initiated and they can delay the reboot in accordance with IT policy.

The following update policies were added:

- [Update/AutoRestartNotificationSchedule](/windows/client-management/mdm/policy-csp-update#update-autorestartnotificationschedule)
- [Update/AutoRestartRequiredNotificationDismissal](/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
- [Update/ConfigureDeadlineForFeatureUpdates](/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforfeatureupdates)
- [Update/ConfigureDeadlineForQualityUpdates](/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforqualityupdates)
- [Update/ConfigureDeadlineGracePeriod](/windows/client-management/mdm/policy-csp-update#update-configuredeadlinegraceperiod)
- [Update/ConfigureDeadlineNoAutoReboot](/windows/client-management/mdm/policy-csp-update#update-configuredeadlinenoautoreboot)
- [Update/ScheduleImminentRestartWarning](/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning)
- [Update/ScheduleRestartWarning](/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)
- [Update/UpdateNotificationLevel](/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)

### Smart Retry for app updates

Now enabled for HoloLens is a new policy that allows IT Admins to set a recurring or one time date to restart apps whose update failed due to the app being in use allowing the update to be applied. These can be set based on a few different triggers such as a scheduled time or sign-in. To learn more about how to use this policy view [ApplicationManagement/ScheduleForceRestartForUpdateFailures](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-scheduleforcerestartforupdatefailures).

### Use only private store apps for Microsoft Store

The RequirePrivateStoreOnly  policy has been enabled for HoloLens. This policy enables the Microsoft Store app to be configured to only show the private store configured for your organization. Limiting access to only the apps you’ve made available.

Learn more about [ApplicationManagement/RequirePrivateStoreOnly](http://windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-requireprivatestoreonly)

### Use WDAC and LOB apps

You can now use WDAC to block apps or processes from launching and continue to use your own line of bushiness apps. you can now allow them in your WDAC policy. Using this policy involves running an extra line of code in PowerShell when creating your WDAC policy. [Review the steps here.](/mem/intune/configuration/custom-profile-hololens)

### Fixes and improvements

- Fixed a [known issue for Device Portal where there was no prompt downloading locked files.](hololens-troubleshooting.md#downloading-locked-files-doesnt-error)
- Fixed a [known issue for Device Portal with file upload and download time outs.](hololens-troubleshooting.md#device-portal-file-uploaddownload-times-out)
- Addresses issues around reporting compliance properties from HoloLens devices; a reboot may be required for the correct reporting to be triggered on Insider builds.  
- Enabled an [Assigned Access API](/uwp/api/windows.system.userprofile.assignedaccesssettings?view=winrt-20348&preserve-view=true) so that apps can now determine if a HoloLens is running in a Kiosk mode for the user logged into the HoloLens.
- Updated the in-box version of Remote Assist that's installed on fresh flashes.
- Gamepad processing for 2D apps was disabled in Insider builds. By removing it, apps are now free to use the Gamepad APIs directly and have access to the whole set of controls and do whatever they want. Developers should use the Gamepad APIs to consume Gamepad input. Here is a sample for [Gamepad Class (Windows.Gaming.Input) - Windows UWP applications](/uwp/api/windows.gaming.input.gamepad?view=winrt-20348&preserve-view=true)
- Fixed an issue where after first user sign-in, OOBE was being terminated in scenarios where AAD group based kiosk configurations were being used.
- Corrected an issue around displaying update notifications and dialog prompts for device restart.

## Start receiving Insider builds

> [!NOTE]
> If you haven’t updated recently, please reboot your device to update state and get the latest build.
>
> - The “Reboot device” voice command works well.
> - You can also choose the restart button in Settings/Windows Insider Program.
>
> We had a bug on the back-end that you may have encountered and this will get you back on track.

On a HoloLens 2 device go to **Settings** > **Update & Security** > **Windows Insider Program** and select **Get started**. Link the account you used to register as a Windows Insider.

Windows insider is now moving to Channels. The **Fast** ring will become the **Dev Channel**, the **Slow** ring will become the **Beta Channel**, and the **Release Preview** ring will become the **Release Preview Channel**. Here is what that mapping looks like:

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
