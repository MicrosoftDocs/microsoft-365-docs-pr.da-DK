---
title: Håndter kompromitterede brugerkonti med automatiseret undersøgelse og svar
keywords: AIR, autoIR, Microsoft Defender for Endpoint, automatiseret, undersøgelse, reaktion, afhjælpning, trusler, avanceret, trussel, beskyttelse, kompromitteret
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
description: Få mere at vide om, hvordan du fremskynder processen med at registrere og løse kompromitterede brugerkonti med automatiserede undersøgelses- og svarfunktioner i Microsoft Defender for Office 365 Plan 2.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a8c78847e36d4a4887c4f7a3c54904cc26a012e5
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131146"
---
# <a name="address-compromised-user-accounts-with-automated-investigation-and-response"></a>Håndter kompromitterede brugerkonti med automatiseret undersøgelse og svar

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Microsoft Defender for Office 365 Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) indeholder effektive [funktioner til automatiseret undersøgelse og svar](office-365-air.md) (AIR). Sådanne funktioner kan spare dit team for sikkerhedshandlinger en masse tid og kræfter på at håndtere trusler. Microsoft fortsætter med at forbedre sikkerhedsfunktionerne. For nylig blev AIR-funktionerne udvidet til at omfatte en kompromitteret brugersikkerhedslegebog (i øjeblikket som prøveversion). Læs denne artikel for at få mere at vide om den kompromitterede brugersikkerhedslegebog. Og se blogindlægget [Gør det hurtigere at registrere og reagere på brugerkompromis og begrænse omfanget af brud med Microsoft Defender for Office 365 for at](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Speed-up-time-to-detect-and-respond-to-user-compromise-and-limit/ba-p/977053) få flere oplysninger.

![Automatiseret undersøgelse for en kompromitteret bruger.](/microsoft-365/media/office365atp-compduserinvestigation.jpg)

Den kompromitterede brugersikkerhedslegebog gør det muligt for organisationens sikkerhedsteam at:

- Gør registreringen af kompromitterede brugerkonti hurtigere.
- Begræns omfanget af et brud, når en konto kompromitteres. Og
- Reager på kompromitterede brugere mere effektivt og effektivt.

## <a name="compromised-user-alerts"></a>Kompromitterede brugerbeskeder

Når en brugerkonto kompromitteres, opstår der atypiske eller unormale funktionsmåder. Phishing- og spammeddelelser kan f.eks. blive sendt internt fra en brugerkonto, der er tillid til. Defender for Office 365 kan registrere sådanne uregelmæssigheder i mailmønstre og samarbejdsaktivitet i Office 365. Når det sker, udløses beskeder, og processen til afhjælpning af trusler starter.

Her er f.eks. en besked, der blev udløst på grund af mistænkelig afsendelse af mail:

![Beskeden blev udløst på grund af mistænkelig afsendelse af mail.](/microsoft-365/media/office365atp-suspiciousemailsendalert.jpg)

Og her er et eksempel på en besked, der blev udløst, da en afsendelsesgrænse blev nået for en bruger:

![Besked udløst af afsendelsesgrænsen er nået.](/microsoft-365/media/office365atp-sendinglimitreached.jpg)

## <a name="investigate-and-respond-to-a-compromised-user"></a>Undersøg og reager på en kompromitteret bruger

Når en brugerkonto kompromitteres, udløses der beskeder. Og i nogle tilfælde er brugerkontoen blokeret og forhindret i at sende yderligere mails, indtil problemet er løst af organisationens sikkerhedsteam. I andre tilfælde starter en automatiseret undersøgelse, hvilket kan resultere i anbefalede handlinger, som dit sikkerhedsteam skal foretage.

