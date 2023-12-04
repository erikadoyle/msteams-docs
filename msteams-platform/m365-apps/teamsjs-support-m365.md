---
title: The Teams JavaScript client library support across Microsoft 365
date: 06/26/2023
author: erikadoyle
ms.author: mosdevdocs
description: Understand the level of support for different TeamsJS library capabilities running in different hosts for Teams apps, including Microsoft Teams, Outlook, and Microsoft 365 app.
ms.localizationpriority: high
ms.topic: conceptual
ms.custom: m365apps
ms.date: 05/18/2023
keywords: TeamsJS Teams JavaScript library capability Microsoft 365 M365
---
# TeamsJS capability support across Microsoft 365

Starting with version 2.0.0, Microsoft Teams JavaScript client library (TeamsJS) enables [certain types of Teams apps](./overview.md) to run across the Microsoft 365 ecosystem. Currently, Microsoft 365 applications that can host Teams apps (Microsoft 365 app and Outlook) support only a subset of the application types and capabilities you can build for the Teams platform. This support expands over time.

This article details the level of support of TeamsJS version 2.x capabilities across various host applications. For more information on what's changed between TeamsJS versions 1.x and 2.x, see [What's new in TeamsJS version 2.x.x](../tabs/how-to/using-teams-client-library.md#whats-new-in-teamsjs-version-2xx).

The following *TeamsJS Capability* table lists TeamsJS capabilities (public namespaces) and their support across Microsoft 365 host applications. Some capabilities are marked with *Deprecated* or *Preview* badges, which have the following meanings:

| Badge | Meaning |
| - | - |
| :::image type="content" source="./images/preview-badge.png" alt-text="Image with the word 'Preview' inside a blue rectangle":::  | This capability is in preview and subject to change based on feedback. Don't use this capability in production. |
| :::image type="content" source="./images/deprecated-badge.png" alt-text="Image with the word 'Deprecated' inside an orange rectangle"::: | This capability is deprecated in favor of newer functionality, though it's supported for backwards compatibility purposes. For new apps, use the capability recommended in the usage notes of the deprecated capability. |

Microsoft 365 hosts are signified by the product icons in the following tables:

| Teams | Microsoft 365 app | Outlook |
| :-: | :-: | :-: |
| :::image type="content" source="./images/teams-icon.png" alt-text="Microsoft Teams icon"::: | :::image type="content" source="./images/microsoft-365-icon.png" alt-text="Microsoft 365 app icon"::: | :::image type="content" source="./images/outlook-icon.png" alt-text="Microsoft Outlook icon"::: |

Preview versions for both Teams and Outlook (launched through *Try the new Teams* and *Try the new Outlook* toggle controls in Teams and Outlook clients respectively) have different levels of support. The preview versions are designated by the following **PRE** (preview) icons:

| Teams preview | Outlook preview |
| :-: | :-: |
| :::image type="content" source="./images/teams-preview-icon.png" alt-text="Microsoft Teams (Preview) icon"::: | :::image type="content" source="./images/outlook-preview-icon.png" alt-text="Microsoft Outlook preview icon"::: |

Entries marked with a check and asterisk (&#x2713;*) indicate support for the host that is available only to preview audience who are enrolled in [Microsoft 365 Targeted Releases](prerequisites.md#enroll-your-developer-tenant-for-microsoft-365-targeted-releases-optional) for web clients or [Beta Channel apps](./prerequisites.md#install-microsoft-365-apps-in-your-test-environment) installed for desktop clients.

Using the following table, select any TeamsJS Capability for further details including reference docs, samples, usage notes, and limitations.

## Cross-host capabilities

The following table lists host application support for TeamsJS capabilities that can run outside of Teams.

<br />
<table border>
    <thead>
        <tr>
            <th>TeamsJS Capability</th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th><a href="#app">app</a></th>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
        </tr>
        <tr>
            <th><a href="#appinstalldialog">appInstallDialog</a></th>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#authentication">authentication</a></th>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
        </tr>
        <tr>
            <th><a href="#calendar">calendar</a></th>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
        </tr>
        <tr>
            <th><a href="#dialog">dialog</a><img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#geolocation">geoLocation</a><img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#mail">mail</a></th>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
        </tr>
        <tr>
            <th><a href="#pages">pages</a></th>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
        </tr>
        <tr>
            <th><a href="#profile">profile</a><img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#search">search</a><img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#secondarybrowser">secondaryBrowser</a><img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## Teams-only capabilities

The following table lists support for TeamsJS capabilities that run only in the Teams environment.

<br />
<table border>
    <thead>
        <tr>
            <th>TeamsJS Capability</th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th><a href="#appinitialization">appInitialization</a><img src="./images/deprecated-badge.png" alt="Badge indicating this capability is deprecated" /></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#call">call</a></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#chat">chat</a><img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#location">location</a><img src="./images/deprecated-badge.png" alt="Badge indicating this capability is deprecated" /></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#menus">menus</a></th>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#people">people</a></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#settings">settings</a><img src="./images/deprecated-badge.png" alt="Badge indicating this capability is  deprecated" /></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#sharing">sharing</a></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#stageview">stageView</a><img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#tasks">tasks</a><img src="./images/deprecated-badge.png" alt="Badge indicating this capability is deprecated" /></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#teamscore">teamsCore</a></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#video">video</a><img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#webstorage">webStorage</a><img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## Preview capabilities awaiting host support

Some capabilities in the source are in early preview and still awaiting initial support in one or more host applications that include [**barCode**](#barcode), [**media**](#media), [**meeting**](#meeting), and  [**search**](#search).

Later in this article, you can find more information on each capability of the Teams JavaScript client library.

## `app`

[Reference](/javascript/api/@microsoft/teams-js/app) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/App.css)

Namespace to interact with app initialization and lifecycle.

The `app` namespace is supported globally across all application hosts and, therefore, doesn't have an `isSupported` function.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>app</th>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
        </tr>
    </tbody>
</table>

## `appInitialization`

[Reference](/javascript/api/@microsoft/teams-js/appInitialization)

Deprecated. Namespace for initializing an app. For new apps, use [app.initialize()](/javascript/api/@microsoft/teams-js/app#@microsoft-teams-js-app-initialize) from the [app](#app) capability.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>appInitialization <img src="./images/deprecated-badge.png" alt="Badge indicating this capability is deprecated" /></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## `appInstallDialog`

[Reference](/javascript/api/@microsoft/teams-js/appinstalldialog) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/AppInstallDialog.tsx)

Namespace used to open a dialog for installing an application.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>appInstallDialog</th>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## `authentication`

[Reference](/javascript/api/@microsoft/teams-js/authentication)

Namespace to interact with the authentication-related part of the library. This module is used for starting or completing authentication flows.

The `authentication` namespace is supported globally across all application hosts and, therefore, doesn't have an `isSupported` function.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>authentication</th>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
        </tr>
    </tbody>
</table>

## `barCode`

[Reference](/javascript/api/@microsoft/teams-js/barcode)

Preview. Namespace to interact with the barcode scanning-related part of the library.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>barCode <img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## `calendar`

[Reference](/javascript/api/@microsoft/teams-js/calendar)

Namespace providing calendar-related functionality.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>calendar</th>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
        </tr>
    </tbody>
</table>

## `call`

[Reference](/javascript/api/@microsoft/teams-js/call) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/Call.tsx)

Namespace providing functionality to start a call with others.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>call</th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## `chat`

[Reference](/javascript/api/@microsoft/teams-js/chat) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/Chat.tsx)

