---
title: Administrer deling for Microsoft Whiteboard i GCC High-miljøer
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
description: Få mere at vide om, hvordan du administrerer deling for Microsoft Whiteboard i GCC High-miljøer.
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 3b16b55b1d8adc52318e8549a92ef703d68f548a
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/30/2022
ms.locfileid: "66858891"
---
# <a name="manage-sharing-for-microsoft-whiteboard-in-gcc-high-environments"></a>Administrer deling for Microsoft Whiteboard i GCC High-miljøer

>[!NOTE]
> Denne vejledning gælder for GCC High-miljøer (US Government Community Cloud).

Delingsoplevelsen varierer afhængigt af den enhed og klient, der bruges. 

## <a name="share-in-teams-meetings"></a>Del i Teams-møder

Når du deler et whiteboard i et Teams-møde, opretter Whiteboard et delingslink, der er tilgængeligt for alle i organisationen. Det deler derefter automatisk whiteboardet med alle brugere i lejeren i mødet.

>[!NOTE]
> Ekstern deling under et Teams-møde er endnu ikke tilgængelig, men tilføjes i en fremtidig version.

|Scenario |Lager og ejerskab |Delingsindstillinger |Delingsoplevelse |
|---------|---------|---------|---------|
|Start whiteboardet fra en stationær eller mobilenhed |Lager: OneDrive for Business<br><br>Ejer: Bruger, der opretter whiteboardet |Endnu ikke tilgængelig |Brugere i lejere: Kan oprette, få vist og samarbejde<br><br>Eksterne brugere: Endnu ikke tilgængelig<br><br>Delte enhedskonti: Endnu ikke tilgængelige |
|Start whiteboardet fra en Surface Hub eller Microsoft Teams-rum |Endnu ikke tilgængelig |         |         |

## <a name="add-as-a-tab-in-teams-channels-and-chats"></a>Tilføj som en fane i Teams-kanaler og -chats

Når du tilføjer et whiteboard som en fane i en Teams-kanal eller -chat, opretter Whiteboard et delingslink, der er tilgængeligt for alle i organisationen.

|Scenario  |Lager og ejerskab  |Delingsindstillinger  |Delingsoplevelse  |
|---------|---------|---------|---------|
|Føj whiteboardet til en kanal eller chat fra en skrivebords- eller mobilenhed  |Lager: OneDrive for Business<br><br>Ejer: Bruger, der opretter whiteboardet  |Ikke relevant  |Brugere i lejere: Kan starte, få vist og samarbejde<br><br>Eksterne brugere: Understøttes ikke  |

## <a name="create-and-share-in-whiteboard-native-clients"></a>Opret og del i oprindelige whiteboardklienter

Når du deler et whiteboard fra web-, skrivebords- eller mobilklienter, kan du vælge bestemte personer. Du kan også oprette et delingslink, der er tilgængeligt for alle i organisationen. 

>[!NOTE]
> Ekstern deling under et Teams-møde er endnu ikke tilgængelig, men tilføjes i en fremtidig version.

|Scenario  |Lager og ejerskab  |Delingsindstillinger  |Delingsoplevelse  |
|---------|---------|---------|---------|
|Opret whiteboardet fra en stationær eller mobilenhed  |Lager: OneDrive for Business<br><br>Ejer: Bruger, der opretter whiteboardet  |Ikke relevant  |Brugere i lejere: Kan dele i deres organisation<br><br>Eksterne brugere: Deling med eksterne brugere understøttes ikke i øjeblikket  |
|Opret whiteboardet fra en Surface Hub  |Lager: Lokal<br><br>Ejer: Ingen  |Ikke relevant  |Brugere i lejer (kommer snart): Brugeren kan logge på for at gemme og dele tavlen<br><br>Eksterne brugere: Deling med eksterne brugere understøttes ikke i øjeblikket |
|Opret whiteboardet ud fra Microsoft Teams-rum  |Endnu ikke tilgængelig         |         |         |

## <a name="see-also"></a>Se også

[Administrer adgang til Whiteboard – GCC High](manage-whiteboard-access-gcc-high.md)

[Administrer data for Whiteboard – GCC High](manage-data-gcc-high.md)

[Administrer klienter for Whiteboard – GCC High](manage-clients-gcc-high.md)
