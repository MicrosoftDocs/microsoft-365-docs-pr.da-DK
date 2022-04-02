---
title: Sikkerhedsanbefalinger af Håndtering af trusler og sikkerhedsrisici
description: Få konkrete sikkerhedsanbefalinger, der er prioriteret efter trussel, sandsynligheden for, at de bliver brudt, og værdi, Håndtering af trusler og sikkerhedsrisici.
keywords: Håndtering af trusler og sikkerhedsrisici, Microsoft Defender til Endpoint tvm sikkerheds anbefaling, cybersecurity anbefaling, handlings løsning sikkerhedsanbefaling
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 57c1909ff54fea6b9151e212f465abb75bab48f8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63603114"
---
# <a name="security-recommendations---threat-and-vulnerability-management"></a>Sikkerhedsanbefalinger – Håndtering af trusler og sikkerhedsrisici

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Cybertrusler, der identificeres i din organisation, er tilknyttet brugbare sikkerhedsanbefalinger og prioriteret af deres virkning. Prioriteret anbefalinger hjælper med at afkorte tiden til at afhjælpe eller afhjælpe sårbarheder og fremme overholdelse af regler og standarder.

Hver sikkerhedsanbefaling omfatter afhjælpningstrin, der kan afhjælpes. Som en hjælp til opgavestyring kan anbefalingen også sendes ved hjælp af Microsoft Intune og Microsoft Endpoint Configuration Manager. Når trusselsbilledet ændrer sig, ændres anbefalingen også, da den løbende indsamler oplysninger fra dit miljø.

> [!TIP]
> Hvis du vil have mails om nye sikkerhedsrisikohændelser, skal [du se Konfigurer mailbeskeder om sikkerhedsrisiko i Microsoft Defender til Endpoint](configure-vulnerability-email-notifications.md)

## <a name="how-it-works"></a>Sådan fungerer det

Hver enhed i organisationen får en score baseret på tre vigtige faktorer, der kan hjælpe kunderne med at fokusere på de rigtige ting på det rigtige tidspunkt.

- **Trussel**: Karakteristikken af sårbarheder og udnyttelse i din organizations enheder og historik over brud. Baseret på disse faktorer viser sikkerhedsanbefalingerne de tilsvarende links til aktive beskeder, igangværende trusselskampagner og deres tilsvarende trusselsanalyserapporter.
- **Sandsynlighed for** brud: Din organisations sikkerhedsholdning og fleksibilitet over for trusler.
- **Forretningsværdi**: Din organisations aktiver, kritiske processer og immaterielle egenskaber.

## <a name="navigate-to-the-security-recommendations-page"></a>Gå til siden med sikkerhedsanbefalinger

Få adgang til siden med anbefalinger om sikkerhed på forskellige måder:

- Navigationsmenuen Håndtering af sikkerhedsrisici sikkerhed og sikkerhed [i Microsoft 365 Defender portal](portal-overview.md)
- De vigtigste sikkerhedsanbefalinger [i Håndtering af trusler og sikkerhedsrisici dashboard](tvm-dashboard-insights.md)

Se relaterede sikkerhedsanbefalinger på følgende steder:

- Softwareside
- Siden Enhed

### <a name="navigation-menu"></a>Navigationsmenu

Gå til **navigationsmenuen til administration af** sikkerhedsrisiko, og **vælg Anbefalinger**. Siden indeholder en liste over sikkerhedsanbefalinger for de trusler og sårbarheder, der findes i organisationen.

### <a name="top-security-recommendations-in-the-threat-and-vulnerability-management-dashboard"></a>De vigtigste sikkerhedsanbefalinger i Håndtering af trusler og sikkerhedsrisici dashboard

I en given dag som sikkerhedsadministrator kan du se nærmere på [Håndtering af trusler og sikkerhedsrisici-dashboardet](tvm-dashboard-insights.md) for at se din [eksponeringsscore](tvm-exposure-score.md) side om side med [din Microsoft Secure Score for Enheder](tvm-microsoft-secure-score-devices.md). Målet er **at mindske** organisationens eksponering for sårbarheder og øge organisationens  enhedssikkerhed, så den er mere robust over for cyberangreb. Den øverste liste med sikkerhedsanbefalinger kan hjælpe dig med at opnå dette mål.

