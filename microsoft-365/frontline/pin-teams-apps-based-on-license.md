---
title: Tilpas Teams-apps til dine frontlinjearbejdere
author: LanaChin
ms.author: v-lanachin
ms.reviewer: aaglick
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Få mere at vide om den skræddersyede appoplevelse til frontlinjemedarbejdere i Microsoft Teams.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 24393b11abc9bb7ba4c6736daca4dfa5969f94b8
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66824018"
---
# <a name="tailor-teams-apps-for-your-frontline-workers"></a>Tilpas Teams-apps til dine frontlinjearbejdere

> [!NOTE]
> Denne funktion udrulles i øjeblikket og er muligvis ikke tilgængelig i din organisation endnu. Hvis du vil holde styr på kommende Teams-funktioner, kan du se [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=microsoft%2Cteams).

## <a name="overview"></a>Oversigt

Teams fastgør apps baseret på licens for at give dine frontlinjemedarbejdere en indbygget oplevelse i Teams, der er skræddersyet til deres behov. 

Med den skræddersyede frontline-app får dine frontlinjemedarbejdere de mest relevante apps i Teams, uden at administratoren behøver at foretage sig noget.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4VuCH]

## <a name="tailored-frontline-app-experience"></a>Skræddersyet frontlineappoplevelse

