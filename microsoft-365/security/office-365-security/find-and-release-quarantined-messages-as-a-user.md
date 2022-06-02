---
title: Find og frigiv meddelelser i karantæne som en bruger
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
description: Brugerne kan få mere at vide om, hvordan de får vist og administrerer karantænemeddelelser i Exchange Online Protection (EOP), der skulle have været leveret til dem.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bc3e53283f59d7a750e05d56718d389f48e6a9d9
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840010"
---
# <a name="find-and-release-quarantined-messages-as-a-user-in-eop"></a>Find og frigiv karantænemeddelelser som en bruger i EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående EOP-organisationer (Exchange Online Protection) uden Exchange Online postkasser, indeholder karantæne potentielt farlige eller uønskede meddelelser. Du kan få flere oplysninger under [Karantæne i EOP](quarantine-email-messages.md).

Som almindelig bruger (ikke administrator) er de **standardfunktioner** , der er tilgængelige for dig som modtager af en karantænemeddelelse, beskrevet i følgende tabel:

|Årsag til karantæne|Vis|Udgivelse|Slette|
|---|:---:|:---:|:---:|
|**Politikker til bekæmpelse af spam**||||
|Bulk|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|
|Spam|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|
|Spam med høj genkendelsessikkerhed|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|
|Phishing|![Markeret.](../../media/checkmark.png)|![Markeret](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|
|Phishing med høj genkendelsessikkerhed||||
|**Politikker for antiphishing**||||
|Spoof intelligence-beskyttelse i EOP|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|
|Repræsenteret brugerbeskyttelse i Defender for Office 365|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|
|Repræsenteret domænebeskyttelse i Defender for Office 365|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|
|Beskyttelse af postkasseintelligens i Defender for Office 365|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|
|**Politikker for antimalware**||||
|Mails med vedhæftede filer, der er sat i karantæne som malware.||||
|**Sikre vedhæftede filer i Defender for Office 365**||||
|Pengeskab politikker for vedhæftede filer, der sætter mails med skadelige vedhæftede filer i karantæne som malware.||||
|Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams, der sætter skadelige filer i karantæne som malware.||||
|**Regler for mailflow (transportregler)**||||
|Regler for mailflow, der sætter mails i karantæne.||||

_Karantænepolitikker_ definerer, hvad brugerne har tilladelse til at gøre for meddelelser i karantæne baseret på, hvorfor meddelelsen blev sat i karantæne i [understøttede funktioner](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). Standardkarantatpolitikker gennemtvinger de historiske funktioner, som beskrevet i den forrige tabel. Administratorer kan oprette og anvende brugerdefinerede karantænepolitikker, der definerer mindre restriktive eller mere restriktive funktioner for brugere i understøttede funktioner. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).

Du kan få vist og administrere dine karantænemeddelelser på Microsoft 365 Defender-portalen eller (hvis en administrator har konfigureret dette) karantænemeddelelser fra karantænepolitikker.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Hvis du vil åbne Microsoft 365 Defender-portalen, skal du gå til <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Karantæne** , skal du bruge <https://security.microsoft.com/quarantine>.

- Administratorer kan konfigurere, hvor længe meddelelser holdes i karantæne, før de slettes permanent i politikker mod spam. Meddelelser, der er udløbet fra karantæne, kan ikke genoprettes. Du kan få flere oplysninger under [Konfigurer politikker til bekæmpelse af spam i EOP](configure-your-spam-filter-policies.md).

- Meddelelser, der er sat i karantæne for phishing med høj sikkerhed, malware eller regler for mailflow, er som standard kun tilgængelige for administratorer og er ikke synlige for brugerne. Du kan få flere oplysninger under [Administrer karantænerede meddelelser og filer som administrator i EOP](manage-quarantined-messages-and-files.md).

## <a name="view-your-quarantined-messages"></a>Få vist dine karantænemeddelelser

> [!NOTE]
> Din mulighed for at få vist karantænemeddelelser styres af den [karantænepolitik](quarantine-policies.md) , der gælder for den karantænerede meddelelsestype (som kan være [standard karantænepolitikken af karantæneårsagen](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features)).

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & karantæne for gennemsyn**  \> af samarbejde.\> Hvis du vil gå direkte til siden **Karantæne** , skal du bruge <https://security.microsoft.com/quarantine>.

2. På siden **Karantæne** kan du sortere resultaterne ved at klikke på en tilgængelig kolonneoverskrift. Klik på **Tilpas kolonner**  for at ændre de kolonner, der vises. Standardværdierne er markeret med en stjerne (<sup>\*</sup>):

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

   Klik på **Anvend**, når du er færdig.

