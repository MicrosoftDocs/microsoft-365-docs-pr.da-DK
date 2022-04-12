---
title: Beskyt sikkerhedsindstillinger med manipulationsbeskyttelse
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: Brug beskyttelse mod ændring for at forhindre, at skadelige apps ændrer vigtige sikkerhedsindstillinger.
keywords: malware, defender, antivirus, manipulationsbeskyttelse
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom:
- nextgen
- admindeeplinkDEFENDER
ms.technology: mde
ms.date: 04/07/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: ccf72b1f7e5625f3b3b9599a50d734a7316b8659
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780253"
---
# <a name="protect-security-settings-with-tamper-protection"></a>Beskyt sikkerhedsindstillinger med manipulationsbeskyttelse

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Tamperbeskyttelse er tilgængelig for enheder, der kører en af følgende versioner af Windows:

- Windows 11
- Windows 11 Enterprise flere sessioner 
- Windows 10
- Windows 10 Enterprise flere sessioner
- Windows Server 2022
- Windows Server 2019
- Windows Server, version 1803 eller nyere
- Windows Server 2016
- Windows Server 2012 R2

> [!NOTE]
> Tamper-beskyttelse i Windows Server 2012 R2 er tilgængelig til enheder, der er onboardet ved hjælp af den moderne unified løsningspakke. Du kan få flere oplysninger under [Onboard Windows-servere til tjenesten Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/configure-server-endpoints).


## <a name="overview"></a>Oversigt

Under nogle former for cyberangreb forsøger dårlige aktører at deaktivere sikkerhedsfunktioner, f.eks. antivirusbeskyttelse, på dine maskiner. Dårlige aktører vil gerne deaktivere dine sikkerhedsfunktioner for at få lettere adgang til dine data, installere malware eller på anden måde udnytte dine data, identitet og enheder. Ændringsbeskyttelse hjælper med at forhindre, at denne type ting sker. Med manipulationsbeskyttelse forhindres ondsindede apps i at træffe handlinger som f.eks.:

- Deaktivering af beskyttelse mod virus og trusler
- Deaktivering af beskyttelse i realtid
- Deaktivering af overvågning af funktionsmåde
- Deaktivering af antivirus (f.eks. IOfficeAntivirus (IOAV))
- Deaktivering af skybaseret beskyttelse
- Fjerner sikkerhedsintelligensopdateringer
- Deaktivering af automatiske handlinger på registrerede trusler

### <a name="how-it-works"></a>Sådan fungerer det

Ændringsbeskyttelse låser i bund og grund Microsoft Defender Antivirus til dens sikre standardværdier og forhindrer, at dine sikkerhedsindstillinger ændres via apps og metoder, f.eks.:

- Konfiguration af indstillinger i Registreringseditor på din Windows enhed
- Ændring af indstillinger via PowerShell-cmdlet'er
- Redigering eller fjernelse af sikkerhedsindstillinger via Gruppepolitik

Ændringsbeskyttelse forhindrer dig ikke i at få vist dine sikkerhedsindstillinger. Og ændringsbeskyttelse påvirker ikke, hvordan antivirusprogrammer, der ikke er fra Microsoft, registreres i Windows Sikkerhed-appen. Hvis din organisation bruger Windows 10 Enterprise E5, kan individuelle brugere ikke ændre indstillingen for beskyttelse mod ændring. I disse tilfælde administreres ændringsbeskyttelse af dit sikkerhedsteam.

### <a name="what-do-you-want-to-do"></a>Hvad vil du foretage dig?

