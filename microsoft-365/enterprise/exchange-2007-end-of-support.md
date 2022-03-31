---
title: Exchange end of support 2007
ms.author: dstrome
author: dstrome
manager: laurawi
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
description: Få mere at vide om dine muligheder, når Exchange Server support i 2007 er slut, og begynd at planlægge overførslen Microsoft 365, Office 365 eller Exchange 2016.
ms.openlocfilehash: d5e79666c0e8e9804a63c89a0095a8725f14cd35
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63601619"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Exchange end of support 2007

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Exchange Server supporten i april 2017 nås til slutningen af 2017. Hvis du ikke har startet overførslen fra Exchange 2007 til Microsoft 365, Office 365 eller Exchange 2016, skal du begynde planlægningen nu.
  
## <a name="what-does-end-of-support-mean"></a>Hvad *betyder ophør af support* ?

Exchange Server som stort set alle Microsoft-produkter har en supportlivscyklus, hvor vi giver dig nye funktioner, fejlrettelser, sikkerhedsopdateringer osv. Denne livscyklus varer typisk 10 år fra produktets første udgivelse. Slutningen af denne livscyklus kaldes for ophør af support for produktet. Siden Exchange 2007 havde ophør af supporten d. 11. april 2017, yder Microsoft ikke længere:
  
- Teknisk support til problemer, der kan opstå.
    
- Fejlrettelser af problemer, der kan påvirke stabiliteten og anvendeligheden af serveren.
    
- Sikkerhedsopdateringer til sårbarheder, der kan gøre serveren sårbar over for sikkerhedsbrister.
    
- Tidszoneopdateringer.
    
Din installation af Exchange 2007 fortsætter med at køre efter slutdatoen for support. Men da der ikke er nogen nye opdateringer eller support, anbefaler vi på det kraftigste, at du overfører fra Exchange 2007 så tidligt som muligt.
  
