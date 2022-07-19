---
title: Tillad cookies for LMS-URL-adresser i din browser
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du tillader cookies for LMS-URL-adresser i Edge-, Chrome- og Firefox- og Safari-browsere.
ms.openlocfilehash: 84ba252f9d3854fad4e89bd6e9dac8d0b020cf3a
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "66858522"
---
# <a name="allow-cookies-for-lms-urls-in-your-browser"></a>Tillad cookies for LMS-URL-adresser i din browser

Der kræves browsercookies fra tredjepart for at fuldføre LTI 1.3-håndtrykket i henhold til globale IMS-standarder. Når du starter LTI-værktøjet fra et LMS (Learning Management System), skal browserindstillingen derfor tillade cookies fra tredjepart for LMS-URL-adressen.

Her er de trin, du skal udføre for at tillade cookies i din browser.

# <a name="microsoft-edge"></a>[Microsoft Edge](#tab/edge)

## <a name="allow-cookies-for-lms-urls-in-microsoft-edge"></a>Tillad cookies for URL-adresser til LMS i Microsoft Edge

1. I vinduet **Edge-indstillinger** skal du vælge **Cookies og webstedstilladelser** > **Cookies og data, der er gemt** > **Administrer og slet cookies og webstedsdata**.
2. Slå **Tillad, at websteder gemmer og læser cookiedata (anbefales),** og sørg for, at **Bloker cookies fra tredjepart** er slået fra.

Hvis du skal blokere cookies fra tredjepart:

1. I vinduet **Edge-indstillinger** skal du vælge **Cookies og webstedstilladelser** > **Cookies og data, der er gemt** > **Administrer og slet cookies og webstedsdata**.
2. Under **Tillad** skal du vælge **Tilføj** for at tilføje DOMÆNE-URL-adressen til LMS-platformen.
   1. Hvis LMS-platformen f.eks. hostes på `https://contoso.com`, skal denne URL-adresse tilføjes under **Tillad**.

![Skærmbillede af siden med indstillinger for cookies i Microsoft Edge](media/edge-cookies.png)

# <a name="google-chrome"></a>[Google Chrome](#tab/chrome)

## <a name="allow-cookies-for-lms-urls-in-google-chrome"></a>Tillad cookies for LMS URL-adresser i Google Chrome

1. I vinduet **Chrome-indstillinger** under fanen **Beskyttelse af personlige oplysninger og sikkerhed** skal du vælge **Cookies og andre webstedsdata**.

2. Under **Websteder, der altid kan bruge cookies** skal du vælge **Tilføj** og derefter markere afkrydsningsfeltet **Herunder cookies fra tredjepart på dette websted** .

3. Tilføj DOMÆNE-URL-adressen for LMS-platformen.
   1. Hvis LMS-platformen f.eks. hostes på `https://contoso.com`, skal den pågældende URL-adresse bruges.

![Skærmbillede af siden med indstillinger for Google Chrome-cookie](media/chrome-cookies.png)

# <a name="mozilla-firefox"></a>[Mozilla Firefox](#tab/firefox)

## <a name="allow-cookies-for-lms-urls-in-mozilla-firefox"></a>Tillad cookies for LMS URL-adresser i Mozilla Firefox

1. I vinduet **Firefox-indstillinger** skal du vælge fanen **Beskyttelse af personlige oplysninger & Sikkerhed** .

2. Under **Cookies og Webstedsdata** skal du vælge **Administrer undtagelser**.

3. I tekstfeltet **Adresse på websted** skal du angive URL-adressen til LMS-platformen.
   1. Hvis LMS-platformen f.eks. hostes på `https://contoso.com`, skal den pågældende URL-adresse bruges.

4. Vælg **Tillad** for at tillade cookies for det angivne websted.

5. Vælg **Gem ændringer**.

![Skærmbillede af siden med indstillinger for Mozilla Firefox-cookie](media/firefox-cookies.png)

# <a name="safari"></a>[Safari](#tab/safari)

## <a name="allow-cookies-for-lms-urls-in-safari"></a>Tillad cookies for LMS URL-adresser i Safari

1. Vælg **Indstillinger** > **Beskyttelse af personlige oplysninger**.

2. Fjern markeringen i afkrydsningsfeltet **Forbyd sporing på tværs af websteder** .

---

> [!NOTE]
> I kan du ikke selv ændre indstillingerne (din browser administreres af din organisation), skal du kontakte it-afdelingen.
