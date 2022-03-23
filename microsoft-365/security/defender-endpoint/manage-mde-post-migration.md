---
title: Administrer Microsoft Defender til slutpunkt efter overførslen
description: Nu hvor du har skiftet til Microsoft Defender for Endpoint, er det næste trin at administrere dine funktioner til trusselsbeskyttelse
keywords: efter overførslen, administrer, handlinger, vedligeholdelse, udnyttelse, Microsoft Defender til slutpunkt, edr
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
ms.topic: conceptual
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 2be934da8a87e02ead5c395097d90ccde46cb9d7
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/30/2021
ms.locfileid: "63593656"
---
# <a name="manage-microsoft-defender-for-endpoint-post-migration"></a>Administrer Microsoft Defender til slutpunkt efter overførslen

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Når du er flyttet fra din tidligere slutpunktsbeskyttelse og din antivirusløsning til Microsoft Defender til slutpunkt, er næste trin at administrere dine funktioner og egenskaber. Vi anbefaler at [Microsoft Endpoint Manager](/mem/endpoint-manager-overview), som [omfatter Microsoft Intune](/mem/intune/fundamentals/what-is-intune) [og Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction), til at administrere organisationens enheder og sikkerhedsindstillinger. Du kan dog bruge andre værktøjer/metoder, f.eks[. Gruppepolitik objekter i Azure Active Directory Domain Services](/azure/active-directory-domain-services/manage-group-policy).

I følgende tabel vises en liste over forskellige værktøjer/metoder, du kan bruge, med links til at få mere at vide.

<br/><br/>

|Værktøj/metode|Beskrivelse|
|---|---|
|**[Indsigt i håndtering af sikkerhedsrisici med trusler og](/windows/security/threat-protection/microsoft-defender-atp/tvm-dashboard-insights)** dashboard [i Microsoft 365 Defender](https://security.microsoft.com/) portalen|Trusselsdashboardet i & håndtering af sikkerhedsrisici indeholder brugbare oplysninger, som dit sikkerhedsteam kan bruge til at reducere eksponering og forbedre din organisations sikkerhedsposition. <br/><br/> Se [Trusselsoversigt & håndtering af sikkerhedsrisici](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) [oversigt over Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use).|
|**[Microsoft Intune](/mem/intune/fundamentals/what-is-intune)** (anbefales)|Microsoft Intune (Intune), som er en [komponent i Microsoft Endpoint Manager](/mem/endpoint-manager-overview), fokuserer på administration af mobilenheder (MDM) og administration af mobilapps (MAM). Med Intune styrer du, hvordan organisationens enheder bruges, herunder mobiltelefoner, tablets og bærbare computere. Du kan også konfigurere bestemte politikker til at styre programmer. <br/><br/> Se [Administrer Microsoft Defender for Endpoint ved hjælp af Intune](manage-mde-post-migration-intune.md).|
|**[Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction)**|Microsoft Endpoint Manager (Konfigurationsstyring), tidligere kaldet System Center Configuration Manager, er en komponent [af Microsoft Endpoint Manager](/mem/endpoint-manager-overview). Konfigurationsstyring er et effektivt værktøj til at administrere brugere, enheder og software. <br/><br/> Se [Administrer Microsoft Defender til slutpunkt med Konfigurationsstyring](manage-mde-post-migration-configuration-manager.md).|
|**[Gruppepolitik objekter i Azure Active Directory Domain Services](/azure/active-directory-domain-services/manage-group-policy)**|[Azure Active Directory-domænetjenester](/azure/active-directory-domain-services/overview) omfatter indbyggede Gruppepolitik-objekter til brugere og enheder. Du kan tilpasse den indbyggede Gruppepolitik efter behov for dit miljø, samt oprette brugerdefinerede Gruppepolitik objekter og organisationsenheder (OUs). <br/><br/> Se [Administrer Microsoft Defender til slutpunkt med Gruppepolitik objekter](manage-mde-post-migration-group-policy-objects.md).|
|**[PowerShell, WMI og MPCmdRun.exe](manage-mde-post-migration-other-tools.md)**|*Vi anbefaler at Microsoft Endpoint Manager (som omfatter Intune og Konfigurationsstyring) til at administrere funktioner til trusselsbeskyttelse på din organisations enheder. Du kan dog konfigurere nogle indstillinger, f.eks Microsoft Defender Antivirus indstillinger på individuelle enheder (slutpunkter) med PowerShell, WMI eller MPCmdRun.exe enhed.* <br/><br/> Du kan bruge PowerShell til at administrere Microsoft Defender Antivirus, udnytte beskyttelsen og dine regler for reduktion af angrebsoverfladen. Se [Konfigurer Microsoft Defender til slutpunkt med PowerShell](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-powershell). <br/><br/> Du kan bruge Windows Management Instrumentation (WMI) til at administrere Microsoft Defender Antivirus og udeladelse. Se [Konfigurer Microsoft Defender til slutpunkt med WMI](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi). <br/><br/> Du kan bruge Microsoft Malware Protection Command-Line Utility (MPCmdRun.exe) til at administrere Microsoft Defender Antivirus og undtagelser samt validere forbindelser mellem dit netværk og skyen. Se [Konfigurer Microsoft Defender til slutpunkt med MPCmdRun.exe](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe).|


## <a name="see-also"></a>Se også

- [Adressere falske positive/negativer i Microsoft Defender til slutpunkt](defender-endpoint-false-positives-negatives.md)
