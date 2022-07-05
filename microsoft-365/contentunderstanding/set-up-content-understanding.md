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
ms.openlocfilehash: 3511719e4f396141217a2b4711f642c675ac781e
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617232"
---
# <a name="set-up-sharepoint-syntex"></a>Konfigurer SharePoint Syntex

Administratorer kan bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> til at konfigurere [Microsoft SharePoint Syntex](index.md). 

Overvej følgende, før du starter:

- På hvilke SharePoint-websteder vil du aktivere formularbehandling? Alle dem, nogle, eller vælg websteder?
- Hvad vil du kalde dit standardindholdscenter?

Du kan ændre dine indstillinger efter den indledende konfiguration i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>.

Før du konfigurerer, skal du sørge for at planlægge den bedste måde at konfigurere forståelse af indhold på i dit miljø. Du skal f.eks. træffe følgende beslutninger:

- De SharePoint-websteder, hvor du vil aktivere formularbehandling – dem alle, nogle eller valgte websteder
- Navn og administratorer for dit indholdscenter

## <a name="requirements"></a>Krav 

> [!NOTE]
> Du skal have tilladelser som global administrator eller SharePoint-administrator for at kunne få adgang til Microsoft 365 Administration og konfigurere SharePoint Syntex.

Som administrator kan du også foretage ændringer af dine valgte indstillinger når som helst efter konfigurationen og i hele indstillingerne for administration af indhold i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>.

### <a name="custom-power-platform-environments"></a>Brugerdefinerede Power Platform-miljøer

