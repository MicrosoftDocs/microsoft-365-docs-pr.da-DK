---
title: Få mere at vide om forebyggelse af datatab
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
description: Lær at beskytte dine følsomme oplysninger ved hjælp Microsoft 365 politikker og værktøjer til forebyggelse af datatab og få en rundvisning i DLP-livscyklussen.
ms.openlocfilehash: f64fa30ed0f2eddae03a14451c55f95c9e4249a3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63597916"
---
# <a name="learn-about-data-loss-prevention"></a>Få mere at vide om forebyggelse af datatab

Organisationer har følsomme oplysninger under deres kontrol, f.eks. finansielle data, beskyttede data, kreditkortnumre, sundhedsjournaler eller personnumre. For at beskytte disse følsomme data og reducere risikoen har de brug for en metode til at forhindre deres brugere i upassende at dele dem med personer, der ikke bør have dem. Denne fremgangsmåde kaldes forebyggelse af datatab (DLP).

I Microsoft 365 implementerer du forebyggelse af datatab ved at definere og anvende DLP-politikker. Med en DLP-politik kan du identificere, overvåge og automatisk beskytte følsomme elementer på tværs af:

- Microsoft 365 tjenester som Teams, Exchange, SharePoint og OneDrive
- Office programmer som Word, Excel og PowerPoint
- Windows 10-slutpunkter Windows 11 og macOS (Catalina 10.15 og nyere)
- ikke-Microsoft-skyapps
- lokale filshares og lokale SharePoint.

Microsoft 365 registrerer følsomme elementer ved hjælp af omfattende analyse af indholdet, ikke kun ved en enkel tekstscanning. Indhold analyseres for primære datamatches med nøgleord ved evaluering af regulære udtryk, af intern funktionsvalidering og af sekundære datamatches, der er i nærheden af den primære data match. Derudover bruger DLP også maskinlæringsalgoritmer og andre metoder til at registrere indhold, der svarer til dine DLP-politikker.

## <a name="dlp-is-part-of-the-larger-microsoft-365-compliance-offering"></a>DLP er en del af de større Microsoft 365 overholdelsestilbud

Microsoft 365 DLP er blot et af de Microsoft 365 Overholdelsesværktøjer, du vil bruge til at beskytte dine følsomme elementer, uanset hvor de bor eller rejser. Du bør forstå de andre værktøjer i Microsoft 365 overholdelsesværktøjerne, hvordan de indbyrdes forener og arbejder bedre sammen.  Se Værktøjer [til Microsoft 365 overholdelse af regler](protect-information.md) og standarder for at få mere at vide om processen til beskyttelse af oplysninger.

## <a name="protective-actions-of-dlp-policies"></a>Beskyttende handlinger for DLP-politikker

Microsoft 365 DLP-politikker bruges til at overvåge de aktiviteter, som brugere anvender på følsomme inaktivitetselementer, følsomme elementer under overførsel eller følsomme elementer, der er i brug, og udføre beskyttende handlinger. Når en bruger f.eks. forsøger at udføre en forbudt handling, f.eks. kopiere et følsomt element til en ikke-godkendt placering eller dele medicinske oplysninger i en mail eller andre betingelser, der er fastsat i en politik, kan DLP:

- vise et pop op-politiktip til brugeren, der advarer brugeren om, at vedkommende muligvis forsøger at dele et følsomt element upassende
- blokere delingen og via et politiktip tillade brugeren at tilsidesætte blokeringen og registrere brugerens begrundelse
- bloker delingen uden at tilsidesætte indstillingen
- For data, der er i rest, kan følsomme elementer låses og flyttes til en sikker karantæneplacering
- i Teams chat, vises de følsomme oplysninger ikke

Alle DLP-overvågede aktiviteter registreres som [Microsoft 365 overvågningsloggen](search-the-audit-log-in-security-and-compliance.md) og dirigeres til [Aktivitetsstifinder](data-classification-activity-explorer.md). Når en bruger udfører en handling, der opfylder kriterierne i en DLP-politik, og du har konfigureret påmindelser, leverer DLP beskeder i [dashboardet til administration af DLP-beskeder](dlp-configure-view-alerts-policies.md).

## <a name="dlp-lifecycle"></a>DLP-livscyklus

En DLP-implementering følger typisk disse store faser.

