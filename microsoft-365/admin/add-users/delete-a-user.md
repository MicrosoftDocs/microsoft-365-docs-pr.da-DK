---
title: Slet en bruger fra din organisation
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- SPO_Content
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
ms.assetid: d5155593-3bac-4d8d-9d8b-f4513a81479e
description: Få mere at vide om, hvordan du sletter en brugerkonto, og hvad du skal gøre med brugerens mail og OneDrive indhold, og om du vil beholde produktlicensen.
ms.openlocfilehash: 894bcef6cc273c067b3d9b622f244d361ed24d96
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090701"
---
# <a name="delete-a-user-from-your-organization"></a>Slet en bruger fra din organisation
  
**Leder du efter, hvordan du sletter din *egen* Microsoft 365 brugerkonto, som du bruger på arbejdet eller i skolen? Kontakt den tekniske support på dit arbejde eller på dit universitet for at udføre disse trin for dig.**

## <a name="before-you-begin"></a>Før du begynder

- Det er kun personer, der har [Microsoft 365 globale administrator-](about-admin-roles.md) eller brugeradministrationstilladelser til virksomheden eller skolen, der kan slette brugerkonti.
- Du har 30 dage til at [gendanne](restore-user.md) kontoen, før brugerens data slettes permanent.
- Hvis du vil beholde brugerens OneDrive data, skal du flytte dem til en anden placering. Du kan endda flytte dataene op til 30 dage efter sletning af kontoen. Se [Få adgang til og sikkerhedskopiér en tidligere brugers data](get-access-to-and-back-up-a-former-user-s-data.md). Du behøver ikke at flytte deres SharePoint filer. Du har stadig adgang til dem.
- Hvis du vil beholde brugerens mail, **før** du sletter kontoen, skal du flytte mailen til en anden placering. Hvis du allerede har slettet kontoen: Hvis det har været mindre end 30 dage, kan du gendanne den og derefter flytte maildataene og derefter slette kontoen. Se [Få adgang til og sikkerhedskopiér en tidligere brugers data](get-access-to-and-back-up-a-former-user-s-data.md).
- Hvis du har et Enterprise-abonnement som Office 365 Enterprise E3, kan du bevare postkassedataene for en slettet brugerkonto ved at omdanne den til en *inaktiv postkasse*. Du kan få mere at vide under [Administrer inaktive postkasser i Exchange Online](../../compliance/inactive-mailboxes-in-office-365.md).

## <a name="global-admin-delete-a-user-stop-paying-for-their-license-and-choose-what-to-do-with-their-email-and-onedrive-content"></a>Global administrator: Slet en bruger, stop med at betale for sin licens, og vælg, hvad der skal gøres med vedkommendes mail og OneDrive indhold

Hvis du er global administrator, kan du, når du sletter en bruger, også give en anden bruger adgang til deres mail og vælge, hvad der skal gøres med vedkommendes OneDrive indhold.

### <a name="things-to-consider"></a>Ting, du skal overveje

Før du begynder, skal du tænke over, hvad du vil gøre med brugerens mail og OneDrive indhold, og om du vil beholde licensen eller holde op med at betale for det.
  
|Element | Beskrivelse |
|:-----|:-----|
|Produktlicenser  <br/> |Du kan fjerne licensen fra brugeren og fjerne den fra dine abonnementer for at stoppe med at betale for den pågældende licens. Hvis du vælger denne indstilling, fjernes licensen automatisk fra dine abonnementer.  <br/><br/> **Du kan ikke fjerne licensen** , hvis du har købt den via en partner eller volumenlicens. Hvis du betaler for en årlig plan, eller hvis du er midt i en faktureringscyklus, kan du ikke fjerne licensen fra dit abonnement, før din forpligtelse er fuldført.  <br/> |
|OneDrive indhold  <br/> |Hvis brugeren har gemt sine filer til OneDrive, kan du give en anden bruger adgang til disse filer.  <br/><br/> Du skal flytte de filer, du vil beholde, inden for den opbevaringsperiode, der er angivet for OneDrive filer. **Opbevaringsperioden er som standard 30 dage.** Hvis du ikke flytter filerne inden for opbevaringsperioden efter sletning af brugeren, flyttes OneDrive for den slettede bruger til papirkurven for gruppen af websteder, hvor den opbevares i 93 dage. I denne periode vil brugerne ikke længere kunne få adgang til delt indhold i OneDrive. Hvis du vil gendanne OneDrive, skal du bruge PowerShell. Du kan finde flere oplysninger under [Gendan en slettet OneDrive](/onedrive/restore-deleted-onedrive).<br/><br/> Hvis du vil øge det antal dage, du bevarer OneDrive filer for slettede konti, skal du se [Angiv opbevaring af OneDrive for slettede brugere](/onedrive/set-retention).  <br/><br/> **Vigtigt!** Hvis den slettede bruger har brugt en personlig computer til at downloade filer fra SharePoint og OneDrive, kan du ikke slette de filer, de har gemt på deres computer. De vil fortsat have adgang til filer, der blev synkroniseret fra OneDrive.           |
|E-mail  <br/> | Hvis du giver en anden bruger adgang til den slettede brugers mail, konverteres den slettede brugers postkasse til en delt postkasse. Den nye postkasseejer kan derefter få adgang til postkassen og overvåge nye mails. Du har også følgende muligheder:  <br/>  <br/>Skift det viste navn – Vi anbefaler, at du ændrer det viste navn, så det er nemt at identificere den delte postkasse på listen **Aktive brugere** .  <br/>  <br/>  Slå autosvar til - Vi har allerede skrevet et høfligt autosvar til dig. Du kan sende forskellige autosvar til personer i din organisation og personer uden for organisationen. <br/> <br/> [Fjern alle eksisterende kalendertilladelser](/powershell/module/exchange/remove-mailboxfolderpermission?view=exchange-ps) ved hjælp af PowerShell. <br/> <br/> Ryd op i aliasser – Aliasser er yderligere mailadresser for brugere. Nogle organisationer bruger dem ikke, så hvis du ikke har nogen, behøver du ikke at foretage dig andet her. Hvis brugeren har aliasser, anbefaler vi, at du fjerner dem, så du kan genbruge disse mailadresser. Ellers kan du ikke genbruge disse mailadresser, før opbevaringsperioden for slettede postkasser er overskredet. En slettet postkasse kan som standard gendannes i 30 dage. Du kan finde flere oplysninger under [Slet eller gendan brugerpostkasser i Exchange Online](/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes#delete-a-user-mailbox). <br/> |
|Active Directory  <br/> |Hvis din virksomhed bruger **Active Directory** , der synkroniseres med Azure AD, skal du slette brugerkontoen fra Active Directory. Du kan ikke gøre det gennem Office 365. Du kan finde [instruktioner under Slet en brugerkonto](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)).  <br/> |

