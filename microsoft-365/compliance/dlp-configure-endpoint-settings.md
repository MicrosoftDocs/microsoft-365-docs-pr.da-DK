---
title: Konfigurer DLP-indstillinger for slutpunkt
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
description: Få mere at vide om, hvordan du konfigurerer centrale indstillinger for forebyggelse af datatab for slutpunkter (DLP).
ms.openlocfilehash: f76f6ec18464229fa50ad54a06fc7969abb3dd23
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64952814"
---
# <a name="configure-endpoint-data-loss-prevention-settings"></a>Konfigurer indstillinger for forebyggelse af datatab ved slutpunkt

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Mange aspekter af DLP-funktionsmåden (Endpoint Data Loss Prevention) styres af centralt konfigurerede indstillinger. Indstillinger anvendes på alle DLP-politikker for enheder.

![DLP-indstillinger for slutpunkt](../media/endpoint-dlp-1-using-dlp-settings.png)

Du skal konfigurere disse indstillinger, hvis du vil styre:

- Begrænsninger for udgående sky
- Forskellige typer restriktive handlinger på brugeraktiviteter pr. program.
- Udeladelser af filstier for Windows- og macOS-enheder.
- Begrænsninger for browser og domæne.
- Sådan vises forretningsberettigelser for tilsidesættelse af politikker i politiktip.
- Hvis aktiviteter på Office-, PDF- og CSV-filer overvåges automatisk.

## <a name="dlp-settings"></a>DLP-indstillinger

Før du går i gang, skal du konfigurere dine DLP-indstillinger. 

### <a name="endpoint-dlp-windows-1011-and-macos-settings"></a>DLP-Windows 10/11- og macOS-indstillinger for slutpunkt

|Indstilling |Windows 10, 1809 og nyere Windows 11  |macOS Catalina 10.15 eller nyere |Bemærkninger  |
|---------|---------|---------|---------|
|Udeladelser af filsti     |Understøttes         |Understøttes         |macOS indeholder en anbefalet liste over undtagelser, der er slået til som standard          |
|Begrænsede apps     |Understøttes         |Understøttes         |         |
|Begrænsede appgrupper |Understøttes |Understøttes ikke
|Ikke-tilladte Bluetooth apps    |Understøttes         |Understøttes ikke         |         |
|Browser- og domænebegrænsninger for følsomme elementer      |Understøttes         |Understøttes         |         |
|Yderligere indstillinger for Slutpunkt DLP     |Understøttes         |Understøttes         |Kun forretningsjusteringer, der er standard, understøttes for macOS-enheder         |
|Overvåg altid filaktivitet for enheder     |Understøttes         |Understøttes         |         |
|Sæt automatisk fil i karantæne fra ikke-tilladte apps | Understøttes | Understøttes ikke| |
|Avanceret klassificering | Understøttes | Understøttes ikke| |
|Forretningsberettigelse i tip til politik | Understøttes | Understøttes| |

### <a name="advanced-classification-scanning-and-protection"></a>Avanceret klassificeringsscanning og -beskyttelse

Avanceret klassificeringsscanning og -beskyttelse gør det muligt for den mere avancerede cloudbaserede Microsoft Purview-dataklassificeringstjeneste at scanne elementer, klassificere dem og returnere resultaterne til den lokale computer. Det betyder, at du kan drage fordel af klassificeringsteknikker som [nøjagtig datamatchklassificering](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md) , [navngivne enheder](named-entities-learn.md) og [klassificeringer, der kan oplæres](classifier-learn-about.md) , i dine DLP-politikker.

Når avanceret klassificering er slået til, sendes indhold fra den lokale enhed til cloudtjenesterne med henblik på scanning og klassificering. Hvis båndbreddeudnyttelsen er et problem, kan du angive en grænse for, hvor meget der kan bruges i en rullende 24-timers periode. Grænsen er konfigureret i Endpoint DLP-indstillinger og anvendes pr. enhed. Hvis du angiver en forbrugsgrænse for båndbredde, og den overskrides, holder DLP op med at sende brugerindholdet til cloudmiljøet. På dette tidspunkt fortsætter dataklassificeringen lokalt på enheden, men klassificering ved hjælp af præcise datamatch, navngivne enheder og klassificeringer, der kan oplæres, er ikke tilgængelige. Når den akkumulerede båndbreddeforbrug falder til under grænsen for rullende 24 timer, genoptages kommunikationen med cloudtjenesterne.

