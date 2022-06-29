---
title: Opret lister over sikre afsendere
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MET150s
ms.assetid: 9721b46d-cbea-4121-be51-542395e6fd21
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om de tilgængelige og foretrukne muligheder for at tillade indgående meddelelser i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 016257a6cdc3128ba6753532bb0bed74845355d0
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493081"
---
# <a name="create-safe-sender-lists-in-eop"></a>Opret lister over sikre afsendere i EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Hvis du er Microsoft 365-kunde med postkasser i Exchange Online eller en separat EOP-kunde (Exchange Online Protection) uden Exchange Online postkasser, tilbyder EOP flere måder at sikre, at brugerne modtager mail fra afsendere, der er tillid til. Disse indstillinger omfatter Regler for Exchange-mailflow (også kendt som transportregler), Outlook Safe Senders, IP-tilladelseslisten (forbindelsesfiltrering) og lister over tilladte afsendere eller tilladte domænelister i politikker til bekæmpelse af spam. Samlet set kan du tænke på disse indstillinger som _sikre afsenderlister_.

De tilgængelige lister over sikre afsendere er beskrevet på følgende liste i rækkefølge fra de mest anbefalede til mindst anbefalede:

1. Regler for mailflow
2. Afsendere, der er tillid til i Outlook
3. Liste over IP-tilladte (forbindelsesfiltrering)
4. Lister over tilladte afsendere eller tilladte domænelister (politikker til bekæmpelse af spam)

Regler for mailflow giver størst fleksibilitet til at sikre, at kun de rigtige meddelelser er tilladt. Lister over tilladte afsendere og tilladte domæner i politikker til bekæmpelse af spam er ikke så sikre som listen over tilladte IP-adresser, fordi afsenderens maildomæne nemt bliver forfalsket. Men ip-listen over tilladte ip-adresser udgør også en risiko, fordi mail fra _et hvilket som helst_ domæne, der sendes fra den pågældende IP-adresse, tilsidesætter filtrering af spam.

