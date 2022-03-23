---
title: Nær registrering af dubletter – eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Brug registrering af nær dubletter til at gruppere dokumenter, der ligner hinanden, når du analyserer sagsdata Advanced eDiscovery.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: cbd01bd38f45a397a82a8db3774997349f4eec88
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589553"
---
# <a name="near-duplicate-detection-in-advanced-ediscovery"></a>Registrering af dubletter i Advanced eDiscovery

Overvej at gennemse et sæt dokumenter, hvor et undersæt er baseret på den samme skabelon og primært har det samme standardsprog, med nogle få forskelle her og der. Hvis en korrekturlæser kunne identificere dette undersæt, gennemse et af dem grundigt og gennemse forskellene på resten, ville vedkommende ikke have overset nogen unikke oplysninger, mens det kun tog en brøkdel af tiden, der ville have taget dem at læse alle dokumenter for at dække. Nærregistrering af dubletter grupperer tekst, der ligner hinanden, for at hjælpe dig med at gøre gennemsynsprocessen mere effektiv.

## <a name="how-does-it-work"></a>Hvordan fungerer det?

Når registrering af nær dubletter køres, fortolker systemet hvert dokument med tekst. Derefter sammenlignes hvert dokument med hinanden for at afgøre, om deres lighed er større end den agrænsede grænse. Hvis det er, grupperes dokumenterne sammen. Når alle dokumenter er blevet sammenlignet og grupperet, markeres et dokument fra hver gruppe som "pivot"; Når du gennemgår dine dokumenter, kan du gennemgå en pivot først og gennemgå de andre dokumenter i det samme næsten duplikerede sæt og fokusere på forskellen mellem pivot og det dokument, der gennemgås.
