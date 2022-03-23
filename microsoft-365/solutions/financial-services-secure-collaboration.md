---
title: Vigtige overvejelser i forbindelse med overholdelse og sikkerhed for det amerikanske bank- og kapitalmarked
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
description: Få mere at vide om, hvordan den finansielle sektor kan opretholde overholdelse af finansielle regler og standarder og samarbejde effektivt Microsoft 365 og Teams.
f1.keywords: NOCSH
ms.openlocfilehash: e94ad0e1f7b6f0c8b76f40b6492f69b23655855c
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63590038"
---
# <a name="key-compliance-and-security-considerations-for-us-banking-and-capital-markets"></a>Vigtige overvejelser i forbindelse med overholdelse og sikkerhed for det amerikanske bank- og kapitalmarked

## <a name="introduction"></a>Introduktion
Den finansielle sektor overstiger næsten alle kommercielle virksomheder i deres behov for strenge kontroller af sikkerhed, overholdelse og styring. Beskyttelse af data, identiteter, enheder og programmer er ikke kun afgørende for deres virksomhed, den er underlagt overholdelseskrav og retningslinjer fra lovgivningsmæssige organisationer som f.eks. USA Securities og Exchange Commission (SEC), DEN finansielle branche (FINRA), det føderale finansieringsinstitution – undersøgelsesråd for finansielle institutioner (FFIEC) og den finansielle futures trade Commission (CFTC). Desuden er finansielle institutioner underlagt love som f.eks. Dodd-Frank og Sarbanes-Oxley act of 2002.

I nutidens verden af øget fleksibilitet til sikkerhed, insider-risikoproblemer og offentlige databrider kræver kunderne også et højt sikkerhedsniveau fra deres finansielle institutioner for at kunne stole på deres personlige data og bankaktiver.

Historisk set har behovet for omfattende kontrolelementer direkte påvirket og begrænset de it-systemer og platforme, som de finansielle institutioner bruger til at samarbejde internt og eksternt. I dag har medarbejdere i den finansielle sektor brug for en moderne samarbejdsplatform, der er nem at indføre og brugervenlig. Men finansielle tjenester kan ikke handle med fleksibilitet til at samarbejde mellem brugere, teams og afdelinger med sikkerheds- og overholdelseskontroller, der gennemtvinger politikker for at beskytte brugere og it-systemer mod trusler.

Inden for den finansielle sektor er der behov for nøje overvejelser i forbindelse med konfiguration og implementering af samarbejdsværktøjer og sikkerhedskontrolelementer, herunder:
- Risikovurdering af almindelige scenarier for organisatorisk samarbejde og forretningsproces
- Krav til beskyttelse af oplysninger og datastyring
- Cybersikkerhed og insidertrusler
- Lovmæssige krav til overholdelse af regler og standarder
- Andre driftsrisici

**Microsoft 365 er et moderne skymiljø på arbejdspladsen, som kan tage hånd om de udfordringer, som organisationer med finansielle tjenester står over for. Sikkert og fleksibelt samarbejde på tværs af virksomheden kombineres med kontrolelementer og håndhævelse af politikker for at overholde strenge lovgivningsmæssige rammer.** I denne artikel beskrives det, hvordan den Microsoft 365-platform hjælper de finansielle tjenester med at flytte til en moderne samarbejdsplatform, og hjælper med at holde data og systemer sikre og overholde bestemmelser:

* Aktivér produktivitet for organisationen og medarbejderne ved hjælp Microsoft 365 og Microsoft Teams
* Beskyt moderne samarbejde ved hjælp af Microsoft 365 
* Identificer følsomme data, og undgå tab af data
* Forsvar den besfæst
* Styre data og overholde bestemmelser ved effektiv administration af data
* Opret etiske vægge med informationsbarrierer
* Beskyt dig mod dataudfyldning og insider-risiko

Som Microsoft-partner bvirkede Protiviti til og gav materialefeedback til denne artikel.

Følgende illustrationer, der kan downloades, supplerer denne artikel. Woodgrove Bank og Contoso bruges til at demonstrere, hvordan de funktioner, der er beskrevet i denne artikel, kan anvendes til at løse almindelige lovmæssige krav vedrørende finansielle tjenester. Du er velkommen til at tilpasse disse illustrationer til eget brug. 

**Microsoft 365 illustrationer om beskyttelse af oplysninger og overholdelse af regler og standarder**

| Element | Beskrivelse |
|:-----|:-----|
|[![Modelplakat: Microsoft 365 funktioner til beskyttelse af oplysninger og overholdelse af regler og standarder.](../media/solutions-architecture-center/m365-compliance-illustrations-thumb.png)](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf) <br/>Engelsk: [Download som PDF-download](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf)\| [som Visio](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.vsdx)   <br/> Japansk: [Download som PDF-download](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.pdf)\| [som Visio](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.vsdx)  <br/> Opdateret i november 2020|Omfatter: <ul><li>  Microsoft-beskyttelse af oplysninger og forebyggelse af datatab</li><li>Opbevaringspolitikker og opbevaringsnavne </li><li>Informationsbarrierer</li><li>Kommunikationsoverholdelse</li><li>Insider-risiko</li><li>Tredjepartsdataindtrindelse</li>|


## <a name="empower-organizational-and-employee-productivity-by-using-microsoft-365-and-teams"></a>Giv organisatorisk og medarbejderproduktivitet ved hjælp af Microsoft 365 og Teams

Samarbejde kræver typisk forskellige former for kommunikation, mulighed for at gemme og få adgang til dokumenter/data og muligheden for at integrere andre programmer efter behov. Medarbejdere i den finansielle sektor har typisk brug for at samarbejde og kommunikere med medlemmer af andre afdelinger eller teams og nogle gange med eksterne enheder. Derfor er det uønsket at bruge systemer, der opretter siloer eller gør det svært at dele oplysninger. I stedet er det at foretrække at udnytte platforme og programmer, der giver medarbejderne mulighed for at kommunikere, samarbejde og dele oplysninger sikkert og i henhold til virksomhedens politik.

Ved at give medarbejderne en moderne, skybaseret samarbejdsplatform kan de vælge og integrere værktøjer, der gør dem mere produktive og giver dem mulighed for at finde Agile-måder at arbejde på. Brug Teams sammen med sikkerhedskontrolelementer og politikker for informationsstyring, der beskytter organisationen, kan hjælpe medarbejderne med at kommunikere og samarbejde effektivt.

Teams en samarbejdshub for organisationen. Det hjælper med at samle personer, så de kan arbejde produktivt på almindelige initiativer og projekter. Teams gør det muligt for teammedlemmer at føre 1:1- og chatsamtaler med flere parter, samarbejde og udføre samtidig redigering af dokumenter samt gemme og dele filer. Teams letter også onlinemøder via integreret tale og video for virksomheder. Teams kan også tilpasses med Microsoft-apps som Microsoft Planner, Microsoft Dynamics 365, Power Apps, Power BI og line of business-programmer fra tredjeparter. Teams er beregnet til brug af både interne teammedlemmer og tilladte eksterne brugere, der kan deltage i teamkanaler, deltage i chatsamtaler, få adgang til gemte filer og udnytte andre programmer

Alle Microsoft-teams understøttes af en Microsoft 365 gruppe. Den pågældende gruppe betragtes som tjenesten medlemskab for mange Office 365 tjenester, herunder Teams. Microsoft 365 grupper bruges til sikkert at skelne mellem "ejere" og "medlemmer" og til at kontrollere adgangen til forskellige funktioner inden for Teams. Når de er kombineret med relevante styringskontroller og regelmæssigt administrerede adgangsvurderinger, tillader Teams kun medlemmer og ejere at benytte autoriserede kanaler og egenskaber.

