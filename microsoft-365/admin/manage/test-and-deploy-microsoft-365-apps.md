---
title: Teste og installere Microsoft 365 Apps efter partnere i portalen for integrerede apps
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid: MET150
ROBOTS: NOINDEX, NOFOLLOW
description: Find, test og installer Microsoft- og Microsoft-partnerapps til brugere og grupper i organisationen fra portalen integrerede apps i Microsoft 365 Administration.
ms.openlocfilehash: bc633b2a2541a5c1fd813848cd39c7c6e91420ee
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/02/2021
ms.locfileid: "63590224"
---
# <a name="test-and-deploy-microsoft-365-apps-by-partners-in-the-integrated-apps-portal"></a>Teste og installere Microsoft 365 Apps efter partnere i portalen for integrerede apps

The Microsoft 365 Administration giver dig fleksibilitet til at installere Single Store-apps, brugerdefinerede forretningsområder af apps og Microsoft 365-partnerapps fra et enkelt sted. Placeringen kan tilgås i indstillingerne i Microsoft Administration i integrerede apps. Muligheden for at finde, teste og installere fuldt ud købte og licenserede apps af Microsoft-partnere fra portalen integrerede apps giver den brugervenlighed og de fordele, din organisation kræver for at holde virksomhedstjenester opdateret regelmæssigt og køre effektivt.

