---
title: HoloLens kiosk reference information
description: Information and samples for kiosks on HoloLens devices. 
ms.prod: hololens
ms.sitesec: library
author: evmill
ms.author: v-evmill
ms.topic: article
ms.localizationpriority: medium
ms.date: 8/24/2021
ms.reviewer: 
manager: yannisle
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# HoloLens Kiosk reference information

This page contains helpful information for setting up your HoloLens device's kiosk mode. This references include AUMIDs for inbox apps and locating yours, and several XML samples for Kiosk mode, that are just a few edits away from being ready to use for several different scenarios. For information on setting up a Kiosk, read the [set up a Kiosk page.](hololens-kiosk.md)

## HoloLens Application User Model IDs (AUMIDs)  

For general information about how to choose kiosk apps, see [Guidelines for choosing an app for assigned access (kiosk mode)](/windows/configuration/guidelines-for-assigned-access-app).

If you use a Mobile Device Management (MDM) system or a provisioning package to configure kiosk mode, you use the [AssignedAccess Configuration Service Provider (CSP)](/windows/client-management/mdm/assignedaccess-csp) to specify applications. The CSP uses [Application User Model IDs (AUMIDs)](/windows/configuration/find-the-application-user-model-id-of-an-installed-app) to identify applications. The following table lists the AUMIDs of some in-box applications that you can use in a multi-app kiosk.

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

In addition, the Mixed Reality Home is not able to be set as a kiosk app.

