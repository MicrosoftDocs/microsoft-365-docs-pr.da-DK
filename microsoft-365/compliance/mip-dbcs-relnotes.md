---
title: Microsoft Purview-understøttelse af produktbemærkninger med dobbeltbytetegnsæt
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
description: Produktbemærkninger til understøttelse af dobbeltbytetegnsæt.
ms.openlocfilehash: 593e1db04c5e4dc56bc4cc1a7fd11d907d4fe09d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622409"
---
# <a name="support-for-double-byte-character-set-release-notes"></a>Understøttelse af produktbemærkninger med dobbeltbytetegnsæt

 Microsoft 365 Information Protection understøtter nu sprog med dobbeltbytetegnsæt for:

- Kinesisk (forenklet)
- Kinesisk (traditionelt)
- Korean
- Japanese

Denne understøttelse er tilgængelig for følsomme informationstyper og nøgleordsordbøger og afspejles i Microsoft Purview Forebyggelse af datatab (for Exchange Online, SharePoint Online, OneDrive for Business og Teams), overholdelse af kommunikation, automatisk mærkning på kontoret apps og Microsoft Defender for Cloud Apps.

## <a name="known-issues"></a>Kendte problemer

- Når en tekstfil, der er knyttet til en mail, er i UTF-8-format uden byteordremærke (BOM), registreres mailen ikke af politikken for kommunikationoverensstemmelse.

- Politikker for overholdelse af kommunikation kan ikke registrere værdier, hvis der angives en sætning for politikbetingelsen: "Meddelelsen indeholder nogle af disse ord". Hvis den tekst, der er angivet i politikken, skrives som et ord, kan den registreres. Men hvis den skrives midt i en sætning, registreres den ikke.

- Politikker for overholdelse af kommunikation, der angiver ordbøger som typeoplysninger, registrerer ikke private Teams-chats og kanalchats.

- Følgende betingelser understøttes ikke i forbindelse med kommunikationsoverholdelse i denne fase (vi planlægger at løse disse problemer i fremtiden): 
  - "Meddelelsen indeholder et af disse ord"
  - "Meddelelsen indeholder ingen af disse ord"
  - "Vedhæftet fil indeholder et af disse ord"
  - "Vedhæftet fil indeholder et af disse ord"

- Politikker til forebyggelse af datatab kan gennemtvinges på macOS-enheder (prøveversion), der kører Catalina 10.15 og nyere, bortset fra nedenstående betingelser for østasiatiske sprog, herunder japansk.
  - Der registreres ikke tal i fuld bredde, f.eks. ved hjælp af en indbygget skabelon, f.eks.
  - Tal uden afgrænsere registreres ikke
  - Nøgleord adskilt af mellemrum i halv bredde registreres ikke for en følsom oplysningstype. Eksempel: Japansk ord er angivet til typen af følsomme oplysninger, og ordbogen registreres ikke, hvis det er i en sætning
  - Ord, der indeholder både engelsk og japansk (東京2020), registreres ikke

Vi anbefaler i stedet, at du opretter en brugerdefineret SIT (Sensitive Information Type) med nøgleordsordbogen, som registrerer mønstre på tværs af meddelelser og vedhæftede filer og bruger denne brugerdefinerede SIT som en politikbetingelse for kommunikationsoverholdelse.
