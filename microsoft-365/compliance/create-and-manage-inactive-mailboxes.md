---
title: Opret og administrer inaktive postkasser
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
ms.openlocfilehash: 485352f292321ccfa56e59451cf017c01f3d7fdd
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/13/2022
ms.locfileid: "65393360"
---
# <a name="create-and-manage-inactive-mailboxes"></a>Opret og administrer inaktive postkasser

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Inaktive postkasser giver dig mulighed for at bevare tidligere medarbejderes mail, når de forlader organisationen, og du kan få adgang til dem af godkendte personer, der har fået tildelt [eDiscovery-tilladelser](assign-ediscovery-permissions.md) af hensyn til overholdelse af angivne standarder eller juridiske årsager. Det kan f.eks. være administratorer, overholdelsesansvarlige og dataadministratorer, der derefter kan bruge Indholdssøgning til at søge efter og eksportere indholdet af en inaktiv postkasse. Inaktive postkasser kan ikke modtage mail og vises ikke i organisationens delte adressekartotek eller andre lister.

Du kan finde flere oplysninger om inaktive postkasser under [Få mere at vide om inaktive postkasser](inactive-mailboxes-in-office-365.md).

## <a name="create-an-inactive-mailbox"></a>Opret en inaktiv postkasse

Hvis en postkasse skal være inaktiv, skal postkassen være i venteposition, og postkassen eller den tilsvarende brugerkonto skal slettes.

Hvis du vil gøre en postkasse inaktiv, skal den tildeles en Exchange Online Plan 2-licens (eller en Exchange Online Plan 1-licens med en Exchange Online-arkivering licens til tilføjelsesprogrammet), så der kan anvendes en venteposition på postkassen, før den slettes. Når brugerkontoen er slettet, vil alle Exchange Online licenser, der er knyttet til brugerkontoen, være tilgængelige for en ny bruger.

Vi anbefaler, at du bruger Microsoft 365 opbevaring til at anvende ventepositionen på postkassen. Andre metoder beskrives i [Få mere at vide om inaktive postkasser](inactive-mailboxes-in-office-365.md).

Den bedste måde at slette en postkasse på er ved at slette den tilsvarende brugerkonto i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Du kan få oplysninger om sletning af brugerkonti under [Slet en bruger fra din organisation](../admin/add-users/delete-a-user.md). Du kan dog også slette postkassen ved hjælp af cmdlet'en **Fjern postkasse** i Exchange Online PowerShell. Du kan finde flere oplysninger under [Slet eller gendan brugerpostkasser i Exchange Online](/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes).

I følgende tabel opsummeres processen med at oprette en inaktiv postkasse til forskellige opbevaringsscenarier.

<br/>

|Til...|Gør dette...|Resultat|
|---|---|---|
|Bevar postkasseindholdet på ubestemt tid, når en medarbejder forlader organisationen|1. Anvend Microsoft 365 opbevaringsindstillinger med opbevaringshandlinger for postkassen (en opbevaringspolitik) eller bestemte mailelementer (et eller flere opbevaringsmærkater). <br /><br> 2. Vent på, at opbevaringsindstillingerne anvendes. <br /><br> 3. Fjern brugerens Microsoft 365 konto.|Alt indhold i den inaktive postkasse, hvor der er anvendt opbevaringsindstillinger, herunder elementer i mappen Gendanbare elementer, bevares på ubestemt tid.|
|Bevar alt postkasseindhold i en bestemt periode, når en medarbejder forlader organisationen, og slet derefter postkassen|1. Anvend en Microsoft 365 opbevaringspolitik på postkassen med opbevaringsindstillinger, der bevarer og derefter sletter elementer, når opbevaringsperioden udløber. <br /><br> 2. Vent på, at opbevaringsindstillingerne anvendes. <br /><br> 3. Fjern brugerens Microsoft 365 konto.|Når opbevaringsperioden for et postkasseelement udløber, flyttes elementet til mappen Gendanbare elementer, og det slettes permanent (fjernes) fra den inaktive postkasse, når opbevaringsperioden for slettede elementer (for Exchange postkasser) udløber. Opbevaringsperioden for den Microsoft 365 opbevaringspolitik er altid baseret på den oprindelige dato, hvor et postkasseelement blev modtaget eller oprettet.|


