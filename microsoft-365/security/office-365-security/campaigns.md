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
description: Få mere at vide om kampagnevisninger i Microsoft Defender for Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5308770e4ddb72ead5e4d5dac7506c507aa407f6
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739621"
---
# <a name="campaign-views-in-microsoft-defender-for-office-365"></a>Kampagnevisninger i Microsoft Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Kampagnevisninger er en funktion i Microsoft Defender for Office 365 Plan 2 (f.eks. Microsoft 365 E5 eller organisationer med et tilføjelsesprogram til Defender for Office 365 Plan 2). Kampagnevisninger på Microsoft 365 Defender-portalen identificerer og kategoriserer phishingangreb i tjenesten. Kampagnevisninger kan hjælpe dig med at:

- Undersøg og reager effektivt på phishing-angreb.
- Bedre at forstå omfanget af angrebet.
- Vis værdi til beslutningstagere.

Kampagnevisninger giver dig mulighed for at se det store billede af et angreb hurtigere og mere komplet end noget menneske.

Se denne korte video om, hvordan kampagnevisninger i Microsoft Defender for Office 365 hjælper dig med at forstå angrebskampagner, der er målrettet din organisation.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGBL8]

## <a name="what-is-a-campaign"></a>Hvad er en kampagne?

En kampagne er et koordineret mailangreb mod en eller mange organisationer. Mailangreb, der stjæler legitimationsoplysninger og virksomhedsdata, er en stor og indbringende branche. Efterhånden som teknologier øges i et forsøg på at stoppe angreb, ændrer angribere deres metoder i et forsøg på at sikre fortsat succes.

Microsoft udnytter de store mængder data om anti-phishing, anti-spam og antimalware på tværs af hele tjenesten for at hjælpe med at identificere kampagner. Vi analyserer og klassificerer angrebsoplysningerne i henhold til flere faktorer. Eksempel:

- **Angrebskilde**: Kilde-IP-adresserne og afsendermaildomænerne.
- **Meddelelsesegenskaber**: Meddelelsernes indhold, typografi og tone.
- **Meddelelsesmodtagere**: Sådan er modtagere relateret. F.eks. modtagerdomæner, funktioner for modtagerjob (administratorer, direktører osv.), virksomhedstyper (store, små, offentlige, private osv.) og brancher.
- **Nyttedata for angreb**: Ondsindede links, vedhæftede filer eller andre nyttedata i meddelelserne.

En kampagne kan være kortlevende eller kunne strække sig over flere dage, uger eller måneder med aktive og inaktive perioder. En kampagne kan blive startet i forhold til din specifikke organisation, eller din organisation kan være en del af en større kampagne på tværs af flere virksomheder.

## <a name="campaign-views-in-the-microsoft-365-defender-portal"></a>Kampagnevisninger på Microsoft 365 Defender-portalen

Kampagnevisninger er tilgængelige på Microsoft 365 Defender-portalen via <https://security.microsoft.com> **mail &** **samarbejdskampagner**\> eller direkte på <https://security.microsoft.com/campaigns>.

:::image type="content" source="../../media/campaigns-overview.png" alt-text="Oversigt over kampagner på Microsoft 365 Defender-portalen" lightbox="../../media/campaigns-overview.png":::

Du kan også få vist kampagnevisninger fra:

- **Mail & samarbejde** \> **Explorer** \> **Se** \> **Kampagner**
- **Mail & samarbejde** \> **Explorer** \> **Se** \> **Alle mails** \> Fanen **Kampagne**
- **Mail & samarbejde** \> **Explorer** \> **Se** \> **Phish** \> Fanen **Kampagne**
- **Mail & samarbejde** \> **Explorer** \> **Se** \> **Malware** \> Fanen **Kampagne**

Hvis du vil have adgang til kampagnevisninger, skal du være medlem af rollegrupperne **Organisationsadministration**, **Sikkerhedsadministrator** eller **Sikkerhedslæser** på Microsoft 365 Defender portalen. Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).

