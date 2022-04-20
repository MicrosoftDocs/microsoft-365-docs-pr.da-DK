---
title: Aktivér rapportmeddelelsen eller tilføjelsesprogrammer til rapport phishing
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
description: Få mere at vide om, hvordan du aktiverer tilføjelsesprogrammer til rapportmeddelelse eller rapport phishing for Outlook og Outlook på internettet, for individuelle brugere eller for hele organisationen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 14d59cbe6f3f98aabc231da88e4f0919a3974c97
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64973217"
---
# <a name="enable-the-report-message-or-the-report-phishing-add-ins"></a>Aktivér rapportmeddelelsen eller tilføjelsesprogrammer til rapport phishing

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Hvis du er administrator i en Microsoft 365 organisation med Exchange Online postkasser, anbefaler vi, at du bruger siden **Indsendelser** på Microsoft 365 Defender-portalen. Du kan få flere oplysninger under [Brug indsendelse af administratorer til at sende mistanke om spam, phish, URL-adresser og filer til Microsoft](admin-submission.md).

Tilføjelsesprogrammerne Rapportmeddelelse og Rapport phishing til Outlook og Outlook på internettet (tidligere kendt som Outlook Web App) gør det nemt at rapportere falske positiver (god mail markeret som dårlige) eller falske negativer (dårlig mail er tilladt) til Analyse til Microsoft og microsofts associerede virksomheder.

Microsoft bruger disse indsendelser til at forbedre effektiviteten af mailbeskyttelsesteknologier. Antag f.eks., at folk rapporterer mange meddelelser ved hjælp af tilføjelsesprogrammet Rapport phishing. Disse oplysninger vises i sikkerhedsdashboardet og andre rapporter. Organisationens sikkerhedsteam kan bruge disse oplysninger som en indikation af, at politikker til bekæmpelse af phishing muligvis skal opdateres.

Du kan installere tilføjelsesprogrammet Rapportmeddelelse eller Rapport phishing. Hvis du vil have, at dine brugere skal rapportere både spam- og phishing-meddelelser, skal du installere tilføjelsesprogrammet Rapportmeddelelse i din organisation.

Tilføjelsesprogrammet Rapportmeddelelse giver mulighed for at rapportere både spam- og phishing-meddelelser. Administratorer kan aktivere tilføjelsesprogrammet Rapportmeddelelse for organisationen, og individuelle brugere kan selv installere det.

Tilføjelsesprogrammet Rapport phishing giver mulighed for kun at rapportere phishing-meddelelser. Administratorer kan aktivere tilføjelsesprogrammet Rapport phishing for organisationen, og individuelle brugere kan selv installere det.

Hvis du er individuel bruger, kan du selv aktivere begge tilføjelsesprogrammer.

Hvis du er global administrator eller Exchange Online administrator, og Exchange er konfigureret til at bruge OAuth-godkendelse, kan du aktivere tilføjelsesprogrammet Rapportmeddelelse og tilføjelsesprogrammet Rapport phishing for din organisation. Begge tilføjelsesprogrammer er nu tilgængelige via [Centraliseret installation](../../admin/manage/centralized-deployment-of-add-ins.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Både tilføjelsesprogrammet Rapportmeddelelse og tilføjelsesprogrammet Rapport phishing fungerer sammen med de fleste Microsoft 365 abonnementer og følgende produkter:
  - Outlook på internettet
  - Outlook 2013 SP1 eller nyere
  - Outlook 2016 til Mac
  - Outlook inkluderet i Microsoft 365 apps til Enterprise
  - Outlook app til iOS og Android

- Begge tilføjelsesprogrammer er ikke tilgængelige for delte postkasser.

- Begge tilføjelsesprogrammer er ikke tilgængelige for postkasser i det lokale miljø Exchange. 

- Din eksisterende webbrowser bør fungere med tilføjelsesprogrammer til rapportmeddelelse og rapport phishing. Men hvis du bemærker, at tilføjelsesprogrammet ikke er tilgængeligt eller ikke fungerer som forventet, kan du prøve en anden browser.

- I forbindelse med organisationsinstallationer skal organisationen konfigureres til at bruge OAuth-godkendelse. Du kan finde flere oplysninger under [Find ud af, om central installation af tilføjelsesprogrammer fungerer for din organisation](../../admin/manage/centralized-deployment-of-add-ins.md).

- Administratorer skal være medlem af rollegruppen Globale administratorer. Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).

