---
title: Konfigurer SharePoint Syntex
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom:
- admindeeplinkMAC
search.appverid: MET150
ms.localizationpriority: high
description: Konfigurer SharePoint Syntex
ms.openlocfilehash: 244038e4c49801cad59bd9cf8939c47291c5270f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588454"
---
# <a name="set-up-sharepoint-syntex"></a>Konfigurer SharePoint Syntex

Administratorer kan bruge administratorerne <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> at konfigurere [Microsoft SharePoint Syntex](index.md). 

Overvej følgende, før du starter:

- På hvilke SharePoint vil du så aktivere behandling af formular? Alle af dem, nogle eller vælg websteder?
- Hvad navngiver du dit standardindholdscenter?

Du kan ændre dine indstillinger efter den indledende konfiguration i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>.

Før konfigurationen skal du sørge for at planlægge den bedste måde at konfigurere og konfigurere indholdsforståelse i dit miljø. Du skal f.eks. træffe følgende beslutninger:

- De SharePoint, hvor du vil aktivere behandling af formular – dem alle, nogle eller udvalgte websteder
- Navnet og administratorerne for dit indholdscenter

## <a name="requirements"></a>Krav 

> [!NOTE]
> Du skal have globale administrator- SharePoint-administratortilladelser for at kunne få adgang til Microsoft 365 Administration og konfigurere SharePoint Syntex.

Som administrator kan du også foretage ændringer til dine valgte indstillinger når som helst efter konfigurationen og i alle indstillingerne for indholdsforståelse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">i Microsoft 365 Administration</a>.

