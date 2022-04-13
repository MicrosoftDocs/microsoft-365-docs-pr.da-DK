---
title: Integrer Microsoft OneDrive LTI med lærred
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Opret og begrader opgaver, byg og organiser kursusindhold, og samarbejd om filer i realtid med den nye Microsoft OneDrive Learning Tools Interoperability App for Canvas.
ms.openlocfilehash: 5de027c9d7606ebe546a8dc8e087b91da7f0400e
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824558"
---
# <a name="integrate-microsoft-onedrive-lti-with-canvas"></a>Integrer Microsoft OneDrive LTI med lærred

Integration af Microsoft OneDrive LTI med lærred er en proces med to trin. Det første trin aktiverer Microsoft OneDrive på lærredet, og det andet trin gør Microsoft OneDrive LTI tilgængelig i lærredskurser.

## <a name="recommended-browser-settings"></a>Anbefalede browserindstillinger

- Cookies skal være aktiveret for Microsoft OneDrive.
- Pop op-vinduet bør ikke blokeres for Microsoft OneDrive.

> [!NOTE]
>
> - Cookies er ikke aktiveret som standard i Chrome-browserens inkognitotilstand og skal aktiveres.
> - Microsoft OneDrive LTI fungerer i privat tilstand i Microsoft Edge browser. Sørg for, at du ikke har blokeret cookies (som er aktiveret som standard).

## <a name="enable-microsoft-onedrive-lti-in-canvas"></a>Aktivér Microsoft OneDrive LTI på lærredet

> [!IMPORTANT]
> Den person, der udfører denne integration, skal være administrator af lærredet og administrator af den Microsoft 365 lejer.

1. Log på <a href="https://onedrivelti.microsoft.com/admin" target="_blank">Microsoft OneDrive LTI-registreringsportalen</a>
2. Vælg knappen **Administratorsamtykke** , og acceptér tilladelserne.

   > [!CAUTION]
   > Hvis dette trin ikke udføres, giver følgende trin dig en fejl, og du kan ikke udføre dette trin i en time, når du har fået fejlen.

3. Vælg knappen **Opret ny LTI-lejer** . På siden LTI-registrering skal du vælge **Lærred** på rullelisten og angive den grundlæggende URL-adresse til din lærredsforekomst.

   > [!NOTE]
   > Hvis din lærredsforekomst f.eks `https://contoso.test.instructure.com`. er , skal den komplette URL-adresse angives.

   :::image type="content" source="media/OneDrive-LTI-07.png" alt-text="Administrationssiden for LTI-lejeren med et rullelistefelt til valg af LTI-forbrugerplatformen og et tekstfelt til URL-adressen.":::

4. Kopiér JSON ved at vælge knappen **Kopiér** (et ikon til højre, der viser to sider oven på hinanden). Dette bruges til at generere nøglen på lærredet.

   :::image type="content" source="media/OneDrive-LTI-08.png" alt-text="Et billede, der viser kopiknappen, som kopierer den viste JSON-tekst og gør den tilgængelig til oprettelse af nøgler på lærredet.":::

5. Log på din lærredsforekomst som administrator, og vælg **Udviklernøgler** i menuen til venstre på siden. Opret en udviklernøgle på rullelisten ved at vælge **LTI-nøgle** på rullelisten øverst til højre på siden.

   :::image type="content" source="media/OneDrive-LTI-14.png" alt-text="Et skærmbillede, der viser navigationslinjen til venstre, hvor Udviklernøgler er valgt, og LTI-nøgleposten er valgt på en rulleliste til højre på siden.":::

6. På siden Konfigurer på rullelisten **Metode** skal du vælge **Indsæt JSON** som metode og indsætte den JSON-tekst, du kopierede i trin 4, i det viste tekstfelt.

    > [!TIP]
    > **Valgfrit trin:** Hvis din skoles undervisere selv vil styre, hvilke links der vises i deres kursers navigation, kan du ændre ``default`` parameteren i den kopierede JSON. Parameteren ``default`` er indstillet til ``enabled`` automatisk, men hvis du ændrer ``default`` parameteren ``disabled`` , kan underviserne vælge navigation i deres egne kurser.
    >
    > Du kan få flere oplysninger om, hvordan undervisere kan ændre deres links til kursusnavigation, [under Hvordan gør jeg administrere links til kursusnavigation?](https://community.canvaslms.com/t5/Instructor-Guide/How-do-I-manage-Course-Navigation-links/ta-p/1020)

7. Gem nøglen, så bliver den tilgængelig i lærredet i tilstanden **Fra** . Slå nøglen **til** , og kopiér den nøgle, der er angivet i kolonnen **Detaljer** , som skal bruges i næste trin.

   :::image type="content" source="media/OneDrive-LTI-19.png" alt-text="Lærredssiden med nøglen angivet i en anden tilstand. Den skal aktiveres, og nøglen skal kopieres fra detaljekolonnen på denne side.":::

8. Vend tilbage til Microsoft OneDrive LTI-registreringsportalen, og indsæt nøglen i feltet **Lærredsklient-id**. Vælg **Næste** , når du er klar.

   :::image type="content" source="media/OneDrive-LTI-20.png" alt-text="LTI-lejerregistreringssiden, der viser JSON-teksten og tekstfeltet, som nøglen skal kopieres til.":::

9. Gennemse og gem dine ændringer. Der vises en meddelelse ved vellykket registrering.
10. Dine registreringsoplysninger kan også gennemses ved at vælge knappen **Vis LTI-lejere** på startsiden.

## <a name="enable-microsoft-onedrive-lti-in-canvas-courses"></a>Aktivér Microsoft OneDrive LTI i lærredskurser

En lærredsadministrator kan aktivere Microsoft OneDrive LTI for alle kurser. Hvis Microsoft OneDrive LTI er nødvendig i et bestemt kursus (og ikke alle kurser), skal kursuslæreren følge de samme trin i kursusindstillingerne.

1. Log på som administrator, og gå til afsnittet **Indstillinger**.
2. Gå til afsnittet **Apps** , og vælg knappen **Vis appkonfigurationer** .
3. Vælg knappen **Tilføj app** .
4. På rullelisten **Konfigurationstype** skal du vælge indstillingen **Efter klient-id** .
5. Indsæt værdien for den udviklernøgle, der tidligere er oprettet i feltet **Klient-id** , og vælg knappen **Send** .

:::image type="content" source="media/OneDrive-LTI-31.png" alt-text="Siden Tilføj app, der viser indstillingen Efter klient-id i rullemenuen Konfigurationstype.":::

## <a name="collaboration-settings-for-microsoft-onedrive-lti-in-canvas-courses"></a>Samarbejds-Indstillinger til Microsoft OneDrive LTI i lærredskurser

> [!NOTE]
> Hvis samarbejde skal fungere for undervisere og studerende, skal du ikke aktivere samarbejdsindstillingen. Følg nedenstående trin for at sikre, at indstillingen ikke er aktiveret.

1. Log på som administrator, og gå til afsnittet **Indstillinger**.
1. Gå til afsnittet **Funktionsindstillinger** , og gå derefter til afsnittet **Kursus** .
1. Angiv funktionen **Værktøj til eksternt samarbejde** , så den ikke er aktiveret.

> [!NOTE]
> Samarbejde kan tildeles til individuelle studerende og grupper af studerende. Tildeling til individuelle studerende fungerer som standard. Hvis du vil tildele samarbejde til en gruppe studerende, skal du følge disse trin:

1. Log på som administrator, og gå til afsnittet **Udviklernøgler** .
1. Find nøglen med værdien 170000000000710, og angiv den til **Til**.
