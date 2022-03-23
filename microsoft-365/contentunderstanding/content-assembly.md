---
title: Opret dokumenter ved hjælp af indholdssamling i Microsoft SharePoint Syntex
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
description: Lær, hvordan du automatisk kan oprette dokumenter og andet indhold ved hjælp af samling af indhold i Microsoft SharePoint Syntex.
ms.openlocfilehash: 9da2aa91443ffe1dd3bbd632b5284ce8f7622069
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/15/2022
ms.locfileid: "63593066"
---
# <a name="create-documents-using-content-assembly-in-microsoft-sharepoint-syntex"></a>Opret dokumenter ved hjælp af indholdssamling i Microsoft SharePoint Syntex

Du kan bruge SharePoint Syntex som en hjælp til automatisk at generere almindelige gentagne forretningsdokumenter, f.eks. kontrakter, arbejdsopgørelser, serviceaftaler, samtykkebreve, salgstale og korrespondance. Du kan gøre alt dette hurtigere, mere ensartet og mindre tilbøjelig til fejl ved at bruge samling af indhold i SharePoint Syntex.

Med indholdssamling kan du bruge et eksisterende dokument til at oprette en moderne *skabelon og derefter* bruge denne skabelon til automatisk at generere nyt indhold ved hjælp af SharePoint-lister eller brugerinput som datakilde.

> [!NOTE]
> Du skal være licenseret til SharePoint Syntex at få adgang til og bruge egenskaber for indholdssamling. Du skal også have tilladelse til at administrere SharePoint lister.

## <a name="create-a-modern-template"></a>Opret en moderne skabelon

Følg disse trin for at oprette en moderne skabelon.

1. Vælg NyOprette moderne skabelon fra **et** >  **Sharepoint-dokumentbibliotek**. 
 
   ![Skærmbillede af dokumentbibliotek med indstillingen Opret moderne skabelon fremhævet.](../media/content-understanding/content-assembly-create-template-1.png)

2. Vælg et eksisterende Word-dokument, du vil bruge som grundlag for oprettelse af en moderne skabelon, og vælg derefter **Åbn**. 
 
   ![Skærmbillede af overførselsside, hvor du vælger et dokument.](../media/content-understanding/content-assembly-create-template-2.png)

   > [!NOTE]
   > Du kan i øjeblikket kun overføre Word-dokumenter (.docx udvidelse) for at oprette skabeloner. Upload Word-dokumenter fra dit lokale lager eller skrivebord.

3. Når du uploader dokumentet, vises dokumentet i skabelonstudiet, hvor du kan konvertere dokumentet til en skabelon.
 
   ![Skærmbillede af dokumentet i skabelonvisningen.](../media/content-understanding/content-assembly-create-template-3.png)

4. Vælg navnet på skabelonen i øverste venstre hjørne af skabelonstudiet. Standardnavnet er navnet på det dokument, der blev brugt til at oprette skabelonen. Hvis du vil omdøbe skabelonen, skal du vælge standardnavnet eller blyantsikonet ud for navnet, skrive det nye navn og derefter vælge **Enter**.
 
   ![Skærmbillede af skabelonvisningen, der viser navnet på det dokument, du vil vælge for at omdøbe.](../media/content-understanding/content-assembly-create-template-3a.png)

