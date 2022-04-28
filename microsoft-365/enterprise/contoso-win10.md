---
title: Windows 10 Enterprise installation for Contoso
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: Forstå, hvordan Contoso brugte Microsoft Endpoint Configuration Manager til at udrulle direkte opgraderinger til Windows 10 Enterprise.
ms.openlocfilehash: 082c60de614c5a125a1fd2af6ba9d187f21ca39e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095350"
---
# <a name="windows-10-enterprise-deployment-for-contoso"></a>Windows 10 Enterprise installation for Contoso

Før den brede udrulning af Microsoft 365 for virksomheder havde Contoso Windows kompatible pc'er og enheder, der kørte en blanding på Windows 7 (10 %), Windows 8,1 (65 %) og Windows 10 (25 %). Contoso ønskede at opgradere deres pc'er til Windows 10 Enterprise drage fordel af avanceret sikkerhed og reducerede it-omkostninger fra automatiserede udrulninger af opdateringer. 

Efter at have vurderet deres infrastruktur- og forretningsbehov identificerede Contoso disse vigtige krav til udrulningen:

- Så mange pc'er og enheder som muligt bør køre Windows 10 Enterprise
- Udrulningen af de direkte opgraderinger udnytter eksisterende Configuration Manager infrastruktur
- Styr, hvilke versioner af Windows 10 Enterprise der skal installeres, og opdateringer udføres via ringe
- Pc'er og enheder bør holde sig ajour med minimale administrative it-omkostninger og med minimal indvirkning på slutbrugerne

Opdateret defineres som den understøttede version af Windows 10 Enterprise, der opfylder Contosos forretningsmæssige behov, hvilket kan være anderledes end at have alle Windows-kompatible pc'er, der kører den nyeste version af Windows 10 Enterprise.

## <a name="deployment-tools"></a>Installationsværktøjer

Før og under direkte opgraderinger af Windows 10 Enterprise brugte Contoso følgende løsninger i Windows Analytics:

- Opgraderingsparathed  

  Indsamler system-, program- og driverdata til analyse og identificerer derefter kompatibilitetsproblemer, der kan blokere en opgradering, og forslag til rettelser af problemerne, som Microsoft kender.

- Opdateringsoverholdelse  

  Viser dig tilstanden for dine enheder med hensyn til de Windows opdateringer, så du kan sikre, at de er på de mest aktuelle opdateringer efter behov.

- Enhedstilstand  

  Identificerer enheder, der går ned ofte, og som derfor muligvis skal genopbygges eller erstattes, og enhedsdrivere, der forårsager enhedsnedbrud, med forslag til alternative versioner af disse drivere, der kan reducere antallet af nedbrud. Giver besked om Windows Information Protection fejlkonfigurationer, der sender prompter til slutbrugere.
 
Contoso har en eksisterende infrastruktur for Configuration Manager (aktuel forgrening). Configuration Manager skaleres til store miljøer og giver stor kontrol over installation, opdateringer og indstillinger. Den har også indbyggede funktioner, der gør det nemmere og mere effektivt at udrulle og administrere Windows 10 Enterprise.

## <a name="planning-process"></a>Planlægningsproces

Contoso brugte Upgrade Readiness i Windows Analytics til at bestemme sættet af installerede apps og deres kompatibilitet med Windows 10 Enterprise.

## <a name="deployment-process"></a>Installationsproces

For at fuldføre udrulningen af Windows 10 Enterprise implementerede Contoso følgende proces, som omfatter anbefalinger til bedste praksis fra Microsoft:

1. Aktiveret peercache for Configuration Manager.
2. Oprettede brugerdefinerede Windows pakker baseret på billeder fra Volume Licensing Service Center.
3. Bruges Configuration Manager til at installere Windows-pakker til distributionspunkter på tværs af deres netværk og udrullede builds til de tre grupper for validerings- og udrulnings midlertidige grupper.
4. Udført vurdering af, om det lykkedes for pc'er og enheder at udføre de tre test- og udrulningsringe ved hjælp af løsningerne Device Health og Update Compliance i Windows Analytics.
5. På baggrund af Windows Analytics-oplysningerne bestemte Contoso den version af Windows 10 Enterprise, der skulle udrulles til den brede udrulningsgruppe.
6. Kørte sekvenserne for Configuration Manager udrulningsopgaven for at installere den valgte Windows pakke til den brede udrulningsgruppe.
7. Overvågede pc'er og enheder i den brede installationsgruppe ved hjælp af løsningerne Enhedstilstand og Opdateringsoverholdelse for at løse problemer.

Her er Contosos direkte opgradering og den løbende opdateringsarkitektur.

![Contosos Windows 10 Enterprise installationsinfrastruktur.](../media/contoso-win10/contoso-win10-fig1.png)

Denne infrastruktur består af:

- Configuration Manager, som:
  - Henter billeder til Windows 10 Enterprise pakker fra Microsoft Volume Licensing Center i Microsoft Network.
  - Er det centrale administrationspunkt for udrulningspakker.
- Regionale distributionspunkter, der typisk er placeret på Contosos regionale hubkontorer.
- Windows pc'er og enheder på forskellige placeringer, der modtager og installerer udrulningspakkerne til den lokale opgradering eller igangværende opdateringer baseret på gruppemedlemskab.

## <a name="next-step"></a>Næste trin

Få mere at vide om, hvordan Contoso udnytter sin Configuration Manager infrastruktur til at [udrulle og bevare aktuelle Microsoft 365 Apps for enterprise](contoso-o365pp.md) på tværs af organisationen. 

## <a name="see-also"></a>Se også

[Windows 10 Enterprise](/windows/deployment/)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Vejledninger til testlaboratorier](m365-enterprise-test-lab-guides.md)