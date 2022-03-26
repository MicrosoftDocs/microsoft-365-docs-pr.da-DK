---
title: Sikker som standard i Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: 06/28/2021
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: Få mere at vide om den sikre standardindstilling i Exchange Online Protection (EOP)
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 59f29b0e923bdeb7481a64fb9ba1c3890e2b1369
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775494"
---
# <a name="secure-by-default-in-office-365"></a>Sikker som standard i Office 365

[!INCLUDE [Prerelease information](../includes/prerelease.md)]
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

"Sikker som standard" er et udtryk, der bruges til at definere de standardindstillinger, der er mest sikre som muligt.

Sikkerheden skal dog balanceres med produktivitet. Dette kan omfatte justering på tværs af:

- **Brugervenlighed**: Indstillinger ikke komme i vejen for brugernes produktivitet.
- **Risiko**: Sikkerhed kan blokere vigtige aktiviteter.
- **Ældre indstillinger**: Nogle konfigurationer af ældre produkter og funktioner skal muligvis vedligeholdes af forretningsmæssige årsager, selvom nye, moderne indstillinger er blevet forbedret.

Microsoft 365 organisationer med postkasser i Exchange Online er beskyttet af Exchange Online Protection (EOP). Denne beskyttelse omfatter:

- Mail med mistanke om malware bliver automatisk sat i karantæne. Om modtagerne får besked om malwaremeddelelser, der er sat i karantæne, styres af karantænepolitikken og indstillingerne i antimalwarepolitikken. Få mere at vide under [Konfigurer antimalwarepolitikker i EOP](configure-anti-malware-policies.md).
- Mails, der identificeres som phishing med høj tillid, håndteres i henhold til antispampolitikhandlingen. Se [Konfigurer antispam-politikker i EOP](configure-your-spam-filter-policies.md).

Du kan finde flere oplysninger om EOP [Exchange Online Protection oversigt.](exchange-online-protection-overview.md)

Da Microsoft ønsker at beskytte vores kunder som standard, anvendes nogle lejertilsidesættelser ikke for malware eller phishing med høj tillid. Disse tilsidesættelser omfatter:

- Tilladte afsenderlister eller lister over tilladte domæner (antispampolitikker)
- Outlook Pengeskab afsendere
- Liste over tilladte IP-adresser (forbindelsesfiltrering)
- Exchange regler for mailflow (også kaldet transportregler)

Du kan finde flere oplysninger om disse tilsidesættelser på Opret lister [over afsendere, der er tillid til](create-safe-sender-lists-in-office-365.md).

> [!NOTE]
> Vi har frarådet handlingen Flyt  meddelelsen til mappen Uønsket mail for at sikre, at **phishing-mailen** bliver meget tryg i EOP-antispampolitikker. Antispampolitikker, der bruger denne handling til phishingmeddelelser med høj tillid, konverteres til **en karantænemeddelelse**. Handlingen **Omdiriger meddelelse til mailadresse** for phishingmeddelelser med høj tillid påvirkes ikke.

Sikker er som standard ikke en indstilling, der kan slås til eller fra, men er den måde, vores filtrering fungerer ud af boksen på for at holde potentielt farlig eller uønskede meddelelser ude af dine postkasser. Malware og phishingmeddelelser med høj tillid skal være i karantæne. Som standard er det kun administratorer, der kan administrere meddelelser, der er i karantæne som malware eller phishing med høj tillid, og de kan også rapportere falske positive til Microsoft derfra. Få mere at vide under [Administrer meddelelser og filer, der er sat i karantæne som administrator i EOP](manage-quarantined-messages-and-files.md).

## <a name="more-on-why-were-doing-this"></a>Mere om, hvorfor vi gør dette

Ønsker du at være sikker som standard, er det, at vi gør det samme på den meddelelse, du ville tage, hvis du kendte meddelelsen skadelig, selv når en konfigureret undtagelse ellers ville tillade, at meddelelsen blev leveret. Dette er den samme fremgangsmåde, som vi altid har brugt på malware, og nu udvider vi den samme funktionsmåde til phishing-meddelelser med høj tillid.

Vores data angiver, at en bruger er 30 gange mere tilbøjelig til at klikke på et skadeligt link i meddelelser i mappen Uønsket mail kontra karantæne. Vores data indikerer også, at den falske positive hastighed (gode meddelelser, der er markeret som dårlige) for phishingmeddelelser med høj tillid er meget lav, og administratorer kan løse eventuelle falske positive med administratorindlæggene.

Vi besluttede også, at listerne over tilladte afsendere og tilladte domæner i antispam- og Pengeskab-afsendere i Outlook var for brede og forårsagede mere skade end gavn.

Sagt på en anden måde: Som sikkerhedstjeneste handler vi på dine vegne for at forhindre dine brugere i at blive kompromitteret.

## <a name="exceptions"></a>Undtagelser

Du bør kun overveje at bruge tilsidesættelser i følgende scenarier:

- Phishing-simulering: Simulerede angreb kan hjælpe dig med at identificere følsomme brugere, før et rigtigt angreb påvirker din organisation. Hvis du vil forhindre phishing-simuleringsmeddelelser i at blive filtreret, skal du se [Konfigurer phishing-simulering fra tredjeparter i politikken for avanceret levering](/microsoft-365/security/office-365-security/configure-advanced-delivery#use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy).
- Sikkerhed/SecOps-postkasser: Dedikerede postkasser, der bruges af sikkerhedsteams til at få ufiltrerede meddelelser (både gode og dårlige). Teams kan derefter gennemse for at se, om de indeholder skadeligt indhold. Få mere at vide under [Konfigurer SecOps-postkasser i politikken for avanceret levering](/microsoft-365/security/office-365-security/configure-advanced-delivery#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).
- Tredjepartsfiltre: Sikker som standard gælder kun, når MX-posten for dit domæne er indstillet til Exchange Online Protection (contoso.mail.protection.outlook.com). Hvis den er indstillet til en anden tjeneste eller enhed, er det muligt at tilsidesætte Secure som standard med en [transportregel](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl) for at tilsidesætte al spamfiltrering. Når Microsoft registrerer meddelelser som Phish med denne regel på plads, leveres de stadig til indbakken. 
- Falske positive: Det kan være en god ide midlertidigt at tillade, at visse meddelelser stadig analyseres af Microsoft [via administratorindsendelser](admin-submission.md). Som med alle tilsidesættelser anbefales det, at de er midlertidige.
