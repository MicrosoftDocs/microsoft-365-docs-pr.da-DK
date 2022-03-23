---
title: Mailtrådning i Advanced eDiscovery
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
description: Når du udfører en Advanced eDiscovery, fortolker mailtråde en mailsamtale og adskiller hver meddelelse i forskellige kategorier.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 788858d6acaccbe07f3190b5adaaa05fe95c33a5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588929"
---
# <a name="email-threading-in-advanced-ediscovery"></a>Mailtrådning i Advanced eDiscovery

Overvej en mailsamtale, der har stået på i et stykke tid. I de fleste tilfælde vil den sidste meddelelse i mailtråden indeholde indholdet af alle de foregående meddelelser. Derfor giver gennemgangen af den sidste meddelelse en komplet kontekst til den samtale, der skete i tråden. Mailtrådning identificerer sådanne meddelelser, så korrekturlæsere kan gennemse en brøkdel af de indsamlede dokumenter, uden at konteksten går tabt.

## <a name="what-does-email-threading-do"></a>Hvad gør mailtrådning?

Mailtrådning fortolker hver mailtråd og dekonstrukturerer den til individuelle meddelelser. Hver mailtråd er en kæde af individuelle meddelelser. Advanced eDiscovery analyserer alle mails i korrektursættet for at afgøre, om en mail har entydigt indhold, eller om kæden (overordnede meddelelser) er indeholdt i den endelige meddelelse i mailtråden. Mails er opdelt i fire inkluderende værdier:

- **Inkluderende**: *En inkluderende* mail er den endelige mail i en mailtråd og indeholder alt det tidligere indhold fra den pågældende mailtråd.

- **Inklusive minus**: En mail angives som Inkluderende *minus* , hvis der er knyttet en eller flere vedhæftede filer til den specifikke meddelelse i mailtråden. En korrekturlæser kan bruge værdien Inklusive minus til at afgøre, hvilken bestemt mail i tråden der har tilknyttede vedhæftede filer. 

- **Inkluderende kopi**: En mail betragtes som en *inkluderende kopi,* hvis det er en nøjagtig kopi af en inkluderende eller inkluderende minusmeddelelse. 

- **Ingen**: *Værdien Ingen angiver* , at indholdet af meddelelsen er indeholdt i mindst én anden mail, der er markeret som Inkluderende eller Inkluderende minus.

## <a name="how-is-it-different-from-conversations-in-outlook"></a>Hvordan er det forskelligt fra samtaler i Outlook?

Dette lyder hurtigt som samtalegruppering i Outlook. Der findes dog nogle vigtige forskelle. Overvej en mailsamtale, der er blevet forkedt ind i to samtaler; Eksempelvis har nogen svaret på en mail, der ikke er den seneste i samtalen, så de to sidste mails i samtalen begge har entydigt indhold.

Outlook stadig gruppere mails i en enkelt samtale. Hvis du kun læste den sidste mail, ville det betyde, at der manglede konteksten for den næstsidlige mail, som også indeholder entydigt indhold. Da mailtrådning fortolker hver mail til individuelle komponenter og sammenligner dem, markerer mailtrådning begge de sidste to mails som inkluderende og sørger for, at du ikke går glip af kontekst, så længe du læser alle mails, der er markeret som inkluderende.
