---
title: Sådan fungerer SMTP DNS-baseret godkendelse for navngivne enheder (DANE) for at sikre mailkommunikation
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
description: Få mere at vide om, hvordan SMTP DNS-baseret godkendelse af navngivne enheder (DANE) fungerer for at sikre mailkommunikation mellem mailservere.
ms.openlocfilehash: 32c39859d9bfdf292fd9c7a315a0ee1ee08eae2e
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/29/2022
ms.locfileid: "63593683"
---
# <a name="how-smtp-dns-based-authentication-of-named-entities-dane-works"></a>Sådan fungerer SMTP DNS-baseret godkendelse af navngivne enheder (DANE)

SMTP-protokollen er den primære protokol, der bruges til at overføre meddelelser mellem mailservere og er som standard ikke sikker. Protokollen Transport Layer Security (TLS) blev introduceret for flere år siden for at understøtte krypteret overførsel af meddelelser via SMTP. Det bruges ofte opportunistisk i stedet for som et krav, hvilket efterlader meget mailtrafik i klar tekst, sårbar over for skæring efter uønskede deltagere. DESUDEN bestemmer SMTP IP-adresserne på destinationsservere via den offentlige DNS-infrastruktur, hvilket er udsat for spoofing- og MAN-in-the-Middle-angreb (MITM). Dette har medført, at der er skabt mange nye standarder for at øge sikkerheden for afsendelse og modtagelse af mail, en af dem er DNS-baseret godkendelse af navngivne enheder (DANE).
  
