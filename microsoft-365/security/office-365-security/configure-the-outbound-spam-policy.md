---
title: Konfigurer filtrering af udgående spam
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
description: Administratorer kan få mere at vide om, hvordan de får vist, opretter, ændrer og sletter udgående spampolitikker i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 690d4def4081812653cb533765f6c61cca7d1e90
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115823"
---
# <a name="configure-outbound-spam-filtering-in-eop"></a>Konfigurer filtrering af udgående spam i EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående Exchange Online Protection organisationer (EOP) uden Exchange Online postkasser, kontrolleres udgående mails, der sendes via EOP, automatisk for spam og usædvanlig afsendelsesaktivitet.

Udgående spam fra en bruger i din organisation angiver typisk en kompromitteret konto. Mistænkelige udgående meddelelser er markeret som spam (uanset niveauet for spamsikkerhed eller SCL) og dirigeres gennem den [risikobetonede leveringspulje](high-risk-delivery-pool-for-outbound-messages.md) for at hjælpe med at beskytte tjenestens omdømme (dvs. hold Microsoft 365 kildemailservere væk fra IP-bloklister). Administratorer får automatisk besked om mistænkelig udgående mailaktivitet og blokerede brugere via [advarselspolitikker](../../compliance/alert-policies.md).

EOP bruger politikker for udgående spam som en del af organisationens overordnede forsvar mod spam. Du kan få flere oplysninger under [Beskyttelse mod spam](anti-spam-protection.md).

Administratorer kan få vist, redigere og konfigurere (men ikke slette) standardpolitikken for udgående spam. For at opnå større granularitet kan du også oprette brugerdefinerede udgående spampolitikker, der gælder for bestemte brugere, grupper eller domæner i din organisation. Brugerdefinerede politikker har altid forrang frem for standardpolitikken, men du kan ændre prioriteten (kører rækkefølge) for dine brugerdefinerede politikker.

Du kan konfigurere udgående spampolitikker på Microsoft 365 Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til Microsoft 365 organisationer med postkasser i Exchange Online; separat EOP PowerShell til organisationer uden Exchange Online postkasser).

De grundlæggende elementer i en politik for udgående spam i EOP er:

- **Filterpolitikken for udgående spam**: Angiver handlingerne for udgående spamfiltreringsdomme og meddelelsesindstillingerne.
- **Filterreglen for udgående spam**: Angiver prioritets- og afsenderfiltrene (hvem politikken gælder for) for en filterpolitik for udgående spam.

Forskellen mellem disse to elementer er ikke indlysende, når du administrerer udgående spam-politi på Microsoft 365 Defender portalen:

- Når du opretter en politik, opretter du faktisk en regel for filter for udgående spam og den tilknyttede filterpolitik for udgående spam på samme tid ved hjælp af det samme navn for begge.
- Når du ændrer en politik, ændrer indstillinger, der er relateret til navn, prioritet, aktiveret eller deaktiveret, og afsenderfiltre den udgående spamfilterregel. Alle andre indstillinger ændrer den tilknyttede filterpolitik for udgående spam.
- Når du fjerner en politik, fjernes reglen for filter for udgående spam og den tilknyttede filterpolitik for udgående spam.

I Exchange Online PowerShell eller enkeltstående EOP PowerShell kan du administrere politikken og reglen separat. Du kan få flere oplysninger i afsnittet [Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at konfigurere udgående spampolitikker](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies) senere i denne artikel.

Alle organisationer har en indbygget politik for udgående spam med navnet Standard, der har disse egenskaber:

- Politikken anvendes på alle afsendere i organisationen, selvom der ikke er knyttet nogen filterregel for udgående spam (afsenderfiltre) til politikken.
- Politikken har den brugerdefinerede prioritetsværdi **Laveste** , som du ikke kan ændre (politikken anvendes altid sidst). Alle brugerdefinerede politikker, du opretter, har altid en højere prioritet end politikken med navnet Standard.
- Politikken er standardpolitikken (egenskaben **IsDefault** har værdien `True`), og du kan ikke slette standardpolitikken.

