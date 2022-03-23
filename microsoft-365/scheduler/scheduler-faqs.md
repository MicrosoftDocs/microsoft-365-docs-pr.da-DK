---
title: Ofte stillede spørgsmål om Scheduler til Microsoft 365
ms.author: v-aiyengar
author: AshaIyengar21
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
ms.localizationpriority: medium
description: Ofte stillede spørgsmål om Scheduler til Microsoft 365
ms.openlocfilehash: 2392c48de3d80cf41d179eb053c46967626b5159
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/03/2021
ms.locfileid: "63593250"
---
# <a name="scheduler-for-microsoft-365-faq"></a>Ofte stillede spørgsmål om Scheduler til Microsoft 365

**Spørgsmål:** Hvordan integreres Scheduler med andre Cortana-funktioner, f.eks *. Cortana til Windows*, *Daglig briefing af* mail *og Afspil mine mails*?</br>
Scheduler er en uafhængig tjeneste fra andre Cortana-funktioner. Andre Cortana-funktioner kan deaktiveres på lejerniveau, og Scheduler kan stadig aktiveres ved hjælp cortana@yourdomain.com mailadressen. I øjeblikket kan brugerne kun interagere med Scheduler via mail.

**Spørgsmål:** Virker det kun med Outlook? Understøttes andre mailprodukter?</br>
Så længe du har en licens, ud over de tre krav ovenfor, kan brugerne sende mails cortana@yourdomain.com fra en hvilken som helst mailklient på en hvilken som helst enhed.

**Spørgsmål:** Kan kontakter være på en personlig kontaktliste i Outlook og GAL eller andre tilsvarende virksomheder?</br>
Mødedeltagere kan være alle med en mailadresse i eller uden for virksomheden. Desværre kan Scheduler ikke automatisk oversætte navne til mailadresser/alias ved at søge efter det i galen i dag.

**Spørgsmål:** Kan jeg bruge Scheduler med min installerede version (i det lokale miljø) af Outlook?</br>
Scheduler kræver Exchange Online. Fungerer ikke med Exchange Server (i det følgende afsnit). Fungerer med alle mailklienter, Outlook Desktop, OWA, iOS, android, gmail osv.

**Spørgsmål:** Skal Outlook være åben i baggrunden?</br>
Outlook behøver ikke at være åben i baggrunden. Det eneste, du skal gøre, er at sende Cortana en mail og være afhængig af den til at udføre en masse arbejde.

## <a name="frequently-asked-trust-and-privacy-questions"></a>Ofte stillede spørgsmål om tillid og beskyttelse af personlige oplysninger

**Spørgsmål:** Hvordan fungerer Scheduler?</br>
Scheduler bruger Planlægningsintelligens (AI) udvidet med humane assistenter. Hvis AI-modeller skaber behov for support på det naturlige sprog for kommunikation med Cortana, eskaleres mødeindkaldelsen til et menneske, så den bliver gennemset og fuldført.

**Spørgsmål:** Hvem er de mennesker, der gennemser eskalerede anmodninger? </br>
Scheduler-assistenter er Microsoft Supplier Security and Privacy Assurance (SSPA), der er certificeret til personlige og meget fortrolige oplysninger.

**Spørgsmål:** Hvad kan SSPA-assistenter få vist?</br>
Planlæggeren og SSPA-assistenterne kan se de mails, der er adresseret til Cortana. I en mailudveksling med tråde er det kun mails, der indeholder Cortanas mailadresse, der bliver behandlet, ikke de tidligere mails i tråden, før Cortana blev tilføjet.

**Spørgsmål:** Bevares kundedata i Scheduler's Dataflow? </br>
Scheduler gemmer alt kundeindhold inden for lejergrænserne og bevarer data i overensstemmelse med GDPR-retningslinjer, Microsoft 365 Trust & Politikker for beskyttelse af personlige oplysninger og lejerens mailpolitikker.

**Spørgsmål:** Hvordan behandler Scheduler ledig/optaget-data for interne deltagere? </br>
Schedulers automatisering bruger tjenesten *findMeetingTimes* til at identificere tidspunkter, der er fælles tilgængelige for deltagerne og arrangøren. Denne tjeneste styrke andre Outlook-oplevelser, f.eks *. Foreslåede tidspunkter* i Outlook-mødeformularen. Oplysninger om ledig/optaget deltager anvendes ikke eksplicit som ledig/optaget-blokke.

**Spørgsmål:** Er Scheduler GDPR kompatibel? </br>
Ja.

**Spørgsmål:** Hvem har adgang til Cortana-postkassen? </br>
Scheduler behandler mødeindkaldelser og tilknyttede mails, der sendes til din lejers Cortana-postkasse. Microsoft har ikke anden adgang til Cortana-postkassen undtagen via Lockbox-godkendelse på anmodning af lejeradministratoren.

**Spørgsmål:** Bruges kundedata til AI-modeller til uddannelse?</br>
Intet kundeindhold fra Scheduler til Microsoft 365 kan bruges til datakursussæt. Alt kundeindhold befinder sig i kundelejeren.

**Spørgsmål:** Vil Scheduler behandle krypteret mail?</br>
Nej, krypterede mails afvises af Scheduler-arbejdsprocessen.
