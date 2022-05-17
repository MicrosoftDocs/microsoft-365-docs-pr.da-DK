---
title: Udrul tilføjelsesprogrammer i administrationen
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Få mere at vide om, hvordan du udruller tilføjelsesprogrammer til brugere og grupper i din organisation ved hjælp af Central installation i Administration.
ms.openlocfilehash: a599023db47a46baa0318e026e70627320a6b1f8
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437519"
---
# <a name="deploy-add-ins-in-the-microsoft-365-admin-center"></a>Installer tilføjelsesprogrammer i Microsoft 365 Administration

Office tilføjelsesprogrammer hjælper dig med at tilpasse dine dokumenter og strømline den måde, du får adgang til oplysninger på internettet på (se [Begynd at bruge dit Office-tilføjelsesprogram](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862)). Som administrator kan du installere Office tilføjelsesprogrammer for brugerne i din organisation ved hjælp af funktionen Centraliseret installation i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Central installation er den anbefalede og mest funktionsrige måde for de fleste administratorer at udrulle tilføjelsesprogrammer til brugere og grupper i en organisation.

Du kan finde flere oplysninger om, hvordan du finder ud af, om din organisation kan understøtte central installation, under [Find ud af, om central installation af tilføjelsesprogrammer fungerer for din organisation](centralized-deployment-of-add-ins.md).

Hvis du vil vide mere om administration af tilføjelsesprogrammer efter installation, skal du se [Administrer tilføjelsesprogrammer i Administration](manage-addins-in-the-admin-center.md)
  
> [!NOTE]
>  I forbindelse med Word skal du Excel og PowerPoint bruge et [SharePoint app-katalog](/office/dev/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog) til at installere tilføjelsesprogrammer til brugere i et lokalt miljø uden forbindelse til Microsoft 365 og/eller understøttelse af SharePoint tilføjelsesprogrammer. Til Outlook bruge Exchange kontrolpanel til at installere i et lokalt miljø uden forbindelse til Microsoft 365.
  
## <a name="recommended-approach-for-deploying-office-add-ins"></a>Anbefalet fremgangsmåde til installation af Office tilføjelsesprogrammer

Hvis du vil udrulle tilføjelsesprogrammer ved hjælp af en faseinddelt tilgang, anbefaler vi følgende:
  
1. Udrul tilføjelsesprogrammet til et lille sæt virksomhedsinteressenter og medlemmer af it-afdelingen. Hvis installationen lykkes, skal du gå til trin 2.
    
2. Udrul tilføjelsesprogrammet til flere enkeltpersoner i virksomheden. Evaluer igen resultaterne, og fortsæt med fuld udrulning, hvis det lykkes.
    
3. Udfør en komplet udrulning til alle brugere.
    
Afhængigt af målgruppens størrelse kan du tilføje eller fjerne udrulningstrin.
  
## <a name="deploy-an-office-add-in-using-the-admin-center"></a>Udrul et Office-tilføjelsesprogram ved hjælp af Administration

Før du begynder, skal du se [Find ud af, om central installation af tilføjelsesprogrammer fungerer for din organisation](centralized-deployment-of-add-ins.md).
  
1. I Administration skal du gå til siden **Indstillinger** \> **tilføjelsesprogrammer**. Hvis du ikke kan se siden **med tilføjelsesprogrammer**, skal du gå til siden **Indstillinger** \> **tilføjelsesprogrammer** til **integrerede apps**\>.

2. Vælg **Installér tilføjelsesprogram** øverst på siden, og vælg derefter **Næste**.

    > [!NOTE]
    > Du kan også installere tilføjelsesprogrammer i Administration via [integrerede apps](test-and-deploy-microsoft-365-apps.md). Integrerede apps er synlige for globale og Exchange administratorer. Hvis du ikke kan se ovenstående trin, skal du gå til afsnittet Centraliseret installation ved at gå til **Indstillinger** >  **Integrated-apps**. Øverst på siden **Integrerede apps** skal du vælge **Tilføjelsesprogrammer**.

3. Vælg en indstilling, og følg vejledningen.
  
