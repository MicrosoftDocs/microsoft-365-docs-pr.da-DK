---
title: Slet en inaktiv postkasse
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: f5caf497-5e8d-4b7a-bfff-d02942f38150
ms.custom:
- seo-marvel-apr2020
description: Når du ikke længere har brug for at bevare indholdet af en Microsoft 365 inaktiv postkasse, kan du slette den inaktive postkasse permanent.
ms.openlocfilehash: 71223c0b5f53e03d51797e32f249f24146e96dee
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63587687"
---
# <a name="delete-an-inactive-mailbox"></a>Slet en inaktiv postkasse

En inaktiv postkasse bruges til at bevare en tidligere medarbejders mail, når de forlader organisationen. Når du ikke længere har brug for at bevare indholdet af en inaktiv postkasse, kan du slette den inaktive postkasse permanent ved at fjerne ventepositionen. Det er også muligt, at der kan placeres flere ventende filer i en inaktiv postkasse. En inaktiv postkasse kan f.eks. placeres i retslig venteposition og i en eller flere In-Place ventepositioner. Desuden kan en opbevaringspolitik (oprettet i Security and Compliance Center i Office 365 eller Microsoft 365) anvendes på den inaktive postkasse. Du skal fjerne alle ventende filer og opbevaringspolitikker fra en inaktiv postkasse for at slette den. Når du fjerner ventende filer og opbevaringspolitikker, markeres den inaktive postkasse til sletning, og den slettes permanent, når den er behandlet.
  
> [!IMPORTANT]
> Efterhånden som vi fortsætter med at investere på forskellige måder for at bevare postkasseindhold, annoncerer vi tilbagetrækningen af In-Place-ventende ord i Exchange Administration. Det betyder, at du skal bruge retslig tilbageholdelse og opbevaringspolitikker til at oprette en inaktiv postkasse. Fra den 1. juli 2020 kan du ikke oprette nye In-Place i Exchange Online. Men du kan stadig ændre varigheden af ventepositionen på en In-Place i venteposition i en inaktiv postkasse. Men fra den 1. oktober 2020 kan du ikke ændre varigheden af ventepositionen. Du kan kun slette en inaktiv postkasse ved at fjerne In-Place Hold. Eksisterende inaktive postkasser, der In-Place i venteposition, bevares stadig, indtil ventepositionen fjernes. Du kan finde flere oplysninger om tilbagetrækningen In-Place ventende funktioner i [Tilbagetrækning af ældre eDiscovery-værktøjer](legacy-ediscovery-retirement.md).
  
