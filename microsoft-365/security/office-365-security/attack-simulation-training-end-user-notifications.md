---
title: Slutbrugermeddelelser til kursus i angrebssimulering
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
description: Administratorer kan få mere at vide om, hvordan de opretter mails med slutbrugermeddelelser til oplæring i simulering af angreb i Microsoft Defender for Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: b26c8060fb869ea9e02ab06396a5a91281bcf3f0
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "66858638"
---
# <a name="end-user-notifications-for-attack-simulation-training"></a>Slutbrugermeddelelser til kursus i angrebssimulering

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Under oplæring af simulering af angreb i Microsoft 365 E5 eller Microsoft Defender for Office 365 Plan 2 er slutbrugermeddelelser mailmeddelelser, der sendes til brugerne som følge af [simuleringsautomatiseringer](attack-simulation-training.md).[](attack-simulation-training-simulation-automations.md) Følgende typer slutbrugermeddelelser er tilgængelige:

- **Meddelelse om positiv forstærkning**: Sendes, når brugerne rapporterer en simuleret phishing-meddelelse.
- **Simuleringsmeddelelse**: Sendes, når brugerne er inkluderet i en simulerings- eller simuleringsautomatisering, men der ikke er valgt nogen oplæringer.
- **Meddelelse om oplæringstildeling**: Sendes, når brugerne tildeles påkrævede kurser som følge af en simulerings- eller simuleringsautomatisering.
- **Påmindelsesmeddelelse om oplæring**: Sendt som påmindelser for påkrævede kurser.

Hvis du vil se de tilgængelige slutbrugermeddelelser, skal du åbne portalen Microsoft 365 Defender på <https://security.microsoft.com>, gå til **Mail & samarbejde** \> **Oplæring af simulering af angreb** \> **Bibliotek med simuleringsindhold** \> og derefter vælge **Slutbrugermeddelelser**. Hvis du vil gå direkte til fanen **Simuleringsindholdsbibliotek** , hvor du kan vælge **Slutbrugermeddelelser**, skal du bruge <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.

**Slutbrugermeddelelser** har to faner:

- **Globale meddelelser**: Indeholder de indbyggede meddelelser, der ikke kan ændres.
- **Lejermeddelelser**: Indeholder de brugerdefinerede meddelelser, du har oprettet.

Følgende oplysninger vises for hver meddelelse:

- **Meddelelser**: Navnet på meddelelsen.
- **Sprog**: Hvis meddelelsen indeholder flere oversættelser, vises de første to sprog direkte. Hvis du vil se de resterende sprog, skal du holde markøren over det numeriske ikon (f.eks. **+10**).
- **Type**: Værdien er **meddelelse om positiv forstærkning**, **simuleringsmeddelelse**, **meddelelse om oplæringstildeling** eller **påmindelse om oplæring**.
- **Kilde**: For indbyggede meddelelser er værdien **Global**. For brugerdefinerede meddelelser er værdien **Lejer**.
- **Status**: Værdien er **Klar** eller **Kladde**. På fanen **Globale meddelelser** er værdien altid **Klar**.
- **Sammenkædede simuleringer**: Det samlede antal [simulerings-](attack-simulation-training.md) eller [simuleringsautomatiseringer](attack-simulation-training-simulation-automations.md) , der bruger meddelelsen.
- **Oprettet af**: For indbyggede meddelelser er værdien **Microsoft**. For brugerdefinerede meddelelser er værdien UPN for den bruger, der oprettede meddelelsen.
- **Oprettelsestidspunkt**
- **Ændret af**
- **Tidspunkt for seneste ændring**

Hvis du vil finde en meddelelse på listen, skal du bruge søgeikonet ![.](../../media/m365-cc-sc-search-icon.png) **Søgefelt** for at finde navnet på meddelelsen.

Klik på ![Gruppeikon for at gruppere meddelelserne efter type.](../../media/m365-cc-sc-group-icon.png) **Gruppér** , og vælg derefter **Meddelelsestype**. Hvis du vil opdele meddelelserne, skal du vælge **Ingen**.

Klik på ![filterikonet under fanen Kun **lejermeddelelser**.](../../media/m365-cc-sc-filter-icon.png) for at filtrere meddelelserne efter et eller flere sprog.

Hvis du vil fjerne en eller flere kolonner, der vises, skal du klikke på ![ikonet Tilpas kolonner.](../../media/m365-cc-sc-customize-icon.png) **Tilpas kolonner**.

Når du vælger en meddelelse på listen, vises der et detaljeret pop op-vindue med følgende oplysninger:

- **Fanen Eksempel** : Få vist meddelelsesmeddelelsen, som brugerne kan se den. Hvis du vil have vist meddelelsen på forskellige sprog, skal du bruge feltet **Vælg sprog** .
- Fanen **Detaljer**: Få vist detaljer om meddelelsen:
  - **Meddelelsesbeskrivelse**
  - **Kilde**: For indbyggede meddelelser er værdien **Global**. For brugerdefinerede meddelelser er værdien **Lejer**.
  - **Meddelelsestype**
  - **Ændret af**
  - **Senest ændret**
  - **Simuleringer**
    - **Simuleringsnavne**
    - **Simuleringsstatus**
    - **Afslut senest**

