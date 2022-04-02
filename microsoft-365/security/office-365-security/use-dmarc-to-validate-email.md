---
title: Brug DMARC til at validere mail, konfigurationstrin
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
description: Få mere at vide om, hvordan du konfigurerer domænebaseret meddelelsesgodkendelse, -rapportering og -overholdelse (DMARC) til at validere meddelelser, der sendes fra din organisation.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: cae3f007cc046bfc2afd6bb7322c65fe047816d5
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465877"
---
# <a name="use-dmarc-to-validate-email"></a>Brug DMARC til at validere mail

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Domain-based Message Authentication, Reporting, and Conformance ([DMARC](https://dmarc.org)) works with Sender Policy Framework (SPF) and DomainKeys Identified Mail (DKIM) to authenticate mail senders and ensure that destination email systems trust messages sent from your domain. Implementering af DMARC med SPF og DKIM giver yderligere beskyttelse mod spoofing- og phishing-mail. DMARC hjælper modtagende mailsystemer med at afgøre, hvad der skal sker med meddelelser, der sendes fra dit domæne, og som ikke kontrollerer SPF eller DKIM.

> [!TIP]
> Besøg [Kataloget Microsoft Intelligent Security Association (MISA)](https://www.microsoft.com/misapartnercatalog) for at få vist tredjepartsleverandører, der tilbyder DMARC-rapportering for Microsoft 365.

## <a name="how-do-spf-and-dmarc-work-together-to-protect-email-in-microsoft-365"></a>Hvordan arbejder SPF og DMARC sammen for at beskytte mails i Microsoft 365?

 En mail kan indeholde flere afsender- eller afsenderadresser. Disse adresser bruges til forskellige formål. Overvej f.eks. disse adresser:

- **"Mail fra"**-adresse: Identificerer afsenderen og angiver, hvor der skal sendes en meddelelse om returnering, hvis der opstår problemer med leveringen af meddelelsen, f.eks. meddelelser om manglende levering. Dette vises i konvolutdelen af en mail og vises ikke af dit mailprogram. Dette kaldes nogle gange 5321.MailFrom-adressen eller den omvendte stiadresse.

- **"Fra"-adresse**: Den adresse, der vises som Fra-adressen af dit mailprogram. Denne adresse identificerer forfatteren af mailen. Det vil sige postkassen for den person eller det system, der er ansvarlig for at skrive meddelelsen. Dette kaldes sommetider for 5322.From-adressen.

SPF bruger en DNS TXT-post til at levere en liste over autoriserede afsendende IP-adresser for et givet domæne. Normalt udføres SPF-kontroller kun i forhold til 5321.MailFrom-adressen. Det betyder, at 5322.From-adressen ikke godkendes, når du bruger SPF alene. Dette giver mulighed for et scenarie, hvor en bruger kan modtage en meddelelse, som videregiver en SPF-kontrol, men har en efterlignet 5322.From-afsenderadresse. Overvej f.eks. denne SMTP-afskrift:

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

I denne afskrift er afsenderadresserne som følger:

- Mail fra adresse (5321.MailFrom): phish@phishing.contoso.com

- Fra adresse (5322.From): security@woodgrovebank.com

Hvis du har konfigureret SPF, udfører den modtagende server en kontrol af Mail fra phish@phishing.contoso.com. Hvis meddelelsen kommer fra en gyldig kilde for domænets phishing.contoso.com, bliver SPF-kontrol passeret. Da mailklienten kun viser Fra-adressen, kan brugeren se, at denne meddelelse kommer fra security@woodgrovebank.com. Kun med SPF blev woodgrovebank.com godkendt.

Når du bruger DMARC, udfører den modtagende server også en check mod Fra-adressen. Hvis der i eksemplet ovenfor er en DMARC TXT-post på plads for woodgrovebank.com så mislykkes afkrydsningsfeltet mod Fra-adressen.

## <a name="what-is-a-dmarc-txt-record"></a>Hvad er en DMARC TXT-post?

Ligesom DNS-posterne for SPF er posten for DMARC en DNS-tekstpost (TXT), der hjælper med at forhindre spoofing og phishing. Du publicerer DMARC TXT-poster i DNS. DMARC TXT-poster validerer oprindelsen af mails ved at bekræfte IP-adressen på en mails forfatter over for den eksisterende ejer af det afsendende domæne. DMARC TXT-posten identificerer autoriserede udgående mailservere. Destinationens mailsystemer kan derefter bekræfte, at meddelelser, de modtager, stammer fra autoriserede udgående mailservere.

Microsofts DMARC TXT-post ser sådan ud:

```console
_dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.contoso.com; ruf=mailto:d@ruf.contoso.com; fo=1"
```

For flere tredjepartsleverandører, der tilbyder DMARC-rapportering til Microsoft 365, skal du gå til [MISA-kataloget](https://www.microsoft.com/misapartnercatalog?IntegratedProducts=DMARCReportingforOffice365).

## <a name="set-up-dmarc-for-inbound-mail"></a>Konfigurer DMARC til indgående mail

Du behøver ikke at gøre noget for at konfigurere DMARC for mails, du modtager i Microsoft 365. Det hele bliver klaret. Hvis du vil vide, hvad der sker med mail, der ikke består vores DMARC-kontrol, skal du se Hvordan Microsoft 365 håndterer indgående mail, der ikke [lykkes DMARC](#how-microsoft-365-handles-inbound-email-that-fails-dmarc).

## <a name="set-up-dmarc-for-outbound-mail-from-microsoft-365"></a>Konfigurer DMARC for udgående mail fra Microsoft 365

Hvis du bruger Microsoft 365, men du ikke bruger et brugerdefineret domæne, det vil sige, at du bruger onmicrosoft.com, behøver du ikke at gøre andet for at konfigurere eller implementere DMARC for organisationen. SPF er allerede konfigureret for dig, og Microsoft 365 genererer automatisk en DKIM-signatur til din udgående mail. Du kan finde flere oplysninger om denne signatur [under Standardfunktionsmåde for DKIM og Microsoft 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

 Hvis du har et brugerdefineret domæne, eller hvis du bruger lokale Exchange-servere ud over Microsoft 365, skal du implementere DMARC manuelt til din udgående mail. Implementering af DMARC for dit brugerdefinerede domæne omfatter disse trin:

- [Trin 1: Identificer gyldige mailkilder for dit domæne](#step-1-identify-valid-sources-of-mail-for-your-domain)

- [Trin 2: Konfigurer SPF for dit domæne](#step-2-set-up-spf-for-your-domain)

- [Trin 3: Konfigurer DKIM for dit brugerdefinerede domæne](#step-3-set-up-dkim-for-your-custom-domain)

- [Trin 4: Form DMARC TXT-posten for dit domæne](#step-4-form-the-dmarc-txt-record-for-your-domain)

### <a name="step-1-identify-valid-sources-of-mail-for-your-domain"></a>Trin 1: Identificer gyldige mailkilder for dit domæne

Hvis du allerede har konfigureret SPF, har du allerede gennemgået denne øvelse. Men for DMARC er der yderligere overvejelser. Når du identificerer mailkilder for dit domæne, er der to spørgsmål, du skal besvare:

- Hvilke IP-adresser sender meddelelser fra mit domæne?

- For mails, der sendes fra tredjeparter på mine vegne, vil 5321.MailFrom og 5322.From-domænerne svare til hinanden?

### <a name="step-2-set-up-spf-for-your-domain"></a>Trin 2: Konfigurer SPF for dit domæne

Nu hvor du har en liste over alle dine gyldige afsendere, kan du følge trinnene for at Konfigurere SPF for at forhindre [spoofing](set-up-spf-in-office-365-to-help-prevent-spoofing.md).

Hvis contoso.com f.eks. sender mails fra Exchange Online, en lokal Exchange-server, hvis IP-adresse er 192.168.0.1, og et webprogram, hvis IP-adresse er 192.168.100.100, vil SPF TXT-posten se sådan ud:

```console
contoso.com  IN  TXT  " v=spf1 ip4:192.168.0.1 ip4:192.168.100.100 include:spf.protection.outlook.com -all"
```

Som bedste fremgangsmåde skal du sikre dig, at din SPF TXT-post tager hensyn til tredjepartsafsendere.

### <a name="step-3-set-up-dkim-for-your-custom-domain"></a>Trin 3: Konfigurer DKIM for dit brugerdefinerede domæne

Når du har konfigureret SPF, skal du konfigurere DKIM. DKIM gør det muligt at tilføje en digital signatur til mails i brevhovedet. Hvis du ikke konfigurerer DKIM og i stedet tillader, Microsoft 365 bruge STANDARD DKIM-konfigurationen for dit domæne, kan DMARC mislykkes. Dette skyldes, at standard DKIM-konfigurationen bruger dit indledende onmicrosoft.com-domæne som 5322.From-adressen, ikke dit brugerdefinerede domæne. Dette gennemtvinger en uoverensstemmelse mellem adresserne 5321.MailFrom og 5322.From i alle mails, der sendes fra dit domæne.

Hvis du har tredjepartsafsendere, der sender mail på dine vegne, og de mails, de sender, ikke stemmer overens med 5321.MailFrom og 5322.From-adresser, vil DMARC mislykkes for den pågældende mail. For at undgå dette skal du konfigurere DKIM for dit domæne specifikt med den pågældende tredjepartsafsender. Dette gør Microsoft 365 at godkende mail fra denne tredjepartstjeneste. Men det giver også andre, f.eks. Yahoo, Gmail og Comcast, mulighed for at bekræfte mails, der er sendt til dem af tredjeparten, som om det var mails sendt af dig. Dette er nyttigt, fordi det giver dine kunder mulighed for at opbygge tillid til dit domæne, uanset hvor deres postkasse er placeret, og på samme tid markerer Microsoft 365 ikke en meddelelse som spam på grund af spoofing, fordi den videregiver godkendelseskontroller for dit domæne.

Du kan finde en vejledning til konfiguration af DKIM for dit domæne, herunder hvordan du konfigurerer DKIM for tredjepartsafsendere, så de kan efterligne dit domæne, under Brug [DKIM](use-dkim-to-validate-outbound-email.md) til at validere udgående mails, der sendes fra dit brugerdefinerede domæne.

### <a name="step-4-form-the-dmarc-txt-record-for-your-domain"></a>Trin 4: Form DMARC TXT-posten for dit domæne

Selvom der er andre syntaksindstillinger, der ikke er nævnt her, er disse de mest almindeligt anvendte indstillinger for Microsoft 365. Form DMARC TXT-posten for dit domæne i formatet:

```console
_dmarc.domain  TTL  IN  TXT  "v=DMARC1; p=policy; pct=100"
```

Hvor:

- *er* det domæne, du vil beskytte. Posten beskytter som standard mails fra domænet og alle underdomæner. Hvis du f.eks \_. angiver dmarc.contoso.com, beskytter DMARC mails fra domænet og alle underdomæner, f.eks. housewares.contoso.com eller plumbing.contoso.com.

- *TTL* bør altid være det samme som en time. Den enhed, der bruges til TTL, enten timer (1 time), minutter (60 minutter) eller sekunder (3600 sekunder), varierer afhængigt af registratoren for dit domæne.

- *pct=100* angiver, at denne regel skal bruges til 100 % af mail.

- *angiver* , hvilken politik den modtagende server skal følge, hvis DMARC mislykkes. Du kan indstille politikken til ingen, sætte den i karantæne eller afvise den.

Du kan finde oplysninger om, hvilke indstillinger du skal bruge, ved at blive fortrolig med begreberne i Bedste fremgangsmåder [for implementering af DMARC Microsoft 365](#best-practices-for-implementing-dmarc-in-microsoft-365).

Eksempler:

- Politik indstillet til ingen

    ```console
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=none"
    ```

- Politik indstillet til karantæne

    ```console
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=quarantine"
    ```

- Politik indstillet til at afvise

    ```console
    _dmarc.contoso.com  3600 IN  TXT  "v=DMARC1; p=reject"
    ```

Når du har oprettet din post, skal du opdatere posten hos din domæneregistrator.

## <a name="dmarc-mail-public-preview-feature"></a>DMARC-mail (offentlig forhåndsvisningsfunktion)

> [!CAUTION]
> Mails sendes muligvis ikke dagligt, og selve rapporten kan ændres under offentlig forhåndsvisning. Der kan forventes mails i DMARC-aggregeringsrapporten fra forbrugerkonti (f.eks. hotmail.com, outlook.com eller live.com konti).

I dette eksempel DMARC TXT-post: `dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.agari.com; ruf=mailto:d@ruf.agari.com; fo=1"`, kan du se *rua-adressen* , i dette tilfælde, behandlet af tredjepartsfirmaet Agari. Denne adresse bruges til at sende "samlet feedback" til analyse, og den bruges til at oprette en rapport.

> [!TIP]
> Besøg [MISA-kataloget](https://www.microsoft.com/misapartnercatalog) for at få vist flere tredjepartsleverandører, der tilbyder DMARC-rapportering Microsoft 365. Se [IETF.orgs 'Domain-based Message Authentication, Reporting, and Conformance (DMARC)',](https://datatracker.ietf.org/doc/html/rfc7489) hvis du vil have mere at vide om DMARC's 'rua'-adresser.


## <a name="best-practices-for-implementing-dmarc-in-microsoft-365"></a>Bedste fremgangsmåder for implementering af DMARC i Microsoft 365

Du kan implementere DMARC gradvist uden at påvirke resten af dit mailflow. Opret og implementer en udrulningsplan, der følger disse trin. Gør hvert af disse trin først med et underdomæne og derefter andre underdomæner og til sidst med domænet på øverste niveau i organisationen, før du går videre til næste trin.

1. Overvåg effekten af implementering af DMARC

    Start med en simpel overvågningstilstandspost for et underdomæne eller domæne, der anmoder om, at DMARC-modtagere sender dig statistik om meddelelser, som de ser, når de bruger det pågældende domæne. En overvågningspost er en DMARC TXT-post, der har sin politik indstillet til ingen (p=ingen). Mange virksomheder udgiver en DMARC TXT-post med p=ingen, fordi de er i tvivl om, hvor mange mails de kan miste ved at udgive en mere restriktiv DMARC-politik.

    Du kan gøre dette, selv før du har implementeret SPF eller DKIM i din meddelelsesinfrastruktur. Du kan dog ikke sætte mails i karantæne eller afvise mail effektivt ved hjælp af DMARC, før du også implementerer SPF og DKIM. Når du introducerer SPF og DKIM, leverer de rapporter, der genereres via DMARC, de tal og kilder til meddelelser, der består disse kontroller, og dem, der ikke består. Du kan nemt se, hvor meget af din legitime trafik, der er dækket eller ikke er dækket af dem, og foretage fejlfinding af eventuelle problemer. Du vil også begynde at se, hvor mange svigagtige meddelelser, der sendes, og hvor de sendes fra.

2. Anmod om, at eksterne mailsystemer sætter mail i karantæne, hvis DMARC ikke virker

    Når du mener, at al eller det meste af din legitime trafik er beskyttet af SPF og DKIM, og du forstår virkningen af implementering af DMARC, kan du implementere en karantænepolitik. En karantænepolitik er en DMARC TXT-post, der har sin politik indstillet til karantæne (p=karantæne). Ved at gøre dette beder du DMARC-modtagere om at placere meddelelser fra dit domæne, der ikke indeholder DMARC, i den lokale mappe med uønsket post i stedet for kundernes indbakker.

3. Anmod om, at eksterne mailsystemer ikke accepterer meddelelser, der ikke overholder DMARC

    Det sidste trin er at implementere en politik for afvisning. En afvisningspolitik er en DMARC TXT-post, der har indstillet sin politik til at afvise (p=afvis). Når du gør dette, beder du DMARC-modtagere om ikke at acceptere meddelelser, der ikke overholder DMARC-kontrollerne.

4. Sådan konfigureres DMARC til underdomæne?

   DMARC implementeres ved at publicere en politik som en TXT-post i DNS og er hierarkisk (f.eks. vil en publiceret politik for contoso.com gælde for sub.domain.contonos.com, medmindre en anden politik udtrykkeligt er defineret for underdomænet). Dette er nyttigt, da organisationer muligvis kan angive et mindre antal DMARC-poster på højt niveau for at få en bredere dækning. Der skal gøres noget ved at konfigurere eksplicitte underdomæne-DMARC-poster, hvor du ikke vil have underdomænerne til at nedarve domænets DMARC-post på øverste niveau.

   Du kan også tilføje en politik med jokertegn for DMARC, når underdomæner ikke skal sende mail, ved at tilføje `sp=reject` værdien. Eksempel:

   ```text
   _dmarc.contoso.com. TXT "v=DMARC1; p=reject; sp=reject; ruf=mailto:authfail@contoso.com; rua=mailto:aggrep@contoso.com"
   ```

## <a name="how-microsoft-365-handles-outbound-email-that-fails-dmarc"></a>Sådan Microsoft 365 du håndtere udgående mail, der ikke kan håndtere DMARC

Hvis en meddelelse er udgående fra Microsoft 365 og ikke lykkes med DMARC, og du har angivet politikken til p=karantæne eller p=afvis, dirigeres meddelelsen gennem puljen af levering med høj risiko [for udgående](high-risk-delivery-pool-for-outbound-messages.md) meddelelser. Der er ingen tilsidesættelse for udgående mail.

Hvis du publicerer en DMARC-afvisningspolitik (p=afvis), kan ingen andre kunder i Microsoft 365 efterligne dit domæne, fordi meddelelser ikke vil kunne videregive SPF eller DKIM for dit domæne, når en meddelelse videresendes udgående via tjenesten. Men hvis du publicerer en DMARC-afvisningspolitik, men ikke har alle dine mails godkendt via Microsoft 365, kan noget af den være markeret som spam for indgående mail (som beskrevet ovenfor), eller den vil blive afvist, hvis du ikke udgiver SPF og forsøger at videresende den udgående via tjenesten. Dette sker, hvis du f.eks. glemmer at medtage nogle af IP-adresserne til servere og apps, der sender mail på vegne af dit domæne, når du danner din DMARC TXT-post.

## <a name="how-microsoft-365-handles-inbound-email-that-fails-dmarc"></a>Hvordan Microsoft 365 håndterer indgående mail, der ikke lykkes med DMARC

Hvis DMARC-politikken `p=reject`for den server, der sender, [er , markerer Exchange Online Protection](exchange-online-protection-overview.md) (EOP) meddelelsen som spoof i stedet for at afvise den. Med andre ord: for indgående mail Microsoft 365 mails behandles `p=reject` på `p=quarantine` samme måde. Administratorer kan definere den handling, der skal sker på meddelelser, der er klassificeret som spoof inden [for antiphishing-politikken](set-up-anti-phishing-policies.md).

Microsoft 365 konfigureret sådan her, fordi nogle legitime mails måske ikke kan sende DMARC. En meddelelse kan f.eks. mislykkes DMARC, hvis den sendes til en adresseliste, som derefter videresender meddelelsen til alle listedeltagerne. Hvis Microsoft 365 disse meddelelser, kan folk miste legitime mails og ikke kunne hente dem. I stedet vil disse meddelelser stadig mislykkes DMARC, men de markeres som spam og afvises ikke. Hvis du ønsker det, kan brugerne stadig få disse meddelelser i deres indbakke via disse metoder:

- Brugere tilføjer afsendere, der er tillid til, enkeltvis ved hjælp af deres mailklient.

- Administratorer kan [bruge efterlignet](learn-about-spoof-intelligence.md) intelligensindsigt eller lejerens tilladelses [-/blokeringsliste](tenant-allow-block-list.md) til at tillade meddelelser fra den efterlignede afsender.

- Administratorer opretter en regel Exchange for mailflow (også kaldet en transportregel) for alle brugere, der tillader meddelelser for bestemte afsendere.

Få mere at vide under [Opret lister over afsendere, der er tillid til](create-safe-sender-lists-in-office-365.md).

## <a name="how-microsoft-365-utilizes-authenticated-received-chain-arc"></a>Hvordan Microsoft 365 anvender godkendt modtaget kæde (ARC)

Alle værtsbaserede postkasser i Microsoft 365 får nu fordelen af ARC med forbedret leverance af meddelelser og forbedret beskyttelse mod spoofing. ARC bevarer mailgodkendelsesresultaterne fra alle deltagende spring eller hop, når en mail dirigeres fra den oprindelige server til modtagerens postkasse. Før ARC kunne ændringer, der udføres af e-mail-routing, f.eks. regler for videresendelse eller automatiske signaturer, forårsage DMARC-fejl på det tidspunkt, hvor mailen nåede modtagerens postkasse. Med ARC giver den krypterede opbevaring af godkendelsesresultaterne Microsoft 365 at bekræfte ægtheden af en mails afsender.

Microsoft 365 i øjeblikket ARC til at bekræfte godkendelsesresultater, når Microsoft er ARC-sealeren, men planlægger at tilføje understøttelse af tredjeparts ARC-lukkere i fremtiden.

## <a name="troubleshooting-your-dmarc-implementation"></a>Fejlfinding i forbindelse med din DMARC-implementering

Hvis du har konfigureret domænets MX-poster, hvor EOP ikke er den første post, gennemtvinges DMARC-fejl ikke for dit domæne.

Hvis du er kunde, og dit domænes primære MX-post ikke peger på EOP, får du ikke fordelene ved DMARC. DMARC fungerer f.eks. ikke, hvis du peger MX-posten på din lokale mailserver og derefter omdirigerer mail til EOP ved hjælp af en forbindelse. I dette scenarie er det modtagende domæne et af dine Accepted-Domains men EOP er ikke det primære MX. Antag f.eks., at contoso.com peger på sin MX alene og bruger EOP som en sekundær MX-post, ser contoso.coms MX-post således ud:

```console
contoso.com     3600   IN  MX  0  mail.contoso.com
contoso.com     3600   IN  MX  10 contoso-com.mail.protection.outlook.com
```

Alle, eller de fleste, mails dirigeres først til mail.contoso.com, da det er den primære MX, og derefter sendes mail til EOP. I nogle tilfælde vil du muligvis slet ikke en gang vise EOP som en MX-post og blot tilslutte forbindelser for at dirigere dine mails. EOP behøver ikke at være den første post, for at DMARC-validering kan udføres. Det sikrer blot valideringen for at sikre, at alle lokale/ikke-O365-servere kontrollerer DMARC.  DMARC kan håndhæves på en kundes domæne (ikke en server), når du konfigurerer DMARC TXT-posten, men det er op til den modtagende server rent faktisk at gennemtvinge gennemtvingelsen.  Hvis du konfigurerer EOP som den modtagende server, så håndhæver EOP DMARC-håndhævelsen.

:::image type="content" source="../../media/Tp_DMARCTroublehoot.png" alt-text="Fejlfindingsgrafik til DMARC" lightbox="../../media/Tp_DMARCTroublehoot.png":::

## <a name="for-more-information"></a>Du kan finde flere oplysninger

Vil du have flere oplysninger om DMARC? Disse ressourcer kan hjælpe.

- [Antispam-brevhoveder indeholder de syntaks](anti-spam-message-headers.md)- og brevhovedfelter, der bruges Microsoft 365 til DMARC-kontroller.

- Tag [DMARC-kursusserien](https://www.m3aawg.org/activities/training/dmarc-training-series) fra <sup>M3AAWG</sup> (Messaging, Malware, Mobile Anti-Abuse Working Group).

- Brug tjeklisten [på dmarcian](https://space.dmarcian.com/deployment/).

- Gå direkte til [kilden DMARC.org.](https://dmarc.org)

## <a name="see-also"></a>Se også

[Sådan Microsoft 365 SPF (Sender Policy Framework) til at forhindre spoofing](how-office-365-uses-spf-to-prevent-spoofing.md)

[**Konfigurer SPF i en Microsoft 365 at forhindre spoofing**](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

[**Brug DKIM til at validere udgående mails, der sendes fra dit brugerdefinerede domæne Microsoft 365**](use-dkim-to-validate-outbound-email.md)
