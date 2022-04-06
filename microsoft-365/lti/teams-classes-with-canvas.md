---
title: Brug Microsoft Teams klasser med Lærred
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
description: Integrer Microsoft Teams klasser med Lærred
ms.openlocfilehash: 08edb2065cd91ccb0e0d52290dfe83f8a3e60392
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568998"
---
# <a name="use-microsoft-teams-classes-with-canvas"></a>Brug Microsoft Teams klasser med Lærred

Microsoft Teams-klasser er en LTI-app (Learning Tools Interoperability), der gør det nemt for undervisere og studerende at navigere mellem deres Learning Management System (LMS) og Teams. Brugere kan få adgang til deres klasseteams, der er knyttet til deres kursus, direkte fra deres LMS.

## <a name="prerequisites-before-deployment"></a>Forudsætninger før udrulning

> [!NOTE]
> De aktuelle Teams klasser LTI understøtter kun synkronisering af Lærred-brugere med Microsoft Azure Active Directory (AAD) i et begrænset omfang.
>
> - Din lejer skal have en Microsoft Education-licens (A1 eller nyere).
> - Kun en enkelt Microsoft-lejer kan bruges til at tilknytte brugere mellem Canvas og Microsoft.
> - Din lejer skal have et nøjagtigt match mellem et lærredsfelt (mail, entydigt bruger-id, SIS-id eller integrations-id) og et felt i AAD (BRUGERENS hovednavn (UPN), primær mailadresse (mail) eller mailalias (mailNickname)).
> - Hvis du bruger SDS til at oprette klasser og grupper, anbefaler vi, at du deaktiverer indstillingen Oprettelse af team i SDS og udfører en gruppeoprydning for at undgå duplikering af klasser.[](/schooldatasync/group-cleanup) SDS kan stadig bruges til at synkronisere organisations- og brugerdata.

## <a name="enable-the-microsoft-teams-app-in-canvas"></a>Aktivér Microsoft Teams i Lærred

For at starte integrationen skal du aktivere appen i Lærred ved at aktivere udviklernøglerne, aktivere Microsoft Teams-synkroniseringen og godkende appen Microsoft-Teams-Sync-for-Canvas. Bemærk, at godkendelse af appen kun kan udføres af en Microsoft-lejeradministrator, der kan godkende apps.

**Sådan aktiveres Microsoft Teams synkronisere og godkende adgang for appen**:

1. Log på Lærred som administrator.

2. Vælg linket **Administrator** i den globale navigation, og vælg derefter din konto.
3. I administratornavigationen skal du **vælge linket Udviklernøgler** og derefter vælge **fanen Nedarvet** .
4. Aktivér de LTI-apps, du vil installere, ved at **vælge ON-tilstanden** for hver af de relevante apps.

5. I administrationsnavigationen skal **du Indstillinger** **navigationslinket** og derefter fanen Integrationer.

6. Aktivér Microsoft Teams synkronisering ved at slå til/fra-knappen til. Denne synkronisering gør det muligt at oprette klasser i Teams baseret på tilmeldingen af et kursus.

   ![Canvas Teams Sync Updated png.](https://user-images.githubusercontent.com/87142492/128225881-abdfc52d-dc9e-48ad-aec5-f6617c6436f3.png)

7. Udfyld følgende felter med de relevante oplysninger. Disse felter bruges til at matche brugere i Lærred med brugere i AAD.
   - **Lejernavnet er** dit Microsoft-lejernavn.
   - **Logonattributten** er en af følgende Lærred-brugerattributter, der bruges til tilknytning:
      - **Mail** er Lærred-brugerens standardmailadresse. Hvis brugerne ændrer deres standardmailadresse i Lærred, kan deres tilmelding til et kursus være blokeret fra at synkronisere til Teams.
      - **Entydigt bruger-id** er brugerens Logon-id til Lærred.
      - **SIS-bruger-id** er den id-værdi, der er udfyldt fra elevinformationssystemet (SIS), og som kan vises på brugerens profilside.
      - **Integrations-id** udfyldes kun via SIS-import og kan vises på brugerens profilside. Typisk leveres denne entydig identifier af institutionen og bruges i kontotillidsforhold eller -sammenhænge til at identificere brugere på tværs af flere konti.

   - Feltet **Suffiks** er valgfrit og gør det muligt at angive et domæne, når der ikke er en nøjagtig tilknytning mellem lærredsattributter og Microsoft AAD felter. Hvis din Lærred-mail f.eks. er "name@example.edu", mens UPN i Microsoft AAD er "navn", kan du matche brugerne ved at indtaste "@example.edu" i suffiksfeltet. Domænet skal angives i dette felt med det foregående @.
   - Active Directory-opslagsattributten er det felt i AAD, som lærredsattributter passer til. Vælg mellem UPN, primær mailadresse eller mailalias.

8. Vælg **Opdater Indstillinger**.

9. Hvis du vil godkende adgang til Canvas **Microsoft-Teams-Sync-for-Canvas Azure-app**, skal du vælge **linket Giv lejer** adgang. Du bliver omdirigeret til slutpunktet for administratorsamtykke i Microsoft Identity Platform.

   ![tilladelser.](media/permissions.png)

   > [!NOTE]
   > Dette trin skal udføres af en Microsoft-lejeradministrator, der kan godkende apps.

10. Vælg **Acceptér**.

## <a name="integrate-teams-classes-lti-in-canvas"></a>Integrer Teams klasser LTI i Lærred

Når synkroniseringen er aktiveret og godkendt Azure-appen, kan Canvas-administratoren nu føje LTI-appen Teams-klasser til Lærred-miljøet, så den vises i navigationen i lærredets brugergrænseflade.

**Sådan føjer du Teams klasse-LTI-appen til lærredsmiljøet**:

1. På fanen **Apps** i **Administratorindstillinger skal du** vælge **+ App for** at tilføje Teams LTI-apps.

   ![eksterne apps.](media/external-apps.png)

2. Ud **for Konfigurationstype** skal du **vælge Efter klient-id**.

   ![tilføj app.](media/add-app.png)

3. For **Klient-id** skal **du 170000000000570** for Microsoft Teams klasserne LTI og derefter vælge **Send**.

4. I bekræftelsen, der vises, skal du bekræfte appnavnet (Microsoft Teams klasser) og derefter vælge **Installér**.

   Den Microsoft Teams klasser LTI app er nu føjet til listen over eksterne apps.

## <a name="enabling-the-lti-app-for-canvas-courses"></a>Aktivering af LTI-appen til Canvas-kurser

Hvis du vil bruge LTI-appen i et kursus, skal underviseren i lærredskursus aktivere synkronisering af integrationer. Hvert kursus skal aktiveres af en underviser, for at et tilsvarende team kan oprettes. er der ingen global mekanisme til oprettelse af teams. Dette er designet som en sikkerhedsforanstaltning for at forhindre, at der oprettes uønskede teams.

Henvis underviserne til [underviserens dokumentation](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) til aktivering af LTI-appen for hvert kursus og fuldførelse af integrationskonfigurationen.
