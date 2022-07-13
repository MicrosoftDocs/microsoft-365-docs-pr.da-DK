---
title: Oversigt over brug af Microsoft 365 Lighthouse baselines til installation af standard lejerkonfigurationer
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: shcallaw, kywirpel
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: For MSP'er (Managed Service Providers) ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om, hvordan du bruger grundlinjer til at installere standard lejerkonfigurationer.
ms.openlocfilehash: 064968cd75804167493e696f08c3bec764598c94
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66749149"
---
# <a name="overview-of-using-microsoft-365-lighthouse-baselines-to-deploy-standard-tenant-configurations"></a>Oversigt over brug af Microsoft 365 Lighthouse baselines til installation af standard lejerkonfigurationer 

Microsoft 365 Lighthouse baselines giver dig en gentagelig og skalerbar måde at administrere Sikkerhedsindstillinger for Microsoft 365 på tværs af flere kundelejere. Grundlinjer indeholder standardlejerkonfigurationer, der installerer kernesikkerhedspolitikker og standarder for overholdelse af angivne standarder, som holder dine lejers brugere, enheder og data sikre.

Du kan få vist standardgrundlinjen og dens installationstrin inde fra Lighthouse. Hvis du vil anvende en oprindelig plan på en lejer, skal du vælge **Lejere i venstre navigationsrude** og derefter vælge en lejer. Derefter skal du gå til fanen **Udrulningsplaner** for at starte udrulningen.

## <a name="lighthouse-baseline"></a>Grundlinje for fyrtårn

Konfigurationer af fyrtårnsgrundlinje er designet til at sikre, at alle administrerede lejere er sikre og kompatible. Vælg **Oprindelige planer** i navigationsruden til venstre for at få vist den standardgrundlinje, der gælder for alle lejere.  Hvis du vil have vist de installationstrin, der er inkluderet i standardgrundlinjen, skal du vælge **Vis oprindelig plan** for at åbne siden **Standardgrundlinje** . Vælg et af installationstrinnene for at få vist installationsdetaljer og brugerpåvirkning.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/default-baseline-page.png" alt-text="Skærmbillede af siden Standardgrundlinje.":::

### <a name="default-lighthouse-configurations"></a>Standardkonfigurationer for fyrtårn

| Oprindelig konfiguration | Beskrivelse |
|--|--|
| Kræv MFA for administratorer | En politik for betinget adgang, der kræver multifaktorgodkendelse for alle administratorer. Det er påkrævet til alle cloudprogrammer. Du kan få flere oplysninger om denne oprindelige plan under [Betinget adgang: Kræv MFA for alle administratorer](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa).|
| Kræv MFA for slutbrugere | En politik for betinget adgang, der kræver multifaktorgodkendelse for alle brugere.  Det er påkrævet til alle cloudprogrammer. Du kan få flere oplysninger om denne oprindelige plan under [Betinget adgang: Kræv MFA for alle brugere](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa). |
| Bloker ældre godkendelse | En politik for betinget adgang til at blokere ældre klientgodkendelse. Du kan få flere oplysninger om denne oprindelige plan under [Bloker ældre godkendelse for at Azure AD med betinget adgang](/azure/active-directory/conditional-access/block-legacy-authentication).|
| Konfigurer tilmelding af enhed | Enhedsregistrering, så dine lejerenheder kan tilmelde sig Microsoft Endpoint Manager. Dette gøres ved at konfigurere automatisk tilmelding mellem Azure Active Directory og Microsoft Endpoint Manager. Du kan få flere oplysninger om denne baseline under [Konfigurer tilmelding til Windows-enheder](/mem/intune/enrollment/windows-enroll). |
| Konfigurer Microsoft Defender til virksomheder | Klargør lejeren til Microsoft Defender til virksomheder og onboarder de enheder, der allerede er tilmeldt Microsoft Endpoint Manager, til Microsoft Defender til virksomheder. Du kan få flere oplysninger under [Hvad er Microsoft Defender til virksomheder?](../security/defender-business/mdb-overview.md) |
| Konfigurer Exchange Online Protection og Microsoft Defender for Office 365 | En politik, der anvender anbefalede politikker for anti-spam, anti-malware, anti-phishing, sikre links og politikker for sikker vedhæftede filer til dine lejere Exchange Online postkasser. |
| Konfigurer Microsoft Defender Antivirus til Windows 10 og nyere | En enhedskonfigurationsprofil til Windows-enheder med forudkonfigurerede Indstillinger for Microsoft Defender Antivirus. Du kan få flere oplysninger om denne oprindelige plan [under Konfigurer Microsoft Defender for Endpoint i Intune](/mem/intune/protect/advanced-threat-protection-configure).|
| Konfigurer Microsoft Defender Firewall til Windows 10 og nyere | En firewallpolitik, der hjælper med at beskytte enheder ved at forhindre uønsket og uautoriseret netværkstrafik. Du kan få flere oplysninger om denne oprindelige plan under [Bedste fremgangsmåder til konfiguration af Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/best-practices-configuring).  |
| Konfigurer en politik for enhedsoverholdelse for Windows 10 og nyere | En Windows-enhedspolitik med forudkonfigurerede indstillinger, der opfylder grundlæggende krav til overholdelse af angivne standarder. Du kan få flere oplysninger om denne grundlinje under [Betinget adgang: Kræv kompatibel eller hybrid Azure AD tilsluttet enhed](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device). |

