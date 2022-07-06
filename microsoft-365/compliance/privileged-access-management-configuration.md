---
title: Kom i gang med Privileged Access Management
description: Brug denne artikel til at få mere at vide om aktivering og konfiguration af privilegeret adgangsstyring i Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, overholdelse af angivne standarder, privilegeret adgangsstyring
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
ms.openlocfilehash: d53058e89fc1830b6f35eef270d84b99f2cc9f74
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626331"
---
# <a name="get-started-with-privileged-access-management"></a>Kom i gang med Privileged Access Management

I denne artikel får du hjælp til at aktivere og konfigurere privilegeret adgangsstyring i din organisation. Du kan bruge enten <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> eller Exchange Management PowerShell til at administrere og bruge privilegeret adgang.

## <a name="before-you-begin"></a>Før du begynder

Før du går i gang med privilegeret adgangsstyring, skal du bekræfte dit [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) og eventuelle tilføjelsesprogrammer. Hvis du vil have adgang til og bruge privilegeret adgangsstyring, skal din organisation have et af følgende abonnementer eller tilføjelsesprogrammer:

- Microsoft 365 E5 abonnement (betalt version eller prøveversion)
- Microsoft 365 E3 abonnement (eller Office 365 E3 abonnement + Enterprise Mobility- og Security E3-abonnement) + det Microsoft 365 E5 Overholdelse tilføjelsesprogram
- Alle Abonnementer på Microsoft 365, Office 365, Exchange, SharePoint eller OneDrive for Business + tilføjelsesprogrammet Microsoft 365 E5 Insider Risk Management
- Microsoft 365 A5 abonnement (betalt version eller prøveversion)
- Microsoft 365 A3 abonnement (eller Office 365 A3 abonnement + Enterprise Mobility and Security A3-abonnement) + tilføjelsesprogrammet Microsoft A5 Compliance
- Alle Microsoft 365-, Office 365-, Exchange-, SharePoint- eller OneDrive for Education-abonnementer + tilføjelsesprogrammet Microsoft 365 A5 Insider Risk Management
- Office 365 Enterprise E5-abonnement (betalt version eller prøveversion)
- Office 365 Enterprise E3-abonnement + tilføjelsesprogrammet Avanceret overholdelse i Office 365 (ikke længere tilgængeligt for nye abonnementer, se note)

Brugere, der indsender og svarer på anmodninger om privilegeret adgangsstyring, skal tildeles en af ovenstående licenser.

> [!IMPORTANT]
> Avanceret overholdelse i Office 365 sælges ikke længere som et separat abonnement. Når de aktuelle abonnementer udløber, skal kunderne overgå til et af abonnementerne ovenfor, som indeholder de samme eller yderligere funktioner til overholdelse af angivne standarder.

