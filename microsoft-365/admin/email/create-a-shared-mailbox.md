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
description: Opret en delt postkasse for at gøre det muligt for flere brugere i din virksomhed at dele ansvaret for at læse og besvare mails, der sendes til én adresse.
ms.openlocfilehash: 444be08a2083bf184d61ee206dfaa8ab53657b0b
ms.sourcegitcommit: 5fe7f2954a89406245416fc1a218cf4bf19abb85
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65864556"
---
# <a name="create-a-shared-mailbox"></a>Opret en delt postkasse 

> [!NOTE]
> Hvis din organisation bruger et hybridt Exchange miljø, skal du bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> i det lokale miljø til at oprette og administrere delte postkasser. Se [Opret delte postkasser i Exchange Administration](/Exchange/collaboration/shared-mailboxes/create-shared-mailboxes?preserve-view=true.&view=exchserver-2019)
>
> Hvis du ikke er sikker på, om du skal oprette en delt postkasse eller en Microsoft 365 gruppe til Outlook, skal du se [Sammenlign grupper](../create-groups/compare-groups.md) for at få vejledning. Bemærk, at det i øjeblikket ikke er muligt at overføre en delt postkasse til en Microsoft 365 gruppe. Hvis det er noget, de ønsker, så giv os besked ved [at stemme her](https://go.microsoft.com/fwlink/?linkid=871518).

Det er nemt at oprette delte postkasser, så en gruppe personer kan overvåge og sende mails fra en almindelig mailadresse, f.eks. info@contoso.com. Når en person i gruppen svarer på en meddelelse, der er sendt til den delte postkasse, er mailen tilsyneladende fra den delte postkasse og ikke fra den enkelte bruger.

Delte postkasser omfatter en delt kalender. Mange små virksomheder kan lide at bruge den delte kalender som et sted, hvor alle kan deltage i deres aftaler. Hvis du f.eks. har tre personer, der besøger kunden, kan alle bruge den delte kalender til at angive aftalerne. Dette er en nem måde at holde alle informeret om, hvor folk er.

Før du opretter en delt postkasse, skal du læse [Om delte postkasser](about-shared-mailboxes.md) for at få flere oplysninger.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist har du og dine medarbejdere adgang til specialister i små virksomheder døgnet rundt, efterhånden som du får din virksomhed til at vokse, lige fra onboarding til hverdagsbrug.

## <a name="create-a-shared-mailbox-and-add-members"></a>Opret en delt postkasse, og tilføj medlemmer
  
1. Log på med en global administratorkonto eller Exchange administratorkonto. Hvis du får vist meddelelsen "**Du har ikke tilladelse til at få adgang til denne side eller udføre denne handling**", er du ikke administrator. 

::: moniker range="o365-worldwide"

2. I Administration skal du gå til siden **Teams & grupper** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">delte postkasser</a>.

::: moniker-end

::: moniker range="o365-21vianet"

2. I [Administration](https://go.microsoft.com/fwlink/p/?linkid=850627) skal du gå til siden **Teams & grupper** \> **delte postkasser**.

::: moniker-end
    
3. På siden **Delte postkasser** skal du vælge **+ Tilføj en delt postkasse**. Angiv et navn til den delte postkasse. Dette vælger mailadressen, men du kan redigere den, hvis det er nødvendigt.
    
    ![Navngiv din delte postkasse.](../../media/e3035132-8986-4ec7-b7c0-f2752080d2c0.png)
  
4. Vælg **Gem ændringer**. Det kan tage et par minutter, før du kan tilføje medlemmer.

5. Under **Næste trin** skal du vælge **Føj medlemmer til denne postkasse**. Medlemmer er de personer, der kan få vist den indgående mail til denne delte postkasse og de udgående svar.

   ![Vælg Tilføj medlemmer.](../../media/a2a72e3d-6170-40fe-a94f-0af8fbef8ab2.png)

6. Vælg knappen **+Tilføj medlemmer** . Markér afkrydsningsfeltet ud for de personer, du vil bruge denne delte postkasse, og vælg derefter **Gem**.

   ![Tildel medlemmer til den delte postkasse.](../../media/e6c58953-f6d7-4f0b-97ba-308516bf2a94.png)

7. Vælg **Luk**.

Du har en delt postkasse, og den indeholder en delt kalender. Gå til næste trin: [Bloker logon for den delte postkassekonto](#block-sign-in-for-the-shared-mailbox-account).

## <a name="which-permissions-should-you-use"></a>Hvilke tilladelser skal du bruge?

Du kan bruge følgende tilladelser med en delt postkasse:

- **Fuld adgang**: Tilladelsen Fuld adgang giver en bruger mulighed for at åbne den delte postkasse og fungere som ejer af den pågældende postkasse. Når en bruger har fået adgang til den delte postkasse, kan han eller hun oprette kalenderelementer, læse, få vist, slette og ændre mails og oprette opgaver og kalenderkontakter. En bruger med tilladelsen Fuld adgang kan dog ikke sende mail fra den delte postkasse, medmindre vedkommende også har tilladelsen Send som eller Send på vegne af.

- **Send som**: Tilladelsen Send som gør det muligt for en bruger at repræsentere den delte postkasse, når der sendes mail. Hvis Katerina f.eks. logger på den delte postkasse Marketingafdeling og sender en mail, vil det se ud som marketingafdelingen har sendt mailen.

- **Send på vegne**: Tilladelsen Send på vegne giver en bruger mulighed for at sende mail på vegne af den delte postkasse. Hvis John f.eks. logger på den delte postkasse Reception Building 32 og sender en mail, ser det ud til, at mailen blev sendt af "John på vegne af Receptionsbygning 32". Du kan ikke bruge EAC til at give Send på vegne-tilladelser. Du skal bruge **Set-Mailbox-cmdlet'en** med parameteren _GrantSendonBehalf_ .

> [!NOTE]
> Tilladelserne **Send som** og **Send på vegne** fungerer ikke i skrivebordsklienten Outlook, hvor parameteren *HiddenFromAddressListsEnabled* for postkassen er angivet til **Sand**, da de kræver, at postkassen er synlig i Outlook via den globale adresseliste.

### <a name="use-the-eac-to-edit-shared-mailbox-delegation"></a>Brug EAC til at redigere delegering af delt postkasse

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> skal du gå til **Modtageres** \> **postkasser**. Vælg den delte postkasse, og vælg derefter **Rediger** ![ikonet Rediger.](../../media/ITPro-EAC-EditIcon.png)

2. Under **Postkassetilladelser** skal du vælge **Administrer delegering af postkasse**.

3. Hvis du vil tildele eller fjerne tilladelsen Fuld adgang og Send som, skal du vælge **Tilføj** ![ikonet Tilføj.](../../media/ITPro-EAC-AddIcon.png) eller Fjern ikonet](../../media/ITPro-EAC-RemoveIcon.gif) **Fjern**![, og vælg derefter de brugere, du vil give tilladelser til.

   > [!NOTE]
   > Tilladelsen Fuld adgang giver en bruger mulighed for at åbne postkassen samt oprette og redigere elementer i den. Tilladelsen Send som gør det muligt for andre end ejeren af postkassen at sende mail fra denne delte postkasse. Begge tilladelser er påkrævet for at kunne udføre en delt postkassehandling.

4. Vælg **Gem** for at gemme dine ændringer.


## <a name="block-sign-in-for-the-shared-mailbox-account"></a>Bloker logon for den delte postkassekonto

Alle delte postkasser har en tilsvarende brugerkonto. Bemærk, hvordan du ikke blev bedt om at angive en adgangskode, da du oprettede den delte postkasse? Kontoen har en adgangskode, men den er oprettet af systemet (ukendt). Du skal ikke bruge kontoen til at logge på den delte postkasse.

Men hvad nu, hvis en administrator blot nulstiller adgangskoden til brugerkontoen for den delte postkasse? Eller hvad nu, hvis en hacker får adgang til legitimationsoplysningerne for den delte postkassekonto? Dette gør det muligt for brugerkontoen at logge på den delte postkasse og sende mail. For at forhindre dette skal du blokere logon for den konto, der er knyttet til den delte postkasse.

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a> .
::: moniker-end

2. Find kontoen for den delte postkasse på listen over brugerkonti (skift f.eks. filteret til **Brugere uden licens**).

3. Vælg brugeren for at åbne ruden med egenskaber, og vælg derefter ikonet ![**Bloker denne bruger** Skærmbillede af ikonet Bloker denne bruger.](../../media/block-user-icon.png)

   > [!NOTE]
   > Hvis kontoen allerede er blokeret, vises **logon blokeret** øverst, og ikonet læser **Fjern blokering af denne bruger**.

4. I ruden **Bloker denne bruger?** skal du vælge **Bloker brugeren fra at logge på** og derefter vælge **Gem ændringer**.

Du kan finde oplysninger om, hvordan du blokerer logon for konti ved hjælp af Azure AD PowerShell (herunder mange konti på samme tid), under [Bloker brugerkonti med Office 365 PowerShell](../../enterprise/block-user-accounts-with-microsoft-365-powershell.md).

## <a name="add-the-shared-mailbox-to-outlook"></a>Føj den delte postkasse til Outlook

Hvis automapping er aktiveret i din virksomhed (som standard er det de fleste), vises den delte postkasse automatisk i brugerens Outlook app, når brugeren lukker og genstarter Outlook. 

Automatiskmapping er angivet i brugerens postkasse og ikke i den delte postkasse. Det betyder, at hvis du forsøger at bruge en sikkerhedsgruppe til at administrere, hvem der har adgang til den delte postkasse, fungerer automapping ikke. Så hvis du vil automapping, skal du eksplicit tildele tilladelser. Automapping er som standard slået til. Hvis du vil vide mere om, hvordan du slår den fra, skal du se [Fjern automatisk konfiguration for en delt postkasse](/office365/troubleshoot/administration/remove-automapping-for-shared-mailbox).

Hvis du vil vide mere om delte postkasser i Outlook, skal du se:

- <a href="https://support.microsoft.com/office/d94a8e9e-21f1-4240-808b-de9c9c088afd" target="_blank">Åbn og brug en delt postkasse i Outlook</a>

- <a href="https://support.microsoft.com/office/98b5a90d-4e38-415d-a030-f09a4cd28207" target="_blank">Føj en delt postkasse til Outlook på internettet</a>

- <a href="https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f" target="_blank">Føj en delt postkasse til Outlook mobil</a>

- <a href="https://support.microsoft.com/office/6ecc39c5-5577-4a1d-b18c-bbdc92972cb2" target="_blank">Åbn en delt mappe eller postkasse i Outlook til Mac</a>

- <a href="https://support.microsoft.com/office/b0963400-2a51-4c64-afc7-b816d737d164" target="_blank">Føj regler til en delt postkasse</a>

## <a name="use-a-shared-mailbox-on-a-mobile-device-phone-or-tablet"></a>Brug en delt postkasse på en mobilenhed (telefon eller tablet)

Du kan få adgang til en delt postkasse på en mobilenhed på to måder:
- Tilføj den delte postkasse i <a href="https://apps.apple.com/us/app/microsoft-outlook/id951937596" target="_blank">Outlook til iOS-appen</a> eller <a href="https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en_US" target="_blank">Outlook til Android-mobilappen</a>. 
    
    Du kan finde instruktioner under <a href="https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f" target="_blank">Føj en delt postkasse til Outlook mobil</a>.

- Åbn browseren, log på, og gå derefter til Outlook på internettet. Fra Outlook på internettet kan du få adgang til den delte postkasse.

    Du kan finde instruktioner under <a href="https://support.microsoft.com/office/98b5a90d-4e38-415d-a030-f09a4cd28207" target="_blank">Føj en delt postkasse til Outlook på internettet</a>.
    
> [!NOTE]
> Delt postkasse kan kun føjes til Outlook til iOS-appen eller Outlook til Android-mobilappen

## <a name="use-the-shared-calendar"></a>Brug den delte kalender

Da du oprettede den delte postkasse, oprettede du automatisk en delt kalender. Vi kan godt lide kalenderen for den delte postkasse i stedet for en SharePoint kalender til at holde styr på aftaler, og hvor personer er. En delt kalender er integreret med Outlook og er meget nemmere at bruge end en SharePoint kalender.

1. I appen Outlook skal du gå til kalendervisning og vælge den delte postkasse.

2. Når du angiver aftaler, kan alle, der er medlem af den delte postkasse, se dem.

3. Alle medlemmer af den delte postkasse kan oprette, få vist og administrere aftaler i kalenderen på samme måde som deres personlige aftaler. Alle, der er medlem af den delte postkasse, kan se deres ændringer i den delte kalender.

## <a name="related-content"></a>Relateret indhold

[Om delte postkasser](about-shared-mailboxes.md) (artikel)\
[Konfigurer en delt postkasse](configure-a-shared-mailbox.md) (artikel)\
[Konvertér en brugerpostkasse til en delt postkasse](convert-user-mailbox-to-shared-mailbox.md) (artikel)\
[Fjern en licens fra en delt postkasse](remove-license-from-shared-mailbox.md) (artikel)\
[Løs problemer med delte postkasser](resolve-issues-with-shared-mailboxes.md) (artikel)
