---
title: Slutdato for livscyklusindstillinger for grupper, teams og Yammer
ms.reviewer: mmclean
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
description: Indstillinger for ophør af livscyklus for grupper, teams og Yammer.
ms.openlocfilehash: f7774498047f74c27b21e45ed86b284a42325bb0
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64973921"
---
# <a name="end-of-lifecycle-options-for-groups-teams-and-yammer"></a>Slutdato for livscyklusindstillinger for grupper, teams og Yammer

Microsoft 365-grupper og Microsoft Teams arbejde med flere forbundne tjenester. Når en gruppe eller et team slettes, slettes de fleste af oplysningerne i de forbundne tjenester også. I denne artikel beskrives mulighederne for at bevare oplysninger ved at flytte dem ud af gruppen eller teamet, før de slettes.

En almindelig praksis for grupper eller teams, der ikke længere er påkrævet, er at flytte filerne ud af teamet og arkivere dem på en anden placering, f.eks. et SharePoint dokumentbibliotek. Denne praksis er baseret på en ældre arbejdsstil, hvor oplysninger gemmes i filer og mapper, og kommunikation udføres via mail.

I følgende tabel beskrives de tjenester, der er knyttet til grupper og teams, og de vigtigste typer indhold, der findes i hver af dem:

|Tjeneste|Indholdstyper|
|:------|:---------------|
|Teams|Kanalsamtaler, filer i kanaler|
|Former|Undersøgelsesstruktur og resultater|
|OneNote|Notebook|
|Outlook|Mail og kalender|
|Planner|Project status og opgaveoplysninger|
|Power Automate|Arbejdsprocesser|
|Power BI|Data, rapporter og dashboards|
|Project på internettet|Project planer|
|Oversigt|Køreplaner|
|SharePoint|Filer, lister Teams kanalwikidata|
|Stream|Videoer|
|Yammer|Samtaler|

Når du sletter en gruppe eller et team, slettes de fleste af de tilknyttede ressourcer også. Undtagelser omfatter:

- Videoer i Stream forbliver og ejes af den person, der har uploadet/optaget dem
- Flow i Power Automate forbliver og ejes af den person, der oprettede dem.
- Project og oversigtsdata i Project på internettet forbliver i CDS og kan gendannes separat.

Grupper og teams forbliver i blød sletning i 30 dage og kan gendannes når som helst. Men efter de 30 dage fjernes de og eventuelle tilknyttede ressourcer, f.eks. tjenester og indhold, fra det Microsoft 365 miljø. Alt indhold, der er beskyttet af en opbevaringspolitik, forbliver tilgængeligt via eDiscovery-søgninger.

## <a name="end-of-life-cycle-considerations-for-group-connected-services"></a>Overvejelser om afslutning af livscyklus i forbindelse med gruppeforbundne tjenester

Der er tre nøgleområder, som team- og gruppeejere og it-administratorer skal overveje, når du sletter en gruppe eller et team.

**Indhold**

Skal indholdet bevares, når teamet ikke længere er der? Er det tilstrækkeligt at stole på opbevaringsfunktioner i Microsoft 365, eller er noget af indholdet i apps og tjenester, der ikke tilbyder opbevaring? Skal indholdet bevares til administration af poster, arkivering eller fremtidig brug og referenceformål?

For at undgå potentielle tab af data skal disse spørgsmål stilles, før et team arkiveres eller slettes.

**Tjenester**

Skal indholdet forblive i den aktuelle arbejdsformular? Skal den Power BI rapport f.eks. fortsat være tilgængelig? Skal formularresultaterne være tilgængelige i oversigtsvisningen for visualiseringen? Er listerne i SharePoint sammenkædet med eller integreret nogen steder?

Disse spørgsmål skal stilles, før den underliggende gruppe slettes, fordi eksporten af indholdet muligvis ikke er tilstrækkelig.

**Gæsterne**

Når gæster inviteres til et team, oprettes der en gæstekonto i værtsorganisationens Azure Active Directory, før de føjes til teamet. Når et team slettes, fjernes gæster ikke fra Azure Active Directory. Selvom gæster ikke kan få adgang til grupper, websteder, teams eller indhold, som ikke er blevet delt med dem, kan de stadig potentielt bruge funktioner i Microsoft Teams f.eks. starte chats, stemme- og videoopkald og bruge apps.