Return to [Supported scenarios for kiosk mode based on identity type](hololens-kiosk.md#supported-scenarios-for-kiosk-mode-based-on-identity-type)

## Kiosk XML Code Samples

1. [Multiple app global assigned access profile](#multiple-app-global-assigned-access-profile)
1. [Multiple app global assigned access profile excluding device owners](#multiple-app-global-assigned-access-profile-excluding-device-owners)
1. [Multiple app assigned access profile for a local account or AAD user account](#multiple-app-assigned-access-profile-for-a-local-account-or-aad-user-account)
1. [Multiple app assigned access profiles for two AAD users or more](#multiple-app-assigned-access-profiles-for-two-aad-users-or-more)
1. [Multiple app assigned access profile for one AAD group](#multiple-app-assigned-access-profile-for-one-aad-group)
1. [Multiple app assigned access profile for two AAD groups or more](#multiple-app-assigned-access-profile-for-two-aad-groups-or-more)
1. [Multiple app assigned access profile for one AAD account and one AAD group](#multiple-app-assigned-access-profile-for-one-aad-account-and-one-aad-group)
1. [Multiple app assigned access profile for visitors](#multiple-app-assigned-access-profile-for-visitors)

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
         <!--Profile Id can be any unique GUID -->
        <Profile Id="{8739C257-184F-45DD-8657-C235819172A3}"> 
            <AllAppsList> 
                <AllowedApps>                     
                    	<!--
                        TODO:
                        1. Add AUMIDs of app(s) you want displayed in start menu. See examples below.
                        2. Specify rs5:AutoLaunch="true" only for 1 app. If automatic launch not desired, remove this attribute.
                        
                        <App AppUserModelId="Microsoft.Dynamics365.Guides_8wekyb3d8bbwe!MicrosoftGuides" rs5:AutoLaunch="true" />
                        <App AppUserModelId="Microsoft.WindowsFeedbackHub_8wekyb3d8bbwe!App" />
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

[Back to list](#kiosk-xml-code-samples) <br>
Return to [Supported scenarios for kiosk mode based on identity type](hololens-kiosk.md#supported-scenarios-for-kiosk-mode-based-on-identity-type)

### Multiple app global assigned access profile excluding device owners

```xml
<?xml version="1.0" encoding="utf-8" ?> 
<AssignedAccessConfiguration 
xmlns="http://schemas.microsoft.com/AssignedAccess/2017/config" 
xmlns:v2="http://schemas.microsoft.com/AssignedAccess/201810/config" 
xmlns:v3="http://schemas.microsoft.com/AssignedAccess/2020/config" 
xmlns:v5="http://schemas.microsoft.com/AssignedAccess/202010/config"
xmlns:rs5="http://schemas.microsoft.com/AssignedAccess/201810/config" 
> 
    <Profiles>
         <!--Profile Id can be any unique GUID -->
      <Profile Id="{8739C257-184F-45DD-8657-C235819172A3}">
            <AllAppsList>
                <AllowedApps>                   
                    	<!--
                        TODO:
                        1. Add AUMIDs of app(s) you want displayed in start menu. See examples below.
                        2. Specify rs5:AutoLaunch="true" only for 1 app. If automatic launch not desired, remove this attribute.
                        
                        <App AppUserModelId="Microsoft.Dynamics365.Guides_8wekyb3d8bbwe!MicrosoftGuides" rs5:AutoLaunch="true" />
                        <App AppUserModelId="Microsoft.WindowsFeedbackHub_8wekyb3d8bbwe!App" />
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
        <v3:GlobalProfile Id="{8739C257-184F-45DD-8657-C235819172A3}">
            <v5:Exclusions>
                <v5:SpecialGroup Name="DeviceOwner" />
            </v5:Exclusions>
        </v3:GlobalProfile>
    </Configs>
</AssignedAccessConfiguration>
```

[Back to list](#kiosk-xml-code-samples) <br>
Return to [Supported scenarios for kiosk mode based on identity type](hololens-kiosk.md#supported-scenarios-for-kiosk-mode-based-on-identity-type)

### Multiple app assigned access profile for a local account or AAD user account

:::code language="xml" source="samples/kiosk-sample-multi-app-local-or-aad-user.xml" highlight="18-20,51,55":::

[Back to list](#kiosk-xml-code-samples) <br>
Return to [Supported scenarios for kiosk mode based on identity type](hololens-kiosk.md#supported-scenarios-for-kiosk-mode-based-on-identity-type)

### Multiple app assigned access profiles for two AAD users or more

:::code language="xml" source="samples/kiosk-sample-multi-app-two-aad-users-or-more.xml" highlight="22-24,52,53,80,88":::

[Back to list](#kiosk-xml-code-samples) <br>
Return to [Supported scenarios for kiosk mode based on identity type](hololens-kiosk.md#supported-scenarios-for-kiosk-mode-based-on-identity-type)

### Multiple app assigned access profile for one AAD group

:::code language="xml" source="samples/kiosk-sample-multi-app-one-aad-group.xml" highlight="28":::

[Back to list](#kiosk-xml-code-samples) <br>
Return to [Supported scenarios for kiosk mode based on identity type](hololens-kiosk.md#supported-scenarios-for-kiosk-mode-based-on-identity-type)

### Multiple app assigned access profile for two AAD groups or more

:::code language="xml" source="samples/kiosk-sample-multi-app-two-aad-groups-or-more.xml" highlight="22-24,52,53,83,94":::

[Back to list](#kiosk-xml-code-samples) <br>
Return to [Supported scenarios for kiosk mode based on identity type](hololens-kiosk.md#supported-scenarios-for-kiosk-mode-based-on-identity-type)

### Multiple app assigned access profile for one AAD account and one AAD group

:::code language="xml" source="samples/kiosk-sample-multi-app-for-aad-user-and-aad-group.xml" highlight="22-24,52,53,80,91":::

[Back to list](#kiosk-xml-code-samples) <br>
Return to [Supported scenarios for kiosk mode based on identity type](hololens-kiosk.md#supported-scenarios-for-kiosk-mode-based-on-identity-type)

### Multiple app assigned access profile for visitors

:::code language="xml" source="samples/kiosk-sample-multi-app-visitor-user.xml" highlight="18-20":::

[Back to list](#kiosk-xml-code-samples) <br>
Return to [Supported scenarios for kiosk mode based on identity type](hololens-kiosk.md#supported-scenarios-for-kiosk-mode-based-on-identity-type)
