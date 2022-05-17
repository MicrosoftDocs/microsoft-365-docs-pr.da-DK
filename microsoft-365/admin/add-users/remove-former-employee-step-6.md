---
title: Trin 6 – Fjern og slet licensen Microsoft 365 fra en tidligere medarbejder
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
description: Du kan fjerne en tidligere medarbejders Microsoft 365 licens og derefter slette den fra dit abonnement eller tildele licensen til en anden bruger.
ms.openlocfilehash: 95f95403a316e176f91c7f120ce5a26487a7a59f
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436223"
---
# <a name="step-6---remove-and-delete-the-microsoft-365-license-from-a-former-employee"></a>Trin 6 – Fjern og slet licensen Microsoft 365 fra en tidligere medarbejder

Hvis du ikke vil betale for en licens, når nogen forlader din organisation, skal du fjerne deres Microsoft 365 licens og derefter slette den fra dit abonnement. Du kan tildele en licens til en anden bruger, hvis du ikke sletter den.

Hvis postkassen skal tilgås af godkendte personer, der har fået tildelt eDiscovery-tilladelser af overholdelseshensyn eller juridiske årsager, skal den tildeles en Exchange Online Plan 2-licens (eller en Exchange Online Plan 1-licens med en Exchange Online-arkivering  tilføjelsesprogramlicens), så der kan anvendes en venteposition på postkassen, før den slettes. Når brugerkontoen er slettet, vil alle Exchange Online licenser, der er knyttet til brugerkontoen, være tilgængelige for en ny bruger.
  
Når du fjerner licensen, opbevares alle brugerens data i 30 dage. Du kan [få adgang til](get-access-to-and-back-up-a-former-user-s-data.md) dataene eller [gendanne](restore-user.md) kontoen, hvis brugeren kommer tilbage. Efter 30 dage slettes alle brugerens data (undtagen dokumenter, der er gemt på SharePoint Online) permanent fra Microsoft 365 og kan ikke gendannes.

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .
2. Vælg navnet på den medarbejder, du vil blokere, og vælg derefter fanen **Licenser og apps** .
3. Fjern markeringen i afkrydsningsfelterne for den eller de licenser, du vil fjerne, og vælg derefter **Gem ændringer**.

Benyt følgende fremgangsmåde **for at reducere det antal licenser, du betaler for**, indtil du ansætter en anden person:

1. I Administration skal du gå til siden **Fakturering** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">dine produkter</a> og vælge fanen **Produkter** .
2. Vælg det abonnement, du vil fjerne licenser fra.
3. På detaljesiden skal du vælge **Fjern licenser**.
4. I ruden **Fjern licenser** under Ny mængde skal du i feltet **Antal licenser i alt** angive det samlede antal licenser, du vil have til dette abonnement. Hvis du f.eks. har 25 licenser, og du vil fjerne en af dem, skal du angive 24.
5. Vælg **Gem**.

Når du [føjer en anden person](add-users.md) til din virksomhed, bliver du bedt om at købe en licens på samme tid med kun ét trin!

Du kan få flere oplysninger om administration af brugerlicenser til Microsoft 365 til virksomheder [under Tildel licenser til brugere i Microsoft 365 til virksomheder](../manage/assign-licenses-to-users.md) og [Fjern tildeling af licenser fra brugere i Microsoft 365 til virksomheder](../manage/remove-licenses-from-users.md).
  
## <a name="how-the-deleted-employee-account-affects-skype-for-business"></a>Sådan påvirker den slettede medarbejderkonto Skype for Business

Når du fjerner en brugers licens fra Office 365, frigives det PSTN-opkaldsnummer, der er knyttet til brugeren. Du kan tildele den til en anden bruger.
  
Hvis brugeren tilhører en køgruppe, vil vedkommende ikke længere være et levedygtigt mål for opkaldskøagenterne. Det anbefales derfor, at du også fjerner brugeren fra de grupper, der er knyttet til opkaldskøen.

## <a name="set-up-call-forwarding-to-people-in-your-organization"></a>Konfigurer viderestilling af opkald til personer i din organisation

Hvis du har brug for at konfigurere viderestilling af opkald for den opsagte medarbejders telefonnummer, kan indstillingen for viderestilling af opkald under opkaldspolitikker konfigurere viderestilling, hvor indgående opkald kan viderestilles til andre brugere eller ringe til en anden person på samme tid. Du kan få flere oplysninger [under Opkald af politikker i Microsoft Teams](/microsoftteams/teams-calling-policy).
