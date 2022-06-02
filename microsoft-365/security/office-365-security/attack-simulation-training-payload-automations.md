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
ms.openlocfilehash: bc7bba0d91e9b2ff1f9baddc52f717450660d070
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65838907"
---
# <a name="payload-automations-for-attack-simulation-training"></a>Automatiseringer af nyttedata til oplæring af simulering af angreb

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for** [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Under oplæring af simulering af angreb i Microsoft 365 E5 eller Microsoft Defender for Office 365 Plan 2 indsamler nyttedataautomatiseringer (også kaldet _indsamling af nyttedata_) oplysninger fra phishing-angreb, der er rapporteret af brugere i din organisation. Selvom antallet af disse meddelelser sandsynligvis er lavt i din organisation, kan du angive de betingelser, der skal søges efter i phishing-angreb (f.eks. modtagere, teknik til social engineering, afsenderoplysninger osv.). Oplæring af simulering af angreb efterligner derefter de meddelelser og nyttedata, der bruges i angrebet, for automatisk at starte harmløse simuleringer til målrettede brugere.

Hvis du vil se de tilgængelige automatiseringer af nyttedata, skal du åbne portalen Microsoft 365 Defender på <https://security.microsoft.com>, gå til **Mail & samarbejde** \> Oplæring \> **af angrebssimulering** \> **Automations** og derefter vælge **Nyttedataautomatiseringer**. Hvis du vil gå direkte til fanen **Automatiseringer** , hvor du kan vælge **Nyttedataautomatiseringer**, skal du bruge <https://security.microsoft.com/attacksimulator?viewid=automations>.

Følgende oplysninger vises for hver automatisering af nyttedata:

- **Automatiseringsnavn**
- **Type**: Værdien er **Payload**.
- **Elementer, der indsamles**
- **Senest ændret**
- **Status**: Værdien er **Klar** eller **Kladde**.

Når du vælger en automatisering af nyttedata på listen, vises der et pop op-vindue med følgende oplysninger:

- **Fanen Generelt** : Viser grundlæggende oplysninger om automatisering af simulering.
- **Fanen Kørselshistorik** : Denne fane er kun tilgængelig for automatiseringer af nyttedata med værdien **Status** **klar**.

## <a name="create-payload-automations"></a>Opret automatiseringer af nyttedata

Benyt følgende fremgangsmåde for at oprette en automatisering af nyttedata:

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com/>skal du gå til **Mail & samarbejde** \> **Oplæring af** \> simulering af angreb **Automatiseringer** \> **Nyttedataautomatiseringer**. Hvis du vil gå direkte til fanen **Automatiseringer** , hvor du kan vælge **Nyttedataautomatiseringer**, skal du bruge <https://security.microsoft.com/attacksimulator?viewid=automations>.

   Klik på ![Ikonet Opret automatisering.](../../media/m365-cc-sc-create-icon.png) **Opret automatisering**.

   :::image type="content" source="../../media/attack-sim-training-sim-automations-create.png" alt-text="Knappen Opret simulering på fanen Payload automations i Oplæring af simulering af angreb på Microsoft 365 Defender-portalen" lightbox="../../media/attack-sim-training-sim-automations-create.png":::

   > [!NOTE]
   > Når som helst under oprettelsesguiden kan du klikke på **Gem og luk** for at gemme dine fremskridt og fortsætte med at konfigurere automatiseringen af nyttedata senere. Du kan fortsætte, hvor du slap, ved at vælge nyttedataautomatisering i **automatiseringer af nyttedata** og derefter klikke på ![Ikonet Rediger automatisering.](../../media/m365-cc-sc-edit-icon.png) **Rediger automatisering**. Den delvist fuldførte automatisering af nyttedata har **statusværdien** **Kladde**.

2. Konfigurer følgende indstillinger på siden **Automation-navn** :

   - **Navn**: Angiv et entydigt, beskrivende navn til automatiseringen af nyttedata.
   - **Beskrivelse**: Angiv en valgfri detaljeret beskrivelse af automatiseringen af nyttedata.

   Klik på **Næste**, når du er færdig.

3. På siden **Kørselsbetingelser** skal du vælge betingelserne for det virkelige phishing-angreb, der bestemmer, hvornår automatiseringen kører.

   Klik på ![Ikonet Tilføj betingelse.](../../media/m365-cc-sc-create-icon.png) **Tilføj betingelse** , og vælg mellem en af følgende betingelser:

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

   Du kan kun bruge hver betingelse én gang. Flere betingelser bruger AND-logik (\<Condition1\> og \<Condition2\>).

   Hvis du vil tilføje en anden betingelse, skal du klikke på ![ikonet Tilføj betingelse.](../../media/m365-cc-sc-create-icon.png) **Tilføj betingelse**.

   Hvis du vil fjerne en betingelse, når du har tilføjet den, skal du klikke på ![Fjern ikon.](../../media/m365-cc-sc-delete-icon.png).

   Klik på **Næste**, når du er færdig.

4. På siden **Gennemse automatisering** kan du gennemse oplysningerne om din nyttedataautomatisering.

   Du kan vælge **Rediger** i hver sektion for at redigere indstillingerne i sektionen. Du kan også klikke på **Tilbage** eller vælge den specifikke side i guiden.

   Klik på **Send**, når du er færdig.

5. På siden **Ny automatisering oprettet** kan du bruge linkene til at aktivere automatiseringen eller gå til siden **Simuleringer** .

   Klik på **Udført**, når du er færdig.

Tilbage på **automatiseringerne af nyttedata** i **Automatiseringer** er den logonside, du oprettede, nu på listen.

## <a name="turn-payload-automations-on-or-off"></a>Slå automatiseringer af nyttedata til eller fra

Du kan kun slå nyttedataautomatiseringer til eller fra, hvor værdien **Status** er **Klar**. Du kan ikke aktivere eller deaktivere ufuldstændige automatiseringer af nyttedata, **hvor statusværdien** er **Kladde**.

Hvis du vil slå automatisering af nyttedata til, skal du vælge den på listen ved at klikke på afkrydsningsfeltet. Klik på ikonet ![Slå til.](../../media/m365-cc-sc-turn-on-off-icon.png) **Aktivér** det ikon, der vises, og klik derefter på **Bekræft** i dialogboksen.

Hvis du vil slå automatisering af nyttedata fra, skal du vælge den på listen ved at klikke på afkrydsningsfeltet. Klik på ikonet ![Slå fra.](../../media/m365-cc-sc-turn-on-off-icon.png) **Aktivér** det ikon, der vises, og klik derefter på **Bekræft** i dialogboksen.

## <a name="modify-payload-automations"></a>Rediger automatiseringer af nyttedata

Hvis du vil ændre en eksisterende automatisering af nyttedata i **automatiseringer af nyttedata**, skal du gøre et af følgende:

- Vælg automatiseringen af nyttedata på listen ved at klikke på afkrydsningsfeltet. Klik på ikonet ![Rediger automatisering.](../../media/m365-cc-sc-edit-icon.png) **Rediger automatiseringsikon** , der vises.
- Vælg automatiseringen af nyttedata på listen ved at klikke et vilkårligt sted i rækken undtagen afkrydsningsfeltet. I det pop op-vindue med detaljer, der åbnes, skal du klikke på **Rediger** under fanen **Generelt** i sektionerne **Navn**, **Beskrivelse** eller **Kør betingelser**.

Guiden til automatisering af nyttedata åbnes med indstillingerne og værdierne for den valgte automatisering af nyttedata. Trinnene er de samme som beskrevet i afsnittet [Opret automatiseringer af nyttedata](#create-payload-automations) .

## <a name="remove-payload-automations"></a>Fjern automatiseringer af nyttedata

Hvis du vil fjerne en automatisering af nyttedata, skal du vælge automatiseringen af nyttedata på listen ved at klikke på afkrydsningsfeltet. Klik på ikonet ![Slet.](../../media/m365-cc-sc-delete-icon.png) **Slet** ikon, der vises, og klik derefter på **Bekræft** i dialogboksen.

## <a name="related-links"></a>Relaterede links

[Kom i gang med at bruge kursus i angrebssimulering](attack-simulation-training-get-started.md)

[Simuleringsautomatiseringer til oplæring af simulering af angreb](attack-simulation-training-simulation-automations.md)

[Få indsigt via kursus i angrebssimulering](attack-simulation-training-insights.md)
