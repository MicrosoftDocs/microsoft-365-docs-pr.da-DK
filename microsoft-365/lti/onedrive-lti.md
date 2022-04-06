---
title: Brug Microsoft OneDrive Learning interoperabilitetsværktøjer
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
description: Opret opgaver og karakterer, opbyg og lav kursusindhold, og samarbejd om filer i realtid med den nye Microsoft OneDrive Learning interoperabilitetsappen (INTEROPERABILITET).
ms.openlocfilehash: 68622305e6a277b44538d4a05ee42a6b680749f3
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63606610"
---
# <a name="integrate-microsoft-onedrive-lti-with-canvas"></a>Integrer Microsoft OneDrive LTI med Lærred

Integrering Microsoft OneDrive LTI med Lærred er en proces i to trin. Det første trin aktiverer Microsoft OneDrive i Lærred, og det andet trin gør Microsoft OneDrive LTI tilgængelig i Lærred-kurser.

## <a name="recommended-browser-settings"></a>Anbefalede browserindstillinger

- Cookies bør være aktiveret for Microsoft OneDrive.
- Pop op-pop op-programmer bør ikke blokeres for Microsoft OneDrive.

> [!NOTE]
> - Cookies er som standard ikke aktiveret i Chrome-browserens inkognitotilstand og skal være aktiveret.
> - Microsoft OneDrive LTI fungerer i privat tilstand i Microsoft Edge browser. Sørg for, at du ikke har blokerede cookies (der er aktiveret som standard).

## <a name="enable-microsoft-onedrive-lti-in-canvas"></a>Aktivér Microsoft OneDrive LTI i Lærred

> [!IMPORTANT]
> Den person, der udfører denne integration, skal være administrator for Canvas og administrator for Microsoft 365 lejer.

1. Log på Microsoft OneDrive <a href="https://onedrivelti.microsoft.com/admin" target="_blank">LTI-registreringsportal</a>
1. Vælg knappen **Administratorsamtykke** , og acceptér tilladelserne.

> [!CAUTION]
> Hvis dette trin ikke udføres, giver det følgende trin dig en fejl, og du vil ikke kunne tage dette trin i en time, når du har fået fejlen.

3. Vælg knappen **Opret ny LTI-lejer** . På siden LTI-registrering skal du **vælge Lærred** i rullemenuen og angive den grundlæggende URL-adresse for din Lærred-forekomst.

> [!NOTE]
> Hvis din Canvas-forekomst f.eks. https://contoso.test.instructure.comer ](https://contoso.test.instructure.com), skal den fulde URL-adresse angives.

:::image type="content" source="media/OneDrive-LTI-07.png" alt-text="LTI-lejeradministrationssiden med et rullefelt til valg af LTI-forbrugerplatform og et URL-tekstfelt.":::

4. Kopiér JSON ved at vælge **knappen** Kopiér (et ikon til højre, der viser to sider oven på hinanden). Dette bruges til at generere nøglen i Canvas.

:::image type="content" source="media/OneDrive-LTI-08.png" alt-text="Et billede, der viser knappen Kopiér, der kopierer den viste JSON-tekst og gør den tilgængelig til tastegenerering i Lærred.":::

5. Log på din Canvas-forekomst som administrator, **og vælg Udviklernøgler** i menuen til venstre på siden. På rullelisten skal du oprette en udviklernøgle ved at **vælge LTI-nøgle** på rullelisten øverst til højre på siden.

:::image type="content" source="media/OneDrive-LTI-14.png" alt-text="Et skærmbillede, der viser den venstre navigationslinje med Udviklernøgler markeret og LTI-tasten, der er valgt på en rulleliste til højre på siden.":::

