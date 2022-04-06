---
title: Lagerenhed
description: Få mere at vide om de tilgængelige funktioner, du kan bruge, fra listen Enheder, f.eks sortering, filtrering og eksport af listen for at forbedre undersøgelser.
keywords: sortere, filtrere, eksportere, CSV, enhedsnavn, domæne, senest set, intern IP, tilstand, aktive beskeder, aktive malwareregistreringer, trusselskategori, gennemse beskeder, netværk, forbindelse, malware, type, adgangskodesvælger, ransomware, udnytte, trussel, generel malware, uønsket software
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
ms.openlocfilehash: a9753cdc818aefdf33411bd237327310dfc512ab
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474730"
---
# <a name="device-inventory"></a>Lagerenhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-machinesview-abovefoldlink)

Listen **Enheder viser** en liste over de enheder i dit netværk, hvor der blev genereret beskeder. Som standard viser køen enheder, der er set i de seneste 30 dage.

Med et hurtigt øjekast får du vist oplysninger som domæne, risikoniveau, operativsystemplatform og andre oplysninger, der gør det nemt at identificere de enheder, der er mest udsat.

Der er flere muligheder, du kan vælge mellem for at tilpasse listevisningen for enheder. På den øverste navigationslinje kan du:

- Tilføj eller fjern kolonner
- Eksportér hele listen i CSV-format
- Vælg antallet af elementer, der skal vises pr. side
- Anvend filtre

Under onboardingprocessen bliver listen **Enheder gradvist** udfyldt med enheder, når de begynder at rapportere sensordata. Brug denne visning til at spore dine onboardede slutpunkter, efterhånden som de bliver online, eller download den komplette slutpunktsliste som en CSV-fil til offlineanalyse.

> [!NOTE]
> Hvis du eksporterer enhedslisten, indeholder den alle enheder i organisationen. Det kan tage lang tid at downloade, afhængigt af hvor stor din organisation er. Hvis du eksporterer listen i CSV-format, vises dataene på en ufiltreret måde. CSV-filen inkluderer alle enheder i organisationen, uanset om der anvendes filtrering i selve visningen.

:::image type="content" source="images/device-inventory.png" alt-text="Listen over enheder" lightbox="images/device-inventory.png":::

## <a name="sort-and-filter-the-device-list"></a>Sortér og filtrer enhedslisten

Du kan anvende følgende filtre til at begrænse listen over beskeder og få en mere fokuseret visning.

### <a name="device-name"></a>Enhedsnavn

Under startprocessen Microsoft Defender for Endpoint enheder, der er onboardet til MDE, gradvist udfyldt på enhedens lager, når de begynder at rapportere sensordata. Efter dette udfyldes lageret af enheder, der findes i dit netværk via processen med registrering af enheder. Lagerenhed har tre faner, der viser enheder efter:

- **Computere og mobilenheder**: Virksomhedens slutpunkter (arbejdsstationer, servere og mobilenheder)
- **Netværksenheder**: Enheder som routere og skift
- **IoT-enheder**: Enheder som printere og kameraer

## <a name="navigate-to-the-device-inventory-page"></a>Gå til lagersiden for enheden

Få adgang til lagersiden for enheden **ved at vælge** Lagerenhed **i navigationsmenuen** Slutpunkter [i Microsoft 365 Defender portal](/defender/microsoft-365-security-center-mde).

## <a name="device-inventory-overview"></a>Oversigt over lager over enheder

Lagerlisten for enheder åbnes **under fanen Computere og** mobil. Med et hurtigt øjekast får du vist oplysninger som enhedsnavn, domæne, risikoniveau, eksponeringsniveau, OS-platform, onboardingstatus, sensortilstandstilstand og andre oplysninger, der gør det nemt at identificere de enheder, der er størst risiko forbundet med.

Brug kolonnen **Onboarding-status** til at sortere og filtrere efter enheder, der opdages, og dem, der allerede er onboardet Microsoft Defender for Endpoint.

![Billede af liste over enheder med liste over enheder.](images/device-inventory.png)

Fra **fanerne Netværksenheder** **og IoT-enheder** får du også vist oplysninger som leverandør, model og enhedstype:

![Billede af liste over netværksenheder.](images/device-inventory-networkdevices.png)

Øverst på hver lagerfane på enheden kan du se det samlede antal enheder, antallet af enheder, der endnu ikke er onboardet, og antallet af enheder, der er blevet identificeret som en større risiko for din organisation. Du kan bruge disse oplysninger som en hjælp til at prioritere enheder til sikkerhedsforbedringer.

Antallet **af nyopdagede** enheder for fanerne Netværksenheder og IoT-enheder viser antallet af nye enheder, der er fundet inden for de seneste 7 dage, i den aktuelle visning.

![Billede af antallet af nyopdagede enheder.](images/new-discovered-devices.png)

## <a name="explore-the-device-inventory"></a>Udforsk lager for enheder

Der er flere muligheder, du kan vælge mellem for at tilpasse lagervisningen for enheden. I den øverste navigationslinje for hver fane kan du:

- Søg efter en enhed efter navn
- Søg efter en enhed med præfikset for den senest anvendte IP-adresse eller IP-adresse
- Tilføj eller fjern kolonner
- Eksportér hele listen i CSV-format til offlineanalyse
- Vælg det datointerval, der skal vises
- Anvend filtre

> [!NOTE]
> Hvis du eksporterer enhedslisten, indeholder den alle enheder i organisationen. Det kan tage lang tid at downloade, afhængigt af hvor stor din organisation er. Hvis du eksporterer listen i CSV-format, vises dataene på en ufiltreret måde. CSV-filen inkluderer alle enheder i organisationen, uanset om der anvendes filtrering i selve visningen.

Du kan bruge funktionerne til sortering og filtrering, der er tilgængelige på hver fane for enhedslager, til at få en mere fokuseret visning og til at hjælpe dig med at vurdere og administrere enhederne i organisationen.

Optællingen øverst på hver fane opdateres baseret på den aktuelle visning.

## <a name="use-filters-to-customize-the-device-inventory-views"></a>Brug filtre til at tilpasse lagervisningerne for enheden

