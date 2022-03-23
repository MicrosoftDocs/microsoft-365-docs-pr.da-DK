---
title: Administrer Microsoft Defender for Endpoint-hændelser
description: Administrer hændelser ved at tildele den, opdatere dens status eller angive klassificeringen.
keywords: hændelser, administrer, tildel, status, klassificering, sand besked, falsk besked
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 45c08c5a3c304a23b5761d96a4d9aceb1b4f1562
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63593454"
---
# <a name="manage-microsoft-defender-for-endpoint-incidents"></a>Administrer Microsoft Defender for Endpoint-hændelser

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Håndtering af hændelser er en vigtig del af enhver cybersecurity-handling. Du kan administrere hændelser ved at vælge en hændelse fra **køen Hændelser eller** **ruden til administration af hændelser**. 


Hvis du vælger en hændelse fra **køen Hændelser, vises ruden Hændelsesstyring**, hvor du kan åbne hændelsessiden for at få flere oplysninger.


![Billede af ruden til administration af hændelser.](images/atp-incidents-mgt-pane-updated.png)

Du kan tildele hændelser til dig selv, ændre status og klassificering, omdøbe eller kommentere dem for at holde styr på deres fremskridt.

> [!TIP]
> For at få et hurtigt overblik over synligheden genereres hændelsesnavne automatisk baseret på beskedattributter som f.eks. antallet af slutpunkter, der påvirkes, brugere, der er påvirket, registreringskilder eller kategorier. Dette giver dig mulighed for hurtigt at forstå omfanget af hændelsen.
>
> For eksempel: *Hændelser i flere faser på flere slutpunkter rapporteret af flere kilder.*
>
> Hændelser, der fandtes før rullen af automatisk navngivning af hændelser, bevarer deres navne.
>


![Billede af siden med hændelsesdetaljer.](images/atp-incident-details-updated.png)

## <a name="assign-incidents"></a>Tildel hændelser
Hvis en hændelse ikke er blevet tildelt endnu, kan du vælge **Tildel til mig for** at tildele hændelsen til dig selv. Dette antager, at du ikke kun er ejerskab af hændelsen, men også alle de beskeder, der er knyttet til den.

## <a name="set-status-and-classification"></a>Angiv status og klassificering
### <a name="incident-status"></a>Hændelsesstatus
Du kan kategorisere hændelser (som **Aktive eller** Løst) **ved** at ændre deres status, efterhånden som undersøgelsen skrider frem. Dette hjælper dig med at organisere og administrere, hvordan dit team kan reagere på hændelser.

Din SoC-analytiker kan f.eks. gennemgå  dagens vigtige Aktive hændelser og beslutte at tildele dem til sig selv til undersøgelse.

Alternativt kan din SoC-analytiker angive hændelsen som **Løst** , hvis hændelsen er blevet løst. 

### <a name="classification"></a>Klassificering
Du kan vælge ikke at angive en klassificering eller beslutte at angive, om en hændelse er sand eller falsk. Dette hjælper teamet med at se mønstre og lære af dem.

### <a name="add-comments"></a>Tilføj kommentarer
Du kan tilføje kommentarer og få vist historiske begivenheder om en hændelse for at se tidligere ændringer af den.

Når der foretages en ændring eller kommentar til en besked, registreres den i sektionen Kommentarer og historik.

Tilføjede kommentarer vises med det samme i ruden.



## <a name="related-topics"></a>Relaterede emner
- [Kø over hændelser](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [Få vist og organiser køen hændelser](view-incidents-queue.md)
- [Undersøg hændelser](investigate-incidents.md)