3. Klik på **Filter** for at filtrere resultaterne. Følgende filtre er tilgængelige i pop op-vinduet **Filtre** , der vises:
   - **Meddelelses-id**: Meddelelsens globalt entydige id.
   - **Afsenderadresse**
   - **Modtageradresse**
   - **Emne**
   - **Modtaget klokkeslæt**: Angiv **starttidspunkt** og **sluttidspunkt** (dato).
   - **Udløber: Filtrer** meddelelser efter, hvornår de udløber fra karantæne:
     - **Dag**
     - **De næste 2 dage**
     - **De næste 7 dage**
     - **Brugerdefineret**: Angiv et **starttidspunkt** og **et sluttidspunkt** (dato).
   - **Karantæneårsag**:
     - **Bulk**
     - **Spam**
     - **Phishing**: Spamfilterets dom var **,** at meddelelsen var sat i karantæne ([spoof-indstillinger](set-up-anti-phishing-policies.md#spoof-settings) eller [repræsentationsbeskyttelse](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)) i phishing- eller anti-phishing-beskyttelse.
     - **Phishing med høj genkendelsessikkerhed**
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

   Klik på **Anvend**, når du er færdig. Klik på ![ikonet Ryd filtre for at rydde filtrene.](../../media/m365-cc-sc-clear-filters-icon.png) **Ryd filtre**.

4. Brug **søgefeltet** og en tilsvarende værdi til at finde bestemte meddelelser. Jokertegn understøttes ikke. Du kan søge efter følgende værdier:
   - Meddelelses-id
   - Afsendermailadresse
   - Modtagermailadresse
   - Emne. Brug hele meddelelsens emne. Der skelnes ikke mellem store og små bogstaver i søgningen.
   - Politiknavn. Brug hele politiknavnet. Der skelnes ikke mellem store og små bogstaver i søgningen.

   Når du har angivet søgekriterierne, skal du trykke på ENTER for at filtrere resultaterne.

Når du har fundet en bestemt karantænemeddelelse, skal du vælge meddelelsen for at få vist detaljer om den og udføre handlinger på den (f.eks. få vist, udgive, downloade eller slette meddelelsen).

### <a name="view-quarantined-message-details"></a>Vis oplysninger om karantænemeddelelse

Når du vælger karantænemeddelelse på listen, er følgende oplysninger tilgængelige i det detaljerede pop op-vindue, der vises.

:::image type="content" source="../../media/quarantine-user-message-details.png" alt-text="Pop op-vinduet med detaljer for en karantænemeddelelse" lightbox="../../media/quarantine-user-message-details.png":::

Når du vælger en mail på listen, vises følgende meddelelsesoplysninger i ruden **Detaljer** :

- **Meddelelses-id**: Meddelelsens globalt entydige id.
- **Afsenderadresse**
- **Modtaget**: Den dato/det klokkeslæt, hvor meddelelsen blev modtaget.
- **Emne**
- **Årsag til karantæne**
- **Politiktype**: Politiktypen. For eksempel **anti-spam-politik**.
- **Antal modtagere**
- **Modtagere**: Hvis meddelelsen indeholder flere modtagere, skal du klikke på **Vis meddelelse** eller **Vis brevhoved** for at se den komplette liste over modtagere.
- **Udløber**: Den dato/det klokkeslæt, hvor meddelelsen automatisk slettes og slettes permanent fra karantæne.

Hvis du vil udføre en handling på meddelelsen, skal du se næste afsnit.

> [!NOTE]
> Hvis du vil forblive i pop op-vinduet med detaljer, men ændre den karantænemeddelelse, du kigger på, skal du bruge pil op og ned øverst i pop op-vinduet.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-up-down-arrows.png" alt-text="Pil op og ned i detaljevinduet i en karantænemeddelelse" lightbox="../../media/quarantine-message-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-email"></a>Udfør en handling på karantænemail

> [!NOTE]
> Din mulighed for at udføre handlinger på karantænemeddelelser styres af den [karantænepolitik](quarantine-policies.md) , der gælder for den karantænerede meddelelsestype (som kan være [standardkarneret politik af karantæneårsagen](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features)). I dette afsnit beskrives alle tilgængelige handlinger.

Når du har valgt en karantænemeddelelse på listen, er følgende handlinger tilgængelige i pop op-vinduet med detaljer:

:::image type="content" source="../../media/quarantine-user-message-details-flyout-actions.png" alt-text="De tilgængelige handlinger i pop op-vinduet med detaljer i en karantænemeddelelse" lightbox="../../media/quarantine-user-message-details-flyout-actions.png":::

- ![Ikonet Udgivelsesmail.](../../media/m365-cc-sc-check-mark-icon.png) **Udgivelsesmail**<sup>\*</sup>: Leverer meddelelsen til din indbakke.

- ![Vis ikonet for brevhoveder.](../../media/m365-cc-sc-eye-icon.png) **Vis brevhoveder**: Vælg dette link for at få vist teksten i brevhovedet. Pop **op-vinduet Meddelelsesheader** vises med følgende links:
- **Kopiér brevhoved**: Klik på dette link for at kopiere brevhovedet (alle headerfelter) til Udklipsholder.
- **Microsoft Message Header Analyzer**: Hvis du vil analysere overskriftsfelterne og værdierne i dybden, skal du klikke på dette link for at gå til Analyse af meddelelsesoverskrift. Indsæt brevhovedet i sektionen **Indsæt det brevhoved, du vil analysere** (CTRL+V, eller højreklik, og vælg **Sæt ind**), og klik derefter på **Analysér brevhoveder**.

Følgende handlinger er tilgængelige, når du har klikket på ![ikonet Flere handlinger.](../../media/m365-cc-sc-more-actions-icon.png) **Flere handlinger**:

- ![Vis meddelelsesikon.](../../media/m365-cc-sc-eye-icon.png) **Vis meddelelse**: Vælg en af følgende faner i det pop op-vindue, der vises:
  - **Kilde**: Viser HTML-versionen af meddelelsens brødtekst med alle links deaktiveret.
  - **Almindelig tekst**: Viser meddelelsens brødtekst som almindelig tekst.

- ![Fjern fra karantæneikonet.](../../media/m365-cc-sc-delete-icon.png) **Fjern fra karantæne**: Når du har klikket på **Ja** i advarslen, slettes meddelelsen straks uden at blive sendt til de oprindelige modtagere.

- ![Ikonet Download mail.](../../media/m365-cc-sc-download-icon.png) **Download mail**: I det pop op-vindue, der vises, skal du vælge **Jeg forstår risikoen ved at downloade denne meddelelse** og derefter klikke på **Download** for at gemme en lokal kopi af meddelelsen i .eml-format.

- ![Ikonet Bloker afsender.](../../media/m365-cc-sc-block-sender-icon.png) **Bloker afsender**: Føj afsenderen til listen Over blokerede afsendere i **postkassen** . Du kan få flere oplysninger under [Bloker en mailsender](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

<sup>\*</sup>Denne indstilling er ikke tilgængelig for meddelelser, der allerede er udgivet (statusværdien **Frigives**).

Hvis du ikke frigiver eller fjerner meddelelsen, slettes den, når standardopbevaringsperioden for karantæne udløber (som vist i kolonnen **Udløber** ).

> [!NOTE]
> På en mobilenhed er beskrivelsesteksten ikke tilgængelig på handlingsikonerne.
>
> :::image type="content" source="../../media/quarantine-user-message-details-flyout-mobile-actions.png" alt-text="Detaljerne for en karantænemeddelelse med tilgængelige handlinger fremhævet" lightbox="../../media/quarantine-user-message-details-flyout-mobile-actions.png":::

>
> Ikonerne i rækkefølge og deres tilsvarende beskrivelser opsummeres i følgende tabel:
>
> |Ikon|Beskrivelse|
> |---:|---|
> |![Ikonet Udgivelsesmail.](../../media/m365-cc-sc-check-mark-icon.png)|**Frigiv mail**|
> |![Vis ikonet for brevhoveder.](../../media/m365-cc-sc-eye-icon.png)|**Vis brevhoveder**|
> |![Vis meddelelsesikon.](../../media/m365-cc-sc-eye-icon.png)|**Vis meddelelse**|
> |![Fjern fra karantæneikonet.](../../media/m365-cc-sc-delete-icon.png)|**Fjern fra karantæne**|
> |![Ikonet Bloker afsender.](../../media/m365-cc-sc-block-sender-icon.png)|**Afsender af blok**|

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Udfør en handling på flere mails i karantæne

Når du vælger flere karantænemeddelelser på listen (op til 100) ved at klikke i det tomme område til venstre for den første kolonne, vises rullelisten **Massehandlinger** , hvor du kan udføre følgende handlinger:

:::image type="content" source="../../media/quarantine-user-message-bulk-actions.png" alt-text="Rullelisten massehandlinger for meddelelser i karantæne" lightbox="../../media/quarantine-user-message-bulk-actions.png":::

- ![Ikonet Udgivelsesmeddelelser.](../../media/m365-cc-sc-check-mark-icon.png) **Udgivelsesmeddelelser**: Leverer meddelelserne til din indbakke.
- ![Fjern fra karantæneikonet.](../../media/m365-cc-sc-delete-icon.png) **Slet meddelelser**: Når du har klikket på **Ja** i advarslen, fjernes meddelelserne straks fra karantænen uden at blive sendt til de oprindelige modtagere.
