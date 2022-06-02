---
title: Administrer meddelelser og filer i karantæne som en administrator
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 065cc2cf-2f3a-47fd-a434-2a20b8f51d0c
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om, hvordan de får vist og administrerer karantænemeddelelser for alle brugere i Exchange Online Protection (EOP). Administratorer i organisationer med Microsoft Defender for Office 365 kan også administrere filer i karantæne i SharePoint Online, OneDrive for Business og Microsoft Teams.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3bd239231cc49684f8b07fb73f33265c9463bad4
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839793"
---
# <a name="manage-quarantined-messages-and-files-as-an-admin-in-eop"></a>Administrer karantænemeddelelser og filer som administrator i EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående EOP-organisationer (Exchange Online Protection) uden Exchange Online postkasser, indeholder karantæne potentielt farlige eller uønskede meddelelser. Du kan få flere oplysninger under [Karantænelagrede mails i EOP](quarantine-email-messages.md).

Administratorer kan få vist, udgive og slette alle typer af karantænemeddelelser for alle brugere. Administratorer kan også rapportere falske positiver til Microsoft.

Som standard er det kun administratorer, der kan administrere meddelelser, der er sat i karantæne som malware, phishing med høj sikkerhed eller som følge af regler for mailflow (også kendt som transportregler). Men administratorer kan bruge _karantænepolitikker_ til at definere, hvad brugerne må gøre for at sætte meddelelser i karantæne, afhængigt af hvorfor meddelelsen blev sat i karantæne (for understøttede funktioner). Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).

Administratorer i organisationer med Microsoft Defender for Office 365 kan også administrere filer, der er sat i karantæne af [Pengeskab Attachments for SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Du får vist og administrerer karantænemeddelelser på Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til Microsoft 365 organisationer med postkasser i Exchange Online; enkeltstående EOP PowerShell til organisationer uden Exchange Online postkasser).

