---
title: Interaktioner mellem grupper af tjenester
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Interaktioner mellem grupper af tjenester
ms.openlocfilehash: 226c1588c0275c3349d0fd996dd68f5748f11cd6
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/17/2021
ms.locfileid: "63594205"
---
# <a name="groups-services-interactions"></a>Interaktioner mellem grupper af tjenester

Microsoft 365 Groups provides a common fabric for several services and workloads within the Microsoft 365 platform to deliver a connected experience for end users. En gruppe af Microsoft 365 kerne har til at levere:

- En måde at administrere medlemskabet på (Azure AD)
- Et sted, hvor beskeder og samtaler kan foregå (Exchange, Microsoft Teams, Yammer)
- Et sted, hvor filer skal gemmes (SharePoint)
- En kalender til planlægning (Exchange)
- En notesbog til at tage noter (OneNote)

I forbindelse med oprettelse af grupper er flere andre ressourcer også klargjort, men de er ikke synlige, før de åbnes for første gang fra tjenesten:

- En tavle til administration af gruppeopgaver (Planner)
- Et arbejdsområde til rapportering (Power BI)
- Et område til delte videoer (Microsoft Stream)
- Et område til delte formularer (formularer)

På Microsoft 365 kan andre tjenester interagere med Microsoft 365 grupper for at levere yderligere funktionalitet og funktioner til gruppemedlemmer.
Eksempler på dette omfatter:

- Power Apps til apps
- Power Automate for arbejdsprocesser
- Project på internettet og Roadmap til vandfaldsbaseret projektstyring
- Teams til kanalbaserede samtaler
- Yammer til interessegrupper

## <a name="user-interactions-with-groups"></a>Brugerinteraktion med grupper

Microsoft 365 grupper kan oprettes og administreres ud fra forskellige grænseflader, både af administratorer og slutbrugere. 

### <a name="administrative-experiences"></a>Administrative oplevelser

Administratorer kan oprette og administrere Microsoft 365-grupper fra flere af arbejdsbelastningsadministrationscentrene, kommandolinjegrænseflader, der understøtter scripting, samt brugerdefinerede indbyggede apps, der interagerer med Graph API. Den eneste undtagelse til dette er Yammer-grupper – som skal oprettes fra Yammer-webgrænseflade.

**Relaterede indstillinger**

På tværs af de forskellige administrative grænseflader, der kan administrere gruppeindstillinger, findes der flere overlap, du skal være opmærksom på.

**Microsoft 365 Administration**

I Microsoft 365 Administration er gæsteadgang til grupper som standard aktiveret, og det samme er muligheden for at tillade ejere at tilføje gæster. Der er ingen yderligere kontrolelementer på organisationsniveau tilgængelige for grupper fra denne administration.

**Azure AD Administration**

Azure AD Administration indeholder kontrolelementer om, hvorvidt brugere kan oprette grupper eller tildele ejere i Azure-portaler samt indstillinger for udløb og navngivning af politikker.

Administration indeholder også flere kontrolforanstaltninger for gæsteinvitationer, der går ud over Microsoft 365 Administration, f.eks. muligheden for at begrænse, om ikke-ejere også kan invitere gæster

**SharePoint**

SharePoint oprettes med sikkerhedsgrupperne Ejer, Medlem og Besøgende, og de to første matcher med deres Microsoft 365 gruppes modparter. Mens medlemskab af SharePoint Online-websteder generelt administreres af den tilknyttede Microsoft 365 gruppe, er det ikke en tovejsrelation. Eventuelle ændringer i medlemskabet på Microsoft 365-gruppeniveau afspejles i SharePoint, men hvis medlemskabet ændres i SharePoint-gruppen, afspejles dette ikke i Microsoft 365 gruppe.

### <a name="user-experiences"></a>Brugeroplevelser

Slutbrugere kan oprette grupper fra flere af tjenesterne inden for Microsoft 365, og i andre kan de kun dele med en gruppe.

Følgende tjenester gør det muligt at oprette grupper af slutbrugere:

- Outlook
- Planner
- Project til internettet
- SharePoint
- Stream
- Microsoft Teams
- Yammer

#### <a name="restriction-of-group-creation"></a>Begrænsning af oprettelse af grupper

