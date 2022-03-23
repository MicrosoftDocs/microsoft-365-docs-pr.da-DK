---
title: Rediger et brugernavn og en mailadresse
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
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
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: fb5ac074-e203-4e1f-9843-b9d1a3e03297
description: 'Lær, hvordan Microsoft 365 global administrator kan ændre en brugers mailadresse og visningsnavn, når deres navn ændres. '
ms.openlocfilehash: 3c3b83028ba2086cc167895075b9099795d988dc
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63589290"
---
# <a name="change-a-user-name-and-email-address"></a>Rediger et brugernavn og en mailadresse

Det kan være nødvendigt at ændre en andens mailadresse og viste navn, hvis de f.eks. gifter sig og får et andet efternavn.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialspecialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist får du og dine medarbejdere døgnet rundt adgang til små virksomhedsspecialister, efterhånden som du vokser din virksomhed, fra onboarding til daglig brug.

## <a name="watch-change-a-users-name-or-email-address"></a>Se: Skift en brugers navn eller mailadresse

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1SJuc]

1. Vælg Microsoft 365 Administration <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Brugereaktive brugere**</a> >  i dialogboksen Indstillinger.
1. Vælg brugeren på listen over aktive brugere.
1. Vælg **Administrer kontaktoplysninger**.
1. Skift det viste navn, og vælg **Gem ændringer**.

Hvis du synes, denne video var nyttig, kan du [se den komplette kursusserie til små virksomheder og dem, der er nye Microsoft 365](../../business-video/index.yml).

## <a name="before-you-begin"></a>Før du begynder

Du skal være [global administrator for](about-admin-roles.md) at udføre disse trin.

## <a name="change-a-users-email-address"></a>Ændre en brugers mailadresse

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">for</a> brugere.

::: moniker-end

1. Vælg brugerens navn, og vælg derefter Administrer **brugernavn under** **fanen Konto**.

1. I det første felt skal du skrive den første del af den nye mailadresse. Hvis du har føjet dit eget domæne Microsoft 365, skal du vælge domænet til det nye mailalias ved hjælp af rullelisten. [Få mere at vide om, hvordan du tilføjer et domæne](../setup/add-domain.md).

1. Vælg **Gem ændringer**.

