---
title: Besked om karakterering af mistænkelig videresendelse af mail
description: Giv besked om karakterer for mistænkelig videresendelse af mail for at gennemgå beskederne og foretage anbefalede handlinger for at afhjælpe angrebene og beskytte dit netværk.
keywords: hændelser, beskeder, undersøge, analysere, svare, korrelation, angreb, computere, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365
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
ms.openlocfilehash: 2349fb9ac736653b9a74c42aecf5e71cc95381ca
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63601089"
---
# <a name="alert-grading-for-suspicious-email-forwarding-activity"></a>Besked om karakterering af mistænkelig videresendelse af mail

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Trusselsbrugere kan bruge kompromitterede brugerkonti til flere ondsindede formål, herunder at læse mails i en brugers indbakke, videresende mails til eksterne modtagere og sende phishingmails blandt andre. Den målrettede bruger er måske ikke klar over, at deres mails bliver videresendt. Dette er en meget almindelig taktik, som hackere bruger, når brugerkonti bliver kompromitteret.

Mails kan videresendes enten manuelt eller automatisk ved hjælp af regler for videresendelse. Automatisk videresendelse kan gennemføres på flere måder, f.eks. indbakkeregler, Exchange transportregel (ETR) og SMTP-videresendelse. Manuel videresendelse kræver direkte handling fra brugerne, men de er muligvis ikke opmærksomme på alle automatisk videresendte mails. I Microsoft 365 vises en advarsel, når en bruger automatisk videresender en mail til en potentielt skadelig mailadresse.

Denne playbook hjælper dig med at undersøge mistænkelige beskeder om videresendelse af mail og hurtigt give dem karakterer som enten en Sand positiv (TP) eller en falsk positiv (FP). Du kan derefter udføre anbefalede handlinger for TP-beskederne for at afhjælpe angrebene.

Du kan få et overblik over bedømmelsesbeskeder til Microsoft Defender Office 365 og Microsoft Defender til skyapps i [introduktionsartikel](alert-grading-playbooks.md).

Resultaterne af at bruge denne playbook er:

- Du har identificeret de beskeder, der er knyttet til automatisk videresendte mails, som ondsindede (TP) eller benignerede (FP) aktiviteter.

  Hvis ondsindet, har [du stoppet automatisk videresendelse af mail](../office-365-security/external-email-forwarding.md) for de pågældende postkasser.

- Du har taget de nødvendige skridt, hvis mails er blevet videresendt til en skadelig mailadresse.

## <a name="email-forwarding-rules"></a>Regler for videresendelse af mail

Regler for videresendelse af mail giver brugerne mulighed for at oprette en regel om videresendelse af mails, der sendes til en brugers postkasse, til en anden brugers postkasse i eller uden for organisationen. Nogle mailbrugere, især dem med flere postkasser, skal konfigurere videresendelsesregler for at flytte arbejdsgivermails til deres private mailkonti. Videresendelse af mail er en nyttig funktion, men kan også udgøre en sikkerhedsrisiko på grund af den potentielle offentliggørelse af oplysninger. Hackere kan bruge disse oplysninger til at angreb din organisation eller dennes partnere.

### <a name="suspicious-email-forwarding-activity"></a>Mistænkelig videresendelse af mail

Hackere kan oprette mailregler for at skjule indgående mails i den kompromitterede brugerpostkasse for at skjule deres ondsindede aktiviteter for brugeren. De kan også angive regler i den kompromitterede brugerpostkasse for at slette mails, flytte mails til en anden mindre synlig mappe, f.eks. en RSS-mappe, eller videresende mails til en ekstern konto.  

Nogle regler flytter muligvis alle mails til en anden mappe og markerer dem som "læst", mens nogle regler muligvis kun flytter mails, der indeholder bestemte nøgleord i mailen eller emnet. Indbakkereglen kan f.eks. være indstillet til at søge efter nøgleord som "faktura", "phish", "besvar ikke", "mistænkelig mail" eller "spam" blandt andre og flytte dem til en ekstern mailkonto. Hackere kan også bruge den kompromitterede brugerpostkasse til at distribuere spam, phishingmails eller malware.
 
Microsoft Defender for Office 365 kan registrere og advare på mistænkelige regler for videresendelse af mail, så du kan finde og slette skjulte regler ved kilden.

Du kan finde flere oplysninger i disse blogindlæg:

