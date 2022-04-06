---
title: Beskedklassering for mistænkelige regler for manipulation af indbakker
description: Klassificering af beskeder for mistænkelige regler for manipulation af indbakker for at gennemse beskederne og udføre anbefalede handlinger for at afhjælpe angrebet og beskytte dit netværk.
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
ms.openlocfilehash: e663d02037633599b9dffc19e1ebbd174aa279e1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663176"
---
# <a name="alert-grading-for-suspicious-inbox-manipulation-rules"></a>Beskedklassering for mistænkelige regler for manipulation af indbakker

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Trusselsaktører kan bruge kompromitterede brugerkonti til mange skadelige formål, herunder at læse mails i en brugers indbakke, oprette indbakkeregler for at videresende mails til eksterne konti, slette sporinger og sende phishing-mails. Ondsindede indbakkeregler er almindelige i forbindelse med BEC (Business Email Compromise) og phishing-kampagner, og det er vigtigt at overvåge dem på en ensartet måde.

Denne playbook hjælper dig med at undersøge enhver hændelse, der er relateret til mistænkelige regler for manipulation af indbakker, som er konfigureret af hackere, og udføre anbefalede handlinger for at afhjælpe angrebet og beskytte dit netværk. Denne strategiplan er til sikkerhedsteams, herunder SOC-analytikere (Security Operations Center) og it-administratorer, der gennemser, undersøger og karakterer beskederne. Du kan hurtigt bedømme beskeder som enten en sand positiv (TP) eller en falsk positiv (TP) og udføre anbefalede handlinger for TP-beskederne for at afhjælpe angrebet.

Resultaterne af at bruge denne playbook er:

- Du har identificeret de beskeder, der er knyttet til regler for indbakkemanipulation, som skadelige aktiviteter (TP) eller godartede aktiviteter (FP).

  Hvis det er skadeligt, har du fjernet regler for manipulation af ondsindede indbakker.

- Du har foretaget den nødvendige handling, hvis mails er blevet videresendt til en ondsindet mailadresse.

## <a name="inbox-manipulation-rules"></a>Regler for manipulation af indbakke

Indbakkeregler er indstillet til automatisk at administrere mails baseret på foruddefinerede kriterier. Du kan f.eks. oprette en indbakkeregel for at flytte alle meddelelser fra din chef til en anden mappe eller videresende meddelelser, du modtager, til en anden mailadresse.

### <a name="malicious-inbox-manipulation-rules"></a>Regler for manipulation af skadelig indbakke

Personer med ondsindede hensigter kan konfigurere mailregler for at skjule indgående mails i den kompromitterede brugerpostkasse for at skjule deres skadelige aktiviteter for brugeren. De kan også angive regler i den kompromitterede brugerpostkasse for at slette mails, flytte mails til en anden mindre mærkbar mappe (f.eks. RSS) eller videresende mails til en ekstern konto. Nogle regler kan flytte alle mails til en anden mappe og markere dem som "læst", mens nogle regler muligvis kun flytter mails, der indeholder bestemte nøgleord i mailen eller emnet.

Indbakkereglen kan f.eks. være angivet til at søge efter nøgleord som "faktura", "phish", "besvar ikke", "mistænkelig mail" eller "spam" blandt andre og flytte dem til en ekstern mailkonto. Personer med ondsindede hensigter kan også bruge den kompromitterede brugerpostkasse til at distribuere spam, phishing-mails eller malware.

## <a name="workflow"></a>Arbejdsproces

Her er arbejdsprocessen til at identificere aktiviteter med regler for mistænkelig indbakkemanipulation.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png" alt-text="Arbejdsproces til undersøgelse af beskeder om regler for manipulation af indbakke" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png":::

## <a name="investigation-steps"></a>Undersøgelsestrin

Dette afsnit indeholder en detaljeret trinvis vejledning i, hvordan du reagerer på hændelsen og udfører de anbefalede trin for at beskytte din organisation mod yderligere angreb.

### <a name="1-review-the-alerts"></a>1. Gennemse beskederne

Her er et eksempel på en regelbesked om manipulation af indbakker i beskedkøen.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png" alt-text="Eksempel på en regel for manipulation af indbakke" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png":::

Her er et eksempel på detaljerne for en besked, der blev udløst af en regel for manipulation af ondsindede indbakker.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png" alt-text="Detaljer om besked, der blev udløst af en regel for manipulation af ondsindede indbakker" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png":::

### <a name="2-investigate-inbox-manipulation-rule-parameters"></a>2. Undersøg regelparametre for indbakkemanipulation

Find ud af, om reglerne ser mistænkelige ud i henhold til følgende regelparametre eller kriterier:

- Søgeord

   Hackeren anvender muligvis kun manipulationsreglen på mails, der indeholder bestemte ord. Du kan finde disse nøgleord under visse attributter, f.eks.: "BodyContainsWords", "SubjectContainsWords" eller "SubjectOrBodyContainsWords".

   Hvis der er filtrering efter nøgleord, skal du kontrollere, om nøgleordene virker mistænkelige for dig (almindelige scenarier er at filtrere mails, der er relateret til hackeraktiviteter, f.eks. "phish", "spam", "svar ikke", blandt andre).

   Hvis der slet ikke er noget filter, kan det også være mistænkeligt.

