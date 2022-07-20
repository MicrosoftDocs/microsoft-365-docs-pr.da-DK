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
description: Få mere at vide om, hvordan du beskytter dine følsomme oplysninger ved hjælp af microsoft Purview-politikker og -værktøjer til forebyggelse af datatab og får en rundvisning i DLP-livscyklussen.
ms.openlocfilehash: 46c29b8aa19ce9b70cdb9127ab2c6270c0009a0e
ms.sourcegitcommit: 49c275f78664740988bbc4ca4b14d3ad758e1468
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/19/2022
ms.locfileid: "66882406"
---
# <a name="learn-about-data-loss-prevention"></a>Få mere at vide om forebyggelse af datatab

Organisationer har følsomme oplysninger under deres kontrol, f.eks. finansielle data, beskyttede data, kreditkortnumre, sundhedsjournaler eller cpr-numre. For at beskytte disse følsomme data og reducere risikoen har de brug for en metode til at forhindre deres brugere i at dele dem upassende med personer, der ikke skulle have dem. Denne praksis kaldes forebyggelse af datatab (DLP).

I Microsoft Purview implementerer du forebyggelse af datatab ved at definere og anvende DLP-politikker. Med en DLP-politik kan du identificere, overvåge og automatisk beskytte følsomme elementer på tværs af:

- Microsoft 365-tjenester som Teams, Exchange, SharePoint og OneDrive
- Office-programmer som f.eks. Word, Excel og PowerPoint
- Windows 10, Windows 11 og macOS-slutpunkter (Catalina 10.15 eller nyere)
- cloudapps, der ikke er fra Microsoft
- filshares i det lokale miljø og SharePoint i det lokale miljø.

DLP registrerer følsomme elementer ved hjælp af detaljeret indholdsanalyse og ikke kun ved en simpel tekstscanning. Indhold analyseres for primære data, der svarer til nøgleord, ved evaluering af regulære udtryk, ved intern funktionsvalidering og efter sekundære datamatch, der er i nærheden af det primære datamatch. Ud over dette bruger DLP også algoritmer til maskinel indlæring og andre metoder til at registrere indhold, der stemmer overens med dine DLP-politikker.

## <a name="dlp-is-part-of-the-larger-microsoft-purview-offering"></a>DLP er en del af det større Microsoft Purview-tilbud

DLP er blot et af de Microsoft Purview-værktøjer, du skal bruge til at beskytte dine følsomme elementer, uanset hvor de bor eller rejser. Du bør forstå de andre værktøjer i microsoft Purview-værktøjerne, hvordan de hænger sammen og arbejder bedre sammen.  Se [Microsoft Purview-værktøjer](protect-information.md) for at få mere at vide om beskyttelsesprocessen for oplysninger.

## <a name="protective-actions-of-dlp-policies"></a>Beskyttende handlinger for DLP-politikker

DLP-politikker er den måde, du overvåger de aktiviteter, som brugerne foretager på inaktive følsomme elementer, følsomme elementer under overførsel eller følsomme elementer, der er i brug, og foretager beskyttende handlinger. Hvis en bruger f.eks. forsøger at udføre en forbudt handling, f.eks. kopiering af et følsomt element til en ikke-godkendt placering eller deling af medicinske oplysninger i en mail eller andre betingelser, der er fastsat i en politik, kan DLP:

- vis et tip til en pop op-politik til brugeren, der advarer brugeren om, at vedkommende muligvis forsøger at dele et følsomt element på en forkert måde
- blokere delingen og via et politiktip tillade brugeren at tilsidesætte blokken og registrere brugernes begrundelse
- blokere delingen uden tilsidesættelsesindstillingen
- I forbindelse med inaktive data kan følsomme elementer låses og flyttes til en sikker karantæneplacering
- for Teams-chat vises de følsomme oplysninger ikke

Alle DLP-overvågede aktiviteter registreres som standard i [Microsoft 365-overvågningsloggen](search-the-audit-log-in-security-and-compliance.md) og dirigeres til [Aktivitetsoversigt](data-classification-activity-explorer.md). Når en bruger udfører en handling, der opfylder kriterierne i en DLP-politik, og du har konfigureret beskeder, leverer DLP beskeder på [dashboardet til administration af DLP-beskeder](dlp-configure-view-alerts-policies.md).

## <a name="dlp-lifecycle"></a>DLP-livscyklus

En DLP-implementering følger typisk disse overordnede faser.

