---
title: Collaborate on TeamsFx Project using Teams Toolkit v4
author: surbhigupta
description: In this article, learn how to collaborate on TeamsFx Project using Teams Toolkit v4 and collaborate with other developers.
ms.author: surbhigupta
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
---

# Collaborate on Teams project using Microsoft Teams Toolkit v4

> [!IMPORTANT]
>
> We've introduced the [Teams Toolkit v5](../teams-toolkit-fundamentals.md) extension within Visual Studio Code. This version comes to you with many new app development features. We recommend that you use Teams Toolkit v5 for building your Teams app.
>
> Teams Toolkit v4 extension will soon be deprecated.

Multiple developers can work together to debug, provision and deploy for the same TeamsFx project, but it requires manually setting the right permissions of Teams App and Microsoft Entra ID. Teams Toolkit supports collaboration feature to allow developers and project owner to invite other developers or collaborators to the TeamsFx project to debug, provision, and deploy the same TeamsFx project.

## Collaborate with other developers

The following sections guide us to understand the collaboration process as project owner or collaborator:

### As project owner

  > [!NOTE]
  > Before adding collaborators for an environment, project owner needs to [Provision cloud resources](../provision.md) the project first.

  1. Select **Teams Toolkit** in the activity bar.
  
     :::image type="content" source="images/select-teams-toolkit-v4.png" alt-text="Select teams toolkit from activity bar":::

  1. In **ENVIRONMENT** section, select collaborators, that displays as option **1** **Add Microsoft 365 Teams App (with Microsoft Entra App) Owners** and **2** **List Microsoft 365 Teams App (with Microsoft Entra App) Owners** as shown in the following image:

     :::image type="content" source="images/add collaborators-v4.png" alt-text="collaborators":::

  2. Select **Add Microsoft 365 Teams App (with Microsoft Entra App) Owners** and add other Microsoft 365 account email address as collaborator. The account to be added must be on the same tenant as project owner for remote debug as shown in the image:

     :::image type="content" source="images/add-owner-v4.png" alt-text="Add project owner":::

  3. To view collaborators in current environment, select **List Microsoft 365 Teams App (with Microsoft Entra App) Owners**, then you can see collaborators listed in the output channel as shown in following image:

     :::image type="content" source="images/list of collaborators-v4.png" alt-text="list":::

  4. Push the project to GitHub.

     > [!NOTE]
     > The newly added collaborators do not receive any notification. The Project owner needs to notify collaborator.

### As project collaborator

  1. Clone the project from GitHub.
  2. Log on to Microsoft 365 account.
  3. Log on to Azure account, it has contributor permission for all the Azure resources, which are used in the project.
  4. To preview your Teams app, deploy the project to remote.
  5. Launch remote to have a preview of the Teams app.

     > [!NOTE]
     > Collaborators must log in using the account that project owner adds under the same tenant with project owner. For more information, see [build and run your Teams app in remote environment](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=3).

## Remove Collaborators

If you want to remove collaborators from Teams Toolkit extension, you need to remove manually as you can't remove them directly. Perform the following steps to remove collaborators manually:

* Using Developer Portal

  * Go to [Teams Developer Portal](https://dev.teams.microsoft.com/home) and select your Teams app by name or app ID.
  * Select **Owners** from left panel.
  * Select and remove the collaborator.

* Using Microsoft Entra ID

  * Go to [Microsoft Entra ID](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps), select **App registration** from left panel, and find your Microsoft Entra App.
  * Select **Owners** from left panel in Microsoft Entra App management page.
  * Select and remove the collaborator.

    > [!NOTE]
    >
    > * Collaborator added to your project doesn't receive any notification. Project owner needs to notify collaborator offline.
    > * Azure related permissions must be set manually by Azure subscription administrator on Azure portal.
    > * Azure account must have contributor role for the subscription so that developers can work together to provision, and deploy TeamsFx project.

## See also

* [Teams Toolkit Overview](../teams-toolkit-fundamentals.md)
* [Provision cloud resources](../provision.md)
* [Deploy Teams app to the cloud](../deploy.md)
* [Manage multiple environments](TeamsFx-multi-env-v4.md)
