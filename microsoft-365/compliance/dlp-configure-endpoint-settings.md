---
title: Konfigurere indstillinger for forebyggelse af datatab på slutpunkt
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
description: Få mere at vide om, hvordan du konfigurerer de centrale indstillinger for forebyggelse af datatab på slutpunkter (DLP).
ms.openlocfilehash: ebe995512769275999e7ec4837e16542ffce7100
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63705685"
---
# <a name="configure-endpoint-data-loss-prevention-settings"></a>Konfigurere indstillinger for forebyggelse af datatab på slutpunkt

Mange aspekter af forebyggelse af datatab på slutpunkter (DLP) styres af centralt konfigurerede indstillinger. Indstillinger anvendes på alle DLP-politikker for enheder.

![Slutpunkt DLP-indstillinger](../media/endpoint-dlp-1-using-dlp-settings.png)

Du skal konfigurere disse indstillinger, hvis du vil styre:

- Begrænsninger for skybaseret udgangspunkt
- Forskellige typer restriktive handlinger for brugeraktiviteter pr. program.
- Udeladelse af filstier for Windows- og macOS-enheder.
- Browser- og domænebegrænsninger.
- Sådan vises forretningsberettigelse til tilsidesættelse af politikker i politiktip.
- Hvis aktiviteter på Office, PDF- og CSV-filer, overvåges automatisk.

## <a name="dlp-settings"></a>DLP-indstillinger

Før du går i gang, skal du konfigurere dine DLP-indstillinger. 

### <a name="endpoint-dlp-windows-1011-and-macos-settings"></a>Slutpunkt DLP-Windows 10/11 og macOS-indstillinger

|Indstilling |Windows 10, 1809 og nyere, Windows 11  |macOS Catalina 10.15 eller nyere (forhåndsvisning)  |Bemærkninger  |
|---------|---------|---------|---------|
|Udeladelse af filsti     |Understøttet         |Understøttet         |macOS indeholder en anbefalet liste over udeladelsesindstillinger, der er til som standard          |
|Begrænsede apps     |Understøttet         |Understøttet         |         |
|Begrænsede appgrupper |Understøttet |Understøttes ikke
|Ikke tilladt Bluetooth apps    |Understøttet         |Understøttes ikke         |         |
|Browser- og domænebegrænsninger for følsomme elementer      |Understøttet         |Understøttet         |         |
|Yderligere indstillinger for Slutpunkt DLP     |Understøttet         |Understøttet         |Kun virksomhedens standardberettigelse understøttes for macOS-enheder         |
|Altid overvåge filaktivitet for enheder     |Understøttet         |Understøttet         |         |
|Automatisk karantæne af fil fra ikke-tilladte apps | Understøttet | Understøttes ikke| |
|Avanceret klassificering | Understøttet | Understøttes ikke| |
|Forretningsberettigelse i politiktip | Understøttet | Understøttet| |

### <a name="advanced-classification-scanning-and-protection"></a>Avanceret scanning og beskyttelse af klassificering

