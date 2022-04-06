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
description: Få vist og undersøg forsøg på phishing på malware.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: da555769cbff177fff7de4ee4a25908e1eee3782
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475119"
---
# <a name="email-security-with-threat-explorer-in-microsoft-defender-for-office-365"></a>Mailsikkerhed med Threat Explorer i Microsoft Defender for Office 365

I denne artikel:

- [Få vist malware registreret i en mail](#view-malware-detected-in-email)
- [Få vist phishing-URL-adresse, og klik på vurderingsdata](#view-phishing-url-and-click-verdict-data)
- [Start automatiseret undersøgelse og svar](#start-automated-investigation-and-response)

> [!NOTE]
> Dette er en del af en **3-artikelserie** om **Trusselsstifinder** **(Explorer)****,** mailsikkerhed og Explorer og registreringer i realtid (f.eks. forskelle mellem værktøjerne og de tilladelser, der er nødvendige for at kunne betjene dem). De andre to artikler i denne serie er [Trusselssøgning i Threat Explorer](threat-hunting-in-threat-explorer.md) [og Threat Explorer og registreringer i realtid](real-time-detections.md).

I denne artikel forklares det, hvordan du kan få vist og undersøge malware og phishingforsøg, der registreres i mails, Microsoft 365 sikkerhedsfunktioner.

**Gælder for:**

- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="view-malware-detected-in-email"></a>Få vist malware registreret i en mail

For at få malware registreret i mails, der er sorteret efter Microsoft 365, [**\>**](threat-explorer-views.md#email--malware) skal du bruge visningen Mailmalware i Stifinder (eller registreringer i realtid). Malware er standardvisningen, så den bliver muligvis valgt, så snart du åbner Stifinder.

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **& og samarbejde** og derefter vælge **Stifinder****- eller realtidsregistreringer**. For at gå direkte til siden skal du bruge <https://security.microsoft.com/threatexplorer> eller <https://security.microsoft.com/realtimereports>.

   I dette eksempel bruges **Stifinder**.

   Herfra skal du begynde med visningen vælge en bestemt tidsramme, der skal undersøges (hvis det er nødvendigt), og fokusere på filtrene i henhold til [gennemgangen i Stifinder](threat-hunting-in-threat-explorer.md#threat-explorer-walk-through).

2. Kontrollér **, at Mailmalware** er **markeret på** \> **rullelisten** Vis.

3. Klik **på Afsender**, og **vælg derefter** \> **Teknologi til grundlæggende** registrering på rullelisten.

   :::image type="content" source="../../media/exploreremailmalwaredetectiontech-newimg.png" alt-text="Teknologien til registrering af malware" lightbox="../../media/exploreremailmalwaredetectiontech-newimg.png":::

   Dine registreringsteknologier er nu tilgængelige som filtre til rapporten.

4. Vælg en indstilling, og klik derefter på **Opdater** for at anvende filteret (opdater ikke browservinduet).

   :::image type="content" source="../../media/exploreremailmalwaredetectiontech2-new.png" alt-text="valgt registreringsteknologi" lightbox="../../media/exploreremailmalwaredetectiontech2-new.png":::

   Rapporten opdateres for at vise de resultater, som malware registreret i en mail, ved hjælp af den teknologiindstilling, du har valgt. Herfra kan du foretage yderligere analyser.

### <a name="report-a-message-as-clean-in-explorer"></a>Rapportér en meddelelse som ren i Stifinder

Du kan bruge indstillingen **Rapportrengør** i Stifinder til at rapportere en meddelelse som falsk positiv. 

1. I portalen Microsoft 365 Defender skal du gå  til **& samarbejdsstifinder** \> **og derefter** kontrollere, at **Phish** er markeret på rullelisten Vis.

2. Kontrollér, at du er på fanen  Mail, og vælg derefter den, du vil rapportere som rene, på listen over rapporterede meddelelser. 

3. Klik **på Handlinger** for at udvide listen over indstillinger.

4. Rul ned på listen over indstillinger for at gå til **sektionen Start ny** indsendelse, og vælg derefter **Rapportopryd.** Der vises en pop op-meddelelse.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/report-clean-option-explorer.png" alt-text="Indstillingen Rapportrengøring i Stifinder" lightbox="../../media/report-clean-option-explorer.png":::

5. Slå skyderen til **Til**. På rullelisten skal du angive det antal dage, meddelelsen skal fjernes, tilføje en note, hvis det er nødvendigt, og derefter vælge **Send**. 

## <a name="view-phishing-url-and-click-verdict-data"></a>Få vist phishing-URL-adresse, og klik på vurderingsdata

Du kan få vist phishingforsøg via URL-adresser i en mail, herunder en liste over URL-adresser, der blev tilladt, blokeret og tilsidesat. For at identificere URL-adresser, der blev [klikket på, Pengeskab der oprettes](safe-links.md) links. Sørg for, at du [har Pengeskab Links-politikker](set-up-safe-links-policies.md) for klik og logføring af klik Pengeskab Links.

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **& og samarbejde** og derefter vælge **Stifinder****- eller realtidsregistreringer**. For at gå direkte til siden skal du bruge <https://security.microsoft.com/threatexplorer> eller <https://security.microsoft.com/realtimereports>.

   I dette eksempel bruges **Stifinder**.

2. På **rullelisten** Vis skal du vælge **Email** \> **Phish**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerViewEmailPhishMenu.png" alt-text="Menuen Vis for Stifinder i phishing-kontekst" lightbox="../../media/ExplorerViewEmailPhishMenu.png":::

3. Klik **på Afsender**, og vælg derefter **URL-adresser** \> **Klik** på konklusion på rullelisten.

4. I de indstillinger, der vises, skal du vælge en eller flere  indstillinger, f.eks. Blokeret og Blokeret **, og** derefter klikke på **Opdater (opdater** ikke browservinduet).

    :::image type="content" source="../../media/threatexploreremailphishclickverdict-new.png" alt-text="URL-adresserne, og klik på bedømmelser" lightbox="../../media/threatexploreremailphishclickverdict-new.png":::

   Rapporten opdateres, så der vises to forskellige URL-tabeller på **fanen URL-adresser** under rapporten:

   - **Øverste URL-adresser** er URL-adresserne i de meddelelser, du har filtreret ned til, og handlingen til levering af mail tæller for hver URL-adresse. I phish-mailvisningen indeholder denne liste typisk legitime URL-adresser. Hackere har en blanding af gode og dårlige URL-adresser i deres meddelelser for at forsøge at få dem leveret, men de får de ondsindede links til at se mere interessante ud. Tabellen med URL-adresser sorteres efter samlet antal mails, men denne kolonne er skjult for at forenkle visningen.

   - **De mest populære klik** er de Pengeskab URL-adresser, der blev klikket på, sorteret efter samlet antal klik. Denne kolonne vises heller ikke, for at forenkle visningen. Samlet antal pr. kolonne angiver antallet af Pengeskab klik på bedømmelse for hver klikket URL-adresse. I phish-mailvisningen er disse normalt mistænkelige eller skadelige URL-adresser. Men visningen kan indeholde URL-adresser, der ikke er trusler, men som er i phish-meddelelser. Klik på URL-adresse på links, der ikke er blevet åbnet, vises ikke her.

   De to URL-tabeller viser de vigtigste URL-adresser i phishing-mails ved hjælp af leveringshandling og placering. Tabellerne viser URL-klik, der blev blokeret eller besøgt på trods af en advarsel, så du kan se, hvilke potentielt dårlige links der blev vist til brugerne, og som brugerne klikkede på. Herfra kan du foretage yderligere analyser. Eksempelvis kan du under diagrammet se de øverste URL-adresser i mails, der blev blokeret i din organisations miljø.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerPhishClickVerdictURLs.png" alt-text="URL-adresser for Stifinder, der blev blokeret" lightbox="../../media/ExplorerPhishClickVerdictURLs.png":::

   Vælg en URL-adresse for at få vist mere detaljerede oplysninger.

   > [!NOTE]
   > I pop op-dialogboksen URL-adresse fjernes filtreringen af mails for at vise den fulde visning af URL-adressens eksponering i dit miljø. Det gør det muligt at filtrere efter mails, du er bekymret for i Stifinder, finde bestemte URL-adresser, der kan være trusler, og derefter udvide din forståelse af URL-eksponeringen i dit miljø (via dialogboksen med URL-oplysninger) uden at skulle føje URL-filtre til stifindervisningen.

### <a name="interpretation-of-click-verdicts"></a>Fortolkning af klikfortolkninger

I pop op-menuen Mail eller URL-adresse, Øverste klik og i vores filtreringsoplevelser får du vist forskellige klikkriterieværdier:

- **Ingen:** Det er ikke muligt at registrere konklusionen for URL-adressen. Brugeren har muligvis klikket gennem URL-adressen.
- **Tilladt:** Brugeren har fået tilladelse til at gå til URL-adressen.
- **Blokeret:** Brugeren blev blokeret fra at navigere til URL-adressen.
- **Afventende konklusion:** Brugeren fik vist den detonation-afventende side.
- **Blokeret tilsidesættet:** Brugeren blev blokeret fra at navigere direkte til URL-adressen. Men brugeren overrokerer blokken for at gå til URL-adressen.
- **Afventende konklusion er omgået:** Brugeren fik vist detonationssiden. Men brugeren overroker meddelelsen for at få adgang til URL-adressen.
- **Fejl:** Brugeren fik vist fejlsiden, eller der opstod en fejl ved registrering af konklusionen.
- **Fejl:** Der opstod en ukendt undtagelse, mens konklusionen blev registreret. Brugeren har muligvis klikket gennem URL-adressen.

## <a name="start-automated-investigation-and-response"></a>Start automatiseret undersøgelse og svar

> [!NOTE]
> Automatiserede undersøgelses- og svarmuligheder er tilgængelige *Microsoft Defender for Office 365 Plan 2* *og Office 365 E5*.

[Automatiseret undersøgelse og svar](automated-investigation-response-office.md) kan spare tid og besvær for sikkerhedsteamet, når det bruges på at undersøge og mindske cyberangreb. Ud over at konfigurere beskeder, der kan udløse en sikkerhedsspilbog, kan du starte en automatisk undersøgelses- og svarproces fra en visning i Stifinder. Du kan finde flere [oplysninger i Eksempel: En sikkerhedsadministrator udløser en undersøgelse fra Stifinder](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).

## <a name="other-articles"></a>Andre artikler

[Undersøg mails med siden Mailenhed](mdo-email-entity-page.md)
