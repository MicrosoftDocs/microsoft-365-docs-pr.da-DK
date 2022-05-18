---
title: Microsoft Produktivitetsscore og indsigt i beskyttelse af personlige oplysninger
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
monikerRange: o365-worldwide
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
description: Sådan beskyttes beskyttelse af personlige oplysninger med produktivitetsscoren.
ms.openlocfilehash: 823e2cc087d3f0e9c486d8c0c4eca92ba42aee21
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467926"
---
# <a name="privacy-controls-for-productivity-score"></a>Kontrolelementer til beskyttelse af personlige oplysninger for produktivitetsscore

Produktivitetsscore giver indsigt i din organisations digitale transformationsrejse gennem brugen af Microsoft 365 og de teknologioplevelser, der understøtter den.  Din organisations score afspejler målingerne af person- og teknologioplevelsen og kan sammenlignes med benchmarks fra organisationer, der svarer til dine. Du kan finde flere oplysninger i [oversigten produktivitetsscore](productivity-score.md).

Dine personlige oplysninger er vigtige for Microsoft. Du kan få mere at vide om, hvordan vi beskytter dine personlige oplysninger, i [Microsofts erklæring om beskyttelse af personlige oplysninger](https://privacy.microsoft.com/privacystatement). Produktivitetsscore giver dig som din organisations it-administrator adgang til indstillinger for beskyttelse af personlige oplysninger for at sikre, at alle produktivitetsscoreoplysninger, du får vist, kan handles på, uden at det går ud over den tillid, som din organisation placerer i Microsoft.

I området personoplevelser er målepunkter kun tilgængelige på organisationsniveau. I dette område ser vi på, hvordan personer bruger Microsoft 365 ved at se på kategorierne indholdssamarbejde, mobilitet, møder, teamwork og kommunikation. Vi giver dig mulighed for at bruge flere niveauer af kontrolelementer, der kan hjælpe dig med at opfylde dine interne behov for politik om beskyttelse af personlige oplysninger.
Kontrolelementerne giver dig:

- Fleksible administratorroller til at styre, hvem der kan se oplysningerne i Produktivitetsscore.
- Muligheden for at fravælge personoplevelsesområdet.

## <a name="flexible-admin-roles-to-control-who-can-see-the-information-in-productivity-score"></a>Fleksible administratorroller til at styre, hvem der kan se oplysningerne i Produktivitetsscore

Hvis du vil have vist hele produktivitetsresultatet, skal du have en af følgende administratorroller:

- Global administrator
- Exchange administratorer
- SharePoint-administrator
- Skype for Business administrator
- Teams administrator
- Global læser
- Rapportlæser
- Læser af forbrugsoversigtsrapporter

Tildel rollen Rapportlæser eller Læser af oversigt over forbrugsrapporter til alle, der er ansvarlige for administration og implementering af ændringer, men ikke nødvendigvis en it-administrator. Denne rolle giver dem adgang til den komplette produktivitetsscore i Microsoft 365 Administration.

Rollen Rapportlæser for forbrugsoversigt skal tildeles via PowerShell-cmdlet'er, indtil den kan tildeles fra Microsoft 365 Administration senere i 2020.

Sådan tildeler du rollen Rapportlæser for forbrugsoversigt med PowerShell:

- Kør følgende PowerShell:

```powershell
Connect-AzureAD
Enable-AzureADDirectoryRole -RoleTemplateId '75934031-6c7e-415a-99d7-48dbd49e875e'
$role=Get-AzureADDirectoryRole -Filter "roleTemplateId eq '75934031-6c7e-415a-99d7-48dbd49e875e'"
Get-AzureADDirectoryRoleMember -ObjectId $role.ObjectId
$u=Get-AzureADUser -ObjectId <user upn>
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId $u.ObjectId
```

</br>


## <a name="capability-to-opt-out-of-people-experiences"></a>Mulighed for at fravælge personoplevelser

Du kan også fravælge personoplevelsesområdet for Produktivitetsscore. Hvis du fravælger, kan ingen fra din organisation få vist disse målepunkter, og din organisation fjernes fra alle beregninger, der involverer kommunikation, møder, teamwork, indholdssamarbejde og mobilitet. Du skal være global administrator for at fravælge rapporterne over personoplevelser i din organisation.

Sådan fravælger du:

1. I Administration skal du gå til **Indstillinger**  >   **Ellerg Indstillinger** >  **Produktivitetsscore**.
2. Fjern markeringen i afkrydsningsfeltet med teksten **Tillad, at Microsoft 365 forbrugsdata bruges til indsigt i brugeroplevelser**. Hvis du vil vide mere om, hvordan du ændrer indstillinger for datadeling for Endpoint Analytics i Intune konfigurationsstyring, skal du vælge **Få mere at vide**.
3. Vælg  **Gem**.

:::image type="content" source="../../media/orgsettingspageoptout.png" alt-text="Siden Med organisationsindstillinger, hvor du kan fravælge personoplevelser.":::
