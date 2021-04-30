---
title: Set up HoloLens in a commercial environment
description: Learn more about deploying and managing HoloLens in enterprise environments, including infrastructure, azure active directory, and mobile device management.
ms.prod: hololens
ms.sitesec: library
ms.assetid: 88bf50aa-0bac-4142-afa4-20b37c013001
author: scooley
ms.author: scooley
ms.reviewer: aboeger
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
ms.date: 11/04/2020
appliesto:
- HoloLens 2
---

# HoloLens 2 enterprise deployment and management overview

This overview is intended to help IT professionals understand considerations for deploying and managing Microsoft HoloLens 2 devices within the enterprise.

HoloLens 2 runs on Windows 10 Holographic which provides organizations with robust, flexible, built-in mobile device and app management technologies. Windows 10 Holographic supports end-to-end device lifecycle management to give companies control over their devices, data, and apps. The HoloLens 2 can easily be incorporated into standard lifecycle practices, from device enrollment, configuration, and application management to maintenance and retirement using a comprehensive mobile device management solution.

The following steps can help guide you through the process of HoloLens 2 adoption within enterprise.

| <span title="Icon">&nbsp;</span> | <span title="Description">&nbsp;</span> |
|--|--|
| <br> :::image type="icon" source="images/one.png"::: | <br> [Prepare](#prepare): Review the prepare guide to become familiar with the tools and approaches you need to use. |
| <br> :::image type="icon" source="images/two.png"::: | <br> [Configure](#configure): Learn about configuration settings you can use to properly setup your environment. |
| <br> :::image type="icon" source="images/three.png"::: | <br> [Deploy](#deploy): Discover how to distribute and deploy your solution securely and efficiently. |
| <br> :::image type="icon" source="images/four.png"::: | <br> [Maintain](#maintain): Find out what's needed to properly maintain the state of your HoloLens 2 devices and ensure compliance with corporate policy. |

## Prepare

As you prepare to deploy HoloLens 2 to your corporate enterprise environment, there are several considerations that should be reviewed and understood as you begin to plan for scale deployments of HoloLens 2.

### Infrastructure Essentials

For HoloLens 2 in a corporate enterprise deployment scenario, there are certain essential infrastructure services required to support the full set of capabilities. HoloLens 2 was built with [Modern Mobile Device Management](https://www.microsoft.com/itshowcase/managing-windows-10-devices-with-microsoft-intune) in mind for deployment and management. With Azure AD Join + MDM as the primary means of achieving that in an ever-increasing mobile workforce. The below topics provide a brief overview of each infrastructure component that should be considered in your deployment planning for HoloLens 2.

### Azure Active Directory
Azure AD is a cloud-based directory service that provides identity and access management. You can integrate it with existing on-premises directories to create a hybrid identity solution. Organizations that use Microsoft Office 365 or Intune are already using Azure AD, which has three editions: Free, Premium P1, and Premium P2 (see [Azure Active Directory editions](https://azure.microsoft.com/documentation/articles/active-directory-editions/)). All editions support Azure AD device registration, but Premium P1 is required to enable MDM auto-enrollment. HoloLens 2 requires Azure Active Directory Join to enable most enterprise level features and functionality.

> [!NOTE]
> On premises Active Directory Join is not supported on HoloLens 2.

### Mobile Device Management
HoloLens 2 is designed specifically to be managed by Mobile Device Management (MDM) systems in an enterprise environment. Microsoft [Intune](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/microsoft-intune), part of the Enterprise Mobility + Security, is a cloud-based MDM system that manages devices in the enterprise. Like Office 365, Intune uses Azure AD for identity management, so employees use the same credentials to enroll devices in Intune that they use to sign into Office 365. Multiple MDM systems support Windows 10 and most support personal and corporate device deployment scenarios. MDM systems can also manage application deployments and updates for the HoloLens 2 as well. Other MDM providers that support HoloLens 2 currently include: AirWatch, MobileIron, and others. All MDM system vendors have equal access to Windows 10 device management configuration service providers (CSP)s, giving IT organizations the freedom to select whichever system best fits their management requirements, whether Microsoft Intune or a third-party MDM product.

> [!NOTE]
> Traditional on premises PC management systems like System Center Configuration Manager are not supported on HoloLens 2.

### Windows Update for Business
Microsoft designed Windows Update for Business to provide IT administrators with additional Windows Update-centric management capabilities, such as the ability to deploy updates to groups of devices and to define maintenance windows for installing updates. See the [HoloLens updates](https://docs.microsoft.com/hololens/hololens-updates) documentation for details on managing HoloLens 2 updates.

### Certificates
HoloLens 2 supports deployment of certificates through MDM if your environment requires certificates for Corp Wi-Fi network authentication or access to other resources. Some MDM infrastructure configurations may be required to enable certificate deployments to HoloLens 2. Read about how to [prepare certificates and network profiles for HoloLens 2](https://docs.microsoft.com/hololens/hololens-certificates-network). If you're using Intune, check out the [certification configuration](https://docs.microsoft.com/mem/intune/protect/certificates-configure) details.

## Configure

MDM administrators can define and implement policy settings on any corporate device enrolled in an MDM system. What configuration settings you use will differ based on the deployment scenario. In Windows 10, Configuration Service Providers (CSP)s are an interface to read, set, modify, or delete configuration settings on the device. These settings map to registry keys or files. For more information about Windows 10 device management CSPs for HoloLens 2, see the full list of [CSPs supported in HoloLens devices](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens).

HoloLens 2 also supports setting a limited set of CSP configurations through custom provisioning packages. Provisioning packages are typically leveraged for non-MDM managed devices and require to be manually applied to each device. See the [HoloLens provisioning](https://docs.microsoft.com/hololens/hololens-provisioning) documentation for details on building custom provisioning packages.

> [!NOTE]
> HoloLens 2 supports [Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot), providing an easy and simple process for managing your corporate Windows 10 device configurations.

### Identity Management

Employees can use only one account to initialize a device so it&#39;s imperative that your organization controls which account is enabled first. The account chosen will determine who controls the device and influence your management capabilities. HoloLens 2 supports 3 account types: Local User account, personal Microsoft Account, and Azure Active Directory Accounts. It is highly recommended to leverage Azure Active Directory for your enterprise identity management solution, as it will enable the full capabilities on your HoloLens 2 devices. Check out [HoloLens identity](https://docs.microsoft.com/hololens/hololens-identity) for more details on Identities for HoloLens 2.

### Network and Connectivity

As HoloLens 2 is a cloud first device, network access to online resources is required for full functionality and capabilities to be made available. If you are deploying HoloLens 2 devices with connectivity to your corporate intranet network, you may be required to update your proxy/firewall rules to allow access to HoloLens 2 cloud services. For more information, take a look at the list of [common endpoints for the HoloLens 2 operating system](https://docs.microsoft.com/hololens/hololens-offline). Access to additional endpoints may be required for applications or other cloud services to run on HoloLens 2 successfully.

Some common HoloLens 2 services requiring additional endpoint access are as follows:

- [Intune](https://docs.microsoft.com/mem/intune/fundamentals/intune-endpoints)
- [D365 Guides](https://support.microsoft.com/en-us/help/2655102/internet-accessible-urls-required-for-connectivity-to-microsoft-dynami)
- [D365 Remote Assist (O365 Teams Infrastructure)](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams)

### Certificate Deployment

If certificates are required for access to corporate Wi-Fi networks or other services within your organization, HoloLens 2 supports user and device certificate deployment through MDM. Note: Your MDM solution may require additional infrastructure configuration to deploy certificates to Windows 10 devices.

### Security Review

Most enterprise IT departments will require assessment and review of new devices being deployed to a corporate enterprise network. If your organization needs a security review of HoloLens 2, you can find more details to assist with [obtaining security approvals](https://docs.microsoft.com/hololens/security-overview).

### Common HoloLens 2 Device Settings

When deploying HoloLens 2 devices to a corporate enterprise environment, there are a number of common device configurations that may be considered when planning out your deployment of HoloLens 2. This list highlights configurations and settings that are found to be quite common, and does not comprise of a full list of available options:

| Device Setting | Brief description.                                                                              |
|----------------|-------------------------------------------------------------------------------------------------|
| [Hardware restrictions](hololens-requirements.md#hardware-restrictions)               | Hardware restrictions reduce connectivity and assist in data protection.                        |
| [Wi-Fi profiles](hololens-requirements.md#wi-fi-profiles)               | Configure Wi-Fi profiles without user intervention or interaction.                              |
| [Certificates](hololens-requirements.md#certificates-1)               | Provide account and/or Wi-Fi authentication, VPN encryption, and SSL encryption of web content. |
| [Proxy](hololens-requirements.md#proxy)              | Manage internal traffic.                                                                        |
|  [VPN](hololens-requirements.md#vpn)              | Control access to apps and resources on their company's intranet.                               |
| [Kiosk Mode](hololens-requirements.md#kiosk-mode) | Limits the applications that are presented to users via UI. |

#### Hardware restrictions

HoloLens 2 uses state-of-the-art technology that includes popular hardware features such as cameras, microphones, speakers, USB interfaces, Bluetooth interfaces, and Wi-Fi. You can use hardware restrictions to control the availability of these features.

The following lists the most commonly used MDM settings that HoloLens 2 supports to configure hardware restrictions. Some of these hardware restrictions provide connectivity and assist in data protection.

- [**Allow WiFi:**](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi#wifi-allowwifi) Whether users can enable and use the Wi-Fi radio on their devices
- [**Allow USB Connection:**](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity#connectivity-allowusbconnection) Whether the USB connection is enabled (doesn&#39;t affect USB charging)
- [**Allow Bluetooth:**](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity#connectivity-allowbluetooth) Whether users can enable and use the Bluetooth radio on their devices

Read more about other [common device restrictions.](https://docs.microsoft.com/hololens/hololens-common-device-restrictions)

#### Wi-Fi profiles

Most corporate Wi-Fi networks require certificates and other complex information to restrict and secure user access. This advanced Wi-Fi information is difficult for typical users to configure, but MDM systems can fully configure these Wi-Fi profiles without user intervention. You can create multiple Wi-Fi profiles in your MDM system.

For more details on Wi-Fi settings for Windows 10, see [Enterprise Profile WiFi settings](https://docs.microsoft.com/mem/intune/configuration/wi-fi-settings-windows#enterprise-profile).

#### Certificates

Certificates help improve security by providing account authentication, Wi-Fi authentication, VPN encryption, and SSL encryption of web content. Although administrators can manage certificates on devices manually through provisioning packages, it&#39;s a best practice to use your MDM system to manage those certificates throughout their entire lifecycle – from enrollment through renewal and revocation. Your MDM system can automatically deploy these certificates to the devices&#39; certificate stores after you enroll the device (as long as the MDM system supports the Simple Certificate Enrollment Protocol (SCEP) or Public Key Cryptography Standards #12 (PKCS#12)). MDM can also query and delete enrolled client certificates or trigger a new enrollment request before the current certificate is expired.

Read more about how to [prepare certificates and network profiles for HoloLens 2.](https://docs.microsoft.com/hololens/hololens-certificates-network)

#### Proxy

Most corporate intranet networks leverage a proxy to manage internal traffic. With HoloLens 2 you can configure a proxy server for ethernet and Wi-Fi connections. These settings do not apply to VPN connections.

For more details on proxy settings for Windows 10, see [NetworkProxy CSP](https://docs.microsoft.com/windows/client-management/mdm/networkproxy-csp).

#### VPN

Organizations often use a VPN to control access to apps and resources on their company&#39;s intranet. HoloLens 2 supports SSL VPN connections, which require a downloadable plugin from the Microsoft Store and are specific to the VPN vendor of your choice.

For more details about VPN profiles, see the [VPNv2 CSP](https://msdn.microsoft.com/library/windows/hardware/dn914776(v=vs.85).aspx)

#### Kiosk Mode

You can configure a HoloLens 2 device to function as a fixed-purpose device, also called a kiosk, by configuring the device to run in kiosk mode. Kiosk mode limits the applications (or users) that are available on the device. Kiosk mode is a convenient feature that you can use to dedicate a HoloLens 2 device to business apps, or to use the HoloLens 2 device in an app demo.

For more details about configuring a HoloLens 2 in Kiosk Mode, see [Setup HoloLens as a Kiosk](https://docs.microsoft.com/hololens/hololens-kiosk)

## Deploy

### MDM Device Enrollment

For enterprise deployments, it is recommended to [enroll devices](https://docs.microsoft.com/hololens/hololens-enroll-mdm) into MDM as corporate devices only with Azure AD join and automatic MDM enrollment (Azure AD+MDM). This requires Azure AD Premium and supports automatic enrollment to several MDM providers including Intune.

Learn more about the self-deploying enrollment method [Autopilot](https://docs.microsoft.com/hololens/hololens2-autopilot).

### Application Deployment

User productivity on mobile devices is often driven by apps.

Windows 10 makes it possible to develop apps that work seamlessly across multiple devices using the Universal Windows Platform (UWP) for Windows apps.

There are multiple ways to deploy applications to HoloLens 2 devices. Apps can be deployed directly through MDM, the Microsoft Store for Business, or sideloaded through a provisioning package. Check out the [app deployment](https://docs.microsoft.com/hololens/app-deploy-overview) documentation for more details.

> [!NOTE]
> HoloLens 2 supports running of UWP ARM64 apps only.

## Maintain

In enterprise IT environments, the need for security and cost control must be balanced against the desire to provide users with the latest technologies. Since cyberattacks have become an everyday occurrence, it is important to properly maintain the state of your Windows 10 devices. IT needs to control configuration settings, keeping them from drifting out of compliance, as well as enforce which devices can access internal applications. HoloLens 2 delivers the mobile operations management capabilities necessary to ensure that devices are in compliance with corporate policy.

### OS Servicing options

**A streamlined update process**

Microsoft has streamlined the Windows product engineering and release cycle so new features, experiences, and functionality demanded by the market can be delivered more quickly than ever before. Microsoft plans to deliver two Feature Updates per year (12-month period). **Feature Updates** establish a Current Branch or CB, and have an associated version.

Microsoft will also deliver and install updates for security and stability directly to HoloLens 2 devices. These **Quality Updates** , released under Microsoft control via Windows Update, are available monthly. HoloLens 2 consumes Feature Updates and Quality Updates as part of the same standard update process.

Enterprise customers can manage the update experience and process on HoloLens 2s using an MDM system. In most cases, policies to manage the update process will apply to both feature and quality updates. More details in [configuring MDM for HoloLens updates](https://docs.microsoft.com/hololens/hololens-updates).

### Managing Applications

IT administrators can control which apps are allowed to be installed on the HoloLens 2 and how they should be kept up-to-date.

HoloLens 2 supports [Windows Defender Application Control (WDAC)](https://docs.microsoft.com/hololens/windows-defender-application-control-wdac), which enables administrators to create, allow, or disallow lists of apps from the Microsoft Store. This capability extends to built-in apps, as well. The ability to allow or deny apps helps to ensure that people use their devices for their intended purposes. However, it is not always an easy approach to find a balance between what employees need or request and security concerns. Creating allow or disallow lists also requires keeping up with the changing app landscape in the Microsoft Store.

For more details, see [Application Control CSP](https://docs.microsoft.com/windows/client-management/mdm/applicationcontrol-csp).

### Retire

Device retirement is the last phase of the device lifecycle. It&#39;s important that devices being replaced with newer models are securely retired since you don&#39;t want any company data to remain on discarded devices that could compromise the confidentiality of your data. IT also needs a way to adequately support users who need to wipe devices that are lost or stolen.

HoloLens 2 supports 3 methods of wiping the device

**MDM Factory Wipe:** Resets the HoloLens 2 back to the factory image via administrator-initiated MDM command. Erases all stored data on the device.

**Device Reset from within Settings:** End users can manually reset the HoloLens 2 within the Settings app on the device. Erases all stored data on the device.

**Advanced Recovery Companion (ARC):** From a PC running the ARC tool, a user or admin can flash a HoloLens 2 connected to the PC via USB cable. Erases all stored data on the device.

> [!div class="nextstepaction"]
> [Common Deployment Scenarios](common-scenarios.md)
