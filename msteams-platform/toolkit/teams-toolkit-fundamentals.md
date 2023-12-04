---
title: Teams Toolkit Overview
author: zyxiaoyuer
description: Learn about Teams Toolkit, it's installation, navigation, and user journey. Teams Toolkit is available for Visual Studio code.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/24/2022
zone_pivot_groups: teams-toolkit-platform
---
# Teams Toolkit Overview

> [!IMPORTANT]
>
> * We've introduced the Teams Toolkit v5 extension within Visual Studio Code. This version comes to you with many new app development features. We recommend that you use Teams Toolkit v5 for building your Teams app.
> * Teams Toolkit isn't supported in Government Community Cloud (GCC) and GCC-High environments.
> * Teams Toolkit v4 extension will soon be deprecated.

::: zone pivot="visual-studio-code-v5"

Teams Toolkit makes it simple to get started with app development for Microsoft Teams using Visual Studio Code.

* Start with a project template for common custom app built for your org (LOB app) scenarios or from a sample.
* Save setup time with automated app registration and configuration.
* Run and debug to Teams directly from familiar tools.
* Smart defaults for hosting in Azure using infrastructure-as-code and Bicep.
* Create unique configurations like dev, test, and prod using the environment features.

> [!NOTE]
> Before you get started, we strongly recommend that you visit [Teams Toolkit v5 Guide](https://aka.ms/teamsfx-v5.0-guide) to learn key features, such as life cycles and actions.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey2.png" alt-text="Illustration shows the User Journey of the Teams Toolkit." lightbox="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey2.png":::

## Available for Visual Studio Code

Teams Toolkit is available for free for Visual Studio Code. For more information about installation and set up, see [Install Teams Toolkit](install-Teams-Toolkit.md).

| Teams Toolkit | Visual Studio Code |
| - | ------------------ |
| Installation | Available in the VS Code Marketplace |
| Build with | JavaScript, TypeScript, React, SPFx |

## Version Mapping

The following table list out the version support for the Teams Toolkit extension for each release cycle:

| &nbsp; | Teams Toolkit for Visual Studio Code|Teams Toolkit for Visual Studio| Teams Toolkit CLI | TeamsFx SDK |Teams SDK|Manifest|
|----|----|----|----|----|----|----|
|Public Preview|v3.8.x|v17.2|v0.14.x|v0.7.x|v1.11.x, v1.12.x|v1.11|
|GA|v4.0.0|v17.3|v1.0.0|v1.0.0|v1.12.x|v1.11|
|Latest*|v5.x.x|v17.6|-|v2.x.x|v2.x.x|v1.16|
|Beta**|Prerelease|v17.7 Preview|v2.x.x-beta|v2.x.x-beta|v2.x.x-beta|Dev preview|

*Latest is aligned on the major version.<br>
**Beta indicates developer preview.

## Features

The following list provides the key features of Teams Toolkit:

* [Project templates](#project-templates)
* [Automatic registration and configuration](#automatic-registration-and-configuration)
* [Multiple environments](#multiple-environments)
* [Quick access to Teams Developer Portal](#quick-access-to-teams-developer-portal)

### Project templates

You can start directly with the capability-focused templates such as tabs, bots, and message extensions or by following the existing samples if you're already familiar with Teams app development. Teams Toolkit reduces the complexity of getting started with the help of templates for common custom app built for your org (LOB app) scenarios and smart defaults to accelerate your time to production.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/create-new-app_2.png" alt-text="Screenshot shows the create new Teams app menu in Visual Studio Code.":::

### Automatic registration and configuration

You can save time and let the toolkit automatically register the app in Teams Developer Portal. When you first run or debug the app, Teams Toolkit automatically registers the Teams app to your Microsoft 365 tenant and configures settings such as Microsoft Entra ID for your Teams app. Sign in with your Microsoft 365 account to control where the app is configured and customize the included Microsoft Entra manifest when you need flexibility.

### Multiple environments

You can create different groupings of cloud resources to run and test your app. Use the **dev** environment with your Azure subscription or create a new app with a different subscription for staging, test, and production.

### Quick access to Teams Developer Portal

You can access Teams Developer Portal where you can configure, distribute, and manage your app. For more information, see [manage your Teams apps using Developer Portal](../concepts/build-and-test/manage-your-apps-in-developer-portal.md).

:::image type="content" source="../assets/images/teams-toolkit-v2/build-environment-developer-portal-2.png" alt-text="Screenshot shows the Developer Portal option.":::

## See also

[Install Teams Toolkit](install-Teams-Toolkit.md)

::: zone-end

::: zone pivot="visual-studio-code-v4"

Teams Toolkit makes it simple to get started with app development for Microsoft Teams using Visual Studio Code.

* Start with a project templates for common custom app built for your org (LOB app) scenarios or from a sample.
* Save setup time with automated app registration and configuration.
* Run and debug to Teams directly from familiar tools.
* Smart defaults for hosting in Azure using infrastructure-as-code and Bicep.
* Create unique configurations like dev, test, and prod using the environments feature.
* Bring your app to your organization or the Microsoft Teams Store using built-in publishing tools.

:::image type="content" source="toolkit-v4/images/teams-toolkit-user-journey3VS-v4.png" alt-text="User Journey of the Teams Toolkit."  lightbox="toolkit-v4/images/teams-toolkit-user-journey3VS-v4.png":::

## Available for Visual Studio Code

Teams Toolkit v4 is available for free for Visual Studio Code. For more information about installation and setup, see [install Teams Toolkit](~/toolkit/install-teams-toolkit.md).

| Teams Toolkit | Visual Studio Code |
| - | ------------------ |
| Installation | Available in the VS Code Marketplace |
| Build with | JavaScript, TypeScript, React, SPFx |

## Version Mapping

The Teams Toolkit lifecycle and support policy covers Generally available (GA) and future versions.

| &nbsp; | Teams Toolkit for Visual Studio Code|Teams Toolkit for Visual Studio| Teams Toolkit CLI | TeamsFx SDK |Teams SDK|Manifest|
|----|----|----|----|----|----|----|
|Public Preview|v3.8.x|v17.2|v0.14.x|v0.7.x|v1.11.x, v1.12.x|v1.11|
|GA|v4.0.0|v17.3|v1.0.0|v1.0.0|v1.12.x|v1.11|
|Latest*|v5.x.x|v17.6|-|v2.x.x|v2.x.x|v1.16|
|Beta**|Prerelease|v17.7 Preview|v2.x.x-beta|v2.x.x-beta|v2.x.x-beta|Dev preview|

*Latest is aligned on the major version.<br>
**Beta indicates developer preview.

## Features

The following list provides the key features of Teams Toolkit:

* [Project templates](#project-templates)
* [Automatic registration and configuration](#automatic-registration-and-configuration)
* [Multiple environments](#multiple-environments)
* [Quick access to Teams Developer Portal](#quick-access-to-teams-developer-portal)

### Project templates

You can start directly with the capability-focused templates such as tabs, bots, and message extensions or by following existing samples if you're already familiar with Teams app development. Teams Toolkit reduces the complexity of getting started with templates for common custom app built for your org (LOB app) scenarios and smart defaults to accelerate your time to production.

:::image type="content" source="toolkit-v4/images/create-new-app_2-v4.PNG" alt-text="Create new Teams app menu in VS Code.":::

### Automatic registration and configuration

You can save time and let the toolkit automatically register the app in Teams Developer Portal. When you first run or debug the app, configure settings, such as Microsoft Entra ID automatically. Sign in with your Microsoft 365 account to control where the app is configured and customized the included Microsoft Entra manifest when you need flexibility.

### Multiple environments

You can create different groupings of cloud resources to run and test your app. Use the **dev** environment with your Azure subscription or create a new app with a different subscription for staging, test, and production.

### Quick access to Teams Developer Portal

You can access Teams Developer Portal quickly, where you can configure, distribute, and manage your app. For more information, see [manage your Teams apps using Developer Portal](~/concepts/build-and-test/manage-your-apps-in-developer-portal.md).

:::image type="content" source="toolkit-v4/images/build-environment-developer-portal-2-v4.png" alt-text="Developer Portal":::

## See also

* [Build tabs for Teams](~/tabs/what-are-tabs.md)
* [Build bots for Teams](~/bots/what-are-bots.md)
* [Build Message extensions](~/messaging-extensions/what-are-messaging-extensions.md)
* [Create a new Teams app](~/toolkit/create-new-project.md)
* [Provision cloud resources](~/toolkit/provision.md)
* [Deploy Teams app to the cloud](~/toolkit/deploy.md)
* [Publish Teams apps](~/toolkit/publish.md)

::: zone-end
