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
description: Når du ikke længere har brug for at bevare indholdet af en inaktiv microsoft 365-postkasse, kan du slette den inaktive postkasse permanent.
ms.openlocfilehash: a8bdd0cb98d744b6c64f651b7b7bb1754ff4f12e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634483"
---
# <a name="delete-an-inactive-mailbox"></a>Slet en inaktiv postkasse

En inaktiv postkasse bruges til at bevare en tidligere medarbejders mail, når vedkommende forlader din organisation. Når du ikke længere har brug for at bevare indholdet af en inaktiv postkasse, kan du slette den inaktive postkasse permanent ved at fjerne ventepositionen. Det er også muligt, at flere ventepositioner placeres i en inaktiv postkasse. En inaktiv postkasse kan f.eks. placeres i venteposition for procesførelse og på en eller flere In-Place ventepositioner. Derudover kan Microsoft 365-opbevaring anvendes på den inaktive postkasse. Du skal fjerne alle bevarelsespolitikker og opbevaringspolitikker fra en inaktiv postkasse for at slette den. Når du har fjernet politikkerne for bevarelse og opbevaring, markeres den inaktive postkasse til sletning og slettes permanent, når den er behandlet.
  
> [!IMPORTANT]
> Da vi fortsætter med at investere på forskellige måder for at bevare postkasseindhold, annoncerer vi, at In-Place ventepositioner udgår i Exchange Administration. Det betyder, at du skal bruge politikker for retsførelse og opbevaring til at oprette en inaktiv postkasse. Fra og med den 1. juli 2020 kan du ikke oprette nye In-Place Ventepositioner i Exchange Online. Men du kan stadig ændre varigheden af ventepositionen for en In-Place venteposition, der er placeret i en inaktiv postkasse. Fra og med den 1. oktober 2020 kan du dog ikke ændre varigheden af ventepositionen. Du kan kun slette en inaktiv postkasse ved at fjerne In-Place Venteposition. Eksisterende inaktive postkasser, der er på In-Place venteposition, bevares stadig, indtil ventepositionen fjernes. Du kan finde flere oplysninger om udfasning af In-Place ventepositioner under [Udfasning af ældre eDiscovery-værktøjer](legacy-ediscovery-retirement.md).
  
