---
title: Rapport over følsomme enheder – Håndtering af trusler og sikkerhedsrisici
description: En rapport, der viser følsomme enhedstendenser og aktuel statistik. Målet er at få et godt forhold til, hvor meget din enheds eksponering trækkes tilbage.
keywords: Microsoft Defender til endpoint-tvm-følsomme enheder, Microsoft Defender til slutpunkt, tvm, reducere trussel & eksponering af sikkerhedsrisikoen, reducere trussel og sikkerhedsrisiko, overvåge sikkerhedskonfiguration
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 50b30d38a42aab37c295a9f65bd070dd9613927c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591227"
---
# <a name="vulnerable-devices-report---threat-and-vulnerability-management"></a>Rapport over følsomme enheder – Håndtering af trusler og sikkerhedsrisici

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Rapporten viser grafer og liggende søjlediagrammer med følsomme enhedstendenser og aktuel statistik. Målet er at få et godt forhold til, hvor meget din enheds eksponering trækkes tilbage.

Få adgang til rapporten i Microsoft 365 Defender ved at gå **til Rapporter > følsomme enheder**

Der er to kolonner:

- Tendenser (over tid). Kan vise de seneste 30 dage, 3 måneder, 6 måneder eller et brugerdefineret datointerval.
- Status (aktuelle oplysninger)

**Filter**: Du kan filtrere dataene efter alvorlighedsniveauet for sikkerhedsrisikoen, udnyttelsestilgængeligheden, sikkerhedsrisikoens alder, operativsystemplatform, Windows 10 eller Windows 11-version eller enhedsgruppe.

**Analyser** ned: Hvis der er et indsigt, du vil udforske yderligere, kan du vælge det relevante liggende søjlediagram for at få vist en filtreret liste over enheder på lagersiden for enheder. Derfra kan du eksportere listen.

## <a name="severity-level-graphs"></a>Grafer på alvorsniveau

Hver enhed tælles kun én gang i overensstemmelse med den mest alvorlige sikkerhedsrisiko på den pågældende enhed.

:::image type="content" alt-text="En graf over de aktuelle alvorsniveauer for enheders sikkerhedsrisiko og en graf, der viser niveauer over tid." source="images/tvm-report-severity.png" lightbox="images/tvm-report-severity.png":::

## <a name="exploit-availability-graphs"></a>Grafer over udnyttelse af tilgængelighed

Hver enhed tælles kun én gang baseret på det højeste niveau af kendt udnyttelse.

:::image type="content" alt-text="En graf over aktuel tilgængelighed af enhedsudnyttelse og en graf, der viser tilgængelighed over tid." source="images/tvm-report-exploit-availability.png" lightbox="images/tvm-report-exploit-availability.png":::

## <a name="vulnerability-age-graphs"></a>Grafer over alder for sikkerhedsrisiko

Hver enhed tælles kun én gang under publiceringsdatoen for den ældste sikkerhedsrisiko. Ældre sårbarheder har større risiko for at blive udnyttet.

:::image type="content" alt-text="En graf over den aktuelle alder for sikkerhedsrisikoen og en graf, der viser alder over tid." source="images/tvm-report-age.png" lightbox="images/tvm-report-age.png":::

## <a name="vulnerable-devices-by-operating-system-platform-graphs"></a>Sårbar enheder ved hjælp af grafer fra operativsystemets platform

Antallet af enheder på hvert operativsystem, der er eksponeret på grund af softwarerisici.

:::image type="content" alt-text="En graf over nuværende følsomme enheder fra operativsystemplatformen og en graf, der viser sårbar enheder fra OS-platforme over tid." source="images/tvm-report-os.png" lightbox="images/tvm-report-os.png":::

## <a name="vulnerable-devices-by-windows-version-graphs"></a>Sårbar enheder ved Windows-versionsgrafer

Antallet af enheder på hver Windows 10 eller Windows 11-version, der er eksponeret på grund af følsomme programmer eller operativsystem.

:::image type="content" alt-text="En graf over aktuelle følsomme enheder efter Windows 10 version og en graf, der viser sårbar enheder Windows 10 en version over tid." source="images/tvm-report-version.png" lightbox="images/tvm-report-version.png":::

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over trusler håndtering af sikkerhedsrisici sikkerhed](next-gen-threat-and-vuln-mgt.md)
- [Sikkerhedsanbefalinger](tvm-security-recommendation.md)