En fælles tilgang til at kontrollere gruppers massevis er at begrænse, hvilke brugere der kan oprette dem. Dette kan kun gøres ved at begrænse oprettelsen af grupper. Dette påvirker muligheden for at oprette grupper fra andre tjenester, hvor det kan være nødvendigt for slutbrugeren. Microsoft 365 grupper understøtter ikke muligheden for at begrænse oprettelse af grupper fra nogle apps eller tjenester, mens den tillader det fra andre.

Oplevelsen af begrænsning for oprettelse af grupper varierer mellem apps og tjenester:

|App eller tjeneste|Oplevelse|
|---|---|
|Outlook|**Indstillingen Ny** gruppe fjernes fra menuen Ny på siden Personer|
|Planner|**Ny plan** forklarer, at oprettelse af grupper er blevet deaktiveret og tilbyder at føje planen til en eksisterende gruppe|
|Project til internettet og Roadmap|**Menuen Opret gruppe** forklarer, at oprettelse af grupper er begrænset, og foreslår at bruge en eksisterende gruppe.|
|SharePoint|Du kan stadig oprette et teamwebsted, der ikke er knyttet til en gruppe.|
|Stream|**Gruppeindstillingen** vises ikke under **menuen Opret**.|
|Teams|Brugeren kan ikke oprette et team med en ny gruppe, men kan stadig oprette et team, der anvender en eksisterende gruppe.<br><br>**Knappen Opret et team** erstattes af **Opret team fra en gruppe**.|
|Yammer|**Indstillingen Opret en gruppe** fjernes fra hovednavigationen Grupper/Communities.|

## <a name="services-interactions-with-groups"></a>Tjenesters interaktion med grupper

Se plakaten Grupper Microsoft 365 gruppe for at få oplysninger om forskellige typer af grupper, hvordan disse oprettes og administreres, og få nogle anbefalinger om styring.

