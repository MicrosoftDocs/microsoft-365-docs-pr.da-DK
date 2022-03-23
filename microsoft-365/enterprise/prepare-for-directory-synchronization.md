---
title: Forbered katalogsynkronisering på Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Beskriver, hvordan du forbereder at klargøre brugere til Microsoft 365 ved hjælp af katalogsynkronisering og de langsigtede fordele ved at bruge denne metode.
ms.openlocfilehash: 5a8914091eb8df62ba71c8ddff35c3fb355fa031
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63590388"
---
# <a name="prepare-for-directory-synchronization-to-microsoft-365"></a>Forbered katalogsynkronisering på Microsoft 365

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Hvis du har valgt hybrididentitetsmodellen og konfigureret beskyttelse af administratorkonti i trin [2](protect-your-global-administrator-accounts.md) og brugerkonti i trin [3](microsoft-365-secure-sign-in.md) i denne løsning, er den næste opgave at installere katalogsynkronisering. Fordelene ved katalogsynkronisering for din organisation omfatter:

- Reduktion af administrative programmer i organisationen
- Du kan også aktivere enkelt-logon-scenarie
- Automatisering af kontoændringer i Microsoft 365

Du kan finde flere oplysninger om fordelene ved at bruge katalogsynkronisering [i hybrididentitet Azure Active Directory (Azure AD)](/azure/active-directory/hybrid/whatis-hybrid-identity).

Katalogsynkronisering kræver dog planlægning og forberedelse for at sikre, at din Active Directory-domæneservices (AD DS) synkroniseres med Azure AD-lejeren for dit Microsoft 365-abonnement med et minimum af fejl.

Følg disse trin for at få de bedste resultater.

> [!NOTE]
> Ikke-ASCII-tegn synkroniseres ikke for nogen attributter AD DS brugerkontoen.

## <a name="ad-ds-preparation"></a>AD DS forberedelse

For at sikre problemfri overgang til Microsoft 365 ved hjælp af synkronisering skal du forberede din AD DS-skov, før du starter din Microsoft 365-katalogsynkroniseringsinstallation.
  
Din katalogforberedelse bør fokusere på følgende opgaver:

