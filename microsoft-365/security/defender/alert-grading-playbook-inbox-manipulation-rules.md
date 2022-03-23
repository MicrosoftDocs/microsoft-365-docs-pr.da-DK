---
title: Besked om karakterer for mistænkelige regler for indbakkemanipulation
description: Giv karakterer for mistænkelige regler for indbakkemanipulation for at gennemgå beskederne og foretage anbefalede handlinger for at afhjælpe angrebene og beskytte dit netværk.
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
ms.openlocfilehash: 89d068feb5051a72e7592b7ea365b2e253e35115
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593688"
---
# <a name="alert-grading-for-suspicious-inbox-manipulation-rules"></a>Besked om karakterer for mistænkelige regler for indbakkemanipulation

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Trusselsbrugere kan bruge kompromitterede brugerkonti til mange ondsindede formål, herunder at læse mails i en brugers indbakke, oprette indbakkeregler for at videresende mails til eksterne konti, slette sporinger og sende phishingmails. Ondsindede indbakkeregler er almindelige i forbindelse med BEC (Business Email Compromise) og phishingkampagner, og det er vigtigt at holde øje med dem på en ensartet måde. 

Denne playbook hjælper dig med at undersøge enhver hændelse, der er relateret til manipulationsregler for mistænkelig indbakke, som er konfigureret af hackere, og tage anbefalede handlinger for at afhjælpe angrebene og beskytte dit netværk. Denne playbook er til sikkerhedsteams, herunder SOC-analytikere (Security Operations Center) og it-administratorer, som gennemser, undersøger og vurderer beskederne. Du kan hurtigt give beskeder karakterer som enten en sand positiv (TP) eller en falsk positiv (TP) og foretage anbefalede handlinger til TP-beskederne for at afhjælpe angrebene. 

Resultaterne af at bruge denne playbook er:

- Du har identificeret de beskeder, der er knyttet til regler for indbakkemanipulation som skadelige (TP) eller benignere (FP) aktiviteter.

  Hvis skadelig, har du fjernet regler for manipulation af skadelig indbakke.

- Du har taget de nødvendige skridt, hvis mails er blevet videresendt til en skadelig mailadresse.

## <a name="inbox-manipulation-rules"></a>Regler for indbakkemanipulation

Indbakkeregler er indstillet til automatisk at administrere mails baseret på foruddefinerede kriterier. Du kan f.eks. oprette en indbakkeregel for at flytte alle meddelelser fra din chef til en anden mappe eller videresende meddelelser, du modtager til en anden mailadresse.

### <a name="malicious-inbox-manipulation-rules"></a>Skadelige regler for indbakkemanipulation

Hackere kan oprette mailregler for at skjule indgående mails i den kompromitterede brugerpostkasse for at skjule deres ondsindede aktiviteter for brugeren. De kan også angive regler i den kompromitterede brugerpostkasse for at slette mails, flytte mails til en anden mindre synlig mappe (f.eks. RSS) eller videresende mails til en ekstern konto. Nogle regler flytter muligvis alle mails til en anden mappe og markerer dem som "læst", mens nogle regler muligvis kun flytter mails, der indeholder bestemte nøgleord i mailen eller emnet. 

Indbakkereglen kan f.eks. være indstillet til at søge efter nøgleord som "faktura", "phish", "besvar ikke", "mistænkelig mail" eller "spam" blandt andre og flytte dem til en ekstern mailkonto. Hackere kan også bruge den kompromitterede brugerpostkasse til at distribuere spam, phishingmails eller malware. 

## <a name="workflow"></a>Arbejdsproces

Her er arbejdsprocessen til at identificere mistænkelige manipulationsregelaktiviteter for indbakke.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png" alt-text="Arbejdsproces for undersøgelse af beskeder om regler for indbakkemanipulation" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png":::


## <a name="investigation-steps"></a>Undersøgelsestrin

Dette afsnit indeholder en detaljeret trinvis vejledning til at reagere på hændelsen og tage de anbefalede trin for at beskytte din organisation mod yderligere angreb.

### <a name="1-review-the-alerts"></a>1. Gennemse beskederne

Her er et eksempel på en påmindelse om en indbakkemanipulationsregel i beskedkøen.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png" alt-text="Eksempel på en regel for manipulation af indbakken" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png":::

Her er et eksempel på detaljerne i en besked, der blev udløst af en regel for ondsindet manipulation i indbakken.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png" alt-text="Detaljer for påmindelse, der blev udløst af en regel for manipulation af skadelig indbakke" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png":::


### <a name="2-investigate-inbox-manipulation-rule-parameters"></a>2. Undersøg parametre for indbakkemanipulationsregel 

Afgør, om reglerne ser mistænkelige ud i henhold til følgende regelparametre eller kriterier:

