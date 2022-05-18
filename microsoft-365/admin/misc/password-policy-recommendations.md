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
description: Gør din organisation mere sikker mod adgangskodeangreb, og forbud mod almindelige adgangskoder, og aktivér risikobaseret multifaktorgodkendelse.
ms.openlocfilehash: 006e537c2e2d77a19b27f1c2d537269d69d07c1e
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65469002"
---
# <a name="password-policy-recommendations-for-microsoft-365-passwords"></a>Anbefalinger til adgangskodepolitik for Microsoft 365 adgangskoder

Som administrator af en organisation er du ansvarlig for at angive adgangskodepolitikken for brugere i din organisation. Angivelse af adgangskodepolitikken kan være kompliceret og forvirrende, og denne artikel indeholder anbefalinger til at gøre din organisation mere sikker mod adgangskodeangreb.

Microsoft-konti kun i skyen har en foruddefineret adgangskodepolitik, der ikke kan ændres. De eneste elementer, du kan ændre, er antallet af dage, indtil en adgangskode udløber, og om adgangskoder overhovedet udløber. 
  
Hvis du vil finde ud af, hvor ofte Microsoft 365 adgangskoder udløber i din organisation, skal du se [Angiv politik for udløb af adgangskode for Microsoft 365](../manage/set-password-expiration-policy.md).

Du kan få flere oplysninger om Microsoft 365 adgangskoder under:

[Nulstil adgangskoder](../add-users/reset-passwords.md) (artikel)

[Angiv en individuel brugers adgangskode til aldrig at udløbe](../add-users/set-password-to-never-expire.md) (artikel)

[Lad brugerne nulstille deres egne adgangskoder](../add-users/let-users-reset-passwords.md) (artikel)

[Send en brugers adgangskode igen – Hjælp til administratorer](../add-users/resend-user-password.md) (artikel)
  
## <a name="understanding-password-recommendations"></a>Om anbefalinger til adgangskoder

God praksis for adgangskoder kan opdeles i nogle få brede kategorier:
  
- **Modstand mod almindelige angreb** Dette omfatter valget af, hvor brugerne indtaster adgangskoder (kendte og pålidelige enheder med god malwareregistrering, validerede websteder) og valget af, hvilken adgangskode de skal vælge (længde og unikhed).

- **Indeholder vellykkede angreb** At indeholde vellykkede hackerangreb handler om at begrænse eksponeringen for en bestemt tjeneste eller forhindre, at skaden helt forhindres, hvis en brugers adgangskode bliver stjålet. For eksempel at sikre, at et brud på dine legitimationsoplysninger til sociale netværk ikke gør din bankkonto sårbar eller ikke lader en dårligt overvåget konto acceptere nulstillingslinks for en vigtig konto.

- **Forståelse af den menneskelige natur** Mange gyldige praksisser for adgangskoder mislykkes i forhold til naturlige menneskelige adfærd. Det er vigtigt at forstå den menneskelige natur, fordi forskning viser, at næsten alle de regler, du pålægger dine brugere, vil resultere i en svækkelse af adgangskodekvaliteten. Krav til længde, særlige tegnkrav og krav til ændring af adgangskode resulterer alle i normalisering af adgangskoder, hvilket gør det nemmere for hackere at gætte eller knække adgangskoder.

## <a name="password-guidelines-for-administrators"></a>Retningslinjer for adgangskoder for administratorer

Det primære mål med et mere sikkert adgangskodesystem er mangfoldighed af adgangskoder. Din adgangskodepolitik skal indeholde mange forskellige adgangskoder, som er svære at gætte. Her er nogle anbefalinger til, hvordan du holder din organisation så sikker som muligt.
  
- Bevar et minimumlængdekrav på 8 tegn

