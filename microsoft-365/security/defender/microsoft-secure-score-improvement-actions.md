---
title: Vurder din sikkerhedsstilling via Microsoft Secure Score
description: Beskriver, hvordan du kan gøre noget for at forbedre din Microsoft Secure Score i Microsoft 365 Defender portal.
keywords: microsoft secure score, secure score, office 365 secure score, microsoft security score, Microsoft 365 Defender portal, forbedringshandlinger
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: d9f1b4619670c1998dbac584bf7ef4e1d1f940b6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591222"
---
# <a name="assess-your-security-posture-with-microsoft-secure-score"></a>Vurder din sikkerhedsstilling med Microsoft Secure Score

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft Secure Score er en måling af en organisations sikkerhedshold, med et højere tal, der angiver, at der er foretaget flere forbedringshandlinger. Den kan findes på https://security.microsoft.com/securescore [Microsoft 365 Defender-portalen](microsoft-365-defender.md).

For at hjælpe dig med hurtigere at finde de oplysninger, du skal bruge, er Microsoft-forbedringshandlinger organiseret i grupper:

- Identitet (Azure Active Directory konti & roller)
- Enhed (Microsoft Defender til slutpunkt, kendt som [Microsoft Secure Score for enheder](/windows/security/threat-protection/microsoft-defender-atp/tvm-microsoft-secure-score-devices))
- Apps (mail og skyapps, herunder Office 365 og Microsoft Defender til skyapps)

>[!NOTE]
>I den seneste version af Microsoft Secure Score blev der udgivet en forbedret pointmodel, som gjorde Microsoft Secure Score midlertidigt inkompatibel med Identity Secure Score og Graph API. [Vis detaljer](microsoft-secure-score-whats-new.md)

På siden Microsoft Secure Score overview kan du se, hvordan punkter opdeles mellem disse grupper, og hvilke punkter der er tilgængelige. Du kan også få en komplet oversigt over det samlede antal point, den historiske tendens for din sikre score med sammenligninger af benchmarks og prioriteret forbedringshandlinger, der kan foretages for at forbedre din score.

![Secure Score-startside.](../../media/secure-score/secure-score-home-page.png)

## <a name="check-your-current-score"></a>Kontrollér din aktuelle score

For at tjekke dit aktuelle resultat skal du gå til Microsoft Secure Score-oversigtssiden og se efter det felt, hvor der **står Din sikre score**. Dit resultat vises som en procentdel sammen med det antal point, du har opnået ud af de samlede mulige point.

Hvis du vælger knappen **Medtag ud** for din score, kan du desuden vælge forskellige visninger af din score. Disse forskellige scorevisninger vises i grafen på score-flisen og punktopdelingsdiagrammet.

Følgende er resultater, du kan tilføje til din visning af dine samlede resultater for at give dig et mere komplet billede af dit samlede resultat:

- **Planlagt score**: Vis projiceret score, når planlagte handlinger er fuldført
- **Aktuel licensscore**: Vis score, som kan opnås med din aktuelle Microsoft-licens
- **Opnåbar score: Vis score**, der kan opnås med dine Microsoft-licenser og nuværende risikoaccept

Sådan ser denne visning ud, hvis du har inkluderet alle mulige scorevisninger:

![Dit sikre resultat, herunder planlagt score, aktuelle licenspoint og opnåelige resultater.](../../media/secure-score/secure-score-achievable.png)

## <a name="take-action-to-improve-your-score"></a>Gør noget for at forbedre din score

Fanen **Forbedringshandlinger viser** de sikkerhedsanbefalinger, der adresserer mulige angrebsoverflader. Det omfatter også deres status (for at håndtere, planlagt, risiko accepteret, løst gennem tredjepart, løst via alternativ afhjælpning og fuldført). Du kan søge, filtrere og gruppere alle forbedringshandlingerne.  

### <a name="ranking"></a>Rangering

Rangering er baseret på antallet af punkter, der er tilbage for at opnå, implementeringsvanskeligheder, brugerpåvirkning og kompleksitet. De højest rangerede forbedringshandlinger har et stort antal punkter tilbage med lave problemer, brugerpåvirkning og kompleksitet.

### <a name="view-improvement-action-details"></a>Vis detaljer om forbedringshandling

Når du vælger en bestemt forbedringshandling, vises en pop op-meddelelse på hele siden.  

![Pop op-eksempel på forbedringshandling.](../../media/secure-score/secure-score-improvement-action-details.png)

For at fuldføre handlingen har du nogle få muligheder:

- Vælg **Administrer** for at gå til konfigurationsskærmen og foretage ændringen. Du får derefter de point, som handlingen er værd, synlig i pop op-handling. Det tager som regel ca. 24 timer, før point er opdateret.