> [!IMPORTANT]
>
> - Meddelelser, der identificeres som malware eller phishing med høj sikkerhed, er altid sat i karantæne, uanset hvilken liste over sikre afsendere du bruger. Du kan få flere oplysninger under [Sikker som standard i Office 365](secure-by-default.md).
>
> - Vær forsigtig med nøje at overvåge _eventuelle_ undtagelser, som du gør for spamfiltrering ved hjælp af sikre afsenderlister.
>
> - Mens du kan bruge sikre afsenderlister til at hjælpe med falske positiver (god e-mail markeret som dårlig), bør du overveje brugen af sikre afsenderlister som en midlertidig løsning, der bør undgås, hvis det er muligt. Vi anbefaler ikke, at du administrerer falske positiver ved hjælp af sikre afsenderlister, da undtagelser fra spamfiltrering kan åbne din organisation for spoofing og andre angreb. Hvis du insisterer på at bruge lister over sikre afsendere til at administrere falske positiver, skal du være på vagt og holde emnet [Rapportmeddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md) klar.
>
> - Hvis du vil tillade, at et domæne sender ikke-godkendt mail (omgå beskyttelse mod spoofing), men ikke tilsidesætte anti-spam og andre beskyttelser, kan du bruge [indsigt i spoof intelligence](learn-about-spoof-intelligence.md) og [lejerens tilladelses-/blokliste](tenant-allow-block-list.md).
>
> - EOP og Outlook undersøger forskellige meddelelsesegenskaber for at bestemme meddelelsens afsender. Du kan få flere oplysninger i afsnittet [Overvejelser i forbindelse med massemail](#considerations-for-bulk-email) senere i denne artikel.
>

I modsætning hertil har du også flere muligheder for at blokere mail fra bestemte kilder ved hjælp af _lister over blokerede afsendere_. Du kan få flere oplysninger under [Opret lister over afsenderblokering i EOP](create-block-sender-lists-in-office-365.md).

## <a name="recommended-use-mail-flow-rules"></a>(Anbefalet) Brug regler for mailflow

> [!NOTE]
> Du kan ikke bruge regler for brevhoveder og mailflow til at angive en intern afsender som en sikker afsender. Procedurerne i dette afsnit fungerer kun for eksterne afsendere.

Regler for mailflow i Exchange Online og separat EOP bruger betingelser og undtagelser til at identificere meddelelser og handlinger til at angive, hvad der skal gøres for disse meddelelser. Du kan få flere oplysninger under [Regler for mailflow (transportregler) i Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).

I følgende eksempel antages det, at du har brug for mail fra contoso.com til at springe spamfiltrering over. Det gør du ved at konfigurere følgende indstillinger:

1. **Betingelse**: **Afsenderens** \> **domæne er** \> contoso.com.

2. Konfigurer en af følgende indstillinger:

   - **Regelbetingelse for mailflow**: **En meddelelsesheader** \> **indeholder et af disse ord** \> **Headernavn**: `Authentication-Results` \> **Headerværdi**: `dmarc=pass` eller `dmarc=bestguesspass`.

     Denne betingelse kontrollerer mailgodkendelsesstatussen for det sendende maildomæne for at sikre, at det afsendende domæne ikke bliver spoofed. Du kan få flere oplysninger om mailgodkendelse under [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) og [DMARC](use-dmarc-to-validate-email.md).

   - **Ip-tilladelsesliste**: Angiv kildens IP-adresse eller adresseområde i forbindelsesfilterpolitikken.

     Brug denne indstilling, hvis det afsendende domæne ikke bruger mailgodkendelse. Vær så restriktiv som muligt, når det kommer til kilde-IP-adresserne på listen over tilladte IP-adresser. Vi anbefaler et IP-adresseinterval på /24 eller mindre (mindre er bedre). Brug ikke IP-adresseintervaller, der tilhører forbrugertjenester (f.eks. outlook.com) eller delte infrastrukturer.

   > [!IMPORTANT]
   >
   > - Konfigurer aldrig regler for mailflow _med kun_ afsenderdomænet som betingelse for at springe spamfiltrering over. Hvis du gør det _, øges sandsynligheden_ for, at angribere kan spoofe det afsendende domæne (eller repræsentere den fulde mailadresse), springe al spamfiltrering over og springe kontrol af afsendergodkendelse over, så meddelelsen modtages i modtagerens indbakke.
   >
   > - Brug ikke domæner, du ejer (også kendt som accepterede domæner) eller populære domæner (f.eks. microsoft.com) som betingelser i regler for mailflow. Det anses for at være en høj risiko, fordi det giver personer med ondsindede hensigter mulighed for at sende mails, der ellers ville blive filtreret.
   >
   > - Hvis du tillader en IP-adresse bag en NAT-gateway (Network Address Translation), skal du kende de servere, der er involveret i NAT-gruppen, for at kende omfanget af din IP-liste over tilladte. IP-adresser og NAT-deltagere kan ændre sig. Du skal jævnligt kontrollere dine IP-listeposter som en del af dine standardvedligeholdelsesprocedurer.

3. **Valgfrie betingelser**:
   - **Afsenderen** \> **er intern/ekstern** \> **Uden for organisationen**: Denne betingelse er implicit, men det er OK at bruge den til at tage højde for mailservere i det lokale miljø, der muligvis ikke er konfigureret korrekt.
   - **Emnet eller brødteksten** \> **emne eller brødtekst indeholder et af disse ord** \> \<keywords\>: Hvis du yderligere kan begrænse meddelelserne efter nøgleord eller udtryk i emnelinjen eller meddelelsesteksten, kan du bruge disse ord som en betingelse.

4. **Handling**: Konfigurer begge disse handlinger i reglen:
   1. **Rediger meddelelsesegenskaberne** \> **angiv niveauet for spamsikkerhed (SCL)** \> **Omgå filtrering af spam**.
   2. **Rediger meddelelsesegenskaberne** \> **angiv en brevhoved**: **Angiv brevhovedet** \<CustomHeaderName\> **til værdien** \<CustomHeaderValue\>.

      Det kunne f.eks. være `X-ETR: Bypass spam filtering for authenticated sender 'contoso.com'`. Hvis du har mere end ét domæne i reglen, kan du tilpasse overskriftsteksten efter behov.

      Når en meddelelse springer spamfiltrering over pga. en regel for mailflow, stemples værdien `SFV:SKN` i **headeren X-Forefront-Antispam-Report** . Hvis meddelelsen kommer fra en kilde, der er på listen over tilladte IP-adresser, tilføjes værdien `IPV:CAL` også. Disse værdier kan hjælpe dig med fejlfinding.

      :::image type="content" source="../../media/1-AllowList-SkipFilteringFromContoso.png" alt-text="Regelindstillingerne for mailflow i EAC til omgåelse af spamfiltrering" lightbox="../../media/1-AllowList-SkipFilteringFromContoso.png":::

## <a name="use-outlook-safe-senders"></a>Brug Afsendere, der er tillid til i Outlook

> [!CAUTION]
> Denne metode skaber en høj risiko for, at personer med ondsindede hensigter leverer mails til indbakken, som ellers ville blive filtreret. Men lister over sikre afsendere eller sikre domæner for brugeren forhindrer ikke filtrering af phishing-meddelelser med høj sikkerhed eller skadelig software.

I stedet for en organisationsindstilling kan brugere eller administratorer føje afsendermailadresserne til listen Afsendere, der er tillid til i postkassen. Du kan finde instruktioner under [Konfigurer indstillinger for uønsket mail på Exchange Online postkasser i Office 365](configure-junk-email-settings-on-exo-mailboxes.md). Denne metode er ikke ønskelig i de fleste situationer, da afsendere tilsidesætter dele af filtreringsstakken. Selvom du har tillid til afsenderen, kan afsenderen stadig blive kompromitteret og sende skadeligt indhold. Det er bedre, når du lader vores filtre kontrollere hver meddelelse og derefter [rapportere den falske positive/negative til Microsoft](report-junk-email-messages-to-microsoft.md) , hvis vi fik det forkert. Omgåelse af filtreringsstakken forstyrrer også [automatisk udrensning på nul timer (ZAP).](zero-hour-auto-purge.md)

Som design og for at øge sikkerheden for Exchange Online postkasser genkendes kun indstillingerne for uønsket mail for sikre afsendere, blokerede afsendere og blokerede domæner. Indstillingerne for sikre domæner ignoreres.

Når meddelelser springer spamfiltrering over på grund af en brugers liste over sikre afsendere, indeholder headerfeltet **X-Forefront-Antispam-Report** værdien `SFV:SFE`, hvilket angiver, at filtrering efter spam, spoof og phishing blev omgået.

## <a name="use-the-ip-allow-list"></a>Brug listen over tilladte IP-adresser

Hvis du ikke kan bruge regler for mailflow som tidligere beskrevet, er den næstbedste mulighed at føje kildemailserveren eller -serverne til IP-tilladelseslisten i forbindelsesfilterpolitikken. Du kan finde flere oplysninger [under Konfigurer forbindelsesfiltrering i EOP](configure-the-connection-filter-policy.md).

**Noter**:

- Det er vigtigt, at du holder antallet af tilladte IP-adresser på et minimum, så undgå at bruge hele IP-adresseintervaller, når det er muligt.
- Brug ikke IP-adresseintervaller, der tilhører forbrugertjenester (f.eks. outlook.com) eller delte infrastrukturer.
- Gennemse jævnligt posterne på listen over tilladte IP-adresser, og fjern de poster, du ikke længere har brug for.

> [!CAUTION]
> Uden yderligere bekræftelse, f.eks. regler for mailflow, springer mail fra kilder på IP-listen over filtrering af spam og sendergodkendelse (SPF, DKIM, DMARC) kontrol. Dette skaber en høj risiko for, at angribere leverer mails til indbakken, som ellers ville blive filtreret. Ip-listen over tilladte forhindrer dog ikke filtrering af phishing-meddelelser med høj sikkerhed eller skadelig software.

## <a name="use-allowed-sender-lists-or-allowed-domain-lists"></a>Brug lister over tilladte afsendere eller tilladte domænelister

Den mindst ønskelige mulighed er at bruge listen over tilladte afsendere eller den tilladte domæneliste i politikker til bekæmpelse af spam. Du bør undgå denne indstilling _, hvis det overhovedet er muligt_ , fordi afsendere tilsidesætter al beskyttelse mod spam, spoof og phishing og afsendergodkendelse (SPF, DKIM, DMARC). Denne metode bruges bedst kun til midlertidig test. Du kan finde de detaljerede trin i emnet [Konfigurer politikker mod spam i EOP](configure-your-spam-filter-policies.md) .

Den maksimale grænse for disse lister er ca. 1000 poster. Du kan dog kun angive 30 poster på portalen. Du skal bruge PowerShell til at tilføje mere end 30 poster.

> [!CAUTION]
>
> - Denne metode skaber en høj risiko for, at personer med ondsindede hensigter leverer mails til indbakken, som ellers ville blive filtreret. De tilladte afsendere eller lister over tilladte domæner forhindrer dog ikke filtrering af phishing-meddelelser med høj sikkerhed eller skadelig software.
>
> - Brug ikke domæner, du ejer (også kendt som accepterede domæner) eller populære domæner (f.eks. microsoft.com) på tilladte domænelister.

## <a name="considerations-for-bulk-email"></a>Overvejelser i forbindelse med massemail

En standard-SMTP-mail består af en _meddelelseskonvolut_ og meddelelsesindhold. Meddelelseskonvolutten indeholder oplysninger, der kræves for at sende og levere meddelelsen mellem SMTP-servere. Meddelelsesindholdet indeholder brevhovedfelter (samlet kaldet _meddelelsesoverskriften_) og meddelelsens brødtekst. Meddelelseskonvolutten er beskrevet i RFC 5321, og brevhovedet er beskrevet i RFC 5322. Modtagerne får aldrig vist den faktiske meddelelseskonvolut, fordi den genereres af meddelelsesoverførselsprocessen, og den er faktisk ikke en del af meddelelsen.

- Adressen `5321.MailFrom` (også kendt som **MAIL FROM-adresse** , P1-afsender eller konvolut afsender) er den mailadresse, der bruges i SMTP-overførslen af meddelelsen. Denne mailadresse registreres typisk i headerfeltet **Return-Path** i meddelelsesoverskriften (selvom det er muligt for afsenderen at angive en anden mailadresse for **returstien** ). Hvis meddelelsen ikke kan leveres, er det modtageren af rapporten om manglende levering (også kendt som en NDR eller bounce-meddelelse).
- `5322.From` (også kendt som **Fra-adressen** eller P2-afsenderen) er mailadressen i headerfeltet **Fra** og er afsenderens mailadresse, der vises i mailklienter.

Adresserne `5321.MailFrom` og `5322.From` er ofte de samme (person til person-kommunikation). Men når mail sendes på vegne af en anden, kan adresserne være forskellige. Dette sker oftest for massemailmeddelelser.

Antag f.eks., at Blue Yonder Airlines har hyret Margie's Travel til at sende sin e-mail-reklame. Den meddelelse, du modtager i indbakken, har følgende egenskaber:

- Adressen `5321.MailFrom` er blueyonder.airlines@margiestravel.com.
- Adressen `5322.From` er blueyonder@news.blueyonderairlines.com, hvilket er det, du får vist i Outlook.

Lister over sikre afsendere og lister over sikre domæner i politikker til bekæmpelse af spam i EOP undersøger kun adresserne `5322.From` . Dette svarer til Outlook Safe Senders, der bruger adressen `5322.From` .

Hvis du vil forhindre, at denne meddelelse filtreres, kan du benytte følgende fremgangsmåde:

- Tilføj blueyonder@news.blueyonderairlines.com ( `5322.From` adressen) som Outlook Safe Sender.
- [Brug en regel for et mailflow](#recommended-use-mail-flow-rules) med en betingelse, der søger efter meddelelser fra blueyonder@news.blueyonderairlines.com (adressen `5322.From` , blueyonder.airlines@margiestravel.com (den `5321.MailFrom`) eller begge dele.
