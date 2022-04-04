---
title: Rapport over følsomme enheder – Håndtering af trusler og sikkerhedsrisici
description: En rapport, der viser følsomme enhedstendenser og aktuel statistik. Målet er at få et godt forhold til, hvor meget din enheds eksponering trækkes tilbage.
keywords: Microsoft Defender for Endpoint-tvm-følsomme enheder, Microsoft Defender for Endpoint, tvm, reducere eksponering af trusler & sikkerhedsrisiko, reducere trusler og sikkerhedsrisiko, overvåge sikkerhedskonfiguration
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
ms.openlocfilehash: fa5280d9c6f396e8e164397210c1b58dfcfc8d9b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466713"
---
# <a name="vulnerable-devices-report---threat-and-vulnerability-management"></a>Rapport over følsomme enheder – Håndtering af trusler og sikkerhedsrisici

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Rapporten viser grafer og liggende søjlediagrammer med følsomme enhedstendenser og aktuel statistik. Målet er at få et godt forhold til, hvor meget din enheds eksponering trækkes tilbage.

Få adgang til rapporten i Microsoft 365 Defender ved at gå **til Rapporter > følsomme enheder**

Der er to kolonner:

- Tendenser (over tid). Kan vise de seneste 30 dage, 3 måneder, 6 måneder eller et brugerdefineret datointerval.
- Status (aktuelle oplysninger)

**Filter**: Du kan filtrere dataene efter alvorlighedsniveauet for sikkerhedsrisikoen, udnyttelsestilgængeligheden, sikkerhedsrisikoens alder, operativsystemplatform, Windows 10-eller Windows 11-version eller enhedsgruppe.

**Analyser** ned: Hvis der er et indsigt, du vil udforske yderligere, kan du vælge det relevante liggende søjlediagram for at få vist en filtreret liste over enheder på lagersiden for enheder. Derfra kan du eksportere listen.

## <a name="severity-level-graphs"></a>Grafer på alvorsniveau

Hver enhed tælles kun én gang i overensstemmelse med den mest alvorlige sikkerhedsrisiko på den pågældende enhed.

:::image type="content" source="images/tvm-report-severity.png" alt-text=" Graferne, der viser alvorsniveauet for de aktuelle enheders sikkerhedsrisiko og niveauerne over tid." lightbox="images/tvm-report-severity.png":::

## <a name="exploit-availability-graphs"></a>Grafer over udnyttelse af tilgængelighed

Hver enhed tælles kun én gang baseret på det højeste niveau af kendt udnyttelse.

:::image type="content" source="images/tvm-report-exploit-availability.png" alt-text="Graferne, der viser den aktuelle tilgængelighed af enheds udnyttelse, og tilgængeligheden over tid" lightbox="images/tvm-report-exploit-availability.png":::

## <a name="vulnerability-age-graphs"></a>Grafer over alder for sikkerhedsrisiko

Hver enhed tælles kun én gang under publiceringsdatoen for den ældste sikkerhedsrisiko. Ældre sårbarheder har større risiko for at blive udnyttet.

:::image type="content" source="images/tvm-report-age.png" alt-text="Graferne, der viser den aktuelle alder for sikkerhedsrisikoen og alderen over tid" lightbox="images/tvm-report-age.png":::

## <a name="vulnerable-devices-by-operating-system-platform-graphs"></a>Sårbar enheder ved hjælp af grafer fra operativsystemets platform

Antallet af enheder på hvert operativsystem, der er eksponeret på grund af softwarerisici.

:::image type="content" source="images/tvm-report-os.png" alt-text="Graferne, der viser de aktuelle følsomme enheder via operativsystemplatformen og de følsomme enheder fra OS-platforme over tid" lightbox="images/tvm-report-os.png":::

## <a name="vulnerable-devices-by-windows-version-graphs"></a>Sårbar enheder ved Windows-versionsgrafer

Antallet af enheder på hver enkelt Windows 10 eller Windows 11, der er eksponeret på grund af følsomme programmer eller operativsystem.

:::image type="content" source="images/tvm-report-version.png" alt-text="Graferne, der viser de aktuelle følsomme enheder Windows 10 deres version og de sårbar enheder ved Windows 10 version over tid" lightbox="images/tvm-report-version.png":::

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over trusler håndtering af sikkerhedsrisici sikkerhed](next-gen-threat-and-vuln-mgt.md)
- [Sikkerhedsanbefalinger](tvm-security-recommendation.md)
