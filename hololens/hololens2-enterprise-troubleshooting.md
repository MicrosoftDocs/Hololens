---
title: HoloLens 2 Implementation Troubleshooting
description: Troubleshooting HoloLens 2 devices in an Enterprise environment
author: JoyJaz
ms.author: v-jjaswinski
ms.date: 5/11/2021
ms.topic: article
keywords: troubleshooting
ms.prod: hololens
ms.sitesec: library
ms.localizationpriority: high
ms.reviewer: 
appliesto:
- HoloLens 2
---

# Implementation Troubleshooting

## Networking and Wi-Fi
### EAP Troubleshooting
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

### Troubleshooting your connection to Wi-Fi

Here are some things to try if you can't connect your HoloLens to a Wi-Fi network:

1. Make sure that Wi-Fi is turned on. To check, use the Start gesture, then select Settings > Network & Internet > Wi-Fi. If Wi-Fi is on, try turning it off and then on again.
2. Move closer to the router or access point.
3. Restart your Wi-Fi router, then restart HoloLens. Try connecting again.
4. If none of these things work, check to make sure that your router is using the latest firmware. You can find this information on the manufacturer website.

When you sign into an enterprise or organizational account on the device, it may also apply Mobile Device Management (MDM) policy, if the policy is configured by your IT administrator.

## Enterprise Device Management

### Certain devices joined in Azure AD may be unable to logon users after updating to 21H1

#### Symptoms
- Using PIN to logon will fail after entering the correct PIN.
- Using the web logon method will fail after successfully signing in on the web page.
- The device is not listed as “Azure AD joined” in [Azure portal](https://portal.azure.com/) -> Azure Active Directory -> Devices.

#### Cause
The impacted device may have been deleted from the Azure AD tenant. For example, this may happen because:

- An administrator or user deleted the device in the Azure portal or using PowerShell.
- The device was removed from the Azure AD tenant due to inactivity. For an efficiently managed environment, we typically recommend IT admins to [remove stale, inactive devices from their Azure AD tenant](https://docs.microsoft.com/azure/active-directory/devices/manage-stale-devices).

When an impacted device attempts to contact the Azure AD tenant again after it has been deleted it will fail to authenticate with Azure AD. This effect is often invisible to the user of the device, as cached logon via PIN will continue to allow the user to logon.

#### Mitigation
There is currently no way to add a deleted HoloLens device back into Azure AD. Affected devices will need to be clean-reflashed by following the instructions on [reflashing their device](https://docs.microsoft.com/hololens/hololens-recovery#clean-reflash-the-device).