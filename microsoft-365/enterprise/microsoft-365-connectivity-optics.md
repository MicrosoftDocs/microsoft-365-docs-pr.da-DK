---
title: optik i forbindelse med Microsoft 365 forbindelse
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
ms.openlocfilehash: cda5fa074aa04be5fbbaff9b98360a3a2f927fc2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090313"
---
# <a name="microsoft-365-connectivity-optics"></a>optik i forbindelse med Microsoft 365 forbindelse

I dette dokument beskrives nogle af de forbindelsesmuligheder, Som Microsoft typisk indsamler fra kundeenheder, og beskriver nogle af de måder, hvorpå Microsoft bruger disse data til at analysere og optimere levering af tjenester og til at vurdere og sikre den bedst mulige slutbrugeroplevelse.

Forbindelsesoptik indsamles generelt fra Microsoft-programmer, som kan installeres på slutbrugerenheder eller åbnes fra browsere. I modsætning til valgfri dataindsamling i Microsoft 365-tjenester er mange af de forbindelsesmuligheder, der er beskrevet her, en integreret del af at sikre, at Microsoft opfylder vores forpligtelse til tilgængelighed og ydeevne for kunder. Disse optik gør det muligt for Microsoft hurtigt at registrere og reagere på eventuelle problemer i forbindelsesstien mellem slutbrugere og Microsoft-tjenesteslutpunkter. Nogle af disse optik bruges også til at aktivere funktioner som [netværksforbindelse i Microsoft 365 Administration Center](office-365-network-mac-perf-overview.md).

## <a name="optics-collected-from-microsoft-365-applications"></a>Optik, der indsamles fra Microsoft 365 programmer

Optik indsamles i øjeblikket ved hjælp af sjældne udsnit på tværs af alle enheder. Generelt er det specifikke sæt optik og destinationer (tjenesteslutpunkter), der skal måles i en bestemt gentagelse, konfigureret af Microsoft baseret på tjenestekrav og randomiseret til samplingsformål.
Ved hvert optikindsamlingsinterval kan en eller flere af følgende målinger indsamles ved hjælp af slutbrugerenheden som målingskilde og et Microsoft 365 tjenesteslutpunkt som målingsdestination:

| Måling | Beskrivelse |
| --- | --- |
| Latency | Den tid, det tager at hente en lille fil via HTTP |
| Overførselshastighed | Den tid, det tager at hente en større fil via HTTP, målt sjældent for at undgå overdrevent båndbreddeforbrug |
| Rundturstid (RTT) | ICMP-ping |
| Traceroute | ICMP-sporingsroute |

Hver måling er typisk knyttet til yderligere oplysninger, som kan omfatte følgende elementer:

| Element | Beskrivelse |
| --- | --- |
| Lejer-id | Entydigt id for kundens Azure Active Directory lejer, der er knyttet til slutbrugerenheden. |
| Skærm-id | Id for det program, der genererer anmodningen (f.eks. Outlook, OneDrive osv.), som leveres af det klientprogram, der udfører målingen. |
| Anmodnings-id | Identifikator for anmodningen om måling, der er angivet i den målingskonfiguration, der leveres af Microsoft. |
| Ekstern IP | Maskeret kilde-IP, der er knyttet til anmodningen fra klienten til tjenesteslutpunktet, leveret af den server, der modtog målingsanmodningen og beregnede baseret på klientens IP-adresse, som er synlig for Microsoft. IP-adresser maskeres til et /24-undernet for IPv4-adresser eller et /48-undernet for IPv6-adresser for at sikre, at Microsoft ikke kan identificere individuelle enheder eller brugere. |
| Front-end | Microsoft 365 tjenestefrontend-id, der leveres af den server, der modtog anmodningen om måling. |
| Slutpunkt | Microsoft 365 placering af tjenesteslutpunkt, som leveres af den server, der modtog anmodningen om måling. |
| Certifikat udstedt af | Egenskaben "certifikat udstedt af" for det SSL-certifikat, der blev præsenteret under oprettelse af forbindelse til tjenesteslutpunktet, hvilket angiver det nøglecenter, der har udstedt certifikatet til tjenesteslutpunktet. |
| Certifikataftryk | Egenskaben "certifikataftryk" for det SSL-certifikat, der blev præsenteret under oprettelse af forbindelse til tjenesteslutpunktet, som er et offentligt tilgængeligt entydigt id for certifikatet. |
| Breddegrad/længdegrad | Den abstrakte breddegrad og længdegrad for slutbrugerenheden. Dette indsamles kun for lejere, der har aktiveret Windows Placeringstjeneste på slutbrugerenheder, og som også har [aktiveret indsamling af disse oplysninger på Microsoft 365 administrationsportal.](office-365-network-mac-perf-overview.md#1-enable-windows-location-services) |

## <a name="measurement-process"></a>Måleproces

Hver slutbrugerenhed udfører typisk en måling enten på et planlagt grundlag (for installerede programmer) eller baseret på den handling, der udføres ved indlæsning af browsersider (for webbaserede programmer). Måleaktiviteter udføres som handlinger i baggrunden og påvirker ikke programoplevelsen for brugerne. Da de målingstyper og destinationer, der skal bruges til en bestemt gentagelse af denne proces, er tilfældige, vil kunderne muligvis bemærke anmodninger til Microsoft-tjenesteslutpunkter i deres område, der svarer til de typiske anmodninger, der foretages af slutbrugerenheder for normal programforbindelse. Derudover kan kunder bemærke anmodninger til Microsoft-tjenesteslutpunkter, der ligger uden for deres lokale område. Disse målinger bruges ofte til at sikre optimal routing af kundeanmodninger til det bedste tjenesteslutpunkt, da ændringer i kunde- og ISP-infrastrukturen kan kræve, at Microsoft løbende ændrer vores politikker for anmodningsrouting. Få mere at vide om, hvordan Microsoft dirigerer trafik til det bedste tjenesteslutpunkt, og hvordan du optimerer forbindelsen til Microsoft 365 tjenester i [oversigten over Microsoft 365 netværksforbindelse](microsoft-365-networking-overview.md).

## <a name="service-endpoints"></a>Tjenesteslutpunkter

De Microsoft-tjenesteslutpunkter, der bruges som destinationer for disse målinger, er indeholdt i de publicerede [Office 365 URL-adresser og IP-adresseområder](urls-and-ip-address-ranges.md). Adgang til yderligere tjenesteslutpunkter er ikke nødvendig for samlingen af disse forbindelsesoptik.
