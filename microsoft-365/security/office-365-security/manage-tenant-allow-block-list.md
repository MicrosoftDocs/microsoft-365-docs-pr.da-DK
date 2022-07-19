---
title: Administrer tillader og blokke på listen over tilladte/blokerede lejere
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Få mere at vide om, hvordan du administrerer tilladelser og blokke på listen over tilladte/blokerede lejere på sikkerhedsportalen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d8ac90e8e9b7b955457c9bd90cae68e18cb69915
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66859090"
---
# <a name="manage-your-allows-and-blocks-in-the-tenant-allowblock-list"></a>Administrer dine tilladelser og blokke på listen over tilladte/blokerede lejere

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365-organisationer med postkasser i Exchange Online eller enkeltstående EOP-organisationer (Exchange Online Protection) uden Exchange Online postkasser kan du være uenig i dommen om EOP-filtrering. En god meddelelse kan f.eks. være markeret som dårlig (et falsk positivt), eller der kan tillades en forkert meddelelse via (falsk negativ).

Listen over tilladte/blokerede lejere på Microsoft 365 Defender-portalen giver dig mulighed for manuelt at tilsidesætte Microsoft 365-filtreringsdommene. Lejerlisten tillad/bloker bruges under mailflow til indgående meddelelser (gælder ikke for meddelelser i organisationen) og på tidspunktet for brugerens klik. Du kan angive følgende typer tilsidesættelser:

- URL-adresser, der skal blokeres.
- Filer, der skal blokeres.
- Afsendermails eller domæner, der skal blokeres.
- Forfalskede afsendere, der skal tillades eller blokeres. Hvis du tilsidesætter den tilladte eller blokerede dom i [indsigten spoof intelligence](learn-about-spoof-intelligence.md), bliver den spoofede afsender en manuel tilladelses- eller blokindtastning, der kun vises under fanen **Spoof** på listen Over tilladte/blokerede lejere. Du kan også manuelt oprette tillad eller blokere poster for spoofed afsendere her, før de registreres af spoof intelligence.
- URL-adresser, der skal tillades.
- Filer, der skal tillades.
- Sender mails eller domæner, der skal tillades.

I denne artikel beskrives det, hvordan du konfigurerer poster på listen over tilladte/blokerede lejere på Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til Microsoft 365-organisationer med postkasser i Exchange Online; enkeltstående EOP PowerShell til organisationer uden Exchange Online  postkasser).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Politikker & regler** \> **Trusselspolitikker** \> **Lejer tillad/bloker lister** i afsnittet **Regler**. Hvis du vil gå direkte til siden **med lister over tilladte/blokerede lejere** , skal du bruge <https://security.microsoft.com/tenantAllowBlockList>.

- Du angiver filer ved hjælp af filens SHA256-hashværdi. Hvis du vil finde SHA256-hashværdien for en fil i Windows, skal du køre følgende kommando i en kommandoprompt:

  ```console
  certutil.exe -hashfile "<Path>\<Filename>" SHA256
  ```

  En eksempelværdi er `768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3a`. Perceptuelle hashværdier (pHash) understøttes ikke.

- For afsendere, URL-adresser og filhash tillader lejerlisten Tillad/Bloker 500 poster hver for både tillader og blokerer, hvilket gør det til i alt 1000 poster. For spoofing (spoofed afsendere) er det samlede antal tilladte poster 1024.

- Det maksimale antal tegn for hver post er:
  - Filhashes = 64
  - URL-adresse = 250

- En post skal være aktiv inden for 30 minutter, men det kan tage op til 24 timer, før posten er aktiv.

