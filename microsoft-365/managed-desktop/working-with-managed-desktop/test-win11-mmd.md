---
title: Forhåndsvisning og test Windows 11 med Microsoft Managed Desktop
description: Sådan får du Windows 11 i dit miljø
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: 3e840a0af2313702686398fdef0e158bad0b74b8
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63598026"
---
# <a name="preview-and-test-windows-11-with-microsoft-managed-desktop"></a>Forhåndsvisning og test Windows 11 med Microsoft Managed Desktop

Denne artikel forklarer, hvordan du tilmelder dig og deltager i Windows 11-kompatibilitetstesteprogrammet i dit Microsoft Managed Desktop-miljø. Du kan finde flere generelle oplysninger Windows 11 og Microsoft Managed Desktop [under Windows 11 og Microsoft Managed Desktop](../intro/win11-overview.md).  

## <a name="add-devices-to-the-windows-11-test-group"></a>Føj enheder til Windows 11-testgruppen

Vi har oprettet gruppen af enheder (Moderne arbejdsplads **– Windows 11 foreløbige testenheder**) til test og evaluering Windows 11. På trods af "foreløbige" i navnet modtager enheder i denne gruppe Windows 11 generelt tilgængelige builds, og konfigurationer af grundlinjekonfigurationer for Microsoft Managed Desktop, efterhånden som de bliver tilgængelige. De overvåges for at sikre pålidelighedsproblemer.

Du kan bruge nye enheder eller alle eksisterende enheder til Windows 11 test. Du bør dog ikke tilmelde produktionsenheder i denne gruppe, før du er sikker på testenheders kompatibilitet og samlede oplevelse.

## <a name="prioritize-applications-to-submit-to-the-test-base"></a>Prioriter programmer, der skal sendes til Testbase

Forretningskritiske programmer er de bedste kandidater til mere validering i et lukket Windows 11-miljø. Vi kan hjælpe dig med at beslutte apps til Windows 11-test baseret på data om brug og pålidelighed. Følg disse trin for at anmode om vores anbefalinger:

1. Åbn en ny supportanmodning med Microsoft Managed Desktop Service Engineering-teamet. Hvis du har brug for flere oplysninger om, hvordan du arkiverer anmodningen, skal du [se Administratorsupport](admin-support.md).
2. Brug disse værdier til felterne:
    - Titel: Windows 11 Test Base-kandidater
    - Anmodningstype: Anmodning om oplysninger
    - Kategori: Apps
    - Underkategori: Andet

## <a name="report-issues"></a>Rapportér problemer

Hvis du finder Windows 11-kompatibilitetsproblemer med dine line of business- eller Microsoft 365-apps, skal du rapportere dem til os med henblik på undersøgelse og afhjælpning. Hvis du vil rapportere et problem, skal du følge disse trin:

1. Åbn en ny supportanmodning med Microsoft Managed Desktop Service Engineering-teamet.
2. Brug disse værdier til felterne:
    - Titel: Windows 11-kompatibilitetstest
    - Anmodningstype: Hændelse
    - Kategori: Enheder
    - Underkategori: Windows opgradering/opdatering

3. Beskriv adfærden, og hvor alvorligt det vil forhindre din virksomhed i et produktionsmiljø.

Microsoft Managed Desktop-triages og håndterer Windows 11 problemer, der er baseret på effekten på produktiviteten. Når anmodningen åbnes, kommunikerer vi med kundeadministratorer for at sikre, at problemer, der blokerer brugerproduktivitet, løses, før du starter bredere Windows 11 migrering inden for en given lejer.
