---
title: Attributter for informationsbarrierer
description: Denne artikel er en reference til de Azure Active Directory, du kan bruge til at definere informationsbarrieresegmenter.
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
ms.openlocfilehash: 33143e85bf17a707ade6dd0d6d0c66886fd85373
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588931"
---
# <a name="information-barriers-attributes"></a>Attributter for informationsbarrierer

Visse attributter i Azure Active Directory kan bruges til at segmentere brugere. Når segmenter er defineret, kan disse segmenter bruges som filtre til politikker for informationsbarrierer. Du kan f.eks. bruge **Afdeling** til at definere segmenter af brugere efter afdeling i din organisation (det antages, at der ikke er enkelte medarbejdere, der arbejder for to afdelinger på samme tid).

Denne artikel beskriver, hvordan du bruger attributter med informationsbarrierer, og den indeholder en liste over attributter, der kan bruges. Du kan få mere at vide om informationsbarrierer i følgende ressourcer:

- [Informationsbarrierer](information-barriers.md)
- [Definer politikker for informationsbarrierer i Microsoft Teams](information-barriers-policies.md)
- [Rediger (eller fjern) politikker for informationsbarrierer](information-barriers-edit-segments-policies.md)

## <a name="how-to-use-attributes-in-information-barrier-policies"></a>Sådan bruger du attributter i politikker for informationsbarrierer

De attributter, der er angivet i denne artikel, kan bruges til at definere eller redigere brugersegmenter. Dine definerede segmenter fungerer som parametre (kaldet *UserGroupFilter-værdier* ) i [informationsbarrierepolitikker](information-barriers-policies.md).

1. Find ud af, hvilken attribut du vil bruge til at definere segmenter. Se afsnittet [Reference](#reference) i denne artikel.

2. Sørg for, at brugerkontiene har værdier udfyldt for den eller de attribut(er), du valgte i trin 1. Få vist oplysninger om brugerkontoen, og rediger om nødvendigt brugerkonti for at medtage attributværdier. 

    - Hvis du vil redigere flere konti (eller bruge PowerShell til at redigere en enkelt konto), skal du se Konfigurere egenskaber [for brugerkonti Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

    - Hvis du vil redigere en enkelt konto, [skal du se Tilføje eller opdatere en brugers profiloplysninger ved hjælp Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

3. [Definer segmenter ved hjælp af PowerShell](information-barriers-policies.md#define-segments-using-powershell) i stil med følgende eksempler:

    |**Eksempel**|**Cmdlet**|
    |:----------|:---------|
    | Definer et segment med navnet Segment1 ved hjælp af attributten Afdeling | `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "Department -eq 'Department1'"` |
    | Definer et segment med navnet SegmentA ved hjælp af attributten MemberOf (antag, at denne attribut indeholder gruppenavne, f.eks. "BlueGroup") | `New-OrganizationSegment -Name "SegmentA" -UserGroupFilter "MemberOf -eq 'BlueGroup'"` |
    | Definer et segment med navnet Day Automatisk brug af ExtensionAttribute1 (antag, at denne attribut indeholder jobtitler, f.eks. "Day Automatisk") | `New-OrganizationSegment -Name "DayTraders" -UserGroupFilter "ExtensionAttribute1 -eq 'DayTrader'"` |

    > [!TIP]
    > Når du definerer segmenter, skal du bruge den samme attribut for alle dine segmenter. Hvis du f.eks. definerer nogle segmenter ved hjælp *af Afdeling*, skal du definere alle segmenter ved hjælp af *Afdeling*. Definer ikke nogle segmenter ved hjælp af *Afdeling og* andre, der *bruger MemberOf*. Sørg for, at dine segmenter ikke overlapper. Hver bruger skal være tildelt præcis ét segment.

## <a name="reference"></a>Reference

I følgende tabel vises de attributter, du kan bruge med informationsbarrierer.

|**Azure Active Directory egenskabsnavn<br/>(LDAP-visningsnavn)**|**Exchange egenskabsnavn**|
|:---------------------------------------------------------------|:-------------------------|
| Co | Co |
| Firma | Firma |
| Afdeling | Afdeling |
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
| ProxyAddresses | Mailadresser |
| StreetAddress | StreetAddress |
| TargetAddress | ExternalEmailAddress |
| UsageLocation | UsageLocation |
| UserPrincipalName | UserPrincipalName |
| Mail | WindowsEmailAddress |
| Beskrivelse | Beskrivelse |
| MedlemAf | MemberOfGroup |

## <a name="resources"></a>Ressourcer

- [Definer politikker for informationsbarrierer i Microsoft Teams](information-barriers-policies.md)
- [Fejlfinding af informationsbarrierer](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)
- [Informationsbarrierer](information-barriers.md)