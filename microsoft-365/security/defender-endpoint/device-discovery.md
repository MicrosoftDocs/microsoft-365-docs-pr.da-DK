---
title: Oversigt over enhedsregistrering
description: Få mere at vide om, hvordan du kan udnytte slutpunktsregistrering Microsoft 365 Defender at finde ikke-administrerede enheder i dit netværk
keywords: enhedsregistrering, find, passiv, proaktiv, netværk, synlighed, server, arbejdsstation, onboard, ikke-administrerede enheder
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: siosulli
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365-initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 926d23cb4e9abcecd9d34e976dee60851471613b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472919"
---
# <a name="device-discovery-overview"></a>Oversigt over enhedsregistrering

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Beskyttelse af dit miljø kræver, at du lageropgørelser over de enheder, der er i dit netværk. Men tilknytningsenheder i et netværk kan ofte være dyre, udfordrende og tidskrævende.

Microsoft Defender for Endpoint en funktion til registrering af enheder, der hjælper dig med at finde enheder, der ikke er administrerede, og som er sluttet til virksomhedens netværk uden behov for ekstra hvidevarer eller besværlige procesændringer. Enhedsregistrering bruger onboardede slutpunkter i dit netværk til at indsamle, undersøge eller scanne dit netværk for at finde ikke-administrerede enheder. Registreringsfunktionaliteten for enheder gør det muligt at finde:

- Enterprise-slutpunkter (arbejdsstationer, servere og mobilenheder), der endnu ikke er onboardet Microsoft Defender for Endpoint
- Netværksenheder som routere og skift
- IoT-enheder som printere og kameraer

Ukendte og ikke-administrerede enheder indebærer betydelige risici i dit netværk – uanset om det er en ikke-sendt printer, netværksenheder med svage sikkerhedskonfigurationer eller en server uden sikkerhedskontrolelementer. Når enhederne findes, kan du:

- Onboard ikke-administrerede slutpunkter i tjenesten, hvilket øger synligheden af sikkerheden på dem.
- Reducer angrebsoverfladen ved at identificere og vurdere sårbarheder og opdage konfigurationsproblemer.

Se denne video for at få et hurtigt overblik over, hvordan opdagelse af enheder:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWORdQ]

Sammen med denne funktion er en sikkerhedsanbefaling til onboardingenheder Microsoft Defender for Endpoint tilgængelig som en del af den eksisterende Håndtering af trusler og sikkerhedsrisici oplevelse.

## <a name="discovery-methods"></a>Registreringsmetoder

Du kan vælge registreringstilstanden, der skal bruges af dine onboardede enheder. Tilstanden styrer det synlighedsniveau, du kan få for enheder, der ikke er administrerede i virksomhedens netværk.

Der findes to metoder til opdagelse:

- **Grundlæggende opdagelse**: I denne tilstand indsamler slutpunkter passivt hændelser i dit netværk og udtrækker enhedsoplysninger fra dem. Grundlæggende opdagelse bruger binær SenseNDR.exe til indsamling af passive netværksdata, og netværkstrafik startes ikke. Slutpunkter udtrækker ganske enkelt data fra hver enkelt netværkstrafik, der ses af en onboarded enhed. Med grundlæggende opdagelse får du kun begrænset synlighed af ikke-administrerede slutpunkter i dit netværk.

- **Standardregistrering** (anbefales): Med denne tilstand kan slutpunkter aktivt finde enheder i dit netværk til at forbedre indsamlede data og finde flere enheder – hvilket hjælper dig med at opbygge et pålideligt og sammenhængende lager over enheder. Ud over enheder, der er blevet observeret ved hjælp af den passive metode, udnytter standardtilstand også almindelige registreringsprotokoller, der bruger multicast-forespørgsler på netværket til at finde endnu flere enheder. Standardtilstand anvender smart, aktiv sonde til at finde yderligere oplysninger om observerede enheder til at forbedre eksisterende enhedsoplysninger. Når standardtilstanden er aktiveret, kan minimal og tilsigtet netværksaktivitet, der genereres af Discovery-sensoren, observeres af netværksværktøjer i organisationen.

