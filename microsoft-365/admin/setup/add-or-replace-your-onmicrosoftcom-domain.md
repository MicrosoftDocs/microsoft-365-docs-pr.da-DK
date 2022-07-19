---
title: Tilføj og erstat dit onmicrosoft.com reservedomæne i Microsoft 365
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365_Setup
- Adm_O365
- Adm_TOC
ms.custom:
- TopSMBIssues
- SaRA
- MSStore_Link
- okr_smb
- business_assist
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: ''
description: Få mere at vide om, hvordan du opretter et nyt onmicrosoft.com domæne og gør det til dit nye reservedomæne.
ms.openlocfilehash: 967cc1992b33b3a17a853954175adbf050b34f1c
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/28/2022
ms.locfileid: "66858602"
---
# <a name="add-and-replace-your-onmicrosoftcom-fallback-domain-in-microsoft-365"></a>Tilføj og erstat dit onmicrosoft.com reservedomæne i Microsoft 365

Når du tilmelder dig Microsoft 365, leverer Microsoft et *onmicrosoft.com* domæne – dit **reservedomæne** – i tilfælde af at du ikke ejer et domæne eller ikke vil oprette forbindelse til Microsoft 365 (f.eks. tailspintoys.onmicrosoft.com). Reservedomænet bruges som standard i:

- Brugernavne og mailadresser
- Mailaliaser for Microsoft 365-teams & grupper
- Automatiske domæneafhængighedsflytninger

Den fungerer som en standardadresse til e-mail-routing for dit Microsoft 365-miljø. Når en bruger er konfigureret med en postkasse, distribueres mail til reservedomænet.  Selvom der bruges et brugerdefineret domæne (f.eks. tailspintoys.com), sikrer reservedomænet, at din brugers mail distribueres korrekt, hvis det brugerdefinerede domæne slettes fra dit Microsoft 365-miljø.

Du kan ændre reservedomænet i Microsoft 365 Administration. Almindelige årsager til, at kunder ændrer deres reservedomæne, omfatter:

- Det firmanavn, der skal bruges, da de første gang tilmeldte sig Microsoft 365, kendes ikke. Nu, hvor de kender firmanavnet, ønsker de, at deres brugere skal have de relevante logonkontonavne. 
- De vil ændre, hvordan deres SharePoint-URL-adresser ser ud, når de opretter et nyt websted. SharePoint-URL-adresser i dit Microsoft 365-miljø oprettes på baggrund af dit reservedomænenavn. Hvis du ikke brugte det korrekte firmanavn, da du første gang tilmeldte dig, vil dine SharePoint-URL-adresser til dine websteder fortsat bruge dette navn, når du opretter nye SharePoint-websteder. 


Selvom du kan tilføje flere onmicrosoft.com domæner, kan du kun bruge ét onmicrosoft.com domæne som reservedomæne. Trinnene i denne artikel beskriver, hvordan du:
- Opret et nyt onmicrosoft.com domæne
- Tildel det som reservedomæne

> [!NOTE]
> Du er begrænset til i alt fem onmicrosoft.com domæner i dit Microsoft 365-miljø. Når de er tilføjet, kan de ikke fjernes. 
  
## <a name="before-you-begin"></a>Før du begynder

Hvis du vil tilføje, redigere eller fjerne domæner, **skal** du være **administrator af domænenavne** eller **global administrator** af en [virksomheds- eller virksomhedsplan](https://products.office.com/business/office). Disse ændringer påvirker hele lejeren. *Brugerdefinerede administratorer* eller *almindelige brugere* kan ikke foretage disse ændringer.


## <a name="add-a-new-onmicrosoftcom-domain"></a>Tilføj et nyt onmicrosoft.com domæne

1. Vælg **Indstillinger** i Microsoft 365 Administration, og vælg derefter **Domæner**.
2. Vælg dit onmicrosoft.com standarddomæne.

    ![Siden Domæner.](../../media/onmicrosoft-domains.png)
  
3. På siden med domæneegenskaber skal du i afsnittet **Om dette domæne** vælge **Tilføj microsoft-domæne**.

    ![Om denne domæneside.](../../media/add-onmicrosoft-domain-link.png)

4. Skriv navnet på det nye onmicrosoft.com domæne i feltet **Domænenavn** **på siden Tilføj onmicrosoft-domæne**. 

    ![Skærmbillede af siden Tilføj onmicrosoft-domæne.](../../media/add-an-onmicrosoftcom-domain-page.png)

    > [!NOTE]
    > Sørg for at kontrollere stavemåden og nøjagtigheden af det angivne domænenavn. Du er begrænset til fem onmicrosoft.com domæner, og de kan i øjeblikket ikke slettes, når de først er oprettet.     

5. Vælg **Tilføj domæne**. Når du er tilføjet, får du vist en meddelelse, der angiver dette. 
    
    ![Skærmbillede af det domæne, der er tilføjet.](../../media/domain-added.png)



## <a name="make-your-new-onmicrosoftcom-domain-your-fallback-domain"></a>Gør dit nye onmicrosoft.com domæne til reservedomænet


> [!NOTE]
> Før du ændrer reservedomænet til et nyt onmicrosoft.com domæne, kan du overveje at ændre dit onmicrosoft.com SharePoint-domæne. Hvis du opretter et ekstra onmicrosoft-domæne og bruger det som reservedomæne, omdøbes det ikke til SharePoint Online. Dine eksisterende URL-adresser til SharePoint og OneDrive forbliver de samme.  Du kan ændre dit.onmicrosoft SharePoint-domæne via PowerShell-trinnene i [prøveversionen af omdøbning af SharePoint-domæner](/sharepoint/change-your-sharepoint-domain-name) (er i øjeblikket tilgængelig for alle lejere med mindre end 1.000 websteder).

Når du har oprettet dit nye onmicrosoft.com domæne, skal du gøre følgende for at ændre det til dit reservedomæne.

1. Vælg **Indstillinger** i Microsoft 365 Administration, og vælg derefter **Domæner**. 

2. Vælg det nye onmicrosoft.com domæne, du har oprettet.

    ![Vælg et domæne.](../../media/onmicrosoft-domains-added.png) 

3. På domænets egenskabsside skal du vælge **Opret reservedomæne**.
 
    ![Skærmbillede af valg af et nyt reservedomæne.](../../media/new-fallback.png) 

4. Der vises en meddelelse på siden om, at reservedomænet er blevet ændret til det nye domæne.

    ![Det nye reservedomæne blev tilføjet.](../../media/fallback-success.png) 

## <a name="related-content"></a>Relateret indhold

[Ofte stillede spørgsmål om domæner](domains-faq.yml) (artikel)</br>
[Hvad er et domæne?](../get-help-with-domains/what-is-a-domain.md) (artikel)</br>
[Køb et domænenavn i Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (artikel)</br>
[Tilføj DNS-poster for at oprette forbindelse til dit domæne](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) (artikel)</br>
[Skift navneservere for at konfigurere Microsoft 365 med en hvilken som helst domæneregistrator](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md) (artikel)
