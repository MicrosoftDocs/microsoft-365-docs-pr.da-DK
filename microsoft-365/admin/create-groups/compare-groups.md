---
title: Sammenligne grupper
ms.reviewer: arvaradh
f1.keywords: CSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 758759ad-63ee-4ea9-90a3-39f941897b7d
description: Medlemmer af Microsoft 365-gruppen får en gruppemail og et delt arbejdsområde til samtaler, filer og kalenderhændelser, Stream og en Planner.
ms.openlocfilehash: cf66d4b2b2aab903934a87f64f53fa485d82f572
ms.sourcegitcommit: c314e989202dc1c9c260fffd459d53bc1f08514e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66717640"
---
# <a name="compare-groups"></a>Sammenligne grupper

I afsnittet <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupper**</a> i Microsoft 365 Administration kan du oprette og administrere disse typer grupper: 

- **Microsoft 365-grupper** bruges til samarbejde mellem brugere, både i og uden for din virksomhed. De omfatter samarbejdstjenester som SharePoint og Planner.
- **Distributionsgrupper** bruges til at sende mailmeddelelser til en gruppe personer.
- **Sikkerhedsgrupper** bruges til at tildele adgang til ressourcer som f.eks. SharePoint-websteder.
- **Mailaktiverede sikkerhedsgrupper** bruges til at give adgang til ressourcer som SharePoint og mailmeddelelser til disse brugere.
- **Delte postkasser** bruges, når flere personer skal have adgang til den samme postkasse, f.eks. firmaoplysninger eller supportmailadresse.
- **Dynamiske distributionsgrupper** oprettes for at fremskynde massesending af mails og andre oplysninger i en organisation.

Nogle grupper tillader dynamisk medlemskab eller mail.

||Microsoft 365-grupper|Distributionsgrupper|Sikkerhedsgrupper|Mailaktiverede sikkerhedsgrupper|Delte postkasser|Dynamiske distributionsgrupper|
|:----|:----|:----|:----|:----|:----|:----|
|**Mailaktiveret**|Ja|Ja|Nej|Ja|Ja|Ja|
|**Dynamisk medlemskab i Azure AD**|Ja|Nej|Ja|Nej|Nej|Nej|

Alle disse gruppetyper kan bruges sammen med Power Automate.

## <a name="microsoft-365-groups"></a>Microsoft 365-grupper

Microsoft 365-grupper bruges til samarbejde mellem brugere både i og uden for din virksomhed. For hver Microsoft 365-gruppe får medlemmer en gruppemail og et delt arbejdsområde til samtaler, filer og kalenderbegivenheder, Stream og en Planner.

Du kan føje personer uden for din organisation til en gruppe, så længe denne er [blevet aktiveret af administratoren](manage-guest-access-in-groups.md). Du kan også tillade, at eksterne afsendere sender mail til gruppens mailadresse.

Microsoft 365-grupper kan [konfigureres til dynamisk medlemskab i Azure Active Directory](/azure/active-directory/users-groups-roles/groups-change-type), så gruppemedlemmer kan tilføjes eller fjernes automatisk på baggrund af brugerattributter som afdeling, placering, titel osv.

Microsoft 365-grupper kan tilgås via mobilapps, f.eks Outlook til iOS og Outlook til Android.

Gruppemedlemmer kan sende som eller sende på vegne af gruppens mailadresse, hvis dette er [blevet aktiveret af administratoren](../../solutions/allow-members-to-send-as-or-send-on-behalf-of-group.md).

Microsoft 365-grupper understøtter indlejring via [dynamiske grupper i Azure Active Directory](/azure/active-directory/enterprise-users/groups-dynamic-rule-member-of).

Microsoft 365-grupper kan føjes til en af de tre SharePoint-grupper (ejere, medlemmer eller besøgende) for at give personer tilladelser til webstedet.

## <a name="distribution-groups"></a>Distributionsgrupper

[Distributionsgrupper](/exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups) bruges til at sende meddelelser til en gruppe personer. De kan modtage eksterne mails, hvis de er aktiveret af administratoren.

Distributionsgrupper er bedst til situationer, hvor du har brug for at udsende oplysninger til en bestemt gruppe personer, f.eks. "Personer i bygning A" eller "Alle på Contoso".

