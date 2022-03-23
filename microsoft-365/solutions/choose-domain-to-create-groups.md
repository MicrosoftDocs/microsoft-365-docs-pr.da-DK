---
title: Vælg det domæne, der skal bruges, når du Microsoft 365 grupper
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 7cf5655d-e523-4bc3-a93b-3ccebf44a01a
recommendations: false
description: Lær at vælge det domæne, der skal bruges, når Microsoft 365 grupper, ved at konfigurere mailadressepolitikker ved hjælp af PowerShell.
ms.openlocfilehash: 31b84304643190f343ae9ee74a947ecf6741f135
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/17/2021
ms.locfileid: "63594201"
---
# <a name="choose-the-domain-to-use-when-creating-microsoft-365-groups"></a>Vælg det domæne, der skal bruges, når du Microsoft 365 grupper

Nogle organisationer bruger separate maildomæner til at segmentere forskellige dele af deres forretninger. Du kan angive, hvilket domæne der skal bruges, når brugerne opretter Microsoft 365 grupper.
  
Hvis organisationen har brug for, at brugerne opretter deres grupper på andre domæner end det standard accepterede domæne for din virksomhed, kan du tillade dette ved at konfigurere mailadressepolitikker (EUP'er) ved hjælp af PowerShell.

Før du kan køre PowerShell-cmdletterne, skal du downloade og installere et modul, der giver dig mulighed for at tale med din organisation. Se, [Forbind du Exchange Online bruge Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="example-scenarios"></a>Eksempelscenarier

Lad os sige, at din virksomheds hoveddomæne er Contoso.com. Men organisationens standard accepterede domæne er service.contoso.com. Det betyder, at grupper oprettes i service.contoso.com (f.eks. jimsteam@service.contoso.com).
  
Lad os sige, at du også har underdomæner konfigureret i organisationen. Du vil også gerne have, at der oprettes grupper på disse domæner:
  
- students.contoso.com for studerende
    
- faculty.contoso.com til fakultetsmedlemmer
    
De følgende to scenarier forklarer, hvordan du vil gøre dette.

> [!NOTE]
> Når du har flere EUP'er, evalueres de efter prioritet. En værdi på 1 betyder højeste prioritet. Når en EAP matcher, evalueres der ingen yderligere EAP, og adresser, der bliver stemplet på gruppen, er i henhold til den matchede EAP. > Hvis ingen EUP'er opfylder de angivne kriterier, bliver gruppen klargjort på organisationens standard accepterede domæne. Se Administrer [accepterede domæner i Exchange Online for at](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) få mere at vide om, hvordan du tilføjer et accepteret domæne.
  
### <a name="scenario-1"></a>Scenarie 1

Følgende eksempel viser, hvordan du klargør alle Microsoft 365 grupper i organisationen på groups.contoso.com domæne.
  
```
New-EmailAddressPolicy -Name Groups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@groups.contoso.com" -Priority 1
```

### <a name="scenario-2"></a>Scenarie 2

Lad os sige, at du vil styre, hvilke underdomæner Microsoft 365 grupper oprettes i. Du ønsker:
  
- Grupper, der er oprettet af studerende (brugere **, der har Afdeling** **indstillet** til Studerende) på students.groups.contoso.com domæne. Brug denne kommando:
    
  ```
  New-EmailAddressPolicy -Name StudentsGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Students'} -Priority 1
  ```

- Grupper oprettet af fakultetsmedlemmer ( **brugere, der** har Afdeling angivet til Fakultet eller mailadresse **indeholder faculty.contoso.com)**) på faculty.groups.contoso.com domæne. Brug denne kommando:
    
  ```
  New-EmailAddressPolicy -Name FacultyGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@faculty.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Faculty' -or EmailAddresses -like "*faculty.contoso.com*"} -Priority 2
  ```

- Grupper, der er oprettet af andre, oprettes i groups.contoso.com domæne. Brug denne kommando:
    
  ```
  New-EmailAddressPolicy -Name OtherGroups -IncludeUnifiedGroupRecipients -EnabledPrimarySMTPAddressTemplate "SMTP:@groups.contoso.com" -Priority 3
  ```

## <a name="change-email-address-policies"></a>Ændre mailadressepolitikker

Hvis du vil ændre prioriteten eller mailadresseskabelonerne for en eksisterende EAP, skal du Set-EmailAddressPolicy cmdlet'en.
  
```
Set-EmailAddressPolicy -Name StudentsGroups -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com", "smtp:@students.contoso.com" ManagedByFilter {Department -eq 'Students'} -Priority 2

```

Ændring af en EAP har ingen indflydelse på de grupper, der allerede er blevet klargjort.
  
## <a name="delete-email-address-policies"></a>Slet mailadressepolitikker

Hvis du vil slette en EAP, skal du Remove-EmailAddressPolicy en cmdlet.
  
```
Remove-EmailAddressPolicy -Identity StudentsGroups
```

Ændring af en EAP har ingen indflydelse på de grupper, der allerede er blevet klargjort.
  
## <a name="hybrid-requirements"></a>Hybridkrav

Hvis din organisation er konfigureret i et hybridscenarie, skal du se Konfigurer [Microsoft 365-grupper med lokal Exchange hybrid](/exchange/hybrid-deployment/set-up-microsoft-365-groups) for at sikre, at din organisation opfylder kravene til oprettelse af Microsoft 365 grupper. 
  
## <a name="additional-info-about-using-email-address-policies-groups"></a>Flere oplysninger om brug af mailadressepolitikker for grupper:

Der er flere ting, du skal vide:
  
- Hvor hurtigt grupper oprettes, afhænger af antallet af ESP'er, der er konfigureret i organisationen.
    
- Administratorer og brugere kan også redigere domæner, når de opretter grupper.
    
- Gruppe af brugere bestemmes ved hjælp af standardforespørgsler (brugeregenskaber), der allerede er tilgængelige. Se [Filtrerbare egenskaber for parameteren -RecipientFilter for understøttede](/powershell/exchange/recipientfilter-properties) egenskaber, der kan filtreres. 
    
- Hvis du ikke konfigurerer nogen EUP'er for grupper, vælges det standard accepterede domæne til gruppeoprettelse.
    
- Hvis du fjerner et accepteret domæne, skal du opdatere EUP'er først, ellers vil klargøring af grupper blive påvirket.
    
- Der kan konfigureres en maksimumgrænse på 100 mailadressepolitikker for en organisation.
    
## <a name="related-content"></a>Relateret indhold

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations) (artikel)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md) (artikel)

[Opret en Microsoft 365 gruppe i Administration](../admin/create-groups/create-groups.md) (artikel)