Hvis du vil øge effektiviteten af filtrering af udgående spam, kan du oprette brugerdefinerede politikker for udgående spam med strengere indstillinger, der anvendes på bestemte brugere eller grupper af brugere.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Indstillinger for spam** , skal du bruge <https://security.microsoft.com/antispam>.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, [skal du se Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du se Forbind til Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser i **Exchange Online**, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil tilføje, redigere og slette udgående spampolitikker, skal du være medlem af rollegrupperne **Organisationsadministration** eller **Sikkerhedsadministrator** .
  - Hvis du vil have skrivebeskyttet adgang til udgående spampolitikker, skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser** .

  Du kan få flere oplysninger [under Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Noter**:

  - Tilføjelse af brugere til den tilsvarende Azure Active Directory rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - Rollegruppen **Vis kun organisationsadministration** i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) giver også skrivebeskyttet adgang til funktionen.

- Du kan se vores anbefalede indstillinger for politikker for udgående spam under [Politikindstillinger for udgående spamfilter for EOP](recommended-settings-for-eop-and-office365.md#eop-outbound-spam-policy-settings).

- [Standardpolitikkerne for beskeder](../../compliance/alert-policies.md) med navnet **Grænse for afsendelse af mail er overskredet**, **der er registreret mistænkelige mønstre for afsendelse af mails**, og **brugeren er begrænset til at sende mails**, der allerede sender mailmeddelelser til medlemmer af gruppen **TenantAdmins** (**globale administratorer**) om usædvanlig udgående mailaktivitet og blokerede brugere på grund af udgående spam. Du kan finde flere oplysninger under [Kontrollér beskedindstillingerne for begrænsede brugere](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users). Vi anbefaler, at du bruger disse politikker for beskeder i stedet for meddelelsesindstillingerne i politikker for udgående spam.

## <a name="use-the-microsoft-365-defender-portal-to-create-outbound-spam-policies"></a>Brug Microsoft 365 Defender-portalen til at oprette politikker for udgående spam

Når du opretter en brugerdefineret politik for udgående spam på Microsoft 365 Defender-portalen, oprettes reglen for spamfilteret og den tilknyttede filterpolitik for spam samtidig med det samme navn for begge.

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Indstillinger for spam** , skal du bruge <https://security.microsoft.com/antispam>.

2. Klik på Ikonet Opret på ![siden **Politikker mod spam**.](../../media/m365-cc-sc-create-icon.png) **Opret en politik** , og vælg derefter **Udgående** på rullelisten.

3. Politikguiden åbnes. Konfigurer disse indstillinger **på siden Navngiv din politik**:
   - **Navn**: Angiv et entydigt, beskrivende navn til politikken.
   - **Beskrivelse**: Angiv en valgfri beskrivelse af politikken.

   Klik på **Næste**, når du er færdig.

4. På siden **Brugere, grupper og domæner** , der vises, skal du identificere de interne afsendere, som politikken gælder for (modtagerbetingelser):
   - **Brugere**: De angivne postkasser, mailbrugere eller mailkontakter.
   - **Grupper**:
     - Medlemmer af de angivne distributionsgrupper eller mailaktiverede sikkerhedsgrupper.
     - Den angivne Microsoft 365-grupper.
   - **Domæner**: Alle afsendere i de angivne [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i din organisation.

   Klik i det relevante felt, begynd at skrive en værdi, og vælg den ønskede værdi fra resultaterne. Gentag denne proces så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Fjern ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   For brugere eller grupper kan du bruge de fleste identifikatorer (navn, vist navn, alias, mailadresse, kontonavn osv.), men det tilsvarende viste navn vises i resultaterne. For brugere skal du angive en stjerne (\*) alene for at se alle tilgængelige værdier.

   Flere værdier i samme betingelse bruger OR-logik (f.eks. _\<sender1\>_ eller _\<sender2\>_). Forskellige betingelser bruger AND-logik (f.eks. _\<sender1\>_ og _\<member of group 1\>_).

   - **Udelad disse brugere, grupper og domæner**: Hvis du vil tilføje undtagelser for de interne afsendere, som politikken gælder for (modtagerundtagelser), skal du vælge denne indstilling og konfigurere undtagelserne. Indstillingerne og funktionsmåden er præcis som betingelserne.

   > [!IMPORTANT]
   > Flere forskellige betingelser eller undtagelser er ikke additive; de er inkluderende. Politikken anvendes _kun_ på de modtagere, der stemmer overens med _alle_ de angivne modtagerfiltre. Du kan f.eks. konfigurere en modtagerfilterbetingelse i politikken med følgende værdier:
   >
   > - Modtageren er: romain@contoso.com
   > - Modtageren er medlem af: Direktører
   >
   > Politikken anvendes _kun_ på romain@contoso.com, hvis han også er medlem af koncernerne Direktører. Hvis han ikke er medlem af gruppen, anvendes politikken ikke på ham.
   >
   > Hvis du på samme måde bruger det samme modtagerfilter som en undtagelse til politikken, anvendes politikken ikke _kun_ på romain@contoso.com, hvis han også er medlem af grupperne Direktører. Hvis han ikke er medlem af gruppen, gælder politikken stadig for ham.

   Klik på **Næste**, når du er færdig.

5. Konfigurer følgende indstillinger på siden **Beskyttelsesindstillinger** , der åbnes:
   - **Meddelelsesgrænser**: Indstillingerne i dette afsnit konfigurerer grænserne for udgående mails fra **Exchange Online** postkasser:
     - **Angiv en ekstern meddelelsesgrænse**: Det maksimale antal eksterne modtagere pr. time.
     - **Angiv en intern meddelelsesgrænse**: Det maksimale antal interne modtagere pr. time.
     - **Angiv en daglig meddelelsesgrænse**: Det maksimale samlede antal modtagere pr. dag.

     En gyldig værdi er 0 til 10000. Standardværdien er 0, hvilket betyder, at tjenestestandarderne bruges. Du kan få flere oplysninger under [Afsendelse af grænser](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

    Angiv en værdi i feltet, eller brug pilene til forøgelse/reduktion i feltet.

   - **Begrænsning, der er placeret på brugere, der når meddelelsesgrænsen**: Vælg en handling på rullelisten, når en af grænserne i afsnittet **Beskyttelsesindstillinger** er overskredet.

     For alle handlinger modtager de afsendere, der er angivet i **brugerens** beskedpolitik for afsendelse af mail (og i det nu overflødige **Giv disse brugere og grupper besked, hvis en afsender er blokeret på grund af afsendelse af udgående spam** senere på denne side), mailmeddelelser.

     - **Begræns brugerens adgang til at sende mails til den følgende dag**: Dette er standardværdien. Der sendes mailmeddelelser, og brugeren kan ikke sende flere meddelelser før den følgende dag baseret på UTC-tid. Administratoren kan ikke tilsidesætte denne blok.
       - Beskedpolitikken med navnet **Bruger er begrænset til at sende mailbeskeder** til administratorer (via mail og på siden **Hændelser & beskeder** \> **Få vist beskeder** ).
       - Alle modtagere, der er angivet i indstillingen **Giv bestemte personer besked, hvis en afsender er blokeret på grund af afsendelse af udgående spam** i politikken, får også besked.
       - Brugeren kan ikke sende flere meddelelser før den følgende dag baseret på UTC-tid. Administratoren kan ikke tilsidesætte denne blok.
     - **Begræns brugerens mulighed for at sende mail**: Mailmeddelelser sendes, brugeren føjes til **Brugere med begrænset** <https://security.microsoft.com/restrictedusers> adgang på Microsoft 365 Defender portalen, og brugeren kan ikke sende mail, før vedkommende fjernes fra **Begrænsede brugere** af en administrator. Når en administrator fjerner brugeren fra listen, begrænses brugeren ikke igen den pågældende dag. Du kan finde instruktioner under [Fjernelse af en bruger fra portalen Brugere med begrænset adgang efter afsendelse af spammail](removing-user-from-restricted-users-portal-after-spam.md).
     - **Ingen handling, kun besked**: Der sendes mailmeddelelser.

   - **Regler for videresendelse**: Brug indstillingerne i dette afsnit til at styre automatisk videresendelse af mails via **Exchange Online postkasser til eksterne afsendere**. Du kan få flere oplysninger under [Kontrollér automatisk ekstern videresendelse af mail i Microsoft 365](external-email-forwarding.md).

     > [!NOTE]
     > Når automatisk videresendelse er deaktiveret, modtager modtageren en rapport om manglende levering (også kaldet en meddelelse om manglende levering eller afvisning af levering), hvis eksterne afsendere sender mail til en postkasse, hvor videresendelse er på plads. Hvis meddelelsen sendes af en intern afsender, **og** videresendelsesmetoden er [videresendelse af postkasse](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) (også kendt som _SMTP-videresendelse_), får den interne afsender NDR. Den interne afsender får ikke en NDR, hvis videresendelse fandt sted på grund af en indbakkeregel.

     Vælg en af følgende handlinger på rullelisten **Regler for automatisk videresendelse** :

     - **Automatisk – Systemstyret**: Tillader filtrering af udgående spam for at styre automatisk ekstern videresendelse af mail. Dette er standardværdien.
     - **Til**: Automatisk ekstern videresendelse af mail er ikke deaktiveret af politikken.
     - **Fra**: Al automatisk ekstern videresendelse af mail er deaktiveret af politikken.

   - **Meddelelser**: Brug indstillingerne i sektionen til at konfigurere yderligere modtagere, der skal modtage kopier og meddelelser om mistænkelige udgående mails:

     - **Send en kopi af mistænkelig udgående post, der overskrider disse grænser, til disse brugere og grupper**: Denne indstilling føjer de angivne modtagere til feltet Bcc for mistænkelige udgående meddelelser.

       > [!NOTE]
       > Denne indstilling fungerer kun i standardpolitikken for udgående spam. Det fungerer ikke i brugerdefinerede politikker for udgående spam, som du opretter.

       Markér afkrydsningsfeltet for at aktivere denne indstilling. I det felt, der vises, skal du klikke i feltet, angive en gyldig mailadresse og derefter trykke på Enter eller vælge den komplette værdi, der vises under feltet.

       Gentag dette trin så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Fjern ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   - **Giv disse brugere og grupper besked, hvis en afsender er blokeret på grund af afsendelse af udgående spam**

     > [!IMPORTANT]
     >
     > - Denne indstilling er ved at blive udfaset fra udgående spampolitikker.
     >
     > - [Standardbeskedpolitikken](../../compliance/alert-policies.md) med navnet **Bruger, der er begrænset til at sende mail**, sender allerede mailmeddelelser til medlemmer af gruppen **Lejeradministratorer** (**globale administratorer**), når brugerne blokeres, fordi grænserne i afsnittet **Modtagergrænser** overskrides. **Vi anbefaler på det kraftigste, at du bruger beskedpolitikken i stedet for denne indstilling i politikken for udgående spam til at give administratorer og andre brugere besked**. Du kan finde instruktioner under [Kontrollér beskedindstillingerne for begrænsede brugere](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).

   Klik på **Næste**, når du er færdig.

6. Gennemse dine indstillinger på siden **Gennemse** , der vises. Du kan vælge **Rediger** i hver sektion for at redigere indstillingerne i sektionen. Du kan også klikke på **Tilbage** eller vælge den specifikke side i guiden.

   Klik på **Opret**, når du er færdig.

7. Klik på **Udført** på den bekræftelsesside, der vises.

## <a name="use-the-microsoft-365-defender-portal-to-view-outbound-spam-policies"></a>Brug Microsoft 365 Defender-portalen til at få vist politikker for udgående spam

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Indstillinger for spam** , skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Politikker mod spam** skal du søge efter en af følgende værdier:
   - **Typeværdien** er **brugerdefineret politik for udgående spam**
   - Værdien **navn** er **politik for udgående spam (standard)**

   Følgende egenskaber vises på listen over politikker til bekæmpelse af spam:

   - **Navn**
   - **Status**
   - **Prioritet**
   - **Type**

3. Når du vælger en politik for udgående spam ved at klikke på navnet, vises politikindstillingerne i et pop op-vindue.

## <a name="use-the-microsoft-365-defender-portal-to-modify-outbound-spam-policies"></a>Brug Microsoft 365 Defender-portalen til at ændre politikker for udgående spam

1. På Microsoft 365 Defender-portalen skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet **Politikker**.

2. På siden **Politikker for uønsket post** skal du vælge en politik for udgående spam på listen ved at klikke på navnet:
   - En brugerdefineret politik, som du har oprettet, hvor værdien i kolonnen **Type** er **Brugerdefineret politik for udgående spam**.
   - Standardpolitikken med navnet **Udgående politik for uønsket post (standard).**

3. I det pop op-vindue med politikoplysninger, der vises, skal du vælge **Rediger** i hvert afsnit for at redigere indstillingerne i sektionen. Du kan få flere oplysninger om indstillingerne i det forrige afsnit [Brug Microsoft 365 Defender-portalen til at oprette udgående spampolitikker](#use-the-microsoft-365-defender-portal-to-create-outbound-spam-policies) i denne artikel.

   For standardpolitikken for udgående spam er sektionen **Anvendt på** ikke tilgængelig (politikken gælder for alle), og du kan ikke omdøbe politikken.

Hvis du vil aktivere eller deaktivere en politik, angive prioritetsrækkefølgen for politikken eller konfigurere slutbrugermeddelelser, skal du se følgende afsnit.

### <a name="enable-or-disable-custom-outbound-spam-policies"></a>Aktivér eller deaktiver brugerdefinerede udgående spampolitikker

Du kan ikke deaktivere standardpolitikken for udgående spam.

1. På Microsoft 365 Defender-portalen skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet **Politikker**.

2. På siden **Politikker til bekæmpelse af spam** skal du vælge en politik med **typeværdien** **brugerdefineret udgående spampolitik** på listen ved at klikke på navnet.

3. Øverst i pop op-vinduet med politikoplysninger, der vises, kan du se en af følgende værdier:
   - **Politik slået fra**: Hvis du vil aktivere politikken, skal du klikke på ![Slå ikonet til.](../../media/m365-cc-sc-turn-on-off-icon.png) **Aktivér** .
   - **Politik slået** til: Hvis du vil slå politikken fra, skal du klikke på ![Slå ikonet fra.](../../media/m365-cc-sc-turn-on-off-icon.png) **Sluk for den**.

4. I den bekræftelsesdialogboks, der vises, skal du klikke **på Slå til** eller **Slå fra**.

5. Klik på **Luk** i pop op-vinduet med politikoplysninger.

Tilbage på hovedpolitiksiden **vil statusværdien** for politikken være **Til** eller **Fra**.

### <a name="set-the-priority-of-custom-outbound-spam-policies"></a>Angiv prioriteten for brugerdefinerede politikker for udgående spam

Som standard får udgående spampolitikker en prioritet, der er baseret på den rækkefølge, de blev oprettet i (nyere politikker har lavere prioritet end ældre politikker). Et lavere prioritetsnummer angiver en højere prioritet for politikken (0 er den højeste), og politikker behandles i prioriteret rækkefølge (politikker med højere prioritet behandles før politikker med lavere prioritet). Der kan ikke være to politikker, der har samme prioritet, og behandlingen af politikker stopper, når den første politik er anvendt.

Hvis du vil ændre prioriteten for en politik, skal du klikke på **Forøg prioritet** eller **Formindsk prioritet** i egenskaberne for politikken (du kan ikke direkte ændre **prioritetsnummeret** på portalen Microsoft 365 Defender). Det giver kun mening at ændre prioriteten for en politik, hvis du har flere politikker.

 **Noter**:

- I Microsoft 365 Defender-portalen kan du kun ændre prioriteten for politikken for udgående spam, når du har oprettet den. I PowerShell kan du tilsidesætte standardprioriteten, når du opretter reglen for spamfilter (hvilket kan påvirke prioriteten af eksisterende regler).
- Politikker for udgående spam behandles i den rækkefølge, de vises i (den første politik har **prioritetsværdien** 0). Standardpolitikken for udgående spam har prioritetsværdien **Laveste**, og du kan ikke ændre den.

1. På Microsoft 365 Defender-portalen skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet **Politikker**.

2. På siden **Politikker mod spam** skal du vælge en politik med **typeværdien** **Brugerdefineret udgående spampolitik** på listen ved at klikke på navnet.

3. Øverst i pop op-vinduet med politikoplysninger, der vises, kan du se **Forøg prioritet** eller **Formindsk prioritet** baseret på den aktuelle prioritetsværdi og antallet af brugerdefinerede politikker:
   - Politikken for udgående spam med **prioritetsværdien** **0** har kun indstillingen **Formindsk prioritet** tilgængelig.
   - Politikken for udgående spam med den laveste **prioritetsværdi** (f.eks. **3**) har kun indstillingen **Forøg prioritet** tilgængelig.
   - Hvis du har tre eller flere udgående spampolitikker, har politikkerne mellem de højeste og laveste prioritetsværdier både **indstillingerne Forøg prioritet** og **Formindsk prioritet** tilgængelige.

   Klik på ![ikonet Forøg prioritet.](../../media/m365-cc-sc-increase-icon.png) **Forøg prioritet** eller ![formindsk prioritetsikon](../../media/m365-cc-sc-decrease-icon.png) **Formindsk prioritet** for at ændre **prioritetsværdien** .

4. Når du er færdig, skal du klikke på **Luk** i pop op-vinduet med politikoplysninger.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-outbound-spam-policies"></a>Brug Microsoft 365 Defender-portalen til at fjerne brugerdefinerede udgående spampolitikker

Når du bruger Microsoft 365 Defender-portalen til at fjerne en brugerdefineret politik for udgående spam, slettes reglen for spamfilteret og den tilsvarende politik for spamfilter begge. Du kan ikke fjerne standardpolitikken for udgående spam.

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Indstillinger for spam** , skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Politikker til bekæmpelse af spam** skal du vælge en politik med **typeværdien** **brugerdefineret udgående spampolitik** på listen ved at klikke på navnet. Øverst i pop op-vinduet med politikoplysninger, der vises, skal du klikke på ![ikonet Flere handlinger.](../../media/m365-cc-sc-more-actions-icon.png) **Flere handlinger** \> ![Ikonet](../../media/m365-cc-sc-delete-icon.png) Slet politik **Slet politik**.

3. Klik på **Ja** i den bekræftelsesdialogboks, der vises.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies"></a>Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at konfigurere udgående spampolitikker

Som tidligere beskrevet består en politik for udgående spam af en filterpolitik for udgående spam og en regel for filter for udgående spam.

I Exchange Online PowerShell eller enkeltstående EOP PowerShell er forskellen mellem politikker for udgående spamfilter og regler for udgående spamfilter synlig. Du administrerer politikker for filter for udgående spam ved hjælp **\*af cmdlet'erne -HostedOutboundSpamFilterPolicy** , og du administrerer regler for filter for udgående spam ved hjælp **\*af -HostedOutboundSpamFilterRule-cmdlet'erne** .

- I PowerShell skal du først oprette filterpolitikken for udgående spam og derefter oprette reglen for filter for udgående spam, der identificerer den politik, som reglen gælder for.
- I PowerShell kan du ændre indstillingerne i filterpolitikken for udgående spam og reglen for filter for udgående spam separat.
- Når du fjerner en filterpolitik for udgående spam fra PowerShell, fjernes den tilsvarende regel for filter for udgående spam ikke automatisk og omvendt.

### <a name="use-powershell-to-create-outbound-spam-policies"></a>Brug PowerShell til at oprette politikker for udgående spam

Oprettelse af en politik for udgående spam i PowerShell er en proces med to trin:

1. Opret filterpolitikken for udgående spam.
2. Opret filterreglen for udgående spam, der angiver den filterpolitik for udgående spam, som reglen gælder for.

   **Noter**:

   - Du kan oprette en ny regel for filter for udgående spam og tildele den en eksisterende, ikke-tilknyttet filterpolitik for udgående spam. En regel for filter for udgående spam kan ikke knyttes til mere end én filterpolitik for udgående spam.
   - Du kan konfigurere følgende indstillinger for nye politikker for udgående spamfilter i PowerShell, der ikke er tilgængelige på Microsoft 365 Defender-portalen, før du har oprettet politikken:
     - Opret den nye politik som deaktiveret (_aktiveret_ `$false` på cmdlet'en **New-HostedOutboundSpamFilterRule** ).
     - Angiv prioriteten for politikken under oprettelse (_prioritet_ _\<Number\>_) på cmdlet'en **New-HostedOutboundSpamFilterRule** .
   - En ny filterpolitik for udgående spam, som du opretter i PowerShell, er ikke synlig på Microsoft 365 Defender-portalen, før du tildeler politikken til en regel for udgående spamfilter.

#### <a name="step-1-use-powershell-to-create-an-outbound-spam-filter-policy"></a>Trin 1: Brug PowerShell til at oprette en filterpolitik for udgående spam

Hvis du vil oprette en filterpolitik for udgående spam, skal du bruge denne syntaks:

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

I dette eksempel oprettes der en ny filterpolitik for udgående spam med navnet Contoso Executives med følgende indstillinger:

- Grænserne for modtagerfrekvensen er begrænset til mindre værdier, som standardværdierne er. Du kan få flere oplysninger under [Afsendelse af grænser på tværs af Microsoft 365 indstillinger](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options).

- Når en af grænserne er nået, forhindres brugeren i at sende meddelelser.

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "Contoso Executives" -RecipientLimitExternalPerHour 400 -RecipientLimitInternalPerHour 800 -RecipientLimitPerDay 800 -ActionWhenThresholdReached BlockUser
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [New-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/new-hostedoutboundspamfilterpolicy).

#### <a name="step-2-use-powershell-to-create-an-outbound-spam-filter-rule"></a>Trin 2: Brug PowerShell til at oprette en regel for filter for udgående spam

Hvis du vil oprette en regel for filter for udgående spam, skal du bruge denne syntaks:

```PowerShell
New-HostedOutboundSpamFilterRule -Name "<RuleName>" -HostedOutboundSpamFilterPolicy "<PolicyName>" <Sender filters> [<Sender filter exceptions>] [-Comments "<OptionalComments>"]
```

I dette eksempel oprettes der en ny regel for filter for udgående spam med navnet Contoso Executives med disse indstillinger:

- Filterpolitikken for udgående spam med navnet Contoso Executives er knyttet til reglen.
- Reglen gælder for medlemmer af gruppen med navnet Contoso Executives Group.

```PowerShell
New-HostedOutboundSpamFilterRule -Name "Contoso Executives" -HostedOutboundSpamFilterPolicy "Contoso Executives" -FromMemberOf "Contoso Executives Group"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-HostedOutboundSpamFilterRule](/powershell/module/exchange/new-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-view-outbound-spam-filter-policies"></a>Brug PowerShell til at få vist filterpolitikker for udgående spam

Hvis du vil returnere en oversigt over alle politikker for udgående spamfilter, skal du køre denne kommando:

```PowerShell
Get-HostedOutboundSpamFilterPolicy
```

Hvis du vil returnere detaljerede oplysninger om en bestemt politik for udgående spamfilter, skal du bruge denne syntaks:

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

I dette eksempel returneres alle egenskabsværdierne for filterpolitikken for udgående spam med navnet Direktører.

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "Executives" | Format-List
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Get-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/get-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-view-outbound-spam-filter-rules"></a>Brug PowerShell til at få vist regler for filter for udgående spam

Hvis du vil have vist eksisterende regler for filter for udgående spam, skal du bruge følgende syntaks:

```PowerShell
Get-HostedOutboundSpamFilterRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>]
```

Hvis du vil returnere en oversigt over alle regler for filter for udgående spam, skal du køre denne kommando:

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

Hvis du vil returnere detaljerede oplysninger om en bestemt regel for filter for udgående spam, skal du bruge denne syntaks:

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

I dette eksempel returneres alle egenskabsværdierne for filterreglen for udgående spam med navnet Contoso Executives.

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "Contoso Executives" | Format-List
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Get-HostedOutboundSpamFilterRule](/powershell/module/exchange/get-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-modify-outbound-spam-filter-policies"></a>Brug PowerShell til at ændre filterpolitikker for udgående spam

De samme indstillinger er tilgængelige, når du ændrer en politik for malwarefilter i PowerShell, som når du opretter politikken som beskrevet i [trin 1: Brug PowerShell til at oprette en politik for udgående spamfilter](#step-1-use-powershell-to-create-an-outbound-spam-filter-policy) tidligere i denne artikel.

> [!NOTE]
> Du kan ikke omdøbe en filterpolitik for udgående spam ( **Cmdlet'en Set-HostedOutboundSpamFilterPolicy** har ingen _navneparameter_ ). Når du omdøber en politik for udgående spam på Microsoft 365 Defender-portalen, omdøber du kun _reglen_ for filter for udgående spam.

Hvis du vil ændre en filterpolitik for udgående spam, skal du bruge denne syntaks:

```PowerShell
Set-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/set-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-modify-outbound-spam-filter-rules"></a>Brug PowerShell til at ændre filterregler for udgående spam

Den eneste indstilling, der ikke er tilgængelig, når du ændrer en regel for filter for udgående spam i PowerShell, er parameteren _Enabled_ , der giver dig mulighed for at oprette en deaktiveret regel. Hvis du vil aktivere eller deaktivere eksisterende regler for udgående spamfilter, skal du se næste afsnit.

Ellers er der ingen yderligere indstillinger tilgængelige, når du ændrer en regel for filter for udgående spam i PowerShell. De samme indstillinger er tilgængelige, når du opretter en regel, som beskrevet i [Trin 2: Brug PowerShell til at oprette en regel for udgående spamfilter](#step-2-use-powershell-to-create-an-outbound-spam-filter-rule) tidligere i denne artikel.

Hvis du vil ændre en regel for filter for udgående spam, skal du bruge denne syntaks:

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-HostedOutboundSpamFilterRule](/powershell/module/exchange/set-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-enable-or-disable-outbound-spam-filter-rules"></a>Brug PowerShell til at aktivere eller deaktivere regler for udgående spamfilter

Aktivering eller deaktivering af en regel for filter for udgående spam i PowerShell aktiverer eller deaktiverer hele politikken for udgående spam (reglen for filter for udgående spam og den tildelte filterpolitik for udgående spam). Du kan ikke aktivere eller deaktivere standardpolitikken for udgående spam (den anvendes altid på alle afsendere).

Hvis du vil aktivere eller deaktivere en regel for filter for udgående spam i PowerShell, skal du bruge denne syntaks:

```PowerShell
<Enable-HostedOutboundSpamFilterRule | Disable-HostedOutboundSpamFilterRule> -Identity "<RuleName>"
```

I dette eksempel deaktiveres filterreglen for udgående spam med navnet Marketingafdeling.

```PowerShell
Disable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

I dette eksempel aktiveres samme regel.

```PowerShell
Enable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Enable-HostedOutboundSpamFilterRule](/powershell/module/exchange/enable-hostedoutboundspamfilterrule) og [Disable-HostedOutboundSpamFilterRule](/powershell/module/exchange/disable-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-set-the-priority-of-outbound-spam-filter-rules"></a>Brug PowerShell til at angive prioriteten for filterregler for udgående spam

Den højeste prioritetsværdi, du kan angive for en regel, er 0. Den laveste værdi, du kan angive, afhænger af antallet af regler. Hvis du f.eks. har fem regler, kan du bruge prioritetsværdierne 0 til 4. Hvis du ændrer prioriteten for en eksisterende regel, kan det have en overlappende effekt på andre regler. Hvis du f.eks. har fem brugerdefinerede regler (prioriteter 0 til 4), og du ændrer prioriteten for en regel til 2, ændres den eksisterende regel med prioritet 2 til prioritet 3, og reglen med prioritet 3 ændres til prioritet 4.

Hvis du vil angive prioriteten for en regel for filter for udgående spam i PowerShell, skal du bruge følgende syntaks:

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" -Priority <Number>
```

I dette eksempel angives prioriteten for reglen marketingafdeling til 2. Alle eksisterende regler, der har en prioritet, der er mindre end eller lig med 2, reduceres med 1 (deres prioritetstal øges med 1).

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "Marketing Department" -Priority 2
```

**Noter**:

- Hvis du vil angive prioriteten for en ny regel, når du opretter den, skal du i stedet bruge parameteren _Priority_ på **Cmdlet'en New-HostedOutboundSpamFilterRule** .
- Den udgående standardfilterpolitik for spam har ikke en tilsvarende regel for spamfilter, og den har altid den ikke-redigerbare prioritetsværdi **Laveste**.

### <a name="use-powershell-to-remove-outbound-spam-filter-policies"></a>Brug PowerShell til at fjerne filterpolitikker for udgående spam

Når du bruger PowerShell til at fjerne en filterpolitik for udgående spam, fjernes den tilsvarende regel for filter for udgående spam ikke.

Hvis du vil fjerne en filterpolitik for udgående spam i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>"
```

I dette eksempel fjernes filterpolitikken for udgående spam med navnet Marketingafdeling.

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Remove-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/remove-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-remove-outbound-spam-filter-rules"></a>Brug PowerShell til at fjerne regler for filter for udgående spam

Når du bruger PowerShell til at fjerne en regel for filter for udgående spam, fjernes den tilsvarende filterpolitik for udgående spam ikke.

Hvis du vil fjerne en filterregel for udgående spam i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "<PolicyName>"
```

I dette eksempel fjernes filterreglen for udgående spam med navnet Marketingafdeling.

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Remove-HostedOutboundSpamFilterRule](/powershell/module/exchange/remove-hostedoutboundspamfilterrule).

## <a name="for-more-information"></a>Du kan få flere oplysninger

[Fjern blokerede brugere fra portalen Begrænsede brugere](removing-user-from-restricted-users-portal-after-spam.md)

[Højrisikoleveringspulje for udgående meddelelser](high-risk-delivery-pool-for-outbound-messages.md)

[Ofte stillede spørgsmål om beskyttelse mod spam](anti-spam-protection-faq.yml)

[Rapport over automatisk videresendte meddelelser](mfi-auto-forwarded-messages-report.md)
