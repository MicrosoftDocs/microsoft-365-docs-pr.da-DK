---
title: Integrer Microsoft OneDrive LTI med Blackboard
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Opret og begrader opgaver, byg og organiser kursusindhold, og samarbejd om filer i realtid med det nye Microsoft OneDrive Learning Tools Interoperability for Blackboard.
ms.openlocfilehash: 7e43ff51a069db55be06236fb0318aa4453d8feb
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824646"
---
# <a name="integrate-microsoft-onedrive-lti-with-blackboard"></a>Integrer Microsoft OneDrive LTI med Blackboard

Integration af Microsoft OneDrive LTI med Blackboard er en totrinsproces. Det første trin gør Microsoft OneDrive LTI tilgængelig i Blackboard-kurser, og det andet trin aktiveres Microsoft OneDrive for Blackboard.

> [!IMPORTANT]
> Den person, der udfører denne integration, skal være administrator af Blackboard og administrator af den Microsoft 365 lejer.

## <a name="recommended-browser-settings"></a>Anbefalede browserindstillinger

- Cookies bør være tilladt for Microsoft OneDrive.
- Pop op-filer bør ikke blokeres for Microsoft OneDrive.

> [!NOTE]
>
> - Cookies er ikke tilladt som standard i Chrome-browserens inkognitotilstand og skal være tilladt.
> - Microsoft OneDrive LTI fungerer i privat tilstand i Microsoft Edge browser. Sørg for, at du ikke har blokeret cookies (som er tilladt som standard).

## <a name="register-the-onedrive-lti-13-tool-in-blackboard"></a>Registrer værktøjet OneDrive LTI 1.3 i Blackboard

1. Vælg **LTI-værktøjsprovidere** i Blackboards administratorpanel.
2. Vælg **Registrer LTI 1.3-værktøj**.
3. I feltet Klient-id skal du skrive eller kopiere og indsætte dette id: ``78cd1b1c-ccbd-4318-9f90-22241f63b1f5``

   > [!NOTE]
   > Hvis du tilføjer dette klient-id, konfigureres to forskellige placeringer i Blackboard: én, der giver adgang til værktøjet fra indholdsmarkedet, bøger og værktøjer og RTF-editoren, og en anden, der giver adgang til værktøjet fra menuen Tilføj indhold i kurset online til Ultra-kurser.

4. Vælg **Send**.
5. Gennemse alle forudindstillede indstillinger i visningen **Værktøjsstatus** , og sørg for, at knappen **Afrundet værktøjsstatus** er **Godkendt**.
6. I **Institutionspolitikker** skal du vælge kurset **Rolle og** afkrydsningsfelterne **Navn** i de brugerfelter, der skal sendes. Alle andre brugerfelter er valgfrie, men det anbefales, at du lader dem være på et senere tidspunkt, hvor du kan kontrollere din OneDrive installation.
7. **Tillad tjenesteadgang til kvalitet** og **Tillad adgang til medlemskabstjeneste** er også valgfri på nuværende tidspunkt, men kan være påkrævet for fremtidige opdateringer af LTI-værktøjet.
8. Kopiér **installations-id'et**. Du skal bruge det for at konfigurere Microsoft LTI Tool.
9. Vælg knappen **Send** for at afslutte.

## <a name="configure-the-microsoft-lti-tool-to-work-with-blackboard"></a>Konfigurer Microsoft LTI-værktøjet til at arbejde med Blackboard

1. Log på [Microsoft OneDrive LTI-registreringsportalen](https://onedrivelti.microsoft.com/admin).
2. Vælg knappen **Administratorsamtykke** , og acceptér tilladelserne.

> [!CAUTION]
> Hvis dette trin ikke udføres, giver følgende trin dig en fejl, og du kan ikke udføre dette trin i en time, når du har fået fejlen.

3. Vælg knappen **Opret ny LTI-lejer** .
4. På siden LTI Registration skal du vælge **Blackboard** på rullelisten LTI Consumer Platform og derefter vælge knappen **Næste** .
5. Indsæt det **installations-id** , du kopierede under registreringen af værktøjet i Blackboard, og vælg **Næste**.
6. Gennemse og gem dine ændringer. Der vises en meddelelse ved vellykket registrering.
7. Dine registreringsoplysninger kan også gennemses ved at vælge knappen **Vis LTI-lejere** på startsiden.

Når du har fuldført disse trin, kan dine instruktører åbne dokumenter fra OneDrive, når de bruger menuen 'plus' på siden Kursusindhold.

## <a name="recommended-content"></a>Anbefalet indhold

[Microsoft Integrations for Blackboard](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft)

[integration af Microsoft Teams klasser](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft_Classes)
