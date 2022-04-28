---
title: Administrer Microsoft 365 lejere med Windows PowerShell for DAP-partnere
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: I denne artikel kan du få mere at vide om, hvordan du bruger PowerShell til Microsoft 365 til at administrere dine kundelejer.
ms.openlocfilehash: 11869157a5ed106d1aea0a4ce0e21716be1cc78f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096782"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Administrer Microsoft 365 lejere med Windows PowerShell for DAP-partnere (Delegated Access Permissions)

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Windows PowerShell gør det nemt for syndikerings- og Cloud Solution Provider-partnere (CSP) at administrere og rapportere om indstillinger for kundeleje, der ikke er tilgængelige i Microsoft 365 Administration. Bemærk, at der kræves tilladelser til administration på vegne af (AOBO), for at partneradministratorkontoen kan oprette forbindelse til kundens lejere.

DAP-partnere (Delegated Access Permission) er syndikerings- og CSP-partnere (Cloud Solution Providers). De er ofte netværks- eller telekommunikationsudbydere til andre virksomheder. De bundter Microsoft 365 abonnementer i deres servicetilbud til deres kunder. Når de sælger et Microsoft 365 abonnement, tildeles de automatisk tilladelserne Administrer på vegne af (AOBO) til kundens lejere, så de kan administrere og rapportere om kundens lejere.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

Procedurerne i dette emne kræver, at du opretter forbindelse til [Forbind for at Microsoft 365 med PowerShell](connect-to-microsoft-365-powershell.md).

Du skal også bruge legitimationsoplysningerne for din partnerlejeradministrator.

## <a name="what-do-you-want-to-do"></a>Hvad vil du foretage dig?

### <a name="list-all-tenant-ids"></a>Vis alle lejer-id'er

> [!NOTE]
> Hvis du har mere end 500 lejere, skal du udvide cmdlet-syntaksen med enten  _-All_ eller _-MaxResultsParameter_. Dette gælder for andre cmdlet'er, der kan give et stort output, f.eks **. Get-MsolUser**.

Kør denne kommando for at få vist alle kundelejer-id'er, som du har adgang til.

```powershell
Get-MsolPartnerContract -All | Select-Object TenantId
```

Dette viser en liste over alle dine kundelejere efter **TenantId**.

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell moduler og cmdlet'er med **Msol** i deres navn. Hvis du vil fortsætte med at bruge disse cmdlet'er, skal du køre dem fra Windows PowerShell.
>

### <a name="get-a-tenant-id-by-using-the-domain-name"></a>Hent et lejer-id ved hjælp af domænenavnet

Hvis du vil hente **TenantId** for en bestemt kundelejer efter domænenavn, skal du køre denne kommando. Erstat _<domainname.onmicrosoft.com>_ med det faktiske domænenavn for den ønskede kundelejer.

```powershell
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>Vis alle domæner for en lejer

Hvis du vil hente alle domæner for en hvilken som helst kundelejer, skal du køre denne kommando. Erstat  _\<customer TenantId value>_ med den faktiske værdi.

```powershell
Get-MsolDomain -TenantId <customer TenantId value>
```

Hvis du har registreret yderligere domæner, returnerer dette alle domæner, der er knyttet til **kundens TenantId**.

### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>Hent en tilknytning af alle lejere og registrerede domæner

De tidligere PowerShell til Microsoft 365-kommandoer viste dig, hvordan du henter enten lejer-id'er eller domæner, men ikke begge dele på samme tid, og uden nogen klar tilknytning mellem dem alle. Denne kommando genererer en liste over alle dine kundelejer-id'er og deres domæner.

```powershell
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>Hent alle brugere for en lejer

Dette viser **UserPrincipalName**, **DisplayName** og statussen **isLicensed** for alle brugere for en bestemt lejer. Erstat _\<customer TenantId value>_ med den faktiske værdi.

```powershell
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>Få alle oplysninger om en bruger

Hvis du vil se alle egenskaberne for en bestemt bruger, skal du køre denne kommando. Erstat  _\<customer TenantId value>_ og _\<user principal name value>_ med de faktiske værdier.

```powershell
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>Tilføj brugere, angiv indstillinger, og tildel licenser

Masseoprettelse, konfiguration og licensering af Microsoft 365 brugere er særligt effektiv ved hjælp af PowerShell til Microsoft 365. I denne proces med to trin skal du først oprette poster for alle de brugere, du vil tilføje, i en fil med kommaseparerede værdier (CSV) og derefter importere filen ved hjælp af PowerShell til Microsoft 365.

#### <a name="create-a-csv-file"></a>Opret en CSV-fil

Opret en CSV-fil i dette format:

`UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`

Hvor:

- **UsageLocation**: Værdien for dette er brugerens ISO-lande-/områdekode på to bogstaver. Lande-/områdekoderne kan slås op på [platformen til onlinebrowsing iISO](https://go.microsoft.com/fwlink/p/?LinkId=532703). Koden for USA er f.eks. USA, og koden for Brasilien er BR.

- **LicenseAssignment**: Værdien for dette bruger dette format: `syndication-account:<PROVISIONING_ID>`. Hvis du f.eks. tildeler brugere af kundelejer O365_Business_Premium licenser, ser værdien **LicenseAssignment** ud på følgende måde: **syndikeringskonto:O365_Business_Premium**. Du finder de PROVISIONING_IDs på Syndication Partner Portal, som du har adgang til som syndikerings- eller CSP-partner.

#### <a name="import-the-csv-file-and-create-the-users"></a>Importér CSV-filen, og opret brugerne

Når du har oprettet din CSV-fil, skal du køre denne kommando for at oprette brugerkonti med adgangskoder, der ikke udløber, som brugeren skal ændre ved første logon, og som tildeler den licens, du angiver. Sørg for at erstatte det korrekte CSV-filnavn.

```powershell
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>Se også

[Hjælp til partnere](https://go.microsoft.com/fwlink/p/?LinkId=533477)
