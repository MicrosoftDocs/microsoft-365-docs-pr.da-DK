---
title: Beskyttelse mod spoofing
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
description: Administratorer kan få mere at vide om de antipoofing-funktioner, der er tilgængelige i Exchange Online Protection (EOP), som kan hjælpe med at reducere phishingangreb fra forfalskede afsendere og domæner.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 140ed15b793b5d6b74b39a35b854b7432a658bc3
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475163"
---
# <a name="anti-spoofing-protection-in-eop"></a>Beskyttelse mod spoofing i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser, indeholder EOP funktioner, der beskytter din organisation mod forfalskede (forfalskede) afsendere.

Når det drejer sig om at beskytte brugerne, tager Microsoft truslen om phishing alvorligt. Spoofing er en almindelig teknik, der bruges af hackere. **Spoofed meddelelser ser ud til at komme fra en person eller et andet sted end den faktiske kilde**. Denne metode bruges ofte i phishingkampagner, der er beregnet til at hente brugerlegitimationsoplysninger. Antispoofing-teknologien i EOP undersøger specifikt forfalskning af brevhovedet Fra i meddelelsesteksten (bruges til at vise meddelelsens afsender i mailklienter). Når EOP har høj tillid til, at brevhovedet Fra er forfalsket, identificeres meddelelsen som forfalsket.

Følgende antispoofing-teknologier er tilgængelige i EOP:

- **Mailgodkendelse**: En integreret del af enhver antispoofingindsats er brug af mailgodkendelse (også kaldet mailvalidering) af SPF-, DKIM- og DMARC-poster i DNS. Du kan konfigurere disse poster for dine domæner, så destinationens mailsystemer kan kontrollere gyldigheden af meddelelser, der hævder at være fra afsendere på dine domæner. For indgående meddelelser kræver Microsoft 365 mailgodkendelse for afsenderdomæner. Du kan finde flere oplysninger [under Mailgodkendelse i Microsoft 365](email-validation-and-authentication.md).

  EOP analyserer og blokerer meddelelser, der ikke kan godkendes ved en kombination af standardmetode til mailgodkendelse og teknikker til afsender ry.

  :::image type="content" source="../../media/eop-anti-spoofing-protection.png" alt-text="EOP-kontrol mod spoofing" lightbox="../../media/eop-anti-spoofing-protection.png":::

- **Efterlignet intelligensindsigt**: Gennemse efterlignede meddelelser fra afsendere i interne og eksterne domæner i løbet af de seneste 7 dage, og tillad eller bloker disse afsendere. Du kan finde flere oplysninger [under Efterlignet intelligensindsigt i EOP](learn-about-spoof-intelligence.md).

- **Tillad eller bloker spoof-afsendere på lejerens tilladelses- eller blokeringsliste**: Når du tilsidesætter konklusionen i spoof intelligence-indsigten, bliver den spooferede afsender til en manuel tillad eller bloker post, der kun vises på fanen **Spoof** på lejerens tilladelses-/blokeringsliste. Du kan også manuelt oprette tillade eller blokere poster for spoof afsendere, før de registreres af efterlignet intelligens. Få mere at vide under [Administrer lejerens tilladelses-/blokeringsliste i EOP](tenant-allow-block-list.md).

