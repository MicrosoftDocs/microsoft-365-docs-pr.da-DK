---
title: Administrer Microsoft Defender for Endpoint vigtige beskeder
description: Rediger status for beskeder, opret skjulningsregler for at skjule beskeder, sende kommentarer og gennemse ændringsoversigten for individuelle beskeder med menuen Administrer besked.
keywords: administrere beskeder, administrere, beskeder, status, ny, i gang, løst, løse beskeder, undertrykke, supression, regler, kontekst, historik, kommentarer, ændringer
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
ms.openlocfilehash: 83e7bd2cc46469cb6a5a6bc8c29a8d21dba20b7f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466185"
---
# <a name="manage-microsoft-defender-for-endpoint-alerts"></a>Administrer Microsoft Defender for Endpoint vigtige beskeder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

Defender til slutpunkt giver dig besked om mulige skadelige hændelser, attributter og kontekstafhængige oplysninger via beskeder. Der vises en oversigt over nye beskeder på **dashboardet** sikkerhedshandlinger, og du kan få adgang til alle beskeder i **køen Vigtige beskeder**.

Du kan administrere beskeder ved at vælge en besked i køen Vigtige beskeder eller fanen Beskeder på  siden Enhed for en enkelt enhed.

Hvis du vælger en besked et af disse steder, vises **administrationsruden Vigtige beskeder**.

:::image type="content" source="images/atp-alerts-selected.png" alt-text="Administrationsruden Beskeder og køen Vigtige beskeder" lightbox="images/atp-alerts-selected.png":::

## <a name="link-to-another-incident"></a>Opret et link til en anden hændelse

Du kan oprette en ny hændelse fra beskeden eller linke til en eksisterende hændelse.

## <a name="assign-alerts"></a>Tildel beskeder

Hvis en besked endnu ikke er tildelt, kan du vælge **Tildel til mig for** at tildele beskeden til dig selv.

## <a name="suppress-alerts"></a>Undertrykke beskeder

Der kan være scenarier, hvor du er nødt til at undertrykke beskeder fra at blive vist i Microsoft 365 Defender. Defender til Slutpunkt giver dig mulighed for at oprette undertrykkende regler for bestemte beskeder, der er kendt for at være besværlige, f.eks. kendte værktøjer eller processer i organisationen.

Du kan oprette skjule regler ud fra en eksisterende besked. De kan deaktiveres og gennables, hvis det er nødvendigt.

Når der oprettes en undertrykkende regel, træder den i kraft fra det tidspunkt, hvor reglen oprettes. Reglen påvirker ikke eksisterende beskeder, der allerede er i køen, før reglen blev oprettet. Reglen anvendes kun på beskeder, der opfylder de betingelser, der er angivet, efter reglen er oprettet.

Der er to kontekster for en undertrykkende regel, du kan vælge mellem:

- **Skjule beskeder på denne enhed**
- **Skjule beskeder i min organisation**

Reglens kontekst giver dig mulighed for at skræddersy, hvad der bliver dukket op i portalen, og sikre, at kun reelle sikkerhedsadvarsler vises på portalen.

Du kan bruge eksemplerne i følgende tabel som en hjælp til at vælge konteksten for en undertrykkende regel:

|Kontekst|Definition|Eksempelscenarier|
|---|---|---|
|**Skjule beskeder på denne enhed**|Beskeder med den samme titel på beskeden og på den specifikke enhed vil kun blive undertrykt. <p> Alle andre beskeder på den pågældende enhed undertrykkes ikke.|<ul><li>En sikkerhedsekspert undersøger et skadeligt script, der er blevet brugt til at angreb andre enheder i organisationen.</li><li>En udvikler opretter regelmæssigt PowerShell-scripts til deres team.</li></ul>|
|**Skjule beskeder i min organisation**|Beskeder med den samme titel for besked på en hvilken som helst enhed skjules.|<ul><li>Der anvendes et godt administrativt værktøj af alle i organisationen.</li></ul>|

### <a name="suppress-an-alert-and-create-a-new-suppression-rule"></a>Undertrykke en besked og oprette en ny suppressionsregel

Opret brugerdefinerede regler til at styre, hvornår beskeder undertrykkes eller løses. Du kan styre konteksten for, hvornår en besked skjules, ved at angive beskedens titel, Indikator for kompromis og betingelserne. Når du har angivet konteksten, kan du konfigurere handlingen og omfanget af beskeden.

