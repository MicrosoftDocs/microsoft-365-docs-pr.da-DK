---
title: Test og udrul Microsoft 365 Apps af partnere på portalen integrerede apps
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
description: Find, test og udrul Microsoft- og Microsoft-partnerapps til brugere og grupper i din organisation fra portalen integrerede apps i Microsoft 365 Administration.
ms.openlocfilehash: 862d70fe57974d2940458cb1fa59d05674d7ff58
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115493"
---
# <a name="test-and-deploy-microsoft-365-apps-by-partners-in-the-integrated-apps-portal"></a>Test og udrul Microsoft 365 Apps af partnere på portalen integrerede apps

Den Microsoft 365 Administration giver dig fleksibiliteten til at udrulle apps fra en enkelt butik, brugerdefinerede forretningslinjer og Microsoft 365 partnerapps fra en enkelt placering. Du kan få adgang til placeringen i indstillingerne for Microsoft Administration Center i Integrerede apps. Muligheden for at finde, teste og udrulle apps, der er købt og licenseret af Microsoft-partnere, fra portalen til integrerede apps giver den bekvemmelighed og de fordele, som din organisation kræver for at holde forretningstjenesterne opdateret regelmæssigt og køre effektivt.

Du kan finde flere oplysninger om køb og licensering Microsoft 365 apps fra partnere i din organisation under [Administrer og udrul Microsoft 365 Apps fra Microsoft 365 Administration](https://techcommunity.microsoft.com/t5/microsoft-365-blog/manage-and-deploy-microsoft-365-apps-from-the-microsoft-365/ba-p/1194324).

Du kan finde flere oplysninger om, hvordan partnere opretter disse apps, under [Sådan planlægger du et SaaS-tilbud til den kommercielle markedsplads](https://go.microsoft.com/fwlink/?linkid=2158277)

Portalen integrerede apps er kun tilgængelig for globale administratorer og er kun tilgængelig for kunder over hele verden. Denne funktion er ikke tilgængelig i nationale cloudmiljøer og offentlige cloudmiljøer.

Portalen Integrerede apps viser en liste over apps, som omfatter enkelte apps og Microsoft 365 apps fra partnere, der er udrullet i din organisation. Det er kun webapps, SPFx apps, Office tilføjelsesprogrammer og Teams apps, der vises. For webapps kan du se to slags apps.

- SaaS-apps, der er tilgængelige i appsource.microsoft.com, og som kan udrulles af administratorer, der giver samtykke på vegne af organisationen.
- SAML-galleriapps, der er sammenkædet med Office tilføjelsesprogrammer.

## <a name="manage-apps-in-the-integrated-apps-portal"></a>Administrer apps på portalen integrerede apps

Du kan administrere test og udrulning af købte og licenserede Microsoft 365 Apps fra partnere.

1. Vælg **Indstillinger** i Administration, og vælg derefter **Integrerede apps**.

2. Vælg en app med **status** for **Flere apps, der er tilgængelige** for at åbne ruden **Administrer** . Status for **flere tilgængelige apps** giver dig besked om, at der er flere integrationer fra ISV'erne, der endnu ikke er udrullet.

3. Under fanen **Oversigt** skal du vælge **Installér**. Nogle apps kræver, at du tilføjer brugere, før du kan vælge Udrul.

4. Vælg  **Brugere**, vælg **Er dette en testinstallation**, og vælg derefter **Hele organisationen**, **Bestemte brugere/grupper** eller **Bare mig**. Du kan også vælge **Test udrulning** , hvis du foretrækker at vente med at installere appen i hele organisationen. Bestemte brugere eller grupper kan være en Microsoft 365 gruppe, en sikkerhedsgruppe eller en distributionsgruppe.

5. Vælg **Opdater** og derefter **Udført**. Du kan nu vælge Udrul under fanen Oversigt.

6. Gennemse appoplysningerne, og vælg derefter **Installér**.

7. Vælg **Udført** på siden Installation fuldført, og gennemse detaljerne om testen eller den komplette installation under fanen **Oversigt** .

8. Hvis appen har statussen **Opdater ventende**, kan du klikke på appen for at åbne ruden Administrer og opdatere appen.

## <a name="find-published-apps-for-testing-and-full-deployment"></a>Find publicerede apps til test og fuld installation

Du kan finde, teste og udrulle udgivne apps, der ikke allerede vises på listen på siden Integrerede apps. Ved at købe og licensere apps fra Administration kan du føje Microsoft- og Microsoft-partnerapps til din liste fra en enkelt placering.

1. Vælg **Indstillinger** i venstre navigationsrude i Administration, og vælg derefter <a href="https://admin.microsoft.com/adminportal/home?#/Settings/IntegratedApps" target="_blank">**Integrerede apps**</a>.

2. Vælg **Hent apps** for at få vist appsene.

3. På siden **Microsoft 365 Apps** publicerede apps skal du vælge den app, du vil installere, ved at vælge **Hent den nu**. De apps, der vises, er primært Word-, PowerPoint-, Excel-, Outlook-tilføjelsesprogrammer, Teams-apps og SharePoint-apps (bygget på SharePoint Framework teknologi). Acceptér tilladelserne, og vælg **Fortsæt**.

5. Vælg **Installér** øverst på siden ud for den meddelelse, der refererer til, og som venter på at blive installeret.

    Hvis den valgte app er knyttet til et SaaS-tilbud af en ISV, vises alle de andre apps, der er en del af dette sammenkædede tilbud, på siden Konfiguration. Hvis du vælger at installere alle apps, skal du vælge **Næste**. Ellers skal du vælge **Rediger** og vælge, hvilke apps du vil installere. Nogle apps kræver, at du tilføjer brugere, før du kan vælge **Udrul**.

6. Vælg **Tilføj brugere**, vælg **Er dette en testinstallation**, og vælg derefter **Hele organisationen** eller **Specifikke brugere/grupper** eller **Bare mig**.

    Bestemte brugere/grupper kan være en Microsoft 365 gruppe, en sikkerhedsgruppe eller en distribueret gruppe. Du kan også vælge **Test udrulning** , hvis du foretrækker at vente med at installere appen i hele organisationen.

7. Vælg **Næste** for at gå til siden **Acceptér anmodning om tilladelse** . Appfunktionerne og -tilladelserne for hver af appsene vises. Hvis appen har brug for samtykke, skal du vælge **Acceptér tilladelser**. Det er kun en global administrator, der kan give samtykke.

8. Vælg **Næste** for at gennemse installationen og vælge **Afslut installation**. Du kan få vist installationen fra fanen **Oversigt** ved at vælge **Få vist denne installation**. I Microsoft 365 Administration kan du se status for hver udrullet app og den dato, hvor du installerede appen.

> [!NOTE]
> Hvis en app tidligere er blevet udrullet fra et andet sted end portalen til integrerede apps, er **installationstypen** **brugerdefineret.**

## <a name="unsupported-scenarios"></a>Scenarier, der ikke understøttes

Du kan ikke udrulle en enkelt store-app eller Microsoft 365 Apps af partner fra portalen integrerede apps til følgende scenarier.

- Det samme tilføjelsesprogram er knyttet til mere end ét SaaS-tilbud.
- SaaS-tilbuddet er knyttet til tilføjelsesprogrammer, men det integreres ikke med Microsoft Graph, og der er ikke angivet noget AAD-app-id.
- SaaS-tilbuddet er knyttet til tilføjelsesprogrammer, men AAD-app-id, der leveres til Microsoft Graph integration, deles på tværs af flere SaaS-tilbud.

## <a name="upload-custom-line-of-business-apps-for-testing-and-full-deployment"></a>Upload brugerdefinerede line of business-apps til test og fuld udrulning

1. Vælg **Indstillinger** og derefter **Integrerede apps** i venstre navigationsrude i Administration.

2. Vælg **Upload brugerdefinerede apps**. Kun en brugerdefineret applinje til Word, PowerPoint, Excel og Outlook understøttes.

3. Upload manifestfilen fra enheden, eller tilføj et URL-link. Nogle apps kræver, at du tilføjer brugere, før du kan vælge Udrul.

4. Vælg **Tilføj brugere**, vælg **Er dette en testinstallation**, og vælg **Hele organisationen** eller **Specifikke brugere/grupper** eller **Bare mig**.

    Bestemte brugere/grupper kan være en Microsoft 365 gruppe, en sikkerhedsgruppe eller en distribueret gruppe. Du kan også vælge **Test udrulning** , hvis du vil vente med at installere appen i hele organisationen.

5. Vælg **Næste** for at gå til siden **Acceptér anmodning om tilladelse** . Appfunktionerne og -tilladelserne for appsene vises. Hvis appen har brug for samtykke, skal du vælge **Acceptér tilladelser**. Det er kun en global administrator, der kan give samtykke.

6. Vælg **Næste** for at gennemse installationen og vælge **Afslut installation**. Du kan få vist installationen fra fanen **Oversigt** ved at vælge **Få vist denne installation**.

## <a name="prepare-to-deploy-add-ins-in-integrated-apps"></a>Forbered installation af tilføjelsesprogrammer i integrerede apps

Office tilføjelsesprogrammer hjælper dig med at tilpasse dine dokumenter og strømline den måde, du får adgang til oplysninger på internettet på (se Begynd at bruge dit Office-tilføjelsesprogram). 

Tilføjelsesprogrammer giver følgende fordele: 

- Når det relevante Office program starter, downloades tilføjelsesprogrammet automatisk. Hvis tilføjelsesprogrammet understøtter kommandoer i tilføjelsesprogrammet, vises tilføjelsesprogrammet automatisk på båndet i det Office program. 

- Tilføjelsesprogrammer vises ikke længere for brugere, hvis administratoren slår tilføjelsesprogrammet fra eller sletter det, eller hvis brugeren er fjernet fra Azure Active Directory eller fra en gruppe, som tilføjelsesprogrammet er tildelt. 

Tilføjelsesprogrammer understøttes på tre skrivebordsplatforme Windows, Mac og Online Office apps. Det understøttes også i iOS og Android (kun Outlook mobile tilføjelsesprogrammer). 

Det kan tage op til 24 timer, før et tilføjelsesprogram vises for klienten for alle brugere. 

I dag kan både Exchange administratorer og globale administratorer udrulle tilføjelsesprogrammer fra integrerede apps.   

### <a name="before-you-begin"></a>Før du begynder

Installation af tilføjelsesprogrammer kræver, at brugerne bruger Microsoft 365 Business-licenser (Business Basic, Business Standard, Business Premium), Office 365 Enterprise licenser (E1/E3/E5/F3) eller Microsoft 365 Enterprise licenser (E3/E5/F3). Brugerne skal også være logget på Office ved hjælp af deres organisations-id) og have Exchange Online og aktive Exchange Online postkasser. Din abonnementsmappe skal enten være i eller sammenkædet med Azure Active Directory. 

Installationen understøtter ikke følgende: 

- Tilføjelsesprogrammer, der er målrettet til Word, Excel eller PowerPoint i Office 2013 
- En katalogtjeneste i det lokale miljø 
- Installation af tilføjelsesprogram i en Exchange postkasse i det lokale miljø 
- Installation af COM (Component Object Model) eller Visual Studio Tools for Office -tilføjelsesprogrammer (VSTO). 
- Udrulninger af Microsoft 365, der ikke indeholder Exchange Online, f.eks. Microsoft 365 Apps for Business og Microsoft 365 Apps for Enterprise.  

### <a name="office-requirements"></a>krav til Office 

I forbindelse med Word-, Excel- og PowerPoint-tilføjelsesprogrammer skal brugerne bruge et af følgende: 
- På en Windows enhed, version 1704 eller nyere af Microsoft 365 Business-licenser (Business Basic, Business Standard, Business Premium), Office 365 Enterprise licenser (E1/E3/E5/F3) eller Microsoft 365 Enterprise licenser (E3/E5/F3). 
- På en Mac, version 15.34 eller nyere. 

Brugerne skal bruge en af følgende fremgangsmåder til Outlook: 
- Version 1701 eller nyere af Microsoft 365 Business-licenser (Business Basic, Business Standard, Business Premium), Office 365 Enterprise licenser (E1/E3/E5/F3) eller Microsoft 365 Enterprise licenser (E3/E5/F3). 
- Version 1808 eller nyere af Office Professional Plus 2019 eller Office Standard 2019. 
- Version 16.0.4494.1000 eller nyere af Office Professional Plus 2016 (MSI) eller Office Standard 2016 (MSI).
    > [!NOTE]
    > MSI-versioner af Outlook viser tilføjelsesprogrammer, der er installeret af administratorer, på det relevante Outlook bånd og ikke i afsnittet "Mine tilføjelsesprogrammer".  
- Version 15.0.4937.1000 eller nyere af Office Professional Plus 2013 (MSI) eller Office Standard 2013 (MSI).
- Version 16.0.9318.1000 eller nyere af Office 2016 til Mac. 
- Version 2.75.0 eller nyere af Outlook mobil til iOS. 
- Version 2.2.145 eller nyere af Outlook mobil til Android. 



### <a name="exchange-online-requirements"></a>krav til Exchange Online 
Microsoft Exchange gemmer tilføjelsesprogrammets manifester i din organisations lejer. Den administrator, der installerer tilføjelsesprogrammer, og de brugere, der modtager disse tilføjelsesprogrammer, skal være på en version af Exchange Online, der understøtter OAuth-godkendelse. 

Kontakt organisationens Exchange administrator for at finde ud af, hvilken konfiguration der er i brug. OAuth-forbindelse pr. bruger kan bekræftes ved hjælp af PowerShell-cmdlet'en [Test-OAuthConnectivity](/powershell/module/exchange/test-oauthconnectivity) . 

### <a name="user-and-group-assignments"></a>Bruger- og gruppetildelinger
Installationen af tilføjelsesprogrammet understøttes i øjeblikket af de fleste grupper, der understøttes af Azure Active Directory, herunder Microsoft 365 grupper, distributionslister og sikkerhedsgrupper. Udrulning understøtter brugere i grupper på øverste niveau eller grupper uden overordnede grupper, men ikke brugere i indlejrede grupper eller grupper, der har overordnede grupper. 

> [!NOTE]
> Ikke-mailaktiverede sikkerhedsgrupper understøttes ikke i øjeblikket. 

I følgende eksempel tildeles gruppen Sandra, Sheila og gruppen Salgsafdeling til et tilføjelsesprogram. Da salgsafdelingen for vestkysten er en indlejret gruppe, er Bert og Fred ikke tildelt et tilføjelsesprogram. 

![Diagram over salgsafdeling.](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)

### <a name="find-out-if-a-group-contains-nested-groups"></a>Find ud af, om en gruppe indeholder indlejrede grupper

Den nemmeste måde at registrere, om en gruppe indeholder indlejrede grupper, er ved at få vist gruppens visitkort i Outlook. Hvis du angiver gruppenavnet i feltet **Til** i en mail og derefter vælger gruppenavnet, når det fortolkes, vises det, hvis det indeholder brugere eller indlejrede grupper. I eksemplet nedenfor vises ingen brugere og kun to undergrupper under fanen **Medlemmer** på visitkortet Outlook for testgruppen. 

![Fanen Medlemmer på Outlook visitkort.](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)

Du kan udføre den modsatte forespørgsel ved at løse problemet for gruppen for at se, om den er medlem af en gruppe. I eksemplet nedenfor kan du se under fanen <b>Medlemskab</b> på Outlook visitkort, at Undergruppe 1 er medlem af testgruppen. 

![Fanen Medlemskab på Outlook visitkort.](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)

Bemærk, at du kan bruge API'en Azure Active Directory Graph til at køre forespørgsler for at finde listen over grupper i en gruppe. Du kan få flere oplysninger under [Handlinger på grupper | Graph API-reference](/previous-versions/azure/ad/graph/api/groups-operations). 

## <a name="recommended-approach-for-deploying-office-add-ins"></a>Anbefalet fremgangsmåde til installation af Office tilføjelsesprogrammer 
Hvis du vil udrulle tilføjelsesprogrammer ved hjælp af en faseinddelt tilgang, anbefaler vi følgende: 
1. Udrul tilføjelsesprogrammet til et lille sæt virksomhedsinteressenter og medlemmer af it-afdelingen. Du kan aktivere flaget **Er dette en testinstallation**. Hvis installationen lykkes, skal du gå til trin 2. 

2. Udrul tilføjelsesprogrammet til flere enkeltpersoner i virksomheden. Evaluer igen resultaterne, og fortsæt med fuld udrulning, hvis det lykkes. 

3. Udfør en komplet udrulning til alle brugere. Slå flaget fra **Er dette en testinstallation**. 

Afhængigt af målgruppens størrelse kan du tilføje eller fjerne udrulningstrin.  

## <a name="deploy-an-office-add-in-using-the-admin-center"></a>Udrul et Office-tilføjelsesprogram ved hjælp af Administration 

1. Vælg **Indstillinger** i Administration, og vælg derefter **Integrerede apps**. 

2. Vælg **Hent apps** øverst på siden. AppSource indlæses i et integreret format. Søg efter et tilføjelsesprogram, eller find det ved at klikke på Produkt i venstre navigationsrude.  Hvis tilføjelsesprogrammet er kædet sammen af ISV'en til en SaaS-app eller andre apps og tilføjelsesprogrammer, og hvis SaaS-appen er en betalt app, vises der en dialogboks, hvor du enten kan købe licensen eller Udrul. Uanset om du har købt licensen eller ej, kan du gå videre med udrulningen. Vælg **Installér**.  

3. Du får vist siden **Konfiguration** , hvor alle apps er angivet. Hvis du ikke har tilladelser eller har den rette adgang til at installere appen, fremhæves de respektive oplysninger. Du kan vælge de apps, du vil installere. Når du vælger **Næste**, får du vist siden **Brugere** . Hvis tilføjelsesprogrammet ikke er blevet linket af ISV'en, bliver du dirigeret til siden Brugere. 

4. Vælg **Alle**, **Specifikke brugere/grupper** eller **Bare mig** for at angive, hvem tilføjelsesprogrammet skal udrulles til. Brug søgefeltet til at finde bestemte brugere eller grupper. Hvis du tester tilføjelsesprogrammet, skal du vælge **Er dette en testinstallation**. 

5. Vælg **Næste**. Alle appfunktioner og -tilladelser vises i en enkelt rude sammen med certificeringsoplysninger, hvis appen har Microsoft 365 certificering. Hvis du vælger certificeringslogoet, kan brugeren se flere oplysninger om certificeringen.  

6. Gennemse, og vælg derefter **Afslut installation**.  

7. Der vises et grønt "kryds"-ikon, når tilføjelsesprogrammet installeres. Følg vejledningen på siden for at teste tilføjelsesprogrammet. 

> [!NOTE]
> Brugerne skal muligvis genstarte Office for at få vist ikonet for tilføjelsesprogrammet på appbåndet. Outlook tilføjelsesprogrammer kan tage op til 24 timer, før de vises på appbånd. 

Det er god praksis at informere brugere og grupper om, at det udrullede tilføjelsesprogram er tilgængeligt. Overvej at sende en mail, der beskriver, hvornår og hvordan du bruger tilføjelsesprogrammet. Medtag eller opret et link til indhold eller ofte stillede spørgsmål, der kan hjælpe brugerne, hvis de har problemer med tilføjelsesprogrammet. 

## <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a>Overvejelser ved tildeling af et tilføjelsesprogram til brugere og grupper 

Globale administratorer og Exchange administratorer kan tildele et tilføjelsesprogram til alle eller til bestemte brugere og grupper. Hver indstilling har konsekvenser: 

- **Alle** Denne indstilling tildeler tilføjelsesprogrammet til alle brugere i organisationen. Brug denne indstilling sparsomt og kun til tilføjelsesprogrammer, der er universelle for din organisation. 

- **Brugere** Hvis du tildeler et tilføjelsesprogram til en enkelt bruger og derefter installerer tilføjelsesprogrammet til en ny bruger, skal du først tilføje den nye bruger. 

- **Grupper** Hvis du tildeler et tilføjelsesprogram til en gruppe, tildeles de brugere, der føjes til gruppen, automatisk tilføjelsesprogrammet. Når en bruger fjernes fra en gruppe, mister brugeren adgangen til tilføjelsesprogrammet. I begge tilfælde kræves der ingen yderligere handling fra administratoren. 

- **Bare mig** Hvis du kun tildeler et tilføjelsesprogram til dig selv, tildeles tilføjelsesprogrammet kun til din konto, hvilket er ideelt til test af tilføjelsesprogrammet. 

Den rigtige indstilling for din organisation afhænger af din konfiguration. Vi anbefaler dog, at du foretager tildelinger ved hjælp af grupper. Som administrator kan det være nemmere at administrere tilføjelsesprogrammer ved hjælp af grupper og styre medlemskabet af disse grupper i stedet for at tildele individuelle brugere hver gang. I nogle situationer kan det være en god idé at begrænse adgangen til et lille sæt brugere ved at tildele tildelinger til bestemte brugere ved at tildele brugere manuelt. 

### <a name="more-about-office-add-ins-security"></a>Mere om sikkerhed i forbindelse med Office tilføjelsesprogrammer 
Office tilføjelsesprogrammer kombinerer en XML-manifestfil, der indeholder metadata om tilføjelsesprogrammet, men vigtigst af alt peger på et webprogram, der indeholder al kode og logik. Tilføjelsesprogrammer kan variere i deres funktioner. Tilføjelsesprogrammer kan f.eks.:
- Vis data. 
- Læs en brugers dokument for at levere kontekstafhængige tjenester. 
- Læs og skriv data til og fra en brugers dokument for at give den pågældende bruger værdi.  

Du kan få flere oplysninger om typerne og egenskaberne i Office tilføjelsesprogrammer under [oversigt over Office platform til tilføjelsesprogrammer](/office/dev/add-ins/overview/office-add-ins), især afsnittet "Anatomi af et Office-tilføjelsesprogram". 

Hvis du vil interagere med brugerens dokument, skal tilføjelsesprogrammet deklarere, hvilken tilladelse det har brug for i manifestet. En JavaScript API-adgangsrettighedsmodel på fem niveauer udgør grundlaget for beskyttelse af personlige oplysninger og sikkerhed for brugere af tilføjelsesprogrammer i opgaverude. De fleste tilføjelsesprogrammer i Office Store er ReadWriteDocument-niveauet, og næsten alle tilføjelsesprogrammer understøtter mindst ReadDocument-niveauet. Du kan få flere oplysninger om tilladelsesniveauer under [Anmodning om tilladelser til API-brug i indhold og tilføjelsesprogrammer i opgaveruden](/office/dev/add-ins/develop/requesting-permissions-for-api-use-in-content-and-task-pane-add-ins). 

Når du opdaterer et manifest, er de typiske ændringer af et tilføjelsesprograms ikon og tekst. Indimellem ændres tilføjelseskommandoer. Tilladelserne for tilføjelsesprogrammet ændres dog ikke. Webprogrammet, hvor al kode og logik for tilføjelsesprogrammet kører, kan ændres når som helst, hvilket er arten af webprogrammer. 

Opdateringer til tilføjelsesprogrammer sker på følgende måde: 
- **Tilføjelsesprogram til line of business**: Hvis en administrator eksplicit har uploadet et manifest, kræver tilføjelsesprogrammet, at administratoren uploader en ny manifestfil for at understøtte ændringer af metadata. Næste gang de relevante Office programmer starter, opdateres tilføjelsesprogrammet. Webprogrammet kan ændres når som helst. 

- **Office Store tilføjelsesprogram**: Når en administrator har valgt et tilføjelsesprogram fra Office Store, opdateres tilføjelsesprogrammet, næste gang de relevante Office programmer starter, hvis et tilføjelsesprogram opdateres i Office Store. Webprogrammet kan ændres når som helst. 

> [!NOTE]
> I forbindelse med Word, Excel og PowerPoint bruge et [SharePoint app-katalog](/sharepoint/dev/sp-add-ins/publish-sharepoint-add-ins) til at installere tilføjelsesprogrammer til brugere i et lokalt miljø uden forbindelse til Microsoft 365 og/eller understøttelse af SharePoint tilføjelsesprogrammer er påkrævet. Til Outlook bruge Exchange kontrolpanel til at installere i et lokalt miljø uden forbindelse til Microsoft 365.  

## <a name="add-in-states"></a>Tilstande for tilføjelsesprogrammer
Et tilføjelsesprogram kan være i tilstanden **Til** eller **Fra** . 

| Staten | Sådan opstår tilstanden | Indvirkning |
|:-----|:-----|:-----|
|**Aktive**  <br/> |Administration uploadet tilføjelsesprogrammet og tildelt det til brugere eller grupper.  <br/> |Brugere og grupper, der er tildelt tilføjelsesprogrammet, kan se det i de relevante klienter.  <br/> |
|**Slukket**  <br/> |Administration slået tilføjelsesprogrammet fra.  <br/> |Brugere og grupper, der er tildelt tilføjelsesprogrammet, har ikke længere adgang til det.  <br/> Hvis tilføjelsesprogrammets tilstand ændres til Aktiv, har brugerne og grupperne adgang til det igen.  <br/> |
|**Slettet**  <br/> |Administration slettede tilføjelsesprogrammet.  <br/> |Brugere og grupper, der er tildelt tilføjelsesprogrammet, har ikke længere adgang til det.  <br/> |
 
Overvej at slette et tilføjelsesprogram, hvis ingen bruger det længere. Hvis du f.eks. deaktiverer et tilføjelsesprogram, kan det give mening, hvis et tilføjelsesprogram kun bruges på bestemte tidspunkter af året. 

## <a name="manage-an-office-add-in-using-the-admin-center"></a>Administrer et Office-tilføjelsesprogram ved hjælp af Administration

Efter installationen kan administratorer også administrere brugeradgang til tilføjelsesprogrammer. 

1. Vælg **Indstillinger** i Administration, og vælg derefter **Integrerede apps**. 
2. På siden Integrerede apps vises der en liste over apps som enten enkelttilføjelsesprogram eller tilføjelsesprogrammer, der er sammenkædet med andre apps. 
3. Vælg en app med **status** for **Flere apps, der er tilgængelige** for at åbne ruden **Administrer** . Status for **flere tilgængelige apps** giver dig besked om, at der er flere integrationer fra ISV'erne, der endnu ikke er udrullet. 
4. Under fanen **Oversigt** skal du vælge **Installér**. Nogle apps kræver, at du tilføjer brugere, før du kan vælge Udrul. 
5. Vælg **Brugere**, vælg **Er dette en testinstallation**, og vælg derefter enten **Hele organisationen**, **Specifikke brugere/grupper** eller **Bare mig**. Du kan også vælge **Test udrulning** , hvis du foretrækker at vente med at installere appen i hele organisationen. Bestemte brugere eller grupper kan være en Microsoft 365 gruppe, en sikkerhedsgruppe eller en distributionsgruppe. 
6. Vælg **Opdater** , og vælg derefter **Udført**. Du kan nu vælge **Udrul** under fanen **Oversigt** . 
7. Gennemse appoplysningerne, og vælg derefter **Installér**.
8. Vælg **Udført** på siden **Installation fuldført** , og gennemse detaljerne om testen eller den komplette installation under fanen **Oversigt** . 
9. Hvis appen har statussen **Opdater ventende**, kan du klikke på appen for at åbne ruden **Administrer** og opdatere appen. 
10. Hvis du kun vil opdatere brugere, skal du vælge fanen **Brugere** og foretage den relevante ændring. Vælg **Opdater** , når du har foretaget dine ændringer.  

## <a name="delete-an-add-in"></a>Slet et tilføjelsesprogram

Du kan også slette et tilføjelsesprogram, der er installeret.

1. Vælg **Indstillinger** i Administration, og vælg derefter **Integrerede apps** .
2. Vælg en række for at få vist administrationsruden. 
3. Vælg fanen **Konfiguration** . 
4. Vælg det tilføjelsesprogram, du vil slette, og vælg derefter **Fjern**.  

> [!NOTE]
>  Hvis tilføjelsesprogrammet er blevet installeret af en anden administrator, deaktiveres knappen Fjern. Det er kun den administrator, der har installeret appen eller en global administrator, der kan slette tilføjelsesprogrammet.

## <a name="scenarios-where-exchange-admin-cannot-deploy-an-add-in"></a>Scenarier, hvor Exchange administrator ikke kan installere et tilføjelsesprogram 

Der er to tilfælde, hvor et Exchange Administration ikke kan installere et tilføjelsesprogram:
- Hvis et tilføjelsesprogram skal have tilladelse til MS Graph API'er og skal have samtykke fra en global administrator.
- Hvis et tilføjelsesprogram er sammenkædet med to eller flere tilføjelsesprogrammer og webapps, og mindst ét af disse tilføjelsesprogrammer installeres af en anden administrator (exchange/global), og brugertildelingen ikke er ensartet. Vi tillader kun installation af tilføjelsesprogrammer, når brugertildelingen er den samme for alle de apps, der allerede er installeret.  


## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="which-administrator-role-do-i-need-to-access-integrated-apps"></a>Hvilken administratorrolle skal jeg have for at få adgang til integrerede apps?

Det er kun globale administratorer, der kan få adgang til integrerede apps. Integrerede apps vises ikke i venstre navigationsrude for andre administratorer.

### <a name="why-do-i-see-add-in-in-the-left-nav-under-setting-but-not-integrated-apps"></a>Hvorfor kan jeg se tilføjelsesprogrammet i venstre navigationsrude under Indstilling, men ikke integrerede apps?

Der kan være et par årsager:

- Den administrator, der er logget på, er en Exchange administrator.
- Kunden er i national cloud, og integreret appoplevelse er tilgængelig for nationale cloudkunder endnu.

### <a name="what-apps-can-i-deploy-from-integrated-apps"></a>Hvilke apps kan jeg installere fra integrerede apps?

Integrerede apps gør det muligt at installere Web Apps, Teams app, Excel, PowerPoint, Word, Outlook tilføjelsesprogrammer og SPFx apps. I forbindelse med tilføjelsesprogrammer understøtter integrerede apps installation til Exchange onlinepostkasser og ikke i det lokale miljø Exchange postkasser.

### <a name="can-administrators-delete-or-remove-apps"></a>Kan administratorer slette eller fjerne apps?

Ja. Globale administratorer kan slette eller fjerne apps.

- Vælg en app i listevisningen. Under fanen **Konfiguration** skal du vælge, hvilke apps der skal fjernes.  

### <a name="is-integrated-apps-available-in-sovereign-cloud"></a>Er integrerede apps tilgængelige i nationale cloudmiljøer?

Nej. Integrerede apps er ikke tilgængelige for nationale cloudkunder.

### <a name="is-integrated-apps-available-in-government-clouds"></a>Er integrerede apps tilgængelige i offentlige cloudmiljøer?

Nej. Integrerede apps er ikke tilgængelige for offentlige cloudkunder.
