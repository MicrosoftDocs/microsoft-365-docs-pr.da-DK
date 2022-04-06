---
title: Enhedslager
description: Få mere at vide om de tilgængelige funktioner, som du kan bruge på listen Enheder, f.eks. sortering, filtrering og eksport af listen for at forbedre undersøgelserne.
keywords: sort, filter, eksport, csv, enhedsnavn, domæne, sidst set, intern IP, tilstand, aktive beskeder, aktive malware opdagelser, trusselskategori, anmeldelsesbeskeder, netværk, forbindelse, malware, type, adgangskode stealer, ransomware, udnytte, trussel, generel malware, uønsket software
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 631a141ca6c898c6394bfd34839fd65d351fe8fc
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665530"
---
# <a name="device-inventory"></a>Enhedslager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-machinesview-abovefoldlink)

**På listen Enheder** vises en liste over de enheder på netværket, hvor der blev genereret beskeder. Som standard viser køen enheder, der er set inden for de sidste 30 dage.

Du kan hurtigt se oplysninger som f.eks. domæne, risikoniveau, OS-platform og andre oplysninger, så du nemt kan identificere de enheder, der er mest udsatte.

Der er flere indstillinger, du kan vælge imellem for at tilpasse listevisningen for enheder. På den øverste navigationslinje kan du:

- Tilføj eller fjern kolonner
- Eksportér hele listen i CSV-format
- Vælg det antal elementer, der skal vises pr. side
- Anvend filtre

Under onboardingprocessen udfyldes **listen Enheder** gradvist med enheder, når de begynder at rapportere sensordata. Brug denne visning til at spore dine onboardede slutpunkter, efterhånden som de bliver online, eller download den komplette slutpunktsliste som en CSV-fil til offlineanalyse.

> [!NOTE]
> Hvis du eksporterer enhedslisten, indeholder den alle enheder i din organisation. Det kan tage lang tid at downloade, afhængigt af hvor stor din organisation er. Når du eksporterer listen i CSV-format, vises dataene på en ufiltreret måde. CSV-filen omfatter alle enheder i organisationen, uanset hvilken filtrering der er anvendt i selve visningen.

:::image type="content" source="images/device-inventory.png" alt-text="Listen over enheder" lightbox="images/device-inventory.png":::

## <a name="sort-and-filter-the-device-list"></a>Sortér og filtrer enhedslisten

Du kan anvende følgende filtre for at begrænse listen over beskeder og få en mere fokuseret visning.

### <a name="device-name"></a>Enhedsnavn

Under den Microsoft Defender for Endpoint onboardingproces udfyldes enheder, der er onboardet til MDE, gradvist i enhedslageret, når de begynder at rapportere sensordata. Herefter udfyldes enhedsoversigten af enheder, der registreres på netværket via enhedens registreringsproces. Enhedsoversigten har tre faner, der viser enheder efter:

- **Computere og mobilenheder**: Virksomhedsslutpunkter (arbejdsstationer, servere og mobilenheder)
- **Netværksenheder**: Enheder som routere og kontakter
- **IoT-enheder**: Enheder som printere og kameraer

## <a name="navigate-to-the-device-inventory-page"></a>Gå til siden Enhedslager

Få adgang til enhedens lagerside ved at vælge **Enhedslager** i **navigationsmenuen Slutpunkter** på [Microsoft 365 Defender portalen](/defender/microsoft-365-security-center-mde).

## <a name="device-inventory-overview"></a>Oversigt over enhedslager

Enhedsoversigten åbnes under fanen **Computere og mobil** . Du kan hurtigt se oplysninger som enhedsnavn, domæne, risikoniveau, eksponeringsniveau, OS-platform, onboardingstatus, tilstand for sensortilstand og andre oplysninger, så du nemt kan identificere de enheder, der er mest udsatte.

Brug kolonnen **Onboarding Status** til at sortere og filtrere efter registrerede enheder og dem, der allerede er onboardet til Microsoft Defender for Endpoint.

![Billede af listen over enheder med en liste over enheder.](images/device-inventory.png)

Under fanerne **Netværksenheder** og **IoT-enheder** kan du også se oplysninger som leverandør, model og enhedstype:

![Billede af listen over netværksenheder.](images/device-inventory-networkdevices.png)

Øverst på hver enheds lagerfane kan du se det samlede antal enheder, antallet af enheder, der endnu ikke er onboardet, og antallet af enheder, der er blevet identificeret som en højere risiko for din organisation. Du kan bruge disse oplysninger til at hjælpe dig med at prioritere enheder i forbindelse med forbedringer af sikkerhedsholdning.

Fanerne **Nyopdaget** enhed for netværksenheder og IoT-enheder viser antallet af nye enheder, der er registreret inden for de seneste 7 dage, og som er angivet i den aktuelle visning.

![Billede af antallet af nye fundne enheder.](images/new-discovered-devices.png)

## <a name="explore-the-device-inventory"></a>Udforsk enhedsoversigten

Der er flere muligheder, du kan vælge imellem for at tilpasse enhedens lagervisning. På den øverste navigationslinje for hver fane kan du:

- Søg efter en enhed efter navn
- Søg efter en enhed efter den senest anvendte IP-adresse eller præfikset IP-adresse
- Tilføj eller fjern kolonner
- Eksportér hele listen i CSV-format til offlineanalyse
- Vælg det datointerval, der skal vises
- Anvend filtre

> [!NOTE]
> Hvis du eksporterer enhedslisten, indeholder den alle enheder i din organisation. Det kan tage lang tid at downloade, afhængigt af hvor stor din organisation er. Når du eksporterer listen i CSV-format, vises dataene på en ufiltreret måde. CSV-filen omfatter alle enheder i organisationen, uanset hvilken filtrering der er anvendt i selve visningen.

Du kan bruge den sorterings- og filterfunktionalitet, der er tilgængelig på hver enheds lagerfane, til at få en mere fokuseret visning og til at hjælpe dig med at vurdere og administrere enhederne i din organisation.

Antallet øverst på hver fane opdateres på baggrund af den aktuelle visning.

## <a name="use-filters-to-customize-the-device-inventory-views"></a>Brug filtre til at tilpasse enhedslagervisningerne

