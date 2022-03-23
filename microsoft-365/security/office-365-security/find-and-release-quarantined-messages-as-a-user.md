---
title: Find og slip meddelelser, der er sat i karantæne, som en bruger
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Consumer/IW
ms.topic: how-to
ms.localizationpriority: high
search.appverid:
- MET150
- MEW150
ms.assetid: efff08ec-68ff-4099-89b7-266e3c4817be
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Brugerne kan lære, hvordan de får vist og administrerer meddelelser, der er sat i Exchange Online Protection (EOP), der skulle være blevet leveret til dem.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1cfdd441cff8481ef1ec7ea5ef3cabc54f062694
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63589126"
---
# <a name="find-and-release-quarantined-messages-as-a-user-in-eop"></a>Find og slip meddelelser, der er sat i karantæne, som en bruger i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 med postkasser i Exchange Online eller enkeltstående Exchange Online Protection (EOP)-organisationer uden Exchange Online-postkasser, sætter karantæne i potentielt farlig eller uønskede meddelelser. Du kan få mere at vide [under Karantæne i EOP](quarantine-email-messages.md).

Som en almindelig bruger (ikke en administrator) er  de standardfunktioner, der er tilgængelige for dig som modtager af en meddelelse i karantæne, beskrevet i følgende tabel:

<br>

****

|Årsagen til karantæne|Vis|Udgivelse|Slet|
|---|:---:|:---:|:---:|
|**Antispampolitikker**||||
|Masse|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|
|Spam|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|
|Spam med høj tillid|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|
|Phishing|![Markering.](../../media/checkmark.png)|![Markering](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|
|Phishing med høj tillid||||
|**Antiphishing-politikker**||||
|Efterlignet intelligensbeskyttelse i EOP|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|
|Efterligning af brugerbeskyttelse i Defender for Office 365|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|
|Efterligning af domænebeskyttelse i Defender for Office 365|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|
|Postkasseintelligensbeskyttelse i Defender til Office 365|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|
|**Antimalwarepolitikker**||||
|Mails med vedhæftede filer, der er sat i karantæne som malware.||||
|**Pengeskab vedhæftede filer i Defender til Office 365**||||
|Pengeskab politikker for vedhæftede filer, der sætter mails i karantæne med skadelige vedhæftede filer som malware.||||
|Pengeskab Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams, der sætter skadelige filer i karantæne som malware.||||
|**Regler for mailflow (transportregler)**||||
|Regler for mailflow, der sætter mails i karantæne.||||
|

_Karantænepolitikker_ definerer, hvad brugere har tilladelse til at gøre til meddelelser, der er sat i karantæne, baseret på, hvorfor meddelelsen var i karantæne i [understøttede funktioner](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). Standardkarantænepolitikker gennemtvinger de historiske egenskaber som beskrevet i den forrige tabel. Administratorer kan oprette og anvende brugerdefinerede karantænepolitikker, der definerer mindre restriktive eller mere restriktive funktioner for brugere i understøttede funktioner. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).

Du kan få vist og administrere dine meddelelser, der er i karantæne, Microsoft 365 Defender portalen eller (hvis en administrator har konfigureret denne) karantænemeddelelser fra karantænepolitikker.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Hvis du vil åbne Microsoft 365 Defender, skal du gå til <https://security.microsoft.com>. Hvis du vil gå direkte til **siden Karantæne** , skal du bruge <https://security.microsoft.com/quarantine>.

- Administratorer kan konfigurere, hvor længe meddelelser opbevares i karantæne, før de slettes permanent i antispampolitikker. Meddelelser, der er udløbet fra karantæne, kan ikke gendannes. Få mere at vide under [Konfigurer antispam-politikker i EOP](configure-your-spam-filter-policies.md).

- Som standard er meddelelser, der var i karantæne for phishing, malware eller regler for mailflow, kun tilgængelige for administratorer og er ikke synlige for brugere. Få mere at vide under [Administrer meddelelser og filer, der er sat i karantæne som administrator i EOP](manage-quarantined-messages-and-files.md).

## <a name="view-your-quarantined-messages"></a>Få vist dine meddelelser, der er sat i karantæne

> [!NOTE]
> Din mulighed for at få vist meddelelser, der er i [](quarantine-policies.md) karantæne, styres af den karantænepolitik, der gælder for meddelelsestypen i karantæne (som kan være standardkarantænepolitikken [for årsagen til karantæne](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features)).

1. I portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **Mail & gennemsynskarantæne** \>  \>. Hvis du vil gå direkte til **siden Karantæne** , skal du bruge <https://security.microsoft.com/quarantine>.

2. På siden **Karantæne** kan du sortere resultaterne ved at klikke på en tilgængelig kolonneoverskrift. Klik **på Tilpas kolonner**  for at ændre de kolonner, der vises. Standardværdierne er markeret med en stjerne (<sup>\*</sup>):

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

   Klik på Anvend, når du er **færdig**.

