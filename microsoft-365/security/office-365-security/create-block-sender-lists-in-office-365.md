---
title: Opret lister over blokerede afsendere
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
description: Administratorer kan få mere at vide om de tilgængelige og foretrukne indstillinger til at blokere indgående meddelelser Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bf47fd7723bc1fe9cdef1b57cf16e1948112e749
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63675642"
---
# <a name="create-blocked-sender-lists-in-eop"></a>Opret lister over blokerede afsendere i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser tilbyder EOP flere måder at blokere mails fra uønskede afsendere på. Disse indstillinger omfatter Outlook-blokerede afsendere, lister over blokerede afsendere eller blokerede domæner i antispampolitikker, Exchange regler for mailflow (også kaldet transportregler) og IP-blokeringslisten (forbindelsesfiltrering). Samlet kan du se disse indstillinger som lister over _blokerede afsendere_.

Den bedste metode til at blokere afsendere varierer i forhold til omfanget af påvirkningen. For en enkelt bruger kan den rigtige løsning være Outlook blokerede afsendere. For mange brugere vil en af de andre indstillinger være mere passende. Følgende indstillinger er rangeret efter både effektområde og brødkrus. Listen går fra smal til bred, men læs _de specifikke oplysninger_ for at få alle anbefalinger.

1. Outlook blokerede afsendere (listen over blokerede afsendere, der er gemt i hver postkasse)

2. Lister over blokerede afsendere eller blokerede domæner (antispampolitikker)

3. Regler for mailflow

4. IP-blokliste (forbindelsesfiltrering)

> [!NOTE]
> Selvom du kan bruge blokindstillinger for hele organisationen til at adressere falske negative (mistet spam), bør du også sende disse meddelelser til Microsoft til analyse. Administration af falske negativer ved hjælp af bloklister øger administrativt arbejde betydeligt. Hvis du bruger bloklister til at undgå mistet spam, skal du holde emnet [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md) klar.

Til sammenligning har du også flere muligheder for altid at tillade mail fra bestemte kilder ved hjælp af lister over _afsendere, der er tillid til_. Få mere at vide under [Opret lister over afsendere, der er tillid til](create-safe-sender-lists-in-office-365.md).

## <a name="email-message-basics"></a>Grundlæggende om mails

En standard-SMTP-mail består af en konvolut _og_ meddelelsesindhold. Konvolutten indeholder oplysninger, der er nødvendige for at sende og levere meddelelsen mellem SMTP-servere. Meddelelsesindholdet indeholder brevhovedfelter (samlet kaldet _brevhovedet_) og meddelelsens brødtekst. Konvolutten er beskrevet i RFC 5321, og brevhovedet er beskrevet i RFC 5322. Modtagerne får aldrig vist den faktiske konvolut, fordi den genereres af meddelelsesprocessen, og den er faktisk ikke en del af meddelelsen.

- Adressen `5321.MailFrom` (også kaldet **MAIL FROM-adressen** , P1-afsenderen eller konvolutafsenderen) er den mailadresse, der bruges i SMTP-afsendelsen af meddelelsen. Denne mailadresse registreres typisk i feltet Med retursti i brevhovedet (selvom afsenderen kan angive en anden  **Retursti-mailadresse**). Hvis meddelelsen ikke kan leveres, er det modtageren af rapporten om manglende levering (også kaldet en NDR- eller meddelelse om ikke-leveret mail).

- (også kaldet Fra-adressen  eller P2-afsenderen) er mailadressen i feltet Fra og  er afsenderens mailadresse, der vises i mailklienter.`5322.From`

Ofte er adresserne `5321.MailFrom` `5322.From` de samme (person til person-kommunikation). Men når mail sendes på vegne af andre, kan adresserne være forskellige.

Lister over blokerede afsendere og blokerede domæner i antispampolitikker i EOP undersøger både adresserne `5321.MailFrom` og `5322.From` . Outlook afsendere af uønsket mail bruger kun `5322.From` adressen.

## <a name="use-outlook-blocked-senders"></a>Brug Outlook blokerede afsendere

Når kun et lille antal brugere har modtaget uønsket mail, kan brugere eller administratorer føje afsenderens mailadresser til listen over blokerede afsendere i postkassen. Du kan finde en vejledning [i Konfigurere indstillinger for uønsket mail Exchange Online postkasser](configure-junk-email-settings-on-exo-mailboxes.md).

Når meddelelser blokeres på grund af en brugers liste over blokerede afsendere, indeholder feltet **X-Forefront Antispam Report** værdien `SFV:BLK`.

> [!NOTE]
> Hvis de uønskede meddelelser er nyhedsbreve fra en anerkendt og genkendelig kilde, er det en anden mulighed at fjerne abonnementet fra mailen for at forhindre brugeren i at modtage meddelelserne.

## <a name="use-blocked-sender-lists-or-blocked-domain-lists"></a>Brug lister over blokerede afsendere eller lister over blokerede domæner

Når flere brugere påvirkes, er omfanget bredere, så den bedste løsning er lister over blokerede afsendere eller lister over blokerede domæner i antispampolitikker. Meddelelser fra afsendere på listerne er markeret som **Spam** (ikke spam med høj **tillid), og** den handling, du har konfigureret for **spamfilterets** vurdering, sker på meddelelsen. Få mere at vide under [Konfigurer antispam-politikker](configure-your-spam-filter-policies.md).

Den maksimale grænse for disse lister er ca. 1000 poster.

## <a name="use-mail-flow-rules"></a>Brug af regler for mailflow

Hvis du har brug for at blokere meddelelser, der sendes til bestemte brugere eller på tværs af hele organisationen, kan du bruge regler for mailflow. Regler for mailflow er mere fleksible end at blokere lister over afsendere eller lister over blokerede afsenderdomæner, fordi de også kan søge efter nøgleord eller andre egenskaber i de uønskede meddelelser.

Uanset de betingelser eller undtagelser, du bruger til at identificere meddelelserne, skal du konfigurere handlingen til at angive meddelelsens konfidensniveau (SCL) til 9, hvilket markerer meddelelsen som Spam med høj **tillid.** Få mere at vide under [Brug regler for mailflow til at indstille SCL i meddelelser](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

> [!IMPORTANT]
> Det er nemt at oprette regler, der er alt _for aggressive,_ så det er vigtigt, at du kun identificerer de meddelelser, du vil blokere, ved hjælp af meget specifikke kriterier. Sørg også for at aktivere overvågning af reglen og teste resultaterne af reglen for at sikre, at alt fungerer som forventet.

## <a name="use-the-ip-block-list"></a>Brug IP-bloklisten

Når det ikke er muligt at bruge en af de andre muligheder for at blokere en _afsender, skal_ du kun bruge LISTEN over blokerede IP-adresser i forbindelsesfilterpolitikken. Du kan finde flere oplysninger [under Konfigurere filterpolitikken for forbindelse](configure-the-connection-filter-policy.md). Det er vigtigt at holde antallet af blokerede IP-adresser på et minimum, så det anbefales ikke at blokere hele _IP-adresseintervaller_ .

Du bør  især undgå at tilføje IP-adresseintervaller, der tilhører forbrugertjenester (f.eks. outlook.com) eller delte værdier, og du skal også sørge for at gennemgå listen over blokerede IP-adresser som en del af almindelig vedligeholdelse.
