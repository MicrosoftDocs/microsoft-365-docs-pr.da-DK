---
title: Aktivere rapportmeddelelsen eller phishing-tilføjelses ins
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 4250c4bc-6102-420b-9e0a-a95064837676
ms.collection:
- M365-security-compliance
description: Få mere at vide om, hvordan du aktiverer rapportmeddelelsen eller phishing-tilføjelsesprogrammet rapport til Outlook og Outlook på internettet, for individuelle brugere eller for hele organisationen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 758ee81852d9037ce39cbfdc6f2c2d6ad795aff2
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466819"
---
# <a name="enable-the-report-message-or-the-report-phishing-add-ins"></a>Aktivere rapportmeddelelsen eller phishing-tilføjelses ins

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Hvis du er administrator i en Microsoft 365 organisation med Exchange Online-postkasser, anbefaler vi, at du bruger siden Indsendelser på Microsoft 365 Defender-portalen. Få mere at vide under [Brug administratorindsendelse til at sende mistænkeligt spam, phish, URL-adresser og filer til Microsoft](admin-submission.md).

Tilføjelsesprogrammet Rapportmeddelelse og Phishing til Outlook og Outlook på internettet (tidligere kaldet Outlook Web App) gør det nemt at rapportere falske positive (god mail markeret som dårlig) eller falske negativer (dårlig mail tilladt) til Microsoft og Microsofts associerede selskaber til analyse.

Microsoft bruger disse indsendelser til at forbedre effektiviteten af teknologier til mailbeskyttelse. Antag f.eks., at folk rapporterer mange meddelelser ved hjælp af tilføjelsesprogrammet Rapportphishing. Disse oplysninger vises i sikkerhedsdashboardet og andre rapporter. Organisationens sikkerhedsteam kan bruge disse oplysninger som et tegn på, at antiphishing-politikker muligvis skal opdateres.

Du kan installere enten rapportmeddelelsen eller tilføjelsesprogrammet Rapportphishing. Hvis dine brugere skal rapportere både spam- og phishingmeddelelser, skal du installere tilføjelsesprogrammet Rapportmeddelelse i organisationen.

Tilføjelsesprogrammet Rapportmeddelelse giver mulighed for at rapportere både spam- og phishingmeddelelser. Administratorer kan aktivere tilføjelsesprogrammet Rapportmeddelelse for organisationen, og individuelle brugere kan selv installere det.

Tilføjelsesprogrammet Rapportphishing giver mulighed for kun at rapportere phishingmeddelelser. Administratorer kan aktivere tilføjelsesprogrammet Report Phishing for organisationen, og individuelle brugere kan selv installere det.

Hvis du er individuel bruger, kan du aktivere begge tilføjelsesprogrammet for dig selv.

