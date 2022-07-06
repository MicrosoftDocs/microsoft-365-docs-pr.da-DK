---
title: Mailtrådning i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Når du foretager en eDiscovery-analyse (Premium), opdeler mailtrådning en mailsamtale og adskiller hver meddelelse i forskellige kategorier.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: a17f746cb0c88fb68e4654d0dd7de528135d62ee
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629701"
---
# <a name="email-threading-in-ediscovery-premium"></a>Mailtrådning i eDiscovery (Premium)

Overvej en mailsamtale, der har stået på i et stykke tid. I de fleste tilfælde indeholder den sidste meddelelse i mailtråden indholdet af alle de foregående meddelelser. Derfor vil gennemgang af den sidste meddelelse give en komplet kontekst for den samtale, der skete i tråden. Mailtrådning identificerer sådanne meddelelser, så korrekturlæsere kan gennemse en brøkdel af indsamlede dokumenter uden at miste nogen kontekst.

## <a name="what-does-email-threading-do"></a>Hvad gør mailtrådning?

Mailtråde fortolker hver mailtråd og dekonstruerer den til individuelle meddelelser. Hver mailtråd er en kæde af individuelle meddelelser. Microsoft Purview eDiscovery (Premium) analyserer alle mails i korrektursættet for at afgøre, om en mail har entydigt indhold, eller om kæden (overordnede meddelelser) er helt indeholdt i den endelige meddelelse i mailtråden. Mailmeddelelser er opdelt i fire inklusive værdier:

- **Inklusive**: En *inkluderende* mail er den endelige mail i en mailtråd og indeholder alt det tidligere indhold i den pågældende mailtråd.

- **Inklusive minus**: En mail er angivet som *Inklusive minus* , hvis der er knyttet en eller flere vedhæftede filer til den specifikke meddelelse i mailtråden. En korrekturlæser kan bruge minusværdien Inclusive til at bestemme, hvilken bestemt mail i tråden der har knyttet vedhæftede filer. 

- **Inklusive kopi**: En mail betragtes som en *inclusive-kopi* , hvis det er en nøjagtig kopi af en inclusive- eller inclusive-minusmeddelelse. 

- **Ingen**: Værdien *Ingen* angiver, at indholdet af meddelelsen er helt indeholdt i mindst én anden mail, der er markeret som Inklusive eller Inklusive minus.

## <a name="how-is-it-different-from-conversations-in-outlook"></a>Hvordan adskiller det sig fra samtaler i Outlook?

Det lyder hurtigt som samtalegrupperinger i Outlook. Der er dog nogle vigtige forskelle. Overvej en mailsamtale, der blev opdelt i to samtaler. En person har f.eks. besvaret en mail, der ikke er den nyeste i samtalen, så de sidste to mails i samtalen begge har unikt indhold.

Outlook grupperer stadig mails i en enkelt samtale. Hvis du kun læser den sidste mail, vil det betyde, at konteksten for den anden til sidste mail, som også indeholder entydigt indhold, mangler. Da mailtrådning fortolker hver mail i individuelle komponenter og sammenligner dem, markerer mailtrådning begge de sidste to mails som inklusive, hvilket sikrer, at du ikke går glip af nogen kontekst, så længe du læser alle de mails, der er markeret som inklusive.
