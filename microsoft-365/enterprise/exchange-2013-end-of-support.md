---
title: Exchange slutdato for support for 2013
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
description: Exchange 2013 når sin ophør af supporten i april 2023. Brug denne planlægningsoversigt til at forberede dig på at opgradere Exchange Online eller til en nyere version Exchange Server lokalt miljø.
ms.openlocfilehash: 2b949c113be16db97d68d92f2f1529245c287e48
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63598542"
---
# <a name="exchange-2013-end-of-support-roadmap"></a>Exchange slutdato for support for 2013

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Exchange Server 2013 slutter supporten d. **11. april 2023**. Hvis du ikke allerede er begyndt at bruge overførslen fra Exchange 2013 til Microsoft 365, Office 365 eller Exchange 2019, skal du begynde planlægningen nu.

## <a name="what-does-end-of-support-mean"></a>Hvad *betyder ophør af support* ?

De fleste Microsoft-produkter har en supportlivscyklus, hvor de får nye funktioner, fejlrettelser, sikkerhedsopdateringer osv. Denne livscyklus varer typisk 10 år fra produktets første udgivelse. Slutningen af denne livscyklus kaldes for ophør af support for produktet. Da Exchange 2013 når slutningen af supporten d. 11. april 2023, yder Microsoft længere:

- Teknisk support til problemer, der kan opstå.
- Fejlrettelser af problemer, der kan påvirke stabiliteten og anvendeligheden af serveren.
- Sikkerhedsopdateringer til sårbarheder, der kan gøre serveren sårbar over for sikkerhedsbrister.
- Tidszoneopdateringer.

Din installation af Exchange 2013 fortsætter med at køre efter denne dato. Men på grund af ændringerne, der er angivet ovenfor, anbefaler vi kraftigt, at du overfører fra Exchange 2013 til Exchange 2019 så tidligt som muligt.


## <a name="what-are-my-options"></a>Hvilke muligheder har jeg?

Det er et godt tidspunkt at udforske dine muligheder og forberede en overførselsplan. Du kan:

- Overfør til Microsoft 365. Overfør postkasser, offentlige mapper og andre data ved hjælp af komplet, minimal hybrid eller fuld hybridoverførsel. Fjern derefter lokale servere Exchange Active Directory.
- Opgrader Exchange 2013. Flyt til Exchange 2019 til dine lokale servere.

> [!IMPORTANT]
> Hvis din organisation vælger at overføre postkasser til Microsoft 365 men planlægger at fortsætte med at bruge Azure AD Forbind til at administrere brugerkonti i Active Directory, skal du have mindst én Microsoft Exchange-server lokalt. Hvis du fjerner alle Exchange-servere, kan du ikke foretage ændringer til Exchange-modtagere i Exchange Online, fordi kilden til autoriteten er din lokale Active Directory. I dette scenarie har du følgende muligheder:
>
>- *Anbefalet:* Overfør dine postkasser til Microsoft 365 og opgrader dit miljø til Exchange 2019 senest d. 11. april 2023. Brug Exchange 2013 til at oprette forbindelse Microsoft 365 og overføre postkasser. Opgrader derefter fra Exchange 2013 til Exchange 2019, og uddemissionsservere, der Exchange 2013.
>- Hvis du ikke kan gennemføre en overførsel til Exchange Online og opgradere dine lokale servere senest d. 11. april 2023, skal du opgradere fra Exchange 2013 til Exchange 2019 først og derefter bruge Exchange 2019 til at overføre postkasser til Microsoft 365.

Her er de tre stier, du kan gå for at undgå ophør af support til Exchange Server 2013.

## <a name="migrate-to-microsoft-365"></a>Overfør til Microsoft 365

Overførsel til en Microsoft 365 er den bedste og mest enkle metode til at hjælpe dig med at trække din Exchange 2013-installation tilbage. Med en overførsel til Microsoft 365, kan du foretage et enkelt hop fra gammel teknologi til aktuelle funktioner, herunder:

- Større postkasser med større datarobusthed;
- Sikkerhedsegenskaber som f.eks. beskyttelse mod uønsket post og antimalware, 
- Overholdelsesegenskaber som forebyggelse af datatab, opbevaringspolitikker, In-Place retslig tilbageholdelse og retslig tilbageholdelse, direkte eDiscovery og meget mere;
- Integration med SharePoint online, OneDrive, Teams, Power BI og andre Microsoft 365 tjenester;
- Fokuseret indbakke; og
- Avanceret analyse og Viva Insights.

