---
title: Grupperer tjenesteinteraktioner
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
description: Grupperer tjenesteinteraktioner
ms.openlocfilehash: 64de83690edb96e3bf7a889309c262a92f8e8193
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286335"
---
# <a name="groups-services-interactions"></a>Grupperer tjenesteinteraktioner

Microsoft 365-grupper giver en fælles struktur til flere tjenester og arbejdsbelastninger på den Microsoft 365 platform, så slutbrugerne får en forbundet oplevelse. I sin kerne findes der en Microsoft 365 gruppe, der kan levere:

- En måde at administrere medlemskabet på (Azure AD)
- Et sted til beskeder og samtaler (Exchange postkasse, Microsoft Teams, Yammer)
- Et sted, hvor filer skal gemmes (SharePoint)
- En kalender til planlægning (Exchange)
- En notesbog til hentning af noter (OneNote)

Ved oprettelsen af en gruppe klargøres flere andre ressourcer også, men de er først synlige, første gang de åbnes fra tjenesten:

- En bestyrelse til administration af gruppeopgaver (Planner)
- Et arbejdsområde til rapportering (Power BI)
- Et område til delte videoer (Microsoft Stream)
- Et område til delte formularer (formularer)

På tværs af Microsoft 365 kan andre tjenester interagere med Microsoft 365 grupper for at levere yderligere funktionalitet og funktioner til gruppemedlemmer.
Eksempler på dette omfatter:

- Power Apps til apps
- Power Automate til arbejdsprocesser
- Project på internettet og oversigt over vandfaldsbaseret projektstyring
- Teams til kanalbaserede samtaler
- Yammer for interessefællesskaber

## <a name="user-interactions-with-groups"></a>Brugerinteraktioner med grupper

Microsoft 365-grupper kan oprettes og administreres fra forskellige grænseflader, både af administratorer og slutbrugere. 

### <a name="administrative-experiences"></a>Administrative oplevelser

Administratorer kan oprette og administrere Microsoft 365 grupper fra flere af administrationscentrene for arbejdsbelastning, kommandolinjegrænseflader, der understøtter scripting, samt brugerdefinerede apps, der interagerer med API'en til Graph. Den eneste undtagelse til dette er Yammer grupper – som skal oprettes fra den Yammer webgrænseflade.

**Relaterede indstillinger**

På tværs af de forskellige administrative grænseflader, der kan administrere gruppeindstillinger, findes der flere overlap, som du skal være opmærksom på.

**Microsoft 365 Administration**

I Microsoft 365 Administration er gæsteadgang til Grupper aktiveret som standard, og det samme gør muligheden for at give ejere mulighed for at tilføje gæster. Der er ikke flere tilgængelige kontrolelementer på organisationsniveau for grupper fra dette administrationscenter.

**Azure AD Administration**

Azure AD Administration tilbyder kontrolelementer omkring, om brugerne kan oprette grupper eller tildele ejere på Azure-portaler samt politikindstillinger for udløb og navngivning.

Administration indeholder også flere kontrolforanstaltninger for gæsteinvitationer, der går ud over Microsoft 365 Administration, f.eks. muligheden for at begrænse, om ikke-ejere også kan invitere gæster

**SharePoint**

SharePoint websteder oprettes med sikkerhedsgrupperne Ejer, Medlem og Besøgende, hvor de første to stemmer overens med deres Microsoft 365 gruppekollegaer. Selvom medlemskab af SharePoint Online-websteder generelt administreres af den tilknyttede Microsoft 365 gruppe, er det ikke en tovejsrelation. Eventuelle ændringer af medlemskabet på Microsoft 365 gruppeniveau afspejles i SharePoint, men hvis medlemskabet ændres i den SharePoint gruppe, afspejles dette ikke i den Microsoft 365 gruppe.

### <a name="user-experiences"></a>Brugeroplevelser

Slutbrugere kan oprette grupper ud fra flere af tjenesterne i Microsoft 365, og i andre kan de kun dele med en gruppe.

Følgende tjenester tillader, at slutbrugere kan oprette grupper:

- Outlook
- Planner
- Project til internettet
- SharePoint
- Stream
- Microsoft Teams
- Yammer

#### <a name="restriction-of-group-creation"></a>Begrænsning af oprettelse af gruppe

