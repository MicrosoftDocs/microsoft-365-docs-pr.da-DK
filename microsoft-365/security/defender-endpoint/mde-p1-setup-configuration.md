---
title: Konfigurere og konfigurere Microsoft Defender for Endpoint Plan 1
description: Få mere at vide om, hvordan du konfigurerer Defender til Endpoint Plan 1. Gennemse kravene, planlæg din udrulning, og konfigurer dit miljø.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 01/14/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: e2a8f7166e1fa3a05b95b1a48dbf91b30ef34224
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470367"
---
# <a name="set-up-and-configure-microsoft-defender-for-endpoint-plan-1"></a>Konfigurere og konfigurere Microsoft Defender for Endpoint Plan 1

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Denne artikel beskriver, hvordan du konfigurerer Defender for Endpoint Plan 1. Uanset om du har hjælp, eller du gør det selv, kan du bruge denne artikel som vejledning i hele installationen.  

## <a name="the-setup-and-configuration-process"></a>Konfigurationsprocessen

:::image type="content" source="images/mde-p1-deploymentflow.png" alt-text="Konfigurations- og installationsflow Microsoft Defender for Endpoint Plan 1" lightbox="images/mde-p1-deploymentflow.png":::

Den generelle konfigurations- og konfigurationsproces for Defender til Endpoint Plan 1 er som følger: <br/><br/>


