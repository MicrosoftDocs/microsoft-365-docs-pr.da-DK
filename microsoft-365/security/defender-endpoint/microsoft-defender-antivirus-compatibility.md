---
title: Microsoft Defender Antivirus kompatibilitet med andre sikkerhedsprodukter
description: Få mere Microsoft Defender Antivirus oplysninger om, hvordan du bruger andre sikkerhedsprodukter og operativsystemer.
keywords: windows defender, defender til slutpunkt, næste generation, antivirus, kompatibilitet, passiv tilstand
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: mkaminska, pahuijbr
manager: dansimp
ms.technology: mde
ms.date: 03/16/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: be29874a087936c7131492bde1a3f541e7d00f43
ms.sourcegitcommit: 2bbccbcffce3ea6d10ea6d307349874eafb21339
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/05/2022
ms.locfileid: "64645072"
---
# <a name="microsoft-defender-antivirus-compatibility-with-other-security-products"></a>Microsoft Defender Antivirus kompatibilitet med andre sikkerhedsprodukter

**Gælder for:**

- Microsoft Defender Antivirus
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

Microsoft Defender Antivirus installeres automatisk på slutpunkter, der kører følgende versioner af Windows:

- Windows 10 eller nyere
- Windows Server 2022
- Windows Server 2019
- Windows Server, version 1803 eller nyere
- Windows Server 2016

Hvad sker der, når der bruges en anden ikke-Microsoft antivirus-/antimalwareløsning? Kan man køre Microsoft Defender Antivirus sammen med et andet antivirusprodukt? Svarene afhænger af flere faktorer, f.eks. dit operativsystem, og om [du bruger Microsoft Defender for Endpoint](microsoft-defender-endpoint.md) sammen med din antivirusbeskyttelse.

I denne artikel beskrives, hvad der Microsoft Defender Antivirus og en løsning, der ikke er Microsoft-antivirus/antimalware, med og uden Defender til Slutpunkt.

> [!IMPORTANT]
> - Microsoft Defender Antivirus fås til enheder, der kører Windows 10 og 11, Windows Server 2022, Windows Server 2019, Windows Server, version 1803 eller nyere og Windows Server 2016. 
> - Microsoft Defender Antivirus fås også på Windows Server 2012 R2, når den er onboardet med [den moderne, samlede løsning](/microsoft-365/security/defender-endpoint/configure-server-endpoints).
> - På Windows 8.1 tilbydes antivirusbeskyttelse på virksomhedsniveau som [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10), som administreres via Microsoft Endpoint Configuration Manager.
> - Windows Defender også på forbrugerenheder på [Windows 8.1](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender), Windows Defender giver dog ikke administration på virksomhedsniveau.

## <a name="antivirus-protection-without-defender-for-endpoint"></a>Antivirusbeskyttelse uden Defender til slutpunkt

I dette afsnit beskrives, hvad der sker, når du bruger Microsoft Defender Antivirus sammen med ikke-Microsoft-antivirus-/antimalwareprodukter på slutpunkter, der ikke er onboardet til Defender til slutpunkt. 

> [!NOTE]
> Generelt kan Microsoft Defender Antivirus ikke i passiv tilstand på enheder, der ikke er onboardet til Defender til slutpunkt.

Følgende tabel opsummerer, hvad du kan forvente:

|Windows version|Primær antivirus-/antimalwareløsning|Microsoft Defender Antivirus tilstand|
|:---|:---|:---|
|Windows 10 <br/> Windows 11|Microsoft Defender Antivirus|Aktiv tilstand|
|Windows 10 <br/> Windows 11|En løsning til antivirus/antimalware, der ikke er Microsoft|Deaktiveret tilstand (sker automatisk)|
|Windows Server 2022 <br/> Windows Server 2019<br/> Windows Server, version 1803 eller nyere <br/> Windows Server 2016 |Microsoft Defender Antivirus|Aktiv tilstand|
|Windows Server 2022<br/>Windows Server 2019<br/>Windows Server, version 1803 eller nyere <br/> Windows Server 2016  |En løsning til antivirus/antimalware, der ikke er Microsoft|Deaktiveret (angivet manuelt) <sup>[[1](#fn1)]</sup>|

(<a id="fn1">1</a>) Hvis du Windows et antivirusprodukt fra en server, der ikke er Microsoft, kan du fjerne disse Microsoft Defender Antivirus for at forhindre konflikter. Hvis enheden er onboardet til Microsoft Defender for Endpoint, kan du bruge Microsoft Defender Antivirus i passiv tilstand (se nedenfor).

> [!TIP]
> På Windows Server 2016 vises den muligvis *Windows Defender Antivirus i* stedet for *Microsoft Defender Antivirus*.

## <a name="microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions"></a>Microsoft Defender Antivirus og ikke-Microsoft-antivirus-/antimalwareløsninger

> [!NOTE]
> Generelt kan Microsoft Defender Antivirus indstilles til kun passiv tilstand på slutpunkter, der er onboardet til Defender til slutpunkt.

Om Microsoft Defender Antivirus kører i aktiv tilstand, passiv tilstand eller er deaktiveret, afhænger af flere faktorer, f.eks.:

- Hvilken version Windows er installeret på et slutpunkt
- Uanset Microsoft Defender Antivirus er den primære antivirus-/antimalwareløsning på slutpunktet
- Om slutpunktet er onboardet til Defender til slutpunkt

Følgende tabel opsummerer tilstanden af Microsoft Defender Antivirus i flere scenarier. 

| Windows version   | Antivirus/antimalwareløsning  | Onboarded til <br/> Defender til Slutpunkt? | Microsoft Defender Antivirus tilstand     |
|:------|:------|:-------|:-------|
| Windows 10 <br/> Windows 11| Microsoft Defender Antivirus | Ja  | Aktiv tilstand | 
| Windows 10 <br/> Windows 11 | Microsoft Defender Antivirus | Nej   | Aktiv tilstand |
| Windows 10 <br/> Windows 11  | En løsning til antivirus/antimalware, der ikke er Microsoft | Ja  | Passiv tilstand (automatisk) |
| Windows 10 <br/> Windows 11  | En løsning til antivirus/antimalware, der ikke er Microsoft | Nej   | Deaktiveret tilstand (automatisk)    |
| Windows Server 2022 <br/> Windows Server 2019 <br/>Windows Server, version 1803 eller nyere  | Microsoft Defender Antivirus  | Ja |         Aktiv tilstand  |
| Windows Server 2022 <br/> Windows Server 2019 <br/> Windows Server, version 1803 eller nyere   | Microsoft Defender Antivirus | Nej  | Aktiv tilstand |
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server, version 1803 eller nyere  | En løsning til antivirus/antimalware, der ikke er Microsoft | Ja  | Microsoft Defender Antivirus skal indstilles til passiv tilstand (manuelt) <sup>[[2](#fn2)]<sup>  | 
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server, version 1803 eller nyere  | En løsning til antivirus/antimalware, der ikke er Microsoft | Nej  | Microsoft Defender Antivirus skal deaktiveres (manuelt) <sup>[[3](#fn3)]<sup></sup>  |
| Windows Server 2016 <br/> Windows Server 2012 R2   | Microsoft Defender Antivirus | Ja | Aktiv tilstand |
|Windows Server 2016 <br/> Windows Server 2012 R2  | Microsoft Defender Antivirus | Nej | Aktiv tilstand |
| Windows Server 2016 <br/> Windows Server 2012 R2  | En løsning til antivirus/antimalware, der ikke er Microsoft | Ja | Microsoft Defender Antivirus skal indstilles til passiv tilstand (manuelt) <sup>[[2](#fn2)]<sup> |
|Windows Server 2016 <br/> Windows Server 2012 R2  | En løsning til antivirus/antimalware, der ikke er Microsoft | Nej | Microsoft Defender Antivirus skal deaktiveres (manuelt) <sup>[[3](#fn3)]<sup> |

(<a id="fn2">2</a>) På Windows Server 2019, Windows Server, version 1803 eller nyere, Windows Server 2016 eller Windows Server 2012 R2 skifter Microsoft Defender Antivirus ikke passiv tilstand automatisk, når du installerer et antivirusprodukt, der ikke er Microsoft. I disse tilfælde skal du indstille Microsoft Defender Antivirus til passiv tilstand for at forhindre problemer, der skyldes, at du har flere antivirusprodukter installeret på en server. Du kan indstille Microsoft Defender Antivirus til passiv tilstand ved hjælp af PowerShell, Gruppepolitik eller en registreringsdatabasenøgle. 

  Du kan indstille Microsoft Defender Antivirus til passiv tilstand ved at angive følgende registreringsdatabasenøgle:
- Sti: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Navn: `ForceDefenderPassiveMode`
- Skriv: `REG_DWORD`
- Værdi: `1`

 > [!NOTE]
 > For at passiv tilstand kan fungere på slutpunkter, der kører Windows Server 2016 og Windows Server 2012 R2, skal disse slutpunkter være onboardet med den moderne, samlede løsning, der er beskrevet i [Onboard Windows-servere](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016). 

(<a id="fn3">3</a>) På Windows Server 2016 skal du Windows Server 2012 R2, Windows Server version 1803 eller nyere, Windows Server 2019 og Windows Server 2022, hvis du bruger et antivirusprodukt, der ikke er Microsoft, på et slutpunkt, der ikke er onboardet til  Microsoft Defender for Endpoint, deaktiver/fjern Microsoft Defender Antivirus manuelt for at forhindre problemer, der skyldes, at du har flere antivirusprodukter installeret på en server.

> [!TIP]
> På Windows Server 2016 vises den muligvis *Windows Defender Antivirus i* stedet for *Microsoft Defender Antivirus*.

> [!IMPORTANT]
> Microsoft Defender Antivirus er kun tilgængelig på enheder, der kører Windows 10 og 11, Windows Server 2022, Windows Server 2019, Windows Server, version 1803 eller nyere, Windows Server 2016 og Windows Server 2012 R2.
>
> I Windows 8.1 tilbydes antivirusbeskyttelse på virksomhedsniveau som [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)), der administreres via Microsoft Endpoint Configuration Manager.
>
> Windows Defender også på forbrugerenheder på [Windows 8.1](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender), Windows Defender giver dog ikke administration på virksomhedsniveau.

Defender til Slutpunkt omfatter funktioner, der yderligere udvider den antivirusbeskyttelse, der er installeret på dit slutpunkt. Du kan drage fordel af at køre Microsoft Defender Antivirus sammen med en anden antivirusløsning.

Eksempelvis giver registrering af slutpunkter og svar [(Slutpunktsregistrering og -svar)](edr-in-block-mode.md) i bloktilstand ekstra beskyttelse mod skadelige artefakter, selvom Microsoft Defender Antivirus ikke er det primære antivirusprodukt. Disse funktioner kræver, Microsoft Defender Antivirus installeres og kører i passiv tilstand eller aktiv tilstand.

### <a name="requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode"></a>Krav til, Microsoft Defender Antivirus skal køre i passiv tilstand

For at Microsoft Defender Antivirus i passiv tilstand, skal slutpunkter opfylde følgende krav:

- Operativsystem: Windows 10 eller nyere; Windows Server 2022, Windows Server 2019 eller Windows Server, version 1803 eller nyere
- Microsoft Defender Antivirus skal være installeret
- Et andet antivirus-/antimalwareprodukt, der ikke er Microsoft, skal installeres og bruges som den primære antivirusløsning
- Slutpunkter skal være onboardet til Defender for Endpoint

## <a name="how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality"></a>Sådan Microsoft Defender Antivirus Det påvirker Defender i forbindelse med slutpunktsfunktionaliteten

Defender til slutpunkt påvirker, om Microsoft Defender Antivirus kan køre i passiv tilstand. Microsoft Defender Antivirus kan også påvirke visse funktioner i Defender til slutpunkt. Beskyttelse i realtid fungerer f.eks., når Microsoft Defender Antivirus er i aktiv eller passiv tilstand, men ikke når Microsoft Defender Antivirus deaktiveres eller afinstalleres.

Tabellen i dette afsnit opsummerer de funktioner og funktioner, der aktivt fungerer eller ej, afhængigt af om Microsoft Defender Antivirus er i aktiv tilstand, passiv tilstand eller deaktiveret/fjernet.

> [!IMPORTANT]
> Den følgende tabel er beregnet til kun at være til orientering. **Deaktiver** ikke egenskaber som beskyttelse i realtid, beskyttelse i skyen eller begrænset periodisk scanner, hvis du bruger Microsoft Defender Antivirus i passiv tilstand, eller hvis du bruger [Slutpunktsregistrering og -svar](edr-in-block-mode.md) i bloktilstand, som bruges i baggrunden til at registrere og afhjælpe skadelige komponenter, der er blevet registreret efter brud.

 | Beskyttelse | Microsoft Defender Antivirus <br/>(*Aktiv tilstand*) | Microsoft Defender Antivirus <br/>(*Passiv tilstand*) | Microsoft Defender Antivirus <br/>(*Deaktiveret eller fjernet*) | [EDR i bloktilstand](edr-in-block-mode.md) | 
 |:---|:---|:---|:---|:---| 
 | [Beskyttelse i realtid](configure-real-time-protection-microsoft-defender-antivirus.md) | Ja | Se bemærkning <sup>[[4](#fn4)]</sup> | Nej | Nej | 
 | [Cloud-leveret beskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md) | Ja | Nej  | Nej | Nej | 
 | [Netværksbeskyttelse](network-protection.md)  | Ja | Nej | Nej | Nej | 
 | [Regler for reduktion af angrebsoverflade](attack-surface-reduction.md)  | Ja | Nej | Nej  | Nej | 
 | [Begrænset tilgængelighed af periodisk scanner](limited-periodic-scanning-microsoft-defender-antivirus.md) | Nej | Nej | Ja | Nej | 
 | [Oplysninger om scanning og registrering af filer](review-scan-results-microsoft-defender-antivirus.md) | Ja | Ja<sup>[[5](#fn5)]</sup> | Nej | Ja | 
 | [Trussels afhjælpning](configure-remediation-microsoft-defender-antivirus.md) | Ja | Se bemærkning <sup>[[6](#fn6)]</sup> | Nej | Ja | 
 | [Sikkerhedsintelligensopdateringer](manage-updates-baselines-microsoft-defender-antivirus.md) | Ja | Ja | Nej | Ja | 

(<a id="fn4">4</a>) Når Microsoft Defender Antivirus er i passiv tilstand, giver beskyttelse i realtid generelt ikke nogen blokering eller håndhævelse, selvom den er aktiveret og i passiv tilstand.

(<a id="fn5">5</a>) Når Microsoft Defender Antivirus i passiv tilstand, planlægges scanninger ikke.

(<a id="fn6">6</a>) Når Microsoft Defender Antivirus er i passiv tilstand, afhjælper det ikke trusler. Trusler kan dog afhjælpes ved at registrere [og reagere på slutpunkter (Slutpunktsregistrering og -svar) i blokeringstilstand](edr-in-block-mode.md). I dette tilfælde vises beskeder muligvis som Microsoft Defender Antivirus som en kilde, også selvom Microsoft Defender Antivirus er i passiv tilstand.

> [!NOTE]
> [Microsoft 365 beskyttelse mod datatab på](/microsoft-365/compliance/endpoint-dlp-learn-about) slutpunkter fungerer fortsat normalt, når Microsoft Defender Antivirus er i enten aktiv eller passiv tilstand.

## <a name="important-notes"></a>Vigtige bemærkninger

- Deaktiver, stop eller rediger ikke nogen af de tilknyttede tjenester, der bruges af Microsoft Defender Antivirus, Defender til slutpunkt eller Windows Sikkerhed-appen. Denne anbefaling omfatter *tjenester og processer fra wscsvc*, *SecurityHealthService*, *MsSense*, *Sense*, *WinDefend* eller *MsMpEng* . Hvis du manuelt ændrer disse tjenester, kan det medføre alvorlig ustabilitet på dine enheder og gøre dit netværk sårbar. Deaktivering, stop eller ændring af disse tjenester kan også medføre problemer, når du bruger ikke-Microsoft-antivirusløsninger, og hvordan deres oplysninger vises [i Windows Sikkerhed-appen](microsoft-defender-security-center-antivirus.md).

- I Defender til Slutpunkt skal du slå Slutpunktsregistrering og -svar bloktilstand til, også selvom Microsoft Defender Antivirus ikke er din primære antivirusløsning. Slutpunktsregistrering og -svar blokeringstilstand registrerer og afhjælper skadelige elementer, der findes på enheden (efter brud). Du kan få mere at vide [Slutpunktsregistrering og -svar i bloktilstand](edr-in-block-mode.md).

## <a name="how-to-confirm-the-state-of-microsoft-defender-antivirus"></a>Sådan bekræftes tilstanden for Microsoft Defender Antivirus

Du kan bruge en af flere metoder til at bekræfte tilstanden af Microsoft Defender Antivirus, som beskrevet i følgende tabel:

 | Metode | Procedure | 
 |:---|:---| 
 | Windows Sikkerhed app |  1. På Windows enhed skal du åbne Windows Sikkerhed appen.<br/>2. Vælg **Virus- & trusselsbeskyttelse**.<br/>3. **Under Who jeg? vælg** **Administrer udbydere**.<br/>4. På **siden Sikkerhedsudbydere** under **Antivirus** kan du se, **Microsoft Defender Antivirus er slået til**. | 
 | Jobliste |  1. Åbn Windows Jobliste på en enhed med en anden enhed.<br/>2. Vælg **fanen** Detaljer.<br/>3. Se **MsMpEng.exe** på listen. | 
 | Windows PowerShell <br/> (Sådan bekræfter du, Microsoft Defender Antivirus kører) |  1. På en Windows enhed skal du åbne Windows PowerShell. <br/>2. Kør følgende PowerShell-cmdlet: `Get-Process`.<br/>3. Gennemse resultaterne. Du bør kunne se **MsMpEng.exe** hvis Microsoft Defender Antivirus er aktiveret. | 
 | Windows PowerShell <br/>(For at bekræfte, at antivirusbeskyttelse er på plads) |  Du kan bruge [Cmdlet'en Get-MpComputerStatus PowerShell](/powershell/module/defender/get-mpcomputerstatus).<br/>1. På en Windows enhed skal du åbne Windows PowerShell.<br/>2. Kør følgende PowerShell-cmdlet:<br/> \|Get-MpComputerStatus amrunningMode <br/>3. Gennemse resultaterne. Du bør kunne se **enten Normal** **eller Passiv**, Microsoft Defender Antivirus er aktiveret på slutpunktet.  | 
 | Kommandoprompt |  1. På en Windows skal du åbne Kommandoprompt.<br/>2. Skriv `sc query windefend`, og tryk derefter på Enter.<br/>3. Gennemse resultaterne for at bekræfte, Microsoft Defender Antivirus kører i passiv tilstand.  | 

## <a name="more-details-about-microsoft-defender-antivirus-states"></a>Flere oplysninger om Microsoft Defender Antivirus tilstande

Tabellen i dette afsnit beskriver forskellige tilstande, du kan få vist med Microsoft Defender Antivirus.

 |  Stat  |  Hvad sker der?  | 
 |:---|:---| 
 |  Aktiv tilstand  |  I aktiv tilstand Microsoft Defender Antivirus bruges som antivirusapp på computeren. Indstillinger, der er konfigureret ved hjælp af Configuration Manager, Gruppepolitik, Microsoft Intune eller andre administrationsprodukter, gælder. Filer scannes, trusler afhjælpes, og registreringsoplysninger rapporteres i konfigurationsværktøjet (f.eks. Configuration Manager eller Microsoft Defender Antivirus-appen på selve slutpunktet).  | 
 |  Passiv tilstand  |  I passiv tilstand Microsoft Defender Antivirus programmer ikke som antivirusapp, og trusler afhjælpes ikke af Microsoft Defender Antivirus. Trusler kan dog løses ved at [slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) i bloktilstand](edr-in-block-mode.md). <br/><br/> Filer scannes af Slutpunktsregistrering og -svar, og rapporter leveres til trusselsregistreringer, der deles med Defender for Endpoint-tjenesten. Du får muligvis vist beskeder Microsoft Defender Antivirus en kilde, selv når Microsoft Defender Antivirus er i passiv tilstand. <br/><br/> Når Microsoft Defender Antivirus er i passiv tilstand, kan du stadig administrere opdateringer [til Microsoft Defender Antivirus](manage-updates-baselines-microsoft-defender-antivirus.md), men du kan ikke flytte Microsoft Defender Antivirus  i aktiv tilstand, hvis dine enheder har et antivirusprodukt, der ikke er Microsoft, og som giver beskyttelse mod malware i realtid. <br/><br/> For optimalt sikkerhedsbeslag til forsvar og registrering af effektivitet skal du sørge for at få dine antivirus- og antimalwareopdateringer, også selvom Microsoft Defender Antivirus kører i passiv tilstand. Se [Administrere Microsoft Defender Antivirus opdateringer og anvende oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md). <br/><br/> Bemærk, at passiv tilstand kun understøttes på Windows Server 2012 R2 & 2016, når computeren er onboardet med den moderne[, samlede løsning](/microsoft-365/security/defender-endpoint/configure-server-endpoints).  | 
 |  Deaktiveret <br/><br/> eller <br/><br/> Fjernet  |  Når den er deaktiveret eller Microsoft Defender Antivirus, bruges den ikke som antivirusapp. Filer scannes ikke, og trusler bliver ikke løst. <br/><br/> Deaktivere eller fjerne Microsoft Defender Antivirus anbefales ikke generelt. Hvis det er muligt, skal du holde Microsoft Defender Antivirus i passiv tilstand, hvis du bruger en ikke-Microsoft-antimalware-/antivirusløsning. <br/><br/> I tilfælde hvor Microsoft Defender Antivirus deaktiveres automatisk, kan den aktiveres igen automatisk, hvis det ikke-Microsoft-antivirus-/antimalwareprodukt udløber eller på anden måde holder op med at levere beskyttelse i realtid mod virus, malware eller andre trusler. Den automatiske genaktivering af Microsoft Defender Antivirus hjælper med at sikre, at antivirusbeskyttelse bevares på dine slutpunkter. <br/><br/> Du kan også bruge [begrænset periodisk scanner](limited-periodic-scanning-microsoft-defender-antivirus.md), som fungerer sammen med Microsoft Defender Antivirus-programmet, så du med jævne mellemrum kan kontrollere, om der er trusler, hvis du bruger en antivirusapp, der ikke er Microsoft.  | 


## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus på Windows klienter](microsoft-defender-antivirus-in-windows-10.md)
- [Microsoft Defender Antivirus på Windows Server](microsoft-defender-antivirus-on-windows-server.md)
- [EDR i bloktilstand](edr-in-block-mode.md)
- [Få mere at Microsoft 365 om forebyggelse af datatab på slutpunkter](/microsoft-365/compliance/endpoint-dlp-learn-about)
