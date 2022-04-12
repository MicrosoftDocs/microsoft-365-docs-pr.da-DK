---
title: Sådan fungerer SMTP DNS-baseret godkendelse af navngivne enheder (DANE) til sikker mailkommunikation
f1.keywords:
- NOCSH
ms.author: v-mathavale
author: v-mathavale
manager: dansimp
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Få mere at vide om, hvordan SMTP DNS-baseret godkendelse af navngivne enheder (DANE) fungerer til at sikre mailkommunikation mellem mailservere.
ms.openlocfilehash: b5f9337457556dda53b5b2f982480a4c2501fcc9
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782847"
---
# <a name="how-smtp-dns-based-authentication-of-named-entities-dane-works"></a>Sådan fungerer SMTP DNS-baseret godkendelse af navngivne enheder (DANE)

SMTP-protokollen er den primære protokol, der bruges til at overføre meddelelser mellem mailservere og er som standard ikke sikker. TLS-protokollen (Transport Layer Security) blev introduceret for år siden for at understøtte krypteret overførsel af meddelelser via SMTP. Det bruges ofte opportunistisk snarere end som et krav, hvilket efterlader meget e-mail-trafik i klartekst, sårbar over for opfangelse af forbryderiske aktører. SMTP bestemmer desuden IP-adresserne på destinationsservere via den offentlige DNS-infrastruktur, som er udsat for spoofing- og MITM-angreb (Man-in-the-Middle). Dette har medført, at der er blevet oprettet mange nye standarder for at øge sikkerheden for afsendelse og modtagelse af mail, en af dem er DNS-baseret godkendelse af navngivne enheder (DANE).

