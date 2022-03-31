---
title: Microsoft 365 over netværksforbindelse
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Diskuterer, hvorfor netværksoptimering er vigtigt for SaaS-tjenester, formålet med at Microsoft 365 netværk, og hvordan SaaS kræver forskellige netværksmuligheder fra andre arbejdsbelastninger.
ms.openlocfilehash: e5dcbae5a1fbac3b0b4fd4472fdcac2380b84382
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63601581"
---
# <a name="microsoft-365-network-connectivity-overview"></a>Microsoft 365 over netværksforbindelse

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Microsoft 365 er en distribueret Software-as-a-Service (SaaS)-sky, der leverer produktivitets- og samarbejdsscenarier gennem et varieret sæt mikrotjenester og programmer. Klientkomponenter af Microsoft 365 f.eks. Outlook, Word og PowerPoint kører på brugercomputere og opretter forbindelse til andre komponenter i Microsoft 365, der kører i Microsoft-datacentre. Den mest betydningsfulde faktor, der bestemmer kvaliteten af Microsoft 365-slutbrugeroplevelsen, er netværkspålidelighed og lav latenstid mellem Microsoft 365-klienter og Microsoft 365 forside døre.

I denne artikel får du mere at vide om målene med Microsoft 365-netværk, og hvorfor Microsoft 365-netværk kræver en anden tilgang til optimering end generisk internettrafik.

## <a name="microsoft-365-networking-goals"></a>Microsoft 365 med at netværke mål

Det ultimative mål med Microsoft 365 netværk er at optimere slutbrugeroplevelsen ved at give den mindst restriktive adgang mellem klienter og de Microsoft 365 slutpunkter. Kvaliteten af slutbrugeroplevelsen er direkte relateret til ydeevnen og svarigheden i det program, brugeren bruger. Eksempelvis er Microsoft Teams afhængig af lav ventetid, så brugernes telefonopkald, telefonmøder og delte skærmsamarbejder er problemfrie, og Outlook afhænger af gode netværksforbindelser til funktioner til hurtigsøgning, der anvender indeksering og AI-funktioner på serversiden.