Hvis du ikke har en eksisterende Office 365 Enterprise E5-plan og vil prøve privilegeret adgangsstyring, kan du [føje Microsoft 365](/office365/admin/try-or-buy-microsoft-365) til dit eksisterende Office 365-abonnement eller [tilmelde dig en prøveversion](https://www.microsoft.com/microsoft-365/enterprise) af Microsoft 365 Enterprise E5.

## <a name="enable-and-configure-privileged-access-management"></a>Aktivér og konfigurer privilegeret adgangsstyring

Følg disse trin for at konfigurere og bruge privilegeret adgang i din organisation:

- [Trin 1: Opret en godkenders gruppe](privileged-access-management-configuration.md#step1)

    Før du begynder at bruge rettighedsadgang, skal du bestemme, hvem der har brug for godkendelsesmyndighed for indgående anmodninger om adgang til udvidede og privilegerede opgaver. Alle brugere, der er en del af godkendergruppen, kan godkende adgangsanmodninger. Denne gruppe aktiveres ved at oprette en mailaktiveret sikkerhedsgruppe i Office 365.

- [Trin 2: Aktivér privilegeret adgang](privileged-access-management-configuration.md#step2)

    Privilegeret adgang skal være eksplicit aktiveret i Office 365 med standardgodkendergruppen, herunder et sæt systemkonti, der skal udelukkes fra det privilegerede adgangsstyringskontrolelement.

- [Trin 3: Opret en adgangspolitik](privileged-access-management-configuration.md#step3)

    Når du opretter en godkendelsespolitik, kan du definere de specifikke godkendelseskrav, der er beregnet til individuelle opgaver. Indstillingerne for godkendelsestype er **Automatisk** eller **Manuel**.

- [Trin 4: Indsend/godkend privilegerede adgangsanmodninger](privileged-access-management-configuration.md#step4)

    Når privilegeret adgang er aktiveret, kræver det godkendelser for alle opgaver, der har en tilknyttet godkendelsespolitik defineret. For opgaver, der er inkluderet i en godkendelsespolitik, skal brugerne anmode om og få tildelt adgangsgodkendelse for at have de tilladelser, der er nødvendige for at udføre opgaven.

Når godkendelsen er givet, kan den anmodende bruger udføre den tilsigtede opgave, og privilegeret adgang godkender og udfører opgaven på vegne af brugeren. Godkendelsen forbliver gyldig i den ønskede varighed (standardvarigheden er 4 timer), hvor anmoderen kan udføre den tiltænkte opgave flere gange. Alle disse udførelser logføres og gøres tilgængelige for overvågning af sikkerhed og overholdelse af angivne standarder.

> [!NOTE]
> Hvis du vil bruge Exchange Management PowerShell til at aktivere og konfigurere privilegeret adgang, skal du følge trinnene i [Opret forbindelse til Exchange Online PowerShell ved hjælp af Multi-Factor-godkendelse](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-using-mfa) for at oprette forbindelse til Exchange Online PowerShell med dine legitimationsoplysninger til Office 365. Du behøver ikke at aktivere multifaktorgodkendelse for din organisation for at bruge trinnene til at aktivere privilegeret adgang, mens du opretter forbindelse til Exchange Online PowerShell. Hvis du opretter forbindelse med multifaktorgodkendelse, oprettes der et godkendelsestoken, der bruges af privilegeret adgang til at signere dine anmodninger.

<a name="step1"> </a>

## <a name="step-1-create-an-approvers-group"></a>Trin 1: Opret en godkenders gruppe

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din organisation.

2. I Administration skal du gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupper**</a> > **Tilføj en gruppe**.

3. Vælg **mailaktiveret sikkerhedsgruppe** , og udfyld derefter felterne **Navn**, **Gruppemailadresse** og **Beskrivelse** for den nye gruppe.

4. Gem gruppen. Det kan tage et par minutter, før gruppen er fuldt konfigureret og vises i Microsoft 365 Administration.

5. Vælg den nye godkenders gruppe, og vælg **Rediger** for at føje brugere til gruppen.

6. Gem gruppen.

<a name="step2"> </a>

## <a name="step-2-enable-privileged-access"></a>Trin 2: Aktivér privilegeret adgang

### <a name="in-the-microsoft-365-admin-center"></a>I Microsoft 365 Administration Center

1. Log på [Microsoft 365 Administration Center](https://admin.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din organisation.

2. I Administration skal du gå til **Indstillinger** > **Organisationsindstillinger** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Sikkerhed & Privilegeret adgang til beskyttelse af personlige oplysninger**</a> > .

3. Aktivér kontrolelementet **Kræv godkendelser for privilegerede opgaver** .

4. Tildel godkenderens gruppe, som du oprettede i trin 1, som **gruppen Standardgodkendere**.

5. **Gem** og **luk**.

### <a name="in-exchange-management-powershell"></a>I Exchange Management PowerShell

Hvis du vil aktivere privilegeret adgang og tildele godkenderens gruppe, skal du køre følgende kommando i Exchange Online PowerShell:

```PowerShell
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```

Eksempel:

```PowerShell
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', 'sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> Funktionen Systemkonti er gjort tilgængelig for at sikre, at visse automatiseringer i din organisation kan fungere uden afhængighed af privilegeret adgang, men det anbefales, at sådanne undtagelser er ekstraordinære, og at de tilladte bør godkendes og overvåges regelmæssigt.

<a name="step3"> </a>

## <a name="step-3-create-an-access-policy"></a>Trin 3: Opret en adgangspolitik

Du kan oprette og konfigurere op til 30 privilegerede adgangspolitikker for din organisation.

### <a name="in-the-microsoft-365-admin-center"></a>I Microsoft 365 Administration Center

1. Log på [Microsoft 365 Administration Center](https://admin.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din organisation.

2. I Administration Center skal du gå til **Indstillinger** > **Organisationsindstillinger** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Sikkerhed & Privilegeret adgang til beskyttelse af personlige oplysninger**</a> > .

3. Vælg **Administrer adgangspolitikker og -anmodninger**.

4. Vælg **Konfigurer politikker** , og vælg **Tilføj en politik**.

5. Vælg de relevante værdier for din organisation på rullelisten:

    **Politiktype**: Opgave, Rolle eller Rollegruppe

    **Politikområde**: Exchange

    **Politiknavn**: Vælg mellem de tilgængelige politikker

    **Godkendelsestype**: Manuel eller Automatisk

    **Godkendelsesgruppe**: Vælg den gruppe godkendere, der er oprettet i trin 1

6. Vælg **Opret** og derefter **Luk**. Det kan tage et par minutter, før politikken er fuldt konfigureret og aktiveret.

### <a name="in-exchange-management-powershell"></a>I Exchange Management PowerShell

Hvis du vil oprette og definere en godkendelsespolitik, skal du køre følgende kommando i Exchange Online PowerShell:

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```

Eksempel:

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

<a name="step4"> </a>

## <a name="step-4-submitapprove-privileged-access-requests"></a>Trin 4: Indsend/godkend privilegerede adgangsanmodninger

### <a name="requesting-elevation-authorization-to-execute-privileged-tasks"></a>Anmodning om udvidede tilladelser til udførelse af privilegerede opgaver

Anmodninger om privilegeret adgang er gyldige i op til 24 timer, efter at anmodningen er sendt. Hvis de ikke godkendes eller afvises, udløber anmodningerne, og adgangen godkendes ikke.

#### <a name="in-the-microsoft-365-admin-center"></a>I Microsoft 365 Administration Center

1. Log på [Microsoft 365 Administration Center](https://admin.microsoft.com) ved hjælp af dine legitimationsoplysninger.

2. I Administration Center skal du gå til **Indstillinger** > **Organisationsindstillinger** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Sikkerhed & Privilegeret adgang til beskyttelse af personlige oplysninger**</a> > .

3. Vælg **Administrer adgangspolitikker og -anmodninger**.

4. Vælg **Ny anmodning**. Vælg de relevante værdier for din organisation på rullelisten:

    **Anmodningstype**: Opgave, rolle eller rollegruppe

    **Anmodningsområde**: Exchange

    **Anmodning om**: Vælg mellem de tilgængelige politikker

    **Varighed (timer)**: Antal timer med anmodet adgang. Der er ikke en grænse for det antal timer, der kan anmodes om.

    **Kommentarer**: Tekstfelt til kommentarer, der er relateret til din adgangsanmodning

5. Vælg **Gem** og derefter **Luk**. Din anmodning sendes til godkenderens gruppe via mail.

#### <a name="in-exchange-management-powershell"></a>I Exchange Management PowerShell

Kør følgende kommando i Exchange Online PowerShell for at oprette og sende en godkendelsesanmodning til godkenderens gruppe:

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```

Eksempel:

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```

### <a name="view-status-of-elevation-requests"></a>Vis status for anmodninger om udvidede rettigheder

Når der er oprettet en godkendelsesanmodning, kan status for anmodninger om udvidede rettigheder gennemses i Administration eller i Exchange Management PowerShell ved hjælp af det, der er knyttet til anmodnings-id'et.

#### <a name="in-the-microsoft-365-admin-center"></a>I Microsoft 365 Administration

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com) med dine legitimationsoplysninger.

2. I Administration skal du gå til **Indstillinger** > **Organisationsindstillinger** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Sikkerhed & Privilegeret adgang til beskyttelse af personlige oplysninger**</a> > .

3. Vælg **Administrer adgangspolitikker og -anmodninger**.

4. Vælg **Vis** for at filtrere sendte anmodninger efter status for **ventende**, **godkendt**, **nægtet** eller **kundelåsekasse** .

#### <a name="in-exchange-management-powershell"></a>I Exchange Management PowerShell

Kør følgende kommando i Exchange Online PowerShell for at få vist en godkendelsesanmodningsstatus for et bestemt anmodnings-id:

```PowerShell
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```

Eksempel:

```PowerShell
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>Godkendelse af en anmodning om tilladelse til udvidede rettigheder

Når der oprettes en godkendelsesanmodning, modtager medlemmer af den relevante godkendergruppe en mailmeddelelse og kan godkende den anmodning, der er knyttet til anmodnings-id'et. Anmoderen får besked om anmodningens godkendelse eller afvisning via mail.

#### <a name="in-the-microsoft-365-admin-center"></a>I Microsoft 365 Administration

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com) med dine legitimationsoplysninger.

2. I Administration skal du gå til **Indstillinger** > **Organisationsindstillinger** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Sikkerhed & Privilegeret adgang til beskyttelse af personlige oplysninger**</a> > .

3. Vælg **Administrer adgangspolitikker og -anmodninger**.

4. Vælg en angivet anmodning for at få vist detaljerne og udføre en handling på anmodningen.

5. Vælg **Godkend** for at godkende anmodningen, eller vælg **Afvis** for at afvise anmodningen. Tidligere godkendte anmodninger kan få adgang tilbagekaldt ved at vælge **Tilbagekald**.

#### <a name="in-exchange-management-powershell"></a>I Exchange Management PowerShell

Hvis du vil godkende en anmodning om godkendelse af udvidede rettigheder, skal du køre følgende kommando i Exchange Online PowerShell:

```PowerShell
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```

Eksempel:

```PowerShell
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

Hvis du vil afvise en anmodning om udvidede tilladelser, skal du køre følgende kommando i Exchange Online PowerShell:

```PowerShell
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```

Eksempel:

```PowerShell
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

## <a name="delete-a-privileged-access-policy-in-office-365"></a>Slet en politik for privilegeret adgang i Office 365

Hvis det ikke længere er nødvendigt i din organisation, kan du slette en politik for privilegeret adgang.

### <a name="in-the-microsoft-365-admin-center"></a>I Microsoft 365 Administration

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din organisation.

2. I Administration skal du gå til **Indstillinger** > **Organisationsindstillinger** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Sikkerhed & Privilegeret adgang til beskyttelse af personlige oplysninger**</a> > .

3. Vælg **Administrer adgangspolitikker og -anmodninger**.

4. Vælg **Konfigurer politikker**.

5. Vælg den politik, du vil slette, og vælg derefter **Fjern politik**.

6. Vælg **Luk**.

### <a name="in-exchange-management-powershell"></a>I Exchange Management PowerShell

Hvis du vil slette en politik for privilegeret adgang, skal du køre følgende kommando i Exchange Online Powershell:

```PowerShell
Remove-ElevatedAccessApprovalPolicy -Identity <identity GUID of the policy you want to delete>
```

## <a name="disable-privileged-access-in-office-365"></a>Deaktiver privilegeret adgang i Office 365

Hvis det er nødvendigt, kan du deaktivere privilegeret adgangsstyring for din organisation. Deaktivering af privilegeret adgang sletter ikke tilknyttede godkendelsespolitikker eller godkendergrupper.

### <a name="in-the-microsoft-365-admin-center"></a>I Microsoft 365 Administration

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com) med legitimationsoplysninger for en administratorkonto i din organisation.

2. I Administration Center skal du gå til **Indstillinger** > **Organisationsindstillinger** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Sikkerhed & Privilegeret adgang til beskyttelse af personlige oplysninger**</a> > .

3. Aktivér **Kræv godkendelser for privilegeret adgangskontrol** .

### <a name="in-exchange-management-powershell"></a>I Exchange Management PowerShell

Hvis du vil deaktivere privilegeret adgang, skal du køre følgende kommando i Exchange Online Powershell:

```PowerShell
Disable-ElevatedAccessControl
```