5. Opret pladsholdere for al dynamisk tekst i dokumentet, som brugerne muligvis vil ændre fra ét dokument til et andet. Det kan f.eks. være, at du vil oprette en pladsholder for input, f.eks. firmanavn, kundenavn, adresse, telefonnummer eller dato.

    Hvis du vil oprette en pladsholder, skal du markere teksten (f.eks. datoen). Panelet **Alle pladsholdere** åbnes, hvor du giver pladsholderen et relevant navn og vælger den type input, du vil knytte til pladsholderen.
 
   ![Skærmbillede af skabelonvisningen, der viser et fremhævet felt og panelet Alle pladsholdere.](../media/content-understanding/content-assembly-create-template-4a.png)

   Brugere kan i øjeblikket udfylde en pladsholder på to måder:

   - [Skriv teksten, eller vælg en dato](#associate-a-placeholder-by-entering-text-or-selecting-a-date)
   - [Vælge mellem valgmuligheder i en kolonne på en liste eller i et bibliotek](#associate-a-placeholder-by-selecting-from-choices-in-a-column-of-a-list-or-library)

   > [!NOTE]
   > Du kan kun oprette pladsholdere til tekst. Aktuelt understøttes billeder, smartart, tabeller og punktopstillinger ikke.   

### <a name="associate-a-placeholder-by-entering-text-or-selecting-a-date"></a>Tilknytte en pladsholder ved at indtaste tekst eller vælge en dato 

På **panelet Alle pladsholdere** :

1. Angiv et **relevant** navn til pladsholderen i feltet Navn.

   ![Skærmbillede af skabelonvisningen, der viser panelet Alle pladsholdere for manuelt input.](../media/content-understanding/content-assembly-create-template-5.png)

2. I sektionen **Hvordan forfattere udfylder denne pladsholder** skal du **vælge Skriv tekst eller vælge en dato**.

3. Vælg **den datatype** , du vil knytte til pladsholderen, i feltet Type af oplysninger. Der er i øjeblikket seks tilgængelige **indstillinger: Enkelt** tekstlinje **, Flere** tekstlinjer **, Tal**, Dato og **klokkeslæt****, Mail** og **Link**.

4. Vælg **Tilføj**.

### <a name="associate-a-placeholder-by-selecting-from-choices-in-a-column-of-a-list-or-library"></a>Tilknyt en pladsholder ved at vælge mellem valgmuligheder i en kolonne på en liste eller i et bibliotek

På **panelet Alle pladsholdere** :

1. Angiv et **relevant** navn til pladsholderen i feltet Navn.

   ![Skærmbillede af skabelonvisningen, der viser panelet Alle pladsholdere til input fra SharePoint liste.](../media/content-understanding/content-assembly-create-template-6.png)

2. I sektionen **Hvordan forfattere udfylder denne pladsholder** skal du vælge **Vælg** mellem valgmuligheder i en kolonne på en liste eller i et bibliotek og derefter vælge **Vælg**.

3. Vælg den **liste, du vil bruge, på listen** Vælg en liste for at tilføje en kildekolonne, og vælg derefter **Næste**.

   ![Skærmbillede af siden Vælg en liste til tilføjelse af en kildekolonne med lister.](../media/content-understanding/content-assembly-create-template-7.png)

4. På siden **Vælg en kildekolonne** på den eksisterende liste skal du vælge det kolonnenavn, du vil knytte til pladsholderen, og derefter vælge **Gem**. 

   ![Skærmbillede af vælg en kildekolonne fra den eksisterende listeside, der viser kolonnenavne.](../media/content-understanding/content-assembly-create-template-8.png)

    Hvis du vil se den oprindelige side med lister igen, skal du vælge linket Gå til (listenavn **)** nederst på listen.

5. Når du er færdig, kan du se, at listefeltet er knyttet til pladsholderen.

   ![Skærmbillede af panelet Alle pladsholdere, der viser det listefelt, der er knyttet til pladsholderen.](../media/content-understanding/content-assembly-create-template-9.png)

6. Hvis brugerne skal kunne tilføje input manuelt, skal du ud over at vælge fra en liste vælge Tillad forfattere **at tilføje nye valgmuligheder**. I dette tilfælde er standardindstillingen for den manuelle indtastning *datatype Enkelt tekstlinje*. Desuden bruges inputværdierne fra forfatterne kun til at generere dokumentet. De føjes ikke til listen SharePoint kontakter.
 
Du kan oprette lige så mange pladsholdere, som du mener er nødvendige. Når du er færdig, kan du vælge at gemme skabelonen som en kladde eller publicere skabelonen.

   - **Gem kladde** – Gemmer skabelonen som en kladde, så du kan få adgang til den senere. Du kan få vist, redigere eller publicere gemte kladder fra  sektionen Moderne skabeloner ved at vælge **menuen** >  **NyRedigering Ny** i dokumentbiblioteket. 
   - **Publicer** – Publicerer den skabelon, der skal bruges af andre brugere i organisationen til at oprette dokumenter. Du kan få vist, redigere eller annullere publicerede  skabeloner fra sektionen Moderne  skabeloner ved at vælge **menuen** >  **NyRedigering Ny** i dokumentbiblioteket. 

## <a name="edit-a-modern-template"></a>Rediger en moderne skabelon

Hvis du vil redigere en eksisterende skabelon eller slette eller annullere publiceringen af en skabelon, skal du følge disse trin.

1. Fra et Sharepoint-dokumentbibliotek skal du **vælge NyEdit** >  **Ny menu**. 
 
   ![Skærmbillede af dokumentbibliotek med menuindstillingen Rediger ny fremhævet.](../media/content-understanding/content-assembly-edit-template-1.png)

2. På **menupanelet Rediger ny i** sektionen Moderne skabeloner **skal du vælge** den publicerede skabelon eller den kladdeskabelon, du vil redigere.
 
   ![Skærmbillede af menupanelet Rediger ny, der viser sektionen Moderne skabeloner.](../media/content-understanding/content-assembly-edit-template-2.png)

3. Sådan redigerer du en publiceret skabelon eller en kladdeskabelon:

   - For **Publicerede skabeloner** skal du  **vælgeRedigeringfor**  at åbne skabelonstudiet, hvor du kan redigere den publicerede skabelon. Du kan også vælge at slette eller annullere publiceringen af skabelonen. 
 
      ![Skærmbillede af afsnittet Moderne skabeloner, der viser de publicerede skabeloner.](../media/content-understanding/content-assembly-edit-published.png)

   - For **Kladdeskabeloner** skal du  **vælgeRedigeringfor**  at åbne skabelonstudiet, hvor du kan redigere kladdeskabelonen. Du kan også vælge at slette eller publicere skabelonen.
 
      ![Skærmbillede af afsnittet Moderne skabeloner, der viser kladdeskabelonerne.](../media/content-understanding/content-assembly-edit-draft.png)

## <a name="create-a-document-from-a-modern-template"></a>Opret et dokument ud fra en moderne skabelon

Du kan bruge en *publiceret* , moderne skabelon til hurtigt at oprette lignende dokumenter uden at skulle starte fra bunden. Hvis du vil oprette et dokument ud fra en publiceret skabelon, skal du følge disse trin:

1. Fra et Sharepoint-dokumentbibliotek skal **du vælge** Ny og derefter vælge den moderne skabelon, du vil bruge.
 
   ![Skærmbillede af dokumentbibliotek, der viser valgmulighederne for moderne skabeloner i menuen Ny.](../media/content-understanding/content-assembly-create-document-1.png)

2. Skabelonen åbnes i skabelonstudiet.

3. Angiv **oplysningerne i panelet Opret et dokument fra** en skabelon, og vælg derefter **Opret dokument**.

   ![Skærmbillede af dokumentbibliotek, der viser panelet Opret et dokument fra en skabelon.](../media/content-understanding/content-assembly-create-document-2.png)

   Hvis du vil reducere tids- og indsatstiden ved udfyldning af værdier for pladsholdere, SharePoint Syntex følgende:

      - Forslag, der gør det nemt for dig at vælge værdier, når du vælger værdier på en liste.
      - Automatisk udfyldning af pladsholderværdier, hvis det er muligt entydigt at identificere en post for pladsholdere, der er knyttet til den samme liste.

> [!NOTE]
> - I øjeblikket er det Microsoft Word dokumenter (.docx) der understøttes til oprettelse af en skabelon. Før du uploader dokumentet, skal du sikre dig, at Der ikke er aktiveret **Registrer ændringer** eller kommentarer i Word-dokumentet. Hvis dokumentet indeholder pladsholdere til tekst til billeder, skal du sikre dig, at de ikke er ombrudt tekst. Vi understøtter ikke **indholdskontrolelementer** i Word i øjeblikket. Hvis du vil oprette en skabelon ud fra et Word-dokument med indholdskontrolelementer, skal du fjerne dem, før du opretter en moderne skabelon.
>- Skabelonen og dokumentet er knyttet til ét dokumentbibliotek. Hvis du vil bruge skabelonen i et andet dokumentbibliotek, skal du oprette skabelonen igen i det pågældende dokumentbibliotek.
>- Det uploadede dokument, der bruges til at oprette den moderne skabelon, gemmes som en separat kopi og placeres i dokumentbiblioteks /forms-mappe. Den oprindelige fil på disken påvirkes ikke.
>- Du kan kun oprette pladsholdere til tekst. Aktuelt understøttes billeder, smartart, tabeller og punktopstillinger ikke.
>- Når et dokument er oprettet ud fra en skabelon, er det ikke knyttet til skabelonen.



 