Et almindeligt scenarie, Teams fordel ved finansielle tjenester, er ved kørsel af interne projekter eller programmer. Mange finansielle institutioner, herunder banker, udbydere af pengestyring, kreditorganisationer og forsikringsudbydere, skal f.eks. have antipenge og andre programmer til overholdelse af regler og standarder på plads. Et tværfunktionelt team bestående af IT, forretningsområder som f.eks. detail- og pengestyring og en finansiel gerningsenhed kan være nødvendig for at dele data med hinanden og kommunikere om programmet eller bestemte undersøgelser. Traditionelt har disse programmer brugt delte netværksdrev, men denne tilgang kan være en lang række udfordringer, herunder:
* Kun én person kan redigere et dokument ad gangen.
* Administration af sikkerhed er tidskrævende, fordi tilføjelse/fjernelse af enkeltpersoner typisk involverer it.
* Data forbliver iboende på delte netværksdrev meget længere end påkrævet eller ønsket.

Teams kan give et samarbejdsrum til sikkert at gemme følsomme kundedata og føre samtaler mellem teammedlemmer, hvor der kan diskuteres følsomme emner. Flere medlemmer af teamet kan redigere eller samarbejde om et enkelt dokument på samme tid. Programejeren eller -ejeren kan konfigureres som teamejer og kan derefter tilføje og fjerne medlemmer efter behov.

Et andet almindeligt scenarie er at Teams som et "virtuelt datarum" til sikkert samarbejde, herunder lagring og administration af dokumenter. Teammedlemmer og syndikere inden for investeringsbank, aktivstyring eller private firmaer, der kan samarbejde sikkert om en handel eller investering. Tværfunktionelle teams er ofte involveret i planlægning og udførelse af sådanne aftaler, og muligheden for at dele data og føre samtaler sikkert er et grundlæggende krav. Sikker deling af relaterede dokumenter med eksterne investorer er også et vigtigt krav. Teams et sikkert og fuldt auditable sted, hvorfra data kan lagres, beskyttes og deles centralt.

![En gruppe af kontormedarbejdere på et møde diskuterer billeder på en stor puds.](../media/m365cO19-ent-dell-latitude13-5951.jpg)
 
### <a name="teams-improve-collaboration-and-reduce-compliance-risk"></a>Teams: Forbedr samarbejde og reducer risikoen for overholdelse af regler og standarder

Microsoft 365 indeholder andre almindelige politikfunktioner til Teams dens brug af Microsoft 365 som en underliggende medlemskabstjeneste. Disse politikker kan hjælpe med at forbedre samarbejde og opfylde overholdelsesbehov.

**Microsoft 365 navngivningspolitikker for grupper** er med til at sikre, Microsoft 365 grupper, og derfor teams, navngives i henhold til virksomhedens politik. Navne kan være problematiske, hvis de ikke er relevante. Medarbejdere ved måske ikke, hvilke teams de skal arbejde med, eller de kan dele oplysninger med, hvis navne ikke anvendes korrekt. Politikker for gruppenavngivning (herunder understøttelse af præfiks-/suffiksbaserede politikker og bruger blokerede ord) kan gennemtvinge gode "sprogbrug" og forhindre brug af bestemte ord, f.eks. reserverede ord eller upassende terminologi.
  
**Microsoft 365 udløbspolitikker** for grupper er med til at sikre, Microsoft 365 grupper og derfor teams ikke bevares i længere tid, end organisationen ønsker eller har brug for. Denne funktion hjælper med at forhindre to vigtige problemer med administration af oplysninger:

* Spredning af teams, der ikke er nødvendige eller anvendes.
* Overopbevaring af data, der ikke længere er påkrævet eller bruges af organisationen (undtagen i tilfælde af retslig tilbageholdelse/bevaring).

Administratorer kan angive en udløbsperiode for Microsoft 365 grupper, f.eks. 90, 180 eller 365 dage. Hvis en tjeneste, der understøttes af en Microsoft 365 gruppe, er inaktiv i udløbsperioden, får gruppeejere besked. Hvis der ikke sker noget, Microsoft 365 gruppen og alle dens relaterede tjenester, herunder Teams, slettet.
  
Den overbevaring af data, der er gemt i Teams og andre gruppebaserede tjenester, kan udgøre en risiko for organisationer inden for den finansielle sektor. Microsoft 365 gruppes udløbspolitikker er en anbefalet metode til at forhindre opbevaring af data, der ikke længere er nødvendige. Kombineret med indbyggede opbevaringsmærkater og politikker hjælper Microsoft 365 med at sikre, at organisationer kun opbevarer de data, der er nødvendige for at overholde virksomhedens politikker og lovmæssige overholdelsesforpligtelser.

#### <a name="teams-integrate-custom-requirements-with-ease"></a>Teams: Integrer brugerdefinerede krav uden besvær

Teams mulighed for selvbetjeningsoprettelse af teams som standard. Mange regulerede organisationer ønsker dog at kontrollere og forstå, hvilke samarbejdskanaler deres medarbejdere aktuelt bruger, hvilke kanaler kan indeholde følsomme data og ejerskabet af organisationskanaler. For at facilitere disse styringskontrolforanstaltninger Microsoft 365 organisationen deaktivere oprettelse af selvbetjeningsteams. Ved hjælp af automatiseringsværktøjer til forretningsprocesser som f.eks. Microsoft Power Apps og Power Automate kan organisationer oprette og implementere simple formularer og godkendelsesprocesser, som medarbejderne kan bruge til at anmode om oprettelse af et nyt team. Når de er godkendt, kan teamet klargøres automatisk, og der sendes et link til anmoderen. På denne måde kan organisationer designe og integrere deres kontrolelementer til overholdelse af regler og standarder og brugerdefinerede krav i processen til oprettelse af teams.
 
### <a name="acceptable-digital-communication-channels"></a>Acceptable digitale kommunikationskanaler

