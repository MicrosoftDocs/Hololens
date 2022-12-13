---
title: Best Practices for creating ‘Experiences’ with HoloLens 2
description: How to create an experience for your HoloLens 2 devices.
author: evmill
ms.author: millerevan
manager: lolab
ms.reviewer: channing.gardner
ms.prod: hololens
ms.sitesec: library
ms.topic: article
ms.date: 11/8/2022
audience: ITPro
appliesto:
- HoloLens 2

---

# Best Practices for creating ‘Experiences’ with HoloLens

## Introduction

Our customers and partners have created amazing experiences with HoloLens, and we see multiple fantastic applications and scenarios created in museums, aquariums, and attractions across the world. Our partners have multiple methods of deploying and maintaining these, and this guide focuses on the best practices for your application, your technical architecture, and your device management and provisioning.

By following the guidance below, you'll be able to ensure your experience is scalable, easy to manage, and ready for use with your experience partners, to give your customers a delightful time with your experiences.

## Areas of focus

During this guide, we'll focus on several key areas that will work together to form an overall solution.  

1. [Application Considerations](#application-considerations)
1. [Environment Considerations](#environment-considerations)
1. [Choosing the right Device Management options](#choosing-the-right-device-management-option)
1. [Policy configuration](#policy-configuration)
1. [“Out of Box” production line](#out-of-box-production-line)
1. [Troubleshooting and device reset](#troubleshooting)

We expect this guidance to be useful for small experiences of anywhere between 10-20 devices right up to larger deployments of 100+ devices.

## Application Considerations

Your experience will run within the context of a UWP application that will run on the HoloLens device. Development support is outside the context of this document, however there are a few elements that will be useful to consider during your development.  

### Single Self-Contained UWP Application

When deploying the application following our recommended methodology, we'll deploy a “Single App Kiosk”, which will automatically launch your application. Users will not have access to the HoloLens Operating System (OS) or Shell, which means that all activities that are used by your experience should be contained within this one application.

Your application should be able to reset back to a “Starting” state and continue operating in a “loop”. Any calibration or navigation features should be contained within your application, as the app will effectively control the device experience. This removes any worry that a guest can modify or damage the experience and enables rapid turnaround for your experience.

### Kick out to Settings

In any IT environment, there may be intermittent issues with networking, or a need to reset a malfunctioning application. In a single app kiosk, there's no way to kick out to a “Settings” screen to perform this minor troubleshooting.  

Your application should have a method to get out to an “Operator” menu (protected by a shared passcode or similar) which will launch the In-Box settings menu, to allow for functionality such as network configuration, Hologram map reset, or device reset). You can use the “Launch URI” capability to launch the device settings menu. Launch the Windows Settings app - UWP applications

## Environment Considerations

HoloLens seamlessly blends holographic assets into real world surroundings appending stable and accurate holograms by tracking users in a space. Proper tracking is at the center of how HoloLens places experiences in your environment. To maintain proper tracking performance and for optimum usage, there are some Environment considerations that need to be adhered to for HoloLens to operate as intended. Please see HoloLens environment considerations.

|     Consideration                                                                                                                                  |     Description                                                                                                                                                                                                                                                                                                                          |
|----------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     Lighting           (Average Luxmeter - 500 – 1000 lux)                                                                                         |     Lighting is used to track location and the usage   environment. It must not be too bright nor too dark. The recommendation is   lighting should be bright, even and comfortable for a human to see without   effort. See [Lighting](hololens-environment-considerations.md#lighting)                                                                                                    |
|     Types of Lighting                                                                                                                              |     Different types of light can influence tracking and   affect performance. Please see for more information. See [Types of Lighting](hololens-environment-considerations.md#types-of-lighting)                                                                                                                                                                                                     |
|     Items in a space                                                                                                                               |     HoloLens uses unique landmarks in your environment   known as features. To ensure optimal tracking make sure your surrounding is   feature rich, with posters, plants, unique objects etc., to aid tracking. See [Items in a space](hololens-environment-considerations.md#items-in-a-space)                                                                                                    |
|     Wormholes                                                                                                                                      |     Try to differentiate areas by making them   distinctive. Areas that look the same can cause wormholes, where the HoloLens   tracker thinks these areas are the same place. Use labels or other   distinguishing features in your commercial environment to differentiate and   help mitigate. See [Wormholes](hololens-environment-considerations.md#wormholes)                          |
|     Movement in a space                                                                                                                            |     Constantly moving, shifting and changing   environments (including areas with lots of people) are difficult for the   HoloLens to track. Try to provide a stable space clearly visible to the   device for better tracking. See [Movement in a space](hololens-environment-considerations.md#movement-in-a-space)                                                                                  |
|     Proximity of the user to   items in the space                                                                                                  |     HoloLens cameras can see no closer than 15 cm from   an object. See [Proximity of the user to items in the space](hololens-environment-considerations.md#proximity-of-the-user-to-items-in-the-space)                                                                                                                                                                                                                       |
|     Surfaces in the space                                                                                                                          |     Less shiny objects are easier to track against. See   [Surfaces in a space](hololens-environment-considerations.md#surfaces-in-a-space)                                                                                                                                                                                                                                                            |
|     Wi-Fi fingerprint   considerations                                                                                                             |     With Wi-Fi enabled, map data will be correlated   with a Wi-Fi fingerprint even when not connected to a router. Without Wi-Fi   info on the device, hologram and space recognition may be slower. Significant   change in Wi-Fi signal can make the device believe it is in another space.   See [Wi-Fi fingerprint considerations](hololens-environment-considerations.md#wi-fi-fingerprint-considerations)    |
|     Temperature and Regulatory Information       (Typical advised temperature   range - HoloLens 2 is designed for use between +10 C and +35 C)    |     HoloLens should be stored in an environment within   the accepted temperature range (either when in standby or off for an hr   before using the device). Please see the [HoloLens Regulatory Information](https://support.microsoft.com/topic/hololens-regulatory-information-b0a1780e-47be-864c-f804-095d2909c141) page for the temperature range and regulatory,   usage and safety information.                                               |
|     Environmental Compliance Disclosure                                                                                                            |     See details for HoloLens [Materials and substances](https://www.microsoft.com/legal/compliance/materials-substances) for Environmental compliance                                                                                                                                                                                                                                                       |
|     Battery Information                                                                                                                            |     2 - 3 hours battery usage time. USB-C battery packs   can be utilized to extend this time.                                                                                                                                                                                                                                           |

For experiences that are likely to last more than 5 to 10 minutes, it's recommended to launch eye calibration at the start of your experience.

## Choosing the right Device Management Option

Device management is a key consideration to deploying HoloLens at scale with ease. This can be achieved through the following options: Provisioning Package or Mobile Device Management with Microsoft Intune both have pros and cons to use but view these considerations below to make the correct decision for your environment.

### Provisioning Package

Follow the steps at Configure HoloLens by using a provisioning package (HoloLens).

|     Pros                                                                                                                                   |     Cons                                                                                                                                                                                |
|--------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     All   configurations can be placed in the same package including Wi-Fi, VPN, Kiosk   Mode, using Windows Configuration Designer        |     Some   familiarity with XML is desirable                                                                                                                                            |
|     Use   low code or GUI to configure settings.                                                                                           |     New   package must be generated for each update.                                                                                                                                    |
|     Ideal   for offline secure deployments, with limited to no internet access allowed                                                     |     If   you deploy certificates via MDM or certificate manager, the certificate must   be deployed to the local machine store to sign apps installed with a   provisioning package.    |
|     Apps   and certificates may be installed via the same provisioning package                                                             |                                                                                                                                                                                         |
|     Provisioning   packages can be stacked to meet specific needs should you want to change a   setting later                              |                                                                                                                                                                                         |

To configure HoloLens 2 by using a provisioning package please follow the steps at Configure HoloLens by using a provisioning package.  Download Windows Configuration Designer from the Microsoft Store to build the package

### Intune

Follow the steps at Using Microsoft’s Endpoint Manager Intune to manage HoloLens devices.
Use Windows Autopilot to simplify setting up HoloLens for scale by following the steps at Windows Autopilot for HoloLens 2.

|     Pros                                                                                                                                                                                                         |     Cons                                                                                                     |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|     Devices   can be grouped together, and configurations can be applied to groups of users   of devices                                                                                                         |     Intune   license is required. However, a shared Intune Device License would cover this   requirement.    |
|     Great   for scale deployments over 15 – 20 devices                                                                                                                                                           |     Requires   familiarity with Intune or other Modern Mobile Device Management services.                    |
|     Allows   implementation of configuration in a hands-off way. Configurations can be   built and pushed out to multiple devices as well as application updates   remotely.                                     |                                                                                                              |
|     Configuration   can be made using the Endpoint Manager portal through configuration profiles   in easy-to-use GUI. Additionally, OMA-URI offers flexibility to create   customized settings and profiles.    |                                                                                                              |
|     Allows   for tenant restrictions to prevent devices being stolen or reused in   unauthorized ways.                                                                                                           |                                                                                                              |

## Policy configuration

Policies are used to define the settings that govern the HoloLens devices. In this section we share the configurations that should be applied for the Experience solution. As discussed in previous sections, policies can be applied through 2 provisioning methods: Provisioning Package or using Microsoft Intune for Mobile Device Management.

### Single App Kiosk with Settings app AutoLaunch and Visitor Mode (Sample XML Policy)

For Provisioning packages, configurations can be shown in a hierarchical XML structure as shown below.

```xml
<AssignedAccessConfiguration
            xmlns="http://schemas.microsoft.com/AssignedAccess/2017/config"
            >
            <Profiles>
                <Profile Id="{8739C257-184F-45DD-8657-C235819172A3}">
                    <KioskModeApp AppUserModelId="BAEAEF15-9BAB-47FC-800B-ACECAD2AE94B_cw5n1h2txyewy!App" />
                </Profile>
            </Profiles>
            <Configs>
                <Config>
                    <SpecialGroup Name="Visitor"/>
                    <DefaultProfile Id="{8739C257-184F-45DD-8657-C235819172A3}"/>
                </Config>
            </Configs>
        </AssignedAccessConfiguration>
```

AUMID of the Settings App: **BAEAEF15-9BAB-47FC-800B-ACECAD2AE94B_cw5n1h2txyewy!App**

### Single App Kiosk with Microsoft Intune

Intune uses Kiosk templates or custom OMA-URI configurations, which can be remotely applied to HoloLens. For details see Steps in configuring Kiosk mode for HoloLens, and then follow the Microsoft Intune Single App Kiosk Template to set up a configuration profile.

### Visitor Auto Login

The Auto Logon to a visitor profile allows you to jump straight into the action without ever seeing the login screen. The device will be launched straight into the kiosk experience using the visitor profile. This is a required setting and can be managed using the custom policy OMA-URI.

| Setting      | Value                                                                   |
|--------------|-------------------------------------------------------------------------|
|     URI      |     ./Device/Vendor/MSFT/Policy/Config/MixedReality/VisitorAutoLogon    |
|     Type     |     Boolean                                                             |
|     Value    |     1 (0 – Disabled by default)                                         |

### Tenant Lockdown

The Tenant Lockdown CSP keeps devices on the organization's tenant by locking them to that tenant even through device reset or reflash. It enables HoloLens 2 to be tied to MDM enrollment using Autopilot only and can be managed using the custom policy OMA-URI below …

| Setting      | Value                                                    |
|--------------|----------------------------------------------------------|
|     URI      |     ./Vendor/MSFT/TenantLockdown/RequireNetworkInOOBE    |
|     Type     |     Boolean                                              |
|     Value    |     True                                                 |

### Limiting Settings options available

To limit the options available as part of our Settings, use the Page Settings Visibility CSP. This allows the admin to reduce the settings available to the user.

| Setting      | Value                                                                 |
|--------------|-----------------------------------------------------------------------|
|     URI      |     ./Device/Vendor/MSFT/Policy/Config/Settings/PageVisibilityList    |
|     Type     |     String                                                            |
|     Value    |     Showonly:network-wifi;holograms;reset;                            |

> [!NOTE]
> Given the value above… Wi-Fi, Holograms, Reset will be available in settings.

## Application Deployment

To deploy the application using Intune please see [Deploying applications using Intune and Company Portal](app-deploy-intune.md) for more information.

## Application Updates

For Application updates of the experience, please see [Add apps to Microsoft Intune](/mem/intune/apps/apps-add) for more information.  To update an Experience, upload a new app package file with the latest version of the application and deploy using Intune.

## Out of Box Production Line

### Preparation

It's advised that all devices are updated to the latest build using [Advanced Recovery Companion](https://www.microsoft.com/store/productId/9P74Z35SFRS8) (ARC) which can be downloaded from Microsoft Store.

#### Provisioning package

1. Make sure the provisioning package (.ppkg) is copied to the root of a USB drive, only packages at the root will be applied and if multiple packages are present these will be applied sequentially.
1. Plug in the USB drive with the provisioning package during the Out of Box Experience (OOBE)’s “first interactable moment” (i.e., the hummingbird screen for HoloLens 2).
1. When the device is ready to be provisioned, a prompt will automatically open with the provisioning page.
1. Wait for provisioning to be complete.
1. The specified experience above will then be automatically loaded.

For updates with a provisioning package, it's recommended to reflash the device using Advanced Recovery Companion (ARC) and apply a new provisioning package with your specific configurations for any updates.

#### Mobile Device Management – Microsoft Intune

1. Autopilot requires internet access and one of the following options must be used to establish internet access
    1. Connect the device with Ethernet using a USB-C to Ethernet adapter for wired internet connectivity and HoloLens 2 will complete the Autopilot experience automatically.

> [!NOTE]
> Wi-Fi network is also possible as part of the Out of Box Experience (OOBE) however more interaction is required to get Wi-Fi setup for your device.

2. The device will automatically start the Out of Box Experience, which shouldn't be interacted with once the internet connection is established. The device may restart during the OOBE but allow the process to finish before interacting with the device.
1. When the OOBE process is complete the device will automatically load into the visitor profile single app experience if set up as dictated above.

For updates using Mobile Device Management – Microsoft Intune, follow the steps set out in [Installing, updating or removing required apps](/mem/intune/apps/apps-add#installing-updating-or-removing-required-apps).

## Best practices for Charging and Re-use

For busy working environments there are some best practices to follow to ensure the HoloLens device is always ready and prepared for use. Here's a list of cleaning and charging information to ensure optimal use.
Best practices for Charging [HoloLens 2 Battery and Charging](hololens2-charging.md)
Best practices for HoloLens cleaning [HoloLens 2 cleaning FAQ](hololens2-maintenance.md)

## Troubleshooting

When challenges arise with the device, there are some steps to carry out to troubleshoot and get back to active usage. Please visit the troubleshooting documentation at [Restart, reset, or recover HoloLens 2](hololens-recovery.md) to cover the main routes to resolving issues with the device.

In many cases restarting, reset or recovering your device will be enough to resolve issues with the device hardware.

Additionally, it's important to report any issues, through the Feedback Hub app available on the HoloLens device. [Give us feedback](hololens-feedback.md)
