---
title: Få hændelsesmeddelelser via mail Microsoft 365 Defender
description: Få mere at vide om, hvordan du opretter regler for at få mailbeskeder om hændelser i Microsoft 365 Defender
keywords: hændelse, mail, mailbeskeder, konfigurer, brugere, postkasse, mail, hændelser, analysér, svar
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 600ff555762112222769fde0372716f4a89a12b9
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/03/2021
ms.locfileid: "63592005"
---
# <a name="get-incident-notifications-by-email"></a>Få hændelsesmeddelelser via mail

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Du kan konfigurere en Microsoft 365 Defender at give dine medarbejdere besked via mail om nye hændelser eller opdateringer til eksisterende hændelser. Du kan vælge at få meddelelser baseret på:

- Hændelsens alvorsgrad.
- Enhedsgruppe.
- Kun ved den første opdatering pr. hændelse.

Mailmeddelelsen indeholder vigtige oplysninger om hændelsen, f.eks. hændelsens navn, alvorsgrad og kategorier, blandt andre. Du kan også gå direkte til hændelsen og starte din analyse med det samme. Få mere at vide under [Undersøg hændelser](investigate-incidents.md).

Du kan tilføje eller fjerne modtagere i mailmeddelelser. Nye modtagere får besked om hændelser, når de er tilføjet. 

>[!NOTE]
>Du skal have tilladelsen "Administrer sikkerhedsindstillinger" for at konfigurere indstillinger for mailbeskeder. Hvis du har valgt at bruge grundlæggende administration af tilladelser, kan brugere med sikkerhedsadministratorroller eller globale administratorroller konfigurere mailbeskeder for dig. <br> <br>
På samme måde kan du, hvis din organisation bruger rollebaseret adgangskontrol, kun oprette, redigere, slette og modtage meddelelser baseret på enhedsgrupper, som du har tilladelse til at administrere.

## <a name="create-a-rule-for-email-notifications"></a>Opret en regel for mailbeskeder

Følg disse trin for at oprette en ny regel og tilpasse indstillinger for mailbeskeder.

1. I navigationsruden skal du vælge Indstillinger > Microsoft 365 Defender > **hændelsesmailmeddelelser**.
2. Vælg **Tilføj element**.
3. Skriv **regelnavnet og** en beskrivelse på siden Grundlæggende, og vælg derefter **Næste**.
4. På siden **Meddelelsesindstillinger** skal du konfigurere:
    - **Alvorsgrad for besked** – Vælg de alvorsgrader for beskeden, der udløser en hændelsesmeddelelse. Hvis du f.eks. kun vil informeres om hændelser med høj alvorlighed, skal du vælge **Høj**.
    - **Omfang for enhedsgrupper** – Du kan angive alle enhedsgrupper eller vælge på listen over enhedsgrupper i din lejer.
    - **Giv kun besked ved første forekomst pr. hændelse** – Vælg, om du kun vil have en besked på den første besked, der svarer til dine andre valg. Senere opdateringer eller beskeder, der er relateret til hændelsen, sender ikke yderligere meddelelser.
    - **Medtag organisationsnavn i mailen** – Vælg, om din organisations navn skal vises i mailmeddelelsen.
    - **Medtag lejerspecifik portallink** – Vælg, om du vil tilføje et link til lejer-id'et i mailmeddelelsen om adgang til en bestemt Microsoft 365 lejer.

    :::image type="content" source="../../media/get-incident-notifications/incidents-ss-email-notification-settings.png" alt-text="Indstillinger for meddelelser om hændelsesmail.":::

5. Vælg **Næste**. På siden **Modtagere skal** du tilføje de mailadresser, der modtager beskeder om hændelser. Vælg **Tilføj,** når du har skrevet hver ny mailadresse. Hvis du vil teste meddelelser og sikre, at modtagerne modtager dem i indbakkerne, skal du vælge **Send testmail**. 
6. Vælg **Næste**. Gennemgå **reglens indstillinger** på siden Gennemse regel, og vælg derefter **Opret regel**. Modtagerne begynder at modtage beskeder om hændelser via mail baseret på indstillingerne.

Hvis du vil redigere en eksisterende regel, skal du vælge den på listen over regler. I ruden med regelnavnet skal du **vælge Rediger** regel og foretage dine ændringer på **siderne Grundlæggende,** **Meddelelsesindstillinger og** Modtagere. 

Hvis du vil slette en regel, skal du markere den på listen over regler. Vælg Slet i ruden med **regelnavnet**.

## <a name="see-also"></a>Se også
- [Oversigt over hændelser](incidents-overview.md)
- [Prioriter hændelser](incident-queue.md)
- [Undersøg hændelser](investigate-incidents.md)