> [!IMPORTANT]
> Hvis du får vist en fejlmeddelelse, skal du [se Løs fejlmeddelelser](#resolve-error-messages).

## <a name="set-the-primary-email-address"></a>Angiv den primære mailadresse

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">for</a> brugere.

::: moniker-end

2. Vælg brugerens navn, og vælg derefter Administrer **mailaliasser** **på fanen Konto**.

3. Vælg **Angiv som primær** for den mailadresse, du vil angive som den primære mailadresse for den pågældende person.

   > [!IMPORTANT]
   > Du får ikke vist denne indstilling til Angiv som primær, hvis du har købt Microsoft 365 fra GoDaddy eller en anden Partner-tjeneste, der indeholder en administrationskonsol. Log i stedet på GoDaddys/partnerens administrationskonsol for at angive det primære alias.
   >
   > Desuden får du kun vist denne indstilling, hvis du er global administrator. Hvis du ikke kan se indstillingen, har du ikke tilladelse til at ændre en brugers navn og primære mailadresse.

4. Du får vist en stor gul advarsel om, at du er ved at ændre personens logonoplysninger. Vælg **Gem** og derefter **Luk**.

5. Giv personen følgende oplysninger:

   - Denne ændring kan tage et stykke tid.

   - Deres nye brugernavn. De skal bruge det for at logge på Microsoft 365.

   - Hvis de bruger Skype for Business Online, skal de ændre deres tidsplan for alle Skype for Business Online-møder, de har organiseret, og bede deres eksterne kontakter om at opdatere deres kontaktoplysninger.

   - Hvis de bruger OneDrive, er URL-adressen til denne placering ændret. Hvis de OneNote notesbøger i deres OneDrive, skal de muligvis lukke og genåbne dem OneNote. Hvis de har delte filer fra deres OneDrive, fungerer linkene til filerne muligvis ikke, og brugeren kan dele igen.

   - Hvis adgangskoden også er ændret, bliver de bedt om at angive den nye adgangskode på deres mobilenhed, ellers synkroniseres den ikke.

## <a name="change-a-users-display-name"></a>Ændre en brugers viste navn

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere. 

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">for</a> brugere.

::: moniker-end

2. Vælg brugerens navn, og vælg derefter Administrer **kontaktoplysninger** på **fanen Konto**.

3. Skriv et **nyt navn** til personen i feltet Vist navn, og vælg derefter **Gem**.

   Hvis du får fejlmeddelelsen "**Vi beklager, men brugeren kunne redigeres. Gennemse brugeroplysningerne, og prøv igen**. [Se Løs fejlmeddelelser](#resolve-error-messages).

Det kan tage op til 24 timer, før denne ændring træder i kraft i alle tjenester. Når ændringen er gået i kraft, skal personen logge på med Outlook, Skype for Business og SharePoint med sit opdaterede brugernavn.

## <a name="resolve-error-messages"></a>Løs fejlmeddelelser

### <a name="a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>"Der blev ikke fundet en parameter, der svarer til parameternavnet 'Mailadresser"

Hvis fejlmeddelelsen " Der blev ikke fundet en parameter, der svarer til **parameternavnet "Mailadresser**" vises, betyder det, at det tager lidt længere tid at fuldføre konfigurationen af din lejer eller dit brugerdefinerede domæne, hvis du for nyligt tilføjede et. Installationen kan tage op til fire timer at gennemføre. Vent lidt, så installationen kan blive fuldført, og prøv derefter igen. Hvis problemet fortsætter, skal du ringe [til support](../../business-video/get-help-support.md) og bede dem om at udføre en fuld synkronisering for dig.

### <a name="were-sorry-the-user-couldnt-be-edited-review-the-user-information-and-try-again"></a>"Vi beklager, men brugeren kunne redigeres. Gennemse brugeroplysningerne, og prøv igen"

Hvis du får fejlmeddelelsen " **Vi beklager, men brugeren kunne redigeres. Gennemse brugeroplysningerne, og prøv igen**." betyder det, at du ikke er global administrator, og at du ikke har tilladelse til at ændre brugernavnet. Find den globale administrator i din virksomhed, og bed vedkommende om at foretage ændringen.

## <a name="what-to-do-with-old-email-addresses"></a>Hvad kan du gøre med gamle mailadresser?

En persons tidligere primære mailadresse bevares som en ekstra mailadresse. **Vi anbefaler på det kraftigste, at du ikke fjerner den gamle mailadresse.**

Nogle personer kan fortsætte med at sende mails til personens gamle mailadresse, og hvis du sletter den, kan det medføre NDR-fejl. Microsoft sender den automatisk til den nye. Genbrug heller ikke gamle SMTP-mailadresser, og anvend dem på nye konti. Dette kan også forårsage NDR-fejl eller levering til en utilsigtet postkasse.

## <a name="what-if-the-persons-offline-address-book-wont-sync-with-the-global-address-list"></a>Hvad nu, hvis personens offlineadressekartotek ikke kan synkroniseres med den globale adresseliste?

Hvis de bruger Exchange Online, eller hvis deres konto er sammenkædet med din organisations lokale Exchange-miljø, får du muligvis vist denne fejl, når du forsøger at ændre et brugernavn og en mailadresse: "Denne bruger er synkroniseret med dit lokale Active Directory. Nogle detaljer kan kun redigeres via dit lokale Active Directory."

Dette skyldes MICROSOFT Online Email Routing Address (MOERA). MOERA er opbygget ud fra personens _userPrincipalName-attribut_ i Active Directory og tildeles automatisk til skykontoen under den indledende synkronisering, og når den er oprettet, kan den ikke ændres eller fjernes Microsoft 365. Du kan efterfølgende ændre brugernavnet i Active Directory, men det ændrer ikke MOERA, og du kan komme ud for problemer med at få vist det nyligt ændrede navn i den globale adresseliste.

Det løser du ved at logge på [Azure Active Directory Module for PowerShell](https://go.microsoft.com/fwlink/?LinkId=823193) med dine Microsoft 365 legitimationsoplysninger som administrator. og bruge følgende syntaks:

```powershell
Set-MsolUserPrincipalName -UserPrincipalName anne.wallace@contoso.onmicrosoft.com -NewUserPrincipalName anne.jones@contoso.com
```

> [!TIP]
> Dette ændrer brugerens **userPrincipalName-attribut** og har ingen indflydelse på vedkommendes Microsoft Online Email Routing Address-mailadresse (MOERA). Den bedste fremgangsmåde er dog at få personens logon-UPN til at matche vedkommendes primære SMTP-adresse.

Hvis du vil lære, hvordan du ændrer en andens brugernavn i Active Directory i Windows Server 2003 og tidligere, skal du se [Omdøbe en brugerkonto](/previous-versions/windows/it-pro/windows-server-2003/cc772952(v=ws.10)).

## <a name="related-content"></a>Relateret indhold

[Tilføj et domæne](../setup/add-domain.md)
 [Administratorer: Nulstil en adgangskode for en eller flere brugere](reset-passwords.md)
 [Føj en anden mailadresse til en bruger](../email/add-another-email-alias-for-a-user.md)
 [Opret en delt postkasse](../email/create-a-shared-mailbox.md)