![Eksempel på kortet med Topsikkerhedsanbefalinger med fire sikkerhedsanbefalinger.](images/top-security-recommendations350.png)

De øverste sikkerhedsanbefalinger viser de forbedrede muligheder, der er prioriteret ud fra de vigtige faktorer, der er nævnt i forrige afsnit – trusler, sandsynlighed for brud og værdi. Hvis du vælger en anbefaling, kommer du til siden med sikkerhedsanbefalinger med flere oplysninger.

## <a name="security-recommendations-overview"></a>Oversigt over sikkerhedsanbefalinger

Få vist anbefalinger, antallet af fundne resultater, relaterede komponenter, trusselsindsigt, antal enheder, der vises, status, afhjælpningstype, afhjælpningsaktiviteter, indvirkning på din eksponeringsscore og Microsoft Secure Score for enheder og tilknyttede mærker.

Farven på grafen **Oversatte enheder** ændres i løbet af tendensen. Hvis antallet af enheder, der vises, stiger, ændres farven til rød. Hvis der er et fald i antallet af enheder, der vises, ændres grafens farve til grøn.

> [!NOTE]
> Trussels- håndtering af sikkerhedsrisici viser enheder, der blev brugt for op til **30 dage** siden. Dette er forskelligt fra resten af Microsoft Defender til slutpunkt, hvor hvis en enhed ikke har været i brug i mere end syv dage, har den statussen "Inaktiv".

![Eksempel på landingssiden for sikkerhedsanbefalinger.](images/tvmsecrec-updated.png)

### <a name="icons"></a>Ikoner

Nyttige ikoner gør også hurtigt opmærksom på følgende:

- ![pil, der rammer et mål.](images/tvm_alert_icon.png) mulige aktive beskeder
- ![rød fejl.](images/tvm_bug_icon.png) tilknyttede offentlige udnyttelser
- ![elpære.](images/tvm_insight_icon.png) anbefalingsindsigt

### <a name="explore-security-recommendation-options"></a>Udforsk indstillinger for sikkerhedsanbefaling

Vælg den sikkerhedsanbefaling, du vil undersøge eller behandle.

:::image type="content" alt-text="Eksempel på en pop op-side med en sikkerhedsanbefaling." source="images/secrec-flyouteolsw.png" lightbox="images/secrec-flyouteolsw.png":::

I pop op-menuen kan du vælge en af følgende indstillinger:

- **Siden Åbn software** – Åbn softwaresiden for at få mere kontekst om softwaren, og hvordan den distribueres. Oplysningerne kan omfatte trusselskontekst, tilknyttede anbefalinger, ukendte enheder, antal enheder, der opdages, sårbarheder, navne og detaljerede enheder med den installerede software og versionsfordeling.

- [**Afhjælpningsindstillinger**](tvm-remediation.md) – Indsend en anmodning om afhjælpning for at åbne en anmodning i Microsoft Intune, som din it-administrator kan hente og løse. Spor afhjælpningsaktiviteten på siden Afhjælpning.

- [**Undtagelsesindstillinger**](tvm-exception.md) – Send en undtagelse, angiv begrundelse, og angiv undtagelsesvarighed, hvis du endnu ikke kan løse problemet.

> [!NOTE]
> Når en softwareændring foretages på en Windows-, Linux- eller macOS-enhed, tager det normalt 2-4 timer, før dataene afspejles i sikkerhedsportalen. Det kan tage op til 8 timer, før ændringer på iOS- og Android-enheder afspejles. Der kan være situationer, hvor det tager længere tid.
> 
> Konfigurationsændringer kan tage et sted mellem 4 til 24 timer.

### <a name="investigate-changes-in-device-exposure-or-impact"></a>Undersøg ændringer i enheds eksponering eller virkning

Hvis der er et stort spring i antallet af enheder, der eksponeres, eller en skarp stigning i effekten på din organisations eksponeringsscore og Microsoft Secure Score for enheder, er denne sikkerhedsanbefaling værd at undersøge.

1. Vælg anbefalingen, og **siden Åbn software**
2. Vælg fanen **Begivenhedstidslinje** for at få vist alle de virkningsfulde begivenheder, der er relateret til den pågældende software, f.eks. nye sårbarheder eller nye offentlige udnyttelser. [Få mere at vide om begivenhedstidslinje](threat-and-vuln-mgt-event-timeline.md)
3. Beslut, hvordan du skal håndtere stigningen eller din organisations eksponering, f.eks. sende en afhjælpningsanmodning

