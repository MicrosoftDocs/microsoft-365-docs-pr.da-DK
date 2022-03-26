---
title: Beskyt sikkerhedsindstillinger med beskyttelse mod tæmmer
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: Brug tæmmebeskyttelse til at forhindre skadelige apps i at ændre vigtige sikkerhedsindstillinger.
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
ms.date: 01/18/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: ef9db769811c3848646c0bf7b8f7755941918362
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/31/2022
ms.locfileid: "63595887"
---
# <a name="protect-security-settings-with-tamper-protection"></a>Beskyt sikkerhedsindstillinger med beskyttelse mod tæmmer

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Tamper protection er tilgængelig for enheder, der kører en af følgende versioner af Windows:

- Windows 10
- Windows 11
- Windows 10 Enterprise flere sessioner
- Windows 11 Enterprise-session 
- Windows Server 2019
- Windows Server 2022
- Windows Server, version 1803 eller nyere
- Windows Server 2016
- Windows Server 2012 R2

> [!NOTE]
> Tamper protection i Windows Server 2012 R2 fås til enheder, der er onboardet med den moderne samlede løsningspakke. Få mere at vide under Ny funktionalitet i den moderne samlede løsning [til Windows Server 2012 R2 og 2016 Preview](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

## <a name="overview"></a>Oversigt

Under nogle typer cyberangreb forsøger dårlige angreb at deaktivere sikkerhedsfunktioner, f.eks. antivirusbeskyttelse, på dine computere. Dårlige venner, som f.eks. vil deaktivere dine sikkerhedsfunktioner for at få nemmere adgang til dine data, installere malware eller på anden måde udnytte dine data, identiteter og enheder. Tamper protection hjælper med at forhindre disse typer af ting i at ske.

Med tæmmebeskyttelse forhindres skadelige apps i at udføre handlinger som f.eks.:

- Deaktivere virus- og trusselsbeskyttelse
- Deaktivere beskyttelse i realtid
- Slå overvågning af funktionsmåder fra
- Deaktivere antivirus (f.eks IOfficeAntivirus (IOAV))
- Deaktivering af skybaseret leveringsbeskyttelse
- Fjernelse af sikkerhedsintelligensopdateringer
- Deaktivere automatiske handlinger for registrerede trusler

### <a name="how-it-works"></a>Sådan fungerer det

Manipulationsbeskyttelse låser grundlæggende Microsoft Defender Antivirus dens sikre standardværdier, og forhindrer, at dine sikkerhedsindstillinger ændres via apps og metoder som f.eks.:

- Konfiguration af indstillinger i Registreringseditor på din Windows enhed
- Ændring af indstillinger via PowerShell-cmdlet'er
- Redigere eller fjerne sikkerhedsindstillinger via Gruppepolitik

Manipulationsbeskyttelse forhindrer dig ikke i at få vist dine sikkerhedsindstillinger. Og beskyttelse mod tæmme har ingen indflydelse på, hvordan ikke-Microsoft-antivirusapps registreres i Windows Sikkerhed-appen. Hvis din organisation bruger Windows 10 Enterprise E5, kan individuelle brugere ikke ændre indstillingen for beskyttelse mod foranstaltninger. I disse tilfælde administreres beskyttelse mod manipulation af sikkerhedsteamet.

### <a name="what-do-you-want-to-do"></a>Hvad vil du gøre?

<br/><br/>

|Hvis du vil udføre denne opgave...|Se dette afsnit...|
|---|---|
|Administrer beskyttelse mod foranstaltninger på tværs af din lejer <p> Brug portalen Microsoft 365 Defender til at slå manipulationsbeskyttelse til eller fra|[Administrer beskyttelse mod tæmme for organisationen ved hjælp af Microsoft 365 Defender](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)|
|Finjustere indstillinger for beskyttelse af tæmme i din organisation <p> Brug Intune (Microsoft Endpoint Manager) til at slå manipulationsbeskyttelse til eller fra. Du kan konfigurere beskyttelse mod tæmme for nogle eller alle brugere med denne metode.|[Administrer beskyttelse mod tæmme for organisationen ved hjælp af Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)|
|Slå tæmmebeskyttelse til (eller fra) for din organisation med Konfigurationsstyring|[Administrer beskyttelse mod foranstaltninger for din organisation ved hjælp af lejer vedhæft Konfigurationsstyring, version 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)|
|Slå manipulationsbeskyttelse til (eller fra) for en enkelt enhed|[Administrer beskyttelse mod tæmme på en enkelt enhed](#manage-tamper-protection-on-an-individual-device)|
|Få vist oplysninger om tæmme forsøg på enheder|[Få vist oplysninger om tæmme forsøg](#view-information-about-tampering-attempts)|
|Gennemse dine sikkerhedsanbefalinger|[Gennemse sikkerhedsanbefalinger](#review-your-security-recommendations)|
|Gennemse listen over ofte stillede spørgsmål (Ofte stillede spørgsmål)|[Gennemse de ofte stillede spørgsmål](#view-information-about-tampering-attempts)|

Afhængigt af den metode eller det administrationsværktøj, du bruger til at aktivere beskyttelse mod tæmmer, kan der være afhængighed af skybaseret leveringsbeskyttelse.

Den følgende tabel indeholder oplysninger om metoder, værktøjer og afhængigheder.

<br/><br/>

|Sådan aktiveres tæmmebeskyttelse|Afhængighed af skybaseret leveringsbeskyttelse (MAPS)|
|---|---|
|Microsoft Intune|Nej|
|Microsoft Endpoint Configuration Manager + Lejer vedhæft|Nej|
|Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com))|Ja|

## <a name="manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal"></a>Administrere beskyttelse mod tæmme for organisationen ved hjælp Microsoft 365 Defender portal

Beskyttelse mod manipulation kan slås til eller fra for din lejer via Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)). Her er nogle ting, du skal huske på:

- I øjeblikket er indstillingen til administration af beskyttelse mod manipulation i Microsoft 365 Defender som standard aktiveret for nye installationer. For eksisterende installationer er beskyttelse mod manipulation tilgængeligt fravalgsbasis. Hvis du vil tilmelde dig, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender du</a> vælge **Indstillinger** \> **Endpoints** \> **Advanced features** \> **Tamper Protection**.

- Når du bruger portalen Microsoft 365 Defender til at administrere beskyttelse mod manipulation, behøver du ikke at bruge intune- eller lejerhæftemetoden.

- Når du administrerer beskyttelse mod manipulation i Microsoft 365 Defender-portalen, anvendes indstillingen for hele lejeren, hvilket påvirker alle dine enheder, der kører Windows 10, Windows 10 Enterprise flersessionssession, Windows 11, Windows 11 Enterprise-multisession, Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 eller Windows Server 2022. Hvis du vil finjustere beskyttelse mod tæmmer (f.eks. at have tæmmebeskyttelse på nogle enheder, men deaktiveret for andre), skal du bruge enten [Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager) eller [Konfigurationsstyring med lejeren vedhæftet](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006).

- Hvis du har et hybridmiljø, tilsidesætter indstillinger for beskyttelse af foranstaltninger, der er konfigureret i Intune, indstillinger, der er konfigureret i Microsoft 365 Defender portal.

### <a name="requirements-for-managing-tamper-protection-in-the-microsoft-365-defender-portal"></a>Krav til administration af beskyttelse mod manipulation i Microsoft 365 Defender portal

- Du skal have de [rette tilladelser](/microsoft-365/security/defender-endpoint/assign-portal-access) tildelt, f.eks. global administrator, sikkerhedsadministrator eller sikkerhedshandlinger.

- Dine Windows enheder skal køre en af følgende versioner af Windows:
  
  - Windows 10
  - Windows 11
  - Windows 10 Enterprise flere sessioner
  - Windows 11 Enterprise-session 
  - Windows Server 2019
  - Windows Server 2022
  - Windows Server, version 1803 eller nyere
  - Windows Server 2016
  - Windows Server 2012 R2

Du kan finde flere oplysninger om udgivelser [Windows 10 oplysninger om udgivelser](/windows/release-health/release-information).

- Dine enheder skal [være onboardet til Microsoft Defender til Slutpunkt](/microsoft-365/security/defender-endpoint/onboarding).

- Dine enheder skal bruge platformversioner for antimalware `4.18.2010.7` (eller derover) og versionen af antimalwareprogrammet `1.1.17600.5` (eller derover). ([Administrer Microsoft Defender Antivirus opdateringer, og anvend oprindelige](manage-updates-baselines-microsoft-defender-antivirus.md) planer).

- [Beskyttelse, der leveres i skyen](enable-cloud-protection-microsoft-defender-antivirus.md) , skal være slået til.

### <a name="turn-tamper-protection-on-or-off-in-the-microsoft-365-defender-portal"></a>Slå manipulationsbeskyttelse til (eller fra) i Microsoft 365 Defender portal

:::image type="content" source="../../media/mde-turn-tamperprotectionon.png" alt-text="Slå tæmmebeskyttelse til i Microsoft 365 Defender portal.":::

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Indstillinger** \> **slutpunkter**.

3. Gå til **Generelle** \> **avancerede funktioner**, og slå derefter tæmmebeskyttelse til.

## <a name="manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager"></a>Administrer beskyttelse mod tæmme for organisationen ved hjælp af Microsoft Endpoint Manager

Hvis din organisation bruger Microsoft Endpoint Manager (MEM), kan du slå manipulationsbeskyttelse til (eller fra) for din organisation Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Brug Intune, når du vil finjustere indstillingerne for beskyttelse af tæmmer. Hvis du f.eks. vil aktivere tæmmebeskyttelse på nogle enheder, men ikke alle, skal du bruge Intune.

### <a name="requirements-for-managing-tamper-protection-in-endpoint-manager"></a>Krav til administration af beskyttelse mod tæmme i Endpoint Manager

- Dine enheder skal [være onboardet til Microsoft Defender til Slutpunkt](/microsoft-365/security/defender-endpoint/onboarding).

- Du skal have de [rette tilladelser](/microsoft-365/security/defender-endpoint/assign-portal-access) tildelt, f.eks. global administrator, sikkerhedsadministrator eller sikkerhedshandlinger.

- Din organisation bruger [Microsoft Endpoint Manager til at administrere enheder](/mem/endpoint-manager-getting-started). (Microsoft Endpoint Manager (MEM) licenser er påkrævede. MEM er inkluderet i Microsoft 365 E3/E5, Enterprise Mobility + Security E3/E5, Microsoft 365 Business Premium, Microsoft 365 F1/F3 Microsoft 365  Government G3/G5 og tilsvarende uddannelseslicenser).

- Dine Windows enheder skal køre Windows 11 eller Windows 10 [1709](/windows/release-health/status-windows-10-1709), [1803](/windows/release-health/status-windows-10-1803), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) eller nyere. (Du kan finde flere oplysninger om udgivelser [Windows 10 oplysninger om udgivelser](/windows/release-health/release-information)).

