---
title: Plan for ophør af support-software og softwareversioner
description: Find og planlæg software- og softwareversioner, der ikke længere understøttes, og som ikke modtager sikkerhedsopdateringer.
keywords: Håndtering af trusler og sikkerhedsrisici, Microsoft Defender til Endpoint tvm sikkerheds anbefaling, cybersecurity anbefaling, handlings løsning sikkerhedsanbefaling
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 65842d0bd56308b6a5e5476f84c089b63a04987b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63591928"
---
# <a name="plan-for-end-of-support-software-and-software-versions-with-threat-and-vulnerability-management"></a>Planlæg ophør af supportsoftware og softwareversioner med Håndtering af trusler og sikkerhedsrisici

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Ophør af support (EOS), ellers kaldet slutningen af levetid (EOL), for software eller softwareversioner betyder, at de ikke længere vil blive understøttet eller serviceret, og ikke vil modtage sikkerhedsopdateringer. Når du bruger software- eller softwareversioner med ophørt support, udsætter du din organisation for sikkerhedsrisici, juridiske og økonomiske risici.

Det er vigtigt for sikkerhed og it-administratorer at arbejde sammen og sikre, at organisationens softwarelager er konfigureret til optimale resultater, overholdelse og et sund netværksøkosystem. De bør undersøge mulighederne for at fjerne eller erstatte apps, der har nået ophør af support og opdateringsversioner, der ikke længere understøttes. Det er bedst at oprette og implementere en plan **før** slutdatoerne for support.

> [!NOTE]
> Support ved afslutning er i øjeblikket kun tilgængelig for Windows-produkter.

## <a name="find-software-or-software-versions-that-are-no-longer-supported"></a>Find software- eller softwareversioner, der ikke længere understøttes

1. Fra menuen Håndtering af trusler og sikkerhedsrisici skal du gå til [**Sikkerhedsanbefalinger**](tvm-security-recommendation.md).
2. Gå til panelet **Filtre** , og se efter mærkesektionen. Vælg en eller flere af EOS-mærkeindstillingerne. Derefter **skal du anvende**.

    ![Skærmbillede af mærker, der siger EOS-software, EOS-versioner og kommende EOS-versioner.](images/tvm-eos-tag.png)

3. Du får vist en liste med anbefalinger relateret til software med ophørt support, softwareversioner, der er ophør på support, eller versioner med kommende ophør af support. Disse mærker er også synlige på [softwarelagersiden](tvm-software-inventory.md) .

    ![Anbefalinger med EOS-mærke.](images/tvm-eos-tags-column.png)

## <a name="list-of-versions-and-dates"></a>Liste over versioner og datoer

Hvis du vil have vist en liste over versioner, der har nået supportens ophør eller slutdato eller support snart, og disse datoer, skal du følge nedenstående trin:

1. Der vises en meddelelse i pop op-pop-op-pop-op-meddelelsen med sikkerhedsanbefaling for software med versioner, der har nået ophør af supporten, eller snart når ophør af support.

    ![Skærmbillede af versionsdistributionslink.](images/eos-upcoming-eos.png)

2. Vælg **versionsdistributionslinket** for at gå til siden til analyse af software. Her kan du se en filtreret liste over versioner med mærker, der identificerer dem som ophør af supporten eller kommende ophør af supporten.

    ![Skærmbillede af siden til analyse af software med ophør af supportsoftware.](images/software-drilldown-eos.png)

3. Vælg en af versionerne i tabellen, der skal åbnes. For eksempel version 10.0.18362.1. Der vises et pop op-møde med slutdato for support.

    ![Skærmbillede af slutdato for support.](images/version-eos-date.png)

Når du har identificeret, hvilke software- og softwareversioner der er sårbar pga. statussen for ophør af understøttelsen, skal du beslutte, om du vil opdatere eller fjerne dem fra organisationen. Hvis du gør det, sænker det din organizations eksponering for sårbarheder og avancerede vedvarende trusler.

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over trusler håndtering af sikkerhedsrisici sikkerhed](next-gen-threat-and-vuln-mgt.md)
- [Sikkerhedsanbefalinger](tvm-security-recommendation.md)
- [Lager over software](tvm-software-inventory.md)
