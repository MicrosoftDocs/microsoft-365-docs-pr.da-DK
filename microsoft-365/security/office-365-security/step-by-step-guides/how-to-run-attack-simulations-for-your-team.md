---
title: Sådan kører du angrebssimuleringer for dit team
description: Trinnene til at sende en nyttedata til angrebssimulering til dine målbrugere for dit team eller din organisation til oplæring. Simulerede angreb kan hjælpe dig med at identificere og finde sårbare brugere, politikker og fremgangsmåder, før et reelt angreb påvirker din organisation.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: c67c709a36c07b947cd1b92abefcc7548acf8f3a
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66044304"
---
# <a name="how-to-run-attack-simulations-for-your-team"></a>Sådan kører du angrebssimuleringer for dit team

Træning i simulering af angreb giver dig mulighed for at køre realistiske, men godartede cyberangrebsscenarier i din organisation. Simulerede angreb kan hjælpe dig med at identificere og finde sårbare brugere, politikker og fremgangsmåder, før et reelt angreb påvirker din organisation, ved at bruge indbygget eller brugerdefineret træning til at reducere risikoen og bedre uddanne slutbrugerne om trusler.

## <a name="what-youll-need"></a>Det skal du bruge

- Microsoft Defender for Office 365 Plan 2 (inkluderet som en del af E5)
- Tilstrækkelige tilladelser (rolle som sikkerhedsadministrator)
- 5-10 minutter for at udføre trinnene nedenfor.

## <a name="send-a-payload-to-target-users"></a>Send en nyttedata til målbrugere

1. Naviger til [Træning i simulering af angreb](https://security.microsoft.com/attacksimulator ) i dit abonnement.
1. Vælg **Simuleringer** på den øverste navigationslinje.
1. Vælg **Start en simulering**.
1. Vælg den teknik, du vil bruge, i pop op-vinduet, og tryk på **Næste**.
1. Navngiv simuleringen med noget relevant/mindeværdigt, og tryk på **Næste**.
1. Vælg en relevant nyttedata fra guiden, gennemse oplysningerne, og tilpas, hvis det er relevant. Tryk på **Næste**, når du er tilfreds med valget.
1. Vælg, hvem der skal målrettes med nyttedataene. Hvis du vælger hele organisationen, skal du fremhæve alternativknappen og trykke på **Næste**.
1. Ellers skal du vælge **Tilføj brugere** og derefter søge eller filtrere brugerne med guiden. Vælg Tilføj bruger(e) og derefter **Næste**.
1. Under **Vælg indstillinger for oplæringsindhold** skal du lade *standarden for Microsoft-oplæringsoplevelsen (anbefales)* eller vælge *Omdiriger til en brugerdefineret URL-adresse* , hvis du vil bruge den brugerdefinerede URL-adresse. Hvis du ikke vil tildele nogen oplæring, skal du vælge *Ingen oplæring*.
    - Du kan enten lade Microsoft tildele kurser ved at vælge *Tildel træning til mig* , eller du kan selv vælge bestemte moduler med *Vælg kurser og moduler*
    - Vælg en forfaldsdato (30, 15 eller 7 dage) i rullemenuen.
    - Klik på **Næste** for at fortsætte.
1. Tilpas den landingsside, der vises, når en bruger er phished, hvis det er relevant, eller på anden måde forlade Microsoft Standard.
    1. Markér afkrydsningsfeltet under **Payload-indikatorer** for at føje nyttedataindikatorer til mail. Tilføjelse af nyttedata hjælper brugerne med at få mere at vide om, hvordan de identificerer phishing-mailen. Vælg *Åbn eksempelpanelet* for at få vist meddelelsen.
    1. Klik på **Næste** for at fortsætte.
1. Vælg, om du vil have slutbrugermeddelelser, og hvis det er tilfældet, skal du vælge leveringsindstillingerne og tilpasse, hvor det er nødvendigt.
    1. Bemærk, at du også kan vælge *standardsprog* til meddelelsen i rullemenuen **Vælg standardsprog** .
1. Vælg, hvornår simuleringen skal startes, og hvor længe den skal være gyldig for. Du kan også aktivere *levering af tidszone, der er opmærksom på området*. Denne indstilling leverer simulerede angrebsmeddelelser til dine medarbejdere i løbet af *deres arbejdstid* baseret på deres område. Vælg **Næste**.
1. Send en test, hvis du er klar. Gennemse oversigten over valgmuligheder. Klik på **Send**.

### <a name="further-reading"></a>Yderligere læsning

Du kan få mere at vide om, hvordan simulering af angreb fungerer, under [Simuler et phishing-angreb med oplæring i simulering af angreb – Office 365 | Microsoft Docs](../../office-365-security/attack-simulation-training.md)
