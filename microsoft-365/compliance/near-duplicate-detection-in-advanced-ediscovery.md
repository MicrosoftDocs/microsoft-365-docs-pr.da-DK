---
title: Nær registrering af dubletter i eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Brug nær registrering af dubletter til at gruppere tekstlignende dokumenter, når du analyserer sagsdata i eDiscovery (Premium).
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 985374558189b2001c6f11e09581f7cb3ed6d11b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622563"
---
# <a name="near-duplicate-detection-in-ediscovery-premium"></a>Nær registrering af dubletter i eDiscovery (Premium)

Overvej et sæt dokumenter, der skal gennemses, hvor et undersæt er baseret på den samme skabelon og for det meste har det samme standardsprog med nogle få forskelle her og der. Hvis en validator kunne identificere dette undersæt, gennemse et af dem grundigt og gennemse forskellene for resten, ville de ikke have overset nogen entydige oplysninger, samtidig med at de kun havde taget en brøkdel af tiden, der ville have taget dem til at læse alle dokumenter, der var dækket. I nærheden af registrering af dubletter grupperer tekstlignende dokumenter sammen for at hjælpe dig med at gøre din korrekturproces mere effektiv.

## <a name="how-does-it-work"></a>Hvordan fungerer det?

Når du er tæt på at registrere dubletter, fortolker systemet alle dokumenter med tekst. Derefter sammenlignes hvert dokument med hinanden for at afgøre, om deres lighed er større end den angivne grænse. Hvis det er, grupperes dokumenterne sammen. Når alle dokumenter er blevet sammenlignet og grupperet, markeres et dokument fra hver gruppe som "pivot". Når du gennemser dine dokumenter, kan du først gennemse en pivot og gennemse de andre dokumenter i det samme næsten duplikerede sæt med fokus på forskellen mellem pivot og det dokument, der gennemses.
