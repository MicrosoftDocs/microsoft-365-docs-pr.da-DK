---
title: Mailflow intelligence
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: troubleshooting
ms.custom: ''
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: c29f75e5-c16e-409e-a123-430691e38276
description: Administratorer kan få mere at vide om de fejlkoder, der er knyttet til levering af meddelelser ved hjælp af forbindelser (også kaldet mailflow intelligence).
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 2536120dfc336145ec9fdba1db34a8da1f56c1b4
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680990"
---
# <a name="mail-flow-intelligence-in-eop"></a>Mailflow intelligence i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser, bruger du typisk en forbindelse til at distribuere mails fra EOP til dit lokale mailmiljø. Du kan også bruge en forbindelse til at distribuere meddelelser Microsoft 365 til en partnerorganisation. Når Microsoft 365 ikke kan levere disse meddelelser via forbindelsen, er de i kø i Microsoft 365. Microsoft 365 fortsætter med at forsøge levering for hver meddelelse i 24 timer. Efter 24 timer udløber meddelelsen i kø, og meddelelsen returneres til den oprindelige afsender i en rapport om manglende levering (også kaldet en NDR eller meddelelse om ikke-leveret mail).

Microsoft 365 genererer en fejl, når en meddelelse ikke kan leveres ved hjælp af en forbindelse. De mest almindelige fejl og deres løsninger er beskrevet i denne artikel. Samlet set kaldes kø- og meddelelsesfejl for meddelelser, der ikke kan leveres, som sendes via forbindelser, for _mailflow intelligence_.

## <a name="error-code-450-44312-dns-query-failed"></a>Fejlkode: DNS-forespørgslen 450 4.4.312 mislykkedes

Typisk betyder denne fejl, at Microsoft 365 forsøgte at oprette forbindelse til den intelligente vært, der er angivet i forbindelsen, men DNS-forespørgslen for at finde den intelligente værts IP-adresser mislykkedes. De mulige årsager til denne fejl er:

- Der er et problem med dit domænes DNS-værtstjeneste (den part, der vedligeholder de autoritative navneservere for dit domæne).

- Dit domæne er for nylig udløbet, så MX-posten ikke kan hentes.

- Domænets MX-post er blevet ændret for nylig, og DNS-serverne har stadig tidligere cachelagret DNS-oplysninger for dit domæne.

### <a name="how-do-i-fix-error-code-450-44312"></a>Hvordan retter jeg fejlkode 450 4.4.312?

- Arbejd med din DNS-hostingtjeneste for at identificere og løse problemet med dit domæne.

- Hvis fejlen opstår i din partnerorganisation (f.eks. en tredjepartsudbyder af serviceudbyder), skal du kontakte din partner for at løse problemet.

## <a name="error-code-450-44315-connection-timed-out"></a>Fejlkode: 450 4.4.315-forbindelse timed out

Det betyder typisk, Microsoft 365 ikke kan oprette forbindelse til destinationsmailserveren. Fejloplysningerne forklarer problemet. Eksempel:

- Din lokale mailserver er nede.

- Der er en fejl i forbindelsens intelligente værtsindstillinger, så Microsoft 365 forsøger at oprette forbindelse til den forkerte IP-adresse.

### <a name="how-do-i-fix-error-code-450-44315"></a>Hvordan retter jeg fejlkode 450 4.4.315?

- Find ud af, hvilket scenarie der gælder for dig, og foretag de nødvendige rettelser. Hvis mailflowet f.eks. har fungeret korrekt, og du ikke har ændret indstillingerne for forbindelsen, skal du kontrollere dit lokale mailmiljø for at se, om serveren er nede, eller om der er foretaget ændringer i din netværksinfrastruktur (f.eks. har du ændret internetudbydere, så du har nu forskellige IP-adresser).

- Hvis fejlen opstår i din partnerorganisation (f.eks. en tredjepartsudbyder af serviceudbyder), skal du kontakte din partner for at løse problemet.

## <a name="error-code-450-44316-connection-refused"></a>Fejlkode: 450 4.4.316 Forbindelse nægtet

Typisk betyder denne fejl Microsoft 365 du stødte på en forbindelsesfejl, når den forsøgte at oprette forbindelse til destinationens mailserver. En sandsynlig årsag til denne fejl er, at din firewall blokerer forbindelser fra Microsoft 365 IP-adresser. Eller denne fejl kan være tilses af designet, hvis du har overført dit lokale mailsystem til Microsoft 365 og lukker dit lokale mailmiljø.

### <a name="how-do-i-fix-error-code-450-44316"></a>Hvordan retter jeg fejlkode 450 4.4.316?

- Hvis du har postkasser i dit lokale miljø, skal du ændre dine firewallindstillinger for at tillade forbindelser fra Microsoft 365 IP-adresser på TCP-port 25 til dine lokale mailservere. Du kan finde en liste over Microsoft 365 IP-adresser i [Microsoft 365 URL-adresser og IP-adresseintervaller](../../enterprise/urls-and-ip-address-ranges.md).

