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
description: Få mere at vide om, hvordan du opretter en formularbehandlingsmodel i SharePoint Syntex.
ms.openlocfilehash: 3eb14a76bd597f1f382b87813c7e4bd2a4518e19
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882346"
---
# <a name="create-a-form-processing-model-in-microsoft-sharepoint-syntex"></a>Opret en formularbehandlingsmodel i Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GnhN]  

</br>

Brug af [AI Builder](/ai-builder/overview) – en funktion i Microsoft Power Apps – SharePoint Syntex brugere kan oprette en [formularbehandlingsmodel](form-processing-overview.md) direkte fra et SharePoint dokumentbibliotek. 

Oprettelse af en formularbehandlingsmodel omfatter følgende trin:

 - [Trin 1: Opret en formularbehandlingsmodel](create-a-form-processing-model.md#step-1-create-a-form-processing-model)
 - [Trin 2: Tilføj og analysér dokumenter](create-a-form-processing-model.md#step-2-add-and-analyze-documents)
 - [Trin 3: Mærk felter og tabeller](create-a-form-processing-model.md#step-3-tag-fields-and-tables)
 - [Trin 4: Oplær og publicer din model](create-a-form-processing-model.md#step-4-train-and-publish-your-model)
 - [Trin 5: Brug din model](create-a-form-processing-model.md#step-5-use-your-model)

## <a name="requirements"></a>Krav

Du kan kun oprette en formularbehandlingsmodel i SharePoint dokumentbiblioteker, som den er aktiveret for. Hvis formularbehandling er aktiveret, kan du se **AutomateAI** >  **BuilderOpret** >  **en model til behandling af formularmenuen** i dokumentbiblioteket. Hvis behandlingen skal være aktiveret i dokumentbiblioteket, skal du kontakte SharePoint administrator.

 ![Skærmbillede, der viser AI Builder-modellen.](../media/content-understanding/create-ai-builder-model2.png)

## <a name="step-1-create-a-form-processing-model"></a>Trin 1: Opret en formularbehandlingsmodel

Det første trin i oprettelsen af en model til formularbehandling er at navngive modellen, definere den nye indholdstype og oprette en ny dokumentbiblioteksvisning til den.

1. Vælg menuen **Automate** i dokumentbiblioteket, vælg **AI Builder**, og vælg derefter **Opret en model for at behandle formularer**.

    ![Skærmbillede, der viser menuen Automatiser og indstillingen Opret en model til behandling af formularer.](../media/content-understanding/create-ai-builder-model2.png)

2. Skriv et navn til din model i feltet **Navn** i panelet **Opret en model til behandling af formularer**, f.eks *. Indkøbsordrer*.

    ![Skærmbillede, der viser panelet Opret en model til behandling af formularer.](../media/content-understanding/new-form-model2.png) 

3. Du kan nu automatisk udtrække og gemme oplysninger fra en *samling* strukturerede filer, der deler et lignende layout, f.eks. fakturaer eller skattedokumenter, som findes i et SharePoint dokumentbibliotek. Det giver dig mulighed for at oprette flere modeller i en enkelt model og udtrække specifikke oplysninger om tabelelement.

   Samlingens navn gemmes i en dedikeret kolonne i det dokumentbibliotek, hvor modellen anvendes, hvilket giver dig mulighed for at skelne mellem forskellige fillayout, der behandles af den samme model.

   Desuden gemmes de udtrukne tabeloplysninger på en angivet liste og knyttes til den overførte fil for nem visning eller for yderligere automatisering af forretningsprocesser.

   Sådan udtrækkes tabeloplysninger til en tilknyttet liste:<br><br>

     1. I afsnittet **Udtræk oplysninger fra tabeller?** skal du vælge **Ja**.

      ![Skærmbillede, der viser afsnittet Udtræk oplysninger fra tabeller i panelet Opret en model til behandling af formularer.](../media/content-understanding/extract-info-from-tables.png) 

     2. I afsnittet **Hvor skal vi gemme tabeloplysninger?**
 
        - Hvis du vælger **En ny liste** (standardindstillingen), angives der automatisk et foreslået navn i feltet **Nyt listenavn** . Du kan ændre navnet, hvis du vil. Hvis du vil have vist listen i webstedsnavigationen, skal du markere afkrydsningsfeltet **Vis i webstedsnavigation** .

        - Hvis du vælger **En eksisterende liste**, skal du vælge den liste, du vil bruge, på **listen Valgt** .

4. Når du opretter en formularbehandlingsmodel, opretter du en ny SharePoint indholdstype. En SharePoint indholdstype repræsenterer en kategori af dokumenter, der har fælles egenskaber og deler en samling af kolonner eller metadataegenskaber for det pågældende indhold. SharePoint indholdstyper administreres via <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration</a>.

   Hvis du vil knytte denne model til en eksisterende indholdstype i galleriet med SharePoint indholdstyper, skal du vælge **Avancerede indstillinger**.

    ![Skærmbillede, der viser avancerede indstillinger i panelet Opret en model til behandling af formularer.](../media/content-understanding/new-form-model-advanced-settings.png) 

   1. I <a href="https://go.microsoft.com/fwlink/?linkid=2185074" target="_blank">galleriet Indholdstype</a> skal du vælge, om du vil oprette en ny indholdstype eller bruge en eksisterende. 

   2. Hvis du vil bruge en eksisterende indholdstype, skal du vælge **Vælg en** og vælge en indholdstype på listen.

   3. Din model opretter en ny visning i dokumentbiblioteket for de udtrukne data. Hvis det ikke skal være standardvisningen, skal du fjerne markeringen i afkrydsningsfeltet **Angiv visningen som standard** i sektionen **Biblioteksvisning for denne model**.

   4. Hvis du vil anvende en opbevaringsmærkat på dine filer, skal du vælge det opbevaringsmærkat, du vil bruge, i afsnittet **Opbevaringsmærkat** .

5. Vælg **Opret**.

## <a name="step-2-add-and-analyze-documents"></a>Trin 2: Tilføj og analysér dokumenter

Når du har oprettet din nye formularbehandlingsmodel, åbner browseren en ny Power Apps modelsiden til behandling af AI Builder-formularer. På denne side kan du tilføje og analysere dine eksempeldokumenter. 

> [!NOTE]
> Når du kigger efter eksempelfiler, der skal bruges, kan du se [kravene til inputdokumentet til formularbehandlingsmodellen og tip til optimering](/ai-builder/form-processing-model-requirements). 
 
1. Du skal først definere de felter og tabeller, du vil lære din model at udtrække på siden **Vælg oplysninger, der skal udtrækkes** . Du kan finde detaljerede trin under [Definer felter og tabeller, der skal udtrækkes](/ai-builder/create-form-processing-model#define-fields-and-tables-to-extract). 

2.  Du kan oprette lige så mange samlinger af dokumentlayout, som modellen skal behandle. Du kan finde detaljerede trin under [Gruppér dokumenter efter samlinger](/ai-builder/create-form-processing-model#group-documents-by-collections). 

3. Når du har oprettet dine samlinger og tilføjet eksempelfilerne for hver enkelt, undersøger AI Builder de uploadede dokumenter for at registrere felterne og tabellerne. Dette tager normalt et par minutter. Når analysen er fuldført, kan du fortsætte med at mærke dokumenterne.

## <a name="step-3-tag-fields-and-tables"></a>Trin 3: Mærk felter og tabeller

Du skal mærke dokumenterne for at lære modellen at kende for at forstå de felter og tabeldata, du vil udtrække. Du kan finde detaljerede trin under [Mærk dokumenter](/ai-builder/create-form-processing-model#tag-documents).

## <a name="step-4-train-and-publish-your-model"></a>Trin 4: Oplær og publicer din model

1. Når du har oprettet og oplært din model, er du klar til at publicere den og bruge den i SharePoint. Du kan finde detaljerede trin under [Oplær og publicer din formularbehandlingsmodel](/ai-builder/form-processing-train). 

2. Når modellen er publiceret, skal du vælge **Brug model** og derefter vælge **Opret flow**. Dette opretter et Power Automate flow, der kan køre i SharePoint dokumentbibliotek, og som udtrækker de felter, der er identificeret i modellen.

    ![Skærmbillede i AI Builder, der viser panelet Opret et flow.](../media/content-understanding/ai-builder-create-a-flow.png)
 
3. Når du er færdig, får du vist meddelelsen: *Dit flow blev oprettet*.

    ![Skærmbillede i AI Builder, der viser, at flowet blev oprettet.](../media/content-understanding/ai-builder-flow-created.png)

4. Vælg knappen **Gå til SharePoint** for at se, at dokumentbiblioteket er opdateret med din model.

## <a name="step-5-use-your-model"></a>Trin 5: Brug din model

1. Bemærk, at de valgte felter nu vises som kolonner i modelvisningen for dokumentbiblioteket.

    ![Der er anvendt en dokumentbiblioteksmodel.](../media/content-understanding/doc-lib-view.png)

2. Bemærk, at oplysningslinket ud for **Dokumenter** bemærker, at der anvendes en formularbehandlingsmodel på dette dokumentbibliotek.

    ![Knappen Oplysninger.](../media/content-understanding/info-button.png)  

3. Upload filer til dokumentbiblioteket. Alle filer, som modellen identificerer som indholdstype, viser filerne i visningen og viser de udtrukne data i kolonnerne.

    ![Gjort.](../media/content-understanding/doc-lib-done.png) 

> [!NOTE]
> Hvis der anvendes en model til behandling af en brugerdefineret formular og en model til dokumentforståelse for det samme bibliotek, klassificeres filen ved hjælp af modellen til dokumentforståelse og eventuelle oplærte udtrækninger for den pågældende model. Hvis der er tomme kolonner, der svarer til formularens behandlingsmodel, udfyldes kolonnerne med disse udtrukne værdier.

### <a name="use-flows-to-extract-information"></a>Brug flow til at udtrække oplysninger

Der er to flow tilgængelige til behandling af en valgt fil eller batch af filer i et bibliotek, hvor der er anvendt en formularbehandlingsmodel.

- **Udtræk oplysninger fra et billede eller en PDF-fil med en formularbehandlingsmodel** – Bruges til at udtrække tekst fra et markeret billede eller en PDF-fil ved at køre en formularbehandlingsmodel. Understøtter en enkelt valgt fil ad gangen og understøtter kun PDF-filer og billedfiler (PNG, JPG og JPEG). Hvis du vil køre flowet, skal du vælge en fil og derefter vælge **AutomateExtract-oplysninger** > .

    ![Skærmbillede, der viser menuen Automatiser med Udtræk oplysninger fremhævet.](../media/content-understanding/automate-extract-info.png)  

- **Udtræk oplysninger fra filer med en formularbehandlingsmodel** – Bruges sammen med modeller til formularbehandling til at læse og udtrække oplysninger fra en batch af filer. Behandler op til 5.000 SharePoint filer ad gangen. Når du kører dette flow, er der visse parametre, du kan angive. Du kan:

    - Vælg, om tidligere behandlede filer skal medtages (standarden er ikke at inkludere tidligere behandlede filer).
    - Vælg det antal filer, der skal behandles (standarden er 100 filer).
    - Angiv den rækkefølge, filerne skal behandles i (der kan vælges efter fil-id, filnavn, tidspunkt for oprettelse af fil eller tidspunkt for seneste ændring).
    - Angiv, hvordan rækkefølgen skal sorteres (stigende eller faldende rækkefølge).

    ![Skærmbillede, der viser panelet Kør flow med parameterindstillinger fremhævet.](../media/content-understanding/run-flow-panel.png)  

### <a name="classification-date-field"></a>Feltet Klassificeringsdato

Når der anvendes en SharePoint Syntex formularbehandlingsmodel (eller en model til dokumentforståelse) på et dokumentbibliotek, medtages feltet **Klassificeringsdato** i biblioteksskemaet. Dette felt er som standard tomt. Når dokumenter behandles og klassificeres af en model, opdateres dette felt dog med et dato/klokkeslætsstempel for færdiggørelse. 

Når en model stemples med **klassificeringsdatoen**, kan du bruge **Send en mail, når SharePoint Syntex behandler et filflow**, til at give brugerne besked om, at en ny fil er blevet behandlet og klassificeret af en model i SharePoint dokumentbibliotek.

Sådan kører du flowet:

1. Vælg en fil, og vælg derefter **Integrer** >  **Power Automate** >  **Opret et flow**.

2. På panelet **Opret et flow** skal du vælge **Send en mail, når SharePoint Syntex behandler en fil**.

    ![Skærmbillede, der viser indstillingen Opret et flowpanel og flow fremhævet.](../media/content-understanding/integrate-create-flow.png) 

## <a name="see-also"></a>Se også
  
[dokumentation til Power Automate](/power-automate/)

[Oplæring: Øg virksomhedens ydeevne med AI Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)