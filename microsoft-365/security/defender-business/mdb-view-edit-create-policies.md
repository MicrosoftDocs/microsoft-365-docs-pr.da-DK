---
title: Få vist eller rediger politikker i Microsoft Defender til virksomheder
description: Få mere at vide om, hvordan du får vist, redigerer, opretter og sletter politikker for cybersikkerhed i Defender for Business. Beskyt dine enheder med sikkerhedspolitikker.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: c5606c19e4cef64e701d34a5e4ccc2143f51f394
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66090360"
---
# <a name="view-or-edit-policies-in-microsoft-defender-for-business"></a>Få vist eller rediger politikker i Microsoft Defender til virksomheder

I Microsoft Defender til virksomheder konfigureres sikkerhedsindstillinger via politikker, der anvendes på enheder. For at hjælpe med at forenkle din konfigurationsoplevelse indeholder Defender for Business forudkonfigurerede politikker, der hjælper med at beskytte din virksomheds enheder, så snart de er onboardet. Du kan bruge standardpolitikkerne, redigere politikker eller oprette dine egne politikker.

**I denne artikel beskrives det, hvordan du**:

- [Få et overblik over dine standardpolitikker](#default-policies-in-defender-for-business)
- [Få vist dine eksisterende politikker](#view-your-existing-policies)
- [Rediger en eksisterende politik](#edit-an-existing-policy)
- [Opret en ny politik](#create-a-new-policy)


## <a name="default-policies-in-defender-for-business"></a>Standardpolitikker i Defender for Business

I Defender for Business er der to primære typer politikker, der beskytter din virksomheds enheder:

- **Næste generations beskyttelsespolitikker**, der bestemmer, hvordan Microsoft Defender Antivirus og andre funktioner til trusselsbeskyttelse er konfigureret
- **Firewallpolitikker**, der bestemmer, hvilken netværkstrafik der må overføres til og fra virksomhedens enheder


## <a name="view-your-existing-policies"></a>Få vist dine eksisterende politikker

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på. 

2. Vælg **Enhedskonfiguration** i navigationsruden. Politikker er organiseret efter operativsystem (f.eks **. Windows klient**) og politiktype (f.eks **. næste generations beskyttelse** og **firewall**). 

3. Vælg en operativsystemfane (f.eks. **Windows klienter**), og gennemse derefter listen over politikker under kategorierne **Næste generation af beskyttelse** og **Firewall**. 

4. Hvis du vil have vist flere oplysninger om en politik, skal du vælge dens navn. Der åbnes en siderude, der indeholder flere oplysninger om den pågældende politik, f.eks. hvilke enheder der er beskyttet af den pågældende politik.

## <a name="edit-an-existing-policy"></a>Rediger en eksisterende politik

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på. 

2. Vælg **Enhedskonfiguration** i navigationsruden. Politikker er organiseret efter operativsystem (f.eks **. Windows klient**) og politiktype (f.eks **. næste generations beskyttelse** og **firewall**). 

3. Vælg en operativsystemfane (f.eks. **Windows klienter**), og gennemse derefter listen over politikker under kategorierne **Næste generation af beskyttelse** og **Firewall**. 

4. Hvis du vil redigere en politik, skal du vælge dens navn og derefter vælge **Rediger**.

5. Gennemse oplysningerne under fanen **Generelle oplysninger** . Hvis det er nødvendigt, kan du redigere beskrivelsen. Vælg derefter **Næste**.

6. På fanen **Enhedsgrupper** skal du bestemme, hvilke enhedsgrupper der skal modtage denne politik.  

   - Hvis du vil beholde den valgte enhedsgruppe, som den er, skal du vælge **Næste**.
   - Hvis du vil fjerne en enhedsgruppe fra politikken, skal du vælge **Fjern**.
   - Hvis du vil konfigurere en ny enhedsgruppe, skal du vælge **Opret ny gruppe** og derefter konfigurere din enhedsgruppe. Hvis du vil have hjælp til denne opgave, skal [du se Enhedsgrupper i Microsoft Defender til virksomheder](mdb-create-edit-device-groups.md).
   - Hvis du vil anvende politikken på en anden enhedsgruppe, skal du vælge **Brug eksisterende gruppe**.

   Når du har angivet, hvilke enhedsgrupper der skal modtage politikken, skal du vælge **Næste**.

7. Gennemse indstillingerne under fanen **Konfigurationsindstillinger** . Hvis det er nødvendigt, kan du redigere indstillingerne for din politik. Du kan få hjælp til denne opgave i følgende artikler: 

   - [Om konfigurationsindstillinger for næste generation](mdb-next-gen-configuration-settings.md)   
   - [Firewallindstillinger](mdb-firewall.md)

   Når du har angivet dine næste generations beskyttelsesindstillinger, skal du vælge **Næste**.

8. Gennemse de generelle oplysninger, målrettede enheder og konfigurationsindstillinger under fanen **Gennemse din politik** . 

   - Foretag de nødvendige ændringer ved at vælge **Rediger**.
   - Når du er klar til at fortsætte, skal du vælge **Opdater politik**.

## <a name="create-a-new-policy"></a>Opret en ny politik

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på. 

2. Vælg **Enhedskonfiguration** i navigationsruden. Politikker er organiseret efter operativsystem (f.eks **. Windows klient**) og politiktype (f.eks **. næste generations beskyttelse** og **firewall**). 

3. Vælg en operativsystemfane (f.eks. **Windows klienter**), og gennemse derefter listen over **næste generations beskyttelsespolitikker**. 

4. Under **Næste generation af beskyttelse** eller **Firewall** skal du vælge **+ Tilføj**.

5. Udfør følgende trin under fanen **Generelle oplysninger** :

   1. Angiv et navn og en beskrivelse. Disse oplysninger hjælper dig og dit team med at identificere politikken senere.
   2. Gennemse politikrækkefølgen, og rediger den, hvis det er nødvendigt. Du kan få flere oplysninger under [Politikrækkefølge](mdb-policy-order.md).
   3. Vælg **Næste**. 

7. På fanen **Enhedsgrupper** skal du enten oprette en ny enhedsgruppe eller bruge en eksisterende gruppe. Politikker tildeles til enheder via enhedsgrupper. Her er nogle ting, du skal være opmærksom på:

   - Indledningsvist har du måske kun din standardenhedsgruppe, som omfatter de enheder, som personer i din virksomhed bruger til at få adgang til firmadata og mail. Du kan beholde og bruge din standardenhedsgruppe.
   - Opret en ny enhedsgruppe for at anvende en politik med specifikke indstillinger, der er forskellige fra standardpolitikken. 
   - Når du konfigurerer din enhedsgruppe, angiver du visse kriterier, f.eks. operativsystemversionen. Enheder, der opfylder kriterierne, er inkluderet i den pågældende enhedsgruppe, medmindre du ekskluderer dem. 
   - Alle enhedsgrupper, herunder de standard- og brugerdefinerede enhedsgrupper, du definerer, gemmes i Azure Active Directory (Azure AD).

   Du kan få mere at vide om enhedsgrupper [under Enhedsgrupper i Defender for Business](mdb-create-edit-device-groups.md).

8. Under fanen **Konfigurationsindstillinger** skal du angive indstillingerne for din politik og derefter vælge **Næste**. Du kan få flere oplysninger om de individuelle indstillinger under [Konfigurationsindstillinger for Microsoft Defender til virksomheder](mdb-next-gen-configuration-settings.md).

9. Gennemse de generelle oplysninger, målrettede enheder og konfigurationsindstillinger under fanen **Gennemse din politik** . 

   - Foretag de nødvendige ændringer ved at vælge **Rediger**.
   - Når du er klar til at fortsætte, skal du vælge **Opret politik**.


## <a name="next-steps"></a>Næste trin

Vælg en eller flere af følgende opgaver:

- [Administrer enheder](mdb-manage-devices.md)
- [Opret en ny politik i Microsoft Defender til virksomheder](mdb-create-new-policy.md)
- [Få vist og administrer hændelser i Microsoft Defender til virksomheder](mdb-view-manage-incidents.md)
- [Reagere på og afhjælpe trusler i Microsoft Defender til virksomheder](mdb-respond-mitigate-threats.md)
- [Gennemse afhjælpningshandlinger i Løsningscenter](mdb-review-remediation-actions.md)