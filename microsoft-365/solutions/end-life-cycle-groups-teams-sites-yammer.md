---
title: Indstillinger for slutningen af livscyklus for grupper, teams og Yammer
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
description: Indstillinger for afslutning af livscyklus for grupper, teams og Yammer.
ms.openlocfilehash: 883af3878bd0bc68aa539fc1cc36b66c4f1cfe9e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589706"
---
# <a name="end-of-lifecycle-options-for-groups-teams-and-yammer"></a>Indstillinger for slutningen af livscyklus for grupper, teams og Yammer

Microsoft 365 Groups og Microsoft Teams fungerer med flere forbundne tjenester. Når en gruppe eller et team slettes, slettes de fleste af oplysningerne i de tilknyttede tjenester også. I denne artikel beskrives muligheder for at bevare oplysninger ved at flytte dem ud af gruppen eller teamet, før de slettes.

En almindelig fremgangsmåde for grupper eller teams, der ikke længere er påkrævet, er at flytte filerne ud af teamet og arkivere dem et andet sted, f.eks. et SharePoint dokumentbibliotek. Denne fremgangsmåde er baseret på en ældre arbejdsstil, hvor oplysninger er gemt i filer og mapper, og kommunikation udføres via mail.

I følgende tabel vises de tjenester, der er knyttet til grupper og teams, samt de vigtigste indholdstyper, der findes i hver af dem:

|Tjeneste|Typer af indhold|
|:------|:---------------|
|Teams|Kanalsamtaler, filer i kanaler|
|Formularer|Undersøgelsesstruktur og resultater|
|OneNote|Notesbog|
|Outlook|Mail og kalender|
|Planner|Project status og opgaveoplysninger|
|Power Automate|Arbejdsprocesser|
|Power BI|Data, rapporter og dashboards|
|Project på internettet|Project planer|
|Oversigt|Oversigter|
|SharePoint|Filer, lister, Teams kanalwikidata|
|Stream|Videoer|
|Yammer|Samtaler|

Når du sletter en gruppe eller et team, slettes de fleste af de tilknyttede ressourcer også. Undtagelser omfatter:

- Videoer i Stream forbliver og ejes af den person, der har uploadet/optaget dem
- Flows i Power Automate forbliver og ejes af den person, der har oprettet dem.
- Project og oversigtsdata i Project på internettet forbliver i CDS og kan gendannes separat.

Grupper og teams forbliver i en blød sletningstilstand i 30 dage og kan når som helst gendannes. Men efter de 30 dage bliver de og eventuelle tilknyttede ressourcer, f.eks. tjenester og indhold, fjernet fra Microsoft 365 miljø. Alt indhold, der er beskyttet af en opbevaringspolitik, forbliver tilgængeligt via eDiscovery-søgninger.

## <a name="end-of-life-cycle-considerations-for-group-connected-services"></a>Overvejelser om slutningen af livscyklus for gruppeforbundne tjenester

Der er tre vigtige områder, som team- og gruppeejere og it-administratorer skal overveje, når de sletter en gruppe eller et team.

**Indhold**

Skal indholdet bevares, når teamet ikke længere er der? Er det tilstrækkeligt at stole på opbevaringsfunktioner i Microsoft 365, eller er noget af indholdet i apps og tjenester, der ikke tilbyder opbevaring? Skal indholdet bevares med henblik på datastyring, arkivering eller fremtidig brug og reference?

For at undgå potentielle datatab skal du stille disse spørgsmål, før et team arkiveres eller slettes.

**Tjenester**

Skal indhold bevares i dets aktuelle arbejdsformular? Skal rapporten om Power BI fortsat være tilgængelig? Skal formularresultaterne være tilgængelige i visningen Visuel oversigt? Er listerne i SharePoint til eller integreret hvor som helst?

Disse spørgsmål skal stilles, før den underliggende gruppe slettes, da det muligvis ikke er nok at eksportere indholdet.

**Gæster**

