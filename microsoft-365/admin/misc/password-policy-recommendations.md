---
title: Anbefalinger til adgangskodepolitik
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9fa2539a-2211-41fd-85a0-bc37b9619ca4
description: Gør din organisation mere sikker mod adgangskodeangreb, og forbyder almindelige adgangskoder og aktivér risikobaseret multifaktorgodkendelse.
ms.openlocfilehash: 46e6c4ba163df0693630896b8db17b4eefe9828a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588507"
---
# <a name="password-policy-recommendations"></a>Anbefalinger til adgangskodepolitik

Som administrator for en organisation er du ansvarlig for at angive adgangskodepolitikken for brugere i organisationen. Det kan være kompliceret og forvirrende at angive adgangskodepolitikken, og denne artikel indeholder anbefalinger til at gøre din organisation mere sikker mod adgangskodeangreb.

Microsoft-konti, der kun er skybaserede, har en foruddefineret adgangskodepolitik, der ikke kan ændres. De eneste elementer, du kan ændre, er antallet af dage, der går, før en adgangskode udløber, og hvorvidt adgangskoder overhovedet udløber eller ej. 
  
Hvis du vil fastlægge, Microsoft 365 adgangskoder udløber i din organisation, skal du se [Angive udløbspolitik for adgangskoder Microsoft 365](../manage/set-password-expiration-policy.md).

Du kan finde flere oplysninger Microsoft 365 adgangskoder i:

[Nulstil adgangskoder](../add-users/reset-passwords.md) (artikel)

[Angiv en individuel brugers adgangskode til aldrig at udløbe](../add-users/set-password-to-never-expire.md) (artikel)

[Lad brugere nulstille deres egne adgangskoder](../add-users/let-users-reset-passwords.md) (artikel)

[Sende en brugers adgangskode igen – Hjælp til administratorer](../add-users/resend-user-password.md) (artikel)
  
## <a name="understanding-password-recommendations"></a>Forstå anbefalinger til adgangskoder

Gode adgangskodevaner kan indordnes i nogle få, brede kategorier:
  
- **Modstå almindelige angreb** Dette indebærer valget af, hvor brugerne indtaster adgangskoder (kendte og pålidelige enheder med god malwareregistrering, validerede websteder), og valget af hvilken adgangskode, der skal vælges (længde og entydighed).

- **Besigtig vellykkede angreb** At begrænse hackerangreb, der er sket, handler om at begrænse adgangen til en bestemt tjeneste eller helt at forhindre denne skade, hvis en brugers adgangskode bliver stjålet. Det kan f.eks. være at sikre, at en overtrædelse af dine legitimationsoplysninger til sociale netværk ikke gør din bankkonto sårbar eller ikke tillader en dårligt bevogtt konto at nulstille links til en vigtig konto.

- **Forstå den menneskelige natur** Mange gode adgangskodevaner står ikke under for naturlig menneskelig opførsel. Det er vigtigt at forstå den menneskelige natur, fordi forskning viser, at stort set hver eneste regel, du pålægger dine brugere, vil betyde, at adgangskoden svækkes. Længdekrav, krav til særlige tegn og krav om ændring af adgangskode fører alle til normalisering af adgangskoder, hvilket gør det nemmere for hackere at gætte eller revne adgangskoder.

## <a name="password-guidelines-for-administrators"></a>Retningslinjer for adgangskoder for administratorer

Det primære mål med et sikkert adgangskodesystem er mangfoldighed. Din adgangskodepolitik skal indeholde masser af forskellige adgangskoder, der er svære at gætte. Her er nogle anbefalinger til, hvordan du holder din organisation så sikker som muligt.
  
- Bevar et krav til minimumlængde på 8 tegn