En almindelig metode til at styre udbredelse af teams er at begrænse, hvilke brugere der kan oprette dem. Dette kan kun gøres ved at begrænse oprettelsen af grupper. Dette påvirker muligheden for at oprette grupper fra andre tjenester, hvor det kan være nødvendigt for slutbrugeren. Microsoft 365-grupper understøtter ikke muligheden for at begrænse oprettelsen af grupper fra nogle apps eller tjenester, samtidig med at du tillader det fra andre.

Oplevelsen af begrænsning af gruppeoprettelse varierer mellem apps og tjenester:

|App eller tjeneste|Erfaring|
|---|---|
|Outlook|**Indstillingen Ny gruppe** fjernes fra menuen Ny på siden Personer|
|Planner|**Ny plan** forklarer, at gruppeoprettelse er slået fra, og tilbyder at føje planen til en eksisterende gruppe|
|Project til internettet og roadmap|**Menuen Opret gruppe** forklarer, at gruppeoprettelsen er begrænset, og foreslår, at der bruges en eksisterende gruppe.|
|SharePoint|Det er stadig muligt at oprette et teamwebsted, der ikke har forbindelse til en gruppe.|
|Stream|**Gruppeindstillingen** vises ikke i **menuen Opret**.|
|Teams|Brugeren kan ikke oprette et team med en ny gruppe, men kan stadig oprette et team, der anvender en eksisterende gruppe.<br><br>**Knappen Opret et team** erstattes med **Opret team fra en gruppe**.|
|Yammer|**Indstillingen Opret en gruppe** fjernes fra hovednavigationen Grupper/Communities.|

## <a name="services-interactions-with-groups"></a>Tjenesteinteraktioner med grupper

Se plakaten Grupper i Microsoft 365 for at få oplysninger om forskellige typer grupper, hvordan disse oprettes og administreres, og nogle få anbefalinger til styring.

[![Miniaturebillede for gruppers infografik.](../downloads/msft-m365-groups-architecture-thumb.png)](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.pdf)

