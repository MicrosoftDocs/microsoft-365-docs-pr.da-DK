---
title: Vigtige overvejelser i forbindelse med overholdelse af angivne standarder og sikkerhed i forbindelse med banker og kapitalmarkeder i USA
ms.author: bcarter
author: brendacarter
manager: laurawi
audience: ITPro
ms.topic: article
ms.collection:
- M365-security-compliance
ms.prod: microsoft-365-enterprise
ms.custom: seo-marvel-jun2020
ms.localizationpriority: high
description: Få mere at vide om, hvordan finansielle institutioner kan opretholde overholdelse af angivne standarder for finansiel sikkerhed og samarbejde effektivt ved hjælp af Microsoft 365 og Teams.
f1.keywords: NOCSH
ms.openlocfilehash: ed00d120d00253c1abbb6d0c0109fdce0b7ff863
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64948259"
---
# <a name="key-compliance-and-security-considerations-for-us-banking-and-capital-markets"></a>Vigtige overvejelser i forbindelse med overholdelse af angivne standarder og sikkerhed i forbindelse med banker og kapitalmarkeder i USA

## <a name="introduction"></a>Indførelsen
Finansielle institutioner overgår næsten alle kommercielle virksomheder i deres efterspørgsel efter strenge sikkerheds-, overholdelses- og styringskontrol. Beskyttelsen af data, identiteter, enheder og applikationer er ikke kun afgørende for deres virksomhed, den er underlagt overholdelseskrav og retningslinjer fra regulerende organer, f.eks. DEN AMERIKANSKE Værdipapir- og Exchange kommission (SEC), FINRA (Financial Industry Regulatory Authority), FFIEC (Federal Financial Institutions Examination Council) og CFTC (Commodity Futures Trading Commission). Desuden er finansielle institutioner underlagt love som Dodd-Frank og Sarbanes-Oxley lov af 2002.

I nutidens klima med øget sikkerhedsovervågning, bekymringer om insiderrisiko og brud på offentlige data, kræver kunderne også et højt sikkerhedsniveau fra deres finansielle institutioner for at have tillid til dem med deres personlige data og bankaktiver.

Historisk set har behovet for omfattende kontroller direkte påvirket og begrænset de it-systemer og platforme, som finansielle institutioner bruger til at muliggøre samarbejde internt og eksternt. I dag har de finansielle medarbejdere brug for en moderne samarbejdsplatform, der er nem at anvende og nem at bruge. Men finansielle tjenester kan ikke handle med fleksibiliteten til at samarbejde mellem brugere, teams og afdelinger med sikkerheds- og overholdelseskontrol, der gennemtvinger politikker for at beskytte brugere og it-systemer mod trusler.

I sektoren for finansielle tjenesteydelser er det nødvendigt at være opmærksom på konfiguration og installation af samarbejdsværktøjer og sikkerhedskontroller, herunder:
- Risikovurdering af almindelige organisationssamarbejds- og forretningsprocesscenarier
- Krav til beskyttelse af oplysninger og datastyring
- Cybersikkerhed og insidertrusler
- Lovmæssige krav til overholdelse af angivne standarder
- Andre driftsmæssige risici

**Microsoft 365 er et moderne cloudmiljø på arbejdspladsen, der kan håndtere de aktuelle udfordringer, som organisationer med finansielle tjenesteydelser står over for. Et sikkert og fleksibelt samarbejde på tværs af virksomheden kombineres med kontroller og håndhævelse af politikker for at overholde strenge lovgivningsmæssige rammer for overholdelse af angivne standarder.** I denne artikel beskrives det, hvordan Microsoft 365-platformen hjælper finansielle tjenester med at flytte til en moderne samarbejdsplatform, samtidig med at data og systemer er sikre og overholder reglerne:

* Aktivér organisations- og medarbejderproduktivitet ved hjælp af Microsoft 365 og Microsoft Teams
* Beskyt moderne samarbejde ved hjælp af Microsoft 365 
* Identificer følsomme data, og undgå tab af data
* Forsvar fæstningen
* Styr data, og overhold reglerne ved effektivt at administrere poster
* Etabler etiske vægge med informationsbarrierer
* Beskyt mod dataudfiltrering og insiderrisiko

Som Microsoft-partner har Protiviti bidraget til og leveret materialefeedback til denne artikel.

Følgende illustrationer, der kan downloades, supplerer denne artikel. Woodgrove Bank og Contoso bruges til at demonstrere, hvordan kapaciteter, der er beskrevet i denne artikel, kan anvendes til at håndtere fælles lovmæssige krav til finansielle tjenesteydelser. Du er velkommen til at tilpasse disse illustrationer til eget brug. 

**illustrationer Microsoft 365 beskyttelse af oplysninger og overholdelse af angivne standarder**

| Element | Beskrivelse |
|:-----|:-----|
|[![Modelplakat: Microsoft 365 funktioner til beskyttelse af oplysninger og overholdelse af angivne standarder.](../media/solutions-architecture-center/m365-compliance-illustrations-thumb.png)](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf) <br/>Engelsk: [Download som en PDF Download](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf)\| [som en Visio](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.vsdx)   <br/> Japansk: [Download som en PDF-download](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.pdf)\| [som en Visio](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.vsdx)  <br/> Opdateret i november 2020|Omfatter: <ul><li>  Microsoft Purview Information Protection og Microsoft Purview forebyggelse af datatab</li><li>Opbevaringspolitikker og opbevaringsmærkater </li><li>Informationsbarrierer</li><li>Kommunikationsoverholdelse</li><li>Insiderrisiko</li><li>Dataindtagelse fra tredjepart</li>|


## <a name="empower-organizational-and-employee-productivity-by-using-microsoft-365-and-teams"></a>Styrk organisationens og medarbejdernes produktivitet ved hjælp af Microsoft 365 og Teams

Samarbejde kræver typisk forskellige former for kommunikation, muligheden for at gemme og få adgang til dokumenter/data og muligheden for at integrere andre programmer efter behov. Medarbejdere i finansielle tjenester skal typisk samarbejde og kommunikere med medlemmer af andre afdelinger eller teams og nogle gange med eksterne enheder. Derfor er det uønsket at bruge systemer, der skaber siloer eller gør informationsdeling vanskelig. Det er i stedet at foretrække at udnytte platforme og programmer, der gør det muligt for medarbejderne at kommunikere, samarbejde og dele oplysninger sikkert og i henhold til virksomhedens politik.

Hvis medarbejderne får en moderne, cloudbaseret samarbejdsplatform, kan de vælge og integrere værktøjer, der gør dem mere produktive og giver dem mulighed for at finde fleksible måder at arbejde på. Hvis du bruger Teams sammen med sikkerhedskontroller og politikker for styring af oplysninger, der beskytter organisationen, kan det hjælpe din arbejdsstyrke med at kommunikere og samarbejde effektivt.

Teams er et samarbejdshub for organisationen. Det hjælper med at få folk til at arbejde produktivt på fælles initiativer og projekter. Teams gør det muligt for teammedlemmer at føre 1:1-chatsamtaler og chatsamtaler med flere grupper, samarbejde og medforfattere af dokumenter samt gemme og dele filer. Teams faciliterer også onlinemøder via integreret virksomhedstale og -video. Teams kan også tilpasses med Microsoft-apps, f.eks. Microsoft Planner, Microsoft Dynamics 365, Power Apps, Power BI og line of business-programmer fra tredjepart. Teams er designet til brug af både interne teammedlemmer og tilladt eksterne brugere, der kan deltage i teamkanaler, deltage i chatsamtaler, få adgang til gemte filer og udnytte andre programmer

Alle Microsoft-team understøttes af en Microsoft 365 gruppe. Denne gruppe anses for medlemskabstjeneste for mange Office 365 tjenester, herunder Teams. Microsoft 365 grupper bruges til på en sikker måde at skelne mellem "ejere" og "medlemmer" og til at styre adgangen til forskellige funktioner i Teams. Når Teams er kombineret med relevante styringskontrolelementer og regelmæssigt administrerede adgangsgennemgange, er det kun medlemmer og ejere, der kan bruge godkendte kanaler og egenskaber.

