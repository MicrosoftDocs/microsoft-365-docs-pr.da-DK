---
title: Konvertér en brugerpostkasse til en delt postkasse
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkEXCHANGE
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 2e122487-e1f5-4f26-ba41-5689249d93ba
description: 'Lær at konvertere en privat postkasse til en delt postkasse, der kan åbnes af flere personer i stedet for kun én person. '
ms.openlocfilehash: a1b82d744cc43f8119e9819537467133f2bae17c
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63590778"
---
# <a name="convert-a-user-mailbox-to-a-shared-mailbox"></a>Konvertér en brugerpostkasse til en delt postkasse

Når du konverterer en brugers postkasse til en delt postkasse, bevares hele den eksisterende mail og kalender. Først nu findes den i en delt postkasse, hvor flere personer kan få adgang til den i stedet for én person. På et senere tidspunkt kan du konvertere en delt postkasse tilbage til en brugerpostkasse (privat).

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialspecialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist får du og dine medarbejdere døgnet rundt adgang til små virksomhedsspecialister, efterhånden som du vokser din virksomhed, fra onboarding til daglig brug.

## <a name="before-you-begin"></a>Før du begynder

**Her er nogle meget vigtige ting, du skal vide:**

- Den brugerpostkasse, du konverterer, skal have en licens tildelt, før du konverterer den til en delt postkasse. Ellers får du ikke vist muligheden for at konvertere postkassen. Hvis du har fjernet licensen, skal du tilføje den igen, så du kan konvertere postkassen. Når du har konverteret postkassen til en delt postkasse, kan du fjerne licensen fra brugerens konto.

- Delte postkasser kan have op til 50 GB data uden at være tildelt en licens. Hvis du vil opbevare flere data end det, skal du have tildelt en licens. Det kan være nødvendigt at slette en masse store mails (f.eks. mails med vedhæftede filer) fra den delte postkasse for at formindske den, så du kan fjerne licensen.

