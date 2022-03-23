---
title: Prøve på Microsoft Defender til skyapps med Microsoft 365 Defender
description: Konfigurer dit Microsoft 365 Defender-prøvelaboratorium eller pilotmiljø for at teste og opleve den sikkerhedsløsning, der er udviklet til at beskytte enheder, identitet, data og programmer.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 484924d936f348fb29421b6bcc1789df4a44dc90
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63593340"
---
# <a name="pilot-microsoft-defender-for-cloud-apps-with-microsoft-365-defender"></a>Prøve på Microsoft Defender til skyapps med Microsoft 365 Defender


**Gælder for:**
- Microsoft 365 Defender

Denne artikel er [trin 3 af 3 i](eval-defender-mcas-overview.md) oprettelsen af evalueringsmiljøet til Microsoft Defender til skyapps. Du kan finde flere oplysninger om denne proces i [oversigtsartikel](eval-defender-mcas-overview.md).

Brug følgende trin til at konfigurere pilotprojektet for Microsoft Defender til skyapps.


![Trin til pilotprojekter med Microsoft Defender til skyapps.](../../media/defender/m365-defender-mcas-pilot-steps.png)

- Trin 1. [Opret pilotgruppen – Omfang af din pilotinstallation til visse brugergrupper](#step-1-create-the-pilot-group--scope-your-pilot-deployment-to-certain-user-groups)
- [Trin 2. Konfigurere beskyttelse – Betinget adgang til appkontrol](#step-2-configure-protection--conditional-access-app-control)
- [Trin 3. Prøv funktioner – Gennemgå de selvstudier, der beskytter dit miljø](#step-3-try-out-capabilities--walk-through-tutorials-for-protecting-your-environment) 


## <a name="step-1-create-the-pilot-group--scope-your-pilot-deployment-to-certain-user-groups"></a>Trin 1. Opret pilotgruppen – Omfang af din pilotinstallation til visse brugergrupper

Microsoft Defender til skyapps giver dig mulighed for at begrænse din installation. Angivelse af områder giver dig mulighed for at vælge bestemte brugergrupper, der skal overvåges for apps, eller som ikke skal overvåges. Du kan medtage eller udelade brugergrupper. Hvis du vil begrænse din pilotinstallation, skal [du se Omfangslagt udrulning](/cloud-app-security/scoped-deployment).


## <a name="step-2-configure-protection--conditional-access-app-control"></a>Trin 2. Konfigurere beskyttelse – Betinget adgang til appkontrol

En af de mest effektive beskyttelser, du kan konfigurere, er Betinget adgang til appkontrol. Dette kræver integration med Azure Active Directory (Azure AD). Det giver dig mulighed for at anvende betingede access-politikker, herunder relaterede politikker (f.eks. krav om sunde enheder), på apps i skyen, som du har tilladt. 

Det første trin til at bruge Microsoft Defender til skyapps til at administrere SaaS-apps er at finde disse og derefter føje dem til din Azure AD-lejer. Hvis du har brug for hjælp til discovery, kan [du se Opdag og administrer SaaS-apps i dit netværk](/cloud-app-security/tutorial-shadow-it). Når du har fundet apps, skal du [føje disse til din Azure AD-lejer](/azure/active-directory/manage-apps/add-application-portal).

Du kan begynde at administrere disse ved at gøre følgende:

- Først skal du i Azure AD oprette en ny politik for betinget adgang og konfigurere den til "Brug Betinget adgang-appkontrol". Dette omdirigerer anmodningen til Defender til skyapps. Du kan oprette én politik og tilføje alle SaaS-apps til denne politik.
- Dernæst skal du i Defender til skyapps oprette sessionspolitikker. Opret én politik for hvert kontrolelement, du vil anvende.

Du kan finde flere oplysninger, herunder understøttede apps og klienter, [under Beskyt apps med Betinget adgang til apps med Microsoft Defender til skyapps](/cloud-app-security/proxy-intro-aad). 

Se for eksempel politikker under Anbefalede [politikker for Microsoft Defender til skyapps til SaaS-apps](../office-365-security/mcas-saas-access-policies.md). Disse politikker er baseret på et sæt [fælles identitets- og enhedsadgangspolitikker](../office-365-security/microsoft-365-policies-configurations.md) , der anbefales som udgangspunkt for alle kunder. 

## <a name="step-3-try-out-capabilities--walk-through-tutorials-for-protecting-your-environment"></a>Trin 3. Prøv funktioner – Gennemgå de selvstudier, der beskytter dit miljø 

Dokumentationen til Microsoft Defender til skyapps indeholder en række selvstudier, der kan hjælpe dig med at opdage risici og beskytte dit miljø. 

Prøv selvstudier til Defender til skyapps:

- [Registrer mistænkelig brugeraktivitet](/cloud-app-security/tutorial-suspicious-activity)
- [Undersøg risikabelt bruger](/cloud-app-security/tutorial-ueba)
- [Undersøg risikige OAuth-apps](/cloud-app-security/investigate-risky-oauth)
- [Find og beskyt følsomme oplysninger](/cloud-app-security/tutorial-dlp)
- [Beskyt enhver app i din organisation i realtid](/cloud-app-security/tutorial-proxy)
- [Bloker overførsler af følsomme oplysninger](/cloud-app-security/use-case-proxy-block-session-aad)
- [Beskyt dine filer med administratorkarantæne](/cloud-app-security/use-case-admin-quarantine)
- [Kræv trin-op-godkendelse efter risikabel handling](/cloud-app-security/tutorial-step-up-authentication)

Du kan finde flere oplysninger om avanceret jagt på Microsoft Defender til skyapps-data i [videoen](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa).

## <a name="next-steps"></a>Næste trin

[Undersøg og svar ved Microsoft 365 Defender i et pilotmiljø](eval-defender-investigate-respond.md)

Gå tilbage til oversigten for [Evaluer Microsoft Defender til skyapps](eval-defender-mcas-overview.md)

Gå tilbage til oversigten for [Evaluer og Microsoft 365 Defender](eval-overview.md)
