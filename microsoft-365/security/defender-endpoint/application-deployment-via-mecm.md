---
title: Overførsel af servere fra Microsoft Monitoring Agent til den samlede løsning
description: Få mere at vide om, hvordan du overfører servere på et tidligere niveau fra Microsoft Monitoring Agent til den nye samlede løsning trinvist fra denne artikel.
keywords: overfør server, server, 2012r2, 2016, onboarding af serveroverførsel Microsoft Defender for Endpoint servere, MECM, Microsoft Monitoring Agent, MMA, server i lavere niveau, samlet løsning, UA
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: alekyaj
ms.author: macapara
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: fef1a5a7b8e47c4f97d36d4002ccf00401948d12
ms.sourcegitcommit: 2aa5c026cc06ed39a9c1c2bcabd1f563bf5a1859
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/09/2022
ms.locfileid: "66696321"
---
# <a name="migrating-servers-from-microsoft-monitoring-agent-to-the-unified-solution"></a>Overførsel af servere fra Microsoft Monitoring Agent til den samlede løsning

**Gælder for:**

- Windows Server 2012 R2
- Windows Server 2016

I denne artikel kan du se, hvordan du overfører servere på et nede niveau fra Microsoft Monitoring Agent (MMA) til den samlede løsning.

## <a name="prerequisites"></a>Forudsætninger

- Microsoft Endpoint Configuration Manager (MECM) ældre end 2207.
- Operativsystemenheder på et niveau ned i dit miljø, der er onboardet med Microsoft Monitoring Agent. Bekræft, at kører i Jobliste, for at `MsSenseS.exe` bekræfte det.
- Tilstedeværelse af MMA-agenten. Du kan bekræfte det ved at kontrollere, om det korrekte arbejdsområde-id findes i Kontrolpanel> Microsoft-overvågningsagent.
- Aktiv Microsoft 365 Defender portal med enheder onboardet.
- En enhedsgruppe, der indeholder servere på et niveau, f.eks. Windows Server 2012 R2 eller Windows Server 2016 ved hjælp af MMA-agent, konfigureres i din MECM-forekomst.

