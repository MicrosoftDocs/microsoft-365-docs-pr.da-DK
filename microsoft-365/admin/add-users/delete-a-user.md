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
description: Få mere at vide om, hvordan du sletter en brugerkonto, og hvad du skal gøre med brugerens mail- OneDrive indhold, og om du vil beholde produktlicensen.
ms.openlocfilehash: 462e9bcec4dac7e9d708618777ea58fb5d182473
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63589288"
---
# <a name="delete-a-user-from-your-organization"></a>Slet en bruger fra din organisation
  
**Leder du efter, hvordan du *sletter din* Microsoft 365 brugerkonto, som du bruger på arbejdet eller i skolen? Kontakt den tekniske support på dit arbejde eller universitet for at få dem til at udføre disse trin for dig.**

## <a name="before-you-begin"></a>Før du begynder

- Det er kun personer [Microsoft 365 der har de globale administrator](about-admin-roles.md)- eller brugeradministratortilladelser for virksomheden eller skolen, der kan slette brugerkonti.
- Du har 30 dage [til](restore-user.md) at gendanne kontoen, før brugerens data slettes permanent.
- Hvis du vil bevare brugerens data OneDrive, skal du flytte dem til en anden placering. Du kan endda flytte dataene op til 30 dage, efter du har slettet kontoen. Se [Få adgang til og sikkerhedskopier af en tidligere brugers data](get-access-to-and-back-up-a-former-user-s-data.md). Du behøver ikke at flytte deres SharePoint filer, du har stadig adgang til dem.
- Hvis du vil bevare brugerens mail, skal du **flytte mailen** til en anden placering, INDEN du sletter kontoen. Hvis du allerede har slettet kontoen: Hvis der er gået mindre 30 dage, kan du gendanne den og derefter flytte maildataene og derefter slette kontoen. Se [Få adgang til og sikkerhedskopier af en tidligere brugers data](get-access-to-and-back-up-a-former-user-s-data.md).
- Hvis du har et Enterprise-abonnement som Office 365 Enterprise E3, kan du bevare postkassedata fra en slettet brugerkonto ved at gøre den til en *inaktiv postkasse*. Du kan få mere at vide [under Administrer inaktive postkasser i Exchange Online](../../compliance/inactive-mailboxes-in-office-365.md).

## <a name="global-admin-delete-a-user-stop-paying-for-their-license-and-choose-what-to-do-with-their-email-and-onedrive-content"></a>Global administrator: Slet en bruger, stop med at betale for brugerens licens, og vælg, hvad der skal gøre med brugerens mail og OneDrive indhold

Hvis du er global administrator, kan du, når du sletter en bruger, også give en anden bruger adgang til deres mail og vælge, hvad du vil gøre med deres OneDrive indhold.

### <a name="things-to-consider"></a>Ting, du skal overveje

Før du begynder, skal du tænke over, hvad du vil gøre med brugerens mail- og OneDrive indhold, og om du vil beholde licensen eller ophøre med at betale for den.
  
|Element | Beskrivelse |
|:-----|:-----|
|Produktlicenser  <br/> |Du kan fjerne licensen fra brugeren og fjerne den fra dine abonnementer for at holde op med at betale for den pågældende licens. Hvis du vælger denne indstilling, fjernes licensen automatisk fra dine abonnementer.  <br/><br/> **Du kan ikke fjerne licensen, hvis** du har købt den via en partner eller volumenlicens. Hvis du betaler for en årlig plan, eller hvis du er midt i en faktureringscyklus, kan du ikke fjerne licensen fra dit abonnement, før din bindingsperiode er slut.  <br/> |
|OneDrive indhold  <br/> |Hvis brugeren har gemt sine filer på en OneDrive, kan du give en anden bruger adgang til disse filer.  <br/><br/> Du skal flytte de filer, du vil beholde, inden for den opbevaringsperiode, der er angivet for OneDrive filer. **Som standard er en opbevaringsperiode på 30 dage.** Hvis du ikke flytter filerne inden for opbevaringsperioden, efter du har slettet brugeren, flyttes OneDrive for den slettede bruger til papirkurven for gruppen af websteder, hvor den opbevares i 93 dage. I dette tidsrum vil brugerne ikke længere have adgang til delt indhold i OneDrive. Hvis du vil OneDrive, skal du bruge PowerShell. Du kan finde flere [oplysninger i gendanne et slettet OneDrive](/onedrive/restore-deleted-onedrive).<br/><br/> Hvis du vil øge antallet af dage, du OneDrive filer til slettede konti, skal du se Angiv [opbevaringen OneDrive slettede brugere](/onedrive/set-retention).  <br/><br/> **Vigtigt!** Hvis den slettede bruger brugte sin egen computer til at downloade filer fra SharePoint og OneDrive, er det ikke muligt for dig at slette de filer, brugeren har gemt på computeren. De vil fortsat have adgang til filer, der blev synkroniseret fra OneDrive.           |
|Mail  <br/> | Hvis du giver en anden bruger adgang til den slettede brugers mail, konverteres den slettede brugers postkasse til en delt postkasse. Den nye postkasseejer kan derefter få adgang til postkassen og holde øje med nye mails. Du har også følgende muligheder:  <br/>  <br/>Skift det viste navn – Vi anbefaler, at du ændrer det viste navn, så det er nemt at identificere den delte postkasse på **listen over aktive** brugere.  <br/>  Aktiver autosvar – vi har allerede skrevet et høfligt autosvar for dig. Du kan sende forskellige autosvar til personer i organisationen og personer uden for organisationen.  <br/> <br/> Ryd op i aliasser – Aliasser er flere mailadresser for brugere. Nogle organisationer bruger dem ikke, så hvis du ikke har nogen, behøver du ikke at gøre mere her. Hvis brugeren har aliasser, anbefaler vi, at du fjerner dem, så du kan genbruge disse mailadresser. Ellers kan du ikke genbruge disse mailadresser, før opbevaringsperioden for slettede postkasser er overskredet. En slettet postkasse kan som standard gendannes i 30 dage. Få mere at vide under [Slet eller gendan brugerpostkasser i Exchange Online](/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes#delete-a-user-mailbox). <br/> |
|Active Directory  <br/> |Hvis din virksomhed bruger **Active Directory** , der synkroniseres med Azure AD, skal du slette brugerkontoen fra Active Directory. Du kan ikke gøre det via Office 365. Du kan finde en vejledning [under Slet en brugerkonto](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)).  <br/> |

