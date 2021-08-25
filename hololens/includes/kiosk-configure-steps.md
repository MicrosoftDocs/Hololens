# [Intune UI Single app](#tab/uisak)

## Microsoft Intune single app kiosk template

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

## Microsoft Intune multi app kiosk template

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

## Microsoft Intune custom template

1. Create xml configuration for your desired kiosk experience. See [examples](../hololens-kiosk-reference.md#kiosk-xml-code-samples) here to begin.

1. Create a custom configuration profile <br>
<kbd>
    <img alt="Create a custom configuration profile" src="../images/kiosk-steps/kiosk-custom-1.png"/>
</kbd>

<br>

3. Specify name of custom configuration profile and click on “Add” in “Configuration settings” section to add OMA-URI settings.
<kbd>
    <img alt="Name and add" src="../images/kiosk-steps/kiosk-custom-2.png"/>
</kbd>

<br>

4. Specify name of OMA-URI settings.

    1. In OMA-URI textbox, enter **./Device/Vendor/MSFT/AssignedAccess/Configuration**
    1. Choose Data type as **String**.
    1. In value textbox, copy-paste the assigned access configuration xml (see reference links for examples based on your scenario and update as needed before copy-pasting).
    1. Select the save button to save the setting and configuration.

    <kbd>
        <img alt="Specify OMA-URI settings" src="../images/kiosk-steps/kiosk-custom-3.png"/>
    </kbd>

<br>

5. Choose which groups / devices or users this configuration profile should get assigned to.
<kbd>
    <img alt="Choose how to assign" src="../images/kiosk-steps/kiosk-custom-4.png"/>
</kbd>

<br>

6. Review and create to save configuration profile.
1. Perform MDM sync starting from either device or Intune to apply configuration to device. [Sync devices from Intune](/mem/intune/remote-actions/device-sync#sync-a-device) or on device via **Settings -> Accounts -> Work or school ->** select the connected account **-> Info -> Sync**
1. Sign in as the target user to experience kiosk.

# [Provisioning package multi app kiosk](#tab/ppkgmak)

## Runtime provisioning - Multi app

1. Create xml configuration for your desired kiosk experience. See [examples](../hololens-kiosk-reference.md#kiosk-xml-code-samples) here to begin.

1. Open [Windows Configuration Designer](https://www.microsoft.com/store/apps/9nblggh4tx22).

1. On the Start page select **Provision HoloLens devices.**
<kbd>
    <img alt="Selecting provision HoloLens" src="../images/kiosk-steps/kiosk-provision-1.png"/>
</kbd>

<br>

4. Select **Provision HoloLens 2 devices,** then select next.
<kbd>
    <img alt="Select HoloLens 2" src="../images/kiosk-steps/kiosk-provision-2.png"/>
</kbd>

<br>

5. Name your project. Optionally write a description. Select **Finish** to proceed.

6. In the bottom left of the screen, select **Switch to advanced editor.** Confirm switching to the advanced editor by selecting **Yes.**

    <kbd>
        <img alt="Switch to advanced editor" src="../images/kiosk-steps/kiosk-provision-2.png"/>
    </kbd>

<br>

7. On the left hand side, expand Runtime settings, AssignedAccess and select **MultiAppAssignedAccess**.

    <kbd>
        <img alt="select MultiAppAssignedAccess" src="../images/kiosk-steps/kiosk-provision-3.png"/>
    </kbd>

<br>

8. Select the **Browse…** button to open the file explorer. And select the your configured Kiosk xml file.

9. Select **Export** , then **Provisioning Package**.

    <kbd>
        <img alt="Export package" src="../images/kiosk-steps/kiosk-provision-4.png"/>
    </kbd>

<br>

10. Change owner type to **IT Admin**.

    <kbd>
        <img alt="Exporting as IT Admin" src="../images/kiosk-steps/kiosk-provision-5.png"/>
    </kbd>

<br>

11. Select **Next** three times. Then select **Build**.

12. After your provisioning package builds, open the Output location folder. The .ppkg file is your provision package. Optional step: Save your project.

13. Now you can apply your provisioning package. You can either [apply a provisioning package to HoloLens during setup](../hololens-provisioning.md#apply-a-provisioning-package-to-hololens-during-setup) or [apply a provisioning package to HoloLens after setup](../hololens-provisioning.md#applyremove-a-provisioning-package-to-hololens-after-setup).

14. Sign in as the target user to experience kiosk.

# [Provisioning package single app kiosk](#tab/ppkgsak)

## Runtime provisioning - Single app

1. Open [Windows Configuration Designer](https://www.microsoft.com/store/apps/9nblggh4tx22).

1. On the Start page select **Provision HoloLens devices.**

    <kbd>
        <img alt="Selecting provision HoloLens" src="../images/kiosk-steps/kiosk-provision-1.png"/>
    </kbd>

<br>

3. Select **Provision HoloLens 2 devices,** then select next.

    <kbd>
        <img alt="Select HoloLens 2" src="../images/kiosk-steps/kiosk-provision-2.png"/>
    </kbd>

<br>

4. Name your project. Optionally write a description. Select **Finish** to proceed.

5. In the bottom left of the screen, select **Switch to advanced editor.** Confirm switching to the advanced editor by selecting **Yes.**

    <kbd>
        <img alt="Switch to advanced editor" src="../images/kiosk-steps/kiosk-provision-2.png"/>
    </kbd>

<br>

6. On the left hand side, expand Runtime settings, AssignedAccess and select **AssignedAccessSettings**.

    <kbd>
        <img alt="Navigate to assigned access settings" src="../images/kiosk-steps/kiosk-provision-sak-1.png"/>
    </kbd>

<br>

7. Define your kiosk in the text box. For example, the following creates a single app kiosk for a local account named LocalAccount that is the settings app.
```{"Account":"LocalAccount","AUMID":"BAEAEF15-9BAB-47FC-800B-ACECAD2AE94B_cw5n1h2txyewy!App"}```

8. Select **Export** , then **Provisioning Package**.

    <kbd>
        <img alt="Export package" src="../images/kiosk-steps/kiosk-provision-4.png"/>
    </kbd>

<br>

9. Change owner type to **IT Admin**.

    <kbd>
        <img alt="Exporting as IT Admin" src="../images/kiosk-steps/kiosk-provision-5.png"/>
    </kbd>

<br>

10. Select **Next** three times. Then select **Build**.

11. After your provisioning package builds, open the Output location folder. The .ppkg file is your provision package. Optional step: Save your project.

12. Now you can apply your provisioning package. You can either [apply a provisioning package to HoloLens during setup](../hololens-provisioning.md#apply-a-provisioning-package-to-hololens-during-setup) or [apply a provisioning package to HoloLens after setup](../hololens-provisioning.md#applyremove-a-provisioning-package-to-hololens-after-setup).