Du kan ændre og tilpasse dine registreringsindstillinger for at få mere at vide under [Konfigurer enhedsregistrering](configure-device-discovery.md).

> [!IMPORTANT]
> Standardregistrering er standardtilstanden for alle kunder fra den 19. juli 2021. Du kan vælge at ændre denne konfiguration til grundlæggende via siden med indstillinger. Hvis du vælger grundlæggende tilstand, får du kun begrænset synlighed af ikke-administrerede slutpunkter i dit netværk.

> [!NOTE]
> Discovery-programmet skelner mellem netværkshændelser, der modtages i virksomhedens netværk kontra uden for virksomhedens netværk. Enheder, der ikke har forbindelse til virksomhedens netværk, vil ikke blive fundet eller anført på listen over enheder.

## <a name="device-inventory"></a>Lagerenhed

Enheder, der er blevet fundet, men endnu ikke er blevet onboardet og sikret af Microsoft Defender for Endpoint, vil blive vist på enhedens lager under fanen Computere og mobil.

For at vurdere disse enheder kan du bruge et filter på lagerlisten for enheder med navnet Onboardingstatus, som kan have en af følgende værdier:

- Onboarded: Slutpunktet er onboardet til Microsoft Defender for Endpoint.
- Kan onboardes: Slutpunktet blev fundet i netværket, og operativsystemet blev identificeret som et, der understøttes af Microsoft Defender for Endpoint, men det er ikke i øjeblikket onboardet. Vi anbefaler stærkt, at du onboarder disse enheder.
- Ikke understøttet: Slutpunktet blev fundet på netværket, men understøttes ikke af Microsoft Defender for Endpoint.
- Utilstrækkelige oplysninger: Systemet kunne ikke fastslå, om enheden understøttes. Aktivering af standardregistrering på flere enheder i netværket kan forbedre de fundne attributter.

:::image type="content" source="images/2b62255cd3a9dd42f3219e437b956fb9.png" alt-text="Dashboard for lagerenhed" lightbox="images/2b62255cd3a9dd42f3219e437b956fb9.png":::

> [!TIP]
> Du kan altid anvende filtre for at udelukke enheder, der ikke er administrerede, fra listen over enheders lager. Du kan også bruge kolonnen onboardingstatus på API-forespørgsler til at frafiltrere enheder, der ikke er administrerede.

Du kan få mere at vide under [Lager over enheder](machines-view-overview.md).

## <a name="network-device-discovery"></a>Registrering af netværksenhed

Det store antal ikke-administrerede netværksenheder, der er installeret i en organisation, opretter et stort angrebsområde på overfladen og udgør en betydelig risiko for hele virksomheden. Microsoft Defender for Endpoint med netværksregistrering hjælper dig med at sikre, at netværksenheder opdages, klassificeres nøjagtigt og føjes til aktivlageret.

Netværksenheder administreres ikke som almindelige slutpunkter, da Defender til slutpunkt ikke har en sensor indbygget i selve netværksenhederne. Disse typer enheder kræver en agentløs tilgang, hvor en fjernscanning henter de nødvendige oplysninger fra enhederne. For at gøre dette skal en Microsoft Defender for Endpoint enhed bruges på hvert netværkssegment til at udføre periodiske godkendte scanninger af forudkonfigurerede netværksenheder. Når De opdages, giver Defender for Endpoints Håndtering af trusler og sikkerhedsrisici-funktioner integrerede arbejdsprocesser til at sikre switche, routere, WLAN-controllere, firewalls og VPN-gateways.

Du kan finde flere oplysninger [under Netværksenheder](network-devices.md).

## <a name="device-discovery-integrations"></a>Integration af enhedsregistrering

