---
title: Administrer Microsoft Defender til slutpunkt ved hjælp af Gruppepolitik-objekter
description: Få mere at vide om, hvordan du administrerer Microsoft Defender til slutpunkt med Gruppepolitik-objekter
keywords: efter overførslen, administrere, handlinger, vedligeholdelse, udnyttelse, PowerShell, Microsoft Defender til slutpunkt, edr
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 2155c72d7008bf3669a1908b3fd866877eb36a7c
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/09/2022
ms.locfileid: "63593036"
---
# <a name="manage-microsoft-defender-for-endpoint-with-group-policy-objects"></a>Administrer Microsoft Defender til slutpunkt med Gruppepolitik objekter

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Vi anbefaler at [Microsoft Endpoint Manager til](/mem) at administrere organisationens funktioner til trusselsbeskyttelse af enheder (også kaldet slutpunkter). Endpoint Manager omfatter [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) og [Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction). **[Få mere at vide Endpoint Manager](/mem/endpoint-manager-overview)**.

Du kan bruge Gruppepolitik i Azure Active Directory Domain Services til at administrere nogle indstillinger i Microsoft Defender til slutpunkt.

## <a name="configure-microsoft-defender-for-endpoint-with-group-policy-objects"></a>Konfigurer Microsoft Defender til slutpunkt med Gruppepolitik objekter

> [!NOTE]
> Hvis du bruger den nye[, samlede Microsoft Defender for Endpoint-løsning til Windows Server 2012 R2 og 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview), skal du sikre dig, at du bruger de nyeste ADMX-filer i din central butik for at få adgang til de korrekte politikindstillinger for Microsoft Defender til slutpunkt. Se Sådan opretter og administrerer du [Central Store til Gruppepolitik](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) administrative skabeloner i Windows og download de nyeste filer til brug med **Windows 10**. 

I følgende tabel vises forskellige opgaver, du kan udføre for at konfigurere Microsoft Defender til slutpunkt med Gruppepolitik-objekter.

<br/><br/>

|Opgave|Ressourcer til at få mere at vide|
|---|---|
|**Administrere indstillinger for bruger- og computerobjekter** <br/><br/> *Tilpas indbyggede objekter Gruppepolitik objekter, eller opret brugerdefinerede objekter Gruppepolitik organisationsenheder, der passer til dine virksomhedsbehov.*|[Administrer Gruppepolitik i et Azure Active Directory domænetjenester administreret domæne](/azure/active-directory-domain-services/manage-group-policy)|
|**Konfigurer Microsoft Defender Antivirus** <br/><br/> *Konfigurer antivirusfunktioner & funktioner, herunder politikindstillinger, udeladelse, afhjælpning og planlagte scanninger på din organisations enheder (også kaldet slutpunkter).*|[Brug Gruppepolitik til at konfigurere og administrere Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus) <br/><br/> [Brug Gruppepolitik til at aktivere beskyttelse, der leveres i skyen](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-group-policy-to-enable-cloud-delivered-protection)|
|**Administrer din organisations regler for reduktion af angrebsoverfladen** <br/><br/> *Tilpas dine reduktionsregler for angrebsoverfladen ved at udelukke filer & mapper eller ved at føje brugerdefineret tekst til meddelelsesbeskeder, der vises på brugernes enheder.*|[Tilpas regler for reduktion af angrebsoverfladen med Gruppepolitik objekter](/microsoft-365/security/defender-endpoint/customize-attack-surface-reduction#use-group-policy-to-exclude-files-and-folders)|
|**Administrer indstillinger for udnyttelse af beskyttelse** <br/><br/> *Du kan tilpasse dine indstillinger for udnyttelsesbeskyttelse, importere en konfigurationsfil og derefter bruge Gruppepolitik til at installere den pågældende konfigurationsfil.*|[Tilpasse indstillinger for udnyttelse af beskyttelse](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [Importere, eksportere og implementere konfigurationer af exploit protection](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml) <br/><br/> [Brug Gruppepolitik til at distribuere konfigurationen](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml#use-group-policy-to-distribute-the-configuration)|
|**Aktivér netværksbeskyttelse** for at forhindre medarbejdere i at bruge apps med skadeligt indhold på internettet <br/><br/> *Vi anbefaler, at [du først bruger overvågningstilstand](/microsoft-365/security/defender-endpoint/evaluate-network-protection) for netværksbeskyttelse i et testmiljø for at se, hvilke apps der blev blokeret før udrulning.*|[Slå netværksbeskyttelse til ved hjælp Gruppepolitik](/microsoft-365/security/defender-endpoint/enable-network-protection#group-policy)|
|**Konfigurer styret mappeadgang for** at beskytte mod ransomware <br/><br/> *[Kontrolleret mappeadgang](/microsoft-365/security/defender-endpoint/controlled-folders) kaldes også antiransomwarebeskyttelse.*|[Aktivér styret mappeadgang ved hjælp af Gruppepolitik](/microsoft-365/security/defender-endpoint/enable-controlled-folders#group-policy)|
|**Konfigurer Microsoft Defender SmartScreen** at beskytte mod skadelige websteder og filer på internettet.|[Konfigurere Microsoft Defender SmartScreen Gruppepolitik og mdm-indstillinger (mobile device management) ved hjælp Gruppepolitik](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#group-policy-settings)|
|**Konfigurer kryptering og BitLocker** til at beskytte oplysninger på organisationens enheder, der kører Windows|[BitLocker Gruppepolitik indstillinger](/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings)|
|**Konfigurer Microsoft Defender Credential Guard for at beskytte** dig mod angreb med legitimationstyveri|[Aktivér Windows Defender Credential Guard ved hjælp af Gruppepolitik](/windows/security/identity-protection/credential-guard/credential-guard-manage#enable-windows-defender-credential-guard-by-using-group-policy)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Konfigurere din Microsoft 365 Defender portal

Hvis du ikke allerede har gjort det, skal du konfigurere din Microsoft 365 Defender-portal for at få vist beskeder, konfigurere funktioner til trusselsbeskyttelse og få vist detaljerede oplysninger om organisationens overordnede sikkerhedslag. Se [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Du kan også konfigurere, om og hvilke funktioner slutbrugere kan se i Microsoft 365 Defender portal.

- [Oversigt over Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Slutpunktsbeskyttelse: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Næste trin

- [Få et overblik over Håndtering af trusler og sikkerhedsrisici](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Gå til Microsoft 365 Defender portalsikkerhedsdashboard](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Administrer Microsoft Defender til slutpunkt med Intune](manage-mde-post-migration-intune.md)
