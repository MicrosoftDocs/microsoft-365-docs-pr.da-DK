---
title: Automatisk tømning uden time i Microsoft Defender for Office 365
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
- MBS150
- MET150
ms.assetid: 96deb75f-64e8-4c10-b570-84c99c674e15
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Automatisk tømning (ZAP) med tilbagevirkende kraft flytter leveret meddelelser i en Exchange Online-postkasse til mappen uønsket mail eller karantæne, der findes at være spam, phishing eller indeholder malware efter levering.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a48f5eb1d45af16ab275c16d2965dc9a578d9312
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2022
ms.locfileid: "63587518"
---
# <a name="zero-hour-auto-purge-zap-in-exchange-online"></a>Automatisk tømning (ZAP) i nul timer i Exchange Online

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

## <a name="zero-hour-auto-purge-zap-basics"></a>Grundlæggende om automatisk tømning (ZAP) uden time

I Microsoft 365 organisationer med postkasser i Exchange Online er automatisk tømning (ZAP) uden time en funktion til beskyttelse af mail, som med tilbagevirkende kraft registrerer og neutraliserer skadelige phishing-, spam- eller malwaremeddelelser, der allerede er blevet leveret til Exchange Online-postkasser.

ZAP fungerer ikke i enkeltstående Exchange Online Protection (EOP),-miljøer, der beskytter lokale Exchange postkasser.

## <a name="how-zap-works"></a>Sådan fungerer ZAP

Signaturer til spam og malware opdateres dagligt i tjenesten i realtid. Brugerne kan dog stadig modtage skadelige meddelelser af en række forskellige årsager, herunder hvis indhold er standardiseret, efter det er blevet leveret til brugerne. ZAP løser dette problem ved kontinuerligt at overvåge opdateringer af spam- og malwaresignaturerne i tjenesten. ZAP kan finde og fjerne meddelelser, der allerede findes i en brugers postkasse.

ZAP-handlingen er problemfri for brugeren; de får ikke besked, hvis en meddelelse registreres og flyttes.

[Pengeskab afsenderlister](create-safe-sender-lists-in-office-365.md), regler for mailflow (også kaldet transportregler), indbakkeregler eller ekstra filtre tilsidesætter ZAP. Ligesom det, der sker i mailflowet, betyder det, at selvom tjenesten bestemmer, at den leveres meddelelse har brug for ZAP, reageres meddelelsen ikke på grund af konfigurationen af afsendere, der er tillid til. Dette er en anden grund til at være forsigtig med at konfigurere meddelelser til at tilsidesætte filtrering.

### <a name="zero-hour-auto-purge-zap-for-malware"></a>Nul-timers automatisk tømning (ZAP) for malware

For **læste eller ulæste meddelelser** , der indeholder malware efter levering, sætter ZAP den meddelelse i karantæne, der indeholder den vedhæftede malware. Som standard er det kun administratorer, der kan få vist og administrere malwaremeddelelser i karantæne. Men administratorer kan oprette og bruge karantænepolitikker  til at definere, hvad brugerne har tilladelse til at gøre i meddelelser, der er sat i karantæne som malware. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).

ZAP er som standard aktiveret for malware i antimalwarepolitikker. Få mere at vide under [Konfigurer antimalwarepolitikker i EOP](configure-anti-malware-policies.md).

### <a name="zero-hour-auto-purge-zap-for-phishing"></a>Nul-timers automatisk tømning (ZAP) for phishing

For **læste eller ulæste** meddelelser, der identificeres som phishing efter levering, afhænger ZAP-resultatet af den handling, der er konfigureret til en phishing-mailfiltreringkonstering med den gældende antispampolitik. De tilgængelige filtreringskriteriehandlinger for phishing og deres mulige ZAP-resultater er beskrevet på følgende liste:

- **Tilføj X-brevhoved**, **forudindstillet** emnelinje med **tekst,** Omdiriger meddelelse til **mailadresse, Slet** meddelelse: ZAP gør ingen handling på meddelelsen.

