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
description: Lær at installere tilføjelser til brugere og grupper i organisationen ved hjælp af Centraliseret udrulning i Administration.
ms.openlocfilehash: e9f5cb01394d947a6b44e1c34870d33b0d6dd9bd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590154"
---
# <a name="deploy-add-ins-in-the-admin-center"></a>Udrul tilføjelsesprogrammer i administrationen

Office-tilføjelsesprogrammet hjælper dig med at tilpasse dine dokumenter og strømline den måde, hvorpå du får adgang til oplysninger på internettet (se Begynd at [bruge Office-tilføjelsesprogrammet](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862)). Som administrator kan du installere Office til brugerne i organisationen ved hjælp af funktionen Centraliseret udrulning på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Centraliseret udrulning er den mest funktionsrige måde for de fleste administratorer at udrulle tilføjelser til brugere og grupper i en organisation.

Du kan finde flere oplysninger om, hvordan du finder ud af, om din organisation kan understøtte Centraliseret udrulning, i Finde ud af, om Centraliseret udrulning af tilføjelsesprogrammet [fungerer for din organisation](centralized-deployment-of-add-ins.md).

Du kan få mere at vide om administration af tilføjelser efter [installation i Administrer tilføjelser i Administration](manage-addins-in-the-admin-center.md)
  
> [!NOTE]
>  I Word Excel og PowerPoint skal du bruge et [SharePoint-appkatalog](/office/dev/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog) til at installere tilføjelsesprogrammet til brugere i et lokalt miljø uden forbindelse til Microsoft 365 og/eller kræver understøttelse af SharePoint-tilføjelsesprogrammet. Du Outlook bruge Exchange til at installere det i et lokalt miljø uden en forbindelse til Microsoft 365.
  
## <a name="recommended-approach-for-deploying-office-add-ins"></a>Anbefalet fremgangsmåde til Office tilføjelsesprogrammet

Hvis du vil udrulle tilføjelser ved hjælp af en trinvis tilgang, anbefaler vi følgende:
  
1. Udrul tilføjelsesprogrammet til et lille sæt virksomheds interessenter og medlemmer af it-afdelingen. Hvis installationen lykkes, skal du gå til trin 2.
    
2. Udrul tilføjelsesprogrammet til flere personer i virksomheden. Igen skal du evaluere resultaterne og fortsætte den fulde installation, hvis det lykkes.
    
3. Udfør en fuld udrulning for alle brugere.
    
Afhængigt af målgruppen kan du tilføje eller fjerne udrulningstrin.
  
## <a name="deploy-an-office-add-in-using-the-admin-center"></a>Installere Office tilføjelsesprogrammet Administration

Før du begynder, skal [du se Find ud af, om Centraliseret udrulning af tilføjelses-ins fungerer for din organisation](centralized-deployment-of-add-ins.md).
  
1. Gå til siden Indstillinger  \> **Administration**. Hvis siden Tilføjelsesprogrammer ikke vises, **skal** du gå til siden **Indstillinger** \> **integrerede** **apps-tilføjelsesprogrammer**\>.

2. Vælg **Installer tilføjelsesprogrammet** øverst på siden, og vælg derefter **Næste**.

    > [!NOTE]
    > Du kan også installere tilføjelsesprogrammer i Administration via [integrerede apps](test-and-deploy-microsoft-365-apps.md). Integrerede apps er synlige for globale og Exchange administratorer. Hvis du ikke kan se ovenstående trin, skal du gå til sektionen Centraliseret udrulning ved at **gå til Indstillinger** >  **Integrerede apps**. Øverst på siden **Integrerede apps** skal du **vælge Tilføjelsesprogrammer**.

3. Vælg en indstilling, og følg vejledningen.
  