Når gæster inviteres til et team, oprettes der en gæstekonto i værtsorganisationens Azure Active Directory før de føjes til teamet. Når et team slettes, fjernes gæster ikke fra Azure Active Directory. Gæster kan ikke få adgang til grupper, websteder, teams eller indhold, som ikke er blevet delt med dem, men de kan stadig bruge funktioner i Microsoft Teams f.eks. starte chatsamtaler, tale- og videoopkald og bruge apps.

En team- eller gruppeejer kan invitere personer uden for organisationen til at blive gæst i Azure Active Directory ved at føje dem til et team. En teamejer kan dog ikke fjerne gæsten fra Azure Active Directory. Sletning af konti kan kun udføres af en global administrator eller brugeradministrator.

Det er vigtigt at udføre gæstevurderinger og for at forstå, om gæster skal fjernes fra Azure Active Directory efter teamsletning. Der kan være et gyldigt tilfælde, hvor gæster skal forblive i kataloget, f.eks. være medlem af andre teams eller bruge andre Microsoft 365 eller Azure-tjenester.

## <a name="teams"></a>Teams

Teams specifikt indhold primært i form af samtaler.

Samtaler i kanaler kan ikke kopieres eller flyttes ved hjælp af oprindelige Microsoft Teams funktionalitet. De kan dog eksporteres ved hjælp af Graph API.

Hvis der anvendes en opbevaringspolitik for Teams, bevares og er samtalerne desuden tilgængelige via eDiscovery-søgninger. Ved hjælp af avanceret eDiscovery kan du [genoprette Teams chatsamtale](/microsoft-365/compliance/conversation-review-sets).


### <a name="archiving-a-team"></a>Arkivere et team

Fordelen ved at [arkivere et team](/microsoftteams/archive-or-delete-a-team) er, at det giver fuld adgang til teamet, som det var. Brugere kan stadig gennemse kanalsamtaler og åbne filer, også selvom de ikke er aktive. Desuden kan teams gøres uarkiverede, hvis der er behov for at fortsætte arbejdet på dem (f.eks. hvis et projekt forlænges).

Når et team arkiveres af en ejer, er det indstillet til skrivebeskyttet for medlemmer både for indhold i teamet og, hvis det er valgt, den tilknyttede SharePoint webstedet. Formålet med denne handling er at sikre, at samtaler i kanaler bevares i deres eksisterende tilstand sammen med SharePoint-baseret indhold som f.eks. filer og wikier.

I SharePoint er der ingen synlige ændringer. Der kan dog ikke foretages ændringer af nogen filer eller lister, fordi tilladelserne SharePoint for gruppen Microsoft 365 er indstillet til Besøgende **på webstedet**. Dette omfatter OneNote for teamet, som er gemt i biblioteket Webstedsaktiver på SharePoint websted.

Når et team arkiveres, er den underliggende Microsoft 365 gruppe stadig underlagt udløbspolitikken (hvis den er indstillet), og ejeren skal derfor fortsætte med at forny teamet.

Mens teamets kanalsamtaler og indhold på SharePoint er indstillet til skrivebeskyttet, gælder det samme ikke for andre tilknyttede tjenester:

- Planner-buckets og opgaver kan stadig oprettes, ændres og slettes.
- Formularer kan stadig modtage indsendelser.
- Den Outlook postkasse kan stadig modtage mails.
- Power BI dashboards, rapporter og data kan stadig ændres.
- Projekter og oversigter kan stadig redigeres i Project på internettet.
- Videoer kan stadig uploades, ændres og slettes i Stream.
- Flows i Power Automate kan stadig oprettes, ændres, slettes og fortsætter med at køre. (De vil dog mislykkes, hvis det er nødvendigt at sende en meddelelse til en kanal i det arkiverede team.)

## <a name="forms"></a>Formularer

Selvom en formular kan flyttes fra en enkelt konto til en gruppe, kan den ikke flyttes eller kopieres fra én gruppe til en anden. Der er tre tilgængelige indstillinger for en formular, når et team slettes.

**Dupliker formularen**