## <a name="campaigns-overview"></a>Oversigt over kampagner

Oversigtssiden viser oplysninger om alle kampagner.

Under standardfanen **Campaign (Kampagnetype** ) vises der et søjlediagram med antallet af modtagere pr. dag i området **Kampagnetype** . Grafen viser som standard både data for **phish** og **malware** .

> [!TIP]
> Hvis du ikke kan se nogen kampagnedata, kan du prøve at ændre datointervallet eller [filtrene](#filters-and-settings).

I tabellen under grafen på oversigtssiden kan du se følgende oplysninger under fanen **Kampagne** :

- **Navn**

- **Emneeksempel**: Emnelinjen i en af meddelelserne i kampagnen. Bemærk, at alle meddelelser i kampagnen ikke nødvendigvis har det samme emne.

- **Målrettet**: Procentdelen beregnet af: (antallet af kampagnemodtagere i din organisation) / (det samlede antal modtagere i kampagnen på tværs af alle organisationer i tjenesten). Denne værdi angiver, i hvor høj grad kampagnen kun er rettet mod din organisation (en højere værdi) i forhold til andre organisationer i tjenesten (en lavere værdi).

- **Type**: Denne værdi er enten **Phish** eller **Malware**.

- **Undertype**: Denne værdi indeholder flere oplysninger om kampagnen. Eksempel:
  - **Phish**: Hvor det er tilgængeligt, det mærke, der bliver phished af denne kampagne. For eksempel , `Microsoft``365`, `Unknown`, `Outlook`eller `DocuSign`.
  - **Malware**: f.eks `HTML/PHISH` . eller `HTML/<MalwareFamilyName>`.

  Hvor det er tilgængeligt, det mærke, der bliver phished af denne kampagne. Når registreringen er baseret på Defender for Office 365 teknologi, føjes præfikset **ATP-** til undertypeværdien.

- **Modtagere**: Antallet af brugere, der blev målrettet af denne kampagne.

- **Indbakke:** Antallet af brugere, der har modtaget meddelelser fra denne kampagne i deres indbakke (ikke leveret til deres mappe med uønsket mail).

- **Klikket**: Antallet af brugere, der har klikket på URL-adressen eller åbnet den vedhæftede fil i phishing-meddelelsen.

- **Klikfrekvens**: Procentdelen beregnet af "**Klikket** / **indbakke"**. Denne værdi er en indikator for kampagnens effektivitet. Det vil sige, at hvis modtagerne kunne identificere meddelelsen som phishing, og hvis de ikke klikkede på URL-adressen til nyttedata.

  Bemærk, at **Klikfrekvens** ikke bruges i malwarekampagner.

- **Besøgt**: Hvor mange brugere, der rent faktisk nåede frem til nyttedatawebstedet. Hvis der er **Klikkede** værdier, men Pengeskab Links blokerede adgang til webstedet, er denne værdi nul.

Fanen **Kampagnes oprindelse** viser meddelelseskilderne på et kort over verden.

### <a name="filters-and-settings"></a>Filtre og indstillinger

Øverst på siden **Kampagne** er der flere filter- og forespørgselsindstillinger, der kan hjælpe dig med at finde og isolere bestemte kampagner.

:::image type="content" source="../../media/campaign-filters-and-settings.png" alt-text="Kampagnefiltrene" lightbox="../../media/campaign-filters-and-settings.png":::

Den mest grundlæggende filtrering, du kan foretage, er startdatoen/klokkeslættet og slutdatoen/-klokkeslættet.

Hvis du vil filtrere visningen yderligere, kan du foretage en enkelt egenskab med filtrering af flere værdier ved at klikke på knappen **Kampagnetype** , foretage dit valg og derefter klikke på **Opdater**.

De kampagneegenskaber, der kan filtreres, og som er tilgængelige på knappen **Kampagnetype** , er beskrevet på følgende liste:

- **Grundlæggende**:
  - **Kampagnetype**: Vælg **Malware** eller **Phish**. Rydning af markeringerne har det samme resultat som at vælge begge.
  - **Kampagnenavn**
  - **Kampagneundertype**
  - **Afsender**
  - **Modtagere**
  - **Afsenderdomæne**
  - **Emne**
  - **Navn på vedhæftet fil**
  - **Malwarefamilie**
  - **Tags**: Brugere eller grupper, der har anvendt det angivne brugermærke (herunder prioritetskonti). Du kan få flere oplysninger om brugerkoder under [Brugerkoder](user-tags.md).
  - **Leveringshandling**
  - **Yderligere handling**
  - **Retningsbestemthed**
  - **Registreringsteknologi**
  - **Oprindelig leveringsplacering**
  - **Seneste leveringsplacering**
  - **Systemtilsidesættelser**

- **Avanceret**:
  - **Internetmeddelelses-id**: Tilgængelig i headerfeltet **Meddelelses-id** i brevhovedet. Et eksempel på en værdi er `<08f1e0f6806a47b4ac103961109ae6ef@server.domain>` (bemærk vinkelparenteserne).
  - **Netværksmeddelelses-id**: En GUID-værdi, der er tilgængelig i headerfeltet **X-MS-Exchange-Organization-Network-Message-Id** i meddelelsesheaderen.
  - **Afsenders IP**
  - **Vedhæftet SHA256**: Hvis du vil finde SHA256-hashværdien for en fil i Windows, skal du køre følgende kommando i en kommandoprompt: `certutil.exe -hashfile "<Path>\<Filename>" SHA256`.
  - **Klynge-id**
  - **Besked-id**
  - **Beskedpolitik-id**
  - **Kampagne-id**
  - **ZAP URL-signal**

- **URL-adresser**:
  - **URL-domæne**
  - **URL-domæne og -sti**
  - **URL**
  - **URL-sti**
  - **Klik på dom**

Hvis du vil have mere avanceret filtrering, herunder filtrering efter flere egenskaber, kan du klikke på knappen **Avanceret filter** for at oprette en forespørgsel. De samme kampagneegenskaber er tilgængelige, men med følgende forbedringer:

- Du kan klikke på **Tilføj en betingelse** for at vælge flere betingelser.
- Du kan vælge operatoren **And** eller **Or** mellem betingelser.
- Du kan vælge **gruppeelementet Betingelse** nederst på listen betingelser for at danne komplekse sammensatte betingelser.

Når du er færdig, skal du klikke på knappen **Forespørgsel** .

Når du har oprettet et grundlæggende eller avanceret filter, kan du gemme det ved hjælp af **Gem forespørgsel** eller **Gem forespørgsel som**. Når du senere vender tilbage til siden **Kampagner** , kan du indlæse et gemt filter ved at klikke på **Indstillinger for gemt forespørgsel**.

Hvis du vil eksportere grafen eller listen over kampagner, skal du klikke på **Eksportér** og vælge **Eksportér diagramdata** eller **Eksportér kampagneliste**.

Hvis du har et Microsoft Defender for Endpoint abonnement, kan du klikke på **MDE-Indstillinger** for at oprette forbindelse til eller afbryde oplysningerne om kampagnerne med Microsoft Defender for Endpoint. Du kan få flere oplysninger under [Integrer Microsoft Defender for Office 365 med Microsoft Defender for Endpoint](integrate-office-365-ti-with-mde.md).

## <a name="campaign-details"></a>Kampagnedetaljer

Når du klikker på navnet på en kampagne, vises kampagneoplysningerne i et pop op-vindue.

### <a name="campaign-information"></a>Kampagneoplysninger

Øverst i visningen med kampagnedetaljer er følgende kampagneoplysninger tilgængelige:

- **Kampagne-id**: Det entydige kampagne-id.
- **Aktivitet**: Kampagnens varighed og aktivitet.
- Følgende data for det valgte datoområdefilter (eller som du vælger på tidslinjen):
- **Indvirkning**
- **Meddelelser**: Det samlede antal modtagere.
- **Indbakke:** Antallet af meddelelser, der blev leveret til indbakken, ikke til mappen Uønsket mail.
- **Klikket på link**: Hvor mange brugere, der har klikket på URL-nyttedataene i phishing-meddelelsen.
- **Besøgt link**: Hvor mange brugere, der har besøgt URL-adressen.
- **Målrettet(%)**: Procentdelen beregnet af: (antallet af kampagnemodtagere i din organisation) / (det samlede antal modtagere i kampagnen på tværs af alle organisationer i tjenesten). Bemærk, at denne værdi beregnes i hele kampagnens levetid og ikke ændres på baggrund af datofiltre.
- Filtre for startdato/klokkeslæt og slutdata/klokkeslæt for kampagneflowet, som beskrevet i næste afsnit.
- En interaktiv tidslinje over kampagneaktivitet: Tidslinjen viser aktivitet over hele kampagnens levetid. Du kan holde markøren over datapunkterne i grafen for at se mængden af registrerede meddelelser.

:::image type="content" source="../../media/campaign-details-campaign-info.png" alt-text="Kampagneoplysningerne" lightbox="../../media/campaign-details-campaign-info.png":::

### <a name="campaign-flow"></a>Kampagneflow

Midt i visningen med kampagnedetaljer vises vigtige oplysninger om kampagnen i et vandret rutediagram (kaldet et _Sankey-diagram_ ). Disse oplysninger hjælper dig med at forstå elementerne i kampagnen og den potentielle indvirkning i din organisation.

> [!TIP]
> De oplysninger, der vises i rutediagrammet, styres af filteret for datointerval på tidslinjen, som beskrevet i det forrige afsnit.

:::image type="content" source="../../media/campaign-details-no-recipient-actions.png" alt-text="Kampagnedetaljerne, der ikke indeholder klik på brugerens URL-adresse" lightbox="../../media/campaign-details-no-recipient-actions.png":::

Hvis du holder markøren over et vandret bånd i diagrammet, kan du se antallet af relaterede meddelelser (f.eks. meddelelser fra en bestemt kilde-IP, meddelelser fra kilde-IP'en ved hjælp af det angivne afsenderdomæne osv.).

Diagrammet indeholder følgende oplysninger:

- **Afsender-IP-adresser**
- **Afsenderdomæner**
- **Filterbesigelser: Dommens** værdier er relateret til de tilgængelige phishing- og spamfiltreringssvarsler, som beskrevet i [overskrifter til anti-spammeddelelser](anti-spam-message-headers.md). De tilgængelige værdier er beskrevet i følgende tabel:

  |Værdi|Dom for spamfilter|Beskrivelse|
  |---|---|---|
  |**Tilladt**|`SFV:SKN` <p> `SFV:SKI`|Meddelelsen blev markeret som ikke spam og/eller sprunget over filtrering, før den blev evalueret af spamfiltrering. Meddelelsen blev f.eks. markeret som ikke spam af en regel for mailflow (også kendt som en transportregel). <p> Meddelelsen sprang over filtrering af spam af andre årsager. Afsenderen og modtageren ser f.eks. ud til at være i samme organisation.|
  |**Blokeret**|`SFV:SKS`|Meddelelsen blev markeret som spam, før den blev evalueret af spamfiltrering. Det kan f.eks. være en regel for et mailflow.|
  |**Opdaget**|`SFV:SPM`|Meddelelsen blev markeret som spam ved filtrering af spam.|
  |**Ikke registreret**|`SFV:NSPM`|Meddelelsen blev markeret som ikke spam af spamfiltrering.|
  |**Udgivet**|`SFV:SKQ`|Meddelelsen sprang over filtrering af spam, fordi den blev frigivet fra karantæne.|
  |**Tillad lejer**<sup>\*</sup>|`SFV:SKA`|Meddelelsen sprang over filtrering af spam på grund af indstillingerne i en politik mod spam. Afsenderen var f.eks. på listen over tilladte afsendere eller listen over tilladte domæner.|
  |**Lejerblok**<sup>\*\*</sup>|`SFV:SKA`|Meddelelsen blev blokeret af spamfiltrering på grund af indstillingerne i en politik mod spam. Afsenderen var f.eks. på listen over tilladte afsendere eller listen over tilladte domæner.|
  |**Tillad bruger**<sup>\*</sup>|`SFV:SFE`|Meddelelsen sprang over filtrering af spam, fordi afsenderen var på en brugers liste over Pengeskab afsendere.|
  |**Brugerblokering**<sup>\*\*</sup>|`SFV:BLK`|Meddelelsen blev blokeret af filtrering efter spam, fordi afsenderen var på en brugers liste over blokerede afsendere.|
  |**ZAP**|Nielsen|[Automatisk fjernelse på nul timer (ZAP)](zero-hour-auto-purge.md) flyttede den leverede meddelelse til mappen Uønsket mail eller karantæne. Du kan konfigurere handlingen i [politikker til bekæmpelse af spam](configure-your-spam-filter-policies.md).|

  <sup>\*</sup> Gennemse dine politikker for spam, da den tilladte meddelelse sandsynligvis ville være blevet blokeret af tjenesten.

  <sup>\*\*</sup> Gennemse dine politikker for spam, da disse meddelelser skal sættes i karantæne og ikke leveres.

- **Meddelelsesdestinationer**: Du vil sandsynligvis undersøge meddelelser, der er leveret til modtagere (enten til indbakken eller mappen Uønsket mail), også selvom brugerne ikke har klikket på URL-adressen med nyttedata i meddelelsen. Du kan også fjerne de karantænerede meddelelser fra karantæne. Du kan få flere oplysninger under [Karantænelagrede mails i EOP](quarantine-email-messages.md).
  - **Mappen Slettet**
  - **Faldt**
  - **Ekstern**: Modtageren er placeret i din lokale mailorganisation i hybridmiljøer.
  - **Mislykkedes**
  - **Videresendt**
  - **Indbakke**
  - **Mappen Uønsket mail**
  - **Karantæne**
  - **Unknown**

- **Klik på URL-adresser**: Disse værdier er beskrevet i næste afsnit.

> [!NOTE]
> I alle lag, der indeholder mere end 10 elementer, vises de øverste 10 elementer, mens resten er samlet i **Andre**.

#### <a name="url-clicks"></a>Klik på URL-adresser

Når en phishing-meddelelse leveres til en modtagers indbakke eller mappe med uønsket mail, er der altid en chance for, at brugeren klikker på URL-adressen til nyttedata. Hvis du ikke klikker på URL-adressen, er det en lille succes, men du skal finde ud af, hvorfor phishing-meddelelsen endda blev leveret til postkassen.

Hvis en bruger har klikket på URL-adressen til nyttedata i phishing-meddelelsen, vises handlingerne i **url-klikområdet** i diagrammet i visningen med kampagneoplysninger.

- **Tilladt**
- **BlockPage**: Modtageren klikkede på URL-adressen til nyttedata, men vedkommendes adgang til det skadelige websted blev blokeret af en politik [for Pengeskab links](safe-links.md) i din organisation.
- **BlockPageOverride**: Modtageren klikkede på NYTTEdata-URL-adressen i meddelelsen, Pengeskab Links forsøgte at stoppe dem, men de fik tilladelse til at tilsidesætte blokken. Undersøg dine [politikker for Pengeskab links](set-up-safe-links-policies.md) for at se, hvorfor brugerne har tilladelse til at tilsidesætte dommen Pengeskab Links og fortsætte til det skadelige websted.
- **PendingDetonationPage**: Pengeskab Vedhæftede filer i Microsoft Defender for Office 365 er i gang med at åbne og undersøge NYTTEDATA-URL-adressen i et virtuelt computermiljø.
- **PendingDetonationPageOverride**: Modtageren fik tilladelse til at tilsidesætte processen til detonation af nyttedata og åbne URL-adressen uden at vente på resultaterne.

### <a name="tabs"></a>Faner

Fanerne i visningen med kampagnedetaljer giver dig mulighed for at undersøge kampagnen yderligere.

> [!TIP]
> De oplysninger, der vises under fanerne, styres af filteret for datointerval på tidslinjen, som beskrevet i afsnittet [Kampagneoplysninger](#campaign-information) .

- **Klik på URL-adresser**: Hvis brugerne ikke har klikket på URL-adressen til nyttedata i meddelelsen, er denne sektion tom. Hvis en bruger kunne klikke på URL-adressen, udfyldes følgende værdier:
  - **Bruger**<sup>\*</sup>
  - **URL**<sup>\*</sup>
  - **Kliktidspunkt**
  - **Klik på dom**

- **Afsender-IP-adresser**
  - **Afsenders IP**<sup>\*</sup>
  - **Samlet antal**
  - **Indbakke**
  - **Ikke indbakket**
  - **SPF blev sendt**: Afsenderen blev godkendt af [SPF (Sender Policy Framework).](how-office-365-uses-spf-to-prevent-spoofing.md) En afsender, der ikke består SPF-valideringen, angiver en ikke-godkendt afsender, eller meddelelsen forfalsker en gyldig afsender.

- **Afsendere**
  - **Afsender**: Dette er den faktiske afsenderadresse i kommandoen SMTP MAIL FROM, som ikke nødvendigvis er den fra: mailadresse, som brugerne får vist i deres mailklienter.
  - **Samlet antal**
  - **Indbakke**
  - **Ikke indbakket**
  - **DKIM bestået**: Afsenderen blev godkendt af [Domænenøgler Identificeret Mail (DKIM)](support-for-validation-of-dkim-signed-messages.md). En afsender, der ikke består DKIM-validering, angiver en ikke-godkendt afsender, eller meddelelsen spooferer en gyldig afsender.
  - **DMARC sendt**: Afsenderen blev godkendt af [domænebaseret meddelelsesgodkendelse, rapportering og overensstemmelse (DMARC).](use-dmarc-to-validate-email.md) En afsender, der ikke består DMARC-valideringen, angiver en ikke-godkendt afsender, eller meddelelsen forfalsker en gyldig afsender.

- **Vedhæftede filer**
  - **Filnavn**
  - **SHA256**
  - **Malwarefamilie**
  - **Samlet antal**

- **URL**
  - **URL**<sup>\*</sup>
  - **Samlet antal**

<sup>\*</sup> Når du klikker på denne værdi, åbnes et nyt pop op-vindue, der indeholder flere oplysninger om det angivne element (bruger, URL-adresse osv.) oven på visningen med kampagneoplysninger. Hvis du vil vende tilbage til visningen med kampagnedetaljer, skal du klikke på **Udført** i det nye pop op-vindue.

### <a name="buttons"></a>Knapper

Knapperne nederst i visningen med kampagnedetaljer giver dig mulighed for at undersøge og registrere oplysninger om kampagnen:

- **Udforsk meddelelser**: Brug styrken ved Threat Explorer til at undersøge kampagnen yderligere:
  - **Alle meddelelser**: Åbner en ny Threat Explorer-søgefane ved hjælp af værdien **Kampagne-id** som søgefilter.
  - **Indbakkede meddelelser**: Åbner en ny Threat Explorer-søgefane ved hjælp af placeringen **Kampagne-id** og **Levering: Indbakke** som søgefilter.
  - **Interne meddelelser**: Åbner en ny Threat Explorer-søgefane ved hjælp af **kampagne-id** og **retningsbestemthed: Intern organisation** som søgefilter.

- **Download trusselsrapport**: Download kampagneoplysningerne til et Word-dokument (som standard kaldet CampaignReport.docx). Bemærk, at downloaden indeholder oplysninger om hele kampagnens levetid (ikke kun de filterdatoer, du har valgt).
