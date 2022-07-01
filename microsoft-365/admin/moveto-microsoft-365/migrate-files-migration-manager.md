---
title: Overfør Google-filer til Microsoft 365 til virksomheder
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
ms.custom:
- AdminSurgePortfolio
- adminvideo
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Få mere at vide om, hvordan du overfører Google-filer til Microsoft 365 til virksomheder ved hjælp af SharePoint Migration Manager.
ms.openlocfilehash: 68b3a0455a2bf57e35308c428bf2b5de3e4b5983
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602110"
---
# <a name="migrate-google-files-to-microsoft-365-for-business-with-migration-manager"></a>Overfør Google-filer til Microsoft 365 til virksomheder med Migration Manager

Se [Hjælp til små virksomheder i Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2197659) på YouTube.

## <a name="watch-migrate-google-files-to-microsoft-365-for-business"></a>Se: Overfør Google-filer til Microsoft 365 til virksomheder

Se denne video og andre på vores [YouTube-kanal](https://go.microsoft.com/fwlink/?linkid=2198217).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWSx43?autoplay=false]

Når du flytter til Microsoft 365 til virksomheder fra Google Workspace, skal du overføre dine filer fra Google Drev. Du kan bruge SharePoint Migration Manager til at flytte filer fra personlige og delte drev. Denne video og en oversigt over de påkrævede trin giver dig et overblik over, hvordan du gør dette. Du kan få mere at vide under [Overfør Google Workspace til Microsoft 365 med Overførselssstyring](/sharepointmigration/mm-google-overview).

> [!NOTE]
> Overførselsstyring opretter en kopi af filerne og flytter kopierne til Microsoft 365 til virksomheder. De oprindelige filer vil bo i Google Drev også.

## <a name="before-you-start"></a>Før du starter

Alle brugerne skal være logget på Microsoft 365 til virksomheder og konfigurere deres OneDrive for Business. Det gør du ved at gå til [office.com](https://office.com), logge på med dine legitimationsoplysninger til Microsoft 365 til virksomheder og derefter vælge OneDrive.

## <a name="install-the-microsoft-365-migration-app"></a>Installér Microsoft 365 Migration-appen

Brug følgende trin til at installere Microsoft 365 Migration-appen i dit Google Workspace-miljø. 
1. Vælg **Overførsel** i SharePoint Administration Center.
2. På siden **Migrering** i afsnittet **Google Workspace** skal du vælge **Kom i gang**.
3. På siden **Overfør dit Google Workspace-indhold til Microsoft 365** skal du vælge **Opret forbindelse til Google Workspace**.
4. Vælg **Installér og godkend**.
5. På siden **Google Workspace Marketplace** skal du vælge **Log på** og angive dine legitimationsoplysninger som administrator af Google Workspace.
6. Vælg **Domæneinstallation**.
7. Vælg **Fortsæt**.
8. Markér afkrydsningsfeltet, og vælg derefter **Tillad**.
9. Når installationen er fuldført, skal du vælge **Udført**.
10. Gå tilbage til siden **Installér overførselsappen** , og vælg **Næste**.
11. Vælg **Log på Google Workspace**, og angiv derefter dine legitimationsoplysninger som administrator af Google Workspace.
12. Vælg **Udfør**.

## <a name="select-and-scan-your-drives"></a>Vælg og scan dine drev

Når du har installeret Microsoft 365 Migration App i dit Google-miljø, kan du nu vælge de drev, du vil overføre, og derefter scanne dem for at sikre, at de er sikre at kopiere til Microsoft 365.

1. Under fanen **Scan** skal du vælge de Google-drev, du vil kopiere til Microsoft 365.
2. Vælg **Scan**. Når scanningen er fuldført, vises scanningsstatussen **Klar til overførsel** på drevene.
3. Vælg **Kopiér til overførsel**.

## <a name="start-the-migration"></a>Start migreringen

Når du har valgt og scannet de drev, du vil overføre, skal du bruge følgende trin til at overføre dem.

1. Kontrollér destinationsstierne for de drev, du vil overføre, under fanen **Overførsel** . Rediger dem, hvis det er nødvendigt.
2. Vælg de drev, du vil overføre, og vælg derefter **Overfør**. 
3. Når overførslen er fuldført, vises **overførselsstatussen** **Fuldført** på hvert drev.