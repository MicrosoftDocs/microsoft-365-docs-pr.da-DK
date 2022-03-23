---
title: Sådan forhindrer SPF (Sender Policy Framework) spoofing
f1.keywords:
- CSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 12/15/2016
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 3aff33c5-1416-4867-a23b-e0c0c5b4d2be
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Få mere at Microsoft 365, hvordan du bruger SPF (Sender Policy Framework) TXT-posten i DNS til at sikre, at destinationens mailsystemer har tillid til meddelelser, der sendes fra dit brugerdefinerede domæne.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 76bc783dc624487b438ca41dcd9fc38bd9bce911
ms.sourcegitcommit: 07405a81513d1c63071a128b9d5070d3a3bfe1cd
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63587289"
---
# <a name="how-microsoft-365-uses-sender-policy-framework-spf-to-prevent-spoofing"></a>Sådan Microsoft 365 SPF (Sender Policy Framework) til at forhindre spoofing

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

 **Oversigt:** I denne artikel beskrives, hvordan Microsoft 365 bruger SPF (Sender Policy Framework) TXT-posten i DNS til at sikre, at destinationens mailsystemer har tillid til meddelelser, der sendes fra dit brugerdefinerede domæne. Dette gælder for udgående mails, der sendes Microsoft 365. Meddelelser, der Microsoft 365 til en modtager inden Microsoft 365, passerer altid SPF.

En SPF TXT-post er en DNS-post, der er med til at forhindre spoofing og phishing ved at bekræfte det domænenavn, som mails sendes fra. SPF validerer oprindelsen af mails ved at bekræfte IP-adressen på afsenderen over for den retmæssige ejer af det afsendende domæne.

> [!NOTE]
> SPF-posttyper blev frarådet af Internet Engineering Task Force (IETF) i 2014. I stedet skal du sikre dig, at du bruger TXT-poster i DNS til at publicere dine SPF-oplysninger. I resten af denne artikel bruges udtrykket SPF TXT-post for at skabe klarhed.

