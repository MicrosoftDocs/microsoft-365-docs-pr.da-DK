---
title: Oversigt
description: Om testbasen
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 13eaea1e62dd030f86e08d885ad743d673d6142c
ms.sourcegitcommit: b16520d8bfe04b29274f7a129d90ef116bb77f69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/05/2022
ms.locfileid: "65231687"
---
# <a name="what-is-test-base-for-microsoft-365"></a>Hvad er testbase for Microsoft 365?

Test Base er en Azure-tjeneste, der muliggør test af datadrevne programmer, samtidig med at brugeren får adgang til intelligent test overalt i verden.

Følgende enheder opfordres til at onboarde deres programmer, binære filer og testscripts i testbasen for Microsoft 365-tjenesten: UAFHÆNGIGE softwareleverandører (ISV'er), systemintegratorer (SIs) for at validere deres programmer og it-teknikere, der vil validere deres line of business-programmer (LOB) gennem integration med Microsoft Intune.

## <a name="why-test-your-application-with-test-base"></a>Hvorfor teste dit program med testbasen?

Testbasen for Microsoft 365-tjenesten kan imødekomme udvidelsen af din testmatrix efter behov, så du har tillid til dine programmers integritet, kompatibilitet og anvendelighed.

Testbasen gør det muligt for dit program at fortsætte med at fungere som forventet, selvom platformafhængigheder varierer, og der anvendes nye opdateringer af Windows opdateringstjenesten. Med testbasen kan du undgå forværring, langvarige tidsforpligtelser og udgifter til konfiguration og vedligeholdelse af et komplekst laboratoriemiljø til test af dine programmer.

Derudover kan du automatisk teste kompatibilitet mod sikkerheds- og funktionsopdateringer til Windows ved hjælp af sikre virtuelle maskiner (VM'er), samtidig med at du får adgang til intelligens i verdensklasse til test af dine programmer. Du kan også få dine apps testet for kompatibilitet i forhold til foreløbige windows-sikkerhedsopdateringer ved at sende en anmodning om at få adgang.

## <a name="how-does-test-base-work"></a>Hvordan fungerer testbasen?

Hvis du vil tilmelde dig testbasetjenesten, skal du se [Opret en ny testbasekonto](createAccount.md).

Når en kunde har tilmeldt sig testbasetjenesten, er det nemt at begynde at uploade programpakker til test.

Efter en vellykket upload testes pakker mod Windows foreløbige opdateringer.

Når de indledende test er fuldført, kan kunden foretage en grundig gennemgang med indsigt i ydeevne og regressionsanalyse for at registrere, om foreløbige indholdsopdateringer på nogen måde har forringet programydeevnen.

Men hvis pakken mislykkedes en test, kan kunden også udnytte Insights fra hukommelses- eller CPU-regressioner for at afhjælpe fejlen og derefter opdatere pakken efter behov.

Med Test Base kan kunden bruge en enkelt placering til at administrere alle de pakker, der testes, hvilket også kan lette upload og opdatering af pakker for at generere nye programversioner efter behov.

> [!NOTE]
> **For at kunderne kan drage fordel af indhold fra foreløbige opdateringer, skal de specifikt anmode om adgang til det. Når din anmodning om adgang til foreløbige opdateringer er godkendt, bliver dine uploadede pakker automatisk planlagt til at blive testet i forhold til den foreløbige Windows opdateringer til de operativsystemversioner, der blev valgt under onboarding**.

Når nye Windows foreløbige opdateringer bliver tilgængelige, testes programpakker automatisk med nyt foreløbig indhold. Derefter kan det være nødvendigt med en ekstra runde indsigt. Hvis kunderne ikke specifikt anmoder om adgang, bliver programpakkerne kun testet i forhold til den aktuelt udgivne version af Windows.

Når pakkerne er testet, kan kunderne levere dem til deres softwarekunder og slutbrugere med tillid og forsikringen om, at Test Base gjorde sit arbejde.

## <a name="next-steps"></a>Næste trin

Følg linket for at komme i gang
> [!div class="nextstepaction"]
> [Opret en ny testbasekonto | Microsoft Docs](createaccount.md)
