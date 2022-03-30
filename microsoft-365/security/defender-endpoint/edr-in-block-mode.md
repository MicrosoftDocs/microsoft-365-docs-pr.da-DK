---
title: Slutpunktsregistrering og -svar i blokeringstilstand
description: Få mere at slutpunktsregistrering og -svar i bloktilstand
keywords: Microsoft Defender til slutpunkt, mde, Slutpunktsregistrering og -svar blokeret tilstand, blokering af passiv tilstand
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
ms.date: 03/16/2022
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: 6c3df0efe5c565497803ecdd84716ec70e590afd
ms.sourcegitcommit: b67385243fb56ad20f2a6f1c40be46f5691c1c2a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63599303"
---
# <a name="endpoint-detection-and-response-edr-in-block-mode"></a>Slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) i bloktilstand

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-edr-in-block-mode"></a>Hvad er Slutpunktsregistrering og -svar i bloktilstand?

[Slutpunktsregistrering og](overview-endpoint-detection-response.md) -svar (Slutpunktsregistrering og -svar) i bloktilstand giver ekstra beskyttelse mod skadelige artefakter, når Microsoft Defender Antivirus ikke er det primære antivirusprodukt og kører i passiv tilstand. Slutpunktsregistrering og -svar i bloktilstand fungerer bag kulisserne for at afhjælpe skadelige artefakter, der blev registreret af Slutpunktsregistrering og -svar funktioner. Sådanne artefakter kan være gået glip af det primære antivirusprodukt, som ikke er Microsoft. For enheder Microsoft Defender Antivirus der kører Microsoft Defender Antivirus som deres primære antivirus, giver Slutpunktsregistrering og -svar i bloktilstand et ekstra lag af forsvar ved at gøre det muligt for Microsoft Defender Antivirus at udføre automatiske handlinger vedrørende efter brud, funktionsmåde Slutpunktsregistrering og -svar registreringer.

> [!IMPORTANT]
> Slutpunktsregistrering og -svar bloktilstand giver ikke al den beskyttelse, der er tilgængelig, når Microsoft Defender Antivirus realtidsbeskyttelse er aktiveret. Alle funktioner, der afhænger Microsoft Defender Antivirus at være den aktive antivirusløsning, fungerer ikke, herunder følgende vigtige eksempler:
>
> - Beskyttelse i realtid, herunder scanning ved adgang, er ikke tilgængelig, når Microsoft Defender Antivirus er i passiv tilstand. Du kan få mere at vide om indstillinger for beskyttelsespolitik i realtid under **[Aktivér Microsoft Defender Antivirus altid aktiveret beskyttelse](configure-real-time-protection-microsoft-defender-antivirus.md)**.
> - Funktioner som **[f.eks.](network-protection.md)** **[netværksbeskyttelse og reduktion af angrebsoverfladen](attack-surface-reduction.md)** er kun tilgængelige, Microsoft Defender Antivirus kører i aktiv tilstand.
>
> Det forventes, at din antivirusløsning, der ikke er Microsoft, leverer disse funktioner.

Slutpunktsregistrering og -svar i bloktilstand er integreret med [& håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md). Organisationens sikkerhedsteam får en sikkerhedsanbefaling for at Slutpunktsregistrering og -svar blokeringstilstand til, hvis det ikke allerede er aktiveret.[](tvm-security-recommendation.md)

:::image type="content" source="images/edrblockmode-TVMrecommendation.png" alt-text="anbefaling om at Slutpunktsregistrering og -svar i bloktilstand.":::

> [!TIP]
> Du får den bedste beskyttelse ved at installere **[Microsoft Defender som grundlinje for Slutpunkt](configure-machines-security-baseline.md)**.

## <a name="what-happens-when-something-is-detected"></a>Hvad sker der, når der registreres noget?

