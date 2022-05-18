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
description: 'Få mere at vide om, hvordan du konverterer en privat postkasse til en delt postkasse, som flere personer kan få adgang til i stedet for kun én person. '
ms.openlocfilehash: 07b36e5c8b2cb7b2e88dfedd80b31353cb8f7e32
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65466212"
---
# <a name="convert-a-user-mailbox-to-a-shared-mailbox"></a>Konvertér en brugerpostkasse til en delt postkasse

Når du konverterer en brugers postkasse til en delt postkasse, bevares al den eksisterende mail og kalender. Først nu er det i en delt postkasse, hvor flere personer kan få adgang til den i stedet for én person. På et senere tidspunkt kan du konvertere en delt postkasse tilbage til en brugerpostkasse (privat).

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist har du og dine medarbejdere adgang til specialister i små virksomheder døgnet rundt, efterhånden som du får din virksomhed til at vokse, lige fra onboarding til hverdagsbrug.

## <a name="before-you-begin"></a>Før du begynder

**Her er nogle vigtige ting, du skal vide**:

- Brugerpostkassen skal have tildelt en licens, før du konverterer den til en delt postkasse. Ellers kan du ikke se muligheden for at konvertere postkassen. Hvis du har fjernet licensen, skal du tilføje den igen, så du kan konvertere postkassen. Når du har konverteret brugerpostkassen til en delt postkasse, kan du fjerne licensen fra brugerens konto.

- Uden en licens er delte postkasser begrænset til 50 GB. Du skal muligvis slette en masse store meddelelser (f.eks. meddelelser med vedhæftede filer) fra den delte postkasse for at formindske den, så du kan fjerne licensen.

  Hvis du vil øge størrelsesgrænsen til 100 GB, skal du tildele en Exchange Online Plan 2-licens til den delte postkasse.

  Hvis du tildeler en Exchange Online Plan 1-licens og en Exchange Online-arkivering tilføjelsesprogramlicens til den delte postkasse, kan du aktivere automatisk udvidelse af arkivering for at få yderligere arkivlagerkapacitet.