Klik på **Rediger meddelelse** under fanen **Lejermeddelelser** i pop op-vinduet med detaljer for at redigere meddelelsen.

## <a name="create-end-user-notifications"></a>Opret slutbrugermeddelelser

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Fanen** \> Mail & samarbejde \> **Oplæring af simulering af angreb** \> **Bibliotek med simulering af indhold** og derefter vælge **Slutbrugermeddelelser**. Hvis du vil gå direkte til fanen **Simuleringsindholdsbibliotek** , hvor du kan vælge **Slutbrugermeddelelser**, skal du bruge <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.

2. Klik på ![Opret nyt ikon under fanen **Lejermeddelelser**.](../../media/m365-cc-sc-create-icon.png) **Opret ny** for at starte guiden til slutbrugermeddelelser.

   > [!NOTE]
   > Når som helst under oprettelsesguiden kan du klikke på **Gem og luk** for at gemme status og fortsætte med at konfigurere meddelelsen senere. Du kan fortsætte, hvor du slap, ved at vælge meddelelsen under fanen **Lejermeddelelser** i **Slutbrugermeddelelser** og derefter klikke på ![Ikonet Rediger automatisering.](../../media/m365-cc-sc-edit-icon.png) **Rediger automatisering**. Den delvist fuldførte meddelelse **har statusværdien** **Kladde**.

3. Konfigurer følgende indstillinger på siden **Definer detaljer** **:
   - **Vælg meddelelsestype**: Vælg en af følgende værdier:
     - **Meddelelse om positiv forstærkning**
     - **Simuleringsmeddelelse**
     - **Meddelelse om oplæringstildeling**
     - **Påmindelse om oplæring**
   - **Navn**: Angiv et entydigt navn.
   - **Beskrivelse**: Angiv en valgfri beskrivelse.

   Klik på **Næste**, når du er færdig.

4. På siden **Definer indhold** er den eneste indstilling, der er tilgængelig, knappen **Tilføj indhold på forretningssprog** . Når du klikker på det, vises pop op-vinduet **Tilføj indhold på standardsprog** , der indeholder følgende indstillinger:
   - **Fra vist navn**
   - **Fra mailadresse**
   - **Vælg sproget for mailen**: Vælg et sprog på listen.
   - **Markér dette som standardsproget**: Da dette er det første og eneste sprog for meddelelsen, vælges denne værdi, og du kan ikke ændre den.
   - **Emne**: Standardværdien er **Tak, fordi du rapporterer phish**, men du kan ændre den.
   - **Importér mail**: Du kan eventuelt klikke på denne knap og derefter klikke på **Vælg fil** for at importere en eksisterende meddelelsesfil i almindelig tekst.
   - Mailindholdsområde: To faner er tilgængelige:
     - **Fanen Tekst** : Der er en RTF-editor tilgængelig til oprettelse af din meddelelsesmail. Ud over de almindelige skrifttype- og formateringsindstillinger er følgende indstillinger tilgængelige:
       - **Dynamisk mærke**: Vælg mellem følgende mærker:
         - **Indsæt fornavn**
         - **Indsæt efternavn**
         - **Indsæt UPN**
         - **Indsæt mailadresse**
         - **Indsæt nyttedata**
     - **Fanen Kode** : Du kan få vist og redigere HTML-koden direkte.

   Du kan få vist resultaterne ved at klikke på knappen **Vis mail** øverst på siden.

   Klik på **Gem**, når du er færdig.

   Du vender tilbage til siden **Definer indhold** , hvor den meddelelse, du lige har oprettet, opsummeres med følgende oplysninger:

   - **Sprog**
   - **Emne**
   - **Kategori**
   - **Handlinger**: Følgende ikoner er tilgængelige:
     - ![Ikonet Rediger.](../../media/m365-cc-sc-edit-icon.png) **Redigere**
     - ![Ikonet Vis.](../../media/m365-cc-sc-view-icon.png) **Vis**
     - ![Ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) **Slet**: Hvis der kun er en sprogversion af meddelelsen, kan du ikke slette den.

   Hvis du vil tilføje en version af meddelelsen på et andet sprog, skal du klikke på ![Tilføj oversættelsesikon.](../../media/m365-cc-sc-create-icon.png) I pop op-vinduet **Tilføj oversættelse** , der vises, er de samme indstillinger tilgængelige som i pop op-vinduet **Tilføj indhold på standardsprog** , som tidligere blev beskrevet. Den eneste forskel er, at du kan vælge **Markér dette som standardsprog** i yderligere oversættelser.

   Når du er færdig, skal du klikke på **Gem**

   Du kan gentage disse trin så mange gange, det er nødvendigt, for at oprette oversatte versioner af meddelelsen på de 12 understøttede sprog.

   Klik på **Næste**, når du er færdig

