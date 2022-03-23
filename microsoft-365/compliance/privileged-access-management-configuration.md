---
title: Introduktion til administration af adgangspriviligerede rettigheder
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
- admindeeplinkMAC
ms.assetid: ''
description: Brug denne artikel til at få mere at vide om aktivering og konfiguration af administration af adgangspriviligerede rettigheder i Office 365.
ms.openlocfilehash: fd7216b09b17f7f900a9aee98059918a1796fe19
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/01/2022
ms.locfileid: "63588950"
---
# <a name="get-started-with-privileged-access-management"></a>Introduktion til administration af adgangspriviligerede rettigheder

Dette emne fører dig gennem aktivering og konfiguration af administration af adgangspriviligerede rettigheder i organisationen. Du kan bruge enten Microsoft 365 Administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">eller</a> Exchange Management PowerShell til at administrere og bruge privilegeret adgang.

## <a name="before-you-begin"></a>Før du begynder

Før du går i gang med at bruge administration af adgangsrettigheder, [skal du Microsoft 365 dit abonnement](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) og eventuelle tilføjelsesabonnementer. Din organisation skal have et af følgende abonnementer eller tilføjelser for at få adgang til og bruge adgangsstyring:

- Microsoft 365 E5-abonnement (betalt version eller prøveversion)
- Microsoft 365 E3 -abonnement (eller Office 365 E3 + Enterprise Mobility and Security E3-abonnement) + Microsoft 365 E5 Overholdelse-tilføjelsesprogrammet
- Alle Microsoft 365-, Office 365-, Exchange-, SharePoint- eller OneDrive for Business abonnement + Microsoft 365 E5 insider-tilføjelsesprogrammet til risikostyring
- Microsoft 365 A5-abonnement (betalt version eller prøveversion)
- Microsoft 365 A3 -abonnement (eller Office 365 A3 +Enterprise Mobility and Security A3-abonnement) + Tilføjelsesprogrammet Microsoft A5 Compliance
- Alle Microsoft 365-, Office 365-, Exchange-, SharePoint- eller OneDrive for Education-abonnement + Microsoft 365 A5 tilføjelsesprogrammet Insider Risk Management
- Office 365 Enterprise E5-abonnement (betalt version eller prøveversion)
- Office 365 Enterprise E3-abonnement + tilføjelsesprogrammet Avanceret overholdelse i Office 365 (der er ikke længere tilgængeligt for nye abonnementer, se bemærk)

Brugere, der indsender og besvarer anmodninger om adgangstilladelser, skal være tildelt en af licenserne ovenfor.

> [!IMPORTANT]
> Avanceret overholdelse i Office 365 sælges ikke længere som enkeltstående abonnement. Når aktuelle abonnementer udløber, skal kunder overgå til et af abonnementerne ovenfor, som indeholder de samme eller yderligere funktioner til overholdelse af regler og standarder.

