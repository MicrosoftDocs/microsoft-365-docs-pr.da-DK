---
title: Opret dokumenter ved hjælp af indholdsassembly i Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.reviewer: anrasto
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du automatisk opretter dokumenter og andet indhold ved hjælp af indholdsassemblyen i Microsoft SharePoint Syntex.
ms.openlocfilehash: 906118458688d40c392cc9333357f1b8c946910b
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823206"
---
# <a name="create-documents-using-content-assembly-in-microsoft-sharepoint-syntex"></a>Opret dokumenter ved hjælp af indholdsassembly i Microsoft SharePoint Syntex

Du kan bruge SharePoint Syntex til at hjælpe dig med automatisk at generere gentagne standardforretningsdokumenter, f.eks. kontrakter, arbejdsopgørelser, serviceaftaler, samtykkebreve, salgspladser og korrespondance. Du kan gøre alt dette hurtigere, mere konsekvent og mindre tilbøjelig til fejl ved at bruge indholdsassembly i SharePoint Syntex.

Med indholdsassemblyen kan du bruge et eksisterende dokument til at oprette en *moderne skabelon* og derefter bruge skabelonen til automatisk at generere nyt indhold ved hjælp af SharePoint lister eller brugerinput som datakilde.

> [!NOTE]
> Du skal være en licenseret SharePoint Syntex bruger for at få adgang til og bruge funktioner til indholdsassembly. Du skal også have tilladelse til at administrere SharePoint lister.

## <a name="create-a-modern-template"></a>Opret en moderne skabelon

Følg disse trin for at oprette en moderne skabelon.

1. Vælg **NyOpret** >  **moderne skabelon** i et SharePoint-dokumentbibliotek.

   ![Skærmbillede af dokumentbiblioteket med indstillingen Opret moderne skabelon fremhævet.](../media/content-understanding/content-assembly-create-template-1.png)

2. Vælg et eksisterende Word-dokument, som du vil bruge som udgangspunkt for at oprette en moderne skabelon, og vælg derefter **Åbn**.

   ![Skærmbillede af uploadside, hvor du vælger et dokument.](../media/content-understanding/content-assembly-create-template-2.png)

   > [!NOTE]
   > I øjeblikket kan du kun overføre Word-dokumenter (.docx filtypenavn) for at oprette skabeloner. Upload Word-dokumenter fra dit lokale lager eller skrivebord.

3. Når du har uploadet dokumentet, vises dokumentet i skabelonstudiet, hvor du kan konvertere dokumentet til en skabelon.

   ![Skærmbillede af dokumentet i skabelonfremviseren.](../media/content-understanding/content-assembly-create-template-3.png)

4. Vælg navnet på skabelonen i øverste venstre hjørne af skabelonstudiet. Standardnavnet er navnet på det dokument, der bruges til at oprette skabelonen. Hvis du vil omdøbe skabelonen, skal du vælge standardnavnet eller blyantsikonet ud for navnet, skrive det nye navn og derefter vælge **Enter**.

   ![Skærmbillede af skabelonfremviseren, der viser navnet på det dokument, der skal vælges for at omdøbe.](../media/content-understanding/content-assembly-create-template-3a.png)

