---
title: Rediger varigheden af fastfrysning for en inaktiv postkasse
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: 8/29/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: bdee24ed-b8cf-4dd0-92ae-b86ec4661e6b
ms.custom:
- seo-marvel-apr2020
description: Når en Office 365 postkasse er gjort inaktiv, skal du ændre varigheden af ventepositionen eller Office 365 opbevaringspolitik, der er tildelt den inaktive postkasse.
ms.openlocfilehash: 6fdb3993fd6b6503ab672a0c6465a394f3824c4b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628875"
---
# <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Rediger varigheden af fastfrysning for en inaktiv postkasse

En [inaktiv postkasse](inactive-mailboxes-in-office-365.md) er postkassetilstand, der bruges til at bevare en tidligere medarbejders mail, når vedkommende forlader din organisation. En postkasse bliver inaktiv, når der anvendes en relevant venteposition på den, før Microsoft 365-brugerobjektet slettes.  Følgende typer ventepositioner starter oprettelsen af en inaktiv postkasse ved sletning af brugerkonto:

- [Microsoft 365-opbevaringspolitikker og -mærkater](retention.md) med indstillinger for bevarelse eller bevarelse og sletning

- En venteposition, der er knyttet til en [eDiscovery-sag](ediscovery.md)

- [Procesførelse - venteposition](create-a-litigation-hold.md)

- En eksisterende In-Place venteposition.

> [!IMPORTANT]
> Selvom en af ovenstående ventepositioner tvinger en postkasse til at blive inaktiv ved sletning af en Microsoft 365-brugerkonto, anbefales det på det kraftigste, at du bruger Microsoft 365-opbevaring, når du proaktivt planlægger at bruge inaktive postkasser.
>
> - eDiscovery-ventepositioner er beregnet til specifikke, tidsbundne sager, der er relateret til et juridisk problem. På et tidspunkt slutter en retssag sandsynligvis, og de ventepositioner, der er knyttet til sagen, fjernes, og eDiscovery-sagen lukkes (eller slettes). Hvis en venteposition, der er placeret på en inaktiv postkasse, er knyttet til en eDiscovery-sag, og ventepositionen frigives, eller eDiscovery-sagen lukkes eller slettes, slettes den inaktive postkasse permanent.
>
> - In-Place Ventepositioner i Exchange Administration udgår nu. Fra den 1. juli 2020 kunne nye In-Place Ventepositioner ikke oprettes i Exchange Online. Fra den 1. oktober 2020 kunne varigheden af bevarelse på stedet ikke længere ændres. Alle inaktive postkasser, hvor der er anvendt en In-Place venteposition, kan kun slettes ved at fjerne In-Place Venteposition. Eksisterende inaktive postkasser, der er på In-Place venteposition, bevares fortsat, indtil ventepositionen fjernes. Du kan finde flere oplysninger om, In-Place ventepositioner udgår, under [Udfasning af ældre eDiscovery-værktøjer](legacy-ediscovery-retirement.md).
>
> - [Procesførelse i venteposition](create-a-litigation-hold.md) understøttes fortsat som en alternativ metode til at bevare indhold i en postkasse og gøre det inaktivt, når en brugerkonto er slettet. Men som en ældre teknologi anbefaler vi, at du bruger Microsoft 365-opbevaring i stedet.

Når postkassen er inaktiv, bevares indholdet af postkassen, herunder [mappen Gendanbare elementer](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) , indtil den venteposition, der blev placeret på postkassen, før den blev gjort inaktiv, ikke længere gælder.  

Hvis den relevante venteposition ikke er tidsbaseret, f.eks. en venteposition, der er knyttet til en opbevarelsespolitik eller mærkat på ubestemt tid i Microsoft 365, en eDiscovery-sag eller en litigation-venteposition (uden konfigureret ```LitigationHoldDuration``` ), bevares postkasseindholdet på ubestemt tid, indtil ventepositionen fjernes.  

Men hvis ventepositionen er tidsbaseret, bevares postkasseindholdet, indtil varigheden af ventepositionen udløber, hvorefter alle elementer i mappen Gendanbare elementer slettes permanent (fjernes) fra den inaktive postkasse.

