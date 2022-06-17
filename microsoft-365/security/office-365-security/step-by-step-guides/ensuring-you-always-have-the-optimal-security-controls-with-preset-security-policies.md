---
title: Sikring af, at du altid har de optimale sikkerhedskontroller med forudindstillede sikkerhedspolitikker
description: Trinnene til at sikre, at du altid har de bedste sikkerhedskontroller med forudindstillede sikkerhedspolitikker. Med forudindstillede politikker kan du vælge en sikkerhedsprofil af typen Enten Standard eller Strict. Microsoft administrerer og vedligeholder sikkerhedskontroller på tværs af Microsoft Defender for Office 365 for dig.
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
ms.openlocfilehash: 534e548dbd0950b387e757bfb81ebb446f617086
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139450"
---
# <a name="ensuring-you-always-have-the-optimal-security-controls-with-preset-security-policies"></a>Sikring af, at du altid har de optimale sikkerhedskontroller med forudindstillede sikkerhedspolitikker

Forudindstillede sikkerhedspolitikker giver dig mulighed for at vælge en sikkerhedsprofil af enten Standard eller Strict og få Microsoft til at administrere og vedligeholde sikkerhedskontroller på tværs af Microsoft Defender for Office 365 for dig.

Når der tilføjes nye kontrolelementer, eller hvis indstillingen for bedste praksis for et sikkerhedskontrolelement ændres i takt med trusselsbilledet i udvikling, opdaterer Microsoft automatisk indstillingerne for sikkerhedskontrol for brugere, der er tildelt en standard- eller streng forudindstillet sikkerhedspolitik. Når du bruger forudindstillede politikker for sikkerhed, vil du altid have Microsofts anbefalede konfiguration af bedste praksis for dine brugere.

## <a name="what-you-will-need"></a>Det skal du bruge
- Microsoft Defender for Office 365 Plan 1 eller nyere (inkluderet i E5)
- Tilstrækkelige tilladelser (rolle som sikkerhedsadministrator)
- 5 minutter til at udføre nedenstående trin.

## <a name="choosing-between-standard-and-strict-policies"></a>Valg mellem Standard- og Strict-politikker

Vores strenge forudindstillede sikkerhedspolitik har mere aggressive grænser og indstillinger for sikkerhedskontroller, der vil resultere i mere aggressive registreringer og vil involvere administratoren i at træffe beslutninger om, hvilke blokerede mails der frigives til slutbrugere.

- Indsaml listen over dine brugere, der kræver mere aggressive registreringer, selvom det betyder, at mere god mail bliver markeret som mistænkelig. Det er typisk dine chefer, supportmedarbejdere og historisk meget målrettede brugere.

- Sørg for, at de valgte brugere har administratordækning til at gennemse og frigive mails, hvis slutbrugeren mener, at mailen kan være god, og anmoder om, at meddelelsen frigives til dem.

- Hvis ovenstående kriterier er opfyldt, skal brugeren placeres i den strenge forudindstillede sikkerhedspolitik. Ellers skal brugeren placeres i den forudindstillede standardsikkerhedspolitik.

> [!TIP]
> Du kan få oplysninger om, hvad Standard- og Strict-sikkerhedspoliti er, i denne [artikel](../../office-365-security/recommended-settings-for-eop-and-office365.md).

## <a name="enable-security-presets"></a>Aktivér forudindstillinger for sikkerhed

Når du har valgt mellem standard- og strenge sikkerhedsindstillinger for dine brugere, kræver det et par yderligere trin at tildele brugere til hver forudindstillede.

1. Identificer de brugere, grupper eller domæner, du vil medtage i standard- og strenge sikkerhedsindstillinger.
1. Log på Microsoft Security-portalen på https://security.microsoft.com.
1. Vælg Politikker & regler under **Mail & samarbejde** i venstre navigationsrude.
1. Vælg **Trusselspolitikker**.
1. Vælg **Forudindstillede sikkerhedspolitikker** under overskriften **Skabelonpolitikker**
1. Vælg **Administrer** under forudindstillingen Standardbeskyttelse.
1. Vælg **Alle modtagere** for at anvende Exchange Online Protection lejer bredt, eller vælg **Specifikke modtagere** for manuelt at tilføje brugere, grupper eller domæner, du vil anvende beskyttelsespolitikken på. Klik på knappen **Næste** .
1. Vælg **Alle modtagere** for at anvende lejeren Defender for Office 365 Beskyttelse, eller vælg **Specifikke modtagere** for manuelt at tilføje brugere, grupper eller domæner, du vil anvende beskyttelsespolitikken på. Klik på knappen **Næste** .
1. I afsnittet **Repræsentationsbeskyttelse** skal du tilføje mailadresser & domæner for at beskytte mod repræsentationsangreb og derefter tilføje eventuelle afsendere og domæner, der er tillid til, som du ikke ønsker, at repræsentationsbeskyttelsen skal gælde for, og tryk derefter på **Næste**
3. Klik på knappen **Bekræft** .
4. Vælg linket **Administrer** i forudindstillet streng beskyttelse.
5. Gentag trin 7-10 igen, men for brugerne skal der anvendes streng beskyttelse på. (hvis relevant)
7. Klik på knappen **Bekræft** .

> [!TIP]
> Hvis du vil vide mere om forudindstillede politikker, skal du klikke [her](../../office-365-security/preset-security-policies.md)

## <a name="next-steps"></a>Næste trin

Brug konfigurationsanalyse til at afgøre, om dine brugere er konfigureret i henhold til Microsofts bedste praksis.

> [!TIP]
> Konfigurationsanalyse gør det muligt for administratorer at finde og løse sikkerhedspolitikker, hvor indstillingerne er under profilindstillingerne Standard eller Strict i forudindstillede sikkerhedspolitikker. Få mere at vide om Konfigurationsanalyse [her](../../office-365-security/configuration-analyzer-for-security-policies.md).

Der foreslås altid sikre forudindstillinger, da det sikrer, at du altid udøver Microsofts bedste praksis. I nogle tilfælde er brugerdefinerede konfigurationer dog påkrævet. Få mere at vide om brugerdefinerede politikker [her](../../office-365-security/tenant-wide-setup-for-increased-security.md).

