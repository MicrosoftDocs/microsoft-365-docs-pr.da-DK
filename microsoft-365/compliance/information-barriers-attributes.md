---
title: Attributter for informationsbarrierer
description: Denne artikel er en reference til attributterne for Azure Active Directory-brugerkontoen, som du kan bruge til at definere informationsbarrieresegmenter.
keywords: Microsoft 365, Microsoft Purview, overholdelse af angivne standarder, informationsbarrierer
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a1549a0cb3bf03056b37a75175c3b24416bec7b5
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639770"
---
# <a name="information-barriers-attributes"></a>Attributter for informationsbarrierer

Visse attributter i Azure Active Directory kan bruges til at segmentere brugere i informationsbarrierer (IB). Når segmenter er defineret, kan disse segmenter bruges som filtre for IB-politikker. Du kan f.eks. bruge **Afdeling** til at definere segmenter af brugere efter afdeling i din organisation (forudsat at ingen enkelt medarbejder arbejder for to afdelinger på samme tid).

I denne artikel beskrives det, hvordan du bruger attributter med informationsbarrierer, og den indeholder en liste over attributter, der kan bruges. Du kan få mere at vide om informationsbarrierer i følgende ressourcer:

- [Informationsbarrierer](information-barriers.md)
- [Definer politikker for informationsbarrierer i Microsoft Teams](information-barriers-policies.md)
- [Rediger (eller fjern) IB-politikker](information-barriers-edit-segments-policies.md)

## <a name="how-to-use-attributes-in-ib-policies"></a>Sådan bruger du attributter i IB-politikker

De attributter, der er angivet i denne artikel, kan bruges til at definere eller redigere segmenter af brugere. Dine definerede segmenter fungerer som parametre (kaldet *UserGroupFilter-værdier* ) i [IB-politikker](information-barriers-policies.md).

1. Find ud af, hvilken attribut du vil bruge til at definere segmenter. Se afsnittet [Reference](#reference) i denne artikel.

2. Sørg for, at der er udfyldt værdier for de attribut(er), du valgte i trin 1, på brugerkontiene. Få vist oplysninger om brugerkontoen, og rediger evt. brugerkonti for at inkludere attributværdier. 

    - Hvis du vil redigere flere konti (eller bruge PowerShell til at redigere en enkelt konto), skal du se [Konfigurer egenskaber for brugerkonto med Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

    - Hvis du vil redigere en enkelt konto, skal du se [Tilføj eller opdater en brugers profiloplysninger ved hjælp af Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

3. [Definer segmenter ved hjælp af PowerShell](information-barriers-policies.md#define-segments-using-powershell) på samme måde som følgende eksempler:

    |**Eksempel**|**Cmdlet**|
    |:----------|:---------|
    | Definer et segment med navnet Segment1 ved hjælp af attributten Afdeling | `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "Department -eq 'Department1'"` |
    | Definer et segment kaldet SegmentA ved hjælp af attributten MemberOf (lad os antage, at denne attribut indeholder gruppenavne, f.eks. "BlueGroup") | `New-OrganizationSegment -Name "SegmentA" -UserGroupFilter "MemberOf -eq 'BlueGroup'"` |
    | Definer et segment med navnet DayTraders ved hjælp af ExtensionAttribute1 (lad os antage, at denne attribut indeholder jobtitler, f.eks. "DayTrader") | `New-OrganizationSegment -Name "DayTraders" -UserGroupFilter "ExtensionAttribute1 -eq 'DayTrader'"` |

    > [!TIP]
    > Når du definerer segmenter, skal du bruge den samme attribut for alle dine segmenter. Hvis du f.eks. definerer nogle segmenter ved hjælp af *Afdeling*, skal du definere alle de segmenter, der bruger *Afdeling*. Definer ikke nogle segmenter ved hjælp af *Afdeling* og andre, der bruger *MemberOf*. Sørg for, at dine segmenter ikke overlapper hinanden. hver bruger skal tildeles nøjagtigt ét segment.

## <a name="reference"></a>Reference

I følgende tabel vises de attributter, du kan bruge sammen med informationsbarrierer.

|**Azure Active Directory-egenskabsnavn<br/> (vist navn på LDAP)**|**Navn på Exchange-egenskab**|
|:---------------------------------------------------------------|:-------------------------|
| Co | Co |
| Virksomhed | Virksomhed |
| Institut | Institut |
| ExtensionAttribute1 | CustomAttribute1 |
| ExtensionAttribute2 | CustomAttribute2 |
| ExtensionAttribute3 | CustomAttribute3 |
| ExtensionAttribute4 | CustomAttribute4 |
| ExtensionAttribute5 | CustomAttribute5 |
| ExtensionAttribute6 | CustomAttribute6 |
| ExtensionAttribute7 | CustomAttribute7 |
| ExtensionAttribute8 | CustomAttribute8 |
| ExtensionAttribute9 | CustomAttribute9 |
| ExtensionAttribute10 | CustomAttribute10 |
| ExtensionAttribute11 | CustomAttribute11 |
| ExtensionAttribute12 | CustomAttribute12 |
| ExtensionAttribute13 | CustomAttribute13 |
| ExtensionAttribute14 | CustomAttribute14 |
| ExtensionAttribute15 | CustomAttribute15 |
| MSExchExtensionCustomAttribute1 | ExtensionCustomAttribute1 |
| MSExchExtensionCustomAttribute2 | ExtensionCustomAttribute2 |
| MSExchExtensionCustomAttribute3 | ExtensionCustomAttribute3 |
| MSExchExtensionCustomAttribute4 | ExtensionCustomAttribute4 |
| MSExchExtensionCustomAttribute5 | ExtensionCustomAttribute5 |
| MailNickname | Alias |
| PhysicalDeliveryOfficeName | Office |
| Postnummer | Postnummer |
| ProxyAdresser | Mailadresser |
| Gadeadresse | Gadeadresse |
| Targetaddress | ExternalEmailAddress |
| UsageLocation | UsageLocation |
| UserPrincipalName | UserPrincipalName |
| Mail | WindowsEmailAddress |
| Beskrivelse | Beskrivelse |
| Medlem af | MemberOfGroup |

## <a name="resources"></a>Ressourcer

- [Definer politikker for informationsbarrierer i Microsoft Teams](information-barriers-policies.md)
- [Fejlfinding af informationsbarrierer](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)
- [Informationsbarrierer](information-barriers.md)