En team- eller gruppeejer kan invitere en person uden for organisationen til at blive gæst i Azure Active Directory ved at føje vedkommende til et team. En teamejer kan dog ikke fjerne gæsten fra Azure Active Directory. Sletning af konti kan kun udføres af en global administrator eller brugeradministrator.

Det er vigtigt at udføre gæsteanmeldelser og forstå, om gæster skal fjernes fra Azure Active Directory ved teamsletning. Der kan være et gyldigt tilfælde, hvor gæster skal forblive i mappen, f.eks. være medlem af andre teams eller bruge andre Microsoft 365 eller Azure-tjenester.

## <a name="teams"></a>Teams

Teams-specifikt indhold er primært i form af samtaler.

Samtaler i kanaler kan ikke kopieres eller flyttes ved hjælp af oprindelig Microsoft Teams funktionalitet. De kan dog eksporteres ved hjælp af API'en til Graph.

Hvis der anvendes en opbevaringspolitik på Teams, bevares samtalerne, og de er tilgængelige via eDiscovery-søgninger. Ved hjælp af eDiscovery (Premium) kan du [genskabe en Teams chatsamtale](/microsoft-365/compliance/conversation-review-sets).


### <a name="archiving-a-team"></a>Arkivering af et team

Fordelen ved [arkivering af et team](/microsoftteams/archive-or-delete-a-team) er, at det giver fuld adgang til teamet, som det var. Brugerne kan stadig gennemse kanalsamtaler og åbne filer, selvom de ikke er aktive. Derudover kan teams ikke arkiveres, hvis der er behov for at fortsætte med at arbejde med dem (f.eks. hvis et projekt udvides).

Når et team arkiveres af en ejer, angives det til skrivebeskyttet for medlemmer både for indhold i teamet og, hvis det er valgt, det tilknyttede SharePoint websted. Formålet med denne handling er at sikre, at samtaler i kanaler bevares i deres eksisterende tilstand sammen med SharePoint-baseret indhold, f.eks. filer og wikier.

Der er ingen synlige ændringer på det SharePoint websted. Der kan dog ikke foretages ændringer af nogen filer eller lister, fordi SharePoint tilladelser for den Microsoft 365 gruppe er angivet til **Besøgende på webstedet**. Dette omfatter den OneNote notesbog for teamet, som er gemt i biblioteket Webstedsaktiver på SharePoint websted.

Når et team arkiveres, er den underliggende Microsoft 365 gruppe stadig underlagt udløbspolitikken (hvis det er angivet), og ejeren skal derfor fortsætte med at forny teamet.

Selvom teamets kanalsamtaler og SharePoint webstedsindhold er angivet til skrivebeskyttet, gælder det samme ikke for andre tilknyttede tjenester:

- Planner-buckets og -opgaver kan stadig oprettes, ændres og slettes.
- Formularer kan stadig modtage indsendelser.
- Den Outlook postkasse kan stadig modtage mails.
- Power BI dashboards, rapporter og data kan stadig ændres.
- Projekter og køreplaner kan stadig redigeres i Project på internettet.
- Videoer kan stadig uploades, redigeres og slettes i Stream.
- Flow i Power Automate kan stadig oprettes, ændres, slettes og fortsætter med at køre. (De vil dog mislykkes, hvis det kræves for at sende en meddelelse til en kanal af det arkiverede team.)

## <a name="forms"></a>Former

Selvom en formular kan flyttes fra en individuel konto til en gruppe, kan den ikke flyttes eller kopieres fra én gruppe til en anden. Der er tre tilgængelige indstillinger for en formular, når et team slettes.

**Dupliker formularen**