DANE til SMTP [RFC 7672](https://tools.ietf.org/html/rfc7672) bruger tilstedeværelsen af en TLSA-post (Transport Layer Security Authentication) i et domænes DNS-post, der er angivet til at signalere et domæne, og dets mailserver(er) understøtter DANE. Hvis der ikke er nogen TLSA-post til stede, fungerer DNS-opløsningen for postflowet som normalt, uden at der forsøges at udføre DANE-kontroller. TLSA-posten signalerer sikkert TLS-understøttelse og publicerer DANE-politikken for domænet. Derfor kan afsendelse af mailservere godkende legitime modtagelsesservere ved hjælp af SMTP-DANE. Det gør det resistent over for nedgradering og MITM-angreb. DANE har direkte afhængigheder af DNSSEC, som fungerer ved digitalt at signere poster for DNS-opslag ved hjælp af kryptografi for offentlige nøgler. DNSSEC kontrollerer rekursive DNS-fortolkere, de DNS-servere, der foretager DNS-forespørgsler for klienter. DNSSEC sikrer, at der ikke pills ved DNS-poster, og at de er autentiske.

Når MX-, A/AAAA- og DNSSEC-relaterede ressourceposter for et domæne returneres til den REkursive DNS-fortolker som dnsSEC-autentisk, bliver den sendende mailserver bedt om den TLSA-post, der svarer til MX-værtsposten eller -posterne. Hvis TLSA-posten er til stede og dokumenteret autentisk ved hjælp af en anden DNSSEC-kontrol, returnerer den rekursive DNS-fortolker TLSA-posten til den afsendende mailserver.

Når den autentiske TLSA-post er modtaget, opretter den sendende postserver en SMTP-forbindelse til den MX-vært, der er knyttet til den autentiske TLSA-post. Den afsendere, der sender mail, forsøger at konfigurere TLS og sammenligne serverens TLS-certifikat med dataene i TLSA-posten for at validere, at den destinationsmailserver, der er forbundet med afsenderen, er den legitime modtagermailserver. Meddelelsen sendes (ved hjælp af TLS), hvis godkendelsen lykkes. Når godkendelse mislykkes, eller hvis TLS ikke understøttes af destinationsserveren, vil Exchange Online prøve hele valideringsprocessen igen, der starter med en DNS-forespørgsel for det samme destinationsdomæne, igen efter 15 minutter og derefter 15 minutter efter dette og derefter hver time i de næste 24 timer. Hvis godkendelsen fortsætter med at mislykkes efter 24 timers forsøg, udløber meddelelsen, og der genereres en NDR med fejloplysninger, som sendes til afsenderen.

## <a name="what-are-the-components-of-dane"></a>Hvad er komponenterne i DANE?

### <a name="tlsa-resource-record"></a>TLSA-ressourcepost

TLS-godkendelsesposten (TLSA) bruges til at knytte en servers X.509-certifikat eller offentlige nøgleværdi til det domænenavn, der indeholder posten. Der kan kun være tillid til TLSA-poster, hvis DNSSEC er aktiveret på dit domæne. Hvis du bruger en DNS-udbyder til at hoste dit domæne, kan dette være en indstilling, der tilbydes, når du konfigurerer et domæne med dem. Hvis du vil vide mere om signering af DNSSEC-zone, skal du gå til dette link: [Oversigt over DNSSEC-| Microsoft Docs](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj200221(v=ws.11)).

Eksempel på TLSA-post:

:::image type="content" source="../media/compliance-trial/example-TLSA-record.png" alt-text="Eksempel på TLSA-post" lightbox="../media/compliance-trial/example-TLSA-record.png":::

Der er fire konfigurerbare felter, der er entydige for TLSA-posttypen:

**Feltet Certifikatanvendelse**: Angiver, hvordan den afsendende mailserver skal bekræfte destinationens mailservers certifikat.

|Værdi|Akronym|Beskrivelse|
|---|---|---|
|01<sup></sup>|PKIX-TA|Det anvendte certifikat er det offentlige nøglecenter, der er tillid til, fra X.509-tillidskæden.|
|11<sup></sup>|PKIX-EE|Det markerede certifikat er destinationsserveren. DNSSEC-kontroller skal bekræfte ægtheden.|
|2|DANE-TA|Brug serverens private nøgle fra X.509-træet, der skal valideres af et tillidsforankring i tillidskæden. TLSA-posten angiver det tillidsforankring, der skal bruges til at validere TLS-certifikaterne for domænet.|
|3|DANE-EE|Stemmer kun overens med destinationsserverens certifikat.|

<sup>1</sup> Exchange Online følger RFC-implementeringsvejledningen om, at værdierne i certifikatanvendelsesfeltet 0 eller 1 ikke skal bruges, når DANE implementeres med SMTP. Når en TLSA-post med værdien 0 eller 1 i feltet Certifikatanvendelse returneres til Exchange Online, behandler Exchange Online den som ikke anvendelig. Hvis alle TLSA-poster ikke kan bruges, udfører Exchange Online ikke DANE-valideringstrinnene for 0 eller 1, når du sender mailen. På grund af tilstedeværelsen af en TLSA-post gennemtvinger Exchange Online i stedet brugen af TLS til at sende mailen, sende mailen, hvis destinationsmailserveren understøtter TLS eller slippe mailen og generere en NDR, hvis destinationsmailserveren ikke understøtter TLS.

I eksemplet på en TLSA-post er feltet certifikatanvendelse angivet til '3', så dataene for certifikattilknytningen ('abc123... xyz789') ville kun blive matchet med destinationsserverens certifikat.

**Vælgerfelt**: Angiver, hvilke dele af destinationsserverens certifikat der skal kontrolleres.

|Værdi|Akronym|Beskrivelse|
|---|---|---|
|0|Cert|Brug det fulde certifikat.|
|1|SPKI (oplysninger om offentlig nøgle for emne)|Brug certifikatets offentlige nøgle og den algoritme, som den offentlige nøgle identificeres til at bruge.|

I eksemplet med TLSA-posten er vælgerfeltet angivet til '1', så dataene for certifikattilknytningen matches ved hjælp af destinationservercertifikatets offentlige nøgle og den algoritme, som den offentlige nøgle identificeres til at bruge.

**Matchende typefelt**: Angiver det format, som certifikatet repræsenteres i TLSA-posten.

|Værdi|Akronym|Beskrivelse|
|---|---|---|
|0|Fuld|Dataene i TSLA-posten er det fulde certifikat eller SPKI.|
|1|SHA-256|Dataene i TSLA-posten er et SHA-256-hash for certifikatet eller SPKI.|
|2|SHA-512|Dataene i TSLA-posten er et SHA-512-hash for certifikatet eller SPKI.|

I eksemplet på en TLSA-post er feltet Matchende type angivet til '1', så dataene for certifikattilknytningen er en SHA-256-hash for emnets offentlige nøgleoplysninger fra destinationens servercertifikat

**Data for certifikattilknytning**: Angiver de certifikatdata, der bruges til at matche med destinationens servercertifikat. Disse data afhænger af værdien i selektorfeltet og den tilsvarende typeværdi.

I eksemplet på en TLSA-post er dataene for certifikattilknytningen angivet til 'abc123.. xyz789'. Da værdien for Selektorfelt i eksemplet er angivet til '1', refererer den til destinationens servercertifikats offentlige nøgle og den algoritme, der er identificeret til at blive brugt sammen med det. Og da feltværdien matchende type i eksemplet er angivet til '1', refererer den til SHA-256-hashen for emneoplysningerne for den offentlige nøgle fra destinationens servercertifikat.

## <a name="how-can-exchange-online-customers-use-smtp-dane-outbound"></a>Hvordan kan Exchange Online kunder bruge SMTP DANE-udgående?

Som Exchange Online kunde er der ikke noget, du skal gøre for at konfigurere denne forbedrede mailsikkerhed for din udgående mail. Dette er noget, vi har bygget til dig, og det er som standard aktiveret for alle Exchange Online kunder og bruges, når destinationsdomænet reklamerer for support til DANE. Hvis du vil høste fordelene ved at sende mail med DNSSEC- og DANE-kontroller, skal du kommunikere med dine forretningspartnere, som du udveksler mail med, at de skal implementere DNSSEC og DANE, så de kan modtage mail ved hjælp af disse standarder.

## <a name="how-can-exchange-online-customers-use-smtp-dane-inbound"></a>Hvordan kan Exchange Online kunder bruge indgående SMTP-DANE?

I øjeblikket understøttes indgående SMTP-DANE ikke for Exchange Online. Support forventes at blive frigivet i slutningen af 2022.

## <a name="what-is-the-recommended-tlsa-record-configuration"></a>Hvad er den anbefalede konfiguration af TLSA-poster?

Pr. RFC-implementeringsvejledning til SMTP DANE, en TLSA-post, der består af feltet Certifikatanvendelse, der er angivet til 3, feltet Selector, der er angivet til 1, og feltet Matchende type, der er angivet til 1, anbefales.

## <a name="exchange-online-mail-flow-with-smtp-dane"></a>Exchange Online Mail-Flow med SMTP-DANE

Mailflowprocessen for Exchange Online med SMTP-DANE, der vises i flowdiagrammet nedenfor, validerer domæne- og ressourcepostsikkerhed via DNSSEC, TLS-understøttelse på destinationsmailserveren, og at destinationsmailserverens certifikat stemmer overens med det, der forventes baseret på dens tilknyttede TLSA-post.

Der er kun to scenarier, hvor en SMTP-DANE-fejl medfører, at mailen blokeres:

- Destinationsdomænet signalerede DNSSEC-understøttelse, men en eller flere poster blev returneret som ikke-godkendt.

- Alle MX-poster for destinationsdomænet har TLSA-poster, og ingen af destinationsserverens certifikater svarer til det, der var forventet for TSLA-postdataene, eller en TLS-forbindelse understøttes ikke af destinationsserveren.

:::image type="content" source="../media/compliance-trial/mail-flow-smtp-dane.png" alt-text="Exchange onlinemailflow med SMTP DANE" lightbox="../media/compliance-trial/mail-flow-smtp-dane.png":::

## <a name="related-technologies"></a>Relaterede teknologier

|Teknologi|Yderligere oplysninger|
|---|---|
|**Mail Transfer Agent – Strict Transport Security (MTA-STS)** hjælper med at forhindre nedgradering og Man-in-the-Middle-angreb ved at levere en mekanisme til angivelse af domænepolitikker, der angiver, om destinationsmailserveren understøtter TLS, og hvad der skal gøres, når TLS ikke kan forhandles, f.eks. stoppe overførslen.|Flere oplysninger om Exchange Online kommende support til indgående og udgående MTA-STS vil blive udgivet senere på året. <br/><br/> [Exchange Online Transport News fra Microsoft Ignite 2020 – Microsoft Tech Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-online-transport-news-from-microsoft-ignite-2020/ba-p/1687699) <br/><br/> [rfc8461 (ietf.org)](https://datatracker.ietf.org/doc/html/rfc8461)|
|**SPF (Sender Policy Framework)** bruger IP-oplysninger til at sikre, at destinationens mailsystemer har tillid til meddelelser, der sendes fra dit brugerdefinerede domæne.|[Sådan forhindrer SPF (Sender Policy Framework) spoofing – Office 365 – Microsoft Docs](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing)|
|**DomainKeys Identificeret mail (DKIM)** bruger X.509-certifikatoplysninger til at sikre, at destinationens mailsystemer har tillid til meddelelser, der sendes udgående fra dit brugerdefinerede domæne.|[Sådan bruger du DKIM til e-mail i dit brugerdefinerede domæne – Office 365 – Microsoft Docs](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)|
|**Domænebaseret meddelelsesgodkendelse, -rapportering og -overensstemmelse (DMARC)** fungerer sammen med Sender Policy Framework og DomainKeys Identificerede mails for at godkende mailafsendere og sikre, at destinationens mailsystemer har tillid til meddelelser, der er sendt fra dit domæne.|[Brug DMARC til at validere mail, konfigurationstrin – Office 365 – Microsoft Docs](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)|

## <a name="troubleshooting-sending-emails-with-smtp-dane"></a>Fejlfinding i forbindelse med afsendelse af mails med SMTP-DANE

Der er i øjeblikket fire fejlkoder til DANE, når du sender mails med Exchange Online. Microsoft opdaterer aktivt denne fejlkodeliste. Fejlene vil være synlige i:

1. Portalen Exchange Administration via visningen Meddelelsessporingsdetaljer.
2. NDR'er genereres, når en meddelelse ikke sendes på grund af en DANE- eller DNSSEC-fejl.
3. Værktøjet Remote Connectivity Analyzer [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365).

|NDR-kode|Beskrivelse|
|---|---|
|5.7.321|starttls-not-supported: Destinationsmailserver skal understøtte TLS for at modtage mail.|
|5.7.322|certificate-expired: Destinationens mailservers certifikat er udløbet.|
|5.7.323|tlsa-invalid: Domænet mislykkedes DANE-validering.|
|5.7.324|dnssec-invalid: Destinationsdomænet returnerede ugyldige DNSSEC-poster.|

### <a name="troubleshooting-57321-starttls-not-supported"></a>Fejlfinding 5.7.321 starttls-not-supported

Dette angiver normalt et problem med destinationsmailserveren. Efter modtagelse af meddelelsen:

1. Kontrollér, at destinationsmailadressen er angivet korrekt.
2. Giv destinationsmailadministratoren besked om, at du har modtaget denne fejlkode, så de kan afgøre, om destinationsserveren er konfigureret korrekt til at modtage meddelelser ved hjælp af TLS.
3. Prøv at sende mailen igen, og gennemse meddelelsessporingsoplysningerne for meddelelsen på Exchange Administrationsportal.

### <a name="troubleshooting-57322-certificate-expired"></a>Fejlfinding 5.7.322 certifikat er udløbet

Et gyldigt X.509-certifikat, der ikke er udløbet, skal præsenteres på den sendende mailserver. X.509-certifikater skal fornys efter deres udløb, ofte årligt. Efter modtagelse af meddelelsen:

1. Giv destinationsmailadministratoren besked om, at du har modtaget denne fejlkode, og angiv fejlkodestrengen.
2. Tillad, at tiden for destinationens servercertifikat fornys, og at TLSA-posten opdateres, så den refererer til det nye certifikat. Prøv derefter at sende mailen igen, og gennemse meddelelsessporingsoplysningerne for meddelelsen på Exchange Administrationsportal.

### <a name="troubleshooting-57323-tlsa-invalid"></a>Fejlfinding 5.7.323 tlsa-invalid

Denne fejlkode er relateret til en forkert konfiguration af en TLSA-post og kan kun genereres, når der er returneret en TLSA-post, der er godkendt af DNSSEC. Der er mange scenarier under DANE-valideringen, der opstår, når posten er blevet returneret, som kan resultere i, at koden genereres. Microsoft arbejder aktivt på de scenarier, der er omfattet af denne fejlkode, så hvert scenarie har en bestemt kode. I øjeblikket kan et eller flere af disse scenarier medføre oprettelsen af fejlkoden:

1. Destinationsmailserverens certifikat stemmer ikke overens med det, der forventes for den autentiske TLSA-post.
2. Den autentiske TLSA-post er konfigureret forkert.
3. Destinationsdomænet angribes.
4. Enhver anden DANE-fejl.

Efter modtagelse af meddelelsen:

1. Giv destinationsmailadministratoren besked om, at du har modtaget denne fejlkode, og giv dem fejlkodestrengen.
2. Giv administratoren af destinationsmailen tid til at gennemse deres DANE-konfiguration og mailservercertifikatets gyldighed. Prøv derefter at sende mailen igen, og gennemse meddelelsessporingsoplysningerne for meddelelsen på Exchange Administrationsportal.

### <a name="troubleshooting-57324-dnssec-invalid"></a>Fejlfinding af 5.7.324 dnssec-invalid

Denne fejlkode genereres, når destinationsdomænet angav, at det var DNSSEC-autentisk, men Exchange Online ikke kunne bekræfte det som DNSSEC-autentisk.

Efter modtagelse af meddelelsen:

1. Giv destinationsmailadministratoren besked om, at du har modtaget denne fejlkode, og giv dem fejlkodestrengen.
2. Giv administratoren af destinationsmailen tid til at gennemse domænets DNSSEC-konfiguration. Prøv derefter at sende mailen igen, og gennemse meddelelsessporingsoplysningerne for meddelelsen på Exchange Administrationsportal.

## <a name="troubleshooting-receiving-emails-with-smtp-dane"></a>Fejlfinding i forbindelse med modtagelse af mails med SMTP-DANE

I øjeblikket er der to metoder, som en administrator af et modtagende domæne kan bruge til at validere og foretage fejlfinding af deres DNSSEC- og DANE-konfiguration for at modtage mail fra Exchange Online ved hjælp af disse standarder.

1. Anvend SMTP TLS-RPT (Transport Layer Security Reporting), der blev introduceret i [RFC8460](https://datatracker.ietf.org/doc/html/rfc8460)
2. Brug værktøjet Microsoft [Remote Connectivity Analyzer til Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365)

TLS-RPT [https://datatracker.ietf.org/doc/html/rfc8460](https://datatracker.ietf.org/doc/html/rfc8460) er en rapporteringsmekanisme, hvor afsendere kan give oplysninger til administratorer af destinationsdomæner om DANE- og MTA-STS-succeser og -fejl med disse respektive destinationsdomæner. Hvis du vil modtage TLS-RPT-rapporter, skal du kun tilføje en TXT-post i domænets DNS-poster, der indeholder den mailadresse eller URI, som rapporterne skal sendes til. Exchange Online sender TLS-RPT-rapporter i JSON-format.

Eksempel på post:

:::image type="content" source="../media/compliance-trial/example-record.png" alt-text="Eksempelpost" lightbox="../media/compliance-trial/example-record.png":::

Den anden metode er at bruge Remote Connectivity Analyzer [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365), som kan udføre de samme DNSSEC- og DANE-kontroller i forhold til din DNS-konfiguration, som Exchange Online vil gøre, når der sendes mail uden for tjenesten. Dette er den mest direkte måde at foretage fejlfinding af fejl i konfigurationen på for at modtage mail fra Exchange Online ved hjælp af disse standarder.

Når du foretager fejlfinding, kan nedenstående fejlkoder blive genereret:

|NDR-kode|Beskrivelse|
|---|---|
|4/5.7.321|starttls-not-supported: Destinationsmailserver skal understøtte TLS for at modtage mail.|
|4/5.7.322|certificate-expired: Destinationens mailservers certifikat er udløbet.|
|4/5.7.323|tlsa-invalid: Domænet mislykkedes DANE-validering.|
|4/5.7.324|dnssec-invalid: Destinationsdomænet returnerede ugyldige DNSSEC-poster.|

### <a name="troubleshooting-57321-starttls-not-supported"></a>Fejlfinding 5.7.321 starttls-not-supported

> [!NOTE]
> Disse trin er til mailadministratorer, der foretager fejlfinding af modtagelse af mail fra Exchange Online ved hjælp af SMTP-DANE.

Dette angiver normalt et problem med destinationsmailserveren. Den mailserver, som Remote Connectivity Analyzer tester oprettelse af forbindelse til. Der er generelt to scenarier, der genererer denne kode:

1. Destinationsmailserveren understøtter slet ikke sikker kommunikation, og almindelig, ikke-krypteret kommunikation skal bruges.
2. Destinationsserveren er konfigureret forkert og ignorerer STARTTLS-kommandoen.

Efter modtagelse af meddelelsen:

1. Kontrollér mailadressen.
2. Find den IP-adresse, der er knyttet til fejlsætningen, så du kan identificere den mailserver, som sætningen er knyttet til.
3. Kontrollér mailserverens indstilling for at sikre, at den er konfigureret til at lytte efter SMTP-trafik (ofte portene 25 og 587).
4. Vent et par minutter, og prøv derefter at udføre testen igen med værktøjet Remote Connectivity Analyzer.
5. Hvis det stadig ikke lykkes, kan du prøve at fjerne TLSA-posten og køre testen med værktøjet Remote Connectivity Analyzer igen.
6. Hvis der ikke er nogen fejl, kan dette indikere, at den mailserver, du bruger til at modtage mails, ikke understøtter STARTTLS, og du skal muligvis opgradere til en, der gør det for at bruge DANE.

### <a name="troubleshooting-57322-certificate-expired"></a>Fejlfinding 5.7.322 certifikat er udløbet

> [!NOTE]
> Disse trin er til mailadministratorer, der foretager fejlfinding af modtagelse af mail fra Exchange Online ved hjælp af SMTP-DANE.

Et gyldigt X.509-certifikat, der ikke er udløbet, skal præsenteres på den sendende mailserver. X.509-certifikater skal fornys efter deres udløb, ofte årligt. Efter modtagelse af meddelelsen:

1. Kontrollér den IP-adresse, der er knyttet til fejlsætningen, så du kan identificere den mailserver, den er knyttet til. Find det udløbne certifikat på den mailserver, du har identificeret.
2. Log på din certifikatudbyders websted.
3. Vælg det udløbne certifikat, og følg instruktionerne for at forny og betale for fornyelsen.
4. Når din udbyder har bekræftet købet, kan du downloade et nyt certifikat.
5. Installér det nye certifikat på den tilknyttede mailserver.
6. Opdater mailserverens tilknyttede TLSA-post med det nye certifikats data.
7. Når du har ventet et passende tidsrum, skal du prøve testen igen med værktøjet Remote Connectivity Analyzer.

### <a name="troubleshooting-57323-tlsa-invalid"></a>Fejlfinding 5.7.323 tlsa-invalid

> [!NOTE]
> Disse trin er til mailadministratorer, der foretager fejlfinding af modtagelse af mail fra Exchange Online ved hjælp af SMTP-DANE.

Denne fejlkode er relateret til en forkert konfiguration af en TLSA-post og kan kun genereres, når der er returneret en TSLA-post, der er godkendt af DNSSEC. Men der er mange scenarier under DANE-valideringen, der opstår, når posten er blevet returneret, som kan resultere i, at koden genereres. Microsoft arbejder aktivt på de scenarier, der er omfattet af denne fejlkode, så hvert scenarie har en bestemt kode. I øjeblikket kan et eller flere af disse scenarier medføre oprettelsen af fejlkoden:

1. Den autentiske TLSA-post er konfigureret forkert.
2. Certifikatet er endnu ikke gyldigt/konfigureret til et fremtidigt tidsvindue.
3. Destinationsdomænet angribes.
4. Enhver anden DANE-fejl.

Efter modtagelse af meddelelsen:

1. Kontrollér den IP-adresse, der er knyttet til fejlsætningen, for at identificere den mailserver, den er knyttet til.
2. Identificer den TLSA-post, der er knyttet til den identificerede mailserver.
3. Kontrollér konfigurationen af TLSA-posten for at sikre, at den signalerer afsenderen til at udføre de foretrukne DANE-kontroller, og at de korrekte certifikatdata er inkluderet i TLSA-posten.
    1. Hvis du er nødt til at foretage opdateringer af posten for uoverensstemmelser, skal du vente et par minutter og derefter køre testen igen med værktøjet Remote Connectivity Analyzer.
4. Find certifikatet på den identificerede mailserver.
5. Kontrollér det tidsvindue, som certifikatet er gyldigt for. Hvis den er indstillet til at starte gyldigheden på en fremtidig dato, skal den fornys for dags dato.
    1. Log på din certifikatudbyders websted.
    2. Vælg det udløbne certifikat, og følg instruktionerne for at forny og betale for fornyelsen.
    3. Når din udbyder har bekræftet købet, kan du downloade et nyt certifikat.
    4. Installér det nye certifikat på den tilknyttede mailserver.

### <a name="troubleshooting-57324-dnssec-invalid"></a>Fejlfinding af 5.7.324 dnssec-invalid

> [!NOTE]
> Disse trin er til mailadministratorer, der foretager fejlfinding af modtagelse af mail fra Exchange Online ved hjælp af SMTP-DANE.

Denne fejlkode genereres, når destinationsdomænet angav, at det er DNSSEC-autentisk, men Exchange Online ikke kan bekræfte det som DNSSEC-autentisk. Dette afsnit er ikke omfattende til fejlfinding af DNSSEC-problemer og fokuserer på scenarier, hvor domæner tidligere har bestået DNSSEC-godkendelse, men ikke nu.

Efter modtagelse af meddelelsen:

1. Hvis du bruger en DNS-udbyder, f.eks. GoDaddy, skal du advare din DNS-udbyder om fejlen, så de kan arbejde med fejlfindings- og konfigurationsændringen.
2. Hvis du administrerer din egen DNSSEC-infrastruktur, er der mange fejlkonfigurationer i DNSSEC, der kan generere denne fejlmeddelelse. Nogle almindelige problemer, du skal kontrollere, om din zone tidligere har passeret DNSSEC-godkendelse:
    1. Brudt tillidskæde, når den overordnede zone indeholder et sæt DS-poster, der peger på noget, der ikke findes i den underordnede zone. Dette medfører, at den underordnede zone markeres som falsk ved at validere fortolkere.
        - Løs problemet ved at gennemgå de underordnede domænerSIG-nøgle-id'er og sikre, at de stemmer overens med nøgle-id'erne i de DS-poster, der er publiceret i den overordnede zone.
    2. RRSIG-ressourceposten for domænet er ikke gyldig tid, den er enten udløbet, eller dens gyldighedsperiode er ikke begyndt.
        - Løs problemet ved at generere nye signaturer for domænet ved hjælp af gyldige tidsintervaller.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="as-an-exchange-online-customer-can-i-opt-out-of-using-dnssec-andor-dane"></a>Kan jeg som Exchange Online kunde fravælge at bruge DNSSEC og/eller DANE?

Vi er overbeviste om, at DNSSEC og DANE vil øge vores tjenestes sikkerhedsposition markant og gavne alle vores kunder. Vi har i løbet af det sidste år arbejdet flittigt på at reducere risikoen for og alvorsgraden af den potentielle indvirkning, som denne udrulning kan have for M365-kunder. Vi overvåger og sporer aktivt udrulningen for at sikre, at negativ indvirkning minimeres, efterhånden som den udrulles. Derfor er undtagelser på lejerniveau eller fravalg ikke tilgængelige.
Hvis du oplever problemer, der er relateret til aktivering af DNSSEC og/eller DANE, hjælper de forskellige metoder til undersøgelse af fejl, der er nævnt i dette dokument, dig med at identificere kilden til fejlen. I de fleste tilfælde er problemet med den eksterne destinationspart, og du skal kommunikere med disse forretningspartnere, at de skal konfigurere DNSSEC og DANE korrekt for at modtage mail fra Exchange Online ved hjælp af disse standarder.

### <a name="how-does-dnssec-relate-to-dane"></a>Hvordan relaterer DNSSEC til DANE?

DNSSEC føjer et tillidslag til DNS-opløsningen ved at bruge infrastrukturen for offentlige nøgler for at sikre, at de poster, der returneres som svar på en DNS-forespørgsel, er autentiske. DANE sikrer, at den modtagende mailserver er den legitime og forventede mailserver for den autentiske MX-post.

### <a name="what-is-the-difference-between-mta-sts-and-dane-for-smtp"></a>Hvad er forskellen mellem MTA-STS og DANE for SMTP?

DANE og MTA-STS har samme formål, men DANE kræver DNSSEC til DNS-godkendelse, mens MTA-STS er afhængig af nøglecentre.

### <a name="why-isnt-opportunistic-tls-sufficient"></a>Hvorfor er opportunistisk TLS ikke tilstrækkelig?

Opportunistisk TLS krypterer kommunikationen mellem to slutpunkter, hvis begge accepterer at understøtte den. Men selvom TLS krypterer overførslen, kan et domæne blive spoofed under DNS-opløsningen, så det peger på en ondsindet aktørs slutpunkt i stedet for det reelle slutpunkt for domænet. Dette er et hul i mailsikkerheden, der håndteres ved at implementere MTA-STS- og/eller SMTP-DANE med DNSSEC.

### <a name="why-isnt-dnssec-sufficient"></a>Hvorfor er DNSSEC ikke tilstrækkeligt?

DNSSEC er ikke helt modstandsdygtig over for Man-in-the-Middle-angreb og nedgradere (fra TLS til klartekst)-angreb i forbindelse med mailflowscenarier. Tilføjelsen af MTA-STS og DANE sammen med DNSSEC giver en omfattende sikkerhedsmetode til at forhindre både MITM- og nedgraderingsangreb.

## <a name="additional-links"></a>Yderligere links

[Find og løs problemer, når du har tilføjet dit domæne eller dine DNS-poster](/microsoft-365/admin/get-help-with-domains/find-and-fix-issues)

[Oversigt over DNSSEC-| Microsoft Docs](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj200221(v=ws.11))

[Brug DMARC til at validere mail, konfigurationstrin – Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)

[Sådan bruger du DKIM til mail i dit brugerdefinerede domæne - Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)

[Sådan forhindrer SPF (Sender Policy Framework) spoofing – Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing)

[Exchange Online Transport News fra Microsoft Ignite 2020 – Microsoft Tech Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-online-transport-news-from-microsoft-ignite-2020/ba-p/1687699)

[rfc8461 (ietf.org)](https://datatracker.ietf.org/doc/html/rfc8461)
