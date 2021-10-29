---
title: HoloLens environment considerations
description: Get the best possible experience using HoloLens when you optimize the device for your eyes and environment.
author: dorreneb
ms.author: dobrown
manager: jarrettr
ms.date: 8/29/2019
ms.prod: hololens
ms.topic: article
audience: ITPro
ms.localizationpriority: high
keywords: holographic frame, field of view, fov, calibration, spaces, environment, how-to, HoloLens, mixed reality, mixed reality headsets
---

# HoloLens environment considerations

HoloLens blends the holographic with the "real" world, placing holograms in your surroundings. A holographic app window "hangs" on the wall, a holographic ballerina spins on the tabletop, bunny ears sit on top of your unwitting friend’s head. When you’re using an immersive game or app, the holographic world will spread to fill your surroundings but you can still see and move around the space.

The holograms you place will stay where you’ve put them, even if you turn off your device.

## Setting up an environment

HoloLens devices know how to place stable and accurate holograms by *tracking* users in a space. Without proper tracking, the device doesn't understand the environment or the user within it. Holograms can appear in the wrong places, not appear in the same spot every time, or not appear at all. The data used to track users is represented in the *spatial map*.  

Tracking performance is heavily influenced by the environment the user is in, and tuning an environment to induce stable and consistent tracking is an art rather than a science. Many different environmental factors are fused together to enable tracking, but as a Mixed Reality developer, there are several factors you can keep in mind to tune a space for better tracking.

### Lighting

Windows Mixed Reality uses visual light to track the user's location. When an environment is too bright, the cameras can get saturated, and nothing is seen. If the environment is too dark, the cameras can't pick up enough information, and nothing is seen. Lighting should be even and sufficiently bright a human can see without effort, but not so bright the light is painful to look at.  

Areas where there are points of bright light in an overall dim area are also problematic, as the camera has to adjust when moving in and out of bright spaces. This can cause the device to "get lost" and think that the change in light equates to a change in location. Stable light levels in an area will lead to better tracking.  

Any outdoor lighting can also cause instability in the tracker, as the sun may vary considerably over time. For example, tracking in the same space in the summer vs. winter can produce drastically different results, as the second hand light outside may be higher at different times of year.  

If you have a luxmeter, a steady 500-1000 lux is a good place to start.  

#### Types of lighting

Different types of light in a space can also influence tracking. Light bulbs pulse with the AC electricity running through it - if the AC frequency is 50 Hz, then the light pulses at 50 Hz. For a human, this pulsing isn't noticed. However, HoloLens' 30 fps camera sees these changes - some frames will be well-lit, some will be poorly lit, and some will be over-exposed as the camera tries to compensate for light pulses.  

In the USA, electricity frequency standard is 60 Hz, so light bulb pulses are harmonized with HoloLens' framerate - 60 Hz pulses align with HoloLens' 30 FPS framerate. However, many countries have an AC frequency standard of 50 Hz, which means some HoloLens frames will be taken during pulses, and others will not. In particular, fluorescent lighting in Europe has been known to cause issues.  

There are a few things you can try to resolve flickering issues. Temperature, bulb age, and warm-up cycles are common causes of fluorescent flickering and replacing bulbs may help. Tightening bulbs and making sure current draws are constant can also help.  

### Items in a space

HoloLens uses unique environmental landmarks, also known as *features*, to locate itself in a space.  

A device can almost never track in a feature-poor area, as the device has no way of knowing where in space it is. Adding features to the walls of a space is usually a good way to improve tracking. Posters, symbols taped to a wall, plants, unique objects, or other similar items all help. A messy desk is a good example of an environment that leads to good tracking - there are a lot of different features in a single area.  

Additionally, use unique features in the same space. The same poster repeated multiple times over a wall, for example, will cause device confusion as the HoloLens won't know which of the repetitive posters it's looking at. One common way of adding unique features is to use lines of masking tape to create unique, non-repetitive patterns along the walls and floor of a space.  

A good question to ask yourself is: if you saw just a small amount of the scene, could you uniquely locate yourself in the space? If not, it's likely the device will have problems tracking as well.

#### Wormholes

If you have two areas or regions that look the same, the tracker may think they're the same. This results in the device tricking itself into thinking it's somewhere else. We call these types of repetitive areas *wormholes*.  

To prevent wormholes, try to prevent identical areas in the same space. Identical areas can sometimes include factory stations, windows on a building, server racks, or work stations. Labeling areas or adding unique features to each similar-looking area can help mitigate wormholes.

### Movement in a space

If your environment is constantly shifting and changing, the device has no stable features to locate against.  

The more moving objects that are in a space, including people, the easier it's to lose tracking. Moving conveyor belts, items in different states of construction, and lots of people in a space have all been known to cause tracking issues.

