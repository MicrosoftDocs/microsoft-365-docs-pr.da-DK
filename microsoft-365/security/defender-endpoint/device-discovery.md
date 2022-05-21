---
title: Oversigt over enhedssøgning
description: Få mere at vide om, hvordan du udnytter registrering af slutpunkter i Microsoft 365 Defender til at finde ikke-administrerede enheder i dit netværk
keywords: enhedsregistrering, finde, passiv, proaktiv, netværk, synlighed, server, arbejdsstation, onboard, ikke-administrerede enheder
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
ms.openlocfilehash: 68503556a1d2f3330e47fe601a303363a3f28896
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623241"
---
# <a name="device-discovery-overview"></a>Oversigt over enhedssøgning

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Beskyttelse af dit miljø kræver, at du opretter en oversigt over de enheder, der findes i dit netværk. Tilknytning af enheder i et netværk kan dog ofte være dyrt, udfordrende og tidskrævende.

Microsoft Defender for Endpoint indeholder en enhedsregistreringsfunktion, der hjælper dig med at finde ikke-administrerede enheder, der er tilsluttet virksomhedens netværk, uden at der er behov for ekstra apparater eller besværlige procesændringer. Enhedsregistrering bruger onboardede slutpunkter i dit netværk til at indsamle, undersøge eller scanne dit netværk for at finde ikke-administrerede enheder. Funktionen til enhedsregistrering giver dig mulighed for at finde:

- Virksomhedsslutpunkter (arbejdsstationer, servere og mobilenheder), der endnu ikke er onboardet til Microsoft Defender for Endpoint
- Netværksenheder som routere og kontakter
- IoT-enheder som printere og kameraer

Ukendte og ikke-administrerede enheder medfører betydelige risici for dit netværk – uanset om det er en ikke-opdateret printer, netværksenheder med svage sikkerhedskonfigurationer eller en server uden sikkerhedskontroller. Når enhederne er fundet, kan du:

- Onboarde ikke-administrerede slutpunkter til tjenesten, hvilket øger sikkerhedens synlighed på dem.
- Reducer angrebsoverfladen ved at identificere og vurdere sikkerhedsrisici og registrere konfigurationshuller.

Se denne video for at få et hurtigt overblik over, hvordan du vurderer og onboarder ikke-administrerede enheder, som Microsoft Defender for Endpoint opdaget.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4RwQz]

I forbindelse med denne funktion findes der en sikkerhedsanbefaling til onboarding af enheder til Microsoft Defender for Endpoint som en del af den eksisterende Håndtering af trusler og sikkerhedsrisici oplevelse.

## <a name="discovery-methods"></a>Registreringsmetoder

Du kan vælge den registreringstilstand, der skal bruges af dine onboardede enheder. Tilstanden styrer det synlighedsniveau, du kan få for ikke-administrerede enheder på virksomhedens netværk.

Der er to tilgængelige registreringstilstande:

- **Grundlæggende registrering**: I denne tilstand indsamler slutpunkter passivt hændelser i dit netværk og udtrækker enhedsoplysninger fra dem. Grundlæggende søgning bruger den binære SenseNDR.exe til indsamling af passive netværksdata, og der vil ikke blive startet netværkstrafik. Slutpunkter udtrækker blot data fra hver netværkstrafik, der ses af en onboardet enhed. Med grundlæggende registrering får du kun begrænset synlighed af ikke-administrerede slutpunkter i dit netværk.

- **Standardregistrering** (anbefales): Denne tilstand gør det muligt for slutpunkter aktivt at finde enheder på dit netværk for at forbedre indsamlede data og finde flere enheder – hvilket hjælper dig med at opbygge en pålidelig og sammenhængende enhedsoversigt. Ud over enheder, der blev observeret ved hjælp af den passive metode, bruger standardtilstand også almindelige registreringsprotokoller, der bruger multicast-forespørgsler i netværket, til at finde endnu flere enheder. Standardtilstand bruger intelligente, aktive sondering til at finde yderligere oplysninger om observerede enheder for at forbedre eksisterende enhedsoplysninger. Når Standardtilstand er aktiveret, kan minimal og ubetydelig netværksaktivitet, der genereres af registreringssensoren, blive observeret af værktøjer til netværksovervågning i din organisation.

Du kan ændre og tilpasse dine registreringsindstillinger. Du kan finde flere oplysninger under [Konfigurer enhedsregistrering](configure-device-discovery.md).

