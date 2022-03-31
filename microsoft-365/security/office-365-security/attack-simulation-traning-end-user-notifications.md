---
title: Beskeder til slutbrugeren om simulering af angreb
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
description: Administratorer kan få mere at vide om, hvordan du opretter mailmeddelelser for angrebssimulering af angreb i Microsoft Defender Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: 3aa46724ef3414c83a5ece0c5fa17b4f9342c81c
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63601066"
---
# <a name="end-user-notifications-for-attack-simulation-training"></a>Beskeder til slutbrugeren om simulering af angreb

I angrebssimuleringskurser i Microsoft 365 E5 eller Microsoft Defender til Office 365 Plan 2 er slutbrugermeddelelser mails, der sendes til brugere Der er to grundlæggende typer meddelelser:

- **Simuleringsmeddelelser**: Disse meddelelser sendes, når brugerne er tilmeldt kurser og som påmindelser om nødvendige kurser.
- **Positive beskeder fra positive positive**: Disse meddelelser sendes, når brugere rapporterer en simuleret phishingmeddelelse.

Hvis du vil se den tilgængelige slutbrugermeddelelse, skal du åbne Microsoft 365 Defender-portalen  \>  \> <https://security.microsoft.com>på og derefter gå til mail & simulering af angrebssimulering **af samarbejde** Slutbrugerbeskeder. Hvis du vil gå direkte til **fanen Beskeder til slutbrugeren**, skal du bruge <https://security.microsoft.com/attacksimulator?viewid=endUserNotification>.

Fanen **Beskeder til slutbrugeren** har to faner:

- **Globale meddelelser**: Indeholder de indbyggede og ikke-modifierbare meddelelser.
- **Lejermeddelelser**: Indeholder de brugerdefinerede meddelelser, du har oprettet.

Følgende oplysninger vises for hver meddelelse:

- **Meddelelser**: Navnet på meddelelsen.
- **Sprog**: Hvis meddelelsen indeholder flere oversættelser, vises de første to sprog direkte. Hvis du vil se de resterende sprog, skal du holde markøren over det numeriske ikon (f.eks. **+10**).
- **Type**: Værdien er **Simuleringsmeddelelse** eller **Meddelelse om positivt resultat**.
- **Kilde**: For indbyggede meddelelser er værdien **Global**. For brugerdefinerede meddelelser er værdien **Lejer**.
- **Status**
- **Sammenkædede simuleringer**
- **Oprettet af**: Ved indbyggede meddelelser er værdien **Microsoft**. For brugerdefinerede beskeder er værdien UPN for den bruger, der oprettede meddelelsen.
- **Tidspunkt for oprettelse**
- **Ændret af**
- **Klokkeslæt for seneste ændring**

Hvis du vil finde en meddelelse på listen, skal du bruge ![ikonet Søg.](../../media/m365-cc-sc-search-icon.png) **Søgefelt** til at finde navnet på meddelelsen.

Hvis du vil gruppere meddelelserne efter type, skal du klikke på ![Gruppeikon.](../../media/m365-cc-sc-group-icon.png) **Gruppen,** og vælg derefter **Meddelelsestype**. Hvis du vil opdele gruppen i meddelelserne, skal du **vælge Ingen**.

Klik på **Filterikon på** fanen Lejerbeskeder ![.](../../media/m365-cc-sc-filter-icon.png) for at filtrere meddelelser efter et eller flere sprog.

Hvis du vil fjerne en eller flere kolonner, der vises, skal du klikke på ![ikonet Tilpas kolonner.](../../media/m365-cc-sc-customize-icon.png) **Tilpas kolonner**.

Når du vælger en meddelelse på listen, vises der en pop op med oplysninger med følgende oplysninger:

- **Fanen** Eksempel: Se meddelelse. Hvis du vil have vist meddelelsen på forskellige sprog, skal du **bruge feltet Vælg** sprog.
- **Fanen** Detaljer: Få vist oplysninger om meddelelsen:
  - **Beskrivelse af meddelelse**
  - **Kilde**: For indbyggede meddelelser er værdien **Global**. For brugerdefinerede meddelelser er værdien **Lejer**.
  - **Meddelelsestype**
  - **Ændret af**
  - **Senest ændret**

## <a name="create-end-user-notifications"></a>Opret beskeder til slutbrugeren

På fanen **Lejermeddelelser** kan du klikke på ![Opret nyt ikon.](../../media/m365-cc-sc-create-icon.png) **Opret ny** for at starte den nye guide til besked til slutbrugeren.

1. På siden **Definer** detaljer**skal du konfigurere følgende indstillinger:
   - **Vælg meddelelsestype**: Meddelelse **om positivt resultat eller** **Simuleringsmeddelelse** er tilgængelige.
   - **Navn**: Angiv et entydigt navn.
   - **Beskrivelse**: Angiv en valgfri beskrivelse.

   Klik på Næste, når du er **færdig**.

