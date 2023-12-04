---
title: Test app behavior in different environment v4
author: surbhigupta
description: In this module, learn how to test app behavior in different environment using Teams toolkit v4.
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/03/2022
---

# Test app behavior in different environment v4

> [!IMPORTANT]
>
> We've introduced the [Teams Toolkit v5](../teams-toolkit-fundamentals.md) extension within Visual Studio Code. This version comes to you with many new app development features. We recommend that you use Teams Toolkit v5 for building your Teams app.
>
> Teams Toolkit v4 extension will soon be deprecated.

You can test your Teams app after integrating with Microsoft Teams. To test your Teams app, you need to create at least one workspace in your environment. You can use Teams Toolkit for testing your Teams app:

* **Locally hosted in Teams**: Teams Toolkit locally hosts your Teams app by uploading it into Teams for testing in local environment.

* **Cloud-hosted in Teams**: For testing your Teams app remotely, you need to Cloud-host it using provisioning and deploying on Microsoft Entra ID. It involves uploading your solution to the Microsoft Entra ID and then upload into Teams.

> [!NOTE]
> For production-scale debugging and testing, we recommend that you follow your own company guidelines to ensure you are able to support testing, staging, and deployment through your own processes.

## Locally hosted environment

Teams is a cloud-based product that requires all services it accesses, to be available publicly using HTTPS endpoints. Local hosting is about custom app upload into Teams for testing in local environment.

> [!NOTE]
> Although you can use any tool of your choice for testing, we recommend you to use [ngrok](https://ngrok.com/download).

## Cloud-hosted environment

To host your development and production code and their HTTPS endpoints, You need to remotely test your teams app using provisioning and deploying on Microsoft Entra ID. You need to ensure that all domains are accessible from your Teams app listed in the [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) object in the `manifest.jason` file

> [!NOTE]
> To ensure a secure environment, be explicit about the exact domain and subdomains you reference and those domains must be in your control. For example, `*.azurewebsites.net` is not recommended, however `contoso.azurewebsites.net` is recommended.

## See also

* [Teams Toolkit Overview](../teams-toolkit-fundamentals.md)
* [Debug your Microsoft Teams app locally](../debug-local.md)
* [Debug background process v4](debug-background-process-v4.md)
* [Use Teams Toolkit to provision cloud resources](../provision.md)
* [Deploy to the cloud](../deploy.md)
* [Preview and customize Teams app manifest](../TeamsFx-preview-and-customize-app-manifest.md)
* [Manage multiple environments in Teams Toolkit v4](TeamsFx-multi-env-v4.md)
