---
title: Sådan prioriterer, administrerer, undersøger & svar på hændelser i Microsoft 365 Defender
description: Trinnene til administration af beskeder, der udløses i Microsoft 365 Defender. Automatiseret undersøgelse og svar (AIR) jagter på tværs af abonnementet og bestemmer virkningen og omfanget af en trussel og kombinerer oplysningerne til en enkelt hændelse.
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
ms.openlocfilehash: 18127cd732c0e2e1392a9c62e221dadfbd123246
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043428"
---
# <a name="prioritize-manage-investigate--respond-to-incidents-in-microsoft-365-defender"></a>Prioriter, Administrer, Undersøg & Svar på hændelser i Microsoft 365 Defender

Når beskeder udløses i Microsoft 365 Defender, udløses automatiseret undersøgelse og svar (AIR) for at jage på tværs af en organisations abonnement, fastslå virkningen og omfanget af truslen og samle oplysningerne i en enkelt hændelse, så administratorer ikke behøver at administrere flere hændelser.

## <a name="what-youll-need"></a>Det skal du bruge

- Microsoft Defender for Office 365 plan 2 eller nyere
- Tilstrækkelige tilladelser (sikkerhedslæser, sikkerhedshandlinger eller sikkerhedsadministrator samt [rollen Søg og fjern](../permissions-microsoft-365-security-center.md) )

## <a name="prioritize--manage-incidents"></a>Prioriter & administrere hændelser

Gå til siden https://security.microsoft.com/incidentsHændelser på sikkerhedsportalen .

Når siden Hændelse indlæses, kan du filtrere og prioritere ved at klikke på kolonner for at sortere handlingerne eller trykke på Filtre for at anvende et filter, f.eks. datakilde, koder eller tilstand.

Nu har du en prioriteret liste over hændelser, hvorfra du kan vælge at omdøbe, tildele, klassificere, mærke, ændre status eller tilføje kommentarer via knappen Administrer hændelser.

Brug filtrene til at sikre, at Microsoft Defender til Office elementer er inkluderet.

Hvis du leder efter bestemte beskeder, skal du enten bruge hændelsessøgefunktionen (*Søg efter navn eller id*) eller overveje at bruge filtrering af beskedkøen på en bestemt besked.

## <a name="investigate--respond-to-incidents"></a>Undersøg & svar på hændelser

Når du har prioriteret din hændelseskø, skal du klikke på den hændelse, du vil undersøge for at indlæse siden Oversigt over hændelser. Der vil være nyttige oplysninger som *MITRE ATT&CK teknikker observeret* og en *tidslinje for angrebet*.

Fanerne øverst på hændelsessiden giver dig mulighed for at udforske flere oplysninger, f.eks. de berørte brugere, postkasser, slutpunkter og et cetera.

Under fanen *Beviser og svar* vises elementer, der er identificeret som relateret til den oprindelige besked via undersøgelsen.

Alle elementer, der vises som *Ventende handling* i Beviser og Svar, afventer godkendelse fra en administrator.  Det anbefales at sortere efter kolonnen med afhjælpningsstatus i visningen *Alle beviser* efterfulgt af at klikke på enheden eller klyngen for at indlæse pop op-menuen, hvor du derefter kan godkende handlingerne, hvis det er relevant.

Hvis du har brug for at forstå de involverede elementer yderligere, kan du bruge hændelsesgrafen til at se den visuelle sammenkædning af de involverede beviser og enheder. Du kan også gennemse de underliggende undersøgelser, som viser flere af de enheder og elementer, der er involveret i sikkerhedshændelsen.

## <a name="next-steps"></a>Næste trin

Du kan begynde at bruge *Løsningscenter* til at reagere på ventende handlingselementer fra alle hændelser i organisationen, hvis du vil fokusere på de handlingselementer, SOM AIR skal godkendes for.  

## <a name="more-information"></a>Flere oplysninger

[Administrer hændelser i Microsoft 365 Defender | Microsoft Docs](../../defender/manage-incidents.md)

[Sådan fungerer automatiseret undersøgelse og svar i Microsoft Defender for Office 365](../automated-investigation-response-office.md)

[Afhjælpningshandlinger i Microsoft Defender for Office 365](../air-remediation-actions.md)