---
title: Bruger rapporterede meddelelsesindstillinger
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Administratorer kan lære, hvordan de konfigurerer en postkasse til at indsamle spam- og phishingmails, der rapporteres af brugerne.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 525b761b09a68c3e44443cec7bf718d9eaa4d8d1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590869"
---
# <a name="user-reported-message-settings"></a>Bruger rapporterede meddelelsesindstillinger

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 med Exchange Online postkasser kan du angive en postkasse for at modtage meddelelser, som brugerne rapporterer som skadelige eller ikke skadelige. Når brugere rapporterer meddelelser ved hjælp af de forskellige rapporteringsmuligheder, kan du bruge denne postkasse til at opfange meddelelser (kun sende til den brugerdefinerede postkasse) eller modtage kopier af meddelelser (send til den brugerdefinerede postkasse og Microsoft). Denne funktion fungerer sammen med følgende indstillinger for rapportering af meddelelser:

- [Tilføjelsesprogrammet Rapportmeddelelse](enable-the-report-message-add-in.md)
- [Tilføjelsesprogrammet Report Phishing](enable-the-report-phish-add-in.md)
- [Tredjeparts rapporteringsværktøjer](#third-party-reporting-tools)

Levering af meddelelser rapporteret af brugeren til en brugerdefineret postkasse i stedet for direkte til Microsoft giver dine administratorer mulighed for selektivt og manuelt rapportere meddelelser til Microsoft ved hjælp af [administratorindsendelse](admin-submission.md). Disse indstillinger var tidligere kendt som politikken for brugerindsendelser.

  > [!NOTE]
  > Hvis rapportering er blevet [deaktiveret i Outlook på internettet](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web), tilsidesætter aktivering af brugerrapporterede meddelelser her denne indstilling og giver brugerne mulighed for at rapportere meddelelser Outlook på internettet igen.

## <a name="custom-mailbox-prerequisites"></a>Forudsætninger for brugerdefineret postkasse

Brug følgende artikler til at konfigurere de nødvendige forudsætninger for, at brugerrapporterede meddelelser sendes til den brugerdefinerede postkasse:

- Spring spamfiltrering over den brugerdefinerede postkasse ved at oprette en regel for mailflow i Exchange for at angive tillidsniveauet til spam. Se [Brug EAC til](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl#use-the-eac-to-create-a-mail-flow-rule-that-sets-the-scl-of-a-message) at oprette en regel for mailflow, der indstiller SCL i en meddelelse til at indstille SCL til at **omgå spamfiltrering**.

- [Opret en antimalwarepolitik](configure-your-spam-filter-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) , der omfatter den brugerdefinerede postkasse, hvor automatisk tømning (ZAP) uden time (ZAP) for malware er slået **fra (** \> sektionen Beskyttelse indstillinger Aktivér automatisk tømning **af malware** i nul timer er ikke markeret).

- [Opret en antispampolitik](configure-your-spam-filter-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) , der omfatter den brugerdefinerede postkasse, hvor ZAP til spam og ZAP til phishing er slået **fra (** \> sektionen Automatisk tømning uden time Aktiveret automatisk tømning **uden time (ZAP)** er ikke markeret).

Hvis du har Microsoft Defender Office 365, skal du også konfigurere følgende indstillinger, så vores avancerede filtrering ikke påvirker de brugere, der rapporterer meddelelser:

- [Opret en Pengeskab-politik for links](set-up-safe-links-policies.md), der omfatter den brugerdefinerede postkasse, hvor scanning af Pengeskab Links er slået fra (Vælg handlingen **for ukendt potentielt** \> skadelige URL-adresser i meddelelsessektionen **Fra**).

- [Opret en Pengeskab](set-up-safe-attachments-policies.md) politik for vedhæftede filer, der omfatter den brugerdefinerede postkasse, hvor scanning af Pengeskab vedhæftede filer er slået fra (**Pengeskab Ukendt malware** svar på vedhæftede filer **fra**\>).

Når du har bekræftet, at din postkasse opfylder alle relevante forudsætninger, kan du bruge procedurerne i denne artikel til at konfigurere postkassen til brugerindsendelser.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til **siden Brugerindsendelser** skal du bruge <https://security.microsoft.com/reportsubmission>.

- Hvis du vil ændre konfigurationen for brugerindsendelser, skal du være medlem af en af følgende rollegrupper:

  - **Organisationsadministration** **eller sikkerhedsadministrator** [i tilladelserne på Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

- Du skal have adgang til Exchange Online PowerShell. Hvis den konto, du forsøger at bruge, ikke har adgang til Exchange Online PowerShell, modtager du en fejl, der ser sådan ud, når du angiver postkassen for indsendelser:

  > Angiv en mailadresse i dit domæne

  Du kan finde flere oplysninger om aktivering eller deaktivering af Exchange Online PowerShell under følgende emner:

  - [Aktivér eller deaktiver adgang til Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [Regler for klientadgang i Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="use-the-microsoft-365-defender-portal-to-configure-the-user-submissions-mailbox"></a>Brug portalen Microsoft 365 Defender til at konfigurere postkassen for brugerindsendelser

1. I portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **Politikker & regler** \> **Fortrudt-politikker** \> Brugeren har **rapporteret meddelelsesindstillinger** i **sektionen** Andre. For at gå direkte til **siden Brugerindsendelser** skal du bruge <https://security.microsoft.com/reportsubmission>.

2. På siden **Brugerindsendelser** bestemmes det, du ser, af, om **knappen Microsoft Outlook Rapportmeddelelse** er **slået Fra** eller **Til**:

   - **Microsoft Outlook** \>  ![Rapportmeddelelse til Til/fra.](../../media/scc-toggle-on.png): Vælg denne indstilling, hvis du bruger tilføjelsesprogrammet Rapportmeddelelse, tilføjelsesprogrammet Rapportphishing eller den indbyggede rapportering i Outlook på internettet, og konfigurer derefter følgende indstillinger:
     - **Send de rapporterede meddelelser til**: Vælg en af følgende indstillinger:
       - **Microsoft**: Brugerindsendelsespostkassen bruges ikke (alle rapporterede meddelelser sendes til Microsoft).
       - **Microsoft og min organisations postkasse: I** det felt, der vises, skal du angive mailadressen til en eksisterende Exchange Online postkasse. Distributionsgrupper er ikke tilladt. Brugerindsendelser går til både Microsoft til analyse og den brugerdefinerede postkasse, som din administrator eller dit sikkerhedsteam kan analysere.
       - **Min organisations postkasse: I** det felt, der vises, skal du skrive mailadressen til en eksisterende Exchange Online postkasse. Distributionsgrupper er ikke tilladt. Brug denne indstilling, hvis meddelelsen kun skal sendes til en administrator eller sikkerhedsteamet til analyse først. Meddelelser sendes ikke til Microsoft, medmindre administratoren videresender dem selv.

          > [!IMPORTANT]
          > Amerikanske myndigheder (GCC, GCC High og DoD) kan kun konfigurere **Min organisations postkasse**. De andre to indstillinger deaktiveres.
          >
          > Hvis organisationer er konfigureret til kun at sende til brugerdefineret postkasse, sendes rapporterede meddelelser ikke til genscanning, og resultaterne i portalen brugerrapporterede meddelelser vil altid være tomme.

       Uanset den værdi, du har valgt for **Send de rapporterede meddelelser til**, er følgende indstillinger tilgængelige:

       - **Lad brugere vælge, om de vil rapportere deres meddelelse til Microsoft**
       - **Vælg rapporteringsindstillinger, der er tilgængelige for** brugere: Vælg mindst én af følgende indstillinger:
         - **Spørg, før du sender meddelelsen**
         - **Rapportér altid meddelelsen**
         - **Rapportér aldrig meddelelsen**

          > [!CAUTION]
          > Hvis du har deaktiveret rapportering om uønsket mail i [Outlook på internettet](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) ved hjælp af Outlook på internettet-postkassepolitikker, men du har konfigureret nogen af de tidligere indstillinger til at rapportere meddelelser til Microsoft, kan brugerne rapportere meddelelser til Microsoft i Outlook på internettet  ved hjælp af tilføjelsesprogrammet Rapportmeddelelse eller tilføjelsesprogrammet Report Phishing.

     Lad knappen **Microsoft Outlook Rapportmeddelelse** ![](../../media/scc-toggle-on.png) være slå til for at tillade slutbrugere at rapportere falske positive meddelelser fra karantæneportalen.

     - **Sektionen Brugerrapporteringsoplevelse**
       - **Før fanen** Rapportering: I felterne  Titel og  Meddelelsestekst skal du angive den beskrivende tekst, som brugerne ser, før de rapporterer en meddelelse ved hjælp af tilføjelsesprogrammet Rapportmeddelelse eller tilføjelsesprogrammet Rapportphishing. Du kan bruge variablen %type% til at medtage indsendelsestypen (uønsket, ikke uønsket, phish osv.).
       - **Efter rapporteringsfanen**:  I felterne  Titel og Bekræftelse skal du skrive den beskrivende tekst, som brugerne ser, efter de rapporterer en meddelelse ved hjælp af tilføjelsesprogrammet Rapportmeddelelse eller tilføjelsesprogrammet Rapportphishing. Du kan bruge variablen %type% til at medtage indsendelsestypen.
       - **Vis kun, når brugeren rapporterer phishing**: Markér denne indstilling, hvis du kun vil have vist meddelelsen, når en mail rapporteres som phish. Hvis ikke, vises markerede meddelelser for enhver type rapport.

       Som vist på siden føjes følgende tekst også til meddelelsen, hvis du vælger en indstilling, der sender de rapporterede meddelelser til Microsoft:

          > Din mail sendes, som den er til Microsoft til analyse. Nogle mails kan indeholde personlige eller følsomme oplysninger.

   - **Microsoft Outlook Report Message-knappen** \>  ![Fra.](../../media/scc-toggle-off.png): Vælg denne indstilling, hvis du bruger rapporteringsværktøjer fra en tredjepart i stedet for tilføjelsesprogrammet Rapportmeddelelse, tilføjelsesprogrammet Rapportphishing eller den indbyggede rapportering i Outlook på internettet, og konfigurer derefter følgende indstillinger:
     - Vælg **Brug denne brugerdefinerede postkasse til at modtage brugerrapporterede indsendelser**. I den dialogboks, der vises, skal du skrive mailadressen til en eksisterende Exchange Online, der kan modtage mail.

   - **Knappen Anmeld rapportmeddelelse**: Aktivér denne funktion, hvis du vil lade slutbrugere rapportere meddelelser fra karantæne.

   Klik på Bekræft, når du er **færdig**. Hvis du vil rydde disse værdier, skal du klikke på **Gendan**

## <a name="third-party-reporting-tools"></a>Tredjeparts rapporteringsværktøjer

Du kan konfigurere rapporteringsværktøjer fra tredjepart til at sende rapporterede meddelelser til den brugerdefinerede postkasse. Det gør du ved at angive knappen **Microsoft Outlook Report Message** til Fra og angive Min organisations  postkasse til en Office 365  postkasse efter eget valg.

Det eneste krav er, at den oprindelige meddelelse medtages som en . EML eller . Vedhæftet MSG-fil (ikke komprimeret) i den meddelelse, der sendes til den brugerdefinerede postkasse (du skal ikke bare videresende den oprindelige meddelelse til den brugerdefinerede postkasse).

Kravene til formatering af meddelelser er beskrevet i næste afsnit. Formateringen er valgfri, men hvis den ikke følger det angivne format, bliver rapporterne altid sendt som phish.

## <a name="message-submission-format"></a>Meddelelsesafsendelsesformat

For at identificere de oprindelige vedhæftede meddelelser korrekt skal de meddelelser, der sendes til den brugerdefinerede postkasse, have en bestemt formatering. Hvis meddelelserne ikke bruger dette format, identificeres de oprindelige vedhæftede meddelelser altid som phishing-indsendelser.

Hvis du vil angive den rapporterede årsag til de oprindelige vedhæftede meddelelser, skal meddelelser, der sendes til den brugerdefinerede postkasse (ikke ændrer den vedhæftede fil), starte med en af følgende præfikser i Emne (konvoluttitel):

- 1| eller Uønsket:
- 2| eller Ikke uønsket
- 3| eller phishing

Eksempel:

`3|This part is ignored by the system` <br>
`Not Junk:This part of the subject is ignored as well`

- Begge disse meddelelser rapporteres som Ikke uønsket baseret på emne.
- Resten ignoreres.


Meddelelser, der ikke følger dette format, vises ikke korrekt i portalen Indsendelser.
