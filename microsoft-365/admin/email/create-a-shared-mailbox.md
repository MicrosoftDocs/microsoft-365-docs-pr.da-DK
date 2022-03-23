---
title: Opret en delt postkasse
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkEXCHANGE
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 871a246d-3acd-4bba-948e-5de8be0544c9
description: Opret en delt postkasse for at give flere brugere i din virksomhed mulighed for at dele ansvaret for at læse og besvare mails, der sendes til én adresse.
ms.openlocfilehash: f8a7f725e029021626bf408a3797ac6bfbb16215
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63590777"
---
# <a name="create-a-shared-mailbox"></a>Opret en delt postkasse 

> [!NOTE]
> Hvis din organisation bruger et Exchange-miljø, skal du bruge den lokale <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> til at oprette og administrere delte postkasser. Se [Opret delte postkasser Exchange Administration](/Exchange/collaboration/shared-mailboxes/create-shared-mailboxes?preserve-view=true.&view=exchserver-2019)
>
> Hvis du ikke er sikker på, om du skal oprette en delt postkasse eller en Microsoft 365 gruppe til Outlook, kan du se Sammenlign [grupper for at](../create-groups/compare-groups.md) få vejledning. Bemærk, at det i øjeblikket ikke er muligt at overføre en delt postkasse til en Microsoft 365 gruppe. Hvis dette er noget, du gerne vil have, kan du give os besked [ved at stemme her](https://go.microsoft.com/fwlink/?linkid=871518).

Det er nemt at oprette delte postkasser, så en gruppe af personer kan overvåge og sende mails fra en fælles mailadresse, f.eks. info@contoso.com. Når en person i gruppen besvarer en meddelelse, der er sendt til den delte postkasse, ser mailen ud til at være fra den delte postkasse og ikke fra den enkelte bruger.

Delte postkasser omfatter en delt kalender. Mange mindre virksomheder bruger gerne den delte kalender som et sted, hvor alle kan lave deres aftaler. Hvis du f.eks. har 3 personer, der tager på kundebesøg, kan alle bruge den delte kalender til at angive aftaler. Dette er en nem metode til at holde alle informeret, hvor folk er.

Før du opretter en delt postkasse, skal du sørge for at læse [Om delte postkasser for at](about-shared-mailboxes.md) få flere oplysninger.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialspecialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist får du og dine medarbejdere døgnet rundt adgang til små virksomhedsspecialister, efterhånden som du vokser din virksomhed, fra onboarding til daglig brug.

## <a name="create-a-shared-mailbox-and-add-members"></a>Opret en delt postkasse, og tilføj medlemmer
  
1. Log på med en global administratorkonto eller Exchange administratorkonto. Hvis du får vist meddelelsen "**Du har** ikke tilladelse til at få adgang til denne side eller udføre denne handling", er du ikke administrator. 

::: moniker range="o365-worldwide"

2. I Administration skal du gå til siden **Teams & delte** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">postkasser i</a> Grupper.

::: moniker-end

::: moniker range="o365-21vianet"

2. I [Administration skal](https://go.microsoft.com/fwlink/p/?linkid=850627) du gå til siden **Teams & Delte** \> **postkasser** i Grupper.

::: moniker-end
    
3. På siden **Delte postkasser** skal du vælge **+ Tilføj en delt postkasse**. Angiv et navn til den delte postkasse. Mailadressen vælges, men du kan redigere den, hvis det er nødvendigt.
    
    ![Navngive din delte postkasse.](../../media/e3035132-8986-4ec7-b7c0-f2752080d2c0.png)
  
4. Vælg **Gem ændringer**. Det kan tage et par minutter, før du kan tilføje medlemmer.

5. Under **Næste trin** skal du **vælge Føj medlemmer til denne postkasse**. Medlemmer er de personer, der vil kunne få vist de indgående mails til denne delte postkasse samt udgående svar.

   ![Vælg Tilføj medlemmer.](../../media/a2a72e3d-6170-40fe-a94f-0af8fbef8ab2.png)

6. Vælg **knappen +Tilføj** medlemmer. Markér ud for de personer, du vil bruge denne delte postkasse til, og vælg derefter **Gem**.

   ![Tildel medlemmer til den delte postkasse.](../../media/e6c58953-f6d7-4f0b-97ba-308516bf2a94.png)

7. Vælg **Luk**.

Du har en delt postkasse, og den indeholder en delt kalender. Gå til næste trin: [Bloker logon for den delte postkassekonto](#block-sign-in-for-the-shared-mailbox-account).

## <a name="which-permissions-should-you-use"></a>Hvilke tilladelser skal du bruge?

Du kan bruge følgende tilladelser med en delt postkasse:

- **Fuld adgang**: Tilladelsen Fuld adgang giver en bruger mulighed for at åbne den delte postkasse og fungere som ejeren af den pågældende postkasse. Når en bruger har tilgå den delte postkasse, kan han eller hun oprette kalenderelementer, læse, få vist, slette og ændre mails og oprette opgaver og kalenderkontakter. Men en bruger med tilladelsen Fuld adgang kan ikke sende mails fra den delte postkasse, medmindre de også har tilladelsen Send som eller Send på vegne af.

- **Send som**: Med tilladelsen Send som kan en bruger udgive sig for at være den delte postkasse, når der sendes mail. Hvis for eksempel Logges på den delte postkasse Marketingafdeling og sender en mail, vil det se ud som om Marketingafdelingen har sendt mailen.

- **Send på vegne** af: Tilladelsen Send på vegne af giver en bruger mulighed for at sende mail på vegne af den delte postkasse. Hvis John f.eks. logger på den delte postkasse Modtagelsesbygning 32 og sender en mail, vil det se ud som om, mailen blev sendt af "John på vegne af Receptionsbygning 32". Du kan ikke bruge EAC til at tildele Send på vegne af-tilladelser. Du skal bruge **Set-Mailbox-cmdlet'en** med _GrantSendonBehalf-parameteren_ .

### <a name="use-the-eac-to-edit-shared-mailbox-delegation"></a>Brug EAC til at redigere delegering af delte postkasser

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration skal</a> du gå **til Delte** \> **modtagere**. Vælg den delte postkasse, og vælg derefter **Rediger** ![ikonet Rediger](../../media/ITPro-EAC-EditIcon.png).

2. Vælg **Postkassedelegering**.

3. Hvis du vil tildele eller fjerne tilladelserne Fuld adgang og Send som, skal du **vælge Tilføj** ![ikon.](../../media/ITPro-EAC-AddIcon.png) eller **ikonet** ![Fjern Fjern](../../media/ITPro-EAC-RemoveIcon.gif) , og vælg derefter de brugere, du vil give tilladelser til.

   > [!NOTE]
   > Tilladelsen Fuld adgang giver en bruger mulighed for at åbne postkassen samt oprette og redigere elementer i den. Tilladelsen Send som giver alle andre end ejeren af postkassen mulighed for at sende mails fra denne delte postkasse. Begge tilladelser kræves for, at den delte postkasse kan bruges korrekt.

4. Vælg **Gem** for at gemme ændringerne.


## <a name="block-sign-in-for-the-shared-mailbox-account"></a>Bloker logon for den delte postkassekonto

Hver delt postkasse har en tilsvarende brugerkonto. Bemærk, hvordan du ikke blev bedt om at angive en adgangskode, da du oprettede den delte postkasse? Kontoen har en adgangskode, men den er systemgenereret (ukendt). Det er ikke meningen, at du skal bruge kontoen til at logge på den delte postkasse.

Men hvad nu, hvis en administrator blot nulstiller adgangskoden til brugerkontoen for den delte postkasse? Eller hvad nu, hvis en hacker får adgang til legitimationsoplysningerne til den delte postkassekonto? Dette gør det muligt for brugerkontoen at logge på den delte postkasse og sende mails. For at undgå dette skal du blokere logon for den konto, der er knyttet til den delte postkasse.

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">for</a> brugere.
::: moniker-end

2. På listen over brugerkonti skal du finde kontoen for den delte postkasse (f.eks. skal du ændre filteret **til Brugere uden licens**).

3. Vælg brugeren for at åbne ruden med deres egenskaber, og vælg derefter skærmbilledet **Bloker** ![denne bruger af ikonet Bloker denne bruger](../../media/block-user-icon.png).

   > [!NOTE]
   > Hvis kontoen allerede er blokeret, **vises Log på blokeret** øverst, og ikonet læser Fjern blokering **fra denne bruger**.

4. I **ruden Bloker denne bruger?** skal **du vælge Bloker brugeren fra at logge** på og derefter vælge **Gem ændringer**.

Du kan finde en vejledning til at blokere logon for konti ved hjælp af Azure AD PowerShell (herunder mange konti på samme tid) under Bloker brugerkonti med [Office 365 PowerShell](../../enterprise/block-user-accounts-with-microsoft-365-powershell.md).

## <a name="add-the-shared-mailbox-to-outlook"></a>Føj den delte postkasse til Outlook

Hvis du har aktiveret automapping i din virksomhed (det har de fleste som standard), vises den delte postkasse automatisk i din brugers Outlook-app, når de lukker og genstarter Outlook. 

Automapping er angivet på brugerens postkasse, ikke den delte postkasse. Det betyder, at hvis du forsøger at bruge en sikkerhedsgruppe til at administrere, hvem der har adgang til den delte postkasse, fungerer automapping ikke. Så hvis du vil bruge automapping, skal du tildele tilladelser eksplicit. Automapping er som standard markeret. Du kan få mere at vide om, hvordan du slår [det fra, under Fjern automapping for en delt postkasse](/office365/troubleshoot/administration/remove-automapping-for-shared-mailbox).

Du kan få mere at vide om delte Outlook i:

- <a href="https://support.microsoft.com/office/d94a8e9e-21f1-4240-808b-de9c9c088afd" target="_blank">Åbn og brug en delt postkasse i Outlook</a>

- <a href="https://support.microsoft.com/office/98b5a90d-4e38-415d-a030-f09a4cd28207" target="_blank">Føj en delt postkasse til Outlook på internettet</a>

- <a href="https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f" target="_blank">Føj en delt postkasse til Outlook mobil</a>

- <a href="https://support.microsoft.com/office/6ecc39c5-5577-4a1d-b18c-bbdc92972cb2" target="_blank">Åbn en delt mappe eller postkasse i Outlook til Mac</a>

- <a href="https://support.microsoft.com/office/b0963400-2a51-4c64-afc7-b816d737d164" target="_blank">Føje regler til en delt postkasse</a>

## <a name="use-a-shared-mailbox-on-a-mobile-device-phone-or-tablet"></a>Bruge en delt postkasse på en mobilenhed (telefon eller tablet)

Du kan få adgang til en delt postkasse på en mobilenhed på to måder:
- Tilføj den delte postkasse i <a href="https://apps.apple.com/us/app/microsoft-outlook/id951937596" target="_blank">Outlook til iOS-appen</a> eller <a href="https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en_US" target="_blank">Outlook til Android-mobilappen</a>. 
    
    Du kan finde en vejledning <a href="https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f" target="_blank">under Føj en delt postkasse til Outlook mobil</a>.

- Åbn browseren, log på, og gå derefter til Outlook på internettet. Fra Outlook på internettet vil du kunne få adgang til den delte postkasse.

    Du kan finde en vejledning <a href="https://support.microsoft.com/office/98b5a90d-4e38-415d-a030-f09a4cd28207" target="_blank">i Føje en delt postkasse til Outlook på internettet</a>.
    
> [!NOTE]
> Delt postkasse kan kun føjes til Outlook til iOS-appen eller Outlook til Android-mobilappen

## <a name="use-the-shared-calendar"></a>Brug den delte kalender

Da du oprettede den delte postkasse, oprettede du automatisk en delt kalender. Vi synes godt om kalenderen i den delte postkasse i stedet for en SharePoint kalender til at holde styr på aftaler og personer. En delt kalender er integreret med Outlook og den er meget nemmere at bruge end en SharePoint kalender.

1. I Outlook skal du gå til kalendervisning og vælge den delte postkasse.

2. Når du angiver aftaler, vil alle, der er medlem af den delte postkasse, kunne se dem.

3. Alle medlemmer af den delte postkasse kan oprette, få vist og administrere aftaler i kalenderen på samme måde som med deres personlige aftaler. Alle medlemmer af en delt postkasse kan se deres ændringer af den delte kalender.

## <a name="related-content"></a>Relateret indhold

[Om delte postkasser](about-shared-mailboxes.md) (artikel)\
[Konfigurer en delt postkasse](configure-a-shared-mailbox.md) (artikel)\
[Konvertér en brugerpostkasse til en delt postkasse](convert-user-mailbox-to-shared-mailbox.md) (artikel)\
[Fjern en licens fra en delt postkasse](remove-license-from-shared-mailbox.md) (artikel)\
[Løse problemer med delte postkasser](resolve-issues-with-shared-mailboxes.md) (artikel)