### <a name="get-started"></a>Kom i gang

Da den guidede oplevelse gennemgår trinnene til sletning af en bruger, kan du komme i gang her.

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .

::: moniker-end

::: moniker range="o365-21vianet"

 1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a> .

::: moniker-end

2. Vælg den bruger, du vil slette, og vælg derefter **Slet bruger**.

## <a name="user-management-admin-delete-one-or-more-users-from-office-365"></a>Administrator af brugeradministration: Slet en eller flere brugere fra Office 365

> [!IMPORTANT]
> Slet ikke en brugers konto, hvis du har [konverteret den til en delt postkasse](../email/convert-user-mailbox-to-shared-mailbox.md) , eller hvis du har konfigureret videresendelse af mail på kontoen. Disse funktioner har stadig brug for kontoen. En delt postkasse kræver ikke en licens. Hvis du har konverteret kontoen til en delt postkasse, kan du [stoppe med at betale for licensen](#stop-paying-for-the-license). Hvis du har konfigureret videresendelse af mail på kontoen, kan du ikke fjerne licensen. Hvis du gør det, stoppes videresendelse af mail, og postkassen deaktiveres.
  
::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .  

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a> .

::: moniker-end

2. Vælg navnene på de brugere, du vil slette, vælg de tre prikker (flere handlinger), og vælg derefter  **Slet bruger**.

   Selvom du har slettet brugerens konto, **betaler du stadig for licensen**. Se den næste procedure for at stoppe med at betale for licensen.  Du kan også tildele licensen til en anden bruger. Den tildeles ikke automatisk til nogen.

### <a name="stop-paying-for-the-license"></a>Stop med at betale for licensen

Reduktion af antallet af licenser er et separat trin, der kun kan udføres af den globale administrator eller faktureringsadministrator.
  
::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Fakturering**\><a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Dine produkter</a>.
::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden **Fakturering**\><a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Dine produkter</a>.
::: moniker-end

2. Under fanen **Produkter** skal du vælge det abonnement, du vil fjerne licenser for.

3. På siden med abonnementsoplysninger skal du vælge **Fjern licenser**.

4. I ruden **Fjern licenser** under **Ny mængde** skal du i feltet **Antal licenser i alt** angive det samlede antal licenser, du vil have til dette abonnement. Hvis du f.eks. har 100 licenser, og du vil fjerne fem af dem, skal du angive 95.

5. Vælg **Gem**.

Når du senere gennemgår trinnene for at føje en anden person til din virksomhed, bliver du bedt om at købe en licens på samme tid med kun ét trin!

## <a name="delete-many-users-at-the-same-time"></a>Slet mange brugere på samme tid

Se PowerShell-cmdlet'en [Remove-MsolUser](/powershell/module/msonline/remove-msoluser) .

## <a name="fix-issues-with-deleting-a-user"></a>Løs problemer med at slette en bruger

Her er de mest almindelige problemer, som personer støder på, når de sletter en bruger:
  
- **Du får vist en fejlmeddelelse i stil med "Brugeren kan ikke slettes. Prøv igen senere."** Dobbelttjek, om kontoen har konfigureret videresendelse af mail, eller om den er konverteret til en delt postkasse. Begge disse vil forårsage denne fejl. Slet ikke kontoen, hvis den har videresendelse af mail, eller hvis den er blevet konverteret til en delt postkasse.

- **Du har ikke de nødvendige tilladelser til at slette en bruger**. Det er kun personer, der er [Microsoft 365 globale administratorer eller administratorer af brugeradministration](about-admin-roles.md), der kan slette brugere. Normalt er dette den tekniske support i din skole eller virksomhed.

- **Du sletter brugeren, men vedkommendes navn vises fortsat i det globale adressekartotek**. Dette sker, når en virksomhed bruger Active Directory. Du skal slette brugerkontoen fra Active Directory. Du kan finde [instruktioner under Slet en brugerkonto.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11))

**Vil du slette Microsoft 365 fra computeren? Gå til [Annuller dit abonnement](../../commerce/subscriptions/cancel-your-subscription.md).**

## <a name="related-content"></a>Relateret indhold

[Gendan en bruger](restore-user.md) (artikel)\
[Slet en postkasse](/exchange/permanently-delete-a-mailbox-exchange-2013-help) permanent (artikel)\
[Fjern en tidligere medarbejder fra Office 365](remove-former-employee.md) (artikel)\
[Føj en ny medarbejder til Office 365](add-new-employee.md) (artikel)\
[Slet en brugerkonto](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)): Brug disse instruktioner, hvis din virksomhed bruger **Active Directory** , der synkroniseres med Azure AD. Du kan ikke gøre det gennem Office 365. (artikel)
