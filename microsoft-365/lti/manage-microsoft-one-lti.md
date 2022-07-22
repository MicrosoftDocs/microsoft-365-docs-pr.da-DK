---
title: Administrer Microsoft LMS Gateway for alle LMS
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
description: Få mere at vide om, hvordan du udfører vigtige microsoft LMS Gateway-administrationsopgaver, herunder visning, sletning, redigering og fejlfinding.
ms.openlocfilehash: 77f89927a7beb7cd045c2325bd805efdf45996a0
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944103"
---
# <a name="manage-microsoft-lms-gateway-for-any-lms"></a>Administrer Microsoft LMS Gateway for alle LMS

Microsoft LMS Gateway kan integreres med flere LMS-elementer, herunder Lærred, Blackboard, Moodle og Brightspace.

I denne artikel finder it-administratorer instruktioner til vigtige Administrationsopgaver for Microsoft LMS Gateway.

- [Få vist en LTI-registrering](#view-an-lti-registration).
- [Slet en LTI-registrering](#delete-an-lti-registration).
- [Rediger en LTI-registrering](#edit-an-lti-registration).
- [Foretag fejlfinding af problemer med Microsoft LMS Gateway](#troubleshoot-issues-with-microsoft-lms-gateway).
- [Rapportér problemer med Microsoft LMS Gateway](#report-problems-with-lti-registration-portal).

## <a name="view-an-lti-registration"></a>Få vist en LTI-registrering

Hvis du vil have vist detaljerne for en LTI-registrering, skal du følge nedenstående trin.

1. Besøg [Microsoft LMS Gateway](https://lti.microsoft.com/).
2. Log på med en Microsoft 365-administratorkonto.
3. Find den LTI-registrering, du vil have vist, på registreringslisten.
4. Vælg **ikonet med øjet** ud for listen.
5. Panelet med registreringsoplysninger åbnes.

## <a name="delete-an-lti-registration"></a>Slet en LTI-registrering

Hvis du vil slette en LTI-registrering, skal du følge nedenstående trin.

1. Besøg [Microsoft LMS Gateway](https://lti.microsoft.com/).
2. Log på med en Microsoft 365-administratorkonto.
3. Find den LTI-registrering, du vil slette, på registreringslisten.
4. Vælg **skraldespandsikonet ud** for listen.
5. Vælg **Slet** i bekræftelsesdialogboksen for at bekræfte sletningen.
6. Du får vist en meddelelse om, at den lykkedes, når den er slettet.

## <a name="edit-an-lti-registration"></a>Rediger en LTI-registrering

I øjeblikket understøtter vi ikke redigering af en eksisterende LTI-registrering, når den er tilføjet.

Hvis du vil ændre en LTI-registrering, skal du:

1. [Slet den eksisterende registrering](#delete-an-lti-registration).
2. Tilføj en ny registrering.

## <a name="troubleshoot-issues-with-microsoft-lms-gateway"></a>Foretag fejlfinding af problemer med Microsoft LMS Gateway

Hvis du eller dine undervisere oplever problemer med Microsoft LMS Gateway, kan du foretage fejlfinding på følgende ting.

### <a name="issues-while-launching-an-lti-app-from-the-lms"></a>Problemer under start af en LTI-app fra LMS

Undervisere kan opleve problemer med at starte en Microsoft LTI-app i deres LMS.

Hvis det er tilfældet, er her nogle almindelige problemer, og hvordan du løser dem.

- **Cookies blev ikke fundet**
  - Cookies fra tredjepart skal være tilladt for **LMS URL-adressen** i browserindstillingerne.
  - Disse cookies er nødvendige for at fuldføre LTI 1.3-håndtrykket i henhold til IMS-specifikationerne.
  - Hvis du vil vide mere om, hvordan du opdaterer browserens cookieindstillinger, skal du se [Tillad cookies for LMS URL-adresser i din browser](browser-cookies.md).

- **Registreringsoplysningerne blev ikke fundet**
  - Dette problem opstår, når registreringen af LTI-appen ikke blev fuldført, eller hvis registreringen blev slettet i Microsoft LMS Gateway.
  - It-administratoren skal fuldføre registreringen af LTI-appen.

- **Nogle oplysninger fra LMS er ikke gyldige**
  - Dette problem opstår, når de oplysninger, der sendes fra LMS i appstartanmodningen, ikke er justeret i overensstemmelse med IMS LTI 1.3-specifikationen.
  - It-administratoren skal kontakte [Microsofts uddannelsessupportteam](https://edusupport.microsoft.com/support?product_id=lti_apps&platform_id=web) , hvis problemet fortsætter.

### <a name="issues-with-signing-in-to-the-microsoft-lms-gateway"></a>Problemer med at logge på Microsoft LMS Gateway

Når du logger på Microsoft LMS Gateway, kan du have problemer med at få adgang til registreringssiden eller modtage en logonfejl.

Her er nogle almindelige logonproblemer, og hvordan du løser dem.

- **Autorisationsfejl**
  - Hvis du får vist fejlmeddelelsen "Din konto har ikke tilladelse til at få adgang til denne side", skal du enten:
    - Kontoen tilhører ikke en registreret lejer, eller
    - Kontoen tilhører ikke en underviser eller administrator.

  - I begge disse tilfælde får du vist knappen **Log af & skift konti** .
    - Vælg denne knap, eller vælg knappen **Log af** i brugerprofilmenuen.
    - Log på med en konto, der tilhører lejeren, en underviser eller en administrator.

  - Hvis lejeren ikke er registreret, skal it-administratoren registrere den, før vedkommende forsøger at registrere LTI-integrationer.

  - Hvis du stadig får vist denne fejl, når du har prøvet disse trin, skal du logge af og logge på igen.
    - Du kan også rydde cookies og lokalt lager for Microsoft LMS Gateway og `https://login.microsoftonline.com/`.
    - Prøv at logge på igen.
    - Hvis problemet fortsætter, skal du rapportere problemet ved at vælge linket **Rapportér et problem** øverst til højre.

- **Godkendelsesfejl**
  - Hvis du får vist fejlmeddelelsen "Godkendelse mislykkedes. Prøv igen", er logonsessionen muligvis udløbet.
    - Log af, og log på igen.
    - Du kan også rydde cookies og lokalt lager for Microsoft LMS Gateway og `https://login.microsoftonline.com/`.
    - Prøv at logge på igen.
    - Hvis problemet fortsætter, skal du rapportere problemet ved at vælge linket **Rapportér et problem** øverst til højre.

- **Andre fejl**
  - For alle andre fejl får du vist fejlmeddelelsen "Noget gik galt. Prøv igen senere."
    - Dette kan være en intern behandlingsfejl.
    - Prøv at logge på igen efter et par timer.
      - Vælg knappen **Gå til startside** . Dette navigerer tilbage til landingssiden.
      - Vælg knappen **Gå til registreringsportal** for at gå tilbage til Microsoft LMS Gateway.

### <a name="report-problems-with-lti-registration-portal"></a>Rapportér problemer med LTI-registreringsportalen

Hvis du vil rapportere problemer eller sende feedback til LTI-registreringsportalen, skal du følge nedenstående trin.

1. På LTI-registreringsportalen skal du vælge **spørgsmålstegnsikonet** i sidehovedet.
2. Vælg **Rapportér et problem** på rullelisten.
3. Siden Microsoft Education Support åbnes. Log på med dine legitimationsoplysninger til Microsoft 365.
4. Udfyld formularen, og send.