## <a name="request-remediation"></a>Anmod om afhjælpning

Afhjælpnings Håndtering af trusler og sikkerhedsrisici broer mellem sikkerhed og it-administratorer via arbejdsprocessen for afhjælpningsanmodninger. Sikkerhedsadministratorer som dig kan anmode it-administratoren om at afhjælpe en sikkerhedsrisiko fra siden **med anbefaling om sikkerhed** til Intune. [Få mere at vide om afhjælpningsindstillinger](tvm-remediation.md)

### <a name="how-to-request-remediation"></a>Sådan anmoder du om afhjælpning

Vælg en sikkerhedsanbefaling, du vil anmode om afhjælpning for, og vælg derefter **Afhjælpningsindstillinger**. Udfyld formularen, og vælg **Send anmodning**. Gå til siden [**Afhjælpning for**](tvm-remediation.md) at få vist status for din afhjælpningsanmodning. [Få mere at vide om, hvordan du anmoder om afhjælpning](tvm-remediation.md#request-remediation)

## <a name="file-for-exception"></a>Fil for undtagelse

Som et alternativ til en afhjælpningsanmodning, når en anbefaling ikke er relevant i øjeblikket, kan du oprette undtagelser for anbefalinger. [Få mere at vide om undtagelser](tvm-exception.md)

Kun brugere med tilladelser til "håndtering af undtagelser" kan tilføje undtagelser. [Få mere at vide om RBAC-roller](user-roles.md).

Når der oprettes en undtagelse for en anbefaling, er anbefalingen ikke længere aktiv. Tilstanden Anbefaling ændres til **Fuld undtagelse** eller **Delvis undtagelse** (efter enhedsgruppe).

### <a name="how-to-create-an-exception"></a>Sådan oprettes en undtagelse

Vælg en sikkerhedsanbefaling, du vil oprette en undtagelse for, og vælg derefter **Undtagelsesindstillinger**.

![Viser, hvor knappen for "undtagelsesindstillinger" er placeringen i et pop op-pop op-billede med en sikkerhedsanbefaling.](images/tvm-exception-options.png)

Udfyld formularen, og send. Hvis du vil have vist alle dine undtagelser (nuværende og tidligere), [](tvm-remediation.md) skal du gå til siden Afhjælpning under menuen **Administration af trussel &-sikkerhedsrisiko** og vælge  fanen Undtagelser. Få mere at vide om, hvordan du opretter en [undtagelse](tvm-exception.md#create-an-exception)

## <a name="report-inaccuracy"></a>Rapportér unøjagtighed

Du kan rapportere en falsk positiv, når der vises uklare, unøjagtige, ufuldstændige eller allerede afhjulpet sikkerhedsanbefalingsoplysninger.

1. Åbn sikkerhedsanbefalingen.

2. Vælg de tre prik ud for den sikkerhedsanbefaling, du vil rapportere, og vælg **derefter Rapport unøjagtighed**.

    ![Viser, hvor knappen "Rapport unøjagtighed" er i et pop op-pop op-billede med en sikkerhedsanbefaling.](images/report-inaccuracy500.png)

3. I pop op-ruden skal du vælge kategorien unøjagtighed i rullemenuen, udfylde din mailadresse og oplysninger om unøjagtigheden.

4. Vælg **Send**. Din feedback sendes straks til Håndtering af trusler og sikkerhedsrisici eksperter.

## <a name="related-articles"></a>Relaterede artikler

- [Oversigt over trusler håndtering af sikkerhedsrisici sikkerhed](next-gen-threat-and-vuln-mgt.md)
- [Dashboard](tvm-dashboard-insights.md)
- [Eksponeringsscore](tvm-exposure-score.md)
- [Microsoft Secure Score til enheder](tvm-microsoft-secure-score-devices.md)
- [Afhjælpe sårbarheder](tvm-remediation.md)
- [Opret og få vist undtagelser for sikkerhedsanbefalinger](tvm-exception.md)
- [Begivenhedstidslinje](threat-and-vuln-mgt-event-timeline.md)
