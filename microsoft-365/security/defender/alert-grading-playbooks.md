---
title: Besked om karakterer i lærebøger
description: Gennemse beskederne om velkendte angreb, og tag anbefalede handlinger for at afhjælpe angrebene og beskytte dit netværk.
keywords: hændelser, beskeder, undersøge, analysere, svare, korrelation, angreb, computere, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365
search.appverid: met150
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
- m365initiative-m365-defender
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 129a4f2efd9a47c09535be3ba0f56504f3da697c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594735"
---
# <a name="alert-grading-playbooks"></a>Besked om karakterer i lærebøger

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Karakterer af karakterer giver dig mulighed for at gennemse og hurtigt klassificere beskeder om kendte angreb og foretage anbefalede handlinger for at afhjælpe angrebene og beskytte dit netværk. Karakterering af beskeder hjælper også med at klassificere den overordnede hændelse korrekt.

Som sikkerhedsanalytiker eller SOC-analytiker skal du have adgang til Microsoft 365 Defender, så du kan:

- Vurder og gennemse de oprettede beskeder og tilknyttede hændelser. Se [under undersøg vigtige beskeder](investigate-alerts.md).
- Søg efter din lejers sikkerhedssignaldata, og kontrollér potentielle trusler og mistænkelige aktiviteter. Se [avanceret jagt](advanced-hunting-overview.md).

>[!Note]
>Du kan give feedback til Microsoft om positive og falske positive beskeder, ikke kun når undersøgelsen er afsluttet, men også under undersøgelsesprocessen. Dette kan hjælpe Microsoft med fremtidig analyse og klassificering af sikkerhedshændelser.
>

## <a name="microsoft-defender-for-office-365"></a>Microsoft Defender til Office 365

[Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/defender-for-office-365) beskytter din organisation mod skadelige trusler fra mails, links (URL-adresser) og samarbejdsværktøjer. Defender til Office 365 omfatter:

- Politikker for trusselsbeskyttelse

   Definer politikker for trusselsbeskyttelse for at angive det passende beskyttelsesniveau for organisationen.

- Rapporter

  Få vist rapporter i realtid for at overvåge Defender for Office 365 ydeevnen i organisationen.

- Muligheder for trusselsundersøgelse og svar

  Brug førende værktøjer til at undersøge, forstå, simulere og forhindre trusler.

- Automatiserede undersøgelses- og svarmuligheder

  Spar tid og besvær med at undersøge og mindske trusler.

Defender til Office 365 vigtige beskeder kan klassificeres som: 

- Sand positiv (TP) for bekræftet ondsindet aktivitet. 
- Falsk positiv (FP) for bekræftet ikke-skadelig aktivitet.

>[!Note]
>Microsoft 365 Defender-portalen [https://security.microsoft.com](https://security.microsoft.com) samler funktionalitet fra eksisterende Microsoft-sikkerhedsportaler. Portalen Microsoft 365 Defender fremhæver hurtig adgang til oplysninger, enklere layout og samler relaterede oplysninger, så de er nemmere at bruge.
>

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender til skyapps

[Microsoft Defender til skyapps](/defender-cloud-apps) er en CLOUD Access Security Broker (CASB), der understøtter forskellige installationstilstande, herunder logsamling, API-forbindelser og omvendt proxy. Det giver stor synlighed, kontrol over datarejse og avancerede analyser til at identificere og bekæmpe cybertrusler på tværs af alle dine Microsoft- og tredjepartsskytjenester.

Defender til skyapps integreres oprindeligt med førende Microsoft-løsninger og er udviklet med sikkerhedsfagfolk i tankerne. Det giver enkel installation, centraliseret styring og innovative automatiseringsfunktioner.

Defender for Cloud Apps Framework omfatter muligheden for at beskytte dit netværk mod cybertrusler og anomalies, registrerer usædvanlig adfærd på tværs af skyapps for at identificere ransomware, kompromitterede brugere eller programmer. Det aktiverer analysen af forbrug med høj risiko og kan afhjælpes automatisk for at begrænse risikoen for din organisation.

Defender til skyapps-beskeder kan klassificeres som: 

- TP for bekræftet ondsindet aktivitet. 
- Benign true positive (B-TP) for mistænkelig men ikke ondsindet aktivitet, f.eks. en test af en virus eller andre godkendte mistænkelige handlinger. 
- FP for bekræftet ikke-ondsindet aktivitet.

## <a name="alert-grading-playbooks"></a>Besked om karakterer i lærebøger

Se disse lærebøger for at få trin til hurtigere at give besked om følgende trusler:

- [Mistænkelig videresendelse af mail](alert-grading-playbook-email-forwarding.md)
- [Regler for mistænkelig indbakkemanipulation](alert-grading-playbook-inbox-manipulation-rules.md)
- [Mistænkelige regler for videresendelse af indbakke](alert-grading-playbook-inbox-forwarding-rules.md)

Se [Undersøg vigtige beskeder](investigate-alerts.md) for at få oplysninger om, hvordan du undersøger beskeder Microsoft 365 Defender portalen.