Se denne korte video for at få mere at vide om, hvordan du administrerer karantænemeddelelser som administrator. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGGPF]

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Hvis du vil åbne Microsoft 365 Defender-portalen, skal du gå til <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Karantæne** , skal du bruge <https://security.microsoft.com/quarantine>.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, [skal du se Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du se Forbind til Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser i **Exchange Online**, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil udføre handlinger på karantænemeddelelser for alle brugere, skal du være medlem af rollegrupperne **Organisationsadministration**, **Sikkerhedsadministrator** eller **Karantæneadministrator**<sup>\*</sup> . Hvis du vil sende meddelelser til Microsoft, skal du være medlem af rollegruppen **Sikkerhedsadministrator** .
  - Hvis du vil have skrivebeskyttet adgang til karantænemeddelelser for alle brugere, skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser** .

  Du kan få flere oplysninger [under Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Noter**:

  - Tilføjelse af brugere til den tilsvarende Azure Active Directory rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - Rollegruppen **Vis kun organisationsadministration** i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) giver også skrivebeskyttet adgang til funktionen.
  - <sup>\*</sup>Medlemmer af rollegruppen **Karantæneadministrator** i **Mail & samarbejdsroller** i [Microsoft 365 Defender portalen](permissions-microsoft-365-security-center.md#email--collaboration-roles-in-the-microsoft-365-defender-portal) skal også være medlem af rollegruppen **Hygiejnestyring** i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) at udføre karantæneprocedurer i Exchange Online PowerShell.

- Karantænemeddelelser opbevares i en standardperiode baseret på, hvorfor de blev sat i karantæne. Når opbevaringsperioden udløber, slettes meddelelserne automatisk og kan ikke gendannes. Du kan få flere oplysninger [i Karantænemails i EOP og Defender for Office 365](quarantine-email-messages.md).

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-email-messages"></a>Brug Microsoft 365 Defender-portalen til at administrere mails i karantæne

### <a name="view-quarantined-email"></a>Vis karantænemail

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & karantæne for gennemsyn**  \> af samarbejde.\> Hvis du vil gå direkte til siden **Karantæne** , skal du bruge <https://security.microsoft.com/quarantine>.

2. Kontrollér, at fanen **Mail** er valgt på siden **Karantæne**.

3. Du kan sortere resultaterne ved at klikke på en tilgængelig kolonneoverskrift. Klik på **Tilpas kolonner**  for at ændre de kolonner, der vises. Standardværdierne er markeret med en stjerne (<sup>\*</sup>):

   - **Modtaget tid**<sup>\*</sup>
   - **Emne**<sup>\*</sup>
   - **Afsender**<sup>\*</sup>
   - **Årsag til karantæne**<sup>\*</sup>
   - **Udgivelsesstatus**<sup>\*</sup>
   - **Politiktype**<sup>\*</sup>
   - **Udløber**<sup>\*</sup>
   - **Modtager**
   - **Meddelelses-id**
   - **Politiknavn**
   - **Meddelelsesstørrelse**
   - **Postretning**
   - **Modtagerkode**

   Klik på **Anvend**, når du er færdig.

4. Klik på **Filter** for at filtrere resultaterne. Følgende filtre er tilgængelige i pop op-vinduet **Filtre** , der vises:
   - **Meddelelses-id**: Meddelelsens globalt entydige id.

     Du brugte f.eks [. meddelelsessporing](message-trace-scc.md) til at søge efter en meddelelse, der blev sendt til en bruger i din organisation, og du fastslår, at meddelelsen blev sat i karantæne i stedet for leveret. Sørg for at inkludere den fulde meddelelses-id-værdi, som kan indeholde vinkelparenteser (\<\>). For eksempel: `<79239079-d95a-483a-aacf-e954f592a0f6@XYZPR00BM0200.contoso.com>`.

   - **Afsenderadresse**
   - **Modtageradresse**
   - **Emne**
   - **Modtaget klokkeslæt**: Angiv **starttidspunkt** og **sluttidspunkt** (dato).
   - **Udløber: Filtrer** meddelelser efter, hvornår de udløber fra karantæne:
     - **Dag**
     - **De næste 2 dage**
     - **De næste 7 dage**
     - **Brugerdefineret**: Angiv et **starttidspunkt** og **et sluttidspunkt** (dato).
   - **Modtagerkode**
   - **Karantæneårsag**:
     - **Transportregel** (regel for mailflow)
     - **Bulk**
     - **Spam**
     - **Malware**: Politikker for antimalware i EOP eller Pengeskab politikker for vedhæftede filer i Defender for Office 365. Værdien **for Politiktype** angiver, hvilken funktion der blev brugt.
     - **Phishing**: Spamfilterets dom var **Phishing** eller beskyttelse mod phishing sat meddelelsen i karantæne ([spoof-indstillinger](set-up-anti-phishing-policies.md#spoof-settings) eller [repræsentationsbeskyttelse](konfigureret anti-phishing-politikker.
     - **Phishing med høj genkendelsessikkerhed**
   - **Modtager**: **Alle brugere** eller **kun mig**. Slutbrugere kan kun administrere karantænemeddelelser, der sendes til dem.
   - **Udgivelsesstatus**: En af følgende værdier:
     - **Kræver gennemsyn**
     - **Godkendt**
     - **Nægtet**
     - **Der er anmodet om udgivelse**
     - **Udgivet**
   - **Politiktype**: Filtrer meddelelser efter politiktype:
     - **Politik for antimalware**
     - **politik for vedhæftede filer Pengeskab**
     - **Politik til bekæmpelse af phishing**
     - **Politik mod spam**
     - **Transportregel** (regel for mailflow)

   Klik på **Anvend**, når du er færdig. Klik på ![ikonet Ryd filtre for at rydde filtrene.](../../media/m365-cc-sc-clear-filters-icon.png) **Ryd filtre**.

5. Brug **søgefeltet** og en tilsvarende værdi til at finde bestemte meddelelser. Jokertegn understøttes ikke. Du kan søge efter følgende værdier:
   - Afsendermailadresse
   - Emne. Brug hele meddelelsens emne. Der skelnes ikke mellem store og små bogstaver i søgningen.

   Når du har angivet søgekriterierne, skal du trykke på ENTER for at filtrere resultaterne.

Når du har fundet en bestemt karantænemeddelelse, skal du vælge meddelelsen for at få vist detaljer om den og udføre handlinger på den (f.eks. få vist, udgive, downloade eller slette meddelelsen).

#### <a name="view-quarantined-message-details"></a>Vis oplysninger om karantænemeddelelse

Når du vælger karantænemeddelelse på listen, er følgende oplysninger tilgængelige i det detaljerede pop op-vindue, der vises.

:::image type="content" source="../../media/quarantine-message-details-flyout.png" alt-text="Pop op-vinduet med detaljer for en karantænemeddelelse" lightbox="../../media/quarantine-message-details-flyout.png":::

- **Meddelelses-id**: Meddelelsens globalt entydige id. Tilgængelig i headerfeltet **Meddelelses-id** i brevhovedet.
- **Afsenderadresse**
- **Modtaget**: Den dato/det klokkeslæt, hvor meddelelsen blev modtaget.
- **Emne**
- **Karantæneårsag**: Viser, om en meddelelse er blevet identificeret som **spam**, **masse**, **phish**, matchede en regel for mailflow (**transportregel**) eller blev identificeret som indeholdende **malware**.
- **Politiktype**
- **Politiknavn**
- **Antal modtagere**
- **Modtagere**: Hvis meddelelsen indeholder flere modtagere, skal du klikke på **Vis meddelelse** eller **Vis brevhoved** for at se den komplette liste over modtagere.
- **Modtagerkode**: Du kan få flere oplysninger [under Brugerkoder i Microsoft Defender for Office 365](user-tags.md).
- **Udløber**: Den dato/det klokkeslæt, hvor meddelelsen automatisk slettes og slettes permanent fra karantæne.
- **Udgivet til**: Alle de mailadresser (hvis der er nogen), som meddelelsen er blevet frigivet til.
- **Endnu ikke frigivet til**: Alle mailadresser (hvis nogen), som meddelelsen endnu ikke er frigivet til.

Hvis du vil udføre en handling på meddelelsen, skal du se næste afsnit.

> [!NOTE]
> Hvis du vil forblive i pop op-vinduet med detaljer, men ændre den karantænemeddelelse, du kigger på, skal du bruge pil op og ned øverst i pop op-vinduet.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-up-down-arrows.png" alt-text="Pil op og ned i detaljevinduet i en karantænemeddelelse" lightbox="../../media/quarantine-message-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-email"></a>Udfør en handling på karantænemail

Når du har valgt en karantænemeddelelse på listen, er følgende handlinger tilgængelige i pop op-vinduet med detaljer:

:::image type="content" source="../../media/quarantine-message-details-flyout-actions.png" alt-text="De tilgængelige handlinger i pop op-vinduet med detaljer i en karantænemeddelelse" lightbox="../../media/quarantine-message-details-flyout-actions.png":::

- ![Ikonet Udgivelsesmail.](../../media/m365-cc-sc-check-mark-icon.png) **Udgivelsesmail**<sup>\*</sup>: Konfigurer følgende indstillinger i den pop op-rude, der vises:
  - **Føj afsender til organisationens liste over tilladte**: Vælg denne indstilling for at forhindre, at meddelelser fra afsenderen sættes i karantæne.
  - Vælg en af følgende indstillinger:
    - **Udgiv til alle modtagere**
    - **Udgiv til bestemte modtagere**: Vælg modtagerne i feltet **Modtagere** , der vises
  - **Send en kopi af denne meddelelse til andre modtagere**: Vælg denne indstilling, og angiv modtagermailadresserne i feltet **Modtagere** , der vises.

    > [!NOTE]
    > Hvis du vil sende en kopi af meddelelsen til andre modtagere, skal du også frigive meddelelsen mindst én af de oprindelige modtagere (vælg **Udgiv til alle modtagere** eller **Udgiv til bestemte modtagere**).

  - **Send meddelelsen til Microsoft for at forbedre registreringen (falsk positiv)**: Denne indstilling er valgt som standard, og rapporterer den fejlagtigt i karantæne til Microsoft som falsk positiv. Hvis meddelelsen blev sat i karantæne som spam, masse, phishing eller indeholder malware, rapporteres meddelelsen også til Microsoft Spam Analysis Team. Afhængigt af resultaterne af deres analyse kan reglerne for spamfilter for hele tjenesten justeres for at tillade, at meddelelsen kan sendes.

  - **Tillad meddelelser som denne**: Denne indstilling er som standard slået fra (![Slå til/fra).](../../media/scc-toggle-off.png) Slå den til (![Slå](../../media/scc-toggle-on.png) til) for midlertidigt at forhindre, at meddelelser med lignende URL-adresser, vedhæftede filer og andre egenskaber sættes i karantæne. Når du slår denne indstilling til, er følgende indstillinger tilgængelige:
    - **Fjern efter**: Vælg, hvor længe meddelelser som denne skal tillades. Vælg **1 dag** til **30 dage**. Standarden er 30.
    - **Valgfri note**: Angiv en nyttig beskrivelse af tillad.

  Når du er færdig, skal du klikke på **Frigiv meddelelse**.

  Noter om udgivelse af meddelelser:

  - Du kan ikke frigive en meddelelse til den samme modtager mere end én gang.
  - Det er kun modtagere, der ikke har modtaget meddelelsen, der vises på listen over potentielle modtagere.
  - Det er kun medlemmer af rollegruppen **Sikkerhedsadministratorer** , der kan se og bruge **Send meddelelsen til Microsoft for at forbedre registreringen (falsk positiv)** og **Tillad meddelelser som disse** indstillinger.

- ![Ikonet Del mail.](../../media/m365-cc-sc-share-email-icon.png) **Del mail**: I det pop op-vindue, der vises, skal du tilføje en eller flere modtagere for at modtage en kopi af meddelelsen. Når du er færdig, skal du klikke på **Del**.

Følgende handlinger er tilgængelige, når du har klikket på ![ikonet Flere handlinger.](../../media/m365-cc-sc-more-actions-icon.png) **Flere handlinger**:

- ![Vis ikonet for brevhoveder.](../../media/m365-cc-sc-view-message-headers-icon.png) **Vis brevhoveder**: Vælg dette link for at få vist teksten i brevhovedet. Pop **op-vinduet Meddelelsesheader** vises med følgende links:
  - **Kopiér brevhoved**: Klik på dette link for at kopiere brevhovedet (alle headerfelter) til Udklipsholder.
  - **Microsoft Message Header Analyzer**: Hvis du vil analysere overskriftsfelterne og værdierne i dybden, skal du klikke på dette link for at gå til Analyse af meddelelsesoverskrift. Indsæt brevhovedet i sektionen **Indsæt det brevhoved, du vil analysere** (CTRL+V, eller højreklik, og vælg **Sæt ind**), og klik derefter på **Analysér brevhoveder**.

- ![Vis meddelelsesikon.](../../media/m365-cc-sc-preview-message-icon.png) **Vis meddelelse**: Vælg en af følgende faner i det pop op-vindue, der vises:
  - **Kilde**: Viser HTML-versionen af meddelelsens brødtekst med alle links deaktiveret.
  - **Almindelig tekst**: Viser meddelelsens brødtekst som almindelig tekst.

- ![Slet fra karantæneikonet.](../../media/m365-cc-sc-delete-icon.png) **Slet fra karantæne**: Når du har klikket på **Ja** i advarslen, slettes meddelelsen straks uden at blive sendt til de oprindelige modtagere.

- ![Ikonet Download mail.](../../media/m365-cc-sc-download-icon.png) **Download mail**: I det pop op-vindue, der vises, skal du vælge **Jeg forstår risikoen ved at downloade denne meddelelse** og derefter klikke på **Download** for at gemme en lokal kopi af meddelelsen i .eml-format.

- ![Ikonet Bloker afsender.](../../media/m365-cc-sc-block-sender-icon.png) **Bloker afsender**: Føj afsenderen til listen Over blokerede afsendere i **postkassen** . Du kan få flere oplysninger under [Bloker en mailsender](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

- ![Ikonet Send kun.](../../media/m365-cc-sc-create-icon.png) **Send kun**: Rapporterer meddelelsen til Microsoft til analyse. Vælg følgende indstillinger i det pop op-vindue, der vises:
  - **Vælg afsendelsestypen**: **Mail** (standard), **URL-adresse** eller **Fil**.
  - **Tilføj netværksmeddelelses-id'et, eller upload mailfilen**: Vælg en af følgende indstillinger:
    - **Tilføj mailnetværkets meddelelses-id** (standard med den tilsvarende værdi i feltet)
    - **Upload mailfilen (.msg eller eml):** Klik på **Gennemse filer** for at finde og vælge den .msg- eller .eml-meddelelsesfil, der skal sendes.
  - **Vælg en modtager, der havde et problem**: Vælg en (foretrukket) eller flere oprindelige modtagere af meddelelsen for at analysere de politikker, der er anvendt på dem.
  - **Vælg en årsag til afsendelse til Microsoft**: Vælg en af følgende indstillinger:
    - **Burde ikke være blevet blokeret (falsk positiv)** (standard): Følgende indstillinger er tilgængelige:
      - **Tillad meddelelser som denne**: Denne indstilling er som standard slået fra (![Slå til/fra).](../../media/scc-toggle-off.png) Slå den til (![Slå](../../media/scc-toggle-on.png) til) for midlertidigt at forhindre, at meddelelser med lignende URL-adresser, vedhæftede filer og andre egenskaber sættes i karantæne. Når du slår denne indstilling til, er følgende indstillinger tilgængelige:
        - **Fjern efter**: Vælg, hvor længe meddelelser som denne skal tillades. Vælg **1 dag** til **30 dage**. Standarden er 30.
        - **Valgfri note**: Angiv en nyttig beskrivelse af tillad.
    - **Burde være blevet blokeret (falsk negativ)**.

  Klik på **Send**, når du er færdig.

<sup>\*</sup>Denne indstilling er ikke tilgængelig for meddelelser, der allerede er udgivet (statusværdien **Frigives**).

Hvis du ikke frigiver eller fjerner meddelelsen, slettes den, når standardopbevaringsperioden for karantæne udløber (som vist i kolonnen **Udløber** ).

> [!NOTE]
> På en mobilenhed er beskrivelsesteksten ikke tilgængelig på handlingsikonerne.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-mobile-actions.png" alt-text="Detaljerne for en karantænemeddelelse med tilgængelige handlinger fremhævet" lightbox="../../media/quarantine-message-details-flyout-mobile-actions.png":::
>
> Ikonerne i rækkefølge og deres tilsvarende beskrivelser opsummeres i følgende tabel:
>
> |Ikon|Beskrivelse|
> |---:|---|
> |![Ikonet Udgivelsesmail.](../../media/m365-cc-sc-check-mark-icon.png)|**Frigiv mail**|
> |![Ikonet Del mail.](../../media/m365-cc-sc-share-email-icon.png)|**Del mail**|
> |![Vis ikonet for brevhoveder.](../../media/m365-cc-sc-view-message-headers-icon.png)|**Vis brevhoveder**|
> |![Vis meddelelsesikon.](../../media/m365-cc-sc-preview-message-icon.png)|**Vis meddelelse**|
> |![Slet fra karantæneikonet.](../../media/m365-cc-sc-delete-icon.png)|**Slet fra karantæne**|
> |![Ikonet Download mail.](../../media/m365-cc-sc-download-icon.png)|**Download mail**|
> |![Ikonet Bloker afsender.](../../media/m365-cc-sc-block-sender-icon.png)|**Afsender af blok**|
> |![Ikonet Send kun.](../../media/m365-cc-sc-create-icon.png)|**Send kun**|

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Udfør en handling på flere mails i karantæne

Når du vælger flere karantænemeddelelser på listen (op til 100) ved at klikke i det tomme område til venstre for den første kolonne, vises rullelisten **Massehandlinger** , hvor du kan udføre følgende handlinger:

:::image type="content" source="../../media/quarantine-message-bulk-actions.png" alt-text="Rullelisten Massehandlinger for meddelelser i karantæne" lightbox="../../media/quarantine-message-bulk-actions.png":::

- ![Ikonet Udgivelsesmail.](../../media/m365-cc-sc-check-mark-icon.png) **Udgivelsesmeddelelser**: Udgiver meddelelser til alle modtagere. I det pop op-vindue, der vises, kan du vælge følgende indstillinger, som er de samme, som når du udgiver en enkelt meddelelse:
  - **Føj afsender til organisationens liste over tilladte**
  - **Send en kopi af denne meddelelse til andre modtagere**
  - **Send meddelelsen til Microsoft for at forbedre registreringen (falsk positiv)**
  - **Tillad meddelelser som denne**:
    - **Fjern efter**: **1 dag** til **30 dage**
    - **Valgfri note**

  Når du er færdig, skal du klikke på **Frigiv meddelelse**.

  > [!NOTE]
  > Overvej følgende scenarie: john@gmail.com sender en meddelelse for at faith@contoso.com og john@subsidiary.contoso.com. Gmail bifurcates denne meddelelse i to kopier, der begge distribueres til karantæne som phishing i Microsoft. En administrator udgiver begge disse meddelelser for at admin@contoso.com. Den første udgivne meddelelse, der når administratorpostkassen, leveres. Den anden udgivne meddelelse identificeres som duplikeret levering og springes over. Meddelelsen identificeres som dubletter, hvis de har samme meddelelses-id og modtaget tid.

- ![Slet fra karantæneikonet.](../../media/m365-cc-sc-delete-icon.png) **Slet meddelelser**: Når du har klikket på **Ja** i advarslen, fjernes meddelelserne straks fra karantænen uden at blive sendt til de oprindelige modtagere.
- ![Ikonet Download mail.](../../media/m365-cc-sc-download-icon.png) **Download meddelelser**
- ![Ikonet Send kun.](../../media/m365-cc-sc-create-icon.png) **Send kun**

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365"></a>Brug Microsoft 365 Defender-portalen til at administrere filer i karantæne i Defender for Office 365

> [!NOTE]
> Procedurerne for karantænefiler i dette afsnit er kun tilgængelige for Microsoft Defender for Office 365 Plan 1- eller Plan 2-abonnenter.

I organisationer med Defender for Office 365 kan administratorer administrere filer, der er sat i karantæne af Pengeskab Attachments for SharePoint, OneDrive og Microsoft Teams. Hvis du vil aktivere beskyttelse af disse filer, skal du se [Slå Pengeskab vedhæftede filer til for SharePoint, OneDrive og Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

### <a name="view-quarantined-files"></a>Vis filer, der er sat i karantæne

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & karantæne for gennemsyn**  \> af samarbejde.\> Hvis du vil gå direkte til siden **Karantæne** , skal du bruge <https://security.microsoft.com/quarantine>.

2. På siden **Karantæne** skal du vælge fanen **Filer** (**Mail** er standardfanen).

3. Du kan sortere resultaterne ved at klikke på en tilgængelig kolonneoverskrift. Klik på **Tilpas kolonner** for at ændre de kolonner, der vises. Standardkolonnerne er markeret med en stjerne (<sup>\*</sup>):
   - **Bruger**<sup>\*</sup>
   - **Placering**<sup>\*</sup>
   - **Navn på vedhæftet fil**<sup>\*</sup>
   - **URL-adresse til fil**<sup>\*</sup>
   - **Filstørrelse**
   - **Udgivelsesstatus**<sup>\*</sup>
   - **Udløber**<sup>\*</sup>
   - **Registreret af**
   - **Ændret efter klokkeslæt**

   Når du er færdig, skal du klikke på **Anvend** eller **Annuller**.

4. Klik på **Filter** for at filtrere resultaterne. Følgende filtre er tilgængelige i pop op-vinduet **Filtre** , der vises:
   - **Modtaget klokkeslæt**: **Starttidspunkt** og **Sluttidspunkt** (dato).
   - **Udløber**: **Starttidspunkt** og **Sluttidspunkt** (dato).
   - **Karantæneårsag**: Den eneste tilgængelige værdi er **Malware**.
   - **Politiktype**

   Når du er færdig, skal du klikke på **Anvend** eller **Annuller**.

Når du har fundet en bestemt karantænefil, skal du vælge filen for at få vist detaljer om den og udføre handlinger på den (f.eks. få vist, udgive, downloade eller slette filen).

#### <a name="view-quarantined-file-details"></a>Vis oplysninger om karantænefil

Når du vælger en karantænefil på listen, er følgende oplysninger tilgængelige i det detaljerede pop op-vindue, der åbnes:

:::image type="content" source="../../media/quarantine-file-details-flyout.png" alt-text="Pop op-vinduet med detaljer for en karantænefil" lightbox="../../media/quarantine-file-details-flyout.png":::

- **Filnavn**
- **Fil-URL-adresse**: URL-adresse, der definerer filens placering (f.eks. i SharePoint Online).
- **Skadeligt indhold registreret på** Den dato/det klokkeslæt, hvor filen blev sat i karantæne.
- **Udløber**: Den dato, hvor filen slettes fra karantæne.
- **Registreret af**
- **Udgivet?**
- **Navn på skadelig software**
- **Dokument-id**: Et entydigt id for dokumentet.
- **Filstørrelse**: I kilobyte (KB).
- **Organisation** Din organisations entydige id.
- **Senest ændret**
- **Ændret af**: Den bruger, der senest ændrede filen.
- **Sikker værdi for hashalgoritme 256-bit (SHA-256**): Du kan bruge denne hashværdi til at identificere filen i andre omdømmebutikker eller andre steder i dit miljø.

Hvis du vil udføre en handling på filen, skal du se næste afsnit.

> [!NOTE]
> Hvis du vil blive i pop op-vinduet med detaljer, men ændre den karantænefil, du kigger på, skal du bruge pil op og ned øverst i pop op-vinduet.
>
> :::image type="content" source="../../media/quarantine-file-details-flyout-up-down-arrows.png" alt-text="Pil op og ned i detaljevinduet for karantænefiler" lightbox="../../media/quarantine-file-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-files"></a>Udfør en handling på karantænefiler

Når du har valgt en karantænefil på listen, er følgende handlinger tilgængelige i pop op-vinduet med detaljer:

:::image type="content" source="../../media/quarantine-file-details-flyout-actions.png" alt-text="Handlingerne i pop op-vinduet med detaljer for en karantænefil" lightbox="../../media/quarantine-file-details-flyout-actions.png":::

- ![Ikonet Frigiv fil.](../../media/m365-cc-sc-check-mark-icon.png) **Udgivelsesfil**<sup>\*</sup>: I den pop op-rude, der vises, skal du slå **Rapportfiler til Microsoft til analyse** og derefter klikke på **Udgivelse**.
- ![Ikonet Frigiv fil.](../../media/m365-cc-sc-check-mark-icon.png)
- ![Ikonet Download fil.](../../media/m365-cc-sc-download-icon.png) **Downloadfil**: I det pop op-vindue, der vises, skal du vælge **Jeg forstår risikoen ved at downloade denne fil** og derefter klikke på **Download** for at gemme en lokal kopi af filen.
- ![Slet fra karantæneikonet.](../../media/m365-cc-sc-delete-icon.png) **Slet fra karantæne**: Når du har klikket på **Ja** i advarslen, slettes filen straks.
- ![Ikonet Bloker afsender.](../../media/m365-cc-sc-block-sender-icon.png) **Bloker afsender**: Føj afsenderen til listen Over blokerede afsendere i **postkassen** . Du kan få flere oplysninger under [Bloker en mailsender](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

<sup>\*</sup>Denne indstilling er ikke tilgængelig for filer, der allerede er udgivet (**statusværdien Frigives**).

Hvis du ikke frigiver eller fjerner filen, slettes den, når standardopbevaringsperioden for karantæne udløber (som vist i kolonnen **Udløber** ).

#### <a name="take-action-on-multiple-quarantined-files"></a>Udfør en handling på flere filer, der er sat i karantæne

Når du vælger flere filer i karantæne på listen (op til 100) ved at klikke i det tomme område til venstre for kolonnen **Emne** , vises rullelisten **Massehandlinger** , hvor du kan udføre følgende handlinger:

:::image type="content" source="../../media/quarantine-file-bulk-actions.png" alt-text="Rullelisten Massehandlinger for filer i karantæne" lightbox="../../media/quarantine-file-bulk-actions.png":::

- ![Ikonet Frigiv fil.](../../media/m365-cc-sc-check-mark-icon.png) **Udgivelsesfil**: I den pop op-rude, der vises, skal du slå **Rapportfiler til Microsoft til analyse** og derefter klikke på **Udgivelse**.
- ![Slet fra karantæneikonet.](../../media/m365-cc-sc-delete-icon.png) **Slet fra karantæne**: Når du har klikket på **Ja** i advarslen, slettes filen straks.
- ![Ikonet Download fil.](../../media/m365-cc-sc-download-icon.png) **Downloadfil**: I det pop op-vindue, der vises, skal du vælge **Jeg forstår risikoen ved at downloade denne fil** og derefter klikke på **Download** for at gemme en lokal kopi af filen.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-view-and-manage-quarantined-messages-and-files"></a>Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at få vist og administrere karantænemeddelelser og filer

De cmdlet'er, du bruger til at få vist og administrere meddelelser og filer i karantæne, er beskrevet på følgende liste:

- [Slet karantænemeddelelse](/powershell/module/exchange/delete-quarantinemessage)
- [Eksport-KarantæneMeddelelse](/powershell/module/exchange/export-quarantinemessage)
- [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)
- [Preview-QuarantineMessage](/powershell/module/exchange/preview-quarantinemessage): Bemærk, at denne cmdlet kun er til meddelelser og ikke til filer fra Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams.
- [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)

## <a name="for-more-information"></a>Du kan få flere oplysninger

[Ofte stillede spørgsmål om karantænemeddelelser](quarantine-faq.yml)
