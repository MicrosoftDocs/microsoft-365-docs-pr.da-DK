---
title: Brug af forebyggelse af datatab på slutpunkt
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
description: Få mere at vide om, hvordan du konfigurerer politikker til forebyggelse af datatab (DLP) Microsoft 365 at bruge endpoint-placeringer til forebyggelse af datatab (EPDLP).
ms.openlocfilehash: cecd489aa5ceb5f0d5d233a4bf09caa24dee6f8b
ms.sourcegitcommit: 40f89c46032ea33de25417106f39cbeebef5a049
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/10/2022
ms.locfileid: "63599892"
---
# <a name="using-endpoint-data-loss-prevention"></a>Brug af forebyggelse af datatab på slutpunkt

I denne artikel gennemgås fire scenarier, hvor du opretter og redigerer en DLP-politik, der bruger enheder som en placering.

## <a name="dlp-settings"></a>DLP-indstillinger

Før du går i gang, skal du konfigurere dine DLP-indstillinger. Indstillinger anvendes på alle DLP-politikker for enheder. Du skal konfigurere disse, hvis du vil oprette politikker, der gennemtvinger:

- skybaserede udgangspunktbegrænsninger
- ikke-tilladte appbegrænsninger

Eller

- Hvis du vil udelukke støjende filstier fra overvågning

  > [!div class="mx-imgBorder"]
  > ![DLP-indstillinger.](../media/endpoint-dlp-1-using-dlp-settings.png)

### <a name="endpoint-dlp-windows-1011-and-macos-settings"></a>Slutpunkt DLP-Windows 10/11 og macOS-indstillinger

|Indstilling |Windows 10, 1809 og nyere, Windows 11  |macOS Catalina 10.15 eller nyere (forhåndsvisning)  |Bemærkninger  |
|---------|---------|---------|---------|
|Udeladelse af filsti     |Understøttet         |Understøttet         |macOS indeholder en anbefalet liste over udeladelsesindstillinger, der er til som standard          |
|Ikke-tilladte apps     |Understøttet         |Understøttet         |         |
|Ikke tilladt Bluetooth apps    |Understøttet         |Ikke understøttet         |         |
|Browser- og domænebegrænsninger for følsomme elementer      |Understøttet         |Understøttet         |         |
|Yderligere indstillinger for Slutpunkt DLP     |Understøttet         |Understøttet         |Kun virksomhedens standardberettigelse understøttes for macOS-enheder         |
|Altid overvåge filaktivitet for enheder     |Understøttet         |Understøttet         |         |
|Automatisk karantæne af fil fra ikke-tilladte apps | Understøttet | Ikke understøttet| |
|Avanceret klassificering | Understøttet | Ikke understøttet| |
|Forretningsberettigelse i politiktip | Understøttet | Understøttet| |

### <a name="advanced-classification-scanning-and-protection"></a>Avanceret scanning og beskyttelse af klassificering

