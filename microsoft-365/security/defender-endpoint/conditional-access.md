---
title: Aktivér betinget adgang for bedre at beskytte brugere, enheder og data
description: Aktivér Betinget adgang for at forhindre programmer i at køre, hvis en enhed betragtes som værende i fare, og et program vurderes at være ikke-kompatibelt.
keywords: betinget adgang, bloker programmer, sikkerhedsniveau, intune,
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
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8ee1b1542eb2e737da509ce12ad9c2a605a4ffa5
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/25/2021
ms.locfileid: "63591836"
---
# <a name="enable-conditional-access-to-better-protect-users-devices-and-data"></a>Aktivér betinget adgang for bedre at beskytte brugere, enheder og data

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-conditionalaccess-abovefoldlink)

Betinget adgang er en funktion, der hjælper dig med bedre at beskytte dine brugere og virksomhedsoplysninger ved at sikre, at kun sikre enheder har adgang til programmer.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4byD1]

Med Betinget adgang kan du styre adgangen til virksomhedsoplysninger baseret på en enheds risikoniveau. Dette hjælper med at bevare pålidelige brugere på enheder, der er tillid til, ved hjælp af pålidelige programmer.

Du kan definere sikkerhedsbetingelser for, hvilke enheder og programmer der kan køre og få adgang til oplysninger fra dit netværk, ved at gennemtvinge politikker for at stoppe programmer i at køre, indtil en enhed vender tilbage til en kompatibel tilstand.

Implementeringen af Betinget adgang i Defender til Slutpunkt er baseret på politikker for overholdelse af Microsoft Intune (Intune) og politikker for Azure Active Directory (Azure AD).

Overholdelsespolitikken bruges sammen med Betinget adgang til kun at tillade enheder, der opfylder en eller flere regler for overholdelse af regler for enhedsoverholdelse, at få adgang til programmer.

## <a name="understand-the-conditional-access-flow"></a>Forstå flowet Betinget adgang

Betinget adgang sættes på plads, så når en trussel ses på en enhed, blokeres adgangen til følsomt indhold, indtil truslerne afhjælpes.

Flowet begynder med enheder, der ser ud til at have en lav, mellem eller høj risiko. Disse risiko determinationer sendes derefter til Intune.

Afhængigt af hvordan du konfigurerer politikker i Intune, kan Betinget adgang konfigureres således, at når visse betingelser er opfyldt, anvendes politikken.

Du kan f.eks. konfigurere Intune til at anvende Betinget adgang på enheder med høj risiko.

I Intune bruges en politik for enhedsoverholdelse sammen med betinget adgang til Azure AD til at blokere adgangen til programmer. Sideløbende startes en automatisk undersøgelses- og afhjælpningsproces.

 En bruger kan stadig bruge enheden, mens den automatiske undersøgelse og afhjælpning finder sted, men adgangen til virksomhedsdata blokeres, indtil truslerne er fuldt løst.

For at løse den risiko, der findes på en enhed, skal du returnere enheden til en kompatibel tilstand. En enhed vender tilbage til en kompatibel tilstand, når der ikke er nogen risiko ved den.

Der er tre måder at håndtere en risiko på:

1. Brug Manuel eller automatisk afhjælpning.
2. Løs aktive beskeder på enheden. Dette vil fjerne risikoen fra enheden.
3. Du kan fjerne enheden fra de aktive politikker og derfor anvendes Betinget adgang ikke på enheden.

Manuel afhjælpning kræver, at administratoren af en kopi undersøger en besked og adresserer den risiko, der kan ses på enheden. Den automatiserede afhjælpning konfigureres via konfigurationsindstillinger, der er angivet i følgende afsnit, [Konfigurer betinget adgang](configure-conditional-access.md).

Når risikoen fjernes enten via manuel eller automatisk afhjælpning, vender enheden tilbage til en kompatibel tilstand, og der gives adgang til programmer.

I følgende eksempelsekvens af hændelser forklares Betinget adgang i aktion:

1. En bruger åbner en skadelig fil, og Defender for Endpoint markerer enheden som høj risiko.
2. Den høje risikovurdering sendes videre til Intune. Sideløbende igangsættes en automatisk undersøgelse for at afhjælpe den identificerede trussel. En manuel afhjælpning kan også udføres for at afhjælpe den identificerede trussel.
3. Baseret på den politik, der er oprettet i Intune, er enheden markeret som ikke kompatibel. Vurderingen videregives derefter til Azure AD af politikken For betinget adgang i Intune. I Azure AD anvendes den tilsvarende politik til at blokere adgang til programmer.
4. Den manuelle eller automatiserede undersøgelse og afhjælpning er fuldført, og truslerne fjernes. Defender for Endpoint ser, at der ikke er nogen risiko på enheden, og Intune vurderer, at enheden er i en kompatibel tilstand. Azure AD anvender den politik, der tillader adgang til programmer.
5. Brugere kan nu få adgang til programmer.

## <a name="related-topic"></a>Relateret emne

- [Konfigurer Betinget adgang i Microsoft Defender til slutpunkt](configure-conditional-access.md)
