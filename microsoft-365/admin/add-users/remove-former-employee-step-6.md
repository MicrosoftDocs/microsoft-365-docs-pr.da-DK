---
title: Trin 6 – Fjern og slet licensen Microsoft 365 en tidligere medarbejder
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- m365solution-removeemployee
search.appverid:
- BCS160
- MET150
- MOE150
description: Følg disse trin for at fjerne Microsoft 365 licensen fra en tidligere medarbejder.
ms.openlocfilehash: b724e8d65c990396ad376544de86d4ffd0cb5fdc
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63599392"
---
# <a name="step-6---remove-and-delete-the-microsoft-365-license-from-a-former-employee"></a>Trin 6 – Fjern og slet licensen Microsoft 365 en tidligere medarbejder

Hvis du ikke vil betale for en licens, når en person forlader din organisation, skal du fjerne dennes Microsoft 365 og derefter slette den fra dit abonnement. Du kan tildele en licens til en anden bruger, hvis du ikke sletter den.

Hvis postkassen skal tilgås af autoriserede personer, der har fået eDiscovery-tilladelser af overholdelseshensyn eller af juridiske årsager, skal den tildeles en Exchange Online Plan 2-licens (eller en Exchange Online Plan 1-licens med en Exchange Online-arkivering  tilføjelseslicens), så postkassen kan aktiveres i venteposition, før den slettes. Når brugerkontoen er slettet, vil alle Exchange Online licens, der er knyttet til brugerkontoen, være tilgængelige for at tildele den til en ny bruger.
  
Når du fjerner licensen, opbevares alle brugerens data i 30 dage. Du kan [få](get-access-to-and-back-up-a-former-user-s-data.md) adgang til dataene eller [gendanne](restore-user.md) kontoen, hvis brugeren kommer tilbage. Efter 30 dage slettes alle brugerens data (undtagen de dokumenter, der er gemt på SharePoint Online) permanent fra Microsoft 365 og kan ikke gendannes.

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.
2. Vælg navnet på den medarbejder, du vil blokere, og vælg derefter **fanen Licenser og** apps.
3. Fjern markeringen i afkrydsningsfelterne for de licenser, du vil fjerne, og vælg derefter **Gem ændringer**.

**Hvis du vil reducere antallet af licenser, du betaler for,** indtil du ansætter en anden person, skal du gøre følgende:

1. I Administration skal du gå til **siden Fakturering** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">dine</a> produkter og vælge **fanen** Produkter.
2. Vælg det abonnement, hvorfra du vil fjerne licenser.
3. På detaljesiden skal du vælge **Fjern licenser**.
4. I **ruden Fjern** licenser under Nyt antal i feltet **Samlet** antal licenser skal du angive det samlede antal licenser, du ønsker for dette abonnement. Hvis du f.eks. har 25 licenser, og du vil fjerne en af dem, skal du angive 24.
5. Vælg **Gem**.

Når du [føjer en anden person](add-users.md) til din virksomhed, bliver du bedt om at købe en licens samtidigt med bare ét trin!

Du kan finde flere oplysninger om administration af brugerlicenser til Microsoft 365 til virksomheder i Tildel licenser til brugere [i Microsoft 365 til](../manage/assign-licenses-to-users.md) virksomheder og Fjern licenser fra brugere [i Microsoft 365 til virksomheder](../manage/remove-licenses-from-users.md).
  
## <a name="how-the-deleted-employee-account-affects-skype-for-business"></a>Sådan påvirker den slettede medarbejderkonto Skype for Business

Når du fjerner en brugers licens fra en Office 365, frigives det PSTN-opkaldsnummer, der er knyttet til brugeren. Du kan tildele den til en anden bruger.
  
Hvis brugeren tilhører en gruppe, der er medlem af en kø, kan de ikke længere anvendes af opkaldskøagenterne. Vi anbefaler derfor, at du også fjerner brugeren fra de grupper, der er knyttet til opkaldskøen.

## <a name="set-up-call-forwarding-to-people-in-your-organization"></a>Konfigurere viderestilling af opkald til personer i organisationen

Hvis du skal konfigurere viderestilling af opkald for den opsagte medarbejders telefonnummer, kan indstillingen for viderestilling af opkald under opkaldspolitikker konfigurere viderestilling, hvor indgående opkald kan viderestilling til andre brugere eller ringe til en anden person på samme tid. Få mere at vide under [Opkaldspolitikker i Microsoft Teams](/microsoftteams/teams-calling-policy).
