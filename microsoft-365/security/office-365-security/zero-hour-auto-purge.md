---
title: Automatisk udrensning på nul timer i Microsoft Defender for Office 365
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
description: Automatisk tømning på nul time (ZAP) flytter leverede meddelelser med tilbagevirkende kraft i en Exchange Online postkasse til mappen Uønsket mail eller karantæne, der anses for at være spam, phishing eller indeholder malware efter levering.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bd9bb3f231e42c625c87669417210281d1d5a3df
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739455"
---
# <a name="zero-hour-auto-purge-zap-in-exchange-online"></a>Automatisk udrensning (ZAP) på nul timer i Exchange Online

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

## <a name="zero-hour-auto-purge-zap-basics"></a>Grundlæggende oplysninger om automatisk fjernelse på nul timer (ZAP)

I Microsoft 365 organisationer med postkasser i Exchange Online er ZAP (automatisk fjernelse på nul timer) en funktion til mailbeskyttelse, der med tilbagevirkende kraft registrerer og neutraliserer skadelige phishing-, spam- eller malwaremeddelelser, der allerede er blevet leveret til Exchange Online postkasser.

ZAP fungerer ikke i enkeltstående Exchange Online Protection-miljøer (EOP), der beskytter Exchange postkasser i det lokale miljø.

## <a name="how-zap-works"></a>Sådan fungerer ZAP

Spam og malware signaturer opdateres i tjenesten i realtid på daglig basis. Brugerne kan dog stadig modtage ondsindede meddelelser af en række forskellige årsager, herunder hvis indhold er våben, efter at de er blevet leveret til brugerne. ZAP løser dette problem ved løbende at overvåge opdateringer af spam- og malwaresignaturer i tjenesten. ZAP kan finde og fjerne meddelelser, der allerede findes i en brugers postkasse.

ZAP-handlingen er problemfri for brugeren. de får ikke besked, hvis en meddelelse registreres og flyttes.

[Pengeskab afsenderlister](create-safe-sender-lists-in-office-365.md), regler for mailflow (også kaldet transportregler), indbakkeregler eller yderligere filtre har forrang over ZAP. På samme måde som med det, der sker i et mailflow, betyder det, at selvom tjenesten bestemmer, at den leverede meddelelse har brug for ZAP, reageres meddelelsen ikke på grund af konfigurationen af sikre afsendere. Dette er en anden grund til at være forsigtig med at konfigurere meddelelser for at omgå filtrering.

Se denne korte video for at få mere at vide om, hvordan ZAP i Microsoft Defender for Office 365 automatisk registrerer og neutraliserer trusler i en mail. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGrLg]

### <a name="zero-hour-auto-purge-zap-for-malware"></a>Nultimers automatisk fjernelse (ZAP) for malware

For **læste eller ulæste meddelelser** , der efter levering viser sig at indeholde malware, sætter ZAP den meddelelse, der indeholder den vedhæftede malware, i karantæne. Som standard er det kun administratorer, der kan få vist og administrere karantænelagrede malwaremeddelelser. Men administratorer kan oprette og bruge _karantænepolitikker_ til at definere, hvad brugerne har tilladelse til at gøre med meddelelser, der er sat i karantæne som malware. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).

ZAP til malware er som standard aktiveret i politikker for antimalware. Du kan få flere oplysninger under [Konfigurer politikker for antimalware i EOP](configure-anti-malware-policies.md).

### <a name="zero-hour-auto-purge-zap-for-phishing"></a>Automatisk fjernelse (ZAP) på nul timer for phishing

For **læste eller ulæste meddelelser** , der identificeres som phishing efter levering, afhænger ZAP-resultatet af den handling, der er konfigureret for en dom for filtrering af **phishing-mails** i den relevante politik for anti-spam. De tilgængelige filtreringshandlinger for phishing og deres mulige ZAP-resultater er beskrevet på følgende liste:

- **Tilføj X-Header**, **Forudindstillet emnelinje med tekst**, **Omdiriger meddelelse til mailadresse**, **Slet meddelelse**: ZAP udfører ingen handling på meddelelsen.

