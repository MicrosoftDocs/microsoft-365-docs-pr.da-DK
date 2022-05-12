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
description: Få mere at vide om, hvordan du bruger Microsoft Teams til at oprette din kontraktadministrationskanal ved hjælp af en Microsoft 365 løsning.
ms.openlocfilehash: 6020b6e57af285e96c7998454dc46e5eb19bc5f9
ms.sourcegitcommit: 344a254ca268a2f65cf199d9158a47e08861ffa5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/12/2022
ms.locfileid: "65368039"
---
# <a name="step-2-use-microsoft-teams-to-create-your-contract-management-channel"></a>Trin 2. Brug Microsoft Teams til at oprette din kontraktadministrationskanal

Når din organisation konfigurerer en løsning til administration af kontrakter, har du brug for en central placering, hvor interessenter kan gennemse og administrere kontrakter. Til dette formål kan du bruge [Microsoft Teams](/microsoftteams/) til at konfigurere en Teams kanal og bruge funktionerne i Teams til at:

- **Opret en placering for interessenter, så de nemt kan se alle kontrakter, der kræver handling.** I Teams kan du f.eks. oprette fanen **Kontrakter** i kanalen Kontraktstyring, hvor medlemmer kan se en nyttig feltvisning af alle kontrakter, der skal godkendes. Du kan også konfigurere visningen, så hvert "kort" viser de vigtige data, du interesserer dig for (f.eks *. klient*, *underleverandør* og *gebyrbeløb*).

     ![Fanen Kontrakter.](../media/content-understanding/tile-view.png)

- **Hav en placering, hvor medlemmer kan interagere med hinanden og se vigtige begivenheder.** I Teams kan fanen **Indlæg** f.eks. bruges til at føre samtaler, hente opdateringer og se handlinger (f.eks. et medlem, der afviser en kontrakt). Når der er sket noget (f.eks. en ny kontrakt, der er sendt til godkendelse), kan fanen **Indlæg** ikke kun bruges til at annoncere den, men også til at registrere den. Og hvis medlemmer abonnerer på meddelelser, får de besked, når der er en opdatering.

     ![Fanen Indlæg.](../media/content-understanding/posts.png)

- **Har en placering, hvor medlemmer kan se godkendte kontrakter for at vide, hvornår de kan sendes til betaling.** I SharePoint skal du oprette en liste **til betaling** og inkludere kolonner for **Klient**, **Entreprenør** og **Gebyr og** vælge **Enkelt tekstlinje** som kolonnetype. Du skal tilføje listen **Til betaling** som en Teams-fane i kanalen Kontraktstyring på samme måde, [som du gør under fanen **Kontrakter**](solution-manage-contracts-step2.md#attach-your-sharepoint-document-library-to-the-contracts-tab). Under fanen **Til betaling** vises alle kontrakter, der skal sendes til betaling. Du kan nemt udvide denne løsning for i stedet at skrive disse oplysninger direkte til et finansielt program fra tredjepart (f.eks. Dynamics CRM). 


## <a name="attach-your-sharepoint-document-library-to-the-contracts-tab"></a>Vedhæft dit SharePoint dokumentbibliotek til fanen Kontrakter

Når du har oprettet fanen **Kontrakter** i kanalen Styring af kontrakter, skal du [vedhæfte dit SharePoint dokumentbibliotek til den](https://support.microsoft.com/office/add-a-sharepoint-page-list-or-document-library-as-a-tab-in-teams-131edef1-455f-4c67-a8ce-efa2ebf25f0b). Det SharePoint dokumentbibliotek, du vil vedhæfte, er det dokumentbibliotek, hvor du anvendte din SharePoint Syntex model til dokumentforståelse i det forrige afsnit.

Når du har vedhæftet det SharePoint dokumentbibliotek, kan du få vist alle klassificerede kontrakter via en standardlistevisning.

   ![Listevisning af SharePoint bibliotek.](../media/content-understanding/list-view.png)

## <a name="customize-your-contracts-tab-tile-view"></a>Tilpas feltvisningen under fanen Kontrakter

> [!NOTE]
> Dette afsnit henviser til kodeeksempler, der findes i filen [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) , som er inkluderet i [lageret Contracts Management Solution Assets](https://github.com/pnp/syntex-samples/tree/main/scenario%20samples/Contracts%20Management).

Mens Teams giver dig mulighed for at få vist dine kontrakter i en feltvisning, kan det være en god idé at tilpasse den, så den får vist de kontraktdata, du vil gøre synlige på kontraktkortet. For fanen **Kontrakter** er det f.eks. vigtigt, at medlemmerne ser klienten, underleverandøren og gebyrbeløbet på kontraktkortet. Alle disse felter blev udtrukket fra hver kontrakt via din SharePoint Syntex model, der blev anvendt på dokumentbiblioteket. Du vil også kunne ændre feltoverskriftslinjen til forskellige farver for hver status, så medlemmerne nemt kan se, hvor kontrakten er i godkendelsesprocessen. Alle godkendte kontrakter har f.eks. en blå overskriftslinje.

   ![Feltvisning af SharePoint bibliotek.](../media/content-understanding/tile.png)

Den brugerdefinerede feltvisning, du bruger, kræver, at du foretager ændringer i den JSON-fil, der bruges til at formatere den aktuelle feltvisning. Du kan referere til den JSON-fil, der bruges til at oprette kortvisningen, ved at se på filen [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) . I følgende afsnit kan du se specifikke afsnit i koden for de funktioner, der findes på kontraktkortene.

Hvis du vil se eller foretage ændringer af JSON-koden for din visning i din Teams kanal, skal du vælge rullemenuen vis i den Teams kanal og derefter vælge **Formatér aktuel visning**.

   ![Skærmbillede af json-format i Teams kanal.](../media/content-understanding/jason-format.png)

## <a name="card-size-and-shape"></a>Kortstørrelse og -form

I filen [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) skal du se følgende afsnit for at se koden for, hvordan kortets størrelse og form er formateret.

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

Med følgende kode kan du definere status for hvert titelkort. Bemærk, at hver statusværdi (*Ny*, *Gennemse*, *Godkendt* og *Afvist*) viser forskellige farvekode for hver enkelt. I filen [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) skal du se på det afsnit, der definerer status.

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

Hvert kontraktkort viser tre felter, der blev udtrukket for hver kontrakt (*klient*, *entreprenør* og *gebyrbeløb*). Derudover vil du også have vist det klokkeslæt/den dato, hvor filen blev klassificeret af den SharePoint Syntex model, der bruges til at identificere den.

I filen [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) definerer følgende afsnit hver af disse.

### <a name="client"></a>Klient

Dette afsnit definerer, hvordan "Klient" vises på kortet, og bruger værdien for den specifikke kontrakt.

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

### <a name="contractor"></a>Entreprenør

Dette afsnit definerer, hvordan "Contractor" vises på kortet, og bruger værdien for den specifikke kontrakt.

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

Dette afsnit definerer, hvordan "Gebyrbeløb" vises på kortet, og bruger værdien for den specifikke kontrakt.

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

Dette afsnit definerer, hvordan "Klassificering" vises på kortet, og bruger værdien for den specifikke kontrakt.

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

[Trin 3. Brug Power Automate til at oprette flowet for at behandle dine kontrakter](solution-manage-contracts-step3.md)
