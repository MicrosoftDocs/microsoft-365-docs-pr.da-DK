---
title: Administrer det nøjagtige skema for datamatching
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
description: Få mere at vide om, hvordan du redigerer eller fjerner dit nøjagtige dataskema.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8e06cb25db0a8c616b5b692a423d9827e8918dc9
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63593636"
---
# <a name="manage-your-exact-data-match-schema"></a>Administrer det nøjagtige skema for datamatching

## <a name="editing-the-schema-for-edm-based-classification-manually"></a>Redigere skemaet for EDM-baseret klassificering manuelt

Hvis du vil foretage ændringer i dit EDM-skema, f.eks. **edm.xml-filen** , f.eks. ændre, hvilke felter der bruges til EDM-baseret klassificering, skal du følge disse trin:

> [!TIP]
> Du kan ændre dit EDM-skema og din tabelkildefil med følsomme oplysninger for at drage fordel af **et match, der kan konfigureres**. Når det er konfigureret, ignorerer EDM forskelle mellem store og små bogstaver og nogle separatortegn, når et element evalueres. Det gør det nemmere at definere xml-skemaet og dine følsomme datafiler. Du kan få mere at vide [ved at bruge felterne CaseInsensitive og ignoredDelimiters](sit-get-started-exact-data-match-create-schema.md#using-the-caseinsensitive-and-ignoreddelimiters-fields).

1. Rediger din **edm.xml** fil (dette er den fil, der er nævnt i Opret skemaet [for nøjagtige datamatchingbaserede følsomme oplysningstyper](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types).

2. [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

3. Hvis du vil opdatere databaseskemaet, skal du køre følgende kommando:

      ```powershell
      Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
      ```

      Du bliver bedt om at bekræfte på følgende måde:

      > Bekræft
      >
      > Er du sikker på, at du vil udføre denne handling?
      >
      > EDM-skema for datalageret "patientpost" opdateres.
      >
      > \[Y Ja A Ja til alle \[N\] Nej \[L\] nej til alle\[?\]\] \[\] Hjælp (standard er "Y"):

      > [!TIP]
      > Hvis du vil have dine ændringer til at ske uden bekræftelse, skal du ikke `-Confirm:$true` bruge i trin 3.

      > [!NOTE]
      > Det kan tage mellem 10-60 minutter at opdatere EDMSchema med tilføjelser. Opdateringen skal udføres, før du udfører trin, der bruger tilføjelserne.

## <a name="removing-the-schema-for-edm-based-classification-manually"></a>Fjerne skemaet for EDM-baseret klassificering manuelt

Hvis du vil fjerne det skema, du bruger til EDM-baseret klassificering, skal du følge disse trin:

1. [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Kør følgende kommando, hvor du erstatter navnet på datalageret med navnet på "patientjournaler" med den, du vil fjerne (med patientpostlageret som eksempel):

      ```powershell
      Remove-DlpEdmSchema -Identity 'patientrecords'
      ```

      Du bliver bedt om at bekræfte:

      > Bekræft
      >
      > Er du sikker på, at du vil udføre denne handling?
      >
      > EDM-skema for datalageret "patientpost" fjernes.
      >
      > \[Y Ja A Ja til alle \[N\] Nej \[L\] nej til alle\[?\]\] \[\] Hjælp (standard er "Y"):

      > [!TIP]
      > Hvis du ønsker, at dine ændringer skal ske uden bekræftelse, skal du ikke bruge `-Confirm:$true` i trin 2.

### <a name="edit-or-delete-the-edm-schema-with-the-wizard"></a>Rediger eller slet EDM-skemaet med guiden

1. Åbn **Overholdelsescenter** **Dataklassificering** \> nøjagtige \> **dataoverensstemmelser**.

2. Vælg **EDM-skemaer**.

3. Vælg den EDM SIT, du vil redigere.

4. Vælg **Rediger EDM-skema** **eller Slet EDM-skema** i pop op-menuen.

> [!IMPORTANT]
> Hvis du vil fjerne et skema, og det allerede er knyttet til en EDM-følsom oplysningstype, skal du først slette den følsomme EDM-infotype, og derefter kan du slette skemaet.
