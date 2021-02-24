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
                    <App AppUserModelId="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge" rs5:AutoLaunch="true" />
                    <App AppUserModelId="Microsoft.WindowsFeedbackHub_8wekyb3d8bbwe!App" />
                     <App AppUserModelId="Microsoft.settingn_8wekyb3d8bbwe!MicrosoftEdge" />
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
        <Profile Id="{8659AAD0-5C3F-4B55-A991-628E6EC3D4C5}">
          <AllAppsList>
            <AllowedApps>
              <App AppUserModelId="Microsoft.WindowsFeedbackHub_8wekyb3d8bbwe!App" />
            </AllowedApps>
          </AllAppsList>
          <StartLayout>
            <![CDATA[<LayoutModificationTemplate xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout" xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout" Version="1" xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification"> <LayoutOptions StartTileGroupCellWidth="6" /> <DefaultLayoutOverride> <StartLayoutCollection> <defaultlayout:StartLayout GroupCellWidth="6"> <start:Group Name="Life at a glance"> <start:Tile Size="2x2" Column="0" Row="0" AppUserModelID="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge" /> </start:Group> </defaultlayout:StartLayout> </StartLayoutCollection> </DefaultLayoutOverride></LayoutModificationTemplate>]]>
          </StartLayout>
          <Taskbar ShowTaskbar="true" />
        </Profile>
    </Profiles> 
    <Configs> 
        <v3:GlobalProfile Id="{8739C257-184F-45DD-8657-C235819172A3}"> 
            <v5:Exclusions> 
                <v5:SpecialGroup Name="DeviceOwner" /> 
            </v5:Exclusions> 
        </v3:GlobalProfile> 
        <Config>
          <SpecialGroup Name="Visitor"/>
          <DefaultProfile Id="{8659AAD0-5C3F-4B55-A991-628E6EC3D4C5}"/>
        </Config>
    </Configs> 
</AssignedAccessConfiguration>
