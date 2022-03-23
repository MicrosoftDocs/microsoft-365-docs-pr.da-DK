---
title: Isolerede team til et hemmelig projekt for Contoso Corporation
f1.keywords:
- NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.date: 08/14/2020
audience: ITPro
ms.topic: overview
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: Ent_Architecture
description: 'Oversigt: Sådan brugte Contoso et team med sikkerhedsisolation til et tophemmeligt projekt til at udvikle en ny pakke af produkter og tjenester.'
ms.openlocfilehash: 5b6bc72a6476301cf3239aeb7f68486f15ebbac8
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/10/2022
ms.locfileid: "63588643"
---
# <a name="isolated-team-for-a-top-secret-project-of-the-contoso-corporation"></a>Isolerede team til et hemmelig projekt for Contoso Corporation

Efter en leder uden for ledelsen bestilte Contosos administrerende direktør udviklingen af en ny pakke med produkter og tjenester, der kan fordoble Contosos overskud i de næste fem år. Det mest hemmelige projekt til udvikling af forretnings-, teknik- og markedsplanen blev navngivet **Project 2X** og nøglemedarbejdere på tværs af virksomheden blev ansættet. 

Tidslinjerne for forskning og udvikling var tæt, hvilket betød, at samarbejde skulle være effektivt og sørge for sikre møder, igangværende samtaler og fillagring.

De resulterende leverancer for Project 2X var forretningsplaner, produkt- og tekniske specifikationer samt marketingmaterialer og tidsplaner i form af Word-, Excel- og PowerPoint-filer. 

På grund af deres følsomme karakter var adgang til disse filer:

- Begrænset til Project 2X-teammedlemmer og seniorledelse.
- Krypteret og beskyttet med tilladelser til kun at tillade adgang for Project 2X-teammedlemmer og seniorledelse, også selvom filerne blev distribueret uden for deres sikrede mapper.

Contoso-it-medarbejdere brugte et [team med sikkerhedsisolation](secure-teams-security-isolation.md) til Project 2X og disse trin.

## <a name="step-1-created-a-private-team"></a>Trin 1: Oprettet et privat team

For det første konfigurerede Contoso-it-administratorer den anbefalede beskyttelse SharePoint til teamets underliggende websted for [SharePoint adgangspolitikker](../security/office-365-security/sharepoint-file-access-policies.md).

Derefter oprettede en it-administrator for Contoso et nyt privat team ved navn Project 2X og tilføjede brugerkontiene for Project 2X-medarbejdere som medlemmer. De har også konfigureret teamet, så kun Project 2X-teamejere kan oprette private kanaler.

Du kan få mere at vide om [konfigurationen under Opret et privat team](secure-teams-security-isolation.md#create-a-private-team).

## <a name="step-2-created-a-sensitivity-label-for-the-project-2x-team"></a>Trin 2: Oprettet et følsomhedsmærkat til Project 2X-teamet

Contoso-administratorer har oprettet en ny følsomhedsmærkat med **navnet Project 2X**, som:

- Kryptering aktiveret.
- Tilladelse Co-Author tilladelser for Project 2X Microsoft 365 gruppe.
- Tilladte Viewer-tilladelser for gruppen Seniorledelse.
- Blokeret adgang til enheder, der ikke er administrerede.

Filer i sektionen **Dokumenter** på det underliggende Project 2X SharePoint websted var beskyttet af:

- Webstedstilladelserne, som kun giver fuld tilladelse til medlemmer af gruppen Project 2X Microsoft 365 og læsetilladelser til seniorledelsesgruppen.
- 2X Project 2X-følsomhedsetiketten med kryptering og tilladelser, der gælder for filen, hvis den flyttes eller kopieres fra webstedet.

Du kan få mere at vide om konfiguration [under Opret en følsomhedsmærkat](secure-teams-security-isolation.md#create-a-sensitivity-label).

## <a name="step-3-configured-the-underlying-sharepoint-site"></a>Trin 3: Konfigureret den underliggende SharePoint websted

For det første konfigurerede Contoso-it-administratorer den anbefalede beskyttelse SharePoint til teamets underliggende websted for [SharePoint adgangspolitikker](../security/office-365-security/sharepoint-file-access-policies.md).

Derefter konfigurerede de yderligere tilladelsesindstillinger for webstedet:

- Sådan forhindrer Project 2X-gruppemedlemmer i at dele adgang til webstedet. Du kan finde flere oplysninger om [konfiguration SharePoint indstillinger for et team med sikkerhedsisolation](secure-teams-security-isolation.md#sharepoint-settings).
- Læsetilladelser for gruppen Seniorledelse.

Derefter konfigurerede de yderligere tilladelsesindstillinger for webstedet for at forhindre Project 2X-gruppemedlemmer i at dele adgang til webstedet. 

Da private kanaler til Project 2X blev oprettet, deaktiverede gruppeejeren gæstedeling og indstillede standarddelingslinket til **værdien Bestemte** personer.

Her er den resulterende konfiguration af Project 2X-teamet med sikkerhedsisolation.

![Den resulterende konfiguration af Project 2X-teamet.](../media/contoso-team-for-top-secret-project.png)

 ## <a name="step-4-trained-project-2x-team-members"></a>Trin 4: Uddannet Project 2X-teammedlemmer

Contoso-sikkerhedsmedarbejdere uddannede Project 2X-teammedlemmer i et obligatorisk kursus, hvor de blev flyttet gennem:

- Sådan får du adgang til det nye Project 2X-team, bruger møder og chats, og hvordan du samarbejder om teamfiler.
- Sådan opretter du nye filer i teamet og overfører nye filer, der er oprettet lokalt.
- Sådan etikette du filer med Project 2X-følsomhedsmærkat.
- En demonstration af, hvordan Project 2X-etiket beskytter en fil, selv når den forlader teamet.

Det endelige resultat var et sikkert miljø, hvor Project 2X-teammedlemmer samarbejdede i et sikkert miljø til chatsamtaler, møder og filer.

Her er et eksempel på en fil, der er gemt i den underliggende Project 2X-websted med Project 2X-følsomhedsmærkat tildelt.

![Et eksempel på en fil, der er gemt på det underliggende Project 2X-websted.](../media/contoso-team-for-top-secret-project-example.png)

I et par tilfælde har Project 2X-teammedlemmer hentet filer, der er beskyttet af Project 2X-navnet, til et lokalt drev til offlinearbejde. 

Men når de er blevet bedt om legitimationsoplysninger, da de åbnede dem, fandt de deres fejl og slettede dem.

På grund af samarbejdsmiljøet i Teams og sikkerhedsfunktionerne i Microsoft 365 blev oplysningerne i Project 2X hemmelig i hele projektet. Contoso annoncerede sine planer og er i gang med at udrulle de nye produkter og tjenester til glæde for sine kunder og investorer og konkurrenterne.

## <a name="next-step"></a>Næste trin

[Installér et team med sikkerhedsisolation](secure-teams-security-isolation.md) i organisationen.