- Vælg **Del** for at kopiere det direkte link til forbedringshandlingen. Du kan også vælge platformen for at dele linket, f.eks. mail, Microsoft Teams eller Microsoft Planner.

Tilføj **noter** for at holde styr på fremskridt eller andet, du vil skrive en kommentar til. Hvis du føjer dine **egne mærker** til forbedringshandlingen, kan du filtrere efter disse mærker.

### <a name="choose-an-improvement-action-status"></a>Vælg en status for forbedringshandling

Vælg de statusser og registreringsnoter, der er specifikke for forbedringshandlingen.

- **For at løse** dette – Du genkender, at forbedringshandlingen er nødvendig, og planlægger at løse det på et tidspunkt i fremtiden. Denne tilstand gælder også for handlinger, der registreres som delvist, men ikke er helt fuldført.
- **Planlagt** – Der er udarbejdet konkrete planer for at fuldføre forbedringshandlingen.
- **Risiko accepteret** – Sikkerhed bør altid balanceres med brugervenligheden, og ikke alle anbefalinger fungerer for dit miljø. Når det er tilfældet, kan du vælge at acceptere risikoen eller den resterende risiko og ikke gennemføre forbedringshandlingen. Du får ikke nogen point, men handlingen vil ikke længere være synlig på listen over forbedringshandlinger. Du kan når som helst se denne handling i oversigten eller fortryde den.
- **Løst gennem tredjepart og** Løst **gennem** alternativ afhjælpning – Forbedringshandlingen er allerede blevet behandlet af et program eller en software fra en tredjepart eller et internt værktøj. Du får de point, som handlingen er værd, så din score bedre afspejler din overordnede sikkerhed. Hvis et tredjepartsværktøj eller et internt værktøj ikke længere dækker kontrolelementet, kan du vælge en anden status. Husk, at Microsoft ikke kan se, om implementeringen er fuldstændig, hvis forbedringshandlingen er markeret som en af disse statusser.

#### <a name="threat--vulnerability-management-improvement-actions"></a>Forbedringshandlinger & håndtering af sikkerhedsrisici trusselshandlinger

Du kan ikke vælge statusser for forbedringshandlinger i kategorien "Enhed". I stedet bliver du ført til den tilknyttede [Håndtering af trusler og sikkerhedsrisici sikkerhedsanbefaling](/windows/security/threat-protection/microsoft-defender-atp/tvm-security-recommendation) i Microsoft 365 Defender at gøre noget. Den undtagelse, du vælger, og begrundelse, du skriver, vil være specifik for den pågældende portal. Den vil ikke være til stede i Microsoft Secure Score-portalen.

#### <a name="completed-improvement-actions"></a>Fuldførte forbedringshandlinger

Forbedringshandlinger har statussen "fuldført", når alle mulige punkter for forbedringshandlingen er nået. Fuldførte forbedringshandlinger bekræftes via Microsoft-data, og du kan ikke ændre status.

### <a name="assess-information-and-review-user-impact"></a>Vurder oplysninger, og gennemse brugerpåvirkning

Afsnittet med navnet **Hurtigt overblik fortæller** dig kategorien, de angreb, den kan beskyttes mod og produktet.

**Brugerpåvirkning** er, hvad brugerne vil opleve, hvis der sker en forbedring, og de pågældende  brugere er de personer, der vil blive påvirket.

### <a name="implement-the-improvement-action"></a>Implementere forbedringshandlingen

Afsnittet **Implementering** viser eventuelle forudsætninger, trinvise næste trin til at fuldføre forbedringshandlingen, den aktuelle status for implementering af forbedringshandlingen og eventuelle links til at få mere at vide.

Forudsætningerne omfatter de licenser, der er nødvendige, eller handlinger, der skal udføres, før forbedringshandlingen behandles. Sørg for, at du har tilstrækkeligt mange pladser i din licens til at fuldføre forbedringshandlingen, og at disse licenser anvendes på de nødvendige brugere.  

## <a name="we-want-to-hear-from-you"></a>Vi vil gerne høre fra dig

Hvis du har problemer, kan du fortælle os om det ved at slå et indlæg op i [community'et Sikkerhed, & Privacy Compliance](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Vi overvåger communityet og yder hjælp.

## <a name="related-resources"></a>Relaterede ressourcer

- [Oversigt over Microsoft Secure Score](microsoft-secure-score.md)
- [Spor din Microsoft Secure Score-historik, og opfylder mål](microsoft-secure-score-history-metrics-trends.md)
- [Hvad der kommer](microsoft-secure-score-whats-coming.md)
- [Nyheder](microsoft-secure-score-whats-new.md)