Preview. Namespace providing functionality to start a chat with others.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>chat <img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## `dialog`

[Reference](/javascript/api/@microsoft/teams-js/dialog) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/Dialog.Url.tsx)

Preview. This group of capabilities enables apps to show modal task modules (dialogs). There are two primary types of dialogs: URL-based dialogs and Adaptive Card dialogs. Both types of dialogs are shown on top of your app, preventing interaction with your app while they're displayed.

- URL-based dialogs allow you to specify a URL from which the contents are shown inside the dialog. For URL dialogs, use the functions and interfaces in the url namespace.
- Adaptive Card-based dialogs allow you to provide JSON describing an Adaptive Card that is shown inside the dialog. For Adaptive Card dialogs, use the functions and interfaces in the adaptiveCard namespace.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>dialog <img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#dialogadaptivecard">dialog.adaptiveCard</a> <img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#dialogadaptivecardbot">dialog.adaptiveCard.bot</a> <img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#dialogupdate">dialog.update</a><img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#dialogurl">dialog.url</a><img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#dialogurlbot">dialog.url.bot</a><img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

### `dialog.adaptiveCard`

[Reference](/javascript/api/@microsoft/teams-js/dialog.adaptivecard) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/Dialog.AdaptiveCard.tsx)

Preview. Subcapability for interacting with Adaptive Card dialogs.

