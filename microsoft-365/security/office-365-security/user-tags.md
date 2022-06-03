---
title: Brugerkoder i Microsoft Defender for Office 365
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
description: Administratorer kan få mere at vide om, hvordan de identificerer bestemte grupper af brugere med brugerkoder i Microsoft Defender for Office 365 Plan 2. Kodefiltrering er tilgængelig på tværs af beskeder, rapporter og undersøgelser i Microsoft Defender for Office 365 for hurtigt at identificere de mærkede brugere.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 24509489259a368fb35773603e3708a265f8ed76
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873264"
---
# <a name="user-tags-in-microsoft-defender-for-office-365"></a>Brugerkoder i Microsoft Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for:**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Brugerkoder er id'er for bestemte grupper af brugere i [Microsoft Defender for Office 365](defender-for-office-365.md). Der er to typer brugerkoder:

- **Systemkoder**: [Prioritetskonti](../../admin/setup/priority-accounts.md) er i øjeblikket den eneste type systemkode.
- **Brugerdefinerede mærker**: Du opretter selv disse brugerkoder.

Hvis din organisation har Defender for Office 365 Plan 2 (inkluderet i dit abonnement eller som et tilføjelsesprogram), kan du oprette brugerdefinerede brugerkoder ud over at bruge prioritetskontomærket.

> [!NOTE]
> I øjeblikket kan du kun anvende brugerkoder på postkassebrugere.

Når du har anvendt systemkoder eller brugerdefinerede mærker på brugere, kan du bruge disse mærker som filtre i beskeder, rapporter og undersøgelser:

