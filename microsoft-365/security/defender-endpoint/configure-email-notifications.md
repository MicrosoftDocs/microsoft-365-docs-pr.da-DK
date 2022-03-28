---
title: Konfigurer beskeder i Microsoft Defender til Slutpunkt
description: Du kan bruge Microsoft Defender til slutpunkt til at konfigurere indstillinger for mailbeskeder for sikkerhedsadvarsler baseret på alvorsgrad og andre kriterier.
keywords: mailbeskeder, konfigurer beskeder, Microsoft Defender for Endpoint, Microsoft Defender til slutpunktsmeddelelser, Microsoft Defender for Endpoint-beskeder, windows enterprise, windows education
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
ms.openlocfilehash: f2e4cc2db64a01605a0003561ceda27409b16cf5
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63597528"
---
# <a name="configure-alert-notifications-in-microsoft-defender-for-endpoint"></a>Konfigurer beskeder i Microsoft Defender til Slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-emailconfig-abovefoldlink)

Du kan konfigurere Defender til Slutpunkt til at sende mailbeskeder til angivne modtagere for nye beskeder. Denne funktion gør det muligt at identificere en gruppe af personer, der straks vil blive informeret og kan reagere på beskeder baseret på deres alvorlighed.

> [!NOTE]
> Kun brugere med tilladelse til at administrere sikkerhedsindstillinger kan konfigurere mailbeskeder. Hvis du har valgt at bruge grundlæggende administration af tilladelser, kan brugere med sikkerhedsadministratorroller eller globale administratorroller konfigurere mailbeskeder.

Du kan angive de alvorsgradsniveauer for beskeder, der udløser meddelelser. Du kan også tilføje eller fjerne modtagere af mailmeddelelsen. Nye modtagere får besked om beskeder, der udløses, efter de er tilføjet. Du kan finde flere oplysninger om beskeder [i Få vist og organiser køen Vigtige beskeder](alerts-queue.md).

Hvis du bruger rollebaseret adgangskontrol, modtager modtagerne kun meddelelser baseret på de enhedsgrupper, der er konfigureret i meddelelsesreglen.
Brugere med de rette tilladelser kan kun oprette, redigere eller slette meddelelser, der er begrænset til deres administrationsområde for enheder.
Kun brugere, der er tildelt rollen Global administrator, kan administrere meddelelsesregler, der er konfigureret for alle enhedsgrupper.

Mailmeddelelsen indeholder grundlæggende oplysninger om advarslen og et link til portalen, hvor du kan undersøge yderligere.

## <a name="create-rules-for-alert-notifications"></a>Opret regler for beskeder om beskeder
Du kan oprette regler, der bestemmer enhedernes og alvorsgraderne for afsendelse af mailbeskeder og beskedmodtagerne.


1. I **navigationsruden** skal du **vælge Indstillinger** \> Generelle **mailmeddelelser** \> \> **for slutpunkter**.

2. Klik **på Tilføj element**.

3. Angiv generelle oplysninger:
    - **Regelnavn** – Angiv et navn til meddelelsesreglen.
    - **Medtag organisationsnavn** – Angiv det kundenavn, der vises i mailmeddelelsen.
    - **Linket Medtag lejerspecifik portal** – tilføjer et link til lejer-id'et for at tillade adgang til en bestemt lejer.
    - **Medtag enhedsoplysninger** – Medtager enhedsnavnet i mailens meddelelsestekst.

        > [!NOTE]
        > Disse oplysninger kan behandles af modtagermailservere, der ikke er på den geografiske placering, du har valgt for dine Defender til slutpunktsdata.

    - **Enheder** – Vælg, om du vil give modtagere besked om beskeder på alle enheder (kun global administratorrolle) eller på udvalgte enhedsgrupper. Få mere at vide under [Opret og administrer enhedsgrupper](machine-groups.md).
    - **Alvorsgrad for** besked – Vælg alvorsniveauet for beskeden.

4. Klik på **Næste**.

5. Angiv modtagerens mailadresse, og klik derefter på **Tilføj modtager**. Du kan tilføje flere mailadresser.

6. Kontrollér, at mailmodtagere kan modtage mailbeskeder ved at vælge **Send testmail**.

7. Klik **på Gem meddelelsesregel**.

## <a name="edit-a-notification-rule"></a>Rediger en meddelelsesregel

1. Vælg den meddelelsesregel, du vil redigere.

2. Opdater oplysningerne under fanen Generelt og Modtager.

3. Klik **på Gem meddelelsesregel**.

## <a name="delete-notification-rule"></a>Slet meddelelsesregel

1. Vælg den meddelelsesregel, du vil slette.

2. Klik **på Slet**.

## <a name="troubleshoot-email-notifications-for-alerts"></a>Fejlfinding af mailbeskeder for beskeder

I dette afsnit vises en liste over forskellige problemer, der kan opstå, når du bruger mailbeskeder til beskeder.

**Problem:** De tilsigtede modtagere rapporterer, at de ikke modtager meddelelserne.

**Løsning:** Sørg for, at meddelelserne ikke blokeres af mailfiltre:

1. Kontrollér, at meddelelser om Defender til Slutpunkt ikke sendes til mappen Uønsket mail. Markér dem som Ikke uønsket.
2. Kontrollér, at dit mailsikkerhedsprodukt ikke blokerer mailmeddelelser fra Defender til Slutpunkt.
3. Kontrollér dine regler for mailprogram, der kan fange og flytte dine Defender for Endpoint-mailmeddelelser.

## <a name="related-topics"></a>Relaterede emner

- [Opdater indstillinger for dataopbevaring](data-retention-settings.md)
- [Konfigurere avancerede funktioner](advanced-features.md)
- [Konfigurer meddelelser om sikkerhedsrisiko i Microsoft Defender til Slutpunkt](/microsoft-365/security/defender-endpoint/configure-vulnerability-email-notifications)
