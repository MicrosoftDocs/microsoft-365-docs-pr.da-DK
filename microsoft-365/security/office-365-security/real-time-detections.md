---
title: Grundlæggende registreringer af Threat Explorer og realtidsregistreringer i Microsoft Defender for Office 365
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
description: Brug Stifinder- eller realtidsregistreringer til at undersøge og reagere effektivt på trusler.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e7f3109048f3a4931d25029df3db9a3c217d6354
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647419"
---
# <a name="explorer-and-real-time-detections"></a>Explorer- og realtidsregistreringer

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I denne artikel:

- [Forskelle mellem stifinder- og realtidsregistreringer](#differences-between-explorer-and-real-time-detections)
- [Opdateret oplevelse for stifinder- og realtidsregistreringer](#updated-experience-for-explorer-and-real-time-detections)
- [Påkrævede licenser og tilladelser](#required-licenses-and-permissions)

> [!NOTE]
> Dette er en del af en **serie med tre artikler** om **Explorer (også kendt som Threat Explorer),** **grundlæggende oplysninger om mailsikkerhed** og **registreringer i realtid** (f.eks. forskelle mellem de værktøjer og tilladelser, der er nødvendige for at betjene dem). De to andre artikler i denne serie er [Trusselsjagt i Explorer](threat-hunting-in-threat-explorer.md) og [Mailsikkerhed med Explorer](email-security-in-microsoft-defender.md).

I denne artikel forklares forskellen mellem rapportering af registreringer i Stifinder og realtid, opdateret oplevelse med Stifinder og registreringer i realtid, hvor du kan skifte mellem gamle og nye oplevelser og de licenser og tilladelser, der kræves.

Hvis din organisation har [Microsoft Defender for Office 365](defender-for-office-365.md), og du har [tilladelserne](#required-licenses-and-permissions), kan du bruge **Stifinder** (også kendt som **Threat Explorer**) eller **registreringer i realtid** til at registrere og afhjælpe trusler.

I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & samarbejde** og derefter vælge **Stifinder** _eller_ **Registreringer i realtid**. Hvis du vil gå direkte til siden, skal du bruge <https://security.microsoft.com/threatexplorer> eller <https://security.microsoft.com/realtimereports>.

Med disse værktøjer kan du:

- Se malware, der er registreret af Microsoft 365 sikkerhedsfunktioner.
- Vis phishing-URL-adresse, og klik på data for dom.
- Start en automatisk undersøgelses- og svarproces fra en visning i Stifinder.
- Undersøg ondsindet mail m.m.

Du kan få flere oplysninger under [Mailsikkerhed med Stifinder](email-security-in-microsoft-defender.md).

## <a name="differences-between-explorer-and-real-time-detections"></a>Forskelle mellem stifinder- og realtidsregistreringer

- *Registreringer i realtid* er et rapporteringsværktøj, der er tilgængeligt i Defender for Office 365 Plan 1. *Threat Explorer* er et trussels jagt- og afhjælpningsværktøj, der er tilgængeligt i Defender for Office 365 Plan 2.
- Rapporten Registreringer i realtid giver dig mulighed for at få vist registreringer i realtid. Threat Explorer gør det også, men det giver yderligere oplysninger om et givent angreb, f.eks. fremhævning af angrebskampagner, og giver sikkerhedsteams mulighed for at afhjælpe trusler (herunder udløse en [automatiseret undersøgelse og svarundersøgelse](automated-investigation-response-office.md).
- En *alle-mailvisning* er tilgængelig i Threat Explorer, men er ikke inkluderet i rapporten Registreringer i realtid.
- Omfattende filtreringsfunktioner og afhjælpningshandlinger er inkluderet i Threat Explorer. Du kan få flere oplysninger [under Microsoft Defender for Office 365 Servicebeskrivelse: Funktionstilgængelighed på tværs af Defender for Office 365 planer](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

## <a name="updated-experience-for-explorer-and-real-time-detections"></a>Opdateret oplevelse for stifinder- og realtidsregistreringer

Oplevelsen for trusselsstifinder- og realtidsregistreringer opdateres for at justere med moderne standarder for tilgængelighed og for at optimere arbejdsprocessen. I et kort stykke tid vil du være i stand til at skifte mellem den gamle oplevelse og den nye.  

> [!NOTE]
> Hvis du skifter til/fra, påvirker det kun din konto og påvirker ikke andre i din lejer. 

Trusselsoversigt og realtidsregistreringer er opdelt i følgende visninger:

- *Alle mails*: Viser alle mails, der er analyseret af Defender til Office 365, og indeholder både gode og skadelige mails. Denne funktion findes kun i Threat Explorer og er ikke tilgængelig for registreringer i realtid. Som standard er den indstillet til at vise data for to dage, hvilket kan udvides til 30 dage. Dette er også standardvisningen for Threat Explorer.  

- *Visning af malware*: Viser mails, hvor der blev identificeret en malwaretrussel. Dette er standardvisningen for registreringer i realtid og viser data for to dage (kan udvides til 30 dage).  

- *Phish-visning*: Viser mails, hvor der blev identificeret en phish-trussel.

- *Visning af indholdsmalware*: Viser skadelige registreringer, der er identificeret i filer, som deles via OneDrive, SharePoint eller Teams. 

Her er de almindelige komponenter i disse oplevelser:

- Filtre

    - Du kan bruge de forskellige filtre til at få vist dataene baseret på mail- eller filattributter.  

    - Klokkeslætsfilteret anvendes som standard på posterne og anvendes i to dage.  

    - Hvis du anvender flere filtre, anvendes de i tilstanden 'AND', og du kan bruge det avancerede filter til at ændre det til 'OR'-tilstand.  

    - Du kan bruge kommaer til at tilføje flere værdier for det samme filter.  

    > [!div class="mx-imgBorder"]
    > ![Explorer-filtre](../../media/explorer-new-experience-filters.png)

- Diagrammer

    - Diagrammer giver en visuel, samlet visning af data baseret på filtre. Du kan bruge forskellige filtre til at få vist dataene efter forskellige dimensioner.  

    > [!NOTE]
    > Du kan muligvis ikke se nogen resultater i diagramvisning, selvom du får vist en post i listevisningen. Dette sker, hvis filteret ikke producerer nogen data. Hvis du f.eks. har anvendt filtermalwarefamilien, men de underliggende data ikke har nogen skadelige mails, kan du muligvis se meddelelsen ingen tilgængelige data for dette scenarie.  

    > [!div class="mx-imgBorder"]
    > ![Diagramvisning i Stifinder](../../media/explorer-new-experience-export-chart-data.png)

- Resultatgitter  

    - Resultatgitteret viser mailresultaterne baseret på de filtre, du har anvendt.  

    - Baseret på den konfiguration, der er angivet i din lejer, vises data i UTC eller lokal tidszone, hvor tidszoneoplysningerne er tilgængelige i den første kolonne.  

    - Du kan navigere til den enkelte mailenhedsside fra listevisningen ved at klikke på ikonet **Åbn i nyt vindue** . 

    - Du kan også tilpasse dine kolonner for at tilføje eller fjerne kolonner for at optimere visningen.

    > [!Note]
    > Du kan skifte mellem *Diagramvisning* og *Listevisning* for at maksimere dit resultatsæt.  

    > [!div class="mx-imgBorder"]
    > ![Stifindergittervisning](../../media/explorer-new-experience-list-chart-view.png)

- Detaljeret pop op-vindue  

    - Du kan klikke på links for at få vist panelet med mailoversigten (poster i emnekolonnen), modtageren eller IP-pop op-vinduet.  

    - Panelet mailoversigt erstatter det ældre mail-pop op-vindue og giver også en sti til at få adgang til mailobjektpanelet.  

    - Pop op-vinduet for de enkelte objekter, f.eks. IP, modtager og URL-adresse, afspejler de samme oplysninger, men vises i en enkelt fanebaseret visning med mulighed for at udvide og skjule de forskellige sektioner baseret på krav.  

    - I forbindelse med pop op-adresser som URL-adresser kan du klikke på **Vis alle mails** eller **Få vist alle klik** for at få vist det fulde sæt mails/klik, der indeholder den pågældende URL-adresse, samt eksportere resultatsættet.  

- Handlinger

    - Fra Threat Explorer kan du udløse afhjælpningshandlinger, f.eks *. Slet en mail*. Du kan finde flere oplysninger om afhjælpning, afhjælpningsgrænser og sporing af afhjælpning under [Afhjælpning af skadelig mail](remediate-malicious-email-delivered-office-365.md).  

- eksportér

    - Du kan klikke på **Eksportér diagramdata** for at eksportere diagramdetaljerne. På samme måde skal du klikke på **Eksportér mailliste** for at eksportere mailoplysninger.

    - Du kan eksportere op til 200.000 poster for maillisten. Men for at opnå bedre ydeevne og reduceret downloadtid skal du bruge forskellige mailfiltre.

    > [!div class="mx-imgBorder"]
    > ![Eksportér diagramdata](../../media/explorer-new-experience-export-chart-data.png)

Ud over disse funktioner får du også opdaterede oplevelser som *Top URL-adresser*, *Top clicks*, *Top målrettede brugere* og *Mail oprindelse*. *De mest populære URL-adresser*, *de mest populære klik* og *de mest målrettede brugere* kan filtreres yderligere baseret på det filter, du anvender i Stifinder. 

## <a name="required-licenses-and-permissions"></a>Påkrævede licenser og tilladelser

Du skal have [Microsoft Defender for Office 365](defender-for-office-365.md) til at bruge enten Stifinder- eller Realtidsregistreringer:

- Explorer er kun inkluderet i Defender for Office 365 Plan 2.
- Rapporten med registreringer i realtid er inkluderet i Defender for Office 365 Plan 1.

Sikkerhedsteams skal tildele licenser til alle brugere, der skal beskyttes af Defender for Office 365 og være opmærksomme på, at registreringer i Stifinder og realtid viser registreringsdata for brugere med licens.

Hvis du vil have vist og bruge registreringer i Stifinder *eller* realtid, skal du have følgende tilladelser:

- I Defender for Office 365:
  - Organisationsadministration
  - Sikkerhedsadministrator (dette kan tildeles i Azure Active Directory Administration (<https://aad.portal.azure.com>)
  - Sikkerhedslæser
- I Exchange Online:
  - Organisationsadministration
  - View-Only organisationsstyring
  - View-Only modtagere
  - Overholdelsesstyring

Du kan få mere at vide om roller og tilladelser i følgende artikler:

- [Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md)
- [Tilladelser i Exchange Online](/e/exchange/permissions-exo/permissions-exo)

## <a name="more-information"></a>Flere oplysninger

- [Threat Explorer indsamler mailoplysninger på mailenhedssiden](mdo-email-entity-page.md)
- [Find og undersøg ondsindet mail, der blev leveret](investigate-malicious-email-that-was-delivered.md)
- [Vis skadelige filer, der er registreret i SharePoint Online, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [Statusrapport om trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report)
- [Automatiseret undersøgelse og svar i Microsoft Threat Protection](automated-investigation-response-office.md)
