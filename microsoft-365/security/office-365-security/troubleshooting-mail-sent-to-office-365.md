---
title: Fejlfinding af mails, der sendes Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: troubleshooting
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: f4caa4e1-e414-4b21-8822-31c08064c059
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Denne artikel indeholder fejlfindingsoplysninger til problemer med at sende mails til indbakker Microsoft 365 & bedste fremgangsmåder for masseforsendelser til Microsoft 365 kunder.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f5fe128989b66f110899e6af08180e830319b739
ms.sourcegitcommit: 07405a81513d1c63071a128b9d5070d3a3bfe1cd
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63587323"
---
# <a name="troubleshooting-mail-sent-to-microsoft-365"></a>Fejlfinding af mails, der sendes Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)

Denne artikel indeholder fejlfindingsoplysninger til afsendere, der oplever problemer, når de forsøger at sende mails til indbakker i Microsoft 365 og bedste fremgangsmåder for masseforsendelse til kunder.

## <a name="are-you-managing-your-ip-and-domains-sending-reputation"></a>Administrerer du IP og domænets afsendelses ry?

EOP-filtreringsteknologier er designet til at levere beskyttelse mod uønsket post til Microsoft 365 og andre Microsoft-produkter som f.eks. Exchange Server. Vi bruger også SPF, DKIM og DMARC. mailgodkendelsesteknologier, der hjælper med at løse problemet med spoofing og phishing ved at bekræfte, at det domæne, der sender mailen, er autoriseret til at gøre dette. EOP-filtrering påvirkes af mange faktorer i forbindelse med afsender-IP, domæne, godkendelse, listenøjagtighed, klagesatser, indhold og meget mere. Af disse faktorer er en af de vigtigste faktorer i forbindelse med at påvirke en afsenders ry og muligheden for at levere mail, at klageprocenten for uønsket mail er dennes.

## <a name="are-you-sending-email-from-new-ip-addresses"></a>Sender du mail fra nye IP-adresser?

IP-adresser, der ikke tidligere er brugt til at sende mails, har typisk ikke noget ry opbygget i vores systemer. Det betyder, at mails fra nye IP-adresser har større sandsynlighed for at opleve problemer med levering. Når IP har opbygget et ry for ikke at sende spam, vil EOP typisk give en bedre oplevelse med levering af mail.

Nye IP'er, der tilføjes for domæner, der er godkendt under eksisterende SPF-poster, oplever typisk den ekstra fordel ved at nedarve noget af domænets afsendelses ry. Hvis dit domæne har et godt afsendelses ry, kan nye IP'er få tiden til at gå hurtigere. En ny IP kan forvente at blive helt færdig inden for et par uger eller tidligere afhængigt af mængden, nøjagtigheden af lister og klagesatserne for uønsket mail.

## <a name="confirm-that-your-dns-is-set-up-correctly"></a>Kontrollér, at din DNS er konfigureret korrekt

Hvis du vil have vejledning i, hvordan du opretter og vedligeholder DNS-poster, herunder den MX-post, der kræves til mailrouting, skal du kontakte din DNS-udbyder.

## <a name="ensure-that-you-do-not-advertise-yourself-as-a-non-routable-ip"></a>Sørg for, at du ikke annoncerer dig selv som en IP, der ikke kan rouses

Vi accepterer muligvis ikke mail fra afsendere, der ikke har et omvendt DNS-opslag. I nogle tilfælde annoncerer legitime afsendere sig forkert som en IP, der ikke kantribues via internettet, når de forsøger at åbne en forbindelse til EOP. IP-adresser, der er reserveret til private (ikke-rute) netværk omfatter:

- 192.168.0.0/16 (eller 192.168.0.0 - 192.168.255.255)
- 10.0.0.0/8 (eller 10.0.0.0 - 10.255.255.255)
- 172.16.0.0/11 (eller 172.16.0.0 - 172.31.255.255)

## <a name="you-received-a-non-delivery-report-ndr-when-sending-email-to-a-user-in-office-365"></a>Du har modtaget en rapport om manglende levering, når du sender en mail til en bruger Office 365

