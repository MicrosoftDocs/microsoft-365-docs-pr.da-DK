---
title: Få vist eller rediger politikker for beskyttelse af enheder
description: Få vist, rediger, opret og slet politikker for beskyttelse af enheden i Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: d628df3109eafd3d342041784d70b9857e260d81
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66486027"
---
# <a name="view-and-edit-device-protection-policies"></a>Få vist og rediger politikker for beskyttelse af enheder

I Microsoft 365 Business Premium konfigureres sikkerhedsindstillinger for administrerede enheder via politikker for enhedsbeskyttelse i Microsoft Defenders sikkerhedscenter eller Administration center. For at hjælpe med at forenkle konfiguration er der forudkonfigurerede politikker, der hjælper med at beskytte din organisations enheder, så snart de er onboardet. Du kan bruge standardpolitikkerne, redigere eksisterende politikker eller oprette dine egne politikker.

**I denne vejledning beskrives det, hvordan du**:

- Få et overblik over dine standardpolitikker
- Arbejd med enhedspolitikker i Defender Security Center, Administration center og Intune.

## <a name="about-the-default-device-protection-policies"></a>Om standardpolitikker for enhedsbeskyttelse

Microsoft 365 Business Premium indeholder to primære typer politikker til beskyttelse af organisationens enheder:

- **Næste generations beskyttelsespolitikker**, der bestemmer, hvordan Microsoft Defender Antivirus og andre funktioner til trusselsbeskyttelse er konfigureret.

- **Firewallpolitikker**, der bestemmer, hvilken netværkstrafik der må overføres til og fra organisationens enheder.

Disse politikker er en del af Microsoft Defender til virksomheder, der er inkluderet i dit abonnement på Microsoft 365 Business Premium. Der gives oplysninger om arbejde med politikker i Microsoft Defender Security Center, samt hvordan du arbejder med politikker i Administration center og Intune.

## <a name="working-with-device-polices-in-the-microsoft-defender-security-center"></a>Arbejde med enhedspoliti i Microsoft Defender Security Center

Følgende oplysninger gælder for at arbejde med dine politikker i Security Center.

### <a name="view-existing-device-protection-policies"></a>Vis eksisterende politikker for beskyttelse af enheder

Sådan får du vist dine eksisterende politikker for enhedsbeskyttelse i Sikkerhedscenter:

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

1. Vælg **Enhedskonfiguration** i navigationsruden. Politikker er organiseret efter operativsystem (f.eks **. Windows-klient**) og politiktype (f.eks **. næste generations beskyttelse** og **firewall**).

    :::image type="content" source="../media/mdb-deviceconfiguration.png" lightbox="../media/mdb-deviceconfiguration.png" alt-text="Siden Enhedskonfiguration.":::

1. Vælg en operativsystemfane (f.eks **. Windows-klienter**), og gennemse derefter listen over politikker under kategorierne **Beskyttelse af næste generation** og **Firewall** .

1. Hvis du vil have vist flere oplysninger om en politik, skal du vælge dens navn. Der åbnes en siderude, der indeholder flere oplysninger om den pågældende politik, f.eks. hvilke enheder der er beskyttet af den pågældende politik.

   :::image type="content" source="../media/mdb-deviceconfig-selectedpolicy.png" lightbox="../media/mdb-deviceconfig-selectedpolicy.png" alt-text="Skærmbillede af en politik, der er valgt på siden Enhedskonfiguration.":::

### <a name="edit-an-existing-device-protection-policy"></a>Rediger en eksisterende beskyttelsespolitik for enheder

Sådan redigerer du en enhedspolitik:

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

1. Vælg **Enhedskonfiguration** i navigationsruden. Politikker er organiseret efter operativsystem (f.eks **. Windows-klient**) og politiktype (f.eks **. næste generations beskyttelse** og **firewall**).

1. Vælg en operativsystemfane (f.eks **. Windows-klienter**), og gennemse derefter listen over politikker under kategorierne **Beskyttelse af næste generation** og **Firewall** .

1. Hvis du vil redigere en politik, skal du vælge dens navn og derefter vælge **Rediger**.

1. Gennemse oplysningerne under fanen **Generelle oplysninger** . Hvis det er nødvendigt, kan du redigere beskrivelsen. Vælg derefter **Næste**.

1. På fanen **Enhedsgrupper** skal du bestemme, hvilke enhedsgrupper der skal modtage denne politik.  

   - Hvis du vil beholde den valgte enhedsgruppe, som den er, skal du vælge **Næste**.
   - Hvis du vil fjerne en enhedsgruppe fra politikken, skal du vælge **Fjern**.
   - Hvis du vil konfigurere en ny enhedsgruppe, skal du vælge **Opret ny gruppe** og derefter konfigurere din enhedsgruppe. Hvis du vil have hjælp til denne opgave, skal [du se Enhedsgrupper i Microsoft 365 Business Premium](m365bp-device-groups-mdb.md).
   - Hvis du vil anvende politikken på en anden enhedsgruppe, skal du vælge **Brug eksisterende gruppe**.

   Når du har angivet, hvilke enhedsgrupper der skal modtage politikken, skal du vælge **Næste**.