> [!IMPORTANT]
> Standardregistrering er standardtilstanden for alle kunder fra den 19. juli 2021. Du kan vælge at ændre denne konfiguration til grundlæggende via indstillingssiden. Hvis du vælger grundlæggende tilstand, får du kun begrænset synlighed af ikke-administrerede slutpunkter i dit netværk.

> [!NOTE]
> Registreringsprogrammet skelner mellem netværkshændelser, der modtages i virksomhedens netværk i forhold til uden for virksomhedens netværk. Enheder, der ikke har forbindelse til virksomhedens netværk, bliver ikke fundet eller angivet i enhedsoversigten.

## <a name="device-inventory"></a>Enhedslager

Enheder, der er blevet fundet, men endnu ikke er blevet onboardet og sikret af Microsoft Defender for Endpoint, vises i enhedsoversigten under fanen Computere og mobil.

Hvis du vil vurdere disse enheder, kan du bruge et filter på enhedens lagerliste kaldet Onboarding-status, som kan have en af følgende værdier:

- Onboardet: Slutpunktet er onboardet til Microsoft Defender for Endpoint.
- Kan onboardes: Slutpunktet blev opdaget i netværket, og operativsystemet blev identificeret som et, der understøttes af Microsoft Defender for Endpoint, men det er i øjeblikket ikke onboardet. Vi anbefaler på det kraftigste, at du onboarder disse enheder.
- Ikke understøttet: Slutpunktet blev fundet på netværket, men understøttes ikke af Microsoft Defender for Endpoint.
- Utilstrækkelige oplysninger: Systemet kunne ikke fastslå, om enheden understøttes. Aktivering af standardregistrering på flere enheder i netværket kan forbedre de registrerede attributter.

:::image type="content" source="images/2b62255cd3a9dd42f3219e437b956fb9.png" alt-text="Enhedens lagerdashboard" lightbox="images/2b62255cd3a9dd42f3219e437b956fb9.png":::

> [!TIP]
> Du kan altid anvende filtre for at udelade ikke-administrerede enheder fra enhedslagerlisten. Du kan også bruge kolonnen med onboardingstatus i API-forespørgsler til at filtrere ikke-administrerede enheder fra.

Du kan få flere oplysninger under [Enhedsoversigt](machines-view-overview.md).

## <a name="network-device-discovery"></a>Registrering af netværksenhed

Det store antal ikke-administrerede netværksenheder, der er installeret i en organisation, opretter et stort angrebsområde og udgør en betydelig risiko for hele virksomheden. Microsoft Defender for Endpoint netværksregistreringsfunktioner hjælper dig med at sikre, at netværksenheder registreres, klassificeres nøjagtigt og føjes til aktivlageret.

Netværksenheder administreres ikke som standardslutpunkter, da Defender for Endpoint ikke har en sensor indbygget i selve netværksenhederne. Disse typer enheder kræver en agentløs tilgang, hvor en fjernscanning henter de nødvendige oplysninger fra enhederne. For at gøre dette bruges en angivet Microsoft Defender for Endpoint enhed på hvert netværkssegment til at udføre periodiske godkendte scanninger af forudkonfigurerede netværksenheder. Når funktionerne i Defender for Endpoint er opdaget, leverer de funktioner til Håndtering af trusler og sikkerhedsrisici integrerede arbejdsprocesser, der sikrer fundne parametre, routere, WLAN-controllere, firewalls og VPN-gateways.

Du kan få flere oplysninger under [Netværksenheder](network-devices.md).

## <a name="device-discovery-integrations"></a>Integrationer af enhedsregistrering

Hvis du vil løse udfordringen med at få tilstrækkelig synlighed til at finde, identificere og sikre hele ot/IOT-aktivlageret, Microsoft Defender for Endpoint understøtter nu følgende integrationer:

- **Corelight**: Microsoft har indgået partnerskab med Corelight for at modtage data fra Corelight-netværksapparater. Dette giver Microsoft 365 Defender med øget synlighed i netværksaktiviteterne for ikke-administrerede enheder, herunder kommunikation med andre ikke-administrerede enheder eller eksterne netværk. Du kan få flere oplysninger under [Aktivér corelight-dataintegration](corelight-integration.md).

