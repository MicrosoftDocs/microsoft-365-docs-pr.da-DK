---
title: Pilot Microsoft Defender for Cloud Apps med Microsoft 365 Defender
description: Konfigurer dit Microsoft 365 Defender prøvelaboratorium eller et pilotmiljø for at teste og opleve sikkerhedsløsningen, der er udviklet til at beskytte enheder, identitet, data og programmer.
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
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 7dbf9154769ab4b97c15dc5fc67593b376ab2f6d
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750336"
---
# <a name="pilot-microsoft-defender-for-cloud-apps-with-microsoft-365-defender"></a>Pilot Microsoft Defender for Cloud Apps med Microsoft 365 Defender


**Gælder for:**
- Microsoft 365 Defender

Denne artikel er [trin 3 af 3](eval-defender-mcas-overview.md) i processen med at konfigurere evalueringsmiljøet for Microsoft Defender for Cloud Apps. Du kan få flere oplysninger om denne proces i [oversigtsartiklen](eval-defender-mcas-overview.md).

Brug følgende trin til at konfigurere pilotprojektet til Microsoft Defender for Cloud Apps.


:::image type="content" source="../../media/defender/m365-defender-mcas-pilot-steps.png" alt-text="Trinnene til at styre Microsoft Defender for Cloud Apps" lightbox="../../media/defender/m365-defender-mcas-pilot-steps.png":::
- [Trin 1. Opret pilotgruppen – Afgræns pilotudrulningen til bestemte brugergrupper](#step-1-create-the-pilot-groupscope-your-pilot-deployment-to-certain-user-groups)
- [Trin 2. Konfigurer beskyttelse – appkontrol med betinget adgang](#step-2-configure-protectionconditional-access-app-control)
- [Trin 3. Prøv funktioner – Gennemgang af selvstudier til beskyttelse af dit miljø](#step-3-try-out-capabilitieswalk-through-tutorials-for-protecting-your-environment) 

## <a name="step-1-create-the-pilot-groupscope-your-pilot-deployment-to-certain-user-groups"></a>Trin 1. Opret pilotgruppen – Afgræns pilotudrulningen til bestemte brugergrupper

Microsoft Defender for Cloud Apps gør det muligt for dig at tilpasse udrulningen. Med scoping kan du vælge visse brugergrupper, der skal overvåges for apps eller udelukkes fra overvågning. Du kan inkludere eller udelade brugergrupper. Hvis du vil undersøge din pilotinstallation, [skal du se Områdeudrulning](/cloud-app-security/scoped-deployment).


## <a name="step-2-configure-protectionconditional-access-app-control"></a>Trin 2. Konfigurer beskyttelse – appkontrol med betinget adgang

En af de mest effektive beskyttelser, du kan konfigurere, er Appkontrol med betinget adgang. Denne beskyttelse kræver integration med Azure Active Directory (Azure AD). Den giver dig mulighed for at anvende politikker for betinget adgang, herunder relaterede politikker (f.eks. krav om sunde enheder), for cloudapps, du har sanktioneret. 

Det første trin i brugen af Microsoft Defender for Cloud Apps til at administrere SaaS-apps er at finde disse apps og derefter føje dem til din Azure AD lejer. Hvis du har brug for hjælp til at finde, skal du se [Find og administrer SaaS-apps i dit netværk](/cloud-app-security/tutorial-shadow-it). Når du har opdaget apps, kan du [føje disse apps til din Azure AD lejer](/azure/active-directory/manage-apps/add-application-portal).

Du kan begynde at administrere disse apps ved at udføre følgende opgaver:

- I Azure AD skal du først oprette en ny politik for betinget adgang og konfigurere den til "Brug appkontrol med betinget adgang". Denne konfiguration hjælper med at omdirigere anmodningen til Defender for Cloud Apps. Du kan oprette én politik og føje alle SaaS-apps til denne politik.
- Derefter skal du oprette sessionspolitikker i Defender for Cloud Apps. Opret én politik for hvert kontrolelement, du vil anvende.

Du kan få flere oplysninger, herunder understøttede apps og klienter, under [Beskyt apps med Microsoft Defender for Cloud Apps appkontrol med betinget adgang](/cloud-app-security/proxy-intro-aad). 

Du kan f.eks. se Politikker under [Anbefalede Microsoft Defender for Cloud Apps politikker for SaaS-apps](../office-365-security/mcas-saas-access-policies.md). Disse politikker bygger på et sæt [fælles politikker for identitet og enhedsadgang](../office-365-security/microsoft-365-policies-configurations.md) , der anbefales som udgangspunkt for alle kunder. 

## <a name="step-3-try-out-capabilitieswalk-through-tutorials-for-protecting-your-environment"></a>Trin 3. Prøv funktioner – Gennemgang af selvstudier til beskyttelse af dit miljø 

Dokumentationen til Microsoft Defender for Cloud Apps indeholder en række selvstudier, der hjælper dig med at finde risici og beskytte dit miljø. 

Prøv Defender for Cloud Apps-selvstudier:

- [Registrer mistænkelig brugeraktivitet](/cloud-app-security/tutorial-suspicious-activity)
- [Undersøg risikable brugere](/cloud-app-security/tutorial-ueba)
- [Undersøg risikable OAuth-apps](/cloud-app-security/investigate-risky-oauth)
- [Find og beskyt følsomme oplysninger](/cloud-app-security/tutorial-dlp)
- [Beskyt alle apps i din organisation i realtid](/cloud-app-security/tutorial-proxy)
- [Bloker downloads af følsomme oplysninger](/cloud-app-security/use-case-proxy-block-session-aad)
- [Beskyt dine filer med administrator karantæne](/cloud-app-security/use-case-admin-quarantine)
- [Kræv trinvis godkendelse ved risikobelagt handling](/cloud-app-security/tutorial-step-up-authentication)

Du kan finde flere oplysninger om avanceret jagt i Microsoft Defender for Cloud Apps data i [videoen](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa).

## <a name="next-steps"></a>Næste trin

[Undersøg og besvar ved hjælp af Microsoft 365 Defender i et pilotmiljø](eval-defender-investigate-respond.md)

Vend tilbage til oversigten for [Evaluate Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

Vend tilbage til oversigten for [Evaluate og pilot Microsoft 365 Defender](eval-overview.md)
