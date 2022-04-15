---
title: Anvend en model til dokumentforståelse i Microsoft SharePoint Syntex
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
description: Få mere at vide om, hvordan du anvender en publiceret model på et SharePoint dokumentbibliotek i Microsoft SharePoint Syntex.
ms.openlocfilehash: a3c1ca971853234bb4b203d8b1b3e40aec7c1d7d
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882390"
---
# <a name="apply-a-document-understanding-model-in-microsoft-sharepoint-syntex"></a>Anvend en model til dokumentforståelse i Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSoL]

</br>

Når du har udgivet din model til dokumentforståelse, kan du anvende den på et eller flere SharePoint dokumentbiblioteker i din Microsoft 365 lejer.

> [!NOTE]
> Du kan kun anvende modellen på dokumentbiblioteker, som du har adgang til.


## <a name="apply-your-model-to-a-document-library"></a>Anvend din model på et dokumentbibliotek

Sådan anvender du din model på et SharePoint dokumentbibliotek:

1. På modellens startside skal du på feltet **Anvend model på biblioteker** vælge **Anvend model**. Du kan også vælge **+Tilføj bibliotek** i afsnittet **Hvor modellen anvendes**.

    ![Skærmbillede af sektionen Hvor modellen anvendes med indstillingen Tilføj bibliotek fremhævet.](../media/content-understanding/apply-to-library.png)

2. Du kan derefter vælge det SharePoint websted, der indeholder det dokumentbibliotek, du vil anvende modellen på. Hvis webstedet ikke vises på listen, kan du bruge søgefeltet til at finde det.

    ![Vælg et websted.](../media/content-understanding/site-search.png)

    > [!NOTE]
    > Du skal have *tilladelserne Administrer liste* eller *Rediger* til det dokumentbibliotek, du anvender modellen på.

3. Når du har valgt webstedet, skal du vælge det dokumentbibliotek, du vil anvende modellen på. I eksemplet skal du vælge dokumentbiblioteket *Dokumenter* på webstedet *Contoso-sagssporing* .

    ![Vælg et dokumentbibliotek.](../media/content-understanding/select-doc-library.png)