- Du skal bruge en Windows med [sikkerhedsintelligens](https://www.microsoft.com/wdsi/definitions), der er opdateret til version 1.287.60.0 (eller nyere).

- Dine enheder skal bruge antimalwareplatformversion 4.18.1906.3 (eller nyere) og antimalwareprogramversion `1.1.15500.X` (eller derover). ([Administrer Microsoft Defender Antivirus opdateringer, og anvend oprindelige](manage-updates-baselines-microsoft-defender-antivirus.md) planer).

### <a name="turn-tamper-protection-on-or-off-in-microsoft-endpoint-manager"></a>Slå tæmmebeskyttelse til (eller fra) i Microsoft Endpoint Manager

![Slå tæmmebeskyttelse til med Endpoint Manager.](images/turnontamperprotectinmem.png)

1. I Microsoft Endpoint Manager [Administration skal](https://go.microsoft.com/fwlink/?linkid=2109431) du gå til **Endpoint Security** \> **Antivirus** og derefter vælge **+ Opret politik**.

   - På listen **Platform** skal du vælge **Windows 10 og nyere**.
   - På listen **Profil** skal du vælge **Windows Sikkerhed oplevelse**.

2. Opret en profil, der indeholder følgende indstilling:

    - **Aktivér beskyttelse mod tæmme for at forhindre, at Microsoft Defender deaktiveres: Aktivér**

3. Tildel profilen til en eller flere grupper.
 
### <a name="manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006"></a>Administrer beskyttelse mod foranstaltninger for din organisation Konfigurationsstyring, version 2006

Hvis du bruger [version 2006 af Konfigurationsstyring](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2006), kan du administrere indstillinger for beskyttelse mod manipulation på Windows 10, Windows 10 Enterprise Multi-Session, Windows 11, Windows 11 Enterprise multi-session, Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 og Windows Server 2022 ved hjælp af en metode kaldet *lejeren vedhæfter*. Vedhæft lejer gør det muligt at synkronisere dine enheder, der kun findes i det lokale miljø Konfigurationsstyring, i Microsoft Endpoint Manager Administration og derefter levere politikker for konfiguration af slutpunktssikkerhed til lokale samlinger & enheder.

> [!NOTE]
> Fremgangsmåden kan bruges til at udvide beskyttelse mod manipulation til enheder, der kører Windows 10, Windows 10 Enterprise-session, Windows 11, Windows 11 Enterprise multi-session, Windows Server 2019 og Windows Server 2022. Sørg for at gennemgå forudsætningerne og andre oplysninger i de ressourcer, der er nævnt i denne procedure.

1. Konfigurer lejer vedhæft. Du kan få mere at vide [under Introduktion: Oprette og installere sikkerhedspolitikker for slutpunkter fra Administration](/mem/configmgr/tenant-attach/endpoint-security-get-started).

2. I Microsoft Endpoint Manager [Administration skal](https://go.microsoft.com/fwlink/?linkid=2109431) du gå til **Endpoint Security** \> **Antivirus** og derefter vælge **+ Opret politik**.

   - På listen **Platform** skal du **vælge Windows 10, Windows 11 og Windows Server (ConfigMgr)**.
   - På listen **Profil** skal du vælge **Windows Sikkerhed oplevelse (forhåndsvisning)**.

3. Implementer politikken på din enhedssamling.

#### <a name="need-help-with-this-method"></a>Har du brug for hjælp til denne metode?

Se følgende ressourcer:

- [Indstillinger for Windows Sikkerhed brugeroplevelsesprofil i Microsoft Intune](/mem/intune/protect/antivirus-security-experience-windows-settings)
- [Tech Community-blog: Announcing Tamper Protection for Konfigurationsstyring tenant Attach clients](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

## <a name="manage-tamper-protection-on-an-individual-device"></a>Administrer beskyttelse mod tæmme på en enkelt enhed

> [!NOTE]
> Beskyttelse mod manipulation blokerer forsøg på at Microsoft Defender Antivirus indstillingerne via registreringsdatabasen.
>
> For at sikre, at beskyttelse mod manipulation ikke forstyrrer ikke-Microsoft-sikkerhedsprodukter eller virksomhedsinstallationsscripts, der ændrer disse indstillinger, skal du gå til **Windows Sikkerhed** og opdatere Sikkerhedsintelligens til version 1.287.60.0 eller nyere. (Se [Sikkerhedsintelligens-opdateringer](https://www.microsoft.com/wdsi/definitions)).
>
> Når du har foretaget denne opdatering, fortsætter beskyttelse af manipulation med at beskytte dine registreringsdatabaseindstillinger og logfiler forsøger at ændre dem uden at returnere fejl.

Hvis du er privat bruger, eller du ikke er underlagt indstillinger, der administreres af et sikkerhedsteam, kan du bruge Windows Sikkerhed-appen til at administrere beskyttelse mod manipulation. Du skal have de rette administratortilladelser på din enhed for at ændre sikkerhedsindstillingerne, f.eks. beskyttelse mod foranstaltninger.

Her er, hvad du ser i Windows Sikkerhed appen:

![Beskyttelse mod manipulation er slået til i Windows 10 Home.](images/tamperprotectionturnedon.png)

1. Vælg **Start**, og begynd at skrive *Sikkerhed*. I søgeresultaterne skal du vælge **Windows Sikkerhed**.

2. Vælg **Indstillinger & virus-** \> **& trusselsbeskyttelse**.

3. Slå **Manipulationsbeskyttelse** **til Til** eller **Fra**.

## <a name="are-you-using-windows-server-2016-or-windows-version-1709-1803-or-1809"></a>Bruger du Windows Server 2016 eller Windows version 1709, 1803 eller 1809?

Hvis du bruger Windows Server 2016, Windows 10 version 1709, 1803 eller [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019), kan du ikke se **Tamper Protection** i Windows Sikkerhed-appen. I stedet kan du bruge PowerShell til at afgøre, om beskyttelse mod manipulation er aktiveret.

På Windows Server 2016 afspejler Indstillinger-appen ikke nøjagtigt status for beskyttelse i realtid, når beskyttelse mod manipulation er aktiveret.

#### <a name="use-powershell-to-determine-whether-tamper-protection-and-real-time-protection-are-turned-on"></a>Brug PowerShell til at afgøre, om beskyttelse mod manipulation og beskyttelse i realtid er slået til

1. Åbn Windows PowerShell appen.

2. Brug [Cmdlet'en Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus?preserve-view=true&view=win10-ps) PowerShell.

3. På listen over resultater skal du søge efter `IsTamperProtected` eller `RealTimeProtectionEnabled`. (En sand værdi *betyder* , at tæmmebeskyttelse er aktiveret).

## <a name="view-information-about-tampering-attempts"></a>Få vist oplysninger om tæmme forsøg

Tæmme forsøg indikerer typisk større cyberangreb. En dårlig mulighed forsøger at ændre sikkerhedsindstillingerne som en måde at bevares og forblive uopdaget på. Hvis du er en del af organisationens sikkerhedsteam, kan du få vist oplysninger om sådanne forsøg og derefter udføre de relevante handlinger for at afhjælpe trusler.

Når der registreres et tæmmende forsøg, hæves en besked [i Microsoft 365 Defender portal](/microsoft-365/security/defender-endpoint/portal-overview) ([https://security.microsoft.com](https://security.microsoft.com)).

![Microsoft 365 Defender.](images/tamperattemptalert.png)

Når [slutpunktsregistrering og -svar og](overview-endpoint-detection-response.md) [avancerede jagtegenskaber](advanced-hunting-overview.md) i Microsoft Defender til slutpunkt, kan dit sikkerhedsteam undersøge og håndtere sådanne forsøg.

## <a name="review-your-security-recommendations"></a>Gennemse dine sikkerhedsanbefalinger

Beskyttelse mod sikkerhedsrisiko integreres med [funktionerne & til administration af](next-gen-threat-and-vuln-mgt.md) sikkerhedssikkerhedsrisiko. [Sikkerhedsanbefalinger](tvm-security-recommendation.md) omfatter at sikre, at beskyttelse mod foranstaltninger er slået til. Du kan f.eks. søge *efter tæmmer*. I resultaterne kan du vælge Slå **Manipulationsbeskyttelse til for at få** mere at vide og aktivere den.

![Slå beskyttelse mod tæmme til.](images/tamperprotectsecurityrecos.png)

Du kan få mere at vide & administration af trusselssikkerhedsrisiko under [Dashboard-indsigter – Håndtering af trusler og sikkerhedsrisici](tvm-dashboard-insights.md#dashboard-insights---threat-and-vulnerability-management).

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="on-which-versions-of-windows-can-i-configure-tamper-protection"></a>På hvilke versioner af Windows kan jeg konfigurere beskyttelse mod manipulation?

Windows 10 OS [1709](/windows/release-health/status-windows-10-1709), [1803](/windows/release-health/status-windows-10-1803), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) eller nyere sammen med [Microsoft Defender til slutpunkt](/microsoft-365/security/defender-endpoint).
  
Windows 10 Enterprise flere sessioner

Windows 11

Windows 11 Enterprise-session
  
Hvis du bruger Konfigurationsstyring, version 2006, med lejeren vedhæftet, kan beskyttelse mod manipulation udvides til Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 og Windows Server 2022. Se [Lejers vedhæftning: Opret og installer en sikkerhedspolitik for slutpunkter fra Administration (preview)](/mem/configmgr/tenant-attach/deploy-antivirus-policy).

### <a name="will-tamper-protection-affect-non-microsoft-antivirus-registration-in-the-windows-security-app"></a>Påvirker beskyttelse mod foranstaltninger ikke-Microsoft-antivirusregistrering i Windows Sikkerhed appen?

Nej. Antivirustilbud, der ikke er Microsoft, fortsætter med at registrere Windows Sikkerhed program.

### <a name="what-happens-if-microsoft-defender-antivirus-is-not-active-on-a-device"></a>Hvad sker der, Microsoft Defender Antivirus ikke er aktiv på en enhed?

Enheder, der er onboardet til Microsoft Defender til slutpunkt, har Microsoft Defender Antivirus kører i passiv tilstand. I disse tilfælde vil beskyttelse mod foranstaltninger fortsat beskytte tjenesten og dens funktioner.

### <a name="how-do-i-turn-tamper-protection-on-or-off"></a>Hvordan slår jeg beskyttelse mod tæmme til eller fra?

Hvis du er privat bruger, skal du [se Administrer beskyttelse mod tæmmer på en enkelt enhed](#manage-tamper-protection-on-an-individual-device).

Hvis du er en organisation, der bruger [Microsoft Defender til slutpunkt](/microsoft-365/security/defender-endpoint), bør du kunne administrere beskyttelse mod manipulation i Intune på samme måde, som du administrerer andre funktioner til slutpunktsbeskyttelse. Se de følgende afsnit i denne artikel:

- [Administrer beskyttelse mod tæmme ved hjælp Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)
- [Administrere beskyttelse mod tæmme ved hjælp Microsoft 365 Defender portal](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)

### <a name="how-does-configuring-tamper-protection-in-intune-affect-how-i-manage-microsoft-defender-antivirus-with-group-policy"></a>Hvordan påvirker konfiguration af beskyttelse mod manipulation i Intune, hvordan jeg administrerer Microsoft Defender Antivirus med Gruppepolitik?

Gruppepolitik gælder ikke for beskyttelse mod manipulation. Ændringer i Microsoft Defender Antivirus ignoreres, når beskyttelse mod tæmmer er tændt.

### <a name="if-we-use-microsoft-intune-to-configure-tamper-protection-does-it-apply-only-to-the-entire-organization"></a>Hvis vi bruger Microsoft Intune til at konfigurere beskyttelse mod manipulation, gælder det så kun for hele organisationen?

Du har fleksibilitet til at konfigurere beskyttelse mod manipulation med Intune. Du kan målrette mod hele organisationen eller vælge bestemte enheder og brugergrupper.

### <a name="can-i-configure-tamper-protection-with-microsoft-endpoint-configuration-manager"></a>Kan jeg konfigurere Manipulationsbeskyttelse med Microsoft Endpoint Configuration Manager?

Hvis du bruger lejeren vedhæftet, kan du bruge Microsoft Endpoint Configuration Manager. Se følgende ressourcer:

- [Administrer beskyttelse mod foranstaltninger for din organisation Konfigurationsstyring, version 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)
- [Tech Community-blog: Announcing Tamper Protection for Konfigurationsstyring tenant Attach clients](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

### <a name="i-have-the-windows-e3-enrollment-can-i-use-configuring-tamper-protection-in-intune"></a>Jeg har Windows E3-tilmelding. Kan jeg bruge konfiguration af beskyttelse mod manipulation i Intune?

I øjeblikket er konfiguration af beskyttelse mod manipulation i Intune kun tilgængelig for kunder, der har [Microsoft Defender til slutpunkt](/microsoft-365/security/defender-endpoint).

### <a name="what-happens-if-i-try-to-change-microsoft-defender-for-endpoint-settings-in-intune-microsoft-endpoint-configuration-manager-and-windows-management-instrumentation-when-tamper-protection-is-enabled-on-a-device"></a>Hvad sker der, hvis jeg forsøger at ændre Microsoft Defender for Endpoint-indstillinger i Intune, Microsoft Endpoint Configuration Manager og Windows Management Instrumentation, når Tamper Protection er aktiveret på en enhed?

Du kan ikke ændre de funktioner, der er beskyttet med beskyttelse mod manipulation. sådanne ændringsanmodninger ignoreres.

### <a name="im-an-enterprise-customer-can-local-admins-change-tamper-protection-on-their-devices"></a>Jeg er Enterprise-kunde. Kan lokale administratorer ændre beskyttelse mod manipulation på deres enheder?

Nej. Lokale administratorer kan ikke ændre eller ændre indstillinger for beskyttelse mod ændringer.

### <a name="what-happens-if-my-device-is-onboarded-with-microsoft-defender-for-endpoint-and-then-goes-into-an-off-boarded-state"></a>Hvad sker der, hvis min enhed er onboardet med Microsoft Defender til Slutpunkt og derefter går i en off-boarded tilstand?

Hvis en enhed er deaktiveret fra Microsoft Defender for Endpoint, er beskyttelse mod manipulation slået til, hvilket er standardtilstanden for enheder, der ikke er administrerede.

### <a name="if-the-status-of-tamper-protection-changes-are-alerts-shown-in-the-microsoft-365-defender-portal"></a>Hvis status for beskyttelse mod ændringer ændres, vises beskeder i Microsoft 365 Defender portal?

Ja. Beskeden vises under [https://security.microsoft.com](https://security.microsoft.com) **Beskeder**.

Dit sikkerhedsteam kan også bruge søgeforespørgsler, f.eks. følgende eksempel:

`AlertInfo|where Title == "Tamper Protection bypass"`

[Få vist oplysninger om tæmme forsøg](#view-information-about-tampering-attempts).

## <a name="see-also"></a>Se også

[Hjælp med at Windows pc'er med Endpoint Protection til Microsoft Intune](/intune/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

[Få et overblik over Microsoft Defender til slutpunkt](/microsoft-365/security/defender-endpoint)

[Bedre sammen: Microsoft Defender Antivirus og Microsoft Defender til slutpunkt](why-use-microsoft-defender-antivirus.md)
