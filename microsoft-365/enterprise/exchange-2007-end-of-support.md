---
title: køreplan for ophør af support Exchange 2007
ms.author: dstrome
author: dstrome
manager: scotv
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
ms.assetid: c3024358-326b-404e-9fe6-b618e54d977d
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: Få mere at vide om dine muligheder efter ophør af support Exchange Server 2007, og begynd at planlægge migrering til Microsoft 365, Office 365 eller Exchange 2016.
ms.openlocfilehash: 7b8cad31c04d5cd1cd9e618e8e38e872a1b32634
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092663"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>køreplan for ophør af support Exchange 2007

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Exchange Server 2007 ophørte med support i april 2017. Hvis du ikke har startet migreringen fra Exchange 2007 til Microsoft 365, Office 365 eller Exchange 2016, er det nu tid til at begynde at planlægge.

## <a name="what-does-end-of-support-mean"></a>Hvad betyder *ophør af support* ?

Exchange Server har som næsten alle Microsoft-produkter en supportlivscyklus, hvor vi leverer nye funktioner, fejlrettelser, sikkerhedsrettelser osv. Denne livscyklus varer typisk 10 år efter produktets første udgivelse. Slutningen af denne livscyklus er kendt som produktets ophør af support. Da Exchange 2007 ophørte med support den 11. april 2017, leverer Microsoft ikke længere:

- Teknisk support til problemer, der kan opstå.

- Fejlrettelser til problemer, der kan påvirke serverens stabilitet og anvendelighed.

- Sikkerhedsrettelser til sikkerhedsrisici, der kan gøre serveren sårbar over for brud på sikkerheden.

- Tidszoneopdateringer.

Din installation af Exchange 2007 fortsætter med at køre efter slutdatoen for support. Men da der ikke er nogen nye opdateringer eller support, anbefaler vi på det kraftigste, at du overfører fra Exchange 2007 så hurtigt som muligt.

Du kan få flere oplysninger om Office 2007-servere, der nærmer sig ophør af support, under [Planlæg opgraderingen fra Office 2007-servere og -produkter](upgrade-from-office-2007-servers-and-products.md).

## <a name="what-are-my-options"></a>Hvad er mine muligheder?

Du kan:

- Overfør til Microsoft 365 ved hjælp af komplet, faseindsat eller hybrid migrering.

- Overfør dine Exchange 2007-servere til en nyere version af Exchange på dine lokale servere.

I følgende afsnit udforskes hver indstilling mere detaljeret.

### <a name="migrate-to-microsoft-365"></a>Migrer til Microsoft 365

Overførsel af din mail til Microsoft 365 er den bedste og nemmeste løsning, der kan hjælpe dig med at trække udrulningen af Exchange 2007 ud. Med en migrering til Microsoft 365 kan du lave et enkelt hop fra den 10-årige teknologi til de nyeste funktioner, herunder:

- Funktioner til overholdelse af regler og standarder, f.eks. opbevaringspolitikker, In-Place og procesførelse, eDiscovery på stedet og meget mere

- Microsoft 365-grupper

- Fokuseret indbakke.

- MyAnalytics

- REST API'er til programmatisk adgang til mail, kalendere, kontakter osv.

Microsoft 365 får også nye funktioner og oplevelser først, så du og dine brugere normalt kan begynde at bruge dem med det samme. Og du behøver ikke at bekymre dig om:

- Køb og vedligeholdelse af hardware.

- Betale for at varme og køle dine servere.

- Holde dig ajour med rettelser af sikkerhed, produkter og tidszoner.

- Vedligeholdelse af lager og software for at understøtte krav til overholdelse af angivne standarder.

- Opgradering til en ny version af Exchange. Med Microsoft 365 bruger du altid den nyeste version af Exchange.

#### <a name="how-should-i-migrate-to-microsoft-365"></a>Hvordan skal jeg migrere til Microsoft 365?

Du har et par overførselsmuligheder. Du skal overveje et par ting, herunder:

- Det antal pladser eller postkasser, du skal flytte.
- Hvor længe migreringen skal vare.
- Uanset om du har brug for problemfri integration mellem din installation i det lokale miljø og Microsoft 365 under migreringen.

I denne tabel vises dine overførselsindstillinger og de vigtigste faktorer, der bestemmer, hvilken metode der skal bruges:

|Overførselsmulighed|Organisationsstørrelse|Varighed|
|---|---|---|
|Komplet migrering|Færre end 150 pladser|En uge eller mindre|
|Faseindsat migrering|Mere end 150 pladser|Et par uger|
|Komplet hybridoverførsel|Flere hundrede til tusindvis af sæder|Et par måneder eller mere|

Følgende afsnit indeholder en oversigt over disse metoder. Du kan finde flere oplysninger under [Beslut en overførselssti](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27).

#### <a name="cutover-migration"></a>Komplet migrering

I en komplet migrering overfører du alle dine postkasser, distributionsgrupper, kontakter osv. for at Microsoft 365 på en forudvalgt dato og et forudvalgt klokkeslæt. Når migreringen er fuldført, lukker du dine lokale Exchange-servere og begynder at bruge Microsoft 365 med udelt adgang.

Komplet migrering er fantastisk til små organisationer, der ikke har mange postkasser, som gerne vil Microsoft 365 hurtigt og ikke ønsker at håndtere nogle af kompleksiteterne ved de andre metoder. Men det skal fuldføres om en uge eller mindre, og det kræver, at brugerne omkonfigurerer deres Outlook profiler. Komplet migrering kan håndtere op til 2.000 postkasser, men vi anbefaler på det kraftigste, at du bruger den til at overføre maksimalt 150 postkasser. Hvis du forsøger at overføre flere, kan du løbe tør for tid til at overføre alle postkasserne inden din deadline, og it-supportpersonalet kan blive overvældet med anmodninger, der kan hjælpe brugerne med at omkonfigurere Outlook.

Hvis du overvejer at foretage en komplet migrering, skal du overveje følgende:

- Microsoft 365 skal oprette forbindelse til dine Exchange 2007-servere ved hjælp af Outlook Anywhere over TCP-port 443.

- Alle postkasser i det lokale miljø flyttes til Microsoft 365.

- Du skal bruge en administratorkonto i det lokale miljø, der har læseadgang til brugernes postkasser.

- De Exchange 2007-accepterede domæner, som du vil bruge i Microsoft 365, skal tilføjes som bekræftede domæner i tjenesten.

- Mellem det tidspunkt, hvor du starter overførslen, og når du starter fuldførelsesfasen, synkroniserer Microsoft 365 jævnligt de Microsoft 365 og postkasser i det lokale miljø. Det giver dig mulighed for at fuldføre overførslen uden at bekymre dig om, at mails efterlades i dine lokale postkasser.

- Brugerne modtager nye midlertidige adgangskoder til deres Microsoft 365 konti. De skal ændre deres adgangskode, første gang de logger på deres postkasse.

- Du skal bruge en Microsoft 365 licens, der indeholder Exchange Online for hver brugerpostkasse, du overfører.

- Brugerne skal konfigurere en ny Outlook profil på hver af deres enheder og downloade deres mail igen. Mængden af mail, som Outlook downloader, kan variere. Du kan få flere oplysninger under [Rediger, hvor mange mails der skal bevares offline](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).

Du kan få flere oplysninger om komplet migrering under:

- [Det har du brug for at vide om migrering af en komplet mail](https://support.office.com/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)

- [Udfør en komplet migrering af mail](https://support.office.com/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)

#### <a name="staged-migration"></a>Faseindsat migrering

I en faseinddelt migrering har du et par hundrede eller et par tusinde postkasser, som du vil overføre til Microsoft 365, du skal bruge en uge eller mere for at fuldføre migreringen, og du behøver ikke nogen avancerede hybride overførselsfunktioner som f.eks. delte oplysninger om ledig/optaget-kalender.

Faseindstillet migrering er fantastisk til organisationer, der har brug for mere tid til at overføre deres postkasser til Microsoft 365 men stadig planlægger at fuldføre migreringen inden for nogle få uger. Du kan overføre postkasser i batches. Du styrer, hvor mange og hvilke postkasser der migreres på et givet tidspunkt. Du kan f.eks. batchpostkasser for brugere i samme afdeling sikre, at de alle flyttes på samme tid. Du kan også forlade administrationens postkasser indtil det sidste bundt. På samme måde som med komplet migrering skal brugerne genskabe deres Outlook profiler.

Hvis du overvejer at foretage en trinvis migrering, skal du overveje følgende:

- Microsoft 365 skal oprette forbindelse til dine Exchange 2007-servere ved hjælp af Outlook Anywhere over TCP-port 443.

- Du skal bruge en administratorkonto i det lokale miljø, der har læseadgang til brugernes postkasser.

- De Exchange 2007-accepterede domæner, som du planlægger at bruge i Microsoft 365, skal tilføjes som bekræftede domæner i tjenesten.

- Du skal oprette en CSV-fil med det fulde navn og den fulde mailadresse for hver postkasse, som du planlægger at overføre i et batch. Du skal også inkludere en ny adgangskode for hver postkasse, du overfører, og sende adgangskoden til hver bruger. Brugeren bliver bedt om at ændre adgangskoden, første gang vedkommende logger på sin nye Microsoft 365 postkasse.

- Fra det tidspunkt, hvor du starter overførselsbatchen, og når du starter fuldførelsesfasen, synkroniserer Microsoft 365 jævnligt de Microsoft 365 og lokale postkasser, der er inkluderet i batchen. Det giver dig mulighed for at fuldføre overførslen uden at bekymre dig om, at mails efterlades i dine lokale postkasser.

- Du skal bruge en Microsoft 365 licens, der indeholder Exchange Online for hver brugerpostkasse, du overfører.

- Brugerne skal konfigurere en ny Outlook profil på hver af deres enheder og downloade deres mail igen. Mængden af mail, som Outlook downloader, kan variere. Du kan få flere oplysninger under [Rediger, hvor mange mails der skal bevares offline](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).

Du kan få flere oplysninger om trinvis overførsel under:

- [Det har du brug for at vide om en trinvis migrering af mail](https://support.office.com/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)

- [Udfør en faseindsat migrering af mail](https://support.office.com/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)

#### <a name="full-hybrid"></a>Fuld hybrid

I en komplet hybridoverførsel har din organisation mange hundrede, op til titusinder af postkasser, og du vil flytte nogle eller dem alle til Microsoft 365. Da disse migreringer typisk er længerevarende, gør hybride migreringer det muligt at:

- Vis oplysninger om ledig/optaget tid for brugere i det lokale miljø i Microsoft 365 og omvendt.

- Se en samlet global adresseliste, der indeholder modtagere både i det lokale miljø og i Microsoft 365.

- Få vist alle Outlook modtageregenskaber for alle brugere, uanset om de er i det lokale miljø eller i Microsoft 365.

- Sikker mailkommunikation mellem lokale Exchange servere og Microsoft 365 ved hjælp af TLS og certifikater.

- Behandl meddelelser, der sendes mellem Exchange servere i det lokale miljø, og Microsoft 365 som interne, så de kan:

  - Blive ordentligt evalueret og behandlet af transport- og overholdelsesagenter, der målretter interne meddelelser.

  - Omgå filtre mod spam.

Fuld hybridoverførsel er bedst til organisationer, der forventer at forblive i en hybridkonfiguration i mange måneder eller mere. Du får vist de funktioner, der er angivet tidligere i dette afsnit, samt katalogsynkronisering, bedre integrerede funktioner til overholdelse af angivne standarder og muligheden for at flytte postkasser til og fra Microsoft 365 ved hjælp af flytninger af postkasser online. Microsoft 365 bliver en udvidelse af din organisation i det lokale miljø.

Hvis du overvejer at foretage en komplet hybridoverførsel, skal du overveje følgende:

- Komplet hybridoverførsel er ikke velegnet til alle typer organisationer. På grund af kompleksiteten ved komplette hybride migreringer kan organisationer med mindre end nogle få hundrede postkasser typisk ikke se fordele, der begrunder den indsats og de omkostninger, der er nødvendige for at konfigurere en. Hvis det lyder som din organisation, anbefaler vi, at du i stedet overvejer en komplet eller iscenesat migrering.

- Du skal installere mindst én Exchange 2013-server i din Exchange 2007-organisation for at fungere som en "hybridserver". Denne server kommunikerer med Microsoft 365 på vegne af dine Exchange 2007-servere.

- Microsoft 365 skal oprette forbindelse til "hybridserveren" ved hjælp af Outlook Anywhere over TCP-port 443.

- Du skal konfigurere katalogsynkronisering ved hjælp af Azure Active Directory (Azure AD) Forbind mellem dine Active Directory i det lokale miljø servere og Microsoft 365.

- Brugerne kan logge på deres Microsoft 365 postkasse med det samme brugernavn og den samme adgangskode, som når de logger på det lokale netværk. Denne funktion kræver Azure AD-Forbind med synkronisering af adgangskode og/eller Active Directory Federation Services.

- Du skal bruge en Microsoft 365 licens, der indeholder Exchange Online for hver brugerpostkasse, du overfører.

- Brugerne behøver ikke at konfigurere en ny Outlook profil på de fleste af deres enheder, selvom nogle ældre Android-telefoner muligvis har brug for en ny profil. Brugerne behøver ikke at genindlæse deres mail.

Hvis fuld hybridoverførsel lyder rigtigt for dig, kan du se følgende ressourcer for at få hjælp til din migrering:

- [Exchange Installationsassistent](/exchange/exchange-deployment-assistant)

- [Exchange Server hybridinstallationer](/exchange/exchange-hybrid)

- [Guiden Hybridkonfiguration](/exchange/hybrid-configuration-wizard)

- [Ofte stillede spørgsmål om guiden Hybridkonfiguration](/exchange/hybrid-configuration-wizard-faqs)

- [Forudsætninger for hybridinstallation](/exchange/hybrid-deployment-prerequisites)

### <a name="migrate-to-a-newer-version-of-exchange-server"></a>Overfør til en nyere version af Exchange Server

Vi er overbeviste om, at du kan opnå den bedste værdi og brugeroplevelse ved at migrere til Microsoft 365. Men vi forstår også, at nogle organisationer skal beholde deres mail i det lokale miljø. Dette kan skyldes lovmæssige krav for at sikre, at data ikke gemmes i et datacenter, der er placeret i et andet land, eller lignende. Hvis du vælger at beholde din mail i det lokale miljø, kan du overføre dit Exchange 2007-miljø til Exchange 2010, Exchange 2013 eller Exchange 2016.

Hvis du ikke kan migrere til Microsoft 365, anbefaler vi, at du overfører til Exchange 2016. Exchange 2016 indeholder alle funktionerne i tidligere versioner af Exchange. Den passer også bedst til den oplevelse, der er tilgængelig med Microsoft 365, selvom nogle funktioner kun er tilgængelige i Microsoft 365. Se blot nogle af de ting, du har savnet:

|Exchange version|Funktioner|
|---|---|
|Exchange 2010| Role-Based Access Control (tilladelser uden ACL'er) <br/> politikker for Outlook Web App postkasse <br/> Mulighed for at dele ledig/optaget tid og uddelegere kalendere mellem organisationer|
|Exchange 2013| *Funktioner fra Exchange 2010 og ...* <br/> Forenklet arkitektur, der reducerede antallet af serverroller til tre (Postkasse, Klientadgang, Edge Transport) <br/> DLP-politikker (forebyggelse af datatab), der hjælper med at forhindre, at følsomme oplysninger lækker <br/> Forbedret Outlook Web App oplevelse|
|Exchange 2016| *Funktioner fra Exchange 2013 og ...* <br/> Yderligere forenklede serverroller til postkasse og Edge Transport <br/> Forbedret DLP sammen med integration med SharePoint <br/> Forbedret database robusthed <br/> Onlinedokumentsamarbejde|

#### <a name="which-version-should-i-migrate-to"></a>Hvilken version skal jeg migrere til?

Vi anbefaler, at du starter med at antage, at du vil migrere til Exchange 2016. Brug derefter følgende oplysninger til at bekræfte din antagelse eller til at udelukke Exchange 2016. Hvis du af en eller anden grund ikke kan migrere til Exchange 2016, skal du udføre den samme proces med Exchange 2013 osv.

|Overvejelse|Flere oplysninger|
|---|---|
|Slutdatoer for support| På samme måde som Exchange 2007 har hver version af Exchange sin egen slutdato for support: <br/> *Exchange 2010* - januar 2020 <br/> *Exchange 2013* - april 2023 <br/> *Exchange 2016* - oktober 2025 <br/> Jo tidligere supporten ophører, desto hurtigere skal du udføre en anden migrering.|
|Overførselssti til Exchange 2010 og 2013.|Her er de generelle faser for migrering til Exchange 2010 eller Exchange 2013: <br/> – Installér Exchange 2010 eller 2013 i din eksisterende Exchange 2007-organisation. <br/>– Flyt tjenester og anden infrastruktur til Exchange 2010 eller 2013.<br/>- Flyt postkasser og offentlige mapper til Exchange 2010 eller 2013.<br/>- De resterende Exchange 2007-servere tages ud af drift.|
|Overførselssti til Exchange 2016|Her er de generelle faser for migrering til Exchange 2016: <br/> – Installér Exchange 2013 i din eksisterende Exchange 2007-organisation.<br/>- Flyt tjenester og anden infrastruktur til Exchange 2013.<br/>- Flyt postkasser og offentlige mapper til Exchange 2013.<br/>- De resterende Exchange 2007-servere tages ud af drift.<br/>– Installér Exchange 2016 i din eksisterende Exchange 2013-organisation.<br/>– Flyt postkasser, offentlige mapper, tjenester og anden infrastruktur til Exchange 2016 (ordre betyder ikke noget). De resterende Exchange 2013-servere tages ud af drift.<br/><br/> **Bemærk:** Det er nemt at overføre fra Exchange 2013 til Exchange 2016. De to versioner har næsten de samme hardwarekrav, og disse versioner er meget kompatible. Så du kan genopbygge en server, du har købt til Exchange 2013, og installere Exchange 2016 på den. I forbindelse med flytning af onlinepostkasser vil de fleste brugere ikke engang bemærke, at deres postkasse blev flyttet fra serveren og derefter tilbage, efter at du har genopbygget den med Exchange 2016.|
|Version sameksistens| Når der migreres til ... <br/> **Exchange 2016:** Exchange 2016 kan ikke installeres i en organisation, der indeholder en Exchange 2007-server. Du skal først migrere til Exchange 2010 eller 2013 (vi anbefaler kraftigt Exchange 2013), fjerne alle Exchange 2007-servere og derefter migrere til Exchange 2016. <br/> **Exchange 2010 eller Exchange 2013:** Du kan installere Exchange 2010 eller Exchange 2013 i en eksisterende Exchange 2007-organisation. Dette giver dig mulighed for at installere en eller flere Exchange 2010- eller 2013-servere og udføre overførslen.|
|Serverhardware| Kravene til serverhardware er ændret fra Exchange 2007. Sørg for, at hardwaren er kompatibel. Du kan finde flere oplysninger i: <br/> [systemkrav til Exchange 2016](/Exchange/plan-and-deploy/system-requirements) <br/> [systemkrav til Exchange 2013](/exchange/exchange-2013-system-requirements-exchange-2013-help) <br/> [systemkrav til Exchange 2010](/previous-versions/office/exchange-server-2010/aa996719(v=exchg.141)) <br/> Du vil opdage, at de betydelige forbedringer i Exchange ydeevne og den øgede beregningskraft og lagerkapacitet på nyere servere betyder, at du sandsynligvis har brug for færre servere til at understøtte det samme antal postkasser.|
|Operativsystemversion| De operativsystemversioner, der som minimum understøttes for hver version, er: <br/> **Exchange 2016** – Windows Server 2012 <br/> **Exchange 2013** – Windows Server 2008 R2 SP1 <br/> **Exchange 2010** – Windows Server 2008 SP2 <br/> Du kan finde flere oplysninger om understøttelse af operativsystemet på [Exchange Supportability Matrix](/Exchange/plan-and-deploy/supportability-matrix).|
|Funktionelt niveau for Active Directory-område| De mindste understøttede funktionelle niveauer for Active Directory-områder for hver version er: <br/> **Exchange 2016** Windows Server 2008 R2 SP1 <br/> **Exchange 2013** Windows Server 2003 <br/> **Exchange 2010** Windows Server 2003 <br/> Du kan finde flere oplysninger om understøttelse af skovfunktionelt niveau på [Exchange Supportability Matrix](/Exchange/plan-and-deploy/supportability-matrix).|
|Office klientversioner| Den mindste understøttede Office klientversioner for hver version er: <br/> **Exchange 2016** – Office 2010 (med de seneste opdateringer) <br/> **Exchange 2013** - Office 2007 SP3 <br/> **Exchange 2010** - Office 2003 <br/> Du kan finde flere oplysninger om Office klientsupport på [Exchange Supportability Matrix](/Exchange/plan-and-deploy/supportability-matrix).|

#### <a name="how-do-i-migrate"></a>Hvordan gør jeg migrere?

Hvis du har besluttet at beholde din mail i det lokale miljø, kan du bruge følgende ressourcer til at hjælpe med din migrering:

- [Exchange Installationsassistent](/exchange/exchange-deployment-assistant)

- Active Directory-skemaændringer for Exchange [2016](/Exchange/plan-and-deploy/active-directory/ad-schema-changes), [2013](/exchange/exchange-2013-active-directory-schema-changes-exchange-2013-help), [2010](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)

- Systemkrav til Exchange [2016](/Exchange/plan-and-deploy/system-requirements), [2013](/exchange/exchange-2013-system-requirements-exchange-2013-help), [2010](/previous-versions/office/exchange-server-2010/aa996719(v=exchg.141))

- Forudsætninger for Exchange [2016](/Exchange/plan-and-deploy/prerequisites), [2013](/exchange/exchange-2013-prerequisites-exchange-2013-help), [2010](/previous-versions/office/exchange-server-2010/bb691354(v=exchg.141))

## <a name="get-help"></a>Få hjælp

Hvis du migrerer til Microsoft 365, er du muligvis berettiget til at bruge vores Microsoft FastTrack-tjeneste. FastTrack indeholder de bedste fremgangsmåder, værktøjer og ressourcer, så din migrering til Microsoft 365 så problemfrit som muligt. Det bedste af det hele er, at en supporttekniker fører dig gennem din migrering fra planlægning og design til overførsel af din sidste postkasse. Du kan få mere at vide om FastTrack under [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Hvis du støder på problemer under overførslen til Microsoft 365, og du ikke bruger FastTrack eller din migrering til en nyere version af Exchange Server, er vi her for at hjælpe. Her er nogle ressourcer, du kan bruge:

- [Teknisk community](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)

- [Kundesupport](https://support.microsoft.com/gp/support-options-for-business)

## <a name="related-topics"></a>Relaterede emner

[Ressourcer, der kan hjælpe dig med at opgradere dine Office 2007 servere og -klienter](upgrade-from-office-2007-servers-and-products.md)
