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
ms.openlocfilehash: 72d048bc99876c0f252feffe3159d3ce01303028
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63588902"
---
# <a name="learn-about-inactive-mailboxes"></a>Få mere at vide om inaktive postkasser

Din organisation skal muligvis bevare tidligere medarbejderes mail, når de forlader organisationen. Afhængigt af din organisations krav til opbevaring kan det være nødvendigt at bevare postkasseindhold et par måneder eller år efter ansættelse slutter, eller det kan være nødvendigt at bevare postkasseindhold på ubestemt tid. Uanset hvor længe du har brug for at bevare mail, kan du oprette inaktive postkasser til at bevare postkassen for tidligere medarbejdere.

## <a name="what-are-inactive-mailboxes"></a>Hvad er inaktive postkasser?

Når en medarbejder forlader organisationen (eller får et længere orlov), kan du fjerne den medarbejders Microsoft 365 konto. Medarbejderens postkassedata bevares i 30 dage, efter kontoen er fjernet. I denne periode kan du stadig gendanne postkassedataene ved at slette kontoen igen. Efter 30 dage fjernes dataene permanent.

Men hvis postkassen er i venteposition, før postkassen slettes Microsoft 365, konverteres postkassen til en inaktiv postkasse. De følgende afsnit indeholder oplysninger om ventende filer, der kan anvendes med Microsoft 365 opbevarings- og eDiscovery-ventende elementer.

