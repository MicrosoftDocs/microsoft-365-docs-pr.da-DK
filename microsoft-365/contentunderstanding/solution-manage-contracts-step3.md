---
title: Trin 3. Brug Power Automate til at oprette flowet til at behandle dine kontrakter
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
description: Lær at bruge Power Automate til at oprette dit flow til at behandle dine kontrakter ved hjælp af en Microsoft 365 løsning.
ms.openlocfilehash: d83fb6e5ca911cbafc6f064c615ab15ae0f570c7
ms.sourcegitcommit: f3c912780bbcf5a5b47de192202adb3afbd5952b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/26/2022
ms.locfileid: "63597929"
---
# <a name="step-3-use-power-automate-to-create-the-flow-to-process-your-contracts"></a>Trin 3. Brug Power Automate til at oprette flowet til at behandle dine kontrakter

Du har oprettet din kontraktadministrationskanal og har vedhæftet SharePoint dokumentbibliotek. Det næste trin er at oprette et Power Automate til at behandle dine kontrakter, som din SharePoint Syntex identificerer og klassificerer. Du kan udføre dette trin ved [at oprette Power Automate flow i dit SharePoint dokumentbibliotek](https://support.microsoft.com/office/create-a-flow-for-a-list-or-library-in-sharepoint-or-onedrive-a9c3e03b-0654-46af-a254-20252e580d01).

For din løsning til administration af kontrakter vil du oprette et Power Automate for at gøre følgende handlinger:

-  Når en kontrakt er blevet klassificeret ud fra SharePoint Syntex, skal du ændre kontraktstatus til **Til gennemgang**.
- Derefter gennemgås kontrakten, og den godkendes eller afvises.
- For godkendte kontrakter sendes kontraktoplysningerne til en fane til behandling af betalinger.
- Ved afviste kontrakter underrettes teamet til yderligere analyse. 

Følgende diagram viser Power Automate for løsningen til kontraktstyring.

![Flow diagram, der viser hele løsningen.](../media/content-understanding/flow-entire-process.png)

## <a name="prepare-your-contract-for-review"></a>Forbered din kontrakt til gennemsyn

Når en kontrakt identificeres og klassificeres ud fra SharePoint Syntex dokumentforståelsesmodel, ændrer Power Automate først status til **Under gennemgang**.

![Opdater status.](../media/content-understanding/flow-overview.png)

Når du har tjekket filen ud, skal du ændre statusværdien til **Gennemse**.

![I status for gennemsyn.](../media/content-understanding/in-review.png)

Næste trin er at oprette et tilpasset kort med en besked om, at kontrakten venter på gennemgang og offentliggørelse af den på kontraktadministrationskanalen.

![Indlæg til gennemgang af kontrakt.](../media/content-understanding/contract-approval-post.png)


![Opret tilpasset kort til gennemsyn.](../media/content-understanding/adaptive-card.png)

Følgende kode er den JSON, der bruges til dette trin i Power Automate flow.

```JSON
{
"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
"type": "AdaptiveCard",
"version": "1.0",
"body": [
    {
    "type": "TextBlock",
    "text": "Contract approval request",
    "size": "large",
    "weight": "bolder",
     "wrap": true
    },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Date created",
                            "value": "@{triggerOutputs()?['body/Modified']} "
                        },
                        {
                            "title": "Link",
                            "value": "[@{triggerOutputs()?['body/{FilenameWithExtension}']}](@{triggerOutputs()?['body/{Link}']})"
                        }
                    ]
                }
            ]
         },
    {
    "type": "TextBlock",
    "text": "Comment:"
    },
        {
            "type": "Input.Text",
            "placeholder": "Enter comments",
            "id": "acComments"
        }
],
"actions": [
    {
    "type": "Action.Submit",
    "title": "Approve",
    "data": {
        "x": "Approve"
    }
    },
    {
    "type": "Action.Submit",
    "title": "Reject",
    "data": {
        "x": "Reject"
    }
    }
]
}
```


## <a name="conditional-context"></a>Betinget kontekst

I dit flow skal du derefter oprette en betingelse, hvor din kontrakt enten  [godkendes](#if-the-contract-is-approved) [eller afvises](#if-the-contract-is-rejected).

![Betinget.](../media/content-understanding/condition.png)

## <a name="if-the-contract-is-approved"></a>Hvis kontrakten godkendes

Når en kontrakt er blevet godkendt, sker følgende:

- Under fanen **Kontrakter** ændres status på kontraktkortet til **Godkendt**.

   ![Kortstatus godkendt.](../media/content-understanding/approved-contracts-tab.png)

- I dit flow ændres status til **Godkendt**.

   ![Flow godkendt.](../media/content-understanding/status-approved.png)

- I denne løsning føjes kontraktdata til fanen **Til** betaling, så udbetalingen kan administreres. Denne proces kan forlænges for at tillade, at flowet indsende kontrakter til betaling af et finansielt program fra en tredjepart (f.eks. Dynamics CRM).

   ![Kontrakt flyttet til Betal.](../media/content-understanding/for-payout.png)

- I flowet opretter du følgende element for at flytte godkendte kontrakter til **fanen Til** betaling.

   ![Flow, der skal flyttes til Betal.](../media/content-understanding/ready-for-payout.png)

    Hvis du vil hente udtryk for de oplysninger, der skal bruges Teams visitkortet, skal du bruge værdierne, der er vist i nedenstående tabel.
 
    |Navn     |Expression |
    |---------|-----------|
    | Godkendelsestilstand  | brødtekst(Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response)? ['submitActionId']         |
    | Godkendt af     | brødtekst(Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response)? ['svarer'] ['displayName']        |
    | Godkendelsesdato     | brødtekst(Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response)? ['responseTime']         |
    | Kommenter     | brødtekst(Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response)? ['data']? ['acComments']         |
    
    I følgende eksempel vises det, hvordan du kan bruge formelfeltet i Power Automate til at skrive et udtryk.

   ![Skærmbillede i Power Automate der viser en udtryksformel.](../media/content-understanding/expression-formula-power-automate.png)    

- Et tilpasset kort, der angiver, at kontrakten er blevet godkendt, oprettes og offentliggøres på kontraktadministrationskanalen.

   ![Godkendelse af kontrakt er opslået.](../media/content-understanding/adaptive-card-approval.png)

   ![Adaptive kortgodkendelse.](../media/content-understanding/adaptive-card.png)


   Følgende kode er den JSON, der bruges til dette trin i Power Automate flow.

```JSON
{ 
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "Container",
            "style": "emphasis",
            "items": [
                {
                    "type": "ColumnSet",
                    "columns": [
                        {
                            "type": "Column",
                            "items": [
                                {
                                    "type": "TextBlock",
                                    "size": "Large",
                                    "weight": "Bolder",
                                    "text": "CONTRACT APPROVED"
                                }
                            ],
                            "width": "stretch"
                        }
                    ]
                }
            ],
            "bleed": true
        },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Approval by",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responder']['displayName']}"
                        },
                        {
                            "title": "Approved date",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responseTime']}"
                        },
                        {
                            "title": "Approval comment",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['data']?['acComments']}"
                        },
                        {
                            "title": " ",
                            "value": " "
                        },
                        {
                            "title": "Status",
                            "value": "Ready for payout"
                        }
                    ]
                }
            ]
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2",
    "fallbackText": "This card requires Adaptive Cards v1.2 support to be rendered properly."
}
```

## <a name="if-the-contract-is-rejected"></a>Hvis kontrakten afvises

Når en kontrakt er blevet afvist, sker følgende:

- Under fanen **Kontrakter** ændres status på kontraktkortet til **Afvist**.

   ![Kortstatus afvist.](../media/content-understanding/rejected-contracts-tab.png)

- I dit flow kan du tjekke kontraktfilen ud, ændre status til **Afvist og derefter** tjekke filen ind igen.

   ![Flow status afvist i kontraktfilen.](../media/content-understanding/reject-flow.png)

- I dit flow opretter du et tilpasset kort med en besked om, at kontrakten er blevet afvist.

   ![Flow viser afvist på adaptive kort.](../media/content-understanding/reject-flow-item.png)

Følgende kode er den JSON, der bruges til dette trin i Power Automate flow.

```JSON
{ 
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "Container",
            "style": "attention",
            "items": [
                {
                    "type": "ColumnSet",
                    "columns": [
                        {
                            "type": "Column",
                            "items": [
                                {
                                    "type": "TextBlock",
                                    "size": "Large",
                                    "weight": "Bolder",
                                    "text": "CONTRACT REJECTED"
                                }
                            ],
                            "width": "stretch"
                        }
                    ]
                }
            ],
            "bleed": true
        },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Rejected by",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responder']['displayName']}"
                        },
                        {
                            "title": "Rejected date",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responseTime']}"
                        },
                        {
                            "title": "Comment",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['data']?['acComments']}"
                        },
                        {
                            "title": " ",
                            "value": " "
                        },
                        {
                            "title": "Status",
                            "value": "Needs review"
                        }
                    ]
                }
            ]
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2",
    "fallbackText": "This card requires Adaptive Cards v1.2 support to be rendered properly."
}
```

- Kortet er slået op i kanalen Kontraktadministration.

   ![Flow tilpasset kort til afvisning.](../media/content-understanding/rejected.png)
