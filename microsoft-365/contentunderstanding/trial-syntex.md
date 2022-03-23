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
description: Få mere at vide om, hvordan du planlægger og kører et prøveprogram til SharePoint Syntex i din organisation.
ms.openlocfilehash: 74b44c14140f26e0744aac73fd948e58d9d33e24
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63593936"
---
# <a name="run-a-trial-of-microsoft-sharepoint-syntex"></a>Kør en prøveversion af Microsoft SharePoint Syntex

I denne artikel beskrives det, hvordan du konfigurerer og kører et prøveprogram for at SharePoint Syntex i organisationen. Det anbefaler også bedste fremgangsmåder for prøveversionen.

## <a name="sign-up-for-a-trial"></a>Tilmeld dig en prøveversion

Prøveversionen af SharePoint Syntex giver adgang til 300 brugere i 30 dage.

> [!NOTE]
> Op til 300 brugere er inkluderet i prøveversionen for at sikre automatisk tilføjelse af 1 million AI Builder-kreditter. Du behøver ikke at medtage 300 brugere, for at en prøveversion kan lykkes.

Du kan hente prøveversionen fra en af følgende kilder:

- Den [SharePoint Syntex produktside](https://www.microsoft.com/microsoft-365/enterprise/sharepoint-syntex?activetab=pivot:overviewtab)

- [Microsoft 365 Administration](https://admin.microsoft.com)
    1. Log på [Microsoft 365 Administration](https://admin.microsoft.com).
    2. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">**BillingPurchase**</a> >  Services.
    3. Rul ned **til sektionen Tilføjelser** .
    4. På SharePoint Syntex du vælge **Detaljer**.
    5. Vælg **Hent gratis prøveversion**.
    6. Følg de resterende trin i guiden for at bekræfte prøveabonnementet.

Du skal være global Microsoft 365 eller faktureringsadministrator for at aktivere en prøveversion.

### <a name="who-should-be-involved-in-a-trial"></a>Who skal være involveret i et prøveabonnement

|Rolle|Aktivitet|
|---|---|
|Microsoft 365 global administrator eller faktureringsadministrator|Aktivér prøveversionen, og tildel licenser|
|Microsoft 365 global administrator eller SharePoint administrator|Konfigurere SharePoint Syntex og oprette indholdscenter|
|Virksomhedsbrugere|Modelopbygning og test|

### <a name="before-you-activate-a-trial"></a>Før du aktiverer en prøveversion

For at planlægge en SharePoint Syntex prøveversion skal du overveje følgende faktorer:

- De mest meningsfulde test gennemføres med scenarier og data i den "virkelige verden".
- Du kan kun aktivere en SharePoint Syntex én gang pr. lejer.

En test- eller demolejer kan bruges som en "tør kørsel" til at gennemgå aktiveringstrinnene og de administrative kontrolfunktioner. Men det er sandsynligvis bedst at evaluere modelopbygning på en produktionslejer.

Hvis du vil maksimere værdien af en prøveversion på en produktionslejer, er planlægning og forretningsmæssig aftale afgørende. Du bør involvere dig i et eller flere forretningsområder for at identificere tre til seks brugstilfælde, som potentielt kan behandles af SharePoint Syntex. Disse use cases skal:

- Inkluder scenarier, der kan løses enten ved hjælp af formularbehandling eller dokumentforståelsesmodel.
- Have en klar forståelse af formålet med eventuelle udpakkede metadata; f.eks. kan du få vist formatering eller automatisering ved hjælp Power Automate. Selvom SharePoint Syntex fokuserer på at klassificere dokumenter og udtrække metadata, er værdien til at sætte tal på, hvad metadataene giver mulighed for.
- Være baseret på et defineret sæt data; For eksempel bestemte SharePoint eller biblioteker. En almindelig årsag til SharePoint Syntex er, at generelle formålsmodeller kan anvendes på tværs af hele organisationens indhold. En mere præcis visning er, at modeller er udviklet til at hjælpe med at løse specifikke forretningsmæssige problemer på målrettede placeringer.

Alle disse use cases passer muligvis ikke godt til SharePoint Syntex. Målet med et prøveabonnement er ikke at bevise, at SharePoint Syntex vil passe ind i alle scenarierne. I stedet bør prøveversionen hjælpe dig med bedre at forstå produktets værdi.

For hver af de planlagte use cases skal du identificere brugere, der er emneeksperter i det relaterede indhold eller den relaterede proces. Oprettelse af SharePoint Syntex er fokuseret på domæneeksperter i indholdet i stedet for på it-fagfolk eller udviklerressourcer.

## <a name="activate-a-trial"></a>Aktivér et prøveabonnement

Når du starter et prøveabonnement, skal du:

- Tildel licenser til de relevante brugere.
- Udfør [yderligere konfiguration af SharePoint Syntex](set-up-content-understanding.md).
  - Det kan være en [ide at oprette flere indholdscentre](create-a-content-center.md).

Når prøveperioden er aktiveret, kan du oprette modeller og procesfiler. Se [vejledning til oprettelse af modeller](create-a-content-center.md).

## <a name="during-a-trial"></a>Under en prøveversion

Prøveperioder er begrænsede, så det er bedst først at fokusere på, om SharePoint Syntex-modeller kan klassificere dokumenter og udtrække metadata for de definerede use cases. Når prøveperioden er slut, kan du evaluere, hvordan metadataene kan udnyttes.

## <a name="after-a-trial"></a>Efter en prøveversion

Baseret på resultatet af prøveversionen kan du beslutte, om du vil fortsætte med at bruge SharePoint Syntex.

### <a name="proceed-to-production-use"></a>Fortsæt til produktionsbrug

For at sikre kontinuitet i tjenesten skal du købe det nødvendige antal licenser og tildele disse licenser til brugerne. Prøvebrugere, der ikke har en fuld licens i slutningen af prøveperioden, vil ikke kunne udnytte deres SharePoint Syntex.

Du skal muligvis anslå din forventede brug af formularer og planlægge for det forventede beløb af AI Builder-kredit. Du kan få hjælp under [Anslå den AI Builder-kapacitet, der passer til dine ønsker](https://powerapps.microsoft.com/ai-builder-calculator/).

### <a name="dont-proceed-to-production-use"></a>Fortsæt ikke til produktionsbrug

Hvis du ikke køber licenser efter prøveversionen:

- Du vil ikke kunne oprette nye modeller.
- Biblioteker, der kørte modeller, klassificerer ikke længere automatisk filer eller udtrækker modeller.
- Tidligere klassificerede filer eller udpakkede metadata påvirkes ikke.
- Indholdscenter og eventuelle dokumentforståelsesmodeller slettes ikke automatisk. Disse kan stadig bruges, hvis du beslutter dig for at købe licenser på et senere tidspunkt.
- Modeller til behandling af formularer gemmes i forekomsten af Power Platform-standardmiljøet i Dataverse (tidligere kaldet Common Data Service [CDS]). Disse kan bruges sammen med fremtidige licenser til SharePoint Syntex eller med AI Builder-funktioner i Power-platformen.

## <a name="see-also"></a>Se også

[Microsoft SharePoint Syntex implementering: Introduktion](adoption-getstarted.md)
