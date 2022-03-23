---
title: Oversigt over brug af oprindelige planer til installation af standardlejerkonfigurationer
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
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
description: For administrerede tjenesteudbydere, der bruger Microsoft 365 Lighthouse, kan du få mere at vide om at bruge grundlinjer til at udrulle standardlejerkonfigurationer.
ms.openlocfilehash: 643bb962277d30caf8ea067b9276a5986af8914f
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/15/2022
ms.locfileid: "63592485"
---
# <a name="overview-of-using-baselines-to-deploy-standard-tenant-configurations"></a>Oversigt over brug af oprindelige planer til installation af standardlejerkonfigurationer 

Microsoft 365 Lighthouse giver dig en gentagelig og skalerbar måde, hvorpå du kan administrere Microsoft 365 på tværs af flere kundelejere. Oprindelige planer giver standardlejerkonfigurationer, der udruller centrale sikkerhedspolitikker og overholdelsesstandarder, der holder dine lejeres brugere, enheder og data sikre.

Du kan få vist standard oprindelige planer og installationstrinnene fra Fyrtårn. Hvis du vil anvende en oprindelig plan for en lejer, **skal du vælge** Lejere i venstre navigationsrude og derefter vælge en lejer. Gå derefter til fanen **Installationsplaner for** at starte installationen.

## <a name="lighthouse-baseline"></a>Grundlinjen Fyrtårn

Konfigurationer af grundlinjer for fyrtårne er designet til at sikre, at alle administrerede lejere er sikre og kompatible. Vælg **Grundlinjer i venstre navigationsrude** for at få vist den standardlinje, der gælder for alle lejere.  Hvis du vil have vist installationstrinnene, der er inkluderet i standarden for den oprindelige plan, skal du vælge Vis **oprindelig plan** for at åbne standardsiden for den oprindelige plan. Vælg en af installationstrinnene for at få vist installationsdetaljer og brugerpåvirkning.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/default-baseline-page.png" alt-text="Skærmbillede af siden Standard for grundlinje.":::

### <a name="default-lighthouse-configurations"></a>Standardkonfigurationer af fyrtårne

| Konfiguration af grundlinje | Beskrivelse |
|--|--|
| Kræv MFA for administratorer | En politik for betinget adgang, der kræver multifaktorgodkendelse for alle administratorer. Det er påkrævet for alle skyprogrammer. Du kan finde flere oplysninger om denne oprindelige plan [under Betinget adgang: Kræv MFA til alle administratorer](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa).|
| Kræv MFA for slutbrugere | En politik for betinget adgang, der kræver multifaktorgodkendelse for alle brugere.  Det er påkrævet for alle skyprogrammer. Du kan finde flere oplysninger om denne grundlinje [i Betinget adgang: Kræv MFA for alle brugere](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa). |
| Bloker ældre godkendelse | En politik for betinget adgang til at blokere ældre klientgodkendelse. Du kan finde flere oplysninger om denne grundlinje [under Bloker ældre godkendelse til Azure AD med betinget adgang](/azure/active-directory/conditional-access/block-legacy-authentication).|
| Konfigurere tilmelding af enhed | Tilmelding af enhed for at give dine lejerenheder tilladelse til at tilmelde sig Microsoft Endpoint Manager. Dette gøres ved at konfigurere automatisk registrering mellem Azure Active Directory og Microsoft Endpoint Manager. Du kan finde flere oplysninger om denne [grundlinje i Konfigurere tilmelding til Windows enheder](/mem/intune/enrollment/windows-enroll). |
| Konfigurer Microsoft Defender Antivirus til Windows 10 og nyere | En enhedskonfigurationsprofil for Windows enheder med forudkonfigurerede Microsoft Defender Antivirus indstillinger. Du kan finde flere oplysninger om denne [grundlinje under Konfigurer Microsoft Defender til slutpunkt i Intune](/mem/intune/protect/advanced-threat-protection-configure).|
| Konfigurer Microsoft Defender Firewall til Windows 10 og nyere | En firewallpolitik, der hjælper med at sikre enheder ved at forhindre uønsket og uautoriseret netværkstrafik. Du kan finde flere oplysninger om denne [grundlinje i Bedste fremgangsmåder til konfiguration Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/best-practices-configuring).  |
| Konfigurere en politik for enhedsoverholdelse for Windows 10 og nyere | En Windows af enheder med forudkonfigurerede indstillinger, der opfylder de grundlæggende krav til overholdelse af regler og standarder. Du kan finde flere oplysninger om denne grundlinje under [Betinget adgang: Kræv kompatibel eller hybrid Azure AD-enhed, der er forbundet](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device). |

