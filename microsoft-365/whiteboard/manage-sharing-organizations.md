---
title: Administrer deling for Microsoft Whiteboard
ms.author: chucked
author: chuckedmonson
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.prod: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du administrerer deling for Microsoft Whiteboard.
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 0d21c9e80e2f5f44a135e0f252eb90dfae408275
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/30/2022
ms.locfileid: "66858899"
---
# <a name="manage-sharing-for-microsoft-whiteboard"></a>Administrer deling for Microsoft Whiteboard

Delingsoplevelsen varierer, afhængigt af om du er i et Teams-møde, om du bruger en delt enhed, eller hvilke indstillinger for deling på lejerniveau der er aktiveret. Følgende scenarier gælder kun for nye whiteboards, der er oprettet, når Whiteboard skifter til at bruge OneDrive for Business lager. Der er ingen ændring af tidligere oprettede tavler, der stadig er gemt i Azure.

## <a name="share-in-teams-meetings"></a>Del i Teams-møder

Når du deler et whiteboard i et Teams-møde, opretter Whiteboard et delingslink, der er tilgængeligt for alle i organisationen. Det deler derefter automatisk whiteboardet med alle brugere i lejeren i mødet.

Der er en yderligere mulighed for midlertidigt samarbejde mellem eksterne og delte enhedskonti under et møde. Denne funktion gør det muligt for disse brugere midlertidigt at få vist og samarbejde på whiteboards, når de deles i et Teams-møde, på samme måde som PowerPoint Live deling.

>[!NOTE]
> Dette er ikke et delingslink og giver ikke adgang til filen. Det giver mulighed for midlertidig visning og samarbejde på whiteboardet, så længe Teams-mødet kun varer.

Hvis du har aktiveret ekstern deling for OneDrive for Business, kræves der ingen yderligere handling.

Hvis du begrænser ekstern deling for OneDrive for Business, kan du begrænse den og blot aktivere en ny indstilling, så eksterne og delte enhedskonti fungerer. Det gør du ved at følge disse trin:

1. Brug PowerShell til at oprette forbindelse til din lejer, og sørg for, at SharePoint Online-modulet opdateres ved at køre følgende kommando:

   <pre><code class="lang-powershell">Update-Module -Name Microsoft.Online.SharePoint.PowerShell</code></pre>
 
2. Kør derefter følgende <code>Set-SPOTenant</code> cmdlet:

   <pre><code class="lang-powershell">Set-SPOTenant -AllowAnonymousMeetingParticipantsToAccessWhiteboards On</code></pre>

Denne indstilling gælder kun for whiteboards og erstatter de tidligere delte indstillinger **, OneDriveLoopSharingCapability** og **CoreLoopSharingCapability**. Disse indstillinger er ikke længere tilgængelige og kan ignoreres.

>[!NOTE]
> Indstillingen **Anonyme brugere kan som standard interagere med apps i møder i** Teams-mødet er aktiveret. Hvis du har deaktiveret den, har anonyme brugere (i modsætning til gæster eller brugere i organisationsnetværket) ikke adgang til whiteboardet under mødet.

Det bør tage ca. 60 minutter at anvende disse ændringer på tværs af din lejer. 

|Scenario  |Lager og ejerskab  |Delingsindstillinger  |Delingsoplevelse  |
|---------|---------|---------|---------|
|Start whiteboardet fra en stationær eller mobilenhed  |Lager: OneDrive for Business<br><br>Ejer: Bruger, der opretter whiteboardet  |Aktiveret  |Brugere i lejere: Kan oprette, få vist og samarbejde<br><br>Eksterne brugere: Kan kun få vist og samarbejde under mødet (knappen til deling af et whiteboard vises ikke for eksterne brugere)<br><br>Delte enhedskonti: Kan kun få vist og samarbejde under mødet  |
|Start whiteboardet fra en stationær eller mobilenhed  |Lager: OneDrive for Business<br><br>Ejer: Bruger, der opretter whiteboardet  |Deaktiveret  |Brugere i lejere: Kan starte, få vist og samarbejde<br><br>Eksterne brugere: Der kan ikke vises eller samarbejdes<br><br>Delte enhedskonti: Der kan ikke vises eller samarbejdes  |
|Start whiteboardet fra en Surface Hub eller Microsoft Teams-rum  |Lager: Azure (dette flyttes til OneDrive for Business i fremtiden)<br><br>Ejer: Mødedeltager   |Ikke relevant  |Brugere i lejere: Kan starte, få vist og samarbejde<br><br>Eksterne brugere: Kan kun få vist og samarbejde under mødet<br><br>Delte enhedskonti: Kan kun få vist og samarbejde under mødet  |

## <a name="add-as-a-tab-in-teams-channels-and-chats"></a>Tilføj som en fane i Teams-kanaler og -chats

Når du tilføjer et whiteboard som en fane i en Teams-kanal eller -chat, opretter Whiteboard et delingslink, der er tilgængeligt for alle i organisationen.

|Scenario  |Lager og ejerskab  |Delingsindstillinger  |Delingsoplevelse  |
|---------|---------|---------|---------|
|Føj whiteboardet til en kanal eller chat fra en skrivebords- eller mobilenhed  |Lager: OneDrive for Business<br><br>Ejer: Bruger, der opretter whiteboardet  |Ikke tilgængelig (gælder kun for møder)  |Brugere i lejere: Kan starte, få vist og samarbejde<br><br>Eksterne brugere: Understøttes ikke<br><br>Teams-gæster: Kan få vist og samarbejde<br><br>Konti for delte enheder: Ikke tilgængelig  |

## <a name="create-and-share-in-whiteboard-native-clients"></a>Opret og del i oprindelige whiteboardklienter

Når du deler whiteboards fra web-, skrivebords- eller mobilklienter, kan du vælge bestemte personer. Du kan også oprette et delingslink, der er tilgængeligt for alle i organisationen. 

>[!NOTE]
> Ekstern deling under et Teams-møde er endnu ikke tilgængelig, men tilføjes i en fremtidig version.

|Scenario  |Lager og ejerskab  |Delingsindstillinger  |Delingsoplevelse  |
|---------|---------|---------|---------|
|Opret whiteboardet fra en stationær eller mobilenhed  |Lager: OneDrive for Business<br><br>Ejer: Bruger, der opretter whiteboardet  |Ikke tilgængelig (gælder kun for møder)  |Brugere i lejere: Kan dele i deres organisation<br><br>Eksterne brugere: Deling med eksterne brugere understøttes ikke i øjeblikket  |
|Opret whiteboardet fra en Surface Hub  |Lager: Lokal<br><br>Ejer: Ingen (medmindre brugeren logger på for at gemme og dele tavlen, som gemmes i OneDrive for Business. Nem deling vil blive tilføjet igen i fremtiden.  |Ikke tilgængelig (gælder kun for møder)  |Brugere i lejer: Brugeren skal logge på for at gemme og dele tavlen (Nem deling tilføjes fremover)<br><br>Eksterne brugere: Deling med eksterne brugere understøttes ikke i øjeblikket uden for et Teams-møde  |
|Opret whiteboardet ud fra Microsoft Teams-rum  |Understøttes endnu ikke  |Ikke tilgængelig (gælder kun for møder)  |Understøttes endnu ikke  |

## <a name="see-also"></a>Se også

[Administrer adgang til Whiteboard](manage-whiteboard-access-organizations.md)

[Administrer data for Whiteboard](manage-data-organizations.md)

[Installer whiteboard på Windows](deploy-on-windows-organizations.md)