---
title: Sådan prioriterer og administrerer du automatiserede undersøgelser og svar (AIR).
description: Sådan får du trin til at analysere og godkende AIR-handlinger direkte fra Løsningscenter. Når beskeder udløses, bestemmer automatiseret undersøgelse og svar omfanget af virkningen af en trussel i din organisation og leverede anbefalede afhjælpningshandlinger.
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
ms.openlocfilehash: 234ce1ecb486c01b95c91aa51a0c5fd6b46e7a3c
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043526"
---
# <a name="prioritize-and-manage-automated-investigations-and-response-air"></a>Prioriter og administrer automatiserede undersøgelser og svar (AIR)

Air (Automated Investigation and Response) sparer tid og kræfter på dit sikkerhedsteam.

- Når beskeder udløses, bestemmer den automatiserede undersøgelse omfanget af en trussels indvirkning i din organisation og giver anbefalede afhjælpningshandlinger.
- Sikkerhedsteams kan spare tid ved at udnytte AIR automation til at reducere behovet for manuel jagt.
- Disse undersøgelser kan identificere mails, der ikke er blevet ryddet op med ZAP (Auto Purge) eller anden afhjælpning på nul timer.
- AIR-undersøgelser identificerer også postkassekonfigurationer, der kan være risikable eller angive en kompromitteret postkasse.

Undersøgelseshandlinger (og undersøgelser) er tilgængelige fra flere punkter på Microsoft Security-portalen: via *hændelser*, via *beskeder* eller via *Handlingscenter*. Hvilke administratorer der bruger er baseret på den arbejdsproces, som en administrator følger.

## <a name="why-use-the-action-center-workflow"></a>Hvorfor bruge arbejdsprocessen i Løsningscenter

I takt med at automatiserede undersøgelser af *mail & resulterer samarbejdsindhold* i domme, f.eks *. ondsindet* eller *mistænkeligt*, oprettes der visse afhjælpningshandlinger. De foreslåede afhjælpningshandlinger udføres ikke automatisk. SecOps skal navigere til hver undersøgelse for at *godkende* disse foreslåede handlinger. I *Løsningscenter* samles alle ventende handlinger til hurtig godkendelse.

## <a name="what-youll-need"></a>Det skal du bruge

- Microsoft Defender for Office 365 Plan 2 eller nyere (inkluderet med E5)
- Tilstrækkelige tilladelser (sikkerhedslæser, sikkerhedshandlinger eller sikkerhedsadministrator samt [rollen Søg og fjern](../permissions-microsoft-365-security-center.md) )

## <a name="steps-to-analyze-and-approve-air-actions-directly-from-the-action-center"></a>Trin til at analysere og godkende AIR-handlinger direkte fra Løsningscenter

1. Gå til [Microsoft 365 Defender portal,](https://security.microsoft.com/action-center) og log på.
2. Når Handlingscenter indlæser, skal du filtrere og prioritere ved at klikke på kolonner for at sortere handlingerne eller trykke på **Filtre** for at anvende et filter, f.eks. *objekttype* (for en bestemt URL-adresse) eller handlingstype (f.eks. blød sletning af mail).
3. Et pop op-vindue åbnes, når der klikkes på en handling. Den vises til højre på skærmen til gennemsyn.
4. Du kan finde flere oplysninger om, hvorfor der anmodes om en handling, ved at vælge **Åbn undersøgelsesside** i pop op-vinduet for at få mere at vide om den undersøgelse eller de beskeder, der er knyttet til denne handling. Administratorer kan også godkende handlinger, der vises på undersøgelsessiden, ved at vælge fanen *Ventende handlinger* .
5. Ellers skal du vælge **Godkend** for at udføre den anbefalede handling direkte fra Løsningscenter.
6. Afvis handlingen, hvis du finder den unødvendig.

## <a name="check-air-history"></a>Kontrollér AIR-historik

1. Gå til [Microsoft 365 Defender-portalen](https://security.microsoft.com), og log på.
2. I navigationsruden til venstre skal du udvide **Handling & indsendelser** og derefter klikke på **Løsningscenter**.
3. Når Handlingscenter indlæses, skal du trykke på fanen **Oversigt** .
4. Få vist historikken for AIR, herunder de beslutninger, der er truffet, kilden til handlingen og den administrator, der har truffet beslutningen, hvis det er relevant.

## <a name="more-information"></a>Flere oplysninger

[Få vist resultaterne af en automatisk undersøgelse i Microsoft 365 – Office 365 | Microsoft Docs](../air-view-investigation-results.md)

[Få mere at vide om godkendelse og afvisning af ventende handlinger fra siden Undersøgelse](../air-review-approve-pending-completed-actions.md)