> [!NOTE]
> I forbindelse med inaktive postkasser anbefaler vi, at du bruger en indstilling for opbevaring og sletning af dine Microsoft 365-opbevaringspolitik eller -mærkater.  Hvis du vælger indstillingen Bevar kun, fjernes mappen Elementer, der kan gendannes, efter varigheden af ventepositionen, men alle andre elementer, der ikke slettes, forbliver i den inaktive postkasse på ubestemt tid.

Efterhånden som regler og politikker udvikler sig, kan der være situationer, hvor du skal ændre varigheden af den venteposition, der er tildelt den inaktive postkasse.  I følgende trin beskrives det, hvordan du gør det.

## <a name="connect-to-powershell"></a>Opret forbindelse til PowerShell

Som vi har nævnt før, kan mange forskellige typer ventepositioner udløse oprettelsen af en inaktiv postkasse.  Hvis du vil ændre varigheden af ventepositionen for den inaktive postkasse, skal du derfor først identificere, hvilken type ventepositioner der påvirker den.  Hvis du vil gøre dette, skal du bruge Exchange Online PowerShell til at identificere typerne af ventepositioner, og hvis den inaktive postkasse påvirkes af Opbevaringspolitikker eller -mærkater i Microsoft 365, skal du også bruge Security & Compliance PowerShell til at identificere de specifikke politikker.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell eller Security & Compliance PowerShell, skal du se et af følgende emner:

  - [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

  - [Opret forbindelse til Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell)

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>Trin 1: Identificer ventepositionerne i en inaktiv postkasse

Da forskellige typer ventepositioner eller en eller flere Microsoft 365-opbevaringspolitikker kan placeres i en inaktiv postkasse, er det første trin at identificere ventepositionerne i en inaktiv postkasse.
  
Kør følgende kommando i Exchange Online PowerShell for at få vist oplysninger om venteposition for en bestemt inaktiv postkasse i din organisation.
  
```powershell
Get-Mailbox -Identity <identity of inactive mailbox> -InactiveMailboxOnly | FL DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied
```

Hvis du har brug for at identificere typen af venteposition for flere inaktive postkasser, og din organisation har et stort antal af dem, kan det blive ikke-administreret at få vist ved hjælp af PowerShell. I dette tilfælde kan du eksportere alle de relevante oplysninger til en CSV-fil ved hjælp af følgende kommando og ændre efter ```Path``` behov for dit miljø:

```powershell
Get-Mailbox -InactiveMailboxOnly -ResultSize Unlimited | Select DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied | Export-Csv -NoTypeInformation -Path "C:\Temp\InactiveMailboxHoldTypes.csv"
```

I dette eksempel viser følgende resultater for seks inaktive postkasser med forskellige mulige ventepositionstyper.

> [!NOTE]
> Flere ventepositioner, herunder flere typer ventepositioner, kan gælde for en enkelt inaktiv postkasse.
  
```text
DisplayName              : Ann Beebe
Name                     : annb
DistinguishedName        : CN=annb,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 664ef44e-c1a0-47b0-9553-2ecdfc6ef840
IsInactiveMailbox        : True
LitigationHoldEnabled    : True
LitigationHoldDuration   : 365.00:00:00
LitigationHoldDate       : 10/25/2021 6:54:57 PM
LitigationHoldOwner      : admin@contoso.com
InPlaceHolds             : {}
ComplianceTagHoldApplied : False
...
DisplayName              : Carol Olson
Name                     : carolo
DistinguishedName        : CN=carolo,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : e646a369-00bf-43d3-837a-8eae8b301d44
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {mbxcdbbb86ce60342489bff371876e7f224:3}
ComplianceTagHoldApplied : False
...
DisplayName              : Megan Bowen
Name                     : meganb
DistinguishedName        : CN=meganb,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 36ec77cb-c524-468a-a8e8-bfb75e01a176
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {mbx6fe063689d404a5bb9940eed0f0bf5d2:1}
ComplianceTagHoldApplied : True
...
DisplayName              : Mario Necaise
Name                     : marion
DistinguishedName        : CN=marion,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 0579e039-a695-40d5-8f0a-0dc04f4b4c8f
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {}
ComplianceTagHoldApplied : False
...
DisplayName              : Abraham McMahon
Name                     : abrahamm
DistinguishedName        : CN=abrahamm,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 55ad8905-4e68-4c8d-940d-e068ec6b51fc
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {UniH7d895d48-7e23-4a8d-8346-533c3beac15d}
ComplianceTagHoldApplied : False
...
DisplayName              : Pilar Pinilla
Name                     : pilarp
DistinguishedName        : CN=pilarp,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 8d7867d6-bb6d-4cd8-a51f-09d208f97fcc
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {c0ba3ce811b6432a8751430937152491}
ComplianceTagHoldApplied : False
```

I følgende tabel identificeres de seks forskellige ventepositionstyper, der blev brugt til at gøre hver postkasse inaktiv i ovenstående eksempel.
  
|**Inaktiv postkasse**|**Ventepositionstype**|**Sådan identificerer du ventepositionen i den inaktive postkasse**|
|:-----|:-----|:-----|
|Ann Beebe  <br/> |Procesførelse - venteposition  <br/> | Egenskaben  `LitigationHoldEnabled`  er angivet til at angive, at  `True` postkassen er i en procesførelsesventeposition. <br/><br/> Derudover er indstillet til at `365.00:00:00` angive, `LitigationHoldDuration` at postkasseelementer ikke længere vil være underlagt procesførelse i venteposition 365 dage efter deres oprettelsesdato (sendt/modtaget).  <br/><br/> `LitigationHoldDate` angiver den dato, hvor LitigationHold blev aktiveret, og `LitigationHoldOwner` identificerer den person, der startede ventepositionen for procesførelsen. <br/> |
|Carol Olson  <br/> |Microsoft 365-opbevaringspolitik fra den Microsoft Purview-compliance-portal, der anvendes på bestemte postkasser  <br/> |Egenskaben  `InPlaceHolds`  indeholder GUID'et for den Microsoft 365-opbevaringspolitik, der anvendes på den inaktive postkasse. Du kan se, at dette er en opbevaringspolitik, der anvendes på bestemte postkasser, fordi GUID'et starter med præfikset `mbx` og ender i en `:2` eller `:3`. <br/><br/> Du kan finde flere oplysninger under [Om formatet af værdien InPlaceHolds for opbevaringspolitikker](identify-a-hold-on-an-exchange-online-mailbox.md#understanding-the-format-of-the-inplaceholds-value-for-retention-policies).  <br/> |
|Megan Bowen <br/> | Microsoft 365-opbevaringsmærkat med en bevar eller bevar og slet-handling anvendes på mindst ét element i postkassen  <br/> |Egenskaben `ComplianceTagHoldApplied` `True` angiver, at et element er mærket med en bevar eller bevar og slet mærkat.  <br/><br/> Derudover indeholder egenskaben `InPlaceHolds` GUID for den Microsoft 365-politik for opbevaringsmærkat, der anvendes på den inaktive postkasse.  <br/><br/> Du kan finde flere oplysninger under [Identificere postkasser i venteposition, fordi der er anvendt en opbevaringsmærkat på en mappe eller et element](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) <br/>  |
|Mario Necaise  <br/> |Microsoft 365-opbevaringspolitik for hele organisationen fra Microsoft Purview-compliance-portal <br/> |Egenskaben  `InPlaceHolds`  er tom, `LitigationHoldEnabled` er `False` og `ComplianceTagHoldApplied` er `False`. Dette angiver, at en eller flere hele (Exchange) placering Microsoft 365-opbevaringspolitikker, der anvendes på den organisation, som den inaktive postkasse nedarver. <br/><br/> Du kan finde flere oplysninger under [Sådan bekræfter du, at der anvendes en opbevaringspolitik for hele organisationen på en postkasse](identify-a-hold-on-an-exchange-online-mailbox.md#how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox) <br/> |
|Abraham McMahon  <br/> |eDiscovery-sag i den Microsoft Purview-compliance-portal  <br/> |Egenskaben  `InPlaceHolds`  indeholder GUID'et for den eDiscovery-sagsposition, der er placeret i den inaktive postkasse. Du kan se, at dette er en eDiscovery-sag i venteposition, fordi GUID'et starter med præfikset  `UniH` .  <br/><br/> Du kan finde flere oplysninger under [eDiscovery-ventepositioner](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds). <br/> |
|Pilar Pinilla  <br/> |In-Place venteposition  <br/> |Egenskaben  `InPlaceHolds`  indeholder GUID'et for den In-Place venteposition, der er placeret i den inaktive postkasse. Du kan se, at dette er en In-Place venteposition, fordi GUID'et ikke starter med et præfiks.  <br/><br/> **BEMÆRK**! Fra den 1. oktober 2020 kan bevarelsestiden for bevarelse på stedet ikke længere ændres. Du kan kun fjerne en In-Place venteposition, hvilket medfører sletning af den inaktive postkasse. <br/><br/> Du kan finde flere oplysninger under [Udfasning af ældre eDiscovery-værktøjer](legacy-ediscovery-retirement.md). <br/> |

## <a name="step-2-change-the-hold-duration-for-an-inactive-mailbox"></a>Trin 2: Rediger varigheden af ventepositionen for en inaktiv postkasse

Når du har identificeret, hvilken type venteposition der er placeret i den inaktive postkasse (og om der er flere ventepositioner), er det næste trin at ændre varigheden af ventepositionen.  Processen varierer afhængigt af den anvendte type venteposition.

- [Rediger varigheden af en Microsoft 365-opbevaringspolitik](#change-the-duration-for-a-microsoft-365-retention-policy)

- [Rediger varigheden af et Microsoft 365-opbevaringsmærkat](#change-the-duration-for-a-microsoft-365-retention-label)

- [Skift varigheden af en eDiscovery-venteposition](#change-the-duration-for-an-ediscovery-hold)

- [Rediger varigheden af en procesførelsesventetid](#change-the-duration-for-a-litigation-hold)

- [Rediger varigheden af en In-Place venteposition](#change-the-duration-for-an-in-place-hold)

### <a name="change-the-duration-for-a-microsoft-365-retention-policy"></a>Rediger varigheden af en Microsoft 365-opbevaringspolitik

Hvis du vil ændre varigheden af ventepositionen for en Microsoft 365-opbevaringspolitik, skal du først identificere den politik, der påvirker den inaktive postkasse, ved at køre `Get-RetentionCompliancePolicy` med det tilknyttede GUID fra `InPlaceHolds` egenskaben i postkassen i Security & Compliance PowerShell.

Sørg for at fjerne præfikset og suffikset fra GUID,når du kører denne kommando.  Hvis du f.eks. bruger eksempeloplysningerne ovenfor, skal du tage værdien `InPlaceHolds` for `mbxcdbbb86ce60342489bff371876e7f224:3` og derefter fjerne `mbx` og `:3` resultere i et politik-GUID for `cdbbb86ce60342489bff371876e7f224`.  I dette eksempel skal du køre:

```powershell
Get-RetentionCompliancePolicy cdbbb86ce60342489bff371876e7f224 | FL Name
```

Når du kender navnet på politikken, kan du blot ændre opbevaringspolitikken i Microsoft Purview-compliance-portal.  Vær opmærksom på, at opbevaringspolitikker typisk anvendes på mere end én placering, så ændring af politikken påvirker alle anvendte placeringer – både inaktive og aktive, hvilket også kan omfatte andre placeringer end Exchange.  Du kan få flere oplysninger under [Opret og konfigurer opbevaringspolitikker](create-retention-policies.md).  

> [!IMPORTANT]
> Opbevaringspolitikker med [bevarelseslås](retention-preservation-lock.md) aktiveret kan have opbevaringsperioden forlænget, men ikke reduceret eller fjernet.

Hvis det er hensigten kun at ændre opbevaringsperioden for inaktive postkasser eller kun bestemte inaktive postkasser, kan du overveje at installere [tilpassede politikområder](retention.md#adaptive-or-static-policy-scopes-for-retention), som kan bruges til individuelt at målrette bestemte postkasser – eller postkassetyper, f.eks. inaktive postkasser – ved hjælp af Azure AD- og Exchange-attributter og -egenskaber.

### <a name="change-the-duration-for-a-microsoft-365-retention-label"></a>Rediger varigheden af et Microsoft 365-opbevaringsmærkat

På samme måde som med opbevaringspolitikker skal du, når du ændrer varigheden af ventepositionen for en Microsoft 365-opbevaringsmærkat, først identificere den politik, der publicerer mærkaten, der påvirker indholdet i den inaktive postkasse, ved at køre `Get-RetentionCompliancePolicy` med det tilknyttede GUID fra `InPlaceHolds` egenskaben i postkassen i Security & Compliance PowerShell.

Sørg for at fjerne præfikset og suffikset fra GUID,når du kører denne kommando.  Hvis du f.eks. bruger eksempeloplysningerne ovenfor, skal du tage værdien `InPlaceHolds` for `mbx6fe063689d404a5bb9940eed0f0bf5d2:1` og derefter fjerne `mbx` og `:1` resultere i et politik-GUID for `6fe063689d404a5bb9940eed0f0bf5d2`.  I dette eksempel skal du køre:

```powershell
Get-RetentionCompliancePolicy 6fe063689d404a5bb9940eed0f0bf5d2 | FL Name
```

Når du har identificeret politikken, ved du, hvilke mærkater der er blevet publiceret, og deres indstillinger.  Da mærkater gælder for individuelle elementer, kan du muligvis ikke direkte identificere, hvilken mærkat der påvirker indholdet, afhængigt af antallet af etiketter, der er publiceret med politikken og deres indstillinger.  

En metode, som du kan bruge til at identificere det indhold, som hver mærkat gælder for, er ved hjælp af [indholdssøgning](content-search.md).  Hvis du f.eks. bruger eksempeloplysningerne ovenfor, antages det, at politikken publicerer flere mærkater, hvoraf det ene hedder "HR-Content".  Med de korrekte tilladelser kan der køres en [indholdssøgning](microsoft-365-compliance-center-permissions.md) med [PowerShell-kommandoen New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch), der angiver den inaktive postkasses primære SMTP-adresse, der er forudindstillet med et punktum (`.`) og parameteren `-AllowNotFoundExchangeLocationsEnabled $true` til at springe validering over:

```powershell
New-ComplianceSearch -Name "MeganB Inactive Mailbox HR-Content Label Search" -ExchangeLocation .meganb@contoso.onmicrosoft.com -AllowNotFoundExchangeLocationsEnabled $true -ContentMatchQuery "compliancetag=HR-Content"
```

Når søgningen er oprettet, skal du starte søgningen ved hjælp af følgende kommando:

```powershell
Start-ComplianceSearch "MeganB Inactive Mailbox HR-Content Label Search"
```

Ved hjælp af denne metode kan du derefter identificere, hvilke mærkater fra den identificerede mærkatpolitik der gælder for indhold i den inaktive postkasse, så du kan ændre deres opbevaringsperioder. Vær opmærksom på, at opbevaringsmærkater typisk anvendes på mere end én placering, så ændring af en mærkat påvirker alle anvendte placeringer og markeret indhold, som også kan omfatte placeringer og andet indhold end Exchange. Du kan finde flere oplysninger under [Publicer opbevaringsmærkater og anvend dem i apps](create-apply-retention-labels.md).

> [!NOTE]
> Det er ikke alle typer opbevaringsmærkater, der kan ændres.  For nogle mærkater kan du muligvis kun øge opbevaringstiden, og for andre kan du muligvis slet ikke ændre opbevaringsperioden.

### <a name="change-the-duration-for-an-ediscovery-hold"></a>Skift varigheden af en eDiscovery-venteposition

Ventepositioner, der er knyttet til eDiscovery-sager, er ubestemte ventepositioner, hvilket betyder, at der ikke er nogen venteposition, der kan ændres. Elementer opbevares for evigt, eller indtil [ventepositionen fjernes](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold) , eller sagen lukkes.
  
### <a name="change-the-duration-for-a-litigation-hold"></a>Rediger varigheden af en procesførelsesventetid

Du skal bruge Exchange Online PowerShell til at ændre varigheden af ventepositionen for en procesførelse, der er placeret i en inaktiv postkasse. Du kan ikke bruge EAC. Kør følgende kommando for at ændre varigheden af ventepositionen. I dette eksempel ændres varigheden af ventepositionen til en ubegrænset tidsperiode:
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldDuration unlimited
```

Resultatet er, at elementer i den inaktive postkasse bevares på ubestemt tid, eller indtil ventepositionen fjernes, eller varigheden af ventepositionen ændres til en anden værdi.
  
> [!TIP]
> Den bedste måde at identificere en inaktiv postkasse på er ved hjælp af værdien **Entydigt navn** eller **Exchange GUID** . Brug af en af disse værdier hjælper med at forhindre, at den forkerte postkasse angives ved et uheld.

### <a name="change-the-duration-for-an-in-place-hold"></a>Rediger varigheden af en In-Place venteposition

In-Place Ventepositioner er udgået og kan ikke længere ændres. Hvis der er anvendt en In-Place venteposition på en inaktiv postkasse, kan du ikke ændre varigheden af ventepositionen. Du kan kun fjerne den In-Place venteposition, hvilket medfører sletning af den inaktive postkasse. Du kan få flere oplysninger under [Slet en inaktiv postkasse](delete-an-inactive-mailbox.md#remove-in-place-holds).
  
## <a name="more-information"></a>Flere oplysninger

- **Hvordan beregnes varigheden af ventepositionen for et element i en inaktiv postkasse?** Varigheden beregnes ud fra den oprindelige dato, hvor et postkasseelement blev modtaget eller oprettet.
    
- **Hvad sker der, når varigheden af ventepositionen udløber?** Når varigheden af ventepositionen udløber for et postkasseelement i mappen Gendanbare elementer, slettes elementet permanent (fjernes) fra den inaktive postkasse. Hvis der ikke er angivet nogen varighed for ventepositionen i den inaktive postkasse, fjernes elementerne i mappen Gendanbare elementer aldrig (medmindre varigheden af ventepositionen for den inaktive postkasse ændres). 
    
- **Behandles en Exchange MRM-politik stadig på inaktive postkasser?**  Hvis der blev anvendt en MRM-opbevaringspolitik på en postkasse, før den blev inaktiv, behandles alle politikker for sletning (MRM-opbevaringskoder, der er konfigureret med en **Slet-handling** ) fortsat på den inaktive postkasse. Det betyder, at elementer, der er mærket med en MRM-sletningspolitik, flyttes til mappen Gendanbare elementer, når opbevaringsperioden udløber. Disse elementer fjernes fra den inaktive postkasse, når varigheden af ventepositionen udløber. Hvis der ikke er angivet en varighed for venteposition for den inaktive postkasse, bevares elementerne i mappen Gendan elementer på ubestemt tid.

    Omvendt ignoreres alle arkivpolitikker (MRM-opbevaringskoder, der er konfigureret med handlingen **FlytTilArkivér** ), som er inkluderet i den MRM-opbevaringspolitik, der er tildelt en inaktiv postkasse. Det betyder, at elementer i en inaktiv postkasse, der er mærket med en arkivpolitik, forbliver i den primære postkasse, når opbevaringsperioden udløber. De flyttes ikke til arkivpostkassen eller til mappen Gendanbare elementer i arkivpostkassen. De vil blive bevaret på ubestemt tid.
    > [!NOTE]
    > Anvendelse af en Exchange-opbevaringspolitik (funktionen Administration af meddelelsesposter eller MRM i Exchange Online) opretter ikke en inaktiv postkasse, når brugerkontoen slettes.

- **Som med almindelige postkasser behandler MFA (Managed Folder Assistant) også inaktive postkasser.** I Exchange Online behandler MFA postkasser ca. en gang hver syvende dag. Når du har ændret varigheden af ventepositionen for en inaktiv postkasse, kan du bruge cmdlet'en **Start-ManagedFolderAssistant** til straks at begynde at behandle den nye ventepositionsvarighed for den inaktive postkasse. Kør følgende kommando. 

    ```powershell
    Start-ManagedFolderAssistant -InactiveMailbox <identity of inactive mailbox>
    ```
   
- **Hvis mange `InPlaceHolds` er placeret i en inaktiv postkasse, vises ikke alle GUID'er for venteposition.** Du kan køre følgende kommando for at få vist GUID'erne for alle `InPlaceHolds` , der er placeret i en inaktiv postkasse.
    
    ```powershell
    Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds
    ```
