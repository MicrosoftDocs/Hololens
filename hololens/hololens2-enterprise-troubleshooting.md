---
title: HoloLens 2 implementation and managed device troubleshooting
description: Troubleshooting HoloLens 2 devices in an Enterprise environment
author: JoyJaz
ms.author: v-jjaswinski
ms.date: 6/22/2021
ms.topic: article
keywords: troubleshooting
ms.prod: hololens
ms.sitesec: library
ms.localizationpriority: high
ms.reviewer: 
appliesto:
- HoloLens 2
---
# Troubleshooting implementation and managed devices 

This article describes how to resolve several issues or answer questions regarding implementation and management of HoloLens 2.

>[!IMPORTANT]
> Before you start any troubleshooting procedure, make sure that your device is charged to **20 to 40 percent** of battery capacity, if possible. The [battery indicator lights](hololens2-setup.md#lights-that-indicate-the-battery-level) located under the power button are a quick way to verify the battery capacity without logging into the device.


<a id="list"></a>
- [EAP Troubleshooting](#eap-troubleshooting)
- [Wi-Fi Troubleshooting](#wi-fi-troubleshooting)
- [Can't sign in to a previously setup HoloLens device](#cant-sign-in-to-a-previously-setup-hololens-device)
- [Can't login after updating to Windows Holographic 21H1](#cant-login-after-updating-to-windows-holographic-21h1)
- [Autopilot Troubleshooting](#autopilot-troubleshooting)
- [Questions about managing HoloLens devices](#questions-about-managing-hololens-devices)

## EAP Troubleshooting
1. Double check Wi-Fi profile has right settings:
    - EAP type is configured correctly, common EAP types: EAP-TLS (13), EAP-TTLS (21) and PEAP (25).
    - Wi-Fi SSID name is right and matches with HEX string.
    - For EAP-TLS, TrustedRootCA contains the SHA-1 hash of server's trusted root CA certificate. On Windows PC "certutil.exe -dump cert_file_name" command will show a certificate's SHA-1 hash string.
2. Collect network packet capture on the Access Point or Controller or AAA server logs to find out where the EAP session fails.
    - If the EAP identity provided by HoloLens is not expected, check whether the identity has been correctly provisioned through Wi-Fi profile or client certificate.
    - If server rejects HoloLens client certificate, check whether the required client certificate has been provisioned on the device.
    - If HoloLens rejects server certificate, check if the server root CA certificate has been provisioned on HoloLens.
3. If the enterprise profile is provisioned through Wi-Fi provisioning package, consider applying the provisioning package on a Windows 10 PC. If it also fails on Windows 10 PC, follow the Windows client 802.1X authentication troubleshooting guide.
4. Send us feedback through Feedback Hub.

[Back to list](#list)

## Wi-Fi Troubleshooting

Here are some things to try if you can't connect your HoloLens to a Wi-Fi network:

1. Make sure that Wi-Fi is turned on. To check, use the Start gesture, then select Settings > Network & Internet > Wi-Fi. If Wi-Fi is on, try turning it off and then on again.
2. Move closer to the router or access point.
3. Restart your Wi-Fi router, then restart HoloLens. Try connecting again.
4. If none of these things work, check to make sure that your router is using the latest firmware. You can find this information on the manufacturer website.

When you sign into an enterprise or organizational account on the device, it may also apply Mobile Device Management (MDM) policy, if the policy is configured by your IT administrator.

[Back to list](#list)

## Can't sign in to a previously setup HoloLens device

If your device was previously set up for someone else, either for a client or for a former employee, and you don't have their password to unlock the device, you can use Intune to remotely [wipe](https://docs.microsoft.com/intune/remote-actions/devices-wipe) the device. The device then re-flashes itself.  
> [!IMPORTANT]
> When you wipe the device, make sure to leave **Retain enrollment state and user account** unchecked.
[Back to list](#list)

## Can't login after updating to Windows Holographic 21H1

### Symptoms
- Using PIN to logon will fail after entering the correct PIN.
- Using the web logon method will fail after successfully signing in on the web page.
- The device is not listed as “Azure AD joined” in [Azure portal](https://portal.azure.com/) -> Azure Active Directory -> Devices.

### Cause
The impacted device may have been deleted from the Azure AD tenant. For example, this may happen because:

- An administrator or user deleted the device in the Azure portal or using PowerShell.
- The device was removed from the Azure AD tenant due to inactivity. For an efficiently managed environment, we typically recommend IT admins to [remove stale, inactive devices from their Azure AD tenant](https://docs.microsoft.com/azure/active-directory/devices/manage-stale-devices).

When an impacted device attempts to contact the Azure AD tenant again after it has been deleted it will fail to authenticate with Azure AD. This effect is often invisible to the user of the device, as cached logon via PIN will continue to allow the user to logon.

### Mitigation
There is currently no way to add a deleted HoloLens device back into Azure AD. Affected devices will need to be clean-reflashed by following the instructions on [reflashing their device](hololens-recovery.md#clean-reflash-the-device).

## Autopilot Troubleshooting

The following articles may be a useful resource for you to learn more information and troubleshoot Autopilot Issues, however please be aware that these articles are based on Windows 10 Desktop and not all information may apply to HoloLens:

- [Windows Autopilot - known issues](https://docs.microsoft.com/mem/autopilot/known-issues)
- [Troubleshoot Windows device enrollment problems in Microsoft Intune](https://docs.microsoft.com/mem/intune/enrollment/troubleshoot-windows-enrollment-errors)
- [Windows Autopilot - Policy Conflicts](https://docs.microsoft.com/mem/autopilot/policy-conflicts)

## Managed HoloLens Devices FAQs

### Can I use System Center Configuration Manager (SCCM) to manage HoloLens devices?

No. You have to use an MDM system to manage HoloLens devices.

### Can I use Active Directory Domain Services (AD DS) to manage HoloLens user accounts?

No. You have to use Azure Active Directory (Azure AD) to manage user accounts for HoloLens devices.

### Is HoloLens capable of Automated Data Capture Systems (ADCS) auto-enrollment?

No.

### Can HoloLens participate in Integrated Windows Authentication?

No.

### Does HoloLens support branding?

No. However, you can work around this issue by using one of the following approaches:

- Create a custom app, and then [enable Kiosk mode](hololens-kiosk.md). The custom app can have branding, and can launch other apps (such as Remote Assist).  
- Change all of the user profile pictures in Azure AD to your company logo. However, this may not be desirable for all scenarios.

### What logging capabilities does HoloLens 2 offer?

Logging is limited to traces that can be captured in development or troubleshooting scenarios, or telemetry that the devices send to Microsoft servers.

## Questions about securing HoloLens devices

See [our HoloLens 2 security information](security-overview.md).
For HoloLens 1st Gen devices please review [this FAQ](hololens1-faq-security.md).

[Back to list](#list)