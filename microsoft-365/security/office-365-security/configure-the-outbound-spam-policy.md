---
title: Konfigurere udgående spamfiltrering
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a44764e9-a5d2-4c67-8888-e7fb871c17c7
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om, hvordan du får vist, opretter, redigerer og sletter politikker for udgående spam Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7f635eb17d458ca707f7a18d3eb1f7fe655bd2b9
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63587302"
---
# <a name="configure-outbound-spam-filtering-in-eop"></a>Konfigurere udgående spamfiltrering i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående Exchange Online Protection -organisationer (EOP) uden Exchange Online-postkasser kontrolleres udgående mails, der sendes via EOP, automatisk for spam og usædvanlig afsendelsesaktivitet.

Udgående spam fra en bruger i organisationen angiver typisk en kompromitteret konto. Mistænkelige udgående meddelelser markeres som spam (uanset spamtillidsniveauet eller SCL) og dirigeres gennem puljen af levering med høj risiko for at beskytte tjenestens omdømme (dvs. holde Microsoft 365-kildemailservere uden for [IP-blokeringslister](high-risk-delivery-pool-for-outbound-messages.md)). Administratorer får automatisk besked om mistænkelig udgående mailaktivitet og blokerede brugere via [beskedpolitikker](../../compliance/alert-policies.md).

EOP bruger udgående spampolitikker som en del af organisationens overordnede forsvar mod spam. Du kan finde flere oplysninger [under Beskyttelse mod uønsket post](anti-spam-protection.md).

Administratorer kan få vist, redigere og konfigurere (men ikke slette) standardpolitikken for udgående spam. Hvis du vil have større granularitet, kan du også oprette brugerdefinerede politikker for udgående spam, der gælder for bestemte brugere, grupper eller domæner i organisationen. Brugerdefinerede politikker tilsidesætter altid standardpolitikken, men du kan ændre prioriteten (rækkefølgen) for dine brugerdefinerede politikker.

Du kan konfigurere politikker for udgående spam i Microsoft 365 Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til Microsoft 365-organisationer med postkasser i Exchange Online; enkeltstående EOP PowerShell til organisationer uden Exchange Online postkasser).

De grundlæggende elementer i en udgående spampolitik i EOP er:

- **Politikken for udgående spamfilter**: Angiver handlingerne for udgående spamfiltrering og meddelelsesindstillingerne.
- **Reglen for udgående spamfilter**: Angiver prioriteten og modtagerens filtre (hvem politikken gælder for) for en politik for udgående spamfilter.

Forskellen mellem disse to elementer er ikke indlysende, når du administrerer udgående spam politik i Microsoft 365 Defender portal:

- Når du opretter en politik, opretter du faktisk en regel for udgående spamfilter og den tilknyttede politik for udgående spamfilter på samme tid med samme navn for begge.
- Når du ændrer en politik, ændrer indstillinger, der er relateret til navn, prioritet, aktiveret eller deaktiveret, og modtageren filtrerer og ændrer reglen for udgående spamfilter. Alle andre indstillinger ændrer den tilknyttede politik for udgående spamfilter.
- Når du fjerner en politik, fjernes reglen for udgående spamfilter og den tilknyttede politik for udgående spamfilter.

I Exchange Online PowerShell eller enkeltstående EOP PowerShell administrerer du politikken og reglen separat. Du kan finde flere oplysninger i [afsnittet Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies) til at konfigurere politikker for udgående spam senere i denne artikel.

Hver organisation har en indbygget udgående spampolitik kaldet Standard, der har disse egenskaber:

- Politikken anvendes på alle modtagere i organisationen, selvom der ikke er knyttet nogen regel for udgående spamfilter (modtagerfiltre) til politikken.
- Politikken har den brugerdefinerede **prioritetsværdi Laveste** , som du ikke kan ændre (politikken anvendes altid sidst). Eventuelle brugerdefinerede politikker, du opretter, har altid en højere prioritet end politikken Standard.
- Politikken er standardpolitikken (egenskaben **IsDefault** har værdien ), `True`og du kan ikke slette standardpolitikken.

