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
description: Oversigt over planlægningsprocessen for forebyggelse af datatab
ms.openlocfilehash: afda017b2cc627876134888a83f70e9464aba2c8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634439"
---
# <a name="plan-for-data-loss-prevention-dlp"></a>Plan for forebyggelse af datatab (DLP)

Hver organisation planlægger og implementerer DLP (forebyggelse af datatab) forskelligt, fordi hver organisations forretningsmæssige behov, mål, ressourcer og situation er unikke for dem. Der er dog elementer, der er fælles for alle vellykkede DLP-implementeringer. Denne artikel præsenterer de bedste fremgangsmåder, der bruges af organisationer i deres DLP-planlægning.

## <a name="multiple-starting-points"></a>Flere startpunkter

Mange organisationer vælger at implementere DLP for at overholde forskellige statslige eller brancheregler. F.eks. EU's generelle forordning om databeskyttelse (GDPR) eller HIPAA (Health Insurance Portability and Accountability Act) eller CCPA (California Consumer Privacy Act). De implementerer også forebyggelse af datatab for at beskytte deres intellektuelle ejendomsrettigheder. Men startstedet og den ultimative destination på DLP-rejsen varierer. 

Organisationer kan starte deres DLP-rejse:

- fra et platformfokus, f.eks. at ville beskytte oplysninger i Teams Chat- og Kanalmeddelelser eller på Windows 10 enheder
- at vide, hvilke følsomme oplysninger de ønsker at prioritere beskyttelse, f.eks. sundhedsjournaler, og gå direkte til at definere politikker for at beskytte dem
- uden at vide, hvad deres følsomme oplysninger er, hvor de er, og hvem der gør hvad med det, så de starter med opdagelse og kategorisering og tager en mere metodisk tilgang
- uden at vide, hvad deres følsomme oplysninger er, hvor de er, eller hvem der gør hvad med dem, men de vil gå direkte til at definere politikker og bruge disse resultater som udgangspunkt og derefter tilpasse deres politikker derfra
- ved at vide, at de har brug for at implementere hele Microsoft Purview Information Protection stakken og derfor har til hensigt at tage en længere, metodisk tilgang

Dette er blot nogle eksempler på, hvordan kunder kan nærme sig DLP, og det betyder ikke noget, hvor du starter fra, DLP er fleksibel nok til at imødekomme forskellige typer af informationsbeskyttelsesrejser fra start til en fuldt realiseret strategi til forebyggelse af datatab. 

## <a name="overview-of-planning-process"></a>Oversigt over planlægningsprocessen