4. Hvis du har valgt indstillingen for at tilføje et tilføjelsesprogram fra Office Store, skal du markere dit tilføjelsesprogram. </br>

    Du kan få vist tilgængelige tilføjelsesprogrammer efter kategorier: **Foreslået til dig**, **Bedømmelse** eller **Navn**. Det er kun gratis tilføjelsesprogrammer, der er tilgængelige fra Office Store. Betalte tilføjelsesprogrammer understøttes ikke i øjeblikket. Når du har valgt et tilføjelsesprogram, skal du acceptere vilkårene og betingelserne for at fortsætte. <br/> 

    > [!NOTE]
    > Med indstillingen Office Store udrulles opdateringer og forbedringer automatisk til brugere.

5. På den næste side skal du vælge **Alle**, **Specifikke brugere/grupper** eller **Bare mig** for at angive, hvem tilføjelsesprogrammet skal installeres til. Brug søgefeltet til at finde bestemte brugere eller grupper. <br/>

    > [!NOTE]
    > Hvis du vil vide mere om andre tilstande, der gælder for et tilføjelsesprogram, skal du se [Tilføjelsestilstande](./manage-addins-in-the-admin-center.md).
  
6. Vælg **Installér**.
  
7. Der vises et grønt tik, når tilføjelsesprogrammet installeres. Følg vejledningen på siden for at teste tilføjelsesprogrammet.

    > [!NOTE]
    > Brugerne skal muligvis genstarte Office for at få vist ikonet for tilføjelsesprogrammet på appbåndet. Outlook tilføjelsesprogrammer kan tage op til 24 timer, før de vises på appbånd.

8. Når du er færdig, skal du vælge **Næste**. Hvis du kun har udrullet til dig selv, kan du vælge **Skift, hvem der har adgang til tilføjelsesprogrammet** , for at udrulle til flere brugere.

    Hvis du har installeret tilføjelsesprogrammet til andre medlemmer af din organisation, skal du følge vejledningen for at annoncere installationen af tilføjelsesprogrammet. <br/>
  
    Det er god praksis at informere brugere og grupper om, at det udrullede tilføjelsesprogram er tilgængeligt. Overvej at sende en mail, der beskriver, hvornår og hvordan du bruger tilføjelsesprogrammet. Medtag eller opret et link til Hjælp-indhold eller ofte stillede spørgsmål, der kan hjælpe brugerne, hvis de har problemer med tilføjelsesprogrammet.
  
### <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a>Overvejelser ved tildeling af et tilføjelsesprogram til brugere og grupper

Globale administratorer og Exchange administratorer kan tildele et tilføjelsesprogram til alle eller til bestemte brugere og grupper. Hver indstilling har konsekvenser:
  
- **Alle** Denne indstilling tildeler tilføjelsesprogrammet til alle brugere i organisationen. Brug denne indstilling sparsomt og kun til tilføjelsesprogrammer, der er universelle for din organisation.

- **Brugere** Hvis du tildeler et tilføjelsesprogram til en enkelt bruger og derefter installerer tilføjelsesprogrammet til en ny bruger, skal du først tilføje den nye bruger.

- **Grupper** Hvis du tildeler et tilføjelsesprogram til en gruppe, tildeles de brugere, der føjes til gruppen, automatisk tilføjelsesprogrammet. Når en bruger fjernes fra en gruppe, mister brugeren adgangen til tilføjelsesprogrammet. I begge tilfælde kræves der ingen yderligere handling fra administratoren.

- **Bare mig** Hvis du kun tildeler et tilføjelsesprogram til dig selv, tildeles tilføjelsesprogrammet kun til din konto, hvilket er ideelt til test af tilføjelsesprogrammet.

Den rigtige indstilling for din organisation afhænger af din konfiguration. Vi anbefaler dog, at du foretager tildelinger ved hjælp af grupper. Som administrator kan det være nemmere at administrere tilføjelsesprogrammer ved hjælp af grupper og styre medlemskabet af disse grupper i stedet for at tildele individuelle brugere hver gang. I nogle situationer kan det være en god idé at begrænse adgangen til et lille sæt brugere ved at tildele tildelinger til bestemte brugere ved at tildele brugere manuelt.
  
