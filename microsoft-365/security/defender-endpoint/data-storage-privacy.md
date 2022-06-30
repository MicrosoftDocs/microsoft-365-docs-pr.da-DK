---
title: Microsoft Defender for Endpoint datalager og beskyttelse af personlige oplysninger
description: Få mere at vide om, hvordan Microsoft Defender for Endpoint håndterer beskyttelse af personlige oplysninger og data, der indsamles.
keywords: Microsoft Defender for Endpoint, datalager og beskyttelse af personlige oplysninger, lager, beskyttelse af personlige oplysninger, licenser, geoplacering, dataopbevaring, data
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
ms.openlocfilehash: d1d8ad0a16129e909476891291c0b2c0f0d54956
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554131"
---
# <a name="microsoft-defender-for-endpoint-data-storage-and-privacy"></a>Microsoft Defender for Endpoint datalager og beskyttelse af personlige oplysninger

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

I dette afsnit beskrives nogle af de oftest stillede spørgsmål om beskyttelse af personlige oplysninger og datahåndtering for Defender for Endpoint.

> [!NOTE]
> I dette dokument forklares datalageret og oplysningerne om beskyttelse af personlige oplysninger, der er relateret til Defender for Endpoint. Du kan finde flere oplysninger om Defender for Endpoint og andre produkter og tjenester, f.eks. Microsoft Defender Antivirus og Windows, i [Microsofts erklæring om beskyttelse af personlige oplysninger](https://go.microsoft.com/fwlink/?linkid=827576). Se også [Ofte stillede spørgsmål om beskyttelse af personlige oplysninger i Windows](https://go.microsoft.com/fwlink/?linkid=827577) for at få flere oplysninger.

## <a name="what-data-does-microsoft-defender-for-endpoint-collect"></a>Hvilke data indsamler Microsoft Defender for Endpoint?

Microsoft Defender for Endpoint indsamler og gemmer oplysninger fra dine konfigurerede enheder i en kunde dedikeret og adskilt lejer, der er specifik for tjenesten med henblik på administration, sporing og rapportering.

De indsamlede oplysninger omfatter fildata (f.eks. filnavne, størrelser og hashen), procesdata (kørende processer, hashes), registreringsdata, netværksforbindelsesdata (værts-IP'er og porte) og enhedsoplysninger (f.eks. enheds-id'er, navne og operativsystemversionen).

Microsoft gemmer disse data sikkert i Microsoft Azure og vedligeholder dem i overensstemmelse med Microsofts praksis for beskyttelse af personlige oplysninger og [Microsoft Trust Center-politikker](https://go.microsoft.com/fwlink/?linkid=827578).

Disse data gør det muligt for Defender for Endpoint at:

- Identificer proaktivt indikatorer for angreb (IOA'er) i din organisation
- Generér beskeder, hvis der blev registreret et muligt angreb
- Giv dine sikkerhedshandlinger en visning i enheder, filer og URL-adresser, der er relateret til trusselssignaler fra dit netværk, så du kan undersøge og udforske tilstedeværelsen af sikkerhedstrusler på netværket.

Microsoft bruger ikke dine data til annoncering.

## <a name="data-protection-and-encryption"></a>Databeskyttelse og kryptering

Defender for Endpoint-tjenesten anvender de nyeste databeskyttelsesteknologier, der er baseret på Microsoft Azure-infrastruktur.

Der er forskellige aspekter af relevans for databeskyttelse, som vores tjeneste tager sig af. Kryptering er en af de mest kritiske og omfatter inaktiv datakryptering, kryptering under flyvning og nøgleadministration med Key Vault. Du kan finde flere oplysninger om andre teknologier, der bruges af Defender for Endpoint-tjenesten, i [Oversigt over Azure-kryptering](/azure/security/security-azure-encryption-overview).

I alle scenarier krypteres data med mindst 256-bit [AES-kryptering](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) .

## <a name="data-storage-location"></a>Placering af datalager

Defender for Endpoint opererer i Microsoft Azure-datacentre i EU, Storbritannien eller i USA. Kundedata, der indsamles af tjenesten, kan gemmes i: (a) lejerens geografiske placering, som identificeret under klargøring, eller (b), hvis Defender for Endpoint bruger en anden Microsoft-onlinetjeneste til at behandle disse data, geoplaceringen som defineret i reglerne for datalager for den anden onlinetjeneste.

Kundedata i pseudonymiseret form kan også gemmes i det centrale lager- og behandlingssystemer i USA.

Når dataene er konfigureret, kan du ikke ændre den placering, hvor dine data er gemt. Dette gør det nemt at minimere risikoen for overholdelse af angivne standarder ved aktivt at vælge de geografiske placeringer, hvor dine data skal placeres.

## <a name="is-my-data-isolated-from-other-customer-data"></a>Er mine data isoleret fra andre kundedata?

Ja, dine data isoleres via adgangsgodkendelse og logisk adskillelse baseret på kundeidentifikator. Hver kunde kan kun få adgang til data, der indsamles fra sin egen organisation, og generiske data, som Microsoft leverer.

## <a name="how-does-microsoft-prevent-malicious-insider-activities-and-abuse-of-high-privilege-roles"></a>Hvordan forhindrer Microsoft ondsindede insideraktiviteter og misbrug af roller med høje rettigheder?

Microsoft-udviklere og -administratorer har til design fået tilstrækkelige rettigheder til at udføre deres tildelte opgaver for at drive og udvikle tjenesten. Microsoft udruller kombinationer af forebyggende, detektiv- og reaktive kontrolelementer, herunder følgende mekanismer for at beskytte mod uautoriseret udvikler- og/eller administrativ aktivitet:

- Tæt adgangskontrol til følsomme data
- Kombinationer af kontrolelementer, der i høj grad forbedrer uafhængig registrering af skadelig aktivitet
- Flere niveauer af overvågning, logføring og rapportering

Derudover udfører Microsoft kontrol i baggrunden af visse operationspersonale og begrænser adgangen til programmer, systemer og netværksinfrastruktur i forhold til niveauet af baggrundsbekræftelse. Operations personale følger en formel proces, når de er forpligtet til at få adgang til en kundes konto eller relaterede oplysninger i forbindelse med udførelsen af deres opgaver.

Adgang til data for tjenester, der er udrullet i Microsoft Azure Government-datacentre, gives kun til driftspersonale, der er blevet screenet og godkendt til at håndtere data, der er underlagt visse offentlige bestemmelser og krav, f.eks. FedRAMP, NIST 800.171 (DIB), ITAR, IRS 1075, DoD L4 og CJIS.

## <a name="is-data-shared-with-other-customers"></a>Deles data med andre kunder?

Nej. Kundedata er isoleret fra andre kunder og deles ikke. Indsigt i de data, der stammer fra Microsoft-behandling, og som ikke indeholder kundespecifikke data, kan dog deles med andre kunder. Hver kunde kan kun få adgang til data, der indsamles fra sin egen organisation, og generiske data, som Microsoft leverer.

## <a name="how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy"></a>Hvor længe vil Microsoft gemme mine data? Hvad er Microsofts politik for dataopbevaring?

### <a name="at-service-onboarding"></a>Vedr. onboarding

Data bevares som standard i 180 dage. Du kan dog angive politikken for dataopbevaring for dine data. Dette bestemmer, hvor længe Microsoft Defender for Endpoint gemmer dine data. Der er en fleksibilitet i at vælge mellem én måned og seks måneder for at opfylde din virksomheds lovmæssige overholdelsesbehov.

### <a name="at-contract-termination-or-expiration"></a>Ved kontraktafslutning eller udløb

Dine data bevares og vil være tilgængelige for dig, mens licensen er under udvidet periode eller suspenderet tilstand. Ved udgangen af denne periode slettes disse data fra Microsofts systemer for at gøre dem uoprettelige, senest 180 dage fra kontraktens ophør eller udløb.

### <a name="advanced-hunting-data"></a>Avancerede jagtdata

Avanceret jagt er et forespørgselsbaseret værktøj til trusselsjagt, der giver dig mulighed for at udforske op til 30 dages rådata.

## <a name="can-microsoft-help-us-maintain-regulatory-compliance"></a>Kan Microsoft hjælpe os med at opretholde overholdelse af angivne standarder?

Microsoft giver kunderne detaljerede oplysninger om Microsofts programmer til sikkerhed og overholdelse af angivne standarder, herunder overvågningsrapporter og overholdelsespakker, for at hjælpe kunderne med at vurdere Defender for Endpoint-tjenester i forhold til deres egne juridiske og lovmæssige krav. Defender for Endpoint har opnået en række certificeringer, herunder ISO, SOC, FedRAMP High og PCI og fortsætter med at forfølge yderligere nationale, regionale og branchespecifikke certificeringer.

Ved at give kunder kompatible, uafhængigt verificerede tjenester gør Microsoft det nemmere for kunderne at opnå overholdelse af angivne standarder for den infrastruktur og de programmer, de kører.

Du kan finde flere oplysninger om Defender for Endpoint-certificeringsrapporter i [Microsoft Center for sikkerhed og rettighedsadministration](https://servicetrust.microsoft.com/). 

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-datastorage-belowfoldlink)
