---
title: Capture, record, and share mixed reality photos and videos
description: Learn how to capture, record, and view, and mixed reality photos and videos using HoloLens mixed reality devices. Learn how to share via Miracast or gathered files.
keywords: hololens, photo, video, capture, mrc, mixed reality capture, photos, camera,  miracast, stream, livestream, demo, record
ms.assetid: 1b636ec3-6186-4fbb-81b2-71155aef0593
ms.prod: hololens
ms.sitesec: library
author: mattzmsft
ms.author: mazeller
ms.topic: article
audience: ITPro
ms.localizationpriority:
ms.date: 10/28/2019
manager: jarrettr
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Create mixed reality photos and videos

HoloLens gives users the experience of mixing the real world with the digital world.  Mixed reality capture (MRC) lets you capture that experience as a photo or video, or share what you see with others in real-time.

Mixed reality capture uses a first-person point of view so other people can see holograms as you see them. For a third-person point of view, use [spectator view](/windows/mixed-reality/spectator-view). Spectator view is especially useful for demos.

While it's fun to share videos amongst friends and colleagues, videos can also help teach other people to use an app or to communicate problems with apps and experiences.

> [!NOTE]
> If you can't launch mixed reality capture experiences and your HoloLens is a work device, check with your system administrator. Access to the camera can be restricted through company policy.

## Capture a mixed reality photo

There are several ways to take a photo of mixed reality on HoloLens; you can use hardware buttons, voice, or the Start menu.

### Hardware buttons to take photos

To take a quick photo of your current view, press the volume up and volume down buttons at the same time.  This is a bit like the HoloLens version of a screenshot or print screen.