[I Learn about Microsoft Purview Forebyggelse af datatab](dlp-learn-about-dlp.md#learn-about-data-loss-prevention) introduceres de tre forskellige aspekter af [DLP-planlægningsprocessen](dlp-learn-about-dlp.md#plan-for-dlp). Vi går mere i detaljer her om de elementer, der er fælles for alle DLP-planer.

### <a name="identify-stakeholders"></a>Identificer interessenter

Når de er implementeret, kan DLP-politikker anvendes på tværs af store dele af organisationen. It-virksomheden kan ikke selv udvikle en omfattende plan uden negative konsekvenser. Du skal identificere de interessenter, der kan:

- beskrive de forordninger, love og branchestandarder, som organisationen er underlagt
- kategorier af følsomme elementer, der skal beskyttes
- de forretningsprocesser, de bruges i
- den risikable adfærd, der bør begrænses
- prioriter, hvilke data der først skal beskyttes, baseret på følsomheden af de elementer og risici, der er involveret
- skitsere DLP-politikkens hændelsesgennemgangs- og afhjælpningsproces 
 
Generelt er der en tendens til, at disse behov er 85 % beskyttelse af lovgivning og overholdelse af angivne standarder og 15 % beskyttelse af intellektuel ejendomsret. Her er nogle forslag til roller, der skal medtages i din planlægningsproces:

- Forskrifts- og overholdelsesofficerer
- Chief Risk Officer
- Juridiske medarbejdere
- Sikkerheds- og overholdelsesofficerer
- Virksomhedsejere for dataelementerne
- Erhvervsbrugere
- DET

### <a name="describe-the-categories-of-sensitive-information-to-protect"></a>Beskriv kategorierne af følsomme oplysninger, der skal beskyttes

Interessenterne beskriver derefter kategorierne af følsomme oplysninger, der skal beskyttes, og den forretningsproces, de bruges i. DLP definerer f.eks. disse kategorier:

- Finansielle 
- Oplysninger om medicinsk og sundhed
- Beskyttelse af personlige oplysninger
- Brugerdefinerede

Interessenterne kan identificere de følsomme oplysninger som "Vi er databehandler, så vi er nødt til at implementere beskyttelse af personlige oplysninger om registreredes oplysninger og finansielle oplysninger".

 
  <!-- The business process is important as it informs the ‘data at rest’, ‘data in transit’, ‘data in use’ aspect of DLP planning and who should be sharing the items and who should not.-->

### <a name="set-goals-and-strategy"></a>Angiv mål og strategi

Når du har identificeret dine interessenter, og du ved, hvilke følsomme oplysninger der skal beskyttes, og hvor de bruges, kan interessenterne angive deres beskyttelsesmål, og it-administratoren kan udvikle en implementeringsplan. 


 <!--
### Discovery
 for the locations (DLP workloads) of these types of items.  (mapping DLP locations and data at rest, data in transit, data in use)

### IT can start coding test policies
start small and always in test mode. Note that DLP policies can feed into insider risk.

### Business process owners help with tuning
 false positive/false negative results and fitting DLP into their business processes.

-->

### <a name="set-implementation-plan"></a>Angiv implementeringsplan

Din implementeringsplan skal omfatte:

- Tilknytning af starttilstanden og den ønskede sluttilstand og de trin, du skal udføre for at komme fra den ene til den anden
- sådan håndterer du registrering af følsomme elementer
- planlægning og den rækkefølge, de skal implementeres i
- hvordan du skal håndtere eventuelle forudsætninger
- planlægning af, hvordan politikkerne først testes, før de går over til håndhævelse
- hvordan du vil oplære dine slutbrugere
- hvordan du tester og justerer dine politikker
- hvordan du gennemser og opdaterer din strategi til forebyggelse af datatab baseret på ændring af lovgivningsmæssige, juridiske, branchestandard- eller immaterielle rettigheder og forretningsbehov

#### <a name="map-out-path-from-start-to-desired-end-state"></a>Tilknyt stien fra start til den ønskede sluttilstand

Det er vigtigt at dokumentere, hvordan din organisation kommer fra starttilstanden til den ønskede sluttilstand, for at kommunikere med dine interessenter og angive projektomfanget. Her er en række trin, der ofte bruges til at installere DLP. Du vil gerne have flere detaljer end dette, men du kan bruge dette til at indramme din DLP-indføringssti.

![grafik, der viser den fælles rækkefølge for installation af DLP.](../media/dlp-deployment-planning.png)

#### <a name="sensitive-item-discovery"></a>Registrering af følsomme elementer

Der er flere måder at finde ud af, hvilke individuelle følsomme elementer der er, og hvor de er placeret. Du har muligvis allerede udrullet følsomhedsmærkater, eller du har muligvis besluttet at udrulle en bred DLP-politik på alle placeringer, der kun registrerer og overvåger elementer. Du kan få mere at vide under [Kend dine data](information-protection.md#know-your-data).

#### <a name="policy-planning"></a>Politikplanlægning

Når du begynder at indføre DLP, kan du bruge disse spørgsmål til at fokusere dit politikdesign og din implementeringsindsats.

##### <a name="what-laws-regulations-and-industry-standards-must-your-organization-comply-with"></a>Hvilke love, bestemmelser og branchestandarder skal din organisation overholde?

Da mange organisationer kommer til DLP med det formål at overholde lovgivningen, er besvarelsen af dette spørgsmål et naturligt udgangspunkt for planlægning af din DLP-implementering. Men som it-implementer er du sandsynligvis ikke i stand til at besvare den. Det skal besvares af dit juridiske team og forretningsledere. 
 
**Eksempel** Din organisation er underlagt Storbritannien finansforordninger.


##### <a name="what-sensitive-items-does-your-organization-have-that-must-be-protected-from-leakage"></a>Hvilke følsomme elementer har din organisation, der skal beskyttes mod lækage?

Når din organisation ved, hvor den står med hensyn til lovmæssige overholdelsesbehov, har du en idé om, hvilke følsomme elementer der skal beskyttes mod lækage, og hvordan du vil prioritere implementering af politikker for at beskytte dem. Dette hjælper dig med at vælge de mest relevante DLP-politikskabeloner. Microsoft Purview leveres med forudkonfigurerede DLP-skabeloner til økonomi, medicinsk og sundhed, beskyttelse af personlige oplysninger, og du kan bygge din egen ved hjælp af skabelonen Brugerdefineret. Når du designer og opretter dine faktiske DLP-politikker, hjælper det også dig med at vælge den rigtige [type følsomme oplysninger](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types), når du kender svaret på dette spørgsmål.

**Eksempel** For hurtigt at komme i gang skal du vælge `U.K. Financial Data` politikskabelonen, som omfatter typerne `Credit Card Number`, `EU Debit Card Number`og `SWIFT Code` følsomme oplysninger. 

##### <a name="where-are-the-sensitive-items-and-what-business-processes-are-they-involved-in"></a>Hvor er de følsomme elementer, og hvilke forretningsprocesser er de involveret i?

De elementer, der indeholder dine organisationers følsomme oplysninger, bruges hver dag i forbindelse med forretning. Du skal vide, hvor forekomster af disse følsomme oplysninger kan forekomme, og hvilke forretningsprocesser de bruges i. Dette hjælper dig med at vælge de rigtige placeringer, som dine DLP-politikker skal anvendes på. DLP-politikker anvendes på placeringer:

- Exchange-mail
- SharePoint-websteder
- OneDrive-konti
- Teams-chat- og kanalmeddelelser
- Windows 10 enheder
- Microsoft Defender for Cloud Apps
- Lagre i det lokale miljø

**Eksempel** Din organisations interne auditører sporer et sæt kreditkortnumre. De opbevarer et regneark med dem på et sikkert SharePoint-websted. Flere af medarbejderne kopierer og gemmer dem på deres arbejds OneDrive for Business websted, som synkroniseres med deres Windows 10 enhed. En af dem indsætter en liste over 14 af dem i en mail og forsøger at sende den til eksterne revisorer til gennemsyn. Du vil anvende politikken på det sikre SharePoint-websted, alle interne revisorer OneDrive for Business konti, deres Windows 10 enheder og Exchange-mail.

##### <a name="what-is-your-organizations-tolerance-for-leakage"></a>Hvad er din organisations tolerance for lækage?

Forskellige grupper i din organisation kan have forskellige visninger af, hvad der er et acceptabelt niveau af lækage af følsomme elementer, og hvad der ikke er. Opnåelse af perfektion af nul lækage kan komme på for høje omkostninger for virksomheden.

**Eksempel** Dine organisationers sikkerhedsgruppe føler sammen med det juridiske team, at der ikke bør være nogen deling af kreditkortnumre med nogen uden for organisationen og insisterer på nul lækage. Men som en del af regelmæssig gennemgang af kreditkortnummeraktivitet skal de interne revisorer dele nogle kreditkortnumre med tredjepartsrevisorer. Hvis din DLP-politik forbyder al deling af kreditkortnumre uden for organisationen, vil der være en betydelig afbrydelse af forretningsprocessen og ekstra omkostninger for at afhjælpe afbrydelsen, så de interne auditører kan fuldføre deres sporing. Denne ekstra udgift er uacceptabel for ledelsen. For at løse dette skal der være en intern samtale for at beslutte et acceptabelt niveau af lækage. Når det er besluttet, kan politikken give undtagelser, så visse personer kan dele oplysningerne, eller den kan anvendes i tilstanden Kun overvågning.

#### <a name="planning-for-prerequisites"></a>Planlægning af forudsætninger

Før du kan overvåge nogle DLP-placeringer, er der forudsætninger, der skal opfyldes. Se afsnittene **Før du begynder** på:

- [Kom i gang med forebyggelse af datatab i det lokale miljø (prøveversion)](dlp-on-premises-scanner-get-started.md#before-you-begin)
- [Kom i gang med forebyggelse af datatab forebyggelse af datatab ved slutpunkt](endpoint-dlp-getting-started.md#before-you-begin)
- [Kom i gang med Microsofts overholdelsesudvidelse](dlp-chrome-get-started.md#before-you-begin)
- [Brug politikker til forebyggelse af datatab til cloudapps, der ikke er fra Microsoft (prøveversion)](dlp-use-policies-non-microsoft-cloud-apps.md#before-you-begin)

#### <a name="policy-deployment"></a>Politikinstallation

Når du opretter dine DLP-politikker, bør du overveje at udrulle dem gradvist for at vurdere deres indvirkning og teste deres effektivitet, før du håndhæver dem fuldt ud. Du ønsker f.eks. ikke, at en ny DLP-politik utilsigtet blokerer adgangen til tusindvis af dokumenter eller afbryder en eksisterende forretningsproces.
  
Hvis du opretter DLP-politikker med stor potentiel indvirkning, anbefaler vi, at du følger denne sekvens:
  
1. **Start i testtilstand uden politiktips** , og brug derefter DLP-rapporterne og eventuelle hændelsesrapporter til at vurdere virkningen. Du kan bruge DLP-rapporter til at få vist antallet, placeringen, typen og alvorsgraden af politikforekomster. Baseret på resultaterne kan du finjustere politikkerne efter behov. I testtilstand påvirker DLP-politikker ikke produktiviteten hos personer, der arbejder i din organisation. Brug også denne fase til at teste din arbejdsproces til gennemsyn af DLP-hændelser og problemafhjælpning.
    
2. **Flyt til testtilstand med meddelelser og politiktips** , så du kan begynde at lære brugerne om dine politikker for overholdelse af angivne standarder og forberede dem på de politikker, der skal anvendes. Det er nyttigt at have et link til en side med organisationspolitik, der indeholder flere oplysninger om politikken i politiktippen. I denne fase kan du også bede brugerne om at rapportere falske positiver, så du kan tilpasse politikkerne yderligere. Gå til denne fase, når du har tillid til, at resultaterne af politikprogrammet stemmer overens med det, de interessenter havde i tankerne. 
    
3. **Start fuld håndhævelse af politikkerne** , så handlingerne i reglerne anvendes, og indholdet er beskyttet. Fortsæt med at overvåge DLP-rapporterne og eventuelle hændelsesrapporter eller meddelelser for at sikre, at resultaterne er, hvad du har tænkt dig. 

    ![Indstillinger for brug af testtilstand og aktivering af politik.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

    Du kan når som helst slå en DLP-politik fra, hvilket påvirker alle regler i politikken. Hver regel kan dog også slås fra enkeltvist ved at ændre dens status i regeleditoren.

    ![Indstillinger for deaktivering af en regel i en politik.](../media/f7b258ff-1b8b-4127-b580-83c6492f2bef.png)

    Du kan også ændre prioriteten for flere regler i en politik. Det gør du ved at åbne en politik til redigering. I en række for en regel skal du vælge ellipsen (**...**) og derefter vælge en indstilling, f.eks **. Flyt ned** eller **Placer til sidst**.

    ![Angiv regelprioritet.](../media/dlp-set-rule-priority.png)

#### <a name="end-user-training"></a>Slutbrugeruddannelse

Når en DLP-politik udløses, kan du konfigurere dine politikker til at [sende mailmeddelelser og vise politiktip til DLP-politikker](use-notifications-and-policy-tips.md#send-email-notifications-and-show-policy-tips-for-dlp-policies) til administratorer og slutbrugere. Selvom dine politikker stadig er i testtilstand, og før de er indstillet til at gennemtvinge en blokeringshandling, er politiktip nyttige måder at øge kendskabet til risikable adfærd på følsomme elementer og træne brugerne til at undgå disse funktionsmåder i fremtiden.  

#### <a name="review-dlp-requirements-and-update-strategy"></a>Gennemse DLP-krav og opdateringsstrategi

De forordninger, love og branchestandarder, som din organisation er underlagt, ændres over tid, og det vil dine forretningsmål for DLP også. Sørg for at inkludere regelmæssige gennemgange af alle disse områder, så din organisation overholder angivne standarder, og din implementering af DLP fortsat opfylder dine forretningsbehov.

## <a name="approaches-to-deployment"></a>Metoder til udrulning

|Beskrivelse af kundeforretningsbehov  | Tilgang  |
|---------|---------|
|**Contoso Bank** er i en yderst reguleret branche og har mange forskellige typer følsomme varer på mange forskellige placeringer. </br> - ved, hvilke typer følsomme oplysninger der har førsteprioritet. </br> - skal minimere afbrydelser i virksomheden, efterhånden som politikkerne udrulles. </br> – har it-ressourcer og kan hyre eksperter til at hjælpe med at planlægge, designe udrulning </br> - har en Premier Support-kontrakt med Microsoft| - Tag dig tid til at forstå, hvilke regler de skal overholde, og hvordan de skal overholde. </br> -Tag dig tid til at forstå værdien af Microsoft Purview Information Protection stakken </br> – Udvikl skemaet for følsomhedsmærkater for prioriterede elementer, og anvend </br> - Involver ejere af forretningsprocesser </br>- Design-/kodepolitikker, udrul i testtilstand, oplær brugere </br>- gentag|
|**TailSpin Toys** ved ikke, hvad de har, eller hvor det er, og har kun lidt eller ingen ressourcedybde. De bruger Teams, OneDrive for Business og Exchange i vid udstrækning.     |– Start med enkle politikker for de prioriterede placeringer. </br>- Overvåge, hvad der bliver identificeret </br>- Anvend følsomhedsmærkater i overensstemmelse hermed </br>– Afgræns politikker, oplær brugere       |
|**Fabrikam** er en lille nystartet virksomhed og ønsker at beskytte sin intellektuelle ejendom og skal bevæge sig hurtigt. De er villige til at dedikere nogle ressourcer, men har ikke råd til at ansætte eksterne eksperter. </br>– Følsomme elementer findes alle i Microsoft 365 OneDrive for Business/SharePoint </br>- Ibrugtagningen af OneDrive for Business og SharePoint er langsom, medarbejdere/skygge-it bruger DropBox og Google-drev til at dele/gemme elementer </br>- Medarbejdere sætter pris på, hvor hurtigt arbejdet går i forhold til databeskyttelsesdisciplinen </br>- Kunde splurged og købte alle 18 medarbejdere nye Windows 10 enheder     |– Udnyt standardpolitikken for forebyggelse af databegivenheden i Teams </br>– Brug begrænset som standardindstilling for SharePoint-elementer </br>– Udrul politikker, der forhindrer ekstern deling </br>– Udrul politikker på prioriterede placeringer </br>– Udrul politikker på Windows 10 enheder </br>– Bloker uploads til et cloudlager, der ikke er OneDrive for Business      |

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