Filter | Beskrivelse
:---|:---
**Risikoniveau** </br> | Risikoniveauet afspejler enhedens overordnede risikovurdering baseret på en kombination af faktorer, herunder typerne og alvorsgraden af aktive beskeder på enheden. Løsning af aktive beskeder, godkendelse af afhjælpningsaktiviteter og undertrykkelse af efterfølgende beskeder kan sænke risikoniveauet.
**Eksponeringsniveau** </br> | Eksponeringsniveauet afspejler enhedens aktuelle eksponering baseret på den kumulative virkning af dens afventende sikkerhedsanbefalinger. De mulige niveauer er lave, mellem og høje. Lav eksponering betyder, at dine enheder er mindre sårbare over for udnyttelse. </br> </br> Hvis der på eksponeringsniveauet står "Ingen tilgængelige data", er der et par grunde til, at dette kan være tilfældet:</br>- Enheden stoppede rapporteringen i mere end 30 dage. I så fald betragtes den som inaktiv, og eksponeringen beregnes ikke.</br>– Enhedsoperativsystemer understøttes ikke – se [minimumkrav til Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/minimum-requirements).</br>- Enhed med forældet agent (usandsynligt).
**Tags** </br> | Filtrer listen baseret på den gruppering og mærkning, du har føjet til de enkelte enheder. Se [Opret og administrer enhedskoder](machine-tags.md).
**Enhedsværdi**</br> | Filtrer listen ud fra, om enheden er markeret som høj eller lav værdi.
**Udeladelsestilstand** </br> | Filtrer listen ud fra, om enheden er blevet udelukket eller ej. Du kan få flere oplysninger under [Udelad enheder](exclude-devices.md).
**OS-platform** </br>| Filtrer efter de OS-platforme, du er interesseret i at undersøge </br></br>(_Kun computere og mobilenheder og IoT-enheder_)
**Først set** </br> | Filtrer visningen på baggrund af, hvornår enheden første gang blev set på netværket, eller hvornår den første gang blev rapporteret af Microsoft Defender for Endpoint sensor.</br></br>(_Kun computere og mobilenheder og IoT-enheder_)
**Windows version** </br> | Filtrer efter de Windows versioner, du er interesseret i at undersøge.</br></br> (_Kun computere og mobilenheder_)
**Tilstand for sensortilstand** </br> | Filtrer efter følgende tilstande for sensortilstand for enheder, der er onboardet i Microsoft Defender for Endpoint:</br> - **Aktiv**: Enheder, der aktivt rapporterer sensordata til tjenesten.</br> - **Inaktiv:** Enheder, der har stoppet med at sende signaler i mere end 7 dage. </br> - **Forkert konfigureret**: Enheder, der har nedsat kommunikation med tjenesten eller ikke kan sende sensordata. </br> Forkert konfigurerede enheder kan klassificeres yderligere til: </br>  - Ingen sensordata </br>  - Nedsat kommunikation </br>  Du kan finde flere oplysninger om, hvordan du løser problemer på forkert konfigurerede enheder, under [Løs usunde sensorer](/microsoft-365/security/defender-endpoint/fix-unhealthy-sensors).</br></br> (_Kun computere og mobilenheder_)
**Onboardingstatus** </br> | Onboardingstatus angiver, om enheden i øjeblikket er onboardet til Microsoft Defender for Endpoint eller ej. Du kan filtrere efter følgende tilstande: </br> - **Onboardet**: Slutpunktet er onboardet til Microsoft Defender for Endpoint.  </br> - **Kan onboardes**: Slutpunktet blev fundet i netværket som en understøttet enhed, men det er i øjeblikket ikke onboardet. Microsoft anbefaler på det kraftigste onboarding af disse enheder. </br> - **Ikke understøttet**: Slutpunktet blev fundet på netværket, men understøttes ikke af Microsoft Defender for Endpoint. </br> - **Utilstrækkelige oplysninger**: Systemet kunne ikke fastslå, om enheden understøttes.</br></br> (_Kun computere og mobilenheder_)
**Status for antivirus** </br> | Filtrer visningen baseret på, om antivirusstatussen er deaktiveret, ikke opdateret eller ukendt.</br></br> (_Kun computere og mobilenheder_)
**Gruppe** </br> | Filtrer listen baseret på den gruppe, du er interesseret i at undersøge. </br></br> (_Kun computere og mobilenheder_)
**Administreret af** </br> | Administreret af angiver, hvordan enheden administreres. Du kan filtrere efter:</br>- Microsoft Defender for Endpoint </br> – Administration af mobilenheder (MDM) </br>- Ukendt: Dette kan skyldes, at der kører en forældet Windows version, at SCCM er på plads, eller at en anden tredjepart MDM kører.</br></br> (_Kun computere og mobilenheder_)
**Enhedstype** </br> | Filtrer efter den enhedstype, du er interesseret i at undersøge.</br></br> (_Kun IoT-enheder_)

## <a name="use-columns-to-customize-the-device-inventory-views"></a>Brug kolonner til at tilpasse enhedslagervisningerne

Du kan tilføje eller fjerne kolonner fra visningen og sortere posterne ved at klikke på en tilgængelig kolonneoverskrift.

Under fanen **Computer og mobilenheder** skal du vælge **Tilpas kolonner** for at se de tilgængelige kolonner. Standardværdierne kontrolleres på billedet nedenfor:

![Billede af computere og mobilenheder](images/computerandmobilescolumns.png)

Under fanen **Netværksenheder** skal du vælge **Tilpas kolonner** for at se de tilgængelige kolonner. Standardværdierne kontrolleres på billedet nedenfor:

![Billede af netværksenhedskolonner](images/networkdevicescolumns.png)

På fanen **IoT-enheder** skal du vælge **Tilpas kolonner** for at se de tilgængelige kolonner. Standardværdierne kontrolleres på billedet nedenfor:

![Billede af IoT-enhedskolonner](images/iotdevicescolumns.png)

## <a name="related-articles"></a>Relaterede artikler

[Undersøg enheder på listen over Microsoft Defender for Endpoint enheder](investigate-machines.md)
