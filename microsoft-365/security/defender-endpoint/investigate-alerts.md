---
title: Undersøg Microsoft Defender for at få slutpunktsbeskeder
description: Brug undersøgelsesmulighederne til at få oplysninger om vigtige beskeder påvirker dit netværk, hvad de betyder, og hvordan du kan løse dem.
keywords: undersøge, undersøge, enheder, enhed, kø af beskeder, dashboard, IP-adresse, fil, indsende, indsendelser, dybdegående analyse, tidslinje, søgning, domæne, URL, IP
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: f228d0ca44589b9c140226c2b39984c717c7d9f8
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63592944"
---
# <a name="investigate-alerts-in-microsoft-defender-for-endpoint"></a>Undersøg vigtige beskeder i Microsoft Defender til slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatealerts-abovefoldlink)

Undersøg beskeder, der påvirker dit netværk, forstå, hvad de betyder, og hvordan du løser dem.

Vælg en besked fra køen med vigtige beskeder for at gå til siden med vigtige beskeder. Denne visning indeholder beskedens titel, de berørte aktiver, sideruden med detaljer og beskedens historie.

Start din undersøgelse på påmindelsessiden ved at vælge de påvirkede aktiver eller enhederne under trævisningen af beskedhistorien. Detaljeruden udfyldes automatisk med yderligere oplysninger om, hvad du har valgt. Hvis du vil se, hvilke oplysninger du kan få vist her, [skal du læse Gennemse vigtige beskeder i Microsoft Defender til slutpunkt](/microsoft-365/security/defender-endpoint/review-alerts).

## <a name="investigate-using-the-alert-story"></a>Undersøg ved hjælp af beskedens tekstenhed

Beskedens historie fortæller, hvorfor beskeden blev udløst, relaterede hændelser, der skete før og efter, samt andre relaterede enheder.

Enheder er klikbare, og alle enheder, der ikke er en besked, kan udvides ved hjælp af udvidelsesikonet i højre side af enhedens kort. Den enhed, der er i fokus, angives med en blå stribe til venstre side af enhedens kort, hvor beskeden i titlen i første omgang er i fokus.

Udvid enheder for at få et hurtigt overblik over detaljer. Når du vælger en enhed, skiftes konteksten for detaljeruden til denne enhed, og du kan gennemse yderligere oplysninger samt administrere den pågældende enhed. Hvis du *vælger ...* til højre for enhedskortet, vises alle tilgængelige handlinger for den pågældende enhed. De samme handlinger vises i detaljeruden, når enheden er i fokus.

> [!NOTE]
> Sektionen med besked tekstenhed kan indeholde mere end én besked, hvor flere vigtige beskeder om det samme eksekveringstræ vises før eller efter den besked, du har valgt.

![Et eksempel på en historie med en besked i fokus og nogle udvidede kort.](images/alert-story-tree.png)

## <a name="take-action-from-the-details-pane"></a>Tag skridtet ud fra detaljeruden

Når du har valgt en enhed af interesse, ændres detaljeruden for at vise oplysninger om den valgte enhedstype, historiske oplysninger, når den er tilgængelig, og tilbyde kontrolelementer at handle  på denne enhed direkte fra påmindelsessiden.

Når du er færdig med at undersøge sagen, skal du gå tilbage til den besked, du startede med, markere beskedens status som Løst og klassificere den som enten Falsk **besked eller** **Sand besked**. Klassificering af beskeder hjælper med at finjustere denne mulighed for at give mere sande beskeder og færre falske beskeder.

Hvis du klassificerer den som en sand besked, kan du også vælge en bestemmelse, sådan som det er vist på billedet nedenfor.

![Et kodestykke af detaljeruden med en løst besked og determinations-rullemenuen udvidet.](images/alert-details-resolved-true.png)

Hvis du oplever en falsk besked med en line of business-applikation, kan du oprette en undertrykkende regel for at undgå denne type besked i fremtiden.

![handlinger og klassificering i detaljeruden med skjulereglen fremhævet.](images/alert-false-suppression-rule.png)

> [!TIP]
> Hvis du oplever problemer, der ikke er beskrevet ovenfor, kan du bruge 🙂 knappen til at give feedback eller åbne en supportbillet.


## <a name="related-topics"></a>Relaterede emner
- [Få vist og organiser køen for Microsoft Defender for Endpoint Alerts](alerts-queue.md)
- [Administrer Microsoft Defender for Endpoint-beskeder](manage-alerts.md)
- [Undersøg en fil, der er knyttet til en Defender for Endpoint-besked](investigate-files.md)
- [Undersøg enhederne på listen Defender for Endpoint-enheder](investigate-machines.md)
- [Undersøg en IP-adresse, der er knyttet til en Defender for Endpoint-besked](investigate-ip.md)
- [Undersøg et domæne, der er knyttet til en Defender for Endpoint-besked](investigate-domain.md)
- [Undersøg en brugerkonto i Defender for Endpoint](investigate-user.md)