- [Beskeder](alerts.md)
- [Brugerdefinerede beskedpolitikker](../../compliance/alert-policies.md#viewing-alerts)
- [Trusselsoversigt og registreringer i realtid](threat-explorer.md)
- [Kompromitteret brugerrapport](view-email-security-reports.md#compromised-users-report)
- [Mailobjektside](mdo-email-entity-page.md#other-innovations)
- [Statusrapport om trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report)
- [Rapport over de vigtigste afsendere og modtagere](view-email-security-reports.md#top-senders-and-recipients-report)
- [Simulering af angreb](attack-simulation-training.md#target-users)
- [Kampagnevisninger](campaigns.md)
- [Administration og brugerindsendelser](admin-submission.md)
- [Karantæne](quarantine.md)
- For prioritetskonti kan du bruge [rapporten Mailproblemer for prioritetskonti](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report) i Exchange Administration (EAC).

I denne artikel forklares det, hvordan du konfigurerer brugerkoder på Microsoft 365 Defender-portalen. Der er ingen cmdlet'er i Microsoft 365 Defender portal til administration af brugerkoder.

Hvis du vil se, hvordan brugerkoder er en del af strategien for at beskytte brugerkonti med stor indvirkning, skal du se [Sikkerhedsanbefalinger for prioritetskonti i Microsoft 365](security-recommendations-for-priority-accounts.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Brugerkoder** , skal du bruge <https://security.microsoft.com/securitysettings/userTags>.

- Du skal have tildelt tilladelser på Microsoft 365 Defender-portalen, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil oprette, redigere og slette brugerdefinerede brugerkoder, skal du være medlem af rollegrupperne **Organisationsadministration** eller **Sikkerhedsadministrator** .
  - Hvis du vil tilføje og fjerne medlemmer fra systemkoden Prioritetskonto, skal du være medlem af **sikkerhedsadministratoren** og **Exchange Administration** rollegrupper.
  - Hvis du vil tilføje og fjerne medlemmer fra eksisterende brugerdefinerede brugerkoder, skal du være medlem af rollegrupperne **Organisationsadministration** eller **Sikkerhedsadministrator** .
  - Hvis du vil have skrivebeskyttet adgang til brugerkoder, skal du være medlem af rollegrupperne **Global læser**, **Sikkerhedsoperator** eller **Sikkerhedslæser** .

  Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).

  > [!NOTE]
  >
  > - Tilføjelse af brugere til den tilsvarende Azure Active Directory rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser på Microsoft 365 Defender-portalen _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  >
  > - Administration af brugerkode styres af rollerne **Mærkelæser** og **Kodestyring** .

- Du kan også administrere og overvåge prioritetskonti i Microsoft 365 Administration. Du kan finde instruktioner under [Administrer og overvåg prioritetskonti](../../admin/setup/priority-accounts.md).

- Du kan finde oplysninger om sikring af _privilegerede konti_ (administratorkonti) i [dette emne](/security/compass/critical-impact-accounts).

## <a name="use-the-microsoft-365-defender-portal-to-create-user-tags"></a>Brug Microsoft 365 Defender-portalen til at oprette brugerkoder

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Indstillinger** \> **Mail & brugerkoder til samarbejde**\>. Hvis du vil gå direkte til siden **Brugerkoder** , skal du bruge <https://security.microsoft.com/securitysettings/userTags>.

2. Klik på ![Opret mærkeikon på siden **Brugerkoder**.](../../media/m365-cc-sc-create-icon.png) **Opret mærke**.

3. Guiden **Opret kode** åbnes i et nyt pop op-vindue. Konfigurer følgende indstillinger på siden **Definer mærke** :
   - **Navn**: Angiv et entydigt, beskrivende navn til koden. Dette er den værdi, du får vist og bruger. Bemærk, at du ikke kan omdøbe et mærke, når du har oprettet det.
   - **Beskrivelse**: Angiv en valgfri beskrivelse af koden.

   Klik på **Næste**, når du er færdig.

4. Benyt en af følgende fremgangsmåder på siden **Tildel medlemmer** :
   - Klik på ![ikonet Tilføj medlemmer.](../../media/m365-cc-sc-create-icon.png) **Tilføj medlemmer**. Gør et af følgende for at tilføje individuelle brugere eller grupper i det viste flyv ud:
     - Klik på feltet, og rul gennem listen for at vælge en bruger eller gruppe.
     - Klik i feltet, og begynd at skrive for at filtrere listen og vælge en bruger eller gruppe.
     - Hvis du vil tilføje flere værdier, skal du klikke i et tomt område i feltet.
     - Hvis du vil fjerne individuelle poster, skal du klikke på ![Fjern indtastningsikonet.](../../media/m365-cc-sc-remove-selection-icon.png) ud for posten i feltet.
     - Hvis du vil fjerne alle poster, skal du klikke på ![ikonet Fjern indtastning.](../../media/m365-cc-sc-remove-selection-icon.png) på elementet **Valgte nn brugere og nn grupper** under feltet.

     Klik på **Tilføj**, når du er færdig.

     Tilbage på siden **Tildel medlemmer** kan du også fjerne poster ved at klikke på ![ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) ud for posten.

   - Klik på **Importér** for at vælge en tekstfil, der indeholder mailadresserne på brugerne eller grupperne. Sørg for, at tekstfilen indeholder én post pr. linje.

   Klik på **Næste**, når du er færdig.

5. Gennemse dine indstillinger på siden **Gennemse mærke** , der vises. Du kan vælge **Rediger** i hver sektion for at redigere indstillingerne i sektionen. Du kan også klikke på **Tilbage** eller vælge den specifikke side i guiden.

   Når du er færdig, skal du klikke på **Send** og derefter klikke på **Udført**.

## <a name="use-the-microsoft-365-defender-portal-to-view-user-tags"></a>Brug Microsoft 365 Defender-portalen til at få vist brugerkoder

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Indstillinger** \> **Mail & brugerkoder til samarbejde**\>. Hvis du vil gå direkte til siden **Brugerkoder** , skal du bruge <https://security.microsoft.com/securitysettings/userTags>.

2. På siden **Brugerkoder** vises følgende egenskaber på listen over brugerkoder:

   - **Mærke**: Navnet på brugerkoden. Bemærk, at dette omfatter det indbyggede **systemmærke prioritetskonto** .
   - **Anvendt på**: Antallet af medlemmer
   - **Senest ændret**
   - **Oprettet den**

3. Når du vælger et brugermærke ved at klikke på navnet, vises oplysningerne i et pop op-vindue.

## <a name="use-the-microsoft-365-defender-portal-to-modify-user-tags"></a>Brug Microsoft 365 Defender-portalen til at redigere brugerkoder

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Indstillinger** \> **Mail & brugerkoder til samarbejde**\>. Hvis du vil gå direkte til siden **Brugerkoder** , skal du bruge <https://security.microsoft.com/securitysettings/userTags>.

2. På siden **Brugerkoder** skal du vælge brugermærket på listen og derefter klikke på ![Ikonet Rediger mærke.](../../media/m365-cc-sc-edit-icon.png) **Rediger kode**.

3. I det pop op-vindue med detaljer, der vises, er den samme guide og de samme indstillinger tilgængelige som beskrevet i afsnittet [Brug Microsoft 365 Defender-portalen til at oprette brugerkoder](#use-the-microsoft-365-defender-portal-to-create-user-tags) tidligere i denne artikel.

   **Noter**:

   - Siden **Definer kode** er ikke tilgængelig for det indbyggede **systemmærke Prioritetskonto** , så du kan ikke omdøbe koden eller ændre beskrivelsen.
   - Du kan ikke omdøbe et brugerdefineret mærke, men du kan ændre beskrivelsen.

## <a name="use-the-microsoft-365-defender-portal-to-remove-user-tags"></a>Brug Microsoft 365 Defender-portalen til at fjerne brugerkoder

> [!NOTE]
> Du kan ikke fjerne det indbyggede **systemmærke prioritetskonto** .

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Indstillinger** \> **Mail & brugerkoder til samarbejde**\>. Hvis du vil gå direkte til siden **Brugerkoder** , skal du bruge <https://security.microsoft.com/securitysettings/userTags>.

2. På siden **Brugerkoder** skal du vælge brugermærket på listen og derefter klikke på ![Ikonet Slet mærke.](../../media/m365-cc-sc-delete-icon.png) **Slet mærke**.

3. Læs advarslen i den bekræftelsesdialogboks, der vises, og klik derefter på **Ja, fjern**.

## <a name="more-information"></a>Flere oplysninger

[Konfigurer og gennemse prioritetskonti i Microsoft Defender for Office 365](configure-review-priority-account.md)
