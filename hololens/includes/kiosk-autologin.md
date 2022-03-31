# [Autopilot with MDM](#tab/autopilot)

#### Autopilot with MDM

Visitor Auto logon can be managed via [custom OMA-URI policy](/mem/intune/configuration/custom-settings-windows-10).

- URI value: ./Device/Vendor/MSFT/Policy/Config/MixedReality/VisitorAutoLogon

| Policy | Description | Configurations |
| --------------------------- | ------------- | -------------------- |
| MixedReality/VisitorAutoLogon | Allows for a Visitor to Auto logon to a Kiosk. | 1 (Yes), 0 (No, default.) |

For details, see the Policy CSP page for [MixedReality/VisitorAutoLogon](/windows/client-management/mdm/policy-csp-mixedreality#mixedreality-visitorautologon).

# [Provisioning Package](#tab/provisioning)

#### Provisioning Package

1. Create a provisioning package that:
    1. Configures **Runtime settings/Policies/MixedReality/VisitorAutoLogon** to allow Visitor accounts.
    2. Optionally enrolls the device in MDM (**Runtime settings/Workplace/Enrollments**) so that it can be managed later.
    3. Do not create a local account
2. [Apply the provisioning package](../hololens-provisioning.md).