Hvis du planlægger at bruge et brugerdefineret Power Platform-miljø, skal du installere *AI Builder til Project Cortex* app i dette miljø. Se [Administrer Dynamics 365-apps](/power-platform/admin/manage-apps#install-an-app-in-the-environment-view) for at få flere oplysninger, og se *efter AI Builder til Project Cortex* app på listen over Dynamics 365-apps.

Du skal også [tildele AI Builder-kreditter](/power-platform/admin/capacity-add-on) til det brugerdefinerede miljø, før du kan oprette modeller til formularbehandling. 

Når du bruger et brugerdefineret miljø, skal modeloprettere tildeles sikkerhedsrollen Miljøopretter, og modelbrugere skal have tildelt sikkerhedsrollen Grundlæggende bruger. Se [Tildel en sikkerhedsrolle til en bruger for at](/power-platform/admin/assign-security-roles) få flere oplysninger.

Brugere, der opretter modeller på et [indholdscenterwebsted](/microsoft-365/contentunderstanding/create-a-content-center) , skal være medlemmer af webstedet. Brugere, der opretter modeller lokalt uden for indholdscenteret, skal være webstedsejere af disse websteder.

### <a name="licensing"></a>Licensering

Hvis du vil bruge SharePoint Syntex, skal din organisation have et abonnement på SharePoint Syntex, og hver bruger skal have tildelt en licens. SharePoint Syntex licenser omfatter følgende apps, som alle skal tildeles:

- SharePoint Syntex
- SharePoint Syntex – SPO-type
- Common Data Service til SharePoint Syntex

Hvis du vil bruge formularbehandling, skal du også bruge AI Builder-kreditter. For hver licenseret bruger af SharePoint Syntex gives der en allokering af AI Builder-kreditter hver måned.

Du kan finde flere oplysninger om SharePoint Syntex licenser under [SharePoint Syntex licenser](syntex-licensing.md)

## <a name="to-set-up-sharepoint-syntex"></a>Sådan konfigurerer du SharePoint Syntex

1. I Microsoft 365 Administration skal du vælge <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Installation**</a> og derefter se afsnittet **Filer og indhold**.

2. I afsnittet **Filer og indhold** skal du vælge **Automatiser forståelse af indhold**. Bemærk, at din aktuelle AI Builder-kredittilgængelighed vises i afsnittet **Hurtigt overblik** .<br/>

3. På siden **Automatiser forståelse af indhold** skal du klikke på **Kom i gang** for at gennemgå konfigurationsprocessen. <br/>

    > [!div class="mx-imgBorder"]
    > ![Start konfigurationen.](../media/content-understanding/admin-content-understanding-get-started.png)</br>

4. På siden **Konfigurer formularbehandling** kan du vælge, om du vil give brugerne mulighed for at oprette modeller til formularbehandling i bestemte SharePoint-dokumentbiblioteker. Der er en menuindstilling tilgængelig på båndet i dokumentbiblioteket, hvor du kan **oprette en formularbehandlingsmodel** i De SharePoint-dokumentbiblioteker, hvor den er aktiveret.
 
     **For hvilke SharePoint-biblioteker skal vise muligheden for at oprette en formularbehandlingsmodel**, kan du vælge:</br>
      - **Biblioteker på alle SharePoint-websteder** for at gøre det tilgængeligt for alle SharePoint-biblioteker i din organisation.</br>
      - **Biblioteker på valgte SharePoint-websteder**, og vælg derefter de websteder, hvor du vil gøre dem tilgængelige, eller upload en liste over op til 50 websteder.</br>
      - **Ingen SharePoint-biblioteker** , hvis du ikke vil gøre det tilgængeligt for nogen websteder (du kan ændre dette efter konfigurationen).

   > [!div class="mx-imgBorder"]
   > ![Konfigurer indstillinger for formularbehandlingswebsted.](../media/content-understanding/admin-configforms.png)

   > [!Note]
   > Hvis du fjerner et websted, når det er inkluderet, påvirker det ikke eksisterende modeller, der er anvendt på bibliotekerne på det pågældende websted, eller muligheden for at anvende modeller til dokumentforståelse i et bibliotek. 
    
    Hvis du har konfigureret flere Power Platform-miljøer, kan du vælge, hvilket du vil bruge sammen med til formularbehandling. Denne indstilling vises ikke, hvis du kun har ét miljø.

    ![Konfigurer indstillinger for formularbehandling i Power Platform.](../media/content-understanding/setup-power-platform-env.png)

    I **Power Platform-miljøet** kan du vælge:
    - **Brug standardmiljøet** til at bruge dit Power Platform-standardmiljø.
    - **Brug et brugerdefineret miljø** til at bruge et brugerdefineret miljø. Vælg det miljø, du vil bruge, på listen. ([Se kravene til et brugerdefineret miljø](/microsoft-365/contentunderstanding/set-up-content-understanding#requirements)).

    Klik på **Næste**.

5. På siden **Opret indholdscenter** kan du oprette et SharePoint-indholdscenterwebsted, hvor brugerne kan oprette og administrere modeller til dokumentforståelse. Hvis du tidligere har oprettet et indholdscenter fra SharePoint Administration, vises disse oplysninger her, og du kan blot vælge **Næste**.

    1. Under **Navn på websted** skal du skrive det navn, du vil give dit indholdscenterwebsted.
    
    1. **Webstedsadressen** viser URL-adressen for dit websted baseret på det, du har valgt for webstedets navn. Klik på **Rediger**, hvis du vil ændre den.

       > [!div class="mx-imgBorder"]
       > ![Opret indholdscenter.](../media/content-understanding/admin-cu-create-cc.png)</br>

       Vælg **Næste**.

6. På siden **Gennemse og afslut** kan du se på den valgte indstilling og vælge at foretage ændringer. Hvis du er tilfreds med dine valg, skal du vælge **Aktivér**.

7. Klik på **Udført** på bekræftelsessiden.

8. Du vender tilbage til siden **til forståelse af automatiseret indhold** . På denne side kan du vælge **Administrer** for at foretage ændringer af dine konfigurationsindstillinger. 

## <a name="assign-licenses"></a>Tildel licenser

Når du har konfigureret SharePoint Syntex, skal du tildele licenser til de brugere, der skal bruge SharePoint Syntex funktioner.

Sådan tildeler du licenser:

1. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Aktive brugere**</a> under **Brugere** i Microsoft 365 Administration.

2. Vælg de brugere, du vil licensere, og vælg **Administrer produktlicenser**.

3. Vælg **Apps** i rullemenuen.

4. Vælg **Vis apps for SharePoint Syntex**. Under **Apps** skal du sørge for, at **Common Data Service til SharePoint Syntex**, **SharePoint Syntex** og **SharePoint Syntex – SPO-typen** er valgt.

    > [!div class="mx-imgBorder"]
    > ![SharePoint Syntex licenser i Microsoft 365 Administration.](../media/content-understanding/sharepoint-syntex-licenses.png)

5. Klik på **Gem ændringer**.

## <a name="see-also"></a>Se også

[Oversigt over formularbehandlingsmodellen](/ai-builder/form-processing-model-overview)

[Trin for trin: Sådan opretter du en model til dokumentforståelse (video)](https://www.youtube.com/watch?v=DymSHObD-bg)

[Opret og administrer miljøer i Power Platform Administration](/power-platform/admin/create-environment)
