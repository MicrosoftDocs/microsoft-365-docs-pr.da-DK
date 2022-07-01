---
title: Administrer Microsoft Defender for Endpoint efter overførsel
description: Nu, hvor du har skiftet til Microsoft Defender for Endpoint, er dit næste skridt at administrere dine trusselsbeskyttelsesfunktioner
keywords: efter migrering, administration, drift, vedligeholdelse, udnyttelse, Microsoft Defender for Endpoint,
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
ms.topic: conceptual
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 0103fea7a569b7462e455541e574fee58c719d24
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66601086"
---
# <a name="manage-microsoft-defender-for-endpoint-post-migration"></a>Administrer Microsoft Defender for Endpoint, efter overførsel

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Når du har flyttet fra din forrige slutpunktsbeskyttelses- og antivirusløsning til Microsoft Defender for Endpoint, er dit næste trin at administrere dine funktioner og egenskaber. Vi anbefaler, at du bruger [Microsoft Endpoint Manager](/mem/endpoint-manager-overview), som omfatter [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) og [Microsoft Endpoint-Configuration Manager](/mem/configmgr/core/understand/introduction), til at administrere organisationens enheder og sikkerhedsindstillinger. Du kan dog bruge andre værktøjer/metoder, f.eks. [Gruppepolitik Objekter i Azure Active Directory-domæneservices](/azure/active-directory-domain-services/manage-group-policy).

I følgende tabel vises forskellige værktøjer/metoder, du kan bruge, med links til at få mere at vide.

<br/><br/>

|Værktøj/metode|Beskrivelse|
|---|---|
|**[Dashboardindsigt i administration af trusler og sårbarheder](/windows/security/threat-protection/microsoft-defender-atp/tvm-dashboard-insights)** på [Microsoft 365 Defender-portalen](https://security.microsoft.com/)|Truslen & dashboard til administration af sårbarheder indeholder handlingsrelaterede oplysninger, som dit sikkerhedsteam kan bruge til at reducere eksponeringen og forbedre din organisations sikkerhedsholdning. <br/><br/> Se [Trussel & administration af sårbarheder](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) og [Oversigt over Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use).|
|**[Microsoft Intune](/mem/intune/fundamentals/what-is-intune)** (anbefales)|Microsoft Intune (Intune), der er en komponent [i Microsoft Endpoint Manager](/mem/endpoint-manager-overview), fokuserer på administration af mobilenheder (MDM) og administration af mobilapps (MAM). Med Intune kan du styre, hvordan organisationens enheder bruges, herunder mobiltelefoner, tablets og bærbare computere. Du kan også konfigurere specifikke politikker til at styre programmer. <br/><br/> Se [Administrer Microsoft Defender for Endpoint ved hjælp af Intune](manage-mde-post-migration-intune.md).|
|**[Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction)**|Microsoft Endpoint Manager (Configuration Manager), tidligere kaldet System Center Configuration Manager, er en komponent i [Microsoft Endpoint Manager](/mem/endpoint-manager-overview). Configuration Manager er et effektivt værktøj til at administrere dine brugere, enheder og software. <br/><br/> Se [Administrer Microsoft Defender for Endpoint med Configuration Manager](manage-mde-post-migration-configuration-manager.md).|
|**[Gruppepolitik objekter i Azure Active Directory-domæneservices](/azure/active-directory-domain-services/manage-group-policy)**|[Azure Active Directory-domæneservices](/azure/active-directory-domain-services/overview) indeholder indbyggede Gruppepolitik objekter til brugere og enheder. Du kan tilpasse de indbyggede Gruppepolitik objekter efter behov i dit miljø samt oprette brugerdefinerede Gruppepolitik objekter og organisationsenheder. <br/><br/> Se [Administrer Microsoft Defender for Endpoint med Gruppepolitik objekter](manage-mde-post-migration-group-policy-objects.md).|
|**[PowerShell, WMI og MPCmdRun.exe](manage-mde-post-migration-other-tools.md)**|*Vi anbefaler, at du bruger Microsoft Endpoint Manager (som omfatter Intune og Configuration Manager) til at administrere trusselsbeskyttelsesfunktioner på din organisations enheder. Du kan dog konfigurere nogle indstillinger, f.eks. Microsoft Defender Antivirus-indstillinger på individuelle enheder (slutpunkter) med PowerShell, WMI eller værktøjet MPCmdRun.exe.* <br/><br/> Du kan bruge PowerShell til at administrere Microsoft Defender Antivirus, udnytte beskyttelse og dine regler for reduktion af angrebsoverfladen. Se [Konfigurer Microsoft Defender for Endpoint med PowerShell](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-powershell). <br/><br/> Du kan bruge WMI (Windows Management Instrumentation) til at administrere Microsoft Defender Antivirus og undtagelser. Se [Konfigurer Microsoft Defender for Endpoint med WMI](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi). <br/><br/> Du kan bruge Microsoft Malware Protection Command-Line Utility (MPCmdRun.exe) til at administrere Microsoft Defender Antivirus og undtagelser samt validere forbindelser mellem dit netværk og cloudmiljøet. Se [Konfigurer Microsoft Defender for Endpoint med MPCmdRun.exe](manage-mde-post-migration-other-tools.md#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe).|


## <a name="see-also"></a>Se også

- [Adresser falske positive/negativer i Microsoft Defender for Endpoint](defender-endpoint-false-positives-negatives.md)
