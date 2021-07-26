---
title: HoloLens kiosk reference information
description: Information and samples for kiosks on HoloLens devices. 
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: v-evmill
ms.topic: article
ms.localizationpriority: medium
ms.date: 8/1/2021
ms.reviewer: 
manager: yannisle
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# HoloLens Kiosk reference information

This page contains helpful information for setting up your HoloLens device's kiosk mode. This includes AUMIDs for inbox apps and locating yours, and several XML samples for Kiosk mode, that are just a few edits away from being ready to use for several different senarios. For information on setting up a Kiosk, read the [set up a Kiosk page.](hololens-kiosk.md)

## HoloLens AUMIDs

For general information about how to choose kiosk apps, see [Guidelines for choosing an app for assigned access (kiosk mode)](/windows/configuration/guidelines-for-assigned-access-app).

If you use the Windows Device Portal to configure a single-app kiosk, you select the app during the setup process.  

If you use a Mobile Device Management (MDM) system or a provisioning package to configure kiosk mode, you use the [AssignedAccess Configuration Service Provider (CSP)](/windows/client-management/mdm/assignedaccess-csp) to specify applications. The CSP uses [Application User Model IDs (AUMIDs)](/windows/configuration/find-the-application-user-model-id-of-an-installed-app) to identify applications. The following table lists the AUMIDs of some in-box applications that you can use in a multi-app kiosk.

> [!IMPORTANT]
> Kiosk mode determines which apps are available when a user signs in to the device. However, kiosk mode is not a security method. It does not stop an "allowed" app from opening another app that is not allowed. Because we do not restrict this behavior, apps can still be launched from Edge, File explorer, and the Microsoft Store apps. If there are specific apps you don't want launched from a Kiosk, use [Windows Defender Application Control (WDAC) CSP](/windows/client-management/mdm/applicationcontrol-csp) to create appropriate policies.
>
> In addition, the Mixed Reality Home is not able to be set as a kiosk app.

<a id="aumids"></a>

|App Name |AUMID |
| --- | --- |
|3D Viewer |Microsoft.Microsoft3DViewer\_8wekyb3d8bbwe\!Microsoft.Microsoft3DViewer |
|Calendar |microsoft.windowscommunicationsapps\_8wekyb3d8bbwe\!microsoft.windowslive.calendar |
|Camera<sup>1, 2</sup> |HoloCamera\_cw5n1h2txyewy\!HoloCamera |
|Cortana<sup>3</sup> |Microsoft.549981C3F5F10\_8wekyb3d8bbwe\!App |
|Device Picker on HoloLens (1st gen) |HoloDevicesFlow\_cw5n1h2txyewy\!HoloDevicesFlow |
|Device Picker on HoloLens 2 |Microsoft.Windows.DevicesFlowHost\_cw5n1h2txyewy\!Microsoft.Windows.DevicesFlowHost |
|Dynamics 365 Guides |Microsoft.Dynamics365.Guides\_8wekyb3d8bbwe\!MicrosoftGuides |
|Dynamics 365 Remote Assist |Microsoft.MicrosoftRemoteAssist\_8wekyb3d8bbwe\!Microsoft.RemoteAssist |
|Feedback&nbsp;Hub |Microsoft.WindowsFeedbackHub\_8wekyb3d8bbwe\!App |
|File Explorer |c5e2524a-ea46-4f67-841f-6a9465d9d515_cw5n1h2txyewy!App |
|Mail |microsoft.windowscommunicationsapps_8wekyb3d8bbwe!microsoft.windowslive.mail |
|Old Microsoft Edge |Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge |
|New Microsoft Edge |Microsoft.MicrosoftEdge.Stable_8wekyb3d8bbwe!MSEDGE |
|Microsoft Store |Microsoft.WindowsStore_8wekyb3d8bbwe!App |
|Miracast<sup>4</sup> | &nbsp; |
|Movies & TV |Microsoft.ZuneVideo\_8wekyb3d8bbwe\!Microsoft.ZuneVideo |
|OneDrive |microsoft.microsoftskydrive\_8wekyb3d8bbwe\!App |
|Photos |Microsoft.Windows.Photos\_8wekyb3d8bbwe\!App |
|Old Settings |HolographicSystemSettings_cw5n1h2txyewy!App |
|New Settings |BAEAEF15-9BAB-47FC-800B-ACECAD2AE94B_cw5n1h2txyewy!App |
|Tips |Microsoft.HoloLensTips\_8wekyb3d8bbwe\!HoloLensTips |

