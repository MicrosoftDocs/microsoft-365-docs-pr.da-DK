---
title: Nyheder i Microsoft 365 Defender
description: Viser de nye funktioner og funktionalitet i Microsoft 365 Defender
keywords: nyheder i Microsoft 365 Defender, ga, generelt tilgængelige, funktioner, tilgængelige, nye
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: edaa7398b8d3213479c9b81af248b928f7b3f3e0
ms.sourcegitcommit: f8267a0860de62dbd53ebb8a151a8e71a8ccda6a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/08/2022
ms.locfileid: "63593171"
---
# <a name="whats-new-in-microsoft-365-defender"></a>Nyheder i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

> Vil du gerne Microsoft 365 Defender? Du kan [evaluere det i et labmiljø](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) eller [køre dit pilotprojekt i produktion](m365d-pilot.md?ocid=cx-evalpilot).

Følgende funktioner er i forhåndsvisning eller generelt tilgængelige (GA) i den seneste version af Microsoft 365 Defender.

RSS-feed: Få besked, når denne side opdateres, ved at kopiere og indsætte følgende URL-adresse i din feedlæser:

```http
https://docs.microsoft.com/api/search/rss?search=%22Lists+the+new+features+and+functionality+in+Microsoft+365+defender%22&locale=en-us
```

Du kan finde flere oplysninger om nyheder i forbindelse med andre Microsoft Defender-sikkerhedsprodukter her:

- [Nyheder i Microsoft Defender til Office 365](../office-365-security/whats-new-in-defender-for-office-365.md)
- [Nyheder i Microsoft Defender til slutpunkt](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [Nyheder i Microsoft Defender for Identity](/defender-for-identity/whats-new)
- [Nyheder i Microsoft Defender til skyapps](/cloud-app-security/release-notes)

Du kan også få produktopdateringer og vigtige meddelelser via [meddelelsescenteret](https://admin.microsoft.com/Adminportal/Home#/MessageCenter). 

## <a name="december-2021"></a>December 2021

- (GA) Tabellen `DeviceTvmSoftwareEvidenceBeta` blev tilføjet på kort tid ved avanceret jagt for at give dig mulighed for at få vist beviser for, hvor en bestemt software blev registreret på en enhed.

## <a name="november-2021"></a>November 2021

- (Eksempel) Tilføjelsesprogrammet Programstyring til Defender for Cloud Apps er nu tilgængelig i Microsoft 365 Defender. Appstyring giver adgang til sikkerheds- og politikstyringsfunktionalitet, der er udviklet til OAuth-aktiverede apps, som Microsoft 365 adgang til data via Microsoft Graph API'er. Appstyring giver fuld synlighed, afhjælpning og styring i, hvordan disse apps og deres brugere får adgang til, bruger og deler dine følsomme data, der er gemt i Microsoft 365 via brugbar indsigt og automatiserede politikbeskeder og handlinger. [Få mere at vide om programstyring](/cloud-app-security/app-governance-manage-app-governance).
- (Eksempel) [Den avancerede](advanced-hunting-overview.md) jagtside har nu understøttelse af flere faner, intelligent rulning, strømlinede skemafaner, hurtige redigeringsindstillinger for forespørgsler, en indikator for brug af forespørgselsressourcer og andre forbedringer, der gør forespørgsler mere jævne og nemmere at finjustere.
- (Eksempel) Du kan nu bruge [linket](advanced-hunting-link-to-incident.md) til hændelsesfunktionen til at medtage hændelser eller poster fra de avancerede forespørgselsresultater direkte til en ny eller eksisterende hændelse, som du undersøger.

## <a name="october-2021"></a>Oktober 2021

- (GA) I avanceret jagt er der blevet tilføjet flere kolonner [i tabellen CloudAppEvents](advanced-hunting-cloudappevents-table.md) . Du kan nu `AccountType`medtage `IsExternalUser`, `IsImpersonated`, `IPTags`, `IPCategory`, og `UserAgentTags` til dine forespørgsler.

## <a name="september-2021"></a>September 2021

- (GA) Microsoft Defender for Office 365-hændelsesdata er tilgængelige i den Microsoft 365 Defender-hændelsesstreaming-API. Du kan se tilgængeligheden og status for hændelsestyper i de [understøttede Microsoft 365 Defender i streaming-API'en](supported-event-types.md).
- (GA) Microsoft Defender til Office 365 data, der er tilgængelige i avanceret jagt, er nu generelt tilgængelige.
- (GA) Tildel hændelser og beskeder til brugerkonti

  Du kan tildele en hændelse og alle de beskeder, der er knyttet til den, til en brugerkonto fra Tildel til **:** i  ruden Administrer hændelse for en hændelse eller ruden  Administrer beskeder for en besked.

## <a name="august-2021"></a>August 2021

- (Eksempel) Microsoft Defender til Office 365 data, der er tilgængelige i avanceret jagt

  Nye kolonner i mailtabeller kan give mere indsigt i mailbaserede trusler til mere grundige undersøgelser ved hjælp af avanceret jagt. Du kan nu medtage kolonnen `AuthenticationDetails` i [EmailEvents](./advanced-hunting-emailevents-table.md), `FileSize` [i EmailAttachmentInfo](./advanced-hunting-emailattachmentinfo-table.md)`ThreatTypes` `DetectionMethods` og i [tabellerne EmailPostDeliveryEvents](./advanced-hunting-emailpostdeliveryevents-table.md).

- (Eksempel) Graf over hændelser

  En ny **Graph** under fanen Oversigt over en hændelse  viser det fulde omfang af angrebene, hvordan angrebene spredte sig gennem dit netværk over tid, hvor det startede, og hvor langt hackeren er gået.

## <a name="july-2021"></a>Juli 2021

- [Katalog over professionelle tjenester](https://sip.security.microsoft.com/interoperability/professional_services)

  Gør registrering, undersøgelse og trusselsintelligens bedre for platformen med understøttede partnerforbindelser.

## <a name="june-2021"></a>Juni 2021

- (Eksempel) [Få vist rapporter pr. trusselsmærker](threat-analytics.md#view-reports-per-threat-tags)

  Trusselsmærker hjælper dig med at fokusere på bestemte trusselskategorier og gennemse de mest relevante rapporter.

- (Eksempel) [Streaming-API](../defender-endpoint/raw-data-export.md)

  Microsoft 365 Defender understøtter streaming af alle de hændelser, der er tilgængelige via Avanceret jagt på en Event Hubs og/eller Azure-lagerkonto.

- (Eksempel) [Tag skridtet videre i avanceret jagt](advanced-hunting-take-action.md)

  Indeholder hurtigt trusler eller adresserer kompromitterede aktiver, som du finder i [avanceret jagt](advanced-hunting-overview.md).

- (Eksempel) [Skemareference for portal](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)

  Få oplysninger om avancerede skematabeller direkte i sikkerhedscenteret. Ud over tabel- og kolonnebeskrivelser omfatter denne reference understøttede hændelsestyper (`ActionType` værdier) og eksempelforespørgsler.

- (Eksempel) [DeviceFromIP() function](advanced-hunting-devicefromip-function.md)

  Få oplysninger om, hvilke enheder der har fået tildelt en bestemt IP-adresse eller adresser i et givet tidsinterval.

## <a name="may-2021"></a>Maj 2021

- [Siden Ny besked i Microsoft 365 Defender portal](https://techcommunity.microsoft.com/t5/microsoft-365-defender/easily-find-anomalies-in-incidents-and-alerts/ba-p/2339243)

  Indeholder forbedrede oplysninger om konteksten i et angreb. Du kan se, hvilke andre udløste beskeder, der forårsagede den aktuelle besked og alle de berørte enheder og aktiviteter, der er involveret i angrebene, herunder filer, brugere og postkasser. Se [Undersøg beskeder for at](/microsoft-365/security/defender/investigate-alerts) få flere oplysninger.

- [Tendensdiagram over hændelser og beskeder i Microsoft 365 Defender-portalen](https://techcommunity.microsoft.com/t5/microsoft-365-defender/new-alert-page-for-microsoft-365-defender-incident-detections/ba-p/2350425)

  Afgør, om der er flere beskeder for en enkelt hændelse, eller om din organisation er under angreb med flere forskellige hændelser. Se [Prioriter hændelser for at](/microsoft-365/security/defender/incident-queue) få flere oplysninger.

## <a name="april-2021"></a>I april 2021

- Microsoft 365 Defender

  Den forbedrede [Microsoft 365 Defender](https://security.microsoft.com) portal er nu tilgængelig. Denne nye oplevelse samler Defender for Endpoint, Defender Office 365, Defender for Identity og meget mere i en enkelt portal. Dette er det nye hjem til at administrere dine sikkerhedskontrolelementer. [Få mere at vide om nyhederne](./microsoft-365-defender.md#the-microsoft-365-defender-portal).

- [Microsoft 365 Defender rapport over trusselsanalyse](threat-analytics.md)

  Trusselsanalyse hjælper dig med at reagere på og minimere effekten af aktive angreb. Du kan også få mere at vide om angrebsforsøg, der blokeres af Microsoft 365 Defender løsninger og udføre sikkerhedsforanstaltninger, der reducerer risikoen for yderligere eksponering og øger fleksibiliteten. Som en del af den samlede sikkerhedsoplevelse er trusselsanalyse nu tilgængelig for Microsoft Defender til slutpunkt og Microsoft Defender til Office E5-licensindehavere.

## <a name="march-2021"></a>Marts 2021

- [Tabellen CloudAppEvents](advanced-hunting-cloudappevents-table.md)

  Find oplysninger om begivenheder i forskellige skyapps og -tjenester, der er dækket Microsoft Cloud App Security. Denne tabel indeholder også oplysninger, der tidligere er tilgængelige i `AppFileEvents` tabellen.

## <a name="february-2021"></a>I februar 2021

- (Eksempel) Den forbedrede [Microsoft 365 Defender portal (https://security.microsoft.com)](https://security.microsoft.com) er nu tilgængelig i offentlig prøveversion. Denne nye oplevelse bringer Defender for Endpoint og Defender Office 365 direkte i midten. [Få mere at vide om, hvad der er ændret](microsoft-365-defender.md#the-microsoft-365-defender-portal).

- **[(Eksempel) Microsoft 365 Defender API'er](api-overview.md)** – API'er på øverste Microsoft 365 Defender gør det muligt at automatisere arbejdsprocesser baseret på den delte hændelse og avancerede søgetabeller.
