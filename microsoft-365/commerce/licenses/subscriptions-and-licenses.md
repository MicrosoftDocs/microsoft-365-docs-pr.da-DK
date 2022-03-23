---
title: Forstå abonnementer og licenser i Microsoft 365 til virksomheder
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: micurn, nicholak
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
description: De programmer og tjenester, du modtager, afhænger af, Microsoft 365 produkt du har købt, f.eks. Microsoft 365 Apps for business.
ms.date: 07/01/2020
ms.openlocfilehash: fefdca1b1321e19d76a227ecd313708e700b9c01
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590728"
---
# <a name="understand-subscriptions-and-licenses-in-microsoft-365-for-business"></a>Forstå abonnementer og licenser i Microsoft 365 til virksomheder

Når du køber et abonnement på Microsoft 365 til virksomheder, tilmelder du dig et sæt apps og tjenester, som du betaler for enten månedligt eller årligt. De programmer og tjenester, du modtager som en del af dit abonnement, afhænger af, hvilket produkt du har købt, f.eks. Microsoft 365 Apps for business eller Microsoft 365 Business Standard. Du kan se, hvad der følger med hvert produkt [på Microsoft 365 til små og mellemstore](https://products.office.com/compare-all-microsoft-office-products?&activetab=tab:primaryr1) virksomheder.

Når du køber et abonnement, angiver du det antal licenser, du skal bruge, baseret på, hvor mange personer du har i organisationen. Når du har købt et abonnement, kan du oprette konti til personer i organisationen og derefter tildele en licens til hver enkelt person. Efterhånden som organisationens behov ændrer sig, kan du købe flere licenser til nye personer eller tildele licenser til andre brugere, når en person forlader organisationen.

Hvis du har mere end ét abonnement, kan du tildele licenser til forskellige personer for hvert abonnement. Du kan f.eks. tildele alle dine brugere til alle Microsoft 365 programmer og tjenester som en del af et Microsoft 365 Business Standard-abonnement. Du kan også tildele et undersæt af brugere til Visio Online via et separat Visio abonnement.

## <a name="how-many-devices-can-people-install-office-on"></a>Hvor mange enheder kan folk installere Office på?

Hvis dit abonnement omfatter et af følgende produkter, kan hver person installere Office på op til fem pc'er eller Mac-computere, fem tablets og fem telefoner.

:::row:::
   :::column span="":::
        - Microsoft 365 Apps for business - Microsoft 365 Apps for enterprise - Microsoft 365 Business Standard - Microsoft 365 Business Premium - Microsoft 365 A3 – Microsoft 365 A5
   :::column-end:::
   :::column span="":::
        - Microsoft 365 E3 - Microsoft 365 E5 - Office 365 A1 Plus - Office 365 A3 - Office 365 A5 - Office 365 E3 - Office 365 E5
   :::column-end:::
:::row-end:::

## <a name="what-happens-when-you-assign-a-license-to-someone"></a>Hvad sker der, når du tildeler en person en licens?

I følgende tabel vises, hvad der automatisk sker, når du tildeler en person en licens:
  
|**Hvis abonnementet har denne tjeneste**|**Dette sker automatisk**|
|:-----|:-----|
|Exchange Online  <br/> |Der oprettes en postkasse til den pågældende person. <br/> Hvis du vil have mere at vide om serviceaftalen for denne opgave, skal du se ["Konfigurere..." meddelelser i Microsoft 365 Administration](https://support.microsoft.com/help/2635238/setting-up-messages-in-the-office-365-admin-center). |
|SharePoint Online  <br/> |Personen tildeles redigeringstilladelser SharePoint onlineteamwebstedet.  <br/> |
|Skype for Business Online  <br/> |Personen har adgang til de funktioner, der er knyttet til licensen.  <br/> |
|Microsoft 365 Apps for enterprise og Microsoft 365 Apps for business  <br/> |Personen kan downloade Office apps på op til fem Mac-computere eller pc'er, fem tablets og fem smartphones.  <br/> |

## <a name="understand-licenses-for-non-user-mailboxes"></a>Forstå licenser til postkasser uden brugere

Du behøver ikke at tildele licenser til ressourcepostkasser, lokalepostkasser og delte postkasser, medmindre de  når over deres lagerkvote på 50 gigabyte (GB). Du kan finde flere oplysninger om postkasser uden brugere i følgende artikler:
  
- [Opret en delt postkasse](../../admin/email/create-a-shared-mailbox.md)
- [Fjerne en licens fra en delt postkasse](../../admin/email/remove-license-from-shared-mailbox.md)
- [Delte postkasser i Exchange Online](/exchange/collaboration-exo/shared-mailboxes) for alle Microsoft 365-planer.

## <a name="who-can-assign-licenses"></a>Who kan tildele licenser?

Forskellige typer af administratorer kan arbejde med licenser på forskellige måder, afhængigt af deres roller. I følgende tabel vises de mest almindelige indstillinger. Du kan finde en komplet liste over administratorroller og -rettigheder [i Om administratorroller](../../admin/add-users/about-admin-roles.md).
  
|**Administratorrolle**|**Tildel en licens**|**Fjern tildeling af en licens**|**Køb flere licenser**|**Slet en konto**|
|:-----|:-----|:-----|:-----|:-----|
|Faktureringsadministrator  <br/> |Nej  <br/> |Nej  <br/> |Ja  <br/> |Nej  <br/> |
|Global administrator  <br/> |Ja  <br/> |Ja  <br/> |Ja  <br/> |Ja  <br/> |
|Licensadministrator <br/> |Ja <br/>|Ja <br/> |Nej <br/> |Nej <br/> |
|Tjenestesupportadministrator  <br/> |Nej  <br/> |Nej  <br/> |Nej  <br/> |Nej  <br/> |
|Brugeradministrator  <br/> |Ja  <br/> |Ja  <br/> |Nej  <br/> |Ja  <br/> |

## <a name="related-content"></a>Relateret indhold

[Køb eller fjern licenser til dit virksomhedsabonnement](buy-licenses.md) (artikel)\
[Tildel licenser til brugere](../../admin/manage/assign-licenses-to-users.md) (artikel)\
[Fjern tildeling af licenser fra brugere](../../admin/manage/remove-licenses-from-users.md) (artikel)\
[Fjern en licens fra en delt postkasse](../../admin/email/remove-license-from-shared-mailbox.md) (artikel)
