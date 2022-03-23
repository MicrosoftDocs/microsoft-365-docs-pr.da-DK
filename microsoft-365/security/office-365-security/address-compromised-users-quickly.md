---
title: Håndtere kompromitterede brugerkonti med automatiseret undersøgelse og svar
keywords: AIR, autoIR, Microsoft Defender til slutpunkt, automatiseret, undersøgelse, svar, afhjælpning, trusler, avanceret, trussel, beskyttelse, kompromitteret
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
ms.custom: ''
ms.date: 06/10/2021
description: Få mere at vide om, hvordan du hurtigere registrerer og adresserer kompromitterede brugerkonti med automatiseret undersøgelse og svarmuligheder i Microsoft Defender Office 365 Plan 2.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: cbc3c6c8a81d59bebbd5272e13e0f96de2257623
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63590718"
---
# <a name="address-compromised-user-accounts-with-automated-investigation-and-response"></a>Håndtere kompromitterede brugerkonti med automatiseret undersøgelse og svar

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)


[Microsoft Defender til Office 365 Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) omfatter effektive funktioner [til automatisk undersøgelse](office-365-air.md) og svar (AIR). Disse funktioner kan gemme dit sikkerhedsteam en masse tid og besvær i forbindelse med trusler. Microsoft fortsætter med at forbedre sikkerhedsfunktionerne. For nylig blev AIR-egenskaberne forbedret med en kompromitteret brugersikkerhedsspilbog (i øjeblikket i forhåndsvisning). Læs denne artikel for at få mere at vide om spilbogen for kompromitteret brugersikkerhed. Og se blogindlægget Få hurtigere tid til at registrere og reagere på brugerforlig og begrænse omfanget af brud med [Microsoft Defender for Office 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Speed-up-time-to-detect-and-respond-to-user-compromise-and-limit/ba-p/977053) for at få flere oplysninger.

![Automatiseret undersøgelse af en kompromitteret bruger.](/microsoft-365/media/office365atp-compduserinvestigation.jpg)

Den kompromitterede sikkerhedsplan for brugerne gør det muligt for organisationens sikkerhedsteam at:

- Gør registrering af kompromitterede brugerkonti hurtigere.
- Begræns omfanget af en overtrædelse, når en konto er kompromitteret; og
- Svar på kompromitterede brugere mere effektivt og effektivt.

## <a name="compromised-user-alerts"></a>Kompromitterede brugerbeskeder

Når en brugerkonto er kompromitteret, opstår der atypiske eller unormale funktionsmåder. Eksempelvis sendes phishing- og spammeddelelser muligvis internt fra en pålidelig brugerkonto. Defender for Office 365 kan registrere sådanne anomalies i mailmønstre og samarbejdsaktivitet i Office 365. Når dette sker, udløses beskeder, og processen til afhjælpning af trusler starter.

Her er f.eks. en alarm, der blev udløst på grund af mistænkelig afsendelse af mails:

![Besked udløst på grund af mistænkelig afsendelse af mails.](/microsoft-365/media/office365atp-suspiciousemailsendalert.jpg)

Her er et eksempel på en påmindelse, der blev udløst, når en afsendelsesgrænse blev nået for en bruger:

![Besked udløst af grænsen for afsendelse er nået.](/microsoft-365/media/office365atp-sendinglimitreached.jpg)

## <a name="investigate-and-respond-to-a-compromised-user"></a>Undersøg og svar på en kompromitteret bruger

Når en brugerkonto er blevet kompromitteret, udløses beskeder. Og i nogle tilfælde er den pågældende brugerkonto blokeret og forhindret i at sende yderligere mails, før problemet er løst af organisationens sikkerhedsteam. I andre tilfælde starter en automatiseret undersøgelse, som kan resultere i anbefalede handlinger, som dit sikkerhedsteam skal udføre.

