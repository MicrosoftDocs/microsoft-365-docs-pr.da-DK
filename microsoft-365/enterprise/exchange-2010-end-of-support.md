---
title: Exchange end of support i 2010
ms.author: dstrome
author: dstrome
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
f1.keywords:
- NOCSH
description: Exchange supporten i 2010 er slut. Brug denne planlægningsoversigt til at forberede opgraderingen til Exchange Online eller en nyere version Exchange Server lokalt miljø.
ms.openlocfilehash: e49bf68ce2fb9b441ecd40ae4bb89ad88ea568c8
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2021
ms.locfileid: "63591607"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Exchange end of support i 2010

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Exchange Server 2010 ophør af supporten d. **13. oktober 2020**. Hvis du ikke allerede er begyndt at bruge overførslen fra Exchange 2010 til Microsoft 365, Office 365 eller Exchange 2016, skal du begynde planlægningen nu.

## <a name="what-does-end-of-support-mean"></a>Hvad *betyder ophør af support* ?

De fleste Microsoft-produkter har en supportlivscyklus, hvor de får nye funktioner, fejlrettelser, sikkerhedsopdateringer osv. Denne livscyklus varer typisk 10 år fra produktets første udgivelse. Slutningen af denne livscyklus kaldes for ophør af support for produktet. Da Exchange 2010 ikke længere understøttet den 13. oktober 2020, yder Microsoft ikke længere:

- Teknisk support til problemer, der kan opstå.
- Fejlrettelser af problemer, der kan påvirke stabiliteten og anvendeligheden af serveren.
- Sikkerhedsopdateringer til sårbarheder, der kan gøre serveren sårbar over for sikkerhedsbrister.
- Tidszoneopdateringer.

Installationen af Exchange 2010 vil fortsætte efter denne dato. På grund af ændringerne, der er angivet ovenfor, anbefaler vi imidlertid på det kraftigste, at du overfører Exchange 2010 så tidligt som muligt.

Du kan finde flere oplysninger om, at support snart er slut, under Ressourcer, der kan hjælpe dig med at [opgradere fra Office 2010-servere og -klienter](upgrade-from-office-2010-servers-and-products.md).

## <a name="what-are-my-options"></a>Hvilke muligheder har jeg?

Det er et godt tidspunkt at udforske dine muligheder og forberede en overførselsplan. Du kan:

- Overfør fuldt Microsoft 365. Overfør postkasser ved hjælp af komplet, minimal hybrid eller fuld hybridoverførsel. Fjern derefter lokale servere Exchange og Active Directory.
- Overfør Exchange 2010-servere Exchange 2016 på dine lokale servere.

> [!IMPORTANT]
> Hvis din organisation vælger at overføre postkasser til Microsoft 365 men planlægger at beholde DirSync eller Azure AD Forbind på plads for at fortsætte med at administrere brugerkonti fra Active Directory i det lokale miljø, skal du have mindst én Microsoft Exchange-server lokalt. Hvis du fjerner alle Exchange-servere, kan du ikke foretage ændringer til Exchange-modtagere i Exchange Online, fordi kilden til autoritet forbliver i dit lokale Active Directory. Der skal du foretage ændringer. I dette scenarie har du følgende muligheder:
>
>- *Anbefalet:* Hvis du har overført dine postkasser til Microsoft 365 og opgraderet dine servere senest d. 13. oktober 2020, skal du bruge Exchange 2010 til at oprette forbindelse til Microsoft 365 og overføre postkasser. Dernæst skal du Exchange 2010 til Exchange 2016 og afvikle eventuelle resterende Exchange 2010-servere.
>- Hvis du ikke fuldførte postkasseoverflytningen og serveropgraderingen i det lokale miljø senest d. 13. oktober 2020, skal du opgradere dine lokale Exchange 2010-servere til Exchange 2016 først. Brug derefter Exchange 2016 til at oprette forbindelse Microsoft 365 og overføre postkasser.

> [!NOTE]
> Det er lidt mere kompliceret, men du kan også overføre postkasser til Microsoft 365, mens du overfører dine lokale Exchange 2010-servere til Exchange 2016.

Her er de tre stier, du kan gå for at undgå ophør af support til Exchange Server 2010.

![Exchange Server 2010-opgraderingsstier.](../media/exchange-2010-end-of-support/exchange-2010-end-of-support-options.png)

I de følgende afsnit gennemgås hver indstilling mere detaljeret.

## <a name="migrate-to-microsoft-365"></a>Overfør til Microsoft 365

