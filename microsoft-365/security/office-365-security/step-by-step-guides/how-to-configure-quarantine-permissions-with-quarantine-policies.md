---
title: Sådan konfigureres karantænetilladelser og -politikker
description: Trinnene til at konfigurere karantænepolitikker og -tilladelser på tværs af forskellige grupper, herunder AdminOnlyPolicy, begrænset adgang, fuld adgang og give sikkerhedsadministratorer og brugere en nem måde at administrere falske positive mapper på.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: c8f739a82223a9315e5082377b4951a88b1ea1df
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043668"
---
# <a name="how-to-configure-quarantine-permissions-and-policies"></a>Sådan konfigureres karantænetilladelser og -politikker

Det er vigtigt at give sikkerhedsadministratorer og brugere en meget enkel måde at administrere falske positive mapper på i betragtning af den øgede efterspørgsel efter en mere aggressiv sikkerhedsholdning med udviklingen af hybridarbejde. Ved hjælp af en præskriptiv tilgang kan administratorer og brugere opnå dette med vejledningen nedenfor.

> [!TIP]
> Du kan finde en kort video, der er målrettet til administratorer, der forsøger at angive karantænetilladelser og -politikker, [i dette link](https://www.youtube.com/watch?v=vnar4HowfpY). Hvis du er slutbruger, skal du vælge dette [1 minuts oversigt over](https://www.youtube.com/watch?v=s-vozLO43rI) processen.

## <a name="what-you-will-need"></a>Det skal du bruge
- Tilstrækkelige tilladelser (rolle som sikkerhedsadministrator)
- 5 minutter til at udføre nedenstående trin.

## <a name="creating-custom-quarantine-policies-with-request-release-flow"></a>Oprettelse af brugerdefinerede karantænepolitikker med anmodningsfrigivelsesflow

Vores brugerdefinerede politikker giver administratorer mulighed for at beslutte, hvilke elementer deres brugere kan prioritere i mappen ***Falsk positiv** _ med udvidet mulighed for at give brugeren mulighed for at anmode om _release* af disse elementer fra mappen.

1. Beslut, hvilke domme kategori (bulk, spam, phish, høj tillid phish, eller malware) af elementer, du vil have din bruger til at triage og ikke triage.
1. For de kategorier, som du ikke ønsker, at brugerne skal triage, skal du tildele elementerne til **AdminOnlyPolicy**. Hvad angår den kategori, du vil have, at brugerne skal triage med begrænset adgang, kan du *oprette en brugerdefineret politik* med adgang til anmodningsfrigivelse og tildele brugere til den pågældende kategori.
1. Det **anbefales på det kraftigste** , at elementer af typen malware og phish med høj sikkerhed tildeles **adminOnlyPolicy**, at almindelige tillids phish-elementer tildeles *begrænset adgang med anmodningsfrigivelse*, mens masse- og spam kan efterlades som fuld adgang for brugere.

> [!IMPORTANT]
> Du kan finde flere oplysninger om, hvordan detaljerede brugerdefinerede politikker kan oprettes, under [Karantænepolitikker – Office 365 | Microsoft Docs](../../office-365-security/quarantine-policies.md).

## <a name="assigning-quarantine-policies-and-enabling-notification-with-organization-branding"></a>Tildeling af karantænepolitikker og aktivering af meddelelser med organisationsbranding

Når det er besluttet, hvilke kategorier af elementer brugerne kan triage eller ikke-triage, og har oprettet de tilsvarende karantænepolitikker, skal administratorer tildele disse politikker til de respektive brugere og aktivere meddelelser.

1. Identificer de brugere, grupper eller domæner, du vil medtage i kategorien *fuld adgang* i forhold til kategorien *begrænset adgang* i forhold til kategorien *Kun administrator* .
1. Log på [Microsoft Security-portalen](https://security.microsoft.com).
1. Vælg **Mail & samarbejdspolitikker** > **& regler**.
1. Vælg **Trusselspolitikker**.
1. Vælg hver af følgende: **Anti-spam-politikker**, **Anti-phishing-politik**, **Anti-Malware-politik**.
1. Vælg **Opret politik** , og vælg **Indgående**.
1. Tilføj politiknavn, brugere, grupper eller domæner, som politikken skal anvendes på, og **Næste**.
1. Under fanen **Handlinger** skal du vælge **Karantænemeddelelse** for kategorier. Du vil bemærke et ekstra panel til *valg af karantænepolitik*. Brug denne rulleliste til at vælge den karantænepolitik, du oprettede tidligere.
1. Gå videre til afsnittet **Gennemse** , og klik på knappen **Bekræft** for at oprette den nye politik.
1. Gentag de samme trin for de andre politikker: **Anti-phishing-politik**, **Anti-Malware-politik** og **Pengeskab politik for vedhæftede filer**.

> [!TIP]
> Du kan finde flere detaljerede oplysninger om, hvad du har lært indtil videre, under [Konfigurer politikker for spamfilter – Office 365 | ](../../office-365-security/configure-your-spam-filter-policies.md)|  Microsoft Docs [Konfigurer politikker til bekæmpelse af phishing i EOP – Office 365 | ](../../office-365-security/configure-anti-phishing-policies-eop.md) |  Microsoft Docs [Konfigurer antimalwarepolitikker – Office 365 | ](../../office-365-security/configure-anti-malware-policies.md)|  Microsoft Docs [Konfigurer politikker for vedhæftede filer Pengeskab i Microsoft Defender for Office 365 – Office 365 | Microsoft Docs](../../office-365-security/set-up-safe-attachments-policies.md)

## <a name="next-steps"></a>Næste trin

- Brug **Den globale politik** , der er tilgængelig i karantænepolitikken, til at aktivere organisationens brandinglogo, visningsnavn og ansvarsfraskrivelse.
- Angiv også **brugerhyppigheden til 1 dag** for karantænemeddelelsen.

## <a name="more-information"></a>Flere oplysninger

Få mere at vide om organisationens branding- og meddelelsesindstillinger her [Karantænepolitikker – Office 365 | Microsoft Docs](../../office-365-security/quarantine-policies.md)
