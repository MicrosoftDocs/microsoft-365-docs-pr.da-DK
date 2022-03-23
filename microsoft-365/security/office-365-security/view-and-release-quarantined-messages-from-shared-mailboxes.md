---
title: Få vist og frigive meddelelser, der er sat i karantæne, fra delte postkasser
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ROBOTS: NOINDEX
description: Brugerne kan få mere at vide om, hvordan de får vist og reagerer på meddelelser, der er sat i karantæne, og som blev sendt til delte postkasser, de har tilladelser til.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3f136f373fa63be7dab6cfbd63e44b33b4eca2ff
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/12/2022
ms.locfileid: "63590484"
---
# <a name="view-and-release-quarantined-messages-from-shared-mailboxes"></a>Få vist og frigive meddelelser, der er sat i karantæne, fra delte postkasser

Brugere kan administrere meddelelser, der er sat i karantæne, hvor de er en af modtagerne, som beskrevet i Finde og frigive meddelelser, der er sat i karantæne, som [en bruger i EOP](find-and-release-quarantined-messages-as-a-user.md). Men hvad med **delte postkasser**, hvor brugeren har tilladelserne Fuld adgang og Send som eller Send på vegne af til postkassen som beskrevet i Delte postkasser [i Exchange Online](/exchange/collaboration-exo/shared-mailboxes)?

Tidligere var brugernes mulighed for at administrere meddelelser, der er sat i karantæne, og som blev sendt til en delt postkasse, påkrævet, at administratorer lader automapping være aktiveret for den delte postkasse (den er aktiveret som standard, når en administrator giver en bruger adgang til en anden postkasse). Men afhængigt af størrelsen og antallet af postkasser, som brugeren har adgang til, kan det gå ud over ydeevnen, når Outlook forsøger  at åbne alle postkasser, som brugeren har adgang til. Derfor vælger mange administratorer at fjerne [automapping for delte postkasser](/outlook/troubleshoot/profiles-and-accounts/remove-automapping-for-shared-mailbox).

Nu kræves der ikke længere automapping, for at brugerne kan administrere meddelelser, der er i karantæne, som blev sendt til delte postkasser. Det fungerer bare. Der er to forskellige metoder til at få adgang til meddelelser, der er sat i karantæne, som blev sendt til en delt postkasse:

- Hvis administratoren har konfigureret karantænepolitikker for at tillade beskeder om karantæne (tidligere kaldet beskeder om spam til slutbrugeren), kan alle brugere, der har adgang til meddelelser i karantæne i den delte postkasse,  klikke på knappen Gennemse i meddelelsen for at gå til karantæne i Microsoft 365 Defender-portalen.[](quarantine-policies.md) Bemærk, at denne metode kun giver brugerne mulighed for at administrere meddelelser, der er sat i karantæne, som blev sendt til den delte postkasse. Brugerne kan ikke administrere deres egne meddelelser i karantæne i denne kontekst.
- Brugeren kan gå [til karantæne i Microsoft 365 Defender-portalen](find-and-release-quarantined-messages-as-a-user.md) og klikke på **Filtrer** for at filtrere resultaterne efter Modtageradresse **(** mailadressen til den delte postkasse). På hovedsiden **Karantæne** kan du klikke på kolonnen Modtager for at **sortere efter meddelelser** , der blev sendt til den delte postkasse.

## <a name="things-to-keep-in-mind"></a>Ting, du skal huske

- _Karantænepolitikker_ definerer, hvad brugerne har tilladelse til at gøre eller ikke må til meddelelser, der er sat i karantæne, baseret på, hvorfor meddelelsen var sat i karantæne (for understøttede funktioner). Standardkarantænepolitikker gennemtvinger de historiske funktioner, der giver modtagerne mulighed for at få vist og handle på meddelelser. Administratorer kan oprette og anvende brugerdefinerede karantænepolitikker, der definerer mindre restriktive eller mere restriktive funktioner for brugerne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).

- Den første bruger, der skal handle på meddelelsen, der er sat i karantæne, bestemmer meddelelsens stilling for alle, der bruger den delte postkasse. Hvis f.eks. 10 brugere tilgås af en delt postkasse, og en bruger beslutter sig for at slette karantænemeddelelsen, slettes meddelelsen for alle 10 brugere. Hvis en bruger beslutter at frigive meddelelsen, frigives den til den delte postkasse og er tilgængelig for alle andre brugere af den delte postkasse.

- I øjeblikket er **knappen Bloker** afsender ikke tilgængelig i pop op-pop-op-pop-op-filen Detaljer for meddelelser, der er sat i karantæne, som blev sendt til den delte postkasse.

- I forbindelse med karantænehandlinger for delte postkasser anbefaler vi, at du ikke bruger mere end to niveauer af indlejrede grupper, hvis du bruger indlejrede sikkerhedsgrupper til at give adgang til en delt postkasse. Gruppe A er f.eks. medlem af gruppe B, som er medlem af Gruppe C. Hvis du vil tildele tilladelser til en delt postkasse, skal du ikke føje brugeren til Gruppe A og derefter tildele Gruppe C til den delte postkasse.  

- For at administrere meddelelser, der er sat i karantæne for den delte postkasse [i Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), skal slutbrugeren bruge [Get-QuarantineMessage-cmdlet'en](/powershell/module/exchange/get-quarantinemessage) med den delte postkasses mailadresse til værdien af _parameteren RecipientAddress_ til at identificere meddelelserne. Eksempel:

  ```powershell
  Get-QuarantineMessage -RecipientAddress officeparty@contoso.com
  ```

  Derefter kan slutbrugeren vælge en meddelelse, der er sat i karantæne, på listen for at få vist eller handle på den.

  I dette eksempel vises alle de meddelelser, der er sat i karantæne, som blev sendt til den delte postkasse, og den første meddelelse på listen frigives fra karantæne (den første meddelelse på listen er 0, den anden er 1 og så videre).

  ```powershell
  $SharedMessages = Get-QuarantineMessage -RecipientAddress officeparty@contoso.com | select -ExpandProperty Identity
  $SharedMessages
  Release-QuarantineMessage -Identity $SharedMessages[0]
  ```

  Du kan finde detaljerede oplysninger om syntaks og parameter i følgende emner:

  - [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)
  - [Get-QuarantineMessageHeader](/powershell/module/exchange/get-quarantinemessageheader)
  - [Preview-QuarantineMessage](/powershell/module/exchange/preview-quarantinemessage)
  - [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)
