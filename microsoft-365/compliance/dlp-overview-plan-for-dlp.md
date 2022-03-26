---
title: Plan for forebyggelse af datatab
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Oversigt over planlægningsprocessen til forebyggelse af datatab
ms.openlocfilehash: c695a6a2a4bd21a147e5e81bc73fb65ab1378960
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63595941"
---
# <a name="plan-for-data-loss-prevention-dlp"></a>Plan for forebyggelse af datatab (DLP)

Hver organisation planlægger og implementerer forebyggelse af datatab (DLP) forskelligt, fordi alle organisationers forretningsmæssige behov, mål, ressourcer og situation er unikke for dem. Der er dog elementer, der er fælles for alle vellykkede DLP-implementeringer. I denne artikel beskrives de bedste fremgangsmåder, der bruges af organisationer i deres DLP-planlægning.

## <a name="multiple-starting-points"></a>Flere udgangspunkter

Mange organisationer vælger at implementere DLP for at overholde forskellige statslige love og forordninger. Det kan f.eks. være EU's generelle forordning om databeskyttelse (GDPR) eller HIPAA (Health Insurance Portability and Accountability Act) eller CCPA (California Consumer Privacy Act). De implementerer også forebyggelse af datatab for at beskytte deres immaterielle ejendom. Men udgangspunktet og den ultimative destination på DLP-rejsen varierer. 

Organisationer kan starte deres DLP-rejse:

- fra en platform som f.eks. gerne vil beskytte oplysninger Teams chat- og kanalmeddelelser eller på Windows 10-enheder
- at vide hvilke følsomme oplysninger, de ønsker at prioritere i beskyttelsen, f.eks. sundhedsjournaler, og gå direkte til at definere politikker for at beskytte dem
- uden at vide, hvad deres følsomme oplysninger er, hvor de er, og hvem der gør hvad med dem, så de begynder med opdagelse og kategorisering og tager en mere metodisk tilgang
- uden at vide, hvad deres følsomme oplysninger er, hvor de er, eller hvem der gør hvad med dem, men de går direkte til at definere politikker og bruge disse resultater som udgangspunkt og derefter finjustere deres politikker derfra
- velvidende at de skal implementere den komplette Microsoft 365 Information Protection-stakken og ønsker således at tage en langsigtet, metodisk tilgang

Dette er blot nogle eksempler på, hvordan kunderne kan gribe DLP til og det er ligegyldigt, hvor du starter fra, Microsoft 365 DLP er fleksibelt nok til at kunne tage højde for forskellige typer af foranstaltninger til beskyttelse af oplysninger fra start til en fuldt ud klar strategi til forebyggelse af datatab. 

## <a name="overview-of-planning-process"></a>Oversigt over planlægningsprocessen

