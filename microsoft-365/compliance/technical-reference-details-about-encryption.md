---
title: Tekniske referenceoplysninger om kryptering
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
- Strat_O365_IP
search.appverid:
- MET150
- MOE150
ms.assetid: 862cbe93-4268-4ef9-ba79-277545ecf221
description: Få mere at vide om de forskellige certifikater, teknologier og TLS-pakker (Transport Layer Security), der bruges til kryptering i Office 365 og Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6b5df1f9e983ab2e8add09b50c2dfbd30dc1243e
ms.sourcegitcommit: 2a4dddf7c655b44b17d4fd7f5e1e5d8a6e2b7aef
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/06/2021
ms.locfileid: "63587722"
---
# <a name="technical-reference-details-about-encryption"></a>Tekniske referenceoplysninger om kryptering

Se denne artikel for at få mere at vide om certifikater, teknologier og TLS-krypteringspakker, der bruges til [kryptering Office 365](encryption.md). Denne artikel indeholder også oplysninger om planlagte udrådninger.
  
- Hvis du leder efter oversigtsoplysninger, skal du se [Kryptering i Office 365](encryption.md).
- Hvis du leder efter konfigurationsoplysninger, skal du se [Konfigurer kryptering i Office 365 Enterprise](set-up-encryption.md).
- Du kan finde oplysninger om kryptering af pakker, der understøttes af bestemte versioner af Windows, under [Cipher-pakker i TLS/SSL (Schannel SSP)](/windows/desktop/SecAuthN/cipher-suites-in-schannel).

## <a name="microsoft-office-365-certificate-ownership-and-management"></a>Microsoft Office 365 ejerskab af certifikat og administration

Du behøver ikke at købe eller vedligeholde certifikater til Office 365. I stedet Office 365 bruge sine egne certifikater.
  
## <a name="current-encryption-standards-and-planned-deprecations"></a>Aktuelle krypteringsstandarder og planlagte udrådninger

Hvis du vil levere førsteklasses kryptering, gennemgår Office 365 regelmæssigt understøttede krypteringsstandarder. Nogle gange frarådes gamle standarder, når de bliver forældede og mindre sikre. I denne artikel beskrives de aktuelt understøttede krypteringspakker og andre standarder og detaljer om planlagte udfald.

## <a name="fips-compliance-for-office-365"></a>FIPS-overholdelse for Office 365

Alle krypterede pakker, der understøttes Office 365 bruger algoritmer, som er acceptable under FIPS 140-2. Office 365 nedarver FIPS-valideringer Windows (via Schannel). Du kan finde oplysninger om [Schannel under Cipher-pakker i TLS/SSL (Schannel SSP)](/windows/desktop/SecAuthN/cipher-suites-in-schannel).
  
## <a name="versions-of-tls-supported-by-office-365"></a>Versioner af TLS, der understøttes af Office 365

TLS og SSL, der kom før TLS, er krypterede protokoller, der sikrer kommunikationen via et netværk ved hjælp af sikkerhedscertifikater til at kryptere en forbindelse mellem computere. Office 365 understøtter TLS version 1.2 (TLS 1.2).

TLS version 1.3 (TLS 1.3) understøttes af nogle af tjenesterne.

> [!IMPORTANT]
> Vær opmærksom på, at forældet TLS-versioner er forældet, og at forældet *versioner ikke* bør bruges, når der er nyere versioner tilgængelige. Hvis dine ældre tjenester ikke kræver TLS 1.0 eller 1.1, bør du deaktivere dem.
  
## <a name="support-for-tls-10-and-11-deprecation"></a>Understøttelse af udrådning af TLS 1.0 og 1.1

Office 365 stoppet understøttelsen af TLS 1.0 og 1.1 d. 31. oktober 2018. Vi har fuldført deaktivering af TLS 1.0 og 1.1 i GCC High- og DoD-miljøer. Vi begyndte at deaktivere TLS 1.0 og 1.1 for Worldwide- og GCC-miljøer fra d. 15. oktober 2020 og vil fortsætte med udrulning i løbet af de næste uger og måneder.

For at bevare en sikker forbindelse til Office 365- og Microsoft 365-tjenester bruger alle klientserver- og browserserverkombinationer TLS 1.2 og moderne krypteringspakker. Du skal muligvis opdatere visse kombinationer af klientserver og browserserver. Du kan finde oplysninger om, hvordan denne ændring påvirker dig, under Forberedelse til obligatorisk brug af [TLS 1.2 Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).
  
## <a name="deprecating-support-for-3des"></a>Fraråde understøttelse af 3DES

