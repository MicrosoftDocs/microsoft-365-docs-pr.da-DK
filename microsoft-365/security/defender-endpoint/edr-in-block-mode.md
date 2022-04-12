---
title: Registrering af slutpunkt og svar i bloktilstand
description: Få mere at vide om slutpunktsregistrering og -svar i bloktilstand
keywords: Microsoft Defender for Endpoint, mde, Slutpunktsregistrering og -svar i bloktilstand, blokering af passiv tilstand
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
- admindeeplinkDEFENDER
ms.date: 04/04/2022
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: 655681820633b0f53ba29de49052690018cab1e7
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783705"
---
# <a name="endpoint-detection-and-response-edr-in-block-mode"></a>Registrering af slutpunkt og svar (Slutpunktsregistrering og -svar) i bloktilstand

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-edr-in-block-mode"></a>Hvad er Slutpunktsregistrering og -svar i blokeringstilstand?

[Registrering og svar af slutpunkter](overview-endpoint-detection-response.md) (Slutpunktsregistrering og -svar) i blokeringstilstand giver ekstra beskyttelse mod skadelige artefakter, når Microsoft Defender Antivirus ikke er det primære antivirusprodukt og kører i passiv tilstand. Slutpunktsregistrering og -svar i bloktilstand fungerer bag kulisserne for at afhjælpe skadelige artefakter, der blev registreret af Slutpunktsregistrering og -svar funktioner. Sådanne artefakter kan være blevet overset af det primære antivirusprodukt, der ikke er fra Microsoft. For enheder, der kører Microsoft Defender Antivirus som deres primære antivirus, giver Slutpunktsregistrering og -svar i bloktilstand et ekstra forsvarslag ved at tillade Microsoft Defender Antivirus at udføre automatiske handlinger ved efterbrud, adfærdsmæssige Slutpunktsregistrering og -svar registreringer.

> [!IMPORTANT]
> Slutpunktsregistrering og -svar i blokeringstilstand giver ikke al den beskyttelse, der er tilgængelig, når Microsoft Defender Antivirus realtidsbeskyttelse er aktiveret. Alle funktioner, der afhænger af, Microsoft Defender Antivirus er den aktive antivirusløsning, fungerer ikke, herunder følgende vigtige eksempler:
>
> - Beskyttelse i realtid, herunder scanning efter adgang, er ikke tilgængelig, når Microsoft Defender Antivirus er i passiv tilstand. Hvis du vil vide mere om indstillinger for beskyttelsespolitik i realtid, skal du se **[Aktivér og konfigurer Microsoft Defender Antivirus altid aktiveret beskyttelse](configure-real-time-protection-microsoft-defender-antivirus.md)**.
>
> - Funktioner som **[netværksbeskyttelse](network-protection.md)** og **[regler for reduktion af angrebsoverfladen](attack-surface-reduction.md)** er kun tilgængelige, når Microsoft Defender Antivirus kører i aktiv tilstand.
>
> Det forventes, at din antivirusløsning, der ikke er fra Microsoft, leverer disse funktioner.

Slutpunktsregistrering og -svar i bloktilstand er integreret med [trussel & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md). Organisationens sikkerhedsteam får en [sikkerhedsanbefaling](tvm-security-recommendation.md) om at slå Slutpunktsregistrering og -svar til i blokeringstilstand, hvis den ikke allerede er aktiveret.

:::image type="content" source="images/edrblockmode-TVMrecommendation.png" alt-text="Anbefalingen om at slå Slutpunktsregistrering og -svar til i bloktilstand" lightbox="images/edrblockmode-TVMrecommendation.png":::

> [!TIP]
> Hvis du vil have den bedste beskyttelse, skal du sørge for at **[udrulle Microsoft Defender for Endpoint grundlinjer](configure-machines-security-baseline.md)**.

## <a name="what-happens-when-something-is-detected"></a>Hvad sker der, når der registreres noget?

