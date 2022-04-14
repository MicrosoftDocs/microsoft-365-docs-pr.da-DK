---
title: Konfigurer politikker for spamfilter
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 316544cb-db1d-4c25-a5b9-c73bbcf53047
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorer kan få mere at vide om, hvordan de kan få vist, oprette, redigere og slette politikker til bekæmpelse af spam i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 94d6ace6cd5d6fcfd87800053048e84e25d4c153
ms.sourcegitcommit: a7e1d155939e862337271fbe38bf26f62bd49bdd
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/14/2022
ms.locfileid: "64847378"
---
# <a name="configure-anti-spam-policies-in-eop"></a>Konfigurer politikker mod spam i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående EOP-organisationer (Exchange Online Protection) uden Exchange Online postkasser beskyttes indgående mails automatisk mod spam af EOP. EOP bruger politikker til bekæmpelse af spam (også kendt som politikker for spamfilter eller politikker for indholdsfiltrering) som en del af organisationens overordnede forsvar mod spam. Du kan få flere oplysninger under [Beskyttelse mod spam](anti-spam-protection.md).

Administratorer kan få vist, redigere og konfigurere (men ikke slette) standardpolitikken for spam. For at opnå større granularitet kan du også oprette brugerdefinerede anti-spam-politikker, der gælder for bestemte brugere, grupper eller domæner i din organisation. Brugerdefinerede politikker har altid forrang frem for standardpolitikken, men du kan ændre prioriteten (kører rækkefølge) for dine brugerdefinerede politikker.

Du kan konfigurere politikker til bekæmpelse af spam på Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til Microsoft 365 organisationer med postkasser i Exchange Online; enkeltstående EOP PowerShell til organisationer uden Exchange Online  postkasser).

De grundlæggende elementer i en politik mod spam er:

- **Filterpolitikken for spam**: Angiver handlingerne for spamfiltrering af domme og meddelelsesindstillingerne.
- **Regel for spamfilter**: Angiver prioritets- og modtagerfiltrene (hvem politikken gælder for) for en politik for spamfilter.

Forskellen mellem disse to elementer er ikke indlysende, når du administrerer anti-spam-politi på Microsoft 365 Defender portalen:

- Når du opretter en politik mod spam, opretter du faktisk en regel for spamfilter og den tilknyttede spamfilterpolitik på samme tid ved hjælp af det samme navn for begge.
- Når du ændrer en politik mod spam, ændrer indstillinger, der er relateret til navn, prioritet, aktiveret eller deaktiveret, og modtagerfiltre reglen for spamfilter. Alle andre indstillinger ændrer den tilknyttede politik for spamfilter.
- Når du fjerner en politik mod spam, fjernes reglen for spamfilteret og den tilknyttede filterpolitik for spam.

I Exchange Online PowerShell eller enkeltstående EOP PowerShell kan du administrere politikken og reglen separat. Du kan få flere oplysninger i afsnittet [Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at konfigurere politikker til bekæmpelse af spam](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-spam-policies) senere i denne artikel.

Alle organisationer har en indbygget politik mod spam med navnet Standard, der har disse egenskaber:

- Politikken anvendes på alle modtagere i organisationen, selvom der ikke er knyttet nogen filterregel for spam (modtagerfiltre) til politikken.
- Politikken har den brugerdefinerede prioritetsværdi **Laveste** , som du ikke kan ændre (politikken anvendes altid sidst). Alle brugerdefinerede politikker, du opretter, har altid en højere prioritet.
- Politikken er standardpolitikken (egenskaben **IsDefault** har værdien `True`), og du kan ikke slette standardpolitikken.

For at øge effektiviteten af spamfiltrering kan du oprette brugerdefinerede anti-spam-politikker med strengere indstillinger, der anvendes på bestemte brugere eller grupper af brugere.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Politikker mod spam** , skal du bruge <https://security.microsoft.com/antispam>.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, [skal du se Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du se Forbind til Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser i **Exchange Online**, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil tilføje, redigere og slette politikker til bekæmpelse af spam, skal du være medlem af rollegrupperne **Organisationsadministration** eller **Sikkerhedsadministrator** .
  - Hvis du vil have skrivebeskyttet adgang til politikker mod spam, skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser** .

  Du kan få flere oplysninger [under Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Noter**:

  - Tilføjelse af brugere til den tilsvarende Azure Active Directory rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få flere oplysninger under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - Rollegruppen **Vis kun organisationsadministration** i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) giver også skrivebeskyttet adgang til funktionen.