3. Hvis du vil filtrere resultaterne, skal du klikke **på Filtrer**. Følgende filtre er tilgængelige i pop **op-vinduesruden** Filtre, der vises:
   - **Meddelelses-id**: GUID (Globally Unique Identifier) i meddelelsen.
   - **Afsenderadresse**
   - **Modtageradresse**
   - **Emne**
   - **Tidspunkt modtaget**: Angiv et **start- og** **sluttidspunktet** (dato).
   - **Udløber:** Filtrerer meddelelser efter, hvornår de udløber fra karantæne:
     - **I dag**
     - **Næste 2 dage**
     - **Næste 7 dage**
     - **Brugerdefineret**: Angiv **et Start-klokkeslæt** **og Et Slut-klokkeslæt** (dato).
   - **Årsagen til karantæne**:
     - **Masse**
     - **Spam**
     - **Phishing**: Spamfilteret var **phishing** - eller antiphishingbeskyttelse i karantæne for meddelelsen ([spoof-indstillinger](set-up-anti-phishing-policies.md#spoof-settings) [eller beskyttelse mod efterligning](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)).
     - **Phishing med høj tillid**
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

   Klik på Anvend, når du er **færdig**. Klik på ikonet Ryd filtre for at ![rydde filtrene.](../../media/m365-cc-sc-clear-filters-icon.png) **Ryd filtre**.

4. Brug **søgefeltet** og en tilsvarende værdi til at finde bestemte meddelelser. Jokertegn understøttes ikke. Du kan søge efter følgende værdier:
   - Meddelelses-id
   - Afsendermailadresse
   - Modtagerens mailadresse
   - Emne. Brug hele meddelelsens emne. Der er ikke store og små bogstaver i søgningen.
   - Politiknavn. Brug hele politikkens navn. Der er ikke store og små bogstaver i søgningen.

   Når du har angivet søgekriterierne, skal du trykke på Enter for at filtrere resultaterne.

Når du har fundet en bestemt meddelelse, der er sat i karantæne, skal du markere meddelelsen for at få vist oplysninger om den og for at handle på den (f.eks. få vist, slippe, hente eller slette meddelelsen).

### <a name="view-quarantined-message-details"></a>Få vist oplysninger om meddelelser i karantæne

Når du markerer en meddelelse, der er sat i karantæne, på listen, kan du finde følgende oplysninger i pop op-dialogboksen med oplysninger, der vises.

![Pop op-meddelelsen med oplysninger om en meddelelse, der er sat i karantæne.](../../media/quarantine-user-message-details.png)

Når du vælger en mail på listen, vises følgende meddelelsesoplysninger i pop **op-ruden** Detaljer:

- **Meddelelses-id**: GUID (Globally Unique Identifier) for meddelelsen.
- **Afsenderadresse**
- **Modtaget**: Dato/klokkeslæt for modtagelse af meddelelsen.
- **Emne**
- **Årsagen til karantæne**
- **Politiktype**: Typen af politik. F.eks **. Antispam-politik**.
- **Antal modtagere**
- **Modtagere:** Hvis meddelelsen indeholder flere modtagere, skal du klikke på Vis meddelelse eller  Vis brevhoved  for at få vist hele listen over modtagere.
- **Udløber**: Den dato/det klokkeslæt, hvor meddelelsen automatisk og permanent slettes fra karantæne.

Hvis du vil handle på meddelelsen, skal du se næste afsnit.

> [!NOTE]
> Hvis du vil forblive i pop op-mailen med oplysninger, men ændre den meddelelse, du kigger på i karantæne, skal du bruge pil op og pil ned øverst i pop-op-meddelelsen.
>
> ![Pil op og pil ned i pop op-pilene for oplysninger for en meddelelse, der er sat i karantæne.](../../media/quarantine-message-details-flyout-up-down-arrows.png)

### <a name="take-action-on-quarantined-email"></a>Handle på en mail, der er sat i karantæne

> [!NOTE]
> Din mulighed for at handle på meddelelser, der er sat i karantæne[](quarantine-policies.md), styres af den karantænepolitik, der gælder for meddelelsestypen i karantæne (som kan være standardkarantænepolitikken [for årsagen til karantæne](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features)). I dette afsnit beskrives alle tilgængelige handlinger.

Når du har valgt en meddelelse, der er sat i karantæne, på listen, kan du vælge følgende handlinger i pop op-menuen med oplysninger:

![Tilgængelige handlinger i pop op-menuen med oplysninger for en meddelelse, der er sat i karantæne.](../../media/quarantine-user-message-details-flyout-actions.png)

- ![Ikonet Frigiv mail.](../../media/m365-cc-sc-check-mark-icon.png) **Frigiv**<sup>\*</sup> mail: Leverer meddelelsen til din indbakke.

- ![Ikonet Vis brevhoveder.](../../media/m365-cc-sc-eye-icon.png) **Få vist brevhoveder:** Vælg dette link for at få vist teksten i brevhovedet. Pop **op-mailens** brevhoved vises med følgende links:
- **Kopiér brevhoved**: Klik på dette link for at kopiere brevhovedet (alle brevhovedfelter) til din udklipsholder.
- **Microsoft Analyse af brevhoved**: Hvis du vil analysere brevhovedfelterne og værdierne i dybden, skal du klikke på dette link for at gå til Analyse af brevhoved. Indsæt brevhovedet i indsæt brevhovedet Indsæt det brevhoved, du vil analysere (Ctrl+V eller højreklik, og vælg Sæt **ind), og** klik derefter  på **Analysér brevhoveder**.

Følgende handlinger er tilgængelige, når du klikker på ![ikonet Flere handlinger.](../../media/m365-cc-sc-more-actions-icon.png) **Flere handlinger**:

- ![Ikonet for eksempel på meddelelse.](../../media/m365-cc-sc-eye-icon.png) **Eksempelmeddelelse**: I pop op-menuen, der vises, skal du vælge en af følgende faner:
  - **Kilde**: Viser HTML-versionen af brødteksten i meddelelsen, hvor alle links er deaktiveret.
  - **Almindelig tekst**: Viser meddelelsesteksten i almindelig tekst.

- ![Ikonet Fjern fra karantæne.](../../media/m365-cc-sc-delete-icon.png) **Fjern fra karantæne**: Når du har **klikket** på Ja i den advarsel, der vises, slettes meddelelsen straks, uden at den sendes til de oprindelige modtagere.

- ![Ikonet Download mail.](../../media/m365-cc-sc-download-icon.png) **Download mail**: I pop op-menuen, der vises, skal du vælge Jeg forstår risikoen ved at hente denne **meddelelse og derefter** klikke på **Download** for at gemme en lokal kopi af meddelelsen i .eml-format.

- ![Ikonet Bloker afsender.](../../media/m365-cc-sc-block-sender-icon.png) **Bloker** afsender: Føj afsenderen til listen over blokerede afsendere i **din** postkasse. Du kan få mere at vide [under Blokere en mailafsender](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

<sup>\*</sup> Denne indstilling er ikke tilgængelig for meddelelser, der allerede er blevet frigivet ( **statusværdien Frigivet** er **Udgivet**).

Hvis du ikke frigiver eller fjerner meddelelsen, slettes den, når standardopbevaringsperioden i karantæne udløber (som vist i **kolonnen Udløber** ).

> [!NOTE]
> På en mobilenhed er beskrivelsesteksten ikke tilgængelig på handlingsikonerne.
>
> ![Oplysninger om en meddelelse i karantæne med tilgængelige handlinger fremhævet.](../../media/quarantine-user-message-details-flyout-mobile-actions.png)
>
> Ikonerne i rækkefølge og deres tilsvarende beskrivelser opsummeres i følgende tabel:
>
> |Ikon|Beskrivelse|
> |---:|---|
> |![Ikonet Frigiv mail.](../../media/m365-cc-sc-check-mark-icon.png)|**Udgivelsesmail**|
> |![Ikonet Vis brevhoveder.](../../media/m365-cc-sc-eye-icon.png)|**Få vist brevhoveder for meddelelser**|
> |![Ikonet for eksempel på meddelelse.](../../media/m365-cc-sc-eye-icon.png)|**Forhåndsvisning af meddelelse**|
> |![Ikonet Fjern fra karantæne.](../../media/m365-cc-sc-delete-icon.png)|**Fjern fra karantæne**|
> |![Ikonet Bloker afsender.](../../media/m365-cc-sc-block-sender-icon.png)|**Bloker afsender**|

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Handle på flere af dine mails i karantæne

Når du markerer flere meddelelser, der er sat i karantæne, på listen (op til 100) ved at klikke i det tomme område til venstre for den første  kolonne, vises rullelisten Massehandlinger, hvor du kan udføre følgende handlinger:

![Rullelisten Massehandlinger for meddelelser i karantæne.](../../media/quarantine-user-message-bulk-actions.png)

- ![Ikonet Frigiv mail.](../../media/m365-cc-sc-check-mark-icon.png) **Frigiv** meddelelser: Leverer meddelelserne til din indbakke.
- ![Ikonet Fjern fra karantæne.](../../media/m365-cc-sc-delete-icon.png) **Slet meddelelser**: Når du har **klikket** på Ja i den advarsel, der vises, fjernes meddelelserne straks fra karantæne, uden at de sendes til de oprindelige modtagere.
