---
title: oversigt over Microsoft 365 Netværksforbindelse
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 08/27/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
f1.keywords:
- NOCSH
description: Her beskrives, hvorfor netværksoptimering er vigtig for SaaS-tjenester, målet om Microsoft 365 netværk, og hvordan SaaS kræver forskellige netværk fra andre arbejdsbelastninger.
ms.openlocfilehash: 64af558653ff57e91068d2e028235b73c165376b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096760"
---
# <a name="microsoft-365-network-connectivity-overview"></a>oversigt over Microsoft 365 netværksforbindelse

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Microsoft 365 er en saaS-cloud (Software-as-a-Service), der leverer produktivitets- og samarbejdsscenarier via en lang række mikrotjenester og -programmer. Klientkomponenter i Microsoft 365 f.eks. Outlook, Word og PowerPoint køre på brugercomputere og oprette forbindelse til andre komponenter i Microsoft 365, der kører i Microsoft-datacentre. Den vigtigste faktor, der bestemmer kvaliteten af den Microsoft 365 slutbrugeroplevelse, er netværkspålidelighed og lav ventetid mellem Microsoft 365 klienter og Microsoft 365 service front døre.

I denne artikel får du mere at vide om målene for Microsoft 365 netværk, og hvorfor Microsoft 365 netværk kræver en anden tilgang til optimering end generisk internettrafik.

## <a name="microsoft-365-networking-goals"></a>Microsoft 365 netværksmål

Det endelige mål med Microsoft 365 netværk er at optimere slutbrugeroplevelsen ved at aktivere den mindst restriktive adgang mellem klienter og de nærmeste Microsoft 365 slutpunkter. Kvaliteten af slutbrugeroplevelsen er direkte relateret til ydeevnen og svartid for det program, som brugeren bruger. Microsoft Teams er f.eks. afhængig af lav ventetid, så brugeropkald, konferencer og samarbejde på delt skærm er fejlfri, og Outlook er afhængig af fantastiske netværksforbindelser til hurtigsøgningsfunktioner, der anvender serverbaseret indeksering og AI-funktioner.