- **Microsoft Defender for IoT**: Denne integration kombinerer Microsoft Defender for Endpoint enheds registreringsfunktioner med de agentløse overvågningsfunktioner i Microsoft Defender til IoT for at sikre virksomheds-IoT-enheder, der er forbundet til et it-netværk (f.eks. VoIP (Voice over Internet Protocol), printere og intelligente tv'er). Du kan få flere oplysninger under [Aktivér Microsoft Defender for IoT-integration](enable-microsoft-defender-for-iot-integration.md).

## <a name="vulnerability-assessment-on-discovered-devices"></a>Vurdering af sårbarheder på registrerede enheder

Sikkerhedsrisici og risici på dine enheder samt andre registrerede ikke-administrerede enheder i netværket er en del af de aktuelle TVM-flow under "Sikkerheds Anbefalinger" og vises på enhedssider på tværs af portalen.
Søg efter "SSH"-relaterede sikkerhedsanbefalinger for at finde SSH-sikkerhedsrisici, der er relateret til ikke-administrerede og administrerede enheder.

:::image type="content" source="images/1156c82ffadd356ce329d1cf551e806c.png" alt-text="Dashboardet med sikkerhedsanbefalinger" lightbox="images/1156c82ffadd356ce329d1cf551e806c.png":::

## <a name="use-advanced-hunting-on-discovered-devices"></a>Brug avanceret jagt på registrerede enheder

Du kan bruge avancerede jagtforespørgsler til at få indsigt på registrerede enheder. Du kan finde oplysninger om registrerede enheder i tabellen DeviceInfo eller netværksrelaterede oplysninger om disse enheder i tabellen DeviceNetworkInfo.

:::image type="content" source="images/f48ba1779eddee9872f167453c24e5c9.png" alt-text="Siden Avanceret jagt, hvor forespørgsler kan bruges" lightbox="images/f48ba1779eddee9872f167453c24e5c9.png":::

### <a name="query-discovered-devices-details"></a>Oplysninger om fundne enheder for forespørgsler

Kør denne forespørgsel i tabellen DeviceInfo for at returnere alle registrerede enheder sammen med de nyeste oplysninger for hver enhed:

```query
DeviceInfo
| summarize arg_max(Timestamp, *) by DeviceId  // Get latest known good per device Id
| where isempty(MergedToDeviceId) // Remove invalidated/merged devices
| where OnboardingStatus != "Onboarded"
```

Ved at aktivere funktionen **SeenBy** kan du i din avancerede jagtforespørgsel få detaljer om, hvilken onboardet enhed en registreret enhed blev set af. Disse oplysninger kan hjælpe med at bestemme netværksplaceringen for hver fundet enhed og derefter hjælpe med at identificere den i netværket.

```query
DeviceInfo
| where OnboardingStatus != "Onboarded"
| summarize arg_max(Timestamp, *) by DeviceId 
| where isempty(MergedToDeviceId) 
| limit 100
| invoke SeenBy()
| project DeviceId, DeviceName, DeviceType, SeenBy
```

Du kan få flere oplysninger i funktionen [SeenBy().](/microsoft-365/security/defender/advanced-hunting-seenby-function)

### <a name="query-network-related-information"></a>Forespørg om netværksrelaterede oplysninger

Enhedsregistrering udnytter Microsoft Defender for Endpoint onboardede enheder som en netværksdatakilde til at tildele aktiviteter til ikke-onboardede enheder. Netværkssensoren på den Microsoft Defender for Endpoint onboardede enhed identificerer to nye forbindelsestyper:

- ConnectionAttempt – Et forsøg på at oprette en TCP-forbindelse (syn)
- ConnectionAcknowledged – En bekræftelse på, at en TCP-forbindelse blev accepteret (syn\ack)

Det betyder, at når en ikke-onboardet enhed forsøger at kommunikere med en onboardet Microsoft Defender for Endpoint enhed, genererer forsøget en DeviceNetworkEvent, og de ikke-onboardede enhedsaktiviteter kan ses på den onboardede enhedstidslinje og via tabellen Advanced hunting DeviceNetworkEvents.

Du kan prøve denne eksempelforespørgsel:

```text
DeviceNetworkEvents
| where ActionType == "ConnectionAcknowledged" or ActionType == "ConnectionAttempt"
| take 10
```

## <a name="next-steps"></a>Næste trin

- [Konfigurer enhedssøgning](configure-device-discovery.md)
- [Ofte stillede spørgsmål om enhedsregistrering](device-discovery-faq.md)
