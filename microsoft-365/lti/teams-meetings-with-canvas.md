---
title: Brug Microsoft Teams møder med Lærred
ms.author: v-cichur
author: cichur
manager: serdars
ms.reviewer: sovaish
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Integrer Microsoft Teams møder med Lærred
ms.openlocfilehash: 529cc27b6b63fca76d47487f26bd6deda7478640
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569573"
---
# <a name="use-microsoft-teams-meetings-with-canvas"></a>Brug Microsoft Teams møder med Lærred

Microsoft Teams-møder er en LTI-app (Learning Tools Interoperability), der gør det nemt for undervisere og studerende at navigere mellem deres Learning Management System (LMS) og Teams. Brugere kan få adgang til deres klasseteams, der er knyttet til deres kursus, direkte fra deres LMS.

## <a name="prerequisites-before-deployment"></a>Forudsætninger før udrulning

> [!NOTE]
> Den aktuelle Teams Meetings LTI understøtter kun synkronisering af Lærred-brugere med Microsoft Azure Active Directory (AAD) i et begrænset omfang.
>
> - Din lejer skal have en Microsoft Education-licens.
> - Kun en enkelt Microsoft-lejer kan bruges til at tilknytte brugere mellem Canvas og Microsoft.
> - Du skal deaktivere SDS Skoledatasynkronisering (Class Teams LTI) for at undgå duplikering af grupper.

## <a name="microsoft-office-365-admin"></a>Microsoft Office 365 administrator

Før du administrerer integration af Microsoft Teams i Instructure Canvas, er det vigtigt, at Canvass **Microsoft-Teams-Sync-for-Canvas Azure-app** er godkendt af din institutions Microsoft Office 365-administrator i din Microsoft Azure-lejer, før du afslutter Lærred-administratorkonfigurationen.

1. Log på Lærred.

2. Vælg linket **Administrator** i den globale navigation, og vælg derefter din konto.

3. I administrationsnavigationen skal **du Indstillinger** **navigationslinket** og derefter fanen Integrationer.

   ![Canvas Teams Sync Updated png.](https://user-images.githubusercontent.com/87142492/128552407-78cb28e9-47cf-4026-954d-12dc3553af6f.png)

4. Angiv Microsoft-lejernavn, logonattribut, domænesuffiks og AAD opslagsattribut. Disse felter bruges til at matche brugere i Lærred med brugere i Microsoft Azure Active Directory.
   - Logonattributten er lærredets brugerattribut, der bruges til at matche.
   - Feltet Suffiks er valgfrit og gør det muligt at angive et domæne, når der ikke er en nøjagtig tilknytning mellem lærredsattributter og Microsoft AAD felter. Hvis din Lærred-mail f.eks. er "name@example.edu", mens UPN i Microsoft AAD er "navn", kan du matche brugerne ved at indtaste "example.edu" i suffiksfeltet.
   - Active Directory-opslagsattributten er det felt på Microsoft-siden, som lærredsattributter passer til. Vælg mellem UPN, primær mailadresse eller mailalias.

5. Vælg **Opdater Indstillinger når** du er færdig.

6. Hvis du vil godkende adgang til Canvas **Microsoft-Teams-Sync-for-Canvas Azure-app**, skal du vælge **linket Giv lejer** adgang. Du bliver omdirigeret til slutpunktet for administratorsamtykke i Microsoft Identity Platform.

   ![tilladelser.](media/permissions.png)

7. Vælg **Acceptér**.

   > [!NOTE]
   > Synkronisering er en funktionalitet, der administreres af LMS-partner og bruges til at synkronisere medlemskab på kursusniveau til Teams-teamet ved hjælp af Microsoft Graph-API'er. Dette er primært en funktionalitet, som en underviser slår til som sand på et kursusniveau. Efterfølgende ændringer, der foretages på LMS-siden for tilføjelse eller sletning af medlemmer, afspejles ved hjælp af den synkronisering, der implementeres af LMS-partneren. Selv før denne proces er aktiveret for en underviser, giver administratoren af M365 Education Institute deres undervisere mulighed for at få adgang til synkronisering ved hjælp af synkroniseringstilladelsen modal nedenfor. Disse tilladelser gives til LMS-partneren for at give undervisere mulighed for at synkronisere medlemskab mellem LMS-kurset Teams klasseteams.

8. Aktivér Microsoft Teams synkronisering ved at slå til/fra-knappen til.

   ![teams-sync.](media/teams-sync.png)

## <a name="canvas-admin"></a>Lærredsadministrator

Konfigurer Microsoft Teams LTI 1.3-integration.

Som Canvas-administrator skal du tilføje LTI-appen til Microsoft Teams-møder i dit miljø. Noter LTI-klient-id'et for appen.

 - Microsoft Teams møder – 170000000000703

1. Få **adgang til** **administratorindstillingerApps** > .

2. Vælg **+ App for** at tilføje Teams LTI-apps.

   ![eksterne apps.](media/external-apps.png)

3. Vælg **Efter klient-id** for konfigurationstype.

   ![tilføj app.](media/add-app.png)

4. Angiv det angivne klient-id, og vælg derefter **Send**.

   Du vil bemærke det Microsoft Teams LTI-appnavn for klient-id'et for bekræftelse.

5. Vælge **Installér**.

   LTI Microsoft Teams-mødeappen føjes til listen over eksterne apps.

6. Aktivér appen ved at navigere til udviklernøglerne i lærredets administratorkonto, vælge nedarvet og slå til/fra-knappen "til" for Microsoft Teams-møder.

## <a name="enable-for-canvas-courses"></a>Aktivere lærredskurser

Hvis du vil bruge LTI i et kursus, skal underviseren i Lærred-kurset aktivere integrationssynkronisering. Hvert kursus skal aktiveres af en underviser, for at der kan oprettes Teams tilsvarende kursus; der er ingen global mekanisme til Teams oprettelse. Dette er designet af forsigtighed for at forhindre uønskede Teams oprettes.

Henvis underviserne til [underviserens dokumentation](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) for aktivering af LTI for hvert kursus og færdiggøre integrationskonfigurationen.