2. På siden **Definer** indhold er den eneste indstilling, der er tilgængelig, **knappen Tilføj indhold på virksomhedssprog** . Når du klikker på den, **vises pop op-menuen Tilføj indhold i** standardsprog, der indeholder følgende indstillinger:
   - **Fra vist navn**
   - **Fra mailadresse**
   - **Vælg sproget for mailen**: Vælg et sprog på listen.
   - **Markér dette som standardsprog**: Da dette er det første og eneste sprog for meddelelsen, vælges denne værdi, og du kan ikke ændre den.
   - **Emne**: Standardværdien er **Tak for phish-rapportering**, men du kan ændre den.
   - **Importér mail**: Du kan eventuelt klikke på denne knap og derefter klikke på **Vælg fil for** at importere en eksisterende meddelelsesfil i almindelig tekst.
   - Området Mailindhold: Der er to tilgængelige faner:
     - **Fanen Tekst** : Der kan oprettes en RTF-editor til at oprette din meddelelsesmail. Ud over de typiske skrifttype- og formateringsindstillinger er følgende indstillinger tilgængelige:
       - **Dynamisk mærke**: Vælg mellem følgende mærker:
         - **Indsæt fornavn**
         - **Indsæt efternavn**
         - **Indsæt UPN**
         - **Indsæt mailadresse**
         - **Indsæt nyttedata**
     - **Fanen** Kode: Du kan få vist og redigere HTML-koden direkte.

   Du kan få vist resultaterne ved at klikke **på knappen** Vis mail øverst på siden.

   Klik på **Gem**, når du er færdig.

   Du kommer tilbage til siden **Definer indhold** , hvor meddelelsen, som du lige har oprettet, opsummeres med følgende oplysninger:

   - **Sprog**
   - **Emne**
   - **Kategori**
   - **Handlinger**: Der findes følgende ikoner:
     - ![Ikonet Rediger.](../../media/m365-cc-sc-edit-icon.png) **Rediger**
     - ![Ikonet Vis.](../../media/m365-cc-sc-view-icon.png) **Vis**
     - ![Ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) **Slet**: Hvis meddelelsen kun er en sprogversion, kan du ikke slette den.

   Hvis du vil tilføje en version af meddelelsen på et andet sprog, skal du klikke ![på Ikonet Tilføj oversættelse](../../media/m365-cc-sc-create-icon.png). I pop **op-menuen** Tilføj oversættelse, der vises, er de samme indstillinger tilgængelige som  i pop op-dialogboksen Tilføj indhold i standardsprog, der er blevet beskrevet tidligere. Den eneste forskel er, at du kan **vælge Markér dette som standardsprog** i yderligere oversættelser.

   Når du er færdig, skal du klikke på **Gem**

   Du kan gentage disse trin så mange gange, som det er nødvendigt, for at oprette oversatte versioner af meddelelsen på de 12 understøttede sprog.

   Når du er færdig, skal du klikke på **Næste**

3. På siden **Gennemse** meddelelse kan du gennemse oplysningerne om din meddelelse.

   Du kan vælge **Rediger** i hver sektion for at ændre indstillingerne i sektionen. Eller du kan klikke **på** Tilbage eller vælge den bestemte side i guiden.

   Klik på Send, når du er **færdig**.

   På siden **Ny simuleringsmeddelelse** , der er oprettet, kan du bruge linkene til at oprette en ny meddelelse, starte en simulering eller få vist alle meddelelser.

   Klik på Udført, når du er **færdig**.

Tilbage på fanen **Lejermeddelelser er** den meddelelse, du oprettede, nu liste.

Når du vælger en meddelelse, er følgende yderligere indstillinger tilgængelige:

Du kommer tilbage til siden med meddelelsen  om positive, hvor den meddelelse, du lige har oprettet, nu vises på **listen Vælg en positiv** meddelelse.

- Hvis du vil ændre meddelelsen eller tilføje flere oversættelser, skal du markere meddelelsen og derefter klikke på ![ikonet Rediger.](../../media/m365-cc-sc-edit-icon.png) **Rediger meddelelse** for at starte meddelelsesguiden som beskrevet tidligere (med de fleste værdier allerede udfyldt). Hvis meddelelsen allerede indeholder oversættelser for de 12 understøttede sprog, kan du ikke tilføje flere oversættelser.

- Hvis du vil oprette en kopi af en meddelelse, skal du markere den og derefter klikke på ![Ikonet Opret en kopi.](../../media/m365-cc-sc-copy-icon.png).

- Hvis du vil slette en meddelelse, skal du markere den og derefter klikke på ![Ikonet Slet.](../../media/m365-cc-sc-delete-icon.png).

## <a name="related-links"></a>Relaterede links

[Kom i gang med at bruge simuleringskursus til angreb](attack-simulation-training-get-started.md)

[Opret en simulering af phishingangreb](attack-simulation-training.md)

[Simulerings automatisering til simulering af angreb](attack-simulation-training-simulation-automations.md)
