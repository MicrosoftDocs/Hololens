# [Non-AAD configuration](#tab/nonaadlogon)

#### Non-AAD configuration

1. Create a provisioning package that:
    1. Configures Runtime settings/AssignedAccess to allow Visitor accounts.
    1. Optionally enrolls the device in MDM (Runtime settings/Workplace/Enrollments) so that it can be managed later.
    1. Do not create a local account
2. [Apply the provisioning package](../hololens-provisioning.md).

# [AAD configuration](#tab/aadlogon)

#### AAD configuration

AAD joined devices configured for kiosk mode can sign in a Visitor account with a single button tap from the sign-in screen. Once signed in to the visitor account, the device will not prompt for sign-in again until the Visitor is explicitly signed out from the start menu or the device is restarted.

Visitor Auto logon can be managed via [custom OMA-URI policy](/mem/intune/configuration/custom-settings-windows-10):

- URI value: ./Device/Vendor/MSFT/MixedReality/VisitorAutoLogon

| Policy | Description | Configurations |
| --------------------------- | ------------- | -------------------- |
| MixedReality/VisitorAutoLogon | Allows for a Visitor to Auto logon to a Kiosk. | 1 (Yes), 0 (No, default.) |