For at løse udfordringen med at få tilstrækkelig synlighed til at finde, identificere og sikre dit komplette lager over OT/IOT-aktiver Microsoft Defender for Endpoint understøtter nu følgende integrationer:

- **Corelight**: Microsoft har indgået partnerskab med Corelight for at modtage data fra Corelight-netværkskabe. Dette giver Microsoft 365 Defender øget synlighed i netværksaktiviteterne for enheder, der ikke er administrerede, herunder kommunikation med andre enheder, der ikke er administrerede, eller eksterne netværk. Få mere at vide under [Aktivér Corelight-dataintegration](corelight-integration.md).

- **Microsoft Defender til IoT**: Denne integration kombinerer Microsoft Defender for Endpoint's enhedsregistreringsfunktioner med de agentfri overvågningsfunktioner i Microsoft Defender til IoT for at sikre virksomhedens IoT-enheder, der er sluttet til et it-netværk (f.eks. VoIP (Voice over Internet Protocol), printere og smart-tv). Få mere at vide under [Aktivér Microsoft Defender til IoT-integration](enable-microsoft-defender-for-iot-integration.md).

## <a name="vulnerability-assessment-on-discovered-devices"></a>Vurdering af sikkerhedsrisiko på enheder, der opdages

Sårbarheder og risici på dine enheder samt andre enheder, der ikke er administrerede i netværket, er en del af de aktuelle TVM-flows under "Security Anbefalinger" og er repræsenteret på enhedssider på tværs af portalen.
Søg efter "SSH"-relaterede sikkerhedsanbefalinger for at finde SSH-sårbarheder, der er relateret til ikke-administrerede og administrerede enheder.

:::image type="content" source="images/1156c82ffadd356ce329d1cf551e806c.png" alt-text="Dashboardet med sikkerhedsanbefalinger" lightbox="images/1156c82ffadd356ce329d1cf551e806c.png":::


## <a name="use-advanced-hunting-on-discovered-devices"></a>Brug Avanceret jagt på enheder, der opdages

Du kan bruge avanceret jagtforespørgsler til at opnå synlighed på enheder, der opdages.
Find oplysninger om fundne slutpunkter i tabellen DeviceInfo eller netværksrelaterede oplysninger om disse enheder i tabellen DeviceNetworkInfo.

:::image type="content" source="images/f48ba1779eddee9872f167453c24e5c9.png" alt-text="Den avancerede jagtside, hvor forespørgsler kan bruges" lightbox="images/f48ba1779eddee9872f167453c24e5c9.png":::

Enhedsregistrering udnytter Microsoft Defender for Endpoint onboardede enheder som en netværksdatakilde til at attributaktiviteter til ikke-onboardede enheder. Det betyder, at hvis en Microsoft Defender for Endpoint onboarded enhed kommunikeret med en ikke-onboardet enhed, kan aktiviteter på den ikke-onboardede enhed ses på tidslinjen og via tabellen Avanceret på jagt efter DeviceNetworkEvents.

Nye hændelser er TCP-forbindelser (Transmission Control Protocol) og vil passe til det aktuelle DeviceNetworkEvents-skema. TCP-Microsoft Defender for Endpoint fra en ikke-aktiveret Microsoft Defender for Endpoint.

Følgende handlingstyper er også blevet tilføjet:

- ConnectionAttempt – Et forsøg på at oprette en TCP-forbindelse (syn)
- ConnectionAckendt – En bekræftelse af, at en TCP-forbindelse blev accepteret (syn\ack)

Du kan prøve denne eksempelforespørgsel:

```text
DeviceNetworkEvents
| where ActionType == "ConnectionAcknowledged" or ActionType == "ConnectionAttempt"
| take 10
```

## <a name="next-steps"></a>Næste trin

- [Konfigurer enhedsregistrering](configure-device-discovery.md)
- [Ofte stillede spørgsmål om enhedsregistrering](device-discovery-faq.md)