> <sup>1</sup> To enable photo or video capture, you have to enable the Camera app as a kiosk app.  
> <sup>2</sup> When you enable the Camera app, be aware of the following conditions:
> - The Quick Actions menu includes the Photo and Video buttons.
> - You should also enable an app (such as Photos, Mail, or OneDrive) that can interact with or retrieve pictures.  
>  
> <sup>3</sup> Even if you do not enable Cortana as a kiosk app, built-in voice commands are enabled. However, commands that are related to disabled features have no effect.  
> <sup>4</sup> You cannot enable Miracast directly. To enable Miracast as a kiosk app enable the Camera app and the Device Picker app.

## Kiosk XML Code Samples

1. [Multiple app global assigned access profile](#multiple-app-global-assigned-access-profile)
1. [Multiple app global assigned access profile excluding device owners](#multiple-app-global-assigned-access-profile-excluding-device-owners)
1. [Multiple app assigned access profile for a local account or AAD user account](#multiple-app-assigned-access-profile-for-a-local-account-or-aad-user-account)
1. [Multiple app assigned access profiles for 2 AAD users or more](#multiple-app-assigned-access-profiles-for-2-aad-users-or-more)
1. 
1. [Multi app kiosk mode targeting an Azure AD group](#multi-app-kiosk-mode-targeting-an-azure-ad-group)
1. [Multiple app kiosk mode targeting Azure AD account](#multiple-app-kiosk-mode-targeting-azure-ad-account)

> [!NOTE]
> Replace TODO actions as per your requirements.



### Multiple app global assigned access profile
```xml
<?xml version="1.0" encoding="utf-8" ?> 
<AssignedAccessConfiguration 
    xmlns="http://schemas.microsoft.com/AssignedAccess/2017/config" 
    xmlns:v2="http://schemas.microsoft.com/AssignedAccess/201810/config" 
    xmlns:v3="http://schemas.microsoft.com/AssignedAccess/2020/config" 
    xmlns:rs5="http://schemas.microsoft.com/AssignedAccess/201810/config" 
> 
    <Profiles> 
         <!—Profile Id can be any unique GUID -->
        <Profile Id="{8739C257-184F-45DD-8657-C235819172A3}"> 
            <AllAppsList> 
                <AllowedApps>                     
                    	<!--TODO: Add AUMIDs of apps you want to be shown here, e.g. 
<App AppUserModelId="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge" rs5:AutoLaunch="true" /> 
--> 
                 </AllowedApps> 
            </AllAppsList> 
            <StartLayout> 
                <![CDATA[<LayoutModificationTemplate xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout" xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout" Version="1" xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification"> 
                      <LayoutOptions StartTileGroupCellWidth="6" /> 
                      <DefaultLayoutOverride> 
                        <StartLayoutCollection> 
                          <defaultlayout:StartLayout GroupCellWidth="6"> 
                            <start:Group Name="Life at a glance"> 
                              <!--This AUMID can be of any app and is not used on Hololens but is required for parity, so you can leave it as is. --> 
                              <start:Tile Size="2x2" Column="0" Row="0" AppUserModelID="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge" />                               
                            </start:Group> 
                          </defaultlayout:StartLayout> 
                        </StartLayoutCollection> 
                      </DefaultLayoutOverride> 
                    </LayoutModificationTemplate> 
                ]]> 
            </StartLayout> 
            <Taskbar ShowTaskbar="true"/> 
        </Profile> 
    </Profiles> 
    <Configs>
        <v3:GlobalProfile Id="{8739C257-184F-45DD-8657-C235819172A3}"/> 
    </Configs> 
</AssignedAccessConfiguration>
```




### Multiple app global assigned access profile excluding device owners

```xml
<?xml version="1.0" encoding="utf-8" ?> 
<AssignedAccessConfiguration 
    xmlns="http://schemas.microsoft.com/AssignedAccess/2017/config" 
    xmlns:v2="http://schemas.microsoft.com/AssignedAccess/201810/config" 
    xmlns:v3="http://schemas.microsoft.com/AssignedAccess/2020/config" 
    xmlns:v5="http://schemas.microsoft.com/AssignedAccess/202010/config" 
> 
    <Profiles>
         <!—Profile Id can be any unique GUID -->
        <Profile Id="{8739C257-184F-45DD-8657-C235819172A3}"> 
            <AllAppsList> 
                <AllowedApps>                     
                    	<!--TODO: Add AUMIDs of apps you want to be shown here, e.g. 
<App AppUserModelId="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge" rs5:AutoLaunch="true" /> 
--> 
                 </AllowedApps> 
            </AllAppsList> 
            <StartLayout> 
                <![CDATA[<LayoutModificationTemplate xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout" xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout" Version="1" xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification"> 
                      <LayoutOptions StartTileGroupCellWidth="6" /> 
                      <DefaultLayoutOverride> 
                        <StartLayoutCollection> 
                          <defaultlayout:StartLayout GroupCellWidth="6"> 
                            <start:Group Name="Life at a glance"> 
                              <!--This AUMID can be of any app and is not used on Hololens but is required for parity, so you can leave it as is. --> 
                              <start:Tile Size="2x2" Column="0" Row="0" AppUserModelID="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge" />                               
                            </start:Group> 
                          </defaultlayout:StartLayout> 
                        </StartLayoutCollection> 
                      </DefaultLayoutOverride> 
                    </LayoutModificationTemplate> 
                ]]> 
            </StartLayout> 
            <Taskbar ShowTaskbar="true"/> 
        </Profile> 
    </Profiles> 
    <Configs> 
        <v3:GlobalProfile Id="{8739C257-184F-45DD-8657-C235819172A3}"> 
            <v5:Exclusions> 
                <v5:SpecialGroup Name="DeviceOwner" /> 
            </v5:Exclusions> 
        </v3:GlobalProfile> 
    </Configs> 
</AssignedAccessConfiguration>
```

### Multiple app assigned access profile for a local account or AAD user account

:::code language="xml" source="samples/kiosk-sample-multi-app-local-or-aad-user.xml" highlight="24,26":::

### Multiple app assigned access profiles for 2 AAD users or more

:::code language="xml" source="samples/kiosk-sample-multi-app-two-aad-users-or-more.xml" highlight="36,41":::

### Multi app kiosk mode targeting an Azure AD group

This kiosk deploys a Kiosk that for users in the Azure AD group, they will have a Kiosk enabled that includes the three apps: Settings, Remote Assist, and Feedback Hub. To modify this sample to be used immediately, make sure to change the GUID highlighted below to match an Azure AD Group of your own.

:::code language="xml" source="samples/kiosk-sample-multi-aad-group.xml" highlight="20":::

### Multiple app kiosk mode targeting Azure AD account

This kiosk deploys a Kiosk for a single user, they will have a Kiosk enabled that includes the three apps: Settings, Remote Assist, and Feedback Hub. To modify this sample to be used immediately, make sure to change the account highlighted below to match an Azure AD Account of your own.

:::code language="xml" source="samples/kiosk-sample-multi-aad-account.xml" highlight="20":::
















## Updates to Kiosk

### Global Assigned Access – Kiosk Mode

- Reduced Identity management for Kiosk, by enabling new Kiosk method that applies Kiosk mode at the system level.

This new feature allows an IT Admin to configure a HoloLens 2 device for multi app kiosk mode, which is applicable at system level, has no affinity with any identity on the system, and applies to everyone who signs into the device. See the [HoloLens global assigned access kiosk](hololens-global-assigned-access-kiosk.md) documentation for more details on this new feature.

### Automatic launch of an application in multiple-app kiosk mode

- Focused experience with automatic app launch, further increasing the UI and app selections chosen for Kiosk mode experiences.

Applies only to multiple-app kiosk mode and only one app can be designated to autolaunch using highlighted attribute below in Assigned Access configuration.

Application is automatically launched when user signs-in.

```xml
<AllowedApps>                     
      <!--TODO: Add AUMIDs of apps you want to be shown here, e.g. <App AppUserModelId="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge" rs5:AutoLaunch="true"/> --> 
</AllowedApps>
```

### Kiosk mode behavior changes for handling of failures

When encountering failures in applying kiosk mode, the following behavior appears:

- Prior to Windows Holographic, version 20H2 - HoloLens will show all applications in the Start menu.
- Windows Holographic, version 20H2 - if a device has a kiosk configuration, which is a combination of both global assigned access and AAD group member assigned access, if determining AAD group membership fails, the user will see “nothing shown in start” menu.

![Image of what Kiosk mode now looks when it fails.](images/hololens-kiosk-failure-behavior.png )

- Starting with [Windows Holographic, version 21H1](hololens-release-notes.md#windows-holographic-version-21h1), Kiosk mode looks for Global Assigned Access before showing an empty start menu. The kiosk experience will fall back to a global kiosk configuration (if present) if there are failures during AAD group kiosk mode.

### Cache Azure AD Group membership for offline Kiosk

- More secure Kiosk mode by eliminating available apps on Kiosk mode failures.
- Enabled Offline Kiosks to be used with Azure AD groups for up to 60 days.

This policy controls for how many days, Azure AD group membership cache is allowed to be used for Assigned Access configurations targeting Azure AD groups for signed in user. Once this policy value is set to value greater than 0 only then cache is used otherwise not.  

Name: AADGroupMembershipCacheValidityInDays
URI value: ./Vendor/MSFT/Policy/Config/MixedReality/AADGroupMembershipCacheValidityInDays

Min - 0 days  
Max - 60 days

Steps to use this policy correctly:

1. Create a device configuration profile for kiosk targeting Azure AD groups and assign it to HoloLens device(s).
1. Create a custom OMA URI based device configuration that sets this policy value to desired number of days (> 0) and assign it to HoloLens device(s).
    1. The URI value should be entered in OMA-URI text box as ./Vendor/MSFT/Policy/Config/MixedReality/AADGroupMembershipCacheValidityInDays
    1. The value can be between min / max allowed.
1. Enroll HoloLens devices and verify both configurations get applied to the device.
1. Let Azure AD user 1 sign-in when internet is available, once user signs-in and Azure AD group membership is confirmed successfully, cache will be created.
1. Now Azure AD user 1 can take HoloLens offline and use it for kiosk mode as long as policy value allows for X number of days.
1. Steps 4 and 5 can be repeated for any other Azure AD user N. Key point here is that any Azure AD user must sign-in to device using Internet so at least once we can determine that they are member of Azure AD group to which Kiosk configuration is targeted.

> [!NOTE]
> Until step 4 is performed for a Azure AD user will experience failure behavior mentioned in “disconnected” environments.

### Enable Visitor Autologon

On builds [Windows Holographic, version 21H1](hololens-release-notes.md#windows-holographic-version-21h1) and onwards:

- AAD and Non-ADD configurations both support visitor accounts being autologon enabled for Kiosk modes.

#### Non-AAD configuration

1. Create a provisioning package that:
    1. Configures Runtime settings/AssignedAccess to allow Visitor accounts.
    1. Optionally enrolls the device in MDM (Runtime settings/Workplace/Enrollments) so that it can be managed later.
    1. Do not create a local account
2. [Apply the provisioning package](hololens-provisioning.md).

#### AAD configuration

AAD joined devices configured for kiosk mode can sign in a Visitor account with a single button tap from the sign-in screen. Once signed in to the visitor account, the device will not prompt for sign-in again until the Visitor is explicitly signed out from the start menu or the device is restarted.

Visitor Auto logon can be managed via [custom OMA-URI policy](/mem/intune/configuration/custom-settings-windows-10):

- URI value: ./Device/Vendor/MSFT/MixedReality/VisitorAutoLogon

| Policy | Description | Configurations |
| --------------------------- | ------------- | -------------------- |
| MixedReality/VisitorAutoLogon | Allows for a Visitor to Auto logon to a Kiosk. | 1 (Yes), 0 (No, default.) |

## Tips and Troubleshooting Kiosk

If you need to install additional apps to your Kiosk, you can install additional apps from the Microsoft store or by side loading more easily if you have an account that does not use Kiosk. Can also assign [required apps via MDM](/mem/intune/apps/apps-deploy#assign-an-app) to install automatically.

- To help protect devices that run in kiosk mode, consider adding device management policies that turn off features such as USB connectivity. Additionally, check your update ring settings to make sure that automatic updates do not occur during business hours.
- Do not include Classic Windows applications (Win32). HoloLens does not support these applications.
- S mode isn't supported on Windows Holographic for Business.

### References

For more information about how enrollment, see [Intune enrollment methods for Windows devices](/mem/intune/enrollment/windows-enrollment-methods).

For more information about how to create a kiosk configuration profile, see [Windows 10 and Windows Holographic for Business device settings to run as a dedicated kiosk using Intune](/intune/configuration/kiosk-settings).

For more information about the available settings for multi-app kiosks in Intune, see [Multi-app kiosks](/mem/intune/configuration/kiosk-settings-holographic#multi-app-kiosks)

For information about how to configure a kiosk configuration profile in Intune, see [How to Configure Kiosk Mode Using Microsoft Intune](hololens-commercial-infrastructure.md#how-to-configure-kiosk-mode-using-microsoft-intune).

### Kiosk and HoloLens (1st gen)

Kiosk mode is available only if the device has Windows Holographic for Business. All HoloLens 2 devices ship with Windows Holographic for Business and there are no other editions. Every HoloLens 2 device is able to run Kiosk mode out of the box.

HoloLens (1st gen) devices need to be upgraded both in terms of OS build and OS edition. Here is more information on updating a HoloLens (1st gen) to [Windows Holographic for Business](hololens1-upgrade-enterprise.md) edition. To update a HoloLens (1st gen) device to use kiosk mode, you must first make sure that the device runs Windows 10, version 1803, or a later version. If you have used the Windows Device Recovery Tool to recover your HoloLens (1st gen) device to its default build, or if you have installed the most recent updates, your device is ready to configure.

### <a id="ppkioskguest"></a>Optional: Add guest access to the kiosk configuration

In the [**Configs** section of the XML file](/windows/configuration/lock-down-windows-10-to-specific-apps#configs), you can configure a special group named **Visitor** to allow guests to use the kiosk. When the kiosk is configured to support the **Visitor** special group, a "**Guest**" option is added to the sign-in page. The **Guest** account does not require a password, and any data that is associated with the account is deleted when the account signs out.

To enable the **Guest** account, add the following snippet to your kiosk configuration XML:

```xml
<Configs>
  <Config>  
    <SpecialGroup Name="Visitor" />  
    <DefaultProfile Id="enter a profile ID"/>  
  </Config>  
</Configs>  
```

### Device Portal method

Set up the HoloLens device to use the Windows Device Portal](https://developer.microsoft.com/windows/mixed-reality/using_the_windows_device_portal#setting_up_hololens_to_use_windows_device_portal). The Device Portal is a web server on your HoloLens that you can connect to from a web browser on your PC.

 > [!CAUTION]
 > When you set up HoloLens to use the Device Portal, you have to enable Developer Mode on the device. Developer Mode on a device that has Windows Holographic for Business enables you to side-load apps. However, this setting creates a risk that a user can install apps that have not been certified by the Microsoft Store. Administrators can block the ability to enable Developer Mode by using the **ApplicationManagement/AllowDeveloper Unlock** setting in the [Policy CSP](/windows/client-management/mdm/policy-configuration-service-provider). [Learn more about Developer Mode.](/windows/uwp/get-started/enable-your-device-for-development#developer-mode)

Kiosk Mode can be set via Device Portal’s REST API by doing a POST to /api/holographic/kioskmode/settings with one required query string parameter (“kioskModeEnabled” with a value of “true” or “false”) and one optional parameter (“startupApp” with a value of a package name). Keep in mind that Device Portal is intended for developers only and should not be enabled on non-developer devices. The REST API is subject to change in future updates/releases.

### Kiosk deployment methods

- Microsoft Intune or other mobile device management (MDM) service
- Provisioning package
- Windows Device Portal

   > [!NOTE]  
   > Because Device Portal requires that Developer Mode be enabled on the device, we recommend that you use it only for demonstrations.

The following table lists the capabilities and benefits of each of the deployment methods.

| &nbsp; |Deploy by using Windows Device Portal |Deploy by using a provisioning package |Deploy by using MDM |
| --------------------------- | ------------- | -------------------- | ---- |
|Deploy single-app kiosks   | Yes           | Yes                  | Yes  |
|Deploy multi-app kiosks    | No            | Yes                  | Yes  |
|Deploy to local devices only | Yes           | Yes                  | No   |
|Deploy by using Developer Mode |Required       | Not required            | Not required   |
|Deploy by using Azure Active Directory (Azure AD)  | Not required            | Not required                   | Required  |
|Deploy automatically      | No            | No                   | Yes  |
|Deployment speed            | Fast       | Fast                 | Slow |
|Deploy at scale | Not recommended    | Recommended        | Recommended |
