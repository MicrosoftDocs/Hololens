---
title: Frequently asked questions about HoloLens devices and holograms
description: Do you have a quick question about HoloLens or interacting with holograms?  This article provides a quick answer and more resources.
keywords: hololens, faq, known issue, help
ms.prod: hololens
ms.sitesec: library
author: Teresa-Motiv
ms.author: v-tea
ms.topic: article
audience: ITPro
ms.localizationpriority: medium
ms.date: 02/27/2020
ms.reviewer: 
ms.custom: 
- CI 114606
- CSSTroubleshooting
manager: jarrettr
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Hologram Troubleshooting

This article troubleshoots issues with placing holograms, working with spaces, and reporting issues with holograms.

Anytime that you have problems, make sure:
- The HoloLens is [charged up](https://support.microsoft.com/help/12627/hololens-charge-your-hololens) (charged for at least an hour). 
- Try [restarting it](hololens-restart-recover.md) to see whether that fixes things.

Please use the Feedback app to send us information about the issue. You'll find the Feedback app on the [**Start** menu](holographic-home.md). 

For tips about how to wear your HoloLens, see [Adjust Fit](hololens2-setup.md#adjust-fit).

<a id="list"></a>
- [New spaces can't be created](#new-spaces-cant-be-created)
- [Spaces can't be identified or loaded](#spaces-cant-be-identified-or-loaded)
- [How do I delete all spaces?](how-do-i-delete-all-spaces)
- [Holograms don't look right or are moving around](#holograms-dont-look-right-or-are-moving-around)
- ["Finding your space" message](#finding-your-space-message)
- [Expected holograms aren't showing in my space](#expected-holograms-arent-showing-in-my-space)
- [Can't place holograms or see previously placed holograms](#cant-place-holograms-or-see-previously-placed-holograms)
- [Holograms disappear or are encased in other holograms or objects](#holograms-disappear-or-are-encased-in-other-holograms-or-objects)
- [Holograms are appearing on the other side of a wall](#holograms-are-appearing-on-the-other-side-of-a-wall)
- [After placing a hologram on a wall, it seems to float](#after-placing-a-hologram-on-a-wall-it-seems-to-float)
- [Apps appear too close after moving them](#apps-appear-too-close-after-moving-them)
- [Reporting issues with unstable or inexact holograms](#reporting-issues-with-unstable-or-inexact-holograms)

## New spaces can't be created

The most likely problem is that you're running low on storage space. [Free up some disk space](hololens-troubleshooting.md#low-disk-space-error) and then retry.

[Back to list](#list)

## Spaces can't be identified or loaded

If your HoloLens can't identify and load the space you're in automatically, check the following factors:

- Make sure that you're connected to Wi-Fi
- Make sure that there's plenty of light in the room
- Make sure that there haven't been any major changes to the surroundings.

You can also load a space manually or manage your spaces by going to **Settings** > **System** > **Spaces**.

[Back to list](#list)

## How do I delete all spaces?

*Coming soon*

[Back to list](#list)

## Holograms don't look right or are moving around

If your holograms don't look right (for example, they're jittery or shaky, or you see black patches on top of them), try one of these fixes:

- [Clean your device visor](hololens1-hardware.md#care-and-cleaning) and make sure nothing is blocking the sensors.
- Make sure that you're in a well-lit room that does not have a lot of direct sunlight.
- Try walking around and gazing at your surroundings so that HoloLens can scan them more completely.
- If you've placed a lot of holograms, try removing some.

If you're still having problems, trying running the Calibration app. This app calibrates your HoloLens just for you to help keep your holograms looking their best. To do this, go to **Settings** > **System** > **Utilities**. Under **Calibration**, select **Open Calibration**.

[Back to list](#list)

## "Finding your space" message

When HoloLens is learning or loading a space, you may see a brief message that says "Finding your space." If this message displays for more than a few seconds, you'll see another message under the Start menu that says "Still looking for your space."

These messages mean that HoloLens is having trouble mapping your space. When this happens, you can open apps, but you can't place holograms in your environment.

If you see these messages often, try one or more of the following fixes:

- Make sure that you're in a well-lit room that does not have a lot of direct sunlight.
- Make sure that your device visor is clean. [Learn how to clean your visor](hololens1-hardware.md#care-and-cleaning).
- Make sure that you have a strong Wi-Fi signal. If you enter a new environment that has no Wi-Fi or a weak Wi-Fi signal, HoloLens won't be able find your space. Check your Wi-Fi connection by going to **Settings** > **Network &amp; Internet** > **Wi-Fi**.
- Try moving more slowly.

[Back to list](#list)

## Expected holograms aren't showing in my space

If you don't see the holograms that you placed, or if you're seeing some that you don't expect, try one or more of the following fixes:

- Turn on some lights. HoloLens works best in a well-lit space.
- Remove holograms that you don't need by going to **Settings** > **System** > **Holograms** > **Remove nearby holograms**. Or, if needed, select **Remove all holograms**.

  > [!NOTE]
  > If the layout or lighting in your space changes significantly, your device might have trouble identifying your space and showing your holograms.

[Back to list](#list)

## Can't place holograms or see previously placed holograms

If HoloLens can't map or load your space, it enters Limited mode and you won't be able to place holograms or see holograms that you've placed. Here are some things to try:

- Make sure that there's enough light in your environment so HoloLens can see and map the space.
- Stand between one and three meters from where you're trying to place the hologram.
- Don't place holograms on black or reflective surfaces.
- Make sure that you're connected to a Wi-Fi network. If you're not connected to Wi-Fi, HoloLens can't identify and load a known space.
- Walk around the rooms so HoloLens can rescan your surroundings. To see what's already been scanned, air tap to reveal the mapping mesh graphic.
- If you need to create a new space, connect to Wi-Fi, then restart your HoloLens.
- To see if the correct space is active, or to manually load a space, go to **Settings** > **System** > **Spaces**.
- If the correct space is loaded and you're still having problems, the space may be corrupt. To fix this issue, select the space, then select **Remove**. After you remove the space, HoloLens starts to map your surroundings and create a new space.

[Back to list](#list)

## Holograms disappear or are encased in other holograms or objects

If you get too close to a hologram, it will temporarily disappear&mdash;to restore the hologram, just move away from it. Also, if you've placed several holograms close together, some may disappear. Try removing a few.

Holograms can also be blocked or encased by other holograms or by objects such as walls. If this happens, try one of the following fixes:

- If the hologram is encased in another hologram, move the encased hologram to another location. To do this, select **Adjust**, then tap and hold to position it.
- If the hologram is encased in a wall, select **Adjust**, then walk toward the wall until the hologram appears. Tap and hold, then pull the hologram forward and out of the wall.
- If you can't move the hologram by using gestures, use your voice to remove it. Gaze at the hologram, then say "Remove." Then reopen the hologram and place it in a new location.

[Back to list](#list)

## Holograms are appearing on the other side of a wall

If you're very close to a wall, or if HoloLens hasn't scanned the wall yet, you can see holograms that are in the next room. To scan the wall, stand between one and three meters from the wall and gaze at it.

A black or reflective object (for example, a black couch or a stainless steel refrigerator) near the wall may cause problems when HoloLens tries to scan the wall. If there is such an object, scan the other side of the wall.

[Back to list](#list)

## After placing a hologram on a wall, it seems to float

A hologram that you place on a wall typically appears to be an inch or so away from the wall. If it appears to be farther away, try one or more of the following fixes:

- When you place a hologram on a wall, stand between one and three meters from the wall and face the wall straight on.
- Air tap the wall to reveal the mapping mesh graphic. Make sure that the mesh aligns with the wall. If it doesn't, remove the hologram, rescan the wall, and then try again.
- If the issue persists, run the Calibration app. You'll find it in **Settings** > **System** > **Utilities**.

[Back to list](#list)

## Apps appear too close after moving them

Try walking around and looking at the area where you're placing the app so that HoloLens scans the area from different angles. [Cleaning your device visor](hololens1-hardware.md#care-and-cleaning) may also help.

[Back to list](#list)

## Reporting issues with unstable or inexact holograms
 
1. Please record and a [Mixed Reality Capture video](holographic-photos-and-videos.md#capture-a-mixed-reality-video) of the issue. This video can be later uploaded through Feedback Hub as an attached file.  
1. Enable full telemetry via the **Settings** app -> **Privacy** -> **Diagnostics & feedback** and under **Optional diagnostics data** ensure the toggle is set to **On**
1. Get the latest hologram scale and stability fixes by updating to the latest [Windows Holographic OS, (20H2 or higher)](hololens-release-notes.md#windows-holographic-version-20h2). After updating perform the following:
    1. Remove all Holograms via **Settings** app -> **System** -> **Holograms** -> then select **Remove all holograms** and start with a fresh map.
    1. Create a new map of your space by wearing the HoloLens and walking around your room and looking at all areas and surfaces in the space. Do this for 2-3 minutes.
    1. Perform IPD calibration. Go to **Settings** > **System** > **Utilities**. Under **Calibration**, select **Open Calibration**.
    1. Re-test the scenario and see if it still persists.
1. If updating does not fix the issue, please file a [Feedback Hub issue](hololens-feedback.md). After you've filled feedback you can use the **Share** button, to create an easy to share link that can be sent when contacting support.

[Back to list](#list)