For at øge effektiviteten af udgående spamfiltrering kan du oprette brugerdefinerede politikker for udgående spam med strengere indstillinger, der anvendes for bestemte brugere eller grupper af brugere.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til siden **med indstillinger for uønsket post** skal du bruge <https://security.microsoft.com/antispam>.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du Forbind Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser **i Exchange Online,** før du kan udføre procedurerne i denne artikel:
  - Hvis du vil tilføje, redigere og slette politikker for udgående spam, skal du være medlem af **rollegrupperne Organisationsadministration** **eller Sikkerhedsadministrator** .
  - For skrivebeskyttet adgang til udgående spampolitikker skal du være medlem af **rollegrupperne Global Læser** eller **Sikkerhedslæser** .

  Du kan finde flere [oplysninger i Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Bemærkninger**:

  - Hvis du føjer brugere til den Azure Active Directory rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser og tilladelser til andre  funktioner Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - **Rollegruppen Skrivebeskyttet** organisationsadministration i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) også skrivebeskyttet adgang til funktionen.

- For vores anbefalede indstillinger for udgående spampolitikker skal du se [Politikindstillinger for EOP-udgående spamfilter](recommended-settings-for-eop-and-office365.md#eop-outbound-spam-policy-settings).

- Standardpolitikken [](../../compliance/alert-policies.md) for påmindelser med navnet Grænse for afsendelse af mail er **overskredet,** Mistænkelige mønstre for  afsendelse af mails registreret og Bruger begrænset fra at sende mail sender allerede mailmeddelelser til medlemmer af gruppen **TenantAdmins** (**globale** administratorer) om usædvanlig udgående mailaktivitet og blokerede brugere på grund af udgående spam. Få mere at vide under [Bekræft beskedindstillingerne for begrænsede brugere](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users). Vi anbefaler, at du bruger disse beskedpolitikker i stedet for beskedindstillingerne i politikker for udgående spam.

## <a name="use-the-microsoft-365-defender-portal-to-create-outbound-spam-policies"></a>Brug Microsoft 365 Defender til at oprette politikker for udgående spam

Når du opretter en brugerdefineret politik for udgående spam i Microsoft 365 Defender-portalen, oprettes reglen for spamfilter og den tilknyttede politik for spamfilter på samme tid med det samme navn for begge.

1.  I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **&-samarbejdspolitikker** \> **& Politikker** \> \> for trussel mod **trusler** i **afsnittet Politikker.** For at gå direkte til siden **med indstillinger for uønsket post** skal du bruge <https://security.microsoft.com/antispam>.

2. Klik på **Opret ikon på siden** Antispam-politikker ![.](../../media/m365-cc-sc-create-icon.png) **Opret en** politik, og **vælg derefter** Udgående på rullelisten.

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

   - **Udelad disse brugere,** grupper og domæner: Hvis du vil tilføje undtagelser for de interne modtagere, som politikken gælder for (recpient-undtagelser), skal du vælge denne indstilling og konfigurere undtagelserne. Indstillingerne og funktionsmåden er præcis som betingelserne.

   Klik på Næste, når du er **færdig**.

5. På siden **med indstillinger for** beskyttelse, der åbnes, skal du konfigurere følgende indstillinger:
   - **Meddelelsesgrænser**: Indstillingerne i dette afsnit konfigurerer begrænsningerne for udgående mails **fra Exchange Online** postkasser:
     - **Angiv en grænse for eksterne meddelelser**: Det maksimale antal eksterne modtagere pr. time.
     - **Angiv en intern meddelelsesgrænse**: Det maksimale antal interne modtagere pr. time.
     - **Angiv en daglig meddelelsesgrænse**: Det maksimale samlede antal modtagere pr. dag.

     En gyldig værdi er 0 til 10000. Standardværdien er 0, hvilket betyder, at standardindstillingerne for tjenesten bruges. Få mere at vide under [Grænser for afsendelse](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

    Angiv en værdi i feltet, eller brug pilene for forøg/formindsk i feltet.

   - **Begrænsning for brugere, der når** meddelelsesgrænsen: Vælg en handling på rullelisten, når en af grænserne i sektionen Beskyttelsesindstillinger overskrides.

     For alle handlinger modtager de modtagere, der er angivet  i brugerens begrænsede adgang til at sende mailbeskedpolitik (og i de nu redundante Underret disse brugere og grupper, hvis en afsender blokeres pga. afsendelse af udgående **spamindstilling** senere på denne side), mailbeskeder.

     - **Begræns brugerens mulighed for at sende mail indtil følgende** dag: Dette er standardværdien. Mailbeskeder sendes, og brugeren vil ikke kunne sende flere meddelelser før den følgende dag baseret på UTC-tid. Det er ikke muligt for administratoren at tilsidesætte denne blokering.
       - Den beskedpolitik **, der** hedder Bruger har ikke adgang til at sende mail, giver administratorer (via mail og på siden & **Beskeder** \> **Vis beskeder** ).
       - Alle modtagere, der er angivet i **indstillingen Giv** bestemte personer besked, hvis en afsender blokeres pga. afsendelse af udgående spam i politikken, får også besked.
       - Brugeren kan ikke sende flere meddelelser før den følgende dag baseret på UTC-tid. Det er ikke muligt for administratoren at tilsidesætte denne blokering.
     - **Begræns** brugerens mulighed for at sende mail: Mailmeddelelser sendes,  <https://security.microsoft.com/restrictedusers> brugeren føjes til Begrænsede brugere på Microsoft 365 Defender-portalen, og brugeren kan ikke sende mail, før de fjernes fra Begrænsede brugere af en  administrator. Når en administrator fjerner brugeren fra listen, begrænses brugeren ikke igen for den pågældende dag. Du kan finde en vejledning under [Fjerne en bruger fra portalen Begrænsede brugere efter afsendelse af spammail](removing-user-from-restricted-users-portal-after-spam.md).
     - **Ingen handling, kun besked**: Mailbeskeder sendes.

   - **Regler for videresendelse**: Brug indstillingerne i dette afsnit til at styre automatisk videresendelse af **mails Exchange Online postkasser** til eksterne afsendere. Du kan få mere at vide [under Kontrollere automatisk videresendelse af eksterne mails Microsoft 365](external-email-forwarding.md).

     > [!NOTE]
     > Når automatisk videresendelse er deaktiveret, modtager modtageren en rapport om manglende levering (også kaldet en NDR eller meddelelse om ikke-leveret post), hvis eksterne afsendere sender mails til en postkasse, hvor videresendelse er på plads. Hvis meddelelsen sendes af en intern afsender, og  videresendelsesmetoden er videresendelse af [postkasse (også](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) kaldet _SMTP-videresendelse_), får den interne afsender NDR. Den interne afsender modtager ikke en NDR, hvis videresendelsen skete på grund af en indbakkeregel.

     Vælg en af følgende handlinger på **rullelisten Regler for automatisk** videresendelse:

     - **Automatisk – Systemkontrolleret**: Tillader udgående spamfiltrering for at styre automatisk videresendelse af eksterne mails. Dette er standardværdien.
     - **Til**: Automatisk videresendelse af eksterne mails er ikke deaktiveret af politikken.
     - **Fra**: Al automatisk ekstern videresendelse af mail er deaktiveret af politikken.

   - **Meddelelser**: Brug indstillingerne i sektionen til at konfigurere flere modtagere, som skal modtage kopier og meddelelser om mistænkelige udgående mails:

     - **Send en kopi af mistænkelig** udgående, der overskrider disse begrænsninger for disse brugere og grupper: Denne indstilling føjer de angivne modtagere til feltet Bcc i mistænkelige udgående meddelelser.

       > [!NOTE]
       > Denne indstilling fungerer kun i standardpolitikken for udgående spam. Det fungerer ikke i brugerdefinerede politikker for udgående spam, som du opretter.

       Markér afkrydsningsfeltet for at aktivere denne indstilling. I den dialogboks, der vises, skal du klikke i feltet, angive en gyldig mailadresse og derefter trykke på Enter eller vælge den fulde værdi, der vises under feltet.

       Gentag dette trin så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Ikonet Fjern.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   - **Giv disse brugere og grupper besked, hvis en afsender blokeres på grund af afsendelse af udgående spam**

     > [!IMPORTANT]
     >
     > - Denne indstilling frarådes fra politikker for udgående spam.
     >
     > - Standardpolitikken [for](../../compliance/alert-policies.md) påmindelser  kaldet Bruger, der er begrænset fra at sende mail, sender allerede mailbeskeder til medlemmer af **gruppen TenantAdmins** (globale administratorer), når brugere **blokeres** pga. overskrider begrænsningerne i sektionen **Modtagergrænser**. **Vi anbefaler på det kraftigste, at du bruger** påmindelsespolitikken i stedet for denne indstilling i politikken for udgående spam til at underrette administratorer og andre brugere. Du kan finde en vejledning [i Bekræfte indstillingerne for påmindelse for brugere med begrænset adgang](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).

   Klik på Næste, når du er **færdig**.

6. Gennemgå dine **indstillinger** på siden Gennemse, der vises. Du kan vælge **Rediger** i hver sektion for at ændre indstillingerne i sektionen. Eller du kan klikke **på** Tilbage eller vælge den bestemte side i guiden.

   Klik på Opret, når du er **færdig**.

7. Klik på Udført på bekræftelsessiden, der **vises**.

## <a name="use-the-microsoft-365-defender-portal-to-view-outbound-spam-policies"></a>Brug portalen Microsoft 365 Defender til at få vist politikker for udgående spam

1.  I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **&-samarbejdspolitikker** \> **& Politikker** \> \> for trussel mod **trusler** i **afsnittet Politikker.** For at gå direkte til siden **med indstillinger for uønsket post** skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Anti-spam-politikker** skal du se efter en af følgende værdier:
   - Værdien **Type** er **brugerdefineret politik for udgående spam**
   - Værdien **Navn** er en **politik for udgående uønsket post (standard)**

   Følgende egenskaber vises på listen over antispampolitikker:

   - **Navn**
   - **Status**
   - **Prioritet**
   - **Type**

3. Når du vælger en udgående spampolitik ved at klikke på navnet, vises politikindstillingerne i en pop op-meddelelse.

## <a name="use-the-microsoft-365-defender-portal-to-modify-outbound-spam-policies"></a>Brug portalen Microsoft 365 Defender til at ændre politikker for udgående spam

1. I portalen Microsoft 365 Defender skal du gå til **& politikker** \> for **samarbejde & politikker** \>  \> for trussel mod **uønsket post** i **afsnittet** Politikker.

2. På siden **Antispam-politikker** skal du vælge en udgående spampolitik på listen ved at klikke på navnet:
   - En brugerdefineret politik, du har oprettet, hvor værdien i kolonnen **Type** er **brugerdefineret politik for udgående spam**.
   - Standardpolitikken for **udgående uønsket post (standard).**

3. I pop op-vindue med politikoplysninger skal du **vælge Rediger** i hver sektion for at ændre indstillingerne i sektionen. Du kan finde flere oplysninger om indstillingerne i det forrige [afsnit Brug Microsoft 365 Defender til at oprette politikker for udgående spam](#use-the-microsoft-365-defender-portal-to-create-outbound-spam-policies) i denne artikel.

   For standardpolitikken for udgående spam er sektionen Anvendt  på ikke tilgængelig (politikken gælder for alle), og du kan ikke omdøbe politikken.

Hvis du vil aktivere eller deaktivere en politik, angive prioritetsrækkefølgen for politikken eller konfigurere beskeder til slutbrugere, skal du se følgende afsnit.

### <a name="enable-or-disable-custom-outbound-spam-policies"></a>Aktivere eller deaktivere brugerdefinerede politikker for udgående spam

Du kan ikke deaktivere standardpolitikken for udgående spam.

1. I portalen Microsoft 365 Defender skal du gå til **& politikker** \> for **samarbejde & politikker** \>  \> for trussel mod **uønsket post** i **afsnittet** Politikker.

2. På siden **Anti-spam-politikker** skal du vælge en politik med værdien **Type** for Brugerdefineret politik for udgående **spam** på listen ved at klikke på navnet.

3. Øverst i pop op-vindue med politikoplysninger, der vises, får du vist en af følgende værdier:
   - **Politik deaktiveret**: Hvis du vil aktivere politikken, skal du klikke ![på ikonet Slå til.](../../media/m365-cc-sc-turn-on-off-icon.png) **Slå til** .
   - **Politik slået til**: Hvis du vil deaktivere politikken, skal du klikke ![på Ikonet Slå fra.](../../media/m365-cc-sc-turn-on-off-icon.png) **Slå fra**.

4. I bekræftelsesdialogboksen, der vises, skal **du klikke på Aktivér** **eller Slå fra**.

5. Klik **på Luk** i pop op-menuen med politikoplysninger.

Tilbage på hovedpolitiksiden vil **politikkens statusværdi** **være Til eller** **Fra**.

### <a name="set-the-priority-of-custom-outbound-spam-policies"></a>Angiv prioriteten af brugerdefinerede udgående spampolitikker

Som standard får udgående spampolitikker en prioritet, der er baseret på den rækkefølge, de blev oprettet i (nyere politikker har lavere prioritet end ældre politikker). Et tal for lavere prioritet angiver en højere prioritet for politikken (0 er den højeste), og politikkerne behandles i prioritetsrækkefølgen (politikker med højere prioritet behandles før politikker med lavere prioritet). Der er ikke to politikker, der kan have samme prioritet, og behandling af politikker stopper, når den første politik er anvendt.

Hvis du vil ændre prioriteten af en politik, skal du klikke  på Forøg prioritet eller Formindsk prioritet i egenskaberne for politikken (du kan ikke direkte ændre tallet prioritet i Microsoft 365 Defender portal). Det giver kun mening at ændre prioriteten af en politik, hvis du har flere politikker.

 **Bemærkninger**:

- I Microsoft 365 Defender-portalen kan du kun ændre prioriteten af politikken for udgående spam, når du har oprettet den. I PowerShell kan du tilsidesætte standardprioriteten, når du opretter reglen for spamfilter (hvilket kan påvirke prioriteten af eksisterende regler).
- Politikker for udgående spam behandles i den rækkefølge, de vises (den første politik har **prioritetsværdien** 0). Standardpolitikken for udgående spam har prioritetsværdien **Laveste**, og du kan ikke ændre den.

1. I portalen Microsoft 365 Defender skal du gå til **& politikker** \> for **samarbejde & politikker** \>  \> for trussel mod **uønsket post** i **afsnittet** Politikker.

2. På siden **Antispam-politikker** skal du vælge en politik med værdien **Type** for Brugerdefineret politik for udgående **spam** på listen ved at klikke på navnet.

3. Øverst i pop op-vindue med politikoplysninger, der vises, får du vist  Forøg  prioritet eller Formindsk prioritet baseret på den aktuelle prioritetsværdi og antallet af brugerdefinerede politikker:
   - Politikken for udgående spam med værdien **Prioritet** **0 har** kun indstillingen **Formindsk** prioritet tilgængelig.
   - Politikken for udgående spam med den laveste **prioritetsværdi** (f.eks **. 3**) har kun indstillingen **Forøg** prioritet tilgængelig.
   - Hvis du har tre eller flere udgående spampolitikker, har politikkerne mellem de højeste og laveste prioritetsværdier både indstillingerne Forøg prioritet og **Formindsk** prioritet.

   Klik på ![ikonet Forøg prioritet.](../../media/m365-cc-sc-increase-icon.png) **Forøg** prioritet ![eller ikonet Formindsk prioritet](../../media/m365-cc-sc-decrease-icon.png) **Formindsk prioritet** for at **ændre værdien** Prioritet.

4. Når du er færdig, skal du **klikke på** Luk i pop op-menuen med politikoplysninger.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-outbound-spam-policies"></a>Brug portalen Microsoft 365 Defender til at fjerne brugerdefinerede politikker for udgående spam

Når du bruger Microsoft 365 Defender til at fjerne en brugerdefineret udgående spampolitik, slettes både reglen for spamfilter og den tilsvarende politik for spamfilter. Du kan ikke fjerne standardpolitikken for udgående spam.

1.  I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **&-samarbejdspolitikker** \> **& Politikker** \> \> for trussel mod **trusler** i **afsnittet Politikker.** For at gå direkte til siden **med indstillinger for uønsket post** skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Anti-spam-politikker** skal du vælge en politik med værdien **Type** for Brugerdefineret politik for udgående **spam** på listen ved at klikke på navnet. Øverst i pop op-vindue med politikoplysninger, der vises, skal du klikke på ![ikonet Flere handlinger.](../../media/m365-cc-sc-more-actions-icon.png) **Flere handlinger** \> ![Ikonet Slet politik **Slet**](../../media/m365-cc-sc-delete-icon.png) politik.

3. Klik på Ja i bekræftelsesdialogboksen, der **vises**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies"></a>Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at konfigurere politikker for udgående spam

Som beskrevet tidligere består en politik for udgående spam af en politik for udgående spamfilter og en regel for udgående spamfilter.

I Exchange Online PowerShell eller enkeltstående EOP PowerShell fremgår forskellen mellem politikker for udgående spamfilter og regler for udgående spamfilter tydeligt. Du administrerer politikker for udgående spamfilter **\*ved hjælp af cmdlet'erne -HostedOutboundSpamFilterPolicy**, og du administrerer regler for udgående spamfilter ved hjælp af cmdlet'erne **-HostedOutboundSpamFilterRule.\***

- I PowerShell opretter du først politikken for udgående spamfilter, og derefter opretter du reglen for udgående spamfilter, der identificerer den politik, som reglen gælder for.
- I PowerShell ændrer du indstillingerne i politikken for udgående spamfilter og reglen for udgående spamfilter separat.
- Når du fjerner en politik for udgående spamfilter fra PowerShell, fjernes den tilsvarende regel for udgående spamfilter ikke automatisk og omvendt.

### <a name="use-powershell-to-create-outbound-spam-policies"></a>Brug PowerShell til at oprette udgående spampolitikker

Oprettelse af en politik for udgående spam i PowerShell er en proces i to trin:

1. Opret politikken for udgående spamfilter.
2. Opret reglen for udgående spamfilter, der angiver den politik for filtrering af udgående spam, som reglen gælder for.

   **Bemærkninger**:

   - Du kan oprette en ny regel for udgående spamfilter og tildele den en eksisterende, ikke-tilknyttet politik for udgående spamfilter. En regel for udgående spamfilter kan ikke knyttes til mere end én politik for udgående spamfilter.
   - Du kan konfigurere følgende indstillinger for nye politikker for udgående spamfilter i PowerShell, der ikke er tilgængelige i Microsoft 365 Defender-portalen, før du har oprettet politikken:
     - Opret den nye politik som deaktiveret (_Aktiveret_ `$false` på **cmdlet'en New-HostedOutboundSpamFilterRule** ).
     - Angiv prioriteten af politikken under oprettelse (_Prioritet_ _\<Number\>_) på **cmdlet'en New-HostedOutboundSpamFilterRule** ).
   - En ny politik for udgående spamfilter, som du opretter i PowerShell, er ikke synlig i Microsoft 365 Defender-portalen, før du tildeler politikken til en regel for udgående spamfilter.

#### <a name="step-1-use-powershell-to-create-an-outbound-spam-filter-policy"></a>Trin 1: Brug PowerShell til at oprette en politik for udgående spamfilter

Hvis du vil oprette en politik for udgående spamfilter, skal du bruge denne syntaks:

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

I dette eksempel oprettes en ny politik for udgående spamfilter med navnet Contoso-ledere med følgende indstillinger:

- Modtagersatsgrænserne er begrænset til mindre værdier, som standardværdierne. Få mere at vide under [Send grænser på tværs Microsoft 365 indstillinger](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options).

- Når en af grænserne er nået, er brugeren forhindret i at sende meddelelser.

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "Contoso Executives" -RecipientLimitExternalPerHour 400 -RecipientLimitInternalPerHour 800 -RecipientLimitPerDay 800 -ActionWhenThresholdReached BlockUser
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/new-hostedoutboundspamfilterpolicy).

#### <a name="step-2-use-powershell-to-create-an-outbound-spam-filter-rule"></a>Trin 2: Brug PowerShell til at oprette en regel for udgående spamfilter

Hvis du vil oprette en regel for udgående spamfilter, skal du bruge denne syntaks:

```PowerShell
New-HostedOutboundSpamFilterRule -Name "<RuleName>" -HostedOutboundSpamFilterPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

I dette eksempel oprettes en ny regel for udgående spamfilter med navnet Contoso Executives med disse indstillinger:

- Politikken for udgående spamfilter med navnet Contoso Executives er knyttet til reglen.
- Reglen gælder for medlemmer af den gruppe, der hedder Contoso Executives Group.

```PowerShell
New-HostedOutboundSpamFilterRule -Name "Contoso Executives" -HostedOutboundSpamFilterPolicy "Contoso Executives" -FromMemberOf "Contoso Executives Group"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-HostedOutboundSpamFilterRule](/powershell/module/exchange/new-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-view-outbound-spam-filter-policies"></a>Brug PowerShell til at få vist politikker for udgående spamfilter

Kør denne kommando for at returnere en oversigt over alle politikker for udgående spamfilter:

```PowerShell
Get-HostedOutboundSpamFilterPolicy
```

Hvis du vil returnere detaljerede oplysninger om en bestemt politik for udgående spamfilter, skal du bruge denne syntaks:

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

I dette eksempel returneres alle egenskabsværdierne for politikken for udgående spamfilter med navnet Ledere.

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "Executives" | Format-List
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/get-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-view-outbound-spam-filter-rules"></a>Brug PowerShell til at få vist regler for udgående spamfilter

Hvis du vil have vist eksisterende regler for udgående spamfilter, skal du bruge følgende syntaks:

```PowerShell
Get-HostedOutboundSpamFilterRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>]
```

Kør denne kommando for at returnere en oversigt over alle regler for udgående spamfilter:

```PowerShell
Get-HostedOutboundSpamFilterRule
```

Hvis du vil filtrere listen efter aktiverede eller deaktiverede regler, skal du køre følgende kommandoer:

```PowerShell
Get-HostedOutboundSpamFilterRule -State Disabled
```

```PowerShell
Get-HostedOutboundSpamFilterRule -State Enabled
```

Hvis du vil returnere detaljerede oplysninger om en bestemt regel for udgående spamfilter, skal du bruge denne syntaks:

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

I dette eksempel returneres alle egenskabsværdierne for reglen for udgående spamfilter med navnet Contoso Executives.

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "Contoso Executives" | Format-List
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-HostedOutboundSpamFilterRule](/powershell/module/exchange/get-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-modify-outbound-spam-filter-policies"></a>Brug PowerShell til at ændre politikker for udgående spamfilter

De samme indstillinger er tilgængelige, når du ændrer en politik for malwarefiltrering i PowerShell, som når du opretter politikken som beskrevet i Trin [1: Brug PowerShell](#step-1-use-powershell-to-create-an-outbound-spam-filter-policy) til at oprette en sektion med en politik for udgående spamfilter tidligere i denne artikel.

> [!NOTE]
> Du kan ikke omdøbe en politik for udgående spamfilter ( **cmdlet'en Set-HostedOutboundSpamFilterPolicy** har ingen _Navneparameter_ ). Når du omdøber en politik for udgående spam i Microsoft 365 Defender-portalen, omdøber du kun reglen for udgående _spamfilter_.

Hvis du vil ændre en politik for udgående spamfilter, skal du bruge denne syntaks:

```PowerShell
Set-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/set-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-modify-outbound-spam-filter-rules"></a>Brug PowerShell til at ændre regler for udgående spamfilter

Den eneste indstilling, der ikke er tilgængelig, når du ændrer en regel for udgående spamfilter i PowerShell,  er parameteren Enabled, der gør det muligt at oprette en deaktiveret regel. Hvis du vil aktivere eller deaktivere eksisterende regler for udgående spamfilter, skal du se næste afsnit.

Ellers er der ingen yderligere indstillinger tilgængelige, når du ændrer en regel for udgående spamfilter i PowerShell. De samme indstillinger er tilgængelige, når du opretter en regel som beskrevet i Trin [2: Brug PowerShell](#step-2-use-powershell-to-create-an-outbound-spam-filter-rule) til at oprette en sektion med en regel for udgående spamfilter tidligere i denne artikel.

Hvis du vil ændre en regel for udgående spamfilter, skal du bruge denne syntaks:

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-HostedOutboundSpamFilterRule](/powershell/module/exchange/set-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-enable-or-disable-outbound-spam-filter-rules"></a>Brug PowerShell til at aktivere eller deaktivere regler for udgående spamfilter

Aktivering eller deaktivering af en regel for udgående spamfilter i PowerShell aktiverer eller deaktiverer hele politikken for udgående spam (reglen for udgående spamfilter og politikken for udgående spamfilter). Du kan ikke aktivere eller deaktivere standardpolitikken for udgående spam (den anvendes altid på alle modtagere).

Hvis du vil aktivere eller deaktivere en regel for udgående spamfilter i PowerShell, skal du bruge denne syntaks:

```PowerShell
<Enable-HostedOutboundSpamFilterRule | Disable-HostedOutboundSpamFilterRule> -Identity "<RuleName>"
```

I dette eksempel deaktiveres reglen for udgående spamfilter med navnet Marketingafdeling.

```PowerShell
Disable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

I dette eksempel kan du bruge den samme regel.

```PowerShell
Enable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parameter i [Enable-HostedOutboundSpamFilterRule](/powershell/module/exchange/enable-hostedoutboundspamfilterrule) og [Disable-HostedOutboundSpamFilterRule](/powershell/module/exchange/disable-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-set-the-priority-of-outbound-spam-filter-rules"></a>Brug PowerShell til at angive prioriteten af regler for udgående spamfilter

Den højeste prioritetsværdi, du kan angive for en regel, er 0. Den laveste værdi, du kan angive, afhænger af antallet af regler. Hvis du f.eks. har fem regler, kan du bruge prioritetsværdierne 0 til 4. Hvis du ændrer prioriteten af en eksisterende regel, kan det have en overlappende effekt på andre regler. Hvis du f.eks. har fem brugerdefinerede regler (prioriteter 0 til 4), og du ændrer prioriteten af en regel til 2, ændres den eksisterende regel med prioritet 2 til prioritet 3, og reglen med prioritet 3 ændres til prioritet 4.

Hvis du vil angive prioriteten af en regel for udgående spamfilter i PowerShell, skal du bruge følgende syntaks:

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" -Priority <Number>
```

I dette eksempel angives prioriteten af reglen Marketingafdeling til 2. Alle eksisterende regler, der har en prioritet, der er mindre end eller lig med 2, formindskes med 1 (deres prioritetstal øges med 1).

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "Marketing Department" -Priority 2
```

**Bemærkninger**:

- Hvis du vil angive prioriteten af en ny regel, når du opretter den, skal du bruge parameteren _Prioritet_ på **cmdlet'en New-HostedOutboundSpamFilterRule** i stedet.
- Politikken for udgående standardspamfilter har ikke en tilsvarende regel for spamfilter, og den har altid den uændrede prioritetsværdi **Laveste**.

### <a name="use-powershell-to-remove-outbound-spam-filter-policies"></a>Brug PowerShell til at fjerne politikker for udgående spamfilter

Når du bruger PowerShell til at fjerne en politik for udgående spamfilter, fjernes den tilsvarende regel for udgående spamfilter ikke.

Hvis du vil fjerne en politik for udgående spamfilter i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>"
```

I dette eksempel fjernes politikken for udgående spamfilter med navnet Marketingafdeling.

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/remove-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-remove-outbound-spam-filter-rules"></a>Brug PowerShell til at fjerne regler for udgående spamfilter

Når du bruger PowerShell til at fjerne en regel for udgående spamfilter, fjernes den tilsvarende politik for udgående spamfilter ikke.

Hvis du vil fjerne en regel for udgående spamfilter i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "<PolicyName>"
```

I dette eksempel fjernes reglen for udgående spamfilter med navnet Marketingafdeling.

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-HostedOutboundSpamFilterRule](/powershell/module/exchange/remove-hostedoutboundspamfilterrule).

## <a name="for-more-information"></a>Du kan finde flere oplysninger

[Fjern blokerede brugere fra portalen Begrænsede brugere](removing-user-from-restricted-users-portal-after-spam.md)

[Pulje til levering med høj risiko for udgående meddelelser](high-risk-delivery-pool-for-outbound-messages.md)

[Ofte stillede spørgsmål om beskyttelse mod spam](anti-spam-protection-faq.yml)

[Rapport over automatisk videresendte meddelelser](mfi-auto-forwarded-messages-report.md)
