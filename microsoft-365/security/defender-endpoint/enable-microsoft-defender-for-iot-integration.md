---
title: Onboard Microsoft Defender til IoT med Microsoft Defender for Endpoint
description: Onboard med Microsoft Defender for IoT for at få synlighed og sikkerhedsvurderinger, der fokuserer på IoT-enheder.
keywords: aktivér siem-connector, siem, connector, sikkerhedsoplysninger og -hændelser
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
ms.openlocfilehash: a70b61ff9a27b10e66b6f4537751790eaabc59af
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617276"
---
# <a name="onboard-with-microsoft-defender-for-iot"></a>Onboard med Microsoft Defender for IoT

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Microsoft Defender for Endpoint integreres nu problemfrit med Microsoft Defender for IoT. Denne integration udvider enhedens registreringsfunktioner med de agentløse overvågningsfunktioner, der leveres af Defender for IoT. Dette hjælper med at sikre IoT-enheder til virksomheder, der har forbindelse til it-netværk, f.eks. VoIP-enheder (Voice over Internet Protocol), printere og kameraer. Det giver organisationer mulighed for at drage fordel af en enkelt integreret løsning, der sikrer al deres IoT- og OT-infrastruktur (Operational Technology). Du kan få flere oplysninger under [Enterprise IoT-netværksbeskyttelse](/azure/defender-for-iot/organizations/overview-eiot).

Når du har defineret en Defender for IoT-plan og konfigureret en Enterprise IoT-netværkssensor, starter enhedsdataene automatisk streaming til både Defender for Endpoint- og Defender for IoT-portaler. 

Defender for IoT-integration giver øget synlighed for at hjælpe med at finde, identificere og sikre IoT-enhederne i dit netværk. Dette giver dig et enkelt samlet overblik over dit komplette OT/IoT-lager sammen med resten af dine it-enheder (arbejdsstationer, servere og mobil).

Kunder, der har onboardet til Defender for IoT, har også sikkerhedsanbefalinger til sårbarhedsvurderinger og forkert konfiguration af IoT-enheder.

## <a name="prerequisites"></a>Forudsætninger

Brugeren skal have følgende roller for at ændre indstillingerne for integration af Defender for Endpoint:

- Global lejeradministrator i Azure Active Directory
- Sikkerhedsadministrator for det Azure-abonnement, der skal bruges til Microsoft Defender for IoT-integration

## <a name="onboard-a-defender-for-iot-plan"></a>Ombord på en Defender for IoT-plan

1. I navigationsruden på portalen [https://security.microsoft.com](https://security.microsoft.com/) skal du vælge **Indstillinger** \> **Enhedsregistrering** \> **Enterprise IoT**.

1. Vælg følgende indstillinger for din plan:

   - Vælg Azure-abonnementet på listen over tilgængelige abonnementer i din Azure Active Directory-lejer, hvor du vil tilføje en plan.

   - Vælg en prisplan, enten en månedlig eller årlig forpligtelse eller en prøveversion. Microsoft Defender til IoT indeholder en 30-dages gratis prøveversion af de første 1.000 bekræftede enheder til evalueringsformål.

      Du kan finde flere oplysninger på [siden med priser på Microsoft Defender for IoT](https://azure.microsoft.com/pricing/details/iot-defender/).
   
   - Vælg det antal bekræftede enheder, du vil overvåge. Hvis du har valgt en prøveversion, vises denne sektion ikke, da du har en standardversion på 1000 enheder.

## <a name="set-up-a-network-sensor"></a>Konfigurer en netværkssensor

Hvis du vil konfigurere en netværkssensor, skal dit Azure-abonnement have en Defender for IoT-plan med Enterprise IoT-enheder tilføjet. Du kan få flere oplysninger under [Kom i gang med Defender for IoT](/azure/defender-for-iot/organizations/getting-started).

Hvis du vil tilføje en netværkssensor, skal du under **Konfigurer netværkssensorer** vælge **linket Microsoft Defender for IoT** . Dette fører dig til Onboard-sensorkonfigurationsprocessen i Azure Portal. Du kan få flere oplysninger under [Kom i gang med Enterprise IoT](/azure/defender-for-iot/organizations/tutorial-getting-started-eiot-sensor).

## <a name="managing-your-iot-devices"></a>Administration af dine IoT-enheder

Hvis du vil have vist og administrere dine IoT-enheder på [Microsoft 365 Defender-portalen](https://security.microsoft.com/), skal du gå til **enhedsoversigten** i **navigationsmenuen Slutpunkter** og vælge fanen **IoT-enheder**.

Du kan få oplysninger om, hvordan du får vist enhederne i Defender for IoT, under [Administrer dine IoT-enheder med enhedslageret for organisationer](/azure/defender-for-iot/organizations/how-to-manage-device-inventory-for-organizations).


## <a name="view-devices-alerts-recommendations-and-vulnerabilities"></a>Få vist enheder, beskeder, anbefalinger og sikkerhedsrisici

Når du har defineret din plan og konfigureret en netværkssensor, kan du få vist registrerede data og sikkerhedsvurderinger på følgende placeringer:

- Få vist enhedsdata i Defender for Endpoint eller Defender for IoT
- Få vist beskeder, anbefalinger og sikkerhedsrisici i Defender for Endpoint

Du kan finde flere oplysninger på [siden med priser på Defender for IoT](https://azure.microsoft.com/pricing/details/iot-defender/). 

## <a name="cancel-your-defender-for-iot-plan"></a>Annuller din Defender for IoT-plan

Du kan annullere din Defender for IoT-plan fra siden med indstillinger for Defender for Endpoint på portalen [https://security.microsoft.com](https://security.microsoft.com/) . Når du annullerer din plan, stopper integrationen, og du får ikke længere sikkerhedsvurderingsværdi i Defender for Endpoint eller registrerer nye enheder i Defender for IoT.

## <a name="see-also"></a>Se også

- [Oversigt over enhedssøgning](configure-device-discovery.md)
- [Ofte stillede spørgsmål om enhedssøgning](device-discovery-faq.md)
