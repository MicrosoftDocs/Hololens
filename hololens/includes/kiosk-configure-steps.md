# [Microsoft Intune single app kiosk template](#tab/uisak)

### Microsoft Intune single app kiosk template

1. Create a configuration profile.

    :::image type="content" alt-text="Create a configuration profile." source="../images/kiosk-steps/kiosk-template-sa-1.png":::

2. Choose kiosk template.

    :::image type="content" alt-text="Create a kiosk profile." source="../images/kiosk-steps/kiosk-template-sa-2.png":::

3. Choose whether single app or multiple app kiosk and also choose kind of user targeting for kiosk mode.

    :::image type="content" alt-text="Select single app kiosk mode." source="../images/kiosk-steps/kiosk-template-sa-3.png":::

4. Choose the app to run in kiosk mode.

    :::image type="content" alt-text="Choose the app." source="../images/kiosk-steps/kiosk-template-sa-4.png":::

5. Leave rest of the options as is.

    :::image type="content" alt-text="Leave options." source="../images/kiosk-steps/kiosk-template-sa-5.png":::

6. Choose which groups / devices or users this configuration profile should get assigned to. 

    :::image type="content" alt-text="Choose how to assign." source="../images/kiosk-steps/kiosk-template-sa-6.png":::

7. Review and create to save configuration profile.

