---
title: Troubleshooting
description: Stay up to date on the most common solutions to HoloLens device issues and troubleshooting techniques.
author: mattzmsft
ms.author: mazeller
ms.date: 12/02/2019
ms.prod: hololens
ms.topic: article
audience: HoloLens
ms.localizationpriority: medium
manager: jarrettr
ms.custom: 
- CI 111456
- CSSTroubleshooting
keywords: issues, bug, troubleshoot, fix, help, support, HoloLens
---

# Troubleshooting

This article describes how to resolve several common HoloLens issues.

## My HoloLens is unresponsive or won't start

If your HoloLens won't start:

- If the LEDs next to the power button don't light up, or only one LED briefly blinks, you may need to [charge your HoloLens.](hololens-recovery.md#charge-the-device)
- If the LEDs light up when you press the power button but you can't see anything on the displays, [preform a hard reset of the device](hololens-recovery.md#hard-reset-procedure).

If your HoloLens becomes frozen or unresponsive:

- Turn off your HoloLens by pressing the power button until all five of the LEDs turn themselves off, or for 15 seconds if the LEDs are unresponsive. To start your HoloLens, press the power button again.

If these steps don't work, you can try [recovering your HoloLens 2 device](hololens-recovery.md) or [HoloLens (1st gen) device.](hololens1-recovery.md)

## Holograms don't look good

If your holograms are unstable, jumpy, or don't look right, try:

- Cleaning your device visor and sensor bar on the front of your HoloLens.
- Increasing the light in your room.
- Walking around and looking at your surroundings so that HoloLens can scan them more completely.
- Calibrating your HoloLens for your eyes. Go to **Settings** > **System** > **Utilities**. Under **Calibration**, select **Open Calibration**.
 
### Reporting issues where Holograms are unstable or don't look right
 
1. Please record and a [Mixed Reality Capture video](holographic-photos-and-videos.md#capture-a-mixed-reality-video) of the issue. This video can be later uploaded through Feedback Hub as an attached file.  
1. Enable full telemetry via the **Settings** app -> **Privacy** -> **Diagnostics & feedback** and under **Optional diagnostics data** ensure the toggle is set to **On**
1. Get the latest hologram scale and stability fixes by updating to the latest [Windows Holographic OS, (20H2 or higher)](hololens-release-notes.md#windows-holographic-version-20h2). After updating perform the following:
    1. Remove all Holograms via **Settings** app -> **System** -> **Holograms** -> then select **Remove all holograms** and start with a fresh map.
    1. Create a new map of your space by wearing the HoloLens and walking around your room and looking at all areas and surfaces in the space. Do this for 2-3 minutes.
    1. Perform IPD calibration. Go to **Settings** > **System** > **Utilities**. Under **Calibration**, select **Open Calibration**.
    1. Re-test the scenario and see if it still persists.
1. If updating does not fix the issue, please file a [Feedback Hub issue](hololens-feedback.md). After you've filled feedback you can use the **Share** button, to create an easy to share link that can be sent when contacting support.

## HoloLens doesn't respond to hand input

To ensure that HoloLens can see your hands, you need to keep them in the gesture frame.  The Mixed Reality Home provides feedback that lets you know when your hands are tracked.  The feedback is different on different versions of HoloLens:
- On HoloLens (1st gen), the gaze cursor changes from a dot to a ring
- On HoloLens 2, a fingertip cursor appears when your hand is close to a slate, and a hand ray appears when slates are further away

Many immersive apps follow input patterns that are similar to Mixed Reality Home.  Learn more about using hand input on [HoloLens (1st gen)](hololens1-basic-usage.md#use-hololens-with-your-hands) and [HoloLens 2](hololens2-basic-usage.md#the-hand-tracking-frame).

If you are wearing gloves, note that some types of gloves do not work with hand tracking.  A common example is black rubber gloves, which tend to absorb infrared light and are not picked up by the depth camera.  If your work involves rubber gloves, we recommend trying a lighter color such as blue or gray.  Another example is large baggy gloves, which tend to obscure the shape of your hand. We recommend using gloves that are as form-fitting as possible for best results.

If your visor has fingerprints or smudges, use the microfiber cleaning cloth that came with the HoloLens to clean your visor gently.

## HoloLens doesn't respond to my voice commands

If Cortana isn't responding to your voice commands, make sure Cortana is turned on. On the All apps list, select **Cortana** > **Menu** > **Notebook** > **Settings** to make changes. To learn more about what you can say, see [Use your voice with HoloLens](hololens-cortana.md).

## I can't place holograms or see holograms that I previously placed

If HoloLens can't map or load your space, it enters Limited mode and you won't be able to place holograms or see holograms that you've placed. Here are some things to try:

- Make sure that there's enough light in your environment so HoloLens can see and map the space.
- Make sure that you're connected to a Wi-Fi network. If you're not connected to Wi-Fi, HoloLens can't identify and load a known space.
- If you need to create a new space, connect to Wi-Fi, then restart your HoloLens.
- To see if the correct space is active, or to manually load a space, go to **Settings** > **System** > **Spaces**.
- If the correct space is loaded and you're still having problems, the space may be corrupt. To fix this issue, select the space, then select **Remove**. After you remove the space, HoloLens starts to map your surroundings and create a new space.

## My HoloLens can't tell what space I'm in

If your HoloLens can't identify and load the space you're in automatically, check the following factors:

- Make sure that you're connected to Wi-Fi
- Make sure that there's plenty of light in the room
- Make sure that there haven't been any major changes to the surroundings.

You can also load a space manually or manage your spaces by going to **Settings** > **System** > **Spaces**.

## I'm getting a "low disk space" error

You'll need to free up some storage space by doing one or more of the following:

- Delete some unused spaces. Go to **Settings** > **System** > **Spaces**, select a space that you no longer need, and then select **Remove**.
- Remove some of the holograms that you've placed.
- Delete some pictures and videos from the Photos app.
- Uninstall some apps from your HoloLens. In the **All apps** list, tap and hold the app you want to uninstall, and then select **Uninstall**.

## My HoloLens can't create a new space

The most likely problem is that you're running low on storage space. Try one of the [previous tips](#im-getting-a-low-disk-space-error) to free up some disk space.

## The HoloLens emulator isn't working

Information about the HoloLens emulator is located in our developer documentation.  Read more about [troubleshooting the HoloLens emulator](https://docs.microsoft.com/windows/mixed-reality/using-the-hololens-emulator#troubleshooting).