- **Antiphishing-politikker**: I EOP og Microsoft Defender for Office 365 indeholder antiphishing-politikker følgende antispoofing-indstillinger:
  - Slå efterlignet intelligens til eller fra.
  - Slå ikke-godkendt afsenderidentifikation i Outlook til eller fra.
  - Angiv handlingen for blokerede efterlignede afsendere.

  Du kan finde flere oplysninger [under Indstillinger for spoof i antiphishing-politikker](set-up-anti-phishing-policies.md#spoof-settings).

  **Bemærk**! Antiphishing-politikker i Defender for Office 365 indeholder tilføjelsesbeskyttelse, herunder **repræsentationsbeskyttelse**. Du kan finde flere oplysninger [under Eksklusive indstillinger i antiphishing-politikker i Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

- **Rapport over spoof-registreringer**: Du kan finde flere oplysninger i [Rapporten Spoof-registreringer](view-email-security-reports.md#spoof-detections-report).

  **Bemærk**: Defender for Office 365 organisationer kan også bruge registreringer i realtid (Plan 1) eller Threat Explorer (Plan 2) til at få vist oplysninger om forsøg på phishing. Du kan finde flere oplysninger [Microsoft 365 undersøgelse af trusler og svar](office-365-ti.md).

## <a name="how-spoofing-is-used-in-phishing-attacks"></a>Sådan bruges spoofing i phishing-angreb

Spoofing-meddelelser har følgende negative konsekvenser for brugerne:

- **Spoofed messages deceive users**: A spoof message might trick the recipient into clicking a link and give up their credentials, downloading malware, or replying to a message with sensitive content (known as a business email compromise or BEC).

  Følgende meddelelse er et eksempel på phishing, der bruger forfalskede afsendere msoutlook94@service.outlook.com:

  ![Phishingmeddelelse, der service.outlook.com.](../../media/1a441f21-8ef7-41c7-90c0-847272dc5350.jpg)

  Denne meddelelse kommer ikke fra en service.outlook.com, men hackeren spoofed feltet **Fra** for at få det til at se ud som om, den gjorde. Dette var et forsøg på at narre modtageren til at klikke på linket til at **ændre adgangskoden** og afgive sine legitimationsoplysninger.

  Følgende meddelelse er et eksempel på BEC, der bruger det spoofede maildomæne contoso.com:

  ![Phishing-meddelelse – kompromis med virksomhedsmail.](../../media/da15adaa-708b-4e73-8165-482fc9182090.jpg)

  Meddelelsen ser legitim ud, men afsenderen er efterlignet.

- **Brugere bliver forvirret af falske** meddelelser: Selv brugere, der kender til phishing, kan have svært ved at se forskellene mellem rigtige meddelelser og falske meddelelser.

  Følgende meddelelse er et eksempel på en rigtig meddelelse om nulstilling af adgangskode fra Microsoft Security-kontoen:

  ![Nulstilling af microsoft-legitim adgangskode.](../../media/58a3154f-e83d-4f86-bcfe-ae9e8c87bd37.jpg)

  Meddelelsen er i virkeligheden kommet fra Microsoft, men brugerne er blevet betingelsen om at være mistænkelige. Da det er svært at skelne mellem en rigtig meddelelse til nulstilling af adgangskode og en falsk meddelelse, kan brugerne ignorere meddelelsen, rapportere den som spam eller unødvendigt rapportere meddelelsen til Microsoft som phishing.

## <a name="different-types-of-spoofing"></a>Forskellige typer spoofing

Microsoft skelner mellem to forskellige typer af efterlignede meddelelser:

- **Intra-org spoofing**: Also known _as self-to-self_ spoofing. Eksempel:

  - Afsenderen og modtageren er i det samme domæne:
    > Fra: chris@contoso.com <br> Hvis du vil: michelle@contoso.com

  - Afsenderen og modtageren er i underdomæner af samme domæne:
    > Fra: laura@marketing.fabrikam.com <br> Hvis du vil: julia@engineering.fabrikam.com

  - Afsenderen og modtageren er på forskellige domæner, der tilhører den samme organisation (det vil sige, at begge domæner er konfigureret som accepterede [domæner i samme](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) organisation):
    > Fra: sender @ microsoft.com <br> Til: modtager @ bing.com

    Mellemrum bruges i mailadresserne til at forhindre indsamling af spambot.

  Meddelelser, der [ikke indeholder sammensat](email-validation-and-authentication.md#composite-authentication) godkendelse på grund af intra-org spoofing, indeholder følgende overskriftsværdier:

  `Authentication-Results: ... compauth=fail reason=6xx`

  `X-Forefront-Antispam-Report: ...CAT:SPOOF;...SFTY:9.11`

  - `reason=6xx` angiver intra-org-spoofing.

  - SFTY er meddelelsens sikkerhedsniveau. 9 angiver phishing, 0,11 angiver intra-org spoofing.

- **Spoofing på tværs af domæner**: Afsender- og modtagerdomænerne er forskellige og har ingen relation til hinanden (også kaldet eksterne domæner). Eksempel:
    > Fra: chris@contoso.com <br> Hvis du vil: michelle@tailspintoys.com

  Meddelelser, der [ikke indeholder sammensat](email-validation-and-authentication.md#composite-authentication) godkendelse på grund af spoofing på tværs af domæner, indeholder følgende brevhovedværdier:

  `Authentication-Results: ... compauth=fail reason=000/001`

  `X-Forefront-Antispam-Report: ...CAT:SPOOF;...SFTY:9.22`

  - `reason=000` angiver, at meddelelsen ikke kunne eksplicit mailgodkendelse. `reason=001` angiver, at meddelelsen ikke kunne bruges til implicit mailgodkendelse.

  - `SFTY` er meddelelsens sikkerhedsniveau. 9 angiver phishing. 22 angiver spoofing på tværs af domæner.

> [!NOTE]
> Hvis du har fået en meddelelse som ***compauth=fail reason=##_** og har brug for at vide om sammensat godkendelse (compauth) og de værdier, der er relateret til spoofing, skal du se [_Anti-spam-meddelelsesoverskrifter i Microsoft 365*](anti-spam-message-headers.md). Eller gå direkte til [*årsagskoderne*](anti-spam-message-headers.md) .

Du kan finde flere oplysninger om DMARC i [Brug DMARC til at validere mail Microsoft 365](use-dmarc-to-validate-email.md).

## <a name="problems-with-anti-spoofing-protection"></a>Problemer med beskyttelse mod spoofing

Adresselister (også kaldet diskussionslister) er kendt for at have problemer med uønsket spoofing på grund af måden, hvorpå de videresender og redigerer meddelelser.

Gabriela Laureano (glaureano@contoso.com) er f.eks. interesseret i fuglekigge, deltager i birdwatchers@fabrikam.com og sender følgende meddelelse til listen:

> **Fra:** "Gabriela Laureano" \<glaureano@contoso.com\> <br> **Hvis du vil:** Fugleurets diskussionsliste \<birdwatchers@fabrikam.com\> <br> **Emne:** Fantastisk visning af blå havblå øverst i Mt. Rainier denne uge <p> Alle, der vil tjekke visningen denne uge fra Mt. Rainier?

Adresselisteserveren modtager meddelelsen, ændrer dens indhold og afspiller det igen til medlemmerne af listen. Den genafspilte meddelelse har den samme Fra-adresse (glaureano@contoso.com), men et mærke føjes til emnelinjen, og der tilføjes en sidefod nederst i meddelelsen. Denne type ændring er almindelig på adresselister, og kan resultere i falske positive for spoofing.

> **Fra:** "Gabriela Laureano" \<glaureano@contoso.com\> <br> **Hvis du vil:** Fugleurets diskussionsliste \<birdwatchers@fabrikam.com\> <br> **Emne:** [BIRDWATCHERS] Fantastisk visning af blå seere øverst i Mt. Rainier denne uge <p> Alle, der vil tjekke visningen denne uge fra Mt. Rainier? <p> Denne meddelelse blev sendt til Birdwatchers-diskussionslisten. Det er gratis, og du kan afmelde dig til hver en tid.

For at hjælpe adresselistemeddelelser med at bestå antispoofingkontroller skal du udføre følgende trin, afhængigt af om du styrer adresselisten:

- Din organisation ejer adresselisten:

  - Se ofte stillede spørgsmål DMARC.org: Jeg arbejder med en adresseliste, og jeg vil arbejde sammen med [DMARC, hvad skal jeg gøre?](https://dmarc.org/wiki/FAQ#I_operate_a_mailing_list_and_I_want_to_interoperate_with_DMARC.2C_what_should_I_do.3F).

  - Læs instruktionerne i dette blogindlæg: Et tip til adresselisteoperatorer til at fungere sammen med [DMARC for at undgå fejl](/archive/blogs/tzink/a-tip-for-mailing-list-operators-to-interoperate-with-dmarc-to-avoid-failures).

  - Overvej at installere opdateringer på adresselisteserveren for at understøtte ARC under <http://arc-spec.org>.

- Din organisation ejer ikke adresselisten:

  - Bed vedligeholderen af adresselisten om at konfigurere mailgodkendelse for det domæne, som adresselisten videresender fra.

    Når nok afsendere svarer tilbage til domæneejere, at de skal konfigurere mailgodkendelsesposter, bliver de sendt til handling. Microsoft arbejder også sammen med domæneejere om at publicere de nødvendige poster, men det hjælper endnu mere, når individuelle brugere anmoder om det.

  - Opret indbakkeregler i din mailklient for at flytte meddelelser til indbakken. Du kan også bede dine administratorer om at konfigurere tilsidesættelser, sådan som det er beskrevet i Efterlignet intelligensindsigt i [EOP](learn-about-spoof-intelligence.md) og Administrer lejerens [tilladelses-/blokeringsliste](tenant-allow-block-list.md).

  - Brug lejerens tilladelses-/blokeringsliste til at oprette en tilsidesættelse af adresselisten for at behandle den som legitim. Du kan få mere at vide [under Tilføj tillader på lejerens tilladelses-/blokeringsliste](manage-tenant-allows.md).

Hvis intet andet virker, kan du rapportere meddelelsen som en falsk positiv til Microsoft. Få mere at vide under [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="considerations-for-anti-spoofing-protection"></a>Overvejelser i forbindelse med beskyttelse mod spoofing

Hvis du er administrator og i øjeblikket sender meddelelser til Microsoft 365, skal du sikre dig, at din mail er godkendt korrekt. Ellers kan det være markeret som spam eller phishing. Du kan finde flere [oplysninger under Løsninger til legitime afsendere, der sender ikke-godkendt mail](email-validation-and-authentication.md#solutions-for-legitimate-senders-who-are-sending-unauthenticated-email).

Afsendere i en enkelt brugers (eller administrators) liste over Pengeskab afsendere tilsidesætter dele af filtreringsstakken, herunder spoof-beskyttelse. Du kan finde flere oplysninger [Outlook Pengeskab Afsendere](create-safe-sender-lists-in-office-365.md#use-outlook-safe-senders).

Administratorer skal (når det er muligt) undgå at bruge lister over tilladte afsendere eller tilladte domæner. Disse afsendere tilsidesætter al spam, spoofing og phishingbeskyttelse samt afsendergodkendelse (SPF, DKIM, DMARC). Få mere at vide under [Brug lister over tilladte afsendere eller tilladte domæner](create-safe-sender-lists-in-office-365.md#use-allowed-sender-lists-or-allowed-domain-lists).
