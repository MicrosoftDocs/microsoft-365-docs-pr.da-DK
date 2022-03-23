---
title: Microsoft Productivity Score – beskyttelse af personlige oplysninger
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
description: Sådan beskyttes beskyttelse af personlige oplysninger med Produktivitetsscore.
ms.openlocfilehash: 94e0e1fb3190bc45fb0ad580cd823cb121fb60cf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594335"
---
# <a name="privacy-controls-for-productivity-score"></a>Kontrolelementer til beskyttelse af personlige oplysninger for Produktivitetsscore

Produktivitetsscore giver indsigt i din organisations digitale transformationsrejse gennem dens brug af Microsoft 365 og de teknologioplevelser, der understøtter den.  Organisationens resultat afspejler måleenheder for personer og teknologi og kan sammenlignes med benchmarks fra organisationer, der ligner din. Få mere at vide i Oversigt [over Produktivitetsscore](productivity-score.md).

Det er vigtigt for Microsoft, at du beskytter dine personlige oplysninger. Du kan få mere at vide om, hvordan vi beskytter dine personlige oplysninger, [i Microsofts erklæring om beskyttelse af personlige oplysninger](https://privacy.microsoft.com/privacystatement). Produktivitetsscore giver dig som din organisations it-administrator adgang til indstillinger for beskyttelse af personlige oplysninger for at sikre, at der kan handles på alle produktivitetsscoreoplysninger, du får vist, mens du ikke går på kompromis med den tillid, din organisation placerer i Microsoft.

I området med personers oplevelser er målepunkter kun tilgængelige på organisationsniveau. Dette område ser på, hvordan Microsoft 365 ved at se på kategorierne for indholdsamarbejde, mobilitet, møder, teamwork og kommunikation. Vi giver dig mulighed for at bruge flere niveauer af kontrolelementer til at hjælpe dig med at opfylde dine interne behov for politik om beskyttelse af personlige oplysninger.
Kontrolelementerne giver dig:

- Fleksible administratorroller til at styre, hvem der kan se oplysningerne i Produktivitetsscore.
- Muligheden for at fravælge personers oplevelsesområde.

## <a name="flexible-admin-roles-to-control-who-can-see-the-information-in-productivity-score"></a>Fleksible administratorroller til at styre, hvem der kan se oplysningerne i Produktivitetsscore

Hvis du vil have vist hele Produktivitetsscore, skal du have en af følgende administratorroller:

- Global administrator
- Exchange administratorer
- SharePoint administrator
- Skype for Business administrator
- Teams administrator
- Global læser
- Rapportlæser
- Læser til oversigt over brugsrapporter

Tildel rollen Rapportlæser eller Oversigt over brugsrapporter til alle, der er ansvarlige for administration og anvendelse af ændringer, men ikke nødvendigvis en it-administrator. Denne rolle giver dem adgang til den komplette produktivitetsscore-oplevelse Microsoft 365 Administration.

Rollen Læser til brugsoversigtsrapporter skal tildeles via PowerShell-cmdlet'er, før den kan tildeles fra Microsoft 365 Administration senere i 2020.

Sådan tildeles rollen Brugeroversigt over rapporter Reader med PowerShell:

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


## <a name="capability-to-opt-out-of-people-experiences"></a>Mulighed for at fravælge oplevelser med personer

Du kan også fravælge området personer, der oplever produktivitetsscore. Hvis du fravælger, vil ingen fra din organisation kunne se disse målepunkter, og din organisation fjernes fra enhver beregning, der involverer kommunikation, møder, teamwork, indholdsamarbejde og mobilitet. Du skal være global administrator for at fravælge rapporterne om personers oplevelser i organisationen.

Sådan fravælger du:

1. I Administration skal du gå **til Indstillinger**  >   **Org Indstillinger** >  **Productivity Score**.
2. Fjern et afkrydsningsfelt, hvor der står **Tillad, Microsoft 365 brugsdata skal bruges til personoplevelser**. For at forstå, hvordan du redigerer indstillinger for datadeling for Endpoint Analytics i Intune Configuration Manager, skal du vælge **Få mere at vide**.
3. Vælg  **Gem**.

:::image type="content" source="../../media/orgsettingspageoptout.png" alt-text="Siden Indstillinger for organisation, hvor du kan fravælge personers oplevelser.":::