Se afsnittet [Flere oplysninger](#more-information) for at få en beskrivelse af, hvad der sker, når ventepositioner er fjernet fra en inaktiv postkasse.
  
## <a name="before-you-delete-an-inactive-mailbox"></a>Før du sletter en inaktiv postkasse

- Du skal bruge Exchange Online PowerShell til at fjerne ventepositioner fra en inaktiv postkasse. Du kan ikke bruge Exchange Administration eller Microsoft Purview-compliance-portal til disse procedurer. Du kan finde en trinvis vejledning i at bruge Exchange Online PowerShell under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Du kan kopiere indholdet af en inaktiv postkasse til en anden postkasse, før du fjerner ventepositionen og sletter en inaktiv postkasse. Du kan finde flere oplysninger under [Gendan en inaktiv postkasse i Office 365](restore-an-inactive-mailbox.md).

- Hvis du fjerner ventepositions- eller opbevaringspolitikken fra en inaktiv postkasse, og opbevaringsperioden for postkassen til blød sletning er udløbet, slettes postkassen permanent, når den 183-dages periode for blød sletning af postkassen udløber. Du kan få flere oplysninger om opbevaringsperioden for den blød slettede postkasse i afsnittet [Flere oplysninger](#more-information) i denne artikel. Når den inaktive postkasse er slettet permanent, kan den ikke gendannes. Før du fjerner ventepositionen, skal du sørge for, at du ikke længere har brug for indholdet i postkassen. Hvis du vil genaktivere en inaktiv postkasse, kan du gendanne den. Du kan finde flere oplysninger under [Gendan en inaktiv postkasse i Office 365](recover-an-inactive-mailbox.md).

- Du kan finde flere oplysninger om inaktive postkasser under [Få mere at vide om inaktive postkasser](inactive-mailboxes-in-office-365.md).

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>Trin 1: Identificer ventepositionerne i en inaktiv postkasse

Som tidligere nævnt kan en politik for procesførelse, In-Place venteposition eller opbevaring være placeret i en inaktiv postkasse. Det første trin er at identificere ventepositionerne i en inaktiv postkasse.
  
[Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), og kør derefter følgende kommando for at få vist oplysninger om venteposition for alle inaktive postkasser i din organisation.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL DisplayName,Name,IsInactiveMailbox,LitigationHoldEnabled,InPlaceHolds
```

Værdien for egenskaben **True** for egenskaben **LitigationHoldEnabled** angiver, at den inaktive postkasse er i litigation-venteposition. Hvis en In-Place venteposition er placeret i en inaktiv postkasse, vises GUID for ventepositionen som værdien for egenskaben **InPlaceHolds** . Følgende resultater for to inaktive postkasser viser f.eks., at en litigation hold er placeret på Ann Beebe, og at der er placeret en In-Place ventepositions- og opbevaringspolitik på Pilar Pinilla.
  
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
> Hvis en masse In-Place ventepositioner eller opbevaringspolitikker placeres i en inaktiv postkasse, vises ikke alle GUID'er for venteposition for In-Place. Du kan køre følgende kommando for at få vist alle GUID'erne i egenskaben InPlaceHolds:  `Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds`
  
Du kan finde flere oplysninger om, hvordan du identificerer ventepositioner, under [Sådan identificerer du den type venteposition, der er placeret i en postkasse](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="step-2-remove-a-hold-from-an-inactive-mailbox"></a>Trin 2: Fjern en venteposition fra en inaktiv postkasse

Når du har identificeret, hvilken type venteposition der er placeret i den inaktive postkasse (og om der er flere ventepositioner), er det næste trin at fjerne ventepositionerne i postkassen. Som tidligere nævnt skal du fjerne alle ventepositioner for at slette en inaktiv postkasse permanent.
  
### <a name="remove-a-litigation-hold"></a>Fjern en procesførelsesventeposition

Kør følgende PowerShell-kommando for at fjerne en retslig venteposition.
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldEnabled $false
```

> [!TIP]
> Den bedste måde at identificere en inaktiv postkasse på er ved hjælp af værdien Entydigt navn eller Exchange GUID. Brug af en af disse værdier hjælper med at forhindre, at den forkerte postkasse angives ved et uheld. 
  
### <a name="remove-an-inactive-mailbox-from-a-retention-policy"></a>Fjern en inaktiv postkasse fra en opbevaringspolitik

Proceduren for fjernelse af en inaktiv postkasse fra en Opbevaringspolitik for Microsoft 365 afhænger af, om den opbevaringspolitik, der er tildelt den inaktive postkasse, er eksplicit for hele organisationen eller eksplicit:

- Opbevaringspolitikker for hele organisationen, der er tildelt alle postkasser i organisationen. Brug **Cmdlet'en Get-OrganizationConfig** i Exchange Online PowerShell til at få oplysninger om opbevaringspolitikker for hele organisationen.

- Specifikke politikker for placeringsopbevaring, der er tildelt bestemte postkasser. Dette er politikker, der er tildelt bestemte brugeres indholdsplaceringer. Brug **Cmdlet'en Get-Mailbox -IncludeInactiveMailbox** i Exchange Online PowerShell til at få oplysninger om opbevaringspolitikker, der er tildelt bestemte inaktive postkasser.

#### <a name="remove-an-inactive-mailbox-from-an-organization-wide-retention-policy"></a>Fjern en inaktiv postkasse fra en opbevaringspolitik for hele organisationen

Kør følgende PowerShell-kommando for at udelade en inaktiv postkasse fra en opbevaringspolitik for hele organisationen.

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromOrgHolds <retention policy GUID without prefix or suffix>
```

Du kan finde flere oplysninger om, hvordan du identificerer opbevaringspolitikker for hele organisationen, som anvendes på en inaktiv postkasse og henter GUID'et for en opbevaringspolitik, i afsnittet "Get-OrganizationConfig" i [Sådan identificeres den type venteposition, der er placeret i en postkasse](identify-a-hold-on-an-exchange-online-mailbox.md#get-organizationconfig).

Du kan også køre følgende PowerShell-kommando for at fjerne den inaktive postkasse fra alle politikker for hele organisationen:

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromAllOrgHolds
```

#### <a name="remove-an-inactive-mailbox-from-a-specific-location-retention-policy"></a>Fjern en inaktiv postkasse fra en bestemt opbevaringspolitik for en placering

Brug [Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) til at fjerne en inaktiv postkasse fra en eksplicit opbevaringspolitik:

```powershell
Set-RetentionCompliancePolicy -Identity <retention policy GUID without prefix or suffix> -RemoveExchangeLocation <identity of inactive mailbox>
```

Du kan finde flere oplysninger om identifikation af specifikke politikker for placeringsopbevaring, der anvendes på en inaktiv postkasse, og hente GUID'et for en opbevaringspolitik i afsnittet "Hent-postkasse" i [Sådan identificeres den type venteposition, der er placeret i en postkasse](identify-a-hold-on-an-exchange-online-mailbox.md#get-mailbox).

### <a name="remove-in-place-holds"></a>Fjern In-Place ventepositioner

 Der er to måder at fjerne en In-Place venteposition fra en inaktiv postkasse på:
  
- **Slet objektet In-Place venteposition**. Hvis den inaktive postkasse, du vil slette permanent, er den eneste kildepostkasse for en In-Place venteposition, kan du blot slette objektet In-Place Venteposition. 

    > [!NOTE]
    > Du skal deaktivere ventepositionen, før du kan slette et objekt af typen In-Place venteposition. Hvis du forsøger at slette et In-Place ventepositionsobjekt, hvor ventepositionen er aktiveret, får du vist en fejlmeddelelse. 
  
- **Fjern den inaktive postkasse som en kildepostkasse for en In-Place venteposition**. Hvis du vil bevare andre kildepostkasser for en In-Place venteposition, kan du fjerne den inaktive postkasse fra listen over kildepostkasser og beholde objektet In-Place Venteposition.

#### <a name="delete-an-in-place-hold"></a>Slet en In-Place venteposition

1. Opret en variabel, der indeholder egenskaberne for den In-Place venteposition, du vil slette. Brug det GUID for In-Place venteposition, som du fik i [trin 1: Identificer ventepositionerne i en inaktiv postkasse](#step-1-identify-the-holds-on-an-inactive-mailbox).

   ```powershell
   $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
   ```

2. Deaktiver ventepositionen på In-Place Venteposition.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -InPlaceHoldEnabled $false
   ```

3. Slet den In-Place venteposition.

   ```powershell
   Remove-MailboxSearch $InPlaceHold.Name
   ```

#### <a name="remove-an-inactive-mailbox-from-an-in-place-hold"></a>Fjern en inaktiv postkasse fra en In-Place venteposition

Hvis den In-Place venteposition indeholder et stort antal kildepostkasser, er det muligt, at den inaktive postkasse ikke vises på siden **Kilder** i EAC. Der vises op til 3.000 postkasser på siden **Kilder** , når du redigerer en In-Place venteposition. Hvis en inaktiv postkasse ikke er angivet på siden **Kilder**, kan du bruge Exchange Online PowerShell til at fjerne den fra In-Place Venteposition. 
  
1. Opret en variabel, der indeholder egenskaberne for den In-Place Venteposition, der er placeret i den inaktive postkasse. Brug det GUID for In-Place venteposition, som du fik i [trin 1: Identificer ventepositionerne i en inaktiv postkasse](#step-1-identify-the-holds-on-an-inactive-mailbox).

    ```powershell
    $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
    ```

2. Kontrollér, at den inaktive postkasse er angivet som en kildepostkasse for In-Place Venteposition. 

   ```powershell
   $InPlaceHold.Sources
   ```

   > [!NOTE]
   > Egenskaben *Sources* for den In-Place Venteposition identificerer kildepostkasserne ved hjælp af deres *LegacyExchangeDN-egenskaber* . Da denne egenskab entydigt identificerer inaktive postkasser, hjælper brugen af egenskaben *Sources* fra den In-Place venteposition med at forhindre, at den forkerte postkasse fjernes. Dette hjælper også med at undgå problemer, hvis to postkasser har samme alias eller SMTP-adresse. 

3. Fjern den inaktive postkasse fra listen over kildepostkasser i variablen. Sørg for at bruge **LegacyExchangeDN** for den inaktive postkasse, der returneres af kommandoen i det forrige trin. 

    ```powershell
    $InPlaceHold.Sources.Remove("<LegacyExchangeDN of the inactive mailbox>")
    ```

    Følgende kommando fjerner f.eks. den inaktive postkasse for Pilar Pinilla.

    ```powershell
    $InPlaceHold.Sources.Remove("/o=contoso/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/ cn=9c8dfff651ec4908950f5df60cbbda06-pilarp")
    ```

4. Kontrollér, at den inaktive postkasse er fjernet fra listen over kildepostkasser i variablen.

   ```powershell
   $InPlaceHold.Sources
   ```

5. Rediger den In-Place Venteposition med den opdaterede liste over kildepostkasser, som ikke indeholder den inaktive postkasse.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -SourceMailboxes $InPlaceHold.Sources
   ```

6. Kontrollér, at den inaktive postkasse er fjernet fra listen over kildepostkasser for den In-Place venteposition.

   ```powershell
   Get-MailboxSearch $InPlaceHold.Name | FL Sources
   ```

## <a name="more-information"></a>Flere oplysninger

- **En inaktiv postkasse er en type blød slettet postkasse.** I Exchange Online er en blød slettet postkasse en postkasse, der er blevet slettet, men som kan gendannes inden for en bestemt opbevaringsperiode. Postkassen kan gendannes inden for 30 dage for postkasser, der ikke er i venteposition. En inaktiv postkasse (en postkasse i venteposition, før den blev slettet) forbliver i en blød slettet postkasse med ventepositionstilstand, indtil ventepositionen fjernes. Når ventepositionen er fjernet fra en inaktiv postkasse, vil postkassen ikke længere være i en inaktiv tilstand. I stedet bliver den slettet blød og forbliver i Exchange Online i 183 dage fra den dag, hvor ventepositionen blev fjernet og kan genoprettes i løbet af den pågældende periode. Efter 183 dage er en blød slettet postkasse markeret til permanent sletning og kan ikke gendannes.

- **Hvad sker der, når du har fjernet ventepositionen på en inaktiv postkasse?** Postkassen behandles som andre blød slettede postkasser og er markeret til permanent sletning, når den 183-dages opbevaringsperiode for blød slettede postkasser udløber. Denne opbevaringsperiode starter den dato, hvor ventepositionen fjernes fra den inaktive postkasse. Egenskaben *InactiveMailboxRetireTime* angives, når postkassen skifter fra at være inaktiv (blød slettet i venteposition) til ikke længere at være inaktiv (blød slettet uden ventepositioner). På det tidspunkt er egenskaben *InactiveMailboxRetireTime* angivet til den aktuelle dato, da overgangen fandt sted. Der er en assistent, der kører (kaldet *MailboxLifeCycle-assistenten* ), der søger efter postkasser, hvor egenskaben *InactiveMailboxRetireTime* er angivet. Hvis "InactiveMailboxRetireTime + 183 dage" er mindre end den aktuelle dato, fjernes postkassen.

- **Slettes en inaktiv postkasse permanent, umiddelbart efter at ventepositionen er fjernet?** En tidligere inaktiv postkasse vil være tilgængelig i tilstanden med blød sletning i 183 dage. Efter 183 dage markeres postkassen til permanent sletning.

- **Hvordan får du vist oplysninger om en inaktiv postkasse, når ventepositionen er fjernet?** Når en venteposition er fjernet, og den inaktive postkasse vender tilbage til en blød slettet postkasse, returneres den ikke ved hjælp af parameteren  *InactiveMailboxOnly*  med **cmdlet'en Get-Mailbox** . Men du kan få vist oplysninger om postkassen ved hjælp af kommandoen **Get-Mailbox -SoftDeletedMailbox** . Eksempel:

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

  I ovenstående eksempel identificerer egenskaben *WhenSoftDeleted* datoen for blød sletning, som i dette eksempel er den 16. juni 2020. Egenskaben *WasInactiveMailbox* er angivet, som `True` om den tidligere var en inaktiv postkasse. Postkassen slettes permanent 183 dage efter den 30. september 2020.
