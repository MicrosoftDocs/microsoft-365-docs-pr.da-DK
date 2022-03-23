---
title: Lejerisolation i Microsoft 365 søgning
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: I denne artikel skal du finde en forklaring på, hvordan lejerisolation fungerer for separate lejerdata i Microsoft 365 Søg.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3416afdeceaa7000b516ec89b4a2a1e59d8708d0
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/16/2021
ms.locfileid: "63589714"
---
# <a name="tenant-isolation-in-microsoft-365-search"></a>Lejerisolation i Microsoft 365 søgning

SharePoint Onlinesøgning anvender en lejersepareringsmodel, der afbalancerer effektiviteten af delte datastrukturer med beskyttelse mod lækage af oplysninger mellem lejere. Med denne model forhindrer vi søgefunktionerne i at:

- Returnere forespørgselsresultater, der indeholder dokumenter fra andre lejere
- Når der vises tilstrækkelige oplysninger i forespørgselsresultater, kan en erfaren bruger udlede oplysninger om andre lejere
- Viser skema eller indstillinger fra en anden lejer
- Blanding af analyser, der behandler oplysninger mellem lejere eller gemmer, resulterer i den forkerte lejer
- Bruge ordbogsposter fra en anden lejer

For hver type lejerdata bruger vi et eller flere lag beskyttelse i koden for at forhindre utilsigtet lækage af oplysninger. De mest kritiske data har de fleste beskyttelseslag for at sikre, at en enkelt fejl ikke medfører lækage af faktiske eller opfattede oplysninger.

## <a name="tenant-separation-for-the-search-index"></a>Lejerseparation for søgeindekset

Søgeindekset gemmes på disken på de servere, der hoster indekskomponenterne, og lejerne deler indeksfilerne. En lejers indekserede dokumenter er kun synlige for forespørgsler for den pågældende lejer. Tre uafhængige mekanismer forhindrer lækage af oplysninger:

- Filtrering af lejer-id
- Præfiks for lejer-id
- ACL-kontroller

Alle tre mekanismer vil mislykkes, for at Søg kan returnere dokumenter til den forkerte lejer.

## <a name="tenant-id-filtering-and-tenant-id-term-prefixing"></a>Lejer-id-filtrering og lejer-id-præfiks

Søgepræfikser hvert ord, der er indekseret i fuldtekstindekset med lejer-id'et. Når f.eks. udtrykket "*foo*" er indekseret for en lejer med et id på "*123*", er indtastningen i indekset i fuld tekst "*123foo"*.

Hver forespørgsel konverteres til at medtage lejer-id'et ved hjælp af en proces kaldet filtrering af lejer-id. For eksempel konverteres forespørgslen "*foo*" til "<*guid*>. *foo* AND *tenantID*:<*guid*>", hvor <*guid*> repræsenterer lejeren, der udfører forespørgslen. Denne forespørgselskonvertering forekommer inden for hver indeksnode, og hverken forespørgsel eller indholdsbehandling kan påvirke den. Da lejer-id'et føjes til hver forespørgsel, kan hyppigheden af et ord i andre lejere ikke udledes ved at se på den bedste rangering for match i én lejer.

Præfiks for lejer-id forekommer kun i indekset med hele teksten. Feltsøgninger, f.eks. "*titel:foo*", skal gå til et søgeindeks, hvor begreber ikke er præfikset af lejer-id. I stedet har feltsøgninger præfiks med feltnavnet. For eksempel konverteres forespørgslen "*title:foo*" til "*fields.title:foo AND fields.tenantID*:<*guid*>." Da hyppigheden af et ord ikke påvirker rangeringen af hits i det tilsigtende søgeindeks, er der ikke behov for lejerseparation ved hjælp af præfiksering af ord. For en feltsøgning som f.eks. "*titel:foo*" afhænger lejerens indholdsseparation af lejer-id'ets filtrering efter forespørgselskonvertering.

## <a name="document-access-control-list-checks"></a>Kontrollistekontroller for dokumentadgang

Søgning styrer adgangen til dokumenter via ACL'er, der er gemt i søgeindekset. Hvert element er indekseret med et sæt ord i et specielt ACL-felt. ACL-feltet indeholder ét ord pr. gruppe eller bruger, der kan få vist dokumentet. Hver forespørgsel udvides med en liste over adgangskontrolpostvilkår (ACE), én for hver gruppe, som den godkendte bruger tilhører.

For eksempel en forespørgsel som "<*guid*>. *foo AND tenantID*:<*guid*>" bliver: "<*guid*>. *foo AND tenantID*:<*guidAND*>  (*docACL:*<*ace1OR*>  *docACL*:<*ace2OR*>  *docACL*:<*ace3*> *...*)"

Da bruger- og gruppe-id'er og dermed ACEs er entydige, giver dette et ekstra sikkerhedsniveau mellem lejere til dokumenter, som kun er synlige for nogle brugere. Det samme er tilfældet med det særlige "Alle undtagen eksterne brugere", som giver adgang til almindelige brugere i lejeren. Men da ACEs for "Alle" er ens for alle lejere, afhænger lejerseparation for offentlige dokumenter af filtrering af lejer-id. Afvisning af ACEs understøttes også. Forespørgselsudvidelsen tilføjer en delsætning, der fjerner et dokument fra resultatet, når der er match med en afvisning af ACE.

I Exchange Online er indekset partitioneret på postkasse-id for den enkelte brugers postkasser i stedet for lejer-id (abonnements-id) som i SharePoint Online. Partitioneringsmekanismen er den samme som SharePoint Online, men der er ingen ACL-filtrering.
