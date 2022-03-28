---
title: Den forenklede konfigurationsproces i Microsoft Defender for Business
description: Få mere at vide om den forenklede konfigurationsproces i Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 2445b7f35fb808c49c046027e2279c3b00057f54
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63596966"
---
# <a name="the-simplified-configuration-process-in-microsoft-defender-for-business"></a>Den forenklede konfigurationsproces i Microsoft Defender for Business

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

Microsoft Defender for Business har en forenklet konfigurationsproces, der er udviklet specielt til små og mellemstore virksomheder. Denne oplevelse fjerner gætværket ud af onboarding og administration af enheder med en guide-lignende oplevelse og standardpolitikker, der er designet til at beskytte din virksomheds enheder fra dag ét. **Vi anbefaler, at du bruger den forenklede konfigurationsproces, men du er ikke begrænset til denne indstilling**.

Når det gælder onboardingenheder og konfiguration af sikkerhedsindstillinger for virksomhedens enheder, kan du vælge mellem flere forskellige oplevelser: 

- Den forenklede konfigurationsproces i Microsoft Defender for Business (*anbefales*) 
- Microsoft Endpoint Manager, som omfatter Microsoft Intune (inkluderet i [Microsoft 365 Business Premium](../../business-premium/index.md))
- Din løsning til administration af enheder, som ikke er Microsoft 

## <a name="what-to-do"></a>Hvad kan du gøre?

1. [Gennemse dine konfigurations- og konfigurationsindstillinger](#review-your-setup-and-configuration-options)

2. [Få mere at vide om den forenklede konfigurationsproces i Defender for Business](#why-we-recommend-using-the-simplified-configuration-process)

3. [Fortsæt til de næste trin](#next-steps)

>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>

## <a name="review-your-setup-and-configuration-options"></a>Gennemse dine konfigurations- og konfigurationsindstillinger

I følgende tabel beskrives hver oplevelse:
<br/><br/>

| Portaloplevelse  | Beskrivelse  |
|---------|---------|
| Den forenklede konfigurationsoplevelse i Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) <br/>(*Dette er den anbefalede indstilling for de fleste kunder*)  | Den forenklede konfigurationsoplevelse omfatter en guide-lignende oplevelse, der hjælper dig med at konfigurere Defender for Business. Forenklet konfiguration omfatter også standardsikkerhedsindstillinger og -politikker, der hjælper dig med at beskytte din virksomheds enheder, så snart de er onboardet til Defender for Business. <br/><br/>Med denne oplevelse bruger dit sikkerhedsteam Microsoft 365 Defender portal til at: <br/>- Konfigurere Defender for Business <br/>- Få vist og administrer hændelser<br/>- Reagere på og afhjælpe trusler<br/>- Vis rapporter<br/>- Gennemse afventende eller fuldførte handlinger <br/><br/> Portalen Microsoft 365 Defender er dit sted, hvor du kan finde din virksomheds sikkerhedsindstillinger og funktioner til trusselsbeskyttelse. Du får en forenklet oplevelse, så du kan komme hurtigt og effektivt i gang. Du kan få mere at [vide under Brug guiden til at konfigurere Microsoft Defender for Business](mdb-use-wizard.md).<br/><br/>Du kan også redigere dine indstillinger eller definere nye politikker, der passer til din virksomheds behov.<br/><br/>Du kan få mere at vide [under Få vist eller rediger enhedspolitikker i Microsoft Defender for Business](mdb-view-edit-policies.md). |
| Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  | Microsoft Endpoint Manager omfatter Microsoft Intune, en skybaseret administration af mobilenheder (MDM) og mam-udbyder til administration af mobilapps til apps og enheder. [Microsoft 365 Business Premium](../../business-premium/index.md) kunder har allerede Endpoint Manager. <br/><br/>Mange virksomheder bruger Intune til at administrere deres enheder, f.eks. mobiltelefoner, tablets og bærbare computere. Hvis du vil have mere at [vide, Microsoft Intune du er MDM- og MAM-udbyder til dine enheder](/mem/intune/fundamentals/what-is-intune). <br/><br/>Hvis du allerede bruger en Microsoft Intune eller Microsoft Endpoint Manager, kan du fortsætte med at bruge den løsning. |
| Din løsning til administration af enheder, der ikke er Microsoft  | Hvis du bruger en løsning, der ikke er en Microsoft-produktivitets- og enhedsadministrationsløsning, kan du fortsætte med at bruge den pågældende løsning med Defender for Business. <br/><br/>Når enheder er onboardet til Defender for Business, får du vist deres status og beskeder i Microsoft 365 Defender portal. Du kan få mere at vide [under Indstillinger for onboarding- og konfigurationsværktøj for Defender til Slutpunkt](../defender-endpoint/onboard-configure.md). |


## <a name="why-we-recommend-using-the-simplified-configuration-process"></a>Derfor anbefaler vi, at du bruger den forenklede konfigurationsproces

**Vi anbefaler, at du bruger den forenklede konfigurationsproces i Microsoft Defender for Business** for de fleste kunder. Den forenklede konfigurationsproces er strømlinet specielt til små og mellemstore virksomheder. Defender for Business er udviklet til at hjælpe dig med at beskytte din virksomheds enheder på én dag uden behov for dybt teknisk ekspertise eller særlig viden. Med standardsikkerhedsindstillinger og -politikker er dine enheder beskyttet, så snart de er onboardet.

Defender for Business er udviklet til at yde stærk beskyttelse, samtidig med at du sparer tid og anstrengelser i konfiguration af sikkerhedsindstillingerne. Den strømlinede oplevelse i Microsoft 365 Defender gør det nemt at onboarde enheder og administrere dem. Desuden er standardpolitikker inkluderet, så din virksomheds enheder er beskyttet, så snart de er onboardet. Du kan beholde standardindstillingerne, som de er, eller du kan foretage ændringer, så de passer til virksomhedens behov. Du kan også tilføje nye politikker for at administrere enheder efter behov.

## <a name="next-steps"></a>Næste trin

- [Konfigurere Microsoft Defender for Business](mdb-setup-configuration.md)

- [Kom i gang med at bruge Microsoft Defender for Business](mdb-get-started.md)
