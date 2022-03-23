---
title: Ændre varigheden af ventepositionen for en inaktiv postkasse
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
description: Når en Office 365 postkassen er gjort inaktiv, kan du ændre varigheden af den opbevaringspolitik Office 365, der er tildelt den inaktive postkasse.
ms.openlocfilehash: bf1131aa0d14222bec7ab1c94983925cfe39e673
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63589118"
---
# <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Ændre varigheden af ventepositionen for en inaktiv postkasse

En [inaktiv postkasse](inactive-mailboxes-in-office-365.md) er postkassetilstanden, der bruges til at bevare en tidligere medarbejders mail, når han eller hun forlader organisationen. En postkasse bliver inaktiv, når der er anvendt relevant venteposition på den, Microsoft 365 brugerobjektet slettes.  Følgende typer ventende indstillinger starter oprettelsen af en inaktiv postkasse ved sletning af brugerkonti:

- [Microsoft 365 opbevaringspolitikker og navne med](retention.md) indstillinger for at bevare eller bevare og slette

- En venteposition, der er knyttet [til en eDiscovery-sag](ediscovery.md)

- [Retslig venteposition](create-a-litigation-hold.md)

- En eksisterende In-Place venteposition.

> [!IMPORTANT]
> Selvom et af ovenstående ventende funktioner vil gennemtvinge, at en postkasse bliver inaktiv efter Microsoft 365 sletning af en brugerkonto, anbefales det kraftigt, at du bruger Microsoft 365-opbevaring, når du proaktivt planlægger at bruge inaktive postkasser.
>
> - eDiscovery-ventende oplysninger er beregnet til bestemte, tidsbundne sager relateret til et juridisk problem. På et tidspunkt vil en juridisk sag sandsynligvis slutte, og de hold, der er knyttet til sagen, fjernes, og eDiscovery-sagen lukkes (eller slettes). Hvis en venteposition, der er sat i en inaktiv postkasse, er knyttet til en eDiscovery-sag, og ventepositionen frigives, eller eDiscovery-sagen lukkes eller slettes, slettes den inaktive postkasse permanent.
>
> - In-Place ventende ord i Exchange Administration er nu udgået. Fra den 1. juli 2020 kunne nye vente In-Place ikke oprettes i Exchange Online. Pr. 1. oktober 2020 kan ventepositionen for ventepositioner på stedet ikke længere ændres. Alle inaktive postkasser med In-Place Hold anvendt kan kun slettes ved at fjerne In-Place hold. Eksisterende inaktive postkasser, der In-Place i venteposition, vil fortsat blive bevaret, indtil ventepositionen fjernes. Du kan finde flere oplysninger In-Place om at In-Place, ved at se [Tilbagetrækning af ældre eDiscovery-værktøjer](legacy-ediscovery-retirement.md).
>
> - [Retslig tilbageholdelse](create-a-litigation-hold.md) forbliver understøttet som en alternativ metode til at bevare indhold i en postkasse og gøre det inaktivt, når en brugerkonto slettes. Som en ældre teknologi anbefaler vi dog, at du bruger Microsoft 365 opbevaring i stedet.

Når det er gjort inaktivt, bevares indholdet [](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) af postkassen, herunder mappen Genoprettelige elementer, indtil det hold, der blev sat i postkassen, før den blev gjort inaktiv, ikke længere er gældende.  

Hvis den gældende venteposition ikke er tidsbaseret, f.eks. venteposition, der er knyttet til en opbevaringspolitik eller etiket til opbevaring på ubestemt tid Microsoft 365 opbevaringspolitik eller -etiket, en eDiscovery-sag eller retslig tilbageholdelse (```LitigationHoldDuration```uden konfigureret), bevares postkassens indhold på ubestemt tid, indtil ventepositionen fjernes.  

Men hvis ventepositionen er tidsbaseret, bevares postkasseindholdet, indtil varigheden af ventepositionen udløber, hvorefter elementer i mappen Genoprettelige elementer slettes permanent (slettes) fra den inaktive postkasse.

> [!NOTE]
> For inaktive postkasser anbefaler vi, at du bruger en opbevarings- og sletningsindstilling Microsoft 365 opbevaringspolitik eller etiketter.  Hvis du vælger en indstilling, der kun kan bevares, slettes mappen Genoprettelige elementer i slutningen af ventepositionen, men andre elementer, der ikke slettes, forbliver i den inaktive postkasse på ubestemt tid.

Efterhånden som regler og politikker udvikles, kan der være visse situationer, hvor du skal ændre varigheden af den venteposition, der er tildelt den inaktive postkasse.  Følgende trin beskriver, hvordan du gør dette.

