---
title: Sådan aktiverer du DMARC-rapportering for MOERA (Microsoft Online Email Routing Address) og parkerede domæner
description: Trinnene til konfiguration af DMARC for MOERA og parkerede domæner.
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
ms.openlocfilehash: dbe994ee0cba90f37acf7dcbd92c3b0d81d673a3
ms.sourcegitcommit: a209c9f86a7b4340a426c4cfed2d36a388c71124
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66859007"
---
# <a name="how-to-enable-dmarc-reporting-for-microsoft-online-email-routing-address-moera-and-parked-domains"></a>Sådan aktiverer du DMARC-rapportering for MOERA (Microsoft Online Email Routing Address) og parkerede domæner

Bedste praksis for beskyttelse af domænemailsikkerhed er at beskytte dig selv mod spoofing ved hjælp af domænebaseret meddelelsesgodkendelse, rapportering og overensstemmelse (DMARC). Hvis du ikke allerede har aktiveret DMARC for dine domæner, bør det være det første trin, der beskrives her: [Domænebaseret meddelelsesgodkendelse, rapportering og overensstemmelse (DMARC)](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)

Denne vejledning er designet til at hjælpe dig med at konfigurere DMARC for de domæner, der ikke er omfattet af ovenstående vejledning, både din Microsoft Online Email Routing Address (MOERA) dvs. contosocorp.onmicrosoft.com og parkerede domæner, som du muligvis ikke bruger til mail endnu, men som kan udnyttes af hackere, indtil de er beskyttet.

## <a name="what-youll-need"></a>Det skal du bruge

- Microsoft 365 Administration og adgang til din DNS-udbyder, der hoster dine domæner
- Tilstrækkelige tilladelser som Global Administration til at foretage de nødvendige ændringer i Microsoft 365 Administration Center
- 10 minutter til at fuldføre følgende trin

## <a name="activate-dmarc-for-moera-domain"></a>Aktivér DMARC for MOERA-domæne

1. Log på [Microsoft 365 Administration Center](https://admin.microsoft.com).
1. Vælg **Vis alle** i navigationen til venstre.
1. Udvid Indstillinger, og tryk på **Domæner**.
1. Vælg dit lejerdomæne (contoso.onmicrosoft.com).
1. Vælg **DNS-poster** på den side, der indlæses.
1. Vælg **+ Tilføj post**.
1. Der vises et pop op-vindue til højre. Kontrollér, at den valgte type er **TXT (Text)**.
1. Tilføj _dmarc som TXT-navn.
1. Tilføj din specifikke DMARC-værdi.
1. Tryk på **Gem**.

## <a name="active-dmarc-for-parked-domains"></a>Aktiv DMARC for parkerede domæner

1. Kontrollér, om SPF allerede er konfigureret for dit parkerede domæne, ved at følge denne vejledning: [Konfigurer SPF for at forhindre spoofing – Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing#how-to-handle-subdomains)
1. Kontakt din DNS-domæneudbyder.
1. Bed om at tilføje denne DMARC txt-post med de relevante mailadresser `v=DMARC1; p=reject; rua=mailto:d@rua.contoso.com;ruf=mailto:d@ruf.contoso.com`.

## <a name="next-steps"></a>Næste trin

Vent, indtil DNS-ændringerne overføres, og prøv at spoof de konfigurerede domæner. Kontrollér, om forsøget er blokeret baseret på DMARC-posten, og du modtager en DMARC-rapport.

## <a name="more-information"></a>Flere oplysninger

[Konfigurer SPF for at forhindre spoofing – Office 365 | ](/microsoft-365/security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing)
 Microsoft Docs [Brug DMARC til at validere mail, konfigurationstrin – Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)
