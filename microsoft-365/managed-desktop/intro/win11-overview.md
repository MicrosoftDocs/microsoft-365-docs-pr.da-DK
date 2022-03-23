---
title: Microsoft-administreret skrivebord og Windows 11
description: Hvordan og hvornår Windows 11 er tilgængelig i tjenesten
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: 494f147dad24b8c668fcb8adfc9b8a845a5fbe8f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592296"
---
# <a name="microsoft-managed-desktop-and-windows-11"></a>Microsoft-administreret skrivebord og Windows 11

Efter annonceringen af Windows 11 er du måske begyndt at planlægge Windows 11-migrering som et led i dine bestræbelser på at holde Windows 10-enheder opdateret.

I denne artikel beskrives vigtige overvejelser, og hvordan Microsoft Managed Desktop understøtter jævne overgange i dine miljøer. Du kan finde oplysninger Windows 11 selv i [Windows 11 oversigt](/windows/whats-new/windows-11).

Hvis du vil have specifikke trin til at få Windows 11 installeret på dine Microsoft-administrerede skrivebordsenheder, skal du se forhåndsvisning og [test Windows 11 med Microsoft Managed Desktop](../working-with-managed-desktop/test-win11-mmd.md).

## <a name="timeline-for-windows-10-and-windows-11"></a>Tidslinje for Windows 10 og Windows 11

Windows 11 blev alment tilgængelig d. 4. oktober 2021. Det er klar til implementering af forbrugere og virksomheder, og det er en fuldt understøttet platform.

Vi begynder planlægning af installationer for alle Microsoft-administrerede skrivebordsenheder fra januar 2023. Vi yder dog fuld support til dem, der ønsker at installere Windows 11 tidligere. Vi vil rådføre os med og rådgive administratorer om at udvikle og implementere overførselsplaner for hver lejer ud fra tekniske parathed og forretningsmæssige overvejelser.

Microsoft Managed Desktop fortsætter med at understøtte Windows 10, indtil den når ophør af virksomhedssupport. Se [Windows 10 om livscyklusoplysninger](/windows/release-health/release-information).

## <a name="assessing-pre-release-versions-of-windows-11"></a>Vurdering af foreløbige versioner af Windows 11

Mere end 95 % af Microsofts administrerede skrivebordsenheder er berettiget til Windows 11. Det kan være en ide at prøve opgraderingen på testenheder før produktionsinstallationen. Du kan finde flere Windows 11-systemkrav under [Windows 11 systemkrav](/windows/whats-new/windows-11-requirements).

For Microsoft-administrerede skrivebordsenheder kan [du føje enheder til Windows 11-testenhed](/microsoft-365/managed-desktop/working-with-managed-desktop/test-win11-mmd?view=o365-worldwide#add-devices-to-the-windows-11-test-group). Denne gruppe modtager buildet Windows 11 generel tilgængelighed sammen med en microsoft-administreret grundlinjekonfiguration på skrivebordet. Når den er føjet til gruppen enhed, kan du bruge én til to dage på en enhed til at tage de nye indstillinger og blive tilbudt Windows 11.

For enheder, der ikke administreres af Microsoft Managed Desktop, kan du læse Endpoint Manager [for](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/endpoint-manager-simplifies-upgrades-to-windows-11/ba-p/2771886) at få mere at vide om installation Windows 11. Hvis du har enheder, der Windows 11 eller nyere og tilmelder dem i Microsoft Managed Desktop, vil de ikke vende tilbage til Windows 10.

## <a name="support-for-pre-release-windows-11-devices"></a>Understøttelse af foreløbige Windows 11 enheder

For dem, der har tilmeldt Windows 11-test før generel tilgængelighed, har enhederne muligvis forhåndsvisnings builds installeret.

Microsoft-administrerede skrivebordsenheder i denne tilstand vil ikke blive tilbudt den Windows 11 generelle tilgængeligheds build. Enhederne understøttes dog stadig til at løse de problemer, der opstår. Microsoft Managed Desktop overvåger alle administrerede enheder for sikkerhedstrusler og besvarer eventuelle beskeder, uanset om enheden kører et Windows 11-eksempel build.

Da vi er forpligtet til at hjælpe dig med at overflytte til Windows 11, mens du er produktiv, opfordrer vi dig til at rapportere fejl, du støder på med platformen. Vi prioriterer:

- Fejl, der blokerer brugerproduktiviteten ved bred udrulning Windows 11.
- Det betyder, at det blokerer brugerproduktiviteten Windows 10 enheder.

## <a name="testing-application-compatibility"></a>Test af programkompatibilitet

Programkompatibilitet er en af de mest almindelige overvejelser i enhver platformoverførsel på grund af risikoen for produktivitetsafbrydelser. Vi bruger flere proaktive og reaktive foranstaltninger for at hjælpe dig med at være sikker på problemfri appovergange til Windows 11.

### <a name="proactive-measures"></a>Proaktive målinger

Følgende er nogle proaktive målinger:

| Proaktive målinger | Beskrivelse |
| ----- | ----- |
| Almindelige apps | Microsoft tester i stor udstrækning de mest almindelige virksomhedsprogrammer og -pakker, der er installeret Windows 11 builds. Vi arbejder sammen med eksterne softwareudgivere og interne produktteams for at løse eventuelle problemer, der opdages under testen. Du kan finde flere oplysninger om vores proaktive indsats for kompatibilitetstest i [bloggen Programkompatibilitet](https://blogs.windows.com/windowsexperience/2019/01/15/application-compatibility-in-the-windows-ecosystem/).
| Line of business-apps | [Testbase](https://www.microsoft.com/en-us/testbase) er en ressource, som appudgivere og it-administratorer kan bruge til at sende apps og testtilfælde, så Microsoft kan køre på en virtuel maskine, der kører Windows 11-builds i et sikkert Azure-miljø.<br><br>Resultater, testindsigt og regressionsanalyse for hver testudførelse er tilgængelige for dig på en privat Azure-portal. Microsoft Managed Desktop hjælper dig med at prioritere dine line of business-apps til validering baseret på data om appanvendelse og pålidelighed. Du kan finde flere oplysninger om Test Base [i Test Base for at Microsoft 365](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/test-base-for-microsoft-365-microsoft-ignite-2021-updates/ba-p/2185566). |

### <a name="reactive-measures"></a>Reactive measures

Hvis du støder på problemer med appkompatibilitet i test- eller produktionsmiljøer, kan du få support uden omkostninger ved at åbne en [supportanmodning](/microsoft-365/managed-desktop/working-with-managed-desktop/test-win11-mmd?view=o365-worldwide#report-issues).

For Windows 11 omfatter support alle funktioner med følgende apps, der kører med de nyeste builds til operativsystemet:

- Office
- Microsoft Edge
- Teams
- line of business-programmer

Microsoft App Assure involverer app-udgivere direkte i at prioritere og løse problemer med appkompatibilitet, når det er nødvendigt.
