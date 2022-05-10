---
title: Rutediagram, der bestemmer, hvornår et element bevares eller slettes
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Brug et rutediagram til at bestemme resultatet, når et element har flere opbevaringspolitikker eller en opbevaringsmærkat og opbevaringspolitikker
ms.openlocfilehash: cf35a89faf3ed526c94acf362f1a927eb36420f0
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286796"
---
# <a name="flowchart-to-determine-when-an-item-will-be-retained-or-permanently-deleted"></a>Rutediagram, der bestemmer, hvornår et element bevares eller slettes permanent

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug følgende rutediagram til at anvende [principperne for opbevaring af](retention.md#the-principles-of-retention-or-what-takes-precedence) et element for at afgøre, om systemet vil bevare eller slette det permanent som følge af en opbevaringsmærkat eller opbevaringspolitik.

Dette logikflow bruges til et element, når en af følgende betingelser gælder:

- Der anvendes mere end én opbevaringspolitik
- Der er en opbevaringsmærkat og en eller flere opbevaringspolitikker

Når et element er i eDiscovery-venteposition (eller de ældre teknologier inden for procesførelse eller In-Place venteposition), bevares det altid før beslutningsflowene for opbevaringspolitikker og en opbevaringsmærkat.

Hvis du ikke kender nogen af de ord, der bruges i dette rutediagram, skal du se [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md).


   ![Rutediagram, der bestemmer, hvornår et element bevares eller slettes permanent.](../media/retention-flowchart.svg)

> [!NOTE]
> Det er vigtigt at skelne mellem den længste opbevaringsperiode for elementet i forhold til den længste angivne periode i en opbevaringspolitik eller -mærkat. Og på samme måde mellem den korteste udløbsdato for elementet i forhold til den korteste angivne periode i en opbevaringspolitik.
> 
> Du kan få flere oplysninger i forklaringen efter grafikken i [afsnittet principper for opbevaring](retention.md#the-principles-of-retention-or-what-takes-precedence) .
