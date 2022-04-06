---
title: Sammenlign grupper
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
description: Microsoft 365-medlemmer får en gruppemail og et delt arbejdsområde til samtaler, filer og kalenderbegivenheder, Stream og en Planner.
ms.openlocfilehash: 72da8af8acd0725a5d7509b84f08e4220f7772d4
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/01/2022
ms.locfileid: "64594703"
---
# <a name="compare-groups"></a>Sammenlign grupper

I sektionen <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupper**</a> i Microsoft 365 Administration kan du oprette og administrere disse typer af grupper: 

- **Microsoft 365-grupper** bruges til samarbejde mellem brugere, både i og uden for virksomheden. De omfatter samarbejdstjenester som f.SharePoint og Planner.
- **Distributionsgrupper** bruges til at sende mailbeskeder til en gruppe af personer.
- **Sikkerhedsgrupper** bruges til at give adgang til ressourcer, f.eks. SharePoint websteder.
- **Mailaktiverede sikkerhedsgrupper** bruges til at give adgang til ressourcer som f.eks SharePoint mailbeskeder og mailbeskeder til disse brugere.
- **Delte postkasser bruges** , når flere personer skal have adgang til den samme postkasse, f.eks. en firmaoplysninger eller en supportmailadresse.
- **Der oprettes** dynamiske distributionsgrupper for at fremskynde masseafsendelse af mails og andre oplysninger i en organisation.

Nogle grupper tillader dynamisk medlemskab eller mail.

||Microsoft 365-grupper|Distributionsgrupper|Sikkerhedsgrupper|Mailaktiverede sikkerhedsgrupper|Delte postkasser|Dynamiske distributionsgrupper|
|:----|:----|:----|:----|:----|:----|:----|
|**Mailaktiveret**|Ja|Ja|Nej|Ja|Ja|Ja|
|**Dynamisk medlemskab i Azure AD**|Ja|Nej|Ja|Nej|Nej|Nej|

Alle disse gruppetyper kan bruges sammen med Power Automate.

## <a name="microsoft-365-groups"></a>Microsoft 365-grupper

Microsoft 365-grupper bruges til samarbejde mellem brugere, både i og uden for virksomheden. For hver Microsoft 365 gruppe får medlemmer en gruppemail og et delt arbejdsområde til samtaler, filer og kalenderbegivenheder, Stream og en Planner.

Du kan føje personer uden for organisationen til en gruppe, så længe dette er blevet [aktiveret af administratoren](manage-guest-access-in-groups.md). Du kan også tillade eksterne afsendere at sende mails til gruppens mailadresse.

Microsoft 365-grupper kan konfigureres til dynamisk medlemskab af [Azure Active Directory](/azure/active-directory/users-groups-roles/groups-change-type), så gruppemedlemmer kan tilføjes eller fjernes automatisk baseret på brugerattributter som f.eks. afdeling, placering, titel osv.

Microsoft 365-grupper kan tilgås via mobilapps som f.eks. Outlook til iOS og Outlook til Android.

Gruppemedlemmer kan sende som eller sende på vegne af gruppens mailadresse, hvis dette er [blevet aktiveret af administratoren](../../solutions/allow-members-to-send-as-or-send-on-behalf-of-group.md).

Microsoft 365-grupper ikke indlejring med andre Microsoft 365-grupper eller med distributions- eller sikkerhedsgrupper.

Microsoft 365-grupper kan føjes til en af de tre SharePoint grupper (Ejere, Medlemmer eller Gæster) for at give personer tilladelser til webstedet.

## <a name="distribution-groups"></a>Distributionsgrupper

[Distributionsgrupper](/exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups) bruges til at sende meddelelser til en gruppe af personer. De kan modtage eksterne mails, hvis de er aktiveret af administratoren.

Distributionsgrupper er bedst til de situationer, hvor du har brug for at udsende oplysninger til en gruppe af personer, f.eks. "Personer i bygning A" eller "Alle i Contoso".