### `dialog.adaptiveCard.bot`

[Reference](/javascript/api/@microsoft/teams-js/dialog.adaptivecard.bot) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/Dialog.AdaptiveCard.Bot.tsx)

Preview. Subcapability for interaction with Adaptive Card dialogs that need to communicate with the Bot Framework.

### `dialog.update`

[Reference](/javascript/api/@microsoft/teams-js/dialog.update) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/Dialog.Update.tsx)

Preview. Namespace for updating dialogs.

### `dialog.url`

[Reference](/javascript/api/@microsoft/teams-js/dialog.url) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/Dialog.Url.tsx)

Preview. Subcapability for interacting with HTML-based dialogs.

### `dialog.url.bot`

[Reference](/javascript/api/@microsoft/teams-js/dialog.url.bot) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/Dialog.Url.Bot.tsx)

Preview. Subcapability for interacting with HTML-based dialogs that need to communicate with the Bot Framework.

## `geoLocation`

[Reference](/javascript/api/@microsoft/teams-js/geolocation) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/GeoLocation.tsx)

Preview. Namespace providing location-related functionality. This is the newer version of the location module.

Capabilities that require the user to grant [device permissions](../concepts/device-capabilities/device-capabilities-overview.md) (such as *geoLocation*) are partially supported for apps running outside of Teams. Users can adjust app permissions from the app header when running in Outlook and Microsoft 365 app, or from app settings on mobile. It's recommended to modify your code to check Outlook and Microsoft 365 supportability:

- Call `isSupported` on a capability before using it.
- Catch and handle errors when calling TeamsJS and HTML5 APIs

When an API doesn't support or generates an error, add logic to fail or provide a workaround. For example:

- Direct the user to your app's website
- Direct the user to use the app in Teams to complete the flow
- Notify the user that the functionality isn't yet available

> [!TIP]
> Ensure your app manifest only specifies the device permissions it's using.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>geoLocation <img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#geolocationmap">geoLocation.map</a> <img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

### `geoLocation.map`

[Reference](/javascript/api/@microsoft/teams-js/geolocation.map) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/GeoLocation.map.tsx)

Preview. Subcapability providing map-related functionality.

## `location`

[Reference](/javascript/api/@microsoft/teams-js/location)

Deprecated. Namespace providing location-related functionality (get and show location). Use [geoLocation](#geolocation) for new apps.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>location <img src="./images/deprecated-badge.png" alt="Badge indicating this capability is deprecated" /></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## `mail`

[Reference](/javascript/api/@microsoft/teams-js/mail)

Namespace providing email-related functionality.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>mail</th>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
        </tr>
    </tbody>
</table>

## `media`

[Reference](/javascript/api/@microsoft/teams-js/media)

Namespace providing image file-related functionality.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>media</th>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## `meeting`

[Reference](/javascript/api/@microsoft/teams-js/meeting)

Namespace providing in-meeting app functionality.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>meeting</th>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

> [!NOTE]
> The following methods aren't supported on the Teams mobile client:
>
> - `meeting.requestStartLiveStreaming`
> - `meeting.requestStopLiveStreaming`
> - `meeting.getLiveStreamState`
> - `meeting.registerLiveStreamChangedHandler`

## `menus`

[Reference](/javascript/api/@microsoft/teams-js/menus) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/Menus.tsx)

Namespace to interact with the menu-related part of the library. This module is used to show *View Configuration*, *Action Menu*, and *Navigation Bar Menu*.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>menus</th>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## `pages`

[Reference](/javascript/api/@microsoft/teams-js/pages) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/Pages.tsx)

Navigation-related part of the TeamsJS library.

Prior to TeamsJS version 2.0, all deep linking scenarios were handled using `shareDeepLink` (to generate a link *to* a specific part of your app) and `executeDeepLink` (to navigate to a deep link *from* or *within* your app). TeamsJS v.2.0 introduces a new API, `navigateToApp`, for navigating to pages (and subpages) within an app in a consistent way across app hosts (Microsoft 365 app and Outlook, in addition to Teams). For new apps, follow the linked updated guidance depending on your navigation scenario:

- **Deep links into your app.** Use [`pages.shareDeepLink`](/javascript/api/@microsoft/teams-js/pages#@microsoft-teams-js-pages-sharedeeplink) (known as *shareDeepLink* prior to TeamsJS v.2.0) to generate and display a copyable link for the user to share. When selected, the user is prompted to install the app if it's not already installed for the application host.

- **Navigation within your app.** Use the new [`pages.currentApp`](/javascript/api/@microsoft/teams-js/pages.currentapp) namespace to navigate within your app within the hosting application. Specifically, the function [`navigateTo(NavigateWithinAppParams)`](/javascript/api/@microsoft/teams-js/pages.currentapp#@microsoft-teams-js-pages-currentapp-navigateto) to allow navigation to a specific tab within the current app and the function [`navigateToDefaultPage()`](/javascript/api/@microsoft/teams-js/pages.currentapp#@microsoft-teams-js-pages-currentapp-navigatetodefaultpage) to navigate to the first tab defined in the app's manifest. For more information, see [navigate within a tab app](../tabs/how-to/tab-navigation.md).

    These APIs provide the equivalent of navigating to a deep link (as the now deprecated *executeDeepLink* was once used for) without requiring your app to construct a URL or manage different deep link formats for different application hosts.

- **Deep links out of your app.** For deep links from your app to various areas of its current host, use the typed APIs provided by the TeamsJS library. For example, use the `calendar` capability to open a scheduling dialog or calendar item from your app.

    For deep links from your app to other apps running in the same host, use [`pages.navigateToApp`](/javascript/api/@microsoft/teams-js/pages#@microsoft-teams-js-pages-navigatetoapp).

    For any other external deep linking scenarios, you can use [`app.openLink`](/javascript/api/@microsoft/teams-js/app#@microsoft-teams-js-app-openlink), which provides similar functionality to the now deprecated (starting in TeamsJS v.2.0) *executeDeepLink* API.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th><a href="#pages">pages</a></th>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
        </tr>
        <tr>
            <th><a href="#pagesappbutton">pages.appButton</a></th>
            <td>&#x2713;</td>
            <td>&#x2713;</td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#pagesbackstack">pages.backStack</a></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#pagescurrentapp">pages.currentApp</a></th>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
        </tr>
        <tr>
            <th><a href="#pagesconfig">pages.config</a></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <th><a href="#pagestabs">pages.tabs</a></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

> [!NOTE]
> The following methods aren't supported on the Teams mobile client:
>
> - `pages.getConfig`
> - `pages.setCurrentFrame`
> - `pages.initializeWithFrameContext`
> - `pages.tabs.navigateToTab`
> - `pages.tabs.getMruTabInstances`
> - `pages.tabs.getTabInstances`

### `pages.appButton`

[Reference](/javascript/api/@microsoft/teams-js/pages.appbutton) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/Pages.tsx)

Provides APIs to interact with the app button part of the SDK.

### `pages.backStack`

[Reference](/javascript/api/@microsoft/teams-js/pages.backstack) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/pagesSubCapability/NavigateBack.tsx)

Provides APIs for handling the user's navigational history.

### `pages.config`

[Reference](/javascript/api/@microsoft/teams-js/pages.config)

Provides APIs to interact with the configuration-specific part of the SDK. This object is usable only on the configuration frame.

### `pages.currentApp`

[Reference](/javascript/api/@microsoft/teams-js/pages.currentapp) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/Pages.Current.tsx)

Provides functions for navigating without needing to specify your application ID.

### `pages.tabs`

[Reference](/javascript/api/@microsoft/teams-js/pages.tabs)

Provides APIs for querying and navigating between contextual tabs of an application. Unlike personal tabs, contextual tabs are pages associated with a specific context, such as channel or chat.

## `people`

[Reference](/javascript/api/@microsoft/teams-js/people) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/People.tsx)

Namespace providing functionality for [People Picker API](../concepts/device-capabilities/people-picker-capability.md).

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>people</th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## `profile`

[Reference](/javascript/api/@microsoft/teams-js/profile)

Preview. Namespace providing for profile-related functionality.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>profile <img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

> [!NOTE]
> The `profile.showProfile` method isn't supported on the Teams mobile client.

## `search`

[Reference](/javascript/api/@microsoft/teams-js/search)

Preview. Allows your application to interact with the host Microsoft 365 application's search box. By integrating your application with the host's search box, users can search your app using the same search box they use elsewhere in Teams, Outlook, or Microsoft 365 app.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>search <img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## `secondaryBrowser`