Avanceret scanning og beskyttelse af klassificering giver den mere avancerede Microsoft 365 skybaserede dataklassificeringstjeneste til at scanne elementer, klassificere dem og returnere resultaterne til den lokale computer. Det betyder, at du kan drage fordel af [klassificeringsteknikker](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md) for specifikke datamatching, navngivne enheder (forhåndsvisning [)](named-entities-learn.md#learn-about-named-entities-preview) i dine DLP-politikker.

I avanceret klassificering sendes indhold fra den lokale enhed til skytjenesterne til scanning og klassificering. Hvis udnyttelse af båndbredde er et problem, kan du angive en grænse i denne globale indstilling, der anvendes pr. enhed på, hvor meget der kan bruges i en rullende 24-timers periode. Hvis du angiver en begrænsning for anvendelsen af båndbredde, og den overskrides, stopper DLP med at sende brugerindhold til skyen, og dataklassificeringen fortsætter lokalt på enheden. Når den akkumulerede udnyttelse af båndbredden falder under den rullende 24-timers grænse, genoptages kommunikationen med skytjenesterne.

Hvis udnyttelse af båndbredde ikke er et problem, kan du ikke angive en grænse og tillade ubegrænset brug.

Disse Windows versioner understøtter avanceret scanning og beskyttelse af klassificering:

- Windows 10 20H1/20H2/21H1 (KB 5006738)
- Windows 10 version 19H1/19H2 (KB 5007189)
- Windows 10 RS5 (KB 5006744)

> [!NOTE]
> Understøttelse af avanceret klassificering er tilgængelig for Office (Word-, Excel-, PowerPoint) og PDF-filtyper.

> [!NOTE]
> DLP-politikevaluering forekommer altid i skyen, også selvom der ikke sendes brugerindhold.

### <a name="file-path-exclusions"></a>Udeladelse af filsti

Open [Compliance CenterData](https://compliance.microsoft.com) >  **loss preventionEndpoint** >  **DLP settingsFile** >  **path exclusions**.

Det kan være en god ide at udelukke bestemte stier fra håndhævelsen af DLP-overvågning, DLP-påmindelser og DLP-politikken på dine enheder, fordi de er for støjende eller ikke indeholder filer, du er interesseret i. Filer på disse placeringer overvåges ikke, og alle filer, der oprettes eller ændres på disse placeringer, vil ikke være underlagt DLP-politikkens håndhævelse. Du kan konfigurere udeladelse af stier i DLP-indstillinger.

#### <a name="windows-10-devices"></a>Windows 10 enheder

Du kan bruge denne logik til at opbygge dine udeladelsesstier til Windows 10 enheder:

- Gyldig filsti, der slutter med `\`, hvilket betyder, at det kun er filer direkte under mappen. <br/>For eksempel: `C:\Temp\`

- Gyldig filsti, der slutter med `\*`, hvilket betyder, at det kun er filer under undermapper, ud over filerne direkte under mappen. <br/>For eksempel: `C:\Temp\*`

- Gyldig filsti, der slutter uden `\` eller `\*`, hvilket betyder, at alle filer direkte under mappe og alle undermapper. <br/>For eksempel: `C:\Temp`

- En sti med jokertegn mellem `\` fra hver side. <br/>For eksempel: `C:\Users\*\Desktop\`

- En sti med jokertegn mellem `\` hver side og med for `(number)` at give det nøjagtige antal undermapper. <br/>For eksempel: `C:\Users\*(1)\Downloads\`

- En sti med SYSTEM-miljøvariabler. <br/>For eksempel: `%SystemDrive%\Test\*`

- En blanding af alt ovenfor. <br/>For eksempel: `%SystemDrive%\Users\*\Documents\*(2)\Sub\`

#### <a name="macos-devices-preview"></a>macOS-enheder (forhåndsvisning)

Ligesom Windows 10-enheder kan du tilføje dine egne udeladelser for macOS-enheder.

- Definitioner af filstier kan ikke bruges til store og små bogstaver, så `User` det er det samme som `user`.

- Jokertegnsværdier understøttes. Så en stidefinition kan indeholde `*` en i midten af stien eller i slutningen af stien. For eksempel: `/Users/*/Library/Application Support/Microsoft/Teams/*`

#####  <a name="recommended-file-path-exclusions-preview"></a>Anbefalede udeladelse af filstier (forhåndsvisning)

Af hensyn til ydeevnen omfatter Slutpunkt DLP en liste over anbefalede filstier for macOS-enheder. Disse undtagelser er som standard slået til. Du kan deaktivere dem, hvis du vil, ved at slå **til/fra-knappen Medtag anbefalede** filstier for Mac til/ fra. Listen indeholder:

- /Applications/*
- /System/*
- /usr/*
- /Library/*
- /private/*
- /opt/*
- /Users/*/Library/Application Support/Microsoft/Teams/*

### <a name="unallowed-apps"></a>Ikke-tilladte apps

Ikke-tilladte apps er en liste over programmer, som du opretter, og som ikke har tilladelse til at få adgang til en DLP-beskyttet fil. Den er tilgængelig til Windows 10 og macOS-enheder (forhåndsvisning).

Når indstillingen Tilgås  af apps, der ikke er tilladt for en politik er slået til, og en app, der er på listen over tilladte, forsøger at få adgang til en beskyttet fil, tillades, blokeres eller blokeres aktiviteten, men brugere kan tilsidesætte begrænsningen. Alle aktiviteter overvåges og kan gennemses i Aktivitetsoversigt.

> [!IMPORTANT]
> Medtag ikke stien til den eksekverbare, men kun det eksekverbare navn (f.eksbrowser.exe).

#### <a name="macos-devices-preview"></a>macOS-enheder (forhåndsvisning)

Ligesom på Windows-enheder kan du nu forhindre macOS-apps i at få adgang til følsomme data ved at definere dem på listen **Over ikke-tilladte** apps. 

> [!NOTE]
> Bemærk, at apps på tværs af platforme skal indtastes med deres entydige stier til det operativsystem, de kører på.

Sådan finder du hele stien til Mac-apps:

1. Åbn Aktivitetsovervågning på **macOS-enheden**. Find og dobbeltklik på den proces, du vil begrænse

2. Vælg **fanen Åbn filer og** porte.
  
3. For macOS-apps skal du bruge det fulde stinavn, herunder navnet på appen.

#### <a name="protect-sensitive-data-from-cloud-synchronization-apps"></a>Beskyt følsomme data fra skysynkroniseringsapps

Hvis du vil forhindre følsomme elementer i at blive synkroniseret til skyen af skysynkroniseringsapps, f.eks. *onedrive.exe*, skal du føje synkroniseringsappen til skyen til **listen Ikke-tilladte** apps. Når en ikke-tilladt app til skysynkronisering forsøger at få adgang til et element, der er beskyttet af en blokerende DLP-politik, kan DLP generere gentagne meddelelser. Du kan undgå disse gentagne meddelelser ved at aktivere **indstillingen Automatisk** karantæne under **Ikke tilladte apps**.  

##### <a name="auto-quarantine-preview"></a>Automatisk karantæne (forhåndsvisning)

> [!NOTE]
> Automatisk karantæne understøttes kun i Windows 10

Når denne indstilling er aktiveret, aktiveres Automatisk karantæne, når en ikke-tilladt app forsøger at få adgang til et DLP-beskyttet følsomt element. Automatisk karantæne flytter det følsomme element til en administratorkonfigureret mappe og kan lade en **.txt-fil** blive i stedet for den oprindelige. Du kan konfigurere teksten i pladsholderfilen for at fortælle brugerne, hvor elementet blev flyttet til, og andre relevante oplysninger.  

Du kan bruge automatisk karantæne for at forhindre en endeløs kæde af DLP-meddelelser til brugeren og administratorerne – se Scenarie 4: Undgå at gentage [DLP-meddelelser](#scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview) fra skysynkroniseringsapps med automatisk karantæne (forhåndsvisning).

### <a name="unallowed-bluetooth-apps"></a>Ikke tilladt Bluetooth apps

Undgå, at personer overfører filer, der er beskyttet af dine politikker, via bestemte Bluetooth apps.

### <a name="browser-and-domain-restrictions-to-sensitive-data"></a>Browser- og domænebegrænsninger for følsomme data

Begræns følsomme filer, der svarer til dine politikker, i at blive delt med ikke-ubegrænset skytjenestedomæner.

#### <a name="unallowed-browsers"></a>Ikke-tilladte browsere

For Windows enheder, du tilføjer browsere, identificeret ved deres eksekverbare navne, der vil være blokeret fra at få adgang til filer, der opfylder betingelserne i en gennemtvunget DLP-politik, hvor begrænsningen for upload til skytjenester er indstillet til at blokere eller blokere tilsidesættelse. Når disse browsere er blokeret fra at få adgang til en fil, får slutbrugerne vist en toastbesked, der beder dem om at åbne filen via Microsoft Edge eller vise en tilpasset meddelelse, hvis en sådan er konfigureret.

På macOS-enheder skal du tilføje den fulde filsti. Sådan finder du hele stien til Mac-apps:

1. Åbn Aktivitetsovervågning på **macOS-enheden**. Find og dobbeltklik på den proces, du vil begrænse

2. Vælg **fanen Åbn filer og** porte.
  
3. For macOS-apps skal du bruge det fulde stinavn, herunder navnet på appen.

#### <a name="service-domains"></a>Tjenestedomæner

> [!NOTE]
> Indstillingen **Tjenestedomæner gælder kun** for filer, der er overført ved hjælp Microsoft Edge eller Google Chrome, hvor [Microsoft Overholdelsesudvidelse er](dlp-chrome-learn-about.md#learn-about-the-microsoft-compliance-extension) installeret.

Du kan styre, om følsomme filer, der er beskyttet af dine politikker, kan overføres til bestemte tjenestedomæner fra Microsoft Edge.

Hvis listetilstanden er **indstillet til** Bloker, vil brugeren ikke kunne overføre følsomme elementer til disse domæner. Når en overførselshandling blokeres, fordi et element svarer til en DLP-politik, genererer DLP enten en advarsel eller blokerer upload af det følsomme element.

Hvis listetilstanden er indstillet til **Tillad, vil** brugerne kun kunne uploade følsomme elementer til **** disse domæner, og upload af adgang til alle andre domæner er ikke tilladt.

> [!IMPORTANT]
> Når tjenestebegrænsningstilstanden er indstillet til "Tillad", skal du have mindst ét tjenestedomæne konfigureret, før begrænsninger håndhæves.

Brug FQDN-formatet for tjenestedomænet uden endelsen `.` 

Eksempel:

 `www.contoso.com` 

Jokertegn understøttes ikke.

### <a name="additional-settings-for-endpoint-dlp"></a>Yderligere indstillinger for slutpunkt DLP

#### <a name="business-justification-in-policy-tips"></a>Forretningsberettigelse i politiktip

Du kan styre, hvordan brugere interagerer med indstillingen forretningsberettigelse i tipmeddelelser for DLP-politik. Denne indstilling vises, når brugere udfører en aktivitet, der er beskyttet af **indstillingen Bloker med tilsidesættelse** i en DLP-politik. Dette er en global indstilling. Du kan vælge mellem en af følgende indstillinger:

- **Vis standardindstillinger og brugerdefineret tekstfelt**: Som standard kan brugerne vælge enten en indbygget justering eller angive deres egen tekst.
- **Vis kun standardindstillinger**: Brugerne kan kun vælge en indbygget justering.
- **Vis kun brugerdefineret tekstfelt**: Brugerne kan kun angive deres egen begrundelse. Det er kun tekstfeltet, der vises i tipbeskeden om politik til slutbrugeren. 

##### <a name="customizing-the-options-in-the-drop-down-menu"></a>Tilpasning af indstillingerne i rullemenuen

Du kan oprette op til fem tilpassede indstillinger, der vises, når brugerne interagerer med politikmeddelelsestip ved at vælge **rullemenuen Tilpas indstillinger**. 


|Indstilling |Standardtekst  |
|---------|---------|
|mulighed 1    | **Dette er en del af en etableret forretningsarbejdsproces**  , eller du kan indtaste tilpasset tekst        |
|mulighed 2  |**Min chef har godkendt denne handling,** eller du kan angive brugerdefineret tekst         |
|mulighed 3   |**Haster adgang påkrævet. Jeg giver min chef besked separat,** eller du kan angive brugerdefineret tekst          |
|Indstillingen Vis falsk positiv     |**Oplysningerne i disse filer er ikke følsomme,** eller du kan indtaste tilpasset tekst          |
|mulighed 5    |**Andet** , eller du kan skrive tilpasset tekst         |

<!--See [Scenario 5: Configure a policy to use the customized business justification](#scenario-5-configure-a-policy-to-use-the-customized-business-justification)-->

### <a name="always-audit-file-activity-for-devices"></a>Altid overvåge filaktivitet for enheder

Når enheder er onboardet, overvåges aktivitet for filer Office PDF- og CSV-filer som standard automatisk og kan gennemses i Aktivitetsoversigt. Slå denne funktion fra, hvis du kun vil have denne aktivitet overvåget, når onboardede enheder er inkluderet i en aktiv politik.

Filaktivitet overvåges altid for onboardede enheder, uanset om de er inkluderet i en aktiv politik.

## <a name="tying-dlp-settings-together"></a>At binde DLP-indstillinger sammen

Med Endpoint DLP og Edge Chromium-webbrowser kan du begrænse utilsigtet deling af følsomme elementer til ikke-tilladte skyapps og -tjenester. Edge Chromium forstå, når et element begrænses af en Slutpunkt DLP-politik og gennemtvinger adgangsbegrænsninger.

Når du bruger Slutpunkt DLP som en placering i en korrekt konfigureret DLP-politik og Microsoft Edge-browseren, vil de ikke-tilladte browsere, du har defineret i disse indstillinger, være forhindret i at få adgang til de følsomme elementer, der passer til dine DLP-politikkontrolelementer. I stedet vil brugerne blive omdirigeret til at bruge Microsoft Edge, som med en forståelse af de DLP-pålagde begrænsninger kan blokere eller begrænse aktiviteter, når betingelserne i DLP-politikken er opfyldt.

Hvis du vil bruge denne begrænsning, skal du konfigurere tre vigtige dele:

1. Angiv de steder – tjenester, domæner og IP-adresser – som du vil forhindre, at følsomme elementer deles med.

2. Tilføj de browsere, der ikke har tilladelse til at få adgang til bestemte følsomme elementer, når der opstår et DLP-politik match.

3. Konfigurer DLP-politikker til at definere typer af følsomme elementer, som uploads skal begrænses til disse steder ved at slå **Upload** til skytjenester og Access fra **ikke-tilladt browser**.

Du kan fortsætte med at tilføje nye tjenester, apps og politikker for at udvide og udvide dine begrænsninger, så de opfylder virksomhedens behov, og beskytte følsomme data. 

Denne konfiguration hjælper med at sikre, at dine data forbliver sikre, og samtidig undgå unødvendige begrænsninger, der forhindrer eller begrænser brugere i at få adgang til og dele ikke-følsomme elementer.

## <a name="endpoint-dlp-policy-scenarios"></a>Scenarier for DLP-politik for slutpunkter

For at gøre dig bekendt med slutpunkt-DLP-funktioner, og hvordan de findes i DLP-politikker, har vi samlet nogle scenarier, som du kan følge.

> [!IMPORTANT]
> Disse Slutpunkt-DLP-scenarier er ikke de officielle procedurer for oprettelse og justering af DLP-politikker. Se nedenstående emner, når du har brug for at arbejde med DLP-politikker i generelle situationer:
>
>- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
>- [Introduktion til DLP-standardpolitikken](get-started-with-the-default-dlp-policy.md)
>- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
>- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)

### <a name="scenario-1-create-a-policy-from-a-template-audit-only"></a>Scenarie 1: Opret en politik ud fra en skabelon, kun overvågning

Disse scenarier kræver, at du allerede har enheder onboardet og rapportering i Aktivitetsoversigt. Hvis du ikke har onboardede enheder endnu, kan du se [Introduktion til forebyggelse af datatab i](endpoint-dlp-getting-started.md) slutpunkt.

1. Åbn siden [forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Vælg **Opret politik**.

3. I dette scenarie skal **du** vælge Beskyttelse af **personlige oplysninger og derefter USA Personidentificerbare oplysninger (PII)-data** og vælge **Næste**.

4. Slå feltet **Status fra** for alle placeringer undtagen **Enheder**. Vælg **Næste**.

5. Acceptér **standardindstillingerne Gennemse og tilpas indstillingerne fra skabelonmarkering** , og vælg **Næste**.

6. Acceptér **standardindstillingerne for Beskyttelse-handlinger** , og vælg **Næste**.

7. Vælg **Overvågning, eller begræns aktiviteter Windows enheder**, og lad handlingerne være indstillet **til Kun overvågning**. Vælg **Næste**.

8. Acceptér den **standard, jeg gerne vil teste den for første værdi** , og **vælg Vis politiktip, mens jeg er i testtilstand**. Vælg **Næste**.

9. Gennemse dine indstillinger, og vælg **Send**.

10. Den nye DLP-politik vises på politiklisten.

11. Kontrollér Aktivitetsstifinder for data fra de overvågede slutpunkter. Angiv placeringsfilteret for enheder, og tilføj politikken, og filtrer derefter efter politiknavn for at se effekten af denne politik. Se [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md), hvis det er nødvendigt.

12. Forsøg at dele en test, der indeholder indhold, som udløser databetingelse for personidentificerbare oplysninger (PII) med en person uden for organisationen. Dette bør udløse politikken.

13. Kontrollér Aktivitetsstifinder for begivenheden.

### <a name="scenario-2-modify-the-existing-policy-set-an-alert"></a>Scenarie 2: Rediger den eksisterende politik, angiv en besked

1. Åbn siden [forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Vælg den **amerikanske politik for personidentificerbare oplysninger (PII), som** du oprettede i scenarie 1.

3. Vælg **Rediger politik**.

4. Gå til siden **med avancerede DLP-regler**, og rediger den registrerede lave mængde indhold amerikansk personligt **identificerbare oplysninger.**

5. Rul ned til **sektionen Hændelsesrapporter** , og **angiv Send en besked til administratorer, når en regel matcher til** **Til**. Mailbeskeder sendes automatisk til administratoren og alle andre, du føjer til listen over modtagere. 

   > [!div class="mx-imgBorder"]
   > ![turn-on-incident-reports.](../media/endpoint-dlp-2-using-dlp-incident-reports.png)
   
6. I dette scenarie skal du vælge **Send besked, hver gang en aktivitet svarer til reglen**.

7. Vælg **Gem**.

8. Behold alle dine tidligere indstillinger ved at **vælge Næste** og **derefter Sende** politikændringerne.

9. Forsøg at dele en test, der indeholder indhold, som udløser databetingelse for personidentificerbare oplysninger (PII) med en person uden for organisationen. Dette bør udløse politikken.

10. Kontrollér Aktivitetsstifinder for begivenheden.

### <a name="scenario-3-modify-the-existing-policy-block-the-action-with-allow-override"></a>Scenarie 3: Rediger den eksisterende politik, bloker handlingen med tillad tilsidesættelse

1. Åbn siden [forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Vælg den **amerikanske politik for personidentificerbare oplysninger (PII), som** du oprettede i scenarie 1.

3. Vælg **Rediger politik**.

4. Gå til siden **med avancerede DLP-regler**, og rediger den registrerede lave mængde indhold amerikansk personligt **identificerbare oplysninger.**

5. Rul ned til **afsnittet Overvågning eller begræns aktiviteter Windows enhed**, og for hver aktivitet skal den tilsvarende handling angives **til Bloker med tilsidesættelse**.

   > [!div class="mx-imgBorder"]
   > ![angiv blok med tilsidesættelseshandling.](../media/endpoint-dlp-6-using-dlp-set-blocked-with-override.png)
   
6. Vælg **Gem**.

7. Gentag trin 4-7 for den **store mængde indhold, der registreres af USA Personligt identificerbare inf**.

8. Behold alle dine tidligere indstillinger ved at **vælge Næste** og **derefter Sende** politikændringerne.

9. Forsøg at dele en test, der indeholder indhold, som udløser databetingelse for personidentificerbare oplysninger (PII) med en person uden for organisationen. Dette bør udløse politikken.

   Du får vist et pop op-vindue som dette på klientenhed:

   > [!div class="mx-imgBorder"]
   > ![endpoint dlp client blocked override notification.](../media/endpoint-dlp-3-using-dlp-client-blocked-override-notification.png)

10. Kontrollér Aktivitetsstifinder for begivenheden.

### <a name="scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview"></a>Scenarie 4: Undgå at gentage DLP-meddelelser fra skysynkroniseringsapps med automatisk karantæne (forhåndsvisning)

#### <a name="before-you-begin"></a>Før du begynder

I dette scenarie blokeres synkronisering af filer med **etiketten Meget** fortroligt følsomhed OneDrive filer. Dette er et komplekst scenarie med flere komponenter og procedurer. Du skal bruge:

- En AAD-brugerkonto at målrette mod og en onboardet Windows 10-computer, der allerede synkroniserer en lokal OneDrive-mappe med OneDrive-lagerplads i skyen.
- Microsoft Word installeret på destinationscomputeren Windows 10 computeren
- Følsomhedsmærkater konfigureret og publiceret – [se Introduktion til følsomhedsmærkater](get-started-with-sensitivity-labels.md#get-started-with-sensitivity-labels) [og Opret og konfigurer følsomhedsmærkater og deres politikker](create-sensitivity-labels.md#create-and-configure-sensitivity-labels-and-their-policies).

Der er tre procedurer.

1. Konfigurer indstillingerne for den automatiske DLP-karantæne for Slutpunkt.
2. Opret en politik, der blokerer følsomme elementer, der har **etiketten Meget fortroligt** følsomhed.
3. Opret et Word-dokument på Windows 10-enhed, som politikken er målrettet til, anvend etiketten, og kopiér det til brugerkontienes lokale OneDrive mappe, der synkroniseres.  

#### <a name="configure-endpoint-dlp-unallowed-app-and-auto-quarantine-settings"></a>Konfigurere indstillinger for ikke-tilladt slutpunkt for app og automatisk karantæne

1. Åbn [DLP-indstillinger for Slutpunkt](https://compliance.microsoft.com/datalossprevention?viewid=globalsettings)

2. **Udvid Ikke-tilladte apps**.

3. Vælg **Tilføj eller** rediger ikke-tilladte apps, og tilføj *OneDrive* som vist navn og det eksekverbare navn *onedrive.exefor ikke* at tillade onedrive.exe at få adgang til elementer med navnet Meget **fortroligt.**

4. Vælg **Automatisk karantæne og** **Gem**.

5. Under **Indstillinger for automatisk karantæne skal** du **vælge Rediger indstillinger for automatisk karantæne**.

6. **Aktivér automatisk karantæne for ikke-tilladte apps**.

7. Angiv stien til mappen på lokale computere, hvor du vil flytte de oprindelige følsomme filer til. Eksempel:
   
    **'%homedrive%%homepath%\Microsoft DLP\Quarantine'** for brugernavnet *Isaaka langer* placerer de flyttede elementer i en mappe med navnet:  

    *C:\Users\Isaæder\Microsoft DLP\Quarantine\OneDrive*

    og føje et dato- og tidsstempel til det oprindelige filnavn.
    
    > [!NOTE]
    > DLP Auto-karantæne opretter undermapper for filerne for hver app, der ikke er tilladt. Så hvis du har både *Notesblok* *og OneDrive* på listen over ikke-tilladte apps, oprettes der en undermappe til **\OneDrive** og en anden undermappe til **\Notesblok**.

8. Vælg **Erstat filerne med en .txt,** der indeholder følgende tekst, og skriv den ønskede tekst i pladsholderfilen. Eksempel: for en fil med *navnet 1.docx*:
    
    > %%FileName%% indeholder følsomme oplysninger, som din organisation beskytter med DLP-politikken (forebyggelse af datatab), %%PolicyName%%, og er blevet flyttet til karantænemappen: %%QuarantinePath%%
    
    en tekstfil, der indeholder denne meddelelse:
    
    > Automatisk kvartil 1.docx indeholder følsomme oplysninger, som din organisation beskytter med politikken til forebyggelse af datatab (DLP) og er blevet flyttet til karantænemappen: C:\Users\Isachet\Microsoft DLP\Quarantine\OneDrive\auto quar 1_20210728_151541.docx.

9. Vælg **Gem**

#### <a name="configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential"></a>Konfigurer en politik til at OneDrive synkronisering af filer med følsomhedsmærkatet Meget fortroligt

1. Åbn siden [forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Vælg **Opret politik**.

3. I dette scenarie skal du **vælge Brugerdefineret**, **derefter Brugerdefineret politik** og vælge **Næste**.

4. Udfyld felterne Navn **og** **Beskrivelse,** og vælg **Næste**.

5. Slå feltet **Status fra** for alle placeringer undtagen **Enheder**. Hvis du har en bestemt slutbrugerkonto, du vil teste denne fra, skal du sørge for at markere den i området. Vælg **Næste**.

6. Acceptér **standardindstillingen Opret eller tilpas avancerede DLP-regler,** og vælg **Næste**.

7. Opret en regel med disse værdier:
    1. **Navn** >  *Scenarie 4 Automatisk karantæne*.
    1. **Betingelser** >  **Indhold indeholder** >  **Følsomhedsmærkater** >  **Meget fortroligt**.
    1.  **Handlinger** >  **Overhold eller begræns aktiviteter på Windows** >  **enhederAccess ved ikke-tilladte** **appsBlokering** > . I dette scenarie skal du rydde alle de andre aktiviteter.
    1. **Brugerbeskeder** >  **Til**.
    1. **Slutpunktsenheder skal >** Vis brugere **en besked med et politiktip, når en aktivitet ikke** allerede er aktiveret.
    
8. Vælg **Gem** og **Næste**.

9. Vælg **Slå det til med det samme**. Vælg **Næste**.

10. Gennemse dine indstillinger, og vælg **Send**.

    > [!NOTE]
    > Det kan være mindst en time, før den nye politik replikeres og anvendes på den Windows 10 computer.

11. Den nye DLP-politik vises på politiklisten.

#### <a name="test-auto-quarantine-on-the-windows-10-device"></a>Test automatisk karantæne på Windows 10 enhed

1. Log på Windows 10-computeren med den brugerkonto, du angav i Konfigurer en politik for at blokere [OneDrive](#configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential) synkronisering af filer med følsomhedsmærkatet Meget fortroligt trin 5.

2. Opret en mappe, hvis indhold ikke synkroniseres OneDrive. Eksempel:

    *C:\auto-quarantine source folder*

3. Åbn Microsoft Word og opret en fil i mappen med kildekilden automatisk i karantæne. Anvende **etiketten Meget fortroligt** følsomhed. se [Anvend følsomhedsetiketter på dine filer og mails i Office](https://support.microsoft.com/topic/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

4. Kopiér den fil, du lige har oprettet, OneDrive din synkroniseringsmappe. Der vises nu en toastbesked om, at handlingen ikke er tilladt, og at filen er sat i karantæne. For brugernavnet *Isa hele Langer* og et dokument med titlen automatisk karantæne på dokument, *1.docx* får du vist denne meddelelse:

    ![Pop op-vindue til forebyggelse af datatab med en besked om, at OneDrive synkronisering ikke er tilladt for den angivne fil, og at filen skal være i karantæne.](../media/auto-quarantine-user-notification-toast.png)
    
    Meddelelsen læses op:
    
    > Det er ikke tilladt at åbne 1.docx dokument med denne app. Filen er sat i karantæne til 'C:\Users\Isalager\Microsoft DLP\OneDrive'

5. Vælg **Afvis**.

6. Åbn tekstfilen med pladsholderen. Det navngives **automatisk karantæne på dokument 1.docx_ *date_time*.txt**. 

7. Åbn karantænemappen, og bekræft, at den oprindelige fil findes der.
 
8. Kontrollér Aktivitetsstifinder for data fra de overvågede slutpunkter. Angiv placeringsfilteret for enheder, og tilføj politikken, og filtrer derefter efter politiknavn for at se effekten af denne politik. Se [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md), hvis det er nødvendigt.

9. Kontrollér Aktivitetsstifinder for begivenheden.

## <a name="see-also"></a>Se også

- [Få mere at vide om forebyggelse af datatab på slutpunkt](endpoint-dlp-learn-about.md)
- [Kom i gang med forebyggelse af datatab på slutpunkt](endpoint-dlp-getting-started.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md)
- [Microsoft Defender til Slutpunkt](/windows/security/threat-protection/)
- [Onboard Windows 10 og Windows 11 enheder i Microsoft 365 oversigt](/microsoft-365/compliance/device-onboarding-overview)
- [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure Active Directory (AAD) tilmeldt](/azure/active-directory/devices/concept-azure-ad-join)
- [Download den nye Microsoft Edge baseret på Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
- [Introduktion til DLP-standardpolitikken](get-started-with-the-default-dlp-policy.md)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