Et almindeligt scenarie, hvor Teams er til gavn for finansielle tjenester, er, når du kører interne projekter eller programmer. For eksempel er mange finansielle institutioner, herunder banker, formueforvaltningsvirksomheder, kreditforeninger og forsikringsudbydere, forpligtet til at have bekæmpelse af hvidvaskning af penge og andre overholdelsesprogrammer på plads. Et tværfunktionelt team bestående af it, forretningsområder som detail- og rigdomsstyring og en økonomisk kriminalitetsenhed kan være forpligtet til at dele data med hinanden og kommunikere om programmet eller specifikke undersøgelser. Disse programmer har traditionelt brugt delte netværksdrev, men denne fremgangsmåde kan give mange udfordringer, herunder:
* Kun én person kan redigere et dokument ad gangen.
* Administration af sikkerhed er tidskrævende, fordi tilføjelse/fjernelse af enkeltpersoner typisk involverer it.
* Data forbliver placeret på delte netværksdrev meget længere end påkrævet eller eftersøgt.

Teams kan give et samarbejdsområde til sikker lagring af følsomme klientdata og føre samtaler mellem teammedlemmer, hvor følsomme emner kan diskuteres. Flere medlemmer af teamet kan redigere eller samarbejde om et enkelt dokument på samme tid. Programejeren eller -koordinatoren kan konfigureres som teamejer og derefter tilføje og fjerne medlemmer efter behov.

Et andet almindeligt scenarie er at bruge Teams som et "virtuelt datarum" til sikkert samarbejde, herunder lagring og administration af dokumenter. Teammedlemmer og syndikater inden for investment banking, asset management eller private equity virksomheder kan sikkert samarbejde om en aftale eller investering. Tværfunktionelle teams er ofte involveret i planlægning og opfyldelse af sådanne tilbud, og muligheden for sikkert at dele data og føre samtaler er et centralt krav. En sikker deling af relaterede dokumenter med eksterne investorer er også et vigtigt krav. Teams giver en sikker og fuldt overvågelig placering, hvorfra investeringsdata kan gemmes, beskyttes og deles centralt.

![En gruppe kontormedarbejdere på et møde diskuterer billeder på en stor skrue.](../media/m365cO19-ent-dell-latitude13-5951.jpg)
 
### <a name="teams-improve-collaboration-and-reduce-compliance-risk"></a>Teams: Øg samarbejdet, og reducer risikoen for overholdelse af angivne standarder

Microsoft 365 indeholder andre fælles politikfunktioner til Teams ved hjælp af Microsoft 365 grupper som en underliggende medlemskabstjeneste. Disse politikker kan hjælpe med at forbedre samarbejdet og opfylde behovet for overholdelse af angivne standarder.

**Microsoft 365 politikker for navngivning af grupper** er med til at sikre, at Microsoft 365 grupper og derfor teams navngives i henhold til virksomhedens politik. Navne kan være problematiske, hvis de ikke er relevante. Medarbejderne ved måske ikke, hvilke teams de skal arbejde med eller dele oplysninger med, hvis navne ikke anvendes korrekt. Gruppe navngivningspolitikker (herunder understøttelse af præfiks-/suffiksbaserede politikker og brugerdefinerede blokerede ord) kan gennemtvinge god "hygiejne" og forhindre brug af bestemte ord, f.eks. reserverede ord eller upassende terminologi.
  
**Microsoft 365 politikker for udløb af grupper** er med til at sikre, at Microsoft 365 grupper og derfor teams ikke bevares i længere tid, end organisationen ønsker eller har brug for. Denne funktion hjælper med at forhindre to vigtige problemer med administration af oplysninger:

* Spredning af teams, der ikke er nødvendige eller bruges.
* Overopbevaring af data, der ikke længere kræves eller bruges af organisationen (undtagen i tilfælde af juridisk bevarelse).

Administratorer kan angive en udløbsperiode for Microsoft 365 grupper, f.eks. 90, 180 eller 365 dage. Hvis en tjeneste, der understøttes af en Microsoft 365 gruppe, er inaktiv i udløbsperioden, får gruppeejere besked. Hvis der ikke udføres nogen handling, slettes den Microsoft 365 gruppe og alle dens relaterede tjenester, herunder Teams.
  
Den overopbevaring af data, der er gemt i Teams og andre gruppebaserede tjenester, kan udgøre en risiko for organisationer for finansielle tjenester. Microsoft 365 udløbspolitikker for grupper er en anbefalet metode til at forhindre opbevaring af data, der ikke længere er nødvendige. Kombineret med indbyggede opbevaringsmærkater og politikker hjælper Microsoft 365 med at sikre, at organisationer kun bevarer de data, der kræves for at overholde virksomhedens politikker og lovmæssige overholdelsesforpligtelser.

#### <a name="teams-integrate-custom-requirements-with-ease"></a>Teams: Du kan nemt integrere brugerdefinerede krav

Teams gør det som standard muligt at oprette teams via selvbetjening. Mange regulerede organisationer ønsker dog at styre og forstå, hvilke samarbejdskanaler der i øjeblikket bruges af deres medarbejdere, hvilke kanaler der kan indeholde følsomme data, og ejerskabet over organisatoriske kanaler. For at lette disse styringskontrolelementer Microsoft 365 gør det muligt for organisationen at deaktivere oprettelse af selvbetjeningsteams. Ved hjælp af værktøjer til automatisering af forretningsprocesser, f.eks. Microsoft Power Apps og Power Automate, kan organisationer oprette og udrulle simple formularer og godkendelsesprocesser for medarbejdere for at anmode om oprettelse af et nyt team. Når teamet godkendes, kan det klargøres automatisk, og der sendes et link til anmoderen. På denne måde kan organisationer designe og integrere deres kontrolelementer til overholdelse af angivne standarder og brugerdefinerede krav i teamoprettelsesprocessen.
 
### <a name="acceptable-digital-communication-channels"></a>Acceptable digitale kommunikationskanaler

