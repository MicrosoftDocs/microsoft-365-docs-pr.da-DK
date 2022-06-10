---
title: Oversigt over siden Med enhedsoverholdelse i Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: ragovind
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
description: Få mere at vide om siden Enhedsoverholdelse for udbydere af administrerede tjenester ved hjælp af Microsoft 365 Lighthouse.
ms.openlocfilehash: 1d00df09231863dd2d7d110dbf9d3c2600f464dc
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017826"
---
# <a name="overview-of-the-device-compliance-page-in-microsoft-365-lighthouse"></a>Oversigt over siden Med enhedsoverholdelse i Microsoft 365 Lighthouse

Microsoft 365 Lighthouse giver dig mulighed for at få vist indsigt og oplysninger, der er relateret til Intune enhedsoverholdelse for alle dine kundelejere, ved at vælge **Enheder** i venstre navigationsrude for at åbne siden Enhedsoverholdelse. Fra denne side kan du få en oversigt over status for overholdelse af angivne standarder på tværs af lejere, få vist en liste over enheder for hver lejer og få statusrapporter om politikker og indstillinger for overholdelse af angivne standarder.

## <a name="overview-tab"></a>Fanen Oversigt  
  
Under fanen Oversigt kan du få vist enhedens overholdelsesstatus på tværs af dine lejere, se månedlige tendenser for enhedsoverholdelse og spore, om enheder har fået tildelt overholdelsespolitikker. Du kan også se, hvor mange lejere der ikke har nogen krav om enhedsoverholdelse gennemtvunget ved hjælp af politikker for betinget adgang. Du kan vælge **Vis mere** for at få vist flere oplysninger.

Hvis du vil have detaljerede oplysninger om enhedens overholdelse af angivne standarder for en bestemt kundelejer, skal du vælge en værdi under en af statuskolonnerne for den pågældende lejer. Dette åbner fanen Enheder, så du kan få vist oplysninger om enhedens overholdelse af angivne standarder for den valgte lejer.

Hvis du vil eksportere data om enhedens overholdelse af angivne standarder til en Excel fil med kommaseparerede værdier (.csv), skal du vælge **Eksportér**.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/device-overview-tab.png" alt-text="Skærmbillede af fanen Oversigt." lightbox="../media/m365-lighthouse-device-compliance-page-overview/device-overview-tab.png":::

## <a name="devices-tab"></a>Fanen Enheder

Under fanen Enheder viser den farvede linje med antal anmærkninger det samlede antal enheder på tværs af alle dine kundelejere, der har følgende status for overholdelse af angivne standarder: Kompatibel, Ikke kompatibel, I udvidet periode og Ikke evalueret. Du kan få flere oplysninger om de forskellige statusser for overholdelse af angivne standarder under [Overvåg Intune politikker for enhedsoverholdelse](/mem/intune/protect/compliance-policy-monitor).

Hvis du vil se, hvilke lejere der har enheder med en bestemt status for overholdelse af angivne standarder, skal du vælge denne status på linjen med antal anmærkninger for at filtrere listen. Hvis du vil se status for enhedens overholdelse af angivne standarder for en eller flere specifikke kundelejere, skal du bruge rullemenuen **Lejere** til at filtrere listen.

Vælg et enhedsnavn på listen for at få vist flere oplysninger om enhedens aktuelle overholdelsestilstand. Du kan synkronisere eller genstarte enheden eller vælge **Vis enhed i Microsoft Endpoint Manager** hvis du har brug for at foretage fejlfinding eller foretage yderligere handling.

> [!NOTE]
> Når du genstarter en enhed, får enhedsejeren ikke automatisk besked og kan miste arbejde, der ikke er gemt. Derfor kan det være en god idé at give enhedsejeren besked, før du genstarter en enhed.

Fanen Enheder indeholder også følgende indstillinger:

- **Eksport:** Vælg at eksportere data om enhedens overholdelse af angivne standarder til en Excel fil med kommaseparerede værdier (.csv).
- **Opdatere:** Vælg at hente de nyeste data om enhedens overholdelse af angivne standarder.
- **Sync:** Vælg en eller flere enheder på listen, der har statussen Ikke kompatibel, I udvidet periode eller Ikke evalueret, og vælg derefter denne indstilling for at tvinge disse enheder til at tjekke ind med Intune og straks modtage eventuelle politikker, der er tildelt dem.
- **Genstarte:** Vælg en eller flere enheder på listen, der har statussen Ikke kompatibel, I udvidet periode eller Ikke evalueret, og vælg derefter denne indstilling for at genstarte disse enheder.
- **Søg:** Angiv nøgleord for hurtigt at finde en bestemt enhed på listen.
 
:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/devices-device-tab.png" alt-text="Skærmbillede af fanen Enheder." lightbox="../media/m365-lighthouse-device-compliance-page-overview/devices-device-tab.png":::

## <a name="policies-tab"></a>Fanen Politikker

Under fanen Politikker kan du få vist politikker for enhedsoverholdelse på tværs af dine lejere og sammenligne to eller tre politikker af samme platformtype ved hjælp af indstillingen **Sammenlign** .

Hvis du vil se politikker for enheder på en bestemt platform, skal du bruge rullemenuen for **operativsystemet** til at filtrere listen. Hvis du vil se politikker for en eller flere specifikke kundelejere, skal du bruge rullemenuen **Lejere** til at filtrere listen.

Vælg et hvilket som helst politiknavn på listen for at få vist flere oplysninger om den pågældende politik. Hvis du har brug for at udføre en handling eller få vist flere oplysninger, skal du vælge **Få vist denne politik i Microsoft Endpoint Manager**.

Fanen Politikker indeholder også følgende indstillinger:

- **Eksport:** Vælg at eksportere politikdata for enhedens overholdelse af regler og standarder til en Excel fil med kommaseparerede værdier (.csv).
- **Opdatere:** Vælg at hente de nyeste data for enhedens politik for overholdelse af regler og standarder.
- **Søg:** Angiv nøgleord for hurtigt at finde en bestemt politik for enhedens overholdelse af angivne standarder på listen.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/devices-policies-tab.png" alt-text="Skærmbillede af fanen Politikker." lightbox="../media/m365-lighthouse-device-compliance-page-overview/devices-policies-tab.png":::

## <a name="settings-tab"></a>fanen Indstillinger

Fanen Indstillinger indeholder en samlet rapport over indstillinger, der ikke overholder angivne standarder, på tværs af lejerenheder. 

Hvis du vil se indstillinger, der ikke overholder angivne standarder for enheder på en bestemt platform, skal du bruge rullemenuen **Platform** til at filtrere listen. Hvis du vil se indstillinger, der ikke overholder angivne standarder for en eller flere specifikke kundelejere, skal du bruge rullemenuen **Lejere** til at filtrere listen.

Vælg et vilkårligt indstillingsnavn, der ikke overholder angivne standarder, på listen for at åbne en rude, hvor du kan få vist en liste over lejere, der har enheder med denne specifikke indstilling, der ikke overholder angivne standarder. Herfra kan du foretage yderligere detailudledning ved at vælge en hvilken som helst lejer på listen for at få vist oplysninger om enhederne i den pågældende lejer, der har den specifikke indstilling, der ikke overholder angivne standarder. Du kan også synkronisere eller genstarte enheden eller vælge **Vis enhed i Microsoft Endpoint Manager** hvis du har brug for at foretage fejlfinding eller foretage yderligere handling.

Fanen Indstillinger indeholder også følgende indstillinger:

- **Eksport:** Vælg at eksportere ikke-kompatible indstillingsdata til en Excel fil med kommaseparerede værdier (.csv).
- **Opdatere:** Vælg at hente de nyeste ikke-kompatible indstillingsdata.
- **Søg:** Angiv nøgleord for hurtigt at finde en bestemt indstilling, der ikke overholder angivne standarder, på listen.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/device-settings-tab.png" alt-text="Skærmbillede af fanen Indstillinger." lightbox="../media/m365-lighthouse-device-compliance-page-overview/device-settings-tab.png":::

## <a name="related-content"></a>Relateret indhold

[Oversigt over siden Windows 365 (cloud-pc'er) i Microsoft 365 Lighthouse](m365-lighthouse-win365-page-overview.md) (artikel)\
[ofte stillede spørgsmål om Microsoft 365 fyrtårn](m365-lighthouse-faq.yml) (artikel)
