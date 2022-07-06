---
title: Få mere at vide om inaktive postkasser
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 1fbd74e8-7a60-4157-afe8-fe79f05d2038
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du bevarer postkasseindhold for tidligere medarbejdere ved at gøre postkassen til en inaktiv postkasse.
ms.openlocfilehash: 981675f64015e0320805e2be8e955cbd6d98769a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627211"
---
# <a name="learn-about-inactive-mailboxes"></a>Få mere at vide om inaktive postkasser

Din organisation skal muligvis bevare tidligere medarbejderes mail, når de forlader organisationen. Afhængigt af din organisations opbevaringskrav skal du muligvis bevare postkasseindholdet i et par måneder eller år, efter ansættelsen er afsluttet, eller du skal muligvis bevare postkasseindholdet på ubestemt tid. Uanset hvor længe du har brug for at bevare mails, kan du oprette inaktive postkasser for at bevare tidligere medarbejderes postkasse.

## <a name="what-are-inactive-mailboxes"></a>Hvad er inaktive postkasser?

Når en medarbejder forlader organisationen (eller går på en udvidet orlov), kan du fjerne vedkommendes Microsoft 365-konto. Medarbejderens postkassedata opbevares i 30 dage, efter at kontoen er fjernet. I denne periode kan du stadig gendanne postkassedataene ved at slette kontoen. Efter 30 dage fjernes dataene permanent.

Men hvis der anvendes venteposition på postkassen, før du sletter Microsoft 365-kontoen, konverteres postkassen til en inaktiv postkasse. De følgende afsnit indeholder oplysninger om ventepositioner, der kan anvendes med Microsoft 365-opbevaring og eDiscovery-ventepositioner.

