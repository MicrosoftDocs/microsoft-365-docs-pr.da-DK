---
title: Bliv Microsoft Defender for Endpoint-partner
ms.reviewer: ''
description: Få mere at vide om trin og krav til integration af din løsning med Microsoft Defender til slutpunkt og bliv partner
keywords: partner, integration, løsningsvalidering, certificering, krav, medlem, fejl, programportal
ms.prod: w10
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
ms.openlocfilehash: b063d8435817d7dd64c3febf6e3399f3876ef894
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63603089"
---
# <a name="become-a-microsoft-defender-for-endpoint-partner"></a>Bliv Microsoft Defender for Endpoint-partner

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


For at blive Defender for Endpoint-løsningspartner skal du følge og udføre følgende trin.

## <a name="step-1-subscribe-to-a-microsoft-defender-for-endpoint-license"></a>Trin 1: Abonner på en Microsoft Defender for Endpoint-licens

Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink). Hvis du abonnerer, kan du bruge en Microsoft Defender for Endpoint-lejer med op til tre enheder til at udvikle løsninger, der integreres med Microsoft Defender til slutpunkt.

## <a name="step-2-fulfill-the-solution-validation-and-certification-requirements"></a>Trin 2: Opfylder løsningsvalideringen og certificeringskravene

Den bedste måde for teknologipartnere at bekræfte, at deres integrationsarbejde er at få en fælles kunde til at godkende det foreslåede integrationsdesign (kunden kan bruge Anbefal en **partnerindstilling**\(: Partnere og API >-partnerprogrammer\) på siden [Partnerprogram](https://security.microsoft.com/interoperability/partnersapps) i Microsoft 365 Defender og få det testet og demoeret til Microsoft Defender til slutpunktsteamet.

Når Microsoft Defender for Endpoint-teamet har gennemgået og godkendt integrationen, leder vi dig til at blive inkluderet som partner i Microsoft Intelligent Security Association.

## <a name="step-3-get-listed-in-the-microsoft-defender-for-endpoint-partner-application-portal"></a>Trin 3: Bliv vist på Microsoft Defender for Endpoint-partnerprogramportalen

Microsoft Defender til Slutpunkt understøtter registrering og integration af tredjepartsprogrammer ved hjælp af partnersiden i [](partner-applications.md) produktet, der er integreret i administrationsportalen for Microsoft Defender til Slutpunkt.

Hvis din virksomhed skal være angivet som partner på siden produktpartner, skal du angive følgende oplysninger:

1. Et firkantet logo (SVG).
2. Navnet på det produkt, der skal præsenteres.
3. Angiv en produktbeskrivelse på 15 ord.
4. Link til landingssiden, hvor kunden kan fuldføre integrations- eller blogindlægget, der indeholder tilstrækkelige oplysninger til kunderne. Enhver pressemeddelelse, herunder produktnavnet for Microsoft Defender til Slutpunkt, bør gennemgås af marketing- og teknikteamet. Vent mindst 10 dage, indtil gennemsynsprocessen er færdig.
5. Hvis du bruger en Azure AD-tilgang med flere lejere, skal vi bruge Azure AD-programnavnet til at registrere brugen af programmet.
6. Medtag User-Agent i hvert API-opkald, der foretages til offentlige API'er eller API'er Graph Microsoft Defender til slutpunkter. Dette bruges til statistiske formål, fejlfinding og partnergenkendelse. Dette trin er desuden et krav for medlemskab af Microsoft Intelligent Security Association (MISA).

   Følg disse trin:

   - Indstil feltet User-Agent HTTP-anmodning til nedenstående format.

     ```http
     MdePartner-{CompanyName}-{ProductName}/{Version}
     ```

     Eksempelvis Brugeragent:

     ```http
     MdePartner-Contoso-ContosoCognito/1.0.0
     ```

   - Få mere at vide under [RFC 2616 sektion-14.43](https://tools.ietf.org/html/rfc2616#section-14.43).

Partnerskab med Microsoft Defender til Slutpunkt hjælper vores fælles kunder med yderligere at strømline, integrere og styre forsvar. Vi er glade for, at du har valgt at blive Microsoft Defender for Endpoint-partner og at opnå vores fælles mål om effektivt at beskytte kunder og deres aktiver ved at forhindre og besvare moderne trusler sammen.

## <a name="misa-nomination"></a>MISA, der er tilsigtet 
Administrerede sikkerhedstjenesteudbydere (MSSP) og uafhængige softwareleverandører (ISV) kan udpeges til Microsoft Intelligent Security Association (MISA). Du kan finde flere oplysninger på [siden Med misa-oplysninger](https://www.microsoft.com/security/business/intelligent-security-association).


## <a name="related-topics"></a>Relaterede emner

- [Tekniske partnermuligheder](partner-integration.md)
