---
title: Microsoft Secure Score til enheder
description: Dine pointtal for enheder viser den kollektive sikkerhedskonfigurationstilstand for dine enheder på tværs af programmer, operativsystemer, netværk, konti og sikkerhedskontrolelementer.
keywords: Microsoft Secure Score til enheder, Microsoft Defender til slutpunkt Microsoft Secure Score til enheder, sikker score, konfigurationsscore, Håndtering af trusler og sikkerhedsrisici, sikkerhedskontrolelementer, forbedringsmuligheder, sikkerhedskonfigurationsscore over tid, sikkerhedsovergang, grundlinje
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ccd5164839244250c5e2d908f41c35a706e0f49d
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592046"
---
# <a name="microsoft-secure-score-for-devices"></a>Microsoft Secure Score til enheder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

> [!NOTE]
> Konfigurationsresultatet er nu en del Håndtering af trusler og sikkerhedsrisici Microsoft Secure Score for enheder.

Dine pointtal for enheder vises på [Håndtering af trusler og sikkerhedsrisici dashboard](tvm-dashboard-insights.md) i Microsoft 365 Defender portalen. Et højere Microsoft Secure Score for Devices betyder, at dine slutpunkter er mere robuste mod cyberangreb. Den afspejler den kollektive sikkerhedskonfigurationstilstand for dine enheder på tværs af følgende kategorier:

- Program
- Operativsystem
- Netværk
- Konti
- Sikkerhedskontrolelementer

Vælg en kategori for at gå til [**siden med sikkerhedsanbefalinger**](tvm-security-recommendation.md) og få vist de relevante anbefalinger.

## <a name="turn-on-the-microsoft-secure-score-connector"></a>Slå Microsoft Secure Score-forbindelsen til

Videresende Microsoft Defender til slutpunktssignaler, hvilket giver Microsoft Secure Score indblik i enhedens sikkerhedslager. Videresendte data gemmes og behandles på samme placering som dine Microsoft Secure Score-data.

Der kan gå op til et par timer, før ændringerne afspejles i dashboardet.

1. I navigationsruden skal du gå **til Indstillinger** \> **Generelle avancerede funktioner** \> **i** \> **Slutpunkter**

2. Rul ned **til Microsoft Secure Score** , og skift indstillingen til **Til**.

3. Vælg **Gem indstillinger**.

## <a name="how-it-works"></a>Sådan fungerer det

> [!NOTE]
> Microsoft Secure Score for enheder understøtter i øjeblikket konfigurationer, der er angivet via Gruppepolitik. På grund af den aktuelle delvise understøttelse af Intune kan konfigurationer, der er blevet konfigureret via Intune, blive vist som forkert konfigurerede. Kontakt din it-administrator for at bekræfte den faktiske konfigurationsstatus, hvis din organisation bruger Intune til sikker konfigurationsstyring.

Dataene i kortet Microsoft Secure Score for Devices er produktet af en omhyggelig og løbende proces til registrering af sikkerhedsrisiko. Det samles med konfigurationsvurderinger for registrering, som løbende:

- Sammenlign indsamlede konfigurationer med de indsamlede benchmarks for at finde forkert konfigurerede aktiver
- Knyt konfigurationer til sårbarheder, der kan afhjælpes eller afhjælpes delvist (risikoreduktion)
- Indsamle og vedligeholde benchmarks for konfiguration af bedste praksis (leverandører, sikkerhedsfeeds, interne forskningsteams)
- Indsaml og overvåg ændringer af konfigurationstilstand for sikkerhedskontrol fra alle aktiver

## <a name="improve-your-security-configuration"></a>Forbedre sikkerhedskonfigurationen

Du kan forbedre sikkerhedskonfigurationen ved at løse problemer fra listen med sikkerhedsanbefalinger. Når du gør det, forbedres din Microsoft Secure Score for Devices, og din organisation bliver mere robust over for trusler og sårbarheder i cybersikkerhed.

1. Vælg en af kategorierne på kortet Microsoft Secure Score for Håndtering af trusler og sikkerhedsrisici dashboard. Du får vist en liste med anbefalinger, der er relateret til den pågældende kategori. Her kommer du til siden [**med sikkerhedsanbefalinger**](tvm-security-recommendation.md) . Hvis du vil se alle sikkerhedsanbefalinger, skal du rydde søgefeltet, når du kommer til siden med sikkerhedsanbefalinger.

2. Vælg et element på listen. Pop op-panelet åbnes med oplysninger, der er relateret til anbefalingen. Vælg **Afhjælpningsindstillinger**.

   :::image type="content" alt-text="Sikkerhedskontrolelementer relaterede sikkerhedsanbefalinger." source="images/security-controls.png":::

3. Læs beskrivelsen for at forstå konteksten for problemet, og hvad du så skal gøre. Vælg en forfaldsdato, tilføj noter, og vælg Eksportér alle afhjælpningsaktivitetsdata til **CSV,så** du kan vedhæfte den til en mail til opfølgning.

4. **Indsend anmodning**. Du får vist en bekræftelsesmeddelelse om, at afhjælpningsopgaven er blevet oprettet.

   :::image type="content" alt-text="Bekræftelse af afhjælpning af opgaveoprettelse." source="images/remediation-task-created.png":::

5. Gem CSV-filen.

   :::image type="content" alt-text="Gem CSV-fil." source="images/tvm_save_csv_file.png":::

6. Send en opfølgende mail til din it-administrator, og giv den tid, du har tildelt til afhjælpningen, til at blive overført i systemet.

7. Gennemse kortet **Microsoft Secure Score for Devices** igen på dashboardet. Antallet af anbefalinger til sikkerhedskontrolelementer mindskes. Når du vælger **Sikkerhedskontrolelementer** for at gå tilbage til  siden med sikkerhedsanbefalinger, vises det element, du har behandlet, ikke længere på listen. Din Microsoft Secure Score til enheder bør blive større.

> [!IMPORTANT]
>For at øge registreringsfrekvensen for sikkerhedsrisikoen skal du downloade følgende obligatoriske sikkerhedsopdateringer og udrulle dem i dit netværk:
>
> - 19H1-kunder | [KB 4512941](https://support.microsoft.com/help/4512941/windows-10-update-kb4512941)
> - RS5-kunder | [KB 4516077](https://support.microsoft.com/help/4516077/windows-10-update-kb4516077)
> - RS4-kunder | [KB 4516045](https://support.microsoft.com/help/4516045/windows-10-update-kb4516045)
> - RS3-kunder | [KB 4516071](https://support.microsoft.com/help/4516071/windows-10-update-kb4516071)
>
> Sådan hentes sikkerhedsopdateringerne:
>
> 1. Gå til [Microsoft Update-katalog](https://www.catalog.update.microsoft.com/home.aspx).
> 2. Nøgle i sikkerhedsopdateringens KB-nummer, som du skal downloade, og klik derefter på **Søg**.

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over trusler håndtering af sikkerhedsrisici sikkerhed](next-gen-threat-and-vuln-mgt.md)
- [Dashboard](tvm-dashboard-insights.md)
- [Eksponeringsscore](tvm-exposure-score.md)
- [Sikkerhedsanbefalinger](tvm-security-recommendation.md)
