---
title: Konfigurer automatiserede undersøgelses- og afhjælpningsfunktioner
description: Konfigurer dine automatiserede undersøgelses- og afhjælpningsfunktioner i Microsoft Defender for Endpoint.
keywords: konfigurere, konfigurere, automatiseret, undersøgelse, registrering, beskeder, afhjælpning, svar
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.openlocfilehash: c82962640f992f892e21205dcfc0725a79001f10
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437868"
---
# <a name="configure-automated-investigation-and-remediation-capabilities-in-microsoft-defender-for-endpoint"></a>Konfigurer automatiserede undersøgelses- og afhjælpningsfunktioner i Microsoft Defender for Endpoint

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Hvis din organisation bruger [Microsoft Defender for Endpoint](/windows/security/threat-protection/) (Defender for Endpoint), kan [automatiserede undersøgelses- og afhjælpningsfunktioner](/microsoft-365/security/defender-endpoint/automated-investigations) spare tid og kræfter på dit sikkerhedsteam. Som beskrevet i [dette blogindlæg](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/enhance-your-soc-with-microsoft-defender-atp-automatic/ba-p/848946) efterligner disse funktioner de ideelle trin, som en sikkerhedsanalytiker tager for at undersøge og afhjælpe trusler. [Få mere at vide om automatiseret undersøgelse og afhjælpning](/microsoft-365/security/defender-endpoint/automated-investigations).

Sådan konfigurerer du automatiseret undersøgelse og afhjælpning:

1. [Slå funktionerne til](#turn-on-automated-investigation-and-remediation). Og
2. [Konfigurer enhedsgrupper](#set-up-device-groups).

## <a name="turn-on-automated-investigation-and-remediation"></a>Slå automatiseret undersøgelse og afhjælpning til

1. Som global administrator eller sikkerhedsadministrator skal du gå til Microsoft 365 Defender-portalen (<https://security.microsoft.com>) og logge på.
2. Vælg **Indstillinger** i navigationsruden.
3. Vælg **Slutpunkter**, og vælg derefter **Avancerede funktioner**.
4. Aktivér både **Automatiseret undersøgelse** og **Automatisk løsning af beskeder**.

## <a name="set-up-device-groups"></a>Konfigurer enhedsgrupper

1. På Microsoft 365 Defender-portalen (<https://security.microsoft.com>) på siden **Indstillinger** under **Tilladelser** skal du vælge **Enhedsgrupper**.
2. Vælg **+ Tilføj enhedsgruppe**.
3. Opret mindst én enhedsgruppe på følgende måde:
   - Angiv et navn og en beskrivelse til enhedsgruppen.
   - Vælg et niveau på **listen Automatiseringsniveau**, f.eks **. Fuld – afhjælp automatisk trusler**. Automatiseringsniveauet bestemmer, om afhjælpningshandlinger udføres automatisk eller kun efter godkendelse. Du kan få mere at vide [under Automatiseringsniveauer i automatiseret undersøgelse og afhjælpning](automation-levels.md).
   - I afsnittet **Medlemmer** skal du bruge en eller flere betingelser til at identificere og inkludere enheder.
   - Under fanen **Brugeradgang** skal du vælge de [Azure Active Directory grupper](/azure/active-directory/fundamentals/active-directory-manage-groups?context=azure/active-directory/users-groups-roles/context/ugr-context), der skal have adgang til den enhedsgruppe, du opretter.
4. Vælg **Udført** , når du er færdig med at konfigurere din enhedsgruppe.

## <a name="next-steps"></a>Næste trin

- [Besøg Løsningscenter for at få vist ventende og fuldførte afhjælpningshandlinger](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
- [Gennemse og godkend ventende handlinger](/microsoft-365/security/defender-endpoint/manage-auto-investigation)

## <a name="see-also"></a>Se også

- [Adresser falske positive/negativer i Microsoft Defender for Endpoint](defender-endpoint-false-positives-negatives.md)
