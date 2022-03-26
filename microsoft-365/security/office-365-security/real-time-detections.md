---
title: Grundlæggende om registreringer af Threat Explorer og realtid i Microsoft Defender Office 365
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
description: Brug Explorer eller registreringer i realtid til at undersøge og reagere effektivt på trusler.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3b889649de7b56d6a1b5300ff323850a4e555b57
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775356"
---
# <a name="explorer-and-real-time-detections"></a>Registreringer i Stifinder og i realtid

**Gælder for**
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I denne artikel:

- [Forskelle mellem Explorer- og realtidsregistreringer](#differences-between-explorer-and-real-time-detections)
- [Opdateret oplevelse for registreringer i Stifinder og i realtid](#updated-experience-for-explorer-and-real-time-detections)
- [Påkrævede licenser og tilladelser](#required-licenses-and-permissions)

> [!NOTE]
> Dette er en del af en **3-artikelserie** om **Stifinder (også kaldet Threat Explorer),** mailsikkerhed og grundlæggende registreringer i **Stifinder** og registreringer i realtid (f.eks. forskelle mellem værktøjerne og de tilladelser, der kræves for at kunne anvende dem). De andre to artikler i denne serie er [Trusselssøgning i Stifinder](threat-hunting-in-threat-explorer.md) og [Mailsikkerhed med Explorer](email-security-in-microsoft-defender.md).

I denne artikel beskrives forskellen mellem registreringer i Stifinder og registreringer i realtid, den opdaterede oplevelse med Stifinder og registreringer i realtid, hvor du kan skifte mellem gamle og nye oplevelser samt de licenser og tilladelser, der kræves.

Hvis din organisation har [Microsoft Defender til Office 365](defender-for-office-365.md), og du har tilladelserne [, kan](#required-licenses-and-permissions) du bruge **Stifinder** (også kaldet **Threat Explorer**) eller registreringer i  realtid til at registrere og afhjælpe trusler.

I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **& og samarbejde** og derefter vælge **Stifinder**  **- eller realtidsregistreringer**. For at gå direkte til siden skal du bruge <https://security.microsoft.com/threatexplorer> eller <https://security.microsoft.com/realtimereports>.

Med disse værktøjer kan du:

- Se malware, der registreres Microsoft 365 af sikkerhedsfunktionerne.
- Få vist phishing-URL-adresse, og klik på vurderingsdata.
- Start en automatisk undersøgelses- og svarproces fra en visning i Stifinder.
- Undersøg ondsindede mails og meget mere.

Du kan få mere at vide [under Mailsikkerhed med Stifinder](email-security-in-microsoft-defender.md).

## <a name="differences-between-explorer-and-real-time-detections"></a>Forskelle mellem Explorer- og realtidsregistreringer

- *Registreringer i realtid er et rapporteringsværktøj*, der er tilgængeligt i Defender Office 365 Plan 1. *Threat Explorer* er et trussels- og afhjælpningsværktøj, der er tilgængeligt i Defender Office 365 Plan 2.
- Registreringer i realtid gør det muligt at få vist registreringer i realtid. Threat Explorer gør det også, men det indeholder flere oplysninger om et givent angreb, f.eks. fremhævning af angrebskampagner, og giver sikkerhedsteams mulighed for at løse trusler (herunder udløse en automatisk undersøgelse og [svarundersøgelse](automated-investigation-response-office.md).
- En *alle mailvisning* er tilgængelig i Threat Explorer, men den er ikke medtaget i rapporten registreringer i realtid.
- Omfattende filtreringsfunktioner og afhjælpningshandlinger er inkluderet i Threat Explorer. Få mere at vide under [Beskrivelse af Microsoft Defender Office 365: Tilgængelighed af funktioner på tværs af Defender Office 365-planer](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

## <a name="updated-experience-for-explorer-and-real-time-detections"></a>Opdateret oplevelse for registreringer i Stifinder og i realtid

Oplevelsen af registreringer af Threat Explorer og realtid er opdateret til at være i overensstemmelse med moderne tilgængelighedsstandarder og for at optimere arbejdsprocessen. I kort tid kan du skifte mellem den gamle og den nye oplevelse.  

> [!NOTE]
> Når du slår det fra, påvirker det kun din konto og påvirker ikke andre personer i din lejer. 

Registreringer af Trusselsstifinder og Realtid er opdelt i følgende visninger:

- *Alle mails*: Viser alle mails, der er analyseret af Defender til Office 365 og indeholder både gode og skadelige mails. Denne funktion findes kun i Threat Explorer og er ikke tilgængelig til registreringer i realtid. Som standard er den indstillet til at vise data for to dage, som kan udvides op til 30 dage. Dette er også standardvisningen for Threat Explorer.  

- *Malwarevisning*: Viser mails, hvor der blev identificeret en malwaretrussel. Dette er standardvisningen for registreringer i realtid og viser data for to dage (kan udvides til 30 dage).  

- *Phish-visning*: Viser mails, hvor en phish-trussel blev identificeret.

- *Visning af indholdsmalware*: Viser skadelige registreringer, der er identificeret i filer, der deles OneDrive, SharePoint eller Teams. 

Her er de mest almindelige komponenter i disse oplevelser:

- Filtre

    - Du kan bruge de forskellige filtre til at få vist data baseret på mail- eller filattributter.  

    - Som standard anvendes tidsfilteret på posterne og anvendes i to dage.  

    - Hvis du anvender flere filtre, anvendes de i 'OG'-tilstand, og du kan bruge det avancerede filter til at ændre det til 'ELLER'-tilstand.  

    - Du kan bruge kommaer til at tilføje flere værdier for det samme filter.  

    > [!div class="mx-imgBorder"]
    > ![Stifinderfiltre](../../media/explorer-new-experience-filters.png)

- Diagrammer

    - Diagrammer giver en visuel, samlet visning af data baseret på filtre. Du kan bruge forskellige filtre til at få vist data efter forskellige dimensioner.  

    > [!NOTE]
    > Du får muligvis ikke vist nogen resultater i diagramvisningen, selvom du får vist en post i listevisningen. Dette sker, hvis filteret ikke frembringer nogen data. Hvis du f.eks. har anvendt filtermalwarefamilien, men de underliggende data ikke har nogen ondsindede mails, vil du muligvis se meddelelsen ingen tilgængelige data for dette scenarie.  

    > [!div class="mx-imgBorder"]
    > ![Stifinderdiagramvisning](../../media/explorer-new-experience-export-chart-data.png)

- Resultatgitter  

    - Resultatgitteret viser mailresultaterne baseret på de filtre, du har anvendt.  

    - Baseret på konfigurationssættet i din lejer vises data i UTC eller lokal tidszone med de tilgængelige tidszoneoplysninger i den første kolonne.  

    - Du kan navigere til den enkelte mailenhedsside fra listevisningen ved at klikke på **ikonet Åbn i nyt** vindue. 

    - Du kan også tilpasse dine kolonner for at tilføje eller fjerne kolonner for at optimere din visning.

    > [!Note]
    > Du kan skifte mellem *Diagramvisning og* Listevisning *for* at maksimere resultatsættet.  

    > [!div class="mx-imgBorder"]
    > ![Gittervisning i Stifinder](../../media/explorer-new-experience-list-chart-view.png)

- Detaljeret pop op-out  

    - Du kan klikke på links for at få adgang til mailoversigtspanelet (poster i kolonnen Emne), modtageren eller pop op-menuen IP.  

    - Panelet til mailoversigt erstatter den ældre mail-pop op-mail og indeholder også en sti til at få adgang til mailenhedspanelet.  

    - Pop op-eksempler på individuelle enheder som IP, modtager og URL afspejler de samme oplysninger, men præsenteres i en enkelt fanebaseret visning med mulighed for at udvide og skjule de forskellige sektioner baseret på krav.  

    - For pop op-sider som URL-adresser kan du  klikke på Vis alle  mails eller Vis alle klik for at få vist det komplette sæt mails/klik, der indeholder den pågældende URL-adresse, samt eksportere resultatsættet.  

- Handlinger

    - Fra Threat Explorer kan du udløse afhjælpningshandlinger som *f.eks. Slet en mail*. Du kan finde flere oplysninger om afhjælpning, afhjælpningsbegrænsninger og sporing af afhjælpning i [Afhjulpet ondsindet mail](remediate-malicious-email-delivered-office-365.md).  

- eksportér

    - Du kan klikke på **Eksportér diagramdata** for at eksportere diagramdetaljerne. På samme måde skal du **klikke på Eksportér mailliste** for at eksportere mailoplysninger.

    - Du kan eksportere op til 200.000 poster til mailliste. For bedre systemydeevne og reduceret downloadtid skal du dog bruge forskellige mailfiltre.

    > [!div class="mx-imgBorder"]
    > ![Eksportér diagramdata](../../media/explorer-new-experience-export-chart-data.png)

Ud over disse funktioner får du også opdaterede oplevelser som f.eks. Top *URL-adresser*, *Øverste klik*, *Mest målrettede* brugere og *Mailindrindelse*. *De mest populære* *URL-adresser, Øverste klik* og *Mest målrettede* brugere kan filtreres yderligere baseret på det filter, du anvender i Stifinder. 

## <a name="required-licenses-and-permissions"></a>Påkrævede licenser og tilladelser

Du skal have [Microsoft Defender, Office 365](defender-for-office-365.md) du kan bruge en af registreringerne i Explorer eller realtid:

- Explorer er kun inkluderet i Defender Office 365 Plan 2.
- Registreringer af realtid er inkluderet i Defender for Office 365 Plan 1.

Sikkerhedsteams skal tildele licenser til alle brugere, der skal være beskyttet af Defender til Office 365, og vær opmærksom på, at Explorer- og realtidsregistreringer viser registreringsdata for licenserede brugere.

Hvis du vil have vist *og bruge* Registreringer i Stifinder eller i realtid, skal du have følgende tilladelser:

- I Defender til Office 365:
  - Organisationsadministration
  - Sikkerhedsadministrator (kan tildeles i Azure Active Directory Administration (<https://aad.portal.azure.com>)
  - Sikkerhedslæser
- I Exchange Online:
  - Organisationsadministration
  - View-Only organisationsadministration
  - View-Only modtagere
  - Styring af overholdelse

Du kan få mere at vide om roller og tilladelser i følgende artikler:

- [Tilladelser i Microsoft 365 Defender portalen](permissions-microsoft-365-security-center.md)
- [Tilladelser i Exchange Online](/e/exchange/permissions-exo/permissions-exo)

## <a name="more-information"></a>Flere oplysninger

- [Threat Explorer indsamler mailoplysninger på siden mailenhed](mdo-email-entity-page.md)
- [Find og undersøg skadelige mails, der blev leveret](investigate-malicious-email-that-was-delivered.md)
- [Få vist skadelige filer, der er registreret SharePoint Online, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [Statusrapport over trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report)
- [Automatiseret undersøgelse og svar i Microsoft Threat Protection](automated-investigation-response-office.md)