1. Gennemse indstillingerne under fanen **Konfigurationsindstillinger** . Hvis det er nødvendigt, kan du redigere indstillingerne for din politik. Du kan få hjælp til denne opgave i følgende artikler: 

   - [Om konfigurationsindstillinger for næste generation](../security/defender-business/mdb-next-gen-configuration-settings.md)   
   - [Firewallindstillinger](../security/defender-business/mdb-firewall.md)

   Når du har angivet dine næste generations beskyttelsesindstillinger, skal du vælge **Næste**.

1. Gennemse de generelle oplysninger, målrettede enheder og konfigurationsindstillinger under fanen **Gennemse din politik** .

   - Foretag de nødvendige ændringer ved at vælge **Rediger**.
   - Når du er klar til at fortsætte, skal du vælge **Opdater politik**.

### <a name="create-a-new-device-protection-policy"></a>Opret en ny politik for beskyttelse af enheder

Sådan opretter du en ny politik for beskyttelse af enheder:

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

1. Vælg **Enhedskonfiguration** i navigationsruden. Politikker er organiseret efter operativsystem (f.eks **. Windows-klient**) og politiktype (f.eks **. næste generations beskyttelse** og **firewall**).

1. Vælg en operativsystemfane (f.eks **. Windows-klienter**), og gennemse derefter listen over **næste generations beskyttelsespolitikker** .

1. Under **Næste generation af beskyttelse** eller **Firewall** skal du vælge **+ Tilføj**.

1. Udfør følgende trin under fanen **Generelle oplysninger** :

   1. Angiv et navn og en beskrivelse. Disse oplysninger hjælper dig og dit team med at identificere politikken senere.
   2. Gennemse politikrækkefølgen, og rediger den, hvis det er nødvendigt. Du kan få flere oplysninger under [Politikrækkefølge](../security/defender-business/mdb-policy-order.md).
   3. Vælg **Næste**.

1. På fanen **Enhedsgrupper** skal du enten oprette en ny enhedsgruppe eller bruge en eksisterende gruppe. Politikker tildeles til enheder via enhedsgrupper. Her er nogle ting, du skal være opmærksom på:

   - Indledningsvist har du måske kun din standardenhedsgruppe, som omfatter de enheder, som personer i din organisation bruger til at få adgang til organisationsdata og -mail. Du kan beholde og bruge din standardenhedsgruppe.
   - Opret en ny enhedsgruppe for at anvende en politik med specifikke indstillinger, der er forskellige fra standardpolitikken.
   - Når du konfigurerer din enhedsgruppe, angiver du visse kriterier, f.eks. operativsystemversionen. Enheder, der opfylder kriterierne, er inkluderet i den pågældende enhedsgruppe, medmindre du ekskluderer dem.
   - Alle enhedsgrupper, herunder de standard- og brugerdefinerede enhedsgrupper, du definerer, gemmes i Azure Active Directory (Azure AD).

   Du kan få mere at vide om enhedsgrupper [under Enhedsgrupper i Microsoft Defender til virksomheder](../security/defender-business/mdb-create-edit-device-groups.md).

1. Under fanen **Konfigurationsindstillinger** skal du angive indstillingerne for din politik og derefter vælge **Næste**. Du kan finde flere oplysninger om de individuelle indstillinger [under Forstå næste generations konfigurationsindstillinger i Microsoft Defender til virksomheder](../security/defender-business/mdb-next-gen-configuration-settings.md).

1. Gennemse de generelle oplysninger, målrettede enheder og konfigurationsindstillinger under fanen **Gennemse din politik** .

   - Foretag de nødvendige ændringer ved at vælge **Rediger**.
   - Når du er klar til at fortsætte, skal du vælge **Opret politik**.

## <a name="using-device-policies-in-the-admin-center"></a>Brug af enhedspolitikker i Administration center

Følgende oplysninger beskriver visning og administration af politikker i Microsoft Business Premium Administration center.

### <a name="working-with-device-policies"></a>Arbejde med enhedspolitikker

Sådan arbejder du med politikker i Administration center:

1.  Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.

1. Vælg **Enhedspolitikker** \> i venstre navigationsrude.

    På denne side kan du oprette, redigere, ændre målgruppe eller slette en politik.

    ![Skærmbillede af siden Politikker.](../media/devicepolicies.png)
  
### <a name="view-and-manage-devices"></a>Få vist og administrer enheder

Sådan får du vist og administrerer politikker:

1. Vælg **Enheder** \> **Administrer** i venstre navigationsrude.

    På denne side kan du vælge en eller flere enheder og fjerne firmadata. For Windows 10 enheder, som du har angivet indstillinger for beskyttelse af enheder for, kan du også vælge at nulstille enheden til fabriksindstillingerne.
  
   ![Siden Administrer enheder.](../media/devicesmanage.png)

