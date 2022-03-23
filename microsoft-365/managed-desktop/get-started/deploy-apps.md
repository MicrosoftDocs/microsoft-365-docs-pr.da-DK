---
title: Installér apps på enheder
description: Oplysninger om tilføjelse og implementering af apps på Microsoft-administrerede skrivebordsenheder.
keywords: Microsoft Managed Desktop, Microsoft 365, service, dokumentation, apps, line of business-apps, LOB-apps
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: d0c8dbb71a56701cb5ca75aadb1a5bcc7290844f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587871"
---
# <a name="deploy-apps-to-devices"></a>Installér apps på enheder

En del af onboarding til Microsoft Managed Desktop omfatter tilføjelse og implementering af apps på dine brugeres enheder. Når du bruger Microsoft Managed Desktop-portalen, kan du tilføje og installere dine apps.

Den overordnede proces ser sådan ud:

1. [Føj apps til Microsoft Managed Desktop-portalen](#1): Disse apps kan være eksisterende LOB-apps (line of business), eller apps fra Microsoft Store til Virksomheder, som du har synkroniseret med Intune.
2. [Opret Azure Active Directory (AD)-grupper for apptildeling](#2): Du skal bruge disse grupper til at administrere apptildeling.
3. [Tildel apps til dine brugere](#3).

<span id="1" />

## <a name="step-1-add-apps-to-microsoft-managed-desktop-portal"></a>Trin 1: Føj apps til Microsoft Managed Desktop-portalen

Du kan tilføje [Win32 eller Windows MSI-baserede apps](#lob-apps) eller [Microsoft Store til Virksomheder-apps](#msfb-apps) til Microsoft Managed Desktop og derefter installere dem på Microsoft Managed Desktop-enheder.

<span id="lob-apps">

### <a name="win32-or-windows-msi-based-apps-to-microsoft-managed-desktop"></a>Win32 eller Windows MSI-baserede apps til Microsoft Managed Desktop

Du kan føje dine LOB-apps (line of business) til Microsoft Managed Desktop-portalen. Du kan finde oplysninger om krav til apps, der er installeret på Microsoft-administrerede skrivebordsenheder, [under Krav til Microsoft-administreret skrivebordsapp](../service-description/mmd-app-requirements.md).

I denne fremgangsmåde skal du vælge, hvilken type app du vil tilføje, og derefter konfigurere og overføre appkilden.

**Sådan føjer du din LOB-app Windows-app til Microsoft Managed Desktop-portalen:**

Du kan logge på Microsoft Managed Desktop-portalen eller logge på Intune og derefter søge efter Microsoft Managed Desktop. Vi viser, hvordan du logger på Microsoft Managed Desktop-portalen nedenfor:

1. Log på [administrationsportalen for Microsoft-administreret skrivebord](https://aka.ms/mmdportal).
2. Under **Lager skal** du vælge **Apps**.
3. I sektionen Apps-arbejdsbelastning skal du vælge **Tilføj**.
4. I **Tilføj app** skal du **vælge Line of business-app** **eller Windows -app (Win32)**.
    - Hvis du har valgt **Line of business-app**, skal du se Føj en [Windows line of business-app til Microsoft Intune](/intune/lob-apps-windows) for at få vejledning til at tilføje og konfigurere line of business-apps.
    - Hvis du har **valgt Windows-app (Win32),** skal du se [Win32-appadministration](/intune/apps-win32-app-management) for at få vejledning til at tilføje og konfigurere Windows apps.

<span id="msfb-apps">

### <a name="microsoft-store-for-business-apps"></a>Microsoft Store til Virksomheder apps

Hvis du ikke har tilmeldt dig et Microsoft Store til Virksomheder, kan du tilmelde dig, når du køber apps. Når du har dine apps, kan du synkronisere dem med Microsoft Managed Desktop.

**Sådan køber du apps fra Microsoft Store til Virksomheder:**

1. Log på [Microsoft Store til Virksomheder](https://businessstore.microsoft.com) med din Microsoft Store til Virksomheder administratorkonto.
2. Vælg **Køb til min gruppe**.
3. Brug Søg til at finde den ønskede app, og vælg appen.
4. I produktoplysningerne skal du vælge **Hent appen**.
Microsoft Store tilføjer appen til **Dine produkter** for organisationen.

**Sådan kontrollerer du, at en synkronisering mellem Intune og Microsoft Store til Virksomheder er aktiv:**

1. Log på [Microsoft Store til Virksomheder](https://businessstore.microsoft.com) med din Microsoft Store til Virksomheder administratorkonto.
2. Vælg **Administrer**.
3. Vælg **Indstillinger og** vælg derefter **Distribuer**.
4. Under **Administrationsværktøjer skal** du kontrollere, at Intune er angivet, og at status er **Aktiv**.  

**Sådan gennemtvinger du en synkronisering mellem Intune og Microsoft Store til Virksomheder:**

1. Log på [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Vælg **Lejeradministration** , derefter **Forbindelser og tokens**, og **Microsoft Store til Virksomheder**.
3. Vælg **Aktiveret** for **aktivering Microsoft Store til Virksomheder synkronisering giver dig adgang til volumenkøbte apps med Intune.**
4. Vælg dit foretrukne sprog, og vælg **derefter** Synkroniser for at hente de apps, du har købt, Microsoft Store i Intune.

<span id="2" />

## <a name="step-2-create-azure-ad-groups"></a>Trin 2: Opret Azure AD-grupper

Opret tre Azure AD-grupper for hver app. I denne tabel vises de grupper, du skal bruge (Tilgængelig, Påkrævet og Fjern).

Apptildelingstype | Brug af gruppe | Eksempel på Azure AD-navn |
--- | --- | --- |
Tilgængelig |  Appen vil være tilgængelig fra Firmaportal app eller websted. | MMD – *appnavn* – tilgængelig |
Påkrævet |  Appen installeres på enheder i de valgte grupper. | MMD – *appnavn* – påkrævet |
Fjern |  Appen fjernes fra enheder i de valgte grupper. | MMD – *appnavn –* Fjern |

Føj dine brugere til disse grupper til enten:

- Gør appen tilgængelig
- Installer appen, eller
- Fjern appen fra deres Microsoft-administrerede skrivebordsenhed.

<span id="3" />

## <a name="step-3-assign-apps-to-your-users"></a>Trin 3: Tildel apps til dine brugere

**Sådan tildeler du appen til dine brugere:**

1. Log på [administrationsportalen for Microsoft-administreret skrivebord](https://aka.ms/mmdportal).
2. I ruden Administreret skrivebord skal du vælge **Apps**.
3. I sektionen Apps-arbejdsbelastning skal du vælge den app, du vil tildele brugere til, og vælge **Tildel brugergrupper**.
4. For den specifikke app skal du vælge en opgavetype (Tilgængelig, Påkrævet, Fjern) og tildele den relevante gruppe.
5. I ruden Tildel apps skal du vælge **OK**.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Trin til at komme i gang med Microsoft-administreret skrivebord

1. Få adgang [til administrationsportalen](access-admin-portal.md).
1. [Tilføj og bekræft administratorkontakter i administrationsportalen](add-admin-contacts.md).
1. [Juster indstillinger efter tilmelding](conditional-access.md).
1. Installér og [tildel Intune-firmaportal](company-portal.md).
1. [Tildel licenser](assign-licenses.md).
1. Installer apps (denne artikel).
1. [Klargør enheder](prepare-devices.md).
1. Konfigurer første [kørselsoplevelse med Autopilot og Statussiden For tilmelding](esp-first-run.md).
1. [Aktivér brugersupportfunktioner](enable-support.md).
1. [Gør dine brugere klar til at bruge enheder](get-started-devices.md).
1. [Kom i gang med appstyring](get-started-app-control.md).

<!--# Preparing apps for Microsoft Managed Desktop

This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.

-->