Du kan finde flere oplysninger Office 2007-servere, hvor support snart er slut, under Planlæg din opgradering fra [Office 2007-servere og -produkter](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Hvilke muligheder har jeg?

Du kan:
  
- Overfør til Microsoft 365 ved hjælp af cutover, staged eller hybrid migrering.
    
- Overfør Exchange 2007-servere til en nyere version Exchange på dine lokale servere.
    
I de følgende afsnit gennemgås hver indstilling mere detaljeret.
  
### <a name="migrate-to-microsoft-365"></a>Overfør til Microsoft 365

Den nemmeste og mest enkle Microsoft 365 at hjælpe med at trække din mail tilbage Exchange 2007-installation. Med en overførsel til Microsoft 365 kan du foretage et enkelt hop fra 10 år gamle teknologi til avancerede funktioner, herunder:
  
- Overholdelsesegenskaber som f.eks Opbevaringspolitikker, In-Place retslig tilbageholdelse, direkte eDiscovery og meget mere
    
- Microsoft 365 grupper
    
- Fokuseret indbakke.
    
- MyAnalytics
    
- REST-API'er til programmeringsadgang til mail, kalendere, kontakter og så videre
    
Microsoft 365 får også nye funktioner og oplevelser først, så du og dine brugere som regel kan begynde at bruge dem med det samme. Og du behøver ikke at bekymre dig om at:
  
- Købe og vedligeholde hardware.
    
- Betaling for varme og afkøling af dine servere.
    
- Hold dig opdateret om rettelser af sikkerhed, produkter og tidszoner.
    
- Vedligeholdelse af lagerplads og software for at understøtte overholdelseskrav.
    
- Opgradering til en ny version af Exchange. Med Microsoft 365 bruger du altid den nyeste version af Exchange.
    
#### <a name="how-should-i-migrate-to-microsoft-365"></a>Hvordan skal jeg overføre til Microsoft 365?

Du har et par overførselsmuligheder. Du skal overveje et par ting, herunder:

- Antallet af pladser eller postkasser, du skal flytte.
- Hvor længe du ønsker, at overførslen skal vare.
- Uanset om du har brug for problemfri integration mellem din lokale installation og Microsoft 365 under overførslen.

Denne tabel viser dine overførselsmuligheder og de vigtigste faktorer, der bestemmer, hvilken metode du skal bruge:
  

|**Overførselsmulighed**|**Organisationens størrelse**|**Varighed**|
|:-----|:-----|:-----|
|Cutover migration  <br/> |Færre end 150 pladser  <br/> |En uge eller mindre  <br/> |
|Faseind faseindret migrering  <br/> |Mere end 150 pladser  <br/> |Et par uger  <br/> |
|Fuld hybridoverførsel  <br/> |Flere hundrede til tusindvis af pladser  <br/> |Et par måneder eller mere  <br/> |
   
De følgende afsnit indeholder en oversigt over disse metoder. Få mere at vide under [Beslut dig for en overførselsti](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27). 
  
#### <a name="cutover-migration"></a>Cutover migration

I en cutover-migrering overfører du alle dine postkasser, distributionsgrupper, kontakter osv., for at Microsoft 365 på et forhåndsvalgt dato og klokkeslæt. Når overførslen er fuldført, lukker du dine lokale servere Exchange begynde at bruge Microsoft 365 udelukkende.
  
Den gratis migrering er god til små organisationer, der ikke har mange postkasser, ønsker at få hurtig adgang til Microsoft 365 og ikke ønsker at håndtere nogle af kompleksiteterne ved de andre metoder. Men det bør gennemføres om en uge eller mindre, og det kræver, at brugerne omkonfigurere deres Outlook profiler. Den gratis migrering kan håndtere op til 2.000 postkasser, men vi anbefaler på det kraftigste, at du bruger den til at overføre maksimalt 150 postkasser. Hvis du forsøger at overføre flere, kan du løbe tør for tid til at overføre alle postkasserne før din deadline, og dit it-supportpersonale kan blive overvældet af anmodninger om at hjælpe brugerne med at konfigurere Outlook.
  
Hvis du overvejer at udføre en migrering, skal du overveje følgende:
  
- Microsoft 365 skal oprette forbindelse til dine Exchange 2007-servere, der bruger Outlook over TCP-port 443.
    
- Alle lokale postkasser flyttes til Microsoft 365.
    
- Du skal bruge en lokal administratorkonto, der har læseadgang til dine brugeres postkasser.
    
- De Exchange 2007-accepterede domæner, du vil bruge i Microsoft 365, skal tilføjes som bekræftede domæner i tjenesten.
    
- Mellem tidspunktet, hvor du starter overførslen, og hvor du går i gang med fuldførelsesfasen, Microsoft 365 med jævne mellemrum Microsoft 365 postkasserne og de lokale postkasser. Dette giver dig mulighed for at fuldføre overførslen uden at bekymre dig om mails, der efterlades i dine lokale postkasser.
    
- Brugerne modtager nye midlertidige adgangskoder til deres Microsoft 365 konti. De skal ændre deres adgangskode, når de logger på deres postkasse for første gang.
    
- Du skal bruge en Microsoft 365, der omfatter Exchange Online for hver brugerpostkasse, du overfører.
    
- Brugerne skal konfigurere en ny profil til Outlook på hver af deres enheder og hente deres mail igen. Mængden af mails, Outlook downloadet, kan variere. Du kan finde flere oplysninger under [Ændre, hvor mange mails, der bevares offline](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Du kan finde flere oplysninger om den gratis migrering i:
  
- [Hvad du bør vide om en migrering af en mail](https://support.office.com/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [Udfør en migrering af mail](https://support.office.com/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="staged-migration"></a>Faseind faseindret migrering

I en faseinddelt migrering har du et par hundrede eller et par tusinde postkasser, du vil overføre til Microsoft 365, har brug for at tage en uge eller mere for at fuldføre overførslen og har ikke brug for nogen avancerede hybridoverførselsfunktioner som f.eks. delte ledig/optaget-kalenderoplysninger.
  
Faseind faseindret migrering er god for organisationer, der har brug for mere tid til at overføre deres postkasser til Microsoft 365 men stadig planlægger at fuldføre overførslen inden for et par uger. Du kan overføre postkasser i batches. Du styrer, hvor mange og hvilke postkasser der overføres på et givet tidspunkt. Du kan f.eks. batche postkasser af brugere i den samme afdeling for at sikre, at de alle flyttes på samme tid. Eller du kan lade ledelsens postkasser være tilbage til det sidste batch. Ligesom med de samme migreringer skal brugerne genoprette deres Outlook profiler.
  
Hvis du overvejer at udføre en faseind faseindret migrering, skal du overveje følgende:
  
- Microsoft 365 skal oprette forbindelse til dine Exchange 2007-servere ved hjælp af Outlook hvor som helst via TCP-port 443.
    
- Du skal bruge en lokal administratorkonto, der har læseadgang til dine brugeres postkasser.
    
- Den Exchange 2007-accepterede domæner, som du planlægger at bruge i Microsoft 365, skal tilføjes som bekræftede domæner i tjenesten.
    
- Du skal oprette en CSV-fil med det fulde navn og mailadressen til hver postkasse, som du planlægger at overføre i en batch. Du skal også medtage en ny adgangskode for hver postkasse, du overfører, og sende adgangskoden til hver enkelt bruger. Brugeren bliver bedt om at ændre adgangskoden, første gang der logges på den nye Microsoft 365 postkasse.
    
- Mellem tidspunktet, hvor du starter overførselsbatchen, og hvor du går i gang med fuldførelsesfasen, synkroniserer Microsoft 365 med jævne mellemrum Microsoft 365-postkasser og lokale postkasser, der er inkluderet i batchen. Dette giver dig mulighed for at fuldføre overførslen uden at bekymre dig om mails, der efterlades i dine lokale postkasser.
    
- Du skal bruge en Microsoft 365, der omfatter Exchange Online for hver brugerpostkasse, du overfører.
    
- Brugerne skal konfigurere en ny profil til Outlook på hver af deres enheder og hente deres mail igen. Mængden af mails, Outlook downloadet, kan variere. Du kan finde flere oplysninger under [Ændre, hvor mange mails, der bevares offline](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Du kan finde flere oplysninger om faseinddeinddeindteret migrering under:
  
- [Hvad du bør vide om en faseindret migrering af mail](https://support.office.com/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)
    
- [Udføre en faseindindret migrering af mail](https://support.office.com/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)
    
#### <a name="full-hybrid"></a>Fuld hybrid

I en fuld hybridoverførsel har din organisation mange hundredvis, op til titusindvis af postkasser, og du vil flytte nogle eller dem alle til Microsoft 365. Da disse migrering typisk er langsigtede, gør hybridoverførsel det muligt at:
  
- Vis lokale brugere oplysninger om ledig/optaget-kalender for brugere i Microsoft 365 og omvendt.
    
- Se en samlet global adresseliste, der indeholder modtagere både lokalt og Microsoft 365.
    
- Få vist Outlook egenskaber for modtagere for alle brugere, uanset om de er lokale eller Microsoft 365.
    
- Sikre mailkommunikation mellem lokale servere og Exchange og Microsoft 365 ved hjælp af TLS og certifikater.
    
- Behandle meddelelser, der sendes mellem lokale servere Exchange og Microsoft 365 som interne, så de kan:
    
  - Korrekt evalueres og behandles af transport- og overholdelsesagenter målrettet mod interne meddelelser.
    
  - Omgå antispamfiltre.
    
Fuld hybridoverførsel er bedst til organisationer, der forventer at forblive i en hybridkonfiguration i mange måneder eller mere. Du får funktionerne angivet tidligere i dette afsnit samt katalogsynkronisering, bedre integrerede overholdelsesfunktioner og muligheden for at flytte postkasser til og fra Microsoft 365 ved hjælp af onlinepostkasse flytter. Microsoft 365 bliver en udvidelse af din lokale organisation.
  
Hvis du overvejer at udføre en fuld hybridoverførsel, skal du overveje følgende:
  
- Fuld hybridoverførsel er ikke egnet til alle typer organisationer. På grund af kompleksiteten ved fulde hybrid-migrering, ser organisationer med mindre end et par hundrede postkasser typisk ikke fordele, der berettiger den nødvendige indsats og de nødvendige omkostninger til at oprette en. Hvis det lyder som din organisation, anbefaler vi, at du i stedet overvejer en migrering eller faseindret migrering.
    
- Du skal installere mindst én Exchange 2013-server i din Exchange 2007-organisation for at fungere som en "hybridserver". Denne server kommunikerer med Microsoft 365 på vegne af dine Exchange 2007-servere.
    
- Microsoft 365 skal oprette forbindelse til "hybridserveren", der bruger Outlook over TCP-port 443.
    
- Du skal konfigurere katalogsynkronisering med Azure Active Directory (Azure AD) Forbind mellem dine lokale Active Directory-servere og Microsoft 365.
    
- Brugerne vil kunne logge på deres Microsoft 365-postkasse med samme brugernavn og adgangskode, som når de logger på det lokale netværk. (Denne funktionalitet kræver Azure AD-Forbind adgangskodesynkronisering og/eller Active Directory Federation Services).
    
- Du skal bruge en Microsoft 365, der omfatter Exchange Online for hver brugerpostkasse, du overfører.
    
- Brugere behøver ikke at konfigurere en ny profil Outlook på de fleste af deres enheder, selvom nogle ældre Android-telefoner muligvis skal bruge en ny profil. Brugerne behøver ikke at downloade deres mail igen.
    
Hvis en fuld hybridoverførsel lyder som den rigtige for dig, kan du se følgende ressourcer, der kan hjælpe dig med overførslen:
  
- [Exchange installationsassistent](/exchange/exchange-deployment-assistant)
    
- [Exchange Server hybridinstallationer](/exchange/exchange-hybrid)
    
- [Guiden Hybridkonfiguration](/exchange/hybrid-configuration-wizard)
    
- [Ofte stillede spørgsmål til guiden Hybridkonfiguration](/exchange/hybrid-configuration-wizard-faqs)
    
- [Forudsætninger for hybridinstallation](/exchange/hybrid-deployment-prerequisites)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>Overfør til en nyere version af Exchange Server

Vi er stærkt overbeviste om, at du kan opnå den bedste værdi og brugeroplevelse ved at overføre Microsoft 365. Men vi forstår også, at nogle organisationer har brug for at bevare deres mail lokalt. Dette kan skyldes lovmæssige krav for at garantere, at data ikke er gemt i et datacenter i et andet land eller lignende. Hvis du vælger at bevare din mail i det lokale miljø, kan du overføre dit Exchange 2007-miljø til Exchange 2010, Exchange 2013 eller Exchange 2016.
  
Hvis du ikke kan overføre til Microsoft 365, anbefaler vi, at du overfører til Exchange 2016. Exchange 2016 indeholder alle funktionerne fra tidligere versioner af Exchange. Den passer også bedst til den oplevelse, der er Microsoft 365, selvom visse funktioner kun er tilgængelige i Microsoft 365. Se blot nogle af de ting, du har manglet:
  
|**Exchange udgivelse**|**Funktioner**|
|:-----|:-----|
|Exchange 2010  <br/> | Role-Based Access Control (tilladelser uden ACL'er)  <br/>  Outlook Web App postkassepolitikker  <br/>  Mulighed for at dele ledig/optaget tid og uddelegere kalendere mellem organisationer  <br/> |
|Exchange 2013  <br/> | *Funktioner fra Exchange 2010 og ...*  <br/>  Forenklet arkitektur, der reducerede antallet af serverroller til tre (postkasse, klientadgang, Edge-transport)  <br/>  Politikker til forebyggelse af datatab (DLP), der hjælper med at beskytte mod lækage af følsomme oplysninger  <br/>  Forbedret Outlook Web App oplevelse  <br/> |
|Exchange 2016  <br/> | *Funktioner fra Exchange 2013 og ...*  <br/>  Yderligere forenklede serverroller kun til postkasse og Edge-transport  <br/>  Forbedret DLP samt integration med SharePoint  <br/>  Forbedret databaserobusthed  <br/>  Online dokumentsamarbejde |
   
#### <a name="which-version-should-i-migrate-to"></a>Hvilken version skal jeg overføre til?

Vi anbefaler, at du først antager, at du vil overføre Exchange 2016. Brug derefter følgende oplysninger til at bekræfte din antagelse eller udelukke Exchange 2016. Hvis du af en eller anden grund ikke kan overføre til Exchange 2016, skal du udføre den samme proces med Exchange 2013 osv.
  
|**Overvejelse**|**Flere oplysninger**|
|:-----|:-----|
|Slutdato for support  <br/> | Ligesom Exchange 2007 har hver Exchange sin egen slutdato for support:  <br/> *Exchange 2010* – januar 2020  <br/> *Exchange 2013* – april 2023  <br/> *Exchange 2016* – oktober 2025  <br/>  Jo tidligere slutdato for support, jo tidligere skal du udføre en anden overførsel.<br/> |
|Overførselssti til Exchange 2010 og 2013.  <br/> |Her er de generelle faser for overførsel til Exchange 2010 eller Exchange 2013:  <br/> - Installere Exchange 2010 eller 2013 i din eksisterende Exchange 2007-organisation. <br/>- Flytte tjenester og anden infrastruktur til Exchange 2010 eller 2013.<br/>- Flyt postkasser og offentlige mapper til Exchange 2010 eller 2013.<br/>- Afvikle resterende Exchange 2007-servere. |
|Overførselssti til Exchange 2016  <br/> |Her er de generelle faser for overførsel til Exchange 2016:  <br/> - Installere Exchange 2013 i din eksisterende Exchange 2007-organisation.<br/>- Flytte tjenester og anden infrastruktur til Exchange 2013.<br/>- Flyt postkasser og offentlige mapper til Exchange 2013.<br/>- Afvikle resterende Exchange 2007-servere.<br/>- Installere Exchange 2016 i din eksisterende Exchange 2013-organisation.<br/>- Flyt postkasser, offentlige mapper, tjenester og anden infrastruktur til Exchange 2016 (rækkefølgen er ligegyldig). Afmeld resterende Exchange 2013-servere.<br/><br/> **Bemærk!** Det er nemt at Exchange fra Exchange 2013 til Exchange 2016. De to versioner har næsten de samme hardwarekrav, og disse versioner er meget kompatible. Så du kan genopbygge en server, du har købt til Exchange 2013 og Exchange 2016 på den. De fleste brugere bemærker ikke, at deres postkasse er blevet flyttet væk fra serveren og derefter tilbage igen, når du har genopbygget den med Exchange 2016.           |
|Versions coexistence  <br/> | Når du overfører til ...  <br/> **Exchange 2016:** Exchange 2016 kan ikke installeres i en organisation, der indeholder en Exchange 2007-server. Du skal først overføre til Exchange 2010 eller 2013 (vi anbefaler kraftigt Exchange 2013), fjerne alle Exchange 2007-servere og derefter overføre til Exchange 2016.  <br/> **Exchange 2010 eller Exchange 2013:** Du kan installere Exchange 2010 eller Exchange 2013 i en eksisterende Exchange 2007-organisation. Dette giver dig mulighed for at installere en eller flere Exchange 2010- eller 2013-servere og udføre overførslen.  <br/> |
|Serverhardware  <br/> | Krav til serverhardware har ændret sig Exchange 2007. Sørg for, at din hardware er kompatibel. Du kan finde flere oplysninger i:  <br/> [Exchange 2016-systemkrav](/Exchange/plan-and-deploy/system-requirements) <br/> [Exchange 2013-systemkrav](/exchange/exchange-2013-system-requirements-exchange-2013-help) <br/> [Exchange 2010-systemkrav](/previous-versions/office/exchange-server-2010/aa996719(v=exchg.141)) <br/>  Du vil opdage, at de betydelige forbedringer af ydeevnen i Exchange og den øgede computerkraft og lagerkapacitet i nyere servere betyder, at du sandsynligvis har brug for færre servere til at understøtte det samme antal postkasser.  <br/> |
|Version af operativsystem  <br/> | De understøttede minimumsversioner af operativsystemer for hver version er:  <br/> **Exchange 2016** – Windows Server 2012  <br/> **Exchange 2013** – Windows Server 2008 R2 SP1  <br/> **Exchange 2010** – Windows Server 2008 SP2  <br/>  Du kan finde flere oplysninger om understøttelse af operativsystem [Exchange Supportability Matrix](/Exchange/plan-and-deploy/supportability-matrix).  <br/> |
|Funktionsniveau for Active Directory-skoven  <br/> | De understøttede minimumsfunktionsniveauer for Active Directory-skoven for hver version er:  <br/> **Exchange 2016** Windows Server 2008 R2 SP1  <br/> **Exchange 2013** Windows Server 2003  <br/> **Exchange 2010** Windows Server 2003  <br/>  Du kan finde flere oplysninger om understøttelse af skovens funktionsniveau [Exchange Supportability Matrix](/Exchange/plan-and-deploy/supportability-matrix).  <br/> |
|Office klientversioner  <br/> | De understøttede minimums Office klientversioner for hver version er:  <br/> **Exchange 2016** – Office 2010 (med de seneste opdateringer)  <br/> **Exchange 2013** – Office 2007 SP3  <br/> **Exchange 2010** – Office 2003  <br/>  Du kan finde flere oplysninger Office klientsupport [på Exchange Supportability Matrix](/Exchange/plan-and-deploy/supportability-matrix).  <br/> |
   
#### <a name="how-do-i-migrate"></a>Hvordan overfører jeg?

Hvis du beslutter dig for at beholde din mail lokalt, kan du bruge følgende ressourcer til at hjælpe med din overførsel:
  
- [Exchange installationsassistent](/exchange/exchange-deployment-assistant)
    
- Active Directory-skemaændringer Exchange [2016](/Exchange/plan-and-deploy/active-directory/ad-schema-changes), [2013](/exchange/exchange-2013-active-directory-schema-changes-exchange-2013-help), [2010](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)
    
- Systemkrav til Exchange [2016](/Exchange/plan-and-deploy/system-requirements), [2013](/exchange/exchange-2013-system-requirements-exchange-2013-help), [2010](/previous-versions/office/exchange-server-2010/aa996719(v=exchg.141))
    
- Forudsætninger for Exchange [2016](/Exchange/plan-and-deploy/prerequisites), [2013](/exchange/exchange-2013-prerequisites-exchange-2013-help), [2010](/previous-versions/office/exchange-server-2010/bb691354(v=exchg.141))
    
## <a name="get-help"></a>Få hjælp

Hvis du overfører til en Microsoft 365, er du muligvis berettiget til at bruge vores Microsoft FastTrack-tjeneste. FastTrack giver de bedste fremgangsmåder, værktøjer og ressourcer til at gøre din overførsel Microsoft 365 så problemfri som muligt. Det bedste er, at en supporttekniker hjælper dig gennem din overførsel fra planlægning og design hele vejen til overførsel af din sidste postkasse. Du kan finde flere FastTrack i [Microsoft FastTrack](https://fasttrack.microsoft.com/).
  
Hvis du løber ind i problemer under din overførsel til Microsoft 365, og du ikke bruger FastTrack eller din overførsel til en nyere version af Exchange Server, er vi klar til at hjælpe. Her er nogle ressourcer, du kan bruge:
  
- [Teknisk community](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
    
- [Kundesupport](https://support.microsoft.com/gp/support-options-for-business)
    
## <a name="related-topics"></a>Relaterede emner

[Ressourcer, der kan hjælpe dig med at opgradere dine Office 2007 servere og -klienter](upgrade-from-office-2007-servers-and-products.md)