- [Få vist og undersøg begrænsede brugere](#view-and-investigate-restricted-users)

- [Få vist oplysninger om automatiserede undersøgelser](#view-details-about-automated-investigations)

> [!IMPORTANT]
> Du skal have de nødvendige tilladelser til at udføre følgende opgaver. Se [Påkrævede tilladelser til at bruge AIR-funktioner](office-365-air.md#required-permissions-to-use-air-capabilities).

### <a name="view-and-investigate-restricted-users"></a>Få vist og undersøg begrænsede brugere

Du har et par muligheder for at navigere til en liste over begrænsede brugere. På Microsoft 365 Defender-portalen kan du f.eks. gå til **Mail & samarbejde** \> **Gennemse** **brugere med begrænset adgang**\>. I følgende procedure beskrives navigationen ved hjælp af dashboardet **Beskeder** , hvilket er en god måde at se forskellige typer beskeder, der kan være blevet udløst.

1. Åbn Microsoft 365 Defender-portalen på , <https://security.microsoft.com> og gå til **Hændelser & vigtige beskeder**\>. Du kan også gå direkte til siden **Beskeder** ved at bruge <https://security.microsoft.com/alerts>.

2. På siden **Beskeder** skal du filtrere resultaterne efter tidsperiode og politikken med navnet **Bruger begrænset fra at sende mail**.

   :::image type="content" source="../../media/m365-sc-alerts-page-with-restricted-user.png" alt-text="Siden Beskeder på Microsoft 365 Defender-portalen filtreret efter brugere med begrænset adgang" lightbox="../../media/m365-sc-alerts-page-with-restricted-user.png":::

3. Hvis du vælger posten ved at klikke på navnet, åbnes en bruger, der ikke kan **sende mailsiden** , med yderligere oplysninger, som du kan gennemse. Ud for knappen **Administrer besked** kan du klikke på ![ikonet Flere indstillinger.](../../media/m365-cc-sc-more-actions-icon.png) **Flere indstillinger** , og vælg derefter **Vis begrænsede brugeroplysninger** for at gå til siden **Begrænsede brugere** , hvor du kan [frigive den begrænsede bruger](removing-user-from-restricted-users-portal-after-spam.md).

  :::image type="content" source="../../media/m365-sc-alerts-user-restricted-from-sending-email-page.png" alt-text="Brugeren har begrænset adgang til at sende en mailside" lightbox="../../media/m365-sc-alerts-user-restricted-from-sending-email-page.png":::

### <a name="view-details-about-automated-investigations"></a>Få vist oplysninger om automatiserede undersøgelser

Når en automatiseret undersøgelse er begyndt, kan du se dens detaljer og resultater i Security & Compliance Center. Gå til **Trusselsadministrationsundersøgelser**\>, og vælg derefter en undersøgelse for at få vist dens detaljer.

Du kan få mere at vide under [Få vist detaljer om en undersøgelse](air-view-investigation-results.md).

## <a name="keep-the-following-points-in-mind"></a>Vær opmærksom på følgende punkter

- **Hold dig opdateret om dine beskeder**. Jo længere et kompromis bliver opdaget, jo større er risikoen for omfattende indvirkning og omkostninger for din organisation, dine kunder og dine partnere. Tidlig registrering og rettidig reaktion er afgørende for at afhjælpe trusler, og især når en brugers konto kompromitteres.

- **Automatisering hjælper, men erstatter ikke, dit team for sikkerhedshandlinger**. Automatiserede undersøgelses- og svarfunktioner kan registrere en kompromitteret bruger tidligt, men dit team for sikkerhedshandlinger skal sandsynligvis foretage undersøgelser og afhjælpning. Har du brug for hjælp til dette? Se [Gennemse og godkend handlinger](air-review-approve-pending-completed-actions.md).

- **Brug ikke en mistænkelig logonadvarsel som din eneste indikator**. Når en brugerkonto er kompromitteret, udløser den muligvis eller udløser muligvis ikke en mistænkelig logonbesked. Nogle gange er det en række aktiviteter, der forekommer, når en konto er kompromitteret, som udløser en besked. Vil du vide mere om beskeder? Se [Beskedpolitikker](../../compliance/alert-policies.md).

## <a name="next-steps"></a>Næste trin

- [Gennemse de nødvendige tilladelser for at bruge AIR-funktioner](office-365-air.md#required-permissions-to-use-air-capabilities)

- [Find og undersøg skadelige mails i Office 365](investigate-malicious-email-that-was-delivered.md)

- [Få mere at vide om AIR i Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [Besøg køreplanen for Microsoft 365 for at se, hvad der kommer snart, og udrulle](https://www.microsoft.com/microsoft-365/roadmap?filters=)