[![Miniaturebillede til gruppe infografik.](../downloads/msft-m365-groups-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf)

[PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx)

Følgende tabel indeholder en oversigt over Microsoft 365 interaktioner mellem grupper med forskellige tjenester:

|Produkt|Funktioner|Findes tjenesten uden en gruppe?|Kan tjenesten oprette en gruppe?|Slettes gruppen, når du sletter forekomsten?|
|---|---|---|---|---|
|Azure AD|Medlemskab, gruppekontrolelementer, gæster|Ja|Ja|Ja|
|Exchange|Kalender, postkasse|Ja|Ja|Ja|
|Formularer|Formular|Ja|Nej|Nej|
|OneNote|Notesbog|Ja|Nej|Nej|
|Planner|Opgavetavle|Nej|Ja|Ja|
|Power Apps app|App|Ja|Nej|Nej|
|Power Automate|Arbejdsproces|Ja|Nej|Nej|
|Power BI (klassisk)|Workspace|Nej|Ja|Ja|
|Power BI (ny)|Workspace|Ja|Nej|Ja|
|Project til internettet|Project plan|Ja|Ja|Nej|
|Oversigt|Oversigt|Ja|Ja|Nej|
|SharePoint|Websted|Ja|Ja|Ja|
|Stream|Kanal, video|Ja|Ja|Ja|
|Teams|Team|Nej|Ja|Ja|
|Yammer|Gruppe|Ja|Ja|Ja|

Mens tabellen ovenfor giver en detaljeret oversigt over gruppeinteraktion med Microsoft 365 tjenester, er der flere nuancer og intricacies, som du bør forstå. De følgende afsnit giver et mere dybtgående kig på de specifikke arbejdsbelastninger og deres interaktioner med grupper.

## <a name="azure-ad"></a>Azure AD

Azure AD leverer de underliggende identitetsadministrationsfunktioner på tværs Microsoft 365.

**Vigtige funktioner, der leveres til Grupper**

- Gruppemedlemskab
- Navngivningspolitik
- Udløbspolitik
- Gæster
- Begrænsning af oprettelse af grupper

**Kan Azure AD oprette en gruppe?**

Ja, Microsoft 365 grupper kan oprettes fra Azure AD enten via administrationswebportalen, via PowerShell eller Graph API.

**Findes Azure AD uden en gruppe?**

Ja, Azure AD udfører et stort antal tjenester, der ikke har relation til Microsoft 365 Grupper. Hver Microsoft 365 gruppe er repræsenteret som et objekt i Azure AD.

**Kan der være flere forekomster af Azure AD pr. gruppe?**

Nej, der er kun én forekomst af Azure AD.

**Kan Azure AD være knyttet til flere grupper?**

Ja, fordi Azure AD er den underliggende platform, der leverer tjenesten til gruppemedlemskab.

**Kan Azure AD's tilknytning til en gruppe ændres?**

Nej, Azure AD er den underliggende platform, hvor der findes grupper.

**Sletter du forekomsten, når du sletter gruppen?**

Når du sletter gruppen i Azure AD, slettes relevante gruppe tilknyttede tjenester og indhold.

## <a name="teams"></a>Teams

Teams er et chatbaseret arbejdsområde, der er beregnet til at forbedre samarbejdet ved at give en enkelt grænseflade til at interagere med forskellige Microsoft- og tredjepartstjenester.

Når der oprettes et team, er postkassen og kalenderen, der er knyttet til Microsoft 365-gruppen, som standard skjult både i den globale adresseliste i Exchange og i Outlook. Dette kan tilsidesættes manuelt af en administrator, hvis brugeren vil bruge både Outlook og Teams på den samme Microsoft 365 gruppe.

**Vigtige funktioner, der leveres til Grupper**

- Samtaler
- Kanaler & faner
- Møder

**Kan Teams oprette en gruppe?**

Ja, hvis du opretter et nyt team, oprettes der Microsoft 365 gruppe. Det er også muligt at oprette et team for en eksisterende gruppe, der ikke har et i øjeblikket.

**Findes teams uden en gruppe?**

Nej, det er ikke muligt for et team at eksistere uden en gruppe.

**Kan der være flere teams pr. gruppe?**

Nej, relationen mellem et team og en gruppe er 1:1.

**Kan et team være knyttet til flere grupper?**

Nej, selve teamet kan kun knyttes til en enkelt gruppe.

**Kan et teams tilknytning til en gruppeændring?**

Nej, teamet kan kun nogensinde blive knyttet til den gruppe, som det oprindeligt blev knyttet til.

**Sletter du gruppen, når du sletter gruppen?**

Ja, hvis du sletter teamet Microsoft Teams Team, slettes gruppen, de tilknyttede tjenester og indholdet.

## <a name="exchange"></a>Exchange

Exchange Online indeholder meddelelses-, kalender-, kontakt- og tilknyttede funktioner. I forbindelse med en gruppe er der kun knyttet en enkelt ressource – i modsætning til en hel tjenesteforekomst.

**Vigtige funktioner, der leveres til Grupper**

- Postkasse og kalender
- Mulighed for at sende alle gruppemedlemmer via mail
- Storage af Teams kanalsamtaler til eDiscovery-formål, planner kommentarer

**Kan Exchange oprette en gruppe?**

Ja, det er muligt at oprette en gruppe Exchange Online Administration samt fra Outlook. Du kan også konvertere Exchange distributionslister til Microsoft 365 grupper.

**Findes Exchange en gruppe?**

Ja, Exchange Online indeholder adskillige tjenester, herunder delte postkasser og kalendere, uden nogen gruppesammenknytning.

**Kan der være flere forekomster af Exchange postkasser eller kalendere pr. gruppe?**

Nej, der kan kun være et enkelt Exchange Online postkasse og kalender for en gruppe.

**Kan Exchange postkasser og kalendere være knyttet til flere grupper?**

Nej, postkassen og kalenderen har en 1:1-relation til gruppen. Det er muligt at dele postkassen med andre brugere eller grupper, men dette etablerer ikke nogen form for tjenestetilknytning.

**Kan Exchange eller kalenderens tilknytning til en gruppeændring?**

Nej, postkassen og kalenderen kan ikke ændres til en anden gruppe. Indholdet kan dog flyttes fra én postkasse til en anden i Outlook eller ved hjælp af et tredjepartsværktøj.

**Slettes gruppen, når du sletter postkassen?**

Ja, hvis du sletter postkassen i Exchange, slettes gruppen samt de gruppebundne tjenester og indhold.

## <a name="forms"></a>Formularer

Formularer indeholder webbaserede undersøgelser og tests.

**Vigtige funktioner, der leveres til grupper**

- Ejerskab af formularer

**Kan Forms oprette en gruppe?**

Nej, Formularer kan ikke oprette en gruppe.

**Findes formularer uden en gruppe?**

Ja, undersøgelser og tests kan oprettes direkte i en slutbrugers konto.

**Kan der være flere formularer pr. gruppe?**

Ja, der kan være flere formularer knyttet til en gruppe.

**Kan formularer være knyttet til flere grupper?**

Nej, en formular kan kun knyttes til en enkelt gruppe.

**Kan en formulars tilknytning til en gruppe ændres?**

Nej, når en formular er knyttet til en gruppe (enten oprettet direkte i eller ejerskab overført fra en enkeltperson), kan den ikke flyttes til en anden gruppe.

**Slettes gruppen, når du sletter formularen?**

Nej, det er ikke muligt at slette en gruppe fra grænsefladen Formularer, kun enkelte formularer.

## <a name="onenote"></a>OneNote

OneNote er et digitalt notesbogprogram. Den OneNote notesbog, der er oprettet med en gruppe, er en fil på det tilknyttede SharePoint websted i stedet for en gruppeforbundet tjeneste.

**Vigtige funktioner, der leveres til grupper**

- Delt notesbog (gemt i det gruppe-tilknyttede SharePoint bibliotek)

**Kan OneNote oprette en gruppe?**

Nej, OneNote ikke oprette en gruppe.

**Findes OneNote notesbøger uden en gruppe?**

Ja, notesbøger kan oprettes direkte OneDrive eller på andre delte placeringer.

**Kan der være flere OneNote notesbøger pr. gruppe?**

Ja, en notesbog oprettes som standard, og andre kan tilføjes, men eventuelle links til OneNote fra gruppetilknyttede tjenester vil altid gå til standardnotesbogen.

**Kan en OneNote være knyttet til flere grupper?**

Nej, notesbogen er gemt i det gruppebundne webstedsbibliotek SharePoint og sammenkædes fra forskellige grænseflader. Den kan dog deles med andre grupper på samme måde, som den kan deles med enkeltpersoner.

**Kan notesbogens tilknytning til en gruppe ændres?**

Nej, selve notesbogen er knyttet til gruppen og kan åbnes direkte fra andre gruppeforbundne tjenester, men indholdet kan flyttes fra én notesbog til en anden i OneNote program.

**Sletter du gruppen, når du sletter notesbogen?**

Nej, men hvis notesbogen OneNote, kan der være brudte links i nogle af de gruppe tilknyttede tjenester.

## <a name="planner"></a>Planner

Planner er en let gruppeopgaveadministrationstjeneste.

**Vigtige funktioner, der leveres til grupper**

- Tavle til administration af gruppeopgaver

**Kan Planner oprette en gruppe?**

Ja, hvis du opretter en plan, oprettes der en ny gruppe.

**Findes en Planner-tavle uden en gruppe?**

Nej, en plan skal knyttes til en gruppe.

**Kan der være flere planer pr. gruppe?**

Ja, der kan være flere planer pr. gruppe.

**Kan en plan være knyttet til flere grupper?**

Nej, en plan afhænger udelukkende af gruppemedlemskabet for at bestemme adgangen.

**Kan en plans tilknytning til en gruppeændring?**

Nej, men hvis du kopierer en plan, oprettes der en ny gruppe.

> [!NOTE]
> En gruppe, der er oprettet af et andet program, vises ikke automatisk i Planner for en bruger. For at få adgang til tavlen i første omgang skal de åbne den fra en anden gruppebaseret grænseflade, f.eks Outlook.

**Sletter du gruppen, når du sletter planen?**

Ja, hvis du sletter planen, slettes den gruppe og de tilknyttede tjenester og det tilknyttede indhold.

## <a name="power-apps"></a>Power Apps

Power Apps et lærred til appudvikling uden kode.

**Vigtige funktioner, der leveres til Grupper**

- Apps kan deles med en gruppe, der skal køres og ændres

**Kan Power Apps oprette en gruppe?**

Nej, Power Apps ikke oprette en Microsoft 365 gruppe.

**Findes Power Apps en gruppe?**

Ja, apps kan oprettes i Power Apps og findes på kontoen til oprettelse af filer, indtil de er delt eller publiceret.

**Kan der være flere apps pr. gruppe?**

Ja, der kan være flere apps, der deles med en gruppe.

**Kan apps være knyttet til flere grupper?**

Ja, en app kan deles med flere grupper.

**Kan en apps tilknytning til en gruppe ændres?**

Ja, da tilknytningen mellem Power Apps og en Microsoft 365-gruppe kun deler – findes appen stadig hos den, der har oprettet den.

> [!IMPORTANT]
> [Grupper skal være aktiveret til sikkerhed, før apps kan deles med dem](/powerapps/maker/canvas-apps/share-app#share-an-app-with-office-365-groups).

**Sletter du gruppen, når du sletter appen?**

Nej, appsene har ikke andre forbindelse til gruppen end at blive delt med dem.

## <a name="power-automate"></a>Power Automate

Power Automate (tidligere kaldet Microsoft Flow) leverer arbejdsprocesser og automatiseringstjenester.

**Vigtige funktioner, der leveres til grupper**

- Arbejdsprocesser kan deles med en gruppe, der skal køres og ændres.

**Kan Power Automate oprette en gruppe?**

Nej, Power Automate ikke oprette en Microsoft 365 gruppe i forbindelse med at blive knyttet til en.

Det er dog muligt at oprette et flow, der udfører forskellige handlinger, f.eks. oprettelse af en Azure AD-sikkerhedsgruppe eller opdatering af medlemskab af Microsoft 365 gruppe.

**Findes flows uden en gruppe?**

Ja, flows kan oprettes i Power Automate og befinder sig på Creators-kontoen, indtil de er delt eller publiceret.

**Kan der være flere flow pr. gruppe?**

Ja, der kan være flere flows, der deles med en gruppe.

**Kan et flow være knyttet til flere grupper?**

Ja, et flow kan deles med flere grupper.

**Kan et flows tilknytning til en gruppeændring?**

Ja, da tilknytningen mellem Power Automate og en Microsoft 365-gruppe kun deler – findes flowet stadig hos den, der har oprettet det.

**Slettes gruppen, når et flow slettes?**

Nej, ligesom Power Apps, er flowet ikke forbundet med gruppen ud over at blive delt med dem.

## <a name="power-bi-classic"></a>Power BI (klassisk)

Power BI indeholder interaktive datadrevne dashboards og rapporter.

**Vigtige funktioner, der leveres til grupper**

- Datarapportering

**Kan Power BI oprette en gruppe?**

Ja, hvis du opretter et klassisk arbejdsområde, oprettes Microsoft 365 gruppe.

**Findes der Power BI arbejdsområde uden en gruppe?**

Nej, [et klassisk arbejdsområde Power BI skal knyttes til en gruppe](/power-bi/collaborate-share/service-collaborate-power-bi-workspace).

**Kan der være flere Power BI arbejdsområder pr. gruppe?**

Nej, relationen mellem et klassisk arbejdsområde og en gruppe er 1:1.

**Kan et arbejdsområde være knyttet til flere grupper?**

Teknisk set nej, mens det klassiske arbejdsområde oprettes sammen med gruppen, kan indholdet deles uden for gruppen med brugere og sikkerhedsgrupper.

**Kan arbejdsområdets tilknytning til en gruppe ændres?**

Nej, det klassiske arbejdsområde er knyttet til gruppen, men indholdet kan flyttes fra et arbejdsområde til et andet i Power BI-grænsefladen eller ved at eksportere indhold lokalt.

**Sletter du gruppen, når du sletter arbejdsområdet?**

Ja, hvis du sletter arbejdsområdet i Power BI slettes gruppe- og gruppe tilknyttede tjenester og indhold.

## <a name="power-bi-new"></a>Power BI (ny)

Power BI indeholder interaktive datadrevne dashboards og rapporter.

Selvom oprettelse af et nyt arbejdsområde i Power BI ikke opretter en Microsoft 365-gruppe, vil oprettelse af en gruppe på anden måde oprette et nyt (ikke klassisk) arbejdsområde i Power BI.

**Vigtige funktioner, der leveres til grupper**

- Datarapportering

**Kan Power BI oprette en gruppe?**

Nej, det er ikke muligt at oprette en Microsoft 365 gruppe fra den nye Power BI grænseflade.

**Findes det nye Power BI arbejdsområde uden en gruppe?**

Ja, det er muligt at oprette rapporter og arbejdsområder i Power BI, der ikke er knyttet til Microsoft 365 grupper.

**Kan der være flere arbejdsområder pr. gruppe?**

Ja, [flere arbejdsområder, der er Power BI, kan deles med en enkelt gruppe](/power-bi/collaborate-share/service-create-the-new-workspaces#give-access-to-your-workspace).

**Kan et arbejdsområde være knyttet til flere grupper?**

Nej, et arbejdsområde, der er oprettet Power BI, kan kun knyttes til en enkelt gruppe.

**Kan et arbejdsområdes tilknytning til en gruppe ændres?**

Ja og nej. Et arbejdsområde, der er Power BI kan kun knyttes til en enkelt gruppe ad gangen, men kan når som helst ændre tilknytningen. Et arbejdsområde, der Power BI i en gruppe, knyttes permanent til den pågældende gruppe.

**Sletter du gruppen, når du sletter arbejdsområdet?**

Ja, hvis du sletter arbejdsområdet i Power BI, slettes den gruppe og de gruppebundne tjenester og det tilknyttede indhold.

## <a name="project-for-the-web"></a>Project til internettet

Project til internettet giver mulighed for at oprette projektplaner, Gantt-diagrammer og roadmaps.
Vigtige funktioner, der leveres til grupper.

- Project planer

**Kan Project oprette en gruppe til internettet?**

Ja, det er muligt at oprette en ny Microsoft 365 gruppe direkte fra Project til internettet.

**Findes projekter uden en gruppe?**

Ja, projekter kan eksistere uden at være knyttet til Microsoft 365 gruppe, men tildeling af opgaver kræver gruppesammenknytning.

**Kan der være flere projekter pr. gruppe?**

Ja, det er muligt at forbinde flere projekter i en enkelt gruppe.

**Kan projektet være knyttet til flere grupper?**

Nej, et projekt kan kun knyttes til en enkelt gruppe.

**Kan et projekts tilknytning til en gruppeændring?**

Nej, når tilknytningen til en gruppe er oprettet, kan den ikke ændres.

**Sletter du gruppen, når du sletter projektet?**

Nej, hvis du sletter projektet Project til internettet, slettes gruppen ikke.

## <a name="roadmap"></a>Oversigt

Roadmap gør det muligt at oprette projektoversigter med Project til internettet og Project Online.

**Vigtige funktioner, der leveres til Grupper**

- Project oversigter

**Kan Roadmap oprette en gruppe?**

Ja, det er muligt at oprette en ny gruppe Microsoft 365 direkte fra oversigten.

**Findes Roadmap uden en gruppe?**

Ja, der kan oprettes roadmaps uden at blive knyttet til Microsoft 365 gruppe, men deling af oversigten kræver gruppesammenknytning.

**Kan der være flere oversigter pr. gruppe?**

Ja, det er muligt at forbinde flere roadmaps til en enkelt gruppe.

**Kan en oversigt knyttes til flere grupper?**

Nej, en oversigt kan kun knyttes til en enkelt gruppe.

**Kan en oversigts tilknytning til en gruppeændring?**

Nej, når tilknytningen til en gruppe er oprettet, kan den ikke ændres.

**Sletter du gruppen, når du sletter oversigten?**

Nej, hvis du sletter oversigten, slettes gruppen ikke.

## <a name="sharepoint"></a>SharePoint

SharePoint er en webbaseret platform til indholdsstyring, der blandt andet leverer lagertjenester til flere Microsoft 365 tjenester.

**Vigtige funktioner, der leveres til Grupper**

- Dokumentbibliotek
- Bibliotek til lagring af OneNote notesbog
- Storage af Teams wiki-filer

**Kan SharePoint oprette en gruppe?**

Ja, hvis du opretter et teamwebsted SharePoint teamwebsted, oprettes der Microsoft 365 gruppe som standard. Det er også muligt at oprette en gruppe og eventuelt et team til et eksisterende websted.

**Findes SharePoint websteder uden en gruppe?**

Ja, SharePoint tilbyder flere ikke-gruppe-tilknyttede tjenester og websteder som f.eks. kommunikations- og hubwebsteder. 

**Kan der være flere websteder pr. gruppe?**

Nej, der kan kun være et enkelt websted pr. gruppe. Private kanaler i Teams andre websteder, der ikke har forbindelse til gruppen.

**Kan websteder være knyttet til flere grupper?**

Teknisk set nej, men mens der oprettes et websted med en gruppe, kan indholdet deles med andre grupper.

**Kan et websteds tilknytning til en gruppe ændres?**

Nej, selve webstedet er knyttet til gruppen, men indholdet kan flyttes fra ét websted til et andet inden for SharePoint-grænsefladen, ved at eksportere indhold lokalt eller ved hjælp af et tredjepartsværktøj.

**Sletter du gruppen, når du sletter webstedet?**

Ja, hvis du sletter webstedet i SharePoint, slettes gruppe- og gruppe tilknyttede tjenester og indhold.

## <a name="stream"></a>Stream

Microsoft Stream er en videohosting- og delingsplatform.

**Vigtige funktioner, der leveres til Grupper**

- Videolagerplads
- Teams mødeoptagelse
- Videokanaler

**Kan Stream oprette en gruppe?**

Ja, det er muligt at oprette en ny Microsoft 365 gruppe direkte fra Stream.

**Findes Stream uden en gruppe?**

Ja, videokanaler og videoer kan findes i Stream uden at være knyttet til en gruppe.

**Kan der være flere videoer og kanaler pr. gruppe?**

Ja, der kan være flere videoer og kanaler i hver gruppe.

**Kan en video eller kanal være knyttet til flere grupper?**

Ja, mens en video eller kanal oprettes sammen med en gruppe, kan den deles med andre grupper.

**Kan dens tilknytning til en gruppeændring?**

Ja og nej. Videoer i Stream ejes af den oprindelige uploader eller mødeoptager og kan derfor knyttes til enhver gruppe, men videokanaler kan kun knyttes til den gruppe, de oprindeligt blev oprettet i.

**Slettes gruppen, når du sletter videoer eller kanaler?**

Nej, hvis du sletter videoer eller kanaler, slettes gruppen ikke. Men hvis du sletter selve gruppen i Stream, slettes de gruppe tilknyttede tjenester og indhold med undtagelse af de faktiske videoer.

## <a name="yammer"></a>Yammer

Yammer er en social platform for virksomheder, der er udviklet til at fremme community'ets engagement i og mellem organisationer.

Når du opretter et community (tidligere kaldet "gruppe") i Yammer oprettes en postkasse, men dette bruges ikke i øjeblikket.

En Microsoft 365 gruppe, der er knyttet Yammer, kan ikke bruges sammen med et team Microsoft Teams.

**Vigtige funktioner, der leveres til Grupper**

- Samtaleområde

**Kan Yammer oprette en Microsoft 365 gruppe?**

Ja, hvis du opretter en ny gruppe i Yammer, oprettes en ny Microsoft 365-gruppe, hvis platforme er forbundet, og brugeren har mulighed for at oprette en gruppe.

En Yammer gruppe med tilknyttet Microsoft 365 gruppe kan ikke oprettes i andre grænseflader eller tjenester end Yammer sig selv.

**Findes en Yammer gruppe uden en Microsoft 365 gruppe?**

Ja, det er muligt at oprette Yammer gruppe uden en Microsoft 365 gruppe.

Hvis Yammer-platformen ikke er knyttet til Microsoft 365-grupper, eller hvis brugerne ikke har mulighed for at oprette en Microsoft 365-gruppe, oprettes Yammer-grupper uden en Microsoft 365 gruppesammenknytning.

**Kan der være flere Yammer grupper pr. Microsoft 365 gruppe?**

Nej, relationen mellem en Yammer og en Microsoft 365 gruppe er 1:1.

**Kan en Yammer gruppe være knyttet til flere Microsoft 365 grupper?**

Nej, den Yammer gruppe kan kun knyttes til en enkelt Microsoft 365 gruppe. Det er muligt at dele indlæg med eller flytte til andre Yammer grupper.

**Kan en Yammer gruppes tilknytning til en Microsoft 365 gruppe ændres?**

Nej, Yammer-gruppen kan kun nogensinde blive knyttet til den Microsoft 365, som den oprindeligt blev knyttet til.

**Sletter et Yammer gruppen Microsoft 365 gruppen?**

Ja, hvis du sletter gruppen i en Yammer Microsoft-gruppe og tilknyttede tjenester og indhold for grupper.

## <a name="related-topics"></a>Relaterede emner

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md)
