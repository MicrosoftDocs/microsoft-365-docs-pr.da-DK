---
title: Opret lister over afsendere, der er tillid til
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
description: Administratorer kan få mere at vide om de tilgængelige og foretrukne indstillinger til at tillade indgående meddelelser Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b1edcbba31075e9880b8ea2034f4ffde50bb71e9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465723"
---
# <a name="create-safe-sender-lists-in-eop"></a>Opret lister over afsendere, der er tillid til i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Hvis du er Microsoft 365-kunde med postkasser i Exchange Online eller en enkeltstående Exchange Online Protection-kunde (EOP) uden Exchange Online-postkasser, tilbyder EOP flere måder at sikre, at brugerne modtager mail fra afsendere, der er tillid til. Disse indstillinger omfatter Exchange regler for mailflow (også kaldet transportregler), Outlook Pengeskab-afsendere, LISTEN over tilladte IP-adresser (filtrering af forbindelse) og tilladte lister over afsendere eller tilladte domæner i antispampolitikker. Samlet kan du overveje disse indstillinger som lister over afsendere, der _er tillid til_.

De tilgængelige lister over afsendere, der er tillid til, er beskrevet på følgende liste i rækkefølge fra mest anbefalede til mindst anbefalede:

1. Regler for mailflow
2. Outlook Pengeskab afsendere
3. Liste over tilladte IP-adresser (forbindelsesfiltrering)
4. Tilladte afsenderlister eller lister over tilladte domæner (antispampolitikker)

Regler for mailflow giver den største fleksibilitet til at sikre, at kun de rigtige meddelelser er tilladt. Lister over tilladte afsendere og tilladte domæner i antispampolitikker er ikke så sikre som IP-tilladelseslisten, fordi afsenderens maildomæne nemt bliver efterlignet. Men listen over tilladte IP-adresser udgør også en risiko, fordi mails  fra alle domæner, der sendes fra den pågældende IP-adresse, tilsidesætter spamfiltrering.