- Destinationsmappen

   For at undgå sikkerhedsregistrering kan hackeren flytte mails til en mindre mærkbar mappe og markere mails som læst (f.eks. "RSS"-mappen). Hvis hackeren anvender handlingen "MoveToFolder" og "MarkAsRead", skal du kontrollere, om destinationsmappen på en eller anden måde er relateret til nøgleordene i reglen, for at afgøre, om den virker mistænkelig eller ej.

- Slet alle

   Nogle personer med ondsindede hensigter sletter blot alle indgående mails for at skjule deres aktivitet. For det meste er en regel om "slet alle indgående mails" uden at filtrere dem med nøgleord en indikator for ondsindet aktivitet.

Her er et eksempel på regelkonfigurationen "Slet alle indgående mails" (som vist på RawEventData.Parameters) for den relevante hændelseslog.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png" alt-text="Eksempel på konfiguration af regel for sletning af alle indgående mails" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png":::

### <a name="3-investigate-the-ip-address"></a>3. Undersøg IP-adressen

Gennemse attributterne for den IP-adresse, der udførte den relevante hændelse for regeloprettelse:

- Søg efter andre mistænkelige cloudaktiviteter, der stammer fra den samme IP-adresse i lejeren. Mistænkelig aktivitet kan f.eks. være flere mislykkede logonforsøg.
- Er internetudbyderen almindelig og rimelig for denne bruger?
- Er placeringen fælles og rimelig for denne bruger?

### <a name="4-investigate-suspicious-activity-by-the-user-prior-to-creating-the-rules"></a>4. Undersøg mistænkelig aktivitet fra brugeren, før reglerne oprettes

Du kan gennemse alle brugeraktiviteter, før der blev oprettet regler, kontrollere, om der er indikatorer for kompromis, og undersøge brugerhandlinger, der virker mistænkelige.

For flere mislykkede logons skal du f.eks. undersøge:

- Logonaktivitet

   Kontrollér, at logonaktiviteten før oprettelsen af reglen ikke er mistænkelig. (fælles placering/internetudbyder/brugeragent).

- Beskeder

   Kontrollér, om brugeren har modtaget beskeder, før reglerne blev oprettet. Dette kan indikere, at brugerkontoen kan være kompromitteret. Det kan f.eks. være en umulig rejsebesked, sjældent land, flere mislykkede logons, blandt andre.)

- Hændelse

   Kontrollér, om beskeden er knyttet til andre beskeder, der angiver en hændelse. Hvis det er tilfældet, skal du kontrollere, om hændelsen indeholder andre sande positive beskeder.

## <a name="advanced-hunting-queries"></a>Avancerede jagtforespørgsler

[Advanced Hunting](advanced-hunting-overview.md) er et forespørgselsbaseret trusselsjagtværktøj, der giver dig mulighed for at inspicere hændelser i dit netværk for at finde trusselsindikatorer.

Brug denne forespørgsel til at finde alle de nye hændelser for indbakkereglen i løbet af et bestemt tidsrum.

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

Kolonnen *RuleConfig* leverer den nye indbakkeregelkonfiguration.

Brug denne forespørgsel til at kontrollere, om internetudbyderen er almindelig for brugeren, ved at se på brugerens historik.

```kusto
let alert_date = now(); //enter alert date
let timeback = 60d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP
```

Brug denne forespørgsel til at kontrollere, om landet er almindeligt for brugeren, ved at se på brugerens historik.

```kusto
let alert_date = now(); //enter alert date
let timeback = 60d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

Brug denne forespørgsel til at kontrollere, om brugeragenten er almindelig for brugeren, ved at se på brugerens historik.

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

1. Deaktiver reglen for skadelig indbakke.
2. Nulstil brugerkontoens legitimationsoplysninger. Du kan også kontrollere, om brugerkontoen er blevet kompromitteret med Microsoft Defender for Cloud Apps, hvilket henter sikkerhedssignaler fra Azure Active Directory (Azure AD) Identity Protection.
3. Søg efter andre skadelige aktiviteter, der udføres af den påvirkede brugerkonto.
4. Kontrollér, om der er andre mistænkelige aktiviteter i lejeren, der stammer fra den samme IP-adresse eller fra den samme internetudbyder (hvis internetudbyderen er ualmindelig), for at finde andre kompromitterede brugerkonti.

## <a name="see-also"></a>Se også

- [Oversigt over beskedklassering](alert-grading-playbooks.md)
- [Mistænkelig aktivitet for videresendelse af mail](alert-grading-playbook-email-forwarding.md)
- [Mistænkelige regler for videresendelse af indbakke](alert-grading-playbook-inbox-forwarding-rules.md)
- [Undersøg beskeder](investigate-alerts.md)
