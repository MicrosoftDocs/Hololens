---
title: Overview of Corporate connected HoloLens 2 with Dynamics 365 Guides
description: Learn how to enroll HoloLens 2 devices over a corporate Connected network with Dynamics 365 Guides.
keywords: HoloLens, management, corporate connected, Dynamics 365 Guides, AAD, Azure AD, MDM, Mobile Device Management
author: joyjaz
ms.author: v-jjaswinski
ms.reviewer: aboeger
ms.date: 03/16/2021
ms.prod: hololens
ms.topic: article
ms.sitesec: library
ms.localizationpriority: medium
audience: HoloLens
manager: yannisle
appliesto:
- HoloLens 2
---

# CONFIGURE

## Azure Users and Groups

Azure, and Intune by that extension, uses users and groups to help assign configurations and licenses. For the sake of validating this deployment flow and being able to check that you can author and operate a guide you&#39;ll need a user account.

We can make a single user group specifically for assigning licenses.

If you don&#39;t already have access to two Azure AD accounts in a user group you can use; here are the quick start guides for:

- [How to create a user](https://docs.microsoft.com/mem/intune/fundamentals/quickstart-create-user)
- [How to create a group](https://docs.microsoft.com/mem/intune/fundamentals/quickstart-create-group)
- [Add users to a group](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-members-azure-portal) – Add created users to create group
- [Configure Azure AD to allow a User Group to join devices](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan#configure-your-device-settings) – Ensure new user group has permission to enroll devices to Azure AD

## Auto Enrollment on HoloLens 2

In order to have a smooth and seamless experience, setting up Azure Active Directory Join (AADJ) and Auto Enrollment to Intune for HoloLens 2 devices is the way to go. This allows users to input their organization log-in credentials during OOBE and automatically register with Azure AD and enroll the device into MDM.

By using [Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home), we can select services and navigate a few pages until we can select Get a Premium trial. You may notice there is Azure Active Directory Premium 1 and 2, for Automatic Enrollment P1 is sufficient. We can select Intune and select the user scope for automatic enrollment and select the group that was previously created.

For full details and steps read the guide on [how to enable auto enrollment for Intune](https://docs.microsoft.com/mem/intune/enrollment/quickstart-setup-auto-enrollment).

## Wi-Fi and Certificates and Wi-Fi sSet up

Certificate-based authentication is a common requirement for customers using HoloLens 2. You might require certificates to access Wi-Fi, to connect to VPN solutions, or for accessing internal resources in your organization. You will need to deploy such certificates by using a Simple Certificate Enrollment Protocol (SCEP) or Public Key Cryptography Standard (PKCS) certificate infrastructure that is integrated with your MDM solution. Using Wi-Fi certificates with Intune creates a seamless experience for end users. Wi-Fi certificates eliminate the need for a username and password and ensure a connection to the corporate Wi-Fi network(s) regardless of the user or HoloLens. Prerequisites for certificate use:

### Certificate requirements

[Root certificates](https://docs.microsoft.com/mem/intune/protect/certificates-trusted-root) are required to deploy certificates through a SCEP or PKCS infrastructure. Other applications and services in your organization might require root certificates to be deployed to your HoloLens 2 devices as well.A trusted root certificate – must be deployed before other certificates. This profile helps establish the trust from the device back to the CA and is required by the other certificate profiles.

[Certification Authority](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj125375(v=ws.11))

On-premises infrastructure

[PKCS](#_PKCS)

A trusted root certificate – must be deployed before other certificates. This profile helps establish the trust from the device back to the CA and is required by the other certificate profiles.

Once this infrastructure is in place, the Wi-Fi certificate(s) can be created and deployed.

### Wi-Fi connectivity requirements

Create a [profile](https://docs.microsoft.com/mem/intune/protect/certificates-profile-scep) for each SCEP Wi-Fi certificate. Each of these profiles must have a description that includes an expiration date in DD/MM/YYYY format. Certificate profiles without an expiration date will not be deployed.

1. [Assign](https://docs.microsoft.com/mem/intune/configuration/device-profile-assign) the device profiles to the HoloLens device group.
2. [Monitor](https://docs.microsoft.com/mem/intune/configuration/device-profile-monitor) the device profiles in Intune.

If there are issues with Wi-Fi profiles, reference [Troubleshoot Wi-Fi device configuration profiles in Intune](https://docs.microsoft.com/troubleshoot/mem/intune/troubleshoot-wi-fi-profiles).

## Proxy Set-up

Now is the time to create the Wi-Fi Proxy device configuration profile. This profile will be assigned to the previously created group and will enable proxy on the specific Wi-Fi connection(s). Currently, the recommended method is taking a working Wi-Fi profile and importing it into the HoloLens.

Reference these instructions to [Import Wi-Fi settings for Windows devices in Microsoft Intune.](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fmem%2Fintune%2Fconfiguration%2Fwi-fi-settings-import-windows-8-1&amp;data=04%7C01%7Cv-evmill%40microsoft.com%7Cf3111c90a57d4c9f791b08d8d39783f9%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637491994999180795%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&amp;sdata=Z4cxH4EJpToWVeaoz5RpP1YXyxFSSm1a5leboVpfwVc%3D&amp;reserved=0)

See More: [Create a Wi-Fi profile for devices in Microsoft Intune - Azure | Microsoft Docs](https://docs.microsoft.com/mem/intune/configuration/wi-fi-settings-configure)

### Troubleshooting Proxy via Firewall

When things try to not go through Proxy, they try to run through the firewall. You can add a list of endpoint specifics to your Firewall to troubleshoot this issue.

If you&#39;re blocked at firewall ports enable some common [endpoints](https://docs.microsoft.com/hololens/hololens-offline) for HoloLens.

You can also enable the Guides specific ports: [Internet accessible URLs required for connectivity to Microsoft Dynamics CRM Online](https://support.microsoft.com/help/2655102/internet-accessible-urls-required-for-connectivity-to-microsoft-dynami)

## App Deployment

Deploying a Line of Business (LOB) app via MDM is a method that&#39;s easily scalable and can be automatically deployed to your devices upon enrollment in a created group.

If you are still developing your Apps or don&#39;t have one yet, you can use a sample app of the MRTK examples hub. This sample app is ready to use, and won&#39;t require the use of either Unity or Visual Studio. [Download the MRTK Examples Sample app](https://aka.ms/HoloLensDocs-Sample-MRTK-Examples-App).

If you would prefer to use your own app or are interested in app development for Mixed Reality, then feel free to review our [Mixed Reality developer documentation](https://docs.microsoft.com/windows/mixed-reality/design/design).

**\&gt; [!NOTE]**
 \&gt; The System Requirements for HoloLens devices are based on the architecture of the app build. HoloLens 2 devices use ARM architecture. When building your apps in Visual Studio, ensure that you have selected the correct architecture for the device and include any needed dependencies.

**\&gt; [!IMPORTANT]**
 \&gt; When deploying LOB apps, it&#39;s important to also upload the certificate to Intune, and assign it to the same group that is intended to use the app or it will not install properly.

### Upload and Assign the App

1. Navigate to the [MEM admin center](https://endpoint.microsoft.com/#home).
2. Select **Apps** \&gt; **All apps** \&gt; and select the **+ Add** button.
3. Underneath Other, Select **Line-of-business app**. Click **select**.
4. Select the app package file, this is your APPXBUNDLE file, or in our case of this example the app is _MRTK Examples Hub\_2.4.2.0\_arm\_Master.appxbundle_.
5. You will be notified of missing dependencies. In this case we need to upload _Microsoft.VCLibs.ARM.14.00.appx_. Search for it under **Select a file.**
6. Select OK.
7. In the next screen, the required fields will be auto-filled. Select **Next.**
8. Under Required, add our previously created group to make this app required for the group. This will cause the app to automatically download to enrolled devices in the group. Select **Next.**
9. Select **Create.**

Read more: [Assign apps to groups in Microsoft Intune](https://docs.microsoft.com/mem/intune/apps/apps-deploy#assign-an-app)

// Ryan Nadel to review below.

## Setup Guides: Application licenses, dataverse, and authoring

In order to use Dynamics 365 Guides, you&#39;ll need to do some preparation. There are three areas in which we&#39;ll need to prepare; users, dataverse, and the guides themselves.

### Users and application licenses

For someone to use Guides, they&#39;ll need to use an Azure AD account, which we have set up in this guide previously.

You&#39;ll also need to assign the proper Application Licenses,Licenses; you&#39;ll do this from the [Microsoft 365 admin center](https://admin.microsoft.com/AdminPortal/Home). You&#39;ll want to ensure you assign the following 3 three application licenses to the user we&#39;ve created. Also assign these licenses to your primary Azure Account.

- Microsoft Dataverse
- Dynamics 365 Guides
- Power Apps for Guides

Follow [this short guide](https://docs.microsoft.com/dynamics365/mixed-reality/guides/setup-step-one#assign-the-dynamics-365-guides-license-to-user-accounts) with pictures for step-by-step instructions on applying application licenses.

### Set up the Dataverse

In order to [set up a production environment](https://docs.microsoft.com/dynamics365/mixed-reality/guides/setup-step-two#set-up-a-production-environment-for-purchased-licenses-only) you will need to meet two prerequisites. You must have the [**System Administrator**](https://docs.microsoft.com/power-platform/admin/database-security) role,  **and**  you must have a [**Power Apps license**](https://docs.microsoft.com/power-platform/admin/signup-question-and-answer) (or a license like a [**Dynamics 365 Guides license**](https://docs.microsoft.com/dynamics365/mixed-reality/guides/setup-step-one) that includes a Power Apps license). If following this guide you created the Azure AD, then you meet the role requirements for System Administrator. We also have assigned a Guides License in the previous step.

Within this guide to [create a Microsoft Dataverse environment](https://docs.microsoft.com/dynamics365/mixed-reality/guides/setup-step-two):

1. Start by using the [Power Platform admin center](https://admin.powerplatform.microsoft.com/environments) and creating a New Environment.
2. When creating the **New Environment**, for the **Type** you&#39;ll be selecting **Production**.
3. It is important that you toggle **Create a database for this environment?**  option to  **Yes**.
4. In the  **Add database**  dialog box set the  **Enable Dynamics 365 apps**  option to  **Yes.**

You&#39;ll want to increase the maximum file size of items in your dataverse. Increasing the max file size will allow you to upload larger 3D models or video files that you&#39;ll use later in your guides. Follow a short guide [to change the maximum upload file size.](https://docs.microsoft.com/dynamics365/mixed-reality/guides/setup-step-two#change-the-maximum-upload-file-size)

Lastly, you&#39;ll need to [install and configure the solution](https://docs.microsoft.com/dynamics365/mixed-reality/guides/setup-step-two#install-and-configure-the-solution). In the [Power Platform admin center](https://admin.powerplatform.microsoft.com/environments), select  **Resources**  \&gt;  **Dynamics 365 apps**, select  **Dynamics 365 Guides**  in the list, and then select  **Install**.

### Create a test Guide on your PC via Authoring

When creating Guides you will always start on your PC. Creating the steps, selecting models, and how to anchor the guide. This will be followed by placing content for your guide later in in authoring mode on your HoloLens device. For the purposes of this guide, we suggest making a short test guide with minimal steps and models.

If you&#39;d like to start learning about authoring for Guides, start here with the [authoring overview](https://docs.microsoft.com/dynamics365/mixed-reality/guides/authoring-overview). Or to get a fast track overview, watch this short video.

\&lt;iframe width=&quot;560&quot; height=&quot;315&quot; src=&quot;https://www. **youtube**.com/embed/EC24dMlAy90&quot; frameborder=&quot;0&quot; allow=&quot;accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture&quot; allowfullscreen\&gt;\&lt;/iframe\&gt;

![](RackMultipart20210312-4-5gvo1a_html_53cae776fa223b33.png)

// end necessary Ryan Nadel review. (Feel free to review more)

## Optional: Kiosk mode

Kiosk mode is a mode that let&#39;s an IT Admin configure the start menu&#39;s UI to show only a single app, or selection of apps. A kiosk can also be applied to specific users, groups, or at the device level; and in some cases, exclude certain users from the Kiosk still allowing them access to the regular start menu.

Kiosk mode has many different variables, both in scope and configurations that can be set as well as methods of deploying the Kiosk to the HoloLens. Because of all these variables, Kiosk mode is being left as _optional_ for this guide and won&#39;t be revisited. If you believe you have a business need to restrict available apps to users or would like to learn more, then feel free to learn how to [Set up HoloLens as a kiosk](https://docs.microsoft.com/hololens/hololens-kiosk).

## Optional: WDAC

WDAC allows an IT Admin to configure their devices to block the launch of apps on devices. This is different than methods of device restriction, such as Kiosk mode, where the user is presented with a UI that hides the apps on the device, but they can still be launched. While WDAC is implemented, the apps are still visible in the All Apps list, but WDAC stops those apps and processes from being able to be launched by the device user.

For more information, reference [Use WDAC and Windows PowerShell to allow or block apps on HoloLens 2 devices with Microsoft Intune](https://docs.microsoft.com/mem/intune/configuration/custom-profile-hololens).

[Windows Defender Application Control - WDAC | Microsoft Docs](https://docs.microsoft.com/hololens/windows-defender-application-control-wdac)

# Next step 
> [!div class="nextstepaction"]
> [Corporate connected deployment - Deploy](hololens2-corp-connected-deploy.md)