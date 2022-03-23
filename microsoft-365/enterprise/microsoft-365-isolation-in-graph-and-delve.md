---
title: Microsoft 365 lejerisolation i Microsoft Graph og Delve
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
description: I denne artikel kan du finde en forklaring på, Microsoft 365 lejerisolation fungerer i Office Graph og Delve.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 966f02726a2cce18e30e4d5bc7ab0beb5db51a29
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/16/2021
ms.locfileid: "63591587"
---
# <a name="microsoft-365-tenant-isolation-in-the-microsoft-graph-and-delve"></a>Microsoft 365 lejerisolation i Microsoft Graph og Delve

## <a name="tenant-isolation-in-the-microsoft-graph"></a>Lejerisolation i Microsoft-Graph

Aktiviteten [Microsoft Graph](https://developer.microsoft.com/graph) modeller i Microsoft 365, herunder Exchange Online, SharePoint Online, Yammer, Skype for Business, Azure Active Directory , og mere, og i eksterne tjenester, f.eks Microsoft-tjenester tjenester eller tredjepartstjenester. Microsoft Graph-komponenter bruges overalt Microsoft 365. Microsofts Graph repræsenterer en samling af indhold og aktiviteter, og relationerne mellem dem, der sker på tværs Office pakke. It uses sophisticated machine learning techniques to connect people to the relevant content, conversations and people around them. Lejerindekset i SharePoint Online har f.eks. et Microsoft Graph-indeks, der bruges til at behandle Delve-forespørgsler. Analysebehandlingsprogrammet i SharePoint Online bruges til at lagre signaler og beregne indsigter, og Exchange Online beregner hver brugers modtagercache som input til lejeranalyse.

Microsofts Graph indeholder oplysninger om virksomhedsobjekter, f.eks. personer og dokumenter, samt relationerne og interaktionerne mellem disse objekter. Relationer og interaktioner vises som *kanter*. Microsofts Graph er segmenteret efter lejer, så kanterne kun kan findes *mellem noder* i samme lejer. En node er en enhed med en URI (Uniform Resource Identifier), en *nodetype* , en adgangskontrolliste og et sæt facetter, der indeholder *metadata* og kanter. Hver node har tilknyttede metadata og kanter, *arrangeret i facetter* som i den fælles vidensmodel. *Metadata* navngives egenskaber, der gemmes på en node, som kan bruges til søgning, filtrering eller analyse i Microsoft Graph. En *facet* er en logisk samling af metadata og kanter på en node. Hver facet beskriver ét aspekt af en node. 

Microsofts Graph henter ikke alle dataene til et enkelt lager; i stedet gemmes metadata og relationer om data, der findes andre steder. Microsofts Graph består af flere datalagre og behandlingskomponenter:

- Tenant Graph Store masselager, der er optimeret til effektiv analyse.
- Active Content Cache giver hurtig tilfældig adgang til aktiv node og kanter, der kan drive brugeroplevelser.
- Inputouteren giver komponenter internt og eksternt besked om ændringer i lejerdiagrammet.

Analyser inden for hver arbejdsmængde udleder indsigter, der er relevante for beregninger for hele lejeren, og skubber dem til lejerdiagrammet. Årsager til lejeranalyse over al aktivitet i et leje for at give indsigt i adfærdsmønstre. Eksempel: Exchange Online beregner modtagercachen for hver bruger med analyser, der årsagen er effektiv over hver brugers postkasse. Disse analyser pr. bruger frembringer et sæt *RecipientCache-kanter* på hver person, som igen er sendt videre til lejerdiagrammet. Dette holder så meget af analyserne, der behandles, så tæt på kildedataene som muligt.

## <a name="tenant-isolation-in-delve"></a>Lejerisolation i Delve

Som nævnt tidligere gør Microsoft Graph brug af oplevelser, der gør det lettere for folk at opdage og samarbejde om aktuelle aktiviteter i deres virksomhed, og giver en enhedscentreret platform til analyse til begrundelse for indhold og aktivitet på tværs af arbejdsbelastninger og mere end Microsoft 365. Delve er den første oplevelse, der leveres af Microsoft Graph.
Delve er en Microsoft 365 weboplevelse, der viser indhold fra Microsoft 365 og Yammer Enterprise til Microsoft 365 brugere via Microsoft Graph. Weboplevelsen viser data som forskellige tavler, hver med et bestemt emne, f.eks. Populære *omkring mig* eller *Ændret af mig*. Hver tavle består af flere dokumentkort, der viser oversigtstekst og et billede fra dokumentet. Kortet giver brugerne mulighed for at gøre ting som f.eks. at åbne dokumentet Yammer en side i dokumentet. Der er en side for hver person i en Microsoft 365-lejer, der viser de mest relevante dokumenter for denne person, og ikoner, der kan fremkalde Exchange Online eller Skype for Business for at interagere med den pågældende person. Da Delve er baseret på Microsoft Graph API, er den bundet af den lejerbaserede isolation af den pågældende API.