Inaktive postkasser er nyttige, når din organisation skal bevare postkasseindhold fra tidligere medarbejdere af lovmæssige eller andre årsager. Selvom enhver type venteposition, der er angivet i dette dokument, vil tvinge en postkasse til at blive gjort inaktiv, når et brugerobjekt slettes, anbefaler vi, at du gør dette ved at anvende en Microsoft 365-opbevaringspolitik eller opbevaringsbeskrivelser, [bekræfte, at ventepositionen er anvendt](#confirming-a-hold-is-applied-to-a-mailbox), og derefter fjerne den tilsvarende Microsoft 365-konto. På det tidspunkt bevares indholdet af den inaktive postkasse i varigheden af den opbevaringsperiode, der blev angivet, før brugerkontoen blev slettet. Du kan stadig gendanne den tilsvarende brugerkonto i en 30-dages periode, men efter 30 dage bevares postkassen i Microsoft 365 som en inaktiv postkasse, indtil opbevaringspolitikken eller opbevaringsmærkater fjernes.

> [!IMPORTANT]
> Som tidligere nævnt anbefaler vi, at du bruger Microsoft 365-opbevaring til at oprette en inaktiv postkasse:
> - In-Place Ventepositioner i Exchange Administration udgår nu. Fra den 1. juli 2020 kunne nye In-Place Ventepositioner ikke oprettes i Exchange Online. Fra den 1. oktober 2020 kunne varigheden af bevarelse på stedet ikke længere ændres. Alle inaktive postkasser, hvor der er anvendt en In-Place venteposition, kan kun slettes ved at fjerne In-Place Venteposition. Eksisterende inaktive postkasser, der er på In-Place venteposition, bevares fortsat, indtil ventepositionen fjernes. Du kan finde flere oplysninger om, In-Place ventepositioner udgår, under [Udfasning af ældre eDiscovery-værktøjer](legacy-ediscovery-retirement.md).
> 
> - [Procesførelse i venteposition](create-a-litigation-hold.md) understøttes fortsat som en alternativ metode til at bevare indhold i en postkasse og gøre det inaktivt, når en brugerkonto er slettet. Men som en ældre teknologi anbefaler vi, at du bruger Microsoft 365-opbevaring i stedet.

Når der er flere ventepositioner på det samme indhold, [gælder princippet om opbevaring](retention.md#the-principles-of-retention-or-what-takes-precedence) , og indholdet bevares i den længste periode.

### <a name="confirming-a-hold-is-applied-to-a-mailbox"></a>Bekræftelse af en venteposition anvendes på en postkasse

Uanset om du anvender en Microsoft 365-opbevaringspolitik, opbevaringsmærkater, eDiscovery-venteposition, procesførelse eller har en eksisterende In-Place venteposition, kan du bekræfte, at ventepositionen er anvendt på postkassen ved hjælp af PowerShell. Hvis du for nylig har konfigureret ventepositionen, skal du muligvis vente, indtil den anvendes på postkassen.

Hvis du vil forhindre utilsigtet eller utilsigtet sletning, anbefaler vi, at du bekræfter ventepositionen, før du sletter brugerkontoen. Hvis ventepositionen ikke anvendes, konverteres postkassen ikke til en inaktiv postkasse.

Du kan finde instruktioner under [Sådan identificerer du den type venteposition, der er placeret i en Exchange Online postkasse](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="inactive-mailboxes-and-microsoft-365-retention"></a>Inaktive postkasser og Microsoft 365-opbevaring

Hvis der anvendes en Microsoft 365-opbevaringspolitik på en postkasse, eller hvis der er anvendt en opbevaringsmærkat for et eller flere mailelementer i en postkasse, og Microsoft 365-brugerkontoen slettes, konverteres postkassen til en inaktiv postkasse. Sådan oprettes den inaktive postkasse:

- Opbevaringsindstillingerne skal konfigureres til at [bevare indhold eller bevare og derefter slette indhold](retention-settings.md#settings-for-retaining-and-deleting-content). Hvis opbevaringshandlingen er konfigureret til kun at slette indhold, bliver postkassen ikke inaktiv, når brugerkontoen slettes. I forbindelse med inaktive postkasser anbefaler vi, at du bruger indstillingen Bevar og slet.

- Opbevaringsindstillingerne skal anvendes på en [opbevaringsplacering](retention-settings.md#locations) , der er knyttet til en Exchange-postkasse:
    - Exchange-mail
    - Microsoft 365-grupper
    - Skype for Business
    - Offentlige Exchange-mapper
    - Teams-kanalmeddelelser
    - Teams-chats
    - Teams-meddelelser om privat kanal
    - Yammer-communitymeddelelser
    - Yammer-brugermeddelelser

Du kan finde flere oplysninger om Microsoft-opbevaring under [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md).

Hvis Microsoft 365-opbevaring bruges til at oprette en inaktiv postkasse, gælder opbevaringsindstillingerne fra opbevaringspolitikken eller opbevaringsmærkater fortsat for den inaktive postkasse. Det betyder, at hvis opbevaringsindstillingerne er konfigureret til at bevare og derefter slette indhold, flyttes elementer til mappen Gendanbare elementer, når opbevaringsvarigheden udløber og derefter fjernes fra den inaktive postkasse. Hvis opbevaringsindstillingerne ikke er konfigureret til slettede elementer, flyttes elementer, der ikke er slettet permanent af brugeren (før postkassen blev gjort inaktiv), ikke til mappen Gendanbare elementer og bevares på ubestemt tid, når postkassen bliver inaktiv.

> [!TIP]
> Du kan bruge egenskaben *ComplianceTagHoldApplied* til at identificere, om en postkasse indeholder elementer, hvor der er anvendt en eller flere opbevaringsmærkater til at bevare eller bevare og derefter slette indhold. Du kan finde flere oplysninger under [Identificere postkasser i venteposition, fordi der er anvendt en opbevaringsmærkat på en mappe eller et element](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item).

### <a name="using-adaptive-policy-scopes-to-manage-retention-of-inactive-mailboxes"></a>Brug af tilpassede politikområder til at administrere opbevaring af inaktive postkasser

Med [tilpassede politikområder](retention.md#adaptive-or-static-policy-scopes-for-retention) kan du anvende opbevaringsindstillinger specifikt på inaktive postkasser. Fordelene ved denne konfiguration omfatter:

- Du kan overholde organisationens regler eller politikker, der kræver forskellige opbevaringsperioder for aktive medarbejdere og tidligere medarbejdere.

- Du kan konfigurere opbevaringsindstillingerne for kun at bevare postkasseindhold, så længe det er nødvendigt for at opfylde organisationens krav til tidligere medarbejdere.

- Du kan hurtigt identificere politikken for opbevaring, der er tildelt til inaktive postkasser i din organisation, hvilket gør det nemmere at ændre opbevaringsindstillingerne, hvis det er nødvendigt. 

- Det er nemmere at slette en inaktiv postkasse permanent, fordi du kan fjerne den fra politikken ved [at konfigurere det tilpassede område](retention-settings.md#to-configure-an-adaptive-scope) til at udelade den, baseret på attributter eller egenskaber for den inaktive postkasse. Ellers skal du bruge [Exchange Online PowerShell](delete-an-inactive-mailbox.md#remove-an-inactive-mailbox-from-a-retention-policy), før [du sletter postkassen](delete-an-inactive-mailbox.md#before-you-delete-an-inactive-mailbox).

> [!NOTE]
> Afhængigt af konfigurationen af dit tilpassede politikområde er inaktive postkasser muligvis eller måske ikke inkluderet.  Hvis du specifikt vil målrette eller udelade inaktive postkasser fra et tilpasset politikområde, skal du se [konfigurationsoplysninger for offentlige Exchange-mailmapper og Exchange-mapper](retention-settings.md#locations).

### <a name="using-static-policy-scopes-and-inactive-mailboxes"></a>Brug af statiske politikområder og inaktive postkasser

Hvis du ikke bruger [tilpassede politikområder](retention.md#adaptive-or-static-policy-scopes-for-retention) med Microsoft 365-opbevaring og i stedet bruger et [statisk område](retention.md#adaptive-or-static-policy-scopes-for-retention), skal du overveje følgende:

- Statiske politikområder omfatter inaktive postkasser, når du bruger standardkonfigurationen **Alle modtagere** , men ikke understøttes for [bestemte medtagelser eller udeladelser](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions). Men hvis du medtager eller udelukker en modtager, der har en aktiv postkasse på det tidspunkt, hvor politikken anvendes, og postkassen senere bliver inaktiv, anvendes eller udelades opbevaringsindstillingerne fortsat. I dette scenarie gælder [der stadig specifikke begrænsninger for medtagelse og udelukkelse](retention-limits.md) .
    
    > [!NOTE]
    > Det betyder også, at alle nye Indstillinger for Microsoft 365-opbevaring ved hjælp af et statisk område, der anvendes på standardvalget af **Alle modtagere** , automatisk inkluderer alle eksisterende inaktive postkasser.

- Hvis du ændrer standardvalget for **Alle modtagere** til at omfatte bestemte modtagere, gælder opbevaringsindstillingerne for politikken ikke længere for nogen inaktive postkasser, som nu er berettiget til automatisk sletning.

- Hvis du vil frigive en opbevaringspolitik, der anvendes på en inaktiv postkasse, skal du se [Frigivelse af en politik til opbevaring](retention.md#releasing-a-policy-for-retention).

> [!CAUTION]
> Når du bruger Microsoft 365-opbevaring til at gøre en postkasse inaktiv, skal du ikke ændre eller fjerne brugerens hovednavn (UPN) for postkassen, før du sletter den tilsvarende brugerkonto. Du skal heller ikke ændre den primære SMTP-adresse (der er afledt af UPN) eller fjerne denne mailadresse fra listen over sekundære SMTP-adresser, der er knyttet til postkassen, før du gør postkassen inaktiv.
> 
> Hvis du ændrer UPN'et eller mailadresserne (som blev tildelt til postkassen på det tidspunkt, hvor opbevaringsindstillingerne blev anvendt) og derefter sletter brugerkontoen for at gøre postkassen inaktiv, kan du ikke slette den inaktive postkasse, hvis du ikke længere har brug for at beholde den. Det skyldes, at du ikke kan fjerne den inaktive postkasse fra politikken ved hjælp af et UPN eller en mailadresse (til at identificere den inaktive postkasse), der er forskellig fra dem, der fandtes, da opbevaringsindstillingerne oprindeligt blev anvendt på postkassen. Du kan få flere oplysninger om sletning af inaktive postkasser [under Slet en inaktiv postkasse i Office 365](delete-an-inactive-mailbox.md).

## <a name="inactive-mailboxes-and-ediscovery-case-holds"></a>Inaktive postkasser og ventepositioner for eDiscovery-sager

Hvis en venteposition, der er knyttet til en [eDiscovery-sag](./get-started-core-ediscovery.md) i Microsoft Purview-compliance-portal placeres i en postkasse, og derefter postkassen eller brugerens konto slettes, bliver postkassen en inaktiv postkasse. Vi anbefaler dog ikke, at du bruger eDiscovery-sagsbevaring til at gøre en postkasse inaktiv. Det skyldes, at eDiscovery-sager er beregnet til specifikke, tidsbundne sager, der er relateret til et juridisk problem. På et tidspunkt slutter en juridisk sag sandsynligvis, og de ventepositioner, der er knyttet til sagen, fjernes, og eDiscovery-sagen lukkes. Hvis en venteposition, der er placeret i en inaktiv postkasse, er knyttet til en eDiscovery-sag, og ventepositionen frigives, eller eDiscovery-sagen lukkes (eller slettes), slettes den inaktive postkasse permanent. Du kan heller ikke oprette en tidsbaseret eDiscovery-venteposition. Det betyder, at indhold i en inaktiv postkasse bevares for evigt, eller indtil ventepositionen fjernes, og den inaktive postkasse slettes. Derfor anbefaler vi, at du bruger Microsoft 365-opbevaring til inaktive postkasser.

Du kan finde flere oplysninger om forskellene mellem eDiscovery-ventepositioner og Microsoft 365-opbevaring under [Hvornår skal du bruge opbevaringspolitikker og opbevaringsmærkater eller eDiscovery-ventepositioner](retention.md#when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds)?

## <a name="inactive-mailboxes-and-auto-expanding-archives"></a>Inaktive postkasser og arkiver, der automatisk udvides

En inaktiv postkasse, der er konfigureret med et arkiv til automatisk udvidelse, kan ikke gendannes eller gendannes. I situationer, hvor det er nødvendigt at gendanne data fra en inaktiv postkasse med et arkiv, der automatisk udvides, anbefales det, at du bruger værktøjet til indholdssøgning til at eksportere dataene fra postkassen og derefter importere dem til en anden postkasse. Hvis du vil have en trinvis vejledning til at søge i en inaktiv postkasse og eksportere søgeresultaterne, skal du se:

- [Indholdssøgning](content-search.md)

- [Eksportér resultater af indholdssøgning](export-search-results.md)

## <a name="inactive-mailboxes-and-exchange-mrm-retention-policies"></a>Inaktive postkasser og EXCHANGE MRM-opbevaringspolitikker

Anvendelse af en Exchange-opbevaringspolitik (funktionen Administration af meddelelsesposter eller MRM i Exchange Online) opretter ikke en inaktiv postkasse, når brugerkontoen slettes.

Men hvis denne MRM-opbevaringspolitik blev anvendt på en postkasse, før den blev inaktiv, behandles alle politikker for sletning (MRM-opbevaringskoder, der er konfigureret med en **Slet-handling** ) fortsat på den inaktive postkasse. Det betyder, at elementer, der er mærket med en MRM-sletningspolitik, flyttes til [mappen Gendanbare elementer](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) , når opbevaringsperioden udløber. Disse elementer fjernes fra den inaktive postkasse, når varigheden af ventepositionen udløber. Hvis der ikke er angivet en varighed for venteposition for den inaktive postkasse, bevares elementerne i mappen Gendan elementer på ubestemt tid.

Omvendt ignoreres alle arkivpolitikker (MRM-opbevaringskoder, der er konfigureret med handlingen **FlytTilArkivér** ), som er inkluderet i den MRM-opbevaringspolitik, der er tildelt en inaktiv postkasse. Det betyder, at elementer i en inaktiv postkasse, der er mærket med en arkivpolitik, forbliver i den primære postkasse, når opbevaringsperioden udløber. De flyttes ikke til arkivpostkassen eller til mappen Gendanbare elementer i arkivpostkassen. De vil blive bevaret på ubestemt tid.

## <a name="next-steps"></a>Næste trin

Hvis du vil gøre en postkasse inaktiv og administrere den, f.eks. gendanne, gendanne og slette den, skal du se [Opret og administrer inaktive postkasser](create-and-manage-inactive-mailboxes.md).