> [!NOTE]
> Hvis Microsoft 365 opbevaringsindstillinger, der er konfigureret til at bevare eller bevare og derefter slette indhold, allerede er anvendt på postkassen eller postkasseelementerne, eller der allerede er placeret en retslig venteposition på en postkasse, eller så skal du kun slette den tilsvarende brugerkonto for at oprette en inaktiv postkasse.


## <a name="view-a-list-of-inactive-mailboxes"></a>Få vist en liste over inaktive postkasser

Sådan får du vist en liste over de inaktive postkasser i din organisation:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a>, og log på med legitimationsoplysningerne for en Global administrator- eller en overholdelsesadministratorkonto i din organisation.

2. Vælg **Vis alle** i navigationsruden til venstre, og vælg derefter **Administration af** >  datalivscyklusRetentionspolitikker.

3. Vælg indstillingen **Inaktiv postkasse** :

   ![Indstillingen Inaktiv postkasse på siden Opbevaringspolitikker fra administration af datalivscyklus.](../media/inactive-mailbox-option.png)

4. På siden **Inaktive postkasser** vises en liste over inaktive postkasser. Vælg en for at få vist oplysninger om den inaktive postkasse. Detaljerne omfatter, hvor længe det har været inaktivt, Exchange-id' et, hvornår det blev sat i venteposition.

På siden **Inaktive postkasser** skal du vælge ![Ikonet Eksportér søgeresultater.](../media/47205c65-babd-4b3a-bd7b-98dfd92883ba.png) **Eksportér** for at få vist eller downloade en CSV-fil, der indeholder flere oplysninger om de inaktive postkasser i din organisation.

Du kan også køre følgende kommando i Exchange Online PowerShell for at få vist listen over inaktive postkasser:

```powershell
 Get-Mailbox -InactiveMailboxOnly | FT DisplayName,PrimarySMTPAddress,WhenSoftDeleted
```

Du kan også køre følgende kommando for at eksportere listen over inaktive postkasser og andre oplysninger til en CSV-fil. I dette eksempel oprettes CSV-filen i den aktuelle mappe.

```powershell
Get-Mailbox -InactiveMailboxOnly | Select Displayname,PrimarySMTPAddress,DistinguishedName,ExchangeGuid,WhenSoftDeleted | Export-Csv InactiveMailboxes.csv -NoType
```

> [!NOTE]
> Det er muligt, at en inaktiv postkasse har samme SMTP-adresse som en aktiv brugerpostkasse. I dette tilfælde kan værdien af egenskaben **DistinguishedName** eller **ExchangeGuid** bruges til entydigt at identificere en inaktiv postkasse.
  
## <a name="search-and-export-the-contents-of-an-inactive-mailbox"></a>Søg i og eksportér indholdet af en inaktiv postkasse

Du kan få adgang til indholdet af den inaktive postkasse ved hjælp af værktøjet Indholdssøgning i Microsoft Purview-compliance-portal. Når du søger i en inaktiv postkasse, kan du oprette en nøgleordssøgningsforespørgsel for at søge efter bestemte elementer, eller du kan returnere hele indholdet af den inaktive postkasse. Du kan få vist søgeresultaterne eller eksportere søgeresultaterne til en pst-fil (Outlook Data) eller som individuelle mails. Du kan finde trinvise procedurer for søgning i postkasser og eksport af søgeresultater i følgende emner:
  
- [Indholdssøgning](content-search.md)

- [Eksportér søgeresultater](export-search-results.md)

Her er et par ting, du skal være opmærksom på, når du søger i inaktive postkasser.
  