[PDF](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.pdf) \| [Visio](https://download.microsoft.com/download/6/3/0/6309218f-a169-4f2d-af4c-2fe49e30ba17/msft-m365-groups.vsdx)

Følgende tabel indeholder en oversigt over Microsoft 365-grupper interaktioner med forskellige tjenester:

|Produkt|Funktioner|Findes tjenesten uden en gruppe?|Kan tjenesten oprette en gruppe?|Sletter du forekomsten, sletter gruppen?|
|---|---|---|---|---|
|Azure AD|Medlemskab, gruppekontrolelementer, gæster|Ja|Ja|Ja|
|Exchange|Kalender, postkasse|Ja|Ja|Ja|
|Former|Form|Ja|Nej|Nej|
|OneNote|Notebook|Ja|Nej|Nej|
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

Mens ovenstående tabel indeholder en overordnet oversigt over gruppeinteraktioner med Microsoft 365 tjenester, er der flere nuancer og komplicerede ting, som du skal forstå. I de følgende afsnit ser vi nærmere på de specifikke arbejdsbelastninger og deres interaktioner med grupper.

## <a name="azure-ad"></a>Azure AD

Azure AD leverer de underliggende funktioner til administration af identiteter på tværs af Microsoft 365.

**Nøglefunktioner, der leveres til grupper**

- Gruppemedlemskab
- Navngivningspolitik
- Udløbspolitik
- Gæsterne
- Begrænsning af oprettelse af gruppe

**Kan Azure AD oprette en gruppe?**

Ja, Microsoft 365-grupper kan oprettes fra Azure AD enten via administrationswebportalen, via PowerShell eller Graph API.

**Findes Azure AD uden en gruppe?**

Ja, Azure AD udfører en lang række tjenester, der ikke har nogen relation til Microsoft 365-grupper. Hver Microsoft 365 gruppe repræsenteres som et objekt i Azure AD.

**Kan der være flere forekomster af Azure AD pr. gruppe?**

Nej, der er kun én forekomst af Azure AD.

**Kan Azure AD knyttes til flere grupper?**

Ja, fordi Azure AD er den underliggende platform, der leverer tjenesten til gruppemedlemskab.

**Kan Azure AD tilknytning til en gruppeændring?**

Nej, Azure AD er den underliggende platform, hvor grupper findes.

**Sletter du forekomsten, sletter gruppen?**

Hvis du sletter gruppen i Azure AD slettes relevante grupperelaterede tjenester og indhold.

## <a name="teams"></a>Teams

Teams er et chatbaseret arbejdsområde, der har til formål at forbedre samarbejdet ved at levere en enkelt grænseflade, der kan interagere med forskellige Microsoft- og tredjepartstjenester.

Når der oprettes et team, skjules den postkasse og kalender, der er knyttet til gruppen Microsoft 365, som standard fra både den globale adresseliste i Exchange og Outlook. Dette kan tilsidesættes manuelt af en administrator, hvis brugeren vil bruge både Outlook og Teams på den samme Microsoft 365 gruppe.

**Nøglefunktioner, der leveres til grupper**

- Samtaler
- Kanaler & faner
- Møder

**Kan Teams oprette en gruppe?**

Ja, hvis du opretter et nyt team, oprettes der en ny Microsoft 365 gruppe. Det er også muligt at oprette et team for en eksisterende gruppe, der ikke har en i øjeblikket.

**Findes teams uden en gruppe?**

Nej, det er ikke muligt for et team at eksistere uden en gruppe.

**Kan der være flere teams pr. gruppe?**

Nej, relationen mellem et team og en gruppe er 1:1.

**Kan et team knyttes til flere grupper?**

Nej, selve teamet kan kun knyttes til en enkelt gruppe.

**Kan et teams tilknytning til en gruppe ændres?**

Nej, teamet kan altid kun knyttes til den gruppe, som det oprindeligt var tilknyttet.

**Sletter du gruppen?**

Ja, hvis du sletter teamet i Microsoft Teams, slettes gruppen, de gruppetilhørende tjenester og indholdet.

## <a name="exchange"></a>Exchange

Exchange Online leverer meddelelses-, kalender-, kontakt- og tilknyttet funktionalitet. I forbindelse med en gruppe er der kun knyttet en enkelt ressource – i modsætning til en hel tjenesteforekomst.

**Nøglefunktioner, der leveres til grupper**

- Postkasse og kalender
- Mulighed for at sende mail til alle gruppemedlemmer
- Storage af Teams kanalsamtaler til eDiscovery-formål, planner-kommentarer

**Kan Exchange oprette en gruppe?**

Ja, det er muligt at oprette en gruppe fra Exchange Online Administration samt fra Outlook. Du kan også konvertere Exchange distributionslister til Microsoft 365 grupper.

**Findes Exchange uden en gruppe?**

Ja, Exchange Online leverer flere tjenester, herunder delte postkasser og kalendere, uden nogen gruppetilknytning.

**Kan der være flere forekomster af Exchange postkasser eller kalendere pr. gruppe?**

Nej, der kan kun være en enkelt Exchange Online postkasse og kalender for en gruppe.

**Kan Exchange postkasser og kalendere knyttes til flere grupper?**

Nej, postkassen og kalenderen har en 1:1-relation til gruppen. Det er muligt at dele postkassen med andre brugere eller grupper, men det etablerer ingen form for tjenestetilknytning.

**Kan Exchange postkassen eller kalenderens tilknytning til en gruppe ændres?**

Nej, postkassen og kalenderen kan ikke ændres til en anden gruppe. Indholdet kan dog flyttes fra én postkasse til en anden i Outlook eller ved hjælp af et tredjepartsværktøj.

**Sletter du postkassen?**

Ja, hvis du sletter postkassen i Exchange, slettes gruppen samt gruppetilhørende tjenester og indhold.

## <a name="forms"></a>Former

Formularer indeholder webbaserede undersøgelser og quizzer.

**Nøglefunktioner, der leveres til grupper**

- Ejerskab af formularer

**Kan formularer oprette en gruppe?**

Nej, formularer kan ikke oprette en gruppe.

**Findes formularer uden en gruppe?**

Ja, undersøgelser og quizzer kan oprettes direkte på en slutbrugers konto.

**Kan der være flere formularer pr. gruppe?**

Ja, der kan være knyttet flere formularer til en gruppe.

**Kan formularer knyttes til flere grupper?**

Nej, en formular kan kun knyttes til en enkelt gruppe.

**Kan en formulars tilknytning til en gruppe ændres?**

Nej, når en formular er knyttet til en gruppe (enten oprettet direkte i eller ejerskab overført fra en person), kan den ikke flyttes til en anden gruppe.

**Sletter du formularen, sletter du gruppen?**

Nej, det er ikke muligt at slette en gruppe fra grænsefladen Formularer, kun individuelle formularer.

## <a name="onenote"></a>OneNote

OneNote er et program til digital notesbog. Den OneNote notesbog, der er oprettet med en gruppe, er en fil på det tilknyttede SharePoint websted i stedet for en gruppeforbundet tjeneste.

**Nøglefunktioner, der leveres til grupper**

- Delt notesbog (gemt i det gruppetilhørende SharePoint bibliotek)

**Kan OneNote oprette en gruppe?**

Nej, det OneNote program kan ikke oprette en gruppe.

**Findes OneNote notesbøger uden en gruppe?**

Ja, notesbøger kan oprettes direkte i OneDrive eller på andre delte placeringer.

**Kan der være flere OneNote notesbøger pr. gruppe?**

Ja, en notesbog oprettes som standard, og andre kan tilføjes, men ethvert link til OneNote fra gruppetilhørende tjenester vil altid gå til standardnotesbogen.

**Kan en OneNote notesbog knyttes til flere grupper?**

Nej, notesbogen gemmes i det gruppetilhørende SharePoint webstedsbibliotek og sammenkædes fra forskellige grænseflader. Den kan dog deles med andre grupper på samme måde, som den kan deles med enkeltpersoner.

**Kan notesbogens tilknytning til en gruppe ændres?**

Nej, selve notesbogen er knyttet til gruppen og kan tilgås direkte fra andre gruppetilsluttede tjenester, men indholdet kan flyttes fra én notesbog til en anden i OneNote program.

**Sletter du notesbogen, og slettes gruppen?**

Nej, men hvis den OneNote notesbog slettes, kan der være brudte links i nogle af de gruppetilhørende tjenester.

## <a name="planner"></a>Planner

Planner er en tjeneste til administration af gruppeopgave.

**Nøglefunktioner, der leveres til grupper**

- Bestyrelse til administration af gruppeopgaver

**Kan Planner oprette en gruppe?**

Ja, oprettelsen af en plan opretter en ny gruppe.

**Findes der et planner-board uden en gruppe?**

Nej, en plan skal være knyttet til en gruppe.

**Kan der være flere planer pr. gruppe?**

Ja, der kan være flere planer pr. gruppe.

**Kan en plan knyttes til flere grupper?**

Nej, en plan er udelukkende afhængig af gruppemedlemskabet for at bestemme adgangen.

**Kan en plans tilknytning til en gruppe ændres?**

Nej, men hvis du kopierer en plan, oprettes der en ny gruppe.

> [!NOTE]
> En gruppe, der er oprettet af et andet program, vises ikke automatisk i Planner for en bruger. For at få adgang til bestyrelsen i første omgang skal de åbne den fra en anden gruppebaseret grænseflade, f.eks. Outlook.

**Sletter du planen for at slette gruppen?**

Ja, hvis du sletter planen, slettes gruppen og de gruppetilhørende tjenester og indholdet.

## <a name="power-apps"></a>Power Apps

Power Apps indeholder et lærred til appudvikling uden kode.

**Nøglefunktioner, der leveres til grupper**

- Apps kan deles med en gruppe, der skal køres og ændres

**Kan Power Apps oprette en gruppe?**

Nej, Power Apps kan ikke oprette en Microsoft 365 gruppe.

**Findes Power Apps uden en gruppe?**

Ja, apps kan oprettes i Power Apps og være placeret i opretterkontoen, indtil de deles eller publiceres.

**Kan der være flere apps pr. gruppe?**

Ja, der kan være flere apps, der deles med en gruppe.

**Kan apps knyttes til flere grupper?**

Ja, en app kan deles med flere grupper.

**Kan en apps tilknytning til en gruppe ændres?**

Ja, da tilknytningen mellem Power Apps og en Microsoft 365 gruppe kun deles – appen er stadig placeret hos forfatteren.

> [!IMPORTANT]
> [Grupper skal være sikkerhedsaktiveret, før apps kan deles med dem](/powerapps/maker/canvas-apps/share-app#share-an-app-with-office-365-groups).

**Sletter du appen, og sletter den gruppen?**

Nej, appsene har ikke forbindelse til gruppen ud over at blive delt med dem.

## <a name="power-automate"></a>Power Automate

Power Automate (tidligere kaldet Microsoft Flow) leverer arbejdsprocesser og automatiseringstjenester.

**Nøglefunktioner, der leveres til grupper**

- Arbejdsprocesser kan deles med en gruppe, der skal køres og ændres.

**Kan Power Automate oprette en gruppe?**

Nej, Power Automate kan ikke oprette en Microsoft 365 gruppe i konteksten af at være knyttet til en.

Det er dog muligt at oprette et flow, der udfører forskellige handlinger, f.eks. oprettelse af en Azure AD sikkerhedsgruppe eller opdatering af medlemskab af en Microsoft 365 gruppe.

**Findes flow uden en gruppe?**

Ja, flow kan oprettes i Power Automate og være placeret på opretterkontoen, indtil de deles eller publiceres.

**Kan der være flere flow pr. gruppe?**

Ja, der kan være flere flow, der deles med en gruppe.

**Kan et flow knyttes til flere grupper?**

Ja, et flow kan deles med flere grupper.

**Kan tilknytningen til en gruppe ændres for et flow?**

Ja, da tilknytningen mellem Power Automate og en Microsoft 365 gruppe kun deles – flowet er stadig placeret hos forfatteren.

**Sletter du gruppen, når du sletter et flow?**

Nej, som Power Apps er flowene ikke forbundet til gruppen ud over at blive delt med dem.

## <a name="power-bi-classic"></a>Power BI (klassisk)

Power BI indeholder interaktive datadrevne dashboards og rapporter.

**Nøglefunktioner, der leveres til grupper**

- Datarapportering

**Kan Power BI oprette en gruppe?**

Ja, hvis du opretter et klassisk arbejdsområde, oprettes der en Microsoft 365 gruppe.

**Findes der et Power BI klassisk arbejdsområde uden en gruppe?**

Nej, [et klassisk arbejdsområde i Power BI skal være knyttet til en gruppe](/power-bi/collaborate-share/service-collaborate-power-bi-workspace).

**Kan der være flere Power BI arbejdsområder pr. gruppe?**

Nej, relationen mellem et klassisk arbejdsområde og en gruppe er 1:1.

**Kan et arbejdsområde knyttes til flere grupper?**

Teknisk set nej, mens det klassiske arbejdsområde oprettes med gruppen, kan indholdet deles uden for gruppen med brugere og sikkerhedsgrupper.

**Kan arbejdsområdets tilknytning til en gruppe ændres?**

Nej, selve det klassiske arbejdsområde er knyttet til gruppen, men indholdet kan flyttes fra ét arbejdsområde til et andet i den Power BI grænseflade eller ved at eksportere indhold lokalt.

**Sletter du arbejdsområdet?**

Ja, hvis du sletter arbejdsområdet i Power BI, slettes gruppe- og gruppetilhørende tjenester og indhold.

## <a name="power-bi-new"></a>Power BI (ny)

Power BI indeholder interaktive datadrevne dashboards og rapporter.

Når du opretter et nyt arbejdsområde i Power BI oprettes der ikke en Microsoft 365 gruppe, men hvis du opretter en gruppe på anden måde, oprettes der et nyt (ikke klassisk) arbejdsområde i Power BI.

**Nøglefunktioner, der leveres til grupper**

- Datarapportering

**Kan Power BI oprette en gruppe?**

Nej, det er ikke muligt at oprette en Microsoft 365 gruppe ud fra den nye Power BI grænseflade.

**Findes det nye Power BI arbejdsområde uden en gruppe?**

Ja, det er muligt at få oprettet rapporter og arbejdsområder i Power BI, der ikke er knyttet til Microsoft 365 grupper.

**Kan der være flere arbejdsområder pr. gruppe?**

Ja, [flere arbejdsområder, der er oprettet af Power BI, kan deles med en enkelt gruppe](/power-bi/collaborate-share/service-create-the-new-workspaces#give-access-to-your-workspace).

**Kan et arbejdsområde knyttes til flere grupper?**

Nej, et arbejdsområde, der er oprettet af Power BI, kan kun knyttes til en enkelt gruppe.

**Kan tilknytningen til en gruppe ændres for et arbejdsområde?**

Ja og nej. Et arbejdsområde, der er oprettet af Power BI, kan kun knyttes til en enkelt gruppe ad gangen, men kan når som helst ændre tilknytningen. Et arbejdsområde, der er oprettet i Power BI af en gruppe, er permanent knyttet til den pågældende gruppe.

**Sletter du arbejdsområdet?**

Ja, hvis du sletter arbejdsområdet i Power BI, slettes gruppen og de gruppetilhørende tjenester og indhold.

## <a name="project-for-the-web"></a>Project til internettet

Project til internettet giver mulighed for at oprette projektplaner, Gantt-diagrammer og køreplaner.
Vigtige funktioner, der leveres til grupper.

- Project planer

**Kan Project til internettet oprette en gruppe?**

Ja, det er muligt at oprette en ny Microsoft 365 gruppe direkte fra Project til internettet.

**Findes projekter uden en gruppe?**

Ja, projekter kan eksistere uden at være knyttet til en Microsoft 365 gruppe, men tildeling af opgaver kræver gruppetilknytning.

**Kan der være flere projekter pr. gruppe?**

Ja, det er muligt at forbinde flere projekter i en enkelt gruppe.

**Kan projektet knyttes til flere grupper?**

Nej, et projekt kan kun knyttes til en enkelt gruppe.

**Kan et projekts tilknytning til en gruppe ændres?**

Nej, når tilknytningen til en gruppe er oprettet, kan den ikke ændres.

**Sletter du projektet, slettes gruppen?**

Nej, hvis du sletter projektet i Project til internettet, slettes gruppen ikke.

## <a name="roadmap"></a>Oversigt

Roadmap giver mulighed for at oprette projektoversigter med Project til internettet og Project Online.

**Nøglefunktioner, der leveres til grupper**

- køreplaner for Project

**Kan Roadmap oprette en gruppe?**

Ja, det er muligt at oprette en ny Microsoft 365 gruppe direkte fra roadmapet.

**Findes Roadmap uden en gruppe?**

Ja, køreplaner kan eksistere uden at være knyttet til en Microsoft 365 gruppe, men deling af køreplanen kræver gruppetilknytning.

**Kan der være flere køreplaner pr. gruppe?**

Ja, det er muligt at forbinde flere køreplaner med en enkelt gruppe.

**Kan en oversigt knyttes til flere grupper?**

Nej, en oversigt kan kun knyttes til en enkelt gruppe.

**Kan en oversigts tilknytning til en gruppe ændres?**

Nej, når tilknytningen til en gruppe er oprettet, kan den ikke ændres.

**Sletter du gruppen, når køreplanen slettes?**

Nej, hvis du sletter oversigtsoversigten, slettes gruppen ikke.

## <a name="sharepoint"></a>SharePoint

SharePoint er en webbaseret platform til administration af indhold, der bl.a. leverer lagertjenester til flere Microsoft 365 tjenester.

**Nøglefunktioner, der leveres til grupper**

- Dokumentbibliotek
- Bibliotek til lagring af OneNote notesbog
- Storage af Teams wikifiler

**Kan SharePoint oprette en gruppe?**

Ja, hvis du opretter et teamwebsted i SharePoint, oprettes der som standard en Microsoft 365 gruppe. Det er også muligt at oprette en gruppe og eventuelt et team for et eksisterende websted.

**Findes SharePoint websteder uden en gruppe?**

Ja, SharePoint tilbyder flere tjenester og websteder, der ikke er tilknyttet grupper, f.eks. kommunikations- og hubwebsteder. 

**Kan der være flere websteder pr. gruppe?**

Nej, der kan kun være et enkelt websted pr. gruppe. Private og delte kanaler i Teams bruge flere websteder, der ikke har forbindelse til gruppen.

**Kan websteder knyttes til flere grupper?**

Teknisk set nej, men mens et websted oprettes med en gruppe, kan indholdet deles med andre grupper.

**Kan tilknytningen til en gruppe ændres for et websted?**

Nej, selve webstedet er knyttet til gruppen, men indholdet kan flyttes fra ét websted til et andet i den SharePoint grænseflade ved at eksportere indhold lokalt eller ved hjælp af et tredjepartsværktøj.

**Sletter du webstedet for at slette gruppen?**

Ja, hvis du sletter webstedet i SharePoint, slettes gruppe- og gruppetilhørende tjenester og indhold.

## <a name="stream"></a>Stream

Microsoft Stream er en platform til videohosting og -deling.

**Nøglefunktioner, der leveres til grupper**

- Videolager
- Teams mødeoptagelse
- Videokanaler

**Kan Stream oprette en gruppe?**

Ja, det er muligt at oprette en ny Microsoft 365 gruppe direkte fra Stream.

**Findes Stream uden en gruppe?**

Ja, videokanaler og videoer kan findes i Stream uden at være knyttet til en gruppe.

**Kan der være flere videoer og kanaler pr. gruppe?**

Ja, der kan være flere videoer og kanaler i hver gruppe.

**Kan en video eller kanal knyttes til flere grupper?**

Ja, mens en video eller kanal oprettes med en gruppe, kan den deles med andre grupper.

**Kan tilknytningen til en gruppe ændres?**

Ja og nej. videoer i Stream ejes af den oprindelige uploader eller mødeoptager og kan derfor knyttes til en hvilken som helst gruppe, men videokanaler kan kun knyttes til den gruppe, de oprindeligt blev oprettet i.

**Sletter du gruppen, når du sletter videoer eller kanaler?**

Nej, sletning af videoer eller kanaler sletter ikke gruppen. Hvis du sletter selve gruppen i Stream, slettes gruppetilhørende tjenester og indhold, bortset fra de faktiske videoer.

## <a name="yammer"></a>Yammer

Yammer er en social platform til virksomheder, der er designet til at fremme engagement i lokalsamfundet i og mellem organisationer.

Oprettelse af et community (tidligere kaldet "gruppe") i Yammer opretter en postkasse, men bruges ikke i øjeblikket.

En Microsoft 365 gruppe, der er knyttet til Yammer, kan ikke bruges sammen med et team i Microsoft Teams.

**Nøglefunktioner, der leveres til grupper**

- Samtaleområde

**Kan Yammer oprette en Microsoft 365 gruppe?**

Ja, hvis du opretter en ny gruppe i Yammer oprettes der en ny Microsoft 365 gruppe, hvis platformene er forbundet, og brugeren har mulighed for at oprette en gruppe.

En Yammer gruppe med tilknyttet Microsoft 365 gruppe kan ikke oprettes i andre grænseflader eller tjenester end Yammer sig selv.

**Findes der en Yammer gruppe uden en Microsoft 365 gruppe?**

Ja, det er muligt at oprette en Yammer gruppe uden en Microsoft 365 gruppe.

Hvis den Yammer platform ikke har forbindelse til Microsoft 365 grupper, eller hvis brugerne ikke har mulighed for at oprette en Microsoft 365 gruppe, oprettes der Yammer grupper uden en Microsoft 365 gruppetilknytning.

**Kan der være flere Yammer grupper pr. Microsoft 365 gruppe?**

Nej, relationen mellem en Yammer gruppe og en Microsoft 365 gruppe er 1:1.

**Kan en Yammer gruppe knyttes til flere Microsoft 365 grupper?**

Nej, den Yammer gruppe kan kun knyttes til en enkelt Microsoft 365 gruppe. Det er muligt at dele opslag med eller flytte dem til andre Yammer grupper.

**Kan en Yammer gruppes tilknytning til en Microsoft 365 gruppe ændres?**

Nej, den Yammer gruppe kan altid kun knyttes til den Microsoft 365 gruppe, som den oprindeligt var tilknyttet.

**Sletter du den Microsoft 365 gruppe, hvis du sletter den Yammer gruppe?**

Ja, hvis du sletter gruppen i Yammer, slettes relaterede Microsoft-grupper og gruppetilhørende tjenester og indhold.

## <a name="related-topics"></a>Relaterede emner

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md)
