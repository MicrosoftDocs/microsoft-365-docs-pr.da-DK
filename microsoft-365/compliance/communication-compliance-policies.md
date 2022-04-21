---
title: Politikker for kommunikation med overholdelse af angivne standarder
description: Få mere at vide om politikker for overholdelse af kommunikation.
keywords: Microsoft 365, Microsoft Purview, overholdelse af angivne standarder, kommunikation
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
ms.openlocfilehash: 47c7ddbc5ce935e8b9fedb7682daa6af468b66b4
ms.sourcegitcommit: 5b321693214e3859f5af8f1774d2a5ff685ab3b7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/21/2022
ms.locfileid: "65015018"
---
# <a name="communication-compliance-policies"></a>Politikker for kommunikation med overholdelse af angivne standarder

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

## <a name="policies"></a>Politikker

> [!IMPORTANT]
> Brug af PowerShell til at oprette og administrere politikker for kommunikation med overholdelse af angivne standarder understøttes ikke. Hvis du vil oprette og administrere disse politikker, skal du bruge kontrolelementerne til administration af politikker i [kommunikationsoverholdelsesløsningen](https://compliance.microsoft.com/supervisoryreview).

Du opretter politikker for overholdelse af kommunikation for Microsoft 365 organisationer på Microsoft Purview-overholdelsesportalen. Politikker for kommunikation med overholdelse af angivne standarder definerer, hvilken kommunikation og hvilke brugere der skal gennemses i din organisation, definerer, hvilke brugerdefinerede betingelser kommunikationen skal opfylde, og angiver, hvem der skal udføre korrekturer. Brugere, der er tildelt rollen *Administrator af kommunikationsoverholdelse* , kan konfigurere politikker, og alle, der har denne rolle tildelt, kan få adgang til siden **Kommunikation med overholdelse af angivne standarder** og globale indstillinger på Microsoft Purview-overholdelsesportalen. Hvis det er nødvendigt, kan du eksportere oversigten over ændringer til en politik til en .csv (kommaseparerede værdier), der også indeholder status for beskeder, der afventer gennemsyn, eskalerede elementer og løste elementer. Politikker kan ikke omdøbes og kan slettes, når der ikke længere er brug for dem.

## <a name="policy-templates"></a>Politikskabeloner

Politikskabeloner er foruddefinerede politikindstillinger, som du kan bruge til hurtigt at oprette politikker til at håndtere almindelige scenarier for overholdelse af angivne standarder. Hver af disse skabeloner har forskelle i betingelser og omfang, og alle skabeloner bruger de samme typer scanningssignaler. Du kan vælge mellem følgende politikskabeloner:

|**Område**|**Politikskabelon**|**Detaljer**|
|:-----|:-----|:-----|
| **Upassende tekst** | Registrer upassende tekst | - Placeringer: Exchange Online, Microsoft Teams, Yammer, Skype for Business <br> - Retning: Indgående, Udgående, Intern <br> - Procent for gennemsyn: 100 % <br> - Betingelser: Trussel, diskrimination og målrettet chikaneklassificering |
| **Upassende billeder** | Registrer upassende billeder | - Placeringer: Exchange Online, Microsoft Teams, Yammer, Skype for Business <br> - Retning: Indgående, Udgående, Intern <br> - Procent for gennemsyn: 100 % <br> - Betingelser: Billedklassificering for voksne og racy |
| **Følsomme oplysninger** | Overvåg for følsomme oplysninger | - Placeringer: Exchange Online, Microsoft Teams, Yammer, Skype for Business <br> - Retning: Indgående, Udgående, Intern <br> - Procent for gennemsyn: 10% <br> - Betingelser: Følsomme oplysninger, brugsklare indholdsmønstre og typer, indstilling for brugerordbog, vedhæftede filer, der er større end 1 MB |
| **Overholdelse af regler og standarder** | Overvåg overholdelse af regler og standarder | - Placeringer: Exchange Online, Microsoft Teams, Yammer, Skype for Business <br> - Retning: Indgående, Udgående <br> - Procent for gennemsyn: 10% <br> - Betingelser: indstilling for brugerordbog, vedhæftede filer, der er større end 1 MB |
| **Interessekonflikt** | Overvågning af interessekonflikter | - Placeringer: Exchange Online, Microsoft Teams, Yammer, Skype for Business <br> - Retning: Intern <br> - Procent for gennemsyn: 100 % <br> - Betingelser: Ingen |

Kommunikation scannes hver 24. time fra det tidspunkt, hvor politikkerne oprettes. Hvis du f.eks. opretter en upassende indholdspolitik kl. 11:00, indsamler politikken kommunikationsoverholdelsessignaler hver 24. time kl. 11:00 dagligt. Redigering af en politik ændres ikke denne gang. Hvis du vil have vist den seneste scanningsdato og -klokkeslæt for en politik, skal du gå til kolonnen *Seneste politikscanning* på siden **Politik** . Når du har oprettet en ny politik, kan det tage op til 24 timer at få vist den første dato og det første klokkeslæt for politikscanning. Datoen og klokkeslættet for den seneste scanning konverteres til tidszonen i dit lokale system.

## <a name="pause-a-policy-preview"></a>Afbryd en politik midlertidigt (prøveversion)

Når du har oprettet en politik for overholdelse af angivne standarder for kommunikation, kan politikken være midlertidigt afbrudt, hvis det er nødvendigt. Afbrydelse af en politik kan bruges til at teste eller foretage fejlfinding af politikforekomster eller til at optimere politikbetingelser. I stedet for at slette en politik under disse omstændigheder bevarer midlertidig afbrydelse af en politik også eksisterende politikbeskeder og meddelelser i forbindelse med igangværende undersøgelser og anmeldelser. Hvis en politik afbrydes midlertidigt, forhindres kontrol og oprettelse af beskeder for alle de betingelser for brugermeddelelser, der er defineret i politikken, for det tidspunkt, hvor politikken afbrydes midlertidigt. Hvis du vil afbryde en politik midlertidigt eller genstarte den, skal brugerne være medlem af rollegruppen *Administrator af kommunikationsoverholdelse* .

Hvis du vil afbryde en politik midlertidigt, skal du gå til siden **Politik** , vælge en politik og derefter vælge **Afbryd politik midlertidigt** på værktøjslinjen Handlinger. I ruden **Afbryd politik midlertidigt** skal du bekræfte, at du vil afbryde politikken midlertidigt ved at vælge **Afbryd midlertidigt**. I nogle tilfælde kan det tage op til 24 timer, før en politik afbrydes midlertidigt. Når politikken er midlertidigt afbrudt, oprettes der ikke beskeder om meddelelser, der stemmer overens med politikken. Meddelelser, der er knyttet til beskeder, som blev oprettet, før politikken blev afbrudt midlertidigt, forbliver dog tilgængelige til undersøgelse, gennemgang og afhjælpning.

Politikstatussen for midlertidigt afbrudte politikker kan angive flere tilstande:

- **Aktiv**: Politikken er aktiv
- **Midlertidigt afbrudt**: Politikken er midlertidigt afbrudt.
- **Pause:** Politikken er i gang med at blive midlertidigt afbrudt.
- **Genoptagelse**: Politikken, der er ved at blive genoptaget.
- **Fejl under genoptagelse**: Der opstod en fejl under genoptagelse af politikken. I forbindelse med sporingen af fejlstakken skal du holde musen over *fejlen ved at genoptage* status i kolonnen Status på siden Politik.
- **Fejl ved afbrydelse**: Der opstod en fejl under midlertidig afbrydelse af politikken. I forbindelse med sporingen af fejlstakken skal du holde musen over *fejlen ved at afbryde status midlertidigt* i kolonnen Status på siden Politik.

Hvis du vil genoptage en politik, skal du gå til siden **Politik** , vælge en politik og derefter vælge **Genoptag politik** på værktøjslinjen Handlinger. I ruden **Genoptag politik** skal du bekræfte, at du vil genoptage politikken ved at vælge **Fortsæt**. I nogle tilfælde kan det tage op til 24 timer, før en politik genoptages. Når politikken genoptages, oprettes der beskeder om meddelelser, der stemmer overens med politikken, og de vil være tilgængelige til undersøgelse, gennemgang og afhjælpning.

## <a name="copy-a-policy-preview"></a>Kopiér en politik (eksempelvisning)

For organisationer med eksisterende politikker for overholdelse af kommunikation kan der være scenarier, når du opretter en ny politik ud fra en eksisterende politik, kan være nyttig. Når du kopierer en politik, oprettes der en nøjagtig dublet af en eksisterende politik, herunder alle brugere i området, alle tildelte korrekturlæsere og alle politikbetingelser. Nogle scenarier kan omfatte:

- **Lagergrænsen for politik er nået**: Politikker for overholdelse af angivne standarder for aktiv kommunikation har grænser for meddelelseslager. Når lagergrænsen for en politik er nået, deaktiveres politikken automatisk. Organisationer, der har brug for fortsat at registrere, registrere og reagere på upassende meddelelser, der er omfattet af den deaktiverede politik, kan hurtigt oprette en ny politik med en identisk konfiguration.
- **Registrer og gennemse upassende meddelelser for forskellige grupper af brugere**: Nogle organisationer foretrækker måske at oprette flere politikker med den samme konfiguration, men omfatter forskellige brugere i området og forskellige korrekturlæsere for hver politik.
- **Lignende politikker med små ændringer**: For politikker med komplekse konfigurationer eller betingelser kan det spare tid at oprette en ny politik ud fra en lignende politik.

Hvis du vil kopiere en politik, skal brugerne være medlem af rollegrupperne *Kommunikationsoverholdelse* eller *Administrator af kommunikationsoverholdelse* . Når en ny politik er oprettet ud fra en eksisterende politik, kan det tage op til 24 timer at få vist meddelelser, der svarer til den nye politikkonfiguration.

Hvis du vil kopiere en politik og oprette en ny politik, skal du fuldføre følgende trin:

1. Vælg den politik, du vil kopiere.
2. Vælg **Knappen Kopiér politikkommandolinje** på kommandolinjen, eller vælg **Kopiér politik** i handlingsmenuen for politikken.
3. I ruden **Kopiér politik** kan du acceptere standardnavnet for politikken i feltet **Politiknavn** eller omdøbe politikken. Politiknavnet for den nye politik må ikke være det samme som en eksisterende aktiv eller deaktiveret politik. Udfyld feltet **Beskrivelse** efter behov.
4. Hvis du ikke har brug for yderligere tilpasning af politikken, skal du vælge **Kopiér politik** for at fuldføre processen. Hvis du har brug for at opdatere konfigurationen af den nye politik, skal du vælge **Tilpas politik**. Dette starter guiden Politik for at hjælpe dig med at opdatere og tilpasse den nye politik.

## <a name="user-reported-messages-policy"></a>Politik for brugerrapporterede meddelelser

>[!NOTE]
>Brugerrapporterede meddelelser vil begynde at være tilgængelige for organisationer, der har licens til [kommunikation med overholdelse af angivne standarder](/microsoft-365/compliance/communication-compliance-configure#subscriptions-and-licensing) og Microsoft Teams fra og med maj 2022. Denne funktion skal være tilgængelig for alle organisationer med licens senest den 31. august 2022.

Som en del af et lagdelt forsvar til registrering og afhjælpning af upassende meddelelser i din organisation kan du supplere politikker for overholdelse af kommunikation med brugerrapporterede meddelelser i Microsoft Teams. Denne funktion giver brugerne i din organisation mulighed for selv at rapportere upassende meddelelser, f.eks. chikanere eller truende sprog, deling af indhold fra voksne og deling af følsomme eller fortrolige oplysninger, for at hjælpe med at fremme et sikkert og kompatibelt arbejdsmiljø.

Indstillingen *Rapportér et problem* i Teams-meddelelser er som standard aktiveret i [Teams Administration](/microsoftteams/manage-teams-in-modern-portal), så brugere i din organisation kan sende upassende meddelelser til gennemsyn af korrekturlæsere af overholdelse af angivne standarder for politikken. Disse meddelelser understøttes af en standardsystempolitik, der understøtter rapportering af meddelelser i Teams kanaler, grupper og private chats.

![Rapport om overholdelse af kommunikation er et problem.](../media/communication-compliance-report-a-concern-full-menu.png)

Når en bruger sender en Teams chatmeddelelse til gennemsyn, kopieres meddelelsen til politikken for brugerrapporterede meddelelser. Rapporterede meddelelser forbliver først synlige for alle chatmedlemmer, og der er ikke nogen meddelelse til chatmedlemmerne eller indsenderen om, at en meddelelse er blevet rapporteret i kanal-, privat- eller gruppechats. En bruger kan ikke rapportere den samme meddelelse mere end én gang, og meddelelsen forbliver synlig for alle brugere, der er inkluderet i chatsessionen under korrekturprocessen for politikken. 

Under korrekturprocessen kan korrekturlæsere af overholdelse af angivne standarder udføre alle [standardafhjælpningshandlinger](/microsoft-365/compliance/communication-compliance-investigate-remediate#step-3-decide-on-a-remediation-action) i meddelelsen, herunder fjerne meddelelsen fra Teams chat. Afhængigt af hvordan meddelelserne afhjælpes, får afsenderen og modtagerne af meddelelsen vist forskellige [meddelelsesmeddelelser](/microsoftteams/communication-compliance#act-on-inappropriate-messages-in-microsoft-teams) i Teams chats efter gennemgangen.

![Politik for brugerrapporterede meddelelser om kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-user-reported-messages-policy.png)

Brugerrapporterede meddelelser fra Teams chats er de eneste meddelelser, der behandles af politikken for brugerrapporterede meddelelser, og kun de tildelte korrekturlæsere for politikken kan ændres. Alle andre politikegenskaber kan ikke redigeres. Når politikken oprettes, er de første korrekturlæsere, der er tildelt politikken, alle medlemmer af rollegruppen *Administratorer af kommunikationsoverholdelse* (hvis de udfyldes med mindst én bruger) eller alle medlemmer af organisationens *rollegruppe Global administrator* . Politikopretteren er en tilfældigt valgt bruger fra rollegruppen *Administratorer af kommunikationsoverholdelse* (hvis den udfyldes med mindst én bruger) eller en tilfældigt valgt bruger fra din organisations *rollegruppe Global administrator* .  

Administratorer skal straks tildele brugerdefinerede korrekturlæsere til denne politik efter behov for din organisation. Dette kan omfatte korrekturlæsere, f.eks. overholdelsesansvarlige, risikoansvarlige eller medlemmer af hr-afdelingen. Hvis du vil tilpasse korrekturlæserne for chatmeddelelser, der er sendt som brugerrapporterede meddelelser, skal du udføre følgende trin:

1. Log på [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/) ved hjælp af legitimationsoplysninger for en administratorkonto i din Microsoft 365 organisation.
2. Gå til **Kommunikation med overholdelse af angivne standarder på portalen for overholdelse af angivne standarder**.
3. Under fanen **Politik** skal du vælge politikken *Brugerrapporterede meddelelser* og vælge **Rediger**.
4. I ruden **Overvåg for brugerrapporterede meddelelser** skal du tildele validatorer til politikken. Korrekturlæsere skal have postkasser, der hostes på Exchange Online. Når validatorer føjes til en politik, modtager de automatisk en mail, der giver dem besked om tildelingen til politikken og indeholder links til oplysninger om korrekturprocessen.
5. Vælg **Gem**.

Hvis du vil deaktivere brugere fra at rapportere Teams meddelelser med *indstillingen Rapportér et problem*, skal du deaktivere indstillingen **Slutbrugerrapportering** i [Teams Administration](/microsoftteams/manage-teams-in-modern-portal). 

>[!IMPORTANT]
>Hvis du bruger PowerShell til at deaktivere indstillingen **Slutbrugerrapportering** i Teams Administration, skal du bruge [Microsoft Teams cmdlet'er modul version 4.2.0](/MicrosoftTeams/teams-powershell-release-notes) eller nyere.

## <a name="storage-limit-notification-preview"></a>Storage meddelelse om grænse (prøveversion)

Hver politik for overholdelse af angivne standarder for kommunikation har en lagergrænse på 100 GB eller 1 million meddelelser, alt efter hvad der nås først. Efterhånden som politikken nærmer sig disse grænser, sendes der automatisk meddelelsesmails til brugere, der er tildelt rollegrupperne *Kommunikationsoverholdelse* eller *Administrator af kommunikationsoverholdelse* . Meddelelser sendes, når lagerstørrelsen eller antallet af meddelelser når 80, 90 og 95 % af grænsen. Når politikgrænsen er nået, deaktiveres politikken automatisk, og politikken stopper behandlingen af meddelelser for beskeder.

>[!IMPORTANT]
>Hvis en politik deaktiveres, fordi du når lager- og meddelelsesgrænserne, skal du evaluere, hvordan du administrerer den deaktiverede politik. Hvis du sletter politikken, slettes alle meddelelser, tilknyttede vedhæftede filer og meddelelsesbeskeder permanent. Hvis du har brug for at vedligeholde disse elementer til fremtidig brug, skal du ikke slette den deaktiverede politik.

Hvis du vil administrere politikker, der nærmer sig lager- og meddelelsesgrænserne, kan du overveje at oprette en kopi af politikken for at opretholde dækningskontinuitet eller udføre følgende handlinger for at minimere den aktuelle politiks lagerstørrelse og antallet af meddelelser:

- Overvej at reducere antallet af brugere, der er tildelt politikken. Hvis du fjerner brugere fra politikken eller opretter forskellige politikker for forskellige grupper af brugere, kan det hjælpe med at bremse væksten i politikstørrelsen og det samlede antal meddelelser.
- Undersøg politikken for overdrevne falske positive beskeder. Overvej at føje undtagelser eller ændringer til politikbetingelserne for at ignorere almindelige falske positive beskeder.
- Hvis en politik har nået lager- eller meddelelsesgrænserne og er blevet deaktiveret, skal du oprette en kopi af politikken for fortsat at registrere og udføre handlinger for de samme betingelser og brugere.

## <a name="policy-settings"></a>Politikindstillinger

### <a name="users"></a>Brugere

Du kan vælge at vælge **Alle brugere** eller definere bestemte brugere i en politik for kommunikation med overholdelse af angivne standarder. Hvis du vælger **Alle brugere** , anvendes politikken på alle brugere og alle grupper, som alle brugere er inkluderet i som medlem. Når du definerer bestemte brugere, anvendes politikken på de definerede brugere, og de grupper, de definerede brugere er inkluderet i som et medlem.

### <a name="direction"></a>Retning

Som standard vises betingelsen **Retning er** , og den kan ikke fjernes. Indstillinger for kommunikationsretning i en politik vælges enkeltvist eller sammen:

- **Indgående**: Registrerer kommunikation, der sendes **til** overvågede brugere fra eksterne og interne afsendere, herunder andre overvågede brugere i politikken.
- **Udgående**: Registrerer kommunikation, der sendes **fra** overvågede brugere til eksterne og interne modtagere, herunder andre overvågede brugere i politikken.
- **Intern**: Registrerer kommunikation **mellem** overvågede brugere eller grupper i politikken.

### <a name="sensitive-information-types"></a>Typer af følsomme oplysninger

Du har mulighed for at inkludere følsomme informationstyper som en del af politikken for overholdelse af angivne standarder for kommunikation. Følsomme oplysningstyper er enten foruddefinerede eller brugerdefinerede datatyper, der kan hjælpe med at identificere og beskytte kreditkortnumre, bankkontonumre, pasnumre og meget mere. Som en del af [Få mere at vide om Forebyggelse af datatab i Microsoft Purview](dlp-learn-about-dlp.md) kan konfigurationen af følsomme oplysninger bruge mønstre, tegn nærhed, tillidsniveauer og endda brugerdefinerede datatyper til at identificere og markere indhold, der kan være følsomt. Standardtyperne for følsomme oplysninger er:

- Finansielle
- Medicinsk og sundhed
- Beskyttelse af personlige oplysninger
- Brugerdefineret oplysningstype

> [!IMPORTANT]
> SIT'er har to forskellige måder at definere de maksimale antal parametre for entydige forekomster på. Hvis du vil vide mere, skal du se [Antal understøttede værdier for SIT.](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit)

Hvis du vil vide mere om oplysninger om følsomme oplysninger og de mønstre, der er inkluderet i standardtyperne, skal du se [Objektdefinitioner for følsomme oplysninger](sensitive-information-type-entity-definitions.md).

### <a name="custom-keyword-dictionaries"></a>Brugerordbøger med nøgleord

Konfigurer brugerordbøger med nøgleord (eller leksikoner) for at give enkel administration af nøgleord, der er specifikke for din organisation eller branche. Nøgleordsordbøger understøtter op til 100 KB ord (efter komprimering) i ordbogen og understøtter ethvert sprog. Lejergrænsen er også 100 KB efter komprimering. Hvis det er nødvendigt, kan du anvende flere brugerdefinerede nøgleordsordbøger på en enkelt politik eller have en enkelt nøgleordsordbog pr. politik. Disse ordbøger tildeles i en politik for overholdelse af angivne standarder for kommunikation og kan hentes fra en fil (f.eks. en .csv eller .txt liste) eller fra en liste, du kan [importere i Overholdelsescenter](create-a-keyword-dictionary.md). Brug brugerdefinerede ordbøger, når du har brug for at understøtte begreber eller sprog, der er specifikke for din organisation og politikker.

### <a name="classifiers"></a>Klassificeringer

Indbyggede og globale klassificeringer scanner sendte eller modtagne meddelelser på tværs af alle kommunikationskanaler i din organisation for forskellige typer problemer med overholdelse af angivne standarder. Klassificeringer bruger en kombination af kunstig intelligens og nøgleord til at identificere sprog i meddelelser, der kan være i strid med politikker til bekæmpelse af chikane. Indbyggede klassificeringer understøtter i øjeblikket identifikation af nøgleord på flere sprog:

- Kinesisk (forenklet)
- English
- French
- German
- Italian
- Japanese
- Portugisisk
- Spanish

Indbyggede klassificeringer, der kan oplæres i kommunikation, og globale klassificeringer scanner kommunikation for vilkår, billeder og synspunkter for følgende typer sprog og indhold:

- **Voksne billeder**: Scanner efter billeder, der er seksuelt eksplicitte i naturen.
- **Diskrimination**: Scanner efter eksplicit diskriminerende sprog og er særligt følsom over for diskriminerende sprog mod de afrikanske amerikanske/sorte samfund sammenlignet med andre samfund.
- **Gory-billeder**: Scanner efter billeder, der viser vold og gore.
- **Bandeord**: Scanner efter profane udtryk, der gør de fleste til grin.
- **Racy-billeder**: Scanner efter billeder, der er seksuelt suggestive i naturen, men som indeholder mindre eksplicit indhold end billeder, der anses for Voksne.
- **Målrettet chikane**: Scans for stødende adfærd rettet mod personer vedrørende race, farve, religion, national oprindelse.
- **Trussel**: Scanner efter trusler for at begå vold eller fysisk skade på en person eller ejendom.

Billedklassificeringerne *Voksen*, *Racy* og *Gory* scanner filer i formaterne .jpeg, .png, .gif og .bmp. Størrelsen på billedfiler skal være mindre end 4 MB (megabyte), og billedernes dimensioner skal være større end 50 x 50 pixel og større end 50 KB, for at billedet kan kvalificeres til evaluering. Billedidentifikation understøttes for Exchange Online mails og Microsoft Teams kanaler og chats.

De indbyggede og globale klassificeringer giver ikke en udtømmende liste over begreber eller billeder på tværs af disse områder. Desuden ændres sprog- og kulturelle standarder hele tiden, og i lyset af disse realiteter forbeholder Microsoft sig ret til at opdatere klassificeringer efter eget skøn. Selvom klassificeringer kan hjælpe din organisation med at overvåge disse områder, er klassificeringer ikke beregnet til at levere din organisations eneste måde at overvåge eller håndtere sådanne sprog eller billeder på. Din organisation, ikke Microsoft, forbliver ansvarlig for alle beslutninger vedrørende overvågning, scanning og blokering af sprog og billeder i disse områder, herunder overholdelse af lokale love om beskyttelse af personlige oplysninger og andre gældende love. Microsoft opfordrer til at rådføre sig med juridisk rådgivning før udrulning og brug.

> [!NOTE]
> Politikker, der bruger klassificeringer, undersøger og evaluerer meddelelser med et ordantal på seks eller flere. Meddelelser, der indeholder mindre end seks ord, evalueres ikke i politikker ved hjælp af klassificeringer. For at identificere og reagere på kortere meddelelser, der indeholder upassende indhold, anbefaler vi, at du inkluderer en brugerdefineret nøgleordsordbog til overvågning af politikker for kommunikation med overholdelse af angivne standarder for denne type indhold.

Du kan finde oplysninger om klassificeringer, der kan oplæres, under [Introduktion til klassificeringer, der kan oplæres](classifier-get-started-with.md).

### <a name="optical-character-recognition-ocr"></a>Optisk tegngenkendelse (OCR)

Konfigurer indbyggede eller brugerdefinerede politikker for overholdelse af angivne standarder for kommunikation for at scanne og identificere trykt eller håndskrevet tekst fra billeder, der kan være upassende i din organisation. Integreret [understøttelse af Azure Cognitive Services og optisk scanning](/azure/cognitive-services/computer-vision/overview-ocr) til identificering af tekst i billeder hjælper analytikere og efterforskere med at registrere og reagere på tilfælde, hvor upassende adfærd kan gå glip af i kommunikation, der primært ikke er tekstuel.

Du kan aktivere optisk tegngenkendelse (OCR) i nye politikker fra skabeloner, brugerdefinerede politikker eller opdatere eksisterende politikker for at udvide understøttelsen af behandling af integrerede billeder og vedhæftede filer. Når funktionen er aktiveret i en politik, der er oprettet ud fra en politikskabelon, understøttes automatisk scanning for integrerede eller vedhæftede billeder i mails og Microsoft Teams chatbeskeder. OCR-scanning understøttes ikke for billeder, der er integreret i dokumentfiler. I forbindelse med brugerdefinerede politikker skal en eller flere betingede indstillinger, der er knyttet til nøgleord, indbyggede klassificeringer eller følsomme infotyper, konfigureres i politikken for at muliggøre valg af OCR-scanning.

Billeder fra 50 KB til 4 MB i følgende billedformater scannes og behandles:

- .jpg/.jpeg (fælles fotoekspertgruppe)
- .png (bærbar netværksgrafik)
- .bmp (bitmap)
- .tiff (tag image file format)
- .pdf (bærbart dokumentformat)

> [!NOTE]
> Scanning og udtrækning af integrerede og vedhæftede .pdf billeder understøttes i øjeblikket kun for mails.

Når du gennemser ventende beskeder for politikker, hvor OCR er aktiveret, vises de billeder, der er identificeret og matchet med politikbetingelser, som underordnede elementer for tilknyttede beskeder. Du kan få vist det oprindelige billede for at evaluere den identificerede tekst i kontekst med den oprindelige meddelelse. Det kan tage op til 48 timer, før registrerede billeder er tilgængelige med beskeder.

### <a name="conditional-settings"></a>Betingede indstillinger
<a name="ConditionalSettings"> </a>

De betingelser, du vælger for politikken, gælder for kommunikation fra både mailkilder og tredjepartskilder i din organisation (f.eks. fra Instant Bloomberg).

I følgende tabel forklares mere om hver betingelse.

|**Betingelse**|**Sådan bruges denne betingelse**|
|:-----|:-----|
| **Indhold stemmer overens med en af disse klassificeringer** | Anvend på politikken, når klassificeringer medtages eller udelades i en meddelelse. Nogle klassificeringer er foruddefinerede i din lejer, og brugerdefinerede klassificeringer skal konfigureres separat, før de er tilgængelige for denne betingelse. Der kan kun defineres én klassificering som en betingelse i en politik. Du kan finde flere oplysninger om konfiguration af klassificeringer under [Få mere at vide om klassificeringer, der kan oplæres (prøveversion).](classifier-learn-about.md) |
| **Indhold indeholder en af disse følsomme infotyper** | Anvend på politikken, når følsomme oplysningstyper medtages eller udelades i en meddelelse. Nogle klassificeringer er foruddefinerede i din lejer, og brugerdefinerede klassificeringer kan konfigureres separat eller som en del af betingelsestildelingsprocessen. Hver type følsomme oplysninger, du vælger, anvendes separat, og kun én af disse følsomme oplysningstyper skal gælde, for at politikken kan anvendes på meddelelsen. Du kan finde flere oplysninger om brugerdefinerede typer følsomme oplysninger under [Få mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md). |
| **Der modtages en meddelelse fra et af disse domæner**  <br><br> **Meddelelsen modtages ikke fra nogen af disse domæner** | Anvend politikken på at inkludere eller udelade bestemte domæner eller mailadresser i modtagne meddelelser. Angiv hvert domæne eller hver mailadresse, og adskil flere domæner eller mailadresser med et komma. Hvert domæne eller hver mailadresse, der angives, anvendes separat. Der må kun gælde ét domæne eller én mailadresse, for at politikken kan anvendes på meddelelsen. <br><br> Hvis du vil scanne alle mails fra et bestemt domæne, men vil udelade meddelelser, der ikke skal gennemses (nyhedsbreve, meddelelser osv.), skal du konfigurere, at der **ikke modtages en meddelelse fra nogen af disse domæner-betingelse,** der udelukker mailadressen (f.eks. "newsletter@contoso.com"). |
| **Meddelelsen sendes til et af disse domæner**  <br><br> **Meddelelsen sendes ikke til nogen af disse domæner** | Anvend politikken til at inkludere eller udelade bestemte domæner i sendte meddelelser. Angiv hvert domæne, og adskil flere domæner med et komma. Hvert domæne anvendes separat, og der må kun gælde ét domæne, for at politikken kan anvendes på meddelelsen. <br><br> Hvis du vil udelade alle mails, der er sendt til to specifikke domæner, skal du konfigurere, **at Meddelelsen ikke sendes til nogen af disse domæner** med de to domæner (f.eks. 'contoso.com,wingtiptoys.com'). |
| **Meddelelsen er klassificeret med et af disse navne**  <br><br> **Meddelelsen er ikke klassificeret med nogen af disse mærkater** | At anvende politikken, når visse opbevaringsmærkater medtages eller udelades i en meddelelse. Opbevaringsmærkater skal konfigureres separat, og konfigurerede mærkater vælges som en del af denne betingelse. Hver etiket, du vælger, anvendes separat (kun ét af disse mærkater skal gælde, for at politikken kan anvendes på meddelelsen). Du kan finde flere oplysninger om opbevaringsmærkater under [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md).|
| **Meddelelsen indeholder et af disse ord**  <br><br> **Meddelelsen indeholder ingen af disse ord** | Hvis du vil anvende politikken, når bestemte ord eller udtryk medtages eller udelades i en meddelelse, skal du angive hvert ord adskilt med et komma. I forbindelse med udtryk med to ord eller mere skal du bruge anførselstegn omkring udtrykket. Hvert ord eller udtryk, du angiver, anvendes separat (kun ét ord skal gælde, for at politikken kan anvendes på meddelelsen). Du kan finde flere oplysninger om indtastning af ord eller udtryk i næste afsnit [Matchning af ord og udtryk til mails eller vedhæftede filer](communication-compliance-policies.md#Matchwords).|
| **Den vedhæftede fil indeholder et af disse ord**  <br><br> **Den vedhæftede fil indeholder ingen af disse ord** | Hvis du vil anvende politikken, når bestemte ord eller udtryk medtages eller udelades i en vedhæftet fil i en meddelelse (f.eks. et Word-dokument), skal du skrive hvert ord adskilt med et komma. I forbindelse med udtryk med to ord eller mere skal du bruge anførselstegn omkring udtrykket. Hvert ord eller udtryk, du angiver, anvendes separat (kun ét ord skal gælde, for at politikken kan anvendes på den vedhæftede fil). Du kan finde flere oplysninger om indtastning af ord eller udtryk i næste afsnit [Matchning af ord og udtryk til mails eller vedhæftede filer](communication-compliance-policies.md#Matchwords).|
| **Vedhæftet fil er en af disse filtyper**  <br><br> **Vedhæftet fil er ingen af disse filtyper** | Hvis du vil overvåge kommunikation, der omfatter eller udelukker bestemte typer vedhæftede filer, skal du angive filtypenavnene (f.eks. .exe eller .pdf). Hvis du vil medtage eller udelade flere filtypenavne, skal du angive filtyper adskilt af et komma (f.eks *..exe,.pdf,.zip*). Der må kun være én filtypenavn for vedhæftede filer, der svarer til den politik, der skal anvendes.|
| **Meddelelsesstørrelsen er større end**  <br><br> **Meddelelsesstørrelsen er ikke større end** | Hvis du vil gennemse meddelelser baseret på en bestemt størrelse, skal du bruge disse betingelser til at angive den maksimale eller mindste størrelse, en meddelelse kan være, før den kan gennemses. Hvis du f.eks. angiver **, at Meddelelsesstørrelse er større end** \> **1,0 MB**, kan alle meddelelser, der er 1,01 MB og større, gennemses. Du kan vælge byte, kilobyte, megabyte eller gigabyte til denne betingelse.|
| **Den vedhæftede fil er større end**  <br><br> **Den vedhæftede fil er ikke større end** | Hvis du vil gennemse meddelelser baseret på størrelsen på deres vedhæftede filer, skal du angive den maksimale eller mindste størrelse, en vedhæftet fil kan være, før meddelelsen og dens vedhæftede filer kan gennemses. Hvis du f.eks. angiver, at **Vedhæftet fil er større end** \> **2,0 MB**, kan alle meddelelser med vedhæftede filer på 2,01 MB og derover gennemses. Du kan vælge byte, kilobyte, megabyte eller gigabyte til denne betingelse.|

#### <a name="matching-words-and-phrases-to-emails-or-attachments"></a>Matchende ord og udtryk til mails eller vedhæftede filer
<a name="Matchwords"> </a>

Hvert ord, du indtaster og adskiller med et komma, anvendes separat (kun ét ord skal gælde, for at politikbetingelsen kan anvendes på mailen eller den vedhæftede fil). Lad os f.eks. bruge betingelsen **Meddelelse indeholder et af disse ord** med nøgleordene "banker", "fortroligt" og "insiderhandel" adskilt af et komma (bankmand, fortroligt,"insiderhandel"). Politikken gælder for alle meddelelser, der indeholder ordet "bankmand", "fortroligt" eller udtrykket "insiderhandel". Kun ét af disse ord eller udtryk må forekomme, for at denne politikbetingelse kan anvendes. Ordene i meddelelsen eller den vedhæftede fil skal svare nøjagtigt til det, du angiver.

> [!IMPORTANT]
>
> Når du importerer en brugerordbogsfil, skal hvert ord eller udtryk adskilles med vognretur og på en separat linje. Eksempel:
>
> *Bankmand* <br>
> *Fortrolige* <br>
> *insiderhandel*

Hvis du vil scanne både mails og vedhæftede filer for de samme nøgleord, skal du oprette en [brugerordbog med nøgleord](create-a-keyword-dictionary.md) for de ord, du vil scanne i meddelelser. Denne politikkonfiguration identificerer definerede nøgleord, der enten vises i mailen **eller** i den vedhæftede fil. Hvis du bruger standardindstillingerne for betinget politik (*Meddelelse indeholder et af disse ord* , og *vedhæftet fil indeholder et af disse ord*) til at identificere ord i meddelelser og i vedhæftede filer, kræver det, at vilkårene er til **stede både i** meddelelsen og den vedhæftede fil.

#### <a name="enter-multiple-conditions"></a>Angiv flere betingelser

Hvis du angiver flere betingelser, bruger Microsoft 365 alle betingelserne sammen til at bestemme, hvornår politikken for kommunikation med overholdelse af angivne standarder skal anvendes på kommunikationselementer. Når du konfigurerer flere betingelser, skal alle betingelser være opfyldt, for at politikken kan anvendes, medmindre du angiver en undtagelse. Du skal f.eks. bruge en politik, der gælder, hvis en meddelelse indeholder ordet "handel", og er større end 2 MB. Men hvis meddelelsen også indeholder ordene "Godkendt af Contoso financial", bør politikken ikke gælde. I dette eksempel defineres de tre betingelser på følgende måde:

- **Meddelelsen indeholder et af disse ord** med nøgleordet "handel"
- **Meddelelsesstørrelsen er større end** med værdien 2 MB
- **Meddelelsen indeholder ingen af disse ord** med nøgleordene "Godkendt af Contoso financial team"

### <a name="review-percentage"></a>Procent for gennemsyn

Hvis du vil reducere mængden af indhold, der skal gennemses, kan du angive en procentdel af al kommunikation, der er omfattet af en politik for kommunikation med overholdelse af angivne standarder. Et tilfældigt indholdseksempel i realtid vælges ud fra den samlede procentdel af indhold, der opfylder de valgte politikbetingelser. Hvis korrekturlæsere skal gennemse alle elementer, kan du konfigurere **100 %** i en politik for overholdelse af angivne standarder for kommunikation.

## <a name="alert-policies"></a>Underretningspolitikker

Når du har konfigureret en politik, oprettes der automatisk en tilsvarende beskedpolitik, og der genereres beskeder for meddelelser, der opfylder de betingelser, der er defineret i politikken. Det kan tage op til 24 timer, efter at en politik er begyndt at modtage beskeder fra aktivitetsindikatorer. Som standard tildeles alle politikforekomster af beskedudløsere en alvorsgrad på mellem i den tilknyttede beskedpolitik. Der genereres beskeder for en politik for kommunikation med overholdelse af angivne standarder, når grænseniveauet for sammenlægningsudløseren er nået i den tilknyttede beskedpolitik. Der sendes en enkelt mail hver 24. time for alle beskeder, uanset antallet af individuelle meddelelser, der stemmer overens med politikbetingelserne. Contoso har f.eks. aktiveret en upassende indholdspolitik, og for den 1. januar var der 100 politikforekomster, der genererede seks beskeder. Der sendes en enkelt mailmeddelelse for de seks beskeder i slutningen af den 1. januar.

I forbindelse med politikker for kommunikation med overholdelse af regler og standarder konfigureres følgende værdier for beskedpolitik som standard:

|**Udløser for beskedpolitik**|**Standardværdien**|
|:-----|:-----|
| Sammenlægning | Enkel aggregering |
| Tærskel | Standard: 4 aktiviteter <br> Minimum: 3 aktiviteter <br> Maksimum: 2.147.483.647 aktiviteter |
| Vinduet | Standard: 60 minutter <br> Minimum: 60 minutter <br> Maksimum: 10.000 minutter |

> [!NOTE]
> Tærskel for beskedpolitik for udløserindstillinger for aktiviteter understøtter en minimumværdi på 3 eller højere for politikker for kommunikation med overholdelse af angivne standarder.

Du kan ændre standardindstillingerne for udløsere for antallet af aktiviteter, perioden for aktiviteterne og for bestemte brugere i beskedpolitikker på siden **Beskedpolitikker** på Microsoft Purview-overholdelsesportalen.

### <a name="change-the-severity-level-for-an-alert-policy"></a>Skift alvorsgradsniveauet for en beskedpolitik

Hvis du vil ændre det alvorsgradsniveau, der er tildelt i en beskedpolitik for en bestemt politik for overholdelse af angivne standarder for kommunikation, skal du udføre følgende trin:

1. Log på [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din Microsoft 365 organisation.

2. Gå til **Politikker** på Microsoft Purview-overholdelsesportalen.

3. Vælg **Office 365 besked** på siden **Politikker** for at åbne siden **Politikker for beskeder**.

4. Markér afkrydsningsfeltet for den politik for kommunikation med overholdelse af regler og standarder, du vil opdatere, og vælg derefter **Rediger politik**.

5. Under fanen **Beskrivelse** skal du vælge rullelisten **Alvorsgrad** for at konfigurere beskedniveauet for politikken.

6. Vælg **Gem** for at anvende det nye alvorsgradsniveau på politikken.

7. Vælg **Luk** for at afslutte siden med oplysninger om beskedpolitik.