Hvis du er global administrator eller Exchange Online-administrator, og Exchange er konfigureret til at bruge OAuth-godkendelse, kan du aktivere tilføjelsesprogrammet Rapportmeddelelse og tilføjelsesprogrammet Rapportphishing for organisationen. Begge tilføjelser er nu tilgængelige via [Centraliseret udrulning](../../admin/manage/centralized-deployment-of-add-ins.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Både tilføjelsesprogrammet Rapportmeddelelse og tilføjelsesprogrammet Report Phishing fungerer med de fleste Microsoft 365 og følgende produkter:
  - Outlook på internettet
  - Outlook 2013 SP1 eller nyere
  - Outlook 2016 til Mac
  - Outlook inkluderet Microsoft 365 apps til store virksomheder
  - Outlook-app til iOS og Android

- Begge tilføjelser er ikke tilgængelige for delte postkasser.

- Begge tilføjelser er ikke tilgængelige for lokale Exchange postkasser. 

- Din eksisterende webbrowser bør fungere med både tilføjelsesprogrammet Rapportmeddelelse og Rapportér phishing. Men hvis du bemærker, at tilføjelsesprogrammet ikke er tilgængeligt eller ikke fungerer som forventet, kan du prøve en anden browser.

- Organisationen skal konfigureres til at bruge OAuth-godkendelse til organisationsinstallationer. Du kan finde flere oplysninger [i Finde ud af, om Centraliseret udrulning af tilføjelses ins fungerer for din organisation](../../admin/manage/centralized-deployment-of-add-ins.md).

- Administratorer skal være medlem af rollegruppen Globale administratorer. Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

- Du kan finde flere oplysninger om, hvordan du rapporterer en meddelelse ved hjælp af funktionen Rapportmeddelelse, under Rapportere falske [positive og falske negativer Outlook](report-false-positives-and-false-negatives.md).

- Organisationer, der har en URL-filtrering eller sikkerhedsløsning (f.eks. en proxy og/eller firewall) på plads, skal have ipagave.azurewebsites.net- og outlook.office.com-slutpunkter tilladt at blive nået på HTTPS-protokollen.

### <a name="turn-off-the-built-in-reporting-experience"></a>Slå den indbyggede rapporteringsoplevelse fra

Vi anbefaler ikke den indbyggede rapporteringsoplevelse i Outlook fordi den ikke kan bruge politikken for [brugerindsendelse](./user-submission.md). Vi anbefaler, at du i stedet bruger tilføjelsesprogrammet Rapportmeddelelse eller phishing-tilføjelsesprogrammet Rapport.

Du skal have tildelt tilladelser, før du kan køre denne cmdlet. For at finde de tilladelser, der kræves for at køre en cmdlet eller parameter i din organisation, skal du se Find de nødvendige tilladelser til at køre en Exchange [cmdlet](/powershell/exchange/find-exchange-cmdlet-permissions).

Kør følgende PowerShell-kommando for at deaktivere den indbyggede rapporteringsoplevelse:

```powershell
Set-OwaMailboxPolicy -Identity OwaMailboxPolicy-Default -ReportJunkEmailEnabled $false
```

## <a name="get-the-report-message-add-in"></a>Hent tilføjelsesprogrammet Rapportmeddelelse

### <a name="get-the-report-message-add-in-for-yourself"></a>Hent tilføjelsesprogrammet Rapportmeddelelse til dig selv

1. Gå til Microsoft AppSource på, <https://appsource.microsoft.com/marketplace/apps> og søg efter tilføjelsesprogrammet Rapportmeddelelse. Hvis du vil gå direkte til tilføjelsesprogrammet Rapportmeddelelse, skal du gå til <https://appsource.microsoft.com/product/office/wa104381180>.

2. KLIK **PÅ HENT DEN NU**.

   :::image type="content" source="../../media/ReportMessageGETITNOW.png" alt-text="Rapportmeddelelsen Hent den nu" lightbox="../../media/ReportMessageGETITNOW.png":::

3. Gennemse vilkårene for anvendelse og politikken om beskyttelse af personlige oplysninger i den dialogboks, der vises, og klik derefter på **Fortsæt**.

4. Log på med din arbejds- eller skolekonto (til virksomhedsbrug) eller din Microsoft-konto (til personlig brug).

Når tilføjelsesprogrammet er installeret og aktiveret, får du vist følgende ikoner:

- I Outlook ser ikonet sådan ud:

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/OutlookReportMessageIcon.png" alt-text="Ikonet for tilføjelsesprogrammet Rapportmeddelelse for Outlook" lightbox="../../media/OutlookReportMessageIcon.png":::

- I Outlook på internettet ser ikonet sådan ud:

    > [!div class="mx-imgBorder"]
    > ![Outlook på internettet ikon for tilføjelsesprogrammet Rapportmeddelelse.](../../media/owa-report-message-icon.png)

### <a name="get-the-report-message-add-in-for-your-organization"></a>Hent tilføjelsesprogrammet Rapportmeddelelse for din organisation

> [!NOTE]
> Det kan tage op til 12 timer, før tilføjelsesprogrammet vises i organisationen.

1. I [Microsoft 365 Administration skal](https://admin.microsoft.com/AdminPortal/Home?#/homepage) du gå til **Indstillinger** \> **integrerede apps**. Klik **på Hent apps**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-integrated-apps.png" alt-text="De Microsoft 365 Administration integrerede apps" lightbox="../../media/microsoft-365-admin-center-integrated-apps.png":::


2. På siden **Microsoft 365 Apps**, der vises, skal du klikke i feltet Søg, skrive Rapportmeddelelse og derefter klikke **på ikonet** ![Søg søg.](../../media/search-icon.png) Find og vælg Rapportmeddelelse på listen **over resultater**. 

3. Siden med appoplysninger åbnes. Vælg **Hent den nu**. 

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-report-message.png" alt-text="Tilføjelsesprogrammet Rapportmeddelelse" lightbox="../../media/microsoft-365-admin-center-report-message.png":::

4. Udfyld de grundlæggende profiloplysninger, og klik derefter på **Fortsæt**. 

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-profile-info.png" alt-text="Profilkonfigurationen for tilføjelsesprogrammet Rapportmeddelelse" lightbox="../../media/microsoft-365-admin-center-profile-info.png":::

5. Pop **op-pop op-pop-op-programmet Installér** ny app åbnes. Konfigurer følgende indstillinger. Klik **på Næste** for at gå til den næste side for at fuldføre konfigurationen. 

   - **Tilføj brugere**: Vælg en af følgende værdier:
     - **Bare mig**
     - **Hele organisationen**
     - **Bestemte brugere/grupper**

   - **Installation**:
     - **Acceptér anmodninger om tilladelser**: Læs apptilladelserne og -egenskaberne omhyggeligt, før du går til næste side.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="../../media/microsoft-365-admin-center-deploy-new-app.png" alt-text="Siden Acceptér anmodninger om tilladelser" lightbox="../../media/microsoft-365-admin-center-deploy-new-app.png":::

     - **Afslut** installationen: Gennemse og afslut udrulningen af tilføjelsesprogrammet. 
     - **Installationen er fuldført**: Vælg **Udført** for at fuldføre konfigurationen. 

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="../../media/microsoft-365-admin-center-deployment-complete.png" alt-text="Den meddelelse af installationen, der er fuldført" lightbox="../../media/microsoft-365-admin-center-deployment-complete.png":::

## <a name="edit-settings-for-the-report-message-add-in"></a>Redigeringsindstillinger for tilføjelsesprogrammet Rapportmeddelelse

1. I Microsoft 365 Administration skal du gå til **Indstillinger** \> **integrerede apps** \. Find og vælg **derefter tilføjelsesprogrammet** Rapportmeddelelse.

2. I pop op-menuen, der vises, skal du **vælge Rediger brugere** for at redigere brugerindstillinger.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-report-message-edit.png" alt-text="Pop op-meddelelsen Rapport" lightbox="../../media/microsoft-365-admin-center-report-message-edit.png":::

3. Hvis du vil fjerne tilføjelsesprogrammet, skal du **vælge Fjern app** **under Handlinger** i det samme pop op-pop-op-program. 

## <a name="get-the-report-phishing-add-in"></a>Hent tilføjelsesprogrammet Rapportphishing

### <a name="get-the-report-phishing-add-in-for-yourself"></a>Hent tilføjelsesprogrammet Report Phishing til dig selv

1. Gå til Microsoft AppSource på , <https://appsource.microsoft.com/marketplace/apps> og søg efter tilføjelsesprogrammet Report Phishing.

2. KLIK **PÅ HENT DEN NU**.

3. Gennemse vilkårene for anvendelse og politikken om beskyttelse af personlige oplysninger i den dialogboks, der vises, og klik derefter på **Fortsæt**.

4. Log på med din arbejds- eller skolekonto (til virksomhedsbrug) eller din Microsoft-konto (til personlig brug).

Når tilføjelsesprogrammet er installeret og aktiveret, får du vist følgende ikoner:

- I Outlook ser ikonet sådan ud:

  ![Ikonet rapportér phishing-tilføjelsesprogrammet for Outlook.](../../media/Outlook-ReportPhishing.png)

- I Outlook på internettet ser ikonet sådan ud:

    > [!div class="mx-imgBorder"]
    > ![Outlook på internettet ikon for tilføjelsesprogrammet Rapportér phishing.](../../media/OWA-ReportPhishing.png)

### <a name="get-the-report-phishing-add-in-for-your-organization"></a>Hent tilføjelsesprogrammet Rapportphishing for din organisation

> [!NOTE]
> Det kan tage op til 12 timer, før tilføjelsesprogrammet vises i organisationen.

1. I [Microsoft 365 Administration skal](https://admin.microsoft.com/AdminPortal/Home?#/homepage) du gå til **Indstillinger** \> **integrerede apps**. Klik **på Hent apps**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-integrated-apps.png" alt-text="De Microsoft 365 Administration integrerede apps" lightbox="../../media/microsoft-365-admin-center-integrated-apps.png":::

2. På siden **Microsoft 365 Apps**, der vises, skal du klikke i feltet  Søg, skrive **Rapportphishing** og derefter klikke **på ikonet** ![Søg søg](../../media/search-icon.png). Find og vælg Rapportér phishing på listen **over resultater**. 
 
3. Siden med appoplysninger åbnes. Vælg **Hent den nu**.

4. Udfyld de grundlæggende profiloplysninger, og klik derefter på **Fortsæt**.

5. Pop **op-pop op-pop-op-programmet Installér** ny app åbnes. Følg trinnene ovenfor [for at](enable-the-report-message-add-in.md#get-the-report-message-add-in-for-your-organization) fuldføre konfigurationen. 

## <a name="edit-settings-for-the-report-phishing-add-in"></a>Rediger indstillinger for tilføjelsesprogrammet Rapportphishing

1. I Microsoft 365 Administration skal du gå til **Indstillinger** \> **integrerede apps** \. Find og vælg derefter **Rapportér phishing-tilføjelsesprogrammet** .

2. I pop op-menuen, der vises, skal du **vælge Rediger brugere** for at redigere brugerindstillinger.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-report-phishing-edit.png" alt-text="Pop op-pop op-pop-op-rapporten om phishing" lightbox="../../media/microsoft-365-admin-center-report-phishing-edit.png":::

3. Hvis du vil fjerne tilføjelsesprogrammet, skal du **vælge Fjern app** **under Handlinger** i det samme pop op-pop-op-program. 
