---
title: Få mere at vide om styring af insider-risiko
description: Få mere at vide om, hvordan du hjælper med at minimere risikoen i din organisation med styring af insiderrisiko i Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, insiderrisiko, risikostyring, overholdelse af angivne standarder
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.openlocfilehash: 3a2d678f8e653d65007369c2db5ddd8c72a71c66
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923275"
---
# <a name="learn-about-insider-risk-management"></a>Få mere at vide om styring af insider-risiko

> [!TIP]
> *Vidste du, at du kan prøve premiumversionerne af alle ni Microsoft Purview-løsninger gratis?* Brug den 90-dages prøveversion af Purview-løsninger til at udforske, hvordan robuste Purview-funktioner kan hjælpe din organisation med at opfylde sine behov for overholdelse af angivne standarder. Microsoft 365 E3- og Office 365 E3-kunder kan starte nu på [Microsoft Purview-portalen med prøveversioner](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef). Få mere at vide om [, hvem der kan tilmelde sig og prøvevilkår](compliance-easy-trials.md).

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview Insider Risk Management er en løsning til overholdelse af angivne standarder, der hjælper med at minimere interne risici ved at gøre det muligt for dig at registrere, undersøge og reagere på skadelige og utilsigtede aktiviteter i din organisation. Politikker for insiderrisiko giver dig mulighed for at definere de typer risici, der skal identificeres og registreres i din organisation, herunder at reagere på sager og eskalere sager til Microsoft eDiscovery (Premium), hvis det er nødvendigt. Risikoanalytikere i din organisation kan hurtigt udføre de nødvendige handlinger for at sikre, at brugerne overholder organisationens standarder for overholdelse af angivne standarder.

Du kan finde flere oplysninger og en oversigt over planlægningsprocessen for at håndtere risikable aktiviteter i din organisation under [Start af et program til styring af insiderrisiko](https://download.microsoft.com/download/b/2/0/b208282a-2482-4986-ba07-15a9b9286df0/pwc-starting-an-insider-risk-management-program-with-pwc-and-microsoft.pdf).

Se videoerne nedenfor for at få mere at vide om, hvordan styring af insiderrisiko kan hjælpe din organisation med at forhindre, registrere og indeholde risici, samtidig med at du prioriterer organisationens værdier, kultur og brugeroplevelse:
<br>
<br>

**Løsning til styring af insiderrisiko & udvikling**:
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4j9CN]
<br>

**Arbejdsproces til styring af insiderrisiko**:
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OUXB]

