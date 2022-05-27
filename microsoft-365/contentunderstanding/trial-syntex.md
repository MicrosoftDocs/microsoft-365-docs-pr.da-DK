---
title: Kør en prøveversion af Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris; jaeccles
ms.date: ''
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom:
- Adopt
- admindeeplinkMAC
search.appverid: ''
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du planlægger, tilmelder dig og kører et prøvepilotprogram til SharePoint Syntex i din organisation.
ms.openlocfilehash: ccbf1208d5c655171825b5a96f3a78b25ea3bbf2
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754438"
---
# <a name="run-a-trial-of-microsoft-sharepoint-syntex"></a>Kør en prøveversion af Microsoft SharePoint Syntex

I denne artikel beskrives det, hvordan du konfigurerer og kører et forsøgsprogram til installation af SharePoint Syntex i din organisation. Den anbefaler også bedste praksis for prøveversionen.

## <a name="sign-up-for-a-trial"></a>Tilmeld dig en prøveversion

Prøveversionen af SharePoint Syntex giver adgang til 300 brugere i 30 dage.

> [!NOTE]
> Op til 300 brugere er inkluderet i prøveversionen for at sikre automatisk tilføjelse af 1 million AI Builder-kreditter. Du behøver ikke at inkludere 300 brugere for at få en prøveversion.

Du kan hente prøveversionen fra en af følgende kilder:

- Siden [SharePoint Syntex produkt](https://www.microsoft.com/microsoft-365/enterprise/sharepoint-syntex?activetab=pivot:overviewtab)

- [Microsoft 365 Administration](https://admin.microsoft.com)
    1. Log på [Microsoft 365 Administration](https://admin.microsoft.com).
    2. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">**Faktureringskøbstjenester**</a> > .
    3. Rul ned til afsnittet **Tilføjelsesprogrammer** .
    4. Vælg **Detaljer** i feltet SharePoint Syntex.
    5. Vælg **Start gratis prøveversion**.
    6. Følg de resterende trin i guiden for at bekræfte prøveversionen.

Du skal være Microsoft 365 global administrator eller faktureringsadministrator for at aktivere en prøveversion.

### <a name="who-should-be-involved-in-a-trial"></a>Who bør inddrages i en retssag

|Rolle|Aktivitet|
|---|---|
|Microsoft 365 global administrator eller faktureringsadministrator|Aktivér prøveversionen, og tildel licenser|
|Microsoft 365 global administrator eller SharePoint administrator|Konfigurer SharePoint Syntex, og opret indholdscentre|
|Erhvervsbrugere|Modelopbygning og -test|

### <a name="before-you-activate-a-trial"></a>Før du aktiverer en prøveversion

Hvis du vil planlægge en SharePoint Syntex prøveversion, skal du overveje følgende faktorer:

- Den mest meningsfulde test udføres på scenarier og data i den "virkelige verden".
- Du kan kun aktivere en prøveversion af SharePoint Syntex én gang pr. lejer.

En test- eller demolejer kan bruges som en "tørkørsel" til at gennemgå aktiveringstrinnene og administrative kontroller. Men det er sandsynligvis bedst at evaluere modelopbygning på en produktionslejer.

Planlægning og forretningsengagement er afgørende for at maksimere værdien af en prøveversion på en produktionslejer. Du bør engagere et eller flere forretningsområder for at identificere tre til seks use cases, der potentielt kan håndteres af SharePoint Syntex. Disse use cases skal:

- Medtag scenarier, der kan løses ved enten formularbehandling eller model til dokumentforståelse.
- Hav en klar forståelse af formålet med alle udtrukne metadata. f.eks. visning af formatering eller automatisering ved hjælp af Power Automate. Selvom SharePoint Syntex fokuserer på at klassificere dokumenter og udtrække metadata, er den værdi, der skal kvantificeres, hvad disse metadata muliggør.
- Være baseret på et defineret sæt data. f.eks. specifikke SharePoint websteder eller biblioteker. En almindelig misforståelse af SharePoint Syntex er, at generelle modeller kan anvendes på tværs af alt organisationsindhold. En mere præcis visning er, at modeller er udviklet til at hjælpe med at løse specifikke forretningsproblemer på målrettede placeringer.

Alle disse use cases passer muligvis ikke til SharePoint Syntex. Målet med en kvalitetsprøveperiode er ikke at bevise, at SharePoint Syntex passer til alle scenarierne. Prøveversionen bør i stedet hjælpe dig med bedre at forstå værdien af produktet.

For hver af de planlagte use cases skal du identificere brugere, der er eksperter i det relaterede indhold eller den relaterede proces. Oprettelsen af SharePoint Syntex modeller fokuserer på domæneeksperter i indholdet i stedet for på it-fagfolk eller udviklerressourcer.

## <a name="activate-a-trial"></a>Aktivér en prøveversion

Når du starter en prøveversion, skal du:

- Tildel licenser til de relevante brugere.
- Udfør [yderligere konfiguration af SharePoint Syntex](set-up-content-understanding.md).
  - Det kan være en god idé at [oprette flere indholdscentre](create-a-content-center.md).

Når prøveversionen er aktiveret, kan du oprette modeller og behandle filer. Se [vejledning til oprettelse af modeller](create-a-content-center.md).

## <a name="during-a-trial"></a>Under en prøveversion

Prøveperioder er begrænsede, så det er bedst først at fokusere på, om SharePoint Syntex modeller kan klassificere dokumenter og udtrække metadata for de definerede use cases. Når prøveperioden er ovre, kan du evaluere, hvordan metadataene kan udnyttes.

## <a name="after-a-trial"></a>Efter en prøveversion

På baggrund af resultatet af prøveversionen kan du beslutte, om du vil fortsætte med at bruge SharePoint Syntex i produktionen.

### <a name="proceed-to-production-use"></a>Fortsæt til produktionsbrug

For at sikre kontinuitet i tjenesten skal du købe det påkrævede antal [licenser](syntex-licensing.md) og tildele disse licenser til brugere. Prøveversionsbrugere, der ikke har en fuld licens i slutningen af prøveperioden, kan ikke bruge SharePoint Syntex fuldt ud.

Du skal muligvis estimere din forventede brug af formularbehandling og -plan for det forventede antal AI Builder-kreditter. Du kan få hjælp under [Estimer den AI Builder-kapacitet, der passer til dig](https://powerapps.microsoft.com/ai-builder-calculator/).

### <a name="dont-proceed-to-production-use"></a>Fortsæt ikke med produktionsbrug

Hvis du ikke køber licenser efter prøveversionen:

- Du kan ikke oprette nye modeller.
- Biblioteker, der kørte modeller, klassificerer ikke længere automatisk filer eller udtrækker modeller.
- Tidligere klassificerede filer eller udpakkede metadata påvirkes ikke.
- Indholdscentre og alle modeller til dokumentforståelse slettes ikke automatisk. Disse forbliver tilgængelige til brug, hvis du beslutter dig for at købe licenser i fremtiden.
- Formularbehandlingsmodeller gemmes i Dataverse-forekomsten (tidligere kaldet Common Data Service (CDS)) i Power Platform-standardmiljøet. Disse kan bruges med fremtidige licenser til SharePoint Syntex eller med AI Builder-funktioner i Power Platform.

## <a name="see-also"></a>Se også

[Kom i gang med at indføre SharePoint Syntex](adoption-getstarted.md)
