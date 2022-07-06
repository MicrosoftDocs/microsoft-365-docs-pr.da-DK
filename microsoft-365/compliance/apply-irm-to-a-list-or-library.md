---
title: Anvend IRM på en liste eller et bibliotek
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 7/2/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- OSU150
- OSU160
- MET150
ms.assetid: 3bdb5c4e-94fc-4741-b02f-4e7cc3c54aa1
ms.collection:
- M365-security-compliance
- SPO_Content
description: Du kan bruge IRM (Information Rights Management) til at styre og beskytte filer, der downloades fra lister eller biblioteker.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: cf677fc81a20b7e86d9b66505dd8968c0a31272b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633119"
---
# <a name="apply-information-rights-management-irm-to-a-list-or-library"></a>Anvend IRM (Information Rights Management) på en liste eller et bibliotek

Du kan bruge IRM (Information Rights Management) til at styre og beskytte filer, der downloades fra lister eller biblioteker. Denne funktion understøttes kun i Microsofts globale cloud. IRM understøttes ikke for SharePoint-lister og -biblioteker i nationale cloudinstallationer.
  
## <a name="administrator-preparations-before-applying-irm"></a>Administratorforberedelser før anvendelse af IRM

- Azure Rights Management-tjenesten (Azure RMS) fra Azure Information Protection og ad RMS (Active Directory Rights Management Services) i det lokale miljø understøtter Information Rights Management for websteder. Der kræves ingen separate eller yderligere installationer.

- Før du anvender IRM på en liste eller et bibliotek, skal du aktivere IRM for dit websted. Du skal have administratortilladelser for at aktivere IRM.

- Hvis du vil anvende IRM på en liste eller et bibliotek, skal du have administratorrettigheder til listen eller biblioteket.

- Hvis du bruger SharePoint Online, kan brugerne opleve timeout, når de downloader større IRM-beskyttede filer. Hvis du vil undgå timeout, skal du bruge dine Office-programmer til at anvende IRM-beskyttelse og gemme større filer i et SharePoint-bibliotek, der ikke bruger IRM.

> [!NOTE]
> Hvis du bruger SharePoint Server 2013, skal en serveradministrator installere beskyttere på alle frontendwebservere for hver filtype, som personerne i din organisation vil beskytte ved hjælp af IRM.
  
## <a name="apply-irm-to-a-list-or-library"></a>Anvend IRM på en liste eller et bibliotek
<a name="__toc256598179"> </a>

![Indstillinger for Information Rights Management.](../media/1b708102-9c90-42b0-b255-ef0e72d0be88.png)
  
1. Gå til den liste eller det bibliotek, du vil konfigurere IRM for.

2. På båndet skal du vælge fanen **Bibliotek** og derefter vælge **Biblioteksindstillinger**. Hvis du arbejder på en liste, skal du vælge fanen **Liste** og derefter vælge **Listeindstillinger**.
    
    ![Knapper til indstillinger for SharePoint-bibliotek på båndet.](../media/cdf718fa-d792-40fc-8026-00c3b80b9e05.png)
  
3. Under **Tilladelser og administration** skal du vælge **Information Rights Management**. Hvis linket Information Rights Management ikke vises, er IRM muligvis ikke aktiveret for dit websted. Kontakt serveradministratoren for at se, om du kan aktivere IRM for dit websted. Linket **Information Rights Management** vises ikke for billedbiblioteker.

4. På siden **Indstillinger for Information Rights Management** skal du markere afkrydsningsfeltet **Begræns tilladelse til dokumenter i dette bibliotek ved overførsel** for at anvende begrænsede tilladelser på dokumenter, som brugere downloader fra denne liste eller dette bibliotek.

5. Angiv et beskrivende navn til politikken i feltet **Opret en tilladelsespolitiktitel** . Brug et navn, der hjælper dig med at identificere denne politik fra andre politikker. Brug f.eks. **Firmafortrolige** til at anvende begrænsede tilladelser på en liste eller et bibliotek, der indeholder fortrolige virksomhedsdokumenter.

6. I feltet **Tilføj en beskrivelse af tilladelsespolitikken** skal du skrive en beskrivelse, der vises for de personer, der bruger denne liste eller dette bibliotek, som forklarer, hvordan de skal håndtere dokumenterne på denne liste eller dette bibliotek. Du kan f.eks **. kun skrive Diskuter indholdet af dette dokument med andre medarbejdere** , hvis du vil begrænse adgangen til oplysningerne i disse dokumenter til interne medarbejdere. 

7. Hvis du vil anvende yderligere begrænsninger på dokumenterne på denne liste eller dette bibliotek, skal du vælge **Vis indstillinger** og gøre et af følgende:

|**Sådan gør du:**|**Gør følgende:**|
|:-----|:-----|
|Tillad, at personer udskriver dokumenter fra denne liste eller dette bibliotek|Markér afkrydsningsfeltet **Tillad, at brugere udskriver** .|
|Tillad, at personer med mindst tilladelsen Vis elementer kører integreret kode eller makroer i et dokument.|Markér afkrydsningsfeltet **Tillad, at seere kører script og skærmlæser til at fungere på hentede dokumenter** . Hvis du vælger denne indstilling, kan brugerne køre kode for at udtrække indholdet af et dokument.           |
|Vælg denne indstilling, hvis du vil begrænse adgangen til indhold til et angivet tidsrum. Hvis du vælger denne indstilling, udløber udstedelseslicenser for personer for at få adgang til indholdet efter det angivne antal dage, og folk bliver bedt om at vende tilbage til serveren for at bekræfte deres legitimationsoplysninger og downloade en ny kopi.|Markér afkrydsningsfeltet **Efter hentning udløber adgangen til dokumentet efter dette antal dage (1-365),** og angiv derefter det antal dage, som dokumentet skal kunne ses for.|
| Undgå, at personer overfører dokumenter, der ikke understøtter IRM, til denne liste eller dette bibliotek. Hvis du vælger denne indstilling, kan andre ikke overføre nogen af følgende filtyper: Filtyper, hvor der ikke er installeret tilsvarende IRM-beskyttere på alle frontendwebservere. Filtyper, som SharePoint Server 2010 ikke kan dekryptere. Filtyper, der er IRM-beskyttede i et andet program.|Markér afkrydsningsfeltet **Tillad ikke, at brugere overfører dokumenter, der ikke understøtter IRM** .|
|Fjern begrænsede tilladelser fra denne liste eller dette bibliotek på en bestemt dato.|Markér afkrydsningsfeltet **Stop begrænsning af adgang til biblioteket på** , og vælg derefter den ønskede dato.|
|Kontrollér det interval, hvor legitimationsoplysningerne cachelagres for det program, der har licens til at åbne dokumentet.|Markér afkrydsningsfeltet **Brugerne skal bekræfte deres legitimationsoplysninger ved hjælp af dette interval (dage),** og angiv derefter intervallet for cachelagring af legitimationsoplysninger i antal dage.|
|Tillad gruppebeskyttelse, så brugerne kan dele med medlemmer af den samme gruppe.|Vælg **Tillad gruppebeskyttelse**, og angiv gruppens navn til deling.|

8. Når du er færdig med at vælge de ønskede indstillinger, skal du vælge **OK**.
  
## <a name="what-is-information-rights-management"></a>Hvad er Information Rights Management?
<a name="__toc256598175"> </a>

IRM (Information Rights Management) giver dig mulighed for at begrænse de handlinger, som brugerne kan udføre på filer, der er blevet downloadet fra lister eller biblioteker. IRM krypterer de downloadede filer og begrænser sættet af brugere og programmer, der har tilladelse til at dekryptere disse filer. IRM kan også begrænse rettighederne for de brugere, der har tilladelse til at læse filer, så de ikke kan udføre handlinger, f.eks. udskrive kopier af filerne eller kopiere tekst fra dem.
  
Du kan bruge IRM på lister eller biblioteker til at begrænse udbredelsen af følsomt indhold. Hvis du f.eks. opretter et dokumentbibliotek for at dele oplysninger om kommende produkter med udvalgte marketingrepræsentanter, kan du bruge IRM til at forhindre disse personer i at dele dette indhold med andre medarbejdere i virksomheden.
  
På et websted anvender du IRM på en hel liste eller et bibliotek i stedet for på individuelle filer. Det gør det nemmere at sikre et ensartet beskyttelsesniveau for et helt sæt dokumenter eller filer. IRM kan dermed hjælpe din organisation med at håndhæve virksomhedspolitikker, der styrer brugen og formidlingen af fortrolige eller beskyttede oplysninger.
  
> [!NOTE]
> Oplysningerne på denne side om Information Rights Management tilsidesætter alle vilkår, der refererer til "Information Rights Management" i alle Licensaftaler til Microsoft SharePoint Server 2013 og SharePoint Server 2016. 
  
### <a name="how-irm-can-help-protect-content"></a>Sådan hjælper IRM med at beskytte indhold
<a name="__toc256598176"> </a>

IRM hjælper med at beskytte begrænset indhold på følgende måder:
  
- Hjælper med at forhindre, at en godkendt fremviser kopierer, redigerer, udskriver, faxer eller kopierer og indsætter indholdet til uautoriseret brug
    
- Hjælper med at forhindre, at en godkendt fremviser kopierer indholdet ved hjælp af funktionen Udskriftsskærm i Microsoft Windows
    
- Hjælper med at forhindre, at en uautoriseret fremviser får vist indholdet, hvis det sendes i en mail, efter at den er downloadet fra serveren
    
