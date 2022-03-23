---
title: Arbejde med Microsoft Consulting Services
description: Forberedelse og trin til at følge for at arbejde med MCS for at pakke dine apps
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 5dd6bf62625d6b22a0585645abbeb24dabd6c9fd
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/10/2022
ms.locfileid: "63589097"
---
# <a name="working-with-microsoft-consulting-services"></a>Arbejde med Microsoft Consulting Services

Du kan interagere med Microsoft Consulting Services (MCS) for at pakke dine apps til brug med Microsoft Managed Desktop. Du kan få mere at vide ved at samarbejde med din kunderepræsentant om at kontakte MCS for at gennemgå dit specifikke projekt med appemballage.

## <a name="roles-and-responsibilities"></a>Roller og ansvarsområder

| Rolle | Ansvar |
| ------ | ------ |
| Du | Hvis du vil arbejde med MCS-appemballage **, skal du angive følgende elementer**: <ul><li> Installationsfilerne til kildefilen (f.eks. setup.exe eller .msi).</li><li>Installationsvejledningen, der angiver detaljer om, hvordan den endelige installation skal se ud. Skal der f.eks være en skrivebordsgenvej til appen? Hvad skal appens synlighed være? Skal appen oprette forbindelse til en server, og i så tilfælde hvilken? Du kan finde flere oplysninger i [skabelonen til anmodning om programemballage](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/app-packaging-template.docx).</li><li>Du skal udføre din egen test af accept for at bekræfte, at appen fungerer som forventet i dit miljø.</li><ul> |
| Microsoft Consulting Services (MCS) | **MCS udføre følgende handlinger:** <ul><li>Kontrollér, om appen er forbudt eller begrænset i Microsoft Managed Desktop-miljøet.</li><li>Test installation, start og fjernelse af appen for at sikre kompatibilitet med Windows 10. Hvis MCS opdager et kompatibilitetsproblem, afleverer de appen til [App Assure-programmet](/fasttrack/products-and-capabilities#app-assure) for at afhjælpe problemet.</li><li>Pak appen til dine specifikationer, og test installation af appen ved hjælp af Microsoft Intune.</li><ul>

## <a name="app-delivery-schedule"></a>Tidsplan for applevering

Start pakkeprocessen ved at uploade appoplysningerne til portalen for Microsoft Managed Desktop. Pakketeamet gennemser nye indsendelser hver torsdag. Efter gennemsyn og pakning leveres de pakkede apps den efterfølgende fredag. Du kan pakke op til fem apps pr. uge til start, men tjenesten kan skaleres, så den opfylder dine behov.

![kalender, der viser appindløb en torsdag (den 21. i dette eksempel), medievalidering den næste dag, pakke den følgende mandag (den 25. mandag) og applevering på den efterfølgende fredag (den 29. ).](../../media/MCS-cal.png)

Du får besked, når appen er blevet leveret. På det tidspunkt har du 21 dage til at udføre test af accept og godkende arbejdet i Microsoft Managed Desktop-portalen. Hvis du opdager et problem med appen under din test af accept, skal du afvise appen i Microsoft Managed Desktop-portalen. Du får forbindelse via mail med en Microsoft Consulting Services(MCS)-pakker for at forstå og løse problemet.

## <a name="testing-accounts-and-environment"></a>Test af konti og miljø

For at pakketeamet kan fuldføre overførslen til Microsoft Intune, anbefaler vi, at du giver bestemte tilladelser:

- Adgang til Microsoft Intune appinstallationsfunktioner, som pakkeren kan bruge til at tilføje og tildele appen.
- Testgrupper, brugerkonti og licenser til pakkerne for at kunne teste appsene.

MCS bruger disse tilladelser til at udføre følgende handlinger:

- Sørg for, at appen fungerer på virtuel maskine, der er konfigureret til Microsoft Managed Desktop.
- Upload appen til Microsoft Intune til installation for dine brugere.

Uden disse tilladelser er det muligt for MCS at gå fremad, men de vil ikke kunne overføre programmerne til dit miljø.