- Slet ikke den gamle brugers konto, fordi kontoen er påkrævet for at forankre den delte postkasse. Hvis du allerede har slettet brugerkontoen, skal du se [Konvertér en slettet brugers postkasse](#convert-the-mailbox-of-a-deleted-user).

- Du behøver ikke at nulstille kontoens adgangskode til brugerpostkassen. Men hvis du ikke nulstiller adgangskoden, **vil det oprindelige brugernavn og den oprindelige adgangskode fortsat fungere i den delte postkasse** , når konverteringen er fuldført.

- Indbakkeregler bevares, når brugerpostkassen konverteres til en delt postkasse.

- Hvis du vil sætte en In-Place venteposition eller en procesretlig venteposition på en delt postkasse, skal du tildele en Exchange Online Plan 2-licens *eller* en Exchange Online Plan 1-licens og en Exchange Online-arkivering tilføjelsesprogramlicens til den delte postkasse.

## <a name="use-the-classic-exchange-admin-center-to-convert-a-mailbox"></a>Brug Classic Exchange Administration til at konvertere en postkasse

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Klassisk Exchange Administration</a>.

2. Vælg **Modtageres** \> **postkasser**.

3. Vælg brugerpostkassen. Under **Konvertér til delt postkasse** skal du vælge **Konvertér**.

4. Hvis postkassen er mindre end 50 GB, kan du fjerne [licensen fra brugeren](../manage/remove-licenses-from-users.md) og stoppe med at betale for den. Slet ikke brugerens konto. Den delte postkasse skal bruge den der som et anker. Hvis du konverterer postkassen for en medarbejder, der forlader din organisation, skal du udføre yderligere trin for at sikre, at vedkommende ikke længere kan logge på. Du kan få flere oplysninger under [Fjern en tidligere medarbejder fra Microsoft 365](../add-users/remove-former-employee.md).

Du kan se alt andet, du har brug for at vide om delte postkasser, under [Om delte postkasser](about-shared-mailboxes.md) og [Opret en delt postkasse](create-a-shared-mailbox.md).

## <a name="use-the-new-exchange-admin-center-to-convert-a-mailbox"></a>Brug Nyt Exchange Administration til at konvertere en postkasse

1. Gå til <a href="https://admin.exchange.microsoft.com/#/homepage" target="_blank"> Exchange Administration</a>.

2. Vælg **Modtageres** \> **postkasser**.

3. Vælg brugerpostkassen. Under fanen **Andre** skal du vælge **Konvertér til delt postkasse**.

4. Hvis postkassen er mindre end 50 GB, kan du fjerne [licensen fra brugeren](../manage/remove-licenses-from-users.md) og stoppe med at betale for den. Slet ikke brugerens konto. Den delte postkasse skal bruge den der som et anker. Hvis du konverterer postkassen for en medarbejder, der forlader organisationen, skal du udføre yderligere trin for at sikre, at vedkommende ikke længere kan logge på. Se [Fjern en tidligere medarbejder fra Microsoft 365](../add-users/remove-former-employee.md).

Du kan se alt andet, du har brug for at vide om delte postkasser, under [Om delte postkasser](about-shared-mailboxes.md) og [Opret en delt postkasse](create-a-shared-mailbox.md).

## <a name="convert-the-mailbox-of-a-deleted-user"></a>Konvertér postkassen for en slettet bruger

Når du har slettet en brugerkonto, skal du følge disse trin for at konvertere den gamle postkasse til en sharepostkasse:

1. [Gendan brugerens konto](../add-users/restore-user.md).

2. Sørg for, at der er tildelt en Microsoft 365 licens til den.

3. Nulstil brugerens adgangskode.

4. Vent 20-30 minutter på, at postkassen genoprettes.

5. Når postkassen er oprettet igen, skal du fjerne licensen fra brugerens postkasse. Slet ikke brugerens gamle postkasse. Den delte postkasse skal bruge den der som et anker.

6. Føj medlemmer til den delte postkasse.

## <a name="convert-a-shared-mailbox-back-to-a-users-private-mailbox"></a>Konvertér en delt postkasse tilbage til en brugers (private) postkasse

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>.

2. Vælg **Delte modtagere**\>.

3. Vælg den delte postkasse. Under **Konvertér til almindelig postkasse** skal du vælge **Konvertér**.

4. Gå tilbage til Administration. Under **Brugere** skal du vælge den brugerkonto, der er knyttet til den gamle delte postkasse. Tildel en licens til kontoen, og nulstil derefter adgangskoden.

   Det tager et par minutter, før postkassen er konfigureret, men derefter er den person, der skal bruge kontoen, klar til at gå i gang. Når de logger på, får de vist de mail- og kalenderelementer, der tidligere var i den delte postkasse.

## <a name="convert-a-users-mailbox-in-a-hybrid-environment"></a>Konvertér en brugers postkasse i et hybridmiljø

Du kan finde flere oplysninger om konvertering af en brugerpostkasse til en delt postkasse i et Exchange Hybrid-miljø under:

- [Cmdlet'er til oprettelse eller ændring af en delt fjernpostkasse i et lokalt Exchange miljø](https://support.microsoft.com/office/cmdlets-to-create-or-modify-a-remote-shared-mailbox-in-an-on-premises-exchange-environment-9e83fb59-c001-729c-a4c0-b2964c154b49)
- [Delte postkasser konverteres uventet til brugerpostkasser, når katalogsynkronisering har kørt i en Exchange hybridinstallation](/exchange/troubleshoot/user-and-shared-mailboxes/shared-mailboxes-unexpectedly-converted-to-user-mailboxes)

> [!NOTE]
> Hvis du er medlem af rollegruppen Organisationsadministration eller Modtageradministration, kan du bruge Exchange Management Shell til at ændre en brugerpostkasse til en delt postkasse i det lokale miljø. For eksempel `Set-Mailbox -Identity mailbox1@contoso.com -Type Shared`.

## <a name="related-content"></a>Relateret indhold

[Om delte postkasser](about-shared-mailboxes.md) (artikel)\
[Opret en delt postkasse](create-a-shared-mailbox.md) (artikel)\
[Konfigurer en delt postkasse](configure-a-shared-mailbox.md) (artikel)\
[Fjern en licens fra en delt postkasse](remove-license-from-shared-mailbox.md) (artikel)\
[Løs problemer med delte postkasser](resolve-issues-with-shared-mailboxes.md) (artikel)
