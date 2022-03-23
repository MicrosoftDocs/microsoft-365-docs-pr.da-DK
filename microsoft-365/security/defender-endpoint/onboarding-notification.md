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
ms.openlocfilehash: 36713496b5885866dd21a3402dcfe66b4af5b76e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63593423"
---
# <a name="create-a-notification-rule-when-a-local-onboarding-or-offboarding-script-is-used"></a>Opret en meddelelsesregel, når der bruges et lokalt onboarding- eller offboarding-script

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

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

    ![Billede af flow.](images/new-flow.png)

3. Opbyg et planlagt flow.
   1. Angiv et flownavn.
   2. Angiv start- og klokkeslæt.
   3. Angiv hyppigheden. For eksempel hvert 5. minut.

    ![Billede af meddelelsesflowet.](images/build-flow.png)

4. Vælg knappen + for at tilføje en ny handling. Den nye handling bliver en HTTP-anmodning til Defender for Endpoint Security Center-enheden(e) API'en.. Du kan også erstatte den med "WDATP-forbindelse" (handling: "Maskiner – Hent liste over maskiner").

    ![Billede af gentagelse og tilføj handling.](images/recurrence-add.png)

5. Angiv følgende HTTP-felter:

   - Metode: "HENT" som en værdi for at få listen over enheder.
   - URI: Enter `https://api.securitycenter.microsoft.com/api/machines`.
   - Godkendelse: Vælg "Active Directory OAuth".
   - Lejer: Log på, og https://portal.azure.com naviger til Azure Active Directory > **appregistrering og** få værdien for Lejer-id.
   - Målgruppe: `https://securitycenter.onmicrosoft.com/windowsatpservice\`
   - Klient-id: Log på, og https://portal.azure.com naviger til **Azure Active Directory > appregistrering og** få værdien klient-id.
   - Legitimationstype: Vælg "Hemmelig".
   - Hemmelig: Log på, og naviger https://portal.azure.com til **Azure Active Directory >-appregistreringerne**, og få værdien lejer-id.

    ![Billede af HTTP-betingelserne.](images/http-conditions.png)

6. Tilføj et nyt trin ved at vælge **Tilføj ny handling,** søg derefter efter **Datahandlinger** , og **vælg Parse JSON**.

    ![Billede af datahandlinger.](images/data-operations.png)

7. Tilføj brødtekst i **feltet** Indhold.

    ![Billede af fortolkning af JSON.](images/parse-json.png)

8. Vælg linket **Brug eksempel på nyttedata til at generere skema** .

    ![Billede af parse json med nyttedata.](images/parse-json-schema.png)

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

    ![Billede af anvend på hver enkelt.](images/flow-apply.png)

    ![Billede af anvend på hver med Hent elementer.](images/apply-to-each.png)

11. Under **Betingelse** skal du tilføje følgende udtryk: "længde(brødtekst('Get_items')?[' værdi'])" og angive betingelsen til lig med 0.

    ![Billede af anvend på hver betingelse.](images/apply-to-each-value.png)
    ![ Billede af betingelse1.](images/conditions-2.png)
    ![ Billede af betingelse2.](images/condition3.png)
    ![ Billede af Send mail.](images/send-email.png)

## <a name="alert-notification"></a>Meddelelse om besked

Følgende billede er et eksempel på en mailmeddelelse.

![Billede af meddelelse via mail.](images/alert-notification.png)

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