- Fjern **dublerede proxyAddress** - **og userPrincipalName-attributter** .
- Opdater tomme og ugyldige **userPrincipalName-attributter** med gyldige **userPrincipalName-attributter** .
- Fjern ugyldige og tvivlsomme tegn i attributterne **givenName**, efternavn ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname** og **userPrincipalName** . Hvis du vil have mere at vide om forberedelse af [attributter, skal du se Liste over attributter, der synkroniseres Azure Active Directory synkroniseringsværktøjet](https://go.microsoft.com/fwlink/p/?LinkId=396719).

    > [!NOTE]
    > Dette er de samme attributter, som Azure AD Forbind synkroniserer. 
  
## <a name="multi-forest-deployment-considerations"></a>Overvejelser i forbindelse med implementering af flere skove

Til flere områder og SSO-indstillinger skal du bruge en [brugerdefineret installation af Azure AD Forbind](/azure/active-directory/hybrid/how-to-connect-install-custom).
  
Hvis din organisation har flere skove til godkendelse (logonskove), anbefaler vi stærkt følgende:
  
- **Overvej at konsolidere dine skove.** Generelt kræves højere omkostninger til at vedligeholde flere skove. Medmindre din organisation har sikkerhedsbegrænsninger, der dikterer behovet for separate skove, bør du overveje at forenkle dit lokale miljø.
- **Brug kun i din primære logonskov.** Overvej kun Microsoft 365 i din primære logonskov til din indledende udrulning af Microsoft 365. 

Hvis du ikke kan konsolidere din installation af AD DS med flere skove eller bruger andre katalogtjenester til at administrere identiteter, kan du muligvis synkronisere disse ved hjælp af Microsoft eller en partner.
  
Se [Topologier til Azure AD-Forbind](/azure/active-directory/hybrid/plan-connect-topologies) for at få flere oplysninger.
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a>Funktioner, der er afhængige af katalogsynkronisering
  
Katalogsynkronisering er påkrævet for følgende funktioner:
  
- Azure AD Seamless Single Sign-On (SSO)
- Skype sameksistens
- Exchange hybridinstallation, herunder:
  - Fuldt delt global adresseliste (GAL) mellem dit lokale miljø Exchange og Microsoft 365.
  - Synkronisering af GAL-oplysninger fra forskellige mailsystemer.
  - Muligheden for at føje brugere til og fjerne brugere fra Microsoft 365 servicetilbud. Dette kræver følgende:
  - Tovejssynkronisering skal konfigureres under konfiguration af katalogsynkronisering. Som standard skriver værktøjer til katalogsynkronisering kun oplysninger til skyen. Når du konfigurerer tovejssynkronisering, aktiverer du funktionen tilbageskrivning, så et begrænset antal objektattributter kopieres fra skyen og derefter skriver dem tilbage til din lokale AD DS. Tilbageskrivning kaldes også for Exchange hybridtilstand. 
  - En lokal Exchange hybridinstallation
  - Muligheden for at flytte nogle brugerpostkasser til Microsoft 365 mens andre brugerpostkasser bevares lokalt.
  - Pengeskab lokale afsendere og blokerede afsendere replikeres til Microsoft 365.
  - Grundlæggende uddelegering og mailfunktionen send på vegne af.
  - Du har et integreret lokalt chipkort eller en løsning til multifaktorgodkendelse.
- Synkronisering af fotos, miniaturer, mødelokaler og sikkerhedsgrupper

## <a name="1-directory-cleanup-tasks"></a>1. Katalogoprydningsopgaver

Før du synkroniserer AD DS med din Azure AD-lejer, skal du rydde op i AD DS.

> [!IMPORTANT]
> Hvis du ikke udfører en AD DS før du synkroniserer, kan det have en betydelig negativ indvirkning på installationsprocessen. Det kan tage dage eller endda uger at gå gennem cyklussen for katalogsynkronisering, identificere fejl og gensynkronisering.

I din AD DS skal du udføre følgende oprydningsopgaver for hver brugerkonto, der tildeles en Microsoft 365 licens:

1. Sørg for en gyldig og entydig mailadresse i **proxyAddresses-attributten** .

2. Fjern eventuelle dublerede værdier i **proxyAddresses-attributten** .

3. Hvis det er muligt, skal du sikre dig en gyldig og entydig værdi for **userPrincipalName-attributten** i **brugerens brugerobjekt** . Du får den bedste synkroniseringsoplevelse ved at sikre, AD DS UPN svarer til Azure AD UPN. Hvis en bruger ikke har en værdi for **userPrincipalName-attributten**, skal brugerobjektet indeholde en gyldig og entydig værdi for **sAMAccountName-attributten**. Fjern eventuelle dublerede værdier i **userPrincipalName-attributten** .

4. For optimal brug af den globale adresseliste (GAL) skal du sikre dig, at oplysningerne i de følgende attributter for AD DS er korrekte:

   - givenName
   - efternavn
   - displayName
   - Stilling
   - Afdeling
   - Office
   - Office Telefon
   - Mobildata Telefon
   - Faxnummer
   - Adresse
   - By
   - Stat eller provins
   - Postnummer
   - Land eller område

## <a name="2-directory-object-and-attribute-preparation"></a>2. Forberedelse af katalogobjekt og attribut

Vellykket katalogsynkronisering mellem dine AD DS og Microsoft 365 kræver, at dine AD DS attributter er ordentligt forberedt. Du skal f.eks. sikre dig, at bestemte tegn ikke bruges i visse attributter, der synkroniseres med Microsoft 365 miljøet. Uventede tegn får ikke katalogsynkronisering til at mislykkes, men returnerer muligvis en advarsel. Ugyldige tegn medfører, at katalogsynkronisering mislykkes.

Katalogsynkronisering vil heller ikke mislykkes, hvis nogle AD DS brugere har en eller flere duplikerede attributter. Hver bruger skal have entydige attributter.

De attributter, du skal forberede, vises her:

- **displayName**

  - Hvis attributten findes i brugerobjektet, synkroniseres den med Microsoft 365.
  - Hvis denne attribut findes i brugerobjektet, skal der være en værdi for den. Det vil sige, at attributten ikke må være tom.
  - Maksimale antal tegn: 256

- **givenName**

  - Hvis attributten findes i brugerobjektet, synkroniseres den med Microsoft 365, men Microsoft 365 kræver den eller bruger den ikke.
  - Maksimale antal tegn: 64

- **mail**

  - Attributværdien skal være entydig i kataloget.

    > [!NOTE]
    > Hvis der er dublerede værdier, synkroniseres den første bruger med værdien. Efterfølgende brugere vises ikke i Microsoft 365. Du skal enten ændre værdien i Microsoft 365 eller ændre begge værdier i AD DS for at begge brugere kan vises i Microsoft 365.

- **mailNickname** (Exchange alias)

  - Attributværdien må ikke starte med et punktum (.).
  - Attributværdien skal være entydig i kataloget.

    > [!NOTE]
    > Understregningstegn ("_") i det synkroniserede navn angiver, at den oprindelige værdi for denne attribut indeholder ugyldige tegn. Du kan finde flere oplysninger om denne attribut Exchange [aliasattribut](/powershell/module/exchange/set-mailbox).
    >

- **proxyAddresses**

  - Attribut med flere værdier
  - Maksimale antal tegn pr. værdi: 256
  - Attributværdien må ikke indeholde et mellemrum.
  - Attributværdien skal være entydig i kataloget.
  - Ugyldige tegn: \< \> ( ) ; , [ ] "
  - Bogstaver med diakritiske tegn, f.eks omlyd, accenter og tilder, er ugyldige tegn.

    Bemærk, at de ugyldige tegn gælder for de tegn, der følger typeafgrænseren og ":", så de SMTP:User@contso.com er tilladt, men SMTP:user:M@contoso.com ikke er.

    > [!IMPORTANT]
    > Alle SMTP-adresser skal overholde mailstandarder. Fjern dublerede eller uønskede adresser, hvis de findes.

- **sAMAccountName**

  - Maksimale antal tegn: 20
  - Attributværdien skal være entydig i kataloget.
  - Ugyldige tegn: [ \ " | , / : \< \> + = ; ? \* ']
  - Hvis en bruger har en ugyldig **sAMAccountName-attribut**, men har en gyldig **userPrincipalName-attribut**, oprettes brugerkontoen i Microsoft 365.
  - Hvis både **sAMAccountName** og **userPrincipalName er** ugyldige, skal AD DS **userPrincipalName-attributten** opdateres.

- **sn** (efternavn)

  - Hvis attributten findes i brugerobjektet, synkroniseres den med Microsoft 365, men Microsoft 365 kræver den eller bruger den ikke.

- **targetAddress**

    Det er påkrævet, at **attributten targetAddress** (f.eks SMTP:tom@contoso.com), der er udfyldt for brugeren, skal vises i den Microsoft 365 gal. I tredjeparts scenarier for meddelelsesoverførsel kræver dette Microsoft 365 skemaudvidelsen for AD DS. Skemaudvidelsen Microsoft 365 også andre nyttige attributter til at administrere Microsoft 365 objekter, der er udfyldt ved hjælp af et katalogsynkroniseringsværktøj fra AD DS. Attributten **msExchHideFromAddressLists** til administration af skjulte postkasser eller distributionsgrupper tilføjes f.eks.

  - Maksimale antal tegn: 256
  - Attributværdien må ikke indeholde et mellemrum.
  - Attributværdien skal være entydig i kataloget.
  - Ugyldige tegn: \ \< \> ( ) ; , [ ] "
  - Alle SMTP-adresser skal overholde mailstandarder.

- **userPrincipalName**

  - **userPrincipalName-attributten** skal være i internetformatet, hvor brugernavnet efterfølges af snaf-tegnet (@) og et domænenavn: f.eks. user@contoso.com. Alle SMTP-adresser skal overholde mailstandarder.
  - Det maksimale antal tegn for **userPrincipalName-attributten** er 113. Et bestemt antal tegn er tilladt før og efter snedtegnet (@), som følger:
  - Maksimale antal tegn for brugernavnet, der står foran snædtegnet (@): 64
  - Maksimale antal tegn for domænenavnet efter snr.-tegnet (@): 48
  - Ugyldige tegn: \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "
  - Tilladte tegn: A – Z, a - z, 0 - 9, ' . - _ ! # ^ ~
  - Bogstaver med diakritiske tegn, f.eks omlyd, accenter og tilder, er ugyldige tegn.
  - Tegnet @ er påkrævet i hver **userPrincipalName-værdi** .
  - Tegnet @ må ikke være det første tegn i hver **userPrincipalName-værdi** .
  - Brugernavnet kan ikke slutte med et punktum (.), et og-tegn (&amp;), et mellemrum eller et snogtegn (@).
  - Brugernavnet må ikke indeholde mellemrum.
  - Du skal bruge domæne, der kantribuere. Lokale eller interne domæner kan f.eks. ikke bruges.
  - Unicode konverteres til understregningstegn.
  - **userPrincipalName kan** ikke indeholde dublerede værdier i kataloget.

## <a name="3-prepare-the-userprincipalname-attribute"></a>3. Forbered userPrincipalName-attributten

Active Directory er udviklet til at give slutbrugerne i organisationen mulighed for at logge på dit katalog enten ved hjælp af **sAMAccountName** eller **userPrincipalName**. På samme måde kan slutbrugere logge på Microsoft 365 bruge brugerens hovednavn (UPN) på deres arbejds- eller skolekonto. Katalogsynkronisering forsøger at oprette nye brugere i Azure Active Directory ved hjælp af det samme UPN, der er i din AD DS. UPN formateres som en mailadresse.

I Microsoft 365 er UPN standardattributten, der bruges til at generere mailadressen. Det er nemt at indstille **userPrincipalName** (i AD DS og i Azure AD) og den primære mailadresse i **proxyAddresses** til forskellige værdier. Når de er indstillet til forskellige værdier, kan der være forvirring for administratorer og slutbrugere.

Det er bedst at justere disse attributter for at mindske forvirringen. For at overholde kravene til enkelt logon med Active Directory Federation Services (AD FS) 2.0 skal du sikre dig, at UPN'erne i Azure Active Directory og dit AD DS matcher og bruger et gyldigt domænenavneområde.

## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a>4. Føj et alternativt UPN-suffiks til AD DS

Det kan være nødvendigt at tilføje et alternativt UPN-suffiks for at knytte brugerens firmalegitimationsoplysninger til Microsoft 365 miljø. Et UPN-suffiks er den del af et UPN, der står til højre for tegnet @. UPN'er, der bruges til enkelt sign-on, kan indeholde bogstaver, tal, punktummer, tankestreger og understregningstegn, men ikke andre typer tegn.

Du kan finde flere oplysninger om, hvordan du føjer et alternativt UPN-suffiks til Active Directory i [Forbered katalogsynkronisering](https://go.microsoft.com/fwlink/p/?LinkId=525430).

## <a name="5-match-the-ad-ds-upn-with-the-microsoft-365-upn"></a>5. Match AD DS UPN med Microsoft 365 UPN

Hvis du allerede har konfigureret katalogsynkronisering, stemmer brugerens UPN for Microsoft 365 muligvis ikke overens med brugerens AD DS UPN, som er defineret i din AD DS. Dette kan ske, når en bruger blev tildelt en licens, før domænet blev bekræftet. Det løser du ved at bruge PowerShell til at rette duplikerede [UPN'er](https://go.microsoft.com/fwlink/p/?LinkId=396730) for at opdatere brugerens UPN for at sikre, at Microsoft 365 UPN svarer til virksomhedens brugernavn og domæne. Hvis du opdaterer UPN'et i AD DS og gerne vil have det synkroniseret med Azure Active Directory-identiteten, skal du fjerne brugerens licens i Microsoft 365, før du foretager ændringerne i AD DS.

Se også [Sådan forberedes et domæne, der ikke kan kan maile (f.eks. domænet .local), til katalogsynkronisering](prepare-a-non-routable-domain-for-directory-synchronization.md).

## <a name="next-steps"></a>Næste trin

Når du har udført 1 til 5 ovenfor, skal du se [Konfigurer katalogsynkronisering](set-up-directory-synchronization.md).
