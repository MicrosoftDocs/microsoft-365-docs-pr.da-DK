---
title: Brug DMARC til at validere trin til konfiguration af mail
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/10/2021
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 4a05898c-b8e4-4eab-bd70-ee912e349737
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Få mere at vide om, hvordan du konfigurerer domænebaseret meddelelsesgodkendelse, -rapportering og -overensstemmelse (DMARC) for at validere meddelelser, der er sendt fra din organisation.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 99c688587e7e09e2726457256f14403e2db73d1e
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772056"
---
# <a name="use-dmarc-to-validate-email"></a>Brug DMARC til at validere mail

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Domænebaseret meddelelsesgodkendelse, -rapportering og -overensstemmelse ([DMARC](https://dmarc.org)) fungerer sammen med SPF (Sender Policy Framework) og DomainKeys Identified Mail (DKIM) til godkendelse af mailafsendere.

DMARC sikrer, at destinationsmailsystemerne har tillid til meddelelser, der sendes fra dit domæne. Brug af DMARC med SPF og DKIM giver organisationer mere beskyttelse mod spoofing- og phishingmails. DMARC hjælper med at modtage mail systemer beslutte, hvad de skal gøre med meddelelser fra dit domæne, der mislykkes SPF eller DKIM kontrol.

> [!TIP]
> Besøg [Kataloget for Microsoft Intelligent Security Association (MISA)](https://www.microsoft.com/misapartnercatalog) for at få vist tredjepartsleverandører, der tilbyder DMARC-rapportering for Microsoft 365.

## <a name="how-do-spf-and-dmarc-work-together-to-protect-email-in-microsoft-365"></a>Hvordan arbejder SPF og DMARC sammen om at beskytte mails i Microsoft 365?

 En mail kan indeholde flere afsendere eller afsenderadresser. Disse adresser bruges til forskellige formål. Overvej f.eks. disse adresser:

- **"Mail fra"-adresse**: Identificerer afsenderen og siger, hvor der skal sendes returmeddelelser, hvis der opstår problemer med leveringen af meddelelsen (f.eks. meddelelser om manglende levering). *Mail Fra-adresse* vises i konvolutdelen af en mail og vises ikke af dit mailprogram og kaldes nogle gange *5321.MailFrom-adressen* eller adressen med den *omvendte sti*.

- **"Fra"-adresse**: Den adresse, der vises som Fra-adressen af dit postprogram. *Fra adresse* identificerer forfatteren af mailen. Dvs. postkassen for den person eller det system, der er ansvarlig for at skrive meddelelsen. *Fra-adressen* kaldes også *5322.From-adressen*.

SPF bruger en DNS TXT-post til at vise godkendte afsendelses-IP-adresser for et bestemt domæne. Normalt udføres SPF-kontroller kun mod 5321.MailFrom-adressen. Adressen 5322.From godkendes ikke, når du selv bruger SPF, hvilket giver mulighed for et scenarie, hvor en bruger får en meddelelse, der har sendt SPF-kontroller, men har en spoofed 5322.From-afsenderadresse. Overvej f.eks. denne SMTP-transskription:

```console
S: Helo woodgrovebank.com
S: Mail from: phish@phishing.contoso.com
S: Rcpt to: astobes@tailspintoys.com
S: data
S: To: "Andrew Stobes" <astobes@tailspintoys.com>
S: From: "Woodgrove Bank Security" <security@woodgrovebank.com>
S: Subject: Woodgrove Bank - Action required
S:
S: Greetings User,
S:
S: We need to verify your banking details.
S: Please click the following link to verify that Microsoft has the right information for your account.
S:
S: https://short.url/woodgrovebank/updateaccount/12-121.aspx
S:
S: Thank you,
S: Woodgrove Bank
S: .
```

I denne transskription er afsenderadresserne som følger:

- Post fra adresse (5321.MailFrom): phish@phishing.contoso.com

- Fra adresse (5322.From): security@woodgrovebank.com

Hvis du har konfigureret SPF, foretager modtagerserveren en kontrol af mailen fra phish@phishing.contoso.com. Hvis meddelelsen kom fra en gyldig kilde for domænet phishing.contoso.com, overføres SPF-kontrollen. Da mailklienten kun viser fra-adressen, får brugeren vist denne meddelelse fra security@woodgrovebank.com. Med SPF alene blev gyldigheden af woodgrovebank.com aldrig godkendt.

Når du bruger DMARC, udfører modtagerserveren også en kontrol i forhold til fra-adressen. Hvis der er en DMARC TXT-post på plads til woodgrovebank.com i eksemplet ovenfor, mislykkes kontrollen i forhold til Fra-adressen.

## <a name="what-is-a-dmarc-txt-record"></a>Hvad er en DMARC TXT-post?

Ligesom DNS-posterne for SPF er posten for DMARC en DNS-tekstpost (TXT), der hjælper med at forhindre spoofing og phishing. Du publicerer DMARC TXT-poster i DNS. DMARC TXT-poster validerer oprindelsen af mails ved at bekræfte IP-adressen for en e-mail-forfatter i forhold til den påståede ejer af det afsendende domæne. DMARC TXT-posten identificerer godkendte udgående mailservere. Destinationsmailsystemer kan derefter bekræfte, at de meddelelser, de modtager, stammer fra godkendte udgående mailservere.

Microsofts DMARC TXT-post ser nogenlunde sådan ud:

```console
_dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.contoso.com; ruf=mailto:d@ruf.contoso.com; fo=1"
```

Hvis du vil have flere tredjepartsleverandører, der tilbyder DMARC-rapportering for Microsoft 365, skal du gå til [MISA-kataloget](https://www.microsoft.com/misapartnercatalog?IntegratedProducts=DMARCReportingforOffice365).

## <a name="set-up-dmarc-for-inbound-mail"></a>Konfigurer DMARC til indgående post

Du behøver ikke at gøre en ting for at konfigurere DMARC for mails, som du modtager i Microsoft 365. Det hele bliver ordnet. Hvis du vil vide mere om, hvad der sker med mails, der ikke kan bestå vores DMARC-kontroller, skal du se [Sådan håndterer Microsoft 365 indgående mail, der mislykkes DMARC](#how-microsoft-365-handles-inbound-email-that-fails-dmarc).

## <a name="set-up-dmarc-for-outbound-mail-from-microsoft-365"></a>Konfigurer DMARC til udgående post fra Microsoft 365

Hvis du bruger Microsoft 365, men du ikke bruger et brugerdefineret domæne (du bruger onmicrosoft.com), behøver du ikke at foretage dig andet. SPF er allerede konfigureret til dig, og Microsoft 365 genererer automatisk en DKIM-signatur for din udgående post. Der er ikke mere at gøre for at konfigurere DMARC for din organisation. Du kan få flere oplysninger om denne signatur under [Standardfunktionsmåde for DKIM og Microsoft 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

 Hvis du har et brugerdefineret domæne eller bruger lokale Exchange servere sammen med Microsoft 365, skal du konfigurere DMARC manuelt til udgående mails. Konfiguration af DMARC for dit brugerdefinerede domæne omfatter følgende trin:

- [Trin 1: Identificer gyldige mailkilder for dit domæne](#step-1-identify-valid-sources-of-mail-for-your-domain)

- [Trin 2: Konfigurer SPF for dit domæne](#step-2-set-up-spf-for-your-domain)

- [Trin 3: Konfigurer DKIM til dit brugerdefinerede domæne](#step-3-set-up-dkim-for-your-custom-domain)

- [Trin 4: Form DMARC TXT-posten for dit domæne](#step-4-form-the-dmarc-txt-record-for-your-domain)

### <a name="step-1-identify-valid-sources-of-mail-for-your-domain"></a>Trin 1: Identificer gyldige mailkilder for dit domæne

Hvis du allerede har konfigureret SPF, har du allerede gennemgået denne øvelse. Der er nogle yderligere overvejelser i forbindelse med DMARC. Når du identificerer mailkilder for dit domæne, skal du besvare disse to spørgsmål:

- Hvilke IP-adresser sender meddelelser fra mit domæne?

- Vil 5321.MailFrom og 5322.From domæner matche for mails, der sendes fra tredjeparter på mine vegne?

### <a name="step-2-set-up-spf-for-your-domain"></a>Trin 2: Konfigurer SPF for dit domæne

Nu, hvor du har en liste over alle dine gyldige afsendere, kan du følge trinnene for at [konfigurere SPF for at forhindre spoofing](set-up-spf-in-office-365-to-help-prevent-spoofing.md).

Hvis contoso.com f.eks. sender mail fra Exchange Online, en lokal Exchange server, hvis IP-adresse er 192.168.0.1, og et webprogram, hvis IP-adresse er 192.168.100.100, vil SPF TXT-posten se sådan ud:

```console
contoso.com  IN  TXT  " v=spf1 ip4:192.168.0.1 ip4:192.168.100.100 include:spf.protection.outlook.com -all"
```

Som bedste praksis skal du sikre, at der tages hensyn til tredjeparts afsendere af SPF TXT-posten.

### <a name="step-3-set-up-dkim-for-your-custom-domain"></a>Trin 3: Konfigurer DKIM til dit brugerdefinerede domæne

Når du har konfigureret SPF, skal du konfigurere DKIM. I DKIM kan du føje en digital signatur til mails i meddelelsesoverskriften. Hvis du ikke konfigurerer DKIM og i stedet tillader, at Microsoft 365 bruger STANDARD-DKIM-konfigurationen for dit domæne, kan DMARC mislykkes. Denne fejl kan ske, fordi STANDARD-DKIM-konfigurationen bruger dit oprindelige *onmicrosoft.com* domæne som *adressen 5322.From*, ikke dit *brugerdefinerede* domæne. Dette skaber en uoverensstemmelse mellem *5321.MailFrom* og *5322.From-adresserne* i alle de mails, der er sendt fra dit domæne.

Hvis du har afsendere fra tredjepart, der sender mail på dine vegne, og den mail, de sender, har uoverensstemmelse mellem 5321.MailFrom og 5322.From-adresser, mislykkes DMARC for den pågældende mail. For at undgå dette skal du konfigurere DKIM til dit domæne specifikt med denne tredjeparts afsender. Dette gør det muligt for Microsoft 365 at godkende mail fra denne tredjepartstjeneste. Det giver dog også andre, for eksempel Yahoo, Gmail og Comcast, mulighed for at bekræfte e-mail sendt til dem af tredjeparten, som om det var e-mail sendt af dig. Dette er nyttigt, fordi det giver dine kunder mulighed for at opbygge tillid til dit domæne, uanset hvor deres postkasse er placeret, og samtidig markerer Microsoft 365 ikke en meddelelse som spam på grund af spoofing, fordi den består godkendelseskontroller for dit domæne.

Du kan finde oplysninger om, hvordan du konfigurerer DKIM til dit domæne, herunder hvordan du konfigurerer DKIM for afsendere fra tredjepart, så de kan forfalske dit domæne, i [Brug DKIM til at validere udgående mail sendt fra dit brugerdefinerede domæne](use-dkim-to-validate-outbound-email.md).

### <a name="step-4-form-the-dmarc-txt-record-for-your-domain"></a>Trin 4: Form DMARC TXT-posten for dit domæne

Selvom der er andre syntaksindstillinger, der ikke er nævnt her, er disse de mest anvendte indstillinger for Microsoft 365. Form DMARC TXT-posten for dit domæne i følgende format:

```console
_dmarc.domain  TTL  IN  TXT  "v=DMARC1; p=policy; pct=100"
```

Hvor:

- *domæne* er det domæne, du vil beskytte. Posten beskytter som standard mail fra domænet og alle underdomæner. Hvis du f.eks. angiver \_dmarc.contoso.com, beskytter DMARC mail fra domænet og alle underdomæner, f.eks. housewares.contoso.com eller plumbing.contoso.com.

- *TTL* skal altid svare til én time. Den enhed, der bruges til TTL, enten timer (1 time), minutter (60 minutter) eller sekunder (3600 sekunder), varierer afhængigt af registratoren for dit domæne.

- *pct=100* angiver, at denne regel skal bruges til 100 % af mailen.

- *politik* angiver, hvilken politik modtagerserveren skal følge, hvis DMARC mislykkes. Du kan angive politikken til ingen, sætte den i karantæne eller afvise.

Du kan få oplysninger om, hvilke muligheder du skal bruge, ved at blive fortrolig med begreberne i [Bedste fremgangsmåder til implementering af DMARC i Microsoft 365](#best-practices-for-implementing-dmarc-in-microsoft-365).

Eksempler:

- Politik angivet til ingen

    ```console
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=none"
    ```

- Politik indstillet til karantæne

    ```console
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=quarantine"
    ```

- Politik, der er indstillet til at blive afvist

    ```console
    _dmarc.contoso.com  3600 IN  TXT  "v=DMARC1; p=reject"
    ```

Når du har oprettet din post, skal du opdatere posten hos din domæneregistrator.

## <a name="dmarc-mail-public-preview-feature"></a>DMARC Mail (offentlig prøveversion)

> [!CAUTION]
> Mails sendes muligvis ikke dagligt, og selve rapporten kan blive ændret under den offentlige prøveversion. De samlede DMARC-rapportmails kan forventes fra forbrugerkontiene (f.eks. hotmail.com, outlook.com eller live.com konti).

I dette eksempel kan du se DMARC TXT-posten: `dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.agari.com; ruf=mailto:d@ruf.agari.com; fo=1"`, hvor *rua-adressen* , i dette tilfælde, behandles af tredjepartsvirksomheden Agari. Denne adresse bruges til at sende "samlet feedback" til analyse, og den bruges til at generere en rapport.

> [!TIP]
> Besøg [MISA-kataloget](https://www.microsoft.com/misapartnercatalog) for at få vist flere tredjepartsleverandører, der tilbyder DMARC-rapportering for Microsoft 365. Se [IETF.org's 'Domain-based Message Authentication, Reporting, and Conformance (DMARC)'](https://datatracker.ietf.org/doc/html/rfc7489) for at få flere oplysninger om DMARC 'rua'-adresser.

## <a name="best-practices-for-implementing-dmarc-in-microsoft-365"></a>Bedste praksis for implementering af DMARC i Microsoft 365

Du kan implementere DMARC gradvist uden at påvirke resten af dit mailflow. Opret og implementer en udrulningsplan, der følger disse trin. Gør hvert af disse trin først med et underdomæne, derefter andre underdomæner og til sidst med domænet på øverste niveau i din organisation, før du går videre til næste trin.

1. Overvåg virkningen af gennemførelsen af DMARC

    Start med en simpel overvågningstilstandspost for et underdomæne eller domæne, der anmoder om, at DMARC-modtagere sender dig statistikker om meddelelser, som de ser ved hjælp af det pågældende domæne. En overvågningstilstandspost er en DMARC TXT-post, hvor politikken er angivet til ingen (p=none). Mange virksomheder publicerer en DMARC TXT-post med p=none, fordi de er i tvivl om, hvor meget e-mail de kan miste ved at publicere en mere restriktiv DMARC-politik.

    Det kan du gøre, selv før du har implementeret SPF eller DKIM i din meddelelsesinfrastruktur. Du vil dog ikke være i stand til effektivt at sætte mails i karantæne eller afvise dem ved hjælp af DMARC, før du også implementerer SPF og DKIM. Når du introducerer SPF og DKIM, giver de rapporter, der genereres via DMARC, antallet og kilderne til meddelelser, der passerer disse kontroller, i forhold til dem, der ikke gør det. Du kan nemt se, hvor meget af din legitime trafik der er eller ikke er dækket af dem, og foretage fejlfinding af eventuelle problemer. Du begynder også at se, hvor mange falske meddelelser der sendes, og hvor de sendes fra.

2. Anmod om, at eksterne mailsystemer sætter mail i karantæne, der mislykkes DMARC

    Når du mener, at al eller størstedelen af din legitime trafik er beskyttet af SPF og DKIM, og du forstår effekten af at implementere DMARC, kan du implementere en karantænepolitik. En karantænepolitik er en DMARC TXT-post, hvor politikken er angivet til karantæne (p=karantæne). Ved at gøre dette beder du DMARC-modtagere om at placere meddelelser fra dit domæne, der mislykkes DMARC i den lokale ækvivalent af en spam-mappe i stedet for dine kunders indbakker.

3. Anmod om, at eksterne mailsystemer ikke accepterer meddelelser, der mislykkes DMARC

    Det sidste trin er implementering af en afvisningspolitik. En politik til afvisning er en DMARC TXT-post, hvor politikken er indstillet til at blive afvist (p=afvis). Når du gør dette, beder du DMARC-modtagere om ikke at acceptere meddelelser, der mislykkes DMARC-kontrollerne.

4. Hvordan konfigurerer du DMARC for underdomænet?

   DMARC implementeres ved at publicere en politik som en TXT-post i DNS og er hierarkisk (en politik, der f.eks. er publiceret til contoso.com gælder for sub.domain.contonos.com, medmindre en anden politik udtrykkeligt er defineret for underdomænet). Dette er nyttigt, da organisationer kan angive et mindre antal DMARC-poster på højt niveau for at få større dækning. Man skal være omhyggelig med at konfigurere eksplicitte DMARC-poster for underdomæner, hvor du ikke ønsker, at underdomænerne arver DMARC-posten på øverste niveau.

   Du kan også tilføje en politik af typen jokertegn for DMARC, når underdomæner ikke skal sende mail, ved at tilføje værdien `sp=reject` . Eksempel:

   ```text
   _dmarc.contoso.com. TXT "v=DMARC1; p=reject; sp=reject; ruf=mailto:authfail@contoso.com; rua=mailto:aggrep@contoso.com"
   ```

## <a name="how-microsoft-365-handles-outbound-email-that-fails-dmarc"></a>Sådan håndterer Microsoft 365 udgående mail, der ikke lykkes DMARC

Hvis en meddelelse er udgående fra Microsoft 365 og mislykkes DMARC, og du har angivet politikken til p=karantæne eller p=afvis, dirigeres meddelelsen gennem [gruppen for højrisikolevering for udgående meddelelser](high-risk-delivery-pool-for-outbound-messages.md). Der er ingen tilsidesættelse af udgående mail.

Hvis du publicerer en DMARC-afvisningspolitik (p=afvis), kan ingen andre kunder i Microsoft 365 forfalske dit domæne, fordi meddelelser ikke kan overføre SPF eller DKIM til dit domæne, når en meddelelse sendes udgående via tjenesten. Men hvis du publicerer en DMARC-afvisningspolitik, men ikke har alle dine mails godkendt via Microsoft 365, kan nogle af dem være markeret som spam for indgående mail (som beskrevet ovenfor), eller den vil blive afvist, hvis du ikke publicerer SPF og forsøger at videresende den udgående via tjenesten. Dette sker f.eks., hvis du glemmer at inkludere nogle af IP-adresserne for servere og apps, der sender mail på vegne af dit domæne, når du opretter din DMARC TXT-post.

## <a name="how-microsoft-365-handles-inbound-email-that-fails-dmarc"></a>Sådan håndterer Microsoft 365 indgående mail, der mislykkes DMARC

Hvis DMARC-politikken for afsendelsesserveren er `p=reject`, markerer [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) meddelelsen som spoof i stedet for at afvise den. Med andre ord, for indgående mail, Microsoft 365 godbidder `p=reject` og `p=quarantine` på samme måde. Administratorer kan definere den handling, der skal udføres på meddelelser, der er klassificeret som spoof i [politikken til bekæmpelse af phishing](set-up-anti-phishing-policies.md).

Microsoft 365 er konfigureret på denne måde, fordi nogle legitime mails muligvis mislykkes i DMARC. En meddelelse kan f.eks. mislykkes DMARC, hvis den sendes til en adresseliste, der derefter videresender meddelelsen til alle listedeltagere. Hvis Microsoft 365 afviste disse meddelelser, kan folk miste legitime mails og ikke have nogen måde at hente dem på. I stedet vil disse meddelelser stadig mislykkes DMARC, men de vil blive markeret som spam og ikke afvist. Hvis det er nødvendigt, kan brugerne stadig få disse meddelelser i deres indbakke via disse metoder:

- Brugerne tilføjer afsendere, der er tillid til, individuelt ved hjælp af deres mailklient.

- Administratorer kan bruge indsigt i [spoof intelligence](learn-about-spoof-intelligence.md) eller [lejerens tilladelses-/blokliste](tenant-allow-block-list.md) til at tillade meddelelser fra den spoofede afsender.

- Administratorer opretter en regel for Exchange mailflow (også kendt som en transportregel) for alle brugere, der tillader meddelelser for disse bestemte afsendere.

Du kan få flere oplysninger under [Opret lister over sikre afsendere](create-safe-sender-lists-in-office-365.md).

## <a name="how-microsoft-365-utilizes-authenticated-received-chain-arc"></a>Sådan bruger Microsoft 365 godkendt modtaget kæde (ARC)

Alle hostede postkasser i Microsoft 365 får nu fordel af ARC med forbedret leveringsdygtighed af meddelelser og forbedret beskyttelse mod spoofing. ARC bevarer resultaterne af mailgodkendelsen fra alle deltagende mellemled eller hop, når en mail distribueres fra den oprindelige server til modtagerpostkassen. Før ARC kan ændringer udført af mellemled i maildistribution, f.eks. regler for videresendelse eller automatiske signaturer, medføre DMARC-fejl, når mailen nåede modtagerpostkassen. Med ARC gør den kryptografiske bevarelse af godkendelsesresultaterne det muligt for Microsoft 365 at bekræfte ægtheden af afsenderen af en mail.

Microsoft 365 bruger i øjeblikket ARC til at bekræfte godkendelsesresultater, når Microsoft er ARC Sealer, men planlægger at tilføje understøttelse af arc-sealere fra tredjepart i fremtiden.

## <a name="troubleshooting-your-dmarc-implementation"></a>Fejlfinding af din DMARC-implementering

Hvis du har konfigureret dit domænes MX-poster, hvor EOP ikke er den første post, gennemtvinges DMARC-fejl ikke for dit domæne.

Hvis du er kunde, og dit domænes primære MX-post ikke peger på EOP, får du ikke fordelene ved DMARC. DMARC fungerer f.eks. ikke, hvis du peger MX-posten på din lokale mailserver og derefter distribuerer mail til EOP ved hjælp af en connector. I dette scenarie er modtagerdomænet et af dine Accepted-Domains men EOP er ikke den primære MX. Antag f.eks., at contoso.com peger sin MX på sig selv og bruger EOP som en sekundær MX-post, ser MX-posten på contoso.com ud på følgende måde:

```console
contoso.com     3600   IN  MX  0  mail.contoso.com
contoso.com     3600   IN  MX  10 contoso-com.mail.protection.outlook.com
```

Alle eller de fleste mails distribueres først til mail.contoso.com da det er den primære MX, og derefter sendes mail til EOP. I nogle tilfælde kan du slet ikke angive EOP som en MX-post og blot koble connectors sammen for at distribuere din mail. EOP behøver ikke at være den første post for DMARC-validering, der skal udføres. Det sikrer blot valideringen for at være sikker på, at alle lokale/ikke-O365-servere udfører DMARC-kontroller.  DMARC er berettiget til at blive gennemtvunget for en kundes domæne (ikke server), når du konfigurerer DMARC TXT-posten, men det er op til den modtagende server at udføre håndhævelsen.  Hvis du konfigurerer EOP som modtagerserver, gennemtvinger EOP DMARC-håndhævelsen.

:::image type="content" source="../../media/Tp_DMARCTroublehoot.png" alt-text="En fejlfindingsgrafik til DMARC" lightbox="../../media/Tp_DMARCTroublehoot.png":::

## <a name="for-more-information"></a>Du kan få flere oplysninger

Vil du have flere oplysninger om DMARC? Disse ressourcer kan hjælpe.

- [Brevhoveder mod spam](anti-spam-message-headers.md) indeholder syntaks- og headerfelter, der bruges af Microsoft 365 til DMARC-kontroller.

- Tag [DMARC Training Series](https://www.m3aawg.org/activities/training/dmarc-training-series) fra M<sup>3</sup>AAWG (Messaging, Malware, Mobile Anti-Abuse Working Group).

- Brug tjeklisten på [dmarcian](https://space.dmarcian.com/deployment/).

- Gå direkte til kilden på [DMARC.org](https://dmarc.org).

## <a name="see-also"></a>Se også

[Sådan bruger Microsoft 365 SPF (Sender Policy Framework) til at forhindre spoofing](how-office-365-uses-spf-to-prevent-spoofing.md)

[**Konfigurer SPF i Microsoft 365 for at forhindre spoofing**](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

[**Brug DKIM til at validere udgående mails, der er sendt fra dit brugerdefinerede domæne i Microsoft 365**](use-dkim-to-validate-outbound-email.md)

[Brug ARC-afsendere, der er tillid til, til legitime mailflow](/microsoft-365/security/office-365-security/use-arc-exceptions-to-mark-trusted-arc-senders?view=o365-21vianet&branch=tracyp_emailauth)
