---
title: Opret et indholdscenter i Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.custom: admindeeplinkSPO
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du opretter et indholdscenter i Microsoft SharePoint Syntex.
ms.openlocfilehash: c630bba8bafad8bcbf9749e7a4d08ae1e86f4d68
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882214"
---
# <a name="create-a-content-center-in-microsoft-sharepoint-syntex"></a>Opret et indholdscenter i Microsoft SharePoint Syntex


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CPSF]

</br>

Hvis du vil oprette og administrere modeller til dokumentforståelse, skal du først have et indholdscenter. Indholdscenteret er grænsefladen til oprettelse af modellen og indeholder også oplysninger om, hvilke dokumentbiblioteker publicerede modeller der er anvendt på.

   ![Vælg et dokumentbibliotek.](../media/content-understanding/content-center-page.png)

Du opretter et standardindholdscenter under [konfigurationen](set-up-content-understanding.md). Men en SharePoint administrator kan også vælge at oprette flere centre efter behov. Selvom et enkelt indholdscenter kan være fint for de miljøer, hvor du vil have en oprulning af alle modelaktiviteter, kan det være en god idé at have flere centre for flere afdelinger i din organisation, som kan have forskellige behov og tilladelseskrav til deres modeller.

Hvis du vil prøve SharePoint Syntex, kan du desuden oprette et indholdscenter ved hjælp af vejledningen i denne artikel uden at købe licenser. Brugere uden licens kan oprette modeller til dokumentforståelse, men de kan ikke anvende dem på et dokumentbibliotek.

> [!NOTE]
> Hvis du i et [Microsoft 365 Multi-Geo-miljø](../enterprise/microsoft-365-multi-geo.md) har et enkelt standardindholdscenter på din centrale placering, kan du kun angive en akkumulering af modelaktivitet inde fra denne placering. Du kan i øjeblikket ikke få en opløftning af modelaktivitet på tværs af farmgrænser i Multi-Geo-miljøet. 

## <a name="create-a-content-center"></a>Opret et indholdscenter

En SharePoint administrator kan oprette et indholdscenterwebsted på samme måde, som de [ville oprette andre SharePoint websted](/sharepoint/create-site-collection) via administrationspanelet til webstedsklargøring.

Sådan opretter du et nyt indholdscenter:

1. Gå til <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">SharePoint Administration > **Aktive websteder** på Microsoft 365 Administration</a>.

2. Klik på **Opret** på siden **Aktive websteder**, og vælg derefter **Andre indstillinger**.

3. Vælg **Indholdscenter** i menuen **Vælg en skabelon**.

4. For det nye websted skal du angive **navnet på webstedet**, **den primære administrator** og et **sprog**.</br>

   > [!NOTE] 
   > Du kan vælge et indholdscenterwebsted, der skal gengives på et hvilket som helst af de tilgængelige sprog, men bemærk, at der i øjeblikket kun kan oprettes modeller til engelske filer. Bemærk også, at standardsproget for webstedet ikke kan redigeres, når webstedet er oprettet, ligesom med andre webstedsskabeloner.

5. Vælg **Udført**.
 
Når du har oprettet et websted for indholdscenter, kan du se det angivet på <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a> i SharePoint Administration. 

### <a name="give-access-to-additional-users"></a>Giv adgang til flere brugere
 
Når du har oprettet webstedet, kan du give yderligere brugere adgang til webstedet via [standardmodellen SharePoint webstedstilladelser](/sharepoint/modern-experience-sharing-permissions).

### <a name="roll-up-of-models-in-the-default-content-center"></a>Opløft af modeller i standardindholdscenteret

I SharePoint Syntex er det første indholdscenter, der oprettes under konfigurationen, *standardindholdscenteret*. Hvis der oprettes efterfølgende indholdscentre, vises deres modeller i standardvisningen for indholdscenteret.

![Skærmbillede af modelbiblioteket i standardindholdscenteret.](../media/content-understanding/model-library-default-content-center.png)

Biblioteket **Modeller** i visningen for standardindholdscenteret grupperer de oprettede modeller efter indholdscenter for at få en oversigtsvisning af alle modeller til dokumentforståelse og modeller til formularbehandling, der er blevet oprettet.

> [!NOTE]
> Du kan ikke ændre det angivne standardindholdscenter. Det er altid det første indholdscenter, der oprettes under konfigurationen. 

## <a name="see-also"></a>Se også

[Opret en klassificering](create-a-classifier.md)

[Opret en udtrækningsmaskine](create-an-extractor.md)

[Opret et indholdscenter](create-a-content-center.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Opret en formularbehandlingsmodel](create-a-form-processing-model.md)

[Anvend en model](apply-a-model.md)