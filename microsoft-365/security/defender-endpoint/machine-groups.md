---
title: Opret og administrer enhedsgrupper i Microsoft Defender til Slutpunkt
description: Opret enhedsgrupper, og angiv automatiserede afhjælpningsniveauer for dem ved at bekræfte de regler, der gælder for gruppen
keywords: enhedsgrupper, grupper, afhjælpning, niveau, regler, aad-gruppe, rolle, tildel, rang
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
ms.openlocfilehash: 951e49ddb7cb9ed0154fa70f66d54944a8aae066
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/25/2022
ms.locfileid: "63592743"
---
# <a name="create-and-manage-device-groups"></a>Opret og administrer enhedsgrupper

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- Azure Active Directory
- Office 365
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

I et virksomhedsscenarie tildeles sikkerhedsteams typisk et sæt enheder. Disse enheder er grupperet sammen baseret på et sæt af attributter, f.eks. deres domæner, computernavne eller angivne mærker.

I Microsoft Defender til Slutpunkt kan du oprette enhedsgrupper og bruge dem til at:

- Begræns adgang til relaterede beskeder og data til bestemte Azure AD-brugergrupper med tildelte [RBAC-roller](rbac.md)
- Konfigurer forskellige indstillinger for automatisk afhjælpning for forskellige sæt enheder
- Tildel specifikke afhjælpningsniveauer, der skal anvendes under automatiserede undersøgelser
- Under en undersøgelse skal du filtrere **listen enheder til** bestemte enhedsgrupper ved hjælp af **filteret** Gruppe.

Du kan oprette enhedsgrupper i forbindelse med rollebaseret adgang (RBAC) for at styre, hvem der kan gøre noget specifikt eller se oplysninger ved at tildele en eller flere enhedsgruppe(er) til en brugergruppe. Få mere at vide under [Administrer portaladgang ved hjælp af rollebaseret adgangskontrol](rbac.md).

> [!TIP]
> Du kan få et nærmere kig på RBAC-programmet ved at læse: [Kører din SOC fladt med RBAC](https://techcommunity.microsoft.com/t5/Windows-Defender-ATP/Is-your-SOC-running-flat-with-limited-RBAC/ba-p/320015).

Som en del af processen med at oprette en enhedsgruppe skal du:

- Angiv det automatiserede afhjælpningsniveau for den pågældende gruppe. Du kan finde flere oplysninger om afhjælpningsniveauer [i Brug automatiseret undersøgelse til at undersøge og afhjælpe trusler](automated-investigations.md).
- Angiv den matchende regel, der bestemmer, hvilken enhedsgruppe der tilhører gruppen, baseret på enhedsnavn, domæne, mærker og styresystemplatform. Hvis en enhed også matches til andre grupper, føjes den kun til den højest placerede enhedsgruppe.
- Vælg den Azure AD-brugergruppe, der skal have adgang til enhedsgruppen.
- Rangordn enhedsgruppen i forhold til andre grupper, efter den er blevet oprettet.

> [!NOTE]
> En enhedsgruppe er tilgængelig for alle brugere, hvis du ikke tildeler nogen Azure AD-grupper til den.

## <a name="create-a-device-group"></a>Opret en enhedsgruppe

1. I navigationsruden skal **du Indstillinger** \> **grupperne** **Slutpunktstilladelser** \> \> **enhed**.

2. Klik **på Tilføj enhedsgruppe**.

3. Angiv gruppenavnet og automatiseringsindstillingerne, og angiv den matchende regel, der bestemmer, hvilke enheder der tilhører gruppen. Se [Sådan starter den automatiserede undersøgelse](automated-investigations.md#how-the-automated-investigation-starts).

    > [!TIP]
    > Hvis du vil bruge mærkning til gruppering af enheder, skal du se [Opret og administrer enhedsmærker](machine-tags.md).

4. Få vist eksempler på flere enheder, der matches af denne regel. Hvis du er tilfreds med reglen, skal du klikke på **fanen Brugeradgang** .

5. Tildel de brugergrupper, der har adgang til den enhedsgruppe, du har oprettet.

    > [!NOTE]
    > Du kan kun give adgang til Azure AD-brugergrupper, der er tildelt RBAC-roller.

6. Klik **på Luk**. Konfigurationsændringerne anvendes.

## <a name="manage-device-groups"></a>Administrer enhedsgrupper

Du kan hæve eller sænke rangen for en enhedsgruppe, så den får en højere eller lavere prioritet under matchning. Når en enhed matches til mere end én gruppe, føjes den kun til den højest rangerede gruppe. Du kan også redigere og slette grupper.

> [!WARNING]
> Sletning af en enhedsgruppe kan påvirke regler for mailbeskeder. Hvis en enhedsgruppe er konfigureret under en mailmeddelelsesregel, fjernes den fra denne regel. Hvis enhedsgruppen er den eneste gruppe, der er konfigureret til en mailmeddelelse, slettes den pågældende mailmeddelelsesregel sammen med enhedsgruppen.

Som standard er enhedsgrupper tilgængelige for alle brugere med portaladgang. Du kan ændre standardfunktionsmåden ved at tildele Azure AD-brugergrupper til enhedsgruppen.

Enheder, der ikke passer til nogen grupper, føjes til gruppen Grupperede enheder (standard). Du kan ikke ændre rangen for denne gruppe eller slette den. Du kan dog ændre afhjælpningsniveauet for denne gruppe og definere de Azure AD-brugergrupper, der kan få adgang til denne gruppe.

> [!NOTE]
> Det kan tage op til flere minutter at anvende ændringer på enhedsgruppering.

### <a name="add-device-group-definitions"></a>Tilføje enhedsgruppedefinitioner

Definitioner af enhedsgrupper kan også indeholde flere værdier for hver betingelse. Du kan angive flere mærker, enhedsnavne og domæner som definition af en enkelt enhedsgruppe.

1. Opret en ny enhedsgruppe, og vælg derefter **fanen** Enheder.
2. Adder den første værdi for en af betingelserne.
3. Vælg `+` for at tilføje flere rækker af samme egenskabstype.

> [!TIP]
> Brug operatoren 'ELLER' mellem rækker af samme betingelsestype, som tillader flere værdier pr. egenskab.
> Du kan tilføje op til 10 rækker (værdier) for hver egenskabstype – mærke, enhedsnavn, domæne.

Du kan finde flere oplysninger om at oprette kæder til definitioner af [enhedsgrupper under Enhedsgrupper – Microsoft 365 sikkerhed](https://sip.security.microsoft.com/homepage).

## <a name="related-topics"></a>Relaterede emner

- [Administrere portaladgang ved hjælp af rollebaseret adgangskontrol](rbac.md)
- [Opret og administrer enhedsmærker](machine-tags.md)
- [Hent en liste over lejerenhedsgrupper ved hjælp Graph API](/graph/api/device-list-memberof)
