---
title: Opret en meddelelsesregel for onboarding eller offboarding
description: Få en meddelelse, når der bruges et lokalt onboarding- eller offboarding-script.
keywords: onboarding, offboarding, lokal, script, meddelelse, regel
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 0208e21394e350c2b5ffffdca6f8e14ebba227c8
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476021"
---
# <a name="create-a-notification-rule-when-a-local-onboarding-or-offboarding-script-is-used"></a>Opret en meddelelsesregel, når der bruges et lokalt onboarding- eller offboarding-script

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


Opret en meddelelsesregel, så du får besked, når der bruges et lokalt onboarding- eller offboarding-script.

## <a name="before-you-begin"></a>Før du begynder

Du skal have adgang til:

- Power Automate (minimum pr. bruger-plan). Du kan finde flere oplysninger [Power Automate siden med priser](https://flow.microsoft.com/pricing/).
- Azure Table eller SharePoint List or Library/ SQL DB.

## <a name="create-the-notification-flow"></a>Opret meddelelsesflowet

1. I [flow.microsoft.com](https://flow.microsoft.com/).

2. Gå til **Mine flow > Ny > Planlagt – fra tom**.

   :::image type="content" source="images/new-flow.png" alt-text="Flowet" lightbox="images/new-flow.png":::


3. Opbyg et planlagt flow.
   1. Angiv et flownavn.
   2. Angiv start- og klokkeslæt.
   3. Angiv hyppigheden. For eksempel hvert 5. minut.

   :::image type="content" source="images/build-flow.png" alt-text="Meddelelsesflowet" lightbox="images/build-flow.png":::

4. Vælg knappen + for at tilføje en ny handling. Den nye handling bliver en HTTP-anmodning til Defender for Endpoint Security Center-enheden(e) API'en.. Du kan også erstatte den med "WDATP-forbindelse" (handling: "Maskiner – Hent liste over maskiner").

   :::image type="content" source="images/recurrence-add.png" alt-text="Gentagelsen og tilføjelsen" lightbox="images/recurrence-add.png":::

5. Angiv følgende HTTP-felter:

   - Metode: "HENT" som en værdi for at få listen over enheder.
   - URI: Enter `https://api.securitycenter.microsoft.com/api/machines`.
   - Godkendelse: Vælg "Active Directory OAuth".
   - Lejer: Log på, og https://portal.azure.com naviger til Azure Active Directory > **appregistrering og** få værdien for Lejer-id.
   - Målgruppe: `https://securitycenter.onmicrosoft.com/windowsatpservice\`
   - Klient-id: Log på, og https://portal.azure.com naviger til **Azure Active Directory > appregistrering og** få værdien klient-id.
   - Legitimationstype: Vælg "Hemmelig".
   - Hemmelig: Log på, og naviger https://portal.azure.com til **Azure Active Directory >-appregistreringerne**, og få værdien lejer-id.

    :::image type="content" source="images/http-conditions.png" alt-text="HTTP-betingelserne" lightbox="images/http-conditions.png":::

6. Tilføj et nyt trin ved at vælge **Tilføj ny handling,** søg derefter efter **Datahandlinger** , og **vælg Parse JSON**.

   :::image type="content" source="images/data-operations.png" alt-text="Posten med datahandlinger" lightbox="images/data-operations.png":::

7. Tilføj brødtekst i **feltet** Indhold.

   :::image type="content" source="images/parse-json.png" alt-text="Afsnittet fortolke JSON" lightbox="images/parse-json.png":::

8. Vælg linket **Brug eksempel på nyttedata til at generere skema** .

   :::image type="content" source="images/parse-json-schema.png" alt-text="Parse JSON med nyttedata" lightbox="images/parse-json-schema.png":::

9. Kopiér og indsæt følgende JSON-kodestykke:

    ```json
    {
        "type": "object",
        "properties": {
            "@@odata.context": {
                "type": "string"
            },
            "value": {
                "type": "array",
                "items": {
                    "type": "object",
                    "properties": {
                        "id": {
                            "type": "string"
                        },
                        "computerDnsName": {
                            "type": "string"
                        },
                        "firstSeen": {
                            "type": "string"
                        },
                        "lastSeen": {
                            "type": "string"
                        },
                        "osPlatform": {
                            "type": "string"
                        },
                        "osVersion": {},
                        "lastIpAddress": {
                            "type": "string"
                        },
                        "lastExternalIpAddress": {
                            "type": "string"
                        },
                        "agentVersion": {
                            "type": "string"
                        },
                        "osBuild": {
                            "type": "integer"
                        },
                        "healthStatus": {
                            "type": "string"
                        },
                        "riskScore": {
                            "type": "string"
                        },
                        "exposureScore": {
                            "type": "string"
                        },
                        "aadDeviceId": {},
                        "machineTags": {
                            "type": "array"
                        }
                    },
                    "required": [
                        "id",
                        "computerDnsName",
                        "firstSeen",
                        "lastSeen",
                        "osPlatform",
                        "osVersion",
                        "lastIpAddress",
                        "lastExternalIpAddress",
                        "agentVersion",
                        "osBuild",
                        "healthStatus",
                        "rbacGroupId",
                        "rbacGroupName",
                        "riskScore",
                        "exposureScore",
                        "aadDeviceId",
                        "machineTags"
                    ]
                }
            }
        }
    }

    ```

10. Udtræk værdierne fra JSON-opkaldet, og kontrollér, om onboardede enheder er / allerede er registreret på listen SharePoint som eksempel:

    - Hvis ja, udløses der ingen meddelelse
    - Hvis nej, vil den eller de nye onboardede enheder blive registreret på SharePoint, og der sendes en meddelelse til administratoren for Defender til slutpunktet

    :::image type="content" source="images/flow-apply.png" alt-text="Anvendelse af flowet på hvert element" lightbox="images/flow-apply.png":::

    :::image type="content" source="images/apply-to-each.png" alt-text="Anvendelse af flowet på elementet Hent elementer" lightbox="images/apply-to-each.png":::

11. Under **Betingelse** skal du tilføje følgende udtryk: "længde(brødtekst('Get_items')?[' værdi'])" og angive betingelsen til lig med 0.

    :::image type="content" source="images/apply-to-each-value.png" alt-text="Anvendelse af flowet på hver betingelse" lightbox="images/apply-to-each-value.png":::
    :::image type="content" source="images/conditions-2.png" alt-text="Betingelsen-1" lightbox="images/conditions-2.png":::
    :::image type="content" source="images/condition3.png" alt-text="Betingelsen-2" lightbox="images/condition3.png":::
    :::image type="content" source="images/send-email.png" alt-text="Afsnittet Send en mail" lightbox="images/send-email.png":::

## <a name="alert-notification"></a>Meddelelse om besked

Følgende billede er et eksempel på en mailmeddelelse.

:::image type="content" source="images/alert-notification.png" alt-text="Skærmbilledet med besked om mail" lightbox="images/alert-notification.png":::

## <a name="tips"></a>Tips

- Du kan filtrere her udelukkende ved hjælp af lastSeen:
  - Hvert 60. minut:
    - Tag alle enheder, der sidst er set i de seneste 7 dage.

- For hver enhed:
  - Hvis egenskaben Senest set er på et timeinterval på [-7 dage, -7 dage + 60 minutter ] -> besked om offboarding-mulighed.
  - Hvis set første gang er på den seneste time > besked om onboarding.

I denne løsning får du ikke dublerede beskeder: Der er lejere, der har mange enheder. Det kan være meget dyrere at få alle disse enheder, og det kan kræve sideinddeling.

Du kan opdele den i to forespørgsler:

1. For offboarding tager det kun dette interval at bruge OData-$filter og kun underrette, hvis betingelserne er opfyldt.
2. Tag alle enheder, der sidst blev set i den seneste time, og kontrollér først set-egenskaben for dem (hvis den første sete egenskab er på den seneste time, skal den sidst sete også være der).
