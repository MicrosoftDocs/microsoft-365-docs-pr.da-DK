---
title: Brug Microsoft Teams-møder med lærred
ms.author: danismith
author: DaniEASmith
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
description: Integrer Microsoft Teams møder med lærred
ms.openlocfilehash: cbb24972dba7fafe60cb460e514a0fede64a08fb
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621467"
---
# <a name="use-microsoft-teams-meetings-with-canvas"></a>Brug Microsoft Teams-møder med lærred

Microsoft Teams møder er en LTI-app (Learning Tools Interoperability), der hjælper undervisere og studerende med nemt at navigere mellem deres LMS (Learning Management System) og Teams. Brugerne kan få adgang til deres klasseteams, der er knyttet til deres kursus, direkte fra deres LMS.

## <a name="prerequisites-before-deployment"></a>Forudsætninger før udrulning

> [!NOTE]
> Den aktuelle Teams Meetings LTI understøtter kun synkronisering af lærredsbrugere med Microsoft Azure Active Directory (AAD) i et begrænset omfang.
>
> - Din lejer skal have en Microsoft Education-licens.
> - Det er kun en enkelt Microsoft-lejer, der kan bruges til at tilknytte brugere mellem lærred og Microsoft.
> - Du skal slå Skoledatasynkronisering (SDS) fra, før du bruger LTI-klasse Teams for at undgå dubletter af grupper.

## <a name="microsoft-office-365-admin"></a>Microsoft Office 365 administrator

Før du administrerer Microsoft Teams integration i Instructure Canvas, er det vigtigt, at Canvass **Microsoft-Teams-Sync-for-Canvas Azure-app** godkendes af din institutions Microsoft Office 365 administrator i din Microsoft Azure lejer, før du fuldfører konfigurationen af lærredsadministratoren.

1. Log på Lærred.

2. Vælg linket **Administrator** i den globale navigation, og vælg derefter din konto.

3. I administrationsnavigationen skal du vælge linket **Indstillinger** og derefter fanen **Integrationer**.

   ![Lærred Teams synkroniser opdateret png.](https://user-images.githubusercontent.com/87142492/128552407-78cb28e9-47cf-4026-954d-12dc3553af6f.png)

4. Angiv dit Microsoft-lejernavn, din logonattribut, dit domænesuffiks og din AAD-opslagsattribut. Disse felter bruges til at matche brugere på lærredet med brugere i Microsoft Azure Active Directory.
   - Logonattributten er den lærredsbrugerattribut, der anvendes til matchning.
   - Feltet Suffiks er valgfrit og giver dig mulighed for at angive et domæne, når der ikke er en nøjagtig tilknytning mellem lærredsattributter og Microsoft AAD-felter. Hvis din lærredsmail f.eks. er 'name@example.edu', mens UPN i Microsoft AAD er 'navn', kan du matche brugerne ved at angive 'example.edu' i suffiksfeltet.
   - Active Directory-opslagsattributten er det felt på Microsoft-siden, som lærredsattributterne matches til. Vælg mellem UPN, primær mailadresse eller mailaliasset.

5. Vælg **Opdater Indstillinger** når du er færdig.

6. Hvis du vil godkende adgang til Lærredets **Microsoft-Teams-Sync-for-Canvas Azure-app**, skal du vælge linket **Tildel lejeradgang**. Du bliver omdirigeret til slutpunktet for Samtykke for Microsoft Identity Platform-administrator.

   ![Tilladelser.](media/permissions.png)

7. Vælg **Acceptér**.

   > [!NOTE]
   > Synkronisering er en funktionalitet, der administreres af LMS-partneren og bruges til at synkronisere medlemskab på kursusniveau til det Teams team ved hjælp af Microsoft graph-API'er. Dette er primært en funktionalitet, som en underviser skifter til som sand på kursusniveau. Efterfølgende afspejles alle ændringer af medlemskabet på LMS-siden for tilføjelse eller sletning af medlemmerne ved hjælp af den synkronisering, der er implementeret af LMS-partneren. Selv før denne proces er aktiveret for en underviser, giver M365 Education Institute-administratoren deres undervisere mulighed for at få adgang til synkronisering ved hjælp af indstillingen Synkroniser tilladelse nedenfor. Disse tilladelser tildeles LMS-partneren for at gøre det muligt for undervisere at synkronisere medlemskab mellem LMS-kurset og Teams klasseteams.

8. Aktivér synkroniseringen af Microsoft Teams ved at slå til/fra-knappen til.

   ![teams-synkronisering.](media/teams-sync.png)

## <a name="canvas-admin"></a>Lærredsadministrator

Konfigurer Microsoft Teams LTI 1.3 Integration.

Som lærredsadministrator skal du tilføje LTI-appen Microsoft Teams møder i dit miljø. Notér LTI-klient-id'et for appen.

 - Microsoft Teams møder – 170000000000703

1. Adgang **til administratorindstillingerApps** > .

2. Vælg **+ App** for at tilføje Teams LTI-apps.

   ![eksterne apps.](media/external-apps.png)

3. Vælg **Efter klient-id** som konfigurationstype.

   ![tilføj app.](media/add-app.png)

4. Angiv det angivne klient-id, og vælg derefter **Send**.

   Du vil bemærke navnet på LTI-appen Microsoft Teams møder for klient-id'et til bekræftelse.

5. Vælge **Installér**.

   LTI-appen Microsoft Teams møder føjes til listen over eksterne apps.

6. Aktivér appen ved at navigere til udviklernøglerne på lærredsadministratorens konto, vælge Nedarvet og slå til/fra-knappen "til" for Microsoft Teams møder.

## <a name="enable-for-canvas-courses"></a>Aktivér for lærredskurser

Hvis du vil bruge LTI i et kursus, skal en underviser i canvaskurset aktivere synkronisering af integrationer. Hvert kursus skal aktiveres af en instruktør, for at der kan oprettes en tilsvarende Teams. Der er ingen global mekanisme til oprettelse af Teams. Dette er designet af forsigtighed for at forhindre, at der oprettes uønskede Teams.

Se dokumentationen til [undervisere](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) for at få oplysninger om aktivering af LTI for hvert kursus og fuldførelse af integrationskonfigurationen.
