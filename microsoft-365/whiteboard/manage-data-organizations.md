---
title: Administrer data til Microsoft Whiteboard
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
description: Få mere at vide om dataopbevaring for Microsoft Whiteboard i Azure og OneDrive for Business.
ms.openlocfilehash: 103a48b01aa7ad87d0e3f84e6093344ea9cce0f0
ms.sourcegitcommit: 24827a509b3e78959ce67679646e572a0c996282
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66917623"
---
# <a name="manage-data-for-microsoft-whiteboard"></a>Administrer data til Microsoft Whiteboard

Whiteboardindhold gemmes både i Azure og OneDrive for Business. Nye whiteboards gemmes i OneDrive for Business. Den eneste undtagelse er whiteboards, der startes fra en Surface Hub, gemmes i Azure (som flyttes til OneDrive for Business i fremtiden). Du kan få flere oplysninger under [Administrer deling i Whiteboard](manage-sharing-organizations.md).

## <a name="azure-storage-overview"></a>Oversigt over Azure Storage

Whiteboard gemmer i øjeblikket indhold sikkert i Azure. Data kan være gemt på forskellige placeringer, afhængigt af landet, og når Whiteboard skiftede til lagring af nyt indhold på disse placeringer. Hvis du vil kontrollere, hvor nye data oprettes, skal du se [Hvor dine Microsoft 365-kundedata er gemt](/microsoft-365/enterprise/o365-data-locations). 

Indhold i Azure understøtter ikke DLP (Forebyggelse af datatab), eDiscovery, opbevaringspolitikker og lignende funktioner. Indhold kan administreres ved hjælp af [Whiteboard PowerShell-cmdlet'er](/powershell/module/whiteboard/), og med tiden skal dette indhold enten overføres til OneDrive for Business eller slettes.

### <a name="if-a-user-account-is-deleted-in-azure"></a>Hvis en brugerkonto slettes i Azure

Vi ændrer, hvordan whiteboards gemmes, når en brugers konto slettes i Azure. Før ændringen, da en brugers konto blev slettet, blev whiteboards, som brugeren ejede, også slettet, men whiteboards, der blev delt med andre, blev ikke slettet.

>[!NOTE]
> Whiteboards, der er gemt i OneDrive for Business, håndteres som alt andet indhold i OneDrive for Business. Du kan få flere oplysninger under [Angiv OneDrive-opbevaring for slettede brugere](/onedrive/set-retention).

Fra **den 1. juni 2022** er funktionsmåden for whiteboards på Azure ændret. Alle whiteboards, der deles med andre brugere, slettes.

Hvis du vil bevare en slettet brugers whiteboards, *før* du sletter kontoen, kan du overføre ejerskabet. Du kan overføre et enkelt whiteboard eller dem alle til en anden bruger. 

- Følg disse instruktioner for at [overføre alle whiteboards](/powershell/module/whiteboard/invoke-transferallwhiteboards).

- Du kan få flere oplysninger om, hvordan du sletter brugerkonti, under [Slet en bruger fra din organisation](/microsoft-365/admin/add-users/delete-a-user).

Sørg for, at enhver sletningsproces eller et script håndterer denne ændring. Hvis du har det fint med, at whiteboards slettes, kræves der ingen handling. 

## <a name="onedrive-for-business-storage-overview"></a>oversigt over OneDrive for Business lager

Whiteboards oprettes i mappen OneDrive for Business for den person, der starter whiteboardet (SharePoint understøttes endnu ikke). Denne proces gælder for alle whiteboards, der er oprettet i de separate Whiteboard-programmer og i Microsoft Teams-møder, -chats og -kanaler. Den eneste undtagelse er whiteboards, der startes fra en Surface Hub, gemmes i Azure (som flyttes til OneDrive for Business i fremtiden).

Alle brugere, der ikke har OneDrive for Business klargjort, kan ikke længere oprette nye whiteboards, når denne ændring implementeres. De kan dog stadig redigere deres tidligere oprettede tavler. De kan også samarbejde om alle whiteboards, der deles med dem af andre, som har OneDrive for Business.

Et gennemsnitligt whiteboard kan være alt fra 50 KB til 1 MB og placeret, uanset hvor dit OneDrive for Business indhold er placeret. Hvis du vil kontrollere, hvor data for din lejer er gemt, skal du se [Hvor dine Microsoft 365-kundedata er gemt](/microsoft-365/enterprise/o365-data-locations). Se derefter på placeringen for OneDrive for Business.

### <a name="controls-for-onedrive-for-business-storage"></a>Kontrolelementer til OneDrive for Business lager 

Du kan administrere Whiteboard-data ved hjælp af eksisterende OneDrive for Business kontrolelementer. Du kan få flere oplysninger i [OneDrive-vejledning til virksomheder](/onedrive/plan-onedrive-enterprise).

Du kan bruge eksisterende OneDrive for Business værktøjer til at opfylde DSR-anmodninger (Data Subject Requests) for General Data Protection Regulation (GDPR). Hvis du vil sikre dig, at alle tidligere ændringer fjernes fra filen, skal du slette hele filen.

Whiteboardfiler kan flyttes på samme måde som andet indhold i OneDrive for Business. Men del links og tilladelser flyttes muligvis ikke.

Understøttede datakontrolelementer i dag:

- Opbevaringspolitikker
- Kvote
- Juridisk venteposition
- DLP
- Grundlæggende eDiscovery – .whiteboard-filerne gemmes som filer i forfatterens OneDrive for Business. De er indekseret til søgning efter nøgleord og filtype, men de er ikke tilgængelige til eksempelvisning eller gennemsyn. Ved eksport skal en administrator uploade filen tilbage til OneDrive for Business for at få vist indholdet. Der er planlagt yderligere support fremover.

Datakontrolelementer, der er planlagt for fremtidige udgivelser:

- Følsomhedsmærkater
- Analytics
- Yderligere eDiscovery-support

## <a name="see-also"></a>Se også

[Administrer adgang til Whiteboard](manage-whiteboard-access-organizations.md)

[Administrer deling for Whiteboard](manage-sharing-organizations.md)

[Installer whiteboard på Windows](deploy-on-windows-organizations.md)


