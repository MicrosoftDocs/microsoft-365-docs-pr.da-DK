---
title: Referencepolitikker, fremgangsmåder og retningslinjer
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ff3f140b-b005-445f-bfe0-7bc3f328aaf0
ms.collection:
- M365-security-compliance
description: Microsoft har udviklet forskellige politikker, procedurer og vedtaget flere bedste praksisser for branchen for at beskytte vores brugere mod stødende, uønskede eller skadelige mails.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 815fea8981fdab8825a109dae69abaf8232997f9
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130357"
---
# <a name="reference-policies-practices-and-guidelines"></a>Reference: Politikker, fremgangsmåder og retningslinjer

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft er dedikeret til at hjælpe med at give den brugeroplevelse, der er mest tillid til, på internettet. Microsoft har derfor udviklet forskellige politikker, procedurer og vedtaget flere bedste praksisser for branchen for at beskytte vores brugere mod stødende, uønskede eller skadelige mails. Afsendere, der forsøger at sende mail til brugerne, skal sikre, at de forstår det fuldt ud og følger vejledningen i denne artikel for at hjælpe med dette og for at undgå potentielle leveringsproblemer.

Hvis du ikke overholder disse politikker og retningslinjer, er det muligvis ikke muligt for vores supportteam at hjælpe dig. Hvis du overholder de retningslinjer, fremgangsmåder og politikker, der præsenteres i denne artikel, og stadig oplever leveringsproblemer, der er baseret på din afsendende IP-adresse, skal du følge trinnene for at sende en fralisteanmodning. Du kan finde en vejledning [under Brug af fralisten til at fjerne dig selv fra listen over blokerede afsendere](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md).

## <a name="general-microsoft-policies"></a>Generelle Microsoft-politikker

Mail, der sendes til Microsoft 365 brugere, skal overholde alle Microsoft-politikker vedrørende overførsel og brug af Microsoft 365.

- Servicebetingelser, der gælder for Microsoft 365, især forbuddet mod at bruge tjenesten til at spamme eller distribuere malware.

- [Microsoft-serviceaftale](https://www.microsoft.com/servicesagreement/)

## <a name="governmental-regulations"></a>Regeringsbestemmelser

Mail, der sendes til Microsoft 365 brugere, skal overholde alle gældende love og bestemmelser for mailkommunikation i den relevante jurisdiktion.

- [CAN-SPAM Act: En vejledning i overholdelse af angivne standarder for virksomheder](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business)

- ["Fjern mig"-svar og -ansvar: Marketingfolk i mail skal overholde "Opsig abonnement"-krav](https://www.lawpublish.com/ftc-emai-marketers-unsubscribe-claims.html)

## <a name="technical-guidelines"></a>Tekniske retningslinjer

Mail, der sendes til Microsoft 365, skal overholde de relevante anbefalinger, der er angivet i dokumenterne nedenfor (nogle links er kun tilgængelige på engelsk).

- [RFC 2505: Anti-Spam-Anbefalinger til SMTP MTA'er](https://www.ietf.org/rfc/rfc2505.txt)

- [RFC 2920: SMTP-tjenesteudvidelse til kommandopipeline](https://www.ietf.org/rfc/rfc2920.txt)

Desuden skal mailservere, der opretter forbindelse til Microsoft 365 overholde følgende krav:

- Afsender forventes at overholde alle tekniske standarder for overførsel af internet-e-mail, som offentliggjort af Internet Society's Internet Engineering Task Force (IETF), herunder RFC 5321, RFC 5322, og andre.

- Efter at have givet en numerisk SMTP-fejlsvarkode mellem 500 og 599 (også kendt som et permanent svar, der ikke leveres eller NDR), må afsenderen ikke forsøge at videreoversende meddelelsen til den pågældende modtager.

- Efter flere svar, der ikke leveres, skal afsenderen ophøre med yderligere forsøg på at sende mail til den pågældende modtager.

- Meddelelser må ikke sendes via usikker mailrelæ eller proxyservere.

- Mekanismen for opsigelse af abonnementet, enten fra individuelle lister eller alle lister, der hostes af afsenderen, skal være klart dokumenteret og let at finde og bruge for modtagerne.

- Forbindelser fra dynamisk IP-område accepteres muligvis ikke.

- Mailservere skal have gyldige omvendte DNS-poster.

## <a name="reputation-management"></a>Administration af omdømme

Afsendere, internetudbydere og andre tjenesteudbydere skal aktivt administrere omdømmet for dine udgående IP-adresser.

## <a name="microsoft-365-limits"></a>Microsoft 365 grænser

Afsendere skal overholde Microsoft 365 grænser, der er angivet i [Exchange Online Protection grænser](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-limits).

## <a name="email-delivery-resources-and-organizations"></a>Mailleveringsressourcer og -organisationer

Microsoft arbejder aktivt sammen med brancheorganisationer og tjenesteudbydere for at forbedre internet- og mailøkosystemet. Disse organisationer har publiceret dokumenter om bedste praksis, som vi understøtter og anbefaler afsendere overholder. Dette forbedrer din mulighed for at levere mail blandt flere udbydere af mailtjenester over hele verden.

- [Messaging Malware Mobile Anti-Abuse Working Group](https://www.m3aawg.org/)

- [Online Trust Alliance](https://www.internetsociety.org/ota/)

- [Koalition af mailsender & udbydere](https://www.espcoalition.org/)

## <a name="abuse-and-spam-reporting"></a>Anmeldelse af misbrug og spam

Hvis du vil rapportere ulovlige, stødende, uønskede eller skadelige mails, skal du se [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md). Afsendelse af disse typer kommunikation er en overtrædelse af Microsofts politik, og der vil blive foretaget passende handlinger på bekræftede rapporter.

## <a name="law-enforcement"></a>Retshåndhævende

Hvis du er medlem af de retshåndhævende myndigheder og ønsker at betjene Microsoft Corporation med juridisk dokumentation vedrørende Office 365, eller hvis du har spørgsmål vedrørende juridisk dokumentation, du har indsendt til Microsoft, bedes du ringe (1) (425) 722-1299.
