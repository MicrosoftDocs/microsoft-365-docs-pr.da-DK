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
description: Få mere at vide om indstillingen Sikker som standard i Exchange Online Protection (EOP)
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ab5fa5e9c769d68589b722e8fdc9976fa616e6ac
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648123"
---
# <a name="secure-by-default-in-office-365"></a>Sikker som standard i Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

"Sikker som standard" er et ord, der bruges til at definere de standardindstillinger, der er mest sikre som muligt.

Men sikkerheden skal afbalanceres med produktiviteten. Dette kan omfatte justering på tværs af:

- **Anvendelighed**: Indstillinger bør ikke komme i vejen for brugerproduktivitet.
- **Risiko**: Sikkerhed kan blokere vigtige aktiviteter.
- **Ældre indstillinger**: Nogle konfigurationer til ældre produkter og funktioner skal muligvis vedligeholdes af forretningsmæssige årsager, selvom nye, moderne indstillinger forbedres.

Microsoft 365 organisationer med postkasser i Exchange Online er beskyttet af EOP (Exchange Online Protection). Denne beskyttelse omfatter:

- Mail med mistanke om malware vil automatisk blive sat i karantæne. Hvorvidt modtagere får besked om karantænelagrede malwaremeddelelser styres af karantænepolitikken og indstillingerne i politikken for antimalware. Du kan få flere oplysninger under [Konfigurer politikker for antimalware i EOP](configure-anti-malware-policies.md).
- Mail, der er identificeret som phishing med høj tillid, håndteres i henhold til den politik, der skal bekæmpe spam. Se [Konfigurer politikker for spam i EOP](configure-your-spam-filter-policies.md).

Du kan få flere oplysninger om EOP [under Exchange Online Protection oversigt](exchange-online-protection-overview.md).

Da Microsoft ønsker at beskytte vores kunder som standard, anvendes nogle lejeres tilsidesættelser ikke for malware eller phishing med høj genkendelsessikkerhed. Disse tilsidesættelser omfatter:

- Lister over tilladte afsendere eller tilladte domænelister (politikker til bekæmpelse af spam)
- afsendere af Outlook Pengeskab
- Liste over IP-tilladte (forbindelsesfiltrering)
- Exchange regler for mailflow (også kaldet transportregler)

Du kan finde flere oplysninger om disse tilsidesættelser på [listerne Opret sikre afsendere](create-safe-sender-lists-in-office-365.md).

> [!NOTE]
> Vi har frarådet handlingen **Flyt meddelelse til uønsket mail for at** få en dom for **phishingmail med høj tillid** i EOP-politikker til bekæmpelse af spam. Politikker til bekæmpelse af spam, der bruger denne handling til phishing-meddelelser med høj sikkerhed, konverteres til **karantænemeddelelse**. Handlingen **Omdiriger meddelelse til mailadresse** for phishing-meddelelser med høj genkendelsessikkerhed påvirkes ikke.

Sikker er som standard ikke en indstilling, der kan slås til eller fra, men er den måde, som vores filtrering fungerer på, så potentielt farlige eller uønskede meddelelser holdes væk fra dine postkasser. Phishing-meddelelser med høj sikkerhed og malware skal sættes i karantæne. Som standard er det kun administratorer, der kan administrere meddelelser, der er sat i karantæne som malware eller phishing med høj sikkerhed, og de kan også rapportere falske positiver til Microsoft derfra. Du kan få flere oplysninger under [Administrer karantænerede meddelelser og filer som administrator i EOP](manage-quarantined-messages-and-files.md).

## <a name="more-on-why-were-doing-this"></a>Mere om, hvorfor vi gør dette

Ånden i at være sikker som standard er: Vi foretager den samme handling på den meddelelse, som du ville tage, hvis du vidste meddelelsen ondsindet, selv når en konfigureret undtagelse ellers ville tillade meddelelsen at blive leveret. Dette er den samme fremgangsmåde, som vi altid har brugt på malware, og nu udvider vi denne samme funktionsmåde til phishing-meddelelser med høj tillid.

Vores data angiver, at der er 30 gange større sandsynlighed for, at en bruger klikker på et skadeligt link i meddelelser i mappen Uønsket mail i forhold til Karantæne. Vores data angiver også, at den falske positive rate (gode meddelelser markeret som dårlige) for phishing-meddelelser med høj genkendelsessikkerhed er meget lav, og administratorer kan løse eventuelle falske positiver med administratorindsendelser.

Vi har også fastslået, at de tilladte afsender- og tilladte domænelister i politikker for anti-spam og Pengeskab Afsendere i Outlook var for brede og forårsager mere skade end gavn.

For at sige det på en anden måde: Som en sikkerhedstjeneste handler vi på dine vegne for at forhindre, at dine brugere kompromitteres.

## <a name="exceptions"></a>Undtagelser

Du bør kun overveje at bruge tilsidesættelser i følgende scenarier:

- Phishing-simuleringer: Simulerede angreb kan hjælpe dig med at identificere sårbare brugere, før et reelt angreb påvirker din organisation. Hvis du vil forhindre, at phishing-simuleringsmeddelelser filtreres, skal du se [Konfigurer phishing-simuleringer fra tredjepart i den avancerede leveringspolitik](/microsoft-365/security/office-365-security/configure-advanced-delivery#use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy).
- Sikkerheds-/SecOps-postkasser: Dedikerede postkasser, der bruges af sikkerhedsteams til at hente ufiltrerede meddelelser (både gode og dårlige). Teams kan derefter gennemse for at se, om de indeholder skadeligt indhold. Du kan få flere oplysninger under [Konfigurer SecOps-postkasser i politikken for avanceret levering](/microsoft-365/security/office-365-security/configure-advanced-delivery#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).
- Tredjepartsfiltre: Sikker gælder som standard kun, når MX-posten for dit domæne er angivet til Exchange Online Protection (contoso.mail.protection.outlook.com). Hvis den er indstillet til en anden tjeneste eller enhed, er det muligt at tilsidesætte Secure som standard med en [transportregel](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl) for at omgå al spamfiltrering. Når Microsoft registrerer meddelelser som Phish med høj genkendelsessikkerhed med denne regel på plads, leveres de stadig til indbakken. 
- Falske positiver: Det kan være en god idé midlertidigt at tillade visse meddelelser, der stadig analyseres af Microsoft [via Administration indsendelser](admin-submission.md). Som med alle tilsidesættelser anbefales det, at de er midlertidige.
