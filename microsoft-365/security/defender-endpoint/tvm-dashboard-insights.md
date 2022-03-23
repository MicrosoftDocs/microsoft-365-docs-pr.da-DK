---
title: Dashboardindsigt – Håndtering af trusler og sikkerhedsrisici
description: Dashboardet Håndtering af trusler og sikkerhedsrisici hjælpe SecOps og sikkerhedsadministratorer med at håndtere cybertrusler og opbygge deres organisations sikkerhedsrobusthed.
keywords: Microsoft Defender til Endpoint-tvm, Microsoft Defender til Endpoint-tvm-dashboard, trussel & håndtering af sikkerhedsrisici, Håndtering af trusler og sikkerhedsrisici, risikobaseret trussel & håndtering af sikkerhedsrisici , sikkerhedskonfiguration, Microsoft Secure Score til enheder, eksponeringsscore
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
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: fb93b179b9d342a4a0d098ddb889a94371fbabc4
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/09/2022
ms.locfileid: "63593792"
---
# <a name="dashboard-insights---threat-and-vulnerability-management"></a>Dashboardindsigt – Håndtering af trusler og sikkerhedsrisici

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Trussels- håndtering af sikkerhedsrisici er en komponent i Defender til slutpunkt og giver både sikkerhedsadministratorer og sikkerhedsteams unik værdi, herunder:

- Indsigter i realtid slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) korreleret med slutpunktsrisici
- Uvurderlig enhedssikkerhedsrisiko under hændelsesundersøgelse
- Indbyggede afhjælpningsprocesser gennem Microsoft Intune og Microsoft Endpoint Configuration Manager

Du kan bruge Håndtering af trusler og sikkerhedsrisici i portalen <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender til</a> at:

- Se din eksponeringsscore og Microsoft Secure Score til enheder sammen med de vigtigste sikkerhedsanbefalinger, softwaresikkerhedsrisiko, afhjælpningsaktiviteter og blotlagte enheder
- Korreler med Slutpunktsregistrering og -svar med slutpunktssårbarheder, og bearbejde dem
- Vælg afhjælpningsindstillinger for at triage og spore afhjælpningsopgaverne
- Vælge undtagelsesindstillinger og registrere aktive undtagelser

> [!NOTE]
> Enheder, der ikke er aktive inden for de seneste 30 dage, tages ikke med i de data, der afspejler din organisations Håndtering af trusler og sikkerhedsrisici eksponeringsscore og Microsoft Secure Score for enheder.

Se denne video for at få en hurtig oversigt over, hvad der er i Håndtering af trusler og sikkerhedsrisici dashboard.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4r1nv]

## <a name="threat-and-vulnerability-management-dashboard"></a>Trussels- håndtering af sikkerhedsrisici dashboard

:::image type="content" source="../../media/tvmdashboard.png" lightbox="../../media/tvmdashboard.png" alt-text="Dashboard til administration af trusler og sikkerhedsrisiko for enheder.":::

<br>

****

|Område|Beskrivelse|
|---|---|
|**Valgte enhedsgrupper (#/#)**|Filtrer Håndtering af trusler og sikkerhedsrisici data, du vil se i dashboardet og kort efter enhedsgrupper. Det, du vælger i filteret, gælder for alle Håndtering af trusler og sikkerhedsrisici sider.|
|[**Eksponeringsscore**](tvm-exposure-score.md)|Se den aktuelle tilstand for din organisations enheds eksponering for trusler og sårbarheder. Flere faktorer påvirker din organisations eksponeringsresultat: enheder, der opdages på dine enheder, sandsynligheden for, at dine enheder bliver brudt, enheders værdi for din organisation samt relevante beskeder, der opdages med dine enheder. Målet er at sænke eksponeringsresultatet for din organisation for at være mere sikker. For at reducere antallet af point skal du løse de relaterede sikkerhedskonfigurationsproblemer, der er angivet i sikkerhedsanbefalinger.|
|[**Microsoft Secure Score til enheder**](tvm-microsoft-secure-score-devices.md)|Se organisationens sikkerhedsfunktioner, operativsystem, programmer, netværk, konti og sikkerhedskontrolelementer. Målet er at løse de relaterede sikkerhedskonfigurationsproblemer for at øge din score for enheder. Når du vælger søjlerne, kommer du til **siden Sikkerhedsanbefaling** .|
|**Fordeling af enheds eksponering**|Se, hvor mange enheder der er eksponeret baseret på deres eksponeringsniveau. Vælg en sektion i kransediagrammet for at gå til  listesiden Enheder og få vist de påvirkede enhedsnavne, eksponeringsniveau, risikoniveau og andre oplysninger, f.eks. domæne, operativsystemplatform, tilstand, hvornår den sidst blev set samt dens mærker.|
|**Vigtigste sikkerhedsanbefalinger**|Se de sætvis sikkerhedsanbefalinger, der sorteres og prioriteres baseret på din organisations risiko eksponering og hvor meget det haster, som det kræver. Vælg **Vis mere** for at få vist resten af sikkerhedsanbefalinger på listen. Vælg **Vis undtagelser** for listen over anbefalinger, der har en undtagelse.|
|**Mest sårbar software**|Få indsigt i organisationens softwarelager i realtid med en liste over sårbar software, der er installeret på dit netværks enheder, og hvordan de påvirker din virksomheds eksponeringsscore. Vælg et element for at få flere **oplysninger eller** Vis mere for at få vist resten af listen over sårbar software på **siden Softwarelager** .|
|**Vigtigste afhjælpningsaktiviteter**|Spor afhjælpningsaktiviteterne, der genereres fra sikkerhedsanbefalinger. Du kan markere hvert element på listen for at få vist detaljerne på siden  Afhjælpning eller vælge Vis mere  for at få vist resten af afhjælpningsaktiviteterne og aktive undtagelser.|
|**Mest synlige enheder**|Få vist eksponerede enhedsnavne og deres eksponeringsniveau. Vælg et enhedsnavn på listen for at gå til siden enhed, hvor du kan se vigtige beskeder, risici, hændelser, sikkerhedsanbefalinger, installeret software og opdagede sårbarheder, der er knyttet til de eksponerede enheder. Vælg **Vis mere** for at se resten af listen over de eksponerede enheder. På listen over enheder kan du administrere mærker, starte automatiserede undersøgelser, starte en direkte svarsession, samle en undersøgelsespakke, køre antivirusscanning, begrænse udførelse af apps og isolere enheden.|
|

Du kan finde flere oplysninger om de ikoner, der bruges i hele [portalen, under Ikoner for Microsoft Defender til slutpunkt](portal-overview.md#microsoft-defender-for-endpoint-icons).

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over trusler håndtering af sikkerhedsrisici sikkerhed](next-gen-threat-and-vuln-mgt.md)
- [Eksponeringsscore](tvm-exposure-score.md)
- [Microsoft Secure Score til enheder](tvm-microsoft-secure-score-devices.md)
- [Sikkerhedsanbefalinger](tvm-security-recommendation.md)
- [Lager over software](tvm-software-inventory.md)
- [Begivenhedstidslinje](threat-and-vuln-mgt-event-timeline.md)
