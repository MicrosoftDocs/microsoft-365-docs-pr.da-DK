---
title: Administrer meddelelser og filer, der er sat i karantæne, som administrator
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
description: Administratorer kan lære, hvordan du får vist og administrerer meddelelser, der er sat i karantæne, for alle brugere Exchange Online Protection (EOP). Administratorer i organisationer med Microsoft Defender for Office 365 kan også administrere filer, der er sat i karantæne, i SharePoint Online, OneDrive for Business og Microsoft Teams.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 449886f6272c81f9947fd3e7ea869e565326578f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469641"
---
# <a name="manage-quarantined-messages-and-files-as-an-admin-in-eop"></a>Administrer meddelelser og filer, der er sat i karantæne, som administrator i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 med postkasser i Exchange Online eller enkeltstående Exchange Online Protection (EOP)-organisationer uden Exchange Online-postkasser, sætter karantæne i potentielt farlig eller uønskede meddelelser. Du kan få mere at vide [under Meddelelser, der er sat i karantæne i EOP](quarantine-email-messages.md).

Administratorer kan få vist, frigive og slette alle typer af meddelelser, der er sat i karantæne, for alle brugere. Administratorer kan også rapportere falske positive til Microsoft.

Som standard er det kun administratorer, der kan administrere meddelelser, der var i karantæne som malware, phishing med høj tillid eller som et resultat af regler for mailflow (også kaldet transportregler). Men administratorer kan bruge karantænepolitikker til at definere, hvad brugerne har tilladelse til at gøre for meddelelser, der er sat i karantæne, baseret på, hvorfor meddelelsen var i karantæne (for understøttede funktioner). Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).

