---
title: Microsoft 365 Apps for enterprise installation for Contoso
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
description: Forstå, hvordan Contoso bruger Microsoft Endpoint Configuration Manager til at udrulle Microsoft 365 Apps for enterprise.
ms.openlocfilehash: 8b6fb639083145c728870156d848b75897483d25
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096540"
---
# <a name="microsoft-365-apps-for-enterprise-deployment-for-contoso"></a>Microsoft 365 Apps for enterprise installation for Contoso

Contoso opgraderede deres pc'er til Windows 10 Enterprise og Microsoft 365 Apps for enterprise for at muliggøre mere effektivt samarbejde, bedre sikkerhed og en mere moderne skrivebordsoplevelse. Efter at have vurderet deres infrastruktur- og forretningsbehov identificerede Contoso disse vigtige krav til udrulningen:

- Alle pc'er skal køre Microsoft 365 Apps for enterprise.
- Udrulningen skal bruge eksisterende administrationsværktøjer og infrastruktur, når det er muligt.
- Installationen skal understøtte flere sprog og eksisterende arkitekturer på brugernes enheder.
- Pc'er bør holde sig ajour og sikre med minimale administrative it-omkostninger og minimal indvirkning på brugerne.

## <a name="deployment-tools"></a>Installationsværktøjer

På baggrund af deres krav valgte Contoso at udrulle Windows 10 Enterprise og Microsoft 365 Apps for enterprise via Configuration Manager (Current Branch). Configuration Manager skaleres til store miljøer og giver stor kontrol over installation, opdateringer og indstillinger. Den har også indbyggede funktioner, der gør det nemmere og mere effektivt at udrulle og administrere Office, herunder:

- Peer-cache, som kan hjælpe med begrænset netværkskapacitet, når der udrulles til enheder på eksterne placeringer.
- Dashboardet Office Klientadministration, som gør det nemt at udrulle Office og overvåge opdateringer og give administratorer adgang til de nyeste udrulnings- og administrationsfunktioner.
- Udrulning af intelligent sprogpakke, herunder automatisk installation af det samme sprog som operativsystemet.
- En fuldt understøttet og brugervenlig metode til fjernelse af eksisterende versioner af Office fra en klient under installationen.

Ud over Configuration Manager brugte Contoso [Readiness Toolkit til Office tilføjelsesprogrammer og VBA](/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps), et gratis værktøj fra Microsoft, til at vurdere kompatibilitetsproblemer med deres Office makroer og tilføjelsesprogrammer.

## <a name="managing-deployment-and-updates"></a>Administration af udrulning og opdateringer

Microsoft 365 Apps for enterprise har en ny udgivelsesmodel: Office som en tjeneste. Tjenestemodellen gør det nemt at holde dig ajour med nye funktioner. Men det kræver ofte, at it-afdelinger ændrer, hvordan de udruller og tester nye udgivelser. Contoso udrullede Windows og Office i to faser for at minimere kompatibilitetsproblemer og sikre, at deres computere forbliver opdateret:

- Først udrullede de Microsoft 365 Apps for enterprise til et lille sæt repræsentative enheder på tværs af organisationen. Denne pilotgruppe blev brugt til at teste apps, tilføjelsesprogrammer og hardware med Microsoft 365 Apps for enterprise.
- Fire måneder senere udrullede Contoso efter at have håndteret alle kritiske problemer med apps, tilføjelsesprogrammer og hardware i pilotgruppen Microsoft 365 Apps for enterprise til resten af enhederne i organisationen (den brede gruppe).

I stedet for at administrere opdateringer til Office ved hjælp af Configuration Manager aktiverede Contoso automatiske opdateringer fra cloudmiljøet. Skybaserede opdateringer reducerer de administrative omkostninger, samtidig med at det sikres, at enhederne er opdaterede.

Contoso fulgte den samme totrinstilgang til funktionsopdateringer, som de brugte til udrulning af Office: Enheder i pilotgruppen modtog funktionsopdateringer fire måneder tidligere end enheder i resten af organisationen (den brede gruppe). For at aktivere dette for Office brugte Contoso to anbefalede [opdateringskanaler](/DeployOffice/overview-update-channels):