- Du kan se vores anbefalede indstillinger for politikker til bekæmpelse af spam under [Politikindstillinger for eOP for spam](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- Du kan ikke slå filtrering af spam helt fra, men du kan bruge en regel for mailflow (også kendt som en transportregel) til at omgå de fleste spamfiltrering på indgående meddelelser (f.eks. hvis du distribuerer mail via en tredjepartsbeskyttelsestjeneste eller enhed, før den leveres til Microsoft 365). Du kan få flere oplysninger under [Brug regler for mailflow til at angive niveauet for spamsikkerhed i meddelelser](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).
  - Phishing-meddelelser med høj genkendelsessikkerhed filtreres stadig. Andre funktioner i EOP påvirkes ikke (f.eks. scannes meddelelser altid for malware).
  - Hvis du har brug for at omgå spamfiltrering for SecOps-postkasser eller phishingsimuleringer, skal du ikke bruge regler for mailflow. Du kan få flere oplysninger under [Konfigurer levering af phishing-simuleringer fra tredjepart til brugere og ufiltrerede meddelelser til SecOps-postkasser](configure-advanced-delivery.md).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-spam-policies"></a>Brug Microsoft 365 Defender-portalen til at oprette politikker til bekæmpelse af spam

Når du opretter en brugerdefineret politik til bekæmpelse af spam på Microsoft 365 Defender-portalen, oprettes reglen for spamfilteret og den tilknyttede filterpolitik for spam samtidig med det samme navn for begge.

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Politikker mod spam** , skal du bruge <https://security.microsoft.com/antispam>.

2. Klik på Ikonet Opret på ![siden **Politikker mod spam**.](../../media/m365-cc-sc-create-icon.png) **Opret en politik** , og vælg derefter **Indgående** på rullelisten.

3. Politikguiden åbnes. Konfigurer disse indstillinger **på siden Navngiv din politik**:
   - **Navn**: Angiv et entydigt, beskrivende navn til politikken.
   - **Beskrivelse**: Angiv en valgfri beskrivelse af politikken.

   Klik på **Næste**, når du er færdig.

4. På siden **Brugere, grupper og domæner** , der vises, skal du identificere de interne modtagere, som politikken gælder for (modtagerbetingelser):
   - **Brugere**: De angivne postkasser, mailbrugere eller mailkontakter.
   - **Grupper**:
     - Medlemmer af de angivne distributionsgrupper eller mailaktiverede sikkerhedsgrupper.
     - Den angivne Microsoft 365-grupper.
   - **Domæner**: Alle modtagere i de angivne [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i din organisation.

   Klik i det relevante felt, begynd at skrive en værdi, og vælg den ønskede værdi fra resultaterne. Gentag denne proces så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Fjern ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   For brugere eller grupper kan du bruge de fleste identifikatorer (navn, vist navn, alias, mailadresse, kontonavn osv.), men det tilsvarende viste navn vises i resultaterne. For brugere skal du angive en stjerne (\*) alene for at se alle tilgængelige værdier.

   Flere værdier i samme betingelse bruger OR-logik (f.eks. _\<recipient1\>_ eller _\<recipient2\>_). Forskellige betingelser bruger AND-logik (f.eks. _\<recipient1\>_ og _\<member of group 1\>_).

   - **Udelad disse brugere, grupper og domæner**: Hvis du vil tilføje undtagelser for de interne modtagere, som politikken gælder for (modtagerundtagelser), skal du vælge denne indstilling og konfigurere undtagelserne. Indstillingerne og funktionsmåden er præcis som betingelserne.

   Klik på **Næste**, når du er færdig.

5. Konfigurer følgende indstillinger **på siden Massemailtærskel & egenskaber for spam** , der vises:

   - **Grænseværdi for massemail**: Angiver BCL-niveauet (Bulk Complaint Level) for en meddelelse, der udløser den angivne handling for dommen **massefiltrering** af spam, som du konfigurerer på næste side. En højere værdi angiver, at meddelelsen er mindre ønskelig (der er større sandsynlighed for at ligne spam). Standardværdien er 7. Du kan få flere oplysninger under [Samlet klageniveau (BCL) i EOP](bulk-complaint-level-values.md) og [Hvad er forskellen mellem uønsket mail og massemail?](what-s-the-difference-between-junk-email-and-bulk-email.md)

     PowerShell-indstillingen _MarkAsSpamBulkMail_ er `On` som standard angivet i politikker til bekæmpelse af spam. Denne indstilling påvirker resultaterne af en dom om **massefiltrering** dramatisk:

     - **_MarkAsSpamBulkMail_ er slået** til: En BCL, der er større end eller lig med tærsklen, konverteres til en SCL 6, der svarer til en filtrerings dom af **spam**, og handlingen for **massefiltrering** dom er taget på meddelelsen.
     - **_MarkAsSpamBulkMail_ er slået fra**: Meddelelsen er stemplet med BCL, men der udføres _ingen handling_ for en massefiltreringss dom. Faktisk er domshandlingen for BCL-tærsklen og **massefiltrering** irrelevant.

   - **Øg scoren for spam**, **Markér som spam**<sup>\*</sup> og **testtilstand**: Avancerede indstillinger for spamfilter (ASF), der som standard er slået fra.

     Du kan finde flere oplysninger om disse indstillinger [under Avancerede indstillinger for spamfilter i EOP](advanced-spam-filtering-asf-options.md).

      <sup>\*</sup> Indstillingerne **indeholder bestemte sprog** og **fra disse lande** er ikke en del af ASF.

   - **Indeholder bestemte sprog**: Klik på feltet, og vælg **Til** eller **Fra** på rullelisten. Hvis du slår den til, vises der et felt. Begynd at skrive navnet på et sprog i feltet. Der vises en filtreret liste over understøttede sprog. Når du finder det sprog, du leder efter, skal du vælge det. Gentag dette trin så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på fjern ![ikonet Fjern.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   - **Fra disse lande** _: Klik på feltet, og vælg _ *On** eller **Off** på rullelisten. Hvis du slår den til, vises der et felt. Begynd at skrive navnet på et land i feltet. Der vises en filtreret liste over understøttede lande. Når du finder det land, du leder efter, skal du vælge det. Gentag dette trin så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på fjern ![ikonet Fjern.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   Klik på **Næste**, når du er færdig.

6. Konfigurer følgende indstillinger på siden **Handlinger** , der vises:

   - **Meddelelseshandlinger**: Vælg eller gennemse den handling, der skal udføres på meddelelser baseret på følgende spamfiltreringsvurderinger:
     - **Spam**
     - **Spam med høj genkendelsessikkerhed**
     - **Phishing**
     - **Phishing med høj genkendelsessikkerhed**
     - **Bulk**

     De tilgængelige handlinger for spamfiltreringsdomme er beskrevet i følgende tabel.

     - En markering ( ![Markeret.](../../media/checkmark.png)) angiver, at handlingen er tilgængelig (ikke alle handlinger er tilgængelige for alle domme).
     - En stjerne ( <sup>\*</sup> ) efter markeringen angiver standardhandlingen for dom for filtrering af spam.

     |Handling|Spam|Høj<br>Tillid<br>Spam|Phishing|Høj<br>Tillid<br>Phishing|Bulk|
     |---|:---:|:---:|:---:|:---:|:---:|
     |**Flyt meddelelsen til mappen Uønsket mail**: Meddelelsen leveres til postkassen og flyttes til mappen Uønsket mail. <sup>1</sup>|![Markeret.](../../media/checkmark.png)<sup>\*</sup>|![Markeret.](../../media/checkmark.png)<sup>\*</sup>|![Markeret.](../../media/checkmark.png)|![Markeret](../../media/checkmark.png)|![Markeret](../../media/checkmark.png)<sup>\*</sup>|
     |**Tilføj X-header**: Føjer en X-header til brevhovedet og leverer meddelelsen til postkassen. <p> Du skal angive navnet på X-headerfeltet (ikke værdien) senere i **tekstfeltet Tilføj dette X-headerfelt** . <p> I forbindelse med **spam** - og **spamdomme med høj genkendelsessikkerhed** flyttes meddelelsen til mappen Uønsket mail. <sup>1,2</sup>|![Markeret.](../../media/checkmark.png)|![Markeret](../../media/checkmark.png)|![Markeret](../../media/checkmark.png)||![Markeret](../../media/checkmark.png)|
     |**Forudindstillet emnelinje med tekst**: Føjer tekst til starten af meddelelsens emnelinje. Meddelelsen leveres til postkassen og flyttes til mappen Uønsket mail. <sup>1,2</sup> <p> Du skal indtaste teksten senere i **emnelinjen præfiks med dette tekstfelt** .|![Markeret.](../../media/checkmark.png)|![Markeret](../../media/checkmark.png)|![Markeret](../../media/checkmark.png)||![Markeret](../../media/checkmark.png)|
     |**Omdiriger meddelelse til mailadresse**: Sender meddelelsen til andre modtagere i stedet for de ønskede modtagere. <p> Du skal angive modtagerne senere i feltet **Omdiriger til denne mailadresse** .|![Markeret.](../../media/checkmark.png)|![Markeret](../../media/checkmark.png)|![Markeret](../../media/checkmark.png)|![Markeret](../../media/checkmark.png)|![Markeret](../../media/checkmark.png)|
     |**Slet meddelelse**: Hele meddelelsen slettes uovervåget, herunder alle vedhæftede filer.|![Markeret.](../../media/checkmark.png)|![Markeret](../../media/checkmark.png)|![Markeret](../../media/checkmark.png)||![Markeret](../../media/checkmark.png)|
     |**Karantænemeddelelse**: Sender meddelelsen til karantæne i stedet for de ønskede modtagere. <p> Du angiver, hvor længe meddelelsen skal holdes i karantæne senere i feltet **Karantæne** . <p> Du angiver den [karantænepolitik](quarantine-policies.md) , der gælder for karantænemeddelelser for domsafsigelsen for spamfilteret, i feltet **Vælg en politik** , der vises. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md). <sup>3</sup>|![Markeret.](../../media/checkmark.png)|![Markeret](../../media/checkmark.png)|![Markeret](../../media/checkmark.png)<sup>\*</sup>|![Markeret](../../media/checkmark.png)<sup>\*</sup>|![Markeret](../../media/checkmark.png)|
     |**Ingen handling**|||||![Markeret](../../media/checkmark.png)|

     > <sup>1</sup> EOP bruger nu sin egen mailflowleveringsagent til at distribuere meddelelser til mappen Uønsket mail i stedet for at bruge reglen for uønsket mail. Parameteren _Enabled_ på Cmdlet'en **Set-MailboxJunkEmailConfiguration** har ikke længere nogen effekt på mailflowet. Du kan få flere oplysninger under [Konfigurer indstillinger for uønsket mail på Exchange Online postkasser](configure-junk-email-settings-on-exo-mailboxes.md).
     >
     > I hybridmiljøer, hvor EOP beskytter Exchange postkasser i det lokale miljø, skal du konfigurere regler for mailflow (også kaldet transportregler) i Exchange i det lokale miljø. Disse regler for mailflow oversætter dommen til filtrering af uønsket mail, så reglen for uønsket mail i postkassen kan flytte meddelelsen til mappen Uønsket mail. Du kan finde flere oplysninger under [Konfigurer EOP til at levere spam til mappen Uønsket mail i hybridmiljøer](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).
     >
     > <sup>2</sup> Du kan bruge værdien som en betingelse i regler for mailflow til at filtrere eller distribuere meddelelsen.
     >
     > <sup>3</sup> Hvis **du vælger en tom værdi for en politik** , betyder det, at standardkarantænepolitikken for den pågældende dom bruges. Når du senere redigerer politikken for bekæmpelse af spam eller får vist indstillingerne, vises standardnavnet for karantænepolitikken. Du kan få flere oplysninger om de standard karantænepolitikker, der bruges til domsafsigelser for spamfilteret, i [denne tabel](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features).

   - **Bevar spam i karantæne i dette antal dage**: Angiver, hvor længe meddelelsen skal holdes i karantæne, hvis du har valgt **Karantænemeddelelse** som handlingen for en dom til filtrering af spam. Når tidsperioden udløber, slettes meddelelsen, og den kan ikke gendannes. En gyldig værdi er fra 1 til 30 dage.

     > [!NOTE]
     > Standardværdien er 15 dage i standardpolitikken for spam og i nye politikker mod spam, som du opretter i PowerShell. Standardværdien er 30 dage i nye politikker mod spam, som du opretter på Microsoft 365 Defender portalen.
     >
     > Denne indstilling styrer også, hvor længe meddelelser, der blev sat i karantæne af **politikker til bekæmpelse af phishing** , bevares. Du kan få flere oplysninger [under Karantænemeddelelser i EOP og Defender for Office 365](quarantine-email-messages.md).

   - **Tilføj denne X-headertekst**: Dette felt er kun påkrævet og tilgængeligt, hvis du har valgt **Tilføj X-header** som handlingen for en dom til filtrering af spam. Den værdi, du angiver, er det *overskriftsfeltnavn* , der føjes til meddelelsesoverskriften. Værdien *i* overskriftsfeltet er altid `This message appears to be spam`.

     Maksimumlængden er 255 tegn, og værdien må ikke indeholde mellemrum eller kolon (:).

     Hvis du f.eks. angiver værdien `X-This-is-my-custom-header`, er den X-header, der føjes til meddelelsen, `X-This-is-my-custom-header: This message appears to be spam.`

     Hvis du angiver en værdi, der indeholder mellemrum eller kolon (:), ignoreres den angivne værdi, og standard-X-headeren føjes til meddelelsen (`X-This-Is-Spam: This message appears to be spam.`).

   - **Forudindstillet emnelinje med denne tekst**: Dette felt er kun påkrævet og tilgængeligt, hvis du har valgt **Forudindstillet emnelinje med tekst** som handlingen for en spamfiltreringsbesigelse. Skriv den tekst, der skal føjes til starten af meddelelsens emnelinje.

   - **Omdiriger til denne mailadresse**: Dette felt er kun påkrævet og tilgængeligt, hvis du har valgt **omdirigeringsmeddelelsen til mailadressen** som handlingen for en dom for filtrering af spam. Angiv den mailadresse, hvor du vil levere meddelelsen. Du kan angive flere værdier adskilt af semikolon (;).

   - **Aktivér sikkerhed Tips**: Sikkerhed Tips er som standard aktiveret, men du kan deaktivere dem ved at fjerne markeringen i afkrydsningsfeltet.

   - **Aktivér automatisk sletning på nul timer: ZAP** registrerer og reagerer på meddelelser, der allerede er leveret til Exchange Online postkasser. Du kan få flere oplysninger under [Automatisk tømninger på nul timer – beskyttelse mod spam og malware](zero-hour-auto-purge.md).

     ZAP er som standard slået til. Når ZAP er slået til, er følgende indstillinger tilgængelige:

     - **Aktivér ZAP til phishing-meddelelser**: ZAP er som standard aktiveret til phishing-registreringer, men du kan deaktivere det ved at fjerne markeringen i afkrydsningsfeltet.
     - **Aktivér ZAP for spammeddelelser**: ZAP er som standard aktiveret til registrering af spam, men du kan deaktivere det ved at fjerne markeringen i afkrydsningsfeltet.

   > [!NOTE]
   > Spammeddelelser fra slutbrugere er blevet erstattet af _karantænemeddelelser_ i karantænepolitikker. Karantænemeddelelser indeholder oplysninger om karantænemeddelelser for alle understøttede beskyttelsesfunktioner (ikke kun dom over spampolitik og anti-phishing-politik). Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).

   Klik på **Næste**, når du er færdig.

7. På **pop op-vinduet Tillad & blokere liste** , der vises, kan du konfigurere afsendere af meddelelser efter mailadresse eller maildomæne, der har tilladelse til at springe spamfiltrering over.

   I afsnittet **Tilladt** kan du konfigurere tilladte afsendere og tilladte domæner. I afsnittet **Blokeret** kan du tilføje blokerede afsendere og blokerede domæner.

   > [!IMPORTANT]
   >
   > Tænk dig godt om, før du føjer domæner til listen over tilladte domæner. Du kan få flere oplysninger under [Opret lister over sikre afsendere i EOP](create-safe-sender-lists-in-office-365.md)
   >
   > Føj aldrig dine egne [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) eller fælles domæner (f.eks. microsoft.com eller office.com) til listen over tilladte domæner. Hvis disse domæner har tilladelse til at omgå filtrering af spam, kan hackere nemt sende meddelelser, der spoof disse domæner, der er tillid til, til din organisation.
   >
   > Det er ikke farligt at blokere domæner manuelt ved at føje domænerne til listen over blokerede domæner, men det kan øge den administrative arbejdsbelastning. Du kan få flere oplysninger under [Opret lister over afsenderblokering i EOP](create-block-sender-lists-in-office-365.md).
   >
   > Der vil være tidspunkter, hvor vores filtre vil gå glip af en meddelelse, du ikke er enig i filtrering dommen, eller det tager tid for vores systemer at indhente det. I disse tilfælde er listen over tilladte og blokerede til at tilsidesætte de aktuelle filtreringsdomme. Men du bør bruge disse lister sparsomt og midlertidigt: Longs-lister kan blive ikke-administrerelige, og vores filtreringsstak skal gøre, hvad det skal gøre. Hvis du vil beholde et tilladt domæne i en længere periode, skal du bede afsenderen om at bekræfte, at deres domæne er godkendt og indstillet til DMARC-afvisning, hvis det ikke er.

   Fremgangsmåden til at føje poster til en af listerne er de samme:

   1. Klik på linket til den liste, du vil konfigurere:
      - **Tilladt** \> **Afsendere**: Klik på **Administrer (nn) afsender(e)**.
      - **Tilladt** \> **Domæner**: Klik på **Tillad domæner**.
      - **Blokeret** \> **Afsendere**: Klik på **Administrer (nn) afsender(e)**.
      - **Blokeret** \> **Domæner**: Klik på **Bloker domæner**.

   2. Gør følgende i det pop op-vindue, der vises:
      1. Klik på ![Ikonet Opret.](../../media/m365-cc-sc-create-icon.png) **Tilføj afsendere** eller **Tilføj domæner**.
      2. I pop op-vinduet **Tilføj afsendere** eller **Tilføj domæner** , der vises, skal du angive afsenderens mailadresse i feltet **Afsender** eller domænet i feltet **Domæne** . Når du skriver, vises værdien under feltet. Når du er færdig med at skrive mailadressen eller domænet, skal du vælge værdien under feltet.
      3. Gentag det forrige trin så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Fjern ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

      Når du er færdig, skal du klikke på **Tilføj afsendere** eller **Tilføj domæner**.

      Tilbage på det primære pop op-vindue vises de afsendere eller domæner, du har tilføjet, på siden. Benyt følgende fremgangsmåde for at fjerne en post fra denne side:

      1. Vælg et eller flere poster på listen. Du kan også **bruge søgefeltet** til at finde værdier på listen.
      2. Når du har valgt mindst én post, sletteikonet ![Ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) Vises.
      3. Klik på sletteikonet ![Ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) for at fjerne de markerede poster.

      Klik på **Udført**, når du er færdig.

      Tilbage på **siden Tillad & bloker liste** skal du klikke på **Næste** , når du er læst for at fortsætte.

8. Gennemse dine indstillinger på siden **Gennemse** , der vises. Du kan vælge **Rediger** i hver sektion for at redigere indstillingerne i sektionen. Du kan også klikke på **Tilbage** eller vælge den specifikke side i guiden.

   Klik på **Opret**, når du er færdig.

9. Klik på **Udført** på den bekræftelsesside, der vises.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-spam-policies"></a>Brug Microsoft 365 Defender-portalen til at få vist politikker mod spam

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Politikker mod spam** , skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Politikker mod spam** skal du søge efter en af følgende værdier:
   - **Type-værdien** er **brugerdefineret politik mod spam**
   - Værdien **af Name** er politikken **for indgående spam (standard)**

   Følgende egenskaber vises på listen over politikker til bekæmpelse af spam:

   - **Navn**
   - **Status**
   - **Prioritet**
   - **Type**

3. Når du vælger en politik mod spam ved at klikke på navnet, vises politikindstillingerne i et pop op-vindue.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-spam-policies"></a>Brug Microsoft 365 Defender-portalen til at ændre politikker mod spam

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Politikker mod spam** , skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Politikker for bekæmpelse af spam** skal du vælge en politik til bekæmpelse af spam på listen ved at klikke på navnet:
   - En brugerdefineret politik, som du har oprettet, hvor værdien i kolonnen **Type** er **Brugerdefineret politik mod spam**.
   - Standardpolitikken med navnet **Indgående politik for uønsket post (standard).**

3. I det pop op-vindue med politikoplysninger, der vises, skal du vælge **Rediger** i hvert afsnit for at redigere indstillingerne i sektionen. Du kan få flere oplysninger om indstillingerne i det forrige afsnit [Brug Microsoft 365 Defender-portalen til at oprette politikker mod spam](#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) i denne artikel.

   For standardpolitikken for spam er sektionen **Anvendt på** ikke tilgængelig (politikken gælder for alle), og du kan ikke omdøbe politikken.

Hvis du vil aktivere eller deaktivere en politik eller angive prioritetsrækkefølgen for politikken, skal du se følgende afsnit.

### <a name="enable-or-disable-anti-spam-policies"></a>Aktivér eller deaktiver politikker mod spam

Du kan ikke deaktivere standardpolitikken for spam.

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Politikker mod spam** , skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Politikker mod spam** skal du vælge en politik med **typeværdien** **brugerdefineret politik for spam** på listen ved at klikke på navnet.

3. Øverst i pop op-vinduet med politikoplysninger, der vises, kan du se en af følgende værdier:
   - **Politik slået fra**: Hvis du vil aktivere politikken, skal du klikke på ![Slå ikonet til.](../../media/m365-cc-sc-turn-on-off-icon.png) **Aktivér** .
   - **Politik slået** til: Hvis du vil slå politikken fra, skal du klikke på ![Slå ikonet fra.](../../media/m365-cc-sc-turn-on-off-icon.png) **Sluk for den**.

4. I den bekræftelsesdialogboks, der vises, skal du klikke **på Slå til** eller **Slå fra**.

5. Klik på **Luk** i pop op-vinduet med politikoplysninger.

Tilbage på hovedpolitiksiden **vil statusværdien** for politikken være **Til** eller **Fra**.

### <a name="set-the-priority-of-custom-anti-spam-policies"></a>Angiv prioriteten for brugerdefinerede politikker mod spam

Som standard får politikker til bekæmpelse af spam en prioritet, der er baseret på den rækkefølge, de blev oprettet i (nyere politikker har lavere prioritet end ældre politikker). Et lavere prioritetsnummer angiver en højere prioritet for politikken (0 er den højeste), og politikker behandles i prioriteret rækkefølge (politikker med højere prioritet behandles før politikker med lavere prioritet). Der kan ikke være to politikker, der har samme prioritet, og behandlingen af politikker stopper, når den første politik er anvendt.

Hvis du vil ændre prioriteten for en politik, skal du klikke på **Forøg prioritet** eller **Formindsk prioritet** i egenskaberne for politikken (du kan ikke direkte ændre **prioritetsnummeret** på portalen Microsoft 365 Defender). Det giver kun mening at ændre prioriteten for en politik, hvis du har flere politikker.

 **Noter**:

- I Microsoft 365 Defender-portalen kan du kun ændre prioriteten for politikken til bekæmpelse af spam, når du har oprettet den. I PowerShell kan du tilsidesætte standardprioriteten, når du opretter reglen for spamfilter (hvilket kan påvirke prioriteten af eksisterende regler).
- Politikker mod spam behandles i den rækkefølge, de vises i (den første politik har **prioritetsværdien** 0). Standardpolitikken for spam har prioritetsværdien **Laveste**, og du kan ikke ændre den.

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Politikker mod spam** , skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Politikker mod spam** skal du vælge en politik med **typeværdien** **Brugerdefineret politik for spam** på listen ved at klikke på navnet.

3. Øverst i pop op-vinduet med politikoplysninger, der vises, kan du se **Forøg prioritet** eller **Formindsk prioritet** baseret på den aktuelle prioritetsværdi og antallet af brugerdefinerede politikker:
   - Politikken mod spam med **prioritetsværdien** **0** har kun indstillingen **Formindsk prioritet** tilgængelig.
   - Politikken for spam med den laveste **prioritetsværdi** (f.eks. **3**) har kun indstillingen **Forøg prioritet** tilgængelig.
   - Hvis du har tre eller flere anti-spam-politikker, har politikkerne mellem de højeste og laveste prioritetsværdier både **indstillingerne Forøg prioritet** og **Formindsk prioritet** tilgængelige.

   Klik på ![ikonet Forøg prioritet.](../../media/m365-cc-sc-increase-icon.png) **Forøg prioritet** eller ![formindsk prioritetsikon](../../media/m365-cc-sc-decrease-icon.png) **Formindsk prioritet** for at ændre **prioritetsværdien** .

4. Når du er færdig, skal du klikke på **Luk** i pop op-vinduet med politikoplysninger.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-spam-policies"></a>Brug Microsoft 365 Defender-portalen til at fjerne brugerdefinerede politikker mod spam

Når du bruger Microsoft 365 Defender-portalen til at fjerne en brugerdefineret politik til bekæmpelse af spam, slettes reglen for spamfilteret og den tilsvarende politik for spamfilter. Du kan ikke fjerne standardpolitikken for spam.

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Politikker mod spam** , skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Politikker mod spam** skal du vælge en politik med **typeværdien** **brugerdefineret politik for spam** på listen ved at klikke på navnet. Øverst i pop op-vinduet med politikoplysninger, der vises, skal du klikke på ![ikonet Flere handlinger.](../../media/m365-cc-sc-more-actions-icon.png) **Flere handlinger** \> ![Ikonet](../../media/m365-cc-sc-delete-icon.png) Slet politik **Slet politik**.

3. Klik på **Ja** i den bekræftelsesdialogboks, der vises.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-spam-policies"></a>Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at konfigurere politikker for spam

Som tidligere beskrevet består en politik mod spam af en politik for spamfilter og en regel for spamfilter.

I Exchange Online PowerShell eller enkeltstående EOP PowerShell er forskellen mellem politikker for spamfilter og regler for spamfilter synlig. Du administrerer politikker for spamfilter ved hjælp **\*af -HostedContentFilterPolicy-cmdlet'erne** , og du administrerer regler for spamfilter ved hjælp **\*af -HostedContentFilterRule-cmdlet'erne** .

- I PowerShell skal du først oprette filterpolitikken for spam og derefter oprette filterreglen for spam, der identificerer den politik, som reglen gælder for.
- I PowerShell kan du ændre indstillingerne i filterpolitikken for spam og reglen for spamfilter separat.
- Når du fjerner en politik for spamfilter fra PowerShell, fjernes den tilsvarende regel for spamfilteret ikke automatisk og omvendt.

Følgende indstillinger for politik for spam er kun tilgængelige i PowerShell:

- Parameteren _MarkAsSpamBulkMail_ , der er `On` som standard. Effekten af denne indstilling blev forklaret i afsnittet [Brug portalen Microsoft 365 Defender til at oprette politikker mod spam](#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) tidligere i denne artikel.
- Følgende indstillinger for meddelelser om spamkarantæne for slutbrugere:
  - Parameteren _DownloadLink_, der viser eller skjuler linket til rapporteringsværktøjet til uønsket mail for Outlook.
  - Parameteren _EndUserSpamNotificationCustomSubject_ , som du kan bruge til at tilpasse emnelinjen i meddelelsen.

### <a name="use-powershell-to-create-anti-spam-policies"></a>Brug PowerShell til at oprette politikker mod spam

Oprettelse af en politik til bekæmpelse af spam i PowerShell er en proces med to trin:

1. Opret filterpolitikken for spam.
2. Opret den regel for spamfilter, der angiver den politik for spamfilter, som reglen gælder for.

 **Noter**:

- Du kan oprette en ny regel for spamfilter og tildele den en eksisterende filterpolitik for ikke-tilknyttet spam. En regel for spamfilter kan ikke knyttes til mere end én filterpolitik for spam.
- Du kan konfigurere følgende indstillinger for nye politikker for spamfiltre i PowerShell, der ikke er tilgængelige på Microsoft 365 Defender-portalen, før du har oprettet politikken:
  - Opret den nye politik som deaktiveret (_aktiveret_ `$false` på cmdlet'en **New-HostedContentFilterRule** ).
  - Angiv prioriteten for politikken under oprettelse (_prioritet_ _\<Number\>_) på cmdlet'en **New-HostedContentFilterRule** .

- En ny politik for spamfilter, som du opretter i PowerShell, er ikke synlig på Microsoft 365 Defender-portalen, før du tildeler politikken til en regel for spamfilter.

#### <a name="step-1-use-powershell-to-create-a-spam-filter-policy"></a>Trin 1: Brug PowerShell til at oprette en filterpolitik for spam

Brug denne syntaks til at oprette en politik for spamfilter:

```PowerShell
New-HostedContentFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

I dette eksempel oprettes der en filterpolitik for spam med navnet Contoso Executives med følgende indstillinger:

- Sæt meddelelser i karantæne, når den dom, der filtrerer efter spam, er spam eller høj tillid til spam, og brug standard [karantænepolitikken](quarantine-policies.md) for de karantænede meddelelser (vi bruger ikke parametrene _SpamQuarantineTag_ eller _HighConfidenceSpamQuarantineTag_ ).
- BCL 7, 8 eller 9 udløser handlingen for en massemail spam filtrering dom.

```PowerShell
New-HostedContentFilterPolicy -Name "Contoso Executives" -HighConfidenceSpamAction Quarantine -SpamAction Quarantine -BulkThreshold 6
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

> [!NOTE]
> Du kan finde detaljerede instruktioner til, hvordan du angiver den [karantænepolitik](quarantine-policies.md) , der skal bruges i en politik for spamfilter, under [Brug PowerShell til at angive karantænepolitikken i politikker til bekæmpelse af spam](quarantine-policies.md#anti-spam-policies-in-powershell).

#### <a name="step-2-use-powershell-to-create-a-spam-filter-rule"></a>Trin 2: Brug PowerShell til at oprette en regel for spamfilter

Brug denne syntaks til at oprette en filterregel for spam:

```PowerShell
New-HostedContentFilterRule -Name "<RuleName>" -HostedContentFilterPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

I dette eksempel oprettes en ny regel for spamfilter med navnet Contoso Executives med disse indstillinger:

- Politikken for spamfilteret med navnet Contoso Executives er knyttet til reglen.
- Reglen gælder for medlemmer af gruppen med navnet Contoso Executives Group.

```PowerShell
New-HostedContentFilterRule -Name "Contoso Executives" -HostedContentFilterPolicy "Contoso Executives" -SentToMemberOf "Contoso Executives Group"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-HostedContentFilterRule](/powershell/module/exchange/new-hostedcontentfilterrule).

### <a name="use-powershell-to-view-spam-filter-policies"></a>Brug PowerShell til at få vist politikker for spamfilter

Hvis du vil returnere en oversigt over alle politikker for spamfiltrering, skal du køre denne kommando:

```PowerShell
Get-HostedContentFilterPolicy
```

Hvis du vil returnere detaljerede oplysninger om en bestemt politik for spamfilter, skal du bruge denne syntaks:

```PowerShell
Get-HostedContentFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

I dette eksempel returneres alle egenskabsværdierne for filterpolitikken for spam med navnet Direktører.

```PowerShell
Get-HostedContentFilterPolicy -Identity "Executives" | Format-List
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

### <a name="use-powershell-to-view-spam-filter-rules"></a>Brug PowerShell til at få vist regler for spamfilter

Hvis du vil have vist eksisterende regler for spamfilteret, skal du bruge følgende syntaks:

```PowerShell
Get-HostedContentFilterRule [-Identity "<RuleIdentity>] [-State <Enabled | Disabled]
```

Hvis du vil returnere en oversigt over alle regler for spamfilter, skal du køre denne kommando:

```PowerShell
Get-HostedContentFilterRule
```

Hvis du vil filtrere listen efter aktiverede eller deaktiverede regler, skal du køre følgende kommandoer:

```PowerShell
Get-HostedContentFilterRule -State Disabled
```

```PowerShell
Get-HostedContentFilterRule -State Enabled
```

Hvis du vil returnere detaljerede oplysninger om en bestemt regel for spamfilter, skal du bruge denne syntaks:

```PowerShell
Get-HostedContentFilterRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

I dette eksempel returneres alle egenskabsværdierne for reglen for spamfilteret med navnet Contoso Executives.

```PowerShell
Get-HostedContentFilterRule -Identity "Contoso Executives" | Format-List
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-HostedContentFilterRule](/powershell/module/exchange/get-hostedcontentfilterrule).

### <a name="use-powershell-to-modify-spam-filter-policies"></a>Brug PowerShell til at ændre politikker for spamfilter

Ud over følgende elementer er de samme indstillinger tilgængelige, når du ændrer en politik for spamfilter i PowerShell, som når du opretter politikken som beskrevet i [trin 1: Brug PowerShell til at oprette en politik for spamfilter](#step-1-use-powershell-to-create-a-spam-filter-policy) tidligere i denne artikel.

- Parameteren _MakeDefault_ , der ændrer den angivne politik til standardpolitikken (anvendt på alle, altid **laveste** prioritet, og du kan ikke slette den), er kun tilgængelig, når du ændrer en politik for spamfilter i PowerShell.
- Du kan ikke omdøbe en politik for spamfilter ( **Set-HostedContentFilterPolicy-cmdlet'en** har ingen _navneparameter_ ). Når du omdøber en politik til bekæmpelse af spam på Microsoft 365 Defender-portalen, omdøber du kun _reglen_ for spamfilter.

Hvis du vil ændre en politik for spamfilter, skal du bruge denne syntaks:

```PowerShell
Set-HostedContentFilterPolicy -Identity "<PolicyName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

> [!NOTE]
> Du kan finde detaljerede instruktioner til, hvordan du angiver den [karantænepolitik](quarantine-policies.md) , der skal bruges i en politik for spamfilter, under [Brug PowerShell til at angive karantænepolitikken i politikker til bekæmpelse af spam](quarantine-policies.md#anti-spam-policies-in-powershell).

### <a name="use-powershell-to-modify-spam-filter-rules"></a>Brug PowerShell til at ændre regler for spamfilter

Den eneste indstilling, der ikke er tilgængelig, når du ændrer en regel for spamfilter i PowerShell, er parameteren _Enabled_ , der giver dig mulighed for at oprette en deaktiveret regel. Hvis du vil aktivere eller deaktivere eksisterende regler for spamfilter, skal du se næste afsnit.

Ellers er der ingen yderligere indstillinger tilgængelige, når du ændrer en regel for spamfilter i PowerShell. De samme indstillinger er tilgængelige, når du opretter en regel som beskrevet i [trin 2: Brug PowerShell til at oprette en regel for spamfilter](#step-2-use-powershell-to-create-a-spam-filter-rule) tidligere i denne artikel.

Hvis du vil ændre en regel for spamfilter, skal du bruge denne syntaks:

```PowerShell
Set-HostedContentFilterRule -Identity "<RuleName>" <Settings>
```

I dette eksempel omdøbes den eksisterende regel for spamfilteret med navnet `{Fabrikam Spam Filter}`.

```powershell
Set-HostedContentFilterRule -Identity "{Fabrikam Spam Filter}" -Name "Fabrikam Spam Filter"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-HostedContentFilterRule](/powershell/module/exchange/set-hostedcontentfilterrule).

### <a name="use-powershell-to-enable-or-disable-spam-filter-rules"></a>Brug PowerShell til at aktivere eller deaktivere regler for spamfilter

Aktivering eller deaktivering af en regel for spamfilter i PowerShell aktiverer eller deaktiverer hele politikken for spamfilter (reglen for spamfilteret og den tildelte filterpolitik for spam). Du kan ikke aktivere eller deaktivere standardpolitikken for spam (den anvendes altid på alle modtagere).

Hvis du vil aktivere eller deaktivere en regel for spamfilter i PowerShell, skal du bruge denne syntaks:

```PowerShell
<Enable-HostedContentFilterRule | Disable-HostedContentFilterRule> -Identity "<RuleName>"
```

I dette eksempel deaktiveres reglen for spamfilteret med navnet Marketingafdeling.

```PowerShell
Disable-HostedContentFilterRule -Identity "Marketing Department"
```

I dette eksempel aktiveres samme regel.

```PowerShell
Enable-HostedContentFilterRule -Identity "Marketing Department"
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Enable-HostedContentFilterRule](/powershell/module/exchange/enable-hostedcontentfilterrule) og [Disable-HostedContentFilterRule](/powershell/module/exchange/disable-hostedcontentfilterrule).

### <a name="use-powershell-to-set-the-priority-of-spam-filter-rules"></a>Brug PowerShell til at angive prioriteten for regler for spamfilter

Den højeste prioritetsværdi, du kan angive for en regel, er 0. Den laveste værdi, du kan angive, afhænger af antallet af regler. Hvis du f.eks. har fem regler, kan du bruge prioritetsværdierne 0 til 4. Hvis du ændrer prioriteten for en eksisterende regel, kan det have en overlappende effekt på andre regler. Hvis du f.eks. har fem brugerdefinerede regler (prioriteter 0 til 4), og du ændrer prioriteten for en regel til 2, ændres den eksisterende regel med prioritet 2 til prioritet 3, og reglen med prioritet 3 ændres til prioritet 4.

Hvis du vil angive prioriteten for en regel for spamfilter i PowerShell, skal du bruge følgende syntaks:

```PowerShell
Set-HostedContentFilterRule -Identity "<RuleName>" -Priority <Number>
```

I dette eksempel angives prioriteten for reglen marketingafdeling til 2. Alle eksisterende regler, der har en prioritet, der er mindre end eller lig med 2, reduceres med 1 (deres prioritetstal øges med 1).

```PowerShell
Set-HostedContentFilterRule -Identity "Marketing Department" -Priority 2
```

**Noter**:

- Hvis du vil angive prioriteten for en ny regel, når du opretter den, skal du i stedet bruge parameteren _Priority_ på Cmdlet'en **New-HostedContentFilterRule** .
- Standardfilterpolitikken for spam har ikke en tilsvarende regel for spamfilter, og den har altid den ikke-redigerbare prioritetsværdi **Laveste**.

### <a name="use-powershell-to-remove-spam-filter-policies"></a>Brug PowerShell til at fjerne politikker for spamfilter

Når du bruger PowerShell til at fjerne en politik for spamfilter, fjernes den tilsvarende regel for spamfilteret ikke.

Hvis du vil fjerne en politik for spamfilter i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-HostedContentFilterPolicy -Identity "<PolicyName>"
```

I dette eksempel fjernes filterpolitikken for spam med navnet Marketingafdeling.

```PowerShell
Remove-HostedContentFilterPolicy -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Remove-HostedContentFilterPolicy](/powershell/module/exchange/remove-hostedcontentfilterpolicy).

### <a name="use-powershell-to-remove-spam-filter-rules"></a>Brug PowerShell til at fjerne regler for spamfilter

Når du bruger PowerShell til at fjerne en regel for spamfilter, fjernes den tilsvarende politik for spamfilter ikke.

Hvis du vil fjerne en regel for spamfilter i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-HostedContentFilterRule -Identity "<PolicyName>"
```

I dette eksempel fjernes reglen for spamfilteret med navnet Marketingafdeling.

```PowerShell
Remove-HostedContentFilterRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Remove-HostedContentFilterRule](/powershell/module/exchange/remove-hostedcontentfilterrule).

## <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer virkede?

### <a name="send-a-gtube-message-to-test-your-spam-policy-settings"></a>Send en GTUBE-meddelelse for at teste indstillingerne for din spampolitik

> [!NOTE]
> Disse trin fungerer kun, hvis den mailorganisation, du sender GTUBE-meddelelsen fra, ikke scanner efter udgående spam. Hvis den gør det, kan du ikke sende testmeddelelsen.

Generic Test for Unsolicited Bulk Email (GTUBE) er en tekststreng, som du inkluderer i en testmeddelelse for at bekræfte din organisations indstillinger for spam. En GTUBE-meddelelse ligner tekstfilen fra Det Europæiske Institut for Computer Antivirus Research (EICAR) til test af malwareindstillinger.

Medtag følgende GTUBE-tekst i en mail på en enkelt linje uden mellemrum eller linjeskift:

```text
XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
```
