---
title: Karantænemeddelelser (meddelelser fra slutbrugere om spam) i Microsoft 365
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
description: Administratorer kan få mere at vide om meddelelser om spam fra slutbrugere for karantænemeddelelser i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c1688e4a56787c9593aae7006a05d52b16558647
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/13/2022
ms.locfileid: "65393474"
---
# <a name="use-quarantine-notifications-to-release-and-report-quarantined-messages"></a>Brug karantænemeddelelser til at frigive og rapportere karantænemeddelelser

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående EOP-organisationer (Exchange Online Protection) uden Exchange Online postkasser, indeholder karantæne potentielt farlige eller uønskede meddelelser. Du kan få flere oplysninger under [Karantænemeddelelser i EOP](quarantine-email-messages.md).

_Karantænepolitikker_ definerer, hvad brugerne må gøre for at sætte meddelelser i karantæne, afhængigt af hvorfor meddelelsen blev sat i karantæne (for understøttede funktioner). Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md). Karantænepolitiet styrer også, om de berørte modtagere (herunder delte postkasser) modtager periodiske _karantænemeddelelser_ om deres karantænemeddelelser. Karantænemeddelelser er erstatning for slutbrugere af spammeddelelser for alle understøttede beskyttelsesfunktioner (ikke kun dom over spampolitik).

Karantænemeddelelser er ikke slået til i de indbyggede karantænemeddelelser med navnet AdminOnlyAccessPolicy eller DefaultFullAccessPolicy. Karantænemeddelelser er slået til i den indbyggede karantænepolitik med navnet NotificationEnabledPolicy [, hvis din organisation har den](quarantine-policies.md#full-access-permissions-and-quarantine-notifications). Ellers skal du [oprette og konfigurere en ny karantænepolitik](quarantine-policies.md#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal) for at aktivere karantænemeddelelser i karantænepolitikker.

Hvis du vil tillade, at indstillingen 'Bloker afsender' i karantænemeddelelser fungerer korrekt, skal brugerne desuden være aktiveret til fjern-PowerShell. Du kan finde instruktioner under [Aktivér eller deaktiver adgang til Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell).

Administratorer kan også bruge de globale indstillinger i karantænepolitikker til at tilpasse afsenderens viste navn, ansvarsfraskrivelsetekst på forskellige sprog og det firmalogo, der bruges i karantænemeddelelser. Du kan finde instruktioner under [Konfigurer indstillinger for global karantænemeddelelse](quarantine-policies.md#configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal).

I forbindelse med delte postkasser understøttes karantænemeddelelser kun for brugere, der har fået tildelt FullAccess-tilladelse til den delte postkasse. Du kan få flere oplysninger under [Brug EAC til at redigere delegering af delt postkasse](/Exchange/collaboration-exo/shared-mailboxes#use-the-eac-to-edit-shared-mailbox-delegation).

> [!NOTE]
> Meddelelser, der er sat i karantæne som phishing med høj sikkerhed, malware, efter regler for mailflow (også kendt som transportregler) eller Pengeskab Vedhæftede filer-politikker i Defender for Office 365 er som standard kun tilgængelige for administratorer (som standard bruges karantænepolitikken for AdminOnlyAccessPolicy). Du kan få flere oplysninger under [Administrer karantænerede meddelelser og filer som administrator i EOP](manage-quarantined-messages-and-files.md).
>
> I øjeblikket understøttes karantænemeddelelser ikke for grupper.

Når du modtager en karantænemeddelelse, er følgende oplysninger altid tilgængelige for hver karantænemeddelelse:

- **Afsender**: Afsendelsesnavnet og mailadressen på den karantænerede meddelelse.
- **Emne**: Emnelinjeteksten i den karantænerede meddelelse.
- **Dato**: Den dato og det klokkeslæt (i UTC), hvor meddelelsen blev sat i karantæne.

De handlinger, der er tilgængelige i karantænemeddelelsen, afhænger af, hvorfor meddelelsen blev sat i karantæne, og de tilladelser, der er tildelt af den tilknyttede karantænepolitik. Du kan finde flere oplysninger under [Oplysninger om tilladelse til karantænepolitik](quarantine-policies.md#quarantine-policy-permission-details).

Følgende handlinger er som standard tilgængelige i karantænemeddelelsen for meddelelser, der er sat i karantæne som spam, spam med høj genkendelsessikkerhed eller masse:

- **Bloker afsender**: Klik på dette link for at føje afsenderen til listen Over blokerede afsendere i _postkassen_ . Du kan få flere oplysninger under [Bloker en mailsender](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).
- **Version**: Du kan frigive meddelelsen her uden at gå til **karantæne** på Microsoft 365 Defender-portalen.
- **Gennemse**: Klik på dette link for at gå til **Karantæne** på Microsoft 365 Defender-portalen, hvor du kan (afhængigt af hvorfor meddelelsen blev sat i karantæne) få vist, frigive, slette eller rapportere dine karantænemeddelelser. Du kan finde flere oplysninger under [Find og frigiv karantænemeddelelser som bruger i EOP](find-and-release-quarantined-messages-as-a-user.md).

:::image type="content" source="../../media/end-user-spam-notification.png" alt-text="Eksemplet på en karantænemeddelelse" lightbox="../../media/end-user-spam-notification.png":::

> [!NOTE]
> En blokeret afsender kan stadig sende dig en mail. Alle meddelelser fra denne afsender, der kommer til postkassen, flyttes straks til mappen Uønsket mail. Fremtidige meddelelser fra denne afsender går til mappen uønsket mail eller til karantæne. Hvis du vil slette disse meddelelser ved ankomsten i stedet for at quarantinere dem, skal du bruge [regler for mailflow](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (også kaldet transportregler) til at slette meddelelserne ved ankomsten.