Formularer kan [deles som skabeloner](https://support.microsoft.com/office/82ea9d8a-260a-47a0-afdb-497f3d746e3f), så andre brugere kan kopiere dem til deres egen konto eller en gruppe. Dette bevarer ikke dataene fra indsendelser af resultater. kun formularstruktur, f.eks. spørgsmål og indstillinger.

**Eksportér resultater til et regneark**

Hvis dataene i formularsvar skal bevares, kan det opnås ved at [eksportere resultaterne til et Excel regneark](https://support.office.com/article/02859424-341d-406f-b32a-9a0fbaf357af). Dette eksporterer kun spørgsmålene og deres svar som data – det omfatter ikke grafer, der er oprettet af formularer.

**Slet formularen**

Selvom sletning af gruppen også medfører sletning af eventuelle tilknyttede formularer, kan gruppemedlemmer [direkte slette dem](https://support.microsoft.com/office/2207e468-ce1b-4c4a-a256-caf631d87af0) uden at være ejer af gruppen. Dette er dog et manuelt trin, der ikke giver nogen yderligere fordel.

## <a name="onenote"></a>OneNote

Den OneNote notesbog, der er inkluderet i en gruppe, gemmes i biblioteket Webstedsaktiver på det tilknyttede SharePoint websted. Selvom notesbogfiler nogle gange kan spredes på tværs af flere individuelle filer, kan de ikke kopieres og åbnes uafhængigt af hinanden. I stedet skal indholdet af den OneNote notesbog flyttes eller eksporteres ved hjælp af OneNote 2016.

**Flyt sider og sektioner til en anden notesbog**

[Individuelt at flytte sider eller sektioner til en anden notesbog](https://support.office.com/article/c3c8b098-7f9c-4c2a-a0dc-ebb83bc76364) giver ejerne mulighed for at rydde op i deres data og kun tage det, der skal bevares.

**Eksportér hele notesbogen som en pakke**

Hvis hele notesbogen skal bevares med dens eksisterende struktur, kan den [eksporteres som en OneNote pakkefil](https://support.office.com/article/a4b60da5-8f33-464e-b1ba-b95ce540f309) og derefter importeres til en ny placering. Dette kan i stedet bruges som en metode til at bevare indholdet i en enkelt fil i stedet for den eksisterende flerfilstruktur.

**Udskriv til PDF**

I scenarier, hvor noget af indholdet i notesbogen kun skal bevares som reference eller som poster, kan individuelle sider [udskrives til PDF og gemmes et andet sted](https://support.office.com/article/13d173b5-7f4c-45a8-94eb-9354d63af5cd).

## <a name="mailbox-and-calendar"></a>Postkasse og kalender

Det er ikke ualmindeligt, at den gruppetilhørende postkasse bruges, selvom mange samtaler kan være blevet dirigeret i teamkanaler. Postkassen gemmer kun mails, der er sendt direkte til den, og som ikke indeholder mails, der er sendt direkte til kanaler.

I nogle tilfælde kan de mails, der er gemt i postkassen, være meddelelser om møder, planlægningsopgaveopdateringer og andre app- eller systemoprettede meddelelser. Det er vigtigt, at indholdet af postkassen gennemses for at afgøre, om indholdet skal bevares eller slettes.

Hvis der anvendes en opbevaringspolitik i Exchange, bevares mails og kalenderelementer, og de er tilgængelige via eDiscovery-søgninger.

**Eksportér mail og kalender**

Gruppe- eller gruppemedlemmer kan [eksportere indholdet af postkassen og kalenderen til en Outlook-fil med data/personlige Storage (PST).](https://support.office.com/article/14252b52-3075-4e9b-be4e-ff9ef1068f91) Denne fil kan derefter gemmes et andet sted, eller indholdet kan importeres til en anden postkasse. Den første anbefales ikke, da der ikke kan søges i indholdet af PST-filen uden at åbne den i Outlook, og selve filen kan blive beskadiget med tiden.

**It-udført overførsel af indhold**

Administratorer kan bruge tredjepartsværktøjer til at overføre mail- og kalenderindhold mellem postkasser uden brugerinput. En potentiel lagerplacering kan være en delt postkasse, der udelukkende er oprettet for at fungere som et "arkiv" for indholdet i gruppepostkassen.

## <a name="planner"></a>Planner

Hver gruppe eller hvert team kan have flere planer. Det er vigtigt under processen til off-boarding for at sikre, at opbevaringskrav håndteres for hver plan. Ligesom de andre tjenester er der flere tilgange til indhold uden for bestyrelsen i Planner.

**Eksportér planen til et regneark**

Hvis det kun er nødvendigt at beholde en kopi af planen til registreringsformål, er den nemmeste metode at [eksportere planen til et Excel regneark](https://support.microsoft.com/office/4d850c6e-e548-4aab-83b4-b62b68662d2a). Dette er en envejshandling – der er ingen mulighed for at importere planer fra et regneark.

> [!IMPORTANT]
> Eksport af en plan til Excel tager de fleste oplysninger i planen, men indeholder ikke kommentarer, links eller filer.

**Kopiér og flyt opgaver til en anden plan**

Mens kopiering eller flytning af opgaver til en anden plan ser ud som en løsning, kan individuelle opgaver kun [kopieres eller flyttes mellem planer](https://support.microsoft.com/office/ad43a5d8-c1ad-42fd-b3da-fe97d72c8a1b) i den samme gruppe. Dette sikkerhedskopieres ikke dataene, hvis den gruppe, der er knyttet til planen, slettes.

**Kopiér hele planen**

Det er også muligt at [kopiere hele planen](https://support.microsoft.com/office/50401e13-a25f-40df-93c6-b608cc28c3d4). Kopiering kan ikke udføres til en eksisterende gruppe. Hvis du kopierer planen, oprettes der en ny gruppe. Desuden omfatter kopiering af hele planen ikke kommentarer, tildelinger, links, vedhæftede filer eller datoer.

## <a name="power-automate"></a>Power Automate

Flow, der er oprettet i Power Automate og knyttet til en gruppe eller et team, tilhører ikke gruppen. De ejes af forfatteren og deles blot med andre brugere og grupper. De påvirkes derfor ikke, hvis en gruppe eller et team slettes.

**Skift ejerskab af flowet**

Hvis flowet skal fortsætte med at fungere, kan alle ejere tilføje andre brugere eller Microsoft 365 grupper som ejere.

**Eksportér flowet**

Hvis flowet ikke behøver at fortsætte med at fungere, men det skal bevares til potentiel fremtidig brug, kan det [eksporteres som en fil](https://flow.microsoft.com/blog/import-export-bap-packages/) og importeres igen senere.

## <a name="power-bi"></a>Power BI

Power BI data og arbejdsområder kan fungere uafhængigt af grupper og teams, og på samme måde som andre arbejdsbelastninger er der forskellige måder at være uden for om bord på.

**Kopiér rapporter til et andet arbejdsområde**

Hvis du har brug for rapporten, når gruppen eller teamet er slettet, kan den [kopieres fra det eksisterende arbejdsområde til et andet arbejdsområde i Power BI](/power-bi/connect-data/service-datasets-copy-reports).

**Eksportér data fra et dashboard eller en rapport**

Hvis rapporten i stedet ikke længere skal være aktiv, men dataene skal bevares, kan den [eksporteres til Excel](/power-bi/visuals/power-bi-visualization-export-data).

## <a name="project"></a>Project

Projekter og køreplaner, der oprettes i Project til internettet, er knyttet til Microsoft 365 grupper og har tilgange til off-boarding svarende til Power BI.

**Tildel projektet til en anden gruppe**

Hvis projektet skal bevares i sin funktionelle tilstand ud over gruppens eller teamets levetid, kan det [tildeles til en anden Microsoft 365 gruppe](/project-for-the-web/access-a-project-after-group-is-deleted#reassign-the-project). Dette kan gøres ved hjælp af Dynamics 365 Administration.

**Eksportér data fra projektet eller køreplanen**

Ved hjælp af Dynamics 365 Administration er det muligt at [eksportere brugerdata fra projektet](/project-for-the-web/export-user-data-from-project-for-the-web) til et regneark. Dataene kan også eksporteres til Project fil (. MPP) og XML-filformater ved hjælp af PowerShell.

## <a name="sharepoint"></a>SharePoint

Alle filer i teamkanaler gemmes på det SharePoint websted for den tilknyttede gruppe. I nogle tilfælde kan der være andet indhold end dokumenter i SharePoint, f.eks. lister eller sider.

Filer gemmes normalt på tre primære placeringer på et SharePoint websted:

- Sider - bibliotek med webstedssider
- Billeder, der bruges på sider – biblioteket Webstedsaktiver
- Filer i kanaler – dokumentbibliotek
- Wikisider – Teams wikidatabiblioteket

Hvis webstedet har et eller flere underordnede websteder, skal processen ved udstigning gentages for hvert underordnet websted. Hvis teamet indeholder private eller delte kanaler, er der et separat SharePoint websted for hver kanal.

Når du fjerner filer fra en gruppe eller et team, er det vigtigt at overveje, at de muligvis deles med brugere, der ikke er medlemmer af gruppen eller teamet. Det kan være en god idé at kommunikere den forestående ændring til dem.

**Download filer**

Filer, der er gemt i SharePoint i et af de ovenfor nævnte biblioteker, kan [downloades til en lokal computer](https://support.office.com/article/5c7397b7-19c7-4893-84fe-d02e8fa5df05).

**Flyt filer**

Derudover kan filer [flyttes til en anden placering i SharePoint f.eks. et bibliotek på et andet websted](https://support.office.com/article/00e2f483-4df3-46be-a861-1f5f0c1a87bc).

**Eksportér liste**

Data, der er gemt på SharePoint lister, kan [eksporteres til et Excel regneark](https://support.office.com/article/bfb2ea48-6118-4fa9-abb6-cced9424e5d9) og importeres igen til en liste på et andet websted.

Alternativt kan et tredjepartsværktøj bruges til at overføre listen mellem websteder for at bevare funktionen, listevisninger, formatering og andre attributter.

**"Eksportér" wikifiler**

Wikiindhold i teamkanaler gemmes i en HTML-formateret fil i et dedikeret bibliotek på det tilknyttede SharePoint websted. De kan ikke let eksporteres og importeres til en anden kanalwiki, men kan konverteres til en HTML-fil og åbnes som en webside.

## <a name="microsoft-stream"></a>Microsoft Stream

På samme måde som Power Automate ejes videoer i Stream, der er knyttet til en gruppe eller et team, faktisk ikke af gruppen og slettes ikke, når gruppen slettes. Videoer i Stream ejes af den person, der har uploadet eller oprettet videoen, selvom de tilføjer brugere eller grupper som ejere. Møder, der er registreret i en Teams kanal, ejes af den person, der startede optagelsen.

**Tilføjelse af andre ejere**

Da videoen bevares i Stream, når gruppen slettes, kan den oprindelige ejer [dele videoen med andre brugere og grupper og endda tilføje dem som ejere](/stream/portal-edit-video).

**Download videoen**

I scenarier, hvor videoen ikke behøver at blive opbevaret i Stream eller skal gemmes på en anden placering, f.eks. et dataadministrationssystem, kan en ejer [downloade den lokalt](/stream/portal-download-video).

## <a name="yammer"></a>Yammer

I modsætning til samtaler i Microsoft Teams giver Yammer både brugere og administratorer mulighed for at flytte eller eksportere samtaler.

**Flyt samtaler til en anden gruppe eller et andet community**

Samtaler kan flyttes til en anden Yammer gruppe af alle brugere, ikke kun ejere eller administratorer. Dette er muligt i både den [klassiske Yammer](https://support.office.com/article/149c6399-4ac1-4ced-84d7-e0660960a872) og de [nye Yammer](https://support.office.com/article/d63debf1-1c90-4ec5-b5ae-8a00939a1680) grænseflader.

**Eksportér netværksdata**

Yammer netværksadministratorer [eksporterer netværksdata](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Men hvis du gør det, eksporteres alle samtaler for hele netværket. Den resulterende eksport viser gruppe-id'et. Det er muligt at filtrere samtaler baseret på dette id.

## <a name="related-topics"></a>Relaterede emner

[Fjern en tidligere medarbejder og beskyt data](/microsoft-365/admin/add-users/remove-former-employee)
