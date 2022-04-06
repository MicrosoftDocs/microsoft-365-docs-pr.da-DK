---
title: Kampagnevisninger i Microsoft Defender for Office 365 plan
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: mcostea
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Få mere at vide om kampagnevisninger Microsoft Defender for Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: eb1e5e6e740accdb9c6102b798df8e60ab47dfff
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467725"
---
# <a name="campaign-views-in-microsoft-defender-for-office-365"></a>Kampagnevisninger i Microsoft Defender for Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Kampagnevisninger er en funktion i Microsoft Defender for Office 365 Plan 2 (f.eks. Microsoft 365 E5 organisationer med Defender for Office 365 plan 2-tilføjelsesprogrammet). Kampagnevisninger i Microsoft 365 Defender identificerer og kategoriserer phishing-angreb i tjenesten. Kampagnevisninger kan hjælpe dig med at:

- Undersøg og res responder effektivt på phishing-angreb.
- Bedre forstå omfanget af angrebene.
- Vis værdi til beslutningstagere.

Med kampagnevisninger kan du få et overblik over et angreb hurtigere og mere komplet end andre mennesker.

## <a name="what-is-a-campaign"></a>Hvad er en kampagne?

En kampagne er et koordineret mailangreb mod en eller mange organisationer. Mailangreb, der stjæler legitimationsoplysninger og virksomhedsdata, er en stor og logiske branche. I tilfælde af at teknologierne øges i et forsøg på at stoppe angreb, ændrer hackere deres metoder i et forsøg på at sikre fortsat succes.

Microsoft udnytter de enorme mængder antiphishing-, antispam- og antimalwaredata på tværs af hele tjenesten for at hjælpe med at identificere kampagner. Vi analyserer og klassificerer angrebsoplysningerne ud fra forskellige faktorer. Eksempel:

- **Angrebskilde**: IP-kildemailadresser og afsendermaildomæner.
- **Meddelelsesegenskaber**: Meddelelsernes indhold, typografi og tone.
- **Meddelelsesmodtagere**: Hvordan modtagerne er relaterede. Modtagerdomæner, modtagerjobfunktioner (administratorer, direktører osv.), virksomhedstyper (store, små, offentlige, private osv.) og brancher.
- **Angrebslast**: Ondsindede links, vedhæftede filer eller andre nyttedata i meddelelserne.

En kampagne kan være kortvarig eller kan strække sig over flere dage, uger eller måneder med aktive og inaktive perioder. En kampagne kan startes mod din specifikke organisation, eller din organisation kan være en del af en større kampagne på tværs af flere virksomheder.

## <a name="campaign-views-in-the-microsoft-365-defender-portal"></a>Kampagnevisninger i Microsoft 365 Defender portalen

Kampagnevisninger er tilgængelig i Microsoft 365 Defender på Mail <https://security.microsoft.com> **og & kampagner** \> **med** samarbejde eller direkte på <https://security.microsoft.com/campaigns>.

:::image type="content" source="../../media/campaigns-overview.png" alt-text="Oversigten Kampagner i Microsoft 365 Defender portal" lightbox="../../media/campaigns-overview.png":::

Du kan også få adgang til kampagnevisninger fra:

- **Mail & samarbejde** \> **Stifinder** \> **Vis** \> **Kampagner**
- **Mail & samarbejde** \> **Stifinder** \> **Vis** \> **Alle mails** \> **Fanen** Kampagne
- **Mail & samarbejde** \> **Stifinder** \> **Vis** \> **Phish** \> **Fanen** Kampagne
- **Mail & samarbejde** \> **Stifinder** \> **Vis** \> **Malware** \> **Fanen** Kampagne

For at få adgang til kampagnevisninger skal du være medlem af rollegrupperne Organisationsadministration **, Sikkerhedsadministrator** eller Sikkerhedslæser i Microsoft 365 Defender portal. Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

## <a name="campaigns-overview"></a>Oversigt over kampagner

