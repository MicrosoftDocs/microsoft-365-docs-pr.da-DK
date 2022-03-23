---
title: Anvend en dokumentforståelsesmodel i Microsoft SharePoint Syntex
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
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du anvender en publiceret model SharePoint et dokumentbibliotek i Microsoft SharePoint Syntex.
ms.openlocfilehash: 0edb87faacc3518179b8bd1a4d41d7e3834394c3
ms.sourcegitcommit: 9f0e84835121ce6228fdc69182c24be7ad1cb20e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2022
ms.locfileid: "63591533"
---
# <a name="apply-a-document-understanding-model-in-microsoft-sharepoint-syntex"></a>Anvend en dokumentforståelsesmodel i Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSoL]

</br>

Når du har publicere dokumentets forståelsesmodel, kan du anvende den på en eller flere SharePoint dokumentbiblioteker i din Microsoft 365 lejer.

> [!NOTE]
> Du kan kun anvende modellen på dokumentbiblioteker, som du har adgang til.


## <a name="apply-your-model-to-a-document-library"></a>Anvend din model på et dokumentbibliotek

Sådan anvender du din model på et SharePoint dokumentbibliotek:

1. På modellens startside skal du **vælge Anvend** model i feltet Anvend model på **biblioteker**. Eller i sektionen **Hvor modellen anvendes skal du** vælge **+Tilføj bibliotek**.

    ![Skærmbillede af sektionen Hvor modellen anvendes med indstillingen Tilføj bibliotek fremhævet.](../media/content-understanding/apply-to-library.png)

2. Du kan derefter vælge det SharePoint, der indeholder det dokumentbibliotek, du vil anvende modellen på. Hvis webstedet ikke vises på listen, kan du bruge søgefeltet til at finde det.

    ![Vælg et websted.](../media/content-understanding/site-search.png)

    > [!NOTE]
    > Du skal have *tilladelse til* at administrere liste *eller redigere* rettigheder til det dokumentbibliotek, du anvender modellen på.

3. Når du har valgt webstedet, skal du vælge det dokumentbibliotek, som du vil anvende modellen på. I eksemplet skal du vælge *dokumentdokumentbiblioteket* Dokumenter fra *webstedet Contoso-sagssporing* .

    ![Vælg et dokumentbibliotek.](../media/content-understanding/select-doc-library.png)

