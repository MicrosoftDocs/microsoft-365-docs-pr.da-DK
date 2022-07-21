---
title: Installer Microsoft Whiteboard på Windows 10 enheder
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
description: Få mere at vide om, hvordan du installerer Microsoft Whiteboard på enheder, der kører Windows 10 eller nyere versioner.
ms.openlocfilehash: 31341bc446313c54d95e14efdf569ba6e0b5263f
ms.sourcegitcommit: 24827a509b3e78959ce67679646e572a0c996282
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66917183"
---
# <a name="deploy-microsoft-whiteboard-on-windows-10-devices"></a>Installer Microsoft Whiteboard på Windows 10 enheder

Whiteboard kan installeres på enheder, der kører Windows 10 eller nyere, ved hjælp af Microsoft Intune eller Microsoft Configuration Manager (tidligere System Center Configuration Manager). Whiteboard understøttes ikke på Windows Server.

- **Microsoft Intune ved hjælp af en onlinelicenstilstand** – denne proces giver dig mulighed for at angive grupper af brugere, der skal have adgang til Whiteboard-appen.

- **Microsoft Configuration Manager ved hjælp af manuel offlineinstallation og opdateringer** – Denne proces giver dig mulighed for at installere Whiteboard og derefter opdatere det manuelt hver 2.-4. uge.

>[!NOTE]
> Vi anbefaler, at du bruger Microsoft Intune. Brug af Microsoft Configuration Manager kræver, at it-tjenesten løbende pakker og installerer opdateringer for at sikre, at brugerne kører en opdateret version.

## <a name="install-whiteboard-using-microsoft-intune"></a>Installer Whiteboard ved hjælp af Microsoft Intune

1. Tilføj Whiteboard som en tilgængelig app ved hjælp af trinnene i denne artikel: [Føj Microsoft Store-apps til Microsoft Intune](/mem/intune/apps/store-apps-windows).

2. Tildel appen til en gruppe ved hjælp af trinnene i denne artikel: [Tildel apps til grupper med Microsoft Intune](/mem/intune/apps/apps-deploy).

## <a name="install-whiteboard-using-microsoft-configuration-manager"></a>Installer Whiteboard ved hjælp af Microsoft Configuration Manager

1. Log på [Microsoft Store til Virksomheder](https://businessstore.microsoft.com) ved hjælp af en global administratorkonto.

2. Vælg **Administrer** i overskriften.

3. I navigationsruden til højre skal du vælge **Indstillinger** og derefter aktivere **Vis offlineapps**.

4. Vent 10-15 minutter på overførsel.

5. Derefter skal du gå til [appen Whiteboard](https://businessstore.microsoft.com/store/details/microsoft-whiteboard/9mspc6mp8fm4).

6. Vælg **Hent appen**, og acceptér derefter licensvilkårene.

7. Gå tilbage til programsiden.

8. Vælg **Offline** i rullemenuen **Licenstype**.

9. Vælg **Administrer**.

10. Denne handling fører dig til siden lagerstyring, som nu giver mulighed **for at downloade pakken til offlinebrug**.

11. Vælg arkitekturversionen, og download den derefter.

12. Så snart du har downloadet appen, kan du udrulle den via Configuration Manager. Hvis du vil oprette en opdateringspakke, skal du følge trin 7-10 for at downloade en nyere version og pakke den til Configuration Manager.

13. Du kan få flere oplysninger under [Installér programmer til en enhed](/mem/configmgr/apps/deploy-use/install-app-for-device).

## <a name="see-also"></a>Se også

[Administrer adgang til Whiteboard](manage-whiteboard-access-organizations.md)

[Administrer data for Whiteboard](manage-data-organizations.md)

[Administrer deling for Whiteboard](manage-sharing-organizations.md)