Filter | Beskrivelse
:---|:---
**Risikoniveau** </br> | Risikoniveauet afspejler den overordnede risikovurdering af enheden baseret på en kombination af faktorer, herunder typerne og alvorsgraderne af aktive beskeder på enheden. Løsning af aktive beskeder, godkendelse af afhjælpningsaktiviteter og undertrykke efterfølgende beskeder kan sænke risikoniveauet.
**Eksponeringsniveau** </br> | Eksponeringsniveauet afspejler enhedens aktuelle eksponering baseret på den kumulative effekt af dens afventende sikkerhedsanbefalinger. De mulige niveauer er lave, mellem og høje. Lav eksponering betyder, at dine enheder er mindre sårbar over for udnyttelse. </br> </br> Hvis eksponeringsniveauet siger "Ingen tilgængelige data", kan det være af forskellige årsager:</br>- Enheden holdt op med at rapportere i mere end 30 dage. I dette tilfælde betragtes den som inaktiv, og eksponeringen beregnes ikke.</br>- Enhedens operativsystem understøttes ikke - [se minimumskravene til Microsoft Defender for Endpoint](https://microsoft-my.sharepoint.com/personal/siosulli_microsoft_com/Documents/Security%20Posture/TVM/minimum-requirements.md).</br>- Enhed med forældet agent (usandsynligt).
**Mærker** </br> | Filtrer listen ud fra den gruppering og mærkning, du har føjet til individuelle enheder. Se [Opret og administrer enhedsmærker](machine-tags.md).
**Enhedsværdi**</br> | Filtrer listen ud fra, om enheden er markeret som høj værdi eller lav værdi.
**Udelukkelsestilstand** </br> | Filtrer listen ud fra, om enheden er blevet udeladt eller ej. Få mere at vide under [Udelad enheder](exclude-devices.md).
**OS-platform** </br>| Filtrer efter de OS-platforme, du er interesseret i at undersøge </br></br>(_Kun computere og mobilenheder og IoT-enheder_)
**Set første gang** </br> | Filtrer din visning ud fra, hvornår enheden blev set i netværket første gang, eller da den første gang blev rapporteret af Microsoft Defender for Endpoint sensoren.</br></br>(_Kun computere og mobilenheder og IoT-enheder_)
**Windows version** </br> | Filtrer efter Windows, du er interesseret i at undersøge.</br></br> (_Kun computere og mobil_)
**Tilstandstilstanden for sensoren** </br> | Filtrer efter følgende tilstande for sensorens tilstand for enheder i gang med Microsoft Defender for Endpoint:</br> - **Aktiv**: Enheder, der aktivt rapporterer sensordata til tjenesten.</br> - **Inaktiv**: Enheder, der har stoppet med at sende signaler i mere end 7 dage. </br> - **Forkert konfigureret**: Enheder, der har nedsat kommunikation med tjenesten, eller som ikke kan sende sensordata. </br> Forkert konfigurerede enheder kan klassificeres yderligere til: </br>  - Ingen sensordata </br>  - Forringet kommunikation </br>  Du kan finde flere oplysninger om, hvordan du løser problemer på forkert konfigurerede enheder under [Løse usunde sensorer](https://microsoft-my.sharepoint.com/personal/siosulli_microsoft_com/Documents/Security%20Posture/TVM/fix-unhealthy-sensors.md).</br></br> (_Kun computere og mobil_)
**Onboardingstatus** </br> | Onboardingstatus angiver, om enheden i øjeblikket er onboardet til Microsoft Defender for Endpoint eller ej. Du kan filtrere efter følgende tilstande: </br> - **Onboarded**: Slutpunktet er onboardet til Microsoft Defender for Endpoint.  </br> - **Kan onboardes**: Slutpunktet blev fundet i netværket som en understøttet enhed, men det er ikke i øjeblikket onboardet. Microsoft anbefaler kraftigt onboarding af disse enheder. </br> - **Ikke understøttet**: Slutpunktet blev fundet i netværket, men understøttes ikke af Microsoft Defender for Endpoint. </br> - **Utilstrækkelige oplysninger**: Systemet kunne ikke fastslå, om enheden understøttes.</br></br> (_Kun computere og mobil_)
**Antivirusstatus** </br> | Filtrer visningen ud fra, om antivirusstatus er deaktiveret, ikke opdateret eller ukendt.</br></br> (_Kun computere og mobil_)
**Gruppe** </br> | Filtrer listen ud fra den gruppe, du er interesseret i at undersøge. </br></br> (_Kun computere og mobil_)
**Administreres af** </br> | Administreres af angiver, hvordan enheden administreres. Du kan filtrere efter:</br>- Microsoft Defender for Endpoint </br> - Administration af mobilenheder (MDM) </br>- Ukendt: Dette kan skyldes, at der kører en forældet Windows version, SCCM er på plads eller en anden tredjeparts MDM.</br></br> (_Kun computere og mobil_)
**Enhedstype** </br> | Filtrer efter den enhedstype, du er interesseret i at undersøge.</br></br> (_Kun IoT-enheder_)

## <a name="use-columns-to-customize-the-device-inventory-views"></a>Brug kolonner til at tilpasse lagervisningerne for enheden

Du kan tilføje eller fjerne kolonner fra visningen og sortere posterne ved at klikke på en tilgængelig kolonneoverskrift.

På fanen **Computer og mobilenheder skal du** vælge Tilpas **kolonner for at få** vist de tilgængelige kolonner. Standardværdierne er markeret på billedet nedenfor:

![Billede af computere og mobilenheder](images/computerandmobilescolumns.png)

På fanen **Netværksenheder skal** du vælge Tilpas **kolonner for at** få vist de tilgængelige kolonner. Standardværdierne er markeret på billedet nedenfor:

![Billede af kolonner på netværksenhed](images/networkdevicescolumns.png)

På fanen **IoT-enheder skal** du vælge **Tilpas kolonner for at** få vist de tilgængelige kolonner. Standardværdierne er markeret på billedet nedenfor:

![Billede af kolonner til IoT-enheder](images/iotdevicescolumns.png)

## <a name="related-articles"></a>Relaterede artikler

[Undersøg enhederne Microsoft Defender for Endpoint listen Over enheder](investigate-machines.md)
