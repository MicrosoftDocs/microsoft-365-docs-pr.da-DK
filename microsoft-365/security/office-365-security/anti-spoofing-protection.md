---
title: Beskyttelse mod forfalskning
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
search.appverid:
- MET150
ms.assetid: d24bb387-c65d-486e-93e7-06a4f1a436c0
ms.collection:
- M365-security-compliance
- Strat_O365_IP
- m365initiative-defender-office365
ms.custom:
- TopSMBIssues
- seo-marvel-apr2020
ms.localizationpriority: high
description: Administratorer kan få mere at vide om de anti-spoofing-funktioner, der er tilgængelige i Exchange Online Protection (EOP), hvilket kan hjælpe med at afhjælpe phishingangreb fra forfalskede afsendere og domæner.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 446b82d668041a476d748956008002c42a92a7f3
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65435451"
---
# <a name="anti-spoofing-protection-in-eop"></a>Beskyttelse mod spoofing i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online postkasser indeholder EOP funktioner, der hjælper med at beskytte din organisation mod forfalskede afsendere.

Når det kommer til at beskytte sine brugere, tager Microsoft truslen om phishing alvorligt. Spoofing er en almindelig teknik, der bruges af hackere. **Forfalskede meddelelser stammer tilsyneladende fra en anden person eller et andet sted end den faktiske kilde**. Denne teknik bruges ofte i phishing-kampagner, der er udviklet til at hente brugerlegitimationsoplysninger. Anti-spoofing-teknologien i EOP undersøger specifikt forfalskning af headeren From i meddelelsesteksten (bruges til at vise meddelelsens afsender i mailklienter). Når EOP har stor tillid til, at headeren Fra er forfalsket, identificeres meddelelsen som forfalsket.

Følgende anti-spoofing-teknologier er tilgængelige i EOP:

- **Mailgodkendelse**: En integreret del af enhver anti-spoofing-indsats er brugen af mailgodkendelse (også kendt som mailvalidering) af SPF-, DKIM- og DMARC-poster i DNS. Du kan konfigurere disse poster for dine domæner, så destinationsmailsystemer kan kontrollere gyldigheden af meddelelser, der hævder at være fra afsendere i dine domæner. I forbindelse med indgående meddelelser kræver Microsoft 365 mailgodkendelse for afsenderdomæner. Du kan få flere oplysninger under [Mailgodkendelse i Microsoft 365](email-validation-and-authentication.md).

  EOP analyserer og blokerer meddelelser, der ikke kan godkendes ved hjælp af en kombination af standardmetoder til godkendelse af mail og teknikker til afsenderomdømme.

  :::image type="content" source="../../media/eop-anti-spoofing-protection.png" alt-text="EOP-kontrol mod spoofing" lightbox="../../media/eop-anti-spoofing-protection.png":::

- **Indsigt i spoof intelligence**: Gennemse spoofed-meddelelser fra afsendere i interne og eksterne domæner inden for de seneste 7 dage, og tillad eller bloker disse afsendere. Du kan få flere oplysninger under [Spoof intelligence-indsigt i EOP](learn-about-spoof-intelligence.md).

- **Tillad eller bloker spooferede afsendere på listen over tilladte/blokerede lejere**: Når du tilsidesætter dommen i indsigten spoof intelligence, bliver den spooferede afsender en manuel tilladelses- eller blokpost, der kun vises under fanen **Spoof** på listen over tilladte/blokerede lejere. Du kan også manuelt oprette tillad eller blokere poster for spoof-afsendere, før de registreres af spoof intelligence. Du kan få flere oplysninger under [Administrer listen over tilladte/blokerede lejere i EOP](tenant-allow-block-list.md).

