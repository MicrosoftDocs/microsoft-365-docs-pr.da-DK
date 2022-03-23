---
title: Oprette og administrere inaktive postkasser
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
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 296a02bd-ebde-4022-900e-547acf38ddd7
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
description: Opret og administrer inaktive postkasser, der bevarer indholdet af slettede postkasser i Microsoft 365.
ms.openlocfilehash: 18bcc4c69fc15ea44253bbc4b0f5d5813cc23085
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63589110"
---
# <a name="create-and-manage-inactive-mailboxes"></a>Oprette og administrere inaktive postkasser

Inaktive postkasser gør det muligt at bevare tidligere medarbejderes mail, når de forlader organisationen, og de kan tilgås af autoriserede personer, der har fået [eDiscovery-tilladelser af overholdelseshensyn](assign-ediscovery-permissions.md) eller af juridiske årsager. Eksempelvis administratorer, dem der er ansvarlige for overholdelse af regler og standarder og dataadministratorer, som derefter kan bruge indholdssøgning til at søge efter og eksportere indholdet af en inaktiv postkasse. Inaktive postkasser kan ikke modtage mails og vises ikke i organisationens delte adressekartotek eller andre lister.

Du kan finde flere oplysninger om inaktive postkasser i [Få mere at vide om inaktive postkasser](inactive-mailboxes-in-office-365.md).

## <a name="create-an-inactive-mailbox"></a>Oprette en inaktiv postkasse

Når en postkasse skal være inaktiv, skal postkassen være i venteposition og derefter slettes postkassen eller den tilhørende brugerkonto.

For at gøre en postkasse inaktiv skal den tildeles en Exchange Online Plan 2-licens (eller en Exchange Online Plan 1-licens med en licens til Exchange Online-arkivering-tilføjelsesprogrammet), så postkassen kan opbevares, før den slettes. Når brugerkontoen er slettet, vil alle Exchange Online licens, der er knyttet til brugerkontoen, være tilgængelige for at tildele den til en ny bruger.

Vi anbefaler, at du Microsoft 365 opbevaring til at anvende ventepositionen på postkassen. Andre metoder er dækket under Få [mere at vide om inaktive postkasser](inactive-mailboxes-in-office-365.md).

Den bedste måde at slette en postkasse på er at slette den tilsvarende brugerkonto i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Hvis du vil have mere at vide om at slette brugerkonti, [skal du se Slet en bruger fra organisationen](../admin/add-users/delete-a-user.md). Du kan dog også slette postkassen ved hjælp af **cmdlet'en Remove-Mailbox** i Exchange Online PowerShell. Få mere at vide under [Slet eller gendan brugerpostkasser i Exchange Online](/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes).

Følgende tabel opsummerer processen med at gøre en inaktiv postkasse til forskellige opbevaringsscenarier.

<br/>

|Hvis du vil ...|Skal du...|Resultat|
|---|---|---|
|Bevare postkasseindhold på ubestemt tid, når en medarbejder forlader organisationen|1. Anvend Microsoft 365 opbevaringsindstillinger med opbevaringshandlinger for postkassen (en opbevaringspolitik) eller bestemte mailelementer (et eller flere opbevaringsmærkater). <br /><br> 2. Vent på, at opbevaringsindstillingerne anvendes. <br /><br> 3. Fjern brugerens konto Microsoft 365 konto.|Alt indhold i den inaktive postkasse, hvor der er anvendt opbevaringsindstillinger, herunder elementer i mappen Genoprettelige elementer, bevares på ubestemt tid.|
|Bevare alt postkasseindhold i en bestemt periode, efter en medarbejder forlader organisationen og derefter slette postkassen|1. Anvend Microsoft 365 opbevaringspolitik på postkassen med opbevaringsindstillinger, der bevarer og derefter sletter elementer, når en opbevaringsperiode udløber. <br /><br> 2. Vent på, at opbevaringsindstillingerne anvendes. <br /><br> 3. Fjern brugerens konto Microsoft 365 konto.|Når en postkasses opbevaringsperiode udløber, flyttes elementet til mappen Genoprettelige elementer, og derefter slettes det permanent (slettes) fra den inaktive postkasse, når opbevaringsperioden for slettede elementer (for Exchange postkasser) udløber. Opbevaringsperioden for opbevaringspolitikken Microsoft 365 baseret på den oprindelige dato, hvor et postkasseelement blev modtaget eller oprettet.|


