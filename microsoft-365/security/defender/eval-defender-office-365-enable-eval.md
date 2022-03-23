---
title: Aktivér evalueringsmiljøet for Microsoft Defender Office 365 dit produktionsmiljø
description: Trin til at aktivere Microsoft Defender Office 365 evaluering med prøvelicenser, håndtering af MX-poster, & overvågning af accepterede domæner og indgående forbindelser.
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
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: 4d2f77b41dccd5620b96d816869d7d7b6458a798
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63592293"
---
# <a name="enable-the-evaluation-environment"></a>Aktivér evalueringsmiljøet

**Gælder for:**
- Microsoft 365 Defender

Denne artikel er [trin 2 af 3 i](eval-defender-office-365-overview.md) oprettelsen af evalueringsmiljøet for Microsoft Defender til Office 365. Du kan finde flere oplysninger om denne proces i [oversigtsartikel](eval-defender-office-365-overview.md).

Brug følgende trin til at aktivere evalueringen af Microsoft Defender for Office 365.

![Trin til at aktivere Microsoft Defender Office 365 i Microsoft Defender-evalueringsmiljøet.](../../media/defender/m365-defender-office-eval-enable-steps.png)

- [Trin 1: Aktivér prøvelicenser](#step-1-activate-trial-licenses)
- [Trin 2: Overvåge og bekræfte den offentlige MX-post](#step-2-audit-and-verify-the-public-mx-record)
- [Trin 3: Overvåge accepterede domæner](#step-3-audit-accepted-domains)
- [Trin 4: Overhold indgående forbindelser](#step-4-audit-inbound-connectors)
- [Trin 5: Aktivér evalueringen](#step-5-activate-the-evaluation)

## <a name="step-1-activate-trial-licenses"></a>Trin 1: Aktivér prøvelicenser

Log på din eksisterende Microsoft Defender til Office 365-miljø eller lejeradministrationsportal.

1. Gå til administrationsportalen.
2. Vælg Køb tjenester fra hurtig start.

   :::image type="content" source="../../media/mdo-eval/1_m365-purchase-services.png" alt-text="Klik på Køb tjenester i navigationsruden Office 365.":::

3. Rul ned til sektionen Add-On (eller søg efter "Defender") for at finde Microsoft Defender til Office 365 planer.
4. Klik på Detaljer ud for den plan, du vil evaluere.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="Klik på knappen Detaljer, næste.":::

5. Klik på *linket Start gratis* prøveversion.

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Klik på linket Start gratis prøveversion *link* på dette panel.":::

6. Bekræft din anmodning, og klik *på knappen Prøv* nu.

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Klik nu på knappen Prøv nu *.":::

## <a name="step-2-audit-and-verify-the-public-mx-record"></a>Trin 2: Overvåge og bekræfte den offentlige MX-post

For effektivt at evaluere Microsoft Defender til Office 365 er det vigtigt, at indgående eksterne mails videresendes via den Exchange Online Protection (EOP)-forekomst, der er knyttet til din lejer.

1. Log på M365-administrationsportalen, udvid Indstillinger, og vælg Domæner.
2. Vælg dit bekræftede maildomæne, og klik på DNS-styring.
3. Noter den MX-post, der genereres og tildeles til din EOP-lejer.
4. Få adgang til din eksterne (offentlige) DNS-zone, og kontrollér den primære MX-post, der er knyttet til dit maildomæne.
    - *Hvis din offentlige MX-post aktuelt svarer til den tildelte EOP-adresse (f.eks. tenant-com.mail.protection.outlook.com), skal der ikke kræves yderligere routingændringer*.
    - Hvis din offentlige MX-post i øjeblikket løses til en tredjeparts- eller lokal SMTP-gateway, kan yderligere routingkonfigurationer være påkrævet.
    - Hvis din offentlige MX-post i øjeblikket løses til en lokal Exchange så er du muligvis stadig i en hybridmodel, hvor nogle modtagerpostkasser endnu ikke er blevet overført til EXO.

## <a name="step-3-audit-accepted-domains"></a>Trin 3: Overvåge accepterede domæner

1. Log på administrationsportalen Exchange Online mail, vælg Mail Flow, og klik derefter på Accepterede domæner.
2. På listen over accepterede domæner, der er blevet tilføjet og bekræftet i din lejer, skal du notere dig **domænetypen** for dit primære maildomæne.
    - Hvis domænetypen er angivet til ***Autoritativ***, antages det, at alle modtagerpostkasser for organisationen aktuelt befinder sig Exchange Online.
    - Hvis domænetypen er angivet til ***Intern*** videresendelse, kan du stadig være i en hybridmodel, hvor nogle modtagerpostkasser stadig er placeret lokalt.

## <a name="step-4-audit-inbound-connectors"></a>Trin 4: Overhold indgående forbindelser

1. Log på Exchange Online, vælg Mailadministrator Flow, og klik derefter på Forbindelser.
2. På listen over konfigurerede forbindelser skal du notere alle poster, der er fra **partnerorganisation** , og som kan korrelere med en SMTP-gateway fra en tredjepart.
3. På listen over konfigurerede forbindelser skal du notere dig alle poster med navnet Fra din  organisations mailserver, som kan betyde, at du stadig er i hybridscenariet.

## <a name="step-5-activate-the-evaluation"></a>Trin 5: Aktivér evalueringen

Følg vejledningen her for at aktivere din Microsoft Defender Office 365 din evaluering fra Microsoft 365 Defender portalen.

1. Log på din lejer med en konto, der har adgang til Microsoft 365 Defender portal.
2. Vælg, om du vil gøre **Microsoft 365 Defender-portalen** til din standardgrænseflade for Microsoft Defender Office 365 administration (anbefales).

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-activate-eval.png" alt-text="Klik på knappen Aktivér indstillinger for at bruge den centraliserede og Microsoft 365 Defender portal til administration.":::

3. I navigationsmenuen skal du **vælge Politikker & Regler** under *& samarbejde*.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-activate-eval.png" alt-text="Her er et billede af & mailsamarbejde, der peger på politikker & regler. Klik på det!":::

4. På *dashboardet Regler for & skal* du klikke på **Trusselspolitikker**.

   :::image type="content" source="../../media/mdo-eval/3_mdo-eval-activate-eval.png" alt-text="Billede af dashboardet Politik & Regler og en pil, der peger på Trusselspolitikker. Klik på det næste!":::

5. Rul ned *til Yderligere* politikker, og **vælg flisen Evaluer Defender Office 365** Felt.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-activate-eval.png" alt-text="Flisen Eval Defender Office 365, der fortæller, at det er en 30 dages prøveversion på tværs & med samarbejdsvektorer. Klik dig igennem.":::

6. Vælg nu, om eksterne mails routes Exchange Online direkte eller til en gateway eller tjeneste fra en tredjepart, og klik på Næste.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-activate-eval.png" alt-text="Defender for Office 365 vil evaluere mails, der sendes til Exchange Online postkasser. Giv oplysninger om, hvordan din mail dirigeres nu, herunder navnet på den udgående forbindelse, der sender din mail. Hvis du kun bruger Exchange Online Protection (EOP), har du ikke en forbindelse. Vælg et af jeg bruger en tredjepartsudbyder eller en lokal udbyder, eller jeg bruger kun EOP.":::

7. Hvis du bruger en tredjepartsgateway, skal du vælge leverandørnavnet på rullelisten sammen med den indgående forbindelse, der er knyttet til den pågældende løsning. Når du har angivet svarene, skal du klikke på Næste.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png" alt-text="I denne dialogboks skal du vælge den tredjepartsleverandørtjeneste, din organisation bruger, eller vælge *Andre*. I den næste dialogboks ned skal du vælge den indgående forbindelse. Klik derefter på Næste.":::

8. Gennemgå dine indstillinger, og klik på **knappen Opret** evaluering.

   |Før|Efter|
   |:---:|:---:|
   |:::image type="content" source="../../media/mdo-eval/7-mdo-eval-activate-review.png" alt-text="Denne rude indeholder en rulleliste, hvor du kan gennemse dine indstillinger. Den har også et klikbart link til Rediger din routingtype, hvis du har brug for det. Når du er klar, skal du klikke på den store blå Opret evaluering-knap.":::|:::image type="content" source="../../media/mdo-eval/8-mdo-eval-activate-complete.png" alt-text="Og nu er opsætningen fuldført. Den blå knap på denne side siger &quot;Gå til evaluering&quot;.":::|
   |

## <a name="next-steps"></a>Næste trin

Trin 3 af 3: Konfigurer pilotprojektet for Microsoft Defender til Office 365

Gå tilbage til oversigten for [Evaluer Microsoft Defender for Office 365](eval-defender-office-365-overview.md)

Gå tilbage til oversigten for [Evaluer og Microsoft 365 Defender](eval-overview.md)
