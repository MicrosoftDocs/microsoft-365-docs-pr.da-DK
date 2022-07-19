---
title: Administrer ejerløse Microsoft 365-grupper og -teams
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- MET150
- MOE150
description: Få mere at vide om, hvordan du automatisk inviterer medlemmer til at blive ejere i en Ejerløs Microsoft 365-gruppe eller et team i Microsoft Teams.
ms.openlocfilehash: da332d32bef075c8ca6ecf45fa642ef6d944bea1
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66858695"
---
# <a name="manage-ownerless-microsoft-365-groups-and-teams"></a>Administrer ejerløse Microsoft 365-grupper og -teams

Et team i Microsoft Teams eller en Microsoft 365-gruppe og dens relaterede tjenester kan blive ejerløse, hvis en ejers konto slettes eller deaktiveres i Microsoft 365. Grupper og teams kræver, at en ejer tilføjer eller fjerner medlemmer og ændrer gruppeindstillinger.

En Global administrator kan oprette en politik, der automatisk spørger de mest aktive medlemmer af en ejerløs gruppe eller et team, om de vil acceptere ejerskab. Når et medlem accepterer invitationen til at blive ejer, logføres handlingen i overvågningsloggen for overholdelsesportalen. Gæster inviteres aldrig til at være ejere.

Når du opretter politikken, kan du angive:
- Hvis du vil begrænse, hvem der kan inviteres til at være ejer, ved at angive en sikkerhedsgruppe
- Afsenderadressen for meddelelserne
- Det antal uger, meddelelserne sendes
- Hvilke grupper eller teams der er en del af politikken

> [!Note]
> Hvis du bruger en sikkerhedsgruppe til at begrænse, hvem der kan inviteres til at være ejer, kræver det, at du besidder, men ikke nødvendigvis tildeler en Azure AD Premium-licens til hvert Microsoft 365-gruppemedlem i din organisation.

Sådan angiver du en ejerløs gruppe- eller teampolitik

1. Gå til **Vis alle** \> **indstillinger** \> **Organisationsindstillinger** i Administration, og vælg **Microsoft 365-grupper** <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">under fanen **Tjenester**</a>.

1. Markér afkrydsningsfeltet **Når der ikke er nogen ejer, mail og bed aktive gruppemedlemmer om at blive ejer** .

1. Hvis du vil beholde standardkonfigurationsindstillingerne, skal du vælge **Gem**, ellers skal du vælge **Konfigurer politik** og fuldføre følgende trin.

1. På siden *Med indstillinger for ugentlige meddelelser* skal du angive, hvem der kan modtage ejerskabsmeddelelser. Hvis du vælger at tillade eller blokere visse medlemmer, skal du søge efter og tilføje den sikkerhedsgruppe, du vil bruge.

1. Skriv det antal aktive medlemmer, du vil give besked, og vælg det antal uger, meddelelsen skal sendes. Meddelelseslisten oprettes under den første meddelelse og ændres ikke. Vælg **Næste**.

1. Vælg en afsender til mailen på siden *Hvem er denne mail, der kommer fra* , og vælg derefter **Næste**.

1. På siden *Emne og meddelelse* skal du tilpasse mailen og eventuelt inkludere **url-adressen til en politikretningslinje** og derefter vælge **Næste**.

1. På siden *Vælg, hvilke grupper der skal målrettes skal* du vælge **Specifikke grupper** og vælge de grupper og teams, du vil medtage i denne politik, eller vælge **Alle grupper**.

1. Vælg **Næste**.

1. På siden *Gennemse og afslut* skal du bekræfte dine indstillinger og klikke på **Udfør** og derefter vælge **Udført**.

Meddelelser sendes ugentligt med start inden for 24 timer efter oprettelsen af en politik. Modtagerne kan ikke videresende meddelelserne til andre. Meddelelser og svar spores i overvågningsloggen.

Op til to gruppemedlemmer pr. gruppe kan acceptere invitationen for at blive ejer. Hvis ingen gruppemedlemmer accepterer, skal en administrator [tildele en gruppeejer](/admin/create-groups/add-or-remove-members-from-groups).