Distributionsgrupper kan [opgraderes til Microsoft 365-grupper](../manage/upgrade-distribution-lists.md).

Distributionsgrupper kan føjes til et team i Microsoft Teams, selvom det kun er medlemmerne, der tilføjes, og ikke selve gruppen.

Microsoft 365-grupper kan ikke være medlem af distributionsgrupper.

## <a name="dynamic-distribution-groups"></a>Dynamiske distributionsgrupper 

[Dynamiske distributionsgrupper](/exchange/recipients-in-exchange-online/manage-dynamic-distribution-groups/manage-dynamic-distribution-groups) er mailaktiverede grupper, der bruges til at sende mail til personer med bestemte attributter, f.eks. afdeling eller placering. Disse attributter defineres i Exchange Administration i stedet for Azure AD.

I modsætning til almindelige distributionsgrupper, der indeholder et defineret sæt medlemmer, beregnes medlemskabslisten for dynamiske distributionsgrupper, hver gang der sendes en meddelelse til gruppen, baseret på de filtre og betingelser, du definerer. Når der sendes en mail til en dynamisk distributionsgruppe, leveres den til alle modtagere i organisationen, der opfylder de kriterier, der er defineret for den pågældende gruppe.

## <a name="security-groups"></a>Sikkerhedsgrupper

[Sikkerhedsgrupper](../email/create-edit-or-delete-a-security-group.md) bruges til at tildele adgang til Microsoft 365-ressourcer, f.eks. SharePoint. De kan gøre administrationen nemmere, fordi du kun skal administrere gruppen i stedet for at føje brugere til hver ressource enkeltvist.

Sikkerhedsgrupper kan indeholde brugere eller enheder. Oprettelse af en sikkerhedsgruppe for enheder kan bruges sammen med tjenester til administration af mobilenheder, f.eks. Intune.

Sikkerhedsgrupper kan [konfigureres til dynamisk medlemskab i Azure Active Directory](/azure/active-directory/users-groups-roles/groups-change-type), så gruppemedlemmer eller enheder kan tilføjes eller fjernes automatisk på baggrund af brugerattributter, f.eks. afdeling, placering eller titel. eller enhedsattributter, f.eks. operativsystemversionen.

Sikkerhedsgrupper kan føjes til et team.

Microsoft 365-grupper kan ikke være medlem af sikkerhedsgrupper.

## <a name="mail-enabled-security-groups"></a>Mailaktiverede sikkerhedsgrupper

Mailaktiverede sikkerhedsgrupper fungerer på samme måde som almindelige sikkerhedsgrupper, bortset fra at de ikke kan administreres dynamisk via Azure Active Directory og ikke kan indeholde enheder.

De omfatter muligheden for at sende mails til alle medlemmer af gruppen.

Mailaktiverede sikkerhedsgrupper kan føjes til et team.

## <a name="shared-mailboxes"></a>Delte postkasser

[Delte postkasser](../email/create-a-shared-mailbox.md) bruges, når flere personer skal have adgang til den samme postkasse, f.eks. en firmaoplysninger eller supportmailadresse, receptionsskranke eller en anden funktion, der kan deles af flere personer.

Delte postkasser kan modtage eksterne mails, hvis administratoren har aktiveret dette.

Delte postkasser indeholder en kalender, der kan bruges til samarbejde.

Brugere med tilladelser til gruppepostkassen kan sende som eller sende på vegne af postkassens mailadresse, hvis administratoren har givet denne bruger tilladelse til at gøre det. Dette er især nyttigt i forbindelse med postkasser til hjælp og support, fordi brugerne kan sende mails fra "Contoso Support" eller "Oprettelse af et receptionsskrivebord".

Det er ikke muligt at overføre en delt postkasse til en Microsoft 365-gruppe.

## <a name="related-content"></a>Relateret indhold

[Få mere at vide om Microsoft 365-grupper](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Opgrader distributionslister til Microsoft 365-grupper i Outlook](/microsoft-365/admin/manage/upgrade-distribution-lists)

[Derfor skal du opgradere distributionslisterne til grupper i Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)