1. Vælg den besked, du vil skjule. Dette viser ruden **Administration af** beskeder.

2. Vælg **Opret en undertrykkeregel**.

    Du kan oprette en undertrykkende betingelse ved hjælp af disse attributter. En AND-operator anvendes mellem hver betingelse, så der opstår kun undertrykkelse, hvis alle betingelser er opfyldt.

    - Fil SHA1
    - Filnavn – jokertegn understøttes
    - Mappesti – jokertegn understøttes
    - IP-adresse
    - URL- adresse – jokertegn understøttes
    - Kommandolinje – jokertegn understøttes

3. Vælg Udløser **IOC**.

4. Angiv handlingen og omfanget af beskeden.

   Du kan automatisk løse en besked eller skjule den fra portalen. Beskeder, der løses automatisk, vises i den løste sektion af køen til vigtige beskeder, siden med påmindelser og enhedens tidslinje og vises som løst på tværs af Defender til slutpunkt-API'er.

   Beskeder, der er markeret som skjulte, vil blive skjult fra hele systemet, både på enhedens tilknyttede beskeder og fra dashboardet og vil ikke blive streamet på tværs af Defender for Endpoint-API'er.

5. Angiv et regelnavn og en kommentar.

6. Klik på **Gem**.

#### <a name="view-the-list-of-suppression-rules"></a>Få vist listen over undertrykkende regler

1. I navigationsruden skal du **vælge Indstillinger** \> **Beskedundertrykning**.

2. Listen over regler for undertrykkelse viser alle de regler, som brugerne i organisationen har oprettet.

Du kan finde flere oplysninger om administration af regler for undertrykkelse [i Administrer regler for undertrykkelse](manage-suppression-rules.md)

## <a name="change-the-status-of-an-alert"></a>Ændre status for en besked

Du kan kategorisere vigtige beskeder ( **som Ny**, **I gang** eller **Løst) ved** at ændre deres status, efterhånden som undersøgelsen skrider frem. På den måde kan du organisere og administrere, hvordan dit team kan reagere på vigtige beskeder.

En teamleder kan f.eks. gennemse **alle nye beskeder** og beslutte at tildele dem til **køen I gang** til yderligere analyse.

Alternativt kan teamlederen tildele beskeden til den løste kø, hvis de ved, at beskeden er god, kommer fra en enhed, der er irrelevant (f.eks. en, der hører til en sikkerhedsadministrator), eller som bliver behandlet via en tidligere besked.

## <a name="alert-classification"></a>Klassificering af beskeder

Du kan vælge ikke at angive en klassificering eller angive, om en besked er en sand besked eller en falsk besked. Det er vigtigt at angive klassificeringen af sand positiv/falsk positiv. Denne klassificering bruges til at overvåge kvaliteten af beskeder og gøre beskeder mere nøjagtige. Feltet "determination" definerer yderligere pålidelighed for en "sand positiv" klassificering.

## <a name="add-comments-and-view-the-history-of-an-alert"></a>Tilføj kommentarer, og få vist en beskeds historik

Du kan tilføje kommentarer og få vist historiske hændelser for en besked for at se tidligere ændringer af beskeden.

Når der foretages en ændring eller kommentar til en besked, registreres den i **sektionen Kommentarer og** historik.

Tilføjede kommentarer vises med det samme i ruden.

## <a name="related-topics"></a>Relaterede emner

- [Administrer skjuleregler](manage-suppression-rules.md)
- [Få vist og organiser Microsoft Defender for Endpoint i køen vigtige beskeder](alerts-queue.md)
- [Undersøg Microsoft Defender for Endpoint vigtige beskeder](investigate-alerts.md)
- [Undersøg en fil, der er knyttet Microsoft Defender for Endpoint besked](investigate-files.md)
- [Undersøg enhederne Microsoft Defender for Endpoint listen Over enheder](investigate-machines.md)
- [Undersøg en IP-adresse, der er knyttet Microsoft Defender for Endpoint besked](investigate-ip.md)
- [Undersøg et domæne, der er knyttet Microsoft Defender for Endpoint besked](investigate-domain.md)
- [Undersøg en brugerkonto i Microsoft Defender for Endpoint](investigate-user.md)
