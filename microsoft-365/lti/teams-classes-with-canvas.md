---
title: Brug Microsoft Teams-hold med lærred
ms.author: danismith
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
description: Integrer Microsoft Teams-klasser med lærred
ms.openlocfilehash: 10024e124ce50ab542e6e68a5c237a47e1f7af83
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923013"
---
# <a name="use-microsoft-teams-classes-with-canvas"></a>Brug Microsoft Teams-hold med lærred

Microsoft Teams-klasser er en LTI-app (Learning Tools Interoperability), der hjælper undervisere og studerende med nemt at navigere mellem deres LMS (Learning Management System) og Teams. Brugerne kan få adgang til deres klasseteams, der er knyttet til deres kursus, direkte fra deres LMS.

## <a name="prerequisites-before-deployment"></a>Forudsætninger før udrulning

> [!NOTE]
> De aktuelle Teams-klasser LTI understøtter kun synkronisering af lærredsbrugere med Microsoft Azure Active Directory (AAD) i et begrænset omfang.
>
> - Din lejer skal have en Microsoft Education-licens (A1 eller nyere).
> - Det er kun en enkelt Microsoft-lejer, der kan bruges til at tilknytte brugere mellem lærred og Microsoft.
> - Din lejer skal have et nøjagtigt match mellem et lærredsfelt (mail, entydigt bruger-id, SIS-id eller integrations-id) og et felt i AAD (Brugerens hovednavn (UPN), Primær mailadresse (Mail) eller Mailalias (mailNickname)).
> - Hvis du bruger SDS til at oprette klasser og grupper, anbefaler vi, at du deaktiverer indstillingen Teamoprettelse i SDS og udfører en [gruppeoprydning](/schooldatasync/group-cleanup) for at undgå duplikering af klasser. SDS kan stadig bruges til at synkronisere organisations- og brugerdata.

## <a name="enable-the-microsoft-teams-app-in-canvas"></a>Aktivér Microsoft Teams-appen på lærredet

Hvis du vil starte integrationen, skal du aktivere appen på lærredet ved at aktivere udviklernøglerne, aktivere Microsoft Teams-synkronisering og godkende Microsoft-Teams-synkroniserings-for-lærredsappen. Bemærk, at godkendelse af appen kun kan udføres af en Microsoft-lejeradministrator, der kan godkende apps.

**Sådan aktiverer du Microsoft Teams-synkronisering og -godkendelse af adgang til appen**:

1. Log på Lærred som administrator.

2. Vælg linket **Administrator** i den globale navigation, og vælg derefter din konto.
3. I administrationsnavigationen skal du vælge linket **Udviklernøgler** og derefter vælge fanen **Nedarvet** .
4. Aktivér de LTI-apps, du vil udrulle, ved at vælge tilstanden **ON** for hver af de relevante apps.

5. I administrationsnavigationen skal du vælge linket **Indstillinger** og derefter fanen **Integrationer** .

6. Aktivér Microsoft Teams-synkronisering ved at slå til/fra-knappen til. Denne synkronisering gør det muligt at oprette klasser i Teams baseret på tilmeldingen af et kursus.

   ![Lærredsteams synkroniserer opdateret png.](https://user-images.githubusercontent.com/87142492/128225881-abdfc52d-dc9e-48ad-aec5-f6617c6436f3.png)

7. Udfyld følgende felter med de relevante oplysninger. Disse felter bruges til at matche brugere på lærredet med brugere i AAD.
   - **Lejernavnet** er dit Microsoft-lejernavn.
   - **Logonattributten** er en af følgende lærredsbrugerattributter, der bruges til tilknytning:
      - **Mail** er lærredsbrugerens standardmailadresse. Hvis brugerne ændrer deres standardmailadresse på lærredet, kan deres tilmelding til et kursus blive blokeret fra at synkronisere til Teams.
      - **Entydigt bruger-id** er brugerens lærredslogon-id.
      - **SIS-bruger-id** er den id-værdi, der udfyldes fra Student Information System (SIS), og som kan ses på brugerens profilside.
      - **Integrations-id** udfyldes kun via SIS-import og kan ses på brugerens profilside. Dette entydige id leveres typisk af institutionen og bruges i kontotillidsforhold eller konsortier til at identificere brugere på tværs af flere konti.

   - Feltet **Suffiks** er valgfrit og giver dig mulighed for at angive et domæne, når der ikke er en nøjagtig tilknytning mellem lærredsattributter og Microsoft AAD-felter. Hvis din lærredsmail f.eks. er 'name@example.edu', mens UPN'et i Microsoft AAD er 'navn', kan du matche brugerne ved at angive '@example.edu' i suffiksfeltet. Domænet skal angives i dette felt med den foregående @.
   - Active Directory-opslagsattributten er det felt i AAD, som lærredsattributterne stemmer overens med. Vælg mellem UPN, primær mailadresse eller mailaliasset.

8. Vælg **Opdater indstillinger**.

9. Hvis du vil godkende adgang til Lærredets **Microsoft-Teams-Sync-for-Canvas Azure-app** , skal du vælge linket **Tildel lejeradgang** . Du bliver omdirigeret til slutpunktet for Samtykke for Microsoft Identity Platform-administrator.

   ![Tilladelser.](media/permissions.png)

   > [!NOTE]
   > Dette trin skal udføres af en Microsoft-lejeradministrator, der kan godkende apps.

10. Vælg **Acceptér**.

## <a name="integrate-teams-classes-lti-in-canvas"></a>Integrer Teams-klasse-LTI på lærred

Når du har aktiveret synkroniseringen og godkendt Azure-appen, kan lærredsadministratoren nu føje Teams-klasse-LTI-appen til lærredsmiljøet, så den vises i navigationen i lærredets brugergrænseflade.

**Sådan føjer du Teams-klasse-LTI-appen til lærredsmiljøet**:

1. Under fanen **Apps** i **Administratorindstillinger** skal du vælge **+ App** for at tilføje Teams LTI-apps.

   ![eksterne apps.](media/external-apps.png)

2. Vælg **Efter klient-id** som **Konfigurationstype**.

   ![tilføj app.](media/add-app.png)

3. Angiv **170000000000570** for LTI-klasserne i Microsoft Teams for **Klient-id**, og vælg derefter **Send**.

4. I den bekræftelse, der vises, skal du bekræfte appnavnet (Microsoft Teams-klasser) og derefter vælge **Installér**.

   LTI-appen til Microsoft Teams-klasser føjes nu til listen over eksterne apps.

## <a name="enabling-the-lti-app-for-canvas-courses"></a>Aktivering af LTI-appen for lærredskurser

Hvis du vil bruge LTI-appen i et kursus, skal en underviser i canvaskurset aktivere synkronisering af integrationer. Hvert kursus skal aktiveres af en instruktør, for at et tilsvarende team kan oprettes. der ikke er nogen global mekanisme til oprettelse af teams. Dette er udformet som en forholdsregel for at forhindre, at der oprettes uønskede teams.

Se dokumentationen til [underviseren](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) for at få oplysninger om, hvordan du aktiverer LTI-appen for hvert kursus og fuldfører integrationskonfigurationen.
