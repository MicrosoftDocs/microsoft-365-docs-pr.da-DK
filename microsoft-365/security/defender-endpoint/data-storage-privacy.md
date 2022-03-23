---
title: Microsoft Defender til lagring af data i slutpunktet og beskyttelse af personlige oplysninger
description: Få mere at vide om, hvordan Microsoft Defender til Slutpunkt håndterer beskyttelse af personlige oplysninger og data, som det indsamler.
keywords: Microsoft Defender til Slutpunkt, datalagring og beskyttelse af personlige oplysninger, lager, beskyttelse af personlige oplysninger, licenser, geoplacering, dataopbevaring, data
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 7e6e530406b4211c62d315f26b8f956cf6bf1bde
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63591271"
---
# <a name="microsoft-defender-for-endpoint-data-storage-and-privacy"></a>Microsoft Defender til lagring af data i slutpunktet og beskyttelse af personlige oplysninger

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Dette afsnit omhandler nogle af de oftest stillede spørgsmål om beskyttelse af personlige oplysninger og datahåndtering for Defender til Slutpunkt.

> [!NOTE]
> Dette dokument forklarer oplysningerne om datalagring og beskyttelse af personlige oplysninger, der er relateret til Defender til Slutpunkt. Du kan finde flere oplysninger om Defender til Slutpunkt og andre produkter og tjenester som f.Microsoft Defender Antivirus og Windows i Microsofts erklæring om beskyttelse af [personlige oplysninger](https://go.microsoft.com/fwlink/?linkid=827576). Se også Ofte [stillede Windows om beskyttelse](https://go.microsoft.com/fwlink/?linkid=827577) af personlige oplysninger for at få flere oplysninger.

## <a name="what-data-does-microsoft-defender-for-endpoint-collect"></a>Hvilke data indsamler Microsoft Defender til slutpunkt?

Microsoft Defender til Slutpunkt indsamler og gemmer oplysninger fra dine konfigurerede enheder i en dedikeret og adskilt lejer, som er adskilt af kunden, og som er specifik for tjenesten med henblik på administration, sporing og rapportering.

De oplysninger, der indsamles, omfatter fildata (f.eks. filnavne, størrelser og hashes), procesdata (kører processer, hashes), registreringsdata, netværksforbindelsesdata (værts-IP'er og porte) og enhedsoplysninger (f.eks. enheds-id'er, navne og versionen af operativsystemet).

Microsoft gemmer disse data sikkert i Microsoft Azure og vedligeholder dem i overensstemmelse med Microsofts politik for beskyttelse af personlige oplysninger og [Microsoft Center for sikkerhed og sikkerhed.](https://go.microsoft.com/fwlink/?linkid=827578)

Disse data gør det muligt for Defender for Endpoint at:

- Proaktivt identificere angrebsindikatorer (IOAs) i organisationen
- Generer beskeder, hvis der blev fundet et muligt angreb
- Giv dine sikkerhedshandlinger et indblik i enheder, filer og URL-adresser, der er relateret til trusselssignaler fra dit netværk, så du kan undersøge og undersøge tilstedeværelsen af sikkerhedstrusler på netværket.

Microsoft bruger ikke dine data til annoncering.

## <a name="data-protection-and-encryption"></a>Databeskyttelse og kryptering

Defender for Endpoint-tjenesten anvender avancerede teknologier til databeskyttelse, som er baseret på Microsoft Azure infrastruktur.

Der er forskellige aspekter, som er relevante for databeskyttelse, som vores tjeneste tager sig af. Kryptering er en af de mest kritiske, og den indeholder datakryptering, kryptering i flight og nøgleadministration med Nøgle boks. Du kan finde flere oplysninger om andre teknologier, der bruges af Defender for Endpoint-tjenesten, under [Oversigt over Azure-kryptering](/azure/security/security-azure-encryption-overview).

I alle scenarier krypteres data ved hjælp af 256-bit [AES-kryptering](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) som minimum.

## <a name="data-storage-location"></a>Placering af datalager

Defender for Endpoint fungerer Microsoft Azure datacentre i EU, Storbritannien eller USA. Kundedata, der indsamles af tjenesten, kan gemmes i: (a) lejerens geoplacering som identificeret under klargøring, eller(b) hvis Defender til Slutpunkt bruger en anden Microsoft-onlinetjeneste til at behandle sådanne data, geoplaceringen som defineret af datalagringsreglerne for den pågældende anden onlinetjeneste.

Kundedata i pseudonymiseret form kan også gemmes i de centrale lagrings- og behandlingssystemer i USA.

Når det er konfigureret, kan du ikke ændre den placering, hvor dine data er gemt. Dette er en nem metode til at minimere risikoen for overholdelse ved aktivt at vælge de geografiske placeringer, hvor dine data vil være placeret.

## <a name="is-my-data-isolated-from-other-customer-data"></a>Er mine data isolerede fra andre kundedata?

Ja, dine data isoleres via adgangsgodkendelse og logisk opdeling baseret på kundeidentifikator. Hver kunde kan kun få adgang til data, der er indsamlet fra sin egen organisation, og generiske data, som Microsoft leverer.

## <a name="how-does-microsoft-prevent-malicious-insider-activities-and-abuse-of-high-privilege-roles"></a>Hvordan forhindrer Microsoft skadelige Insider-aktiviteter og misbrug af roller med høj rettighed?

Microsoft-udviklere og -administratorer har tilsendet, at de har fået tilstrækkelige rettigheder til at udføre deres opgaver for at drive og udvikle tjenesten. Microsoft implementerer kombinationer af sikkerhedsforanstaltninger, angreb og reaktive kontrolelementer, herunder følgende mekanismer, der hjælper med at beskytte mod uautoriserede udvikler- og/eller administrative aktiviteter:

- Tæt adgangskontrol til følsomme data
- Kombinationer af kontrolelementer, der markant forbedrer den uafhængige registrering af skadelig aktivitet
- Overvågning, logføring og rapportering på flere niveauer

Desuden udfører Microsoft baggrundsbekræftelse for visse operationsmedarbejdere og begrænser adgangen til programmer, systemer og netværksinfrastruktur i forhold til niveauet af baggrundsbekræftelse. Driftsmedarbejdere følger en formel proces, når de skal have adgang til en kundes konto eller relaterede oplysninger for at udføre deres opgaver.

Adgang til data for tjenester, der er installeret i Microsoft Azure Government-datacentre, gives kun til driftsmedarbejdere, der er blevet screenet og godkendt til at håndtere data, der er underlagt visse offentlige bestemmelser og krav, f.eks. FedRAMP, NIST 800.171 (DIB), ITAR, IRS 1075, DoD L4 og CJIS.

## <a name="is-data-shared-with-other-customers"></a>Deles data med andre kunder?

Nej. Kundedata isoleres fra andre kunder og deles ikke. Indsigt i de data, der kommer fra Microsoft-behandling, og som ikke indeholder nogen kundespecifikke data, kan dog deles med andre kunder. Hver kunde kan kun få adgang til data, der er indsamlet fra sin egen organisation, og generiske data, som Microsoft leverer.

## <a name="how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy"></a>Hvor længe gemmer Microsoft mine data? Hvad er Microsofts politik for opbevaring af data?

### <a name="at-service-onboarding"></a>Til service-onboarding

Data bevares som standard i 180 dage. Du kan dog angive dataopbevaringspolitikken for dine data. Dette bestemmer, hvor længe Window Defender til Slutpunkt gemmer dine data. Der er fleksibilitet ved at vælge mellem en måned og seks måneder for at imødekomme din virksomheds lovmæssige behov for overholdelse.

### <a name="at-contract-termination-or-expiration"></a>Ved ophør af kontrakt eller udløb

Dine data gemmes og vil være tilgængelige for dig, mens licensen er under udvidet periode eller suspenderet tilstand. I slutningen af denne periode bliver disse data slettet fra Microsofts systemer, så de ikke kan gendannes senest 180 dage fra kontraktafslutning eller udløb.

### <a name="advanced-hunting-data"></a>Avancerede jagtdata

Avanceret jagt er et forespørgselsbaseret værktøj til trusselssøgning, som giver dig mulighed for at udforske op til 30 dages rå data.

## <a name="can-microsoft-help-us-maintain-regulatory-compliance"></a>Kan Microsoft hjælpe os med at overholde lovgivningen?

Microsoft giver kunderne detaljerede oplysninger om Microsofts sikkerheds- og overholdelsesprogrammer, herunder overvågningsrapporter og kompatibilitetspakker, for at hjælpe kunder med at vurdere Defender for Endpoint-tjenester i forhold til deres egne juridiske og lovmæssige krav. Defender for Endpoint har opnået en række certificeringer, herunder ISO, SOC, FedRAMP High og ETHERNET og fortsætter med at gennemføre yderligere nationale, regionale og branchespecifikke certificeringer.

Ved at give kunderne kompatible, uafhængigt bekræftede tjenester gør Microsoft det nemmere for kunderne at opnå overholdelse af de infrastruktur- og programmer, de kører.

Du kan finde flere oplysninger om Defender for Endpoint-certificeringsrapporterne i [Microsoft Center for sikkerhed og sikkerhed](https://servicetrust.microsoft.com/). 

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-datastorage-belowfoldlink)
