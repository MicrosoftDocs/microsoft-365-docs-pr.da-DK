---
title: Brugertags i Microsoft Defender til Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 12/17/2021
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorer kan lære, hvordan de identificerer bestemte grupper af brugere med brugermærker i Microsoft Defender Office 365 Plan 2. Filtrering af mærker er tilgængelig på tværs af beskeder, rapporter og undersøgelser i Microsoft Defender for Office 365 hurtigt at identificere de mærkede brugere.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f6a5262b184e5785695d73be32080adb8b44109c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63589819"
---
# <a name="user-tags-in-microsoft-defender-for-office-365"></a>Brugertags i Microsoft Defender til Office 365

Brugermærker er identifikatorer for bestemte grupper af brugere [i Microsoft Defender Office 365](defender-for-office-365.md). Der findes to typer brugermærker:

- **Systemmærker**: [Prioritetskonti er i](../../admin/setup/priority-accounts.md) øjeblikket den eneste type systemmærke.
- **Brugerdefinerede mærker**: Du opretter selv disse brugermærker.

Hvis din organisation har Defender til Office 365 Plan 2 (inkluderet i dit abonnement eller som et tilføjelsesprogrammet), kan du oprette brugerdefinerede brugermærker ud over at bruge mærket prioritetskonti.

> [!NOTE]
> I øjeblikket kan du kun anvende brugermærker på postkassebrugere.

Når du anvender systemmærker eller brugerdefinerede mærker for brugere, kan du bruge disse mærker som filtre i beskeder, rapporter og undersøgelser:

