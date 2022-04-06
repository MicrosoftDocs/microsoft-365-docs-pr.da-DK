---
title: Ofte stillede spørgsmål, når du aktiverer Microsoft 365 Defender
description: Få svar på de mest almindeligt stillede spørgsmål om licenser, tilladelser, indledende indstillinger og andre produkter og tjenester, der er relateret til aktivering af Microsoft 365 Defender
keywords: ofte stillede spørgsmål, ofte stillede spørgsmål, GCC, kom i gang, aktivér Microsoft 365 Defender, Microsoft 365 Defender, M365, sikkerhed, dataplacering, påkrævede tilladelser, licensberettigelse, indstillingsside
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 73dddcfc1389eb5bb0b0115f0666c413dc7d2a01
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663198"
---
# <a name="frequently-asked-questions-when-turning-on-microsoft-365-defender"></a>Ofte stillede spørgsmål, når du aktiverer Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Læs svar på de oftest stillede spørgsmål om aktivering [af Microsoft 365 Defender](microsoft-365-defender.md), herunder påkrævede licenser og tilladelser, installation af supporttjenester og indledende indstillinger.

Hvis du vil have en vejledning i, hvordan du slår tjenesten til, skal [du læse Slå Microsoft 365 Defender](m365d-enable.md) til.

## <a name="i-dont-have-a-microsoft-365-e5-license-can-i-still-use-microsoft-365-defender"></a>Jeg har ikke en Microsoft 365 E5 licens. Kan jeg stadig bruge Microsoft 365 Defender?

Kunder med følgende ikke-E5-licenser kan bruge Microsoft 365 Defender:

- Microsoft Defender for Endpoint
- Microsoft Defender for Identity
- Microsoft Defender for Cloud Apps
- Defender for Office 365 (Plan 2)

Du kan se en komplet liste over understøttede licenser [ved at læse licenskravene](prerequisites.md#licensing-requirements).

## <a name="do-i-need-to-install-or-deploy-anything-to-start-using-microsoft-365-defender"></a>Skal jeg installere eller installere noget for at begynde at bruge Microsoft 365 Defender?

Nej, Microsoft 365 Defender konsoliderer data fra Microsoft 365 sikkerhedstjenester, du allerede har installeret. Når du slår den til, vil hændelser, automatiseringer og jagtoplevelser begynde at fungere inden for rammerne af de udrullede produkter. Hvis ingen af disse produkter er installeret korrekt, viser Microsoft 365 Defender ingen data og kan ikke udføre nogen handlinger.

Hvis du vil optimere dine Microsoft 365 Defender oplevelser, anbefaler vi, at du udruller *alle* understøttede [Microsoft 365 sikkerhedsprodukter og -tjenester](deploy-supported-services.md).

## <a name="where-does-microsoft-365-defender-process-and-store-my-data"></a>Hvor behandler og gemmer Microsoft 365 Defender mine data?

Microsoft 365 Defender vælger automatisk en optimal placering for det datacenter, hvor konsoliderede data behandles og gemmes. Hvis du har Microsoft Defender for Endpoint, vælges den samme placering, som bruges af Defender for Endpoint.

>[!NOTE]
>Microsoft Defender for Endpoint automatisk klargør i EU-datacentre, når de aktiveres via Microsoft Defender for Cloud. Microsoft 365 Defender klargøres automatisk i det samme EU-datacenter til kunder, der har klargjort Microsoft Defender for Endpoint på denne måde.

Datacenterplaceringen vises før og efter, at tjenesten er klargjort på indstillingssiden for Microsoft 365 Defender (**Indstillinger > Microsoft 365 Defender**). Hvis du foretrækker at bruge en anden placering i datacenteret, skal du vælge **Har du brug for hjælp?** på portalen Microsoft 365 Defender for at kontakte Microsoft Support.

## <a name="where-can-i-access-microsoft-365-defender"></a>Hvor kan jeg få adgang til Microsoft 365 Defender?

Microsoft 365 Defender findes på: <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a>.

## <a name="what-permissions-do-i-need-to-access-microsoft-365-defender"></a>Hvilke tilladelser skal jeg have for at få adgang til Microsoft 365 Defender?

Konti, der er tildelt følgende Azure Active Directory (Azure AD) roller, kan få adgang til Microsoft 365 Defender funktionalitet og data:

- Global administrator
- Sikkerhedsadministrator
- Sikkerhedsoperator
- Global læser
- Sikkerhedslæser
- Overholdelsesadministrator
- Administrator af overholdelsesdata
- Programadministrator
- Cloud Application Administrator


> [!NOTE]
> Rollebaserede indstillinger for adgangskontrol i Microsoft Defender for Endpoint påvirker adgangen til data. Du kan få flere oplysninger ved at læse om [administration af adgang til Microsoft 365 Defender](m365d-permissions.md).

## <a name="what-time-zone-does-microsoft-365-defender-default-to"></a>Hvilken tidszone er Microsoft 365 Defender standard for?

Som standard viser Microsoft 365 Defender klokkeslætsoplysninger i UTC-tidszonen. Du kan ændre denne indstilling, så du bruger din lokale tidszone. [Få mere at vide om angivelse af tidszone](m365d-time-zone.md)

## <a name="how-can-i-learn-about-new-microsoft-365-defender-feature-and-ui-updates"></a>Hvordan kan jeg få mere at vide om nye Microsoft 365 Defender funktions- og brugergrænsefladeopdateringer?

Microsoft leverer jævnligt oplysninger via de forskellige kanaler, herunder:

- [Meddelelsescenteret](../../admin/manage/message-center.md) i Microsoft 365 Administration
- Blogposts i det [tekniske community til Microsoft 365 sikkerhed & overholdelse af angivne standarder](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/bg-p/securityprivacycompliance)

Få de nyeste offentligt tilgængelige oplevelser ved at aktivere [prøveversionsfunktioner](preview.md).

## <a name="related-topics"></a>Relaterede emner

- [oversigt over Microsoft 365 Defender](microsoft-365-defender.md)
- [Slå Microsoft 365 Defender](m365d-enable.md) til.
- [Licenskrav og andre forudsætninger](prerequisites.md)
- [Udrul understøttede tjenester](deploy-supported-services.md)
- [Slå prøveversionsfunktioner til](preview.md)
