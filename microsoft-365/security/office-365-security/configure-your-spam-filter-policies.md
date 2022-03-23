---
title: Konfigurere politikker for spamfilter
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
description: Administratorer kan lære, hvordan de får vist, opretter, redigerer og sletter antispampolitikker i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1ac240f402d230362cb33ea818e62c1e0629eb39
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/19/2022
ms.locfileid: "63587910"
---
# <a name="configure-anti-spam-policies-in-eop"></a>Konfigurer antispampolitikker i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser er indgående mails automatisk beskyttet mod spam af EOP. EOP bruger antispampolitikker (også kaldet politikker for spamfilter eller politikker for filtrering af indhold) som en del af organisationens overordnede forsvar mod spam. Du kan finde flere oplysninger [under Beskyttelse mod uønsket post](anti-spam-protection.md).

Administratorer kan få vist, redigere og konfigurere (men ikke slette) standardpolitikken for uønsket post. Hvis du vil have større granularitet, kan du også oprette brugerdefinerede antispampolitikker, der gælder for bestemte brugere, grupper eller domæner i organisationen. Brugerdefinerede politikker tilsidesætter altid standardpolitikken, men du kan ændre prioriteten (rækkefølgen) for dine brugerdefinerede politikker.

Du kan konfigurere antispampolitikker i Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til Microsoft 365-organisationer med postkasser i Exchange Online; enkeltstående EOP PowerShell til organisationer uden Exchange Online  postkasser).

De grundlæggende elementer i en antispampolitik er:

- **Politik for spamfilter**: Angiver handlingerne for spamfiltrering og meddelelsesindstillingerne.
- **Reglen for spamfilter**: Angiver prioriteten og modtagerens filtre (hvem politikken gælder for) for en politik for spamfilter.

Forskellen mellem disse to elementer er ikke indlysende, når du administrerer antispam-politik på Microsoft 365 Defender portal:

- Når du opretter en antispampolitik, opretter du faktisk en regel for spamfilter og den tilknyttede politik for spamfilter på samme tid med det samme navn til begge dele.
- Når du ændrer en antispampolitik, ændrer indstillinger, der er relateret til navn, prioritet, aktiveret eller deaktiveret, og modtagerfiltrene ændrer reglen for spamfilter. Alle andre indstillinger ændrer den tilknyttede politik for spamfilter.
- Når du fjerner en politik for uønsket post, fjernes reglen for spamfilter og den tilknyttede politik for spamfiltrering.

I Exchange Online PowerShell eller enkeltstående EOP PowerShell administrerer du politikken og reglen separat. Du kan finde flere oplysninger i [afsnittet Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at konfigurere antispampolitikker](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-spam-policies) senere i denne artikel.

Hver organisation har en indbygget politik for uønsket post med navnet Standard, der har disse egenskaber:

- Politikken anvendes på alle modtagere i organisationen, selvom der ikke er knyttet nogen regel for spamfilter (modtagerfiltre) til politikken.
- Politikken har den brugerdefinerede **prioritetsværdi Laveste** , som du ikke kan ændre (politikken anvendes altid sidst). Eventuelle brugerdefinerede politikker, du opretter, har altid en højere prioritet.
- Politikken er standardpolitikken (egenskaben **IsDefault** har værdien ), `True`og du kan ikke slette standardpolitikken.

For at øge effektiviteten af spamfiltrering kan du oprette brugerdefinerede antispampolitikker med mere restriktive indstillinger, der anvendes til bestemte brugere eller grupper af brugere.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til **siden Politikker for uønsket post** skal du bruge <https://security.microsoft.com/antispam>.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du Forbind Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser **i Exchange Online,** før du kan udføre procedurerne i denne artikel:
  - Hvis du vil tilføje, ændre og slette antispampolitikker, skal du være medlem af **rollegrupperne Organisationsadministration** **eller Sikkerhedsadministrator** .
  - For skrivebeskyttet adgang til antispampolitikker skal du være medlem af **rollegrupperne Global Læser** eller **Sikkerhedslæser** .

  Du kan finde flere [oplysninger i Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Bemærkninger**:

  - Hvis du føjer brugere til den Azure Active Directory rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser og tilladelser til andre  funktioner Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - **Rollegruppen Skrivebeskyttet** organisationsadministration i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) også skrivebeskyttet adgang til funktionen.