- [Kompromis med virksomhedsmail](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/business-email-uncompromised-part-one/ba-p/2159900)
- [Bag kulisserne for virksomhedsmailforlig: Brug af trusselsdata på tværs af domæner til at afbryde en stor BEC-kampagne](https://www.microsoft.com/security/blog/2021/06/14/behind-the-scenes-of-business-email-compromise-using-cross-domain-threat-data-to-disrupt-a-large-bec-infrastructure/)


## <a name="alert-details"></a>Beskeddetaljer

Hvis du vil gennemse beskeden om mistænkelig videresendelse af mail, skal du **åbne siden Vigtige beskeder** for at få **vist afsnittet Aktivitetsliste** . Her er et eksempel.
 
:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png" alt-text="Liste over aktiviteter, der er relateret til beskeden" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png":::

Vælg **Aktivitet**  for at få vist detaljerne for den pågældende aktivitet i sidepanelet. Her er et eksempel.
 
:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png" alt-text="Detaljer om aktiviteten" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png":::

Feltet **Årsag** indeholder følgende oplysninger, der er relateret til denne besked.

- Videresendelsestype (FT) er et af følgende:

    -  Exchange transportregel (ETR): Videresendt ved hjælp Exchange transportregel 

    -  SMTP: Videresendt ved hjælp af Videresendelse af postkasse

    -  Indbakkeregel: Videresendt ved hjælp af en indbakkeregel

- MTI (Message Trace ID): Dette er identifikatoren (NetworkMessageId) for den videresendte mail, der udløste denne besked. NetworkMessageId er den entydig identifier af en mail i organisationen.
- Videresender (F): Den bruger, der videresendte denne mail.
- Mistænkelig modtagerliste (SRL): Listen over modtagere blev betragtet som mistænkelig i denne mail.
- Modtagerliste ( RL): Listen over alle modtagerne i denne mail.

## <a name="investigation-workflow"></a>Undersøgelsesarbejdsproces

Mens du undersøger denne besked, skal du finde ud af, at:

- Er brugerkontoen og dens postkasse kompromitteret?
- Er aktiviteterne skadelige?

### <a name="is-the-user-account-and-its-mailbox-compromised"></a>Er brugerkontoen og dens postkasse kompromitteret?

Ved at se på afsenderens tidligere funktionsmåde og seneste aktiviteter bør du kunne afgøre, om brugerens konto skal betragtes som kompromitteret eller ej. Du kan se detaljerne for beskeder, der er hævet fra brugerens side, i Microsoft 365 Defender portal. 

Du kan også analysere disse yderligere aktiviteter for den pågældende postkasse:

- Brug Threat Explorer til at forstå mailrelaterede trusler

    - Se, hvor mange af de seneste mails, der er sendt af afsenderen, der registreres som phish, spam eller malware.

    - Se, hvor mange af de sendte mails der indeholder følsomme oplysninger. 

- Vurder risikabel logon-funktionsmåde i Microsoft Azure portal.
- Kontrollér for ondsindede aktiviteter på brugerens enhed.

### <a name="are-the-activities-malicious"></a>Er aktiviteterne skadelige?

Undersøg aktiviteten for videresendelse af mail. Kontrollér f.eks. typen af mail, modtageren af denne mail eller den måde, som mailen videresendes på. 

Du kan finde flere oplysninger i følgende artikler:

- [Indsigt i automatisk videresendte meddelelser](/microsoft-365/security/office-365-security/mfi-auto-forwarded-messages-report)
- [Nye brugere, der videresender mailindsigt](/microsoft-365/security/office-365-security/mfi-new-users-forwarding-email)
- [Besvare en kompromitteret mailkonto](/microsoft-365/security/office-365-security/responding-to-a-compromised-email-account)
- [Rapportér falske positive og falske negativer i Outlook](/microsoft-365/security/office-365-security/report-false-positives-and-false-negatives)

Her er arbejdsprocessen til at identificere mistænkelige videresendelsesaktiviteter for mail.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png" alt-text="Arbejdsproces for undersøgelse af beskeder om videresendelse af mail" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png":::

Du kan undersøge en besked om videresendelse af mail ved hjælp af Threat Explorer eller med avancerede forespørgselsforespørgsler baseret på tilgængeligheden af funktioner i Microsoft 365 Defender portal. Du kan vælge at følge hele processen eller en del af processen efter behov.

## <a name="using-threat-explorer"></a>Brug af Threat Explorer

Threat Explorer giver en interaktiv undersøgelsesoplevelse til mailrelaterede trusler for at afgøre, om denne aktivitet er mistænkelig eller ej. Du kan bruge følgende indikatorer fra beskedoplysningerne:

- SRL/RL: Brug listen over mistænkelige modtagere (SRL) til at finde disse oplysninger:
 
    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png" alt-text="Eksempel på listen over modtagere" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png":::

    - Who andet har videresendt mails til disse modtagere?

    - Hvor mange mails er blevet videresendt til disse modtagere?

    - Hvor ofte videresendes mails til disse modtagere?
 

- MTI: Brug meddelelsessporings-id'et/netværksmeddelelses-id'et til at finde disse oplysninger:

    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png" alt-text="Eksempel på netværksmeddelelses-id'et" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png":::

    - Hvilke yderligere oplysninger er tilgængelige for denne mail? Eksempel: emne, retursti og tidsstempel.

    - Hvad er oprindelsen af denne mail? Er der nogen lignende mails?

    - Indeholder denne mail nogen URL-adresser? Peger URL-adressen på nogen følsomme data?

    - Indeholder mailen nogen vedhæftede filer? Indeholder de vedhæftede filer følsomme oplysninger?

    - Hvad blev der gjort med mailen? Blev den slettet, markeret som læst eller flyttet til en anden mappe?

    - Er der nogen trusler i forbindelse med denne mail? Er denne mail en del af en kampagne?

Baseret på svar på disse spørgsmål, bør du kunne afgøre, om en mail er skadelig eller godartet.

## <a name="advanced-hunting-queries"></a>Avancerede forespørgselsforespørgsler

Hvis du vil [bruge avancerede søgeforespørgsler](advanced-hunting-overview.md) til at indsamle oplysninger, der er relateret til en besked og afgøre, om aktiviteten er mistænkelig, skal du sørge for, at du har adgang til følgende tabeller:

- EmailEvents – indeholder oplysninger, der er relateret til mailflow.

- EmailUrlInfo – indeholder oplysninger, der er relateret til URL-adresser i mails.

- CloudAppEvents – indeholder overvågningslog over brugeraktiviteter.

- IdentityLogonEvents – indeholder logonoplysninger for alle brugere.

>[!Note]
>Visse parametre er unikke for din organisation eller dit netværk. Udfyld disse specifikke parametre, som anvist i hver forespørgsel.
>

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

Kør denne forespørgsel for at finde ud af, om mailen indeholder url-adresser.
 
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

Kør denne forespørgsel for at finde ud af, om der var nogen unormale logonhændelser fra denne bruger. Eksempel: ukendte IP'er, nye programmer, ualmindelige lande, flere LogonFailed-hændelser.

```kusto
let sender = "{SENDER}"; //Replace {SENDER} with email of the Forwarder 
IdentityLogonEvents
| where AccountUpn == sender
```

### <a name="investigating-forwarding-rules"></a>Undersøger regler for videresendelse

Du kan også finde mistænkelige regler for videresendelse via Exchange Administration baseret på regeltypen (FT-værdien i beskeden).

- ETR 

  Exchange transportregler er angivet i **sektionen** Regler. Kontrollér, at alle regler er som forventet.

- SMTP

  Du kan se regler for videresendelse af postkasse ved at vælge afsenderens postkasse **\> Administrer indstillinger for mailflow Videresendelse \> Rediger.\>**

- IndbakkeRegel

  Indbakkeregler konfigureres med mailklienten. Du kan bruge [Get-InboxRule](/powershell/module/exchange/get-inboxrule) PowerShell-cmdlet'en til at få vist de indbakkeregler, der er oprettet af brugere.

### <a name="additional-investigation"></a>Yderligere undersøgelse

Sammen med de beviser, der indtil videre findes, kan du afgøre, om der oprettes nye regler for videresendelse. Undersøg den IP-adresse, der er knyttet til reglen. Sørg for, at det ikke er en unormal IP-adresse, og er i overensstemmelse med de sædvanlige aktiviteter, der udføres af brugeren.

## <a name="recommended-actions"></a>Anbefalede handlinger

Når du har afgøret, om de aktiviteter, der er knyttet til denne påmindelse, er sand positiv, skal du klassificere beskeden og udføre disse handlinger for at afhjælpe problemet:

1. Deaktiver og slet reglen for videresendelse af indbakke.
2. For videresendelsestypen Indbakkeregel skal du nulstille brugerens kontolegitimationsoplysninger.
3. For videresendelsestypen SMTP eller ETR skal du undersøge aktiviteterne for den brugerkonto, der oprettede beskeden.

    - Undersøg alle andre mistænkelige administratoraktiviteter.

    - Nulstil brugerkontoens legitimationsoplysninger.

4. Kontrollér for yderligere aktiviteter, der stammer fra på påvirkede konti, IP-adresser og mistænkelige afsendere.

## <a name="see-also"></a>Se også

- [Oversigt over bedømmelse af beskeder](alert-grading-playbooks.md)
- [Mistænkelige regler for videresendelse af indbakke](alert-grading-playbook-inbox-forwarding-rules.md)
- [Regler for mistænkelig indbakkemanipulation](alert-grading-playbook-inbox-manipulation-rules.md)
- [Undersøg beskeder](investigate-alerts.md)
