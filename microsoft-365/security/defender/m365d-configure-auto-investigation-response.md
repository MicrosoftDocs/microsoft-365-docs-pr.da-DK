---
title: Konfigurer automatiserede undersøgelses- og svarfunktioner i Microsoft 365 Defender
description: Konfigurer automatiseret undersøgelse og svar med selvhelbredende i Microsoft 365 Defender
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
ms.openlocfilehash: 51efeb57c6670f9c798fa254bb0a6242b30c5700
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944365"
---
# <a name="configure-automated-investigation-and-response-capabilities-in-microsoft-365-defender"></a>Konfigurer automatiserede undersøgelses- og svarfunktioner i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft 365 Defender omfatter effektive [automatiserede undersøgelses- og svarfunktioner](m365d-autoir.md), der kan spare dit team for sikkerhedshandlinger meget tid og kræfter. Med [selvreparerende](m365d-autoir.md#how-automated-investigation-and-self-healing-works) funktioner efterligner disse funktioner de trin, som en sikkerhedsanalytiker ville udføre for at undersøge og reagere på trusler– kun hurtigere og med større evne til at skalere.

I denne artikel beskrives det, hvordan du konfigurerer automatiseret undersøgelse og svar i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> med disse trin:

1. [Gennemse forudsætningerne](#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).
2. [Gennemse eller rediger automatiseringsniveauet for enhedsgrupper](#review-or-change-the-automation-level-for-device-groups).
3. [Gennemse politikker for sikkerhed og beskeder i Office 365](#review-your-security-and-alert-policies-in-office-365).
4. [Kontrollér, at Microsoft 365 Defender er slået til](#make-sure-microsoft-365-defender-is-turned-on).

Når du er konfigureret, kan du derefter [få vist og administrere afhjælpningshandlinger i Løsningscenter](m365d-autoir-actions.md).

## <a name="prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender"></a>Forudsætninger for automatiseret undersøgelse og svar i Microsoft 365 Defender

<br>

****

|Krav|Detaljer|
|---|---|
|Abonnementskrav|Et af disse abonnementer: <ul><li>Microsoft 365 E5</li><li>Microsoft 365 A5</li><li>Microsoft 365 E3 med tilføjelsesprogrammet Microsoft 365 E5 Sikkerhed</li><li>Microsoft 365 A3 med tilføjelsesprogrammet Microsoft 365 A5 Sikkerhed</li><li>Office 365 E5 plus Enterprise Mobility + Security E5 plus Windows E5</li></ul> <p> Se [Microsoft 365 Defender licenskrav](./prerequisites.md#licensing-requirements).|
|Netværkskrav|<ul><li>[Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp) aktiveret</li><li>[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) konfigureret</li><li>[Microsoft Defender for Identity integration](/cloud-app-security/mdi-integration)</li></ul>|
|krav til Windows enhed|<ul><li>Windows 11</li><li>Windows 10, version 1709 eller nyere installeret (se [Windows udgivelsesoplysninger](/windows/release-information/))</li><li>Følgende trusselsbeskyttelsestjenester er konfigureret:<ul><li>[Microsoft Defender for Endpoint](../defender-endpoint/configure-endpoints.md)</li><li>[Microsoft Defender Antivirus](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features)</li></ul></li></ul>|
|Beskyttelse af mailindhold og Office filer|[Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/defender-for-office-365#configure-atp-policies) konfigureret|
|Tilladelser|Hvis du vil konfigurere automatiserede undersøgelses- og svarfunktioner, skal du have tildelt rollen Global administrator eller Sikkerhedsadministrator enten i Azure Active Directory (<https://portal.azure.com>) eller i Microsoft 365 Administration (<https://admin.microsoft.com>). <p> Hvis du vil hente de tilladelser, der er nødvendige for at arbejde med automatiserede undersøgelses- og svarfunktioner, f.eks. gennemse, godkende eller afvise ventende handlinger, skal du se [Påkrævede tilladelser til Opgaver i Løsningscenter](m365d-action-center.md#required-permissions-for-action-center-tasks).|
|

## <a name="review-or-change-the-automation-level-for-device-groups"></a>Gennemse eller rediger automatiseringsniveauet for enhedsgrupper

Om automatiserede undersøgelser kører, og om afhjælpningshandlinger udføres automatisk eller kun efter godkendelse af dine enheder, afhænger af visse indstillinger, f.eks. organisationens politikker for enhedsgruppe. Gennemse det konfigurerede automatiseringsniveau for dine enhedsgruppepolitikker.

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Gå til **Indstillinger** >  **EndpointsDevice-grupper** >  under **Tilladelser**.

3. Gennemse politikker for enhedsgruppe. Se især kolonnen **Automation-niveau** . Vi anbefaler, at du bruger **Fuld – afhjælper trusler automatisk**.  Du skal muligvis oprette eller redigere dine enhedsgrupper for at få det ønskede automatiseringsniveau. Du kan få hjælp til denne opgave i følgende artikler:
   - [Sådan afhjælpes trusler](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations#how-threats-are-remediated)
   - [Opret og administrer enhedsgrupper](/windows/security/threat-protection/microsoft-defender-atp/machine-groups)

## <a name="review-your-security-and-alert-policies-in-office-365"></a>Gennemse dine politikker for sikkerhed og beskeder i Office 365

Microsoft leverer indbyggede [beskedpolitikker](../../compliance/alert-policies.md) , der hjælper med at identificere visse risici. Disse risici omfatter Exchange misbrug af administratortilladelser, malwareaktivitet, potentielle eksterne og interne trusler og risici for styring af oplysninger. Nogle beskeder kan udløse [automatiseret undersøgelse og svar i Office 365](../office-365-security/office-365-air.md). Sørg for, at dine [Defender for Office 365](../office-365-security/defender-for-office-365.md) funktioner er konfigureret korrekt.

Selvom visse beskeder og sikkerhedspolitikker kan udløse automatiserede undersøgelser, *udføres der ingen afhjælpningshandlinger automatisk for mail og indhold*. I stedet afventer alle afhjælpningshandlinger for mail- og mailindhold godkendelse af dit team for sikkerhedshandlinger i [Løsningscenter](m365d-action-center.md).

Sikkerhedsindstillinger i Office 365 hjælpe med at beskytte mail og indhold. Hvis du vil have vist eller ændre disse indstillinger, skal du følge vejledningen i [Beskyt mod trusler](../office-365-security/protect-against-threats.md).

1. På <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a> skal du gå til **Politikker & Regler** \> **Trusselspolitikker**.

2. Kontrollér, at alle følgende politikker er konfigureret. Hvis du vil have hjælp og anbefalinger, skal du se [Beskyt mod trusler](/microsoft-365/security/office-365-security/protect-against-threats).
   - [Antimalware](../office-365-security/protect-against-threats.md#part-1---anti-malware-protection-in-eop)
   - [Anti-phishing](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
   - [Sikre vedhæftede filer](../office-365-security/protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365)
   - [Sikre links](../office-365-security/protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365)
   - [Anti-spam](../office-365-security/protect-against-threats.md#part-3---anti-spam-protection-in-eop)

3. Sørg for, at [Pengeskab Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams](../office-365-security/mdo-for-spo-odb-and-teams.md) er slået til.

4. Sørg for, at [zap (automatisk tøm på nul timer) i Exchange Online](../office-365-security/zero-hour-auto-purge.md) er i kraft.

5. (Dette trin er valgfrit). Gennemse dine [Office 365 beskedpolitikker](../../compliance/alert-policies.md) på Microsoft Purview-overholdelsesportalen ([https://compliance.microsoft.com/compliancepolicies](https://compliance.microsoft.com/compliancepolicies)). Der findes flere standardpolitikker for beskeder i kategorien Trusselsadministration. Nogle af disse beskeder kan udløse automatiseret undersøgelse og svar. Du kan få mere at vide under [Standardpolitikker for beskeder](../../compliance/alert-policies.md#default-alert-policies).

## <a name="make-sure-microsoft-365-defender-is-turned-on"></a>Sørg for, at Microsoft 365 Defender er slået til

:::image type="content" source="../../media/mtp-enable/mtp-on.png" alt-text="Den venstre navigationsrude i Microsoft 365 Defender portalen, når Microsoft 365 Defender er slået til" lightbox="../../media/mtp-enable/mtp-on.png":::

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>

2. I navigationsruden skal du se efter **Hændelser & Beskeder**, **Jagt** og **Handlingscenter** som vist på det foregående billede.
   - Hvis du ser **Hændelser & Beskeder**, **Jagt** og **Handlingscenter**, er Microsoft 365 Defender slået til. Se afsnittet [Gennemse eller rediger automatiseringsniveauet for enhedsgrupper](#review-or-change-the-automation-level-for-device-groups) i denne artikel.
   - Hvis du *ikke* kan se **Hændelser**, **Handlingscenter** eller **Jagt**, er Microsoft 365 Defender muligvis ikke slået til. I dette tilfælde [skal du besøge Handlingscenter](m365d-action-center.md).

> [!TIP]
> Har du brug for hjælp? Se [Slå Microsoft 365 Defender](m365d-enable.md) til.

## <a name="next-steps"></a>Næste trin

- [Afhjælpningshandlinger i Microsoft 365 Defender](m365d-remediation-actions.md)
- [Besøg Løsningscenter](m365d-action-center.md)
