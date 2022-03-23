---
title: Besvare en kompromitteret mailkonto
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.collection:
- o365_security_incident_response
- M365-security-compliance
- m365solution-smb
ms.custom:
- TopSMBIssues
- seo-marvel-apr2020
ms.localizationpriority: high
search.appverid:
- MET150
description: Få mere at vide om, hvordan du genkender og svarer på en kompromitteret mailkonto ved hjælp af værktøjer, der er tilgængelige Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bdce44bc54c71d03e8064fa10187c06237d38b5b
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63589582"
---
# <a name="responding-to-a-compromised-email-account"></a>Besvare en kompromitteret mailkonto

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Oversigt** Få mere at vide om, hvordan du genkender og svarer på en kompromitteret mailkonto i Microsoft 365.

## <a name="what-is-a-compromised-email-account-in-microsoft-365"></a>Hvad er en kompromitteret mailkonto i Microsoft 365?

Adgang til Microsoft 365, data og andre tjenester styres ved hjælp af legitimationsoplysninger, f.eks. et brugernavn og en adgangskode eller en pinkode. Når en anden end den tilsigtede bruger stjæler disse legitimationsoplysninger, anses de stjålne legitimationsoplysninger for at være kompromitteret. Med dem kan hackeren logge på som den oprindelige bruger og udføre handlinger, der fungerer som en person.

Ved hjælp af de stjålne legitimationsoplysninger kan hackeren få adgang til brugerens Microsoft 365 postkasse, SharePoint-mapper eller filer i brugerens OneDrive. En handling, som oftest opleves, er en hacker, der sender mails som den oprindelige bruger til modtagere både i og uden for organisationen. Når hackeren mailer data til eksterne modtagere, kaldes det dataudfyldning.

## <a name="symptoms-of-a-compromised-microsoft-email-account"></a>Symptomer på en kompromitteret Microsoft-mailkonto

Brugere vil muligvis bemærke og rapportere usædvanlig aktivitet i deres Microsoft 365 postkasser. Her er nogle almindelige symptomer:

- Mistænkelig aktivitet, f.eks. manglende eller slettede mails.
- Andre brugere kan modtage mails fra den kompromitterede konto uden den tilsvarende mail, der findes **i** mappen Sendt post for afsenderen.
- Tilstedeværelsen af indbakkeregler, der ikke blev oprettet af den tilsigtede bruger eller administratoren. Disse regler kan automatisk videresende mails til ukendte adresser eller flytte dem til **mapperne** **Noter,** Uønsket mail eller **RSS-abonnementer** .
- Brugerens viste navn kan ændres i den globale adresseliste.
- Brugerens postkasse er blokeret fra at sende mails.
- Mapperne Sendt eller Slettet post i Microsoft Outlook eller Outlook på internettet (tidligere kaldet Outlook Web App) indeholder almindelige hackede kontomeddelelser, f.eks. "Jeg sidder fast i London, send penge".
- Usædvanlige profilændringer, f.eks. navn, telefonnummer eller postnummer, er blevet opdateret.
- Usædvanlige ændringer af legitimationsoplysninger, f.eks. flere ændringer af adgangskode er nødvendige.
- Videresendelse af mail er for nylig blevet tilføjet.
- Der er for nylig blevet tilføjet en usædvanlig signatur, f.eks. en falsk banksignatur eller en signatur, der er din signatur.

Hvis en bruger rapporterer nogen af de ovennævnte symptomer, bør du udføre yderligere undersøgelse. Portalen Microsoft 365 Defender Azure-portalen indeholder værktøjer, der kan hjælpe dig med at undersøge aktiviteten for en brugerkonto, som du tror kan være kompromitteret.

- Samlede overvågningslogfiler på **Microsoft 365 Defender-portalen**: Gennemse alle aktiviteter for den mistænkelige konto ved at filtrere resultaterne for det datointerval, der strækker sig fra umiddelbart før den mistænkelige aktivitet forekom til den aktuelle dato. Filtrer ikke på aktiviteterne under søgningen. Få mere at vide under [Søg i overvågningsloggen i overholdelsescenteret](../../compliance/search-the-audit-log-in-security-and-compliance.md).