- Hvis der ikke bør leveres flere meddelelser til dit lokale miljø, skal du klikke på  Ret nu i advarslen, så Microsoft 365 straks kan afvise meddelelser med ugyldige modtagere. Dette vil reducere risikoen for at overskride organisationens kvote for ugyldige modtagere, hvilket kan påvirke den normale levering af meddelelser. Eller du kan bruge følgende vejledning til manuelt at løse problemet:

  - I administration Exchange skal du deaktivere eller slette den forbindelse, der leverer mail fra Microsoft 365 til dit lokale mailmiljø:

    1. I EAC på skal <https://admin.exchange.microsoft.com>du gå til **Mailflow** \> **Connectors**. For at gå direkte til **siden Forbindelser skal** du bruge <https://admin.exchange.microsoft.com/#/connectors>.

    2. Vælg forbindelsen med værdien **Fra Office 365** værdien **Til** værdien **Din organisations mailserver**, og gør et af følgende trin:
       - Slet forbindelsen ved at klikke på **ikonet** ![Slet Fjern.](../../media/adf01106-cc79-475c-8673-065371c1897b.gif)
       - Deaktiver forbindelsen ved at klikke på **Ikonet** ![Rediger redigering.](../../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) og fjerne **markeringen i Slå den til**.

  - Rediger det accepterede domæne Microsoft 365, der er knyttet til dit lokale mailmiljø fra **Intern videresendelse** **til Autoritativ**. Du kan finde en vejledning [under Administrere accepterede domæner i Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).

  **Bemærk**! Typisk tager det mellem 30 minutter og en time, før ændringerne træder i kraft. Kontrollér efter en time, at du ikke længere modtager fejlen.

- Hvis fejlen opstår i din partnerorganisation (f.eks. en tredjepartsudbyder af skybaseret serviceudbyder), skal du kontakte din partner for at løse problemet.

## <a name="error-code-450-44317-cannot-connect-to-remote-server"></a>Fejlkode: 450 4.4.317 Kan ikke oprette forbindelse til fjernserver

Typisk betyder denne fejl Microsoft 365 du har oprettet forbindelse til destinationens mailserver, men serveren har svaret med en øjeblikkelig fejl eller opfylder ikke forbindelseskravene. Fejloplysningerne forklarer problemet. Eksempel:

- Destinationens mailserver svarede med fejlen "Tjenesten er ikke tilgængelig", som angiver, at serveren ikke kan opretholde kommunikationen Microsoft 365.
- Forbindelsen er konfigureret til at kræve TLS, men destinationsmailserveren understøtter ikke TLS.

### <a name="how-do-i-fix-error-code-450-44317"></a>Hvordan retter jeg fejlkode 450 4.4.317?

- Kontrollér TLS-indstillingerne og certifikaterne på dine lokale mailservere og TLS-indstillingerne på forbindelsen.
- Hvis fejlen opstår i din partnerorganisation (f.eks. en tredjepartsudbyder af skybaseret serviceudbyder), skal du kontakte din partner for at løse problemet.

## <a name="error-code-450-44318-connection-was-closed-abruptly"></a>Fejlkode: 450 4.4.318 Forbindelse blev lukket efter dine oplysninger

Typisk betyder denne fejl Microsoft 365 at du har problemer med at kommunikere med dit lokale mailmiljø, så forbindelsen blev afbrudt. De mulige årsager til denne fejl er:

- Din firewall bruger SMTP-pakkeundersøgelsesregler, og disse regler fungerer ikke korrekt.
- Din lokale mailserver fungerer ikke korrekt (f.eks. tjenesten hænger, går ned eller lav systemressourcer), hvilket medfører, at serveren får time out og lukker forbindelsen til Microsoft 365.
- Der er netværksproblemer mellem dit lokale miljø og dit lokale Microsoft 365.

### <a name="how-do-i-fix-error-code-450-44318"></a>Hvordan retter jeg fejlkode 450 4.4.318?

- Find ud af, hvilket scenarie der gælder for dig, og foretag de nødvendige rettelser.
- Hvis problemet skyldes netværksproblemer mellem dit lokale miljø og dit lokale miljø Microsoft 365 skal du kontakte dit netværksteam for at foretage fejlfinding af problemet.
- Hvis fejlen opstår i din partnerorganisation (f.eks. en tredjepartsudbyder af skybaseret serviceudbyder), skal du kontakte din partner for at løse problemet.

## <a name="error-code-450-47320-certificate-validation-failed"></a>Fejlkode: 450 4.7.320 Certifikatvalidering mislykkedes

Typisk betyder denne fejl Microsoft 365 du stødte på en fejl under forsøget på at validere certifikatet for destinationens mailserver. Fejloplysningerne forklarer fejlen. Eksempel:

- Certifikat udløbet
- Uoverensstemmelse mellem certifikats emne
- Certifikat er ikke længere gyldigt

### <a name="how-do-i-fix-error-code-450-47320"></a>Hvordan retter jeg fejlkode 450 4.7.320?

- Ret certifikatet eller indstillingerne på forbindelsen, så meddelelser i kø i Microsoft 365 kan leveres.
- Hvis fejlen opstår i din partnerorganisation (f.eks. en tredjepartsudbyder af skybaseret serviceudbyder), skal du kontakte din partner for at løse problemet.

## <a name="other-error-codes"></a>Andre fejlkoder

Microsoft 365 har problemer med at levere meddelelser til din lokale mailserver eller partnermailserver. Brug **destinationsserveroplysningerne** i fejlen til at undersøge problemet i dit miljø, eller rediger forbindelsen, hvis der er en konfigurationsfejl.

Hvis fejlen opstår i din partnerorganisation (f.eks. en tredjepartsudbyder af skybaseret serviceudbyder), skal du kontakte din partner for at løse problemet.