Oversigtssiden viser oplysninger om alle kampagner.

På **standardfanen** Kampagne viser **området Kampagnetype** et søjlediagram, der viser antallet af modtagere pr. dag. Grafen viser som standard både **Phish-** og **Malware-data** .

> [!TIP]
> Hvis du ikke kan se nogen kampagnedata, kan du prøve at ændre datointervallet eller [filtrene](#filters-and-settings).

Tabellen under grafen på oversigtssiden viser følgende oplysninger på **fanen** Kampagne:

- **Navn**

- **Eksempel på** emne: Emnelinjen i en af meddelelserne i kampagnen. Bemærk, at alle meddelelser i kampagnen ikke nødvendigvis har det samme emne.

- **Målrettet**: Procentdelen som beregnet af: (antallet af kampagnemodtagere i din organisation) / (det samlede antal modtagere i kampagnen på tværs af alle organisationer i tjenesten). Denne værdi angiver, i hvilken grad kampagnen kun er rettet mod din organisation (en højere værdi) vs. også rettet mod andre organisationer i tjenesten (en lavere værdi).

- **Type**: Denne værdi er enten **Phish** eller **Malware**.

- **Undertype**: Denne værdi indeholder flere oplysninger om kampagnen. Eksempel:
  - **Phish**: Hvor det er tilgængeligt, er det brand, der bliver phishet af denne kampagne. F.eks. `Microsoft`, `Unknown``365`, , `Outlook`eller `DocuSign`.
  - **Malware**: For eksempel, `HTML/PHISH` eller `HTML/<MalwareFamilyName>`.

  Hvor det er tilgængeligt, vil dette brand, der bliver phishet af denne kampagne. Når registrering er drevet af Defender for Office 365, føjes **PRÆfikset ATP-** til undertypeværdien.

- **Modtagere:** Antallet af brugere, der blev målrettet af denne kampagne.

- **Indbakke:** Antallet af brugere, der har modtaget meddelelser fra denne kampagne i deres Indbakke (ikke leveret til mappen Uønsket mail).

- **Klikket**: Antallet af brugere, der klikkede på URL-adressen eller åbnede den vedhæftede fil i phishing-meddelelsen.

- **Klik på rente**: Procentdelen som beregnet med "**Klikket** /  **Iboks**". Denne værdi er et symbol for kampagnens effektivitet. Med andre ord, hvis modtagerne kunne identificere meddelelsen som phishing, og hvis de ikke klikkede på URL'en med nyttedata.

  Bemærk, **at Klikhastighed** ikke bruges i malwarekampagner.

- **Besøgte**: Hvor mange brugere, der rent faktisk kom igennem til webstedet med nyttedata. Hvis der er **klikkede** værdier, men Pengeskab Links blokeret adgang til webstedet, er denne værdi nul.

Fanen **Kampagneindrindelse** viser meddelelseskilder på et kort over verden.

### <a name="filters-and-settings"></a>Filtre og indstillinger

Øverst på siden Kampagne er **der flere** filter- og forespørgselsindstillinger, der kan hjælpe dig med at finde og isolere bestemte kampagner.

:::image type="content" source="../../media/campaign-filters-and-settings.png" alt-text="Kampagnefiltrene" lightbox="../../media/campaign-filters-and-settings.png":::

Den mest grundlæggende filtrering, du kan udføre, er startdato/-klokkeslæt og slutdato/-klokkeslæt.

Hvis du vil filtrere visningen yderligere, kan du udføre enkeltegenskab med filtrering af flere værdier ved at klikke på knappen **Kampagnetype** , foretage dit valg og derefter klikke på **Opdater**.

De filtrerbare kampagneegenskaber, der er tilgængelige **i knappen Kampagnetype** , er beskrevet på følgende liste:

- **Grundlæggende**:
  - **Kampagnetype**: Vælg **Malware** eller **Phish**. Når du fjerner markeringen, får du det samme resultat som at markere begge dele.
  - **Kampagnenavn**
  - **Kampagneundertype**
  - **Afsender**
  - **Modtagere**
  - **Afsenderdomæne**
  - **Emne**
  - **Vedhæftet filnavn**
  - **Malwarefamilie**
  - **Mærker**: Brugere eller grupper, der har fået det angivne brugermærke anvendt (herunder prioritetskonti). Du kan finde flere oplysninger om brugermærker under [Brugermærker](user-tags.md).
  - **Leveringshandling**
  - **Yderligere handling**
  - **Retningalitet**
  - **Registreringsteknologi**
  - **Oprindelig leveringssted**
  - **Seneste leveringssted**
  - **Systemet tilsidesætter**

- **Avanceret**:
  - **Internetmeddelelses-id**: Tilgængeligt **i brevhovedfeltet** meddelelses-id i brevhovedet. En eksempelværdi er `<08f1e0f6806a47b4ac103961109ae6ef@server.domain>` (bemærk vinkelparenteserne).
  - **Netværksmeddelelses-id**: En GUID-værdi, der er tilgængelig i overskriftsfeltet **X-MS-Exchange-Organization-Network-Message-Id** i brevhovedet.
  - **Afsender-IP**
  - **Vedhæftet SHA256**: For at finde SHA256-hash-værdien for en fil i Windows skal du køre følgende kommando i en kommandoprompt: `certutil.exe -hashfile "<Path>\<Filename>" SHA256`.
  - **Klynge-id**
  - **Besked-id**
  - **Id for beskedpolitik**
  - **Kampagne-id**
  - **ZAP URL-signal**

- **URL-adresser**:
  - **URL-domæne**
  - **URL-domæne og sti**
  - **URL-adresse**
  - **URL-sti**
  - **Klik på konklusion**

Hvis du vil have mere avanceret filtrering, herunder filtrering efter flere egenskaber, kan du klikke på **knappen Avanceret filter** for at oprette en forespørgsel. De samme kampagneegenskaber er tilgængelige, men med følgende forbedringer:

- Du kan klikke på **Tilføj en betingelse for** at vælge flere betingelser.
- Du kan vælge **operatoren Og** **eller Eller** mellem betingelser.
- Du kan vælge **elementet Betingelsesgruppe** nederst på listen over betingelser for at danne komplekse sammensatte betingelser.

Når du er færdig, skal du klikke på **knappen** Forespørgsel.

Når du har oprettet et grundlæggende eller avanceret filter, kan du gemme det ved hjælp **af Gem forespørgsel** eller **Gem forespørgsel som**. Senere, når du vender tilbage til siden **Kampagner** , kan du indlæse et gemt filter ved at klikke på **Gemte forespørgselsindstillinger**.

Hvis du vil eksportere grafen eller listen over kampagner, skal du klikke **på Eksportér** og vælge **Eksportér diagramdata** eller **Eksportér kampagneliste**.

Hvis du har et Microsoft Defender for Endpoint abonnement, kan du klikke **på MDE-Indstillinger at** oprette forbindelse til eller afbryde forbindelsen mellem kampagneoplysningerne og Microsoft Defender for Endpoint. Du kan finde flere oplysninger [under Integrer Microsoft Defender for Office 365 med Microsoft Defender for Endpoint](integrate-office-365-ti-with-mde.md).

## <a name="campaign-details"></a>Kampagneoplysninger

Når du klikker på navnet på en kampagne, vises kampagneoplysningerne i en pop op-mail.

### <a name="campaign-information"></a>Kampagneoplysninger

Øverst i visningen kampagnedetaljer er følgende kampagneoplysninger tilgængelige:

- **Kampagne-id**: Det entydige kampagne-id.
- **Aktivitet**: Varigheden og aktiviteten for kampagnen.
- Følgende data for det datointervalfilter, du har valgt (eller som du vælger på tidslinjen):
- **Virkning**
- **Meddelelser**: Det samlede antal modtagere.
- **Indbakke:** Antallet af meddelelser, der blev leveret til indbakken, ikke til mappen Uønsket mail.
- **Klikket på link**: Hvor mange brugere, der har klikket på URL-adressen som nyttedata i phishing-meddelelsen.
- **Besøgt link**: Hvor mange brugere har besøgt URL-adressen.
- **Målrettet(%)**: Procentdelen som beregnet af: (antallet af kampagnemodtagere i din organisation) / (det samlede antal modtagere i kampagnen på tværs af alle organisationer i tjenesten). Bemærk, at denne værdi beregnes i hele kampagnens levetid og ikke ændres baseret på datofiltre.
- Filtre for startdato/-klokkeslæt og slutdata/-klokkeslæt for kampagneflowet som beskrevet i næste afsnit.
- En interaktiv tidslinje for kampagneaktivitet: Tidslinjen viser aktivitet i hele kampagnens levetid. Du kan pege på datapunkterne i grafen for at se antallet af registrerede meddelelser.

:::image type="content" source="../../media/campaign-details-campaign-info.png" alt-text="Kampagneoplysningerne" lightbox="../../media/campaign-details-campaign-info.png":::

### <a name="campaign-flow"></a>Kampagneflow

Midt i visningen Kampagnedetaljer vises vigtige detaljer om kampagnen i et vandret rutediagram (kendt som et _Sankey-diagram_ ). Disse detaljer hjælper dig med at forstå elementerne i kampagnen og den potentielle indvirkning i din organisation.

> [!TIP]
> De oplysninger, der vises i rutediagrammet, styres af datoområdefilteret på tidslinjen som beskrevet i forrige afsnit.

:::image type="content" source="../../media/campaign-details-no-recipient-actions.png" alt-text="De kampagneoplysninger, der ikke indeholder klik med brugerens URL-adresse" lightbox="../../media/campaign-details-no-recipient-actions.png":::

Hvis du peger på et vandret bånd i diagrammet, får du vist antallet af relaterede meddelelser (f.eks. meddelelser fra en bestemt kilde-IP, meddelelser fra kilde-IP'en ved hjælp af det angivne afsenderdomæne osv.).

Diagrammet indeholder følgende oplysninger:

- **Afsender-IP'er**
- **Afsenderdomæner**
- **Filterovergange**: Vurderingsværdier er relateret til de tilgængelige advarsler i forbindelse med phishing og spamfiltrering, som beskrevet i [antispammeddelelsesoverskrifter](anti-spam-message-headers.md). De tilgængelige værdier er beskrevet i følgende tabel:

  |Værdi|Spamfilterets konklusion|Beskrivelse|
  |---|---|---|
  |**Tilladt**|`SFV:SKN` <p> `SFV:SKI`|Meddelelsen blev markeret som ikke spam og/eller sprunget filtrering over, før den blev evalueret af spamfiltrering. Meddelelsen blev f.eks. markeret som ikke spam af en regel for mailflow (også kaldet en transportregel). <p> Meddelelsen ignorerede spamfiltrering af andre årsager. Afsenderen og modtageren ser f.eks. ud til at være i samme organisation.|
  |**Blokeret**|`SFV:SKS`|Meddelelsen blev markeret som spam, før den blev evalueret af spamfiltrering. F.eks. ved en regel for mailflow.|
  |**Registreret**|`SFV:SPM`|Meddelelsen blev markeret som spam af spamfiltrering.|
  |**Det blev ikke fundet**|`SFV:NSPM`|Meddelelsen blev markeret som ikke spam af spamfiltrering.|
  |**Udgivet**|`SFV:SKQ`|Meddelelsen ignorerede spamfiltrering, fordi den blev frigivet fra karantæne.|
  |**Lejers tilladelse**<sup>\*</sup>|`SFV:SKA`|Meddelelsen ignorerede spamfiltrering på grund af indstillingerne i en antispampolitik. Afsenderen var f.eks. på listen over tilladte afsendere eller på listen over tilladte domæner.|
  |**Lejerblok**<sup>\*\*</sup>|`SFV:SKA`|Meddelelsen blev blokeret af spamfiltrering på grund af indstillingerne i en antispampolitik. Afsenderen var f.eks. på listen over tilladte afsendere eller på listen over tilladte domæner.|
  |**Bruger tillade**<sup>\*</sup>|`SFV:SFE`|Meddelelsen ignorerede spamfiltrering, fordi afsenderen var på en brugers liste Pengeskab Afsendere.|
  |**Brugerblok**<sup>\*\*</sup>|`SFV:BLK`|Meddelelsen blev blokeret af spamfiltrering, fordi afsenderen var på en brugers liste over blokerede afsendere.|
  |**ZAP**|i/t|[En nul-timers automatisk tømning (ZAP)](zero-hour-auto-purge.md) flyttede den sendte meddelelse til mappen uønsket mail eller karantæne. Du konfigurerer handlingen i [antispam-politikker](configure-your-spam-filter-policies.md).|

  <sup>\*</sup> Gennemse dine antispampolitikker, da den tilladte meddelelse sandsynligvis er blevet blokeret af tjenesten.

  <sup>\*\*</sup> Gennemse dine antispampolitikker, da disse meddelelser skal være i karantæne og ikke skal leveres.

- **Meddelelsesdestinationer**: Du vil sandsynligvis undersøge meddelelser, der blev leveret til modtagere (enten til indbakken eller mappen Uønsket mail), selvom brugerne ikke klikkede på URL'en for nyttedata i meddelelsen. Du kan også fjerne meddelelser, der er sat i karantæne, fra karantæne. Du kan få mere at vide [under Meddelelser, der er sat i karantæne i EOP](quarantine-email-messages.md).
  - **Slettet mappe**
  - **Ind tabt**
  - **Ekstern**: Modtageren er placeret i din lokale mailorganisation i hybridmiljøer.
  - **Mislykkedes**
  - **Videresendt**
  - **Indbakke**
  - **Mappen Uønsket**
  - **Karantæne**
  - **Unknown**

- **Klik på URL-adressen**: Disse værdier er beskrevet i næste afsnit.

> [!NOTE]
> I alle lag, der indeholder mere end 10 elementer, vises de øverste 10 elementer, mens resten er bundtet sammen i **Andre**.

#### <a name="url-clicks"></a>Klik på URL-adresse

Når en phishingmeddelelse leveres til en modtagers indbakke eller mappen Uønsket mail, er der altid en chance for, at brugeren klikker på URL-adressen til nyttedata. Når du ikke klikker på URL-adressen, er det en lille grad af succes, men du skal finde ud af, hvorfor phishingmeddelelsen endda blev leveret til postkassen.

Hvis en bruger klikkede på WEBADRESSEn til nyttedata i phishing-meddelelsen, vises handlingerne i området til **url-klik** i diagrammet i visningen kampagnedetaljer.

- **Tilladt**
- **Blokeringsside**: Modtageren klikkede på webadressen til nyttedata, men modtagerens adgang til det skadelige websted blev blokeret af en [politik for Pengeskab links](safe-links.md) i organisationen.
- **BlockPageOverride**: Modtageren klikkede på WEBADRESSEn til nyttedata i meddelelsen, og Pengeskab Links forsøgte at stoppe dem, men de fik tilladelse til at tilsidesætte blokeringen. Undersøg [dine Pengeskab Links-politikker](set-up-safe-links-policies.md) for at se, hvorfor brugere har tilladelse til at tilsidesætte Pengeskab Links'ens konklusion og fortsætte med det skadelige websted.
- **PendingDetonationPage**: Pengeskab vedhæftede filer i Microsoft Defender for Office 365 er i gang med at åbne og undersøge WEBADRESSEn til nyttedata i et virtuelt computermiljø.
- **PendingDetonationPageOverride**: Modtageren fik tilladelse til at tilsidesætte processen med aflæsning af nyttedata og åbne URL-adressen uden at vente på resultaterne.

### <a name="tabs"></a>Faner

Fanerne i visningen kampagnedetaljer giver dig mulighed for at undersøge kampagnen yderligere.

> [!TIP]
> De oplysninger, der vises på fanerne, styres af filteret for datointerval på tidslinjen som beskrevet i [afsnittet Kampagneoplysninger](#campaign-information) .

- **Klik på URL-adressen**: Hvis brugerne ikke klikkede på URL-adressen til nyttedata i meddelelsen, er denne sektion tom. Hvis en bruger kunne klikke på URL-adressen, udfyldes følgende værdier:
  - **Bruger**<sup>\*</sup>
  - **URL-adresse**<sup>\*</sup>
  - **Klik på klokkeslæt**
  - **Klik på konklusion**

- **Afsender-IP'er**
  - **Afsender-IP**<sup>\*</sup>
  - **Samlet antal**
  - **Indbakke**
  - **Ikke indbakke**
  - **SPF er blevet** overført: Afsenderen blev godkendt af [SPF (Sender Policy Framework).](how-office-365-uses-spf-to-prevent-spoofing.md) En afsender, der ikke passerer SPF-validering, angiver en ikke-godkendt afsender, eller meddelelsen spoofer en legitim afsender.

- **Afsendere**
  - **Afsender**: Dette er den faktiske afsenderadresse i SMTP-MAIL FRA-kommandoen, som ikke nødvendigvis er Fra:-mailadressen, som brugere ser i deres mailklienter.
  - **Samlet antal**
  - **Indbakke**
  - **Ikke indbakke**
  - **DKIM er blevet** overført: Afsenderen blev godkendt af [Domænenøgler identificeret mail (DKIM)](support-for-validation-of-dkim-signed-messages.md). En afsender, der ikke passerer DKIM-validering, angiver en ikke-godkendt afsender, eller meddelelsen spoofer en legitim afsender.
  - **DMARC er** videregivet: Afsenderen blev godkendt ved hjælp af domænebaseret meddelelsesgodkendelse, -rapportering og - [overholdelse (DMARC)](use-dmarc-to-validate-email.md). En afsender, der ikke passerer DMARC-validering, angiver en ikke-godkendt afsender, eller meddelelsen spoofer en legitim afsender.

- **Vedhæftede filer**
  - **Filnavn**
  - **SHA256**
  - **Malwarefamilie**
  - **Samlet antal**

- **URL-adresse**
  - **URL-adresse**<sup>\*</sup>
  - **Samlet antal**

<sup>\*</sup> Når du klikker på denne værdi, åbnes en pop op-vindue, der indeholder flere oplysninger om det angivne element (bruger, URL-adresse osv.) øverst i visningen kampagnedetaljer. Hvis du vil vende tilbage til visningen kampagnedetaljer, skal du **klikke på** Udført i det nye pop op-billede.

### <a name="buttons"></a>Knapper

Knapperne nederst i visningen kampagnedetaljer giver dig mulighed for at undersøge og registrere oplysninger om kampagnen:

- **Udforsk meddelelser**: Brug styrken i Threat Explorer til yderligere at undersøge kampagnen:
  - **Alle meddelelser**: Åbner en ny trusselsstifinder-søgefane ved hjælp af **værdien Kampagne-id** som søgefilter.
  - **Meddelelser i indbakken**: Åbner en ny trusselsstifinder-søgefane ved hjælp af **Kampagne-id** og **Leveringsplacering:** Indbakke som søgefilter.
  - **Interne meddelelser**: Åbner en ny trusselsstifinders søgefane ved hjælp af **Kampagne-id** og Retning **: Intra-org** som søgefilter.

- **Download trusselsrapport**: Download kampagnedetaljerne til et Word-dokument (som standard kaldet CampaignReport.docx). Bemærk, at overførslen indeholder oplysninger for hele kampagnens levetid (ikke kun de filterdatoer, du har valgt).
