---
title: Administrer indsendelser
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: seo-marvel-apr2020
description: Administratorer kan lære, hvordan de bruger portalen til indsendelser i Microsoft 365 Defender-portalen til at sende mistænkelige mails, mistænkelige phishingmails, spam og andre potentielt skadelige meddelelser, URL-adresser og vedhæftede filer til Microsoft til genscanning.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6a897ba6973dfba86e3d0628088bad419c61c04c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589570"
---
# <a name="use-the-submissions-portal-to-submit-suspected-spam-phish-urls-and-files-to-microsoft"></a>Brug portalen til indsendelser til at sende mistænkeligt spam, phish, URL-adresser og filer til Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)


I Microsoft 365 med Exchange Online-postkasser kan administratorer bruge portalen Indsendelser på Microsoft 365 Defender-portalen til at sende mails, URL-adresser og vedhæftede filer til Microsoft til scanning.

Når du sender en mail til analyse, får du:

- **Kontrol af mailgodkendelse**: Oplysninger om, hvorvidt mailgodkendelsen blev videregivet eller mislykkedes, da den blev leveret.
- **Politikhit**: Oplysninger om eventuelle politikker, der kan have tilladt eller blokeret indgående mail til din lejer, tilsidesætter vores tjenestefilters konklusion.
- **Nyttedata ry/detonation**: Opdateret undersøgelse af eventuelle URL-adresser og vedhæftede filer i meddelelsen.
- **Grader-analyse**: Gennemsyn udført af hr.-grader for at bekræfte, om meddelelser er skadelige eller ej.

> [!IMPORTANT]
> Payload reputation/detonation and grader analysis are not done in all tenants. Oplysninger er blokeret fra at gå uden for organisationen, når data ikke skal forlade lejerrammen af hensyn til overholdelse af regler og standarder.