- **Politikker til bekæmpelse af phishing**: I EOP og Microsoft Defender for Office 365 indeholder politikker til bekæmpelse af phishing følgende indstillinger for anti-spoofing:
  - Slå spoof intelligence til eller fra.
  - Slå ikke-godkendte afsenderindikatorer i Outlook til eller fra.
  - Angiv handlingen for blokerede spoofed afsendere.

  Du kan få flere oplysninger under [Spoof-indstillinger i politikker til bekæmpelse af phishing](set-up-anti-phishing-policies.md#spoof-settings).

  **Bemærk**! Politikker til bekæmpelse af phishing i Defender for Office 365 indeholder tilføjelsesbeskyttelse, herunder **repræsentationsbeskyttelse**. Du kan få flere oplysninger [under Eksklusive indstillinger i politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

- **Rapport over spoof registreringer**: Du kan få flere oplysninger under [Spoof Detections-rapport](view-email-security-reports.md#spoof-detections-report).

  **Bemærk**! Defender for Office 365 organisationer kan også bruge registreringer i realtid (Plan 1) eller Threat Explorer (Plan 2) til at få vist oplysninger om phishingforsøg. Du kan få flere oplysninger [under Microsoft 365 trusselsundersøgelse og -svar](office-365-ti.md).

## <a name="how-spoofing-is-used-in-phishing-attacks"></a>Sådan bruges spoofing i phishing-angreb

Efterligningsmeddelelser har følgende negative konsekvenser for brugerne:

- **Forfalskede meddelelser bedrager brugere**: En spoofed meddelelse kan narre modtageren til at klikke på et link og opgive deres legitimationsoplysninger, downloade malware eller besvare en meddelelse med følsomt indhold (kendt som en forretningsmail kompromitteret eller BEC).

  Følgende meddelelse er et eksempel på phishing, der bruger den spoofede afsenders msoutlook94@service.outlook.com:

  ![Phishingmeddelelse, der repræsenterer service.outlook.com.](../../media/1a441f21-8ef7-41c7-90c0-847272dc5350.jpg)

  Denne meddelelse kom ikke fra service.outlook.com, men hackeren forfalskede headerfeltet **Fra** for at få det til at se ud, som det gjorde. Dette var et forsøg på at narre modtageren til at klikke på **ændring af dit adgangskodelink** og opgive deres legitimationsoplysninger.

  Følgende meddelelse er et eksempel på BEC, der bruger det spoofede maildomæne contoso.com:

  ![Phishingmeddelelse – kompromitteret forretningsmail.](../../media/da15adaa-708b-4e73-8165-482fc9182090.jpg)

  Meddelelsen ser legitim ud, men afsenderen er spoofed.

- **Brugere forvirrer rigtige meddelelser for falske**: Selv brugere, der kender til phishing, kan have svært ved at se forskellene mellem rigtige meddelelser og spoofede meddelelser.

  Følgende meddelelse er et eksempel på en rigtig meddelelse om nulstilling af adgangskode fra Microsoft-sikkerhedskontoen:

  ![Microsofts legitime nulstilling af adgangskode.](../../media/58a3154f-e83d-4f86-bcfe-ae9e8c87bd37.jpg)

  Meddelelsen kom virkelig fra Microsoft, men brugerne er blevet betinget til at være mistænkelige. Da det er svært at skelne mellem en rigtig meddelelse om nulstilling af adgangskode og en falsk, kan brugerne ignorere meddelelsen, rapportere den som spam eller unødvendigt rapportere meddelelsen til Microsoft som phishing.

## <a name="different-types-of-spoofing"></a>Forskellige typer spoofing

Microsoft skelner mellem to forskellige typer spoofed-meddelelser:

- **Intra-org spoofing**: Også kendt som _selv-til-selv_ spoofing. Eksempel:

  - Afsenderen og modtageren befinder sig i det samme domæne:
    > Fra: chris@contoso.com <br> Til: michelle@contoso.com

  - Afsenderen og modtageren er i underdomæner for det samme domæne:
    > Fra: laura@marketing.fabrikam.com <br> Til: julia@engineering.fabrikam.com

  - Afsenderen og modtageren er i forskellige domæner, der tilhører den samme organisation (dvs. begge domæner er konfigureret som [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i samme organisation):
    > Fra: afsender @ microsoft.com <br> Til: modtager @ bing.com

    Spaces bruges i mailadresserne for at forhindre høst af spambot.

  Meddelelser, der ikke kan [godkende sammensat på](email-validation-and-authentication.md#composite-authentication) grund af spoofing internt i organisationen, indeholder følgende headerværdier:

  `Authentication-Results: ... compauth=fail reason=6xx`

  `X-Forefront-Antispam-Report: ...CAT:SPOOF;...SFTY:9.11`

  - `reason=6xx` angiver spoofing i organisationen.

  - SFTY er meddelelsens sikkerhedsniveau. 9 angiver phishing, .11 angiver spoofing i organisationen.

- **Spoofing på tværs af domæner**: Afsender- og modtagerdomænerne er forskellige og har ingen relation til hinanden (også kaldet eksterne domæner). Eksempel:
    > Fra: chris@contoso.com <br> Til: michelle@tailspintoys.com

  Meddelelser, der ikke kan [godkendes på](email-validation-and-authentication.md#composite-authentication) grund af spoofing på tværs af domæner, indeholder følgende headerværdier:

  `Authentication-Results: ... compauth=fail reason=000/001`

  `X-Forefront-Antispam-Report: ...CAT:SPOOF;...SFTY:9.22`

  - `reason=000` angiver, at meddelelsen mislykkedes med eksplicit mailgodkendelse. `reason=001` angiver, at meddelelsen mislykkedes med implicit mailgodkendelse.

  - `SFTY` er meddelelsens sikkerhedsniveau. 9 angiver phishing, .22 angiver spoofing på tværs af domæner.

> [!NOTE]
> Hvis du har fået en meddelelse som ***compauth=fail reason=###_** og har brug for at vide om sammensat godkendelse (compauth) og de værdier, der er relateret til spoofing, skal du se [_Anti-spammeddelelsesheadere i Microsoft 365*](anti-spam-message-headers.md). Eller gå direkte til [*årsagskoderne*](anti-spam-message-headers.md) .

Du kan få flere oplysninger om DMARC under [Brug DMARC til at validere mail i Microsoft 365](use-dmarc-to-validate-email.md).

## <a name="problems-with-anti-spoofing-protection"></a>Problemer med beskyttelse mod spoofing

Adresselister (også kaldet diskussionslister) er kendt for at have problemer med anti-spoofing på grund af den måde, de videresender og redigerer meddelelser på.

Gabriela Laureano (glaureano@contoso.com) er f.eks. interesseret i at kigge på fugle, tilmelde sig adresselisten birdwatchers@fabrikam.com og sender følgende meddelelse til listen:

> **Fra:** "Gabriela Laureano" \<glaureano@contoso.com\> <br> **Til:** Birdwatcher's diskussionsliste \<birdwatchers@fabrikam.com\> <br> **Emne:** Fantastisk visning af blå jays øverst i Mt. Rainier denne uge <p> Alle, der ønsker at tjekke ud visning i denne uge fra Mt. Rainier?

Maillisteserveren modtager meddelelsen, ændrer dens indhold og genafspiller den til listens medlemmer. Den genafspillede meddelelse har samme Fra-adresse (glaureano@contoso.com), men der føjes et mærke til emnelinjen, og der tilføjes en sidefod nederst i meddelelsen. Denne type ændring er almindelig på adresselister og kan resultere i falske positiver for spoofing.

> **Fra:** "Gabriela Laureano" \<glaureano@contoso.com\> <br> **Til:** Birdwatcher's diskussionsliste \<birdwatchers@fabrikam.com\> <br> **Om:** [BIRDWATCHERS] Fantastisk visning af blue jays øverst i Mt. Rainier denne uge <p> Alle, der ønsker at tjekke ud visning i denne uge fra Mt. Rainier? <p> Denne meddelelse blev sendt til Birdwatchers-diskussionslisten. Du kan når som helst opsige dit abonnement.

Du kan hjælpe postlistemeddelelser med at overføre anti-spoofing-kontroller ved at udføre følgende trin, afhængigt af om du styrer adresselisten:

- Din organisation ejer adresselisten:

  - Tjek ofte stillede spørgsmål på DMARC.org: [Jeg driver en adresseliste, og jeg ønsker at samarbejde med DMARC, hvad skal jeg gøre?](https://dmarc.org/wiki/FAQ#I_operate_a_mailing_list_and_I_want_to_interoperate_with_DMARC.2C_what_should_I_do.3F).

  - Læs vejledningen i dette blogindlæg: [Et tip til postlisteoperatorer for at kunne samarbejde med DMARC for at undgå fejl](/archive/blogs/tzink/a-tip-for-mailing-list-operators-to-interoperate-with-dmarc-to-avoid-failures).

  - Overvej at installere opdateringer på maillisteserveren for at understøtte ARC, se <http://arc-spec.org>.

- Din organisation ejer ikke adresselisten:

  - Bed vedligeholderen af adresselisten om at konfigurere mailgodkendelse for det domæne, som adresselisten videresender fra.

    Når der er nok afsendere til at svare domæneejere om, at de skal konfigurere mailgodkendelsesposter, bliver de ansporet til at handle. Selvom Microsoft også arbejder sammen med domæneejere om at publicere de påkrævede poster, hjælper det endnu mere, når individuelle brugere anmoder om det.

  - Opret indbakkeregler i din mailklient for at flytte meddelelser til indbakken. Du kan også bede dine administratorer om at konfigurere tilsidesættelser som beskrevet i [Indsigt i Spoof intelligence i EOP](learn-about-spoof-intelligence.md) og [administrere listen over tilladte/blokerede lejere](tenant-allow-block-list.md).

  - Brug listen over tilladte/blokerede lejere til at oprette en tilsidesættelse af adresselisten for at behandle den som legitim. Du kan få flere oplysninger under [Tilføj tillader på listen over tilladte/blokerede lejere](manage-tenant-allows.md).

Hvis alt andet mislykkes, kan du rapportere meddelelsen som en falsk positiv til Microsoft. Du kan få flere oplysninger under [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="considerations-for-anti-spoofing-protection"></a>Overvejelser i forbindelse med beskyttelse mod spoofing

Hvis du er administrator, og du i øjeblikket sender meddelelser til Microsoft 365, skal du sikre dig, at din mail er godkendt korrekt. Ellers kan det være markeret som spam eller phishing. Du kan finde flere oplysninger under [Løsninger til legitime afsendere, der sender ikke-godkendte mails](email-validation-and-authentication.md#solutions-for-legitimate-senders-who-are-sending-unauthenticated-email).

Afsendere i en enkelt brugers (eller administrators) Pengeskab afsenderliste tilsidesætter dele af filtreringsstakken, herunder spoof-beskyttelse. Du kan få flere oplysninger [under Outlook Pengeskab Afsendere](create-safe-sender-lists-in-office-365.md#use-outlook-safe-senders).

Administratorer bør undgå (når det er muligt) at bruge tilladte afsenderlister eller tilladte domænelister. Disse afsendere tilsidesætter al spam, spoofing og phishing-beskyttelse samt afsendergodkendelse (SPF, DKIM, DMARC). Du kan få flere oplysninger under [Brug lister over tilladte afsendere eller tilladte domænelister](create-safe-sender-lists-in-office-365.md#use-allowed-sender-lists-or-allowed-domain-lists).
