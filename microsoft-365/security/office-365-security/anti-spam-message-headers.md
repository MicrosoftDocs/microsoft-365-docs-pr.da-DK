---
title: Meddelelsesoverskrift for antispammeddelelser
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 2e3fcfc5-5604-4b88-ac0a-c5c45c03f1db
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Administratorer kan få mere at vide om de headerfelter, der føjes til meddelelser af Exchange Online Protection (EOP). Disse headerfelter indeholder oplysninger om meddelelsen, og hvordan den blev behandlet.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2d9c98446b7963581654c5920c30202f547ce271
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089017"
---
# <a name="anti-spam-message-headers-in-microsoft-365"></a>Brevhoveder mod spam i Microsoft 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I alle Microsoft 365 organisationer scanner Exchange Online Protection (EOP) alle indgående meddelelser for spam, malware og andre trusler. Resultaterne af disse scanninger føjes til følgende headerfelter i meddelelser:

- **X-Forefront-Antispam-Report**: Indeholder oplysninger om meddelelsen og om, hvordan den blev behandlet.

- **X-Microsoft-Antispam**: Indeholder flere oplysninger om massemails og phishing.

- **Godkendelsesresultater**: Indeholder oplysninger om resultater for SPF, DKIM og DMARC (mailgodkendelse).

I denne artikel beskrives det, hvad der er tilgængeligt i disse headerfelter.

