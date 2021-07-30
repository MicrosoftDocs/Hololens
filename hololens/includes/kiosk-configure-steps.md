# [Intune UI Single app](#tab/uisak)

Microsoft Intune kiosk template - Single App Kiosk.

1. Create a configuration profile <br> 
![Create a configuration profile](./images/kiosk-steps/kiosk-template-sa-1.png)
<kbd>
    <img alt="Create a configuration profile" src="./images/kiosk-steps/kiosk-template-sa-1.png" width="586" height="330" />
</kbd>
1. Choose kiosk template <br> 
![Create a kiosk profile](./images/kiosk-steps/kiosk-template-sa-2.png)
1. Choose whether single app or multiple app kiosk and also choose kind of user targeting for kiosk mode <br> 
![Select single app kiosk mode](./images/kiosk-steps/kiosk-template-sa-3.png)
1. Choose the app to run in kiosk mode <br> 
![Choose the app](./images/kiosk-steps/kiosk-template-sa-4.png)
1. Leave rest of the options as is <br> 
![Leave options](./images/kiosk-steps/kiosk-template-sa-5.png)
1. Choose which groups / devices or users this configuration profile should get assigned to <br> 
![Choose how to assign](./images/kiosk-steps/kiosk-template-sa-6.png)
1. Review and create to save configuration profile
1. Perform MDM sync starting from either device or Intune to apply configuration to device. [Sync devices from Intune](/mem/intune/remote-actions/device-sync#sync-a-device) or on device via **Settings -> Accounts -> Work or school ->** select the connected account **-> Info -> Sync**
1. Sign in as the target user to experience kiosk.

# [Intune UI Multi app](#tab/uimak)

Microsoft Intune kiosk template - Multi App Kiosk.

1. Create a configuration profile <br> 
![Create a configuration profile](./images/kiosk-steps/kiosk-template-sa-1.png)
1. Choose kiosk template <br> 
![Create a kiosk profile](./images/kiosk-steps/kiosk-template-sa-2.png)
1. Choose whether single app or multiple app kiosk and also choose kind of user targeting for kiosk mode <br> 
![Select multi app kiosk mode](./images/kiosk-steps/kiosk-template-mak-3.png)
1. Choose the app(s) to run in kiosk mode <br> 
![Choose the apps](./images/kiosk-steps/kiosk-template-mak-4.png)
1. Leave rest of the options as is <br> 
![Leave options](./images/kiosk-steps/kiosk-template-sa-5.png)
1. Choose which groups / devices or users this configuration profile should get assigned to <br> 
![Choose how to assign](./images/kiosk-steps/kiosk-template-sa-6.png)
1. Review and create to save configuration profile
1. Perform MDM sync starting from either device or Intune to apply configuration to device. [Sync devices from Intune](/mem/intune/remote-actions/device-sync#sync-a-device) or on device via **Settings -> Accounts -> Work or school ->** select the connected account **-> Info -> Sync**
1. Sign in as the target user to experience kiosk.