---
title: køreplan for ophør af support Exchange 2013
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
f1.keywords:
- NOCSH
description: Exchange 2013 ophører supporten i april 2023. Brug denne oversigt over planlægning til at forberede opgradering til Exchange Online eller til en nyere version af Exchange Server i det lokale miljø.
ms.openlocfilehash: 0d0cf068ad018e710c6d8e861ac04acfd261def9
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468498"
---
# <a name="exchange-2013-end-of-support-roadmap"></a>køreplan for ophør af support Exchange 2013

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Exchange Server 2013 ophører supporten **den 11. april 2023**. Hvis du ikke allerede har påbegyndt overførslen fra Exchange 2013 til Microsoft 365, Office 365 eller Exchange 2019, er det nu tid til at begynde at planlægge.

## <a name="what-does-end-of-support-mean"></a>Hvad betyder *ophør af support* ?

De fleste Microsoft-produkter har en supportlivscyklus, hvor de får nye funktioner, fejlrettelser, sikkerhedsrettelser osv. Denne livscyklus varer typisk 10 år efter produktets første udgivelse. Slutningen af denne livscyklus er kendt som produktets ophør af support. Da Exchange 2013 ophører med support den 11. april 2023, leverer Microsoft ikke længere følgende efter denne dato:

- Teknisk support til problemer, der kan opstå.
- Fejlrettelser til problemer, der kan påvirke serverens stabilitet og anvendelighed.
- Sikkerhedsrettelser til sikkerhedsrisici, der kan gøre serveren sårbar over for brud på sikkerheden.
- Tidszoneopdateringer.

Installationen af Exchange 2013 fortsætter med at køre efter denne dato. Men på grund af de ændringer, der er angivet ovenfor, anbefaler vi på det kraftigste, at du overfører fra Exchange 2013 til Exchange 2019 så hurtigt som muligt.


## <a name="what-are-my-options"></a>Hvad er mine muligheder?

Det er et godt tidspunkt til at udforske dine muligheder og udarbejde en overførselsplan. Du kan:

- Overfør til Microsoft 365. Overfør postkasser, offentlige mapper og andre data ved hjælp af cutover, minimal hybrid eller fuld hybridoverførsel. Fjern derefter Exchange-servere og Active Directory i det lokale miljø.
- Opgrader Exchange 2013. Flyt til Exchange 2019 for dine lokale servere.

> [!IMPORTANT]
> Hvis din organisation vælger at overføre postkasser til Microsoft 365 men planlægger at fortsætte med at bruge Azure AD Forbind til at administrere brugerkonti i Active Directory, skal du beholde mindst én Microsoft Exchange-server i det lokale miljø. Hvis du fjerner alle Exchange servere, kan du ikke foretage ændringer af Exchange modtagere i Exchange Online, fordi autoritetskilden er din Active Directory i det lokale miljø. I dette scenarie har du følgende muligheder:
>
>- *Anbefalede:* Overfør dine postkasser til Microsoft 365, og opgrader dit miljø til Exchange 2019 senest den 11. april 2023. Brug Exchange 2013 til at oprette forbindelse til Microsoft 365 og overføre postkasser. Derefter skal du opgradere fra Exchange 2013 til Exchange 2019 og demonteringsservere, der kører Exchange 2013.
>- Hvis du ikke kan fuldføre en migrering til Exchange Online og opgradere dine lokale servere senest den 11. april 2023, skal du først opgradere fra Exchange 2013 til Exchange 2019 og derefter bruge Exchange 2019 til at overføre postkasser til Microsoft 365.

Her er de tre veje, du kan gå for at undgå ophør af support til Exchange Server 2013.

## <a name="migrate-to-microsoft-365"></a>Migrer til Microsoft 365

Overførsel til Microsoft 365 er den bedste og nemmeste løsning, der kan hjælpe dig med at trække udrulningen af Exchange 2013 ud. Med en migrering til Microsoft 365 kan du oprette et enkelt hop fra gammel teknologi til aktuelle funktioner, herunder:

- Større postkasser med større data robusthed;
- Sikkerhedsfunktioner som f.eks. beskyttelse mod spam og antimalware, 
- Funktioner til overholdelse af angivne standarder, f.eks. forebyggelse af datatab, opbevaringspolitikker, In-Place og procesførelse, direkte eDiscovery m.m.
- Integration med SharePoint Online, OneDrive, Teams, Power BI og andre Microsoft 365 tjenester;
- Fokuseret indbakke; Og
- Avanceret analyse og Viva Insights.

Microsoft 365 får også nye funktioner og oplevelser først, så din organisation kan begynde at bruge dem med det samme. Du behøver heller ikke at bekymre dig om:

- Køb og vedligeholdelse af hardware;
- Betaling for at køre og køle dine servere.
- Holde servere opdateret om sikkerheds-, produkt- og tidszonerettelser.
- Vedligeholdelse af serverlager og software for at understøtte krav til overholdelse af angivne standarder. Eller
- Opgradering til en ny version af Exchange. Du har altid den nyeste version med Microsoft 365.

### <a name="how-should-i-migrate-to-microsoft-365"></a>Hvordan skal jeg migrere til Microsoft 365?

Afhængigt af din organisation har du et par muligheder for at få adgang til Microsoft 365. Først skal du overveje et par ting, f.eks.:

- Det antal postkasser, du skal flytte.
- Hvor længe migreringen skal vare. Og
- Uanset om du har brug for en problemfri integration mellem dit lokale miljø og Microsoft 365 under migreringen.

I denne tabel vises dine overførselsindstillinger og de vigtigste faktorer, der bestemmer, hvilken metode der skal bruges.

<br>

****

|Overførselsmulighed|Organisationsstørrelse|Varighed|
|---|---|---|
|Komplet migrering|Færre end 150 postkasser|En uge eller mindre|
|Minimal hybridoverførsel|Færre end 150 postkasser|Et par uger eller mindre|
|Komplet hybridoverførsel|Mere end 150 postkasser|Et par uger eller mere|
|

I følgende afsnit får du et overblik over disse metoder. Du kan få flere oplysninger under [Fastgør en overførselssti](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27).

### <a name="cutover-migration"></a>Komplet migrering

I en komplet migrering overfører du alle dine postkasser, distributionsgrupper, kontakter osv. for at Office 365 på en angivet dato og et angivet klokkeslæt. Når du er færdig, lukker du dine lokale Exchange-servere og begynder at bruge Microsoft 365 med udelt adgang.

Komplet migrering er fantastisk til små organisationer, der ikke har mange postkasser, som gerne vil Microsoft 365 hurtigt og ikke vil håndtere kompleksiteten af de andre metoder. Men det bør være afsluttet om en uge eller mindre. Og det kræver, at brugerne omkonfigurerer deres Outlook profiler. Komplet migrering kan overføre op til 2.000 postkasser, men vi anbefaler, at du bruger den til højst 150. Hvis du forsøger at overføre flere, kan du løbe tør for tid til at overføre alle postkasserne inden din deadline, og it-supportpersonalet kan blive overvældet med anmodninger, der kan hjælpe brugerne med at omkonfigurere Outlook.

Her er ting, du skal overveje i forbindelse med komplet migrering:

- Microsoft 365 skal oprette forbindelse til dine Exchange 2013-servere ved hjælp af Outlook Anywhere over TCP-port 443.
- Alle postkasser i det lokale miljø flyttes til Microsoft 365.
- Du skal bruge en administratorkonto i det lokale miljø, der har læseadgang til brugernes postkasser.
- De Exchange 2013-accepterede domæner, som du vil bruge i Microsoft 365 skal tilføjes som bekræftede domæner i tjenesten.
- Mellem når du starter overførslen, og når du starter fuldførelsesfasen, synkroniserer Microsoft 365 jævnligt de Microsoft 365 og postkasser i det lokale miljø. Det giver dig mulighed for at fuldføre overførslen uden at bekymre dig om, at mails efterlades i dine lokale postkasser.
- Brugerne modtager nye midlertidige adgangskoder til deres Microsoft 365 konto. De skal ændre dem, første gang de logger på deres postkasser.
- Du skal bruge en Microsoft 365 licens, der indeholder Exchange Online for hver brugerpostkasse, du overfører.
- Brugerne skal konfigurere en ny Outlook profil på hver af deres enheder og downloade deres mail igen. Mængden af mail, som Outlook downloader, kan variere. Du kan få flere oplysninger [under Arbejd offline i Outlook](https://support.microsoft.com/office/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

Du kan få mere at vide om komplet migrering under:

- [Det har du brug for at vide om migrering af en komplet mail](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration)
- [Udfør en komplet migrering af mail til Office 365](/Exchange/mailbox-migration/cutover-migration-to-office-365)

### <a name="minimal-hybrid-migration"></a>Minimal hybridoverførsel

I en minimal hybrid eller hurtig overførsel flytter du nogle få hundrede postkasser til Microsoft 365 inden for nogle få uger. Denne metode understøtter ikke avancerede hybridoverførselsfunktioner, f.eks. delte oplysninger om ledig/optaget tid.

Minimal hybridoverførsel er fantastisk til organisationer, der har brug for mere tid til at overføre deres postkasser til Microsoft 365, men stadig planlægger at fuldføre migreringen inden for nogle få uger. Du får nogle af fordelene ved den mere avancerede *fuld hybride migrering* uden meget af kompleksiteten. Du kan styre, hvor mange og hvilke postkasser der skal overføres på et givet tidspunkt. Microsoft 365 postkasser oprettes med brugernavnene og adgangskoderne for kontiene i det lokale miljø. Og i modsætning til komplet migrering behøver dine brugere ikke at genskabe deres Outlook profiler.

Her er ting, du skal overveje i forbindelse med minimal hybridoverførsel:

- Du skal udføre en engangsmappesynkronisering mellem dine Active Directory i det lokale miljø servere og Microsoft 365.
- Brugerne kan logge på deres Microsoft 365 postkasse med samme brugernavn og adgangskode som før deres postkasse.
- Du skal bruge en Microsoft 365 licens, der indeholder Exchange Online for hver brugerpostkasse, du overfører.
- Brugerne behøver ikke at konfigurere en ny Outlook profil på de fleste af deres enheder, selvom nogle ældre Android-telefoner muligvis har brug for en ny profil. Brugerne behøver ikke at downloade deres mail igen.

Du kan finde flere oplysninger under [Brug Minimal Hybrid til hurtigt at overføre Exchange postkasser til Office 365](/Exchange/mailbox-migration/use-minimal-hybrid-to-quickly-migrate).

### <a name="full-hybrid"></a>Fuld hybrid

I en komplet hybridoverførsel har du mange hundreder, op til titusinder af postkasser, og du flytter nogle eller alle til Microsoft 365. Da disse migreringer typisk er længerevarende, gør hybride migreringer det muligt at:

- Vis oplysninger om ledig/optaget tid for brugere i det lokale miljø i Microsoft 365 og omvendt.
- Se en samlet global adresseliste, der indeholder modtagere både i det lokale miljø og i Microsoft 365.
- Få vist alle Outlook modtageregenskaber for alle brugere, uanset om de er i det lokale miljø eller i Microsoft 365.
- Sikker mailkommunikation mellem lokale Exchange servere og Office 365 ved hjælp af TLS og certifikater.
- Behandl meddelelser, der sendes mellem Exchange servere i det lokale miljø, og Microsoft 365 som interne, så de kan:
  - Blive ordentligt evalueret og behandlet af transport- og overholdelsesagenter, der målretter interne meddelelser.
  - Omgå filtre mod spam.

Komplette hybride migreringer er bedst til organisationer, der forventer at forblive i en hybridkonfiguration i mange måneder eller mere. Du får vist de funktioner, der er angivet tidligere i dette afsnit, samt katalogsynkronisering, bedre integrerede funktioner til overholdelse af angivne standarder og muligheden for at flytte postkasser til og fra Microsoft 365 ved hjælp af flytninger af onlinepostkasser. Microsoft 365 bliver en udvidelse af din organisation i det lokale miljø.

Ting, du skal overveje i forbindelse med komplet hybridoverførsel:

- De er ikke velegnede til alle organisationer. På grund af kompleksiteten ved komplette hybride migreringer kan organisationer med mindre end nogle få hundrede postkasser typisk ikke se fordele, der begrunder indsatsen og omkostningerne. I sådanne tilfælde anbefaler vi, at du overvejer komplet overførsel eller minimal hybridoverførsel i stedet.
- Du skal konfigurere katalogsynkronisering ved hjælp af Azure Active Directory (Azure AD) Forbind mellem dine Active Directory i det lokale miljø servere og Microsoft 365.
- Brugerne kan logge på deres Microsoft 365 postkasse med samme brugernavn og adgangskode, som de bruger, når de logger på det lokale netværk. Denne funktion kræver Azure AD Forbind med adgangskodesynkronisering og/eller Active Directory Federation Services).
- Du skal bruge en Microsoft 365 licens, der indeholder Exchange Online for hver brugerpostkasse, du overfører.
- Brugerne behøver ikke at konfigurere en ny Outlook profil på de fleste af deres enheder, selvom nogle ældre Android-telefoner muligvis har brug for en ny profil. Brugerne behøver ikke at downloade deres mail igen.

> [!IMPORTANT]
> Hvis din organisation vælger at overføre postkasser til Microsoft 365 men planlægger at beholde Azure AD Forbind til administration af brugerkonti i Active Directory, skal du beholde mindst én Exchange server i det lokale miljø. Hvis alle Exchange servere fjernes, kan du ikke foretage ændringer af Exchange modtagere. Det skyldes, at autoritetskilden er Active Directory, og at der skal foretages ændringer der.

Hvis en fuld hybridoverførsel lyder rigtigt for dig, kan du se følgende nyttige ressourcer:

- [Exchange Installationsassistent](/exchange/exchange-deployment-assistant)
- [Exchange Server hybridinstallationer](/exchange/exchange-hybrid)
- [Guiden Hybridkonfiguration](/exchange/hybrid-configuration-wizard)
- [Ofte stillede spørgsmål om guiden Hybridkonfiguration](/exchange/hybrid-configuration-wizard-faqs)
- [Forudsætninger for hybridinstallation](/exchange/hybrid-deployment-prerequisites)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Opgrader til en nyere version af Exchange Server i det lokale miljø

Vi er overbeviste om, at du får den bedste værdi og brugeroplevelse ved at migrere fuldt ud til Microsoft 365. Men vi forstår, at nogle organisationer skal beholde nogle Exchange servere i det lokale miljø. Dette kan skyldes lovmæssige krav, for at garantere, at data ikke gemmes i et fremmed datacenter, fordi du har entydige indstillinger eller krav, der ikke kan opfyldes i cloudmiljøet, eller fordi du har brug for Exchange til at administrere cloudpostkasser, fordi du stadig bruger Active Directory i det lokale miljø. Hvis du beholder Exchange i det lokale miljø, skal du under alle omstændigheder sikre, at dit Exchange 2013-miljø opgraderes.

For at få den bedste oplevelse anbefaler vi, at du opgraderer dit resterende lokale miljø til Exchange 2019. Du behøver ikke at installere Exchange Server 2016, fordi du kan gå direkte fra Exchange Server 2013 til Exchange Server 2019. Exchange 2019 stemmer bedst overens med den oplevelse, der er tilgængelig med Microsoft 365, selvom nogle funktioner kun er tilgængelige i Microsoft 365.



****
Nedenfor er vigtige ting at vide om opgradering Exchange 2013:

|Element|Flere oplysninger|
|---|---|
|Slutdatoer for support|På samme måde som Exchange 2013 har hver version af Exchange sin egen slutdato for support: <p> Exchange 2013 - april 2023 <p> April 2023 er meget tættere på, end du tror!|
|Overførselssti til Exchange 2019|Overførselsstien fra Exchange 2013 til en nyere version er enkel: <p> Installér Exchange 2019 i din eksisterende Exchange 2013-organisation. <p> Flyt tjenester og data fra Exchange 2013 til Exchange 2019, og demonter Exchange 2013-servere.|
|Serverhardware|Kravene til serverhardware er ændret fra Exchange 2013. Sørg for, at hardwaren er kompatibel. Få mere at vide om hardwarekrav her: <p> [systemkrav til Exchange 2019](/exchange/plan-and-deploy/system-requirements?view=exchserver-2019) <p>Med de betydelige forbedringer i Exchange ydeevne og den øgede beregningskapacitet og lagerkapacitet på nyere servere har du sandsynligvis brug for færre servere til at understøtte det samme antal postkasser.|
|Operativsystemversion|Den mindste understøttede operativsystemversion for Exchange 2019 er Windows Server 2019. Windows Server 2022-support kommer snart <p> Du kan finde flere oplysninger om understøttelse af operativsystemet på [Exchange Supportability Matrix](/exchange/plan-and-deploy/supportability-matrix).|
|Funktionelt niveau for Active Directory-område|Det mindste understøttede funktionelle niveau i Active Directory-området er Windows Server 2012 R2. Du kan finde flere oplysninger om understøttelse af skovfunktionelt niveau på [Exchange Supportability Matrix](/exchange/plan-and-deploy/supportability-matrix).|
|Office klientversioner|Den mindste understøttede Office klientversion er også dokumenteret i [Exchange Supportability Matrix](/exchange/plan-and-deploy/supportability-matrix?view=exchserver-2019#clients).|
|

Brug følgende ressourcer til at hjælpe med overførslen:

- [Exchange Installationsassistent](/exchange/exchange-deployment-assistant)
- Active [Directory-skemaændringer for Exchange 2019](/exchange/plan-and-deploy/active-directory/ad-schema-changes?view=exchserver-2019)
- [Systemkrav til Exchange 2019](/exchange/plan-and-deploy/system-requirements?view=exchserver-2019)


## <a name="what-if-i-need-help"></a>Hvad hvis jeg har brug for hjælp?

Hvis du migrerer til Microsoft 365, er du muligvis berettiget til at bruge vores Microsoft FastTrack-tjeneste. FastTrack indeholder de bedste fremgangsmåder, værktøjer og ressourcer, så din migrering til Microsoft 365 så problemfrit som muligt. Det bedste af det hele er, at du får en supporttekniker til at gennemgå alt lige fra planlægning og design til migrering af din sidste postkasse. Du kan få mere at vide om FastTrack under [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Hvis du støder på problemer under overførslen til Microsoft 365, og du ikke bruger FastTrack, eller du overfører til en nyere version af Exchange Server, er her nogle ressourcer, du kan bruge:

- [Teknisk community](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [Kundesupport](https://support.microsoft.com/gp/support-options-for-business)


