---
title: Beskedklassering for mistænkelig mail videresendelsesaktivitet
description: Beskedklassering for mistænkelig mail videresendelsesaktivitet for at gennemse beskederne og udføre anbefalede handlinger for at afhjælpe angrebet og beskytte dit netværk.
keywords: hændelser, beskeder, undersøge, analysere, svar, korrelation, angreb, maskiner, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: dcfb6d01503dd4499ce6431b95a433c4cb598de1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663220"
---
# <a name="alert-grading-for-suspicious-email-forwarding-activity"></a>Beskedklassering for mistænkelig mail videresendelsesaktivitet

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Trusselsaktører kan bruge kompromitterede brugerkonti til flere skadelige formål, herunder at læse mails i en brugers indbakke, videresende mails til eksterne modtagere og bl.a. sende phishing-mails. Den målrettede bruger er muligvis ikke klar over, at vedkommendes mails videresendes. Dette er en meget almindelig taktik, som angribere bruger, når brugerkonti kompromitteres.

Mails kan videresendes enten manuelt eller automatisk ved hjælp af regler for videresendelse. Automatisk videresendelse kan implementeres på flere måder, f.eks. indbakkeregler, Exchange transportregel (ETR) og SMTP-videresendelse. Selvom manuel videresendelse kræver direkte handling fra brugerne, er de muligvis ikke opmærksomme på alle de automatisk videresendte mails. I Microsoft 365 udløses der en besked, når en bruger automatisk videresender en mail til en potentielt ondsindet mailadresse.

Denne playbook hjælper dig med at undersøge mistænkelige beskeder om videresendelse af mailaktivitet og hurtigt bedømme dem som enten en sand positiv (TP) eller falsk positiv (FP). Du kan derefter udføre anbefalede handlinger for TP-beskederne for at afhjælpe angrebet.

Du kan få en oversigt over beskedklassering for Microsoft Defender for Office 365 og Microsoft Defender for Cloud Apps i [introduktionsartiklen](alert-grading-playbooks.md).

Resultaterne af at bruge denne playbook er:

- Du har identificeret de beskeder, der er knyttet til automatisk videresendte mails, som skadelige (TP) eller godartede aktiviteter (FP).

  Hvis det er skadeligt, har du [stoppet automatisk videresendelse af mail](../office-365-security/external-email-forwarding.md) for de berørte postkasser.

- Du har foretaget den nødvendige handling, hvis mails er blevet videresendt til en ondsindet mailadresse.

## <a name="email-forwarding-rules"></a>Regler for videresendelse af mail

Regler for videresendelse af mail giver brugerne mulighed for at oprette en regel til videresendelse af mails, der er sendt til en brugers postkasse til en anden brugers postkasse i eller uden for organisationen. Nogle mailbrugere, især dem med flere postkasser, konfigurerer regler for videresendelse for at flytte arbejdsgivermails til deres private mailkonti. Videresendelse af mail er en nyttig funktion, men kan også udgøre en sikkerhedsrisiko på grund af en potentiel offentliggørelse af oplysninger. Personer med ondsindede hensigter kan bruge disse oplysninger til at angribe din organisation eller dens partnere.

### <a name="suspicious-email-forwarding-activity"></a>Mistænkelig aktivitet for videresendelse af mail

Personer med ondsindede hensigter kan konfigurere mailregler for at skjule indgående mails i den kompromitterede brugerpostkasse for at skjule deres skadelige aktiviteter for brugeren. De kan også angive regler i den kompromitterede brugerpostkasse for at slette mails, flytte mails til en anden mindre mærkbar mappe, f.eks. en RSS-mappe, eller videresende mails til en ekstern konto.

