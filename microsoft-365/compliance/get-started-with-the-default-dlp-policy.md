---
title: Introduktion til DLP-standardpolitikken
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: e0ada764-6422-4b44-9472-513bed04837b
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du bruger rapporten til at forbedre organisationens standardpolitik for forebyggelse af datatab (DLP).
ms.openlocfilehash: 0e63648f78fd5adf2b0a354fa1a26abae4561ba8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589129"
---
# <a name="get-started-with-the-default-dlp-policy"></a>Introduktion til DLP-standardpolitikken

Før du opretter din første politik til forebyggelse af datatab (DLP), hjælper DLP med at beskytte dine følsomme oplysninger med en standardpolitik. Denne standardpolitik og dens anbefaling (vist nedenfor) hjælper med at beskytte dit følsomme indhold ved at give dig besked, når mails eller dokumenter, der indeholder et kreditkortnummer, er blevet delt med en person uden for organisationen. Du får vist denne anbefaling på **startsiden i** Security &amp; Compliance Center. 
  
Du kan bruge denne widget til hurtigt at få vist, hvornår og hvor mange følsomme oplysninger, der blev delt, og derefter tilpasse DLP-standardpolitikken med et enkelt klik eller to. Du kan også når som helst redigere DLP-standardpolitikken, fordi den kan tilpasses fuldt ud. Bemærk, at hvis du ikke kan se anbefalingen i første omgang, kan du prøve at klikke **på +** Mere nederst **i afsnittet Anbefalet til** dig. 
  
![Widget med navnet Yderligere beskyttelse af delt indhold.](../media/2bae6dbc-cc92-4f35-b54c-c36e60226b5b.png)
  
## <a name="view-the-report-and-refine-the-default-dlp-policy"></a>Få vist rapporten, og tilpas DLP-standardpolitikken

Når widgetten viser dig, at brugere har delt følsomme oplysninger med personer uden for organisationen, skal du **vælge Indskrænk DLP-politik** nederst. 
  
Den detaljerede rapport viser dig, hvornår og hvor meget indhold, der indeholder kreditkortnumre, der er blevet delt inden for de seneste 30 dage. Bemærk, at det kan tage op til 48 timer, før reglen matches vises i widgetten.
  
For at beskytte de følsomme oplysninger skal du bruge DLP-standardpolitikken:
  
- Registrerer, når indhold i Exchange, SharePoint og OneDrive, der indeholder mindst ét kreditkortnummer, deles med personer uden for organisationen.
    
- Viser et politiktip og sender en mail til brugerne, når de forsøger at dele disse følsomme oplysninger med personer uden for organisationen. Få mere at vide om disse indstillinger under [Send mailbeskeder, og vis politiktip til DLP-politikker](use-notifications-and-policy-tips.md).
    
- Genererer detaljerede aktivitetsrapporter, så du kan spore ting som, hvem der har delt indholdet med personer uden for organisationen, og hvornår de har gjort det. Du kan bruge [DLP-rapporter og](view-the-dlp-reports.md) data [fra overvågningsloggen](search-the-audit-log-in-security-and-compliance.md) (hvor **ActivityDLP** = ) til at få vist disse oplysninger.
    
Hvis du hurtigt vil afgrænse DLP-standardpolitikken, kan du vælge at få den:
  
- Send dig en hændelsesrapport via mail, når brugere deler disse følsomme oplysninger med personer uden for organisationen.
    
- Føj andre brugere til rapporten over mailhændelser.
    
- Bloker adgang til det indhold, der indeholder de følsomme oplysninger, men tillad brugeren at tilsidesætte og dele eller sende, hvis der er behov for det.
    
Du kan finde flere oplysninger om hændelsesrapporter eller begrænsning af adgangen under [Reference til forebyggelse af datatab](data-loss-prevention-policies.md).
  
Hvis du vil ændre disse indstillinger senere, kan du når som helst redigere DLP-standardpolitikken – se næste afsnit.
  
![Indstillinger for widget med navnet Yderligere beskyttelse af delt indhold.](../media/dad30a84-2715-4c0a-a5c5-44d85492363e.png)
  
## <a name="edit-the-default-dlp-policy"></a>Rediger DLP-standardpolitikken

Denne politik har navnet **Standard DLP-politik** og vises under **Forebyggelse af datatab** på siden Politik i  Security &amp; Compliance Center. 
  
Denne politik kan tilpasses fuldt ud, det samme som enhver DLP-politik, du opretter dig selv fra bunden. Du kan også deaktivere eller slette politikken, så dine brugere ikke længere modtager politiktip eller mailmeddelelser.
  
![DLP-politik med navnet Standard DLP-politik.](../media/260731e8-4d57-4c98-abec-07b052ec48d5.png)
  
## <a name="when-the-widget-does-and-does-not-appear"></a>Når widgetten gør og ikke vises

Widgetten med **navnet Yderligere beskyt delt indhold** vises i **afsnittet Anbefalet** til dig på **startsiden** i Security &amp; Compliance Center. 
  
Denne widget vises kun, når:
  
- Der er ingen politikker til forebyggelse af datatab i Security &amp; Compliance Center eller Exchange Administration. Denne widget er beregnet til at hjælpe dig i gang med DLP, så den vises ikke, hvis du allerede har DLP-politikker.
    
- Indhold, der indeholder mindst ét kreditkort, er blevet delt med en person uden for organisationen inden for de seneste 30 dage.
    
Bemærk, at det kan tage op til 48 timer, før reglen er tilgængelig for widgetten, så når følsomme oplysninger, der deles eksternt, kan det tage op til to dage, før anbefalingen vises.
  
Når du har brugt widgetten til at afgrænse DLP-standardpolitikken, forsvinder widgetten fra **startsiden** . 
  