Det primære mål i netværksdesignet bør være at minimere ventetiden ved at reducere rundturstiden (RTT) fra klientcomputere til Microsoft Global Network, Microsofts offentlige netværks backbone, der forbinder alle Microsofts datacentre med lav ventetid og adgangspunkter for cloudprogrammer med høj tilgængelighed rundt om i verden. Du kan få mere at vide om Microsoft Global Network på [Sådan bygger Microsoft sit hurtige og pålidelige globale netværk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Optimering af Microsoft 365 netværksydeevne behøver ikke at være kompliceret. Du kan få den bedst mulige ydeevne ved at følge nogle få nøgleprincipper:

- Identificer Microsoft 365 netværkstrafik
- Tillad udgående lokal forgrening af Microsoft 365 netværkstrafik til internettet fra hver placering, hvor brugerne opretter forbindelse til Microsoft 365
- Tillad, at Microsoft 365 trafik tilsidesætter proxyer og pakkeinspektionsenheder

Du kan få flere oplysninger om principper for Microsoft 365 netværksforbindelser i [Microsoft 365 Principper for netværksforbindelse](microsoft-365-network-connectivity-principles.md).

## <a name="traditional-network-architectures-and-saas"></a>Traditionelle netværksarkitekturer og SaaS

Traditionelle principper for netværksarkitektur for klient-/serverarbejdsbelastninger er designet ud fra den antagelse, at trafikken mellem klienter og slutpunkter ikke udvides uden for virksomhedens netværksperimeter. I mange virksomhedsnetværk gennemgår alle udgående internetforbindelser også virksomhedens netværk og udgående data fra en central placering.

I traditionelle netværksarkitekturer er højere ventetid for generisk internettrafik en nødvendig konsekvens for at opretholde sikkerheden for netværksperimetre, og optimering af ydeevnen for internettrafik omfatter typisk opgradering eller udskalering af udstyr på netværksudgangspunkter. Denne fremgangsmåde imødekommer dog ikke kravene om optimal netværksydeevne for SaaS-tjenester, f.eks. Microsoft 365.

## <a name="identifying-microsoft-365-network-traffic"></a>Identificere Microsoft 365 netværkstrafik

Vi gør det nemmere at identificere Microsoft 365 netværkstrafik og gøre det nemmere at administrere netværksidentifikationen.

- Nye kategorier af netværksslutpunkter, der adskiller meget kritisk netværkstrafik fra netværkstrafik, der ikke påvirkes af internetventetider. Der er kun en håndfuld URL-adresser og understøttende IP-adresser i den mest kritiske kategori "Optimer".
- Webtjenester til scriptbrug eller direkte enhedskonfiguration og ændringsstyring af Microsoft 365 netværksidentifikation. Ændringer er tilgængelige fra webtjenesten eller i RSS-format eller via mail ved hjælp af en Microsoft Flow skabelon.
- [Office 365 Netværkspartnerprogram](./microsoft-365-networking-partner-program.md) med Microsoft-partnere, der leverer enheder eller tjenester, der følger Microsoft 365 principper for netværksforbindelse og har enkel konfiguration.

## <a name="securing-microsoft-365-connections"></a>Sikring af Microsoft 365 forbindelser

Målet med traditionel netværkssikkerhed er at hærde virksomhedens netværksperimeter mod indtrængen og ondsindede udnyttelser. De fleste virksomhedsnetværk gennemtvinger netværkssikkerhed for internettrafik ved hjælp af teknologier som proxyservere, firewalls, SSL-afbrydelse og -inspektion, dybpakkekontrol og systemer til forebyggelse af datatab. Disse teknologier giver en vigtig risikoafhjælpning for generiske internetanmodninger, men kan reducere ydeevnen, skalerbarheden og kvaliteten af slutbrugerens oplevelse væsentligt, når de anvendes på Microsoft 365 slutpunkter.

Microsoft 365 hjælper med at imødekomme organisationens behov for indholdssikkerhed og overholdelse af dataforbrug med indbyggede sikkerheds- og styringsfunktioner, der er udviklet specielt til Microsoft 365 funktioner og arbejdsbelastninger. Du kan få flere oplysninger om Microsoft 365 sikkerhed og overholdelse af angivne standarder i [oversigt over Office 365 sikkerhed](/office365/securitycompliance/security-roadmap). Du kan finde flere oplysninger om Microsofts anbefalinger og supportposition for avancerede netværksløsninger, der udfører behandling på Microsoft 365 trafik på avanceret niveau, under [Brug af netværksenheder eller løsninger fra tredjepart på Office 365 trafik](https://support.microsoft.com/help/2690045).

## <a name="why-is-microsoft-365-networking-different"></a>Hvorfor er Microsoft 365 netværk anderledes?

Microsoft 365 er udviklet til optimal ydeevne ved hjælp af slutpunktssikkerhed og krypterede netværksforbindelser, hvilket reducerer behovet for håndhævelse af perimetersikkerhed. Microsoft 365 datacentre er placeret over hele verden, og tjenesten er designet til at bruge forskellige metoder til at oprette forbindelse mellem klienter og de bedst tilgængelige tjenesteslutpunkter. Da brugerdata og -behandling distribueres mellem mange Microsoft-datacentre, er der ikke noget enkelt netværksslutpunkt, som klientcomputere kan oprette forbindelse til. Faktisk optimeres data og tjenester i din Microsoft 365 lejer dynamisk af Microsoft Global Network for at tilpasse sig de geografiske placeringer, hvorfra slutbrugerne tilgås dem.

Der opstår visse almindelige problemer med ydeevnen, når Microsoft 365 trafik er underlagt pakkekontrol og centraliseret udgående trafik:

- Høj ventetid kan medføre dårlig ydeevne for video- og lydstreams og langsom svar på datahentning, søgninger, samarbejde i realtid, oplysninger om ledig/optaget tid i kalenderen, indhold i produktet og andre tjenester
- Udgående forbindelser fra en central placering besejrer de dynamiske routingfunktioner i det Microsoft 365 globale netværk og tilføjer ventetid og rundturstid
- Dekryptering af SSL-sikret Microsoft 365 netværkstrafik og genkryptering af den kan medføre protokolfejl og udgør en sikkerhedsrisiko

Hvis netværksstien forkortes for at Microsoft 365 indgangspunkter ved at tillade klienttrafik at udgående data så tæt som muligt på deres geografiske placering, kan det forbedre forbindelsesydeevnen og slutbrugeroplevelsen i Microsoft 365. Det kan også hjælpe med at reducere virkningen af fremtidige ændringer af netværksarkitekturen på Microsoft 365 ydeevne og pålidelighed. Den optimale forbindelsesmodel er altid at give netværksafgang på brugerens placering, uanset om det er på virksomhedens netværk eller fjernplaceringer som f.eks. hjem, hoteller, kaffebarer og lufthavne. Generisk internettrafik og WAN-baseret firmanetværkstrafik distribueres separat og bruger ikke den lokale model for direkte udgående trafik. Denne lokale model for direkte udgående data er repræsenteret i diagrammet nedenfor.

![Arkitektur for lokalt udgående netværk.](../media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

Den lokale udgangsarkitektur har følgende fordele for Microsoft 365 netværkstrafik via den traditionelle model:
  
- Giver optimal Microsoft 365 ydeevne ved at optimere rutelængden. Slutbrugerforbindelser dirigeres dynamisk til det nærmeste Microsoft 365 indgangspunkt af Microsoft Global Network's _Distributed Service Front Door-infrastruktur_, og trafikken dirigeres derefter internt til data- og tjenesteslutpunkter over Microsofts fiber med høj ventetid med høj tilgængelighed.
- Reducerer belastningen på virksomhedens netværksinfrastruktur ved at tillade lokal udgående trafik for Microsoft 365 trafik, omgå proxyer og trafikkontrolenheder.
- Sikrer forbindelser i begge ender ved at anvende klientslutpunktsikkerhed og cloudsikkerhedsfunktioner, så du undgår anvendelse af redundante netværksteknologier.

> [!NOTE]
> _Front Door-infrastrukturen for distribuerede tjenester_ er Microsoft Global Network's yderst tilgængelige og skalerbare netværkskant med geografisk distribuerede placeringer. Den afslutter slutbrugerforbindelser og distribuerer dem effektivt inden for Microsoft Global Network. Du kan få mere at vide om Microsoft Global Network på [Sådan bygger Microsoft sit hurtige og pålidelige globale netværk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Du kan få flere oplysninger om, hvordan du forstår og anvender principper for Microsoft 365 netværksforbindelser, [under principper for Microsoft 365 Network Connectivity](microsoft-365-network-connectivity-principles.md).

## <a name="conclusion"></a>Konklusion

Optimering af Microsoft 365 netværksydeevnen kommer virkelig til at fjerne unødvendige hindringer. Ved at behandle Microsoft 365 forbindelser som trafik, der er tillid til, kan du forhindre, at ventetid introduceres af pakkeinspektion og konkurrence om proxybåndbredde. Hvis du tillader lokale forbindelser mellem klientcomputere og Office 365 slutpunkter, kan trafikken distribueres dynamisk via Microsoft Global Network.

## <a name="related-topics"></a>Relaterede emner

[principper for Microsoft 365 netværksforbindelser](microsoft-365-network-connectivity-principles.md)

[Administrere Office 365-slutpunkter](managing-office-365-endpoints.md)

[Office 365-URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md)

[Office 365 IP-adresse og URL-adressewebtjeneste](microsoft-365-ip-web-service.md)

[Vurderer Microsoft 365 netværksforbindelse](assessing-network-connectivity.md)

[Netværksplanlægning og justering af ydeevnen for Microsoft 365](network-planning-and-performance.md)

[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](performance-tuning-using-baselines-and-history.md)

[Plan for fejlfinding af ydeevnen for Office 365](performance-troubleshooting-plan.md)

[Netværk til levering af indhold](content-delivery-networks.md)

[Microsoft 365 forbindelsestest](https://aka.ms/netonboard)

[Sådan bygger Microsoft sit hurtige og pålidelige globale netværk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 netværksblog](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
