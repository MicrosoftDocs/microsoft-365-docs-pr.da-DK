---
title: 'Forbedring af mailflow med MTA-STS '
f1.keywords:
- NOCSH
ms.author: v-bshilpa
author: Benny-54
manager: serdars
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
description: Få mere at vide om, hvordan du forbedrer mailflowet med MTA-STS.
ms.openlocfilehash: 735cce96c61a2083b8f0785ace49a5b199790989
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "66858527"
---
# <a name="enhancing-mail-flow-with-mta-sts"></a>Forbedring af mailflow med MTA-STS

Understøttelse af [SMTP MTA Strict Transport Security](https://datatracker.ietf.org/doc/html/rfc8461) -standarden (MTA-STS) føjes til Exchange Online. Standarden blev udviklet for at sikre, at TLS altid bruges til forbindelser mellem mailservere. Det giver også mulighed for at sende servere for at validere, at modtagerserveren har et certifikat, der er tillid til. Hvis enten TLS ikke tilbydes, eller certifikatet ikke er gyldigt, nægter afsenderen at levere meddelelser. Disse nye kontroller forbedrer den overordnede sikkerhed for SMTP og beskytter mod man-in-the-middle-angreb.

MTA-STS kan opdeles i to scenarier: Indgående og udgående beskyttelse. Indgående dækker beskyttelse af domæner, der hostes i Exchange Online med MTA-STS, og udgående data dækker de MTA-STS-valideringer, der udføres af Exchange Online, når der sendes mails til MTA-STS-beskyttede domæner.

## <a name="outbound-protection"></a>Udgående beskyttelse

Alle meddelelser, der sendes udgående fra Exchange Online til MTA-STS-beskyttede modtagere, valideres med disse ekstra sikkerhedskontroller, der er angivet i MTA-STS-standarden. Der er ikke noget, som administratorer behøver at gøre for at anvende det. Vores udgående implementering respekterer modtagerens domæneejeres ønsker via deres MTA-STS-politik. MTA-STS er en del af sikkerhedsinfrastrukturen for Exchange Online, og den er derfor altid slået til (ligesom andre smtp-kernefunktioner).

## <a name="inbound-protection"></a>Indgående beskyttelse

Domæneejere kan udføre handlinger for at beskytte mails, der sendes til deres domæner med MTA-STS, hvis deres MX-post peger på Exchange Online. Hvis din MX-post peger på en mellemliggende tredjepartstjeneste, skal du kontrollere, at MTA-STS-kravene er opfyldt af dem og følge deres instruktioner.

Når MTA-STS er konfigureret for dit domæne, vil alle meddelelser, der sendes fra afsendere, der understøtter MTA-STS, udføre de valideringer, der er fastlagt af standarden, for at sikre en sikker forbindelse. Hvis du modtager en mail fra en afsender, der ikke understøtter MTA-STS, leveres mailen stadig uden den ekstra beskyttelse. På samme måde er der ingen afbrydelse af meddelelser, hvis du endnu ikke bruger MTA-STS, men afsenderen understøtter det. Det eneste scenarie, hvor meddelelser ikke leveres, er, når begge sider bruger MTA-STS- og MTA-STS-validering mislykkes.

## <a name="how-to-adopt-mta-sts"></a>Sådan adopterer du MTA-STS

MTA-STS gør det muligt for et domæne at deklarere understøttelse af TLS og kommunikere den MX-post og det destinationscertifikat, der forventes. Det angiver også, hvad en afsendende server skal gøre, hvis der er et problem. Dette gøres ved hjælp af en kombination af en DNS TXT-post og en politikfil, der udgives som en HTTPS-webside. Den HTTPS-beskyttede politik introducerer en anden sikkerhedsbeskyttelse, som angribere skal overvinde.

Et domænes MTA-STS TXT-post angiver MTA-STS-understøttelse til en afsender, hvorefter domænets HTTPS-baserede MTA-STS-politik hentes af afsenderen. Følgende TXT-post er et eksempel, der deklarerer understøttelse af MTA-STS:

`_mta-sts.contoso.com. 3600 IN TXT v=STSv1; id=20220101000000Z;`

Et domænes MTA-STS-politik skal være placeret på en foruddefineret URL-adresse, der hostes af domænets webinfrastruktur. Syntaksen for URL-adressen er `https://mta-sts.<domain name>/.well-known/mta-sts.txt`. Microsoft.coms politik findes f.eks. på: <https://mta-sts.microsoft.com/.well-known/mta-sts.txt>.

```text
version: STSv1
mode: enforce
mx: *.mail.protection.outlook.com
max_age: 604800
```

Alle kunder, hvis MX-poster peger direkte på Exchange Online, kan angive i deres egen politik med de samme værdier, som er vist ovenfor i politikken for microsoft.com. De entydige påkrævede oplysninger i politikken er den MX-post, der peger på Exchange Online (`*`.mail.protection.outlook.com), og det samme certifikat deles af alle Exchange Online kunder. Det er muligt at publicere din politik i *testtilstand* for at sikre, at den er gyldig, før du ændrer den til *tilstanden gennemtving* . Der findes valideringsværktøjer fra tredjepart, som kan kontrollere konfigurationen.

Disse politikker er ikke noget, som Exchange Online kan hoste på vegne af kunder, og kunderne bør gøre brug af den webhostingtjeneste, de bruger. Politikken skal være beskyttet af HTTPS med et certifikat for underdomænet `mta-sts.<domain name>`. Der er alternativer til at hoste en politik, herunder [denne løsning](https://github.com/jpawlowski/mta-sts.template) , der bruger GitHub-sider til at hoste den.

Når DNS TXT-domæneposten er oprettet, og politikfilen er tilgængelig på den påkrævede HTTPS URL-adresse, beskyttes domænet af MTA-STS. Du kan finde oplysninger om MTA-STS i [RFC 8461](https://datatracker.ietf.org/doc/html/rfc8461).