- **Flyt meddelelsen til uønsket mail**: ZAP flytter meddelelsen til mappen Uønsket mail. Du kan finde flere oplysninger [i Konfigurere indstillinger for uønsket mail Exchange Online postkasser i Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Karantænemeddelelse**: ZAP sætter meddelelsen i karantæne.

Som standard er ZAP til phishing aktiveret i antispampolitikker, og standardhandlingen for filtrering af **phishing-mail** er karantænemeddelelse **, hvilket** betyder, at ZAP til phishingkarantæne får meddelelsen som standard.

Du kan finde flere oplysninger om konfigurering af spamfiltrering under [Konfigurer politikker for uønsket post Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="zero-hour-auto-purge-zap-for-high-confidence-phishing"></a>Nul-timers automatisk tømning (ZAP) for phishing med høj sikkerhed

For **læste eller ulæste meddelelser** , der er identificeret som phishing med høj tillid efter levering, sætter ZAP meddelelsen i karantæne. Som standard er det kun administratorer, der kan få vist og administrere phish-meddelelser, der er sat i karantæne. Men administratorer kan oprette og bruge karantænepolitikker  til at definere, hvad brugerne har tilladelse til at gøre på meddelelser, der er sat i karantæne, som phishing med høj tillid. Få mere at vide under [Karantænepolitikker](quarantine-policies.md)

ZAP for phish er aktiveret som standard. Du kan finde flere oplysninger [under Sikkerhed som standard i Office 365](secure-by-default.md).

### <a name="zero-hour-auto-purge-zap-for-spam"></a>Nul-timers automatisk tømning (ZAP) for spam

For **ulæste** meddelelser, der identificeres som spam efter levering, afhænger ZAP-resultatet af den handling, der er konfigureret til spamfiltreringkonfigurering med den gældende antispampolitik. De tilgængelige filtreringskriteriehandlinger for spam og deres mulige ZAP-resultater er beskrevet på følgende liste:

- **Tilføj X-brevhoved**, **forudindstillet** emnelinje med **tekst,** Omdiriger meddelelse til **mailadresse, Slet** meddelelse: ZAP gør ingen handling på meddelelsen.

- **Flyt meddelelsen til uønsket mail**: ZAP flytter meddelelsen til mappen Uønsket mail. Du kan finde flere oplysninger [i Konfigurere indstillinger for uønsket mail Exchange Online postkasser i Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Karantænemeddelelse**: ZAP sætter meddelelsen i karantæne. Slutbrugere kan som standard få vist og administrere meddelelser, der er i spamkarantæne, hvor de er modtager. Men administratorer kan oprette og bruge karantænepolitikker  til at definere, hvad brugerne har tilladelse til at gøre i meddelelser, der er sat i karantæne som spam. Få mere at vide under [Karantænepolitikker](quarantine-policies.md)

Spam-ZAP er som standard aktiveret i antispampolitikker, og standardhandlingen for  spamfiltrering er Flyt meddelelsen til mappen Uønsket **mail, hvilket** betyder, at spam  ZAP som standard flytter ulæste meddelelser til mappen Uønsket mail.

Du kan finde flere oplysninger om konfigurering af spamfiltrering under [Konfigurer politikker for uønsket post Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="zero-hour-auto-purge-zap-considerations-for-microsoft-defender-for-office-365"></a>Overvejelser om automatisk tømning uden time (ZAP) for Microsoft Defender Office 365

ZAP sætter ikke meddelelser i karantæne, der er i gang med dynamisk [](safe-attachments.md#dynamic-delivery-in-safe-attachments-policies) levering i Pengeskab Scanning af politik for vedhæftede filer, eller hvor EOP-malwarefiltrering allerede har erstattet den vedhæftede fil med **malware alert Text.txt-filen**. Hvis der modtages et phishing- eller spamsignal for disse typer meddelelser, og filtreringen i antispampolitikken er indstillet til at gøre noget ved meddelelsen (Flyt til Uønsket, Omdiriger, Slet eller Karantæne), vil ZAP som standard være indstillet til en handling med "Flyt til uønsket".

## <a name="how-to-see-if-zap-moved-your-message"></a>Sådan kan du se, om ZAP har flyttet din meddelelse

Hvis du vil finde ud af, om ZAP har flyttet din meddelelse, har du følgende muligheder:

- **Antal meddelelser**: Brug visningen [Mailflow i statusrapporten Mailflow](view-email-security-reports.md#mailflow-view-for-the-mailflow-status-report) for at se antallet af meddelelser, som er blevet påvirket af ZAP, for det angivne datointerval.
- **Meddelelsesdetaljer**: [Brug Trusselsstifinder (](threat-explorer.md)og registreringer i realtid)  til at filtrere Alle mailhændelser efter værdien **ZAP** for **kolonnen Yderligere** handling.

**Bemærk**: ZAP er ikke logget på Exchange i postkassens overvågningslog som en systemhandling.

## <a name="zero-hour-auto-purge-zap-faq"></a>Ofte stillede spørgsmål om automatisk tømning (ZAP) uden time

### <a name="what-happens-if-a-legitimate-message-is-moved-to-the-junk-email-folder"></a>Hvad sker der, hvis en legitim meddelelse flyttes til mappen Uønsket mail?

Du skal følge den normale rapporteringsproces for [falske positive](report-junk-email-messages-to-microsoft.md). Den eneste grund til, at meddelelsen blev flyttet fra indbakken til mappen Uønsket mail, vil være, at tjenesten har besluttet, at meddelelsen er spam eller skadelig.

### <a name="what-if-i-use-the-quarantine-folder-instead-of-the-junk-mail-folder"></a>Hvad gør jeg, hvis jeg bruger mappen Karantæne i stedet for mappen Uønsket mail?

ZAP vil handle på en meddelelse, der er baseret på konfigurationen af dine antispampolitikker, som beskrevet tidligere i denne artikel.

### <a name="what-if-im-using-safe-senders-mail-flow-rules-or-allowedblocked-sender-lists"></a>Hvad gør jeg, hvis jeg bruger afsendere, der er tillid til, regler for mailflow eller lister over tilladte/blokerede afsendere?

Pengeskab afsendere, regler for mailflow eller blokere og tillade, at organisationsindstillinger har forrang. Disse meddelelser er ikke medtaget i ZAP, da tjenesten gør det, du har konfigureret den til at gøre. Dette er en anden grund til at være forsigtig med at konfigurere meddelelser til at tilsidesætte filtrering.

### <a name="what-are-the-licensing-requirements-for-zero-hour-auto-purge-zap-to-work"></a>Hvad skal licenskrav for automatisk TØM (Zero-hour tømning) fungere?

Der er ingen begrænsninger på licenser. ZAP fungerer på alle postkasser, der hostes Exchange online. ZAP fungerer ikke i enkeltstående Exchange Online Protection (EOP),-miljøer, der beskytter lokale Exchange postkasser.

### <a name="what-if-a-message-is-moved-to-another-folder-eg-inbox-rules"></a>Hvad nu, hvis en meddelelse flyttes til en anden mappe (f.eks. indbakkeregler)?

Automatisk tømning uden time fungerer stadig, så længe meddelelsen ikke er blevet slettet, eller så længe den samme eller stærkere handling ikke allerede er anvendt. Hvis f.eks. antiphishing-politikken er indstillet til karantæne, og meddelelsen allerede findes i uønsket mail, vil ZAP tage skridt til at sætte meddelelsen i karantæne.

### <a name="how-does-zap-affect-mailboxes-on-hold"></a>Hvordan påvirker ZAP postkasser i venteposition?

Nul-timers automatisk tømning sætter meddelelser i karantæne fra postkasser, der er sat i venteposition. ZAP kan flytte meddelelser til mappen Uønsket mail baseret på den handling, der er konfigureret til spam eller phishingkonkonfigurerede i antispampolitikker.

Du kan finde flere oplysninger om Exchange Online i [Direkte venteposition og retslig venteposition i Exchange Online](/Exchange/security-and-compliance/in-place-and-litigation-holds).