- [Plan for DLP](#plan-for-dlp)
- [Forbered dig på DLP](#prepare-for-dlp)
- [Installér dine politikker i produktion](#deploy-your-policies-in-production)


<!--ADD DIAGRAM OF THE DLP LIFECYCLE WORK ON WITH MAS-->

### <a name="plan-for-dlp"></a>Plan for DLP

Microsoft 365 DLP-overvågning og -beskyttelse er indbygget i de programmer, som brugerne bruger hver dag. Dette hjælper med at beskytte dine organisationers følsomme elementer mod risikabelt aktivitet, selvom dine brugere ikke er fortrolige med tanke på forebyggelse af datatab og fremgangsmåder. Hvis din organisation og dine brugere er nye brugere af fremgangsmåder til forebyggelse af datatab, kan indføring af DLP kræve en ændring af dine forretningsprocesser, og der vil være en kulturændring for dine brugere. Men med korrekt planlægning, test og justering beskytter dine DLP-politikker dine følsomme elementer, mens du minimerer potentielle afbrydelser af forretningsprocessen.

**Teknologiplanlægning for DLP**

Husk på, at DLP som teknologi kan overvåge og beskytte dine data i hvile, data i brug og data i bevægelse på tværs af Microsoft 365-tjenester, Windows 10-, Windows 11- og macOS-enheder (Catalina 10.15 og nyere), lokale filshares og lokale SharePoint. Der er planlægnings konsekvenser for de forskellige placeringer, den type data, du vil overvåge og beskytte, og de handlinger, der skal foretages, når der opstår et politik match.

**Planlægning af forretningsprocesser for DLP**

DLP-politikker kan blokere forbudte aktiviteter, f.eks. upassende deling af følsomme oplysninger via mail. Når du planlægger dine DLP-politikker, skal du identificere de forretningsprocesser, der rører ved dine følsomme elementer. Ejere af forretningsprocessen kan hjælpe dig med at identificere relevante brugeradfærd, der skal være tilladte og upassende brugeradfærd, der skal være beskyttet mod. Du skal planlægge dine politikker og implementere dem i testtilstand og evaluere deres virkning via [Aktivitetsstifinder](data-classification-activity-explorer.md) først, før du anvender dem i mere restriktive tilstande.

**Planlægning af organisationskultur for DLP**

En vellykket DLP-implementering er lige så afhængig af at få dine brugere oplært og tilgængelig som praksis til forebyggelse af datatab, som den er baseret på velorganiserede og afstemmede politikker. Da dine brugere er meget involveret, skal du sørge for også at planlægge kurser til dem. Du kan bruge politiktips strategisk til at skabe opmærksomhed hos dine brugere, før du ændrer håndhævelsen af politikken fra testtilstand til mere restriktive tilstande.

<!--For more information on planning for DLP, including suggestions for deployment based on your needs and resources, see [Planning for Microsoft 365 data loss prevention](dlp-plan-for-dlp.md).-->

### <a name="prepare-for-dlp"></a>Forbered dig på DLP

Du kan anvende DLP-politikker på in rest-data, data i brug og data i bevægelse i placeringer, f.eks.:

- Exchange Online mail
- SharePoint onlinewebsteder
- OneDrive konti
- Teams chat og kanalmeddelelser
- Microsoft Cloud App Security
- Windows 10, Windows 11 og macOS-enheder (Catalina 10.15 og nyere)
- Lokale lagre
- PowerBI-websteder

Hver enkelt har forskellige forudsætninger. Følsomme elementer på nogle steder, f.eks. Exchange online, kan tages med under DLP-paraplyen ved blot at konfigurere en politik, der gælder for dem. Andre, f.eks. lokale fillager, kræver en installation af Azure Information Protection (AIP)-scanner. Du skal forberede dit miljø, lave kodeudkast for politikker og teste dem grundigt, før du aktiverer blokeringshandlinger.

### <a name="deploy-your-policies-in-production"></a>Installér dine politikker i produktion

#### <a name="design-your-policies"></a>Designe dine politikker

Start med at definere dine kontrolmål, og hvordan de gælder på tværs af hver respektive arbejdsbyrde. Udkast en politik, der rummer dine målsætninger. Du er velkommen til at starte med én arbejdsbelastning ad gangen eller på tværs af alle arbejdsbelastninger – det har endnu ingen indvirkning.

#### <a name="implement-policy-in-test-mode"></a>Implementer politik i testtilstand

Evaluer effekten af kontrolelementerne ved at implementere dem med en DLP-politik i testtilstand. Det er ok at anvende politikken på alle arbejdsbelastninger i testtilstand, så du kan få den fulde bredde af resultaterne, men du kan starte med en arbejdsbelastning, hvis du har brug for det.

#### <a name="monitor-outcomes-and-fine-tune-the-policy"></a>Overvåge resultater og finjustere politikken

Når du er i testtilstand, skal du overvåge resultaterne af politikken og finjustere den, så den opfylder dine kontrolmål og samtidig sikre, at du ikke påvirkes negativt eller utilsigtet påvirker gyldige brugerarbejdsprocesser og produktivitet. Her er nogle eksempler på, hvordan du finjusterer:

- juster placeringer og personer/steder, der er in or out of scope
- finjustere de betingelser og undtagelser, der bruges til at afgøre, om et element, og hvad der bliver gjort med det, stemmer overens med politikken
- definition/s af følsomme oplysninger
- handlingerne
- niveauet af begrænsninger
- tilføje nye kontrolelementer
- tilføj nye personer
- tilføj nye begrænsede apps
- tilføje nye begrænsede websteder

#### <a name="enable-the-control-and-tune-your-policies"></a>Aktivér kontrolelementet, og finjuster dine politikker

Når politikken opfylder alle dine målsætninger, skal du aktivere den. Fortsæt med at overvåge resultaterne af politikprogrammet, og finjuster efter behov. 

> [!NOTE]
> Generelt træder politikker i kraft ca. en time efter, at de er blevet slået til.

<!--See, LINK TO topic for SLAs for location specific  details-->

## <a name="dlp-policy-configuration-overview"></a>Oversigt over konfiguration af DLP-politik

Du har fleksibilitet i den måde, du opretter og konfigurerer dine DLP-politikker på. Du kan starte fra en foruddefineret skabelon og oprette en politik med blot nogle få klik, eller du kan designe din egen fra bunden. Uanset hvad du vælger, kræver alle DLP-politikker de samme oplysninger fra dig.

1. **Vælg, hvad du vil overvåge** – Microsoft 365 leveres med mange foruddefinerede politikskabeloner, der kan hjælpe dig med at komme i gang, eller du kan oprette en brugerdefineret politik.
    - En foruddefineret politikskabelon: finansielle data, medicinske og sundhedsdata, data om beskyttelse af personlige oplysninger for alle for forskellige lande og områder.
    - En brugerdefineret politik, der bruger de tilgængelige typer af følsomme oplysninger, opbevaringsmærkater og følsomhedsmærkater.
2. **Vælg, hvor du vil overvåge** – Du vælger en eller flere placeringer, du vil have DLP til at overvåge for følsomme oplysninger. Du kan overvåge:

placering | medtag/udelad efter|
|---------|---------|
|Exchange mail| distributionsgrupper|
|SharePoint websteder |websteder |
|OneDrive konti |konti eller distributionsgrupper |
|Teams chat og kanalmeddelelser |konto eller distributionsgruppe |
|Windows 10, Windows 11 og macOS-enheder (Catalina 10.15 og nyere) |bruger eller gruppe |
|Microsoft Cloud App Security |forekomst |
|Lokale lagre| lagerfilsti|

3. **Vælg de betingelser, der skal matches, for** at en politik kan anvendes på et element – Du kan acceptere forudkonfigurerede betingelser eller definere brugerdefinerede betingelser. Her er nogle eksempler:

- element indeholder en bestemt type følsomme oplysninger, der bruges i en bestemt sammenhæng. Eksempelvis sendes der 95 CPR-numre til modtagere uden for din organisation.
- elementet har en angivet følsomhedsmærkat
- Element med følsomme oplysninger deles enten internt eller eksternt

4. **Vælg den handling, der skal udføre, når politikbetingelserne** er opfyldt – Handlingerne afhænger af den placering, hvor aktiviteten sker.  Her er nogle eksempler:

- SharePoint/Exchange/OneDrive: Bloker personer uden for organisationen til at få adgang til indholdet. Vis brugeren et tip, og send vedkommende en mail om, at vedkommende gør en handling, der er forbudt i henhold til DLP-politikken.
- Teams chat og kanal: Bloker for, at følsomme oplysninger deles i chatten eller kanalen
- Windows 10-, Windows 11- og macOS-enheder (Catalina 10.15 og nyere): Overvåg eller begræns kopiering af et følsomt element til en USB-enhed, der kan fjernes
- Office apps: Vis et pop op-vindue med besked om, at brugeren er i gang med en risikabel funktionsmåde og blokerer eller blokerer, men tillader tilsidesættelse.
- Lokale filshares: Flyt filen fra det sted, hvor den er gemt, til en karantænemappe

> [!NOTE]
> Betingelserne og de handlinger, der skal udføres, er defineret i et objekt, der kaldes en regel.

<!--## Create a DLP policy

All DLP policies are created and maintained in the Microsoft 365 Compliance center. See, INSERT LINK TO ARTICLE THAT WILL START WALKING THEM THROUGH THE POLICY CREATION PROCEDURES for more information.-->

Når du har oprettet en DLP-politik i Overholdelsescenter, gemmes den i et centralt politiklager og synkroniseres derefter til de forskellige indholdskilder, herunder:

- Exchange Online, og derfra til Outlook på internettet og Outlook.
- OneDrive for Business websteder.
- SharePoint onlinewebsteder.
- Office programmer (Excel, PowerPoint og Word).
- Microsoft Teams kanaler og chatmeddelelser.

Når politikken er synkroniseret til de rigtige placeringer, begynder den at evaluere indhold og gennemtvinge handlinger.

## <a name="viewing-policy-application-results"></a>Vise resultater for politikprogram

DLP rapporterer en stor mængde oplysninger til andre Microsoft 365 lige fra overvågning, politik matches og handlinger og brugeraktiviteter. Du skal bruge og reagere på disse oplysninger for at finjustere dine politikker og tilpasse de handlinger, der skal udføre på følsomme elementer. Telemetrien går først til [overvågningslogfilerne Microsoft 365 Overholdelsescenter](search-the-audit-log-in-security-and-compliance.md#search-the-audit-log-in-the-compliance-center), behandles og gør vej til forskellige rapporteringsværktøjer. Hvert rapporteringsværktøj har forskellige formål.

### <a name="dlp-alerts-dashboard"></a>Dashboard for DLP-beskeder

Når DLP tager en handling på et følsomt element, kan du få besked om denne handling via en konfigurerbar besked. I stedet for at disse beskeder hober sig op i en postkasse, som du kan få adgang til, gør Overholdelsescenter dem tilgængelige i [dashboardet til administration af DLP-beskeder](dlp-configure-view-alerts-policies.md). Brug dashboardet for DLP-beskeder til at konfigurere beskeder, gennemse dem, gennemgå dem og spore løsning af DLP-beskeder. Her er et eksempel på beskeder, der genereres af politik matches og aktiviteter fra Windows 10 enheder.

> [!div class="mx-imgBorder"]
> ![Beskedoplysninger.](../media/Alert-info-1.png)

Du kan også få vist oplysninger om den tilknyttede begivenhed med omfattende metadata i det samme dashboard

> [!div class="mx-imgBorder"]
> ![oplysninger om begivenhed.](../media/Event-info-1.png)

### <a name="reports"></a>Rapporter

[DLP-rapporterne](view-the-dlp-reports.md#view-the-reports-for-data-loss-prevention) viser generelle tendenser over tid og giver specifik indsigt i:

- **DLP-politik svarer** over tid og filtrerer efter datointerval, placering, politik eller handling
- **DLP-hændelses** matches viser også matches over tid, men drejes om elementerne i stedet for politikreglerne.
- **Falske DLP-positive og tilsidesættelser** viser antallet af falske positive og, hvis konfigureret, brugertilsidesættelser sammen med brugerberettigelse.

### <a name="dlp-activity-explorer"></a>DLP-aktivitetsstifinder

Fanen Aktivitetsstifinder på DLP-siden har filteret *Aktivitet* forudindstillet *til DLPRuleMatch*. Brug dette værktøj til at gennemgå aktivitet, der er relateret til indhold, der indeholder følsomme oplysninger, eller hvor der er anvendt navne, f.eks. hvilke navne der er blevet ændret, filer er blevet ændret og matchet en regel.

![skærmbillede af DLPRuleMatch-aktivitetsstifinderen, der er begrænset til DLPRuleMatch.](../media/dlp-activity-explorer.png)

Få mere at vide under [Introduktion til aktivitetsstifinder](data-classification-activity-explorer.md)

Du kan få mere at vide Microsoft 365 DLP i:

- [Få mere at Microsoft 365 om forebyggelse af datatab på slutpunkter](endpoint-dlp-learn-about.md)
- [Få mere at vide om standardpolitikken til forebyggelse af datatab i Microsoft Teams (forhåndsvisning)](dlp-teams-default-policy.md)
- [Få mere at vide Microsoft 365 om lokal scanner til forebyggelse af datatab (forhåndsvisning)](dlp-on-premises-scanner-learn.md)
- [Få mere at vide om Microsoft Overholdelsesudvidelse (preview)](dlp-chrome-learn-about.md)
- [Få mere at vide om dashboardet til forebyggelse af datatab](dlp-alerts-dashboard-learn.md)

Du kan få mere at vide om, hvordan du bruger forebyggelse af datatab til at overholde bestemmelser om beskyttelse af data ved at se Udrul beskyttelse af personlige oplysninger [for data med Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy).

## <a name="licensing-and-subscriptions"></a>Licenser og abonnementer

Se [licenskravene til informationsbeskyttelse for at](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection) få mere at vide om de abonnementer, der understøtter DLP.