Du kan finde flere oplysninger om Microsoft 365 og licenser til apps fra partnere i organisationen under [Administrere og Microsoft 365 Apps fra Microsoft 365 Administration](https://techcommunity.microsoft.com/t5/microsoft-365-blog/manage-and-deploy-microsoft-365-apps-from-the-microsoft-365/ba-p/1194324).

Du kan finde flere oplysninger om, hvordan partnere opretter disse apps, [under Sådan planlægger du et SaaS-tilbud til den kommercielle markedsplads](https://go.microsoft.com/fwlink/?linkid=2158277)

Portalen integrerede apps er kun tilgængelig for globale administratorer og er kun tilgængelig for kunder i hele verden. Denne funktion er ikke tilgængelig i nationale og offentlige skyer.

Portalen integrerede apps viser en liste over apps, som indeholder enkelte apps og Microsoft 365-apps fra partnere, der er installeret i organisationen. Kun webapps, SPFx, Office og tilføjelsesprogrammer og Teams vises. For webapps kan du se to typer apps.

- SaaS-apps, der er tilgængelige i appsource.microsoft.com, og som kan installeres af administratorer, der giver samtykke på vegne af organisationen.
- SAML-galleriapps, der er sammenkædet med Office-tilføjelsesprogrammer.

## <a name="manage-apps-in-the-integrated-apps-portal"></a>Administrer apps i portalen for integrerede apps

Du kan administrere test og installation af købte og licenserede Microsoft 365 Apps fra partnere.

1. I Administration skal du vælge **Indstillinger** og derefter vælge **Integrerede apps**.

2. Vælg en app med **Status for** **Flere apps tilgængelige** for at åbne **ruden** Administrer. Status for flere **tilgængelige apps fortæller** dig, at der er flere integrationer fra isv'er, der endnu ikke er installeret.

3. På fanen **Oversigt** skal du vælge **Installér**. Nogle apps kræver, at du tilføjer brugere, før du kan vælge Installer.

4. Vælg  **Brugere**, vælg **Er dette en testinstallation**, og vælg derefter **Hele organisationen**, **Bestemte brugere/grupper** eller **Kun mig**. Du kan også vælge **Testinstallation,** hvis du foretrækker at vente med at installere appen på hele organisationen. Bestemte brugere eller grupper kan være Microsoft 365 gruppe, en sikkerhedsgruppe eller en distributionsgruppe.

5. Vælg **Opdater** og derefter **Udført**. Du kan nu vælge Installer på fanen Oversigt.

6. Gennemse appoplysningerne, og vælg derefter **Installér**.

7. Vælg **Udført** på siden Installation fuldført, og gennemgå oplysningerne om testen eller den komplette installation på **fanen** Oversigt.

8. Hvis appen har statussen Opdater **afventende**, kan du klikke på appen for at åbne ruden Administrer og opdatere appen.

## <a name="find-published-apps-for-testing-and-full-deployment"></a>Find publicerede apps til test og fuld udrulning

Du kan finde, teste og installere publicerede apps fuldt ud, som ikke allerede vises på listen på siden Integrerede apps. Ved at købe og licensere appsene fra Administration kan du føje Microsoft- og Microsoft-partnerapps til din liste fra en enkelt placering.

1. I Administration i venstre navigationslinje skal du vælge **Indstillinger** og derefter vælge <a href="https://go.microsoft.com/fwlink/p/?linkid=2125823" target="_blank">**Integrerede apps**</a>.

2. Vælg **Hent apps** for at få en visning af appsene.

3. På siden **Microsoft 365 Apps** publicerede apps skal du vælge den app, du vil installere, ved at vælge **Hent den nu**. De apps, der vises primært, er Word-, PowerPoint-, Excel-, Outlook-tilføjelsesprogrammer, Teams-apps og SharePoint-apps (bygget på SharePoint Framework teknologi). Acceptér tilladelserne, og vælg **Fortsæt**.

5. Vælg **Installer** øverst på siden ud for den meddelelse, der refererer til at vente på at blive installeret.

    Hvis den valgte app er sammenkædet med et SaaS-tilbud fra en ISV, vises alle de andre apps, der er en del af dette tilknyttede tilbud, på siden Konfiguration. Hvis du vælger at installere alle appsene, skal du vælge **Næste**. Ellers skal du **vælge Rediger** og vælge, hvilke apps du vil installere. Nogle apps kræver, at du tilføjer brugere, før du kan **vælge Installer**.

6. Vælg **Tilføj brugere**, vælg **Er dette en testinstallation**, og vælg derefter **Hele organisationen** eller **Bestemte brugere/grupper** eller **Kun mig**.

    Bestemte brugere/grupper kan være en Microsoft 365 gruppe, en sikkerhedsgruppe eller en distribueret gruppe. Du kan også vælge **Testinstallation,** hvis du foretrækker at vente med at installere appen på hele organisationen.

7. Vælg **Næste** for at komme til siden **Acceptér anmodning om** tilladelse. Appfunktionerne og -tilladelserne for hver af disse apps vises. Hvis appen kræver samtykke, skal du **vælge Acceptér tilladelser**. Kun en global administrator kan give samtykke.

8. Vælg **Næste for** at gennemgå installationen, og vælg **Afslut udrulning**. Du kan få vist installationen fra fanen **Oversigt** ved at vælge **Vis denne installation**. I Microsoft 365 Administration kan du se status for hver installeret app og den dato, hvor du har installeret appen.

> [!NOTE]
> Hvis en app tidligere blev installeret fra et andet sted end portalen til integrerede apps, **er Installationstype** **brugerdefineret.**

## <a name="unsupported-scenarios"></a>Ikke-understøttede scenarier

Du kan ikke installere en enkelt Store-app eller -Microsoft 365 Apps efter partner fra portalen for integrerede apps til følgende scenarier.

- Det samme tilføjelsesprogrammet er sammenkædet med mere end ét SaaS-tilbud.
- SaaS-tilbuddet er sammenkædet med tilføjelsesapps, men det integreres ikke med Microsoft Graph og der AAD-app-id.
- SaaS-tilbuddet er sammenkædet med tilføjelsesapps, men det app-AAD, der leveres med Microsoft Graph-integration, deles på tværs af flere SaaS-tilbud.

## <a name="upload-custom-line-of-business-apps-for-testing-and-full-deployment"></a>Upload brugerdefinerede line of business-apps til test og fuld udrulning

1. I Administration i venstre navigationslinje skal du vælge **Indstillinger** og derefter **Integrerede apps**.

2. Vælg **Upload brugerdefinerede apps**. Kun en brugerdefineret linje med apps til Word, PowerPoint, Excel og Outlook understøttes.

3. Upload manifestfilen fra din enhed, eller tilføj et URL-link. Nogle apps kræver, at du tilføjer brugere, før du kan vælge Installer.

4. Vælg **Tilføj brugere**, vælg **Er dette en testinstallation**, og vælg **Hele organisationen** eller **Bestemte brugere/grupper** eller **Kun mig**.

    Bestemte brugere/grupper kan være en Microsoft 365 gruppe, en sikkerhedsgruppe eller en distribueret gruppe. Du kan også vælge **Testinstallation** , hvis du vil vente med at installere appen på hele organisationen.

5. Vælg **Næste** for at komme til siden **Acceptér anmodning om** tilladelse. Appfunktionerne og -tilladelserne for disse apps vises. Hvis appen kræver samtykke, skal du **vælge Acceptér tilladelser**. Kun en global administrator kan give samtykke.

6. Vælg **Næste for** at gennemgå installationen, og vælg **Afslut udrulning**. Du kan få vist installationen fra fanen **Oversigt** ved at vælge **Vis denne installation**.

## <a name="prepare-to-deploy-add-ins-in-integrated-apps"></a>Forbered dig på at installere tilføjelsesprogrammer i integrerede apps

Office-tilføjelsesprogrammet hjælper dig med at tilpasse dine dokumenter og strømline den måde, hvorpå du får adgang til oplysninger på internettet (se Begynd at bruge dit Office-tilføjelsesprogrammet). 

Tilføjelsesprogrammet har følgende fordele: 

- Når det Office program startes, downloades tilføjelsesprogrammet automatisk. Hvis tilføjelsesprogrammet understøtter tilføjelsesprogramkommandoer, vises tilføjelsesprogrammet automatisk på båndet i det Office program. 

- Tilføjelsesprogrammet vises ikke længere for brugere, hvis administratoren deaktiverer eller sletter tilføjelsesprogrammet, eller hvis brugeren fjernes fra Azure Active Directory eller fra en gruppe, som tilføjelsesprogrammet er tildelt til. 

Tilføjelsesprogrammer understøttes i tre skrivebordsplatforme til Windows, Mac og online Office apps. Det understøttes også i iOS og Android (Outlook kun for mobile tilføjelser). 

Det kan tage op til 24 timer, før et tilføjelsesprogrammet vises for klienten for alle brugere. 

I dag kan Exchange administratorer og globale administratorer installere tilføjelsesprogrammer fra integrerede apps.   

### <a name="before-you-begin"></a>Før du begynder

Installation af tilføjelser kræver, at brugerne bruger Microsoft 365 Business-licenser (Business Basic, Business Standard, Business Premium), Office 365 Enterprise-licenser (E1/E3/E5/F3) eller Microsoft 365 Enterprise-licenser (E3/E5/F3). Brugerne skal også være logget på Office deres organisations-id) og have Exchange Online aktive Exchange Online postkasser. Din abonnementsmappe skal enten være i eller være medlem af organisationsnetværket for Azure Active Directory. 

Installation understøtter ikke følgende: 

- Tilføjelser, der er rettet mod Word, Excel eller PowerPoint i Office 2013 
- En lokal katalogtjeneste 
- Installation af tilføjelsesprogrammet på Exchange lokale postkasse 
- Installation af Component Object Model (COM) eller Visual Studio Tools Office til tilføjelsesprogrammet VSTO (Component Object Model). 
- Installationer af Microsoft 365, der ikke Exchange Online, f.eks. Microsoft 365 Apps for Business og Microsoft 365 Apps for Enterprise.  

### <a name="office-requirements"></a>Office krav 

For Word Excel og PowerPoint-tilføjelsesprogrammet skal dine brugere benytte en af følgende fremgangsmåder: 
- På en Windows-enhed version 1704 eller nyere af Microsoft 365 Business-licenser (Business Basic, Business Standard, Business Premium), Office 365 Enterprise-licenser (E1/E3/E5/F3) eller Microsoft 365 Enterprise-licenser (E3/E5/F3). 
- På en Mac, version 15.34 eller nyere. 

For Outlook skal dine brugere bruge en af følgende: 
- Version 1701 eller nyere af Microsoft 365 Business-licenser (Business Basic, Business Standard, Business Premium), Office 365 Enterprise-licenser (E1/E3/E5/F3) eller Microsoft 365 Enterprise licenser (E3/E5/F3). 
- Version 1808 eller nyere af Office Professional Plus 2019 eller Office Standard 2019. 
- Version 16.0.4494.1000 eller nyere af Office Professional Plus 2016 (MSI) eller Office Standard 2016 (MSI).
    > [!NOTE]
    > MSI-versioner af Outlook viser tilføjelsesprogrammet administratorinstalleret i det relevante Outlook, ikke sektionen "Mine tilføjelsesprogrammet".  
- Version 15.0.4937.1000 eller nyere af Office Professional Plus 2013 (MSI) eller Office Standard 2013 (MSI).
- Version 16.0.9318.1000 eller nyere af Office 2016 til Mac. 
- Version 2.75.0 eller nyere af Outlook til iOS. 
- Version 2.2.145 eller nyere af Outlook til Android. 



### <a name="exchange-online-requirements"></a>Exchange Online krav 
Microsoft Exchange gemmer manifester for tilføjelsesprogrammet i din organisations lejer. Administratoren, der udruller tilføjelsesprogrammet, og de brugere, der modtager disse tilføjelses ins, skal bruge en version af Exchange Online der understøtter OAuth-godkendelse. 

Kontakt din organisations administrator Exchange at finde ud af, hvilken konfiguration der er i brug. OAuth-forbindelse pr. bruger kan bekræftes ved hjælp af  [cmdlet'enTest-OAuthConnectivityPowerShell](/powershell/module/exchange/test-oauthconnectivity) . 

### <a name="user-and-group-assignments"></a>Bruger- og gruppetildelinger
Installation af tilføjelsesprogrammet understøttes i øjeblikket i størstedelen af grupper, der understøttes af Azure Active Directory, herunder Microsoft 365-grupper, distributionslister og sikkerhedsgrupper. Udrulning understøtter brugere i grupper på øverste niveau eller grupper uden overordnede grupper, men ikke brugere i indlejrede grupper eller grupper, der har overordnede grupper. 

> [!NOTE]
> Ikke-mailaktiverede sikkerhedsgrupper understøttes ikke i øjeblikket. 

I følgende eksempel er Sandra, Sheila og gruppen Salgsafdeling tildelt et tilføjelsesprogrammet. West Coast Sales Department er en indlejret gruppe, og derfor er Bert og Fred ikke tildelt et tilføjelsesprogrammet. 

![Diagram over salgsafdelingen.](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)

### <a name="find-out-if-a-group-contains-nested-groups"></a>Find ud af, om en gruppe indeholder indlejrede grupper

Den nemmeste måde at registrere, om en gruppe indeholder indlejrede grupper, er at få vist gruppens visitkort i Outlook. Hvis du angiver gruppenavnet i  **feltetTil**  for en mail og derefter vælger gruppenavnet, når det findes, får du vist, om den indeholder brugere eller indlejrede grupper. I eksemplet herunder viser  **undergruppens**  medlemmer Outlook for Testgruppen ingen brugere og kun to undergrupper. 

![Fanen Medlemmer på Outlook visitkort.](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)

Du kan udføre den modsatte forespørgsel ved at finde gruppen for at se, om den er medlem af en gruppe. I eksemplet nedenfor kan du undertabuleringsposten <b></b>  for gruppen Outlook se, at Undergruppe 1 er medlem af Testgruppen. 

![Fanen Medlemskab på Outlook visitkort.](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)

Bemærk, at du kan bruge Azure Active Directory Graph-API'en til at køre forespørgsler for at finde listen over grupper inden for en gruppe. Du kan få mere at vide  [underOperations på | Graph API-reference](/previous-versions/azure/ad/graph/api/groups-operations). 

## <a name="recommended-approach-for-deploying-office-add-ins"></a>Anbefalet fremgangsmåde til Office tilføjelsesprogrammet 
Hvis du vil udrulle tilføjelser ved hjælp af en trinvis tilgang, anbefaler vi følgende: 
1. Udrul tilføjelsesprogrammet til et lille sæt virksomheds interessenter og medlemmer af it-afdelingen. Du kan aktivere flaget Er **dette en testinstallation**. Hvis installationen lykkes, skal du gå til trin 2. 

2. Udrul tilføjelsesprogrammet til flere personer i virksomheden. Igen skal du evaluere resultaterne og fortsætte den fulde installation, hvis det lykkes. 

3. Udfør en fuld udrulning for alle brugere. Deaktivere flaget fra **Er dette en testinstallation**. 

Afhængigt af målgruppen kan du tilføje eller fjerne udrulningstrin.  

## <a name="deploy-an-office-add-in-using-the-admin-center"></a>Installere Office tilføjelsesprogrammet Administration 

1. I Administration skal **du vælge Indstillinger** og derefter vælge **Integrerede apps**. 

2.  **VælgFå** apps øverst på siden. AppSource indlæses i et integreret format. Du kan enten søge efter et tilføjelsesprogrammet eller finde det ved at klikke på Produkt i venstre navigationslinje.  Hvis tilføjelsesprogrammet er blevet sammenkædet af ISV til en SaaS-app eller andre apps og tilføjelsesprogrammer, og hvis SaaS-appen er en betalt app, vises der en dialogboks for enten at købe licensen eller installere. Uanset om du har købt licensen eller ej, kan du fortsætte installationen. Vælg **Installér**.  

3. Du får vist siden **Konfiguration** , hvor alle apps er angivet. Hvis du ikke har de rette tilladelser eller den rigtige adgang til at installere appen, fremhæves de pågældende oplysninger. Du kan vælge de apps, du vil installere. Ved at **vælge Næste** får du vist **siden** Brugere. Hvis tilføjelsesprogrammet ikke er blevet sammenkædet af ISV, dirigeres du til siden Brugere. 

4.  **VælgEveryOne,Bestemte**  **brugere/grupper**,  **ellerJust meto**  for at angive, hvem tilføjelsesprogrammet er installeret til. Brug feltet Søg til at finde bestemte brugere eller grupper. Hvis du tester tilføjelsesprogrammet, skal du vælge **Er dette en testinstallation**. 

5. Vælg **Næste**. Alle appfunktioner og -tilladelser vises i en enkelt rude sammen med certificeringsoplysninger, hvis appen er blevet Microsoft 365 certificering. Ved at vælge certificeringslogoet kan brugeren se flere oplysninger om certificeringen.  

6. Gennemse, og vælg derefter **Afslut udrulning**.  

7. Der vises et grønt "flueben", når tilføjelsesprogrammet installeres. Følg vejledningen på siden for at teste tilføjelsesprogrammet. 

> [!NOTE]
> Brugere skal muligvis starte for Office for at få vist tilføjelsesprogrammets ikon på appbåndet. Outlook det kan tage op til 24 timer, før tilføjelsesapps vises på appbånd. 

Det er god praksis at informere brugere og grupper om, at det installerede tilføjelsesprogrammet er tilgængeligt. Overvej at sende en mail, der beskriver, hvornår og hvordan du bruger tilføjelsesprogrammet. Medtag eller link til Hjælp-indhold eller Ofte stillede spørgsmål, der kan hjælpe brugerne, hvis de har problemer med tilføjelsesprogrammet. 

## <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a>Overvejelser i forbindelse med tildeling af et tilføjelsesprogrammet til brugere og grupper 

Globale administratorer og Exchange-administratorer kan tildele et tilføjelsesprogrammet til alle eller til bestemte brugere og grupper. Hver indstilling har konsekvenser: 

- **Alle**  Denne indstilling tildeler tilføjelsesprogrammet til alle brugere i organisationen. Brug denne indstilling sparsomt og kun til tilføjelser, der er virkelig universale for din organisation. 

- **Brugere**  Hvis du tildeler et tilføjelsesprogrammet til en enkelt bruger og derefter installerer tilføjelsesprogrammet til en ny bruger, skal du først tilføje den nye bruger. 

- **Grupper**  Hvis du tildeler et tilføjelsesprogrammet til en gruppe, tildeles brugere, der er føjet til gruppen, automatisk tilføjelsesprogrammet. Når en bruger fjernes fra en gruppe, mister brugeren adgang til tilføjelsesprogrammet. I begge tilfælde kræves der ingen yderligere handling fra administratoren. 

- **Bare mig**  Hvis du kun tildeler et tilføjelsesprogrammet til dig selv, tildeles tilføjelsesprogrammet kun til din konto, hvilket er ideelt til test af tilføjelsesprogrammet. 

Den rigtige indstilling for din organisation afhænger af din konfiguration. Vi anbefaler dog, at du foretager tildelinger ved hjælp af grupper. Som administrator kan det være nemmere at administrere tilføjelser ved hjælp af grupper og styre medlemskabet af disse grupper i stedet for at tildele individuelle brugere hver gang. I nogle situationer kan det være en god ide at begrænse adgangen for et lille antal brugere ved at tildele brugere manuelt til bestemte brugere. 

### <a name="more-about-office-add-ins-security"></a>Flere oplysninger Office sikkerhed for tilføjelsesopdateringer 
Office-tilføjelsesprogram kombinerer en XML-manifestfil, der indeholder nogle metadata om tilføjelsesprogrammet, men det vigtigste peger på et webprogram, som indeholder alle koder og logik. Tilføjelses-ins kan variere i deres egenskaber. Tilføjelsesprogrammet kan f.eks.:
- Vise data. 
- Læs en brugers dokument for at tilbyde kontekstafhængige tjenester. 
- Læs og skriv data til og fra en brugers dokument for at skabe værdi for den pågældende bruger.  

Du kan finde flere oplysninger om typerne og egenskaberne for  [Office-tilføjelsesprogrammet i oversigten over](/office/dev/add-ins/overview/office-add-ins) tilføjelsesprogrammet Office især afsnittet "Office-tilføjelsesprogrammet". 

Hvis du vil interagere med brugerens dokument, skal tilføjelsesprogrammet angive hvilke tilladelser, det skal bruge i manifestet. En JavaScript API-adgangstilladelsesmodel i fem niveauer udgør grundlaget for beskyttelse af personlige oplysninger og sikkerhed for brugere opgaverude tilføjelsesprogrammet. Størstedelen af tilføjelses insendet i Office Store niveau LæsSkrivDokument, hvor næsten alle tilføjelses ins understøtter mindst LæsDokument-niveauet. Hvis du vil have mere at vide om tilladelsesniveauer, skal du  [seQuesting permissions for API use in content and opgaverude add-ins](/office/dev/add-ins/develop/requesting-permissions-for-api-use-in-content-and-task-pane-add-ins). 

Når du opdaterer et manifest, vil de typiske ændringer være et tilføjelsesprogrammets ikon og tekst. Nogle gange ændres tilføjelsesprogrammets kommandoer. Tilladelserne for tilføjelsesprogrammet ændres dog ikke. Det webprogram, hvor alle koder og logik til tilføjelsesprogrammet kører, kan ændres når som helst, hvilket er en del af webprogrammers karakter. 

Opdateringer til tilføjelser sker på følgende måde: 
- **Line of business-tilføjelsesprogrammet**: I dette tilfælde, hvor en administrator eksplicit overførte et manifest, kræver tilføjelsesprogrammet, at administratoren overfører et nyt manifest for at understøtte ændringer af metadata. Næste gang de relevante Office programmer starter, opdateres tilføjelsesprogrammet. Webprogrammet kan ændres når som helst. 

- **Office Store tilføjelsesprogrammet**: Næste gang de relevante Office Office Store-programmer startes, opdateres tilføjelsesprogrammet, hvis et tilføjelsesprogrammet opdateres i Office Store, næste gang de relevante Office-programmer starter. Webprogrammet kan ændres når som helst. 

> [!NOTE]
> I Word Excel og PowerPoint skal du bruge et  [SharePoint-appkatalog](https://dev.office.com/docs/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog)  til at installere tilføjelsesprogrammet til brugere i et lokalt miljø uden forbindelse til Microsoft 365 og/eller understøttelse af SharePoint-tilføjelsesprogrammet. Du Outlook bruge Exchange til at installere det i et lokalt miljø uden en forbindelse til Microsoft 365.  

## <a name="add-in-states"></a>Tilføjelsesprogrammets tilstande
Et tilføjelsesprogrammet kan være i  **entenOnorOffstate**  **** . 

| Stat | Sådan opstår tilstanden | Virkning |
|:-----|:-----|:-----|
|**Aktiv**  <br/> |Administratoren har uploadet tilføjelsesprogrammet og tildelt det til brugere eller grupper.  <br/> |Brugere og grupper, der er tildelt til tilføjelsesprogrammet, kan se det i de relevante klienter.  <br/> |
|**Deaktiveret**  <br/> |Administratoren har deaktiveret tilføjelsesprogrammet.  <br/> |Brugere og grupper, der er tildelt til tilføjelsesprogrammet, har ikke længere adgang til det.  <br/> Hvis tilføjelsesprogrammets tilstand ændres til Aktiv, har brugere og grupper adgang til det igen.  <br/> |
|**Slettet**  <br/> |Administratoren har slettet tilføjelsesprogrammet.  <br/> |Brugere og grupper, der er tildelt tilføjelsesprogrammet, har ikke længere adgang til det.  <br/> |
 
Overvej at slette et tilføjelsesprogrammet, hvis der ikke længere er nogen, der bruger det. Det kan f.eks. være en god ide at deaktivere et tilføjelsesprogrammet, hvis det kun bruges på bestemte tidspunkter af året. 

## <a name="manage-an-office-add-in-using-the-admin-center"></a>Administrere et Office via Administration

Efter udrulningen kan administratorer også administrere brugeradgang til tilføjelsesprogrammet. 

1. I Administration skal **du vælge Indstillinger** og derefter vælge **Integrerede apps**. 
2. På siden Integrerede apps vises der en liste over apps, som enten er enkelte tilføjelsesprogrammer eller tilføjelsesprogrammer, der er blevet sammenkædet med andre apps. 
3. Vælg en app  **medStatusofMore-apps**   **tilgængeligefor**  at  **åbneManagepane** . Status for flere  **tilgængelige apps Du**  ved, at der er flere integrationer fra isV'er, der endnu ikke er installeret. 
4. På  **fanenOverview**  skal du  **vælgeDeploy**. Nogle apps kræver, at du tilføjer brugere, før du kan vælge Installer. 
5.  **SelectUsers**,  **selectIs this a test deployment**, and then select  **eitherEntire organization,Specific**  **users/groupsorJust**   **me**. Du kan også  **vælgeTest-installation** , hvis du foretrækker at vente med at installere appen på hele organisationen. Bestemte brugere eller grupper kan være Microsoft 365 gruppe, en sikkerhedsgruppe eller en distributionsgruppe. 
6.  **VælgOpdatering,**  og vælg derefter **Udført**. Du kan nu vælge **Installer** på **fanen** Oversigt. 
7. Gennemse appoplysningerne, og vælg  **derefterInstallation**.
8.  **SelectDonepå**  siden **Installation fuldført**, og gennemgå oplysningerne om testen eller den komplette installation på  **fanenOvervisning** . 
9. Hvis appen har status Afventer  **Opdatering, kan** du klikke på appen for at åbne **ruden** Administrer og opdatere appen. 
10. Hvis du kun vil opdatere brugere, skal **du vælge fanen** Brugere og foretage de relevante ændringer. Vælg **Opdater,** når du har foretaget dine ændringer.  

## <a name="delete-an-add-in"></a>Slette et tilføjelsesprogrammet

Du kan også slette et tilføjelsesprogrammet, der blev installeret.

1. I Administration skal **du vælge Indstillinger** og derefter vælge **Integrerede apps** .
2. Vælg en række for at få vist administrationsruden. 
3. Vælg **fanen** Konfiguration. 
4. Vælg det tilføjelsesprogrammet, du vil slette, og vælg derefter **Fjern**.  

> [!NOTE]
>  Hvis tilføjelsesprogrammet er blevet installeret af en anden administrator, deaktiveres knappen Fjern. Kun den administrator, der har installeret appen eller en global administrator, kan slette tilføjelsesprogrammet.

## <a name="scenarios-where-exchange-admin-cannot-deploy-an-add-in"></a>Scenarier, hvor Exchange kan installere et tilføjelsesprogrammet 

Der er to tilfælde, hvor Exchange administrator ikke kan installere et tilføjelsesprogrammet:
- Hvis et tilføjelsesprogrammet kræver tilladelse til MS Graph API'er og skal have tilladelse fra en global administrator.
- Hvis et tilføjelsesprogrammet er sammenkædet med to eller flere tilføjelsesapps og webapps, og mindst ét af disse tilføjelsesapps installeres af en anden administrator (exchange/global), og brugertildelingen ikke er ensartet. Vi tillader kun installation af tilføjelsesprogrammer, når brugertildelingen er den samme for alle de allerede installerede apps.  


## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="which-administrator-role-do-i-need-to-access-integrated-apps"></a>Hvilken administratorrolle skal jeg have for at få adgang til integrerede apps?

Kun globale administratorer kan få adgang til integrerede apps. Integrerede apps vises ikke i venstre navigationslinje for andre administratorer.

### <a name="why-do-i-see-add-in-in-the-left-nav-under-setting-but-not-integrated-apps"></a>Hvorfor kan jeg se tilføjelsesprogrammet i venstre navigationslinje under Indstilling, men ikke integrerede apps?

Der kan være flere årsager:

- Den administrator, der er logget på, Exchange administrator.
- Kunden er i national cloud og integreret appoplevelse er tilgængelig for kunder med national cloud endnu.

### <a name="what-apps-can-i-deploy-from-integrated-apps"></a>Hvilke apps kan jeg installere fra integrerede apps?

Integrerede apps gør det muligt at installere tilføjelsesprogrammer til webapps, Teams apps, Excel, PowerPoint, Word Outlook-tilføjelsesprogrammer SPFx apps. For tilføjelsesprogrammer understøtter integrerede apps installation Exchange onlinepostkasser og ikke lokale Exchange postkasser.

### <a name="can-administrators-delete-or-remove-apps"></a>Kan administratorer slette eller fjerne apps?

Ja. Globale administratorer kan slette eller fjerne apps.

- Vælg en app fra listevisningen. På fanen **Konfiguration skal** du vælge, hvilke apps der skal fjernes.  

### <a name="is-integrated-apps-available-in-sovereign-cloud"></a>Er integrerede apps tilgængelige i national cloud?

Nej. Integrerede apps er ikke tilgængelige for nationale skykunder.

### <a name="is-integrated-apps-available-in-government-clouds"></a>Er integrerede apps tilgængelige i offentlige skyer?

Nej. Integrerede apps er ikke tilgængelige for skybaserede offentlige kunder.
