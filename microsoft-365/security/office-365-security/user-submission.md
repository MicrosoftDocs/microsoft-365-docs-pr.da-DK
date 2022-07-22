---
title: Brugerrapporterede mailindstillinger for spam, phish, som skadelig mail
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 07/19/2022
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Sådan konfigurerer du en postkasse til at indsamle spam og phishing-mail rapporteret af brugere. Opret en postkasse til meddelelser, som brugerne rapporterer som spam, phish, som ondsindet eller ikke ondsindet.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 02356f03f60e2bfc0c6c7de992fdc0c4331f3a4c
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66942510"
---
# <a name="user-reported-message-settings"></a>Brugerrapporterede meddelelsesindstillinger

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365-organisationer med Exchange Online postkasser kan du sende mails til en postkasse, når brugerne rapporterer spam, phish, som skadelige eller endda ikke skadelige meddelelser. Når brugerne rapporterer mails ved hjælp af forskellige rapporteringsindstillinger, kan administratorer bruge denne postkasse til at opfange disse mails (kun sende til den brugerdefinerede postkasse) eller modtage kopier af meddelelser (sende til den brugerdefinerede postkasse og Microsoft).

Denne funktion fungerer sammen med disse indstillinger for meddelelsesrapportering:

- [Tilføjelsesprogrammet Rapportmeddelelse](enable-the-report-message-add-in.md)
- [Tilføjelsesprogrammet Rapport phishing](enable-the-report-phish-add-in.md)
- [Rapporteringsværktøjer fra tredjepart](user-submission.md#third-party-email-reporting-tools)

Levering af brugerrapporterede meddelelser til en brugerdefineret postkasse i stedet for direkte til Microsoft giver administratorer mulighed for selektivt og manuelt at rapportere mails til Microsoft ved hjælp af [Administration indsendelse](admin-submission.md). *Disse indstillinger var tidligere kendt som politikken Brugerindsendelser*.

  > [!NOTE]
  > Hvis rapportering er blevet [deaktiveret i Outlook på internettet](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web), tilsidesætter aktivering af brugerrapporterede meddelelser denne indstilling og giver brugerne mulighed for at rapportere meddelelser i Outlook på internettet igen.

## <a name="custom-mailbox-prerequisites"></a>Forudsætninger for brugerdefineret postkasse

Brug artiklerne nedenfor til at konfigurere forudsætninger for, at brugerrapporterede mails går til din brugerdefinerede postkasse:

- [Identificer den brugerdefinerede postkasse som en SecOps-postkasse](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).

- [Opret en antimalwarepolitik](configure-anti-malware-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-malware-policies) for den brugerdefinerede postkasse med følgende indstillinger:
  - Automatisk udrensning (ZAP) på nul timer for malware er slået fra (afsnittet \>**Beskyttelsesindstillinger** **Aktivér automatisk tøm af malware på nul timer** er ikke valgt).
  - Den fælles indstilling for filtrering af vedhæftede filer er slået fra (afsnittet \>**Beskyttelsesindstillinger** **Aktivér filteret for fælles vedhæftede filer** er ikke valgt).

**Hvis du har Microsoft Defender for Office 365**, skal du også konfigurere følgende indstillinger, så vores avancerede filtrering ikke påvirker de rapporterede mails:

- Sørg for, at den brugerdefinerede postkasse ikke er en del af nogen [forudindstillede sikkerhedspolitikker](preset-security-policies.md#use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-standard-and-strict-preset-security-policies)

- [Opret en politik for sikre links](set-up-safe-links-policies.md) for den brugerdefinerede postkasse, hvor scanning af sikre links er slået fra (**Vælg handlingen for ukendte potentielt skadelige URL-adresser i meddelelser** > **Fra**).

- [Opret en politik for vedhæftede filer, der er tillid](set-up-safe-attachments-policies.md) til, for den brugerdefinerede postkasse, hvor scanning af vedhæftede filer, der er tillid til, herunder Dynamisk levering, er slået fra (sektionen **Sikre vedhæftede filer ukendt malwaresvar** > **Slået fra**).

Når du har kontrolleret, at din postkasse opfylder forudsætningerne, kan du bruge resten af denne artikel til at konfigurere postkassen til brugerindsendelser.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Brugerindsendelser** , skal du bruge <https://security.microsoft.com/userSubmissionsReportMessage>.

- Hvis du vil ændre konfigurationen for brugerindsendelser, skal du være medlem af en af følgende rollegrupper:

  - **Organisationsadministration** eller **Sikkerhedsadministrator** i [tilladelserne på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).

- Du skal have adgang til Exchange Online PowerShell. Hvis den konto, du forsøger at bruge, ikke har adgang til Exchange Online PowerShell, får du vist en fejl, der ser sådan ud, når du angiver postkassen for indsendelser:

  > Angiv en mailadresse i dit domæne

  Du kan få flere oplysninger om aktivering eller deaktivering af adgang til Exchange Online PowerShell i følgende emner:

  - [Aktivér eller deaktiver adgang til Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [Klientadgangsregler i Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="use-the-microsoft-365-defender-portal-to-configure-the-user-submissions-mailbox-for-emails"></a>Brug Microsoft 365 Defender-portalen til at konfigurere postkassen for brugerindsendelser for mails

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Politikker & regler** > **Trusselspolitikker** > **Brugerrapporterede meddelelsesindstillinger** i afsnittet **Andre**. Hvis du vil gå direkte til siden **Brugerindsendelser** , skal du bruge <https://security.microsoft.com/userSubmissionsReportMessage>.

2. På siden **Brugerindsendelser** bestemmes det, du ser, af, om **indstillingen for microsoft Outlook-rapportmeddelelsen** er **Slået fra** eller **Til**:

   - **Microsoft Outlook-rapportmeddelelsesknap** >  **På** ![ Slå til.](../../media/scc-toggle-on.png): Vælg denne indstilling, hvis du bruger tilføjelsesprogrammet Rapportmeddelelse, tilføjelsesprogrammet Rapport phishing eller den indbyggede rapportering i Outlook på internettet, og konfigurer derefter følgende indstillinger:
     - **Send de rapporterede meddelelser til**: Vælg en af følgende indstillinger:
       - **Microsoft**: Postkassen til brugerindsendelser bruges ikke (alle rapporterede meddelelser sendes til Microsoft).
       - **Microsoft og min organisations postkasse**: Angiv mailadressen på en eksisterende Exchange Online postkasse i det felt, der vises. Distributionsgrupper er ikke tilladt. Brugerindsendelser sendes til både Microsoft til analyse og til den brugerdefinerede postkasse, som administratoren eller sikkerhedsteamet skal analysere.
       - **Min organisations postkasse**: Angiv mailadressen på en eksisterende Exchange Online postkasse i det felt, der vises. Distributionsgrupper er ikke tilladt. Brug denne indstilling, hvis meddelelsen kun skal gå til en administrator eller sikkerhedsteamet til analyse først. Meddelelser sendes ikke til Microsoft, medmindre administratoren selv videresender den.

          > [!IMPORTANT]
          > Amerikanske offentlige organisationer (GCC, GCC High og DoD) kan kun konfigurere **Min organisations postkasse**. De to andre indstillinger er deaktiveret.
          >
          > Hvis organisationer er konfigureret til kun at sende brugerrapporterede meddelelser til den brugerdefinerede postkasse, vises rapporterede meddelelser i **brugerrapporterede meddelelser** , men deres resultater vil altid være tomme (da de ikke ville være blevet scannet igen).
          >
          > Hvis du udfører phishingsimulering ved hjælp af [oplæring i simulering af angreb](attack-simulation-training-get-started.md) eller et tredjepartsprodukt, skal du [konfigurere denne postkasse som en SecOps-postkasse](configure-advanced-delivery.md). Hvis du ikke gør det, kan rapportering af meddelelser udløse oplæringsopgaver i phishingsimuleringsproduktet.

       Uanset hvilken værdi du har valgt for **Send de rapporterede meddelelser til**, er følgende indstillinger tilgængelige:

       - **Lad brugerne vælge, om de vil rapportere deres meddelelse til Microsoft**
       - **Vælg rapportindstillinger, der er tilgængelige for brugere** : Vælg mindst én blandt følgende indstillinger:
         - **Spørg mig, før du sender meddelelsen**
         - **Rapportér altid meddelelsen**
         - **Rapportér aldrig meddelelsen**

          > [!CAUTION]
          > Hvis du har [deaktiveret rapportering af uønsket mail i Outlook på internettet](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) ved hjælp af Outlook på internettet postkassepolitikker, men du har konfigureret en af de tidligere indstillinger for at rapportere meddelelser til Microsoft, kan brugerne rapportere meddelelser til Microsoft i Outlook på internettet  ved hjælp af tilføjelsesprogrammet Rapportmeddelelse eller tilføjelsesprogrammet Rapport phishing.

     Lad knappen ![Meddelelse **i Microsoft Outlook-rapport** til/fra være **slået**](../../media/scc-toggle-on.png) til for at give slutbrugere mulighed for at rapportere falske positive meddelelser fra karantæneportalen.

     - **Afsnittet Brugerrapporteringsoplevelse**
       - **Før rapporteringsfanen** : I felterne **Titel** og **Meddelelsesbrødtekst** skal du angive den beskrivende tekst, som brugerne får vist, før de rapporterer en meddelelse ved hjælp af tilføjelsesprogrammet Rapportmeddelelse eller tilføjelsesprogrammet Rapport phishing. Du kan bruge variablen %type% til at inkludere indsendelsestypen (uønsket, ikke uønsket mail, phish osv.).
       - **Efter rapporteringsfanen** : I felterne **Titel** og **Bekræftelse** skal du angive den beskrivende tekst, som brugerne får vist, når de rapporterer en meddelelse ved hjælp af tilføjelsesprogrammet Rapportmeddelelse eller tilføjelsesprogrammet Rapport phishing. Du kan bruge variablen %type% til at inkludere afsendelsestypen.
       - **Vis kun, når brugeren rapporterer phishing**: Markér denne indstilling, hvis du kun vil have vist meddelelsen, når en mail rapporteres som phish. Hvis ikke, vises de markerede meddelelser for enhver form for rapport.

       Hvis du vælger en indstilling, der sender de rapporterede meddelelser til Microsoft, føjes følgende tekst også til meddelelsen som vist på siden:

          > Din mail sendes, som den er, til Microsoft til analyse. Nogle mails kan indeholde personlige eller følsomme oplysninger.

   - **Microsoft Outlook-rapportmeddelelsesknap** >  **Ud** ![ Slå indstillingen fra](../../media/scc-toggle-off.png): Vælg denne indstilling, hvis du bruger rapporteringsværktøjer fra tredjepart i stedet for tilføjelsesprogrammet Rapportmeddelelse, tilføjelsesprogrammet Rapport phishing eller den indbyggede rapportering i Outlook på internettet, og konfigurer derefter følgende indstillinger:
     - Vælg **Brug denne brugerdefinerede postkasse til at modtage brugerrapporterede indsendelser**. I feltet, der vises, skal du angive mailadressen på en eksisterende Exchange Online postkasse, der kan modtage mail.

   - **Knappen Sæt rapportmeddelelse i karantæne**: Aktivér denne funktion, hvis du vil lade slutbrugerne rapportere meddelelser fra karantæne.

3. Klik på **Bekræft**, når du er færdig. Klik på **Gendan** for at rydde disse værdier.

## <a name="third-party-email-reporting-tools"></a>Værktøjer til rapportering af mail fra tredjepart

Du kan konfigurere værktøjer til rapportering af meddelelser fra tredjepart for at sende rapporterede meddelelser til den brugerdefinerede postkasse. Det gør du ved at angive **knappen Meddelelse i Microsoft Outlook-rapport** til **Fra** og angive **Min organisations postkasse** til en Office 365 postkasse efter eget valg.

Det eneste krav er, at den oprindelige meddelelse er inkluderet som en . EML eller . Den vedhæftede MSG-fil (ikke komprimeret) i den meddelelse, der sendes til den brugerdefinerede postkasse (videresend ikke kun den oprindelige meddelelse til den brugerdefinerede postkasse).

 > [!NOTE]
 > Hvis der findes flere vedhæftede filer i mailen, kasseres indsendelsen. Vi understøtter kun mails med én vedhæftet fil.

Kravene til meddelelsesformatering er beskrevet i næste afsnit. Formateringen er valgfri, men hvis den ikke følger det foreskrevne format, sendes rapporterne altid som phish.

## <a name="message-submission-format"></a>Format for afsendelse af meddelelse

Hvis du vil identificere de oprindelige vedhæftede meddelelser korrekt, kræver meddelelser, der sendes til den brugerdefinerede postkasse, specifik formatering. Hvis meddelelserne ikke bruger dette format, identificeres de oprindelige vedhæftede meddelelser altid som phishing-indsendelser.

Hvis du vil angive den rapporterede årsag til de oprindelige vedhæftede meddelelser, skal meddelelser, der sendes til den brugerdefinerede postkasse (ikke ændre den vedhæftede fil), starte med et af følgende præfikser i emnelinjen (konvoluttitel):

- 1| eller Uønsket:
- 2| eller Ikke uønsket:
- 3| eller phishing:

Eksempel:

`3|This part is ignored by the system` <br>
`Not Junk:This part of the subject is ignored as well`

Meddelelser, der ikke følger dette format, vises ikke korrekt på portalen Indsendelser.