- Kræver ikke krav til tegnkomposition. F.eks. \*&amp;(^%$

- Kræver ikke obligatorisk periodisk nulstilling af adgangskode for brugerkonti

- Forbud mod almindelige adgangskoder for at holde de mest sårbare adgangskoder ude af systemet

- Oplær dine brugere i ikke at genbruge deres organisationsadgangskoder til ikke-arbejdsrelaterede formål

- Gennemtving registrering for [multifaktorgodkendelse](../security-and-compliance/set-up-multi-factor-authentication.md)

- Aktivér risikobaserede udfordringer med multifaktorgodkendelse

### <a name="password-guidance-for-your-users"></a>Vejledning til adgangskoder til dine brugere

Her er nogle vejledninger til adgangskoder for brugere i din organisation. Sørg for at fortælle brugerne om disse anbefalinger og gennemtvinge de anbefalede adgangskodepolitikker på organisationsniveau.
  
- Brug ikke en adgangskode, der er den samme eller ligner den, du bruger på andre websteder

- Brug ikke et enkelt ord, f.eks. **adgangskode**, eller et almindeligt brugt udtryk som **f.eks.**

- Gør det svært at gætte adgangskoder, selv af dem, der ved meget om dig, f.eks. dine venners og venners fødselsdage, dine yndlingsbands og sætninger, du kan lide at bruge

## <a name="some-common-approaches-and-their-negative-impacts"></a>Nogle almindelige tilgange og deres negative virkninger

Dette er nogle af de mest anvendte praksisser for administration af adgangskoder, men undersøgelser advarer os om de negative virkninger af dem.
  
### <a name="password-expiration-requirements-for-users"></a>Krav til udløb af adgangskode for brugere

Kravene til udløb af adgangskoder skader mere end gavn, da disse krav gør, at brugerne vælger forudsigelige adgangskoder, der består af sekventielle ord og tal, der er tæt forbundet med hinanden. I disse tilfælde kan den næste adgangskode forudsiges baseret på den forrige adgangskode. Krav til udløb af adgangskode giver ingen opbevaringsfordele, fordi cyberkriminelle næsten altid bruger legitimationsoplysninger, så snart de kompromitterer dem. Se [Tid til at gentænke obligatoriske adgangskodeændringer](https://go.microsoft.com/fwlink/p/?linkid=861018) for at få flere oplysninger.
  
### <a name="requiring-long-passwords"></a>Kræver lange adgangskoder

Krav til adgangskodens længde (mere end ca. 10 tegn) kan resultere i en forudsigelig og uønsket brugeradfærd. Brugere, der skal have en adgangskode på 16 tegn, kan f.eks. vælge gentagne mønstre, f.eks. **firefourfour** eller **passwordpassword** , der opfylder kravet om tegnlængde, men som ikke er svære at gætte. Derudover øger længdekrav chancen for, at brugerne vil anvende andre usikre fremgangsmåder, f.eks. at skrive deres adgangskoder ned, genbruge dem eller gemme dem ukrypteret i deres dokumenter. Hvis du vil opfordre brugerne til at tænke på en unik adgangskode, anbefaler vi, at du beholder et rimeligt minimumlængdekrav på 8 tegn.
  
### <a name="requiring-the-use-of-multiple-character-sets"></a>Krav om brug af flere tegnsæt

Krav til adgangskodekompleksitet reducerer den centrale plads og får brugerne til at handle på forudsigelige måder og gøre mere skade end gavn. De fleste systemer gennemtvinger et vist niveau af kompleksitetskrav til adgangskoder. Adgangskoder skal f.eks. bruge tegn fra alle tre af følgende kategorier:
  
- store bogstaver

- små bogstaver

- ikke-alfanumeriske tegn

De fleste bruger lignende mønstre, f.eks. et stort bogstav i første position, et symbol i det sidste og et tal i de sidste 2. Cyberkriminelle ved dette, så de kører deres ordbogsangreb ved hjælp af de mest almindelige erstatninger, "$" for "s", "@" for "a", "1" for "l". Det har en negativ effekt at tvinge brugerne til at vælge en kombination af øvre, nederste, cifre og specialtegn. Nogle kompleksitetskrav forhindrer endda brugerne i at bruge sikre og mindeværdige adgangskoder og tvinger dem til at komme med mindre sikre og mindre mindeværdige adgangskoder.
  
## <a name="successful-patterns"></a>Vellykkede mønstre

I modsætning hertil er her nogle anbefalinger til at fremme mangfoldighed af adgangskoder.
  
### <a name="ban-common-passwords"></a>Forbud mod almindelige adgangskoder

Det vigtigste krav til adgangskoder, som du skal stille til dine brugere, når du opretter adgangskoder, er at forbyde brugen af almindelige adgangskoder for at reducere din organisations følsomhed over for brute force-adgangskodeangreb. Almindelige brugeradgangskoder omfatter: **abcdefg**, **adgangskode**, **abe**.
  
### <a name="educate-users-to-not-reuse-organization-passwords-anywhere-else"></a>Oplær brugerne i ikke at genbruge organisationsadgangskoder andre steder

En af de vigtigste meddelelser, du kan få adgang til for brugerne i din organisation, er ikke at genbruge deres organisationsadgangskode andre steder. Brugen af organisationsadgangskoder på eksterne websteder øger i høj grad sandsynligheden for, at cyberkriminelle kompromitterer disse adgangskoder.
  
### <a name="enforce-multi-factor-authentication-registration"></a>Gennemtving registrering af multifaktorgodkendelse

Sørg for, at brugerne opdaterer kontakt- og sikkerhedsoplysninger, f.eks. en alternativ mailadresse, et telefonnummer eller en enhed, der er registreret til pushmeddelelser, så de kan reagere på sikkerhedsudfordringer og få besked om sikkerhedshændelser. Opdaterede kontakt- og sikkerhedsoplysninger hjælper brugerne med at bekræfte deres identitet, hvis de glemmer deres adgangskode, eller hvis en anden forsøger at overtage deres konto. Den indeholder også en kanal, hvor der ikke er flere båndmeddelelser, hvis der er sikkerhedshændelser, f.eks. logonforsøg eller ændrede adgangskoder. 
  
Du kan få mere at vide under [Konfigurer multifaktorgodkendelse](../security-and-compliance/set-up-multi-factor-authentication.md).
  
### <a name="enable-risk-based-multi-factor-authentication"></a>Aktivér risikobaseret multifaktorgodkendelse

Risikobaseret multifaktorgodkendelse sikrer, at når vores system registrerer mistænkelig aktivitet, kan det udfordre brugeren for at sikre, at de er den legitime kontoejer. 
  
## <a name="next-steps"></a>Næste trin

Vil du vide mere om administration af adgangskoder? Her er nogle anbefalede læsning:

- [Glem adgangskoder, gå uden adgangskode](https://www.microsoft.com/security/business/identity-access-management/passwordless-authentication)

- [Vejledning til Microsoft-adgangskode](https://www.microsoft.com/research/wp-content/uploads/2016/06/Microsoft_Password_Guidance-1.pdf)

- [Udfører stærke webadgangskoder noget?](https://go.microsoft.com/fwlink/p/?linkid=861008)

- [Oversigter over adgangskoder og den Finite-Effort bruger](https://go.microsoft.com/fwlink/p/?linkid=861014)

- [Forhindrer svage adgangskoder ved at læse brugernes sind](https://go.microsoft.com/fwlink/p/?linkid=861015)

- [Valg af sikre adgangskoder](https://go.microsoft.com/fwlink/p/?linkid=861016)

- [Tid til at gentænke obligatoriske adgangskodeændringer](https://go.microsoft.com/fwlink/p/?linkid=861018)

- [Værste adgangskoder i 2015](https://go.microsoft.com/fwlink/p/?linkid=861020)

## <a name="related-content"></a>Relateret indhold

[Nulstil adgangskoder](../add-users/reset-passwords.md) (artikel)\
[Angiv en individuel brugers adgangskode til aldrig at udløbe](../add-users/set-password-to-never-expire.md) (artikel)\
[Lad brugerne nulstille deres egne adgangskoder](../add-users/let-users-reset-passwords.md) (artikel)\
[Send en brugers adgangskode igen – Hjælp til administratorer](../add-users/resend-user-password.md) (artikel)
