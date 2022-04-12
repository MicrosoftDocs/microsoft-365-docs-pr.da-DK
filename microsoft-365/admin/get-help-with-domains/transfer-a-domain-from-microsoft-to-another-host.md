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
ms.openlocfilehash: 18f2b6502268b757b651abe08585cc06b63d7129
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782473"
---
# <a name="transfer-a-domain-from-microsoft-to-another-host"></a>Overfør et domæne fra Microsoft til en anden vært

Du kan ikke overføre et Microsoft 365 domæne til en anden registrator i 60 dage, efter at du har købt domænet fra Microsoft.

> [!NOTE]
> En _Whois-forespørgsel_ viser en domæneregistrator, der er købt af Microsoft, som Wild West Domains LLC. Det er dog kun Microsoft, der skal kontaktes vedrørende dit Microsoft 365 købte domæne.

Følg disse trin for at hente en kode på Microsoft 365, og gå derefter til det andet domæneregistratorwebsted for at konfigurere overførsel af dit domænenavn til den nye registrator.

## <a name="transfer-a-domain"></a>Overfør et domæne

1. I Administration skal du gå til **Indstillinger** \> **Domæner**.

2. På siden **Domæner** skal du vælge det Microsoft 365 domæne, du vil overføre til en anden domæneregistrator, og derefter vælge **Kontrollér tilstand**.

3. Øverst på siden skal du vælge **Overfør domæne**.

4. Vælg **En anden registrator** på siden **Vælg, hvor du vil overføre dit domæne**, og klik derefter på **Næste**.

5. På siden **Lås domæneoverførsel op** skal du vælge **Lås overførsel op for <_dit domæne_>** og derefter vælge **Næste**.

6. Kontrollér kontaktoplysningerne for domæneoverførslen, og vælg derefter **Næste**.

7. Kopiér godkendelseskoden, og vent ca. 30 minutter på, at statussen for domæneoverførslen ændres til **Ulåst til overførsel** under fanen **Registrering,** før du fortsætter med de næste trin.

8. Gå til webstedet for den domæneregistrator, du vil administrere dit domænenavn fremover. Følg vejledningen for overførsel af et domæne (søg efter hjælp på deres websted). Dette betyder normalt betaling af overførselsgebyrer og at give Authcode til den nye registrator, så de kan starte overførslen. Microsoft sender en mail til dig for at bekræfte, at vi har modtaget anmodningen om overførsel, og at domænet overføres inden for 5 dage.

    Du kan finde fanen **Registrering** af godkendelseskode på siden **Domæner** i Microsoft 365.

    > [!TIP]
    > .uk-domæner kræver en anden procedure. Kontakt Microsoft Support, og anmod om en **ændring af IPS-koden** , så den stemmer overens med den registrator, du vil administrere dit domæne fremover. Når koden ændres, overføres domænet straks til den nye registrator. Du skal derefter arbejde sammen med den nye registrator for at gennemføre overførslen, sandsynligvis betale overførselsgebyrer og føje det overførte domæne til din konto med din nye registrator.

9. Når overførslen er fuldført, skal du forny dit domæne hos den nye domæneregistrator.

10. For at afslutte processen skal du gå tilbage til siden **Domæner** i Administration og derefter vælge **Fuldfør domæneoverførsel**. Dette markerer domænet som ikke længere købt fra Microsoft 365 og deaktiverer domæneabonnementet. Det fjerner ikke domænet fra lejeren og påvirker ikke eksisterende brugere og postkasser på domænet.

> [!NOTE]
> Microsoft 365 købte domæner er ikke berettiget til navneserverændringer eller overførsel af domænet mellem Microsoft 365 organisationer. Hvis en af disse er påkrævet, skal domæneregistreringen overføres til en anden registrator.
