---
title: Politikker for antiphishing
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
description: Administratorer kan få mere at vide om de politikker til bekæmpelse af phishing, der er tilgængelige i Exchange Online Protection (EOP) og Microsoft Defender for Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: cb33af08174890565994ffc253cf2332c01c31eb
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66770993"
---
# <a name="anti-phishing-policies-in-microsoft-365"></a>Politikker til bekæmpelse af phishing i Microsoft 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Politikker til konfiguration af indstillinger for beskyttelse mod phishing er tilgængelige i Microsoft 365-organisationer med Exchange Online postkasser, enkeltstående Exchange Online Protection organisationer (EOP) uden Exchange Online postkasser, og Microsoft Defender for Office 365 organisationer.

Eksempler på Microsoft Defender for Office 365 organisationer omfatter:

- Microsoft 365 Enterprise E5, Microsoft 365 Education A5 osv.
- [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise/home)
- [Microsoft 365 Business](https://www.microsoft.com/microsoft-365/business)
- [Microsoft Defender for Office 365 som et tilføjelsesprogram](https://products.office.com/exchange/advance-threat-protection)

Forskellene på højt niveau mellem anti-phishing-politikker i EOP og anti-phishing-politikker i Defender for Office 365 er beskrevet i følgende tabel:

|Funktion|Politikker til bekæmpelse af phishing i EOP|Politikker til bekæmpelse af phishing i Defender for Office 365|
|---|:---:|:---:|
|Automatisk oprettet standardpolitik|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|
|Opret brugerdefinerede politikker|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|
|Almindelige politikindstillinger<sup>\*</sup>|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|
|Spoof-indstillinger|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|
|Sikkerhedstip til første kontakt|![Markeret.](../../media/checkmark.png)|![Markeret](../../media/checkmark.png)|
|Repræsentationsindstillinger||![Markeret](../../media/checkmark.png)|
|Avancerede tærskler for phishing||![Markeret](../../media/checkmark.png)|

<sup>\*</sup> I standardpolitikken er politiknavnet og beskrivelsen skrivebeskyttet (beskrivelsen er tom), og du kan ikke angive, hvem politikken gælder for (standardpolitikken gælder for alle modtagere).

Hvis du vil konfigurere politikker til bekæmpelse af phishing, skal du se følgende artikler:

- [Konfigurer politikker for antiphishing i EOP](configure-anti-phishing-policies-eop.md)
- [Konfigurer politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md)

I resten af denne artikel beskrives de indstillinger, der er tilgængelige i politikker til bekæmpelse af phishing i EOP og Defender for Office 365.

## <a name="common-policy-settings"></a>Almindelige politikindstillinger

Følgende politikindstillinger er tilgængelige i politikker til bekæmpelse af phishing i EOP og Defender for Office 365:

- **Navn**: Du kan ikke omdøbe standardpolitikken til anti-phishing. Når du har oprettet en brugerdefineret anti-phishing-politik, kan du ikke omdøbe politikken på Microsoft 365 Defender portalen.

- **Beskrivelse** Du kan ikke føje en beskrivelse til standardpolitikken til anti-phishing, men du kan tilføje og ændre beskrivelsen af brugerdefinerede politikker, som du opretter.

- **Brugere, grupper og domæner**: Identificerer interne modtagere, som politikken mod phishing gælder for. Denne værdi kræves i brugerdefinerede politikker og er ikke tilgængelig i standardpolitikken (standardpolitikken gælder for alle modtagere).

  Du kan kun bruge en betingelse eller undtagelse én gang, men du kan angive flere værdier for betingelsen eller undtagelsen. Flere værdier med samme betingelse eller undtagelse bruger OR-logik (f.eks. _\<recipient1\>_ eller _\<recipient2\>_). Forskellige betingelser eller undtagelser bruger AND-logik (f.eks. _\<recipient1\>_ og _\<member of group 1\>_).

  - **Brugere**: En eller flere postkasser, mailbrugere eller mailkontakter i din organisation.
  - **Grupper**: En eller flere grupper i din organisation.
  - **Domæner**: Et eller flere af de konfigurerede [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i Microsoft 365.

  - **Udelad disse brugere, grupper og domæner**: Undtagelser for politikken. Indstillingerne og funktionsmåden er præcis som betingelserne:
    - **Brugere**
    - **Grupper**
    - **Domæner**

  > [!NOTE]
  > Der kræves mindst ét valg i indstillingerne **for brugere, grupper og domæner** i brugerdefinerede politikker til bekæmpelse af phishing for at identificere de meddelelsesmodtagere  <u>, som politikken gælder for</u>. Politikker til bekæmpelse af phishing i Defender for Office 365 har også [repræsentationsindstillinger](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365), hvor du kan angive individuelle afsendermailadresser eller afsenderdomæner<u>, der modtager repræsentationsbeskyttelse</u>, som beskrevet senere i denne artikel.
  >
  > Flere forskellige betingelser eller undtagelser er ikke additive; de er inkluderende. Politikken anvendes _kun_ på de modtagere, der stemmer overens med _alle_ de angivne modtagerfiltre. Du kan f.eks. konfigurere en modtagerfilterbetingelse i politikken med følgende værdier:
  >
  > - Modtageren er: romain@contoso.com
  > - Modtageren er medlem af: Direktører
  >
  > Politikken anvendes _kun_ på romain@contoso.com, hvis han også er medlem af gruppen Direktører. Hvis han ikke er medlem af gruppen, anvendes politikken ikke på ham.
  >
  > Hvis du på samme måde bruger det samme modtagerfilter som en undtagelse til politikken, anvendes politikken ikke _på romain@contoso.com kun_ , hvis han også er medlem af gruppen Direktører. Hvis han ikke er medlem af gruppen, gælder politikken stadig for ham.

## <a name="spoof-settings"></a>Spoof-indstillinger

Spoofing er, når Fra-adressen i en mail (den afsenderadresse, der vises i mailklienter) ikke svarer til domænet for mailkilden. Du kan få flere oplysninger om spoofing under [Beskyttelse mod spoofing i Microsoft 365](anti-spoofing-protection.md).

Følgende spoof-indstillinger er tilgængelige i politikker til bekæmpelse af phishing i EOP og Defender for Office 365:

- **Aktivér spoof intelligence**: Slår spoof intelligence til eller fra. Vi anbefaler, at du lader den være tændt.

  Når spoof intelligence er aktiveret, viser **indsigten spoof intelligence** spoofed afsendere, der automatisk blev registreret og tilladt eller blokeret af spoof intelligence. Du kan tilsidesætte spoof intelligence-dommen manuelt for at tillade eller blokere de registrerede spoofed-afsendere inde fra indsigten. Men når du gør det, forsvinder den spoofede afsender fra indsigten spoof intelligence og er nu kun synlig på fanen **Spoof** på listen over tilladte/blokerede lejere. Du kan også manuelt oprette tillad eller blokere poster for spoofede afsendere på lejerlisten Tillad/Bloker. Du kan finde flere oplysninger i følgende artikler:

  - [Spoof intelligence-indsigt i EOP](learn-about-spoof-intelligence.md)
  - [Administrer listen over tilladte/blokerede lejere i EOP](tenant-allow-block-list.md)

  > [!NOTE]
  >
  > - Beskyttelse mod spoofing er som standard aktiveret i standardpolitikken mod phishing og i alle nye brugerdefinerede politikker til bekæmpelse af phishing, som du opretter.
  > - Du behøver ikke at deaktivere beskyttelse mod spoofing, hvis din MX-post ikke peger på Microsoft 365. du aktiverer forbedret filtrering for forbindelser i stedet. Du kan finde instruktioner [under Udvidet filtrering for forbindelser i Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).
  > - Deaktivering af beskyttelse mod spoofing deaktiverer kun _implicit_ spoofing-beskyttelse fra [kontrol af sammensatte godkendelser](email-validation-and-authentication.md#composite-authentication) . Hvis afsenderen ikke kan _udføre eksplicit_ [DMARC-kontrol](use-dmarc-to-validate-email.md) , hvor politikken er indstillet til at sætte den i karantæne eller afvises, er meddelelsen stadig sat i karantæne eller afvist.

- **Ikke-godkendte afsenderindikatorer**: Tilgængelige i afsnittet **Tip til sikkerhed & kun indikatorer** , når spoof intelligence er slået til. Se detaljerne i næste afsnit.
- **Handlinger**: For meddelelser fra blokerede spoofede afsendere (automatisk blokeret af spoof intelligence eller manuelt blokeret på listen over tilladte/blokerede lejere) kan du også angive den handling, der skal udføres på meddelelserne:
  - **Flyt meddelelser til modtagernes mapper med uønsket mail**: Dette er standardværdien. Meddelelsen leveres til postkassen og flyttes til mappen Uønsket mail. Du kan få flere oplysninger under [Konfigurer indstillinger for uønsket mail på Exchange Online postkasser i Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).
  - **Sæt meddelelsen i karantæne**: Sender meddelelsen til karantæne i stedet for de ønskede modtagere. Du kan få oplysninger om karantæne i følgende artikler:
    - [Sæt karantæne i Microsoft 365](quarantine-email-messages.md)
    - [Administrer karantænemeddelelser og filer som administrator i Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Find og frigiv karantænemeddelelser som en bruger i Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

    Hvis du vælger **Sæt meddelelsen i karantæne**, kan du også vælge den karantænepolitik, der gælder for meddelelser, der er sat i karantæne af spoof intelligence Protection. Karantænepolitikker definerer, hvad brugerne kan gøre for at sætte meddelelser i karantæne, og om brugerne modtager karantænemeddelelser. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).

### <a name="unauthenticated-sender-indicators"></a>Ikke-godkendte afsenderindikatorer

Ikke-godkendte afsenderindikatorer er en del af de [Spoof-indstillinger](#spoof-settings), der er tilgængelige i afsnittet **Sikkerhedstips & indikatorer** i politikker til bekæmpelse af phishing i både EOP og Defender for Office 365. Følgende indstillinger er kun tilgængelige, når spoof intelligence er slået til:

- **Vis (?) for ikke-godkendte afsendere til spoof**: Føjer et spørgsmålstegn til afsenderens foto i feltet Fra, hvis meddelelsen ikke sender SPF- eller DKIM-kontroller, **og** meddelelsen ikke består DMARC eller [sammensat godkendelse](email-validation-and-authentication.md#composite-authentication). Når denne indstilling er slået fra, føjes spørgsmålstegnet ikke til afsenderens foto.

- **Vis koden "via"**: Tilføjer via-mærket (chris@contoso.com <u>via</u> fabrikam.com) i feltet Fra, hvis domænet i fra-adressen (den meddelelsesafsender, der vises i mailklienter) er forskellig fra domænet i **DKIM-signaturen eller MAIL FROM-adressen** . Du kan få flere oplysninger om disse adresser under [En oversigt over standarder for mailmeddelelser](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

Hvis du vil forhindre, at spørgsmålstegnet eller via -mærket føjes til meddelelser fra bestemte afsendere, har du følgende muligheder:

- Tillad den spoofede afsender i [indsigten spoof intelligence](learn-about-spoof-intelligence.md) eller manuelt på [lejerlisten tillad/bloker](tenant-allow-block-list.md). Hvis du tillader den spoofede afsender, forhindres via-mærket i at blive vist i meddelelser fra afsenderen, selvom **kodeindstillingen Vis "via"** er slået til i politikken.
- [Konfigurer mailgodkendelse](email-validation-and-authentication.md#configure-email-authentication-for-domains-you-own) for afsenderdomænet.
  - For spørgsmålstegnet på afsenderens billede er SPF eller DKIM det vigtigste.
  - For via-koden skal du bekræfte, at domænet i **DKIM-signaturen eller MAIL FROM-adressen** matcher (eller er et underdomæne af) domænet i Fra-adressen.

Du kan finde flere oplysninger [under Identificer mistænkelige meddelelser i Outlook.com og Outlook på internettet](https://support.microsoft.com/office/3d44102b-6ce3-4f7c-a359-b623bec82206)

## <a name="first-contact-safety-tip"></a>Sikkerhedstip til første kontakt

Indstillingerne **Vis sikkerhedstip til første kontakt** er tilgængelige i EOP og Defender for Office 365 organisationer og er ikke afhængige af indstillinger for spoof intelligence eller repræsentationsbeskyttelse. Sikkerhedstip vises til modtagere i følgende scenarier:

- Første gang, de modtager en meddelelse fra en afsender
- De modtager ikke ofte meddelelser fra afsenderen.

:::image type="content" source="../../media/safety-tip-first-contact-one-recipient.png" alt-text="Sikkerhedstip til første kontakt for meddelelser med én modtager" lightbox="../../media/safety-tip-first-contact-one-recipient.png":::

:::image type="content" source="../../media/safety-tip-first-contact-multiple-recipients.png" alt-text="Sikkerhedstip til første kontakt for meddelelser med flere modtagere" lightbox="../../media/safety-tip-first-contact-multiple-recipients.png":::

Denne funktion tilføjer et ekstra lag af sikkerhedsbeskyttelse mod potentielle repræsentationsangreb, så vi anbefaler, at du slår den til.

Det første kontaktsikkerhedstip erstatter også behovet for at oprette regler for mailflow (også kaldet transportregler), der tilføjer headeren med navnet **X-MS-Exchange-EnableFirstContactSafetyTip** med værdien **Aktivér** til meddelelser (selvom denne funktion stadig er tilgængelig).

> [!NOTE]
> Hvis meddelelsen har flere modtagere, om tip vises, og til hvem der er baseret på en flertalsmodel. Hvis størstedelen af modtagerne aldrig eller ofte modtager meddelelser fra afsenderen, modtager de berørte modtagere tipet **Nogle personer, der har modtaget denne meddelelse...** Hvis du er bekymret for, at denne funktionsmåde viser en modtagers kommunikationsvaner for en anden, bør du ikke aktivere det første kontaktsikkerhedstip og fortsætte med at bruge regler for mailflow i stedet.

## <a name="exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Eksklusive indstillinger i anti-phishing-politikker i Microsoft Defender for Office 365

I dette afsnit beskrives de politikindstillinger, der kun er tilgængelige i politikker til bekæmpelse af phishing i Defender for Office 365.

> [!NOTE]
> Standardpolitikken mod phishing i Defender for Office 365 giver [spoof-beskyttelse](set-up-anti-phishing-policies.md#spoof-settings) og postkasseintelligens til alle modtagere. De andre tilgængelige [repræsentationsbeskyttelsesfunktioner](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) og [avancerede indstillinger](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365) er dog ikke konfigureret eller aktiveret i standardpolitikken. Hvis du vil aktivere alle beskyttelsesfunktioner, skal du ændre standardpolitikken for anti-phishing eller oprette yderligere politikker til bekæmpelse af phishing.

### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Repræsentationsindstillinger i politikker til bekæmpelse af phishing i Microsoft Defender for Office 365

Repræsentation er det tilfælde, hvor afsenderens eller afsenderens maildomæne i en meddelelse ligner en rigtig afsender eller et rigtigt domæne:

- Et eksempel på repræsentation af domæne contoso.com er ćóntoso.com.
- Bruger repræsentation er en kombination af brugerens viste navn og mailadresse. Valeria Barrios (vbarrios@contoso.com) kan f.eks. repræsenteres som Valeria Barrios, men med en helt anden mailadresse.

> [!NOTE]
> Repræsentationsbeskyttelse søger efter domæner, der ligner hinanden. Hvis dit domæne f.eks. er contoso.com, søger vi efter forskellige domæner på øverste niveau (.com, .biz osv.) som repræsentationsforsøg, men også domæner, der ligner hinanden noget. Contosososo.com eller contoabcdef.com kan f.eks. ses som repræsentationsforsøg på contoso.com.

Et repræsenterede domæne kan ellers blive betragtet som legitimt (registreret domæne, konfigurerede mailgodkendelsesposter osv.), bortset fra at det er hensigten at bedrage modtagere.

Følgende repræsentationsindstillinger er kun tilgængelige i politikker til bekæmpelse af phishing i Defender for Office 365:

- **Giv brugerne mulighed for at beskytte**: Forhindrer, at de angivne interne eller eksterne mailadresser repræsenteres **som afsendere af meddelelser**. Du modtager f.eks. en mail fra virksomhedens næstformand, hvor du bliver bedt om at sende hende nogle interne firmaoplysninger. Vil du gøre det? Mange ville sende svaret uden at tænke.

  Du kan bruge beskyttede brugere til at tilføje interne og eksterne afsendermailadresser for at beskytte mod repræsentation. Denne liste over **afsendere** , der er beskyttet mod brugerrepræsentation, er forskellig fra listen over **modtagere** , som politikken gælder for (alle modtagere for standardpolitikken, bestemte modtagere som konfigureret i indstillingen **Brugere, grupper og domæner** i afsnittet [Indstillinger for fælles politik](#common-policy-settings) ).

  > [!NOTE]
  >
  > - I hver politik til bekæmpelse af phishing kan du maksimalt angive 350 beskyttede brugere (afsendermailadresser). Du kan ikke angive den samme beskyttede bruger i flere politikker. Så uanset hvor mange politikker der gælder for en modtager, er det maksimale antal beskyttede brugere (afsendermailadresser) for hver enkelt modtager 350. Du kan finde flere oplysninger om politikprioritet, og hvordan behandlingen af politikker stopper, når den første politik anvendes, under [Rækkefølge af mailbeskyttelse og prioritet](how-policies-and-protections-are-combined.md).
  > - Beskyttelse af brugerrepræsentation fungerer ikke, hvis afsenderen og modtageren tidligere har kommunikeret via mail. Hvis afsenderen og modtageren aldrig har kommunikeret via mail, identificeres meddelelsen som et repræsentationsforsøg.

  Som standard er ingen afsendermailadresser konfigureret til repræsentationsbeskyttelse i **Brugere for at beskytte**. Derfor er ingen afsendermailadresser som standard omfattet af repræsentationsbeskyttelse, hverken i standardpolitikken eller i brugerdefinerede politikker.

  Når du føjer interne eller eksterne mailadresser til **brugerne for at beskytte** listen, er meddelelser fra disse **afsendere** underlagt kontrol af repræsentationsbeskyttelse. Meddelelsen kontrolleres for repræsentation **, hvis** meddelelsen sendes til en **modtager** , som politikken gælder for (alle modtagere for standardpolitikken. **Brugere, grupper og domæner modtagere** i brugerdefinerede politikker). Hvis der registreres repræsentation i afsenderens mailadresse, anvendes repræsentationsbeskyttelseshandlinger for brugerne på meddelelsen (hvad der skal gøres med meddelelsen, om der skal vises sikkerhedstip til repræsenterede brugere osv.).

- **Aktivér domæner for at beskytte**: Forhindrer, at de angivne domæner **repræsenteres i meddelelsens afsenders domæne**. For eksempel alle domæner, som du ejer ([accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)) eller specifikke brugerdefinerede domæner (domæner, du ejer eller partnerdomæner). Denne liste over **afsenderdomæner** , der er beskyttet mod repræsentation, er forskellig fra listen over **modtagere** , som politikken gælder for (alle modtagere for standardpolitikken, bestemte modtagere som konfigureret i indstillingen **Brugere, grupper og domæner** i afsnittet [Indstillinger for fælles politik](#common-policy-settings) ).

  > [!NOTE]
  > Du kan maksimalt angive 50 brugerdefinerede domæner i hver anti-phishing-politik.

  Der er som standard ikke konfigureret nogen afsenderdomæner til repræsentationsbeskyttelse i **Aktivér domæner for at beskytte**. Derfor er ingen afsenderdomæner som standard omfattet af repræsentationsbeskyttelse, hverken i standardpolitikken eller i brugerdefinerede politikker.

  Når du føjer domæner til listen **Aktivér domæner for at beskytte** , er meddelelser fra **afsendere i disse domæner** underlagt kontrol af repræsentationsbeskyttelse. Meddelelsen kontrolleres for repræsentation **, hvis** meddelelsen sendes til en **modtager** , som politikken gælder for (alle modtagere for standardpolitikken. **Brugere, grupper og domæner modtagere** i brugerdefinerede politikker). Hvis der registreres repræsentation i afsenderens domæne, anvendes repræsentationsbeskyttelseshandlingerne for domæner på meddelelsen (hvad skal der gøres med meddelelsen, om der skal vises sikkerhedstip for repræsenterede brugere osv.).

- **Handlinger**: Vælg den handling, der skal udføres på indgående meddelelser, der indeholder repræsentationsforsøg mod de beskyttede brugere og beskyttede domæner i politikken. Du kan angive forskellige handlinger for repræsentation af beskyttede brugere i forhold til repræsentation af beskyttede domæner:
  - **Anvend ikke nogen handling**
  - **Omdiriger meddelelse til andre mailadresser**: Sender meddelelsen til de angivne modtagere i stedet for de ønskede modtagere.
  - **Flyt meddelelser til modtagernes mapper med uønsket mail**: Meddelelsen leveres til postkassen og flyttes til mappen Uønsket mail. Du kan få flere oplysninger under [Konfigurer indstillinger for uønsket mail på Exchange Online postkasser i Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).
  - **Sæt meddelelsen i karantæne**: Sender meddelelsen til karantæne i stedet for de ønskede modtagere. Du kan få oplysninger om karantæne i følgende artikler:
    - [Sæt karantæne i Microsoft 365](quarantine-email-messages.md)
    - [Administrer karantænemeddelelser og filer som administrator i Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Find og frigiv karantænemeddelelser som en bruger i Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

    Hvis du vælger **Sæt meddelelsen i karantæne**, kan du også vælge den karantænepolitik, der gælder for meddelelser, der er sat i karantæne af beskyttelse mod brugerpræsentation eller domæne repræsentation. Karantænepolitikker definerer, hvad brugerne kan gøre for at sætte meddelelser i karantæne. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).

  - **Levér meddelelsen, og føj andre adresser til Bcc-linjen**: Levér meddelelsen til de ønskede modtagere, og levér meddelelsen uovervåget til de angivne modtagere.
  - **Slet meddelelsen, før den leveres**: Sletter hele meddelelsen uovervåget, herunder alle vedhæftede filer.

- **Tip til repræsentation af sikkerhed**: Slå følgende tip til repræsentation af sikkerhed til eller fra, der vises meddelelser, der ikke kan repræsenteres:
  - **Vis tip til repræsenterede brugere**: Fra-adressen indeholder en **Aktivér brugere for at beskytte** brugeren. Kun tilgængelig, hvis **Aktivér brugere til at beskytte** er slået til og konfigureret.
  - **Vis tip til repræsenterede domæner**: Fra-adressen indeholder en **Aktivér domæner for at beskytte** domænet. Kun tilgængelig, hvis **Aktivér domæner for at beskytte** er slået til og konfigureret.
  - **Vis tip til usædvanlige tegn**: Fra-adressen indeholder usædvanlige tegnsæt (f.eks. matematiske symboler og tekst eller en blanding af store og små bogstaver) i et **Aktivér brugere til at beskytte** afsenderen eller et **Aktivér domæner for at beskytte** afsenderdomæner.  Kun tilgængelig, hvis **Aktivér brugere til at beskytte** _eller_ **Aktivér domæner for at beskytte** er slået til og konfigureret.

- **Aktivér postkasseintelligens**: Aktiverer eller deaktiverer kunstig intelligens (AI), der bestemmer brugermailmønstre med deres hyppige kontakter. Denne indstilling hjælper AI'en med at skelne mellem meddelelser fra legitime og repræsenterede afsendere.

  Gabriela Laureano (glaureano@contoso.com) er f.eks. ceo for din virksomhed, så du tilføjer hende som beskyttet afsender i **Aktivér brugere for at beskytte** indstillingerne for politikken. Men nogle af de modtagere, som politikken gælder for at kommunikere regelmæssigt med en leverandør, der også hedder Gabriela Laureano (glaureano@fabrikam.com). Da disse modtagere har en kommunikationsoversigt med glaureano@fabrikam.com, identificerer postkasseintelligens ikke meddelelser fra glaureano@fabrikam.com som et forsøg på at glaureano@contoso.com for disse modtagere.

  Hvis du vil bruge hyppige kontakter, der blev lært af postkasseintelligens (og mangel på samme) til at hjælpe med at beskytte brugere mod repræsentationsangreb, kan du aktivere **Aktivér beskyttelse af identitet for intelligens** , når du har slået **Aktivér postkasseintelligens** til.

- **Aktivér beskyttelse af repræsentation af intelligens**: Aktivér denne indstilling for at angive den handling, der skal udføres på meddelelser til repræsentationsregistreringer fra resultaterne af mailbox intelligence:
  - **Anvend ikke nogen handling**: Bemærk, at denne værdi har det samme resultat som at aktivere **Mailbox intelligence** , men deaktivere **Aktivér beskyttelse af repræsentation af intelligens**.
  - **Omdiriger meddelelse til andre mailadresser**
  - **Flyt meddelelsen til modtagernes mapper med uønsket mail**
  - **Sæt meddelelsen i karantæne**: Hvis du vælger denne handling, kan du også vælge den karantænepolitik, der gælder for meddelelser, der er sat i karantæne af mailbox intelligence Protection. Karantænepolitikker definerer, hvad brugerne kan gøre for at sætte meddelelser i karantæne, og om brugerne modtager karantænemeddelelser. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).
  - **Levér meddelelsen, og føj andre adresser til Bcc-linjen**
  - **Slet meddelelsen, før den leveres**

- **Tilføj afsendere og domæner, der er tillid** til: Undtagelser fra indstillingerne for repræsentationsbeskyttelse. Meddelelser fra de angivne afsendere og afsenderdomæner klassificeres aldrig som repræsentationsbaserede angreb af politikken. Det vil sige, at handlingen for beskyttede afsendere, beskyttede domæner eller postkasseintelligensbeskyttelse ikke anvendes på disse afsendere eller afsenderdomæner, der er tillid til. Den maksimale grænse for disse lister er 1024 poster.

### <a name="advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Avancerede tærskler for phishing i politikker til bekæmpelse af phishing i Microsoft Defender for Office 365

Følgende avancerede tærskler for phishing er kun tilgængelige i politikker til bekæmpelse af phishing i Defender for Office 365. Disse tærskler styrer følsomheden for anvendelse af modeller til maskinel indlæring på meddelelser for at fastslå en phishing-dom:

- **1 – Standard**: Dette er standardværdien. Alvorsgraden af den handling, der udføres på meddelelsen, afhænger af graden af tillid til, at meddelelsen er phishing (lav, mellem, høj eller meget høj tillid). Meddelelser, der identificeres som phishing med en meget høj grad af tillid, har f.eks. de mest alvorlige handlinger anvendt, mens meddelelser, der er identificeret som phishing med en lav grad af tillid, har anvendt mindre alvorlige handlinger.
- **2 – Aggressive**: Meddelelser, der identificeres som phishing med en høj grad af tillid, behandles, som om de blev identificeret med en meget høj grad af tillid.
- **3 – Mere aggressive**: Meddelelser, der identificeres som phishing med en medium eller høj grad af tillid, behandles, som om de blev identificeret med en meget høj grad af tillid.
- **4 – Mest aggressive**: Meddelelser, der identificeres som phishing med lav, mellem eller høj grad af tillid, behandles, som om de blev identificeret med en meget høj grad af tillid.

Chancen for falske positiver (gode meddelelser markeret som dårlige) øges, efterhånden som du øger denne indstilling. Du kan få flere oplysninger om de anbefalede indstillinger [under politik til bekæmpelse af phishing i Microsoft Defender for Office 365 indstillinger](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365).
