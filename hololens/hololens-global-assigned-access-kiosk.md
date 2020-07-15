---
title: Global Assigned Access
description: Guide for using OMA-URI for Global Assigned Access Kiosks
author: evmill
ms.author: v-evmill
ms.date: 7/13/2020
ms.topic: article
keywords: hololens, hololens 2, assigned access, kiosk
ms.prod: hololens
ms.sitesec: library
ms.localizationpriority: high
ms.reviewer: lavinds
manager: yannisle
appliesto:
- HoloLens 2
---

# Global Assigned Access – Kiosk

This feature configures Hololens 2 device for multiple app kiosk mode which is applicable at system level, has no affinity with any identity on the system and applies to everyone who signs into the device. 

> [!NOTE]
> This feature is currently only avalible in Windows Insider builds. If you would like to try this feature before it is generally avalible in HoloLens releases please read more about [Windows Insider](hololens-insider.md) builds.
 
## How to use this in Intune? 

> [!NOTE]
> Please be aware of the areas marked with "<!-". These areas will require you to make modifications based on your preferences. 

1.	Create a custom OMA URI device configuration profile as follows and apply it to HoloLens device group: 
![Global Assigned Access OMA-URI in Intune](images/global-assigned-access-omauri.png)

2.	For value, update and paste following content: 

   ```xml
   <?xml version="1.0" encoding="utf-8" ?> 
   <AssignedAccessConfiguration 
       xmlns="http://schemas.microsoft.com/AssignedAccess/2017/config" 
       xmlns:v2="http://schemas.microsoft.com/AssignedAccess/201810/config" 
       xmlns:v3="http://schemas.microsoft.com/AssignedAccess/2020/config" 
       xmlns:rs5="http://schemas.microsoft.com/AssignedAccess/201810/config" 
   > 
       <Profiles> 
           <Profile Id="{8739C257-184F-45DD-8657-C235819172A3}"> 
               <AllAppsList> 
                   <AllowedApps>                     
                       <!—TODO: Add AUMIDs of apps you want to be shown here, e.g. <App AppUserModelId="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge" rs5:AutoLaunch=”true” /> --> 
                        <!—TODO: Add AUMIDs of apps you want to be shown here, e.g. <App AppUserModelId="Microsoft.settingn_8wekyb3d8bbwe!MicrosoftEdge" /> --> 
                    </AllowedApps> 
               </AllAppsList> 
               <StartLayout> 
                   <![CDATA[<LayoutModificationTemplate xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout" xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout" Version="1" xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification"> 
                         <LayoutOptions StartTileGroupCellWidth="6" /> 
                         <DefaultLayoutOverride> 
                           <StartLayoutCollection> 
                             <defaultlayout:StartLayout GroupCellWidth="6"> 
                               <start:Group Name="Life at a glance"> 
                                 <!—This AUMID can be of any app and is not used on Hololens but is required for parity, so you can leave it as is. --> 
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

## How to use this in Windows Configuration Designer? 
 
1.	Update and save XML blob mentioned above as XML file. 

2.	Follow the steps in [Use a provisioning package to set up a single-app or multi-app kiosk](https://docs.microsoft.com/hololens/hololens-kiosk#use-a-provisioning-package-to-set-up-a-single-app-or-multi-app-kiosk), specifically the section "Prov. package, step 2 – Add the kiosk configuration XML file to a provisioning package" and refer to the XML file that was saved in the previous step. 

## Can I create a configuration where global applies to everyone except 1 AAD account or AAD group? 

Yes, please refer to the example XML blob below. Global Assigned Access profile is applied on Hololens when a specific one for the signed in user is not found, so it is default kiosk mode configuration for signed-in user. 
Here is an example of XML blob to be used: 

> [!NOTE]
> Please be aware of the areas marked with <!-  these areas will require you to make modifications based on your preferences. 

```xml
<?xml version="1.0" encoding="utf-8" ?> 
<AssignedAccessConfiguration xmlns="http://schemas.microsoft.com/AssignedAccess/2017/config" 
    xmlns:v2="http://schemas.microsoft.com/AssignedAccess/201810/config" 
    xmlns:v3="http://schemas.microsoft.com/AssignedAccess/2020/config" 
    xmlns:rs5="http://schemas.microsoft.com/AssignedAccess/201810/config"> 
    <Profiles> 
        <Profile Id="{9A2A490F-10F6-4764-974A-43B19E722C23}"> 
            <!—specify AUMIDs and other nodes as used in example above --> 
        </Profile> 
        <Profile Id="{8739C257-184F-45DD-8657-C235819172A3}"> 
            <!—specify AUMIDs and other nodes as used in example above --> 
        </Profile> 
    </Profiles> 
    <Configs> 
        <v3:GlobalProfile Id="{8739C257-184F-45DD-8657-C235819172A3}"/> 
        <Config> 
           <Account>AzureAD\<!-fully qualified AAD account name></Account> 
           <DefaultProfile Id="{9A2A490F-10F6-4764-974A-43B19E722C23}"/> 
        </Config> 
    </Configs> 
</AssignedAccessConfiguration> 
```