Nogle regler kan flytte alle mails til en anden mappe og markere dem som "læst", mens nogle regler muligvis kun flytter mails, der indeholder bestemte nøgleord i mailen eller emnet. Indbakkereglen kan f.eks. være angivet til at søge efter nøgleord som "faktura", "phish", "besvar ikke", "mistænkelig mail" eller "spam" blandt andre og flytte dem til en ekstern mailkonto. Personer med ondsindede hensigter kan også bruge den kompromitterede brugerpostkasse til at distribuere spam, phishing-mails eller malware.

Microsoft Defender for Office 365 kan registrere og advare om mistænkelige regler for videresendelse af mail, så du kan finde og slette skjulte regler i kilden.

Du kan få flere oplysninger i disse blogindlæg:

- [Kompromitteret firmamail](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/business-email-uncompromised-part-one/ba-p/2159900)
- [Bag kulisserne i forbindelse med kompromitteret virksomhedsmail: Brug af data på tværs af domæner til at afbryde en stor BEC-kampagne](https://www.microsoft.com/security/blog/2021/06/14/behind-the-scenes-of-business-email-compromise-using-cross-domain-threat-data-to-disrupt-a-large-bec-infrastructure/)

## <a name="alert-details"></a>Beskedoplysninger

Hvis du vil gennemse beskeden Videresendelse af mistænkelig mail, skal du åbne siden **Beskeder** for at se sektionen **Aktivitetsliste** . Her er et eksempel.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png" alt-text="Liste over aktiviteter, der er relateret til beskeden" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png":::

Vælg **Aktivitet**  for at få vist detaljer om den pågældende aktivitet i sidepanelet. Her er et eksempel.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png" alt-text="Detaljer om aktiviteten" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png":::

Feltet **Årsag** indeholder følgende oplysninger, der er relateret til denne besked.

- Videresendelsestype (FT) er en af følgende:
  - Exchange transportregel: Videresendt ved hjælp af og Exchange transportregel
  - SMTP: Viderestillet ved hjælp af videresendelse af postkasse
  - InboxRule: Videresendt ved hjælp af en indbakkeregel

- MTI (Message Trace ID): Dette er id'et (NetworkMessageId) for den videresendte mail, der udløste denne besked. NetworkMessageId er det entydige id for en mail i din organisation.
- Forwarder (F): Den bruger, der videresendte denne mail.
- Mistænkelig modtagerliste: Listen over modtagere, der betragtes som mistænkelige i denne mail.
- Modtagerliste : Listen over alle modtagerne i denne mail.

## <a name="investigation-workflow"></a>Undersøgelsesarbejdsproces

Når du undersøger denne besked, skal du bestemme:

- Er brugerkontoen og dens postkasse kompromitteret?
- Er aktiviteterne skadelige?

### <a name="is-the-user-account-and-its-mailbox-compromised"></a>Er brugerkontoen og dens postkasse kompromitteret?

Når du kigger på afsenderens tidligere adfærd og seneste aktiviteter, bør du kunne afgøre, om brugerens konto skal betragtes som kompromitteret eller ej. Du kan se oplysninger om beskeder, der vises fra brugerens side, på Microsoft 365 Defender-portalen.

Du kan også analysere disse yderligere aktiviteter for den pågældende postkasse:

- Brug Threat Explorer til at forstå mailrelaterede trusler
  - Se, hvor mange af de seneste mails, der er sendt af afsenderen, der registreres som phish, spam eller malware.
  - Se, hvor mange af de sendte mails der indeholder følsomme oplysninger.

- Vurder risikabel logonfunktion på Microsoft Azure-portalen.
- Kontrollér, om der er skadelige aktiviteter på brugerens enhed.

### <a name="are-the-activities-malicious"></a>Er aktiviteterne skadelige?

Undersøg videresendelsesaktiviteten for mail. Du kan f.eks. kontrollere typen af mail, modtageren af denne mail eller den måde, som mailen viderestilles på.

Du kan finde flere oplysninger i følgende artikler:

- [Indsigt i automatisk videresendte meddelelser](/microsoft-365/security/office-365-security/mfi-auto-forwarded-messages-report)
- [Nye brugere videresender mailindsigt](/microsoft-365/security/office-365-security/mfi-new-users-forwarding-email)
- [Svar på en kompromitteret mailkonto](/microsoft-365/security/office-365-security/responding-to-a-compromised-email-account)
- [Rapportér falske positiver og falske negativer i Outlook](/microsoft-365/security/office-365-security/report-false-positives-and-false-negatives)

Her er arbejdsprocessen til at identificere mistænkelige aktiviteter for videresendelse af mail.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png" alt-text="Arbejdsproces til undersøgelse af beskeder for videresendelse af mail" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png":::

Du kan undersøge en besked om videresendelse af mail ved hjælp af Threat Explorer eller med avancerede jagtforespørgsler baseret på tilgængeligheden af funktioner på Microsoft 365 Defender-portalen. Du kan vælge at følge hele processen eller en del af processen efter behov.

## <a name="using-threat-explorer"></a>Brug af Threat Explorer

Threat Explorer giver en interaktiv undersøgelsesoplevelse for mailrelaterede trusler for at afgøre, om denne aktivitet er mistænkelig eller ej. Du kan bruge følgende indikatorer fra beskedoplysningerne:

- SRL/RL: Brug listen over (mistænkelige) modtagere (SRL) til at finde disse oplysninger:

    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png" alt-text="Eksempel på listen over modtagere" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png":::

  - Who andre har videresendt mails til disse modtagere?
  - Hvor mange mails er blevet videresendt til disse modtagere?
  - Hvor ofte videresendes mails til disse modtagere?

- MTI: Brug meddelelsessporings-id'et/netværksmeddelelses-id'et til at finde disse oplysninger:

    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png" alt-text="Eksempel på netværksmeddelelses-id'et" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png":::

  - Hvilke yderligere oplysninger er tilgængelige for denne mail? Eksempel: emne, retursti og tidsstempel.
  - Hvad er oprindelsen af denne mail? Er der nogen lignende e-mails?
  - Indeholder denne mail NOGEN URL-adresser? Peger URL-adressen på følsomme data?
  - Indeholder mailen vedhæftede filer? Indeholder de vedhæftede filer følsomme oplysninger?
  - Hvad blev handlingen udført på mailen? Er den slettet, markeret som læst eller flyttet til en anden mappe?
  - Er der knyttet nogen trusler til denne mail? Er denne mail en del af en kampagne?

Baseret på svar på disse spørgsmål bør du kunne afgøre, om en mail er ondsindet eller godartet.

## <a name="advanced-hunting-queries"></a>Avancerede jagtforespørgsler

Hvis du vil bruge [avancerede](advanced-hunting-overview.md) jagtforespørgsler til at indsamle oplysninger, der er relateret til en besked, og afgøre, om aktiviteten er mistænkelig eller ej, skal du sørge for, at du har adgang til følgende tabeller:

- EmailEvents – Indeholder oplysninger, der er relateret til mailflow.

- EmailUrlInfo – Indeholder oplysninger, der er relateret til URL-adresser i mails.

- CloudAppEvents – Indeholder overvågningslog over brugeraktiviteter.

- IdentityLogonEvents – Indeholder logonoplysninger for alle brugere.

> [!NOTE]
> Visse parametre er entydige for din organisation eller dit netværk. Udfyld disse specifikke parametre som beskrevet i hver forespørgsel.

Kør denne forespørgsel for at finde ud af, hvem der ellers har videresendt mails til disse modtagere (SRL/RL).

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| distinct SenderDisplayName, SenderFromAddress, SenderObjectId
```

Kør denne forespørgsel for at finde ud af, hvor mange mails der blev videresendt til disse modtagere.

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| summarize Count=dcount(NetworkMessageId) by RecipientEmailAddress
```

Kør denne forespørgsel for at finde ud af, hvor ofte mails videresendes til disse modtagere.

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| summarize Count=dcount(NetworkMessageId) by RecipientEmailAddress, bin(Timestamp, 1d)
```

Kør denne forespørgsel for at finde ud af, om mailen indeholder URL-adresser.

```kusto
let mti='{MTI}'; //Replace {MTI} with MTI from alert
EmailUrlInfo
| where NetworkMessageId == mti
```

Kør denne forespørgsel for at finde ud af, om mailen indeholder vedhæftede filer.

   ```kusto
   let mti='{MTI}'; //Replace {MTI} with MTI from alert
   EmailAttachmentInfo
   | where NetworkMessageId == mti
   ```

Kør denne forespørgsel for at finde ud af, om videresenderen (afsenderen) har oprettet nye regler.

```kusto
let sender = "{SENDER}"; //Replace {SENDER} with display name of Forwarder
let action_types = pack_array(
    "New-InboxRule",
    "UpdateInboxRules",
    "Set-InboxRule",
    "Set-Mailbox",
    "New-TransportRule",
    "Set-TransportRule");
CloudAppEvents
| where AccountDisplayName == sender
| where ActionType in (action_types)
```

Kør denne forespørgsel for at finde ud af, om der var nogen unormale logonhændelser fra denne bruger. Eksempel: ukendte IP-adresser, nye programmer, ualmindelige lande, flere LogonFailed-hændelser.

```kusto
let sender = "{SENDER}"; //Replace {SENDER} with email of the Forwarder
IdentityLogonEvents
| where AccountUpn == sender
```

### <a name="investigating-forwarding-rules"></a>Undersøger regler for videresendelse

Du kan også finde mistænkelige regler for videresendelse ved hjælp af Exchange Administration baseret på regeltypen (FT-værdien i beskeden).

- ETR

  Exchange transportregler er angivet i afsnittet **Regler**. Kontrollér, at alle regler er som forventet.

- SMTP

  Du kan se regler for videresendelse af postkasser ved at vælge afsenderens postkasse **\>  Administrer mailflowindstillinger \> Rediger til videresendelse af \> mail**.

- IndbakkeRegel

  Indbakkeregler konfigureres med mailklienten. Du kan bruge PowerShell-cmdlet'en [Get-InboxRule](/powershell/module/exchange/get-inboxrule) til at få vist de indbakkeregler, der er oprettet af brugere.

### <a name="additional-investigation"></a>Yderligere undersøgelse

Sammen med de beviser, der er fundet indtil videre, kan du afgøre, om der oprettes nye regler for videresendelse. Undersøg den IP-adresse, der er knyttet til reglen. Sørg for, at det ikke er en unormal IP-adresse og er i overensstemmelse med brugerens normale aktiviteter.

## <a name="recommended-actions"></a>Anbefalede handlinger

Når du har fastslået, at de tilknyttede aktiviteter gør denne besked til en sand positiv, skal du klassificere beskeden og foretage følgende handlinger for at løse problemet:

1. Deaktiver og slet reglen for videresendelse af indbakken.
2. For videresendelsestypen IndbakkeRegel skal du nulstille brugerens legitimationsoplysninger.
3. Undersøg aktiviteterne for den brugerkonto, der oprettede beskeden, for videresendelsestypen SMTP eller ETR.

    - Undersøg alle andre mistænkelige administratoraktiviteter.

    - Nulstil brugerkontoens legitimationsoplysninger.

4. Kontrollér, om der er yderligere aktiviteter, der stammer fra påvirkede konti, IP-adresser og mistænkelige afsendere.

## <a name="see-also"></a>Se også

- [Oversigt over beskedklassering](alert-grading-playbooks.md)
- [Mistænkelige regler for videresendelse af indbakke](alert-grading-playbook-inbox-forwarding-rules.md)
- [Regler for mistænkelig manipulation af indbakke](alert-grading-playbook-inbox-manipulation-rules.md)
- [Undersøg beskeder](investigate-alerts.md)
