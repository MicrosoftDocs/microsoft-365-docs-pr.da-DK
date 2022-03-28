---
title: Administrer indikatorer
ms.reviewer: ''
description: Administrer indikatorer for filhash, IP-adresse, URL-adresser eller domæner, der definerer registrering, forebyggelse og udelukkelse af enheder.
keywords: importér, indikator, liste, ioc, csv, manage, allowed, blocked, block, clean, malicious, file hash, ip address, URLs, domain
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
ms.openlocfilehash: 2f66106dd39b9cd1f590148addfdd2cae89748c6
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63597621"
---
# <a name="manage-indicators"></a>Administrer indikatorer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

1. I **navigationsruden** skal du **vælge Indstillinger** \> **Slutpunktsindikatorer** \> (under **Regler**).

2. Vælg fanen for den enhedstype, du vil administrere.

3. Opdater oplysningerne for indikatoren, og **klik** på Gem eller klik  på knappen Slet, hvis du vil fjerne objektet fra listen.

## <a name="import-a-list-of-iocs"></a>Importere en liste over IoCs

Du kan også vælge at overføre en CSV-fil, der definerer attributterne for indikatorer, den handling, der skal gøres, og andre oplysninger.

Download CSV-eksemplet for at kende de understøttede kolonneattributter.

1. I **navigationsruden** skal du **vælge Indstillinger** \> **Slutpunktsindikatorer** \> (under **Regler**).

2. Vælg fanen for den enhedstype, du vil importere indikatorer for.

3. Vælg **Importér** \> **Vælg fil**.

4. Vælg **Importér**. Gør dette for alle de filer, du vil importere.

5. Vælg **Udført**.

> [!NOTE]
> Der kan kun overføres 500 indikatorer for hver batch.

Følgende tabel viser de understøttede parametre.

Parameter|Type|Beskrivelse
:---|:---|:---
indicatorType|Enum|Type af indikatoren. De mulige værdier er: "FileSha1", "FileSha256", "IpAddress", "DomainName" og "URL". **Påkrævet**
indicatorValue|String|Identiteten på [indikatorobjektet](ti-indicator.md) . **Påkrævet**
handling|Enum|Den handling, der skal anvendes, hvis indikatoren findes i organisationen. De mulige værdier er: "Påmindelse", "AlertAndBlock" og "Tilladt". **Påkrævet**
titel|String|Titel på indikatormeddelelse. **Påkrævet**
beskrivelse|String| Beskrivelse af indikatoren. **Påkrævet**
expirationTime|DateTimeOffset|Udløbstidspunkt for indikatoren i følgende format YYYY-MM-DDTHH:MM:SS.0Z. Indikatoren slettes, hvis udløbsdatoen overskrides, og det, der sker på udløbstidspunkt, vises for SS-værdien. **Valgfrit**
alvorsgrad|Enum|Alvorsgrad for indikatoren. De mulige værdier er: "Informational", "Lav", "Mellem" og "Høj". **Valgfrit**
recommendedActions|String|Anbefalede handlinger for TI-indikatorbeskeder. **Valgfrit**
rbacGroupNames|String|Kommasepareret liste over RBAC-gruppenavne, som indikatoren ville blive anvendt på. **Valgfrit**
kategori|String|Kategori for beskeden. Eksempler omfatter: Eksekvering og adgang til legitimationsoplysninger. **Valgfrit**
mitretechniques|String|MITRE-teknikker kode/id (kommasepareret). Du kan finde flere oplysninger under [Virksomhedstakst](https://attack.mitre.org/tactics/enterprise/). **Valgfrit** Det anbefales at tilføje en værdi i kategorien, når en MITRE-teknik.
GenerateAlert|String|Om beskeden skal genereres eller ej. Mulige værdier er: Sand eller Falsk. **Valgfrit**



> [!NOTE]
> CIDR-notation (Classless Inter-Domain Routing) for IP-adresser understøttes ikke.
Du kan få mere at vide [under Kategorierne for påmindelser for Microsoft Defender til Slutpunkt er nu justeret med MITRE ATT&CK!](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-atp-alert-categories-are-now-aligned-with/ba-p/732748).

## <a name="see-also"></a>Se også

- [Opret indikatorer](manage-indicators.md)
- [Opret indikatorer for filer](indicator-file.md)
- [Opret indikatorer for IP'er og URL-adresser/domæner](indicator-ip-domain.md)
- [Opret indikatorer baseret på certifikater](indicator-certificates.md)