- [Få vist og undersøg begrænsede brugere](#view-and-investigate-restricted-users)

- [Få vist detaljer om automatiserede undersøgelser](#view-details-about-automated-investigations)

> [!IMPORTANT]
> Du skal have de rette tilladelser for at kunne udføre følgende opgaver. Se [Påkrævede tilladelser for at bruge AIR-funktioner](office-365-air.md#required-permissions-to-use-air-capabilities).

### <a name="view-and-investigate-restricted-users"></a>Få vist og undersøg begrænsede brugere

Du har nogle få muligheder for at navigere til en liste over brugere med begrænsninger. Eksempelvis kan du i Microsoft 365 Defender gå til Mail og & **Gennemsyn** \> **begrænsede** \> **brugere**. I følgende procedure beskrives navigation ved hjælp **af dashboardet** Vigtige beskeder, som er en god måde at se forskellige typer af beskeder, der kan være blevet udløst.

1. Åbn Microsoft 365 Defender på, <https://security.microsoft.com> og gå til **Hændelser & vigtige beskeder**\>. Eller du kan bruge til at gå **direkte til siden** Vigtige beskeder <https://security.microsoft.com/alerts>.

2. På siden **Beskeder skal du** filtrere resultaterne efter tidsperiode og politikken Bruger begrænset fra **at sende mail**.

   ![Siden Vigtige beskeder i Microsoft 365 Defender filtreret for brugere med begrænset adgang.](../../media/m365-sc-alerts-page-with-restricted-user.png)

3. Hvis du vælger posten ved at klikke på navnet, åbnes en bruger, der ikke kan sende mails, med yderligere oplysninger, som du kan gennemse. Ud for knappen **Administrer besked** kan du klikke på ikonet ![Flere indstillinger.](../../media/m365-cc-sc-more-actions-icon.png) **Flere indstillinger** og derefter vælge **Vis begrænsede brugeroplysninger** for at gå til **siden Begrænsede** brugere, hvor du kan [frigive den begrænsede bruger](removing-user-from-restricted-users-portal-after-spam.md).

   ![Brugeren har begrænset sig til at kunne sende mail fra beskedcenteret.](../../media/m365-sc-alerts-user-restricted-from-sending-email-page.png)

### <a name="view-details-about-automated-investigations"></a>Få vist detaljer om automatiserede undersøgelser

Når en automatiseret undersøgelse er begyndt, kan du se dens oplysninger og resultater i Security & Compliance Center. Gå til **Undersøgelser af trusselsadministration**\>, og vælg derefter en undersøgelse for at få vist **dens** detaljer.

Du kan få mere at vide [under Få vist oplysninger om en undersøgelse](air-view-investigation-results.md).

## <a name="keep-the-following-points-in-mind"></a>Husk følgende punkter

- **Hold dig på for altid at få besked**. Som du ved, jo længere tid et forlig bliver uopdaget, jo større er potentialet for effekt og omkostninger for din organisation, kunder og partnere. Tidlig registrering og rettidig respons er afgørende for at reducere trusler, og især når en brugers konto er kompromitteret.

- **Automatisering hjælper, men erstatter ikke dit sikkerhedsteam**. Automatiserede undersøgelses- og svarfunktioner kan opdage en kompromitteret bruger tidligt, men dit sikkerhedsteam vil sandsynligvis skulle deltage og foretage en undersøgelse og afhjælpning. Har du brug for hjælp til dette? Se [Gennemse og godkend handlinger](air-review-approve-pending-completed-actions.md).

- **Brug ikke en mistænkelig logonbesked som din eneste indikator**. Når en brugerkonto er blevet kompromitteret, udløser den muligvis en mistænkelig logonbesked eller ej. Nogle gange er det den række af aktiviteter, der sker, når en konto er blevet kompromitteret, der udløser en besked. Vil du vide mere om beskeder? Se [Beskedpolitikker](../../compliance/alert-policies.md).

## <a name="next-steps"></a>Næste trin

- [Gennemgå de nødvendige tilladelser for at bruge AIR-funktioner](office-365-air.md#required-permissions-to-use-air-capabilities)

- [Find og undersøg ondsindede mails i Office 365](investigate-malicious-email-that-was-delivered.md)

- [Få mere at vide om AIR i Microsoft Defender til Endpoint](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [Besøg Oversigt Microsoft 365 for at se, hvad der snart kommer og rulles ud](https://www.microsoft.com/microsoft-365/roadmap?filters=)