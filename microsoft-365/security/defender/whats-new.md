---
title: Nyheder i Microsoft 365 Defender
description: Viser de nye funktioner og funktioner i Microsoft 365 Defender
keywords: nyheder i Microsoft 365 Defender, ga, offentligt tilgængelig, funktioner, tilgængelige, nye
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
ms.openlocfilehash: ed3d06e1719b51d0914c89e6283c8b53c2ab0812
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530504"
---
# <a name="whats-new-in-microsoft-365-defender"></a>Nyheder i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Viser de nye funktioner og funktioner i Microsoft 365 Defender. 

RSS-feed: Få besked, når denne side opdateres, ved at kopiere og indsætte følgende URL-adresse i din feedlæser:

```http
https://docs.microsoft.com/api/search/rss?search=%22Lists+the+new+features+and+functionality+in+Microsoft+365+defender%22&locale=en-us
```

Du kan få flere oplysninger om nyheder i andre Microsoft Defender-sikkerhedsprodukter under:

- [Nyheder i Microsoft Defender for Office 365](../office-365-security/whats-new-in-defender-for-office-365.md)
- [Nyheder i Microsoft Defender for Endpoint](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [Nyheder i Microsoft Defender for Identity](/defender-for-identity/whats-new)
- [Nyheder i Microsoft Defender for Cloud Apps](/cloud-app-security/release-notes)

Du kan også få produktopdateringer og vigtige meddelelser via [meddelelsescenteret](https://admin.microsoft.com/Adminportal/Home#/MessageCenter). 

## <a name="june-2022"></a>Juni 2022
- (eksempelvisning) Tabellerne [DeviceTvmInfoGathering](advanced-hunting-devicetvminfogathering-table.md) og [DeviceTvmInfoGatheringKB](advanced-hunting-devicetvminfogatheringkb-table.md) er nu tilgængelige i det avancerede jagtskema. Brug disse tabeller til at jage gennem vurderingshændelser i Defender Vulnerability Management, herunder status for forskellige konfigurationer og enheders tilstande for angrebsoverfladen.

## <a name="may-2022"></a>Maj 2022
- (eksempelvisning) I overensstemmelse med den nyligt annoncerede udvidelse til en ny tjenestekategori kaldet [Microsoft Security Experts](https://aka.ms/MicrosoftSecurityExperts) introducerer vi tilgængeligheden af [Microsoft Defender Experts for Hunting](defenderexpertsforhuntingprev.md) (Defender Experts for Hunting) til offentlig prøveversion. Defender Experts for Hunting er til kunder, der har et robust center for sikkerhedshandlinger, men som gerne vil have Microsoft til proaktivt at jage efter trusler på tværs af Microsoft Defender-data, herunder slutpunkter, Office 365, cloudprogrammer og identitet. 

## <a name="april-2022"></a>April 2022
- (eksempelvisning) [Handlinger](advanced-hunting-take-action.md) kan nu udføres på mails direkte fra resultaterne af jagtforespørgslen. Mails kan flyttes til andre mapper eller slettes permanent. 
- (eksempelvisning) Den nye [`UrlClickEvents` tabel](advanced-hunting-urlclickevents-table.md) i avanceret jagt kan bruges til at jage efter trusler som phishing-kampagner og mistænkelige links baseret på oplysninger, der kommer fra klik på sikre links i mails, Microsoft Teams og Office 365 apps.

## <a name="march-2022"></a>Marts 2022

- (eksempelvisning) Hændelseskøen er blevet forbedret med flere funktioner, der er designet til at hjælpe dine undersøgelser. Forbedringer omfatter funktioner som f.eks. mulighed for at søge efter hændelser efter id eller navn, angive et brugerdefineret tidsinterval og andre.


## <a name="december-2021"></a>December 2021

- (GA) Tabellen `DeviceTvmSoftwareEvidenceBeta` blev tilføjet på kort sigt i avanceret jagt for at give dig mulighed for at se beviser på, hvor en bestemt software blev registreret på en enhed.

## <a name="november-2021"></a>November 2021

- (eksempelvisning) Tilføjelsesprogrammet programstyring til Defender for Cloud Apps er nu tilgængeligt i Microsoft 365 Defender. Appstyring indeholder en funktionalitet til administration af sikkerhed og politik, der er udviklet til OAuth-aktiverede apps, der har adgang til Microsoft 365-data via Microsoft Graph-API'er. Appstyring giver fuld synlighed, afhjælpning og styring af, hvordan disse apps og deres brugere får adgang til, bruger og deler dine følsomme data, der er gemt i Microsoft 365, via handlingsbaseret indsigt og automatiserede politikbeskeder og handlinger. [Få mere at vide om programstyring](/cloud-app-security/app-governance-manage-app-governance).
- (eksempelvisning) Den [avancerede jagtside](advanced-hunting-overview.md) understøtter nu flere faner, smart rulning, strømlinede skemafaner, indstillinger for hurtig redigering af forespørgsler, en indikator for ressourceforbrug for forespørgsler og andre forbedringer for at gøre forespørgslerne mere jævne og nemmere at finjustere.
- (eksempelvisning) Du kan nu bruge [funktionen link til hændelse](advanced-hunting-link-to-incident.md) til at inkludere hændelser eller poster fra de avancerede resultater af jagtforespørgslen direkte i en ny eller eksisterende hændelse, som du er ved at undersøge.

## <a name="october-2021"></a>Oktober 2021

- (GA) I avanceret jagt blev der tilføjet flere kolonner i tabellen [CloudAppEvents](advanced-hunting-cloudappevents-table.md) . Du kan nu inkludere `AccountType`, `IsExternalUser`, `IsImpersonated`, `IPTags`, `IPCategory`og `UserAgentTags` i dine forespørgsler.

## <a name="september-2021"></a>September 2021

- (GA) Microsoft Defender for Office 365 hændelsesdata er tilgængelige i API'en til Microsoft 365 Defender hændelsesstreaming. Du kan se tilgængeligheden og status for [hændelsestyper i Understøttede Microsoft 365 Defender hændelsestyper i streaming-API'en](supported-event-types.md).
- (GA) Microsoft Defender for Office 365 data, der er tilgængelige inden for avanceret jagt, er nu offentligt tilgængelige.
- (GA) Tildel hændelser og beskeder til brugerkonti

  Du kan tildele en hændelse og alle de beskeder, der er knyttet til den, til en brugerkonto fra **Tildel til:** i ruden **Administrer hændelse** for en hændelse eller ruden **Administrer besked** for en besked.

## <a name="august-2021"></a>August 2021

- (eksempelvisning) Microsoft Defender for Office 365 data, der er tilgængelige i avanceret jagt

  Nye kolonner i mailtabeller kan give mere indsigt i mailbaserede trusler for at få mere grundige undersøgelser ved hjælp af avanceret jagt. Du kan nu inkludere kolonnen `AuthenticationDetails` i [EmailEvents](./advanced-hunting-emailevents-table.md), `FileSize` i [EmailAttachmentInfo](./advanced-hunting-emailattachmentinfo-table.md) og `ThreatTypes` `DetectionMethods` i tabellerne [EmailPostDeliveryEvents](./advanced-hunting-emailpostdeliveryevents-table.md) .

- (eksempelvisning) Hændelsesgraf

  En ny **Graph-fane** under fanen **Oversigt** i en hændelse viser det fulde omfang af angrebet, hvordan angrebet spredte sig gennem dit netværk over tid, hvor det startede, og hvor langt angriberen gik.

## <a name="july-2021"></a>Juli 2021

- [Katalog over professionelle tjenester](https://sip.security.microsoft.com/interoperability/professional_services)

  Gør platformens registrering, undersøgelse og trusselsintelligens bedre med understøttede partnerforbindelser.

## <a name="june-2021"></a>Juni 2021

- (eksempelvisning) [Få vist rapporter pr. trusselstags](threat-analytics.md#view-reports-per-threat-tags)

  Trusselstags hjælper dig med at fokusere på specifikke trusselskategorier og gennemse de mest relevante rapporter.

- (eksempelvisning) [Streaming-API](../defender-endpoint/raw-data-export.md)

  Microsoft 365 Defender understøtter streaming af alle de hændelser, der er tilgængelige via Advanced Hunting, til en Event Hubs- og/eller Azure Storage-konto.

- (eksempelvisning) [Handle i avanceret jagt](advanced-hunting-take-action.md)

  Hurtigt indeholde trusler eller løse kompromitterede aktiver, som du finder i [avanceret jagt](advanced-hunting-overview.md).

- (eksempelvisning) [Skemareference i portalen](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)

  Få oplysninger om avancerede jagtskematabeller direkte i Security Center. Ud over beskrivelser af tabeller og kolonner indeholder denne reference understøttede hændelsestyper (`ActionType` værdier) og eksempelforespørgsler.

- (eksempelvisning) [Funktionen DeviceFromIP()](advanced-hunting-devicefromip-function.md)

  Få oplysninger om, hvilke enheder der er blevet tildelt en bestemt IP-adresse eller -adresser inden for et bestemt tidsinterval.

## <a name="may-2021"></a>Maj 2021

- [Ny beskedside på Microsoft 365 Defender-portalen](https://techcommunity.microsoft.com/t5/microsoft-365-defender/easily-find-anomalies-in-incidents-and-alerts/ba-p/2339243)

  Indeholder forbedrede oplysninger om konteksten i et angreb. Du kan se, hvilke andre udløste beskeder der forårsagede den aktuelle besked, og alle de berørte enheder og aktiviteter, der er involveret i angrebet, herunder filer, brugere og postkasser. Se [Undersøg beskeder](/microsoft-365/security/defender/investigate-alerts) for at få flere oplysninger.

- [Tendensgraf for hændelser og beskeder på Microsoft 365 Defender-portalen](https://techcommunity.microsoft.com/t5/microsoft-365-defender/new-alert-page-for-microsoft-365-defender-incident-detections/ba-p/2350425)

  Find ud af, om der er flere beskeder for en enkelt hændelse, eller om din organisation er under angreb med flere forskellige hændelser. Se [Prioriter hændelser](/microsoft-365/security/defender/incident-queue) for at få flere oplysninger.

## <a name="april-2021"></a>I april 2021

- Microsoft 365 Defender

  Den forbedrede [Microsoft 365 Defender-portal](https://security.microsoft.com) er nu tilgængelig. Denne nye oplevelse samler Defender for Endpoint, Defender for Office 365, Defender for Identity og meget mere i en enkelt portal. Dette er det nye hjem, hvor du kan administrere dine sikkerhedskontrolelementer. [Få mere at vide om nyheder](./microsoft-365-defender.md#the-microsoft-365-defender-portal).

- [rapport over Microsoft 365 Defender trusselsanalyse](threat-analytics.md)

  Trusselsanalyser hjælper dig med at reagere på og minimere virkningen af aktive angreb. Du kan også få mere at vide om angrebsforsøg, der er blokeret af Microsoft 365 Defender løsninger, og træffe forebyggende foranstaltninger, der afhjælper risikoen for yderligere eksponering og øger robusthed. Som en del af den samlede sikkerhedsoplevelse er trusselsanalyse nu tilgængelig for licensindehavere af Microsoft Defender for Endpoint og Microsoft Defender for Office E5.

## <a name="march-2021"></a>Marts 2021

- [Tabellen CloudAppEvents](advanced-hunting-cloudappevents-table.md)

  Find oplysninger om hændelser i forskellige cloudapps og -tjenester, der er omfattet af Microsoft Cloud App Security. Denne tabel indeholder også oplysninger, der tidligere er tilgængelige i tabellen `AppFileEvents` .

