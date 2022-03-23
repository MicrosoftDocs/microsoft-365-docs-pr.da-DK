---
title: Trin 2. Brug Microsoft Teams til at oprette din kontraktadministrationskanal
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.localizationpriority: medium
ROBOTS: ''
description: Lær at bruge en Microsoft Teams at oprette din kontraktadministrationskanal ved hjælp af en Microsoft 365 løsning.
ms.openlocfilehash: a5a42bedcb6acba4caf8f6f114812c63869ee92e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63593253"
---
# <a name="step-2-use-microsoft-teams-to-create-your-contract-management-channel"></a>Trin 2. Brug Microsoft Teams til at oprette din kontraktadministrationskanal

Når din organisation opretter en løsning til administration af kontrakter, har du brug for et centralt sted, hvor interessenter kan gennemse og administrere kontrakter. Til dette formål kan du bruge [Microsoft Teams til](/microsoftteams/) at konfigurere Teams kanal og bruge funktionerne i Teams til at:

- **Opret et sted, hvor interessenter nemt kan se alle kontrakter, der kræver handling.** I en Teams kan du f.eks. oprette fanen Kontrakter  i kanalen Kontraktadministration, hvor medlemmerne kan se en nyttig feltvisning af alle kontrakter, der skal godkendes. Du kan også konfigurere visningen, så hvert "kort" viser de vigtige *data, der* er vigtige for dig (f.eks. *kunde, leverandør* *og gebyrbeløb*).

     ![Fanen Kontrakter.](../media/content-understanding/tile-view.png)

- **Have en placering, hvor medlemmerne kan interagere med hinanden og se vigtige begivenheder.** I en Teams kan fanen Indlæg f.eks.  bruges til at have samtaler, hente opdateringer og se handlinger (f.eks. et medlem, der afviser en kontrakt). Når der er sket noget (f.eks. en ny kontrakt, der  er indsendt til godkendelse), kan fanen Indlæg bruges ikke blot til at annoncere det, men også til at holde styr på det. Og hvis medlemmer abonnerer på meddelelser, får de besked, når der er en opdatering.

     ![Fanen Indlæg.](../media/content-understanding/posts.png)