The HoloLens can quickly adapt to these changes, but only when that area is clearly visible to the device. Areas that aren't seen as frequently may lag behind reality, which can cause errors in the spatial map. For example, a user scans a friend and then turns around while the friend leaves the room. A 'ghost' representation of the friend will persist in the spatial mapping data until the user re-scans the now empty space.

### Proximity of the user to items in the space

Similarly to how humans can't focus well on objects close to the eyes, HoloLens struggles when objects are close to its cameras. If an object is too close to be seen with both cameras, or if an object is blocking one camera, the device will have far more issues with tracking against the object.  

The cameras can see no closer than 15 cm from an object.

### Surfaces in a space

Strongly reflective surfaces will likely look different depending on the angle, which affects tracking. Think of a brand new car - when you move around it, light reflects and you see different objects in the surface as you move. To the tracker, the different objects reflected in the surface represent a changing environment, and the device loses tracking.

Less shiny objects are easier to track against.

### Wi-Fi fingerprint considerations

As long as Wi-Fi is enabled, map data will be correlated with a Wi-Fi fingerprint, even when not connected to an actual WiFi network/router. Without Wi-Fi info, the space and holograms may be slightly slower to recognize. If the Wi-Fi signals change significantly, the device may think it is in a different space altogether.

Network identification (such as SSID or MAC address) isn't sent to Microsoft, and all Wi-Fi references are kept local on the HoloLens.

## Mapping new spaces

When you enter a new space (or load an existing one), you’ll see a mesh graphic spreading over the space. This means your device is mapping your surroundings. While a HoloLens will learn a space over time, there are tips and tricks to map spaces.

## Environment management

Holograms exist in **Settings** > **System** > **Holograms** and **Settings** > **System** > **Privacy**  > **Environment**. There are two settings that enable users to “clean up” holograms and allow HoloLens to “forget" a space.

1. **Delete nearby holograms**.  When you select this setting, HoloLens erases all anchored holograms and all stored map data for the “current space” where the device is located. A new map section is created and stored in the database for that location once holograms are again placed in that same space.

    To delete nearby holograms, go to **Settings** > **System** > **Holograms** > **Remove nearby holograms**.

1. **Delete all holograms**. When you select this setting, HoloLens erases ALL map data and anchored holograms in the entire databases of spaces. Deleted holograms will not be rediscovered, and any holograms deleted will have to be replaced to again store map sections in the database.

    To delete all holograms, go to **Settings** > **System** > **Holograms** > **Remove all holograms**.

## Hologram quality

Holograms can be placed throughout your environment—high, low, and all around you—but you’ll see them through a [holographic frame](/windows/mixed-reality/holographic-frame) that sits in front of your eyes. To get the best view, make sure to adjust your device so you can see the entire frame. And don’t hesitate to walk around your environment and explore!

For your [holograms](/windows/mixed-reality/hologram) to look crisp, clear, and stable, your HoloLens needs to be calibrated just for you. When you first set up your HoloLens, you’ll be guided through this process. Later on, if holograms don’t look right or you’re seeing numerous errors, you can make adjustments.

If you're having trouble-mapping spaces, try deleting nearby holograms and remapping the space.

### Calibration

If your holograms look jittery or shaky, or if you’re having trouble placing holograms, the first thing to try is the [Calibration app](hololens-calibration.md). This app can also help if you’re experiencing any discomfort while using your HoloLens.

To get to the Calibration app, go to **Settings** > **System** > **Utilities**. Select **Open Calibration** and follow the instructions.

If someone else is going to be using your HoloLens, they should run the Calibration app first so the device is set up properly for them.

## Temperature and regulatory information

[HoloLens Regulatory information](https://support.microsoft.com/en-us/help/13761/hololens-regulatory-information): Includes information on temperature range, disposal, radio and TV interference, and more.

See details for "HoloLens" in [Materials and substances](https://www.microsoft.com/legal/compliance/materials-substances) > REACH Article 33 Disclosure on Environmental Compliance (PDF).

Here are some guidelines to follow when using your device:

1. Store device in an environment within temperature range (either in Standby or Off) for an hour before using the device.
1. Use device in an environment within temperature range.
1. Use device indoors.
1. Use device in shade; even indoors avoid direct sunlight though windows or skylights.
1. If you follow the above guidelines but experience unexpected overheating issues, follow the below steps for submitting [Feedback](hololens-feedback.md). 
    1. Ensure **Full** or **Optional** telemetry is enabled on your device. If it is not, enable it. 
    >[!CAUTION]
    > Telemetry is not retroactive for thermal events - it must be enabled during the overheating or the required data will not be captured.
    
    2. Reproduce the heating issue.
    3. Include the date and time the overheating occurred.
    4. Submit [Feedback](hololens-feedback.md).

## See also

- [Spatial mapping design](/windows/mixed-reality/spatial-mapping)
- [Holograms](/windows/mixed-reality/hologram)