- Du behøver ikke krav til tegnsammensætning. F.eks. \*&amp;(^%$

- Kræver ikke obligatoriske periodiske nulstillinger af adgangskoder for brugerkonti

- Forbyder almindelige adgangskoder for at holde de mest følsomme adgangskoder ude af dit system

- Opdan dine brugere, at de ikke må genbruge deres organisationsadgangskoder til ikke-arbejdsrelaterede formål

- Gennemtving registrering [for multifaktorgodkendelse](../security-and-compliance/set-up-multi-factor-authentication.md)

- Aktivér risikobaseret multifaktorgodkendelsesudfordringer

### <a name="password-guidance-for-your-users"></a>Retningslinjer for adgangskoder til dine brugere

Her er nogle retningslinjer for adgangskoder til brugerne i organisationen. Sørg for, at dine brugere kender til disse anbefalinger, og gennemtving de anbefalede adgangskodepolitikker på organisationsniveau.
  
- Brug ikke en adgangskode, der er den samme som eller ligner den, du bruger på andre websteder

- Brug ikke et enkelt ord, f.eks. **en adgangskode** eller et almindeligt brugt udtryk som **jeg loveyou**

- Gør det svært at gætte adgangskoder, selv for dem, der kender dig godt, f.eks. navne og fødselsdage på venner og familie, dit yndlingsband og sætninger, du godt kan lide at bruge

## <a name="some-common-approaches-and-their-negative-impacts"></a>Almindelige fremgangsmåder og deres negative indvirkninger

Dette er nogle af de mest almindeligt anvendte fremgangsmåder inden for administration af adgangskoder, men forskning advarer os om de negative konsekvenser af dem.
  
### <a name="password-expiration-requirements-for-users"></a>Krav til udløb af adgangskoder for brugere

Krav til udløb af adgangskoder gør mere skade end gavn, fordi disse krav får brugerne til at vælge forudsigelige adgangskoder, der består af sekvenser af ord og tal, der ligner hinanden meget. I disse tilfælde kan den næste adgangskode forudsiges ud fra den forrige adgangskode. Krav om udløb af adgangskoder giver ingen muligheder for opbevaring, fordi cyberkriminelle næsten altid bruger legitimationsoplysninger, så snart de har kompromitteret dem. Se Tid [til at genoverveje obligatorisk ændring af adgangskode](https://go.microsoft.com/fwlink/p/?linkid=861018) for at få flere oplysninger.
  
### <a name="requiring-long-passwords"></a>Krav om lange adgangskoder

Krav til adgangskodelængde (på mere end 10 tegn) kan resultere i forudsigelig og uønsket brugeradfærd. Brugere, der skal have en adgangskode på 16 tegn, kan f.eks. vælge at gentage mønstre som **fourfourfour** eller **passwordpassword** , der opfylder kravet til tegnlængde, men som ikke er svære at gætte. Kravene til længden øger desuden risikoen for, at brugerne indfører andre usikre fremgangsmåder, f.eks. at skrive deres adgangskoder ned, genbruge dem eller gemme dem ikke-krypteret i deres dokumenter. Hvis du vil opfordre brugerne til at overveje en entydig adgangskode, anbefaler vi, at du holder dig til en fornuftig minimumslængde på 8 tegn.
  
### <a name="requiring-the-use-of-multiple-character-sets"></a>Krav om brug af flere tegnsæt

Krav til kompleksiteten af adgangskoder reducerer antallet af nøgler og får brugerne til at handle på forudsigelige måder og gøre mere skade end gavn. De fleste systemer gennemtvinger et niveau af krav til kompleksiteten af adgangskoder. For eksempel skal adgangskoder bruge tegn fra alle de følgende tre kategorier:
  
- store bogstaver

- små bogstaver

- ikke-alfanumeriske tegn

De fleste bruger de samme mønstre, f.eks. et stort bogstav i første position, et symbol i den sidste og et tal i den sidste 2. Cyberkriminelle kender dette, så de kører deres ordbogsangreb med de mest almindelige erstatninger, "$" for "s", "@" for "a", "1" for "I". Når du tvinger dine brugere til at vælge en kombination af store og små bogstaver og specialtegn, har det en negativ effekt. Nogle krav til kompleksitet forhindrer endda brugere i at bruge sikre adgangskoder, der er mindeværdige, og tvinger dem til at finde på mindre sikre adgangskoder, der er lettere at huske.
  
## <a name="successful-patterns"></a>Gode mønstre

Her er til sammenligning nogle anbefalinger til, hvordan man fremmer mangfoldighed.
  
### <a name="ban-common-passwords"></a>Forbyder almindelige adgangskoder

Det vigtigste krav til adgangskoder, du skal stille til dine brugere, når du opretter adgangskoder, er at forbyde almindelige adgangskoder for at reducere din organisations følsomhed over for brute-force-angreb på adgangskoder. Almindelige brugeradgangskoder omfatter: **abcdefg**, **password**, **abe.**
  
### <a name="educate-users-to-not-reuse-organization-passwords-anywhere-else"></a>Opdater brugerne til ikke at genbruge organisationsadgangskoder andre steder

Et af de vigtigste budskaber at give brugerne i organisationen er ikke at genbruge deres organisationsadgangskoden andre steder. Brugen af organisationsadgangskoder på eksterne websteder øger risikoen for, at cyberkriminelle får adgang til disse adgangskoder.
  
### <a name="enforce-multi-factor-authentication-registration"></a>Gennemtving registrering for multifaktorgodkendelse

Sørg for, at dine brugere opdaterer deres kontakt- og sikkerhedsoplysninger, f.eks. en alternativ mailadresse, telefonnummer eller en enhed, der er registreret til pushmeddelelser, så de kan reagere på sikkerhedsmæssige udfordringer og få besked om sikkerhedshændelser. Opdaterede kontakt- og sikkerhedsoplysninger hjælper brugerne med at bekræfte deres identitet, hvis de glemmer deres adgangskode, eller hvis en anden forsøger at overtage deres konto. Det giver også en out of band-meddelelseskanal i tilfælde af sikkerhedshændelser såsom forsøg på at logge på eller ændrede adgangskoder. 
  
Du kan få mere at [vide under Konfigurer multifaktorgodkendelse](../security-and-compliance/set-up-multi-factor-authentication.md).
  
### <a name="enable-risk-based-multi-factor-authentication"></a>Aktivér risikobaseret multifaktorgodkendelse

Risikobaseret multifaktorgodkendelse sikrer, at når vores system registrerer mistænkelig aktivitet, kan det udfordring brugeren for at sikre, at de er den legitime kontoejer. 
  
## <a name="next-steps"></a>Næste trin

Vil du vide mere om administration af adgangskoder? Her er nogle anbefalede læsninger:

- [Glem adgangskoder, slip for adgangskoder](https://www.microsoft.com/security/business/identity-access-management/passwordless-authentication)

- [Vejledning til Microsoft-adgangskode](https://www.microsoft.com/research/wp-content/uploads/2016/06/Microsoft_Password_Guidance-1.pdf)

- [Får man noget ud af stærke webadgangskoder?](https://go.microsoft.com/fwlink/p/?linkid=861008)

- [Adgangskodeporteføljer og Finite-Effort bruger](https://go.microsoft.com/fwlink/p/?linkid=861014)

- [Undgå svage adgangskoder ved at læse brugernes tanker](https://go.microsoft.com/fwlink/p/?linkid=861015)

- [Valg af sikre adgangskoder](https://go.microsoft.com/fwlink/p/?linkid=861016)

- [Tid til at genoverveje obligatorisk ændring af adgangskode](https://go.microsoft.com/fwlink/p/?linkid=861018)

- [Værste adgangskoder i 2015](https://go.microsoft.com/fwlink/p/?linkid=861020)

## <a name="related-content"></a>Relateret indhold

[Nulstil adgangskoder](../add-users/reset-passwords.md) (artikel)\
[Indstil en individuel brugers adgangskode til aldrig at udløbe](../add-users/set-password-to-never-expire.md) (artikel)\
[Lad brugere nulstille deres egne adgangskoder](../add-users/let-users-reset-passwords.md) (artikel)\
[Sende en brugers adgangskode igen – Hjælp til administratorer](../add-users/resend-user-password.md) (artikel)
