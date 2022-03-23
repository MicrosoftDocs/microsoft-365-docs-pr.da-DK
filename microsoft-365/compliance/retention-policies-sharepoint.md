---
title: Få mere at vide om opbevaring SharePoint og OneDrive
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan opbevaring fungerer SharePoint og OneDrive.
ms.openlocfilehash: a553945fdb0b0034d8f3182164749b06badfe503
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/03/2022
ms.locfileid: "63590891"
---
# <a name="learn-about-retention-for-sharepoint-and-onedrive"></a>Få mere at vide om opbevaring SharePoint og OneDrive

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Oplysningerne i denne artikel tillæg Få [mere at vide om opbevaring](retention.md), fordi de indeholder oplysninger, der er specifikke for SharePoint og OneDrive.

For andre arbejdsbelastninger skal du se:

- [Få mere at vide om opbevaring af Microsoft Teams](retention-policies-teams.md)
- [Få mere at vide om opbevaring af Yammer](retention-policies-yammer.md)
- [Få mere at vide om opbevaring af Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Hvad er inkluderet i opbevaring og sletning

Alle filer, der er SharePoint eller OneDrive websteder, kan bevares ved at anvende en opbevaringspolitik eller en opbevaringsmærkat. 

Følgende filer kan slettes:

- Når du bruger en opbevaringspolitik: Alle filer i dokumentbiblioteker, som omfatter de automatisk oprettede SharePoint, f.eks. **Webstedsaktiver**.
    
- Når du bruger opbevaringsnavne: Alle filer i alle dokumentbiblioteker og alle filer på rodniveau, der ikke er i en mappe.
    
> [!TIP]
> Når du bruger en [forespørgsel med en automatisk anvendelsespolitik for](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-keywords-or-searchable-properties) en opbevaringsetiket, kan du udelade bestemte dokumentbiblioteker ved hjælp af følgende element: `NOT(DocumentLink:"<URL to document library>")`

Listeelementer understøttes ikke af opbevaringspolitikker, men understøttes af opbevaringsetiketter med undtagelse af elementer på systemlister. Disse er skjulte lister, SharePoint bruges til at administrere systemet og medtage hovedsidekataloget, løsningskataloget og datakilderne. Når opbevaringsetiketter anvendes på understøttede listeelementer, bevares de altid i overensstemmelse med opbevaringsindstillingerne, men slettes ikke, hvis de er skjult fra søgning.

Når du anvender et opbevaringsnavn på et understøttet listeelement, der har en vedhæftet fil:
- For en standardopbevaringsetiket (erklærer ikke elementet som en post):
    - Den vedhæftede fil arver ikke automatisk opbevaringsindstillingerne for etiketten, men kan navnes uafhængigt af hinanden.
- For en opbevaringsetiket, der erklærer elementet som en post: 
    - Den vedhæftede fil arver automatisk opbevaringsindstillingerne fra etiketten, hvis dokumentet ikke allerede er mærket.

Opbevaringsindstillinger fra både opbevaringspolitikker og opbevaringsnavne gælder ikke for organisering af strukturer, der omfatter biblioteker, lister og mapper.

I forbindelse med opbevaringspolitikker og politikker for automatisk anvendelse af navne: SharePoint websteder skal indekseres, for at opbevaringsindstillingerne kan anvendes. Men hvis elementer i SharePoint-dokumentbiblioteker er konfigureret til ikke at blive vist i søgeresultater, udelukker denne konfiguration ikke filer fra opbevaringsindstillingerne.


## <a name="how-retention-works-for-sharepoint-and-onedrive"></a>Sådan fungerer opbevaring til SharePoint og OneDrive

Hvis du vil gemme indhold, der skal bevares, SharePoint og OneDrive du oprette et bibliotek til opbevaring af dokumenter, hvis der ikke findes et for webstedet. Biblioteket til opbevaring af dokumenter er ikke designet til at blive brugt interaktivt, men gemmer i stedet automatisk filer, når det er nødvendigt af hensyn til overholdelse af regler og standarder. Det fungerer på følgende måde:

Når en bruger ændrer eller sletter et element, der er underlagt opbevaring, kontrolleres det, om indholdet er blevet ændret, siden opbevaringsindstillingerne blev anvendt. Hvis dette er den første ændring, siden opbevaringsindstillingerne blev anvendt, kopieres indholdet til biblioteket til opbevaring af dokumenter, så brugeren kan ændre eller slette det oprindelige indhold.

Et timerjob kører med jævne mellemrum på biblioteket til opbevaring af dokumenter. For indhold, der har været i biblioteket til opbevaring af indhold i mere end 30 dage, sammenligner dette job indholdet med alle forespørgsler, der bruges af opbevaringsindstillingerne for det pågældende indhold. Indhold, der er ældre end den konfigurerede opbevaringsperiode, slettes derefter fra biblioteket til opbevaring af dokumenter og fra den oprindelige placering, hvis det stadig er der. Dette timerjob kører hver syv dage, hvilket betyder, at det sammen med de minimale 30 dage kan tage op til 37 dage, før indhold slettes fra biblioteket til opbevaring af dokumenter.

Denne funktionsmåde ved kopiering af filer til biblioteket til opbevaring af dokumenter gælder for indhold, der findes, da opbevaringsindstillingerne blev anvendt. Desuden bevares nyt indhold, der er oprettet eller føjet til webstedet, efter det blev inkluderet i politikken, i biblioteket til opbevaring af dokumenter for opbevaringspolitikker. Men nyt indhold kopieres ikke til biblioteket til opbevaring af dokumenter første gang, det redigeres, men kun når det slettes. Hvis du vil bevare alle versioner af en [fil, skal](#how-retention-works-with-document-versions) versionsdeling være slået til for det oprindelige websted.
  
Brugerne får vist en fejlmeddelelse, hvis de forsøger at slette et bibliotek, en liste, en mappe eller et websted, der er underlagt opbevaring. De kan slette en mappe, hvis de først flytter eller sletter filer i mappen, der er underlagt opbevaring.

Brugerne får også vist en fejlmeddelelse, hvis de forsøger at slette et mærket element i en af følgende tilfælde. Elementet kopieres ikke til biblioteket til opbevaring af dokumenter, men forbliver på den oprindelige placering:

- Indstillingen til administration af poster, der giver brugerne mulighed for at slette mærkede elementer, er slået fra.
    
    Hvis du vil kontrollere eller ændre denne indstilling, skal  du gå til løsningen Datastyring i Microsoft 365 Overholdelsescenter > >  >  >  Indstillinger for administration af posterPosterSkift navneSlettelse **af elementer**. Der er separate indstillinger for SharePoint og OneDrive.
    
    Alternativt, og hvis du ikke har adgang til løsningen **Datastyring** , kan du bruge *AllowFilesWithKeepLabelToBeDeletedSPO* og *AllowFilesWithKeepLabelToBeDeletedODB* fra [Get-PnPTenant](/powershell/module/sharepoint-pnp/get-pnptenant) og [Set-PnPTenant](/powershell/module/sharepoint-pnp/set-pnptenant).

- Opbevaringsnavnet markerer elementer som en post, og den er [låst](record-versioning.md).
    
    Kun når posten er låst op, gemmes en kopi af den seneste version i biblioteket til opbevaring af dokumenter.

- Opbevaringsetiketten markerer elementer [som en](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked) lovgivningsmæssig post, som altid forhindrer elementet i at blive redigeret eller slettet.

Når opbevaringsindstillinger er tildelt til indhold på en OneDrive-konto eller på et SharePoint-websted, afhænger stierne, som indholdet tager, af, om opbevaringsindstillingerne skal bevares og slettes, kun beholdes eller slettes.

Når opbevaringsindstillingerne skal bevares og slettes:

![Diagram over indholdslivscyklus i SharePoint og OneDrive.](../media/Retention_Diagram_of_retention_flow_in_sites.png)
  
1. **Hvis indholdet** ændres eller slettes i løbet af opbevaringsperioden, oprettes der en kopi af det oprindelige indhold, som det fandtes, da opbevaringsindstillingerne blev tildelt, i biblioteket til opbevaring af dokumenter. Her identificerer timerjobbet elementer, hvis opbevaringsperiode er udløbet. Disse elementer flyttes til Papirkurv for andet trin, hvor de slettes permanent i slutningen af 93 dage. Papirkurv på andet trin er ikke synlig for slutbrugerne (kun papirkurv på første trin er), men administratorer af grupper af websteder kan få vist og gendanne indhold derfra.

    > [!NOTE]
    > For at forhindre utilsigtet datatab sletter vi ikke længere indhold fra biblioteket til opbevaring af data permanent. I stedet sletter vi kun indhold permanent fra Papirkurv, så alt indhold fra biblioteket til opbevaring af dokumenter nu går gennem papirkurven på andet trin.
    
2. **Hvis indholdet ikke ændres** eller slettes under opbevaringsperioden, flytter timerjobbet dette indhold til Papirkurv i første trin i slutningen af en opbevaringsperiode. Hvis en bruger sletter indholdet derfra eller tømmer denne Papirkurv (også kaldet sletning), flyttes dokumentet til Papirkurv for andet trin. En opbevaringsperiode på 93 dage strækker sig over papirkurve på første og andet trin. Ved slutningen af 93 dage slettes dokumentet permanent, uanset hvor det befinder sig, i papirkurven for enten første trin eller andet trin. Papirkurven er ikke indekseret og kan derfor ikke vælges til søgning. Derfor kan en eDiscovery-søgning ikke finde indhold fra papirkurven, hvor der skal anbringes en venteposition.

> [!NOTE]
> På grund af det første princip for opbevaring er permanent sletning altid suspenderet [, hvis](retention.md#the-principles-of-retention-or-what-takes-precedence) det samme element skal bevares på grund af en anden opbevaringspolitik eller opbevaringsmærkat, eller det er under eDiscovery-fasthold af juridiske eller lovmæssige årsager.

Når opbevaringsindstillingerne kun bevares eller slettes, er der variationer af bevarings- og sletningsstier for indholdsstier:

### <a name="content-paths-for-retain-only-retention-settings"></a>Indholdsstier til opbevaringsindstillinger, der kun kan bevares

1.  Hvis indholdet ændres eller slettes under opbevaringsperioden: En kopi af det oprindelige dokument oprettes i biblioteket til opbevaring af dokumenter og bevares indtil slutningen af opbevaringsperioden, når kopien i biblioteket til opbevaring af dokumenter flyttes til Papirkurv for andet trin og slettes permanent efter 93 dage.

2. **Hvis indholdet ikke ændres eller slettes under en opbevaringsperiode** : Der sker intet før og efter opbevaringsperioden; forbliver dokumentet på dets oprindelige placering.

### <a name="content-paths-for-delete-only-retention-settings"></a>Indholdsstier til opbevaringsindstillinger kun for slette

1. **Hvis indholdet slettes i løbet af** den konfigurerede periode: Dokumentet flyttes til Papirkurv på første trin. Hvis en bruger sletter dokumentet derfra eller tømmer denne Papirkurv, flyttes dokumentet til Papirkurv for andet trin. En opbevaringsperiode på 93 dage strækker sig over papirkurve på første trin og andet trin. Ved slutningen af 93 dage slettes dokumentet permanent, uanset hvor det befinder sig, i papirkurven for enten første trin eller andet trin. Hvis indholdet ændres i løbet af den konfigurerede periode, følger det den samme sletningssti efter den konfigurerede periode.

2. **Hvis indholdet** ikke slettes i løbet af den konfigurerede periode: Ved slutningen af den konfigurerede periode i opbevaringspolitikken flyttes dokumentet til Papirkurv i første trin. Hvis en bruger sletter dokumentet derfra eller tømmer denne Papirkurv (også kaldet sletning), flyttes dokumentet til Papirkurv for andet trin. En opbevaringsperiode på 93 dage strækker sig over papirkurve på første trin og andet trin. Ved slutningen af 93 dage slettes dokumentet permanent, uanset hvor det befinder sig, i papirkurven for enten første trin eller andet trin. Papirkurven er ikke indekseret og kan derfor ikke vælges til søgning. Derfor kan en eDiscovery-søgning ikke finde indhold fra papirkurven, hvor der skal anbringes en venteposition.

## <a name="how-retention-works-with-cloud-attachments"></a>Sådan fungerer opbevaring med vedhæftede filer i skyen

Vedhæftede skybaserede filer er integrerede links til filer, som brugere deler, og disse kan bevares og slettes, når dine brugere deler dem i Outlook og Teams meddelelser. Når du automatisk anvender et [opbevaringsnavn](apply-retention-labels-automatically.md#auto-apply-labels-to-cloud-attachments) på vedhæftede filer i skyen, anvendes opbevaringsmærkaten på en kopi af den delte fil, der er gemt i biblioteket til opbevaring af dokumenter.

I dette scenarie anbefaler vi, at du konfigurerer etiketindstillingen til at starte opbevaringsperioden baseret på, hvornår elementet er mærket. Hvis du konfigurerer opbevaringsperioden baseret på, hvornår elementet oprettes eller senest ændres, tages denne dato fra den oprindelige fil på delingstidspunktet. Hvis du konfigurerer starten af opbevaringen til at være på det tidspunkt, hvor det sidst er ændret, har denne indstilling ingen indflydelse på denne kopi i biblioteket til opbevaring af dokumenter.

Men hvis den oprindelige fil ændres og derefter deles igen, gemmes en ny kopi af filen som en ny version og navnmærkes i biblioteket til opbevaring af dokumenter.

Hvis den oprindelige fil deles igen, men ikke ændres, opdateres datoen for kopien i biblioteket til opbevaring af dokumenter. Denne handling nulstiller starten af en opbevaringsperiode, og vi anbefaler, at du konfigurerer starten af en opbevaringsperiode til at være baseret på, hvornår elementet er mærket.

Da opbevaringsetiketten ikke er anvendt på den oprindelige fil, ændres eller slettes den aldrig af en bruger. Den mærkede fil forbliver i biblioteket til opbevaring af dokumenter, indtil timerjobbet identificerer, at opbevaringsperioden er udløbet. Hvis opbevaringsindstillingerne er konfigureret til at slette elementer, flyttes filen derefter til Papirkurv for andet trin, hvor den slettes permanent i slutningen af 93 dage:

![Sådan fungerer opbevaring for vedhæftede filer i skyen, der er SharePoint og OneDrive](../media/retention-diagram-of-retention-flow-cloud-attachments.png)

Den kopi, der er gemt i biblioteket til opbevaring af dokumenter, oprettes typisk inden for en time fra den skybaserede vedhæftede fil, der deles.

## <a name="how-retention-works-with-onenote-content"></a>Sådan fungerer opbevaring med OneNote indhold

Når du anvender en opbevaringspolitik på en placering, der indeholder OneNote-indhold eller et opbevaringsnavn på en OneNote-mappe, er de forskellige OneNote-sider og -sektioner i baggrunden individuelle filer, der nedarver opbevaringsindstillingerne. Det betyder, at hver sektion på en side enkeltvis bevares og slettes i henhold til de opbevaringsindstillinger, du angiver.

Kun sider og sektioner påvirkes af de opbevaringsindstillinger, du angiver. Selvom du f.eks. kan **se en** Ændringsdato for hver enkelt notesbog, bruges denne dato ikke Microsoft 365 opbevaring.

## <a name="how-retention-works-with-document-versions"></a>Sådan fungerer opbevaring med dokumentversioner

Versionsversionering er en funktion til alle dokumentlister og -biblioteker i SharePoint og OneDrive. Versionsversioner bevarer som standard minimum 500 overordnede versioner, selvom du kan øge denne grænse. Du kan få mere at [vide under Aktivér og konfigurer versionsér for](https://support.office.com/article/1555d642-23ee-446a-990a-bcab618c7a37) en liste eller et bibliotek og Hvordan [versionsversioner fungerer for lister og biblioteker](https://support.microsoft.com/office/how-versioning-works-in-lists-and-libraries-0f6cd105-974f-44a4-aadb-43ac5bdfd247).
  
Når et dokument med versioner er underlagt opbevaringsindstillinger for at bevare indholdet, findes versioner, der kopieres til biblioteket til opbevaring af dokumenter, som et separat element. Hvis opbevaringsindstillingerne er konfigureret til at blive slettet ved afslutning af en opbevaringsperiode:

- Hvis opbevaringsperioden er baseret på, hvornår indholdet blev oprettet, har hver version samme udløbsdato som det oprindelige dokument. Det oprindelige dokument og dets versioner udløber alle på samme tid.

- Hvis opbevaringsperioden er baseret på, hvornår indholdet sidst blev ændret, har hver version sin egen udløbsdato, der er baseret på, hvornår det oprindelige dokument blev ændret for at oprette den pågældende version. Det oprindelige dokument og dets versioner udløber uafhængigt af hinanden.

Når opbevaringshandlingen er at slette dokumentet, slettes alle versioner, der ikke er i biblioteket til opbevaring af dokumenter, på samme tid i henhold til den aktuelle version.

For elementer, der er underlagt en opbevaringspolitik (eller et eDiscovery-venteposition), ignoreres versionsbegrænsningerne for dokumentbiblioteket, indtil opbevaringsperioden for dokumentet er nået (eller eDiscovery-ventepositionen frigives). I dette scenarie slettes gamle versioner ikke automatisk, og brugere forhindres i at slette versioner.

Det er ikke tilfældet med opbevaringsetiketter, når indholdet ikke er underlagt en opbevaringspolitik (eller en eDiscovery-venteposition). I stedet bliver versionsbegrænsningerne imødekommet, så ældre versioner automatisk slettes for at give plads til nye versioner, men brugerne er stadig forhindret i at slette versioner.

## <a name="when-a-user-leaves-the-organization"></a>Når en bruger forlader organisationen

**SharePoint**:

Når en bruger forlader organisationen, påvirkes indhold, der er oprettet af den pågældende bruger, ikke, fordi SharePoint betragtes som et samarbejdsmiljø i modsætning til en brugers postkasse eller OneDrive-konto.

**OneDrive**:

Hvis en bruger forlader organisationen, forbliver alle filer, der er underlagt en opbevaringspolitik eller har en opbevaringsetiket, underlagt opbevaringsindstillingerne i hele opbevaringsperioden, der er angivet i politikken eller etiketten. I dette tidsrum fortsætter al delingsadgang med at fungere, og indholdet kan fortsat findes via Indholdssøgning og eDiscovery. 

Når opbevaringsperioden udløber, og opbevaringsindstillingerne inkluderede en sletningshandling, flyttes indhold til papirkurven for gruppen af websteder og er ikke tilgængeligt for andre end administratoren.

## <a name="configuration-guidance"></a>Konfigurationsvejledning

Hvis du er ny bruger af konfiguration af opbevaring i Microsoft 365, skal du se [Introduktion til informationsstyring](get-started-with-information-governance.md).

Hvis du er klar til at konfigurere en opbevaringspolitik eller en opbevaringsmærkat til Exchange, skal du se følgende instruktioner:
- [Opret og konfigurer opbevaringspolitikker](create-retention-policies.md)
- [Opret opbevaringsnavne, og anvend dem i apps](create-apply-retention-labels.md)
- [Anvende en opbevaringsetiket på indhold automatisk](apply-retention-labels-automatically.md)