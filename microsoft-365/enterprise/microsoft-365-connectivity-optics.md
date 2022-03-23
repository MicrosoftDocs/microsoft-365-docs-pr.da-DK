---
title: Microsoft 365 Connectivity Optics
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Denne artikel indeholder oplysninger om Microsoft 365 Connectivity Optics.
ms.openlocfilehash: c1ee14966f13ff50ff809ebbdf4c578bf949e956
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63592479"
---
# <a name="microsoft-365-connectivity-optics"></a>Microsoft 365 Connectivity Optics

Dette dokument beskriver nogle af de forbindelsesoptiske funktioner, som Microsoft typisk indsamler fra kundeenheder, og beskriver nogle af de måder, som Microsoft bruger disse data til at analysere og optimere leveringen af tjenester og for at vurdere og sikre den bedst mulige slutbrugeroplevelse.

Forbindelsesoptics indsamles generelt fra Microsoft-programmer, som kan installeres på slutbrugerenheder eller åbnes fra browsere. I modsætning til valgfri dataindsamling inden for Microsoft 365-tjenester er mange af de forbindelsesoptik, der er beskrevet her, en integreret funktion, der sikrer, at Microsoft opfylder vores forpligtelse til tilgængelighed og ydeevne over for kunder. Disse optik gør det muligt for Microsoft hurtigt at registrere og reagere på eventuelle problemer i forbindelsesstien mellem slutbrugere og Microsoft-tjenesteslutpunkter. Nogle af disse optik bruges også til at aktivere funktioner som [f.eks. netværksforbindelse i Microsoft 365 Administration Center](office-365-network-mac-perf-overview.md).

## <a name="optics-collected-from-microsoft-365-applications"></a>Optics, der er indsamlet Microsoft 365 programmer

Optics indsamles i øjeblikket ved hjælp af sjældne stikprøver på tværs af alle enheder. Generelt set konfigureres det specifikke sæt optics og destinationer (tjenesteslutpunkter), som skal måles i en bestemt iteration, af Microsoft ud fra tjenestekrav og tilfældigt til stikprøveformål.
Ved hvert optiksamlingsinterval kan en eller flere af følgende målinger indsamles ved hjælp af slutbrugerenheden som målekilde, og Microsoft 365-tjenesteslutpunkt som målepunkt:

| Mål | Beskrivelse |
| --- | --- |
| Ventetid | Den tid, det tager at hente en lille fil via HTTP |
| Overførselshastighed | Den tid, det tager at hente en større fil via HTTP, måles sjældent for at undgå overdreven båndbreddeforbrug |
| Tiden på returkørslen (RTT) | ICMP ping |
| Traceroute | ICMP-traceroute |

Hver måling er typisk knyttet til yderligere oplysninger, som kan omfatte følgende elementer:

| Element | Beskrivelse |
| --- | --- |
| Lejer-id | Entydigt id for kundens Azure Active Directory, der er knyttet til slutbrugerenheden. |
| Skærm-id | Id for det program, der genererer anmodningen (f.eks. Outlook, OneDrive osv.), leveret af det klientprogram, der udfører målingen. |
| Anmod om id | Identifikator for anmodningen om måling, som er angivet i den målingskonfiguration, der leveres af Microsoft. |
| Fjern-IP | Maskeret kilde-IP, der er knyttet til anmodningen fra klient til tjenesteslutpunkt, leveres af den server, der modtog måleanmodningen og beregnede baseret på klientkilde-IP-adressen, der er synlig for Microsoft. IP-adresser er maskeret til et /24-undernet til IPv4-adresser eller et /48-undernet til IPv6-adresser for at sikre, at Microsoft ikke kan identificere individuelle enheder eller brugere. |
| Front end | Microsoft 365 tjeneste front end-id, leveret af den server, der modtog anmodningen om måling. |
| Slutpunkt | Microsoft 365 tjenesteslutpunktplacering, der leveres af den server, der modtog anmodningen om måling. |
| Certifikat udstedt af | Egenskaben "certifikat udstedt af" for det SSL-certifikat, der præsenteres under oprettelse af forbindelse til tjenesteslutpunktet, hvilket angiver det nøglecenter, der udstedte certifikatet til tjenestens slutpunkt. |
| Certificate Thumbprint | Egenskaben "certificate thumbprint" for det SSL-certifikat, der præsenteres, når du opretter forbindelse til tjenesteslutpunktet, som er en offentligt tilgængelig entydig identifier for certifikatet. |
| Længde-/breddegrader | Den abstrakte bredde- og længdegrad for slutbrugerenheden. Dette indsamles kun for lejere, der har aktiveret Windows-placeringstjeneste på slutbrugerenheder og også har aktiveret indsamling af disse oplysninger [i Microsoft 365-administrationsportalen](office-365-network-mac-perf-overview.md#1-enable-windows-location-services). |

## <a name="measurement-process"></a>Måleproces

Hver slutbrugerenhed udfører typisk en måling enten på planlagt basis (for installerede programmer) eller baseret på handlingen for indlæsning af browsersider (for webbaserede programmer). Måleaktiviteter udføres som baggrundshandlinger og påvirker ikke programoplevelsen for brugerne. Da de måletyper og destinationer, der skal bruges til en bestemt iteration af denne proces, er randomiserede, vil kunderne muligvis bemærke anmodninger til Microsoft-tjenesteslutpunkter i deres område, der svarer til de typiske anmodninger fra slutbrugerenheder om normal applikationsforbindelse. Desuden vil kunder muligvis lægge mærke til anmodninger til Microsoft-tjenesteslutpunkter, der ligger et godt sted uden for deres område. Disse målinger bruges ofte til at sikre optimal routing af kundeanmodninger til det bedste tjenesteslutpunkt, da ændringer i kundens og internetudbyderens infrastruktur muligvis kræver, at Microsoft løbende ændrer vores omdirigeringspolitikker for anmodninger. Få mere at vide om, hvordan Microsoft routes trafik til det bedste tjenesteslutpunkt, og hvordan du optimerer forbindelse til Microsoft 365-tjenester [i oversigten Microsoft 365 netværksforbindelse](microsoft-365-networking-overview.md).

## <a name="service-endpoints"></a>Tjenesteslutpunkter

Microsoft-tjenesteslutpunkterne, der bruges som destinationer til disse mål, er indeholdt i de publicerede [Office 365 URL- og IP-adresseområder](urls-and-ip-address-ranges.md). Adgang til yderligere tjenesteslutpunkter er ikke nødvendige for samlingen af disse forbindelsesoptik.