FINRA fremhæver, at den digitale kommunikation for regulerede selskaber opfylder kravene til registrering i [Exchange Act rules 17a-3 og 17a-4 samt FINRA-regelserie 4510](https://www.finra.org/rules-guidance/key-topics/books-records). FINRA udgiver en årlig rapport, der indeholder vigtige resultater, observationer og effektive fremgangsmåder til at hjælpe organisationer med at forbedre overholdelse og risikostyring. FINRA identificerede i [sin rapport for 2019](https://www.finra.org/rules-guidance/guidance/reports/2019-report-exam-findings-and-observations) om undersøgelsesresultater og observationer digital kommunikation som et vigtigt område, hvor virksomheder oplever udfordringer med at overholde krav til overvågning og registrering.

Hvis en organisation tillader medarbejderne at bruge et bestemt program, f.eks. en appbaseret meddelelsestjeneste eller samarbejdsplatform, skal virksomheden arkivere forretningsposter og overvåge disse medarbejderes aktiviteter og kommunikation i det pågældende program. Organisationer er ansvarlige for at udføre på grund af manglende overholdelse af FINRA-regler og love om værdipapirer og for at følge op på potentielle overtrædelser af disse regler i forbindelse med medarbejderbrug af sådanne apps.
  
Effektive fremgangsmåder anbefalet af FINRA omfatter følgende:
* Opret et omfattende styringsprogram til digitale kommunikationskanaler. Administrer organisationens beslutninger om, hvilke digitale kommunikationskanaler der er tilladte, og definer overholdelsesprocesser for hver digital kanal. Hold nøje øje med det hurtige skiftende landskab for digitale kommunikationskanaler, og hold overholdelsesprocesser opdateret.
* Definer og styr tydeligt de digitale kanaler, der er digitale kanaler. Definer både godkendte og forbudte digitale kanaler. Blokere eller begrænse brugen af forbudte digitale kanaler eller forbudte funktioner i digitale kanaler, der begrænser organisationens evne til at overholde krav til datastyring og kontrol.
* Giv kurser til digital kommunikation. Implementer obligatoriske undervisningsprogrammer, før du giver registrerede repræsentanter adgang til godkendte digitale kanaler. Kurser hjælper med at tydeliggøre en organisations forventninger til den forretningsmæssige og personlige digitale kommunikation, og det vejleder medarbejderne gennem brugen af tilladte funktioner i hver kanal i overensstemmelse med reglerne.

FINRA's resultater og observationer for Digital communications er direkte relateret til en organisations mulighed for at overholde [SEC-regel 17a-4](https://www.law.cornell.edu/cfr/text/17/240.17a-4) for at bevare al forretningsrelateret kommunikation, FINRA-regler [3110](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3110) og [3120](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3120) til overvågning og gennemgang af kommunikation og Regelserie [4510](https://www.finra.org/rules-guidance/rulebooks/finra-rules/4510) til registrering. The Commodity Futures Trade Commission (CFTC) promulgates similar requirements under 17 CFR 131. Disse bestemmelser diskuteres i dybden senere i denne artikel.

***Teams giver, sammen med den omfattende pakke med Microsoft 365-sikkerheds- og overholdelsestilbud, en virksomhedskanal for digitale kommunikationstjenester til den finansielle sektor, så de effektivt kan udføre forretningsmæssige aktiviteter og overholde bestemmelser.*** Resten af denne artikel beskriver, hvordan Microsoft 365 indbyggede funktioner til datastyring, beskyttelse af oplysninger, informationsbarrierer og kontrolkontrol giver Teams et robust værktøjssæt, der kan hjælpe med at opfylde disse lovmæssige forpligtelser.

## <a name="protect-modern-collaboration-with-microsoft-365"></a>Beskyt moderne samarbejde med Microsoft 365

### <a name="secure-user-identities-and-control-access"></a>Sikre brugeridentiteter og kontrollere adgang

***Beskyttelse af adgang til kundeoplysninger, økonomiske dokumenter og programmer starter med en stærk beskyttelse af brugeridentiteter.*** Dette kræver en sikker platform, hvor virksomheden kan lagre og administrere identiteter, give en pålidelig godkendelsesmetode og dynamisk kontrollere adgangen til disse programmer.

Når medarbejdere arbejder, kan de flytte fra program til program eller mellem flere placeringer og enheder. Adgang til data skal godkendes på hvert trin undervejs. Godkendelsesprocessen skal understøtte en stærk protokol og flere faktorer for godkendelse (f.eks. engangs-sms-adgangskode, godkenderapp og certifikat) for at sikre, at identiteter ikke kompromitteres. Det er afgørende at håndhæve risikobaserede adgangspolitikker for at beskytte finansielle data og programmer mod Insider-trusler, utilsigtede datalækager og dataudfyldning.

Microsoft 365 en sikker identitetsplatform [i Azure Active Directory (Azure AD),](/azure/active-directory/) hvor identiteter gemmes centralt og administreres sikkert. Azure AD udgør sammen med en lang række relaterede Microsoft 365-sikkerhedstjenester grundlaget for at give medarbejderne den adgang, de skal bruge for at arbejde sikkert, og samtidig beskytte organisationen mod trusler.

[Azure AD MFA (Multi-Factor Authentication)](/azure/active-directory/fundamentals/concept-fundamentals-mfa-get-started) er indbygget i platformen og giver en ekstra godkendelsesbevis for at bekræfte brugeridentiteten, når de får adgang til følsomme finansielle data og programmer. Azure MFA kræver mindst to former for godkendelse, f.eks en adgangskode plus en kendt mobilenhed. Det understøtter flere muligheder for anden faktor-godkendelse, herunder:

- Den Microsoft Authenticator app
- En engangs adgangskode leveret via sms
- Et telefonopkald, hvor en bruger skal angive en pinkode

Hvis adgangskoden på en eller anden måde er kompromitteret, vil en potentiel hacker stadig have brug for brugerens telefon for at få adgang til organisationsdata. Desuden bruger Microsoft 365 moderne godkendelse som en nøgleprotokol, hvilket giver den samme stærke og omfattende godkendelsesoplevelse fra webbrowsere til de samarbejdsværktøjer, som medarbejderne bruger til dagligt, herunder Microsoft Outlook og de andre Microsoft Office-programmer.

#### <a name="passwordless"></a>Adgangskodefri

Adgangskoder er det svage led i en sikkerhedskæde. De kan være et enkelt fejlpunkt, hvis der ikke er nogen yderligere bekræftelse. Microsoft understøtter en bred vifte af godkendelsesmuligheder, der passer til de finansielle institutioners behov.

*Metoder uden adgangskoder* er med til at gøre MFA mere praktisk for brugerne. Selvom ikke alle multifaktorgodkendelser er adgangskodefri, anvender adgangskodefri teknologier multifaktorgodkendelse. Microsoft, Google og andre brancheledere har udviklet standarder for at give en enklere, stærkere godkendelsesoplevelse på tværs af internettet og mobilenheder i en gruppe kaldet Fast IDentity Online (FIDO). Den nyligt udviklet FIDO2-standard gør det muligt for brugerne at godkende nemt og sikkert uden brug af en adgangskode for at eliminere phishing.

Microsoft MFA-metoder uden adgangskoder omfatter:
* [Microsoft Authenticator](/azure/active-directory/user-help/user-help-auth-app-overview): For fleksibilitet, brugervenlighed og omkostninger anbefaler vi, at du bruger Microsoft Authenticator-mobilappen. Microsoft Authenticator understøtter biometriske værdier, pushmeddelelser og engangskoder til alle Azure AD-forbundne apps. Den er tilgængelig i Apple- og Android-app stores.
*  [Windows Hello](/windows/security/identity-protection/hello-for-business/hello-overview): For at få en indbygget oplevelse på pc'en anbefaler vi, at du bruger Windows Hello. Den anvender biometriske oplysninger (f.eks. ansigts- eller fingeraftryk) til at logge på automatisk.  
* [FIDO2-sikkerhedsnøgler](/windows/security/identity-protection/hello-for-business/microsoft-compatible-security-key) er nu tilgængelige fra flere Microsoft-partnere: Yubico, Feitian Technologies og HID Global i en USB-, NFC-aktiveret badge eller biometrisk nøgle.

[Betinget adgang til Azure AD](/azure/active-directory/conditional-access/) giver en robust løsning til automatisering af beslutninger om adgangskontrol og gennemtvingelse af organisationspolitikker for at beskytte virksomhedens aktiver. Et klassisk eksempel er, når en finansiel planlægger ønsker at få adgang til et program, der har følsomme kundedata. De er automatisk nødvendige for at udføre multifaktorgodkendelse for specifikt at få adgang til det pågældende program, og adgangen skal være fra en virksomhedsstyret enhed. Azure Betinget adgang samler signaler om en brugers anmodning om adgang, f.eks. egenskaber om brugeren, enheden, placeringen og netværket, og det program, brugeren forsøger at få adgang til. Det evaluerer dynamisk forsøg på at få adgang til programmet mod konfigurerede politikker. Hvis risikoen for brugere eller enheder er hævet, eller andre betingelser ikke er opfyldt, kan Azure AD automatisk gennemtvinge politikker, f.eks. krav om MFA, krav om sikker nulstilling af adgangskode eller begrænsning eller blokering af adgang. Dette er med til at sikre, at følsomme virksomhedsaktiver beskyttes i miljøer, der ændres dynamisk.
 
Azure AD og de relaterede Microsoft 365-sikkerhedstjenester udgør det grundlag, hvorpå en moderne skybaseret samarbejdsplatform kan udrulles til finansielle institutioner, så adgang til data og programmer kan sikres, og overholdelsesforpligtelser for kontrolfunktioner kan overholdes. Disse værktøjer giver følgende vigtige funktioner:

* Gem og administrer brugeridentiteter centralt og sikkert.
* Brug en stærk godkendelsesprotokol, herunder multifaktorgodkendelse, til at godkende brugere på adgangsanmodninger, og giv en ensartet og robust godkendelsesoplevelse på tværs af alle programmer.
* Valider dynamisk politikker på alle anmodninger om adgang, inkorporering af flere signaler i politikkens beslutningsproces, herunder identitet, bruger-/gruppemedlemskab, program, enhed, netværk, placering og risikoscore i realtid.
* Valider detaljerede politikker baseret på brugerfunktionsmåden og filegenskaberne, og gennemtving dynamisk yderligere sikkerhedsforanstaltninger, når det er nødvendigt.
* Identificer "skygge IT" i organisationen, og tillad InfoSec-teams at pålægge eller blokere programmer i skyen.
* Overvåg og kontroller adgang til Microsoft- og ikke-Microsoft-skyprogrammer.
* Proaktivt beskyttes mod phishing- og ransomware-angreb via mail.

#### <a name="azure-ad-identity-protection"></a>Azure AD Identity Protection
Mens Betinget adgang beskytter ressourcer fra mistænkelige anmodninger, går Identitetsbeskyttelse videre ved at levere løbende risikoregistrering og afhjælpning af mistænkelige brugerkonti. Identitetsbeskyttelse holder dig informeret om mistænkelig bruger og logon-adfærd i dit miljø døgnet rundt. Dens automatiske svar forhindrer proaktivt kompromitterede identiteter i at blive misbrugt.
 
Identitetsbeskyttelse er et værktøj, der gør det muligt for organisationer at udføre tre vigtige opgaver:

* Automatiser registrering og afhjælpning af identitetsbaserede risici.
* Undersøg risici ved hjælp af data i portalen.
* Eksportér data fra risikoregistrering til tredjepartsprogrammer til yderligere analyse.

Identity Protection bruger viden, som Microsoft har erhvervet fra sin position i organisationer med Azure AD, på forbrugerpladsen med Microsoft-konti og i spil med Xbox til at beskytte dine brugere. Microsoft analyserer 65 trillion signaler pr. dag for at identificere og beskytte kunder mod trusler. De signaler, der genereres af og videre føres til identitetsbeskyttelse, kan bruges i værktøjer som f.eks. Betinget adgang til at træffe beslutninger om adgang. De kan også få adgang til et værktøj til sikkerhedsoplysninger og begivenhedsstyring (SIEM), som kan bruges til yderligere undersøgelse baseret på organisationens tvungne politikker.

Identitetsbeskyttelse hjælper organisationer med automatisk at beskytte mod identitetsforlig ved at drage fordel af skyintelligens, der bygger på avanceret registrering baseret på heuristics, bruger- og enhedsadfærdsanalyser (UEBA) og maskinlæring (ML) på tværs af Microsofts økosystem.

![Fem informationsmedarbejdere ser på en anden og holder en præsentation.](../media/win17-15021-00-n9.jpg)
 
## <a name="identify-sensitive-data-and-prevent-data-loss"></a>Identificer følsomme data, og undgå tab af data
Microsoft 365 gør det muligt for alle organisationer at identificere følsomme data i organisationen ved hjælp af en kombination af effektive funktioner, herunder:

* **Microsoft Information Protection (MIP)** til både brugerbaseret klassificering og automatisk klassificering af følsomme data.
* Office 365 forebyggelse af datatab **(DLP)** til automatisk identifikation af følsomme data ved hjælp af følsomme datatyper (med andre ord regulære udtryk) og nøgleord og håndhævelse af politikken.

**[Microsoft Information Protection (MIP) giver organisationer](../compliance/information-protection.md)** mulighed for at klassificere dokumenter og mails intelligent ved hjælp af følsomhedsmærkater. Følsomhedsmærkater kan anvendes manuelt af brugerne på dokumenter i Microsoft Office og i mails i Outlook. Etiketterne kan automatisk anvende dokumentmærkning, beskyttelse via kryptering og håndhævelse af rettighedsstyring. Følsomhedsmærkater kan også anvendes automatisk ved at konfigurere politikker, der bruger nøgleord og følsomme datatyper (f.eks kreditkortnumre, socialforsikringsnumre og identitetsnumre) til automatisk at finde og klassificere følsomme data.

Desuden leverer Microsoft "trænbare klassificeringer", der bruger maskinlæringsmodeller til at identificere følsomme data baseret på indholdet, i modsætning til blot via mønstersammenholdelse eller af elementerne i indholdet. En klassificering lærer, hvordan du identificerer en type indhold ved at se på mange eksempler på det indhold, der skal klassificeres. Uddannelse af en klassificering starter med at give den eksempler på indhold i en bestemt kategori. Når den har lært af disse eksempler, testes modellen ved at give den en blanding af matchende og ikke-matchende eksempler. Klassificeringen forudsiger, om et givet eksempel falder inden for kategorien eller ej. En person bekræfter derefter resultaterne, sorterer positive, negativer, falske positive og falske negativer for at øge nøjagtigheden af klassificeringens forudsigelser. Når den uddannede klassificering udgives, behandler den indhold i Microsoft Office SharePoint Online, Exchange Online og OneDrive for Business og klassificerer automatisk indholdet.

Anvendelse af følsomhedsetiketter på dokumenter og mails integrerer metadata, der identificerer den valgte følsomhed i objektet. Følsomheden bevæger sig derefter med dataene. Så selvom et mærket dokument er gemt på en brugers skrivebord eller i et lokalt system, er det stadig beskyttet. Denne funktionalitet gør det muligt for Microsoft 365-løsninger, f.eks. Microsoft Defender til skyapps eller grænseenheder, til at identificere følsomme data og automatisk gennemtvinge sikkerhedskontrolelementer. Følsomhedsmærkater har den ekstra fordel ved at informere medarbejdere om, hvilke data i en organisation der betragtes som følsomme, og hvordan disse data håndteres, når de modtager dem.

Office 365 forebyggelse af datatab **[(DLP)](../compliance/dlp-learn-about-dlp.md)** identificerer automatisk dokumenter, mails og samtaler, der indeholder følsomme data, ved at scanne dem for følsomme data og derefter gennemtvinge en politik for disse objekter. Politikker håndhæves for dokumenter i SharePoint og OneDrive for Business. De gennemtvinges også, når brugere sender mails, og i Teams og kanalsamtaler. Politikker kan konfigureres til at søge efter nøgleord, følsomme datatyper, opbevaringsnavne, og om data deles i organisationen eller eksternt. Der findes kontrolelementer, der kan hjælpe organisationer med at finjustere DLP-politikker for at reducere falske positive. Når der findes følsomme data, kan politiktips, der kan tilpasses, vises til brugere i Microsoft 365-programmer for at informere dem om, at deres indhold indeholder følsomme data, og derefter foreslå afhjælpende handlinger. Politikker kan også forhindre brugere i at få adgang til dokumenter, dele dokumenter eller sende mails, der indeholder bestemte typer af følsomme data. Microsoft 365 understøtter mere end 100 indbyggede følsomme datatyper. Organisationer kan konfigurere brugerdefinerede følsomme datatyper, så de opfylder deres politikker.

Udrulning af MIP- og DLP-politikker til organisationer kræver nøje planlægning og et brugerundervisningsprogram, så medarbejderne forstår organisationens dataklassificeringsskema, og hvilke typer data der betragtes som følsomme. At give medarbejderne værktøjer og uddannelsesprogrammer, der hjælper dem med at identificere følsomme data og forstå, hvordan de skal håndtere dem, gør dem til en del af løsningen til at mindske informationssikkerhedsrisici.

De signaler, der genereres af og videre føres til identitetsbeskyttelse, kan også bruges til værktøjer som Betinget adgang til at træffe beslutninger om adgang eller til et værktøj til sikkerhedsoplysninger og begivenhedsstyring (SIEM) til undersøgelse baseret på en organisations tvungne politikker.

Identitetsbeskyttelse hjælper organisationer automatisk med at beskytte mod identitetsoverfald ved at drage fordel af skyintelligens, der bygger på avancerede registreringer, der er baseret på heuristics, bruger- og enhedsadfærdsanalyser og maskinlæring på tværs af Microsofts økosystem.

![En informationsmedarbejder vises foran et stort udvalg af skærme.](../media/clo1718-portrait-006.jpg)

## <a name="defend-the-fortress"></a>Forsvar den besfæst

Microsoft har for nylig lanceret Microsoft 365 Defender, som er udviklet med henblik på at sikre den moderne organisation mod det voksende trusselsbillede. Ved at udnytte Intelligent Security Graph, giver Threat Protection-løsningen en omfattende, integreret sikkerhed mod flere angrebsvektorer.

### <a name="the-intelligent-security-graph"></a>[Intelligent security-Graph](https://www.microsoft.com/security/business/intelligence) 
Sikkerhedstjenester fra Microsoft 365 leveres af Intelligent Security Graph. For at bekæmpe cybertrusler bruger den intelligente sikkerhedsekspert Graph avanceret analyse til at sammenkæde trusselsintelligens og sikkerhedssignaler fra Microsoft og Microsofts partnere. Microsoft driver globale tjenester i stort omfang og samler trillationer af sikkerhedssignaler, der beskytter strømstyring på tværs af stakken. Modeller for maskinel indlæring vurderer denne intelligens, og signal- og trusselsindsigt deles i stor grad på tværs af vores produkter og tjenester. Det gør det muligt for os hurtigt at registrere og reagere på trusler og give kunderne besked og oplysninger, der kan handles på, for at afhjælpe problemet. Vores modeller til maskinel indlæring er løbende uddannet og opdateret med ny viden, hvilket hjælper os med at udvikle mere sikre produkter og yde mere proaktiv sikkerhed.

[Microsoft Defender for Office 365 indeholder](../security/office-365-security/defender-for-office-365.md) en integreret Microsoft 365-tjeneste, der beskytter organisationer mod skadelige links og malware, som leveres via mail og Office dokumenter. En af de mest almindelige angrebsvektorer, der påvirker brugere i dag, er phishing-e-mail-angreb. Disse angreb kan målrettes bestemte brugere og kan være meget overbevisende med en opfordring til handling, der beder brugeren om at klikke på et skadeligt link eller åbne en vedhæftet fil, der indeholder malware. Når en computer er inficeret, kan hackeren enten stjæle brugerens legitimationsoplysninger og bevæge sig senere rundt i organisationen eller eksfiltrere mails og data for at søge efter følsomme oplysninger. Defender for Office 365 understøtter sikre vedhæftede filer og sikre links ved at evaluere dokumenter og links på klik-tid for potentielt ondsindede hensigter og blokerer adgang. Vedhæftede filer åbnes i en beskyttet sandkasse, før de leveres til en brugers postkasse. Det evaluerer også links i Office for skadelige URL-adresser. Defender til Office 365 beskytter også links og filer i SharePoint Online, OneDrive for Business og Teams. Hvis der registreres en skadelig fil, låser Defender Office 365 automatisk denne fil for at reducere den potentielle skade.

[Microsoft Defender til slutpunkt er](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) en samlet slutpunktssikkerhedsplatform til forebyggelse af beskyttelse, registrering efter brud og automatisk undersøgelse og svar. Defender til Slutpunkt giver indbyggede funktioner til registrering og beskyttelse af følsomme data på virksomhedens slutpunkter.

[Microsoft Defender til skyapps](/cloud-app-security/what-is-cloud-app-security) gør det muligt for organisationer at håndhæve politikker på et granularniveau og registrere funktionsmådeanomer baseret på individuelle brugerprofiler, der er defineret automatisk ved hjælp af maskinel indlæring. Politikker for Defender til skyapps kan bygge på Azure Conditional Access-politikker for at beskytte følsomme virksomhedsaktiver ved at evaluere yderligere signaler relateret til brugeradfærd og egenskaber for de dokumenter, der tilgås. Med tiden lærer Defender til skyapps den typiske adfærd for hver medarbejder med hensyn til de data, de får adgang til, og de programmer, de bruger. Baseret på lærde adfærdsmønstre kan politikker derefter automatisk gennemtvinge sikkerhedskontrolelementer, hvis en medarbejder handler uden for den pågældende funktionsmådeprofil. Hvis en medarbejder typisk åbner et regnskabsprogram fra kl. 9 til 17 mandag til fredag, men pludselig begynder at få adgang til det pågældende program meget på en søndag aften, kan Defender til skyapps dynamisk gennemtvinge politikker, der kræver, at brugeren skal læse det igen. Dette er med til at sikre, at brugerens legitimationsoplysninger ikke er blevet kompromitteret. Defender til skyapps kan også hjælpe med at identificere "skygge IT" i organisationen, hvilket hjælper informationssikkerhedsteams med at sikre, at medarbejderne bruger værktøjer, der er blevet godkendt, når de arbejder med følsomme data. Endelig kan Defender til skyapps beskytte følsomme data hvor som helst i skyen, selv uden for Microsoft 365 platform. Det giver organisationer mulighed for at pålægge (eller ophæve forbud) bestemte eksterne skyapps, kontrollere adgang og overvåge brugen.
 
[Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp) er en skybaseret sikkerhedsløsning, der udnytter dine lokale Active Directory-signaler til at identificere, registrere og undersøge avancerede trusler, kompromitterede identiteter og skadelige Insider-handlinger rettet mod din organisation. AATP gør det muligt for SecOp-analytikere og sikkerhedsmedarbejdere at registrere avancerede angreb i hybridmiljøer for at:
* Overvåg brugere, enhedsfunktionsmåde og aktiviteter ved hjælp af læringsbaseret analyse.
* Beskyt brugeridentiteter og legitimationsoplysninger, der er gemt i Active Directory.
* Identificer og undersøg mistænkelige brugeraktiviteter og avancerede angreb i hele kill-kæden.
* Giv klare oplysninger om hændelsen på en simpel tidslinje, så du hurtigt kan finde oplysninger.

![Kontormedarbejderne mødes i et lille mødelokale. Et giver en præsentation.](../media/clo1717-corporate-office-021.jpg)
 
## <a name="govern-data-and-manage-records"></a>Styre data og administrere poster

Finansielle institutioner skal opbevare deres data og oplysninger i henhold til deres lovgivningsmæssige, juridiske og forretningsmæssige forpligtelser, som de er repræsenteret i deres virksomheds opbevaringstidsplan. SEC-fuldmagter for [eksempel](https://www.sec.gov/rules/interp/34-47806.htm) opbevaringsperioder på tre til seks år baseret på datatype med øjeblikkelig tilgængelighed for de første to år. Organisationer risikerer juridisk og lovgivningsmæssig overholdelse, hvis data bevares under (kasseres for tidligt), og administrerer nu også bestemmelser, som kan bruges til at afhændelse af ressourcer, når der ikke længere er brug for oplysninger. Effektive strategier til datastyring fremhæver en praktisk og ensartet tilgang, så oplysningerne afhændes korrekt, mens omkostninger og risiko minimeres for organisationen.
 
Desuden kræver lovgivningsmæssige fuldmagter fra New York State Department of Financial Services omfattede enheder for at vedligeholde politikker og procedurer for afhændelse af ikke-publicerede oplysninger. 23 NYCRR 500, sektion 500.13, Begrænsninger for dataopbevaring kræver, at "Som en del af dens cybersecurity-program, skal hver dækket enhed indeholde politikker og procedurer til sikker afhændelse med jævne mellemrum fra alle ikke-publicske oplysninger, der er identificeret i afsnit 500.01(g)(2)-(3) i denne del, der ikke længere er nødvendige for forretningshandlinger eller for andre legitime forretningsformål i den omfattede enhed,  undtagen hvis sådanne oplysninger på anden måde er påkrævet for at blive bevaret ved lov eller bestemmelser."
 
De finansielle institutioner administrerer enorme mængder data. Og nogle opbevaringsperioder udløses af hændelser, f.eks. at en kontrakt udløber eller at en medarbejder forlader organisationen. I dette område kan det være en udfordring at anvende opbevaringspolitikker for poster. Metoder til tildeling af postopbevaringsperioder præcist på tværs af organisatoriske dokumenter kan variere. Nogle anvender opbevaringspolitikker bredt eller udnytter automatisk klassificering og maskinlæringsteknikker. Andre identificerer en fremgangsmåde, der kræver en mere detaljeret proces, der tildeler opbevaringsperioder entydigt til individuelle dokumenter.

***Microsoft 365 giver fleksible funktioner til at definere opbevaringsmærkater og politikker, så datastyringskrav implementeres intelligent.*** En poststyring definerer et opbevaringsnavn, der repræsenterer en "posttype" i en traditionel opbevaringstidsplan. Opbevaringsetiketten indeholder indstillinger, der definerer disse detaljer:

- Hvor lang tid en post bevares
- Hvad sker der, når en opbevaringsperiode udløber (slette dokumentet, starte en gennemgang af en disposition eller ikke gøre noget)
-  Hvad udløser opbevaringsperioden til at starte (oprettet dato, dato for seneste ændring, mærket dato eller en begivenhed) og markerer dokumentet eller mailen som en post (hvilket betyder, at den ikke kan redigeres eller slettes)

Opbevaringsnavnene publiceres derefter på SharePoint eller OneDrive websteder, Exchange postkasser og Microsoft 365 grupper. Brugere kan anvende opbevaringsmærkaterne manuelt på dokumenter og mails. Postadministratorer kan anvende intelligens til automatisk at anvende etiketterne. Intelligente funktioner kan være baseret på [indbyggede](../compliance/content-search.md) følsomme oplysningstyper (f.eks. ABA-outingnummer, amerikanske bankkontonummer eller amerikanske CPR-nummer). De kan også tilpasses baseret på nøgleord eller følsomme data, der findes i dokumenter eller mails, f.eks kreditkortnumre eller andre personligt identificerbare oplysninger eller baseret på SharePoint metadata. For data, der ikke er let identificeret ved hjælp af manuel eller automatiseret matchning, kan klassificerede klassificeringer, der kan bruges til intelligente klassificere dokumenter baseret på maskinlæringsteknikker.
 
**Securities and Exchange Commission (SEC)** kræver, at formidlere- og andre regulerede finansielle institutioner beholder al forretningsrelateret kommunikation. Disse krav gælder for mange typer kommunikation og data, herunder mails, dokumenter, chatbeskeder, faxer og meget mere. **SEC-regel 17a-4** definerer de kriterier, som disse organisationer skal opfylde for at lagre poster i et elektronisk datalagringssystem. I 2003 udsendte SEC en udgivelse, der oplyser om disse krav. Det indeholdt følgende kriterier:

* Data, der bevares af et elektronisk lagringssystem, skal ikke kunne omskrives og kan ikke slettes. Dette kaldes et ORME-krav (skriv én gang, læs mange).
* Lagringssystemet skal kunne gemme data ud over den opbevaringsperiode, der kræves af reglen, i tilfælde af en stævning eller en anden juridisk rækkefølge.
* En organisation overtræder ikke kravet i reglens afsnit (f)(2)(ii)(A), hvis den anvender et elektronisk lagringssystem, der forhindrer overskrivning, sletning eller på anden måde ændring af en post i den nødvendige opbevaringsperiode gennem brug af integrerede hardware- og softwarekontrolkoder.
* Elektroniske lagringssystemer, der blot "mindsker" risikoen for, at en post overskrives eller bliver slettet, f.eks. ved at stole på adgangskontrol, opfylder ikke reglens krav.

For at hjælpe de finansielle institutioner med at opfylde kravene i SEC-regel 17a-4 indeholder Microsoft 365 en kombination af funktioner relateret til, hvordan data bevares, politikker konfigureres, og data gemmes i tjenesten. Disse omfatter:

* **Opbevaring af data (regel 17a-4(a), (b)(4))** – Opbevaringsmærkater og -politikker er fleksible, så de opfylder organisatoriske behov og kan anvendes automatisk eller manuelt på forskellige typer data, dokumenter og oplysninger. En lang række datatyper og kommunikation understøttes, herunder dokumenter i SharePoint og OneDrive for Business, data i Exchange Online-postkasser og data i Teams.  
* Format, der ikke kan omskrives, kan ikke slettes **(regel 17a-4(f)(2)(ii)(A))** – Bevaringslåsning for opbevaringspolitikker gør det muligt for dataledere og administratorer at konfigurere opbevaringspolitikker, så de ikke længere kan ændres. Dette forhindrer andre i at fjerne, deaktivere eller ændre opbevaringspolitikken på nogen måde. Det betyder, at når Bevarelseslås er aktiveret, kan den ikke deaktiveres, og der er ingen metode til, at data, som opbevaringspolitikken er blevet anvendt på, kan overskrives, ændres eller slettes under opbevaringsperioden. Opbevaringsperioden kan desuden ikke forkortes. Opbevaringsperioden kan dog forlænges, når der er et juridisk krav om at fortsætte opbevaring af data.<br/><br/>Når en opbevaringslås anvendes på en opbevaringspolitik, begrænses følgende handlinger:

  - Opbevaringsperioden for politikken kan kun øges. Det kan ikke forkortes.
  - Brugere kan føjes til politikken, men eksisterende brugere, der er konfigureret i politikken, kan ikke fjernes.
   - Opbevaringspolitikken kan ikke slettes af nogen administrator i organisationen.
 
  Bevarelseslås hjælper med at sikre, at ingen bruger, ikke selv administratorer med de højeste adgangsniveauer, kan ændre indstillingerne, ændre, overskrive eller slette de data, der er blevet gemt, hvilket bringer arkivering i Office 365 i overensstemmelse med vejledningen i SEC 2003 Release.

* Kvalitet, nøjagtighed og bekræftelse af lagring/serialisering og indeksering af **data (regel 17a-4(f)(2) (ii)(B) og (C))** – Office 365-arbejdsbelastninger indeholder hver funktioner, som automatisk kontrollerer kvaliteten og nøjagtigheden af processen for optagelse af data på lagringsmedier. Desuden gemmes data ved at benytte metadata og tidsstempler for at sikre tilstrækkelig indeksering til effektiv søgning og hentning af data.
 
* Separat lager til dublerede kopier **(regel 17a-4(f)(3(iii))** – Office 365-skytjenesten gemmer duplikerede kopier af data som et centralt aspekt af dens høje tilgængelighed. Dette opnås ved at implementere redundans på alle niveauer i tjenesten, herunder på det fysiske niveau på alle servere, på serverniveau i datacenteret og på tjenesteniveau for geografisk spredte datacentre.

* Data, der kan downloades og gøres tilgængelige **(regel 17a-4(f)(2)(ii)(D))** – Office 365 tillader generelt, at data, der er mærket opbevaring, kan søges efter, åbnes og downloades på plads. Og det gør det muligt at Exchange Online data i arkiver, der kan søges i, ved hjælp af indbyggede eDiscovery-funktioner. Data kan derefter downloades efter behov i standardformater, herunder EDRML og PST.
 
* Overvågningskrav **(regel 17a-4(f)(3)(v))** – Office 365 indeholder overvågningslogføring for hver administrative handling og brugerhandling, der ændrer dataobjekter, konfigurerer eller ændrer opbevaringspolitikker, udfører eDiscovery-søgninger eller ændrer adgangstilladelser. Office 365 fører en omfattende overvågningslog, herunder data om, hvem der udførte en handling, da den blev udført, detaljer om handlingen og de kommandoer, der blev udført. Overvågningsloggen kan derefter output og medtages som en del af de formelle overvågningsprocesser efter behov.

Endelig kræver regel 17a-4, at organisationer bevarer poster for mange typer transaktioner, så de er umiddelbart tilgængelige i to år. Data skal bevares yderligere i tre til seks år med ikke-øjeblikkelig adgang. Dublerede poster skal også gemmes i samme periode på en placering uden for webstedet. Office 365 datastyring gør det muligt at bevare dataposter, så de ikke kan ændres eller slettes, men nemt kan tilgås i en tidsperiode, der styres af poststyringen. Disse perioder kan strække sig over dage, måneder eller år, afhængigt af organisationens lovmæssige overholdelsesforpligtelser.
 
Efter anmodning leverer Microsoft et bekræftelsesbrev om overholdelse af SEC 17a-4, hvis det kræves af en organisation.

Disse funktioner hjælper desuden Microsoft 365 med at opfylde lagerkravene for [CFTC-regel 1.31(c)-(d)](https://www.cftc.gov/sites/default/files/opa/press99/opa4266-99-attch.htm) fra DEN amerikanske handelsdag (**Tradey Futures Trade Commission**) og [FINRA Rule Series 4510](https://www.finra.org/rules-guidance/rulebooks/finra-rules/4511) fra den finansielle branche **.** Samlet repræsenterer disse regler den mest præskripive vejledning globalt for finansielle institutioner til at opbevare poster.

Yderligere oplysninger om, hvordan Microsoft 365 overholder SEC-reglen 17a-4, og andre bestemmelser findes under [Vurdering af Office 365 Exchange Online SEC 17a-4(f) / CFTC 1.31(c)-(d) af Cohasset Associates](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=9fa8349d-a0c9-47d9-93ad-472aa0fa44ec&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers).

## <a name="establish-ethical-walls-with-information-barriers"></a>Opret etiske vægge med informationsbarrierer

Finansielle institutioner kan være underlagt bestemmelser, der forhindrer medarbejdere i bestemte roller i at udveksle oplysninger eller samarbejde med andre roller. FINRA har f.eks. offentliggjort regler 2241(b)(2)(G), 2242(b)(2) (D), (b)(2)(H)(ii) og (b)(2)(H)(iii), der kræver, at medlemmer:

"(G) etablere informationsbarrierer eller andre sikkerhedsforanstaltninger i den pågældende institution med rimelighed for at sikre, at forskningsanalytikere fjernes fra gennemgangen, trykket eller oversigten af personer, der er involveret i bankforretningsaktiviteter eller andre personer, herunder salgs- og handelsmedarbejdere, som kan være involveret i deres vurdering eller overvågning", og "(H) etablere informationsbarrierer eller andre sikkerhedsforanstaltninger i med rimelighed for at sikre, at gældsundersøgelsesanalytikere påvirkes af  gennemgang, pression eller overvågning af personer, der er involveret i: (i) investeringsbanktjenester; (ii) hovedsalgs- eller salgs- og handelsaktiviteter; og (iii) andre personer, der kan være din egen vurdering eller overvågning;"

I sidste ende kræver disse regler, at organisationer etablerer politikker og implementerer informationsbarrierer mellem roller, der er involveret i banktjenester, salg eller handel fra at udveksle oplysninger og kommunikation med analytikere.

[Informationsbarrierer](../compliance/information-barriers.md) giver mulighed for at etablere etiske vægge i dit Office 365-miljø, så overholdelsesadministratorer eller andre autoriserede administratorer kan definere politikker, der tillader eller forhindrer kommunikation mellem grupper af brugere i Teams. Informationsbarrierer kontrollerer bestemte handlinger for at forhindre uautoriseret kommunikation. Informationsbarrierer kan også begrænse kommunikationen i scenarier, hvor interne teams arbejder på fusioner/overtagelser eller følsomme handler eller arbejder med følsomme interne oplysninger, der skal begrænses meget.

Informationsbarrierer i Microsoft 365 understøtter samtaler og filer i Teams. De kan forhindre følgende typer af kommunikationsrelaterede handlinger for at overholde FINRA-bestemmelser:

* Søg efter en bruger
* Føj et medlem til et team, eller fortsæt med at deltage med et andet medlem i et team
* Start eller fortsæt en chatsession
* Start eller fortsæt en gruppechat
* Inviter en person til at deltage i et møde
* Del en skærm
* Af sted et opkald

## <a name="implement-supervisory-control"></a>Implementere kontrol

Finansielle institutioner er typisk nødvendige for at etablere og opretholde en kontrolfunktion i deres organisationer for at overvåge medarbejdernes aktiviteter og for at hjælpe dem med at opnå overholdelse af gældende lovgivning om værdipapirer. Finra har specifikt fastlagt disse overvågningskrav:
 
* [FINRA-regel 3110 (Overvågning)](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3110) kræver, at virksomheder har skriftlige kontrolprocedurer for at overvåge medarbejdernes aktiviteter og den type virksomheder, de er involveret i. Ud over andre krav skal procedurerne omfatte:
   - Overvågning af kontrolmedarbejdere
   - Gennemgang af en virksomheds investeringsbank, værdipapirvirksomhed, intern kommunikation og interne undersøgelser
   - Gennemgang af transaktioner for insider-handel
   - Gennemgang af korrespondance og klager

   Procedurerne skal beskrive de personer, der er ansvarlige for anmeldelser, kontrolaktivitet hver person vil udføre, gennemgå hyppigheden og de typer dokumentation eller kommunikation, der skal gennemgås.
 
* [FINRA-regel 3120 (](https://www.finra.org/rules-guidance/rulebooks/finra-rules/3120) kontrolkontrolsystem) kræver, at virksomheder har et system med politikker og procedurer for kontrol, der validerer deres skriftlige kontrolprocedurer som defineret i regel 3110. Virksomheder skal ikke blot have WSP'er, men også have politikker, der tester disse procedurer årligt for at validere deres evne til at sikre overholdelse af gældende love og bestemmelser om værdipapirer. Der kan benyttes risikobaserede metoder og stikprøver til at definere omfanget af test. Denne regel kræver blandt andet, at virksomhedsselskaber skal udarbejde en årlig rapport til seniorledelsen, som indeholder en oversigt over testresultater og væsentlige undtagelser eller procedurer for vilkårlige undtagelser som svar på testresultater.

![En kontormedarbejder får et diagram og tabeller på en skærm, mens andre mødes i baggrunden.](../media/wco18-desk-work-002.jpg)
 
### <a name="communication-compliance"></a>Kommunikationsoverholdelse

Kommunikationsoverholdelse i Microsoft 365 gør det muligt for organisationer at konfigurere politikker på forhånd til at registrere medarbejderkommunikation til overvågning og gennemgang af autoriserede tilsynsførende. Politikker for overholdelse af kommunikation kan registrere interne/eksterne mails og vedhæftede filer, Teams chat og kanalkommunikation og Skype for Business onlinechatkommunikation og vedhæftede filer. Desuden kan overholdelse af kommunikation indtrænge kommunikation og data fra tredjepartstjenester (f.eks. Bloomberg, T pvson Reuters, LinkedIn, Twitter, Facebook, Box og Dropbox).
Den omfattende karakter af kommunikation, der kan registreres og gennemgås i en organisation, og de omfattende betingelser, som politikker kan konfigureres for, gør det muligt at overholde politikker for overholdelse af kommunikation for at hjælpe de finansielle institutioner med at overholde FINRA-regel 3110. Politikker kan konfigureres til at gennemse kommunikation for enkeltpersoner eller grupper.  Udpegede tilsynsførende kan tildeles på et individuelt niveau eller i en gruppe. Omfattende betingelser kan konfigureres til at registrere kommunikation baseret på indgående eller udgående meddelelser, domæner, opbevaringsetiketter, nøgleord eller udtryk, ordbøger til nøgleord, følsomme datatyper, vedhæftede filer, meddelelsens størrelse eller størrelsen på vedhæftede filer. Korrekturlæsere får et dashboard, hvor de kan gennemse markeret kommunikation, handle på kommunikation, der potentielt overtræder politikker, og markere markerede elementer som løst. De kan også gennemse resultaterne af anmeldelser og elementer, der tidligere er blevet løst.
  
Kommunikationsoverholdelse indeholder rapporter, der gør det muligt at overvåge politikgennemgangsaktiviteter baseret på politikken og korrekturlæseren. Rapporter kan bruges til at validere, at politikker fungerer som defineret af en organisations skrevne overvågningspolitikker. De kan også bruges til at identificere kommunikation, der kræver gennemsyn, og meddelelser, der ikke er i overensstemmelse med virksomhedens politik. Endelig overvåges alle aktiviteter i forbindelse med konfiguration af politikker og gennemgang af kommunikation i Office 365 samlet overvågningslog. Derfor hjælper overholdelse af kommunikation i Microsoft 365 også de finansielle institutioner med at overholde FINRA-regel 3120.

Ud over at overholde FINRA-regler giver kommunikationsoverholdelse organisationer mulighed for at overvåge kommunikation for at overholde andre juridiske krav, virksomhedspolitikker og etiske standarder. Kommunikationsoverholdelse giver indbyggede trusler, chikane og bandeord, der er med til at reducere falske positive, når du gennemser kommunikation, hvilket sparer tid for korrekturlæsere under undersøgelsen og afhjælpningsprocessen. Det giver også organisationer mulighed for at reducere risikoen ved at overvåge kommunikationen, når de gennemgår følsomme ændringer, f.eks. fusioner og overtagelser eller ledelsesændringer.

![En informationsmedarbejder fokuserer på en skærm.](../media/msc16-slalom-004.jpg)
 
## <a name="protect-against-data-exfiltration-and-insider-risk"></a>Beskyt dig mod dataudfyldning og insider-risiko

En almindelig trussel mod virksomheder er dataudfyldning eller en handling, der udtrækker data fra en organisation. Denne risiko kan være et betydeligt problem for de finansielle institutioner på grund af de følsomme oplysninger, der kan tilgås fra dag til dag. Med det stigende antal tilgængelige kommunikationskanaler og spredningen af værktøjer til at flytte data er avancerede funktioner typisk nødvendige for at reducere risikoen for datalækager, politikbrud og insider-risici.

### <a name="insider-risk-management"></a>Insider-risikostyring

Aktivering af medarbejdere med værktøjer til onlinesamarbejde, der kan tilgås hvor som helst, er forbundet med risiko for organisationen. Medarbejdere kan utilsigtet eller ondsindet komme til at sive data ud til hackere eller konkurrenter.  Alternativt kan de eksfiltrere data til personlig brug eller føre data med dem til en fremtidig arbejdsgiver. Disse scenarier udgør alvorlige risici for den finansielle sektor fra både sikkerheds- og overholdelsespunkter. At identificere disse risici, når de opstår, og hurtigt mindske dem kræver både intelligente værktøjer til dataindsamling og samarbejde på tværs af afdelinger som f.eks juridiske ressourcer, HR-ressourcer og informationssikkerhed.

Microsoft 365 for nylig lanceret en insider-løsning til risikostyring, der korrelerer signaler på tværs af Microsoft 365-tjenester og bruger maskinlæringsmodeller til at analysere brugeradfærd for skjulte mønstre og tegn på insider-risici. Dette værktøj muliggør samarbejde mellem sikkerhedshandlinger, interne sikkerhedsfunktioner og HR, så de nemt kan afhjælpe sager baseret på foruddefinerede arbejdsprocesser.  

Insider Risk Management i Microsoft 365 kan f.eks korrelere signaler fra en brugers skrivebordsversion af Windows 10, f.eks. kopiere filer til et USB-drev eller sende en personlig mailkonto via mail med aktiviteter fra onlinetjenester som Office 365-mail, SharePoint Online, Microsoft Teams eller OneDrive for Business for at identificere dataudfyldningsmønstre. Det kan også korrelere disse aktiviteter med medarbejdere, der forlader en organisation, hvilket er et almindeligt mønster til dataudfyldning. Det kan overvåge flere aktiviteter og funktionsmåder over tid. Når der opstår almindelige mønstre, kan det skabe beskeder og hjælpe andre med at fokusere på nøgleaktiviteter for at bekræfte en overtrædelse af politikken med høj grad af tillid. Insider-risikostyring kan pseudo-anonymisere data fra skyer for at hjælpe med at overholde bestemmelser om beskyttelse af data og samtidig overse vigtige aktiviteter, der hjælper dem med at udføre undersøgelser effektivt. Det giver mulighed for at pakke og sikkert sende nøgleaktivitetsdata til HR og juridiske afdelinger, som følger almindelige eskaleringsarbejdsprocesser for at hæve sager for afhjælpningshandling.

Insider-risikostyring i Microsoft 365 øger organisationers evne til at overvåge og undersøge insider-risici markant, samtidig med at det giver organisationer mulighed for at overholde regler om beskyttelse af data og følge etablerede eskaleringsstier, når tilfælde kræver handling på højere niveau. Du kan finde flere oplysninger om insider-risikostyring i Microsoft 365 i Moderne punkter for [risikosmerter og Workflow i Insider-risikostyring Microsoft 365](../compliance/insider-risk-management.md).

![En opkaldscentermedarbejder i et kontormiljø, mens der vises en skærm.](../media/clo17-call-center-006.jpg)
 
### <a name="tenant-restrictions"></a>Lejerbegrænsninger
Organisationer, der håndterer følsomme data og lægger vægt på sikkerhed, ønsker typisk at kontrollere de onlineressourcer, som brugerne kan få adgang til. Samtidig ønsker de at aktivere sikkert samarbejde via onlinetjenester som f.eks. Office 365. Det betyder, at det kan være en udfordring at kontrollere de Office 365-miljøer, som brugerne kan få adgang til, fordi ikke-personlige Office 365-miljøer kan bruges til at eksfiltrere data fra virksomhedens enheder enten skadeligt eller utilsigtet. Organisationer begrænser traditionelt de domæner eller IP-adresser, som brugere kan få adgang til fra virksomhedens enheder. Men dette fungerer ikke i en skybaseret verden, hvor brugerne har brug for at få legitim adgang til Office 365 tjenester.

Microsoft 365 giver [lejerbegrænsningerne muligheden](/azure/active-directory/manage-apps/tenant-restrictions) for at håndtere denne udfordring. Lejerbegrænsninger kan konfigureres til at begrænse medarbejderadgang til eksterne Office 365 virksomhedslejere ved hjælp af identiteter (identiteter, der ikke er en del af virksomhedens adresseliste). I dag gælder lejerbegrænsninger for hele lejeren, så det kun er de lejere, der vises på den liste, du konfigurerer. Microsoft udvikler fortsat denne løsning for at øge granulariteten af kontrol og forbedre den beskyttelse, den giver.

![GRAFIK.](../media/clo1717-corporate-office-001.jpg)
 
## <a name="conclusion"></a>Konklusion

Microsoft 365 og Teams giver en integreret og omfattende løsning til virksomheder inden for den finansielle sektor, som muliggør enkle og effektive skybaserede samarbejds- og kommunikationsfunktioner i hele virksomheden. Ved at bruge sikkerheds- og overholdelsesteknologier fra Microsoft 365 kan institutioner fungere på en mere sikker og kompatibel måde med robuste sikkerhedskontroller for at beskytte data, identiteter, enheder og programmer mod forskellige driftsrisici, herunder cybersikkerhed og insider-risici. Microsoft 365 giver en fundamentalt sikker platform, hvor de finansielle tjenester kan opnå mere, og samtidig beskytte deres virksomhed, medarbejdere og kunder.