Med [Få mere at vide om forebyggelse](dlp-learn-about-dlp.md#learn-about-data-loss-prevention) af datatab introduceres de tre forskellige aspekter af [DLP-planlægningsprocessen](dlp-learn-about-dlp.md#plan-for-dlp). Vi går i detaljer her om de elementer, der er fælles for alle DLP-planer.

### <a name="identify-stakeholders"></a>Identificere interessenter

Når DLP-politikker er implementeret, kan de anvendes på tværs af store dele af organisationen. It-løsninger kan ikke udvikle en bred plan alene uden negative konsekvenser. Du skal identificere interessenterne, som kan:

- beskrive de bestemmelser, love og branchestandarder, din organisation er underlagt
- kategorierne for følsomme elementer, der skal beskyttes
- de forretningsprocesser, de bruges i
- den risikabel adfærd, der bør være begrænset
- prioritere, hvilke data der skal beskyttes først baseret på følsomheden af de elementer og risici, der er involveret
- skitsere DLP-politik for gennemgang og afhjælpningsproces for matchning af begivenheder 
 
Generelt har disse behov for at være 85 % lovgivningsmæssig og overholdelsesbeskyttelse og 15 % intellektuel ejendomsbeskyttelse. Her er nogle forslag til roller, der skal medtages i din planlægningsproces:

- Lovgivnings- og overholdelsesmedarbejdere
- Chief Risk Officer
- Juridiske medarbejdere
- Sikkerheds- og overholdelsesmedarbejdere
- Virksomhedsejere for dataelementerne
- Virksomhedsbrugere
- IT

### <a name="describe-the-categories-of-sensitive-information-to-protect"></a>Beskriv kategorierne for følsomme oplysninger, der skal beskyttes

Interessenterne beskriver derefter kategorierne for følsomme oplysninger, der skal beskyttes, og den forretningsproces, de bruges i. Eksempelvis definerer Microsoft 365 DLP disse kategorier:

- Finansiel 
- Medicinske og sundhedsoplysninger
- Beskyttelse af personlige oplysninger
- Brugerdefineret

Interessenterne kan identificere de følsomme oplysninger som "Vi er dataprocessor, så vi er nødt til at implementere beskyttelse af personlige oplysninger på oplysninger fra den registrerede og økonomiske oplysninger".

 
  <!-- The business process is important as it informs the ‘data at rest’, ‘data in transit’, ‘data in use’ aspect of DLP planning and who should be sharing the items and who should not.-->

### <a name="set-goals-and-strategy"></a>Angiv mål og strategi

Når du har identificeret dine interessenter, og du ved, hvilke følsomme oplysninger der skal beskyttes, og hvor de bruges, kan interessenterne sætte deres beskyttelsesmål, og it-it kan udarbejde en implementeringsplan. 


 <!--
### Discovery
 for the locations (DLP workloads) of these types of items.  (mapping DLP locations and data at rest, data in transit, data in use)

### IT can start coding test policies
start small and always in test mode. Note that DLP policies can feed into insider risk.

### Business process owners help with tuning
 false positive/false negative results and fitting DLP into their business processes.

-->

### <a name="set-implementation-plan"></a>Angiv implementeringsplan

Din implementeringsplan bør omfatte:

- Tilknytning af din starttilstand og den ønskede sluttilstand og trinnene til at få adgang til den ene og den anden
- sådan adresserer du registrering af følsomme elementer
- planlægning af politikker og den rækkefølge, de skal implementeres i
- sådan adresserer du eventuelle forudsætninger
- planlægning af, hvordan politikker først skal testes, før der arbejdes videre med håndhævelsen
- sådan oplærer du dine slutbrugere
- sådan tester og finjusterer du dine politikker
- hvordan du vil gennemgå og opdatere din strategi til forebyggelse af datatab baseret på ændring af lovgivning, juridiske, branchestandarder eller immaterielle rettigheder og forretningsmæssige behov

#### <a name="map-out-path-from-start-to-desired-end-state"></a>Tilknyt sti fra start til ønsket sluttilstand

Det er vigtigt at dokumentere, hvordan organisationen kommer fra start- til sluttilstanden, for at kunne kommunikere med dine interessenter og angive projektets omfang. Her er et sæt trin, der ofte bruges til at udrulle DLP. Du skal have flere detaljer end dette, men du kan bruge dette til at indramme din DLP-indføringssti.

![grafik, der viser en fælles rækkefølge for implementering af DLP.](../media/dlp-deployment-planning.png)

#### <a name="sensitive-item-discovery"></a>Registrering af følsomme elementer

Der er flere måder at finde ud af, hvad individuelle følsomme elementer er, og hvor de er placeret. Du har måske allerede implementeret følsomhedsmærkater, eller du kan have besluttet at implementere en bred DLP-politik på alle placeringer, der kun opdager og overvåger elementer. Du kan få mere at vide under [Kende dine data](information-protection.md#know-your-data).

#### <a name="policy-planning"></a>Planlægning af politikker

Når du starter din DLP-indføring, kan du bruge disse spørgsmål til at fokusere dit politikdesign og dine implementeringsindsatser.

##### <a name="what-laws-regulations-and-industry-standards-must-your-organization-comply-with"></a>Hvilke love, bestemmelser og branchestandarder skal organisationen overholde?

Da mange organisationer kommer til DLP med det formål at overholde lovgivningen, er besvarelse af dette spørgsmål et naturligt udgangspunkt for planlægning af din DLP-implementering. Men som IT-implementerer er du sandsynligvis ikke placeret til at besvare den. Det skal besvares af dit juridiske team og ledere. 
 
**Eksempel** Din organisation er underlagt Storbritannien finansielle bestemmelser.


##### <a name="what-sensitive-items-does-your-organization-have-that-must-be-protected-from-leakage"></a>Hvilke følsomme elementer har din organisation, der skal være beskyttet fra lækage?

Når din organisation ved, hvor den står med hensyn til lovmæssige overholdelsesbehov, får du en ide om, hvilke følsomme elementer der skal beskyttes fra lækage, og hvordan du vil prioritere implementering af politikker for at beskytte dem. Dette hjælper dig med at vælge de mest passende DLP-politikskabeloner. Microsoft 365 leveres med forudkonfigurerede DLP-skabeloner til finansiel, medicinsk og tilstand, beskyttelse af personlige oplysninger, og du kan oprette dine egne ved hjælp af den brugerdefinerede skabelon. Når du designer og opretter dine faktiske DLP-politikker, vil det at kende svaret på dette spørgsmål også hjælpe dig med at vælge den [rigtige type af følsomme oplysninger](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).

**Eksempel** For at komme hurtigt i gang skal du vælge `U.K. Financial Data` politikskabelonen, som omfatter `Credit Card Number`, og `EU Debit Card Number`følsomme `SWIFT Code` oplysningstyper. 

##### <a name="where-are-the-sensitive-items-and-what-business-processes-are-they-involved-in"></a>Hvor er de følsomme elementer og hvilke forretningsprocesser de er involveret i?

De elementer, der indeholder dine organisationers følsomme oplysninger, bruges hver dag i løbet af en forretning. Du skal vide, hvor forekomster af disse følsomme oplysninger kan forekomme, og hvilke forretningsprocesser de bruges i. Dette vil hjælpe dig med at vælge de rigtige steder at anvende dine DLP-politikker på. Microsoft 365 DLP-politikker anvendes på placeringer:

- Exchange mail
- SharePoint websteder
- OneDrive konti
- Teams chat og kanalmeddelelser
- Windows 10 enheder
- Microsoft Defender til skyapps
- Lokale lagre

**Eksempel** Din organizations interne revisorer sporer et sæt kreditkortnumre. De opbevarer et regneark med dem på et sikkert SharePoint websted. Flere af medarbejderne laver kopier og gemmer dem på deres arbejdswebsted, OneDrive for Business, som synkroniseres med deres Windows 10 enhed. En af dem indsætter en liste over 14 af dem i en mail og forsøger at sende den til eksterne revisorer til gennemsyn. Du ønsker at anvende politikken på det sikre SharePoint-websted, alle interne revisorer OneDrive for Business konti, deres Windows 10 enheder og Exchange mail.

##### <a name="what-is-your-organizations-tolerance-for-leakage"></a>Hvad er din organizations tolerance for lækage?

Forskellige grupper i organisationen kan have forskellige visninger af, hvad der er et acceptabelt niveau af lækage af følsomme elementer, og hvad der ikke gør. Det kan medføre for høje omkostninger for virksomheden at opnå nullækage.

**Eksempel** Din organisations sikkerhedsgruppe mener begge sammen med det juridiske team, at der ikke skal være nogen deling af kreditkortnumre med nogen uden for organisationen og lækage på nul lækage. Men som en del af den regelmæssige gennemgang af kreditkortnummeraktiviteten skal de interne revisorer dele nogle kreditkortnumre med tredjepartsrevisorer. Hvis din DLP-politik forhindrer al deling af kreditkortnumre uden for organisationen, vil der være betydelige afbrydelser af forretningsprocessen og ekstra omkostninger for at afhjælpe afbrydelserne, så de interne revisorer kan fuldføre deres sporing. Denne ekstra omkostning er uacceptabel for ledelsen. For at løse dette skal der være en intern samtale for at bestemme et acceptabelt niveau af lækage. Når det er besluttet, kan politikken give undtagelser for visse personer til at dele oplysningerne, eller den kan kun anvendes i overvågningstilstand.

#### <a name="planning-for-prerequisites"></a>Planlægning af forudsætninger

Før du kan overvåge nogle DLP-placeringer, er der forudsætninger, der skal være opfyldt. Se **afsnittene Inden** du går i gang af:

- [Introduktion til forebyggelse af datatab lokalt (eksempel)](dlp-on-premises-scanner-get-started.md#before-you-begin)
- [Kom i gang med forebyggelse af datatab på slutpunkt](endpoint-dlp-getting-started.md#before-you-begin)
- [Kom i gang med Microsoft-udvidelsen til overholdelse af regler og standarder (preview)](dlp-chrome-get-started.md#before-you-begin)
- [Brug politikker til forebyggelse af datatab til ikke-Microsoft-skyapps (forhåndsvisning)](dlp-use-policies-non-microsoft-cloud-apps.md#before-you-begin)

#### <a name="policy-deployment"></a>Installation af politik

Når du opretter dine DLP-politikker, bør du overveje at udrulle dem gradvist for at vurdere deres virkning og teste deres effektivitet, før de håndhæves fuldt ud. Du ønsker f.eks. ikke, at en ny DLP-politik utilsigtet blokerer adgangen til tusindvis af dokumenter eller at bryde en eksisterende forretningsproces.
  
Hvis du opretter DLP-politikker med stor potentiel virkning, anbefaler vi, at du følger denne rækkefølge:
  
1. **Start i testtilstand uden politik Tips** og brug derefter DLP-rapporterne og eventuelle hændelsesrapporter til at vurdere påvirkningen. Du kan bruge DLP-rapporter til at få vist antal, placering, type og alvorsgrad for politik match. Baseret på resultaterne kan du finjustere politikkerne efter behov. I testtilstand påvirker DLP-politikker ikke produktiviteten for personer, der arbejder i organisationen. Brug også denne fase til at teste arbejdsprocessen for gennemgang af DLP-hændelser og afhjælpning af problemer.
    
2. **Gå til testtilstand** med meddelelser og politik Tips så du kan begynde at lære brugerne om dine politikker for overholdelse af regler og standarder og forberede dem til de politikker, der skal anvendes. Det er nyttigt at have et link til en side med organisationspolitik, der indeholder flere oplysninger om politikken i politiktip. På dette tidspunkt kan du også bede brugerne om at rapportere falske positive, så du kan finjustere politikkerne yderligere. Gå til denne fase, når du har tillid til, at resultaterne af politikprogrammet stemmer overens med dem, de interessenter havde i tankerne. 
    
3. **Begynd fuld håndhævelse af politikkerne** , så handlingerne i reglerne anvendes og indholdet beskyttes. Fortsæt med at overvåge DLP-rapporter og eventuelle hændelsesrapporter eller -meddelelser for at sikre, at resultaterne er, som du regner med. 

    ![Indstillinger for brug af testtilstand og aktivering af politik.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

    Du kan til enhver tid deaktivere en DLP-politik, hvilket påvirker alle regler i politikken. Men hver regel kan også deaktiveres enkeltvis ved at slå dens status fra i regeleditoren.

    ![Indstillinger for de deaktivere en regel i en politik.](../media/f7b258ff-1b8b-4127-b580-83c6492f2bef.png)

    Du kan også ændre prioriteten af flere regler i en politik. Det gør du ved at åbne en politik til redigering. Vælg ellipserne (**...**) i en række for en regel, og vælg derefter en indstilling, f.eks. Flyt **ned** eller **Flyt til sidst**.

    ![Angiv regelprioritet.](../media/dlp-set-rule-priority.png)

#### <a name="end-user-training"></a>Kurser til slutbrugere

Når der udløses en DLP-politik, kan du konfigurere dine politikker til at Sende mailmeddelelser og vise politiktip til [DLP-politikker](use-notifications-and-policy-tips.md#send-email-notifications-and-show-policy-tips-for-dlp-policies) til administratorer og slutbrugere. Mens dine politikker stadig er i testtilstand, og før de er indstillet til at gennemtvinge en blokering, er politiktip nyttige måder til at skabe opmærksomhed om risikabel adfærd på følsomme elementer og oplære brugere for at undgå disse funktionsmåder i fremtiden.  

#### <a name="review-dlp-requirements-and-update-strategy"></a>Gennemgå DLP-krav og opdateringsstrategi

De bestemmelser, love og branchestandarder, din organisation er underlagt, ændres med tiden, og dine forretningsmål for DLP vil også blive ændret. Sørg for at medtage regelmæssig gennemgang af alle disse områder, så din organisation overholder de gældende regler og standarder, og din DLP-implementering fortsat opfylder virksomhedens behov.

## <a name="approaches-to-deployment"></a>Metoder til udrulning

|Beskrivelse af kundeforretningens behov  | fremgangsmåde  |
|---------|---------|
|**Contoso Bank** er i en meget regulerede branche og har mange forskellige typer af følsomme elementer mange forskellige steder. </br> - ved, hvilke typer af følsomme oplysninger der har topprioritet. </br> - skal minimere afbrydelser i virksomheden, efterhånden som politikker udrulles. </br> - har it-ressourcer og kan ansætte eksperter til at hjælpe med at planlægge, designe installationen </br> - har en Premier-supportkontrakt med Microsoft| - Tag dig tid til at forstå, hvilke bestemmelser de skal overholde, og hvordan de skal overholde. </br> -Tag dig tid til at forstå den bedre samlede værdi af Microsoft 365 Information Protection-stakken </br> - Udvikle følsomhedsmærkatskema til prioriterede elementer og anvende </br> - Involvere ejere af forretningsproces </br>- Design/kodepolitikker, installation i testtilstand, oplære brugere </br>- gentag|
|**TailSpin Toys** ved ikke, hvad det har, eller hvor det er, og har kun få eller ingen ressource dybde. De bruger Teams, OneDrive for Business og Exchange i stor grad.     |- Start med simple politikker for de prioriterede placeringer. </br>- Overvåge, hvad der bliver identificeret </br>- Anvend følsomhedsmærkater tilsvarende </br>- Tilpas politikker, træn brugere       |
|**Fabrikam** er en lille opstarts-virksomhed og ønsker at beskytte sin immaterielle ejendom og skal hurtigt komme i gang. De er villig til at dedikere nogle ressourcer, men de har ikke råd til at ansætte eksterne eksperter. </br>- Følsomme elementer findes alle i Microsoft 365 OneDrive for Business/SharePoint </br>- Indføring af OneDrive for Business og SharePoint er langsom, medarbejdere/skygge IT bruger DropBox og Google drev til at dele/gemme elementer </br>- Medarbejdere sætter pris på hastigheden af deres arbejde over databeskyttelsesdisciplinen </br>- Kunden splurged og købte alle 18 medarbejdere nyt Windows 10 enheder     |- Udnyt DLP-standardpolitikken i Teams </br>- Brug begrænset af standardindstillingen for SharePoint elementer </br>- Installere politikker, der forhindrer ekstern deling </br>- Installere politikker for at prioritere placeringer </br>- Implementer politikker på Windows 10 enheder </br>- Bloker overførsler til ikke-OneDrive for Business skylager      |

<!--

## Planning for workloads

### Exchange

### SharePoint

### OneDrive for Business

### Teams

### Windows 10 Devices

### Microsoft Cloud App Security (MCAS)

### On-premises Scanner
-->

## <a name="see-also"></a>Se også
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
