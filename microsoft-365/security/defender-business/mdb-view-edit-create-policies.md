---
title: Få vist eller rediger politikker i Microsoft Defender for Business
description: Få mere at vide om, hvordan du får vist, redigerer, opretter og sletter næste generations beskyttelsespolitikker i Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: cb79804985ee888faf1aa70029014a77ac9cae78
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63606818"
---
# <a name="view-or-edit-policies-in-microsoft-defender-for-business"></a>Få vist eller rediger politikker i Microsoft Defender for Business

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

I Microsoft Defender for Business konfigureres sikkerhedsindstillinger via politikker, der anvendes på enheder. For at hjælpe med at forenkle konfigurationen og konfigurationen indeholder Defender for Business forudkonfigurerede politikker, der hjælper med at beskytte din virksomheds enheder, så snart de er onboardet. Du kan bruge standardpolitikker, redigere politikker eller oprette dine egne politikker.

**I denne artikel beskrives det, hvordan** du:

- [Få et overblik over dine standardpolitikker](#default-policies-in-defender-for-business)

- [Få vist dine eksisterende politikker](#view-your-existing-policies)

- [Rediger en eksisterende politik](#edit-an-existing-policy)

- [Opret en ny politik](#create-a-new-policy)

>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>

## <a name="default-policies-in-defender-for-business"></a>Standardpolitikker i Defender for Business

I Defender for Business findes der to primære typer af politikker til beskyttelse af din virksomheds enheder:

- **Næste generations beskyttelsespolitikker,** der bestemmer, hvordan Microsoft Defender Antivirus og andre funktioner til trusselsbeskyttelse er konfigureret

- **Firewallpolitikker**, som bestemmer, hvilken netværkstrafik der må flowes til og fra virksomhedens enheder


## <a name="view-your-existing-policies"></a>Få vist dine eksisterende politikker

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på. 

2. Vælg Enhedskonfiguration i **navigationsruden**. Politikker er organiseret efter operativsystem (f.eks **. Windows klient**) og politiktype (**f.eks. Næste generations beskyttelse** og **Firewall**). 

3. Vælg en fane for operativsystem (f.eks **. Windows klienter**), og gennemgå derefter listen over politikker under kategorierne Næste **generations** beskyttelse **og Firewall**. 

4. Hvis du vil have vist flere oplysninger om en politik, skal du vælge dens navn. Der åbnes en siderude med flere oplysninger om politikken, f.eks. hvilke enheder der er beskyttet af den pågældende politik.

## <a name="edit-an-existing-policy"></a>Rediger en eksisterende politik

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på. 

2. Vælg Enhedskonfiguration i **navigationsruden**. Politikker er organiseret efter operativsystem (f.eks **. Windows klient**) og politiktype (**f.eks. Næste generations beskyttelse** og **Firewall**). 

3. Vælg en fane for operativsystem (f.eks **. Windows klienter**), og gennemgå derefter listen over politikker under kategorierne Næste **generations** beskyttelse **og Firewall**. 

4. Hvis du vil redigere en politik, skal du vælge dens navn og derefter vælge **Rediger**.

5. Gennemgå **oplysningerne under** fanen Generelle oplysninger. Hvis det er nødvendigt, kan du redigere beskrivelsen. Vælg derefter **Næste**.

6. På fanen **Enhedsgrupper skal** du bestemme, hvilke enhedsgrupper der skal modtage denne politik.  

   - Hvis du vil bevare den valgte enhedsgruppe, som den er, skal du vælge **Næste**.
   - Hvis du vil fjerne en enhedsgruppe fra politikken, skal du vælge **Fjern**.
   - Hvis du vil oprette en ny enhedsgruppe, **skal du vælge Opret ny** gruppe og derefter konfigurere din enhedsgruppe. Hvis du vil have hjælp til denne opgave, skal [du se Enhedsgrupper i Microsoft Defender for Business](mdb-create-edit-device-groups.md).
   - Hvis du vil anvende politikken på en anden enhedsgruppe, skal du **vælge Brug eksisterende gruppe**.

   Når du har angivet, hvilke enhedsgrupper der skal modtage politikken, skal du vælge **Næste**.

7. Gennemgå **indstillingerne under** fanen Konfigurationsindstillinger. Hvis det er nødvendigt, kan du redigere indstillingerne for din politik. Hvis du vil have hjælp til denne opgave, skal du se følgende artikler: 

   - [Forstå næste generations konfigurationsindstillinger](mdb-next-gen-configuration-settings.md)   
   - [Firewall-indstillinger](mdb-firewall.md)

   Når du har angivet dine næste generations beskyttelsesindstillinger, skal du vælge **Næste**.

8. På fanen **Gennemse din politik** skal du gennemgå de generelle oplysninger, målrettede enheder og konfigurationsindstillinger. 

   - Foretag eventuelle nødvendige ændringer ved at vælge **Rediger**.
   - Vælg Opdater politik, når du er klar til **at fortsætte**.

## <a name="create-a-new-policy"></a>Opret en ny politik

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på. 

2. Vælg Enhedskonfiguration i **navigationsruden**. Politikker er organiseret efter operativsystem (f.eks **. Windows klient**) og politiktype (**f.eks. Næste generations beskyttelse** og **Firewall**). 

3. Vælg en fane til operativsystem (f.eks **. Windows klienter**), og gennemgå derefter listen **over politikker for næste generations** beskyttelse. 

4. Under **Næste generations beskyttelse eller** **Firewall skal** du vælge **+ Tilføj**.

5. Gør **følgende under** fanen Generelle oplysninger:

   1. Angiv et navn og en beskrivelse. Disse oplysninger hjælper dig og dit team med at identificere politikken senere.
   2. Gennemse politikrækkefølgen, og rediger den, hvis det er nødvendigt. (Du kan finde flere oplysninger [i Politikrækkefølge](mdb-policy-order.md)).
   3. Vælg **Næste**. 

7. På fanen **Enhedsgrupper** skal du enten oprette en ny enhedsgruppe eller bruge en eksisterende gruppe. Politikker tildeles enheder via enhedsgrupper. Her er nogle ting, du skal huske på:

   - Til at begynde med har du muligvis kun din standardenhedsgruppe, som omfatter de enheder, som personer i virksomheden bruger til at få adgang til virksomhedens data og mail. Du kan beholde og bruge din standardenhedsgruppe.
   - Opret en ny enhedsgruppe for at anvende en politik med bestemte indstillinger, der er forskellige fra standardpolitikken. 
   - Når du konfigurerer din enhedsgruppe, angiver du bestemte kriterier, f.eks. operativsystemversionen. Enheder, der opfylder kriterierne, er inkluderet i den pågældende enhedsgruppe, medmindre du udelader dem. 
   - Alle enhedsgrupper, herunder de standard- og brugerdefinerede enhedsgrupper, du definerer, gemmes i Azure Active Directory (Azure AD).

   Du kan få mere at vide om enhedsgrupper [under Enhedsgrupper i Defender for Business](mdb-create-edit-device-groups.md).

8. På fanen **Konfigurationsindstillinger** skal du angive indstillingerne for din politik og derefter vælge **Næste**. Du kan finde flere oplysninger om de enkelte indstillinger [under Konfigurationsindstillinger for Microsoft Defender for Business](mdb-next-gen-configuration-settings.md).

9. På fanen **Gennemse din politik** skal du gennemgå de generelle oplysninger, målrettede enheder og konfigurationsindstillinger. 

   - Foretag eventuelle nødvendige ændringer ved at vælge **Rediger**.
   - Vælg Opret politik, når du er klar til **at fortsætte**.


## <a name="next-steps"></a>Næste trin

Vælg en eller flere af følgende opgaver:

- [Administrer enheder](mdb-manage-devices.md)

- [Opret en ny politik i Microsoft Defender for Business](mdb-create-new-policy.md)

- [Få vist og administrer hændelser i Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [Re besvare og afhjælpe trusler i Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [Gennemse afhjælpningshandlinger i Handlingscenter](mdb-review-remediation-actions.md)