Microsoft 365 får også nye funktioner og oplevelser først, så din organisation kan begynde at bruge dem med det samme. Du behøver heller ikke at bekymre dig om at:

- Købe og vedligeholde hardware
- Betaling for at køre og nedkøling af dine servere;
- Holde servere opdateret om rettelser af sikkerhed, produkter og tidszoner.
- Vedligeholdelse af serverlagring og -software for at understøtte overholdelseskrav; eller
- Opgrader til en ny version Exchange. Du har altid den nyeste version med Microsoft 365.

### <a name="how-should-i-migrate-to-microsoft-365"></a>Hvordan skal jeg overføre til Microsoft 365?

Afhængigt af din organisation har du et par muligheder for at komme til Microsoft 365. Først skal du overveje et par ting, f.eks.:

- Antallet af postkasser, du skal flytte.
- Hvor længe du vil have overførslen til at vare. og
- Uanset om du har brug for problemfri integration mellem dit lokale miljø Microsoft 365 under overførslen.

Denne tabel viser dine overførselsmuligheder og de vigtigste faktorer, der bestemmer, hvilken metode du skal bruge.

<br>

****

|Overførselsmulighed|Organisationens størrelse|Varighed|
|---|---|---|
|Cutover migration|Færre end 150 postkasser|En uge eller mindre|
|Minimal hybridoverførsel|Færre end 150 postkasser|Et par uger eller mindre|
|Fuld hybridoverførsel|Mere end 150 postkasser|Et par uger eller mere|
|

De følgende afsnit giver dig et overblik over disse metoder. Få mere at vide under [Beslut dig for en overførselsti](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27).

### <a name="cutover-migration"></a>Cutover migration

I en migrering overfører du alle dine postkasser, distributionsgrupper, kontakter osv., for at Office 365 på en angivet dato og et angivet klokkeslæt. Når du er færdig, lukker du dine lokale servere og Exchange udelukkende bruge Microsoft 365 serverne.

Den gratis migrering er god til små organisationer, der ikke har mange postkasser, ønsker at få hurtig adgang til Microsoft 365 og ikke ønsker at håndtere kompleksiteten ved de andre metoder. Men det bør gennemføres om en uge eller mindre. Og det kræver, at brugerne omkonfigurere deres Outlook profiler. Den gratis migrering kan overføre op til 2.000 postkasser, men vi anbefaler, at du bruger den maksimalt 150. Hvis du forsøger at overføre flere, kan du løbe tør for tid til at overføre alle postkasserne før din deadline, og dit it-supportpersonale kan blive overvældet af anmodninger om at hjælpe brugerne med at konfigurere Outlook.

Her er nogle ting, du skal overveje om en migrering:

- Microsoft 365 skal oprette forbindelse til dine Exchange 2013-servere ved hjælp af Outlook hvor som helst via TCP-port 443.
- Alle lokale postkasser flyttes til Microsoft 365.
- Du skal bruge en lokal administratorkonto, der har læseadgang til dine brugeres postkasser.
- De Exchange 2013-accepterede domæner, du vil bruge i Microsoft 365, skal tilføjes som bekræftede domæner i tjenesten.
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
> Hvis din organisation vælger at overføre postkasser til Microsoft 365 men planlægger at beholde Azure AD Forbind til administration af brugerkonti i Active Directory, skal du have mindst én Exchange-server lokalt. Hvis alle Exchange serverne fjernes, kan du ikke foretage ændringer for Exchange modtagere. Dette skyldes, at kilden til autoriteten er Active Directory, og ændringerne skal foretages der.

Hvis en fuld hybridoverførsel lyder som den rigtige for dig, kan du finde følgende nyttige ressourcer:

- [Exchange installationsassistent](/exchange/exchange-deployment-assistant)
- [Exchange Server hybridinstallationer](/exchange/exchange-hybrid)
- [Guiden Hybridkonfiguration](/exchange/hybrid-configuration-wizard)
- [Ofte stillede spørgsmål til guiden Hybridkonfiguration](/exchange/hybrid-configuration-wizard-faqs)
- [Forudsætninger for hybridinstallation](/exchange/hybrid-deployment-prerequisites)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Opgrader til en nyere version Exchange Server lokal version