- Se vores anbefalede indstillinger for antispampolitikker under [Indstillinger for EOP-antispampolitik](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- Du kan ikke deaktivere spamfiltrering fuldstændigt, men du kan bruge en regel for mailflow (også kaldet en transportregel) til at tilsidesætte de fleste spamfiltrering på indgående meddelelser (hvis du f.eks. distribuerer mail via en tredjepartsbeskyttelsestjeneste eller -enhed før levering til Microsoft 365). Få mere at vide under [Brug regler for mailflow til at angive tillidsniveauet for spam i meddelelser](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).
  - Phishingmeddelelser, der er meget sikre, filtreres stadig. Andre funktioner i EOP påvirkes ikke (meddelelser scannes f.eks. altid for malware).
  - Hvis du har brug for at tilsidesætte spamfiltrering for SecOps-postkasser eller phishing-simulering, skal du ikke bruge regler for mailflow. Få mere at vide under Konfigurer levering af [phishing-simuleringer fra tredjepart til brugere og ufiltrerede meddelelser til SecOps-postkasser](configure-advanced-delivery.md).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-spam-policies"></a>Brug Microsoft 365 Defender til at oprette antispampolitikker

Når du opretter en brugerdefineret politik for uønsket post i Microsoft 365 Defender-portalen, oprettes reglen for spamfilter og den tilknyttede politik for spamfilter på samme tid med det samme navn for begge.

1.  I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **&-samarbejdspolitikker** \> **& Politikker** \> \> for trussel mod **trusler** i **afsnittet Politikker.** For at gå direkte til **siden Politikker for uønsket post** skal du bruge <https://security.microsoft.com/antispam>.

2. Klik på **Opret ikon på siden** Antispam-politikker ![.](../../media/m365-cc-sc-create-icon.png) **Opret politik** , og **vælg derefter Indgående** på rullelisten.

3. Guiden politik åbnes. På siden **Navngive din politik skal** du konfigurere disse indstillinger:
   - **Navn**: Angiv et entydigt, beskrivende navn til politikken.
   - **Beskrivelse**: Angiv en valgfri beskrivelse af politikken.

   Klik på Næste, når du er **færdig**.

4. På siden **Brugere, grupper og domæner, der** vises, skal du identificere de interne modtagere, som politikken gælder for (modtagerbetingelser):
   - **Brugere**: De angivne postkasser, mailbrugere eller mailkontakter i organisationen.
   - **Grupper**: De angivne distributionsgrupper, mailaktiverede sikkerhedsgrupper eller Microsoft 365 grupper i organisationen.
   - **Domæner:** Alle modtagere på de angivne [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i organisationen.

   Klik i det relevante felt, begynd at skrive en værdi, og vælg den ønskede værdi i resultaterne. Gentag denne proces så mange gange, som det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Ikonet Fjern.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   For brugere eller grupper kan du bruge de fleste identifikatorer (navn, visningsnavn, alias, mailadresse, kontonavn osv.), men det tilsvarende viste navn vises i resultaterne. For brugere skal du angive en stjerne (\*) alene for at få vist alle tilgængelige værdier.

   Flere værdier i samme betingelse bruger ELLER-logik (f.eks. _\<recipient1\>_ eller _\<recipient2\>_). Forskellige betingelser bruger AND-logik (f.eks. _\<recipient1\>_ og _\<member of group 1\>_).

   - **Udelad disse brugere, grupper** og domæner: Hvis du vil tilføje undtagelser for de interne modtagere, som politikken gælder for (undtagelser til modtagere), skal du vælge denne indstilling og konfigurere undtagelserne. Indstillingerne og funktionsmåden er præcis som betingelserne.

   Klik på Næste, når du er **færdig**.

5. På siden **Grænseværdi for massemail & egenskaber for spam** , der vises, skal du konfigurere følgende indstillinger:

   - **Grænseværdi for massemail**: Angiver niveauet for masseklager (BCL) for en meddelelse, der udløser den angivne  handling for vurdering af massespamfiltrering, som du konfigurerer på næste side. En højere værdi angiver, at meddelelsen er mindre hensigtsmæssigt (mere tilbøjelig til at ligne spam). Standardværdien er 7. Du kan finde flere oplysninger [under Masseanmeldeelsesniveau (BCL) i EOP](bulk-complaint-level-values.md) og Hvad er forskellen på uønsket [mail og massemail?](what-s-the-difference-between-junk-email-and-bulk-email.md).

     Som standard er PowerShell kun indstillet _til MarkAsSpamBulkMail i_ `On` antispam-politikker. Denne indstilling har en dramatisk effekt på resultaterne **af en vurdering** af massefiltrering:

     - **_MarkAsSpamBulkMail_ er** til: En BCL, der er større end eller lig med tærskelværdien, konverteres til en SCL 6, der svarer til en filtreringsafslutning af **spam**, og  handlingen for erklæring om massefiltrering behandles på meddelelsen.
     - **_MarkAsSpamBulkMail_ er** slået Fra: Meddelelsen er stemplet med BCL, men  der sker ikke noget ved en vurdering **af** massefiltrering. Faktisk er BCL-grænsen og **massefiltreringshandlingen** irrelevant.

   - **Forøg spamscore**, **Markér som spam**<sup>\*</sup> og **Testtilstand**: Avancerede indstillinger for spamfilter (ASF), der er slået fra som standard.

     Du kan finde flere oplysninger om disse indstillinger [under Avancerede indstillinger for spamfilter i EOP](advanced-spam-filtering-asf-options.md).

      <sup>\*</sup> Indstillingerne **Indeholder bestemte sprog** og **fra disse lande er** ikke en del af ASF.

   - **Indeholder bestemte sprog**: Klik på feltet **, og** **vælg Til** eller Fra på rullelisten. Hvis du slår det til, vises der et felt. Begynd at skrive navnet på et sprog i feltet. Der vises en filtreret liste over understøttede sprog. Når du finder det sprog, du leder efter, skal du vælge det. Gentag dette trin så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   - **Fra disse lande** _: Klik på feltet, og *vælg _Til** **eller** Fra på rullelisten. Hvis du slår det til, vises der et felt. Begynd at skrive navnet på et land i feltet. Der vises en filtreret liste over understøttede lande. Når du finder det land, du leder efter, skal du vælge det. Gentag dette trin så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   Klik på Næste, når du er **færdig**.

6. På siden **Handlinger** , der vises, skal du konfigurere følgende indstillinger:

   - **Meddelelseshandlinger**: Markér eller gennemse den handling, der skal udføre på meddelelser, baseret på følgende fremgangsmåder for spamfiltrering:
     - **Spam**
     - **Spam med høj tillid**
     - **Phishing**
     - **Phishing med høj tillid**
     - **Masse**

     De tilgængelige handlinger for vurdering af spamfiltrering er beskrevet i følgende tabel.

     - En markering ( ![Markering.](../../media/checkmark.png)) angiver, at handlingen er tilgængelig (ikke alle handlinger er tilgængelige for alle bedømmelser).
     - En stjerne ( ) efter <sup>\*</sup> markeringen angiver standardhandlingen for vurdering af spamfiltrering.

     <br>

     ****

     |Handling|Spam|Høj<br>tillid<br>spam|Phishing|Høj<br>tillid<br>phishing|Masse|
     |---|:---:|:---:|:---:|:---:|:---:|
     |**Flyt meddelelsen til mappen Uønsket** mail: Meddelelsen leveres til postkassen og flyttes til mappen Uønsket mail. <sup>1</sup>|![Markering.](../../media/checkmark.png)<sup>\*</sup>|![Markering.](../../media/checkmark.png)<sup>\*</sup>|![Markering.](../../media/checkmark.png)|![Markering](../../media/checkmark.png)|![Markering](../../media/checkmark.png)<sup>\*</sup>|
     |**Tilføj X-brevhoved**: Tilføjer et X-brevhoved i brevhovedet og leverer meddelelsen til postkassen. <p> Du skal angive navnet på X-overskriftsfeltet (ikke værdien) senere i **tekstfeltet Tilføj denne X-overskrift** . <p> For **spam** **og beskeder om høj** tillid til spam flyttes meddelelsen til mappen Uønsket mail. <sup>1,2</sup>|![Markering.](../../media/checkmark.png)|![Markering](../../media/checkmark.png)|![Markering](../../media/checkmark.png)||![Markering](../../media/checkmark.png)|
     |**Foranstillet emnelinje med tekst**: Føjer tekst til starten af meddelelsens emnelinje. Meddelelsen leveres til postkassen og flyttes til mappen Uønsket mail. <sup>1,2</sup> <p> Du kan skrive teksten senere i feltet **Brug dette tekstfelt som præfiks i emnelinjen** .|![Markering.](../../media/checkmark.png)|![Markering](../../media/checkmark.png)|![Markering](../../media/checkmark.png)||![Markering](../../media/checkmark.png)|
     |**Omdiriger meddelelse til** mailadresse: Sender meddelelsen til andre modtagere i stedet for til de tilsigtede modtagere. <p> Du angiver modtagerne senere i feltet **Omdiriger til denne** mailadresse.|![Markering.](../../media/checkmark.png)|![Markering](../../media/checkmark.png)|![Markering](../../media/checkmark.png)|![Markering](../../media/checkmark.png)|![Markering](../../media/checkmark.png)|
     |**Slet meddelelse**: Sletter automatisk hele meddelelsen, inklusive alle vedhæftede filer.|![Markering.](../../media/checkmark.png)|![Markering](../../media/checkmark.png)|![Markering](../../media/checkmark.png)||![Markering](../../media/checkmark.png)|
     |**Karantænemeddelelse**: Sender meddelelsen til karantæne i stedet for de tilsigtede modtagere. <p> Du angiver, hvor længe meddelelsen skal holdes i karantæne senere i **feltet Karantæne** . <p> Du angiver den [karantænepolitik,](quarantine-policies.md) der gælder for meddelelser, der er sat i karantæne, for spamfilterets konklusion i **feltet Vælg en** politik, der vises. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md). <sup>3</sup>|![Markering.](../../media/checkmark.png)|![Markering](../../media/checkmark.png)|![Markering](../../media/checkmark.png)<sup>\*</sup>|![Markering](../../media/checkmark.png)<sup>\*</sup>|![Markering](../../media/checkmark.png)|
     |**Ingen handling**|||||![Markering](../../media/checkmark.png)|
     |

     > <sup>1</sup> EOP bruger nu sin egen agent til levering af mailflow til at distribuere meddelelser til mappen Uønsket mail i stedet for at bruge reglen om uønsket mail. _Parameteren_ Enabled på **cmdlet'en Set-MailboxJunkEmailConfiguration** har ikke længere nogen indflydelse på mailflowet. Du kan finde flere oplysninger [under Konfigurere indstillinger for uønsket mail Exchange Online postkasser](configure-junk-email-settings-on-exo-mailboxes.md).
     >
     > I hybridmiljøer, hvor EOP beskytter lokale Exchange-postkasser, skal du konfigurere regler for mailflow (også kaldet transportregler) i lokale Exchange. Disse regler for mailflow oversætter reglen om spamfiltrering for EOP, så reglen om uønsket mail i postkassen kan flytte meddelelsen til mappen Uønsket mail. Du kan få mere at [vide under Konfigurer EOP til at levere spam til mappen Uønsket mail i hybridmiljøer](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).
     >
     > <sup>2</sup> Du kan bruge denne værdi som en betingelse i regler for mailflow til at filtrere eller distribuere meddelelsen.
     >
     > <sup>3 En</sup> tom værdi **Vælg en politik** betyder, at standardkarantænepolitikken for den pågældende beslutning anvendes. Når du senere redigerer antispampolitikken eller får vist indstillingerne, vises politikkens standardpolitiknavn i karantæne. Du kan finde flere oplysninger om standardkarantænepolitikker, der bruges til spamfilterets konklusion, [i denne tabel](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features).

   - **Bevar spam i karantæne i** dette antal dage: Angiver, hvor lang tid meddelelsen skal være i karantæne, hvis  du har valgt Karantænemeddelelse som handlingen for en vurdering af spamfiltrering. Når perioden udløber, slettes meddelelsen og kan ikke gendannes. En gyldig værdi er fra 1 til 30 dage.

     > [!NOTE]
     > Standardværdien er 15 dage i standardpolitikken for uønsket post og i nye politikker for uønsket post, som du opretter i PowerShell. Standardværdien er 30 dage i nye antispampolitikker, som du opretter i Microsoft 365 Defender-portalen.
     >
     > Denne indstilling styrer også, hvor længe meddelelser, der var i karantæne **via antiphishing-politikker** bevares. Få mere at vide under [Meddelelser, der er sat i karantæne i EOP og Defender for Office 365](quarantine-email-messages.md).

   - **Tilføj denne X-brevhovedtekst**: Dette felt er kun obligatorisk og tilgængeligt, hvis du har valgt **Tilføj X-brevhoved** som handlingen for en vurdering af spamfiltrering. Den værdi, du angiver, er navnet på *hovedfeltet* , der føjes til brevhovedet. Værdien i *hovedfeltet* er altid `This message appears to be spam`.

     Den maksimale længde er 255 tegn, og værdien må ikke indeholde mellemrum eller kolon (:).

     Hvis du f.eks. angiver værdien `X-This-is-my-custom-header`, bliver det X-brevhoved, der føjes til meddelelsen, `X-This-is-my-custom-header: This message appears to be spam.`

     Hvis du angiver en værdi, der indeholder mellemrum eller kolon (:), ignoreres den værdi, du angiver, og standard-X-overskriften føjes til meddelelsen (`X-This-Is-Spam: This message appears to be spam.`).

   - **Før emnelinjen** med denne tekst: Dette felt er kun obligatorisk og tilgængeligt, hvis du har valgt **Forppend** emnelinje med tekst som handlingen for vurdering af spamfiltrering. Skriv den tekst, du vil føje til starten af meddelelsens emnelinje.

   - **Omdiriger** til denne mailadresse: Dette felt er kun obligatorisk og tilgængeligt,  hvis du har valgt Omdiriger meddelelse til mailadresse som handlingen for en vurdering af spamfiltrering. Angiv den mailadresse, hvor du vil levere meddelelsen. Du kan angive flere værdier, der er adskilt med semikolon (;).

   - **Aktivér Tips**: Som standard er sikkerhedsindstillinger Tips aktiveret, men du kan deaktivere dem ved at fjerne markeringen i afkrydsningsfeltet.

   - **Aktivér automatisk tømning uden time (ZAP)**: ZAP registrerer og tager skridt i forbindelse med meddelelser, der allerede er blevet leveret Exchange Online postkasser. Du kan få mere at vide [under Automatisk tømning hver time – beskyttelse mod spam og malware](zero-hour-auto-purge.md).

     ZAP er som standard slået til. Når ZAP er slået til, er følgende indstillinger tilgængelige:

     - **Aktivér ZAP for phishingmeddelelser**: SOM standard er ZAP aktiveret til phishing-registreringer, men du kan deaktivere det ved at fjerne markeringen i afkrydsningsfeltet.
     - **Aktivér ZAP for spammeddelelser**: Som standard er ZAP aktiveret til registrering af spam, men du kan deaktivere det ved at fjerne markeringen i afkrydsningsfeltet.

   > [!NOTE]
   > Beskeder om spam til slutbrugere er blevet erstattet af _karantænemeddelelser i_ karantænepolitikker. Karantænemeddelelser indeholder oplysninger om meddelelser, der er sat i karantæne, for alle understøttede beskyttelsesfunktioner (ikke kun antispampolitik og antiphishingpolitik). Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).

   Klik på Næste, når du er **færdig**.

