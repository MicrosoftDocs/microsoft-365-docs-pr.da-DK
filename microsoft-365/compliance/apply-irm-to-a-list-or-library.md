---
title: Anvende IRM (Information Rights Management) på en liste eller et bibliotek
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
description: Du kan bruge IRM (Information Rights Management) til at kontrollere og beskytte filer, der downloades fra lister eller biblioteker.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 4dfa7360dd178e5943402fcb834236d7d0bf9a08
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589122"
---
# <a name="apply-information-rights-management-irm-to-a-list-or-library"></a>Anvende IRM (Information Rights Management) på en liste eller et bibliotek

Du kan bruge IRM (Information Rights Management) til at kontrollere og beskytte filer, der downloades fra lister eller biblioteker. Denne funktion understøttes kun i Microsofts globale sky. IRM understøttes ikke for SharePoint lister og biblioteker i nationale skybaserede installationer.
  
## <a name="administrator-preparations-before-applying-irm"></a>Forberedelser fra administratorer, før IRM anvendes

- Azure Rights Management-tjenesten (Azure RMS) fra Azure Information Protection og tilsvarende i det lokale miljø, Active Directory Rights Management-tjenester (AD RMS), understøtter Information Rights Management for websteder. Der kræves ingen separate eller yderligere installationer.

- Før du anvender IRM på en liste eller et bibliotek, skal du aktivere IRM for dit websted. Du skal have administratorrettigheder for at aktivere IRM.

- Hvis du vil anvende IRM på en liste eller et bibliotek, skal du have administratortilladelser til listen eller biblioteket.

- Hvis du bruger en SharePoint Online, kan dine brugere opleve timeouts, når de henter større IRM-beskyttede filer. For at undgå timeouts skal du bruge dine Office-programmer til at anvende IRM-beskyttelse og gemme større filer i et SharePoint-bibliotek, der ikke bruger IRM.

> [!NOTE]
> Hvis du bruger SharePoint Server 2013, skal en serveradministrator installere tilladelser på alle front end webservere for hver filtype, som personerne i organisationen vil beskytte ved hjælp af IRM.
  
## <a name="apply-irm-to-a-list-or-library"></a>Anvend IRM på en liste eller et bibliotek
<a name="__toc256598179"> </a>

![Information Rights Management Indstillinger.](../media/1b708102-9c90-42b0-b255-ef0e72d0be88.png)
  
1. Gå til den liste eller det bibliotek, som du vil konfigurere IRM for.

2. Vælg fanen Bibliotek **på båndet,** og vælg derefter **Biblioteksbibliotek Indstillinger**. Hvis du arbejder på en liste, skal du vælge **fanen Liste** og derefter vælge **Vis Indstillinger**).
    
    ![SharePoint på Indstillinger Bibliotek på båndet.](../media/cdf718fa-d792-40fc-8026-00c3b80b9e05.png)
  
3. Under **Tilladelser og administration skal** du vælge **IDE (Information Rights Management**). Hvis linket IRM (Information Rights Management) ikke vises, er IRM muligvis ikke aktiveret for dit websted. Kontakt serveradministratoren for at se, om du kan aktivere IRM for dit websted. Linket **IDE (Information Rights Management** ) vises ikke for billedbiblioteker.