- **Have et sted, hvor medlemmerne kan se godkendte kontrakter for at vide, hvornår de kan sendes til betaling.** I SharePoint skal du oprette en liste til udbetaling og medtage kolonner **for** beløb af typen **Klient, Leverandør** og **Gebyr ved at** vælge Enkelt tekstlinje som kolonnetype.  Du skal tilføje listen til udbetaling som  en Teams-fane i kanalen Kontraktadministration, svarende til det, du skal [gøre under **fanen** Kontrakter](solution-manage-contracts-step2.md#attach-your-sharepoint-document-library-to-the-contracts-tab). Fanen **Til udbetaling** viser alle kontrakter, der skal sendes til betaling. Du kan nemt udvide denne løsning for i stedet at skrive disse oplysninger direkte til et finansielt program fra en tredjepart (f.eks. Dynamics CRM). 


## <a name="attach-your-sharepoint-document-library-to-the-contracts-tab"></a>Vedhæft SharePoint dokumentbibliotek til fanen Kontrakter

Når du har oprettet **fanen** Kontrakter i kanalen Administration af kontrakter, skal du [vedhæfte SharePoint dokumentbiblioteket til den](https://support.microsoft.com/office/add-a-sharepoint-page-list-or-document-library-as-a-tab-in-teams-131edef1-455f-4c67-a8ce-efa2ebf25f0b). Det SharePoint dokumentbibliotek, du vil vedhæfte, er det dokumentbibliotek, hvor du har anvendt SharePoint Syntex dokumentforståelsesmodel i det forrige afsnit.

Når du vedhæfter SharePoint dokumentbibliotek, kan du få vist alle klassificerede kontrakter via en standardlistevisning.

   ![Listevisning af SharePoint bibliotek.](../media/content-understanding/list-view.png)

## <a name="customize-your-contracts-tab-tile-view"></a>Tilpas feltvisningen under fanen Kontrakter

> [!NOTE]
> Dette afsnit henviser til kodeekseler, der er indeholdt i filen [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) , der er inkluderet i lagerlageret for [løsningsaktiver til kontraktstyring](https://github.com/pnp/syntex-samples/tree/main/scenario%20assets/Contracts%20Management).

Mens Teams kan du se dine kontrakter i en feltvisning, kan det være en god ide at tilpasse dem for at få vist de kontraktdata, du vil gøre synlige på kontraktkortet. For fanen Kontrakter er **det f.eks** . vigtigt, at medlemmerne får vist klienten, entreprenøren og gebyrbeløbet på kontraktkortet. Alle disse felter er hentet fra hver kontrakt via din SharePoint Syntex, der blev anvendt til dit dokumentbibliotek. Du vil også kunne ændre feltoverskriftslinjen til forskellige farver for hver status, så medlemmerne nemt kan se, hvor kontrakten er i godkendelsesprocessen. Alle godkendte kontrakter har f.eks. en blå overskriftslinje.

   ![Visning af felter SharePoint biblioteket.](../media/content-understanding/tile.png)

Den brugerdefinerede feltvisning kræver, at du foretager ændringer i den JSON-fil, der bruges til at formatere den aktuelle feltvisning. Du kan henvise til den JSON-fil, der bruges til at oprette kortvisningen, ved at se på filen [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) . I de følgende afsnit får du vist specifikke sektioner i koden for funktioner, der findes på kontraktkortene.

Hvis du vil se eller foretage ændringer i JSON-koden for din visning i din Teams-kanal, skal du i Teams-kanalen vælge rullemenuen Vis og derefter vælge **Formatér** aktuel visning.

   ![Skærmbillede af json-format i Teams kanal.](../media/content-understanding/jason-format.png)

## <a name="card-size-and-shape"></a>Kortstørrelse og -figur

I filen [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) skal du se følgende afsnit for at se koden for, hvordan kortets størrelse og form formateres.

```JSON
                  {
                    "elmType": "div",
                    "style": {
                      "background-color": "#f5f5f5",
                      "padding": "5px",
                      "width": "180px"
                    },
                    "children": [
                      {
                        "elmType": "img",
                        "attributes": {
                          "src": "@thumbnail.large"
                        },
                        "style": {
                          "width": "185px",
                          "height": "248px"
                        }
                      }
```

## <a name="contract-status"></a>Kontraktstatus

Følgende kode gør det muligt at definere status for hvert titelkort. Bemærk, at hver statusværdi (*Ny*, I *gennemsyn*, Godkendt og *Afvist) viser* forskellige farvekoder for hver. I filen [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) skal du se det afsnit, der definerer status.

```JSON
          {
            "elmType": "div",
            "children": [
              {
                "elmType": "div",
                "style": {
                  "color": "white",
                  "background-color": "=if([$Status] == 'New', '#00b7c3', if([$Status] == 'In review', '#ffaa44', if([$Status] == 'Approved', '#0078d4', if([$Status] == 'Rejected', '#d13438', '#8378de'))))",
                  "padding": "5px 15px",
                  "height": "auto",
                  "text-transform": "uppercase",
                  "font-size": "12.5px"
                },
                "txtContent": "[$Status]"
              }
```

## <a name="extracted-fields"></a>Udtrukne felter

Hvert kontraktkort viser tre felter, der er udtrækket for hver kontrakt (*klient*, *leverandør* og *gebyrbeløb*). Desuden vil du også have vist det klokkeslæt/den dato, hvor filen blev klassificeret i forhold til den SharePoint Syntex, der blev brugt til at identificere den.

I filen [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) definerer de følgende afsnit hver af disse.

### <a name="client"></a>Klient

Dette afsnit definerer, hvordan "Klient" vises på kortet og bruger værdien for den specifikke kontrakt.

```JSON
                      {
                        "elmType": "div",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px"
                        },
                        "txtContent": "Client"
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "16px",
                          "font-weight": "600"
                        },
                        "txtContent": "[$Client]"
                      },
```

### <a name="contractor"></a>Leverandør

Dette afsnit definerer, hvordan "Leverandør" vises på kortet, og bruger værdien for den specifikke kontrakt.

```JSON
                        {
                          "elmType": "div",
                          "txtContent": "Contractor",
                          "style": {
                            "color": "#767676",
                            "font-size": "12px",
                            "margin-bottom": "2px"
                          }
                        },
                        {
                          "elmType": "div",
                          "style": {
                            "margin-bottom": "12px",
                            "font-size": "14px"
                          },
                          "txtContent": "[$Contractor]"
                        },
```

### <a name="fee-amount"></a>Gebyrbeløb

Dette afsnit definerer, hvordan "Gebyrbeløb" vises på kortet og bruger værdien for den specifikke kontrakt.

```JSON
                      {
                        "elmType": "div",
                        "txtContent": "Fee amount",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px",
                          "margin-bottom": "2px"
                        }
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "14px"
                        },
                        "txtContent": "[$FeeAmount]"
                      },
```

### <a name="classification-date"></a>Klassificeringsdato

Dette afsnit definerer, hvordan "Klassificering" vises på kortet og bruger værdien for den specifikke kontrakt.

```JSON
                      {
                        "elmType": "div",
                        "txtContent": "Classified",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px",
                          "margin-bottom": "2px"
                        }
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "14px"
                        },
                        "txtContent": "[$PrimeLastClassified]"
                      }
```

## <a name="next-step"></a>Næste trin

[Trin 3. Brug Power Automate til at oprette flowet til at behandle dine kontrakter](solution-manage-contracts-step3.md)
