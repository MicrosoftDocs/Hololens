---
title: Enroll HoloLens in MDM
description: Enroll HoloLens in mobile device management (MDM) for easier management of multiple devices.
ms.prod: hololens
ms.sitesec: library
ms.assetid: 2a9b3fca-8370-44ec-8b57-fb98b8d317b0
author: scooley
ms.author: scooley
ms.topic: article
ms.localizationpriority: medium
ms.date: 10/06/2019
ms.reviewer: 
manager: laurawi
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Enroll HoloLens in MDM

You can manage multiple Microsoft HoloLens devices simultaneously using solutions like [Microsoft Intune](https://docs.microsoft.com/intune/windows-holographic-for-business). You will be able to manage settings, select apps to install and set security configurations tailored to your organization's need. See [Manage devices running Windows Holographic with Microsoft Intune](https://docs.microsoft.com/intune/windows-holographic-for-business), the [configuration service providers (CSPs) that are supported in Windows Holographic](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference#hololens), and the [policies supported by Windows Holographic for Business](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#hololenspolicies).

> [!NOTE]
> Mobile device management (MDM), including the VPN, Bitlocker, and kiosk mode features, is only available when you [upgrade to Windows Holographic for Business](hololens1-upgrade-enterprise.md).

## Requirements

 Your organization will need to have Mobile Device Management (MDM) set up in order to manage HoloLens devices. Your MDM provider can be Microsoft Intune or a 3rd party provider that uses Microsoft MDM APIs.
 
## Different ways to enroll

Depending on the type of identity chosen either during OOBE or post sign-in there are different methods of enrollment. To learn more about each type of Identity on HoloLens please visit [this page](hololens-identity.md).

- If Identity is AAD, then either during OOBE or **Settings App** -> **Access Work or School** -> **Connect** button.
    - For AAD, automatic MDM enrollment only occurs if AAD has been configured with enrollment URLs.
- If Identity is AAD and device has been pre-registered with Intune MDM server with specific configuration profile assigned to it, then AAD-Join and enrollment will automatically occur during OOBE.
    - Also called [Autopilot flow](hololens2-autopilot.md) Available in [19041.1103+ builds](hololens-release-notes.md#windows-holographic-version-2004).
- If Identity is MSA, then using **Settings App** -> **Access Work or School** -> **Connect** button.
    - Also called Add Work Account (AWA) flow.
- If Identity is Local User, then using **Settings App** -> **Access Work or School** -> **Enroll only in device management** link.
    - Also called pure MDM enrollment flow.

Once the device is enrolled with your MDM server, the Settings app will now reflect that the device is enrolled in device management.

## Auto-enrollment in MDM

If your organization uses Azure Active Directory (Azure AD) and an MDM solution that accepts an AAD token for authentication (currently, only supported in Microsoft Intune and AirWatch), your IT admin can configure Azure AD to automatically allow MDM enrollment after the user signs in with their Azure AD account. [Learn how to configure Azure AD enrollment.](https://docs.microsoft.com/mem/intune/enrollment/windows-enroll#enable-windows-10-automatic-enrollment)

When auto-enrollment is enabled, no additional manual enrollment is needed. When the user signs in with an Azure AD account, the device is enrolled in MDM after completing the first-run experience.

When a device is AAD Joined it may affect who considered the [device owner](security-adminless-os.md#device-owner).

## Unenroll HoloLens from Intune

To learn more about unenrolling a device visit [this page](https://docs.microsoft.com/windows/client-management/mdm/disconnecting-from-mdm-unenrollment). 
