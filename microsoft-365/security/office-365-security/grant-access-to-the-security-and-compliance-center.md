---
title: Giv brugere adgang til Security & Compliance Center
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
description: Brugere skal have tildelt tilladelser i Microsoft 365 Security & Compliance Center, før de kan administrere en af dens sikkerheds- eller overholdelsesfunktioner.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5af3d045b174c4405dc2060fea1db22b3b4066ac
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680681"
---
# <a name="give-users-access-to-the-security--compliance-center"></a>Giv brugere adgang til Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Brugere skal have tildelt tilladelser i Security & Compliance Center, før de kan administrere en af dens funktioner til sikkerhed eller overholdelse af regler og standarder. Som global administrator eller medlem af rollegruppen OrganizationManagement i Security & Compliance Center kan du give disse tilladelser til brugerne. Brugerne vil kun kunne administrere de sikkerheds- eller overholdelsesfunktioner, som du giver dem adgang til.

Du kan finde flere oplysninger om de forskellige tilladelser, du kan give brugere i Security & Compliance Center, under Tilladelser i [Security & Compliance Center](permissions-in-the-security-and-compliance-center.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du skal være global administrator eller medlem af rollegruppen OrganizationManagement i Security & Compliance Center for at fuldføre trinnene i denne artikel.

- Rollegrupper i Sikkerheds- & Overholdelsescenter kan have lignende navne som rollegrupperne i Exchange Online, men de er ikke de samme.

- Medlemskaber af rollegrupper deles ikke mellem Exchange Online og Security & Compliance Center.

- Delegerede adgangstilladelse (DAP)-partnere med Administrer på vegne af (AOBO)-tilladelser kan ikke få adgang til Sikkerheds- & Overholdelsescenter.

## <a name="use-the-security--compliance-center-to-give-another-user-access-to-the-security--compliance-center"></a>Brug Security & Compliance Center til at give en anden bruger adgang til Security & Compliance Center

1. Åbn Security & Compliance Center på, <https://protection.office.com> og gå derefter **til Tilladelser**. For at gå direkte til **fanen Tilladelser** skal du åbne <https://protection.office.com/permissions>.

2. Vælg rollegruppen på listen over rollegrupper, og klik derefter på **Rediger** ![redigeringsikon.](../../media/O365-MDM-CreatePolicy-EditIcon.gif)

3. På siden med egenskaber for rollegruppen under Medlemmer **skal du** klikke **på Tilføj**![ tilføjelsesikon.](../../media/ITPro-EAC-AddIcon.gif) og vælg navnet på den bruger (eller brugere), du vil tilføje.

4. Når du har valgt alle de brugere, du vil føje til rollegruppen, skal du klikke **på Tilføj-\>** og derefter **OK**.

5. Klik på **Gem**, når du er færdig.

## <a name="use-security--compliance-center-powershell-to-give-another-user-access-to-the-security--compliance-center"></a>Brug Security & Compliance Center PowerShell til at give en anden bruger adgang til Security & Compliance Center

1. [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Brug følgende syntaks:

   ```powershell
   Add-RoleGroupMember -Identity <RoleGroup> -Member <UserIdentity>

   - _Identity_ is the role group.
   - _Member_ is the user or universal security group (USG). You can specify only one member at a time.

   This example adds MatildaS to the Organization Management role group.

   ```PowerShell
   Add-RoleGroupMember -Identity "Organization Management" -Member MatildaS
   ```

Du kan finde detaljerede problemer med syntaks [og parameter i Add-RoleGroupMember](/powershell/module/exchange/add-rolegroupmember)

### <a name="how-do-you-know-this-worked"></a>Hvordan ved du, at det virkede?

Hvis du vil bekræfte, at du har tildelt adgang til Security & Compliance Center, skal du gøre et af følgende:

- I Security & Compliance Center skal du **gå til Tilladelser** og vælge rollegruppen. I pop op-vindue med oplysninger, der åbnes, skal du bekræfte medlemmerne af rollegruppen.

- I Security & Compliance Center PowerShell skal \<RoleGroupName\> du erstatte med navnet på rollegruppen og køre følgende kommando:

  ```powershell
  Get-RoleGroupMember -Identity "<RoleGroupName>"
  ```

  Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-RoleGroupMember](/powershell/module/exchange/Get-RoleGroupMember).