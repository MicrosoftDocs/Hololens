---
title: HoloLens 2 Capabilities and Solutions
description: Learn about the Microsoft HoloLens Commercial features that make it easier for businesses to manage HoloLens devices. 
author: scooley
ms.author: scooley
ms.date: 08/26/2019
ms.custom: 
- CI 111456
- CSSTroubleshooting
ms.topic: article
audience: ITPro
ms.prod: hololens
ms.sitesec: library
ms.localizationpriority: high
ms.reviewer: 
manager: skerewa
appliesto:
- HoloLens 2
keywords: HoloLens, commercial, features, mdm, mobile device management, kiosk mode, applications, identity
---

# What can HoloLens 2 do for you?

HoloLens 2 enables enterprises to confidently deploy mixed reality applications to be more productive and act with precision. HoloLens 2 brings digital intelligence into the real world at the point of work, enhancing collaboration and allowing workers to comfortably work heads-up, hands free to seamlessly complete critical tasks safely and error free. 


[!INCLUDE [solutions](includes/hlsolutions.md)]

## HoloLens 2 capabilities

Collaborate without boundaries and act with precision at the point of work to increase employee productivity with mixed reality applications on HoloLens 2.


| Feature | Description |
|---------|-------------|
| Windows Hello for Business | Iris-based biometric authentication gets you quickly and securely into the flow of work. |
| Windows Autopilot | Setup and preconfigure services for HoloLens 2 so they're ready to use right out of the box across distributed worksites. |
| World Anchoring | Anchored holograms stay precisely in place. HoloLens 2 understands your workspace. So, digital content persists over time – anchored to objects or surfaces where you work. |
| Hand tracking | Touch, grasp and move holograms in ways that feel natural. HoloLens 2 adapts to your hands for a newfound satisfaction in your interactions. |
| Eye tracking | Enjoy a new level of context and human understanding. HoloLens 2 understands precisely where you’re looking, so it can understand your intent and adapt the holograms to your eyes in real time. |
| Voice enabled | Built-in voice commands allow you to quickly navigate and operate HoloLens 2 when your hands are occupied with a task. |
| Azure-powered | Stream high-fidelity 3D content that can be anchored to a location and/or object that persists across users with Azure mixed reality services.
| Untethered | Move freely, with no wires or external packs to get your way on the job. |
| Best with Microsoft Mesh | With its immersive mixed reality capabilities, connect and collaborate with others as if you are there in person. |
| Mixed Reality Capture | Document an experience as a photo or a video to share with others in real-time. |
| MEMS Display | Experience smooth movements, more-believable animations and quick response when you move your head. It’s all thanks to this industry-defining innovation which dramatically increases immersion while shrinking the size of the displays. | 
| Large Field of View | Enjoy a larger field of view in the HoloLens 2. With this expanded canvas and higher resolution than the original, you can read an 8-point font on a holographic website, have precise interactions with holograms and – ultimately – create and immerse yourself in Mixed Reality. |
| Computer Vision | Using Surface Reconstruction, different surfaces in the room are scanned by the depth cameras. Multiple passes of the scan are stitched together and merged over time (even as you walk through the room) to create a 3D mesh of the many planes in the room.
| Spatial Audio | Perceive sound all around you with audio that stimulates your mind into perceiving sound in 3D. Hear where the holograms are with HoloLens 2. |
| Holographic Processing Unit (HPU) | Experience AI inferencing on the edge for much faster response times. This low latency is due to the custom silicon invented for HoloLens 2. You’ll notice this speed for things like hand tracking. |


## Managing HoloLens 2 in your organization
HoloLens 2 includes features that make it easier for organizations to manage and use HoloLens devices. Some features are included with the device while others can be enabled by [Mobile Device Management (MDM) for HoloLens](hololens-mdm-configure.md)  or through [Provisioning Packages](hololens-provisioning.md) using [Windows Configuration Designer](app-deploy-provisioning-package.md#setup).

| I want to... | Solution | Description |  
|---------| ------------|------------|
Manage how my end users sign in | [**Identity**](hololens-identity.md) | HoloLens 2 supports several kinds of user identities - Azure Active Directory (AAD), Microsoft Account (MSA), and local accounts.  |
| Encrypt user data | [**Data security**](security-encryption-data-protection.md) | BitLocker data encryption is enabled on HoloLens 2 to provide the same level of security protection as any other Windows device. | 
Manage Hololens devices in my organization | [**Mobile Device Managment**](hololens-mdm-configure.md) | Manage settings, select apps to install and set security configurations tailored to your organization's need on multiple HoloLens 2 devices from a central location. | 
|Minimize setup time for new users and devices | [**Autopilot**](hololens2-autopilot.md) | Configure the out-of-box experience (OOBE) in Microsoft Endpoint Manager and enable end users to prepare devices for business use with little to no interaction. |  
| Control OS updates for my devices | [**Windows Update for Business**](hololens-updates.md#managing-updates-by-using-windows-update-for-business) | Windows Update for Business provides controlled operating system updates to devices and support for the long-term servicing channel. |  
| Allow specific and LOB apps to be downloaded |[**Application Management**](app-deploy-overview.md) | Choose how to distribute and control apps for selected groups of HoloLens 2 users. | 
| Show or hide specific apps on your start menu |[**Kiosk mode**](hololens-kiosk.md) | Configure HoloLens 2 to function as a fixed-purpose device for use in app demos or dedicated business apps. 
| Secure my environment by locking down apps | [**WDAC**](windows-defender-application-control-wdac.md) | Windows Defender Application Control (WDAC) blocks apps and processes from being launched by the device user.
| Manage device security with rules for apps and processes | [**Policies (CSPs)**](hololens-csp-policy-overview.md) | IT Admins can define and implement policy settings using an existing list of supported Policy CSPs on HoloLens 2. |  
| Manage how a device connects to the internet | [**Network and Connectivity**](hololens-certificates-network.md) | Use certificate-based authentication to access Wi-Fi, VPNs, or internal resources. | 
| Share the device with multiple users | [**Auto-Customized Display**](hololens-calibration.md#auto-eye-position-support) | HoloLens 2 displays are automatically adjusted with Auto Eye Position (AEP), eliminating the need to run a manual calibration process when the device is [shared between users](hololens-multiple-users.md). |

Learn about [Licensing Requirements](hololens-licenses-requirements.md) for the above solutions.

## Next Steps
> [!div class="nextstepaction"]
> [Explore HoloLens 2 options](hololens2-options.md)

> [!div class="nextstepaction"]
>[Planning HoloLens 2 deployment](hololens-requirements.md) 