- [Plan for DLP](#plan-for-dlp)
- [Forbered dig på DLP](#prepare-for-dlp)
- [Udrul dine politikker i produktion](#deploy-your-policies-in-production)


### <a name="plan-for-dlp"></a>Plan for DLP

DLP-overvågning og -beskyttelse er indbygget i de programmer, som brugerne bruger hver dag. Dette hjælper med at beskytte dine organisationers følsomme elementer mod risikable aktiviteter, selvom dine brugere ikke er vant til at tænke og praktisere forebyggelse af datatab. Hvis din organisation og dine brugere er nye inden for forebyggelse af datatab, kan indførelsen af DLP kræve en ændring af dine forretningsprocesser, og der vil være et kulturskift for dine brugere. Men med korrekt planlægning, test og justering beskytter dine DLP-politikker dine følsomme elementer, samtidig med at du minimerer eventuelle afbrydelser af forretningsprocesser.

**Teknologiplanlægning til DLP**

Vær opmærksom på, at DLP som teknologi kan overvåge og beskytte inaktive data, data i brug og data i bevægelse på tværs af Microsoft 365-tjenester, Windows 10, Windows 11 og macOS-enheder (Catalina 10.15 og nyere), filshares i det lokale miljø og SharePoint i det lokale miljø. Der er planlægningsmæssige konsekvenser for de forskellige placeringer, den type data, du vil overvåge og beskytte, og de handlinger, der skal udføres, når en politik matcher.

**Planlægning af forretningsprocesser for DLP**

DLP-politikker kan blokere forbudte aktiviteter, f.eks. upassende deling af følsomme oplysninger via mail. Når du planlægger dine DLP-politikker, skal du identificere de forretningsprocesser, der berører dine følsomme elementer. Ejerne af forretningsprocesser kan hjælpe dig med at identificere relevante brugeradfærd, der skal være tilladt, og upassende brugeradfærd, der skal beskyttes mod. Du bør planlægge dine politikker og installere dem i testtilstand og evaluere deres indvirkning via [Aktivitetsoversigt](data-classification-activity-explorer.md) først, før du anvender dem i mere restriktive tilstande.

**Organisationskulturplanlægning for DLP**

En vellykket DLP-implementering er lige så meget afhængig af at få dine brugere oplært og acclimeret i praksis for forebyggelse af datatab, som det er i veltilrettelagte og finjusterede politikker. Da dine brugere er meget involveret, skal du også planlægge træning for dem. Du kan strategisk bruge politiktips til at øge bevidstheden over for dine brugere, før du ændrer håndhævelsen af politikken fra testtilstand til mere restriktive tilstande.

<!--For more information on planning for DLP, including suggestions for deployment based on your needs and resources, see [Planning for data loss prevention](dlp-plan-for-dlp.md).-->

### <a name="prepare-for-dlp"></a>Forbered dig på DLP

Du kan anvende DLP-politikker på inaktive data, data i brug og data i gang på placeringer, f.eks.:

- Exchange Online mail
- SharePoint Online-websteder
- OneDrive-konti
- Teams-chat- og kanalmeddelelser
- Microsoft Defender for Cloud Apps
- Windows 10-, Windows 11- og macOS-enheder (Catalina 10.15 eller nyere)
- Lagre i det lokale miljø
- PowerBI-websteder

Hver har forskellige forudsætninger. Følsomme elementer på nogle placeringer, f.eks. Exchange Online, kan overføres under DLP-paraplyen ved blot at konfigurere en politik, der gælder for dem. Andre, f.eks. fillagre i det lokale miljø, kræver en udrulning af AIP-scanner (Azure Information Protection). Du skal forberede dit miljø, kodeudkast til politikker og teste dem grundigt, før du aktiverer eventuelle blokeringshandlinger.

### <a name="deploy-your-policies-in-production"></a>Udrul dine politikker i produktion

#### <a name="design-your-policies"></a>Design dine politikker

Start med at definere dine kontrolmål, og hvordan de gælder på tværs af hver enkelt arbejdsbelastning. Udkast til en politik, der omfatter dine målsætninger. Du er velkommen til at starte med én arbejdsbelastning ad gangen eller på tværs af alle arbejdsbelastninger – der er endnu ingen indvirkning.

#### <a name="implement-policy-in-test-mode"></a>Implementer politik i testtilstand

Evaluer virkningen af kontrolelementerne ved at implementere dem med en DLP-politik i testtilstand. Det er ok at anvende politikken på alle arbejdsbelastninger i testtilstand, så du kan få det fulde resultatbredde, men du kan starte med én arbejdsbelastning, hvis du har brug for det.

#### <a name="monitor-outcomes-and-fine-tune-the-policy"></a>Overvåg resultaterne, og finjuster politikken

I testtilstand skal du overvåge resultaterne af politikken og finjustere den, så den opfylder dine kontrolmål, samtidig med at du sikrer, at du ikke påvirkes negativt eller utilsigtet påvirker gyldige brugerarbejdsprocesser og produktivitet. Her er nogle eksempler på ting, du kan finjustere:

- justere de placeringer og personer/steder, der er inden for eller uden for området
- tilpasse de betingelser og undtagelser, der bruges til at bestemme, om et element, og hvad der udføres med det, stemmer overens med politikken
- definition/definition af følsomme oplysninger
- handlingerne
- begrænsningernes niveau
- tilføj nye kontrolelementer
- tilføj nye personer
- tilføj nye begrænsede apps
- tilføj nye begrænsede websteder

> [!NOTE]
> _Stop behandlingen af flere regler_ fungerer ikke i testtilstand, selvom den er slået til.

#### <a name="enable-the-control-and-tune-your-policies"></a>Aktivér kontrolelementet, og juster dine politikker

Når politikken opfylder alle dine mål, skal du aktivere den. Fortsæt med at overvåge resultaterne af politikprogrammet og indstille efter behov. 

> [!NOTE]
> Politikker træder generelt i kraft ca. en time efter, at de er slået til.

<!--See, LINK TO topic for SLAs for location specific  details-->

## <a name="dlp-policy-configuration-overview"></a>Oversigt over konfiguration af DLP-politik

Du har fleksibilitet i den måde, du opretter og konfigurerer dine DLP-politikker på. Du kan starte fra en foruddefineret skabelon og oprette en politik med blot nogle få klik, eller du kan designe din egen fra bunden. Uanset hvilket du vælger, kræver alle DLP-politikker de samme oplysninger fra dig.

1. **Vælg, hvad du vil overvåge** – DLP leveres med mange foruddefinerede politikskabeloner, der kan hjælpe dig med at komme i gang, eller du kan oprette en brugerdefineret politik.
    - En foruddefineret politikskabelon: Økonomiske data, Medicinske og sundhedsdata, Data om beskyttelse af personlige oplysninger for alle for forskellige lande og områder.
    - En brugerdefineret politik, der bruger de tilgængelige typer følsomme oplysninger, opbevaringsmærkater og følsomhedsmærkater.
2. **Vælg, hvor du vil overvåge** – Du vælger en eller flere placeringer, som DLP skal overvåge for følsomme oplysninger. Du kan overvåge:

Placering | include/exclude by|
|---------|---------|
|Exchange-mail| distributionsgrupper|
|SharePoint-websteder |Websteder |
|OneDrive-konti |konti eller distributionsgrupper |
|Teams-chat- og kanalmeddelelser |konto eller distributionsgruppe |
|Windows 10-, Windows 11- og macOS-enheder (Catalina 10.15 eller nyere) |bruger eller gruppe |
|Microsoft Cloud App Security |Eksempel |
|Lagre i det lokale miljø| filsti til lager|

3. **Vælg de betingelser, der skal matches, for at en politik kan anvendes på et element** – Du kan acceptere forudkonfigurerede betingelser eller definere brugerdefinerede betingelser. Nogle eksempler er:

- elementet indeholder en angivet type følsomme oplysninger, der bruges i en bestemt kontekst. For eksempel 95 cpr-numre, der sendes via mail til modtageren uden for din organisation.
- elementet har en angivet følsomhedsmærkat
- element med følsomme oplysninger deles enten internt eller eksternt

4. **Vælg den handling, der skal udføres, når politikbetingelserne er opfyldt** – Handlingerne afhænger af den placering, hvor aktiviteten finder sted.  Nogle eksempler er:

- SharePoint/Exchange/OneDrive: Bloker personer uden for din organisationsformular, der har adgang til indholdet. Vis brugeren et tip, og send brugeren en mailmeddelelse om, at vedkommende foretager en handling, der er forbudt i forbindelse med DLP-politikken.
- Teams-chat og -kanal: Bloker følsomme oplysninger fra at blive delt i chatten eller kanalen
- Windows 10, Windows 11 og macOS-enheder (Catalina 10.15 eller nyere): Overvåg eller begræns kopiering af et følsomt element til en USB-enhed, der kan fjernes
- Office-apps: Vis et pop op-vindue, der giver brugeren besked om, at brugeren er involveret i en risikabel funktionsmåde, og blokerer eller blokerer, men tillader tilsidesættelse.
- Filshares i det lokale miljø: Flyt filen fra det sted, hvor den er gemt, til en karantænemappe

> [!NOTE]
> Betingelserne og de handlinger, der skal udføres, er defineret i et objekt, der kaldes en regel.

<!--## Create a DLP policy

All DLP policies are created and maintained in the Microsoft Purview center. See, INSERT LINK TO ARTICLE THAT WILL START WALKING THEM THROUGH THE POLICY CREATION PROCEDURES for more information.-->

Når du har oprettet en DLP-politik i Overholdelsescenter, gemmes den i et centralt politiklager og synkroniseres derefter med de forskellige indholdskilder, herunder:

- Exchange Online og derfra til Outlook på internettet og Outlook.
- OneDrive for Business websteder.
- SharePoint Online-websteder.
- Office-skrivebordsprogrammer (Excel, PowerPoint og Word).
- Microsoft Teams-kanaler og chatbeskeder.

Når politikken er synkroniseret til de rigtige placeringer, begynder den at evaluere indhold og gennemtvinge handlinger.

## <a name="viewing-policy-application-results"></a>Visning af resultater for politikprogram

DLP rapporterer en stor mængde oplysninger til Microsoft Purview fra overvågning, politikkampe og handlinger og brugeraktiviteter. Du skal bruge og reagere på disse oplysninger for at justere dine politikker og triage handlinger, der udføres på følsomme elementer. Telemetrien går først ind i [Microsoft Purview-compliance-portal Overvågningslogge](search-the-audit-log-in-security-and-compliance.md#search-the-audit-log-in-the-compliance-portal) behandles og gør sin vej til forskellige rapporteringsværktøjer. Hvert rapporteringsværktøj har forskellige formål.

### <a name="dlp-alerts-dashboard"></a>DLP-beskeddashboard

Når DLP udfører en handling på et følsomt element, kan du få besked om denne handling via en besked, der kan konfigureres. I stedet for at få disse beskeder hobet sig op i en postkasse, som du kan gennemgå, gør Overholdelsescenter dem tilgængelige i [dashboardet til administration af DLP-beskeder](dlp-configure-view-alerts-policies.md). Brug dashboardet DLP-beskeder til at konfigurere beskeder, gennemse dem, triage dem og spore opløsningen af DLP-beskeder. Her er et eksempel på beskeder, der genereres af politikkampe og -aktiviteter fra Windows 10 enheder.

> [!div class="mx-imgBorder"]
> ![Beskedoplysninger.](../media/Alert-info-1.png)

Du kan også få vist detaljer om den tilknyttede hændelse med omfattende metadata på det samme dashboard

> [!div class="mx-imgBorder"]
> ![hændelsesoplysninger.](../media/Event-info-1.png)

### <a name="reports"></a>Rapporter

[DLP-rapporterne](view-the-dlp-reports.md#view-the-reports-for-data-loss-prevention) viser brede tendenser over tid og giver specifik indsigt i:

- **DLP-politik Matcher** over tid og filtrerer efter datointerval, placering, politik eller handling
- **DLP-hændelsesforekomster** viser også matches over tid, men vippes om elementerne i stedet for politikreglerne.
- **DLP-falske positiver og tilsidesættelser** viser antallet af falske positiver og, hvis de er konfigureret, brugertilsidesættelser sammen med brugerberettigelsen.

### <a name="dlp-activity-explorer"></a>DLP-aktivitetsoversigt

Fanen Aktivitetsoversigt på DLP-siden har filteret *Aktivitet* forudindstillet til *DLPRuleMatch*. Brug dette værktøj til at gennemse aktiviteter, der er relateret til indhold, der indeholder følsomme oplysninger, eller hvor der er anvendt mærkater, f.eks. hvilke mærkater der er blevet ændret, filer er blevet ændret og matchet med en regel.

![skærmbillede af DLPRuleMatch-områdebaseret aktivitetsoversigt.](../media/dlp-activity-explorer.png)

Du kan få flere oplysninger under [Kom i gang med aktivitetsoversigt](data-classification-activity-explorer.md)

Hvis du vil vide mere om Microsoft Purview DLP, skal du se:

- [Få mere at vide om forebyggelse af datatab ved slutpunkt](endpoint-dlp-learn-about.md)
- [Få mere at vide om standardpolitikken for forebyggelse af datatab i Microsoft Teams (prøveversion)](dlp-teams-default-policy.md)
- [Få mere at vide om scanner til forebyggelse af datatab i det lokale miljø](dlp-on-premises-scanner-learn.md)
- [Få mere at vide om Microsoft Overholdelsesudvidelse](dlp-chrome-learn-about.md)
- [Få mere at vide om dashboardet til forebyggelse af datatab](dlp-alerts-dashboard-learn.md)

Hvis du vil vide mere om, hvordan du bruger forebyggelse af datatab til at overholde reglerne for beskyttelse af personlige oplysninger, skal du se [Udrul regler om beskyttelse af personlige oplysninger med Microsoft Purview](../solutions/information-protection-deploy.md)  (aka.ms/m365dataprivacy).

## <a name="licensing-and-subscriptions"></a>Licenser og abonnementer

Se [licenskravene for Information Protection for](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection) at få oplysninger om de abonnementer, der understøtter DLP.
