---
title: Få vist og frigiv karantænemeddelelser fra delte postkasser
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
description: Brugerne kan få mere at vide om, hvordan de får vist og reagerer på meddelelser i karantæne, der er sendt til delte postkasser, som de har tilladelse til.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a37ed03535bd3f3b48aca81c7bf7adeb3c660b46
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629007"
---
# <a name="view-and-release-quarantined-messages-from-shared-mailboxes"></a>Få vist og frigiv karantænemeddelelser fra delte postkasser

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Brugerne kan administrere karantænemeddelelser, hvor de er en af modtagerne, som beskrevet i [Find og frigiv karantænemeddelelser som en bruger i EOP](find-and-release-quarantined-messages-as-a-user.md). Men hvad med **delte postkasser**, hvor brugeren har tilladelsen Fuld adgang og Send som eller Send på vegne af til postkassen som beskrevet i [Delte postkasser i Exchange Online](/exchange/collaboration-exo/shared-mailboxes)?

Tidligere krævede brugeres mulighed for at administrere karantænemeddelelser, der sendes til en delt postkasse, at administratorer skulle lade automatisk konfiguration være aktiveret for den delte postkasse (den er som standard aktiveret, når en administrator giver en bruger adgang til en anden postkasse). Afhængigt af størrelsen og antallet af postkasser, som brugeren har adgang til, kan ydeevnen dog blive forringet, da Outlooks forsøger at åbne _alle_ postkasser, som brugeren har adgang til. Derfor vælger mange administratorer at [fjerne automapping for delte postkasser](/outlook/troubleshoot/profiles-and-accounts/remove-automapping-for-shared-mailbox).

Automapping er nu ikke længere påkrævet, for at brugerne kan administrere karantænemeddelelser, der blev sendt til delte postkasser. Det virker bare. Der er to forskellige metoder til at få adgang til karantænemeddelelser, der er sendt til en delt postkasse:

- Hvis administratoren har konfigureret [karantænepolitikker](quarantine-policies.md) for at tillade karantænemeddelelser (tidligere kaldet slutbrugermails om spam), kan alle brugere, der har adgang til karantænemeddelelserne i den delte postkasse, klikke på knappen **Gennemse** i meddelelsen for at gå i karantæne på Microsoft 365 Defender-portalen. Bemærk, at denne metode kun giver brugerne mulighed for at administrere karantænemeddelelser, der er sendt til den delte postkasse. Brugerne kan ikke administrere deres egne karantænemeddelelser i denne kontekst.
- Brugeren kan [gå i karantæne på Microsoft 365 Defender-portalen](find-and-release-quarantined-messages-as-a-user.md) og klikke på **Filter** for at filtrere resultaterne efter **modtageradresse** (mailadressen på den delte postkasse). På hovedsiden **Karantæne** kan du klikke på kolonnen **Modtager** for at sortere efter meddelelser, der er sendt til den delte postkasse.

## <a name="things-to-keep-in-mind"></a>Ting, du skal være opmærksom på

- _Karantænepolitikker_ definerer, hvad brugerne har tilladelse til at gøre eller ikke gøre for at sætte meddelelser i karantæne, afhængigt af hvorfor meddelelsen blev sat i karantæne (for understøttede funktioner). Standard karantænepolitikker gennemtvinger de historiske funktioner, der gør det muligt for modtagerne at få vist og reagere på meddelelser. Administratorer kan oprette og anvende brugerdefinerede karantænepolitikker, der definerer mindre restriktive eller mere restriktive egenskaber for brugerne. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).

- Den første bruger, der reagerer på den karantænerede meddelelse, bestemmer meddelelsens skæbne for alle, der bruger den delte postkasse. Hvis en delt postkasse f.eks. tilgås af 10 brugere, og en bruger beslutter at slette karantænemeddelelsen, slettes meddelelsen for alle 10 brugere. Hvis en bruger på samme måde beslutter at udgive meddelelsen, frigives den til den delte postkasse og er tilgængelig for alle andre brugere af den delte postkasse.

- Knappen **Bloker afsender** er i øjeblikket ikke tilgængelig i pop op-vinduet **Detaljer** for karantænemeddelelser, der blev sendt til den delte postkasse.

- Hvad angår karantænehandlinger for delte postkasser, anbefaler vi ikke mere end to niveauer af indlejrede grupper, hvis du bruger indlejrede sikkerhedsgrupper til at give adgang til en delt postkasse. Gruppe A er f.eks. medlem af Gruppe B, som er medlem af Gruppe C. Hvis du vil tildele tilladelser til en delt postkasse, skal du ikke føje brugeren til Gruppe A og derefter tildele Gruppe C til den delte postkasse.

- Fra og med juli 2022 bør brugere med primære SMTP-adresser, der er forskellige fra deres UPN'er (user principal names), kunne få adgang til karantænemeddelelser for den delte postkasse.

- Hvis du vil administrere meddelelser i karantæne for den delte postkasse i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), skal slutbrugeren bruge cmdlet'en [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage) med delt postkassemailadresse til værdien af parameteren _RecipientAddress_ til at identificere meddelelserne. Eksempel:

  ```powershell
  Get-QuarantineMessage -RecipientAddress officeparty@contoso.com
  ```

  Slutbrugeren kan derefter vælge en meddelelse i karantæne på listen, der skal vises eller udføres handlinger på.

  I dette eksempel vises alle de karantænemeddelelser, der er sendt til den delte postkasse, og derefter frigives den første meddelelse på listen fra karantæne (den første meddelelse på listen er 0, den anden er 1 osv.).

  ```powershell
  $SharedMessages = Get-QuarantineMessage -RecipientAddress officeparty@contoso.com | select -ExpandProperty Identity
  $SharedMessages
  Release-QuarantineMessage -Identity $SharedMessages[0]
  ```

  Du kan finde detaljerede oplysninger om syntaks og parametre i følgende emner:

  - [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)
  - [Get-QuarantineMessageHeader](/powershell/module/exchange/get-quarantinemessageheader)
  - [Eksempel på karantænemeddelelse](/powershell/module/exchange/preview-quarantinemessage)
  - [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)
