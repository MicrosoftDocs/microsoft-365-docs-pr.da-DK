---
title: Konfigurerer Planlægger for Microsoft 365.
ms.author: v-aiyengar
author: AshaIyengar21
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
ms.localizationpriority: medium
description: Konfigurerer Planlægger for Microsoft 365.
ms.openlocfilehash: ef377393134e4d8028ab0e6e40ddcc3647f60695
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953842"
---
# <a name="setting-up-scheduler-for-microsoft-365"></a>Konfiguration af Tidsplan for Microsoft 365

Lejeradministratorer skal konfigurere en scheduler-assistents postkasse og hente Scheduler-licenser til mødearrangører for at aktivere Scheduler for Microsoft 365-tjenesten. 

## <a name="licensing"></a>Licensering

Få mere at vide: [Planlægger for Microsoft 365 licenser](https://www.microsoft.com/microsoft-365/meeting-scheduler-pricing)

> [!NOTE]
> Mødedeltagere behøver ikke en tidsplan eller Microsoft 365 licens.
>
> Postkassen i Scheduler-assistenten kræver ikke en Microsoft 365 eller en Scheduler-licens.

## <a name="prerequisites"></a>Forudsætninger

|Forudsætning|Beskrivelse|
|---|---|
|En planlægningsassistent-postkasse for lejeren |En Exchange ressourcepostkasse af udstyrstypen, der fungerer som Scheduler-assistentens postkasse, så din lejer kan sende og modtage mails til og fra Cortana. Alle mails, der sendes til Cortana, bevares i din lejers Cortana postkasse baseret på din opbevaringspolitik. Planlægningsassistentens postkasse hedder typisk "Cortana" eller "Cortana Scheduler", da alle mails fra assistenten signeres Cortana. <ul><li>Opret en udstyrstype Exchange ressourcepostkasse</li><li>Navngiv postkassens viste navn og primære SMTP-adresse `Cortana <cortana@yourdomain.com>` eller `Cortana Scheduler <cortana.scheduler@yourdomain.com>`.</li></ul> <br/> **Bemærk:** Postkassen i Scheduler-assistenten kræver ikke en Microsoft 365 eller en Scheduler-licens.|
|Exchange Online postkasse |Mødearrangører skal have en Exchange Online postkasse og kalender som regel som en del af deres Microsoft 365 licens. Mødearrangører skal desuden have en scheduler-licens. Scheduler-licensen gør det muligt for Planlægningsassistenten at bruge mødearrangørens postkasse og kalender til at planlægge møder for dem. <br/><br/> Se Scheduler for at få Microsoft 365 for at få oplysninger om licenser og priser. <br/><br/> **Bemærk:** Mødedeltagere behøver ikke en tidsplan eller Microsoft 365 licens. Mødedeltagere kan være interne eller eksterne i forhold til lejeren. Mødedeltagere skal kun have adgang til en mailadresse.|

## <a name="setting-up-the-scheduler-assistant-mailbox"></a>Konfiguration af planlægningsassistentens postkasse

Scheduler Assistant-postkassen er en Exchange udstyrstypepostkasse, der ikke kræver en ekstra Microsoft 365- eller Scheduler-licens. Det viste navn og den primære SMTP-adresse for postkassen skal indeholde Cortana da alle mails fra Scheduler-assistenten signeres Cortana (dvs. `Cortana <cortana@yourdomain.com>` eller `Cortana Scheduler <cortana.scheduler@yourdomain.com>`). Når planlægningsassistentens postkasse er blevet oprettet, skal du angive postkassen som planlægningsassistentens postkasse. Når du har angivet planlægningsassistentens postkasse, vil Cortana være tilgængelige til at planlægge møder på vegne af dine brugere.

- Brug Microsoft 365 Administration til at oprette en brugerpostkasse. En 30-dages opbevaringspolitik anbefales. 
- Brug navnet Cortana i postkassens primære SMTP-adresse. Navne som `Cortana@yourdomain.com`, `CortanaScheduler@contoso.com`eller `Cortana.Scheduler@yourdomain.com` anbefales.

## <a name="designate-the-mailbox-as-the-scheduler-assistant"></a>Angiv postkassen som Planlægningsassistent

Når der er oprettet en entydig postkasse til Cortana Scheduler, skal du angive, at postkassen skal Microsoft 365 formelt. Når du har angivet den Cortana Scheduler-postkasse, vil den være tilgængelig til at planlægge møder på vegne af dine brugere.

### <a name="connect-to-powershell"></a>Forbind til PowerShell

Brug Microsoft 365 Administration til at oprette en brugerpostkasse. En 30-dages opbevaringspolitik anbefales.
Brug navnet Cortana i postkassens primære SMTP-adresse. Navne som `Cortana@yourdomain.com`, `CortanaScheduler@contoso.com`eller `Cortana.Scheduler@yourdomain.com` anbefales.

```PowerShell
$domain="yourdomain.com"
$tenantAdmin="<tenantadmin>@$domain"
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $tenantAdmin
```

### <a name="create-the-scheduler-assistant-mailbox"></a>Opret planlægningsassistentens postkasse

```PowerShell
New-Mailbox -Name Cortana -Organization $domain -DisplayName "Cortana Scheduler" -Equipment 
Set-CalendarProcessing Cortana@$domain -DeleteNonCalendarItems $false 
```

### <a name="designate-the-scheduler-assistant-mailbox"></a>Angiv planlægningsassistentens postkasse

```PowerShell
Set-mailbox cortana@$domain -SchedulerAssistant:$true
```

Når du har kørt denne "set"-kommando på Cortana Scheduler-assistentens postkasse, angives der en ny "PersistedCapability" i postkassen for at bemærke, at denne postkasse er "SchedulerAssistant".

> [!NOTE]
> Hvis du vil vide mere om, hvordan du opretter forbindelse mellem din organisation og PowerShell, [skal du se: Forbind at Microsoft 365 med PowerShell](/microsoft-365/enterprise/connect-to-microsoft-365-powershell)

### <a name="verifying-the-scheduler-assistant-mailbox"></a>Kontrollerer planlægningsassistentens postkasse

Sådan bekræfter du, at planlægningsassistentens postkasse er blevet oprettet

```PowerShell
Get-CalendarProcessing cortana@$domain | fl DeleteNonCalendarItems
```

Resultatet skal være "false".

```PowerShell
Get-Mailbox -Identity cortana@$domain | fl *type*
```

Resultatet skal være

- Ressourcetype: Udstyr
- Fjernmodtagertype: Ingen
- Modtagertype: UserMailbox
- RecipientTypeDetails: EquipmentMailbox

### <a name="to-discover-which-mailbox-is-the-scheduler-assistant-mailbox"></a>Sådan finder du ud af, hvilken postkasse der er planlægningsassistentens postkasse

```PowerShell
Get-Mailbox -ResultSize Unlimited | where {$_.PersistedCapabilities -Match "SchedulerAssistant"}
```

> [!IMPORTANT]
> Det kan tage flere timer for Scheduler-assistentens postkasse at fuldføre fuld klargøring for at angive funktionen SchedulerAssistant.

## <a name="exchange-online-mailbox"></a>Exchange Online postkasse

En scheduler-licens er et tilføjelsesprogram til Microsoft 365, som gør det muligt for mødearrangøren at delegere sine mødeplanlægningsopgaver til deres planlægningsassistent. Ud over at angive en postkasse som en Scheduler-assistent-postkasse skal mødearrangørerne også have en Scheduler-licens og Exchange Online postkasse og kalender, typisk via Microsoft 365 licens, så Scheduler kan arbejde. Mødedeltagere behøver ikke en scheduler-licens eller en Microsoft 365 licens.

Hvis du vil købe tilføjelsesprogrammet Tidsplan, skal du bruge en af følgende licenser:

- Microsoft 365 E3, A3, E5, A5
- Business Basic, Business, Business Standard, Business Premium
- Office 365 E1, A1, E3, A3, E5, A5
- Business Essentials, Business Premium
- Exchange Online Plan 1- eller Plan 2-licens.

> [!NOTE]
> Planlægger for Microsoft 365 er kun tilgængelig i globale miljøer med flere lejere på engelsk. **Planlægger for Microsoft 365** er ikke tilgængelig for brugere af:
>
> - Microsoft 365 drevet af 21Vianet i Kina
> - Microsoft 365 med den tyske cloud, der bruger datatillidscenteret Tysk Telekom
> - Government-cloud, herunder GCC, forbruger, GCC høj eller dod
>
> Scheduler understøtter brugere i Tyskland, hvis dataplacering ikke er det tyske datacenter.