DANE for SMTP [RFC 7672](https://tools.ietf.org/html/rfc7672) bruger tilstedeværelsen af en TLSA-post (Transport Layer Security Authentication) i et domænes DNS-postsæt til at signalere et domæne, og dets mailserver(er) understøtter DANE. Hvis der ikke er nogen TLSA-post til stede, vil DNS-opløsningen for mailflow fungere som normalt, uden der forsøges DANE-kontroller. TLSA-posten signalerer sikkert TLS-understøttelse og udgiver DANE-politikken for domænet. Derfor kan afsendelse af mailservere godkende legitime modtagende mailservere ved hjælp af SMTP DANE. Det gør det yndet at nedgradere og MITM-angreb. DANE har direkte afhængigheder af DNSSEC, som fungerer ved digitalt at signere poster for DNS-opslag ved hjælp af offentlig nøglekryptografi. DNSSEC-kontroller udføres på rekursive DNS resolvers, de DNS-servere, der laver DNS-forespørgsler for klienter. DNSSEC sikrer, at DNS-poster ikke bliver ændret og er ægte.  

Når de MX-, A/AAAA- og DNSSEC-relaterede ressourceposter for et domæne returneres til den DNS-rekursive resolver som DNSSEC-autentisk, vil den afsendende mailserver bede om TLSA-posten svarende til MX-værtsposten eller -posterne. Hvis TLSA-posten er til stede og har vist sig at være ægte ved hjælp af en anden DNSSEC-kontrol, vil den DNS-rekursive løsning returnere TLSA-posten til den afsendende mailserver. 

Når du har modtaget den ægte TLSA-post, etablerer den afsendende mailserver en SMTP-forbindelse til den MX-vært, der er knyttet til den ægte TLSA-post. Den afsendende mailserver forsøger at konfigurere TLS og sammenligne serverens TLS-certifikat med dataene i TLSA-posten for at validere, om den destinationsmailserver, der har forbindelse til afsenderen, er den legitime modtagende mailserver. Meddelelsen overføres ved hjælp af TLS, hvis godkendelse lykkes. Når godkendelse mislykkes, eller hvis TLS ikke understøttes af destinationsserveren, vil Exchange Online forsøge hele valideringsprocessen igen med en DNS-forespørgsel for det samme destinationsdomæne igen efter 15 minutter og derefter 15 minutter derefter hver time de næste 24 timer. Hvis godkendelse mislykkes efter 24 timer efter forsøg på at prøve igen, udløber meddelelsen, og der genereres en NDR med fejloplysninger, som sendes til afsenderen. 

## <a name="what-are-the-components-of-dane"></a>Hvad er komponenterne i DANE?

### <a name="tlsa-resource-record"></a>TLSA-ressourcepost

TLS-godkendelsesposten (TLSA) bruges til at knytte en servers X.509-certifikat eller offentlige nøgleværdi til det domænenavn, der indeholder posten. Der kan kun være tillid til TLSA-poster, hvis DNSSEC er aktiveret på dit domæne. Hvis du bruger en DNS-udbyder som vært for dit domæne, kan dette være en indstilling, der tilbydes, når du konfigurerer et domæne med dem. Hvis du vil have mere at vide om SIGNERING af DNSSEC-zone, skal du se dette link: [Oversigt over DNSSEC | Microsoft Docs](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj200221(v=ws.11)). 
  
Eksempel på TLSA-post:
  
:::image type="content" source="../media/compliance-trial/example-TLSA-record.png" alt-text="Eksempel på TLSA-post" lightbox="../media/compliance-trial/example-TLSA-record.png":::

Der findes fire konfigurerbare felter, der er entydige for TLSA-posttypen: 

**Feltet Brug af certifikat**: Angiver, hvordan den afsendende mailserver skal bekræfte mailserverens certifikat.

|Værdi  |Akronym  |Beskrivelse |
|---------|---------|---------|
|01<sup></sup>     |PKIX-TA          |Det brugte certifikat er det offentlige nøglecenter for tillidsankeren fra X.509-tillidskæden.          |
|11<sup></sup>     |PKIX-EE         |Afkrydset certifikat er destinationsserveren. DNSSEC-kontroller skal bekræfte ægtheden.          |
|2     |DANE-TA         |Brug serverens private nøgle fra X.509-træet, der skal valideres af en tillidsanker i tillidskæden. TLSA-posten angiver tillidsankeret, der skal bruges til at validere TLS-certifikaterne for domænet.         |
|3     |DANE-EE         |Matcher kun med destinationsserverens certifikat.           |

<sup>1</sup> Exchange Online følger RFC-implementeringsvejledningen, som angiver, at værdierne for feltet Certifikatforbrug på 0 eller 1 ikke skal bruges, når DANE implementeres med SMTP.   Når en TLSA-post med feltværdien 0 eller 1 i certifikatforbrug returneres til Exchange Online, behandler Exchange Online den som ikke brugbar. Hvis alle TLSA-poster bliver fundet ubrugelige, udfører Exchange Online DANE-valideringstrinnene for 0 eller 1, når du sender mailen. På grund af tilstedeværelsen af en TLSA-post gennemtvinger Exchange Online i stedet brugen af TLS til at sende mailen, sender mailen, hvis destinationsmailserveren understøtter TLS, eller slipper mailen og genererer en NDR, hvis destinationsmailserveren ikke understøtter TLS.     

I eksemplet TLSA-post er feltet Brug af certifikat angivet til '3', så dataene for certifikatsammenknytning ('abc123... xyz789' blev kun matchet med destinationsserverens certifikat.

**Vælgerfelt**: Angiver, hvilke dele af destinationsserverens certifikat der skal kontrolleres. 

|Værdi  |Akronym  |Beskrivelse  |
|---------|---------|---------|
|0     |Cert         |Brug det fulde certifikat.         |
|1     |SPKI (oplysninger om offentlig emnenøgle)          |Brug certifikatets offentlige nøgle og den algoritme, som den offentlige nøgle er identificeret med til brug.          |

I eksemplet TLSA-post er feltet Selector angivet til "1", så data for certifikatsammenknytning ville blive matchet ved hjælp af destinationens servercertifikats offentlige nøgle og algoritmen, som den offentlige nøgle identificeres med til brug.

**Feltet Tilsvarende type**: Angiver det format, som certifikatet skal repræsenteres i TLSA-posten. 

|Værdi  |Akronym  |Beskrivelse  |
|---------|---------|---------|
|0     |Fuld         |Dataene i TSLA-posten er det fulde certifikat eller SPKI.          |
|1     |SHA-256         |Dataene i TSLA-posten er en SHA-256-hash for enten certifikatet eller SPKI'en.          |
|2     |SHA-512         |Dataene i TSLA-posten er en SHA-512-hash for enten certifikatet eller SPKI..         |

I eksemplet TLSA-post er feltet Tilsvarende type angivet til "1", så dataene i certifikatsammenknytning er en SHA-256-hash for den offentlige emnenøgle fra destinationens servercertifikat

**Data for** certifikatsammenknytning: Angiver de certifikatdata, der bruges til at matche med destinationens servercertifikat. Disse data afhænger af værdien for feltetvælger og værdien for den matchende type.

I eksemplet TLSA-post er dataene for certifikatsammenknytning angivet til "abc123... xyz789'. Da værdien Feltvælger i eksemplet er angivet til '1', henviser den til destinationens servercertifikats offentlige nøgle og den algoritme, der er identificeret til at blive brugt sammen med det. Og da feltværdien Matchende Type i eksemplet er angivet til '1', henviser den til SHA-256-hash'en for offentlige emnenøgleoplysninger fra destinationens servercertifikat.

## <a name="how-can-exchange-online-customers-use-smtp-dane-outbound"></a>Hvordan kan Exchange Online bruge SMTP DANE udgående?

Som kunde Exchange Online er der ikke noget, du skal gøre for at konfigurere denne udvidede mailsikkerhed for din udgående mail. Dette er noget, vi har bygget til dig, og det er som standard tændt for alle Exchange Online-kunder og bruges, når destinationsdomænet annoncerer understøttelse af DANE. For at få fordelene ved at sende mail med DNSSEC- og DANE-kontroller kan du kommunikere med dine forretningspartnere, som du udveksler mail med, om de skal implementere DNSSEC og DANE, så de kan modtage mails ved hjælp af disse standarder. 

## <a name="how-can-exchange-online-customers-use-smtp-dane-inbound"></a>Hvordan kan Exchange Online benytte SMTP DANE indgående?

Indgående SMTP DANE understøttes i øjeblikket ikke for Exchange Online. Support forventes at blive frigivet i slutningen af 2022. 

## <a name="what-is-the-recommended-tlsa-record-configuration"></a>Hvad er den anbefalede konfiguration af TLSA-post?

Pr. RFC-implementeringsvejledning for SMTP DANE, en TLSA-post, der består af feltet Certifikatforbrug angivet til 3, feltet Selector angivet til 1, og det matchende typefelt, der er angivet til 1, anbefales. 

## <a name="exchange-online-mail-flow-with-smtp-dane"></a>Exchange Online mail Flow med SMTP DANE 

Mailflowprocessen for Exchange Online med SMTP DANE, der er vist i rutediagrammet nedenfor, validerer domæne- og ressourcepostsikkerheden via DNSSEC, TLS-understøttelse på destinationsmailserveren, og at destinationens mailservers certifikat stemmer overens med det forventede ud fra den tilknyttede TLSA-post. 

Der er kun to scenarier, hvor en SMTP DANE-fejl medfører, at mailen blokeres:

- Destinationsdomænet signalerede DNSSEC-support, men en eller flere poster blev returneret som ikke-godkendt. 

- Alle MX-poster for destinationsdomænet har TLSA-poster, og ingen af destinationsserverens certifikater svarer til det, der forventes pr. TSLA-postdataene, eller en TLS-forbindelse understøttes ikke af destinationsserveren.

:::image type="content" source="../media/compliance-trial/mail-flow-smtp-dane.png" alt-text="Exchange onlinemailflow med SMTP DANE" lightbox="../media/compliance-trial/mail-flow-smtp-dane.png":::

## <a name="related-technologies"></a>Relaterede teknologier 

|Teknologi  |Yderligere oplysninger  |
|---------|---------|
|**Mailoverførselsagent – Strict Transport Security (MTA-STS)** hjælper med at nedgradere og Man-in-the-Middle-angreb ved at give en mekanisme til at angive domænepolitikker, der angiver, om destinationens mailserver understøtter TLS, og hvad der skal ske, når der ikke kan forhandles i TLS, f.eks. stoppe overførslen.     |Flere oplysninger om Exchange Online kommende support til indgående og udgående MTA-STS udgives senere i år.     [Exchange Online transportnyheder fra Microsoft Ignite 2020 – Microsoft Tech Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-online-transport-news-from-microsoft-ignite-2020/ba-p/1687699)<br /><br />[rfc8461 (ietf.org)](https://datatracker.ietf.org/doc/html/rfc8461) |
|**SPF (Sender Policy Framework) bruger IP-oplysninger** til at sikre, at destinationens mailsystemer har tillid til meddelelser, der sendes fra dit brugerdefinerede domæne.    |   [Sådan forhindrer SPF (Sender Policy Framework) spoofing - Office 365 - Microsoft Docs](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing)      |
|**DomainKeys Identified Mail (DKIM)** bruger X.509-certifikatoplysninger til at sikre, at destinationens mailsystemer har tillid til meddelelser, der sendes udgående fra dit brugerdefinerede domæne.      | [Sådan bruger du DKIM til mail i dit brugerdefinerede domæne – Office 365 – Microsoft Docs](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)        |
|**Domain-based Message Authentication, Reporting, and Conformance (DMARC)** works with Sender Policy Framework and DomainKeys Identified Mail to authenticate mail senders and ensure that destination email systems trust messages sent from your domain.      |  [Brug DMARC til at validere mail, konfigurationstrin – Office 365 – Microsoft-dokumenter](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)       |

## <a name="troubleshooting-sending-emails-with-smtp-dane"></a>Fejlfinding i forbindelse med afsendelse af mails med SMTP DANE

Der er i øjeblikket fire fejlkoder til DANE, når du sender mails med Exchange Online. Microsoft opdaterer aktivt denne fejlkodeliste. Fejlene vil være synlige i:
1.  Portalen Exchange Administration via visningen Detaljer om meddelelsessporing.
2.  NDR'er genereres, når en meddelelse ikke sendes på grund af en DANE- eller DNSSEC-fejl.
3.  Værktøjet Remote Connectivity Analyzer [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365).

|NDR-kode  |Beskrivelse  |
|---------|---------|
|5.7.321     |starttls-not-supported: Destination mailserveren skal understøtte TLS for at modtage mail.          |
|5.7.322     |certifikat udløbet: Destinationens mailservers certifikat er udløbet.          |
|5.7.323     |tlsa-invalid: Domænet kunne ikke validere DANE.          |
|5.7.324     |dnssec-invalid: Destinationsdomænet har returneret ugyldige DNSSEC-poster.         |

### <a name="troubleshooting-57321-starttls-not-supported"></a>Fejlfinding af 5.7.321 starttls-not-supported

Dette angiver som regel et problem med mailserveren på destinationen. Når du har modtaget meddelelsen:
1.  Kontrollér, at destinationsmailadressen blev angivet korrekt.
2.  Giv destinationen besked til mailadministratoren om, at du har modtaget denne fejlkode, så de kan afgøre, om destinationsserveren er konfigureret korrekt til at modtage meddelelser ved hjælp af TLS. 
3.  Prøv igen at sende mailen, og gennemse oplysninger om meddelelsessporing for meddelelsen i Exchange Administration.

### <a name="troubleshooting-57322-certificate-expired"></a>Fejlfinding af 5.7.322 certifikat udløbet

Et gyldigt X.509-certifikat, der ikke er udløbet, skal præsenteres for den afsendende mailserver. X.509-certifikater skal fornys efter deres udløb årligt. Når du har modtaget meddelelsen:

1.  Giv destinationen en mailadministrator besked om, at du har modtaget denne fejlkode, og angiv fejlkodestrengen.
2.  Sørg for, at tiden til, at destinationsservercertifikatet fornyes, og TLSA-posten opdateres for at henvise til det nye certifikat. Prøv derefter at sende mailen igen, og gennemse detaljer om meddelelsessporing for meddelelsen Exchange Portalen Administration.

### <a name="troubleshooting-57323-tlsa-invalid"></a>Fejlfinding af 5.7.323 tlsa-invalid

Denne fejlkode er relateret til en forkert konfiguration af en TLSA-post og kan kun genereres, når der er returneret en DNSSEC-autentisk TLSA-post. Der er mange scenarier under DANE-valideringen, der opstår, når posten er returneret, og som kan resultere i, at koden genereres. Microsoft arbejder aktivt på de scenarier, der er dækket af denne fejlkode, så hvert scenarie har en bestemt kode. I øjeblikket kan et eller flere af disse scenarier forårsage generering af fejlkoden:

1.  Destinationens mailservers certifikat stemmer ikke overens med det, der forventes pr. den autentiske TLSA-post.
2.  Den autentiske TLSA-post er konfigureret forkert.
3.  Destinationsdomænet bliver angreb.
4.  Alle andre DANE-fejl.

Når du har modtaget meddelelsen:

1. Giv destinationen en mailadministrator besked om, at du har modtaget denne fejlkode, og giv dem fejlkodestrengen.
2. Giv destinationen for mailadministratoren tid til at gennemgå dens DANE-konfiguration og mailservercertifikats gyldighed. Prøv derefter at sende mailen igen, og gennemse detaljer om meddelelsessporing for meddelelsen Exchange Portalen Administration.

### <a name="troubleshooting-57324-dnssec-invalid"></a>Fejlfinding af 5.7.324 dnssec-invalid

Denne fejlkode genereres, når destinationsdomænet angav, at det var DNSSEC-autentisk, men Exchange Online kunne ikke bekræfte den som DNSSEC-autentisk. 

Når du har modtaget meddelelsen:

1. Giv destinationen en mailadministrator besked om, at du har modtaget denne fejlkode, og giv dem fejlkodestrengen.
2. Giv mailadministratoren for destinationen tid til at gennemgå domænets DNSSEC-konfiguration. Prøv derefter at sende mailen igen, og gennemse detaljer om meddelelsessporing for meddelelsen Exchange Portalen Administration.

## <a name="troubleshooting-receiving-emails-with-smtp-dane"></a>Fejlfinding i forbindelse med modtagelse af mails med SMTP DANE

Der er i øjeblikket to metoder, en administrator af et modtagende domæne kan bruge til at validere og foretage fejlfinding af deres DNSSEC- og DANE-konfiguration for at modtage mails fra Exchange Online ved hjælp af disse standarder. 

1. Indføre SMTP TLS-RPT (Transport Layer Security Reporting) introduceret i [RFC8460](https://datatracker.ietf.org/doc/html/rfc8460) 
2. Brug analyseværktøjet Remote Connectivity Analyzer [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365)

TLS-RPT [https://datatracker.ietf.org/doc/html/rfc8460](https://datatracker.ietf.org/doc/html/rfc8460) er en rapporteringsmekanisme, som afsendere kan bruge til at give oplysninger til destinationens domæneadministratorer om succeser og fejl i MTA-STS med disse respektive destinationsdomæner. For at modtage TLS-RPT-rapporter skal du kun tilføje en TXT-post i domænets DNS-poster, som indeholder den mailadresse eller URI, som rapporterne skal sendes til. Exchange Online sender TLS-RPT-rapporter i JSON-format. 

Eksempelpost:

:::image type="content" source="../media/compliance-trial/example-record.png" alt-text="Eksempelpost" lightbox="../media/compliance-trial/example-record.png":::

Den anden metode er at bruge [Microsoft Remote Connectivity Analyzer Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365), som kan udføre de samme DNSSEC- og DANE-kontroller i forhold til din DNS-konfiguration, som Exchange Online gør, når du sender mails uden for tjenesten. Dette er den mest direkte metode til fejlfinding i din konfiguration til at modtage mails fra Exchange Online ved hjælp af disse standarder. 

Ved fejlfinding kan nedenstående fejlkoder genereres:

|NDR-kode  |Beskrivelse |
|---------|---------|
|4/5.7.321     |starttls-not-supported: Destination mailserveren skal understøtte TLS for at modtage mail.          |
|4/5.7.322     |certifikat udløbet: Destinationens mailservers certifikat er udløbet.          |
|4/5.7.323    |tlsa-invalid: Domænet kunne ikke validere DANE.         |
|4/5.7.324     |dnssec-invalid: Destinationsdomænet har returneret ugyldige DNSSEC-poster.         |

### <a name="troubleshooting-57321-starttls-not-supported"></a>Fejlfinding af 5.7.321 starttls-not-supported

> [!NOTE]
> Disse trin er til mailadministratorer, der foretager fejlfinding i forbindelse med at modtage Exchange Online mail via SMTP DANE.

Dette angiver som regel et problem med mailserveren på destinationen. Den mailserver, som Remote Connectivity Analyzer tester forbindelsen med. Der er generelt to scenarier, der genererer denne kode: 

1.  Destinationsmailserveren understøtter slet ikke sikker kommunikation, og almindelig, ikke-krypteret kommunikation skal bruges. 
2.  Destinationsserveren er konfigureret forkert og ignorerer kommandoen STARTTLS.
    
Når du har modtaget meddelelsen:

1. Kontrollér mailadressen.
2. Find den IP-adresse, der er knyttet til fejlsætningen, så du kan identificere den mailserver, som sætningen er knyttet til.
3. Kontrollér mailserverens indstilling for at sikre, at den er konfigureret til at lytte efter SMTP-trafik (ofte portene 25 og 587).
4. Vent et par minutter, og prøv derefter testen igen med værktøjet Remote Connectivity Analyzer.
5. Hvis det stadig mislykkes, skal du prøve at fjerne TLSA-posten og køre testen med værktøjet Remote Connectivity Analyzer igen.
6. Hvis der ikke er nogen fejl, kan dette angive, at den mailserver, du bruger til at modtage mail, ikke understøtter STARTTLS, og det kan være nødvendigt at opgradere til en, der gør det, for at bruge DANE. 

### <a name="troubleshooting-57322-certificate-expired"></a>Fejlfinding af 5.7.322 certifikat udløbet

> [!NOTE]
> Disse trin er til mailadministratorer, der foretager fejlfinding i forbindelse med at modtage Exchange Online mail via SMTP DANE.

Et gyldigt X.509-certifikat, der ikke er udløbet, skal præsenteres for den afsendende mailserver. X.509-certifikater skal fornys efter deres udløb årligt. Når du har modtaget meddelelsen:

1. Kontrollér den IP- adresse, der er knyttet til fejlsætningen, så du kan identificere den mailserver, den er knyttet til. Find det udløbne certifikat på den mailserver, du har identificeret.
2. Log på certifikatudbyderens websted.
3. Vælg det udløbne certifikat, og følg vejledningen for at forny og betale for fornyelsen.
4. Når din udbyder har bekræftet købet, kan du downloade et nyt certifikat.
5. Installér det fornyede certifikat til den tilknyttede mailserver.
6. Opdater mailserverens tilknyttede TLSA-post med det nye certifikats data. 
7. Når du har ventet et passende tidsrum, kan du prøve testen igen med værktøjet Remote Connectivity Analyzer.

### <a name="troubleshooting-57323-tlsa-invalid"></a>Fejlfinding af 5.7.323 tlsa-invalid

> [!NOTE]
> Disse trin er til mailadministratorer, der foretager fejlfinding i forbindelse med at modtage Exchange Online mail via SMTP DANE.

Denne fejlkode er relateret til en forkert konfiguration af en TLSA-post og kan kun genereres, når der er returneret en DNSSEC-autentisk TSLA-post. Men der er mange scenarier under DANE-valideringen, der opstår, når posten er returneret, hvilket kan resultere i, at koden genereres. Microsoft arbejder aktivt på de scenarier, der er dækket af denne fejlkode, så hvert scenarie har en bestemt kode. I øjeblikket kan et eller flere af disse scenarier forårsage generering af fejlkoden:

1. Den autentiske TLSA-post er konfigureret forkert.
2. Certifikatet er endnu ikke tidsgyldigt/konfigureret for en fremtidig periode. 
3. Destinationsdomænet bliver angreb.
4. Alle andre DANE-fejl.

Når du har modtaget meddelelsen:

1. Kontrollér den IP-adresse, der er knyttet til fejlsætningen, for at identificere den mailserver, den er knyttet til. 
2. Identificer den TLSA-post, der er knyttet til den identificerede mailserver. 
3. Kontrollér konfigurationen af TLSA-posten for at sikre, at den signalerer, at afsenderen skal udføre den foretrukne DANE-kontrol, og at de korrekte certifikatdata er inkluderet i TLSA-posten. 
    1. Hvis du skal foretage opdateringer af posten for uoverensstemmelser, skal du vente et par minutter og derefter køre testen igen med værktøjet Remote Connectivity Analyzer. 
4. Find certifikatet på den identificerede mailserver.
5. Kontrollér det tidsrum, certifikatet er gyldigt i. Hvis den er indstillet til at starte gyldighed på en fremtidig dato, skal den fornys for den aktuelle dato.
    1. Log på certifikatudbyderens websted.
    2. Vælg det udløbne certifikat, og følg vejledningen for at forny og betale for fornyelsen.
    3. Når din udbyder har bekræftet købet, kan du downloade et nyt certifikat.
    4. Installér det fornyede certifikat til den tilknyttede mailserver.

### <a name="troubleshooting-57324-dnssec-invalid"></a>Fejlfinding af 5.7.324 dnssec-invalid

> [!NOTE]
> Disse trin er til mailadministratorer, der foretager fejlfinding i forbindelse med at modtage Exchange Online mail via SMTP DANE.

Denne fejlkode genereres, når destinationsdomænet har angivet, at det er DNSSEC-autentisk, men Exchange Online kan ikke bekræfte den som DNSSEC-autentisk. Dette afsnit er ikke omfattende til fejlfinding af DNSSEC-problemer og fokuserer på scenarier, hvor domæner tidligere har videregivet DNSSEC-godkendelse, men ikke nu. 

Når du har modtaget meddelelsen:

1. Hvis du bruger en DNS-udbyder, f.eks. GoDaddy, skal du give din DNS-udbyder besked om fejlen, så de kan arbejde på fejlfinding og konfigurationsændring. 
2. Hvis du administrerer din egen DNSSEC-infrastruktur, er der mange forkerte DNSSEC-konfigurationer, der kan generere denne fejlmeddelelse. Nogle almindelige problemer til at kontrollere, om din zone tidligere anvendte DNSSEC-godkendelse:
    1. Brudt tillidskæde, når den overordnede zone indeholder et sæt DS-poster, der peger på noget, der ikke findes i den underordnede zone. Dette medfører, at den underordnede zone markeres som bogus ved at validere løsere. 
        - Løs problemet ved at gennemgå de underordnede domæners RRSIG-nøgle-ID'er og sikre, at de stemmer overens med de vigtigste IDs i de DS-poster, der er publiceret i den overordnede zone. 
    2. RRSIG-ressourcepost for domænet er ikke gyldig i tide, den er enten udløbet, eller også er dens gyldighedsperiode ikke begyndt. 
        - Løs ved at generere nye signaturer for domænet ved hjælp af gyldige tidsrum. 

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="as-an-exchange-online-customer-can-i-opt-out-of-using-dnssec-andor-dane"></a>Kan jeg Exchange Online DNSSEC og/eller DANE som kunde?

Vi er stærkt overbeviste om, at DNSSEC og DANE vil øge sikkerhedspositionen betydeligt for vores tjenester og til gavn for alle vores kunder. Vi har arbejdet omhyggelig i løbet af det sidste år for at reducere risikoen og alvorligheden af de potentielle konsekvenser, denne installation kan have for M365-kunder. Vi overvåger og sporer aktivt installationen for at sikre, at den negative påvirkning minimeres, efterhånden som den udrulles. På grund af dette vil undtagelser eller fravalg på lejerniveau ikke være tilgængelige.
Hvis du oplever problemer i forbindelse med aktivering af DNSSEC og/eller DANE, kan de forskellige metoder til undersøgelse af fejl, der er angivet i dette dokument, hjælpe dig med at identificere årsagen til fejlen. I de fleste tilfælde vil problemet være hos den eksterne destinationspartner, og du skal kommunikere til disse forretningspartnere, at de skal konfigurere DNSSEC og DANE korrekt for at kunne modtage mails fra Exchange Online ved hjælp af disse standarder.

### <a name="how-does-dnssec-relate-to-dane"></a>Hvordan er DNSSEC relateret til DANE?

DNSSEC tilføjer et lag af tillid til DNS-opløsningen ved at udnytte den offentlige nøgleinfrastruktur for at sikre, at de poster, der returneres som svar på en DNS-forespørgsel, er ægte. DANE sikrer, at den modtagende mailserver er den legitime og forventede mailserver til den autentiske MX-post. 

### <a name="what-is-the-difference-between-mta-sts-and-dane-for-smtp"></a>Hvad er forskellen mellem MTA-STS og DANE for SMTP?

DANE og MTA-STS tjener det samme formål, men DANE kræver DNSSEC til DNS-godkendelse, mens MTA-STS afhænger af nøglecertifikater. 

### <a name="why-isnt-opportunistic-tls-sufficient"></a>Hvorfor er Opportunistic TLS ikke tilstrækkelig?

Opportunistic TLS krypterer kommunikationen mellem to slutpunkter, hvis begge er enige om at understøtte det. Men selvom TLS krypterer overførslen, kan et domæne være efterlignet under DNS-opløsningen, så det peger på en ondsindet agents slutpunkt i stedet for det egentlige slutpunkt for domænet. Dette er et hul i mailsikkerhed, der løses ved at implementere MTA-STS og/eller SMTP DANE med DNSSEC.  

### <a name="why-isnt-dnssec-sufficient"></a>Hvorfor er DNSSEC ikke tilstrækkelig?

DNSSEC er ikke fuldt tænkelige over for Man-in-the-Middle-angreb og nedgradering (fra TLS til klar tekst)-angreb til mailflowscenarier. Tilføjelsen af MTA-STS og DANE sammen med DNSSEC giver en omfattende sikkerhedsmetode til at modarbejde både MITM og nedgradere angreb.

## <a name="additional-links"></a>Flere links 

[Find og løs problemer efter at have tilføjet dit domæne eller DNS-poster](/microsoft-365/admin/get-help-with-domains/find-and-fix-issues)

[Oversigt over DNSSEC-| Microsoft Docs ](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj200221(v=ws.11))

[Brug DMARC til at validere mail, konfigurationstrin – Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)

[Sådan bruger du DKIM til mail i dit brugerdefinerede domæne – Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)

[Sådan forhindrer SPF (Sender Policy Framework) spoofing - Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing)

[Exchange Online transportnyheder fra Microsoft Ignite 2020 – Microsoft Tech Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-online-transport-news-from-microsoft-ignite-2020/ba-p/1687699)

[rfc8461 (ietf.org)](https://datatracker.ietf.org/doc/html/rfc8461)