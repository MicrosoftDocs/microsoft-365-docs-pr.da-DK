---
title: Optimer og ret sikkerhedspolitikker med konfigurationsanalyse
description: Trinnene til optimering og rettelse af sikkerhedspolitikker med konfigurationsanalyse. Konfigurationsanalyse er en central placering og en enkelt glasrude til administration og visning af de mailsikkerhedspolitikker, du har konfigureret i din lejer.
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
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: dcb40c0abd619291da2f05fdfa362c03f853181e
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842448"
---
# <a name="optimize-and-correct-security-policies-with-configuration-analyzer"></a>Optimer og ret sikkerhedspolitikker med konfigurationsanalyse

Konfigurationsanalyse er en central placering og en enkelt glasrude til administration og visning af de mailsikkerhedspolitikker, du har konfigureret i din lejer. Du kan udføre en side-til-side-sammenligning af dine indstillinger med vores Anbefalede Standard- og Strict-indstillinger, anvende anbefalinger og få vist historiske ændringer, der påvirkede din arbejdsstilling.

## <a name="what-youll-need"></a>Det skal du bruge
- Microsoft Defender for Office 365 Plan 1
- Tilstrækkelige tilladelser (rolle som sikkerhedsadministrator)
- 5 minutter til at udføre nedenstående trin.

## <a name="compare-settings-and-apply-recommendations"></a>Sammenlign indstillinger, og anvend anbefalinger
1. Gå til [https://security.microsoft.com/configurationAnalyzer](https://security.microsoft.com/configurationAnalyzer).
1. Vælg enten **Standardanbefalinger** eller **Strenge anbefalinger** i den øverste menu baseret på den side til side-sammenligning, du vil foretage.
1. Anbefalinger for politikændringer vises. (Hvis relevant)
1. Du kan derefter vælge en anbefaling, notere dig den anbefalede handling, den politik, som anbefalingen gælder for, indstillingsnavn & aktuel konfiguration osv.
1. Når du har valgt en anbefaling, kan du trykke på **Anvend anbefaling** og derefter på **OK** i den bekræftelsesmeddelelse, der vises.
1. Hvis du vil redigere en politik manuelt eller bekræfte indstillingerne direkte i politikken, kan du trykke på **Vis politik** i stedet for **Anvend anbefaling** , som indlæser en ny fane og fører dig direkte til den pågældende politik for nemheds vedkommende.

## <a name="view-historical-configuration-changes"></a>Få vist historiske konfigurationsændringer

I **Konfigurationsanalyse** kan du vælge **Konfigurationsdriftsanalyse og -historik** på den øverste menulinje.

Den side, der indlæses, viser dig ændringerne af dine sikkerhedspolitikker inden for den tidsramme, der er valgt af filtrene, sammen med data om ændringen, og om den er steget eller reduceret din samlede arbejdsstilling.

Hvis du vil vide mere om Konfigurationsanalyse, skal du se [Konfigurationsanalyse for sikkerhedspolitikker – Office 365 | Microsoft Docs](../../office-365-security/configuration-analyzer-for-security-policies.md).