Den nemmeste og mest enkle Microsoft 365 er at Exchange din mail Exchange 2010-installationen. Med en overførsel til Microsoft 365, kan du foretage et enkelt hop fra gammel teknologi til aktuelle funktioner, herunder:

- Overholdelsesegenskaber som f.eks Opbevaringspolitikker, In-Place retslig tilbageholdelse og retslig tilbageholdelse, direkte eDiscovery og meget mere.
- Microsoft Teams.
- Power BI.
- Fokuseret indbakke.
- MyAnalytics.

Microsoft 365 får også nye funktioner og oplevelser først, så din organisation kan begynde at bruge dem med det samme. Du behøver heller ikke at bekymre dig om at:

- Købe og vedligeholde hardware.
- Betaling for varme og afkøling af dine servere.
- Hold dig opdateret om rettelser af sikkerhed, produkter og tidszoner.
- Vedligeholdelse af lagerplads og software for at understøtte overholdelseskrav.
- Opgradering til en ny version af Exchange. Du har altid den nyeste version af Exchange i Microsoft 365.

### <a name="how-should-i-migrate-to-microsoft-365"></a>Hvordan skal jeg overføre til Microsoft 365?

Afhængigt af din organisation har du et par muligheder for at komme til Microsoft 365. Først skal du overveje et par ting, f.eks.:

- Antallet af pladser eller postkasser, du skal flytte.
- Hvor længe du ønsker, at overførslen skal vare.
- Uanset om du har brug for problemfri integration mellem din lokale installation og Microsoft 365 under overførslen.

Denne tabel viser dine overførselsmuligheder og de vigtigste faktorer, der bestemmer, hvilken metode du skal bruge.

<br>

****

|Overførselsmulighed|Organisationens størrelse|Varighed|
|---|---|---|
|Cutover migration|Færre end 150 pladser|En uge eller mindre|
|Minimal hybridoverførsel|Færre end 150 pladser|Et par uger eller mindre|
|Fuld hybridoverførsel|Mere end 150 pladser|Et par uger eller mere|
|

De følgende afsnit giver dig et overblik over disse metoder. Få mere at vide under [Beslut dig for en overførselsti](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27).

### <a name="cutover-migration"></a>Cutover migration

I en migrering overfører du alle dine postkasser, distributionsgrupper, kontakter osv., for at Office 365 på en angivet dato og et angivet klokkeslæt. Når du er færdig, lukker du dine lokale servere og Exchange udelukkende bruge Microsoft 365 serverne.

Den gratis migrering er god til små organisationer, der ikke har mange postkasser, ønsker at få hurtig adgang til Microsoft 365 og ikke ønsker at håndtere kompleksiteten ved de andre metoder. Men det bør gennemføres om en uge eller mindre. Og det kræver, at brugerne omkonfigurere deres Outlook profiler. Den gratis migrering kan overføre op til 2.000 postkasser, men vi anbefaler, at du bruger den maksimalt 150. Hvis du forsøger at overføre flere, kan du løbe tør for tid til at overføre alle postkasserne før din deadline, og dit it-supportpersonale kan blive overvældet af anmodninger om at hjælpe brugerne med at konfigurere Outlook.

Her er nogle ting, du skal overveje om en migrering:

- Microsoft 365 skal oprette forbindelse til dine Exchange 2010-servere ved hjælp af Outlook hvor som helst via TCP-port 443.
- Alle lokale postkasser flyttes til Microsoft 365.
- Du skal bruge en lokal administratorkonto, der har læseadgang til dine brugeres postkasser.
- Den Exchange 2010-accepterede domæner, du vil bruge i Microsoft 365, skal tilføjes som bekræftede domæner i tjenesten.
- Mellem hvornår du starter overførslen, og hvor du går i gang med fuldførelsesfasen Microsoft 365 med jævne mellemrum Microsoft 365-postkasserne og de lokale postkasser. Dette giver dig mulighed for at fuldføre overførslen uden at bekymre dig om mails, der efterlades i dine lokale postkasser.
- Brugerne modtager nye midlertidige adgangskoder til deres Microsoft 365 konto. De skal ændre dem, når de logger på deres postkasser for første gang.
- Du skal bruge en Microsoft 365, der omfatter Exchange Online for hver brugerpostkasse, du overfører.
- Brugerne skal konfigurere en ny profil til Outlook på hver af deres enheder og hente deres mail igen. Mængden af mails, Outlook downloadet, kan variere. Få mere at vide under [Arbejd offline i Outlook](https://support.microsoft.com/office/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

Du kan få mere at vide om en cutover-migrering under:

- [Hvad du bør vide om en migrering af en mail](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration)
- [Udfør en cutover-migrering af mail for at Office 365](/Exchange/mailbox-migration/cutover-migration-to-office-365)

### <a name="minimal-hybrid-migration"></a>Minimal hybridoverførsel

I en minimal hybrid- eller hurtig migrering flytter du et par hundrede postkasser til Microsoft 365 inden for et par uger. Denne metode understøtter ikke avancerede funktioner til hybridoverførsel som f.eks. delte oplysninger om ledig/optaget kalender.

Minimal hybridoverførsel er god for organisationer, der har brug for mere tid til at overføre deres postkasser til Microsoft 365, men stadig planlægger at fuldføre overførslen inden for et par uger. Du får nogle af fordelene ved den mere avancerede *fuld hybrid-migrering* uden den store kompleksitet. Du kan styre, hvor mange og hvilke postkasser der skal overføres på et givet tidspunkt. Microsoft 365 postkasser oprettes med brugernavne og adgangskoder for de lokale konti. Og i modsætning til en uoverenskårne migrering behøver brugerne ikke at genskabe deres Outlook profiler.

Her er nogle ting, du skal overveje vedrørende minimal hybridoverførsel:

- Du skal udføre en enkelttidssynkronisering mellem dine lokale Active Directory-servere og Microsoft 365.
- Brugerne vil kunne logge på deres postkasse Microsoft 365 med samme brugernavn og adgangskode som før deres postkasse.
- Du skal bruge en Microsoft 365 licens, der omfatter Exchange Online for hver brugerpostkasse, du overfører.
- Brugere behøver ikke at konfigurere en ny profil Outlook på de fleste af deres enheder, selvom nogle ældre Android-telefoner muligvis skal bruge en ny profil. Brugerne behøver ikke at downloade deres mail igen.

Få mere at vide under [Brug Minimal hybrid til hurtigt at overføre Exchange postkasser til Office 365](/Exchange/mailbox-migration/use-minimal-hybrid-to-quickly-migrate).

### <a name="full-hybrid"></a>Fuld hybrid

I en fuld hybridoverførsel har du mange hundredvis, op til titusindvis af postkasser, og du flytter nogle eller alle til Microsoft 365. Da disse migrering typisk er langsigtede, gør hybridoverførsel det muligt at:

- Vis lokale brugere oplysninger om ledig/optaget-kalender for brugere i Microsoft 365 og omvendt.
- Se en samlet global adresseliste, der indeholder modtagere både lokalt og Microsoft 365.
- Få vist Outlook egenskaber for modtagere for alle brugere, uanset om de er lokale eller Microsoft 365.
- Sikre mailkommunikation mellem lokale servere og Exchange Office 365 ved hjælp af TLS og certifikater.
- Behandle meddelelser, der sendes mellem lokale servere Exchange og Microsoft 365 som interne, så de kan:
  - Korrekt evalueres og behandles af transport- og overholdelsesagenter målrettet mod interne meddelelser.
  - Omgå antispamfiltre.

Fulde hybridoverførsel er bedst til organisationer, der forventer at forblive i en hybridkonfiguration i mange måneder eller mere. Du får funktionerne angivet tidligere i dette afsnit samt katalogsynkronisering, bedre integrerede overholdelsesfunktioner og muligheden for at flytte postkasser til og fra Microsoft 365 ved hjælp af onlinepostkasse flytter. Microsoft 365 bliver en udvidelse af din lokale organisation.

Ting du bør overveje om fuld hybridoverførsel:

- De er ikke egnet til alle organisationer. På grund af kompleksiteten ved fulde hybrid-migrering, ser organisationer med mindre end et par hundrede postkasser typisk ikke fordele, der berettiger den pågældende indsats og de involverede omkostninger. I sådanne tilfælde anbefaler vi, at du overvejer at bruge cutover eller minimal hybridoverførsel i stedet.
- Du skal konfigurere katalogsynkronisering ved hjælp Azure Active Directory (Azure AD) Forbind mellem dine lokale Active Directory-servere og Microsoft 365.
- Brugerne vil kunne logge på deres Microsoft 365-postkasse med samme brugernavn og adgangskode, de bruger, når de logger på det lokale netværk. (Denne funktion kræver Azure AD-Forbind adgangskodesynkronisering og/eller Active Directory Federation Services).
- Du skal bruge Microsoft 365 licens, der omfatter Exchange Online for hver brugerpostkasse, du overfører.
- Brugere behøver ikke at konfigurere en ny profil Outlook på de fleste af deres enheder, selvom nogle ældre Android-telefoner muligvis skal bruge en ny profil. Brugerne behøver ikke at downloade deres mail igen.

> [!IMPORTANT]
> Hvis din organisation vælger at overføre postkasser til Microsoft 365 men planlægger at beholde DirSync eller Azure AD Forbind på plads for at fortsætte med at administrere brugerkonti fra Active Directory i det lokale miljø, skal du have mindst én Exchange-server lokalt. Hvis alle Exchange-servere fjernes, kan du ikke foretage ændringer for Exchange modtagere i Exchange Online. Dette skyldes, at kilden til autoritet forbliver i dit lokale Active Directory, og ændringerne skal foretages der.

Hvis en fuld hybridoverførsel lyder som den rigtige for dig, kan du finde følgende nyttige ressourcer:

- [Exchange installationsassistent](/exchange/exchange-deployment-assistant)
- [Exchange Server hybridinstallationer](/exchange/exchange-hybrid)
- [Guiden Hybridkonfiguration](/exchange/hybrid-configuration-wizard)
- [Ofte stillede spørgsmål til guiden Hybridkonfiguration](/exchange/hybrid-configuration-wizard-faqs)
- [Forudsætninger for hybridinstallation](/exchange/hybrid-deployment-prerequisites)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Opgrader til en nyere version Exchange Server lokal version

Vi er stærkt overbeviste om, at du får den bedste værdi og brugeroplevelse ved at overføre fuldt ud Microsoft 365. Men vi forstår, at nogle organisationer har brug for at bevare Exchange lokale servere. Dette kan skyldes lovmæssige krav for at garantere, at data ikke gemmes i et fremmed datacenter, fordi du har unikke indstillinger eller krav, der ikke kan opfyldes i skyen, eller fordi du skal Exchange til at administrere postkasser i skyen, fordi du stadig bruger Active Directory lokalt. Hvis du beholder Exchange lokalt, skal du under alle omstændigheder sikre dig, at dit Exchange 2010-miljø opgraderes til mindst Exchange 2013 eller Exchange 2016.

For at få den bedste oplevelse anbefaler vi, at du opgraderer dit resterende lokale miljø til Exchange 2016. Du behøver ikke at installere Exchange Server 2013, hvis du vil gå direkte fra Exchange Server 2010 Exchange Server 2016.

Exchange 2016 indeholder alle funktionerne fra tidligere versioner af Exchange. Den passer bedst til den oplevelse, der er tilgængelig med Microsoft 365, selvom visse funktioner kun er tilgængelige i Microsoft 365. Se blot nogle af de ting, du har manglet:

<br>

****

|Exchange udgivelse|Funktioner|
|---|---|
|**Exchange 2013**|Forenklet arkitektur reducerer antallet af serverroller til tre (postkasse, klientadgang, Edge-transport)|
||Politikker til forebyggelse af datatab (DLP), der hjælper med at beskytte mod lækage af følsomme oplysninger|
||Forbedret Outlook Web App oplevelse|
|**Exchange 2016**|*Funktioner fra Exchange 2013 og ...*|
||Yderligere forenklede serverroller kun til postkasse og Edge-transport|
||Forbedret DLP samt integration med SharePoint|
||Forbedret databaserobusthed|
||Online dokumentsamarbejde|
|

<br>

****

|Overvejelse|Flere oplysninger|
|---|---|
|Slutdato for support|Ligesom Exchange 2010 har hver version Exchange sin egen slutdato for support: <p> Exchange 2013 – april 2023 <p> Exchange 2016 – oktober 2025 <p> Jo tidligere slutdatoen for support, jo tidligere skal du udføre endnu en overførsel. April 2023 er meget tættere på, end du tror!|
|Overførselssti til Exchange 2013 eller 2016|Overførselsstien fra Exchange 2010 til en nyere version er den samme, uanset om du Exchange 2013 eller Exchange 2016: <p> Installér Exchange 2013 eller 2016 i din eksisterende Exchange 2010-organisation. <p> Flyt tjenester og anden infrastruktur til Exchange 2013 eller 2016. <p> Flyt postkasser og offentlige mapper til Exchange 2013 eller 2016 Dekomprimer resterende Exchange 2010-servere.|
|Versions coexistence|Når du overfører til Exchange 2013 eller Exchange 2016, kan du installere begge versioner til en eksisterende Exchange 2010-organisation. Dette giver dig mulighed for at installere en eller flere Exchange 2013- Exchange 2016-servere og udføre overførslen.|
|Serverhardware|Krav til serverhardware har ændret sig Exchange 2010. Sørg for, at din hardware er kompatibel. Få mere at vide om hardwarekrav for hver version her: <p> [Exchange 2016-systemkrav](/Exchange/plan-and-deploy/system-requirements?view=exchserver-2016&preserve-view=true) <p> [Exchange 2013-systemkrav](/Exchange/exchange-2013-system-requirements-exchange-2013-help) <p> Med de væsentlige forbedringer af Exchange-ydeevnen og den øgede computerkraft og lagerkapacitet i nyere servere har du sandsynligvis brug for færre servere til at understøtte det samme antal postkasser.|
|Version af operativsystem|De understøttede minimumsversioner af operativsystemer for hver version er: <p> Exchange 2016 – Windows Server 2012 <p> Exchange 2013 – Windows Server 2008 R2 SP1 <p> Du kan finde flere oplysninger om understøttelse af operativsystem [i Exchange Supportability Matrix](/exchange/plan-and-deploy/supportability-matrix).|
|Funktionsniveau for Active Directory-skoven|De understøttede minimumsfunktionsniveauer for Active Directory-skoven for hver version er: <p> Exchange 2016 – Windows Server 2008 R2 SP1 <p> Exchange 2013 – Windows Server 2003 <p> Du kan finde flere oplysninger om understøttelse af skovens funktionsniveau [i Exchange Supportability Matrix](/exchange/plan-and-deploy/supportability-matrix).|
|Office klientversioner|De understøttede minimums Office klientversioner for hver version er: <p> Exchange 2016 – Office 2010 (med de seneste opdateringer) <p> Exchange 2013 – Office 2007 SP3 <p> Du kan finde flere oplysninger Office klientsupport [på Exchange Supportability Matrix](/exchange/plan-and-deploy/supportability-matrix).|
|

Brug følgende ressourcer som hjælp til din overførsel:

- [Exchange installationsassistent](/exchange/exchange-deployment-assistant)
- Active Directory-skemaændringer for Exchange [2016](/exchange/plan-and-deploy/active-directory/ad-schema-changes?view=exchserver-2016&preserve-view=true), [2013](/Exchange/exchange-2013-active-directory-schema-changes-exchange-2013-help)
- Systemkrav for Exchange [2016](/exchange/plan-and-deploy/system-requirements?view=exchserver-2016&preserve-view=true), [2013](/Exchange/exchange-2013-system-requirements-exchange-2013-help)
- Forudsætninger for Exchange [2016](/exchange/plan-and-deploy/prerequisites?view=exchserver-2016&preserve-view=true), [2013](/Exchange/exchange-2013-prerequisites-exchange-2013-help)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Oversigt over indstillinger for Office 2010-klient og -servere Windows 7

Du kan finde en visuel oversigt over indstillingerne for opgradering, overførsel og flytning til skyen for Office 2010-klienter og -servere og Windows 7 i slutningen af [supportplakaten](../downloads/Office2010Windows7EndOfSupport.pdf).

[![Ophør af support til Office 2010-klienter og -servere Windows 7 poster.](../media/microsoft-365-overview/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Denne plakat på én side illustrerer de forskellige veje Microsoft 365 Enterprise, du kan gå for at reagere på Office 2010-klienten og serverprodukter samt Windows 7, hvor understøttelsen af foretrukne stier og indstillinger er fremhævet.

Du kan også [downloade](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) denne plakat og udskrive den i letter-, legal- eller tabloid-format (11 x 17).

## <a name="what-if-i-need-help"></a>Hvad gør jeg, hvis jeg har brug for hjælp?

Hvis du overfører til en Microsoft 365, er du muligvis berettiget til at bruge vores Microsoft FastTrack-tjeneste. FastTrack giver de bedste fremgangsmåder, værktøjer og ressourcer til at gøre din overførsel Microsoft 365 så problemfri som muligt. Det bedste er, at du får en supporttekniker til at hjælpe dig fra planlægning og design til overførsel af din sidste postkasse. Du kan finde flere FastTrack i [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Hvis du løber ind i problemer under din overførsel til Microsoft 365, og du ikke bruger FastTrack, eller du overfører til en nyere version af Exchange Server, er her nogle ressourcer, du kan bruge:

- [Teknisk community](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [Kundesupport](https://support.microsoft.com/gp/support-options-for-business)

## <a name="related-articles"></a>Relaterede artikler

[Ressourcer, der kan hjælpe dig med at opgradere fra Office 2010-servere og -klienter](upgrade-from-office-2010-servers-and-products.md)
