---
title: Administrer dit skema for nøjagtige datamatch
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du redigerer eller fjerner det nøjagtige skema til datamatch.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 29cfefbd6bf9bb9f92fe5ed7664575ec75adfa12
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014668"
---
# <a name="manage-your-exact-data-match-schema"></a>Administrer dit skema for nøjagtige datamatch

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

## <a name="editing-the-schema-for-edm-based-classification-manually"></a>Redigere skemaet for EDM-baseret klassificering manuelt

Hvis du vil foretage ændringer i EDM-skemaet, f.eks. **filenedm.xml** , f.eks. ændre, hvilke felter der bruges til EDM-baseret klassificering, skal du følge disse trin:

> [!TIP]
> Du kan ændre EDM-skemaet og kildefilen til tabellen med følsomme oplysninger for at drage fordel af **det match, der kan konfigureres**. Når EDM er konfigureret, ignoreres forskel på store og små bogstaver og nogle afgrænsere, når et element evalueres. Det gør det nemmere at definere xml-skemaet og dine følsomme datafiler. Hvis du vil vide mere, skal [du se Brug af felterne Store og små bogstaver Og Ignorerafgrænsere](sit-get-started-exact-data-match-create-schema.md#using-the-caseinsensitive-and-ignoreddelimiters-fields).

1. Rediger din **edm.xml-fil** (dette er den fil, der er beskrevet i [Opret skemaet til præcise datamatchbaserede typer følsomme oplysninger](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types).

2. [Forbind til PowerShell til sikkerhed & overholdelse af angivne standarder](/powershell/exchange/connect-to-scc-powershell).

3. Kør følgende kommando for at opdatere databaseskemaet:

      ```powershell
      Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
      ```

      Du bliver bedt om at bekræfte følgende:

      > Bekræfte
      >
      > Er du sikker på, at du vil udføre denne handling?
      >
      > EDM-skemaet for datalageret 'patientrecords' opdateres.
      >
      > \[Y Ja et ja til alle \[N\] Nej \[L\] Nej til alle\[?\]\] \[\] Hjælp (standard er "Y"):

      > [!TIP]
      > Hvis dine ændringer skal ske uden bekræftelse, skal du ikke bruge `-Confirm:$true` i trin 3.

      > [!NOTE]
      > Det kan tage mellem 10-60 minutter at opdatere EDMSchema med tilføjelser. Opdateringen skal fuldføres, før du udfører trin, der bruger tilføjelserne.

## <a name="removing-the-schema-for-edm-based-classification-manually"></a>Fjernelse af skemaet for EDM-baseret klassificering manuelt

Hvis du vil fjerne det skema, du bruger til EDM-baseret klassificering, skal du følge disse trin:

1. [Forbind til PowerShell til sikkerhed & overholdelse af angivne standarder](/powershell/exchange/connect-to-scc-powershell).

2. Kør følgende kommando, hvor navnet på datalageret for "patientjournaler" erstattes med det, du vil fjerne (ved hjælp af patientpostlageret som eksempel):

      ```powershell
      Remove-DlpEdmSchema -Identity 'patientrecords'
      ```

      Du bliver bedt om at bekræfte:

      > Bekræfte
      >
      > Er du sikker på, at du vil udføre denne handling?
      >
      > EDM-skemaet for datalageret 'patientrecords' fjernes.
      >
      > \[Y Ja et ja til alle \[N\] Nej \[L\] Nej til alle\[?\]\] \[\] Hjælp (standard er "Y"):

      > [!TIP]
      > Hvis dine ændringer skal ske uden bekræftelse, skal du ikke bruge `-Confirm:$true` i trin 2.

### <a name="edit-or-delete-the-edm-schema-with-the-wizard"></a>Rediger eller slet EDM-skemaet med guiden

1. Open **Compliance Center** \> **Dataklassificering** \> **Præcise dataforekomster**.

2. Vælg **EDM-skemaer**.

3. Vælg det EDM SIT, du vil redigere.

4. Vælg **Rediger EDM-skema** eller **Slet EDM-skema** i pop op-vinduet.

> [!IMPORTANT]
> Hvis du vil fjerne et skema, og det allerede er knyttet til en EDM-følsom infotype, skal du først slette typen af følsomme EDM-oplysninger, så kan du slette skemaet.
