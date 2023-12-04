---
title: Debug your Teams app locally
author: surbhigupta 
description: In this module, learn how to debug your Teams app locally in Teams Toolkit.
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/21/2022
zone_pivot_groups: teams-toolkit-platform
---

# Debug your Teams app locally

Teams Toolkit helps you to debug and preview your Microsoft Teams app locally. During the debug process, Teams Toolkit automatically starts app services, launches debuggers, and uploads Teams app. You can preview your Teams app in Teams web client locally after debugging.

::: zone pivot="visual-studio-code-v5"

## Debug your Teams app locally for Visual Studio Code

Teams Toolkit in Microsoft Visual Studio Code gives you the features to automate debugging of your Teams app locally. Visual Studio Code allows you to debug tab, bot, and message extension. You need to set up Teams Toolkit before you debug your app.

> [!NOTE]
> Your old Teams Toolkit project gets upgraded to use new tasks, for more information, see [tasks doc](https://aka.ms/teamsfx-tasks).

## Set up your Teams Toolkit for debugging

The following steps help you set up your Teams Toolkit before you initiate the debug process:

# [Windows](#tab/Windows)

1. Select **Debug (Edge)** or **Debug (Chrome)** from the **RUN AND DEBUG ▷** drop down.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/debug-run.png" alt-text="Screenshot shows the Browser option.":::

1. Select **Run** > **Start Debugging (F5)**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/start-debugging.png" alt-text="Screenshot shows the Start debugging option.":::

3. Select **Create a Microsoft 365 Testing Tenant** to Microsoft 365 account.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/microsoft365-signin.png" alt-text="Screenshot shows the Sign in option highlighted.":::

   > [!TIP]
   > You can select **Create a Microsoft 365 Testing Tenant** to learn about Microsoft 365 Developer Program. Your default web browser opens to let you sign in to your Microsoft 365 account with your credentials.

4. Select **Install** to install the development certificate for localhost.

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/install-certificate.png" alt-text="Screenshot shows the certificate to install.":::

   > [!TIP]
   > You can select **Learn More** to know about the development certificate.

5. Select **Yes** in the **Security Warning** dialog.

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/development-certificate.png" alt-text="Screenshot shows the certification authority to install the certificate.":::

Toolkit launches a new Microsoft Edge or Chrome browser instance based on your selection and opens a web page to load Teams client.  

# [macOS](#tab/macOS)

1. Select **Debug Edge** or **Debug Chrome** from the **RUN AND DEBUG ▷** drop down.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/debug-run.png" alt-text="Screenshot shows the Browser lists.":::

1. Select **Start Debugging (F5)** or  **Run** to run your Teams app in debug mode.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/start-debugging.png" alt-text="Screenshot shows the Debug option.":::

3. Select **Sign in**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/microsoft365-signin.png" alt-text="Screenshot shows the Sign in option highlighted in the dialog.":::

   > [!TIP]
   > You can select **Create a Microsoft 365 Testing Tenant** to learn about Microsoft 365 Developer Program. Your default web browser opens to let you sign in to your Microsoft 365 account using your credentials.

4. Select **Install** to install the development certificate for localhost.

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/install-certificate.png" alt-text="Screenshot shows the dialog to Install the certificate.":::

   > [!TIP]
   > You can select **Learn More** to know about the development certificate.

5. Enter your **User Name** and **Password**, then select **Update Settings**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/mac-settings.png" alt-text="Screenshot shows the mac sign in dialog.":::

Teams Toolkit launches your browser instance and opens a webpage to load Teams client.

---

## Debug your app

After the initial setup process, Teams Toolkit starts the following processes:

* [Starts app services](#starts-app-services)
* [Launches debug configurations](#launches-debug-configurations)
* [Uploads the Teams app](#uploads-the-teams-app)

### Starts app services

Runs tasks as defined in `.vscode/tasks.json`. By default, the task name is `"Start application"`. If your project contains more than one component, there'll be more dependent tasks.

```JSON
// .vscode/tasks.json
{
    "label": "Start application",
    "dependsOn": [
        "Start Frontend", // Tab
        "Start Backend", // Azure Functions
        "Start Bot" // Bot or message extensions
    ]
}

```

The following image displays task names in the **OUTPUT** and **TERMINAL** tabs of the Visual Studio Code while running tab, bot or message extension, and Azure Functions.

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/Terminal1.png" alt-text="Screenshot shows the Start app services." lightbox="../assets/images/teams-toolkit-v2/debug/Terminal1.png":::

### Start local tunnel

Use dev tunnel as a local tunnel service to make your local bot message endpoint public.

#### Dev tunnel

To manually migrate your local tunnel task from a v4 project, update the following code in the `.vscode/tasks.json` file:

```json
{
      "label": "Start local tunnel",
      "type": "teamsfx",
      "command": "debug-start-local-tunnel",
      "args": {
          "type": "dev-tunnel",
          "ports": [
              {
                  "portNumber": 3978,
                  "protocol": "http",
                  "access": "public",
                  "writeToEnvironmentFile": {
                      "endpoint": "BOT_ENDPOINT",
                      "domain": "BOT_DOMAIN"
                  }
              }
        ],
          "env": "local"
      },
      "isBackground": true,
      "problemMatcher": "$teamsfx-local-tunnel-watch"
    },
```

To use another port for local bot service, change the `portNumber` in the `.vscode/tasks.json` file and also change the `portNumber` in the `index.js` or `index.ts` file.

The following table lists the required arguments:

| **Arguments** | **Type** | **Required** | **Description** |
| --- | --- | --- |--------|
| `type` | string | required | The type of tunnel service to use. This argument must be set to `dev-tunnel`. |
| `env` | string | optional | The environment name. Teams Toolkit writes the environment variables defined in `output` to `.env.<env>` file. |
| `ports` | array | required | An array of port configurations, each specifying the local port number, protocol, and access control settings. |

The `ports` argument must be an array of objects, with each object specifying the configuration for a particular port. Each object must contain the following fields:

| **Port** | **Type** | **Required** | **Description**|
|---|---|---|------|
| `portNumber` | number | required | The local port number of the tunnel. |
| `protocol` | string | required | The protocol of the tunnel. |
| `access` | string | optional | The access control setting for the tunnel. This value can be set to `private` or `public`. If not specified, the default value is `private`.|
 | `writeToEnvironmentFile` | object | optional | The key of tunnel endpoint and tunnel domain environment variables that are written to `.env` file.|

The `writeToEnvironmentFile` object contains two fields:

| **WriteToEnvironmentFile** | **Type** | **Required** | **Description** |
|-----|---|---|------|
| `endpoint` | string | optional | The key of tunnel endpoint environment variable.|
| `domain` | string | optional | The key of tunnel domain environment variable.|

When `writeToEnvironmentFile` is included, the specified environment variables are written to the `.env` file. When the field is omitted, no environment variables are written to the file.

### Launches debug configurations

Launches the debug configurations as defined in `.vscode/launch.json`.

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/launch-debuggers.png" alt-text="Screenshot shows the Launch debugger.":::

The following table lists the debug configuration names and types for project with tab, bot or message extension app, and Azure Functions:

|  Component |  Debug configuration name  | Debug configuration type |
| --- | --- | --- |
|  Tab |  **Attach to Frontend (Edge)** or  **Attach to Frontend (Chrome)**  |  msedge or chrome  |
|  Bot or message extensions |   **Attach to Bot** |  node |
| Azure Functions |   **Attach to Backend** |  node |

The following table lists the debug configuration names and types for project with bot app, Azure Functions, and without tab app:

|  Component | Debug configuration name | Debug configuration type |
| --- | --- | --- |
|  Bot or message extension  | **Launch Bot (Edge)** or  **Launch Bot (Chrome)**  |   msedge or chrome  |
|  Bot or message extension  |   **Attach to Bot** |  node  |
|  Azure Functions |  **Attach to Backend** |  node |

### Uploads the Teams app

The configuration **Attach to Frontend** or **Launch App** launches Microsoft Edge or Chrome browser instance to load Teams client in web page. After the Teams client is loaded, upload Teams app that is controlled by the uploading URL defined in the launch configurations [Microsoft Teams](https://teams.microsoft.com/l/app/>${localTeamsAppId}?installAppPackage=true&webjoin=true&${account-hint}). When Teams client loads in the web browser, select **Add** or select an option from the dropdown as per your requirement.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/hello-local-debug.png" alt-text="Screenshot shows the Add local debug." lightbox="../assets/images/teams-toolkit-v2/debug/hello-local-debug.png":::

   Your app is added to Teams!

## Next step

> [!div class="nextstepaction"]
> [Debug background process](debug-background-process.md)

## See also

* [Teams Toolkit Overview](teams-toolkit-fundamentals.md)
* [Introduction to Azure Functions](/azure/azure-functions/functions-overview)
* [Use Teams Toolkit to provision cloud resources](provision.md)
* [Add capabilities to your Teams apps](toolkit-v4/add-capability-v4.md)
* [Deploy to the cloud](deploy.md)
* [Manage multiple environments in Teams Toolkit](TeamsFx-multi-env.md)

::: zone-end

::: zone pivot="visual-studio-code-v4"

> [!IMPORTANT]
>
> We've introduced the [Teams Toolkit v5](/microsoftteams/platform/toolkit/teams-toolkit-fundamentals?pivots=visual-studio-code-v5) extension within Visual Studio Code. This version comes to you with many new app development features. We recommend that you use Teams Toolkit v5 for building your Teams app.
>
> Teams Toolkit v4 extension will soon be deprecated.

Teams Toolkit helps you to debug and preview your Microsoft Teams app locally. During the debug process, Teams Toolkit automatically starts app services, launches debuggers, and side-loads the Teams app. You can preview your Teams app in Teams web client locally after debugging.

## Debug your Teams app locally for Visual Studio Code

Teams Toolkit in Microsoft Visual Studio Code gives you the features to automate debugging of your Teams app locally. Visual Studio Code allows you to debug tab, bot, and message extension. You need to set up Teams Toolkit before you debug your app.

> [!NOTE]
> You can upgrade your old Teams Toolkit project to use new tasks, for more information, see [debug settings doc](https://aka.ms/teamsfx-debug-upgrade-new-tasks)

## Set up your Teams Toolkit for debugging

The following steps help you set up your Teams Toolkit before you initiate the debug process:

# [Windows](#tab/Windows)

1. Select **Debug (Edge)** or **Debug (Chrome)** from the **RUN AND DEBUG ▷** drop down.

   :::image type="content" source="toolkit-v4/images/debug-run-v4.png" alt-text="Browser option":::

1. Select **Run** > **Start Debugging (F5)**.

   :::image type="content" source="toolkit-v4/images/start-debugging-v4.png" alt-text="Start debugging":::

3. Select **Sign in** to Microsoft 365 account.

   :::image type="content" source="toolkit-v4/images/microsoft365-signin-v4.PNG" alt-text="Sign in":::

   > [!TIP]
   > You can select **Read more** to learn about Microsoft 365 Developer Program. Your default web browser opens to let you sign-in to your Microsoft 365 account with your credentials.

4. Select **Install** to install the development certificate for localhost.

    :::image type="content" source="toolkit-v4/images/install-certificate-v4.PNG" alt-text="certificate":::

   > [!TIP]
   > You can select **Learn More** to know about the development certificate.

5. Select **Yes** in the **Security Warning** dialog box:

    :::image type="content" source="toolkit-v4/images/development-certificate-v4.PNG" alt-text="certification authority":::

Toolkit launches a new Microsoft Edge or Chrome browser instance based on your selection and opens a web page to load Teams client.  

# [macOS](#tab/macOS)

1. Select **Debug Edge** or **Debug Chrome** from the **RUN AND DEBUG ▷** drop down.

   :::image type="content" source="toolkit-v4/images/debug-run-v4.png" alt-text="Browser lists":::

1. Select **Start Debugging (F5)** or  **Run** to run your Teams app in debug mode.

   :::image type="content" source="toolkit-v4/images/start-debugging-v4.png" alt-text="Debug your app":::

3. Select **Sign in** to Microsoft 365 account.

   :::image type="content" source="toolkit-v4/images/microsoft365-signin-v4.PNG" alt-text="Sign into M365 account":::

   > [!TIP]
   > You can select **Read more** to learn about Microsoft 365 Developer Program. Your default web browser opens to let you sign-in to your Microsoft 365 account using your credentials.

4. Select **Install** to install the development certificate for localhost.

    :::image type="content" source="toolkit-v4/images/install-certificate-v4.PNG" alt-text="certificate":::

   > [!TIP]
   > You can select **Learn More** to know about the development certificate.

5. Enter your **User Name** and **Password**, then select **Update Settings**.

    :::image type="content" source="toolkit-v4/images/mac-settings-v4.png" alt-text="mac sign in":::

Teams Toolkit launches your browser instance and opens a web page to load Teams client.

---

## Debug your app

After the initial setup process, Teams Toolkit starts the following processes:

* [Starts app services](#starts-app-services)
* [Launches debug configurations](#launches-debug-configurations)
* [Uploads the Teams app](#uploads-the-teams-app)

### Starts app services

Runs tasks as defined in `.vscode/tasks.json`.

|  Component |  Task name  | Folder |
| --- | --- | --- |
|  Tab |  **Start Frontend** |  tabs |
|  Bot or message extensions |  **Start Bot** |  bot |
|  Azure Functions |  **Start Backend** |  API |

The following image displays task names in the **OUTPUT** and **TERMINAL** tabs of the Visual Studio Code while running tab, bot or message extension, and Azure Functions.

:::image type="content" source="toolkit-v4/images/Terminal1-v4.png" alt-text="Start app services" lightbox="toolkit-v4/images/Terminal1-v4.png":::

### Launches debug configurations

Launches the debug configurations as defined in `.vscode/launch.json`.

:::image type="content" source="toolkit-v4/images/launch-debuggers-v4.png" alt-text="Launch debugger":::

The following table lists the debug configuration names and types for project with tab, bot or message extension app, and Azure Functions:

|  Component |  Debug configuration name  | Debug configuration type |
| --- | --- | --- |
|  Tab |  **Attach to Frontend (Edge)** or  **Attach to Frontend (Chrome)**  |  pwa-msedge or pwa-chrome  |
|  Bot or message extensions |   **Attach to Bot** |  pwa-node |
| Azure Functions |   **Attach to Backend** |  pwa-node |

The following table lists the debug configuration names and types for project with bot app, Azure Functions and without tab app:

|  Component |  Debug configuration name  | Debug configuration type  |
| --- | --- | --- |
|  Bot or message extension  | **Launch Bot (Edge)** or  **Launch Bot (Chrome)**  |   pwa-msedge or pwa-chrome  |
|  Bot or message extension  |   **Attach to Bot** |  pwa-node  |
|  Azure Functions |  **Attach to Backend** |  pwa-node |

### Uploads the Teams app

The configuration **Attach to Frontend** or **Launch Bot** launches Microsoft Edge or Chrome browser instance to load Teams client in web page. After the Teams client is loaded, Teams uploads the custom app that is controlled by the uploading URL defined in the launch configurations [Microsoft Teams](https://teams.microsoft.com/l/app/>${localTeamsAppId}?installAppPackage=true&webjoin=true&${account-hint}). When Teams client loads in the web browser, select **Add** or select an option from the dropdown as per your requirement.

   :::image type="content" source="toolkit-v4/images/hello-local-debug-v4.png" alt-text="Add local debug" lightbox="toolkit-v4/images/hello-local-debug-v4.png":::

   Your app is added to Teams!

## Next step

> [!div class="nextstepaction"]
> [Debug background process](debug-background-process.md)

## See also

* [Teams Toolkit Overview](teams-toolkit-fundamentals.md)
* [Introduction to Azure Functions](/azure/azure-functions/functions-overview)
* [Use Teams Toolkit to provision cloud resources](provision.md)
* [Add capabilities of Teams Toolkit v4 to Microsoft Teams app](toolkit-v4/add-capability-v4.md)
* [Manage multiple environments in Teams Toolkit](TeamsFx-multi-env.md)

::: zone-end
