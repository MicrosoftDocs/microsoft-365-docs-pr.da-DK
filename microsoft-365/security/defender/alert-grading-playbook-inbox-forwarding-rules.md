---
title: Besked om karakterer for mistænkelige regler for videresendelse af indbakke
description: Giv besked om karakterer for mistænkelige videresendelsesregler for indbakker for at gennemgå beskederne og foretage anbefalede handlinger for at afhjælpe angrebene og beskytte dit netværk.
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
ms.openlocfilehash: 08178a1672e3bdd5b124138f698b42be8181373a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594136"
---
# <a name="alert-grading-for-suspicious-inbox-forwarding-rules"></a>Besked om karakterer for mistænkelige regler for videresendelse af indbakke

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Trusselsbrugere kan bruge kompromitterede brugerkonti til flere ondsindede formål, herunder at læse mails i en brugers indbakke, oprette indbakkeregler for at videresende mails til eksterne konti, sende phishingmails blandt andre. Ondsindede indbakkeregler er meget almindelige i forbindelse med BEC-kampagner (Business Email Compromise) og phishing, og det er vigtigt at holde øje med dem på en ensartet måde.

Denne playbook hjælper dig med at undersøge beskeder om mistænkelige regler for videresendelse af indbakker og hurtigt give dem karakterer som enten en Sand positiv (TP) eller en falsk positiv (TP). Du kan derefter udføre anbefalede handlinger for TP-beskederne for at afhjælpe angrebene. 

Du kan få et overblik over bedømmelsesbeskeder til Microsoft Defender Office 365 og Microsoft Defender til skyapps i [introduktionsartikel](alert-grading-playbooks.md).

Resultaterne af at bruge denne playbook er:

- Du har identificeret de beskeder, der er knyttet til regler for videresendelse af indbakke, som skadelige (TP) eller benignerende aktiviteter (FP).

  Hvis skadelig, har du fjernet regler for videresendelse af skadelig indbakke.

- Du har taget de nødvendige skridt, hvis mails er blevet videresendt til en skadelig mailadresse.

## <a name="inbox-forwarding-rules"></a>Regler for videresendelse af indbakke

Du kan konfigurere indbakkeregler til automatisk at administrere mails baseret på foruddefinerede kriterier. Du kan f.eks. oprette en indbakkeregel for at flytte alle meddelelser fra din chef til en anden mappe eller videresende meddelelser, du modtager til en anden mailadresse.

### <a name="suspicious-inbox-forwarding-rules"></a>Mistænkelige regler for videresendelse af indbakke

Efter at have få adgang til brugernes postkasser opretter hackere ofte en indbakkeregel, der giver dem mulighed for at eksfiltrere følsomme data til en ekstern mailadresse og bruge den til ondsindede formål. 

Ondsindede indbakkeregler automatiserer udfyldningsprocessen. Med specifikke regler vil alle mails i målbrugerens indbakke, der opfylder reglens kriterier, blive videresendt til hackerens postkasse. En hacker kan f.eks. ønske at indsamle følsomme data relateret til finans. De opretter en indbakkeregel for at videresende alle mails, der indeholder nøgleord, f.eks. "finans" og "faktura" i emne- eller meddelelsesteksten, til deres postkasse.

Mistænkelige regler for videresendelse af indbakke kan være meget svære at registrere, fordi vedligeholdelse af indbakkeregler er en almindelig opgave udført af brugerne. Det er derfor vigtigt at overvåge beskederne. 

## <a name="workflow"></a>Arbejdsproces

Her er arbejdsprocessen til at identificere mistænkelige regler for videresendelse af mail.
 
:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png" alt-text="Arbejdsproces for undersøgelse af beskeder om videresendelsesregler for indbakke" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png":::

## <a name="investigation-steps"></a>Undersøgelsestrin

Dette afsnit indeholder en detaljeret trinvis vejledning til at reagere på hændelsen og tage de anbefalede trin for at beskytte din organisation mod yderligere angreb.

### <a name="review-generated-alerts"></a>Gennemse genererede beskeder

Her er et eksempel på en besked om videresendelsesregel for indbakken i beskedkøen.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png" alt-text="Eksempel på en meddelelse i beskedkøen" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png":::

Her er et eksempel på oplysninger om den besked, der blev udløst af en regel for videresendelse af skadelig indbakke.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png" alt-text="Detaljer for påmindelse, der blev udløst af en regel for videresendelse af skadelig indbakke" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png":::

### <a name="investigate-rule-parameters"></a>Undersøg regelparametre 

Formålet med denne fase er at afgøre, om reglerne ser mistænkelige ud fra bestemte kriterier:

