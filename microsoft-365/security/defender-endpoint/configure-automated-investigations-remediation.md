---
title: Konfigurer automatiseret undersøgelse og afhjælpningsfunktioner
description: Konfigurer din automatiske undersøgelse og afhjælpningsfunktioner i Microsoft Defender til Slutpunkt.
keywords: konfigurer, konfiguration, automatiseret, undersøgelse, registrering, beskeder, afhjælpning, svar
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
ms.date: 01/27/2021
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.openlocfilehash: f8416d480731c133e93a0a6e22e5b5b32913ba57
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63603060"
---
# <a name="configure-automated-investigation-and-remediation-capabilities-in-microsoft-defender-for-endpoint"></a>Konfigurer automatiseret undersøgelse og afhjælpningsfunktioner i Microsoft Defender til Slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Hvis din organisation bruger [Microsoft Defender til Slutpunkt](/windows/security/threat-protection/) (Defender til [Slutpunkt), kan](/microsoft-365/security/defender-endpoint/automated-investigations) automatiseret undersøgelse og afhjælpning spare tid og besvær for dit sikkerhedsteam. Som beskrevet i dette [blogindlæg efterligner](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/enhance-your-soc-with-microsoft-defender-atp-automatic/ba-p/848946) disse funktioner de ideelle trin, som en sikkerhedsanalytiker tager for at undersøge og afhjælpe trusler. [Få mere at vide om automatiseret undersøgelse og afhjælpning](/microsoft-365/security/defender-endpoint/automated-investigations).

Sådan konfigureres automatiseret undersøgelse og afhjælpning:

1. [Slå funktionerne til](#turn-on-automated-investigation-and-remediation). og
2. [Konfigurer enhedsgrupper](#set-up-device-groups).

## <a name="turn-on-automated-investigation-and-remediation"></a>Slå automatiseret undersøgelse til og afhjælpning til

1. Som global administrator eller sikkerhedsadministrator skal du gå til Microsoft 365 Defender -portalen (<https://security.microsoft.com>) og logge på.
2. I navigationsruden skal du **vælge Indstillinger**.
3. I sektionen **Generelt** skal du vælge **Avancerede funktioner**.
4. Aktiver både **automatisk undersøgelse** **og Automatisk løsning af beskeder**.

## <a name="set-up-device-groups"></a>Konfigurer enhedsgrupper

1. I Microsoft 365 Defender (<https://security.microsoft.com>) på siden **Indstillinger** under Tilladelser **skal** du vælge **Enhedsgrupper**.
2. Vælg **+ Tilføj enhedsgruppe**.
3. Opret mindst én enhedsgruppe på følgende måde:
   - Angiv et navn og en beskrivelse af enhedsgruppen.
   - På listen **Automatiseringsniveau skal** du vælge et niveau, f.eks. **Fuld – afhjælpe trusler automatisk**. Automatiseringsniveauet afgør, om afhjælpningshandlinger skal løses automatisk eller kun efter godkendelse. Du kan få mere at vide [under Automatiseringsniveauer i automatiseret undersøgelse og afhjælpning](automation-levels.md).
   - I sektionen **Medlemmer** skal du bruge en eller flere betingelser til at identificere og inkludere enheder.
   - På fanen **Brugeradgang** skal du vælge de [Azure Active Directory grupper](/azure/active-directory/fundamentals/active-directory-manage-groups?context=azure/active-directory/users-groups-roles/context/ugr-context), der skal have adgang til den enhedsgruppe, du opretter.
4. Vælg **Udført** , når du er færdig med at konfigurere din enhedsgruppe.

## <a name="next-steps"></a>Næste trin

- [Gå til Handlingscenter for at få vist afventende og fuldførte afhjælpningshandlinger](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
- [Gennemse og godkende afventende handlinger](/microsoft-365/security/defender-endpoint/manage-auto-investigation)

## <a name="see-also"></a>Se også

- [Adressere falske positive/negativer i Microsoft Defender til slutpunkt](defender-endpoint-false-positives-negatives.md)
