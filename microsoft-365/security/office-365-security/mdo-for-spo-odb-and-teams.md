---
title: Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 26261670-db33-4c53-b125-af0662c34607
ms.collection:
- M365-security-compliance
- SPO_Content
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
description: Få mere at Microsoft Defender for Office 365 om filer i SharePoint Online, OneDrive for Business og Microsoft Teams.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 220bb976ebe701e5db5f03370a1a7c188f197cb1
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475757"
---
# <a name="safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams i [Microsoft Defender for Office 365](whats-new-in-defender-for-office-365.md) giver et ekstra lag beskyttelse til filer, der allerede er blevet scannet asynkront ved den almindelige [virusregistrering i Microsoft 365](virus-detection-in-spo.md). Pengeskab vedhæftede filer til SharePoint, OneDrive og Microsoft Teams hjælper med at registrere og blokere eksisterende filer, der identificeres som skadelige i teamwebsteder og dokumentbiblioteker.

Pengeskab vedhæftede filer til SharePoint, OneDrive og Microsoft Teams ikke som standard. Hvis du vil slå den til, [skal du se Pengeskab Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

## <a name="how-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams-works"></a>Sådan Pengeskab vedhæftede filer til SharePoint, OneDrive og Microsoft Teams fungerer

Når Pengeskab vedhæftede filer til SharePoint, OneDrive og Microsoft Teams er aktiveret og identificerer en fil som skadelig, låses filen ved hjælp af direkte integration med fillagrene. Følgende billede viser et eksempel på en ondsindet fil, der er registreret i et bibliotek.

:::image type="content" source="../../media/2bba71cc-7ad1-4799-8b9d-d56f923db3a7.png" alt-text="Filerne i en OneDrive for Business registreret som skadelige" lightbox="../../media/2bba71cc-7ad1-4799-8b9d-d56f923db3a7.png":::

Selvom den blokerede fil stadig er angivet i dokumentbiblioteket og i web-, mobil- eller computerprogrammer, kan andre ikke åbne, kopiere, flytte eller dele filen. Men de kan slette den blokerede fil.

Her er et eksempel på, hvordan en blokeret fil ser ud på en mobilenhed:

:::image type="content" source="../../media/cb1c1705-fd0a-45b8-9a26-c22503011d54.png" alt-text="Muligheden for at slette en blokeret fil fra OneDrive for Business fra OneDrive-mobilappen" lightbox="../../media/cb1c1705-fd0a-45b8-9a26-c22503011d54.png":::

Som standard kan folk downloade en blokeret fil. Sådan ser download af en blokeret fil ud på en mobilenhed:

:::image type="content" source="../../media/be288a82-bdd8-4371-93d8-1783db3b61bc.png" alt-text="Muligheden for at downloade en blokeret fil i OneDrive for Business" lightbox="../../media/be288a82-bdd8-4371-93d8-1783db3b61bc.png":::

SharePoint Onlineadministratorer kan forhindre folk i at downloade skadelige filer. Du kan finde en vejledning [under Brug SharePoint Online PowerShell til at forhindre brugere i at downloade skadelige filer](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).

Hvis du vil have mere at vide om brugeroplevelsen, når en fil er blevet registreret som skadelig, skal du se Hvad du skal gøre, når der findes en skadelig fil i [SharePoint Online, OneDrive eller Microsoft Teams](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2).

## <a name="view-information-about-malicious-files-detected-by-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Få vist oplysninger om skadelige filer, der registreres Pengeskab vedhæftede filer til SharePoint, OneDrive og Microsoft Teams

Filer, der er identificeret som skadelige ved hjælp af Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams vises i rapporter [til Microsoft Defender for Office 365](view-reports-for-mdo.md) og i [Stifinder (](threat-explorer.md)og registreringer i realtid).

Når en fil identificeres som skadelig ved hjælp af Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams, er filen også tilgængelig i karantæne, men kun for administratorer. Få mere at vide under [Administrer filer i karantæne i Defender for Office 365](manage-quarantined-messages-and-files.md#use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365).

## <a name="keep-these-points-in-mind"></a>Husk disse punkter

- Defender for Office 365 scanner ikke hver enkelt fil i SharePoint Online, OneDrive for Business eller Microsoft Teams. Dette er tilsdesignet. Filer scannes asynkront. Processen bruger delings- og gæsteaktivitetshændelser sammen med smarte heuristics og trusselssignaler til at identificere skadelige filer.

- Sørg for, SharePoint websteder er konfigureret til at bruge [den moderne oplevelse](/sharepoint/guide-to-sharepoint-modern-experience). Defender for Office 365 gælder, uanset om den moderne oplevelse eller den klassiske visning bruges, men visuelle indikatorer for, at en fil er blokeret, er kun tilgængelige i den moderne oplevelse.

- Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams er en del af organisationens overordnede strategi for trusselsbeskyttelse, som omfatter beskyttelse mod spam og malware i Exchange Online Protection (EOP) samt Pengeskab  Links og Pengeskab vedhæftede filer i Microsoft Defender for Office 365. Du kan få mere at vide [under Beskyt mod trusler i Office 365](protect-against-threats.md).