7. I pop **op&** blokeringsliste, der vises, kan du konfigurere meddelelsesafsendere efter mailadresse eller maildomæne, der har tilladelse til at springe spamfiltrering over.

   I sektionen **Tilladt** kan du konfigurere tilladte afsendere og tilladte domæner. I sektionen **Blokerede** kan du tilføje blokerede afsendere og blokerede domæner.

   > [!IMPORTANT]
   >
   > Tænk dig meget omhyggeligt om, før du føjer domæner til listen over tilladte domæner. Få mere at vide under [Opret lister over afsendere, der er tillid til i EOP](create-safe-sender-lists-in-office-365.md)
   >
   > Føj aldrig dine egne [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) eller fælles domæner (f.eks. microsoft.com eller office.com) til listen over tilladte domæner. Hvis disse domæner har tilladelse til at tilsidesætte spamfiltrering, kan hackere nemt sende meddelelser, der efterligner disse pålidelige domæner i din organisation.
   >
   > Det er ikke farligt at blokere domæner manuelt ved at føje domænerne til listen over blokerede domæner, men det kan øge din administrative arbejdsbyrde. Få mere at vide under [Opret lister over blokerede afsendere i EOP](create-block-sender-lists-in-office-365.md).
   >
   > Der vil være tidspunkter, hvor vores filtre vil gå glip af en meddelelse, du ikke er enig i filtreringens konklusion, eller det tager tid for vores systemer at indhente den. I disse tilfælde kan tilladelseslisten og blokeringslisten tilsidesætte de aktuelle filtreringskriterier. Men du bør bruge disse lister sparsomt og midlertidigt: lange lister kan blive ikke-administrerede, og vores filtreringsstak bør gøre det, den skulle gøre. Hvis du vil beholde et tilladt domæne i længere tid, skal du bede afsenderen om at bekræfte, at deres domæne er godkendt og indstillet til DMARC-afvisning, hvis det ikke er.

   Trinnene til at føje poster til en af listerne er de samme:

   1. Klik på linket for den liste, du vil konfigurere:
      - **Tilladt** \> **Afsendere**: Klik **på Administrer (nn) afsendere**.
      - **Tilladt** \> **Domæner:** Klik på **Tillad domæner**.
      - **Blokeret** \> **Afsendere**: Klik **på Administrer (nn) afsendere**.
      - **Blokeret** \> **Domæner:** Klik på **Bloker domæner**.

   2. Gør følgende i pop op-pop-op-pop-op-vindue:
      1. Klik ![på ikonet Opret.](../../media/m365-cc-sc-create-icon.png) **Tilføj afsendere** **eller Tilføj domæner**.
      2. I pop **op-meddelelsen** Tilføj afsendere eller Tilføj domæner skal du angive **afsenderens** mailadresse i feltet **Afsender** eller domænet i **feltet** Domæne. Når du skriver, vises værdien under feltet. Når du er færdig med at skrive mailadressen eller domænet, skal du vælge værdien under feltet.
      3. Gentag det forrige trin så mange gange, som det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Ikonet Fjern.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

      Når du er færdig, skal du **klikke på Tilføj** **afsendere eller Tilføj domæner**.

      Tilbage på pop op-pop-op-filen vises afsendere eller domæner, du har tilføjet, på siden. Hvis du vil fjerne en post fra denne side, skal du gøre følgende:

      1. Vælg en eller flere poster på listen. Du kan også bruge **feltet Søg** til at finde værdier på listen.
      2. Når du har valgt mindst én post, ikonet Slet ![Ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) vises.
      3. Klik på ikonet slet ![Ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) for at fjerne de markerede poster.

      Klik på Udført, når du er **færdig**.

      Tilbage på siden **Tillad blokering & skal du** klikke på **Næste** , når du læser for at fortsætte.

