---
title: Microsoft Defender for Identity registreringsudelse i Microsoft 365 Defender
description: Lær, hvordan du konfigurerer Microsoft Defender for Identity registreringsudetagelser i Microsoft 365 Defender.
ms.date: 11/02/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: e2df92e44b323bd0555407d72ebd48a7e050c9a5
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473909"
---
# <a name="configure-defender-for-identity-detection-exclusions-in-microsoft-365-defender"></a>Konfigurer udeladelse af Defender til identitetsregistrering i Microsoft 365 Defender

**Gælder for:**

- Microsoft 365 Defender
- Defender for Identity

Denne artikel forklarer, hvordan [du konfigurerer Microsoft Defender for Identity](/defender-for-identity) registreringsudetagelser [i Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

> [!IMPORTANT]
> Som en del af dine Microsoft 365 Defender har nogle indstillinger og detaljer ændret sig fra deres placering i Defender for Identity-portalen. Læs oplysningerne nedenfor for at finde ud af, hvor du kan finde både de velkendte og nye funktioner.

[!INCLUDE [Product long](includes/product-long.md)] gør det muligt at udelade bestemte IP-adresser, computere, domæner eller brugere fra en række registreringer.

Eksempelvis kan en **DNS-rekognoseringsbesked** blive udløst af en sikkerhedsscanner, der bruger DNS som scanningsmekanisme. Hvis du opretter en udelukkelse, hjælper det Defender for Identity med at ignorere sådanne scannere og reducere falske positive.

>[!NOTE]
>Af de mest almindelige domæner med mistænkelig kommunikation [over DNS-beskeder](/defender-for-identity/exfiltration-alerts#suspicious-communication-over-dns-external-id-2031) , der er åbnet på dem, har vi observeret de domæner, som kunderne har udelukket mest fra beskeden. Disse domæner føjes som standard til udeladelseslisten, men du har mulighed for nemt at fjerne dem.

## <a name="how-to-add-detection-exclusions"></a>Sådan tilføjes udeladelse af registreringer

1. I [Microsoft 365 Defender](https://security.microsoft.com/) skal du gå **til Indstillinger** og derefter **Identities**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Indstillingen Identiteter i kolonnen Navn" lightbox="../../media/defender-identity/settings-identities.png":::

1. Du får derefter vist **ekskluderede** enheder i menuen til venstre.

   :::image type="content" source="../../media/defender-identity/excluded-entities.png" alt-text="Ruden Udeladte enheder" lightbox="../../media/defender-identity/excluded-entities.png":::

Du kan derefter angive udeladelsesmetoder ved hjælp af to metoder: **Udeladelse ved registrering af regel** **og globale udeladte enheder**.

## <a name="exclusions-by-detection-rule"></a>Udeladelse ved registreringsregel

1. I menuen til venstre skal du vælge **Udeladelse ved registreringsregel**. Du får vist en liste over registreringsregler.

   :::image type="content" source="../../media/defender-identity/exclusions-by-detection-rule.png" alt-text="Indstillingen Udelader ved registrering af regel i elementet Udeladte enheder i ruden til venstre" lightbox="../../media/defender-identity/exclusions-by-detection-rule.png":::

1. For hver registrering, du vil konfigurere, skal du gøre følgende:

    1. Vælg reglen. Du kan søge efter registreringer ved hjælp af søgelinjen. Når denne indstilling er markeret, åbnes en rude med oplysninger om registreringsreglen.

       :::image type="content" source="../../media/defender-identity/detection-rule-details.png" alt-text="Oplysninger om en registreringsregel" lightbox="../../media/defender-identity/detection-rule-details.png":::

    1. Hvis du vil tilføje en udeladelse, skal **du vælge knappen** Udeladte enheder og derefter vælge udeladelsestypen. Forskellige ekskluderede enheder er tilgængelige for hver regel. De omfatter brugere, enheder, domæner og IP-adresser. I dette eksempel er valgmulighederne **Ekskluder enheder og** **Udelad IP-adresser**.

       :::image type="content" source="../../media/defender-identity/exclude-devices-or-ip-addresses.png" alt-text="Muligheden for at udelade enheder eller IP-adresser" lightbox="../../media/defender-identity/exclude-devices-or-ip-addresses.png":::

    1. Når du har valgt udeladelsestypen, kan du tilføje udelukkelsen. I den rude, der åbnes, skal du vælge **+** knappen for at tilføje udeladelse.

       :::image type="content" source="../../media/defender-identity/add-exclusion.png" alt-text="Muligheden for at tilføje en udeladelse" lightbox="../../media/defender-identity/add-exclusion.png":::

    1. Tilføj derefter den enhed, der skal udelades. Vælg **+ Tilføj** for at føje enheden til listen.

       :::image type="content" source="../../media/defender-identity/add-excluded-entity.png" alt-text="Muligheden for at tilføje en enhed, der skal udelukkes" lightbox="../../media/defender-identity/add-excluded-entity.png":::

    1. Vælg derefter **Udelad IP-adresser** (i dette eksempel) for at fuldføre udeladelse.

       :::image type="content" source="../../media/defender-identity/exclude-ip-addresses.png" alt-text="Muligheden for at udelade IP-adresser" lightbox="../../media/defender-identity/exclude-ip-addresses.png":::

    1. Når du har tilføjet udeladelse, kan du eksportere listen eller fjerne udeladelserne ved at gå tilbage til knappen **Udeladte** enheder. I dette eksempel har vi returneret til **Udelad enheder**. Hvis du vil eksportere listen, skal du vælge pil ned-knappen.

       :::image type="content" source="../../media/defender-identity/return-to-exclude-devices.png" alt-text="Indstillingen Tilbage til udelad enheder" lightbox="../../media/defender-identity/return-to-exclude-devices.png":::

    1. Hvis du vil slette en udeladelse, skal du vælge udelukkelsen og vælge papirkurvsikonet.

       :::image type="content" source="../../media/defender-identity/delete-exclusion.png" alt-text="Indstillingen Slet en udeladelse" lightbox="../../media/defender-identity/delete-exclusion.png":::

## <a name="global-excluded-entities"></a>Globale udeladte enheder

Du kan nu også konfigurere udeladelse fra udeladelse fra **globale ekskluderede enheder**. Globale udeladelser gør det muligt at definere bestemte enheder (IP-adresser, undernet, enheder eller domæner), der skal udelukkes på tværs af alle de registreringer, som Defender for Identity har. Hvis du f.eks. udelader en enhed, gælder den kun for de registreringer, der har enheds-id som en del af registreringerne.

1. I menuen til venstre skal du vælge **Globale ekskluderede enheder**. Du får vist de kategorier af enheder, som du kan udelukke.

   :::image type="content" source="../../media/defender-identity/global-excluded-entities.png" alt-text="Undermenuelementet Globale udeladte enheder" lightbox="../../media/defender-identity/global-excluded-entities.png":::

1. Vælg en udeladelsestype. I dette eksempel har vi valgt **Udelad domæner**.

   :::image type="content" source="../../media/defender-identity/exclude-domains.png" alt-text="Fanen Domæner" lightbox="../../media/defender-identity/exclude-domains.png":::

1. Der åbnes en rude, hvor du kan tilføje et domæne, der skal udelades. Tilføj det domæne, du vil udelade.

   :::image type="content" source="../../media/defender-identity/add-excluded-domain.png" alt-text="Muligheden for at tilføje et domæne, der skal udelades" lightbox="../../media/defender-identity/add-excluded-domain.png":::

1. Domænet føjes til listen. Vælg **Udelad domæner for** at fuldføre udelukkelsen.

   :::image type="content" source="../../media/defender-identity/select-exclude-domains.png" alt-text="Muligheden for at vælge domæner, der skal udelades" lightbox="../../media/defender-identity/select-exclude-domains.png":::

1. Du får derefter vist domænet på listen over enheder, der skal udelukkes fra alle registreringsregler. Du kan eksportere listen eller fjerne enhederne ved at markere dem og klikke på **knappen** Fjern.

   :::image type="content" source="../../media/defender-identity/global-excluded-entries-list.png" alt-text="Listen over poster, der er udeladt globalt" lightbox="../../media/defender-identity/global-excluded-entries-list.png":::

## <a name="see-also"></a>Se også

- [Administrer sikkerhedsadvarsler for Defender for Identity](manage-security-alerts.md)