> [!IMPORTANT]
>
> - Meddelelser, der identificeres som malware eller phishing med høj tillid, er altid i karantæne, uanset hvilken indstilling på listen over afsendere, der er tillid til, som du bruger. Du kan finde flere oplysninger [under Sikkerhed som standard i Office 365](secure-by-default.md).
>
> - Sørg for at holde nøje øje med _eventuelle undtagelser_ , du gør i forbindelse med spamfiltrering ved hjælp af lister over afsendere, der er tillid til.
>
> - Selvom du kan bruge lister over afsendere, der er tillid til, til at hjælpe med falske positive (god mail, der er markeret som dårlig), bør du overveje at bruge lister over afsendere, der er tillid til, som en midlertidig løsning, der skal undgås, hvis det er muligt. Vi anbefaler ikke at administrere falske positive ved hjælp af lister over afsendere, der er tillid til, fordi undtagelser til spamfiltrering kan åbne din organisation for spoofing og andre angreb. Hvis du er på vagt over at bruge lister over afsendere, der er tillid til, til at administrere falske positive, skal du være afhængig og holde emnet Rapportere meddelelser og filer [til Microsoft](report-junk-email-messages-to-microsoft.md) klar.
>
> - Hvis du vil tillade et domæne at sende ikke-godkendt mail (bypass anti-spoofing-beskyttelse), men ikke omgå antispam og andre beskyttelsestjenester, kan du bruge [](learn-about-spoof-intelligence.md) efterlignet intelligensindsigt og lejerens [tilladelses-/blokeringsliste](tenant-allow-block-list.md).
>
> - EOP og Outlook undersøge forskellige meddelelsesegenskaber for at bestemme afsenderen af meddelelsen. Du kan finde flere oplysninger i [afsnittet Overvejelser ved massemail](#considerations-for-bulk-email) senere i denne artikel.
>

I modsætning hertil har du også flere muligheder for at blokere mail fra bestemte kilder ved hjælp af _lister over blokerede afsendere_. Få mere at vide under [Opret lister over blokerede afsendere i EOP](create-block-sender-lists-in-office-365.md).

## <a name="recommended-use-mail-flow-rules"></a>(Anbefalet) Brug af regler for mailflow

> [!NOTE]
> Du kan ikke bruge brevhoveder og regler for mailflow til at angive en intern afsender som en sikker afsender. Fremgangsmåderne i dette afsnit fungerer kun for eksterne afsendere.

Regler for mailflow i Exchange Online enkeltstående EOP bruger betingelser og undtagelser til at identificere meddelelser, og handlinger til at angive, hvad der skal gøres ved disse meddelelser. Du kan finde flere oplysninger [i Regler for mailflow (transportregler) Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).

I følgende eksempel antages det, at du skal bruge mail contoso.com for at springe spamfiltrering over. Det gør du ved at konfigurere følgende indstillinger:

1. **Betingelse**: **Afsenderdomænet** \> **er contoso.com**\>.

2. Konfigurer en af følgende indstillinger:

   - **Betingelse for mailflowregel**: **Et brevhoved** \> **indeholder et af disse ord** **Sidehovednavn**\>: `Authentication-Results` \> **Sidehovedværdi**: `dmarc=pass` eller `dmarc=bestguesspass`.

     Denne betingelse kontrollerer mailgodkendelsesstatus for det afsendende maildomæne for at sikre, at det afsendende domæne ikke bliver efterlignet. Du kan finde flere oplysninger om mailgodkendelse [under SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) og [DMARC](use-dmarc-to-validate-email.md).

   - **Liste over tilladte IP-adresser**: Angiv kilde-IP-adressen eller adresseområdet i forbindelsesfilterpolitikken.

     Brug denne indstilling, hvis det afsendende domæne ikke bruger mailgodkendelse. Vær så restriktiv som muligt, når det gælder kilde-IP-adresserne på listen over tilladte IP-adresser. Vi anbefaler et IP-adresseområde på /24 eller mindre (mindre er bedre). Brug ikke IP-adresseintervaller, der tilhører forbrugertjenester (f.eks. outlook.com) eller delte billeder.

   > [!IMPORTANT]
   >
   > - Konfigurer aldrig regler for mailflow kun _med_ afsenderdomænet som betingelse for at springe spamfiltrering over. Hvis du gør  dette, øges sandsynligheden for, at hackere kan efterligne det afsendende domæne (eller udgive sig for at være den fulde mailadresse), springe al spamfiltrering over og springe afsendergodkendelseskontrol over, så meddelelsen ankommer i modtagerens indbakke.
   >
   > - Brug ikke domæner, du ejer (også kendt som accepterede domæner) eller populære domæner (f.eks microsoft.com) som betingelser i regler for mailflow. At gøre dette betragtes som høj risiko, fordi det skaber muligheder for hackere at sende mails, der ellers ville blive filtreret.
   >
   > - Hvis du tillader en IP-adresse, der er bag en netværksadresseoversættelsesgateway (NAT), skal du kende de servere, der er involveret i NAT-puljen, for at kende omfanget af din liste over tilladte IP-adresser. IP-adresser og NAT-deltagere kan ændre sig. Du skal med jævne mellemrum kontrollere dine IP-tilladelseslisteposter som en del af dine standardvedligeholdelsesprocedurer.

3. **Valgfri betingelser**:
   -  \> Afsenderen **er intern/ekstern** \> **Uden for organisationen**: Denne betingelse er implicit, men det er OK at bruge den til at tage højde for lokale mailservere, der muligvis ikke er konfigureret korrekt.
   - **Emnet eller brødteksten** \> **emne eller brødtekst omfatter et af disse ord** \> \<keywords\>Hvis du yderligere kan begrænse meddelelser efter nøgleord eller udtryk i emnelinjen eller meddelelsesteksten, kan du bruge disse ord som en betingelse.

4. **Handling**: Konfigurer begge disse handlinger i reglen:
   1. **Rediger meddelelsesegenskaberne** \> **indstille SCL (spam confidence level)** \> **Tilgår spamfiltrering**.
   2. **Rediger meddelelsesegenskaberne** \> **angiv et brevhoved**: **Indstil brevhovedet** \<CustomHeaderName\> **til værdien** \<CustomHeaderValue\>.

      F.eks. `X-ETR: Bypass spam filtering for authenticated sender 'contoso.com'`. Hvis du har mere end ét domæne i reglen, kan du tilpasse brevhovedteksten efter behov.

      Når en meddelelse springer spamfiltrering over på grund af en regel for mailflow, `SFV:SKN` stemples værdien i **overskriften X-Forefront Antispam Report** . Hvis meddelelsen kommer fra en kilde, der er på listen over tilladte IP-adresser, tilføjes `IPV:CAL` værdien også. Disse værdier kan hjælpe dig med fejlfinding.

      :::image type="content" source="../../media/1-AllowList-SkipFilteringFromContoso.png" alt-text="Indstillinger for mailflowregel i EAC til at tilsidesætte spamfiltrering" lightbox="../../media/1-AllowList-SkipFilteringFromContoso.png":::


## <a name="use-outlook-safe-senders"></a>Brug Outlook Pengeskab afsendere

> [!CAUTION]
> Denne metode skaber en høj risiko for, at hackere kan levere mails til indbakken, som ellers ville blive filtreret. Men brugerens lister over afsendere Pengeskab afsendere Pengeskab domæner forhindrer ikke malware eller phishingmeddelelser med høj tillid til at blive filtreret.

I stedet for en organisatorisk indstilling kan brugere eller administratorer føje afsenderens mailadresser til listen Pengeskab afsendere i postkassen. Du kan finde en vejledning [i Konfigurere indstillinger for uønsket mail Exchange Online postkasser i Office 365](configure-junk-email-settings-on-exo-mailboxes.md). Dette ønskes ikke i de fleste situationer, da afsendere kommer til at tilsidesætte dele af filtreringsstakken. Selvom du har tillid til afsenderen, kan afsenderen stadig kompromitteres og sende skadeligt indhold. Det er bedst, at du lader vores filtre gøre det, der er nødvendigt for at kontrollere alle meddelelser og derefter rapportere det falske [positive/negative til Microsoft](report-junk-email-messages-to-microsoft.md) , hvis vores filtre gik galt. Hvis du tilsidesætter filtreringsstakken, forstyrrer det også [ZAP](zero-hour-auto-purge.md).

Når meddelelser springer spamfiltrering over på grund af en brugers liste over Pengeskab-afsendere, vil **X-Forefront Antispam Report-overskriftsfeltet** `SFV:SFE`indeholde værdien , som angiver, at filtrering for spam, spoof og phishing er blevet ignoreret.

## <a name="use-the-ip-allow-list"></a>Brug listen over tilladte IP-adresser

Hvis du ikke kan bruge regler for mailflow som beskrevet tidligere, er den bedste løsning at føje kildemailserveren eller -servere til listen over tilladte IP-adresser i forbindelsesfilterpolitikken. Du kan få mere at [vide under Konfigurer filtrering af forbindelse i EOP](configure-the-connection-filter-policy.md).

**Bemærkninger**:

- Det er vigtigt, at du holder antallet af tilladte IP-adresser på et minimum, så undgå at bruge hele IP-adresseintervaller, når det er muligt.
- Brug ikke IP-adresseintervaller, der tilhører forbrugertjenester (f.eks. outlook.com) eller delte billeder.
- Gennemgå regelmæssigt posterne på listen over tilladte IP-adresser, og fjern de poster, du ikke længere skal bruge.

> [!CAUTION]
> Uden yderligere bekræftelse, som f.eks. regler for mailflow, springer mail fra kilder i listen over tilladte IP-adresser spamfiltrering og afsendergodkendelse (SPF, DKIM, DMARC) over. Dette skaber en høj risiko for, at hackere kan levere mails til indbakken, som ellers ville blive filtreret. Men listen over tilladte IP-adresser forhindrer ikke malware eller phishingmeddelelser med høj tillid i at blive filtreret.

## <a name="use-allowed-sender-lists-or-allowed-domain-lists"></a>Brug lister over tilladte afsendere eller tilladte domæner

Den mindst ønskede mulighed er at bruge listen over tilladte afsendere eller listen over tilladte domæner i politikker for uønsket post. Du bør undgå denne indstilling, hvis det overhovedet er muligt, fordi afsendere tilsidesætter alt spam, spoof og phishing-beskyttelse og afsendergodkendelse (SPF, DKIM, DMARC). Denne metode anbefales kun til midlertidige test. De detaljerede trin kan findes i Konfigurer [antispam-politikker i EOP-emnet](configure-your-spam-filter-policies.md) .

Den maksimale grænse for disse lister er ca. 1000 poster. du kan dog kun angive 30 poster på portalen. Du skal bruge PowerShell til at tilføje mere end 30 poster.

> [!CAUTION]
>
> - Denne metode skaber en høj risiko for, at hackere kan levere mails til indbakken, som ellers ville blive filtreret. De tilladte afsendere eller lister over tilladte domæner forhindrer dog ikke malware eller phishingmeddelelser med høj tillid i at blive filtreret.
>
> - Brug ikke domæner, du ejer (også kaldet accepterede domæner) eller populære domæner (f.eks. microsoft.com) på lister over tilladte domæner.

## <a name="considerations-for-bulk-email"></a>Overvejelser i forbindelse med massemail

En standard-SMTP-mail består af en konvolut _og_ meddelelsesindhold. Konvolutten indeholder oplysninger, der er nødvendige for at sende og levere meddelelsen mellem SMTP-servere. Meddelelsesindholdet indeholder brevhovedfelter (samlet kaldet _brevhovedet_) og meddelelsens brødtekst. Konvolutten er beskrevet i RFC 5321, og brevhovedet er beskrevet i RFC 5322. Modtagerne får aldrig vist den faktiske konvolut, fordi den genereres af meddelelsesprocessen, og den er faktisk ikke en del af meddelelsen.

- Adressen `5321.MailFrom` (også kaldet **MAIL FROM-adressen** , P1-afsenderen eller konvolutafsenderen) er den mailadresse, der bruges i SMTP-afsendelsen af meddelelsen. Denne mailadresse registreres typisk i feltet Med retursti i brevhovedet (selvom afsenderen kan angive en anden  **Retursti-mailadresse**). Hvis meddelelsen ikke kan leveres, er det modtageren af rapporten om manglende levering (også kaldet en NDR- eller meddelelse om ikke-leveret mail).
- (også kaldet Fra-adressen  eller P2-afsenderen) er mailadressen i feltet Fra og  er afsenderens mailadresse, der vises i mailklienter.`5322.From`

Ofte er adresserne `5321.MailFrom` `5322.From` de samme (person til person-kommunikation). Men når mail sendes på vegne af andre, kan adresserne være forskellige. Dette sker oftest for massemails.

Antag f.eks., at Blue Yonder Airlines har ansat Margies Travel til at udsende sin mailannoncering. Den meddelelse, du modtager i din indbakke, har følgende egenskaber:

- Adressen `5321.MailFrom` er blueyonder.airlines@margiestravel.com.
- Adressen `5322.From` er blueyonder@news.blueyonderairlines.com, hvilket er, hvad du ser i Outlook.

Pengeskab afsenderlister og lister over sikre domæner i antispampolitikker i EOP`5322.From`, skal du kun undersøge adresserne, dette svarer til Outlook Pengeskab-afsendere, der bruger `5322.From` adressen.

Hvis du vil forhindre denne meddelelse i at blive filtreret, kan du gøre følgende:

- Tilføj blueyonder@news.blueyonderairlines.com (adressen`5322.From`) som afsender Outlook Pengeskab afsender.
- [Brug en regel for mailflow](#recommended-use-mail-flow-rules) med en betingelse, der søger efter meddelelser blueyonder@news.blueyonderairlines.com ( `5322.From` adressen, blueyonder.airlines@margiestravel.com (), `5321.MailFrom`eller begge.