8. Gennemgå dine **indstillinger** på siden Gennemse, der vises. Du kan vælge **Rediger** i hver sektion for at ændre indstillingerne i sektionen. Eller du kan klikke **på** Tilbage eller vælge den bestemte side i guiden.

   Klik på Opret, når du er **færdig**.

9. Klik på Udført på bekræftelsessiden, der **vises**.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-spam-policies"></a>Brug portalen Microsoft 365 Defender til at få vist antispampolitikker

1.  I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **&-samarbejdspolitikker** \> **& Politikker** \> \> for trussel mod **trusler** i **afsnittet Politikker.** For at gå direkte til **siden Politikker for uønsket post** skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Anti-spam-politikker** skal du se efter en af følgende værdier:
   - Værdien **Type** er **Brugerdefineret politik for uønsket post**
   - Værdien **Navn** er **en indgående politik for uønsket post (standard)**

   Følgende egenskaber vises på listen over antispampolitikker:

   - **Navn**
   - **Status**
   - **Prioritet**
   - **Type**

3. Når du vælger en politik for uønsket post ved at klikke på navnet, vises politikindstillingerne i et pop op-pop op-format.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-spam-policies"></a>Brug portalen Microsoft 365 Defender til at ændre antispampolitikker

1.  I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **&-samarbejdspolitikker** \> **& Politikker** \> \> for trussel mod **trusler** i **afsnittet Politikker.** For at gå direkte til **siden Politikker for uønsket post** skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Antispam-politikker** skal du vælge en antispampolitik på listen ved at klikke på navnet:
   - En brugerdefineret politik, du har oprettet, hvor værdien **i kolonnen Type** er **Brugerdefineret politik for uønsket post**.
   - Standardpolitikken for **indgående uønsket post (standard).**

