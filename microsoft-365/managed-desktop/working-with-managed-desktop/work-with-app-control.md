---
title: Arbejde med appkontrol
description: Få mere at vide om, hvordan du administrerer appkontrol.
keywords: Microsoft Managed Desktop, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: 99979a08a67245d471b33ce26e4b7f35790fead5
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569903"
---
# <a name="work-with-app-control"></a>Arbejde med appkontrol

Når appkontrol er blevet installeret i dit miljø, har både du og Microsoft Managed Desktop Operations løbende ansvarsområder. Det kan f.eks. være, at du vil tilføje en ny app i miljøet eller tilføje (eller fjerne) en underskriver, der er tillid til. For at forbedre sikkerheden skal alle apps signeres med kode, før du frigiver dem til brugerne. En apps udgiveroplysninger indeholder oplysninger om underskriveren.

## <a name="add-a-new-app"></a>Tilføj en ny app

**Sådan tilføjer du en ny app:**

1. Føj appen til [Microsoft Intune](/mem/intune/apps/apps-win32-app-management).
1. Installér appen på en hvilken som helst enhed i Testring.
1. Test din app i overensstemmelse med dine almindelige forretningsprocesser.
1. Kontrollér Logbog under **Application and Services Logs\Microsoft\Windows\AppLocker**. Se efter **8003-** eller **8006-begivenheder** . Disse hændelser angiver, at appen er blokeret. Du kan finde flere oplysninger om alle app-skabsbegivenheder og deres betydning i [Brug Logbog med AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/using-event-viewer-with-applocker).
1. Hvis du finder nogen af disse hændelser, skal du åbne en underskriveranmodning med Microsoft Managed Desktop Handlinger.

## <a name="add-or-remove-a-trusted-signer"></a>Tilføje (eller fjerne) en underskriver, der er tillid til

Når du åbner en underskriveranmodning, skal du først angive nogle vigtige udgiveroplysninger.

**Sådan tilføjer (eller fjerner du) en underskriver, der er tillid til:**

1. [Saml udgiveroplysninger](#gather-publisher-details).
1. Åbn en billet hos Microsoft Managed Desktop Operations for at anmode om underskriverreglen og inkludere følgende oplysninger:  
    - Programmets navn
    - Programversion
    - Beskrivelse
    - Skift type ("tilføj" eller "fjern")  
    - Publisher detaljer (f.eks.: `O=<publisher name>,L=<location>,S=State,C=Country`)

> [!NOTE]
> Hvis du vil fjerne tillid til en app, skal du følge de samme trin, men angive **ændringstypen, der** skal *fjernes*.

Handlinger vil løbende udrulle politikker til installationsgrupper efter denne tidsplan:

|Installationsgruppe|Politiktype|Tidsindstilling|
|---|---|---|
|Test|Overvågning|Dag 0|
|Første|Gennemtvunget|Dag 1|
|Hurtig|Gennemtvunget|Dag 2|
|Bred|Gennemtvunget|Dag 3|

Du kan når som helst afbryde eller tilbagerulle installationen under udrulningen. Hvis du vil afbryde eller rulle tilbage, skal du åbne en anden supportanmodning Microsoft Managed Desktop Handlinger.

> [!NOTE]
> Hvis du afbryder frigivelsen af en underskriverregel midlertidigt, skal reglen enten annulleres eller fuldføres, før en anden udrulning kan starte.

## <a name="gather-publisher-details"></a>Indsamle udgiveroplysninger

**Sådan får du adgang til udgiverdataene for en app:**

1. Find en Microsoft Managed Desktop enhed i testringen, der har en politik for overvågningstilstand anvendt.
1. Forsøg at installere appen på enheden.
1. Åbn Logbog på den pågældende enhed.
1. I dialogboksen Logbog du gå til **Application and Services Logs\Microsoft\Windows** og derefter vælge **AppLocker**.
1. Find en **vilkårlig 8003** - **eller 8006-begivenhed** , og kopiér derefter oplysninger fra begivenheden:
    - Programmets navn
    - Programversion
    - Beskrivelse
    - Publisher detaljer (f.eks.: `O=<publisher name>, L=<location>, S=State, C=Country`)