5. Opret pladsholdere for al dynamisk tekst i dokumentet, som brugerne måske vil ændre fra ét dokument til et andet. Det kan f.eks. være, at du vil oprette en pladsholder for input, f.eks. firmanavn, klientnavn, adresse, telefonnummer eller dato.

    Hvis du vil oprette en pladsholder, skal du markere teksten (f.eks. datoen). Panelet **Alle pladsholdere** åbnes, hvor du giver pladsholderen et relevant navn og vælger den type input, du vil knytte til pladsholderen.

   ![Skærmbillede af skabelonfremviseren, der viser et fremhævet felt og panelet Alle pladsholdere.](../media/content-understanding/content-assembly-create-template-4a.png)

   Der er i øjeblikket to måder, som brugerne kan udfylde en pladsholder på:

   - [Indtast tekst, eller markér en dato](#associate-a-placeholder-by-entering-text-or-selecting-a-date)
   - [Vælg mellem valg i en kolonne på en liste eller i et bibliotek](#associate-a-placeholder-by-selecting-from-choices-in-a-column-of-a-list-or-library)

   > [!NOTE]
   > Du kan kun oprette pladsholdere for tekst. I øjeblikket understøttes billeder, smartart, tabeller og punktopstilling ikke.

### <a name="associate-a-placeholder-by-entering-text-or-selecting-a-date"></a>Tilknyt en pladsholder ved at indtaste tekst eller vælge en dato

På panelet **Alle pladsholdere** :

1. Angiv et relevant navn til pladsholderen i feltet **Navn** .

   ![Skærmbillede af skabelonfremviseren, der viser panelet Alle pladsholdere til manuelt input.](../media/content-understanding/content-assembly-create-template-5.png)

2. I afsnittet **Sådan udfylder forfattere denne pladsholder** skal du vælge **Angiv tekst eller vælge en dato**.

3. I feltet **Type af oplysninger** skal du vælge den datatype, du vil knytte til pladsholderen. Der er i øjeblikket seks tilgængelige indstillinger: **Enkelt tekstlinje**, **Flere tekstlinjer**, **Tal**, **Dato og klokkeslæt**, **Mail** og **Link**.

4. Vælg **Tilføj**.

### <a name="associate-a-placeholder-by-selecting-from-choices-in-a-column-of-a-list-or-library"></a>Tilknyt en pladsholder ved at vælge mellem valg i en kolonne på en liste eller i et bibliotek

På panelet **Alle pladsholdere** :

1. Angiv et relevant navn til pladsholderen i feltet **Navn** .

   ![Skærmbillede af skabelonfremviseren, der viser panelet Alle pladsholdere til input fra en SharePoint liste.](../media/content-understanding/content-assembly-create-template-6.png)

2. I afsnittet **Sådan udfylder forfattere denne pladsholder** skal du vælge **Vælg blandt valgmuligheder i en kolonne på en liste eller et bibliotek** og derefter vælge **Vælg**.

3. På siden **Vælg en liste til tilføjelse af en kildekolonne** skal du vælge den liste, du vil bruge, og derefter vælge **Næste**.

   ![Skærmbillede af siden Vælg en liste til tilføjelse af en kildekolonne, der viser lister.](../media/content-understanding/content-assembly-create-template-7.png)

4. På siden **Vælg en kildekolonne på den eksisterende liste** skal du vælge det kolonnenavn, du vil knytte til pladsholderen, og derefter vælge **Gem**.

   ![Skærmbillede af vælg en kildekolonne på den eksisterende listeside, der viser kolonnenavne.](../media/content-understanding/content-assembly-create-template-8.png)

    Hvis du vil se den oprindelige side med lister igen, skal du vælge **Gå til (listenavn)** nederst på listen.

5. Når du er færdig, kan du se, at listefeltet er knyttet til pladsholderen.

   ![Skærmbillede af panelet Alle pladsholdere, der viser det listefelt, der er knyttet til pladsholderen.](../media/content-understanding/content-assembly-create-template-9.png)

6. Hvis du ønsker, at brugerne skal kunne tilføje input manuelt, skal du ud over at vælge på en liste vælge **Tillad, at forfattere tilføjer nye valgmuligheder**. I dette tilfælde er standarden for den manuelle inputdatatype *Enkelt tekstlinje*. Værdierne fra forfatterne bruges også kun til at generere dokumentet. De føjes ikke til listen over SharePoint.

   Du kan oprette lige så mange pladsholdere, som du mener, er nødvendige. Når du er færdig, kan du vælge at gemme skabelonen som en kladde eller publicere skabelonen.

   - **Gem kladde** – gemmer skabelonen som en kladde, og du kan få adgang til den senere. Du kan få vist, redigere eller publicere gemte kladder i afsnittet **Moderne skabeloner** ved at vælge **NyRedigering** >  **ny i** dokumentbiblioteket.
   - **Publicer** – publicerer skabelonen, der skal bruges af andre brugere i organisationen til at oprette dokumenter. Du kan få vist, redigere eller annullere publicering af *publicerede* skabeloner i afsnittet **Moderne skabeloner** ved at vælge **NyRedigering** >  **ny i** dokumentbiblioteket.

## <a name="edit-a-modern-template"></a>Rediger en moderne skabelon

Hvis du har brug for at redigere en eksisterende skabelon eller slette eller annullere publiceringen af en skabelon, skal du følge disse trin.

1. Vælg **NyMenuen** >  **Ny i** et SharePoint-dokumentbibliotek.

   ![Skærmbillede af dokumentbiblioteket med menuindstillingen Rediger ny fremhævet.](../media/content-understanding/content-assembly-edit-template-1.png)

2. Vælg den publicerede eller kladdeskabelon, du vil redigere, i afsnittet **Moderne skabeloner** i **menupanelet Rediger ny**.

   ![Skærmbillede af menupanelet Rediger ny, der viser sektionen Moderne skabeloner.](../media/content-understanding/content-assembly-edit-template-2.png)

3. Sådan redigerer du en publiceret skabelon eller en kladdeskabelon:

   - For **Publicerede skabeloner** skal du vælge **Rediger** for at åbne skabelonstudiet, hvor du kan redigere den publicerede skabelon. Du kan også vælge at slette eller annullere publiceringen af skabelonen.

      ![Skærmbillede af afsnittet Moderne skabeloner, der viser de publicerede skabeloner.](../media/content-understanding/content-assembly-edit-published.png)

   - For **Kladdeskabeloner** skal du vælge **Rediger** for at åbne skabelonstudiet, hvor du kan redigere kladdeskabelonen. Du kan også vælge at slette eller udgive skabelonen.

      ![Skærmbillede af afsnittet Moderne skabeloner, der viser kladdeskabelonerne.](../media/content-understanding/content-assembly-edit-draft.png)

## <a name="create-a-document-from-a-modern-template"></a>Opret et dokument ud fra en moderne skabelon

Du kan bruge en *publiceret* moderne skabelon til hurtigt at oprette lignende dokumenter uden at skulle starte fra bunden. Følg disse trin for at oprette et dokument ved hjælp af en publiceret skabelon:

1. Vælg **Ny** i et SharePoint-dokumentbibliotek, og vælg derefter den moderne skabelon, du vil bruge.

   ![Skærmbillede af dokumentbiblioteket, der viser de moderne skabelonvalg i menuen Ny.](../media/content-understanding/content-assembly-create-document-1.png)

2. Skabelonen åbnes i skabelonstudiet.

3. Angiv oplysningerne i panelet **Opret et dokument fra en skabelon** , og vælg derefter **Opret dokument**.

   ![Skærmbillede af dokumentbiblioteket, der viser Opret et dokument fra et skabelonpanel.](../media/content-understanding/content-assembly-create-document-2.png)

   For at hjælpe med at reducere den tid og indsats, der er forbundet med at udfylde værdier for pladsholdere, giver SharePoint Syntex:

      - Forslag, der hjælper dig med nemt at vælge værdier, når du vælger værdier på en liste.
      - Autofyld pladsholderværdier, hvis det er muligt entydigt at identificere en post for pladsholdere, der er knyttet til den samme liste.

> [!NOTE]
>
> - I øjeblikket understøttes kun Microsoft Word dokumenter (.docx udvidelse) til oprettelse af en skabelon. Før du uploader dokumentet, skal du kontrollere, at **Registrering af ændringer** eller kommentarer ikke er aktiveret i Word-dokumentet. Hvis dit dokument indeholder tekstpladsholdere for billeder, skal du kontrollere, at de ikke er tekstombrudte. Vi understøtter ikke **indholdskontrolelementer** i Word i øjeblikket. Hvis du vil oprette en skabelon ud fra et Word-dokument med indholdskontrolelementer, skal du fjerne dem, før du opretter en moderne skabelon.
> - Skabelonen og dokumentet er knyttet til ét dokumentbibliotek. Hvis du vil bruge skabelonen i et andet dokumentbibliotek, skal du oprette skabelonen igen i dokumentbiblioteket.
> - Det overførte dokument, der bruges til at oprette den moderne skabelon, gemmes som en separat kopi og placeres i mappen /forms i dokumentbiblioteket. Den oprindelige fil på disken påvirkes ikke.
> - Du kan kun oprette pladsholdere for tekst. I øjeblikket understøttes billeder, smartart, tabeller og punktopstilling ikke.
> - Når et dokument er oprettet ud fra en skabelon, er det ikke knyttet til skabelonen.
