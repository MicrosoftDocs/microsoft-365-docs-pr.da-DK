---
title: Meddelelser, der er sat i karantæne
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 4c234874-015e-4768-8495-98fcccfc639b
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om karantæne i Exchange Online Protection (EOP), der indeholder potentielt skadelige eller uønskede meddelelser.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 509e093d1618cf17d8f5f880aa82a2c54e8204bf
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63587933"
---
# <a name="quarantined-email-messages-in-eop-and-defender-for-office-365"></a>Sendte mails i karantæne i EOP og Defender for Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående Exchange Online Protection (EOP)-organisationer uden Exchange Online-postkasser er karantæne tilgængelig for potentielt farlig eller uønskede meddelelser.

Antimalwarepolitikker sætter automatisk en meddelelse i karantæne *, hvis* der findes vedhæftede filer, der indeholder malware. Få mere at vide under [Konfigurer antimalwarepolitikker i EOP](configure-anti-malware-policies.md).

Antispam har som standard sat phishing i karantæne og phishingmeddelelser med høj tillid til samt levering af spam, spam og massemails til brugerens mappe til uønsket mail. Men du kan også oprette og tilpasse antispampolitikker for at sætte spam i karantæne, spam med høj tillid og massemails. Få mere at vide under [Konfigurer antispam-politikker i EOP](configure-your-spam-filter-policies.md).

Både brugere og administratorer kan arbejde med meddelelser, der er sat i karantæne:

- _Karantænepolitikker_ definerer, hvad brugerne har tilladelse til at gøre eller ikke må til meddelelser, der er sat i karantæne, baseret på, hvorfor meddelelsen var sat i karantæne (for understøttede funktioner). Standardkarantænepolitikker gennemtvinger de historiske egenskaber som beskrevet nedenfor. Administratorer kan oprette og anvende brugerdefinerede karantænepolitikker, der definerer mindre restriktive eller mere restriktive funktioner for brugere, og de kan også aktivere beskeder i karantæne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).

- Administratorer kan arbejde med alle typer af meddelelser, der er sat i karantæne, for alle brugere. Som standard er det kun administratorer, der kan arbejde med meddelelser, der var i karantæne som malware, phishing med høj tillid eller som et resultat af regler for mailflow (også kaldet transportregler). Få mere at vide under [Administrer meddelelser og filer, der er sat i karantæne som administrator i EOP](manage-quarantined-messages-and-files.md).

- Som standard kan brugerne arbejde med meddelelser, der er sat i karantæne, hvor de er en modtager, og meddelelsen var sat i karantæne som spam, massemail eller phishing (phishing er ikke meget tillid til). Få mere at vide under [Find og slip meddelelser, der er sat i karantæne, som bruger i EOP](find-and-release-quarantined-messages-as-a-user.md).

  Hvis du vil forhindre brugere i at administrere deres egne phishingmeddelelser i karantæne, kan administratorerne tildele en politik for karantæne, der afviser adgang til meddelelser, der er sat i karantæne, fra phishingmailfiltrering med antispampolitikker. Få mere at vide under [Tildel karantænepolitikker i antispampolitikker](quarantine-policies.md#anti-spam-policies)[.](quarantine-policies.md)

- Administratorer og brugere kan rapportere falske positive til Microsoft i karantæne.

- Hvor længe meddelelser, der er sat i karantæne, før de udløber, varierer, afhængigt af hvorfor meddelelsen blev sat i karantæne. De funktioner, der sætter meddelelser i karantæne og deres tilsvarende opbevaringsperioder, er beskrevet i følgende tabel:

  <br>

  ****

  |Årsagen til karantæne|Standardopbevaringsperiode|Kan du tilpasse?|Kommentarer|
  |---|---|:---:|---|
  |Meddelelser, der er sat i karantæne af antispampolitikker: spam, spam, phishing, phishing med høj tillid eller massemails.|15 dage: <ul><li>I standardpolitikken for uønsket post.</li><li>I antispam-politikker, som du opretter i PowerShell.</li></ul> <p> 30 dage i politikker for uønsket post, som du opretter i Microsoft 365 Defender-portalen.|Ja|Du kan konfigurere (lavere) denne værdi i antispampolitikker. Du kan finde flere oplysninger i **indstillingen Behold spam** i karantæne for dette antal dage (_KarantæneRetentionPeriod_) i [Konfigurer antispampolitikker](configure-your-spam-filter-policies.md).|
  |Meddelelser, der er sat i karantæne via antiphishing-politikker: efterlignet intelligens i EOP; bruger efterligning, domænepersonation eller postkasseintelligens i Defender Office 365.|30 dage|Ja|Denne opbevaringsperiode styres også af indstillingen Behold **spam** i karantæne i dette antal dage (_KarantæneRetentionPeriod_) i **antispampolitikker** . Den opbevaringsperiode, der bruges, er værdien fra den første matchende **antispampolitik** , som modtageren er defineret i.|
  |Meddelelser, der er sat i karantæne af antimalwarepolitikker (malwaremeddelelser).|15 dage|Nej||
  |Meddelelser, der er sat i karantæne Pengeskab politikker for vedhæftede filer i Defender Office 365 (malwaremeddelelser).|15 dage|Nej||
  |Meddelelser, der er sat i karantæne efter regler for mailflow: handlingen er Lever **meddelelsen til den værtsbaserede karantæne** (_karantæne_).|30 dage|Nej||
  |Filer, der er sat i Pengeskab af Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams (malwarefiler).|15 dage|Nej||
  |

  Når en meddelelse udløber fra karantæne, kan du ikke gendanne den.

Du kan finde flere oplysninger om karantæne under Ofte [stillede spørgsmål om karantæne](quarantine-faq.yml).
