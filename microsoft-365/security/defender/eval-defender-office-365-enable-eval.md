---
title: Aktivér evalueringsmiljøet for Microsoft Defender for Office 365 i produktionsmiljøet
description: Trin til aktivering af Microsoft Defender for Office 365 evaluering med prøvelicenser, håndtering af MX-poster & overvågning af accepterede domæner og indgående forbindelser.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 07/01/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: f3298c67421dea921a014bc32e91be8033733183
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750094"
---
# <a name="enable-the-evaluation-environment"></a>Aktivér evalueringsmiljøet

**Gælder for:**
- Microsoft 365 Defender

Denne artikel er [trin 2 af 3](eval-defender-office-365-overview.md) i processen med at konfigurere evalueringsmiljøet for Microsoft Defender for Office 365. Du kan få flere oplysninger om denne proces i [oversigtsartiklen](eval-defender-office-365-overview.md).

Brug følgende trin til at aktivere evalueringen af Microsoft Defender for Office 365.

:::image type="content" source="../../media/defender/m365-defender-office-eval-enable-steps.png" alt-text="Trinnene til aktivering af Microsoft Defender for Office 365 i Microsoft Defender-evalueringsmiljøet" lightbox="../../media/defender/m365-defender-office-eval-enable-steps.png":::


- [Trin 1: Aktivér prøvelicenser](#step-1-activate-trial-licenses)
- [Trin 2: Overvåg og bekræft den offentlige MX-post](#step-2-audit-and-verify-the-public-mx-record)
- [Trin 3: Overvåg accepterede domæner](#step-3-audit-accepted-domains)
- [Trin 4: Overvåg indgående connectors](#step-4-audit-inbound-connectors)
- [Trin 5: Aktivér evalueringen](#step-5-activate-the-evaluation)

## <a name="step-1-activate-trial-licenses"></a>Trin 1: Aktivér prøvelicenser

Log på dit eksisterende Microsoft Defender for Office 365 miljø eller lejeradministrationsportal.

1. Gå til administrationsportalen.
2. Vælg Køb tjenester på hurtig start.

   :::image type="content" source="../../media/mdo-eval/1_m365-purchase-services.png" alt-text="Indstillingen Køb tjenester, der skal klikkes på i Microsoft 365 Administration" lightbox="../../media/mdo-eval/1_m365-purchase-services.png":::

3. Rul ned til sektionen Add-On (eller søg efter "Defender") for at finde de Microsoft Defender for Office 365 planer.
4. Klik på Detaljer ud for den plan, du vil evaluere.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="Knappen Detaljer, der skal klikkes på" lightbox="../../media/mdo-eval/2_mdo-eval-license-details.png":::

5. Klik på linket *Start gratis prøveversion* .

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Linket Start gratis prøveversion" lightbox="../../media/mdo-eval/3-m365-purchase-button.png":::

6. Bekræft din anmodning, og klik på knappen *Prøv nu* .

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Knappen Prøv nu" lightbox="../../media/mdo-eval/4_mdo-trial-order.png":::

## <a name="step-2-audit-and-verify-the-public-mx-record"></a>Trin 2: Overvåg og bekræft den offentlige MX-post

Hvis du vil evaluere Microsoft Defender for Office 365 effektivt, er det vigtigt, at indgående eksterne mails videresendes via den Exchange Online Protection (EOP)-forekomst, der er knyttet til din lejer.

1. Log på M365 Administration Portal, udvid Indstillinger, og vælg Domæner.
2. Vælg dit bekræftede maildomæne, og klik på Administrer DNS.
3. Notér den MX-post, der er genereret og tildelt din EOP-lejer.
4. Få adgang til din eksterne (offentlige) DNS-zone, og kontrollér den primære MX-post, der er knyttet til dit maildomæne.
    - *Hvis din offentlige MX-post i øjeblikket stemmer overens med den tildelte EOP-adresse (f.eks. tenant-com.mail.protection.outlook.com), skal der ikke kræves yderligere ændringer af distributionen*.
    - Hvis din offentlige MX-post i øjeblikket fortolkes som en SMTP-gateway fra tredjepart eller i det lokale miljø, kan der være behov for yderligere konfigurationer af routing.
    - Hvis din offentlige MX-post i øjeblikket omsættes til Exchange i det lokale miljø, er du måske stadig i en hybridmodel, hvor nogle modtagerpostkasser endnu ikke er blevet overført til EXO.

## <a name="step-3-audit-accepted-domains"></a>Trin 3: Overvåg accepterede domæner

1. Log på Exchange Online Administration-portalen, vælg Mailflow, og klik derefter på Accepterede domæner.
2. På listen over accepterede domæner, der er blevet tilføjet og bekræftet i din lejer, skal du notere **dig domænetypen** for dit primære maildomæne.
    - Hvis domænetypen er angivet til ***Autoritativ***, antages det, at alle modtagerpostkasser for din organisation aktuelt er placeret i Exchange Online.
    - Hvis domænetypen er angivet til ***Intern relæ*** , er du måske stadig i en hybridmodel, hvor nogle modtagerpostkasser stadig er placeret i det lokale miljø.

## <a name="step-4-audit-inbound-connectors"></a>Trin 4: Overvåg indgående connectors

1. Log på Exchange Online Administration-portalen, vælg Mailflow, og klik derefter på Forbindelser.
2. På listen over konfigurerede connectors skal du notere eventuelle poster, der er fra **Partnerorganisation** og kan korrelere med en SMTP-gateway fra tredjepart.
3. På listen over konfigurerede connectors skal du notere eventuelle poster, der **er mærket Fra organisationens mailserver** , hvilket kan indikere, at du stadig er i hybridscenarie.

## <a name="step-5-activate-the-evaluation"></a>Trin 5: Aktivér evalueringen

Brug vejledningen her til at aktivere din Microsoft Defender for Office 365 evaluering fra Microsoft 365 Defender-portalen.

1. Log på din lejer med en konto, der har adgang til Microsoft 365 Defender-portalen.
2. Vælg, om du vil gøre **Microsoft 365 Defender-portalen** til standardgrænsefladen for Microsoft Defender for Office 365 administration (anbefales).

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-activate-eval.png" alt-text="Knappen Slå til i Indstillinger fører til en centraliseret og forbedret Microsoft 365 Defender portal til administration" lightbox="../../media/mdo-eval/1_mdo-eval-activate-eval.png":::

3. I navigationsmenuen skal du vælge **Politikker & Regler** under *Mail & Samarbejde*.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-activate-eval.png" alt-text="Menupunktet Politikker & regler, der skal klikkes på" lightbox="../../media/mdo-eval/2_mdo-eval-activate-eval.png":::

4. Klik på **Trusselspolitikker** på dashboardet *Politik & regler*.

   :::image type="content" source="../../media/mdo-eval/3_mdo-eval-activate-eval.png" alt-text="Menupunktet Trusselspolitikker, der skal klikkes på" lightbox="../../media/mdo-eval/3_mdo-eval-activate-eval.png":::

5. Rul ned til *Yderligere politikker,* og vælg feltet **Evaluer Defender for Office 365**.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-activate-eval.png" alt-text="Feltet Evaluering Defender for Office 365" lightbox="../../media/mdo-eval/4_mdo-eval-activate-eval.png":::

6. Vælg nu, om eksterne mails distribueres til Exchange Online direkte eller til en gateway eller tjeneste fra tredjepart, og klik på Næste.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-activate-eval.png" alt-text="Ruden Distributionsindstillinger på Microsoft Defender for Office 365-portalen" lightbox="../../media/mdo-eval/5_mdo-eval-activate-eval.png":::

7. Hvis du bruger en gateway fra tredjepart, skal du vælge leverandørnavnet på rullelisten sammen med den indgående connector, der er knyttet til den pågældende løsning. Klik på Næste, når du har angivet dine svar.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png" alt-text="Ruden Indstillinger for tredjepart eller det lokale miljø på Microsoft Defender for Office 365-portalen" lightbox="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png":::

8. Gennemse indstillingerne, og klik på knappen **Opret evaluering** .

   |Før|Efter|
   |:---:|:---:|
   |:::image type="content" source="../../media/mdo-eval/7-mdo-eval-activate-review.png" alt-text="Ruden Gennemse dine indstillinger på Microsoft Defender for Office 365-portalen" lightbox="../../media/mdo-eval/7-mdo-eval-activate-review.png":::|:::image type="content" source="../../media/mdo-eval/8-mdo-eval-activate-complete.png" alt-text="Meddelelse om fuldførelse af evalueringskonfiguration på Microsoft Defender for Office 365-portalen" lightbox="../../media/mdo-eval/8-mdo-eval-activate-complete.png":::|
   |

## <a name="next-steps"></a>Næste trin

Trin 3 af 3: Konfigurer piloten til Microsoft Defender for Office 365

Vend tilbage til oversigten for [Evaluate Microsoft Defender for Office 365](eval-defender-office-365-overview.md)

Vend tilbage til oversigten for [Evaluate og pilot Microsoft 365 Defender](eval-overview.md)