- Slet ikke den gamle brugers konto. Den skal bruges til at forankre den delte postkasse. Hvis du allerede har slettet brugerkontoen, skal du se [Konvertér en slettet brugers postkasse](#convert-the-mailbox-of-a-deleted-user).

- Reglerne er intakte, når postkassen er konverteret til en delt postkasse.

## <a name="use-the-classic-exchange-admin-center-to-convert-a-mailbox"></a>Brug den klassiske Exchange Administration til at konvertere en postkasse
 
1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">den klassiske Exchange Administration</a>.

2. Vælg **Modtagerpostkasser**\>.

3. Vælg brugerpostkassen. Under **Konvertér til delt postkasse skal** du vælge **Konvertér**.

4. Hvis postkassen er mindre end 50 GB, kan du fjerne [licensen fra](../manage/remove-licenses-from-users.md) brugeren og holde op med at betale for den. Slet ikke brugerens konto. Den delte postkasse skal bruge den som en forankring. Hvis du konverterer postkassen for en medarbejder, der forlader organisationen, skal du foretage dig yderligere for at sikre, at de ikke længere kan logge på. Få mere at vide under [Fjern en tidligere medarbejder fra Microsoft 365](../add-users/remove-former-employee.md).
    
> [!NOTE]
> Det er ikke påkrævet at nulstille brugerens adgangskode under konvertering af postkasse. Men hvis adgangskoden ikke nulstilles, fungerer **det oprindelige brugernavn og den oprindelige adgangskode fortsat, når** postkassekonverteringen er fuldført.

Du kan finde alle andre oplysninger om delte postkasser i [Om delte postkasser](about-shared-mailboxes.md) og [Opret en delt postkasse](create-a-shared-mailbox.md).

> [!NOTE]
> Delte postkasser kræver ikke en separat licens. Men hvis du vil aktivere In-Place-arkivet eller sætte en In-Place-venteposition eller en retslig venteposition på en delt postkasse, skal du tildele en Exchange Online Plan 1 med Exchange Online-arkivering- eller Exchange Online Plan 2-licens til postkassen.

## <a name="use-the-new-exchange-admin-center-to-convert-a-mailbox"></a>Brug den nye Exchange Administration til at konvertere en postkasse

1. Gå til <a href="https://admin.exchange.microsoft.com/#/homepage" target="_blank"> Exchange Administration</a>.

2. Vælg **Modtagerpostkasser**\>.

3. Vælg brugerpostkassen. På fanen **Postkasse** under Flere handlinger **skal du** vælge **Konvertér til delt postkasse**.

4. Hvis postkassen er mindre end 50 GB, kan du fjerne [licensen fra](../manage/remove-licenses-from-users.md) brugeren og holde op med at betale for den. Slet ikke brugerens konto. Den delte postkasse skal bruge den som en forankring. Hvis du konverterer postkassen for en medarbejder, der forlader organisationen, skal du foretage dig yderligere for at sikre, at de ikke kan logge på længere. Se Fjern [en tidligere medarbejder fra Microsoft 365](../add-users/remove-former-employee.md).
    
> [!NOTE]
> Det er ikke påkrævet at nulstille brugerens adgangskode under konvertering af postkasse. Men hvis adgangskoden ikke nulstilles, fungerer **det oprindelige brugernavn og den oprindelige adgangskode fortsat, når** postkassekonverteringen er fuldført.

Du kan finde alle andre oplysninger om delte postkasser i [Om delte postkasser](about-shared-mailboxes.md) og [Opret en delt postkasse](create-a-shared-mailbox.md).

> [!NOTE]
> Delte postkasser kræver ikke en separat licens. Men hvis du vil aktivere In-Place-arkivet eller sætte en In-Place-venteposition eller en retslig venteposition på en delt postkasse, skal du tildele en Exchange Online Plan 1 med Exchange Online-arkivering- eller Exchange Online Plan 2-licens til postkassen.

## <a name="convert-the-mailbox-of-a-deleted-user"></a>Konvertér en slettet brugers postkasse

Når du sletter en brugerkonto, skal du følge disse trin for at konvertere brugerens gamle postkasse til en delt postkasse:

1. [Gendan brugerens konto](../add-users/restore-user.md).

2. Sørg for, Microsoft 365 tildelt en licens til den.

3. Nulstil brugerens adgangskode.
    
4. Vent 20-30 minutter på, at postkassen oprettes igen.
      
6. Når postkassen er oprettet igen, skal du fjerne licensen fra brugerens postkasse. Slet ikke brugerens gamle postkasse. Den delte postkasse skal bruge den som en forankring.
    
7. Føj medlemmer til den delte postkasse.

## <a name="convert-a-shared-mailbox-back-to-a-users-private-mailbox"></a>Konvertér en delt postkasse tilbage til en brugers (private) postkasse

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>.
   
2. Vælg **Modtagere** \> **delt**.

3. Vælg den delte postkasse. Under **Konvertér til almindelig postkasse** skal du vælge **Konvertér**.

4. Gå tilbage til Administration. Under **Brugere skal** du vælge den brugerkonto, der er knyttet til den gamle delte postkasse. Tildel en licens til kontoen, og nulstil derefter adgangskoden.

   Det tager et par minutter, før postkassen er konfigureret, men derefter er den person, der skal bruge den pågældende konto, klar til at gå i gang. Når de logger på, får de vist de mail- og kalenderelementer, der plejede at være i den delte postkasse.

## <a name="convert-a-users-mailbox-in-a-hybrid-environment"></a>Konvertér en brugers postkasse i et hybridmiljø

Du kan finde flere oplysninger om konvertering af en brugerpostkasse til en delt postkasse Exchange et hybridmiljø i:

 - [Cmdlet'er til at oprette eller redigere en ekstern delt postkasse i et lokalt Exchange miljø](https://support.microsoft.com/office/cmdlets-to-create-or-modify-a-remote-shared-mailbox-in-an-on-premises-exchange-environment-9e83fb59-c001-729c-a4c0-b2964c154b49)
 - [Delte postkasser konverteres uventet til brugerpostkasser, når katalogsynkronisering kører i en Exchange hybridinstallation](/exchange/troubleshoot/user-and-shared-mailboxes/shared-mailboxes-unexpectedly-converted-to-user-mailboxes)
 

> [!NOTE]
> Hvis du er medlem af rollegruppen Organisationsadministration eller Modtageradministration, kan du bruge Exchange Management Shell til at ændre en brugerpostkasse til en delt postkasse i det lokale miljø. F.eks. `Set-Mailbox -Identity mailbox1@contoso.com -Type Shared`.

## <a name="related-content"></a>Relateret indhold

[Om delte postkasser](about-shared-mailboxes.md) (artikel)\
[Opret en delt postkasse](create-a-shared-mailbox.md) (artikel)\
[Konfigurer en delt postkasse](configure-a-shared-mailbox.md) (artikel)\
[Fjern en licens fra en delt postkasse](remove-license-from-shared-mailbox.md) (artikel)\
[Løse problemer med delte postkasser](resolve-issues-with-shared-mailboxes.md) (artikel)