| Tal  | Trin  | Beskrivelse  |
|:---------:|:---------|:---------|
| 1 | [Gennemse kravene](#review-the-requirements)  | Viser krav til licenser, browser, operativsystem og datacenter   |
| 2 | [Planlæg din installation](#plan-your-deployment) | Viser flere installationsmetoder, du bør overveje, og inkluderer links til flere ressourcer, der kan hjælpe dig med at beslutte, hvilken metode du skal bruge  |
| 3 | [Konfigurer dit lejermiljø](#set-up-your-tenant-environment) | Viser opgaver til konfiguration af dit lejermiljø |
| 4 | [Tildel roller og tilladelser](#assign-roles-and-permissions) | Viser roller og tilladelser, som du bør overveje i sikkerhedsteamet <br/><br/>**Tip**: Så snart roller og tilladelser tildeles, kan dit sikkerhedsteam komme i gang med at Microsoft 365 Defender portal. Du kan få mere at vide under [Introduktion](mde-plan1-getting-started.md). |
| 5 | [Onboard to Defender til Slutpunkt](#onboard-to-defender-for-endpoint) | Viser flere metoder efter operativsystem for at onboarde til Defender for Endpoint Plan 1 og indeholder links til mere detaljerede oplysninger om hver metode  |
| 6 | [Konfigurer næste generations beskyttelse](#configure-next-generation-protection) | Beskrivelse af, hvordan du konfigurerer dine næste generations beskyttelsesindstillinger i Microsoft Endpoint Manager  |
| 7 | [Konfigurer dine muligheder for reduktion af angrebsoverfladen](#configure-your-attack-surface-reduction-capabilities)        | Viser de typer reduktionsfunktioner til angrebsoverfladen, du kan konfigurere, og indeholder procedurer med links til flere ressourcer  |
 
## <a name="review-the-requirements"></a>Gennemse kravene

I følgende tabel vises de grundlæggende krav til Defender for Endpoint Plan 1:<br/><br/>

| Krav | Beskrivelse |
|:---|:---|
| Licenskrav | Defender til Endpoint Plan 1 (tidligere kaldet Microsoft Defender for Endpoint Lite)|
| Browserkrav | Microsoft Edge <br/> Internet Explorer version 11 <br/> Google Chrome |
| Operativsystemer | Windows 10, version 1709 eller nyere <br/>macOS: 11.5 (Big Sur), 10.15.7 (Catalina) eller 10.14.6 (Mojave) <br/>iOS <br/>Android OS  |
| Datacenter | En af følgende datacenterplaceringer: <br/>- EU <br/>- Storbritannien <br/>- USA |


## <a name="plan-your-deployment"></a>Planlæg din installation

Når du planlægger din installation, kan du vælge mellem flere forskellige arkitekturer og installationsmetoder. Hver organisation er unik, så du har flere muligheder at overveje, som angivet i følgende tabel: <br/><br/>

| Metode | Beskrivelse |
|:---|:---|
| [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (inkluderet i Microsoft Endpoint Manager) | Brug Intune til at administrere slutpunkter i et indbygget skymiljø |
| [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) og [Configuration Manager](/mem/configmgr/core/understand/introduction) (findes i Microsoft Endpoint Manager) | Brug Intune og Configuration Manager til at administrere slutpunkter og arbejdsbelastninger, der strækker sig over et lokalt miljø og et skymiljø |
| [Konfigurationsstyring](/mem/configmgr/core/understand/introduction) | Brug Configuration Manager til at beskytte slutpunkter i det lokale miljø med den skybaserede styrke fra Defender til Slutpunkt |
| Lokalt script downloadet fra Microsoft 365 Defender Portal | Brug lokale scripts på slutpunkter til at køre et pilotprojekt eller onboard blot nogle få enheder |

Hvis du vil have mere at vide om dine installationsindstillinger, [skal du se Planlæg din Defender til slutpunktsinstallation](deployment-strategy.md). Hent derefter følgende plakat: 

[:::image type="content" source="../../media/defender-endpoint/mde-deployment-strategy.png" alt-text="Miniaturebillede af plakat for implementeringsstrategi":::](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)

**[Hent installationsplakaten](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)**

> [!TIP]
> Du kan finde mere detaljerede oplysninger om planlægning af din installation [i Planlæg Microsoft Defender for Endpoint installation](deployment-strategy.md).

## <a name="set-up-your-tenant-environment"></a>Konfigurer dit lejermiljø

Konfiguration af dit lejermiljø omfatter opgaver, f.eks.:

- Bekræftelse af dine licenser
- Konfiguration af din lejer
- Konfiguration af dine proxyindstillinger (kun hvis det er nødvendigt)
- Sørg for, at sensorerne fungerer korrekt, og at rapportere data til Defender til Slutpunkt 

Disse opgaver er inkluderet i konfigurationsfasen for Defender til slutpunkt. Se [Konfigurer Defender til Slutpunkt](production-deployment.md).

## <a name="assign-roles-and-permissions"></a>Tildel roller og tilladelser

For at få adgang til Microsoft 365 Defender-portalen skal du konfigurere indstillingerne for Defender til slutpunkt eller udføre opgaver, f.eks. udføre svarhandlinger ved registrerede trusler, tildeles de relevante tilladelser. Defender til Slutpunkt bruger [indbyggede roller i Azure Active Directory](/azure/active-directory/roles/permissions-reference). 

Microsoft anbefaler, at du kun tildeler brugere det tilladelsesniveau, de skal bruge for at kunne udføre deres opgaver. Du kan tildele tilladelser ved hjælp af grundlæggende administration af tilladelser eller ved hjælp af [rollebaseret adgangskontrol](rbac.md) (RBAC). 

- Med grundlæggende administration af tilladelser har globale administratorer og sikkerhedsadministratorer fuld adgang, hvorimod sikkerhedslæsere kun har skrivebeskyttet adgang.
- Med RBAC kan du angive mere detaljerede tilladelser gennem flere roller. Du kan f.eks. have sikkerhedslæsere, sikkerhedsoperatorer, sikkerhedsadministratorer, slutpunktsadministratorer og meget mere.


I følgende tabel beskrives nøgleroller, som skal overvejes for Defender som slutpunkt i organisationen: <br/><br/>

| Rolle | Beskrivelse |
|:---|:---|
| Globale administratorer (også kaldet globale administratorer) <br/><br/> *Som bedste fremgangsmåde skal du begrænse antallet af globale administratorer.* | Globale administratorer kan udføre alle typer opgaver. Den person, der tilmeldte sig din virksomhed Microsoft 365 til Microsoft Defender for Endpoint Plan 1, er som standard global administrator. <br/><br/> Globale administratorer kan få adgang til/ændre indstillinger på tværs af Microsoft 365 portaler, f.eks.: <br/>- Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) <br/>- Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  |
| Sikkerhedsadministratorer (også kaldet sikkerhedsadministratorer) | Sikkerhedsadministratorer kan udføre sikkerhedsoperatorens opgaver samt følgende opgaver: <br/>- Overvåge sikkerhedsrelaterede politikker <br/>- Administrere sikkerhedstrusler og beskeder <br/>- Vis rapporter |
| Sikkerhedsoperatør | Sikkerhedsoperatorer kan udføre opgaver med sikkerhedslæsere samt følgende opgaver: <br/>- Få vist oplysninger om registrerede trusler <br/>- Undersøge og reagere på registrerede trusler  |
| Sikkerhedslæser | Sikkerhedslæsere kan udføre følgende opgaver: <br/>- Få vist sikkerhedsrelaterede politikker på tværs Microsoft 365 tjenester <br/>- Få vist sikkerhedstrusler og beskeder <br/>- Vis rapporter  |


> [!TIP]
> Du kan få mere at vide om Azure Active Directory i Tildel [administratorroller og ikke-administratorroller til brugere med Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal). Og du kan finde flere oplysninger om roller for Defender til slutpunkt [i Rollebaseret adgangskontrol](prepare-deployment.md#role-based-access-control).

## <a name="onboard-to-defender-for-endpoint"></a>Onboard to Defender til Slutpunkt

Når du er klar til at onboarde din organisations slutpunkter, kan du vælge mellem flere forskellige metoder, som angivet i følgende tabel: <br/><br/>

|Slutpunktsoperativsystemet | Onboardingmetoder|
|---|---|
| Windows 10 | [Lokalt script (op til 10 enheder)](configure-endpoints-script.md) <br>  [Gruppepolitik](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/Mobile-Enhedshåndtering](configure-endpoints-mdm.md) <br> [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [VDI-scripts](configure-endpoints-vdi.md)  |
| macOS | [Lokale scripts](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [SYLTEF Pro](mac-install-with-jamf.md) <br> [Mobildata Enhedshåndtering](mac-install-with-other-mdm.md) |
| iOS |[Appbaseret](ios-install.md) |
| Android | [Microsoft Endpoint Manager](android-intune.md) |

Fortsæt derefter med at konfigurere din næste generations beskyttelse og reduktion af angrebsoverfladen.

## <a name="configure-next-generation-protection"></a>Konfigurer næste generations beskyttelse

Vi anbefaler at [Microsoft Endpoint Manager](/mem) til at administrere organisationens enheder og sikkerhedsindstillinger, som vist på følgende billede:
 
:::image type="content" source="../../media/mde-p1/endpoint-policies.png" alt-text="Sikkerhedspolitikker for slutpunkter i Micorosft Endpoint Manager portal" lightbox="../../media/mde-p1/endpoint-policies.png":::

Hvis du vil konfigurere din næste generations beskyttelse i Microsoft Endpoint Manager, skal du følge disse trin:

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Vælg **Endpoint** **securityAntivirus** > , og vælg derefter en eksisterende politik. Hvis du ikke har en eksisterende politik, skal du oprette en ny politik.

3. Angiv eller rediger dine indstillinger for antiviruskonfiguration. Har du brug for hjælp? Se følgende ressourcer: <br/>

   - [Indstillinger til Windows 10 Microsoft Defender Antivirus politik i Microsoft Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-windows)
   - [Konfigurer Defender til Slutpunkt på iOS-funktioner](ios-configure-features.md)

4. Når du er færdig med at angive dine indstillinger, skal du **vælge Gennemse + gem**.

## <a name="configure-your-attack-surface-reduction-capabilities"></a>Konfigurer dine muligheder for reduktion af angrebsoverfladen

Reduktion af angrebsoverfladen handler om at reducere antallet af steder og måder, din organisation er åben for angreb på. Defender til Endpoint Plan 1 indeholder adskillige funktioner og funktioner, der kan hjælpe dig med at reducere dine angrebsoverflader på tværs af dine slutpunkter. Disse funktioner og egenskaber er angivet i følgende tabel: <br/><br/>

| Funktion/funktion | Beskrivelse |
|:---|:---|
| [Regler for reduktion af angrebsoverflade](#attack-surface-reduction-rules) | Konfigurer regler for reduktion af angrebsoverfladen for at begrænse softwarebaseret risikabel adfærd og for at hjælpe med at beskytte din organisation. Regler for reduktion af angrebsoverfladen målretter visse softwarefunktionsmåder, f.eks.<br/>- Starte eksekverbare filer og scripts, der forsøger at hente eller køre filer <br/>- Kører obskøne eller på anden måde mistænkelige scripts <br/>- Udførelse af funktionsmåder, som apps normalt ikke starter under normalt dag-til-dag arbejde <br/><br/>Sådanne softwarefunktionsmåder ses nogle gange i legitime programmer. Disse handlinger anses dog ofte for risikabelt, fordi de ofte misbruges af hackere via malware.  |
| [Afhjælpning af ransomware](#ransomware-mitigation) | Konfigurer afhjælpning af ransomware ved at konfigurere styret mappeadgang, som hjælper med at beskytte din organisations værdifulde data fra skadelige apps og trusler, f.eks ransomware. | 
| [Enhedsstyring](#device-control) | Konfigurer indstillinger for enhedsstyring for din organisation for at tillade eller blokere flytbare enheder (f.eks. USB-drev). | 
| [Netværksbeskyttelse](#network-protection) | Konfigurer netværksbeskyttelse for at forhindre personer i organisationen i at bruge programmer, der får adgang til skadelige domæner eller skadeligt indhold på internettet. |
| [Webbeskyttelse](#web-protection) | Konfigurer beskyttelse mod webtrusler for at beskytte din organisations enheder mod phishingwebsteder, udnytte websteder og andre websteder med upålidelige eller dårligt ry. Konfigurere filtrering af webindhold for at spore og regulere adgangen til websteder baseret på deres indholdskategorier (f.eks. ferie, høj båndbredde, indhold beregnet for voksne eller juridisk ansvar). |
| [Netværksfirewall](#network-firewall) | Konfigurer din netværksfirewall med regler, der bestemmer, hvilken netværkstrafik der må komme ind eller ud af din organisations enheder. |
| [Programkontrolelement](#application-control)  | Konfigurer regler for programkontrol, hvis du kun vil tillade, at der køres programmer og processer på dine Windows enheder.    |

### <a name="attack-surface-reduction-rules"></a>Regler for reduktion af angrebsoverflade

Regler for reduktion af angrebsoverfladen er tilgængelige på enheder, der Windows. Vi anbefaler at Microsoft Endpoint Manager, som vist på følgende billede:

:::image type="content" source="../../media/mde-p1/mem-asrpolicies.png" alt-text="Regler for reduktion af angrebsoverfladen i Microsoft Endpoint Manager portal" lightbox="../../media/mde-p1/mem-asrpolicies.png":::

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Vælg **Endpoint** **securityAttack** >  surface reduction > **+ Opret politik**.

3. Ud **for Platform** skal **du Windows 10 og nyere**.

4. For **Profil** skal du vælge **Regler for reduktion af angrebsoverfladen** og derefter **vælge Opret**.

5. Angiv et **navn og** en beskrivelse af politikken under fanen Grundlæggende, og vælg derefter **Næste**.

6. På fanen **Konfigurationsindstillinger** skal du udvide Regler **for reduktion af angrebsoverfladen**.

7. Angiv indstillinger for hver regel, og vælg derefter **Næste**. (Du kan finde flere oplysninger om, hvad hver regel gør, under [Regler for reduktion af angrebsoverfladen](attack-surface-reduction.md)).) 

8. På fanen **Omfangsmærker** skal du, hvis din organisation bruger omfangsmærker, vælge **+ Vælg** områdemærker og derefter vælge de mærker, du vil bruge. Vælg derefter **Næste**. 
   
   Du kan få mere at vide om omfangsmærker [under Brug rollebaseret adgangskontrol (RBAC) og omfangsmærker for distribueret IT](/mem/intune/fundamentals/scope-tags).

9. På fanen **Opgaver skal** du angive de brugere og grupper, som din politik skal anvendes for, og derefter vælge **Næste**. Hvis du vil have mere at vide om opgaver, [skal du se Tildel bruger- og enhedsprofiler Microsoft Intune](/mem/intune/configuration/device-profile-assign).

10. Gennemgå indstillingerne **under fanen Gennemse** + opret, og vælg derefter **Opret**.

> [!TIP]
> Du kan få mere at vide om regler for reduktion af angrebsoverfladen i følgende ressourcer:
> - [Brug regler for reduktion af angrebsoverfladen til at forhindre malware inficeret](attack-surface-reduction.md)
> - [Få vist listen over reduktionsregler for angrebsoverfladen](attack-surface-reduction-rules-reference.md)
> - [Implementering af regler for reduktion af angrebsoverfladen Trin 3: Implementer ASR-regler](attack-surface-reduction-rules-deployment-implement.md)

### <a name="ransomware-mitigation"></a>Afhjælpning af ransomware

Du får afhjælpning af ransomware gennem [styret mappeadgang](controlled-folders.md#what-is-controlled-folder-access), som kun tillader pålidelige apps at få adgang til beskyttede mapper på dine slutpunkter. 

Vi anbefaler, at Microsoft Endpoint Manager til at konfigurere styret mappeadgang.

:::image type="content" source="../../media/mde-p1/mem-asrpolicies.png" alt-text="ASR-politikker i Microsoft Endpoint Manager portal" lightbox="../../media/mde-p1/mem-asrpolicies.png":::

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på. 

2. Vælg **Endpoint Security**, og vælg derefter **Reduktion af angrebsoverfladen**.

3. Vælg **+ Opret politik**. 

4. Ud **for Platform** skal **du Windows 10 og nyere**, og ud for **Profil** skal du vælge **Regler for reduktion af angrebsoverfladen**. Vælg derefter **Opret**. 

5. Under fanen **Grundlæggende skal** du navngive politikken og tilføje en beskrivelse. Vælg **Næste**. 

6. Rul **ned til** bunden i sektionen Regler for reduktion **af angrebsoverfladen** under fanen Konfigurationsindstillinger. Vælg **Aktivér på** rullelisten Aktivér **mappebeskyttelse**. Du kan eventuelt angive disse andre indstillinger:

   - Ud **for Liste over yderligere** mapper, der skal være beskyttet, skal du vælge rullemenuen og derefter tilføje mapper, der skal være beskyttet.
   - Ud for **Liste over apps**, der har adgang til beskyttede mapper, skal du vælge rullemenuen og derefter tilføje apps, der skal have adgang til beskyttede mapper.
   - Ud for **Udelad filer** og stier fra reduktionsregler for angrebsoverfladen skal du vælge rullemenuen og derefter tilføje de filer og stier, der skal udelukkes fra reduktionsregler for angrebsoverfladen.

   Vælg derefter **Næste**.

7. På fanen **Omfangsmærker** skal du, hvis din organisation bruger omfangsmærker, vælge **+ Vælg** områdemærker og derefter vælge de mærker, du vil bruge. Vælg derefter **Næste**. 
   
   Du kan få mere at vide om omfangsmærker [under Brug rollebaseret adgangskontrol (RBAC) og omfangsmærker for distribueret IT](/mem/intune/fundamentals/scope-tags).

8. På fanen **Opgaver skal** du vælge **Tilføj alle brugere** og **+ Tilføj alle enheder** og derefter vælge **Næste**. (Du kan alternativt angive bestemte grupper af brugere eller enheder).

9. På fanen **Gennemse + Opret** skal du gennemgå indstillingerne for din politik og derefter vælge **Opret**. Politikken vil blive anvendt på alle slutpunkter, der blev onboardet til Defender for Endpoint inden længe.

### <a name="device-control"></a>Enhedsstyring

Du kan konfigurere Defender til slutpunkt til at blokere eller tillade flytbare enheder og filer på flytbare enheder. Vi anbefaler, at Microsoft Endpoint Manager til at konfigurere indstillingerne for enhedsstyring.

:::image type="content" source="../../media/mde-p1/mem-admintemplates.png" alt-text="Microsoft Endpoint Manager administrative skabeloner" lightbox="../../media/mde-p1/mem-admintemplates.png":::

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på. 

2. Vælg **EnhederKonfigurationsprofilerOpret** >  >  **profil**.

3. Under **Platform** skal du **Windows 10 og nyere**, og for **Profiltype** skal du vælge **Skabeloner**. 

   Under **Skabelonnavn** skal du **vælge Administrative skabeloner** og derefter vælge **Opret**. 

4. Under fanen **Grundlæggende skal** du navngive politikken og tilføje en beskrivelse. Vælg **Næste**. 

5. Vælg Alle **indstillinger under** fanen **Konfigurationsindstillinger Indstillinger**. Skriv derefter i søgefeltet for at `Removable` få vist alle de indstillinger, der gælder for flytbare enheder.

6. Vælg et element på listen, f.eks. Alle flytbare **Storage klasser:** Afvisning af al adgang for at åbne pop op-ruden. Pop-op-pop-op-pop-op'en for hver indstilling forklarer, hvad der sker, når den er aktiveret, deaktiveret eller ikke konfigureret. Vælg en indstilling, og vælg derefter **OK**. 

7. Gentag trin 6 for hver indstilling, du vil konfigurere. Vælg derefter **Næste**.

8. På fanen **Omfangsmærker** skal du, hvis din organisation bruger omfangsmærker, vælge **+ Vælg** områdemærker og derefter vælge de mærker, du vil bruge. Vælg derefter **Næste**. 
   
   Du kan få mere at vide om omfangsmærker [under Brug rollebaseret adgangskontrol (RBAC) og omfangsmærker for distribueret IT](/mem/intune/fundamentals/scope-tags).

9. På fanen **Opgaver skal** du vælge **Tilføj alle brugere** og **+ Tilføj alle enheder** og derefter vælge **Næste**. (Du kan alternativt angive bestemte grupper af brugere eller enheder).

10. På fanen **Gennemse + Opret** skal du gennemgå indstillingerne for din politik og derefter vælge **Opret**. Politikken vil blive anvendt på alle slutpunkter, der blev onboardet til Defender for Endpoint inden længe.

> [!TIP]
> Få mere at vide under [Sådan styrer du USB-enheder og andre flytbare medier ved hjælp Microsoft Defender for Endpoint](control-usb-devices-using-intune.md).

### <a name="network-protection"></a>Netværksbeskyttelse

Med netværksbeskyttelse kan du beskytte din organisation mod skadelige domæner, der kan hoste forsøg på phishing, udnyttelse og andet skadeligt indhold på internettet. Vi anbefaler, at Microsoft Endpoint Manager til at slå netværksbeskyttelse til.

:::image type="content" source="../../media/mde-p1/mem-endpointprotectionprofile.png" alt-text="Endpoint Protection-profil i Microsoft Endpoint Manager portalen" lightbox="../../media/mde-p1/mem-endpointprotectionprofile.png":::

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på. 

2. Vælg **EnhederKonfigurationsprofilerOpret** >  >  **profil**.

3. Under **Platform** skal du **Windows 10 og nyere**, og for **Profiltype** skal du vælge **Skabeloner**. 

   Under **Skabelonnavn** skal du **vælge Slutpunktsbeskyttelse** og derefter vælge **Opret**. 

4. Under fanen **Grundlæggende skal** du navngive politikken og tilføje en beskrivelse. Vælg **Næste**. 

5. På fanen **Konfigurationsindstillinger** skal **du udvide Microsoft Defender Exploit Guard** og derefter udvide **Netværksfiltrering**.

   Angiv **Netværksbeskyttelse til** **Aktivér**. Du kan alternativt vælge Overvågning **for at** se, hvordan netværksbeskyttelse fungerer i dit miljø i starten.

   Vælg derefter **Næste**.

6. På fanen **Opgaver skal** du vælge **Tilføj alle brugere** og **+ Tilføj alle enheder** og derefter vælge **Næste**. (Du kan alternativt angive bestemte grupper af brugere eller enheder).

7. Konfigurer **en regel under** fanen Regler for anvendelse. Den profil, du konfigurerer, anvendes kun på enheder, der opfylder de kombinerede kriterier, du angiver. 

   Du kan f.eks. vælge at tildele politikken til slutpunkter, der kun kører en bestemt VERSION af operativsystemet.

   Vælg derefter **Næste**. 

8. På fanen **Gennemse + Opret** skal du gennemgå indstillingerne for din politik og derefter vælge **Opret**. Politikken vil blive anvendt på alle slutpunkter, der blev onboardet til Defender for Endpoint inden længe.

> [!TIP]
> Du kan bruge andre metoder, f.eks. Windows PowerShell eller Gruppepolitik, til at aktivere netværksbeskyttelse. Du kan få mere at vide [under Slå netværksbeskyttelse til](enable-network-protection.md).

### <a name="web-protection"></a>Webbeskyttelse

Med webbeskyttelse kan du beskytte din organisations enheder mod webtrusler og uønsket indhold. Din webbeskyttelse omfatter [beskyttelse mod webtrusler](#configure-web-threat-protection) og [filtrering af webindhold](#configure-web-content-filtering). Konfigurer begge sæt af funktioner. Vi anbefaler, at Microsoft Endpoint Manager til at konfigurere indstillingerne for webbeskyttelse.

#### <a name="configure-web-threat-protection"></a>Konfigurere beskyttelse mod webtrusler

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.
 
2. Vælg **Endpoint** **securityAttack** >  surface reduction, og vælg derefter **+ Opret politik**.

3. Vælg en platform, **f.eks. Windows 10 senere**, vælg **Webbeskyttelsesprofil**, og vælg derefter **Opret**. 

4. Angiv et **navn og** en beskrivelse under fanen Grundlæggende, og vælg derefter **Næste**.

5. På fanen **Konfigurationsindstillinger** skal du **udvide Webbeskyttelse**, angive indstillingerne i følgende tabel og derefter vælge **Næste**. <br/><br/>

   | Indstilling | Anbefaling |
   |:---|:---|
   | **Aktivér netværksbeskyttelse** | Indstillet til **Aktiveret**. Forhindrer brugere i at besøge skadelige websteder eller domæner. <br/><br/>Alternativt kan du angive netværksbeskyttelse til **overvågningstilstand for** at se, hvordan det fungerer i dit miljø. I overvågningstilstand forhindrer netværksbeskyttelse ikke brugere i at besøge websteder eller domæner, men den sporer registreringer som hændelser. |
   | **Kræv SmartScreen til Den ældre version af Microsoft Edge** | Er indstillet **til Ja**. Hjælper med at beskytte brugere mod potentielt forsøg på phishing og skadelig software. |
   | **Bloker ondsindet adgang til webstedet** | Er indstillet **til Ja**. Forhindrer brugere i at ignorere advarsler om potentielt skadelige websteder. |
   | **Bloker ikke-bekræftet filoverførsel** | Er indstillet **til Ja**. Forhindrer brugere i at ignorere advarslerne og hente ikke-bekræftede filer. |

6. På fanen **Omfangsmærker** skal du, hvis din organisation bruger omfangsmærker, vælge **+ Vælg** områdemærker og derefter vælge de mærker, du vil bruge. Vælg derefter **Næste**. 
   
   Du kan få mere at vide om omfangsmærker [under Brug rollebaseret adgangskontrol (RBAC) og omfangsmærker for distribueret IT](/mem/intune/fundamentals/scope-tags).

7. På fanen **Opgaver skal** du angive de brugere og enheder, der skal modtage webbeskyttelsespolitikken, og derefter vælge **Næste**.

8. På fanen **Gennemse + Opret** skal du gennemgå dine politikindstillinger og derefter vælge **Opret**.

> [!TIP]
> Du kan få mere at vide om beskyttelse mod webtrusler [under Beskyt din organisation mod webtrusler](web-threat-protection.md).

#### <a name="configure-web-content-filtering"></a>Konfigurere filtrering af webindhold

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com/](https://security.microsoft.com/)), og log på.

2. Vælg **Indstillinger** >  **Endpoints**.

3. Under **Regler** skal du **vælge Filtrering af webindhold** og derefter **vælge + Tilføj politik**.

4. Angiv **et navn** til politikken på fanen **Generelt** i pop op-dialogboksen Tilføj politik, og vælg derefter **Næste**.

5. I **kategorierne Blokerede** skal du vælge en eller flere kategorier, som du vil blokere, og derefter vælge **Næste**.

6. På fanen **Omfang** skal du vælge de enhedsgrupper, du vil modtage denne politik for, og derefter vælge **Næste**.

7. Gennemgå **politikindstillingerne** under fanen Oversigt, og vælg derefter **Gem**.

> [!TIP]
> Hvis du vil have mere at vide om konfiguration af filtrering af webindhold, skal du [se Filtrering af webindhold](web-content-filtering.md).

### <a name="network-firewall"></a>Netværksfirewall

Netværksfirewall er med til at reducere risikoen for sikkerhedstrusler på netværket. Dit sikkerhedsteam kan angive regler, der bestemmer, hvilken trafik der må flyde til eller fra din organisations enheder. Vi anbefaler, at Microsoft Endpoint Manager til at konfigurere din netværksfirewall. 

:::image type="content" source="../../media/mde-p1/mem-firewallpolicy.png" alt-text="Firewallpolitik i Microsoft Endpoint Manager portalen" lightbox="../../media/mde-p1/mem-firewallpolicy.png":::

Hvis du vil konfigurere grundlæggende firewall-indstillinger, skal du følge disse trin:

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Vælg **Endpoint** **securityFirewall** > , og vælg **derefter + Opret politik**.

3. Vælg en platform, **f.eks. Windows 10 senere**, vælg **Microsoft Defender Firewall-profilen**, og vælg derefter **Opret**. 

4. Angiv et **navn og** en beskrivelse under fanen Grundlæggende, og vælg derefter **Næste**.

5. **Udvid Microsoft Defender Firewall**, og rul derefter ned til bunden af listen.

6. Angiv hver af følgende indstillinger til **Ja**:

   - **Slå Microsoft Defender Firewall til for domænenetværk** 
   - **Slå Microsoft Defender Firewall til for private netværk**
   - **Slå Microsoft Defender Firewall til for offentlige netværk**
   
   Gennemgå listen over indstillinger under hvert af domænenetværk, private netværk og offentlige netværk. Du kan lade dem være indstillet **til Ikke konfigureret**, eller du kan ændre dem, så de passer til din organisations behov.

   Vælg derefter **Næste**.

7. På fanen **Omfangsmærker** skal du, hvis din organisation bruger omfangsmærker, vælge **+ Vælg** områdemærker og derefter vælge de mærker, du vil bruge. Vælg derefter **Næste**. 
   
   Du kan få mere at vide om omfangsmærker [under Brug rollebaseret adgangskontrol (RBAC) og omfangsmærker for distribueret IT](/mem/intune/fundamentals/scope-tags).

8. På fanen **Opgaver skal** du vælge **Tilføj alle brugere** og **+ Tilføj alle enheder** og derefter vælge **Næste**. (Du kan alternativt angive bestemte grupper af brugere eller enheder).

9. På fanen **Gennemse + Opret** skal du gennemgå dine politikindstillinger og derefter vælge **Opret**.

> [!TIP]
> Firewallindstillinger er detaljerede og kan virke komplekse. Se Bedste [fremgangsmåder til konfiguration Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/best-practices-configuring).

### <a name="application-control"></a>Programkontrolelement

Windows Defender (WDAC ) hjælper med at beskytte dine Windows slutpunkter ved kun at tillade kørsel af programmer og processer, der er tillid til. De fleste organisationer har brugt en fasevis installation af WDAC. Det vil sige, at de fleste organisationer ikke udruller WDAC på tværs Windows slutpunkter i starten. Afhængigt af om din organisations Windows-slutpunkter er fuldt administreret, let administreret eller "Medbring din egen enhed"-slutpunkter, kan du installere WDAC på alle eller nogle slutpunkter.

Hvis du vil have hjælp til at planlægge din WDAC-installation, skal du se følgende ressourcer:

- [Programkontrolelement til Windows](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)

- [Windows Defender for politikdesign af programkontrol](/windows/security/threat-protection/windows-defender-application-control/understand-windows-defender-application-control-policy-design-decisions)

- [Windows Defender installation af programkontrol i forskellige scenarier: typer af enheder](/windows/security/threat-protection/windows-defender-application-control/types-of-devices)

## <a name="next-steps"></a>Næste trin

Nu hvor du har gennemgået konfigurationsprocessen, er det næste trin at komme i gang med at bruge Defender til slutpunkt. 

- [Kom i gang med Defender for Endpoint Plan 1](mde-plan1-getting-started.md)
