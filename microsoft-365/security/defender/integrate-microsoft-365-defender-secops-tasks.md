---
title: Trin 6. Identificer SOC-vedligeholdelsesopgaver
description: Identificer SOC-vedligeholdelsesopgaver, Microsoft 365 Defender du integrerer i dine sikkerhedshandlinger.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365, hændelsesrespons, cyberangreb, secops, sikkerhedshandlinger, soc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 33dd846b54072551d2624bec0e025dad9f269b03
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592517"
---
# <a name="step-6-identify-soc-maintenance-tasks"></a>Trin 6. Identificer SOC-vedligeholdelsesopgaver

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Her er de periodiske eller nødvendige opgaver til at vedligeholde din SOC for Microsoft 365 Defender.

| Aktivitet  | Beskrivelse | Kadencer | Team tildelt |
|:-------|:-----|:-------|:-------|
| Samarbejde om tjenesteadministration med SOC-Teams   | Administration af eksterne tjenester som sporing af aktiver (CMDB), programlicens (nye SaaS-licenser), enhedskøb (opgraderinger eller fornyelse af enhedsinstallationer) og andre ændringer i hele Microsoft 365-lejeren (Intune, Microsoft 365 og andre), der kan påvirke installationen af Microsoft 365 Defender-produkter. | Ugentligt og efter behov   | Teknisk & SecOps | 
| Opdatere kampagner til forebyggelse af phishing og datatab | Inkorkorrektur af SOC-use case og erfaringer fra udvidet organisation (HR, juridiske medarbejdere, uddannelse med mere).  | Månedligt og efter behov | SOC-oversigt |
| Implementere automatiseringsscripts og -tjenester, hvor det er relevant | Download og test automatiseringsscripts og konfigurationsfiler fra godkendte Microsoft-websteder for at forbedre Microsoft 365 Defender handlinger. | Ugentligt og efter behov | Teknik og SecOps | 
| Portal- eller licensstyring | Se meddelelser, og Microsoft Beskeder Center for Microsoft 365 Defender portal- eller licensbehov baseret på Microsoft-opdateringer og nye funktioner. | Ugentligt | SOC-oversigt| 
| Opdater SOC-eskaleringsbilletter | Alle SOC-teams' opdateringseskaleringsbilletter (f.eks. Sentinel, ServiceNow-billetter) er tildelt dem. | Dagligt | Alle SOC-teams | 
| Spor Microsoft 365 Defender af trusselssikkerhedsrisiko & aktivitet for afhjælpning af sikkerhedsrisiko | Generér afhjælpning af TvM Secure Score-aktivitet og rapport til aktivejere via en intranetportal. | Dagligt | Overvågning | 
| Generér sikker score-rapport | Overvågning af teamspor og rapporter forbedringer af Secure Score. | Ugentlig SOC | Overvågning | 
| Kør IR-tabletop-øvelse | Test SOC-teams playbooks i tabletop-øvelse. | Efter behov | Alle SOC-teams | 
|||||

Integrer disse opgaver i dine aktuelle SOC-processer.

## <a name="next-steps"></a>Næste trin

Du skal gennemgå de vejledninger, der refereres til i dette indhold og i [Microsoft 365 Defender-biblioteket](/microsoft-365/security/defender) for at afgøre, hvordan din egen implementering af Microsoft 365 Defender skal struktureres og integreres.