Du kan finde andre måder at sende mails, URL-adresser og vedhæftede filer til Microsoft på [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com/>. For at gå direkte til siden **Indsendelser** skal du bruge <https://security.microsoft.com/reportsubmission>.

- Hvis du vil sende meddelelser og filer til Microsoft, skal du være medlem af en af følgende rollegrupper:
  - **Sikkerhedsadministrator** **eller Sikkerhedslæser** [i Microsoft 365 Defender portalen](permissions-microsoft-365-security-center.md).
  
    Bemærk, at medlemskab af denne rollegruppe er påkrævet for [at Få vist brugerindsendelser til den brugerdefinerede postkasse](#view-user-submissions-to-microsoft) som beskrevet senere i denne artikel.

- Administratorer kan sende meddelelser som gamle som 30 dage, hvis den stadig er tilgængelig i postkassen og ikke bliver fjernet af brugeren eller en anden administrator.

- Administratorindsendelser bliver begrænser til følgende takster:
  - Maksimalt bidrag inden for en periode på 15 minutter: 150 indsendelser
  - Samme indsendelser i en 24-timers periode: 3 indsendelser
  - Samme indsendelser inden for en periode på 15 minutter: 1 indsendelse
  
- Du kan finde flere oplysninger om, hvordan brugere kan sende meddelelser og filer til Microsoft, [i Rapportere meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="report-suspicious-content-to-microsoft"></a>Rapportér mistænkeligt indhold til Microsoft

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **siden Indsendelser** på Handlinger & **indsendelser** \> **.** For at gå direkte til siden **Indsendelser** skal du bruge <https://security.microsoft.com/reportsubmission>.

2. På siden **Indsendelser** skal du bekræfte, at  fanen Mails  eller vedhæftede filer eller **URL-adresser** er markeret baseret på den type indhold, du vil rapportere, ![og derefter klikke på ikonet Send til Microsoft til analyse.](../../media/m365-cc-sc-create-icon.png) **Send til Microsoft til analyse**.

3. Brug pop **op-knappen Send til Microsoft** til analyse, der ser ud til at indsende den respektive type indhold (mail, URL-adresse eller vedhæftet fil i mail) som beskrevet i de følgende afsnit.

   > [!NOTE]
   > Fil- og URL-indsendelser er ikke tilgængelige i skyerne, der ikke tillader, at data forlader miljøet. Muligheden for at vælge Fil eller URL-adresse er nedtonet.

### <a name="notify-users-from-within-the-portal"></a>Giv besked til brugere inde fra portalen

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **siden Indsendelser på &** **indsendelser af** \> **samarbejde**. For at gå direkte til siden **Indsendelser** skal du bruge <https://security.microsoft.com/reportsubmission>.

2. På siden **Indsendelser** skal du vælge **fanen Bruger rapporteret meddelelser** og derefter vælge den meddelelse, du vil markere og underrette.

3. Vælg **rullelisten Markér som og giv** besked, og vælg derefter Ingen trusler **fundet Phishing** \> eller **Uønsket**.

   :::image type="content" alt-text="Send meddelelser fra portal." source="../../media/unified-submission-user-reported-message.png" lightbox="../../media/unified-submission-user-reported-message.png":::

Den rapporterede meddelelse markeres som en falsk positiv eller falsk negativ. Der sendes automatisk en mail fra portalen til den bruger, der har rapporteret meddelelsen.

### <a name="submit-a-questionable-email-to-microsoft"></a>Send en tvivlbar mail til Microsoft

1. I feltet **Vælg indsendelsestype skal** du bekræfte, **at** Mail er markeret på rullelisten.

2. I sektionen **Tilføj netværksmeddelelses-id'et eller upload mailfilen** skal du bruge en af følgende indstillinger:
   - Tilføj mailnetværksmeddelelses-id'et **: Dette** er en GUID-værdi, der er tilgængelig i overskriften **X-MS-Exchange-Organization-Network-Message-Id** i meddelelsen eller i **X-MS-Office365-Filtering-Correlation-Id-overskriften** i meddelelser, der er sat i karantæne.
   - **Upload mailfilen (.msg eller .eml): Klik** **på Gennemse filer**. I dialogboksen, der åbnes, skal du finde og vælge .eml- eller .msg-filen og derefter klikke på **Åbn**.

3. I feltet **Vælg en modtager, der har et problem** skal du angive modtageren, som du vil køre en politikkontrol mod. Politikkontrollen afgør, om mailen er blevet ignoreret på grund af bruger- eller organisationspolitikker.

4. Vælg **en af følgende muligheder i sektionen** Vælg en årsag til at sende til Microsoft:
   - **Blev ikke blokeret (falsk positiv)**
   - **Skulle være blevet blokeret (Falsk negativ)**: I Mailen burde **være** blevet kategoriseret som en sektion, der vises, skal du vælge en af følgende værdier (hvis du ikke er sikker, skal du bruge din bedste vurdering):
     - **Phish**
     - **Malware**
     - **Spam**

5. Klik på Send, når du er **færdig**.

    > [!div class="mx-imgBorder"]
    > ![Eksempel på indsendelse af ny URL-adresse.](../../media/submission-flyout-email.png)

### <a name="send-a-suspect-url-to-microsoft"></a>Send en mistænkelig URL-adresse til Microsoft

1. I feltet **Vælg indsendelsestype** skal du **vælge URL** på rullelisten.

2. I feltet **URL-adresse** , der vises, skal du angive den fulde URL-adresse (f.eks. `https://www.fabrikam.com/marketing.html`).

3. Vælg **en af følgende muligheder i sektionen** Vælg en årsag til at sende til Microsoft:
   - **Blev ikke blokeret (falsk positiv)**
   - Skulle **være blevet blokeret (Falsk negativ)**: I Denne **URL-adresse bør være** kategoriseret som en sektion, der vises, skal du vælge en af følgende værdier (hvis du ikke er sikker, skal du bruge din bedste vurdering):
     - **Phish**
     - **Malware**

4. Klik på Send, når du er **færdig**.

    > [!div class="mx-imgBorder"]
    > ![Eksempel på indsendelse af ny mail.](../../media/submission-url-flyout.png)

### <a name="submit-a-suspected-email-attachment-to-microsoft"></a>Send en mistænkelig vedhæftet fil i en mail til Microsoft

1. I feltet **Vælg indsendelsestype skal** du vælge **Vedhæftet fil** i mail på rullelisten.

2. I sektionen **Filer,** der vises, skal du klikke **på Gennemse filer**. I dialogboksen, der åbnes, skal du finde og markere filen og derefter klikke på **Åbn**.

3. Vælg **en af følgende muligheder i sektionen** Vælg en årsag til at sende til Microsoft:
   - **Blev ikke blokeret (falsk positiv)**
   - **Skulle være blevet blokeret (Falsk negativ)**: I denne fil burde **være** blevet kategoriseret som en sektion, der vises, skal du vælge en af følgende værdier (hvis du ikke er sikker, skal du bruge din bedste vurdering):
     - **Phish**
     - **Malware**

4. Klik på Send, når du er **færdig**.

    > [!div class="mx-imgBorder"]
    > ![Eksempel på indsendelse af ny vedhæftet fil.](../../media/submit-email-attachment-for-analysis.png)

> [!NOTE]
> Hvis filtrering af malware har erstattet de vedhæftede filer med filen malware Alert Text.txt, skal du sende den oprindelige meddelelse fra karantæne, der indeholder de oprindelige vedhæftede filer. Du kan finde flere oplysninger om karantæne, og hvordan du frigiver meddelelser med falske malware positive, under Administrer meddelelser og filer, der er sat [i karantæne, som administrator](manage-quarantined-messages-and-files.md).

## <a name="view-admin-submissions-to-microsoft"></a>Få vist administratorindsendelser til Microsoft

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **siden Indsendelser** på Handlinger & **indsendelser** \> **.** For at gå direkte til siden **Indsendelser** skal du bruge <https://security.microsoft.com/reportsubmission>.

2. På siden **Indsendelser skal** du bekræfte, at **fanen Mails**, **URL-adresse** eller **vedhæftede filer** i mails er markeret.

   - Du kan sortere posterne ved at klikke på en tilgængelig kolonneoverskrift. Klik **på Tilpas** kolonner for at få vist maksimalt syv kolonner. Standardværdierne er markeret med en stjerne (<sup>\*</sup>):
     - **Indsendelsesnavn**<sup>\*</sup>
     - **Afsender**<sup>\*</sup>
     - **Modtager**
     - **Indsendt dato**<sup>\*</sup>
     - **Årsag til indsendelse**<sup>\*</sup>
     - **Status**<sup>\*</sup>
     - **Resultat**<sup>\*</sup>
     - **Filterkriterie**
     - **Årsagen til levering/bloker**
     - **Indsendelses-id**
     - **Netværksmeddelelses-id/objekt-id**
     - **Retning**
     - **Afsender-IP**
     - **Samlet kompatibelt niveau (BCL)**
     - **Destination**
     - **Politikhandling**
     - **Indsendt af**
     - **Phish-simulering**
     - **Mærker**<sup>\*</sup>
     - **Tillad**

     Klik på Anvend, når du er **færdig**.

     > [!div class="mx-imgBorder"]
     > ![Ny Tilpas kolonneindstillinger for administratorindsendelser.](../../media/submit-admin-submissios-customize-columns.png)

   - Hvis du vil filtrere posterne, skal du klikke på **Filtrer**. De tilgængelige filtre er:
     - **Indsendt dato**: **Startdato** **og slutdato**.
     - **Indsendelses-id**: En GUID-værdi, der er tildelt til hver indsendelse.
     - **Netværksmeddelelses-id**
     - **Afsender**
     - **Modtager**
     - **Navn**
     - **Indsendt af**
     - **Årsag til indsendelse**
     - **Status**
     - **Mærker**

     Klik på Anvend, når du er **færdig**.

     > [!div class="mx-imgBorder"]
     > ![Nye filterindstillinger for administratorindsendelser.](../../media/submit-admin-submissions-view-filters.png)

   - Hvis du vil gruppere posterne, **skal du** klikke på Grupper og vælge en af følgende værdier på rullelisten:
     - **Ingen**
     - **Type**
     - **Årsag**
     - **Status**
     - **Resultat**
     - **Mærker**

   - Hvis du vil eksportere posterne, skal du klikke på **Eksportér**. I dialogboksen, der vises, skal du gemme .csv fil.

### <a name="admin-submission-result-details"></a>Oplysninger om administratorindsendelsesresultat

Meddelelser, der sendes i administratorindsendelser, gennemses, og resultaterne vises i pop op-pop op-pop-op'en med indsendelsesdetaljerne:

- Hvis der opstod en fejl i afsenderens mailgodkendelse på leveringstidspunktet.
- Oplysninger om eventuelle politikhits, der kan have påvirket eller tilsidesat konklusionen af en meddelelse.
- Aktuelle detonationsresultater for at se, om URL-adresserne eller filerne i meddelelsen var skadelige eller ej.
- Feedback fra gradere.

Hvis der findes en tilsidesættelse, bør resultatet være tilgængeligt på flere minutter. Hvis der ikke var et problem med mailgodkendelse eller levering ikke blev påvirket af en tilsidesættelse, så kan det tage op til en dags feedback fra gradere.

## <a name="view-user-submissions-to-microsoft"></a>Få vist brugerindsendelser til Microsoft

Hvis du har installeret tilføjelsesprogrammet Rapportmeddelelse[, tilføjelsesprogrammet](enable-the-report-message-add-in.md) [Report Phishing](enable-the-report-phish-add-in.md), eller hvis brugerne bruger den [indbyggede](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md) rapportering i Outlook på internettet, kan du se, hvad brugerne rapporterer på fanen Bruger rapporteret meddelelse.

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **siden Indsendelser** på Handlinger & **indsendelser** \> **.** For at gå direkte til siden **Indsendelser** skal du bruge <https://security.microsoft.com/reportsubmission>.

2. På siden **Indsendelser** skal du vælge fanen **Bruger rapporteret** meddelelser.

   - Du kan sortere posterne ved at klikke på en tilgængelig kolonneoverskrift. Klik **på Tilpas kolonner** for at få vist indstillingerne. Standardværdierne er markeret med en stjerne (<sup>\*</sup>):

     - **Mailens emne**<sup>\*</sup>
     - **Rapporteret af**<sup>\*</sup>
     - **Dato rapporteret**<sup>\*</sup>
     - **Afsender**<sup>\*</sup>
     - **Rapporteret årsag**<sup>\*</sup>
     - **Resultat**<sup>\*</sup>
     - **Meddelelse rapporteret id**
     - **Netværksmeddelelses-id**
     - **Afsender-IP**
     - **Rapporteret fra**
     - **Phish-simulering**
     - **Konverteret til administratorindsendelse**
     - **Mærker**<sup>\*</sup>
     - **Markeret som**<sup>\*</sup>
     - **Markeret med**
     - **Dato markeret**

     Klik på Anvend, når du er **færdig**.

   - Hvis du vil filtrere posterne, skal du klikke på **Filtrer**. De tilgængelige filtre er:
     - **Dato rapporteret**: **Startdato** **og slutdato**.
     - **Rapporteret af**
     - **Mailens emne**
     - **Meddelelse rapporteret id**
     - **Netværksmeddelelses-id**
     - **Afsender**
     - **Rapporteret årsag**: **Ikke uønsket**, **phish** eller **spam**
     - **Rapporteret fra**: **Microsoft-tilføjelsesprogrammet** **eller tredjeparts-tilføjelsesprogrammet**
     - **Phish-simulering**: **Ja** eller **Nej**
     - **Konverteret til administratorindsendelse**: **Ja** eller **Nej**
     - **Mærker**

     Klik på Anvend, når du er **færdig**.

     > [!div class="mx-imgBorder"]
     > ![Nye filterindstillinger for brugerindsendelser.](../../media/submit-user-submissions-view-filters.png)

   - Hvis du vil gruppere posterne, **skal du** klikke på Grupper og vælge en af følgende værdier på rullelisten:
     - **Ingen**
     - **Årsag**
     - **Afsender**
     - **Rapporteret af**
     - **Resultat**
     - **Rapporteret fra**
     - **Phish-simulering**
     - **Konverteret til administratorindsendelse**
     - **Mærker**
   
   - Hvis du vil eksportere posterne, skal du klikke på **Eksportér**. I dialogboksen, der vises, skal du gemme .csv fil.

> [!NOTE]
> Hvis organisationer er konfigureret til kun at sende brugerrapporterede meddelelser til den brugerdefinerede postkasse, sendes rapporterede meddelelser ikke til genscanning, og  resultaterne i Brugerrapporterede meddelelser vil altid være tomme.

### <a name="undo-user-submissions"></a>Fortryde brugerindsendelser

Når en bruger sender en mistænkelig mail til den brugerdefinerede postkasse, har brugeren og administratoren ikke mulighed for at fortryde indsendelsen. Hvis brugeren vil gendanne mailen, kan den gendannes i mapperne Slettet post eller Uønsket mail.

### <a name="converting-user-reported-messages-from-the-custom-mailbox-into-an-admin-submission"></a>Konvertere brugerrapporterede meddelelser fra den brugerdefinerede postkasse til en administratorindsendelse 

Hvis du har konfigureret den brugerdefinerede postkasse til at opfange brugerrapporterede meddelelser uden at sende meddelelserne til Microsoft, kan du finde og sende bestemte meddelelser til Microsoft til analyse.

På fanen **Bruger rapporteret** meddelelser skal du vælge en meddelelse på listen, klikke på Send til **Microsoft** til analyse og derefter vælge en af følgende værdier på rullelisten:

- **Rapport rens**
- **Rapportér phishing**
- **Rapportér malware**
- **Rapportér spam**
- **Udløserundersøgelse**

> [!div class="mx-imgBorder"]
> ![Nye indstillinger på knappen Handling.](../../media/admin-submission-main-action-button.png)