> [!NOTE]
> Hvis Microsoft 365 opbevaringsindstillinger, der er konfigureret til at bevare eller bevare og derefter slette indhold, er allerede anvendt på postkassen eller postkasseelementer, eller en retslig tilbageholdelse allerede er placeret på en postkasse, eller derefter skal du kun slette den tilsvarende brugerkonto for at oprette en inaktiv postkasse.


## <a name="view-a-list-of-inactive-mailboxes"></a>Få vist en liste over inaktive postkasser

Sådan får du vist en liste over de inaktive postkasser i organisationen:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter og</a> log på med legitimationsoplysningerne for en Global administrator eller en Overholdelsesadministrator-konto i organisationen.

2. I venstre navigationsrude skal du klikke **på Vis alle** og derefter klikke **på Information** **governanceRetention** > .

   ![Klik på knappen Inaktiv postkasse på siden Opbevaring.](../media/MCCInactiveMailboxes1.png)

3. Klik på **Inaktiv** postkasse på **siden Opbevaring for at** få vist en liste over inaktive postkasser.

4. Vælg en inaktiv postkasse for at få vist en pop op-side med oplysninger om den inaktive postkasse.

   ![Pop op-siden viser oplysninger om den inaktive postkasse.](../media/MCCInactiveMailboxes2.png)  

Du kan klikke på ![ikonet Eksportér søgeresultater.](../media/47205c65-babd-4b3a-bd7b-98dfd92883ba.png) **Eksportér** for at få vist eller hente en CSV-fil, der indeholder flere oplysninger om de inaktive postkasser i organisationen.

Alternativt kan du køre følgende kommando i Exchange Online PowerShell for at få vist listen over inaktive postkasser.

```powershell
 Get-Mailbox -InactiveMailboxOnly | FT DisplayName,PrimarySMTPAddress,WhenSoftDeleted
```

Du kan også køre følgende kommando for at eksportere listen over inaktive postkasser og andre oplysninger til en CSV-fil. I dette eksempel oprettes CSV-filen i den aktuelle mappe.

```powershell
Get-Mailbox -InactiveMailboxOnly | Select Displayname,PrimarySMTPAddress,DistinguishedName,ExchangeGuid,WhenSoftDeleted | Export-Csv InactiveMailboxes.csv -NoType
```

> [!NOTE]
> Det er muligt, at en inaktiv postkasse kan have den samme SMTP-adresse som en aktiv brugerpostkasse. I dette tilfælde kan værdien af **egenskaben DistinguishedName** eller **ExchangeGuid** bruges til entydigt at identificere en inaktiv postkasse.
  
## <a name="search-and-export-the-contents-of-an-inactive-mailbox"></a>Søg efter og eksportér indholdet af en inaktiv postkasse

Du kan få adgang til indholdet af den inaktive postkasse ved hjælp af værktøjet Indholdssøgning i Microsoft 365 Overholdelsescenter. Når du søger i en inaktiv postkasse, kan du oprette en søgeordsforespørgsel til at søge efter bestemte elementer, eller du kan returnere hele indholdet af den inaktive postkasse. Du kan gennemse søgeresultaterne eller eksportere søgeresultaterne til en Outlook datafil (PST) eller som individuelle mails. Hvis du vil have en trinvis vejledning i at søge i postkasser og eksportere søgeresultater, skal du se følgende emner:
  
- [Indholdssøgning](content-search.md)

- [Eksportér søgeresultater](export-search-results.md)

Her er nogle ting, du skal huske på, når du søger i inaktive postkasser.
  