4. På siden **IDE (Information Rights Management Indstillinger** skal du markere afkrydsningsfeltet Begræns adgangen til dokumenter i dette bibliotek ved **download** for at anvende begrænset tilladelse på dokumenter, som brugere downloader fra denne liste eller dette bibliotek.

5. Skriv et **beskrivende navn til** politikken i feltet Opret en titel for tilladelsespolitik. Brug et navn, der hjælper dig med at identificere denne politik fra andre politikker. Brug f.eks **. Firmafortrolige** til at anvende begrænsede tilladelser på en liste eller et bibliotek, der indeholder fortrolige firmadokumenter.

6. I feltet **Tilføj** en beskrivelse af tilladelsespolitik skal du skrive en beskrivelse, der vises til personer, der bruger denne liste eller dette bibliotek, og som forklarer, hvordan de skal håndtere dokumenterne på listen eller i biblioteket. Du kan f.eks. skrive **Diskuter** kun indholdet af dokumentet med andre medarbejdere, hvis du vil begrænse adgangen til oplysningerne i disse dokumenter til interne medarbejdere. 

7. Hvis du vil anvende yderligere begrænsninger på dokumenterne på listen eller i biblioteket, skal **du vælge Vis** indstillinger og gøre et af følgende:

|**Sådan gør du:**|**Skal du gøre følgende:**|
|:-----|:-----|
|Give personer tilladelse til at udskrive dokumenter fra denne liste eller dette bibliotek|Markér **afkrydsningsfeltet Tillad, at brugere udskriver** .|
|Giv personer med mindst tilladelse til visningselementer tilladelse til at køre integreret kode eller makroer i et dokument.|Markér **afkrydsningsfeltet Tillad, at brugere kører script og skærmlæsere for at kunne arbejde på downloadede** dokumenter. Hvis du vælger denne indstilling, kan brugerne køre kode for at udtrække indholdet af et dokument.           |
|Vælg denne indstilling, hvis du vil begrænse adgangen til indhold til en bestemt tidsperiode. Hvis du vælger denne indstilling, udløber personers udstedelseslicenser for at få adgang til indholdet efter det angivne antal dage, og folk skal vende tilbage til serveren for at bekræfte deres legitimationsoplysninger og hente en ny kopi.|Markér afkrydsningsfeltet Efter download, udløber adgangsrettigheder til dokumenter efter dette antal dage **(1-365** ), og angiv derefter det antal dage, dokumentet skal kunne ses for.|
| Forhindre personer i at overføre dokumenter, der ikke understøtter IRM, til denne liste eller dette bibliotek. Hvis du vælger denne indstilling, vil andre ikke kunne overføre nogen af følgende filtyper: Filtyper, der ikke har tilsvarende IRM-opdateringer installeret på alle front end webservere. Filtyper, der SharePoint Server 2010, kan ikke dekryptere. Filtyper, der er IRM-beskyttede i et andet program.|Markér **afkrydsningsfeltet Tillad ikke brugere at overføre dokumenter, der ikke understøtter IRM** .|
|Fjern begrænsede tilladelser fra denne liste eller dette bibliotek på en bestemt dato.|Markér **afkrydsningsfeltet Stop begrænsning af adgang til biblioteket** ved, og vælg derefter den ønskede dato.|
|Styr det interval, legitimationsoplysningerne cachelagres for det program, der er licenseret til at åbne dokumentet.|Markér **afkrydsningsfeltet Brugere skal bekræfte** deres legitimationsoplysninger med dette interval (dage), og angiv derefter intervallet for cachelagring af legitimationsoplysninger i antal dage.|
|Tillad gruppebeskyttelse, så brugere kan dele med medlemmer af den samme gruppe.|Vælg **Tillad gruppebeskyttelse**, og angiv gruppens navn til deling.|

8. Når du er færdig med at vælge de ønskede indstillinger, skal du vælge **OK**.
  
## <a name="what-is-information-rights-management"></a>Hvad er Information Rights Management?
<a name="__toc256598175"> </a>

IRM (Information Rights Management) gør det muligt at begrænse de handlinger, som brugere kan udføre på filer, der er blevet downloadet fra lister eller biblioteker. IRM krypterer de downloadede filer og begrænser sættet af brugere og programmer, der har tilladelse til at dekryptere disse filer. IRM kan også begrænse rettighederne for de brugere, der har tilladelse til at læse filer, så de ikke kan udføre handlinger som f.eks. at udskrive kopier af filerne eller kopiere tekst fra dem.
  
Du kan bruge IRM på lister eller biblioteker til at begrænse spredningen af følsomt indhold. Hvis du f.eks. opretter et dokumentbibliotek for at dele oplysninger om kommende produkter med udvalgte marketingrepræsentanter, kan du bruge IRM til at forhindre disse personer i at dele dette indhold med andre medarbejdere i virksomheden.
  
På et websted anvender du IRM på en hel liste eller et helt bibliotek i stedet for på individuelle filer. Det gør det nemmere at sikre et ensartet beskyttelsesniveau for et helt sæt af dokumenter eller filer. IRM kan således hjælpe din organisation med at håndhæve firmapolitikker, der styrer brugen og spredningen af fortrolige eller beskyttede oplysninger.
  
> [!NOTE]
> Oplysningerne på denne side om Information Rights Management erstatter alle vilkår, der refererer til "Information Rights Management" i enhver Microsoft SharePoint Server 2013- og SharePoint Server 2016-licensaftale. 
  
### <a name="how-irm-can-help-protect-content"></a>Sådan beskytter IRM indhold
<a name="__toc256598176"> </a>

IRM hjælper med at beskytte begrænset indhold på følgende måder:
  
- Hjælper dig med at forhindre, at en autoriseret fremviser kopierer, redigerer, udskriver, faxer eller kopierer og indsætter indhold uautoriseret
    
- Hjælper dig med at forhindre en autoriseret fremviser i at kopiere indholdet ved hjælp af funktionen Print Screen i Microsoft Windows
    
- Hjælper dig med at forhindre uautoriserede seere i at få vist indholdet, hvis det sendes i en mail, efter det er hentet fra serveren
    
- Begrænser adgangen til indhold til en bestemt tidsperiode, hvorefter brugerne skal bekræfte deres legitimationsoplysninger og hente indholdet igen
    
- Hjælper med at håndhæve firmapolitikker, der styrer brugen og spredningen af indhold i din organisation
    
### <a name="how-irm-cannot-help-protect-content"></a>Sådan beskytter IRM ikke indhold
<a name="__toc256598177"> </a>

IRM kan ikke beskytte begrænset indhold fra følgende:
  
- Sletning, tyveri, registrering eller overførsel fra skadelige programmer som trojanske heste, tastetrykslogføringer og visse typer spyware
    
- Tab eller beskadigelse på grund af computervirusser
    
- Manuel kopiering eller ny skrift af indhold fra skærmen på en skærm
    
- Digital billedbilleder eller filmfoto af indhold, der vises på en skærm
    
- Kopiering via brug af tredjepartsskærmbilledeprogrammer
    
- Kopiering af metadata for indhold (kolonneværdier) ved hjælp af programmer til hentning af skærm eller kopiering og indsættelse fra tredjepart
  
## <a name="how-irm-works-for-lists-and-libraries"></a>Sådan fungerer IRM for lister og biblioteker
<a name="__toc256598178"> </a>

IRM-beskyttelse anvendes på filer på liste- eller biblioteksniveau. Når IRM er aktiveret for et bibliotek, anvendes rettighedsstyring på alle filerne i det pågældende bibliotek. Når IRM er aktiveret for en liste, gælder rettighedsstyring kun for filer, der er knyttet til listeelementer, ikke de faktiske listeelementer.
  
Når personer henter filer på en IRM-aktiveret liste eller i et IRM-aktiveret bibliotek, krypteres filerne, så kun autoriserede personer kan se dem. Hver rettighedsstyret fil indeholder også en udstedelseslicens, der pålægger de personer, der får vist filen, begrænsninger. Typiske begrænsninger omfatter at gøre en fil skrivebeskyttet, deaktivere kopieringen af tekst, forhindre brugere i at gemme en lokal kopi og forhindre folk i at udskrive filen. Klientprogrammer, der kan læse IRM-understøttede filtyper, bruger udstedelseslicensen i den rettighedsstyret fil til at håndhæve disse begrænsninger. Sådan bevarer en rettighedsstyret fil beskyttelsen, selv efter den er hentet fra serveren.
  
De typer begrænsninger, der gælder for en fil, når den downloades fra en liste eller et bibliotek, er baseret på den enkelte brugers tilladelser på det websted, der indeholder filen. Følgende tabel forklarer, hvordan tilladelserne på websteder svarer til IRM-tilladelser.
  
|**Tilladelser**|**IRM-tilladelser**|
|:-----|:-----|
|Administrere tilladelser, administrere websted|**Fuld kontrol** (som defineret af klientprogrammet): Denne tilladelse giver generelt en bruger mulighed for at læse, redigere, kopiere, gemme og ændre tilladelser for rettighedsstyret indhold.|
|Rediger elementer, Administrer lister, Tilføj og tilpas sider|**Rediger**, **kopiér** og **gem: En** bruger kan kun udskrive en fil, hvis  afkrydsningsfeltet Tillad brugere at udskrive dokumenter er markeret på siden i Indstillinger for listen eller biblioteket.|
|Vis elementer|**Læs**: En bruger kan læse dokumentet, men kan ikke kopiere eller ændre indholdet. En bruger kan kun udskrive **, hvis** afkrydsningsfeltet Tillad brugere at udskrive dokumenter er markeret på siden IDE (Information Rights Management Indstillinger for listen eller biblioteket.|
|Andet|Ingen andre tilladelser svarer direkte til IRM-tilladelser.|
   
Når du aktiverer IRM for en liste eller et bibliotek i SharePoint Server 2013, kan du kun beskytte filtyper på den pågældende liste eller det pågældende bibliotek, for hvilke der er installeret et program på alle front end-webservere. En kryptering er et program, der kontrollerer kryptering og dekryptering af rettighedsstyret filer i et bestemt filformat. SharePoint indeholder oplysninger om følgende filtyper:
  
- Microsoft Office InfoPath-formularer
    
- 97-2003-filformaterne til følgende Microsoft Office programmer: Word, Excel og PowerPoint
    
- Dialogboksen Office Open XML-formater til følgende Microsoft Office programmer: Word, Excel og PowerPoint
    
- XPS-formatet (XML Paper Specification)
    
Hvis din organisation planlægger at bruge IRM til at beskytte andre filtyper ud over dem, der er anført ovenfor, skal din serveradministrator installere tilladelser for disse yderligere filformater.
  

