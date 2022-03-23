---
title: Begrænsninger for opbevaringspolitikker og opbevaringsetiketpolitikker
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
description: Forstå det maksimale antal politikker og elementer pr. politik for opbevaringspolitikker og opbevaringsmærkatpolitikker
ms.openlocfilehash: 4cd8fc5f141f9e039a271e8534e156e4df0582e9
ms.sourcegitcommit: 40f89c46032ea33de25417106f39cbeebef5a049
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/10/2022
ms.locfileid: "63591959"
---
# <a name="limits-for-retention-policies-and-retention-label-policies"></a>Begrænsninger for opbevaringspolitikker og opbevaringsetiketpolitikker

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Når du bruger [opbevaringspolitikker og opbevaringspolitikker](retention.md#retention-policies-and-retention-labels) til automatisk at bevare eller slette data for organisationen, er der nogle maksimale tal, du skal være opmærksom på.

## <a name="maximum-number-of-retention-labels-per-tenant"></a>Maksimale antal opbevaringsnavne pr. lejer

Der understøttes maksimalt 1.000 opbevaringsetiketter pr. lejer.

## <a name="maximum-number-of-policies-per-tenant"></a>Maksimalt antal politikker pr. lejer

En enkelt lejer kan maksimalt have 10.000 politikker (enhver konfiguration). Dette maksimale antal omfatter de forskellige politikker for opbevaring og andre politikker for overholdelse, som f.eks. politikker for DLP, informationsbarrierer, eDiscovery-ventende funktioner, retslig tilbageholdelser, In-Place vente hold og følsomhedsetiketter. Dette maksimum udelader dog:

- Politikker for automatisk mærkatering for SharePoint og OneDrive, medmindre de er til vedhæftede skybaserede filer.
- Publicerede etiketpolitikker for SharePoint og OneDrive, som kun skal slettes, i stedet for kun at blive bevaret eller bevares og derefter slettes.
- Exchange opbevaringspolitikker fra [MRM (messaging records management](/exchange/security-and-compliance/messaging-records-management/messaging-records-management)).

Inden for denne grænse på 10.000 politikker er der også nogle begrænsninger for det maksimale antal politikker for opbevaring pr. arbejdsbelastning:

- Exchange (enhver konfiguration): 1.800
    - Pr. postkasse: 25 er den anbefalede maksimum, før ydeevnen kan blive påvirket; 50 er den understøttede grænse.
- SharePoint eller OneDrive: (Alle websteder inkluderes automatisk): 13
- SharePoint eller OneDrive (bestemte placeringer medtaget eller udeladt): 2.600

> [!NOTE]
> Disse maksimale tal for Exchange og SharePoint er ikke eksklusive til opbevaring, men deles med andre typer ventepositionspolitikker, der omfatter eDiscovery-ventepositioner, retslig tilbageholdelser og In-Place ventepositioner.

Selvom opbevaringspolitikker for Microsoft Teams og Yammer bruger postkasser til at gemme data til opbevaringsformål, udelader det maksimale antal politikker for Exchange Online opbevaringspolitikker til Teams og Yammer.

## <a name="maximums-for-adaptive-policy-scopes"></a>Maksimum for adaptive politikomfang

Der er ingen begrænsninger for antallet af tilpassede [](retention.md#adaptive-or-static-policy-scopes-for-retention) politikomfang, som du kan føje til en politik for opbevaring, men der er nogle maksimumgrænser for forespørgslen, der definerer hvert tilpasset omfang:

- Strenglængde for attribut- eller egenskabsværdier: 200
- Antal attributter eller egenskaber uden en gruppe eller inden for en gruppe: 10
- Antal grupper: 10
- Antal tegn i en avanceret forespørgsel: 10.000

Gruppering af attributter eller egenskaber i en gruppe understøttes ikke. Det betyder, at det maksimale antal egenskaber eller attributter, der understøttes i et enkelt tilpasset omfang, er 100.

## <a name="maximum-number-of-items-per-policy"></a>Maksimale antal elementer pr. politik

> [!IMPORTANT]
> Gælder kun, hvis du [bruger statiske politikomfang i stedet for tilpassede politikomfang](retention.md#adaptive-or-static-policy-scopes-for-retention).

Hvis du bruger statiske områder og den valgfri konfiguration til at medtage eller udelade bestemte brugere, bestemte Microsoft 365-grupper eller bestemte websteder, er der nogle begrænsninger pr. politik, du skal være opmærksom på. 

Maksimale antal elementer pr. politik for opbevaring for statiske områder:

- Exchange postkasser: 1.000
- Microsoft 365 grupper: 1.000
- Teams kanalmeddelelser: 1.000
- Teams chatsamtaler: 1.000
- Yammer gruppemeddelelser: 1.000
- Yammer brugermeddelelser: 1.000
- SharePoint websteder: 100
- OneDrive konti: 100

Skype for Business skal være begrænset til bestemte brugere, og det maksimale antal understøttede antal understøttede pr. politik er 1.000.

Da disse begrænsninger er pr. politik, kan du oprette yderligere politikker, der har de samme opbevaringsindstillinger, hvis du skal bruge bestemte inklusioner eller udeladelsesbegrænsninger, der fører til, at disse tal udelades. I næste afsnit finder du nogle [eksempler på scenarier og løsninger, der](#examples-of-using-multiple-policies-to-avoid-exceeding-maximum-numbers) bruger flere opbevaringspolitikker af denne årsag.

Flere politikker medfører dog højere administrative omkostninger. Overvej at bruge adaptive områder i stedet for at oprette og vedligeholde flere politikker med medtager og udelader.

### <a name="examples-of-using-multiple-policies-to-avoid-exceeding-maximum-numbers"></a>Eksempler på brug af flere politikker for at undgå at overskride det maksimale antal

Følgende eksempler er til statiske områder og giver nogle designløsninger, når du ikke kun kan angive placeringen for en opbevaringspolitik, og du skal tage højde for det maksimale antal elementer, der er dokumenteret i forrige afsnit.

Exchange eksempel:

- **Krav**: I en organisation, der har over 40.000 brugerpostkasser, skal de fleste brugere have deres mail bevaret i 7 år, men en delmængde af identificerede brugere (425) skal bevare deres mail i kun fem år.

- **Løsning**: Opret én opbevaringspolitik for Exchange med en opbevaringsperiode på 7 år, og ekskluder undersættet af brugere. Opret derefter en anden opbevaringspolitik for Exchange med en opbevaringsperiode på 5 år og medtag undersættet af brugere. 
    
    I begge tilfælde er det antal, der er medtaget og udeladt, under det maksimale antal angivne postkasser for en enkelt politik, og undersættet af brugere skal udtrykkeligt udelukkes fra den første politik, [](retention.md#the-principles-of-retention-or-what-takes-precedence) fordi den har en længere opbevaringsperiode end den anden politik. Hvis undersættet af brugere kræver en længere opbevaringspolitik, behøver du ikke at udelukke dem fra den første politik.
     
    Med denne løsning medtages deres postkasse automatisk i den første politik i 7 år, hvis nogen tilmelder sig organisationen, og det har ingen indflydelse på de maksimalt understøttede tal. Nye brugere, der kræver en opbevaringsperiode på 5 år, føjer dem til medtag og udelader tal, og denne grænse vil blive nået på 1.000.

SharePoint eksempel:

- **Krav**: En organisation har flere tusinde SharePoint websteder, men kun 2.000 websteder kræver en opbevaringsperiode på 10 år, og 8.000 websteder kræver en opbevaringsperiode på 4 år.

- **Løsning**: Opret 20 opbevaringspolitikker til SharePoint med en opbevaringsperiode på 10 år, der omfatter 100 specifikke websteder, og opret 80 opbevaringspolitikker til SharePoint med en opbevaringsperiode på 4 år, der omfatter 100 bestemte websteder.
    
    Da du ikke behøver at bevare alle websteder, SharePoint, skal du oprette opbevaringspolitikker, der angiver de bestemte websteder. Da en opbevaringspolitik ikke understøtter mere end 100 angivne websteder, skal du oprette flere politikker for de to opbevaringsperioder. Disse opbevaringspolitikker har det maksimale antal inkluderede websteder, så det næste nye websted, der skal bevares, vil kræve en ny opbevaringspolitik uanset opbevaringsperioden.

## <a name="maximum-number-of-items-for-disposition"></a>Maksimale antal elementer til disposition

Når du [skal være opmærksom på dispositionen](disposition.md) af indhold, er der nogle begrænsninger, du skal være opmærksom på:

- 1.000.000 elementer, der afventer disposition pr. fase for hver opbevaringsetiket

- Dispositionsbevis i op til syv år, efter at varen er blevet fjernet, med en begrænsning på 1.000.000 elementer pr. opbevaringsmærkat for den pågældende periode. 
    
Hvis du har brug for en disposition, der er højere end denne grænse på 1.000.000 for elementer, der er markeret som poster, skal du kontakte [Microsoft Support](../admin/get-help-support.md).