Distributionsgrupper kan [opgraderes til Microsoft 365-grupper](../manage/upgrade-distribution-lists.md).

Distributionsgrupper kan føjes til et team Microsoft Teams gruppemedlemmer, men kun medlemmerne tilføjes og ikke selve gruppen.

Microsoft 365-grupper kan ikke være medlemmer af distributionsgrupper.

## <a name="dynamic-distribution-groups"></a>Dynamiske distributionsgrupper 

[Dynamiske distributionsgrupper](/exchange/recipients-in-exchange-online/manage-dynamic-distribution-groups/manage-dynamic-distribution-groups) er mailaktiverede grupper, der bruges til at sende mails til personer med bestemte attributter, f.eks. afdeling eller placering. Disse attributter er defineret i Exchange Administration i stedet for Azure AD.

I modsætning til almindelige distributionsgrupper, der indeholder et defineret sæt medlemmer, beregnes medlemskabslisten for dynamiske distributionsgrupper, hver gang der sendes en meddelelse til gruppen, ud fra de filtre og betingelser, du definerer. Når en mail sendes til en dynamisk distributionsgruppe, leveres den til alle modtagere i organisationen, der opfylder de kriterier, der er defineret for den pågældende gruppe.

## <a name="security-groups"></a>Sikkerhedsgrupper

[Sikkerhedsgrupper](../email/create-edit-or-delete-a-security-group.md) bruges til at give adgang til Microsoft 365, f.eks. SharePoint. De kan gøre administrationen nemmere, fordi du kun behøver at administrere gruppen i stedet for at føje brugere til hver enkelt ressource enkeltvis.

Sikkerhedsgrupper kan indeholde brugere eller enheder. Oprettelse af en sikkerhedsgruppe til enheder kan bruges med administrationstjenester til mobilenheder, f.eks. Intune.

Sikkerhedsgrupper kan konfigureres til dynamisk medlemskab af [Azure Active Directory](/azure/active-directory/users-groups-roles/groups-change-type), så gruppemedlemmer eller enheder kan tilføjes eller fjernes automatisk baseret på brugerattributter som f.eks. afdeling, placering eller titel eller enhedsattributter som f.eks. operativsystemversion.

Sikkerhedsgrupper kan føjes til et team.

Microsoft 365-grupper kan ikke være medlemmer af sikkerhedsgrupper.

## <a name="mail-enabled-security-groups"></a>Mailaktiverede sikkerhedsgrupper

Mailaktiverede sikkerhedsgrupper fungerer på samme måde som almindelige sikkerhedsgrupper, bortset fra at de ikke kan administreres dynamisk via Azure Active Directory ikke indeholde enheder.

De omfatter muligheden for at sende mails til alle gruppens medlemmer.

Mailaktiverede sikkerhedsgrupper kan føjes til et team.

## <a name="shared-mailboxes"></a>Delte postkasser

[Delte postkasser](../email/create-a-shared-mailbox.md) bruges, når flere personer skal have adgang til den samme postkasse, f.eks. en firmaoplysninger eller en supportmailadresse, receptionsdesk eller andre funktioner, som kan deles af flere personer.

Delte postkasser kan modtage eksterne mails, hvis administratoren har aktiveret dette.

Delte postkasser indeholder en kalender, der kan bruges til samarbejde.

Brugere med tilladelser til gruppepostkassen kan sende som eller sende på vegne af postkassemailadressen, hvis administratoren har givet den pågældende bruger tilladelse til at gøre det. Dette er især nyttigt til hjælp og supportpostkasser, fordi brugere kan sende mails fra "Contoso Support" eller "Building A Reception Desk".

Det er ikke muligt at overføre en delt postkasse til en Microsoft 365 gruppe.

## <a name="related-content"></a>Relateret indhold

[Få mere at vide Microsoft 365-grupper](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Opgrader distributionslister Microsoft 365-grupper i Outlook](/microsoft-365/admin/manage/upgrade-distribution-lists)

[Derfor skal du opgradere dine distributionslister til grupper i Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)