Når Slutpunktsregistrering og -svar i blokeringstilstand er slået til, og der registreres en skadelig artefakt, Microsoft Defender for Endpoint blokerer og afhjælper dette artefakt. Dit team for sikkerhedshandlinger får vist registreringsstatus som **Blokeret** eller Forhindret i [Løsningscenter](respond-machine-alerts.md#check-activity-details-in-action-center) angivet som **fuldførte** handlinger.

På følgende billede vises en forekomst af uønsket software, der blev registreret og blokeret via Slutpunktsregistrering og -svar i blokeringstilstand:

:::image type="content" source="images/edr-in-block-mode-detection.png" alt-text="Registrering af Slutpunktsregistrering og -svar i bloktilstand" lightbox="images/edr-in-block-mode-detection.png":::


## <a name="enable-edr-in-block-mode"></a>Aktivér Slutpunktsregistrering og -svar i bloktilstand

> [!IMPORTANT]
> Fra og med platformversion 4.18.2202.X kan du nu angive Slutpunktsregistrering og -svar i bloktilstand til at målrette bestemte enhedsgrupper ved hjælp af Intune CSP'er. Du kan fortsætte med at angive Slutpunktsregistrering og -svar i blokeringstilstand for hele <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">lejeren på Microsoft 365 Defender-portalen</a>. Slutpunktsregistrering og -svar i bloktilstand anbefales primært til enheder, der kører Microsoft Defender Antivirus i passiv tilstand (der er installeret en antivirusløsning, der ikke er Microsoft, og som er aktiv på enheden). 

> [!TIP]
> Sørg for, at [kravene](#requirements-for-edr-in-block-mode) er opfyldt, før du aktiverer Slutpunktsregistrering og -svar i blokeringstilstand.

### <a name="security-portal"></a>Sikkerhedsportal 

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com/](https://security.microsoft.com/)), og log på.

2. Vælg **Indstillinger** \> **Slutpunkter** \> **Generelle** \> **avancerede funktioner**.

3. Rul ned, og **aktivér derefter Aktivér Slutpunktsregistrering og -svar i bloktilstand**.

### <a name="intune"></a>Intune

Hvis du vil oprette en brugerdefineret politik i Intune, skal du se [Installér OMA-URIs for at målrette en CSP via Intune og en sammenligning med det lokale miljø](/troubleshoot/mem/intune/deploy-oma-uris-to-target-csp-via-intune).

Du kan få flere oplysninger om den Defender-CSP, der bruges til Slutpunktsregistrering og -svar i bloktilstand, under "Configuration/PassiveRemediation" under [Defender CSP](/windows/client-management/mdm/defender-csp).


## <a name="requirements-for-edr-in-block-mode"></a>Krav til Slutpunktsregistrering og -svar i bloktilstand

I følgende tabel vises kravene til Slutpunktsregistrering og -svar i bloktilstand:

|Krav|Detaljer|
|---|---|
|Tilladelser|Du skal enten have rollen Global administrator eller Sikkerhedsadministrator tildelt i [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal). Du kan få flere oplysninger under [Grundlæggende tilladelser](basic-permissions.md).|
|Operativsystem|Enheder skal køre en af følgende versioner af Windows: <br/>- Windows 11 <br/>- Windows 10 (alle udgivelser)<br/>- Windows Server 2022 <br/>- Windows Server 2019<br/>- Windows Server, version 1803 eller nyere<br/>– Windows Server 2016 og Windows Server 2012 R2 (med den [nye samlede klientløsning](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution))<sup>[[1](#fn1)]</sup>  |
|Microsoft Defender for Endpoint|Enheder skal være onboardet til Defender for Endpoint. Se følgende artikler: <br/>- [Minimumskrav til Microsoft Defender for Endpoint](minimum-requirements.md)<br/>- [Onboarde enheder, og konfigurer Microsoft Defender for Endpoint funktioner](onboard-configure.md)<br/>- [Onboarde Windows-servere til Defender for Endpoint-tjenesten](configure-server-endpoints.md)<br/>- [Ny Windows Server 2012 R2- og 2016-funktionalitet i den moderne samlede løsning (prøveversion)](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) |
|Microsoft Defender Antivirus|Enheder skal have Microsoft Defender Antivirus installeret og køre i enten aktiv eller passiv tilstand. [Bekræft Microsoft Defender Antivirus er i aktiv eller passiv tilstand](#how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode).|
|Skybaseret beskyttelse|Microsoft Defender Antivirus skal konfigureres, så [skybaseret beskyttelse er aktiveret](enable-cloud-protection-microsoft-defender-antivirus.md).|
|Microsoft Defender Antivirus platform|Enheder skal være opdateret. Hvis du vil bekræfte dette, skal du køre [Get-MpComputerStatus-cmdlet'en](/powershell/module/defender/get-mpcomputerstatus) som administrator ved hjælp af PowerShell. På linjen **AMProductVersion** kan du se **4.18.2001.10** eller nyere. <p> Du kan få mere at vide under [Administrer Microsoft Defender Antivirus opdateringer og anvende grundlinjer](manage-updates-baselines-microsoft-defender-antivirus.md).|
|Microsoft Defender Antivirus-program|Enheder skal være opdateret. Hvis du vil bekræfte dette, skal du køre [Get-MpComputerStatus-cmdlet'en](/powershell/module/defender/get-mpcomputerstatus) som administrator ved hjælp af PowerShell. På linjen **AMEngineVersion** kan du se **1.1.16700.2** eller nyere. <p> Du kan få mere at vide under [Administrer Microsoft Defender Antivirus opdateringer og anvende grundlinjer](manage-updates-baselines-microsoft-defender-antivirus.md).|

(<a id="fn1">1</a>) Se [Understøttes Slutpunktsregistrering og -svar i bloktilstand på Windows Server 2016 og Windows Server 2012 R2?](#is-edr-in-block-mode-supported-on-windows-server-2016-and-windows-server-2012-r2)

> [!IMPORTANT]
> Hvis du vil have den bedste beskyttelsesværdi, skal du sørge for, at din antivirusløsning er konfigureret til at modtage regelmæssige opdateringer og vigtige funktioner, og at dine [undtagelser er konfigureret](configure-exclusions-microsoft-defender-antivirus.md). Slutpunktsregistrering og -svar i blokeringstilstand respekterer undtagelser, der er defineret for Microsoft Defender Antivirus, men ikke [indikatorer](manage-indicators.md), der er defineret for Microsoft Defender for Endpoint.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="can-i-specify-exclusions-for-edr-in-block-mode"></a>Kan jeg angive udeladelser for Slutpunktsregistrering og -svar i blokeringstilstand?

Når du får et falsk positivt element, kan du sende filen til analyse på [webstedet til Microsoft Sikkerhedsviden indsendelse](https://www.microsoft.com/en-us/wdsi/filesubmission).

Du kan også definere en udeladelse for Microsoft Defender Antivirus. Se [Konfigurer og valider udeladelser for Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md).

### <a name="do-i-need-to-turn-edr-in-block-mode-on-if-i-have-microsoft-defender-antivirus-running-on-devices"></a>Skal jeg slå Slutpunktsregistrering og -svar til i bloktilstand, hvis jeg har Microsoft Defender Antivirus, der kører på enheder?

Det primære formål med Slutpunktsregistrering og -svar i bloktilstand er at afhjælpe opdagelser efter sikkerhedsbrud, der blev overset af et antivirusprogram, der ikke er fra Microsoft. Der er minimal fordel ved at aktivere Slutpunktsregistrering og -svar i bloktilstand, når Microsoft Defender Antivirus er i aktiv tilstand, fordi beskyttelse i realtid forventes at registrere og afhjælpe registreringer først. Vi anbefaler, at du aktiverer Slutpunktsregistrering og -svar i bloktilstand på slutpunkter, hvor Microsoft Defender for Antivirus kører i passiv tilstand. Slutpunktsregistrering og -svar registreringer kan afhjælpes automatisk ved [hjælp af PUA-beskyttelse](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) eller ved [automatiseret undersøgelse & afhjælpningsfunktioner](automated-investigations.md) i blokeringstilstand.

### <a name="will-edr-in-block-mode-affect-a-users-antivirus-protection"></a>Vil Slutpunktsregistrering og -svar i blokeringstilstand påvirke en brugers antivirusbeskyttelse?

Slutpunktsregistrering og -svar i blokeringstilstand påvirker ikke antivirusbeskyttelse fra tredjepart, der kører på brugernes enheder. Slutpunktsregistrering og -svar i bloktilstand fungerer, hvis den primære antivirusløsning går glip af noget, eller hvis der er en registrering efter sikkerhedsbrud. Slutpunktsregistrering og -svar i blokeringstilstand fungerer på samme måde som Microsoft Defender Antivirus i passiv tilstand, bortset fra at Slutpunktsregistrering og -svar i bloktilstand også blokerer og afhjælper skadelige artefakter eller funktionsmåder, der registreres.

### <a name="why-do-i-need-to-keep-microsoft-defender-antivirus-up-to-date"></a>Hvorfor skal jeg holde Microsoft Defender Antivirus opdateret?

Da Microsoft Defender Antivirus registrerer og afhjælper skadelige elementer, er det vigtigt at holde det opdateret. For at Slutpunktsregistrering og -svar i bloktilstand skal være effektiv, bruges de nyeste modeller til enhedslæring, adfærdsregistreringer og heuristik. [Defender for Endpoint-stakken](microsoft-defender-endpoint.md) af funktioner fungerer på en integreret måde. Hvis du vil have den bedste beskyttelsesværdi, skal du holde Microsoft Defender Antivirus opdateret. Se [Administrer Microsoft Defender Antivirus opdateringer og anvende grundlinjer](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="why-do-we-need-cloud-protection-maps-on"></a>Hvorfor har vi brug for cloudbeskyttelse (MAPS) på?

Cloudbeskyttelse er nødvendig for at aktivere funktionen på enheden. Cloudbeskyttelse gør det muligt [for Defender for Endpoint](microsoft-defender-endpoint.md) at levere den nyeste og bedste beskyttelse baseret på vores bredde og dybde på sikkerhedsintelligens samt adfærds- og enhedslæringsmodeller.

### <a name="what-is-the-difference-between-active-and-passive-mode"></a>Hvad er forskellen mellem aktiv og passiv tilstand?

For slutpunkter, der kører Windows 10, Windows 11, Windows Server, version 1803 eller nyere, Windows Server 2019 eller Windows Server 2022, når Microsoft Defender Antivirus er i aktiv tilstand, bruges det som den primære antivirus på enheden. Når du kører i passiv tilstand, er Microsoft Defender Antivirus ikke det primære antivirusprogram. I dette tilfælde afhjælpes trusler ikke af Microsoft Defender Antivirus i realtid.

> [!NOTE]
> Microsoft Defender Antivirus kan kun køre i passiv tilstand, når enheden er onboardet til Microsoft Defender for Endpoint.

Du kan få flere oplysninger under [Microsoft Defender Antivirus kompatibilitet](microsoft-defender-antivirus-compatibility.md).

### <a name="how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode"></a>Hvordan gør jeg bekræfte, at Microsoft Defender Antivirus er i aktiv eller passiv tilstand?

Hvis du vil bekræfte, om Microsoft Defender Antivirus kører i aktiv eller passiv tilstand, kan du bruge Kommandoprompt eller PowerShell på en enhed, der kører Windows.

|Metode|Procedure|
|---|---|
|PowerShell|1. Vælg menuen Start, begynd at skrive `PowerShell`, og åbn derefter Windows PowerShell i resultaterne.<br/><br/>2. Skriv `Get-MpComputerStatus`.<br/><br/>3. På listen over resultater skal du i rækken **AMRunningMode** søge efter en af følgende værdier:<br/>- `Normal`<br/>- `Passive Mode`<br/><br/>Du kan få mere at vide under [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).|
|Kommandoprompten|1. Vælg menuen Start, begynd at skrive `Command Prompt`, og åbn derefter Windows kommandoprompt i resultaterne.<br/><br/>2. Skriv `sc query windefend`.<br/><br/>3. På listen over resultater skal du i rækken **STATE** bekræfte, at tjenesten kører. |

### <a name="how-do-i-confirm-that-edr-in-block-mode-is-turned-on-with-microsoft-defender-antivirus-in-passive-mode"></a>Hvordan gør jeg bekræfte, at Slutpunktsregistrering og -svar i blokeringstilstand er slået til med Microsoft Defender Antivirus i passiv tilstand?

Du kan bruge PowerShell til at bekræfte, at Slutpunktsregistrering og -svar i blokeringstilstand er slået til med Microsoft Defender Antivirus, der kører i passiv tilstand.

1. Vælg menuen Start, begynd at skrive `PowerShell`, og åbn derefter Windows PowerShell i resultaterne.

2. Skriv `Get-MPComputerStatus|select AMRunningMode`.

3. Bekræft, `EDR Block Mode`at resultatet vises.

   > [!TIP]
   > Hvis Microsoft Defender Antivirus er i aktiv tilstand, får du vist `Normal` i stedet for `EDR Block Mode`. Du kan få mere at vide under [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

### <a name="is-edr-in-block-mode-supported-on-windows-server-2016-and-windows-server-2012-r2"></a>Understøttes Slutpunktsregistrering og -svar i blokeringstilstand på Windows Server 2016 og Windows Server 2012 R2?

Hvis Microsoft Defender Antivirus kører i aktiv tilstand eller passiv tilstand, understøttes Slutpunktsregistrering og -svar i blokeringstilstand af følgende versioner af Windows:

- Windows 11
- Windows 10 (alle udgivelser)
- Windows Server, version 1803 eller nyere 
- Windows Server 2022
- Windows Server 2019 
- Windows Server 2016 og Windows Server 2012 R2 (med den [nye samlede klientløsning](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution))

Med den [nye unified klientløsning](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) til Windows Server 2016 og Windows Server 2012 R2 kan du køre Slutpunktsregistrering og -svar i blokeringstilstand i enten passiv tilstand eller aktiv tilstand.

> [!NOTE]
> Windows Server 2016 og Windows Server 2012 R2 skal onboardes ved hjælp af vejledningen i [Onboard Windows-servere](configure-server-endpoints.md), for at funktionen kan fungere. 

### <a name="how-much-time-does-it-take-for-edr-in-block-mode-to-be-disabled"></a>Hvor lang tid tager det at deaktivere Slutpunktsregistrering og -svar i blokeringstilstand?

Hvis du vælger at deaktivere Slutpunktsregistrering og -svar i blokeringstilstand, kan det tage op til 30 minutter, før systemet deaktiverer denne funktion.

## <a name="see-also"></a>Se også

- [Tech Community-blog: Introduktion til Slutpunktsregistrering og -svar i bloktilstand: Stop angreb på deres spor](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/introducing-edr-in-block-mode-stopping-attacks-in-their-tracks/ba-p/1596617)

- [Blokering og opbevaring af funktionsmåder](behavioral-blocking-containment.md)
