---
title: Grænser for opbevaringspolitikker og politikker for opbevaringsmærkater
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
hideEdit: true
description: Forstå det maksimale antal politikker og elementer pr. politik for opbevaringspolitikker og politikker for opbevaringsmærkater
ms.openlocfilehash: a0246fef2ae72dd2b0b176f82bb42559d405eaa5
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754030"
---
# <a name="limits-for-retention-policies-and-retention-label-policies"></a>Grænser for opbevaringspolitikker og politikker for opbevaringsmærkater

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du bruger [opbevaringspolitikker og politikker for opbevaringsmærkater](retention.md#retention-policies-and-retention-labels) til automatisk at gemme eller slette data for din organisation, er der nogle maksimale tal, du skal være opmærksom på.

## <a name="maximum-number-of-retention-labels-per-tenant"></a>Maksimalt antal opbevaringsmærkater pr. lejer

Der understøttes maksimalt 1.000 opbevaringsmærkater pr. lejer.

## <a name="maximum-number-of-policies-per-tenant"></a>Maksimalt antal politikker pr. lejer

En enkelt lejer kan maksimalt have 10.000 politikker (enhver konfiguration). Dette maksimale antal omfatter de forskellige politikker for opbevaring og andre politikker for overholdelse af angivne standarder, f.eks. politikker for DLP, informationsbarrierer, eDiscovery-ventepositioner, procesførelsespositioner, In-Place ventepositioner og følsomhedsmærkater. Dette maksimum udelukker dog:

- Politikker for automatisk mærkning af SharePoint og OneDrive, medmindre de er til vedhæftede filer i skyen.
- Publicerede mærkatpolitikker for SharePoint og OneDrive, der kun sletter, i stedet for kun at bevare eller bevare og derefter slette.
- Exchange opbevaringspolitikker fra [MRM (Messaging Records Management).](/exchange/security-and-compliance/messaging-records-management/messaging-records-management)

Inden for denne grænse på 10.000 politikker er der også nogle begrænsninger for det maksimale antal politikker for opbevaring pr. arbejdsbelastning:

- Exchange (enhver konfiguration): 1.800
  - Pr. postkasse: 25 er det anbefalede maksimum, før ydeevnen kan blive påvirket. 50 er den understøttede grænse.
- SharePoint eller OneDrive: (alle websteder inkluderes automatisk): 13
- SharePoint eller OneDrive (bestemte lokaliteter inkluderet eller udelukket): 2.600

> [!NOTE]
> Disse maksimale tal for Exchange og SharePoint er ikke eksklusive opbevaring, men deles med andre typer politikker for ventepositioner, der omfatter eDiscovery-ventepositioner, procesførelsespositioner og In-Place ventepositioner.

Selvom opbevaringspolitikker for Microsoft Teams og Yammer bruger postkasser til at gemme data til opbevaringsformål, er det maksimale antal politikker for Exchange Online opbevaringspolitikker for Teams og Yammer.

## <a name="maximums-for-adaptive-policy-scopes"></a>Maksimum for tilpassede politikområder

Der er ingen grænse for antallet af [tilpassede politikområder](retention.md#adaptive-or-static-policy-scopes-for-retention) , som du kan føje til en politik for opbevaring, men der er nogle maksimumgrænser for forespørgslen, der definerer hvert adaptive omfang:

- Strenglængde for attribut- eller egenskabsværdier: 200
- Antal attributter eller egenskaber uden en gruppe eller inden for en gruppe: 10
- Antal grupper: 10
- Antal tegn i en avanceret forespørgsel: 10.000

Grupperingsattributter eller egenskaber i en gruppe understøttes ikke. Det betyder, at det maksimale antal egenskaber eller attributter, der understøttes inden for et enkelt tilpasset område, er 100.

## <a name="maximum-number-of-items-per-policy"></a>Maksimalt antal elementer pr. politik

> [!IMPORTANT]
> Gælder kun, hvis du bruger [statiske politikområder i stedet for tilpassede politikområder](retention.md#adaptive-or-static-policy-scopes-for-retention).

Hvis du bruger statiske områder og den valgfri konfiguration til at inkludere eller udelade bestemte brugere, bestemte Microsoft 365 grupper eller bestemte websteder, er der nogle grænser pr. politik, du skal være opmærksom på.

Maksimalt antal elementer pr. politik for opbevaring for statiske områder:

- Exchange postkasser: 1.000
- Microsoft 365-grupper: 1.000
- Teams kanalmeddelelser: 1.000
- Teams chats: 1.000
- Yammer communitymeddelelser: 1.000
- Yammer brugermeddelelser: 1.000
- SharePoint websteder: 100
- OneDrive konti: 100

Skype for Business skal være begrænset til bestemte brugere, og det maksimale antal, der understøttes pr. politik, er 1.000.

Da disse begrænsninger gælder pr. politik, kan du oprette yderligere politikker, der har de samme opbevaringsindstillinger, hvis du har brug for specifikke medtagelser eller udeladelser, der medfører, at disse tal overskrides. Se næste afsnit for nogle [eksempelscenarier og løsninger](#examples-of-using-multiple-policies-to-avoid-exceeding-maximum-numbers) , der bruger flere opbevaringspolitikker af denne årsag.

Flere politikker medfører dog højere administrative omkostninger. Overvej at bruge tilpassede områder i stedet for at oprette og vedligeholde flere politikker med "include" og "excludes".

### <a name="examples-of-using-multiple-policies-to-avoid-exceeding-maximum-numbers"></a>Eksempler på brug af flere politikker for at undgå at overskride det maksimale antal

Følgende eksempler er til statiske områder og giver nogle designløsninger, når du ikke kun kan angive placeringen for en opbevaringspolitik, og du skal tage højde for det maksimale antal elementer, der er dokumenteret i det forrige afsnit.

Exchange eksempel:

- **Krav**: I en organisation, der har over 40.000 brugerpostkasser, skal de fleste brugere have deres mail opbevaret i syv år, men et undersæt af identificerede brugere (425) skal beholde deres mail i kun fem år.

- **Løsning**: Opret én opbevaringspolitik for Exchange mail med en opbevaringsperiode på 7 år, og udelad undersættet af brugere. Opret derefter endnu en opbevaringspolitik for Exchange mail med en opbevaringsperiode på 5 år, og medtag undersættet af brugere.

    I begge tilfælde er det antal, der er inkluderet og udeladt, under det maksimale antal angivne postkasser for en enkelt politik, og undersættet af brugere skal udtrykkeligt udelades fra den første politik, fordi den har en [længere opbevaringsperiode](retention.md#the-principles-of-retention-or-what-takes-precedence) end den anden politik. Hvis undersættet af brugere krævede en længere opbevaringspolitik, behøver du ikke at udelade dem fra den første politik.

    Med denne løsning er postkassen automatisk inkluderet i den første politik i syv år, hvis nogen nye tilmelder sig organisationen, og der er ingen indvirkning på det maksimale antal, der understøttes. Nye brugere, der kræver opbevaringsperioden på 5 år, føjer dog til tallene for inkludering og udeladelse, og denne grænse nås ved 1.000.

SharePoint eksempel:

- **Krav**: En organisation har flere tusinde SharePoint websteder, men kun 2.000 websteder kræver en opbevaringsperiode på 10 år, og 8.000 websteder kræver en opbevaringsperiode på fire år.

- **Løsning**: Opret 20 opbevaringspolitikker for SharePoint med en opbevaringsperiode på 10 år, der omfatter 100 specifikke websteder, og opret 80 opbevaringspolitikker for SharePoint med en opbevaringsperiode på 4 år, der omfatter 100 specifikke websteder.

    Da du ikke behøver at bevare alle SharePoint websteder, skal du oprette opbevaringspolitikker, der angiver de specifikke websteder. Da en opbevaringspolitik ikke understøtter mere end 100 angivne websteder, skal du oprette flere politikker for de to opbevaringsperioder. Disse opbevaringspolitikker har det maksimale antal inkluderede websteder, så det næste nye websted, der skal bevares, kræver en ny opbevaringspolitik, uafhængigt af opbevaringsperioden.

## <a name="maximum-number-of-items-for-disposition"></a>Maksimalt antal elementer til fordeling

For [fordelingen af indhold](disposition.md) er der nogle grænser, du skal være opmærksom på:

- Maksimalt antal tal pr. lejer:
  - 16.000.000 elementer i en af følgende tilstande for dispositionsgennemgang: ventende disposition eller godkendt fordeling
  - 16.000.000 elementer, der er markeret som poster automatisk fjernet (ingen dispositionsgennemsyn)

- Maksimalt antal tal for hver opbevaringsmærkat:
  - 1.000.000 ventende elementer pr. fase for hver opbevaringsmærkat
  - Bevis for fordeling i op til syv år efter, at varen blev bortskaffet, med en grænse på 1.000.000 elementer pr. opbevaringsmærkat for den pågældende periode.

    Hvis du har brug for bevis for, at dispositionen er højere end denne grænse på 1.000.000 for elementer, der er markeret som poster, skal du kontakte [Microsoft Support](../admin/get-help-support.md).
