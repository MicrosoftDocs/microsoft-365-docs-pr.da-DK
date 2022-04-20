---
title: Administrer meddelelser om fastfrysning
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Brug arbejdsprocessen for kommunikation i eDiscovery (Premium) til at spore status for dine meddelelser om juridisk venteposition og om nødvendigt opdatere og sende dem igen.
ms.openlocfilehash: 83e5331aaea59893f06cfa0629d627e500cfe1b1
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996168"
---
# <a name="manage-hold-notifications"></a>Administrer meddelelser om fastfrysning

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du har startet arbejdsprocessen for meddelelse om juridisk venteposition, kan du bruge arbejdsprocessen for kommunikation i Microsoft Purview eDiscovery (Premium) til at spore status for din kommunikation. Fanen Kommunikation indeholder en liste over alle meddelelser i din eDiscovery (Premium)-sag. Du kan se detaljer som f.eks. antallet af tilsynsførende, der er blevet tildelt eller har bekræftet meddelelsen.

## <a name="monitor-acknowledgments"></a>Overvåg bekræftelser

Når du har valgt en kommunikation under fanen **Kommunikation** , kan du få vist en liste over tilsynsførende, der har bekræftet en meddelelse om venteposition. 

1. I Overholdelsescenter skal du gå til **eDiscovery > eDiscovery (Premium)**.

2. Vælg en sag, og klik derefter på fanen **Kommunikation** .

3. Vælg en kommunikation for at få vist pop op-siden **Tilsynsførende kommunikation** .

Der vises en liste over tilsynsførende, der er knyttet til den valgte kommunikation, på siden med kommunikationsflyet. Denne side viser også indsigt og om, hvor mange bekræftelser der blev modtaget, og hvor mange der er udestående. På siden kan du også se, hvilke tilsynsførende der har sendt en bekræftelse på, at de modtog meddelelsen om venteposition.

## <a name="re-send-a-hold-notice"></a>Send en meddelelse om venteposition igen

Indimellem mister vogtere overblikket over mails i deres daglige arbejde. Eller i en langvarig processag kan en tilsynsførende kontakte dig eller andre og anmode om, at du sender en meddelelse igen. Når du administrerer arbejdsprocessen for kommunikation for meddelelser om juridisk venteposition, skal du muligvis sende en meddelelse igen for at få den tilbage til "toppen af en brugers postkasse".

Sådan sender du en meddelelse om venteposition til en tilsynsførende:

1. I eDiscovery (Premium) skal du vælge en sag og derefter klikke på fanen **Kommunikation** .

2. Vælg en kommunikation for at få vist pop op-siden **Tilsynsførende kommunikation** .

3. Klik på **Flere > Send meddelelse om venteposition igen**.

4. På pop **op-vinduet Send meddelelse om venteposition** skal du vælge de tilsynsførende, som du vil sende meddelelsen igen, og angive en valgfri årsag.

5. Klik på **Send** igen for at sende meddelelsen til de valgte tilsynsførende.

Hvis en tilsynsførende ikke har bekræftet meddelelsen om venteposition, genstartes påmindelses- og eskaleringsarbejdsprocessen. Hvis en varetægtsfængslet har bekræftet ventepositionen, modtager tilsynsførende en kopi af den oprindelige ventepositionsmeddelelse.

> [!NOTE]
> Du kan kun sende en meddelelse om juridisk venteposition til tilsynsførende, der er tildelt til kommunikationen. 

## <a name="update-preservation-requirements"></a>Krav til opdateringsbevaring
  
Efterhånden som sagen skrider frem, kan tilsynsførende blive bedt om at bevare yderligere eller færre data, end de tidligere blev bedt om. Med hensyn til eDiscovery skal du udstede meddelelsen om venteposition igen med opdateret indhold.

Sådan opdaterer du indholdet af den indledende meddelelse om venteposition:

1. I eDiscovery (Premium) skal du vælge en sag og derefter klikke på fanen **Kommunikation** .

2. Vælg den meddelelse om venteposition, du vil opdatere, og klik på **Rediger** på siden **Forældremyndighedskommunikation** .

3. I guiden **Rediger kommunikation** skal du klikke på **Definer portalindhold** i venstre rude i guiden og opdatere indholdet af meddelelsen.

4. Klik på **Gem**.

Meddelelsen om genudgivelse vil blive sendt til alle de tilsynsførende, der er tildelt den juridiske ventepositionsmeddelelse. Hvis påmindelsen eller eskaleringsmeddelelsen er aktiveret, genstartes arbejdsprocesserne for disse typer meddelelser desuden.

## <a name="update-legal-hold-notifications-and-settings"></a>Opdater meddelelser og indstillinger for juridisk venteposition

Når du opdaterer indholdet eller indstillingerne for meddelelse om udstedelse, udgivelse, genudgivelse, påmindelse eller eskalering, gælder disse ændringer for al fremtidig kommunikation, der genereres af arbejdsprocessen.

## <a name="more-information"></a>Flere oplysninger

- [Føj ansvarlige til en sag](add-custodians-to-case.md)

- [Opret en meddelelse om juridisk venteposition](create-hold-notification.md)

- [Anerkend en meddelelse om fastfrysning](acknowledge-hold-notification.md)
