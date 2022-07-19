---
title: Integrer Microsoft Teams-klasser og -møder med Moodle
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
description: Opret og administrer Teams-klasser og -møder med Microsoft OneDrive Learning Tools interoperabilitet for Moodle.
ms.openlocfilehash: da65874516dcf196ac91ecea1acc75e3cb719f58
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66858742"
---
# <a name="integrate-microsoft-teams-classes-and-meetings-within-moodle"></a>Integrer Microsoft Teams-klasser og -møder i Moodle

Denne vejledning indeholder it-administratortrinnene til registrering af både Teams-klasser og LTI-apps til Teams-møder i Moodle.

Du kan finde oplysninger om administration af alle LTI-apps til alle LMS under [Administrer Microsoft LMS Gateway for alle LMS](manage-microsoft-one-lti.md).

## <a name="prerequisites-before-set-up"></a>Forudsætninger, før de konfigureres

For at integrationen mellem Moodle og Teams kan fungere korrekt, skal Moodle og Teams være konfigureret til at kommunikere med hinanden.

Følg [instruktionerne for at installere og konfigurere Moodle-plug-in'en](moodle-plugin-configuration.md).

## <a name="register-microsoft-teams-lti-for-use-in-moodle"></a>Registrer Microsoft Teams LTI til brug i Moodle

> [!IMPORTANT]
> Den person, der udfører denne integration, skal være Moodle-administrator og Microsoft 365-lejeradministrator.

1. Besøg [Microsoft LMS Gateway](https://lti.microsoft.com/) , og vælg knappen **Gå til registreringsportal** .

2. Log på med en Microsoft 365-administratorkonto.

3. Når du har logget på, skal du vælge **Tilføj ny registrering**.

4. Vælg enten **Teams Meetings LTI** eller **Teams Classes LTI** for at registrere, og vælg derefter **Næste**.

5. Angiv et let identificerbart **registreringsnavn,** og vælg **Moodle** som LMS-platformen. Vælg **Næste**.

6. Du får en liste over nøgler, der skal føjes til dit Moodle-websted.

7. Åbn Moodle på en anden fane. Luk ikke fanen Microsoft LMS Gateway.

8. I Moodle skal du gå til **Plug-ins** til **webstedsadministration** >  > **Aktivitetsmoduler** > **Eksterne værktøjer** > **Administrer værktøjer**.

9. På siden **Administrer værktøjer** skal du vælge **Konfigurer et værktøj manuelt**.

10. Angiv et **værktøjsnavn**, f.eks. **Microsoft Teams-klasser**, under **Indstillinger for værktøj**. Vælg **LTI 1.3** som **LTI-version**. Vælg **URL-adresse til nøglesæt** som **Offentlig nøgletype**.

11. Derefter skal du kopiere nøglerne fra **Microsoft LTI-nøgler** til de tilsvarende værktøjsinput.
    1. **Url-nøglen til Microsofts destinationslink** går ind i feltet **URL-adresse til Værktøj** i Moodle.
    1. **Microsofts URL-adressenøgle til Open ID-forbindelse** går ind i feltet **Initier URL-adresse til logon** i Moodle.
    1. Microsofts **URL-adressenøgle til omdirigering** går ind i Feltet **URI(er) for Omdirigering** for Moodle.

12. Vælg **Gem ændringer**.

13. Det nye værktøj bør nu blive vist i afsnittet **Værktøjer** på moodles side **Administrer værktøjer** . Vælg listeikonet for at få vist **oplysninger om konfiguration af værktøj**.

14. Gå tilbage til fanen Microsoft LMS Gateway. Vælg **Næste** for at gå til trinnet **LMS med angivne registreringsnøgler** .

15. Kopiér og indsæt værdierne fra Moodles **konfigurationsoplysninger om værktøjet** til Microsofts **LMS-angivne trin for registreringsnøgler** .

  Indsæt værdierne på følgende måde:

  | På Moodle | På Microsoft LTI-registreringsportalen |
  | --------- | ------------------------------------ |
  | Platform-id | URL-adresse til udsteder-id |
  | Klient-id | Klient-id |
  | Installations-id | Installations-id |
  | URL-adresse til offentlige nøgleret | URL-adresse til nøglesæt |
  | URL-adresse til adgangstoken | URL-adresse til adgangstoken |
  | URL-adresse til godkendelsesanmodning | URL-adresse til platformgodkendelse |

  Vælg **Næste**.

16. Gennemse siden **Gennemse og tilføj** . Hvis der ikke er nogen fejl, skal du vælge **Gem og afslut**. Du får vist en meddelelse, der angiver, at registreringen lykkedes.

Du har fuldført registreringen af enten Teams-klasser eller Teams-møde-LTI-appen.

Hvis du også vil tilføje den anden app, skal du gentage trinnene ovenfor og vælge den anden Teams LTI-app i trin 4.

### <a name="add-teams-lti-apps-to-educators-moodle-courses"></a>Føj Teams LTI-apps til undervisernes Moodle-kurser

Når underviserne har registreret Teams LTI-apps, kan de føje appen Teams-klasser og appen Teams-møder til deres Moodle-kurser.

- [Vejledning til, hvordan du tilføjer appen Teams-klasser](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-ac6a1e34-32f7-45e6-b83e-094185a1e78a).
- [Educator-instruktioner til tilføjelse af Teams-mødeappen](https://support.microsoft.com/topic/use-microsoft-teams-meetings-in-your-lms-11b6095d-f90b-42b9-ab77-4dcff2bb3b76).

## <a name="technical-requirements-to-launch-teams-lti-apps"></a>Tekniske krav til start af Teams LTI-apps

Hvis du vil starte Teams LTI-apps i Moodle, er der nogle tekniske krav, der skal opfyldes.

> [!NOTE]
> It-administratorer og -undervisere kan registrere LTI-apps på LTI-appregistreringsportalen.

### <a name="it-admin-technical-requirements"></a>Tekniske krav til it-administrator

- Brug Moodle version 3.10 eller nyere.
- Download den nyeste Microsoft O365-plug-in til Moodle version 3.10 eller nyere.
- Få adgang til LTI-appsregistreringsportalen for at registrere LTI-apps.
  - Registreringen skal være fuldført på en skrivebordsenhed.
- Download den nyeste version af Microsoft Edge, Google Chrome, Safari eller Mozilla Firefox.

### <a name="educator-technical-requirements"></a>Tekniske krav til undervisere

- Få adgang til registreringsportalen for LTI-apps for at registrere LTI-apps, hvis it-administratoren ikke har registreret appsene.
  - Registreringen skal være fuldført på en skrivebordsenhed.
- Download den nyeste version af Microsoft Edge, Google Chrome, Safari eller Mozilla Firefox.
- [Teams LTI-apps til klasser og møder i Moodle](#add-teams-lti-apps-to-educators-moodle-courses).

### <a name="student-technical-requirements"></a>Tekniske krav til studerende

- Teams LTI-apps til klasser og møder i Moodle.
  - Studerende behøver ikke at foretage sig noget for at tilføje LTI-apps til Teams-klasser eller -møder.