FINRA [understreger, at regulerede virksomheders digitale kommunikation opfylder kravene til registrering i Exchange lovregler 17a-3 og 17a-4 samt FINRA Rule Series 4510](https://www.finra.org/rules-guidance/key-topics/books-records). FINRA udgiver en årlig rapport, der indeholder vigtige resultater, observationer og effektiv praksis for at hjælpe organisationer med at forbedre overholdelse af angivne standarder og risikostyring. I [sin rapport fra 2019 om undersøgelsesresultater og observationer](https://www.finra.org/rules-guidance/guidance/reports/2019-report-exam-findings-and-observations) identificerede FINRA digital kommunikation som et centralt område, hvor virksomheder står over for udfordringer med at overholde tilsyns- og registreringskravene.

Hvis en organisation tillader sine medarbejdere at bruge en bestemt applikation, f.eks. en appbaseret meddelelsestjeneste eller samarbejdsplatform, skal virksomheden arkivere forretningsposter og overvåge disse medarbejderes aktiviteter og kommunikation i det pågældende program. Organisationer er ansvarlige for due diligence for at overholde FINRA-regler og værdipapirlove og for at følge op på potentielle overtrædelser af disse regler i forbindelse med medarbejderanvendelse af sådanne apps.
  
De effektive fremgangsmåder, som FINRA anbefaler, omfatter følgende:
* Etabler et omfattende styringsprogram for digitale kommunikationskanaler. Administrer organisationens beslutninger om, hvilke digitale kommunikationskanaler der er tilladt, og definer overholdelsesprocesser for hver digital kanal. Hold nøje øje med det hurtigt foranderlige landskab af digitale kommunikationskanaler, og hold overholdelsesprocesserne opdateret.
* Klart definere og styre tilladte digitale kanaler. Definer både godkendte og forbudte digitale kanaler. Bloker eller begræns brugen af forbudte digitale kanaler eller forbudte funktioner i digitale kanaler, der begrænser organisationens evne til at overholde kravene til datastyring og tilsyn.
* Tilbyde uddannelse i digital kommunikation. Implementer obligatoriske uddannelsesprogrammer, før registrerede repræsentanter får adgang til godkendte digitale kanaler. Oplæring hjælper med at tydeliggøre en organisations forventninger til forretningsmæssig og personlig digital kommunikation, og den guider medarbejderne gennem brug af tilladte funktioner i hver kanal på en kompatibel måde.

FINRA's resultater og bemærkninger vedrørende digital kommunikation vedrører direkte en organisations evne til at overholde [SEC-regel 17a-4](https://www.law.cornell.edu/cfr/text/17/240.17a-4) om bevarelse af al forretningsrelateret kommunikation, FINRA-regler [3110](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3110) og [3120](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3120) for tilsyn og revision af kommunikation og Regelserie [4510](https://www.finra.org/rules-guidance/rulebooks/finra-rules/4510) for registrering. CfTC (Commodity Futures Trading Commission) udsteder lignende krav i henhold til 17 CFR 131. Disse forordninger gennemgås indgående senere i denne artikel.

***Teams leverer sammen med den omfattende pakke af Microsoft 365 tilbud om sikkerhed og overholdelse af angivne standarder en digital kommunikationskanal for finansielle institutioner, der effektivt kan drive forretning og overholde regler.*** I resten af denne artikel beskrives det, hvordan Microsoft 365 indbyggede funktioner til datastyring, informationsbeskyttelse, informationsbarrierer og tilsynskontrol giver Teams et robust værktøjssæt, der kan hjælpe med at opfylde disse lovgivningsmæssige forpligtelser.

## <a name="protect-modern-collaboration-with-microsoft-365"></a>Beskyt moderne samarbejde med Microsoft 365

### <a name="secure-user-identities-and-control-access"></a>Sikker brugeridentiteter og kontroladgang

***Beskyttelse af adgang til kundeoplysninger, finansielle dokumenter og programmer begynder med en stærk sikring af brugeridentiteter.*** Dette kræver en sikker platform, så virksomheden kan gemme og administrere identiteter, hvilket giver en pålidelig godkendelsesmetode og dynamisk styring af adgangen til disse programmer.

Når medarbejderne arbejder, kan de flytte fra program til program eller mellem flere placeringer og enheder. Adgang til data skal godkendes på hvert trin undervejs. Godkendelsesprocessen skal understøtte en stærk protokol og flere godkendelsesfaktorer (f.eks. engangs-SMS-adgangskode, godkenderapp og certifikat) for at sikre, at identiteter ikke kompromitteres. Gennemtvingelse af risikobaserede adgangspolitikker er afgørende for at beskytte finansielle data og programmer mod insidertrusler, utilsigtede datalækager og dataudfiltrering.

Microsoft 365 leverer en sikker identitetsplatform i [Azure Active Directory (Azure AD),](/azure/active-directory/) hvor identiteter gemmes centralt og administreres sikkert. Azure AD udgør sammen med et væld af relaterede Microsoft 365 sikkerhedstjenester grundlaget for at give medarbejderne den adgang, de har brug for til at arbejde sikkert, samtidig med at organisationen beskyttes mod trusler.

[Azure AD Multi-Factor Authentication (MFA)](/azure/active-directory/fundamentals/concept-fundamentals-mfa-get-started) er indbygget i platformen og giver et ekstra bevis for godkendelse, der kan hjælpe med at bekræfte brugeridentitet, når brugeren får adgang til følsomme økonomiske data og programmer. Azure MFA kræver mindst to former for godkendelse, f.eks. en adgangskode plus en kendt mobilenhed. Den understøtter flere indstillinger for andenfaktorgodkendelse, herunder:

- Appen Microsoft Authenticator
- En engangs-adgangskode, der leveres via sms
- Et telefonopkald, hvor en bruger skal angive en pinkode

Hvis adgangskoden på en eller anden måde kompromitteres, vil en potentiel hacker stadig have brug for brugerens telefon for at få adgang til organisationsdata. Derudover bruger Microsoft 365 moderne godkendelse som en nøgleprotokol, hvilket giver den samme stærke og omfattende godkendelsesoplevelse fra webbrowsere til de samarbejdsværktøjer, som medarbejderne bruger fra dag til dag, herunder Microsoft Outlook og de andre Microsoft Office programmer.

#### <a name="passwordless"></a>Uden adgangskode

Adgangskoder er det svageste link i en sikkerhedskæde. De kan være et enkelt fejlpunkt, hvis der ikke er nogen yderligere bekræftelse. Microsoft understøtter en lang række godkendelsesmuligheder, så de passer til de finansielle institutioners behov.

*Metoder uden adgangskode* hjælper med at gøre MFA mere praktisk for brugerne. Selvom det ikke er alle MFA'er uden adgangskode, anvender teknologier uden adgangskode multifaktorgodkendelse. Microsoft, Google og andre brancheledere har udviklet standarder for at give en enklere og stærkere godkendelsesoplevelse på tværs af internettet og mobilenheder i en gruppe kaldet Fido (Fast IDentity Online). Den nyligt udviklede FIDO2-standard giver brugerne mulighed for nemt og sikkert at godkende uden at kræve en adgangskode for at fjerne phishing.

Microsoft MFA-metoder, der er uden adgangskode, omfatter:
* [Microsoft Authenticator](/azure/active-directory/user-help/user-help-auth-app-overview): Vi anbefaler, at du bruger Microsoft Authenticator-mobilappen for at opnå fleksibilitet, bekvemmelighed og omkostninger. Microsoft Authenticator understøtter biometriske data, pushmeddelelser og engangskoder til alle Azure AD-forbundne apps. Den er tilgængelig fra Apple- og Android-appbutikkerne.
*  [Windows Hello](/windows/security/identity-protection/hello-for-business/hello-overview): Hvis du vil have en indbygget oplevelse på pc'en, anbefaler vi, at du bruger Windows Hello. Den bruger biometriske oplysninger (f.eks. ansigt eller fingeraftryk) til at logge på automatisk.  
* [FIDO2 Sikkerhedsnøgler](/windows/security/identity-protection/hello-for-business/microsoft-compatible-security-key) er nu tilgængelige fra flere Microsoft-partnere: Yubico, Feitian Technologies og HID Global i et BADGE MED USB, NFC-aktiveret eller biometrisk nøgle.

[Betinget adgang i Azure AD](/azure/active-directory/conditional-access/) er en robust løsning til automatisering af beslutninger om adgangskontrol og håndhævelse af organisatoriske politikker for at beskytte virksomhedens aktiver. Et klassisk eksempel er, når en økonomisk planlægning ønsker at få adgang til et program, der har følsomme kundedata. De skal automatisk udføre en multifaktorgodkendelse for specifikt at få adgang til det pågældende program, og adgangen skal være fra en virksomhedsadministrert enhed. Betinget adgang i Azure samler signaler om en brugers anmodning om adgang, f.eks. egenskaber for brugeren, enheden, placeringen og netværket og det program, som brugeren forsøger at få adgang til. Den evaluerer dynamisk forsøg på at få adgang til programmet i forhold til konfigurerede politikker. Hvis bruger- eller enhedsrisikoen er øget, eller hvis andre betingelser ikke er opfyldt, kan Azure AD automatisk gennemtvinge politikker, f.eks. kræve MFA, kræve en sikker nulstilling af adgangskode eller begrænse eller blokere adgang. Dette hjælper med at sikre, at følsomme organisationsaktiver beskyttes i miljøer, der ændrer sig dynamisk.
 
Azure AD og de relaterede Microsoft 365 sikkerhedstjenester udgør det grundlag, hvorpå en moderne cloudsamarbejdesplatform kan udrulles til finansielle institutioner, så adgang til data og programmer kan sikres, og overholdelse af regler og standarder for regulatorer. Disse værktøjer indeholder følgende vigtige funktioner:

* Gem og administrer brugeridentiteter centralt og sikkert.
* Brug en stærk godkendelsesprotokol, herunder multifaktorgodkendelse, til at godkende brugere i forbindelse med adgangsanmodninger og give en ensartet og robust godkendelsesoplevelse på tværs af alle programmer.
* Valider dynamisk politikker for alle adgangsanmodninger, så der inkorporeres flere signaler i politikbeslutningsprocessen, herunder identitet, bruger/gruppemedlemskab, program, enhed, netværk, placering og risikoscore i realtid.
* Valider detaljerede politikker baseret på brugerfunktionsmåde og filegenskaber, og gennemtving dynamisk yderligere sikkerhedsforanstaltninger, når det er nødvendigt.
* Identificer "skygge-it" i organisationen, og giv InfoSec-teams tilladelse til at sanktionere eller blokere cloudprogrammer.
* Overvåg og styr adgangen til Microsoft- og ikke-Microsoft-cloudprogrammer.
* Proaktivt beskytte mod phishing- og ransomware-angreb via mail.

#### <a name="azure-ad-identity-protection"></a>Azure AD Identity Protection
Betinget adgang beskytter ressourcer mod mistænkelige anmodninger, men identitetsbeskyttelse går længere ved at levere løbende risikoregistrering og afhjælpning af mistænkelige brugerkonti. Identity Protection holder dig informeret om mistænkelig brugers og logonadfærd i dit miljø døgnet rundt. Dens automatiske svar forhindrer proaktivt kompromitterede identiteter i at blive misbrugt.
 
Identitetsbeskyttelse er et værktøj, der giver organisationer mulighed for at udføre tre vigtige opgaver:

* Automatiser registrering og afhjælpning af identitetsbaserede risici.
* Undersøg risici ved hjælp af data på portalen.
* Eksportér data til risikoregistrering til tredjepartsværktøjer til yderligere analyse.

Identity Protection bruger den viden, som Microsoft har erhvervet fra sin stilling i organisationer med Azure AD, på forbrugerområdet med Microsoft-konti og i spil med Xbox for at beskytte dine brugere. Microsoft analyserer 65 billioner signaler pr. dag for at identificere og beskytte kunder mod trusler. De signaler, der genereres af og overføres til Identity Protection, kan føres videre til værktøjer som Betinget adgang til at træffe adgangsbeslutninger. De kan også føres tilbage til et SIEM-værktøj (Security Information and Event Management) til yderligere undersøgelse baseret på organisationens gennemtvungne politikker.

Identity Protection hjælper organisationer med automatisk at beskytte sig mod identitets kompromitteret ved at drage fordel af cloudintelligens baseret på avanceret registrering baseret på heuristik, UEBA (user and entity behavior analytics) og machine learning (ML) på tværs af Microsofts økosystem.

![Fem information arbejdstagere ser som en anden giver en præsentation.](../media/win17-15021-00-n9.jpg)
 
## <a name="identify-sensitive-data-and-prevent-data-loss"></a>Identificer følsomme data, og undgå tab af data
Microsoft 365 gør det muligt for alle organisationer at identificere følsomme data i organisationen via en kombination af effektive funktioner, herunder:

* **Microsoft Purview Information Protection** både til brugerbaseret klassificering og automatisk klassificering af følsomme data.
* **Microsoft Purview DLP (Forebyggelse af datatab)** til automatisk identifikation af følsomme data ved hjælp af følsomme datatyper (med andre ord regulære udtryk) og nøgleord og håndhævelse af politikker.

**[Microsoft Purview Information Protection](../compliance/information-protection.md)** gør det muligt for organisationer at klassificere dokumenter og mails på en intelligent måde ved hjælp af følsomhedsmærkater. Brugerne kan anvende følsomhedsmærkater manuelt på dokumenter i Microsoft Office programmer og på mails i Outlook. Mærkaterne kan automatisk anvende dokumentmarkeringer, beskyttelse via kryptering og håndhævelse af rettighedsstyring. Følsomhedsmærkater kan også anvendes automatisk ved at konfigurere politikker, der bruger nøgleord og følsomme datatyper (f.eks. kreditkortnumre, cpr-numre og identitetsnumre), til automatisk at finde og klassificere følsomme data.

Derudover leverer Microsoft "klassificeringsmaskiner, der kan oplæres", og som bruger modeller til maskinel indlæring til at identificere følsomme data, der er baseret på indholdet, i modsætning til blot gennem mønstermatch eller af elementerne i indholdet. En klassificering lærer, hvordan du identificerer en type indhold ved at se på mange eksempler på det indhold, der skal klassificeres. Oplæring af en klassificering starter med at give den eksempler på indhold i en bestemt kategori. Når modellen er blevet lært af disse eksempler, testes den ved at give den en blanding af matchende og ikke-matchende eksempler. Klassificeringen forudsiger, om et givet eksempel falder ind under kategorien eller ej. En person bekræfter derefter resultaterne og sorterer positive, negativer, falske positiver og falske negative for at øge nøjagtigheden af klassificeringens forudsigelser. Når den oplærte klassificering er publiceret, behandler den indhold i Microsoft Office SharePoint Online, Exchange Online og OneDrive for Business og klassificerer automatisk indholdet.

Anvendelse af følsomhedsmærkater på dokumenter og mails integrerer metadata, der identificerer den valgte følsomhed i objektet. Følsomheden følger derefter dataene. Så selvom et navngivet dokument er gemt på en brugers skrivebord eller i et lokalt system, er det stadig beskyttet. Denne funktionalitet gør det muligt for andre Microsoft 365 løsninger, f.eks. Microsoft Defender for Cloud Apps- eller netværksenheder, at identificere følsomme data og automatisk gennemtvinge sikkerhedskontroller. Følsomhedsmærkater har den ekstra fordel, at medarbejderne uddannes i, hvilke data i en organisation der betragtes som følsomme, og hvordan de håndterer disse data, når de modtager dem.

**[Microsoft Purview DLP (Forebyggelse af datatab)](../compliance/dlp-learn-about-dlp.md)** identificerer automatisk dokumenter, mails og samtaler, der indeholder følsomme data, ved at scanne dem for følsomme data og derefter gennemtvinge politikken for disse objekter. Politikker gennemtvinges på dokumenter i SharePoint og OneDrive for Business. De håndhæves også, når brugerne sender mail, og i Teams chats og kanalsamtaler. Politikker kan konfigureres til at søge efter nøgleord, følsomme datatyper, opbevaringsmærkater, og om data deles i organisationen eller eksternt. Der leveres kontrolelementer, der hjælper organisationer med at finjustere DLP-politikker for at reducere falske positiver. Når der findes følsomme data, kan politiktip, der kan tilpasses, vises for brugerne i Microsoft 365 programmer for at informere dem om, at deres indhold indeholder følsomme data og derefter foreslå korrigerende handlinger. Politikker kan også forhindre brugerne i at få adgang til dokumenter, dele dokumenter eller sende mails, der indeholder visse typer følsomme data. Microsoft 365 understøtter mere end 100 indbyggede følsomme datatyper. Organisationer kan konfigurere brugerdefinerede følsomme datatyper, så de opfylder deres politikker.

Udrulning af Microsoft Purview-Information Protection- og DLP-politikker til organisationer kræver omhyggelig planlægning og et brugeruddannelsesprogram, så medarbejderne forstår organisationens dataklassificeringsskema, og hvilke typer data der anses for følsomme. At give medarbejderne værktøjer og uddannelsesprogrammer, der hjælper dem med at identificere følsomme data og forstå, hvordan de håndterer dem, gør dem til en del af løsningen til afhjælpning af sikkerhedsrisici for oplysninger.

De signaler, der genereres af og overføres til Identity Protection, kan også overføres til værktøjer som Betinget adgang til at træffe adgangsbeslutninger eller til et SIEM-værktøj (Security Information And Event Management) til undersøgelse baseret på en organisations gennemtvungne politikker.

Identitetsbeskyttelse hjælper organisationer med automatisk at beskytte sig mod identitets kompromitteret ved at drage fordel af cloudintelligens, der er baseret på avancerede registreringer baseret på heuristik, analyse af bruger- og objektadfærd og maskinel indlæring på tværs af Microsofts økosystem.

![En informationsmedarbejder er afbilledet foran en stor række skærme.](../media/clo1718-portrait-006.jpg)

## <a name="defend-the-fortress"></a>Forsvar fæstningen

Microsoft lancerede for nylig Microsoft 365 Defender-løsningen, som er designet til at sikre den moderne organisation fra det voksende trusselslandskab. Ved at udnytte intelligent sikkerhed Graph tilbyder Threat Protection-løsningen omfattende, integreret sikkerhed mod flere angrebsvektorer.

### <a name="the-intelligent-security-graph"></a>[Graph Intelligent sikkerhed](https://www.microsoft.com/security/business/intelligence) 
Sikkerhedstjenester fra Microsoft 365 leveres af Graph intelligent sikkerhed. For at bekæmpe cybertrusler bruger intelligent sikkerhed Graph avancerede analyser til at linke trusselsintelligens og sikkerhedssignaler fra Microsoft og microsofts partnere. Microsoft driver globale tjenester i stor skala og indsamler billioner af sikkerhedssignaler, der styrer beskyttelseslag på tværs af stakken. Modeller til maskinel indlæring vurderer denne intelligens, og signal- og trusselsindsigt deles bredt på tværs af vores produkter og tjenester. Dette giver os mulighed for hurtigt at registrere og reagere på trusler og sende handlingsbare beskeder og oplysninger til kunder med henblik på afhjælpning. Vores modeller til maskinel indlæring oplæres løbende og opdateres med ny indsigt, hvilket hjælper os med at opbygge mere sikre produkter og give mere proaktiv sikkerhed.

[Microsoft Defender for Office 365](../security/office-365-security/defender-for-office-365.md) leverer en integreret Microsoft 365-tjeneste, der beskytter organisationer mod skadelige links og malware, der leveres via mail og Office dokumenter. En af de mest almindelige angrebsvektorer, der påvirker brugere i dag, er mail phishing-angreb. Disse angreb kan målrettes mod bestemte brugere og kan være meget overbevisende, med nogle opfordring til handling, der beder brugeren om at klikke på et ondsindet link eller åbne en vedhæftet fil, der indeholder malware. Når en computer er inficeret, kan hackeren enten stjæle brugerens legitimationsoplysninger og flytte tværgående på tværs af organisationen eller exfiltrate mails og data for at søge efter følsomme oplysninger. Defender for Office 365 understøtter sikre vedhæftede filer og sikre links ved at evaluere dokumenter og links på kliktidspunktet for potentielt ondsindede hensigter og blokerer adgangen. Vedhæftede filer i mails åbnes i en beskyttet sandkasse, før de leveres til en brugers postkasse. Den evaluerer også links i Office dokumenter for skadelige URL-adresser. Defender for Office 365 beskytter også links og filer i SharePoint Online, OneDrive for Business og Teams. Hvis der registreres en skadelig fil, låser Defender for Office 365 automatisk filen for at reducere den potentielle skade.

[Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) er en samlet slutpunktssikkerhedsplatform til forebyggende beskyttelse, registrering efter sikkerhedsbrud og automatiseret undersøgelse og svar. Defender for Endpoint indeholder indbyggede funktioner til registrering og beskyttelse af følsomme data på virksomhedsslutpunkter.

[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) gør det muligt for organisationer at gennemtvinge politikker på et detaljeret niveau og registrere uregelmæssigheder i funktionsmåden baseret på individuelle brugerprofiler, der automatisk defineres ved hjælp af maskinel indlæring. Defender for Cloud Apps-politikker kan bygge på politikker for betinget adgang i Azure for at beskytte følsomme virksomhedsaktiver ved at evaluere yderligere signaler, der er relateret til brugeradfærd og egenskaber for de dokumenter, der tilgås. Med tiden lærer Defender for Cloud Apps, hvad der er typisk for hver medarbejder med hensyn til de data, de får adgang til, og de programmer, de bruger. Baseret på lærte adfærdsmønstre kan politikker derefter automatisk gennemtvinge sikkerhedskontroller, hvis en medarbejder handler uden for den pågældende adfærdsprofil. Hvis en medarbejder f.eks. typisk tilgår et regnskabsprogram fra kl. 09.00 til 17.00 mandag til fredag, men pludselig begynder at få adgang til programmet kraftigt søndag aften, kan Defender for Cloud Apps dynamisk gennemtvinge politikker for at kræve, at brugeren skal godkende igen. Dette hjælper med at sikre, at brugerens legitimationsoplysninger ikke er blevet kompromitteret. Defender for Cloud Apps kan også hjælpe med at identificere "skygge-it" i organisationen, hvilket hjælper informationssikkerhedsteams med at sikre, at medarbejderne bruger sanktionerede værktøjer, når de arbejder med følsomme data. Til sidst kan Defender for Cloud Apps beskytte følsomme data overalt i cloudmiljøet, selv uden for Microsoft 365 platform. Det giver organisationer mulighed for at sanktionere (eller fjernesanktion) bestemte eksterne Cloud-apps, styre adgang og overvåge forbrug.
 
[Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp) er en cloudbaseret sikkerhedsløsning, der udnytter dine Active Directory i det lokale miljø signaler til at identificere, registrere og undersøge avancerede trusler, kompromitterede identiteter og skadelige insiderhandlinger, der er rettet mod din organisation. AATP gør det muligt for SecOp-analytikere og sikkerhedseksperter at registrere avancerede angreb i hybridmiljøer for at:
* Overvåg brugere, objektadfærd og aktiviteter ved hjælp af læringsbaseret analyse.
* Beskyt brugeridentiteter og legitimationsoplysninger, der er gemt i Active Directory.
* Identificer og undersøg mistænkelige brugeraktiviteter og avancerede angreb i hele drabskæden.
* Angiv tydelige hændelsesoplysninger på en enkel tidslinje for hurtig triage.

![Kontormedarbejderne mødes i et lille mødelokale. Den ene giver en præsentation.](../media/clo1717-corporate-office-021.jpg)
 
## <a name="govern-data-and-manage-records"></a>Styr data, og administrer poster

Finansielle institutioner skal opbevare deres registre og oplysninger i henhold til deres lovmæssige, juridiske og forretningsmæssige forpligtelser som repræsenteret i deres virksomheds opbevaringsplan. SEC giver f.eks [. opbevaringsperioder](https://www.sec.gov/rules/interp/34-47806.htm) på tre til seks år baseret på posttypen med øjeblikkelig adgang for de første to år. Organisationer står over for juridiske og lovgivningsmæssige risici for overholdelse af angivne standarder, hvis data opbevares for lidt (kasseres for tidligt), og de administrerer nu også regler, der giver mandat til bortskaffelse, når der ikke længere kræves oplysninger. Effektive datastyringsstrategier lægger vægt på en praktisk og ensartet tilgang, så oplysninger bortskaffes korrekt, samtidig med at omkostninger og risici minimeres for organisationen.
 
Derudover kræver myndighedsmandater fra New York State Department of Financial Services, at dækkede enheder vedligeholder politikker og procedurer for bortskaffelse af ikke-offentlige oplysninger. 23 NYCRR 500, section 500.13, Begrænsninger for dataopbevaring kræver, at "Som en del af sit cybersikkerhedsprogram skal hver dækket enhed indeholde politikker og procedurer for sikker bortskaffelse på periodisk basis af ikke-offentlige oplysninger, der er identificeret i afsnit 500.01(g)(2)-(3) i denne del, som ikke længere er nødvendige til forretningsaktiviteter eller til andre legitime forretningsmæssige formål for den dækkede enhed,  medmindre det på anden måde kræves, at sådanne oplysninger opbevares ved lov eller forordning."
 
Finansielle institutioner administrerer store mængder data. Og nogle opbevaringsperioder udløses af hændelser, f.eks. en kontrakt, der udløber, eller en medarbejder, der forlader organisationen. I denne atmosfære kan det være en udfordring at anvende politikker for opbevaring af poster. Tilgange til tildeling af opbevaringsperioder for poster nøjagtigt på tværs af organisationsdokumenter kan variere. Nogle anvender opbevaringspolitikker bredt eller bruger teknikker til automatisk klassificering og maskinel indlæring. Andre identificerer en tilgang, der kræver en mere detaljeret proces, der tildeler opbevaringsperioder entydigt til individuelle dokumenter.

***Microsoft 365 giver fleksible funktioner til at definere opbevaringsmærkater og politikker til intelligent implementering af krav til datastyring.*** En postadministrator definerer en opbevaringsmærkat, som repræsenterer en "posttype" i en traditionel opbevaringsplan. Opbevaringsmærkaten indeholder indstillinger, der definerer disse oplysninger:

- Hvor længe en post bevares
- Hvad sker der, når opbevaringsperioden udløber (slet dokumentet, start en gennemgang af dispositionen, eller udfør ingen handling)
-  Det, der udløser, at opbevaringsperioden starter (oprettelsesdato, dato for seneste ændring, markeret dato eller en hændelse) og markerer dokumentet eller mailen som en post (hvilket betyder, at den ikke kan redigeres eller slettes)

Opbevaringsbeskrivelserne publiceres derefter på SharePoint eller OneDrive websteder, Exchange postkasser og Microsoft 365 grupper. Brugerne kan anvende opbevaringsmærkater manuelt på dokumenter og mails. Postadministratorer kan bruge intelligens til automatisk at anvende mærkaterne. Intelligente funktioner kan være baseret på [halvfems plus indbyggede følsomme informationstyper](../compliance/content-search.md) (f.eks. ABA-udrulningsnummer, US-bankkontonummer eller US Social Security Number). De kan også tilpasses på baggrund af nøgleord eller følsomme data, der findes i dokumenter eller mails, f.eks. kreditkortnumre eller andre personligt identificerbare oplysninger eller baseret på SharePoint metadata. For data, der ikke nemt identificeres via manuel eller automatiseret mønstermatchning, kan klassificeringer, der kan oplæres, bruges til at klassificere dokumenter på en intelligent måde baseret på teknikker til maskinel indlæring.
 
**Værdipapir- og Exchange kommissionen (SEC)** kræver, at mæglerhandlere og andre regulerede finansielle institutioner bevarer al forretningsrelateret kommunikation. Disse krav gælder for mange typer kommunikation og data, herunder mails, dokumenter, chatbeskeder, fax og meget mere. **SEC-regel 17a-4** definerer de kriterier, som disse organisationer skal opfylde for at gemme poster i et elektronisk datalagersystem. I 2003 udsendte SEC en udgivelse, der afklarede disse krav. Den indeholdt følgende kriterier:

* Data, der bevares af et elektronisk lagersystem, skal være ikke-omskrivelige og ikke-slettelige. Dette kaldes et WORM-krav (skriv én gang, læs mange).
* Lagringssystemet skal kunne gemme data ud over den opbevaringsperiode, der kræves i henhold til reglen, hvis der er tale om en stævning eller en anden retsorden.
* En organisation overtræder ikke kravet i reglens afsnit (f)(2)(ii)(A), hvis den brugte et elektronisk lagersystem, der forhindrer overskrivning, sletning eller på anden måde ændring af en post i løbet af den påkrævede opbevaringsperiode ved hjælp af integrerede hardware- og softwarekontrolkoder.
* Elektroniske lagersystemer, der blot "afhjælper" risikoen for, at en post overskrives eller slettes, f.eks. ved at være afhængig af adgangskontrol, opfylder ikke kravene i reglen.

For at hjælpe finansielle institutioner med at opfylde kravene i SEC-regel 17a-4 indeholder Microsoft 365 en kombination af funktioner, der er relateret til, hvordan data bevares, politikker konfigureres, og data gemmes i tjenesten. Disse omfatter:

* **Bevarelse af data (regel 17a-4(a), (b)(4)) – opbevaringsmærkater** og politikker er fleksible til at imødekomme organisationens behov og kan anvendes automatisk eller manuelt på forskellige typer data, dokumenter og oplysninger. En lang række datatyper og kommunikation understøttes, herunder dokumenter i SharePoint og OneDrive for Business, data i Exchange Online postkasser og data i Teams.  
* **Format, der ikke kan omskrives, kan ikke slettes (regel 17a-4(f)(2)(ii)(A))** – funktionen Bevarelseslås for opbevaringspolitikker gør det muligt for dataadministratorer og administratorer at konfigurere opbevaringspolitikker for at være restriktive, så de ikke længere kan ændres. Dette forhindrer alle i på nogen måde at fjerne, deaktivere eller ændre opbevaringspolitikken. Det betyder, at når Bevarelseslås er aktiveret, kan den ikke deaktiveres, og der er ingen metode til, at data, som opbevaringspolitikken er blevet anvendt på, kan overskrives, ændres eller slettes i løbet af opbevaringsperioden. Derudover kan opbevaringsperioden ikke forkortes. Opbevaringsperioden kan dog forlænges, når der er et juridisk krav om at fortsætte opbevaringen af data.<br/><br/>Når der anvendes en bevarelseslås på en opbevaringspolitik, begrænses følgende handlinger:

  - Opbevaringsperioden for politikken kan kun øges. Det kan ikke forkortes.
  - Brugere kan føjes til politikken, men eksisterende brugere, der er konfigureret i politikken, kan ikke fjernes.
   - Opbevaringspolitikken kan ikke slettes af nogen administrator i organisationen.
 
  Bevarelseslås hjælper med at sikre, at ingen bruger, ikke engang administratorer med de højeste niveauer af privilegeret adgang, kan ændre indstillingerne, ændre, overskrive eller slette de data, der er blevet gemt, hvilket medfører, at arkivering i Microsoft 365 i overensstemmelse med vejledningen i SEC 2003-versionen.

* **Kvalitet, nøjagtighed og bekræftelse af lagring/serialisering og indeksering af data (Regel 17a-4(f)(2) (ii)(B) og (C))** – Office 365 arbejdsbelastninger indeholder hver især funktioner til automatisk at kontrollere kvaliteten og nøjagtigheden af processen til registrering af data på lagermedier. Derudover gemmes data ved hjælp af metadata og tidsstempler for at sikre tilstrækkelig indeksering til at muliggøre effektiv søgning efter og hentning af data.
 
* **Separat lager til kopier af dubletter (Regel 17a-4(f)(3(iii))** – Cloudtjenesten Office 365 gemmer dubletter af data som et centralt aspekt af dens høje tilgængelighed. Dette opnås ved at implementere redundans på alle niveauer af tjenesten, herunder på det fysiske niveau på alle servere, på serverniveau i datacenteret og på tjenesteniveau for geografisk spredte datacentre.

* **Data, der kan downloades og er tilgængelige (Regel 17a-4(f)(2)(ii)(D))** – Office 365 tillader generelt, at data, der er mærket til opbevaring, søges efter, tilgås og downloades på stedet. Og det gør det muligt at søge efter data i Exchange Online-arkiver ved hjælp af indbyggede eDiscovery-funktioner. Data kan derefter downloades efter behov i standardformater, herunder EDRML og PST.
 
* **Overvågningskrav (Regel 17a-4(f)(3)(v))** – Office 365 giver overvågningslogføring for alle administrative handlinger og brugerhandlinger, der ændrer dataobjekter, konfigurerer eller ændrer opbevaringspolitikker, udfører eDiscovery-søgninger eller ændrer adgangstilladelser. Office 365 vedligeholder et omfattende revisionsspor, herunder data om, hvem der udførte en handling, hvornår den blev udført, oplysninger om handlingen og de kommandoer, der blev udført. Overvågningsloggen kan derefter udskrives og inkluderes som en del af formelle overvågningsprocesser efter behov.

Endelig kræver Regel 17a-4, at organisationer opbevarer poster for mange typer transaktioner, så de er umiddelbart tilgængelige i to år. Poster skal opbevares yderligere i tre til seks år med ikke-umiddelbar adgang. Dubletposter skal også opbevares i samme periode på en placering uden for stedet. Microsoft 365 funktioner til administration af poster gør det muligt at bevare poster, så de ikke kan redigeres eller slettes, men det er nemt at få adgang til dem i en bestemt periode, der styres af postadministratoren. Disse perioder kan strække sig over dage, måneder eller år afhængigt af organisationens overholdelse af angivne standarder.
 
Efter anmodning leverer Microsoft en bekræftelsesbrev om overholdelse af SEC 17a-4, hvis det kræves af en organisation.

Derudover hjælper disse funktioner også Microsoft 365 med at opfylde lagerkrav til [CFTC Rule 1.31(c)-(d)](https://www.cftc.gov/sites/default/files/opa/press99/opa4266-99-attch.htm) fra **U.S. Commodity Futures Trading Commission** og [FINRA Rule Series 4510](https://www.finra.org/rules-guidance/rulebooks/finra-rules/4511) fra den **finansielle branchetilsynsmyndighed.** Samlet repræsenterer disse regler den mest præskriptive vejledning globalt, så finansielle institutioner kan opbevare poster.

Yderligere oplysninger om, hvordan Microsoft 365 overholder SEC-regel 17a-4 og andre bestemmelser, findes under [Vurdering af Office 365 Exchange Online SEC 17a-4(f) / CFTC 1.31(c)-(d) af Cohasset Associates](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=9fa8349d-a0c9-47d9-93ad-472aa0fa44ec&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers).

## <a name="establish-ethical-walls-with-information-barriers"></a>Etabler etiske vægge med informationsbarrierer

Finansielle institutioner kan være underlagt regler, der forhindrer medarbejdere i visse roller i at udveksle oplysninger eller samarbejde med andre roller. FINRA har f.eks. offentliggjort regler 2241(b)(2)(G), 2242(b)(2) (D), (b)(2)(H)(ii) og (b)(2)(H)(iii), som kræver, at medlemmerne skal:

"(G) etablere informationsbarrierer eller andre institutionelle sikkerhedsforanstaltninger, der med rimelighed har til formål at sikre, at forskningsanalytikere er isoleret fra gennemgang, pres eller tilsyn af personer, der udfører aktiviteter inden for investeringsbanktjenester, eller andre personer, herunder salgs- og handelspersonale, som kan være forudindtaget i deres vurdering eller tilsyn", og "(H) etablere informationsbarrierer eller andre institutionelle sikkerhedsforanstaltninger, der med rimelighed har til formål at sikre, at analytikere af gældsforskning isoleres fra  gennemgang, pres eller tilsyn foretaget af personer, der er beskæftiget med: i) investeringsbanktjenester ii) hovedvirksomhed i forbindelse med handel eller salg og handel og (iii) andre personer, der kan være forudindtaget i deres dom eller tilsyn;"

I sidste ende kræver disse regler, at organisationer etablerer politikker og implementerer informationsbarrierer mellem roller, der er involveret i banktjenester, salg eller handel fra udveksling af oplysninger og kommunikation med analytikere.

[Informationsbarrierer](../compliance/information-barriers.md) giver mulighed for at etablere etiske vægge i dit Office 365 miljø, så administratorer af overholdelse eller andre godkendte administratorer kan definere politikker, der tillader eller forhindrer kommunikation mellem grupper af brugere i Teams. Informationsbarrierer kontrollerer specifikke handlinger for at forhindre uautoriseret kommunikation. Informationsbarrierer kan også begrænse kommunikationen i scenarier, hvor interne teams arbejder med fusioner/opkøb eller følsomme handler eller arbejder med følsomme interne oplysninger, der skal begrænses meget.

Informationsbarrierer understøtter samtaler og filer i Teams. De kan forhindre følgende typer kommunikationsrelaterede handlinger for at hjælpe med at overholde FINRA-forskrifterne:

* Søg efter en bruger
* Føj et medlem til et team, eller fortsæt med at deltage med et andet medlem i et team
* Start eller fortsæt en chatsession
* Start eller fortsæt en gruppechat
* Inviter en person til at deltage i et møde
* Del en skærm
* Foretag et opkald

## <a name="implement-supervisory-control"></a>Implementer tilsynskontrol

Finansielle institutioner er typisk forpligtet til at etablere og vedligeholde en tilsynsfunktion i deres organisationer for at overvåge de ansattes aktiviteter og for at hjælpe den med at opnå overholdelse af gældende værdipapirlovgivning. FINRA har specifikt fastlagt disse tilsynskrav:
 
* [FINRA-regel 3110 (tilsyn)](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3110) kræver, at virksomhederne skal have skriftlige tilsynsprocedurer (WSP'er) til at føre tilsyn med sine medarbejderes og virksomhedstyper. Ud over andre krav skal procedurerne omfatte:
   - Tilsyn med tilsynspersonale
   - Gennemgang af en virksomheds investeringsbank, værdipapirforretning, intern kommunikation og interne undersøgelser
   - Gennemgang af transaktioner for insiderhandel
   - Gennemgang af korrespondance og klager

   Procedurerne skal beskrive de personer, der er ansvarlige for gennemgange, tilsynsaktiviteter, som hver enkelt person skal udføre, hyppigheden af gennemgangen og typerne af dokumentation eller kommunikation, der undersøges.
 
* [FINRA-regel 3120 (Tilsynskontrolsystem)](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3120) kræver, at virksomhederne har et system med tilsynspolitikker og -procedurer, der validerer deres skriftlige tilsynsprocedurer som defineret i regel 3110. Virksomhederne skal ikke blot have WSP'er, men også have politikker, der tester disse procedurer årligt for at validere deres evne til at sikre overholdelse af gældende love og bestemmelser om sikkerhedsstillelse. Risikobaserede metoder og stikprøvetagning kan bruges til at definere omfanget af test. Denne regel kræver blandt andet, at virksomhederne skal forelægge en årlig rapport til den øverste ledelse, der indeholder en oversigt over testresultaterne og eventuelle væsentlige undtagelser eller ændrede procedurer som svar på testresultaterne.

![En kontormedarbejder får vist et diagram og tabeller på en skærm, mens andre mødes i baggrunden.](../media/wco18-desk-work-002.jpg)
 
### <a name="communication-compliance"></a>Kommunikationsoverholdelse

Kommunikationsoverholdelse gør det muligt for organisationer at forudkonfigurere politikker for at registrere medarbejderkommunikation til overvågning og gennemgang af godkendte vejledere. Politikker for overholdelse af angivne standarder for kommunikation kan registrere interne/eksterne mails og vedhæftede filer, Teams chat og kanalkommunikation og Skype for Business onlinechatkommunikation og vedhæftede filer. Derudover kan kommunikation med overholdelse af angivne standarder indtage kommunikation og data fra tredjepartstjenester (f.eks. Bloomberg, Thomson Reuters, LinkedIn, Twitter, Facebook, Box og Dropbox).
Den omfattende karakter af kommunikation, der kan registreres og gennemses i en organisation, og de omfattende betingelser, som politikker kan konfigureres med, gør det muligt for kommunikationspolitikker at hjælpe finansielle institutioner med at overholde FINRA-regel 3110. Politikker kan konfigureres til at gennemse kommunikation for enkeltpersoner eller grupper.  Udpegede vejledere kan tildeles på individuelt eller gruppeniveau. Omfattende betingelser kan konfigureres til at registrere kommunikation baseret på indgående eller udgående meddelelser, domæner, opbevaringsmærkater, nøgleord eller udtryk, nøgleordsordbøger, følsomme datatyper, vedhæftede filer, meddelelsesstørrelse eller størrelse på vedhæftede filer. Korrekturlæsere får et dashboard, hvor de kan gennemse meddelelser, der er markeret med flag, reagere på kommunikation, der potentielt overtræder politikker, og markere elementer, der er markeret som løst. De kan også gennemse resultaterne af korrekturer og elementer, der tidligere blev løst.
  
Kommunikation med overholdelse af angivne standarder indeholder rapporter, der gør det muligt at overvåge aktiviteter for politikgennemsyn baseret på politikken og korrekturlæseren. Rapporter er tilgængelige til at validere, at politikker fungerer som defineret af en organisations skriftlige overvågningspolitikker. De kan også bruges til at identificere kommunikation, der kræver gennemgang, og dem, der ikke overholder virksomhedens politik. Endelig overvåges alle aktiviteter i forbindelse med konfiguration af politikker og gennemgang af kommunikation i Office 365 samlede overvågningslog. Derfor hjælper overholdelse af kommunikation også finansielle institutioner med at overholde FINRA-regel 3120.

Ud over at overholde FINRA-regler giver kommunikationsoverholdelse organisationer mulighed for at overvåge kommunikation for overholdelse af andre juridiske krav, virksomhedspolitikker og etiske standarder. Kommunikation med overholdelse af angivne standarder giver indbyggede trussels-, chikane- og bandeordsklassifikationer, der hjælper med at reducere falske positiver, når de gennemgår kommunikation, hvilket sparer korrekturlæsere tid under undersøgelsen og afhjælpningsprocessen. Det giver også organisationer mulighed for at reducere risikoen ved at overvåge kommunikation, når de undergår følsomme ændringer, såsom fusioner og opkøb eller lederændringer.

![En informationsmedarbejder fokuserer på en skærm.](../media/msc16-slalom-004.jpg)
 
## <a name="protect-against-data-exfiltration-and-insider-risk"></a>Beskyt mod dataudfiltrering og insiderrisiko

En almindelig trussel mod virksomheder er dataudfiltrering eller udtrækning af data fra en organisation. Denne risiko kan være et betydeligt problem for finansielle institutioner på grund af den følsomme karakter af de oplysninger, der kan tilgås dag for dag. Med det stigende antal tilgængelige kommunikationskanaler og udbredelsen af værktøjer til flytning af data kræves der typisk avancerede funktioner for at afhjælpe risikoen for datalækager, politikovertrædelser og insiderrisiko.

### <a name="insider-risk-management"></a>Styring af insider-risiko

Aktivering af medarbejdere med online samarbejdsværktøjer, der kan tilgås overalt, udgør en risiko for organisationen. Medarbejdere kan utilsigtet eller ondsindet lække data til angribere eller konkurrenter.  Alternativt kan de exfiltrate data til personlig brug eller tage data med dem til en fremtidig arbejdsgiver. Disse scenarier udgør alvorlige risici for finansielle institutioner både set fra et sikkerheds- og overholdelses synspunkt. Identificering af disse risici, når de opstår, og hurtig afhjælpning af dem kræver både intelligente værktøjer til dataindsamling og samarbejde på tværs af afdelinger, f.eks. juridiske, personale og informationssikkerhed.

Microsoft 365 for nylig lanceret en løsning til styring af insiderrisiko, der korrelerer signaler på tværs af Microsoft 365 tjenester og bruger modeller til maskinel indlæring til at analysere brugeradfærd for skjulte mønstre og tegn på insiderrisiko. Dette værktøj muliggør samarbejde mellem sikkerhedshandlinger, interne efterforskere og HR, så de nemt kan afhjælpe sager baseret på forudbestemte arbejdsprocesser.  

Styring af insiderrisiko kan f.eks. korrelere signaler fra en brugers Windows 10 desktop, f.eks. kopiere filer til et USB-drev eller sende en personlig mailkonto, med aktiviteter fra onlinetjenester f.eks. Office 365 mail, SharePoint Online, Microsoft Teams eller OneDrive for Business for at identificere dataudfiltreringsmønstre. Det kan også korrelere disse aktiviteter med medarbejdere, der forlader en organisation, hvilket er et almindeligt dataudfiltreringsmønster. Den kan overvåge flere aktiviteter og funktionsmåder over tid. Når der opstår almindelige mønstre, kan det udløse beskeder og hjælpe efterforskerne med at fokusere på vigtige aktiviteter for at bekræfte en politikovertrædelse med en høj grad af tillid. Styring af insiderrisiko kan pseudo-anonymisere data fra efterforskere for at hjælpe med at overholde reglerne for beskyttelse af personlige oplysninger, mens de stadig indeholder vigtige aktiviteter, der hjælper dem med at udføre undersøgelser effektivt. Det giver efterforskerne mulighed for at pakke og sikkert sende vigtige aktivitetsdata til hr- og juridiske afdelinger efter almindelige eskaleringsarbejdsprocesser for at rejse sager til afhjælpningshandling.

Styring af insiderrisiko øger funktionaliteten i organisationer betydeligt til at overvåge og undersøge insiderrisici, samtidig med at organisationer stadig kan overholde reglerne for beskyttelse af personlige oplysninger og følge etablerede eskaleringsstier, når sager kræver handling på højere niveau. Du kan få flere oplysninger om styring af insiderrisiko under [Moderne punkter for risikosmerter og Arbejdsproces i Styring af insiderrisiko](../compliance/insider-risk-management.md).

![En medarbejder i et callcenter i en kontormiljøtype, mens den får vist en skærm.](../media/clo17-call-center-006.jpg)

### <a name="tenant-restrictions"></a>Lejerbegrænsninger

Organisationer, der behandler følsomme data og lægger stor vægt på sikkerhed, vil typisk kontrollere de onlineressourcer, som brugerne kan få adgang til. Samtidig vil de muliggøre et sikkert samarbejde via onlinetjenester som f.eks. Office 365. Derfor bliver det en udfordring at styre de Office 365 miljøer, som brugerne kan få adgang til, fordi ikke-virksomheds-Office 365 miljøer kan bruges til at eksfiltrere data fra virksomhedens enheder enten ondsindet eller utilsigtet. Organisationer begrænser traditionelt de domæner eller IP-adresser, som brugerne kan få adgang til fra virksomhedens enheder. Men det fungerer ikke i en verden, hvor brugerne har brug for lovligt at få adgang til Office 365 tjenester.

Microsoft 365 angiver [lejerbegrænsningerne](/azure/active-directory/manage-apps/tenant-restrictions) for muligheden for at håndtere denne udfordring. Lejerbegrænsninger kan konfigureres til at begrænse medarbejderadgang til eksterne Office 365 virksomhedslejere ved hjælp af rogue-identiteter (identiteter, der ikke er en del af din virksomhedsmappe). I dag gælder der lejerbegrænsninger på tværs af lejeren, hvilket kun giver adgang til de lejere, der vises på den liste, du konfigurerer. Microsoft fortsætter med at udvikle denne løsning for at øge granulariteten af kontrollen og forbedre den beskyttelse, den giver.

![GRAFISK.](../media/clo1717-corporate-office-001.jpg)

## <a name="conclusion"></a>Konklusion

Microsoft 365 og Teams levere en integreret og omfattende løsning til finansielle servicevirksomheder, hvilket muliggør enkle, men effektive cloudbaserede samarbejds- og kommunikationsfunktioner på tværs af virksomheden. Ved hjælp af teknologier til sikkerhed og overholdelse af angivne standarder fra Microsoft 365 kan institutioner arbejde på en mere sikker og kompatibel måde med robuste sikkerhedskontroller for at beskytte data, identiteter, enheder og programmer mod forskellige driftsrisici, herunder cybersikkerhed og insiderrisici. Microsoft 365 er en grundlæggende sikker platform, som organisationer for finansielle tjenesteydelser kan opnå mere på, samtidig med at de beskytter deres virksomhed, medarbejdere og kunder.