- Poster på listen over tilladte/blokerede lejere udløber som standard efter 30 dage. Du kan angive en dato eller indstille dem til aldrig at udløbe (for bloktype af poster).

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, skal du se [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, skal du se [Opret forbindelse til Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser i Exchange Online, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil tilføje og fjerne værdier fra listen over tilladte/blokerede lejere, skal du være medlem af
    - **Rollegruppen Organisationsadministration** eller **Sikkerhedsadministrator** (**rolle som sikkerhedsadministrator**)
    - **Rollegruppe for sikkerhedsoperator** (**Lejer allowBlockList Manager**).
  - Hvis du vil have skrivebeskyttet adgang til listen over tilladte/blokerede lejere, skal du være medlem af
    - **Rollegruppe for global læser**
    - **Rollegruppe for sikkerhedslæser**
    - **Vis kun konfigurationsrollegruppe**

  Du kan få flere oplysninger [under Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Tilføjelse af brugere til den tilsvarende Azure Active Directory-rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser *og* tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  > - Rollegruppen **Vis kun organisationsadministration** i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) giver også skrivebeskyttet adgang til funktionen.

## <a name="configure-the-tenant-allowblock-list"></a>Konfigurer listen over tilladte/blokerede lejere

Hvis du vil tillade eller blokere mails, skal du se [Tillad eller bloker mails ved hjælp af lejerlisten tillad/bloker](allow-block-email-spoof.md).

Hvis du vil tillade eller blokere filer, skal du se [Tillad eller bloker filer ved hjælp af listen over tilladte/blokerede lejere](allow-block-files.md).

Hvis du vil tillade eller blokere URL-adresser, skal du se [Tillad eller bloker URL-adresser ved hjælp af listen over tilladte/blokerede lejere](allow-block-urls.md).

Disse artikler indeholder instruktioner til at tilføje eller fjerne eller redigere poster på listen over tilladte lejere/blokere ved hjælp af både Microsoft 365 Defender-portalen og Exchange Online PowerShell eller enkeltstående EOP PowerShell.

### <a name="what-to-expect-after-you-add-an-allow-or-block-entry"></a>Hvad kan du forvente, når du har tilføjet en tilladelses- eller blokindtastning?

Når du har tilføjet en tilladelsespost via indsendelsesportalen eller en blokpost på lejerlisten tillad/bloker, skal posten begynde at fungere med det samme.

Vi anbefaler, at du lader poster udløbe automatisk efter 30 dage for at se, om systemet har lært om tillad eller blok. Hvis ikke, skal du angive en ny post for at give systemet yderligere 30 dage til at lære.

## <a name="view-entries-in-the-tenant-allowblock-list"></a>Vis poster på listen over tilladte/blokerede lejere

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Politikker & regler** \> **Trusselspolitikker** \> **Lejer tillad/bloker lister** i afsnittet **Regler**. Hvis du vil gå direkte til siden **Med lejer-/bloklister** , skal du bruge <https://security.microsoft.com/tenantAllowBlockList>.

2. Vælg den ønskede fane. De kolonner, der er tilgængelige, afhænger af den fane, du har valgt:

   - **Afsendere**:
     - **Værdi**: Afsenderens domæne eller mailadresse.
     - **Handling**: Værdien **Allow** eller **Block**.
     - **Ændret af**
     - **Senest opdateret**
     - **Fjern den**
     - **Bemærkninger**
   - **Spoofing**
     - **Poofed bruger**
     - **Sender infrastruktur**
     - **Spoof-type**: Værdien **Intern** eller **Ekstern**.
     - **Handling**: Værdien **Block** eller **Allow**.
   - **URL-adresser**:
     - **Værdi**: URL-adressen.
     - **Handling**: Værdien **Allow** eller **Block**.
     - **Ændret af**
     - **Senest opdateret**
     - **Fjern den**
     - **Bemærkninger**
   - **Filer**
     - **Værdi**: Filhash.
     - **Handling**: Værdien **Allow** eller **Block**.
     - **Ændret af**
     - **Senest opdateret**
     - **Fjern den**
     - **Bemærkninger**

   Du kan klikke på en kolonneoverskrift for at sortere i stigende eller faldende rækkefølge.

   Du kan klikke på **Gruppér** for at gruppere resultaterne. De værdier, der er tilgængelige, afhænger af den fane, du har valgt:

   - **Afsendere**: Du kan gruppere resultaterne efter **handling**.
   - **Spoofing**: Du kan gruppere resultaterne efter **Handling** eller **Spoof-type**.
   - **URL-adresser**: Du kan gruppere resultaterne efter **handling**.
   - **Filer**: Du kan gruppere resultaterne efter **handling**.

   Klik på **Søg**, indtast hele eller en del af en værdi, og tryk derefter på ENTER for at finde en bestemt værdi. Når du er færdig, skal du klikke på ![Ikonet Ryd søgning.](../../media/m365-cc-sc-close-icon.png) **Ryd søgning**.

   Klik på **Filtrer** for at filtrere resultaterne. De værdier, der er tilgængelige i pop **op-vinduet Filter** , som vises, afhænger af den fane, du har valgt:

   - **Afsendere**
     - **Handling**
     - **Udløber aldrig**
     - **Dato for seneste opdatering**
     - **Fjern den**
   - **Spoofing**
     - **Handling**
     - **Spoof-type**
   - **Webadresser**
     - **Handling**
     - **Udløber aldrig**
     - **Dato for seneste opdatering**
     - **Fjern den**
   - **Filer**
     - **Handling**
     - **Udløber aldrig**
     - **Senest opdateret**
     - **Fjern den**

   Klik på **Anvend**, når du er færdig. Hvis du vil rydde eksisterende filtre, skal du klikke på **Filter** og klikke på **Ryd filtre** i pop **op-vinduet Filter**, der vises.

## <a name="modify-entries-in-the-tenant-allowblock-list"></a>Rediger poster på listen over tilladte/blokerede lejere

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Politikker & regler** \> Sektionen **Regler for trusselspolitikker**\>, **lejerlister** \> for tilladelse/blokering. Du kan også gå direkte til siden **Med lejer-/blokliste** ved at bruge <https://security.microsoft.com/tenantAllowBlockList>.

2. Vælg den fane, der indeholder den type post, du vil ændre:
   - **Afsendere**
   - **Spoofing**
   - **Webadresser**
   - **Filer**

3. Vælg den post, du vil redigere, og klik derefter på ![Ikonet Rediger.](../../media/m365-cc-sc-edit-icon.png) **Rediger**. De værdier, du kan ændre i det pop op-vindue, der vises, afhænger af den fane, du valgte i det forrige trin:
   - **Afsendere**
     - **Udløber aldrig** og/eller udløbsdatoen.
     - **Valgfri note**
   - **Spoofing**
     - **Handling**: Du kan ændre værdien til **Tillad** eller **Bloker**.
   - **Webadresser**
     - **Udløber aldrig** og/eller udløbsdatoen.
     - **Valgfri note**
   - **Filer**
     - **Udløber aldrig** og/eller udløbsdatoen.
     - **Valgfri note**

    Bemærk, at værdierne for afsendere, URL-adresser og filer aldrig udløber kun for blokerede poster. 

4. Klik på **Gem**, når du er færdig.

> [!NOTE]
> Du kan kun forlænge med maksimalt 30 dage efter oprettelsesdatoen. Blokke kan forlænges i op til 90 dage, men i modsætning til tillader, kan de også indstilles til Aldrig udløber.

## <a name="remove-entries-from-the-tenant-allowblock-list"></a>Fjern poster fra listen over tilladte/blokerede lejere

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Politikker & regler** \> Sektionen **Regler for trusselspolitikker**\>, **lejerlister** \> for tilladelse/blokering. Du kan også gå direkte til siden **Med lejer-/blokliste** ved at bruge <https://security.microsoft.com/tenantAllowBlockList>.

2. Vælg den fane, der indeholder den type post, du vil fjerne:
   - **Afsendere**
   - **Spoofing**
   - **Webadresser**
   - **Filer**

3. Vælg den post, du vil fjerne, og klik derefter på ![Ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) **Slet**.

4. Klik på **Slet** i den viste advarselsdialogboks.

## <a name="related-articles"></a>Relaterede artikler

- [Tillad eller bloker filer på listen over tilladte/blokerede lejere](allow-block-files.md)
- [Tillad eller bloker mails på listen over tilladte/blokerede lejere](allow-block-email-spoof.md)
- [Tillad eller bloker URL-adresser på listen over tilladte/blokerede lejere](allow-block-urls.md)