Siden d. 31. oktober 2018 Office 365 ikke længere brugen af 3DES-krypteringspakker til kommunikation Office 365. Mere specifikt understøtter Office 365 ikke længere TLS_RSA_WITH_3DES_EDE_CBC_SHA cipher-pakken. Siden d. 28. februar 2019 er denne krypteringspakke blevet deaktiveret Office 365. Klienter og servere, der kommunikerer Office 365 klientservere, skal understøtte en eller flere af de understøttede krypteringsservere. Du kan finde en liste over understøttede krypteringer i [TLS-kodepakker, der understøttes Office 365](#tls-cipher-suites-supported-by-office-365).
  
## <a name="deprecating-sha-1-certificate-support-in-office-365"></a>Fraråding af understøttelse af SHA-1-certifikat i Office 365

Siden juni 2016 Office 365 et SHA-1-certifikat for udgående eller indgående forbindelser. Brug SHA-2 (Secure Hash Algorithm 2) eller en stærkere hashing-algoritme i certifikatkæden.
  
## <a name="tls-cipher-suites-supported-by-office-365"></a>TLS-krypteringspakker, der understøttes af Office 365

TLS bruger *krypteringspakker, samlinger* af krypteringsalgoritmer, til at oprette sikre forbindelser. Office 365 understøtter de krypteringspakker, der er angivet i følgende tabel. Tabellen viser de krypterede pakker i styrkerækkefølgen med den stærkeste krypteringspakke først.

Office 365 besvarer en forbindelsesanmodning ved først at forsøge at oprette forbindelse ved hjælp af den mest sikre krypteringspakke. Hvis forbindelsen ikke virker, forsøger Office 365 den anden mest sikre kodepakke på listen osv. Tjenesten fortsætter ned ad listen, indtil forbindelsen er blevet accepteret. På samme måde Office 365 anmode om en forbindelse, vælger den modtagende tjeneste, om TLS skal bruges, og hvilken cipherpakke der skal bruges.

| Navnet på Cipher-pakken | Nøgleudvekslingsalgoritme/-styrke | Fremadskedt | Cipher/styrke | Godkendelsesalgoritme/-styrke |
|:-----|:-----|:-----|:-----|:-----|
| TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384  <br/> | ECDH/192  <br/> | Ja  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256  <br/> | ECDH/128  <br/> | Ja  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384  <br/> | ECDH/192  <br/> | Ja  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256  <br/> | ECDH/128  <br/> | Ja  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA     <br/> | ECDH/192  <br/> | Ja  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA     <br/> | ECDH/128  <br/> | Ja  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS_RSA_WITH_AES_256_GCM_SHA384        <br/> | RSA/112   <br/> | Nej   <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_RSA_WITH_AES_128_GCM_SHA256        <br/> | RSA/112   <br/> | Nej   <br/> | AES/256  <br/> | RSA/112  <br/> |

De følgende krypterede pakker understøttede TLS 1.0- og 1.1-protokoller indtil udrådingsdatoen. For GCC høj- og dod-miljøer var forfaldsdatoen 15. januar 2020. For worldwide and GCC environments that date was October 15, 2020.

| Protokoller | Navnet på Cipher-pakken | Nøgleudvekslingsalgoritme/-styrke | Fremadskedt | Cipher/styrke | Godkendelsesalgoritme/-styrke | 
|:-----|:-----|:-----|:-----|:-----|:-----|
| TLS 1.0, 1.1, 1.2  <br/> | TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA  <br/> | ECDH/192  <br/> | Ja  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA  <br/> | ECDH/128  <br/> | Ja  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_RSA_WITH_AES_256_CBC_SHA        <br/> | RSA/112   <br/> | Nej   <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_RSA_WITH_AES_128_CBC_SHA        <br/> | RSA/112   <br/> | Nej   <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_RSA_WITH_AES_256_CBC_SHA256     <br/> | RSA/112   <br/> | Nej   <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_RSA_WITH_AES_128_CBC_SHA256     <br/> | RSA/112   <br/> | Nej   <br/> | AES/256  <br/> | RSA/112  <br/> |

Visse Office 365 produkter (herunder Microsoft Teams) [bruger Azure Front Door](/azure/frontdoor/front-door-overview) til at afslutte TLS-forbindelser og dirigere netværkstrafik effektivt. Mindst én af de [krypteringspakker, der understøttes af Azure Front Door over TLS 1.2](/azure/frontdoor/front-door-faq#what-are-the-current-cipher-suites-supported-by-azure-front-door-) , skal være aktiveret for at kunne oprette forbindelse til disse produkter. Til Windows 10 og derover anbefaler vi, at du aktiverer en eller begge ECDHE-krypteringspakker for bedre sikkerhed. Windows 7, 8 og 8.1 ikke er kompatible med Azure Front Doors ECDHE-krypteringspakker og DHE-krypteringspakkerne er leveret med henblik på kompatibilitet med disse operativsystemer.

## <a name="related-articles"></a>Relaterede artikler

[TLS Cipher-pakker i Windows 10 v1903](/windows/win32/secauthn/tls-cipher-suites-in-windows-10-v1903)

[Kryptering i Office 365](encryption.md)
  
[Konfigurer kryptering i Office 365 Enterprise](set-up-encryption.md)
  
[Schannel-implementering af TLS 1.0 Windows sikkerhedsstatusopdatering: 24. november 2015](https://support.microsoft.com/kb/3117336)
  
[TLS/SSL-krypterede forbedringer (Windows IT-center)](/previous-versions/windows/it-pro/windows-vista/cc766285(v=ws.10))
  
[Forberedelse til TLS 1.2 i Office 365 og Office 365 GCC](/office365/troubleshoot/security/prepare-tls-1.2-in-office-365)

[Hvad understøttes de aktuelle krypteringspakker af Azure Front Door?](/azure/frontdoor/front-door-faq#what-are-the-current-cipher-suites-supported-by-azure-front-door-)