|Sådan udfører du denne opgave...|Se dette afsnit...|
|---|---|
|Administrer beskyttelse mod ændring på tværs af din lejer <p> Brug Microsoft 365 Defender-portalen til at slå ændringsbeskyttelse til eller fra|[Administrer ændringsbeskyttelse for din organisation ved hjælp af Microsoft 365 Defender](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)|
|Finjuster beskyttelsesindstillinger for ændring i din organisation <p> Brug Intune (Microsoft Endpoint Manager) til at slå beskyttelse mod manipulation til eller fra. Du kan konfigurere manipulationsbeskyttelse for nogle eller alle brugere med denne metode.|[Administrer ændringsbeskyttelse for din organisation ved hjælp af Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)|
|Slå ændringsbeskyttelse til (eller fra) for din organisation med Configuration Manager|[Administrer manipulationsbeskyttelse for din organisation ved hjælp af lejertilknyttelse med Configuration Manager, version 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)|
|Slå manipulationsbeskyttelse til (eller fra) for en individuel enhed|[Administrer beskyttelse mod manipulation på en individuel enhed](#manage-tamper-protection-on-an-individual-device)|
|Få vist oplysninger om forsøg på manipulation på enheder|[Få vist oplysninger om manipulationsforsøg](#view-information-about-tampering-attempts)|
|Gennemse dine sikkerhedsanbefalinger|[Gennemse sikkerhedsanbefalinger](#review-your-security-recommendations)|
|Gennemse listen over ofte stillede spørgsmål|[Gennemse ofte stillede spørgsmål](#view-information-about-tampering-attempts)|

## <a name="potential-dependency-on-cloud-protection"></a>Potentiel afhængighed af cloudbeskyttelse  
  
Afhængigt af den metode eller det administrationsværktøj, du bruger til at aktivere manipulationsbeskyttelse, kan der være en afhængighed af [skybaseret beskyttelse](cloud-protection-microsoft-defender-antivirus.md) Cloudbaseret beskyttelse kaldes også cloudbeskyttelse eller Microsoft Advanced Protection Service (MAPS).

Følgende tabel indeholder oplysninger om metoder, værktøjer og afhængigheder.

| Sådan aktiveres manipulationsbeskyttelse | Afhængighed af cloudbeskyttelse |
|---|---|
|Microsoft Intune|Nej|
|Microsoft Endpoint Configuration Manager med lejer vedhæft|Nej|
|Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com))|Ja|

## <a name="manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal"></a>Administrer ændringsbeskyttelse for din organisation ved hjælp af Microsoft 365 Defender-portalen

Manipulationsbeskyttelse kan slås til eller fra for din lejer ved hjælp af Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)). Her er et par punkter, du skal være opmærksom på:

- I øjeblikket er muligheden for at administrere beskyttelse mod manipulation på Microsoft 365 Defender-portalen aktiveret som standard for nye udrulninger. I forbindelse med eksisterende udrulninger er der mulighed for at ændre beskyttelse via tilvalg. Hvis du vil tilmelde dig, skal du vælge **Indstillinger** **Endpoints** \> **Advanced features** \> **Tamper Protection** på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalen Microsoft 365 Defender</a>\>.
- Når du bruger Microsoft 365 Defender-portalen til at administrere beskyttelse mod manipulation, behøver du ikke at bruge Intune eller lejertilknyttelsesmetoden.
- Når du administrerer beskyttelse mod ændring på Microsoft 365 Defender portalen, anvendes indstillingen for hele lejeren, hvilket påvirker alle de enheder, der kører Windows 10, Windows 10 Enterprise flere sessioner, Windows 11 Windows 11 Enterprise  multi-session, Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 eller Windows Server 2022. Brug enten [Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager) eller [Configuration Manager med lejertilknyttelse](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006) for at finjustere manipulationsbeskyttelsen (f.eks. at have manipulationsbeskyttelse på nogle enheder, men deaktivere den for andre).
- Hvis du har et hybridmiljø, har de indstillinger for beskyttelse af ændringer, der er konfigureret i Intune højere prioritet end de indstillinger, der er konfigureret i Microsoft 365 Defender-portalen.

### <a name="requirements-for-managing-tamper-protection-in-the-microsoft-365-defender-portal"></a>Krav til administration af manipulationsbeskyttelse på Microsoft 365 Defender-portalen

