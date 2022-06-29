---
title: Øg trusselsbeskyttelsen for Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
- admindeeplinkMAC
- admindeeplinkEXCHANGE
- admindeeplinkSPO
search.appverid:
- BCS160
- MET150
description: Få hjælp til at øge beskyttelsesniveauet i Microsoft 365 Business Premium
ms.openlocfilehash: a4f76555fad2147477ab5bf9202c45123d1624f7
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66486049"
---
# <a name="increase-threat-protection-for-microsoft-365-business-premium"></a>Øg trusselsbeskyttelsen for Microsoft 365 Business Premium

I dette mål øger du din trusselsbeskyttelse med Microsoft 365 Business Premium. Det er vigtigt at beskytte din virksomhed mod phishing, malware og andre trusler. Denne målsætning indeholder oplysninger om:

- [Forudindstillede sikkerhedspolitikker](#review-and-apply-preset-security-policies) , der kan spare meget tid i forbindelse med konfiguration og konfiguration.
- [Brugerdefinerede sikkerhedspolitikker](#create-custom-security-policies) , som du kan definere, så de passer til dine forretningsbehov
- Sådan [justerer du dine delingsindstillinger for SharePoint- og OneDrive-filer og -mapper](#set-sharing-settings-for-sharepoint-and-onedrive-files-and-folders).
- [Advarselspolitikker](#review-your-alert-policies) , der overvåger bestemte filer, og hvordan de bruges.

## <a name="review-and-apply-preset-security-policies"></a>Gennemse og anvend forudindstillede sikkerhedspolitikker

Dit abonnement indeholder [forudindstillede sikkerhedspolitikker](../security/office-365-security/preset-security-policies.md) , der bruger anbefalede indstillinger til beskyttelse mod spam, antimalware og anti-phishing. Indbygget beskyttelse er som standard aktiveret. Overvej dog at anvende standard- eller streng beskyttelse for øget sikkerhed.

:::image type="content" source="media/m365bp-presetsecuritypolicies.png" alt-text="Skærmbillede af forudindstillede sikkerhedspolitikker.":::

> [!NOTE]
> Forudindstillede sikkerhedspolitikker er ikke det samme som [sikkerhedsstandarder](m365bp-conditional-access.md#security-defaults). Du bruger typisk *enten* sikkerhedsstandarder *eller* [Betinget adgang](m365bp-conditional-access.md#conditional-access) først, og derefter skal du tilføje dine sikkerhedspolitikker. [Forudindstillede sikkerhedspolitikker](#what-are-preset-security-policies) forenkler processen med at tilføje dine sikkerhedspolitikker. Du kan også [tilføje dine egne brugerdefinerede politikker](#create-custom-security-policies). 

### <a name="what-are-preset-security-policies"></a>Hvad er forudindstillede sikkerhedspolitikker?

Forudindstillede sikkerhedspolitikker beskytter dit mail- og samarbejdsindhold. Disse politikker består af:

- *Profiler*, der bestemmer beskyttelsesniveauet
- *Politikker* (f.eks. spam, antimalware, anti-phishing, spoof-indstillinger, repræsentation, vedhæftede filer og sikre links)
- *Politikindstillinger* (f.eks. grupper, brugere eller domæner for at modtage politikkerne og eventuelle undtagelser)

I følgende tabel opsummeres beskyttelsesniveauer og forudindstillede politiktyper.

| Beskyttelsesniveau | Beskrivelse |
|:---|:---|
| **Standardbeskyttelse** <br/>(*anbefales til de fleste virksomheder*) | Standardbeskyttelse bruger en grundlinjeprofil, der passer til de fleste brugere. Standardbeskyttelse omfatter anti-spam, antimalware, anti-phishing, spoof-indstillinger, repræsentationsindstillinger, sikre links og politikker for vedhæftede filer, der er tillid til.  |
| **Streng beskyttelse**  | Streng beskyttelse omfatter de samme typer politikker som standardbeskyttelse, men med strengere indstillinger. Hvis din virksomhed skal opfylde yderligere sikkerhedskrav eller -bestemmelser, kan du overveje at anvende streng beskyttelse for mindst dine prioriterede brugere eller mål med høj værdi. |
| **Indbygget beskyttelse** | Beskytter mod skadelige links og vedhæftede filer i mails. Indbygget beskyttelse er aktiveret og anvendt på alle brugere som standard.  |

> [!TIP]
> Du kan angive de brugere, grupper og domæner, der skal modtage forudindstillede politikker, og du kan definere visse undtagelser, men du kan ikke selv ændre de forudindstillede politikker. Hvis du vil bruge forskellige indstillinger for dine sikkerhedspolitikker, kan du oprette dine egne brugerdefinerede politikker, så de passer til din virksomheds behov.

### <a name="policy-order-of-priority"></a>Prioritetsrækkefølge for politik

Hvis brugere tildeles flere politikker, bruges en prioritetsrækkefølge til at anvende politikkerne. Prioritetsrækkefølgen fungerer på følgende måde:

1. **Streng beskyttelse** får den højeste prioritet og tilsidesætter alle andre politikker.

2. **Standardbeskyttelse** 

3. **Brugerdefinerede sikkerhedspolitikker**

4. **Indbygget beskyttelse** får den laveste prioritet og tilsidesættes af streng beskyttelse, standardbeskyttelse og brugerdefinerede politikker.

Streng beskyttelse tilsidesætter alle andre politikker, og indbygget beskyttelse tilsidesættes af de andre politikker. 

Hvis du vil vide mere om forudindstillede sikkerhedspolitikker, skal du se [Hvad forudindstillede sikkerhedspolitikker er lavet af](../security/office-365-security/preset-security-policies.md#what-preset-security-policies-are-made-of).

### <a name="how-do-i-assign-preset-security-policies-to-users"></a>Hvordan gør jeg tildele forudindstillede sikkerhedspolitikker til brugere?

> [!IMPORTANT]
> Før du begynder, skal du sørge for, at du har en af følgende roller tildelt i Exchange Online (som er inkluderet i dit abonnement):
> 
> - Global administrator
> - Organisationsadministration
> - Sikkerhedsadministrator
> 
> Du kan få mere at vide [under Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo) og [Om administratorroller](../admin/add-users/about-admin-roles.md).

Hvis du vil tildele forudindstillede sikkerhedspolitikker, skal du følge disse trin:

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Forudindstillede sikkerhedspolitikker** i afsnittet **Skabelonpolitikker** . Hvis du vil gå direkte til siden **Forudindstillede sikkerhedspolitikker** , skal du bruge <https://security.microsoft.com/presetSecurityPolicies>.

2. På siden **Forudindstillede sikkerhedspolitikker** skal du enten i afsnittet **Standardbeskyttelse** eller **Streng beskyttelse** ændre til/fra-knappen fra **Deaktiveret** til **Aktiveret** og derefter vælge **Administrer**.

3. Guiden **Anvend standardbeskyttelse** eller **Anvend streng beskyttelse** starter i et pop op-vindue. På **EOP-beskyttelsen gælder for siden skal** du identificere de interne modtagere, som politikkerne gælder for (modtagerbetingelser):
   - **Brugere**
   - **Grupper**
   - **Domæner**

   Klik i det relevante felt, begynd at skrive en værdi, og vælg derefter den ønskede værdi fra resultaterne. Gentag denne proces så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du vælge ikonet **Fjern** ud for værdien.

   For brugere eller grupper kan du bruge de fleste identifikatorer (navn, vist navn, alias, mailadresse, kontonavn osv.), men det tilsvarende viste navn vises i resultaterne. For brugere skal du skrive en stjerne (\*) alene for at se alle tilgængelige værdier.

   Hvis du vil angive en udeladelse, skal du markere afkrydsningsfeltet **Udelad disse brugere, grupper og domæner** og derefter angive brugere, grupper eller domæner, der skal udelades.

   Når du er færdig, skal du vælge **Næste**.

4. På **siden Defender for Office 365 beskyttelse gælder for** at identificere de interne modtagere, som politikkerne gælder for (modtagerbetingelser). Angiv brugere, grupper og domæner på samme måde som i det forrige trin.

   Klik på **Næste**, når du er færdig.

5. Kontrollér dine valg på siden **Gennemse og bekræft dine ændringer** , og vælg derefter **Bekræft**.

> [!TIP]
> Du kan få mere at vide om tildeling af forudindstillede sikkerhedspolitikker i følgende artikler:
> - [Tildel forudindstillede sikkerhedspolitikker til brugere](../security/office-365-security/preset-security-policies.md#assign-preset-security-policies-to-users)
> - [Anbefalede indstillinger for mail- og samarbejdsindhold](../security/office-365-security/recommended-settings-for-eop-and-office365.md) (Microsoft 365 Business Premium omfatter Exchange Online Protection og Microsoft Defender for Office 365 Plan 1)

## <a name="create-custom-security-policies"></a>Opret brugerdefinerede sikkerhedspolitikker

De [forudindstillede sikkerhedspolitikker](#what-are-preset-security-policies) , der er beskrevet tidligere i denne artikel, sikrer stærk beskyttelse af de fleste virksomheder. Du er dog ikke begrænset til kun at bruge forudindstillede sikkerhedspolitikker. Du kan definere dine egne brugerdefinerede sikkerhedspolitikker, så de passer til virksomhedens behov. 

Brug vores vejledning til hurtig start [, Beskyt mod trusler](../security/office-365-security/protect-against-threats.md), for at komme i gang med at oprette dine egne brugerdefinerede politikker. Vejledningen fører dig ikke kun gennem, hvordan du konfigurerer dine egne sikkerhedspolitikker. Den indeholder også anbefalede indstillinger, der skal bruges som udgangspunkt for:

- [Beskyttelse modmalware](../security/office-365-security/protect-against-threats.md#part-1---anti-malware-protection-in-eop)
- [Avanceret antiphishing-beskyttelse](../security/office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
- [Antispambeskyttelse](../security/office-365-security/protect-against-threats.md#part-3---anti-spam-protection-in-eop)
- [Sikre links og vedhæftede filer, der er tillid til](../security/office-365-security/protect-against-threats.md#part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365)

## <a name="set-sharing-settings-for-sharepoint-and-onedrive-files-and-folders"></a>Angiv delingsindstillinger for SharePoint- og OneDrive-filer og -mapper

Delingsniveauer er som standard angivet til det mest tilladte niveau for både SharePoint og OneDrive. Vi anbefaler, at du ændrer standardindstillingerne for bedre at beskytte din virksomhed.

1. Gå til <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Deling** i SharePoint Administration</a>, og log på med en konto, der har [administratortilladelser til din organisation](/sharepoint/sharepoint-admin-role).
 
2. Under **Ekstern deling** skal du angive delingsniveauet. (Vi anbefaler, at du bruger **Mindst tilladte** for at forhindre ekstern deling).

3. Under **Fil- og mappelinks** skal du vælge en indstilling (f.eks **. Bestemte personer**). Vælg derefter, om du vil tildele visnings- eller redigeringstilladelser som standard for delte links (f.eks **. Vis**).

4. Under **Andre indstillinger** skal du vælge de indstillinger, du vil bruge.

5. Vælg derefter **Gem**.

> [!TIP]
> Du kan få mere at vide om disse indstillinger under [Administrer delingsindstillinger](/sharepoint/turn-external-sharing-on-or-off).

## <a name="review-your-alert-policies"></a>Gennemse dine politikker for beskeder

Advarselspolitikker er nyttige til sporing af bruger- og administratoraktiviteter, potentielle malwaretrusler og datatabshændelser i din virksomhed. Dit abonnement indeholder et sæt standardpolitikker, men du kan også oprette brugerdefinerede politikker. Hvis du f.eks. gemmer en vigtig fil i SharePoint, som ingen skal dele eksternt, kan du oprette en meddelelse, der giver dig besked, hvis nogen deler den.

På følgende billede vises nogle af de standardpolitikker, der er inkluderet i Microsoft 365 Business Premium.

![Standardpolitikker for beskeder, der er inkluderet i Microsoft 365.](../media/alertpolicies.png)

### <a name="view-your-alert-policies"></a>Få vist dine politikker for beskeder

1. Gå til Microsoft Purview-compliance-portal på , og log på[https://compliance.microsoft.com](https://compliance.microsoft.com).

2. Vælg **Politikker** i navigationsruden, og vælg derefter **Beskedpolitikker**.

3. Vælg en individuel politik for at få vist flere oplysninger eller redigere politikken. På følgende billede vises en liste over politikker for beskeder med én politik valgt:

   :::image type="content" source="media/selected-alert-policy.png" lightbox="media/selected-alert-policy.png" alt-text="Skærmbillede af en valgt beskedpolitik.":::

> [!TIP]
> Du kan få flere oplysninger under [Politikker for beskeder](../compliance/alert-policies.md).

### <a name="how-to-view-alerts"></a>Sådan får du vist beskeder

Afhængigt af den specifikke besked kan du få vist dine beskeder enten på Microsoft 365 Defender-portalen eller i Microsoft Purview-compliance-portal.

| Beskedtype  | Sådan gør du  |
|---------|---------|
| Sikkerhedsadvarsel, f.eks. når en bruger klikker på et skadeligt link, en mail rapporteres som malware eller phish, eller en enhed registreres som indeholdende malware     | Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>, og vælg **Politikker & regler** > **Beskedpolitik** under **Mail & samarbejde**. Du kan også gå direkte til <https://security.microsoft.com/alertpolicies>. |
| Besked om overholdelse af regler og standarder, f.eks. når en bruger deler følsomme eller fortrolige oplysninger (advarsel om forebyggelse af datatab), eller der er en usædvanlig mængde ekstern fildeling (besked om styring af oplysninger)    | Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a>, og vælg derefter **Politikker** > **Beskedbeskedpolitikker** > .  |

Du kan få flere oplysninger under [Få vist beskeder](../compliance/alert-policies.md#view-alerts).

## <a name="disable-or-manage-calendar-sharing"></a>Deaktiver eller administrer kalenderdeling

Du kan forhindre personer i din organisation i at dele deres kalendere. Du kan også administrere, hvilket detaljeniveau de kan dele. Du kan f.eks. begrænse delingen til kun ledig/optaget tid.

1. Gå [til Organisationsindstillinger i Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2053743), og log på.

2. Vælg **Kalender**, og vælg, om personer i din organisation kan dele deres kalendere med personer uden for, der har Office 365 eller Exchange, eller med andre.

   Vi anbefaler, at du rydder indstillingen **Ekstern deling** .

   Hvis du vælger indstillingen Del med alle, kan du vælge også kun at dele oplysninger om ledig/optaget tid.

3. Vælg **Gem ændringer** nederst på siden.

   På følgende billede kan du se, at kalenderdeling ikke er tilladt.

   ![Skærmbillede af visning af ekstern kalenderdeling som ikke tilladt.](../media/nocalendarsharing.png)

   På følgende billede vises indstillingerne, når kalenderdeling er tilladt med et maillink med kun oplysninger om ledig/optaget tid.

   ![Skærmbillede af ledig/optaget kalenderdeling med alle.](../media/sharefreebusy.png)

Hvis brugerne har tilladelse til at dele deres kalendere, kan du se [disse instruktioner](https://support.office.com/article/7ecef8ae-139c-40d9-bae2-a23977ee58d5) for, hvordan de deler fra Outlook på internettet.

## <a name="next-steps"></a>Næste trin

Okay, lad os nu [**konfigurere disse ikke-administrerede BYOD-enheder**](m365bp-devices-overview.md).
