---
title: Administrere Microsoft 365 lejere med Windows PowerShell for DAP-partnere
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: I denne artikel kan du lære, hvordan du bruger PowerShell Microsoft 365 til at administrere dine kundeaniteter.
ms.openlocfilehash: ff74cc0ec710996c66a659034f4fb4a49ee57ab1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594222"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Administrere Microsoft 365 lejere med Windows PowerShell for DAP-partnere (Delegated Access Permissions)

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Windows PowerShell gør det muligt for Syndication- og Cloud Solution Provider-partnere nemt at administrere og rapportere om indstillinger for kundemåleevne, der ikke er tilgængelige i Microsoft 365 Administration. Bemærk, at Administrer på vegne af (AOBO)-tilladelser er påkrævet, for at partneradministratorkontoen kan oprette forbindelse til dens kundeancies.

Delegerede adgangstilladelsespartnere (DAP) er Syndication- og Skyløsningsudbydere (CSP-partnere). De er ofte netværks- eller telekommunikationsudbydere til andre virksomheder. They bundle Microsoft 365 subscriptions into their service offerings to their customers. Når de sælger et Microsoft 365-abonnement, tildeles de automatisk Administrer på vegne af (AOBO)-tilladelser til kundens tilladelser, så de kan administrere og rapportere om kundens tilladelser.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

Fremgangsmåderne i dette emne kræver, at du opretter forbindelse [Forbind til Microsoft 365 med PowerShell](connect-to-microsoft-365-powershell.md).

Du skal også have legitimationsoplysninger som partnerlejeradministrator.

## <a name="what-do-you-want-to-do"></a>Hvad vil du gøre?

### <a name="list-all-tenant-ids"></a>Vis alle lejer-iD'er

> [!NOTE]
> Hvis du har mere end 500 lejere, kan du ændre området for cmdlet-syntaksen med enten  _-All_ eller _-MaxResultsParameter_. Dette gælder for andre cmdlet'er, der kan give et stort output, f.eks **. Get-MsolUser**.

Kør denne kommando for at få vist alle kundelejer-id'er, du har adgang til.

```powershell
Get-MsolPartnerContract -All | Select-Object TenantId
```

Dette viser en oversigt over alle dine kundelejere efter **TenantId**.

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory til Windows PowerShell og cmdlet'er med **Msol** i deres navn. Hvis du vil fortsætte med at bruge disse cmdlet'er, skal du køre dem fra Windows PowerShell.
>

### <a name="get-a-tenant-id-by-using-the-domain-name"></a>Få et lejer-id ved hjælp af domænenavnet

Kør denne **kommando for at hente TenantId'et** for en bestemt kundelejer efter domænenavn. _Erstat<domainname.onmicrosoft.com>_ med det faktiske domænenavn for den ønskede kundelejer.

```powershell
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>Vis alle domæner for en lejer

Kør denne kommando for at få alle domæner for én kundelejer. Erstat  _\<customer TenantId value>_ med den faktiske værdi.

```powershell
Get-MsolDomain -TenantId <customer TenantId value>
```

Hvis du har registreret flere domæner, returneres alle domæner, der er knyttet til **kundens TenantId**.

### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>Få tilknytning af alle lejere og registrerede domæner

I den tidligere PowerShell til Microsoft 365-kommandoer viste du, hvordan du kan hente enten lejer-iD'er eller domæner, men ikke begge på samme tid, og uden nogen klar tilknytning mellem dem alle. Denne kommando genererer en oversigt over alle dine kundelejer-app'er og deres domæner.

```powershell
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>Hent alle brugere for en lejer

Dette viser **UserPrincipalName**, **DisplayName** og **isLicensed-status** for alle brugere for en bestemt lejer. Erstat _\<customer TenantId value>_ med den faktiske værdi.

```powershell
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>Få alle oplysninger om en bruger

Hvis du vil se alle egenskaberne for en bestemt bruger, skal du køre denne kommando. Erstat  _\<customer TenantId value>_ _\<user principal name value>_ og med de faktiske værdier.

```powershell
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>Tilføj brugere, angiv indstillinger, og tildel licenser

Masseoprettelse, -konfiguration og -licensering for Microsoft 365 effektiv ved at bruge PowerShell til Microsoft 365. I denne totrinsproces skal du først oprette poster for alle de brugere, du vil tilføje i en fil med kommaseparerede værdier (CSV), og derefter importere filen ved hjælp af PowerShell til Microsoft 365.

#### <a name="create-a-csv-file"></a>Opret en CSV-fil

Opret en CSV-fil ved hjælp af dette format:

`UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`

hvor:

- **UsageLocation**: Værdien for dette er brugerens ISO-lande-/områdekode på to bogstaver. Lande-/områdekoder kan søges påISO [Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). Koden for USA er f.eks. USA, og koden for Brasilien er BR.

- **LicenseAssignment**: Værdien for dette bruger dette format: `syndication-account:<PROVISIONING_ID>`. Hvis du f.eks. tildeler O365_Business_Premium-licenser til lejere, ser værdien **LicenseAssignment** således ud: **syndication-account:O365_Business_Premium**. Du finder de PROVISIONING_IDs i Syndication-partnerportalen, som du har adgang til som Syndication- eller CSP-partner.

#### <a name="import-the-csv-file-and-create-the-users"></a>Importér CSV-filen, og opret brugerne

Når du har oprettet CSV-filen, skal du køre denne kommando for at oprette brugerkonti med adgangskoder, der ikke udløber, som brugeren skal ændre ved første logon, og som tildeler den licens, du angiver. Sørg for at erstatte det korrekte CSV-filnavn.

```powershell
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>Se også

[Hjælp til partnere](https://go.microsoft.com/fwlink/p/?LinkId=533477)
