---
title: Rutediagram til at bestemme, hvornår et element bevares eller slettes permanent
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
ms.openlocfilehash: b9c3b94dcb50499b6af72fd124da384f90d16da9
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63593991"
---
# <a name="flowchart-to-determine-when-an-item-will-be-retained-or-permanently-deleted"></a>Rutediagram til at bestemme, hvornår et element bevares eller slettes permanent

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Brug følgende rutediagram til at anvende principperne for [](retention.md#the-principles-of-retention-or-what-takes-precedence) opbevaring på et element for at afgøre, om systemet bevarer det eller sletter det permanent som et resultat af en opbevaringsmærkat eller opbevaringspolitik.

Dette logikflow bruges til et element, når en af følgende betingelser gælder:

- Der er anvendt mere end én opbevaringspolitik
- Der er et opbevaringsnavn og en eller flere opbevaringspolitikker

Når et element er underlagt et eDiscovery-sæt (eller de ældre teknologier fra Retslig tilbageholdelse eller In-Place Hold), bevares det altid før beslutningsforløb for opbevaringspolitikker og et opbevaringsnavn.

Hvis du ikke er bekendt med nogen af de udtryk, der bruges i dette rutediagram, kan du se [Få mere at vide om opbevaringspolitikker og opbevaringsnavne](retention.md).


   ![Rutediagram for at bestemme, hvornår et element bevares eller slettes permanent.](../media/retention-flowchart.svg)

> [!NOTE]
> Det er vigtigt at skelne mellem den længste opbevaringsperiode for elementet vs. den længste angivne periode i en opbevaringspolitik eller etiket. Og på samme måde mellem den korteste udløbsdato for elementet vs. den korteste angivne periode i en opbevaringspolitik.
> 
> Du kan finde flere oplysninger i forklaringen efter grafikken i [afsnittet om principper for](retention.md#the-principles-of-retention-or-what-takes-precedence) opbevaring.
