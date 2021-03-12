# Deployment Guide - Corporate Connected HoloLens 2 with Dynamics 365 Guides - Overview

This guide will help IT professionals plan for and deploy Microsoft HoloLens 2 devices with Dynamics 365 Guides (Guides) to their organization. This guide is great for pilots as well as production deployments and is similar to the [Scenario B: Deploy inside your organization's network](https://docs.microsoft.com/hololens/common-scenarios#scenario-b-deploy-inside-your-organizations-network) guide. After testing your proof-of-concept, use this guide to move forward with integrating HoloLens into your organization.

In this guide, we will cover how to enroll your devices into your existing device management, applying licenses as needed, and validating that your end users are able to operate a Dynamics 365 Guide, as well as using a custom line of business apps, after device set up. 

## Prerequisite Infrastructure

The following infrastructure should already be in place:
- Wi-Fi
    - Internal corporate network with access to internal resources and limited access to the internet or Cloud services
    - Device-based certificate authentication.
- Azure AD Join with MDM Auto Enrollment ([Azure Active Directory P1 subscription](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) needed)
- MDM (Intune) Managed
    - One or more applications are deployed via MDM.
- Users sign in with their own corporate account (AAD)
    - Single or multiple users per device supported.
- Varying levels of device lockdown configurations are applied based on specific use cases, from Fully Open to Single App Kiosk.

## Dynamics 365 Guides Infrastructure
There are three important pieces of infrastructure that should be setup and configured for a successful HoloLens 2 with Dynamics 365 Guides deployment.
- Network certificates and proxy configuration
- Guides installation
    - Dynamics 365 Guides subscription
        - Microsoft Dataverse (included)
        - Power Apps (included)
    - Power BI Desktop 
- Custom apps deployment
    - uploading, 
    - assigning, and 
    - setting your app to automatically download to specific devices

## Stages of Deployment
### Prepare
> [!div class="checklist"]
>- Learn about the infrastructure essentials for HoloLens 2 devices.
>- Learn more about Azure AD and set up one if you don't have it.
>- Learn about Identity management and how to best set up Azure AD accounts.
>- Learn more about MDM and set up with Intune if you don't already have one ready.
>- Familiarize yourself with certificate-based Wi-Fi
>- Familiarize yourself with Proxy
>- Understand how you can use Line of Business Apps
>- Learn more about the way you can use Guides for your organization 
### Configure
> [!div class="checklist"]
>- How to create users and groups
>- How to set up Auto Enrollment
>- Wi-Fi Certificates Set up
>- Configure Proxy
>-	Upload and Assign Line of Business (LOB) App packages
>-	Setup Dynamics 365 Guides 
    - Users and Application licenses
    - Dataverse
    - PC Authoring
>- Optional: Kiosk
>- Optional: WDAC
### Deploy
> [!div class="checklist"]
>-	Validate enrollment via device and MDM
>-	Wi-Fi certificate validation
>-	Validate LOB app install
>-	Validate Guides via authoring and operating
### Maintain
> [!div class="checklist"]
>- Update HoloLens 2
>- How to update Guides (store apps)
>- How to update LOB apps. 
>- How to manage HoloLens Updates
>- Development plan. 
>- Making a support plan.
>- Device management options

# Next step 
> [!div class="nextstepaction"]
> [Corporate connected deployment - Prepare](hololens2-corp-connected-prepare.md)
