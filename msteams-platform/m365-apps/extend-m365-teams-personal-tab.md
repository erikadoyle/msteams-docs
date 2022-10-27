---
title: Extend a Teams personal tab app across Microsoft 365
description: Learn how to update your personal tab app to run in Outlook and Office, in addition to Microsoft Teams.
ms.date: 10/10/2022
ms.topic: tutorial
ms.custom: m365apps
ms.localizationpriority: medium
---
# Extend a Teams personal tab across Microsoft 365

Personal tabs provide a great way to enhance the Microsoft Teams experience. Using personal tabs, you can provide a user access to their application right within Teams, without the user having to leave the experience or sign in again. With this preview, personal tabs can light up within other Microsoft 365 applications. This tutorial demonstrates the process of taking an existing Teams personal tab and updating it to run in both Outlook and Office desktop and web experiences, as well as Office app for Android.

Updating your personal app to run in Outlook and Office involves these steps:

> [!div class="checklist"]
>
> * Update your app manifest.
> * Update your TeamsJS SDK references.
> * Amend your Content Security Policy headers.
> * Update your Microsoft Azure Active Directory (Azure AD) App Registration for Single Sign On (SSO).
> * Sideload your updated app in Teams.

The rest of this guide walks you through these steps and show you how to preview your personal tab in other Microsoft 365 applications.

## Prerequisites

To complete this tutorial, you'll need:

* A Microsoft 365 Developer Program sandbox tenant
* Your sandbox tenant enrolled in *Office 365 Targeted Releases*
* A machine with Office apps installed from the Microsoft 365 Apps *beta channel*
* (Optional) An Android device or emulator with Office app for Android installed and enrolled in the *beta program*
* (Optional) [Teams Toolkit](https://aka.ms/teams-toolkit) extension for Microsoft Visual Studio Code to help update your code

> [!div class="nextstepaction"]
> [Install prerequisites](prerequisites.md)

## Prepare your personal tab for the upgrade

If you have an existing personal tab app, make a copy or a branch of your production project for testing and update your App ID in the app manifest to use a new identifier (distinct from the production App ID, for testing).

If you'd like to use sample code to complete this tutorial, follow the setup steps in the [Todo List Sample](https://github.com/OfficeDev/TeamsFx-Samples/tree/main/todo-list-with-Azure-backend) to build a personal tab app using the Teams Toolkit extension for Visual Studio Code, then return to this article to update it for Microsoft 365.

Alternately, you can use a basic single sign-on *hello world* app already enabled Microsoft 365 in the following [Quickstart](#quickstart) section and then skip to [Sideload your app in Teams](#sideload-your-app-in-teams) .

### Quickstart

To start with a [personal tab](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend-M365) that's already enabled to run in Outlook and Office, use Teams Toolkit extension for Visual Studio Code.

1. From Visual Studio Code, open the command palette (`Ctrl+Shift+P`), type `Teams: Create a new Teams app`.
1. Select **SSO enabled personal tab**.

    :::image type="content" source="images/toolkit-tab-sample.png" alt-text="Todo List sample (Works in Teams, Outlook and Office) in Teams Toolkit":::

1. Select a location on your local machine for the workspace folder.
1. Open the command palette (`Ctrl+Shift+P`) and type `Teams: Provision in the cloud` to create the required app resources (App Service plan, Storage account, Function App, Managed Identity) in your Azure account.
1. Open the command palette (`Ctrl+Shift+P`) and type `Teams: Deploy to the cloud` to deploy the sample code to the provisioned resources in Azure and start the app.

From here, you can skip ahead to [Sideload your app in Teams](#sideload-your-app-in-teams) and preview your app in Outlook and Office. (The app manifest and TeamsJS API calls have already been updated for Microsoft 365.)

## Update the app manifest

You'll need to use the [Teams developer manifest](../resources/schema/manifest-schema.md) schema version `1.13` to enable your Teams personal tab to run in Outlook and Office.

You have two options for updating your app manifest:

# [Teams Toolkit](#tab/manifest-teams-toolkit)

1. Open the command palette: `Ctrl+Shift+P`.
1. Run the `Teams: Upgrade Teams manifest` command and select your app manifest file. Changes will be made in place.

# [Manual steps](#tab/manifest-manual)

Open your Teams app manifest and update the `$schema` and `manifestVersion` with the following values:

```json
{
    "$schema" : "https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json",
    "manifestVersion" : "1.13"
}
```

---

If you used Teams Toolkit to create your personal app, you can also use it to validate the changes to your manifest file and identify any errors. Open the command palette (`Ctrl+Shift+P`) and find **Teams: Validate manifest file**.

## Update SDK references

To run in Outlook and Office, your app will need to reference the npm package `@microsoft/teams-js@2.0.0` (or higher). While code with downlevel versions is supported in Outlook and Office, deprecation warnings are logged, and support for downlevel versions of TeamsJS in Outlook and Office will eventually cease.

You can use Teams Toolkit to help identify and automate the required code changes to upgrade from 1.x TeamsJS versions to TeamsJS version 2.x.x. Alternately, you can perform the same steps manually; refer to [Microsoft Teams JavaScript client SDK](../tabs/how-to/using-teams-client-sdk.md#whats-new-in-teamsjs-version-20) for details.

1. Open the *Command palette*: `Ctrl+Shift+P`.
1. Run the command `Teams: Upgrade Teams JS SDK and code references`.

Upon completion, your *package.json* file will reference `@microsoft/teams-js@2.0.0` (or higher) and your `*.js/.ts` and `*.jsx/.tsx` files will be updated with:

> [!div class="checklist"]
>
> * Import statements for teams-js@2.x.x
> * [Function, Enum, and Interface calls](../tabs/how-to/using-teams-client-sdk.md#whats-new-in-teamsjs-version-20) for teams-js@2.x.x
> * `TODO` comment reminders flagging areas that might be impacted by [Context](../tabs/how-to/using-teams-client-sdk.md#updates-to-the-context-interface) interface changes
> * `TODO` comment reminders to [convert callback functions to promises](../tabs/how-to/using-teams-client-sdk.md#callbacks-converted-to-promises)

> [!IMPORTANT]
> Code inside *.html* files is not supported by the upgrade tooling and require manual changes.

## Configure Content Security Policy headers

As in Microsoft Teams, tab applications are hosted within [iframe elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) in Office and Outlook web clients.

If your app makes use of [Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy) (CSP) headers, make sure you allow all the following [frame-ancestors](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) in your CSP headers:

|Microsoft 365 host| frame-ancestor permission|
|--|--|
| Teams | `teams.microsoft.com` |
| Office | `*.microsoft365.com`, `*.office.com` |
| Outlook | `outlook.live.com`, `outlook.office.com`, `outlook.office365.com`, `outlook-sdf.office.com`, `outlook-sdf.office365.com` |

## Update Azure AD app registration for SSO

[Azure Active Directory (AD) Single-sign on (SSO)](../tabs/how-to/authentication/tab-sso-overview.md) for personal tabs works the same way in Office and Outlook as it does in Teams. However you'll need to add several client application identifiers to the Azure AD app registration of your tab app in your tenant's *App registrations* portal.

1. Sign in to [Microsoft Azure portal](https://portal.azure.com) with your sandbox tenant account.
1. Open the **App registrations** blade.
1. Select the name of your personal tab application to open its app registration.
1. Select  **Expose an API** (under *Manage*).

    :::image type="content" source="images/azure-app-registration-clients.png" alt-text="Authorize client Ids from the *App registrations* blade on Azure portal":::

1. In the **Authorized client applications** section, ensure all of the following `Client Id` values are added:

    |Microsoft 365 client application | Client ID |
    |--|--|
    |Teams desktop, mobile |1fec8e78-bce4-4aaf-ab1b-5451cc387264 |
    |Teams web |5e3ce6c0-2b1f-4285-8d4b-75ee78787346 |
    |Office web  |4765445b-32c6-49b0-83e6-1d93765276ca|
    |Office desktop  | 0ec893e0-5785-4de6-99da-4ed124e5296c |
    |Office mobile  | d3590ed6-52b3-4102-aeff-aad2292ab01c |
    |Outlook desktop, mobile | d3590ed6-52b3-4102-aeff-aad2292ab01c |
    |Outlook web | bc59ab01-8403-45c6-8796-ac3ef710b3e3|

    > [!NOTE]
    > Some Microsoft 365 client applications share Client IDs.

## Sideload your app in Teams

The final step to running your app in Office and Outlook is to sideload your updated personal tab [app package](..//concepts/build-and-test/apps-package.md) in Microsoft Teams.

1. Package your Teams application ([manifest](../resources/schema/manifest-schema.md) and [app icons](/microsoftteams/platform/resources/schema/manifest-schema#icons)) in a zip file. If you used Teams Toolkit to create your app, you can easily do this using the **Zip Teams metadata package** option in the **Deployment** menu of Teams Toolkit.

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="'Zip Teams metadata package' option in Teams Toolkit extension for Visual Studio Code":::

1. Sign in to Teams with your sandbox tenant account, and toggle into  *Developer Preview* mode. Select the ellipsis (**...**) menu by your user profile, then select: **About** > **Developer preview**.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="From Teams ellipses menu, open 'About', and select 'Developer Preview' option":::

1. Select **Apps** to open the **Manage your apps** pane. Then select **Publish an app**.

    :::image type="content" source="images/teams-manage-your-apps.png" alt-text="Open the 'Manage your apps' pane and select 'Publish an app'":::

1. Choose **Upload a custom app** option and select your app package.

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="'Upload a custom app' option in Teams":::

After it's sideloaded to Teams, your personal tab is available in Outlook and Office. You must sign in with the same credentials that you used to sideload your app in Teams. When running the Office app for Android, you need to restart the app to use your personal tab app from the Office app.

You can pin the app for quick access, or you can find your app in the ellipses (**...**) flyout among recent applications in the sidebar on the left. Pinning an app in Teams don't pin it as an app in Office or Outlook.

## Preview your personal tab in other Microsoft 365 experiences

Here's how to preview your app running in Office and Outlook, web and Windows desktop clients.

> [!NOTE]
> Uninstalling your app from Teams also removes it from the **More Apps** catalogs in Outlook and Office. If you're using the Teams Toolkit sample app provided above.

### Outlook on Windows

To view your app running in Outlook on Windows desktop:

1. Launch Outlook and sign in using your dev tenant account.
1. On the side bar, select  **More Apps**. Your sideloaded app title appears among your installed apps.
1. Select your app icon to launch your app in Outlook.

    :::image type="content" source="images/outlook-desktop-more-apps.png" alt-text="Click on the ellipses ('More apps') option on the side bar of Outlook desktop client to see your installed personal tabs":::

### Outlook on the web

To view your app in Outlook on the web:

1. Go to [Outlook on the web](https://outlook.office.com) and sign in using your dev tenant account.
1. On the side bar, select  **More Apps**. Your sideloaded app title appears among your installed apps.
1. Select your app icon to launch and preview your app running in Outlook on the web.

    :::image type="content" source="images/outlook-web-more-apps.png" alt-text="Click on the ellipses ('More apps') option on the side bar of outlook.com to see your installed personal tabs":::

### Office on Windows

To view your app running in Office on Windows desktop:

1. Launch Office and sign in using your dev tenant account.
1. Select the **Apps** icon on the side bar. Your sideloaded app title appears among your installed apps.
1. Select your app icon to launch your app in Office.

    :::image type="content" source="images/office-desktop-more-apps.png" alt-text="Click on the ellipses ('More apps') option on the side bar of Office desktop client to see your installed personal tabs":::

### Office on the web

To preview your app running in Office on the web:

1. Log into **office.com** with test tenant credentials.
1. Select the **Apps** icon on the side bar. Your sideloaded app title appears among your installed apps.
1. Select your app icon to launch your app in Office on the web.

    :::image type="content" source="images/office-web-more-apps.png" alt-text="Click on the 'More apps' option on the side bar of office.com to see your installed personal tabs":::

### Office app for Android

> [!NOTE]
> Before installing the app, perform [the steps to install the latest Office app beta build](prerequisites.md#mobile) and be a part of the beta program.

To view your app running in Office app for Android:

1. Launch the Office app and sign in using your dev tenant account. If the Office app for Android was already running prior to sideloading your app in Teams, you'll need to restart it to see it among your installed apps.
1. Select the **Apps** icon. Your sideloaded app appears among installed apps.
1. Select your app icon to launch your app in Office app for Android.

:::image type="content" source="images/office-mobile-apps.png" alt-text="Tap on the 'Apps' option on the side bar of the Office app to see your installed personal tabs":::

## Troubleshooting

Currently, a subset of Teams application types and capabilities is supported in Outlook and Office clients. This support expands over time.

Refer to [Microsoft 365 support](../tabs/how-to/using-teams-client-sdk.md#microsoft-365-support-running-teams-apps-in-office-and-outlook) to check host support for various TeamsJS capabilities.

For an overall summary of Microsoft 365 host and platform support for Teams apps, see [Extend Teams apps across Microsoft 365](overview.md).

You can check for host support of a given capability at runtime by calling the `isSupported()` function on that capability (namespace), and adjusting app behavior as appropriate. This allows your app to light up UI and functionality in hosts that support it and provide a graceful fallback experience in hosts that don't. For more information, see [Differentiate your app experience](../tabs/how-to/using-teams-client-sdk.md#differentiate-your-app-experience).

Use the [Microsoft Teams developer community channels](/microsoftteams/platform/feedback) to report issues and provide feedback.

### Debugging

From Teams Toolkit, you can Debug (`F5`) your tab application running in Office and Outlook, in addition to Teams.

:::image type="content" source="images/toolkit-debug-targets.png" alt-text="Choose from Teams, Outlook, and Office debug targets in Teams Toolkit":::

Upon first run of local debug to Office or Outlook, you'll be prompted to sign in to your Microsoft 365 tenant account and install a self-signed test certificate. You'll also be prompted to manually install Teams. Select **Install in Teams** to open a browser window and manually install your app. Then select **Continue** to proceed to debug your app in Office/Outlook.

:::image type="content" source="images/toolkit-dialog-teams-install.png" alt-text="Toolkit dialog Teams install":::

Provide feedback and report any issues with the Teams Toolkit debugging experience at [Microsoft Teams Framework (TeamsFx)](https://github.com/OfficeDev/TeamsFx/issues).

#### Mobile debugging

Teams Toolkit (`F5`) debugging is not yet supported with Office app for Android. Here's how to remotely debug your app running in Office app for Android:

1. If you debug using a physical Android device, connect it to your dev machine and enable the option for [USB debugging](https://developer.android.com/studio/debug/dev-options). This is enabled by default with the Android emulator.
1. Launch the Office app From your Android device.
1. Open your profile **Me > Settings > Allow debugging**, and toggle on the option for **Enable remote debugging**.

    :::image type="content" source="images/office-android-enable-remote-debugging.png" alt-text="Screenshot showing Enable remote debugging":::

1. Exit **Settings**.
1. Exit your profile screen.
1. Select **Apps** and launch your sideloaded app to run within the Office app.
1. Ensure your Android device is connected to your dev machine. From your dev machine, open your browser to its DevTools inspection page. For example, go to `edge://inspect/#devices` in Microsoft Edge to display a list of debug-enabled Android WebViews.
1. Find the `Microsoft Teams Tab` with your tab URL and select **inspect** to start debugging your app with DevTools.

    :::image type="content" source="images/office-android-debug.png" alt-text="screenshot showing list of webviews in devtool":::

1. Debug your tab app within the Android WebView. In the same way you [remotely debug](/microsoft-edge/devtools-guide-chromium/remote-debugging) a regular website on an Android device.

## Code sample

| **Sample Name** | **Description** | **Node.js** |
|---------------|--------------|--------|
| Todo List | Editable todo list with SSO built with React and Azure Functions. Works only in Teams (use this sample app to try the upgrade process described in this tutorial). | [View](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend)  |
| Todo List (Microsoft 365) | Editable todo list with SSO built with React and Azure Functions. Works in Teams, Outlook, Office. | [View](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend-M365)|
| Image Editor (Microsoft 365) | Create, edit, open, and save images using Microsoft Graph API. Works in Teams, Outlook, Office. | [View](https://github.com/OfficeDev/m365-extensibility-image-editor) |
| Sample Launch Page (Microsoft 365) | Demonstrates SSO authentication and TeamsJS SDK capabilities as available in different hosts. Works in Teams, Outlook, Office. | [View](https://github.com/OfficeDev/microsoft-teams-library-js/tree/main/apps/sample-app) |
| Northwind Orders app | Demonstrates how to use Microsoft TeamsJS SDK V2 to extend teams application to other M365 host apps. Works in Teams, Outlook, Office. Optimized for mobile.| [View](https://github.com/microsoft/app-camp/tree/main/experimental/ExtendTeamsforM365) |

## Next step

Publish your app to be discoverable in Teams, Outlook, and Office:

> [!div class="nextstepaction"]
> [Publish Teams apps for Outlook and Office](publish.md)
