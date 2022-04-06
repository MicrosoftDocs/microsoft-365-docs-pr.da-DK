---
title: Politikker for overholdelse af regler og standarder i kommunikation
description: Få mere at vide om politikker for overholdelse af kommunikation.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: d8524715ad0e450671faeaeb0714992e297a02df
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/01/2022
ms.locfileid: "64595174"
---
# <a name="communication-compliance-policies"></a>Politikker for overholdelse af regler og standarder i kommunikation

## <a name="policies"></a>Politikker

> [!IMPORTANT]
> Brug af PowerShell til at oprette og administrere politikker for overholdelse af kommunikation understøttes ikke. Hvis du vil oprette og administrere disse politikker, skal du bruge kontrolelementerne til administration af politikker i [Microsoft 365 af kommunikationsoverholdelse](https://compliance.microsoft.com/supervisoryreview).

Du opretter politikker for overholdelse af kommunikation for Microsoft 365 organisationer i Microsoft 365 Overholdelsescenter. Politikker for overholdelse af kommunikation definerer, hvilken kommunikation og brugere, der skal gennemgås i din organisation, definerer, hvilke brugerdefinerede betingelser kommunikationen skal opfylde, og angiver, hvem der skal udføre anmeldelser. Brugere, der er tildelt rollen *Kommunikationsoverholdelsesadministrator*, kan konfigurere politikker, og alle, der har denne  rolle tildelt, kan få adgang til siden Overholdelse af kommunikation og globale indstillinger i Microsoft 365 Overholdelsescenter. Hvis det er nødvendigt, kan du eksportere historikken for ændringer i en politik til en .csv-fil (kommaseparerede værdier), som også omfatter status for vigtige beskeder, der afventer gennemgang, eskalerede elementer og løste elementer. Politikker kan ikke omdøbes og kan slettes, når der ikke længere er brug for dem.

## <a name="policy-templates"></a>Politikskabeloner

Politikskabeloner er foruddefinerede politikindstillinger, som du kan bruge til hurtigt at oprette politikker, der adresserer almindelige overholdelsesscenarier. Hver af disse skabeloner har forskelle i betingelser og omfang, og alle skabeloner bruger de samme typer scanningssignaler. Du kan vælge mellem følgende politikskabeloner:

|**Område**|**Politikskabelon**|**Detaljer**|
|:-----|:-----|:-----|
| **Upassende tekst** | Finde upassende tekst | - Placeringer: Exchange Online, Microsoft Teams, Yammer, Skype for Business <br> - Retning: Indgående, udgående, intern <br> - Gennemse procent: 100 % <br> - Betingelser: Trussel, trusler, trusler og målrettet chikane-klassificeringer |
| **Upassende billeder** | Find upassende billeder | - Placeringer: Exchange Online, Microsoft Teams, Yammer, Skype for Business <br> - Retning: Indgående, udgående, intern <br> - Gennemse procent: 100 % <br> - Betingelser: Klassificeringer af voksen og racy-billede |
| **Følsomme oplysninger** | Hold øje med følsomme oplysninger | - Placeringer: Exchange Online, Microsoft Teams, Yammer, Skype for Business <br> - Retning: Indgående, udgående, intern <br> - Gennemse procentdel: 10 % <br> - Betingelser: Følsomme oplysninger, indholdsmønstre og typer af indhold, der er direkte i brug, indstilling for brugerordbog, vedhæftede filer, der er større end 1 MB |
| **Lovgivningsmæssig overholdelse af regler og standarder** | Overvåg for overholdelse af lovgivning | - Placeringer: Exchange Online, Microsoft Teams, Yammer, Skype for Business <br> - Retning: Indgående, udgående <br> - Gennemse procentdel: 10 % <br> - Betingelser: Indstillingen Brugerordbog, vedhæftede filer, der er større end 1 MB |
| **I konflikt med hinanden** | Hold øje med interessekonflikter | - Placeringer: Exchange Online, Microsoft Teams, Yammer, Skype for Business <br> - Retning: Intern <br> - Gennemse procent: 100 % <br> - Betingelser: Ingen |

Kommunikation scannes én gang i døgnet fra det tidspunkt, hvor politikker oprettes. Hvis du f.eks. opretter en upassende indholdspolitik kl. 11:00, indsamler politikken signaler om overholdelse af kommunikation hver 24 timer kl. 11:00 dagligt. Redigering af en politik ændres ikke denne gang. Hvis du vil have vist seneste scanningsdato og -klokkeslæt for en politik, skal du gå til *kolonnen Seneste* politikscanning på **siden** Politik. Når du har oprettet en ny politik, kan det tage op til 24 timer at få vist den første scanningsdato og det første klokkeslæt for politikken. Dato og klokkeslæt for den sidste scanning konverteres til tidszonen for dit lokale system.

## <a name="pause-a-policy-preview"></a>Afbryd en politik midlertidigt (eksempel)

Når du har oprettet en politik for overholdelse af kommunikation, kan politikken midlertidigt blive sat på pause, hvis det er nødvendigt. Pause af en politik kan bruges til at teste eller foretage fejlfinding af politik matches eller til optimering af politikbetingelser. I stedet for at slette en politik under disse omstændigheder bevares de eksisterende politikadvarsler og meddelelser om igangværende undersøgelser og anmeldelser også, hvis du pauser. Hvis du stopper en politik, forhindres inspektion og generering af beskeder for alle brugermeddelelsesbetingelser, der er defineret i politikken, når politikken standses midlertidigt. Hvis du vil afbryde eller genstarte en politik midlertidigt, skal brugerne være medlem af *rollegruppen Kommunikationsoverholdelsesadministrator* .

Hvis du vil sætte en politik på pause **, skal du** gå til siden Politik, vælge en politik og derefter **vælge Afbryd** politik midlertidigt på værktøjslinjen handlinger. I **ruden Afbryd** politik midlertidigt skal du bekræfte, at du vil afbryde politikken midlertidigt, ved at vælge **Pause**. I nogle tilfælde kan det tage op til 24 timer, før en politik er sat på pause. Når politikken er sat på pause, oprettes der ikke beskeder om meddelelser, der svarer til politikken. Meddelelser, der er knyttet til beskeder, som blev oprettet, før politikken blev sat på pause, kan dog stadig undersøges, gennemgås og afhjælpes.

Politikstatus for midlertidigt afbrudte politikker kan angive flere tilstande:

- **Aktiv**: Politikken er aktiv
- **Midlertidigt afbrudt**: Politikken er sat på pause.
- **Pause:** Politikken er ved at blive sat på pause.
- **Genoptager**: Politikken i gang med at blive genoptaget.
- **Fejl under fortsættelse**: Der opstod en fejl, når politikken blev genoptaget. For fejlstablingssporingen skal du holde musen *over statussen* Fejl ved fortsættelse i kolonnen Status på siden Politik.
- **Fejl ved pause: Der** opstod en fejl, når politikken blev sat på pause. For sporing af fejlstabling skal du holde musen *over statussen* Fejl i pause i kolonnen Status på siden Politik.

Hvis du vil genoptage en politik, skal du **gå til** siden Politik, vælge en politik og derefter vælge **Fortsæt politik** på værktøjslinjen handlinger. I **ruden Fortsæt** politik skal du bekræfte, at du gerne vil fortsætte politikken ved at vælge **Fortsæt**. I nogle tilfælde kan det tage op til 24 timer, før en politik genoptages. Når politikken genoptages, oprettes der beskeder om meddelelser, der matcher politikken, og de kan undersøges, gennemgås og afhjælpes.

## <a name="copy-a-policy-preview"></a>Kopiér en politik (eksempel)

For organisationer med eksisterende politikker for overholdelse af kommunikation kan der være scenarier, når du opretter en ny politik ud fra en eksisterende politik. Kopiering af en politik opretter en nøjagtig kopi af en eksisterende politik, herunder alle in-scope-brugere, alle tildelte korrekturlæsere og alle politikbetingelser. Nogle scenarier kan omfatte:

- **Politikkens lagergrænse nået**: Politikker for overholdelse af regler og standarder for aktiv kommunikation har begrænsninger for meddelelseslager. Når lagergrænsen for en politik er nået, deaktiveres politikken automatisk. Organisationer, der har brug for fortsat at registrere, registrere og reagere på upassende meddelelser, der er omfattet af den deaktiverede politik, kan hurtigt oprette en ny politik med identisk konfiguration.
- **Registrer og** gennemse upassende meddelelser for forskellige grupper af brugere: Nogle organisationer foretrækker måske at oprette flere politikker med den samme konfiguration, men medtager forskellige in-scope-brugere og forskellige korrekturlæsere for hver politik.
- **Lignende politikker med små ændringer**: For politikker med komplekse konfigurationer eller betingelser kan det spare tid at oprette en ny politik ud fra en lignende politik.

Hvis du vil kopiere en politik, skal brugerne være medlem af rollegrupperne *Kommunikationsoverholdelse* *eller Overholdelse af* kommunikation. Når der oprettes en ny politik ud fra en eksisterende politik, kan det tage op til 24 timer at få vist meddelelser, der svarer til den nye politikkonfiguration.

Hvis du vil kopiere en politik og oprette en ny politik, skal du udføre følgende trin:

1. Vælg den politik, du vil kopiere.
2. Vælg **Knappen Kopiér** politik på kommandolinjen, eller vælg **Kopiér** politik i handlingsmenuen for politikken.
3. I **ruden Kopiér** politik kan du acceptere standardnavnet for politikken i **feltet Politiknavn** eller omdøbe politikken. Politiknavnet for den nye politik kan ikke være det samme som en eksisterende aktiv eller deaktiveret politik. Udfyld feltet **Beskrivelse** efter behov.
4. Hvis du ikke har brug for yderligere tilpasning af politikken, skal du **vælge Kopiér politik** for at fuldføre processen. Hvis du vil opdatere konfigurationen af den nye politik, skal du vælge **Tilpas politik**. Dette starter guiden til politik for at hjælpe dig med at opdatere og tilpasse den nye politik.

## <a name="user-reported-messages-policy"></a>Politik for brugerrapporterede meddelelser

Som en del af et lagdelt forsvar til at registrere og afhjælpe upassende meddelelser i din organisation kan du supplere politikker for overholdelse af kommunikation med brugerrapporterede meddelelser i Microsoft Teams. Denne funktion giver brugerne i organisationen mulighed for selv at rapportere upassende meddelelser, f.eks. chikanering eller farligt sprog, deling af indhold beregnet for voksne og deling af følsomme eller fortrolige oplysninger for at skabe et sikkert og kompatibelt arbejdsmiljø.

Indstillingen Rapportér et problem [i Teams-meddelelser](/microsoftteams/manage-teams-in-modern-portal), der er aktiveret som standard i Teams Administration, giver brugerne i organisationen mulighed for at sende upassende meddelelser til gennemsyn af politikkens korrekturlæsere for kommunikation. Disse meddelelser understøttes af en standardsystempolitik, der understøtter rapportering af meddelelser Teams kanaler, grupper og private chatsamtaler.

![Rapport om overholdelse af kommunikation et problem.](../media/communication-compliance-report-a-concern-full-menu.png)

Når en bruger sender en Teams chatbesked til gennemsyn, kopieres meddelelsen til politikken for brugerrapporterede meddelelser. Rapporterede meddelelser forbliver indledningsvist synlige for alle chatmedlemmer, og der er ikke nogen meddelelse til chatmedlemmerne eller afsenderen om, at en meddelelse er blevet rapporteret i kanal-, privat- eller gruppechats. En bruger kan ikke rapportere den samme meddelelse mere end én gang, og meddelelsen forbliver synlig for alle brugere i chatsessionen under politikgennemsynsprocessen. 

Under gennemsynsprocessen kan korrekturlæsere af kommunikationsoverholdelsen udføre [alle standard](/microsoft-365/compliance/communication-compliance-investigate-remediate#step-3-decide-on-a-remediation-action) afhjælpningshandlinger for meddelelsen, herunder fjerne meddelelsen fra Teams chat. Afhængigt af hvordan meddelelserne afhjælpes, vil meddelelsesafsenderen og modtagerne se [](/microsoftteams/communication-compliance#act-on-inappropriate-messages-in-microsoft-teams) forskellige meddelelser i Teams efter gennemsynet.

![Politik for overholdelse af regler og standarder i forbindelse med kommunikation – rapporteret af brugere.](../media/communication-compliance-user-reported-messages-policy.png)

Brugeren rapporterede meddelelser fra Teams-chatsamtaler er de eneste meddelelser, der behandles af politikken Brugerrapporteret meddelelse, og kun de tildelte korrekturlæsere for politikken kan ændres. Alle andre egenskaber for politikken kan ikke redigeres. Når politikken oprettes, er de første korrekturlæsere, der er tildelt politikken, alle medlemmer af rollegruppen Kommunikationsoverholdelsesadministratorer (hvis den er udfyldt med mindst én bruger) eller alle medlemmer af *organisationens* *globale* administratorrollegruppe. Opretteren af politikken er en tilfældigt udvalgt bruger fra rollegruppen Kommunikationsoverholdelsesadministratorer (hvis den er udfyldt med mindst én bruger) eller en tilfældigt udvalgt bruger fra *organisationens* globale administratorrollegruppe.  

Administratorer bør straks tildele brugerdefinerede korrekturlæsere til denne politik efter behov for organisationen. Dette kan omfatte korrekturlæsere som f.eks. din Compliance Officer, Risk Officer eller medlemmer af din HR-afdeling. Hvis du vil tilpasse korrekturlæserne for chatmeddelelser, der er sendt som brugerrapporterede meddelelser, skal du udføre følgende trin:

1. Log på [Microsoft 365 Overholdelsescenter bruger](https://compliance.microsoft.com/) legitimationsoplysninger til en administratorkonto i din Microsoft 365 organisation.
2. I Microsoft 365 Overholdelsescenter skal du gå til Overholdelse **af kommunikationsreglerne**.
3. På fanen **Politik** skal du vælge politikken *Brugerrapporterede meddelelser* og vælge **Rediger**.
4. I **ruden Overvåg for brugerrapporterede meddelelser** skal du tildele korrekturlæsere for politikken. Korrekturlæsere skal have postkasser hostet på Exchange Online. Når korrekturlæsere føjes til en politik, modtager de automatisk en mail, der giver dem besked om tildelingen af politikken og indeholder links til oplysninger om gennemsynsprocessen.
5. Vælg **Gem**.

Hvis du vil deaktivere brugere Teams meddelelser med indstillingen Rapportér et *problem, skal* du deaktivere [indstillingen slutbrugerrapportering Teams Administration](/microsoftteams/manage-teams-in-modern-portal).

## <a name="storage-limit-notification-preview"></a>Storage besked om begrænsning (forhåndsvisning)

Hver politik for overholdelse af kommunikation har en lagergrænse på 100 GB eller 1 million meddelelser, alt efter hvad der først nås. Efterhånden som politikken nærmer sig disse begrænsninger, sendes der automatisk meddelelser til brugere, der er  tildelt rollegrupperne Kommunikationsoverholdelse eller *Kommunikationsoverholdelse*. Meddelelser sendes, når lagerstørrelsen eller antallet af meddelelser når 80, 90 og 95 % af grænsen. Når politikgrænsen er nået, deaktiveres politikken automatisk, og politikken stopper med at behandle meddelelser for beskeder.

>[!IMPORTANT]
>Hvis en politik er deaktiveret, fordi den når lager- og meddelelsesgrænserne, skal du sørge for at evaluere, hvordan du administrerer den deaktiverede politik. Hvis du sletter politikken, slettes alle meddelelser, tilknyttede vedhæftede filer og beskeder om meddelelser permanent. Hvis du har brug for at bevare disse elementer til senere brug, skal du ikke slette den deaktiverede politik.

Hvis du vil administrere politikker, der nærmer sig lager- og meddelelsesbegrænsningerne, skal du overveje at oprette en kopi af politikken for at bevare dækningskontinuitet eller udføre følgende handlinger for at minimere den aktuelle politiks lagerstørrelse og antallet af meddelelser:

- Overvej at reducere antallet af brugere, der er tildelt til politikken. Hvis du fjerner brugere fra politikken eller opretter forskellige politikker for forskellige grupper af brugere, kan det hjælpe med at sænke væksten i politikstørrelsen og det samlede antal meddelelser.
- Undersøg politikken for unødvendige falske positive beskeder. Overvej at tilføje undtagelser eller ændringer i politikbetingelserne for at ignorere almindelige falske positive beskeder.
- Hvis en politik har nået lager- eller meddelelsesgrænserne og er blevet deaktiveret, skal du oprette en kopi af politikken for at fortsætte med at registrere og handle på de samme betingelser og for brugere.

## <a name="policy-settings"></a>Politikindstillinger

### <a name="users"></a>Brugere

Du kan vælge at vælge **Alle brugere eller** at definere bestemte brugere i en politik for overholdelse af kommunikation. Hvis du **vælger Alle brugere** , anvendes politikken på alle brugere og alle grupper, som en bruger er inkluderet i som medlem. Når du definerer bestemte brugere, anvendes politikken på de definerede brugere og de grupper, de definerede brugere er inkluderet i som medlem.

### <a name="direction"></a>Retning

Som standard er **Retning** betingelsen vist og kan ikke fjernes. Indstillinger for kommunikationsretning i en politik vælges enkeltvis eller sammen:

- **Indgående**: Registrerer kommunikation, der  sendes til overvågede brugere fra eksterne og interne afsendere, herunder andre overvågede brugere i politikken.
- **Udgående**: Registrerer kommunikation sendt fra overvågede brugere til eksterne og interne modtagere, herunder andre overvågede brugere i politikken.
- **Internt**: Registrerer kommunikation **mellem** overvågede brugere eller grupper i politikken.

### <a name="sensitive-information-types"></a>Typer af følsomme oplysninger

Du har mulighed for at medtage typer af følsomme oplysninger som en del af din politik for overholdelse af regler og standarder for kommunikation. Følsomme oplysningstyper er enten foruddefinerede eller brugerdefinerede datatyper, som kan hjælpe med at identificere og beskytte kreditkortnumre, bankkontonumre, pasnumre og meget mere. Som en del af [Få](dlp-learn-about-dlp.md) mere at vide om forebyggelse af datatab kan konfigurationen af følsomme oplysninger bruge mønstre, tegn afstand, tillidsniveauer og endda brugerdefinerede datatyper til at identificere og markere indhold, der kan være følsomt. Standardtyperne for følsomme oplysninger er:

- Finansiel
- Medicin og sundhed
- Beskyttelse af personlige oplysninger
- Brugerdefineret oplysningstype

> [!IMPORTANT]
> SIT'er har to forskellige metoder til at definere parametrene for det maksimale antal entydige forekomster. Du kan få mere at vide under [Forekomstantal understøttede værdier for SIT](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

Du kan få mere at vide om følsomme oplysninger og mønstrene, der er inkluderet i standardtyperne, under [Enhedsdefinitioner af typen Følsomme oplysninger](sensitive-information-type-entity-definitions.md).

### <a name="custom-keyword-dictionaries"></a>Brugerdefinerede ordbøger til nøgleord

Konfigurer brugerordbøger til nøgleord (eller ordbøger) for at levere enkel administration af nøgleord, der er specifikke for din organisation eller branche. Ordbøger til nøgleord understøtter op til 100 KB ord (efter komprimering) i ordbogen og understøtter alle sprog. Lejergrænsen er også 100 KB efter komprimeringen. Hvis det er nødvendigt, kan du anvende flere brugerordbøger til et enkelt ordordbog eller have en ordbog med et enkelt nøgleord pr. politik. Disse ordbøger er tildelt i en politik for overholdelse af kommunikation og kan være kilde fra en fil (f.eks. en .csv- eller .txt-liste), eller fra en liste, du kan importere i [Overholdelsescenter](create-a-keyword-dictionary.md). Brug brugerordbøger, når du har brug for at understøtte ord eller sprog, der er specifikke for din organisation og dine politikker.

### <a name="classifiers"></a>Klassificeringer

Indbyggede, trænbare og globale klassificeringer scanner sendte eller modtagne meddelelser på tværs af alle kommunikationskanaler i organisationen for forskellige typer af problemer med overholdelse. Klassificeringer bruger en kombination af kunstig intelligens og nøgleord til at identificere sprog i meddelelser, der sandsynligvis overtræder politikker for anti chikane. Indbyggede klassificeringer understøtter i øjeblikket identifikation af nøgleord i meddelelser på flere sprog:

- Kinesisk (forenklet)
- English
- French
- German
- Italian
- Japanese
- Portugisisk
- Spanish

Indbygget kommunikationsoverholdelse, der kan bruges, og globale klassificeringer scanner kommunikation for termer, billeder og kompatibilitet for følgende typer sprog og indhold:

- **Voksenbilleder**: Scanninger for billeder, der har et seksuelt eksplicit indhold.
- **Ophav**: Scanninger for eksplicitte sprog, der er særligt følsomme over for sprog, der er særligt følsomme over for de american/sorte grupper, når man sammenligner dem med andre communities.
- **Gory-billeder**: Scanninger for billeder, der afbilder vold og gås.
- **Bandeord**: Scanninger for krænkende udtryk, som er pinlige hos de fleste.
- **Racy-billeder**: Scanninger af billeder, der har et seksuelt indhold, der har et seksuelt indhold, men indeholder mindre eksplicit indhold end billeder, der anses for at være voksne.
- **Målrettet chikane**: Scanninger til stødende adfærd målrettet mod personer vedrørende racer, farve, religion, national oprindelse.
- **Trussel**: Scanninger for trusler om at begået vold eller fysisk skade på en person eller ejendom.

*Billedklasseerne* Voksen, *Racy* og *Gory* scanner filer i formaterne .jpeg, .png, .gif og .bmp. Størrelsen på billedfiler skal være mindre end 4 megabyte (MB), og billedernes dimensioner skal være større end 50x50 pixel og større end 50 kilobyte (KB), for at billedet kan evalueres. Billedidentifikation understøttes Exchange Online mails og Microsoft Teams kanaler og chats.

De indbyggede, træbare og globale klassificeringer giver ikke en komplet liste over ord eller billeder på tværs af disse områder. Yderligere ændres sprog og kulturelle standarder løbende, og i forhold til disse realiteter forbeholder Microsoft sig retten til efter eget skøn at opdatere klassificeringer. Selvom klassificeringer kan hjælpe din organisation med at overvåge disse områder, er klassificeringer ikke beregnet til at levere din organisations eneste måde at overvåge eller adressere et sådant sprog eller billeder på. Din organisation, ikke Microsoft, forbliver ansvarlig for alle beslutninger vedrørende overvågning, scanning og blokering af sprog og billeder på disse områder, herunder overholdelse af lokal lovgivning om beskyttelse af personlige oplysninger og andre gældende love. Microsoft opfordrer til rådgivning med juridisk rådgivning før implementering og brug.

> [!NOTE]
> Politikker, der bruger klassificeringer, undersøger og evaluerer meddelelser med et ordantal på seks eller større. Meddelelser, der indeholder mindre end seks ord, evalueres ikke i politikker ved hjælp af klassificeringer. Hvis du vil identificere og handle på kortere meddelelser, der indeholder upassende indhold, anbefaler vi, at du inkluderer en brugerordbog med nøgleord til overvågning af politikker for overholdelse af kommunikation for denne type indhold.

Du kan finde oplysninger om, hvilke klassificeringer der kan Microsoft 365, i [Introduktion til klassificeringer, der kan trænes](classifier-get-started-with.md).

### <a name="optical-character-recognition-ocr"></a>Optisk tegngenkendelse (OCR)

Konfigurer indbyggede politikker eller brugerdefinerede politikker for overholdelse af regler og standarder for kommunikation for at scanne og identificere udskrevet eller håndskrevet tekst fra billeder, der kan være upassende i din organisation. Integreret [Azure Cognitive Services](/azure/cognitive-services/computer-vision/overview-ocr) og understøttelse af optisk scanning til at identificere tekst i billeder hjælper analytikere og virusser med at registrere og reagere på forekomster, hvor upassende adfærd kan blive overset i kommunikation, der primært er ikke-tekstuel.

Du kan aktivere optisk tegngenkendelse (OCR) i nye politikker fra skabeloner, brugerdefinerede politikker eller opdatere eksisterende politikker for at udvide understøttelsen af behandling af integrerede billeder og vedhæftede filer. Når det er aktiveret i en politik, der er oprettet ud fra en politikskabelon, understøttes automatisk scanning for integrerede eller vedhæftede billeder i Microsoft Teams og chatmeddelelser. For billeder, der er integreret i dokumentfiler, understøttes OCR-scanning ikke. I forbindelse med brugerdefinerede politikker skal en eller flere betingede indstillinger, der er knyttet til nøgleord, indbyggede klassificeringer eller følsomme oplysningstyper, konfigureres i politikken for at aktivere valget af OCR-scanning.

Billeder fra 50 KB til 4 MB i følgende billedformater scannes og behandles:

- .jpg/.jpeg (joint photographic experts group)
- .png (bærbar netværksgrafik)
- .bmp (bitmap)
- .tiff (tag image file format)
- .pdf (portable dokumentformat)

> [!NOTE]
> Scanning og udtrækning for integrerede og .pdf billeder understøttes i øjeblikket kun for mails.

Når du gennemser ventende beskeder for politikker med OCR aktiveret, vises billeder, der identificeres og matches med politikbetingelser, som underordnede elementer for tilknyttede beskeder. Du kan få vist det oprindelige billede for at evaluere den identificerede tekst i konteksten med den oprindelige meddelelse. Det kan tage op til 48 timer, før registrerede billeder er tilgængelige med beskeder.

### <a name="conditional-settings"></a>Betingede indstillinger
<a name="ConditionalSettings"> </a>

De betingelser, du vælger til politikken, gælder for kommunikation fra både mail og tredjepartskilder i din organisation (f.eks. fra Hurtig bloomberg).

I følgende tabel beskrives flere oplysninger om hver enkelt betingelse.

|**Betingelse**|**Sådan bruger du denne betingelse**|
|:-----|:-----|
| **Indhold svarer til en af disse klassificeringer** | Anvend på politikken, når eventuelle klassificeringer medtages eller udelades i en meddelelse. Nogle klassificeringer er foruddefineret i din lejer, og brugerdefinerede klassificeringer skal konfigureres separat, før de er tilgængelige for denne betingelse. Der kan kun defineres én klassificering som en betingelse i en politik. Hvis du vil have mere at vide om konfiguration af klassificeringer, skal du se Få mere at vide om trænbare [klassificeringer (eksempel)](classifier-learn-about.md). |
| **Indhold indeholder en af disse typer af følsomme oplysninger** | Anvend på politikken, når følsomme oplysningstyper medtages eller udelades i en meddelelse. Nogle klassificeringer er foruddefinerede i din lejer, og brugerdefinerede klassificeringer kan konfigureres separat eller som en del af betingelsesprocessen. Hver type af følsomme oplysninger, du vælger, anvendes separat, og kun én af disse typer af følsomme oplysninger skal anvendes, for at politikken kan anvendes på meddelelsen. Du kan finde flere oplysninger om brugerdefinerede typer af følsomme oplysninger [i Få mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md). |
| **Der modtages en meddelelse fra et af disse domæner**  <br><br> **Meddelelsen modtages ikke fra nogen af disse domæner** | Anvend politikken for at medtage eller udelade bestemte domæner eller mailadresser i modtagne meddelelser. Angiv hvert domæne eller hver mailadresse, og adskid flere domæner eller mailadresser med et komma. Hvert domæne eller den angivne mailadresse anvendes separat, kun ét domæne eller én mailadresse skal gælde for politikken for meddelelsen. <br><br> Hvis du vil scanne alle mails fra et bestemt domæne, men vil udelade meddelelser, der ikke behøver at blive gennemset (nyhedsbreve, meddelelser og så videre), skal du konfigurere, at der ikke  modtages en meddelelse fra nogen af disse domænebetingelse, som udelader mailadressen (f.eks. "newsletter@contoso.com"). |
| **Meddelelsen sendes til et af disse domæner**  <br><br> **Meddelelsen sendes ikke til nogen af disse domæner** | Anvend politikken for at medtage eller udelade bestemte domæner i sendte meddelelser. Angiv hvert domæne, og adskid flere domæner med et komma. Hvert domæne anvendes separat, kun ét domæne skal gælde for den politik, der skal gælde for meddelelsen. <br><br> Hvis du vil udelade alle mails, der sendes til **to** bestemte domæner, skal du konfigurere, at meddelelsen ikke sendes til nogen af disse domænebetingede betingelser med de to domæner (f.eks. 'contoso.com,wingtiptoys.com'). |
| **Meddelelsen er klassificeret med nogen af disse etiketter**  <br><br> **Meddelelsen er ikke klassificeret med nogen af disse etiketter** | Sådan anvender du politikken, når visse opbevaringsetiketter medtages eller udelades i en meddelelse. Opbevaringsnavne skal konfigureres separat, og konfigurerede etiketter vælges som en del af denne betingelse. Hver etiket, du vælger, anvendes separat (kun én af disse etiketter skal gælde, for at politikken anvendes på meddelelsen). Du kan finde flere oplysninger om opbevaringsnavne i [Få mere at vide om opbevaringspolitikker og opbevaringsnavne](retention.md).|
| **Meddelelsen indeholder et af disse ord**  <br><br> **Meddelelsen indeholder ingen af disse ord** | Hvis du vil anvende politikken, når bestemte ord eller udtryk medtages eller udelades i en meddelelse, skal du skrive hvert ord adskilt med et komma. I forbindelse med udtryk med to eller flere ord skal du bruge anførselstegn omkring udtrykket. Hvert ord eller udtryk, du skriver, anvendes separat (kun ét ord skal anvendes, for at politikken gælder for meddelelsen). Du kan finde flere oplysninger om at indtaste ord eller udtryk i næste afsnit [Matchende ord og udtryk i mails eller vedhæftede filer](communication-compliance-policies.md#Matchwords).|
| **Vedhæftet fil indeholder et af disse ord**  <br><br> **Vedhæftet fil indeholder ingen af disse ord** | Hvis du vil anvende politikken, når bestemte ord eller udtryk medtages eller udelades i en vedhæftet fil (f.eks. et Word-dokument), skal du angive hvert ord adskilt med et komma. I forbindelse med udtryk med to eller flere ord skal du bruge anførselstegn omkring udtrykket. Hvert ord eller udtryk, du angiver, anvendes separat (kun ét ord skal gælde, for at politikken kan anvendes på den vedhæftede fil). Du kan finde flere oplysninger om at indtaste ord eller udtryk i næste afsnit [Matchende ord og udtryk i mails eller vedhæftede filer](communication-compliance-policies.md#Matchwords).|
| **Vedhæftet fil er en af disse filtyper**  <br><br> **Vedhæftet fil er ingen af disse filtyper** | For at overvåge kommunikation, der indeholder eller udelader bestemte typer vedhæftede filer, skal du indtaste filtypenavnene (f.eks. .exe eller .pdf). Hvis du vil medtage eller udelade flere filtypenavne, skal du angive disse på separate linjer. Kun én udvidelse til vedhæftede filer skal svare til den politik, der skal anvendes.|
| **Meddelelsesstørrelse er større end**  <br><br> **Meddelelsesstørrelse er ikke større end** | Hvis du vil gennemse meddelelser, der er baseret på en bestemt størrelse, skal du bruge disse betingelser til at angive den maksimale eller mindste størrelse, en meddelelse kan være, før den gennemgås. Hvis du f.eks.  angiver, \> at Meddelelsesstørrelse er større end **1,0 MB**, kan alle meddelelser, der er 1,01 MB og større, gennemgås. Du kan vælge byte, kilobyte, megabyte eller gigabyte for denne betingelse.|
| **Vedhæftet fil er større end**  <br><br> **Vedhæftet fil er ikke større end** | Hvis du vil gennemse meddelelser baseret på størrelsen af deres vedhæftede filer, skal du angive den maksimale eller mindste størrelse, en vedhæftet fil kan være, før meddelelsen og dens vedhæftede filer kan gennemgås. Hvis du f.eks. angiver, at Vedhæftet fil er større end **2,0** \> MB, kan alle meddelelser med vedhæftede filer på 2,01 MB og derover gennemgås. Du kan vælge byte, kilobyte, megabyte eller gigabyte for denne betingelse.|

#### <a name="matching-words-and-phrases-to-emails-or-attachments"></a>Matchende ord og udtryk til mails eller vedhæftede filer
<a name="Matchwords"> </a>

Hvert ord, du indtaster og adskiller med et komma, anvendes separat (kun ét ord skal gælde for den politikbetingelse, der gælder for mailen eller den vedhæftede fil). Lad os f.eks. bruge betingelsen **Meddelelse indeholder** et af disse ord med nøgleordene "bankmand", "fortroligt" og "insider-handel" adskilt af et komma (bankmand, fortroligt,"insider-handel"). Politikken gælder for alle meddelelser, der indeholder ordet "banket", "fortroligt" eller ordet "insider-handel". Kun ét af disse ord eller udtryk skal forekomme, for at denne politikbetingelse kan anvendes. Ord i meddelelsen eller den vedhæftede fil skal svare nøjagtigt til det, du angiver.

> [!IMPORTANT]
>
> Når du importerer en brugerordbogsfil, skal hvert ord eller udtryk være adskilt med vognretur og på en separat linje. Eksempel:
>
> *banking* <br>
> *fortrolig* <br>
> *insider-handel*

Hvis du vil scanne både mails og vedhæftede filer for de samme nøgleord, [](create-a-keyword-dictionary.md) skal du oprette en brugerordbog til de ord, du vil scanne, i meddelelser. Denne politikkonfiguration identificerer definerede nøgleord, der vises i enten mailen ELLER **i den** vedhæftede fil. Brug af de almindelige betingede politikindstillinger *(Meddelelse* indeholder et af disse ord, og Vedhæftet fil indeholder et af disse *ord) til* at identificere ord i meddelelser og vedhæftede filer kræver, at ordene er til stede i BÅDE meddelelsen og den vedhæftede fil.

#### <a name="enter-multiple-conditions"></a>Angiv flere betingelser

Hvis du indtaster flere betingelser, Microsoft 365 alle betingelserne sammen for at afgøre, hvornår kommunikationspolitikken skal anvendes på kommunikationselementer. Når du konfigurerer flere betingelser, skal alle betingelser være opfyldt, for at politikken kan anvendes, medmindre du angiver en undtagelse. Du skal f.eks. have en politik, der gælder, hvis en meddelelse indeholder ordet "handel" og er større end 2 MB. Men hvis meddelelsen også indeholder ordene "Godkendt af Contoso Financial", bør politikken ikke gælde. I dette eksempel defineres de tre betingelser således:

- **Meddelelsen indeholder et af disse ord** med nøgleordet "bytte"
- **Meddelelsesstørrelse er større end** med værdien 2 MB
- **Meddelelsen indeholder ingen af disse ord** med nøgleordene "Godkendt af Contoso Financial Team"

### <a name="review-percentage"></a>Gennemse procentdel

Hvis du vil reducere mængden af indhold, der skal gennemses, kan du angive en procentdel af al kommunikation, der er underlagt en politik for overholdelse af regler og standarder for kommunikation. Der vælges et tilfældigt udsnit af indhold i realtid fra den samlede procentdel af indhold, der opfylder de valgte politikbetingelser. Hvis du vil have korrekturlæsere til at gennemse alle elementer, kan du konfigurere **100 % i** en politik for overholdelse af kommunikation.

## <a name="alert-policies"></a>Underretningspolitikker

Når du har konfigureret en politik, oprettes der automatisk en tilsvarende beskedpolitik, og der genereres beskeder for meddelelser, der opfylder de betingelser, der er defineret i politikken. Det kan tage op til 24 timer, efter oprettelse af en politik begynder at modtage beskeder fra aktivitetsindikatorer. Som standard tildeles alle beskedudløsere til påmindelsesbeskeder et alvorsniveau af medie i den tilknyttede beskedpolitik. Der genereres beskeder for en politik for overholdelse af kommunikation, når grænseværdien for sammenlægningsudløser er nået i den tilknyttede beskedpolitik. Der sendes en enkelt mailbesked én gang i døgnet for eventuelle beskeder, uanset antallet af individuelle meddelelser, der opfylder politikbetingelserne. Contoso har f.eks. aktiveret en upassende indholdspolitik, og for 1. januar var der 100 politik match, der genererede seks beskeder. Der sendes en enkelt mailbesked for de seks beskeder i slutningen af 1. januar.

For politikker for overholdelse af kommunikation er følgende værdier for beskedpolitik konfigureret som standard:

|**Beskedpolitikudløser**|**Standardværdi**|
|:-----|:-----|
| Akkumulering | Enkel akkumulering |
| Grænseværdi | Standard: 4 aktiviteter <br> Minimum: 3 aktiviteter <br> Maksimum: 2.147.483.647 aktiviteter |
| Vindue | Standard: 60 minutter <br> Minimum: 60 minutter <br> Maksimum: 10.000 minutter |

> [!NOTE]
> Udløserindstillingerne for grænseværdi for beskedpolitik for aktiviteter understøtter en minimumværdi på 3 eller højere for politikker for overholdelse af kommunikation.

Du kan ændre standardindstillingerne for udløsere for antal aktiviteter, periode for aktiviteterne og for bestemte brugere i beskedpolitikker på siden Beskedpolitikker i Microsoft 365 Overholdelsescenter.

### <a name="change-the-severity-level-for-an-alert-policy"></a>Ændre alvorsniveauet for en beskedpolitik

Hvis du vil ændre alvorsniveauet tildelt i en beskedpolitik for en bestemt politik for overholdelse af kommunikation, skal du udføre følgende trin:

1. Log på [Microsoft 365 Overholdelsescenter bruger](https://compliance.microsoft.com) legitimationsoplysninger til en administratorkonto i din Microsoft 365 organisation.

2. I Microsoft 365 Overholdelsescenter skal du gå til **Politikker**.

3. Vælg **Office 365 besked** på **siden** Politikker for at åbne **siden Politikker for vigtige** beskeder.

4. Markér afkrydsningsfeltet for den politik for overholdelse af kommunikation, du vil opdatere, og vælg derefter **Rediger politik**.

5. På fanen **Beskrivelse** skal du vælge **rullelisten Alvorsgrad** for at konfigurere beskedniveauet for politikker.

6. Vælg **Gem** for at anvende det nye alvorsniveau på politikken.

7. Vælg **Luk for** at afslutte siden med oplysninger om beskedpolitik.
