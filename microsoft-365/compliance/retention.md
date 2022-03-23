---
title: Få mere at vide om opbevaringspolitikker & navne til automatisk at bevare eller slette indhold
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
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om opbevaringspolitikker og opbevaringsetiketter, der hjælper dig med at bevare det, du har brug for, og slette det, du ikke har brug for.
ms.openlocfilehash: ac57859d7f27b22060b88189e79d386791535c9e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589478"
---
# <a name="learn-about-retention-policies-and-retention-labels"></a>Få mere at vide om opbevaringspolitikker og opbevaringsnavne

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Hvis du får vist meddelelser om opbevaringspolitikker i Teams eller har spørgsmål om opbevaringsnavne i dine apps, kan du kontakte din it-afdeling for at få oplysninger om, hvordan de er konfigureret for dig. I mellemtiden kan du finde følgende artikler nyttige:
> -  [Teams meddelelser om opbevaringspolitikker](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b)
> - [Anvend opbevaringsnavne på filer i SharePoint eller OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df)
>
> Oplysningerne på denne side er til it-administratorer, der kan oprette opbevaringspolitikker og opbevaringsnavne af hensyn til overholdelse af regler og standarder.

For de fleste organisationer øges mængden og kompleksiteten af deres data dagligt – mails, dokumenter, chatbeskeder og meget mere. Effektiv administration eller styring af disse oplysninger er vigtigt, fordi du skal:

- **Overhold** proaktivt brancheforordninger og interne politikker, der kræver, at du bevarer indhold i en minimumsperiode – f.eks. kan der i Sarbanes-Oxley Act kræves, at du skal bevare visse typer indhold i syv år.

- **Reducer risikoen i tilfælde af procesførelse** eller sikkerhedsbrud ved permanent at slette gammelt indhold, som du ikke længere skal beholde.

- **Hjælp din organisation med at dele viden effektivt og være mere fleksibel** ved at sikre, at dine brugere kun arbejder med indhold, der er aktuelt og relevant for dem.

Opbevaringsindstillinger, som du konfigurerer, kan hjælpe dig med at nå disse mål. Administration af indhold kræver ofte to handlinger:

| Handling| Formål |
|:-----|:-----|
|Behold indhold | Forebyd permanent sletning og forbliver tilgængelig for eDiscovery |
|Slet indhold | Slet indhold fra din organisation permanent|

Med disse to opbevaringshandlinger kan du konfigurere opbevaringsindstillinger for følgende resultater:

- Be behold-kun: Behold indhold i uendelig lang tid eller i en bestemt tidsperiode.
- Kun slette: Slet indhold permanent efter en bestemt tidsperiode.
- Behold og slet derefter: Behold indhold i en bestemt tidsperiode, og slet det derefter permanent.

Disse opbevaringsindstillinger fungerer med indhold på stedet, hvilket sparer dig de ekstra omkostninger ved at oprette og konfigurere ekstra lagerplads, når du har brug for at bevare indhold af hensyn til overholdelse af regler og standarder. Desuden behøver du ikke at implementere tilpassede processer for at kopiere og synkronisere disse data.

Brug følgende afsnit for at få mere at vide om, hvordan opbevaringspolitikker og opbevaringsnavne fungerer, hvornår de skal bruges, og hvordan de supplerer hinanden. Men hvis du er klar til at komme i gang og installere opbevaringsindstillinger for nogle almindelige scenarier, kan du se [Introduktion til informationsstyring](get-started-with-information-governance.md).

## <a name="how-retention-settings-work-with-content-in-place"></a>Sådan fungerer opbevaringsindstillinger med indhold på plads

Når der er tildelt opbevaringsindstillinger til indholdet, forbliver indholdet på dets oprindelige placering. For det meste fortsætter folk med at arbejde med deres dokumenter eller mails, som om der ikke er noget, der er ændret. Men hvis de redigerer eller sletter indhold, der er inkluderet i opbevaringspolitikken, bevares der automatisk en kopi af indholdet.
  
- Til SharePoint og OneDrive: Kopien bevares i **biblioteket til opbevaring af** dokumenter.

- For Exchange postkasser: Kopien bevares i **mappen Genoprettelige** elementer. 

- For Teams og Yammer meddelelser: Kopien bevares i en skjult mappe med navnet **SubstrateHolds** som en undermappe i Exchange **Genoprettelige** elementer.

> [!NOTE]
> Da biblioteket til opbevaring af dokumenter er inkluderet i webstedets lagerkvote, kan det være nødvendigt at øge din lagerplads, når du bruger opbevaringsindstillinger for SharePoint og Microsoft 365 grupper.
> 
Disse sikre placeringer og det bevarede indhold er ikke synlige for de fleste personer. I de fleste tilfælde behøver folk ikke en gang at vide, at deres indhold er underlagt opbevaringsindstillinger.

Du kan finde flere oplysninger om, hvordan opbevaringsindstillinger fungerer for forskellige arbejdsbelastninger, i følgende artikler:

- [Få mere at vide om opbevaring SharePoint og OneDrive](retention-policies-sharepoint.md)
- [Få mere at vide om opbevaring af Microsoft Teams](retention-policies-teams.md)
- [Få mere at vide om opbevaring af Yammer](retention-policies-yammer.md)
- [Få mere at vide om opbevaring af Exchange](retention-policies-exchange.md)

## <a name="retention-policies-and-retention-labels"></a>Opbevaringspolitikker og opbevaringsnavne

Hvis du vil tildele dine opbevaringsindstillinger til indhold, skal **du bruge opbevaringspolitikker** **og opbevaringsetiketter sammen med etiketpolitikker**. Du kan bruge en af disse metoder eller kombinere dem.

Brug en opbevaringspolitik til at tildele de samme opbevaringsindstillinger for indhold på websteds- eller postkasseniveau, og brug en opbevaringsetiket til at tildele opbevaringsindstillinger på et elementniveau (mappe, dokument, mail).

Hvis f.eks. alle dokumenter på et SharePoint-websted skal opbevares i fem år, er det mere effektivt at gøre dette med en opbevaringspolitik end at anvende den samme opbevaringsetiket på alle dokumenter på webstedet. Men hvis nogle dokumenter på webstedet opbevares i 5 år, og andre opbevares i 10 år, vil en opbevaringspolitik ikke kunne gøre dette. Når du har brug for at angive opbevaringsindstillinger på elementniveau, skal du bruge opbevaringsnavne. 

I modsætning til opbevaringspolitikker flytter opbevaringsindstillinger fra opbevaringsmærkater med indholdet, hvis det flyttes til en anden placering i din Microsoft 365 lejer. Desuden har opbevaringsmærkater følgende funktioner, som opbevaringspolitikker ikke understøtter: 
 
- Indstillinger til at starte en opbevaringsperiode fra det tidspunkt, hvor indholdet blev mærket eller baseret på en begivenhed, ud over alderen på indholdet, eller hvornår det sidst blev ændret.

- Brug [klassificeringer, der kan trænes, til](classifier-learn-about.md) at identificere indhold, der skal mærkes.

- Anvend en standardetiket til SharePoint dokumenter.

- Gennemgang [af support](./disposition.md)  disposition for at gennemgå indholdet, før det slettes permanent.

