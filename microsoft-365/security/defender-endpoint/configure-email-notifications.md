---
title: Konfigurer beskeder i Microsoft Defender for Endpoint
description: Du kan bruge Microsoft Defender for Endpoint til at konfigurere indstillinger for mailbeskeder for sikkerhedsbeskeder baseret på alvorsgrad og andre kriterier.
keywords: mailmeddelelser, konfigurere beskeder, Microsoft Defender for Endpoint, Microsoft Defender for Endpoint meddelelser, Microsoft Defender for Endpoint beskeder, Windows Enterprise, Windows Education
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
ms.openlocfilehash: fde5ce238a44b6722770338378ae33c54a38a450
ms.sourcegitcommit: 60970cf8a2cb451011c423d797dfb77925394f89
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/19/2022
ms.locfileid: "65587484"
---
# <a name="configure-alert-notifications-in-microsoft-defender-for-endpoint"></a>Konfigurer beskeder i Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/mdb-overview.md)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-emailconfig-abovefoldlink)

Du kan konfigurere Defender for Endpoint til at sende mailmeddelelser til angivne modtagere for nye beskeder. Denne funktion giver dig mulighed for at identificere en gruppe personer, der straks informeres og kan reagere på beskeder baseret på deres alvorsgrad.

Hvis du bruger [Defender for Business](../defender-business/mdb-overview.md), kan du konfigurere mailmeddelelser for bestemte brugere (ikke roller eller grupper).

> [!NOTE]
> Det er kun brugere med tilladelserne 'Administrer sikkerhedsindstillinger', der kan konfigurere mailmeddelelser. Hvis du har valgt at bruge grundlæggende administration af tilladelser, kan brugere med rollerne Sikkerhedsadministrator eller Global administrator konfigurere mailmeddelelser.

Du kan angive niveauer for besked alvorsgrad, der udløser meddelelser. Du kan også tilføje eller fjerne modtagere af mailmeddelelsen. Nye modtagere får besked om beskeder, der udløses, når de er tilføjet. Du kan få flere oplysninger om beskeder under [Få vist og organiser køen Beskeder](alerts-queue.md).

Hvis du bruger rollebaseret adgangskontrol, modtager modtagerne kun meddelelser baseret på de enhedsgrupper, der er konfigureret i meddelelsesreglen. Brugere med den korrekte tilladelse kan kun oprette, redigere eller slette meddelelser, der er begrænset til deres område for administration af enhedsgruppe. Kun brugere, der er tildelt rollen Global administrator, kan administrere meddelelsesregler, der er konfigureret for alle enhedsgrupper.

Mailmeddelelsen indeholder grundlæggende oplysninger om beskeden og et link til portalen, hvor du kan foretage yderligere undersøgelser.

## <a name="create-rules-for-alert-notifications"></a>Opret regler for beskedbeskeder
Du kan oprette regler, der bestemmer, hvilke enheder og beskeder der skal sendes mailmeddelelser til, og modtagerne af meddelelserne.

1. Vælg **Indstillinger** \> **Slutpunkter** \> **Generelle** \> **mailmeddelelser** i navigationsruden.

2. Klik på **Tilføj element**.

3. Angiv generelle oplysninger:
    - **Regelnavn** – Angiv et navn til meddelelsesreglen.
    - **Medtag organisationsnavn** – Angiv det kundenavn, der vises i mailmeddelelsen.
    - **Medtag lejerspecifikt portallink** – tilføjer et link med lejer-id'et for at give adgang til en bestemt lejer.
    - **Medtag enhedsoplysninger** – Indeholder enhedsnavnet i brødteksten i mailbeskeden.

        > [!NOTE]
        > Disse oplysninger kan blive behandlet af modtagermailservere, der ikke findes på den geografiske placering, du har valgt til dine Defender for Endpoint-data.

    - **Enheder** – Vælg, om modtagerne skal have besked om beskeder på alle enheder (kun Global administrator rolle) eller på udvalgte enhedsgrupper. Du kan få flere oplysninger under [Opret og administrer enhedsgrupper](machine-groups.md). (Hvis du bruger [Defender for Business](../defender-business/mdb-overview.md), gælder enhedsgrupper ikke).
    - **Alvorsgrad af besked** – vælg niveauet for besked alvorsgrad.

4. Klik på **Næste**.

5. Angiv modtagerens mailadresse, og klik derefter på **Tilføj modtager**. Du kan tilføje flere mailadresser.

6. Kontrollér, at mailmodtagerne kan modtage mailmeddelelserne ved at vælge **Send testmail**.

7. Klik på **Gem meddelelsesregel**.

## <a name="edit-a-notification-rule"></a>Rediger en meddelelsesregel

1. Vælg den meddelelsesregel, du vil redigere.

2. Opdater oplysningerne under fanen Generelt og Modtager.

3. Klik på **Gem meddelelsesregel**.

## <a name="delete-notification-rule"></a>Slet meddelelsesregel

1. Vælg den meddelelsesregel, du vil slette.

2. Klik på **Slet**.

## <a name="troubleshoot-email-notifications-for-alerts"></a>Foretag fejlfinding af mailmeddelelser for beskeder

I dette afsnit kan du se en liste over forskellige problemer, du kan støde på, når du bruger mailmeddelelser til beskeder.

**Problem:** De ønskede modtagere rapporterer, at de ikke modtager meddelelserne.

**Løsning:** Sørg for, at meddelelserne ikke blokeres af mailfiltre:

1. Kontrollér, at mailmeddelelserne med Defender for Endpoint ikke sendes til mappen Uønsket mail. Markér dem som Ikke uønsket.
2. Kontrollér, at dit mailsikkerhedsprodukt ikke blokerer mailmeddelelserne fra Defender for Endpoint.
3. Kontrollér reglerne for dit mailprogram, der kan fange og flytte dine mails med Defender for Endpoint.

## <a name="related-topics"></a>Relaterede emner

- [Opdater indstillinger for dataopbevaring](data-retention-settings.md)
- [Konfigurer avancerede funktioner](advanced-features.md)
- [Konfigurer mailmeddelelser om sikkerhedsrisiko i Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/configure-vulnerability-email-notifications)
