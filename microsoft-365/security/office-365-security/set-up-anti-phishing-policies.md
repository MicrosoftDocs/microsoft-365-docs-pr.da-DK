---
title: Antiphishing-politikker
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
ms.assetid: 5a6f2d7f-d998-4f31-b4f5-f7cbf6f38578
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om de antiphishing-politikker, der er tilgængelige i Exchange Online Protection (EOP) og Microsoft Defender Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 899a76fac01c6058d5642cb52af5a6e8fb7d11ee
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63589152"
---
# <a name="anti-phishing-policies-in-microsoft-365"></a>Antiphishing-politikker i Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Politikker til konfiguration af antiphishing-beskyttelse er tilgængelige i Microsoft 365-organisationer med Exchange Online-postkasser, enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser og Microsoft Defender til Office 365 organisationer.

Eksempler på Microsoft Defender til Office 365 organisationer omfatter:

- Microsoft 365 Enterprise E5, Microsoft 365 Education A5 osv.
- [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise/home)
- [Microsoft 365 Business](https://www.microsoft.com/microsoft-365/business)
- [Microsoft Defender til Office 365 som et tilføjelsesprogrammet](https://products.office.com/exchange/advance-threat-protection)

De høje forskelle mellem antiphishing-politikker i EOP og antiphishing-politikker i Defender for Office 365 er beskrevet i følgende tabel:

<br>

****

|Funktion|Antiphishing-politikker i EOP|Antiphishing-politikker i Defender til Office 365|
|---|:---:|:---:|
|Automatisk oprettet standardpolitik|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|
|Opret brugerdefinerede politikker|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|
|Almindelige politikindstillinger<sup>\*</sup>|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|
|Spoof-indstillinger|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|
|Første kontakt sikkerhedstip|![Markering.](../../media/checkmark.png)|![Markering](../../media/checkmark.png)|
|Indstillinger for repræsentation||![Markering](../../media/checkmark.png)|
|Avancerede grænseværdier for phishing||![Markering](../../media/checkmark.png)|
|

<sup>\*</sup> I standardpolitikken er politikkens navn og beskrivelse skrivebeskyttet (beskrivelsen er tom), og du kan ikke angive, hvem politikken gælder for (standardpolitikken gælder for alle modtagere).

Hvis du vil konfigurere antiphishing-politikker, skal du se følgende artikler:

- [Konfigurer antiphishing-politikker i EOP](configure-anti-phishing-policies-eop.md)
- [Konfigurer antiphishing-politikker i Microsoft Defender til Office 365](configure-mdo-anti-phishing-policies.md)

Resten af denne artikel beskriver de indstillinger, der er tilgængelige i antiphishing-politikker i EOP og Defender for Office 365.

## <a name="common-policy-settings"></a>Almindelige politikindstillinger

Følgende politikindstillinger er tilgængelige i antiphishing-politikker i EOP og Defender til Office 365:

- **Navn**: Du kan ikke omdøbe standardpolitikken for phishing. Når du har oprettet en brugerdefineret politik for phishing, kan du ikke omdøbe politikken i Microsoft 365 Defender portal.

- **Beskrivelse** Du kan ikke føje en beskrivelse til standardpolitikken for phishing, men du kan tilføje og ændre beskrivelsen af brugerdefinerede politikker, du opretter.

- **Brugere, grupper og domæner: Identificerer** interne modtagere, som politikken mod phishing gælder for. Denne værdi er påkrævet i brugerdefinerede politikker og er ikke tilgængelig i standardpolitikken (standardpolitikken gælder for alle modtagere).

  Du kan kun bruge en betingelse eller undtagelse én gang, men du kan angive flere værdier for betingelsen eller undtagelsen. Flere værdier af samme betingelse eller undtagelse bruger ELLER-logik (f.eks. _\<recipient1\>_ eller _\<recipient2\>_). Forskellige betingelser eller undtagelser bruger AND-logik (f.eks. _\<recipient1\>_ og _\<member of group 1\>_).

  - **Brugere**: En eller flere postkasser, mailbrugere eller mailkontakter i organisationen.
  - **Grupper**: En eller flere grupper i organisationen.
  - **Domæner**: Et eller flere af de konfigurerede [accepterede domæner i](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) Microsoft 365.

  - **Udelad disse brugere, grupper og domæner**: Undtagelser for politikken. Indstillingerne og funktionsmåden er nøjagtig som betingelserne:
    - **Brugere**
    - **Grupper**
    - **Domæner**

  > [!NOTE]
  > Der kræves mindst ét valg i indstillingerne brugere, grupper og domæner i brugerdefinerede antiphishing-politikker for at identificere de **meddelelsesmodtagere**,  <u>som politikken gælder for</u>. Antiphishing-politikker i Defender til Office 365 har også <u>repræsentationsindstillinger</u>, hvor du kan angive mailadresser eller afsenderdomæner til individuelle afsendere, der skal beskyttes efterligning som beskrevet senere i denne artikel.[](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)

## <a name="spoof-settings"></a>Spoof-indstillinger

Spoofing er, når Fra-adressen i en mail (afsenderadressen, der vises i mailklienter) ikke stemmer overens med domænet for mailkilden. Du kan finde flere oplysninger om spoofing [under Beskyttelse mod spoofing Microsoft 365](anti-spoofing-protection.md).

Følgende spoof-indstillinger er tilgængelige i antiphishing-politikker i EOP og Defender Office 365:

- **Aktivér efterlignet intelligens**: Slår efterlignet intelligens til eller fra. Vi anbefaler, at du lader den være slået til.

  Når efterlignet intelligens er aktiveret, viser spoof-intelligensindsigtet **spoof** afsendere, der blev registreret og tilladt eller blokeret af efterlignet intelligens. Du kan manuelt tilsidesætte efterlignet intelligenss konklusion om at tillade eller blokere den registrerede spoofed afsendere fra indsigten. Men når du gør det, forsvinder den efterlignede afsender fra efterlignet intelligens indsigt og er nu kun synlig på fanen **Spoof** i lejerens tilladelses-/blokeringsliste. Du kan også manuelt oprette tillade eller blokere poster for efterlignede afsendere på lejerens tilladelses-/blokeringsliste. Du kan finde flere oplysninger i følgende artikler:

  - [Efterlignet intelligensindsigt i EOP](learn-about-spoof-intelligence.md)
  - [Administrer lejerens tilladelses-/blokeringsliste i EOP](tenant-allow-block-list.md)

  > [!NOTE]
  >
  > - Beskyttelse mod spoofing er aktiveret som standard i standardpolitikken for phishing og i eventuelle nye brugerdefinerede antiphishing-politikker, du opretter.
  > - Du behøver ikke at deaktivere beskyttelse mod spoofing, hvis din MX-post ikke peger på Microsoft 365. Du skal i stedet aktivere Udvidet filtrering for forbindelser. Du kan finde en [vejledning under Udvidet filtrering for forbindelser i Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).
  > - Deaktivering af beskyttelse mod spoofing deaktiverer kun _implicit_ spoofingbeskyttelse fra [sammensatte godkendelseskontroller](email-validation-and-authentication.md#composite-authentication) . Hvis afsenderen ikke eksplicit _kontrollerer_[,](use-dmarc-to-validate-email.md) hvor politikken er indstillet til at sætte i karantæne eller afvise den, er meddelelsen stadig sat i karantæne eller afvist.

- **Ikke-godkendte afsendermeddelelser: Disse** meddelelser er kun tilgængelige, når efterlignet intelligens er slået til. Se oplysningerne i næste afsnit.
- **Handlinger**: For meddelelser fra blokerede efterlignede afsendere (automatisk blokeret af efterlignet intelligens eller manuelt blokeret på lejerens liste over tilladte/blokerede afsendere) kan du også angive den handling, der skal sker på meddelelserne:
  - **Flyt meddelelser til modtagernes mapper med uønsket mail**: Dette er standardværdien. Meddelelsen leveres til postkassen og flyttes til mappen Uønsket mail. Du kan finde flere oplysninger [i Konfigurere indstillinger for uønsket mail Exchange Online postkasser i Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).
  - **Sæt meddelelsen i karantæne**: Sender meddelelsen til karantæne i stedet for de tilsigtede modtagere. Du kan finde oplysninger om karantæne i følgende artikler:
    - [Karantæne i Microsoft 365](quarantine-email-messages.md)
    - [Administrer meddelelser og filer i karantæne som administrator i Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Find og slip meddelelser, der er sat i karantæne, som en bruger i Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

    Hvis du vælger **Karantæne i meddelelsen**, kan du også vælge den karantænepolitik, der gælder for meddelelser, der er sat i karantæne af efterlignet intelligensbeskyttelse. Karantænepolitikker definerer, hvad brugerne kan gøre for meddelelser, der er sat i karantæne, og om brugerne modtager beskeder om karantæne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).

### <a name="unauthenticated-sender"></a>Ikke-godkendt afsender

Meddelelser om ikke-godkendte afsendere er en del af [Spoof-indstillingerne](#spoof-settings), der er tilgængelige i antiphishing-politikker i EOP og Defender Office 365 som beskrevet i forrige afsnit. Følgende indstillinger er kun tilgængelige, når efterlignet intelligens er slået til:

- **Vis (?) for** ikke-godkendte afsendere for spoof: Denne meddelelse føjer et spørgsmålstegn til afsenderens billede i feltet Fra, hvis meddelelsen ikke passerer SPF- eller DKIM-kontroller, og meddelelsen ikke  passerer DMARC eller [ikke-sammensat godkendelse](email-validation-and-authentication.md#composite-authentication). Når denne indstilling er slået fra, føjes spørgsmålstegnet ikke til afsenderens billede.

- Vis **"via"**-mærket?: Denne meddelelse tilføjer via-mærket (chris@contoso.com <u>via</u> fabrikam.com) i feltet Fra, hvis domænet i Fra-adressen (meddelelsesafsenderen, der vises i mailklienter) er forskelligt fra domænet i DKIM-signaturen eller **MAIL FRA-adressen**. Du kan finde flere oplysninger om disse adresser [i En oversigt over mailstandarder](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

Hvis du vil forhindre, at spørgsmålstegnet eller via-mærket føjes til meddelelser fra bestemte afsendere, har du følgende muligheder:

- Tillad spoof-afsenderen i [efterlignet intelligensindsigt](learn-about-spoof-intelligence.md) eller manuelt på [lejerens tilladelses-/blokeringsliste](tenant-allow-block-list.md). Hvis du tillader, at den spooferede afsender forhindrer via-mærket i at blive vist i meddelelser fra afsenderen, når ikke-godkendt afsenderidentifikation er deaktiveret.
- [Konfigurere mailgodkendelse](email-validation-and-authentication.md#configure-email-authentication-for-domains-you-own) for afsenderdomænet.
  - For spørgsmålstegnet i afsenderens billede er SPF eller DKIM det vigtigste.
  - For via-mærket skal du bekræfte, at domænet i DKIM-signaturen eller **MAIL FROM-adressen** svarer til (eller er et underdomæne af) domænet i Fra-adressen.

Få mere at vide under [Identificer mistænkelige meddelelser på Outlook.com og Outlook på internettet](https://support.microsoft.com/office/3d44102b-6ce3-4f7c-a359-b623bec82206)

## <a name="first-contact-safety-tip"></a>Første kontakt sikkerhedstip

Indstillingerne **vis første kontaktoplysninger sikkerhedstip** findes i EOP og Defender til Office 365-organisationer og er ikke afhængig af efterlignet intelligens eller indstillinger for repræsentationsbeskyttelse. Den sikkerhedstip vises til modtagerne i følgende scenarier:

- Første gang der vises en meddelelse fra en afsender
- De modtager ikke ofte meddelelser fra afsenderen.

![Første kontakt sikkerhedstip meddelelser med én modtager.](../../media/safety-tip-first-contact-one-recipient.png)

![Første kontakt sikkerhedstip meddelelser med flere modtagere.](../../media/safety-tip-first-contact-multiple-recipients.png)

Denne funktion tilføjer et ekstra lag af sikkerhedsbeskyttelse mod potentielle efterligning angreb, så vi anbefaler, at du slår den til.

Den første kontakt sikkerhedstip erstatter også behovet for at oprette regler for mailflow (også kaldet transportregler), der tilføjer sidehovedet **X-MS-Exchange-EnableFirstContactSafetyTip** med værdien Aktivér meddelelser (selvom denne egenskab stadig  er tilgængelig).

> [!NOTE]
> Hvis meddelelsen har flere modtagere, om tippet vises, og til hvem der er baseret på en flertalsmodel. Hvis størstedelen af modtagerne aldrig eller ikke ofte modtager meddelelser fra afsenderen, modtager de påvirkede modtagere tippet Nogle, der har modtaget **denne meddelelse.** Hvis du er bekymret for, at denne adfærd blotlægger den ene modtagers kommunikationsvaner til en anden, bør du ikke aktivere den første sikkerhedstip og fortsætte med at bruge regler for mailflow i stedet.

## <a name="exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Eksklusive indstillinger i antiphishing-politikker i Microsoft Defender til Office 365

I dette afsnit beskrives de politikindstillinger, der kun er tilgængelige i antiphishing-politikker i Defender Office 365.

> [!NOTE]
> Standardpolitikken for phishing i Defender til Office 365 giver [efterlignet beskyttelse](set-up-anti-phishing-policies.md#spoof-settings) og postkasseintelligens til alle modtagere. Men de andre tilgængelige funktioner [til repræsentationsbeskyttelse](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) og [avancerede indstillinger](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365) er ikke konfigureret eller aktiveret i standardpolitikken. Hvis du vil aktivere alle beskyttelsesfunktioner, skal du ændre standardpolitikken for phishing eller oprette flere antiphishing-politikker.

### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Indstillinger for efterligning i antiphishing-politikker i Microsoft Defender Office 365

Efterligning er der, hvor afsenderen eller afsenderens maildomæne i en meddelelse ligner en rigtig afsender eller et rigtigt domæne:

- Et eksempel på efterligning af domænet contoso.com er ćóntoso.com.
- Bruger efterligning er kombinationen af brugerens viste navn og mailadresse. Valeria Barrios (vbarrios@contoso.com) kan f.eks. være efterlignet som Valeria Barrios, men med en helt anden mailadresse.

> [!NOTE]
> Repræsentationsbeskyttelse søger efter domæner, der ligner hinanden. Hvis dit domæne f.eks. er contoso.com, søger vi efter forskellige topdomæner (.com, .biz osv.) som repræsentationsforsøg, men også domæner, der i nogen grad ligner hinanden. Eksempler på contosososo.com eller contoabcdef.com kan ses som forsøg på at efterligne contoso.com.

Et efterligning af domæne kan ellers betragtes som legitimt (registreret domæne, konfigurerede mailgodkendelsesposter osv.), bortset fra at dets formål er at bedrage modtagere.

Følgende repræsentationsindstillinger er kun tilgængelige i antiphishing-politikker i Defender til Office 365:

- **Giv brugerne mulighed for at** beskytte: Forhindrer, at de angivne interne eller eksterne mailadresser bliver **efterligning som meddelelsesafsendere**. Du modtager f.eks. en mail fra vicedirektøren for din virksomhed, der beder dig sende hende nogle interne firmaoplysninger. Ville du gøre det? Mange personer ville sende svaret uden at tænke dig om.

  Du kan bruge beskyttede brugere til at tilføje interne og eksterne mailadresser for at beskytte mod efterligning. Denne liste over  afsendere, der er beskyttet mod bruger efterligning, er forskellig fra listen  over modtagere, som politikken gælder for (alle modtagere af standardpolitikken; bestemte modtagere som konfigureret i indstillingen Brugere **,** grupper og domæner i sektionen Fælles politikindstillinger).[](#common-policy-settings)

  > [!NOTE]
  >
  > - I hver antiphishingpolitik kan du angive maksimalt 350 beskyttede brugere (afsendermailadresser). Du kan ikke angive den samme beskyttede bruger i flere politikker. Så uanset hvor mange politikker der gælder for en modtager, er det maksimale antal beskyttede brugere (afsendermailadresser) for hver enkelt modtager 350. Du kan finde flere oplysninger om prioritet af politikker, og hvordan behandling af politikker stopper, når den første politik er anvendt, under Rækkefølge [og prioritering af mailbeskyttelse](how-policies-and-protections-are-combined.md).
  > - Beskyttelse af bruger efterligning fungerer ikke, hvis afsenderen og modtageren tidligere har kommunikeret via mail. Hvis afsenderen og modtageren aldrig har kommunikeret via mail, identificeres meddelelsen som et forsøg på efterligning.

  Som standard er ingen afsendermailadresser konfigureret til beskyttelse mod efterligning i **Brugere for at beskytte.** Derfor er ingen afsendermailadresser som standard dækket af beskyttelse mod efterligning, hverken i standardpolitikken eller i brugerdefinerede politikker.

  Når du føjer interne eller eksterne mailadresser til  listen Brugere for at beskytte, bliver meddelelser fra disse afsendere underlagt kontrol af **repræsentationsbeskyttelse**. Meddelelsen kontrolleres for efterligning,  hvis meddelelsen sendes til en modtager,  som politikken gælder for (alle modtagere af standardpolitikken; **Brugere, grupper og domæner modtagere** i brugerdefinerede politikker). Hvis der registreres repræsentation i afsenderens mailadresse, anvendes handlingerne til repræsentationsbeskyttelse for brugerne på meddelelsen (hvad skal der gøre med meddelelsen, om der skal vises sikkerhedstip som efterligninger osv.).

- **Aktivér domæner, der skal** beskyttes: Forhindrer, at de angivne domæner bliver efterligning **i meddelelsens afsenders domæne**. For eksempel alle domæner, som du [ejer (accepterede](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) domæner) eller bestemte brugerdefinerede domæner (domæner, du ejer eller partnerdomæner). Denne liste over  afsenderdomæner, der er beskyttet mod efterligning, er forskellig fra listen  over modtagere, som politikken gælder for (alle modtagere af standardpolitikken; bestemte modtagere som konfigureret i indstillingen Brugere **,** grupper og domæner i sektionen Fælles politikindstillinger).[](#common-policy-settings)

  > [!NOTE]
  > Det maksimale antal beskyttede domæner, som du kan definere i alle antiphishing-politikker, er 50.

  Som standard er ingen afsenderdomæner konfigureret til repræsentationsbeskyttelse i **Aktivér domæner at beskytte**. Derfor er ingen afsenderdomæner som standard dækket af beskyttelse efterligning, hverken i standardpolitikken eller i brugerdefinerede politikker.

  Når du føjer domæner til listen  Aktivér domæner for at beskytte, bliver meddelelser  fra afsendere på disse domæner underlagt kontrol af repræsentationsbeskyttelse. Meddelelsen kontrolleres for efterligning,  hvis meddelelsen sendes til en modtager,  som politikken gælder for (alle modtagere af standardpolitikken; **Brugere, grupper og domæner modtagere** i brugerdefinerede politikker). Hvis efterligning registreres i afsenderens domæne, anvendes efterligningbeskyttelseshandlingerne for domæner på meddelelsen (hvad du skal gøre med meddelelsen, om du skal vise sikkerhedstip for efterligninger af brugere osv.).

- **Handlinger**: Vælg den handling, der skal udføre på indgående meddelelser, der indeholder efterligningsforsøg mod de beskyttede brugere og beskyttede domæner i politikken. Du kan angive forskellige handlinger for efterligning af beskyttede brugere vs. efterligning af beskyttede domæner:
  - **Anvend ikke nogen handling**
  - **Omdiriger meddelelse til andre** mailadresser: Sender meddelelsen til de angivne modtagere i stedet for til de tilsigtede modtagere.
  - **Flyt meddelelser til modtagernes mapper med** uønsket mail: Meddelelsen leveres til postkassen og flyttes til mappen Uønsket mail. Du kan finde flere oplysninger [i Konfigurere indstillinger for uønsket mail Exchange Online postkasser i Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).
  - **Sæt meddelelsen i karantæne**: Sender meddelelsen til karantæne i stedet for de tilsigtede modtagere. Du kan finde oplysninger om karantæne i følgende artikler:
    - [Karantæne i Microsoft 365](quarantine-email-messages.md)
    - [Administrer meddelelser og filer i karantæne som administrator i Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Find og slip meddelelser, der er sat i karantæne, som en bruger i Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

    Hvis du vælger **Karantæne for** meddelelsen, kan du også vælge den karantænepolitik, der gælder for meddelelser, der er i karantæne af bruger efterligning eller domæne efterligningsbeskyttelse. Karantænepolitikker definerer, hvad brugerne kan gøre for meddelelser, der er sat i karantæne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).

  - **Aflever meddelelsen, og føj andre adresser til linjen Bcc**: Lever meddelelsen til de tilsigtede modtagere, og overlever automatisk meddelelsen til de angivne modtagere.
  - **Slet meddelelsen, før den leveres**: Sletter automatisk hele meddelelsen, inklusive alle vedhæftede filer.

- **Sikkerhedstip om efterligning**: Slå følgende sikkerhedstip til efterligning til eller fra, som vises for meddelelser, der ikke kontrollerer efterligning:
  - **Vis tip for efterligning af brugere**: Fra-adressen indeholder en **Gør det muligt for brugere at beskytte** brugere. Kun tilgængelig, **hvis Aktivér brugere at beskytte** er aktiveret og konfigureret.
  - **Vis tip for efterligninger af domæner**: Fra-adressen indeholder en **Aktivér domæner for at beskytte** domæne. Kun tilgængelig, **hvis Aktivér domæner for at beskytte** er aktiveret og konfigureret.
  - **Vis tip for** usædvanlige tegn: Fra-adressen indeholder usædvanlige tegnsæt (f.eks. matematiske symboler og tekst eller en blanding af store og små bogstaver) i en  Aktivér brugere til at beskytte afsendere eller et Aktivér domæner for at **beskytte afsenderdomænet**.  Kun tilgængelig, **hvis Aktivér brugere for at** _beskytte eller_ **Aktivér domæner for at** beskytte er aktiveret og konfigureret.

- **Aktivér postkasseintelligens**: Aktiverer eller deaktiverer kunstig intelligens, der bestemmer brugernes mailmønstre med deres hyppige kontakter. Med denne indstilling kan AI skelne mellem meddelelser fra legitime og efterligninger af afsendere.

  Gabriela Laureano (glaureano@contoso.com) er f.eks. den administrerende direktør i din virksomhed, så du tilføjer hende som en beskyttet afsender i indstillingen Giv  brugerne mulighed for at beskytte indstillingerne for politikken. Men nogle af de modtagere, som politikken gælder for, skal kommunikere regelmæssigt med en leverandør, som også hedder Gabriela Laureano (glaureano@fabrikam.com). Da disse modtagere har en kommunikationsoversigt med glaureano@fabrikam.com, vil postkasseintelligens ikke identificere meddelelser fra glaureano@fabrikam.com som et forsøg på efterligning af glaureano@contoso.com for disse modtagere.

  Hvis du vil bruge hyppige kontakter, der er blevet lært af postkasseintelligens (og mangler derfra) til at beskytte brugere mod efterligningangreb, kan du aktivere Aktivér beskyttelse af intelligens efter aktivering af postkassens **intelligens.**

- **Aktivér intelligence-repræsentationsbeskyttelse**: Aktivér denne indstilling for at angive den handling, der skal gøre følgende for meddelelser til repræsentationsregistreringer fra postkassens intelligensresultater:
  - **Anvend ikke nogen handling: Bemærk**, at denne værdi har det samme resultat som aktivering af **Postkasse-intelligens** , men deaktiver **Aktivér** beskyttelse af efterligning.
  - **Omdiriger meddelelse til andre mailadresser**
  - **Flyt meddelelsen til modtagernes mapper med uønsket mail**
  - **Sæt meddelelsen i karantæne**: Hvis du vælger denne handling, kan du også vælge den karantænepolitik, der gælder for meddelelser, der er sat i karantæne af postkassens intelligencebeskyttelse. Karantænepolitikker definerer, hvad brugerne kan gøre for meddelelser, der er sat i karantæne, og om brugerne modtager beskeder om karantæne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).
  - **Levere meddelelsen og føje andre adresser til linjen Bcc**
  - **Slet meddelelsen, før den leveres**

- **Tilføj afsendere og domæner, der er tillid til**: Undtagelser til indstillingerne for repræsentationsbeskyttelse. Meddelelser fra de angivne afsendere og afsenderdomæner klassificeres aldrig som efterligningsbaserede angreb af politikken. Med andre ord anvendes handlingen for beskyttede afsendere, beskyttede domæner eller postkassens intelligensbeskyttelse ikke på disse afsendere eller afsenderdomæner, der er tillid til. Den maksimale grænse for disse lister er 1024 poster.

### <a name="advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Avancerede grænseværdier for phishing i antiphishing-politikker i Microsoft Defender Office 365

Følgende avancerede grænseværdier for phishing er kun tilgængelige i antiphishing-politikker i Defender til Office 365. Disse grænseværdier styrer følsomheden ved anvendelse af maskinlæringsmodeller på meddelelser for at afgøre, om phishingen skal afgøres:

- **1 – Standard**: Dette er standardværdien. Alvorsgraden af den handling, der er foretaget på meddelelsen, afhænger af graden af tillid til, at meddelelsen er phishing (lav, mellem, høj eller meget høj). Meddelelser, der identificeres som phishing med en meget høj grad af tillid, har f.eks. de mest alvorlige handlinger anvendt, mens meddelelser, der identificeres som phishing med en lav grad af tillid, har anvendt mindre alvorlige handlinger.
- **2 – Aggressive**: Meddelelser, der identificeres som phishing med høj grad af tillid, behandles, som om de blev identificeret med en meget høj grad af tillid.
- **3 – Mere aggressive**: Meddelelser, der identificeres som phishing med en medium eller høj grad af tillid, behandles, som om de blev identificeret med en meget høj grad af tillid.
- **4 – Mest aggressive**: Meddelelser, der identificeres som phishing med lav, mellem eller høj grad af tillid, behandles, som om de blev identificeret med en meget høj grad af tillid.

Risikoen for falske positive (gode meddelelser, der er markeret som dårlige) øges, når du øger denne indstilling. Du kan finde oplysninger om de anbefalede indstillinger [i antiphishing-politikken i Microsoft Defender for Office 365 indstillinger](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365).