5. På siden **Gennemse meddelelse** kan du gennemse detaljerne for din meddelelse.

   Du kan vælge **Rediger** i hver sektion for at redigere indstillingerne i sektionen. Du kan også klikke på **Tilbage** eller vælge den specifikke side i guiden.

   Klik på **Send**, når du er færdig.

   På siden **Ny simuleringsmeddelelse, der er oprettet** , kan du bruge linkene til at oprette en ny meddelelse, starte en simulering eller få vist alle meddelelser.

   Klik på **Udført**, når du er færdig.

Tilbage på fanen **Lejermeddelelser** i **Slutbrugermeddelelser** vises den meddelelse, du har oprettet, nu på listen.

## <a name="modify-end-user-notifications"></a>Rediger slutbrugermeddelelser

Du kan ikke ændre indbyggede meddelelser under fanen **Globale meddelelser** . Du kan kun redigere brugerdefinerede meddelelser under fanen **Lejermeddelelser** .

Hvis du vil redigere en eksisterende brugerdefineret meddelelse under fanen **Lejermeddelelser** , skal du gøre et af følgende:

- Vælg meddelelsen på listen ved at klikke på afkrydsningsfeltet. Klik på ikonet ![Rediger.](../../media/m365-cc-sc-edit-icon.png) **Redigeringsikon** , der vises.
- Klik **på ⋮** (**handlinger**) mellem **meddelelses-** og **sprogværdierne** for meddelelsen på listen, og vælg ![derefter Ikonet Rediger.](../../media/m365-cc-sc-edit-icon.png) **Rediger**.
- Vælg meddelelsen på listen ved at klikke et vilkårligt sted i rækken undtagen afkrydsningsfeltet. Klik på **Rediger meddelelse** i det pop op-vindue med detaljer, der åbnes.

Guiden til slutbrugermeddelelser åbnes med indstillingerne og værdierne for den valgte meddelelse. Trinnene er de samme som beskrevet i afsnittet [Opret slutbrugermeddelelser](#create-end-user-notifications) .

## <a name="copy-end-user-notifications"></a>Kopiér slutbrugermeddelelser

Hvis du vil kopiere en eksisterende meddelelse under **fanerne Lejermeddelelser** eller **Globale meddelelser** , skal du gøre et af følgende:

- Vælg meddelelsen på listen ved at klikke på afkrydsningsfeltet, og klik derefter på ikonet ![Opret en kopi.](../../media/m365-cc-sc-edit-icon.png) **Opret et kopiikon** , der vises.
- Klik **på ⋮** (**handlinger**) mellem **meddelelses-** og **sprogværdierne** for meddelelsen på listen, og vælg ![derefter Ikonet Opret en kopi.](../../media/m365-cc-sc-edit-icon.png) **Opret en kopi**.

Når du kopierer en brugerdefineret meddelelse under fanen **Lejermeddelelser** , er der en kopi af meddelelsen med navnet "\<OriginalName\> - Kopiér" tilgængelig på listen.

Når du kopierer en indbygget meddelelse under fanen **Globale meddelelser** , vises dialogboksen **Opret kopi** . Dialogboksen bekræfter, at der er oprettet en kopi af meddelelsen, og at den er tilgængelig under fanen **Lejermeddelelser** . Hvis du klikker på **Gå til lejermeddelelse** , sendes du til fanen **Lejermeddelelser** , hvor den kopierede indbyggede meddelelse hedder "\<OriginalName\> - Kopiér" er tilgængelig på listen. Hvis du klikker på **Bliv her** i dialogboksen, vender du tilbage til fanen **Globale meddelelser** .

Når kopien er oprettet, kan du ændre den som [beskrevet tidligere](#modify-end-user-notifications).

> [!NOTE]
> Med kontrolelementet **Brug fra standard** på pop op-vinduet **Tilføj indhold på standardsprog** i meddelelsesguiden kan du kopiere indholdet af en indbygget meddelelse.

## <a name="remove-notifications"></a>Fjern meddelelser

Du kan ikke fjerne indbyggede meddelelser fra fanen **Globale meddelelser** . Du kan kun fjerne brugerdefinerede meddelelser under fanen **Lejermeddelelser** .

Hvis du vil fjerne en eksisterende brugerdefineret meddelelse fra fanen **Lejermeddelelser** , skal du gøre et af følgende:

- Vælg meddelelsen på listen ved at klikke på afkrydsningsfeltet, og klik derefter på ikonet ![Slet.](../../media/m365-cc-sc-delete-icon.png) **Slet** ikon, der vises.
- Klik **på ⋮** (**handlinger**) mellem **meddelelses-** og **sprogværdierne** for meddelelsen på listen, og vælg ![derefter Ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) **Slet**.

## <a name="related-links"></a>Relaterede links

[Kom i gang med at bruge kursus i angrebssimulering](attack-simulation-training-get-started.md)

[Opret en simulering af phishingangreb](attack-simulation-training.md)

[Simuleringsautomatiseringer til oplæring af simulering af angreb](attack-simulation-training-simulation-automations.md)
