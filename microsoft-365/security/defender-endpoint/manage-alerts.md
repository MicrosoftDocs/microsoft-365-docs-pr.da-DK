---
title: Administrer Microsoft Defender for Endpoint beskeder
description: Rediger status for beskeder, opret undertrykkelsesregler for at skjule beskeder, sende kommentarer og gennemse ændringsoversigten for individuelle beskeder i menuen Administrer beskeder.
keywords: administrere beskeder, administrere, beskeder, status, ny, i gang, løse, løse beskeder, undertrykke, supression, regler, kontekst, historik, kommentarer, ændringer
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
ms.openlocfilehash: c14447301cfa6abf83c231361c020d261eeb87a9
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623435"
---
# <a name="manage-microsoft-defender-for-endpoint-alerts"></a>Administrer Microsoft Defender for Endpoint beskeder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

Defender for Endpoint giver dig besked om mulige skadelige hændelser, attributter og kontekstafhængige oplysninger via beskeder. Der vises en oversigt over nye beskeder i **dashboardet Til sikkerhedshandlinger**, og du kan få adgang til alle beskeder i **køen Beskeder**.

Du kan administrere beskeder ved at vælge en besked i **køen Beskeder** eller fanen **Beskeder** på siden Enhed for en enkelt enhed.

Når du vælger en besked et af disse steder, vises **ruden Administration af beskeder**.

:::image type="content" source="images/atp-alerts-selected.png" alt-text="Ruden Administration af beskeder og køen Beskeder" lightbox="images/atp-alerts-selected.png":::

Se denne video for at få mere at vide om, hvordan du bruger den nye beskedside Microsoft Defender for Endpoint.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4yiO5]

## <a name="link-to-another-incident"></a>Link til en anden hændelse

Du kan oprette en ny hændelse fra beskeden eller linket til en eksisterende hændelse.

## <a name="assign-alerts"></a>Tildel beskeder

Hvis der endnu ikke er tildelt en besked, kan du vælge **Tildel til mig** for at tildele beskeden til dig selv.

## <a name="suppress-alerts"></a>Skjul beskeder

Der kan være scenarier, hvor du skal undertrykke beskeder fra at blive vist i Microsoft 365 Defender. Med Defender for Endpoint kan du oprette undertrykkelsesregler for bestemte beskeder, der er kendt for at være uskadelige, f.eks. kendte værktøjer eller processer i din organisation.

Der kan oprettes undertrykkelsesregler ud fra en eksisterende besked. De kan deaktiveres og genaktiveres, hvis det er nødvendigt.

Når der oprettes en undertrykkelsesregel, træder den i kraft fra det tidspunkt, hvor reglen oprettes. Reglen påvirker ikke eksisterende beskeder, der allerede er i køen, før reglen oprettes. Reglen anvendes kun på beskeder, der opfylder de betingelser, der er angivet, når reglen er oprettet.

Der er to kontekster for en undertrykkelsesregel, som du kan vælge mellem:

- **Skjul besked på denne enhed**
- **Skjul vigtig besked i min organisation**

Konteksten for reglen giver dig mulighed for at skræddersy det, der vises på portalen, og sikre, at der kun vises reelle sikkerhedsbeskeder i portalen.

Du kan bruge eksemplerne i følgende tabel som en hjælp til at vælge konteksten for en regel for undertrykkelse:

|Forbindelse|Definition|Eksempelscenarier|
|---|---|---|
|**Skjul besked på denne enhed**|Beskeder med samme beskedtitel og kun på den specifikke enhed undertrykkes. <p> Alle andre beskeder på denne enhed undertrykkes ikke.|<ul><li>En sikkerhedsforsker undersøger et skadeligt script, der er blevet brugt til at angribe andre enheder i din organisation.</li><li>En udvikler opretter jævnligt PowerShell-scripts til deres team.</li></ul>|
|**Skjul vigtig besked i min organisation**|Beskeder med samme beskedtitel på en hvilken som helst enhed vil blive undertrykt.|<ul><li>Et godartet administrativt værktøj bruges af alle i din organisation.</li></ul>|

### <a name="suppress-an-alert-and-create-a-new-suppression-rule"></a>Skjul en besked, og opret en ny regel for undertrykkelse

