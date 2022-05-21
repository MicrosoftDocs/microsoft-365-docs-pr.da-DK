---
title: Administrer indikatorer
ms.reviewer: ''
description: Administrer indikatorer for filhash, IP-adresse, URL-adresser eller domæner, der definerer registrering, forebyggelse og udeladelse af enheder.
keywords: import, indikator, liste, ioc, csv, administrere, tilladt, blokeret, bloker, ren, skadelig, filhash, ip-adresse, URL-adresser, domæne
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
ms.openlocfilehash: 72509f7480d54819fc29f40bab0e2bf65dcd8660
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622026"
---
# <a name="manage-indicators"></a>Administrer indikatorer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

1. Vælg **Indstillinger** \> **Slutpunktsindikatorer** \> (under **Regler**) i navigationsruden.

2. Vælg fanen for den objekttype, du vil administrere.

3. Opdater oplysningerne om indikatoren, og klik på **Gem** eller klik på knappen **Slet** , hvis du vil fjerne enheden fra listen.

## <a name="import-a-list-of-iocs"></a>Importér en liste over IoCs

Du kan også vælge at uploade en CSV-fil, der definerer indikatorernes attributter, den handling, der skal udføres, og andre oplysninger.

Download CSV-eksemplet for at få kendskab til de understøttede kolonneattributter.

1. Vælg **Indstillinger** \> **Slutpunktsindikatorer** \> (under **Regler**) i navigationsruden.

2. Vælg fanen for den objekttype, du vil importere indikatorer for.

3. Vælg **Importér** \> **Vælg fil**.

4. Vælg **Importér**. Gør dette for alle de filer, du vil importere.

5. Vælg **Udført**.

> [!NOTE]
> Der kan kun uploades 500 indikatorer for hvert batch.

I følgende tabel vises de understøttede parametre.

Parameter|Type|Beskrivelse
:---|:---|:---
indicatorType|Enum|Indikatorens type. De mulige værdier er: "FileSha1", "FileSha256", "IpAddress", "DomainName" og "URL". **Påkrævet**
indicatorValue|String|Id for [indikatorenheden](ti-indicator.md) . **Påkrævet**
Handling|Enum|Den handling, der udføres, hvis indikatoren registreres i organisationen. De mulige værdier er: "Alert", "AlertAndBlock" og "Allowed". **Påkrævet**
Titel|String|Titel på indikatoradvarsel. **Påkrævet**
Beskrivelse|String| Beskrivelse af indikatoren. **Påkrævet**
expirationTime|DateTimeOffset|Indikatorens udløbstid i følgende format YYYY-MM-DDTHH:MM:SS.0Z. Indikatoren slettes, hvis udløbstiden passerer, og det, der sker på udløbstidspunktet, sker ved sekundværdien (SS). **Valgfrit**
Sværhedsgraden|Enum|Indikatorens alvorsgrad. De mulige værdier er: "Informational", "Low", "Medium" og "High". **Valgfrit**
recommendedActions|String|Anbefalede handlinger for ti-indikatorbeskeder. **Valgfrit**
rbacGroupNames|String|Kommasepareret liste over RBAC-gruppenavne, som indikatoren anvendes på. **Valgfrit**
Kategori|String|Kategorien for beskeden. Eksempler omfatter: Udførelse og adgang til legitimationsoplysninger. **Valgfrit**
mitretechniques|String|MITRE-teknikker kode/id (kommasepareret). Du kan få flere oplysninger under [Virksomhedstaktik](https://attack.mitre.org/tactics/enterprise/). **Valgfri** Det anbefales at tilføje en værdi i kategorien, når en MITRE-teknik.
GenerateAlert|String|Angiver, om beskeden skal genereres. Mulige værdier er: Sand eller Falsk. **Valgfrit**

> [!NOTE]
> CIDR-notation (Classless Inter-Domain Routing) for IP-adresser understøttes ikke.
Du kan få flere oplysninger under [Microsoft Defender for Endpoint beskedkategorier nu er justeret i forhold til MITRE ATT&CK!](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-atp-alert-categories-are-now-aligned-with/ba-p/732748).

Se denne video for at få mere at vide om, hvordan Microsoft Defender for Endpoint giver flere måder at tilføje og administrere indikatorer for kompromitteret (IoCs). 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4qLVw]

## <a name="see-also"></a>Se også

- [Opret indikatorer](manage-indicators.md)
- [Opret indikatorer for filer](indicator-file.md)
- [Opret indikatorer for IP'er og URL-adresser/domæner](indicator-ip-domain.md)
- [Opret indikatorer baseret på certifikater](indicator-certificates.md)