- Du skal have tildelt de nødvendige [tilladelser](/microsoft-365/security/defender-endpoint/assign-portal-access) , f.eks. global administrator, sikkerhedsadministrator eller sikkerhedshandlinger.

- Dine Windows enheder skal køre en af følgende versioner af Windows:
  
  - Windows 11
  - Windows 11 Enterprise flere sessioner 
  - Windows 10
  - Windows 10 Enterprise flere sessioner
  - Windows Server 2022
  - Windows Server 2019
  - Windows Server, version 1803 eller nyere
  - Windows Server 2016
  - Windows Server 2012 R2

Du kan få flere oplysninger om udgivelser [under Windows 10 udgivelsesoplysninger](/windows/release-health/release-information).

- Dine enheder skal [være onboardet til Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/onboarding).
- Dine enheder skal bruge platformversionen `4.18.2010.7` for antimalware (eller nyere) og versionen `1.1.17600.5` af antimalwareprogrammet (eller nyere). ([Administrer Microsoft Defender Antivirus opdateringer, og anvend oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md)).
- [Skybaseret beskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md) skal være aktiveret.

> [!NOTE]
> Når manipulationsbeskyttelse er aktiveret via Microsoft 365 Defender-portalen, kræves skybaseret beskyttelse, så den aktiverede tilstand for manipulationsbeskyttelse kan styres.  
> Fra og med opdateringen fra november 2021 (platformversion`4.18.2111.5`), hvis skybaseret beskyttelse ikke er slået til for en enhed, og ændringsbeskyttelse er slået til på Microsoft 365 Defender portal, aktiveres skybaseret beskyttelse automatisk for den pågældende enhed sammen med manipulationsbeskyttelse.   

### <a name="turn-tamper-protection-on-or-off-in-the-microsoft-365-defender-portal"></a>Slå manipulationsbeskyttelse til (eller fra) på Microsoft 365 Defender-portalen

:::image type="content" source="../../media/mde-turn-tamperprotectionon.png" alt-text="Slå manipulationsbeskyttelse til på Microsoft 365 Defender-portalen" lightbox="../../media/mde-turn-tamperprotectionon.png":::

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Indstillinger** \> **slutpunkter**.

3. Gå til **Generelle** \> **avancerede funktioner**, og slå derefter ændringsbeskyttelse til.

## <a name="manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager"></a>Administrer ændringsbeskyttelse for din organisation ved hjælp af Microsoft Endpoint Manager

Hvis din organisation bruger Microsoft Endpoint Manager (MEM), kan du slå ændringsbeskyttelse til (eller fra) for din organisation i Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Brug Intune, når du vil finjustere beskyttelsesindstillinger for ændring. Hvis du f.eks. vil aktivere manipulationsbeskyttelse på nogle enheder, men ikke alle, skal du bruge Intune.

### <a name="requirements-for-managing-tamper-protection-in-endpoint-manager"></a>Krav til administration af manipulationsbeskyttelse i Endpoint Manager