Avanceret scanning og beskyttelse af klassificering giver den mere avancerede Microsoft 365 skybaserede dataklassificeringstjeneste til at scanne elementer, klassificere dem og returnere resultaterne til den lokale computer. Det betyder, at du kan drage fordel af klassificeringsteknikker som f.eks. klassificering af dataoverensstemmelse, navngivne enheder ([forhåndsvisning](classifier-learn-about.md#learn-about-trainable-classifiers)[)](named-entities-learn.md#learn-about-named-entities-preview) og trænbare klassificeringer i dine DLP-politikker.[](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md)

Når avanceret klassificering er slået til, sendes indhold fra den lokale enhed til skytjenesterne til scanning og klassificering. Hvis udnyttelse af båndbredde er et problem, kan du angive en grænse for, hvor meget der kan bruges i en rullende 24-timers periode. Grænsen konfigureres i Slutpunkt DLP-indstillinger og anvendes pr. enhed. Hvis du angiver en begrænsning for udnyttelse af båndbredde, og den overskrides, stopper DLP med at sende brugerens indhold til skyen. På dette tidspunkt fortsætter dataklassificering lokalt på enheden, men klassificering ved hjælp af nøjagtigt datamatching, navngivne enheder (eksempel) og trænbare klassificeringer er ikke tilgængelige. Når den akkumulerede båndbreddeudnyttelse falder under den rullende 24-timers grænse, genoptages kommunikationen med skytjenesterne.

Hvis udnyttelse af båndbredde ikke er et problem, skal du vælge **Ingen grænse for** at tillade ubegrænset brug af båndbredde.

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

Det kan være en god ide at udelukke bestemte stier fra DLP-overvågning, DLP-påmindelse og DLP-politik på dine enheder, fordi de er for støjende eller ikke indeholder filer, du er interesseret i. Filer på disse placeringer overvåges ikke, og alle filer, der oprettes eller ændres på disse placeringer, vil ikke blive underlagt håndhævelse af DLP-politikken. Du kan konfigurere udeladelse af stier i DLP-indstillinger.

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

### <a name="restricted-apps-and-app-groups"></a>Begrænsede apps og appgrupper

#### <a name="restricted-apps"></a>Begrænsede apps

**Begrænsede apps** (tidligere kaldet **ikke-tilladte apps**) er en liste over programmer, du opretter. Du konfigurerer, hvilke handlinger DLP skal udføre, når en bruger en app på listen til **_at få adgang_** til en DLP-beskyttet fil på en enhed. Den er tilgængelig til Windows 10 macOS-enheder (forhåndsvisning).

Når **Adgang** ved begrænsede apps er valgt i en politik, og en bruger en app, der er på listen begrænsede apps til at få adgang til en beskyttet fil, `audited`vil aktiviteten være , `blocked with override` `blocked`eller afhængigt af hvordan du har konfigureret den. Det vil sige, at medmindre den samme app er medlem af en begrænset **appgruppe**, så tilsidesætter de handlinger, der er konfigureret for aktiviteter i gruppen Begrænset **app** de handlinger, der er konfigureret til adgangsaktiviteten for listen Begrænsede **apps** . Alle aktiviteter overvåges og kan gennemses i Aktivitetsoversigt.

> [!IMPORTANT]
> Medtag ikke stien til den eksekverbare, men kun det eksekverbare navn (f.eksbrowser.exe).

> [!IMPORTANT]
> Handlingen (, eller`audit` ) defineret `block`for apps, der er på listen over begrænsede apps, gælder kun, `block with override`når en bruger forsøger at få adgang ***til*** et beskyttet element. 

#### <a name="file-activities-for-apps-in-restricted-app-groups-preview"></a>Filaktiviteter for apps i begrænsede appgrupper (forhåndsvisning)

Begrænsede appgrupper er grupper af apps, som du opretter i DLP-indstillinger og derefter føjer til en regel i en politik. Når du føjer en begrænset appgruppe til en politik, kan du udføre de handlinger, der er defineret i denne tabel.

|Gruppeindstillingen Begrænset app  |Hvad kan du gøre?  |
|---------|---------|
|Begræns ikke filaktivitet     |Beder DLP om at tillade brugere at få adgang til DLP-beskyttede elementer ved hjælp af apps i appgruppen og ikke udføre nogen **handlinger, når** brugeren forsøger at kopiere til Udklipsholder **,** Kopiér til et **USB-flytbart** drev, Kopiér til et netværksdrev og **Udskriv** fra appen.          |
|Anvend en begrænsning på alle aktiviteter     |Fortæller DLP til `Audit only`, eller `Block with override`når en `Block` bruger forsøger at få adgang til et DLP-beskyttet element ved hjælp af en app, der er i denne appgruppe         |
|Anvend begrænsninger på en bestemt aktivitet     |Denne indstilling giver en bruger adgang til et DLP-beskyttet element ved hjælp af en app, der er i appgruppen, og gør det muligt at vælge en standardhandling (`Audit only`, `Block``Block with override`eller ), som DLP skal tage, når en bruger forsøger at kopiere til Udklipsholder **,** Kopiér til et **USB-flytbart** **drev,** Kopiér til et netværksdrev og **Udskriv**.          |

> [!IMPORTANT]
> Indstillinger i en begrænset appgruppe tilsidesætter eventuelle begrænsninger, der er angivet på listen over begrænsede apps, når de er i den samme regel. Så hvis en app er på listen med begrænsede apps og er medlem af en gruppe med begrænsede apps, anvendes indstillingerne for gruppen med begrænsede apps.

#### <a name="how-dlp-applies-restrictions-to-activities"></a>Sådan anvender DLP begrænsninger på aktiviteter

Interaktioner mellem **filaktiviteter for apps i begrænsede appgrupper (forhåndsvisning)**, Filaktiviteter **for alle apps** og listen Begrænsede **appaktiviteter** er begrænset til den samme regel.

##### <a name="restricted-app-groups-overrides"></a>Tilsidesættelse af begrænsede appgrupper

Konfigurationer, der er defineret i Filaktiviteter **for apps i begrænsede appgrupper (** forhåndsvisning), tilsidesætter konfigurationerne på listen Begrænsede **appaktiviteter** og Filaktiviteter **for alle apps** i samme regel.

##### <a name="restricted-app-activities-and-file-activities-for-all-apps"></a>Begrænsede appaktiviteter og filaktiviteter for alle apps

Konfigurationerne af Begrænsede **appaktiviteter** og Filaktiviteter **for alle apps** fungerer sammen, hvis handlingen, der er defineret for Begrænsede **app-aktiviteter**`Audit only`, `Block with override` enten er eller i samme regel. Dette skyldes, at handlinger, der er defineret for Begrænsede **app-aktiviteter** , kun gælder, når en bruger får adgang til en fil ved hjælp af en app, der er på listen. Når brugeren har adgang, gælder de handlinger, der er defineret for **aktiviteter i Filaktiviteter for alle apps** . 

Her er et eksempel:

Hvis Notepad.exe **føjes** til Begrænsede apps og Filaktiviteter for alle **apps** er konfigureret til Anvend begrænsninger på bestemt  aktivitet, og begge er konfigureret sådan:

|Indstilling i politik  |Appnavn  |Brugeraktivitet  |DLP-handling, der skal  |
|---------|---------|---------|---------|
|Begrænsede appaktiviteter     |Notesblok        |Få adgang til et DLP-beskyttet element         |Kun overvågning         |
|Filaktiviteter for alle apps   |Alle apps        | Kopiér til Udklipsholder        |Kun overvågning         |
|Filaktiviteter for alle apps     |Alle apps         |Kopiér til en USB-enhed, der kan fjernes | Bloker       |
|Filaktiviteter for alle apps     |Alle apps         |Kopiér til et netværksshare         |Kun overvågning         |
|Filaktiviteter for alle apps   |Alle apps         |Udskriv         |Bloker         |
|Filaktiviteter for alle apps     |Alle apps         |Kopiér eller flyt ved hjælp af Bluetooth-app         |Blokeret         |
|Filaktiviteter for alle apps     |Alle apps         |Fjernskrivebord-tjenester         |Bloker med tilsidesættelse         |

Bruger A åbner en DLP-beskyttet fil med Notesblok. DLP gør det muligt at få adgang til og overvåge aktiviteten. Mens du stadig Notesblok, forsøger Bruger A derefter at kopiere til Udklipsholder fra det beskyttede element, dette fungerer, og DLP overvåger aktiviteten. Bruger A forsøger derefter at udskrive det beskyttede element Notesblok, og aktiviteten er blokeret.

> [!NOTE]
> Når DLP-handlingen, der skal udføres i Begrænsede **appaktiviteter** `block`er angivet til , blokeres al adgang, og brugeren kan ikke udføre nogen aktiviteter på filen.
   
##### <a name="file-activities-for-all-apps-only"></a>Filaktiviteter kun for alle apps

Hvis en app ikke er i Filaktiviteter **for apps i begrænsede appgrupper (** forhåndsvisning) eller ikke er på listen Begrænsede **appaktiviteter** eller er på listen Begrænsede **appaktiviteter** `Audit only`med en handling af , eller 'Bloker med tilsidesættelse', anvendes eventuelle begrænsninger, der er defineret i Filaktiviteter **for alle apps** , i den samme regel.  

#### <a name="macos-devices-preview"></a>macOS-enheder (forhåndsvisning)

Ligesom på Windows-enheder kan du nu forhindre macOS-apps i at få adgang til følsomme data ved at definere dem på listen Begrænsede **appaktiviteter**. 

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

Du kan bruge automatisk karantæne for at forhindre en endeløs kæde af DLP-meddelelser til brugeren og administratorerne – se Scenarie 4: Undgå at gentage [DLP-meddelelser](endpoint-dlp-using.md#scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview) fra skysynkroniseringsapps med automatisk karantæne (forhåndsvisning).

### <a name="unallowed-bluetooth-apps"></a>Ikke tilladt Bluetooth apps

Undgå, at personer overfører filer, der er beskyttet af dine politikker, via bestemte Bluetooth apps.

### <a name="browser-and-domain-restrictions-to-sensitive-data"></a>Browser- og domænebegrænsninger for følsomme data

Begræns følsomme filer, der svarer til dine politikker, i at blive delt med ikke-ubegrænset skytjenestedomæner.

#### <a name="unallowed-browsers"></a>Ikke-tilladte browsere

For Windows enheder, du tilføjer browsere, identificeret ved deres eksekverbare navne, der vil være blokeret fra at få adgang til filer, der opfylder betingelserne i en gennemtvunget DLP-politik, hvor begrænsningen for upload til skytjenester er indstillet til at blokere eller blokere tilsidesættelse. Når disse browsere er blokeret fra at få adgang til en fil, får slutbrugerne vist en toastbesked, der beder dem om at åbne filen via Microsoft Edge.

På macOS-enheder skal du tilføje den fulde filsti. Sådan finder du hele stien til Mac-apps:

1. Åbn Aktivitetsovervågning på **macOS-enheden**. Find og dobbeltklik på den proces, du vil begrænse

2. Vælg **fanen Åbn filer og** porte.
  
3. For macOS-apps skal du bruge det fulde stinavn, herunder navnet på appen.

#### <a name="service-domains"></a>Tjenestedomæner

> [!NOTE]
> Indstillingen **Tjenestedomæner gælder kun** for filer, der er overført ved hjælp Microsoft Edge eller Google Chrome, hvor [Microsoft Overholdelsesudvidelse er](dlp-chrome-learn-about.md#learn-about-the-microsoft-compliance-extension) installeret.

Du kan styre, om følsomme filer, der er beskyttet af dine politikker, kan overføres til bestemte tjenestedomæner fra Microsoft Edge.

Hvis listetilstanden er **indstillet til** Bloker, vil brugeren ikke kunne overføre følsomme elementer til disse domæner. Når en overførselshandling blokeres, fordi et element svarer til en DLP-politik, genererer DLP enten en advarsel eller blokerer upload af det følsomme element.

Hvis listetilstanden er indstillet til **Tillad, vil** brugerne kun kunne overføre følsomme elementer til **** disse domæner, og upload af adgang til alle andre domæner er ikke tilladt.

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

### <a name="always-audit-file-activity-for-devices"></a>Altid overvåge filaktivitet for enheder

Når enheder er onboardet, overvåges aktivitet for filer Office PDF- og CSV-filer som standard automatisk og kan gennemses i Aktivitetsoversigt. Slå denne funktion fra, hvis du kun vil have denne aktivitet overvåget, når onboardede enheder er inkluderet i en aktiv politik.

Filaktivitet overvåges altid for onboardede enheder, uanset om de er inkluderet i en aktiv politik.

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