- [Button locations on HoloLens 2](hololens2-hardware.md)
- [Button locations on HoloLens (1st gen)](hololens1-hardware.md#hololens-components)

> [!NOTE]
> Holding the **volume up** and **volume down** buttons for three seconds will start recording a video rather than taking a photo. To stop recording, tap both **volume up** and **volume down** buttons simultaneously.

### Voice commands to take photos

On HoloLens 2, version 2004 (and later), say: "Take a picture."

On HoloLens (1st gen) or HoloLens 2, version 1903, say: "Hey Cortana, take a picture."

### Start menu to take photos

Use the Start gesture to go to **Start**, then select the **Camera** icon.

Point your head in the direction of what you want to capture, then [air tap](hololens2-basic-usage.md#touch-holograms-near-you) to take a photo. You can continue to air tap and capture additional photos. Any photos you capture will be saved to your device.

Use the Start gesture again to end photo capture.  

## Capture a mixed reality video

There are several ways to record a video of mixed reality on HoloLens; you can use hardware buttons, voice, or the Start menu.

### Hardware buttons to record videos

The quickest way to record a video is to press and hold the **volume up** and **volume down** buttons simultaneously until a three-second countdown begins. To stop recording, tap both buttons simultaneously.

> [!NOTE]
> Quickly pressing the **volume up** and **volume down** buttons at the same time will take a photo rather than recording a video.

### Voice to record videos

On HoloLens 2, version 2004 (and later), say: "Start recording." To stop recording, say "Stop recording."

On HoloLens (1st gen) or HoloLens 2, version 1903, say: "Hey Cortana, start recording." To stop recording, say "Hey Cortana, stop recording."

### Start menu to record videos

Use the Start gesture to go to **Start**, then select the **Video** icon. Point your head in the direction of what you want to capture, then [air tap](hololens2-basic-usage.md#touch-holograms-near-you) to start recording. There will be a three second countdown and your recording will begin.

To stop recording, use the Start gesture and select the highlighted **Video** icon. The video will be saved to your device.

> [!NOTE]
> **Applies to HoloLens (1st gen) only**  
> The [Windows 10 October 2018 Update](/windows/mixed-reality/release-notes-october-2018) changes how the Start gesture and Windows button behave on HoloLens (1st gen). Before the update, the Start gesture or Windows button would stop a video recording. After the update, however, the Start gesture or Windows button opens the **Start** menu (or the **quick actions menu** if you are in an immersive app), from which you can select the highlighted **video** icon to stop recording.

## Share what you see in real-time

You can share what you see in HoloLens with friends and colleagues in real-time. There are a few methods available:

1. Connecting to a Miracast-enabled device or adapter to watch on a TV.
1. Using [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) to watch on a PC
1. Using the [Microsoft HoloLens companion app](https://www.microsoft.com/store/productId/9NBLGGH4QWNX) to watch on a PC.
1. Deploying the [Microsoft Dynamics 365 Remote Assist](https://dynamics.microsoft.com/en-us/mixed-reality/remote-assist) app, which enables front-line workers to stream what they see to a remote expert. The remote expert can then guide the front-line worker verbally or by annotating in their world.

> [!NOTE]
> Sharing what you see via Windows Device Portal or Microsoft HoloLens companion app requires your HoloLens to be in [Developer mode](/windows/mixed-reality/using-the-windows-device-portal#setting-up-hololens-to-use-windows-device-portal).

### Stream video with Miracast

Use the Start gesture to go to **Start**, then select the **Connect** icon. From the picker that appears, select the Miracast-enabled device or adapter to which you want to connect.

To stop sharing, use the Start gesture and select the highlighted **Connect** icon. Because you were streaming, nothing will be saved to your device.

> [!NOTE]
> Miracast support was enabled on HoloLens (1st gen) beginning with the [Windows 10 October 2018 Update](/windows/mixed-reality/release-notes-october-2018).

### Real time video with Windows Device Portal

Because sharing via Windows Device Portal requires Developer mode to be enabled on HoloLens, follow the instructions in our developer documentation to [set up Developer mode and navigate Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal).

### Microsoft HoloLens companion app

Because sharing via the Microsoft HoloLens companion app requires Developer mode to be enabled on HoloLens, follow the instructions in our developer documentation to [set up Developer mode](/windows/mixed-reality/using-the-windows-device-portal). Then, download the [Microsoft HoloLens companion app](https://www.microsoft.com/store/productId/9NBLGGH4QWNX) and follow the instructions within the app to connect to your HoloLens.

Once the app is set up with your HoloLens, select the **Live stream** option from the app's main menu.

## View your mixed reality photos and videos

Mixed reality photos and videos are saved to the device's "Camera Roll". You can browse the contents of this folder on your HoloLens with the File Explorer app (navigate to **Pictures > Camera Roll**).

You can also view your mixed reality photos and videos in the Photos app, which is pre-installed on HoloLens. To pin a photo in your world, select it in the Photos app and choose **Place in mixed world**. You can move the photo around your world after it's been placed.

To view and/or save your mixed reality photos and videos on a PC connected to HoloLens, you can use [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal#mixed-reality-capture) or your [PC's File Explorer via MTP](/windows/mixed-reality/release-notes-april-2018#new-features-for-hololens).

### Use File Explorer to get your pictures, videos and files

Similar to other mobile devices, connect your HoloLens to your PC to bring up File Explorer to access your HoloLens libraries (photos, videos, documents) for easy transfer. This method is easy to use and does not require the use of device portal or Wi-Fi.

1. Unlock the device.
1. Connect the device to a PC via USB.
1. File Explorer should open on your PC.
1. Navigate to: This PC\\*yourhololensname*\Internal Storage\Pictures\Camera Roll
1. Copy whatever files you need to your PC.

Tips:
- If you don't see any files, please ensure you sign in to your HoloLens to enable access to your data.
- You can get other files in other folders, such as [diagnostics files](hololens-diagnostic-logs.md#offline-diagnostics) from the Documents folder.
- From File Explorer on your PC, you can select Device properties to see Windows Holographic OS version number (firmware version), device serial number, and battery percentage.
- If your Organization has used MDM to disable [Connectivity/AllowUSBConnection](/windows/client-management/mdm/policy-csp-connectivity#connectivity-allowusbconnection) then you will be unable to connect to your device.

## Share your mixed reality photos and videos

Prior to [Windows Holographic, version 21H1](hololens-release-notes.md#windows-holographic-version-21h1), after capturing a mixed reality photo or video, a preview will appear. Select the **Share** icon above the preview to bring up the share assistant. From there, you can select the end point to which you'd like to share that photo or video.

With Windows Holographic, version 21H1, after capturing a mixed reality photo or video, a preview will appear. Select the **Share** icon above the preview to bring up the share assistant. From there, you can select the end point (Mail, OneDrive, etc.) to which you'd like to share that photo or video. You can also enable your HoloLens to share with nearby devices by going to **Settings -> System -> Shared Experiences**. For more details, read [Share things with nearby devices in Windows 10](https://support.microsoft.com/windows/share-things-with-nearby-devices-in-windows-10-0efbfe40-e3e2-581b-13f4-1a0e9936c2d9).

> [!TIP] 
> You can also share mixed reality photos and videos from OneDrive by automatically uploading your mixed reality photos and videos. Open the OneDrive app on HoloLens and sign in with a **personal [Microsoft account](https://account.microsoft.com)**, if you haven't already. Select the **Settings** icon and choose **Camera upload**. Turn Camera upload on. Your mixed reality photos and videos will now be uploaded to OneDrive each time you launch the app on HoloLens.

> [!NOTE]
> You can only enable camera upload in OneDrive if you’re signed into OneDrive with a personal Microsoft account. If you set up HoloLens with a work or school account, you can add a personal Microsoft account in the OneDrive app to enable this feature.

## Limitations of mixed reality capture

- While using mixed reality capture, the frame rate of HoloLens will be halved to 30 Hz.
- The resolution of photos and videos may be reduced if the photo/video camera is already in use by another application, while live streaming, or when system resources are low.

### Maximum recording length

On HoloLens 2 devices before the Windows Holographic, version 20H2, videos recorded on the device were limited to maximum length of five minutes.

Due to customer feedback, we’ve increased the recording length of [mixed reality captures](holographic-photos-and-videos.md). Mixed reality captures will no longer be limited to 5 minutes by default, but instead will calculate the maximum recording length based on available disk space. The device will estimate the max video recording duration based on available disk space up to 80% of the total disk space.

> [!NOTE]
> The HoloLens will use default video recording length (5 minutes) if one of the following occurs:
> -	The estimated max recording duration is smaller than the default 5 mins.
> -	The available disk space is less than 20% of the total disk space.

## Default file format and resolution

### Default photo format and resolution

|  Device  |  Format  |  Extension  |  Resolution  |
|----------|----------|----------|----------|
| HoloLens 2 | [JPEG](https://en.wikipedia.org/wiki/JPEG) | .jpg | 3904x2196px |
| HoloLens (1st gen) | [JPEG](https://en.wikipedia.org/wiki/JPEG) | .jpg | 1408x792px |

### Recorded video format and resolution

| Device | Format | Extension | Resolution | Speed | Audio |
|----------|----------|----------|----------|----------|----------|
| HoloLens 2 | [MPEG-4](https://en.wikipedia.org/wiki/MPEG-4) | .mp4 | 1920x1080px | 30fps | 48kHz Stereo |
| HoloLens (1st gen) |  [MPEG-4](https://en.wikipedia.org/wiki/MPEG-4) | .mp4 | 1216x684px | 24fps | 48kHz Stereo |