4. Da modellen er knyttet til en indholdstype, tilføjer den indholdstypen og opdaterer standardvisningen med de etiketter, du udtrækkede, og viser den som kolonner, når du anvender den på biblioteket. Du kan dog vælge **Avancerede indstillinger** for eventuelt at vælge at bevare den aktuelle biblioteksvisning eller at bruge en ny visning med modeloplysninger og filminiaturer. Hvis du vælger at beholde den aktuelle biblioteksvisning, er de nye visninger med modeloplysninger stadig tilgængelige i bibliotekets visningsmenu.

    ![Skærmbillede af avancerede indstillinger, der viser biblioteksvisningerne.](../media/content-understanding/library-view.png)

    Du kan få flere oplysninger under [Skift visningen i et dokumentbibliotek](#change-the-view-in-a-document-library) senere i denne artikel.

5. Vælg **Tilføj** for at anvende modellen på biblioteket.

6. På modellens startside i afsnittet **Hvor modellen anvendes** kan du se navnet på det SharePoint websted, der er angivet.

7. Gå til dokumentbiblioteket, og sørg for, at du er i modellens dokumentbiblioteksvisning. Vælg **AutomateView-dokumentforståelse** >  af modeller.

8. På siden **Gennemse modeller og anvend nye** skal du vælge fanen **Anvendt** for at se de modeller, der er anvendt på dokumentbiblioteket.

    ![Skærmbillede, der viser fanen Anvendt valgt og de anvendte modeller.](../media/content-understanding/applied-models.png) 

9. Vælg **Vis modeldetaljer** for at få vist oplysninger om en model, f.eks. en beskrivelse af modellen, hvem der har publiceret modellen, og om modellen anvender opbevarings- eller følsomhedsmærkater på de filer, den klassificerer.

Når du har anvendt modellen på dokumentbiblioteket, kan du begynde at overføre dokumenter til webstedet og se resultaterne.

Modellen identificerer alle filer og mapper med modellens tilknyttede indholdstype og viser dem i visningen. Hvis din model har udtrækninger, vises der kolonner for de data, du udtrækker fra hver fil eller mappe, i visningen.

> [!NOTE]
> Hvis to eller flere modeller til dokumentforståelse anvendes på det samme bibliotek, klassificeres den overførte fil ved hjælp af den model, der har den højeste gennemsnitlige konfidensscore. De udtrukne enheder kommer kun fra den anvendte model. <br><br>Hvis der anvendes en model til behandling af en brugerdefineret formular og en model til dokumentforståelse for det samme bibliotek, klassificeres filen ved hjælp af modellen til dokumentforståelse og eventuelle oplærte udtrækninger for den pågældende model. Hvis der er tomme kolonner, der svarer til formularens behandlingsmodel, udfyldes kolonnerne med disse udtrukne værdier.

## <a name="sync-changes-to-one-or-more-libraries"></a>Synkroniser ændringer i et eller flere biblioteker

Når du publicerer en model til flere dokumentbiblioteker og derefter opdaterer modellen, f.eks. tilføjelse eller fjernelse af en udtrækningsmaskine, skal du pushoverføre opdateringen til alle de biblioteker, som modellen er anvendt på.

Sådan synkroniserer du ændringer i alle anvendte biblioteker:

1. Vælg **Synkroniser alle** i sektionen **Hvor modellen anvendes** på modellens startside.

    ![Skærmbillede, der viser sektionen Hvor modellen anvendes og knappen Synkroniser alle fremhævet.](../media/content-understanding/sync-all-button.png) 

Sådan synkroniserer du ændringer i et eller kun valgte biblioteker:

1. På modellens startside skal du i afsnittet **Hvor modellen anvendes** vælge det eller de biblioteker, du vil anvende ændringerne på.

2. Vælg **Synkroniser**.

    ![Skærmbillede, der viser sektionen Hvor modellen anvendes og knappen Synkroniser fremhævet.](../media/content-understanding/sync-button.png) 

## <a name="apply-the-model-to-files-and-folder-content-already-in-the-document-library"></a>Anvend modellen på filer og mappeindhold, der allerede findes i dokumentbiblioteket

Mens en anvendt model behandler alt fil- og mappeindhold, der er overført til dokumentbiblioteket, når det er anvendt, kan du også gøre følgende for at køre modellen på filer og mappeindhold, der allerede findes i dokumentbiblioteket, før modellen anvendes:

1. Vælg de filer og mapper, du vil behandle af din model, i dokumentbiblioteket.

2. Når du har valgt dine filer og mapper, vises **Klassificer og udpak** på båndet i dokumentbiblioteket. Vælg **Klassificer og udtræk**.

      ![Skærmbillede, der viser indstillingen Klassificer og udtræk.](../media/content-understanding/extract-classify.png) 

3. De filer og mapper, du har valgt, føjes til den kø, der skal behandles.

    > [!NOTE]
    > Du modtager en meddelelse, der angiver, hvor lang tid klassificeringen kan tage. Hvis du kun har valgt filer, kan klassificering tage op til 30 minutter. Hvis du har valgt en eller flere mapper, kan klassificering tage op til 24 timer.

### <a name="classification-date-field"></a>Feltet Klassificeringsdato

Når der anvendes en SharePoint Syntex model til dokumentforståelse (eller en formularbehandlingsmodel) på et dokumentbibliotek, medtages feltet **Klassificeringsdato** i biblioteksskemaet. Dette felt er som standard tomt. Når dokumenter behandles og klassificeres af en model, opdateres dette felt dog med et dato/klokkeslætsstempel for færdiggørelse. 

   ![Skærmbillede af et dokumentbibliotek, der viser kolonnen Klassificeringsdato.](../media/content-understanding/class-date-column.png) 

Feltet **Klassificeringsdato** bruges af udløseren [**Når en fil klassificeres af en model til forståelse af indhold**](/connectors/sharepointonline/#when-a-file-is-classified-by-a-content-understanding-model) til at køre et Power Automate flow, når en model er færdig med at behandle indholdet af en fil eller mappe og har opdateret feltet **Klassificeringsdato**.

   ![Flow udløser.](../media/content-understanding/trigger.png)

Udløseren **Når en fil klassificeres af en model, der forstår indhold** , kan derefter bruges til at starte et flow ved hjælp af eventuelle udpakkede oplysninger fra filen eller mappen.

Når en model stemples med **klassificeringsdatoen**, kan du f.eks. bruge **Send en mail, når SharePoint Syntex behandler et filflow**, til at give brugerne besked om, at en ny fil er blevet behandlet og klassificeret af en model i SharePoint dokumentbibliotek.

Sådan kører du flowet:

1. Vælg en fil, og vælg derefter **Integrer** >  **Power Automate** >  **Opret et flow**.

2. På panelet **Opret et flow** skal du vælge **Send en mail, når SharePoint Syntex behandler en fil**.

    ![Skærmbillede, der viser indstillingen Opret et flowpanel og flow fremhævet.](../media/content-understanding/integrate-create-flow.png) 

## <a name="change-the-view-in-a-document-library"></a>Skift visningen i et dokumentbibliotek

[!INCLUDE [Change the view in a document library](../includes/change-library-view.md)]

## <a name="see-also"></a>Se også

[Opret en klassificering](create-a-classifier.md)

[Opret en udtrækningsmaskine](create-an-extractor.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)