Hvis du planlægger at bruge et brugerdefineret Power Platform-miljø, skal du installere [*AI Builder til Project Cortex-appen*](/power-platform/admin/manage-apps#install-an-app-in-the-environment-view) i dette miljø og tildele [AI Builder-kreditter](/power-platform/admin/capacity-add-on) til den, før du kan oprette modeller til formularbehandling.

### <a name="licensing"></a>Licensering

For at SharePoint Syntex skal din organisation have et abonnement på SharePoint Syntex, og hver enkelt bruger skal have tildelt følgende licenser:

- SharePoint Syntex
- SharePoint Syntex – SPO-type
- Fælles datatjeneste til SharePoint Syntex

Hvis du vil bruge formularbehandling, skal du også bruge AI Builder-kredit. Hvis du har 300 eller flere brugere med licens, tildeles der en tildeling af AI Builder-kredit hver måned.

Du kan få mere SharePoint Syntex om licenser i [SharePoint Syntex licenser](syntex-licensing.md)

## <a name="to-set-up-sharepoint-syntex"></a>Sådan konfigurerer du SharePoint Syntex

1. I sektionen Microsoft 365 Administration du <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**vælge Konfiguration**</a> og derefter få vist **sektionen Filer og** indhold.

2. I sektionen **Filer og indhold** skal du vælge **Automatiser indholdsforståelse**. Bemærk, at din aktuelle tilgængelighed for AI Builder-kredit vises **i sektionen Få et hurtigt** overblik.<br/>

3. På siden **Automatiser indholdsforståelse** skal du klikke **på Introduktion** for at gennemgå konfigurationsprocessen. <br/>

    > [!div class="mx-imgBorder"]
    > ![Start konfigurationen.](../media/content-understanding/admin-content-understanding-get-started.png)</br>

4. På siden **Konfigurer formularbehandling** kan du vælge, om du vil give brugerne mulighed for at oprette modeller til formularbehandling i bestemte SharePoint dokumentbiblioteker. En menuindstilling er tilgængelig på båndet i dokumentbiblioteket til At **oprette en formularbehandlingsmodel** i SharePoint dokumentbiblioteker, hvor den er aktiveret.
 
     For **Hvilke SharePoint biblioteker skal vise muligheden for at oprette en formularbehandlingsmodel**, kan du vælge:</br>
      - **Biblioteker på alle SharePoint for** at gøre det tilgængeligt for SharePoint biblioteker i organisationen.</br>
      - **Biblioteker i de SharePoint websteder**, og vælg derefter de websteder, hvor du vil gøre det tilgængeligt, eller upload en liste over op til 50 websteder.</br>
      - **Ingen SharePoint biblioteker,** hvis du ikke vil gøre det tilgængeligt for nogen websteder (du kan ændre dette efter installationen).

   > [!div class="mx-imgBorder"]
   > ![Konfigurere indstillinger for formularbehandlingswebsted.](../media/content-understanding/admin-configforms.png)

   > [!Note]
   > Hvis du fjerner et websted, efter det er blevet inkluderet, påvirker det ikke eksisterende modeller, der anvendes på bibliotekerne på det pågældende websted, eller muligheden for at anvende dokumentforståelsesmodeller på et bibliotek. 
    
    Hvis du har konfigureret flere Power Platform-miljøer, kan du vælge, hvilket du vil bruge sammen med til formularbehandling. (Denne indstilling vises ikke, hvis du kun har ét miljø).

    ![Konfigurere Power Platform-indstillinger for formularbehandling.](../media/content-understanding/setup-power-platform-env.png)

    For **Power Platform-miljøet** kan du vælge:
    - **Brug standardmiljøet for** at bruge dit standardmiljø til Power Platform.
    - **Brug et brugerdefineret miljø** til at bruge et brugerdefineret miljø. Vælg det miljø, du vil bruge, på listen. Se [kravene til et brugerdefineret miljø](/microsoft-365/contentunderstanding/set-up-content-understanding#requirements).

    Klik på **Næste**.

5. På siden **Opret indholdscenter** kan du oprette et SharePoint websted, hvor brugerne kan oprette og administrere dokumentforståelsesmodeller. Hvis du tidligere har oprettet et indholdscenter SharePoint Administration, vises disse oplysninger her, og du kan blot vælge **Næste**.

    1. Ud **for Webstedsnavn** skal du skrive det navn, du vil give dit indholdscenterwebsted.
    
    1. **Webstedsadressen** viser URL-adressen til webstedet baseret på, hvad du har valgt som navnet på webstedet. Hvis du vil ændre det, skal du klikke på **Rediger**.

       > [!div class="mx-imgBorder"]
       > ![Opret indholdscenter.](../media/content-understanding/admin-cu-create-cc.png)</br>

       Vælg **Næste**.

6. På siden **Gennemse og afslut** kan du se dine valgte indstillinger og vælge at foretage ændringer. Hvis du er tilfreds med dine valg, skal du vælge **Aktivér**.

7. Klik på Udført på **bekræftelsessiden**.

8. Du kommer tilbage til siden **Automatiser indholdsforståelse** . Fra denne side kan du vælge Administrer **for at** foretage ændringer i konfigurationsindstillingerne. 

## <a name="assign-licenses"></a>Tildel licenser

Når du har konfigureret SharePoint Syntex, skal du tildele licenser til de brugere, der skal bruge de SharePoint Syntex funktioner.

Sådan tildeler du licenser:

1. Vælg aktive Microsoft 365 Administration **under Brugere** på <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**listen.**</a>

2. Vælg de brugere, du vil licensere, og vælg **Administrer produktlicenser**.

3. Vælg **Apps** i rullemenuen.

4. Vælg **Vis apps for SharePoint Syntex**. Under **Apps** skal du sørge **for, at Fælles datatjeneste for SharePoint Syntex**, **SharePoint Syntex** og **SharePoint Syntex – SPO-type** alle er markeret.

    > [!div class="mx-imgBorder"]
    > ![SharePoint Syntex licenser i Microsoft 365 Administration.](../media/content-understanding/sharepoint-syntex-licenses.png)

5. Klik på **Gem ændringer**.

## <a name="see-also"></a>Se også

[Oversigt over formularbehandlingsmodellen](/ai-builder/form-processing-model-overview)

[Trinvis vejledning: Sådan opbygges en dokumentforståelsesmodel (video)](https://www.youtube.com/watch?v=DymSHObD-bg)

[Opret og administrer miljøer i Power Platform Administration](/power-platform/admin/create-environment)