- Markér indholdet som en [post som](records-management.md#records) en del af etiketindstillingerne, og har altid bevis for  [disposition](disposition.md#disposition-of-records) , når indhold slettes i slutningen af dets opbevaringsperiode.

### <a name="retention-policies"></a>Opbevaringspolitikker

Opbevaringspolitikker kan anvendes på følgende placeringer:
- Exchange mail
- SharePoint websted
- OneDrive konti
- Microsoft 365 grupper
- Skype for Business
- Exchange offentlige mapper
- Teams kanalmeddelelser
- Teams chats
- Teams private kanalmeddelelser
- Yammer communitymeddelelser
- Yammer brugermeddelelser

Du kan anvende en enkelt politik meget effektivt på flere placeringer eller på bestemte placeringer eller brugere.

I starten af en opbevaringsperiode kan du vælge, hvornår indholdet blev oprettet eller understøttes kun for filer og placeringerne SharePoint, OneDrive og Microsoft 365 Grupper, da indholdet sidst blev ændret.

Elementer nedarver opbevaringsindstillingerne fra deres beholder, der er angivet i opbevaringspolitikken. Hvis de derefter flyttes uden for den pågældende beholder, når politikken er konfigureret til at bevare indhold, bevares en kopi af det pågældende element på arbejdsmængdens sikrede placering. Opbevaringsindstillingerne tager dog ikke med indholdet på den nye placering. Hvis det er nødvendigt, kan du bruge opbevaringsmærkater i stedet for opbevaringspolitikker.

### <a name="retention-labels"></a>Opbevaringsnavne

Brug opbevaringsnavne til forskellige typer indhold, der kræver forskellige opbevaringsindstillinger. Eksempel:
  
- Momsformularer, der skal bevares i en minimumsperiode. 
    
- Tryk på materialer, der skal slettes permanent, når de når en bestemt alder. 
    
- Konkurrencebaseret research, der skal bevares i en bestemt periode og derefter slettes permanent. 
    
- Arbejdsvisa, der skal være markeret som en post, så de ikke kan redigeres eller slettes. 
    
I alle disse tilfælde kan du bruge opbevaringsmærkater til at anvende opbevaringsindstillinger til styring af kontrol på elementniveau (dokument eller mail).
  
Med opbevaringsmærkater kan du:
  
- **Gør det muligt** for personer i organisationen at anvende en opbevaringsmærkat manuelt på indhold i Outlook og Outlook på internettet, OneDrive, SharePoint og Microsoft 365 grupper. Brugere ved ofte bedst, hvilken type indhold de arbejder med, så de kan klassificere det og få de relevante opbevaringsindstillinger anvendt. 
    
- **Anvend automatisk opbevaringsnavne** på indhold, hvis det opfylder bestemte betingelser, som omfatter vedhæftede filer i skyen, som deles i en mail eller Teams, eller når indholdet indeholder: 
    - Bestemte typer af følsomme oplysninger.
    - Specifikke nøgleord, der svarer til en forespørgsel, du opretter.
    - Mønster matches for en klassificering, der kan trænes.

- **Start opbevaringsperioden fra det tidspunkt**, hvor indholdet blev mærket for dokumenter på SharePoint websteder OneDrive konti og for mailelementer.

- **Start opbevaringsperioden, når en begivenhed indtræffer**, f.eks. medarbejdere forlader organisationen, eller kontrakter udløber.

- **Anvend et** standardopbevaringsnavn på et dokumentbibliotek, en mappe eller et dokumentsæt i SharePoint, så alle dokumenter, der er gemt på denne placering, nedarver standardopbevaringsnavnet.

- **Markér elementer som en post som** en del af din [datastyringsstrategi](records-management.md) . Når det mærkede indhold forbliver i Microsoft 365, sættes der yderligere begrænsninger på det indhold, der kan være nødvendigt af lovmæssige årsager. Få mere at vide under [Sammenlign begrænsninger for, hvilke handlinger der er tilladte eller blokerede](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked).

Opbevaringsmærkater [bevares ikke](sensitivity-labels.md), i modsætning til følsomhedsmærkater, hvis indholdet flyttes Microsoft 365.

#### <a name="classifying-content-without-applying-any-actions"></a>Klassifikation af indhold uden at anvende nogen handlinger

Selvom opbevaringsnavne har som hovedformål at bevare eller slette indhold, kan du også bruge opbevaringsnavne uden at slå opbevaringshandlinger eller andre handlinger til. I dette tilfælde kan du bruge en opbevaringsetiket som en tekstetiket uden at udføre nogen handlinger.
  
Du kan f.eks. oprette og anvende en opbevaringsmærkat med navnet "Gennemse senere" uden handlinger, og derefter bruge denne etiket til at finde indholdet senere.
  
![Navneindstillinger til kun at klassificere.](../media/retention-label-retentionoff.png)

#### <a name="using-a-retention-label-as-a-condition-in-a-dlp-policy"></a>Brug af et opbevaringsnavn som en betingelse i en DLP-politik

Du kan angive et opbevaringsnavn som en betingelse i en politik til forebyggelse af datatab (DLP) for dokumenter SharePoint. Konfigurer f.eks. en DLP-politik for at forhindre dokumenter i at blive delt uden for organisationen, hvis de har en bestemt opbevaringsmærkat anvendt på den.

Få mere at vide under [Brug af en opbevaringsetiket som en betingelse i en DLP-politik](data-loss-prevention-policies.md#using-a-retention-label-as-a-condition-in-a-dlp-policy).

#### <a name="retention-labels-and-policies-that-apply-them"></a>Opbevaringsetiketter og politikker, der anvender dem

Når du publicerer opbevaringsnavne, er de inkluderet  i en opbevaringsetiketpolitik, der gør dem tilgængelige for administratorer og brugere, så de kan anvende dem på indhold. Som det fremgår af nedenstående diagram:

1. En enkelt opbevaringsetiket kan medtages i flere opbevaringspolitikker.

2. Opbevaringsetiketpolitikker angiver de placeringer, som opbevaringsnavnene skal publicere. Den samme placering kan medtages i flere opbevaringsmærkatpolitikker.

![Sådan kan opbevaringsnavne føjes til etiketpolitikker, der angiver placeringer.](../media/retention-labels-and-policies.png)

Du kan også oprette en eller flere politikker **for automatisk anvendelse af opbevaringsmærkater**, hver med en enkelt opbevaringsetiket. Med denne politik anvendes der automatisk en opbevaringsetiket, når de betingelser, du angiver i politikken, er opfyldt.

#### <a name="retention-label-policies-and-locations"></a>Opbevaring etiketpolitikker og placeringer

Opbevaringsnavne kan publiceres på forskellige placeringer, afhængigt af hvad opbevaringsmærkaten gør.
  
| Hvis opbevaringsmærkaten er ... | Derefter kan etiketpolitikken anvendes på... |
|:-----|:-----|
|Publiceret til administratorer og slutbrugere  |Exchange, SharePoint, OneDrive og Microsoft 365 grupper  |
|Automatisk anvendt baseret på følsomme oplysningstyper eller klassificeringer, der kan trænes  |Exchange, SharePoint, OneDrive  |
|Automatisk anvendt baseret på nøgleord eller en forespørgsel  |Exchange, SharePoint, OneDrive og Microsoft 365 grupper  |
|Automatisk anvendt på vedhæftede filer i skyen  |SharePoint, OneDrive, Microsoft 365 grupper  |

Exchange offentlige mapper, Skype, Teams og Yammer understøtter ikke opbevaringsetiketter. Hvis du vil bevare og slette indhold fra disse placeringer, skal du i stedet bruge opbevaringspolitikker.

#### <a name="only-one-retention-label-at-a-time"></a>Kun ét opbevaringsnavn ad gangen

En mail eller et dokument kan kun have en enkelt opbevaringsmærkat anvendt på den ad gangen. En opbevaringsetiket [kan anvendes manuelt](create-apply-retention-labels.md#manually-apply-retention-labels) af en slutbruger eller administrator eller automatisk ved hjælp af en af følgende metoder:

- [Anvend etiketpolitik automatisk](apply-retention-labels-automatically.md)
- [Dokumentforståelsesmodel for SharePoint Syntex](../contentunderstanding/apply-a-retention-label-to-a-model.md)
- [Standardetiket til SharePoint](create-apply-retention-labels.md#applying-a-default-retention-label-to-all-content-in-a-sharepoint-library-folder-or-document-set) eller [Outlook](create-apply-retention-labels.md#applying-a-default-retention-label-to-an-outlook-folder)
- [Outlook regler](create-apply-retention-labels.md#automatically-applying-a-retention-label-to-email-by-using-rules)

For standardopbevaringsnavne (de markerer ikke elementer som [en post eller en lovgivningsmæssig post](records-management.md#records)):

- Administratorer og slutbrugere kan manuelt ændre eller fjerne en eksisterende opbevaringsmærkat, der anvendes på indhold. 

- Når der allerede er anvendt en opbevaringsetiket, fjernes den eksisterende etiket ikke automatisk, og den erstattes ikke af en anden opbevaringsetiket med en mulig undtagelse: Den eksisterende etiket blev anvendt som standardetiket. Når du bruger en standardetiket, er der visse scenarier, hvor den kan erstattes af en anden standardetiket eller fjernes automatisk. 
    
    Du kan finde flere oplysninger om etiketfunktionsmåden, når den anvendes, ved hjælp af en standardetiket:
    - Standardetiket til SharePoint: [Etiketfunktionsmåde, når du bruger en standardetiket til SharePoint](create-apply-retention-labels.md#label-behavior-when-you-use-a-default-label-for-sharepoint)
    - Standardetiket til Outlook: [Anvendelse af et standardopbevaringsnavn på Outlook mappe](create-apply-retention-labels.md#applying-a-default-retention-label-to-an-outlook-folder)

- Hvis der er flere politikker for automatisk anvendelse af navne, der kan anvende en opbevaringsmærkat, og indhold opfylder betingelserne i flere politikker, anvendes opbevaringsnavnet for den ældste politik for automatisk anvendelse af navne (efter oprettelsesdato).

Når opbevaringsnavne markerer elementer som en post eller en lovgivningsmæssig post, ændres disse navne aldrig automatisk. Kun administratorer for beholderen kan manuelt ændre eller fjerne opbevaringsetiketter, der markerer elementer som en post, men ikke lovmæssige poster. Få mere at vide under [Sammenlign begrænsninger for, hvilke handlinger der er tilladte eller blokerede](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked).

#### <a name="monitoring-retention-labels"></a>Overvågning af opbevaringsnavne

Vælg dataklassificering Microsoft 365 Overholdelsescenter siden  Oversigt for at overvåge, hvordan dine opbevaringsmærkater bruges i din lejer, og find ud af, hvor de mærkede elementer er placeret. Du kan finde flere oplysninger, herunder vigtige forudsætninger, under [Få mere at vide om dataklassificering](data-classification-overview.md).

Du kan derefter gå ned i detaljer ved hjælp af [indholdsstifinder](data-classification-content-explorer.md) og [aktivitetsstifinder](data-classification-activity-explorer.md).

> [!TIP]
>Overvej at bruge nogle af de andre dataklassificeringsindsigter, f.eks. klassificerede klassificeringer og typer af følsomme oplysninger, som kan hjælpe dig med at identificere indhold, som du muligvis skal bevare eller slette eller administrere som poster.

#### <a name="using-content-search-to-find-all-content-with-a-specific-retention-label"></a>Brug af indholdssøgning til at finde alt indhold med en bestemt opbevaringsmærkat

Når der er anvendt opbevaringsnavne på indhold, enten af brugere eller automatisk anvendt, kan du bruge indholdssøgning til at finde alle elementer, der har en bestemt opbevaringsetiket anvendt.

Når du opretter en indholdssøgning, skal  du vælge Betingelsen for Opbevaringsetiket og derefter angive det fulde opbevaringsnavn eller en del af navnet og bruge et jokertegn. Du kan finde flere oplysninger [i Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).
  
![Opbevaringsetiketbetingelse.](../media/retention-label-condition.png)


## <a name="compare-capabilities-for-retention-policies-and-retention-labels"></a>Sammenlign funktioner for opbevaringspolitikker og opbevaringsnavne

Brug tabellen nedenfor som en hjælp til at identificere, om du skal bruge en opbevaringspolitik eller en opbevaringsmærkat baseret på egenskaberne.

|Funktion|Opbevaringspolitik |Opbevaringsmærkat|
|:-----|:-----|:-----|:-----|
|Opbevaringsindstillinger, der kan beholdes og derefter slettes, bevares eller kun slettes |Ja |Ja |
|Understøttede arbejdsbelastninger: <br />- Exchange <br />- SharePoint <br />- OneDrive <br />- Microsoft 365 grupper <br />- Skype for Business <br />- Teams<br />- Yammer|<br /> Ja <br /> Ja <br /> Ja <br /> Ja <br /> Ja <br /> Ja <br /> Ja | <br /> Ja, undtagen offentlige mapper <br /> Ja <br /> Ja <br /> Ja <br /> Nej <br /> Nej <br /> Nej |
|Opbevaring anvendes automatisk | Ja | Ja |
|Opbevaring anvendt baseret på betingelser <br /> - følsomme oplysningstyper, KQL-forespørgsler og nøgleord, trænbare klassificeringer, vedhæftede skybaserede filer| Nej | Ja |
|Opbevaring anvendt manuelt | Nej | Ja |
|Interaktion mellem slutbrugere | Nej | Ja |
|Bevares, hvis indholdet flyttes | Nej | Ja, i din Microsoft 365 lejer |
|Erklære element som en post| Nej | Ja |
|Start opbevaringsperioden, når den er mærket eller baseret på en begivenhed | Nej | Ja |
|Gennemgang af disposition | Nej| Ja |
|Dispositionsbevis i op til 7 år | Nej |Ja, når du bruger dispositionsgennemsyn, eller elementet er markeret som en post|
|Overvågningsadministratoraktiviteter| Ja | Ja|
|Overvågningsopbevaringshandlinger| Nej | Ja <sup>\*</sup> |
|Identificer elementer, der er underlagt opbevaring: <br /> - Indholdssøgning <br /> - Siden Dataklassificering, Indholdsstifinder, Aktivitetsstifinder | <br /> Nej <br /> Nej | <br /> Ja <br /> Ja|

**Fodnote:**

<sup>\*</sup>For opbevaringsnavne, der ikke markerer indholdet som en post eller lovgivningspost, er overvågningshændelser begrænset til, når et element i SharePoint eller OneDrive har en etiket anvendt, ændret eller fjernet. Hvis du vil have mere at vide om overvågning af opbevaringsnavne, skal du [se afsnittet Overvågning af opbevaringshandlinger](#auditing-retention-actions) på denne side.

### <a name="combining-retention-policies-and-retention-labels"></a>Kombination af opbevaringspolitikker og opbevaringsnavne

Du behøver ikke at vælge mellem kun at bruge opbevaringspolitikker eller kun at bruge opbevaringsnavne. Begge metoder kan bruges sammen og faktisk supplere hinanden for at finde en mere omfattende løsning.

Følgende eksempler er blot nogle af de måder, hvorpå du kan kombinere opbevaringspolitikker og opbevaringsnavne på den samme placering.

Du kan finde flere oplysninger om, hvordan opbevaringspolitikker og opbevaringsnavne fungerer sammen, og hvordan du fastlægger deres kombinerede resultat, i afsnittet på denne side, der forklarer principperne for opbevaring, og hvad der [har forrang](#the-principles-of-retention-or-what-takes-precedence).

**Eksempel, hvor brugere tilsidesætter automatisk sletning**

Scenarie: Som standard slettes indhold i OneDrive-konti automatisk efter fem år, men brugerne skal have mulighed for at tilsidesætte dette for bestemte dokumenter.

1. Du opretter og konfigurerer en opbevaringspolitik, der automatisk sletter indhold fem år efter, det sidst er ændret, og anvender politikken på alle OneDrive konti.

2. Du opretter og konfigurerer et opbevaringsnavn, der bevarer indholdet uendeligt, og føjer dette til en etiketpolitik, som du publicerer på alle OneDrive konti. Du forklarer over for brugerne, hvordan du manuelt anvender denne etiket på bestemte dokumenter, der skal udelades fra automatisk sletning, hvis den ikke ændres efter fem år.

**Eksempel på, hvordan du bevarer elementer i længere tid**

Scenarie: Elementer SharePoint som standard automatisk og slettes derefter efter fem år, men dokumenter i bestemte biblioteker skal bevares i ti år.

1. Du opretter og konfigurerer en opbevaringspolitik, der automatisk bevarer og derefter sletter indhold efter fem år, og anvender politikken på alle SharePoint- Microsoft 365-gruppeforekomster.

2. Du opretter og konfigurerer en opbevaringsetiket, der automatisk bevarer indhold i ti år. Du publicerer denne etiket SharePoint webstedsadministratorer, så de kan anvende den som et standardnavn, der skal nedarves af alle elementer i bestemte dokumentbiblioteker.

**Eksempel på sletning af elementer i en kortere tidsperiode**

Scenarie: Mails bevares som standard ikke, men slettes automatisk efter ti år. Mails, der er relateret til et bestemt projekt, der har et navn på en foreløbige kode, skal dog slettes automatisk efter et år.

1. Du opretter og konfigurerer en opbevaringspolitik, der automatisk sletter indhold efter ti år, og anvender politikken på alle Exchange modtagere.

2. Du opretter og konfigurerer en opbevaringsetiket, der automatisk sletter indhold efter et år. Mulighederne for at anvende denne etiket på relevante mails omfatter:
    - Du opretter en politik for automatisk mærkater, der identificerer indhold ved at bruge projektkodenavnet som nøgleordet, og anvender politikken på alle Exchange modtagere
    - Du publicerer navnet og fortæller de brugere, der er involveret i projektet, hvordan du opretter en automatisk Outlook, der anvender denne etiket
    - Du publicerer navnet og instruerer brugerne i at oprette en mappe i Outlook for alle mails, der er relateret til projektet, og de anvender den publicerede etiket på mappen og opretter derefter en Outlook-regel for at flytte alle projektrelaterede mails til denne mappe

## <a name="how-long-it-takes-for-retention-settings-to-apply"></a>Hvor lang tid det tager at anvende opbevaringsindstillinger

Når du indsender opbevaringspolitikker for arbejdsbelastninger og etiketpolitikker til automatisk at anvende en opbevaringsmærkat, kan der gå op til 7 dage, før opbevaringsindstillingerne anvendes på indhold:

- [Hvor lang tid det tager at opbevaringspolitikkerne træder i kraft](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect)
- [Hvor lang tid det tager, før opbevaringsetiketter træder i kraft](apply-retention-labels-automatically.md#how-long-it-takes-for-retention-labels-to-take-effect)

På samme måde kan der gå op til 7 dage, før opbevaringsetiketter er synlige i apps, når du publicerer etiketterne:

- [Når opbevaringsnavne bliver tilgængelige til anvendelse](create-apply-retention-labels.md#when-retention-labels-become-available-to-apply)

Politikkerne træder ofte i kraft, og etiketterne vil være synlige hurtigere end 7 dage. Men med mange potentielle variabler, der kan påvirke denne proces, er det bedst at planlægge maksimalt syv dage.

## <a name="adaptive-or-static-policy-scopes-for-retention"></a>Tilpassede eller statiske politikomfang for opbevaring

Når du opretter en opbevaringspolitik eller en opbevaringsetiketpolitik, skal du vælge mellem tilpasset og statisk for at definere politikkens omfang.

- Et **tilpasset omfang anvender** en forespørgsel, som du angiver, så medlemskabet er ikke statisk, men dynamisk ved at køre dagligt i forhold til de attributter eller egenskaber, du angiver for de valgte placeringer. Du kan bruge flere tilpassede områder med en enkelt politik.
    
    Eksempel: Mails og OneDrive for ledere kræver en længere opbevaringsperiode end almindelige brugere. Du opretter en opbevaringspolitik med et tilpasset omfang, der bruger Azure AD-attributtens stillingsbetegnelse "Ledelse", og derefter vælger placeringerne Exchange-mail- og OneDrive-konti til politikken. Der er ingen grund til at angive mailadresser OneDrive URL-adresser for disse brugere, fordi det tilpassede omfang automatisk henter disse værdier. For nye ledere er der ingen grund til at omkonfigurere opbevaringspolitikken, fordi disse nye brugere med deres tilsvarende værdier for mail og OneDrive automatisk hentes op.

- Et **statisk omfang** bruger ikke forespørgsler og er begrænset i konfigurationen, da det kan gælde for alle forekomster for en bestemt placering eller bruge inklusion og udeladelse for bestemte forekomster for den pågældende placering. Disse tre valgmuligheder kaldes sommetider for henholdsvis "organisation", "omfatter" og "udelader".
    
    Eksempel: Mails og OneDrive for ledere kræver en længere opbevaringsperiode end almindelige brugere. Du opretter en opbevaringspolitik med et statisk omfang, der vælger Exchange mail- OneDrive-kontisplaceringer for politikken. For mailplaceringen Exchange, kan du identificere en gruppe, der kun indeholder ledere, så du skal angive denne gruppe for opbevaringspolitikken, og gruppemedlemskab med de respektive mailadresser hentes, når politikken oprettes. For placeringen OneDrive-konti skal du identificere og derefter angive individuelle OneDrive URL-adresser for hver leder. For nye ledere skal du omkonfigurere opbevaringspolitikken for at tilføje de nye mailadresser og OneDrive URL-adresser. Du skal også opdatere URL-OneDrive når som helst der sker en ændring i en leders UPN.
    
    OneDrive er særligt udfordrende at angive, fordi disse URL-adresser som standard ikke oprettes, før brugeren får adgang til deres OneDrive første gang. Og hvis en brugers UPN ændres, hvilket du måske ikke kender til, ændres brugerens OneDrive automatisk.

Fordele ved at bruge adaptive områder:

- Ingen grænser for [antallet af elementer pr. politik](retention-limits.md#maximum-number-of-items-per-policy). Selvom adaptive politikker stadig er underlagt det maksimale [](retention-limits.md#maximum-number-of-policies-per-tenant) antal politikker pr. lejers begrænsninger, vil den mere fleksible konfiguration sandsynligvis resultere i langt færre politikker.

- Mere effektiv målretning til dine opbevaringskrav. Du kan f.eks. tildele forskellige opbevaringsindstillinger til brugere ud fra deres geografiske placering ved hjælp af eksisterende Azure AD-attributter uden administrative omkostninger til at oprette og vedligeholde grupper til dette formål.

- Forespørgselsbaseret medlemskab giver fleksibilitet i forhold til forretningsændringer, der muligvis ikke afspejles i gruppemedlemskab eller eksterne processer, der er afhængige af kommunikation på tværs af afdelinger.

- En enkelt opbevaringspolitik kan omfatte placeringer til både Microsoft Teams og Yammer, hvorimod når du bruger et statisk omfang, kræver disse placeringer deres egen opbevaringspolitik.
    
- Du kan anvende bestemte opbevaringsindstillinger til kun inaktive postkasser. Denne konfiguration er ikke mulig med et statisk omfang, da statiske områder på det tidspunkt, hvor politikken tildeles, ikke understøtter specifik inklusion af modtagere med inaktive postkasser.

Fordele ved at bruge statiske områder:

- Enklere konfiguration, hvis du vil have, at alle forekomster vælges automatisk til en arbejdsbelastning.
    
    For "omfatter" og "udelader" kan dette valg være en enklere konfiguration, hvis antallet af forekomster, du skal angive, er lavt og ikke ændres. Men når antallet af forekomster begynder at stige, og du har hyppige ændringer i organisationen, der kræver, at du konfigurerer dine politikker igen, kan det være nemmere at konfigurere tilpassede områder og nemmere at vedligeholde.

- **Placeringerne Skype for Business** **og Exchange offentlige** mapper understøtter ikke adaptive områder. For disse placeringer skal du bruge et statisk omfang. 

Du kan finde konfigurationsoplysninger [under Konfiguration af tilpassede områder](retention-settings.md#configuration-information-for-adaptive-scopes).

Hvis du vil se et optaget webinar (kræver registrering), skal du [gå til Deep Dive om tilpassede områder](https://mipc.eventbuilder.com/event/45703).

> [!IMPORTANT]
> Adaptive områder understøtter i øjeblikket ikke Preservation Lock for at begrænse [ændringer i opbevaringspolitikker og politikker for opbevaringsmærkater](#use-preservation-lock-to-restrict-changes-to-policies).

## <a name="policy-lookup"></a>Politikopslag

Du kan konfigurere flere opbevaringspolitikker for Microsoft 365 opbevaringsplaceringer samt flere politikker for opbevaringsmærkater, som du publicerer eller anvender automatisk. Hvis du vil finde de politikker for opbevaring, der er tildelt bestemte brugere, websteder og Microsoft 365-grupper, skal du  bruge Politikopslag fra  løsningen til styring af oplysninger i Microsoft 365 Overholdelsescenter:

![Politikopslag til at finde de politikker for opbevaring, der er tildelt til bestemte brugere, websteder og Microsoft 365 grupper ](../media/policy-lookup.png)

Du skal angive den nøjagtige mailadresse for en bruger, den nøjagtige URL-adresse for et websted eller den nøjagtige mailadresse for Microsoft 365 gruppe.

Indstillingen for websteder omfatter OneDrive konti. Hvis du vil have mere at vide om, hvordan du angiver URL-adressen til en OneDrive-konto, skal du se Få en liste over alle [OneDrive-webadresser i organisationen](/onedrive/list-onedrive-urls).

## <a name="the-principles-of-retention-or-what-takes-precedence"></a>Principperne for opbevaring, eller hvad der kræver forrang?

I modsætning til opbevaringsnavne kan du anvende mere end én opbevaringspolitik på det samme indhold. Hver opbevaringspolitik kan resultere i en bevarelseshandling og en sletningshandling. Desuden kan det pågældende element også være underlagt disse handlinger fra en opbevaringsetiket.

Når elementer kan være underlagt flere opbevaringsindstillinger, som kan skabe konflikt med hinanden, er det i dette scenarie, hvad der har forrang til at bestemme resultatet?

Resultatet er ikke hvilken enkelt opbevaringspolitik eller enkelt opbevaringsmærkat, der vinder, men hvor lang tid et element opbevares (hvis relevant), og hvornår et element slettes (hvis det er relevant). Disse to handlinger beregnes uafhængigt af hinanden i forhold til alle de opbevaringsindstillinger, der anvendes på et element.

Et element kan f.eks. være underlagt én opbevaringspolitik, der er konfigureret til en handling, der kun kan slettes, og en anden opbevaringspolitik, der er konfigureret til at beholde og derefter slette. Dette element har derfor kun én bevarelseshandling, men to slettehandlinger. Opbevarings- og sletningshandlingerne kan være i konflikt med hinanden, og de to sletningshandlinger kan have en modstridende dato. Principperne for opbevaring forklarer resultatet.

På et højt niveau kan du være sikker på, at opbevaring altid har forrang over permanent sletning og den længste opbevaringsperiode vinder. Disse to enkle regler bestemmer altid, hvor længe et element opbevares.

Der er flere faktorer, der bestemmer, hvornår et element slettes permanent, hvilket omfatter sletningshandlingen fra et opbevaringsnavn, tilsidesætter altid sletningshandlingen fra en opbevaringspolitik.

Brug følgende flow til at forstå opbevarings- og sletningsresultaterne for et enkelt element, hvor hvert niveau fungerer som en slipser for konflikter fra top til bund. Hvis resultatet bestemmes af det første niveau, fordi der ikke er flere konflikter, er der ingen grund til at gå videre til næste niveau osv.

> [!IMPORTANT]
> Hvis du bruger opbevaringsmærkater: Før du anvender principperne for at fastlægge resultatet af flere opbevaringsindstillinger på det samme element, skal du sikre dig, at du ved, hvilken opbevaringsetiket [der anvendes](#only-one-retention-label-at-a-time).

![Diagram over principperne for opbevaring.](../media/principles-of-retention.png)

Før du forklarer hvert princip nærmere, er det vigtigt at forstå forskellen mellem opbevaringsperioden for elementet vs. den angivne opbevaringsperiode i opbevaringspolitikken eller opbevaringsmærkaten. Dette skyldes, at selvom standardkonfigurationen er at starte opbevaringsperioden, når et element oprettes, så slutningen af en opbevaringsperiode er fast for elementet, understøtter filer også konfigurationen til at starte opbevaringsperioden fra det tidspunkt, hvor filen sidst blev ændret. Med denne alternative konfiguration nulstilles starten af en opbevaringsperiode, hver gang filen ændres, hvilket forlænger opbevaringsperiodens afslutning for elementet. Opbevaringsnavne understøtter også start af opbevaringsperioden, når de er mærket og ved starten af en begivenhed.

Hvis du vil anvende principperne i praksis med en række Ja- og Nej-spørgsmål, kan du også [bruge opbevaringsr rutediagrammet](retention-flowchart.md).

Forklaring til de fire forskellige principper:
  
1. **Opbevaringssejre over sletning.** Indhold slettes ikke permanent, når det også har opbevaringsindstillinger til at bevare det. Selvom dette princip sikrer, at indhold bevares af hensyn til overholdelse af regler og standarder, kan sletningsprocessen stadig startes (startet af brugeren eller systemet) og kan derfor fjerne indholdet fra brugernes primære visning. Permanent sletning er dog suspenderet. Du kan finde flere oplysninger om, hvordan og hvor indhold bevares, ved at bruge følgende links for hver arbejdsbyrde:
    
    - [Sådan fungerer opbevaring til SharePoint og OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive)
    - [Sådan fungerer opbevaring med Microsoft Teams](retention-policies-teams.md#how-retention-works-with-microsoft-teams)
    - [Sådan fungerer opbevaring med Yammer](retention-policies-yammer.md#how-retention-works-with-yammer)
    - [Sådan fungerer opbevaring for Exchange](retention-policies-exchange.md#how-retention-works-for-exchange)
    
    Eksempel **på** dette første princip: En mail er underlagt en opbevaringspolitik for Exchange, der er konfigureret til at slette elementer tre år efter, de er oprettet, og den har også en opbevaringsmærkat, der er konfigureret til at bevare elementer fem år efter, de er oprettet.
    
    Mailen bevares i fem år, fordi denne opbevaringshandling tilsidesætter sletning. Mailen slettes permanent i slutningen af de fem år på grund af den slettede handling, der blev afbrudt, mens opbevaringshandlingen var i kraft.

2. **Den længste opbevaringsperiode vinder.** Hvis indhold er underlagt flere opbevaringsindstillinger, der bevarer indhold i forskellige tidsperioder, bevares indholdet indtil slutningen af den længste opbevaringsperiode for elementet.
    
    > [!NOTE]
    > Det er muligt at have en opbevaringsperiode på 5 år i en opbevaringspolitik eller etiket, der vinder over en opbevaringsperiode på 7 år i en opbevaringspolitik eller -etiket, fordi perioden på fem år er konfigureret til at starte baseret på, hvornår filen sidst er ændret, og 7-årsperioden er konfigureret til at starte fra det tidspunkt, hvor filen oprettes.
    
    **Eksempel på dette andet princip**: Dokumenter i marketingwebstedet SharePoint underlagt to opbevaringspolitikker. Den første opbevaringspolitik konfigureres for alle SharePoint til at bevare elementer i fem år, efter de er oprettet. Den anden opbevaringspolitik er konfigureret til bestemte SharePoint til at bevare elementer i ti år, efter de er oprettet.
    
    Dokumenter på dette marketingwebsted SharePoint i ti år, fordi det er den længste opbevaringsperiode for elementet.

3. **Eksplicitte vindere over implicitte sletninger.** Når konflikter nu er løst i forbindelse med opbevaring, er det kun konflikter ved sletning, der forbliver: 
    
    1. En opbevaringsmærkat (som den var anvendt) giver eksplicit opbevaring i sammenligning med opbevaringspolitikker, fordi opbevaringsindstillingerne anvendes på et enkelt element i stedet for implicit tildelt fra en beholder. Det betyder, at en sletningshandling fra en opbevaringsetiket altid tilsidesætter en sletningshandling fra en opbevaringspolitik.
        
        **Eksempel på dette** tredje princip (etiket): Et dokument er underlagt to opbevaringspolitikker, der har en sletningshandling på henholdsvis fem år og ti år samt en opbevaringsetiket, der har en slettehandling på syv år.
        
        Dokumentet slettes permanent efter syv år, fordi sletningen fra opbevaringsetiketten har forrang.
    
    2. Når du kun har opbevaringspolitikker: Hvis en opbevaringspolitik for en placering bruger et tilpasset omfang eller et statisk omfang, der indeholder bestemte forekomster (f.eks. bestemte brugere til Exchange-mail), tilsidesætter denne opbevaringspolitik et statisk omfang, der er konfigureret for alle forekomster for den samme placering.
        
        Et statisk omfang, der er konfigureret for alle forekomster for en placering, kaldes nogle gange en "politik for hele organisationen". Eksempelvis kan **Exchange mail** og standardindstillingen **alle modtagere**. Eller du **SharePoint websteder** og standardindstillingen **Alle websteder**. Når opbevaringspolitikker ikke er for hele organisationen, men er konfigureret med et tilpasset omfang eller et statisk omfang, der omfatter bestemte forekomster, har de samme rangfølge på dette niveau.
        
        **Eksempel 1 for dette tredje princip (politikker)**: En mail er underlagt to opbevaringspolitikker. Den første opbevaringspolitik er unscoped og sletter elementer efter ti år. Den anden opbevaringspolitik er begrænset til bestemte postkasser og sletter elementer efter fem år.
        
        Mailen slettes permanent efter fem år, fordi sletningshandlingen fra den omfangsbaserede opbevaringspolitik tilsidesætter opbevaringspolitikken for hele organisationen.
        
        **Eksempel 2 for dette tredje princip (politikker)**: Et dokument i en OneDrive-konto er underlagt to opbevaringspolitikker. Den første opbevaringspolitik er begrænset til at medtage denne brugers OneDrive-konto og har en sletningshandling efter 10 år. Den anden opbevaringspolitik er begrænset til at medtage denne brugers OneDrive og har en slettehandling efter syv år.
        
        Når dette dokument slettes permanent, kan det ikke bestemmes på dette niveau, da begge opbevaringspolitikker er fastsat til at omfatte bestemte forekomster.

4. **Den korteste sletningsperiode vinder.** Gældende for at bestemme, hvornår elementer slettes fra opbevaringspolitikker, og resultatet kunne ikke løses fra det forrige niveau: Indhold slettes permanent i slutningen af den korteste opbevaringsperiode for elementet.
    
    > [!NOTE]
    > Det er muligt, at en opbevaringspolitik, der har en opbevaringsperiode på 7 år, vinder over en opbevaringspolitik på 5 år, fordi den første politik er konfigureret til at starte opbevaringsperioden baseret på, hvornår filen oprettes, og den anden opbevaringspolitik fra da filen sidst blev ændret.
    
    **Eksempel på dette fjerde princip**: Et dokument i en brugers OneDrive-konto er underlagt to opbevaringspolitikker. Den første opbevaringspolitik er begrænset til at medtage denne brugers OneDrive-konto og har en sletningshandling 10 år efter, at filen er oprettet. Den anden opbevaringspolitik er begrænset til at medtage denne brugers OneDrive-konto og har en sletningshandling på syv år, efter filen er oprettet.
    
    Dette dokument slettes permanent efter syv år, fordi det er den korteste opbevaringsperiode for elementet fra disse to omfangsbelagte opbevaringspolitikker.

Elementer, der er underlagt eDiscovery-hold, falder også ind under det første princip for opbevaring; de kan ikke slettes permanent med nogen opbevaringspolitik eller opbevaringsmærkat. Når denne venteposition frigives, gælder principperne for opbevaring fortsat for dem. De kan f.eks. være underlagt en ikke-udgået opbevaringsperiode eller en sletningshandling.

### <a name="principles-of-retention-examples-that-combine-retain-and-delete-actions"></a>Principper for opbevaringsekseler, der kombinerer bevarelses- og sletningshandlinger

Følgende eksempler er mere komplekse for at illustrere principperne for opbevaring, når forskellige opbevarings- og sletningshandlinger kombineres. For at gøre det nemmere at følge eksemplerne bruger alle opbevaringspolitikker og -etiketter standardindstillingen for at starte en opbevaringsperiode, når elementet oprettes, så slutningen af en opbevaringsperiode er den samme for elementet.

1. Et element har følgende opbevaringsindstillinger anvendt:
    
    - En opbevaringspolitik for kun at blive slettet efter fem år
    - En opbevaringspolitik, der bevares i tre år og derefter slettes
    - En opbevaringsmærkat, der kun kan opbevares i syv år
    
    **Resultat**: Elementet bevares i syv år, fordi opbevaring har forrang over sletningen, og syv år er den længste opbevaringsperiode for elementet. I slutningen af denne opbevaringsperiode slettes elementet permanent på grund af sletningshandlingen fra opbevaringspolitikkerne.
    
    Selvom de to opbevaringspolitikker har forskellige datoer for sletningshandlingerne, er den tidligste, at elementet kan slettes permanent, ved slutningen af den længste opbevaringsperiode, som er længere end begge sletningsdatoer. 

2.  Et element har følgende opbevaringsindstillinger anvendt:
    
    - En opbevaringspolitik, der kun slettes efter ti år
    - En opbevaringspolitik, der er begrænset til bestemte forekomster, der bevares i fem år og derefter slettes
    - En opbevaringsmærkat, der kan opbevares i tre år og derefter slettes
    
    **Resultat**: Elementet bevares i fem år, fordi det er den længste opbevaringsperiode for elementet. Ved slutningen af den pågældende opbevaringsperiode slettes elementet permanent på grund af sletningen på tre år fra opbevaringsmærkaten. Sletning fra opbevaringsnavne tilsidesætter sletning fra alle opbevaringspolitikker. I dette eksempel løses alle konflikter på tredje niveau.

## <a name="use-preservation-lock-to-restrict-changes-to-policies"></a>Brug Preservation Lock til at begrænse ændringer i politikker

Nogle organisationer skal muligvis overholde de regler, der er defineret af lovgivningsmæssige organisationer, f.eks. Securities and Exchange Commission (SEC) Rule 17a-4, som kræver, at når en opbevaringspolitik er slået til, kan den ikke deaktiveres eller gøres mindre restriktiv. 

Bevarelseslås sikrer, at din organisation kan opfylde disse lovmæssige krav, fordi den låser en opbevaringspolitik eller opbevaringsmærkatpolitik, så ingen – herunder en administrator – kan deaktivere politikken, slette politikken eller gøre den mindre restriktiv.
  
Du anvender Preservation Lock, når opbevaringspolitikken eller opbevaringsmærkatpolitikken er oprettet. Du kan finde flere oplysninger og instruktioner under [Brug Bevarelseslås til at begrænse ændringer i opbevaringspolitikker og politikker for opbevaringsmærkater](retention-preservation-lock.md).

## <a name="releasing-a-policy-for-retention"></a>Udgive en politik til opbevaring

Når du leverer dine politikker for opbevaring, der ikke har en Opbevaringslås, kan du når som helst slette dine politikker, hvilket effektivt deaktiverer opbevaringsindstillingerne for en opbevaringspolitik, og opbevaringsmærkater kan ikke længere anvendes fra opbevaringsetiketpolitikker. Eventuelle tidligere anvendte opbevaringsnavne bevares med deres konfigurerede opbevaringsindstillinger, og for disse etiketter kan du stadig opdatere opbevaringsperioden, når den ikke er baseret på, hvornår elementerne blev mærket.

Du kan også beholde en politik, men ændre placeringsstatus til fra eller deaktivere politikken. En anden mulighed er at omkonfigurere politikken, så den ikke længere omfatter bestemte brugere, websteder, grupper osv. 

Yderligere oplysninger om bestemte placeringer:

- **SharePoint websteder og OneDrive-konti:**
    
    Når du frigiver en opbevaringspolitik for SharePoint-websteder og OneDrive-konti, bevares indhold, der er underlagt opbevaring fra politikken, fortsat i 30 dage for at forhindre utilsigtede datatab. I denne udvidede periode på 30 dage bevares slettede filer stadig (filer vil fortsat blive føjet til biblioteket til opbevaring af dokumenter), men timerjobbet, der med jævne mellemrum rydder op i biblioteket til opbevaring af dokumenter, suspenderes for disse filer, så du kan gendanne dem, hvis det er nødvendigt.
    
    En undtagelse fra denne udvidede periode på 30 dage er, når du opdaterer politikken til at udelade et eller flere websteder til SharePoint eller konti for OneDrive. I dette tilfælde sletter timerjobbet filer for disse placeringer i biblioteket til opbevaring af dokumenter uden forsinkelse på 30 dage.
    
    Du kan finde flere oplysninger om biblioteket til opbevaring af dokumenter [under Sådan fungerer opbevaring for SharePoint og OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).
    
    På grund af funktionsmåden i den udvidede periode, hvis du genaktiverer politikken eller ændrer placeringsstatus tilbage til den inden for 30 dage, genoptages politikken uden permanent datatab i dette tidsrum.

- **Exchange mail og Microsoft 365 grupper**
    
    Når du frigiver en opbevaringspolitik for postkasser, der [er inaktive](inactive-mailboxes-in-office-365.md) på det tidspunkt, hvor politikken frigives:
    
    - Hvis opbevaringspolitikken eksplicit anvendes på en postkasse, gælder opbevaringsindstillingerne ikke længere. Når der ikke er anvendt opbevaringsindstillinger, kan en inaktiv postkasse blive berettiget til automatisk sletning på normal vis.
        
        En eksplicit opbevaringspolitik kræver enten et tilpasset politikområde eller et statisk politikområde med en konfiguration, der angivne en aktiv postkasse på det tidspunkt, hvor politikken blev anvendt, og senere blev inaktiv
    
    - Hvis opbevaringspolitikken implicit anvendes på en postkasse, og den konfigurerede opbevaringshandling er at bevare, gælder opbevaringspolitikken fortsat, og en inaktiv postkasse bliver aldrig berettiget til automatisk sletning. Når opbevaringshandlingen ikke længere er gældende, fordi opbevaringsperioden er udløbet, kan den Exchange administrator nu [manuelt slette den inaktive postkasse](delete-an-inactive-mailbox.md)
        
        En implicit opbevaringspolitik kræver et statisk politikområde med Alle **modtagere (for** Exchange mail) eller **Alle grupper (** for Microsoft 365 Gruppe)-konfiguration.
    
    Du kan finde flere oplysninger om inaktive postkasser, hvor der er anvendt opbevaringspolitikker, under [Inaktive postkasser Microsoft 365 opbevaring](inactive-mailboxes-in-office-365.md#inactive-mailboxes-and-microsoft-365-retention).

## <a name="auditing-retention-configuration-and-actions"></a>Overvågning af opbevaringskonfiguration og handlinger

Når [overvågning er aktiveret](turn-audit-log-search-on-or-off.md), understøttes overvågning af hændelser for opbevaring både af administrationskonfiguration (opbevaringspolitikker og opbevaringsnavne) og opbevaringshandlinger (kun opbevaringsnavne).

### <a name="auditing-retention-configuration"></a>Overvågning af opbevaringskonfiguration

Administratorkonfiguration for opbevaringspolitikker og opbevaringsnavne logføres som overvågningshændelser, når en opbevaringspolitik eller -etiket oprettes, omkonfigureres eller slettes.

Du kan se en komplet liste over overvågningshændelser under [Opbevaringspolitik og aktiviteter med opbevaringsmærkater](search-the-audit-log-in-security-and-compliance.md#retention-policy-and-retention-label-activities).

### <a name="auditing-retention-actions"></a>Overvågning af opbevaringshandlinger

Opbevaringshandlinger, der logføres som overvågningshændelser, er kun tilgængelige for opbevaringsnavne og ikke for opbevaringspolitikker:

- Når en opbevaringsetiket anvendes, ændres eller fjernes fra et element i SharePoint eller OneDrive:
    - Fra **Fil- og sideaktiviteter skal** du vælge **Ændret opbevaringsnavn for en fil** 

- Når et mærket element i SharePoint er markeret som en post, og det låses op eller låst af en bruger:
    - Fra **Fil- og sideaktiviteter skal** du **vælge Ændret poststatus til ulåst** og **Ændret poststatus til låst**

- Når et opbevaringsnavn, der markerer indhold som en post eller lovgivningsmæssig post, anvendes på et element i Exchange:
    - Fra **Exchange du vælge** Mærket **meddelelse som en post**

- Når et mærket element i SharePoint, OneDrive eller Exchange er markeret som en post eller lovgivningsmæssig post, og den slettes permanent:
    - Fra **Fil- og sideaktiviteter skal** du vælge **Slettet fil, der er markeret som en post**

- Når en dispositions gennemgår tager handling for et element, der er nået slutningen af sin opbevaringsperiode:
    -  Fra **Dispositionsgennemsynsaktiviteter** skal **du vælge Godkendt** afhændelse, **Udvidet opbevaringsperiode****, Vare** med nyt navn eller Tilføjede **korrekturlæsere**

## <a name="powershell-cmdlets-for-retention-policies-and-retention-labels"></a>PowerShell-cmdlet'er til opbevaringspolitikker og opbevaringsnavne

Hvis du vil bruge opbevarings-cmdletterne, skal du først oprette forbindelse [til Office 365 Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell). Brug derefter en af følgende cmdlet'er:

- [Get-ComplianceTag](/powershell/module/exchange/get-compliancetag)

- [New-ComplianceTag](/powershell/module/exchange/new-compliancetag)

- [Remove-ComplianceTag](/powershell/module/exchange/remove-compliancetag)

- [Set-ComplianceTag](/powershell/module/exchange/set-compliancetag)

- [Enable-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage)

- [Get-ComplianceTagStorage](/powershell/module/exchange/get-compliancetagstorage)

- [Get-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/get-recordreviewnotificationtemplateconfig)

- [Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy)

- [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy)

- [Remove-RetentionCompliancePolicy](/powershell/module/exchange/remove-retentioncompliancepolicy)

- [Set-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/set-recordreviewnotificationtemplateconfig)

- [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy)

- [Get-RetentionComplianceRule](/powershell/module/exchange/get-retentioncompliancerule)

- [New-RetentionComplianceRule](/powershell/module/exchange/new-retentioncompliancerule)

- [Remove-RetentionComplianceRule](/powershell/module/exchange/remove-retentioncompliancerule)

- [Set-RetentionComplianceRule](/powershell/module/exchange/set-retentioncompliancerule)


## <a name="when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds"></a>Hvornår skal jeg bruge opbevaringspolitikker og opbevaringsmærkater eller eDiscovery-venterum?

Selvom opbevaringsindstillinger og vente hold, som du opretter med en [eDiscovery-sag](create-ediscovery-holds.md) , både kan forhindre, at data slettes permanent, er de designet til forskellige scenarier. For at hjælpe dig med at forstå forskellene og beslutte, hvilken du skal bruge, skal du bruge følgende vejledning:

- Opbevaringsindstillinger, som du angiver i opbevaringspolitikker og opbevaringsetiketter, er designet til en langsigtet strategi for informationsstyring til at bevare eller slette data i forbindelse med overholdelseskrav. Omfanget er normalt bredt med det primære fokus at være placering og indhold i stedet for individuelle brugere. Starten og slutningen af en opbevaringsperiode kan konfigureres med mulighed for automatisk at slette indhold uden yderligere handling fra administratoren.

- Vente hold for eDiscovery (enten Core eDiscovery- eller Advanced eDiscovery-sager) er designet til en begrænset varighed for at bevare data til en juridisk undersøgelse. Omfanget er specifikt med det fokus, der ejes af identificerede brugere. Starten og slutningen af opbevaringsperioden kan ikke konfigureres, men afhænger af individuelle administratorhandlinger, uden mulighed for automatisk at slette indhold, når ventepositionen frigives.

Oversigt, der sammenligner opbevaring med ventende opbevaring:

|Overvejelse|Opbevaring |eDiscovery-vente hold|
|:-----|:-----|:-----|:-----|
|Virksomhedsmæssige behov: |Overholdelse af regler og standarder |Juridiske oplysninger |
|Tidsomfang: |Langsigtet |Kortsigtet |
|Fokus: |Bred, indholdsbaseret |Specifik, brugerbaseret |
|Konfigurerbar start- og slutdato: |Ja |Nej |
|Sletning af indhold: |Ja (valgfrit) |Nej |
|Administrative omkostninger: |Lav |Høj |

Hvis indhold er underlagt både opbevaringsindstillinger og en eDiscovery-venteposition, har det altid forrang at bevare indhold til eDiscovery-venteposition. På denne måde [udvider principperne for](#the-principles-of-retention-or-what-takes-precedence) opbevaring sig til eDiscovery-ventepositioner, fordi de bevarer data, indtil en administrator manuelt udgiver ventepositionen. Men på trods af denne rangfølge skal du ikke bruge eDiscovery-ventende ord til langsigtet informationsstyring. Hvis du er bekymret for automatisk sletning af data, kan du konfigurere opbevaringsindstillinger til at bevare elementer uendeligt[](disposition.md#disposition-reviews), eller du kan bruge dispositionsgennemsyn med opbevaringsnavne.

Hvis du bruger ældre eDiscovery-værktøjer til at bevare data, skal du se følgende ressourcer:

- Exchange: 
    - [In-Place Hold and Litigation Hold](/exchange/security-and-compliance/in-place-and-litigation-holds)
    - [Sådan identificeres den type venteposition, der er sat på en Exchange Online postkasse](./identify-a-hold-on-an-exchange-online-mailbox.md)

- SharePoint og OneDrive: 
    - [Føj indhold til en sag, og sæt kilder i venteposition i eDiscovery-centeret](/SharePoint/governance/add-content-to-a-case-and-place-sources-on-hold-in-the-ediscovery-center)

- [Tilbagetrækning af ældre eDiscovery-værktøjer](legacy-ediscovery-retirement.md)

## <a name="use-retention-policies-and-retention-labels-instead-of-older-features"></a>Brug opbevaringspolitikker og opbevaringsmærkater i stedet for ældre funktioner

Hvis du har brug for proaktivt at bevare eller slette indhold i Microsoft 365 for at styre oplysninger, anbefaler vi, at du bruger opbevaringspolitikker og opbevaringsmærkater i stedet for følgende ældre funktioner.

Hvis du i øjeblikket bruger disse ældre funktioner, vil de fortsat fungere side om side med Microsoft 365 opbevaringspolitikker og opbevaringsmærkater. Vi anbefaler dog, at du fremover bruger Microsoft 365-opbevaringspolitikker og opbevaringsetiketter til at drage fordel af en enkelt løsning til at administrere både opbevaring og sletning af indhold på tværs af flere arbejdsbelastninger i Microsoft 365.

**Ældre funktioner fra Exchange Online:**

- [Opbevaringsmærker og opbevaringspolitikker](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies), også kaldet [MRM (messaging records management)](/exchange/security-and-compliance/messaging-records-management/messaging-records-management) (kun sletning)
    
    Men hvis du bruger følgende MRM-funktioner, skal du være opmærksom på, at de ikke aktuelt understøttes af Microsoft 365 opbevaringspolitikker:
    
    - En arkiveringspolitik for [arkivpostkasser](enable-archive-mailboxes.md) til automatisk at flytte mails fra en brugers primære postkasse til dennes arkivpostkasse efter en bestemt tidsperiode. En arkiveringspolitik (med alle indstillinger) kan bruges sammen med en Microsoft 365 opbevaringspolitik, der gælder for en brugers primære postkasse og arkivpostkasse.
    
    - Opbevaringspolitikker anvendt af en administrator på bestemte mapper i en postkasse. En Microsoft 365 opbevaringspolitik gælder for alle mapper i postkassen. En administrator kan dog konfigurere forskellige opbevaringsindstillinger ved hjælp af opbevaringsnavne, som en bruger kan anvende på mapper i Outlook som en [standardopbevaringsetiket](create-apply-retention-labels.md#applying-a-default-retention-label-to-an-outlook-folder).

- [Retslig tilbageholdelse](create-a-litigation-hold.md) (kun opbevaring)
    
   Selvom retslig tilbageholdelse stadig understøttes, anbefaler vi, at du bruger Microsoft 365 opbevarings- eller eDiscovery-ventende funktioner [efter behov](#when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds). 

**Ældre funktioner fra SharePoint og OneDrive:**

- [Politikker for dokumentsletning](https://support.office.com/article/Create-a-document-deletion-policy-in-SharePoint-Server-2016-4fe26e19-4849-4eb9-a044-840ab47458ff) (kun sletning)
    
- [Konfiguration af datastyring på stedet](https://support.office.com/article/7707a878-780c-4be6-9cb0-9718ecde050a) (kun opbevaring) 
    
- [Brug politikker for lukning og sletning af websteder](https://support.microsoft.com/en-us/office/use-policies-for-site-closure-and-deletion-a8280d82-27fd-48c5-9adf-8a5431208ba5) (kun sletning)
    
- [Politikker for administration af oplysninger](intro-to-info-mgmt-policies.md) (kun sletning)
     
Hvis du har konfigureret SharePoint til indholdstypepolitikker eller politikker til administration af oplysninger til at bevare indhold til en liste eller et bibliotek, ignoreres disse politikker, mens en opbevaringspolitik er i kraft. 

## <a name="related-information"></a>Relaterede oplysninger

- [SharePoint onlinegrænser](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)
- [Begrænsninger og specifikationer for Microsoft Teams](/microsoftteams/limits-specifications-teams) 
- [Ressourcer, der kan hjælpe dig med at opfylde lovmæssige krav til informationsstyring og datastyring](retention-regulatory-requirements.md)

## <a name="configuration-guidance"></a>Konfigurationsvejledning

Se [Introduktion til informationsstyring](get-started-with-information-governance.md). Denne artikel indeholder oplysninger om abonnementer, tilladelser og links til en ende-konfigurationsvejledning til opbevaringsscenarier.