Apps fastgøres til applinjen, som er linjen nederst i Teams-mobilklienterne (iOS og Android) og på siden af Teams-skrivebordsklienten. Følgende apps er fastgjort til brugere, der har en [F-licens](https://www.microsoft.com/microsoft-365/enterprise/frontline#office-SKUChooser-0dbn8nt):

- [Aktivitet](https://support.microsoft.com/office/explore-the-activity-feed-in-teams-91c635a1-644a-4c60-9c98-233db3e13a56)
- [Chat](https://support.microsoft.com/office/get-started-with-chat-0b506ce2-eb6d-4fca-9668-e56980ba755e)
- [Hold](https://support.microsoft.com/office/teams-and-channels-in-microsoft-teams-c6d0e61d-a61e-44a6-a972-04f2a8fa4155)
- [Walkie Talkie](https://support.microsoft.com/office/get-started-with-teams-walkie-talkie-25bdc3d5-bbb2-41b7-89bf-650fae0c8e0c)
- [Opgaver](https://support.microsoft.com/office/use-the-tasks-app-in-teams-e32639f3-2e07-4b62-9a8c-fd706c12c070)
- [Skift](https://support.microsoft.com/office/what-is-shifts-f8efe6e4-ddb3-4d23-b81b-bb812296b821)
- [Godkendelser](https://support.microsoft.com/office/what-is-approvals-a9a01c95-e0bf-4d20-9ada-f7be3fc283d3)

**Teams Mobile**

:::image type="content" source="media/tailored-teams-apps-mobile.png" alt-text="Den skræddersyede frontlineappoplevelse på Teams Mobile" lightbox="media/tailored-teams-apps-mobile.png"::: 

**Teams-skrivebord**

:::image type="content" source="media/tailored-teams-apps-desktop.png" alt-text="Den skræddersyede frontlineappoplevelse på Teams Desktop" lightbox="media/tailored-teams-apps-desktop.png"::: 

## <a name="admin-controls"></a>Administration kontrolelementer

> [!NOTE]
> Indstillingen **Fastgørelse af bruger** skal være aktiveret i den globale [appkonfigurationspolitik](/microsoftteams/teams-app-setup-policies) (standard i hele organisationen), for at funktionen kan træde i kraft.

Den tilpassede frontlineappoplevelse styres af indstillingen **Vis tilpassede apps** for hele organisationen på siden [Administrer apps](/microsoftteams/manage-apps#manage-org-wide-app-settings) i Teams Administration. Hvis funktionen er slået til, får alle brugere i din organisation, der har en F-licens, den skræddersyede appoplevelse.

Vær opmærksom på, at alle brugerdefinerede [politikker for konfiguration af apps](/microsoftteams/teams-app-setup-policies) , der er tildelt brugerne, har forrang. Det betyder, at hvis en bruger allerede har fået tildelt en brugerdefineret appkonfigurationspolitik, får brugeren den konfiguration, der er defineret i politikken for konfiguration af den brugerdefinerede app. Hvis du vil vide mere om, hvordan funktionen fungerer sammen med Teams-apppolitikker, herunder den globale politik for konfiguration af apps, skal du se afsnittet [Scenarier](#scenarios) senere i denne artikel.

Denne funktion er som standard slået til. Men hvis du ikke vil have den skræddersyede frontlineappoplevelse, der leveres af Microsoft, kan du slå funktionen fra. Sådan slår du funktionen fra eller til:

1. I venstre navigationsrude i Microsoft Teams Administration skal du gå til **Teams-apps** > **Administrer apps** og derefter vælge **Appindstillinger for hele organisationen**.
2. Under **Tilpassede apps** skal du skifte til Slå **Vis tilpassede apps** til **Fra** eller **Til**.

    :::image type="content" source="media/tailored-teams-apps-admin-center.png" alt-text="Skærmbillede af indstillingen Vis tilpassede apps på siden Administrer apps i Teams Administration" lightbox="media/tailored-teams-apps-admin-center.png":::

## <a name="scenarios"></a>Scenarier

### <a name="how-does-the-tailored-frontline-app-experience-affect-my-global-app-setup-policy"></a>Hvordan påvirker den tilpassede frontlineappoplevelse min globale appkonfigurationspolitik?

Få mere at vide om, hvordan den tilpassede frontlineappoplevelse fungerer sammen med den globale politik for konfiguration af apps. Scenarierne i denne tabel gælder for frontlinemedarbejdere, der har en F-licens og den globale appkonfigurationspolitik, hvor **Brugerfastgørelse** er slået til.

|Hvis... |Derefter... |
|---------|---------|
|En frontlinemedarbejder har den globale appkonfigurationspolitik, og funktionen er slået fra. |Frontlinemedarbejderen henter de apps, der er defineret i den globale appkonfigurationspolitik.|
|En frontlinemedarbejder har den globale appkonfigurationspolitik, og funktionen er slået til.     | Frontlinemedarbejderen får den skræddersyede oplevelse med frontlineappen. Apps, der er defineret i den globale politik for appkonfiguration, er fastgjort under de tilpassede apps.      |
|Du opdaterer den globale appkonfigurationspolitik, og funktionen er slået til.     |Frontlinemedarbejderen får den skræddersyede oplevelse af frontlineappen, og de apps, der er defineret i den globale appkonfigurationspolitik, er fastgjort under de skræddersyede apps.         |
|En frontlinjemedarbejder har den globale appkonfigurationspolitik, og **Fastgørelse af bruger** er slået fra. |Frontlinemedarbejderen henter de apps, der er defineret i den globale appkonfigurationspolitik.|
|En frontlinjemedarbejder har den globale appkonfigurationspolitik, og den globale appkonfigurationspolitik ændres, så den inkluderer en line of business-app (LOB) på den anden placering på applisten. |LOB-appen er fastgjort under de skræddersyede apps. Frontlinjemedarbejderen kan ændre apprækkefølgen, hvis **Fastgørelse af bruger** er slået til.         |
|En frontlinjemedarbejder har den globale konfigurationspolitik, og den globale appkonfigurationspolitik ændres, så den inkluderer Skift på den første placering.  |Skift er fastgjort til den sjette position, som defineret af den skræddersyede frontlineappoplevelse. Frontlinjemedarbejderen kan ændre apprækkefølgen, hvis **Fastgørelse af bruger** er slået til.          |

### <a name="how-does-the-tailored-frontline-app-experience-work-with-other-teams-app-policies"></a>Hvordan fungerer den tilpassede frontlineappoplevelse med andre Politikker for Teams-apps?

Få mere at vide om, hvordan den tilpassede frontlineapp fungerer sammen med andre Politikker for Teams-apps.

|Hvis...  |Derefter... |
|---------|---------|
Funktionen er slået fra.   | Frontlinjemedarbejderen får tildelt de apps, der er defineret i den globale appkonfigurationspolitik eller den brugerdefinerede appkonfigurationspolitik.          |
|En frontlinjemedarbejder har en brugerdefineret appkonfigurationspolitik, og funktionen er slået til.    |Frontlinemedarbejderen henter de apps, der er defineret i politikken for konfiguration af brugerdefinerede apps.          |
|En app i den skræddersyede frontlineappoplevelse er blokeret for en bruger eller for din organisation.      |Den tilpassede frontlineappoplevelse hædr [app-tilladelsespolitikken](/microsoftteams/teams-app-permission-policies). Hvis en app er blokeret, kan frontlinjemedarbejderen ikke se den blokerede app.           |
|En app i den tilpassede frontlineappoplevelse er allerede defineret i en appkonfigurationspolitik, og funktionen er slået til. |Appen er fastgjort på baggrund af den rækkefølge, der er defineret af listen over tilpassede apps.        |
|En bruger har en E-, A- eller G-licens, og funktionen er slået til.   | Brugeren får ikke den skræddersyede frontlineappoplevelse. I øjeblikket gælder oplevelsen kun for brugere, der har en F-licens.        |

> [!NOTE]
> Du kan ikke ændre apps eller rækkefølgen af apps i den skræddersyede frontlineappoplevelse. Hvis du vil foretage ændringer indtil videre, kan du konfigurere din egen brugerdefinerede oplevelse. Det gør du ved først at deaktivere funktionen. Opret derefter [en brugerdefineret appkonfigurationspolitik](/microsoftteams/teams-app-setup-policies), og [tildel den til brugere eller grupper](/microsoftteams/assign-policies-users-and-groups).

## <a name="related-articles"></a>Relaterede artikler

- [Administrer Walkie Talkie-appen i Teams](/microsoftteams/walkie-talkie?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Administrer appen Opgaver i Teams](/microsoftteams/manage-tasks-app?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Administrer appen Skift i Teams](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Administrer appen Godkendelser i Teams](/microsoftteams/approval-admin?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Administrer politikker for konfiguration af apps i Teams](/microsoftteams/teams-app-setup-policies)
- [Administrer politikker for apptilladelser i Teams](/microsoftteams/teams-app-permission-policies)