- Hvis en indholdssøgning indeholder en brugerpostkasse, og denne postkasse gøres inaktiv, fortsætter indholdssøgningen med at søge i den inaktive postkasse, når du kører søgningen igen, når den er inaktiv.

- I nogle tilfælde kan en bruger have en aktiv postkasse og en inaktiv postkasse, der har samme SMTP-adresse. I dette tilfælde er det kun den bestemte postkasse, du vælger som en placering til en indholdssøgning, der søges i. Hvis du med andre ord føjer en brugers postkasse til en søgning, kan du ikke antage, at der søges i både brugerens aktive og inaktive postkasser. Det er kun den postkasse, du udtrykkeligt føjer til søgningen, der søges i.

- Det anbefales på det kraftigste, at du undgår at have en aktiv postkasse og en inaktiv postkasse med samme SMTP-adresse. Hvis du har brug for at genbruge den SMTP-adresse, der i øjeblikket er tildelt til en inaktiv postkasse, anbefaler vi, at du gendanner den inaktive postkasse eller gendanner indholdet af en inaktiv postkasse til en aktiv postkasse (eller arkivet for en aktiv postkasse) og derefter sletter den inaktive postkasse.

## <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Rediger varigheden af fastfrysning for en inaktiv postkasse

Når en postkasse er gjort inaktiv, kan du muligvis ændre varigheden af den venteposition, der er anvendt på den inaktive postkasse.

Du kan se trinvise procedurer under [Skift varigheden af ventepositionen for en inaktiv postkasse](change-the-hold-duration-for-an-inactive-mailbox.md).
  
## <a name="recover-an-inactive-mailbox"></a>Gendan en inaktiv postkasse

Hvis en tidligere medarbejder vender tilbage til din organisation, eller hvis en ny medarbejder hyres til at påtage sig den fraværende medarbejders ansvarsområder, kan du gendanne indholdet af den inaktive postkasse. 

Når du gendanner en inaktiv postkasse, konverteres postkassen til en ny postkasse, indholdet og mappestrukturen for den inaktive postkasse bevares, og postkassen er knyttet til en ny brugerkonto. Når den er gendannet, findes den inaktive postkasse ikke længere. 

Du kan finde trinvise procedurer og flere oplysninger om, hvad der sker, når du gendanner en inaktiv postkasse, under [Gendan en inaktiv postkasse](recover-an-inactive-mailbox.md).
  
## <a name="restore-the-contents-of-an-inactive-mailbox-to-another-mailbox"></a>Gendan indholdet af en inaktiv postkasse til en anden postkasse

Hvis en anden medarbejder påtager sig ansvarsområderne for en tidligere medarbejder, eller hvis en anden person skal have adgang til indholdet i den inaktive postkasse, kan du gendanne (eller flette) indholdet af den inaktive postkasse til en eksisterende postkasse. 

Når du gendanner en inaktiv postkasse, kopieres indholdet til en anden postkasse. Den inaktive postkasse bevares og forbliver en inaktiv postkasse. Der kan stadig søges i den inaktive postkasse ved hjælp af eDiscovery, indholdet kan gendannes i en anden postkasse, eller den kan gendannes eller slettes på et senere tidspunkt. 

Du kan finde trinvise procedurer under [Gendan en inaktiv postkasse](restore-an-inactive-mailbox.md).
  
## <a name="delete-an-inactive-mailbox"></a>Slet en inaktiv postkasse

Hvis du ikke længere har brug for at bevare indholdet af en inaktiv postkasse, kan du slette den inaktive postkasse permanent ved at fjerne den venteposition, der er anvendt på den inaktive postkasse. Postkassen bevares i 183 dage, efter at du har fjernet politikken for bevarelse eller opbevaring og kan genoprettes i løbet af den pågældende periode. Efter 183 dage markeres postkassen til permanent sletning, og postkassen kan ikke genoprettes. 

Du kan se trinvise procedurer for fjernelse af en venteposition eller en opbevaringspolitik for at slette en inaktiv postkasse permanent under [Slet en inaktiv postkasse](delete-an-inactive-mailbox.md).
