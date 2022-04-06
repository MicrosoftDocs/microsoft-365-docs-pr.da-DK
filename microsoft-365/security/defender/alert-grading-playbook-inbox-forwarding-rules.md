---
title: Beskedklassering for mistænkelige regler for videresendelse af indbakker
description: Beskedklassering for mistænkelige regler for videresendelse af indbakker for at gennemse beskederne og udføre anbefalede handlinger for at afhjælpe angrebet og beskytte dit netværk.
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
ms.openlocfilehash: dca305b88e6e8db25e0a798c4361086bd7cb1e8b
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666014"
---
# <a name="alert-grading-for-suspicious-inbox-forwarding-rules"></a>Beskedklassering for mistænkelige regler for videresendelse af indbakker

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Trusselsaktører kan bruge kompromitterede brugerkonti til flere skadelige formål, herunder at læse mails i en brugers indbakke, oprette indbakkeregler for at videresende mails til eksterne konti, bl.a. sende phishing-mails. Reglerne for ondsindede indbakker er meget almindelige i forbindelse med BEC (Business Email Compromise) og phishingkampagner, og det er vigtigt at overvåge dem på en ensartet måde.

Denne playbook hjælper dig med at undersøge beskeder for mistænkelige regler for videresendelse af indbakker og hurtigt bedømme dem som enten en sand positiv (TP) eller en falsk positiv (TP). Du kan derefter udføre anbefalede handlinger for TP-beskederne for at afhjælpe angrebet.

Du kan få en oversigt over beskedklassering for Microsoft Defender for Office 365 og Microsoft Defender for Cloud Apps i [introduktionsartiklen](alert-grading-playbooks.md).

Resultaterne af at bruge denne playbook er:

- Du har identificeret de beskeder, der er knyttet til reglerne for videresendelse af indbakker, som skadelige aktiviteter (TP) eller godartede aktiviteter (FP).

  Hvis det er skadeligt, har du fjernet reglerne for videresendelse af skadelig indbakke.

- Du har foretaget den nødvendige handling, hvis mails er blevet videresendt til en ondsindet mailadresse.

## <a name="inbox-forwarding-rules"></a>Regler for videresendelse af indbakke

Du kan konfigurere indbakkeregler til automatisk at administrere mails baseret på foruddefinerede kriterier. Du kan f.eks. oprette en indbakkeregel for at flytte alle meddelelser fra din chef til en anden mappe eller videresende meddelelser, du modtager, til en anden mailadresse.

### <a name="suspicious-inbox-forwarding-rules"></a>Mistænkelige regler for videresendelse af indbakke

Når angribere har fået adgang til brugernes postkasser, opretter de ofte en indbakkeregel, der giver dem mulighed for at exfiltrere følsomme data til en ekstern mailadresse og bruge dem til skadelige formål.

Regler for skadelig indbakke automatiserer exfiltrationsprocessen. Med specifikke regler videresendes alle mails i målbrugerens indbakke, der opfylder regelkriterierne, til hackerens postkasse. En hacker kan f.eks. indsamle følsomme data, der er relateret til økonomi. De opretter en indbakkeregel for at videresende alle mails, der indeholder nøgleord, f.eks. "økonomi" og "faktura" i emne- eller meddelelsesteksten, til deres postkasse.

Mistænkelige regler for videresendelse af indbakker kan være meget vanskelige at registrere, fordi vedligeholdelse af indbakkeregler er en almindelig opgave, som brugerne udfører. Det er derfor vigtigt at overvåge beskederne.

## <a name="workflow"></a>Arbejdsproces

Her er arbejdsprocessen til at identificere mistænkelige regler for videresendelse af mail.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png" alt-text="Arbejdsproces til undersøgelse af beskeder om regler for videresendelse af indbakke" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png":::

## <a name="investigation-steps"></a>Undersøgelsestrin

Dette afsnit indeholder en detaljeret trinvis vejledning i, hvordan du reagerer på hændelsen og udfører de anbefalede trin for at beskytte din organisation mod yderligere angreb.

### <a name="review-generated-alerts"></a>Gennemse genererede beskeder

Her er et eksempel på en regelbesked om videresendelse af indbakke i beskedkøen.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png" alt-text="Eksempel på en meddelelse i beskedkøen" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png":::

Her er et eksempel på detaljer om den besked, der blev udløst af en regel for videresendelse af skadelig indbakke.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png" alt-text="Oplysninger om besked, der blev udløst af en regel for videresendelse af skadelig indbakke" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png":::

### <a name="investigate-rule-parameters"></a>Undersøg regelparametre

Formålet med denne fase er at afgøre, om reglerne ser mistænkelige ud af visse kriterier:

Modtagere af videresendelsesreglen:

- Valider, at destinationsmailadressen ikke er en ekstra postkasse, der ejes af den samme bruger (undgå tilfælde, hvor brugeren selv videresender mails mellem personlige postkasser).
- Valider, at destinationsmailadressen ikke er en intern adresse eller et underdomæne, der tilhører virksomheden.

Filtre:

