---
title: Antispam-brevhoveder
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
description: Administratorer kan få mere at vide om de overskriftsfelter, der føjes til meddelelser af Exchange Online Protection (EOP). Disse brevhovedfelter indeholder oplysninger om meddelelsen, og hvordan den blev behandlet.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8eaf567e4cbceae66a5acd1fa1a45565f15a4804
ms.sourcegitcommit: e09ced3e3628bf2ccb84d205d9699483cbb4b3b0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/09/2021
ms.locfileid: "63587541"
---
# <a name="anti-spam-message-headers-in-microsoft-365"></a>Antispam-brevhoveder i Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I alle Microsoft 365 scanner Exchange Online Protection (EOP) alle indgående meddelelser for spam, malware og andre trusler. Resultaterne af disse scanninger føjes til følgende brevhovedfelter i meddelelser:

- **X-Forefront Antispam-Report**: Indeholder oplysninger om meddelelsen, og om hvordan den blev behandlet.

- **X-Microsoft-antispam**: Indeholder flere oplysninger om massemail og phishing.

- **Godkendelsesresultater**: Indeholder oplysninger om resultater af SPF, DKIM og DMARC (mailgodkendelse).

I denne artikel beskrives, hvad der er tilgængeligt i disse overskriftsfelter.

Hvis du vil have mere at vide om, hvordan du får vist et brevhoved i en mail på forskellige mailklienter, skal du se Få vist [internetmeddelelsesoverskrifter Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

> [!TIP]
> Du kan kopiere og indsætte indholdet af en brevhoved i værktøjet Analyse [af brevhoved](https://mha.azurewebsites.net/) . Dette værktøj hjælper med at fortolke sidehoveder og sætte dem i et mere læsbart format.

## <a name="x-forefront-antispam-report-message-header-fields"></a>Brevhovedfelter for X-Forefront Antispam Report

Når du har oplysningerne om brevhovedet, skal du finde **X-Forefront Antispam Report-overskriften** . Der vil være flere felt- og værdipar i dette sidehoved adskilt af semikolon (;). Eksempel:

`...CTRY:;LANG:hr;SCL:1;SRV:;IPV:NLI;SFV:NSPM;PTR:;CAT:NONE;SFTY:;...`

De enkelte felter og værdier er beskrevet i følgende tabel.

> [!NOTE]
> Overskriften **X-Forefront Antispam Report** indeholder mange forskellige felter og værdier. Felter, der ikke er beskrevet i tabellen, bruges kun af Microsofts antispamteam til diagnosticeringsformål.

****

|Felt|Beskrivelse|
|---|---|
|`ARC`|Protokollen `ARC` har følgende felter: <ul><li>`AAR`: Registrerer indholdet af overskriften **Godkendelsesresultater** fra DMARC.</li><li>`AMS`: Omfatter krypterede signaturer for meddelelsen.</li><li>`AS`: Omfatter krypterede signaturer for brevhovederne. Dette felt indeholder et mærke fra en kædevalidering `"cv="`, der kaldes , og som inkluderer resultatet af kædevalideringen som **ingen**, **bestå** eller **mislykkes**.</li></ul>|
|`CAT:`|Kategorien for beskyttelsespolitik anvendt på meddelelsen: <ul><li>`BULK`: Masse</li><li>`DIMP`: Domænepersonation</li><li>`GIMP`: [Postkasseintelligens baseret på repræsentation](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>`HPHSH` eller `HPHISH` : Phishing med høj tillid</li><li>`HSPM`: Spam med høj  fortrolighed</li><li>`MALW`: Malware</li><li>`PHSH`: Phishing</li><li>`SPM`: Spam</li><li>`SPOOF`: Spoofing</li><li>`UIMP`: Bruger impersonation</li><li>`AMP`: Antimalware</li><li>`SAP`: Pengeskab vedhæftede filer</li><li>`OSPM`: Udgående spam</li></ul> <p> En indgående meddelelse kan være markeret med flere former for beskyttelse og scanninger med flere registreringer. Politikker har forskellige prioriteter, og politikken med højeste prioritet anvendes først. Få mere at vide under [Hvilken politik gælder, når der køres flere beskyttelsesmetoder, og registrering af scanninger på din mail](how-policies-and-protections-are-combined.md).|
|`CIP:[IP address]`|Den forbindende IP-adresse. Du kan bruge denne IP-adresse på listen over tilladte IP-adresser eller listen over blokerede IP-adresser. Du kan finde flere oplysninger [under Konfigurere filtrering af forbindelse](configure-the-connection-filter-policy.md).|
|`CTRY`|Kildeland som fastlagt af den forbindende IP-adresse, som muligvis ikke er den samme som den oprindelige afsender-IP-adresse.|
|`H:[helostring]`|HELO- eller EHLO-strengen for den mailserver, der opretter forbindelse.|
|`IPV:CAL`|Meddelelsen ignorerede spamfiltrering, fordi kilde-IP-adressen var på listen over tilladte IP-adresser. Du kan finde flere oplysninger [under Konfigurere filtrering af forbindelse](configure-the-connection-filter-policy.md).|
|`IPV:NLI`|IP-adressen blev ikke fundet på nogen liste over IP-omdømmer.|
|`LANG`|Det sprog, som meddelelsen er skrevet på, som angivet i landekoden (f.eks. ru_RU for russisk).|
|`PTR:[ReverseDNS]`|PTR-posten (også kaldet det omvendte DNS-opslag) for kilde-IP-adressen.|
|`SCL`|Meddelelsens tillidsniveau til spam. En højere værdi angiver, at meddelelsen er mere tilbøjelig til at være spam. Du kan få mere at vide under [SCL (Spam confidence level).](spam-confidence-levels.md)|
|`SFTY`|Meddelelsen blev identificeret som phishing og markeres også med en af følgende værdier: <ul><li>9.19: Domænepersonation. Det afsendende domæne forsøger [at udgive sig for at være et beskyttet domæne](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Den sikkerhedstip for domænepersonation føjes til meddelelsen (hvis den er aktiveret).</li><li>9.20: Bruger efterligning. Den afsendende bruger forsøger at udgive sig for at være en bruger i modtagerens organisation eller en beskyttet bruger, der er angivet i en [antiphishingpolitik](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) i Microsoft Defender for Office 365. Beskeden sikkerhedstip brugerens repræsentation føjes til meddelelsen (hvis den er aktiveret).</li></ul>|
|`SFV:BLK`|Filtrering blev sprunget over, og meddelelsen blev blokeret, fordi den blev sendt fra en adresse på en brugers liste over blokerede afsendere. <p> Hvis du vil have mere at vide om, hvordan administratorer kan administrere en brugers liste over blokerede afsendere, skal du se Konfigurer indstillinger for uønsket mail [Exchange Online postkasser](configure-junk-email-settings-on-exo-mailboxes.md).|
|`SFV:NSPM`|Spamfiltrering markerede meddelelsen som ikke uønsket, og meddelelsen blev sendt til de tilsigtede modtagere.|
|`SFV:SFE`|Filtrering blev sprunget over, og meddelelsen blev tilladt, fordi den blev sendt fra en adresse på Pengeskab liste over afsendere. <p> Du kan finde flere oplysninger om, hvordan administratorer kan administrere en brugers liste Pengeskab afsendere, under Konfigurer indstillinger for uønsket mail [Exchange Online postkasser](configure-junk-email-settings-on-exo-mailboxes.md).|
|`SFV:SKA`|Meddelelsen ignorerede spamfiltrering og blev leveret til indbakken, fordi afsenderen var på listen over tilladte afsendere eller tilladte domæner i en politik for uønsket post. Få mere at vide under [Konfigurer antispam-politikker](configure-your-spam-filter-policies.md).|
|`SFV:SKB`|Meddelelsen blev markeret som spam, fordi den matchede en afsender på listen over blokerede afsendere eller listen over blokerede domæner i en antispampolitik. Få mere at vide under [Konfigurer antispam-politikker](configure-your-spam-filter-policies.md).|
|`SFV:SKI`|Ligesom SFV:SKN blev spamfiltrering sprunget over af en anden årsag (f.eks. en intra-organisatorisk mail inden for en lejer).|
|`SFV:SKN`|Meddelelsen blev markeret som ikke-spam, før den blev behandlet af spamfiltrering. Meddelelsen blev f.eks. markeret som SCL-1 eller **Tilslør spamfiltrering** ved hjælp af en regel for mailflow.|
|`SFV:SKQ`|Meddelelsen blev frigivet fra karantæne og blev sendt til de tilsigtede modtagere.|
|`SFV:SKS`|Meddelelsen blev markeret som spam, før den blev behandlet af spamfiltrering. Meddelelsen blev f.eks. markeret som SCL 5 til 9 af en regel for mailflow.|
|`SFV:SPM`|Meddelelsen blev markeret som spam af spamfiltrering.|
|`SRV:BULK`|Meddelelsen blev identificeret som massemail ved hjælp af spamfiltrering og grænseværdien for masseklager. Når _parameteret MarkAsSpamBulkMail_ `On` er (det er til som standard), markeres en massemail som spam (SCL 6). Få mere at vide under [Konfigurer antispam-politikker](configure-your-spam-filter-policies.md).|
|`X-CustomSpam: [ASFOption]`|Meddelelsen matchede en asf-indstilling (Advanced Spam Filter). Hvis du vil have vist X-overskriftsværdien for hver ASF-indstilling, skal du se Avancerede [indstillinger for spamfilter (ASF](advanced-spam-filtering-asf-options.md)).|
|

## <a name="x-microsoft-antispam-message-header-fields"></a>Brevhovedfelter i X-Microsoft-Antispam

I følgende tabel beskrives nyttige felter i brevhovedet **X-Microsoft-Antispam** . Andre felter i denne overskrift bruges udelukkende af Microsofts antispamteam til diagnosticeringsformål.

****

|Felt|Beskrivelse|
|---|---|
|`BCL`|Meddelelsens mange klageniveau (BCL). En højere BCL indikerer, at en massemailmeddelelse er mere tilbøjelig til at generere klager (og derfor er mere tilbøjelig til at være spam). Du kan finde flere oplysninger [under Masseklageniveau (BCL)](bulk-complaint-level-values.md).|
|

## <a name="authentication-results-message-header"></a>Meddelelsesoverskrift for godkendelsesresultater

Resultaterne af mailgodkendelse kontrollerer, om SPF, DKIM og DMARC er registreret (stemplet) i meddelelsens  brevhoved med godkendelsesresultater i indgående meddelelser.

Følgende liste beskriver den tekst, der føjes til overskriften **Godkendelsesresultater** for hver type mailgodkendelseskontrol:

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

****

|Felt|Beskrivelse|
|---|---|
|`action`|Angiver den handling, som spamfilteret har foretaget, baseret på resultaterne af DMARC-kontrol. Eksempel: <ul><li>**oreject** eller **o.reject**: Står for override reject. I dette tilfælde Microsoft 365 denne handling, når den modtager en meddelelse, der mislykkes for DMARC-kontrol fra et domæne, hvis DMARC TXT-post har en politik for p=afvis. I stedet for at slette eller afvise meddelelsen markerer Microsoft 365 meddelelsen som spam. Du kan finde flere oplysninger Microsoft 365, hvorfor din mailkonto er [konfigureret på denne måde, Microsoft 365 håndterer indgående mail, der ikke lykkes med DMARC](use-dmarc-to-validate-email.md#how-microsoft-365-handles-inbound-email-that-fails-dmarc).</li><li>**pct.karantæne**: Angiver, at en procentdel, der er mindre end 100 % af meddelelser, der ikke passerer DMARC, bliver leveret alligevel. Det betyder, at meddelelsen mislykkedes DMARC, og politikken blev indstillet til karantæne, men pct-feltet blev ikke angivet til 100 %, og systemet blev tilfældigt fastlagt til ikke at anvende DMARC-handlingen som angivet i det angivne domænes politik.</li><li>**pct.reject**: Angiver, at en procentdel, der er mindre end 100 % af meddelelser, der ikke passerer DMARC, vil blive leveret alligevel. Det betyder, at meddelelsen mislykkedes DMARC, og politikken blev indstillet til at afvise, men pct-feltet var ikke angivet til 100 %, og systemet blev tilfældigt besluttet ikke at anvende DMARC-handlingen som angivet i det angivne domænes politik.</li><li>**permerror**: Der opstod en permanent fejl under DMARC-evaluering, f.eks. hvis der opstod en forkert udformet DMARC TXT-post i DNS. Forsøg på at sende denne meddelelse igen vil sandsynligvis ikke slutte med et andet resultat. I stedet kan det være nødvendigt at kontakte domænets ejer for at løse problemet.</li><li>**temperror**: Der opstod en midlertidig fejl under DMARC-evaluering. Du kan muligvis anmode afsenderen om at sende meddelelsen igen senere for at behandle mailen korrekt.</li></ul>|
|`compauth`|Sammensat godkendelsesresultat. Bruges af Microsoft 365 til at kombinere flere typer godkendelse, f.eks. SPF, DKIM, DMARC eller andre dele af meddelelsen for at afgøre, om meddelelsen er godkendt. Bruger fra:-domænet som evalueringsbasis.|
|`dkim`|Beskriver resultaterne af DKIM-tjek for meddelelsen. Mulige værdier omfatter: <ul><li>**bestået**: Angiver DKIM-tjek for den overførte meddelelse.</li><li>**mislykkes (årsag)**: Angiver DKIM-tjek for meddelelsen mislykkedes og hvorfor. Hvis f.eks. meddelelsen ikke er signeret, eller signaturen ikke er blevet bekræftet.</li><li>**ingen**: Angiver, at meddelelsen ikke blev signeret. Dette kan eller muligvis ikke betyde, at domænet har en DKIM-post, eller DKIM-posten ikke evalueres til et resultat, kun at denne meddelelse ikke er signeret.</li></ul>|
|`dmarc`|Beskriver resultaterne af DMARC-tjek for meddelelsen. Mulige værdier omfatter: <ul><li>**bestået**: Angiver DMARC-tjek for den overførte meddelelse.</li><li>**mislykkes**: Angiver, at DMARC-tjek for meddelelsen mislykkedes.</li><li>**bestguesspass**: Angiver, at der ikke findes nogen DMARC TXT-post for domænet, men hvis der allerede findes en, så søger DMARC efter meddelelsen.</li><li>**ingen**: Angiver, at der ikke findes nogen DMARC TXT-post for det afsendende domæne i DNS.|
|`header.d`|Domæne identificeret i DKIM-signaturen, hvis dette er nogen. Dette er det domæne, der forespørges om den offentlige nøgle.|
|`header.from`|Domænet for adressen `5322.From` i brevhovedet (også kaldet Fra-adressen eller P2-afsenderen). Modtageren kan se Fra-adressen i mailklienter.|
|`reason`|Årsagen til, at den sammensatte godkendelse er gået eller mislykkedes. Værdien er en 3-cifret kode. Eksempel: <ul><li>**000**: Meddelelsen eksplicit godkendelse mislykkedes (`compauth=fail`). Meddelelsen modtog f.eks. en DMARC-fejl med en handling i karantæne eller afvis.</li><li>**001**: Meddelelsen mislykkedes implicit godkendelse (`compauth=fail`). Det betyder, at det afsendende domæne ikke har publicerede mailgodkendelsesposter, eller hvis de gjorde det, havde de en svag fejlpolitik (SPF soft fail eller neutral, DMARC-politik for `p=none`).</li><li>**002**: Organisationen har en politik for afsender-/domæneparret, der udtrykkeligt er forbudt at sende efterlignet mail. Denne indstilling angives manuelt af en administrator.</li><li>**010**: Meddelelsen mislykkedes DMARC med en afvisnings- eller karantænehandling, og afsenderdomænet er et af organisationens accepterede domæner (dette er en del af selv-til-egen eller intra-org, spoofing).</li><li>**1xx** eller **7xx**: Meddelelsen blev godkendt (`compauth=pass`). De sidste to cifre er interne koder, der bruges af Microsoft 365.</li><li>**2xx**: Meddelelsen blød-overført implicit godkendelse (`compauth=softpass`). De sidste to cifre er interne koder, der bruges af Microsoft 365.</li><li>**3xx**: Meddelelsen blev ikke kontrolleret for ikke-farvesepareret godkendelse (`compauth=none`).</li><li>**4xx** eller **9xx**: Meddelelsen er omgået sammensat godkendelse (`compauth=none`). De sidste to cifre er interne koder, der bruges af Microsoft 365.</li><li>**6xx**: Meddelelsen mislykkedes implicit mailgodkendelse, og afsendende domæne er et af organisationens accepterede domæner (dette er en del af selv-til-selv eller intra-org spoofing).</li></ul>|
|`smtp.mailfrom`|Domænet for adressen `5321.MailFrom` (også kaldet MAIL FROM-adresse, P1-afsender eller konvolutafsender). Dette er den mailadresse, der bruges til rapporter om manglende levering (også kaldet rapporter om manglende levering eller meddelelser om ikke-leveret post).|
|`spf`|Beskriver resultaterne af SPF-kontroller for meddelelsen. Mulige værdier omfatter: <ul><li>`pass (IP address)`: SPF søger efter den meddelelse, der er blevet sendt, og indeholder afsenderens IP-adresse. Klienten er autoriseret til at sende eller videresende mail på vegne af afsenderens domæne.</li><li>`fail (IP address)`: SPF-kontroller, om meddelelsen mislykkedes og indeholder afsenderens IP-adresse. Dette kaldes nogle gange for _"hard fail"_.</li><li>`softfail (reason)`: SPF-posten har udpeget værten som ikke må sende, men er i overgangsfasen.</li><li>`neutral`: SPF-posten angiver udtrykkeligt, at den ikke hævder, om IP-adressen er autoriseret til at sende.</li><li>`none`: Domænet har ikke en SPF-post, eller SPF-posten evalueres ikke til et resultat.</li><li>`temperror`: Der opstod en midlertidig fejl. Eksempelvis en DNS-fejl. Det samme tjek senere kan lykkes.</li><li>`permerror`: Der opstod en permanent fejl. Domænet har f.eks. en forudformateret SPF-post.</li></ul>|
|
