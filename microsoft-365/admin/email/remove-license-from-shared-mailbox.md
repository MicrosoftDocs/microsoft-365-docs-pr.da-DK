---
title: Fjern licens fra delt postkasse
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
ms.reviewer: sinakassaw, nicholak
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: 'Fjern en licens fra en delt postkasse for at tildele den til en anden bruger, eller returner licensen, så du ikke betaler for den. '
ms.date: 05/11/2021
ms.openlocfilehash: 6de6f213cc0df7a216122d55ef07e270586aea12
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63599756"
---
# <a name="remove-a-license-from-a-shared-mailbox"></a>Fjerne en licens fra en delt postkasse

Delte postkasser kræver normalt ikke en licens. Følg disse instruktioner for at fjerne en licens fra en delt postkasse, så du enten kan tildele den til en bruger eller returnere licensen, så du ikke betaler for en licens, du ikke har brug for.

> [!NOTE]
>
> En Exchange Online Plan 2-licens er påkrævet i følgende scenarier:
>
> - Den delte postkasse har mere end 50 GB lagerplads i brug.
> - Den delte postkasse anvender direkte arkivering.
> - Den delte postkasse sættes i retslig venteposition.
> - Den delte postkasse har fået tildelt Microsoft 365 Defender licens.
> 
> Du kan finde en trinvis vejledning i at tildele licenser i [Tildel licenser til brugere](/microsoft-365/admin/manage/assign-licenses-to-users). 


## <a name="remove-the-license"></a>Fjern licensen

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.

::: moniker-end

::: moniker range="o365-21vianet"

 1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">for</a> brugere.

::: moniker-end

   > [!NOTE]
   > Du skal fjerne licensen fra siden Aktive brugere. Du kan ikke fjerne licensen fra siden Delt postkasse, fordi licenser er brugerindstillinger.
  
2. Vælg den delte postkasse.

3. På fanen **Licenser og apps** skal du **udvide Licenser** og fjerne markeringen i afkrydsningsfeltet for den licens, du vil fjerne.

4. Vælg **Gem ændringer**.

5. Når du vender tilbage **til siden Aktive** brugere, vil status for den delte postkasse være **Uden licens**.

6. Du betaler stadig for licensen. Hvis du vil stoppe med at betale for [det, skal du fjerne licensen fra dit abonnement](../../commerce/licenses/buy-licenses.md).

## <a name="related-content"></a>Relateret indhold

[Om delte postkasser](about-shared-mailboxes.md) (artikel)\
[Opret en delt postkasse](create-a-shared-mailbox.md) (artikel)\
[Konfigurer en delt postkasse](configure-a-shared-mailbox.md) (artikel)\
[Konvertér en brugerpostkasse til en delt postkasse](convert-user-mailbox-to-shared-mailbox.md) (artikel)\
[Løse problemer med delte postkasser](resolve-issues-with-shared-mailboxes.md) (artikel)