Domæneadministratorer publicerer SPF-oplysninger i TXT-poster i DNS. SPF-oplysningerne identificerer autoriserede udgående mailservere. Destinationens mailsystemer bekræfter, at meddelelser stammer fra autoriserede udgående mailservere. Hvis du allerede kender SPF, eller hvis du har en simpel installation og blot har brug for at vide, hvad du skal medtage i din SPF TXT-post i DNS til Microsoft 365, kan du gå til Konfigurer SPF i Microsoft 365 for at forhindre [spoofing](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Hvis du ikke har en installation, der er fuldt hostet i Microsoft 365, eller du vil have flere oplysninger om, hvordan SPF fungerer, eller hvordan du foretager fejlfinding af SPF til Microsoft 365, kan du læse videre.

> [!NOTE]
> Tidligere skulle du føje en anden SPF TXT-post til dit brugerdefinerede domæne, hvis du også brugte SharePoint Online. Dette er ikke længere påkrævet. Denne ændring bør reducere risikoen for, at SharePoint Onlinemeddelelser ender i mappen Uønsket mail. Du behøver ikke at foretage ændringer med det samme, men hvis du modtager fejlen "for mange opslag", skal du ændre SPF TXT-posten som beskrevet i Konfigurer SPF i Microsoft 365 for at forhindre [spoofing](set-up-spf-in-office-365-to-help-prevent-spoofing.md).

## <a name="how-spf-works-to-prevent-spoofing-and-phishing-in-microsoft-365"></a>Sådan fungerer SPF til at forhindre spoofing og phishing i Microsoft 365
<a name="HowSPFWorks"> </a>

SPF afgør, hvorvidt en afsender har tilladelse til at sende på vegne af et domæne. Hvis afsenderen ikke har tilladelse til at gøre dette, så bestemmer den spampolitik, der er konfigureret på den pågældende server, hvad der skal gøre med meddelelsen, hvis SPF-kontrollerne mislykkes på den modtagende server.

Hver SPF TXT-post består af tre dele: Erklæringen om, at det er en SPF TXT-post, de IP-adresser, der har tilladelse til at sende mails fra dit domæne, og de eksterne domæner, der kan sende på dit domænes vegne, samt en håndhævelsesregel. Du skal bruge alle tre i en gyldig SPF TXT-post. I denne artikel beskrives det, hvordan du danner din SPF TXT-post, og du får de bedste fremgangsmåder til at arbejde med tjenesterne Microsoft 365. Links til vejledning i at arbejde med din domæneregistrator til at publicere din post til DNS findes også.

### <a name="spf-basics-ip-addresses-allowed-to-send-from-your-custom-domain"></a>Grundlæggende om SPF: IP-adresser, der er tilladt at sende fra dit brugerdefinerede domæne
<a name="SPFBasicsIPaddresses"> </a>

Se nærmere på den grundlæggende syntaks for en SPF-regel:

v=spf1 \<IP\> \<enforcement rule\>

Lad os f.eks. sige, at følgende SPF-regel findes for contoso.com:

v=spf1 \<IP address #1\> \<IP address #2\> \<IP address #3\> \<enforcement rule\>

I dette eksempel instruerer SPF-reglen den modtagende mailserver til kun at acceptere mails fra disse IP-adresser for contoso.com:

- IP-adresse #1

- IP-adresse #2

- IP-adresse #3

Denne SPF-regel fortæller den modtagende mailserver, at hvis en meddelelse kommer fra contoso.com, men ikke fra en af disse tre IP-adresser, skal den modtagende server anvende håndhævelsesreglen på meddelelsen. Håndhævelsesreglen er normalt en af disse indstillinger:

- **Hard fail.** Markér meddelelsen med "mislykket" i meddelelseskonvoluten, og følg derefter den modtagende servers konfigurerede spampolitik for denne type meddelelse.

- **Blød fejl.** Markér meddelelsen med "ikke-blød" i meddelelseskonvoluten. Typisk er mailservere konfigureret til at levere disse meddelelser alligevel. De fleste slutbrugere kan ikke se dette mærke.

- **Neutral.** Gør intet, dvs. Markér ikke konvolutten. Dette er normalt reserveret til testformål og bruges sjældent.

Følgende eksempler viser, hvordan SPF fungerer i forskellige situationer. I disse eksempler er contoso.com afsenderen, og woodgrovebank.com modtageren.

### <a name="example-1-email-authentication-of-a-message-sent-directly-from-sender-to-receiver"></a>Eksempel 1: Mailgodkendelse for en meddelelse, der sendes direkte fra afsender til modtager
<a name="spfExample1"> </a>

SPF fungerer bedst, når stien fra afsender til modtager er direkte, f.eks.:

![Diagram, der viser, hvordan SPF godkender mail, når den sendes direkte fra server til server.](../../media/835c20a7-ed4c-49c4-91fe-b8ebb3e452a1.jpg)

Når woodgrovebank.com modtager meddelelsen, og IP-adresse #1 er i SPF TXT-posten for contoso.com, videregiver meddelelsen SPF-kontrollerne og godkendes.

### <a name="example-2-spoofed-sender-address-fails-the-spf-check"></a>Eksempel 2: Spoof afsenderadressen mislykkes SPF-kontrol
<a name="spfExample2"> </a>

Antag, at en phisher finder en måde at efterligne contoso.com:

![Diagram, der viser, hvordan SPF godkender mail, når den sendes fra en efterlignet server.](../../media/235dac3d-cdc5-466e-86e0-37b5979de198.jpg)

Da IP-adresse #12 ikke er i contoso.com's SPF TXT-post, mislykkes SPF-markeringen, og modtageren kan vælge at markere den som spam.

### <a name="example-3-spf-and-forwarded-messages"></a>Eksempel 3: SPF og videresendte meddelelser
<a name="spfExample3"> </a>

En ulempe ved SPF er, at det ikke virker, når en mail er blevet videresendt. Antag f.eks., at woodgrovebank.com har konfigureret en regel for videresendelse til at sende alle mails til en outlook.com konto:

![Diagram, der viser, hvordan SPF ikke kan godkende mail, når meddelelsen videresendes.](../../media/6e92acd6-463e-4a1b-8327-fb1cf861f356.jpg)

Meddelelsen blev oprindeligt videregivet SPF-kontrol på woodgrovebank.com men SPF-kontrol mislykkes på outlook.com, fordi IP #25 ikke er i contoso.coms SPF TXT-post. Outlook.com kan derefter markere meddelelsen som spam. Du kan løse dette problem ved at bruge SPF sammen med andre mailgodkendelsesmetoder som DKIM og DMARC.

### <a name="spf-basics-including-third-party-domains-that-can-send-mail-on-behalf-of-your-domain"></a>Grundlæggende om SPF: Herunder tredjepartsdomæner, der kan sende mails på vegne af dit domæne
<a name="SPFBasicsIncludes"> </a>

Ud over IP-adresser kan du også konfigurere SPF TXT-posten til at medtage domæner som afsendere. Disse føjes til SPF TXT-posten som "include"-sætninger. Det kan contoso.com, at du vil medtage alle IP-adresserne på mailserverne fra contoso.net og contoso.org som den også ejer. For at gøre dette contoso.com en SPF TXT-post, der ser sådan ud:

```text
v=spf1 include:contoso.net include:contoso.org -all
```

Når den modtagende server ser denne post i DNS, udfører den også et DNS-opslag på SPF TXT-posten for contoso.net og derefter for contoso.org. Hvis der registreres en ekstra include-sætning i posterne for contoso.net eller contoso.org, følger den også disse. For at forhindre Denial of Service-angreb er det maksimale antal DNS-opslag for en enkelt mail 10. Hver medtag-sætning repræsenterer et ekstra DNS-opslag. Hvis en meddelelse overskrider grænsen på 10, mislykkes SPF-meddelelsen. Når en meddelelse når denne grænse, afhængigt af hvordan den modtagende server er konfigureret, får afsenderen muligvis en meddelelse om, at meddelelsen genererede "for mange opslag", eller at "det maksimale hopantal for meddelelsen er overskredet" (hvilket kan ske, når opslagsløkken overstiger DNS-timeout). Du kan finde tip til, hvordan du undgår [dette, under Fejlfinding: Bedste fremgangsmåder for SPF Microsoft 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot).

## <a name="requirements-for-your-spf-txt-record-and-microsoft-365"></a>Krav til SPF TXT-posten og -Microsoft 365
<a name="SPFReqsinO365"> </a>

Hvis du konfigurerer mail, da du konfigurerede Microsoft 365, har du allerede oprettet en SPF TXT-post, der identificerer Microsoft-meddelelsesserverne som en legitim mailkilde for dit domæne. Denne post ser sandsynligvis sådan ud:

```text
v=spf1 include:spf.protection.outlook.com -all
```

Hvis du er en fuldt hostet kunde, dvs. du ikke har nogen lokale mailservere, der sender udgående mail, er dette den eneste SPF TXT-post, du skal publicere til Office 365.

Hvis du har en hybridinstallation (dvs. du har nogle lokale postkasser og nogle, der er hostet i Microsoft 365), eller hvis du er enkeltstående Exchange Online Protection (EOP)-kunde (dvs. din organisation bruger EOP til at beskytte dine lokale postkasser), skal du tilføje den udgående IP-adresse for hver af dine lokale edge-mailservere til SPF TXT-posten i DNS.

## <a name="form-your-spf-txt-record-for-microsoft-365"></a>Form din SPF TXT-post for Microsoft 365
<a name="FormYourSPF"> </a>

Brug syntaksoplysningerne i denne artikel til at danne SPF TXT-posten for dit brugerdefinerede domæne. Selvom der er andre syntaksindstillinger, der ikke er nævnt her, er disse de mest almindeligt brugte indstillinger. Når du har oprettet din post, skal du opdatere posten hos din domæneregistrator.

Du kan finde oplysninger om de domæner, du skal medtage til Microsoft 365, under Eksterne [DNS-poster, der kræves til SPF](../../enterprise/external-domain-name-system-records.md). Brug den [trinvise vejledning til opdatering af](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md#add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online) SPF-poster (TXT) for din domæneregistrator.

### <a name="spf-txt-record-syntax-for-microsoft-365"></a>Syntaks for SPF TXT-post for Microsoft 365
<a name="SPFSyntaxO365"> </a>

En typisk SPF TXT-post til Microsoft 365 har følgende syntaks:

```text
v=spf1 [<ip4>|<ip6>:<IP address>] [include:<domain name>] <enforcement rule>
```

Eksempel:

```text
v=spf1 ip4:192.168.0.1 ip4:192.168.0.2 include:spf.protection.outlook.com -all
```

hvor:

- **v=spf1** er påkrævet. Dette definerer TXT-posten som en SPF TXT-post.

- **ip4** angiver, at du bruger IP version 4-adresser. **ip6** angiver, at du bruger IP version 6-adresser. Hvis du bruger IPv6 IP-adresser, skal **du erstatte ip4** med **ip6** i eksemplerne i denne artikel. Du kan også angive IP-adresseintervaller ved hjælp af CIDR-notation, f.eks **. ip4:192.168.0.1/26**.

- _IP-adresse_ er den IP-adresse, du vil føje til SPF TXT-posten. Dette er normalt IP-adressen på organisationens server til udgående mail. Du kan oprette en liste over flere udgående mailservere. Du kan finde flere oplysninger [i Eksempel: SPF TXT-post for flere udgående lokale mailservere og Microsoft 365](how-office-365-uses-spf-to-prevent-spoofing.md#ExampleSPFMultipleMailServerO365).

- _domænenavn er_ det domæne, du vil tilføje som legitim afsender. Du kan finde en liste over domænenavne, du skal medtage Microsoft 365, under [Eksterne DNS-poster, der kræves til SPF](../../enterprise/external-domain-name-system-records.md).

- Håndhævelsesreglen er som regel et af følgende:

  - -all

    Angiver, at der ikke kan udføres fejl. Hvis du kender alle de autoriserede IP-adresser for dit domæne, kan du få dem vist i SPF TXT-posten og bruge kvalifikatoren -all (hard fail). Hvis du kun bruger SPF, dvs. du ikke bruger DMARC eller DKIM, skal du bruge -alle-kvalifikatoren. Vi anbefaler, at du altid bruger denne kvalifikator.

  - ~all

    Angiver bløde fejl. Hvis du ikke er sikker på, at du har den komplette liste over IP-adresser, skal du bruge kvalifikatoren ~all (soft fail). Hvis du bruger DMARC med p=karantæne eller p=afvis, kan du bruge ~all. Ellers skal du bruge -all.

  - ?all

    Angiver neutral. Dette bruges, når du tester SPF. Vi anbefaler ikke, at du bruger denne kvalifikator i din live-installation.

### <a name="example-spf-txt-record-to-use-when-all-of-your-mail-is-sent-by-microsoft-365"></a>Eksempel: SPF TXT-post til brug, når alle dine mails sendes af Microsoft 365
<a name="ExampleSPFNoSP"> </a>

Hvis alle dine mails sendes af en Microsoft 365, skal du bruge dette i din SPF TXT-post:

```text
v=spf1 include:spf.protection.outlook.com -all
```

### <a name="example-spf-txt-record-for-a-hybrid-scenario-with-one-on-premises-exchange-server-and-microsoft-365"></a>Eksempel: SPF TXT-post til et hybridscenarie med en lokal Exchange Server og Microsoft 365
<a name="ExampleSPFHybridOneExchangeServer"> </a>

Hvis IP-adressen for din lokale Exchange Server i et hybridmiljø er 192.168.0.1, skal du oprette SPF TXT-posten som følger for at indstille SPF-håndhævelsesreglen til ikke at blive håndhævet:

```text
v=spf1 ip4:192.168.0.1 include:spf.protection.outlook.com -all
```

### <a name="example-spf-txt-record-for-multiple-outbound-on-premises-mail-servers-and-microsoft-365"></a>Eksempel: SPF TXT-post for flere udgående lokale mailservere og Microsoft 365
<a name="ExampleSPFMultipleMailServerO365"> </a>

Hvis du har flere udgående mailservere, skal du medtage IP-adressen for hver mailserver i SPF TXT-posten og adskille hver IP-adresse med et mellemrum efterfulgt af en "ip4:"-sætning. Eksempel:

```text
v=spf1 ip4:192.168.0.1 ip4:192.168.0.2 ip4:192.168.0.3 include:spf.protection.outlook.com -all
```

## <a name="next-steps-set-up-spf-for-microsoft-365"></a>Næste trin: Konfigurer SPF til Microsoft 365
<a name="SPFNextSteps"> </a>

Når du har formuleret SPF TXT-posten, skal du følge trinnene i Konfigurer SPF i Microsoft 365 for at forhindre [spoofing](set-up-spf-in-office-365-to-help-prevent-spoofing.md) for at føje den til dit domæne.

Selvom SPF er designet til at forhindre spoofing, men der er spoofing-teknikker, som SPF ikke kan beskytte sig mod. For at beskytte dig mod disse, når du har konfigureret SPF, skal du også konfigurere DKIM og DMARC til Microsoft 365. For at komme i gang skal [du se Brug DKIM til at validere udgående mails, der sendes fra dit brugerdefinerede domæne Microsoft 365](use-dkim-to-validate-outbound-email.md). Læs derefter Brug [DMARC til at validere mail i Microsoft 365](use-dmarc-to-validate-email.md).

## <a name="troubleshooting-best-practices-for-spf-in-microsoft-365"></a>Fejlfinding: Bedste fremgangsmåder for SPF i Microsoft 365
<a name="SPFTroubleshoot"> </a>

Du kan kun oprette én SPF TXT-post for dit brugerdefinerede domæne. Oprettelse af flere poster medfører en omvendt problem, og SPF mislykkes. Du kan undgå dette ved at oprette separate poster for hvert underdomæne. Du kan f.eks. oprette én post for contoso.com og en anden post til bulkmail.contoso.com.

Hvis en mail forårsager mere end 10 DNS-opslag, før den leveres, reagerer den modtagende mailserver med en permanent fejl, også kaldet en  _permerror_, og får meddelelsen til at mislykke SPF-kontrol. Den modtagende server kan også svare med en rapport om manglende levering (NDR), der indeholder en fejl som følgende:

- Meddelelsen oversteg hopantal.

- Meddelelsen kræver for mange opslag.

## <a name="avoiding-the-too-many-lookups-error-when-you-use-third-party-domains-with-microsoft-365"></a>Undgår fejlen "for mange opslag", når du bruger tredjepartsdomæner med Microsoft 365
<a name="SPFTroubleshoot"> </a>

Nogle SPF TXT-poster for tredjepartsdomæner dirigerer den modtagende server til at udføre et stort antal DNS-opslag. På tidspunktet for denne skrivning indeholder Salesforce.com f.eks. 5 udsagn i sin post:

```text
v=spf1 include:_spf.google.com
include:_spfblock.salesforce.com
include:_qa.salesforce.com
include:_spfblock1.salesforce.com
include:spf.mandrillapp.com mx ~all
```

Du kan undgå fejlen ved at implementere en politik, hvor alle, der f.eks. sender massemails, skal bruge et underdomæne specifikt til dette formål. Du kan derefter definere en anden SPF TXT-post for det underdomæne, der indeholder massemailen.

 I nogle tilfælde, f.eks. salesforce.com-eksemplet, skal du bruge domænet i din SPF TXT-post, men i andre tilfælde kan tredjeparten allerede have oprettet et underdomæne, som du kan bruge til dette formål. Eksempelvis har exacttarget.com oprettet et underdomæne, du skal bruge til din SPF TXT-post:

```text
cust-spf.exacttarget.com
```

Når du medtager tredjepartsdomæner i din SPF TXT-post, skal du bekræfte over for tredjeparten, hvilket domæne eller underdomæne du skal bruge, for at undgå at løbe ind i grænsen på 10 opslag.

## <a name="how-to-view-your-current-spf-txt-record-and-determine-the-number-of-lookups-that-it-requires"></a>Sådan får du vist din aktuelle SPF TXT-post og bestemmer det antal opslag, der kræves
<a name="SPFTroubleshoot"> </a>

Du kan bruge nslookup til at få vist dine DNS-poster, herunder din SPF TXT-post. Der findes en række gratis onlineværktøjer, som du kan bruge til at få vist indholdet af din SPF TXT-post. Ved at kigge på din SPF TXT-post og følge kæden af medtag sætninger og omdirigeringer kan du bestemme, hvor mange DNS-opslag posten kræver. Nogle onlineværktøjer kan endda tælle og vise disse opslag for dig. Hvis du holder styr på dette antal, kan det forhindre meddelelser, der sendes fra din organisation, i at udløse en permanent fejl, kaldet en perm-fejl, fra den modtagende server.

## <a name="for-more-information"></a>Du kan finde flere oplysninger
<a name="SPFTroubleshoot"> </a>

Har du brug for hjælp til at tilføje SPF TXT-posten? Læs artiklen Oprette [DNS-poster for Microsoft 365 DNS-hostingudbyder for at](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md#add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online) få detaljerede oplysninger om brug af Sender Policy Framework med dit brugerdefinerede domæne Microsoft 365. [Antispam-brevhoveder indeholder de syntaks- og overskriftsfelter](anti-spam-message-headers.md), der bruges Microsoft 365 til SPF-kontroller.
