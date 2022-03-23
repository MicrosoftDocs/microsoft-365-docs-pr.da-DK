---
title: Windows 10 Enterprise installation af Contoso
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: Få mere at vide om, hvordan Contoso Microsoft Endpoint Configuration Manager brugt til at installere opgraderinger på stedet til Windows 10 Enterprise.
ms.openlocfilehash: 7fe6efd176e156b75337ba79db6c1db839b0ed03
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589085"
---
# <a name="windows-10-enterprise-deployment-for-contoso"></a>Windows 10 Enterprise installation af Contoso

Før den brede udrulning af Microsoft 365 til virksomheder havde Contoso Windows-kompatible pc'er og enheder, der kører en blanding af Windows 7 (10 %), Windows 8,1 (65 %) og Windows 10 (25 %). Contoso ønskede at opgradere deres pc'er Windows 10 Enterprise benytte avanceret sikkerhed og sænket it-omkostninger fra automatiserede implementeringer af opdateringer. 

Efter vurdering af deres infrastruktur og forretningsmæssige behov identificerede Contoso disse nøglekrav til implementeringen:

- Så mange pc'er og enheder som muligt skal køre Windows 10 Enterprise
- Udrulning af de direkte opgraderinger udnytter eksisterende Konfigurationsstyring infrastruktur
- Kontrol over, hvilke versioner af Windows 10 Enterprise der skal installeres, og opdateringer udføres via cirkler
- Pc'er og enheder skal holde sig opdateret med minimale it-administrative omkostninger og med minimal indvirkning for slutbrugere

Opdateret er defineret som den understøttede version af Windows 10 Enterprise, der opfylder Contosos forretningsbehov, som kan være anderledes end at have alle Windows-kompatible pc'er, der kører den nyeste version af Windows 10 Enterprise.

## <a name="deployment-tools"></a>Udrulningsværktøjer

Før og under opgraderinger af Windows 10 Enterprise brugte Contoso følgende løsninger Windows Analytics:

- Opgraderingsparathed  

  Indsamler system-, program- og driverdata til analyse og identificerer derefter kompatibilitetsproblemer, der kan blokere en opgradering, og foreslåede løsninger på problemerne kendes af Microsoft.

- Opdater overholdelse af regler og standarder  

  Viser dig tilstanden for dine enheder med hensyn til opdateringerne Windows, så du kan sikre, at de er på de nyeste opdateringer efter behov.

- Enhedstilstand  

  Identificerer enheder, der ofte går ned, og derfor muligvis skal genopbygges eller udskiftes, og enhedsdrivere, der forårsager nedbrud på enheden, med forslag til alternative versioner af disse drivere, der kan reducere antallet af nedbrud. Giver besked om Windows konfigurationer af Information Protection, der sender prompter til slutbrugere.
 
Contoso har en eksisterende Konfigurationsstyring (Aktuel forgreningsinfrastruktur). Konfigurationsstyring til store miljøer og giver omfattende kontrol over installation, opdateringer og indstillinger. Den har også indbyggede funktioner, som gør det nemmere og mere effektivt at installere og administrere Windows 10 Enterprise.

## <a name="planning-process"></a>Planlægningsproces

Contoso brugte Upgrade Readiness i Windows Analytics til at bestemme sættet af installerede apps og deres kompatibilitet med Windows 10 Enterprise.

## <a name="deployment-process"></a>Installationsproces

For at fuldføre den komplette opgraderingsinstallation af Windows 10 Enterprise har Contoso implementeret følgende proces, som indeholder anbefalinger om bedste praksis fra Microsoft:

1. Peer-cache aktiveret til Konfigurationsstyring.
2. Oprettede brugerdefinerede Windows-pakker baseret på billeder fra Volume Licensing Service Center.
3. Brugt Konfigurationsstyring til at udrulle Windows-pakker til distributionspunkter på tværs af deres netværk og installerede builds til de tre validerings- og installations-opsætningsgrupper.
4. Udførte en vurdering af succes for pc'er og enheder i de tre validerings- og installations-opsætningsringene ved hjælp af løsninger til enhedsstilstand og opdateringsoverholdelse for Windows Analytics.
5. Baseret på Windows Analytics bestemte Contoso, hvilken version af Windows 10 Enterprise der skulle udrulles til den brede installationsgruppe.
6. Kørte Konfigurationsstyring til installation for at installere den valgte Windows pakke til den brede installationsgruppe.
7. Overvågede pc'er og enheder i den brede installationsgruppe ved hjælp af løsningerne Enhedstilstand og Opdateringsoverholdelse for at løse problemer.

Her er Contosos direkte opgradering og løbende opdatering af installationsarkitekturen.

![Contosos Windows 10 Enterprise-installationsinfrastruktur.](../media/contoso-win10/contoso-win10-fig1.png)

Denne infrastruktur består af:

- Konfigurationsstyring, som:
  - Henter billeder til Windows 10 Enterprise fra Microsoft Volume Licensing Center i Microsoft Network.
  - Er det centrale administrationspunkt for installationspakker.
- Regionale distributionspunkter, der typisk er placeret i Contosos regionale hubkontorer.
- Windows pc'er og enheder på forskellige placeringer, der modtager og installerer installationspakker til den direkte opgradering eller løbende opdateringer baseret på gruppemedlemskab.

## <a name="next-step"></a>Næste trin

Få mere at vide om, hvordan Contoso udnytter sin Konfigurationsstyring til at installere og [holde Microsoft 365 Apps for enterprise på](contoso-o365pp.md) tværs af organisationen. 

## <a name="see-also"></a>Se også

[Windows 10 Enterprise](/windows/deployment/)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Test labvejledninger](m365-enterprise-test-lab-guides.md)