- Begrænser adgangen til indhold til et angivet tidsrum, hvorefter brugerne skal bekræfte deres legitimationsoplysninger og downloade indholdet igen
    
- Hjælper med at gennemtvinge virksomhedspolitikker, der styrer brugen og formidlingen af indhold i din organisation
    
### <a name="how-irm-cannot-help-protect-content"></a>Sådan kan IRM ikke hjælpe med at beskytte indhold
<a name="__toc256598177"> </a>

IRM kan ikke beskytte begrænset indhold fra følgende:
  
- Sletning, tyveri, registrering eller overførsel af skadelige programmer, f.eks. trojanske heste, tastetrykloggere og visse typer spyware
    
- Tab eller beskadigelse på grund af computervirushandlinger
    
- Manuel kopiering eller gentagelse af indhold fra visningen på en skærm
    
- Digital eller filmfotografering af indhold, der vises på en skærm
    
- Kopiering via brug af programmer til hentning af skærmbilleder fra tredjepart
    
- Kopiering af indholdsmetadata (kolonneværdier) ved hjælp af programmer til hentning af skærmbilleder fra tredjepart eller handlingen Kopiér og indsæt
  
## <a name="how-irm-works-for-lists-and-libraries"></a>Sådan fungerer IRM for lister og biblioteker
<a name="__toc256598178"> </a>

IRM-beskyttelse anvendes på filer på liste- eller biblioteksniveau. Når IRM er aktiveret for et bibliotek, gælder rights management for alle filerne i det pågældende bibliotek. Når IRM er aktiveret for en liste, gælder rights management kun for filer, der er knyttet til listeelementer, ikke de faktiske listeelementer.
  
Når folk downloader filer på en IRM-aktiveret liste eller et IRM-bibliotek, krypteres filerne, så det kun er godkendte personer, der kan se dem. Hver rettighedsadministreret fil indeholder også en udstedelseslicens, der pålægger begrænsninger for de personer, der får vist filen. Typiske begrænsninger omfatter at gøre en fil skrivebeskyttet, deaktivere kopiering af tekst, forhindre personer i at gemme en lokal kopi og forhindre andre i at udskrive filen. Klientprogrammer, der kan læse IRM-understøttede filtyper, bruger udstedelseslicensen i den rettighedsadministrerede fil til at gennemtvinge disse begrænsninger. Det er sådan, en rettighedsadministreret fil bevarer sin beskyttelse, selv efter at den er hentet fra serveren.
  
De typer begrænsninger, der gælder for en fil, når den downloades fra en liste eller et bibliotek, er baseret på den enkelte brugers tilladelser på det websted, der indeholder filen. I følgende tabel forklares det, hvordan tilladelserne på websteder svarer til IRM-tilladelser.
  
|**Tilladelser**|**IRM-tilladelser**|
|:-----|:-----|
|Administrer tilladelser, Administrer websted|**Fuld kontrol** (som defineret af klientprogrammet): Denne tilladelse giver normalt en bruger mulighed for at læse, redigere, kopiere, gemme og redigere tilladelser til rettighedsadministreret indhold.|
|Rediger elementer, administrer lister, tilføj og tilpas sider|**Rediger**, **kopiér** og **gem**: En bruger kan kun udskrive en fil, hvis afkrydsningsfeltet **Tillad brugere at udskrive dokumenter** er markeret på siden Indstillinger for Information Rights Management for listen eller biblioteket.|
|Vis elementer|**Læs**: En bruger kan læse dokumentet, men kan ikke kopiere eller ændre indholdet. En bruger kan kun udskrive, hvis afkrydsningsfeltet **Tillad, at brugere udskriver dokumenter** er markeret på siden Indstillinger for Information Rights Management for listen eller biblioteket.|
|Andet|Ingen andre tilladelser svarer direkte til IRM-tilladelser.|
   
Når du aktiverer IRM for en liste eller et bibliotek i SharePoint Server 2013, kan du kun beskytte filtyper på den pågældende liste eller det bibliotek, hvor der er installeret en beskytter på alle frontendwebservere. En beskytter er et program, der styrer kryptering og dekryptering af rettighedsadministrerede filer i et bestemt filformat. SharePoint indeholder beskyttere til følgende filtyper:
  
- Microsoft Office InfoPath-formularer
    
- Filformaterne 97-2003 til følgende Microsoft Office-programmer: Word, Excel og PowerPoint
    
- Office Open XML-formaterne til følgende Microsoft Office-programmer: Word, Excel og PowerPoint
    
- XPS-formatet (XML Paper Specification)
    
Hvis din organisation planlægger at bruge IRM til at beskytte andre filtyper ud over dem, der er angivet ovenfor, skal serveradministratoren installere beskyttere til disse yderligere filformater.
  