- Semi-Annual Enterprise Channel (prøveversion) for at få opdateringer til pilotgruppen
- Semi-Annual Enterprise Channel for at få opdateringer til den brede gruppe

Da Semi-Annual Enterprise Channel (prøveversion) udgiver en version af Microsoft 365 Apps for enterprise fire måneder tidligere end Semi-Annual Enterprise Channel, har Contoso tid til at validere opdateringerne uden at skulle administrere dem.

## <a name="deployment-process"></a>Installationsproces

For at fuldføre udrulningen af Office implementerede Contoso følgende proces, som omfatter anbefalinger til bedste praksis fra Microsoft:

1. Før udrulningen brugte Contoso Readiness Toolkit til Office-tilføjelsesprogrammet og VBA til at teste deres apps og Office tilføjelsesprogrammer for at vurdere deres kompatibilitet med Microsoft 365 Apps for enterprise.
1. I Configuration Manager aktiverede de peercache på deres klientenheder, hvilket hjælper med begrænset netværkskapacitet, når de udrulles på klientenheder på eksterne placeringer. 
1. Contoso definerede to udrulningsgrupper som enhedssamlinger i Configuration Manager: en pilotgruppe og en bred gruppe. Pilotgruppen, som omfattede et lille sæt repræsentative enheder på tværs af organisationen, blev brugt til yderligere test af apps, tilføjelsesprogrammer og hardware med Windows 10 Enterprise og Microsoft 365 Apps for enterprise.
1. De har oprettet installationspakker til Office ved hjælp af dashboardet Office Klientadministration og guiden Office 365 Installation, som begge er en del af Configuration Manager-konsollen. De har bygget to Microsoft 365 Apps for enterprise pakker, én til pilotgruppen på Semi-Annual Enterprise Channel (prøveversion) og en til den brede gruppe på Semi-Annual Enterprise Channel.
2. Hver Office pakke omfattede engelsk, fransk og tysk sprogpakker. Hvis en enhed krævede et sprog, der ikke var inkluderet i Office-pakken, blev sprogpakken automatisk downloadet fra Office Content Delivery Network (CDN).
3. De brugte den indbyggede funktion i Office-pakken til automatisk at fjerne alle eksisterende MSI-versioner af Office, før de installerede Microsoft 365 Apps for enterprise.
4. I Configuration Manager udrullede de Windows og Office pakker til distributionspunkter på tværs af deres netværk. Derefter kørte de sekvenserne af Configuration Manager udrulningsopgaven for at installere pilot-Microsoft 365 Apps for enterprise-pakken i pilotgruppen.
5. Når de har løst kompatibilitetsproblemer med pilotgruppen, kørte Contoso opgavesekvenserne for at installere Microsoft 365 Apps for enterprise-pakken til den brede gruppe.

Da Contoso valgte automatisk at opdatere enheder fra cloudmiljøet, var det ikke nødvendigt at administrere processen i Configuration Manager. Deres enheder opdateres automatisk direkte fra det cloudbaserede baseret på den opdateringskanal, der blev defineret i den indledende udrulning.

Her er Contoso-Microsoft 365 Apps for enterprise-installationen og den løbende opdateringsarkitektur.

![Contoso-installationsinfrastrukturen for Microsoft 365 Apps for enterprise.](../media/contoso-o365pp/contoso-o365pp-fig1.png)
 
## <a name="next-step"></a>Næste trin

Få mere at vide om, hvordan Contoso [bruger Microsoft Intune](contoso-mdm.md) i Microsoft 365 for virksomheder til at administrere sine enheder og de apps, de kører på tværs af organisationen.

## <a name="see-also"></a>Se også

[Microsoft 365 Apps for enterprise](/deployoffice/deployment-guide-microsoft-365-apps)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Vejledninger til testlaboratorier](m365-enterprise-test-lab-guides.md)