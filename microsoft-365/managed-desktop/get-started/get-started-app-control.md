---
title: Introduktion til appkontrol
description: I denne artikel beskrives det, hvordan du aktiverer appkontrol
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: a671bf36e957ffc416f51ec531aaeed6ddfa41b3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590912"
---
# <a name="get-started-with-app-control"></a>Introduktion til appkontrol

Før du aktiverer appkontrol i dit miljø, skal du sørge for at gennemse og forstå, hvordan [Microsoft Managed Desktop](../service-description/app-control.md) implementerer det samt dine roller og ansvarsområder.

Microsoft-administreret skrivebord forenkler appstyringen ved at tage sig af de mere udfordrende aspekter af at få en sikker basispolitik.

Dine it-administratorer skal teste dine apps i testringen og gennemse logfilerne for eventuelle advarsler eller fejl. Hvis en app kræver en undtagelse, kan du arkivere en anmodning, eller Microsoft Managed Desktop Operation kan, afhængigt af hvem der registrerer den først.

## <a name="initial-deployment-of-apps"></a>Indledende installation af apps

Når du installerer apps, skal Microsoft Managed Desktop vurdere deres aktuelle funktionsmåde. De nøjagtige trin til aktivering af appstyring afhænger af, om enhederne allerede er installeret i dit miljø.

### <a name="devices-not-yet-in-use"></a>Enheder, der endnu ikke er i brug

Hvis du endnu ikke har nogen enheder i brug, skal du åbne en supportbillet med Microsoft Managed Desktop Operations for at anmode om at aktivere appstyring. Handlinger vil løbende udrulle politikker til installationsgrupper efter denne tidsplan:

| Installationsgruppe | Politiktype | Tidsindstilling |
| ------ | ------ | ------ |
| Test |  Overvågning |  Dag 0 |
| Første | Gennemtvunget | Dag 1 |
| Hurtig | Gennemtvunget |  Dag 2 |
| Bred | Gennemtvunget |  Dag 3 |

Du kan altid åbne en anden supportanmodning for at afbryde eller tilbagetrule en del af denne installation når som helst i løbet af implementeringen.

### <a name="devices-already-in-use"></a>Enheder, der allerede er i brug

Hvis der allerede er mindst én Microsoft-administreret skrivebordsenhed i brug, skal du følge disse trin:

1. Åbn en servicebillet med Microsoft Managed Desktop Operations for at anmode om, at vi aktiverer appkontrol. Handlinger vil implementere en [overvågningspolitik](../service-description/app-control.md#audit-policy) på alle enheder.
2. [Test dine programmer for](../working-with-managed-desktop/work-with-app-control.md#add-a-new-app) at se, om nogen af dem er blokeret. Hvis et program bliver blokeret, skal du åbne en [anmodning om underskriver](../working-with-managed-desktop/work-with-app-control.md#add-or-remove-a-trusted-signer).
3. Når du har gennemført testen (uanset resultaterne), skal du give besked om Handlinger og notere eventuelle ventende anmodninger om underskrivere. Handlinger vil løbende udrulle politikker til installationsgrupper efter denne tidsplan:

| Installationsgruppe | Politiktype | Tidsindstilling |
| ------ | ------ | ------ |
| Test     | Overvågning |  Dag 0 |
| Første     | Gennemtvunget | Dag 1 |
| Hurtig     | Gennemtvunget |  Midlertidigt afbrudt, udrulning efter anmodning |
| Bred     | Gennemtvunget |  Midlertidigt afbrudt, udrulning efter anmodning |

Du kan altid åbne en anden supportanmodning for at afbryde eller tilbagetrule en del af denne installation når som helst i løbet af implementeringen.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Trin til at komme i gang med Microsoft-administreret skrivebord

1. Få adgang [til administrationsportalen](access-admin-portal.md).
1. [Tilføj og bekræft administratorkontakter i administrationsportalen](add-admin-contacts.md).
1. [Juster indstillinger efter tilmelding](conditional-access.md).
1. Installér og [tildel Intune-firmaportal](company-portal.md).
1. [Tildel licenser](assign-licenses.md).
1. [Installér apps](deploy-apps.md).
1. [Klargør enheder](prepare-devices.md).
1. Konfigurer første [kørselsoplevelse med Autopilot og Statussiden For tilmelding](esp-first-run.md).
1. [Aktivér brugersupportfunktioner](enable-support.md).
1. [Gør dine brugere klar til at bruge enheder](get-started-devices.md).
1. Kom i gang med appstyring (denne artikel).
