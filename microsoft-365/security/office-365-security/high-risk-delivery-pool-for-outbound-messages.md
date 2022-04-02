---
title: Udgående leveringspuljer
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
ms.assetid: ac11edd9-2da3-462d-8ea3-bbf9dbc6f948
ms.collection:
- M365-security-compliance
description: Få mere at vide om, hvordan leveringsgrupper bruges til at beskytte omdømmet af mailservere i Microsoft 365 datacentre.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 273d105ca600face4d79d70fc1622dfce8bf9f5e
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403830"
---
# <a name="outbound-delivery-pools"></a>Udgående leveringspuljer

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Mailservere i Microsoft 365 er muligvis midlertidigt det sted, hvor spam sendes. Eksempelvis en malware eller ondsindede spamangreb i en lokal mailorganisation, der sender udgående mail via Microsoft 365-konti eller Microsoft 365 konti. Hackere forsøger også at undgå registrering ved at videresende meddelelser Microsoft 365 videresendelse.

Disse scenarier kan resultere i, at IP-adressen på de berørte Microsoft 365-datacenterservere vises på tredjeparts blokeringslister. Destinationsmailorganisationer, der bruger disse blokeringslister, afviser mails fra disse Microsoft 365 mailkilder.

## <a name="high-risk-delivery-pool"></a>Pulje til levering af høj risiko

For at forhindre, at vores IP-adresser blokeres, sendes alle udgående meddelelser fra Microsoft 365-datacenterservere, der vurderes at være spam, via _risikoleveringspuljen_.

Den store risikoleveringspulje er en separat IP-adressepulje for udgående mail, der kun bruges til at sende meddelelser af "lav kvalitet" (f.eks. spam [og backscatter](backscatter-messages-and-eop.md). Brug af stor risikoleveringspuljen hjælper med at forhindre den normale IP-adressepulje for udgående mail i at sende spam. Den normale IP-adressepulje for udgående mails fastholder omdømmet ved afsendelse af meddelelser af "høj kvalitet", hvilket reducerer sandsynligheden for, at disse IP-adresser vises på IP-blokeringslister.

Den meget reelle mulighed for, at IP-adresser i puljen af levering af høj risiko placeres på IP-blokeringslister, men det er tilsmudsning. Levering til de tilsigtede modtagere er ikke garanteret, fordi mange mailorganisationer ikke vil acceptere meddelelser fra puljen med levering med høj risiko.

Du kan få mere at vide [under Kontrollere udgående spam](outbound-spam-controls.md).

> [!NOTE]
> Meddelelser, hvor kildemaildomænet ikke har en A-post, og ingen MX-post defineret i offentlig DNS dirigeres altid gennem puljen af levering med høj risiko, uanset deres fordeling af spam- eller afsendelsesgrænse.
>
> Meddelelser, der overskrider følgende grænser, blokeres, så de ikke sendes gennem puljen af levering med høj risiko:
>
> - [Tjenestens grænser for afsendelse](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options).
> - [Politikker for udgående spam](configure-the-outbound-spam-policy.md) , hvor afsenderne er begrænset i at kunne sende mail.

### <a name="bounce-messages"></a>Meddelelser om ikke-sendt mail

Den udgående risikoleveringspulje administrerer levering for alle rapporter om manglende levering (også kaldet rapporter om manglende levering, meddelelser om ikke-leveret mail, meddelelser om leveringsstatus eller DSN'er).

Mulige årsager til en stigning i antallet af manglende leveringr omfatter:

- En spoofing-kampagne, der påvirker en af de kunder, der bruger tjenesten.
- Et katalogopslagsangreb.
- Et spamangreb.
- En server til server med server til server med server til

Alle disse problemer kan medføre en pludselig stigning i antallet af NDR'er, der behandles af tjenesten. Mange gange ser disse NDR'er ud til at være spam for andre mailservere og -tjenester (også _[kaldet backscatter](backscatter-messages-and-eop.md)_).

### <a name="relay-pool"></a>Relæpulje

Meddelelser, der videresendes via Microsoft 365 i visse scenarier, sendes ved hjælp af en særlig relæpulje, fordi destinationen ikke bør overveje Microsoft 365 som den faktiske afsender. Det er vigtigt, at vi isolerer denne mailtrafik, fordi der er legitime og ugyldige scenarier for automatisk videresendelse eller videresendelse af mail fra Microsoft 365. Ligesom risikoleveringspuljen bruges en separat IP-adressepulje til videresendelse af mail. Denne adressegruppe publiceres ikke, fordi den kan ændres ofte, og den er ikke en del af den publicerede SPF-post for Microsoft 365.

Microsoft 365 bekræfte, at den oprindelige afsender er legitim, så vi med sikkerhed kan levere den videresendte meddelelse.

Den videresendte eller videresendte meddelelse skal opfylde et af følgende kriterier for at undgå at bruge relæpuljen:

- Den udgående afsender er i et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- SPF videregiver, når meddelelsen kommer til at Microsoft 365.
- DKIM på afsenderdomænet passerer, når meddelelsen kommer til at Microsoft 365.

Du kan se, at en meddelelse blev sendt via relay-puljen ved at kigge på udgående server-IP (relay-puljen vil være i området 40.95.0.0/16) eller ved at se på navnet på den udgående server (har "rly" i navnet).

I tilfælde, hvor vi kan godkende afsenderen, bruger vi SRS (Sender Rewriting Scheme) til at hjælpe modtagerens mailsystem med at vide, at den videresendte meddelelse er fra en pålidelig kilde. Du kan læse mere om, hvordan det fungerer, og hvad du kan gøre for at sikre, at det afsendende domæne videregiver godkendelse i [SRS (Sender Rewriting Scheme) i Office 365](/office365/troubleshoot/antispam/sender-rewriting-scheme).

For at DKIM kan fungere, skal du sørge for at aktivere DKIM til at sende domæne. Eksempelvis er fabrikam.com del af en contoso.com og er defineret i organisationens accepterede domæner. Hvis meddelelsens afsender er sender@fabrikam.com, skal DKIM være aktiveret til fabrikam.com. Du kan læse om, hvordan du aktiverer på [Brug DKIM til at validere udgående mails, der sendes fra dit brugerdefinerede domæne](use-dkim-to-validate-outbound-email.md).

Hvis du vil tilføje et brugerdefineret domæne, skal du følge [trinnene i Føj et domæne Microsoft 365](../../admin/setup/add-domain.md).

Hvis MX-posten for dit domæne peger på en tredjepartstjeneste eller en lokal mailserver, skal du bruge Udvidet [filtrering for forbindelser](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors). Udvidet filtrering sikrer, at SPF-valideringen er korrekt for indgående mail, og undgår at sende mails via relaypuljen.
