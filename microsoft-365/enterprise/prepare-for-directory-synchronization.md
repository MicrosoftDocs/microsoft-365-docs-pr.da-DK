---
title: Forbered katalogsynkronisering til Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Beskriver, hvordan du forbereder klargøring af brugere til Microsoft 365 ved hjælp af katalogsynkronisering og de langsigtede fordele ved at bruge denne metode.
ms.openlocfilehash: 03182d4cb0e9ed1da2687ab23ffae11369f3765a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090767"
---
# <a name="prepare-for-directory-synchronization-to-microsoft-365"></a>Forbered katalogsynkronisering til Microsoft 365

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Hvis du har valgt hybrididentitetsmodellen og konfigureret beskyttelse af administratorkonti i [trin 2](protect-your-global-administrator-accounts.md) og brugerkonti i [trin 3](microsoft-365-secure-sign-in.md) i denne løsning, er din næste opgave at installere katalogsynkronisering. Fordelene ved katalogsynkronisering for din organisation omfatter:

- Reduktion af administrative programmer i din organisation
- Du kan eventuelt aktivere et enkeltlogon-scenarie
- Automatisering af kontoændringer i Microsoft 365

Du kan få flere oplysninger om fordelene ved at bruge katalogsynkronisering under [hybrididentitet med Azure Active Directory (Azure AD)](/azure/active-directory/hybrid/whatis-hybrid-identity).

Katalogsynkronisering kræver dog planlægning og forberedelse for at sikre, at din Active Directory-domæneservices (AD DS) synkroniseres med Azure AD-lejeren for dit Microsoft 365 abonnement med et minimum af fejl.

Følg disse trin for at få de bedste resultater.

> [!NOTE]
> Ikke-ASCII-tegn synkroniseres ikke for nogen attributter på AD DS-brugerkontoen.

## <a name="ad-ds-preparation"></a>AD DS-forberedelse

Hvis du vil sikre en problemfri overgang til Microsoft 365 ved hjælp af synkronisering, skal du forberede AD DS-området, før du begynder at installere Microsoft 365 katalogsynkronisering.
  
Klargøring af mapper skal fokusere på følgende opgaver:

