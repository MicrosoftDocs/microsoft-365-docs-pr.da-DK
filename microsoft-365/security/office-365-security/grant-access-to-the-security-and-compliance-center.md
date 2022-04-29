---
title: Giv brugerne adgang til Security & Compliance Center
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.PermissionsHelp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 2cfce2c8-20c5-47f9-afc4-24b059c1bd76
description: Brugerne skal have tildelt tilladelser i Microsoft 365 Security & Compliance Center, før de kan administrere nogen af dets sikkerheds- eller overholdelsesfunktioner.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5bf2f6f99af13de0858b041807f01e25e3516da8
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130752"
---
# <a name="give-users-access-to-the-security--compliance-center"></a>Giv brugerne adgang til Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Brugerne skal have tildelt tilladelser i Security & Compliance Center, før de kan administrere nogen af dets sikkerheds- eller overholdelsesfunktioner. Som global administrator eller medlem af rollegruppen OrganizationManagement i Security & Compliance Center kan du give disse tilladelser til brugerne. Brugerne kan kun administrere de sikkerheds- eller overholdelsesfunktioner, du giver dem adgang til.

Du kan få flere oplysninger om de forskellige tilladelser, du kan give til brugere i Security & Compliance Center, [under Tilladelser i Security & Compliance Center](permissions-in-the-security-and-compliance-center.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du skal være global administrator eller medlem af rollegruppen OrganizationManagement i Security & Compliance Center for at fuldføre trinnene i denne artikel.

- Rollegrupper for Security & Compliance Center kan have navne, der ligner rollegrupperne i Exchange Online, men de er ikke ens.

- Medlemskaber af rollegrupper deles ikke mellem Exchange Online og Security & Compliance Center.

- DAP-partnere (Delegated Access Permission) med Administration på vegne af (AOBO) kan ikke få adgang til Security & Compliance Center.

## <a name="use-the-security--compliance-center-to-give-another-user-access-to-the-security--compliance-center"></a>Brug Security & Compliance Center til at give en anden bruger adgang til Security & Compliance Center

1. Åbn Security & Compliance Center på , <https://protection.office.com> og gå derefter til **Tilladelser**. Hvis du vil gå direkte til fanen **Tilladelser** , skal du åbne <https://protection.office.com/permissions>.

2. Vælg rollegruppen på listen over rollegrupper, og klik derefter på **Rediger** ![ikonet Rediger.](../../media/O365-MDM-CreatePolicy-EditIcon.gif)

3. På siden med egenskaber for rollegruppen under **Medlemmer** skal du klikke på **Tilføjikon**![.](../../media/ITPro-EAC-AddIcon.gif) og vælg navnet på den bruger (eller de brugere), du vil tilføje.

4. Når du har valgt alle de brugere, du vil føje til rollegruppen, skal du klikke på **Tilføj og\>** derefter **PÅ OK**.

5. Klik på **Gem**, når du er færdig.

## <a name="use-security--compliance-center-powershell-to-give-another-user-access-to-the-security--compliance-center"></a>Brug Security & Compliance Center PowerShell til at give en anden bruger adgang til Security & Compliance Center

1. [Forbind til PowerShell & Security & Compliance Center](/powershell/exchange/connect-to-scc-powershell).

2. Brug følgende syntaks:

   ```powershell
   Add-RoleGroupMember -Identity <RoleGroup> -Member <UserIdentity>

   - _Identity_ is the role group.
   - _Member_ is the user or universal security group (USG). You can specify only one member at a time.

   This example adds MatildaS to the Organization Management role group.

   ```PowerShell
   Add-RoleGroupMember -Identity "Organization Management" -Member MatildaS
   ```

Du kan finde detaljerede syntaks- og parameterproblemer under [Add-RoleGroupMember](/powershell/module/exchange/add-rolegroupmember)

### <a name="how-do-you-know-this-worked"></a>Hvordan ved du, det virkede?

Benyt en af følgende fremgangsmåder for at bekræfte, at du har givet adgang til Security & Compliance Center:

- I Security & Compliance Center skal du gå til **Tilladelser** og vælge rollegruppen. Kontrollér medlemmerne af rollegruppen i det pop op-vindue med detaljer, der åbnes.

- I Security & Compliance Center skal du erstatte \<RoleGroupName\> med navnet på rollegruppen og køre følgende kommando:

  ```powershell
  Get-RoleGroupMember -Identity "<RoleGroupName>"
  ```

  Du kan finde detaljerede syntaks- og parameteroplysninger under [Get-RoleGroupMember](/powershell/module/exchange/Get-RoleGroupMember).
