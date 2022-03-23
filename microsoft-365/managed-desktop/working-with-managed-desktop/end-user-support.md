---
title: Få brugersupport til Microsoft Managed Desktop
description: Sådan kan brugerne få hjælp til tjenesten og enhederne
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 48be29f8db689ddd0911d7512b267ba50c85a469
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2022
ms.locfileid: "63589083"
---
# <a name="getting-help-for-users"></a>Få hjælp til brugere

Hvis du har nået det sted i arbejdsprocessen[](../service-description/user-support.md), hvor du skal anmode om administratoradgang eller eskalering til Microsoft, skal du følge disse trin:

>[!NOTE]
>Disse supportindstillinger er ikke tilgængelige for enheder i gruppen Test.

## <a name="elevation-requests"></a>Anmodninger om udvidelse

Før du anmoder om administratoradgang til en enhed, er det bedst at gennemgå, hvilke handlinger der er bedst egnet.

| Handlinger | Eksempler |
| ------ | ------ |
| **Typiske handlinger** er beregnet til udvidelsesprocessen. Det udføres jævnligt ved fejlfinding af problemer med Microsoft Managed Desktop-enheder. | <ul><li>Administrator af indbyggede systemfejlfindingsprogrammer, kommandoprompten eller Windows PowerShell til fejlfinding af line of business-programmer.</li><li>Brug af en løsning til at rette noget, der bør fungere efter design (f.eks BitLocker-aktivering eller systemtid opdateres ikke).</li><li>Administrator af Enhedshåndtering til at udføre ting som opdateringsdrivere, fjerne en enhed eller søge efter nye ændringer.</li></ul>
| **Handlinger, der ikke anbefales** | <ul><li>Installation af software eller browsere.</li><li>Installation af drivere uden for Windows, herunder drivere til eksterne enheder.</li><li>Installation af .msi eller .exe filer.</li><li>Installation Windows funktioner.</li></ul>
| **Handlinger, der ikke understøttes** | <ul><li>Installation af software eller funktioner, der er i konflikt med Microsoft Managed Desktop-sikkerhed eller administrationsegenskaber eller -handlinger.</li><li>Deaktivere en Windows funktion, der kræves til Microsoft Managed Desktop, f.eks. BitLocker.</li><li>Ændring af indstillinger, der administreres af din organisation.</li><ul>

**Sådan anmoder du om udvidelse:**

1. Log på [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) og gå til **menuen** Enheder.
1. I sektionen **Microsoft Managed Desktop** skal du vælge **Enheder**, som indeholder to faner: **fanen Enheder** og **fanen Udvidelsesanmodninger** .
1. Hvis du vil oprette en ny udvidelsesanmodning på **fanen** Enhed, skal du vælge en enkelt enhed, du vil hæve.
1. I rullemenuen Enhedshandlinger skal du vælge **Anmod om udvidelse**. Der vises et flyv ind til en ny udvidelsesanmodning med enhedens navn udfyldt på forhånd.
1. I stedet skal du vælge + Ny **udvidelsesanmodning** for at oprette en ny udvidelsesanmodning **under fanen Anmodninger om udvidelse.**
1. Angiv disse oplysninger:
    - **Supportbillet-id**: Dette er fra dit eget supportbilletsystem.
    - **Enhedsnavn**: Dette er kun, når du opretter en anmodning fra **fanen Anmodninger om** udvidelse. Angiv enhedens serienummer, og vælg derefter enheden i menuen.
    - **Kategori**: Vælg den kategori, der passer bedst til dit problem. Hvis ingen indstilling ser ud til at være tæt på, skal du vælge **Andre**. Det er bedst at vælge en kategori, hvis det overhovedet er muligt.
    - **Titel**: Angiv en kort beskrivelse af problemet på enheden.
    - **Handlingsplan: Angiv de** fejlfindingstrin, du planlægger at udføre, når udvidelse er tildelt.
1. Vælg **Send**.
1. Listen og detaljerne for alle aktive og lukkede anmodninger kan ses på fanen **Udvidelsesanmodninger** .

## <a name="escalation-requests"></a>Eskaleringsanmodninger

**Sådan [eskalerer](../service-description/user-support.md#escalation-portal) du et problem til Microsoft:**

1. Log på Microsoft Endpoint Manager [og](https://endpoint.microsoft.com/) gå til **menuen Lejeradministration**.
2. I sektionen Microsoft Managed Desktop skal du vælge **Service requests**.
3. I sektionen **Serviceanmodninger** skal du vælge **+ Ny supportanmodning**.
4. Angiv en kort beskrivelse i **feltet** Titel. Angiv derefter **Anmodningstype til Hændelse**.
5. Vælg den **kategori** og **underkategori, der** passer bedst til dit problem. Vælg derefter **Næste**.
6. Angiv **følgende** oplysninger i sektionen Detaljer:
    - **Beskrivelse**: Tilføj eventuelle ekstra detaljer, der kan hjælpe vores team med at forstå problemet. Hvis du vil vedhæfte filer, kan du gøre det ved at vende tilbage til anmodningen, efter at du har indsendt den.
    - **Primære kontaktoplysninger**: Giv oplysninger om, hvordan du kontakter den primære person, der er ansvarlig for at arbejde med vores team.
7. Vælg **alvorsniveau** . Du kan finde flere oplysninger i [Supportanmodninger om alvorlighedsdefinitioner](../working-with-managed-desktop/admin-support.md#support-request-severity-definitions).
8. Angiv så mange oplysninger om anmodningen som muligt for at hjælpe teamet med at reagere hurtigt. Afhængigt af typen af anmodning kan det være nødvendigt at angive forskellige oplysninger.
9. Gennemse alle de oplysninger, du har angivet for nøjagtighed.
10. Vælg Opret, når du er **klar**.
