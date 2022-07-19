---
title: Enhedens tilstande
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: c3ac23c5-d4b4-4b1b-b7ce-ea759521bf8c
description: Få mere at vide om de forskellige enhedstilstande på listen Enhedshandlinger i Administration startside i Microsoft 365 til virksomheder.
ms.openlocfilehash: 07024ea6f4e37e32716c8af3e56f4481104ed975
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66858826"
---
# <a name="device-states-in-microsoft-365-for-business"></a>Enhedstilstande i Microsoft 365 til virksomheder

Denne artikel gælder for Microsoft 365 Business Premium.

> [!NOTE]
> Microsoft Defender til virksomheder udrulles til Microsoft 365 Business Premium kunder fra den 1. marts 2022. Dette tilbud indeholder yderligere sikkerhedsfunktioner til enheder. [Få mere at vide om Defender for Business](../security/defender-business/mdb-overview.md).

Enheder på listen **Enhedshandlinger** (Administration **startenhedshandlinger**\>) kan have følgende tilstande.
  
![På listen Enhedshandlinger kan du se enhedernes tilstande.](./../media/a621c47e-45d9-4e1a-beb9-c03254d40c1d.png)
  
|**Status**|**Beskrivelse**|
|:-----|:-----|
|Administreret af Intune  |Administreret af Microsoft 365 Business Premium.  |
|Afventer tilbagetrækning  |Microsoft 365 Business Premium er ved at gøre klar til at fjerne firmadata fra enheden.  |
|Udgå i gang  |Microsoft 365 Business Premium fjerner i øjeblikket firmadata fra enheden.  |
|Tilbagetrækning mislykkedes  | Det lykkedes ikke at fjerne firmadatahandlingen.  |
|Tilbagetrækning annulleret  |Tilbagetrækningshandlingen blev annulleret.  |
|Afventer sletning  |Venter på, at fabriksnulstillingen starter.  |
|Sletning er i gang  |Fabriksnulstilling er udstedt.  |
|Sletning mislykkedes  |Fabriksnulstillingen kunne ikke udføres.  |
|Sletning annulleret  |Fabrikssletning blev annulleret.  |
|Usunde  |En handling venter (eller er i gang), men enheden har ikke tjekket ind i mere end 30 dage.  |
|Slet ventende  |Sletningshandlingen afventer.  |
|Opdaget  |Microsoft 365 Business Premium har registreret enheden.  |
   

## <a name="see-also"></a>Se også

[Bedste praksis for sikring af Microsoft 365 til virksomheder-planer](../admin/security-and-compliance/secure-your-business-data.md)