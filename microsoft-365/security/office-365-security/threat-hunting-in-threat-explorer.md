---
title: Trusselssøgning i Threat Explorer for Microsoft Defender for Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/05/2021
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Brug registreringer af Threat Explorer eller realtid i Microsoft 365 Defender-portalen til at undersøge og reagere effektivt på trusler.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: de9121320e339ecff2b665737a6b4ccebe5e0fd0
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63593872"
---
# <a name="threat-hunting-in-threat-explorer-for-microsoft-defender-for-office-365"></a>Trusselssøgning i Threat Explorer for Microsoft Defender for Office 365

I denne artikel:

- [Gennemgang af Trusselsstifinder](#threat-explorer-walk-through)
- [Undersøgelse af mail](#email-investigation)
- [Afhjælpning af mail](#email-remediation)
- [Forbedringer af trussels-jagtoplevelsen](#improvements-to-threat-hunting-experience)

> [!NOTE]
> Dette er en del af en **3-artikelserie** om **Trusselsstifinder** **(Explorer)****,** mailsikkerhed og Explorer og registreringer i realtid (f.eks. forskelle mellem værktøjerne og de tilladelser, der er nødvendige for at kunne betjene dem). De to andre artikler i denne serie er [Mailsikkerhed med registreringer](email-security-in-microsoft-defender.md) [af Threat Explorer og Threat Explorer og realtid](real-time-detections.md).


**Gælder for**
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Hvis din organisation har [Microsoft Defender Office 365](defender-for-office-365.md), og du har tilladelserne [, kan](#required-licenses-and-permissions) du bruge **Explorer** eller registreringer i realtid til  at registrere og afhjælpe trusler.

I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **& og samarbejde** og derefter vælge **Stifinder****- eller realtidsregistreringer**. For at gå direkte til siden skal du bruge <https://security.microsoft.com/threatexplorer> eller <https://security.microsoft.com/realtimereports>.

Med disse værktøjer kan du:

- Se malware, der registreres Microsoft 365 af sikkerhedsfunktioner
- Få vist phishing-URL-adresse, og klik på vurderingsdata
- Starte en automatisk undersøgelses- og svarproces fra en visning i Stifinder
- Undersøg ondsindede mails og meget mere

Du kan få mere at vide [under Mailsikkerhed med Threat Explorer](email-security-in-microsoft-defender.md).

## <a name="threat-explorer-walk-through"></a>Gennemgang af Trusselsstifinder

I Microsoft Defender til Office 365 er der to abonnementsplaner – Plan 1 og Plan 2. Manuelt drevet Trussels-søgeværktøjer findes i begge planer, under forskellige navne og med forskellige egenskaber.

Defender til Office 365 Plan 1 bruger registreringer i *realtid, som* er et undersæt af *Threat Explorer* (også kaldet *Explorer*) på jagtværktøjet i Plan 2. I denne artikelserie blev de fleste eksempler oprettet ved hjælp af den komplette Threat Explorer. Administratorer bør teste eventuelle trin i registreringer i realtid for at se, hvor de gælder.

Når du går **til Stifinder**, kommer du som standard til siden **Malware**, men brug rullemenuen Visning til  at blive fortrolig med dine muligheder. Hvis du er på jagt efter phish eller graver dig ind i en trusselskampagne, skal du vælge disse visninger.

> [!div class="mx-imgBorder"]
> ![Vis rullemenuen i Threat Explorer.](../../media/view-drop-down.png)

Når en sikkerhedshandlinger (Sec Ops) person vælger de data, de ønsker at se, uanset om omfanget er smal visning som brugerindsendelser **, eller** en bredere visning, ligesom Alle **mails, kan** de bruge knappen **Afsender** til at filtrere yderligere. Husk at vælge Opdater for at fuldføre dine filtreringshandlinger.

> [!div class="mx-imgBorder"]
> ![Knappen Afsender i Threat Explorer.](../../media/sender-drop-down.png)

Du kan overveje at finafgrænse fokus i Stifinder eller registrering i realtid i lag. Den første er **Vis**. Den anden kan tænkes som et *filtreret fokus*. Du kan f.eks. spore de trin, du har taget i forbindelse med at finde en trussel, ved at registrere dine beslutninger således: For at finde problemet i Stifinder valgte jeg **malwarevisningen** med et modtagerfilterfokus. Dette gør det nemmere at bruge dine trin.

> [!TIP]
> Hvis Sec Ops bruger  Mærker til at markere konti, som de anser for at være mål med høj værdi, kan de foretage valg som f.eks. *Phish-visning* med fokus på filteret Mærker (inkluder et datointerval, hvis det bruges). Dette viser dem eventuelle phishingforsøg rettet mod deres høje brugermål inden for et tidsinterval (f.eks. datoer, hvor visse phishing-angreb sker meget for deres branche).

Forbedringer kan foretages på datointervaller ved hjælp af kontrolelementerne for datoområde. Her kan du se Stifinder i **malwarevisning** med fokus **på filteret Registreringsteknologi** . Men det er knappen **Avanceret filter** , der giver Sec Ops-teams mulighed for at grave dybt.

> [!div class="mx-imgBorder"]
> ![Avanceret filter i Threat Explorer.](../../media/advanced-filter.png)

Når du klikker på **Avanceret filter** , vises et panel, som gør det muligt for Sec Ops selv at opbygge forespørgsler, så de kan medtage eller udelade de oplysninger, de skal se. Både diagrammet og tabellen på Stifinder-siden afspejler deres resultater.

> [!div class="mx-imgBorder"]
> ![Resultater fra en forespørgsel.](../../media/threat-explorer-chart-table.png)

Brug knappen **Kolonneindstillinger** for at få den type oplysninger i tabellen, der ville være mest nyttige:

> [!div class="mx-imgBorder"]
> ![Knappen Indstillinger for kolonne fremhævet.](../../media/threat-explorer-column-options.png)

> [!div class="mx-imgBorder"]
> ![Tilgængelige indstillinger i Kolonner.](../../media/column-options.png)

I samme mien skal du sørge for at teste visningsindstillingerne. Forskellige målgrupper reagerer godt på forskellige præsentationer af de samme data. For nogle brugere kan kortet **Mailoprindelse** vise, at en trussel er udbredt eller hurtigere diskret end indstillingen Kampagnevisning lige ved siden af. Sec Ops kan bruge disse skærme til bedst at fremhæve behovet for sikkerhed og beskyttelse eller til senere sammenligning for at demonstrere effektiviteten af deres handlinger.

> [!div class="mx-imgBorder"]
> ![Kort over Mail Origins.](../../media/threat-explorer-email-origin-map.png)

> [!div class="mx-imgBorder"]
> ![Indstillinger for kampagnevisning.](../../media/threat-explorer-campaign-display.png)

### <a name="email-investigation"></a>Undersøgelse af mail

Når du ser en mistænkelig mail, skal du klikke på navnet for at udvide pop op-mailen i højre side. Her er det banner, der giver Sec Ops adgang til siden [med mailenhed](mdo-email-entity-page.md) .

Siden mailenhed trækker indhold sammen, der kan findes under **Detaljer**, **Vedhæftede filer**, **Enheder**, men indeholder mere organiserede data. Dette omfatter ting som DMARC-resultater, visning af almindelig tekst i mailoverskriften med en kopiindstilling, vurderingsoplysninger om vedhæftede filer, der er blevet detoneret sikkert, og filer, som disse detonationer er blevet afbrudt (kan omfatte IP-adresser, der blev kontaktet, samt skærmbilleder af sider eller filer). URL-adresser og deres konklusion vises også med lignende oplysninger, der er rapporteret.

Når du når til denne fase, er siden for mailenhed afgørende for det sidste trin – *afhjælpning*.

> [!div class="mx-imgBorder"]
> ![Siden for mailenhed.](../../media/threat-explorer-email-entity-page.png)

> [!TIP]
> Du kan få mere at vide om siden med omfattende mailenhed (se  nedenfor på fanen Analyse), herunder resultaterne af detonerede vedhæftede filer, resultater for inkluderede URL-adresser og sikker forhåndsvisning af mail ved at klikke [her](mdo-email-entity-page.md).

> [!div class="mx-imgBorder"]
> ![Fanen Analyse på siden mailenhed.](../../media/threat-explorer-analysis-tab.png)

### <a name="email-remediation"></a>Afhjælpning af mail

Når en Sec Ops-person finder ud af, at en mail er en trussel, er det næste trin til registrering i Explorer eller i realtid vedrørende truslerne og afhjælpning af den. Dette kan gøres ved at gå tilbage til Threat Explorer, markere afkrydsningsfeltet for problemmailen og bruge **knappen** Handlinger.

> [!div class="mx-imgBorder"]
> ![Knappen Handlinger i Trusselsoversigt.](../../media/threat-explorer-email-actions-button.png)

Her kan analytikeren udføre handlinger som rapportering af mail som spam, phishing eller malware, kontakter modtagere eller yderligere undersøgelser, der kan udløse automatiseret undersøgelse og svar (eller AIR) playbooks (hvis du har Plan 2). Eller mailen kan også rapporteres som ren.

> [!div class="mx-imgBorder"]
> ![Rullemenuen Handlinger.](../../media/threat-explorer-email-actions-drop-down.png)

## <a name="improvements-to-threat-hunting-experience"></a>Forbedringer af trussels-jagtoplevelsen

### <a name="alert-id"></a>Besked-id

Når du navigerer fra en besked til Threat Explorer, **filtreres** visningen efter **besked-id**. Dette gælder også ved registrering i realtid. Meddelelser, der er relevante for den specifikke besked, og en mailtotal (et antal) vises. Du kan se, om en meddelelse var en del af en besked, samt navigere fra den pågældende meddelelse til den relaterede besked.

Endelig er påmindelses-id inkluderet i URL-adressen, f.eks.: `https://https://security.microsoft.com/viewalerts`

> [!div class="mx-imgBorder"]
> ![Filtrering af besked-id.](../../media/AlertID-Filter.png)

> [!div class="mx-imgBorder"]
> ![Besked-id i pop op-pop-op-meddelelse.](../../media/AlertID-DetailsFlyout.png)

### <a name="extending-explorer-and-real-time-detections-data-retention-and-search-limit-for-trial-tenants"></a>Forlængelse af Stifinder-registreringer (og registreringer i realtid) af dataopbevaring og søgegrænse for prøveversionslejere

Som en del af denne ændring vil analytikere kunne søge efter og filtrere maildata på tværs af 30 dage (øget fra syv dage) i Threat Explorer og registreringer i realtid for både Defender for Office P1- og P2-prøvelejere. Dette påvirker ikke produktionslejere for både P1- og P2 E5-kunder, hvor opbevaringsstandarden allerede er 30 dage.

### <a name="updated-export-limit"></a>Opdateret eksportgrænse

Antallet af mails, der kan eksporteres fra Threat Explorer, er nu 200.000 (var 9990). Det sæt kolonner, der kan eksporteres, er uændret.

### <a name="tags-in-threat-explorer"></a>Mærker i Threat Explorer

> [!NOTE]
> Funktionen brugermærker er i forhåndsvisning og er muligvis ikke tilgængelig for alle. Desuden kan prøveversioner ændres uden ændringer. Du kan finde oplysninger om udgivelsesplanen i oversigten Microsoft 365 udgivelse.

Brugermærker identificerer bestemte grupper af brugere i Microsoft Defender til Office 365. Du kan finde flere oplysninger om mærker, herunder licenser og konfiguration, under [Brugermærker](user-tags.md).

I Threat Explorer kan du se oplysninger om brugermærker i følgende oplevelser.

#### <a name="email-grid-view"></a>Gittervisning af mail

Når analytikere ser på **kolonnen Mærker** i mailgitteret, får de vist alle mærker, der er blevet anvendt på afsender- eller modtagerpostkasser. Systemmærker som *prioritetskonti vises som* standard først.

> [!div class="mx-imgBorder"]
> ![Filtrer mærker i mailgittervisning.](../../media/tags-grid.png)

#### <a name="filtering"></a>Filtrering

Mærker kan bruges som filtre. Gå på jagt efter prioritetskonti, eller brug bestemte scenarier med brugermærker på denne måde. Du kan også udelade resultater, der har bestemte mærker. Kombiner mærker med andre filtre og datointervaller for at begrænse omfanget af undersøgelsen.

[![Filtermærker.](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)

> [!div class="mx-imgBorder"]
> ![Ikke filtrere mærker.](../../media/tags-filter-not.png)

#### <a name="email-detail-flyout"></a>Pop op-pop op-pop-op-besked med maildetaljer

Hvis du vil have vist de enkelte mærker for afsender og modtager, skal du vælge en mail for at åbne pop op-meddelelsens detaljer. På fanen **Oversigt** vises afsender- og modtagermærkerne separat. Oplysningerne om individuelle mærker for afsender og modtager kan eksporteres som CSV-data.

> [!div class="mx-imgBorder"]
> ![Mærker for Maildetaljer.](../../media/tags-flyout.png)

Oplysninger om mærker vises også i pop op-pop-op-menuen med URL-klik. Du kan se det ved at gå til phish- eller alle **>-webadresser** **eller fanen URL-klik** . Vælg pop op-menuen med en individuel URL-adresse for at få vist flere oplysninger om klik for den pågældende URL-adresse, herunder eventuelle mærker, der er knyttet til det pågældende klik.

### <a name="updated-timeline-view"></a>Opdateret tidslinjevisning

> [!div class="mx-imgBorder"]
> ![URL-koder.](../../media/tags-urls.png)
>
Få mere at vide ved at [se denne video](https://www.youtube.com/watch?v=UoVzN0lYbfY&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=4).

## <a name="extended-capabilities"></a>Udvidede funktioner

### <a name="top-targeted-users"></a>Mest målrettede brugere

De mest populære **malwarefamilier viser de mest målrettede** brugere i afsnittet Malware. De mest målrettede brugere udvides via Phish- og Alle mailvisninger. Analytikere vil kunne se de fem mest populære brugere sammen med antallet af forsøg for hver bruger i hver visning.

Sikkerhedshandlinger brugerne kan eksportere listen over målrettede brugere, op til en grænse på 3.000, sammen med antallet af forsøg, til offlineanalyse for hver mailvisning. Hvis du vælger antallet af forsøg (f.eks. 13 forsøg på billedet nedenfor), åbnes en filtreret visning i Threat Explorer, så du kan se flere detaljer på tværs af mails og trusler for den pågældende bruger.

> [!div class="mx-imgBorder"]
> ![Mest målrettede brugere.](../../media/Top_Targeted_Users.png)

### <a name="exchange-transport-rules"></a>Exchange transportregler

Sikkerhedsteamet vil kunne se alle de Exchange transportregler (eller regler for mailflow) anvendt på en meddelelse i visningen Mailgitter. Vælg **Kolonneindstillinger** i gitteret og derefter **Tilføj Exchange transportregel fra** kolonneindstillingerne. Indstillingen Exchange transportregler kan også ses i pop op-pop-op-mailen Detaljer.

Navne og GUID'er for de transportregler, der anvendes på meddelelsen, vises. Analytikere vil kunne søge efter meddelelser ved hjælp af navnet på transportreglen. Dette er en CONTAINS-søgning, hvilket betyder, at du også kan udføre delvise søgninger.

> [!IMPORTANT]
> Exchange transportregelsøgning og navnetilgængelighed afhænger af den specifikke rolle, der er tildelt dig. Du skal have en af følgende roller eller tilladelser for at få vist transportregelnavnene og søge. Men selv uden rollerne eller tilladelserne nedenfor kan en analytiker se transportregelnavnet og GUID-oplysningerne i Maildetaljerne. Andre oplevelser med visning af poster i Mailgitter, Pop op-pop-op-filer, Filtre og Eksporter påvirkes ikke.
>
> - Exchange Online - Forebyggelse af datatab: Alle
> - Exchange Online kun – O365SupportViewConfig: Alle
> - Microsoft Azure Active Directory eller Exchange Online – Sikkerhedsadministrator: Alle
> - Azure Active Directory eller Exchange Online – Sikkerhedslæser: Alle
> - Exchange Online – Transportregler: Alle
> - Exchange Online – View-Only konfiguration: Alle
>
> I mailgitteret, pop op-billedet Detaljer og Eksporteret CSV får et Navn/GUID som vist nedenfor.
>
> > [!div class="mx-imgBorder"]
> > ![Exchange transportregler.](../../media/ETR_Details.png)

### <a name="inbound-connectors"></a>Indgående forbindelser

Forbindelser er en samling af instruktioner, der tilpasser, hvordan dine mails flyder til og fra din Microsoft 365 eller Office 365 organisation. De gør det muligt for dig at anvende eventuelle sikkerhedsbegrænsninger eller kontrolelementer. I Threat Explorer kan du få vist de forbindelser, der er relateret til en mail, og søge efter mails ved hjælp af forbindelsesnavne.

Søgningen efter forbindelser er en CONTAINS-forespørgsel, hvilket betyder, at delvise nøgleordssøgninger kan fungere:

> [!div class="mx-imgBorder"]
> ![Forbindelsesoplysninger.](../../media/Connector_Details.png)

## <a name="required-licenses-and-permissions"></a>Påkrævede licenser og tilladelser

Du skal have [Microsoft Defender for Office 365](defender-for-office-365.md) at bruge Explorer- eller realtidsregistreringer.

- Explorer er inkluderet i Defender Office 365 Plan 2.
- Registreringer af realtid er inkluderet i Defender for Office 365 Plan 1.
- Planlæg at tildele licenser til alle brugere, der skal være beskyttet af Defender Office 365. Explorer- og realtidsregistreringer viser registreringsdata for licenserede brugere.

Hvis du vil have vist og bruge Registreringer i Stifinder eller i realtid, skal du have følgende tilladelser:

- Gør følgende i Microsoft 365 Defender portalen:
  - Organisationsadministration
  - Sikkerhedsadministrator (kan tildeles i Azure Active Directory Administration (<https://aad.portal.azure.com>)
  - Sikkerhedslæser
- I Exchange Online:
  - Organisationsadministration
  - View-Only organisationsadministration
  - View-Only modtagere
  - Styring af overholdelse

Hvis du vil have mere at vide om roller og tilladelser, skal du se følgende ressourcer:

- [Tilladelser i Microsoft 365 Defender portalen](permissions-microsoft-365-security-center.md)
- [Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo)
- [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)

## <a name="more-information"></a>Flere oplysninger

- [Find og undersøg skadelige mails, der blev leveret](investigate-malicious-email-that-was-delivered.md)
- [Få vist skadelige filer, der er registreret SharePoint Online, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [Få et overblik over visningerne i Threat Explorer (og registreringer i realtid)](threat-explorer-views.md)
- [Statusrapport over trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report)
- [Automatiseret undersøgelse og svar i Microsoft Threat Protection](automated-investigation-response-office.md)
- [Undersøg mails med siden Mailenhed](mdo-email-entity-page.md)