- Hvis indbakkereglen indeholder filtre, der søger efter bestemte nøgleord i mailens emne eller brødtekst, skal du kontrollere, om de angivne nøgleord, f.eks. økonomi, legitimationsoplysninger og netværk, bl.a. synes relateret til ondsindet aktivitet. Du kan finde disse filtre under følgende attributter (som vises i kolonnen RawEventData for hændelsen): "BodyContainsWords", "SubjectContainsWords" eller "SubjectOrBodyContainsWords"
- Hvis hackeren vælger ikke at angive et filter til mails, og i stedet indbakkereglen videresender alle postkasseelementerne til hackerens postkasse), er denne funktionsmåde også mistænkelig.

### <a name="investigate-ip-address"></a>Undersøg IP-adresse

Gennemse de attributter, der er relateret til den IP-adresse, der udførte den relevante hændelse for regeloprettelse:

1. Søg efter andre mistænkelige cloudaktiviteter, der stammer fra den samme IP-adresse i lejeren. Mistænkelig aktivitet kan f.eks. være flere mislykkede logonforsøg.
2. Er internetudbyderen almindelig og rimelig for denne bruger?
3. Er placeringen fælles og rimelig for denne bruger?

### <a name="investigate-any-suspicious-activity-with-the-user-inbox-before-creating-rules"></a>Undersøg enhver mistænkelig aktivitet med brugerens indbakke, før du opretter regler

Du kan gennemse alle brugeraktiviteter, før du opretter regler, kontrollere, om der er indikatorer for kompromitteret handling, og undersøge brugerhandlinger, der virker mistænkelige. Det kan f.eks. være flere mislykkede logons.

- Logon:

  Valider, at logonaktiviteten før regeloprettelseshændelsen ikke er mistænkelig (f.eks. den fælles placering, internetudbyderen eller brugeragenten).

- Andre beskeder eller hændelser
  - Udløste andre beskeder for brugeren før oprettelsen af reglen. Hvis det er tilfældet, kan dette indikere, at brugeren blev kompromitteret.
  - Hvis beskeden korrelerer med andre beskeder for at angive en hændelse, indeholder hændelsen så andre sande positive beskeder?

## <a name="advanced-hunting-queries"></a>Avancerede jagtforespørgsler

[Advanced Hunting](advanced-hunting-overview.md) er et forespørgselsbaseret trussels jagtværktøj, der giver dig mulighed for at inspicere hændelser i dit netværk og finde trusselsindikatorer.

Kør denne forespørgsel for at finde alle de nye hændelser for indbakkereglen i et bestemt tidsrum.

```kusto
let start_date = now(-10h);
let end_date = now();
let user_id = ""; // enter here the user id
CloudAppEvents
| where Timestamp between (start_date .. end_date)
| where AccountObjectId == user_id
| where Application == @"Microsoft Exchange Online"
| where ActionType in ("Set-Mailbox", "New-InboxRule", "Set-InboxRule") //set new inbox rule related operations
| project Timestamp, ActionType, CountryCode, City, ISP, IPAddress, RuleConfig = RawEventData.Parameters, RawEventData
```

*RuleConfig* indeholder regelkonfigurationen.

Kør denne forespørgsel for at kontrollere, om internetudbyderen er fælles for brugeren, ved at se på brugerens historik.

```kusto
let alert_date = now(); //enter alert date
let timeback = 30d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP
```

Kør denne forespørgsel for at kontrollere, om landet er almindeligt for brugeren, ved at se på brugerens historik.

```kusto
let alert_date = now(); //enter alert date
let timeback = 30d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

Kør denne forespørgsel for at kontrollere, om brugeragenten er fælles for brugeren, ved at se på brugerhistorikken.

```kusto
let alert_date = now(); //enter alert date
let timeback = 30d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by UserAgent
```

Kør denne forespørgsel for at kontrollere, om andre brugere har oprettet en videresendelsesregel til den samme destination (det kan også indikere, at andre brugere er kompromitteret).

```kusto
let start_date = now(-10h);
let end_date = now();
let dest_email = ""; // enter here destination email as seen in the alert
CloudAppEvents
| where Timestamp between (start_date .. end_date)
| where ActionType in ("Set-Mailbox", "New-InboxRule", "Set-InboxRule") //set new inbox rule related operations
| project Timestamp, ActionType, CountryCode, City, ISP, IPAddress, RuleConfig = RawEventData.Parameters, RawEventData
| where RuleConfig has dest_email
```

## <a name="recommended-actions"></a>Anbefalede handlinger

1. Deaktiver reglen for skadelig indbakke.
2. Nulstil brugerens legitimationsoplysninger. Du kan også kontrollere, om brugerkontoen er blevet kompromitteret med Microsoft Defender for Cloud Apps, hvilket henter sikkerhedssignaler fra Azure Active Directory (Azure AD) Identity Protection.
3. Søg efter andre skadelige aktiviteter, der udføres af den påvirkede bruger.
4. Kontrollér, om der er andre mistænkelige aktiviteter i lejeren, der stammer fra den samme IP-adresse eller fra den samme internetudbyder (hvis internetudbyderen er ualmindelig) for at finde andre kompromitterede brugere.

## <a name="see-also"></a>Se også

- [Oversigt over beskedklassering](alert-grading-playbooks.md)
- [Mistænkelig aktivitet for videresendelse af mail](alert-grading-playbook-email-forwarding.md)
- [Regler for mistænkelig manipulation af indbakke](alert-grading-playbook-inbox-manipulation-rules.md)
- [Undersøg beskeder](investigate-alerts.md)
