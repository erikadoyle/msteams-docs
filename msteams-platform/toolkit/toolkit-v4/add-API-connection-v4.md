---
title: Integrate existing third-party APIs using Teams Toolkit v4
author: MuyangAmigo
description: Learn how toolkit v4 allows bootstrap sample access to existing APIs. List of different authentication types.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: Overview
ms.date: 05/20/2022
---

# Integrate existing third-party APIs using Teams Toolkit v4

> [!IMPORTANT]
>
> We've introduced the [Teams Toolkit v5](../teams-toolkit-fundamentals.md) extension within Visual Studio Code. This version comes to you with many new app development features. We recommend that you use Teams Toolkit v5 for building your Teams app.
>
> Teams Toolkit v4 extension will soon be deprecated.

Teams Toolkit allows you to access and use existing APIs for building Teams apps. Your organization or a third-party might have developed these APIs. When you use Teams Toolkit to connect to an existing API, Teams Toolkit performs the following functions:

* Generate sample code in the `./bot` or `./api` folder.
* Add a reference to the `@microsoft/teamsfx` package to `package.json`.
* Add app settings for your API in  `.env.teamsfx.local` that configures local debugging.

Teams Toolkit allows you bootstrap sample code to access the APIs, if you don't have language appropriate SDKs to access these APIs.

## Configure API connection

You can add an existing third-party API to your Teams app using:

* [Teams Toolkit](#add-api-connection-using-teams-toolkit)
* [TeamsFx CLI commands](#add-api-connection-using-teamsfx-cli)

### Add API connection using Teams Toolkit

Add a connection to an existing third-party API using the following steps:

1. Open your Teams app project in **Visual Studio Code**.
2. Select **Teams Toolkit** from the Visual Studio Code activity bar.
3. Select **Add features** in the **DEVELOPMENT** section.

    :::image type="content" source="images/api-add-features_1-v4.png" alt-text="api add features":::

     The **Add Feature** dropdown list appears.

4. Select **API Connection**.

    :::image type="content" source="images/api-select-features_1-v4.png" alt-text="api select features":::

5. Enter endpoint for the API, and then press **Enter**.

    Ensure that the endpoint is a valid http(s) URL. Teams Toolkit adds the endpoint to the project's local app settings, and it's the base URL for API requests.

    :::image type="content" source="images/api-endpoint_1-v4.png" alt-text="api endpoint":::

7. Select the component that needs to connect to the API, and then select **OK**.

    :::image type="content" source="images/api-invoke_1-v4.png" alt-text="api invoke":::

9. Enter an alias for the API, and then press **Enter**.

    The alias generates an app setting name for the API. Teams Toolkit adds the alias to the project's local app setting.

    :::image type="content" source="images/api-alias_1-v4.png" alt-text="api alias":::

11. Select the required authentication for the API request from the **API authentication type**.

     :::image type="content" source="images/myAPI connection-v4.png" alt-text="api auth":::

     Teams Toolkit generates appropriate sample code and adds corresponding local application settings based on authentication that you select. To configure authentication:

# [Basic](#tab/basic)

For implementing basic authentication using username and password:

* Select **Basic**.
* Enter the username for basic Auth.

Teams Toolkit generates the sample code to call your API at bot\myAPI.js.

# [Certification](#tab/certification)

* Select **Certification** to authenticate requests using certificates.

Teams Toolkit generates the sample code to call your API at bot\myAPI.js.

# [Microsoft Entra ID](#tab/AAD)

* Select **Microsoft Entra ID** to authenticate requests using Microsoft Entra access tokens.

Teams Toolkit generates the sample code to call your API at bot\myAPI.js.

# [API Key](#tab/apikey)

* Select **API Key** to implement authentication using an API key.
* Select the required API key position in request.
* Enter an API key name.

Teams Toolkit generates the sample code to call your API at bot\myAPI.js.

# [Custom Auth Implementation](#tab/CustomAuthImplementation)

* Select **Custom Auth Implementation** to customize authentication according to your app requirement.

Teams Toolkit generates the sample code to call your API at bot\myAPI.js.

---

You've successfully added a connection in your Teams app to an existing API.

## Add API connection using TeamsFx CLI

The base command of this feature is `teamsfx add api-connection [authentication type]`. The following table provides a list of different authentication types and their corresponding sample commands:

 > [!TIP]
 > You can use `teamsfx add api-connection [authentication type] -h` to get help document.

   |**Authentication type**|**Sample command**|
   |-----------------------|------------------|
   |**Basic**|teamsfx add api-connection basic--endpoint <https://example.com> --component bot--alias example--user-name example user--interactive false|
   |**API Key**|teamsfx add api-connection apikey--endpoint <https://example.com> --component bot--alias example--key-location header--key-name example-key-name--interactive false|
   |**Microsoft Entra ID**|teamsfx add api-connection aad--endpoint <https://example.com> --component bot--alias example--app-type custom--tenant-id your_tenant_id--app-id your_app_id--interactive false|
   |**Certificate**|teamsfx add api-connection cert--endpoint <https://example.com> --component bot--alias example--interactive false|
   |**Custom**|teamsfx add api-connection custom--endpoint <https://example.com> --component bot--alias example--interactive false|

---

## Directory structure updates to your project

 Teams Toolkit modifies `bot` or `api` folder based on your selection:

1. Generate `{your_api_alias}.js\ts` file. The file initializes an API client for your API and exports the API client.

2. Add `@microsoft\teamsfx` package to `package.json`. The package provides support for the common API authentication methods.

3. Add environment variables to `.env.teamsfx.local`. You must configure environment variables for the selected authentication type. The generated code reads values from the environment variables.

## See also

* [Teams Toolkit Overview](../teams-toolkit-fundamentals.md)
* [Publish Teams apps using Teams Toolkit](publish-v4.md)
