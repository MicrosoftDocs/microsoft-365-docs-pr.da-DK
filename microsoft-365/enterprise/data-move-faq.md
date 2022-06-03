---
title: Generelle ofte stillede spørgsmål om dataflytning
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/31/2022
audience: ITPro
ms.topic: faq
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Få svar på ofte stillede spørgsmål om flytning af kernedata til et nyt Office 365 datacenter geo.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 3164612238010e72eb02510e1264cca528b80f38
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65874311"
---
# <a name="data-move-general-faq"></a>Generelle ofte stillede spørgsmål om dataflytning

Her er svar på generelle spørgsmål om flytning af inaktive kernekundedata til et nyt datacenter geo.

### <a name="what-customers-are-eligible-to-request-a-move"></a>Hvilke kunder er berettiget til at anmode om en flytning?
<details><summary>Klik for at udvide</summary>

Eksisterende Microsoft 365 kommercielle kunder, der har valgt et land, der er berettiget til det nye datacenter Geo, kan anmode om en flytning. Programmet findes kun for lejere med en berettiget landekode, der er tildelt den Microsoft 365 lejer, til at overføre centrale kundedata som inaktive data for berettigede arbejdsbelastninger til det tilsvarende Microsoft 365 datacenter geo. Se [Sådan anmoder du om, at dine data flyttes](request-your-data-move.md) for at bekræfte, om landet er berettiget.

</details>

### <a name="how-do-we-define-core-customer-data"></a>Hvordan definerer vi kernekundedata?
<details><summary>Klik for at udvide</summary>