- Du kan få flere oplysninger om, hvordan du rapporterer en meddelelse ved hjælp af funktionen Rapportér meddelelse under [Rapportér falske positiver og falske negativer i Outlook](report-false-positives-and-false-negatives.md).

- Organisationer, der har en URL-filtrerings- eller sikkerhedsløsning (f.eks. en proxy og/eller firewall), skal have ipagave.azurewebsites.net og outlook.office.com slutpunkter, der kan nås på HTTPS-protokollen.

## <a name="get-the-report-message-add-in"></a>Hent tilføjelsesprogrammet Rapportmeddelelse

### <a name="get-the-report-message-add-in-for-yourself"></a>Hent tilføjelsesprogrammet Rapportmeddelelse til dig selv

1. Gå til Microsoft AppSource på <https://appsource.microsoft.com/marketplace/apps> , og søg efter tilføjelsesprogrammet Rapportmeddelelse. Hvis du vil gå direkte til tilføjelsesprogrammet Rapportmeddelelse, skal du gå til <https://appsource.microsoft.com/product/office/wa104381180>.

2. Klik på **HENT DET NU**.

   :::image type="content" source="../../media/ReportMessageGETITNOW.png" alt-text="Rapportmeddelelsen Hent det nu" lightbox="../../media/ReportMessageGETITNOW.png":::

3. Gennemse vilkårene for anvendelse og politik om beskyttelse af personlige oplysninger i den dialogboks, der vises, og klik derefter på **Fortsæt**.

4. Log på med din arbejds- eller skolekonto (til virksomhedsbrug) eller din Microsoft-konto (til personlig brug).

Når tilføjelsesprogrammet er installeret og aktiveret, får du vist følgende ikoner:

- I Outlook ser ikonet sådan ud:

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/OutlookReportMessageIcon.png" alt-text="Tilføjelsesprogrammet Rapportmeddelelse for Outlook" lightbox="../../media/OutlookReportMessageIcon.png":::

- I Outlook på internettet ser ikonet sådan ud:

    > [!div class="mx-imgBorder"]
    > ![Outlook på internettet ikon for tilføjelsesprogrammet Rapportmeddelelse.](../../media/owa-report-message-icon.png)

### <a name="get-the-report-message-add-in-for-your-organization"></a>Hent tilføjelsesprogrammet Rapportmeddelelse for din organisation

> [!NOTE]
> Det kan tage op til 12 timer, før tilføjelsesprogrammet vises i din organisation.

