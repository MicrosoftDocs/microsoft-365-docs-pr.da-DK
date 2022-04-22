---
title: Oversigt over siden Threat Management i Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Få mere at vide om siden Trusselsstyring for udbydere af administrerede tjenester ved hjælp af Microsoft 365 Lighthouse.
ms.openlocfilehash: fea297845446bd8cbb14c81851afb5d51ce33717
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/21/2022
ms.locfileid: "65023343"
---
# <a name="overview-of-the-threat-management-page-in-microsoft-365-lighthouse"></a>Oversigt over siden Threat Management i Microsoft 365 Lighthouse 

**Gælder for:**

- Windows 10

Microsoft Defender Antivirus beskytter lejere, brugere og enheder mod softwaretrusler, herunder virus, malware og spyware. Den er robust, løbende beskyttelse, der er indbygget i Windows 10 og inkluderet i Microsoft 365 Business Premium og Microsoft365E3&nbsp;&nbsp;.  
  
Hvis du vil have adgang til siden Trusselsadministration i Microsoft 365 Lighthouse, skal du vælge **Threat Management** i venstre navigationsrude for at få vist dine kundelejere' sikkerhedsholdning mod trusler. Du får vist lejere, brugere og enheder, der kræver din opmærksomhed og anbefalinger, som kan hjælpe dig med at reducere risikoen.  
  
## <a name="overview-tab"></a>Fanen Oversigt  
  
På fanen Oversigt på siden Threat Management kan du overvåge antivirustilstanden på tværs af alle dine lejere for at identificere de områder, der kræver opmærksomhed.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-overview-tab.png" alt-text="Skærmbillede af fanen Oversigt.":::

## <a name="threats-tab"></a>Fanen Trusler

På fanen Trusler på siden Trusselsadministration kan du se de aktive, afhjælpede, løste og tilladte trusler på tværs af alle dine lejere. Du kan også afhjælpe flere trusler på samme tid på tværs af alle dine lejere ved at filtrere og analysere ned i hver trussel for at få mere at vide om, hvilke enheder, brugere eller lejere der påvirkes.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-threats-tab.png" alt-text="Skærmbillede af siden Standardgrundlinje.":::
  
Du kan filtrere trusler ved at:

- Trusselsstatus
- Alvorsgrad af trussel
- Trusselstype
- Datointerval

I følgende tabel vises de forskellige trusselsstatusser og deres definition:<br><br>

| Trusselsstatus | Definition |
|---|---|
| Aktive | Threat er aktiv på enheden. |
| Ingen status | Trusselsstatus er ikke tilgængelig. Kør en fuld scanning på enheden for at få Microsoft Defender Antivirus at identificere truslen igen. |
| Handlingen mislykkedes | Enheden er ikke i fare. En handling mislykkedes, men en potentiel trussel er stoppet og er ikke aktiv på enheden. Kør en fuld scanning på enheden. |
| Manuelle trin er påkrævet | Truslen er blevet stoppet, men det kræver et manuelt trin at fuldføre, f.eks. en fuld scanning eller en genstart af enheden. |
| Fuld scanning er påkrævet | En fuld scanning af enheden er påkrævet. |
| Genstart er påkrævet | Det er nødvendigt at genstarte enheden. |
| Afhjælpes med ikke-kritiske fejl | Truslen er blevet afhjulpet, og der er ikke behov for yderligere handlinger. |
| Karantæne | Truslen er sat i karantæne. Der kræves ingen yderligere handlinger. |
| Fjernet | Truslen er blevet fjernet fra enheden. Der kræves ingen yderligere handlinger. |
| Renset | Microsoft Defender Antivirus har gendannet og desinficeret filer. Der kræves ingen yderligere handlinger. |
| Tilladt | Truslen er tilladt af en administrator til at forblive på enheden. | 

## <a name="antivirus-protection-tab"></a>Fanen Antivirusbeskyttelse

Fanen Antivirusbeskyttelse på siden Administration af trusler viser enhederne på tværs af alle dine lejere og deres Microsoft Defender Antivirus beskyttelsestilstand. Du kan vurdere status og handle for en eller flere enheder, der kan være sårbare. Du kan også vælge en enhed for at få vist flere oplysninger, f.eks. enhedsoversigt, aktuelle trusler og statusser for enhedshandlinger.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-antivirus-tab.png" alt-text="Skærmbillede af fanen Antivirus.":::

## <a name="related-content"></a>Relateret indhold

[Udrul Microsoft 365 Lighthouse baselines](m365-lighthouse-deploy-baselines.md) (artikel)\
[ofte stillede spørgsmål om Microsoft 365 fyrtårn](m365-lighthouse-faq.yml) (artikel)