## <a name="connect-to-powershell"></a>Forbind til PowerShell

Som vi har nævnt tidligere, kan mange forskellige typer ventende indhold udløse oprettelsen af en inaktiv postkasse.  For at ændre den varighed af venteposition, der anvendes på den inaktive postkasse, skal du derfor først finde ud af, hvilken type venteposition der påvirker den.  For at gøre dette skal du bruge Exchange Online PowerShell til at identificere typerne af ventepositioner, og hvis den inaktive postkasse påvirkes af Microsoft 365-opbevaringspolitikker eller -etiketter, skal du også bruge Security and Compliance Center PowerShell til at identificere de specifikke politikker.

- Hvis du vil oprette Exchange Online til PowerShell eller Security & Compliance Center PowerShell, skal du se et af følgende emner:

  - [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

  - [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell)

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>Trin 1: Identificer ventende funktioner i en inaktiv postkasse

Da der kan være forskellige typer venterum eller en eller flere Microsoft 365-opbevaringspolitikker i en inaktiv postkasse, er det første trin at identificere opbevaringspolitikkerne i en inaktiv postkasse.
  
Kør følgende kommando i Exchange Online PowerShell for at få vist oplysninger om venteposition for en bestemt inaktiv postkasse i organisationen.
  
```powershell
Get-Mailbox -Identity <identity of inactive mailbox> -InactiveMailboxOnly | FL DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied
```

Hvis du har brug for at identificere typen af venteposition for flere inaktive postkasser, og din organisation har et stort antal af dem, kan det blive ikke-administreret at få vist ved hjælp af PowerShell. I dette tilfælde kan du eksportere alle de relevante oplysninger til en CSV-fil ```Path``` ved hjælp af følgende kommando og ændre efter behov for dit miljø:

```powershell
Get-Mailbox -InactiveMailboxOnly -ResultSize Unlimited | Select DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied | Export-Csv -NoTypeInformation -Path "C:\Temp\InactiveMailboxHoldTypes.csv"
```

I dette eksempel viser følgende resultater for seks inaktive postkasser med forskellige mulige ventepositionstyper.

> [!NOTE]
> Der kan gælde flere ventende indholdstyper for en enkelt inaktiv postkasse.
  
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

I følgende tabel kan du se de seks forskellige typer ventepositioner, der blev brugt til at gøre hver postkasse inaktiv i eksemplet ovenfor.
  
|**Inaktiv postkasse**|**Ventepositionstype**|**Sådan identificeres ventepositionen i den inaktive postkasse**|
|:-----|:-----|:-----|
|Ann Beebe  <br/> |Retslig venteposition  <br/> | Egenskaben  `LitigationHoldEnabled`  er indstillet til at  `True` angive, at postkassen er i retslig venteposition. <br/><br/> Desuden angives det, `LitigationHoldDuration` `365.00:00:00` at postkasseelementer ikke længere skal være underlagt procesførelse 365 dage efter oprettelsesdatoen (sendt/modtaget).  <br/><br/> The `LitigationHoldDate` indicates the date LitigationHold was enabled and `LitigationHoldOwner` identifies the person who initiated the litigation hold. <br/> |
|Carol Olson  <br/> |Microsoft 365 opbevaringspolitik fra Microsoft 365 Overholdelsescenter, der anvendes til bestemte postkasser  <br/> |Egenskaben `InPlaceHolds` indeholder GUID'et for den Microsoft 365 opbevaringspolitik, der anvendes på den inaktive postkasse. Du kan se, at dette er en opbevaringspolitik, der anvendes på bestemte postkasser, fordi GUID'et `mbx` starter med præfikset og slutter i et `:2` eller `:3`. <br/><br/> Få mere at vide under [Forstå formatet af Værdien InPlaceHolds til opbevaringspolitikker](identify-a-hold-on-an-exchange-online-mailbox.md#understanding-the-format-of-the-inplaceholds-value-for-retention-policies).  <br/> |
|Megan Bowen <br/> | Microsoft 365 med en opbevarings- eller opbevarings- og sletningshandling anvendes på mindst ét element i postkassen  <br/> |Egenskaben `ComplianceTagHoldApplied` angiver, `True` at et element er blevet mærket med en behold- eller behold- eller slet-etiket.  <br/><br/> Desuden indeholder egenskaben GUID `InPlaceHolds` for den Microsoft 365 opbevaringsetiketpolitik, der anvendes på den inaktive postkasse.  <br/><br/> Du kan få mere at vide [under Identificere postkasser i venteposition, fordi der er anvendt en opbevaringsmærkat på en mappe eller et element](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) <br/>  |
|Mario Necaise  <br/> |Opbevaringspolitik for Microsoft 365 hele organisationen fra Microsoft 365 Overholdelsescenter  <br/> |Egenskaben `InPlaceHolds` er tom, den er `LitigationHoldEnabled` og `ComplianceTagHoldApplied` `False` er `False`. Dette angiver, at en eller flere hele (Exchange) placering Microsoft 365 opbevaringspolitikker anvendt på den organisation, som den inaktive postkasse nedarver. <br/><br/> Du kan få mere at [vide under Sådan bekræftes det, at en opbevaringspolitik for hele organisationen anvendes på en postkasse](identify-a-hold-on-an-exchange-online-mailbox.md#how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox) <br/> |
|Abraham McMahon  <br/> |eDiscovery-sags hold i Microsoft 365 Overholdelsescenter  <br/> |Egenskaben  `InPlaceHolds`  indeholder GUID'et for den eDiscovery-sags venteposition, der placeres på den inaktive postkasse. Du kan se, at dette er en eDiscovery-sag, fordi GUID'et starter med præfikset  `UniH` .  <br/><br/> Du kan få mere at vide [under eDiscovery-vente hold](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds). <br/> |
|Pilar Pinilla  <br/> |In-Place venteposition  <br/> |Egenskaben  `InPlaceHolds`  indeholder GUID'et for den In-Place, der er placeret i den inaktive postkasse. Du kan se, at dette In-Place i venteposition, fordi GUID'et ikke starter med et præfiks.  <br/><br/> **BEMÆRK**! Pr. 1. oktober 2020 kan varigheden af ventepositioner for ventepositioner i det 1. oktober 2020 ikke længere ændres. Du kan kun fjerne en In-Place, hvilket medfører sletning af den inaktive postkasse. <br/><br/> Få mere at vide under [Tilbagetrækning af ældre eDiscovery-værktøjer](legacy-ediscovery-retirement.md). <br/> |

## <a name="step-2-change-the-hold-duration-for-an-inactive-mailbox"></a>Trin 2: Ændre varigheden af ventepositionen for en inaktiv postkasse

Når du har identificeret, hvilken type venteposition der er sat i den inaktive postkasse (og om der er flere ventepositioner), er næste trin at ændre varigheden af ventepositionen.  Processen varierer, afhængigt af hvilken type venteposition der er anvendt.

- [Ændre varigheden for en Microsoft 365 opbevaringspolitik](#change-the-duration-for-a-microsoft-365-retention-policy)

- [Ændre varigheden for en Microsoft 365 opbevaringsetiket](#change-the-duration-for-a-microsoft-365-retention-label)

- [Ændre varigheden for et eDiscovery-hold](#change-the-duration-for-an-ediscovery-hold)

- [Ændre varigheden af en retslig venteposition](#change-the-duration-for-a-litigation-hold)

- [Ændre varigheden af en In-Place venteposition](#change-the-duration-for-an-in-place-hold)

### <a name="change-the-duration-for-a-microsoft-365-retention-policy"></a>Ændre varigheden for en Microsoft 365 opbevaringspolitik

Hvis du vil ændre varigheden af ventepositionen for en Microsoft 365-opbevaringspolitik, skal du først identificere den politik, der påvirker den inaktive postkasse, `Get-RetentionCompliancePolicy` ved at køre med det tilknyttede GUID `InPlaceHolds` fra egenskaben i postkassen i Security and Compliance Center PowerShell.

Sørg for at fjerne præfikset og suffikset fra GUID'et, når du kører denne kommando.  Ved f.eks. at bruge eksempeloplysningerne ovenfor ville du tage værdien af derefter at `:3` `mbx` fjerne og resultere i en politik-GUID af `cdbbb86ce60342489bff371876e7f224`.`InPlaceHolds` `mbxcdbbb86ce60342489bff371876e7f224:3`  I dette eksempel kan det være en ide at køre:

```powershell
Get-RetentionCompliancePolicy cdbbb86ce60342489bff371876e7f224 | FL Name
```

Når du kender navnet på politikken, kan du blot ændre opbevaringspolitikken i Microsoft 365 Compliance Center.  Vær opmærksom på, at opbevaringspolitikker typisk anvendes på mere end én placering, så ændring af politikken påvirker alle anvendte placeringer – både inaktive og aktive, hvilket også kan omfatte andre placeringer end Exchange.  Få mere at vide under [Opret og konfigurer opbevaringspolitikker](create-retention-policies.md).  

> [!IMPORTANT]
> Opbevaringspolitikker med [opbevaringslås](retention-preservation-lock.md) aktiveret kan få opbevaringsperioden forlænget, men kan ikke formindskes eller fjernes.

Hvis det er hensigten at ændre opbevaringsperioden for kun inaktive postkasser eller kun specifikke inaktive postkasser, kan du overveje at anvende tilpassede politikomfang[, som](retention.md#adaptive-or-static-policy-scopes-for-retention) kan bruges til individuelt at målrette mod bestemte postkasser – eller postkassetyper, f.eks. inaktive postkasser – ved hjælp af Azure AD og Exchange attributter og egenskaber.

### <a name="change-the-duration-for-a-microsoft-365-retention-label"></a>Ændre varigheden for en Microsoft 365 opbevaringsetiket

På samme måde som med opbevaringspolitikker skal du, når du ændrer opbevaringsvarigheden for en Microsoft 365-opbevaringsetiket, først identificere den politik, der udgiver navnet, der påvirker indholdet i den inaktive postkasse, `Get-RetentionCompliancePolicy` ved at køre med det tilknyttede GUID `InPlaceHolds` fra egenskaben på postkassen i Security and Compliance Center PowerShell.

Sørg for at fjerne præfikset og suffikset fra GUID'et, når du kører denne kommando.  Ved f.eks. at bruge eksempeloplysningerne ovenfor ville du tage værdien af derefter at `:1` `mbx` fjerne og resultere i en politik-GUID af `6fe063689d404a5bb9940eed0f0bf5d2`.`InPlaceHolds` `mbx6fe063689d404a5bb9940eed0f0bf5d2:1`  I dette eksempel kan det være en ide at køre:

```powershell
Get-RetentionCompliancePolicy 6fe063689d404a5bb9940eed0f0bf5d2 | FL Name
```

Når du har identificeret politikken, kan du se, hvilke etiketter der er blevet publiceret og deres indstillinger.  Da etiketter gælder for individuelle elementer, kan du muligvis ikke direkte identificere, hvilken etiket der påvirker indholdet, afhængigt af antallet af etiketter, der publiceres med politikken og deres indstillinger.  

En metode, du kan bruge til at identificere det indhold, hver etiket gælder for, er at bruge [Indholdssøgning](content-search.md).  Ved f.eks. at bruge eksempeloplysningerne ovenfor antages det, at politikken udgiver flere etiketter, hvoraf en hedder "HR-indhold".  Med de rette tilladelser kan en [indholdssøgning køres](microsoft-365-compliance-center-permissions.md) med [New-ComplianceSearch PowerShell-kommandoen](/powershell/module/exchange/new-compliancesearch), der angiver den inaktive postkasses primære SMTP-adresse, skrevet med et punktum (`.`) `-AllowNotFoundExchangeLocationsEnabled $true` og parameteren for at springe validering over:

```powershell
New-ComplianceSearch -Name "MeganB Inactive Mailbox HR-Content Label Search" -ExchangeLocation .meganb@contoso.onmicrosoft.com -AllowNotFoundExchangeLocationsEnabled $true -ContentMatchQuery "compliancetag=HR-Content"
```

Når søgningen er oprettet, kan du starte søgningen ved hjælp af følgende kommando:

```powershell
Start-ComplianceSearch "MeganB Inactive Mailbox HR-Content Label Search"
```

Ved hjælp af denne metode kan du derefter identificere, hvilke etiketter fra den identificerede etiketpolitik, der gælder for indhold i den inaktive postkasse, så du kan ændre deres opbevaringsperioder. Vær opmærksom på, at opbevaringsnavne typisk anvendes på mere end én placering, så ændring af en etiket vil påvirke alle anvendte placeringer og mærket indhold, hvilket også kan omfatte placeringer og andet indhold end Exchange. Få mere at vide under [Opret opbevaringsmærkater, og anvend dem i apps](create-apply-retention-labels.md).

> [!NOTE]
> Ikke alle typer opbevaringsnavne kan ændres.  For nogle etiketter kan du muligvis kun øge opbevaringstiden, og for andre kan du muligvis slet ikke ændre opbevaringsperioden.

### <a name="change-the-duration-for-an-ediscovery-hold"></a>Ændre varigheden for et eDiscovery-hold

Ventepositioner, der er knyttet til eDiscovery-sager, er ventepositioner på ubestemt tid, hvilket betyder, at der ikke er nogen varighed for venteposition, der kan ændres. Elementer opbevares uendeligt, eller indtil [ventepositionen fjernes](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold) , eller sagen lukkes.
  
### <a name="change-the-duration-for-a-litigation-hold"></a>Ændre varigheden af en retslig venteposition

Du skal bruge Exchange Online PowerShell til at ændre varigheden af venteposition for en retslig venteposition, der placeres på en inaktiv postkasse. Du kan ikke bruge EAC. Kør følgende kommando for at ændre varigheden af ventepositionen. I dette eksempel ændres ventepositionens varighed til en ubegrænset tidsperiode:
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldDuration unlimited
```

Resultatet er, at elementer i den inaktive postkasse bevares på ubestemt tid, eller indtil ventepositionen fjernes, eller varigheden af ventepositionen ændres til en anden værdi.
  
> [!TIP]
> Den bedste måde at identificere en inaktiv postkasse på er ved at bruge **værdien Distinguished Name** **Exchange GUID**. Brug af en af disse værdier hjælper med at forhindre utilsigtet angivelse af den forkerte postkasse.

### <a name="change-the-duration-for-an-in-place-hold"></a>Ændre varigheden af en In-Place venteposition

In-Place ventende ændringer er udgået og kan ikke længere ændres. Hvis en inaktiv postkasse har en In-Place hold anvendt på den, kan du ikke ændre varigheden af ventepositionen. Du kan kun fjerne In-Place, hvilket medfører sletning af den inaktive postkasse. Du kan få mere at vide under [Slet en inaktiv postkasse](delete-an-inactive-mailbox.md#remove-in-place-holds).
  
## <a name="more-information"></a>Flere oplysninger

- **Hvordan beregnes ventepositionsvarigheden for et element i en inaktiv postkasse?** Varigheden beregnes ud fra den oprindelige dato, hvor et postkasseelement blev modtaget eller oprettet.
    
- **Hvad sker der, når varigheden af ventepositionen udløber?** Når varigheden af ventepositionen udløber for et postkasseelement i mappen Genoprettelige elementer, slettes elementet permanent (slettes) fra den inaktive postkasse. Hvis der ikke er angivet nogen varighed for ventepositionen i den inaktive postkasse, bliver elementer i mappen Genoprettelige elementer aldrig slettet (medmindre varigheden af ventepositionen for den inaktive postkasse ændres). 
    
- **Er en Exchange MRM-politik stadig behandlet på inaktive postkasser?**  Hvis en MRM-opbevaringspolitik blev anvendt på en postkasse, før den blev inaktiv, vil eventuelle sletningspolitikker (MRM-opbevaringsmærker, der er konfigureret med en **Delete-handling** ) fortsat blive behandlet på den inaktive postkasse. Det betyder, at elementer, der mærkes med en MRM-sletningspolitik, flyttes til mappen Genoprettelige elementer, når en opbevaringsperiode udløber. Disse elementer bliver slettet fra den inaktive postkasse, når varigheden af ventepositionen udløber. Hvis der ikke er angivet en varighed af venteposition for den inaktive postkasse, bevares elementer i mappen Gendan elementer på ubestemt tid.

    Omvendt ignoreres eventuelle arkiveringspolitikker (MRM-opbevaringsmærker,  der er konfigureret med en FlytTilArkiver-handling), der er inkluderet i MRM-opbevaringspolitikken, der er tildelt en inaktiv postkasse. Det betyder, at elementer i en inaktiv postkasse, der mærkes med en arkiveringspolitik, forbliver i den primære postkasse, når en opbevaringsperiode udløber. De flyttes ikke til arkivpostkassen eller til mappen Genoprettelige elementer i arkivpostkassen. De bevares på ubestemt tid.
    > [!NOTE]
    > Når du Exchange opbevaringspolitik (funktionen Messaging Records Management, eller MRM, i Exchange Online) oprettes der ikke en inaktiv postkasse, når brugerkontoen slettes.

- **Som med almindelige postkasser behandler Administreret mappeassistent (MFA) også inaktive postkasser.** I Exchange Online behandler MFA postkasserne ca. én gang hver syv dage. Når du har ændret varigheden af ventepositionen for en inaktiv postkasse, kan du bruge **start-ManagedFolderAssistant-cmdlet'en** til straks at begynde at behandle den nye varighed af venteposition for den inaktive postkasse. Kør følgende kommando. 

    ```powershell
    Start-ManagedFolderAssistant -InactiveMailbox <identity of inactive mailbox>
    ```
   
- **Hvis mange `InPlaceHolds` placeres i en inaktiv postkasse, vises ikke alle GUID'erne i venteposition.** Du kan køre følgende kommando for at få vist GUID'erne for alle, der `InPlaceHolds` er placeret i en inaktiv postkasse.
    
    ```powershell
    Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds
    ```