## <a name="more-about-office-add-ins-security"></a>Mere om sikkerhed i forbindelse med Office tilføjelsesprogrammer

Office tilføjelsesprogrammer kombinerer en XML-manifestfil, der indeholder metadata om tilføjelsesprogrammet, men vigtigst af alt peger på et webprogram, der indeholder al kode og logik. Tilføjelsesprogrammer kan variere i deres funktioner. Tilføjelsesprogrammer kan f.eks.:
  
- Vis data.

- Læs en brugers dokument for at levere kontekstafhængige tjenester.

- Læs og skriv data til og fra en brugers dokument for at give den pågældende bruger værdi.

Du kan få flere oplysninger om typerne og egenskaberne i Office tilføjelsesprogrammer under [oversigt over Office platform til tilføjelsesprogrammer](/office/dev/add-ins/overview/office-add-ins), især afsnittet "Anatomi af et Office-tilføjelsesprogram".
  
Hvis du vil interagere med brugerens dokument, skal tilføjelsesprogrammet deklarere, hvilken tilladelse det har brug for i manifestet. En JavaScript API-adgangsrettighedsmodel på fem niveauer udgør grundlaget for beskyttelse af personlige oplysninger og sikkerhed for brugere af tilføjelsesprogrammer i opgaverude. De fleste tilføjelsesprogrammer i Office Store er ReadWriteDocument-niveauet, og næsten alle tilføjelsesprogrammer understøtter mindst ReadDocument-niveauet. Du kan få flere oplysninger om tilladelsesniveauer under [Anmodning om tilladelser til API-brug i indhold og tilføjelsesprogrammer i opgaveruden](/office/dev/add-ins/develop/requesting-permissions-for-api-use-in-content-and-task-pane-add-ins).
  
Når du opdaterer et manifest, er de typiske ændringer af et tilføjelsesprograms ikon og tekst. Indimellem ændres tilføjelseskommandoer. Tilladelserne for tilføjelsesprogrammet ændres dog ikke. Webprogrammet, hvor al kode og logik for tilføjelsesprogrammet kører, kan ændres når som helst, hvilket er arten af webprogrammer.
  
Opdateringer til tilføjelsesprogrammer sker på følgende måde:
  
- **Tilføjelsesprogram til line of business:** Hvis en administrator eksplicit har uploadet et manifest, kræver tilføjelsesprogrammet i dette tilfælde, at administratoren uploader en ny manifestfil for at understøtte ændringer af metadata. Næste gang de relevante Office programmer starter, opdateres tilføjelsesprogrammet. Webprogrammet kan ændres når som helst.

    > [!NOTE]
    > Administratoren behøver ikke at fjerne et LOB-tilføjelsesprogram for at udføre en opdatering.   I afsnittet Tilføjelsesprogrammer kan administratoren blot klikke på LOB-tilføjelsesprogrammet og vælge **knappen Opdater** i nederste højre hjørne. Opdateringen fungerer kun, hvis versionen af det nye tilføjelsesprogram er større end det eksisterende tilføjelsesprograms version.

- **Office Store tilføjelsesprogram:** Når en administrator har valgt et tilføjelsesprogram fra Office Store, opdateres tilføjelsesprogrammet senere i Centraliseret installation, hvis et tilføjelsesprogram opdateres i Office Store. Næste gang de relevante Office programmer starter, opdateres tilføjelsesprogrammet. Webprogrammet kan ændres når som helst.
  
## <a name="related-content"></a>Relateret indhold

[Administrer tilføjelsesprogrammer i Administration](manage-addins-in-the-admin-center.md) (artikel)\
[Byg dit første tilføjelsesprogram til opgaveruden Word](/office/dev/add-ins/quickstarts/word-quickstart?tabs=yeomangenerator) (artikel\
[Mindreårige og hentning af tilføjelsesprogrammer fra butikken](minors-and-acquiring-addins-from-the-store.md) (artikel)\
[Brug Central installation PowerShell-cmdlet'er til at administrere tilføjelsesprogrammer](../../enterprise/use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md) (artikel)\
[Fejlfinding: Brugeren får ikke vist tilføjelsesprogrammer](/office365/troubleshoot/access-management/user-not-seeing-add-ins) (artikel)