6. På siden Konfigurer i rullemenuen Metode  skal du vælge Indsæt **JSON** som metode og indsætte den JSON-tekst, du kopierede i trin 4, i det tekstfelt, der vises.

    > [!TIP]
    > **Valgfri trin:** Hvis din skoles lærere selv ønsker at styre, hvilke links der vises i deres fags navigation, ``default`` kan du ændre parameteren i den kopierede JSON. Parameteren ``default`` er indstillet til ``enabled`` automatisk, men hvis parameteren ændres ``default`` ``disabled`` , kan undervisere vælge deres egne kursers navigation.
    >
    > Hvis du vil have mere at vide om, hvordan undervisere kan ændre deres kursusnavigationslinks, [skal du se Hvordan administrerer jeg links til Kursusnavigation?](https://community.canvaslms.com/t5/Instructor-Guide/How-do-I-manage-Course-Navigation-links/ta-p/1020)

7. Gem nøglen, og den bliver tilgængelig i lærredet **i tilstanden Fra** . Slå nøglen Til **,** og kopiér den nøgle, der er angivet **i kolonnen** Detaljer, der skal bruges i næste trin.

:::image type="content" source="media/OneDrive-LTI-19.png" alt-text="Siden Lærred med tasten i en deaktiveret tilstand. Den skal være slået til, og nøglen skal kopieres fra detaljekolonnen på denne side.":::

8. Gå tilbage til Microsoft OneDrive LTI-registreringsportalen, og indsæt nøglen i **feltet Lærred-klient-id**. Vælg **Næste** , når du er klar.

:::image type="content" source="media/OneDrive-LTI-20.png" alt-text="Registreringssiden for LTI-lejeren, som viser JSON-teksten og det tekstfelt, som nøglen skal kopieres til.":::

9. Gennemse og gem ændringerne. Der vises en meddelelse, når registreringen er gennemført.
10. Dine registreringsoplysninger kan også gennemses ved at vælge **knappen Vis LTI-lejere** på startsiden.

## <a name="enable-microsoft-onedrive-lti-in-canvas-courses"></a>Aktivere Microsoft OneDrive LTI i Lærred-kurser

En Lærred-administrator kan aktivere Microsoft OneDrive LTI for alle kurser. Hvis Microsoft OneDrive LTI i et bestemt kursus (og ikke alle kurser), skal underviseren følge de samme trin i kursusindstillingerne.

1. Log på som administrator, og gå til **Indstillinger** sektion.
2. Gå til sektionen **Apps** , og vælg knappen **Vis appkonfigurationer** .
3. Vælg **knappen Tilføj** app.
4. Vælg **indstillingen Efter klient-id** på **rullelisten Konfigurationstype** .
5. Indsæt værdien af udviklernøglen, der tidligere blev genereret **i feltet Klient-id** , og vælg **knappen Send** .

:::image type="content" source="media/OneDrive-LTI-31.png" alt-text="Siden Tilføj app, der viser indstillingen Efter klient-id under rullemenuen Konfigurationstype.":::

## <a name="collaboration-settings-for-microsoft-onedrive-lti-in-canvas-courses"></a>Samarbejdskurser Indstillinger til Microsoft OneDrive LTI i Lærredskurser

> [!NOTE]
> Hvis samarbejde skal kunne fungere for undervisere og studerende, bør du ikke aktivere indstillingen for samarbejde. Følg nedenstående trin for at sikre, at indstillingen ikke er aktiveret.

1. Log på som administrator, og gå til **Indstillinger** sektion.
1. Gå til **sektionen Funktionsindstillinger** , og gå derefter **til sektionen** Kursus.
1. Indstil **funktionen eksternt samarbejde til** ikke at være aktiveret.

> [!NOTE]
> Samarbejde kan tildeles til individuelle studerende og til grupper af studerende. Tildeling til individuelle studerende fungerer som standard. Hvis du vil kunne tildele samarbejde til en gruppe af studerende, skal du følge disse trin:

1. Log på som administrator, og gå **til sektionen Udviklernøgler** .
1. Find nøglen med værdinøglen 170000000000710 og indstil den til **Til**.