Hvis du ikke har en eksisterende Office 365 Enterprise E5-plan og vil prøve administration af adgang med rettigheder, kan du føje [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) til dit eksisterende Office 365-abonnement eller tilmelde dig [en](https://www.microsoft.com/microsoft-365/enterprise) prøveversion af Microsoft 365 Enterprise E5.

## <a name="enable-and-configure-privileged-access-management"></a>Aktivere og konfigurere adgangsstyring med rettigheder

Følg disse trin for at konfigurere og bruge privilegeret adgang i din organisation:

- [Trin 1: Opret en godkenders gruppe](privileged-access-management-configuration.md#step1)

    Før du begynder at bruge adgang til rettigheder, skal du afgøre, hvem der har brug for godkendelsescenteret for indgående anmodninger om adgang til opgaver med administratorrettigheder og tilladelser. Alle brugere, der er en del af Godkenders gruppe, kan godkende anmodninger om adgang. Denne gruppe aktiveres ved at oprette en mailaktiveret sikkerhedsgruppe i Office 365.

- [Trin 2: Aktivér adgang med rettigheder](privileged-access-management-configuration.md#step2)

    Adgang med rettigheder skal eksplicit aktiveres i Office 365 med standardgodkendingsgruppen, herunder et sæt systemkonti, som skal udelukkes fra adgangskontrol for adgangsstyringen.

- [Trin 3: Opret en adgangspolitik](privileged-access-management-configuration.md#step3)

    Når du opretter en godkendelsespolitik, kan du definere de specifikke godkendelseskrav, der er defineret for individuelle opgaver. Indstillingerne for godkendelsestype er **Automatisk eller** **Manuel**.

- [Trin 4: Send/godkend anmodninger om privilegeret adgang](privileged-access-management-configuration.md#step4)

    Når den er aktiveret, kræver privilegeret adgang godkendelse for enhver opgave, der har defineret en tilknyttet godkendelsespolitik. For opgaver, der er inkluderet i en godkendelsespolitik, skal brugere anmode om og få tildelt adgangsgodkendelse for at få de tilladelser, der er nødvendige for at udføre opgaven.

Når der tildeles godkendelse, kan den anmodende bruger udføre den tilsigtede opgave, og den privilegerede adgang tillader og udfører opgaven på vegne af brugeren. Godkendelsen forbliver gyldig i den anmodede varighed (standardvarigheden er 4 timer), hvor anmoderen kan udføre den tilsigtede opgave flere gange. Alle disse eksekveringer logføres og gøres tilgængelige til overvågning af sikkerhed og overholdelse.

> [!NOTE]
> Hvis du vil bruge Exchange Management PowerShell til at aktivere og konfigurere adgangsprivilegitimation, skal du følge trinnene i [Forbind for at Exchange Online PowerShell ved hjælp af Multi-Factor Authentication](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-using-mfa) til at oprette forbindelse til Exchange Online PowerShell med dine Office 365-legitimationsoplysninger. Du behøver ikke at aktivere Multi-Factor Authentication for din organisation for at bruge trinnene til at aktivere privilegeret adgang, når du opretter forbindelse til Exchange Online PowerShell. Oprettelse af forbindelse med multifaktorgodkendelse opretter en godkendelsestoken, der bruges af den privilegerede adgang til signering af dine anmodninger.

<a name="step1"> </a>

## <a name="step-1-create-an-approvers-group"></a>Trin 1: Opret en godkenders gruppe

1. Log på computeren [Microsoft 365 Administration](https://admin.microsoft.com) legitimationsoplysningerne for en administratorkonto i organisationen.

2. I Administration skal du gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**GrupperAdd**</a> >  **en gruppe**.

3. Vælg **mailaktiveret sikkerhedsgruppe** , og udfyld derefter **felterne** Navn, **Gruppemailadresse** **og Beskrivelse** for den nye gruppe.

4. Gem gruppen. Det kan tage et par minutter, før gruppen er helt konfigureret og vises i Microsoft 365 Administration.

5. Vælg den nye godkenders gruppe, og vælg **Rediger** for at føje brugere til gruppen.

6. Gem gruppen.

<a name="step2"> </a>

## <a name="step-2-enable-privileged-access"></a>Trin 2: Aktivér adgang med rettigheder

### <a name="in-the-microsoft-365-admin-center"></a>I Microsoft 365 Administration center

1. Log på Microsoft 365 Administration [ved hjælp](https://admin.microsoft.com) af legitimationsoplysninger for en administratorkonto i organisationen.

2. I Administration skal du gå til **Indstillinger** >  **Org Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged-adgang** > .

3. Aktivere **kontrolelementet Kræv godkendelser for privilegerede** opgaver.

4. Tildel godkenderens gruppe, du oprettede i trin 1, som **gruppen Standardgodkendere**.

5. **Gem** og **luk**.

### <a name="in-exchange-management-powershell"></a>I Exchange Management PowerShell

For at aktivere privilegeret adgang og tildele godkenderens gruppe skal du køre følgende kommando i Exchange Online PowerShell:

```PowerShell
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```

Eksempel:

```PowerShell
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', 'sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> Funktionen Systemkonti gøres tilgængelig for at sikre, at visse automatiseringer i din organisation kan fungere uden afhængighed af privilegeret adgang, men det anbefales dog, at disse undtagelser skal godkendes og godkendes regelmæssigt.

<a name="step3"> </a>

## <a name="step-3-create-an-access-policy"></a>Trin 3: Opret en adgangspolitik

Du kan oprette og konfigurere op til 30 politikker for privilegeret adgang for organisationen.

### <a name="in-the-microsoft-365-admin-center"></a>I Microsoft 365 Administration center

1. Log på Microsoft 365 Administration [ved hjælp](https://admin.microsoft.com) af legitimationsoplysninger for en administratorkonto i organisationen.

2. I Administration skal du gå **til Indstillinger** >  **Org Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged-adgang** > .

3. Vælg **Administrer adgangspolitikker og -anmodninger**.

4. Vælg **Konfigurer politikker,** og **vælg Tilføj en politik**.

5. Vælg de relevante værdier for organisationen fra rullelisten:

    **Politiktype**: Opgave, Rolle eller Rollegruppe

    **Politikområde**: Exchange

    **Politiknavn**: Vælg mellem de tilgængelige politikker

    **Godkendelsestype**: Manuel eller Automatisk

    **Gruppen Godkendelse**: Vælg den godkendergruppe, der blev oprettet i trin 1

6. Vælg **Opret** og derefter **Luk**. Det kan tage et par minutter, før politikken er fuldt konfigureret og aktiveret.

### <a name="in-exchange-management-powershell"></a>I Exchange Management PowerShell

For at oprette og definere en godkendelsespolitik skal du køre følgende kommando i Exchange Online PowerShell:

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```

Eksempel:

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

<a name="step4"> </a>

## <a name="step-4-submitapprove-privileged-access-requests"></a>Trin 4: Send/godkend anmodninger om privilegeret adgang

### <a name="requesting-elevation-authorization-to-execute-privileged-tasks"></a>Anmode om udvidelsesgodkendelse for at udføre opgaver med de tilladelser, der er udført

Anmodninger om privilegeret adgang er gyldige i op til 24 timer, efter anmodningen er sendt. Hvis de ikke godkendes eller afvises, udløber anmodningerne, og adgangen godkendes ikke.

#### <a name="in-the-microsoft-365-admin-center"></a>I Microsoft 365 Administration center

1. Log på Microsoft 365 Administration [ved hjælp](https://admin.microsoft.com) af dine legitimationsoplysninger.

2. I Administration skal du gå **til Indstillinger** >  **Org Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged-adgang** > .

3. Vælg **Administrer adgangspolitikker og -anmodninger**.

4. Vælg **Ny anmodning**. Vælg de relevante værdier for organisationen fra rullelisten:

    **Anmodningstype**: Opgave, Rolle eller Rollegruppe

    **Anmodningsomfang**: Exchange

    **Anmod om**: Vælg mellem de tilgængelige politikker

    **Varighed (timer)**: Antal timer, der anmodes om adgang. Der er ikke nogen grænse for det antal timer, der kan anmodes om.

    **Kommentarer**: Tekstfelt til kommentarer, der er relateret til din adgangsanmodning

5. Vælg **Gem** og derefter **Luk**. Din anmodning sendes til godkenderens gruppe via mail.

#### <a name="in-exchange-management-powershell"></a>I Exchange Management PowerShell

Kør følgende kommando i Exchange Online PowerShell for at oprette og sende en anmodning om godkendelse til godkenderens gruppe:

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```

Eksempel:

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```

### <a name="view-status-of-elevation-requests"></a>Få vist status for anmodninger om udvidelse

Når en anmodning om godkendelse er oprettet, kan udvidelsesanmodningsstatus gennemses i Administration eller i Exchange Management PowerShell ved hjælp af det tilknyttede anmodnings-id.

#### <a name="in-the-microsoft-365-admin-center"></a>I Microsoft 365 Administration

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com) med dine legitimationsoplysninger.

2. I Administration skal du gå til **Indstillinger** >  **Org Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged-adgang** > .

3. Vælg **Administrer adgangspolitikker og -anmodninger**.

4. Vælg **Vis** for at filtrere sendte anmodninger **efter statussen** Afventer, **Godkendt**, Afvist **eller Kundelåskasse**. 

#### <a name="in-exchange-management-powershell"></a>I Exchange Management PowerShell

Kør følgende kommando i powershell Exchange Online for at få vist en godkendelsesanmodningsstatus for et bestemt anmodnings-id:

```PowerShell
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```

Eksempel:

```PowerShell
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>Godkende en anmodning om udvidelsesgodkendelse

Når der oprettes en godkendelsesanmodning, modtager medlemmer af den relevante godkendergruppe en mail og kan godkende den anmodning, der er knyttet til anmodnings-id'et. Anmoderen underrettes om anmodningens godkendelse eller afvisning via mail.

#### <a name="in-the-microsoft-365-admin-center"></a>I Microsoft 365 Administration

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com) med dine legitimationsoplysninger.

2. I Administration skal du gå til **Indstillinger** >  **Org Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged-adgang** > .

3. Vælg **Administrer adgangspolitikker og -anmodninger**.

4. Vælg en angivet anmodning for at få vist detaljerne og for at handle på anmodningen.

5. Vælg **Godkend** for at godkende anmodningen, **eller vælg Afvisning** for at afvise anmodningen. Tidligere godkendte anmodninger kan få adgang tilbagekaldt ved at vælge **Tilbagekald**.

#### <a name="in-exchange-management-powershell"></a>I Exchange Management PowerShell

For at godkende en anmodning om udvidelsesgodkendelse skal du køre følgende kommando Exchange Online PowerShell:

```PowerShell
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```

Eksempel:

```PowerShell
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

Hvis du vil afvise en anmodning om udvidelsesgodkendelse, skal du køre følgende kommando Exchange Online PowerShell:

```PowerShell
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```

Eksempel:

```PowerShell
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

## <a name="delete-a-privileged-access-policy-in-office-365"></a>Slet en politik for adgang med rettigheder i Office 365

Hvis der ikke længere er brug for det i din organisation, kan du slette en politik for adgang med rettigheder.

### <a name="in-the-microsoft-365-admin-center"></a>I Microsoft 365 Administration

1. Log på computeren [Microsoft 365 Administration](https://admin.microsoft.com) legitimationsoplysningerne for en administratorkonto i organisationen.

2. I Administration skal du gå til **Indstillinger** >  **Org Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged-adgang** > .

3. Vælg **Administrer adgangspolitikker og -anmodninger**.

4. Vælg **Konfigurer politikker**.

5. Vælg den politik, du vil slette, og vælg **derefter Fjern politik**.

6. Vælg **Luk**.

### <a name="in-exchange-management-powershell"></a>I Exchange Management PowerShell

Hvis du vil slette en politik for adgang med rettigheder, skal du køre følgende kommando Exchange Online Powershell:

```PowerShell
Remove-ElevatedAccessApprovalPolicy -Identity <identity GUID of the policy you want to delete>
```

## <a name="disable-privileged-access-in-office-365"></a>Deaktiver adgang med rettigheder i Office 365

Hvis det er nødvendigt, kan du deaktivere administration af adgangsrettigheder for din organisation. Deaktivering af privilegeret adgang sletter ikke eventuelle tilknyttede godkendelsespolitikker eller godkendergrupper.

### <a name="in-the-microsoft-365-admin-center"></a>I Microsoft 365 Administration

1. Log [på Microsoft 365 Administration med](https://admin.microsoft.com) legitimationsoplysninger for en administratorkonto i organisationen.

2. I Administration skal du gå **til Indstillinger** >  **Org Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security &**</a> **PrivacyPrivileged-adgang** > .

3. Aktivér **Kræv godkendelser for adgangskontrol for privilegeret** adgang.

### <a name="in-exchange-management-powershell"></a>I Exchange Management PowerShell

For at deaktivere privilegeret adgang skal du køre følgende kommando i Exchange Online Powershell:

```PowerShell
Disable-ElevatedAccessControl
```
