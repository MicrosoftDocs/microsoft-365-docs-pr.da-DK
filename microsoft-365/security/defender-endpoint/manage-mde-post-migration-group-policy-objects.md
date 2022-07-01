---
title: Administrer Microsoft Defender for Endpoint ved hjælp af Gruppepolitik objekter
description: Få mere at vide om, hvordan du administrerer Microsoft Defender for Endpoint med Gruppepolitik objekter
keywords: efter migrering, administration, drift, vedligeholdelse, udnyttelse, PowerShell, Microsoft Defender for Endpoint, edr
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
ms.topic: article
ms.reviewer: chventou
ms.openlocfilehash: 3c7c72597416bda80894f8d44fbf5dbba3d58808
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603874"
---
# <a name="manage-microsoft-defender-for-endpoint-with-group-policy-objects"></a>Administrer Microsoft Defender for Endpoint med Gruppepolitik objekter

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Vi anbefaler, at du bruger [Microsoft Endpoint Manager](/mem) til at administrere organisationens trusselsbeskyttelsesfunktioner for enheder (også kaldet slutpunkter). Endpoint Manager omfatter [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) og [Microsoft Endpoint-Configuration Manager](/mem/configmgr/core/understand/introduction). **[Få mere at vide om Endpoint Manager](/mem/endpoint-manager-overview)**.

Du kan bruge Gruppepolitik-objekter i Azure Active Directory-domæneservices til at administrere nogle indstillinger i Microsoft Defender for Endpoint.

## <a name="configure-microsoft-defender-for-endpoint-with-group-policy-objects"></a>Konfigurer Microsoft Defender for Endpoint med Gruppepolitik objekter

> [!NOTE]
> Hvis du bruger [den nye, samlede Microsoft Defender for Endpoint løsning til Windows Server 2012 R2 og 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview), skal du sikre dig, at du bruger de nyeste ADMX-filer i dit centrale lager for at få adgang til de korrekte Microsoft Defender for Endpoint politikindstillinger. Se [Under Sådan opretter og administrerer du Central Store til Gruppepolitik administrative skabeloner i Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) og downloader de nyeste filer **til brug sammen med Windows 10**. 

I følgende tabel vises en liste over forskellige opgaver, du kan udføre for at konfigurere Microsoft Defender for Endpoint med Gruppepolitik Objekter.

|Opgave|Ressourcer til at få mere at vide|
|---|---|
|**Administrer indstillinger for bruger- og computerobjekter** <br/><br/> *Tilpas indbyggede Gruppepolitik objekter, eller opret brugerdefinerede Gruppepolitik objekter og organisationsenheder, så de passer til organisationens behov.*|[Administrer Gruppepolitik i et Azure Active Directory-domæneservices administreret domæne](/azure/active-directory-domain-services/manage-group-policy)|
|**Konfigurer Microsoft Defender Antivirus** <br/><br/> *Konfigurer antivirusfunktioner & funktioner, herunder politikindstillinger, undtagelser, afhjælpning og planlagte scanninger på din organisations enheder (også kaldet slutpunkter).*|[Brug Gruppepolitik indstillinger til at konfigurere og administrere Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus) <br/><br/> [Brug Gruppepolitik til at aktivere skybaseret beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-group-policy-to-enable-cloud-delivered-protection)|
|**Administrer din organisations regler for reduktion af angrebsoverfladen** <br/><br/> *Tilpas reglerne for reduktion af angrebsoverfladen ved at udelade filer & mapper eller ved at føje brugerdefineret tekst til beskedbeskeder, der vises på brugernes enheder.*|[Tilpas regler for reduktion af angrebsoverfladen med Gruppepolitik objekter](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment-implement)|
|**Administrer beskyttelsesindstillinger for udnyttelse** <br/><br/> *Du kan tilpasse dine indstillinger for beskyttelse mod udnyttelse, importere en konfigurationsfil og derefter bruge Gruppepolitik til at installere den pågældende konfigurationsfil.*|[Tilpas beskyttelsesindstillinger for udnyttelse](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [Importér, eksportér og udrul konfigurationer af Exploit Protection](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml) <br/><br/> [Brug Gruppepolitik til at distribuere konfigurationen](/microsoft-365/security/defender-endpoint/import-export-exploit-protection-emet-xml#use-group-policy-to-distribute-the-configuration)|
|**Aktivér Netværksbeskyttelse** for at forhindre medarbejdere i at bruge apps, der har skadeligt indhold på internettet <br/><br/> *Vi anbefaler, at du først bruger [overvågningstilstand](/microsoft-365/security/defender-endpoint/evaluate-network-protection) til netværksbeskyttelse i et testmiljø for at se, hvilke apps der blokeres, før de udrulles.*|[Slå netværksbeskyttelse til ved hjælp af Gruppepolitik](/microsoft-365/security/defender-endpoint/enable-network-protection#group-policy)|
|**Konfigurer kontrolleret mappeadgang** for at beskytte mod ransomware <br/><br/> *[Kontrolleret mappeadgang](/microsoft-365/security/defender-endpoint/controlled-folders) kaldes også antiransomware-beskyttelse.*|[Aktivér kontrolleret mappeadgang ved hjælp af Gruppepolitik](/microsoft-365/security/defender-endpoint/enable-controlled-folders#group-policy)|
|**Konfigurer Microsoft Defender SmartScreen** for at beskytte mod skadelige websteder og filer på internettet.|[Konfigurer Indstillinger for Microsoft Defender SmartScreen Gruppepolitik og administration af mobilenheder (MDM) ved hjælp af Gruppepolitik](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#group-policy-settings)|
|**Konfigurer kryptering og BitLocker** for at beskytte oplysninger på din organisations enheder, der kører Windows|[Indstillinger for BitLocker-Gruppepolitik](/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings)|
|**Konfigurer Microsoft Defender Credential Guard** for at beskytte mod angreb mod tyveri af legitimationsoplysninger|[Aktivér Windows Defender Credential Guard ved hjælp af Gruppepolitik](/windows/security/identity-protection/credential-guard/credential-guard-manage#enable-windows-defender-credential-guard-by-using-group-policy)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Konfigurer Microsoft 365 Defender-portalen

Hvis du ikke allerede har gjort det, kan du konfigurere din Microsoft 365 Defender-portal til at få vist beskeder, konfigurere funktioner til trusselsbeskyttelse og få vist detaljerede oplysninger om din organisations overordnede sikkerhedsholdning. Se [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Du kan også konfigurere, om og hvilke funktioner slutbrugerne kan se på portalen Microsoft 365 Defender.

- [Oversigt over Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Beskyttelse af slutpunkter: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Næste trin

- [Få et overblik over Håndtering af trusler og sikkerhedsrisici](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Besøg dashboardet til Microsoft 365 Defender-portalens sikkerhedshandlinger](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Administrer Microsoft Defender for Endpoint med Intune](manage-mde-post-migration-intune.md)
