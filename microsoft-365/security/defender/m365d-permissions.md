---
title: Administrere adgang til Microsoft 365 Defender data i Microsoft 365 Defender portalen
description: Få mere at vide om, hvordan du administrerer tilladelser til data Microsoft 365 Defender
keywords: adgang, tilladelser, Microsoft 365 Defender, M365, security, MCAS, Cloud App Security, Microsoft Defender for Endpoint, scope, scoping, RBAC
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 8e9cacf3fb7d74acc210ac0b77ed5e68c7a93961
ms.sourcegitcommit: 2c3b737e71038f843ef9e9ff4d5b99d6110b8ec5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/28/2022
ms.locfileid: "63595855"
---
# <a name="manage-access-to-microsoft-365-defender-with-azure-active-directory-global-roles"></a>Administrer adgang til Microsoft 365 Defender med Azure Active Directory globale roller

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Der er to måder at administrere adgang til Microsoft 365 Defender:
- **Globale Azure Active Directory (AD) roller**
- **Brugerdefineret rolleadgang**

Konti, der er tildelt **følgende globale Azure Active Directory (AD)-** roller, kan Microsoft 365 Defender adgang til funktioner og data:
- Global administrator
- Sikkerhedsadministrator
- Sikkerhedsoperator
- Global læser
- Sikkerhedslæser

Hvis du vil gennemse konti med disse [roller, skal du se Tilladelser i Microsoft 365 Defender portal](https://security.microsoft.com/permissions).

**Brugerdefineret** rolleadgang er en ny funktion i Microsoft 365 Defender og gør det muligt at administrere adgang til bestemte data, opgaver og funktioner i Microsoft 365 Defender. Brugerdefinerede roller giver mere kontrol end globale Azure AD-roller, hvilket giver brugerne kun den adgang, de skal bruge, med de mindst nødvendige roller.  Brugerdefinerede roller kan oprettes ud over de globale Azure AD-roller. [Få mere at vide om brugerdefinerede roller](custom-roles.md).

> [!NOTE]
> Denne artikel gælder kun for administration af globale Azure Active Directory rolleroller. Du kan finde flere oplysninger om brug af brugerdefineret rollebaseret adgangskontrol i [Brugerdefinerede roller for rollebaseret adgangskontrol](custom-roles.md)

## <a name="access-to-functionality"></a>Adgang til funktioner
Adgang til bestemte funktioner bestemmes af din [Azure AD-rolle](/azure/active-directory/roles/permissions-reference). Kontakt en global administrator, hvis du har brug for adgang til bestemte funktioner, der kræver, at du eller din brugergruppe skal tildeles en ny rolle.

### <a name="approve-pending-automated-tasks"></a>Godkend ventende automatiserede opgaver
[Automatiseret undersøgelse og afhjælpning kan](m365d-autoir-actions.md) handle på mails, videresendelsesregler, filer, vedholdenhedsmekanismer og andre artefakter, der er fundet under undersøgelser. Hvis du vil godkende eller afvise afventende handlinger, der kræver udtrykkelig godkendelse, skal bestemte roller være tildelt Microsoft 365. Du kan få mere at vide [under Tilladelser for handlingscenter](m365d-action-center.md#required-permissions-for-action-center-tasks).

## <a name="access-to-data"></a>Adgang til data
Adgang til Microsoft 365 Defender data kan styres ved hjælp af det omfang, der er tildelt brugergrupper i RBAC (Microsoft Defender for Endpoint Role-Based Access Control). Hvis din adgang ikke er fastsat til et bestemt sæt enheder i Defender for Endpoint, har du fuld adgang til data i Microsoft 365 Defender. Men når din konto er begrænset, kan du kun se data om enhederne i dit omfang.

Hvis du f.eks. kun tilhører én brugergruppe med en Microsoft Defender til slutpunkt-rolle, og den pågældende brugergruppe kun har adgang til salgsenheder, vil du kun få vist data om salgsenheder i Microsoft 365 Defender. [Få mere at vide om RBAC-indstillinger i Microsoft Defender til slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/rbac)

### <a name="microsoft-defender-for-cloud-apps-access-controls"></a>Adgangskontrolelementer for Microsoft Defender til skyapps
Under forhåndsvisningen gennemtvinger Microsoft 365 Defender adgangskontrol, der er baseret på indstillingerne for Defender til skyapps. Adgang til Microsoft 365 Defender data påvirkes ikke af disse indstillinger.

## <a name="related-topics"></a>Relaterede emner
- [Brugerdefinerede roller i rollebaseret adgangskontrol for Microsoft 365 Defender](custom-roles.md)
- [Indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference)
- [Microsoft Defender for Endpoint RBAC](/windows/security/threat-protection/microsoft-defender-atp/rbac)
- [Roller for Defender til skyapps](/cloud-app-security/manage-admins)
