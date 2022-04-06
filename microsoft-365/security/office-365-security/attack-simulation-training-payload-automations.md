---
title: Automatisering af nyttedata til simulering af angreb
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Administratorer kan lære, hvordan de bruger automatisering af nyttedata (indsamling af nyttedata) til at indsamle og starte automatiserede simuleringskurser til simulering af angreb Microsoft Defender for Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: aa223ab1abda110e32a9b9dc55e9dc76a1983321
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468429"
---
# <a name="payload-automations-for-attack-simulation-training"></a>Automatisering af nyttedata til simulering af angreb

**Gælder for** [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

I kursus i angrebssimulering i Microsoft 365 E5 eller Microsoft Defender for Office 365 Plan 2 indsamler automatiseringer af nyttedata (også kaldet indsamling af nyttedata) oplysninger fra virkelige phishingmeddelelser, der er rapporteret af brugere i organisationen. Selvom antallet af disse meddelelser sandsynligvis er lavt i din organisation, kan du angive de betingelser, der skal søges efter i phishing-angreb (f.eks. modtagere, social teknik, afsenderoplysninger osv.). Kursus i angrebssimulering efterligner derefter meddelelser og nyttedata, der bruges i angreb, for automatisk at starte uskadelige simuleringssessioner til målrettede brugere.

Hvis du vil oprette en automatisering af nyttedata, skal du gøre følgende:

1. I portalen Microsoft 365 Defender på skal du gå <https://security.microsoft.com/>til Mail **& simulering af** \> **angrebssimuleringskursus** \> **Payload automationsfanen**.

   For at gå direkte til **fanen automatisering af nyttedata** skal du bruge <https://security.microsoft.com/attacksimulator?viewid=payloadautomation>.

2. På fanen **Automatisering af nyttedata** skal du vælge ![Opret automatiseringsikon.](../../media/m365-cc-sc-create-icon.png) **Opret automatisering**.

   :::image type="content" source="../../media/attack-sim-training-sim-automations-create.png" alt-text="Knappen Opret simulering på fanen Automatisering af nyttedata i Kursus i angrebssimulering Microsoft 365 Defender portalen" lightbox="../../media/attack-sim-training-sim-automations-create.png":::

3. Guiden til oprettelse åbnes. Resten af denne artikel beskriver siderne og de indstillinger, de indeholder.

> [!NOTE]
> Du kan når som helst under oprettelsesguiden klikke  på Gem og luk for at gemme din status og fortsætte med at konfigurere automatisering af nyttedata senere. Du kan gå videre til det sted, hvor du slap, ved at vælge automatiseringen af nyttedata under fanen Automatisering af nyttedata og derefter klikke på ![Rediger **automatiseringsikon**.](../../media/m365-cc-sc-edit-icon.png) **Rediger automatisering**.

## <a name="automation-name"></a>Automatiseringsnavn

På siden **Navn på** automatisering skal du konfigurere følgende indstillinger:

- **Navn**: Angiv et entydigt, beskrivende navn til automatisering af nyttedata.
- **Beskrivelse**: Angiv en valgfri detaljeret beskrivelse af automatiseringen af nyttedata.

Klik på Næste, når du er **færdig**.

## <a name="run-conditions"></a>Kørselsbetingelser

På siden **Kørselsbetingelser** skal du vælge betingelserne for det rigtige phishingangreb, der bestemmer, hvornår automatiseringen kører.

Du kan kun bruge hver betingelse én gang. Flere betingelser bruger AND-logik (\<Condition1\> og \<Condition2\>).

![Ikonet Tilføj betingelse.](../../media/m365-cc-sc-create-icon.png) **Tilføj betingelse**.

- **Nej. af brugere, der er målrettet i** kampagnen: Konfigurer følgende indstillinger:
  - **Lig med**, **Mindre end**, **Større end**, **Mindre end eller lig med** eller **Større end eller lig med**.
  - **Angiv værdi**: Antallet af brugere, der er blevet målrettet af phishingkampagnen.
- **Kampagner med en bestemt phish-teknik**: Vælg en af de tilgængelige værdier:
  - **Indsamling af legitimationsoplysninger**
  - **Vedhæftet malware**
  - **Link i vedhæftet fil**
  - **Link til malware**
  - **Drive-by URL**
- **Specifikt afsenderdomæne**: Angiv en domæneværdi for en afsendermail (f.eks contoso.com).
- **Specifikt afsendernavn**: Angiv en værdi for afsendernavn.
- **Specifik afsendermail**: Angiv en afsendermailadresse.
- **Bestemte brugere og gruppemodtagere**: Begynd at skrive navnet eller mailadressen på brugeren eller gruppen. Når den vises, skal du markere den.

Hvis du vil fjerne en betingelse, efter du har tilføjet den, skal du klikke på ![Ikonet Fjern.](../../media/m365-cc-sc-delete-icon.png).

Klik på Næste, når du er **færdig**.

## <a name="review-automation"></a>Gennemse automatisering

På siden **Gennemse automatisering** kan du gennemgå detaljerne for din automatisering af nyttedata.

Du kan vælge **Rediger** i hver sektion for at ændre indstillingerne i sektionen. Eller du kan klikke **på** Tilbage eller vælge den bestemte side i guiden.

Klik på Send, når du er **færdig**.
