---
title: Automatiseringer af nyttedata til oplæring af simulering af angreb
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
description: Administratorer kan få mere at vide om, hvordan de bruger automatiseringer af nyttedata (høst af nyttedata) til at indsamle og starte automatiserede simuleringer til oplæring af simulering af angreb i Microsoft Defender for Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: 5b008dc25ee3b705f212b1fac1bf3779f1de8bda
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647507"
---
# <a name="payload-automations-for-attack-simulation-training"></a>Automatiseringer af nyttedata til oplæring af simulering af angreb

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for** [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Under oplæring af simulering af angreb i Microsoft 365 E5 eller Microsoft Defender for Office 365 Plan 2 indsamler nyttedataautomatiseringer (også kaldet _indsamling af nyttedata_) oplysninger fra phishing-meddelelser fra den virkelige verden, som blev rapporteret af brugere i din organisation. Selvom antallet af disse meddelelser sandsynligvis er lavt i din organisation, kan du angive de betingelser, der skal søges efter i phishing-angreb (f.eks. modtagere, teknik til social engineering, afsenderoplysninger osv.). Oplæring af simulering af angreb efterligner derefter de meddelelser og nyttedata, der bruges i angrebet, for automatisk at starte harmløse simuleringer til målrettede brugere.

Benyt følgende fremgangsmåde for at oprette en automatisering af nyttedata:

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com/>skal du gå til fanen **Email & collaboration** \> **Attack simulation training** \> **Payload automations**.

   Hvis du vil gå direkte til fanen **Nyttedataautomatiseringer** , skal du bruge <https://security.microsoft.com/attacksimulator?viewid=payloadautomation>.

2. På fanen **Payload automations** skal du vælge ![Ikonet Opret automatisering.](../../media/m365-cc-sc-create-icon.png) **Opret automatisering**.

   :::image type="content" source="../../media/attack-sim-training-sim-automations-create.png" alt-text="Knappen Opret simulering på fanen Payload automations i Oplæring af simulering af angreb på Microsoft 365 Defender-portalen" lightbox="../../media/attack-sim-training-sim-automations-create.png":::

3. Guiden Til oprettelse åbnes. I resten af denne artikel beskrives siderne og de indstillinger, de indeholder.

> [!NOTE]
> Når som helst under oprettelsesguiden kan du klikke på **Gem og luk** for at gemme dine fremskridt og fortsætte med at konfigurere automatiseringen af nyttedata senere. Du kan fortsætte, hvor du slap, ved at vælge nyttedataautomatisering under fanen **Nyttedataautomatiseringer** og derefter klikke på ![ikonet Rediger automatisering.](../../media/m365-cc-sc-edit-icon.png) **Rediger automatisering**.

## <a name="automation-name"></a>Automatiseringsnavn

Konfigurer følgende indstillinger på siden **Automation-navn** :

- **Navn**: Angiv et entydigt, beskrivende navn til automatiseringen af nyttedata.
- **Beskrivelse**: Angiv en valgfri detaljeret beskrivelse af automatiseringen af nyttedata.

Klik på **Næste**, når du er færdig.

## <a name="run-conditions"></a>Kørselsbetingelser

På siden **Kørselsbetingelser** skal du vælge betingelserne for det virkelige phishing-angreb, der bestemmer, hvornår automatiseringen kører.

Du kan kun bruge hver betingelse én gang. Flere betingelser bruger AND-logik (\<Condition1\> og \<Condition2\>).

![Tilføj betingelsesikon.](../../media/m365-cc-sc-create-icon.png) **Tilføj betingelse**.

- **Nej. af de brugere, der er målrettet i kampagnen**: Konfigurer følgende indstillinger:
  - **Lig med**, **Mindre end**, **Større end**, **Mindre end eller lig med** eller **Større end eller lig med**.
  - **Angiv værdi**: Antallet af brugere, der blev målrettet af phishing-kampagnen.
- **Kampagner med en bestemt phishteknik**: Vælg en af de tilgængelige værdier:
  - **Høst af legitimationsoplysninger**
  - **Vedhæftet malware**
  - **Link i vedhæftet fil**
  - **Link til malware**
  - **Drev efter URL-adresse**
- **Bestemt afsenderdomæne**: Angiv en værdi for afsenderens maildomæne (f.eks. contoso.com).
- **Bestemt afsendernavn**: Angiv en værdi for afsenderens navn.
- **Bestemt afsendermail**: Angiv en afsendermailadresse.
- **Specifikke bruger- og gruppemodtagere**: Begynd at skrive navnet eller mailadressen på brugeren eller gruppen. Når den vises, skal du vælge den.

Hvis du vil fjerne en betingelse, når du har tilføjet den, skal du klikke på ![Fjern ikon.](../../media/m365-cc-sc-delete-icon.png).

Klik på **Næste**, når du er færdig.

## <a name="review-automation"></a>Gennemse automatisering

På siden **Gennemse automatisering** kan du gennemse oplysningerne om din nyttedataautomatisering.

Du kan vælge **Rediger** i hver sektion for at redigere indstillingerne i sektionen. Du kan også klikke på **Tilbage** eller vælge den specifikke side i guiden.

Klik på **Send**, når du er færdig.