- Dine enheder skal [være onboardet til Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/onboarding).
- Du skal have tildelt de nødvendige [tilladelser](/microsoft-365/security/defender-endpoint/assign-portal-access) , f.eks. global administrator, sikkerhedsadministrator eller sikkerhedshandlinger.
- Din organisation bruger [Microsoft Endpoint Manager til at administrere enheder](/mem/endpoint-manager-getting-started). (Microsoft Endpoint Manager(MEM)-licenser er påkrævet. MEM indgår i Microsoft 365 E3/E5, Enterprise Mobility + Security E3/E5, Microsoft 365 Business Premium, Microsoft 365 F1/F3, Microsoft 365  Government G3/G5 og tilsvarende uddannelseslicenser.)
- Dine Windows enheder skal køre Windows 11 eller Windows 10 [1709](/windows/release-health/status-windows-10-1709), [1803](/windows/release-health/status-windows-10-1803), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) eller nyere. (Du kan få flere oplysninger om udgivelser [under Windows 10 udgivelsesoplysninger](/windows/release-health/release-information)).
- Du skal bruge Windows sikkerhed, hvor [security intelligence](https://www.microsoft.com/wdsi/definitions) er opdateret til version 1.287.60.0 (eller nyere).
- Dine enheder skal bruge platformversion 4.18.1906.3 (eller nyere) og version 4.18.1906.3 (eller nyere) og antimalwaremotorversion `1.1.15500.X` (eller nyere). ([Administrer Microsoft Defender Antivirus opdateringer, og anvend oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md)).

### <a name="turn-tamper-protection-on-or-off-in-microsoft-endpoint-manager"></a>Slå manipulationsbeskyttelse til (eller fra) i Microsoft Endpoint Manager

:::image type="content" source="images/turnontamperprotectinmem.png" alt-text="Slå manipulationsbeskyttelse til med Intune" lightbox="images/turnontamperprotectinmem.png":::

1. I [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431) skal du gå til **Endpoint security** \> **Antivirus** og derefter vælge **+ Opret politik**.

   - Vælg **Windows 10 og nyere** på listen **Platform**.
   - Vælg **Windows Sikkerhed oplevelse** på listen **Profil**.

2. Opret en profil, der indeholder følgende indstilling:

    - **Aktivér beskyttelse mod ændring for at forhindre, at Microsoft Defender deaktiveres: Aktivér**

3. Tildel profilen til en eller flere grupper.
 
### <a name="manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006"></a>Administrer manipulationsbeskyttelse for din organisation med Configuration Manager, version 2006

Hvis du bruger [version 2006 af Configuration Manager](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2006), kan du administrere indstillinger for beskyttelse af Windows 10, Windows 10 Enterprise flere sessioner, Windows 11, Windows 11 Enterprise flere sessioner Windows  Server 2012 R2, Windows Server 2016, Windows Server 2019 og Windows Server 2022 ved hjælp af en metode, der kaldes *lejertilknyt.* Vedhæfting af lejer kan du synkronisere dine Configuration Manager enheder, der kun er i det lokale miljø, til Microsoft Endpoint Manager Administration og derefter levere politikker for konfiguration af slutpunktssikkerhed til samlinger i det lokale miljø & enheder.

> [!NOTE]
> Proceduren kan bruges til at udvide beskyttelse mod manipulation til enheder, der kører Windows 10, Windows 10 Enterprise multisession, Windows 11, Windows 11 Enterprise multisession, Windows Server 2019 og Windows Server 2022. Sørg for at gennemse forudsætningerne og andre oplysninger i de ressourcer, der er nævnt i denne procedure. For Windows Server 2012 R2 kræves den moderne, samlede løsning [version 2203 af Configuration Manager](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2203).

1. Konfigurer tilknytning af lejer. Du kan få mere at vide under [Kom i gang: Opret og installer sikkerhedspolitikker for slutpunkter fra Administration](/mem/configmgr/tenant-attach/endpoint-security-get-started).

2. I [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431) skal du gå til **Endpoint security** \> **Antivirus** og derefter vælge **+ Opret politik**.

   - På listen **Platform** skal du vælge **Windows 10, Windows 11 og Windows Server (ConfigMgr)**.
   - Vælg **Windows Sikkerhed oplevelse (prøveversion)** på listen **Profil**.

3. Installér politikken på din enhedsgruppe.

#### <a name="need-help-with-this-method"></a>Har du brug for hjælp til denne metode?

Se følgende ressourcer:

- [Indstillinger til profilen for Windows Sikkerhed oplevelse i Microsoft Intune](/mem/intune/protect/antivirus-security-experience-windows-settings)
- [Tech Community-blog: Meddelelse om ændringsbeskyttelse for klienter med tilknytning til Configuration Manager lejer](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

## <a name="manage-tamper-protection-on-an-individual-device"></a>Administrer beskyttelse mod manipulation på en individuel enhed

> [!NOTE]
> Ændringsbeskyttelse blokerer forsøg på at ændre Microsoft Defender Antivirus indstillinger via registreringsdatabasen.
>
> Hvis du vil sikre, at ændringsbeskyttelse ikke forstyrrer ikke-Microsoft-sikkerhedsprodukter eller virksomhedsinstallationsscripts, der ændrer disse indstillinger, skal du gå til **Windows Sikkerhed** og opdatere **Sikkerhedsintelligens** til version 1.287.60.0 eller nyere. (Se [Opdateringer til sikkerhedsintelligens](https://www.microsoft.com/wdsi/definitions)). Når du har foretaget denne opdatering, beskytter beskyttelse mod ændring fortsat dine indstillinger i registreringsdatabasen, og logge forsøger at ændre dem uden at returnere fejl.

Hvis du er privat bruger, eller hvis du ikke er underlagt indstillinger, der administreres af et sikkerhedsteam, kan du bruge appen Windows Sikkerhed til at administrere beskyttelse mod ændring. Du skal have de nødvendige administratortilladelser på enheden for at ændre sikkerhedsindstillingerne, f.eks. ændring af beskyttelse.

Her er, hvad du kan se i appen Windows Sikkerhed:

:::image type="content" source="images/tamperprotectionturnedon.png" alt-text="Slå manipulationsbeskyttelse til i Windows 10 Home" lightbox="images/tamperprotectionturnedon.png":::

1. Vælg **Start**, og begynd at skrive *Sikkerhed*. Vælg **Windows Sikkerhed** i søgeresultaterne.

2. Vælg **Indstillinger for virus & trusselsbeskyttelse** \> **Virus & trusselsbeskyttelse**.

3. Indstil **Tamper Protection** til **Til** eller **Fra**.

## <a name="are-you-using-windows-server-2012-r2-2016-or-windows-version-1709-1803-or-1809"></a>Bruger du Windows Server 2012 R2, 2016 eller Windows version 1709, 1803 eller 1809?

Hvis du bruger Windows Server 2012 R2 ved hjælp af den moderne samlede løsning, Windows Server 2016, Windows 10 version 1709, 1803 eller [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019), kan du ikke se **Tamper Protection** i Windows Sikkerhed-appen. Du kan i stedet bruge PowerShell til at afgøre, om beskyttelse mod ændring er aktiveret.

På Windows Server 2016 afspejler appen Indstillinger ikke nøjagtigt status for beskyttelse i realtid, når beskyttelse mod ændring er aktiveret.

#### <a name="use-powershell-to-determine-whether-tamper-protection-and-real-time-protection-are-turned-on"></a>Brug PowerShell til at afgøre, om beskyttelse mod ændring og beskyttelse i realtid er slået til

1. Åbn appen Windows PowerShell.

2. Brug [PowerShell-cmdlet'en Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus?preserve-view=true&view=win10-ps) .

3. Søg efter `IsTamperProtected` eller `RealTimeProtectionEnabled`på listen over resultater. (Værdien *true* betyder, at ændringsbeskyttelse er aktiveret).

## <a name="view-information-about-tampering-attempts"></a>Få vist oplysninger om manipulationsforsøg

Manipulationsforsøg indikerer typisk større cyberangreb. Forkerte aktører forsøger at ændre sikkerhedsindstillingerne for at bevare og forblive uopdaget. Hvis du er en del af organisationens sikkerhedsteam, kan du få vist oplysninger om sådanne forsøg og derefter udføre de nødvendige handlinger for at afhjælpe trusler.

Når der registreres et forsøg på manipulation, udløses der en besked på [Microsoft 365 Defender-portalen](/microsoft-365/security/defender-endpoint/portal-overview) ([https://security.microsoft.com](https://security.microsoft.com)).

:::image type="content" source="images/tamperattemptalert.png" alt-text="Portalen Microsoft 365 Defender" lightbox="images/tamperattemptalert.png":::

Ved hjælp af [slutpunktsregistrering og -svar](overview-endpoint-detection-response.md) og [avancerede jagtfunktioner](advanced-hunting-overview.md) i Microsoft Defender for Endpoint kan dit sikkerhedsteam undersøge og løse sådanne forsøg.

## <a name="review-your-security-recommendations"></a>Gennemse dine sikkerhedsanbefalinger

Manipulationsbeskyttelse kan integreres med [threat & funktionaliteten til administration af sårbarheder](next-gen-threat-and-vuln-mgt.md) . [Sikkerhedsanbefalinger](tvm-security-recommendation.md) omfatter sikring af, at beskyttelse mod manipulation er slået til. Du kan f.eks. søge efter *ændring*. I resultaterne kan du vælge **Slå Tamper Protection** til for at få mere at vide og slå den til.

:::image type="content" source="images/tamperprotectsecurityrecos.png" alt-text="Aktivering af manipulationsbeskyttelse på Microsoft Defender Security Center-portalen" lightbox="images/tamperprotectsecurityrecos.png":::

Hvis du vil vide mere om administration af trussel & sårbarheder, skal [du se Dashboardindsigt – Håndtering af trusler og sikkerhedsrisici](tvm-dashboard-insights.md#dashboard-insights---threat-and-vulnerability-management).

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="on-which-versions-of-windows-can-i-configure-tamper-protection"></a>I hvilke versioner af Windows kan jeg konfigurere beskyttelse mod ændring?

- Windows 11
- Windows 11 Enterprise flere sessioner
- Windows 10 OS [1709](/windows/release-health/status-windows-10-1709), [1803](/windows/release-health/status-windows-10-1803), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) eller nyere sammen med [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint).
- Windows 10 Enterprise flere sessioner
  
Hvis du bruger Configuration Manager version 2006 med lejertilknyttelse, kan ændringsbeskyttelse udvides til Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 og Windows Server 2022. Se [Lejertilknyt: Opret og installér politikken for slutpunktssikkerhed Antivirus fra Administration (prøveversion)](/mem/configmgr/tenant-attach/deploy-antivirus-policy).

### <a name="will-tamper-protection-affect-non-microsoft-antivirus-registration-in-the-windows-security-app"></a>Vil ændringsbeskyttelse påvirke registreringen af antivirusprogrammer, der ikke er fra Microsoft, i Windows Sikkerhed-appen?

Nej. Antivirustilbud, der ikke er fra Microsoft, vil fortsat blive registreret i Windows Sikkerhed-programmet.

### <a name="what-happens-if-microsoft-defender-antivirus-is-not-active-on-a-device"></a>Hvad sker der, hvis Microsoft Defender Antivirus ikke er aktiv på en enhed?

Enheder, der er onboardet til Microsoft Defender for Endpoint, har Microsoft Defender Antivirus kørende i passiv tilstand. I disse tilfælde vil beskyttelse mod manipulation fortsat beskytte tjenesten og dens funktioner.

### <a name="how-do-i-turn-tamper-protection-on-or-off"></a>Hvordan gør jeg slå beskyttelse mod manipulation til eller fra?

Hvis du er privat bruger, skal du se [Administrer beskyttelse mod manipulation på en individuel enhed](#manage-tamper-protection-on-an-individual-device).

Hvis du er en organisation, der bruger [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint), bør du kunne administrere beskyttelse mod ændring i Intune på samme måde som med andre funktioner til beskyttelse af slutpunkter. Se følgende afsnit i denne artikel:

- [Administrer ændringsbeskyttelse ved hjælp af Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)
- [Administrer beskyttelse mod manipulation ved hjælp af Microsoft 365 Defender-portalen](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)

### <a name="how-does-configuring-tamper-protection-in-intune-affect-how-i-manage-microsoft-defender-antivirus-with-group-policy"></a>Hvordan påvirker konfiguration af beskyttelse mod ændring i Intune, hvordan jeg administrerer Microsoft Defender Antivirus med Gruppepolitik?

Gruppepolitik gælder ikke for beskyttelse mod ændring. Ændringer af Microsoft Defender Antivirus indstillinger ignoreres, når beskyttelse mod ændring er slået til.

### <a name="if-we-use-microsoft-intune-to-configure-tamper-protection-does-it-apply-only-to-the-entire-organization"></a>Hvis vi bruger Microsoft Intune til at konfigurere beskyttelse mod manipulation, gælder den så kun for hele organisationen?

Du har fleksibilitet til at konfigurere beskyttelse mod ændring med Intune. Du kan målrette hele organisationen eller vælge bestemte enheder og brugergrupper.

### <a name="can-i-configure-tamper-protection-with-microsoft-endpoint-configuration-manager"></a>Kan jeg konfigurere Tamper Protection med Microsoft Endpoint Configuration Manager?

Hvis du bruger lejertilknyt, kan du bruge Microsoft Endpoint Configuration Manager. Se følgende ressourcer:

- [Administrer manipulationsbeskyttelse for din organisation med Configuration Manager, version 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)
- [Tech Community-blog: Meddelelse om ændringsbeskyttelse for klienter med tilknytning til Configuration Manager lejer](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

### <a name="i-have-the-windows-e3-enrollment-can-i-use-configuring-tamper-protection-in-intune"></a>Jeg har den Windows E3 tilmelding. Kan jeg konfigurere beskyttelse mod manipulation i Intune?

I øjeblikket er konfiguration af beskyttelse mod manipulation i Intune kun tilgængelig for kunder, der har [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint).

### <a name="what-happens-if-i-try-to-change-microsoft-defender-for-endpoint-settings-in-intune-microsoft-endpoint-configuration-manager-and-windows-management-instrumentation-when-tamper-protection-is-enabled-on-a-device"></a>Hvad sker der, hvis jeg forsøger at ændre indstillingerne for Microsoft Defender for Endpoint i Intune, Microsoft Endpoint Configuration Manager og Windows management instrumentation, når Tamper Protection er aktiveret på en enhed?

Du kan ikke ændre de funktioner, der er beskyttet af manipulationsbeskyttelse. sådanne ændringsanmodninger ignoreres.

### <a name="im-an-enterprise-customer-can-local-admins-change-tamper-protection-on-their-devices"></a>Jeg er virksomhedskunde. Kan lokale administratorer ændre beskyttelse mod manipulation på deres enheder?

Nej. Lokale administratorer kan ikke ændre eller ændre beskyttelsesindstillinger for ændring.

### <a name="what-happens-if-my-device-is-onboarded-with-microsoft-defender-for-endpoint-and-then-goes-into-an-off-boarded-state"></a>Hvad sker der, hvis min enhed er onboardet med Microsoft Defender for Endpoint og derefter går i en tilstand uden for om bord?

Hvis en enhed ikke er om bord fra Microsoft Defender for Endpoint, er beskyttelse mod manipulation slået til, hvilket er standardtilstanden for ikke-administrerede enheder.

### <a name="if-the-status-of-tamper-protection-changes-are-alerts-shown-in-the-microsoft-365-defender-portal"></a>Hvis status for ændringsbeskyttelse ændres, vises der så beskeder på Microsoft 365 Defender-portalen?

Ja. Beskeden vises under [https://security.microsoft.com](https://security.microsoft.com) **Beskeder**.

Dit team af sikkerhedshandlinger kan også bruge jagtforespørgsler, f.eks. følgende eksempel:

`AlertInfo|where Title == "Tamper Protection bypass"`

[Vis oplysninger om forsøg på manipulation](#view-information-about-tampering-attempts).

## <a name="see-also"></a>Se også

- [Hjælp med at sikre Windows pc'er med Endpoint Protection til Microsoft Intune](/intune/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)
- [Få et overblik over Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint)
- [Bedre sammen: Microsoft Defender Antivirus og Microsoft Defender for Endpoint](why-use-microsoft-defender-antivirus.md)
