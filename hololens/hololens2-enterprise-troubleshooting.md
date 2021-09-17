---
title: HoloLens 2 implementation and managed device troubleshooting
description: Troubleshooting HoloLens 2 devices in an Enterprise environment
author: beehanson
ms.author: v-beehanson
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
# Troubleshooting implementation and managed devices 0

This article describes how to resolve several issues or answer questions regarding implementation and management of HoloLens 2.

>[!IMPORTANT]
> Before you start any troubleshooting procedure, make sure that your device is charged to **20 to 40 percent** of battery capacity, if possible. The [battery indicator lights](hololens2-setup.md#lights-that-indicate-the-battery-level) located under the power button are a quick way to verify the battery capacity without logging into the device.


<a id="list"></a>
- [EAP Troubleshooting](#eap-troubleshooting)
- [Wi-Fi Troubleshooting](#wi-fi-troubleshooting)
- [Network Troubleshooting](#network-troubleshooting)
- [Can't sign in to a previously setup HoloLens device](#cant-sign-in-to-a-previously-setup-hololens-device)
- [Can't login after updating to Windows Holographic 21H1](#cant-login-after-updating-to-windows-holographic-21h1)
- [Autopilot Troubleshooting](#autopilot-troubleshooting)
- [Managed HoloLens Devices FAQs](#managed-hololens-devices-faqs)

## EAP Troubleshooting
1. Verify that the Wi-Fi profile has right settings:
    - Configure the EAP type correctly. Common EAP types are EAP-TLS (13), EAP-TTLS (21) and PEAP (25).
    - Check the Wi-Fi SSID name, and see that it matches the HEX string.
    - Make sure that for EAP-TLS, TrustedRootCA contains the SHA-1 hash of server's trusted root CA certificate. On Windows PC "certutil.exe -dump cert_file_name", the command will show a certificate's SHA-1 hash string.
2. Collect network packet capture on the Access Point or Controller or AAA server logs to find out where the EAP session fails.
    - If the EAP identity provided by HoloLens is unexpected, check whether the identity has been correctly provisioned through Wi-Fi profile or client certificate.
    - If the server rejects the HoloLens client certificate, check whether the required client certificate has been provisioned on the device.
    - If HoloLens rejects the server certificate, check if the server root CA certificate has been provisioned on HoloLens.
3. If the enterprise profile is provisioned through Wi-Fi provisioning package, consider applying the provisioning package on a Windows 10 PC. If it also fails on Windows 10 PC, follow the Windows client 802.1X authentication troubleshooting guide.
4. Send us feedback through Feedback Hub.

[Back to list](#list)

## Wi-Fi Troubleshooting

Here are some things to try if you can't connect your HoloLens to a Wi-Fi network:

1. Make sure Wi-Fi is turned on. Verify by using the Start gesture, then select Settings > Network & Internet > Wi-Fi. If Wi-Fi is on, try turning it off and on again.
2. Move closer to the router or access point.
3. Restart the Wi-Fi router, then restart HoloLens. Try connecting again.
4. If none of these things work, verify that your router is using the latest firmware. You can find this information on the manufacturer's website.

When you sign into an enterprise or organizational account on the device, it might also apply Mobile Device Management (MDM) policy, if the policy is configured by your IT administrator.

[Back to list](#list)

## Network Troubleshooting
If network issues are an obstacle to successfully deploying and using HoloLens 2 in your organization, configure Fiddler and/or Wireshark to capture and analyze HTTP/HTTPS traffic. 

### Configure Fiddler to capture HTTP traffic
Fiddler is a web debugging proxy and is used to troubleshoot HTTP(S) issues. It captures every HTTP request the computer makes and records everything associated with it. Uncovering end-user authentication issues for your HTTPS apps drives better productivity and efficiency for your target HoloLens 2 use cases. 

#### Prerequisites
 
- HoloLens 2 devices and your PC must be on the same network
- Note the IP address of your PC

#### Install and Configure Fiddler

1. On your PC - [install](https://docs.telerik.com/fiddler-everywhere/get-started/installation-procedure) and start Fiddler.  
1. On your PC - configure Fiddler to allow remote computers to connect.
    1. Go to Fiddler Settings -> Connections.
    1. Note the listening port for Fiddler (default is 8866).
    1. Check Allow remote computers to connect.
    1. Click Save.
3. On your HoloLens 2 – configure Fiddler as the proxy server<sup>1</sup>:
    1. Open the Start menu and select Settings.
    1. Select Network & Internet and then Proxy on the left menu.
    1. Scroll down to Manual proxy setup and toggle Use a proxy server to On.
    1. Enter the IP address of the PC where Fiddler is installed.
    1. Enter the port number noted above (default is 8866).
    1. Click Save.

<sup>1</sup> For builds 20279.1006+ (Insiders and the upcoming release), use the following steps to configure proxy:
1. Open the Start menu and go to your Wi-Fi Network’s Properties page. 
1. Scroll down to Proxy.
1. Change to Manual Setup.
1. Enter the IP address of the PC where Fiddler is installed.
1. Enter the port number noted above (default is 8866).
1. Click Apply.
    
#### Decrypt HTTPS traffic from HoloLens 2

1. On your PC – export the Fiddler certificate.
    1. Go to Fiddler Settings -> HTTPS and expand Advanced Settings.
    2. Click Export Fiddler certificate. It will save to your desktop.
    3. Move the certificate over to the Downloads folder on your HoloLens 2.

2.	On your HoloLens 2 - import the Fiddler certificate.
    1. Go to Settings -> Update and Security -> Certificates.
    2. Click Install Certificate, browse to the Downloads folder and select the Fiddler certificate.
    3. Change Store Location to Local Machine.
    4. Change Certificate Store to root.
    5. Select Install.
    6. Confirm the certificate is showing in the list of certificates. If not, repeat these steps.

#### Inspect HTTP(S) sessions

On your PC, Fiddler will show the HoloLens 2’s live HTTP(S) sessions. The Inspectors panel in Fiddler can show HTTP(S) request/response in different views. For example, the “Raw” view shows the raw request or response in plain text. 

### Configure Wireshark to capture network traffic
Wireshark is a network protocol analyzer that is used to inspect TCP/UDP traffic to and from your HoloLens 2 devices. This makes it easy to identify the traffic that is crossing the network to your HoloLens 2 -- how much there is, its frequency, how much latency there is between certain hops, and so forth.

#### Prerequisites:
- PC must have internet access and support Internet sharing over Wi-Fi.

#### Install and Configure Wireshark
1. On your PC - install [Wireshark](https://www.wireshark.org/#download).
1. On your PC - enable Mobile hotspot to share your Internet connection from Wi-Fi.
1. On your PC - start Wireshark and capture traffic from the Mobile hotspot interface. 
1. On your HoloLens 2 – change its Wi-Fi network to the PC’s Mobile hotspot. HoloLens 2 IP traffic will show up in Wireshark.

#### Analyze Wireshark logs
Wireshark filters can help filtering out the packets of interests. 

Check out the original [blog](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/diagnose-hololens-2-network-issues-with-fiddler-and-wireshark/ba-p/2322458).

[Back to list](#list)

## Can't sign in to a previously setup HoloLens device

If your device was previously set up for someone else, either for a client or for a former employee, and you don't have their password to unlock the device, you can use Intune to remotely [wipe](/intune/remote-actions/devices-wipe) the device. The device then re-flashes itself.  
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
- The device was removed from the Azure AD tenant due to inactivity. For an efficiently managed environment, we typically recommend IT admins to [remove stale, inactive devices from their Azure AD tenant](/azure/active-directory/devices/manage-stale-devices).

When an impacted device attempts to contact the Azure AD tenant again after it has been deleted, it will fail to authenticate with Azure AD. This effect is often invisible to the user of the device, as cached logon via PIN will continue to allow the user to logon.

### Mitigation
There is currently no way to add a deleted HoloLens device back into Azure AD. Affected devices will need to be clean-reflashed by following the instructions on [reflashing their device](hololens-recovery.md#clean-reflash-the-device).

[Back to list](#list)

## Autopilot Troubleshooting

The following articles may be a useful resource for you to learn more information and troubleshoot Autopilot Issues. However, the articles are based on Windows 10 Desktop, and not all information may apply to HoloLens:

- [Windows Autopilot - known issues](/mem/autopilot/known-issues)
- [Troubleshoot Windows device enrollment problems in Microsoft Intune](/mem/intune/enrollment/troubleshoot-windows-enrollment-errors)
- [Windows Autopilot - Policy Conflicts](/mem/autopilot/policy-conflicts)

[Back to list](#list)

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

No. But you can work around this issue by using one of the following approaches:

- Create a custom app, then [enable Kiosk mode](hololens-kiosk.md). The custom app can have branding, and can launch other apps (such as Remote Assist).  
- Change all of the user profile pictures in Azure AD to your company logo. However, this may not be desirable for all scenarios.

### What logging capabilities does HoloLens 2 offer?

Logging is limited to traces that can be captured in development or troubleshooting scenarios, or telemetry that the devices send to Microsoft servers.

## Questions about securing HoloLens devices

See [our HoloLens 2 security information](security-overview.md).
For HoloLens 1st Gen devices please review [this FAQ](hololens1-faq-security.yml).

[Back to list](#list)