Administratorer i organisationer med Microsoft Defender for Office 365 kan også administrere filer, der er blevet sat i karantæne af Pengeskab Vedhæftede filer [for SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Du kan få vist og administrere meddelelser, der er sat i karantæne, i Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til Microsoft 365-organisationer med postkasser i Exchange Online; enkeltstående EOP PowerShell til organisationer uden Exchange Online postkasser).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Hvis du vil åbne Microsoft 365 Defender, skal du gå til <https://security.microsoft.com>. Hvis du vil gå direkte til **siden Karantæne** , skal du bruge <https://security.microsoft.com/quarantine>.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du Forbind Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser **i Exchange Online,** før du kan udføre procedurerne i denne artikel:
  - Hvis du vil handle på meddelelser, der er sat i karantæne for alle brugere, skal du være medlem af rollegrupperne Organisationsadministration **,** **Sikkerhedsadministrator eller Karantæneadministrator**<sup>\*</sup>. Hvis du vil sende meddelelser til Microsoft, skal du være medlem af **rollegruppen Sikkerhedsadministrator** .
  - For skrivebeskyttet adgang til meddelelser, der er sat i karantæne for alle brugere, skal du være medlem af rollegrupperne **Global læser** **eller** Sikkerhedslæser.

  Du kan finde flere [oplysninger i Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Bemærkninger**:

  - Hvis du føjer brugere til den Azure Active Directory rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser og tilladelser til andre  funktioner Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - **Rollegruppen Skrivebeskyttet** organisationsadministration i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) også skrivebeskyttet adgang til funktionen.
  - <sup>\*</sup>Medlemmer af rollegruppen Karantæneadministrator i mail **&-samarbejdsroller** i [Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md#email--collaboration-roles-in-the-microsoft-365-defender-portal) skal også være medlemmer af rollegruppen administration af medarbejdere i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) for at udføre karantæneprocedurer i Exchange Online PowerShell. 

- Meddelelser, der er sat i karantæne, bevares i en standardperiode, baseret på, hvorfor de var i karantæne. Når en opbevaringsperiode udløber, slettes meddelelserne automatisk og kan ikke gendannes. Få mere at vide under [Meddelelser, der er sat i karantæne i EOP og Defender for Office 365](quarantine-email-messages.md).

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-email-messages"></a>Brug portalen Microsoft 365 Defender til at administrere meddelelser, der er sat i karantæne

### <a name="view-quarantined-email"></a>Få vist mails, der er sat i karantæne

1. I portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **Mail & gennemsynskarantæne** \>  \>. Hvis du vil gå direkte til **siden Karantæne** , skal du bruge <https://security.microsoft.com/quarantine>.

2. Kontrollér **,** at fanen Mail er markeret **på** siden Karantæne.

3. Du kan sortere resultaterne ved at klikke på en tilgængelig kolonneoverskrift. Klik **på Tilpas kolonner**  for at ændre de kolonner, der vises. Standardværdierne er markeret med en stjerne (<sup>\*</sup>):

   - **Tidspunkt for modtagelse**<sup>\*</sup>
   - **Emne**<sup>\*</sup>
   - **Afsender**<sup>\*</sup>
   - **Årsagen til karantæne**<sup>\*</sup>
   - **Udgivelsesstatus**<sup>\*</sup>
   - **Politiktype**<sup>\*</sup>
   - **Udløber**<sup>\*</sup>
   - **Modtager**
   - **Meddelelses-id**
   - **Politiknavn**
   - **Meddelelsesstørrelse**
   - **Mailretning**
   - **Modtagermærke**

   Klik på Anvend, når du er **færdig**.

4. Hvis du vil filtrere resultaterne, skal du klikke **på Filtrer**. Følgende filtre er tilgængelige i pop **op-vinduesruden** Filtre, der vises:
   - **Meddelelses-id**: GUID (Globally Unique Identifier) i meddelelsen.

     Du brugte f.eks[](message-trace-scc.md). meddelelsessporing til at søge efter en meddelelse, der blev sendt til en bruger i organisationen, og du afgør, at meddelelsen blev sat i karantæne i stedet for leveret. Sørg for at medtage værdien for hele meddelelses-id'et, som kan indeholde vinkelparenteser (\<\>). For eksempel: `<79239079-d95a-483a-aacf-e954f592a0f6@XYZPR00BM0200.contoso.com>`.

   - **Afsenderadresse**
   - **Modtageradresse**
   - **Emne**
   - **Tidspunkt modtaget**: Angiv et **start- og** **sluttidspunktet** (dato).
   - **Udløber:** Filtrerer meddelelser efter, hvornår de udløber fra karantæne:
     - **I dag**
     - **Næste 2 dage**
     - **Næste 7 dage**
     - **Brugerdefineret**: Angiv **et Start-klokkeslæt** **og Et Slut-klokkeslæt** (dato).
   - **Modtagermærke**
   - **Årsagen til karantæne**:
     - **Transportregel** (regel for mailflow)
     - **Masse**
     - **Spam**
     - **Malware**: Antimalwarepolitikker i EOP eller Pengeskab politikker for vedhæftede filer Defender for Office 365. Værdien **Politiktype** angiver, hvilken funktion der blev brugt.
     - **Phishing**: Spamfilteret var **phishing** - eller antiphishingbeskyttelse i karantæne for meddelelsen ([spoof-indstillinger](set-up-anti-phishing-policies.md#spoof-settings) eller [beskyttelse mod efterligning](set-up-anti-phishing-policies.
     - **Phishing med høj tillid**
   - **Modtager**: **Alle brugere** eller **Kun mig**. Slutbrugere kan kun administrere meddelelser, der er sat i karantæne, som sendes til dem.
   - **Udgivelsesstatus**: En af følgende værdier:
     - **Gennemsyn af behov**
     - **Godkendt**
     - **Afvist**
     - **Version anmodet om**
     - **Udgivet**
   - **Politiktype**: Filtrer meddelelser efter politiktype:
     - **Antimalwarepolitik**
     - **Pengeskab politik for vedhæftede filer**
     - **Antiphishing-politik**
     - **Antispampolitik**
     - **Transportregel** (regel for mailflow)

   Klik på Anvend, når du er **færdig**. Klik på ikonet Ryd filtre for at ![rydde filtrene.](../../media/m365-cc-sc-clear-filters-icon.png) **Ryd filtre**.

5. Brug feltet **Søg** og en tilsvarende værdi til at finde bestemte meddelelser. Jokertegn understøttes ikke. Du kan søge efter følgende værdier:
   - Afsendermailadresse
   - Emne. Brug hele meddelelsens emne. Der er ikke store og små bogstaver i søgningen.

   Når du har angivet søgekriterierne, skal du trykke på Enter for at filtrere resultaterne.

Når du har fundet en bestemt meddelelse, der er sat i karantæne, skal du markere meddelelsen for at få vist oplysninger om den og for at handle på den (f.eks. få vist, slippe, hente eller slette meddelelsen).

#### <a name="view-quarantined-message-details"></a>Få vist oplysninger om meddelelser i karantæne

Når du markerer en meddelelse, der er sat i karantæne, på listen, kan du finde følgende oplysninger i pop op-dialogboksen med oplysninger, der vises.

:::image type="content" source="../../media/quarantine-message-details-flyout.png" alt-text="Pop op-meddelelsen med oplysninger om en meddelelse, der er sat i karantæne" lightbox="../../media/quarantine-message-details-flyout.png":::

- **Meddelelses-id**: GUID (Globally Unique Identifier) for meddelelsen. Tilgængeligt i **brevhovedfeltet Meddelelses-id** i brevhovedet.
- **Afsenderadresse**
- **Modtaget**: Dato/klokkeslæt for modtagelse af meddelelsen.
- **Emne**
- **Årsag til karantæne**: Viser, hvis en meddelelse er blevet identificeret som **Spam**, **Masse**, **Phish**, matchet en regel for mailflow (**transportregel**) eller er blevet identificeret som **indeholdende Malware**.
- **Politiktype**
- **Politiknavn**
- **Antal modtagere**
- **Modtagere:** Hvis meddelelsen indeholder flere modtagere, skal du klikke på Vis meddelelse eller  Vis brevhoved  for at få vist hele listen over modtagere.
- **Modtagermærke**: Få mere at vide under [Brugermærker i Microsoft Defender for Office 365](user-tags.md).
- **Udløber**: Den dato/det klokkeslæt, hvor meddelelsen automatisk og permanent slettes fra karantæne.
- **Udgivet** til: Alle mailadresser (hvis nogen), som meddelelsen er blevet frigivet til.
- **Endnu ikke frigivet til**: Alle mailadresser (hvis nogen), som meddelelsen endnu ikke er blevet frigivet til.

Hvis du vil handle på meddelelsen, skal du se næste afsnit.

> [!NOTE]
> Hvis du vil forblive i pop op-mailen med oplysninger, men ændre den meddelelse, du kigger på i karantæne, skal du bruge pil op og pil ned øverst i pop-op-meddelelsen.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-up-down-arrows.png" alt-text="Pil op og pil ned i pop op-siden med oplysninger om en meddelelse, der er sat i karantæne" lightbox="../../media/quarantine-message-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-email"></a>Handle på en mail, der er sat i karantæne

Når du har valgt en meddelelse, der er sat i karantæne, på listen, kan du vælge følgende handlinger i pop op-menuen med oplysninger:

:::image type="content" source="../../media/quarantine-message-details-flyout-actions.png" alt-text="Tilgængelige handlinger i pop op-menuen med oplysninger om en meddelelse, der er sat i karantæne" lightbox="../../media/quarantine-message-details-flyout-actions.png":::

- ![Ikonet Frigiv mail.](../../media/m365-cc-sc-check-mark-icon.png) **Frigiv mail**<sup>\*</sup>: I pop op-ruden, der vises, skal du konfigurere følgende indstillinger:
  - **Føj afsender til organisationens tilladelsesliste**: Markér denne indstilling for at forhindre meddelelser fra afsenderen i at blive sat i karantæne.
  - Vælg en af følgende indstillinger:
    - **Frigiv til alle modtagere**
    - **Udgivelse til bestemte modtagere**: Markér modtagerne i feltet **Modtagere** , der vises
  - **Send en kopi af meddelelsen til andre** modtagere: Markér denne indstilling, og angiv **modtagerens** mailadresser i feltet Modtagere, der vises.

    > [!NOTE]
    > Hvis du vil sende en kopi af meddelelsen til andre modtagere, skal du også frigive meddelelsen mindst én af de oprindelige modtagere (vælg Frigiv til  alle modtagere eller Frigiv til bestemte **modtagere**).

  - **Send meddelelsen til Microsoft** for at forbedre registrering (falsk positiv): Denne indstilling er valgt som standard og rapporterer en meddelelse, der er i karantæne, til Microsoft som en falsk positiv. Hvis meddelelsen var i karantæne som spam, massemail, phishing eller indeholdende malware, rapporteres meddelelsen også til Microsoft Spam Analysis Team. Afhængigt af resultaterne af deres analyse kan reglerne for spamfilteret for hele tjenesten justeres, så meddelelsen bliver tilladt at komme igennem.

  - **Tillad meddelelser som denne**: Denne indstilling er som standard slået fra (![slå til/fra).](../../media/scc-toggle-off.png) Slå den til (slå![ til](../../media/scc-toggle-on.png)) for midlertidigt at forhindre meddelelser med lignende URL-adresser, vedhæftede filer og andre egenskaber i at blive sat i karantæne. Når du slår denne indstilling til, er følgende tilgængelige:
    - **Fjern efter**: Vælg, hvor længe du vil tillade meddelelser som denne. Vælg **1 dag** til **30 dage**. Standardværdien er 30.
    - **Valgfri note**: Angiv en nyttig beskrivelse af tillad.

  Klik på Slip meddelelse, når du **er færdig**.

  Noter om frigivelse af meddelelser:

  - Du kan ikke slippe en meddelelse til den samme modtager mere end én gang.
  - Kun modtagere, der ikke har modtaget meddelelsen, vises på listen over potentielle modtagere.
  - Kun medlemmer af **rollegruppen Sikkerhedsadministratorer** kan se og bruge meddelelsen Send meddelelsen til Microsoft til at forbedre registrering **(falsk positiv)** og Tillad meddelelser **som denne** indstilling. 

- ![Ikonet Del mail.](../../media/m365-cc-sc-share-email-icon.png) **Del mail**: Tilføj en eller flere modtagere for at modtage en kopi af meddelelsen i det pop op-vindue, der vises. Klik på Del, når du er **færdig**.

Følgende handlinger er tilgængelige, når du klikker på ![ikonet Flere handlinger.](../../media/m365-cc-sc-more-actions-icon.png) **Flere handlinger**:

- ![Ikonet Vis brevhoveder.](../../media/m365-cc-sc-view-message-headers-icon.png) **Få vist brevhoveder:** Vælg dette link for at få vist teksten i brevhovedet. Pop **op-mailens** brevhoved vises med følgende links:
  - **Kopiér brevhoved**: Klik på dette link for at kopiere brevhovedet (alle brevhovedfelter) til din udklipsholder.
  - **Microsoft Analyse af brevhoved**: Hvis du vil analysere brevhovedfelterne og værdierne i dybden, skal du klikke på dette link for at gå til Analyse af brevhoved. Indsæt brevhovedet i indsæt brevhovedet Indsæt det brevhoved, du vil analysere (Ctrl+V eller højreklik, og vælg Sæt **ind), og** klik derefter  på **Analysér brevhoveder**.

- ![Ikonet for eksempel på meddelelse.](../../media/m365-cc-sc-preview-message-icon.png) **Eksempelmeddelelse**: I pop op-menuen, der vises, skal du vælge en af følgende faner:
  - **Kilde**: Viser HTML-versionen af brødteksten i meddelelsen, hvor alle links er deaktiveret.
  - **Almindelig tekst**: Viser meddelelsesteksten i almindelig tekst.

- ![Ikonet Slet fra karantæne.](../../media/m365-cc-sc-delete-icon.png) **Slet fra karantæne**: Når du har **klikket** på Ja i den advarsel, der vises, slettes meddelelsen straks, uden at den sendes til de oprindelige modtagere.

- ![Ikonet Download mail.](../../media/m365-cc-sc-download-icon.png) **Download mail**: I pop op-menuen, der vises, skal du vælge Jeg forstår risikoen ved at hente denne **meddelelse og derefter** klikke på **Download** for at gemme en lokal kopi af meddelelsen i .eml-format.

- ![Ikonet Bloker afsender.](../../media/m365-cc-sc-block-sender-icon.png) **Bloker** afsender: Føj afsenderen til listen over blokerede afsendere i **din** postkasse. Du kan få mere at vide [under Blokere en mailafsender](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

- ![Ikonet Send kun.](../../media/m365-cc-sc-create-icon.png) **Send kun**: Rapporterer meddelelsen til Microsoft til analyse. I pop op-menuen, der vises, skal du vælge følgende indstillinger:
  - **Vælg indsendelsestypen**: **Mail** (standard), **URL-adresse** eller **Fil**.
  - **Tilføj netværksmeddelelses-id'et, eller upload mailfilen**: Vælg en af følgende indstillinger:
    - **Tilføj mailnetværksmeddelelses-id'et** (standard med den tilsvarende værdi i feltet)
    - **Upload mailfilen (.msg eller eml)**: Klik på Gennemse filer  for at finde og vælge den .msg- eller .eml-meddelelsesfil, der skal indsendes.
  - **Vælg en modtager, der havde et problem**: Vælg en (foretrukken) eller flere oprindelige modtagere af meddelelsen for at analysere de politikker, der blev anvendt på dem.
  - **Vælg en årsag til at sende til Microsoft**: Vælg en af følgende muligheder:
    - **Burde ikke være blevet blokeret (falsk positiv)** (standard): Følgende indstillinger er tilgængelige:
      - **Tillad meddelelser som denne**: Denne indstilling er som standard slået fra (![slå til/fra).](../../media/scc-toggle-off.png) Slå den til (slå![ til](../../media/scc-toggle-on.png)) for midlertidigt at forhindre meddelelser med lignende URL-adresser, vedhæftede filer og andre egenskaber i at blive sat i karantæne. Når du slår denne indstilling til, er følgende tilgængelige:
        - **Fjern efter**: Vælg, hvor længe du vil tillade meddelelser som denne. Vælg **1 dag** til **30 dage**. Standardværdien er 30.
        - **Valgfri note**: Angiv en nyttig beskrivelse af tillad.
    - **Skulle være blevet blokeret (falsk negativ)**.

  Klik på Send, når du er **færdig**.

<sup>\*</sup> Denne indstilling er ikke tilgængelig for meddelelser, der allerede er blevet frigivet ( **statusværdien Frigivet** er **Udgivet**).

Hvis du ikke frigiver eller fjerner meddelelsen, slettes den, når standardopbevaringsperioden i karantæne udløber (som vist i **kolonnen Udløber** ).

> [!NOTE]
> På en mobilenhed er beskrivelsesteksten ikke tilgængelig på handlingsikonerne.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-mobile-actions.png" alt-text="Oplysninger om en meddelelse i karantæne med tilgængelige handlinger fremhævet" lightbox="../../media/quarantine-message-details-flyout-mobile-actions.png":::
>
> Ikonerne i rækkefølge og deres tilsvarende beskrivelser opsummeres i følgende tabel:
>
> |Ikon|Beskrivelse|
> |---:|---|
> |![Ikonet Frigiv mail.](../../media/m365-cc-sc-check-mark-icon.png)|**Udgivelsesmail**|
> |![Ikonet Del mail.](../../media/m365-cc-sc-share-email-icon.png)|**Del mail**|
> |![Ikonet Vis brevhoveder.](../../media/m365-cc-sc-view-message-headers-icon.png)|**Få vist brevhoveder for meddelelser**|
> |![Ikonet for eksempel på meddelelse.](../../media/m365-cc-sc-preview-message-icon.png)|**Forhåndsvisning af meddelelse**|
> |![Ikonet Slet fra karantæne.](../../media/m365-cc-sc-delete-icon.png)|**Slet fra karantæne**|
> |![Ikonet Download mail.](../../media/m365-cc-sc-download-icon.png)|**Download mail**|
> |![Ikonet Bloker afsender.](../../media/m365-cc-sc-block-sender-icon.png)|**Bloker afsender**|
> |![Ikonet Send kun.](../../media/m365-cc-sc-create-icon.png)|**Kun sende**|

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Handle på flere af dine mails i karantæne

Når du markerer flere meddelelser, der er sat i karantæne, på listen (op til 100) ved at klikke i det tomme område til venstre for den første  kolonne, vises rullelisten Massehandlinger, hvor du kan udføre følgende handlinger:

:::image type="content" source="../../media/quarantine-message-bulk-actions.png" alt-text="Rullelisten Massehandlinger for meddelelser i karantæne" lightbox="../../media/quarantine-message-bulk-actions.png":::

- ![Ikonet Frigiv mail.](../../media/m365-cc-sc-check-mark-icon.png) **Udgivelsesmeddelelser**: Udgiver meddelelser til alle modtagere. I pop op-menuen, der vises, kan du vælge følgende indstillinger, som er de samme, som når du slipper en enkelt meddelelse:
  - **Føj afsender til din organisations liste over tilladte**
  - **Send en kopi af denne meddelelse til andre modtagere**
  - **Send meddelelsen til Microsoft for at forbedre registrering (falsk positiv)**
  - **Tillad meddelelser som denne**:
    - **Fjern efter**: **1 dag** til **30 dage**
    - **Valgfri note**

  Klik på Slip meddelelse, når du **er færdig**.

  > [!NOTE]
  > Overvej følgende scenarie: john@gmail.com sender en meddelelse til faith@contoso.com og john@subsidiary.contoso.com. Gmail bifurcates this message into two copies that are both routed to quarantine as phishing in Microsoft. En administrator udgiver begge disse meddelelser til admin@contoso.com. Den første frigivne meddelelse, der når administratorpostkassen, leveres. Den anden udgivne meddelelse identificeres som duplikeret levering og ignoreres. Meddelelsen identificeres som dubletter, hvis de har samme meddelelses-id og modtaget tid.

- ![Ikonet Slet fra karantæne.](../../media/m365-cc-sc-delete-icon.png) **Slet meddelelser**: Når du har **klikket** på Ja i den advarsel, der vises, fjernes meddelelserne straks fra karantæne, uden at de sendes til de oprindelige modtagere.
- ![Ikonet Download mail.](../../media/m365-cc-sc-download-icon.png) **Download meddelelser**
- ![Ikonet Send kun.](../../media/m365-cc-sc-create-icon.png) **Kun sende**

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365"></a>Brug portalen Microsoft 365 Defender til at administrere filer, der er sat i karantæne, i Defender for Office 365

> [!NOTE]
> Fremgangsmåderne for filer, der er sat i karantæne i dette afsnit, er kun Microsoft Defender for Office 365 abonnenter på Plan 1 eller Plan 2.

I organisationer med Defender for Office 365 kan administratorer administrere filer, der er blevet sat i karantæne af Pengeskab Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams. Hvis du vil aktivere beskyttelse af disse filer, [skal du se aktivér Pengeskab Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

### <a name="view-quarantined-files"></a>Få vist filer, der er sat i karantæne

1. I portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **Mail & gennemsynskarantæne** \>  \>. Hvis du vil gå direkte til **siden Karantæne** , skal du bruge <https://security.microsoft.com/quarantine>.

2. På siden **Karantæne** skal du vælge **fanen** Filer (**Mail** er standardfanen).

3. Du kan sortere resultaterne ved at klikke på en tilgængelig kolonneoverskrift. Klik **på Tilpas kolonner** for at ændre de kolonner, der vises. Standardkolonnerne er markeret med en stjerne (<sup>\*</sup>):
   - **Bruger**<sup>\*</sup>
   - **Placering**<sup>\*</sup>
   - **Vedhæftet filnavn**<sup>\*</sup>
   - **URL-adresse til fil**<sup>\*</sup>
   - **Filstørrelse**
   - **Udgivelsesstatus**<sup>\*</sup>
   - **Udløber**<sup>\*</sup>
   - **Registreret af**
   - **Ændret af klokkeslæt**

   Når du er færdig, skal du klikke på **Anvend eller** **Annuller**.

4. Hvis du vil filtrere resultaterne, skal du klikke **på Filtrer**. Følgende filtre er tilgængelige i pop **op-vinduesruden** Filtre, der vises:
   - **Tidspunkt modtaget**: **Start- og** **sluttidspunktet** (dato).
   - **Udløber**: **Start- og** **sluttidspunktet** (dato).
   - **Årsagen til** karantæne: Den eneste tilgængelige værdi er **Malware**.
   - **Politiktype**

   Når du er færdig, skal du klikke på **Anvend eller** **Annuller**.

Når du har fundet en bestemt fil, der er sat i karantæne, skal du markere filen for at få vist oplysninger om den og for at handle på den (f.eks. få vist, udgive, downloade eller slette filen).

#### <a name="view-quarantined-file-details"></a>Få vist oplysninger om filer, der er sat i karantæne

Når du vælger en fil, der er sat i karantæne, på listen, kan du finde følgende oplysninger i pop op-menuen med oplysninger, der åbnes:

:::image type="content" source="../../media/quarantine-file-details-flyout.png" alt-text="Pop op-filen med oplysninger om en fil, der er sat i karantæne" lightbox="../../media/quarantine-file-details-flyout.png":::

- **Filnavn**
- **Filens** URL-adresse: URL-adresse, der definerer filens placering (f.eks. i SharePoint Online).
- **Skadeligt indhold registreret på** Den dato/det klokkeslæt, hvor filen var i karantæne.
- **Udløber**: Den dato, hvor filen bliver slettet fra karantæne.
- **Registreret af**
- **Udgivet?**
- **Malware-navn**
- **Dokument-id**: entydig identifier til dokumentet.
- **Filstørrelse**: I kilobyte (KB).
- **Organisation** Din organisations entydige id.
- **Senest ændret**
- **Ændret af**: Den bruger, der senest har ændret filen.
- **Værdi for Secure Hash Algorithm 256-bit (SHA-256**): Du kan bruge denne hash-værdi til at identificere filen i andre omdømmelagre eller andre steder i dit miljø.

Hvis du vil handle på filen, skal du se næste afsnit.

> [!NOTE]
> Hvis du vil forblive i pop op-menuen med oplysninger, men ændre den fil, du kigger på i karantæne, skal du bruge pil op og pil ned øverst i pop op-menuen.
>
> :::image type="content" source="../../media/quarantine-file-details-flyout-up-down-arrows.png" alt-text="Pil op og pil ned i pop op-pilene for filer, der er sat i karantæne" lightbox="../../media/quarantine-file-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-files"></a>Tag skridtet videre på filer, der er sat i karantæne

Når du har valgt en fil, der er sat i karantæne, på listen, kan du se følgende handlinger i pop op-menuen med oplysninger:

:::image type="content" source="../../media/quarantine-file-details-flyout-actions.png" alt-text="Handlingerne i pop op-filen med oplysninger for en fil, der er sat i karantæne" lightbox="../../media/quarantine-file-details-flyout-actions.png":::

- ![Ikon for udgivelsesfil.](../../media/m365-cc-sc-check-mark-icon.png) **Udgivelsesfil**<sup>\*</sup>: I pop op-ruden, der vises, skal du aktivere eller deaktivere **Rapportfiler til Microsoft til** analyse og derefter klikke på **Slip**.
- ![Ikon for udgivelsesfil.](../../media/m365-cc-sc-check-mark-icon.png)
- ![Ikonet Download fil.](../../media/m365-cc-sc-download-icon.png) **Download fil**: I pop op-pop-op-filen, der vises, skal du vælge Jeg forstår risikoen ved at downloade denne **fil og derefter** klikke på **Download** for at gemme en lokal kopi af filen.
- ![Ikonet Slet fra karantæne.](../../media/m365-cc-sc-delete-icon.png) **Slet fra karantæne**: Når du har **klikket på** Ja i den advarsel, der vises, slettes filen straks.
- ![Ikonet Bloker afsender.](../../media/m365-cc-sc-block-sender-icon.png) **Bloker** afsender: Føj afsenderen til listen over blokerede afsendere i **din** postkasse. Du kan få mere at vide [under Blokere en mailafsender](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

<sup>\*</sup> Denne indstilling er ikke tilgængelig for filer, der allerede er blevet frigivet ( **statusværdien Frigivet** er **Udgivet**).

Hvis du ikke frigiver eller fjerner filen, slettes den, når standardopbevaringsperioden i karantæne udløber (som vist i **kolonnen Udløber** ).

#### <a name="take-action-on-multiple-quarantined-files"></a>Tag skridtet videre på flere filer, der er sat i karantæne

Når du markerer flere filer, der er sat i karantæne, på listen (op til 100) ved at klikke i det tomme område til  venstre for kolonnen Emne, vises rullelisten Massehandlinger, hvor du kan udføre følgende handlinger:

:::image type="content" source="../../media/quarantine-file-bulk-actions.png" alt-text="Rullelisten Massehandlinger for filer i karantæne" lightbox="../../media/quarantine-file-bulk-actions.png":::

- ![Ikon for udgivelsesfil.](../../media/m365-cc-sc-check-mark-icon.png) **Udgivelsesfil**: I pop op-ruden, der vises, skal du aktivere eller deaktivere **Rapportfiler til Microsoft til** analyse og derefter klikke på **Slip**.
- ![Ikonet Slet fra karantæne.](../../media/m365-cc-sc-delete-icon.png) **Slet fra karantæne**: Når du har **klikket på** Ja i den advarsel, der vises, slettes filen straks.
- ![Ikonet Download fil.](../../media/m365-cc-sc-download-icon.png) **Download fil**: I pop op-pop-op-filen, der vises, skal du vælge Jeg forstår risikoen ved at downloade denne **fil og derefter** klikke på **Download** for at gemme en lokal kopi af filen.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-view-and-manage-quarantined-messages-and-files"></a>Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at få vist og administrere meddelelser og filer, der er sat i karantæne

De cmdlet'er, du bruger til at få vist og administrere meddelelser og filer i karantæne, er beskrevet på følgende liste:

- [Delete-QuarantineMessage](/powershell/module/exchange/delete-quarantinemessage)
- [Export-QuarantineMessage](/powershell/module/exchange/export-quarantinemessage)
- [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)
- [Preview-QuarantineMessage](/powershell/module/exchange/preview-quarantinemessage): Bemærk, at denne cmdlet kun er for meddelelser, ikke filer, der er sat i karantæne, fra Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams.
- [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)

## <a name="for-more-information"></a>Du kan finde flere oplysninger

[Ofte stillede spørgsmål om meddelelser i karantæne](quarantine-faq.yml)