- [Beskeder](alerts.md)
- [Brugerdefinerede beskedpolitikker](../../compliance/alert-policies.md#viewing-alerts)
- [Trusselsstifinder og registreringer i realtid](threat-explorer.md)
- [Siden Mailenhed](mdo-email-entity-page.md#other-innovations)
- [Statusrapport over trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report)
- [Kampagnevisninger](campaigns.md)
- [Administrator- og brugerindsendelser](admin-submission.md)
- [Karantæne](quarantine.md)
- For prioritetskonti kan du bruge [rapporten Mailproblemer for](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report) prioritetskonti i Exchange Administration (EAC).

I denne artikel forklares det, hvordan du konfigurerer brugermærker Microsoft 365 Defender portalen. Der er ingen cmdlet'er i Microsoft 365 Defender til at administrere brugermærker.

Hvis du vil se, hvordan brugermærker er en del af en strategi for at beskytte brugerkonti med høj effekt, skal du se Sikkerhedsanbefalinger [for prioritetskonti Microsoft 365](security-recommendations-for-priority-accounts.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til siden **Brugermærker** skal du bruge <https://security.microsoft.com/securitysettings/userTags>.

- Du skal have tildelt tilladelser i Microsoft 365 Defender, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil oprette, redigere og slette brugerdefinerede brugermærker, skal du være medlem af **rollegrupperne Organisationsadministration** **eller Sikkerhedsadministrator** .
  - Hvis du vil tilføje og fjerne medlemmer fra systemmærket Prioritetskonto, skal du være medlem af sikkerhedsadministratoren **og Exchange administratorrollegrupper**.
  - Hvis du vil tilføje og fjerne medlemmer fra eksisterende brugerdefinerede brugermærker, skal du være medlem af **rollegrupperne Organisationsadministration** **eller Sikkerhedsadministrator** .
  - For skrivebeskyttet adgang til brugermærker skal du være medlem af **rollegrupperne Global læser****,** Sikkerhedsoperator eller **Sikkerhedslæser**.

  Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

  > [!NOTE]
  >
  > - Når du føjer brugere til den tilsvarende Azure Active Directory-rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser i _Microsoft 365 Defender-portalen og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).
  >
  > - Administration af brugertag styres af **rollerne Mærkelæser** **og Mærkeadministrator** .

- Du kan også administrere og overvåge prioritetskonti i Microsoft 365 Administration. Du kan finde en vejledning [under Administrere og overvåge prioritetskonti](../../admin/setup/priority-accounts.md).

- Du kan finde oplysninger om _beskyttelse af privilegerede_ konti (administratorkonti) [i dette emne](/azure/architecture/framework/security/critical-impact-accounts).

## <a name="use-the-microsoft-365-defender-portal-to-create-user-tags"></a>Brug Microsoft 365 Defender til at oprette brugermærker

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>**gå til Indstillinger** \> **Mail & samarbejde** \> **Brugermærker**. For at gå direkte til siden **Brugermærker** skal du bruge <https://security.microsoft.com/securitysettings/userTags>.

2. Klik på **Opret mærkeikon** på siden ![Brugermærker.](../../media/m365-cc-sc-create-icon.png) **Opret mærke**.

3. Guiden **Opret mærke** åbnes i et nyt pop op-vindue. På siden **Definer** mærke skal du konfigurere følgende indstillinger:
   - **Navn**: Angiv et entydigt, beskrivende navn til koden. Dette er den værdi, du kan se og bruge. Bemærk, at du ikke kan omdøbe et mærke, efter at du har oprettet det.
   - **Beskrivelse**: Angiv en valgfri beskrivelse af koden.

   Klik på Næste, når du er **færdig**.

4. Gør et **af følgende** på siden Tildel medlemmer:
   - Klik ![på ikonet Tilføj medlemmer.](../../media/m365-cc-sc-create-icon.png) **Tilføj medlemmer**. I det pop op-vindue, der vises, skal du gøre et af følgende for at tilføje individuelle brugere eller grupper:
     - Klik i feltet, og rul gennem listen for at vælge en bruger eller gruppe.
     - Klik i feltet, og begynd at skrive for at filtrere listen og vælge en bruger eller gruppe.
     - Hvis du vil tilføje flere værdier, skal du klikke i et tomt område i feltet.
     - Hvis du vil fjerne individuelle poster, skal du klikke på ![Ikonet Fjern indtastning.](../../media/m365-cc-sc-remove-selection-icon.png) ud for indtastningen i feltet.
     - Hvis du vil fjerne alle poster, skal du klikke på ![ikonet Fjern post.](../../media/m365-cc-sc-remove-selection-icon.png) på elementet **Valgte nn-brugere og nn-grupper** under feltet.

     Klik på Tilføj, når du er **færdig**.

     Tilbage på siden **Tildel** medlemmer kan du også fjerne poster ved at klikke på ikonet ![Slet.](../../media/m365-cc-sc-delete-icon.png) ud for posten.

   - Klik **på Importér** for at markere en tekstfil, der indeholder mailadresserne på brugerne eller grupperne. Sørg for, at tekstfilen indeholder ét element pr. linje.

   Klik på Næste, når du er **færdig**.

5. På siden **Gennemse mærke,** der vises, skal du gennemse dine indstillinger. Du kan vælge **Rediger** i hver sektion for at ændre indstillingerne i sektionen. Eller du kan klikke **på** Tilbage eller vælge den bestemte side i guiden.

   Når du er færdig, skal du klikke **på Send** og derefter klikke på **Udført**.

## <a name="use-the-microsoft-365-defender-portal-to-view-user-tags"></a>Brug af Microsoft 365 Defender til at få vist brugermærker

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>**gå til Indstillinger** \> **Mail & samarbejde** \> **Brugermærker**. For at gå direkte til siden **Brugermærker** skal du bruge <https://security.microsoft.com/securitysettings/userTags>.

2. På **siden Brugermærker** vises følgende egenskaber på listen over brugermærker:

   - **Mærke**: Navnet på brugermærket. Bemærk, at dette omfatter det indbyggede **prioritetskontosystemmærke** .
   - **Anvendt på**: Antallet af medlemmer
   - **Senest ændret**
   - **Oprettet den**

3. Når du vælger et brugermærke ved at klikke på navnet, vises oplysningerne i en pop op-meddelelse.

## <a name="use-the-microsoft-365-defender-portal-to-modify-user-tags"></a>Brug portalen Microsoft 365 Defender til at redigere brugermærker

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>**gå til Indstillinger** \> **Mail & samarbejde** \> **Brugermærker**. For at gå direkte til siden **Brugermærker** skal du bruge <https://security.microsoft.com/securitysettings/userTags>.

2. På siden **Brugermærker** skal du vælge brugermærket på listen og derefter klikke på Rediger ![mærkeikon.](../../media/m365-cc-sc-edit-icon.png) **Rediger mærke**.

3. I pop op-menuen med oplysninger er den samme guide og de samme indstillinger tilgængelige som beskrevet i afsnittet [Brug Microsoft 365 Defender-portalen](#use-the-microsoft-365-defender-portal-to-create-user-tags) til at oprette brugermærker tidligere i denne artikel.

   **Bemærkninger**:

   - Siden **Definer** mærke er ikke tilgængelig for **det indbyggede** prioritetskontosystemmærke, så du kan ikke omdøbe dette mærke eller ændre beskrivelsen.
   - Du kan ikke omdøbe et brugerdefineret mærke, men du kan ændre beskrivelsen.

## <a name="use-the-microsoft-365-defender-portal-to-remove-user-tags"></a>Brug portalen Microsoft 365 Defender til at fjerne brugermærker

> [!NOTE]
> Du kan ikke fjerne det indbyggede **prioritetskontosystemmærke** .

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>**gå til Indstillinger** \> **Mail & samarbejde** \> **Brugermærker**. For at gå direkte til siden **Brugermærker** skal du bruge <https://security.microsoft.com/securitysettings/userTags>.

2. På siden **Brugermærker** skal du vælge brugermærket på listen og derefter klikke på Slet ![mærkeikonet.](../../media/m365-cc-sc-delete-icon.png) **Slet mærke**.

3. Læs advarslen i den bekræftelsesdialogboks, der vises, og klik derefter **på Ja, fjern**.
