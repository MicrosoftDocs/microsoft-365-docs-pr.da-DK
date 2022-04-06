---
title: Konfigurer Microsoft Defender for Endpoint Plan 1
description: Få mere at vide om, hvordan du konfigurerer Defender for Endpoint Plan 1. Gennemse kravene, planlæg udrulningen, og konfigurer dit miljø.
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
ms.openlocfilehash: 774139aa6ccbf0562d5f6a9bf14eb89550e865a8
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665948"
---
# <a name="set-up-and-configure-microsoft-defender-for-endpoint-plan-1"></a>Konfigurer Microsoft Defender for Endpoint Plan 1

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

I denne artikel beskrives det, hvordan du konfigurerer Defender for Endpoint Plan 1. Uanset om du har hjælp eller gør det selv, kan du bruge denne artikel som vejledning i hele udrulningen.  

## <a name="the-setup-and-configuration-process"></a>Konfigurationsprocessen

:::image type="content" source="images/mde-p1-deploymentflow.png" alt-text="Konfigurer og udrulningsflow for Microsoft Defender for Endpoint Plan 1" lightbox="images/mde-p1-deploymentflow.png":::

Den generelle konfigurationsproces for Defender for Endpoint Plan 1 er som følger: <br/><br/>


| Antallet  | Trin  | Beskrivelse  |
|:---------:|:---------|:---------|
| 1 | [Gennemse kravene](#review-the-requirements)  | Viser krav til licenser, browser, operativsystem og datacenter   |
| 2 | [Planlæg din installation](#plan-your-deployment) | Viser flere udrulningsmetoder, der skal overvejes og inkluderes links til flere ressourcer, som kan hjælpe dig med at beslutte, hvilken metode der skal bruges  |
| 3 | [Konfigurer dit lejermiljø](#set-up-your-tenant-environment) | Viser en liste over opgaver til konfiguration af dit lejermiljø |
| 4 | [Tildel roller og tilladelser](#assign-roles-and-permissions) | Viser roller og tilladelser, der skal overvejes for dit sikkerhedsteam <br/><br/>**TIP**! Så snart roller og tilladelser er tildelt, kan dit sikkerhedsteam komme i gang med at bruge Microsoft 365 Defender portalen. Du kan få mere at vide under [Introduktion](mde-plan1-getting-started.md). |
| 5 | [Onboard til Defender for Endpoint](#onboard-to-defender-for-endpoint) | Viser flere metoder efter operativsystem til onboarding til Defender for Endpoint Plan 1 og indeholder links til mere detaljerede oplysninger om hver metode  |
| 6 | [Konfigurer næste generations beskyttelse](#configure-next-generation-protection) | Beskriver, hvordan du konfigurerer dine næste generations beskyttelsesindstillinger i Microsoft Endpoint Manager  |
| 7 | [Konfigurer dine funktioner til reduktion af angrebsoverfladen](#configure-your-attack-surface-reduction-capabilities)        | Viser de typer funktioner til reduktion af angrebsoverfladen, som du kan konfigurere og inkludere procedurer med links til flere ressourcer  |
 
## <a name="review-the-requirements"></a>Gennemse kravene

I følgende tabel vises de grundlæggende krav til Defender for Endpoint Plan 1:<br/><br/>

| Krav | Beskrivelse |
|:---|:---|
| Licenskrav | Defender for Endpoint Plan 1 |
| Krav til browser | Microsoft Edge <br/> Internet Explorer version 11 <br/> Google Chrome |
| Operativsystemer | Windows 10, version 1709 eller nyere <br/>macOS: 11.5 (Big Sur), 10.15.7 (Catalina) eller 10.14.6 (Mojave) <br/>Ios <br/>Android OS  |
| Datacenter | En af følgende datacenterplaceringer: <br/>- Den Europæiske Union <br/>- Det Forenede Kongerige <br/>- USA |


## <a name="plan-your-deployment"></a>Planlæg din installation

Når du planlægger din udrulning, kan du vælge mellem flere forskellige arkitekturer og udrulningsmetoder. Alle organisationer er entydige, så du har flere muligheder at overveje, som vist i følgende tabel: <br/><br/>

| Metode | Beskrivelse |
|:---|:---|
| [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (inkluderet i Microsoft Endpoint Manager) | Brug Intune til at administrere slutpunkter i et oprindeligt cloudmiljø |
| [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) og [Configuration Manager](/mem/configmgr/core/understand/introduction) (inkluderet i Microsoft Endpoint Manager) | Brug Intune og Configuration Manager til at administrere slutpunkter og arbejdsbelastninger, der strækker sig over et lokalt miljø og et cloudmiljø |
| [Konfigurationsstyring](/mem/configmgr/core/understand/introduction) | Brug Configuration Manager til at beskytte slutpunkter i det lokale miljø med den cloudbaserede styrke ved Defender for Endpoint |
| Lokalt script downloadet fra Microsoft 365 Defender-portalen | Brug lokale scripts på slutpunkter til at køre et pilotprojekt eller onboarde nogle få enheder |

Du kan få mere at vide om dine udrulningsindstillinger under [Planlæg din installation af Defender for Endpoint](deployment-strategy.md). Og download følgende plakat: 

[:::image type="content" source="../../media/defender-endpoint/mde-deployment-strategy.png" alt-text="Miniature af plakat for installationsstrategi":::](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)

**[Hent installationsplakaten](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)**

> [!TIP]
> Du kan finde flere detaljerede oplysninger om planlægning af udrulningen under [Planlæg din Microsoft Defender for Endpoint udrulning](deployment-strategy.md).

## <a name="set-up-your-tenant-environment"></a>Konfigurer dit lejermiljø

Konfiguration af dit lejermiljø omfatter opgaver, f.eks.:

- Bekræftelse af dine licenser
- Konfiguration af din lejer
- Konfiguration af dine proxyindstillinger (kun hvis det er nødvendigt)
- Sørg for, at sensorer fungerer korrekt, og at rapportere data til Defender for Endpoint 

Disse opgaver er inkluderet i konfigurationsfasen for Defender for Endpoint. Se [Konfigurer Defender for Endpoint](production-deployment.md).

## <a name="assign-roles-and-permissions"></a>Tildel roller og tilladelser

Hvis du vil have adgang til Microsoft 365 Defender-portalen, konfigurere indstillinger for Defender for Endpoint eller udføre opgaver, f.eks. udføre svarhandlinger på registrerede trusler, skal der tildeles de relevante tilladelser. Defender for Endpoint bruger [indbyggede roller i Azure Active Directory](/azure/active-directory/roles/permissions-reference). 

Microsoft anbefaler, at du kun tildeler brugerne det tilladelsesniveau, de har brug for til at udføre deres opgaver. Du kan tildele tilladelser ved hjælp af grundlæggende administration af tilladelser eller ved hjælp af [rollebaseret adgangskontrol](rbac.md) . 

- Med grundlæggende administration af tilladelser har globale administratorer og sikkerhedsadministratorer fuld adgang, hvorimod sikkerhedslæsere har skrivebeskyttet adgang.
- Med RBAC kan du angive flere detaljerede tilladelser via flere roller. Du kan f.eks. have sikkerhedslæsere, sikkerhedsoperatører, sikkerhedsadministratorer, slutpunktsadministratorer og meget mere.


I følgende tabel beskrives de nøgleroller, du skal overveje for Defender for Endpoint i din organisation: <br/><br/>

| Rolle | Beskrivelse |
|:---|:---|
| Globale administratorer (også kaldet globale administratorer) <br/><br/> *Begræns antallet af globale administratorer som bedste praksis.* | Globale administratorer kan udføre alle slags opgaver. Den person, der har tilmeldt dit firma til Microsoft 365 eller Microsoft Defender for Endpoint Plan 1, er som standard global administrator. <br/><br/> Globale administratorer kan få adgang til/ændre indstillinger på tværs af alle Microsoft 365 portaler, f.eks.: <br/>- Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) <br/>- Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  |
| Sikkerhedsadministratorer (også kaldet sikkerhedsadministratorer) | Sikkerhedsadministratorer kan udføre sikkerhedsoperatoropgaver plus følgende opgaver: <br/>– Overvåg sikkerhedsrelaterede politikker <br/>– Administrer sikkerhedstrusler og -beskeder <br/>- Få vist rapporter |
| Sikkerhedsoperator | Sikkerhedsoperatorer kan udføre sikkerhedslæseropgaver plus følgende opgaver: <br/>- Få vist oplysninger om registrerede trusler <br/>- Undersøg og reager på registrerede trusler  |
| Sikkerhedslæser | Sikkerhedslæsere kan udføre følgende opgaver: <br/>– Få vist sikkerhedsrelaterede politikker på tværs af Microsoft 365 tjenester <br/>– Få vist sikkerhedstrusler og -beskeder <br/>- Få vist rapporter  |


> [!TIP]
> Hvis du vil vide mere om roller i Azure Active Directory, skal du se [Tildel administrator- og ikke-administratorroller til brugere med Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal). Du kan også finde flere oplysninger om roller for Defender for Endpoint under [Rollebaseret adgangskontrol](prepare-deployment.md#role-based-access-control).

## <a name="onboard-to-defender-for-endpoint"></a>Onboard til Defender for Endpoint

Når du er klar til at onboarde din organisations slutpunkter, kan du vælge mellem flere metoder, som vist i følgende tabel: <br/><br/>

|Slutpunktsoperativsystem | Onboardingmetoder|
|---|---|
| Windows 10 | [Lokalt script (op til 10 enheder)](configure-endpoints-script.md) <br>  [Gruppepolitik](configure-endpoints-gp.md) <br>  [Enhedshåndtering Microsoft Endpoint Manager/Mobil](configure-endpoints-mdm.md) <br> [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [VDI-scripts](configure-endpoints-vdi.md)  |
| Macos | [Lokale scripts](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Mobil Enhedshåndtering](mac-install-with-other-mdm.md) |
| Ios |[Appbaseret](ios-install.md) |
| Android | [Microsoft Endpoint Manager](android-intune.md) |

Fortsæt derefter med at konfigurere din næste generation af funktioner til beskyttelse og reduktion af angrebsoverfladen.

## <a name="configure-next-generation-protection"></a>Konfigurer næste generations beskyttelse

Vi anbefaler, at du bruger [Microsoft Endpoint Manager](/mem) til at administrere organisationens enheder og sikkerhedsindstillinger, som vist på følgende billede:
 
:::image type="content" source="../../media/mde-p1/endpoint-policies.png" alt-text="Slutpunktssikkerhedspolitikker på Micorosft-Endpoint Manager-portalen" lightbox="../../media/mde-p1/endpoint-policies.png":::

Hvis du vil konfigurere din næste generation af beskyttelse i Microsoft Endpoint Manager, skal du følge disse trin:

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Vælg **Endpoint** **securityAntivirus** > , og vælg derefter en eksisterende politik. Hvis du ikke har en eksisterende politik, skal du oprette en ny politik.

3. Angiv eller rediger indstillingerne for antiviruskonfigurationen. Har du brug for hjælp? Se følgende ressourcer: <br/>

   - [Indstillinger for Windows 10 Microsoft Defender Antivirus politik i Microsoft Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-windows)
   - [Konfigurer Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

4. Når du er færdig med at angive dine indstillinger, skal du vælge **Gennemse + gem**.

## <a name="configure-your-attack-surface-reduction-capabilities"></a>Konfigurer dine funktioner til reduktion af angrebsoverfladen

Reduktion af angrebsoverfladen handler om at reducere de steder og måder, din organisation er åben for angreb på. Defender for Endpoint Plan 1 indeholder flere funktioner og funktioner, der kan hjælpe dig med at reducere dine angrebsoverflader på tværs af dine slutpunkter. Disse funktioner og egenskaber er angivet i følgende tabel: <br/><br/>

| Funktion/funktion | Beskrivelse |
|:---|:---|
| [Regler for reduktion af angrebsoverflade](#attack-surface-reduction-rules) | Konfigurer regler for reduktion af angrebsoverfladen for at begrænse softwarebaserede risikable funktionsmåder og hjælpe med at beskytte din organisation. Regler for reduktion af angrebsoverfladen er målrettet bestemte softwarefunktioner, f.eks.<br/>- Start eksekverbare filer og scripts, der forsøger at downloade eller køre filer <br/>- Kørsel af slørede eller på anden måde mistænkelige scripts <br/>- Udførelse af funktionsmåder, som apps normalt ikke initierer under normalt dag-til-dag-arbejde <br/><br/>Sådanne software adfærd er nogle gange set i legitime applikationer. Disse funktionsmåder betragtes dog ofte som risikable, fordi de ofte misbruges af hackere via malware.  |
| [Ransomware-afhjælpning](#ransomware-mitigation) | Konfigurer afhjælpning af ransomware ved at konfigurere kontrolleret mappeadgang, hvilket hjælper med at beskytte din organisations værdifulde data mod skadelige apps og trusler, f.eks. ransomware. | 
| [Enhedsstyring](#device-control) | Konfigurer indstillingerne for enhedsstyring for din organisation for at tillade eller blokere flytbare enheder (f.eks. USB-drev). | 
| [Netværksbeskyttelse](#network-protection) | Konfigurer netværksbeskyttelse for at forhindre personer i din organisation i at bruge programmer, der har adgang til farlige domæner eller skadeligt indhold på internettet. |
| [Webbeskyttelse](#web-protection) | Konfigurer beskyttelse af webtrusler for at beskytte din organisations enheder mod phishing-websteder, websteder, der udnyttes, og andre websteder, der ikke er tillid til, eller websteder med lavt omdømme. Konfigurer filtrering af webindhold for at spore og regulere adgangen til websteder baseret på deres indholdskategorier (f.eks. fritid, høj båndbredde, indhold fra voksne eller juridisk ansvar). |
| [Netværksfirewall](#network-firewall) | Konfigurer din netværksfirewall med regler, der bestemmer, hvilken netværkstrafik der må komme ind i eller ud fra organisationens enheder. |
| [Programkontrolelement](#application-control)  | Konfigurer regler for programkontrol, hvis du kun vil tillade, at programmer og processer, der er tillid til, kører på dine Windows enheder.    |

### <a name="attack-surface-reduction-rules"></a>Regler for reduktion af angrebsoverflade

Regler for reduktion af angrebsoverfladen er tilgængelige på enheder, der kører Windows. Vi anbefaler, at du bruger Microsoft Endpoint Manager som vist på følgende billede:

:::image type="content" source="../../media/mde-p1/mem-asrpolicies.png" alt-text="Regler for reduktion af angrebsoverfladen på Microsoft Endpoint Manager-portalen" lightbox="../../media/mde-p1/mem-asrpolicies.png":::

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Vælg **Endpoint securityAttack** >  **surface reduction** > **+ Create policy**.

3. Vælg **Windows 10 og nyere** for **Platform**.

4. For **Profil** skal du vælge **Regler for reduktion af angrebsoverfladen** og derefter vælge **Opret**.

5. Angiv et navn og en beskrivelse til politikken under fanen **Grundlæggende** , og vælg derefter **Næste**.

6. På fanen **Konfigurationsindstillinger** skal du udvide **Regler for reduktion af angrebsoverflade**.

7. Angiv indstillinger for hver regel, og vælg derefter **Næste**. (Du kan få flere oplysninger om, hvad hver enkelt regel gør, under [Regler for reduktion af angrebsoverfladen](attack-surface-reduction.md)). 

8. Hvis din organisation bruger områdekoder under fanen **Områdekoder** , skal du vælge **+ Vælg områdekoder** og derefter vælge de mærker, du vil bruge. Vælg derefter **Næste**. 
   
   Du kan få mere at vide om områdekoder under [Brug rollebaseret adgangskontrol (RBAC) og områdekoder til distribueret it](/mem/intune/fundamentals/scope-tags).

9. Under fanen **Tildelinger** skal du angive de brugere og grupper, som politikken skal anvendes på, og derefter vælge **Næste**. Du kan få mere at vide om tildelinger under [Tildel bruger- og enhedsprofiler i Microsoft Intune](/mem/intune/configuration/device-profile-assign).

10. Gennemse indstillingerne under fanen **Gennemse + opret** , og vælg derefter **Opret**.

> [!TIP]
> Du kan få mere at vide om regler for reduktion af angrebsoverfladen i følgende ressourcer:
> - [Brug regler for reduktion af angrebsoverfladen for at forhindre malware-infektion](attack-surface-reduction.md)
> - [Vis listen over regler for reduktion af angrebsoverfladen](attack-surface-reduction-rules-reference.md)
> - [Udrulning af regler for reduktion af angrebsoverfladen Trin 3: Implementer ASR-regler](attack-surface-reduction-rules-deployment-implement.md)

### <a name="ransomware-mitigation"></a>Ransomware-afhjælpning

Du får ransomware-afhjælpning via [kontrolleret mappeadgang](controlled-folders.md#what-is-controlled-folder-access), hvilket kun giver apps, der er tillid til, adgang til beskyttede mapper på dine slutpunkter. 

Vi anbefaler, at du bruger Microsoft Endpoint Manager til at konfigurere kontrolleret mappeadgang.

:::image type="content" source="../../media/mde-p1/mem-asrpolicies.png" alt-text="ASR-politikker på Microsoft Endpoint Manager-portalen" lightbox="../../media/mde-p1/mem-asrpolicies.png":::

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på. 

2. Vælg **Endpoint Security**, og vælg derefter **Reduktion af angrebsoverflade**.

3. Vælg **+ Opret politik**. 

4. Vælg **Windows 10 og nyere** for **Platform**, og vælg **Regler for reduktion af angrebsoverfladen** for **Profil**. Vælg derefter **Opret**. 

5. Navngiv politikken under fanen **Grundlæggende** , og tilføj en beskrivelse. Vælg **Næste**. 

6. Rul ned til bunden i afsnittet **Regler for reduktion af angrebsoverfladen** under fanen **Konfigurationsindstillinger**. På rullelisten **Aktivér mappebeskyttelse** skal du vælge **Aktivér**. Du kan eventuelt angive disse andre indstillinger:

   - Ud for **Liste over yderligere mapper, der skal beskyttes**, skal du vælge rullemenuen og derefter tilføje mapper, der skal beskyttes.
   - Ud for **Liste over apps, der har adgang til beskyttede mapper**, skal du vælge rullemenuen og derefter tilføje apps, der skal have adgang til beskyttede mapper.
   - Ud for **Udelad filer og stier fra regler for reduktion af angrebsoverfladen** skal du vælge rullemenuen og derefter tilføje de filer og stier, der skal udelukkes fra reglerne for reduktion af angrebsoverfladen.

   Vælg derefter **Næste**.

7. Hvis din organisation bruger områdekoder under fanen **Områdekoder** , skal du vælge **+ Vælg områdekoder** og derefter vælge de mærker, du vil bruge. Vælg derefter **Næste**. 
   
   Du kan få mere at vide om områdekoder under [Brug rollebaseret adgangskontrol (RBAC) og områdekoder til distribueret it](/mem/intune/fundamentals/scope-tags).

8. Under fanen **Tildelinger** skal du vælge **Tilføj alle brugere** og **+ Tilføj alle enheder** og derefter vælge **Næste**. Du kan alternativt angive bestemte grupper af brugere eller enheder.

9. Gennemse **+ opret under fanen Gennemse + opret** , gennemse indstillingerne for din politik, og vælg derefter **Opret**. Politikken anvendes på alle slutpunkter, der blev onboardet til Defender for Endpoint om kort tid.

### <a name="device-control"></a>Enhedsstyring

Du kan konfigurere Defender for Endpoint til at blokere eller tillade flytbare enheder og filer på flytbare enheder. Vi anbefaler, at du bruger Microsoft Endpoint Manager til at konfigurere dine indstillinger for enhedskontrol.

:::image type="content" source="../../media/mde-p1/mem-admintemplates.png" alt-text="Microsoft Endpoint Manager administrative skabeloner" lightbox="../../media/mde-p1/mem-admintemplates.png":::

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på. 

2. Vælg **EnhederKonfigurationsprofilerOpret** >  >  **profil**.

3. Vælg **Windows 10 og nyere** for **Platform**, og vælg **Skabeloner** som **Profiltype**. 

   Under **Skabelonnavn** skal du vælge **Administrative skabeloner** og derefter vælge **Opret**. 

4. Navngiv politikken under fanen **Grundlæggende** , og tilføj en beskrivelse. Vælg **Næste**. 

5. Vælg **Alle Indstillinger** under fanen **Konfigurationsindstillinger**. Skriv derefter alle de indstillinger, der gælder for flytbare enheder, `Removable` i søgefeltet.

6. Vælg et element på listen, f.eks **. Alle Flytbare Storage klasser: Afvis alle adgang** for at åbne dens pop op-rude. Pop op-vinduet for hver indstilling forklarer, hvad der sker, når det er aktiveret, deaktiveret eller ikke konfigureret. Vælg en indstilling, og vælg derefter **OK**. 

7. Gentag trin 6 for hver indstilling, du vil konfigurere. Vælg derefter **Næste**.

8. Hvis din organisation bruger områdekoder under fanen **Områdekoder** , skal du vælge **+ Vælg områdekoder** og derefter vælge de mærker, du vil bruge. Vælg derefter **Næste**. 
   
   Du kan få mere at vide om områdekoder under [Brug rollebaseret adgangskontrol (RBAC) og områdekoder til distribueret it](/mem/intune/fundamentals/scope-tags).

9. Under fanen **Tildelinger** skal du vælge **Tilføj alle brugere** og **+ Tilføj alle enheder** og derefter vælge **Næste**. Du kan alternativt angive bestemte grupper af brugere eller enheder.

10. Gennemse **+ opret under fanen Gennemse + opret** , gennemse indstillingerne for din politik, og vælg derefter **Opret**. Politikken anvendes på alle slutpunkter, der blev onboardet til Defender for Endpoint om kort tid.

> [!TIP]
> Du kan få flere oplysninger under [Sådan styrer du USB-enheder og andre flytbare medier ved hjælp af Microsoft Defender for Endpoint](control-usb-devices-using-intune.md).

### <a name="network-protection"></a>Netværksbeskyttelse

Med netværksbeskyttelse kan du hjælpe med at beskytte din organisation mod farlige domæner, der kan hoste phishing-svindel, udnyttelser og andet skadeligt indhold på internettet. Vi anbefaler, at du bruger Microsoft Endpoint Manager til at aktivere netværksbeskyttelse.

:::image type="content" source="../../media/mde-p1/mem-endpointprotectionprofile.png" alt-text="Profil til beskyttelse af slutpunkter på Microsoft Endpoint Manager-portalen" lightbox="../../media/mde-p1/mem-endpointprotectionprofile.png":::

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på. 

2. Vælg **EnhederKonfigurationsprofilerOpret** >  >  **profil**.

3. Vælg **Windows 10 og nyere** for **Platform**, og vælg **Skabeloner** som **Profiltype**. 

   Under **Skabelonnavn** skal du vælge **Slutpunktsbeskyttelse** og derefter vælge **Opret**. 

4. Navngiv politikken under fanen **Grundlæggende** , og tilføj en beskrivelse. Vælg **Næste**. 

5. Udvid **Microsoft Defender Exploit Guard** under fanen **Konfigurationsindstillinger**, og udvid derefter **Netværksfiltrering**.

   Angiv **Netværksbeskyttelse** til **Aktivér**. Du kan alternativt vælge **Overvågning** for at se, hvordan netværksbeskyttelse fungerer i dit miljø i starten.

   Vælg derefter **Næste**.

6. Under fanen **Tildelinger** skal du vælge **Tilføj alle brugere** og **+ Tilføj alle enheder** og derefter vælge **Næste**. Du kan alternativt angive bestemte grupper af brugere eller enheder.

7. Konfigurer en regel under fanen **Anvendelighedsregler** . Den profil, du konfigurerer, anvendes kun på enheder, der opfylder de kombinerede kriterier, du angiver. 

   Du kan f.eks. vælge at tildele politikken til slutpunkter, der kun kører en bestemt operativsystemversion.

   Vælg derefter **Næste**. 

8. Gennemse **+ opret under fanen Gennemse + opret** , gennemse indstillingerne for din politik, og vælg derefter **Opret**. Politikken anvendes på alle slutpunkter, der blev onboardet til Defender for Endpoint om kort tid.

> [!TIP]
> Du kan bruge andre metoder, f.eks. Windows PowerShell eller Gruppepolitik, til at aktivere netværksbeskyttelse. Du kan få mere at vide under [Slå netværksbeskyttelse til](enable-network-protection.md).

### <a name="web-protection"></a>Webbeskyttelse

Med webbeskyttelse kan du beskytte din organisations enheder mod webtrusler og uønsket indhold. Din webbeskyttelse omfatter [beskyttelse mod webtrusler](#configure-web-threat-protection) og [filtrering af webindhold](#configure-web-content-filtering). Konfigurer begge sæt egenskaber. Vi anbefaler, at du bruger Microsoft Endpoint Manager til at konfigurere indstillingerne for webbeskyttelse.

#### <a name="configure-web-threat-protection"></a>Konfigurer beskyttelse mod webtrussel

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.
 
2. Vælg **Endpoint securityAttack** >  **surface reduction (Reduktion af overflade**), og vælg derefter **+ Opret politik**.

3. Vælg en platform, f.eks **. Windows 10 og nyere**, vælg profilen **Webbeskyttelse**, og vælg derefter **Opret**. 

4. Angiv et navn og en beskrivelse under fanen **Grundlæggende** , og vælg derefter **Næste**.

5. På fanen **Konfigurationsindstillinger** skal du udvide **Webbeskyttelse**, angive indstillingerne i følgende tabel og derefter vælge **Næste**. <br/><br/>

   | Indstilling | Anbefaling |
   |:---|:---|
   | **Aktivér netværksbeskyttelse** | Indstillet til **Aktiveret**. Forhindrer brugere i at besøge skadelige websteder eller domæner. <br/><br/>Du kan også angive netværksbeskyttelse til **overvågningstilstand** for at se, hvordan det fungerer i dit miljø. I overvågningstilstand forhindrer netværksbeskyttelse ikke brugere i at besøge websteder eller domæner, men det sporer registreringer som hændelser. |
   | **Kræv SmartScreen til Den ældre version af Microsoft Edge** | Indstillet til **Ja**. Hjælper med at beskytte brugerne mod potentielle phishing-svindel og skadelig software. |
   | **Bloker adgang til skadeligt websted** | Indstillet til **Ja**. Forhindrer brugere i at tilsidesætte advarsler om potentielt skadelige websteder. |
   | **Bloker ikke-bekræftet fildownload** | Indstillet til **Ja**. Forhindrer brugerne i at omgå advarslerne og hente ikke-bekræftede filer. |

6. Hvis din organisation bruger områdekoder under fanen **Områdekoder** , skal du vælge **+ Vælg områdekoder** og derefter vælge de mærker, du vil bruge. Vælg derefter **Næste**. 
   
   Du kan få mere at vide om områdekoder under [Brug rollebaseret adgangskontrol (RBAC) og områdekoder til distribueret it](/mem/intune/fundamentals/scope-tags).

7. Under fanen **Tildelinger** skal du angive de brugere og enheder, der skal modtage webbeskyttelsespolitikken, og derefter vælge **Næste**.

8. Gennemse dine politikindstillinger under fanen **Gennemse + opret** , og vælg derefter **Opret**.

> [!TIP]
> Hvis du vil vide mere om beskyttelse mod webtrusler, skal [du se Beskyt din organisation mod webtrusler](web-threat-protection.md).

#### <a name="configure-web-content-filtering"></a>Konfigurer filtrering af webindhold

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com/](https://security.microsoft.com/)), og log på.

2. Vælg **Indstillinger** >  **Slutpunkter**.

3. Under **Regler** skal du vælge **Filtrering af webindhold** og derefter vælge **+ Tilføj politik**.

4. I pop op-vinduet **Tilføj politik** under fanen **Generelt** skal du angive et navn til politikken og derefter vælge **Næste**.

5. I **Blokerede kategorier** skal du vælge en eller flere kategorier, du vil blokere, og derefter vælge **Næste**.

6. Under fanen **Område** skal du vælge de enhedsgrupper, du vil modtage denne politik på, og derefter vælge **Næste**.

7. Gennemse dine politikindstillinger under fanen **Oversigt** , og vælg derefter **Gem**.

> [!TIP]
> Hvis du vil vide mere om konfiguration af filtrering af webindhold, skal du se [Filtrering af webindhold](web-content-filtering.md).

### <a name="network-firewall"></a>Netværksfirewall

Netværksfirewall hjælper med at reducere risikoen for netværkssikkerhedstrusler. Dit sikkerhedsteam kan angive regler, der bestemmer, hvilken trafik der må overføres til eller fra organisationens enheder. Vi anbefaler, at du bruger Microsoft Endpoint Manager til at konfigurere din netværksfirewall. 

:::image type="content" source="../../media/mde-p1/mem-firewallpolicy.png" alt-text="Firewallpolitik på Microsoft Endpoint Manager-portalen" lightbox="../../media/mde-p1/mem-firewallpolicy.png":::

Følg disse trin for at konfigurere grundlæggende firewallindstillinger:

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Vælg **Endpoint** **securityFirewall** > , og vælg derefter **+ Opret politik**.

3. Vælg en platform, f.eks **. Windows 10 og nyere**, vælg profilen **Microsoft Defender Firewall**, og vælg derefter **Opret**. 

4. Angiv et navn og en beskrivelse under fanen **Grundlæggende** , og vælg derefter **Næste**.

5. Udvid **Microsoft Defender Firewall**, og rul derefter ned til bunden af listen.

6. Angiv hver af følgende indstillinger til **Ja**:

   - **Slå Microsoft Defender Firewall til for domænenetværk** 
   - **Slå Microsoft Defender Firewall til for private netværk**
   - **Slå Microsoft Defender Firewall til for offentlige netværk**
   
   Gennemse listen over indstillinger under hvert domænenetværk, private netværk og offentlige netværk. Du kan lade dem være **indstillet til Ikke konfigureret** eller ændre dem, så de passer til organisationens behov.

   Vælg derefter **Næste**.

7. Hvis din organisation bruger områdekoder under fanen **Områdekoder** , skal du vælge **+ Vælg områdekoder** og derefter vælge de mærker, du vil bruge. Vælg derefter **Næste**. 
   
   Du kan få mere at vide om områdekoder under [Brug rollebaseret adgangskontrol (RBAC) og områdekoder til distribueret it](/mem/intune/fundamentals/scope-tags).

8. Under fanen **Tildelinger** skal du vælge **Tilføj alle brugere** og **+ Tilføj alle enheder** og derefter vælge **Næste**. Du kan alternativt angive bestemte grupper af brugere eller enheder.

9. Gennemse dine politikindstillinger under fanen **Gennemse + opret** , og vælg derefter **Opret**.

> [!TIP]
> Firewallindstillinger er detaljerede og kan virke komplekse. Se [Bedste praksis for konfiguration af Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/best-practices-configuring).

### <a name="application-control"></a>Programkontrolelement

WDAC (Windows Defender Application Control) hjælper med at beskytte dine Windows slutpunkter ved kun at tillade kørsel af programmer og processer, der er tillid til. De fleste organisationer brugte en faseinddelt udrulning af WDAC. Det betyder, at de fleste organisationer ikke udruller WDAC på tværs af alle Windows slutpunkter først. Afhængigt af om din organisations Windows slutpunkter er fuldt administrerede, let administrerede eller "Medbring din egen enhed", kan du installere WDAC på alle eller nogle slutpunkter.

Hvis du vil have hjælp til at planlægge din WDAC-installation, skal du se følgende ressourcer:

- [Programkontrol for Windows](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)

- [Windows Defender beslutninger om design af politikker for programkontrol](/windows/security/threat-protection/windows-defender-application-control/understand-windows-defender-application-control-policy-design-decisions)

- [Windows Defender installation af Application Control i forskellige scenarier: typer af enheder](/windows/security/threat-protection/windows-defender-application-control/types-of-devices)

## <a name="next-steps"></a>Næste trin

Nu, hvor du har gennemgået konfigurationsprocessen, er dit næste trin at komme i gang med at bruge Defender for Endpoint. 

- [Kom i gang med Defender for Endpoint Plan 1](mde-plan1-getting-started.md)