3. I pop op-vindue med politikoplysninger skal du **vælge Rediger** i hver sektion for at ændre indstillingerne i sektionen. Du kan finde flere oplysninger om indstillingerne i det forrige [afsnit Microsoft 365 Defender-portalen til at oprette antispampolitikker](#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) i denne artikel.

   For standardpolitikken for uønsket post er sektionen  Anvendt på ikke tilgængelig (politikken gælder for alle), og du kan ikke omdøbe politikken.

Hvis du vil aktivere eller deaktivere en politik eller angive prioritetsrækkefølgen for politikker, skal du se følgende afsnit.

### <a name="enable-or-disable-anti-spam-policies"></a>Aktivere eller deaktivere antispampolitikker

Du kan ikke deaktivere standardpolitikken for uønsket post.

1.  I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **&-samarbejdspolitikker** \> **& Politikker** \> \> for trussel mod **trusler** i **afsnittet Politikker.** For at gå direkte til **siden Politikker for uønsket post** skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Anti-spam-politikker** skal du vælge en politik med værdien **Type** for Brugerdefineret politik for **uønsket post** på listen ved at klikke på navnet.

3. Øverst i pop op-vindue med politikoplysninger, der vises, får du vist en af følgende værdier:
   - **Politik deaktiveret**: Hvis du vil aktivere politikken, skal du klikke ![på ikonet Slå til.](../../media/m365-cc-sc-turn-on-off-icon.png) **Slå til** .
   - **Politik slået til**: Hvis du vil deaktivere politikken, skal du klikke ![på Ikonet Slå fra.](../../media/m365-cc-sc-turn-on-off-icon.png) **Slå fra**.

4. I bekræftelsesdialogboksen, der vises, skal **du klikke på Aktivér** **eller Slå fra**.

5. Klik **på Luk** i pop op-menuen med politikoplysninger.

Tilbage på hovedpolitiksiden vil **politikkens statusværdi** **være Til eller** **Fra**.

### <a name="set-the-priority-of-custom-anti-spam-policies"></a>Angiv prioriteten af brugerdefinerede antispampolitikker

Som standard får antispam-politikker en prioritet, der er baseret på den rækkefølge, de blev oprettet i (nyere politikker er lavere end ældre politikker). Et tal for lavere prioritet angiver en højere prioritet for politikken (0 er den højeste), og politikkerne behandles i prioritetsrækkefølgen (politikker med højere prioritet behandles før politikker med lavere prioritet). Der er ikke to politikker, der kan have samme prioritet, og behandling af politikker stopper, når den første politik er anvendt.

Hvis du vil ændre prioriteten af en politik, skal du klikke  på Forøg prioritet eller Formindsk prioritet i egenskaberne for politikken (du kan ikke direkte ændre tallet prioritet i Microsoft 365 Defender portal). Det giver kun mening at ændre prioriteten af en politik, hvis du har flere politikker.

 **Bemærkninger**:

- I Microsoft 365 Defender-portalen kan du kun ændre prioriteten af antispampolitikken, når du har oprettet den. I PowerShell kan du tilsidesætte standardprioriteten, når du opretter reglen for spamfilter (hvilket kan påvirke prioriteten af eksisterende regler).
- Antispampolitikker behandles i den rækkefølge, de vises i (den første politik har **prioritetsværdien** 0). Standard antispampolitikken har den **laveste prioritetsværdi**, og du kan ikke ændre den.

1.  I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **&-samarbejdspolitikker** \> **& Politikker** \> \> for trussel mod **trusler** i **afsnittet Politikker.** For at gå direkte til **siden Politikker for uønsket post** skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Anti-spam-politikker** skal du vælge en politik med værdien **Type** for Brugerdefineret politik for **uønsket post** på listen ved at klikke på navnet.

3. Øverst i pop op-vindue med politikoplysninger, der vises, får du vist  Forøg  prioritet eller Formindsk prioritet baseret på den aktuelle prioritetsværdi og antallet af brugerdefinerede politikker:
   - Antispampolitikken med værdien **Prioritet** **0** har kun indstillingen **Formindsk** prioritet tilgængelig.
   - Antispampolitikken med den laveste **prioritetsværdi** (f.eks **. 3**) har kun indstillingen **Forøg** prioritet tilgængelig.
   - Hvis du har tre eller flere antispampolitikker, har politikkerne mellem de højeste og laveste prioritetsværdier både indstillingerne  Forøg prioritet og Formindsk **prioritet**.

   Klik på ![ikonet Forøg prioritet.](../../media/m365-cc-sc-increase-icon.png) **Forøg** prioritet ![eller ikonet Formindsk prioritet](../../media/m365-cc-sc-decrease-icon.png) **Formindsk prioritet** for at **ændre værdien** Prioritet.

4. Når du er færdig, skal du **klikke på** Luk i pop op-menuen med politikoplysninger.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-spam-policies"></a>Brug portalen Microsoft 365 Defender til at fjerne brugerdefinerede antispampolitikker

Når du bruger Microsoft 365 Defender til at fjerne en brugerdefineret antispampolitik, slettes både reglen for spamfilter og den tilsvarende politik for spamfilter. Du kan ikke fjerne standardpolitikken for uønsket post.

1.  I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **&-samarbejdspolitikker** \> **& Politikker** \> \> for trussel mod **trusler** i **afsnittet Politikker.** For at gå direkte til **siden Politikker for uønsket post** skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Anti-spam-politikker** skal du vælge en politik med værdien **Type** for Brugerdefineret politik for **uønsket post** på listen ved at klikke på navnet. Øverst i pop op-vindue med politikoplysninger, der vises, skal du klikke på ![ikonet Flere handlinger.](../../media/m365-cc-sc-more-actions-icon.png) **Flere handlinger** \> ![Ikonet Slet politik **Slet**](../../media/m365-cc-sc-delete-icon.png) politik.

3. Klik på Ja i bekræftelsesdialogboksen, der **vises**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-spam-policies"></a>Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at konfigurere antispampolitikker

Som beskrevet tidligere består en politik for uønsket post af en politik for spamfilter og en regel for spamfilter.

I Exchange Online PowerShell eller den enkeltstående EOP PowerShell fremgår forskellen mellem politikker for spamfiltrering og regler for spamfilter tydeligt. Du administrerer politikker for spamfiltrering **\*ved hjælp af cmdlet'erne -HostedContentFilterPolicy**, og du administrerer regler for spamfilter ved hjælp af cmdlet'erne **-HostedContentFilterRule.\***

- I PowerShell skal du først oprette politikken for spamfilter, og derefter skal du oprette reglen for spamfilter, der identificerer den politik, som reglen gælder for.
- I PowerShell ændrer du indstillingerne i politikken for spamfilter og reglen for spamfilter separat.
- Når du fjerner en politik for spamfilter fra PowerShell, fjernes den tilsvarende regel for spamfilter ikke automatisk og omvendt.

Følgende antispampolitikindstillinger er kun tilgængelige i PowerShell:

- _Parameteren MarkAsSpamBulkMail_ er `On` som standard. Virkningerne af denne indstilling er forklaret i [afsnittet Brug Microsoft 365 Defender til at oprette antispampolitikker](#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) tidligere i denne artikel.
- Følgende indstillinger for beskeder om spam til slutbrugeren i karantæne:
  - _Parameteren DownloadLink_, der viser eller skjuler linket til rapporteringsværktøjet til uønsket mail for Outlook.
  - _Parameteren EndUserSpamNotificationCustomSubject_, som du kan bruge til at tilpasse meddelelsens emnelinje.

### <a name="use-powershell-to-create-anti-spam-policies"></a>Brug PowerShell til at oprette antispampolitikker

Oprettelse af en antispampolitik i PowerShell er en proces i to trin:

1. Opret politikken for spamfilter.
2. Opret reglen for spamfilter, der angiver politikken for spamfilter, som reglen gælder for.

 **Bemærkninger**:

- Du kan oprette en ny regel for spamfilter og tildele den en eksisterende politik for ikke-tilknyttet spamfilter. En regel for spamfilter kan ikke knyttes til mere end én politik for spamfilter.
- Du kan konfigurere følgende indstillinger for nye politikker for spamfilter i PowerShell, der ikke er tilgængelige i Microsoft 365 Defender-portalen, før du har oprettet politikken:
  - Opret den nye politik som deaktiveret (_Aktiveret_ `$false` på **cmdlet'en New-HostedContentFilterRule** ).
  - Angiv prioriteten af politikken under oprettelsen (_Prioritet_ _\<Number\>_) på **cmdlet'en New-HostedContentFilterRule** .

- En ny politik for spamfilter, som du opretter i PowerShell, er ikke synlig i Microsoft 365 Defender-portalen, før du tildeler politikken til en regel for spamfilter.

#### <a name="step-1-use-powershell-to-create-a-spam-filter-policy"></a>Trin 1: Brug PowerShell til at oprette en politik for spamfilter

Hvis du vil oprette en politik for spamfilter, skal du bruge denne syntaks:

```PowerShell
New-HostedContentFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

I dette eksempel oprettes en politik for spamfilter med navnet Contoso-ledere med følgende indstillinger:

- Karantæne af meddelelser, når spamfiltreringkontrast er spam eller høj konfidensspam, og brug standardkarantænepolitikken [for meddelelser](quarantine-policies.md) , der er sat i karantæne (vi bruger ikke parametrene _SpamQuarantineTag_ eller _HighConfidenceSpamQuarantineTag_ ).
- BCL 7, 8 eller 9 udløser handlingen for en vurdering af spamfiltrering for flere mails.

```PowerShell
New-HostedContentFilterPolicy -Name "Contoso Executives" -HighConfidenceSpamAction Quarantine -SpamAction Quarantine -BulkThreshold 6
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

> [!NOTE]
> Hvis du vil have detaljeret vejledning [](quarantine-policies.md) til at angive karantænepolitikken, der skal bruges i en politik for spamfilter, skal du se Brug PowerShell til at angive karantænepolitikken [i antispampolitikker](quarantine-policies.md#anti-spam-policies-in-powershell).

#### <a name="step-2-use-powershell-to-create-a-spam-filter-rule"></a>Trin 2: Brug PowerShell til at oprette en regel for spamfilter

Hvis du vil oprette en regel for spamfilter, skal du bruge denne syntaks:

```PowerShell
New-HostedContentFilterRule -Name "<RuleName>" -HostedContentFilterPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

I dette eksempel oprettes en ny regel for spamfilter med navnet Contoso-ledere med disse indstillinger:

- Politikken for spamfilter med navnet Contoso Executives er knyttet til reglen.
- Reglen gælder for medlemmer af den gruppe, der hedder Contoso Executives Group.

```PowerShell
New-HostedContentFilterRule -Name "Contoso Executives" -HostedContentFilterPolicy "Contoso Executives" -SentToMemberOf "Contoso Executives Group"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-HostedContentFilterRule](/powershell/module/exchange/new-hostedcontentfilterrule).

### <a name="use-powershell-to-view-spam-filter-policies"></a>Brug PowerShell til at få vist politikker for spamfiltrering

Kør denne kommando for at returnere en oversigt over alle politikker for spamfiltrering:

```PowerShell
Get-HostedContentFilterPolicy
```

Hvis du vil returnere detaljerede oplysninger om en bestemt politik for spamfilter, skal du bruge denne syntaks:

```PowerShell
Get-HostedContentFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

I dette eksempel returneres alle egenskabsværdierne for politikken for spamfilter med navnet Ledere.

```PowerShell
Get-HostedContentFilterPolicy -Identity "Executives" | Format-List
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

### <a name="use-powershell-to-view-spam-filter-rules"></a>Brug PowerShell til at få vist regler for spamfilter

For at få vist eksisterende regler for spamfilter skal du bruge følgende syntaks:

```PowerShell
Get-HostedContentFilterRule [-Identity "<RuleIdentity>] [-State <Enabled | Disabled]
```

Kør denne kommando for at returnere en oversigt over alle regler for spamfilter:

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

I dette eksempel returneres alle egenskabsværdierne for reglen for spamfilter med navnet Contoso Executives.

```PowerShell
Get-HostedContentFilterRule -Identity "Contoso Executives" | Format-List
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-HostedContentFilterRule](/powershell/module/exchange/get-hostedcontentfilterrule).

### <a name="use-powershell-to-modify-spam-filter-policies"></a>Brug PowerShell til at ændre politikker for spamfiltrering

Ud over følgende elementer er de samme indstillinger tilgængelige, når du ændrer en politik for spamfilter i PowerShell, som når du opretter politikken som beskrevet i Trin [1: Brug PowerShell](#step-1-use-powershell-to-create-a-spam-filter-policy) til at oprette en politik for spamfilter tidligere i denne artikel.

- _MakeDefault-parameteren_, der ændrer den angivne politik til standardpolitikken (gælder for alle, altid Laveste prioritet, og du kan ikke slette den) er kun tilgængelig, når du redigerer en politik for spamfilter i PowerShell.
- Du kan ikke omdøbe en politik for spamfilter ( **cmdlet'en Set-HostedContentFilterPolicy** har ingen _Name-parameter_ ). Når du omdøber en antispampolitik i Microsoft 365 Defender, omdøber du kun reglen for _spamfilter_.

Hvis du vil ændre en politik for spamfilter, skal du bruge denne syntaks:

```PowerShell
Set-HostedContentFilterPolicy -Identity "<PolicyName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

> [!NOTE]
> Hvis du vil have detaljeret vejledning [](quarantine-policies.md) til at angive karantænepolitikken, der skal bruges i en politik for spamfilter, skal du se Brug PowerShell til at angive karantænepolitikken [i antispampolitikker](quarantine-policies.md#anti-spam-policies-in-powershell).

### <a name="use-powershell-to-modify-spam-filter-rules"></a>Brug PowerShell til at ændre regler for spamfilter

Den eneste indstilling, der ikke er tilgængelig, når du ændrer en regel for spamfilter i PowerShell, er parameteren Enabled, der giver dig mulighed for at oprette en deaktiveret regel. Hvis du vil aktivere eller deaktivere eksisterende regler for spamfilter, skal du se næste afsnit.

Ellers er der ingen yderligere indstillinger tilgængelige, når du ændrer en regel for spamfilter i PowerShell. De samme indstillinger er tilgængelige, når du opretter en regel som beskrevet i Trin [2: Brug PowerShell](#step-2-use-powershell-to-create-a-spam-filter-rule) til at oprette en spamfilterregel tidligere i denne artikel.

Hvis du vil ændre en regel for spamfilter, skal du bruge denne syntaks:

```PowerShell
Set-HostedContentFilterRule -Identity "<RuleName>" <Settings>
```

I dette eksempel omdøbes den eksisterende regel for spamfilter med navnet `{Fabrikam Spam Filter}`.

```powershell
Set-HostedContentFilterRule -Identity "{Fabrikam Spam Filter}" -Name "Fabrikam Spam Filter"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [under Set-HostedContentFilterRule](/powershell/module/exchange/set-hostedcontentfilterrule).

### <a name="use-powershell-to-enable-or-disable-spam-filter-rules"></a>Brug PowerShell til at aktivere eller deaktivere regler for spamfilter

Aktivering eller deaktivering af en regel for spamfilter i PowerShell aktiverer eller deaktiverer hele politikken for uønsket post (reglen for spamfilter og den tildelte politik for spamfilter). Du kan ikke aktivere eller deaktivere standardpolitikken for uønsket post (den anvendes altid på alle modtagere).

Hvis du vil aktivere eller deaktivere en regel for spamfilter i PowerShell, skal du bruge denne syntaks:

```PowerShell
<Enable-HostedContentFilterRule | Disable-HostedContentFilterRule> -Identity "<RuleName>"
```

I dette eksempel deaktiveres reglen for spamfilter med navnet Marketingafdeling.

```PowerShell
Disable-HostedContentFilterRule -Identity "Marketing Department"
```

I dette eksempel kan du bruge den samme regel.

```PowerShell
Enable-HostedContentFilterRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parameter i [Enable-HostedContentFilterRule](/powershell/module/exchange/enable-hostedcontentfilterrule) og [Disable-HostedContentFilterRule](/powershell/module/exchange/disable-hostedcontentfilterrule).

### <a name="use-powershell-to-set-the-priority-of-spam-filter-rules"></a>Brug PowerShell til at angive prioriteten af regler for spamfilter

Den højeste prioritetsværdi, du kan angive for en regel, er 0. Den laveste værdi, du kan angive, afhænger af antallet af regler. Hvis du f.eks. har fem regler, kan du bruge prioritetsværdierne 0 til 4. Hvis du ændrer prioriteten af en eksisterende regel, kan det have en overlappende effekt på andre regler. Hvis du f.eks. har fem brugerdefinerede regler (prioriteter 0 til 4), og du ændrer prioriteten af en regel til 2, ændres den eksisterende regel med prioritet 2 til prioritet 3, og reglen med prioritet 3 ændres til prioritet 4.

Hvis du vil angive prioriteten af en regel for spamfilter i PowerShell, skal du bruge følgende syntaks:

```PowerShell
Set-HostedContentFilterRule -Identity "<RuleName>" -Priority <Number>
```

I dette eksempel angives prioriteten af reglen Marketingafdeling til 2. Alle eksisterende regler, der har en prioritet, der er mindre end eller lig med 2, formindskes med 1 (deres prioritetstal øges med 1).

```PowerShell
Set-HostedContentFilterRule -Identity "Marketing Department" -Priority 2
```

**Bemærkninger**:

- Hvis du vil angive prioriteten af en ny regel, når du opretter den, skal du i stedet bruge parameteren _Priority_ på **New-HostedContentFilterRule-cmdlet'en** .
- Standardpolitikken for spamfilter har ikke en tilsvarende regel for spamfilter, og den har altid den uændrede prioritetsværdi **Laveste**.

### <a name="use-powershell-to-remove-spam-filter-policies"></a>Brug PowerShell til at fjerne politikker for spamfiltrering

Når du bruger PowerShell til at fjerne en politik for spamfilter, fjernes den tilsvarende regel for spamfilter ikke.

Hvis du vil fjerne en politik for spamfilter i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-HostedContentFilterPolicy -Identity "<PolicyName>"
```

I dette eksempel fjernes politikken for spamfilter med navnet Marketingafdeling.

```PowerShell
Remove-HostedContentFilterPolicy -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-HostedContentFilterPolicy](/powershell/module/exchange/remove-hostedcontentfilterpolicy).

### <a name="use-powershell-to-remove-spam-filter-rules"></a>Brug PowerShell til at fjerne regler for spamfilter

Når du bruger PowerShell til at fjerne en regel for spamfilter, fjernes den tilsvarende politik for spamfilter ikke.

Hvis du vil fjerne en regel for spamfilter i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-HostedContentFilterRule -Identity "<PolicyName>"
```

I dette eksempel fjernes reglen for spamfilter med navnet Marketingafdeling.

```PowerShell
Remove-HostedContentFilterRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-HostedContentFilterRule](/powershell/module/exchange/remove-hostedcontentfilterrule).

## <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer fungerede?

### <a name="send-a-gtube-message-to-test-your-spam-policy-settings"></a>Send en GTUBE-meddelelse for at teste dine indstillinger for spampolitik

> [!NOTE]
> Disse trin fungerer kun, hvis den mailorganisation, du sender GTUBE-meddelelsen fra, ikke scanner for udgående spam. Hvis den gør det, kan du ikke sende testmeddelelsen.

Generic Test for Unsolicited Bulk Email (GTUBE) er en tekststreng, som du medtager i en testmeddelelse for at bekræfte din organisations indstillinger for uønsket post. En GTUBE-meddelelse ligner tekstfilen European Institute for Computer Antivirus Research (EICAR) til test af indstillinger for malware.

Medtag følgende GTUBE-tekst i en mail på en enkelt linje uden mellemrum eller linjeskift:

```text
XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
```
