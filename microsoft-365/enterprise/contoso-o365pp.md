---
title: Microsoft 365 Apps for enterprise installation af Contoso
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
description: Få mere at vide om, hvordan Contoso Microsoft Endpoint Configuration Manager til at installere Microsoft 365 Apps for enterprise.
ms.openlocfilehash: 6442deb0c6b7dce83a997bab28aa1c9cc85e8564
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588880"
---
# <a name="microsoft-365-apps-for-enterprise-deployment-for-contoso"></a>Microsoft 365 Apps for enterprise installation af Contoso

Contoso opgraderede deres pc'er til Windows 10 Enterprise og Microsoft 365 Apps for enterprise for at muliggøre mere effektivt samarbejde, bedre sikkerhed og en mere moderne computeroplevelse. Efter at have evalueret deres infrastruktur og forretningsmæssige behov identificerede Contoso disse nøglekrav til implementeringen:

- Alle pc'er skal køre Microsoft 365 Apps for enterprise.
- Installation skal bruge eksisterende administrationsværktøjer og infrastruktur, når det er muligt.
- Udrulning skal understøtte flere sprog og eksisterende arkitekturer på brugernes enheder.
- Pc'er skal holde sig opdateret og sikre med minimale it-administrative omkostninger og minimal indvirkning for brugerne.

## <a name="deployment-tools"></a>Udrulningsværktøjer

Afhængigt af deres krav valgte Contoso at installere Windows 10 Enterprise og Microsoft 365 Apps for enterprise via Konfigurationsstyring (Aktuel forgrening). Konfigurationsstyring til store miljøer og giver omfattende kontrol over installation, opdateringer og indstillinger. Den har også indbyggede funktioner, som gør det nemmere og mere effektivt at installere og administrere Office, herunder:

- Peer-cache, som kan hjælpe med begrænset netværkskapacitet, når du installerer på enheder på eksterne placeringer.
- Dashboardet Office klientadministration, hvilket gør det nemt at installere Office og overvåge opdateringer og giver administratorer adgang til de nyeste funktioner til installation og administration.
- Intelligent installation af sprogpakker, herunder automatisk udrulning af det samme sprog som operativsystemet.
- En fuldt understøttet og brugervenlig metode til at fjerne eksisterende versioner af Office fra en klient under installationen.

Ud over Konfigurationsstyring brugte Contoso Readiness [Toolkit til Office-tilføjelsesprogrammet og VBA](/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps), et gratis værktøj fra Microsoft, til at vurdere kompatibilitetsproblemer med deres Office-makroer og tilføjelsesprogrammet.

## <a name="managing-deployment-and-updates"></a>Administrere udrulning og opdateringer

Microsoft 365 Apps for enterprise har en ny udgivelsesmodel: Office som en tjeneste. Servicemodellen gør det nemt at holde dig opdateret med nye funktioner. Men det kræver ofte, at it-afdelinger ændrer måden, de installerer og tester nye versioner på. For at minimere kompatibilitetsproblemer og sikre, at deres computere holder sig opdateret, installeres Contoso Windows og Office i to faser:

- Først udrullede de Microsoft 365 Apps for enterprise et lille sæt af repræsentative enheder i hele organisationen. Denne pilotgruppe blev brugt til at teste apps, tilføjelsesprogrammer og hardware med Microsoft 365 Apps for enterprise.
- Fire måneder senere, efter at have adresseret alle kritiske problemer med apps, tilføjelsesprogrammer og hardware i pilotgruppen, installerede Contoso Microsoft 365 Apps for enterprise til resten af enhederne i organisationen (den brede gruppe).

I stedet for at administrere opdateringer Office opdateringer ved hjælp Konfigurationsstyring aktiverede Contoso automatiske opdateringer fra skyen. Skybaserede opdateringer reducerer administrativt arbejde og sikrer, at enhederne holder sig opdateret.

