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
- m365-initiative-defender-business
ms.openlocfilehash: 757545231a7bbe544bfbacf082fc03d88fb2df2f
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174168"
---
# <a name="view-and-edit-your-security-policies-and-settings-in-microsoft-defender-for-business"></a>Få vist og rediger dine sikkerhedspolitikker og -indstillinger i Microsoft Defender til virksomheder

Når du har onboardet din virksomheds enheder for at Microsoft Defender til virksomheder, er dit næste skridt at gennemse dine sikkerhedspolitikker. Hvis det er nødvendigt, kan du redigere dine sikkerhedspolitikker og -indstillinger. 

> [!TIP]
> Defender for Business indeholder forudkonfigurerede sikkerhedspolitikker, der bruger anbefalede indstillinger. Du kan dog redigere dine indstillinger, så de passer til dine forretningsbehov.

Sikkerhedspolitikker, der skal gennemses og konfigureres, omfatter:

- **[Næste generations beskyttelsespolitikker](#view-or-edit-your-next-generation-protection-policies)**, der bestemmer beskyttelse mod antivirus og antimalware på din virksomheds enheder
- **[Firewallbeskyttelse og regler](#view-or-edit-your-firewall-policies-and-custom-rules)**, der bestemmer, hvilken netværkstrafik der må overføres til eller fra virksomhedens enheder
- **[Filtrering af webindhold](#set-up-web-content-filtering)**, som forhindrer folk i at besøge bestemte websteder (URL-adresser) baseret på kategorier, f.eks. indhold beregnet til voksne eller juridisk ansvar.
- **[Avancerede funktioner](#review-settings-for-advanced-features)**, f.eks. automatiseret undersøgelse og svar, og slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) i bloktilstand.

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

>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om sikkerhed</a>. Vi vil meget gerne høre fra dig!
>

## <a name="choose-where-to-manage-security-policies-and-devices"></a>Vælg, hvor sikkerhedspolitikker og -enheder skal administreres

Defender for Business indeholder en [forenklet konfigurationsproces](mdb-simplified-configuration.md) , der hjælper med at strømline konfigurationsprocessen. Hvis du vælger den forenklede konfigurationsproces, kan du få vist og administrere dine sikkerhedspolitikker på portalen Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)). Du er dog ikke begrænset til denne indstilling. Hvis du har brugt Microsoft Intune, kan du fortsætte med at bruge Microsoft Endpoint Manager Administration.

Følgende tabel kan hjælpe dig med at vælge, hvor du vil administrere dine sikkerhedspolitikker og -enheder. <br/><br/>

| Mulighed | Beskrivelse |
|:---|:---|
| **Brug Microsoft 365 Defender-portalen** (*anbefales*) | Microsoft 365 Defender-portalen ([https://security.microsoft.com/](https://security.microsoft.com/)) kan være dit one-stop-shop til administration af virksomhedens enheder, sikkerhedspolitikker og sikkerhedsindstillinger. Du kan få adgang til dine sikkerhedspolitikker og -indstillinger, bruge [dashboardet Administration af trussel &](mdb-view-tvm-dashboard.md) [sårbarheder og få vist og administrere hændelser](mdb-view-manage-incidents.md) på ét sted. <br/><br/>Hvis du bruger Intune, er de enheder, du onboarder til Defender for Business, og dine sikkerhedspolitikker synlige i Endpoint Manager Administration. Du kan få mere at vide i følgende artikler:<br/>- [Standardindstillinger og Microsoft Intune for Defender for Business](mdb-next-gen-configuration-settings.md#defender-for-business-default-settings-and-microsoft-intune) <br/>- [Firewall i Microsoft Defender til virksomheder](mdb-firewall.md)   |
| **Brug Microsoft Endpoint Manager Administration** | Hvis din virksomhed allerede bruger Intune til at administrere sikkerhedspolitikker, kan du fortsætte med at bruge Endpoint Manager Administration til at administrere dine enheder og sikkerhedspolitikker. Du kan få mere at vide under [Administrer enhedssikkerhed med sikkerhedspolitikker for slutpunkter i Microsoft Intune](/mem/intune/protect/endpoint-security-policy). <br/><br/>Hvis du beslutter at skifte til den [forenklede konfigurationsproces i Defender for Business](mdb-simplified-configuration.md), bliver du bedt om at slette alle eksisterende sikkerhedspolitikker i Intune for at undgå [politikkonflikter](mdb-troubleshooting.yml) senere. |

> [!IMPORTANT]
> Hvis du administrerer sikkerhedspolitikker på Microsoft 365 Defender-portalen, kan du *få vist* disse politikker i Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) angivet som **Antivirus-** eller **Firewall-politikker**. Når du får vist dine firewallpolitikker i Endpoint Manager Administration, får du vist to politikker: én politik til beskyttelse af din firewall og en anden for brugerdefinerede regler.

## <a name="view-or-edit-your-next-generation-protection-policies"></a>Få vist eller rediger dine beskyttelsespolitikker i næste generation

Afhængigt af om du bruger Microsoft 365 Defender-portalen eller Microsoft Endpoint Manager Administration til at administrere dine beskyttelsespolitikker af næste generation, skal du bruge en af procedurerne i følgende tabel:

| Portal | Procedure |
|:---|:---|
| Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på. <br/><br/>2. Vælg **Enhedskonfiguration** i navigationsruden. Politikker er organiseret efter operativsystem og politiktype.<br/><br/>3. Vælg en operativsystemfane (f.eks. **Windows klienter**).<br/><br/>4. Udvid **Næste generations beskyttelse** for at få vist din liste over politikker.<br/><br/>5. Vælg en politik for at få vist flere oplysninger om politikken. Hvis du vil foretage ændringer eller få mere at vide om politikindstillinger, skal du se følgende artikler: <br/>- [Få vist eller rediger enhedspolitikker](mdb-view-edit-policies.md)<br/>- [Om konfigurationsindstillinger for næste generation](mdb-next-gen-configuration-settings.md)  |
| Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Gå til, [https://endpoint.microsoft.com](https://endpoint.microsoft.com) og log på. Du er nu i Endpoint Manager Administration.<br/><br/>2. Vælg **Slutpunktssikkerhed**.<br/><br/>3. Vælg **Antivirus** for at få vist dine politikker i den pågældende kategori. <br/><br/>Hvis du vil have hjælp til at administrere dine sikkerhedsindstillinger i Intune, skal du starte med [Administrer slutpunktssikkerhed i Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="view-or-edit-your-firewall-policies-and-custom-rules"></a>Få vist eller rediger firewallpolitikker og brugerdefinerede regler

Afhængigt af om du bruger Microsoft 365 Defender-portalen eller Microsoft Endpoint Manager Administration til at administrere firewallbeskyttelsen, skal du bruge en af procedurerne i følgende tabel:

| Portal | Procedure |
|:---|:---|
| Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på. <br/><br/>2. Vælg **Enhedskonfiguration** i navigationsruden. Politikker er organiseret efter operativsystem og politiktype.<br/><br/>3. Vælg en operativsystemfane (f.eks. **Windows klienter**).<br/><br/>4. Udvid **Firewall** for at få vist din liste over politikker.<br/><br/>5. Vælg en politik for at få vist flere oplysninger om politikken. Hvis du vil foretage ændringer eller få mere at vide om politikindstillinger, skal du se følgende artikler: <br/>- [Få vist eller rediger enhedspolitikker](mdb-view-edit-policies.md)<br/>- [Firewallindstillinger](mdb-firewall.md)<br/>- [Administrer dine brugerdefinerede regler for firewallpolitikker](mdb-custom-rules-firewall.md)  |
| Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Gå til, [https://endpoint.microsoft.com](https://endpoint.microsoft.com) og log på. Du er nu i Endpoint Manager Administration.<br/><br/>2. Vælg **Slutpunktssikkerhed**.<br/><br/>3. Vælg **Firewall** for at få vist dine politikker i den pågældende kategori. Brugerdefinerede regler, der er defineret for firewallbeskyttelse, er angivet som separate politikker.<br/><br/>Hvis du vil have hjælp til at administrere dine sikkerhedsindstillinger i Intune, skal du starte med [Administrer slutpunktssikkerhed i Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="set-up-web-content-filtering"></a>Konfigurer filtrering af webindhold

Filtrering af webindhold gør det muligt for dit sikkerhedsteam at spore og regulere adgangen til websteder baseret på deres indholdskategorier, f.eks.:

- Indhold for voksne: Websteder, der er relateret til sekter, hasardspil, nøgenhed, pornografi, seksuelt eksplicit materiale eller vold
- Høj båndbredde: Downloadwebsteder, websteder til billeddeling eller peer-to-peer-værter
- Juridisk ansvar: Websteder, der indeholder billeder af børnemishandling, fremmer ulovlige aktiviteter, fremmer plagiering eller skolesnyd, eller som fremmer skadelige aktiviteter
- Fritid: Websteder, der indeholder webbaserede chatrum, onlinespil, webbaseret mail eller sociale netværk
- Ikke kategoriseret: Websteder, der ikke har noget indhold, eller som er nyligt registreret

Ikke alle websteder i disse kategorier er ondsindede, men de kan være problematiske for din virksomhed på grund af overholdelsesregler, båndbreddeforbrug eller andre bekymringer. Derudover kan du oprette en politik kun for overvågning for at få en bedre forståelse af, om dit sikkerhedsteam skal blokere nogen webstedskategorier.

Filtrering af webindhold er tilgængelig i de større webbrowsere med blokke udført af Windows Defender SmartScreen (Microsoft Edge) og Network Protection (Chrome, Firefox, Brave og Opera). Du kan få flere oplysninger under [Forudsætninger for filtrering af webindhold](../defender-endpoint/web-content-filtering.md#prerequisites).

### <a name="to-set-up-web-content-filtering"></a>Sådan konfigurerer du filtrering af webindhold

1. Vælg **Indstillinger** >  **Webindholdsfiltrering** > **+ Tilføj politik** på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)).

2. Angiv et navn og en beskrivelse til politikken.

3. Vælg kategorier, der skal blokeres. Brug udvidelsesikonet til fuldt ud at udvide hver overordnet kategori, og vælg specifikke kategorier for webindhold. Hvis du vil konfigurere en politik, der kun tillader overvågning, og som ikke blokerer nogen websteder, skal du undlade at vælge nogen kategorier.

   Vælg ikke **Ikke-kategoriseret**.

4. Angiv politikomfanget ved at vælge enhedsgrupper for at anvende politikken. Det er kun enheder i de valgte enhedsgrupper, der forhindres i at få adgang til websteder i de valgte kategorier.

5. Gennemse oversigten, og gem politikken. Det kan tage op til to timer, før opdateringen af politikken gælder for de valgte enheder.

> [!TIP]
> Du kan få mere at vide om filtrering af webindhold under [Filtrering af webindhold](../defender-endpoint/web-content-filtering.md).

## <a name="review-settings-for-advanced-features"></a>Gennemse indstillinger for avancerede funktioner

Ud over næste generations politikker for beskyttelse, firewall og filtrering af webindhold indeholder Defender for Business avancerede sikkerhedsfunktioner. Disse funktioner forudkonfigureres ved hjælp af anbefalede indstillinger. Du kan dog gennemse dem og om nødvendigt redigere indstillingerne, så de passer til dine forretningsbehov.

Hvis du vil have adgang til indstillinger for avancerede funktioner, skal du gå til Indstillinger **EndpointsGenerellefunktioner** >  >  **på** portalen **Microsoft 365 Defender** >  ([https://security.microsoft.com](https://security.microsoft.com)).

I følgende tabel beskrives indstillingerne for avancerede funktioner:

| Indstilling | Beskrivelse |
|:---|:---|
| **Automatiseret undersøgelse** <br/>(slået til som standard) | Efterhånden som der genereres beskeder, kan der forekomme automatiserede undersøgelser. Hver automatiseret undersøgelse bestemmer, om en registreret trussel kræver handling, og tager derefter (eller anbefaler) afhjælpningshandlinger (f.eks. afsendelse af en fil til karantæne, standsning af en proces, isolering af en enhed eller blokering af en URL-adresse). Mens der kører en undersøgelse, føjes alle andre relaterede beskeder, der opstår, til undersøgelsen, indtil den er fuldført. Hvis et berørt objekt vises et andet sted, udvider den automatiserede undersøgelse dens omfang til at omfatte det pågældende objekt, og undersøgelsesprocessen gentages.<br/><br/>Du kan få vist undersøgelser på siden **Hændelser** . Vælg en hændelse, og vælg derefter fanen **Undersøgelser** .<br/><br/>Automatiserede undersøgelses- og svarfunktioner er som standard slået til i hele lejeren. **Vi anbefaler, at automatiseret undersøgelse er slået til**. Hvis du slår den fra, påvirkes beskyttelse i realtid i Microsoft Defender Antivirus, og dit overordnede beskyttelsesniveau reduceres. <br/><br/>[Få mere at vide om automatiserede undersøgelser](../defender-endpoint/automated-investigations.md).   |
| **Live-svar**  | Defender for Business indeholder følgende typer manuelle svarhandlinger: <br/>- Kør antivirusscanning<br/>- Isoler enhed<br/>- Stop og sæt en fil i karantæne<br/>– Tilføj en indikator for at blokere eller tillade en fil <br/><br/>[Få mere at vide om svarhandlinger](../defender-endpoint/respond-machine-alerts.md). |
| **Live-svar til servere** | (Denne indstilling er i øjeblikket ikke tilgængelig i Defender for Business)   |
| **Udførelse af live-svar uden fortegn** | (Denne indstilling er i øjeblikket ikke tilgængelig i Defender for Business)  | 
| **Aktivér Slutpunktsregistrering og -svar i bloktilstand**<br/>(slået til som standard) | Giver ekstra beskyttelse mod skadelige artefakter, når Microsoft Defender Antivirus ikke er det primære antivirusprodukt og kører i passiv tilstand på en enhed. Registrering og svar af slutpunkter (Slutpunktsregistrering og -svar) i bloktilstand fungerer bag kulisserne for at afhjælpe skadelige artefakter, der blev registreret af Slutpunktsregistrering og -svar funktioner. Sådanne artefakter kan være blevet overset af det primære antivirusprodukt, der ikke er fra Microsoft.<br/><br/>[Få mere at vide om Slutpunktsregistrering og -svar i bloktilstand](../defender-endpoint/edr-in-block-mode.md). |
| **Tillad eller bloker en fil** <br/>(slået til som standard) | Giver dig mulighed for at tillade eller blokere en fil ved hjælp af [indikatorer](../defender-endpoint/indicator-file.md). Denne funktion kræver, at Microsoft Defender Antivirus er i aktiv tilstand, og at [skybeskyttelse](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md) er aktiveret.<br/><br/>Blokering af en fil forhindrer den i at blive læst, skrevet eller udført på enheder i din organisation. <br/><br/>[Få mere at vide om indikatorer for filer](../defender-endpoint/indicator-file.md).  |
| **Brugerdefinerede netværksindikatorer**<br/>(slået til som standard) | Giver dig mulighed for at tillade eller blokere en IP-adresse, EN URL-adresse eller et domæne ved hjælp af [netværksindikatorer](../defender-endpoint/indicator-ip-domain.md). Denne funktion kræver, at Microsoft Defender Antivirus er i aktiv tilstand, og [at netværksbeskyttelse](../defender-endpoint/enable-network-protection.md) er aktiveret.<br/><br/>Du kan tillade eller blokere IP-adresser, URL-adresser eller domæner baseret på din egen trusselsintelligens. Du kan også advare brugerne med en prompt, hvis de åbner en risikable app. Prompten forhindrer dem ikke i at bruge appen, men du kan angive en advarsel til brugerne.<br/><br/>[Få mere at vide om netværksbeskyttelse](../defender-endpoint/network-protection.md). |
| **Ændringsbeskyttelse**<br/>(vi anbefaler, at du aktiverer denne indstilling) | Ændringsbeskyttelse forhindrer, at skadelige apps foretager handlinger som f.eks.:<br/>- Deaktivering af beskyttelse mod virus og trusler<br/>- Deaktivering af beskyttelse i realtid<br/>- Deaktivering af overvågning af funktionsmåde<br/>- Deaktivering af skybeskyttelse<br/>- Fjernelse af sikkerhedsintelligensopdateringer<br/>- Deaktivering af automatiske handlinger på registrerede trusler<br/><br/>Manipulationsbeskyttelse låser i bund og grund Microsoft Defender Antivirus til dens sikre standardværdier og forhindrer, at dine sikkerhedsindstillinger ændres af apps og uautoriseret metoder. <br/><br/>[Få mere at vide om beskyttelse mod manipulation](../defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection.md).  |
| **Vis brugeroplysninger**<br/>(slået til som standard) | Gør det muligt for personer i din organisation at se detaljer, f.eks. medarbejdernes billede, navn, titel og afdeling. Disse oplysninger gemmes i Azure Active Directory (Azure AD).<br/><br/>[Få mere at vide om brugerprofiler i Azure AD](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).  |
| **Skype for Business integration**<br/>(slået til som standard) | Skype for Business blev udgået i juli 2021. Hvis du ikke allerede er flyttet til Microsoft Teams, skal du se [Konfigurer Microsoft Teams i din lille virksomhed](/microsoftteams/deploy-small-business). <br/><br/>Integration med Microsoft Teams (eller den tidligere Skype for Business) muliggør kommunikation med et enkelt klik mellem personer i din virksomhed.   |
| **Filtrering af webindhold**<br/>(slået til som standard) | Bloker adgang til websteder, der indeholder uønsket indhold, og spor webaktivitet på tværs af alle domæner. Se [Konfigurer filtrering af webindhold](#set-up-web-content-filtering). |
| **Microsoft Intune forbindelse**<br/>(Vi anbefaler, at du aktiverer denne indstilling, hvis du har Intune) | Hvis din organisations abonnement omfatter Microsoft Intune (inkluderet i [Microsoft 365 Business Premium](../../business/index.yml)), gør denne indstilling det muligt for Defender for Business at dele oplysninger om enheder med Intune.  |
| **Enhedssøgning**<br/>(slået til som standard) | Gør det muligt for sikkerhedsteamet at finde ikke-administrerede enheder, der er forbundet til virksomhedens netværk. Ukendte og ikke-administrerede enheder medfører betydelige risici for dit netværk – uanset om det er en ikke-opdateret printer, netværksenheder med svage sikkerhedskonfigurationer eller en server uden sikkerhedskontroller. <br/><br/>Enhedsregistrering bruger onboardede enheder til at finde ikke-administrerede enheder, så dit sikkerhedsteam kan onboarde de ikke-administrerede enheder og reducere din sårbarhed. <br/><br/>[Få mere at vide om enhedsregistrering](../defender-endpoint/device-discovery.md).    |
| **Visningsfunktioner** | Microsoft opdaterer hele tiden tjenester, f.eks. Defender for Business, for at inkludere nye funktionsforbedringer og funktioner. Hvis du vælger at modtage prøveversionsfunktioner, er du blandt de første til at prøve kommende funktioner i prøveversionsoplevelsen. <br/><br/>[Få mere at vide om prøveversionsfunktioner](../defender-endpoint/preview.md).  |

## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>Få vist og rediger andre indstillinger på Microsoft 365 Defender-portalen

Ud over sikkerhedspolitikker, der anvendes på enheder, er der andre indstillinger, som du kan få vist og redigere i Defender for Business. Du kan f.eks. angive den tidszone, der skal bruges, og du kan onboarde (eller offboard) enheder. 

> [!NOTE]
> Du kan muligvis se flere indstillinger i din lejer, end der er angivet i denne artikel. I denne artikel fremhæves de vigtigste indstillinger, du skal gennemse i Defender for Business.

### <a name="settings-to-review-for-defender-for-business"></a>Indstillinger at gennemse for Defender for Business

I følgende tabel beskrives indstillinger for visning (og om nødvendigt redigering) i Defender for Business:

| Kategori | Indstilling | Beskrivelse |
|:---|:---|:---|
| **Sikkerhedscenter** | **Tidszone** | Vælg den tidszone, der skal bruges til de datoer og klokkeslæt, der vises i hændelser, registrerede trusler og automatisk undersøgelse & afhjælpning. Du kan enten bruge UTC eller din lokale tidszone (*anbefales*).  |
| **Microsoft 365 Defender** | **Konto** | Få vist detaljer, f.eks. hvor dine data er gemt, dit lejer-id og dit organisations-id. |
| **Microsoft 365 Defender**  | **Visningsfunktioner**  | Slå prøveversionsfunktioner til for at prøve kommende funktioner og nye funktioner. Du kan være blandt de første til at få forhåndsvist nye funktioner og give feedback. |
| **Slutpunkter**  | **Mailbeskeder** | Konfigurer eller rediger reglerne for mailmeddelelser. Når der registreres sikkerhedsrisici, eller der oprettes en besked, modtager de modtagere, der er angivet i reglerne for mailmeddelelser, en mail. [Få mere at vide om mailmeddelelser](mdb-email-notifications.md). |
| **Slutpunkter**   | **Enhedshåndtering** >  **Onboarding** | Onboarde enheder til Defender for Business ved hjælp af et script, der kan downloades. Du kan få mere at vide under [Onboard enheder for at Microsoft Defender til virksomheder](mdb-onboard-devices.md).   |  
| **Slutpunkter**  |  **Enhedshåndtering** >  **Offboarding** | Offboard (fjern) enheder fra Defender for Business. Når du kommer væk fra en enhed, sender den ikke længere data til Defender for Business, men data, der modtages før offboarding, bevares. Du kan få mere at vide under [Offboarding af en enhed](mdb-offboard-devices.md).  |

### <a name="access-your-settings-in-the-microsoft-365-defender-portal"></a>Få adgang til dine indstillinger på Microsoft 365 Defender-portalen

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com/](https://security.microsoft.com/)), og log på.

2. Vælg **Indstillinger**, og vælg derefter en kategori (f.eks **. Security Center**, **Microsoft 365 Defender** eller **Endpoints**).

3. Vælg et element, der skal vises eller redigeres, på listen over indstillinger.

## <a name="next-steps"></a>Næste trin

Fortsæt til en eller flere af følgende opgaver:

- [Kom i gang med at bruge Microsoft Defender til virksomheder](mdb-get-started.md)
- [Administrer enheder i Microsoft Defender til virksomheder](mdb-manage-devices.md)
- [Få vist og administrer hændelser i Microsoft Defender til virksomheder](mdb-view-manage-incidents.md)
- [Få vist eller rediger politikker i Microsoft Defender til virksomheder](mdb-view-edit-policies.md)

- [Få vist eller rediger politikker i Microsoft Defender til virksomheder](mdb-view-edit-policies.md)