- Nøgleord

   Hackeren kan kun anvende manipulationsreglen på mails, der indeholder bestemte ord. Du kan finde disse nøgleord under bestemte attributter, f.eks.: "BodyContainsWords", "SubjectContainsWords" eller "SubjectOrWordsyContainsWords". 

   Hvis der filtreres efter nøgleord, skal du kontrollere, om nøgleordene virker mistænkelige for dig (almindelige scenarier er at filtrere mails, der er relateret til hackeraktiviteterne, f.eks. "phish", "spam", "svarer ikke" blandt andre).

   Hvis der slet ikke er noget filter, kan det også være mistænkeligt.

- Destinationsmappe

   For at undgå sikkerhedsregistrering kan hackeren flytte mails til en mappe, der er mindre synlig, og markere mails som læst (f.eks. mappen "RSS"). Hvis hackeren anvender handlingen "MoveToFolder" og "MarkAsRead", skal du kontrollere, om destinationsmappen er relateret til nøgleordene i reglen for at afgøre, om den virker mistænkelig eller ej. 

- Slet alle

   Nogle hackere vil bare slette alle de indgående mails for at skjule deres aktivitet. For det meste er en regel med "slet alle indgående mails" uden at filtrere dem med nøgleord en indikator for ondsindet aktivitet. 
 
Her er et eksempel på en regelkonfiguration med "Slet alle indgående mails" (som det fremgår af RawEventData.Parameters) for den relevante hændelseslog. 

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png" alt-text="Eksempel på en regelkonfiguration til sletning af alle indgående mails" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png":::


### <a name="3-investigate-the-ip-address"></a>3. Undersøg IP-adressen

Gennemse attributterne for den IP-adresse, der udførte den relevante hændelse for oprettelse af regler:

- Søg efter andre mistænkelige skyaktiviteter, der stammer fra den samme IP i lejeren. Mistænkelig aktivitet kan f.eks. være flere mislykkede logonforsøg. 
- Er internetudbyderen fælles og rimelig for denne bruger?
- Er placeringen fælles og rimelig for denne bruger?

### <a name="4-investigate-suspicious-activity-by-the-user-prior-to-creating-the-rules"></a>4. Undersøg mistænkelig aktivitet fra brugeren, før reglerne oprettes

Du kan gennemse alle brugeraktiviteter, før reglerne blev oprettet, se efter indikatorer for kompromis og undersøge brugerhandlinger, der virker mistænkelige. 

Eksempelvis skal du undersøge følgende for flere mislykkede logons: 

- Logonaktivitet 

   Valider, at logonaktiviteten før oprettelsen af reglen ikke er mistænkelig. (almindeligt sted/internetudbyder/brugeragent). 

- Beskeder

   Kontrollér, om brugeren har modtaget beskeder, før reglerne oprettes. Dette kan betyde, at brugerkontoen kan være kompromitteret. Eksempelvis en umulig rejseadvarsel, sjælden land, flere mislykkede logons blandt andre.)

- Hændelse

   Kontrollér, om beskeden er knyttet til andre beskeder, der angiver en hændelse. Hvis det er tilfældet, skal du kontrollere, om hændelsen indeholder andre reelle positive beskeder.

## <a name="advanced-hunting-queries"></a>Avancerede forespørgselsforespørgsler

[Avanceret jagt](advanced-hunting-overview.md) er et forespørgselsbaseret værktøj til trusselssøgning, som gør det muligt at undersøge hændelser i dit netværk for at finde trusselsindikatorer. 

Brug denne forespørgsel til at finde alle de nye indbakkeregelhændelser i løbet af en bestemt periode.  

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

Kolonnen *RuleConfig* leverer konfigurationen af den nye indbakkeregel.

Brug denne forespørgsel til at kontrollere, om internetudbyderen er almindelig for brugeren, ved at se på historikken for brugeren.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 60d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP 
```

Brug denne forespørgsel til at kontrollere, om landet er almindeligt for brugeren, ved at se på historikken for brugeren.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 60d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

Brug denne forespørgsel til at kontrollere, om brugeragenten er fælles for brugeren, ved at se på historikken for brugeren.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 60d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by UserAgent
```

## <a name="recommended-actions"></a>Anbefalede handlinger

1. Deaktiver reglen om skadelig indbakke.
2. Nulstil brugerkontoens legitimationsoplysninger. Du kan også kontrollere, om brugerkontoen er blevet kompromitteret med Microsoft Defender til skyapps, som får sikkerhedssignaler fra Azure Active Directory (Azure AD) Identity Protection.
3. Søg efter andre ondsindede aktiviteter, der udføres af den på påvirkede brugerkonto.
4. Kontrollér for andre mistænkelige aktiviteter i lejeren, der stammer fra den samme IP eller fra den samme internetudbyder (hvis internetudbyderen er ualmindeligt) for at finde andre kompromitterede brugerkonti.

## <a name="see-also"></a>Se også

- [Oversigt over bedømmelse af beskeder](alert-grading-playbooks.md)
- [Mistænkelig videresendelse af mail](alert-grading-playbook-email-forwarding.md)
- [Mistænkelige regler for videresendelse af indbakke](alert-grading-playbook-inbox-forwarding-rules.md)
- [Undersøg beskeder](investigate-alerts.md)