4. Hvis du har valgt muligheden for at tilføje et tilføjelsesprogrammet fra Office Store, skal du foretage dit valg af tilføjelsesprogrammet. </br>

    Du kan få vist tilgængelige tilføjelser efter kategorier: **Foreslået til dig****, Bedømmelse** eller **Navn**. Det er kun gratis tilføjelser, der er tilgængelige fra Office Store. Betalte tilføjelser understøttes ikke i øjeblikket. Når du har valgt et tilføjelsesprogrammet, skal du acceptere vilkårene og betingelserne for at fortsætte. <br/> 

    > [!NOTE]
    > Med Office Store funktion installeres opdateringer og forbedringer automatisk til brugerne.

5. På næste side skal du **vælge Alle**, **Bestemte brugere/grupper** eller **Kun** mig for at angive, hvem tilføjelsesprogrammet er installeret til. Brug feltet Søg til at finde bestemte brugere eller grupper. <br/>

    > [!NOTE]
    > Hvis du vil have mere at vide om andre tilstande, der gælder for et tilføjelsesprogrammet, skal [du se Tilføjelsesprogrammets tilstande](./manage-addins-in-the-admin-center.md).
  
6. Vælg **Installér**.
  
7. Der vises et grønt flueben, når tilføjelsesprogrammet installeres. Følg vejledningen på siden for at teste tilføjelsesprogrammet.

    > [!NOTE]
    > Brugere skal muligvis starte for Office for at få vist tilføjelsesprogrammets ikon på appbåndet. Outlook det kan tage op til 24 timer, før tilføjelsesapps vises på appbånd.

8. Vælg Næste, når du **er færdig**. Hvis du kun har installeret til dig selv, kan du vælge **Skift, hvem** der har adgang til tilføjelsesprogrammet for at udrulle det til flere brugere.

    Hvis du har installeret tilføjelsesprogrammet til andre medlemmer af organisationen, skal du følge vejledningen for at annoncere installationen af tilføjelsesprogrammet. <br/>
  
    Det er god praksis at informere brugere og grupper om, at det installerede tilføjelsesprogrammet er tilgængeligt. Overvej at sende en mail, der beskriver, hvornår og hvordan du bruger tilføjelsesprogrammet. Medtag eller link til indhold i Hjælp eller Ofte stillede spørgsmål, der kan hjælpe brugerne, hvis de har problemer med tilføjelsesprogrammet.
  
### <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a>Overvejelser i forbindelse med tildeling af et tilføjelsesprogrammet til brugere og grupper

Globale administratorer og Exchange-administratorer kan tildele et tilføjelsesprogrammet til alle eller til bestemte brugere og grupper. Hver indstilling har konsekvenser:
  
- **Alle** Denne indstilling tildeler tilføjelsesprogrammet til alle brugere i organisationen. Brug denne indstilling sparsomt og kun til tilføjelser, der er virkelig universale for din organisation.

- **Brugere** Hvis du tildeler et tilføjelsesprogrammet til en enkelt bruger og derefter installerer tilføjelsesprogrammet til en ny bruger, skal du først tilføje den nye bruger.

- **Grupper** Hvis du tildeler et tilføjelsesprogrammet til en gruppe, tildeles brugere, der er føjet til gruppen, automatisk tilføjelsesprogrammet. Når en bruger fjernes fra en gruppe, mister brugeren adgang til tilføjelsesprogrammet. I begge tilfælde kræves der ingen yderligere handling fra administratoren.

- **Bare mig** Hvis du kun tildeler et tilføjelsesprogrammet til dig selv, tildeles tilføjelsesprogrammet kun til din konto, hvilket er ideelt til test af tilføjelsesprogrammet.

Den rigtige indstilling for din organisation afhænger af din konfiguration. Vi anbefaler dog, at du foretager tildelinger ved hjælp af grupper. Som administrator kan det være nemmere at administrere tilføjelser ved hjælp af grupper og styre medlemskabet af disse grupper i stedet for at tildele individuelle brugere hver gang. I nogle situationer kan det være en god ide at begrænse adgangen for et lille antal brugere ved at tildele brugere manuelt til bestemte brugere.
  
## <a name="more-about-office-add-ins-security"></a>Flere oplysninger Office sikkerhed for tilføjelsesopdateringer