Kernekundedata er et begreb, der refererer til et undersæt af kundedata, der er defineret i [vilkårene for Microsoft Online Services](https://aka.ms/ost):

- Exchange Online postkasseindhold (brødtekst, kalenderposter og indholdet af vedhæftede filer i mails)
- SharePoint onlinewebstedsindhold og de filer, der er gemt på det pågældende websted
- Filer, der er overført til OneDrive for Business

</details>

### <a name="what-is-in-scope-for-teams-migration"></a>Hvad er omfanget for Teams migrering?
<details><summary>Klik for at udvide</summary>

Ud over Exchange Online SharePoint Online og OneDrive for Business. Microsoft overfører Teams data til det lokale datacenter.

- Teams chatbeskeder, herunder private meddelelser og kanalmeddelelser.
- Teams billeder, der bruges i chats.

Teams filer gemmes i SharePoint Online, og Teams chatfiler gemmes i OneDrive for Business. Talebesked, kalender og kontakter gemmes i Exchange Online. I mange tilfælde bruges Exchange Online, SharePoint Online og OneDrive for Business allerede af kunden i det lokale datacenter Geo og er også en del af Microsoft 365 migrationsprogrammet for berettigede kundelande.

</details>

### <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a>Hvornår er min migrering fuldført, så min lejers kernekundedata gemmes inaktivt i mit nye geo?
<details><summary>Klik for at udvide</summary>

På grund af delte afhængigheder mellem Exchange Online og SharePoint Online/OneDrive for Business kan enhver overførsel ikke betragtes som fuldført, før begge tjenester er migreret. Exchange Online og SharePoint Online/OneDrive for Business ofte overføres på separate tidspunkter og uafhængigt af hinanden. Kundelejere modtager bekræftelse i Meddelelsescenter, når hver tjenesteoverførsel er fuldført, og kan når som helst få vist dataplaceringskortet i Administration Center for at bekræfte de centrale kundedata på restplaceringen for hver tjeneste.

</details>

### <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a>Hvordan sikrer du, at mine kundedata er sikre under flytningen, og at jeg ikke oplever nedetid?
<details><summary>Klik for at udvide</summary>

Dataflytninger er en back end-tjenestehandling med minimal indvirkning på slutbrugerne. De funktioner, der kan påvirkes, er angivet i [Under og efter dine data flyttes](during-and-after-your-data-move.md). Vi overholder [Serviceniveauaftalen for Microsoft Online Services,](https://go.microsoft.com/fwlink/p/?LinkId=523897) så der ikke er noget, som kunderne behøver at forberede sig på eller overvåge under flytningen.

Alle Microsoft 365 tjenester kører de samme versioner i datacentrene, så du kan være sikker på, at funktionaliteten er ensartet. Din tjeneste understøttes fuldt ud under hele processen.

</details>

### <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a>Hvad er virkningen af at have forskellige tjenester placeret i forskellige geografiske områder?
<details><summary>Klik for at udvide</summary>

Nogle af de Microsoft 365 tjenester kan være placeret i forskellige geografiske områder for nogle eksisterende kunder og for kunder, der er midt i flytteprocessen. Vores tjenester kører uafhængigt af hinanden, og der er ingen indvirkning på brugeroplevelsen, hvis det er tilfældet. I forbindelse med dataopbevaring kan en lejeroverførsel dog ikke betragtes som fuldført, før både Exchange Online og SharePoint Online/OneDrive for Business migreres til det samme datacenter geo.

</details>

### <a name="where-is-my-core-customer-data-located"></a>Hvor er mine kernekundedata placeret?
<details><summary>Klik for at udvide</summary>

Kundelejeradministratorer kan når som helst få vist dataplaceringskortet i Administration Center for at bekræfte de centrale kundedata på inaktive placeringer for hver tjeneste, især for deres lejer. Vi publicerer også placeringen af datacenter-geos, datacentre og placering af Office 365 kundedata på [de Microsoft 365 interaktive datacenterkort](https://office.com/datamaps) som en reference til de aktuelle standardkundedata på inaktive placeringer for nye lejere. Du kan bekræfte placeringen af dine inaktive kundedata via afsnittet Dataplacering under din organisationsprofil i Microsoft 365 Administration.

</details>

### <a name="when-will-i-be-able-to-request-a-move"></a>Hvornår kan jeg anmode om en flytning?
<details><summary>Klik for at udvide</summary>

Se siden [Sådan anmoder du om flytning af data](request-your-data-move.md) for understøttede tidsrammer for dit datacenter geo.

</details>

### <a name="how-can-i-request-to-be-moved"></a>Hvordan kan jeg anmode om at blive flyttet?
<details><summary>Klik for at udvide</summary>

Berettigede kunder får vist en side i deres [Microsoft 365 Administration](https://admin.microsoft.com/). Se [Sådan anmoder du om flytning af dine data for at](request-your-data-move.md) få en vejledning i, hvordan du anmoder om en flytning.

</details>

### <a name="can-i-change-my-selection-after-requesting-a-move"></a>Kan jeg ændre mit valg, når jeg har anmodet om en flytning?
<details><summary>Klik for at udvide</summary>

Det er ikke muligt for os at fjerne dig fra processen, når du har indsendt din anmodning.

</details>

### <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a>Hvad sker der, hvis jeg ikke anmoder om en flytning inden fristens udløb?
<details><summary>Klik for at udvide</summary>

Vi kan ikke acceptere anmodninger om overførsel efter den åbne tilmeldingsperiode.

</details>

### <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a>Hvad gør jeg, hvis jeg vil flytte mine data for at opnå bedre netværksydeevne?
<details><summary>Klik for at udvide</summary>

Fysisk nærhed til et Microsoft 365 datacenter er ikke en garanti for en bedre netværksydeevne. Der er mange faktorer og komponenter, der påvirker netværkets ydeevne mellem slutbrugeren og Microsoft 365-tjenesten. Du kan få flere oplysninger om dette og justering af ydeevnen under [Netværksplanlægning og justering af ydeevnen for Microsoft 365](network-planning-and-performance.md).

</details>

### <a name="do-all-the-services-move-their-data-on-the-same-day"></a>Flytter alle tjenesterne deres data samme dag?
<details><summary>Klik for at udvide</summary>

Hver tjeneste flyttes uafhængigt og flytter sandsynligvis deres data på forskellige tidspunkter.

</details>

### <a name="can-i-choose-when-i-want-my-data-to-be-moved"></a>Kan jeg vælge, hvornår mine data skal flyttes?
<details><summary>Klik for at udvide</summary>

Kunder kan ikke vælge en bestemt dato, de kan ikke forsinke deres flytning, og vi kan ikke dele en bestemt dato eller tidsramme for flytningen.

</details>

### <a name="can-you-share-when-my-data-will-be-moved"></a>Kan du dele, når mine data flyttes?
<details><summary>Klik for at udvide</summary>

Dataflytninger er en back end-handling, der har minimal indvirkning på slutbrugerne. Den kompleksitet, præcision og skalering, hvor vi skal udføre dataflytninger i et globalt drevet og automatiseret miljø, forhindrer os i at dele, når en dataflytning forventes at blive fuldført for din lejer eller en anden enkelt lejer. Kunderne modtager én bekræftelse i Meddelelsescenter pr. deltagertjeneste, når dataflytningen er fuldført.

</details>

### <a name="what-happens-if-users-access-services-while-the-data-is-being-moved"></a>Hvad sker der, hvis brugerne tilgår tjenester, mens dataene flyttes?
<details><summary>Klik for at udvide</summary>

Se [Under og efter dine data flyttes](during-and-after-your-data-move.md) for at få vist en komplet liste over funktioner, der kan være begrænset under dele af dataflytningen for hver tjeneste.

</details>

### <a name="how-do-i-know-the-move-is-complete"></a>Hvordan gør jeg vide, at flytningen er fuldført?
<details><summary>Klik for at udvide</summary>

Se Microsoft 365 Meddelelsescenter for at få bekræftet, at flytningen af hver tjenestes data er fuldført. Når hver tjenestes data flyttes, sender vi en meddelelse om fuldførelse, så du får tre meddelelser om fuldførelse: én for Exchange Online, SharePoint Online og Skype for Business Online. Du kan også bekræfte placeringen af dine inaktive kundedata via afsnittet Dataplacering under din organisationsprofil i Microsoft 365 Administration.

</details>

### <a name="i-am-a-microsoft-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a>Jeg er Microsoft 365 kunde i et af de nye datacenter geos, men da jeg tilmeldte mig, valgte jeg et andet land. Hvordan kan jeg flyttes til det nye datacenter Geo?
<details><summary>Klik for at udvide</summary>

Det er ikke muligt at ændre det tilmeldingsland, der er knyttet til din lejer. Du skal i stedet oprette en ny Microsoft 365 lejer med et nyt abonnement og manuelt flytte dine brugere og data til den nye lejer.

</details>

### <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-microsoft-365-during-the-exchange-online-move"></a>Hvad sker der, hvis vi er i gang med at overføre maildata til Microsoft 365 under flytningen af Exchange Online?
<details><summary>Klik for at udvide</summary>

Dette er et meget almindeligt scenarie og understøttes fuldt ud. Cloudmigrering mellem datacenter-geos forstyrrer ikke migrering af cloudpostkasser i det lokale miljø.

</details>

### <a name="can-i-pilot-some-users"></a>Kan jeg styre nogle brugere?
<details><summary>Klik for at udvide</summary>

Du kan oprette en separat prøveversionslejer for at teste forbindelsen, men prøveversionslejer kan ikke kombineres på nogen måde med din eksisterende lejer.

</details>

### <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a>Jeg vil ikke vente på, at Microsoft flytter mine data. Kan jeg blot oprette en ny lejer og flytte mig selv?
<details><summary>Klik for at udvide</summary>

Ja, processen vil dog ikke være så problemfri, som hvis Microsoft skulle udføre dataflytningen.

Hvis du opretter en ny lejer, når det nye datacenter Geo er tilgængeligt, hostes den nye lejer i den nye geo. Denne nye lejer er helt adskilt fra din tidligere lejer, og du vil være ansvarlig for at flytte alle brugerpostkasser, webstedsindhold, domænenavne og andre data. Bemærk, at du ikke kan flytte lejernavnet fra én lejer til en anden. Vi anbefaler, at du venter på det flytteprogram, der leveres af Microsoft, da vi sørger for at flytte alle indstillinger, data og abonnementer for dine brugere.

</details>

### <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a>Mine kundedata er allerede blevet flyttet til et nyt datacenter geo. Kan jeg flytte tilbage?
<details><summary>Klik for at udvide</summary>

Nej, det er ikke muligt. Kunder, der er blevet flyttet til nye geo-datacentre, kan ikke flyttes tilbage. Som kunde i et hvilket som helst geografisk område vil du opleve den samme kvalitet af service-, ydeevne- og sikkerhedskontroller, som du gjorde før. [Microsoft 365 Multi Geo](https://aka.ms/multi-geo) er tilgængelig for nogle kunder som et tilføjelsesprogram og gør det muligt for en enkelt lejer at oprette flere satellit-geos og flytte brugerdata til disse geografiske områder med forpligtelser til dataopbevaring.

</details>

### <a name="will-microsoft-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a>Vil Microsoft 365 lejere, der hostes i de nye datacentre, være tilgængelige for brugere uden for landet?
<details><summary>Klik for at udvide</summary>

Ja. Microsoft har et stort globalt netværk med offentlige internetforbindelser på mere end 130 placeringer i 35 lande over hele verden med peeringaftaler med mere end 2.700 internetudbydere. Brugerne kan få adgang til datacentrene, uanset hvor de er på internettet.

</details>

### <a name="my-tenant-has-configured-the-multi-geo-add-on-can-i-still-enroll-in-my-tenant-in-the-microsoft-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a>Min lejer har konfigureret Multi Geo-tilføjelsesprogrammet. Kan jeg stadig tilmelde mig min lejer i Microsoft 365 Flyt program? for at ændre min geostandard og flytte alle brugere, der ikke er i et satellitområde, til det nye geostandardområde?
<details><summary>Klik for at udvide</summary>

Ja, din lejer er berettiget til at tilmelde sig, men der er betydelige overvejelser, da flytning på lejerniveau ikke understøttes fuldt ud for kunder, der har konfigureret [Multi-Geo](https://aka.ms/multi-geo).

SharePoint Online og OneDrive for Business kan ikke overføres til det nye datacenter geo på lejerniveau via dette program. Kundeadministratoren kan konfigurere OneDrive for Business shares til at flytte til et hvilket som helst tilgængeligt område ved hjælp af Multi-Geo, men standardplaceringen for lejeren kan ikke ændres, når Multi-Geo er konfigureret for en lejer.

For kunder, der tilmelder sig migrering – flytter vi alle Exchange Online postkasser fra din aktuelle standard-geo til dit nye lokale datacenter geo og opdaterer standardområdet for Exchange Online. Vi flytter ikke nogen EXO-postkasser, der er konfigureret i Multi Geo-satellitområder, for fortsat at respektere dataopbevaring af satellitområder, som du har til hensigt.  Teams lejermigrering for chattjenester for kunder med en Multi Geo-konfiguration fungerer på samme måde som Exchange Online.

</details>

### <a name="i-have-public-folders-deployed-in-my-tenant-what-will-be-the-impact-on-public-folder-access-during-or-after-the-move"></a>Jeg har udrullet offentlige mapper i min lejer. Hvad vil påvirke adgangen til offentlige mapper under eller efter flytningen?
<details><summary>Klik for at udvide</summary>

Det påvirker ikke slutbrugere, der tilgår offentlige mapper under eller efter flytning af offentlige mapper. De offentlige mapper er dog muligvis ikke tilgængelige til administration i værktøjet Exchange Administration Center, før alle postkasser i offentlige mapper flyttes i samme område. Du kan finde flere oplysninger i [denne artikel](https://aka.ms/pfxrf) .

</details>

### <a name="related-topics"></a>Relaterede emner

[Flytning af kernedata til nye Microsoft 365 geos for datacentre](moving-data-to-new-datacenter-geos.md)

[Sådan anmoder du om flytning af dine data](request-your-data-move.md)

[Microsoft 365 Multi Geo](https://aka.ms/multi-geo)

[Microsoft 365 interaktivt datacenterkort](https://office.com/datamaps)

[Microsoft 365 support](../admin/get-help-support.md)

[Nyt datacenter-geos til Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)

[Azure-tjenester efter område](https://azure.microsoft.com/regions/)