Det primære mål i netværksdesignet bør være at minimere ventetiden ved at reducere tiden for returkørslen (RTT) fra klientcomputere til Microsoft Global Network, Microsofts offentlige netværkssten, der indbyrdes forbinder alle Microsofts datacentre med indgangspunkter med lav latenstid og høj tilgængelighed i skyen over hele verden. Du kan få mere at vide om Microsoft Global Network [på Sådan opbygger Microsoft sit hurtige og pålidelige globale netværk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Optimering Microsoft 365 netværkets ydeevne behøver ikke at være kompliceret. Du kan opnå den bedst mulige ydeevne ved at følge nogle få vigtige principper:

- Identificer Microsoft 365 netværkstrafik
- Tillad lokal afdelings udgangspunkt for Microsoft 365 til internettet fra hver placering, hvor brugerne opretter forbindelse til Microsoft 365
- Tillad Microsoft 365 trafik til at tilsidesætte proxyer og pakkeinspektionsenheder

Du kan finde flere Microsoft 365 om principperne for netværksforbindelse under [Microsoft 365 principper for netværksforbindelse](microsoft-365-network-connectivity-principles.md).

## <a name="traditional-network-architectures-and-saas"></a>Traditionelle netværksarkitekturer og SaaS

Traditionelle principper for netværksarkitektur for klient-/server-arbejdsbelastninger er designet ud fra den forudsætning, at trafik mellem klienter og slutpunkter ikke går uden for virksomhedens netværksperimeter. I mange virksomhedsnetværk krydser alle udgående internetforbindelser desuden virksomhedens netværk og udgangspunkt fra en central placering.

I traditionelle netværksarkitekturer er højere ventetid for generisk internettrafik en nødvendig kompromis for at bevare netværkets perimetersikkerhed, og optimering af ydeevnen for internettrafik indebærer typisk opgradering eller skalering af udstyret på netværks udgangspunkter. Denne fremgangsmåde imødekommer dog ikke kravene til optimal netværksydeevne for SaaS-tjenester som f.eks Microsoft 365.

## <a name="identifying-microsoft-365-network-traffic"></a>Identificere Microsoft 365 netværkstrafik

Vi gør det nemmere at identificere netværkstrafik Microsoft 365 nemmere at administrere netværksidentifikationen.

- Nye kategorier af netværksslutpunkter til at skelne meget kritisk netværkstrafik fra netværkstrafik, der ikke påvirkes af internet latender. Der er blot en håndfuld URL-adresser og understøttelse af IP-adresser i den mest kritiske kategori "Optimer".
- Webtjenester til scriptbrug eller direkte enhedskonfiguration og ændringsstyring af Microsoft 365 af netværksidentifikation. Ændringer er tilgængelige fra webtjenesten, i RSS-format eller i mails ved hjælp af en Microsoft Flow skabelon.
- [Office 365 netværkspartnerprogram med](./microsoft-365-networking-partner-program.md) Microsoft-partnere, der leverer enheder eller tjenester, der Microsoft 365 principperne for netværksforbindelse og har enkel konfiguration.

## <a name="securing-microsoft-365-connections"></a>Sikring Microsoft 365 forbindelser

Formålet med traditionel netværkssikkerhed er at skærpe virksomhedens netværksperimeter mod indtrængen og ondsindede udnyttelser. De fleste virksomhedsnetværk gennemtvinger netværkssikkerhed for internettrafik ved hjælp af teknologier som proxyservere, firewalls, SSL-pause og -undersøgelse, omfattende pakkeinspektion og systemer til forebyggelse af datatab. Disse teknologier giver vigtig risiko mod afhjælpning i forbindelse med generiske internetanmodninger, men kan markant reducere ydeevnen, skalerbarheden og kvaliteten af slutbrugeroplevelsen, når de anvendes på Microsoft 365 slutpunkter.

Microsoft 365 hjælper med at opfylde organisationens behov for indholdssikkerhed og overholdelse af dataforbrug med indbyggede sikkerheds- og styringsfunktioner, der er designet specielt til Microsoft 365 funktioner og arbejdsbelastninger. Du kan finde flere Microsoft 365 om sikkerhed og overholdelse af regler og Office 365 [i oversigten over sikkerhed og sikkerhed](/office365/securitycompliance/security-roadmap). Du kan finde flere oplysninger om Microsofts anbefalinger og supportplacering til avancerede netværksløsninger, der udfører avanceret behandling på Microsoft 365-trafik, under Brug af tredjepartsnetværksenheder eller løsninger [på Office 365 trafik](https://support.microsoft.com/help/2690045).

## <a name="why-is-microsoft-365-networking-different"></a>Hvorfor er Microsoft 365 netværk anderledes?

Microsoft 365 er udviklet til optimal ydeevne ved hjælp af slutpunktssikkerhed og krypterede netværksforbindelser, hvilket reducerer behovet for håndhævelse af perimetersikkerhed. Microsoft 365 datacentre er placeret over hele verden, og tjenesten er designet til at bruge forskellige metoder til at forbinde klienter til de bedst tilgængelige tjenesteslutpunkter. Da brugerdata og -behandling fordeles mellem mange Microsoft-datacentre, er der ikke noget enkelt netværksslutpunkt, som klientcomputere kan oprette forbindelse til. Faktisk optimeres data og tjenester i din Microsoft 365-lejer dynamisk af Microsoft Global Network til at tilpasse sig de geografiske placeringer, hvorfra de tilgås af slutbrugere.

Visse almindelige problemer med ydeevnen opstår, når Microsoft 365 er underlagt pakkeinspektion og centraliseret udgangspunkt:

- Høj ventetid kan medføre dårlig ydeevne for video- og lydstreams, og langsom svartid for hentning af data, søgninger, samarbejde i realtid, oplysninger om ledig/optaget i kalenderen, indhold i produktet og andre tjenester
- Udgangsforbindelser fra en central placering overser de dynamiske routingegenskaber fra det globale Microsoft 365, hvilket tilføjer ventetid og returtid
- Dekryptering af SSL-Microsoft 365 og netværkstrafik og genkryptering kan medføre protokolfejl og har sikkerhedsrisiko

Afkortning af netværksstien til Microsoft 365 indgangspunkter ved at tillade klienttrafik at gå ud fra et udgangspunkt så tæt som muligt på deres geografiske placering kan forbedre forbindelsesydeevnen og slutbrugeroplevelsen i Microsoft 365. Det kan også hjælpe med at reducere effekten af fremtidige ændringer af netværksarkitekturen på Microsoft 365 ydeevne og pålidelighed. Den optimale forbindelsesmodel er altid at angive et netværksud udgangspunkt på brugerens placering, uanset om det ligger på virksomhedens netværk eller på en fjernplacering, f.eks. private, cafeer og lufthavne. Generisk internettrafik og WAN-baseret virksomhedsnetværkstrafik distribueres separat og bruger ikke den lokale direkte udgangspunktsmodel. Denne lokale direkte udgangspunktsmodel er repræsenteret i nedenstående diagram.

![Lokal udgangsnetværksarkitektur.](../media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

Den lokale udgangsarkitektur har følgende fordele ved at Microsoft 365 netværkstrafik i forhold til den traditionelle model:
  
- Giver optimal Microsoft 365 ved at optimere rutelængden. Slutbrugerforbindelser dirigeres dynamisk til det nærmeste Microsoft 365-indgangspunkt af Microsoft Global Network's _Distributed Service Front Door-infrastruktur_, og trafik dirigeres derefter internt til data- og tjenesteslutpunkter over Microsofts ultra lave tilgængeligheds fiber.
- Reducerer belastningen på virksomhedens netværksinfrastruktur ved at tillade lokale Microsoft 365 trafik, tilsidesætte proxyer og trafikinspektionsenheder.
- Sikrer forbindelser i begge ender ved at anvende klientslutpunktsikkerhed og skysikkerhedsfunktioner, så du undgår anvendelse af redundante netværksikkerhedsteknologier.

> [!NOTE]
> Distributed _Service Front Door_ infrastructure er Microsoft Global Network's meget tilgængelige og skalerbare netværkskant med geografisk distribuerede placeringer. Det afslutter slutbrugerforbindelser og sender dem effektivt inden for Microsoft Global Network. Du kan få mere at vide om Microsoft Global Network [på Sådan opbygger Microsoft sit hurtige og pålidelige globale netværk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Du kan finde flere oplysninger om at forstå og Microsoft 365 principper for netværksforbindelse i [Microsoft 365 Network Connectivity Principles](microsoft-365-network-connectivity-principles.md).

## <a name="conclusion"></a>Konklusion

Optimering Microsoft 365 af netværksydeevnen er i virkeligheden ned til at fjerne unødvendige hindringer. Ved at behandle Microsoft 365 som pålidelig trafik, kan du forhindre ventetid i at blive introduceret af pakkeinspektion og konkurrence om proxybåndbredde. Hvis du tillader lokale forbindelser mellem klientcomputere og Office 365-slutpunkter, kan trafik dirigeres dynamisk gennem Microsofts globale netværk.

## <a name="related-topics"></a>Relaterede emner

[Microsoft 365 principper for netværksforbindelse](microsoft-365-network-connectivity-principles.md)

[Administrere Office 365 slutpunkter](managing-office-365-endpoints.md)

[Office 365-URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md)

[Office 365 IP-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md)

[Vurdering Microsoft 365 af netværksforbindelsen](assessing-network-connectivity.md)

[Netværksplanlægning og justering af ydeevnen for Microsoft 365](network-planning-and-performance.md)

[Office 365 justering af ydeevnen ved hjælp af grundlinjer og ydeevnehistorik](performance-tuning-using-baselines-and-history.md)

[Fejlfinding af ydeevne i forbindelse med planen for Office 365](performance-troubleshooting-plan.md)

[Content Delivery Networks](content-delivery-networks.md)

[Microsoft 365 forbindelsestest](https://aka.ms/netonboard)

[Sådan opbygger Microsoft sit hurtige og pålidelige globale netværk](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 Networking-blog](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