Formularer kan deles [som skabeloner](https://support.microsoft.com/office/82ea9d8a-260a-47a0-afdb-497f3d746e3f), så andre brugere kan kopiere dem til deres egen konto eller en gruppe. Dette bevarer ikke data fra resultatindsendelser; kun formularstruktur, f.eks. spørgsmål og indstillinger.

**Eksportere resultater til et regneark**

Hvis dataene i formularsvarene skal bevares, kan dette opnås ved at eksportere [resultaterne til et Excel regneark](https://support.office.com/article/02859424-341d-406f-b32a-9a0fbaf357af). Dette eksporterer kun spørgsmålene og deres svar som data – det omfatter ikke grafer, der er oprettet af Forms.

**Slette formularen**

Mens sletning af gruppen også vil resultere i sletning af alle tilknyttede formularer, kan gruppemedlemmerne [](https://support.microsoft.com/office/2207e468-ce1b-4c4a-a256-caf631d87af0) slette dem direkte uden at være ejer af gruppen. Dette er dog et manuelt trin, der ikke giver nogen yderligere fordel.

## <a name="onenote"></a>OneNote

Den OneNote notesbog, der er inkluderet i en gruppe, gemmes i biblioteket Webstedsaktiver i den tilknyttede SharePoint websted. Selvom notesbogfiler nogle gange kan være spredt ud over flere individuelle filer, kan de ikke kopieres og åbnes enkeltvis. I stedet skal indholdet i OneNote flyttes eller eksporteres ved hjælp af OneNote 2016.

**Flyt sider og sektioner til en anden notesbog**

[Individuelle flytninger af sider eller sektioner](https://support.office.com/article/c3c8b098-7f9c-4c2a-a0dc-ebb83bc76364) til en anden notesbog giver ejere mulighed for at rydde op i deres data og kun bruge det, der skal bevares.

**Eksportér hele notesbogen som en pakke**

Hvis hele notesbogen skal bevares med dens eksisterende struktur, kan den eksporteres som en [OneNote-pakkefil](https://support.office.com/article/a4b60da5-8f33-464e-b1ba-b95ce540f309) og derefter importeres til en ny placering. I stedet kan dette bruges som en metode til at bevare indholdet i en enkelt fil i stedet for den eksisterende flerfilstruktur.

**Udskriv til PDF**

I scenarier, hvor noget af indholdet i notesbogen kun skal bevares med henblik på reference eller som poster, kan individuelle sider udskrives til PDF og gemmes [et andet sted](https://support.office.com/article/13d173b5-7f4c-45a8-94eb-9354d63af5cd).

## <a name="mailbox-and-calendar"></a>Postkasse og kalender

Det er ikke ualmindeligt, at den gruppe-tilknyttede postkasse skal bruges, selvom mange samtaler kan have været udført inden for teamkanaler. Postkassen gemmer kun mails, der blev sendt direkte til den, og inkluderer ikke mails, der blev sendt direkte til kanaler.

I nogle tilfælde kan de mails, der er gemt i postkassen, være meddelelser om møder, Planner-opgaveopdateringer og andre app- eller systemgenererede meddelelser. det er vigtigt, at indholdet i postkassen gennemses for at afgøre, om indholdet skal bevares eller slettes.

Hvis der anvendes en opbevaringspolitik i Exchange, bevares og er kalenderelementerne bevaret og tilgængelige via eDiscovery-søgninger.

**Eksportér mail og kalender**

Team- eller gruppemedlemmer kan eksportere indholdet af postkassen og kalenderen til en [Outlook Data/Personal Storage (PST).](https://support.office.com/article/14252b52-3075-4e9b-be4e-ff9ef1068f91) Denne fil kan derefter gemmes et andet sted, eller indholdet kan importeres til en anden postkasse. The former isn't recommended as the contents of the PST file aren't searchable without opening it in Outlook, and the file itself can become corrupted over time.

**Overførsel af indhold udført af it-365**

Administratorer kan bruge tredjepartsværktøjer til at overføre mail- og kalenderindhold mellem postkasser uden brugerens handling. En potentiel lagerplacering kan være en delt postkasse, der kun er oprettet til at fungere som et "arkiv" af gruppens postkasseindhold.

## <a name="planner"></a>Planner

Hver gruppe eller hvert team kan have flere planer. Det er vigtigt under processen at sikre opbevaringskravene for hver plan. Ligesom de andre tjenester er der flere metoder til off-board indhold i Planner.

**Eksportér planen til et regneark**

Hvis det kun er nødvendigt at bevare en kopi af planen til registreringsformål, er den nemmeste tilgang at eksportere planen til et [Excel regneark](https://support.microsoft.com/office/4d850c6e-e548-4aab-83b4-b62b68662d2a). Dette er en envejshandling – der er ingen mulighed for at importere planer fra et regneark.

> [!IMPORTANT]
> Hvis du eksporterer en Excel vil det tage de fleste oplysninger inden for planen, men det omfatter ikke kommentarer, links eller filer.

**Kopiere og flytte opgaver til en anden plan**

Mens kopiering eller flytning af opgaver til en anden plan ser ud som en løsning, kan individuelle opgaver kun kopieres eller flyttes mellem [planer](https://support.microsoft.com/office/ad43a5d8-c1ad-42fd-b3da-fe97d72c8a1b) inden for den samme gruppe. Dette sikkerhedskopier ikke dataene, hvis den gruppe, der er knyttet til planen, slettes.

**Kopiér hele planen**

Det er også muligt at [kopiere hele planen](https://support.microsoft.com/office/50401e13-a25f-40df-93c6-b608cc28c3d4). Kopiering kan ikke udføres til en eksisterende gruppe. Når du kopierer planen, oprettes der en ny gruppe. Desuden vil kopiering af hele planen ikke indeholde kommentarer, tildelinger, links, vedhæftede filer eller datoer.

## <a name="power-automate"></a>Power Automate

Flows, der Power Automate og knyttet til en gruppe eller et team, tilhører ikke gruppen. De ejes af opretteren og deles blot med andre brugere og grupper. De påvirkes derfor ikke, hvis en gruppe eller et team slettes.

**Ændre ejerskabet af flowet**

Hvis flowet skal fortsætte med at fungere, kan alle ejere tilføje andre brugere eller Microsoft 365 grupper som ejere.

**Eksportér flowet**

Hvis flowet ikke behøver at fortsætte med at fungere, men det skal bevares til fremtidig brug, kan det eksporteres som en [fil og](https://flow.microsoft.com/blog/import-export-bap-packages/) importeres igen senere.

## <a name="power-bi"></a>Power BI

Power BI og arbejdsområder kan fungere uafhængigt af grupper og teams, og på samme måde som andre arbejdsbelastninger tilbyder andre måder at blive off-boarded på.

**Kopiere rapporter til et andet arbejdsområde**

Hvis du skal bruge rapporten, når gruppen eller teamet er blevet slettet, kan den kopieres fra det eksisterende arbejdsområde til et andet [arbejdsområde Power BI](/power-bi/connect-data/service-datasets-copy-reports).

**Eksportere data fra et dashboard eller en rapport**

Hvis rapporten ikke længere skal være aktiv, men dataene skal bevares, kan de i stedet eksporteres [til Excel](/power-bi/visuals/power-bi-visualization-export-data).

## <a name="project"></a>Project

Projekter og oversigter, der er oprettet Project til internettet, er knyttet til Microsoft 365-grupper og har metoder til at nedsnappe på samme måde som Power BI.

**Tildele projektet til en anden gruppe**

Hvis projektet skal bevares i dets funktionelle tilstand ud over gruppens eller teamets levetid, kan det tildeles til [en anden Microsoft 365 gruppe](/project-for-the-web/access-a-project-after-group-is-deleted#reassign-the-project). Dette kan gøres ved hjælp af Dynamics 365 Administrationscenter.

**Eksportér data fra projektet eller oversigten**

Ved hjælp af Dynamics 365 Administration er det muligt at [eksportere brugerdata fra projektet](/project-for-the-web/export-user-data-from-project-for-the-web) til et regneark. Dataene kan også eksporteres til en Project fil (. MPP) og XML-filformater ved hjælp af PowerShell.

## <a name="sharepoint"></a>SharePoint

Alle filer i teamkanaler gemmes på SharePoint for den tilknyttede gruppe. I nogle tilfælde kan der være andet indhold end dokumenter i SharePoint, f.eks. lister eller sider.

Filer gemmes normalt på tre primære placeringer på et SharePoint websted:

- Sider – biblioteket Webstedssider
- Billeder, der bruges på sider – biblioteket Webstedsaktiver
- Filer i kanaler – biblioteket Dokumenter
- Wikisider – Teams wikidatabibliotek

Hvis webstedet har et eller flere underordnede websteder, skal overskrivningsprocessen gentages for hvert underordnet websted. Hvis teamet indeholder private kanaler, er der et separat SharePoint for hver kanal.

Når du fjerner filer fra en gruppe eller et team, er det vigtigt at overveje, at de kan deles med brugere, der ikke er medlemmer af gruppen eller teamet. Du ønsker måske at kommunikere den foreende ændring til dem.

**Download filer**

Filer, der er SharePoint i et af de biblioteker, der er nævnt ovenfor, [kan downloades til en lokal computer](https://support.office.com/article/5c7397b7-19c7-4893-84fe-d02e8fa5df05).

**Flyt filer**

Desuden kan filer flyttes til en [anden placering i et SharePoint f.eks. et bibliotek på et andet websted](https://support.office.com/article/00e2f483-4df3-46be-a861-1f5f0c1a87bc).

**Eksportér liste**

Data, der er SharePoint lister, kan eksporteres til et [Excel regneark](https://support.office.com/article/bfb2ea48-6118-4fa9-abb6-cced9424e5d9) og importeres igen til en liste på et andet websted.

Alternativt kan et tredjepartsværktøj bruges til at overføre listen mellem websteder for at bevare funktioner, listevisninger, formatering og andre attributter.

**"Eksportér" wikifiler**

Wikiindhold i teamkanaler gemmes i en HTML-formateret fil i et dedikeret bibliotek på det tilknyttede SharePoint websted. De kan ikke uden videre eksporteres og importeres til en anden kanalwiki, men kan konverteres til en HTML-fil og åbnes som en webside.

## <a name="microsoft-stream"></a>Microsoft Stream

Ligesom Power Automate, ejes videoer i Stream, der er knyttet til en gruppe eller et team, faktisk ikke af gruppen og slettes ikke, når gruppen slettes. Videoer i Stream ejes af den person, der har uploadet eller oprettet videoen, også selvom de tilføjer brugere eller grupper som ejere. Møder, der er optaget i Teams kanal, ejes af den person, der startede optagelsen.

**Tilføje andre ejere**

Da videoen bevares i Stream, når gruppen slettes, kan den oprindelige ejer dele videoen med andre brugere og grupper og endda tilføje [dem som ejere](/stream/portal-edit-video).

**Download videoen**

I scenarier, hvor videoen ikke behøver at blive bevaret i Stream eller skal gemmes på en anden placering, f.eks. et datastyringssystem, kan ejeren [downloade den lokalt](/stream/portal-download-video).

## <a name="yammer"></a>Yammer

I modsætning til samtaler i Microsoft Teams giver Yammer brugere og administratorer mulighed for at flytte eller eksportere samtaler.

**Flyt samtaler til en anden gruppe eller et andet community**

Samtaler kan flyttes til en anden Yammer gruppe af en hvilken som helst bruger, ikke kun ejere eller administratorer. Dette er muligt både i den [klassiske Yammer](https://support.office.com/article/149c6399-4ac1-4ced-84d7-e0660960a872) og [de nye Yammer grænseflader](https://support.office.com/article/d63debf1-1c90-4ec5-b5ae-8a00939a1680).

**Eksportér netværksdata**

Yammer af [netværksadministratorer eksporterer netværksdata](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Men hvis du gør dette, eksporteres alle samtaler for hele netværket. Eksportresultaterne viser gruppe-id'et. Det er muligt at filtrere samtaler baseret på dette id.

## <a name="related-topics"></a>Relaterede emner

[Fjern en tidligere medarbejder, og beskyt data](/microsoft-365/admin/add-users/remove-former-employee)
