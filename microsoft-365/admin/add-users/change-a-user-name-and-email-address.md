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
description: Få mere at vide om, hvordan en global Microsoft 365-administrator kan ændre en brugers mailadresse og viste navn, når vedkommendes navn ændres.
ms.openlocfilehash: 420a25df1383bccd4fe93b2ea79d0eeb6f91d982
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66601108"
---
# <a name="change-a-user-name-and-email-address"></a>Rediger et brugernavn og en mailadresse

Se [Hjælp til små virksomheder i Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2197659) på YouTube.

Du skal muligvis ændre en persons mailadresse og viste navn, hvis de f.eks. bliver gift, og deres efternavn ændres.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist har du og dine medarbejdere adgang til specialister i små virksomheder døgnet rundt, efterhånden som du får din virksomhed til at vokse, lige fra onboarding til hverdagsbrug.

## <a name="watch-change-a-users-name-or-email-address"></a>Se: Skift en brugers navn eller mailadresse

Se denne video og andre på vores [YouTube-kanal](https://go.microsoft.com/fwlink/?linkid=2198016).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1SJuc]

1. Vælg **Aktive** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**brugere**</a> i Microsoft 365 Administration.
1. Vælg brugeren på listen over aktive brugere.
1. Vælg **Administrer kontaktoplysninger**.
1. Rediger det viste navn, og vælg **Gem ændringer**.

Hvis du har fundet denne video nyttig, kan du se den [komplette træningsserie for små virksomheder og nye i Microsoft 365](../../business-video/index.yml).

## <a name="before-you-begin"></a>Før du begynder

Du skal være [global administrator](about-admin-roles.md) for at fuldføre disse trin.

## <a name="change-a-users-email-address"></a>Skift en brugers mailadresse

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a> .

::: moniker-end

1. Vælg brugerens navn, og vælg derefter **Administrer brugernavn** under fanen **Konto**.

1. Skriv den første del af den nye mailadresse i det første felt. Hvis du har føjet dit eget domæne til Microsoft 365, skal du vælge domænet for det nye mailalias ved hjælp af rullelisten. [Få mere at vide om, hvordan du tilføjer et domæne](../setup/add-domain.md).

1. Vælg **Gem ændringer**.

> [!IMPORTANT]
> Hvis du får vist en fejlmeddelelse, skal du se [Løs fejlmeddelelser](#resolve-error-messages).

## <a name="set-the-primary-email-address"></a>Angiv den primære mailadresse

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a> .

::: moniker-end

2. Vælg brugerens navn, og vælg derefter **Administrer mailaliasser** under fanen **Konto**.

3. Vælg **Angiv som primær** for den mailadresse, du vil angive som den primære mailadresse for den pågældende person.

   > [!IMPORTANT]
   > Du kan ikke se denne indstilling for Angiv som primær, hvis du har købt Microsoft 365 fra GoDaddy eller en anden partnertjeneste, der leverer en administrationskonsol. Log i stedet på GoDaddy/partnerens administrationskonsol for at angive det primære alias.
   >
   > Du kan også kun se denne indstilling, hvis du er global administrator. Hvis du ikke kan se indstillingen, har du ikke tilladelse til at ændre en brugers navn og primære mailadresse.

4. Du får vist en stor gul advarsel om, at du er ved at ændre personens logonoplysninger. Vælg **Gem** og derefter **Luk**.

5. Giv personen følgende oplysninger:

   - Denne ændring kan tage et stykke tid.

   - Deres nye brugernavn. De skal bruge den for at logge på Microsoft 365.

   - Hvis de bruger Skype for Business Online, skal de omlægge de Skype for Business Online-møder, som de har organiseret, og bede deres eksterne kontakter om at opdatere deres kontaktoplysninger.

   - Hvis de bruger OneDrive, er URL-adressen til denne placering blevet ændret. Hvis de har OneNote-notesbøger i deres OneDrive, skal de muligvis lukke og genåbne dem i OneNote. Hvis de har delt filer fra deres OneDrive, fungerer linkene til filerne muligvis ikke, og brugeren kan dele igen.

   - Hvis adgangskoden også ændres, bliver vedkommende bedt om at angive den nye adgangskode på sin mobilenhed, eller den synkroniseres ikke.

## <a name="change-a-users-display-name"></a>Skift en brugers viste navn

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> . 

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a> .

::: moniker-end

2. Vælg brugerens navn, og vælg derefter **Administrer kontaktoplysninger** under fanen **Konto**.

3. Skriv et nyt navn til personen i feltet **Vist navn** , og vælg derefter **Gem**.

   Hvis du får vist fejlmeddelelsen "**Vi beklager, men brugeren kunne ikke redigeres. Gennemse brugeroplysningerne, og prøv igen**. Se [Løs fejlmeddelelser](#resolve-error-messages).

Det kan tage op til 24 timer, før ændringen træder i kraft på tværs af alle tjenester. Når ændringen er trådt i kraft, skal personen logge på Outlook, Skype for Business og SharePoint med deres opdaterede brugernavn.

## <a name="resolve-error-messages"></a>Løs fejlmeddelelser

### <a name="a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>"Der blev ikke fundet en parameter, der svarer til parameternavnet 'EmailAddresses"

Hvis du får vist fejlmeddelelsen " **Der blev ikke fundet en parameter, der svarer til parameternavnet 'EmailAddresses**', betyder det, at det tager lidt længere tid at fuldføre indstillingerne for lejeren, eller dit brugerdefinerede domæne, hvis du for nylig har tilføjet et. Det kan tage op til fire timer at fuldføre konfigurationsprocessen. Vent et stykke tid, så installationsprocessen har tid til at afslutte, og prøv derefter igen. Hvis problemet fortsætter, skal du ringe til [support](../../business-video/get-help-support.md) og bede dem om at foretage en fuld synkronisering for dig.

### <a name="were-sorry-the-user-couldnt-be-edited-review-the-user-information-and-try-again"></a>"Vi beklager, men brugeren kunne ikke redigeres. Gennemse brugeroplysningerne, og prøv igen"

Hvis du får vist fejlmeddelelsen " **Vi beklager, men brugeren kunne ikke redigeres. Gennemse brugeroplysningerne, og prøv igen**." Det betyder, at du ikke er global administrator, og at du ikke har tilladelse til at ændre brugernavnet. Find den globale administrator i din virksomhed, og bed vedkommende om at foretage ændringen.

## <a name="what-to-do-with-old-email-addresses"></a>Hvad skal man gøre med gamle mailadresser?

En persons tidligere primære mailadresse bevares som en ekstra mailadresse. **Vi anbefaler på det kraftigste, at du ikke fjerner den gamle mailadresse.**

Nogle personer kan fortsætte med at sende mail til personens gamle mailadresse, og sletning af den kan resultere i NDR-fejl. Microsoft distribuerer automatisk den til den nye. Genbrug heller ikke gamle SMTP-mailadresser, og anvend dem på nye konti. Dette kan også medføre NDR-fejl eller levering til en utilsigtet postkasse.

## <a name="what-if-the-persons-offline-address-book-wont-sync-with-the-global-address-list"></a>Hvad sker der, hvis personens offlineadressekartotek ikke synkroniseres med den globale adresseliste?

Hvis vedkommende bruger Exchange Online, eller hvis vedkommendes konto er knyttet til din organisations Lokale Exchange-miljø, kan du få vist denne fejl, når du forsøger at ændre et brugernavn og en mailadresse: "Denne bruger er synkroniseret med dit lokale Active Directory. Nogle detaljer kan kun redigeres via dit lokale Active Directory."

Dette skyldes Microsoft Online Email Routing Address (MOERA). MOERA er oprettet ud fra personens  _userPrincipalName-attribut_ i Active Directory og tildeles automatisk til cloudkontoen under den indledende synkronisering, og når den først er oprettet, kan den ikke ændres eller fjernes i Microsoft 365. Du kan efterfølgende ændre brugernavnet i Active Directory, men det ændrer ikke MOERA, og du kan støde på problemer med at vise det nyligt ændrede navn på den globale adresseliste.

Du kan løse problemet ved at logge på [Azure Active Directory-modulet til PowerShell](https://go.microsoft.com/fwlink/?LinkId=823193) med dine legitimationsoplysninger til Microsoft 365-administratoren. og brug følgende syntaks:

```powershell
Set-MsolUserPrincipalName -UserPrincipalName anne.wallace@contoso.onmicrosoft.com -NewUserPrincipalName anne.jones@contoso.com
```

> [!TIP]
> Dette ændrer personens **userPrincipalName-attribut** og har ingen indflydelse på vedkommendes MOERA-mailadresse (Microsoft Online Email Routing Address). Det er dog bedste praksis at få personens logon-UPN til at matche vedkommendes primære SMTP-adresse.

Du kan få mere at vide om, hvordan du ændrer en persons brugernavn i Active Directory i Windows Server 2003 og tidligere under [Omdøb en brugerkonto](/previous-versions/windows/it-pro/windows-server-2003/cc772952(v=ws.10)).

## <a name="related-content"></a>Relateret indhold

[Tilføj et domæne](../setup/add-domain.md)
 [Administratorer: Nulstil en adgangskode for en eller flere brugere](reset-passwords.md)
 [Føj en anden mailadresse til en bruger](../email/add-another-email-alias-for-a-user.md)
 [Opret en delt postkasse](../email/create-a-shared-mailbox.md)