4. Da modellen er knyttet til en indholdstype, tilføjer den indholdstypen og opdaterer standardvisningen med de etiketter, du udtrækker, og vises som kolonner, når du anvender den på biblioteket. Du kan dog **vælge Avancerede indstillinger** for eventuelt at bevare den aktuelle biblioteksvisning eller at bruge en ny visning med modeloplysninger og filminiaturer. Hvis du vælger at beholde den aktuelle biblioteksvisning, er de nye visninger med modeloplysninger stadig tilgængelige under bibliotekets visningsmenu.

    ![Skærmbillede af avancerede indstillinger, der viser biblioteksvisningerne.](../media/content-understanding/library-view.png)

    Du kan finde flere oplysninger [i Ændre visningen i et dokumentbibliotek](#change-the-view-in-a-document-library) senere i denne artikel.

5. Vælg **Tilføj** for at anvende modellen på biblioteket.

6. På modellens startside skal du i **sektionen Hvor modellen anvendes** kunne se navnet på det websted, SharePoint på listen.

7. Gå til dit dokumentbibliotek, og sørg for, at du er i modellens dokumentbiblioteksvisning. Vælg **AutomateView** >  **dokumentforståelse af modeller**.

8. På siden **Gennemse modeller og anvend nye** skal du vælge fanen **Anvendt** for at få vist de modeller, der anvendes til dokumentbiblioteket.

    ![Skærmbillede, der viser fanen Anvendt valgt og de anvendte modeller.](../media/content-understanding/applied-models.png) 

9. Vælg **Vis modeldetaljer** for at få vist oplysninger om en model, f.eks. en beskrivelse af modellen, hvem der har publiceret modellen, og hvis modellen anvender opbevarings- eller følsomhedsmærkater på de filer, den klassificerer.

Når du har anvendt modellen på dokumentbiblioteket, kan du begynde at overføre dokumenter til webstedet og se resultaterne.

Modellen identificerer filer og mapper med modellens tilknyttede indholdstype og viser dem i din visning. Hvis modellen har nogen udtræk, viser visningen kolonner for de data, du udtrækker fra hver enkelt fil eller mappe.

> [!NOTE]
> Hvis der anvendes to eller flere dokumentforståelsesmodeller i det samme bibliotek, klassificeres den uploadede fil ved hjælp af den model, der har det højeste gennemsnitlige tillidsresultat. De udtrukne enheder vil kun være fra den anvendte model. <br><br>Hvis der anvendes en brugerdefineret formularbehandlingsmodel og dokumentforståelsesmodel på det samme bibliotek, klassificeres filen ved hjælp af dokumentforståelsesmodellen og eventuelle uddannede udtræk for den pågældende model. Hvis der er tomme kolonner, der svarer til formularbehandlingsmodellen, udfyldes kolonnerne ved hjælp af de udtrukne værdier.

## <a name="sync-changes-to-one-or-more-libraries"></a>Synkroniser ændringer til et eller flere biblioteker

Når du publicerer en model til flere dokumentbiblioteker og derefter opdaterer modellen, f.eks. at tilføje eller fjerne en extractor, skal du skubbe opdateringen til alle de biblioteker, som modellen er blevet anvendt.

Sådan synkroniserer du ændringer til alle anvendte biblioteker:

1. På modellens startside skal du i **sektionen Hvor modellen anvendes** vælge **Synkroniser alle**.

    ![Skærmbillede, der viser sektionen Hvor modellen anvendes, og knappen Synkroniser alle fremhævet.](../media/content-understanding/sync-all-button.png) 

Sådan synkroniserer du ændringer til ét eller kun udvalgte biblioteker:

1. På modellens startside skal du i **sektionen Hvor modellen** anvendes vælge det eller de biblioteker, du vil anvende ændringerne på.

2. Vælg **Synkroniser**.

    ![Skærmbillede, der viser sektionen Hvor modellen anvendes, og knappen Synkroniser fremhævet.](../media/content-understanding/sync-button.png) 

## <a name="apply-the-model-to-files-and-folder-content-already-in-the-document-library"></a>Anvend modellen på filer og mappeindhold, der allerede findes i dokumentbiblioteket

Mens en anvendt model behandler alle filer og mappeindhold, der er overført til dokumentbiblioteket, efter den er anvendt, kan du også gøre følgende for at køre modellen på filer og mappeindhold, der allerede findes i dokumentbiblioteket, før den model, der anvendes:

1. I dit dokumentbibliotek skal du vælge de filer og mapper, der skal behandles af din model.

2. Når du har valgt dine filer og mapper, **vises Klassificer** og udtræk på båndet i dokumentbiblioteket. Vælg **Klassificer og udtræk**.

      ![Skærmbillede, der viser indstillingen Klassificer og udtræk.](../media/content-understanding/extract-classify.png) 

3. De filer og mapper, du har valgt, føjes til den kø, der skal behandles.

    > [!NOTE]
    > Du modtager en meddelelse om, hvor lang tid klassificeringen kan tage. Hvis du kun har valgt filer, kan klassificeringen tage op til 30 minutter. Hvis du har valgt en eller flere mapper, kan klassificeringen tage op til 24 timer.

### <a name="classification-date-field"></a>Feltet Klassificeringsdato

Når der SharePoint Syntex et dokuments forståelsesmodel (eller en formularbehandlingsmodel) til et dokumentbibliotek, medtages feltet Klassificeringsdato i biblioteksskemaet. Dette felt er som standard tomt. Men når dokumenter behandles og klassificeres efter en model, opdateres dette felt med et dato-tidsstempel for færdiggørelse. 

   ![Skærmbillede af et dokumentbibliotek, der viser kolonnen Klassificeringsdato.](../media/content-understanding/class-date-column.png) 

Feltet **Klassificeringsdato** bruges af udløseren Når [](/connectors/sharepointonline/#when-a-file-is-classified-by-a-content-understanding-model) en fil er klassificeret af en indholdsforståelsesmodel til at køre et Power Automate-flow, når en model er færdig med at behandle indholdet af en fil eller mappe, og  den har opdateret feltet Klassificeringsdato.

   ![Flow udløser.](../media/content-understanding/trigger.png)

**Udløseren Når en fil er** klassificeret af en indholdsforståelsesmodel, kan derefter bruges til at starte et flow ved hjælp af eventuelle udpakkede oplysninger fra filen eller mappen.

Som et eksempel kan du bruge Send en mail, når **SharePoint Syntex** behandler et filflow **, når** en model er blevet stemplet med Klassificeringsdato, til at give brugerne besked om, at en ny fil er blevet behandlet og klassificeret af en model i SharePoint-dokumentbiblioteket.

Sådan kører du flowet:

1. Vælg en fil, og vælg derefter **Integrer** >  **Power Automate** >  **Oprette et flow**.

2. I Opret **et flowpanel skal** du vælge **Send en mail, når SharePoint Syntex behandler en fil**.

    ![Skærmbillede, der viser indstillingen Opret et flowpanel og flow fremhævet.](../media/content-understanding/integrate-create-flow.png) 

## <a name="change-the-view-in-a-document-library"></a>Ændre visningen i et dokumentbibliotek

Der er flere måder at få vist, hvordan du kan se oplysningerne i SharePoint dokumentbibliotek. Du kan ændre visningen i dit dokumentbibliotek, så den passer til dine behov eller præferencer.

Hvis du vil ændre visningen på bibliotekssiden, skal du vælge rullemenuen for visning for at få vist indstillingerne og derefter vælge den visning, du vil bruge.

   ![Skærmbillede af en rullemenu for visning, der viser visningsindstillingerne.](../media/content-understanding/document-library-view-menu.png) 

Hvis du f.eks **. vælger Felter** på listen, vises siden som vist.

   ![Skærmbillede af et dokumentbibliotek, der viser visningen Felter.](../media/content-understanding/document-library-tiles-view.png) 

Visningen **Felter viser** op til otte brugeroprettede felter. Hvis der er færre end otte, vises op til fire systemgenererede felter: Følsomhed (hvis det er tilgængeligt), Opbevaring (hvis det er tilgængeligt), Indholdstype, Dato for ændring, Ændret af og Klassificeringsdato.

Hvis du vil redigere en aktuel visning, skal du vælge Rediger aktuel visning **i rullemenuen visning**.

## <a name="see-also"></a>Se også

[Opret en klassificering](create-a-classifier.md)

[Opret en extractor](create-an-extractor.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)