Se afsnittet [Flere oplysninger for at](#more-information) få en beskrivelse af, hvad der sker, efter at ventende data fjernes fra en inaktiv postkasse.
  
## <a name="before-you-delete-an-inactive-mailbox"></a>Før du sletter en inaktiv postkasse

- Du skal bruge en Exchange Online PowerShell til at fjerne en retslig venteposition fra en inaktiv postkasse. Du kan ikke bruge Exchange Administration (EAC). Du kan finde en trinvis vejledning under Forbind [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Du kan kopiere indholdet af en inaktiv postkasse til en anden postkasse, før du fjerner ventepositionen og sletter en inaktiv postkasse. Du kan få mere at vide [under Gendan en inaktiv postkasse Office 365](restore-an-inactive-mailbox.md).

- Hvis du fjerner ventepositionen eller opbevaringspolitikken fra en inaktiv postkasse, og opbevaringsperioden for den blød-slettede postkasse for postkassen er udløbet, slettes postkassen permanent, når den 183-dages blød-slettede opbevaringsperiode for postkassen udløber. Du kan finde flere oplysninger om opbevaringsperioden for den blød-slettede postkasse i [afsnittet Flere](#more-information) oplysninger i denne artikel. Når den inaktive postkasse slettes permanent, kan den ikke gendannes. Før du fjerner ventepositionen, skal du sikre dig, at du ikke længere skal bruge indholdet i postkassen. Hvis du vil genaktivere en inaktiv postkasse, kan du gendanne den. Du kan få mere at vide [under Gendan en inaktiv postkasse Office 365](recover-an-inactive-mailbox.md).

- Du kan finde flere oplysninger om inaktive postkasser i [Få mere at vide om inaktive postkasser](inactive-mailboxes-in-office-365.md).

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>Trin 1: Identificer ventende funktioner i en inaktiv postkasse

Som tidligere nævnt kan en retslig tilbageholdelse, In-Place venteposition eller opbevaringspolitik placeres på en inaktiv postkasse. Det første trin er at identificere ventende plads i en inaktiv postkasse.
  
Kør følgende kommando for at få vist oplysninger om venteposition for alle inaktive postkasser i organisationen.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL DisplayName,Name,IsInactiveMailbox,LitigationHoldEnabled,InPlaceHolds
```

Værdien True for **egenskaben** **LitigationHoldEnabled angiver** , at den inaktive postkasse er i Retslig tilbageholdelse. Hvis en In-Place hold er placeret på en inaktiv postkasse, vises GUID'et for ventepositionen som værdien for egenskaben **InPlaceHolds** . Følgende resultater for to inaktive postkasser viser f.eks., at en retslig tilbageholdelse placeres på Ann Beebe, og at en In-Place Hold- og opbevaringspolitik placeres på Pilar Pinilla.
  
```text
DisplayName           : Ann Beebe
Name                  : annb
IsInactiveMailbox     : True
LitigationHoldEnabled : True
InPlaceHolds          : {}
...
DisplayName           : Pilar Pinilla
Name                  : pilarp
IsInactiveMailbox     : True
LitigationHoldEnabled : False
InPlaceHolds          : {c0ba3ce811b6432a8751430937152491, mbxba6f4ba25b62490aaaa253eea27426ab}
```

> [!TIP]
> Hvis en masse In-Place ventepositioner eller opbevaringspolitikker er placeret på en inaktiv postkasse, vises ikke alle In-Place HOLD-GUID'er. Du kan køre følgende kommando for at få vist alle GUID'erne i egenskaben InPlaceHolds:  `Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds`
  
Hvis du vil have mere at vide om at identificere ventepositioner, [skal du se Sådan identificeres den type venteposition, der er sat i en postkasse](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="step-2-remove-a-hold-from-an-inactive-mailbox"></a>Trin 2: Fjerne en venteposition fra en inaktiv postkasse

Når du har identificeret, hvilken type venteposition der er sat i den inaktive postkasse (og om der er flere ventepositioner), er næste trin at fjerne ventepositionen i postkassen. Som tidligere nævnt skal du fjerne alle ventende filer for at slette en inaktiv postkasse permanent.
  
### <a name="remove-a-litigation-hold"></a>Fjern en retslig venteposition

Som tidligere nævnt skal du bruge en Windows PowerShell at fjerne retslig venteposition fra en inaktiv postkasse. Du kan ikke bruge EAC. Kør følgende kommando for at fjerne en retslig venteposition.
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldEnabled $false
```

> [!TIP]
> Den bedste måde at identificere en inaktiv postkasse på er ved at bruge værdien Distinguished Name Exchange GUID. Brug af en af disse værdier hjælper med at forhindre utilsigtet angivelse af den forkerte postkasse. 
  
### <a name="remove-an-inactive-mailbox-from-a-retention-policy"></a>Fjerne en inaktiv postkasse fra en opbevaringspolitik

Fremgangsmåden til at fjerne en inaktiv postkasse fra en Microsoft 365 opbevaringspolitik afhænger af, om den opbevaringspolitik, der er tildelt den inaktive postkasse, er for hele organisationen eller eksplicit. på den type opbevaringspolitik, der er tildelt den inaktive postkasse.

- Opbevaringspolitikker for hele organisationen er tildelt til alle postkasser i organisationen. Brug **cmdlet'en Get-OrganizationConfig** i Exchange Online PowerShell til at få oplysninger om opbevaringspolitikker for hele organisationen.

- Specifikke opbevaringspolitikker for placeringer, der er tildelt til bestemte postkasser. Dette er politikker, der er tildelt indholdsplaceringer for bestemte brugere. Brug **Get-Mailbox -IncludeInactiveMailbox-cmdlet'en** i Exchange Online PowerShell til at få oplysninger om opbevaringspolitikker, der er tildelt til bestemte inaktive postkasser.

#### <a name="remove-an-inactive-mailbox-from-an-organization-wide-retention-policy"></a>Fjern en inaktiv postkasse fra en opbevaringspolitik for hele organisationen

Kør følgende kommando i Exchange Online PowerShell for at udelukke en inaktiv postkasse fra en opbevaringspolitik for hele organisationen.

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromOrgHolds <retention policy GUID without prefix or suffix>
```

Du kan finde flere oplysninger om opbevaringspolitikker for hele organisationen, der anvendes på en inaktiv postkasse og få GUID'et til en opbevaringspolitik, i afsnittet "Get-OrganizationConfig" i Sådan identificeres [typen](identify-a-hold-on-an-exchange-online-mailbox.md#get-organizationconfig) af venteposition i en postkasse.

Du kan også køre følgende kommando for at fjerne den inaktive postkasse fra alle politikker for hele organisationen:

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromAllOrgHolds
```

#### <a name="remove-an-inactive-mailbox-from-a-specific-location-retention-policy"></a>Fjerne en inaktiv postkasse fra en bestemt opbevaringspolitik for en placering

Kør følgende kommando i [Security & Compliance Center PowerShell for](/powershell/exchange/connect-to-scc-powershell) at fjerne en inaktiv postkasse fra en eksplicit opbevaringspolitik.

```powershell
Set-RetentionCompliancePolicy -Identity <retention policy GUID without prefix or suffix> -AddExchangeLocationException <identity of inactive mailbox>
```

Du kan finde flere oplysninger om, hvordan du identificerer specifikke opbevaringspolitikker for en inaktiv postkasse og får GUID'et til en opbevaringspolitik, i afsnittet "Get-Mailbox" i Sådan identificerer du typen af venteposition i en [postkasse](identify-a-hold-on-an-exchange-online-mailbox.md#get-mailbox).

### <a name="remove-in-place-holds"></a>Fjerne In-Place vente hold

 Der er to måder at fjerne et ventepositions In-Place fra en inaktiv postkasse:
  
- **Slet objektet In-Place Hold**. Hvis den inaktive postkasse, du vil slette permanent, er den eneste kildepostkasse til en In-Place Hold, kan du bare slette In-Place Hold-objektet. 

    > [!NOTE]
    > Du skal deaktivere ventepositionen, før du kan slette In-Place objekt i venteposition. Hvis du forsøger at slette In-Place hold-objekt, der har venteposition aktiveret, får du vist en fejlmeddelelse. 
  
- **Fjern den inaktive postkasse som kildepostkasse i en In-Place hold**. Hvis du vil bevare andre kildepostkasser til en In-Place venteposition, kan du fjerne den inaktive postkasse fra listen over kildepostkasser og bevare In-Place Hold-objektet.

#### <a name="delete-an-in-place-hold"></a>Slet en In-Place venteposition

1. Opret en variabel, der indeholder egenskaberne for den In-Place, du vil slette. Brug In-Place GUID til venteposition, som du fik i [trin 1: Identificer ventepositionerne i en inaktiv postkasse](#step-1-identify-the-holds-on-an-inactive-mailbox).

   ```powershell
   $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
   ```

2. Deaktiver ventepositionen i In-Place venteposition.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -InPlaceHoldEnabled $false
   ```

3. Slet In-Place venteposition.

   ```powershell
   Remove-MailboxSearch $InPlaceHold.Name
   ```

#### <a name="remove-an-inactive-mailbox-from-an-in-place-hold"></a>Fjerne en inaktiv postkasse fra en In-Place hold

Hvis ventepositionen In-Place et stort antal kildepostkasser, er det muligt, at den inaktive postkasse ikke vises på siden Kilder i EAC. Der vises op til 3.000 postkasser på siden **Kilder, når** du redigerer en In-Place i venteposition. Hvis en inaktiv postkasse ikke er angivet på siden  Kilder, kan du bruge Exchange Online PowerShell til at fjerne den fra In-Place Hold. 
  
1. Opret en variabel, der indeholder egenskaberne for den In-Place hold placeret i den inaktive postkasse. Brug In-Place GUID til venteposition, som du fik i [trin 1: Identificer ventepositionerne i en inaktiv postkasse](#step-1-identify-the-holds-on-an-inactive-mailbox).

    ```powershell
    $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
    ```

2. Kontrollér, at den inaktive postkasse er angivet som en kildepostkasse til In-Place Hold. 

   ```powershell
   $InPlaceHold.Sources
   ```

   > [!NOTE]
   > Egenskaben *Kilder* for egenskaben i In-Place identificerer kildepostkasserne ved hjælp af deres *LegacyExchangeDN-egenskaber* . Da denne egenskab entydigt identificerer inaktive postkasser, hjælper  brug af egenskaben Kilder fra In-Place Hold med at forhindre at fjerne den forkerte postkasse. Dette hjælper også med at undgå problemer, hvis to postkasser har samme alias eller SMTP-adresse. 

3. Fjern den inaktive postkasse fra listen over kildepostkasser i variablen. Sørg for at bruge **LegacyExchangeDN** for den inaktive postkasse, der returneres af kommandoen i forrige trin. 

    ```powershell
    $InPlaceHold.Sources.Remove("<LegacyExchangeDN of the inactive mailbox>")
    ```

    Følgende kommando fjerner f.eks. den inaktive postkasse for Pilar Pinilla.

    ```powershell
    $InPlaceHold.Sources.Remove("/o=contoso/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/ cn=9c8dfff651ec4908950f5df60cbbda06-pilarp")
    ```

4. Kontrollér, at den inaktive postkasse fjernes fra listen over kildepostkasser i variablen.

   ```powershell
   $InPlaceHold.Sources
   ```

5. Rediger In-Place med den opdaterede liste over kildepostkasser, som ikke omfatter den inaktive postkasse.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -SourceMailboxes $InPlaceHold.Sources
   ```

6. Kontrollér, at den inaktive postkasse fjernes fra listen over kildepostkasser for In-Place Hold.

   ```powershell
   Get-MailboxSearch $InPlaceHold.Name | FL Sources
   ```

## <a name="more-information"></a>Flere oplysninger

- **En inaktiv postkasse er en type blød-slettet postkasse.** I Exchange Online er en blød-slettet postkasse en postkasse, der er blevet slettet, men som kan gendannes inden for en bestemt opbevaringsperiode. For blød-slettede postkasser, der ikke er i venteposition, kan postkassen gendannes inden for 30 dage. En inaktiv postkasse (en postkasse i venteposition, før den blev slettet) forbliver i en blød-slettet med ventepositionstilstand, indtil ventepositionen fjernes. Når ventepositionen er fjernet fra en inaktiv postkasse, er postkassen ikke længere i inaktiv tilstand. I stedet bliver den blød-slettet og forbliver i Exchange Online i 183 dage fra dagen, hvor ventepositionen blev fjernet og kan gendannes i den periode. Efter 183 dage markeres en blød-slettet postkasse til permanent sletning og kan ikke gendannes.

- **Hvad sker der, når du fjerner ventepositionen på en inaktiv postkasse?** Postkassen behandles som andre blød-slettede postkasser og markeres til permanent sletning, når den 183 dage blød-slettede postkasseopbevaringsperiode udløber. Denne opbevaringsperiode starter på den dato, hvor ventepositionen fjernes fra den inaktive postkasse. Egenskaben *InactiveMailboxRetireTime* angives, når postkasseovergange fra at være inaktive (blød-slettet i venteposition) til ikke længere at være inaktive (blød-slettet uden nogen venteposition). På dette tidspunkt er egenskaben *InactiveMailboxRetireTime* indstillet til den aktuelle dato, hvor overgangen skete. Der er en assistent, der kører (kaldet *MailboxLifeCycle-assistent* ), der søger efter postkasser, der har egenskaben *InactiveMailboxRetireTime* angivet. Hvis "InactiveMailboxRetireTime + 183 dage" er mindre end dags dato, vil den fjerne postkassen.

- **Slettes en inaktiv postkasse permanent, umiddelbart efter at ventepositionen fjernes?** En tidligere inaktiv postkasse vil være tilgængelig i blød-slettet tilstand i 183 dage. Efter 183 dage markeres postkassen til permanent sletning.

- **Hvordan får du vist oplysninger om en inaktiv postkasse, når ventepositionen fjernes?** Når en venteposition er blevet fjernet, og den inaktive postkasse vendes tilbage til en blød-slettet postkasse, returneres den ikke ved hjælp af  *parameteren InactiveMailboxOnly*  med **cmdlet'en Get-Mailbox** . Men du kan få vist oplysninger om postkassen ved hjælp af **kommandoen Get-Mailbox -SoftDeletedMailbox** . Eksempel:

  ```text
  Get-Mailbox -SoftDeletedMailbox -Identity pilarp | FL Name,Identity,LitigationHoldEnabled,In
  Placeholds,WhenSoftDeleted,IsInactiveMailbox,WasInactiveMailbox,InactiveMailboxRetireTime
  Name                   : pilarp
  Identity               : Soft Deleted Objects\pilarp
  LitigationHoldEnabled  : False
  InPlaceHolds           : {}
  WhenSoftDeleted        : 6/16/2020 1:19:04 AM
  IsInactiveMailbox      : False
  WasInactiveMailbox     : True
  InactiveMailboxRetireTime : 9/30/2020 11:16:23 PM
  ```

  I eksemplet ovenfor identificerer egenskaben *WhenSoftDeleted* den blød-slettede dato, som i dette eksempel er 16. juni 2020. Egenskaben *WasInactiveMailbox er angivet* , som om `True` den tidligere var en inaktiv postkasse. Postkassen slettes permanent 183 dage efter den 30. september 2020.
