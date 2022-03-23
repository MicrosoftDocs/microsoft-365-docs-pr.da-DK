---
title: Administrer ventepositionsmeddelelser
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
description: Brug kommunikationsarbejdsprocessen i Advanced eDiscovery til at spore status for dine meddelelser om retslig venteposition og, hvis det er nødvendigt, opdatere dem og sende dem igen.
ms.openlocfilehash: 276771b2a22f6db3e3d0620ee429a16626107bcc
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588719"
---
# <a name="manage-hold-notifications"></a>Administrer ventepositionsmeddelelser

Når du har startet arbejdsprocessen for meddelelser om retslig venteposition, kan du bruge kommunikationsarbejdsprocessen i Advanced eDiscovery til at spore status for din kommunikation. Fanen Kommunikation indeholder en liste over alle meddelelser i din Advanced eDiscovery sag. Du kan se detaljer som f.eks antallet af personer, der har fået tildelt eller har bekræftet meddelelsen.

## <a name="monitor-acknowledgments"></a>Overvåg bekræftelser

Når du har valgt en meddelelse på **fanen Kommunikation** , kan du få vist en liste over personer, der er godkendt til venteposition. 

1. I overholdelsescenteret skal du gå **til eDiscovery > Advanced eDiscovery**.

2. Markér en sag, og klik derefter **på fanen** Kommunikation.

3. Vælg en meddelelse for at få vist **pop op-siden for** kommunikation for YDN.

Der vises en liste over overensstemmelsesianer, der er knyttet til den valgte kommunikation, på pop op-siden for kommunikation. Denne side viser også indsigt og om, hvor mange bekræftelser der er modtaget, og hvor mange der er udestående. Siden viser også, hvilke hjælpere, der har sendt en bekræftelse om, at de har modtaget meddelelsen om venteposition.

## <a name="re-send-a-hold-notice"></a>Send en meddelelse om venteposition igen

Det kan være, at  fejlmeddelelser mister overblikket over mails i deres daglige arbejde. Eller ved længere procesførelse kan en kontaktperson kontakte dig eller andre og anmode om, at du sender en meddelelse igen. Når du administrerer kommunikationsarbejdsprocessen for meddelelser om retslig venteposition, kan det være nødvendigt at sende en meddelelse igen for at få den tilbage til "toppen af en brugers postkasse".

Sådan sender du en besked om venteposition til en leder:

1. I Advanced eDiscovery skal du markere en sag og derefter klikke på **fanen** Kommunikation.

2. Vælg en meddelelse for at få vist **pop op-siden for** kommunikation for YDN.

3. Klik **på Flere > meddelelse om at sende venteposition igen**.

4. På pop **op-siden** Send meddelelse igen med meddelelse om venteposition skal du vælge de vælgere, som du vil sende meddelelsen igen, og eventuelt skrive en årsag.

5. Klik **på Send igen for** at sende meddelelsen til de valgte øvrtere.

Hvis en kontakt, der ikke har bekræftet meddelelsen om venteposition, genstartes påmindelsen og eskaleringsarbejdsprocessen. Hvis en øvermand har bekræftet meddelelsen om venteposition, modtager kontakterne en kopi af den oprindelige meddelelse om venteposition.

> [!NOTE]
> Du kan kun sende en meddelelse om retslig venteposition igen til personer, der er tildelt til kommunikationen. 

## <a name="update-preservation-requirements"></a>Krav til opbevaring af opdatering
  
I løbet af sagens forløb kan det være nødvendigt at give besked om, at der skal bevares yderligere eller færre data, end det tidligere blev beskrevet. I eDiscovery-vilkår skal du udstede ventepositionsmeddelelsen med opdateret indhold igen.

Sådan opdateres indholdet af den oprindelige meddelelse om venteposition:

1. I Advanced eDiscovery skal du markere en sag og derefter klikke på **fanen** Kommunikation.

2. Markér den meddelelse om venteposition, du vil opdatere, og **klik på** Rediger på pop **op-siden Med** kommunikation for 1-1-1.

3. I guiden **Rediger kommunikation** skal du **klikke på Definer portalindhold** i venstre rude i guiden og opdatere indholdet af meddelelsen.

4. Klik på **Gem**.

Der sendes en meddelelse om ny udstedelse til alle de personer, der er tilknyttet meddelelsen om retslig venteposition. Desuden genstartes arbejdsprocesserne for disse meddelelsestyper, hvis påmindelses- eller eskaleringsmeddelelsen er aktiveret.

## <a name="update-legal-hold-notifications-and-settings"></a>Opdater meddelelser og indstillinger for retslig venteposition

Når du opdaterer indholdet eller indstillingerne for udgivelse, udgivelse, videresende, påmindelse eller eskalering, gælder disse ændringer for al fremtidig kommunikation, der genereres af arbejdsprocessen.

## <a name="more-information"></a>Flere oplysninger

- [Føj ydsere til en sag](add-custodians-to-case.md)

- [Opret en meddelelse om retslig venteposition](create-hold-notification.md)

- [Anerkend en meddelelse om venteposition](acknowledge-hold-notification.md)