Office-tilføjelsesprogram kombinerer en XML-manifestfil, der indeholder nogle metadata om tilføjelsesprogrammet, men det vigtigste peger på et webprogram, som indeholder alle koder og logik. Tilføjelses-ins kan variere i deres egenskaber. Tilføjelsesprogrammet kan f.eks.:
  
- Vise data.

- Læs en brugers dokument for at tilbyde kontekstafhængige tjenester.

- Læs og skriv data til og fra en brugers dokument for at skabe værdi for den pågældende bruger.

Du kan finde flere oplysninger om typerne og egenskaberne for [Office-tilføjelsesprogrammet i oversigten over Office-tilføjelsesprogrammets platform](/office/dev/add-ins/overview/office-add-ins), især afsnittet "Office Tilføjelsesprogrammet".
  
Hvis du vil interagere med brugerens dokument, skal tilføjelsesprogrammet angive hvilke tilladelser, det skal bruge i manifestet. En JavaScript API-adgangstilladelsesmodel i fem niveauer udgør grundlaget for beskyttelse af personlige oplysninger og sikkerhed for brugere opgaverude tilføjelsesprogrammet. Størstedelen af tilføjelses insendet i Office Store niveau LæsSkrivDokument, hvor næsten alle tilføjelses ins understøtter mindst LæsDokument-niveauet. Du kan finde flere oplysninger om tilladelsesniveauer i Anmode om tilladelser til brug af [API i opgaverude-tilføjelsesprogrammet](/office/dev/add-ins/develop/requesting-permissions-for-api-use-in-content-and-task-pane-add-ins).
  
Når du opdaterer et manifest, vil de typiske ændringer være et tilføjelsesprogrammets ikon og tekst. Nogle gange ændres tilføjelsesprogrammets kommandoer. Tilladelserne for tilføjelsesprogrammet ændres dog ikke. Det webprogram, hvor alle koder og logik til tilføjelsesprogrammet kører, kan ændres når som helst, hvilket er en del af webprogrammers karakter.
  
Opdateringer til tilføjelser sker på følgende måde:
  
- **Line of business-tilføjelsesprogrammet:** I dette tilfælde, hvor en administrator eksplicit overførte et manifest, kræver tilføjelsesprogrammet, at administratoren overfører et nyt manifest for at understøtte ændringer af metadata. Næste gang de relevante Office programmer starter, opdateres tilføjelsesprogrammet. Webprogrammet kan ændres når som helst.

    > [!NOTE]
    > Administratoren behøver ikke at fjerne et LOB-tilføjelsesprogrammet for at udføre en opdatering.   I sektionen Tilføjelser kan administrator blot klikke på LOB-tilføjelsesprogrammet og vælge knappen Opdater **i nederste** højre hjørne. Opdateringen fungerer kun, hvis versionen af det nye tilføjelsesprogrammet er større end versionen af det eksisterende tilføjelsesprogrammet.

- **Office Store tilføjelsesprogrammet:** Når en administrator har valgt et tilføjelsesprogrammet fra Office Store, opdateres tilføjelsesprogrammet senere i Centraliseret udrulning, hvis et tilføjelsesprogrammet opdateres i Office Store. Næste gang de relevante Office programmer starter, opdateres tilføjelsesprogrammet. Webprogrammet kan ændres når som helst.
  
## <a name="related-content"></a>Relateret indhold

[Administrer tilføjelser i Administration (artikel](manage-addins-in-the-admin-center.md) )\
[Opbyg dit opgaverude Word-tilføjelsesprogrammet](/office/dev/add-ins/quickstarts/word-quickstart?tabs=yeomangenerator) (artikel\
[Mindreårige og henløsning af tilføjelsesprogrammet fra butikken](minors-and-acquiring-addins-from-the-store.md) (artikel)\
[Brug Centraliseret udrulning af PowerShell-cmdlet'er til at administrere tilføjelser](../../enterprise/use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md) (artikel)\
[Fejlfinding: Brugeren får ikke vist tilføjelsesprogram (](/office365/troubleshoot/access-management/user-not-seeing-add-ins) artikel)