Se [Microsoft Mechanics-videoen](https://www.youtube.com/watch?v=Ynkfu8OF0wQ) om, hvordan styring af insiderrisiko og overholdelse af kommunikation fungerer sammen for at minimere datarisici fra brugere i din organisation.

> [!IMPORTANT]
> Styring af insiderrisiko er i øjeblikket tilgængelig i lejere, der hostes i geografiske områder og lande, der understøttes af Azure-tjenesteafhængigheder. Hvis du vil bekræfte, at styring af insiderrisiko understøttes for din organisation, skal du se [Tilgængelighed af Azure-afhængighed efter land/område](/troubleshoot/azure/general/dependency-availability-by-country).

## <a name="modern-risk-pain-points"></a>Moderne risiko smertepunkter

Administration og minimering af risici i din organisation starter med at forstå de typer risici, der findes på den moderne arbejdsplads. Nogle risici er drevet af eksterne hændelser og faktorer, der er uden for direkte kontrol. Andre risici er drevet af interne hændelser og brugeraktiviteter, der kan minimeres og undgås. Nogle eksempler er risici som følge af ulovlig, upassende, uautoriseret eller uetisk adfærd og handlinger udført af brugere i din organisation. Disse funktionsmåder omfatter en lang række interne risici fra brugere:

- Lækager af følsomme data og dataspild
- Fortrolighedsovertrædelser
- Tyveri af intellektuel ejendom (IP)
- Svig
- Insiderhandel
- Overholdelse af regler og standarder

Brugere på den moderne arbejdsplads har adgang til at oprette, administrere og dele data på tværs af en bred vifte af platforme og tjenester. I de fleste tilfælde har organisationer begrænsede ressourcer og værktøjer til at identificere og afhjælpe risici i hele organisationen, samtidig med at de overholder standarderne for beskyttelse af personlige oplysninger for brugerne.

Insiderrisikostyring bruger den fulde bredde af service og tredjepartsindikatorer til at hjælpe dig med hurtigt at identificere, triage og reagere på risikoaktivitet. Ved hjælp af logge fra Microsoft 365 og Microsoft Graph giver insiderrisikostyring dig mulighed for at definere specifikke politikker for at identificere risikoindikatorer. Disse politikker giver dig mulighed for at identificere risikable aktiviteter og reagere for at afhjælpe disse risici.

Insiderrisikostyring er centreret omkring følgende principper:

- **Gennemsigtighed**: Balancer brugerbeskyttelse af personlige oplysninger i forhold til organisationens risiko med arkitekturen for beskyttelse af personlige oplysninger.
- **Konfigurerbar**: Konfigurerbare politikker baseret på branche-, geografiske og forretningsgrupper.
- **Integreret**: Integreret arbejdsproces på tværs af Microsoft Purview-løsninger.
- **Handlingsklar**: Giver indsigt til aktivering af korrekturlæsermeddelelser, dataundersøgelser og brugerundersøgelser.

## <a name="identifying-potential-risks-with-analytics"></a>Identificering af potentielle risici med analyse

Insiderrisikoanalyse giver dig mulighed for at evaluere potentielle insiderrisici i din organisation uden at konfigurere nogen politikker for insiderrisiko. Denne evaluering kan hjælpe din organisation med at identificere potentielle områder med højere brugerrisiko og hjælpe med at bestemme typen og omfanget af politikker for styring af insiderrisiko, som du kan overveje at konfigurere. Denne evaluering kan også hjælpe dig med at fastslå behovet for yderligere licensering eller fremtidig optimering af eksisterende politikker for insiderrisiko.

Hvis du vil vide mere om insiderrisikoanalyse, skal du se [Indstillinger for styring af insiderrisiko: Analytics](insider-risk-management-settings.md#analytics).

## <a name="get-started-with-recommended-actions-preview"></a>Kom i gang med anbefalede handlinger (prøveversion)

Uanset om du konfigurerer styring af insiderrisiko første gang eller kommer i gang med at oprette nye politikker, kan den nye [oplevelse med anbefalede handlinger](insider-risk-management-configure.md#recommended-actions-preview) hjælpe dig med at få mest muligt ud af funktionerne til styring af insiderrisiko. Anbefalede handlinger omfatter konfiguration af tilladelser, valg af politikindikatorer, oprettelse af en politik og meget mere.

## <a name="workflow"></a>Arbejdsproces

Arbejdsprocessen til styring af insiderrisiko hjælper dig med at identificere, undersøge og udføre handlinger for at håndtere interne risici i din organisation. Med fokuserede politikskabeloner, omfattende aktivitet, der signalerer på tværs af Microsoft 365-tjenesten og værktøjer til administration af beskeder og sager, kan du bruge indsigt, der kan handles på, til hurtigt at identificere og reagere på risikobetonet adfærd.

Identificering og løsning af interne risikoaktiviteter og problemer med overholdelse af angivne standarder med styring af insiderrisiko bruger følgende arbejdsproces:

![Arbejdsproces til styring af insiderrisiko.](../media/insider-risk-workflow.png)

### <a name="policies"></a>Politikker

[Politikker for styring af insiderrisiko](insider-risk-management-policies.md) oprettes ved hjælp af foruddefinerede skabeloner og politikbetingelser, der definerer, hvilke udløsende hændelser og risikoindikatorer der undersøges i din organisation. Disse betingelser omfatter, hvordan risikoindikatorer bruges til beskeder, hvilke brugere der er inkluderet i politikken, hvilke tjenester der prioriteres, og overvågningsperioden.

Du kan vælge mellem følgende politikskabeloner for hurtigt at komme i gang med styring af insiderrisiko:

- [Datatyveri foretaget af afrejsende brugere](insider-risk-management-policies.md#data-theft-by-departing-users)
- [Generelle datalækager](insider-risk-management-policies.md#general-data-leaks)
- [Datalækager fra prioriterede brugere (prøveversion)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)
- [Datalækager fra utilfredse brugere (prøveversion)](insider-risk-management-policies.md#data-leaks-by-disgruntled-users-preview)
- [Generelle sikkerhedspolitiske overtrædelser (prøveversion)](insider-risk-management-policies.md#general-security-policy-violations-preview)
- [Generel misbrug af patientdata (prøveversion)](insider-risk-management-policies.md#general-patient-data-misuse-preview)
- [Sikkerhedspolitikovertrædelser af afgåede brugere (prøveversion)](insider-risk-management-policies.md#security-policy-violations-by-departing-users-preview)
- [Sikkerhedspolitikovertrædelser for prioriterede brugere (prøveversion)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Sikkerhedspolitikovertrædelser af utilfredse brugere (prøveversion)](insider-risk-management-policies.md#security-policy-violations-by-disgruntled-users-preview)

![Dashboard med politik for styring af insiderrisiko.](../media/insider-risk-policy-dashboard.png)

### <a name="alerts"></a>Beskeder

Beskeder genereres automatisk af risikoindikatorer, der matcher politikbetingelser og vises i [dashboardet Beskeder](insider-risk-management-activities.md#alert-dashboard). Dette dashboard giver mulighed for hurtigt at få vist alle beskeder, der skal gennemses, åbne beskeder over tid og beskedstatistik for din organisation. Alle politikbeskeder vises med følgende oplysninger, der hjælper dig med hurtigt at identificere status for eksisterende beskeder og nye beskeder, der kræver handling:

- Status
- Sværhedsgraden
- Registreret tid
- Tilfælde
- Sagsstatus

![Advarselsdashboard for styring af insiderrisiko.](../media/insider-risk-alerts-dashboard.png)

### <a name="triage"></a>Triage

Nye brugeraktiviteter, der skal undersøges, genererer automatisk beskeder, der er tildelt statussen *Behovsgennemgang* . Korrekturlæsere kan hurtigt identificere og gennemse, evaluere og triage disse beskeder.

Beskeder løses ved at åbne en ny sag, tildele beskeden til en eksisterende sag eller afvise beskeden. Ved hjælp af beskedfiltre er det nemt hurtigt at identificere beskeder efter status, alvorsgrad eller registreret tid. Som en del af triageprocessen kan korrekturlæsere få vist beskedoplysninger for de aktiviteter, der er identificeret af politikken, få vist brugeraktivitet, der er knyttet til politikmatch, se beskedens alvorsgrad og gennemse oplysninger om brugerprofiler.

![Insider risk management triage.](../media/insider-risk-triage.png)

### <a name="investigate"></a>Undersøg

Undersøg hurtigt alle aktiviteter for en valgt bruger med [brugeraktivitetsrapporter (prøveversion).](insider-risk-management-activities.md#user-activity-reports-preview) Disse rapporter gør det muligt for efterforskere i din organisation at undersøge aktiviteter for bestemte brugere i en defineret tidsperiode uden at skulle tildele dem midlertidigt eller eksplicit til en insiderrisikostyringspolitik. Efter undersøgelse af aktiviteter for en bruger kan efterforskere afvise individuelle aktiviteter som godartede, dele eller sende et link til rapporten via mail med andre efterforskere eller vælge at tildele brugeren midlertidigt eller eksplicit til en insiderrisikostyringspolitik.

[Sager](insider-risk-management-cases.md) oprettes for beskeder, der kræver dybere gennemgang og undersøgelse af aktivitetsdetaljerne og omstændighederne omkring politikmatch. **Dashboardet Sag** indeholder en samlet visning af alle aktive sager, åbne sager over tid og sagsstatistik for din organisation. Korrekturlæsere kan hurtigt filtrere sager efter status, den dato, hvor sagen blev åbnet, og den dato, hvor sagen sidst blev opdateret.

Hvis du vælger en sag på sagsdashboardet, åbnes sagen til undersøgelse og gennemgang. Dette trin er kernen i arbejdsprocessen for styring af insiderrisiko. I dette område syntetiseres risikoaktiviteter, politikbetingelser, beskedoplysninger og brugeroplysninger i en integreret visning for korrekturlæsere. De primære undersøgelsesværktøjer på dette område er:

- **Brugeraktivitet**: Brugeraktivitet vises automatisk i et interaktivt diagram, der afbilder aktiviteter over tid og efter risikoniveau for aktuelle eller tidligere risikoaktiviteter. Korrekturlæsere kan hurtigt filtrere og få vist hele risikooversigten for brugeren og foretage detailudledning i bestemte aktiviteter for at få flere oplysninger.
- **Indholdsoversigt**: Alle datafiler og mails, der er knyttet til vigtige aktiviteter, registreres automatisk og vises i Indholdsoversigt. Korrekturlæsere kan filtrere og få vist filer og meddelelser efter datakilde, filtype, tags, samtale og mange flere attributter.
- **Sagsnoter**: Korrekturlæsere kan angive noter til en sag i afsnittet Sagsnoter. Denne liste konsoliderer alle noter i en central visning og indeholder korrekturlæser og dato for afsendelse af oplysninger.

![Undersøgelse af insiderrisikostyring.](../media/insider-risk-investigate.png)

Derudover giver den nye [overvågningslog (prøveversion)](insider-risk-management-audit-log.md) dig mulighed for at holde dig orienteret om de handlinger, der blev udført på insiderrisikostyringsfunktioner. Denne ressource giver mulighed for uafhængig gennemgang af de handlinger, som brugere, der er tildelt en eller flere insiderrisikostyringsrollegrupper, har udført.

### <a name="action"></a>Handling

Når sager er undersøgt, kan korrekturlæsere hurtigt løse sagen eller samarbejde med andre risikoparter i din organisation. Hvis brugerne utilsigtet eller utilsigtet overtræder politikbetingelserne, kan der sendes en enkel påmindelse til brugeren fra skabeloner til meddelelser, som du kan tilpasse til din organisation. Disse meddelelser kan fungere som enkle påmindelser eller kan dirigere brugeren til oplæring af genopfriskning eller vejledning for at hjælpe med at forhindre fremtidig risikabel adfærd. Du kan få flere oplysninger under [Skabeloner til insiderrisikostyring](insider-risk-management-notices.md).

I mere alvorlige situationer kan det være nødvendigt at dele sagsoplysninger om insiderrisikostyring med andre korrekturlæsere eller -tjenester i din organisation. Styring af insiderrisiko er tæt integreret med andre Microsoft Purview-løsninger for at hjælpe dig med løsning af risici fra ende til anden.

- **eDiscovery (Premium)**: Eskalering af en sag til undersøgelse giver dig mulighed for at overføre data og administration af sagen til Microsoft Purview eDiscovery (Premium). eDiscovery (Premium) indeholder en komplette arbejdsproces til bevarelse, indsamling, gennemgang, analyse og eksport af indhold, der reagerer på din organisations interne og eksterne undersøgelser. Det gør det muligt for juridiske teams at administrere hele arbejdsprocessen for meddelelser om juridiske ventepositioner. Hvis du vil vide mere om eDiscovery(Premium)-sager, skal du se [Oversigt over Microsoft Purview eDiscovery (Premium)](overview-ediscovery-20.md).
- **Integration af API'er til Office 365 Management (prøveversion)**: Styring af insiderrisiko understøtter eksport af beskedoplysninger til SIEM-tjenester (security information and event management) via API'erne til Office 365 Management. Hvis du har adgang til beskedoplysninger på platformen, så de passer bedst til din organisations risikoprocesser, får du større fleksibilitet i forhold til, hvordan du reagerer på risikoaktiviteter. Hvis du vil vide mere om eksport af beskedoplysninger med API'er til Office 365 Administration, skal du se [Eksportér beskeder](insider-risk-management-settings.md#export-alerts).

> [!NOTE]
> Tak for din feedback og support under prøveversionen af ServiceNow-connectoren. Vi har besluttet at afslutte prøveversionen af ServiceNow-connectoren og ophører support i styring af insiderrisiko den 30. november 2020. Vi evaluerer aktivt alternative metoder for at give kunderne serviceNow-integration i styring af insiderrisiko.

## <a name="scenarios"></a>Scenarier

Styring af insiderrisiko kan hjælpe dig med at registrere, undersøge og udføre handlinger for at afhjælpe interne risici i din organisation i flere almindelige scenarier:

### <a name="data-theft-by-departing-users"></a>Datatyveri foretaget af afrejsende brugere

Når brugere forlader en organisation, enten frivilligt eller som følge af opsigelse, er der ofte legitime bekymringer om, at firma-, kunde- og brugerdata er i fare. Brugere kan uskyldigt antage, at projektdata ikke er beskyttet, eller de kan blive fristet til at tage virksomhedsdata til personlig vinding og i strid med virksomhedens politik og juridiske standarder. Politikker for styring af insiderrisiko, der bruger politikskabelonen [Datatyveri ved at forlade brugere](insider-risk-management-policies.md#policy-templates) , registrerer automatisk aktiviteter, der typisk er knyttet til denne type tyveri. Med denne politik modtager du automatisk beskeder om mistænkelige aktiviteter, der er knyttet til datatyveri, af afrejsende brugere, så du kan foretage relevante undersøgelseshandlinger. Konfiguration af en [Microsoft 365 HR-connector](import-hr-data.md) til din organisation er påkrævet for denne politikskabelon.

### <a name="intentional-or-unintentional-leak-of-sensitive-or-confidential-information"></a>Bevidst eller utilsigtet lækage af følsomme eller fortrolige oplysninger

I de fleste tilfælde gør brugerne deres bedste for at håndtere følsomme eller fortrolige oplysninger korrekt. Men nogle gange kan brugere lave fejl, og oplysninger deles ved et uheld uden for organisationen eller overtræder dine politikker for beskyttelse af oplysninger. I andre tilfælde kan brugerne bevidst lække eller dele følsomme og fortrolige oplysninger med ondsindede hensigter og med henblik på potentiel personlig gevinst. Politikker for styring af insiderrisiko, der er oprettet ved hjælp af følgende politikskabeloner til datalækage, registrerer automatisk aktiviteter, der typisk er knyttet til deling af følsomme eller fortrolige oplysninger:

- [Generelle datalækager](insider-risk-management-policies.md#general-data-leaks)
- [Datalækager fra prioriterede brugere (prøveversion)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)
- [Datalækager fra utilfredse brugere (prøveversion)](insider-risk-management-policies.md#data-leaks-by-disgruntled-users-preview)

## <a name="intentional-or-unintentional-security-policy-violations-preview"></a>Tilsigtede eller utilsigtede sikkerhedspolitiske overtrædelser (prøveversion)

Brugerne har typisk en stor grad af kontrol, når de administrerer deres enheder på den moderne arbejdsplads. Dette kontrolelement kan indeholde tilladelser til at installere eller fjerne programmer, der er nødvendige i forbindelse med udførelsen af deres opgaver, eller mulighed for midlertidigt at deaktivere sikkerhedsfunktioner for enheden. Uanset om denne aktivitet er utilsigtet, utilsigtet eller ondsindet, kan denne adfærd udgøre en risiko for din organisation og er vigtig at identificere og handle for at minimere. For at hjælpe med at identificere disse risikable sikkerhedsaktiviteter scorer følgende skabeloner for sikkerhedspolitik for styring af insiderrisiko ved at score indikatorer for sikkerhedsrisiko og bruger Microsoft Defender for Endpoint-beskeder til at give indsigt i sikkerhedsrelaterede aktiviteter:

- [Generelle sikkerhedspolitiske overtrædelser (prøveversion)](insider-risk-management-policies.md#general-security-policy-violations-preview)
- [Sikkerhedspolitikovertrædelser af afgåede brugere (prøveversion)](insider-risk-management-policies.md#security-policy-violations-by-departing-users-preview)
- [Sikkerhedspolitikovertrædelser for prioriterede brugere (prøveversion)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Sikkerhedspolitikovertrædelser af utilfredse brugere (prøveversion)](insider-risk-management-policies.md#security-policy-violations-by-disgruntled-users-preview)

## <a name="policies-for-users-based-on-position-access-level-or-risk-history-preview"></a>Politikker for brugere baseret på placering, adgangsniveau eller risikooversigt (prøveversion)

Brugere i din organisation kan have forskellige risikoniveauer, afhængigt af deres placering, adgangsniveau til følsomme oplysninger eller risikohistorik. Denne struktur kan omfatte medlemmer af organisationens ledelsesteam, it-administratorer, der har omfattende data- og netværksadgangsrettigheder, eller brugere med en tidligere historik over risikable aktiviteter. Under disse omstændigheder er det vigtigt med et nærmere eftersyn og en mere aggressiv risikoscore for at hjælpe med at vise vigtige beskeder til undersøgelse og hurtig handling. Hvis du vil identificere risikable aktiviteter for disse typer brugere, kan du oprette prioriterede brugergrupper og oprette politikker ud fra følgende politikskabeloner:

- [Sikkerhedspolitikovertrædelser for prioriterede brugere (prøveversion)](insider-risk-management-policies.md#security-policy-violations-by-priority-users-preview)
- [Datalækager fra prioriterede brugere (prøveversion)](insider-risk-management-policies.md#data-leaks-by-priority-users-preview)

## <a name="healthcare-preview"></a>Sundhedspleje (prøveversion)

For organisationer i sundhedssektoren har nylige undersøgelser fundet et meget højt antal insiderrelaterede databrud. Registrering af misbrug af patientdata og oplysninger om patientjournaler er en vigtig komponent i sikringen af patienternes privatliv og overholdelse af overholdelsesreglerne, f.eks. HIPAA (Health Insurance Portability and Accountability Act) og HITECH-loven (Health Information Technology for Economic and Clinical Health). Misbrug af patientdata kan variere fra adgang til privilegerede patientjournaler til adgang til patientjournaler fra familie eller naboer med ondsindede hensigter. For at hjælpe med at identificere disse typer risikable aktiviteter bruger følgende skabeloner til styring af insiderrisiko Microsoft 365 HR-connectoren og en sundhedsspecifik dataconnector til at begynde at score risikoindikatorer i forbindelse med adfærd, der kan opstå i dine EHR-systemer (Electronic Heath Record):

- [Generel misbrug af patientdata (prøveversion)](insider-risk-management-policies.md#general-patient-data-misuse-preview)

## <a name="actions-and-behaviors-by-disgruntled-users-preview"></a>Handlinger og funktionsmåder for utilfredse brugere (prøveversion)

Beskæftigelse fremhæver hændelser kan påvirke brugeradfærd på flere måder, der er relateret til insiderrisici. Disse stressfaktorer kan være en gennemgang af dårlig ydeevne, en sænkning af position eller den bruger, der er placeret i en plan for evaluering af ydeevnen. Selvom de fleste brugere ikke reagerer ondsindet på disse hændelser, kan stress af disse handlinger resultere i, at nogle brugere opfører sig på måder, de normalt ikke overvejer under normale omstændigheder. For at hjælpe med at identificere disse typer risikable aktiviteter bruger følgende skabeloner til styring af insiderrisiko microsoft 365 HR-connectoren og starter scoringsrisikoindikatorer i forbindelse med adfærd, der kan opstå i nærheden af stressorhændelser i forbindelse med beskæftigelse:

- [Datalækager fra utilfredse brugere (prøveversion)](insider-risk-management-policies.md#data-leaks-by-disgruntled-users-preview)
- [Sikkerhedspolitikovertrædelser af utilfredse brugere (prøveversion)](insider-risk-management-policies.md#security-policy-violations-by-disgruntled-users-preview)

## <a name="ready-to-get-started"></a>Er du klar til at komme i gang?

- Se [Plan for insiderrisikostyring](insider-risk-management-plan.md) for at få oplysninger om, hvordan du forbereder aktivering af politikker for styring af insiderrisiko i din organisation.
- Se [Kom i gang med indstillinger for styring af insiderrisiko](insider-risk-management-settings.md) for at konfigurere globale indstillinger for politikker for insiderrisiko.
- Se [Kom i gang med styring af insiderrisiko](insider-risk-management-configure.md) for at konfigurere forudsætninger, oprette politikker og begynde at modtage beskeder.
