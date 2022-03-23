---
title: Oprette og administrere roller for rollebaseret adgangskontrol
description: Opret roller, og definer de tilladelser, der er tildelt rollen som en del af den rollebaserede implementering af adgangskontrol i Microsoft 365 Defender
keywords: brugerroller, roller, få adgang til rbac
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
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 6f853df2d37cc41b2effb55ff10418af67df2bd6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592734"
---
# <a name="create-and-manage-roles-for-role-based-access-control"></a>Oprette og administrere roller for rollebaseret adgangskontrol

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-roles-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="create-roles-and-assign-the-role-to-an-azure-active-directory-group"></a>Opret roller, og tildel rollen til en Azure Active Directory gruppe

Følgende trin hjælper dig med at oprette roller i Microsoft 365 Defender. Det antages, at du allerede har oprettet Azure Active Directory brugergrupper.

1. Log på en <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> med en sikkerhedsadministrator eller en global administratorrolle.

2. I navigationsruden skal **du Indstillinger** \> **på Slutpunktsroller** \> (under **Tilladelser**).

3. Vælg **Tilføj element**.

4. Angiv det rollenavn, den beskrivelse og de tilladelser, du vil tildele rollen.

5. Vælg **Næste** for at tildele rollen til en Azure AD-sikkerhedsgruppe.

6. Brug filteret til at vælge den Azure AD-gruppe, du vil føje til denne rolle.

7. **Gem og luk**.

8. Anvend konfigurationsindstillingerne.

> [!IMPORTANT]
> Når du har oprettet roller, skal du oprette en enhedsgruppe og give adgang til enhedsgruppen ved at tildele den til en rolle, du lige har oprettet.

### <a name="permission-options"></a>Tilladelsesindstillinger

- **Vis data**
  - **Sikkerhedshandlinger** – Få vist alle data for sikkerhedshandlinger i portalen
  - **Trussel og håndtering af sikkerhedsrisici** – vis Håndtering af trusler og sikkerhedsrisici data på portalen

- **Aktive afhjælpningshandlinger**
  - **Sikkerhedshandlinger** – udføre svarhandlinger, godkende eller afvise afventende afhjælpningshandlinger, administrere tilladte/blokerede lister til automatisering og indikatorer
  - **Trussel og håndtering af sikkerhedsrisici – Håndtering af undtagelser** – Oprette nye undtagelser og administrere aktive undtagelser
  - **Trussels- håndtering af sikkerhedsrisici afhjælpning –** Indsend nye afhjælpningsanmodninger, opret billetter, og administrer eksisterende afhjælpningsaktiviteter

- **Undersøgelse af beskeder** – Administrer beskeder, start automatiserede undersøgelser, kør scanninger, indsaml undersøgelsespakker, administrer enhedsmærker, og download kun bærbare eksekverbare filer (PE)

- **Administrer indstillinger for portalsystem** – Konfigurer lagerindstillinger, SIEM og trussels-Intel API-indstillinger (gælder globalt), avancerede indstillinger, automatiserede filuploads, roller og enhedsgrupper

    > [!NOTE]
    > Denne indstilling er kun tilgængelig i rollen som Microsoft Defender for Endpoint-administrator (standard).

- **Administrer sikkerhedsindstillinger i Security Center** – Konfigurer indstillinger for ignorering af beskeder, administrer mappeudetryk for automatisering, onboard og offboard-enheder, administrer mailbeskeder, og administrer evalueringslaboratorium

- **Live response-funktioner**
  - **Grundlæggende** kommandoer:
    - Start en direkte svarsession
    - Udføre skrivebeskyttede live svar-kommandoer på eksterne enheder (undtagen kopiering og udførelse af filer)
    - Download en fil fra fjernenheden via live-svar
  - **Avancerede** kommandoer:
    - Download PE- og ikke-PE-filer fra filsiden
    - Upload en fil på fjernenheden
    - Få vist et script fra filbiblioteket
    - Udføre et script på fjernenheden fra filbiblioteket

Du kan finde flere oplysninger om de tilgængelige kommandoer under Undersøg [enheder ved hjælp af Live response](live-response.md).

## <a name="edit-roles"></a>Rediger roller

1. Log på en <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> med sikkerhedsadministrator eller global administratorrolle tildelt.

2. I navigationsruden skal **du Indstillinger** \> **på Slutpunktsroller** \> (under **Tilladelser**).

3. Vælg den rolle, du vil redigere.

4. Klik på **Rediger**.

5. Rediger oplysningerne eller de grupper, der er tildelt rollen.

6. Klik **på Gem, og luk**.

## <a name="delete-roles"></a>Slet roller

1. Log på en <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> med sikkerhedsadministrator eller global administratorrolle tildelt.

2. I navigationsruden skal **du Indstillinger** \> **på Slutpunktsroller** \> (under **Tilladelser**).

3. Vælg den rolle, du vil slette.

4. Klik på rullelisten, og vælg **Slet rolle**.

## <a name="related-topic"></a>Relateret emne

- [Grundlæggende tilladelser til at få adgang til portalen](basic-permissions.md)
- [Opret og administrer enhedsgrupper](machine-groups.md)
