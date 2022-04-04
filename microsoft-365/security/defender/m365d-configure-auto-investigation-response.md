---
title: Konfigurer automatiserede undersøgelses- og svarfunktioner i Microsoft 365 Defender
description: Konfigurer automatiseret undersøgelse og svar med selvbetjening i Microsoft 365 Defender
search.appverid: MET150
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
f1.keywords: CSH
ms.technology: m365d
ms.openlocfilehash: 0e38dc36ca85425c033d2b8fd4828043b4043f1a
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499413"
---
# <a name="configure-automated-investigation-and-response-capabilities-in-microsoft-365-defender"></a>Konfigurer automatiserede undersøgelses- og svarfunktioner i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft 365 Defender indeholder effektive [funktioner til automatisk undersøgelse og svar,](m365d-autoir.md) som kan spare meget tid og besvær for dit sikkerhedsteam. Med [selvbetjening](m365d-autoir.md#how-automated-investigation-and-self-healing-works) efterligner disse egenskaber de trin, en sikkerhedsanalytiker ville tage for at undersøge og reagere på trusler, kun hurtigere og med flere muligheder for skalering.

Denne artikel beskriver, hvordan du konfigurerer automatiseret undersøgelse og svar <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> med disse trin:

1. [Gennemgå forudsætningerne](#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).
2. [Gennemse eller rediger automatiseringsniveauet for enhedsgrupper](#review-or-change-the-automation-level-for-device-groups).
3. [Gennemse dine sikkerhed- og beskedpolitikker i Office 365](#review-your-security-and-alert-policies-in-office-365).
4. [Kontrollér, Microsoft 365 Defender er slået til](#make-sure-microsoft-365-defender-is-turned-on).

Når du er færdig med at konfigurere, kan du derefter [få vist og administrere afhjælpningshandlinger i Handlingscenter](m365d-autoir-actions.md).

## <a name="prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender"></a>Forudsætninger for automatiseret undersøgelse og svar i Microsoft 365 Defender

<br>

****

|Krav|Detaljer|
|---|---|
|Abonnementskrav|Et af disse abonnementer: <ul><li>Microsoft 365 E5</li><li>Microsoft 365 A5</li><li>Microsoft 365 E3 med Microsoft 365 E5 Sikkerhed-tilføjelsesprogrammet</li><li>Microsoft 365 A3 med Microsoft 365 A5 Security-tilføjelsesprogrammet</li><li>Office 365 E5 plus Enterprise Mobility + Security E5 plus Windows E5</li></ul> <p> Se [Microsoft 365 Defender licenskrav](./prerequisites.md#licensing-requirements).|
|Netværkskrav|<ul><li>[Microsoft Defender for Identity aktiveret](/azure-advanced-threat-protection/what-is-atp)</li><li>[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) konfigureret</li><li>[Microsoft Defender for Identity integration](/cloud-app-security/mdi-integration)</li></ul>|
|Windows af enhedskrav|<ul><li>Windows 11</li><li>Windows 10, version 1709 eller nyere installeret (se [Windows udgivelsesoplysninger](/windows/release-information/))</li><li>Følgende trusselsbeskyttelsestjenester er konfigureret:<ul><li>[Microsoft Defender for Endpoint](../defender-endpoint/configure-endpoints.md)</li><li>[Microsoft Defender Antivirus](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features)</li></ul></li></ul>|
|Beskyttelse af mailindhold og Office filer|[Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/defender-for-office-365#configure-atp-policies) konfigureret|
|Tilladelser|For at konfigurere automatiserede undersøgelses- og svarfunktioner skal du have den globale administrator- eller sikkerhedsadministratorrolle tildelt i enten Azure Active Directory (<https://portal.azure.com>) eller i Microsoft 365 Administration (<https://admin.microsoft.com>). <p> Hvis du vil have de nødvendige tilladelser til at arbejde med automatiseret undersøgelse og svarmuligheder, f.eks. gennemgang, godkendelse eller afvisning af afventende handlinger, skal du se Påkrævede tilladelser [til handlingscenteropgaver](m365d-action-center.md#required-permissions-for-action-center-tasks).|
|

## <a name="review-or-change-the-automation-level-for-device-groups"></a>Gennemse eller rediger automatiseringsniveauet for enhedsgrupper

Om automatiserede undersøgelser kører, og om afhjælpningshandlinger skal løses automatisk eller kun efter godkendelse af dine enheder, afhænger af bestemte indstillinger, f.eks. din organisations politikker for enhedsgrupper. Gennemgå det konfigurerede automatiseringsniveau for din enheds gruppepolitikker.

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Gå til **Indstillinger** >  **EndpointsEnheder** >  under **Tilladelser**.

3. Gennemse politikkerne for din enhedsgruppe. Nærmere bestemt skal du kigge på **kolonnen på automatiseringsniveau** . Vi anbefaler, **at du bruger Fuld – afhjulpet trusler automatisk**.  Det kan være nødvendigt at oprette eller redigere dine enhedsgrupper for at få det ønskede automatiseringsniveau. Hvis du vil have hjælp til denne opgave, skal du se følgende artikler:
   - [Sådan afhjælpes trusler](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations#how-threats-are-remediated)
   - [Opret og administrer enhedsgrupper](/windows/security/threat-protection/microsoft-defender-atp/machine-groups)

## <a name="review-your-security-and-alert-policies-in-office-365"></a>Gennemse dine sikkerhed- og beskedpolitikker i Office 365

Microsoft leverer indbyggede advarselspolitikker [, der](../../compliance/alert-policies.md) hjælper med at identificere visse risici. Disse risici omfatter Exchange misbrug af administratortilladelser, malwareaktivitet, potentielle eksterne og interne trusler og risiko for informationsstyring. Nogle beskeder kan udløse [automatiseret undersøgelse og svar Office 365](../office-365-security/office-365-air.md). Sørg for, [Defender for Office 365](../office-365-security/defender-for-office-365.md) alle funktioner er konfigureret korrekt.

Selvom visse advarsler og sikkerhedspolitikker kan udløse automatiserede undersøgelser, bliver der ikke taget nogen *afhjælpningshandlinger automatisk for mails og indhold*. I stedet kan alle afhjælpningshandlinger for mail- og mailindhold vente med godkendelse fra dit sikkerhedsteam i [handlingscenteret](m365d-action-center.md).

Sikkerhedsindstillinger i Office 365 beskytte mail og indhold. Hvis du vil have vist eller ændre disse indstillinger, skal du følge [vejledningen i Beskyt dig mod trusler](../office-365-security/protect-against-threats.md).

1. I portalen <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender skal</a> du gå til **Politikker & Politikker for trussel** \> **om sikkerhed og regler**.

2. Sørg for, at alle følgende politikker er konfigureret. Hvis du vil have hjælp og anbefalinger, [skal du se Beskyt dig mod trusler](/microsoft-365/security/office-365-security/protect-against-threats).
   - [Antimalware](../office-365-security/protect-against-threats.md#part-1---anti-malware-protection-in-eop)
   - [Antiphishing](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
   - [Pengeskab vedhæftede filer](../office-365-security/protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365)
   - [Sikre links](../office-365-security/protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365)
   - [Antispam](../office-365-security/protect-against-threats.md#part-3---anti-spam-protection-in-eop)

3. Kontrollér, [Pengeskab Vedhæftede filer til SharePoint, OneDrive, og Microsoft Teams](../office-365-security/mdo-for-spo-odb-and-teams.md) er slået til.

4. Sørg for[, at automatisk tømning uden time (ZAP) Exchange Online](../office-365-security/zero-hour-auto-purge.md) er i kraft.

5. Dette trin er valgfrit. Gennemse dine [Office 365 i](../../compliance/alert-policies.md) Microsoft 365 Overholdelsescenter ([https://compliance.microsoft.com/compliancepolicies](https://compliance.microsoft.com/compliancepolicies)). Flere standardbeskedpolitikker er i kategorien Trusselsadministration. Nogle af disse beskeder kan udløse automatiseret undersøgelse og svar. Du kan få mere at vide under [Standardbeskedpolitikker](../../compliance/alert-policies.md#default-alert-policies).

## <a name="make-sure-microsoft-365-defender-is-turned-on"></a>Kontrollér, Microsoft 365 Defender er slået til

:::image type="content" source="../../media/mtp-enable/mtp-on.png" alt-text="Den venstre navigationsrude i Microsoft 365 Defender, når Microsoft 365 Defender er slået til" lightbox="../../media/mtp-enable/mtp-on.png":::

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>

2. I navigationsruden skal du se efter **Hændelser & Beskeder****, Jagt** og Handlingscenter som vist på  det foregående billede.
   - Hvis du kan **se Hændelser &,** På **jagt** **og handlingscenter**, Microsoft 365 Defender er slået til. Se afsnittet [Gennemse eller rediger automatiseringsniveauet for enhedsgrupper](#review-or-change-the-automation-level-for-device-groups) i denne artikel.
   - Hvis du ikke *kan* se **Hændelser**, **Handlingscenter eller** **Jagt,** er Microsoft 365 Defender måske ikke slået til. I dette tilfælde skal [du gå til Handlingscenter](m365d-action-center.md).

> [!TIP]
> Har du brug for hjælp? Se [Slå Microsoft 365 Defender til](m365d-enable.md).

## <a name="next-steps"></a>Næste trin

- [Afhjælpningshandlinger i Microsoft 365 Defender](m365d-remediation-actions.md)
- [Gå til handlingscenter](m365d-action-center.md)