Når Slutpunktsregistrering og -svar bloktilstand er slået til, og en skadelig artefakt registreres, blokerer og afhjælper Microsoft Defender til slutpunkt den pågældende artefakt. Dit sikkerhedsteam vil få vist registreringsstatus som **Blokeret** **eller Forhindret** i [handlingscenter](respond-machine-alerts.md#check-activity-details-in-action-center) angivet som fuldførte handlinger.

Følgende billede viser en forekomst af uønsket software, der blev registreret og blokeret via Slutpunktsregistrering og -svar i blokeringstilstand:

:::image type="content" source="images/edr-in-block-mode-detection.png" alt-text="Slutpunktsregistrering og -svar registreret noget i bloktilstand.":::


## <a name="enable-edr-in-block-mode"></a>Aktivér Slutpunktsregistrering og -svar i bloktilstand

> [!IMPORTANT]
> Fra og med platform version 4.18.2202.X kan du nu indstille Slutpunktsregistrering og -svar i bloktilstand til at målrette mod bestemte enhedsgrupper ved hjælp af Intune-csp'er. Du kan fortsætte med at Slutpunktsregistrering og -svar i bloktilstand for hele lejeren <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">i Microsoft 365 Defender-portalen</a>. Bemærk, at Slutpunktsregistrering og -svar blokeret tilstand primært anbefales til enheder, der kører MDAV i passiv tilstand (en tredjeparts-AV er aktiv). 

> [!TIP]
> Sørg for, [at kravene](#requirements-for-edr-in-block-mode) er opfyldt, før du Slutpunktsregistrering og -svar i bloktilstand.

### <a name="security-portal"></a>Sikkerhedsportal 

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com/](https://security.microsoft.com/)), og log på.
2. Vælg **Indstillinger** \> **Avancerede slutpunkter** \> **.** \> 
3. Rul ned, og aktivér **aktivér Slutpunktsregistrering og -svar bloktilstand**.

### <a name="intune"></a>Intune

Hvis du vil oprette en brugerdefineret politik i Intune, skal du se [Deploy OMA-URIs to target a CSP through Intune, og en sammenligning med det lokale miljø](/troubleshoot/mem/intune/deploy-oma-uris-to-target-csp-via-intune).

Du kan finde flere oplysninger om Den Defender CSP, der Slutpunktsregistrering og -svar i bloktilstand, under "Konfiguration/PassivAfstigelse" under [Defender CSP](/windows/client-management/mdm/defender-csp).


## <a name="requirements-for-edr-in-block-mode"></a>Krav til Slutpunktsregistrering og -svar i bloktilstand

|Krav|Detaljer|
|---|---|
|Tilladelser|Du skal have enten den globale administrator- eller sikkerhedsadministratorrolle tildelt [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal). Du kan finde flere oplysninger [under Grundlæggende tilladelser](basic-permissions.md).|
|Operativsystem|Enheder skal køre en af følgende versioner af Windows: <br/>- Windows 10 (alle versioner)<br/>- Windows Server, version 1803 eller nyere<br/>- Windows Server 2019<br/>- Windows Server 2022<br/>- Windows Server 2016 (kun når Microsoft Defender Antivirus er i aktiv tilstand)|
|Microsoft Defender til Slutpunkt|Enheder skal være onboardet til Defender til Slutpunkt. Se [Minimumskrav til Microsoft Defender til slutpunkt](minimum-requirements.md).|
|Microsoft Defender Antivirus|Enheder skal have Microsoft Defender Antivirus installeret og køre i enten aktiv eller passiv tilstand. [Bekræft Microsoft Defender Antivirus er i aktiv eller passiv tilstand](#how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode).|
|Cloud-leveret beskyttelse|Microsoft Defender Antivirus skal konfigureres sådan, at [beskyttelse, der leveres i skyen, er aktiveret](enable-cloud-protection-microsoft-defender-antivirus.md).|
|Microsoft Defender Antivirus platform|Enheder skal være opdateret. For at bekræfte, at du bruger PowerShell, skal [du køre Get-MpComputerStatus-cmdlet'en](/powershell/module/defender/get-mpcomputerstatus) som administrator. I linjen **AMProductVersion** skal du se **4.18.2001.10** eller derover. <p> Du kan få mere at vide [under Administrere Microsoft Defender Antivirus opdateringer og anvende oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md).|
|Microsoft Defender Antivirus program|Enheder skal være opdateret. For at bekræfte, at du bruger PowerShell, skal [du køre Get-MpComputerStatus-cmdlet'en](/powershell/module/defender/get-mpcomputerstatus) som administrator. I linjen **AMEngineVersion** skal du se **1.1.16700.2** eller derover. <p> Du kan få mere at vide [under Administrere Microsoft Defender Antivirus opdateringer og anvende oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md).|

> [!IMPORTANT]
> For at få den bedste beskyttelsesværdi skal du sørge for, at din antivirusløsning er konfigureret til at modtage regelmæssige opdateringer og vigtige funktioner, og at dine undtagelser [er konfigureret](configure-exclusions-microsoft-defender-antivirus.md). Slutpunktsregistrering og -svar i bloktilstand respekterer undtagelser, der er defineret for Microsoft Defender Antivirus, men ikke indikatorer, der er defineret [](manage-indicators.md) for Microsoft Defender til slutpunkt.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="do-i-need-to-turn-edr-in-block-mode-on-if-i-have-microsoft-defender-antivirus-running-on-devices"></a>Har jeg brug for at Slutpunktsregistrering og -svar blokeringstilstand til, hvis jeg har Microsoft Defender Antivirus kører på enheder?

Det primære formål med at Slutpunktsregistrering og -svar blokeringstilstand er at afhjælpe registreringer efter brud, som er blevet overset af et antivirusprodukt, som ikke er Microsoft. Vi anbefaler dog, at Slutpunktsregistrering og -svar bloktilstand er slået til, uanset om Microsoft Defender Antivirus kører i passiv tilstand eller i aktiv tilstand.

- Når Microsoft Defender Antivirus er i passiv tilstand, Slutpunktsregistrering og -svar i bloktilstand et andet lag af forsvar sammen med Microsoft Defender til slutpunkt.
- Når Microsoft Defender Antivirus er i aktiv tilstand, giver Slutpunktsregistrering og -svar i bloktilstand ikke ekstra scanning, men det gør det muligt for Microsoft Defender Antivirus at udføre automatiske handlinger ved efterfølgende brud, funktionsmåde Slutpunktsregistrering og -svar registreringer.

### <a name="will-edr-in-block-mode-affect-a-users-antivirus-protection"></a>Vil Slutpunktsregistrering og -svar blokeringstilstand påvirke en brugers antivirusbeskyttelse?

Slutpunktsregistrering og -svar blokeringstilstand påvirker ikke antivirusbeskyttelse fra tredjeparter, der kører på brugernes enheder. Slutpunktsregistrering og -svar i blokeringstilstand fungerer, hvis den primære antivirusløsning går glip af noget, eller hvis der er en registrering efter brud. Slutpunktsregistrering og -svar bloktilstand fungerer på samme måde som Microsoft Defender Antivirus i passiv tilstand, bortset fra at Slutpunktsregistrering og -svar i bloktilstand også blokerer og afhjælper skadelige komponenter eller funktionsmåder, der registreres.

### <a name="why-do-i-need-to-keep-microsoft-defender-antivirus-up-to-date"></a>Hvorfor skal jeg holde Microsoft Defender Antivirus opdateret?

Da Microsoft Defender Antivirus registrerer og afhjælper skadelige elementer, er det vigtigt at holde det opdateret. For Slutpunktsregistrering og -svar funktion i bloktilstand er effektiv, anvender programmet de nyeste modeller for enhedslæring, funktionsmåderegistreringer og heuristics. [Stakken af egenskaber for Defender](microsoft-defender-endpoint.md) til slutpunkt fungerer integreret. For at få den bedste beskyttelsesværdi skal Microsoft Defender Antivirus holde dig opdateret. Se [Administrere Microsoft Defender Antivirus opdateringer og anvende oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="why-do-we-need-cloud-protection-maps-on"></a>Hvorfor har vi brug for skybeskyttelse (MAPS) på?

Skybeskyttelse er nødvendig for at aktivere funktionen på enheden. Cloud Protection giver [Defender til Slutpunkt mulighed for](microsoft-defender-endpoint.md) at levere den nyeste og bedste beskyttelse, der er baseret på vores brødet og dybde af sikkerhedsintelligens, samt funktionsmåder og enhedslæringsmodeller.

### <a name="what-is-the-difference-between-active-and-passive-mode"></a>Hvad er forskellen mellem aktiv og passiv tilstand?

For slutpunkter, der kører Windows 10, Windows 11, Windows Server, version 1803 eller nyere, Windows Server 2019 eller Windows Server 2022, når Microsoft Defender Antivirus er i aktiv tilstand, bruges det som det primære antivirusprogram på enheden. Når du kører i passiv tilstand, Microsoft Defender Antivirus ikke det primære antivirusprodukt. I dette tilfælde afhjælpes trusler ikke af Microsoft Defender Antivirus i realtid.

> [!NOTE]
> Microsoft Defender Antivirus kan kun køre i passiv tilstand, når enheden er onboardet til Microsoft Defender til Slutpunkt.

Du kan finde flere oplysninger [Microsoft Defender Antivirus kompatibilitet.](microsoft-defender-antivirus-compatibility.md)

### <a name="how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode"></a>Hvordan kan jeg bekræfte Microsoft Defender Antivirus der er i aktiv eller passiv tilstand?

Hvis du vil bekræfte Microsoft Defender Antivirus kører i aktiv eller passiv tilstand, kan du bruge Kommandoprompt eller PowerShell på en enhed, der Windows.

<br/><br/>

|Metode|Procedure|
|---|---|
|PowerShell|1. Vælg menuen Start, begynd at skrive `PowerShell`, og åbn Windows PowerShell i resultaterne.<br/><br/>2. Skriv `Get-MpComputerStatus`.<br/><br/>3. På listen over resultater i rækken **AMRunningMode** skal du søge efter en af følgende værdier:<br/>- `Normal`<br/>- `Passive Mode`<br/><br/>Du kan få mere at vide [under Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).|
|Kommandoprompt|1. Vælg menuen Start, begynd at skrive`Command Prompt`, og åbn Windows Kommandoprompt i resultaterne.<br/><br/>2. Skriv `sc query windefend`.<br/><br/>3. På listen over resultater i rækken **STAT** skal du bekræfte, at tjenesten kører. |

### <a name="how-do-i-confirm-that-edr-in-block-mode-is-turned-on-with-microsoft-defender-antivirus-in-passive-mode"></a>Hvordan kan jeg bekræfte, Slutpunktsregistrering og -svar blokeringstilstand er slået til med Microsoft Defender Antivirus passiv tilstand?

Du kan bruge PowerShell til at bekræfte, Slutpunktsregistrering og -svar blokeringstilstand er slået til, når Microsoft Defender Antivirus kører i passiv tilstand.

1. Markér feltet menuen Start, begynd at `PowerShell`skrive , og åbn Windows PowerShell i resultaterne.

2. Skriv `Get-MPComputerStatus|select AMRunningMode`.

3. Bekræft, at resultatet `EDR Block Mode`, , vises.

   > [!TIP]
   > Hvis Microsoft Defender Antivirus er i aktiv tilstand, vises i stedet `Normal` for `EDR Block Mode`. Du kan få mere at vide [under Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

### <a name="is-edr-in-block-mode-supported-on-windows-server-2016"></a>Understøttes Slutpunktsregistrering og -svar bloktilstand på Windows Server 2016?

Hvis Microsoft Defender Antivirus kører i aktiv eller passiv tilstand, understøttes Slutpunktsregistrering og -svar bloktilstand af følgende versioner af Windows:

- Windows 10 (alle versioner)
- Windows Server, version 1803 eller nyere 
- Windows Server 2022
- Windows Server 2019 
- Windows Server 2016
- Windows Server 2012 R2
- Windows 11

>[!NOTE]
>Windows Server 2016 og Windows Server 2012 R2 skal være onboardet ved hjælp af instruktionerne i [Onboard Windows-servere](configure-server-endpoints.md), for at denne funktion kan fungere. 

### <a name="how-much-time-does-it-take-for-edr-in-block-mode-to-be-disabled"></a>Hvor lang tid tager det for Slutpunktsregistrering og -svar bloktilstand at være deaktiveret?

Hvis du vælger at Slutpunktsregistrering og -svar i bloktilstand, kan det tage op til 30 minutter, før systemet deaktiverer denne funktion.

## <a name="see-also"></a>Se også

- [Tech Community-blog: Introduktion Slutpunktsregistrering og -svar blokeringstilstand: Stoppe angreb på deres spor](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/introducing-edr-in-block-mode-stopping-attacks-in-their-tracks/ba-p/1596617)
- [Blokering og inddæmmelse af funktionsmåder](behavioral-blocking-containment.md)
