---
title: Overfør et domæne fra Microsoft til en anden vært
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
description: 'Find trinnene her for at overføre et domæne fra Microsoft til en anden registrator. '
ms.openlocfilehash: 192e9c1e14666f80fb670c5c8e268ae54ece0c64
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590622"
---
# <a name="transfer-a-domain-from-microsoft-to-another-host"></a>Overfør et domæne fra Microsoft til en anden vært

Du kan ikke overføre et Microsoft 365 domæneregistrator i 60 dage, efter du har købt domænet hos Microsoft.

> [!NOTE]
> En _Whoisquery_  viser en Microsoft-købt domæneregistrator som Wild West Domains LLC. Det er dog kun Microsoft, der bør kontaktes vedrørende dit Microsoft 365 købte domæne.

Følg disse trin for at få en kode på Microsoft 365, og gå derefter til den anden domæneregistrators websted for at konfigurere overførslen af dit domænenavn til den nye registrator.

## <a name="transfer-a-domain"></a>Overfør et domæne

1. I Administration skal du gå til   **Indstillinger** >  **Domæner**.

2. På siden **Domæner skal** du vælge det Microsoft 365 domæne, du vil overføre til en anden domæneregistrator, og derefter vælge **Kontrollér tilstand**.

3. Øverst på siden skal du vælge **Overfør domæne**.

4. På siden **Vælg, hvor du vil overføre dit domæne** skal du **vælge En anden registrator** og derefter klikke på **Næste**.

5. På siden **Lås domæneoverførsel** skal du vælge **Lås op for <_dit domæne_>** og derefter vælge **Næste**.

6. Kontrollér, at dit domæne overfører kontaktoplysninger, og vælg derefter **Næste**.

7. Kopiér godkendelseskoden, og vent ca. 30 minutter på, at domæneoverførslens status ændres til Ulåst **til** overførsel under fanen Registrering, før du fortsætter med de næste trin.

8. Gå til webstedet for den domæneregistrator, du vil administrere dit domænenavn for fremover. Følg vejledningen for at overføre et domæne (søg efter hjælp på deres websted). Det betyder normalt, at du betaler overførselsgebyrer, og at du giver den nye registrator authcode til den nye registrator, så denne kan starte overførslen. Microsoft sender dig en mail for at bekræfte, at vi har modtaget overførselsanmodningen, og domænet overføres inden for 5 dage.

    Du kan finde fanen Registrering af **godkendelseskode** på  **siden** Domæner i Microsoft 365.
    
    > [!TIP]
    > .uk-domæner kræver en anden procedure. Kontakt Microsoft Support, og anmod **om en IPS-mærkeændring** , så den svarer til den registrator, du vil administrere dit domæne på fremover. Når mærket ændres, overføres domænet straks til den nye registrator. Du skal derefter arbejde sammen med den nye registrator for at fuldføre overførslen og betale overførselsgebyrer og føje det overførte domæne til din konto hos din nye registrator.

9. Når overførslen er fuldført, skal du forny dit domæne hos den nye domæneregistrator.

10. For at afslutte processen skal du gå tilbage til **siden** Domæner i Administration og derefter   **vælgeComplete domæneoverførsel**. Dette markerer domænet som ikke længere købt hos Microsoft 365 og deaktiverer domæneabonnementet. Det fjerner ikke domænet fra lejeren og påvirker ikke eksisterende brugere og postkasser på domænet.

> [!NOTE]
> Microsoft 365 købte domæner er ikke berettiget til navneserverændringer eller overførsel af domænet mellem Microsoft 365 organisationer. Hvis en af disse er påkrævet, skal domæneregistreringen overføres til en anden registrator.
