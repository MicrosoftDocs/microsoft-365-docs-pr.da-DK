---
title: Mindske sårbarheder uden for dagen – Håndtering af trusler og sikkerhedsrisici
description: Få mere at vide om, hvordan du kan finde og afhjælpe sårbarheder uden for døgnet i dit miljø Håndtering af trusler og sikkerhedsrisici.
keywords: Microsoft Defender til Endpoint tvm zero day vulnerabilities, tvm, threat & håndtering af sikkerhedsrisici, zero day, 0-day, reducer 0 dages sårbarheder, sårbar CVE
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: f4a3e227dd43a812bea64e227e315d207eb6fc7b
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63593783"
---
# <a name="mitigate-zero-day-vulnerabilities---threat-and-vulnerability-management"></a>Mindske sårbarheder uden for dagen – Håndtering af trusler og sikkerhedsrisici

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

En sikkerhedsrisiko på nul dage er en sårbarhed i software, som der ikke er frigivet nogen officiel programrettelse eller sikkerhedsopdatering til. En softwareleverandør kan eller er muligvis ikke opmærksom på sikkerhedsrisikoen, og der er ingen offentlige oplysninger om denne risiko. Zero-day-sikkerhedsrisici har ofte høj alvorsgrad og udnyttes aktivt.

Trussels- håndtering af sikkerhedsrisici viser kun sårbarheder, der er lige ved navn, og som den indeholder oplysninger om.

## <a name="find-information-about-zero-day-vulnerabilities"></a>Find oplysninger om sårbarheder, der kun er en dags problemer

Når en nuldagssikkerhedsrisiko er fundet, vil oplysninger om den blive formidlet via følgende oplevelser på Microsoft 365 Defender portal.

> [!NOTE]
> 0-dages sikkerhedsrisiko er i øjeblikket kun tilgængelig for Windows-produkter.

### <a name="threat-and-vulnerability-management-dashboard"></a>Trussels- håndtering af sikkerhedsrisici dashboard

Se efter anbefalinger med et nuldagsmærke i kortet "Vigtigste sikkerhedsanbefalinger".

![Vigtigste anbefalinger med et nuldagsmærke.](images/tvm-zero-day-top-security-recommendations.png)

Find topsoftware med zero-day-mærket på kortet "Øverste sårbar software".

![En af de mest følsomme software med et nul dages-mærke.](images/tvm-zero-day-top-software.png)

### <a name="weaknesses-page"></a>Side med til at få det til at se ud

Se efter den navngivne nuldagssikkerhedsrisiko samt en beskrivelse og detaljer.

- Hvis sikkerhedsrisikoen er tildelt et CVE-ID, får du vist etiketten på nul dage ud for CVE-navnet.

- Hvis sikkerhedsrisikoen ikke er tildelt CVE-ID, finder du den under et internt, midlertidigt navn, der ligner "TVM-XXXX-XXXX". Navnet opdateres, når et officielt CVE-ID er blevet tildelt, men det forrige interne navn vil stadig kunne søges og findes i sidepanelet.

:::image type="content" alt-text="Eksempel på nuldag for CVE-2020-17087 på siden med startsiden for nuldag." source="images/tvm-zero-day-weakness-name.png" lightbox="images/tvm-zero-day-weakness-name.png":::

### <a name="software-inventory-page"></a>Side for softwarelager

Søg efter software med zero-day-koden. Filtrer efter mærket "nul dage" for kun at få vist software med zero-day-sårbarheder.

:::image type="content" alt-text="Eksempel på nuldag Windows Server 2016 på softwarelagersiden." source="images/tvm-zero-day-software-inventory.png" lightbox="images/tvm-zero-day-software-inventory.png":::

### <a name="software-page"></a>Softwareside

Kig efter et nul dages-mærke for hver software, der er blevet påvirket af sikkerhedsrisikoen uden dag.

