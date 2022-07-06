---
title: Få mere at vide om opbevaring for SharePoint og OneDrive
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
description: Få mere at vide om, hvordan opbevaring fungerer for SharePoint og OneDrive.
ms.openlocfilehash: 3fb316c0780ccb5c854e12dae8bde450c877f1d2
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629183"
---
# <a name="learn-about-retention-for-sharepoint-and-onedrive"></a>Få mere at vide om opbevaring for SharePoint og OneDrive

>*[Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Oplysningerne i denne artikel supplerer [Få mere at vide om opbevaring](retention.md) , fordi den indeholder oplysninger, der er specifikke for SharePoint og OneDrive.

For andre arbejdsbelastninger skal du se:

- [Få mere at vide om opbevaring til Microsoft Teams](retention-policies-teams.md)
- [Få mere at vide om opbevaring til Yammer](retention-policies-yammer.md)
- [Få mere at vide om opbevaring til Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Hvad er inkluderet i forbindelse med opbevaring og sletning

Alle filer, der er gemt på SharePoint- eller OneDrive-websteder, kan bevares ved at anvende en opbevaringspolitik eller en opbevaringsmærkat. 

Følgende filer kan slettes:

- Når du bruger en opbevaringspolitik: Alle filer i dokumentbiblioteker, som omfatter alle automatisk oprettede SharePoint-dokumentbiblioteker, f.eks **. webstedsaktiver**.
    
- Når du bruger opbevaringsmærkater: Alle filer i alle dokumentbiblioteker og alle filer på rodniveau, der ikke findes i en mappe.
    
> [!TIP]
> Når du bruger en [forespørgsel med en politik for automatisk anvendelse af en opbevaringsmærkat](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-keywords-or-searchable-properties), kan du udelade bestemte dokumentbiblioteker ved hjælp af følgende post: `NOT(DocumentLink:"<URL to document library>")`

Listeelementer understøttes ikke af opbevaringspolitikker, men understøttes af opbevaringsmærkater med undtagelse af elementer på systemlister. Disse er skjulte lister, der bruges af SharePoint til at administrere systemet og omfatter mastersidekataloget, løsningskataloget og datakilder. Når der anvendes opbevaringsmærkater på understøttede listeelementer, bevares de altid i henhold til opbevaringsindstillingerne, men de slettes ikke, hvis de er skjult i søgningen.

Når du anvender en opbevaringsmærkat på et understøttet listeelement, der har en vedhæftet dokumentfil:
- For en standardopbevaringsmærkat (deklarerer ikke, at elementet er en post):
    - Den vedhæftede fil nedarver ikke automatisk mærkatens opbevaringsindstillinger, men kan mærkes uafhængigt af hinanden.
- For en opbevaringsmærkat, der deklarerer elementet, en post: 
    - Den vedhæftede fil nedarver automatisk opbevaringsindstillingerne fra etiketten, hvis dokumentet ikke allerede er mærket.

Opbevaringsindstillinger fra både opbevaringspolitikker og opbevaringsmærkater gælder ikke for organisering af strukturer, der omfatter biblioteker, lister og mapper.

I forbindelse med opbevaringspolitikker og mærkatpolitikker for automatisk anvendelse: SharePoint-websteder skal indekseres, for at opbevaringsindstillingerne kan anvendes. Men hvis elementer i SharePoint-dokumentbiblioteker er konfigureret til ikke at blive vist i søgeresultater, udelukker denne konfiguration ikke filer fra opbevaringsindstillingerne.


## <a name="how-retention-works-for-sharepoint-and-onedrive"></a>Sådan fungerer opbevaring for SharePoint og OneDrive

Hvis du vil gemme indhold, der skal bevares, skal SharePoint og OneDrive oprette et bibliotek til bevarelse af venteposition, hvis der ikke findes et for webstedet. Biblioteket til bevarelse af venteposition er ikke designet til at blive brugt interaktivt, men gemmer i stedet automatisk filer, når dette er nødvendigt af hensyn til overholdelse af angivne standarder. Det fungerer på følgende måde:

Når en bruger ændrer eller sletter et element, der kan opbevares, kontrolleres det, om indholdet er blevet ændret, siden opbevaringsindstillingerne blev anvendt. Hvis dette er den første ændring, siden opbevaringsindstillingerne blev anvendt, kopieres indholdet til biblioteket Bevarelse af venteposition, hvilket gør det muligt for brugeren at ændre eller slette det oprindelige indhold.

Et timerjob kører jævnligt i biblioteket bevarelsesventeposition. For indhold, der har været i biblioteket til bevarelse af venteposition i mere end 30 dage, sammenligner dette job indholdet med alle de forespørgsler, der bruges af opbevaringsindstillingerne for det pågældende indhold. Indhold, der er ældre end deres konfigurerede opbevaringsperiode, slettes derefter fra biblioteket bevarelsesposition og fra den oprindelige placering, hvis det stadig er der. Dette timerjob kører hver 7. dag, hvilket betyder, at det sammen med de minimale 30 dage kan tage op til 37 dage, før indhold slettes fra biblioteket bevarelsesventetid.

Denne funktionsmåde for kopiering af filer til biblioteket til bevarelse af venteposition gælder for indhold, der findes, da opbevaringsindstillingerne blev anvendt. Desuden bevares alt nyt indhold, der er oprettet eller føjet til webstedet, efter at det er inkluderet i politikken, i biblioteket til bevarelse af venteposition i forbindelse med opbevaringspolitikker. Nyt indhold kopieres dog ikke til biblioteket Bevarelses venteposition, første gang det redigeres, kun når det slettes. Hvis du vil bevare alle versioner af en fil, skal [versionsstyring](#how-retention-works-with-document-versions) være aktiveret for det oprindelige websted.
  
Brugerne får vist en fejlmeddelelse, hvis de forsøger at slette et bibliotek, en liste, en mappe eller et websted, der skal opbevares. De kan slette en mappe, hvis de først flytter eller sletter filer i den mappe, der skal opbevares.

Brugerne får også vist en fejlmeddelelse, hvis de forsøger at slette et navngivet element i en af følgende situationer. Elementet kopieres ikke til biblioteket til bevarelse af venteposition, men forbliver på den oprindelige placering:

- Indstillingen for datastyring, der giver brugerne mulighed for at slette navngivne elementer, er deaktiveret.
    
    Hvis du vil kontrollere eller ændre denne indstilling, skal du gå til løsningen **Styring af poster** i **Microsoft Purview-compliance-portal > Indstillinger for** >  administration af **poster** > **Opbevaringsmærkater** > **Sletning af elementer**. Der er separate indstillinger for SharePoint og OneDrive.
    
    Hvis du ikke har adgang til løsningen til **dataadministration** , kan du også bruge *AllowFilesWithKeepLabelToBeDeletedSPO* og *AllowFilesWithKeepLabelToBeDeletedODB* fra [Get-PnPTenant](https://pnp.github.io/powershell/cmdlets/Get-PnPTenant.html) og [Set-PnPTenant](https://pnp.github.io/powershell/cmdlets/Set-PnPTenant.html).

- Opbevaringsmærkaten markerer elementer som en post, og den er [låst](record-versioning.md).
    
    Det er først, når posten er låst op, at en kopi af den sidste version gemmes i biblioteket Bevarelsesventeposition.

- Opbevaringsmærkaten markerer elementer som en [lovmæssig post](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked), hvilket altid forhindrer, at elementet redigeres eller slettes.

Når opbevaringsindstillinger er tildelt til indhold på en OneDrive-konto eller et SharePoint-websted, afhænger stierne af, om opbevaringsindstillingerne skal bevares og slettes, kun bevares eller slettes.

Når opbevaringsindstillingerne skal bevares og slettes:

![Diagram over indholdslivscyklus i SharePoint og OneDrive.](../media/Retention_Diagram_of_retention_flow_in_sites.png)
  
1. **Hvis indholdet ændres eller slettes** i løbet af opbevaringsperioden, oprettes der en kopi af det oprindelige indhold, som det fandtes, da opbevaringsindstillingerne blev tildelt, i biblioteket Bevarelse af venteposition. Her identificerer timerjobbet elementer, hvis opbevaringsperiode er udløbet. Disse elementer flyttes til papirkurven i anden fase, hvor de slettes permanent i slutningen af 93 dage. Papirkurv i andet trin er ikke synlig for slutbrugere (kun papirkurv i første fase), men administratorer af grupper af websteder kan få vist og gendanne indhold derfra.

    > [!NOTE]
    > For at forhindre utilsigtede tab af data sletter vi ikke længere indhold permanent fra biblioteket bevarelsesposition. Vi sletter i stedet kun indhold permanent fra Papirkurven, så alt indhold fra biblioteket til bevarelsesbevaring går nu gennem papirkurven i andet trin.
    
2. **Hvis indholdet ikke ændres eller slettes** i løbet af opbevaringsperioden, flytter timerjobbet dette indhold til papirkurv i første fase i slutningen af opbevaringsperioden. Hvis en bruger sletter indholdet derfra eller tømmer denne papirkurv (også kaldet rensning), flyttes dokumentet til papirkurven i andet trin. En opbevaringsperiode på 93 dage strækker sig over både papirkurve i første og andet trin. Efter 93 dage slettes dokumentet permanent, uanset hvor det er placeret, enten i papirkurv i første fase eller i anden fase. Papirkurven er ikke indekseret og er derfor ikke tilgængelig til søgning. Derfor kan en eDiscovery-søgning ikke finde noget papirkurvsindhold, som en venteposition skal placeres i.

> [!NOTE]
> På grund af det [første opbevaringsprincip](retention.md#the-principles-of-retention-or-what-takes-precedence) suspenderes permanent sletning altid, hvis det samme element skal bevares på grund af en anden opbevaringspolitik eller opbevaringsmærkat, eller den er omfattet af eDiscovery-ventepositioner af juridiske eller undersøgelsesmæssige årsager.

Når opbevaringsindstillingerne kun bevares eller slettes, er indholdsstierne variationer af bevar og slet:

### <a name="content-paths-for-retain-only-retention-settings"></a>Indholdsstier til opbevaringsindstillinger kun for bevarelse

1. **Hvis indholdet ændres eller slettes** i løbet af opbevaringsperioden: Der oprettes en kopi af det oprindelige dokument i biblioteket Bevarelsesposition og bevares indtil slutningen af opbevaringsperioden, når kopien i biblioteket Bevarelses venteposition flyttes til papirkurven i andet trin og slettes permanent efter 93 dage.

2. **Hvis indholdet ikke ændres eller slettes** i løbet af opbevaringsperioden: Der sker intet før og efter opbevaringsperioden; dokumentet forbliver på den oprindelige placering.

### <a name="content-paths-for-delete-only-retention-settings"></a>Indholdsstier til indstillinger for opbevaring, der kun kan slettes

1. **Hvis indholdet slettes** i den konfigurerede periode: Dokumentet flyttes til Papirkurv i første fase. Hvis en bruger sletter dokumentet derfra eller tømmer papirkurven, flyttes dokumentet til papirkurven i anden fase. En opbevaringsperiode på 93 dage strækker sig over både papirkurve for første fase og andet trin. Efter 93 dage slettes dokumentet permanent, uanset hvor det er placeret, enten i papirkurv i første fase eller i anden fase. Hvis indholdet ændres i den konfigurerede periode, følger det den samme sti til sletning efter den konfigurerede periode.

2. **Hvis indholdet ikke slettes** i den konfigurerede periode: I slutningen af den konfigurerede periode i opbevaringspolitikken flyttes dokumentet til papirkurv i første fase. Hvis en bruger sletter dokumentet derfra eller tømmer denne papirkurv (også kaldet rensning), flyttes dokumentet til papirkurven i andet trin. En opbevaringsperiode på 93 dage strækker sig over både papirkurve for første fase og andet trin. Efter 93 dage slettes dokumentet permanent, uanset hvor det er placeret, enten i papirkurv i første fase eller i anden fase. Papirkurven er ikke indekseret og er derfor ikke tilgængelig til søgning. Derfor kan en eDiscovery-søgning ikke finde noget papirkurvsindhold, som en venteposition skal placeres i.

## <a name="how-retention-works-with-cloud-attachments"></a>Sådan fungerer opbevaring med vedhæftede filer i skyen

Vedhæftede filer i skyen er integrerede links til filer, som brugerne deler, og de kan bevares og slettes, når dine brugere deler dem i Outlook-mails og Teams-meddelelser. Når du [automatisk anvender en opbevaringsmærkat på vedhæftede filer i skyen](apply-retention-labels-automatically.md#auto-apply-labels-to-cloud-attachments), anvendes opbevaringsmærkaten på en kopi af den delte fil, som er gemt i biblioteket Bevarelse af venteposition.

I dette scenarie anbefaler vi, at du konfigurerer mærkatindstillingen for at starte opbevaringsperioden baseret på, hvornår elementet er mærket. Hvis du konfigurerer opbevaringsperioden baseret på, hvornår elementet oprettes eller senest ændres, hentes denne dato fra den oprindelige fil på tidspunktet for delingen. Hvis du konfigurerer starten på opbevaringen til at være ved seneste ændring, har denne indstilling ingen effekt for denne kopi i biblioteket bevarelsesventeposition.

Men hvis den oprindelige fil ændres og derefter deles igen, gemmes og navngives der en ny kopi af filen som en ny version i biblioteket bevarelses venteposition.

Hvis den oprindelige fil deles igen, men ikke ændres, opdateres den navngivne dato for kopien i biblioteket Bevarelsesposition. Denne handling nulstiller starten af opbevaringsperioden, og det er derfor, vi anbefaler, at du konfigurerer starten af opbevaringsperioden til at være baseret på, hvornår elementet er mærket.

Da opbevaringsmærkaten ikke anvendes på den oprindelige fil, ændres eller slettes den navngivne fil aldrig af en bruger. Den navngivne fil forbliver i biblioteket bevarelses venteposition, indtil timerjobbet identificerer, at opbevaringsperioden er udløbet. Hvis opbevaringsindstillingerne er konfigureret til at slette elementer, flyttes filen derefter til papirkurven i anden fase, hvor den slettes permanent i slutningen af 93 dage:

![Sådan fungerer opbevaring for vedhæftede filer i skyen, der er gemt i SharePoint og OneDrive](../media/retention-diagram-of-retention-flow-cloud-attachments.png)

Den kopi, der er gemt i biblioteket bevarelsesposition, oprettes typisk inden for en time fra den vedhæftede fil i skyen, der deles.

## <a name="how-retention-works-with-onenote-content"></a>Sådan fungerer opbevaring med OneNote-indhold

Når du anvender en opbevaringspolitik på en placering, der indeholder OneNote-indhold, eller en opbevaringsmærkat til en OneNote-mappe, er de forskellige OneNote-sider og -sektioner i baggrunden individuelle filer, der nedarver opbevaringsindstillingerne. Det betyder, at hver sektion på en side bevares og slettes individuelt i henhold til de opbevaringsindstillinger, du angiver.

Det er kun sider og sektioner, der påvirkes af de opbevaringsindstillinger, du angiver. Selvom du f.eks. får vist datoen **Ændret** for hver enkelt notesbog, bruges denne dato ikke af Microsoft 365-opbevaring.

## <a name="how-retention-works-with-document-versions"></a>Sådan fungerer opbevaring med dokumentversioner

Versionering er en funktion i alle dokumentlister og biblioteker i SharePoint og OneDrive. Versionsstyring bevarer som standard mindst 500 overordnede versioner, selvom du kan øge denne grænse. Du kan få flere oplysninger under [Aktivér og konfigurer versionering for en liste eller et bibliotek](https://support.office.com/article/1555d642-23ee-446a-990a-bcab618c7a37) , og [Sådan fungerer versionering på lister og biblioteker](https://support.microsoft.com/office/how-versioning-works-in-lists-and-libraries-0f6cd105-974f-44a4-aadb-43ac5bdfd247).
  
Når et dokument med versioner er underlagt opbevaringsindstillinger for at bevare dette indhold, findes versioner, der kopieres til biblioteket bevarelsesventeposition, som et separat element. Hvis opbevaringsindstillingerne er konfigureret til at blive slettet i slutningen af opbevaringsperioden:

- Hvis opbevaringsperioden er baseret på, hvornår indholdet blev oprettet, har hver version den samme udløbsdato som det oprindelige dokument. Det oprindelige dokument og dets versioner udløber samtidigt.

- Hvis opbevaringsperioden er baseret på, hvornår indholdet senest blev ændret, har hver version sin egen udløbsdato baseret på, hvornår det oprindelige dokument blev ændret for at oprette den pågældende version. Det oprindelige dokument og dets versioner udløber uafhængigt af hinanden.

Når opbevaringshandlingen er at slette dokumentet, slettes alle versioner, der ikke er i biblioteket til bevarelse af venteposition, samtidig i henhold til den aktuelle version.

For elementer, der er underlagt en opbevaringspolitik (eller eDiscovery-venteposition), ignoreres versionsgrænserne for dokumentbiblioteket, indtil opbevaringsperioden for dokumentet er nået (eller eDiscovery-ventepositionen frigives). I dette scenarie fjernes gamle versioner ikke automatisk, og brugerne forhindres i at slette versioner.

Det er ikke tilfældet for opbevaringsmærkater, når indholdet ikke er underlagt en opbevaringspolitik (eller en eDiscovery-venteposition). I stedet anvendes versionsgrænserne, så ældre versioner automatisk slettes for at imødekomme nye versioner, men brugerne forhindres stadig i at slette versioner.

## <a name="when-a-user-leaves-the-organization"></a>Når en bruger forlader organisationen

**SharePoint**:

Når en bruger forlader organisationen, påvirkes alt indhold, der er oprettet af den pågældende bruger, ikke, fordi SharePoint betragtes som et samarbejdsmiljø, i modsætning til en brugers postkasse eller OneDrive-konto.

**OneDrive**:

Hvis en bruger forlader organisationen, forbliver alle filer, der er omfattet af en opbevaringspolitik eller har en opbevaringsmærkat, underlagt opbevaringsindstillingerne i varigheden af den opbevaringsperiode, der er angivet i politikken eller etiketten. I løbet af denne periode fungerer al delingsadgang fortsat, og indholdet kan fortsat findes af indholdssøgning og eDiscovery. 

Når opbevaringsperioden udløber, og opbevaringsindstillingerne inkluderede en sletningshandling, flyttes indhold til Papirkurv for gruppe af websteder og er ikke tilgængeligt for andre end administratoren.

## <a name="configuration-guidance"></a>Konfigurationsvejledning

Hvis du ikke har arbejdet med at konfigurere opbevaring i Microsoft 365, skal du se [Kom i gang med administration af datalivscyklus](get-started-with-data-lifecycle-management.md).

Hvis du er klar til at konfigurere en opbevaringspolitik eller en opbevaringsmærkat for Exchange, skal du se følgende instruktioner:
- [Opret og konfigurer opbevaringspolitikker](create-retention-policies.md)
- [Publicer opbevaringsmærkater, og anvend dem i apps](create-apply-retention-labels.md)
- [Anvend automatisk en opbevaringsmærkat på indhold](apply-retention-labels-automatically.md)
