---
title: Fejlfinding af mails, der er sendt til Microsoft 365
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
description: Denne artikel indeholder fejlfindingsoplysninger for problemer med at sende mails til indbakker i Microsoft 365 & bedste praksis for masseforsendelse til Microsoft 365 kunder.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 37703ccb0ffb37163033bb2fdca24566a33bb275
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128428"
---
# <a name="troubleshooting-mail-sent-to-microsoft-365"></a>Fejlfinding af mails, der er sendt til Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)

Denne artikel indeholder fejlfindingsoplysninger for afsendere, der oplever problemer, når de forsøger at sende mails til indbakker i Microsoft 365 og bedste praksis for masseforsendelse til kunder.

## <a name="are-you-managing-your-ip-and-domains-sending-reputation"></a>Administrerer du dit IP- og domænes sendeomdømme?

EOP-filtreringsteknologier er udviklet til at sikre beskyttelse mod spam for Microsoft 365 og andre Microsoft-produkter, f.eks. Exchange Server. Vi bruger også SPF, DKIM og DMARC; teknologier til mailgodkendelse, der hjælper med at løse problemet med spoofing og phishing ved at bekræfte, at domænet, der sender mailen, er autoriseret til at gøre det. EOP-filtrering påvirkes af mange faktorer, der er relateret til den afsendende IP, domæne, godkendelse, listenøjagtighed, klagesatser, indhold m.m. Af disse er en af de vigtigste faktorer i at drive en afsenders omdømme ned og deres evne til at levere e-mail deres klagerate for uønsket mail.

## <a name="are-you-sending-email-from-new-ip-addresses"></a>Sender du mail fra nye IP-adresser?

IP-adresser, der ikke tidligere er brugt til at sende e-mails, har typisk ikke noget omdømme bygget op i vores systemer. Som et resultat heraf er der større sandsynlighed for, at mails fra nye IP-adresser oplever leveringsproblemer. Når IP'en har opbygget et ry for ikke at sende spam, vil EOP typisk give en bedre mailleveringsoplevelse.

Nye IP-adresser, der tilføjes for domæner, der er godkendt i henhold til eksisterende SPF-poster, oplever typisk den ekstra fordel ved at arve noget af domænets sendeomdømme. Hvis dit domæne har et godt sendeomdømme, kan nye IP-adresser opleve en hurtigere opgangstid. En ny IP kan forvente at være fuldt ramped inden for et par uger eller tidligere afhængigt af volumen, listenøjagtighed, og junk email klage satser.

## <a name="confirm-that-your-dns-is-set-up-correctly"></a>Bekræft, at din DNS er konfigureret korrekt

Hvis du vil have instruktioner om, hvordan du opretter og vedligeholder DNS-poster, herunder den MX-post, der kræves til postdistribution, skal du kontakte din DNS-udbyder.

## <a name="ensure-that-you-do-not-advertise-yourself-as-a-non-routable-ip"></a>Sørg for, at du ikke reklamerer for dig selv som en ip-adresse, der ikke kan distribueres

Vi accepterer muligvis ikke mail fra afsendere, der ikke udfører et omvendt DNS-opslag. I nogle tilfælde reklamerer legitime afsendere forkert som en IP-adresse, der ikke kan sendes via internettet, når de forsøger at åbne en forbindelse til EOP. IP-adresser, der er reserveret til private (ikke-routable) netværk omfatter:

- 192.168.0.0/16 (eller 192.168.0.0 - 192.168.255.255)
- 10.0.0.0/8 (eller 10.0.0.0 - 10.255.255.255)
- 172.16.0.0/11 (eller 172.16.0.0 - 172.31.255.255)

## <a name="you-received-a-non-delivery-report-ndr-when-sending-email-to-a-user-in-office-365"></a>Du har modtaget en rapport om manglende levering, da du sendte en mail til en bruger i Office 365