[Reference](/javascript/api/@microsoft/teams-js/secondaryBrowser)

Preview. Namespace supporting in-app browser experiences of the host app. For example, opening a URL in the host app inside a browser.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>secondaryBrowser <img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## `settings`

[Reference](/javascript/api/@microsoft/teams-js/settings)

Deprecated. Provides settings-related functionality. Use equivalent APIs from the [pages](#pages) for new apps.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>settings <img src="./images/deprecated-badge.png" alt="Badge indicating this capability is deprecated" /></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## `sharing`

[Reference](/javascript/api/@microsoft/teams-js/sharing) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/Sharing.tsx)

Namespace to open a share dialog for web content. For more information, see [Share to Teams from personal app or tab](../concepts/build-and-test/share-to-teams-from-personal-app-or-tab.md).

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>sharing</th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

> [!NOTE]
> The `sharing.shareWebContent` method isn't supported on the Teams mobile client.

## `stageView`

[Reference](/javascript/api/@microsoft/teams-js/stageview) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/StageView.tsx)

Preview. Namespace to interact with the Stage View specific part of the library.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>stageView <img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## `tasks`

[Reference](/javascript/api/@microsoft/teams-js/tasks)

The earlier version of the capability for providing modal dialog (task module) supports versions prior to TeamsJS v2.8.0. For new apps, use the [dialog](#dialog) capability.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>tasks <img src="./images/deprecated-badge.png" alt="Badge indicating this capability is deprecated" /></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

> [!NOTE]
> The `task.getDefaultSizeIfNotProvided` method isn't supported on the Teams mobile client.

## `teamsCore`

[Reference](/javascript/api/@microsoft/teams-js/teamscore) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/TeamsCore.tsx)

Namespace containing the set of APIs that support Teams-specific functionalities.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>teamsCore</th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td>&#x2713;*</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## `video`

[Reference](/javascript/api/@microsoft/teams-js/videoeffects) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/Video.tsx)

Preview. Namespace representing functionality for in-meeting video effects.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>video <img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

> [!NOTE]
> The following methods aren't supported on the Teams mobile client:
>
> - `video.notifySelectedVideoEffectChanged`
> - `video.registerForVideoEffect`

## `webStorage`

[Reference](/javascript/api/@microsoft/teams-js/webstorage) | [Sample](https://github.com/vikramtha/microsoft-teams-library-js/blob/vikramtha/teamsjs-cc-app/apps/teams-cc-app/src/components/capabilities/WebStorage.tsx)

Preview. Contains functionality to allow web apps to store data in webview cache.

<br />
<table border>
    <thead>
        <tr>
            <th></th>
            <th colspan=3>Web</th>
            <th colspan=5>Desktop</th>
            <th colspan=6>Mobile</th>
        </tr>
        <tr>
            <th></th>
            <th colspan=3></th>
            <th colspan=5>Windows</th>
            <th colspan=3>Android</th>
            <th colspan=3>iOS</th>
        </tr>
        <tr>
            <td></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Teams (Preview)" src="./images/teams-preview-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Outlook (Preview)" src="./images/outlook-preview-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
            <td><img alt="Teams" src="./images/teams-icon.png"/></td>
            <td><img alt="Microsoft 365 app" src="./images/microsoft-365-icon.png"/></td>
            <td><img alt="Outlook" src="./images/outlook-icon.png"/></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th>webStorage <img src="./images/preview-badge.png" alt="Badge indicating this capability is in preview" /></th>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
            <td>&#x2713;</td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

> [!NOTE]
> The `webStorage.isWebStorageClearedOnUserLogOut` method isn't supported on the Teams mobile client.

## Code sample

| Sample name           | Description | Source|
:---------------------|:--------------|:---------|
| TeamsJS Capability Checker| Sample application to demonstrate the capabilities of TeamsJS library v2 in Teams apps extended across Outlook and Microsoft 365. | [TypeScript](https://github.com/vikramtha/microsoft-teams-library-js/tree/vikramtha/teamsjs-cc-app/apps/teams-cc-app)

## See also

- [Extend Teams apps across Microsoft 365](./overview.md)
- [Extend a Teams personal tab across Microsoft 365 app](./extend-m365-teams-personal-tab.md)
- [Teams JavaScript client library overview](../tabs/how-to/using-teams-client-library.md)
- [TeamsJS API Reference](/javascript/api/@microsoft/teams-js)
