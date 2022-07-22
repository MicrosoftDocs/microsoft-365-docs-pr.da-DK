---
title: Få vist og rediger dine sikkerhedsindstillinger i Microsoft Defender til virksomheder
description: Få vist og rediger sikkerhedspolitikker og -indstillinger i Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365solution-mdb-setup
ms.openlocfilehash: 27c8d475f91381d9f7f1842ceffd729230158f51
ms.sourcegitcommit: 00948161a72d8cea8c2baba873743fc4a0e19f90
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/22/2022
ms.locfileid: "66969282"
---
# <a name="view-and-edit-security-policies-and-settings-in-microsoft-defender-for-business"></a>Få vist og rediger sikkerhedspolitikker og -indstillinger i Microsoft Defender til virksomheder

Når du har onboardet din virksomheds enheder til Defender for Business, er det næste trin at gennemse dine sikkerhedspolitikker. 

> [!TIP]
> Defender for Business indeholder forudkonfigurerede sikkerhedspolitikker med anbefalede indstillinger. Du kan redigere disse indstillinger, så de passer til dine forretningsbehov.

Sikkerhedspolitikker, der skal gennemses og konfigureres, omfatter:

- **[Næste generations beskyttelsespolitikker](#view-or-edit-your-next-generation-protection-policies)**, der bestemmer beskyttelse mod antivirus og antimalware på din virksomheds enheder
- **[Firewallbeskyttelse og regler](#view-or-edit-your-firewall-policies-and-custom-rules)**, der bestemmer, hvilken netværkstrafik der må overføres til og fra virksomhedens enheder
- **[Filtrering af webindhold](#set-up-web-content-filtering)**, som forhindrer folk i at besøge bestemte websteder (URL-adresser) baseret på kategorier, f.eks. indhold beregnet af voksne eller juridisk ansvar
- **[Avancerede funktioner](#review-settings-for-advanced-features)**, f.eks. automatiseret undersøgelse og svar og EDR (endpoint detection and response) i bloktilstand

I Defender for Business anvendes sikkerhedspolitikker på enheder via [enhedsgrupper](mdb-create-edit-device-groups.md#what-is-a-device-group). 

Ud over dine sikkerhedspolitikker kan du [få vist og redigere indstillinger](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal), f.eks. hvilken tidszone der skal bruges i Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og om du vil modtage prøveversionsfunktioner, når de bliver tilgængelige.

Brug denne artikel som en vejledning til administration af dine sikkerhedspolitikker og -indstillinger.

## <a name="what-to-do"></a>Sådan gør du

1. [Vælg, hvor du vil administrere dine sikkerhedspolitikker og -enheder](#choose-where-to-manage-security-policies-and-devices).
2. [Gennemse dine beskyttelsespolitikker i næste generation](#view-or-edit-your-next-generation-protection-policies).
3. [Gennemse firewallpolitikker og brugerdefinerede regler](#view-or-edit-your-firewall-policies-and-custom-rules).
4. [Konfigurer filtrering af webindhold](#set-up-web-content-filtering).
5. [Gennemse indstillingerne for avancerede funktioner](#review-settings-for-advanced-features).
6. [Få vist andre indstillinger på Microsoft 365 Defender-portalen](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal). 
7. [Fortsæt til de næste trin](#next-steps).


## <a name="choose-where-to-manage-security-policies-and-devices"></a>Vælg, hvor sikkerhedspolitikker og -enheder skal administreres

Defender for Business indeholder en [forenklet konfigurationsproces](mdb-simplified-configuration.md) , der hjælper med at strømline konfigurationsprocessen. Hvis du vælger den forenklede konfigurationsproces, kan du få vist og administrere dine sikkerhedspolitikker på portalen Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)). Du er dog ikke begrænset til denne indstilling. Hvis du har brugt Microsoft Intune, kan du fortsætte med at bruge Microsoft Endpoint Manager Administration.

Følgende tabel kan hjælpe dig med at vælge, hvor du vil administrere dine sikkerhedspolitikker og -enheder.

| Mulighed | Beskrivelse |
|:---|:---|
| **Brug Microsoft 365 Defender-portalen** (*anbefales*) | Microsoft 365 Defender-portalen ([https://security.microsoft.com/](https://security.microsoft.com/)) er en one-stop-shop til administration af virksomhedens enheder, sikkerhedspolitikker og sikkerhedsindstillinger. Du kan få adgang til dine sikkerhedspolitikker og -indstillinger, bruge [dashboardet Threat & Administration af sårbarheder](mdb-view-tvm-dashboard.md) og [få vist og administrere hændelser](mdb-view-manage-incidents.md) på ét sted. <p>Hvis du bruger Intune, er de enheder, du onboarder til Defender for Business, og dine sikkerhedspolitikker synlige i Endpoint Manager Administration. Du kan få mere at vide i følgende artikler:<ul><li>[Standardindstillinger og Microsoft Intune for Defender for Business](mdb-next-gen-configuration-settings.md#defender-for-business-default-settings-and-microsoft-intune)</li><li>[Firewall i Defender for Business](mdb-firewall.md)</li></ul>   |
| **Brug Microsoft Endpoint Manager Administration** | Hvis din virksomhed allerede bruger Intune til at administrere sikkerhedspolitikker, kan du fortsætte med at bruge Endpoint Manager Administration til at administrere dine enheder og sikkerhedspolitikker. Du kan få mere at vide under [Administrer enhedssikkerhed med sikkerhedspolitikker for slutpunkter i Microsoft Intune](/mem/intune/protect/endpoint-security-policy). <p>Hvis du beslutter at skifte til den [forenklede konfigurationsproces i Defender for Business](mdb-simplified-configuration.md), bliver du bedt om at slette alle eksisterende sikkerhedspolitikker i Intune for at undgå [politikkonflikter](mdb-troubleshooting.yml) senere. |

> [!IMPORTANT]
> Hvis du administrerer sikkerhedspolitikker på Microsoft 365 Defender-portalen, kan du *få vist* disse politikker i Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), hvor de er angivet som **Antivirus-** eller **Firewall-politikker**. Når du får vist dine firewallpolitikker i Administration, kan du se to politikker angivet: én politik for firewallbeskyttelse og en anden for brugerdefinerede regler.

## <a name="view-or-edit-your-next-generation-protection-policies"></a>Få vist eller rediger dine beskyttelsespolitikker i næste generation

Afhængigt af om du bruger Microsoft 365 Defender-portalen eller Microsoft Endpoint Manager Administration til at administrere din næste generation af beskyttelsespolitikker, skal du bruge en af følgende procedurer:

| Portal | Procedure |
|:---|:---|
| Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) |<ol><li>Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.</li><li>Vælg **Enhedskonfiguration** i navigationsruden. Politikker er organiseret efter operativsystem og politiktype.</li><li>Vælg en operativsystemfane (f.eks **. Windows-klienter**).</li><li>Udvid **Næste generation af beskyttelse** for at få vist din liste over politikker.</li><li>Vælg en politik for at få vist flere oplysninger om politikken.</li><li>Hvis du vil foretage ændringer eller få mere at vide om politikindstillinger, skal du se følgende artikler: <ul><li>[Få vist eller rediger enhedspolitikker](mdb-view-edit-policies.md)</li><li>[Om konfigurationsindstillinger for næste generation](mdb-next-gen-configuration-settings.md)</li></ul></li><ol>  |
| Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) |Hvis du vil have hjælp til at administrere dine sikkerhedsindstillinger i Intune, skal du starte med [Administrer slutpunktssikkerhed i Microsoft Intune](/mem/intune/protect/endpoint-security). <ol><li>Gå til , [https://endpoint.microsoft.com](https://endpoint.microsoft.com) og log på. Du er nu i Endpoint Manager Administration.</li><li>Vælg **Slutpunktsikkerhed**.</li><li>Vælg **Antivirus** for at få vist dine politikker i den pågældende kategori.</li></ol>|

## <a name="view-or-edit-your-firewall-policies-and-custom-rules"></a>Få vist eller rediger firewallpolitikker og brugerdefinerede regler

Afhængigt af om du bruger Microsoft 365 Defender-portalen eller Microsoft Endpoint Manager Administration til at administrere din firewallbeskyttelse, skal du bruge en af følgende procedurer.

| Portal | Procedure |
|:---|:---|
| Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) |<ol><li>Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.</li><li>Vælg **Enhedskonfiguration** i navigationsruden. Politikker er organiseret efter operativsystem og politiktype.</li><li>Vælg en operativsystemfane (f.eks **. Windows-klienter**).</li><li>Udvid **Firewall** for at få vist listen over politikker.</li><li>Vælg en politik for at få vist detaljerne. </li><li>Hvis du vil foretage ændringer eller få mere at vide om politikindstillinger, skal du se følgende artikler:<ul><li>[Få vist eller rediger enhedspolitikker](mdb-view-edit-policies.md)</li><li>[Firewallindstillinger](mdb-firewall.md)</li><li>[Administrer dine brugerdefinerede regler for firewallpolitikker](mdb-custom-rules-firewall.md)</li><ul></li><ol>  |
| Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) |Hvis du vil have hjælp til at administrere dine sikkerhedsindstillinger i Intune, skal du starte med [Administrer slutpunktssikkerhed i Microsoft Intune](/mem/intune/protect/endpoint-security). <ol><li>Gå til , [https://endpoint.microsoft.com](https://endpoint.microsoft.com) og log på. Du er nu i Endpoint Manager Administration.</li><li>Vælg **Slutpunktsikkerhed**.</li><li>Vælg **Firewall** for at få vist dine politikker i den pågældende kategori. Brugerdefinerede regler, der er defineret for firewallbeskyttelse, er angivet som separate politikker.</li></ol>|

## <a name="set-up-web-content-filtering"></a>Konfigurer filtrering af webindhold

Filtrering af webindhold gør det muligt for dit sikkerhedsteam at spore og regulere adgangen til websteder baseret på indholdskategorier, f.eks.:

- Indhold for voksne: Websteder, der er relateret til sekter, hasardspil, nøgenhed, pornografi, seksuelt eksplicit materiale eller vold
- Høj båndbredde: Downloadwebsteder, websteder til billeddeling eller peer-to-peer-værter
- Juridisk ansvar: Websteder, der indeholder billeder af børnemishandling, fremmer ulovlige aktiviteter, fremmer plagiering eller skolesnyd, eller som fremmer skadelige aktiviteter
- Fritid: Websteder, der indeholder webbaserede chatrum, onlinespil, webbaseret mail eller sociale netværk
- Ikke kategoriseret: Websteder, der ikke har noget indhold, eller som er nyligt registreret

Ikke alle websteder i disse kategorier er skadelige, men de kan være problematiske for din virksomhed på grund af overholdelsesregler, båndbreddeforbrug eller andre bekymringer. Du kan oprette en politik kun for overvågning for at få en bedre forståelse af, om dit sikkerhedsteam skal blokere webstedskategorier.

Filtrering af webindhold er tilgængelig i de store webbrowsere med blokke udført af Windows Defender SmartScreen (Microsoft Edge) og Network Protection (Chrome, Firefox, Brave og Opera). Du kan få flere oplysninger under [Forudsætninger for filtrering af webindhold](../defender-endpoint/web-content-filtering.md#prerequisites).

### <a name="to-set-up-web-content-filtering"></a>Sådan konfigurerer du filtrering af webindhold

1. På Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) skal du vælge **Indstillinger Filtrering** >  af  > **webindhold****+ Tilføj politik**.

2. Angiv et navn og en beskrivelse til politikken.

3. Vælg de kategorier, der skal blokeres. Brug udvidelsesikonet til fuldt ud at udvide hver overordnede kategori, og vælg derefter specifikke kategorier for webindhold. Hvis du vil konfigurere en politik, der kun tillader overvågning, og som ikke blokerer nogen websteder, skal du ikke vælge nogen kategorier.

   Vælg ikke **Ikke-kategoriseret**.

4. Angiv politikomfanget ved at vælge de enhedsgrupper, politikken skal anvendes på. Det er kun enheder i de valgte enhedsgrupper, der forhindres i at få adgang til websteder i de valgte kategorier.

5. Gennemse oversigten, og gem politikken. Det kan tage op til to timer, før opdateringen af politikken gælder for de valgte enheder.

> [!TIP]
> Du kan få mere at vide om filtrering af webindhold under [Filtrering af webindhold](../defender-endpoint/web-content-filtering.md).

## <a name="review-settings-for-advanced-features"></a>Gennemse indstillinger for avancerede funktioner

Ud over næste generations politikker for beskyttelse, firewall og filtrering af webindhold indeholder Defender for Business avancerede sikkerhedsfunktioner. Disse funktioner er forudkonfigureret til anbefalede indstillinger. Du kan gennemse og redigere indstillingerne, så de passer til dine forretningsbehov.

Hvis du vil have adgang til indstillinger for avancerede funktioner på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), skal du gå til **Indstillinger** > **Slutpunkter** > **Generelle** > **avancerede funktioner**.

I følgende tabel beskrives avancerede funktionsindstillinger.

| Indstilling | Beskrivelse |
|:---|:---|
| **Automatiseret undersøgelse** <br/>(slået til som standard) | Efterhånden som der genereres beskeder, kan der forekomme automatiserede undersøgelser. Hver automatiseret undersøgelse bestemmer, om en registreret trussel kræver handling, og tager eller anbefaler derefter afhjælpningshandlinger, f.eks. afsendelse af en fil til karantæne, standsning af en proces, isolering af en enhed eller blokering af en URL-adresse. Mens der kører en undersøgelse, føjes eventuelle relaterede beskeder, der opstår, til undersøgelsen, indtil den er fuldført. Hvis et berørt objekt vises et andet sted, udvider den automatiserede undersøgelse dens omfang til at omfatte det pågældende objekt, og undersøgelsesprocessen gentages.<p>Du kan få vist undersøgelser på siden **Hændelser** . Vælg en hændelse, og vælg derefter fanen **Undersøgelser** .<p>Automatiserede undersøgelses- og svarfunktioner er som standard slået til i hele lejeren. **Vi anbefaler, at automatiseret undersøgelse er slået til**. Hvis du slår den fra, påvirkes beskyttelse i realtid i Microsoft Defender Antivirus, og dit overordnede beskyttelsesniveau reduceres. <p>[Få mere at vide om automatiserede undersøgelser](../defender-endpoint/automated-investigations.md).   |
| **Live-svar**  | Defender for Business indeholder følgende typer manuelle svarhandlinger: <ul><li>Kør antivirusscanning</li><li>Isoler enhed</li><li>Stop og sæt en fil i karantæne</li><li>Tilføj en indikator for at blokere eller tillade en fil</li></ul> <p>[Få mere at vide om svarhandlinger](../defender-endpoint/respond-machine-alerts.md). |
| **Live-svar til servere** | Denne indstilling er i øjeblikket ikke tilgængelig i Defender for Business.   |
| **Udførelse af live-svar uden fortegn** | Denne indstilling er i øjeblikket ikke tilgængelig i Defender for Business.  | 
| **Aktivér EDR i bloktilstand**<br/>(slået til som standard) | Giver ekstra beskyttelse mod skadelige artefakter, når Microsoft Defender Antivirus ikke er det primære antivirusprodukt og kører i passiv tilstand på en enhed. EDR (Endpoint Detection and Response) i bloktilstand fungerer bag kulisserne for at afhjælpe skadelige artefakter, der registreres af EDR-funktioner. Sådanne artefakter kan være blevet overset af det primære antivirusprodukt, der ikke er fra Microsoft.<p>[Få mere at vide om EDR i bloktilstand](../defender-endpoint/edr-in-block-mode.md). |
| **Tillad eller bloker en fil** <br/>(slået til som standard) | Giver dig mulighed for at tillade eller blokere en fil ved hjælp af [indikatorer](../defender-endpoint/indicator-file.md). Denne funktion kræver, at Microsoft Defender Antivirus er i aktiv tilstand, og [at skybeskyttelse](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md) er slået til.<p>Blokering af en fil forhindrer, at den læses, skrives eller udføres på enheder i din organisation. <p>[Få mere at vide om indikatorer for filer](../defender-endpoint/indicator-file.md).  |
| **Brugerdefinerede netværksindikatorer**<br/>(slået til som standard) | Giver dig mulighed for at tillade eller blokere en IP-adresse, EN URL-adresse eller et domæne ved hjælp af [netværksindikatorer](../defender-endpoint/indicator-ip-domain.md). Denne funktion kræver, at Microsoft Defender Antivirus er i aktiv tilstand, og [at netværksbeskyttelse](../defender-endpoint/enable-network-protection.md) er slået til.<p>Du kan tillade eller blokere IP-adresser, URL-adresser eller domæner baseret på din trusselsintelligens. Du kan også spørge brugerne, om de åbner en risikable app, men prompten forhindrer dem ikke i at bruge appen.<p>[Få mere at vide om netværksbeskyttelse](../defender-endpoint/network-protection.md). |
| **Ændringsbeskyttelse**<br/>(vi anbefaler, at du aktiverer denne indstilling) | Ændringsbeskyttelse forhindrer skadelige apps i at udføre handlinger som f.eks.:<ul><li>Deaktiver beskyttelse mod virus og trusler</li><li>Deaktiver beskyttelse i realtid</li><li>Slå overvågning af funktionsmåde fra</li><li>Deaktiver skybeskyttelse</li><li>Fjern sikkerhedsintelligensopdateringer</li><li>Deaktiver automatiske handlinger på registrerede trusler</li></ul><p>Manipulationsbeskyttelse låser i bund og grund Microsoft Defender Antivirus til sine sikre, standardværdier og forhindrer, at dine sikkerhedsindstillinger ændres af apps og uautoriseret metoder. <p>[Få mere at vide om beskyttelse mod manipulation](../defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection.md).  |
| **Vis brugeroplysninger**<br/>(slået til som standard) | Gør det muligt for personer i din organisation at se detaljer, f.eks. medarbejdernes billeder, navne, titler og afdelinger. Disse oplysninger gemmes i Azure Active Directory (Azure AD).<p>[Få mere at vide om brugerprofiler i Azure AD](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).  |
| **Skype for Business integration**<br/>(slået til som standard) | Skype for Business blev udgået i juli 2021. Hvis du ikke allerede er flyttet til Microsoft Teams, skal du se [Konfigurer Microsoft Teams i din lille virksomhed](/microsoftteams/deploy-small-business). <p>Integration med Microsoft Teams (eller den tidligere Skype for Business) muliggør kommunikation med et enkelt klik mellem personer i din virksomhed.   |
| **Filtrering af webindhold**<br/>(slået til som standard) | Blokerer adgang til websteder, der indeholder uønsket indhold, og sporer webaktivitet på tværs af alle domæner. Se [Konfigurer filtrering af webindhold](#set-up-web-content-filtering). |
| **Microsoft Intune forbindelse**<br/>(Vi anbefaler, at du aktiverer denne indstilling, hvis du har Intune) | Hvis din organisations abonnement omfatter Microsoft Intune (inkluderet i [Microsoft 365 Business Premium](../../business/index.yml)), gør denne indstilling det muligt for Defender for Business at dele oplysninger om enheder med Intune.  |
| **Enhedssøgning**<br/>(slået til som standard) | Gør det muligt for sikkerhedsteamet at finde ikke-administrerede enheder, der er forbundet til virksomhedens netværk. Ukendte og ikke-administrerede enheder medfører betydelige risici for netværket, uanset om det er en ikke-kompatibel printer, en netværksenhed med en svag sikkerhedskonfiguration eller en server uden sikkerhedskontroller.<p>Enhedsregistrering bruger onboardede enheder til at finde ikke-administrerede enheder, så dit sikkerhedsteam kan onboarde de ikke-administrerede enheder og reducere din sårbarhed. <p>[Få mere at vide om enhedsregistrering](../defender-endpoint/device-discovery.md).    |
| **Visningsfunktioner** | Microsoft opdaterer løbende tjenester, f.eks. Defender for Business, for at inkludere nye funktionsforbedringer og funktioner. Hvis du vælger at modtage prøveversionsfunktioner, er du blandt de første til at prøve kommende funktioner i prøveversionsoplevelsen. <p>[Få mere at vide om prøveversionsfunktioner](../defender-endpoint/preview.md).  |

## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>Få vist og rediger andre indstillinger på Microsoft 365 Defender-portalen

Ud over de sikkerhedspolitikker, der anvendes på enheder, er der andre indstillinger, som du kan få vist og redigere i Defender for Business. Du kan f.eks. angive den tidszone, der skal bruges, og du kan onboarde (eller offboard) enheder. 

> [!NOTE]
> Du kan muligvis se flere indstillinger i din lejer, end der er angivet i denne artikel. I denne artikel fremhæves de vigtigste indstillinger, du skal gennemse i Defender for Business.

### <a name="settings-to-review-for-defender-for-business"></a>Indstillinger, der skal gennemses for Defender for Business

I følgende tabel beskrives indstillinger, som du kan få vist og redigere i Defender for Business:

| Kategori | Indstilling | Beskrivelse |
|:---|:---|:---|
| **Sikkerhedscenter** | **Tidszone** | Vælg den tidszone, der skal bruges til de datoer og klokkeslæt, der vises i hændelser, registrerede trusler og automatisk undersøgelse og afhjælpning. Du kan enten bruge UTC eller din lokale tidszone (*anbefales*).  |
| **Microsoft 365 Defender** | **Konto** | Få vist detaljer, f.eks. hvor dine data er gemt, dit lejer-id og dit organisations-id. |
| **Microsoft 365 Defender**  | **Visningsfunktioner**  | Slå prøveversionsfunktioner til for at prøve kommende funktioner og nye funktioner. Du kan være blandt de første til at få forhåndsvist nye funktioner og give feedback. |
| **Slutpunkter**  | **Mailbeskeder** | Konfigurer eller rediger reglerne for mailmeddelelser. Når der registreres sikkerhedsrisici, eller der oprettes en besked, modtager de modtagere, der er angivet i reglerne for mailmeddelelser, en mail. [Få mere at vide om mailmeddelelser](mdb-email-notifications.md). |
| **Slutpunkter**   | **Enhedshåndtering** >  **Onboarding** | Onboarde enheder til Defender for Business ved hjælp af et script, der kan downloades. Du kan få mere at vide under [Onboarder enheder til Defender for Business](mdb-onboard-devices.md).   |  
| **Slutpunkter**  |  **Enhedshåndtering** >  **Offboarding** | Offboard (fjern) enheder fra Defender for Business. Når du kommer væk fra en enhed, sender den ikke længere data til Defender for Business, men data, der modtages før offboarding, bevares. Du kan få mere at vide under [Offboarding af en enhed](mdb-offboard-devices.md).  |

### <a name="access-your-settings-in-the-microsoft-365-defender-portal"></a>Få adgang til dine indstillinger på Microsoft 365 Defender-portalen

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com/](https://security.microsoft.com/)), og log på.

2. Vælg **Indstillinger**, og vælg derefter en kategori (f.eks **. Security Center**, **Microsoft 365 Defender** eller **Slutpunkter**).

3. Vælg et element, der skal vises eller redigeres, på listen over indstillinger.

## <a name="next-steps"></a>Næste trin

- [Kom i gang med at bruge Defender for Business](mdb-get-started.md)
- [Administrer enheder i Defender for Business](mdb-manage-devices.md)
- [Få vist og administrer hændelser i Defender for Business](mdb-view-manage-incidents.md)
- [Få vist eller rediger politikker i Defender for Business](mdb-view-edit-policies.md)
