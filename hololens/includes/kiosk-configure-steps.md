# [Intune UI Single app](#tab/uisak)

Microsoft Intune kiosk template - Single App Kiosk.

1. Create a configuration profile <br> 
<kbd>
    <img alt="Create a configuration profile" src="../images/kiosk-steps/kiosk-template-sa-1.png"/>
</kbd>

<br>

2. Choose kiosk template <br> 
<kbd>
    <img alt="Create a kiosk profile" src="../images/kiosk-steps/kiosk-template-sa-2.png" width="415" height="530" />
</kbd>

<br>

3. Choose whether single app or multiple app kiosk and also choose kind of user targeting for kiosk mode <br> 
<kbd>
    <img alt="Select single app kiosk mode" src="../images/kiosk-steps/kiosk-template-sa-3.png"/>
</kbd>

<br>

4. Choose the app to run in kiosk mode <br> 
<kbd>
    <img alt="Choose the app" src="../images/kiosk-steps/kiosk-template-sa-4.png"/>
</kbd>

<br>

5. Leave rest of the options as is <br> 
<kbd>
    <img alt="Leave options" src="../images/kiosk-steps/kiosk-template-sa-5.png"/>
</kbd>

<br>

6. Choose which groups / devices or users this configuration profile should get assigned to <br> 
<kbd>
    <img alt="Choose how to assign" src="../images/kiosk-steps/kiosk-template-sa-6.png"/>
</kbd>

7. Review and create to save configuration profile
8. Perform MDM sync starting from either device or Intune to apply configuration to device. [Sync devices from Intune](/mem/intune/remote-actions/device-sync#sync-a-device) or on device via **Settings -> Accounts -> Work or school ->** select the connected account **-> Info -> Sync**
9. Sign in as the target user to experience kiosk.

# [Intune UI Multi app](#tab/uimak)

Microsoft Intune kiosk template - Multi App Kiosk.

1. Create a configuration profile <br> 
<kbd>
    <img alt="Create a configuration profile" src="../images/kiosk-steps/kiosk-template-sa-1.png"/>
</kbd>

<br>

2. Choose kiosk template <br> 
<kbd>
    <img alt="Create a kiosk profile" src="../images/kiosk-steps/kiosk-template-sa-2.png" width="415" height="530" />
</kbd>

<br>

3. Choose whether single app or multiple app kiosk and also choose kind of user targeting for kiosk mode <br> 
<kbd>
    <img alt="Select single app kiosk mode" src="../images/kiosk-steps/kiosk-template-mak-3.png"/>
</kbd>

<br>

4. Choose the app(s) to run in kiosk mode <br> 
<kbd>
    <img alt="Choose the app(s)" src="../images/kiosk-steps/kiosk-template-mak-4.png"/>
</kbd>

<br>

5. Leave rest of the options as is <br> 
<kbd>
    <img alt="Leave options" src="../images/kiosk-steps/kiosk-template-sa-5.png"/>
</kbd>

<br>

6. Choose which groups / devices or users this configuration profile should get assigned to <br> 
<kbd>
    <img alt="Choose how to assign" src="../images/kiosk-steps/kiosk-template-sa-6.png"/>
</kbd>

<br>

7. Review and create to save configuration profile
8. Perform MDM sync starting from either device or Intune to apply configuration to device. [Sync devices from Intune](/mem/intune/remote-actions/device-sync#sync-a-device) or on device via **Settings -> Accounts -> Work or school ->** select the connected account **-> Info -> Sync**
9. Sign in as the target user to experience kiosk.

# [Intune Custom profile](#tab/intunecustom)

1. Create a custom configuration profile <br>
<kbd>
    <img alt="Create a custom configuration profile" src="../images/kiosk-steps/kiosk-custom-1.png"/>
</kbd>

<br>

2. Specify name of custom configuration profile and click on “Add” in “Configuration settings” section to add OMA-URI settings.
<kbd>
    <img alt="Name and add" src="../images/kiosk-steps/kiosk-custom-2.png"/>
</kbd>

<br>

3. Specify name of OMA-URI settings.

    1. In OMA-URI textbox, enter **./Device/Vendor/MSFT/AssignedAccess/Configuration**
    1. Choose Data type as **String**.
    1. In value textbox, copy-paste the assigned access configuration xml (see reference links for examples based on your scenario and update as needed before copy-pasting).
    1. Select the save button to save the setting and configuration.

<kbd>
    <img alt="Specify OMA-URI settings" src="../images/kiosk-steps/kiosk-custom-3.png"/>
</kbd>

<br>

4. Choose which groups / devices or users this configuration profile should get assigned to.

<kbd>
    <img alt="Choose how to assign" src="../images/kiosk-steps/kiosk-custom-4.png"/>
</kbd>

<br>

5. Review and create to save configuration profile.
1. Perform MDM sync starting from either device or Intune to apply configuration to device. [Sync devices from Intune](/mem/intune/remote-actions/device-sync#sync-a-device) or on device via **Settings -> Accounts -> Work or school ->** select the connected account **-> Info -> Sync**
1. Sign in as the target user to experience kiosk.
