---
title: Trusselsjagt i Threat Explorer efter Microsoft Defender for Office 365
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
description: Brug Trusselsoversigt eller registreringer i realtid på Microsoft 365 Defender portalen til at undersøge og reagere effektivt på trusler.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2c99bc2ce004156320ec8f53f6b956f7989ee056
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648817"
---
# <a name="threat-hunting-in-threat-explorer-for-microsoft-defender-for-office-365"></a>Trusselsjagt i Threat Explorer efter Microsoft Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for:**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I denne artikel:

- [Gennemgang af Threat Explorer](#threat-explorer-walk-through)
- [Undersøgelse af mail](#email-investigation)
- [Afhjælpning via mail](#email-remediation)
- [Forbedringer af trusselsjagtoplevelsen](#improvements-to-threat-hunting-experience)

> [!NOTE]
> Dette er en del af en **serie med tre artikler** om **Threat Explorer (Explorer),** **mailsikkerhed** og **registreringer i realtid** (f.eks. forskelle mellem værktøjerne og de tilladelser, der er nødvendige for at betjene dem). De to andre artikler i denne serie er [Mailsikkerhed med Threat Explorer](email-security-in-microsoft-defender.md) og [Threat Explorer og registreringer i realtid](real-time-detections.md).

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Hvis din organisation har [Microsoft Defender for Office 365](defender-for-office-365.md), og du har [tilladelserne](#required-licenses-and-permissions), kan du bruge **Stifinder**- eller **realtidsregistreringer** til at registrere og afhjælpe trusler.

I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & samarbejde** og derefter vælge **Stifinder**- eller **realtidsregistreringer**. Hvis du vil gå direkte til siden, skal du bruge <https://security.microsoft.com/threatexplorer> eller <https://security.microsoft.com/realtimereports>.

Med disse værktøjer kan du:

- Se malware, der er registreret af Microsoft 365 sikkerhedsfunktioner
- Vis phishing-URL-adresse, og klik på domsdata
- Start en automatisk undersøgelses- og svarproces fra en visning i Stifinder
- Undersøg ondsindet mail m.m.

Du kan få flere oplysninger under [Mailsikkerhed med Threat Explorer](email-security-in-microsoft-defender.md).

Se denne korte video for at få mere at vide om, hvordan du jagter og undersøger mail- og samarbejdsbaserede trusler ved hjælp af Microsoft Defender for Office 365. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyPRU]

## <a name="threat-explorer-walk-through"></a>Gennemgang af Threat Explorer

I Microsoft Defender for Office 365 er der to abonnementsplaner – Plan 1 og Plan 2. Der findes manuelt styrede trusselsjagtværktøjer i begge planer under forskellige navne og med forskellige egenskaber.

Defender for Office 365 Plan 1 bruger *registreringer i realtid*, som er et undersæt af *jagtværktøjet Threat Explorer* (også kaldet *Explorer*) i Plan 2. I denne artikelserie blev de fleste af eksemplerne oprettet ved hjælp af full Threat Explorer. Administratorer bør teste trin i registreringer i realtid for at se, hvor de gælder.

Når du er gået til **Stifinder**, ankommer du som standard til siden **Malware** , men du kan bruge rullelisten **Vis** til at blive fortrolig med dine muligheder. Hvis du jagter Phish eller graver dig ind i en trusselskampagne, skal du vælge disse visninger.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/view-drop-down.png" alt-text="Rullelisten Vis i Threat Explorer" lightbox="../../media/view-drop-down.png":::

Når en person med sikkerhedshandlinger (sek. ops) vælger de data, vedkommende vil se, om omfanget er smal visning som f.eks. **brugerindsendelser** eller en bredere visning, f.eks **. Alle mails**, kan vedkommende bruge knappen **Afsender** til yderligere at filtrere. Husk at vælge Opdater for at fuldføre dine filtreringshandlinger.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/sender-drop-down.png" alt-text="Knappen Afsender i Threat Explorer" lightbox="../../media/sender-drop-down.png":::

Du kan overveje at justere fokus i Stifinder eller registrering i realtid i lag. Den første er **Vis**. Det andet kan opfattes som et *filtreret fokus*. Du kan f.eks. spore de trin, du har udført for at finde en trussel, ved at registrere dine beslutninger som denne: Hvis du vil finde problemet i Stifinder, **har jeg valgt Visningen Malware med et modtagerfilterfokus**. Det gør det nemmere at udføre dine trin igen.

> [!TIP]
> Hvis Sec Ops bruger **mærker** til at markere konti, de betragter som mål med høj værdi, kan de foretage valg som *Phish-visning med fokus på mærker-filter (omfatter et datointerval, hvis det bruges)*. Dette viser dem eventuelle phishingforsøg, der er rettet mod deres brugermål med høj værdi i løbet af et tidsinterval (f.eks. datoer, hvor visse phishing-angreb sker meget for deres branche).

Afgrænsninger kan foretages i datointervaller ved hjælp af kontrolelementerne for datointervaller. Her kan du se Stifinder i **malwarevisning** med fokus på filter for **registreringsteknologi** . Men det er **filterknappen Avanceret** , der gør det muligt for Sec Ops-teams at gå i dybden.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/advanced-filter.png" alt-text="Det avancerede filter i Threat Explorer" lightbox="../../media/advanced-filter.png":::

Hvis du klikker på **filteret Avanceret** , vises et panel, der lader Sec Ops-jægere selv oprette forespørgsler, så de selv kan inkludere eller udelade de oplysninger, de har brug for at se. Både diagrammet og tabellen på siden Stifinder afspejler deres resultater.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-chart-table.png" alt-text="Resultaterne fra en forespørgsel" lightbox="../../media/threat-explorer-chart-table.png":::

Brug knappen **Kolonneindstillinger** til at få de mest nyttige oplysninger om tabellen:

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-column-options.png" alt-text="Knappen Kolonneindstillinger fremhævet" lightbox="../../media/threat-explorer-column-options.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/column-options.png" alt-text="De tilgængelige indstillinger i Kolonner" lightbox="../../media/column-options.png":::

I den samme mien skal du sørge for at teste dine visningsindstillinger. Forskellige målgrupper reagerer godt på forskellige præsentationer af de samme data. For nogle seere kan kortet **Email Origins** vise, at en trussel er udbredt eller diskret hurtigere end **visningsindstillingen Kampagne** lige ved siden af den. Se Ops kan gøre brug af disse skærme for bedst at fremhæve, at der er behov for sikkerhed og beskyttelse eller til senere sammenligning for at vise effektiviteten af deres handlinger.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-origin-map.png" alt-text="Kortet Mail oprindelser" lightbox="../../media/threat-explorer-email-origin-map.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-campaign-display.png" alt-text="Visningsindstillingerne for kampagne" lightbox="../../media/threat-explorer-campaign-display.png":::

### <a name="email-investigation"></a>Undersøgelse af mail

Når du ser en mistænkelig mail, skal du klikke på navnet for at udvide pop op-vinduet til højre. Her er banneret, hvor Sec Ops kan se [mailenhedssiden](mdo-email-entity-page.md) , tilgængelig.

Mailenhedssiden samler indhold, der kan findes under **Detaljer**, **Vedhæftede filer**, **Enheder**, men indeholder mere organiserede data. Dette omfatter ting som DMARC resultater, almindelig tekst visning af e-mail header med en kopi mulighed, dom oplysninger om vedhæftede filer, der blev sikkert detoneret, og filer disse detonations droppet (kan omfatte IP-adresser, der blev kontaktet og skærmbilleder af sider eller filer). URL-adresser og deres domme vises også med lignende oplysninger rapporteret.

Når du kommer til denne fase, er mailenhedssiden afgørende for det sidste trin – *afhjælpning*.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-entity-page.png" alt-text="Mailobjektsiden" lightbox="../../media/threat-explorer-email-entity-page.png":::

> [!TIP]
> Hvis du vil vide mere om den omfattende mailenhedsside (se nedenfor under fanen **Analyse** ), herunder resultaterne af deonerede vedhæftede filer, resultaterne for inkluderede URL-adresser og sikker eksempelvisning af mail, skal du klikke [her](mdo-email-entity-page.md).

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-analysis-tab.png" alt-text="Fanen Analyse på mailobjektsiden" lightbox="../../media/threat-explorer-analysis-tab.png":::

### <a name="email-remediation"></a>Afhjælpning via mail

Når en sec Ops-person bestemmer, at en mail er en trussel, er det næste opdagelsestrin i Stifinder eller realtid, der beskæftiger sig med truslen og afhjælper den. Det kan du gøre ved at vende tilbage til Threat Explorer, markere afkrydsningsfeltet for mailen med problemet og bruge knappen **Handlinger** .

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-actions-button.png" alt-text="Knappen Handlinger i Threat Explorer" lightbox="../../media/threat-explorer-email-actions-button.png":::

Her kan analytikeren foretage handlinger som f.eks. at rapportere mailen som spam, phishing eller malware, kontakte modtagere eller yderligere undersøgelser, der kan omfatte udløsning af automatiserede undersøgelses- og svarbøger (eller AIR) (hvis du har Plan 2). Eller mailen kan også rapporteres som ren.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-actions-drop-down.png" alt-text="Rullelisten Handlinger" lightbox="../../media/threat-explorer-email-actions-drop-down.png":::

## <a name="improvements-to-threat-hunting-experience"></a>Forbedringer af trusselsjagtoplevelsen

### <a name="alert-id"></a>Besked-id

Når du navigerer fra en besked til Threat Explorer, filtreres **visningen** efter **besked-id**. Dette gælder også i realtidsregistrering. Meddelelser, der er relevante for den specifikke besked, og en samlet mail (antal) vises. Du kan se, om en meddelelse var en del af en besked, samt navigere fra den pågældende meddelelse til den relaterede besked.

Til sidst inkluderes besked-id'et i URL-adressen, f.eks.: `https://https://security.microsoft.com/viewalerts`

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-Filter.png" alt-text="Filteret for besked-id" lightbox="../../media/AlertID-Filter.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-DetailsFlyout.png" alt-text="Pop op-vinduet Besked-id i detaljer" lightbox="../../media/AlertID-DetailsFlyout.png":::

### <a name="extending-explorer-and-real-time-detections-data-retention-and-search-limit-for-trial-tenants"></a>Udvidelse af stifinderdataopbevaring og søgegrænse for prøvelejere (og registreringer i realtid)

Som en del af denne ændring vil analytikere kunne søge efter og filtrere maildata på tværs af 30 dage (steget fra syv dage) i Threat Explorer og registreringer i realtid for både Defender for Office P1- og P2-prøveversionslejere. Dette påvirker ikke nogen produktionslejere for både P1- og P2 E5-kunder, hvor standarden for opbevaring allerede er 30 dage.

### <a name="updated-export-limit"></a>Opdateret eksportgrænse

Antallet af mails, der kan eksporteres fra Threat Explorer, er nu 200.000 (var 9990). Det sæt kolonner, der kan eksporteres, er uændret.

### <a name="tags-in-threat-explorer"></a>Tags i Threat Explorer

> [!NOTE]
> Brugertagsfunktionen er tilgængelig som prøveversion og er muligvis ikke tilgængelig for alle. Prøveversioner kan også ændres. Du kan få oplysninger om udgivelsesplanen i køreplanen for Microsoft 365.

Brugerkoder identificerer bestemte grupper af brugere i Microsoft Defender for Office 365. Du kan få flere oplysninger om mærker, herunder licenser og konfiguration, under [Brugerkoder](user-tags.md).

I Threat Explorer kan du se oplysninger om brugerkoder i følgende oplevelser.

#### <a name="email-grid-view"></a>Mailgittervisning

Når analytikere kigger på kolonnen **Mærker** i mailgitteret, får de vist alle mærker, der er anvendt på afsender- eller modtagerpostkasser. Som standard vises systemkoder som *prioritetskonti* først.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-grid.png" alt-text="Filtrer mærker i mailgittervisning" lightbox="../../media/tags-grid.png":::

#### <a name="filtering"></a>Filtrering

Mærker kan bruges som filtre. Gå på jagt blandt kun prioritetskonti, eller brug specifikke scenarier med brugertags på denne måde. Du kan også udelade resultater, der har bestemte mærker. Kombiner mærker med andre filtre og datointervaller for at indsnævre undersøgelsesområdet.

[![Filtrer mærker.](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-filter-not.png" alt-text="De mærker, der ikke er filtreret" lightbox="../../media/tags-filter-not.png":::

#### <a name="email-detail-flyout"></a>Pop op-vindue med maildetaljer

Hvis du vil have vist de enkelte mærker for afsender og modtager, skal du vælge en mail for at åbne pop op-vinduet med meddelelsesoplysninger. Under fanen **Oversigt** vises afsender- og modtagerkoderne separat. Oplysningerne om individuelle mærker for afsender og modtager kan eksporteres som CSV-data.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-flyout.png" alt-text="Mærkerne Mailoplysninger" lightbox="../../media/tags-flyout.png":::

Oplysninger om mærker vises også i pop op-vinduet med URL-klik. Hvis du vil se den, skal du gå til Visningen Phish eller Alle mails > **URL-adresser** eller fanen **KLIK PÅ URL-adresser** . Vælg et enkelt pop op-vindue til URL-adresser for at få vist yderligere oplysninger om klik for den pågældende URL-adresse, herunder eventuelle mærker, der er knyttet til det pågældende klik.

### <a name="updated-timeline-view"></a>Opdateret tidslinjevisning

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-urls.png" alt-text="URL-mærkerne" lightbox="../../media/tags-urls.png":::
>
Få mere at vide ved at se [denne video](https://www.youtube.com/watch?v=UoVzN0lYbfY&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=4).

## <a name="extended-capabilities"></a>Udvidede funktioner

### <a name="top-targeted-users"></a>Mest målrettede brugere

De mest populære malwarefamilier viser de **mest målrettede brugere** i afsnittet Malware. De mest målrettede brugere udvides også via phish- og alle mailvisninger. Analytikere kan se de øverste fem målrettede brugere sammen med antallet af forsøg for hver bruger i hver visning.

Sikkerhedshandlinger kan eksportere listen over målrettede brugere op til en grænse på 3.000 sammen med antallet af forsøg, der er foretaget, til offlineanalyse for hver mailvisning. Hvis du vælger antallet af forsøg (f.eks. 13 forsøg på billedet nedenfor), åbnes der også en filtreret visning i Threat Explorer, så du kan se flere oplysninger på tværs af mails og trusler for den pågældende bruger.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Top_Targeted_Users.png" alt-text="De brugere, der var mest målrettet" lightbox="../../media/Top_Targeted_Users.png":::

### <a name="exchange-transport-rules"></a>Exchange transportregler

Sikkerhedsteamet kan se alle de Exchange transportregler (eller regler for mailflow), der er anvendt på en meddelelse, i gittervisningen Mail. Vælg **Kolonneindstillinger** i gitteret, og **tilføj derefter Exchange Transportregel** fra kolonneindstillingerne. Indstillingen Exchange transportregler er også synlig i pop op-vinduet **Detaljer** i mailen.

Der vises navne og GUID'er for de transportregler, der er anvendt på meddelelsen. Analytikere kan søge efter meddelelser ved hjælp af navnet på transportreglen. Dette er en CONTAINS-søgning, hvilket betyder, at du også kan foretage delvise søgninger.

> [!IMPORTANT]
> Exchange søgning efter transportregel og tilgængelighed af navn afhænger af den specifikke rolle, der er tildelt dig. Du skal have en af følgende roller eller tilladelser for at få vist transportregelnavne og -søgning. Men selv uden rollerne eller tilladelserne nedenfor kan en analytiker få vist transportregelmærkaten og GUID-oplysningerne i Mailoplysninger. Andre oplevelser med postvisning i mailgitre, pop op-vinduet Mail, Filtre og Eksport påvirkes ikke.
>
> - kun Exchange Online – forebyggelse af datatab: Alle
> - kun Exchange Online – O365SupportViewConfig: Alle
> - Microsoft Azure Active Directory eller Exchange Online – Sikkerheds Administration: Alle
> - Azure Active Directory eller Exchange Online – Sikkerhedslæser: Alle
> - kun Exchange Online – transportregler: alle
> - kun Exchange Online – View-Only konfiguration: Alle
>
> I mailgitteret, pop op-vinduet Detaljer og Eksporteret CSV præsenteres ETR'er med et navn/GUID som vist nedenfor.
>
> > [!div class="mx-imgBorder"]
> > :::image type="content" source="../../media/ETR_Details.png" alt-text="Reglerne for Exchange transport" lightbox="../../media/ETR_Details.png":::

### <a name="inbound-connectors"></a>Indgående forbindelser

Forbindelser er en samling instruktioner, der tilpasser, hvordan dine mailflows til og fra din Microsoft 365 eller Office 365 organisation. De giver dig mulighed for at anvende eventuelle sikkerhedsbegrænsninger eller kontrolelementer. I Threat Explorer kan du få vist de connectors, der er relateret til en mail, og søge efter mails ved hjælp af connectornavne.

Søgningen efter connectors er en CONTAINS-forespørgsel, hvilket betyder, at delvise nøgleordssøgninger kan fungere:

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Connector_Details.png" alt-text="Oplysninger om connectoren" lightbox="../../media/Connector_Details.png":::

## <a name="required-licenses-and-permissions"></a>Påkrævede licenser og tilladelser

Du skal have [Microsoft Defender for Office 365](defender-for-office-365.md) for at bruge Stifinder- eller realtidsregistreringer.

- Explorer er inkluderet i Defender for Office 365 Plan 2.
- Rapporten med registreringer i realtid er inkluderet i Defender for Office 365 Plan 1.
- Planlæg at tildele licenser til alle brugere, der skal beskyttes af Defender for Office 365. Explorer- og realtidsregistreringer viser registreringsdata for brugere med licens.

Hvis du vil have vist og bruge Stifinder- eller realtidsregistreringer, skal du have følgende tilladelser:

- På Microsoft 365 Defender-portalen:
  - Organisationsadministration
  - Sikkerhedsadministrator (dette kan tildeles i Azure Active Directory Administration (<https://aad.portal.azure.com>)
  - Sikkerhedslæser
- I Exchange Online:
  - Organisationsadministration
  - View-Only organisationsstyring
  - View-Only modtagere
  - Overholdelsesstyring

Du kan få mere at vide om roller og tilladelser i følgende ressourcer:

- [Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md)
- [Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo)
- [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)

## <a name="more-information"></a>Flere oplysninger

- [Find og undersøg ondsindet mail, der blev leveret](investigate-malicious-email-that-was-delivered.md)
- [Vis skadelige filer, der er registreret i SharePoint Online, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [Få et overblik over visningerne i Threat Explorer (og registreringer i realtid)](threat-explorer-views.md)
- [Statusrapport om trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report)
- [Automatiseret undersøgelse og svar i Microsoft Threat Protection](automated-investigation-response-office.md)
- [Undersøg mails med mailenhedssiden](mdo-email-entity-page.md)
