---
title: Karantænemeddelelser (beskeder om spam til slutbruger) i Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 56de4ed5-b0aa-4195-9f46-033d7cc086bc
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om beskeder om spam til slutbrugere for meddelelser i karantæne i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1950104e910733bfb3f846ff53411a6c75bbd68d
ms.sourcegitcommit: 2ea2105d40b60a87fc9aa30f392a73a3a9db6d99
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/20/2021
ms.locfileid: "63587310"
---
# <a name="use-quarantine-notifications-to-release-and-report-quarantined-messages"></a>Brug af karantænemeddelelser til at frigive og rapportere meddelelser, der er sat i karantæne

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 med postkasser i Exchange Online eller enkeltstående Exchange Online Protection (EOP)-organisationer uden Exchange Online-postkasser, sætter karantæne i potentielt farlig eller uønskede meddelelser. Få mere at vide under [Meddelelser, der er sat i karantæne i EOP](quarantine-email-messages.md).

_Karantænepolitikker_ definerer, hvad brugere har tilladelse til at gøre til meddelelser, der er sat i karantæne, ud fra, hvorfor meddelelsen var i karantæne (for understøttede funktioner). Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md). Karantæne uden for politik styrer også, om de berørte modtagere (herunder delte postkasser) får periodiske meddelelser _om_ deres meddelelser i karantæne. Karantænemeddelelser er erstatningen for beskeder om spam til slutbrugeren for alle understøttede beskyttelsesfunktioner (ikke kun antispampolitikkens konklusion).

Karantænemeddelelser er ikke slået til i de indbyggede karantænemeddelelser, der hedder AdminOnlyAccessPolicy eller DefaultFullAccessPolicy. Karantænemeddelelser er slået til i den indbyggede karantænepolitik, der hedder NotificationEnabledPolicy [, hvis din organisation har den](quarantine-policies.md#full-access-permissions-and-quarantine-notifications). Ellers skal du oprette og konfigurere en ny karantænepolitik for at slå meddelelser i karantæne [til i karantænepolitikker](quarantine-policies.md#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal).

Desuden skal brugere være aktiveret til Remote Powershell for at tillade, at indstillingen "Bloker afsender" i karantænemeddelelser fungerer korrekt. Du kan finde en vejledning [under Aktivér eller deaktiver adgang til Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell).

Administratorer kan også bruge de globale indstillinger i karantænepolitikker til at tilpasse afsenderens viste navn, ansvarsfraskrivelsestekst på forskellige sprog og firmalogoet, der bruges i karantænemeddelelser. Du kan finde en vejledning under [Konfigurere indstillinger for meddelelser om global karantæne](quarantine-policies.md#configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal).

For delte postkasser understøttes karantænemeddelelser kun for brugere, der har fået FullAccess-tilladelse til den delte postkasse. Få mere at vide under [Brug EAC til at redigere delegering af delte postkasser](/Exchange/collaboration-exo/shared-mailboxes#use-the-eac-to-edit-shared-mailbox-delegation).

> [!NOTE]
> Som standard er meddelelser, der er sat i karantæne som phishing med høj tillid, malware, via regler for mailflow (også kaldet transportregler) eller Pengeskab Politikker for vedhæftede filer i Defender for Office 365 kun tilgængelige for administratorer (som standard bruges politikken AdminOnlyAccessPolicy-karantæne). Få mere at vide under [Administrer meddelelser og filer, der er sat i karantæne som administrator i EOP](manage-quarantined-messages-and-files.md).
>
> I øjeblikket understøttes karantænemeddelelser ikke for grupper eller phishingmeddelelser med høj tillid. 

Når du modtager en besked om karantæne, er følgende oplysninger altid tilgængelige for hver meddelelse, der er sat i karantæne:

- **Afsender**: Send-navnet og mailadressen på den meddelelse, der er sat i karantæne.
- **Emne**: Teksten i emnelinjen for den meddelelse, der er sat i karantæne.
- **Dato**: Dato og klokkeslæt (i UTC), hvor meddelelsen var i karantæne.

De handlinger, der er tilgængelige i karantænemeddelelsen, afhænger af, hvorfor meddelelsen var i karantæne, og de tilladelser, der er tildelt af den tilknyttede karantænepolitik. Du kan få mere at vide under [Oplysninger om tilladelse til karantænepolitik](quarantine-policies.md#quarantine-policy-permission-details).

Følgende handlinger er som standard tilgængelige i karantænemeddelelsen for meddelelser, der var sat i karantæne som spam, spam med høj tillid eller flere mængder:

- **Bloker** afsender: Klik på dette link for at føje afsenderen til listen over blokerede afsendere _i din_ postkasse. Du kan få mere at vide [under Blokere en mailafsender](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).
- **Udgivelse**: Du kan slippe meddelelsen her uden at gå til **Karantæne** i Microsoft 365 Defender portal.
- **Gennemse**: Klik på dette link for at  gå til Karantæne i Microsoft 365 Defender-portalen, hvor du kan (afhængigt af, hvorfor meddelelsen var i karantæne), frigive, slette eller rapportere dine meddelelser, der er i karantæne. Få mere at vide under [Find og slip meddelelser, der er sat i karantæne, som bruger i EOP](find-and-release-quarantined-messages-as-a-user.md).

![Eksempel på besked om karantæne.](../../media/end-user-spam-notification.png)

> [!NOTE]
> En blokeret afsender kan stadig sende dig mails. Alle meddelelser fra denne afsender, der sender dem til din postkasse, flyttes straks til mappen Uønsket mail. Fremtidige meddelelser fra denne afsender sendes til mappen Uønsket mail eller til karantæne. Hvis du vil slette disse meddelelser ved modtagelse i stedet for at modne dem, skal du bruge [regler for mailflow](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (også kaldet transportregler) til at slette meddelelser ved modtagelse.
