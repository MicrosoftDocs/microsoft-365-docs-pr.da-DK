---
title: Beskyttelse mod uønsket post
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6a601501-a6a8-4559-b2e7-56b59c96a586
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om antispamindstillingerne og -filtrene, der er med til at forhindre spam Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1bc5d81b1221b73bcb701345b8db2f160380ba37
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/02/2021
ms.locfileid: "63587752"
---
# <a name="anti-spam-protection-in-eop"></a>Beskyttelse mod spam i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)

> [!NOTE]
> Dette emne er beregnet til administratorer. For slutbrugeremner skal du se Oversigt [over filteret mod uønsket mail og](https://support.microsoft.com/office/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089) [Få mere at vide om uønsket mail og phishing](https://support.microsoft.com/office/86c1d76f-4d5a-4967-9647-35665dc17c31).

I Microsoft 365 med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser, beskyttes mails automatisk mod spam (uønsket mail) af EOP.

Microsofts roadmap til mailsikkerhed omfatter en ikke-relaterede tilgang på tværs af produkter. EOP's antispam- og antiphishing-teknologi anvendes på tværs af vores mailplatforme for at give brugere de nyeste værktøjer og innovationer til antispam og antiphishing i hele netværket. Målet for EOP er at tilbyde en omfattende og brugbar mailtjeneste, der hjælper med at registrere og beskytte brugere mod uønsket mail, falske mailtrusler (phishing) og malware.

I og med brug af mail er det samme, som mailbrug er vokset, og det samme gør misbrug af mail. Uovervåget uønsket mail kan blokere indbakker og netværk, påvirke brugertilfredsheden og øge effektiviteten af legitim mailkommunikation. Det er derfor Microsoft fortsætter med at investere i antispamteknologier. Kort sagt starter det ved at indeholde og filtrere uønsket mail.

> [!TIP]
> Følgende antispamteknologier er nyttige, når du vil tillade eller blokere meddelelser baseret på meddelelsens konvolut (f.eks. afsenderens domæne eller meddelelsens kilde-IP-adresse). Hvis du vil tillade eller blokere meddelelser baseret på nyttedata (f.eks. URL-adresser i meddelelsen eller vedhæftede filer), skal du bruge portalen lejerens tilladelse [/blokeringsliste](tenant-allow-block-list.md).

## <a name="anti-spam-technologies-in-eop"></a>Antispamteknologier i EOP

For at reducere mængden af uønsket mail omfatter EOP beskyttelse mod uønsket mail, der bruger teknologier til filtrering af uønsket post til at identificere og adskille uønsket mail fra legitime mails. EOP-spamfiltrering lærer af kendte trusler mod spam og phishing samt brugerfeedback fra vores forbrugerplatform, Outlook.com. Løbende feedback fra EOP-brugere i klassificeringsprogrammet til uønsket mail hjælper med at sikre, at EOP-teknologierne kontinuerligt uddannes og forbedres.

Antispamindstillingerne i EOP består af følgende teknologier:

- **Filtrering** af forbindelse: Identificerer gode og dårlige mailkildeservere tidligt i den indgående mailforbindelse via ip-tilladelseslisten, listen over blokerede IP-adresser og listen over *sikre (en* dynamisk, men ikke-redigerbar liste over afsendere, der er tillid til, som vedligeholdes af Microsoft). Du skal konfigurere disse indstillinger i forbindelsesfilterpolitikken. Få mere at vide [under Konfigurer filtrering af forbindelse](configure-the-connection-filter-policy.md).

- **Spamfiltrering (indholdsfiltrering)**: EOP bruger spamfiltreringskriteriet **Spam****, Spam** med høj **tillid,** Massemail, **Phishing-mail** og **Phishing-mail** med høj grad af tillid til at klassificere meddelelser. Du kan konfigurere de handlinger, der skal skal laves, baseret på disse konklusioner, og du kan konfigurere, hvad brugerne har tilladelse til at gøre for meddelelser, der er sat i karantæne, og om brugeren modtager meddelelser i karantæne ved hjælp af [karantænepolitikker](quarantine-policies.md). Du kan finde flere oplysninger [i Konfigurere politikker for uønsket post Microsoft 365](configure-your-spam-filter-policies.md).

  > [!NOTE]
  > Som standard er spamfiltrering konfigureret til at sende meddelelser, der er markeret som spam, til modtagerens mappe med Uønsket mail. I hybridmiljøer, hvor EOP beskytter lokale Exchange-postkasser, skal du dog konfigurere to regler for mailflow (også kaldet transportregler) i din lokale Exchange-organisation for at genkende de EOP-spamoverskrifter, der føjes til meddelelser. Du kan få mere at [vide under Konfigurer EOP til at levere spam til mappen Uønsket mail i hybridmiljøer](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).

- **Udgående spamfiltrering**: EOP kontrollerer også for at sikre, at dine brugere ikke sender spam, hverken i udgående meddelelsesindhold eller ved at overskride begrænsninger for udgående meddelelser. Du kan finde flere oplysninger [i Konfigurere udgående spamfiltrering Microsoft 365](configure-the-outbound-spam-policy.md).

- **Efterlignet intelligens**: Få mere at vide under [Beskyttelse mod spoofing i EOP](anti-spoofing-protection.md).

## <a name="manage-errors-in-spam-filtering"></a>Administrer fejl i spamfiltrering

Det er muligt, at gode meddelelser kan identificeres som spam (også kaldet falske positive), eller at spam kan leveres til indbakken (også kaldet falske negativer). Du kan bruge forslagene i de følgende afsnit til at finde ud af, hvad der er sket, og hjælpe med at forhindre, at det sker fremover.

Her er nogle bedste fremgangsmåder, der gælder for begge scenarier:

- Rapportér altid meddelelser, der er klassificeret forkert, til Microsoft. Få mere at vide under [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

- **Undersøg antispam-brevhovederne**: Disse værdier fortæller dig, hvorfor en meddelelse blev markeret som spam, eller hvorfor spamfiltrering blev sprunget over. Du kan få mere at vide [under Brevhoveder for uønsket post](anti-spam-message-headers.md).

- **Peg din MX-post på Microsoft 365**: For at EOP kan yde den bedste beskyttelse, anbefaler vi altid, at du først får mail leveret Microsoft 365 mail. Du kan finde en vejledning [under Oprette DNS-poster for en hvilken som helst DNS-udbyder Microsoft 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

  Hvis MX-posten peger på en anden placering (f.eks. en tredjeparts antispamløsning eller -maskine), er det svært for EOP at levere nøjagtig spamfiltrering. I dette scenarie skal du konfigurere udvidet filtrering for forbindelser (også kaldet spring _over_). Du kan finde en [vejledning under Udvidet filtrering for forbindelser i Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

- **Brug mailgodkendelse**: Hvis du ejer et maildomæne, kan du bruge DNS til at sikre, at meddelelser fra afsendere på dette domæne er legitime. For at forhindre spam og uønsket spoofing i EOP skal du bruge alle følgende mailgodkendelsesmetoder:

  - **SPF**: Sender Policy Framework bekræfter meddelelsens kilde-IP-adresse over for ejeren af det afsendende domæne. Hvis du vil have en hurtig introduktion til SPF og få det konfigureret hurtigt, skal du se Konfigurer [SPF for at forhindre spoofing](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Hvis du vil have en mere dybdegående forståelse af, hvordan Microsoft 365 bruger SPF, eller til fejlfinding eller ikke-standardinstallationer, f.eks. hybride installationer, skal du starte med [Sådan bruger Microsoft 365 SPF (Sender Policy Framework) til at forhindre spoofing](how-office-365-uses-spf-to-prevent-spoofing.md).

  - **DKIM**: DomainKeys Identified Mail tilføjer en digital signatur i brevhovedet på meddelelser, der er sendt fra dit domæne. Få mere at vide under [Brug DKIM til at validere udgående mails, der sendes fra dit brugerdefinerede domæne Microsoft 365](use-dkim-to-validate-outbound-email.md).

  - **DMARC**: Domænebaseret meddelelsesgodkendelse, -rapportering og -overholdelse hjælper destinationens mailsystemer med at afgøre, hvad der skal gøre med meddelelser, som ikke kontrollerer SPF eller DKIM, og giver et andet tillidsniveau til dine mailpartnere. Få mere at vide under [Brug DMARC til at validere mail Microsoft 365](use-dmarc-to-validate-email.md).

- **Bekræft dine indstillinger** for massemails: Grænseværdien for masseklager, som du konfigurerer i antispampolitikker, bestemmer, om massemail (også kaldet grå _mail_) markeres som spam. Indstillingen Kun PowerShell-indstilling _MarkAsSpamBulkMail_ , der er til som standard, bidrager også til resultaterne. Du kan finde flere oplysninger [i Konfigurere politikker for uønsket post Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="prevent-the-delivery-of-spam-to-the-inbox"></a>Forhindre levering af spam til indbakken

- **Bekræft dine organisationsindstillinger**: Hold øje med indstillinger, der tillader meddelelser at springe spamfiltrering over (f.eks. hvis du føjer dit eget domæne til listen over tilladte domæner i politikker for uønsket post). Du kan finde vores anbefalede indstillinger under [Anbefalede indstillinger for EOP og Microsoft Defender for sikkerhed Office 365 Opret](recommended-settings-for-eop-and-office365.md) lister over [afsendere, der er tillid til](create-safe-sender-lists-in-office-365.md).

- **Brug de tilgængelige lister over blokerede afsendere**: Du kan få mere at vide [under Opret lister over blokerede afsendere](create-block-sender-lists-in-office-365.md).

- **Frameld dig massemails** Hvis meddelelsen er noget, brugeren har tilmeldt sig (nyhedsbreve, produktmeddelelser osv.) og indeholder et link til abonnement fra en anerkendt kilde, kan du overveje at bede dem om blot at opsige abonnementet.

- Separat **EOP: Opret regler for mailflow i det lokale Exchange til EOP-spamfiltreringkonfigureringkonstulering**: I hybridmiljøer, hvor EOP beskytter lokale Exchange-postkasser, skal du konfigurere regler for mailflow (også kaldet transportregler) i det lokale Exchange. Disse regler for mailflow oversætter reglen om spamfiltrering for EOP, så reglen om uønsket mail i postkassen kan flytte meddelelsen til mappen Uønsket mail. Du kan få mere at [vide under Konfigurer EOP til at levere spam til mappen Uønsket mail i hybridmiljøer](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).

### <a name="prevent-good-email-from-being-identified-as-spam"></a>Undgå, at gode mails identificeres som spam

Her er nogle trin, du kan gøre for at forhindre falske positive:

- **Kontrollér brugerens indstillinger for filtrering Outlook uønsket mail**:

  - **Kontrollér**, Outlook-filteret mod uønsket mail er deaktiveret: Når filteret Outlook uønsket mail er angivet til standardværdien Ingen automatisk **filtrering, forsøger** Outlook ikke at klassificere meddelelser som spam.  Når filteret er indstillet  til Lav eller **Høj, bruger** filteret til uønsket Outlook sin egen SmartScreen-filterteknologi til at identificere og flytte spam til mappen Uønsket mail, så du kan få falske positive. Bemærk, at Microsoft er holdt op med at producere spamdefinitionsopdateringer til SmartScreen-filtrene Exchange og Outlook i november 2016. De eksisterende SmartScreen-spamdefinitioner bevares, men deres effektivitet vil sandsynligvis forringes med tiden.

  - Kontrollér, **at indstillingen Outlook "Kun Pengeskab-lister"** er deaktiveret: Når denne indstilling er aktiveret, er det kun meddelelser fra afsendere på listen Pengeskab-afsendere eller Pengeskab-modtagerlisten, der sendes til indbakken. Mail fra alle andre flyttes automatisk til mappen Uønsket mail.

  Du kan finde flere oplysninger om disse indstillinger [under Konfigurere indstillinger for uønsket mail Exchange Online postkasser i Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Brug de tilgængelige lister over afsendere, der er tillid til**: Du kan få mere at vide [under Opret lister over afsendere, der er tillid til](create-safe-sender-lists-in-office-365.md).

- **Bekræft, at brugerne er inden for begrænsningerne for** afsendelse og [](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#receiving-and-sending-limits) modtagelse som beskrevet i Begrænsninger for modtagelse og afsendelse Exchange Online servicebeskrivelsen.

- **Enkeltstående EOP:** Brug katalogsynkronisering: Hvis du bruger enkeltstående EOP til at beskytte din lokale Exchange-organisation, skal du synkronisere brugerindstillinger med tjenesten ved hjælp af katalogsynkronisering. Dette sikrer, at dine brugeres Pengeskab lister over afsendere overholdes af EOP. Få mere at vide under [Brug katalogsynkronisering til at administrere mailbrugere](/exchange/standalone-eop/manage-mail-users-in-eop#synchronize-directories-with-azure-active-directory-connect-aad-connect).

## <a name="anti-spam-legislation"></a>Antispamlovgivning

Hos Microsoft mener vi, at udviklingen af nye teknologier og selvlovgivning kræver understøttelse af effektive offentlige politikker og juridiske rammer. Den verdensomspændende spam-spredning har fået en lang række kommercielle organisationer til at regulere kommerciel mail. Mange lande har nu love om spam mod spam. USA har både føderale og statslige love vedrørende spam, og denne komplementære tilgang hjælper med at begrænse spam, samtidig med at det giver mulighed for lovlig e-handel til handel. CAN-SPAM Act udvider de værktøjer, der er tilgængelige til at dæmme op for bedrageriske og vildledende mails.