Opret brugerdefinerede regler for at styre, hvornår beskeder undertrykkes eller løses. Du kan styre konteksten for, hvornår en besked undertrykkes, ved at angive beskedens titel, indikator for kompromis og betingelserne. Når du har angivet konteksten, kan du konfigurere handlingen og omfanget for beskeden.

1. Vælg den besked, du vil undertrykke. Derved vises ruden **Administration af beskeder** .

2. Vælg **Opret en regel for undertrykkelse**.

    Du kan oprette en undertrykkelsesbetingelse ved hjælp af disse attributter. Der anvendes en AND-operator mellem hver betingelse, så undertrykkelse finder kun sted, hvis alle betingelser er opfyldt.

    - Fil-SHA1
    - Filnavn – jokertegn understøttes
    - Mappesti - jokertegn understøttes
    - IP-adresse
    - URL-adresse – jokertegn understøttes
    - Kommandolinje – jokertegn understøttes

3. Vælg **udløser-IOC**.

4. Angiv handlingen og omfanget for beskeden.

   Du kan automatisk løse en besked eller skjule den på portalen. Beskeder, der løses automatisk, vises i sektionen Løst i beskedkøen, beskedsiden og enhedens tidslinje og vises som løst på tværs af Defender for Endpoint-API'er.

   Beskeder, der er markeret som skjulte, undertrykkes fra hele systemet, både på enhedens tilknyttede beskeder og fra dashboardet og streames ikke på tværs af Defender for Endpoint-API'er.

5. Angiv et regelnavn og en kommentar.

6. Klik på **Gem**.

#### <a name="view-the-list-of-suppression-rules"></a>Vis listen over undertrykkelsesregler

1. Vælg **Indstillinger** \> **Undertrykkelse af besked** i navigationsruden.

2. Listen over undertrykkelsesregler viser alle de regler, som brugerne i din organisation har oprettet.

Du kan få flere oplysninger om administration af undertrykkelsesregler under [Administrer undertrykkelsesregler](manage-suppression-rules.md)

## <a name="change-the-status-of-an-alert"></a>Skift status for en besked

Du kan kategorisere beskeder (som **Ny**, **Igangværende** eller **Løst**) ved at ændre deres status, efterhånden som undersøgelsen skrider frem. Dette hjælper dig med at organisere og administrere, hvordan dit team kan reagere på beskeder.

En teamleder kan f.eks. gennemse alle **nye** beskeder og beslutte at tildele dem til køen **I gang** for yderligere analyse.

Alternativt kan teamlederen tildele beskeden til køen **Løst** , hvis vedkommende ved, at beskeden er godartet, der kommer fra en enhed, der er irrelevant (f.eks. en, der tilhører en sikkerhedsadministrator), eller behandles via en tidligere besked.

## <a name="alert-classification"></a>Beskedklassificering

Du kan vælge ikke at angive en klassificering eller angive, om en besked er en sand besked eller en falsk besked. Det er vigtigt at angive klassificeringen af sand positiv/falsk positiv. Denne klassificering bruges til at overvåge beskedkvaliteten og gøre beskeder mere nøjagtige. Feltet "bestemmelse" definerer yderligere pålidelighed for en "sand positiv" klassificering.

## <a name="add-comments-and-view-the-history-of-an-alert"></a>Tilføj kommentarer, og få vist historikken for en besked

Du kan tilføje kommentarer og få vist historiske hændelser om en besked for at se tidligere ændringer af beskeden.

Når der foretages en ændring eller kommentar til en besked, registreres den i afsnittet **Kommentarer og historik** .

Tilføjede kommentarer vises straks i ruden.

## <a name="related-topics"></a>Relaterede emner

- [Administrer undertrykkelsesregler](manage-suppression-rules.md)
- [Få vist og organiser køen Microsoft Defender for Endpoint beskeder](alerts-queue.md)
- [Undersøg Microsoft Defender for Endpoint beskeder](investigate-alerts.md)
- [Undersøg en fil, der er knyttet til en Microsoft Defender for Endpoint besked](investigate-files.md)
- [Undersøg enheder på listen over Microsoft Defender for Endpoint enheder](investigate-machines.md)
- [Undersøg en IP-adresse, der er knyttet til en Microsoft Defender for Endpoint besked](investigate-ip.md)
- [Undersøg et domæne, der er knyttet til en Microsoft Defender for Endpoint besked](investigate-domain.md)
- [Undersøg en brugerkonto i Microsoft Defender for Endpoint](investigate-user.md)
