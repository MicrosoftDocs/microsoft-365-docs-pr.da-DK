---
title: Den forenklede konfigurationsproces i Microsoft Defender til virksomheder
description: Få mere at vide om den forenklede konfigurationsproces i Microsoft Defender til virksomheder
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
ms.openlocfilehash: 02f970f7ad9981336ba54aaafcf936e952f1b726
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663110"
---
# <a name="the-simplified-configuration-process-in-microsoft-defender-for-business"></a>Den forenklede konfigurationsproces i Microsoft Defender til virksomheder

> [!IMPORTANT]
> Microsoft Defender til virksomheder udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra den 1. marts 2022. Defender for Business som et separat abonnement fås som prøveversion og udrulles gradvist til kunder og [it-partnere, der tilmelder sig her](https://aka.ms/mdb-preview) for at anmode om det. Prøveversionen indeholder et [indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer jævnligt funktioner.
> 
> Nogle oplysninger i denne artikel er relateret til forhåndsudgivne produkter/tjenester, der kan blive ændret væsentligt, før de udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, for de oplysninger, der er angivet her. 

Microsoft Defender til virksomheder har en forenklet konfigurationsproces, der er udviklet specielt til små og mellemstore virksomheder. Denne oplevelse tager gætteriet ud af onboarding og administration af enheder med en guidelignende oplevelse og standardpolitikker, der er designet til at beskytte din virksomheds enheder fra dag ét. **Vi anbefaler, at du bruger den forenklede konfigurationsproces, men du er ikke begrænset til denne indstilling**.

Når det drejer sig om onboarding af enheder og konfiguration af sikkerhedsindstillinger for din virksomheds enheder, kan du vælge mellem flere forskellige oplevelser: 

- Den forenklede konfigurationsproces i Microsoft Defender til virksomheder (*anbefales*) 
- Microsoft Endpoint Manager, som omfatter Microsoft Intune (inkluderet i [Microsoft 365 Business Premium](../../business-premium/index.md))
- Din ikke-Microsoft-løsning til administration af enheder 

## <a name="what-to-do"></a>Sådan gør du

1. [Gennemse indstillingerne for konfiguration og konfiguration](#review-your-setup-and-configuration-options)

2. [Få mere at vide om den forenklede konfigurationsproces i Defender for Business](#why-we-recommend-using-the-simplified-configuration-process)

3. [Fortsæt til de næste trin](#next-steps)

>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om Microsoft Defender til virksomheder</a>. Vi vil meget gerne høre fra dig!
>

## <a name="review-your-setup-and-configuration-options"></a>Gennemse indstillingerne for konfiguration og konfiguration

I følgende tabel beskrives hver enkelt oplevelse:
<br/><br/>

| Portaloplevelse  | Beskrivelse  |
|---------|---------|
| Den forenklede konfigurationsoplevelse på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) <br/>*(Dette er den anbefalede indstilling for de fleste kunder*)  | Den forenklede konfigurationsoplevelse omfatter en guidelignende oplevelse, der kan hjælpe dig med at konfigurere Defender for Business. Forenklet konfiguration omfatter også standardsikkerhedsindstillinger og -politikker, der hjælper dig med at beskytte din virksomheds enheder, så snart de er onboardet i Defender for Business. <br/><br/>Med denne oplevelse bruger dit sikkerhedsteam portalen Microsoft 365 Defender til at: <br/>– Konfigurer Defender for Business <br/>- Få vist og administrer hændelser<br/>- Reagere på og afhjælpe trusler<br/>- Få vist rapporter<br/>- Gennemse ventende eller fuldførte handlinger <br/><br/> Microsoft 365 Defender-portalen er din one-stop-shop til virksomhedens sikkerhedsindstillinger og trusselsbeskyttelsesfunktioner. Du får en forenklet oplevelse, så du kan komme hurtigt og effektivt i gang. Du kan få mere at vide under [Brug guiden til at konfigurere Microsoft Defender til virksomheder](mdb-use-wizard.md).<br/><br/>Og du kan redigere dine indstillinger eller definere nye politikker, der passer til din virksomheds behov.<br/><br/>Du kan få mere at vide under [Få vist eller rediger enhedspolitikker i Microsoft Defender til virksomheder](mdb-view-edit-policies.md). |
| Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  | Microsoft Endpoint Manager omfatter Microsoft Intune, en cloudbaseret MDM- (Mobile Device Management) og MAM-udbyder (Mobile Application Management) til apps og enheder. [Microsoft 365 Business Premium](../../business-premium/index.md) kunder har allerede Endpoint Manager. <br/><br/>Mange virksomheder bruger Intune til at administrere deres enheder, f.eks. mobiltelefoner, tablets og bærbare computere. Du kan få mere at vide under [Microsoft Intune er EN MDM- og MAM-udbyder til dine enheder](/mem/intune/fundamentals/what-is-intune). <br/><br/>Hvis du allerede bruger Microsoft Intune eller Microsoft Endpoint Manager, kan du fortsætte med at bruge denne løsning. |
| Din løsning til enhedshåndtering, der ikke er fra Microsoft  | Hvis du bruger en produktivitets- og enhedshåndteringsløsning, der ikke er fra Microsoft, kan du fortsætte med at bruge denne løsning med Defender for Business. <br/><br/>Når enheder er onboardet til Defender for Business, kan du se deres status og beskeder på Microsoft 365 Defender portalen. Du kan få mere at vide under [Onboarding- og konfigurationsværktøjsindstillinger for Defender for Endpoint](../defender-endpoint/onboard-configure.md). |


## <a name="why-we-recommend-using-the-simplified-configuration-process"></a>Derfor anbefaler vi, at du bruger den forenklede konfigurationsproces

**Vi anbefaler, at du bruger den forenklede konfigurationsproces i Microsoft Defender til virksomheder** for de fleste kunder. Den forenklede konfigurationsproces er strømlinet især for små og mellemstore virksomheder. Defender for Business er designet til at hjælpe dig med at beskytte din virksomheds enheder på dag 1 uden at kræve dyb teknisk ekspertise eller særlig viden. Med standardsikkerhedsindstillinger og -politikker beskyttes dine enheder, så snart de er onboardet.

Defender for Business er designet til at yde stærk beskyttelse, samtidig med at du sparer tid og kræfter på at konfigurere dine sikkerhedsindstillinger. Den strømlinede oplevelse på Microsoft 365 Defender portalen gør det nemt at onboarde enheder og administrere dem. Derudover er standardpolitikker inkluderet, så din virksomheds enheder beskyttes, så snart de er onboardet. Du kan beholde dine standardindstillinger, som de er, eller foretage ændringer, så de passer til dine forretningsbehov. Du kan også tilføje nye politikker for at administrere enheder efter behov.

## <a name="next-steps"></a>Næste trin

- [Konfigurer og konfigurer Microsoft Defender til virksomheder](mdb-setup-configuration.md)

- [Kom i gang med at bruge Microsoft Defender til virksomheder](mdb-get-started.md)