:::image type="content" alt-text="Eksempel på nuldag for Windows siden Server 2016-software." source="images/tvm-zero-day-software-page.png" lightbox="images/tvm-zero-day-software-page.png":::

### <a name="security-recommendations-page"></a>Siden med sikkerhedsanbefalinger

Få vist tydelige forslag til afhjælpnings- og afhjælpningsmuligheder, herunder løsninger, hvis de findes. Filtrer efter mærket "nul dage" for kun at få vist sikkerhedsanbefalinger, der adresserer sårbarheder uden dag.

Hvis der er software med en nuldagssikkerhedsrisiko og yderligere sårbarheder, der skal håndteres, får du én anbefaling om alle sårbarheder.

:::image type="content" alt-text="Eksempel på nuldag Windows Server 2016 på siden med anbefalinger om sikkerhed." source="images/tvm-zero-day-security-recommendation.png" lightbox="images/tvm-zero-day-security-recommendation.png":::

## <a name="addressing-zero-day-vulnerabilities"></a>Adressering af sårbarheder uden dag

Gå til siden med en sikkerhedsanbefaling, og vælg en anbefaling med en nuldag. Der åbnes en pop op-pop-op-uddeling med oplysninger om sikkerhedsrisici og andre sårbarheder for den pågældende software.

Der vil være et link til afhjælpningsindstillinger og løsninger, hvis de er tilgængelige. Løsninger kan være med til at reducere risikoen ved dette sikkerhedsrisiko uden for dagen, indtil en programrettelse eller sikkerhedsopdatering kan implementeres.

Åbn afhjælpningsindstillinger, og vælg opmærksomhedstype. En afhjælpningsindstilling, der kræver "opmærksomhed, anbefales til sårbarheder uden dagsvisning, da en opdatering ikke er blevet frigivet endnu. Du kan ikke vælge en forfaldsdato, da der ikke er nogen specifik handling at udføre. Hvis der er ældre sårbarheder for denne software, du ønsker at afhjælpe, kan du tilsidesætte afhjælpningsindstillingen "kræver opmærksomhed" og vælge "Opdater".

![Eksempel på pop op-over for nuldag Windows Server 2016 på siden med sikkerhedsanbefalinger.](images/tvm-zero-day-recommendation-flyout400.png)

## <a name="track-zero-day-remediation-activities"></a>Spor afhjælpningsaktiviteter uden dag

Gå til siden Håndtering af trusler og sikkerhedsrisici [afhjælpning for](tvm-remediation.md) at få vist elementet afhjælpningsaktivitet. Hvis du vælger afhjælpningsindstillingen "Handling påkrævet", vil der ikke være nogen statuslinje, status for billet eller forfaldsdato, da der ikke er nogen handling, vi kan overvåge. Du kan filtrere efter afhjælpningstype, f.eks. "softwareopdatering" eller "kræver opmærksomhed", for at få vist alle aktivitetselementer i samme kategori.

## <a name="patching-zero-day-vulnerabilities"></a>Vi har problemer med sårbarheder i løbet af nul dage

Når der udgives en programrettelse til nuldagen, ændres anbefalingen til "Opdater" og en blå etiket ud for den, hvor der står "Ny sikkerhedsopdatering for nul dage". Det vil ikke længere blive overvejet som en nuldagsmærke, og mærket nul dage fjernes fra alle sider.

![Anbefaling for "Update Microsoft Windows 10" med den nye patchmærkat.](images/tvm-zero-day-patch.jpg)

## <a name="related-articles"></a>Relaterede artikler

- [Oversigt over trusler håndtering af sikkerhedsrisici sikkerhed](next-gen-threat-and-vuln-mgt.md)
- [Dashboard](tvm-dashboard-insights.md)
- [Sikkerhedsanbefalinger](tvm-security-recommendation.md)
- [Lager over software](tvm-software-inventory.md)
- [Sårbarheder i min organisation](tvm-weaknesses.md)