- Hvis en indholdssøgning omfatter en brugerpostkasse, og den pågældende postkasse gøres inaktiv, fortsætter indholdssøgningen med at søge i den inaktive postkasse, når du kører søgningen igen, efter at den bliver inaktiv.

- I nogle tilfælde kan en bruger have en aktiv postkasse og en inaktiv postkasse, der har samme SMTP-adresse. I dette tilfælde søges der kun i den specifikke postkasse, du vælger som en placering til en indholdssøgning. Med andre ord, hvis du føjer en brugers postkasse til en søgning, kan du ikke gå ud fra, at der søges i både deres aktive og inaktive postkasser. Søges der kun i den postkasse, du eksplicit føjer til søgningen.

- Vi anbefaler på det kraftigste, at du undgår at have en aktiv postkasse og en inaktiv postkasse med den samme SMTP-adresse. Hvis du har brug for at genbruge DEN SMTP-adresse, der aktuelt er tildelt en inaktiv postkasse, anbefaler vi, at du gendanner den inaktive postkasse eller gendanner indholdet i en inaktiv postkasse til en aktiv postkasse (eller arkivet for en aktiv postkasse) og derefter sletter den inaktive postkasse.

## <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Ændre varigheden af ventepositionen for en inaktiv postkasse

Når en postkasse er gjort inaktiv, kan du muligvis ændre varigheden af den venteposition, der anvendes på den inaktive postkasse.

Du kan finde trinvise fremgangsmåder under Ændre [varigheden af venteposition for en inaktiv postkasse](change-the-hold-duration-for-an-inactive-mailbox.md).
  
## <a name="recover-an-inactive-mailbox"></a>Gendan en inaktiv postkasse

Hvis en tidligere medarbejder vender tilbage til organisationen, eller hvis en ny medarbejder ansættes til at tage ansvaret for jobbet for den afgåede medarbejder, kan du gendanne indholdet i den inaktive postkasse. 

Når du gendanner en inaktiv postkasse, konverteres postkassen til en ny postkasse, indholdet og mappestrukturen for den inaktive postkasse bevares, og postkassen sammenkædes med en ny brugerkonto. Når den er gendannet, findes den inaktive postkasse ikke længere. 

Du kan finde trinvise procedurer og flere oplysninger om, hvad der sker, når du gendanner en inaktiv postkasse, under [Gendanne en inaktiv postkasse](recover-an-inactive-mailbox.md).
  
## <a name="restore-the-contents-of-an-inactive-mailbox-to-another-mailbox"></a>Gendanne indholdet af en inaktiv postkasse til en anden postkasse

Hvis en anden medarbejder påtager sig en tidligere medarbejders arbejdsansvarsområde, eller hvis en anden person skal have adgang til indholdet af den inaktive postkasse, kan du gendanne (eller flette) indholdet af den inaktive postkasse i en eksisterende postkasse. 

Når du gendanner en inaktiv postkasse, kopieres indholdet til en anden postkasse. Den inaktive postkasse bevares og forbliver en inaktiv postkasse. Den inaktive postkasse kan stadig søges ved hjælp af eDiscovery, dens indhold kan gendannes til en anden postkasse, eller den kan gendannes eller slettes på et senere tidspunkt. 

Du kan finde trinvise fremgangsmåder under Gendanne [en inaktiv postkasse](restore-an-inactive-mailbox.md).
  
## <a name="delete-an-inactive-mailbox"></a>Slet en inaktiv postkasse

Hvis du ikke længere har brug for at bevare indholdet af en inaktiv postkasse, kan du slette den inaktive postkasse permanent ved at fjerne den venteposition, der gælder for den inaktive postkasse. Postkassen bevares i 183 dage, efter du har fjernet ventepositionen eller opbevaringspolitikken og kan gendannes i den periode. Efter 183 dage markeres postkassen til permanent sletning, og postkassen kan ikke gendannes. 

Du kan finde trinvise fremgangsmåder til at fjerne en venteposition eller en opbevaringspolitik for permanent at slette en inaktiv postkasse i [Slet en inaktiv postkasse](delete-an-inactive-mailbox.md).