Vi er stærkt overbeviste om, at du får den bedste værdi og brugeroplevelse ved at overføre fuldt ud Microsoft 365. Men vi forstår, at nogle organisationer har brug for at bevare Exchange lokale servere. Dette kan skyldes lovmæssige krav for at garantere, at data ikke gemmes i et fremmed datacenter, fordi du har unikke indstillinger eller krav, der ikke kan opfyldes i skyen, eller fordi du skal Exchange til at administrere postkasser i skyen, fordi du stadig bruger Active Directory lokalt. Under alle omstændigheder skal du, Exchange lokalt miljø, sikre, at dit Exchange 2013-miljø opgraderes.

For at få den bedste oplevelse anbefaler vi, at du opgraderer dit resterende lokale miljø til Exchange 2019. Du behøver ikke at installere Exchange Server 2016, da du kan gå direkte fra Exchange Server 2013 til Exchange Server 2019. Exchange 2019 passer bedst til den oplevelse, der er tilgængelig Microsoft 365, selvom visse funktioner kun er tilgængelige i Microsoft 365.



****
Nedenfor er der vigtige ting, du bør vide om opgradering Exchange 2013:

|Element|Flere oplysninger|
|---|---|
|Slutdato for support|Ligesom Exchange 2013 har hver version Exchange sin egen slutdato for support: <p> Exchange 2013 – april 2023 <p> April 2023 er meget tættere på, end du tror!|
|Overførselssti til Exchange 2019|Overførselsstien fra Exchange 2013 til en nyere version er enkel: <p> Installér Exchange 2019 i din eksisterende Exchange 2013-organisation. <p> Flyt tjenester og data fra Exchange 2013 til Exchange 2019, og udrævn Exchange 2013-servere.|
|Serverhardware|Krav til serverhardware har ændret sig Exchange 2013. Sørg for, at din hardware er kompatibel. Få mere at vide om hardwarekrav her: <p> [Exchange 2019-systemkrav](/exchange/plan-and-deploy/system-requirements?view=exchserver-2019) <p>Med de væsentlige forbedringer af Exchange-ydeevnen og den øgede computerkraft og lagerkapacitet i nyere servere har du sandsynligvis brug for færre servere til at understøtte det samme antal postkasser.|
|Version af operativsystem|Den understøttede minimumsversion af operativsystemet for Exchange 2019 er Windows Server 2019. Windows snart support til Server 2022 <p> Du kan finde flere oplysninger om understøttelse af operativsystem [i Exchange Supportability Matrix](/exchange/plan-and-deploy/supportability-matrix).|
|Funktionsniveau for Active Directory-skoven|Det understøttede minimumsfunktionsniveau for Active Directory-skoven Windows Server 2012 R2. Du kan finde flere oplysninger om understøttelse af skovens funktionsniveau [i Exchange Supportability Matrix](/exchange/plan-and-deploy/supportability-matrix).|
|Office klientversioner|Den understøttede minimumsversion Office-klientversionen er også dokumenteret [i Exchange Supportability Matrix](/exchange/plan-and-deploy/supportability-matrix?view=exchserver-2019#clients).|
|

Brug følgende ressourcer som hjælp til din overførsel:

- [Exchange installationsassistent](/exchange/exchange-deployment-assistant)
- Ændringer i Active [Directory-skemaet for Exchange 2019](/exchange/plan-and-deploy/active-directory/ad-schema-changes?view=exchserver-2019)
- [Systemkrav for Exchange 2019](/exchange/plan-and-deploy/system-requirements?view=exchserver-2019)


## <a name="what-if-i-need-help"></a>Hvad gør jeg, hvis jeg har brug for hjælp?

Hvis du overfører til en Microsoft 365, er du muligvis berettiget til at bruge vores Microsoft FastTrack-tjeneste. FastTrack giver de bedste fremgangsmåder, værktøjer og ressourcer til at gøre din overførsel Microsoft 365 så problemfri som muligt. Det bedste er, at du får en supporttekniker til at hjælpe dig fra planlægning og design til overførsel af din sidste postkasse. Du kan finde flere FastTrack i [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Hvis du løber ind i problemer under din overførsel til Microsoft 365, og du ikke bruger FastTrack, eller du overfører til en nyere version af Exchange Server, er her nogle ressourcer, du kan bruge:

- [Teknisk community](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [Kundesupport](https://support.microsoft.com/gp/support-options-for-business)


