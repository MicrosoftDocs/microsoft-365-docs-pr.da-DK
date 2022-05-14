---
title: Forstå abonnementer og licenser i Microsoft 365 til virksomheder
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: shegu, nicholak
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_licensing
- okr_smb
- AdminSurgePortfolio
- manage_licenses
- AdminTemplateSet
search.appverid: MET150
description: De programmer og tjenester, du modtager, afhænger af, hvilke Microsoft 365 produkt du har købt, f.eks. Microsoft 365 Apps for business.
ms.date: 05/12/2022
ms.openlocfilehash: 48186847368af2bc43831c6e27ef7d347981f1b3
ms.sourcegitcommit: 4e7ff69f4d7d27c2d419f763cfcb069e3b0d0d9f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/13/2022
ms.locfileid: "65403222"
---
# <a name="understand-subscriptions-and-licenses-in-microsoft-365-for-business"></a>Forstå abonnementer og licenser i Microsoft 365 til virksomheder

Når du køber et abonnement på Microsoft 365 til virksomheder, tilmelder du dig et sæt apps og tjenester, som du betaler for enten månedligt eller årligt. De programmer og tjenester, du modtager som en del af dit abonnement, afhænger af, hvilket produkt du har købt, f.eks. Microsoft 365 Apps for business eller Microsoft 365 Business Standard. Du kan se, hvad der følger med hvert produkt på [siden Microsoft 365 til små og mellemstore virksomheder](https://products.office.com/compare-all-microsoft-office-products?&activetab=tab:primaryr1).

Når du køber et abonnement, angiver du det antal licenser, du har brug for, baseret på, hvor mange personer du har i din organisation. Når du har købt et abonnement, opretter du konti for personer i din organisation og tildeler derefter en licens til hver enkelt person. I takt med at organisationens behov ændres, kan du købe flere licenser for at imødekomme nye personer eller tildele licenser til andre brugere, når nogen forlader organisationen.

Hvis du har mere end ét abonnement, kan du tildele licenser til forskellige personer for hvert abonnement. Du kan f.eks. tildele alle dine brugere til alle Microsoft 365 programmer og tjenester som en del af et Microsoft 365 Business Standard abonnement. Du kan også tildele et undersæt af brugere til Visio Online via et separat Visio abonnement.

## <a name="how-many-devices-can-people-install-office-on"></a>Hvor mange enheder kan personer installere Office på?

Hvis dit abonnement indeholder et af følgende produkter, kan hver person installere Office på op til fem pc'er eller Mac, fem tablets og fem telefoner.

:::row:::
   :::column span="":::
        - Microsoft 365 Apps for business - Microsoft 365 Apps for enterprise - Microsoft 365 Business Standard - Microsoft 365 Business Premium - Microsoft 365 A3 - Microsoft 365 A5
   :::column-end:::
   :::column span="":::
        - Microsoft 365 E3 - Microsoft 365 E5 - Office 365 A1 Plus - Office 365 A3 - Office 365 A5 - Office 365 E3 - Office 365 E5
   :::column-end:::
:::row-end:::

## <a name="what-happens-when-you-assign-a-license-to-someone"></a>Hvad sker der, når du tildeler en licens til en person?

Følgende tabel viser, hvad der automatisk sker, når du tildeler en licens til en person:
  
|Hvis abonnementet har denne tjeneste|Dette sker automatisk|
|:-----|:-----|
|Exchange Online|Der oprettes en postkasse for den pågældende person. <br/> Hvis du vil vide mere om SLA'en for, at denne opgave kan fuldføres, skal du se ["Konfiguration..." meddelelser i Microsoft 365 Administration](https://support.microsoft.com/help/2635238/setting-up-messages-in-the-office-365-admin-center). |
|SharePoint Online|Redigeringstilladelser til standardwebstedet for SharePoint Onlineteam tildeles til den pågældende person.|
|Skype for Business Online|Personen har adgang til de funktioner, der er knyttet til licensen.|
|Microsoft 365 Apps for enterprise og Microsoft 365 Apps for business|Personen kan downloade Office apps på op til fem Macs eller pc'er, fem tablets og fem smartphones.|

## <a name="understand-licenses-for-non-user-mailboxes"></a>Forstå licenser til postkasser, der ikke er bruger

Du behøver ikke at tildele licenser til ressourcepostkasser, lokalepostkasser og delte postkasser, medmindre de har overskredet deres lagerkvote på 50 gigabyte (GB). Du kan få mere at vide om postkasser, der ikke er bruger, i følgende artikler:
  
- [Opret en delt postkasse](../../admin/email/create-a-shared-mailbox.md)
- [Fjern en licens fra en delt postkasse](../../admin/email/remove-license-from-shared-mailbox.md)
- [Delte postkasser i Exchange Online](/exchange/collaboration-exo/shared-mailboxes) for alle andre Microsoft 365 planer.

## <a name="who-can-assign-licenses"></a>Who kan tildele licenser?

Forskellige typer administratorer kan arbejde med licenser på forskellige måder, afhængigt af deres roller. I følgende tabel vises de mest almindelige indstillinger. Du kan se en komplet liste over administratorroller og -rettigheder under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  
|Administratorrolle|Tildel en licens|Fjern tildelingen af en licens|Køb flere licenser|Slet en konto|
|:-----|:-----|:-----|:-----|:-----|
|Faktureringsadministrator|Nej|Nej|Ja|Nej|
|Global administrator|Ja|Ja|Ja|Ja|
|Licensadministrator|Ja|Ja|Nej|Nej|
|Administrator af tjenestesupport|Nej|Nej|Nej|Nej|
|Brugeradministrator|Ja|Ja|Nej|Ja|

## <a name="related-content"></a>Relateret indhold

[Køb eller fjern licenser til dit virksomhedsabonnement](buy-licenses.md) (artikel)\
[Tildel licenser til brugere](../../admin/manage/assign-licenses-to-users.md) (artikel)\
[Fjern tildeling af licenser fra brugere](../../admin/manage/remove-licenses-from-users.md) (artikel)\
[Fjern en licens fra en delt postkasse](../../admin/email/remove-license-from-shared-mailbox.md) (artikel)
