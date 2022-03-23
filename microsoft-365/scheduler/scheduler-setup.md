---
title: Konfiguration af Scheduler for Microsoft 365.
ms.author: v-aiyengar
author: AshaIyengar21
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
ms.localizationpriority: medium
description: Konfiguration af Scheduler for Microsoft 365.
ms.openlocfilehash: 3315c362a6e6ae1eb4fa9bf54d388a89dd667136
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63592401"
---
# <a name="setting-up-scheduler-for-microsoft-365"></a>Konfiguration af Scheduler for Microsoft 365

Lejeradministratorer skal konfigurere en Scheduler-assistentpostkasse og hente Scheduler-licenser til mødearrangører for at aktivere Scheduler til Microsoft 365 tjeneste. 

## <a name="licensing"></a>Licensering

Få mere at vide: [Scheduler til Microsoft 365 licenser](https://www.microsoft.com/microsoft-365/meeting-scheduler-pricing)

> [!Note]
> Mødedeltagerne behøver ikke en Planlægnings- eller Microsoft 365 licens. <br>Scheduler-assistentpostkassen kræver ikke en Microsoft 365 eller en Scheduler-licens.

## <a name="prerequisites"></a>Forudsætninger

| Forudsætninger | Beskrivelse |
|-------------------|-------------|
|En Scheduler-assistentpostkasse for lejeren |En Exchange ressourcepostkasse af typen Udstyr, der fungerer som Scheduler-assistentpostkassen for din lejer, hvor du kan sende og modtage mails til og Cortana. Alle mails, der Cortana mails, bevares i din lejers Cortana baseret på din opbevaringspolitik. Scheduler-assistentpostkassen kaldes typisk "Cortana" eller "Cortana Scheduler", da alle mails fra assistenten bliver signeret Cortana.<ul><li>Oprette en udstyrstype Exchange ressourcepostkasse</li><li>Navngive postkassens viste navn og primære SMTP-adresse `Cortana <cortana@yourdomain.com>` eller `Cortana Scheduler <cortana.scheduler@yourdomain.com>`.</li></ul>**Bemærk!** Scheduler-assistentpostkassen kræver ikke en Microsoft 365 eller en Scheduler-licens.|
|Exchange Online postkasse |Mødearrangører skal have en Exchange Online-postkasse og -kalender typisk som en del af deres Microsoft 365 licens. Desuden skal mødearrangører have en Scheduler-licens. Scheduler-licensen gør det muligt for Scheduler-assistenten at bruge mødearrangørens postkasse og kalender til at planlægge møder for dem.<br/><br/> Se Scheduler for at Microsoft 365 oplysninger om licenser og priser.  <br/><br/>**Bemærk!** Mødedeltagerne behøver ikke en Planlægnings- eller Microsoft 365 licens. Mødedeltagerne kan være interne eller eksterne i forhold til lejeren. Mødedeltagerne skal kun have adgang til en mailadresse.|


## <a name="setting-up-the-scheduler-assistant-mailbox"></a>Konfiguration af Scheduler-assistentpostkassen

Scheduler-assistentpostkassen er en Exchange af udstyrstype, der ikke kræver en ekstra Microsoft 365 eller Scheduler-licens. Det viste navn og den primære SMTP-adresse for postkassen skal indeholde Cortana, da alle mails fra Scheduler-assistenten bliver signeret Cortana (dvs. `Cortana <cortana@yourdomain.com>` eller `Cortana Scheduler <cortana.scheduler@yourdomain.com>`). Når Scheduler-assistentpostkassen er blevet oprettet, skal du angive postkassen som Scheduler-assistentpostkassen. Når du har udpeget Scheduler-assistentpostkassen, Cortana du mulighed for at planlægge møder på vegne af dine brugere.

- Brug Microsoft 365 Administration til at oprette en brugerpostkasse. En 30-dages opbevaringspolitik anbefales. 
- Brug navnet Cortana din postkasses primære SMTP-adresse. Navne som f.eks`Cortana@yourdomain.com``CortanaScheduler@contoso.com`. , eller `Cortana.Scheduler@yourdomain.com` anbefales.

## <a name="designate-the-mailbox-as-the-scheduler-assistant"></a>Angive postkassen som Planlægningsassistent

Når en entydig postkasse til Cortana Scheduler er blevet oprettet, skal du formelt angive postkassen Microsoft 365 postkassen. Når du har udpeget Cortana Scheduler, vil den være tilgængelig til at planlægge møder på vegne af dine brugere.

#### <a name="connect-to-powershell"></a>Forbind til PowerShell

Brug Microsoft 365 Administration til at oprette en brugerpostkasse. En 30-dages opbevaringspolitik anbefales.
Brug navnet Cortana din postkasses primære SMTP-adresse. Navne som f.eks`Cortana@yourdomain.com``CortanaScheduler@contoso.com`. , eller `Cortana.Scheduler@yourdomain.com` anbefales.

```PowerShell
$domain="yourdomain.com"
$tenantAdmin="<tenantadmin>@$domain"
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $tenantAdmin
```

#### <a name="create-the-scheduler-assistant-mailbox"></a>Opret Scheduler-assistentpostkassen

```PowerShell
New-Mailbox -Name Cortana -Organization $domain -DisplayName "Cortana Scheduler" -Equipment 
Set-CalendarProcessing Cortana@$domain -DeleteNonCalendarItems $false 
```
    
#### <a name="designate-the-scheduler-assistant-mailbox"></a>Angive Scheduler-assistentpostkassen

```PowerShell
Set-mailbox cortana@$domain -SchedulerAssistant:$true
```

Når du har kørt denne "set"-kommando i Cortana Scheduler-assistentpostkassen, angives en ny "PersistedCapability" i postkassen for at bemærke, at denne postkasse er "SchedulerAssistant".

> [!Note]
> Du kan få mere at vide om, hvordan du forbinder din organisation til [PowerShell under: Forbind til Microsoft 365 med PowerShell](/microsoft-365/enterprise/connect-to-microsoft-365-powershell)

### <a name="verifying-the-scheduler-assistant-mailbox"></a>Bekræftelse af Scheduler-assistentpostkassen

Sådan bekræfter du, at Scheduler-assistentpostkassen er blevet oprettet

```PowerShell
Get-CalendarProcessing cortana@$domain | fl DeleteNonCalendarItems
```

Resultatet skal være "falsk".

<br>

```PowerShell
Get-Mailbox -Identity cortana@$domain | fl *type*
```

Resultatet skal være
- ResourceType: Udstyr
- Remote RecipientType: Ingen
- RecipientType: UserMailbox
- RecipientTypeDetails: EquipmentMailbox

<br/>

### <a name="to-discover-which-mailbox-is-the-scheduler-assistant-mailbox"></a>Sådan finder du ud af, hvilken postkasse der er Scheduler-assistentpostkassen

```PowerShell
Get-Mailbox -ResultSize Unlimited | where {$_.PersistedCapabilities -Match "SchedulerAssistant"}
```

> [!Important]
> Det kan tage flere timer, før Scheduler-assistentpostkassen er færdig med at udføre fuld klargøring for at konfigurere SchedulerAssistant-funktionen.


## <a name="exchange-online-mailbox"></a>Exchange Online postkasse

En Scheduler-licens er et tilføjelsesprogram til Microsoft 365, som gør det muligt for mødearrangøren at uddelegere deres mødeplanlægningsopgaver til deres Scheduler-assistent. Ud over at designe en postkasse som en Scheduler-assistentpostkasse skal mødearrangører også have en Scheduler-licens og Exchange Online-postkasse og kalender, typisk via Microsoft 365-licens for at Scheduler kan fungere. Mødedeltagerne behøver ikke en Scheduler-licens eller en Microsoft 365 licens.

For at købe Scheduler-tilføjelsesprogrammet skal du have en af følgende licenser:

- Microsoft 365 E3, A3, E5, A5
- Business Basic, Business, Business Standard, Business Premium
- Office 365 E1, A1, E3, A3, E5, A5
- Business Essentials, Business Premium
- Exchange Online plan 1 eller plan 2 licens. 

> [!Note]
> Planlægger til Microsoft 365 findes kun på engelsk i verdensomspændende miljøer med flere lejere. **Planlægger til Microsoft 365** ikke tilgængelig for brugere af:
> 
> - Microsoft 365 drevet af 21Vianet i Kina
> - Microsoft 365 med tysk sky, der bruger datatillidse tysk Telekom
> - Government-skyen, GCC, forbruger, GCC High eller DoD
> 
> Scheduler understøtter brugere i Tyskland, hvis dataplacering ikke er det tyske datacenter.