8. Perform MDM sync starting from either device or Intune to apply configuration to device. [Sync devices from Intune](/mem/intune/remote-actions/device-sync#sync-a-device) or on device via **Settings > Accounts > Work or school >** select the connected account **> Info > Sync**.

9. Sign in as the target user to experience kiosk.

# [Microsoft Intune multi app kiosk template](#tab/uimak)

### Microsoft Intune multi app kiosk template

1. Create a configuration profile.

    :::image type="content" alt-text="Create a configuration profile." source="../images/kiosk-steps/kiosk-template-sa-1.png":::

2. Choose kiosk template.

    :::image type="content" alt-text="Create a kiosk profile." source="../images/kiosk-steps/kiosk-template-sa-2.png":::

3. Choose whether single app or multiple app kiosk and also choose kind of user targeting for kiosk mode.

    :::image type="content" alt-text="Select single app kiosk mode." source="../images/kiosk-steps/kiosk-template-mak-3.png":::

4. Choose the app(s) to run in kiosk mode.

    :::image type="content" alt-text="Choose the app(s)." source="../images/kiosk-steps/kiosk-template-mak-4.png":::

5. Leave rest of the options as is.

    :::image type="content" alt-text="Leave options." source="../images/kiosk-steps/kiosk-template-sa-5.png":::

6. Choose which groups / devices or users this configuration profile should get assigned to. 

    :::image type="content" alt-text="Choose how to assign." source="../images/kiosk-steps/kiosk-template-sa-6.png":::

7. Review and create to save configuration profile.

8. Perform MDM sync starting from either device or Intune to apply configuration to device. [Sync devices from Intune](/mem/intune/remote-actions/device-sync#sync-a-device) or on device via **Settings > Accounts > Work or school >** select the connected account **> Info > Sync**.

9. Sign in as the target user to experience kiosk.

# [Microsoft Intune custom template](#tab/intunecustom)

### Microsoft Intune custom template

1. Create xml configuration for your desired kiosk experience. See [examples](../hololens-kiosk-reference.md#kiosk-xml-code-samples) here to begin.

1. Create a custom configuration profile.

    :::image type="content" alt-text="Create a custom configuration profile." source="../images/kiosk-steps/kiosk-custom-1.png":::

3. Specify name of custom configuration profile and click on “Add” in “Configuration settings” section to add OMA-URI settings.

    :::image type="content" alt-text="Name and add." source="../images/kiosk-steps/kiosk-custom-2.png":::

4. Specify name of OMA-URI settings.

    1. In OMA-URI textbox, enter **./Device/Vendor/MSFT/AssignedAccess/Configuration**
    1. Choose Data type as **String**.
    1. In value textbox, copy-paste the assigned access configuration xml (see reference links for examples based on your scenario and update as needed before copy-pasting).
    1. Select the save button to save the setting and configuration.

        :::image type="content" alt-text="Specify OMA-URI settings." source="../images/kiosk-steps/kiosk-custom-3.png":::
    
5. Choose which groups / devices or users this configuration profile should get assigned to.

    :::image type="content" alt-text="Choose how to assign." source="../images/kiosk-steps/kiosk-custom-4.png":::


6. Review and create to save configuration profile.

1. Perform MDM sync starting from either device or Intune to apply configuration to device. [Sync devices from Intune](/mem/intune/remote-actions/device-sync#sync-a-device) or on device via **Settings > Accounts > Work or school >** select the connected account **> Info > Sync**

1. Sign in as the target user to experience kiosk.

# [Runtime provisioning - Multi app](#tab/ppkgmak)

### Runtime provisioning - Multi app

1. Create xml configuration for your desired kiosk experience. See [examples](../hololens-kiosk-reference.md#kiosk-xml-code-samples) here to begin.

1. Open [Windows Configuration Designer](https://www.microsoft.com/store/apps/9nblggh4tx22).

1. On the Start page select **Provision HoloLens devices**.

    :::image type="content" alt-text="Selecting provision HoloLens." source="../images/kiosk-steps/kiosk-provision-1.png":::

4. Select **Provision HoloLens 2 devices,** then select next.

    :::image type="content" alt-text="Select HoloLens 2." source="../images/kiosk-steps/kiosk-provision-2.png":::

5. Name your project. Optionally write a description. Select **Finish** to proceed.

6. In the bottom left of the screen, select **Switch to advanced editor**. Confirm switching to the advanced editor by selecting **Yes**.
    
	:::image type="content" alt-text="Switch to advanced editor." source="../images/kiosk-steps/kiosk-provision-2.png":::
    
7. On the left hand side, expand Runtime settings, AssignedAccess and select **MultiAppAssignedAccess**.
    
	:::image type="content" alt-text="select MultiAppAssignedAccess." source="../images/kiosk-steps/kiosk-provision-3.png":::
    
8. Select the **Browse…** button to open the file explorer. And select the your configured Kiosk xml file.

9. Select **Export** , then **Provisioning Package**.
    
	:::image type="content" alt-text="Export package." source="../images/kiosk-steps/kiosk-provision-4.png":::

10. Change owner type to **IT Admin**.

	:::image type="content" alt-text="Exporting as IT Admin." source="../images/kiosk-steps/kiosk-provision-5.png":::
    
11. Select **Next** three times. Then select **Build**.

12. After your provisioning package builds, open the Output location folder. The .ppkg file is your provision package. Optional step: Save your project.

13. Now you can apply your provisioning package. You can either [apply a provisioning package to HoloLens during setup](../hololens-provisioning.md#apply-a-provisioning-package-to-hololens-during-setup) or [apply a provisioning package to HoloLens after setup](../hololens-provisioning.md#applyremove-a-provisioning-package-to-hololens-after-setup).

14. Sign in as the target user to experience kiosk.

# [Runtime provisioning - Single app](#tab/ppkgsak)

### Runtime provisioning - Single app

1. Open [Windows Configuration Designer](https://www.microsoft.com/store/apps/9nblggh4tx22).

1. On the Start page select **Provision HoloLens devices**.

	:::image type="content" alt-text="Selecting provision HoloLens." source="../images/kiosk-steps/kiosk-provision-1.png":::

3. Select **Provision HoloLens 2 devices,** then select next.

	:::image type="content" alt-text="Select HoloLens 2." source="../images/kiosk-steps/kiosk-provision-2.png":::

4. Name your project. Optionally write a description. Select **Finish** to proceed.

5. In the bottom left of the screen, select **Switch to advanced editor**. Confirm switching to the advanced editor by selecting **Yes**.

	:::image type="content" alt-text="Switch to advanced editor." source="../images/kiosk-steps/kiosk-provision-2.png":::
    
6. On the left hand side, expand Runtime settings, AssignedAccess and select **AssignedAccessSettings**.

	:::image type="content" alt-text="Navigate to assigned access settings." source="../images/kiosk-steps/kiosk-provision-sak-1.png":::
    
7. Define your kiosk in the text box. For example, the following creates a single app kiosk for a local account named LocalAccount that is the settings app.
`{"Account":"LocalAccount","AUMID":"BAEAEF15-9BAB-47FC-800B-ACECAD2AE94B_cw5n1h2txyewy!App"}`

8. Select **Export** , then **Provisioning Package**.

	:::image type="content" alt-text="Export package." source="../images/kiosk-steps/kiosk-provision-4.png":::
    
9. Change owner type to **IT Admin**.

	:::image type="content" alt-text="Exporting as IT Admin." source="../images/kiosk-steps/kiosk-provision-5.png":::

10. Select **Next** three times. Then select **Build**.

11. After your provisioning package builds, open the Output location folder. The .ppkg file is your provision package. Optional step: Save your project.

12. Now you can apply your provisioning package. You can either [apply a provisioning package to HoloLens during setup](../hololens-provisioning.md#apply-a-provisioning-package-to-hololens-during-setup) or [apply a provisioning package to HoloLens after setup](../hololens-provisioning.md#applyremove-a-provisioning-package-to-hololens-after-setup).
