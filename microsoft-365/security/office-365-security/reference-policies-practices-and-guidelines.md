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
description: Microsoft har udviklet forskellige politikker og procedurer og har indført flere bedste fremgangsmåder for branchen for at beskytte vores brugere mod grove, uønskede eller skadelige mails.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 21b1918155755d7786f7b797ae7c705ca8c0ec39
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589099"
---
# <a name="reference-policies-practices-and-guidelines"></a>Reference: Politikker, fremgangsmåder og retningslinjer

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft har fokus på at hjælpe med at levere den mest pålidelige brugeroplevelse på internettet. Derfor har Microsoft udviklet forskellige politikker og procedurer og indført flere bedste fremgangsmåder for branchen for at beskytte vores brugere mod grove, uønskede eller skadelige mails. Afsendere, der forsøger at sende mails til brugere, skal sikre, at de har fuld forståelse for og følger vejledningen i denne artikel for at hjælpe med dette og for at undgå potentielle problemer med levering.

Hvis du ikke overholder disse politikker og retningslinjer, er det muligvis ikke muligt for vores supportteam at hjælpe dig. Hvis du følger de retningslinjer, fremgangsmåder og politikker, der præsenteres i denne artikel, og du stadig oplever leveringsproblemer baseret på din afsendende IP-adresse, skal du følge trinnene for at sende en anmodning om at framelde dig. Du kan finde en vejledning [under Brug af listeportalen til at fjerne dig selv fra listen over blokerede afsendere](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md).

## <a name="general-microsoft-policies"></a>Generelle Microsoft-politikker

Mail, der sendes Microsoft 365, skal overholde alle Microsoft-politikker, der styrer overførsel og brug af Microsoft 365.

- Servicebetingelser, der er gældende for Microsoft 365, herunder forbud mod brug af tjenesten til spam eller distribution af malware.

- [Microsoft-serviceaftale](https://www.microsoft.com/servicesagreement/)

## <a name="governmental-regulations"></a>Statslige bestemmelser

Mail, der sendes Microsoft 365, skal overholde alle gældende love og bestemmelser for mailkommunikation i den pågældende jurisdiktion.

- [CAN-SPAM Act: A Compliance Guide for Business](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business)

- ["Fjern mig"-svar og -ansvarsområder: Mail marketingfolk skal efterkomme "Frameld" krav](https://www.lawpublish.com/ftc-emai-marketers-unsubscribe-claims.html)

## <a name="technical-guidelines"></a>Tekniske retningslinjer

Mails, der sendes Microsoft 365, skal overholde de gældende anbefalinger, der er angivet i nedenstående dokumenter (nogle links er kun tilgængelige på engelsk).

- [RFC 2505: Uønsket post Anbefalinger FOR SMTP-MTAs](https://www.ietf.org/rfc/rfc2505.txt)

- [RFC 2920: SMTP-tjenesteudvidelse til kommando pipelining](https://www.ietf.org/rfc/rfc2920.txt)

Desuden skal mailservere, der Microsoft 365 til mailservere, overholde følgende krav:

- Afsenderen forventes at overholde alle tekniske standarder for overførsel af internetmail, som udgivet af Internet Congos Internet Engineering Task Force (IETF), herunder RFC 5321, RFC 5322 og andre.

- Efter at have fået en numerisk SMTP-fejl svarkode mellem 500 og 599 (også kaldet et permanent svar om manglende levering eller NDR), må afsenderen ikke forsøge at sende meddelelsen igen til den pågældende modtager.

- Efter flere svar om manglende levering skal afsenderen ophøre med yderligere forsøg på at sende mails til den pågældende modtager.

- Meddelelser må ikke overføres via usikker mail relay eller proxyservere.

- Mekanismen til at abonnere, enten fra individuelle lister eller alle lister, der hostes af afsenderen, skal være tydeligt dokumenteret og nemt for modtagerne at finde og bruge.

- Forbindelser fra dynamisk IP-område accepteres muligvis ikke.

- Mailservere skal have gyldige omvendte DNS-poster.

## <a name="reputation-management"></a>Administration af omdømme

Afsendere, internetudbydere og andre tjenesteudbydere bør aktivt administrere dit ry for dine udgående IP-adresser.

## <a name="microsoft-365-limits"></a>Microsoft 365 begrænsninger

Afsendere skal overholde de Microsoft 365, der er angivet [i Exchange Online Protection grænser](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-limits).

## <a name="email-delivery-resources-and-organizations"></a>Ressourcer til levering af mail og organisationer

Microsoft arbejder aktivt sammen med brancheorganisationer og tjenesteudbydere for at forbedre internet- og mailøkosystemet. Disse organisationer har udgivet dokumenter med bedste praksis, som vi understøtter og anbefaler afsendere at overholde. Dette forbedrer din mulighed for at levere mail blandt flere mailtjenesteudbydere over hele verden.

- [Messaging Malware Mobile Anti-Abuse Working Group](https://www.m3aawg.org/)

- [Online Trust Alliance](https://www.internetsociety.org/ota/)

- [Mailafsender, & provider, der modtager mail](https://www.espcoalition.org/)

## <a name="abuse-and-spam-reporting"></a>Misbrug og spamrapportering

Hvis du vil rapportere ulovlige, grove, uønskede eller skadelige mails, skal [du se Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md). Afsendelse af disse typer kommunikation er en overtrædelse af Microsofts politik, og der vil blive taget relevante handlinger på bekræftede rapporter.

## <a name="law-enforcement"></a>Håndhævelse af lovgivning

Hvis du er medlem af lovgivningen og ønsker at betjene Microsoft Corporation med juridisk dokumentation om Office 365, eller hvis du har spørgsmål vedrørende juridisk dokumentation, du har indsendt til Microsoft, skal du ringe til (1) (425) 722-1299.