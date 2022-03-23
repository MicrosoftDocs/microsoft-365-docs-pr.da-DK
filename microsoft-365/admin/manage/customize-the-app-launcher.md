---
title: Føj brugerdefinerede felter til appstarteren
f1.keywords:
- CSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 1136115a-75af-4497-b693-640c4ce70bc6
description: Opret hurtige links til dine mails, dokumenter, apps, SharePoint websteder, eksterne websteder og andre ressourcer ved at føje brugerdefinerede felter til appstarteren.
ms.openlocfilehash: 31121df0e1af6b8fc2be1e61ba7e0cd0714affa2
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/09/2022
ms.locfileid: "63588103"
---
# <a name="add-custom-tiles-to-the-app-launcher"></a>Føj brugerdefinerede felter til appstarteren

I Microsoft 365 kan du hurtigt og nemt få adgang til dine mails, kalendere, dokumenter og apps ved hjælp af appstarteren (få [mere at vide](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a)). Disse er apps, du får med Microsoft 365 samt brugerdefinerede apps, som du tilføjer fra [SharePoint Store](https://support.microsoft.com/office/dd98e50e-d3db-4ecb-9bb7-82b189822d43) eller [Azure AD](/previous-versions/office/office-365-api/).
  
Du kan føje dine egne brugerdefinerede felter til appstarteren, der peger på SharePoint, eksterne websteder, ældre apps og meget mere. Det brugerdefinerede felt vises under **Alle apps i** appstarteren, men du kan fastgøre den til **Home-appsene** og bede dine brugere om at gøre det samme. Det gør det nemt at finde de relevante websteder, apps og ressourcer, der skal til for at udføre dit arbejde. I eksemplet herunder bruges et brugerdefineret felt med navnet "Contoso-portal" til at få adgang til en SharePoint intranetwebsted. 
  
![Appst starter.](../../media/7acc06cc-ac7a-4c6e-8ea7-81570a5bdbab.png)
  
## <a name="add-a-custom-tile-to-the-app-launcher"></a>Føj et brugerdefineret felt til appstarteren

1. Log på Administration som global administrator,  >  gå til Indstillinger **Ellerg Indstillinger**, og vælg **fanen Organisationsprofil**.
    
2. På fanen **Organisationsprofil** skal du vælge **felter for brugerdefinerede appst startere**.
  
3. Vælg **Tilføj et brugerdefineret felt**. 
  
4. Angiv et **Feltnavn** for det nye felt. Navnet vises i feltet. 
    
5. Angiv en **URL-adresse** til webstedet for feltet. Dette er den placering, brugerne skal hen, når de vælger feltet i appstarteren. Brug HTTPS i URL-adressen.

    > [!TIP]
    > Hvis du opretter et felt til et SharePoint websted, skal du gå til webstedet, kopiere URL-adressen og indsætte den her. URL-adressen til dit standardteamwebsted ser sådan ud: `https://<company_name>.sharepoint.com` 
  
6. Angiv en **URL-adresse til** billedet for feltet. Billedet vises på siden Mine apps og i appstarteren.

    > [!TIP]
    > Billedet skal være 60 x 60 pixel og være tilgængeligt for alle i organisationen uden at kræve godkendelse.

7. Angiv **en** Beskrivelse for feltet. Du får vist dette, når du vælger feltet på siden Mine apps og vælger **Appoplysninger**. 
  
8. Vælg **Gem ændringer** for at oprette det brugerdefinerede felt. 
    
    Dit brugerdefinerede felt vises inden for de næste 24 timer i appstarteren på **fanen Alle** for dig og dine brugere. 

    > [!NOTE]
    > Hvis du ikke kan se det brugerdefinerede felt, der blev oprettet i de forrige trin, skal du kontrollere, at du har en Exchange Online-postkasse tildelt til dig, og at du har logget på din postkasse mindst én gang. Disse trin er nødvendige for brugerdefinerede felter i Microsoft 365. 
  
## <a name="edit-or-delete-a-custom-tile"></a>Rediger eller slet et brugerdefineret felt

1. I Administration skal du gå **til Indstillinger** >  **Org Indstillinger** >  **Organiseringsprofil**.
    
2. På siden **Organisationsprofil** skal du gå til felter for brugerdefineret **appst** starter, Hvis du vælger de tre prik ud for dit Brugerdefinerede felt og vælger **Rediger brugerdefineret felt**.

3. Opdater **Feltnavn**, **URL-adresse**, **Beskrivelse** eller **URL-adresse** til billede for det brugerdefinerede felt (se Føj et [brugerdefineret felt til appstarteren](#add-a-custom-tile-to-the-app-launcher)).
    
4. Vælg **Opdater** \> **Luk**. 
    
Hvis du vil slette et brugerdefineret felt, **skal du markere** feltet i vinduet Brugerdefinerede felter og **vælge Fjern fliseSlette** > . 
  
## <a name="next-steps"></a>Næste trin

 Hvis du vil tilpasse udseendet og Microsoft 365 til at matche din organisations brand, skal du [se Tilpas Microsoft 365 tema](../setup/customize-your-organization-theme.md).

## <a name="related-content"></a>Relateret indhold

[Fastgør apps til dine brugeres appstarter](pin-apps-to-app-launcher.md) (artikel)\
[Opgrader Microsoft 365 til virksomhedsbrugere til den nyeste Office klient](../setup/upgrade-users-to-latest-office-client.md) (artikel)\
[Administrere tilføjelser i Administration](../manage/manage-addins-in-the-admin-center.md) (artikel)
