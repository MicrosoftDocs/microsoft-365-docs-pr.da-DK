---
title: Microsoft 365 understøttelse af overholdelse af regler og standarder for udgivelsesbemærkninger til dobbelt byte-tegnsæt
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Produktbemærkninger til understøttelse af dobbelte bytetegnsæt.
ms.openlocfilehash: e87e88b63bf44c7ea4154fa24c05c0e8e252a446
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63589751"
---
# <a name="support-for-double-byte-character-set-release-notes"></a>Understøttelse af produktbemærkninger til dobbelt byte-tegnsæt

 Microsoft 365 Information Protection understøtter nu dobbelte byte tegnsætsprog til:

- Kinesisk (forenklet)
- Kinesisk (traditionelt)
- Korean
- Japanese

Denne understøttelse er tilgængelig for typer af følsomme oplysninger og ordbøger til nøgleord og afspejles i forebyggelse af datatab (for forebyggelse af datatab (for Exchange Online, SharePoint Online, OneDrive for Business og Teams), Kommunikationsoverholdelse, Automatisk opringning i Office-apps og Microsoft Defender til skyapps.

## <a name="known-issues"></a>Kendte problemer

- Når en tekstfil, der er vedhæftet en mail, er i UTF-8-format uden byterækkefølgemærke (AFST), registreres mailen ikke af politikken for overholdelse af kommunikation.

- Politikker for overholdelse af regler og standarder i kommunikation kan ikke registrere værdier, hvis der er angivet en sætning for betingelsen for politikken: "Meddelelsen indeholder et af disse ord". Hvis den tekst, der er angivet i politikken, er skrevet som et ord, kan den findes; Men hvis den er skrevet midt i en sætning, bliver den ikke fundet.

- Politikker for overholdelse af regler og standarder i kommunikation, der angiver ordbøger som typeoplysninger, Teams private chats og kanalchats.

- Følgende betingelser understøttes ikke for overholdelse af kommunikation på nuværende tidspunkt (vi planlægger at løse disse problemer i fremtiden): 
  - "Meddelelse indeholder et af disse ord"
  - "Meddelelsen indeholder ingen af disse ord"
  - "Vedhæftet fil indeholder et af disse ord"
  - "Vedhæftet fil indeholder et af disse ord"

I stedet anbefaler vi, at du opretter en brugerdefineret SIT (Sensitive Information Type) med ordbogen til nøgleord, som registrerer mønstre på tværs af meddelelser og vedhæftede filer, og bruger dette brugerdefinerede SIT som en betingelse for politikken Til overholdelse af kommunikation.
