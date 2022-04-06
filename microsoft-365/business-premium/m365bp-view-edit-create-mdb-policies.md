---
title: Få vist eller rediger politikker for enhedsbeskyttelse
description: Få vist, rediger, opret og slet politikker for enhedsbeskyttelse i Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/08/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: ba322493b3900c099ab5525f052604604ef0ac23
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705475"
---
# <a name="view-and-edit-your-device-protection-policies"></a>Få vist og redigere politikker for enhedsbeskyttelse

I Microsoft 365 Business Premium konfigureres sikkerhedsindstillinger for administrerede enheder via politikker for enhedsbeskyttelse. For at forenkle konfigurationen og konfigurationen har du forudkonfigurerede politikker, der kan hjælpe med at beskytte din organisations enheder, så snart de er onboardet. Du kan bruge standardpolitikker, redigere politikker eller oprette dine egne politikker.

**I denne artikel beskrives det, hvordan** du:

- Få et overblik over dine standardpolitikker
- Få vist dine eksisterende politikker
- Rediger en eksisterende politik
- Opret en ny politik

## <a name="default-device-protection-policies"></a>Standardpolitikker for enhedsbeskyttelse

Microsoft 365 Business Premium indeholder to primære typer politikker til beskyttelse af din organisations enheder:

- **Næste generations beskyttelsespolitikker,** der bestemmer, hvordan Microsoft Defender Antivirus og andre funktioner til trusselsbeskyttelse er konfigureret

- **Firewallpolitikker**, som bestemmer, hvilken netværkstrafik der må flowes til og fra organisationens enheder

Disse politikker er en del af Microsoft Defender for Business, som er inkluderet i dit Microsoft 365 Business Premium abonnement.

## <a name="view-your-existing-device-protection-policies"></a>Få vist dine eksisterende politikker for enhedsbeskyttelse

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på. 

2. Vælg Enhedskonfiguration i **navigationsruden**. Politikker er organiseret efter operativsystem (f.eks **. Windows klient**) og politiktype (**f.eks. Næste generations beskyttelse** og **Firewall**). 

3. Vælg en fane for operativsystem (f.eks **. Windows klienter**), og gennemgå derefter listen over politikker under kategorierne Næste **generations** beskyttelse **og Firewall**. 

4. Hvis du vil have vist flere oplysninger om en politik, skal du vælge dens navn. Der åbnes en siderude med flere oplysninger om politikken, f.eks. hvilke enheder der er beskyttet af den pågældende politik.

## <a name="edit-an-existing-device-protection-policy"></a>Rediger en eksisterende politik for enhedsbeskyttelse

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på. 

2. Vælg Enhedskonfiguration i **navigationsruden**. Politikker er organiseret efter operativsystem (f.eks **. Windows klient**) og politiktype (**f.eks. Næste generations beskyttelse** og **Firewall**). 

3. Vælg en fane for operativsystem (f.eks **. Windows klienter**), og gennemgå derefter listen over politikker under kategorierne Næste **generations** beskyttelse **og Firewall**. 

4. Hvis du vil redigere en politik, skal du vælge dens navn og derefter vælge **Rediger**.

5. Gennemgå **oplysningerne under** fanen Generelle oplysninger. Hvis det er nødvendigt, kan du redigere beskrivelsen. Vælg derefter **Næste**.

6. På fanen **Enhedsgrupper skal** du bestemme, hvilke enhedsgrupper der skal modtage denne politik.  

   - Hvis du vil bevare den valgte enhedsgruppe, som den er, skal du vælge **Næste**.
   - Hvis du vil fjerne en enhedsgruppe fra politikken, skal du vælge **Fjern**.
   - Hvis du vil oprette en ny enhedsgruppe, **skal du vælge Opret ny** gruppe og derefter konfigurere din enhedsgruppe. Hvis du vil have hjælp til denne opgave, skal [du se Enhedsgrupper Microsoft 365 Business Premium](m365bp-device-groups-mdb.md).
   - Hvis du vil anvende politikken på en anden enhedsgruppe, skal du **vælge Brug eksisterende gruppe**.

   Når du har angivet, hvilke enhedsgrupper der skal modtage politikken, skal du vælge **Næste**.