## <a name="deployment-plans"></a>Udrulningsplaner

Hver aktiv lejer har en udrulningsplan, der indeholder installationstrinnene fra Microsoft 365 Lighthouse Baseline. Hvis du vil have adgang til en lejers udrulningsplan, skal du vælge en aktiv lejer på listen på siden **Lejere** og derefter vælge fanen **Udrulningsplan** .

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/deployment-plan-tab.png" alt-text="Skærmbillede af fanen Installationsplan.":::

Fanen Installationsplan indeholder følgende oplysninger:


|Kolonne  |Beskrivelse  |
|---------|---------|
|Installationstrin     |  Beskrivelse af installationstrin.       |
|Status     |Status for installationstrinnet.         |
|Oprindelige     |Den oprindelige plan, som udrulningstrinnet er afledt fra.         |
|Kategori     | Angiver, om installationstrinnet er knyttet til administration af enheder, identitet eller data.        |
|Senest opdateret    | Den dato, hvor udrulningstrinnet sidst blev opdateret.        |


Fanen Installationsplan indeholder også følgende indstillinger:

- **Eksport:** Vælg at eksportere data for installationstrin til en Excel-fil med kommaseparerede værdier (.csv).
- **Opdatere:** Vælg at hente de nyeste data for udrulningstrinnet.
- **Søg:** Angiv nøgleord for hurtigt at finde et bestemt installationstrin på listen.

## <a name="deployment-steps-and-processes"></a>Installationstrin og -processer

Hver lejers udrulningsplan indeholder installationstrinnene fra Microsoft 365 Lighthouse Baseline. Hvert installationstrin indeholder en eller flere processer, der skal fuldføres. Når en ny lejer bliver aktiv, skal du fuldføre udrulningsaktiviteter, der er knyttet til udrulningstrinnene og -processerne.

For hvert installationstrin kan du foretage følgende handlinger:

|Handling  |Beskrivelse  |
|---------|---------|
| Del    |  Gør det muligt at dele indholdet af installationstrinnet via et link eller via mail.    |
| Gennemse og udrul    |  Gør det muligt for brugeren at: <ul><li>Når det understøttes, skal du sammenligne konfigurationsindstillingerne i installationstrinnet med indstillinger i eksisterende politikker uden at installere indstillingerne i lejeren.<br>Følgende installationstrin understøtter sammenligning:</br><ul><li>Konfigurer en politik for enhedsoverholdelse for Windows 10 og nyere</li><li>Kræv MFA for slutbrugere</li><li>Kræv MFA for administratorer</li><li>Bloker ældre godkendelse</li></ul></li> <li>Udrul konfigurationsindstillingerne til lejeren.</li></ul>**Bemærk:** Trin, der ikke understøtter muligheden for at sammenligne uden at installere indstillingerne i lejeren, giver dig mulighed for at gennemse konfigurationsindstillingerne og installere dem.|
| Opdater status for handlingsplan    |  Giver brugeren mulighed for at rapportere status for sin handlingsplan for udrulningstrinnet.      |

## <a name="related-content"></a>Relateret indhold

[Installér Microsoft 365 Lighthouse baselines](m365-lighthouse-deploy-baselines.md) (artikel)\
[Almindelige politikker for betinget adgang](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) (artikel)\
[Ofte stillede spørgsmål om Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (artikel)
