---
title: Microsoft 365 oversigt over overholdelse af fyrtårnsenhed
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: For administrerede tjenesteudbydere, der bruger Microsoft 365 Lighthouse, kan du få mere at vide om siden Enhedsoverholdelse.
ms.openlocfilehash: 76cb914b878b3da8236e91ddda538cb13fa3aa8c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606623"
---
# <a name="microsoft-365-lighthouse-device-compliance-page-overview"></a>Microsoft 365 oversigt over overholdelse af fyrtårnsenhed

Microsoft 365 Lighthouse giver dig mulighed for at få vist indsigt og oplysninger, der er relateret til overholdelse af enheder i Intune for alle dine  kundelejere, ved at vælge Enheder i venstre navigationsrude for at åbne siden Enhedsoverholdelse. Fra denne side kan du få et overblik over overholdelsesstatus på tværs af lejere, få vist en liste over enheder for hver lejer og få statusrapporter over overholdelsespolitikker og -indstillinger.

## <a name="overview-tab"></a>Fanen Oversigt  
  
På fanen Oversigt kan du få vist status for enhedsoverholdelse på tværs af dine lejere, se månedlige tendens for enhedsoverholdelse og spore, om enheder har tildelt overholdelsespolitikker. Du kan også se, hvor mange lejere der ikke har krav til enhedsoverholdelse håndhævet ved hjælp af politikker for betinget adgang. Du kan vælge Vis **mere for** at få vist flere detaljer.

Hvis du vil have detaljerede oplysninger om enhedsoverholdelse for en bestemt kundelejer, skal du vælge en værdi under en af statuskolonnerne for den pågældende lejer. Dette åbner fanen Enheder, så du kan få vist oplysninger om enhedsoverholdelse for den valgte lejer.

Hvis du vil eksportere data om enhedsoverholdelse til Excel fil med kommaseparerede værdier (.csv), skal du vælge **Eksportér**.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/device-overview-tab.png" alt-text="Skærmbillede af fanen Oversigt." lightbox="../media/m365-lighthouse-device-compliance-page-overview/device-overview-tab.png":::

## <a name="devices-tab"></a>Fanen Enheder

På fanen Enheder viser den farvede antal anmærkningslinje det samlede antal enheder på tværs af alle dine kundelejere, der har følgende statusser for overholdelse: Kompatibel, Ikke kompatibel, I udvidet periode og Evalueres ikke. Du kan finde flere oplysninger om de forskellige overholdelsesstatusser i [Overvåg politikker for overholdelse af regler og standarder for Intune-enheder](/mem/intune/protect/compliance-policy-monitor).

Hvis du vil se, hvilke lejere der har enheder med en bestemt overholdelsesstatus, skal du vælge denne status på antal anmærkningslinjen for at filtrere listen. Hvis du vil se status for enhedsoverholdelse for en eller flere bestemte lejere, skal du bruge rullemenuen **Lejere** til at filtrere listen.

Vælg et vilkårligt enhedsnavn på listen for at få vist flere oplysninger om den pågældende enheds aktuelle overholdelsestilstand. Du kan synkronisere eller genstarte enheden eller vælge Vis enhed i **Microsoft Endpoint Manager** hvis du har brug for at foretage fejlfinding eller udføre yderligere handlinger.

> [!NOTE]
> Når du genstarter en enhed, får ejeren af enheden ikke automatisk besked og kan miste ikke-gemt arbejde. Derfor kan det være en god ide at give ejeren af enheden besked, før du genstarter en enhed.

Fanen Enheder indeholder også følgende indstillinger:

- **Eksportér:** Vælg for at eksportere data om enhedsoverholdelse til Excel fil med kommaseparerede værdier (.csv).
- **Opdater:** Vælg for at hente de mest aktuelle data om enhedsoverholdelse.
- **Synkroniser:** Vælg en eller flere enheder på listen, der har statussen Ikke kompatibel, I udvidet periode eller Evalueres ikke, og vælg derefter denne indstilling for at tvinge disse enheder til at tjekke ind med Intune og straks modtage eventuelle politikker, der er tildelt dem.
- **Genstart:** Vælg en eller flere enheder på listen, der har statussen Ikke kompatibel, I udvidet periode eller Evalueres ikke, og vælg derefter denne indstilling for at genstarte disse enheder.
- **Søg:** Angiv nøgleord for hurtigt at finde en bestemt enhed på listen.
 
:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/devices-device-tab.png" alt-text="Skærmbillede af fanen Enheder." lightbox="../media/m365-lighthouse-device-compliance-page-overview/devices-device-tab.png":::

## <a name="policies-tab"></a>Fanen Politikker

På fanen Politikker kan du få vist politikker for enhedsoverholdelse på tværs af dine lejere og sammenligne to eller tre politikker af samme platformstype ved hjælp af **indstillingen** Sammenlign.

Hvis du vil se politikker for enheder på en bestemt platform, skal **du bruge rullemenuen** OS til at filtrere listen. Hvis du vil se politikker for en eller flere bestemte kundelejere, skal du bruge rullemenuen **Lejere** til at filtrere listen.

Vælg et vilkårligt politiknavn på listen for at få vist flere oplysninger om den pågældende politik. Hvis du skal handle eller se flere oplysninger, skal du vælge **Vis denne politik i Microsoft Endpoint Manager**.

Fanen Politikker indeholder også følgende indstillinger:

- **Eksportér:** Vælg for at eksportere data om overholdelsespolitik for enheder Excel en fil med kommaseparerede værdier (.csv).
- **Opdater:** Vælg for at hente de mest aktuelle data for enheds overholdelsespolitik.
- **Søg:** Angiv nøgleord for hurtigt at finde en bestemt politik for enhedsoverholdelse på listen.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/devices-policies-tab.png" alt-text="Skærmbillede af fanen Politikker." lightbox="../media/m365-lighthouse-device-compliance-page-overview/devices-policies-tab.png":::

## <a name="settings-tab"></a>Indstillinger fane

Fanen Indstillinger indeholder en samlet rapport over ikke-kompatible indstillinger på tværs af lejerenheder. 

Hvis du vil se ikke-kompatible indstillinger for enheder på en bestemt platform, skal **du bruge** rullemenuen Platform til at filtrere listen. Hvis du vil se ikke-kompatible indstillinger for en eller flere bestemte lejere, skal du bruge rullemenuen **Lejere** til at filtrere listen.

Vælg et hvilket som helst ikke-kompatibelt indstillingsnavn på listen for at åbne en rude, hvor du kan få vist en liste over lejere, der har enheder med den specifikke ikke-kompatible indstilling. Herfra kan du analysere yderligere ved at vælge en lejer på listen for at få vist oplysninger om enhederne i den pågældende lejer, der har den specifikke ikke-kompatible indstilling. Du kan også synkronisere eller genstarte enheden eller vælge Vis enhed i **Microsoft Endpoint Manager** hvis du har brug for at foretage fejlfinding eller udføre yderligere handlinger.

Fanen Indstillinger indeholder også følgende indstillinger:

- **Eksportér:** Vælg for at eksportere ikke-kompatible indstillinger til Excel en fil med kommaseparerede værdier (.csv).
- **Opdater:** Vælg for at hente de mest aktuelle ikke-kompatible indstillinger.
- **Søg:** Angiv nøgleord for hurtigt at finde en bestemt ikke-kompatibel indstilling på listen.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/device-settings-tab.png" alt-text="Skærmbillede af Indstillinger Fane." lightbox="../media/m365-lighthouse-device-compliance-page-overview/device-settings-tab.png":::

## <a name="related-content"></a>Relateret indhold

[Windows 365 (Sky-pc'er) sideoversigt](m365-lighthouse-win365-page-overview.md) (artikel)\
[Microsoft 365 ofte stillede spørgsmål om fyrtårn](m365-lighthouse-faq.yml) (artikel)