Nogle leveringsproblemer er resultatet af, at afsenderens IP-adresse blokeres af Microsoft, eller fordi brugerkontoen er identificeret som forbudt afsender på grund af tidligere spamaktivitet. Hvis du mener, at du har modtaget NDR ved en fejl, skal du først følge instruktionerne i NDR-meddelelsen for at løse problemet.

Du kan få flere oplysninger om den fejl, du har modtaget, på listen over fejlkoder i [rapporter om manglende levering af mail i Exchange Online](/exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

 Hvis du f.eks. modtager følgende NDR, angiver det, at den afsendende IP-adresse blev blokeret af Microsoft:

 `550 5.7.606-649 Access denied, banned sending IP [x.x.x.x]; To request removal from this list please visit https://sender.office.com/ and follow the directions.`

Hvis du vil anmode om fjernelse fra denne liste, kan du [bruge portalen til fraliste til at fjerne dig selv fra listen over blokerede afsendere](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md).

## <a name="my-email-landed-in-the-recipients-junk-email-folder"></a>Min mail er landet i modtagerens mappe med uønsket mail

Hvis en meddelelse fejlagtigt blev identificeret som spam af EOP, kan du samarbejde med modtageren om at sende denne falske positive meddelelse til Microsoft Spam Analysis Team, som skal evaluere og analysere meddelelsen. Du kan få flere oplysninger under [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="traffic-from-my-ip-address-is-throttled-by-eop"></a>Trafik fra min IP-adresse er begrænset af EOP

Hvis du modtager en NDR fra EOP, der angiver, at din IP-adresse begrænses af EOP, f.eks.:

 `host xxxx.outlook.com [x.x.x.x]: 451 4.7.550 Access denied, please try again later`

Du har modtaget NDR, fordi der er registreret mistænkelig aktivitet fra IP-adressen, og den er blevet midlertidigt begrænset, mens den evalueres yderligere. Hvis mistanken ryddes gennem evaluering, ophæves denne begrænsning om lidt.

## <a name="i-cant-receive-email-from-senders-in-microsoft-365"></a>Jeg kan ikke modtage mail fra afsendere i Microsoft 365

 For at modtage meddelelser fra vores brugere skal du sørge for, at dit netværk tillader forbindelser fra de IP-adresser, som EOP bruger i vores datacentre. Du kan få flere oplysninger [under Exchange Online Protection IP-adresser](../../enterprise/urls-and-ip-address-ranges.md).

## <a name="best-practices-for-bulk-emailing-to-microsoft-365-users"></a>Bedste praksis for massemailing til Microsoft 365 brugere

Hvis du ofte udfører massemailkampagner for at Microsoft 365 brugere og ønsker at sikre, at dine mails ankommer på en sikker og rettidig måde, skal du følge tipene i dette afsnit.

### <a name="ensure-that-the-from-name-reflects-who-is-sending-the-message"></a>Sørg for, at Fra-navnet afspejler, hvem der sender meddelelsen

Emnet bør være et kort resumé af, hvad meddelelsen handler om, og meddelelsens brødtekst skal tydeligt og kortfattet angive, hvad tilbuddet, servicen eller produktet handler om. Eksempel:

Korrekte:

> Fra: marketing@shoppershandbag.com <br> Om: Opdateret katalog for julesæsonen!

Forkert:

> Fra: someone@outlook.com <br> Emne: Kataloger

Jo lettere du gør det for folk at vide, hvem du er, og hvad du gør, jo mindre svært vil du have at levere gennem de fleste spam filtre.

### <a name="always-include-an-unsubscribe-option-in-campaign-emails"></a>Medtag altid en indstilling for opsigelse af abonnement i kampagnemails

Marketing e-mails, især nyhedsbreve, bør altid indeholde en måde at afmelde sig fra fremtidige e-mails. Eksempel:

 `This email was sent to example@contoso.com by sender@fabrikam.com.`

 `Update Profile/Email Address | Instant removal with SafeUnsubscribe&trade; | Privacy Policy`

Nogle afsendere inkluderer denne indstilling ved at kræve, at modtagerne sender en mail til et bestemt alias med "Opsig abonnement" i emnet. Dette er ikke at foretrække i forhold til eksemplet med et enkelt klik ovenfor. Hvis du vælger at kræve, at modtagerne sender en mail, skal du sørge for, at alle obligatoriske felter er udfyldt på forhånd, når de klikker på linket.

### <a name="use-the-double-opt-in-option-for-marketing-email-or-newsletter-registration"></a>Brug dobbelttilmeldingsmulighed til registrering af marketingmail eller nyhedsbrev

Denne bedste praksis i branchen anbefales, hvis din virksomhed kræver eller opfordrer brugerne til at registrere deres kontaktoplysninger for at få adgang til dit produkt eller dine tjenester. Nogle virksomheder gør det til en praksis automatisk at tilmelde deres brugere til markedsføring e-mails eller e-nyhedsbreve under registreringsprocessen, men dette betragtes som en tvivlsom markedsføring praksis i verden af e-mail filtrering.

Hvis afkrydsningsfeltet "Ja, send mig dit nyhedsbrev" eller "Ja, send mig særtilbud" under registreringen er markeret som standard, kan brugere, der ikke er opmærksomme, utilsigtet tilmelde sig marketingmails eller nyhedsbreve, som de ikke ønsker at modtage.

 Microsoft anbefaler i stedet indstillingen dobbelttilmelding, hvilket betyder, at afkrydsningsfeltet for marketingmails eller nyhedsbreve ikke er markeret som standard. Når registreringsformularen er indsendt, sendes der desuden en bekræftelsesmail til brugeren med en URL-adresse, der giver dem mulighed for at bekræfte deres beslutning om at modtage marketingmails.

 Dette hjælper med at sikre, at det kun er de brugere, der ønsker at modtage marketingmails, der er tilmeldt e-mails, der efterfølgende rydder det afsendende firma for tvivlsomme e-mail-marketingpraksisser.

### <a name="ensure-that-email-message-content-is-transparent-and-traceable"></a>Sørg for, at mailindholdet er gennemsigtigt og sporbart

Lige så vigtigt som den måde, mails sendes på, er det indhold, de indeholder. Når du opretter mailindhold, skal du bruge følgende bedste praksis til at sikre, at dine mails ikke markeres af mailfiltreringstjenester:

- Når modtagerne anmoder om, at afsenderen føjes til adressekartoteket i mailmeddelelsen, skal det tydeligt angives, at en sådan handling ikke er en garanti for levering.

- Omdirigeringer, der er inkluderet i meddelelsens brødtekst, skal være ens og ikke flere og varierede. En omdirigering i denne kontekst er alt, der peger væk fra meddelelsen, f.eks. links og dokumenter. Hvis du har mange reklamer eller opsig links eller opdater profillinks, skal de alle pege på det samme domæne. Eksempel:

  Korrekt (alle domæner er ens):

  `unsubscribe.bulkmailer.com`

  `profile.bulkmailer.com`

  `options.bulkmailer.com`

  Forkert (alle domæner er forskellige):

  `unsubscribe.bulkmailer.com`

  `profile.excite.com`

  `options.yahoo.com`

- Undgå indhold med store billeder og vedhæftede filer eller meddelelser, der udelukkende består af et billede.

- Din offentlige beskyttelse af personlige oplysninger eller P3P-indstillinger skal tydeligt angive tilstedeværelsen af sporingspixel (webbugs eller beacons).

### <a name="remove-incorrect-email-aliases-from-your-databases"></a>Fjern forkerte mailaliasser fra dine databaser

Alle mailaliaser i din database, der opretter en bounce-back, er unødvendige og sætter dine udgående mails i fare for yderligere kontrol via mailfiltreringstjenester. Sørg for, at din maildatabase er opdateret.