## <a name="working-with-device-policies-in-intune"></a>Arbejde med enhedspolitikker i Intune

Brug følgende oplysninger til at oprette og administrere enhedspolitikker i Intune, der udføres via Slutpunktssikkerhed i Microsoft Endpoint Manager Administration.

### <a name="create-duplicate-and-edit-policies"></a>Opret, dupliker og rediger politikker

Sådan opretter du en politik i Intune

1. Log på Microsoft Endpoint Manager Administration.

1. Vælg **Slutpunktssikkerhed** og den type politik, du vil konfigurere, og vælg derefter **Opret politik**.

1. Vælg mellem følgende politiktyper:

    - Antivirus
    - Diskkryptering
    - Firewall
    - Slutpunktsregistrering og -svar
    - Reduktion af angrebsoverfladen
    - Kontobeskyttelse
    - Angiv følgende egenskaber:

1. Platform: Vælg den platform, du opretter politikken for. De tilgængelige indstillinger afhænger af den valgte politiktype.

1. Profil: Vælg mellem de tilgængelige profiler for den valgte platform. Du kan få oplysninger om profilerne i det dedikerede afsnit i denne artikel for at få oplysninger om den valgte politiktype.

1. Vælg **Opret**.

1. Angiv et navn og en beskrivelse til profilen på siden Grundlæggende, og vælg derefter **Næste**.

1. På siden Konfigurationsindstillinger skal du udvide hver gruppe af indstillinger og konfigurere de indstillinger, du vil administrere med denne profil.

1. Når du er færdig med at konfigurere indstillinger, skal du vælge **Næste**.

1. På siden Områdekoder skal du vælge **Vælg områdekoder** for at åbne ruden **Vælg mærker** for at tildele områdekoder til profilen.

1. Vælg **Næste** for at fortsætte.

1. På siden **Tildelinger** skal du vælge de grupper, der skal modtage denne profil. Du kan få flere oplysninger om tildeling af profiler under Tildel bruger- og enhedsprofiler.

1. Vælg **Næste**.

1. På siden Gennemse + opret skal du vælge **Opret**, når du er færdig. Den nye profil vises på listen, når du vælger politiktypen for den profil, du har oprettet.

Sådan duplikerer du en politik i Intune:

1. Log på Microsoft Endpoint Manager Administration.

1. Vælg den politik, du vil kopiere. Vælg **derefter Dupliker** , eller vælg ellipsen **(...)** til højre for politikken, og vælg **Dupliker**.
1. Angiv et nyt navn til politikken, og vælg derefter **Gem**.

Sådan redigerer du en politik:

1. Vælg den nye politik, og vælg derefter **Egenskaber**.

1. Vælg **Indstillinger** for at udvide en liste over konfigurationsindstillingerne i politikken. Du kan ikke ændre indstillingerne fra denne visning, men du kan gennemse, hvordan de er konfigureret.

1. Hvis du vil redigere politikken, skal du vælge **Rediger** for hver kategori, hvor du vil foretage en ændring:

    - Grundlæggende
    - Tildelinger
    - Områdekoder
    - Konfigurationsindstillinger

1. Når du har foretaget ændringer, skal du vælge **Gem** for at gemme dine ændringer. Redigeringer af én kategori skal gemmes, før du kan introducere ændringer til yderligere kategorier.

## <a name="manage-conflicts"></a>Administrer konflikter

Mange af de enhedsindstillinger, du kan administrere med sikkerhedspolitikker for slutpunkter, er også tilgængelige via andre politiktyper i Intune. Disse andre politiktyper omfatter politikker for enhedskonfiguration og grundlæggende sikkerhedsdata. Da indstillinger kan administreres via flere forskellige politiktyper eller af flere forekomster af samme politiktype, skal du være forberedt på at identificere og løse politikkonflikter for enheder, der ikke overholder de konfigurationer, du forventer.

Grundlæggende sikkerhedsindstillinger kan angive en værdi, der ikke er standardværdi, for en indstilling for at overholde den anbefalede konfiguration, der indeholder de oprindelige adresser.

Andre politiktyper, herunder sikkerhedspolitikker for slutpunkter, angiver værdien Ikke konfigureret som standard. Disse andre politiktyper kræver, at du eksplicit konfigurerer indstillingerne i politikken.

Uanset politikmetoden kan administration af den samme indstilling på den samme enhed via flere politiktyper eller via flere forekomster af samme politiktype resultere i konflikter, der bør undgås.

## <a name="see-also"></a>Se også

[Administrer slutpunktssikkerhed i Microsoft Intune](/mem/Intune/protect/endpoint-security)

[Bedste praksis for sikring af Microsoft 365 til virksomheder-planer](../admin/security-and-compliance/secure-your-business-data.md)

## <a name="next-objective"></a>Næste mål

[Konfigurer og administrer enhedsgrupper](m365bp-device-groups-mdb.md).