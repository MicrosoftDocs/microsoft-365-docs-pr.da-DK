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
ms.openlocfilehash: 2de0e67c78ac558f4bdc2648790e49fad86e3178
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/01/2022
ms.locfileid: "64595044"
---
# <a name="support-for-double-byte-character-set-release-notes"></a>Understøttelse af produktbemærkninger til dobbelt byte-tegnsæt

 Microsoft 365 Information Protection understøtter nu dobbelte byte tegnsætsprog for:

- Kinesisk (forenklet)
- Kinesisk (traditionelt)
- Korean
- Japanese

Denne understøttelse er tilgængelig for typer af følsomme oplysninger og ordbøger til nøgleord og afspejles i forebyggelse af datatab (for forebyggelse af datatab (i Exchange Online, SharePoint Online, OneDrive for Business og Teams), overholdelse af kommunikation, automatisk mærkning i Office-apps og Microsoft Defender for Cloud Apps.

## <a name="known-issues"></a>Kendte problemer

- Når en tekstfil, der er vedhæftet en mail, er i UTF-8-format uden byterækkefølgemærke (KALES), registreres mailen ikke af politikken for overholdelse af kommunikation.

- Politikker for overholdelse af regler og standarder i kommunikation kan ikke registrere værdier, hvis der er angivet en sætning for betingelsen for politikken: "Meddelelsen indeholder et af disse ord". Hvis den tekst, der er angivet i politikken, er skrevet som et ord, kan den findes; Men hvis den er skrevet midt i en sætning, bliver den ikke fundet.

- Politikker for overholdelse af kommunikation, der angiver ordbøger som typeoplysninger, registrerer Teams private chats og kanalchats.

- Følgende betingelser understøttes ikke i kommunikationsoverholdelse på nuværende tidspunkt (vi planlægger at løse disse problemer i fremtiden): 
  - "Meddelelse indeholder et af disse ord"
  - "Meddelelsen indeholder ingen af disse ord"
  - "Vedhæftet fil indeholder et af disse ord"
  - "Vedhæftet fil indeholder et af disse ord"

- Politikker til forebyggelse af datatab kan håndhæves på macOS-enheder (prøveversion), der kører Catalina 10.15 og nyere, med undtagelse af de nedenfor nævnte betingelser for østasiatiske sprog, herunder japansk.
  - Tallene i fuld bredde registreres ikke, f.eks. ved hjælp af en indbygget skabelon, f.eks. et japansk bankkontonummer
  - Tal uden separatortegn bliver ikke fundet
  - Nøgleord, der er adskilt med et mellemrum i halv bredde, registreres ikke for en følsom oplysningstype. Det kan f.eks. være: Japansk ord er angivet ved type af følsomme oplysninger, og ordbogen registreres ikke, hvis det er i en sætning
  - Ord, der indeholder både engelsk og japansk (東京2020), bliver ikke fundet

I stedet anbefaler vi, at du opretter en brugerdefineret SIT (Sensitive Information Type) med ordbogen til nøgleord, som registrerer mønstre på tværs af meddelelser og vedhæftede filer, og bruger dette brugerdefinerede SIT som en betingelse for politikken Til overholdelse af kommunikation.
