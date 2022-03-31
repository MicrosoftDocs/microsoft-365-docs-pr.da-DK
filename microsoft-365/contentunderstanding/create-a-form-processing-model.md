---
title: Opret en formularbehandlingsmodel i Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom: admindeeplinkSPO
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du opretter en formularbehandlingsmodel SharePoint Syntex.
ms.openlocfilehash: 6048eabe8bb57da40d940923e313bd496ec1ecec
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63601536"
---
# <a name="create-a-form-processing-model-in-microsoft-sharepoint-syntex"></a>Opret en formularbehandlingsmodel i Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GnhN]  

</br>

Ved [hjælp af AI Builder](/ai-builder/overview) – en funktion i Microsoft Power Apps – kan SharePoint Syntex oprette en [formularbehandlingsmodel](form-processing-overview.md) direkte fra et SharePoint-dokumentbibliotek. 

Oprettelse af en formularbehandlingsmodel indebærer følgende trin:

 - [Trin 1: Oprette en formularbehandlingsmodel](create-a-form-processing-model.md#step-1-create-a-form-processing-model)
 - [Trin 2: Tilføj og analysér dokumenter](create-a-form-processing-model.md#step-2-add-and-analyze-documents)
 - [Trin 3: Mærke felter og tabeller](create-a-form-processing-model.md#step-3-tag-fields-and-tables)
 - [Trin 4: Træn og publicer din model](create-a-form-processing-model.md#step-4-train-and-publish-your-model)
 - [Trin 5: Brug din model](create-a-form-processing-model.md#step-5-use-your-model)

## <a name="requirements"></a>Krav

Du kan kun oprette en formularbehandlingsmodel i SharePoint dokumentbiblioteker, hvor den er aktiveret. Hvis formularbehandling er aktiveret, kan du se **AutomateAI** >  **BuilderOprette** >  en model for at behandle **formularmenuen** i dit dokumentbibliotek. Hvis du skal have behandling aktiveret på dit dokumentbibliotek, skal du kontakte din SharePoint administrator.

 ![Skærmbillede, der viser AI Builder-modellen.](../media/content-understanding/create-ai-builder-model2.png)

## <a name="step-1-create-a-form-processing-model"></a>Trin 1: Oprette en formularbehandlingsmodel

Det første trin i oprettelsen af en formularbehandlingsmodel er at navngive modellen, definere den nye indholdstype og oprette en ny dokumentbiblioteksvisning til den.

1. I dokumentbiblioteket skal du vælge **menuen Automatiser** , vælge **AI Builder** og derefter vælge Opret **en model til at behandle formularer**.

    ![Skærmbillede, der viser menuen Automatiser og indstillingen Opret en model til at behandle formularer.](../media/content-understanding/create-ai-builder-model2.png)

2. I panelet **Opret en model til behandling af** formularer i **feltet Navn skal** du skrive et navn til modellen (f.eks *. Indkøbsordrer*).

    ![Skærmbillede, der viser panelet Opret en model til behandling af formularer.](../media/content-understanding/new-form-model2.png) 

3. Nu kan du automatisk udtrække og gemme oplysninger fra en  samling af strukturerede filer, der deler et lignende layout – f.eks. fakturaer eller skattedokumenter – som findes i et SharePoint-dokumentbibliotek. Dette gør det muligt at skrive flere modeller i en enkelt model og udtrække specifikke oplysninger om tabelelementet.

   Navnet på samlingen gemmes i en dedikeret kolonne i dokumentbiblioteket, hvor modellen anvendes, så du kan skelne mellem forskellige fillayout, der behandles af den samme model.

   Desuden gemmes de udpakkede tabeloplysninger på en bestemt liste og knyttes til den uploadede fil til nem visning eller til yderligere automatisering af forretningsprocesser.

   Sådan udtrækkes tabeloplysninger til en tilknyttet liste:<br><br>

     1. I sektionen **Udtræk oplysninger fra tabeller?** skal du vælge **Ja**.

      ![Skærmbillede, der viser sektionen Udtræk oplysninger fra tabeller i panelet Opret en model til behandling af formularer.](../media/content-understanding/extract-info-from-tables.png) 

     2. I sektionen **Hvor skal vi gemme tabeloplysninger?** skal du gøre følgende:
 
        - Hvis du vælger **En ny liste** (standardindstillingen), angives der automatisk et foreslået navn i **feltet Nyt listenavn** . Du kan ændre navnet, hvis du vil. Hvis du vil vise listen i webstedsnavigationen, skal du markere **afkrydsningsfeltet Vis i webstedsnavigation** .

        - Hvis du vælger **En eksisterende liste**, skal du **vælge den** liste, du vil bruge, på listen Markeret.

4. Når du opretter en formularbehandlingsmodel, opretter du en ny SharePoint indholdstype. En SharePoint indholdstype repræsenterer en kategori af dokumenter, der har fælles karakteristika og deler en samling af kolonner eller metadataegenskaber for det pågældende indhold. SharePoint indholdstyper administreres <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">via SharePoint Administration</a>.

   Hvis du vil knytte denne model til en eksisterende indholdstype i SharePoint indholdstyper, skal du vælge **Avancerede indstillinger**.

    ![Skærmbillede, der viser avancerede indstillinger i panelet Opret en model til behandling af formularer.](../media/content-understanding/new-form-model-advanced-settings.png) 

   1. I <a href="https://go.microsoft.com/fwlink/?linkid=2185074" target="_blank">galleriet Indholdstype skal</a> du vælge, om du vil oprette en ny indholdstype eller bruge en eksisterende. 

   2. Hvis du vil bruge en eksisterende indholdstype, **skal du vælge** Vælg en og vælge en indholdstype på listen.

   3. Din model opretter en ny visning i dit dokumentbibliotek til dine udtrukne data. Hvis det ikke skal være standardvisningen, skal du fjerne markeringen i afkrydsningsfeltet Angiv visningen som standard i **sektionen Biblioteksvisning** **for denne model**.

   4. Hvis du vil anvende et opbevaringsnavn på dine filer, **skal du vælge** den opbevaringsmærkat, du vil bruge, i sektionen Opbevaringsnavn.

5. Vælg **Opret**.

## <a name="step-2-add-and-analyze-documents"></a>Trin 2: Tilføj og analysér dokumenter

Når du har oprettet din nye formularbehandlingsmodel, åbner browseren en ny side Power Apps AI Builder-formularbehandlingsmodel. På denne side kan du tilføje og analysere dine eksempeldokumenter. 

> [!NOTE]
> Når du søger efter f.eks. filer, der skal bruges, skal du se [krav til inputdokument for formularbehandlingsmodel og tip til optimering](/ai-builder/form-processing-model-requirements). 
 
1. Du skal først definere de felter og tabeller, du vil lære din model at udtrække, på **siden Vælg oplysninger, der skal udtrækkes** . Hvis du vil have en detaljeret vejledning, skal [du se definere felter og tabeller, der skal udtrækkes](/ai-builder/create-form-processing-model#define-fields-and-tables-to-extract). 

2.  Du kan oprette lige så mange samlinger af dokumentlayout, som du vil have din model til at behandle. Hvis du vil have en detaljeret vejledning, [skal du se under Gruppere dokumenter efter samlinger](/ai-builder/create-form-processing-model#group-documents-by-collections). 

3. Når du har oprettet dine samlinger og tilføjet eksempelfilerne for hver, undersøger AI Builder de overførte dokumenter for at registrere felterne og tabellerne. Dette tager normalt et par minutter. Når analysen er fuldført, kan du fortsætte med at mærke dokumenterne.

## <a name="step-3-tag-fields-and-tables"></a>Trin 3: Mærke felter og tabeller

Du skal mærke dokumenterne for at lære modellen at forstå de felter og tabeldata, du vil udtrække. Hvis du vil have en detaljeret vejledning, skal [du se under Mærke dokumenter](/ai-builder/create-form-processing-model#tag-documents).

## <a name="step-4-train-and-publish-your-model"></a>Trin 4: Træn og publicer din model

1. Når du har oprettet og trænet din model, er du klar til at publicere den og bruge den SharePoint. Hvis du vil have en detaljeret vejledning, [skal du se under Træne og publicere din formularbehandlingsmodel](/ai-builder/form-processing-train). 

2. Når modellen er publiceret, skal **du vælge Brug model** og derefter vælge **Opret flow**. Dette opretter en Power Automate, der kan køre i dit SharePoint-dokumentbibliotek, og som udtrækker de felter, der er blevet identificeret i modellen.

    ![Skærmbillede i AI Builder, der viser Opret et flowpanel.](../media/content-understanding/ai-builder-create-a-flow.png)
 
3. Når det er fuldført, får du vist meddelelsen: *Dit flow blev oprettet*.

    ![Skærmbillede i AI Builder, der viser, at flowet blev oprettet.](../media/content-understanding/ai-builder-flow-created.png)

4. Vælg knappen **Gå til SharePoint** for at få vist dokumentbiblioteket opdateret med din model.

## <a name="step-5-use-your-model"></a>Trin 5: Brug din model

1. Bemærk, at de felter, du har valgt, nu vises som kolonner i visningen Dokumentbiblioteksmodel.

    ![Model for dokumentbibliotek anvendt.](../media/content-understanding/doc-lib-view.png)

2. Bemærk, at oplysningslinket ud **for Dokumentnoter** henviser til, at der anvendes en model for behandling af formularer på dette dokumentbibliotek.

    ![Knappen Oplysninger.](../media/content-understanding/info-button.png)  

3. Upload filer til dit dokumentbibliotek. Alle filer, som modellen identificerer som dens indholdstype, viser filerne i din visning og viser de udpakkede data i kolonnerne.

    ![Udført.](../media/content-understanding/doc-lib-done.png) 

> [!NOTE]
> Hvis der anvendes en brugerdefineret formularbehandlingsmodel og dokumentforståelsesmodel på det samme bibliotek, klassificeres filen ved hjælp af dokumentforståelsesmodellen og eventuelle uddannede udtræk for den pågældende model. Hvis der er tomme kolonner, der svarer til formularbehandlingsmodellen, udfyldes kolonnerne ved hjælp af de udtrukne værdier.

### <a name="use-flows-to-extract-information"></a>Brug flows til at udtrække oplysninger

Der er to tilgængelige flow, som kan behandle en valgt fil eller batch af filer i et bibliotek, hvor der er anvendt en formularbehandlingsmodel.

- **Udtræk oplysninger fra en billed** - eller PDF-fil med en formularbehandlingsmodel – Bruges til at udtrække tekst fra et valgt billede eller en PDF-fil ved at køre en formularbehandlingsmodel. Understøtter en enkelt markeret fil ad gangen og understøtter kun PDF-filer og billedfiler (PNG, JPG og JPEG). For at køre flowet skal du vælge en fil og derefter **vælge AutomateExtract** >  **info**.

    ![Skærmbillede, der viser menuen Automatiser med Udtræk oplysninger fremhævet.](../media/content-understanding/automate-extract-info.png)  

- **Udtræk oplysninger fra filer med en formularbehandlingsmodel** – Bruges med modeller til behandling af formular til at læse og udtrække oplysninger fra en batch af filer. Behandler op til 5.000 SharePoint filer ad gangen. Når du kører dette flow, er der visse parametre, du kan angive. Du kan:

    - Vælg, om du vil medtage filer, der tidligere er blevet behandlet (standardindstillingen er ikke at medtage filer, der tidligere er blevet behandlet).
    - Vælg det antal filer, der skal behandles (standarden er 100 filer).
    - Angiv den rækkefølge, hvori filerne skal behandles (valgmulighederne er efter fil-id, filnavn, tidspunkt for filens oprettelse eller tidspunkt for seneste ændring).
    - Angiv, hvordan rækkefølgen skal sorteres (stigende eller faldende rækkefølge).

    ![Skærmbillede, der viser panelet Kør flow med parameterindstillinger fremhævet.](../media/content-understanding/run-flow-panel.png)  

### <a name="classification-date-field"></a>Feltet Klassificeringsdato

Når en SharePoint Syntex formularbehandlingsmodel (eller en dokumentforståelsesmodel) anvendes på et dokumentbibliotek, medtages feltet  Klassificeringsdato i biblioteksskemaet. Dette felt er som standard tomt. Men når dokumenter behandles og klassificeres efter en model, opdateres dette felt med et dato-tidsstempel for færdiggørelse. 

Når en model er stemplet med klassificeringsdatoen **, kan** du bruge Send en mail, når **SharePoint Syntex** behandler et filflow for at give brugerne besked om, at en ny fil er blevet behandlet og klassificeret af en model i SharePoint-dokumentbiblioteket.

Sådan kører du flowet:

1. Vælg en fil, og vælg derefter **Integrer** >  **Power Automate** >  **Oprette et flow**.

2. I Opret **et flowpanel skal** du vælge **Send en mail, når SharePoint Syntex behandler en fil**.

    ![Skærmbillede, der viser indstillingen Opret et flowpanel og flow fremhævet.](../media/content-understanding/integrate-create-flow.png) 

## <a name="see-also"></a>Se også
  
[Power Automate dokumentation](/power-automate/)

[Kursus: Forbedr virksomhedens ydeevne med AI Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)