Nogle problemer med levering er resultatet af, at afsenderens IP-adresse blokeres af Microsoft, eller fordi brugerkontoen er identificeret som spærret afsender på grund af tidligere spamaktivitet. Hvis du mener, at du har modtaget en NDR ved en fejl, skal du først følge eventuelle instruktioner i NDR-meddelelsen for at løse problemet.

Du kan finde flere oplysninger om den fejlmeddelelse, du har modtaget, på listen over fejlkoder i [Mailrapporter om manglende levering Exchange Online](/exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

 Hvis du f.eks. modtager følgende NDR, angiver den, at den afsendende IP-adresse blev blokeret af Microsoft:

 `550 5.7.606-649 Access denied, banned sending IP [x.x.x.x]; To request removal from this list please visit https://sender.office.com/ and follow the directions.`

Hvis du vil anmode om at blive fjernet fra denne liste, [kan du Bruge fralist-portalen til at fjerne dig selv fra listen over blokerede afsendere](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md).

## <a name="my-email-landed-in-the-recipients-junk-email-folder"></a>Min mail er landet i modtagerens mappe med uønsket mail

Hvis en meddelelse fejlagtigt er blevet identificeret som spam af EOP, kan du samarbejde med modtageren om at sende denne falske positive meddelelse til Microsoft Spam Analysis Team, som vil evaluere og analysere meddelelsen. Få mere at vide under [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="traffic-from-my-ip-address-is-throttled-by-eop"></a>Trafik fra min IP-adresse er begrænset af EOP

Hvis du modtager en NDR fra EOP, der angiver, at din IP-adresse bliver begrænser af EOP, f.eks.:

 `host xxxx.outlook.com [x.x.x.x]: 451 4.7.550 Access denied, please try again later`

Du har modtaget NDR, fordi mistænkelig aktivitet er blevet registreret fra IP-adressen, og den er blevet midlertidigt begrænset, mens den evalueres yderligere. Hvis mistanken fjernes gennem evalueringen, ophæves denne begrænsning snart.

## <a name="i-cant-receive-email-from-senders-in-microsoft-365"></a>Jeg kan ikke modtage mails fra afsendere i Microsoft 365

 For at kunne modtage meddelelser fra vores brugere skal du sikre dig, at dit netværk tillader forbindelser fra de IP-adresser, som EOP bruger i vores datacentre. Du kan finde flere oplysninger [Exchange Online Protection IP-adresser](../../enterprise/urls-and-ip-address-ranges.md).

## <a name="best-practices-for-bulk-emailing-to-microsoft-365-users"></a>Bedste fremgangsmåder for massemails til Microsoft 365 brugere

Hvis du ofte gennemfører massemailkampagner for Microsoft 365-brugere og ønsker at sikre, at dine mails ankommer sikkert og rettidigt, skal du følge tipene i dette afsnit.

### <a name="ensure-that-the-from-name-reflects-who-is-sending-the-message"></a>Sørg for, at Fra-navnet afspejler, hvem der sender meddelelsen

Emnet bør være en kort oversigt over, hvad meddelelsen handler om, og meddelelsesteksten skal tydeligt og entydigt angive, hvad tilbuddet, tjenesten eller produktet handler om. Eksempel:

Korrekt:

> Fra: marketing@shoppershandbag.com <br> Emne: Opdateret katalog for juletiden!

Forkert:

> Fra: someone@outlook.com <br> Emne: Kataloger

Jo nemmere du gør det for folk at vide, hvem du er, og hvad du laver, jo mindre besvær har du med at levere gennem de fleste spamfiltre.

### <a name="always-include-an-unsubscribe-option-in-campaign-emails"></a>Medtag altid en frameldingsindstilling i kampagnemails

Marketingmails, især nyhedsbreve, bør altid indeholde en metode til at give dit abonnement på fremtidige mails. Eksempel:

 `This email was sent to example@contoso.com by sender@fabrikam.com.`

 `Update Profile/Email Address | Instant removal with SafeUnsubscribe&trade; | Privacy Policy`

Nogle afsendere inkluderer denne indstilling ved at kræve, at modtagerne skal sende en mail til et bestemt alias med "Frameld" i emnelinjen. Dette er ikke at foretrække frem for eksemplet med et enkelt klik ovenfor. Hvis du vælger at kræve, at modtagerne skal sende en mail, skal du sikre dig, at alle de påkrævede felter er udfyldt på forhånd, når de klikker på linket.

### <a name="use-the-double-opt-in-option-for-marketing-email-or-newsletter-registration"></a>Brug den dobbelte tilmeldingsmulighed til registrering af marketingmail eller nyhedsbreve

Denne branche bedste fremgangsmåde anbefales, hvis din virksomhed kræver eller opfordrer brugerne til at registrere deres kontaktoplysninger for at få adgang til dit produkt eller dine tjenester. Nogle virksomheder gør det til en praksis automatisk at tilmelde deres brugere til marketingmails eller nyhedsbreve under registreringsprocessen, men det betragtes som en tvivlsomme marketingpraksis i en verden af mailfiltrering.

Under registreringsprocessen er afkrydsningsfeltet "Ja, send mig dit nyhedsbrev" eller "Ja, send mig specialtilbud" markeret som standard, og brugere, der ikke er særligt opmærksomme på dette, kan ved en fejl tilmelde sig marketingmails eller nyhedsbreve, som de ikke vil modtage.

 Microsoft anbefaler den dobbelte tilmeldingsmulighed i stedet, hvilket betyder, at afkrydsningsfeltet for marketingmails eller nyhedsbreve som standard ikke er markeret. Når registreringsformularen er blevet sendt, sendes der desuden en bekræftelsesmail til brugeren med en URL-adresse, der gør det muligt for brugeren at bekræfte sin beslutning om at modtage marketingmails.

 Dette er med til at sikre, at kun de brugere, der vil modtage marketingmails, bliver tilmeldt mails, hvilket efterfølgende rydder det afsendende firma fra enhver tvivlbar mailmarketingpraksis.

### <a name="ensure-that-email-message-content-is-transparent-and-traceable"></a>Sørg for, at mailindhold er gennemsigtigt og sporbart

Lige så vigtigt som den måde, som mails sendes på, er det indhold, de indeholder. Når du opretter mailindhold, skal du bruge følgende bedste fremgangsmåder til at sikre, at dine mails ikke markeres af mailfiltreringstjenester:

- Når mailen anmoder om, at modtagerne føjer afsenderen til adressekartoteket, skal det tydeligt angive, at en sådan handling ikke er en garanti for levering.

- Omdirigeringer, der medtages i meddelelsens brødtekst, skal være ens og ensartede og ikke flere og varierede. En omdirigering i denne kontekst er alt, der peger væk fra meddelelsen, f.eks links og dokumenter. Hvis du har mange links til annoncering eller Frameld eller Opdater profillinkene, bør de alle pege på det samme domæne. Eksempel:

  Korrekt (alle domæner er ens):

  `unsubscribe.bulkmailer.com`

  `profile.bulkmailer.com`

  `options.bulkmailer.com`

  Forkert (alle domæner er forskellige):

  `unsubscribe.bulkmailer.com`

  `profile.excite.com`

  `options.yahoo.com`

- Undgå indhold med store billeder og vedhæftede filer eller meddelelser, der udelukkende består af et billede.

- Dine offentlige oplysninger eller P3P-indstillinger skal tydeligt angive tilstedeværelsen af registrerings pixel (webfejl eller beacons).

### <a name="remove-incorrect-email-aliases-from-your-databases"></a>Fjern forkerte mailaliasser fra dine databaser

Ethvert mailalias i din database, der opretter en tilbagevisning, er unødvendigt og bringer dine udgående mails i fare, så du kan granske dem yderligere ved hjælp af mailfiltreringstjenester. Sørg for, at din maildatabase er opdateret.