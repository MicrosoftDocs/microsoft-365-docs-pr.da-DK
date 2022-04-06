---
title: Microsoft Defender for Identity sensorens tilstand og indstillinger i Microsoft 365 Defender
description: Lær at konfigurere Microsoft Defender for Identity og overvåge deres tilstand i Microsoft 365 Defender
ms.date: 06/07/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: 246fd5ca880ca2d7e187283d06f19d071f5d7e0e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468517"
---
# <a name="microsoft-defender-for-identity-sensor-health-and-settings-in-microsoft-365-defender"></a>Microsoft Defender for Identity sensorens tilstand og indstillinger i Microsoft 365 Defender

**Gælder for:**

- Microsoft 365 Defender
- Defender for Identity

I denne artikel forklares det, hvordan du [konfigurerer og Microsoft Defender for Identity](/defender-for-identity) sensorerne [i Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Som en del af dine Microsoft 365 Defender har nogle indstillinger og detaljer ændret sig fra deres placering i Defender for Identity-portalen. Læs oplysningerne nedenfor for at finde ud af, hvor du kan finde både de velkendte og nye funktioner.

## <a name="view-defender-for-identity-sensor-settings-and-status"></a>Få vist indstillinger og status for Defender for Identity-sensor

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> skal du gå **til Indstillinger** og derefter **Identities**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Indstillingen identities on the Indstillinger page" lightbox="../../media/defender-identity/settings-identities.png":::

1. Vælg siden **Med sensorerne** , som viser alle dine Defender til identitetssensorer. For hver sensor kan du se dens navn, dets domænemedlemskab, versionsnummeret, hvis opdateringer skulle blive forsinket, tjenestestatus, opdateringsstatus, tilstandsstatus, antallet af tilstandsproblemer, og hvornår sensoren blev oprettet.

    [![Sensorside.](../../media/defender-identity/sensor-page.png)](../../media/defender-identity/sensor-page.png#lightbox)

    >[!NOTE]
    >I portalen Defender for Identity var sensorindstillingerne og tilstandsoplysningerne forskellige steder. Bemærk, Microsoft 365 Defender at de nu er på samme side.

1. Hvis du vælger **Filtre**, kan du vælge, hvilke filtre der skal være tilgængelige. Derefter kan du med hvert filter vælge, hvilke sensorer der skal vises.

    [![Sensorfiltre.](../../media/defender-identity/sensor-filters.png)](../../media/defender-identity/sensor-filters.png#lightbox)

    :::image type="content" source="../../media/defender-identity/filtered-sensor.png" alt-text="Den filtrerede sensor" lightbox="../../media/defender-identity/filtered-sensor.png":::

1. Hvis du vælger en af sensorerne, vises en rude med oplysninger om sensoren og dens tilstand.

    [![Sensoroplysninger.](../../media/defender-identity/sensor-details.png)](../../media/defender-identity/sensor-details.png#lightbox)

1. Hvis du vælger nogen af tilstandsproblemerne, får du en rude med flere oplysninger om dem. Hvis du vælger et lukket problem, kan du åbne det igen her.

   :::image type="content" source="../../media/defender-identity/issue-details.png" alt-text="Oplysninger om problemet" lightbox="../../media/defender-identity/issue-details.png":::
    

1. Hvis du vælger **Administrer sensor**, åbnes en rude, hvor du kan konfigurere sensoroplysningerne.

   :::image type="content" source="../../media/defender-identity/manage-sensor.png" alt-text="Indstillingen Administrer sensor" lightbox="../../media/defender-identity/manage-sensor.png":::

   :::image type="content" source="../../media/defender-identity/configure-sensor-details.png" alt-text="Den side, hvor du konfigurerer indstillinger for sensoren" lightbox="../../media/defender-identity/configure-sensor-details.png":::

1. På siden **Med** sensorerne kan du eksportere listen over sensorer til en .csv fil ved at vælge **Eksportér**.

   :::image type="content" source="../../media/defender-identity/export-sensors.png" alt-text="Listen Eksportér med sensorer" lightbox="../../media/defender-identity/export-sensors.png":::

## <a name="add-a-sensor"></a>Tilføj en sensor

Fra siden **Med** sensorer kan du tilføje en ny sensor.

1. Vælg **Tilføj sensor**.

   :::image type="content" source="../../media/defender-identity/add-sensor.png" alt-text="Indstillingen Tilføj sensor" lightbox="../../media/defender-identity/add-sensor.png":::

1. Der åbnes en rude med en knap til at downloade sensorinstallationsprogrammet og en genereret adgangsnøgle.

   :::image type="content" source="../../media/defender-identity/installer-access-key.png" alt-text="Mulighederne for at downloade installationsprogrammet og genoprette nøglen" lightbox="../../media/defender-identity/installer-access-key.png":::

1. Vælg **Download installationsprogram** for at gemme pakken lokalt. Zip-filen indeholder følgende filer:

    - Installationsprogrammet til Defender for Identity-sensoren

    - Konfigurationsindstillingsfilen med de nødvendige oplysninger til at oprette forbindelse til cloudtjenesten Defender for Identity

1. Kopiér **Access-nøglen**. Adgangsnøglen er påkrævet, for at Defender for Identity-sensoren kan oprette forbindelse til din forekomst af Defender for Identity. Adgangsnøglen er en engangsadgangskode til sensorinstallation, hvorefter al kommunikation udføres ved hjælp af certifikater til godkendelse og TLS-kryptering. Brug knappen **Genskab nøgle** , hvis du nogensinde får brug for at genskabe den nye adgangsnøgle. Det påvirker ikke eventuelle tidligere installerede sensorer, fordi de kun bruges til den indledende registrering af sensoren.

1. Kopiér pakken til den dedikerede server eller domænecontroller, som du installerer Defender for Identity-sensoren på.

## <a name="see-also"></a>Se også

- [Administrer sikkerhedsadvarsler for Defender for Identity](manage-security-alerts.md)
