---
title: HoloLens 2 release notes
description: Learn about updates in each new HoloLens 2 release.
author: scooley
ms.author: scooley
manager: laurawi
ms.prod: hololens
ms.sitesec: library
ms.topic: article
ms.localizationpriority: medium
ms.date: 1/12/2021
ms.custom: 
- CI 111456
- CSSTroubleshooting
audience: ITPro
appliesto:
- HoloLens 2

---

# HoloLens 2 release notes

To ensure you have a productive experience with your HoloLens devices, we continue to release feature, bug, and security updates. On this page, you can see what’s new for HoloLens each month. To get the latest HoloLens 2 update, you can either [check for updates and manually update](hololens-update-hololens.md#check-for-updates-and-manually-update) or get the Full Flash Update (FFU) to [flash your device via Advanced Recovery Companion](hololens-recovery.md#clean-reflash-the-device), [download it here](https://aka.ms/hololens2download). The download is kept up to date and provides the latest generally available build.

We are excited to start flighting new features to Windows Insiders again. We will be flighting to the Dev Channel for the latest updates. We will continue to our [HoloLens Insider notes](hololens-insider.md) as we add more features and updates to our Windows Insider builds. Get excited and ready to mix these updates into your reality. 

>[!NOTE]
> To read HoloLens Emulator release notes, [visit the archive](https://docs.microsoft.com/windows/mixed-reality/hololens-emulator-archive).

## Windows Holographic, version 20H2 - January 2021 Update
- Build 19041.1134

Improvements and fixes in the update:

- Improved performance during startup, resume, and user switching when there are many users on the device.
- Added arm32 support for [Research Mode](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/research-mode).

## Windows Holographic, version 1903 - January 2021 Update
- Build 18362.1091

This monthly quality update doesn't contain any notable changes, we encourage you to try out our latest builds for Windows Holographic, version 2004.

## Windows Holographic, version 20H2 – December 2020 Update
- Build 19041.1131

### Install Apps on HoloLens 2 via App Installer

We are **adding a new capability (App Installer) to allow you to install applications more seamlessly** on your HoloLens 2 devices. The feature will be **on by default for unmanaged devices**. To prevent disruption to enterprises, app installer will be **not be available for managed devices** at this time.  

A device is considered “managed” if **any** of the following are true:
- MDM [Enrolled](hololens-enroll-mdm.md)
- Configured with [provisioning package](hololens-provisioning.md)
- User [Identity](hololens-identity.md) is Azure AD

You are now able to install Apps without needing to enable Developer Mode or using Device Portal.  Simply download (over USB or through Edge) the Appx Bundle to your device and navigate to the Appx Bundle in the File Explorer to be prompted to kick off the installation.  Alternatively, [initiate an install from a web page](https://docs.microsoft.com/windows/msix/app-installer/installing-windows10-apps-web).  Just like apps you install from the Microsoft Store or sideload using MDM’s LOB App deployment capability, apps need to be digitally signed with the [Sign Tool](https://docs.microsoft.com/windows/win32/appxpkg/how-to-sign-a-package-using-signtool) and the [certificate used to sign must be trusted](https://docs.microsoft.com/windows/win32/appxpkg/how-to-sign-a-package-using-signtool#security-considerations) by the HoloLens device before the app can be deployed.

**Application install instructions.**

1.  Ensure that your device is not considered managed
1.  Ensure that your HoloLens 2 device is powered on and connected to your PC
1.  Ensure that you are signed into the HoloLens 2 device
1.  On your PC navigate to your custom app, and copy yourapp.appxbundle to yourdevicename\Internal Storage\Downloads.   After you’ve finished copying your file you can disconnect your device
1.  From your HoloLens 2 device Open the Start Menu, select All apps and launch the File Explorer app.
1.  Navigate to the Downloads folder. You may need to on the left panel of the app select This device first, then navigate to Downloads.
1.  Select the yourapp.appxbundle file.
1.  The App Installer will launch. Select the Install button to install your app.
The installed app will automatically launch upon completion of installation.

You can find sample apps on [Windows Universal Samples GitHub](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples) to test this flow.

Read about the full process of [installing apps on HoloLens 2 with the App Installer](app-deploy-app-installer.md).  

![Installing MRTK Examples via App Installer](images/hololens-app-installer-picture.jpg)

### Improvements and fixes in the update:

- Hand tracking now maintains tracking in many new cases where the hand previously would have been lost.  In some of these new cases, only the palm position continues to update based on the user’s real hand, while the other joints are inferred based on a previous pose.  This change helps improve tracking consistency in movements such as slapping, throwing, scooping, and clapping.  It also helps in cases where the hand is close to a surface or holding an object.  When hand joints are being inferred, the [per joint accuracy](https://docs.microsoft.com/uwp/api/windows.perception.people.jointposeaccuracy?view=winrt-19041&preserve-view=true) value will be set to “Approximate” instead of “High.”
- Fixed an issue where PIN reset for Azure AD accounts would show an error "Something went wrong.
- Users should see much less post-boot OOBE crashes when launching ET, Iris from settings app, new user, or notification toast.
- Users should have correct time zone coming out of OOBE.

## Windows Holographic, version 1903 – December 2020 Update
- Build 18362.1088

This monthly quality update doesn't contain any notable changes, we encourage you to try out our latest Windows Holographic, version 20H2 – December 2020 Update and the new App Installer feature added in the build.


## Windows Holographic, version 20H2
- Build 19041.1128

Windows Holographic, version 20H2 is now available and brings a great set of new features to HoloLens 2 users and IT professionals. From Auto Eye Positioning, to Certificate Manager in Settings, to improved Kiosk Mode functionality, and new Autopilot setup capabilities. This new update enables IT teams to take more granular control to configuring and managing HoloLens devices, and offers users even more seamless holographic experiences. 

This latest release is a monthly update to version 2004, but this time we are including new features. The major build number will remain the same and Windows Update will indicate a monthly release to version 2004 (build 19041). You can look at your Build Number in your Settings > About screen to confirm you are on the latest available build 19041.1128+. To update to the latest release, open the Settings app, go to Update & Security, and tap Check for Updates. For more information on how to manage HoloLens updates, visit [this page](https://docs.microsoft.com/hololens/hololens-updates).

### What’s new in Windows Holographic, version 20H2  

| Feature                                              | Description                                                                                                                                     |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| [Auto Eye Position Support](hololens-release-notes.md#auto-eye-position-support) | Actively computes eye positions without users going through Eye Tracking calibration.   |
| [Certificate Manager](hololens-release-notes.md#certificate-manager)   | Allows new simpler methods to install and remove certificates from the Settings app.     |
| [Auto-launch provisioning from USB](hololens-release-notes.md#auto-launch-provisioning-from-usb)                    | Provisioning packages on USB drives automatically prompt the provisioning page in OOBE.                                                         |
| [Auto-confirm provisioning packages in OOBE](hololens-release-notes.md#auto-confirm-provisioning-packages-in-oobe)           | Provisioning packages are automatically applied during OOBE from the provisioning page.                                                         |
| [Automatic provisioning without using UI](hololens-release-notes.md#automatic-provisioning-without-using-ui) | How to combine the provisioning auto-launch and auto-confirm together. |
| [Using Autopilot with Wi-Fi connection](hololens-release-notes.md#using-autopilot-with-wi-fi-connection) | Use autopilot from device Wi-Fi without need for ethernet adapter. |
| [Tenantlockdown CSP and Autopilot](hololens-release-notes.md#tenantlockdown-csp-and-autopilot)                     | After tenant enrollment and the policy is applied, the device can only be enrolled in that tenant any time the device is reset or   re-flashed. |
| [Global Assigned Access](hololens-release-notes.md#global-assigned-access--kiosk-mode)                               | New configuration method for multiple app kiosk mode which applies the kiosk at the system level, making it applicable to all.                  |
| [Auto-launch an app in multi-app kiosk](hololens-release-notes.md#automatic-launch-of-an-application-in-multiple-app-kiosk-mode)                | Sets an application to launch automatically when signing into a multiple-app kiosk mode.                                                        |
| [Kiosk mode behavior changes for handling of failures](hololens-release-notes.md#kiosk-mode-behavior-changes-for-handling-of-failures) | Kiosk mode failure now has restrictive fallback.                                                                                                |
| [HoloLens Policies](hololens-release-notes.md#hololens-policies)                                    | New policies for HoloLens.     |
| [Cache Azure AD Group membership for offline Kiosk](hololens-release-notes.md#cache-azure-ad-group-membership-for-offline-kiosk)         | New policy allows users to uses group membership cache to use Kiosk mode offline for set number of days.                                        |
| [New device restriction policies for HoloLens 2](hololens-release-notes.md#new-device-restriction-policies-for-hololens-2)       | Device management policies enabled newly enabled for HoloLens 2.                                                                                |
| [New power policies for HoloLens 2](hololens-release-notes.md#new-power-policies-for-hololens-2)       | Newly supported policies for power timeout settings.  |
| [Update Policies](hololens-release-notes.md#newly-enabled-update-policies-for-hololens)        | Newly enabled policies allowing control of updates.           |
| [Enabled Settings page visibility for HoloLens 2](hololens-release-notes.md#enabled-settings-page-visibility-for-hololens-2)      | Policy to pick which pages are seen in Settings app.             |
| [Research mode](hololens-release-notes.md#research-mode) | Using Research mode on HoloLens 2. |
| [Recording length increased](hololens-release-notes.md#recording-length-increased) | MRC recordings no longer capped to 5 minutes. |
| [Improvements and fixes in the update](hololens-release-notes.md#improvements-and-fixes-in-the-update)                 | Additional fixes in the update.   |

### Auto Eye Position Support

In HoloLens 2, eye positions enable accurate hologram positioning, comfortable viewing experience and improved display quality. Eye positions are computed internally as part of the eye tracking computation. However, this requires each user to go through eye tracking calibration, even when the experience might not require eye gaze input.

**Auto Eye Position (AEP)** enables these scenarios with an interaction-free way to compute eye positions for the user. Auto Eye Position starts working in the background automatically from the moment the user puts the device on. If the user does not have a prior eye tracking calibration, Auto Eye Position will start providing the user's eye positions to the display system after a processing time of 20 - 30 seconds. The user data is not persisted on the device and hence this process is repeated if the user takes off and puts the device back on or if the device reboots or wakes up from sleep.

There are a few system behavior changes with Auto Eye Position feature when an uncalibrated user puts on the device. In this context, an uncalibrated user refers to someone who has not gone through the eye tracking calibration process on the device previously.

| Active Application | Prior Behavior | Behavior from Windows Holographic, version 20H2 Update |
|:-------------------|:-----------------|:-----------------------------------|
| Non-gaze enabled app or Holographic Shell |Eye tracking calibration prompt dialog is displayed. | No prompt is displayed. |
| Gaze enabled app | Eye tracking calibration prompt dialog is displayed. | Eye tracking calibration prompt is displayed only when the application accesses eye gaze stream. |

If the user transitions from a non-gaze enabled application to one that accesses the gaze data, the calibration prompt will be displayed. 

All other system behavior will be similar to when the current user does not have an active eye tracking calibration. For example, the One-handed Start gesture will not be enabled. There will be no change to the Out-Of-Box-Experience for initial setup.

For experiences that require eye gaze data or very precise hologram positioning, we recommend uncalibrated users to run eye tracking calibration. It is accessible from the eye tracking calibration prompt or by launching the Settings app from the start menu, and then selecting **System > Calibration > Eye Calibration > Run eye calibration**.

This information can be found later with [other calibration information](hololens-calibration.md#auto-eye-position-support). 

### Certificate Manager

- Improved auditing, diagnosis, and validation tooling for device security and compliance through the new Certificate Manager. This capability will enable you to deploy, troubleshoot, and validate your certificates at scale in commercial environments.

In Windows Holographic version 20H2, we are adding a Certificate Manager in the HoloLens 2 Settings app. Go to **Settings > Update & Security > Certificates**. This feature provides a simple and user-friendly way to view, install and remove certificates on your device. With the new Certificate Manager, admins and users now have improved auditing, diagnosis and validation tooling to ensure that devices remain secure and compliant. 

-	**Auditing:** Ability to validate that a certificate is deployed correctly or to confirm that it was removed appropriately. 
-	**Diagnosis:** When issues arise, validating that the appropriate certificates exist on the device saves time and helps with troubleshooting. 
-	**Validation:** Verifying that a certificate serves the intended purpose and is functional, can save significant time, particularly in commercial environments before deploying certificates at larger scale.

To find a specific certificate in the list quickly, there are options to sort by name, store or expiration date. Users may also directly search for a certificate. To view individual certificate properties, select the certificate and click on **Info**. 

Certificate installation currently supports .cer and .crt files. Device Owners can install certificates in Local Machine and Current User;  all other users can only install into Current User. Users can only remove certificates installed directly from the Settings UI. If a certificate has been installed through other means, it must also be removed by the same mechanism.

#### To install a certificate: 

1.	Connect your HoloLens 2 to a PC.
1.	Place the certificate file you want to install in a location on your HoloLens 2.
1.	Navigate to **Settings App > Update & Security > Certificates**, and select Install a certificate.
1.	Click **Import File** and navigate to the location you saved the certificate.
1.	Select **Store Location**.
1.	Select **Certificate Store**.
1.	Click **Install**.

The certificate should now be installed on the device.

#### To remove a certificate: 
1. Navigate to **Settings App > Update and Security > Certificates**.
1. Search for the certificate by name in the search box.
1. Select the certificate.
1. Click **Remove**
1. Select **Yes** when prompted for confirmation.

![Certificate viewer in the Settings app](images/certificate-viewer-device.jpg)

![Picture showing how to use Certificate UI to install a certificate](images/certificate-device-install.jpg)

This information can be found later [on a new Certificate Manager page](certificate-manager.md).

### Auto-launch provisioning from USB

- Automated processes allowing for less user interaction, when USB Drives with Provisioning Packages are used during OOBE.

Before this release users had to launch the provisioning screen manually during OOBE to provision using a button combination. Now users can skip the button combination, by using a Provisioning Package on a USB storage drive. 

1. Plug in the USB drive with the provisioning package during OOBE’s first interactable moment
1. When the device is ready to be provisioned it will automatically open the prompt with the provisioning page. 

Note: If a USB drive is left plugged in while the device is booting then OOBE will enumerate existing USB storage device, as well as watch for additional ones being plugged in.

For more information about applying provisioning packages during OOBE please continue reading [here](hololens-provisioning.md#apply-a-provisioning-package-to-hololens-during-setup).

This information can be found later [here.](hololens-provisioning.md#auto-launch-provisioning-from-usb)

### Auto-confirm provisioning packages in OOBE
- Automated process allowing for less user interaction, when the Provisioning Package page is displayed it will automatically apply all packages listed.

When the provisioning main screen comes up, OOBE will count down 10 seconds before automatically starting applying all provisioning packages. Users can still confirm or cancel within this 10 seconds after verifying the packages they expected.

This information can be found later [here.](hololens-provisioning.md#auto-confirm-provisioning-packages-in-oobe)

### Automatic provisioning without using UI
- Combined automatic processes for reduced device interactions for provisioning. 

By combining the auto-launch of provisioning from USB devices and the auto-confirmation of provisioning packages, a user can provision HoloLens 2 devices automatically without using the device's UI or even wearing the device. You may continue to use the same USB drive and provisioning package for multiple devices. This is useful for deploying multiple devices at once in the same area. 

1. [Create a Provisioning Package](hololens-provisioning.md) using [Windows Configuration Designer](https://www.microsoft.com/store/productId/9NBLGGH4TX22). 
1. Copy the package to a USB storage drive.
1. [Flash your HoloLens 2](hololens-insider.md#ffu-download-and-flash-directions) to [19041.1361 or newer build](https://aka.ms/hololens2previewdownload). 
1. When [Advanced Recovery Companion](https://www.microsoft.com/store/productId/9P74Z35SFRS8) has completed flashing your device unplug your USB-C cable. 
1. Plug in your USB drive to the device.
1. When the HoloLens 2 device boots into OOBE it will automatically detect the provisioning package on the USB drive and launch the provisioning page.
1. After 10 seconds the device will automatically apply the provisioning package. 

Your device is now configured and will display the Provisioning Successful screen.

This information can be found later [here.](hololens-provisioning.md#automatic-provisioning-without-using-ui)

### Using Autopilot with Wi-Fi connection
- Removed need for USB-C adapters to ethernet reducing hardware needs, by enabling Autopilot to function on Wi-Fi connected devices.

Now during OOBE, once you connect HoloLens 2 with Wifi, OOBE will check for an Autopilot profile for the device. If one is found it will be used to complete rest of the AAD join and enrollment flow. In other words, using ethernet to USB-C or Wi-Fi to USB-C adapter is not a requirement anymore, however they continue to work if provided at beginning of OOBE. Learn more about [Autopilot for HoloLens 2 devices](hololens2-autopilot.md).

### Tenantlockdown CSP and Autopilot
- Keeps devices on the organization's tenant by locking them to the tenant even through device reset or reflash. With further security by disallowing account creation in via provisioning. 

HoloLens 2 devices now support TenantLockdown CSP as of [Windows Holographic version 20H2](hololens-release-notes.md#windows-holographic-version-20h2). 

[TenantLockdown](https://docs.microsoft.com/windows/client-management/mdm/tenantlockdown-csp) CSP enables HoloLens 2 to be tied to MDM enrollment using Autopilot only. Once TenantLockdown CSP’s RequireNetworkInOOBE node is set to either true or false (initially set) value on HoloLens 2, that value remains on the device despite re-flashing, OS updates, etc. 

Once TenantLockdown CSPs’ RequireNetworkInOOBE node is set to true on HoloLens 2, OOBE waits indefinitely for Autopilot profile to be successfully downloaded and applied, after network connectivity. 

Once TenantLockdown CSPs’ RequireNetworkInOOBE node is set to true on HoloLens 2, following operations are disallowed in OOBE: 
- Creating local user using runtime provisioning 
- Performing Azure AD join operation via runtime provisioning 
- Selecting who owns the device in OOBE experience 

#### How to set this using Intune? 
1. Create a custom OMA URI device configuration profile and specify true for RequireNetworkInOOBE node as shown below.
OMA-URI value should be ./Vendor/MSFT/TenantLockdown/RequireNetworkInOOBE

   > [!div class="mx-imgBorder"]
   > ![Setting tennant lockdown via OMA-URI](images/hololens-tenant-lockdown.png)

1. Create a group and assign the device configuration profile to that device group. 

1. Make the HoloLens 2 device member of the group created in previous step and trigger sync.  

Verify in the Intune portal that device configuration has been successfully applied. Once this device configuration successfully applies on the HoloLens 2 device, effects of TenantLockdown will be active.

#### How to unset TenantLockdown’s RequireNetworkInOOBE on HoloLens 2 using Intune? 
1. Remove the HoloLens 2 from the device group to which the device configuration created above was previously assigned. 

1. Create a custom OMA URI based device configuration profile and specify false for RequireNetworkInOOBE as shown below. 
OMA-URI value should be ./Vendor/MSFT/TenantLockdown/RequireNetworkInOOBE

   > [!div class="mx-imgBorder"]
   > ![Screenshot of setting RequireNetworkInOOBE to false via OMA URI in Intune](images/hololens-tenant-lockdown-false.png)

1. Create a group and assign the device configuration profile to that device group. 

1. Make the HoloLens 2 device member of the group created in previous step and trigger sync.

Verify in the Intune portal that device configuration has been successfully applied. Once this device configuration successfully applies on the HoloLens 2 device, effects of TenantLockdown will be inactive. 

#### What would happen during OOBE, if Autopilot profile is unassigned on a HoloLens after TenantLockdown was set to true? 
OOBE will wait indefinitely for Autopilot profile to download and following dialog will be presented. In order to remove effects of TenantLockdown, device must be enrolled with its original tenant first using Autopilot only and RequireNetworkInOOBE must be unset as described in previous step before restrictions introduced by TenantLockdown CSP are removed. 

![In-device view for when policy is enforced on device.](images/hololens-autopilot-lockdown.png)

This information can now be found alongside the rest of Autopilot under [Tenantlockdown CSP and Autopilot](hololens2-autopilot.md#tenantlockdown-csp-and-autopilot).

### Global Assigned Access – Kiosk Mode
- Reduced Identity management for Kiosk, by enabling new Kiosk method that applies Kiosk mode at the system level.

This new feature allows an IT Admin to configure a HoloLens 2 device for multiple app kiosk mode which is applicable at system level, has no affinity with any identity on the system and applies to everyone who signs into the device. Read about this new feature in detail [here](hololens-global-assigned-access-kiosk.md).

### Automatic launch of an application in multiple-app kiosk mode 
- Focused experience with automatic app launch, further increasing the UI and app selections chosen for Kiosk mode experiences.

Applies only to multiple-app kiosk mode and only 1 app can be designated to auto-launch using highlighted attribute below in Assigned Access configuration. 

Application is automatically launched when user signs-in. 

```xml
<AllowedApps>                     
    <!--TODO: Add AUMIDs of apps you want to be shown here, e.g. <App AppUserModelId="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge" rs5:AutoLaunch="true"/> --> 
```

### Kiosk mode behavior changes for handling of failures
- More secure Kiosk mode by eliminating available apps on Kiosk mode failures. 

Earlier on encountering failures in applying kiosk mode, HoloLens used to show up all applications in start menu. Now in Windows Holographic version 20H2 in the case of failures no apps will be shown in the start menu as below: 

![Image of what Kiosk mode now looks when it fails.](images/hololens-kiosk-failure-behavior.png )

### HoloLens Policies
- Device management options specifically for HoloLens created for managing the device. 

New mixed reality policies have been created for HoloLens 2 devices on Windows Holographic version 20H2. New controllable settings include: setting brightness, setting volume, disabling audio recording in mixed reality captures, setting when diagnostics can be collected, and AAD group membership cache.  

| New HoloLens policy                                | Description                                                                               | Notes                                                                |
|----------------------------------------------------|-------------------------------------------------------------------------------------------|----------------------------------------------------------------------|
| MixedReality\BrightnessButtonDisabled              | Allows brightness buttons to be disabled so pressing it does not change brightness.       | 1 Yes, 0 No (default)                                                |
| MixedReality\VolumeButtonDisabled                  | Allows volume buttons to be disabled so pressing it does not change volume.               | 1 Yes, 0 No (default)                                                |
| MixedReality\MicrophoneDisabled                    | Disables microphone so no audio recording is possible on HoloLens 2.                      | 1 Yes, 0 No (default)                                                |
| MixedReality\FallbackDiagnostics                   | Controls behavior of when diagnostic logs can be collected.                               | 0 Disabled, 1 Enabled for Device Owners, 2 Enabled for all (Default) |
| MixedReality\HeadTrackingMode                      | Reserved for future use.                                                                  |                                                                      |
| MixedReality\AADGroupMembershipCacheValidityInDays | Controls how many days Azure AD group membership cache is used for Kiosk targeting Azure AD groups. | See below.                                                           |

### Cache Azure AD Group membership for offline Kiosk
- Enabled Offline Kiosks to be used with AAD groups for up to 60 days.

This policy controls for how many days, Azure AD group membership cache is allowed to be used for Assigned Access configurations targeting Azure AD groups for signed in user. Once this policy value is set to value greater than 0 only then cache is used otherwise not.  

Name: AADGroupMembershipCacheValidityInDays 
URI value: ./Vendor/MSFT/Policy/Config/MixedReality/AADGroupMembershipCacheValidityInDays

Min - 0 days  
Max - 60 days 

Steps to use this policy correctly: 
1. Create a device configuration profile for kiosk targeting Azure AD groups and assign it to HoloLens device(s). 
1. Create a custom OMA URI based device configuration which sets this policy value to desired number of days (> 0) and assign it to HoloLens device(s). 
    1. The URI value should be entered in OMA-URI text box as ./Vendor/MSFT/Policy/Config/MixedReality/AADGroupMembershipCacheValidityInDays
    1. The value can be between min / max allowed.
1. Enroll HoloLens devices and verify both configurations get applied to the device. 
1. Let Azure AD user 1 sign-in when internet is available, once user signs-in and Azure AD group membership is confirmed successfully, cache will be created. 
1. Now Azure AD user 1 can take HoloLens offline and use it for kiosk mode as long as policy value allows for X number of days. 
1. Steps 4 and 5 can be repeated for any other Azure AD user N. Key point here is that any Azure AD user must sign-in to device using Internet so at least once we can determine that they are member of Azure AD group to which Kiosk configuration is targeted. 
 
> [!NOTE]
> Until step 4 is performed for a Azure AD user will experience failure behavior mentioned in “disconnected” environments. 

### New device restriction policies for HoloLens 2
- Allows users to manage specific device management policies such as blocking adding or removing provisioning packages.

Newly enabled policies that allow for more management options of HoloLens 2 devices. 
- [AllowAddProvisioningPackage](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-allowaddprovisioningpackage)
- [AllowRemoveProvisioningPackage](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-allowremoveprovisioningpackage) 
- [ConfigureTimeZone](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-timelanguagesettings#timelanguagesettings-configuretimezone)
- [RemoteLock](https://docs.microsoft.com/windows/client-management/mdm/remotelock-csp)

These two new polices for AllowAddProvisioningPackage and AllowRemoveProvisioningPackage are being added to our [Common Device Restrictions](hololens-common-device-restrictions.md).

> [!NOTE]
> In regard to [RemoteLock](https://docs.microsoft.com/windows/client-management/mdm/remotelock-csp), HoloLens will only support the ./Vendor/MSFT/RemoteLock/Lock configuration. The configurations dealing with PIN such as reset and recover are not supported.

### New power policies for HoloLens 2
- More options for when HoloLens sleeps or locks via power policies. 

These newly added policies allow admins to control power states, such as idle timeout. To read more about each individual policy please click the link for that policy.

|     Policy documentation link                |     Notes                                                                                                                                       |
|----------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
|     [DisplayOffTimeoutOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-displayofftimeoutonbattery)               |     Example value to use in   Windows Configuration Designer, i.e.,  `<enabled/><data   id="EnterVideoDCPowerDownTimeOut" value="100"/>`     |
|     [DisplayOffTimeoutPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-displayofftimeoutpluggedin)               |     Example value to use in   Windows Configuration Designer, i.e.,  `<enabled/><data   id="EnterVideoACPowerDownTimeOut" value="100"/>`     |
|     [EnergySaverBatteryThresholdOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-energysaverbatterythresholdonbattery)     |  Example value to use in Windows Configuration Designer,   i.e., 100                                                                             |
|     [EnergySaverBatteryThresholdPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-energysaverbatterythresholdpluggedin)     |     Example value to use in Windows Configuration   Designer, i.e., 100                                                                          |
|     [StandbyTimeoutOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-standbytimeoutonbattery)                  |     Example value to use in   Windows Configuration Designer, i.e.,   `<enabled/><data   id="EnterDCStandbyTimeOut" value="100"/>`          |
|     [StandbyTimeoutPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-standbytimeoutpluggedin)                  |     Example value to use in   Windows Configuration Designer, i.e.,  `<enabled/><data   id="EnterACStandbyTimeOut" value="100"/>`           |

These two new polices for DisplayOffTimeoutOnBattery and DisplayOffTimeoutPluggedIn are being added to our [Common Device Restrictions](hololens-common-device-restrictions.md).

> [!NOTE]
> For consistent experience on HoloLens 2, please ensure that values for both DisplayOffTimeoutOnBattery and StandbyTimeoutOnBattery are set as same value. Same applies to DisplayOffTimeoutPluggedIn and StandbyTimeoutPluggedIn. Refer to [Display, sleep, and hibernate idle timers](https://docs.microsoft.com/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers) for more details about modern standby.

### Newly enabled Update policies for HoloLens
- More options for when Updates are installed or disabling the Pause Updates button to ensure updates.

These update policies are now enabled on HoloLens 2 devices:
-	[Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)
-	[Update/ActiveHoursMaxRange](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursmaxrange)
-	[Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)
-	[Update/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)

Full details on thise update policies and how to use them for HoloLens devices can be read here in [Manage HoloLens updates](hololens-updates.md).

### Enabled Settings page visibility for HoloLens 2
- Increased UI control in the Settings App, which may be confused to show a limited selection of pages.

We’ve now enabled a policy that allows IT Admins to either prevent specific pages in the System Settings app from being visible or accessible, or to do so for all pages except those specified. To learn how to fully customize this feature click the link below.

- [PageVisibilityList](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-pagevisibilitylist)

To learn which page settings you can customize on HoloLens 2, please visit our [Settings URIs page](settings-uri-list.md). 
 
![Screenshot of active hours being modified in the Settings app](images/hololens-page-visibility-list.jpg)

### Research mode
While in Research Mode, the HoloLens 2 becomes a potent tool for computer vision research. Compared to previous editions, Research Mode for HoloLens 2 has the following advantages:
-	In addition to sensors exposed in HoloLens (1st gen) Research Mode, we now provide IMU sensor access including an accelerometer, gyroscope, and magnetometer.
-	HoloLens 2 provides new capabilities that can be used together with Research Mode. Specifically, access to articulated hand-tracking and eye-tracking APIs that can deliver a richer set of experiments.

Researchers now have the option of enabling Research Mode on their HoloLens devices to access all of these external facing raw image sensors streams. Research Mode for HoloLens 2 also provides access to the accelerometer, gyroscope, and magnetometer readings. To protect users’ privacy, raw eye-tracking camera images are not available through Research Mode, but eye-gaze direction  is available through existing APIs.

Check out the [Research Mode documentation](https://docs.microsoft.com/windows/mixed-reality/research-mode) for further technical details.

### Recording length increased
Due to customer feedback we’ve increased the recording length of [mixed reality captures](holographic-photos-and-videos.md). Mixed reality captures will no longer be limited to 5 minutes by default but instead will calculate the maximum recording length based on available disk space. The device will estimate the max video recording duration based on available disk space up to 80% of the total disk space.

> [!NOTE]
> The HoloLens will use default video recording length (5 minutes) if one of the following occurs:
> -	The estimated max recording duration is smaller than the default 5 mins.
> -	The available disk space is less than 20% of the total disk space.

This information can be found again [here](holographic-photos-and-videos.md#maximum-recording-length). 

### Improvements and fixes in the update:
- More screens in OOBE  are now in dark mode.
- Learn more content should point to the latest Privacy Statement online.
- Addressed an issue where users could not provision VPN profiles through provisioning packages.
- Fixed proxy configuration issue for VPN connection.
- Updated policy to disable enumeration of USB functions through MDM for NCM for AllowUsbConnection.
- Addressed an issue that prevented a HoloLens device from showing up in File Explorer over Media Transfer Protocol (MTP) when the device is set up as a [single-app kiosk](hololens-kiosk.md). Note that MTP (and USB connection in general) can still be disabled using the [AllowUSBConnection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity#connectivity-allowusbconnection) policy.
- Fixed an issue where icons in the Start menu were scaled correctly in Kiosk mode.
- Fixed an issue due to HTTP caching interfering with kiosk mode targeted to Azure AD groups.
- Fixed an issue where users were unable to use the Pair button after enabling Developer mode with provisioning packages unless they disabled and re-enabled Developer mode.

## Windows Holographic, version 1903 - November 2020 Update
- Build 18362.1085

This monthly quality update doesn't contain any notable changes, we encourage you to try out our latest feature release build Windows Holographic, version 20H2.

## Windows Holographic, version 2004 - October 2020 Update
- Build 19041.1124
 
Improvements and fixes in the update:

- Removed an unnecessary check that caused runtime system fault.

## Windows Holographic, version 1903 - October 2020 Update
- Build 18362.1081

This monthly quality update doesn't contain any notable changes, we encourage you to try out our latest builds for Windows Holographic, version 2004.

## Windows Holographic, version 2004 - September 2020 Update
- Build 19041.1117

Improvements and fixes in the update:

- Addresses an issue that prevented Visual Studio from debugging an application when SupportsMultipleInstances=”true” is present in the appxmanifest.
- This release includes NCSI proxy detection fix to address failed Internet detection over network proxy. NCSI can use machine proxy and per-profile proxy for Internet connectivity detection. Per-user proxy will be supported by NCSI in future release.
- On most Windows Mixed Reality devices, the forward direction vector is parallel to the ground when the user's head is in a neutral position looking forward. However, earlier versions of HoloLens 2 aligned the vector to be perpendicular to the display panels instead, which is tilted downward a few degrees relative to the ideal orientation. Newer versions of HoloLens 2 have corrected this to ensure semantic consistency across form factors.
- Improved hand tracking robustness that will result in fewer tracking losses in specific scenarios.
- This release contains a fix to improve audio timestamp quality which may have contributed to video capture issues.

## Windows Holographic, version 1903 - September 2020 Update
- Build 18362.1079

Improvements and fixes in the update:

- On most Windows Mixed Reality devices, the forward direction vector is parallel to the ground when the user's head is in a neutral position looking forward. However, earlier versions of HoloLens 2 aligned the vector to be perpendicular to the display panels instead, which is tilted downward a few degrees relative to the ideal orientation. Newer versions of HoloLens 2 have corrected this to ensure semantic consistency across form factors.
- Improved hand tracking robustness that will result in fewer tracking losses in specific scenarios.

## Windows Holographic, version 2004 - August 2020 Update
- Build 19041.1113

Improvements and fixes in the update:

- Settings app will no longer follow the user into Iris Enrollment or Eye Tracking Calibration experiences.
- Fixed a bug where applying a provisioning package during OOBE that renames the device and performs other actions (such as connecting to a network) would fail to perform the other actions after the device reboot due to rename.
- Modified color scheme of initial device setup flows to improve visual quality.

## Windows Holographic, version 1903 - August 2020 Update
- Build 18362.1074

This monthly quality update doesn't contain any notable changes, we encourage you to try out our latest builds for Windows Holographic, version 2004.

## Windows Holographic, version 2004 - July 2020 Update
- Build 19041.1109

Improvements and fixes in the update:

- Developers can now choose between enabling or disabling having Device Portal require a secure connection.
- Reliability improved for application launches after OS updates.
- Changed default inbox brightness to 100 percent.
- Addressed an issue about HTTPS forwarding for the Windows Device Portal on HoloLens 2.

## Windows Holographic, version 1903 - July 2020 Update
- Build 18362.1071

Improvements and fixes in the update:

- Fixed an issue that could cause holograms to disappear in Unity applications when losing or regaining tracking.
- Fixed an issue that caused exclusive HoloLens apps to crash back to the shell while using the HoloLens Emulator with hardware acceleration on certain devices.
- Addressed an issue concerning HTTPS forwarding for the Windows Device Portal on HoloLens 2.

## Windows Holographic, version 2004 - June 2020 Update
- Build 19041.1106

Improvements and fixes in the update:

- Custom MRC recorders now have new default values for certain properties if they aren't specified.
  - On the *MRC Video Effect*:
    - PreferredHologramPerspective (1 PhotoVideoCamera)
    - GlobalOpacityCoefficient (0.9 (HoloLens) 1.0 (Immersive headset))
  - On the *MRC Audio Effect*:
    - LoopbackGain (the current "App Audio Gain" value on the Mixed Reality Capture page in Windows Device Portal)
    - MicrophoneGain (the current "Mic Audio Gain" value on the Mixed Reality Capture page in Windows Device Portal)
- Fixed a bug to improve audio quality in mixed reality capture scenarios. Specifically, this fix should eliminate audio glitching in the recording when the **Start** menu is displayed.
- Improved hologram stability in recorded videos.
- Resolved an issue where mixed reality capture couldn't record video after the device was left in standby state for multiple days.
- The HolographicSpace.UserPresence API is generally disabled for Unity applications. This behavior avoids an issue that caused some apps to pause when the visor was flipped up, even if the "run in the background" setting was enabled. The API is now enabled for Unity versions 2018.4.18 and later and 2019.3.4 and later.
- When you access Device Portal over a Wi-Fi connection, a web browser might prevent access to due to an invalid certificate. The browser might report an error such as "ERR_SSL_PROTOCOL_ERROR," even if the device certificate was previously trusted. In this case, you can't progress to Device Portal, as there's no option to ignore security warnings. This update resolved the issue. If the device certificate was previously downloaded and trusted on a PC to remove browser security warnings, and the SSL error occurs, the new certificate has to be downloaded and trusted to address browser security warnings.
- Enabled the ability to create a runtime provisioning package that can install an app by using MSIX packages.
- Added a setting in **Settings** > **System** > **Holograms** that allows users to automatically remove all holograms from Mixed Reality home when the device shuts down.
- Fixed an issue that caused HoloLens apps that change their pixel format to render black in the HoloLens emulator.
- Fixed a bug that caused a crash during Iris login.
- Fixed an issue about repeated store downloads for already-current apps.
- Fixed a bug to prevent immersive apps from opening Microsoft Edge repeatedly.
- Fixed an issue with launches of the Photos app in initial boots after updating from the 1903 release.
- Improved performance and reliability.

## Windows Holographic, version 1903 - June 2020 Update
- Build 18362.1064

Improvements and fixes in the update:

- Custom MRC recorders have new default values for certain properties if they aren't specified.
  - On the *MRC Video Effect*:
    - PreferredHologramPerspective (1 PhotoVideoCamera)
    - GlobalOpacityCoefficient (0.9 (HoloLens) 1.0 (Immersive headset))
  - On the *MRC Audio Effect*:
    - LoopbackGain (the current "App Audio Gain" value on the Mixed Reality Capture page in Windows Device Portal)
    - MicrophoneGain (the current "Mic Audio Gain" value on the Mixed Reality Capture page in Windows Device Portal)
- The HolographicSpace.UserPresence API is generally disabled for Unity applications. This behavior avoids an issue that causes some apps to pause when the visor is flipped up, even if the setting to run in the background is enabled. The API is now enabled for Unity versions 2018.4.18 and later, and 2019.3.4 and later.
- Fixed an issue that caused HoloLens apps that change their pixel format to render black in the HoloLens Emulator.
- Fixed an issue about launches of the Photos app in initial boots after updating from the 1903 release.

## Windows Holographic, version 2004  
- Build - 19041.1103

The May 2020 major software update for HoloLens 2, *Windows Holographic, version 2004* includes a host of exciting new capabilities, such as support for Windows Autopilot, app dark mode, USB Ethernet support for 5G/LTE hotspots, and much more. To update to the latest release, open the **Settings** app, go to **Update & Security**, and select the **Check for Updates** button. 

|             Feature                              |          Description                                                                                              |
|--------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
|       Windows Autopilot                          |          Pre-configure and seamlessly set up   new devices for production by using Windows AutoPilot                 |
|       FIDO 2 support                             |          Support for FIDO2 Security Keys to   enable fast and secure authentication for shared devices            |
|       Improved provisioning                      |          Seamlessly apply a provisioning   package from a USB drive to your HoloLens                              |
|       Application install status                 |          Check install status in the Settings app for apps have been pushed to HoloLens 2 via MDM               |
|       Configuration service providers   (CSPs)   |          Added new configuration service providers to enhance admin control capabilities                 |
|       USB 5G/LTE support                       |          Expanded USB Ethernet capability   enables support for 5G/LTE                                    |
|       Dark app mode                              |          Dark app mode available for apps that support both dark and light modes, improving the viewing experience        |
|       Voice commands                             |          Support for additional system voice   commands to control HoloLens hands-free                           |
|       Hand tracking improvements                 |          Hand tracking improvements make buttons and 2D slate interactions more accurate                        |
|       Quality improvements and fixes                 |          Various system performance and   reliability improvements across the platform                            |

### Support for Windows Autopilot

Windows Autopilot for HoloLens 2 lets the device sales channel pre-enroll HoloLens into your Intune tenant. When devices arrive, they’re ready to self-deploy as shared devices under your tenant. To take advantage of self-deployment, the device must connect to a network during the first screen in setup by using a USB-C-to-Ethernet.

After a user starts the Autopilot self-deploying process, the process completes the following steps:

1. Join the device to Azure Active Directory (Azure AD).
1. Use Azure AD to enroll the device in Microsoft Intune (or another MDM service).
1. Download the device-targeted policies, certificates, and networking profiles.
1. Provision the device.
1. Present the sign-in screen to the user.

Learn more from the [Windows Autopilot for HoloLens 2 evaluation guide](https://docs.microsoft.com/hololens/hololens2-autopilot).

*Contact your Account Manager to join the AutoPilot preview now. Autopilot-ready devices will begin shipping soon.*

### FIDO2 security key support

Some users share a HoloLens device with others in a work or school environment. So it's important that users can easily without typing long user names and passwords. Fast Identity Online (FIDO) lets anyone in your organization (Azure AD tenant) seamlessly sign-in to HoloLens without entering a user name or password.

FIDO2 security keys are an "unphishable" standards-based passwordless authentication method that can come in any form factor. FIDO is an open standard for passwordless authentication. It allows users and organizations to sign in to their resources without a user name or password. Instead they use an external security key or a platform key built into a device.

To get started, see [Enable passwordless security key sign-in](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-security-key).

### Improved MDM enrollment via provisioning package

Provisioning packages let you set HoloLens configuration through a config file rather than through the HoloLens out-of-box experience. Previously, provisioning packages had to be copied onto the HoloLens internal memory. Now they can be on a USB drive so they're easier to reuse on multiple HoloLens devices and you can provision devices in parallel. Provisioning packages now also support a field to enroll in device management so there's no manual setup after provisioning.

To try it out:

1. Download the latest version of the Windows Configuration Designer from the Windows store onto your PC.
1. Select **Provision HoloLens Devices** > **Provision HoloLens 2 devices**.
2. Build your configuration profile. Then copy all files that were created to a USB-C storage device.
3. Plug the USB-C device into any freshly flashed HoloLens. Then press the **volume down** + **power** buttons to apply your provisioning package.

### Line-of-business application install status

MDM app deployment and management for line of business apps is critical to HoloLens. Admins and users need to view app install status for auditing and diagnosis. In this release, we added more details in **Settings** > **Accounts** > **Access work or school** > **Click on your account** > **Info**.

### Additional CSPs and policies

A [configuration service provider (CSP)](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference?redirectedfrom=MSDN) is an interface to read, set, modify, or delete configuration settings on a device. In this release, we add support for more policies to increase the control administrators have over deployed HoloLens devices. For the list of CSPs supported by HoloLens, see [NetworkQoSPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp).

New in this release:

**Policy CSP** 

The Policy configuration service provider enables the enterprise to configure policies on Windows devices. In this release, we added new policies for HoloLens, which are listed here. To learn more, see [Policy CSPs supported by HoloLens 2](https://docs.microsoft.com/windows/client-management/mdm/policies-supported-by-hololens2).  

- LetAppsAccessCamera_ForceAllowTheseApps  
- LetAppsAccessCamera_ForceDenyTheseApps  
- LetAppsAccessCamera_UserInControlOfTheseApps 
- LetAppsAccessGazeInput 
- LetAppsAccessGazeInput_ForceAllowTheseApps 
- LetAppsAccessGazeInput_ForceDenyTheseApps 
- LetAppsAccessGazeInput_UserInControlOfTheseApps 
- LetAppsAccessMicrophone_ForceAllowTheseApps 
- LetAppsAccessMicrophone_ForceDenyTheseApps 
- LetAppsAccessMicrophone_UserInControlOfTheseApps 
- AllowWiFi 

**NetworkQoSPolicy CSP**

The NetworkQoSPolicy configuration service provider creates network quality-of-service (QoS) policies. A QoS policy performs a set of actions on network traffic based on a set of matching conditions. To learn more, see [NetworkQoSPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp).

### Expanded USB Ethernet support for 5G/LTE tethered devices

Support was added to enable certain mobile broadband devices, such as 5G/LTE phones and Wi-Fi hotpots, when they're tethered to the HoloLens 2 via USB. These devices are now displayed in **network settings** as another Ethernet connection. (Mobile broadband devices that require an external driver aren't supported.) This functionality enables high-bandwidth connections when Wi-Fi is not available and Wi-Fi tethering isn't performant enough. To learn more about supported USB devices, see [Connect to Bluetooth and USB-C devices](https://docs.microsoft.com/hololens/hololens-connect-devices).  

### Hand tracking improvements

This release includes several hand tracking improvements:

- **Pointing pose stability:** The system now resists bending the index finger when it gets occluded by the palm. This change improves the accuracy when you push buttons, type, scroll content, and more! 
- **Reduced accidental air taps:** We improved detection of the air tap gesture. There are now fewer accidental activations in several common scenarios, such as when you drop your hands to your sides.
- **User switch reliability:** The system is now faster and more reliable at updating the hand size when you share a device.
- **Reduced hand stealing:** We improved handling of cases where there are more than two hands in view of the sensors. If multiple people are working close together, there's now a much lower chance that the tracked hand will "jump" from the user to the hand of someone else in the scene.
- **System reliability:** Fixed an issue that caused hand tracking to stop working when the device is under high load.

### Dark mode

Many Windows apps now support both dark and light modes. HoloLens 2 users can choose the default mode for apps that support both. After the update, the default app mode is "dark," but you can easily change this setting: Navigate to **Settings** > **System** > **Colors** > **Choose your default app mode**. 

These "in-box" apps support dark mode: 

- Settings 
- Microsoft Store 
- Mail 
- Calendar 
- File Explorer 
- Feedback Hub 
- OneDrive 
- Photos 
- 3D Viewer 
- Movies & TV 

![Dark mode windows tiled](images/DarkMode.jpg)

### System voice commands

You can now use voice commands with any app on the device. For more information, see [Use your voice to operate HoloLens](https://docs.microsoft.com/hololens/hololens-cortana). Also see [Supported languages for HoloLens 2](https://docs.microsoft.com/hololens/hololens2-language-support).  

### Cortana updates

The updated app integrates with Microsoft 365 to help you get more done across your devices (currently in US-English only). On HoloLens 2, Cortana no longer supports certain device-specific commands, like adjusting volume or restarting. These options are now supported by the new system voice commands. Learn more about the new Cortana app in our [blog](https://blogs.windows.com/windowsexperience/2020/02/28/cortana-in-the-upcoming-windows-10-release-focused-on-your-productivity-with-enhanced-security-and-privacy/).

### Quality improvements and fixes

Improvements and fixes also in the update:  
- Introduced an active display calibration system. This feature improves the stability and alignment of holograms. They now stay in place when you move your head from side to side.
- Fixed a bug where Wi-Fi streaming to HoloLens got disrupted periodically. If an application indicates that it needs low latency streaming, implement the fix by calling the [SetSocketMediaStreamingMode function](https://docs.microsoft.com/windows/win32/api/socketapi/nf-socketapi-setsocketmediastreamingmode).
- Fixed a device hang that occurred during streaming in research mode.
- Fixed a bug where in some cases the right user wouldn't be displayed on the sign-in screen when resuming a session.
- Fixed an issue where users couldn't export MDM logs through **Settings**.
- Fixed an issue where the accuracy of eye tracking immediately following out-of-box setup could be lower than expected.
- Fixed an issue where the eye tracking subsystem failed to initialize or perform calibration under certain conditions.
- Fixed an issue where eye calibration would be prompted for an already-calibrated user.
- Fixed an issue where a driver would crash during eye calibration.
- Fixed an issue where repeated power button presses could cause a 60-second system timeout and shell crash.
- Improved stability for depth buffers.
- Added a **Share** button in the Feedback Hub so users can more easily share feedback.
- Fixed a bug where RoboRaid wan't installed correctly.

### Known issues

- An issue with the zh-CN system language prevents voice commands from taking a mixed reality capture or displaying the device IP address.
- An issue requires you to launch the Cortana app after starting the device to use "Hey Cortana" voice activation. If you updated from a 18362 build, you may also see a second app tile for the previous version of the Cortana app that no longer works in **Start**.

## Windows Holographic, version 1903 - May 2020 Update 
- Build 18362.1061

This monthly quality update doesn't contain any notable changes because the team was working on the Windows Holographic version 2004 May Update, as described earlier.

## Windows Holographic, version 1903 - April 2020 Update
- Build 18362.1059

**Dark mode for supported apps** 

Many Windows apps support both dark and light mode. HoloLens 2 customers can now choose the default mode for apps that support both color schemes. Based on customer feedback, we set the default app mode to "dark," but you can easily change this setting at any time: Navigate to **Settings > System > Colors** to find **"Choose your default app mode."**

These "in-box" apps support dark mode:
- Settings
- Microsoft Store
- Mail
- Calendar
- File Explorer
- Feedback Hub
- OneDrive
- Photos
- 3D Viewer
- Movies & TV

**Improvements and fixes also in the update:** 
- Ensured that shell overlays are included in mixed reality captures.
- Unreal developers can now use the 3D View page in Device Portal to test and debug their applications.
- Improved hologram stability in mixed reality capture when the *HolographicDepthReprojectionMethod DepthReprojection* algorithm is used.
- Fixed the "WinRT IStreamSocketListener API Class not registered" error on 32-bit ARM apps.

## Windows Holographic, version 1903 - March 2020 Update 
- Build 18362.1056

Improvements and fixes in the update:

- Improved hologram stability in mixed reality capture when the *HolographicDepthReprojectionMethod AutoPlanar* algorithm is used.
- Ensured that the coordinate system attached to a depth MF sample is consistent with public documentation.
- Improved developer productivity by enabling customers to paste large amounts of text through the device portal.

## Windows Holographic, version 1903 - February 2020 Update 
- Build 18362.1053

Improvements and fixes in the update:

- Temporarily disabled the HolographicSpace.UserPresence API for Unity applications. This change avoids an issue that caused some apps to pause when the visor was flipped up, even if the "run in the background" setting was enabled.
- Fixed a random HUP crash caused by hand tracking, in which the user noticed a UI freeze then back to shell after several seconds.
- Improved hand tracking so that when you poke with your index finger, the upper part of that finger is less likely to curl unexpectedly.
- Improved reliability of head tracking, spatial mapping, and other runtimes.

## Windows Holographic, version 1903 - January 2020 Update 
- Build 18362.1043
 
Improvements and fixes in the update:

- Improved stability for exclusive apps when working with the HoloLens 2 emulator.

## Windows Holographic, version 1903 - December 2019 Update 
- Build 18362.1042

Improvements and fixes in the update:

- Introduced last stage reproduction (LSR) fixes. Improved visual rendering of holograms to appear more stable and crisp by more accurately accounting for their depth. This symptom will be more noticeable after this update if apps don't set the depth of holograms correctly.
- Fixed stability of exclusive apps and navigation between exclusive apps.
- Resolved an issue where mixed reality capture couldn't record video after the device was in standby state for several days.
- Improved hologram stability.

## Windows Holographic, version 1903 - November 2019 Update 
- Build 18362.1039

Improvements and fixes in the update:

- Fixed functionality of **Select** voice commands during initial setup for en-CA and en-AU.
- Improved visual quality of objects placed far away in the latest Unity and Mixed Reality Toolkit (MRTK) versions.
- Fixed addressing issues with holographic applications getting stuck in a paused state on startup until the Start menu was opened and then closed.
- OpenXR runtime conformance fixes and improvements for HoloLens 2 and the emulator.