### <a name="get-started"></a>Kom i gang

Da vejledningen gennemgår trinnene til at slette en bruger, kan du se her, hvordan du kommer i gang.

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.

::: moniker-end

::: moniker range="o365-21vianet"

 1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">for</a> brugere.

::: moniker-end

2. Vælg den bruger, du vil slette, og vælg derefter **Slet bruger**.

## <a name="user-management-admin-delete-one-or-more-users-from-office-365"></a>Administrator for brugerstyring: Slet en eller flere brugere fra Office 365

> [!IMPORTANT]
> Slet ikke en brugers konto, hvis du har konverteret den [](../email/convert-user-mailbox-to-shared-mailbox.md) til en delt postkasse, eller hvis du har konfigureret videresendelse af mail på kontoen. Disse funktioner skal stadig bruge kontoen. En delt postkasse kræver ikke en licens. Hvis du har konverteret kontoen til en delt postkasse, kan du Holde op [med at betale for licensen](#stop-paying-for-the-license). Hvis du har konfigureret videresendelse af mail på kontoen, kan du ikke fjerne licensen. Dette stopper videresendelse af mail og deaktiverer postkassen.
  
::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.  

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">for</a> brugere.

::: moniker-end

2. Vælg navnene på de brugere, du vil slette, markér de tre prik (flere handlinger), og vælg derefter  **Slet bruger**.

   Selvom du har slettet brugerens konto, **betaler du stadig for licensen**. Se den næste fremgangsmåde for at holde op med at betale for licensen.  Eller du kan tildele licensen til en anden bruger. Den bliver ikke tildelt til nogen automatisk.

### <a name="stop-paying-for-the-license"></a>Stop betalingen for licensen

Reduktion af antallet af licenser er et separat trin, der kun kan udføres af den globale administrator eller faktureringsadministrator.
  
::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Fakturering** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">dine</a> produkter.
::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Fakturering** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">dine</a> produkter.
::: moniker-end

2. På fanen **Produkter** skal du vælge det abonnement, du vil fjerne licenser til.

3. På siden med abonnementsoplysninger skal du vælge **Fjern licenser**.

4. I **ruden Fjern** licenser under **Nyt antal** i feltet **Samlet** antal licenser skal du angive det samlede antal licenser, du ønsker for dette abonnement. Hvis du f.eks. har 100 licenser, og du vil fjerne fem af dem, skal du angive 95.

5. Vælg **Gem**.

Senere når du gennemgår trinnene for at føje en anden person til din virksomhed, bliver du bedt om at købe en licens samtidigt med kun ét trin!

## <a name="delete-many-users-at-the-same-time"></a>Slet mange brugere på samme tid

Se [cmdlet'en Remove-MsolUser](/powershell/module/msonline/remove-msoluser) PowerShell.

## <a name="fix-issues-with-deleting-a-user"></a>Løs problemer med at slette en bruger

Her er de mest almindelige problemer, der opstår, når du sletter en bruger:
  
- **Du får en fejlmeddelelse i stil med "Brugeren kan ikke slettes. Prøv igen senere."** Kontrollér, om kontoen har konfigureret videresendelse af mail, eller om den er blevet konverteret til en delt postkasse. Begge disse vil medføre denne fejl. Slet ikke kontoen, hvis den har videresendelse af mail, eller den er blevet konverteret til en delt postkasse.

- **Du har ikke de rette tilladelser til at slette en bruger**. Kun de personer, [Microsoft 365 globale administratorer eller administratorer for brugerstyring,](about-admin-roles.md) kan slette brugere. Dette er som regel den tekniske support på din skole eller virksomhed.

- **Du sletter brugeren, men brugerens navn vises fortsat i dit globale adressekartotek**. Dette sker, når en virksomhed bruger Active Directory. Du skal slette brugerkontoen fra Active Directory. Du kan finde en vejledning [under Slet en brugerkonto.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11))

**Vil du slette Microsoft 365 fra computeren? Gå til [Annuller dit abonnement](../../commerce/subscriptions/cancel-your-subscription.md).**

## <a name="related-content"></a>Relateret indhold

[Gendan en bruger](restore-user.md) (artikel)\
[Slet en postkasse permanent](/exchange/permanently-delete-a-mailbox-exchange-2013-help) (artikel)\
[Fjern en tidligere medarbejder fra Office 365](remove-former-employee.md) (artikel)\
[Føj en ny medarbejder til Office 365](add-new-employee.md) (artikel)\
[Slet en brugerkonto](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)): Følg disse instruktioner, hvis din virksomhed bruger **Active Directory** , der synkroniseres med Azure AD. Du kan ikke gøre det via Office 365. (artikel)