- **Flyt meddelelsen til uønsket mail**: ZAP flytter meddelelsen til mappen Uønsket mail. Du kan få flere oplysninger under [Konfigurer indstillinger for uønsket mail på Exchange Online postkasser i Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Karantænemeddelelse**: ZAP sætter meddelelsen i karantæne.

ZAP til phishing er som standard aktiveret i politikker til bekæmpelse af spam, og standardhandlingen for dommen til filtrering af **phishing-mail** er **Karantænemeddelelse**, hvilket betyder, at ZAP til phishing sætter meddelelsen i karantæne som standard.

Du kan få flere oplysninger om konfiguration af dommene om filtrering af spam under [Konfigurer politikker mod spam i Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="zero-hour-auto-purge-zap-for-high-confidence-phishing"></a>Zap (automatisk tøm på nul time) for phishing med høj genkendelsessikkerhed

I forbindelse med **læste eller ulæste meddelelser** , der identificeres som phishing med høj sikkerhed efter levering, sætter ZAP meddelelsen i karantæne. Som standard er det kun administratorer, der kan få vist og administrere meddelelser med høj genkendelsessikkerhed i karantæne. Men administratorer kan oprette og bruge _karantænepolitikker_ til at definere, hvad brugerne har tilladelse til at gøre med meddelelser, der er sat i karantæne som phishing med høj tillid. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md)

ZAP for phish med høj genkendelsessikkerhed er som standard aktiveret. Du kan få flere oplysninger under [Sikker som standard i Office 365](secure-by-default.md).

### <a name="zero-hour-auto-purge-zap-for-spam"></a>Automatisk udrensning (ZAP) på nul timer for spam

For **ulæste meddelelser**, der identificeres som spam efter levering, afhænger ZAP-resultatet af den handling, der er konfigureret til spamfiltreringssagen i den gældende politik for spam. De tilgængelige filtreringshandlinger for spam og deres mulige ZAP-resultater er beskrevet på følgende liste:

- **Tilføj X-Header**, **Forudindstillet emnelinje med tekst**, **Omdiriger meddelelse til mailadresse**, **Slet meddelelse**: ZAP udfører ingen handling på meddelelsen.

- **Flyt meddelelsen til uønsket mail**: ZAP flytter meddelelsen til mappen Uønsket mail. Du kan få flere oplysninger under [Konfigurer indstillinger for uønsket mail på Exchange Online postkasser i Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Karantænemeddelelse**: ZAP sætter meddelelsen i karantæne. Slutbrugere kan som standard få vist og administrere spam-karantænemeddelelser, hvor de er modtager. Men administratorer kan oprette og bruge _karantænepolitikker_ til at definere, hvad brugerne har tilladelse til at gøre med meddelelser, der er sat i karantæne som spam. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md)

Som standard er ZAP for spam aktiveret i politikker til bekæmpelse af spam, og standardhandlingen for dom for filtrering af **spam** er **Flyt meddelelse til mappen Uønsket mail**, hvilket betyder, at SPAM ZAP flytter **ulæste** meddelelser til mappen Uønsket mail som standard.

Du kan få flere oplysninger om konfiguration af dommene om filtrering af spam under [Konfigurer politikker mod spam i Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="zero-hour-auto-purge-zap-considerations-for-microsoft-defender-for-office-365"></a>Zap-overvejelser (automatisk sletning) på nul timer for Microsoft Defender for Office 365

ZAP sætter ikke meddelelser i karantæne, der er i gang med [dynamisk levering](safe-attachments.md#dynamic-delivery-in-safe-attachments-policies) i Pengeskab scanning af politikken vedhæftede filer, eller hvor EOP-malwarefiltrering allerede har erstattet den vedhæftede fil med Malware **Alert Text.txt-filen**. Hvis der modtages et phishing- eller spamsignal for disse typer meddelelser, og den filtrerende dom i politikken for bekæmpelse af spam er indstillet til at udføre en handling på meddelelsen (Flyt til uønsket, Omdirigering, Slet eller Karantæne), vil ZAP som standard bruge handlingen 'Flyt til uønsket'.

## <a name="how-to-see-if-zap-moved-your-message"></a>Sådan kan du se, om ZAP har flyttet din meddelelse

Hvis du vil finde ud af, om ZAP har flyttet din meddelelse, har du følgende muligheder:

- **Antal meddelelser**: Brug [visningen Mailflow i statusrapporten Mailflow](view-email-security-reports.md#mailflow-view-for-the-mailflow-status-report) til at se antallet af ZAP-berørte meddelelser for det angivne datointerval.
- **Meddelelsesoplysninger**: Brug [Threat Explorer (og registreringer i realtid)](threat-explorer.md) til at filtrere **alle mailhændelser** efter værdien **ZAP** for kolonnen **Ekstra handling** .

> [!NOTE]
> ZAP logføres ikke i overvågningslogfilerne for Exchange postkasse som en systemhandling.

## <a name="zero-hour-auto-purge-zap-faq"></a>Ofte stillede spørgsmål om automatisk fjernelse på nul timer (ZAP)

### <a name="what-happens-if-a-legitimate-message-is-moved-to-the-junk-email-folder"></a>Hvad sker der, hvis en gyldig meddelelse flyttes til mappen Uønsket mail?

Du skal følge den normale rapporteringsproces for [falske positiver](report-junk-email-messages-to-microsoft.md). Den eneste årsag til, at meddelelsen flyttes fra indbakken til mappen Uønsket mail, er, at tjenesten har registreret, at meddelelsen er spam eller skadelig.

### <a name="what-if-i-use-the-quarantine-folder-instead-of-the-junk-mail-folder"></a>Hvad gør jeg, hvis jeg bruger mappen Karantæne i stedet for mappen Uønsket mail?

ZAP reagerer på en meddelelse, der er baseret på konfigurationen af dine anti-spam-politikker, som beskrevet tidligere i denne artikel.

### <a name="what-if-im-using-safe-senders-mail-flow-rules-or-allowedblocked-sender-lists"></a>Hvad gør jeg, hvis jeg bruger sikre afsendere, regler for mailflow eller lister over tilladte/blokerede afsendere?

Pengeskab afsendere, regler for mailflow eller bloker og tillad, at organisationens indstillinger har forrang. Disse meddelelser er udelukket fra ZAP, da tjenesten gør, hvad du har konfigureret den til at gøre. Dette er en anden grund til at være forsigtig med at konfigurere meddelelser for at omgå filtrering.

### <a name="what-are-the-licensing-requirements-for-zero-hour-auto-purge-zap-to-work"></a>Hvad er licenskravene for automatisk fjernelse på nul timer (ZAP) til at fungere?

Der er ingen begrænsninger på licenser. ZAP fungerer på alle postkasser, der hostes på Exchange online. ZAP fungerer ikke i enkeltstående Exchange Online Protection-miljøer (EOP), der beskytter Exchange postkasser i det lokale miljø.

### <a name="what-if-a-message-is-moved-to-another-folder-eg-inbox-rules"></a>Hvad sker der, hvis en meddelelse flyttes til en anden mappe (f.eks. indbakkeregler)?

Automatisk fjernelse på nul timer fungerer stadig, så længe meddelelsen ikke er slettet, eller hvis den samme eller stærkere handling ikke allerede er anvendt. Hvis politikken til bekæmpelse af phishing f.eks. er indstillet til at sætte meddelelsen i karantæne, og meddelelsen allerede findes i uønsket mail, vil ZAP udføre en handling for at sætte meddelelsen i karantæne.

### <a name="how-does-zap-affect-mailboxes-on-hold"></a>Hvordan påvirker ZAP postkasser i venteposition?

Automatisk fjernelse på nul timer vil sætte meddelelser fra postkasser i venteposition i karantæne. ZAP kan flytte meddelelser til mappen Uønsket mail baseret på den handling, der er konfigureret til en spam- eller phishing-dom i politikker til bekæmpelse af spam.

Du kan få flere oplysninger om ventepositioner i Exchange Online under [Bevarelse på stedet og bevarelse af procesførelse i Exchange Online](/Exchange/security-and-compliance/in-place-and-litigation-holds).
