---
title: Mailsikkerhed med Threat Explorer i Microsoft Defender for Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/05/2021
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Få vist og undersøg phishing-forsøg på skadelig software.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 637e387ca457c9795892791a1a6d9326107fc6fb
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648189"
---
# <a name="email-security-with-threat-explorer-in-microsoft-defender-for-office-365"></a>Mailsikkerhed med Threat Explorer i Microsoft Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for:**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I denne artikel:

- [Vis malware, der er registreret i en mail](#view-malware-detected-in-email)
- [Vis phishing-URL-adresse, og klik på domsdata](#view-phishing-url-and-click-verdict-data)
- [Start automatiseret undersøgelse og svar](#start-automated-investigation-and-response)

> [!NOTE]
> Dette er en del af en **serie med tre artikler** om **Threat Explorer (Explorer),** **mailsikkerhed** og **registreringer i realtid** (f.eks. forskelle mellem værktøjerne og de tilladelser, der er nødvendige for at betjene dem). De to andre artikler i denne serie er [Trusselsjagt i Threat Explorer](threat-hunting-in-threat-explorer.md) og [Threat Explorer og registreringer i realtid](real-time-detections.md).

I denne artikel forklares det, hvordan du får vist og undersøger malware- og phishingforsøg, der registreres i en mail af Microsoft 365 sikkerhedsfunktioner.

## <a name="view-malware-detected-in-email"></a>Vis malware, der er registreret i en mail

Hvis du vil se malware, der er registreret i en mail, der er sorteret efter Microsoft 365 teknologi, skal du bruge visningen [**Mailmalware \>**](threat-explorer-views.md#email--malware) i Stifinder (eller registreringer i realtid). Malware er standardvisningen, så den kan vælges, så snart du åbner Stifinder.

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & samarbejde** og derefter vælge **Stifinder**- eller **realtidsregistreringer**. Hvis du vil gå direkte til siden, skal du bruge <https://security.microsoft.com/threatexplorer> eller <https://security.microsoft.com/realtimereports>.

   I dette eksempel bruges **Stifinder**.

   Herfra skal du starte ved Visningen, vælge en bestemt tidsperiode for at undersøge det (hvis det er nødvendigt) og fokusere dine filtre i henhold til [gennemgangen i Stifinder](threat-hunting-in-threat-explorer.md#threat-explorer-walk-through).

2. Kontrollér, at **Malware til mail** \> **er valgt** på rullelisten **Vis**.

3. Klik på **Afsender**, og vælg derefter **Basic** \> **Detection-teknologi** på rullelisten.

   :::image type="content" source="../../media/exploreremailmalwaredetectiontech-newimg.png" alt-text="Teknologien til registrering af malware" lightbox="../../media/exploreremailmalwaredetectiontech-newimg.png":::

   Dine registreringsteknologier er nu tilgængelige som filtre for rapporten.

4. Vælg en indstilling, og klik derefter på **Opdater** for at anvende filteret (opdater ikke browservinduet).

   :::image type="content" source="../../media/exploreremailmalwaredetectiontech2-new.png" alt-text="valgt registreringsteknologi" lightbox="../../media/exploreremailmalwaredetectiontech2-new.png":::

   Rapporten opdateres for at vise de resultater, som malware har registreret i en mail, ved hjælp af den valgte teknologiindstilling. Herfra kan du foretage yderligere analyser.

### <a name="report-a-message-as-clean-in-explorer"></a>Rapportér en meddelelse som ren i Stifinder

Du kan bruge indstillingen **Ren rapport** i Stifinder til at rapportere en meddelelse som falsk positiv. 

1. På Microsoft 365 Defender-portalen skal du gå til **Mail & samarbejdsstifinder** \> og derefter bekræfte, at **Phish** er valgt på rullelisten **Vis**.

2. Bekræft, at du er på fanen **Mail** , og vælg derefter den meddelelse, du vil rapportere som ren, på listen over rapporterede meddelelser. 

3. Klik på **Handlinger** for at udvide listen over indstillinger.

4. Rul ned på listen over indstillinger for at gå til afsnittet **Start ny indsendelse** , og vælg derefter **Rapportrens**. Der vises et pop op-vindue.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/report-clean-option-explorer.png" alt-text="Indstillingen Ren rapport i Stifinder" lightbox="../../media/report-clean-option-explorer.png":::

5. Slå skyderen til **Til**. På rullelisten skal du angive det antal dage, meddelelsen skal fjernes, tilføje en note, hvis det er nødvendigt, og derefter vælge **Send**. 

## <a name="view-phishing-url-and-click-verdict-data"></a>Vis phishing-URL-adresse, og klik på domsdata

Du kan få vist phishingforsøg via URL-adresser i en mail, herunder en liste over URL-adresser, der er tilladt, blokeret og tilsidesat. Hvis du vil identificere URL-adresser, der blev klikket på, skal [Pengeskab Links](safe-links.md) være konfigureret. Sørg for, at du konfigurerer [politikker for Pengeskab links](set-up-safe-links-policies.md) til beskyttelsestid og logføring af klik-dommene fra Pengeskab Links.

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & samarbejde** og derefter vælge **Stifinder**- eller **realtidsregistreringer**. Hvis du vil gå direkte til siden, skal du bruge <https://security.microsoft.com/threatexplorer> eller <https://security.microsoft.com/realtimereports>.

   I dette eksempel bruges **Stifinder**.

2. På rullelisten **Vis** skal du vælge **Mail-phish**\>.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerViewEmailPhishMenu.png" alt-text="Menuen Vis for Explorer i phishing-kontekst" lightbox="../../media/ExplorerViewEmailPhishMenu.png":::

3. Klik på **Afsender**, og vælg derefter **URL-adresser** \> **Klik på dom** på rullelisten.

4. I indstillinger, der vises, skal du vælge en eller flere indstillinger, f.eks **. Blokeret** og **Bloker tilsidesat**, og derefter klikke på **Opdater** (opdater ikke browservinduet).

    :::image type="content" source="../../media/threatexploreremailphishclickverdict-new.png" alt-text="URL-adresserne og klik på dommene" lightbox="../../media/threatexploreremailphishclickverdict-new.png":::

   Rapporten opdateres for at vise to forskellige URL-tabeller under fanen **URL-adresser** under rapporten:

   - **De mest populære URL-adresser** er URL-adresserne i de meddelelser, du filtrerede ned til, og antallet af handlinger til levering af mails for hver URL-adresse. I mailvisningen Phish indeholder denne liste typisk legitime URL-adresser. Hackere inkluderer en blanding af gode og dårlige URL-adresser i deres meddelelser for at forsøge at få dem leveret, men de får de skadelige links til at se mere interessante ud. Tabellen med URL-adresser sorteres efter det samlede antal mails, men denne kolonne er skjult for at forenkle visningen.

   - **De mest populære klik** er de Pengeskab linksombrudte URL-adresser, der blev klikket på, sorteret efter det samlede antal klik. Denne kolonne vises heller ikke for at forenkle visningen. Det samlede antal pr. kolonne angiver antallet af Pengeskab links, der klikker på dom for hver url-adresse, der klikkes på. I mailvisningen Phish er disse normalt mistænkelige eller skadelige URL-adresser. Men visningen kan indeholde URL-adresser, der ikke er trusler, men som findes i phish-meddelelser. URL-klik på links, der ikke er føjet til, vises ikke her.

   De to tabeller med URL-adresser viser de mest populære URL-adresser i phishing-mails efter leveringshandling og placering. Tabellerne viser url-klik, der blev blokeret eller besøgt trods en advarsel, så du kan se, hvilke potentielle forkerte links der blev præsenteret for brugerne, og at brugerne klikkede på dem. Herfra kan du foretage yderligere analyser. Under diagrammet kan du f.eks. se de øverste URL-adresser i mails, der er blokeret i organisationens miljø.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerPhishClickVerdictURLs.png" alt-text="De URL-adresser til Stifinder, der blev blokeret" lightbox="../../media/ExplorerPhishClickVerdictURLs.png":::

   Vælg en URL-adresse for at få vist mere detaljerede oplysninger.

   > [!NOTE]
   > I dialogboksen URL-adresse er filtreringen af mails fjernet for at få vist den fulde visning af URL-adressens eksponering i dit miljø. Dette giver dig mulighed for at filtrere efter mails, du er bekymret for i Stifinder, finde bestemte URL-adresser, der er potentielle trusler, og derefter udvide din forståelse af eksponeringen af URL-adresser i dit miljø (via dialogboksen MED URL-oplysninger) uden at skulle føje URL-filtre til selve Stifinder-visningen.

### <a name="interpretation-of-click-verdicts"></a>Fortolkning af click-dommene

I pop op-vinduet Mail eller URL-adresse, De vigtigste klik og i vores filtreringsoplevelser får du vist forskellige værdier for click-dom:

- **Ingen:** Dommen for URL-adressen kunne ikke registreres. Brugeren har muligvis klikket via URL-adressen.
- **Tilladt:** Brugeren fik tilladelse til at navigere til URL-adressen.
- **Blokeret:** Brugeren blev blokeret fra at navigere til URL-adressen.
- **Afventer dom:** Brugeren blev præsenteret for den side, der afventer detonation.
- **Blokeret tilsidesat:** Brugeren blev blokeret fra at navigere direkte til URL-adressen. Men brugeren tilsidesætter blokken for at navigere til URL-adressen.
- **Afventer dom omgået:** Brugeren blev præsenteret for detonationssiden. Men brugeren tilsidesætter meddelelsen for at få adgang til URL-adressen.
- **Fejl:** Brugeren blev præsenteret for fejlsiden, eller der opstod en fejl under hentning af dommen.
- **Fiasko:** Der opstod en ukendt undtagelse under hentning af dommen. Brugeren har muligvis klikket via URL-adressen.

## <a name="start-automated-investigation-and-response"></a>Start automatiseret undersøgelse og svar

> [!NOTE]
> Automatiserede undersøgelses- og svarfunktioner er tilgængelige i *Microsoft Defender for Office 365 Plan 2* og *Office 365 E5*.

[Automatiseret undersøgelse og svar](automated-investigation-response-office.md) kan spare tid og kræfter på at undersøge og mitigere cyberangreb på dit sikkerhedsteam. Ud over at konfigurere beskeder, der kan udløse en sikkerhedslegebog, kan du starte en automatisk undersøgelses- og svarproces fra en visning i Stifinder. Du kan finde flere oplysninger under [Eksempel: En sikkerhedsadministrator udløser en undersøgelse fra Stifinder](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).

## <a name="other-articles"></a>Andre artikler

[Undersøg mails med mailenhedssiden](mdo-email-entity-page.md)
