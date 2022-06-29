---
title: Nulstil adgangskoder
f1.keywords:
- NOCSH
ms.author: v-kcirillo
author: cirilk
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
description: Nulstil adgangskoder for brugere i Microsoft 365 Business Premium.
ms.openlocfilehash: a2841c3819011237fcb0dce3af58b4009d537904
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489683"
---
# <a name="reset-passwords-in-microsoft-365-business-premium"></a>Nulstil adgangskoder i Microsoft 365 Business Premium

Få mere at vide om, hvordan du nulstiller adgangskoder til dig selv og dine brugere, når det er nødvendigt. Som administrator kan du nulstille en brugers adgangskode, hvis vedkommende glemmer den.

## <a name="user-initiated-password-reset"></a>Brugerinitieret nulstilling af adgangskode

Når en bruger anmoder om en ny adgangskode, sendes der en anmodning om nulstilling af adgangskode via mail.

1. Hvis du vil nulstille adgangskoden, skal du åbne appstarteren og vælge **Administration** og logge på med dine legitimationsoplysninger.

2. I Microsoft 365 Administration skal du vælge **Brugere**, <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Aktive brugere**</a> og derefter vælge nøgleikonet ud for den bruger, der anmodede om nulstillingen.

3. Vælg **Opret automatisk adgangskode** for at få oprettet en vilkårlig adgangskode automatisk.

4. Vælg **Nulstil**.

## <a name="admin-initiated-password-reset"></a>Administration startet nulstilling af adgangskode

Der er tidspunkter, hvor en administrator måske ønsker at gennemtvinge nulstilling af adgangskode på konti.

1. I Administration center skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">aktive brugere</a>.

2. På siden **Aktive brugere** skal du vælge den specifikke bruger, der skal nulstilles, og derefter vælge **Nulstil adgangskode**.

3. Følg vejledningen på siden **Nulstil adgangskode** for automatisk at generere en ny adgangskode til brugeren eller oprette en for brugeren, og vælg derefter **Nulstil**.  

4. Angiv en mailadresse, som brugeren kan få adgang til, så vedkommende modtager den nye adgangskode, og følg op på med dem for at sikre, at de fik den.

## <a name="let-users-reset-their-own-passwords"></a>Lad brugerne nulstille deres egne adgangskoder

Det anbefales på det kraftigste, at du konfigurerer selvbetjent nulstilling af adgangskode. På denne måde behøver du ikke manuelt at nulstille adgangskoder for dine brugere. Du kan få mere at vide under [Lad brugerne nulstille deres egne adgangskoder i Office 365](/admin/add-users/let-users-reset-passwords.md).

## <a name="reset-my-admin-password"></a>Nulstil min administratoradgangskode

Brug disse trin, hvis du har glemt din adgangskode, men du kan logge på Microsoft 365, fordi din adgangskode f.eks. gemmes i din browser:

1. Vælg dit navn (ikon) i øverste højre hjørne >**Personlige oplysninger om** **Min konto** > .

2. Under **Kontaktoplysninger** skal du dobbelttjekke, at din **alternative mail** er præcis, og at du har angivet et mobiltelefonnummer. Hvis ikke, skal du ændre dem nu.

3. Log af: Vælg dit navn i øverste højre hjørne \> **Log af**.

4. Log på igen: Skriv dit brugernavn \> **Næste**\>, og vælg derefter **Glemt adgangskode**.

5. Følg trinnene i guiden for at nulstille adgangskoden. Den bruger dine alternative kontaktoplysninger til at bekræfte, at du er den rigtige person til at nulstille din adgangskode.

Hvis du har glemt din adgangskode og ikke kan logge på:

- Bed en anden global administrator i din virksomhed om at nulstille din adgangskode for dig.

- Sørg for, at du har angivet alternative kontaktoplysninger, herunder et mobiltelefonnummer.

## <a name="reset-all-business-passwords-for-everyone-at-the-same-time"></a>Nulstil alle virksomhedsadgangskoder for alle på samme tid

<a name="bkmk_forgot"> </a>

Disse trin fungerer for en virksomhed med mange brugere. Hvis du har hundred- eller tusindvis af brugere, kan du se næste afsnit om nulstilling af adgangskoder samlet (højst 40 brugere ad gangen).
  
1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .

2. Vælg indstillingen ud for **Vist navn** for at vælge alle i din virksomhed. Fjern derefter markeringen af dig selv. Du kan ikke nulstille din egen adgangskode samtidig med, at du nulstiller alle andres adgangskode.

3. Vælg **Nulstil adgangskode**.

4. Følg vejledningen på siden **Nulstil adgangskode** , og vælg **Nulstil**.  Hvis du har valgt automatisk generering af adgangskoder, vises de nye midlertidige adgangskoder.

5. Angiv en mailadresse, hvor du kan modtage de midlertidige adgangskoder. Du skal give dine brugere besked om deres midlertidige adgangskoder.
  
## <a name="reset-business-passwords-in-bulk"></a>Nulstil virksomhedsadgangskoder samlet

<a name="bkmk_forgot"> </a>

Hvis du vil nulstille adgangskoder for flere konti, skal du bruge PowerShell. Se dette indlæg fra Eyal Doron: [Administration af adgangskoder med PowerShell](https://go.microsoft.com/fwlink/?linkid=853696).

Du kan få en oversigt under [Administrer Microsoft 365 med PowerShell](../enterprise/manage-microsoft-365-with-microsoft-365-powershell.md).
  
## <a name="related-content"></a>Relateret indhold
  
[Lad brugerne nulstille deres egne adgangskoder](../admin/add-users/let-users-reset-passwords.md)
 [Nulstil adgangskoder i Microsoft 365 til virksomheder](../admin/add-users/reset-passwords.md)
 [Angiv en individuel brugers adgangskode til aldrig at udløbe](../admin/add-users/set-password-to-never-expire.md) 
 [Angiv politikken for udløb af adgangskode for din organisation](../admin/manage/set-password-expiration-policy.md)