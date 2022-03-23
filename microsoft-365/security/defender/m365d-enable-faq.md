---
title: Ofte stillede spørgsmål ved aktivering af Microsoft 365 Defender
description: Få svar på de oftest stillede spørgsmål om licenser, tilladelser, startindstillinger og andre produkter og tjenester, der er relateret til aktivering af Microsoft 365 Defender
keywords: ofte stillede spørgsmål, ofte stillede spørgsmål, GCC, introduktion, aktivér Microsoft 365 Defender, Microsoft 365 Defender, M365, sikkerhed, dataplacering, påkrævede tilladelser, berettigelse til licens, siden med indstillinger
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
ms.openlocfilehash: e5ed41f400c24a2522ea49f2524d0fe629bdbb9f
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63591303"
---
# <a name="frequently-asked-questions-when-turning-on-microsoft-365-defender"></a>Ofte stillede spørgsmål ved aktivering af Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Læs svar på de oftest stillede spørgsmål om aktivering [af Microsoft 365 Defender](microsoft-365-defender.md) herunder nødvendige licenser og tilladelser, implementering af supporttjenester og indledende indstillinger.

Du kan finde en vejledning til, hvordan du slår tjenesten [til, ved at læse Microsoft 365 Defender](m365d-enable.md).

## <a name="i-dont-have-a-microsoft-365-e5-license-can-i-still-use-microsoft-365-defender"></a>Jeg har ikke en Microsoft 365 E5 licens. Kan jeg stadig bruge Microsoft 365 Defender?

Kunder med følgende ikke-E5-licenser kan bruge Microsoft 365 Defender:

- Microsoft Defender til Slutpunkt
- Microsoft Defender for Identity
- Microsoft Defender til skyapps
- Defender for Office 365 (Plan 2)

Læs licenskravene for at få en [komplet liste over understøttede licenser](prerequisites.md#licensing-requirements).

## <a name="do-i-need-to-install-or-deploy-anything-to-start-using-microsoft-365-defender"></a>Skal jeg installere eller installere noget for at begynde at bruge Microsoft 365 Defender?

Nej, Microsoft 365 Defender konsoliderer data fra Microsoft 365, du allerede har installeret. Når du har aktiveret den, begynder hændelser, automatisering og jagtoplevelser at virke inden for rammerne af de installerede produkter. Hvis ingen af disse produkter er installeret korrekt, viser Microsoft 365 Defender ikke nogen data og kan ikke gøre noget.

Hvis du vil optimere Microsoft 365 Defender brugeroplevelser, anbefaler vi *, at du* installerer alle [understøttede Microsoft 365 og -sikkerhedsprodukter og -tjenester](deploy-supported-services.md).

## <a name="where-does-microsoft-365-defender-process-and-store-my-data"></a>Hvor kan Microsoft 365 Defender behandle og gemme mine data?

Microsoft 365 Defender vælger automatisk en optimal placering til datacenteret, hvor konsoliderede data behandles og gemmes. Hvis du har Microsoft Defender til slutpunkt, vælger det den samme placering, som bruges af Defender til slutpunkt.

>[!NOTE]
>Microsoft Defender til Slutpunkt indsættes automatisk i EU-datacentre, når det er slået til via Microsoft Defender for Cloud. Microsoft 365 Defender bliver automatisk klargjort i det samme EU-datacenter for kunder, der har klargjort Microsoft Defender til slutpunkt på denne måde.

Datacenterplaceringen vises før og efter, tjenesten er klargjort på siden med indstillinger for Microsoft 365 Defender (**Indstillinger > Microsoft 365 Defender**). Hvis du foretrækker at bruge en anden datacenterplacering, skal du **vælge Har** du brug for hjælp? Microsoft 365 Defender-portalen for at kontakte Microsoft Support.

## <a name="where-can-i-access-microsoft-365-defender"></a>Hvor kan jeg få adgang Microsoft 365 Defender?

Microsoft 365 Defender findes på: <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a>.

## <a name="what-permissions-do-i-need-to-access-microsoft-365-defender"></a>Hvilke tilladelser skal jeg have for at få adgang til Microsoft 365 Defender?

Konti, der er tildelt Azure Active Directory (Azure AD) kan få adgang Microsoft 365 Defender funktioner og data:

- Global administrator
- Sikkerhedsadministrator
- Sikkerhedsoperator
- Global læser
- Sikkerhedslæser
- Overholdelsesadministrator
- Dataadministrator for overholdelse af regler og standarder
- Programadministrator
- Administrator for skyprogram


> [!NOTE]
> Rollebaserede indstillinger for adgangskontrol i Microsoft Defender til slutpunkt påvirker adgang til data. Du kan få mere at vide ved at [læse om administration af adgang Microsoft 365 Defender](m365d-permissions.md).

## <a name="what-time-zone-does-microsoft-365-defender-default-to"></a>Hvilken tidszone er Microsoft 365 Defender som standard?

Som standard Microsoft 365 Defender oplysninger om tid i UTC-tidszonen. Du kan ændre denne indstilling for at bruge din lokale tidszone. [Få mere at vide om at angive tidszonen](m365d-time-zone.md)

## <a name="how-can-i-learn-about-new-microsoft-365-defender-feature-and-ui-updates"></a>Hvordan kan jeg få mere at vide om de Microsoft 365 Defender funktioner og opdateringer til brugergrænsefladen?

Microsoft leverer jævnligt oplysninger via de forskellige kanaler, herunder:

- [Meddelelsescenter](../../admin/manage/message-center.md) i Microsoft 365 Administration
- Blogindlæg i Microsoft 365 [og & community'et for overholdelse af regler og standarder](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/bg-p/securityprivacycompliance)

Få de nyeste offentligt tilgængelige oplevelser ved at slå visningsfunktioner [til](preview.md).

## <a name="related-topics"></a>Relaterede emner

- [Microsoft 365 Defender oversigt](microsoft-365-defender.md)
- [Slå Microsoft 365 Defender til](m365d-enable.md).
- [Licenskrav og andre forudsætninger](prerequisites.md)
- [Installér understøttede tjenester](deploy-supported-services.md)
- [Slå visningsfunktioner til](preview.md)