Inaktive postkasser er nyttige, når din organisation har brug for at bevare postkasseindhold fra tidligere medarbejdere af lovmæssige årsager eller af andre årsager. Mens en hvilken som helst type venteposition, der er angivet i dette [dokument,](#confirming-a-hold-is-applied-to-a-mailbox) gennemtvinger, at en postkasse gøres inaktiv, når et brugerobjekt slettes, anbefaler vi at gøre dette ved at anvende en Microsoft 365-opbevaringspolitik eller opbevaringsetiketter, bekræfte at ventepositionen er anvendt og derefter fjerne den tilsvarende Microsoft 365-konto. På dette tidspunkt bevares indholdet af den inaktive postkasse i den periode, der er angivet, før brugerkontoen blev slettet. Du kan stadig gendanne den tilsvarende brugerkonto i en periode på 30 dage, men efter 30 dage bevares postkassen i Microsoft 365 som en inaktiv postkasse, indtil opbevaringspolitikken eller opbevaringsetiketterne fjernes.

> [!IMPORTANT]
> Som tidligere nævnt anbefaler vi, at du bruger en Microsoft 365 til at oprette en inaktiv postkasse:
> - In-Place ventende ord i Exchange Administration er nu udgået. Fra den 1. juli 2020 kunne nye vente In-Place ikke oprettes i Exchange Online. Pr. 1. oktober 2020 kan ventepositionen for ventepositioner på stedet ikke længere ændres. Alle inaktive postkasser med In-Place Hold anvendt kan kun slettes ved at fjerne In-Place hold. Eksisterende inaktive postkasser, der In-Place i venteposition, vil fortsat blive bevaret, indtil ventepositionen fjernes. Du kan finde flere oplysninger In-Place om at In-Place, ved at se [Tilbagetrækning af ældre eDiscovery-værktøjer](legacy-ediscovery-retirement.md).
> 
> - [Retslig tilbageholdelse](create-a-litigation-hold.md) forbliver understøttet som en alternativ metode til at bevare indhold i en postkasse og gøre det inaktivt, når en brugerkonto slettes. Som en ældre teknologi anbefaler vi dog, at du bruger Microsoft 365 opbevaring i stedet.

Når der er flere ventende versioner af det samme indhold[](retention.md#the-principles-of-retention-or-what-takes-precedence), gælder princippet for opbevaring, og indholdet bevares i den længste periode.

### <a name="confirming-a-hold-is-applied-to-a-mailbox"></a>Bekræftelse af at en venteposition anvendes på en postkasse

Uanset om du anvender en Microsoft 365-opbevaringspolitik, opbevaringsetiketter, eDiscovery-venteposition, retslig tilbageholdelse eller har en eksisterende In-Place-venteposition, kan du bekræfte, at ventepositionen anvendes på postkassen ved hjælp af PowerShell. Hvis du for nylig har konfigureret ventepositionen, skal du muligvis vente, indtil den anvendes på postkassen.

For at forhindre utilsigtet eller utilsigtet sletning anbefaler vi, at du bekræfter ventepositionen, før du sletter brugerkontoen. Hvis ventepositionen ikke anvendes, bliver postkassen ikke konverteret til en inaktiv postkasse.

Du kan finde en [vejledning under Sådan identificerer du den type venteposition, der er placeret på Exchange Online postkasse](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="inactive-mailboxes-and-microsoft-365-retention"></a>Inaktive postkasser og Microsoft 365 opbevaring

Hvis en Microsoft 365-opbevaringspolitik anvendes på en postkasse, eller hvis et eller flere mailelementer i en postkasse har en opbevaringsetiket anvendt, og derefter slettes Microsoft 365-brugerkontoen, så konverteres postkassen til en inaktiv postkasse. Sådan oprettes den inaktive postkasse:

- Opbevaringsindstillingerne skal konfigureres til [at bevare indhold eller bevare og derefter slette indhold](retention-settings.md#settings-for-retaining-and-deleting-content). Hvis opbevaringshandlingen er konfigureret til kun at slette indhold, bliver postkassen ikke inaktiv, når brugerkontoen slettes. Til inaktive postkasser anbefaler vi, at du bruger indstillingen Behold og slet.

- Opbevaringsindstillingerne skal anvendes på en [opbevaringsplacering,](retention-settings.md#locations) der er knyttet til en Exchange postkasse:
    - Exchange mail
    - Microsoft 365 grupper
    - Skype for Business
    - Exchange offentlige mapper
    - Teams kanalmeddelelser
    - Teams chats
    - Teams private kanalmeddelelser
    - Yammer communitymeddelelser
    - Yammer brugermeddelelser

Du kan finde flere oplysninger om Microsoft-opbevaring under [Få mere at vide om opbevaringspolitikker og opbevaringsnavne](retention.md).

Hvis Microsoft 365 opbevaring bruges til at oprette en inaktiv postkasse, vil opbevaringsindstillingerne fra opbevaringspolitikken eller opbevaringsnavne fortsat gælde for den inaktive postkasse. Det betyder, at hvis opbevaringsindstillingerne er konfigureret til at bevare og derefter slette indhold, flyttes elementer til mappen Genoprettelige elementer, når opbevaringsvarigheden udløber og derefter slettes fra den inaktive postkasse. Hvis opbevaringsindstillingerne ikke er konfigureret til slettede elementer, flyttes elementer, der ikke er blevet slettet permanent af brugeren (før postkassen blev gjort inaktiv), ikke til mappen Genoprettelige elementer og bevares på ubestemt tid, når postkassen bliver inaktiv.

> [!TIP]
> Du kan bruge egenskaben *ComplianceTagHoldApplied* til at identificere, om en postkasse indeholder elementer, som har en eller flere opbevaringsetiketter anvendt for at bevare eller bevare og derefter slette indhold. Du kan få mere at vide [under Identificere postkasser i venteposition, fordi der er anvendt en opbevaringsmærkat på en mappe eller et element](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item).

### <a name="using-adaptive-policy-scopes-to-manage-retention-of-inactive-mailboxes"></a>Brug af adaptive politikomfang til at administrere opbevaring af inaktive postkasser

Med [tilpassede politikomfang kan du anvende opbevaringsindstillinger](retention.md#adaptive-or-static-policy-scopes-for-retention) specifikt for inaktive postkasser. Fordelene ved denne konfiguration omfatter:

- Du kan overholde din organisations bestemmelser eller politikker, der kræver forskellige opbevaringsperioder for aktive medarbejdere og tidligere medarbejdere.

- Du kan konfigurere opbevaringsindstillingerne til kun at bevare postkasseindhold så længe, som det er nødvendigt for at opfylde organisationens krav til tidligere medarbejdere.

- Du kan hurtigt identificere den politik for opbevaring, der er tildelt til inaktive postkasser i organisationen, hvilket gør det nemmere at ændre opbevaringsindstillingerne, hvis det er nødvendigt. 

- Det er nemmere at slette en inaktiv postkasse permanent, fordi du kan fjerne den fra politikken ved [](retention-settings.md#to-configure-an-adaptive-scope) at konfigurere det tilpassede omfang for at udelukke den baseret på attributter eller egenskaber for den inaktive postkasse. Ellers skal du bruge [Exchange Online PowerShell](delete-an-inactive-mailbox.md#remove-an-inactive-mailbox-from-a-retention-policy)[, før du sletter postkassen](delete-an-inactive-mailbox.md#before-you-delete-an-inactive-mailbox).

> [!NOTE]
> Afhængigt af konfigurationen af omfanget af din tilpassede politik medtages inaktive postkasser muligvis eller ikke.  Hvis du specifikt vil målrette mod eller udelukke inaktive postkasser fra et tilpasset politikområde, skal du se [konfigurationsoplysninger Exchange mail og Exchange offentlige mapper](retention-settings.md#locations).

### <a name="using-static-policy-scopes-and-inactive-mailboxes"></a>Brug af statiske politikomfang og inaktive postkasser

Hvis du ikke bruger [tilpassede politikomfang](retention.md#adaptive-or-static-policy-scopes-for-retention) med Microsoft 365 og i stedet bruger et statisk [omfang](retention.md#adaptive-or-static-policy-scopes-for-retention), skal du overveje følgende:

- Statiske politikomfang omfatter inaktive postkasser, når du bruger standardkonfigurationen Alle modtagere, men **understøttes** ikke ved [bestemte inklusioner eller udeladelse.](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions) Men hvis du medtager eller udelader en modtager, der har en aktiv postkasse på det tidspunkt, hvor politikken anvendes, og postkassen senere bliver inaktiv, vil opbevaringsindstillingerne fortsat blive anvendt eller udeladt. I dette scenarie [gælder specifikke begrænsninger for inklusion og](retention-limits.md) udelukkelse stadig.
    
    > [!NOTE]
    > Det betyder også, at alle nye Microsoft 365 **opbevaringsindstillinger**, der bruger et statisk omfang, der anvendes til standardvalget af Alle modtagere, automatisk medtager alle eksisterende inaktive postkasser.

- Hvis du ændrer standardindstillingen for  Alle modtagere, så de medtager bestemte modtagere, gælder opbevaringsindstillingerne for politikken ikke længere for alle inaktive postkasser, som nu bliver berettiget til automatisk sletning.

- Hvis du vil udgive en opbevaringspolitik, der anvendes på en inaktiv postkasse, skal du se [Udgive en politik for opbevaring](retention.md#releasing-a-policy-for-retention).

> [!CAUTION]
> Når du bruger Microsoft 365 til at gøre en postkasse inaktiv, ændrer eller fjerner du ikke brugerens hovednavn (UPN) for postkassen, før du sletter den tilsvarende brugerkonto. Desuden skal du ikke ændre den primære SMTP-adresse (der er afledt af UPN'et) eller fjerne denne mailadresse fra listen over sekundære SMTP-adresser, der er knyttet til postkassen, før du gør postkassen inaktiv.
> 
> Hvis du ændrer UPN eller mailadresserne (som blev tildelt postkassen på det tidspunkt, hvor opbevaringsindstillingerne blev anvendt), og derefter sletter brugerkontoen for at gøre postkassen inaktiv, kan du ikke slette den inaktive postkasse, hvis du ikke længere har brug for at bevare den. Det skyldes, at du ikke kan fjerne den inaktive postkasse fra politikken ved hjælp af en UPN eller mailadresse (til at identificere den inaktive postkasse), der er forskellig fra dem, der fandtes, da opbevaringsindstillingerne oprindeligt blev anvendt på postkassen. Du kan finde flere oplysninger om at slette inaktive postkasser [i Slet en inaktiv postkasse Office 365](delete-an-inactive-mailbox.md).

## <a name="inactive-mailboxes-and-ediscovery-case-holds"></a>Inaktive postkasser og eDiscovery-sags hold

Hvis en venteposition, der er knyttet til en [eDiscovery-sag](./get-started-core-ediscovery.md) i Microsoft 365 Overholdelsescenter, placeres i en postkasse, og derefter slettes postkassen eller brugerens konto, postkassen bliver en inaktiv postkasse. Vi anbefaler dog ikke at bruge eDiscovery-sags hold til at gøre en postkasse inaktiv. Det skyldes, at eDiscovery-sager er beregnet til bestemte, tidsbundne sager relateret til et juridisk problem. På et tidspunkt vil en juridisk sag sandsynligvis slutte, og de hold, der er knyttet til sagen, fjernes, og eDiscovery-sagen lukkes. Hvis et venteposition, der er sat i en inaktiv postkasse, er knyttet til en eDiscovery-sag, og derefter ventepositionen frigives, eller eDiscovery-sagen lukkes (eller slettes), slettes den inaktive postkasse permanent. Du kan heller ikke oprette et tidsbaseret eDiscovery-venteposition. Det betyder, at indholdet i en inaktiv postkasse bevares uendeligt, eller indtil ventepositionen fjernes, og den inaktive postkasse slettes. Vi anbefaler derfor, at du bruger Microsoft 365 opbevaring til inaktive postkasser.

Du kan finde flere oplysninger om forskellene mellem eDiscovery-vente hold og opbevaring Microsoft 365 opbevaring i Hvornår skal jeg bruge opbevaringspolitikker og opbevaringsetiketter eller [eDiscovery-vente hold](retention.md#when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds).

## <a name="inactive-mailboxes-and-auto-expanding-archives"></a>Inaktive postkasser og automatisk udvide arkiver

En inaktiv postkasse, der er konfigureret med et automatisk udvidende arkiv, kan ikke gendannes eller gendannes. I situationer, hvor det er nødvendigt at gendanne data fra en inaktiv postkasse med et automatisk udvidende arkiv, anbefales det, at du bruger værktøjet til indholdssøgning til at eksportere dataene fra postkassen og derefter importere til en anden postkasse. Du kan finde en trinvis vejledning i at søge i en inaktiv postkasse og eksportere søgeresultaterne i:

- [Indholdssøgning](content-search.md)

- [Eksportér resultater fra indholdssøgning](export-search-results.md)

## <a name="inactive-mailboxes-and-exchange-mrm-retention-policies"></a>Inaktive postkasser og Exchange MRM-opbevaringspolitikker

Når du Exchange opbevaringspolitik (funktionen Messaging Records Management, eller MRM, i Exchange Online) oprettes der ikke en inaktiv postkasse, når brugerkontoen slettes.

Men hvis denne MRM-opbevaringspolitik blev anvendt på en postkasse, før den blev inaktiv, vil eventuelle sletningspolitikker (MRM-opbevaringsmærker, der er konfigureret med en **Delete-handling** ) fortsat blive behandlet på den inaktive postkasse. Det betyder, at elementer, der mærkes med en MRM-sletningspolitik, flyttes [](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) til mappen Genoprettelige elementer, når en opbevaringsperiode udløber. Disse elementer bliver slettet fra den inaktive postkasse, når varigheden af ventepositionen udløber. Hvis der ikke er angivet en varighed af venteposition for den inaktive postkasse, bevares elementer i mappen Gendan elementer på ubestemt tid.

Omvendt ignoreres eventuelle arkiveringspolitikker (MRM-opbevaringsmærker,  der er konfigureret med en FlytTilArkiver-handling), der er inkluderet i MRM-opbevaringspolitikken, der er tildelt en inaktiv postkasse. Det betyder, at elementer i en inaktiv postkasse, der mærkes med en arkiveringspolitik, forbliver i den primære postkasse, når en opbevaringsperiode udløber. De flyttes ikke til arkivpostkassen eller til mappen Genoprettelige elementer i arkivpostkassen. De bevares på ubestemt tid.

## <a name="next-steps"></a>Næste trin

Hvis du vil gøre en postkasse inaktiv og administrere den, f.eks. gendanne, gendanne og slette den, skal du se [Oprette og administrere inaktive postkasser](create-and-manage-inactive-mailboxes.md).