Hvis båndbreddeudnyttelsen ikke er et problem, skal du vælge **Ingen grænse** for at tillade ubegrænset båndbreddeudnyttelse.

Disse Windows versioner understøtter avanceret klassificeringsscanning og -beskyttelse:

- Windows 10 version 20H1/20H2/21H1 (KB 5006738)
- Windows 10 version 19H1/19H2 (KB 5007189)
- Windows 10 RS5 (KB 5006744)

> [!NOTE]
> Understøttelse af avanceret klassificering er tilgængelig for filtyperne Office (Word, Excel, PowerPoint) og PDF.

> [!NOTE]
> DLP-politikevaluering forekommer altid i cloudmiljøet, selvom brugerindhold ikke sendes.

### <a name="file-path-exclusions"></a>Udeladelser af filsti

Åbn [Microsoft Purview-overholdelsesportalDatatabforebyggelseEndpoint](https://compliance.microsoft.com) >  >  **DLP-indstillingerFilstiudeladelser** > .

Det kan være en god idé at udelukke bestemte stier fra DLP-overvågning, DLP-advarsler og gennemtvingelse af DLP-politik på dine enheder, fordi de er for støjende eller ikke indeholder filer, du er interesseret i. Filer på disse placeringer overvåges ikke, og filer, der er oprettet eller ændret på disse placeringer, er ikke underlagt gennemtvingelse af DLP-politik. Du kan konfigurere stiudeladelser i DLP-indstillinger.

#### <a name="windows-10-devices"></a>Windows 10 enheder

Du kan bruge denne logik til at konstruere dine udeladelsesstier til Windows 10 enheder:

- Gyldig filsti, der slutter med `\`, hvilket kun betyder filer direkte under mappen . <br/>For eksempel: `C:\Temp\`

- Gyldig filsti, der slutter med `\*`, hvilket betyder, at det kun er filer under undermapper ud over filerne direkte under -mappen. <br/>For eksempel: `C:\Temp\*`

- Gyldig filsti, der slutter uden `\` eller `\*`, hvilket betyder alle filer direkte under mappen og alle undermapper. <br/>For eksempel: `C:\Temp`

- En sti med jokertegn mellem `\` fra hver side. <br/>For eksempel: `C:\Users\*\Desktop\`

- En sti med jokertegn mellem `\` fra hver side og med `(number)` for at give det nøjagtige antal undermapper. <br/>For eksempel: `C:\Users\*(1)\Downloads\`

- En sti med SYSTEM-miljøvariabler. <br/>For eksempel: `%SystemDrive%\Test\*`

- En blanding af alt det ovenstående. <br/>For eksempel: `%SystemDrive%\Users\*\Documents\*(2)\Sub\`

#### <a name="macos-devices"></a>macOS-enheder

På samme måde som med Windows 10 enheder kan du tilføje dine egne undtagelser for macOS-enheder.

- Der skelnes ikke mellem store og små bogstaver i definitioner af filstier, og `User` det er det samme som `user`.

- Jokertegnværdier understøttes. En stidefinition kan derfor indeholde en `*` midt i stien eller i slutningen af stien. For eksempel: `/Users/*/Library/Application Support/Microsoft/Teams/*`

#####  <a name="recommended-file-path-exclusions-preview"></a>Anbefalede udeladelser af filstier (prøveversion)

Af hensyn til ydeevnen indeholder Endpoint DLP en liste over anbefalede undtagelser for filstier til macOS-enheder. Disse undtagelser er som standard slået til. Du kan deaktivere dem, hvis du vil, ved at slå **indstillingen Medtag anbefalede filstiudeladelser for Mac til** /fra. Listen indeholder:

- /Applications/*
- /System/*
- /usr/*
- /Library/*
- /private/*
- /opt/*
- /Users/*/Library/Application Support/Microsoft/Teams/*

### <a name="restricted-apps-and-app-groups"></a>Begrænsede apps og appgrupper

#### <a name="restricted-apps"></a>Begrænsede apps

**Begrænsede apps** (tidligere kaldet **Ikke-tilladte apps**) er en liste over programmer, du opretter. Du kan konfigurere, hvilke handlinger DLP skal udføre, når en bruger bruger en app på listen til at **_få adgang til_** en DLP-beskyttet fil på en enhed. Den er tilgængelig til Windows 10- og macOS-enheder.

Når **Adgang fra begrænsede apps** er valgt i en politik, og en bruger bruger en app, der findes på listen over begrænsede apps, til at få adgang til en beskyttet fil, vil aktiviteten være `audited`, `blocked`eller `blocked with override` afhængigt af hvordan du har konfigureret den. Det betyder, at medmindre den samme app er medlem af en **begrænset appgruppe**, tilsidesætter de handlinger, der er konfigureret for aktiviteter i **gruppen Begrænset app** , de handlinger, der er konfigureret for adgangsaktiviteten for listen **Begrænsede apps** . Al aktivitet overvåges og kan gennemses i Aktivitetsoversigt.

> [!IMPORTANT]
> Medtag ikke stien til den eksekverbare fil, men kun navnet på den eksekverbare fil (f.eks. browser.exe).

> [!IMPORTANT]
> Den handling (`audit`, `block with override`eller `block`), der er defineret for apps, der er på listen over begrænsede apps, gælder kun, når en bruger forsøger at ***få adgang til*** et beskyttet element. 

#### <a name="file-activities-for-apps-in-restricted-app-groups-preview"></a>Filaktiviteter for apps i begrænsede appgrupper (prøveversion)

Begrænsede appgrupper er samlinger af apps, som du opretter under DLP-indstillinger og derefter føjer til en regel i en politik. Når du føjer en begrænset appgruppe til en politik, kan du udføre de handlinger, der er defineret i denne tabel.

|Indstillingen Begrænset appgruppe  |Hvad det giver dig mulighed for at gøre  |
|---------|---------|
|Begræns ikke filaktivitet     |Fortæller DLP, at brugerne skal have adgang til DLP-beskyttede elementer ved hjælp af apps i appgruppen og ikke foretager sig noget, når brugeren forsøger at **kopiere til Udklipsholder**, **Kopiere til et flytbart USB-drev**, **Kopiere til et netværksdrev** og **Udskrive** fra appen.          |
|Anvend en begrænsning på alle aktiviteter     |Fortæller DLP til `Audit only`, `Block with override`, eller `Block` når en bruger forsøger at få adgang til et DLP-beskyttet element ved hjælp af en app, der er i denne appgruppe         |
|Anvend begrænsninger på en bestemt aktivitet     |Denne indstilling giver en bruger adgang til et DLP-beskyttet element ved hjælp af en app, der er i appgruppen, og giver dig mulighed for at vælge en standardhandling (`Audit only`, eller `Block with override`), som DLP skal tage, `Block`når en bruger forsøger at **kopiere til Udklipsholder**, **kopiere til et flytbart USB-drev**, **kopiere til et netværksdrev** og **udskrive**.          |

> [!IMPORTANT]
> Indstillinger i en begrænset appgruppe tilsidesætter alle begrænsninger, der er angivet på listen over begrænsede apps, når de er i den samme regel. Så hvis en app er på listen over begrænsede apps og er medlem af en gruppe med begrænsede apps, anvendes indstillingerne for gruppen begrænsede apps.

#### <a name="how-dlp-applies-restrictions-to-activities"></a>Sådan anvender DLP begrænsninger for aktiviteter

Interaktioner mellem **filaktiviteter for apps i begrænsede appgrupper (prøveversion),** **Filaktiviteter for alle apps** og listen **Begrænsede appaktiviteter** er begrænset til den samme regel.

##### <a name="restricted-app-groups-overrides"></a>Tilsidesættelser af begrænsede appgrupper

Konfigurationer, der er defineret i **Filaktiviteter for apps i begrænsede appgrupper (prøveversion),** tilsidesætter konfigurationerne på listen **Begrænsede appaktiviteter** og **Filaktiviteter for alle apps** i den samme regel.

##### <a name="restricted-app-activities-and-file-activities-for-all-apps"></a>Begrænsede appaktiviteter og filaktiviteter for alle apps

Konfigurationerne af **Aktiviteter med begrænsede apps** og **Filaktiviteter for alle apps** fungerer i fællesskab, hvis den handling, der er defineret for **Aktiviteter med begrænsede apps** , enten `Audit only`er eller `Block with override` i den samme regel. Det skyldes, at handlinger, der er defineret for **begrænsede appaktiviteter** , kun gælder, når en bruger tilgår en fil ved hjælp af en app, der er på listen. Når brugeren har adgang, gælder de handlinger, der er defineret for aktiviteter i **Filaktiviteter for alle apps** . 

Her er et eksempel:

Hvis Notepad.exe føjes til **Begrænsede apps** , og **Filaktiviteter for alle apps** er konfigureret til at **anvende begrænsninger på bestemte aktiviteter,** og begge er konfigureret på følgende måde:

|Indstilling i politik  |Appnavn  |Brugeraktivitet  |DLP-handling, der skal udføres  |
|---------|---------|---------|---------|
|Begrænsede appaktiviteter     |Notesblok        |Få adgang til et DLP-beskyttet element         |Kun overvågning         |
|Filaktiviteter for alle apps   |Alle apps        | Kopiér til Udklipsholder        |Kun overvågning         |
|Filaktiviteter for alle apps     |Alle apps         |Kopiér til en enhed, der kan fjernes fra USB | Bloker       |
|Filaktiviteter for alle apps     |Alle apps         |Kopiér til et netværksshare         |Kun overvågning         |
|Filaktiviteter for alle apps   |Alle apps         |Udskrive         |Bloker         |
|Filaktiviteter for alle apps     |Alle apps         |Kopiér eller flyt ved hjælp af ikke-tilladte Bluetooth app         |Blokeret         |
|Filaktiviteter for alle apps     |Alle apps         |Fjernskrivebord-tjenester         |Blok med tilsidesættelse         |

Bruger A åbner en DLP-beskyttet fil ved hjælp af Notesblok. DLP giver adgang til og overvåger aktiviteten. Mens bruger A stadig er i Notesblok og derefter forsøger at kopiere til Udklipsholder fra det beskyttede element, fungerer dette, og DLP overvåger aktiviteten. Bruger A forsøger derefter at udskrive det beskyttede element fra Notesblok, og aktiviteten er blokeret.

> [!NOTE]
> Når den DLP-handling, der skal udføres i **Begrænsede appaktiviteter** , er angivet til `block`, blokeres al adgang, og brugeren kan ikke udføre nogen aktiviteter på filen.
   
##### <a name="file-activities-for-all-apps-only"></a>Filaktiviteter kun for alle apps

Hvis en app ikke er i **Filaktiviteter for apps i begrænsede appgrupper (prøveversion)** eller ikke er på listen **Begrænsede appaktiviteter** eller er på listen **Begrænsede appaktiviteter** med handlingen `Audit only`, eller 'Bloker med tilsidesættelse', anvendes alle begrænsninger, der er defineret i **Filaktiviteter for alle apps** , i den samme regel.  

#### <a name="macos-devices"></a>macOS-enheder

På samme måde som på Windows enheder kan du nu forhindre macOS-apps i at få adgang til følsomme data ved at definere dem på listen **Begrænsede appaktiviteter**. 

> [!NOTE]
> Bemærk, at apps på tværs af platforme skal angives med deres unikke stier for det operativsystem, de kører på.

Sådan finder du hele stien til Mac-apps:

1. Åbn **Aktivitetsovervågning** på macOS-enheden. Find og dobbeltklik på den proces, du vil begrænse

2. Vælg fanen **Åbn filer og porte** .
  
3. I forbindelse med macOS-apps skal du have det fulde stinavn, herunder navnet på appen.

#### <a name="protect-sensitive-data-from-cloud-synchronization-apps"></a>Beskyt følsomme data mod cloudsynkroniseringsapps

Hvis du vil forhindre, at følsomme elementer synkroniseres til cloudmiljøet ved hjælp af cloudsynkroniseringsapps, *f.eks.onedrive.exe*, skal du føje cloudsynkroniseringsappen til listen **Ikke-tilladte apps** . Når en ikke-tilladt skysynkroniseringsapp forsøger at få adgang til et element, der er beskyttet af en blokerende DLP-politik, kan DLP generere gentagne meddelelser. Du kan undgå disse gentagne meddelelser ved at aktivere indstillingen **Automatisk karantæne** under **Ikke-tilladte apps**.  

##### <a name="auto-quarantine-preview"></a>Sæt automatisk karantæne (prøveversion)

> [!NOTE]
> Automatisk karantæne understøttes kun i Windows 10

Når indstillingen er aktiveret, aktiveres Automatisk karantæne, når en ikke-tilladt app forsøger at få adgang til et DLP-beskyttet følsomt element. Automatisk karantæne flytter det følsomme element til en administratorkonfigureret mappe og kan efterlade en pladsholder **.txt** fil i stedet for originalen. Du kan konfigurere teksten i pladsholderfilen for at fortælle brugerne, hvor elementet blev flyttet til, og andre relevante oplysninger.  

Du kan bruge automatisk karantæne til at forhindre en endeløs kæde af DLP-meddelelser for brugeren og administratorer – se [scenarie 4: Undgå at løkke DLP-meddelelser fra cloudsynkroniseringsapps med automatisk karantæne (prøveversion)](endpoint-dlp-using.md#scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview).

### <a name="unallowed-bluetooth-apps"></a>Ikke-tilladte Bluetooth apps

Undgå, at personer overfører filer, der er beskyttet af dine politikker, via bestemte Bluetooth apps.

### <a name="browser-and-domain-restrictions-to-sensitive-data"></a>Begrænsninger for browser og domæne for følsomme data

Begræns følsomme filer, der matcher dine politikker, fra at blive delt med uindskrænket domæner for cloudtjenester.

#### <a name="unallowed-browsers"></a>Ikke-tilladte browsere

For Windows enheder, du tilføjer browsere, der identificeres af deres eksekverbare navne, blokeres det fra at få adgang til filer, der opfylder betingelserne for en gennemtvunget DLP-politik, hvor begrænsningen for upload til cloudtjenester er indstillet til at blokere eller blokere tilsidesættelse. Når disse browsere er blokeret, så de ikke kan få adgang til en fil, får slutbrugerne vist en toastbesked, hvor de bliver bedt om at åbne filen via Microsoft Edge.

For macOS-enheder skal du tilføje den fulde filsti. Sådan finder du hele stien til Mac-apps:

1. Åbn **Aktivitetsovervågning** på macOS-enheden. Find og dobbeltklik på den proces, du vil begrænse

2. Vælg fanen **Åbn filer og porte** .
  
3. I forbindelse med macOS-apps skal du have det fulde stinavn, herunder navnet på appen.

#### <a name="service-domains"></a>Tjenestedomæner

> [!NOTE]
> Indstillingen **Tjenestedomæner** gælder kun for filer, der uploades ved hjælp af Microsoft Edge eller Google Chrome, hvor [Microsoft Purview-udvidelsen er](dlp-chrome-learn-about.md#learn-about-the-microsoft-purview-extension) installeret.

Du kan styre, om følsomme filer, der er beskyttet af dine politikker, kan overføres til bestemte tjenestedomæner fra Microsoft Edge.

Hvis listetilstanden er angivet til **Bloker**, kan brugeren ikke overføre følsomme elementer til disse domæner. Når en uploadhandling blokeres, fordi et element stemmer overens med en DLP-politik, genererer DLP enten en advarsel eller blokerer upload af det følsomme element.

Hvis listetilstanden er angivet til **Tillad**, kan brugerne **_kun_** overføre følsomme elementer til disse domæner, og uploadadgang til alle andre domæner er ikke tilladt.

> [!IMPORTANT]
> Når tjenestebegrænsningstilstanden er angivet til "Tillad", skal du have konfigureret mindst ét tjenestedomæne, før begrænsninger gennemtvinges.

Brug FQDN-formatet for tjenestedomænet uden at afslutte `.` 

Eksempel:

 `www.contoso.com` 

Jokertegn understøttes ikke.

### <a name="additional-settings-for-endpoint-dlp"></a>Yderligere indstillinger for slutpunkt DLP

#### <a name="business-justification-in-policy-tips"></a>Forretningsberettigelse i tip til politik

Du kan styre, hvordan brugerne interagerer med indstillingen for forretningsberettigelse i meddelelser om tip til DLP-politik. Denne indstilling vises, når brugerne udfører en aktivitet, der er beskyttet af indstillingen **Bloker med tilsidesættelse** i en DLP-politik. Dette er en global indstilling. Du kan vælge mellem en af følgende muligheder:

- **Vis standardindstillinger og brugerdefinerede tekstfelter**: Som standard kan brugerne vælge enten en indbygget begrundelse eller indtaste deres egen tekst.
- **Vis kun standardindstillinger**: Brugerne kan kun vælge en indbygget begrundelse.
- **Vis kun brugerdefineret tekstfelt**: Brugerne kan kun angive deres egen begrundelse. Det er kun tekstfeltet, der vises i meddelelsen med tip til slutbrugerpolitikken. 

##### <a name="customizing-the-options-in-the-drop-down-menu"></a>Tilpasning af indstillingerne i rullemenuen

Du kan oprette op til fem brugerdefinerede indstillinger, der vises, når brugerne interagerer med tip til politikmeddelelser ved at vælge **rullemenuen Tilpas indstillingerne**. 


|Mulighed |Standardtekst  |
|---------|---------|
|mulighed 1    | **Dette er en del af en etableret forretningsarbejdsproces**  , eller du kan angive brugerdefineret tekst        |
|mulighed 2  |**Min chef har godkendt denne handling** , eller du kan angive brugerdefineret tekst         |
|mulighed 3   |**Der kræves hurtig adgang. Jeg giver min chef besked separat** , eller du kan indtaste tilpasset tekst          |
|Vis falsk positiv indstilling     |**Oplysningerne i disse filer er ikke følsomme** , eller du kan indtaste tilpasset tekst          |
|mulighed 5    |**Andet** , eller du kan indtaste brugerdefineret tekst         |

### <a name="always-audit-file-activity-for-devices"></a>Overvåg altid filaktivitet for enheder

Når enheder onboardes, overvåges aktivitet for Office-, PDF- og CSV-filer som standard automatisk og kan gennemses i Aktivitetsoversigt. Slå denne funktion fra, hvis du kun vil overvåge denne aktivitet, når onboardede enheder er inkluderet i en aktiv politik.

Filaktivitet overvåges altid for onboardede enheder, uanset om de er inkluderet i en aktiv politik.

## <a name="see-also"></a>Se også

- [Få mere at vide om forebyggelse af datatab ved slutpunkt](endpoint-dlp-learn-about.md)
- [Kom i gang med forebyggelse af datatab forebyggelse af datatab ved slutpunkt](endpoint-dlp-getting-started.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Kom i gang med Aktivitetsoversigt](data-classification-activity-explorer.md)
- [Microsoft Defender for Endpoint](/windows/security/threat-protection/)
- [Oversigt over onboarding af Windows 10 og Windows 11 enheder i Microsoft Purview](/microsoft-365/compliance/device-onboarding-overview)
- [Microsoft 365 abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure Active Directory (AAD) er tilmeldt](/azure/active-directory/devices/concept-azure-ad-join)
- [Download den nye Microsoft Edge baseret på Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
- [Kom i gang med DLP-standardpolitikken](get-started-with-the-default-dlp-policy.md)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