## <a name="deployment-plans"></a>Udrulningsplaner

Hver aktiv lejer har en installationsplan, der omfatter installationstrinnene fra Microsoft 365 Lighthouse-grundlinjen. For at få adgang til en **lejers** installationsplan skal du vælge en aktiv lejer på listen på siden Lejere og derefter vælge **fanen Installationsplan** .

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/deployment-plan-tab.png" alt-text="Skærmbillede af fanen Installationsplan.":::

Fanen Installationsplan indeholder følgende oplysninger:


|Kolonne  |Beskrivelse  |
|---------|---------|
|Installationstrin     |  Beskrivelse af installationstrin.       |
|Status     |Status for installationstrinnet.         |
|Oprindelig plan     |Den oprindelige plan, som installationstrinnet er afledt af.         |
|Kategori     | Uanset om installationstrinnet er knyttet til administration af enheder, identitet eller data.        |
|Senest opdateret    | Den dato, hvor installationstrinnet sidst blev opdateret.        |


Fanen Udrulningsplan indeholder også følgende indstillinger:

- **Eksportér:** Vælg for at eksportere installationstrindata Excel en fil med kommaseparerede værdier (.csv).
- **Opdater:** Vælg for at hente de mest aktuelle installationstrindata.
- **Søg:** Angiv nøgleord for hurtigt at finde et bestemt installationstrin på listen.

## <a name="deployment-steps-and-processes"></a>Installationstrin og -processer

Hver lejers installationsplan omfatter installationstrinnene fra den oprindelige Microsoft 365 Lighthouse. Hvert installationstrin består af en eller flere processer, der skal udføres for at opfylde kravene til installationstrinnet. Når en ny lejer bliver aktiv, skal du fuldføre installationsaktiviteter, der er knyttet til installationstrinnene og -processerne.

For hvert installationstrin kan du udføre følgende handlinger:

|Handling  |Beskrivelse  |
|---------|---------|
| Del    |  Aktiverer indholdet af Installationstrinnet til at blive delt via et link eller via mail.    |
| Gennemse og installér    |  Gør det muligt for brugeren at: <ul><li>Når de understøttes, kan du sammenligne konfigurationsindstillingerne i installationstrinnet med indstillingerne i eventuelle eksisterende politikker uden at udrulle indstillingerne for lejeren.<br>Følgende installationstrin understøtter sammenligning:</br><ul><li>Konfigurere en politik for enhedsoverholdelse for Windows 10 og nyere</li><li>Kræv MFA for slutbrugere</li><li>Kræv MFA for administratorer</li><li>Bloker ældre godkendelse</li></ul></li> <li>Installér konfigurationsindstillingerne for lejeren.</li></ul>**Bemærk!** Trin, der ikke understøtter muligheden for at sammenligne uden at udrulle indstillingerne for lejeren, gør det muligt at gennemgå konfigurationsindstillingerne og installere dem.|
| Opdater status for handlingsplan    |  Gør det muligt for brugeren at rapportere status for deres handlingsplan for installationstrinnet.      |

## <a name="related-content"></a>Relateret indhold

[Installér Microsoft 365 Lighthouse-grundlinjer](m365-lighthouse-deploy-baselines.md) (artikel)\
[Almindelige betingede adgangspolitikker](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) (artikel)\
[Microsoft 365 ofte stillede spørgsmål om fyrtårn](m365-lighthouse-faq.yml) (artikel)
