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
description: Opret opgaver og karakterer, opbyg og lav kursusindhold, og samarbejd om filer i realtid med den nye Microsoft OneDrive Learning Tools Interoperability til Blackboard.
ms.openlocfilehash: 94e77181244bbf02115bd706e86751a9382b906b
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63705295"
---
# <a name="integrate-microsoft-onedrive-lti-with-blackboard"></a>Integrer Microsoft OneDrive LTI med Blackboard

Integrering Microsoft OneDrive LTI med Blackboard er en proces i to trin. Det første trin gør Microsoft OneDrive LTI tilgængelig på Blackboard-kurser, og det andet trin Microsoft OneDrive for Blackboard.

> [!IMPORTANT]
> Den person, der udfører denne integration, skal være administrator for Blackboard og administrator for Microsoft 365 lejer.

## <a name="recommended-browser-settings"></a>Anbefalede browserindstillinger

- Cookies bør være tilladt for Microsoft OneDrive.
- Pop op-vindue bør ikke blokeres for Microsoft OneDrive.

> [!NOTE]
>
> - Cookies er ikke tilladt som standard i Chrome-browserens incognito-tilstand og skal være tilladt.
> - Microsoft OneDrive LTI fungerer i privat tilstand i Microsoft Edge browser. Sørg for, at du ikke har blokeret cookies (der er tilladt som standard).

## <a name="register-the-onedrive-lti-13-tool-in-blackboard"></a>Registrer OneDrive LTI 1.3-værktøjet i Blackboard

1. VælgLTI-værktøjsudbydere i  **Blackboards administratorpanel**.
2.  **SelectRegister LTI 1.3-værktøj**.
3. I feltet Klient-id skal du skrive eller kopiere og indsætte dette id: ``78cd1b1c-ccbd-4318-9f90-22241f63b1f5``

  > [!NOTE]
  > Tilføjelse af dette klient-id konfigurerer to forskellige placeringer i Blackboard: en, der giver adgang til værktøjet fra Indholdsmarked, Bøger og værktøjer og RTF-editoren, og en anden, der giver adgang til værktøjet fra menuen Tilføj indhold i kurset online for Ultra-kurser.

4. Vælg **Send**.
5. Gennemse alle forudindstillede indstillinger  **itool-statusvisningen** , og sørg for, at knappen **Status** for værktøj er  **blevet valgt Som godkendt**.
6.  **InInstitution-politikker**, vælg **kurset Rolle i og** **afkrydsningsfelterne** Navn i de brugerfelter, der skal sendes. Alle andre brugerfelter er valgfri, men det anbefales at lade dem være på for at fremtidig korrektur OneDrive installationen.
7. **Tillad tjenesteadgang til karakterer**   **andAllow membership service access** are also optional at this time, but might be required for future updates to the LTI tool.
8. Kopiér **Installations-id'et**. Du skal bruge det for at konfigurere Microsoft LTI-værktøjet.
9. Vælg knappen **Send** for at afslutte.

## <a name="configure-the-microsoft-lti-tool-to-work-with-blackboard"></a>Konfigurer Microsoft LTI-værktøjet til at arbejde med Blackboard

1. Log på Microsoft OneDrive [LTI-registreringsportalen](https://onedrivelti.microsoft.com/admin).
2. Vælg knappen **Administratorsamtykke** , og acceptér tilladelserne.

> [!CAUTION]
> Hvis dette trin ikke udføres, giver det følgende trin dig en fejl, og du vil ikke kunne tage dette trin i en time, når du har fået fejlen.

3. Vælg knappen **Opret ny LTI-lejer** .
4. På siden LTI-registrering skal du **vælge Blackboard** på rullelisten Forbrugerplatform for LTI og derefter vælge **knappen** Næste.
5. Indsæt **installations-id'et** , som du kopierede under registrering af værktøjet i Blackboard, og vælg **Næste**.
6. Gennemse og gem ændringerne. Der vises en meddelelse, når registreringen er gennemført.
7. Dine registreringsoplysninger kan også gennemses ved at vælge **knappen Vis LTI-lejere** på startsiden.

Når du har fuldført disse trin, vil dine undervisere kunne åbne dokumenter fra OneDrive når de bruger menuen "plus" på siden Kursusindhold.

## <a name="recommended-content"></a>Anbefalet indhold

[Microsoft-integration til Blackboard](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft)

[Microsoft Teams integration af klasser](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft_Classes)
