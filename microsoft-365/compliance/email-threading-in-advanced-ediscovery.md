---
title: Mailtrådning i eDiscovery (Premium)
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
description: Når du foretager en eDiscovery-analyse (Premium), opdeler mailtråde en mailsamtale og adskiller hver meddelelse i forskellige kategorier.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 51cc9ce09f1f2c9c95c3ab5a7f2175516c9ed199
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64948699"
---
# <a name="email-threading-in-ediscovery-premium"></a>Mailtrådning i eDiscovery (Premium)

Overvej en mailsamtale, der har stået på i et stykke tid. I de fleste tilfælde indeholder den sidste meddelelse i mailtråden indholdet af alle de foregående meddelelser. Derfor vil gennemgang af den sidste meddelelse give en komplet kontekst for den samtale, der skete i tråden. Mailtrådning identificerer sådanne meddelelser, så korrekturlæsere kan gennemse en brøkdel af indsamlede dokumenter uden at miste nogen kontekst.

## <a name="what-does-email-threading-do"></a>Hvad gør mailtrådning?

Mailtråde fortolker hver mailtråd og dekonstruerer den til individuelle meddelelser. Hver mailtråd er en kæde af individuelle meddelelser. Microsoft Purview eDiscovery (Premium) analyserer alle mail-messaer i korrektursættet for at afgøre, om en mail har entydigt indhold, eller om kæden (overordnede meddelelser) er helt indeholdt i den endelige meddelelse i mailtråden. Mailmeddelelser er opdelt i fire inklusive værdier:

- **Inklusive**: En *inkluderende* mail er den endelige mail i en mailtråd og indeholder alt det tidligere indhold i den pågældende mailtråd.

- **Inklusive minus**: En mail er angivet som *Inklusive minus* , hvis der er knyttet en eller flere vedhæftede filer til den specifikke meddelelse i mailtråden. En korrekturlæser kan bruge minusværdien Inclusive til at bestemme, hvilken bestemt mail i tråden der har knyttet vedhæftede filer. 

- **Inklusive kopi**: En mail betragtes som en *inklusive kopi* , hvis det er en nøjagtig kopi af en inclusive- eller inclusive-minusmeddelelse. 

- **Ingen**: Værdien *Ingen* angiver, at indholdet af meddelelsen er helt indeholdt i mindst én anden mail, der er markeret som Inklusive eller Inklusive minus.

## <a name="how-is-it-different-from-conversations-in-outlook"></a>Hvordan adskiller det sig fra samtaler i Outlook?

Det lyder hurtigt som samtalegrupperinger i Outlook. Der er dog nogle vigtige forskelle. Overvej en mailsamtale, der blev opdelt i to samtaler. En person svarede f.eks. på en mail, der ikke er den nyeste i samtalen, så de sidste to mails i samtalen begge har unikt indhold.

Outlook vil stadig gruppere mails i en enkelt samtale. Hvis du kun læser den sidste mail, vil det betyde, at konteksten for den anden til sidste mail, som også indeholder entydigt indhold, mangler. Da mailtrådning fortolker hver mail i individuelle komponenter og sammenligner dem, markerer mailtrådning begge de sidste to mails som inklusive, hvilket sikrer, at du ikke går glip af nogen kontekst, så længe du læser alle de mails, der er markeret som inklusive.