Modtagere af reglen for videresendelse:

- Valider destinationsmailadressen er ikke en ekstra postkasse, der ejes af den samme bruger (og undgår tilfælde, hvor brugeren selv videresender mails mellem personlige postkasser). 
- Valider, at destinationsmailadressen ikke er en intern adresse eller et underdomæne, der tilhører virksomheden.

Filtre:
 
- Hvis indbakkereglen indeholder filtre, som søger efter bestemte nøgleord i mailens emne eller brødtekst, skal du kontrollere, om de angivne nøgleord, f.eks. økonomi, legitimationsoplysninger og netværk, blandt andre, virker relateret til ondsindet aktivitet. Du kan finde disse filtre under følgende attributter (som vises i kolonnen RawEventData): "BodyContainsWords", "SubjectContainsWords" eller "SubjectOrKaryContainsWords"
- Hvis hackeren vælger ikke at indstille et filter til mails, og indbakkereglen i stedet videresender alle postkasseelementer til hackerens postkasse, så er denne funktionsmåde også mistænkelig. 

### <a name="investigate-ip-address"></a>Undersøg IP-adresse

Gennemgå de attributter, der er relateret til den IP-adresse, der udførte den relevante hændelse for oprettelse af regler:

1. Søg efter andre mistænkelige skyaktiviteter, der stammer fra den samme IP i lejeren. Mistænkelig aktivitet kan f.eks. være flere mislykkede logonforsøg. 
2. Er internetudbyderen fælles og rimelig for denne bruger?
3. Er placeringen fælles og rimelig for denne bruger?

### <a name="investigate-any-suspicious-activity-with-the-user-inbox-before-creating-rules"></a>Undersøg eventuelle mistænkelige aktiviteter med brugerens indbakke, før du opretter regler

Du kan gennemse alle brugeraktiviteter, før du opretter regler, se efter indikatorer for kompromis og undersøge brugerhandlinger, der virker mistænkelige. For eksempel flere mislykkede logons.  

- Log på: 

  Valider, at logonaktiviteten før hændelsen til oprettelse af reglen ikke er mistænkelig (f.eks. den almindelige placering, internetudbyderen eller brugeragenten). 

- Andre beskeder eller hændelser 

   - Udløste andre beskeder for brugeren, før reglen blev oprettet. Hvis det er ja, kan dette indikere, at brugeren er blevet kompromitteret. 

   - Hvis beskeden korrelerer med andre beskeder for at angive en hændelse, indeholder hændelsen så andre egentlige positive beskeder? 

## <a name="advanced-hunting-queries"></a>Avancerede forespørgselsforespørgsler

[Avanceret jagt](advanced-hunting-overview.md) er et forespørgselsbaseret værktøj til trusselssøgning, som gør det muligt at undersøge hændelser i dit netværk og finde trusselsindikatorer. 

Kør denne forespørgsel for at finde alle de nye indbakkeregelhændelser i løbet af en bestemt periode.  

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

*RuleConfig indeholder* regelkonfigurationen.

Kør denne forespørgsel for at kontrollere, om internetudbyderen er almindelig for brugeren, ved at se på historikken for brugeren.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 30d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP 
```

Kør denne forespørgsel for at kontrollere, om landet er almindeligt for brugeren, ved at se på historikken for brugeren.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 30d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

Kør denne forespørgsel for at kontrollere, om brugeragenten er fælles for brugeren, ved at se på historikken for brugeren.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 30d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by UserAgent
```

Kør denne forespørgsel for at kontrollere, om andre brugere har oprettet reglen videresendelse til den samme destination (kan betyde, at andre brugere også er blevet kompromitteret).

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

1. Deaktiver reglen om skadelig indbakke. 
2. Nulstil brugerens legitimationsoplysninger. Du kan også kontrollere, om brugerkontoen er blevet kompromitteret med Microsoft Defender til skyapps, som får sikkerhedssignaler fra Azure Active Directory (Azure AD) Identity Protection.
3. Søg efter andre ondsindede aktiviteter, der udføres af den på hinanden følgende bruger.
4. Kontrollér for andre mistænkelige aktiviteter i lejeren stammer fra den samme IP eller fra den samme internetudbyder (hvis internetudbyderen er ualmindeligt) for at finde andre kompromitterede brugere.

## <a name="see-also"></a>Se også

- [Oversigt over bedømmelse af beskeder](alert-grading-playbooks.md)
- [Mistænkelig videresendelse af mail](alert-grading-playbook-email-forwarding.md)
- [Regler for mistænkelig indbakkemanipulation](alert-grading-playbook-inbox-manipulation-rules.md)
- [Undersøg beskeder](investigate-alerts.md)