7. Gennemgå **indstillingerne under** fanen Konfigurationsindstillinger. Hvis det er nødvendigt, kan du redigere indstillingerne for din politik. Hvis du vil have hjælp til denne opgave, skal du se følgende artikler: 

   - [Forstå næste generations konfigurationsindstillinger](../security/defender-business/mdb-next-gen-configuration-settings.md)   
   - [Firewall-indstillinger](../security/defender-business/mdb-firewall.md)

   Når du har angivet dine næste generations beskyttelsesindstillinger, skal du vælge **Næste**.

8. På fanen **Gennemse din politik** skal du gennemgå de generelle oplysninger, målrettede enheder og konfigurationsindstillinger. 

   - Foretag eventuelle nødvendige ændringer ved at vælge **Rediger**.
   - Vælg Opdater politik, når du er klar til **at fortsætte**.

## <a name="create-a-new-device-protection-policy"></a>Opret en ny politik for enhedsbeskyttelse

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på. 

2. Vælg Enhedskonfiguration i **navigationsruden**. Politikker er organiseret efter operativsystem (f.eks **. Windows klient**) og politiktype (**f.eks. Næste generations beskyttelse** og **Firewall**). 

3. Vælg en fane til operativsystem (f.eks **. Windows klienter**), og gennemgå derefter listen **over politikker for næste generations** beskyttelse. 

4. Under **Næste generations beskyttelse eller** **Firewall skal** du vælge **+ Tilføj**.

5. Gør **følgende under** fanen Generelle oplysninger:

   1. Angiv et navn og en beskrivelse. Disse oplysninger hjælper dig og dit team med at identificere politikken senere.
   2. Gennemse politikrækkefølgen, og rediger den, hvis det er nødvendigt. (Du kan finde flere oplysninger [i Politikrækkefølge](../security/defender-business/mdb-policy-order.md)).
   3. Vælg **Næste**. 

7. På fanen **Enhedsgrupper** skal du enten oprette en ny enhedsgruppe eller bruge en eksisterende gruppe. Politikker tildeles enheder via enhedsgrupper. Her er nogle ting, du skal huske på:

   - Til at begynde med har du muligvis kun din standardenhedsgruppe, som omfatter de enheder, som personer i organisationen bruger til at få adgang til organisationens data og mail. Du kan beholde og bruge din standardenhedsgruppe.
   - Opret en ny enhedsgruppe for at anvende en politik med bestemte indstillinger, der er forskellige fra standardpolitikken. 
   - Når du konfigurerer din enhedsgruppe, angiver du bestemte kriterier, f.eks. operativsystemversionen. Enheder, der opfylder kriterierne, er inkluderet i den pågældende enhedsgruppe, medmindre du udelader dem. 
   - Alle enhedsgrupper, herunder de standard- og brugerdefinerede enhedsgrupper, du definerer, gemmes i Azure Active Directory (Azure AD).

   Du kan få mere at vide om enhedsgrupper [under Enhedsgrupper i Microsoft Defender for Business](../security/defender-business/mdb-create-edit-device-groups.md).

8. På fanen **Konfigurationsindstillinger** skal du angive indstillingerne for din politik og derefter vælge **Næste**. Du kan finde flere oplysninger om de enkelte indstillinger [under Forstå næste generations konfigurationsindstillinger i Microsoft Defender for Business](../security/defender-business/mdb-next-gen-configuration-settings.md).

9. På fanen **Gennemse din politik** skal du gennemgå de generelle oplysninger, målrettede enheder og konfigurationsindstillinger. 

   - Foretag eventuelle nødvendige ændringer ved at vælge **Rediger**.
   - Vælg Opret politik, når du er klar til **at fortsætte**.


## <a name="next-steps"></a>Næste trin

[Enhedsgrupper i Microsoft 365 Business Premium](m365bp-device-groups-mdb.md)