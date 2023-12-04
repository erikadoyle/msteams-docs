---
title: Edit Microsoft Entra manifest in Teams Toolkit v4
author: zyxiaoyuer
description: In this module, learn how to edit, customize, and preview the Microsoft Entra manifest with CodeLens in Teams Toolkit v4.
ms.author: surbhigupta
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/20/2022
---

# Edit Microsoft Entra manifest in Teams Toolkit v4

> [!IMPORTANT]
>
> We've introduced the [Teams Toolkit v5](../teams-toolkit-fundamentals.md) extension within Visual Studio Code. This version comes to you with many new app development features. We recommend that you use Teams Toolkit v5 for building your Teams app.
>
> Teams Toolkit v4 extension will soon be deprecated.

The Microsoft Entra manifest contain definitions of all the attributes of a Microsoft Entra application object in the Microsoft identity platform.

Teams Toolkit now manages Microsoft Entra application with the manifest file as the source of truth during your Teams application development lifecycle.

<a name='customize-azure-ad-manifest-template'></a>

## Customize Microsoft Entra manifest template

You can customize Microsoft Entra manifest template to update Microsoft Entra application.

1. Open `aad.template.json` in your project.
  
     :::image type="content" source="images/add template-v4.png" alt-text="template":::

2. Update the template directly or [reference values from another file](https://github.com/OfficeDev/TeamsFx/wiki/Manage-AAD-application-in-Teams-Toolkit#Placeholders-in-AAD-manifest-template). Following are the customization scenarios:
  
    <details>

    <summary>Add an application permission</summary>

     If the Teams application requires more permissions to call an API with additional permissions, you need to update `requiredResourceAccess` property in the Microsoft Entra manifest template. You can see the following example for this property:

    ```JSON
            "requiredResourceAccess": [
    {
            "resourceAppId": "Microsoft Graph",
            "resourceAccess": [
                {
                    "id": "User.Read", // For Microsoft Graph API, you can also use uuid for permission id
                    "type": "Scope" // Scope is for delegated permission
                },
                {
                    "id": "User.Export.All",
                    "type": "Role" // Role is for application permission
                }
            ]
        },
        {
            "resourceAppId": "Office 365 SharePoint Online",
            "resourceAccess": [
                {
                        "id": "AllSites.Read",
                "type": "Scope"
                }
            ]
        }
    ]

    ```

    The following permissions are used property IDs:

    - The `resourceAppId` property is used for different APIs. For `Microsoft Graph`, and `Office 365 SharePoint Online` enter the name directly instead of UUID, and for other APIs use UUID.

    - The `resourceAccess.id` property is used for different permissions. For `Microsoft Graph`, and `Office 365 SharePoint Online` enter the permission name directly instead of UUID, and for other APIs use UUID.

    - The `resourceAccess.type` property is used for delegated permission or application permission. `Scope` means delegated permission and `Role` means application permission.

    </details>

    <details>

    <summary>Pre-authorize a client application</summary>

     You can use `preAuthorizedApplications` property to authorize a client application to indicate that the API trusts the application. Users don't consent when the client calls it exposed API. You can see the following example for this property:

     ```JSON

           "preAuthorizedApplications": [
           {
               "appId": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
               "permissionIds": [
                    "{{state.fx-resource-aad-app-for-teams.oauth2PermissionScopeId}}"
                ]
           }
           ...
       ]
     ```

     `preAuthorizedApplications.appId` property is used for the application you want to authorize. If you don't know the application ID and know only the application name, use the following steps to search application ID:

     1. Go to [Azure portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps) and open **Application Registrations**.

     1. Select **All applications** and search for the application name.

     1. Select the application name and get the application ID from the overview page.

    </details>

    <details>

    <summary>Update redirect URL for authentication response</summary>

     Redirect URLs are used while returning authentication responses such as tokens after successful authentication. You can customize redirect URLs using property `replyUrlsWithType`. For example, to add `https://www.examples.com/auth-end.html` as redirect URL, you can add it as the following example:

      ``` JSON
          "replyUrlsWithType": [
             ...
           {
               "url": "https://www.examples.com/auth-end.html",
               "type": "Spa"
           }
      ]
      ```

    </details>

<details>
<summary>3. Deploy Microsoft Entra application changes for local environment</summary>

   1. Select `Preview` CodeLens in `aad.template.json`.
  
      :::image type="content" source="images/add deploy1-v4.png" alt-text="deploy1":::

   2. Select **local** environment.
  
      :::image type="content" source="images/add deploy2-v4.png" alt-text="deploy2":::

   3. Select `Deploy Azure AD Manifest` CodeLens in `aad.local.json`.

      :::image type="content" source="images/add deploy3-v4.png" alt-text="deploy3" lightbox="images/add deploy3-v4.png":::

   4. The changes for Microsoft Entra application used in local environment are deployed.

</details>

<details>

<summary>4. Deploy Microsoft Entra application changes for remote environment</summary>

- Open the command palette and select: **Teams: Deploy Microsoft Entra app manifest**.
  
     :::image type="content" source="images/add deploy4-v4.png" alt-text="deploy4":::

- Additionally you can right click on the `aad.template.json` and select **Deploy Microsoft Entra app manifest** from the context menu.
  
    :::image type="content" source="images/add deploy5-v4.png" alt-text="deploy5":::

</details>

<a name='azure-ad-manifest-template-placeholders'></a>

## Microsoft Entra manifest template placeholders

The Microsoft Entra manifest file contains placeholder arguments with {{...}} statements, it's replaced during build for different environments. You can build references to config file, state file, and environment variables with the placeholder arguments.

<a name='reference-state-file-values-in-azure-ad-manifest-template'></a>

### Reference state file values in Microsoft Entra manifest template

The state file is located in `.fx\states\state.xxx.json`. The following example shows state file:

``` JSON
{
    "solution": {
        "teamsAppTenantId": "uuid",
        ...
    },
    "fx-resource-aad-app-for-teams": {
        "applicationIdUris": "api://xxx.com/uuid",
        ...
    }
    ...
}
```

> [!NOTE]
> xxx represents different environment.

You can use this placeholder argument in the Microsoft Entra manifest. `{{state.fx-resource-aad-app-for-teams.applicationIdUris}}` to point out `applicationIdUris` value in `fx-resource-aad-app-for-teams` property.

<a name='reference-config-file-values-in-azure-ad-manifest-template'></a>

### Reference config file values in Microsoft Entra manifest template

The following config file is located in `.fx\configs\config.xxx.json`:

``` JSON
{
  "$schema": "https://aka.ms/teamsfx-env-config-schema",
  "description": "description.",
  "manifest": {
    "appName": {
      "short": "app",
      "full": "Full name for app"
    }
  }
}
```

You can use the placeholder argument in the Microsoft Entra manifest `{{config.manifest.appName.short}}` to refer `short` value.

<a name='reference-environment-variable-in-azure-ad-manifest-template'></a>

### Reference environment variable in Microsoft Entra manifest template

When the value is a secret, you don't need to enter permanent values in Microsoft Entra manifest template. Microsoft Entra manifest template file supports reference environment variables values. You can use the syntax `{{env.YOUR_ENV_VARIABLE_NAME}}` in the tool as parameter values to resolve the current environment variable values.

<a name='edit-and-preview-azure-ad-manifest-with-codelens'></a>

## Edit and preview Microsoft Entra manifest with CodeLens

Microsoft Entra manifest template file has CodeLens to review and edit the code.

:::image type="content" source="images/preview view-v4.png" alt-text="previewview":::

<a name='azure-ad-manifest-template-file'></a>

### Microsoft Entra manifest template file

There's a preview CodeLens at the beginning of the Microsoft Entra manifest template file. Select the CodeLens to generate a Microsoft Entra manifest based as per your environment.

:::image type="content" source="images/add codelens-v4.png" alt-text="addcodelens":::

### Placeholder argument CodeLens

Placeholder argument CodeLens helps you to see the values for local debug and develop your environment. If you hover the mouse on the placeholder argument, it shows tooltip box for the values of all the environments.

:::image type="content" source="images/add arguments-v4.png" alt-text="addarguments":::

### Required resource access CodeLens

Microsoft Entra manifest template in Teams Toolkit also supports user readable strings for `Microsoft Graph` and `Office 365 SharePoint Online` permissions. The official [Microsoft Entra manifest schema](/azure/active-directory/develop/reference-app-manifest), which is the `resourceAppId` and `resourceAccess` in `requiredResourceAccess` property supports only the UUID. If you enter UUID, the CodeLens shows user readable strings, otherwise it shows the UUID.

:::image type="content" source="images/add resource-v4.png" alt-text="add resource to required resource access":::

### Pre-authorized applications CodeLens

CodeLens shows the application name for the pre-authorized application ID for the `preAuthorizedApplications` property.

<a name='view-azure-ad-application-on-the-azure-portal'></a>

## View Microsoft Entra application on the Azure portal

1. Copy the Microsoft Entra application client ID from `state.xxx.json` () file in the `fx-resource-aad-app-for-teams` property.
  
     :::image type="content" source="images/add view1-v4.png" alt-text="view1" lightbox="images/add view1-v4.png":::

   > [!NOTE]
   > xxx in the client ID indicates the environment name where you have deployed the Microsoft Entra application.

2. Go to [Azure portal](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps) and sign in to Microsoft 365 account.
  
   > [!NOTE]
   > Ensure that login credentials of Teams application and M365 account are the same.

3. Open [App Registrations page](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps), and search the Microsoft Entra application using client ID that you copied before.
  
     :::image type="content" source="images/add view2-v4.png" alt-text="view2":::

4. Select Microsoft Entra application from search result to view the detail information.
  
5. In Microsoft Entra app information page, select the `Manifest` menu to view manifest of this application. The schema of the manifest is same as the one in `aad.template.json` file. For more information about manifest, see [Microsoft Entra app manifest](/azure/active-directory/develop/reference-app-manifest).
  
     :::image type="content" source="images/add view3-v4.png" alt-text="view3":::

6. You can select **Other Menu** to view or configure Microsoft Entra application through its portal.
  
<a name='use-an-existing-azure-ad-application'></a>

## Use an existing Microsoft Entra application

You can use the existing Microsoft Entra application for the Teams project. For more information, see [use an existing Microsoft Entra application for your Teams application](https://github.com/OfficeDev/TeamsFx/wiki/Customize-provision-behaviors#use-an-existing-aad-app-for-your-teams-app).

<a name='azure-ad-application-in-teams-application-development-lifecycle'></a>

## Microsoft Entra application in Teams application development lifecycle

You need to interact with Microsoft Entra application during various stages of your Teams application development lifecycle.

1. **To create Project**

      You can create a project with Teams Toolkit that comes with single sign-on (SSO) support by default such as `SSO-enabled tab`. For more information on how to create a new app, see [Create a new Teams app](../create-new-project.md). A Microsoft Entra manifest file is automatically created for you in `templates\appPackage\aad.template.json`. Teams Toolkit creates or updates the Microsoft Entra application during local development or while you move the application to the cloud.

2. **To add SSO to your Bot or Tab**

      After you create a Teams application without built-in SSO, Teams Toolkit progressively helps you to add SSO for the project. As a result, a Microsoft Entra manifest file is automatically created for you in `templates\appPackage\aad.template.json`.

      Teams Toolkit creates or updates the Microsoft Entra application during next local development session or while you move the application to the cloud.

3. **To build Locally**

    Teams Toolkit performs the following functions during local development:

    - Read the `state.local.json` file to find an existing Microsoft Entra application. If a Microsoft Entra application already exists, Teams Toolkit reuses the existing Microsoft Entra application. Otherwise you need to create a new application using the `aad.template.json` file.

    - Initially ignores some properties in the manifest file that requires more context, such as `replyUrls` property that requires a local development endpoint during the creation of a new Microsoft Entra application with the manifest file.

    - After the local dev environment starts successfully, the Microsoft Entra application's `identifierUris`, `replyUrls`, and other properties that aren't available during creation stage are updated accordingly.

    - The changes you've done to your Microsoft Entra application are loaded during next local development session. You can see [Microsoft Entra application changes](https://github.com/OfficeDev/TeamsFx/wiki/) applied manually.

4. **To provision for cloud resources**

      You need to provision cloud resources and deploy your application while moving your application to the cloud. At stages, such as local debug, Teams Toolkit:

      - Reads the `state.{env}.json` file to find an existing Microsoft Entra application. If a Microsoft Entra application already exists, Teams Toolkit re-uses the existing Microsoft Entra application. Otherwise you need to create a new application using the `aad.template.json` file.

      - Ignores some properties in the manifest file initially that requires more context such as `replyUrls` property. This property requires frontend or bot endpoint during the creation of a new Microsoft Entra application with the manifest file.

      - Completes other resources provision, then Microsoft Entra application's `identifierUris`, and `replyUrls` are updated according to the correct endpoints.

5. **To build application**

    - The cloud command deploys your application to the provisioned resources. It doesn't include deploying Microsoft Entra application changes you've made.

    - Teams Toolkit updates the Microsoft Entra application according to the Microsoft Entra manifest template file.

## Limitations

1. Teams Toolkit extension doesn't support all the properties listed in Microsoft Entra manifest schema.
  
      The following table lists the properties that aren't supported in Teams Toolkit extension:

      |**Not supported properties**|**Reason**|
      |-----------|----------|
      |`passwordCredentials`|Not allowed in manifest|
      |`createdDateTime`|Read-only and can't change|
      |`logoUrl`|Read-only and can't change|
      |`publisherDomain`|Read-only and can't change|
      |`oauth2RequirePostResponse`|Doesn't exist in Graph API|
      |`oauth2AllowUrlPathMatching`|Doesn't exist in Graph API|
      |`samlMetadataUrl`|Doesn't exist in Graph API|
      |`orgRestrictions`|Doesn't exist in Graph API|
      |`certification`|Doesn't exist in Graph API|

2. Currently `requiredResourceAccess` property is used for user readable resource application name or permission name strings only for `Microsoft Graph` and `Office 365 SharePoint Online` APIs. You need to use UUID for other APIs. Perform the following steps to retrieve IDs from Azure portal:

    - Register a new Microsoft Entra application on [Azure portal](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps).
    - Select `API permissions` from the Microsoft Entra application page.
    - Select `add a permission` to add the permission you need.
    - Select `Manifest`, from the `requiredResourceAccess` property, where you can find the IDs of API, and the permissions.

## See also

- [Teams Toolkit Overview](../teams-toolkit-fundamentals.md)
- [Microsoft Entra manifest](/azure/active-directory/develop/reference-app-manifest)
- [Customize Teams app manifest](../TeamsFx-preview-and-customize-app-manifest.md)
- [Debug your Teams app](../debug-overview.md)
- [Debug your Teams app locally](../debug-local.md)
