---
title: Insider preview for Microsoft HoloLens
description: Learn how to get started with Insider builds and provide valuable feedback for our next major operating system update for HoloLens.
ms.prod: hololens
ms.sitesec: library
author: scooley
ms.author: scooley
ms.topic: article
ms.custom:
- CI 111456
- CSSTroubleshooting
ms.localizationpriority: medium
audience: ITPro
ms.date: 04/01/2021
ms.reviewer: 
manager: laurawi
appliesto:
- HoloLens 2
---

# Insider preview for Microsoft HoloLens

Welcome to the latest Insider Preview builds for HoloLens! It's simple to [get started](hololens-insider.md#start-receiving-insider-builds) and provide valuable feedback for our next major operating system update for HoloLens.

## Windows Insider Release Notes

We're excited to start flighting new features to Windows Insiders again. New builds will be flighting to the Dev and Beta Channels for the latest updates. We will continue to update this page as we add more features and updates to our Windows Insider builds. Get excited and ready to mix these updates into your reality. 

### OneDrive for work or school Camera Roll upload

*Introduced in build 20346.1402*

We've added a new feature to the HoloLens 2 Settings app, which allows customers to automatically upload mixed reality photos and videos from the device's Pictures > Camera Roll folder to the corresponding OneDrive for work or school folder. This feature addresses a [feature gap within the OneDrive app](holographic-photos-and-videos.md#share-your-mixed-reality-photos-and-videos) on HoloLens 2, which only supports automatic Camera Roll upload to a customer's personal Microsoft account (and not their work or school account).

**How it works**

- Visit **Settings > System > Mixed Reality Camera** to enable "Camera upload."
- By setting this feature to the **On** position, any mixed reality photos or videos captured to your device will automatically be queued for upload to the Pictures > Camera Roll folder of your OneDrive for work or school account.
    >[!NOTE]
    >Photos and videos captured prior to enabling this feature *will not* be queued for upload and will still need to be manually uploaded.
- A status message on the Settings page will display the number of files pending upload (or read "OneDrive is up to date" when all pending files have been uploaded).
- If you're concerned about bandwidth or want to "pause" upload for any reason, you can switch the feature to the **Off** position. Temporarily disabling the feature ensures that the upload queue will continue to increase as you add new files to the Camera Roll folder, but files will not upload until you re-enable the feature.
- Newest files will upload first (last in, first out).
- If your OneDrive account has issues (for example, after your password changes) a **Fix now** button will appear on the Settings page.
- There is no maximum file size, but note that large files will take longer to upload (especially if your upload bandwidth is constrained). If you "pause" or turn off upload while a large file is being uploaded, the partial upload will be preserved. If upload is re-enabled within several hours of being "paused" or turned off, the upload will continue from where it left off. However, if upload is re-enabled after several hours, the large file's upload will restart from the beginning.

**Known issues and caveats**

- This setting has no built in throttling based on current bandwidth usage. If you need to maximize bandwidth for another scenario, turn off the setting manually. Upload will be paused but the feature will continue to monitor newly added files to Camera Roll. Re-enable upload when you're ready for it to continue.
- This feature must be enabled for each user account on the device, and it can only actively upload files for the user who is currently signed-in to the device.
- If you're taking photos or videos while watching the upload count on the Settings page in real-time, note that the pending file count may not change until the current file has completed uploading.
- Upload will pause if your device falls asleep or is powered off. To ensure your pending uploads complete, actively use the device until the Settings page reads "OneDrive is up to date" or adjust your **Power & sleep** settings.

## Start receiving Insider builds
> [!NOTE]
> If you haven’t updated recently, please reboot your device to update state and get the latest build.
> -	The “Reboot device” voice command works well. 
> -	You can also choose the restart button in Settings/Windows Insider Program.
>
> We had a bug on the back-end that you may have encountered and this will get you back on track.

On a HoloLens 2 device go to **Settings** > **Update & Security** > **Windows Insider Program** and select **Get started**. Link the account you used to register as a Windows Insider.
Windows insider is now moving to Channels. The **Fast** ring will become the **Dev Channel**, the **Slow** ring will become the **Beta Channel**, and the **Release Preview** ring will become the **Release Preview Channel**. Here is what that mapping looks like:
![Windows Insider Channels explanation](images/WindowsInsiderChannels.png)
For more information, see [Introducing Windows Insider Channels](https://blogs.windows.com/windowsexperience/2020/06/15/introducing-windows-insider-channels) on Windows Blogs.
Then, select **Active development of Windows**, choose whether you'd like to receive **Dev Channel** or **Beta Channel** builds, and review the program terms.
Select **Confirm > Restart Now** to finish up. After your device has rebooted, go to **Settings > Update & Security > Check for updates** to get the latest build.
### Update error 0x80070490 work-around
If you encounter an update error 0x80070490 when updating on the Dev or Beta channel, try the following short-term work around. It involves moving your insider channel, picking up the update and then moving your Insider channel back.
#### Stage one - Release Preview
1.	Settings, Update & Security, Windows Insider Program, select **Release Preview Channel**.
2.	Settings, Update & Security, Windows Update, **Check for updates**. After the update, continue on to Stage two.
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
> There is a known issue in which users who un-enroll from Insider Preview builds after manually reinstalling a fresh preview build would experience a blue screen. Afterwards they must manually recover their device. For full details on if you would be impacted or not, please view more on this [Known Issue](https://docs.microsoft.com/hololens/hololens-known-issues?source=docs#blue-screen-is-shown-after-unenrolling-from-insider-preview-builds-on-a-device-reflashed-with-a-insider-build).
To verify that your HoloLens is running a production build:
1. Go to **Settings > System > About**, and find the build number.
1. [See the release notes for production build numbers](hololens-release-notes.md).
To opt out of Insider builds:
1. On a HoloLens running a production build, go to **Settings > Update & Security > Windows Insider Program**, and select **Stop Insider builds**.
1. Follow the instructions to opt out your device.