- **Azure AD Logonlogfiler og andre risikorapporter i Azure AD-portalen**: Undersøg værdierne i disse kolonner:
  - Gennemse IP-adresse
  - logonplaceringer
  - logontider
  - logon lykkedes eller mislykkedes

## <a name="how-to-secure-and-restore-email-function-to-a-suspected-compromised-microsoft-365-account-and-mailbox"></a>Sådan sikrer og gendanner du mailfunktionen på en mistænkelig kompromitteret Microsoft 365 og postkasse

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=RE2jvOb&AutoPlayVideo=false]

Selv når du har fået adgang til din konto igen, kan hackeren have tilføjet post ind bag døren, der gør det muligt for hackeren at genoptage kontrollen med kontoen.

Du skal gøre alle følgende trin for at få adgang til din konto igen, jo tidligere jo bedre for at sikre, at kantspilleren ikke genoptager kontrollen med din konto. Disse trin hjælper dig med at fjerne alle posterne med bag dørene, som kan være føjet til din konto. Når du har gjort dette, anbefaler vi, at du kører en virusscanning for at sikre, at computeren ikke er kompromitteret.

### <a name="step-1-reset-the-users-password"></a>Trin 1 Nulstil brugerens adgangskode

Følg fremgangsmåderne i Nulstille [en forretningsadgangskode for en person](../../admin/add-users/reset-passwords.md#reset-my-admin-password).

> [!IMPORTANT]
>
> - Du må ikke sende den nye adgangskode til den tilsigtede bruger via mail, da hackeren stadig har adgang til postkassen på nuværende tidspunkt.
>
> - Sørg for, at adgangskoden er stærk, og at den indeholder store og små bogstaver, mindst ét tal og mindst ét specialtegn.
>
> - Genbrug ikke nogen af dine seneste fem adgangskoder. Selvom kravet til adgangskodehistorikken gør det muligt at genbruge en nyere adgangskode, skal du vælge noget, som hackeren ikke kan gætte.
>
> - Hvis din lokale identitet er i organisationsnetværk med Microsoft 365, skal du ændre din adgangskode i det lokale miljø, og du skal derefter give administratoren besked om forliget.
>
> - Sørg for at opdatere appadgangskoder. Appadgangskoder tilbagekaldes ikke automatisk, når en adgangskode til en brugerkonto nulstilles. Brugeren skal slette eksisterende appadgangskoder og oprette nye. Du kan finde en vejledning [i Oprette og slette appadgangskoder fra siden Yderligere sikkerhedsbekræftelse](/azure/active-directory/user-help/multi-factor-authentication-end-user-app-passwords#create-and-delete-app-passwords-from-the-additional-security-verification-page).
>
> - Vi anbefaler kraftigt, at du aktiverer Multi-Factor Authentication (MFA) for at forhindre kompromis, især for konti med administrative rettigheder. Hvis du vil vide mere om multifaktorgodkendelse, skal [du gå til Konfigurer multifaktorgodkendelse](../../admin/security-and-compliance/set-up-multi-factor-authentication.md).

### <a name="step-2-remove-suspicious-email-forwarding-addresses"></a>Trin 2 Fjern mistænkelige videresendelsesadresser til mail

1. I Microsoft 365 Administration på skal <https://admin.microsoft.com>du gå til **Aktive** \> **brugere for brugere**. For at gå direkte til siden **Aktive brugere skal** du bruge <https://admin.microsoft.com/Adminportal/Home#/users>.

2. På siden **Aktive brugere** skal du finde den pågældende brugerkonto og vælge brugeren (række) uden at markere afkrydsningsfeltet.

3. I pop op-dialogboksen med oplysninger, der vises, skal du **vælge fanen** Mail.

4. Hvis værdien i sektionen Videresendelse **af mail** anvendes, skal **du klikke** på **Administrer videresendelse af mail**. I pop **op-pop op-dialogboksen** Administrer videresendelse af mail, der vises, skal du fjerne markeringen i Videresende alle **mails, der** sendes til denne postkasse og derefter klikke **på Gem ændringer**.

### <a name="step-3-disable-any-suspicious-inbox-rules"></a>Trin 3 Deaktiver mistænkelige indbakkeregler

1. Log på brugerens postkasse ved hjælp af Outlook på internettet.

2. Klik på tandhjulsikonet, og klik på **Mail**.

3. Klik **på Regler for indbakke og** oprydning, og gennemse reglerne.

4. Deaktiver eller slet mistænkelige regler.

### <a name="step-4-unblock-the-user-from-sending-mail"></a>Trin 4 Fjern blokeringen af brugeren i at sende mail

Hvis den mistanke om kompromitterede postkasse blev brugt globalt til at sende spammail, er det sandsynligt, at postkassen er blevet blokeret fra at sende mails.

Hvis du vil fjerne blokeringen af en postkasse i at sende mails, skal du følge fremgangsmåden i Fjerne en [bruger fra portalen Begrænsede brugere efter afsendelse af spammail](removing-user-from-restricted-users-portal-after-spam.md).

### <a name="step-5-optional-block-the-user-account-from-signing-in"></a>Trin 5 Valgfrit: Bloker brugerkontoen fra at logge på

> [!IMPORTANT]
> Du kan blokere den mistænkelige kompromitterede konto fra at logge på, indtil du mener, at det er sikkert at genaktivere adgang.

1. I Microsoft 365 Administration på skal <https://admin.microsoft.com>du gå til **Aktive** \> **brugere for brugere**. For at gå direkte til siden **Aktive brugere skal** du bruge <https://admin.microsoft.com/Adminportal/Home#/users>.

2. På siden **Aktive brugere** skal du finde og vælge brugerkontoen, ![klikke på ikonet Mere](../../media/ITPro-EAC-MoreOptionsIcon.png) og derefter **vælge Rediger logonstatus**.

3. I **ruden Bloker logon,** der vises, skal du **vælge Bloker denne bruger fra at logge på** og derefter klikke **på Gem ændringer**.

4. I Exchange Administration (EAC) på skal du <https://admin.exchange.microsoft.com>gå til **Modtageres** \> **postkasser**. For at gå direkte til siden **Postkasser skal** du bruge <https://admin.exchange.microsoft.com/#/mailboxes>.

5. På siden **Postkasser** skal du finde og vælge brugeren. I pop op-vindue med postkasseoplysninger, der åbnes, skal du gøre følgende:
   - I sektionen **Mailapps** skal du vælge **Administrer indstillinger for mailapps**. I pop **op-menuen Administrer indstillinger for mailapps** , der vises, skal du blokere alle tilgængelige indstillinger ved at flytte til/fra-knappen til højre Deaktiver ![.](../../media/scc-toggle-on.png):
     - **Outlook på internettet**
     - **Outlook (MAPI)**
     - **Exchange webtjenester**
     - **Mobil (Exchange ActiveSync)**
     - **IMAP**
     - **POP3**

   Når du er færdig, skal du klikke **på Gem** og derefter klikke på **Luk**.

### <a name="step-6-optional-remove-the-suspected-compromised-account-from-all-administrative-role-groups"></a>Trin 6 Valgfrit: Fjern den mistænkelige kompromitterede konto fra alle administrative rollegrupper

> [!NOTE]
> Medlemskab af administratorgruppen kan gendannes, når kontoen er sikret.

1. I Microsoft 365 Administration på <https://admin.microsoft.com>skal du gøre følgende:
   1. Gå til **Aktive brugere** \> **for brugere**. For at gå direkte til siden **Aktive brugere skal** du bruge <https://admin.microsoft.com/Adminportal/Home#/users>.
   2. På siden **Aktive brugere** skal du finde og vælge brugerkontoen, klikke på ![ikonet Flere](../../media/ITPro-EAC-MoreOptionsIcon.png) og derefter vælge **Administrer roller**.
   3. Fjern eventuelle administrative roller, der er tildelt til kontoen. Klik på Gem ændringer, når du **er færdig**.

2. i Microsoft 365 Defender på skal <https://security.microsoft.com>du gøre følgende:
   1. Gå til **Tilladelser & roller Mail** \> **& samarbejdsroller Roller**\>. For at gå direkte til **siden Tilladelser skal** du bruge <https://security.microsoft.com/emailandcollabpermissions>.
   2. På siden **Tilladelser skal** du vælge hver rollegruppe på listen og se efter brugerkontoen i sektionen Medlemmer i pop  op-dialogboksen med oplysninger, der vises. Hvis rollegruppen indeholder brugerkontoen, skal du gøre følgende:
      1. Klik på **Rediger** i sektionen **Medlemmer**.
      2. Klik på **Rediger i pop op-vindue** med Rediger Vælg **medlemmer**, der vises.
      3. I pop **op-menuen Vælg** medlemmer, der vises, skal du klikke på **Fjern**.
      4. Vælg brugerkontoen i pop op-pop-op-dialogboksen, og klik derefter på **Fjern**.

         Når du er færdig, skal du klikke **på** **Udført,** Gem og derefter **På Luk**.

3. I Exchange Administration på skal <https://admin.exchange.microsoft.com/>du gøre følgende:
   1. Vælg **Roller** \> **Administratorroller**. For at gå direkte til siden **Administratorroller** skal du bruge <https://admin.exchange.microsoft.com/#/adminRoles>.
   2. På siden **Administratorroller** skal du manuelt vælge hver rollegruppe, og i detaljeruden skal du vælge fanen **Tildelt for at** bekræfte brugerkontiene. Hvis rollegruppen indeholder brugerkontoen, skal du gøre følgende:
      1. Vælg brugerkontoen.
      2. Klik på knappen ![Ikonet Slet.](../../media/m365-cc-sc-delete-icon.png).

         Klik på **Gem**, når du er færdig.

### <a name="step-7-optional-additional-precautionary-steps"></a>Trin 7 Valgfrit: Yderligere sikkerhedstrin

1. Sørg for, at du har bekræftet dine sendte elementer. Du skal muligvis informere personerne på din liste over kontakter om, at din konto er blevet kompromitteret. Hackeren kan have bedt dem om penge, spoofing, f.eks. at du er strandet et andet land og har brug for penge, eller at hackeren kan sende dem en virus for også at sprede deres computere.

2. Alle andre tjenester, der brugte denne Exchange-konto som dens alternative mailkonto, kan være blevet kompromitteret. Du skal først udføre disse trin for Microsoft 365 dit abonnement og derefter udføre disse trin for dine andre konti.

3. Sørg for, at dine kontaktoplysninger, f.eks. telefonnumre og adresser, er korrekte.

## <a name="secure-microsoft-365-like-a-cybersecurity-pro"></a>Beskyt Microsoft 365 som en cybersecurity-pro

Dit Microsoft 365-abonnement leveres med et effektivt sæt sikkerhedsfunktioner, som du kan bruge til at beskytte dine data og dine brugere.  Brug [Microsoft 365-sikkerhedsoversigten – Topprioriteter for de første 30 dage, 90](security-roadmap.md) dage og derefter for at implementere anbefalede microsoft-fremgangsmåder til sikring af din Microsoft 365 lejer.

- Opgaver, der skal udføres inden for de første 30 dage. Disse har øjeblikkelig indvirkning og har lav effekt for dine brugere.
- Opgaver, der skal udføres på 90 dage. Disse tager lidt mere tid at planlægge og implementere, men i høj grad forbedre din sikkerhed.
- Mere end 90 dage. Disse forbedringer er en del af dit første arbejde på 90 dage.

## <a name="see-also"></a>Se også

- [Registrer og afhjulpet Outlook regler og brugerdefinerede formularindskudsangreb i Microsoft 365](detect-and-remediate-outlook-rules-forms-attack.md)
- [Internet til klagecenter for gerningssted](https://www.ic3.gov/Home/Ransomware)
- [Provision for sikkerhed og Exchange - "Phishing"-svindel](https://www.sec.gov/investor/pubs/phishing.htm)
- Sådan rapporterer du spammail direkte til Microsoft og din [administrator Brug tilføjelsesprogrammet Rapportmeddelelse](https://support.microsoft.com/office/b5caa9f1-cdf3-4443-af8c-ff724ea719d2)