1. I [Microsoft 365 Administration](https://admin.microsoft.com/AdminPortal/Home?#/homepage) skal du gå til **Indstillinger** \> **integrerede apps**. Klik på **Hent apps**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-integrated-apps.png" alt-text="De Microsoft 365 Administration integrerede apps" lightbox="../../media/microsoft-365-admin-center-integrated-apps.png":::

2. På den **Microsoft 365 Apps** side, der vises, skal du klikke i feltet **Søg**, angive **Rapportmeddelelse** og derefter klikke på søgeikonet **Søg**![.](../../media/search-icon.png) Find og vælg **Rapportmeddelelse** på listen over resultater. 

3. Siden med oplysninger om appen åbnes. Vælg **Hent det nu**. 

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-report-message.png" alt-text="Tilføjelsesprogrammet Rapportmeddelelse" lightbox="../../media/microsoft-365-admin-center-report-message.png":::

4. Udfyld de grundlæggende profiloplysninger, og klik derefter på **Fortsæt**. 

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-profile-info.png" alt-text="Profilkonfigurationen for tilføjelsesprogrammet Rapportmeddelelse" lightbox="../../media/microsoft-365-admin-center-profile-info.png":::

5. Pop **op-vinduet Installér ny app** åbnes. Konfigurer følgende indstillinger. Klik på **Næste** for at gå til næste side for at fuldføre konfigurationen. 

   - **Tilføj brugere**: Vælg en af følgende værdier:
     - **Bare mig**
     - **Hele organisationen**
     - **Specifikke brugere/grupper**

   - **Installation**:
     - **Acceptér anmodninger om tilladelser**: Læs apptilladelserne og -egenskaberne omhyggeligt, før du går til næste side.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="../../media/microsoft-365-admin-center-deploy-new-app.png" alt-text="Siden Acceptér anmodninger om tilladelser" lightbox="../../media/microsoft-365-admin-center-deploy-new-app.png":::

     - **Afslut installationen**: Gennemse og afslut installationen af tilføjelsesprogrammet. 
     - **Installationen er fuldført**: Vælg **Udført** for at fuldføre konfigurationen. 

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="../../media/microsoft-365-admin-center-deployment-complete.png" alt-text="Meddelelsesmeddelelsen om installationen blev fuldført" lightbox="../../media/microsoft-365-admin-center-deployment-complete.png":::

## <a name="edit-settings-for-the-report-message-add-in"></a>Rediger indstillinger for tilføjelsesprogrammet Rapportmeddelelse

1. I Microsoft 365 Administration skal du gå til **Indstillinger** \> **integrerede apps** \. Find og vælg derefter **tilføjelsesprogrammet Rapportmeddelelse** .

2. I det pop op-vindue, der vises, skal du vælge **Rediger brugere** for at redigere brugerindstillinger.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-report-message-edit.png" alt-text="Pop op-vinduet Rapportmeddelelse" lightbox="../../media/microsoft-365-admin-center-report-message-edit.png":::

3. Hvis du vil fjerne tilføjelsesprogrammet, skal du vælge **Fjern app** under **Handlinger** i det samme pop op-vindue. 

## <a name="get-the-report-phishing-add-in"></a>Hent tilføjelsesprogrammet Rapport phishing

### <a name="get-the-report-phishing-add-in-for-yourself"></a>Hent tilføjelsesprogrammet Rapport phishing til dig selv

1. Gå til Microsoft AppSource på <https://appsource.microsoft.com/marketplace/apps> , og søg efter tilføjelsesprogrammet Rapport phishing.

2. Klik på **HENT DET NU**.

3. Gennemse vilkårene for anvendelse og politik om beskyttelse af personlige oplysninger i den dialogboks, der vises, og klik derefter på **Fortsæt**.

4. Log på med din arbejds- eller skolekonto (til virksomhedsbrug) eller din Microsoft-konto (til personlig brug).

Når tilføjelsesprogrammet er installeret og aktiveret, får du vist følgende ikoner:

- I Outlook ser ikonet sådan ud:

  ![Ikon for phishing-tilføjelsesprogram til rapporter for Outlook.](../../media/Outlook-ReportPhishing.png)

- I Outlook på internettet ser ikonet sådan ud:

    > [!div class="mx-imgBorder"]
    > ![Outlook på internettet ikon for rapport phishing-tilføjelsesprogram.](../../media/OWA-ReportPhishing.png)

### <a name="get-the-report-phishing-add-in-for-your-organization"></a>Hent tilføjelsesprogrammet Rapport phishing for din organisation

> [!NOTE]
> Det kan tage op til 12 timer, før tilføjelsesprogrammet vises i din organisation.

1. I [Microsoft 365 Administration](https://admin.microsoft.com/AdminPortal/Home?#/homepage) skal du gå til **Indstillinger** \> **integrerede apps**. Klik på **Hent apps**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-integrated-apps.png" alt-text="De Microsoft 365 Administration integrerede apps" lightbox="../../media/microsoft-365-admin-center-integrated-apps.png":::

2. På den **Microsoft 365 Apps** side, der vises, skal du klikke i feltet **Søg**, angive **Rapport phishing** og **derefter klikke på** ![søgeikonet Søg.](../../media/search-icon.png) Find og vælg **Rapport phishing** på listen over resultater. 
 
3. Siden med oplysninger om appen åbnes. Vælg **Hent det nu**.

4. Udfyld de grundlæggende profiloplysninger, og klik derefter på **Fortsæt**.

5. Pop **op-vinduet Installér ny app** åbnes. Følg de trin, [der er beskrevet ovenfor](enable-the-report-message-add-in.md#get-the-report-message-add-in-for-your-organization) , for at fuldføre konfigurationen. 

## <a name="edit-settings-for-the-report-phishing-add-in"></a>Rediger indstillinger for tilføjelsesprogrammet Rapport phishing

1. I Microsoft 365 Administration skal du gå til **Indstillinger** \> **integrerede apps** \. Find og vælg derefter tilføjelsesprogrammet **Rapport phishing** .

2. I det pop op-vindue, der vises, skal du vælge **Rediger brugere** for at redigere brugerindstillinger.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-report-phishing-edit.png" alt-text="Pop op-vinduet Phishing-rapport" lightbox="../../media/microsoft-365-admin-center-report-phishing-edit.png":::

3. Hvis du vil fjerne tilføjelsesprogrammet, skal du vælge **Fjern app** under **Handlinger** i det samme pop op-vindue. 