- Fjern dubletattributterne **proxyAddress** og **userPrincipalName** .
- Opdater tomme og ugyldige attributter **for userPrincipalName** med gyldige attributter **for userPrincipalName** .
- Fjern ugyldige og tvivlsomme tegn i attributterne **givenName**, efternavn ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname** og **userPrincipalName** . Du kan finde oplysninger om, hvordan du forbereder attributter, under [Liste over attributter, der synkroniseres af Azure Active Directory synkroniseringsværktøj.](https://go.microsoft.com/fwlink/p/?LinkId=396719)

    > [!NOTE]
    > Dette er de samme attributter, som Azure AD Forbind synkroniserer. 
  
## <a name="multi-forest-deployment-considerations"></a>Overvejelser i forbindelse med udrulning i flere områder

Brug en [brugerdefineret installation af Azure AD](/azure/active-directory/hybrid/how-to-connect-install-custom) Forbind til flere skove og SSO-indstillinger.
  
Hvis din organisation har flere skove til godkendelse (logonskove), anbefaler vi på det kraftigste følgende:
  
- **Overvej at konsolidere dine skove.** Generelt kræves der flere udgifter for at vedligeholde flere skove. Medmindre din organisation har sikkerhedsbegrænsninger, der dikterer behovet for separate skove, kan du overveje at forenkle dit lokale miljø.
- **Brug kun i dit primære logonområde.** Overvej kun at udrulle Microsoft 365 i det primære logonområde til den indledende udrulning af Microsoft 365. 

Hvis du ikke kan konsolidere AD DS-installationen med flere områder eller bruger andre katalogtjenester til at administrere identiteter, kan du muligvis synkronisere disse med hjælp fra Microsoft eller en partner.
  
Se [Topologier for Azure AD-Forbind for](/azure/active-directory/hybrid/plan-connect-topologies) at få flere oplysninger.
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a>Funktioner, der er afhængige af katalogsynkronisering
  
Katalogsynkronisering er påkrævet for følgende funktioner og funktioner:
  
- Azure AD Seamless Single Sign-On (SSO)
- Skype sameksistens
- Exchange hybridinstallation, herunder:
  - Fuldt delt global adresseliste mellem dit lokale Exchange miljø og Microsoft 365.
  - Synkroniserer GAL-oplysninger fra forskellige mailsystemer.
  - Muligheden for at føje brugere til og fjerne brugere fra Microsoft 365 servicetilbud. Dette kræver følgende:
  - Tovejssynkronisering skal konfigureres under konfiguration af katalogsynkronisering. Værktøjer til katalogsynkronisering skriver som standard kun mappeoplysninger til cloudmiljøet. Når du konfigurerer tovejssynkronisering, aktiverer du tilbageskrivningsfunktioner, så et begrænset antal objektattributter kopieres fra skyen og derefter skriver dem tilbage til din lokale AD DS. Tilbageskrivning kaldes også Exchange hybridtilstand. 
  - En Exchange hybridinstallation i det lokale miljø
  - Muligheden for at flytte nogle brugerpostkasser til Microsoft 365 samtidig med, at andre brugerpostkasser bevares i det lokale miljø.
  - Pengeskab afsendere og blokerede afsendere i det lokale miljø replikeres til Microsoft 365.
  - Grundlæggende delegering og send på vegne af mailfunktionalitet.
  - Du har en integreret løsning til chipkort eller multifaktorgodkendelse i det lokale miljø.
- Synkronisering af fotos, miniaturer, mødelokaler og sikkerhedsgrupper

## <a name="1-directory-cleanup-tasks"></a>1. Mappeoprydningsopgaver

Før du synkroniserer din AD DS med din Azure AD-lejer, skal du rydde op i din AD DS.

> [!IMPORTANT]
> Hvis du ikke udfører AD DS-oprydning, før du synkroniserer, kan det have en betydelig negativ indvirkning på udrulningsprocessen. Det kan tage dage eller endda uger at gennemgå cyklussen for katalogsynkronisering, identificere fejl og gensynkronisering.

I din AD DS skal du udføre følgende oprydningsopgaver for hver brugerkonto, der tildeles en Microsoft 365 licens:

1. Kontrollér en gyldig og entydig mailadresse i attributten **proxyAddresses** .

2. Fjern alle dubletværdier i attributten **proxyAddresses** .

3. Hvis det er muligt, skal du sikre en gyldig og entydig værdi for attributten **userPrincipalName** i brugerens **brugerobjekt** . Du opnår den bedste synkroniseringsoplevelse ved at sikre, at AD DS-UPN'et svarer til Azure AD-UPN'et. Hvis en bruger ikke har en værdi for attributten **userPrincipalName** , skal **brugerobjektet** indeholde en gyldig og entydig værdi for attributten **sAMAccountName** . Fjern alle dubletværdier i attributten **userPrincipalName** .

4. Sørg for, at oplysningerne i følgende attributter for AD DS-brugerkontoen er korrekte for at få optimal brug af den globale adresseliste:

   - givenName
   - Efternavn
   - Displayname
   - Stilling
   - Institut
   - Office
   - Office Telefon
   - Mobil Telefon
   - Faxnummer
   - Gadenavn
   - Byen
   - Stat eller provins
   - Postnummer
   - Land eller område

## <a name="2-directory-object-and-attribute-preparation"></a>2. Mappeobjekt og attributforberedelse

Vellykket katalogsynkronisering mellem AD DS og Microsoft 365 kræver, at AD DS-attributterne er forberedt korrekt. Du skal f.eks. sikre, at bestemte tegn ikke bruges i visse attributter, der synkroniseres med det Microsoft 365 miljø. Uventede tegn medfører ikke, at katalogsynkronisering mislykkes, men returnerer muligvis en advarsel. Ugyldige tegn medfører, at katalogsynkronisering mislykkes.

Katalogsynkronisering mislykkes også, hvis nogle af dine AD DS-brugere har en eller flere dubletattributter. Hver bruger skal have entydige attributter.

De attributter, du skal bruge for at forberede, vises her:

- **Displayname**

  - Hvis attributten findes i brugerobjektet, synkroniseres den med Microsoft 365.
  - Hvis denne attribut findes i brugerobjektet, skal der være en værdi for det. Attributten må derfor ikke være tom.
  - Maksimalt antal tegn: 256

- **givenName**

  - Hvis attributten findes i brugerobjektet, synkroniseres den med Microsoft 365, men Microsoft 365 ikke kræver eller bruger den.
  - Maksimalt antal tegn: 64

- **Mail**

  - Attributværdien skal være entydig i mappen.

    > [!NOTE]
    > Hvis der er dubletværdier, synkroniseres den første bruger med værdien. Efterfølgende brugere vises ikke i Microsoft 365. Du skal enten ændre værdien i Microsoft 365 eller ændre begge værdierne i AD DS, for at begge brugere kan blive vist i Microsoft 365.

- **mailNickname** (Exchange alias)

  - Attributværdien må ikke begynde med et punktum (.).
  - Attributværdien skal være entydig i mappen.

    > [!NOTE]
    > Understregningstegn ("_") i det synkroniserede navn angiver, at den oprindelige værdi for denne attribut indeholder ugyldige tegn. Du kan få flere oplysninger om denne attribut [under Exchange aliasattribut](/powershell/module/exchange/set-mailbox).
    >

- **proxyAddresses**

  - Attribut med flere værdier
  - Maksimalt antal tegn pr. værdi: 256
  - Attributværdien må ikke indeholde et mellemrum.
  - Attributværdien skal være entydig i mappen.
  - Ugyldige tegn: \< \> ( ) ; , [ ] "
  - Bogstaver med diakritiske tegn, f.eks. umlauts, accenter og tildes, er ugyldige tegn.

    Bemærk, at de ugyldige tegn gælder for de tegn, der følger efter typeafgrænseren og ":", så SMTP:User@contso.com er tilladt, men det er SMTP:user:M@contoso.com ikke.

    > [!IMPORTANT]
    > Alle SMTP-adresser (Simple Mail Transport Protocol) skal overholde standarderne for mailbeskeder. Fjern dublerede eller uønskede adresser, hvis de findes.

- **sAMAccountName**

  - Maksimalt antal tegn: 20
  - Attributværdien skal være entydig i mappen.
  - Ugyldige tegn: [ \ " | , / : \< \> + = ; ? \* ']
  - Hvis en bruger har en ugyldig **sAMAccountName-attribut**, men har en gyldig **userPrincipalName-attribut**, oprettes brugerkontoen i Microsoft 365.
  - Hvis både **sAMAccountName** og **userPrincipalName** er ugyldige, skal attributten AD DS **userPrincipalName** opdateres.

- **sn** (efternavn)

  - Hvis attributten findes i brugerobjektet, synkroniseres den med Microsoft 365, men Microsoft 365 ikke kræver eller bruger den.

- **Targetaddress**

    Det er påkrævet, at attributten **targetAddress** (f.eks. SMTP:tom@contoso.com), der er udfyldt for brugeren, skal vises i Microsoft 365 GAL. I overførselsscenarier for beskeder fra tredjepart kræver dette den Microsoft 365 skemaudvidelse for AD DS. Den Microsoft 365 skemaudvidelse vil også tilføje andre nyttige attributter til at administrere Microsoft 365 objekter, der udfyldes ved hjælp af et værktøj til katalogsynkronisering fra AD DS. Attributten **msExchHideFromAddressLists** til administration af skjulte postkasser eller distributionsgrupper vil f.eks. blive tilføjet.

  - Maksimalt antal tegn: 256
  - Attributværdien må ikke indeholde et mellemrum.
  - Attributværdien skal være entydig i mappen.
  - Ugyldige tegn: \ \< \> ( ) ; , [ ] "
  - Alle SMTP-adresser (Simple Mail Transport Protocol) skal overholde standarderne for mailbeskeder.

- **userPrincipalName**

  - Attributten **userPrincipalName** skal være i internetlogonformatet, hvor brugernavnet efterfølges af at-tegnet (@) og et domænenavn: f.eks. user@contoso.com. Alle SMTP-adresser (Simple Mail Transport Protocol) skal overholde standarderne for mailbeskeder.
  - Det maksimale antal tegn for attributten **userPrincipalName** er 113. Et bestemt antal tegn er tilladt før og efter at-tegnet (@) på følgende måde:
  - Det maksimale antal tegn for brugernavnet foran tegnet (@): 64
  - Det maksimale antal tegn for domænenavnet efter at-tegnet (@): 48
  - Ugyldige tegn: \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "
  - Tilladte tegn: A – Z, a - z, 0 - 9, ' . - _ ! # ^ ~
  - Bogstaver med diakritiske tegn, f.eks. umlauts, accenter og tildes, er ugyldige tegn.
  - Tegnet @ er obligatorisk i hver **userPrincipalName-værdi** .
  - Tegnet @ må ikke være det første tegn i hver **userPrincipalName-værdi** .
  - Brugernavnet må ikke slutte med et punktum (.), et og-tegn (&amp;), et mellemrum eller et at-tegn (@).
  - Brugernavnet må ikke indeholde mellemrum.
  - Der skal bruges domæner, der kan distribueres. Lokale eller interne domæner kan f.eks. ikke bruges.
  - Unicode konverteres til understregningstegn.
  - **userPrincipalName** må ikke indeholde dubletværdier i mappen.

## <a name="3-prepare-the-userprincipalname-attribute"></a>3. Forbered attributten userPrincipalName

Active Directory er designet til at give slutbrugerne i din organisation mulighed for at logge på din mappe ved hjælp af enten **sAMAccountName** eller **userPrincipalName**. På samme måde kan slutbrugerne logge på Microsoft 365 ved hjælp af brugerens hovednavn (UPN) på deres arbejds- eller skolekonto. Katalogsynkronisering forsøger at oprette nye brugere i Azure Active Directory ved hjælp af det samme UPN, som findes i dit AD DS. UPN er formateret som en mailadresse.

I Microsoft 365 er UPN den standardattribut, der bruges til at generere mailadressen. Det er nemt at få **userPrincipalName** (i AD DS og i Azure AD), og den primære mailadresse i **proxyAddresses** er angivet til forskellige værdier. Når de er angivet til forskellige værdier, kan der være forvirring for administratorer og slutbrugere.

Det er bedst at justere disse attributter for at reducere forvirringen. Hvis du vil opfylde kravene til enkeltlogon med Active Directory Federation Services (AD FS) 2.0, skal du sikre, at UPN'erne i Azure Active Directory og din AD DS stemmer overens og bruger et gyldigt domænenavnområde.

## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a>4. Føj et alternativt UPN-suffiks til AD DS

Du skal muligvis tilføje et alternativt UPN-suffiks for at knytte brugerens legitimationsoplysninger til det Microsoft 365 miljø. Et UPN-suffiks er den del af et UPN til højre for tegnet @ . UPN'er, der bruges til enkeltlogon, kan indeholde bogstaver, tal, punktummer, tankestreger og understregningstegn, men ingen andre tegntyper.

Du kan finde flere oplysninger om, hvordan du føjer et alternativt UPN-suffiks til Active Directory, under [Forbered katalogsynkronisering](https://go.microsoft.com/fwlink/p/?LinkId=525430).

## <a name="5-match-the-ad-ds-upn-with-the-microsoft-365-upn"></a>5. Match AD DS-UPN med det Microsoft 365 UPN

Hvis du allerede har konfigureret katalogsynkronisering, stemmer brugerens UPN for Microsoft 365 muligvis ikke overens med brugerens AD DS-UPN, der er defineret i din AD DS. Dette kan ske, når en bruger fik tildelt en licens, før domænet blev bekræftet. Du kan løse problemet ved [at bruge PowerShell til at rette dublerede UPN'er](https://go.microsoft.com/fwlink/p/?LinkId=396730) for at opdatere brugerens UPN for at sikre, at det Microsoft 365 UPN stemmer overens med virksomhedens brugernavn og domæne. Hvis du opdaterer UPN'et i AD DS og gerne vil synkronisere med den Azure Active Directory identitet, skal du fjerne brugerens licens i Microsoft 365, før du foretager ændringerne i AD DS.

Se også [Sådan forbereder du et domæne, der ikke kan sendes fra en rute (f.eks. et .lokalt domæne), til katalogsynkronisering](prepare-a-non-routable-domain-for-directory-synchronization.md).

## <a name="next-steps"></a>Næste trin

Når du har udført 1 til 5 ovenfor, skal du se [Konfigurer katalogsynkronisering](set-up-directory-synchronization.md).