Contoso fulgte den samme fremgangsmåde i to trin for funktionsopdateringer, som de brugte til implementering af Office: Enheder i pilotgruppen modtog funktionsopdateringer fire måneder tidligere end enheder i resten af organisationen (den brede gruppe). For at aktivere dette for Office brugte Contoso to anbefalede [opdateringskanaler](/DeployOffice/overview-update-channels):

- Semi-Annual Virksomhedskanal (forhåndsvisning) for opdateringer til pilotgruppen
- Semi-Annual virksomhedskanal for opdateringer til den brede gruppe

Da Semi-Annual Enterprise-kanal (forhåndsvisning) udgiver en version af Microsoft 365 Apps for enterprise fire måneder tidligere end Semi-Annual Enterprise-kanalen, har Contoso tid til at validere opdateringerne uden at skulle administrere dem.

## <a name="deployment-process"></a>Installationsproces

For at fuldføre installationen af Office implementerede Contoso følgende proces, som indeholder anbefalinger om bedste praksis fra Microsoft:

1. Før installationen brugte Contoso Readiness Toolkit til tilføjelsesprogrammet Office og VBA til at teste deres apps og Office-tilføjelsesprogrammer for at vurdere deres kompatibilitet med Microsoft 365 Apps for enterprise.
1. I Konfigurationsstyring aktiverede de peer-cachen på deres klientenheder, hvilket hjælper med begrænset netværkskapacitet ved udrulning på klientenheder på eksterne placeringer. 
1. To installationsgrupper defineret af Contoso som enhedssamlinger i Konfigurationsstyring: en pilotgruppe og en bred gruppe. Pilotgruppen, som indeholdt et lille sæt repræsentative enheder i hele organisationen, blev brugt til yderligere test af apps, tilføjelsesprogrammer og hardware med Windows 10 Enterprise og Microsoft 365 Apps for enterprise.
1. De oprettede installationspakker til Office ved hjælp af Office-dashboardet til klientadministration og installationsguiden til Office 365, som begge er en del af Konfigurationsstyring-konsollen. De har opbygget Microsoft 365 Apps for enterprise-pakker, en til pilotgruppen på Semi-Annual Enterprise-kanalen (preview), og en til den brede gruppe på Semi-Annual Enterprise-kanal.
2. Hver Office pakke indeholdt engelsk, fransk og tysk sprogpakker. Hvis en enhed kræver et sprog, der ikke var inkluderet i Office-pakken, blev den pågældende sprogpakke automatisk downloadet fra Office Content Delivery Network (CDN).
3. De brugte den indbyggede funktion i Office til automatisk at fjerne alle eksisterende MSI-versioner af Office før de installerede Microsoft 365 Apps for enterprise.
4. I Konfigurationsstyring udrullede de Windows- Office-pakker til distributionspunkter på tværs af deres netværk. Derefter kørte de Konfigurationsstyring til installation for at udrulle pilotpakken Microsoft 365 Apps for enterprise til pilotgruppen.
5. Når de har løst kompatibilitetsproblemer med pilotgruppen, kørte Contoso opgavesekvenserne for at installere Microsoft 365 Apps for enterprise-pakken til den brede gruppe.

Da Contoso valgte at opdatere enheder automatisk fra skyen, var der ingen grund til at administrere processen Konfigurationsstyring. Deres enheder opdateres automatisk direkte fra skyen baseret på den opdateringskanal, der blev defineret i installationsstart.

Her er Contoso-Microsoft 365 Apps for enterprise installation og løbende opdateringsinstallationsarkitektur.

![Contoso-installationsinfrastrukturen til Microsoft 365 Apps for enterprise.](../media/contoso-o365pp/contoso-o365pp-fig1.png)
 
## <a name="next-step"></a>Næste trin

Få mere at vide om, hvordan Contoso bruger [Microsoft Intune](contoso-mdm.md) i Microsoft 365 til virksomheder til at administrere sine enheder og de apps, de kører på tværs af hele organisationen.

## <a name="see-also"></a>Se også

[Microsoft 365 Apps for enterprise](/deployoffice/deployment-guide-microsoft-365-apps)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Test labvejledninger](m365-enterprise-test-lab-guides.md)