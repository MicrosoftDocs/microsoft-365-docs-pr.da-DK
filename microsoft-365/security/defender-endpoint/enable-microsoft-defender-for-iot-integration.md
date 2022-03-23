---
title: Aktivér Microsoft Defender til IoT-integration i Microsoft Defender for Endpoint
description: Aktivér integration af Microsoft Defender til IoT for at opnå synlighed fokuseret på IoT-/OT-enheder i områder af netværket, hvor MDE ikke er installeret
keywords: aktivér siem-forbindelse, siem, forbindelse, sikkerhedsoplysninger og hændelser
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 70d8586cb8f8babcdc709a67632f32103e9420ce
ms.sourcegitcommit: 388279e10a160b85b345a8ad760f6816dda4e2ad
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/07/2021
ms.locfileid: "63593660"
---
# <a name="enable-microsoft-defender-for-iot-integration"></a>Aktivér Integration af Microsoft Defender til IoT

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender til Slutpunkt](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Microsoft Defender til Slutpunkt kan nu integreres med Microsoft Defender til IoT. Denne integration udvider dine muligheder for enhedsregistrering med de muligheder for agentløs overvågning, der leveres af Microsoft Defender til IoT. Dette er med til at sikre virksomhedens IoT-enheder, der har forbindelse til it-netværk, f.eks. VoIP-enheder (Voice over Internet Protocol), printere og kameraer. Det giver organisationer mulighed for at drage fordel af en enkelt integreret løsning, der sikrer alle deres infrastruktur til IoT og Driftsteknologi (OT). Du kan få mere at vide [under Virksomheds-IoT-netværksbeskyttelse](/azure/defender-for-iot/organizations/overview-eiot).

Med denne integration aktiveret øger Microsoft Defender for Endpoint synligheden for at hjælpe med at finde, identificere og sikre IoT-enheder i dit netværk. IoT-enheder, der opdages af Microsoft Defender til IoT, eller Microsoft Defender til slutpunkt synkroniseres automatisk på tværs af begge portaler. Dette giver dig en samlet oversigt over dit komplette lager af OT/IoT sammen med resten af dine it-enheder (arbejdsstationer, servere og mobil).

Microsoft Defender til IoT omfatter også en netværkssensor, der kan installeres, og som giver en ekstra datakilde. Hvis du konfigurerer en netværkssensor som en del af din integration, får du den mest komplette visning af dine IoT- og OT-enheder, specielt til netværkssegmenter, hvor microsoft Defender til slutpunktssensorer ikke er til stede, og når medarbejdere har fjernadgang til oplysninger.

## <a name="prerequisites"></a>Forudsætninger

For at aktivere Microsoft Defender til IoT skal brugeren have følgende roller:

- Global lejeradministrator i Azure Active Directory
- Sikkerhedsadministrator for det Azure-abonnement, der skal bruges til Microsoft Defender til IoT-integration

## <a name="enabling-the-microsoft-defender-for-iot-integration"></a>Aktivering af integration af Microsoft Defender til IoT

1. I navigationsruden på portalen skal [https://security.microsoft.com](https://security.microsoft.com/) **du vælge Indstillinger** \> **Microsoft** \> **Defender til IoT.**

    ![Billede af konfiguration af IoT-integration.](images/enable-defender-for-iot.png)

2. **Vælg et Azure-abonnement** på rullelisten over tilgængelige abonnementer i din Azure Active Directory, og vælg **Gem**.

## <a name="set-up-a-network-sensor"></a>Konfigurer en netværks sensor

Med et Azure-abonnement markeret kan du tilføje en netværkssensor.

Hvis du vil tilføje en netværkssensor, skal **du vælge** **linket Microsoft Defender til IoT under Konfigurer netværkssensorer** . Dette fører dig til onboard sensor-konfigurationsprocessen i Azure-portalen. Få mere at vide under [Administrer sensorerne med Defender til IoT i Azure-portalen](/azure/defender-for-iot/organizations/how-to-manage-sensors-on-the-cloud).

## <a name="turn-off-subscription-integration"></a>Slå abonnementsintegration fra

Du kan deaktivere Azure-abonnementsintegrationen fra siden med indstillinger for Microsoft Defender til IoT i [https://security.microsoft.com](https://security.microsoft.com/) portalen. Når du deaktiverer abonnementet, får du ikke længere vist IoT-enheder, der findes af Microsoft Defender til IoT, i lageret for Microsoft Defender til slutpunktsenheder.

## <a name="see-also"></a>Se også

- [Oversigt over enhedsregistrering](configure-device-discovery.md)
- [Ofte stillede spørgsmål om enhedsregistrering](device-discovery-faq.md)
