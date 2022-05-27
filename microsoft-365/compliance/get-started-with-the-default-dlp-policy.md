---
title: Kom i gang med DLP-standardpolitikken
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
description: Få mere at vide om, hvordan du bruger rapporten til at tilpasse din organisations standardpolitik til forebyggelse af datatab .
ms.openlocfilehash: 893aae6dfbc4e5c9fcf48a8eec53694352ead4f2
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753446"
---
# <a name="get-started-with-the-default-dlp-policy"></a>Kom i gang med DLP-standardpolitikken

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Før du selv opretter din første DLP-politik (Microsoft Purview Forebyggelse af datatab), hjælper DLP med at beskytte dine følsomme oplysninger med en standardpolitik. Denne standardpolitik og dens anbefaling (vist nedenfor) hjælper med at beskytte dit følsomme indhold ved at give dig besked, når mail eller dokumenter, der indeholder et kreditkortnummer, blev delt med en person uden for din organisation. Du kan se denne anbefaling **på startsiden** for Microsoft Purview-compliance-portal. 
  
Du kan bruge denne widget til hurtigt at få vist, hvornår og hvor mange følsomme oplysninger der blev delt, og derefter tilpasse standardpolitikken for forebyggelse af dataforbrug med blot et klik eller to. Du kan også redigere standard-DLP-politikken når som helst, fordi den kan tilpasses fuldt ud. Bemærk, at hvis du ikke kan se anbefalingen i starten, kan du prøve at klikke på **+Mere** nederst i sektionen **Anbefalet for dig** . 
  
![Widget med navnet Beskyt delt indhold yderligere.](../media/2bae6dbc-cc92-4f35-b54c-c36e60226b5b.png)
  
## <a name="view-the-report-and-refine-the-default-dlp-policy"></a>Få vist rapporten, og afgræns standardpolitikken for DLP

Når widgetten viser dig, at brugerne har delt følsomme oplysninger med personer uden for din organisation, skal du vælge **Afgræns DLP-politik** nederst. 
  
Den detaljerede rapport viser dig, hvornår og hvor meget indhold, der indeholder kreditkortnumre, der er blevet delt i løbet af de seneste 30 dage. Bemærk, at det kan tage op til 48 timer, før regelforekomster vises i widgetten.
  
Standard-DLP-politikken for at beskytte følsomme oplysninger:
  
- Registrerer, når indhold i Exchange, SharePoint og OneDrive, der indeholder mindst ét kreditkortnummer, deles med personer uden for din organisation.
    
- Viser et politiktip og sender en mail til brugerne, når de forsøger at dele disse følsomme oplysninger med personer uden for din organisation. Du kan få flere oplysninger om disse indstillinger under [Send mailmeddelelser og få vist politiktip til DLP-politikker](use-notifications-and-policy-tips.md).
    
- Genererer detaljerede aktivitetsrapporter, så du kan spore ting som f.eks. hvem der delte indholdet med personer uden for din organisation, og hvornår de gjorde det. Du kan bruge [DLP-rapporter](view-the-dlp-reports.md) og [overvågningslogdata](search-the-audit-log-in-security-and-compliance.md) (hvor **Aktivitet** = **DLP**) til at se disse oplysninger.
    
Hvis du hurtigt vil tilpasse standardpolitikken for forebyggelse af data forebyggelse, kan du vælge at have den:
  
- Sender dig en mail med en hændelsesrapport, når brugerne deler disse følsomme oplysninger med personer uden for din organisation.
    
- Føj andre brugere til rapporten over mailhændelser.
    
- Bloker adgang til det indhold, der indeholder de følsomme oplysninger, men giv brugeren tilladelse til at tilsidesætte og dele eller sende, hvis brugeren har brug for det.
    
Du kan få flere oplysninger om hændelsesrapporter eller begrænsning af adgang under [Reference til forebyggelse af datatab](data-loss-prevention-policies.md).
  
Hvis du vil ændre disse indstillinger senere, kan du når som helst redigere DLP-standardpolitikken – se næste afsnit.
  
![Indstillinger for widget med navnet Beskyt delt indhold yderligere.](../media/dad30a84-2715-4c0a-a5c5-44d85492363e.png)
  
## <a name="edit-the-default-dlp-policy"></a>Rediger DLP-standardpolitikken

Denne politik hedder **Standard-DLP-politik** og vises under **Forebyggelse af datatab** på siden **Politik** i Microsoft Purview-compliance-portal. 
  
Denne politik kan tilpasses fuldt ud, det samme som enhver DLP-politik, som du selv opretter fra bunden. Du kan også slå politikken fra eller slette den, så brugerne ikke længere modtager politiktip eller mailmeddelelser.
  
![DLP-politik med navnet Standard-DLP-politik.](../media/260731e8-4d57-4c98-abec-07b052ec48d5.png)
  
## <a name="when-the-widget-does-and-does-not-appear"></a>Når widgetten gør og ikke vises

Widgetten **med navnet Yderligere beskyttelse af delt indhold** vises i afsnittet **Anbefalet til dig** på siden **Startside** for Microsoft Purview-compliance-portal. 
  
Denne widget vises kun, når:
  
- Der er ingen politikker til forebyggelse af datatab i Microsoft Purview-compliance-portal eller Exchange Administration. Denne widget er beregnet til at hjælpe dig med at komme i gang med DLP, så den vises ikke, hvis du allerede har DLP-politikker.
    
- Indhold, der indeholder mindst ét kreditkort, er blevet delt med en person uden for din organisation inden for de seneste 30 dage.
    
Bemærk, at det kan tage op til 48 timer, før regelforekomster er tilgængelige for widgetten, så når følsomme oplysninger, der deles eksternt, er registreret, kan det tage op til to dage, før anbefalingen vises.
  
Når du har brugt widgetten til at tilpasse DLP-standardpolitikken, forsvinder **widgetten til** sidst fra startsiden. 
  