Du kan få oplysninger om, hvordan du får vist en mailheader i forskellige mailklienter, under [Få vist brevhoveder på internettet i Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

> [!TIP]
> Du kan kopiere og indsætte indholdet af en meddelelsesoverskrift i værktøjet [Analyse af meddelelsesoverskrift](https://mha.azurewebsites.net/) . Dette værktøj hjælper med at fortolke overskrifter og sætte dem i et mere læsevenligt format.

## <a name="x-forefront-antispam-report-message-header-fields"></a>Headerfelter for X-Forefront-Antispam-Report

Når du har oplysninger om brevhovederne, skal du finde **X-Forefront-Antispam-Report-headeren** . Der vil være flere felt- og værdipar i denne header adskilt af semikolon (;). Eksempel:

`...CTRY:;LANG:hr;SCL:1;SRV:;IPV:NLI;SFV:NSPM;PTR:;CAT:NONE;SFTY:;...`

De enkelte felter og værdier er beskrevet i følgende tabel.

> [!NOTE]
> **X-Forefront-Antispam-Report-headeren** indeholder mange forskellige felter og værdier. Felter, der ikke er beskrevet i tabellen, bruges udelukkende af Microsofts anti-spam-team til diagnosticeringsformål.

|Feltet|Beskrivelse|
|---|---|
|`ARC`|Protokollen `ARC` indeholder følgende felter: <ul><li>`AAR`: Registrerer indholdet af headeren **med godkendelsesresultater** fra DMARC.</li><li>`AMS`: Indeholder kryptografiske signaturer i meddelelsen.</li><li>`AS`: Indeholder kryptografiske signaturer i brevhovederne. Dette felt indeholder en kode for en kædevalidering, der kaldes `"cv="`, og som indeholder resultatet af kædevalideringen som **ingen**, **bestået** eller **mislykket**.</li></ul>|
|`CAT:`|Kategorien beskyttelsespolitik, der anvendes på meddelelsen: <ul><li>`BULK`, masse</li><li>`DIMP`, repræsentation af domæne</li><li>`GIMP`: [Repræsentation baseret på postkasseintelligens](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>`HPHSH` eller `HPHISH` : Phishing med høj genkendelsessikkerhed</li><li>`HSPM`: Spam med høj genkendelsessikkerhed</li><li>`MALW`: Malware</li><li>`PHSH`, phishing</li><li>`SPM`, spam</li><li>`SPOOF`, spoofing</li><li>`UIMP`, bruger repræsentering</li><li>`AMP`: Antimalware</li><li>`SAP`: Pengeskab vedhæftede filer</li><li>`OSPM`, Udgående spam</li></ul> <p> En indgående meddelelse kan være markeret af flere former for beskyttelse og scanninger med flere registreringer. Politikker har forskellige prioriteter, og politikken med den højeste prioritet anvendes først. Du kan få flere oplysninger under [Hvilken politik gælder, når flere beskyttelsesmetoder og registreringsscanninger kører på din mail](how-policies-and-protections-are-combined.md).|
|`CIP:[IP address]`|Den ip-adresse, der opretter forbindelse. Du kan bruge denne IP-adresse på listen over tilladte IP-adresser eller listen over IP-blokeringer. Du kan få flere oplysninger under [Konfigurer forbindelsesfiltrering](configure-the-connection-filter-policy.md).|
|`CTRY`|Kildelandet i forhold til den forbindelses-IP-adresse, som muligvis ikke er det samme som den oprindelige afsender-IP-adresse.|
|`H:[helostring]`|HELO- eller EHLO-strengen på forbindelsesmailserveren.|
|`IPV:CAL`|Meddelelsen sprang over filtrering af spam, fordi kildens IP-adresse var på listen over tilladte IP-adresser. Du kan få flere oplysninger under [Konfigurer forbindelsesfiltrering](configure-the-connection-filter-policy.md).|
|`IPV:NLI`|IP-adressen blev ikke fundet på nogen liste over IP-omdømme.|
|`LANG`|Det sprog, som meddelelsen blev skrevet på, som angivet i landekoden (f.eks. ru_RU for russisk).|
|`PTR:[ReverseDNS]`|PTR-posten (også kendt som det omvendte DNS-opslag) for kildens IP-adresse.|
|`SCL`|Niveauet for spamsikkerhed (SCL) for meddelelsen. En højere værdi angiver, at der er større sandsynlighed for, at meddelelsen er spam. Du kan få mere at vide under [Niveau for spamsikkerhed (SCL)](spam-confidence-levels.md).|
|`SFTY`|Meddelelsen blev identificeret som phishing og vil også blive markeret med en af følgende værdier: <ul><li>9.19: Repræsentation af domæne. Det afsendende domæne forsøger at [repræsentere et beskyttet domæne](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Sikkerhedstip til repræsentation af domænet føjes til meddelelsen (hvis den er aktiveret).</li><li>9.20: Bruger repræsentation. Den bruger, der sender, forsøger at repræsentere en bruger i modtagerens organisation eller [en beskyttet bruger, der er angivet i en politik til bekæmpelse af phishing](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) i Microsoft Defender for Office 365. Sikkerhedstip til brugerpræsentation føjes til meddelelsen (hvis den er aktiveret).</li><li>9.25: Første kontakt sikkerhedstip. Denne værdi _kan_ være en indikation af en mistænkelig eller phishing-meddelelse. Du kan få flere oplysninger under [Første kontakt sikkerhedstip](set-up-anti-phishing-policies.md#first-contact-safety-tip).</li></ul>|
|`SFV:BLK`|Filtrering blev sprunget over, og meddelelsen blev blokeret, fordi den blev sendt fra en adresse på en brugers liste over blokerede afsendere. <p> Du kan få flere oplysninger om, hvordan administratorer kan administrere en brugers liste over afsendere af uønsket mail, under [Konfigurer indstillinger for uønsket mail på Exchange Online postkasser](configure-junk-email-settings-on-exo-mailboxes.md).|
|`SFV:NSPM`|Filtrering af spam markerede meddelelsen som ikke-spam, og meddelelsen blev sendt til de ønskede modtagere.|
|`SFV:SFE`|Filtrering blev sprunget over, og meddelelsen blev tilladt, fordi den blev sendt fra en adresse på en brugers liste over Pengeskab afsendere. <p> Du kan få flere oplysninger om, hvordan administratorer kan administrere en brugers liste over afsendere af Pengeskab, under [Konfigurer indstillinger for uønsket mail på Exchange Online postkasser](configure-junk-email-settings-on-exo-mailboxes.md).|
|`SFV:SKA`|Meddelelsen sprunget over filtrering af spam og blev leveret til indbakken, fordi afsenderen var på listen over tilladte afsendere eller listen over tilladte domæner i en politik til bekæmpelse af spam. Du kan få flere oplysninger under [Konfigurer politikker til bekæmpelse af spam](configure-your-spam-filter-policies.md).|
|`SFV:SKB`|Meddelelsen blev markeret som spam, fordi den svarede til en afsender på listen over blokerede afsendere eller listen over blokerede domæner i en politik mod spam. Du kan få flere oplysninger under [Konfigurer politikker til bekæmpelse af spam](configure-your-spam-filter-policies.md).|
|`SFV:SKI`|Ligesom med SFV:SKN sprang meddelelsen over filtrering af spam af en anden årsag (f.eks. en mail i organisationen i en lejer).|
|`SFV:SKN`|Meddelelsen blev markeret som ikke-spam, før den blev behandlet af spamfiltrering. Meddelelsen blev f.eks. markeret som SCL -1 eller **Omgå spamfiltrering** efter en regel for mailflow.|
|`SFV:SKQ`|Meddelelsen blev frigivet fra karantænen og blev sendt til de ønskede modtagere.|
|`SFV:SKS`|Meddelelsen blev markeret som spam, før den blev behandlet af spamfiltrering. Meddelelsen blev f.eks. markeret som SCL 5 til 9 af en regel for mailflow.|
|`SFV:SPM`|Meddelelsen blev markeret som spam ved filtrering af spam.|
|`SRV:BULK`|Meddelelsen blev identificeret som massemail ved filtrering af spam og grænseværdien for masseklageniveau (BCL). Når parameteren _MarkAsSpamBulkMail_ er `On` (den er aktiveret som standard), markeres en massemailmeddelelse som spam (SCL 6). Du kan få flere oplysninger under [Konfigurer politikker til bekæmpelse af spam](configure-your-spam-filter-policies.md).|
|`X-CustomSpam: [ASFOption]`|Meddelelsen matchede en indstilling for avanceret spamfilter (ASF). Hvis du vil se X-headerværdien for hver ASF-indstilling, skal du se [Indstillinger for avanceret spamfilter (ASF](advanced-spam-filtering-asf-options.md)).|

## <a name="x-microsoft-antispam-message-header-fields"></a>X-Microsoft-Antispam-meddelelsesheaderfelter

I følgende tabel beskrives nyttige felter i meddelelsesheaderen **X-Microsoft-Antispam** . Andre felter i denne header bruges udelukkende af Microsofts anti-spam-team til diagnosticeringsformål.

|Feltet|Beskrivelse|
|---|---|
|`BCL`|Meddelelsens bulkklageniveau (BCL). En højere BCL angiver, at der er større sandsynlighed for, at en massemailmeddelelse genererer klager (og er derfor mere tilbøjelige til at være spam). Du kan få flere oplysninger under [Samlet klageniveau (BCL).](bulk-complaint-level-values.md)|

## <a name="authentication-results-message-header"></a>Brevhoved med godkendelsesresultater

Resultaterne af e-mailgodkendelseskontroller for SPF, DKIM og DMARC registreres (stemples) i headeren med **godkendelsesresultater** i indgående meddelelser.

På følgende liste beskrives den tekst, der føjes til headeren **Godkendelsesresultater** for hver type kontrol af mailgodkendelse:

- SPF bruger følgende syntaks:

  ```text
  spf=<pass (IP address)|fail (IP address)|softfail (reason)|neutral|none|temperror|permerror> smtp.mailfrom=<domain>
  ```

  Eksempel:

  ```text
  spf=pass (sender IP is 192.168.0.1) smtp.mailfrom=contoso.com
  spf=fail (sender IP is 127.0.0.1) smtp.mailfrom=contoso.com
  ```

- DKIM bruger følgende syntaks:

  ```text
  dkim=<pass|fail (reason)|none> header.d=<domain>
  ```

  Eksempel:

  ```text
  dkim=pass (signature was verified) header.d=contoso.com
  dkim=fail (body hash did not verify) header.d=contoso.com
  ```

- DMARC bruger følgende syntaks:

  ```text
  dmarc=<pass|fail|bestguesspass|none> action=<permerror|temperror|oreject|pct.quarantine|pct.reject> header.from=<domain>
  ```

  Eksempel:

  ```text
  dmarc=pass action=none header.from=contoso.com
  dmarc=bestguesspass action=none header.from=contoso.com
  dmarc=fail action=none header.from=contoso.com
  dmarc=fail action=oreject header.from=contoso.com
  ```

### <a name="authentication-results-message-header-fields"></a>Brevhovedfelter for godkendelsesresultater

I følgende tabel beskrives felterne og de mulige værdier for hver mailgodkendelseskontrol.

|Feltet|Beskrivelse|
|---|---|
|`action`|Angiver den handling, der udføres af spamfilteret baseret på resultaterne af DMARC-kontrollen. Eksempel: <ul><li>**oreject** eller **o.reject**: Står for tilsidesættelse af afvisning. I dette tilfælde bruger Microsoft 365 denne handling, når den modtager en meddelelse, der mislykkes DMARC-kontrollen fra et domæne, hvis DMARC TXT-post har politikken p=reject. I stedet for at slette eller afvise meddelelsen, markerer Microsoft 365 meddelelsen som spam. Du kan få flere oplysninger om, hvorfor Microsoft 365 er konfigureret på denne måde, under [Sådan håndterer Microsoft 365 indgående mail, der ikke lykkes DMARC](use-dmarc-to-validate-email.md#how-microsoft-365-handles-inbound-email-that-fails-dmarc).</li><li>**pct.quarantine**: Angiver, at en procentdel, der er mindre end 100 % af meddelelser, der ikke passerer DMARC, leveres alligevel. Det betyder, at meddelelsen mislykkedes DMARC, og politikken blev indstillet til at sætte feltet pct i karantæne, men feltet pct blev ikke indstillet til 100 %, og systemet har tilfældigt besluttet ikke at anvende DMARC-handlingen i henhold til det angivne domænes politik.</li><li>**pct.reject**: Angiver, at en procentdel, der er mindre end 100 % af meddelelser, der ikke består DMARC, leveres alligevel. Det betyder, at meddelelsen mislykkedes DMARC, og politikken blev indstillet til at blive afvist, men feltet pct blev ikke indstillet til 100 %, og systemet har tilfældigt besluttet ikke at anvende DMARC-handlingen i henhold til det angivne domænes politik.</li><li>**permerror**: Der opstod en permanent fejl under DMARC-evalueringen, f.eks. støder på en forkert udformet DMARC TXT-post i DNS. Det er ikke sandsynligt, at forsøget på at sende denne meddelelse igen vil ende med et andet resultat. I stedet skal du muligvis kontakte domænets ejer for at løse problemet.</li><li>**temperror**: Der opstod en midlertidig fejl under DMARC-evalueringen. Du kan muligvis anmode afsenderen om at sende meddelelsen igen senere for at behandle mailen korrekt.</li></ul>|
|`compauth`|Resultat af sammensat godkendelse. Bruges af Microsoft 365 til at kombinere flere godkendelsestyper, f.eks. SPF, DKIM, DMARC eller andre dele af meddelelsen for at afgøre, om meddelelsen er godkendt eller ej. Bruger domænet From: som grundlag for evaluering.|
|`dkim`|Beskriver resultaterne af DKIM-kontrollen af meddelelsen. Mulige værdier omfatter: <ul><li>**pass**: Angiver DKIM-kontrollen for den overførte meddelelse.</li><li>**fail (årsag)**: Angiver DKIM-kontrollen for meddelelsen mislykkedes og hvorfor. Hvis meddelelsen f.eks. ikke blev signeret, eller signaturen ikke blev bekræftet.</li><li>**none**: Angiver, at meddelelsen ikke er signeret. Dette indikerer måske eller måske ikke, at domænet har en DKIM-post, eller at DKIM-posten ikke evalueres til et resultat, men kun at denne meddelelse ikke er signeret.</li></ul>|
|`dmarc`|Beskriver resultaterne af DMARC-kontrollen af meddelelsen. Mulige værdier omfatter: <ul><li>**pass**: Angiver DMARC-kontrollen for den sendte meddelelse.</li><li>**fail**: Angiver, at DMARC-kontrollen for meddelelsen mislykkedes.</li><li>**bestguesspass**: Angiver, at der ikke findes nogen DMARC TXT-post for domænet, men hvis der havde eksisteret en, ville DMARC-kontrollen for meddelelsen være bestået.</li><li>**none**: Angiver, at der ikke findes nogen DMARC TXT-post for det afsendende domæne i DNS.|
|`header.d`|Domæne identificeret i DKIM-signaturen, hvis der er nogen. Dette er det domæne, der forespørges efter den offentlige nøgle.|
|`header.from`|Domænet for adressen `5322.From` i mailheaderen (også kendt som Fra-adressen eller P2-afsenderen). Modtageren får vist Fra-adressen i mailklienter.|
|`reason`|Årsagen til, at den sammensatte godkendelse blev bestået eller mislykkedes. Værdien er en 3-cifret kode. Eksempel: <ul><li>**000**: Meddelelsen kunne ikke godkende eksplicit (`compauth=fail`). Meddelelsen modtog f.eks. en DMARC-fejl med en handling med karantæne eller afvisning.</li><li>**001**: Meddelelsen mislykkedes implicit godkendelse (`compauth=fail`). Det betyder, at det afsendende domæne ikke har publiceret e-mail-godkendelsesposter, eller hvis de gjorde, havde de en svagere fejlpolitik (SPF soft fail eller neutral, DMARC-politik for `p=none`).</li><li>**002**: Organisationen har en politik for afsenderen/domæneparret, der udtrykkeligt er forbudt at sende forfalsket mail. Denne indstilling angives manuelt af en administrator.</li><li>**010**: Meddelelsen mislykkedes DMARC med en handling med afvisning eller karantæne, og det afsendende domæne er et af organisationens accepterede domæner (dette er en del af selv-til-selv eller intra-org, spoofing).</li><li>**1xx** eller **7xx**: Den sendte godkendelse (`compauth=pass`). De sidste to cifre er interne koder, der bruges af Microsoft 365.</li><li>**2xx**: Meddelelsens bløde overførte implicitte godkendelse (`compauth=softpass`). De sidste to cifre er interne koder, der bruges af Microsoft 365.</li><li>**3xx**: Meddelelsen blev ikke kontrolleret for sammensat godkendelse (`compauth=none`).</li><li>**4xx** eller **9xx**: Meddelelsen ignorerede den sammensatte godkendelse (`compauth=none`). De sidste to cifre er interne koder, der bruges af Microsoft 365.</li><li>**6xx**: Meddelelsen mislykkedes implicit mailgodkendelse, og det afsendende domæne er et af organisationens accepterede domæner (dette er en del af selv-til-selv- eller intra-org-spoofing).</li></ul>|
|`smtp.mailfrom`|Domænet for `5321.MailFrom` adressen (også kendt som MAIL FROM-adresse, P1-afsender eller konvolut afsender). Dette er den mailadresse, der bruges til rapporter om manglende levering (også kendt som NDRs eller bounce-meddelelser).|
|`spf`|Beskriver resultaterne af SPF-kontrollen af meddelelsen. Mulige værdier omfatter: <ul><li>`pass (IP address)`: SPF-kontrollen for den sendte meddelelse indeholder afsenderens IP-adresse. Klienten er godkendt til at sende eller videresende mail på vegne af afsenderens domæne.</li><li>`fail (IP address)`: SPF-kontrollen for meddelelsen mislykkedes og indeholder afsenderens IP-adresse. Dette kaldes nogle gange _hard fail_.</li><li>`softfail (reason)`: Den SPF-post, der har angivet værten som ikke har tilladelse til at sende, men er i overgang.</li><li>`neutral`: SPF-posten angiver udtrykkeligt, at den ikke hævder, om IP-adressen er godkendt til at sende.</li><li>`none`: Domænet har ikke en SPF-post, eller SPF-posten evalueres ikke til et resultat.</li><li>`temperror`: Der opstod en midlertidig fejl. Det kan f.eks. være en DNS-fejl. Den samme kontrol kan blive fuldført senere.</li><li>`permerror`: Der opstod en permanent fejl. Domænet har f.eks. en forkert formateret SPF-post.</li></ul>|
