---
title: Trin 6. Identificer SOC-vedligeholdelsesopgaver
description: Identificer SOC-vedligeholdelsesopgaver, når du integrerer Microsoft 365 Defender i dine sikkerhedshandlinger.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, enheder, brugere, identitet, identitet, postkasse, mail, 365, microsoft, m365, svar på hændelser, cyberangreb, secops, sikkerhedshandlinger, soc
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
ms.openlocfilehash: 6b1ee22f8176d6f682eb9e9f2134cc27db91affd
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783595"
---
# <a name="step-6-identify-soc-maintenance-tasks"></a>Trin 6. Identificer SOC-vedligeholdelsesopgaver

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Her er de periodiske eller efter behov, der skal udføres for at vedligeholde din SOC til Microsoft 365 Defender.

|Aktivitet|Beskrivelse|Kadence|Tildelt gruppe|
|---|---|---|---|
|Samarbejde om administration af tjenester med SOC-Teams|Administration af eksterne tjenester, f.eks. aktivsporing (CMDB), programlicenser (nye SaaS-licenser), enhedskøb (opgraderinger eller fornyelse af enhedsinstallationer) og andre Microsoft 365 ændringer i hele lejeren (Intune, Microsoft 365 og andre), der kan påvirke udrulningen af Microsoft 365 Defender produkter .|Ugentligt og efter behov|Teknisk & SecOps|
|Opdater kampagner til forebyggelse af phishing og datatab|Inkorporer SOC-use case og erfaringer med udvidet organisation (HR, juridisk bistand, uddannelse m.m.).|Månedligt og efter behov|SOC-tilsyn|
|Udrul automatiseringsscripts og -tjenester, hvor det er relevant|Download og test automatiseringsscripts og konfigurationsfiler fra godkendte Microsoft-websteder for at forbedre Microsoft 365 Defender handlinger.|Ugentligt og efter behov|Engineering og SecOps|
|Portal- eller licensstyring|Se meddelelser og Microsoft Beskeder Center for Microsoft 365 Defender portal- eller licensbehov baseret på Microsoft-opdateringer og nye funktioner.|Ugentlige|SOC-tilsyn|
|Opdater SOC-eskaleringsanmodninger|Alle SOC-teams opdaterer eskaleringsanmodninger (f.eks Sentinel, ServiceNow-billetter), der er tildelt dem.|Daglige|Alle SOC-teams|
|Spor afhjælpningsaktivitet for Microsoft 365 Defender Threat &|Generér afhjælpningsaktivitet for TvM Secure Score, og rapportér den til aktivejere via en intranetportal.|Daglige|Overvågning|
|Generér rapport over sikker score|Overvågningsteamet sporer og rapporterer forbedringer af Sikker score.|Ugentligt SOC|Overvågning|
|Kør IR-tablet-øvelse|Test SOC-teamets playbooks i øvelse på bordpladen.|Efter behov|Alle SOC-teams|

Integrer disse opgaver i dine aktuelle SOC-processer.

## <a name="next-steps"></a>Næste trin

Du bør gennemse de vejledninger, der henvises til i dette indhold, og i [biblioteket Microsoft 365 Defender](/microsoft-365/security/defender) for at finde ud af, hvordan din egen implementering af Microsoft 365 Defender skal struktureres og integreres.