Du kan få flere oplysninger om installation af de angivne forudsætninger i afsnittet [relaterede emner](#related-topics) .

## <a name="gather-required-files"></a>Indsaml påkrævede filer

Kopiér den samlede løsningspakke, onboardingscriptet og overførselsscriptet til den samme indholdskilde, som du installerer andre apps med MECM.

1. Download Onboarding Script og den samlede løsning fra [siden med indstillinger for Microsoft 365 Defender](https://sip.security.microsoft.com/preferences2/onboarding).
      :::image type="content" source="images/onboarding-script.png" alt-text="Skærmbillede af onboardingscript og download af samlet løsning." lightbox="images/onboarding-script.png":::
2. Download overførselsscriptet fra dokumentet: [Serveroverførselsscenarier fra den forrige MMA-baserede Microsoft Defender for Endpoint løsning](server-migration.md). Dette script findes også på GitHub: [GitHub – microsoft/mdefordownlevelserver](https://github.com/microsoft/mdefordownlevelserver).
3. Gem alle tre filer i en delt mappe, der bruges af MECM som softwarekilde.
     :::image type="content" source="images/ua-migration.png" alt-text="Skærmbillede af lagring af den delte mappe af MECM.":::

## <a name="create-the-package-as-an-application"></a>Opret pakken som et program

1. I MECM-konsollen skal du følge disse trin: **Softwarebibliotek>Programmer>Opret program**.
2. Vælg **Angiv programoplysningerne manuelt**.
      :::image type="content" source="images/manual-application-information.png" alt-text="Skærmbillede af manuel angivelse af valg af programoplysninger." lightbox="images/manual-application-information.png":::
3. Klik på **Næste** på skærmen Softwarecenter i guiden.
4. Klik på **Tilføj** i installationstyperne.
5. Vælg **Manuelt for at angive oplysninger om installationstypen** , og klik på **Næste**.
6. Giv scriptinstallationen et navn, og klik på **Næste**.
     :::image type="content" source="images/manual-deployment-information.png" alt-text="Skærmbillede, der angiver oplysninger om scriptinstallation.":::
7. På dette trin skal du kopiere den UNC-sti, som dit indhold er placeret i. Eksempel: `\\Cm1\h$\SOFTWARE_SOURCE\UAmigrate`.
     :::image type="content" source="images/deployment-type-wizard.png" alt-text="Skærmbillede, der viser kopi af UNC-sti.":::
8. Derudover skal du angive følgende som installationsprogrammet:

     ```powershell
       Powershell.exe -ExecutionPolicy ByPass -File install.ps1 -Log -Etl -RemoveMMA 48594f03-7e66-4e15-8b60-d9da2f92d564 -OnboardingScript .\WindowsDefenderATP.onboarding
     ```

9. Klik på **Næste** , og klik på Tilføj en delsætning.
10. Delsætningen kigger i registreringsdatabasen for at se, om følgende nøgle findes:  `HKEY_LOCAL_MACHINESOFTWARE\Classes\Installer\Products\63FAD065BFFD18F1926692665F704C6D`

     Angiv følgende input:
     - Værdi: **ProductName**
     - Datatype: **Streng**
     - Markér indstillingen: **Denne indstilling i registreringsdatabasen skal afsluttes på destinationssystemet for at angive, at programmet er til stede.**

     :::image type="content" source="images/detection-rule-wizard.png" alt-text="Skærmbillede, der viser registrering af registrering af registreringsdatabasenøgler.":::

     >[!TIP]
     >Denne registreringsdatabasenøgleværdi blev hentet ved at køre følgende PowerShell-kommando på en enhed, hvor unified-løsningen er installeret. Andre kreative metoder til detektion kan også bruges. Målet er at identificere, om den samlede løsning allerede er installeret på en bestemt enhed.

     ```powershell
     PowerShell Cmd:  get-wmiobject Win32_Product | Sort-Object -Property Name |Format-Table IdentifyingNumber, Name, LocalPackage -AutoSize
     ```

11. I afsnittet **Brugeroplevelse** kan du vælge, hvad der passer til dit miljø, og klikke på **Næste**. Hvis du vil have **vist installationsprogrammet**, anbefales det at installere med **Normal synlighed** under fasetest og derefter ændre det til **Minimeret** for generel udrulning.
     >[!TIP]
     > Den maksimalt tilladte kørselstid kan sænkes fra (standard) 120 minutter til 30 minutter.

     :::image type="content" source="images/user-experience-in-deployment-type-wizard.png" alt-text="Skærmbillede, der viser brugeroplevelsen i guiden installationstype.":::

12. Klik på **Næste** på Krav.
13. Klik på **Næste** på afhængigheder.
14. Klik på **Næste** , indtil afslutningsskærmen vises, og klik derefter på **Luk**.
15. Fortsæt med at klikke på Næste, indtil guiden Program er fuldført. Kontrollér, at alle er blevet grøn kontrolleret.
16. Luk guiden, højreklik på det senest oprettede program, og installer det i din serversamling på et tidligere niveau.
     :::image type="content" source="images/deploy-application.png" alt-text="Skærmbillede, der viser udrulningen af det oprettede program." lightbox="images/deploy-application.png":::
17. Bekræft status for denne migrering i MECM>Overvågning>udrulninger.

      :::image type="content" source="images/deployment-status.png" alt-text="Skærmbillede, der viser statuskontrol af udrulning." lightbox="images/deployment-status.png":::

## <a name="related-topics"></a>Relaterede emner

- [Konfiguration af Microsoft-overvågningsagent](/services-hub/health/mma-setup)
- [Installér programmer – Configuration Manager](/mem/configmgr/apps/deploy-use/deploy-applications)
- [Microsoft Defender for Endpoint - Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection)
- [Onboarde Windows-servere til Microsoft Defender for Endpoint-tjenesten](configure-server-endpoints.md)
- [Microsoft Defender for Endpoint: Forsvar af Windows Server 2012 R2 og 2016](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/defending-windows-server-2012-r2-and-2016/ba-p/2783292)
