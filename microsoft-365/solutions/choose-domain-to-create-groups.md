---
title: Vælg det domæne, der skal bruges, når du opretter Microsoft 365-grupper
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
description: Få mere at vide om, hvordan du vælger det domæne, der skal bruges, når du opretter Microsoft 365-grupper, ved at konfigurere politikker for mailadresser ved hjælp af PowerShell.
ms.openlocfilehash: bd9fad340d136fe4cac228f94f1904761cff7071
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490891"
---
# <a name="choose-the-domain-to-use-when-creating-microsoft-365-groups"></a>Vælg det domæne, der skal bruges, når du opretter Microsoft 365-grupper

Nogle organisationer bruger separate maildomæner til at segmentere forskellige dele af deres virksomheder. Du kan angive, hvilket domæne der skal bruges, når brugerne opretter Microsoft 365-grupper.
  
Hvis din organisation har brug for, at brugerne skal oprette deres grupper i andre domæner end din virksomheds standard accepteret domæne, kan du tillade dette ved at konfigurere politikker for mailadresser ved hjælp af PowerShell.

Før du kan køre PowerShell-cmdlet'erne, skal du downloade og installere et modul, hvor du kan tale med din organisation. Se [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="example-scenarios"></a>Eksempelscenarier

Lad os sige, at din virksomheds hoveddomæne er Contoso.com. Men din organisations standard accepteret domæne er service.contoso.com. Det betyder, at grupper oprettes i service.contoso.com (f.eks. jimsteam@service.contoso.com).
  
Lad os sige, at du også har underdomæner konfigureret i din organisation. Du ønsker også, at grupper skal oprettes i disse domæner:
  
- students.contoso.com for studerende
    
- faculty.contoso.com for fakultetsmedlemmer
    
I følgende to scenarier forklares det, hvordan du kan opnå dette.

> [!NOTE]
> Når du har flere EAP'er, evalueres de i prioriteret rækkefølge. Værdien 1 betyder den højeste prioritet. Når en EAP matcher, evalueres ingen yderligere EAP, og adresser, der stemples på gruppen, er i henhold til den tilsvarende EAP. > Hvis ingen EAP'er opfylder de angivne kriterier, bliver gruppen klargjort i organisationens standard accepterede domæne. Se [Administrer accepterede domæner i Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) for at få oplysninger om, hvordan du tilføjer et accepteret domæne.
  
### <a name="scenario-1"></a>Scenarie 1

I følgende eksempel kan du se, hvordan du klargør alle Microsoft 365-grupper i din organisation i det groups.contoso.com domæne.
  
```
New-EmailAddressPolicy -Name Groups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@groups.contoso.com" -Priority 1
```

### <a name="scenario-2"></a>Scenarie 2

Lad os sige, at du vil styre, hvilke underdomæner Microsoft 365-grupper der oprettes i. Du ønsker:
  
- Grupper, der er oprettet af studerende (brugere, hvor **Afdeling er** angivet til **Studerende**) i domænet students.groups.contoso.com. Brug denne kommando:
    
  ```
  New-EmailAddressPolicy -Name StudentsGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Students'} -Priority 1
  ```

- Grupper, der er oprettet af fakultetsmedlemmer (brugere, hvor **afdelingen** er angivet til **fakultetsafdelingen eller mailadressen indeholder faculty.contoso.com)**) i domænet faculty.groups.contoso.com. Brug denne kommando:
    
  ```
  New-EmailAddressPolicy -Name FacultyGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@faculty.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Faculty' -or EmailAddresses -like "*faculty.contoso.com*"} -Priority 2
  ```

- Grupper, der er oprettet af andre, oprettes i domænet groups.contoso.com. Brug denne kommando:
    
  ```
  New-EmailAddressPolicy -Name OtherGroups -IncludeUnifiedGroupRecipients -EnabledPrimarySMTPAddressTemplate "SMTP:@groups.contoso.com" -Priority 3
  ```
> [!NOTE]
> Dette scenarie fungerer ikke, når MX-posten peger på filtrering af spam fra tredjepart.
 
## <a name="change-email-address-policies"></a>Skift politikker for mailadresse

Hvis du vil ændre skabelonerne for prioritet eller mailadresse for en eksisterende EAP, skal du bruge cmdlet'en Set-EmailAddressPolicy.
  
```
Set-EmailAddressPolicy -Name StudentsGroups -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com", "smtp:@students.contoso.com" ManagedByFilter {Department -eq 'Students'} -Priority 2

```

Ændring af en EAP har ingen indvirkning på de grupper, der allerede er klargjort.
  
## <a name="delete-email-address-policies"></a>Slet politikker for mailadresse

Hvis du vil slette en EAP, skal du bruge cmdlet'en Remove-EmailAddressPolicy.
  
```
Remove-EmailAddressPolicy -Identity StudentsGroups
```

Ændring af en EAP har ingen indvirkning på de grupper, der allerede er klargjort.
  
## <a name="hybrid-requirements"></a>Hybridkrav

Hvis din organisation er konfigureret i et hybridscenarie, skal du se [Konfigurer Microsoft 365-grupper med Exchange-hybrider](/exchange/hybrid-deployment/set-up-microsoft-365-groups) i det lokale miljø for at sikre, at din organisation opfylder kravene til oprettelse af Microsoft 365-grupper. 
  
## <a name="additional-info-about-using-email-address-policies-groups"></a>Yderligere oplysninger om brug af politikker for mailadresser:

Der er et par andre ting, du skal vide:
  
- Hvor hurtigt grupper oprettes, afhænger af antallet af EAP'er, der er konfigureret i din organisation.
    
- Administratorer og brugere kan også ændre domæner, når de opretter grupper.
    
- Gruppe af brugere bestemmes ved hjælp af de standardforespørgsler (brugeregenskaber), der allerede er tilgængelige. Se [Egenskaber, der kan filtreres for parameteren -RecipientFilter](/powershell/exchange/recipientfilter-properties) for understøttede egenskaber, der kan filtreres. 
    
- Hvis du ikke konfigurerer nogen EAP'er for grupper, vælges det standard accepterede domæne til oprettelse af grupper.
    
- Hvis du fjerner et accepteret domæne, skal du opdatere EAP'erne først, ellers påvirkes gruppeklargøring.
    
- Der kan konfigureres en maksimumgrænse på 100 politikker for mailadresser for en organisation.
    
## <a name="related-content"></a>Relateret indhold

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations) (artikel)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md) (artikel)

[Opret en Microsoft 365-gruppe i Administration](../admin/create-groups/create-groups.md) (artikel)
