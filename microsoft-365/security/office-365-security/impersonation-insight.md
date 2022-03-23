---
title: Repræsentationsindsigt
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Administratorer kan lære, hvordan repræsentationsindsigtet fungerer. De kan hurtigt afgøre, hvilke afsendere der legitimt sender mails til deres organisationer fra domæner, der ikke består mailgodkendelseskontroller (SPF, DKIM eller DMARC).
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0d9d8ee89aaa551c5fecf7c38fe0dbba97ed7fc8
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63592221"
---
# <a name="impersonation-insight-in-defender-for-office-365"></a>Repræsentationsindsigt i Defender til Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> De funktioner, der er beskrevet i denne artikel, findes i Preview, kan blive ændret og er ikke tilgængelige i alle organisationer.

Efterligning er der, hvor afsenderen af en mail ligner meget en rigtig eller forventet afsendermailadresse. Hackere bruger ofte efterligninger af afsendermailadresser i phishing eller andre typer angreb for at opnå modtagerens tillid. Der er grundlæggende to former for efterligning:

- **Domæne efterligning**: I lila@contoso.com er den efterligning af afsenderens mailadresse lila@ćóntoso.com.
- **Bruger efterligning**: I michelle@contoso.com er den efterligning af afsenderens mailadresse rnichell@contoso.com.

Domæne efterligning er anderledes end [domænespoofing](anti-spoofing-protection.md), fordi det efterlignede domæne typisk er et rigtigt, registreret domæne. Meddelelser fra afsendere i det efterligne domæne kan og ofte bestå almindelige kontroller til godkendelse af mails, som ellers ville identificere spoofingforsøg (SPF, DKIM og DMARC).

Beskyttelse mod efterligning er en del af politikindstillingerne for antiphishing, der er forbeholdt Microsoft Defender Office 365. Du kan finde flere oplysninger om disse indstillinger [under Indstillinger for repræsentation i antiphishing-politikker i Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

Du kan bruge repræsentationsindsigtet i Microsoft 365 Defender-portalen til hurtigt at identificere meddelelser fra efterligninger af afsendere eller afsenderdomæner, som du har konfigureret til repræsentationsbeskyttelse.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til **antiphishing-siden** skal du bruge <https://security.microsoft.com/antiphishing>. For at gå direkte til **siden Repræsentationsindsigt** skal du bruge <https://security.microsoft.com/impersonationinsight>.

- Du skal have tildelt tilladelser i Microsoft 365 Defender, før du kan udføre procedurerne i denne artikel:
  - **Organisationsadministration**
  - **Sikkerhedsadministrator**
  - **Sikkerhedslæser**
  - **Global læser**

  Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

  **Bemærk**! Når du føjer brugere til den tilsvarende Azure Active Directory-rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser i _Microsoft 365 Defender-portalen og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).

- Du aktiverer og konfigurerer repræsentationsbeskyttelse i antiphishing-politikker i Microsoft Defender til Office 365. Repræsentationsbeskyttelse er ikke aktiveret som standard. Få mere at vide under [Konfigurer antiphishing-politikker i Microsoft Defender Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="open-the-impersonation-insight-in-the-microsoft-365-defender-portal"></a>Åbn repræsentationsindsigtet i Microsoft 365 Defender portalen

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til  & **politikker** \> for **samarbejde & Politikker** \> \> for trussel mod **phishing** i **sektionen** Politikker. For at gå direkte til **antiphishing-siden** skal du bruge <https://security.microsoft.com/antiphishing>.

2. På siden **Antiphishing** ser efterligningsindsigt således ud:

   ![Repræsentationsindsigt og efterlignet intelligens på siden for antiphishing-politik.](../../media/m365-sc-impersonation-and-spoof-intelligence-insight.png)

   Indsigten har to tilstande:

    - **Insight-tilstand**: Hvis repræsentationsbeskyttelse er aktiveret og konfigureret i antiphishing-politikker, viser indsigten antallet af registrerede meddelelser fra efterligninger af domæner og efterligninger af brugere (afsendere) i løbet af de seneste syv dage. Dette er det samlede antal registrerede efterligninger af afsendere fra alle antiphishing-politikker.
    - Hvad hvis-tilstand **: Hvis** repræsentationsbeskyttelse ikke er aktiveret og konfigureret i nogen aktiv antiphishing-politik, viser indsigten,  hvor mange meddelelser der ville være blevet registreret af vores funktioner til repræsentationsbeskyttelse i løbet af de seneste syv dage.

Hvis du vil have vist oplysninger om repræsentationsregistreringerne, skal du klikke på Vis **repræsentationer** i repræsentationsindsigtet.

   > [!NOTE]
   > Du kan finde oplysninger om efterlignet intelligensindsigt i [Spoof intelligence-indsigt i EOP](learn-about-spoof-intelligence.md).

## <a name="view-information-about-messages-from-senders-in-impersonated-domains"></a>Få vist oplysninger om meddelelser fra afsendere i efterligninger af domæner

På siden **Impersonation Insight**, der vises, når du  har klikket på Vis repræsentationer i **repræsentationsindsigtet**, skal du kontrollere, at fanen Domæner er markeret. Fanen **Domæner** indeholder følgende oplysninger:

- **Afsenderdomæne**: Det efterligning af domæne, som er det domæne, der blev brugt til at sende mailen.
- **Antal meddelelser**: Antallet af meddelelser fra at udgive sig for at være afsenderdomæne i løbet af de seneste 7 dage.
- **Repræsentationstype**: Denne værdi viser den registrerede placering af efterligningen (f.eks. **Domæne i adresse**).
- **Efterligning** af domæne:Det efterligne domæne, der ligner det domæne, der er konfigureret til beskyttelse mod efterligning i antiphishing-politikken.
- **Domænetype**: Denne værdi er **Firmadomæne** for interne domæner eller **Brugerdefineret domæne** til brugerdefinerede domæner.
- **Politik**: Politikken for antiphishing, der har registreret det efterligning af domænet.
- **Tilladelse til at repræsentere**: En af følgende værdier:
  - **Ja**: Domænet blev konfigureret som et domæne, der er tillid til (en undtagelse for efterligning af beskyttelse) i antiphishing-politikken. Meddelelser fra afsendere i det efterligne domæne blev registreret, men tilladt.
  - **Nej**: Domænet er konfigureret til beskyttelse mod efterligning i antiphishing-politikken. Meddelelser fra afsendere i det efterligninger domæne blev registreret og reageret på baseret på handlingen for efterligninger af domæner i antiphishing-politikken.

Du kan klikke på markerede kolonneoverskrifter for at sortere resultaterne.

Hvis du vil filtrere resultaterne, kan du bruge ![ikonet Søg.](../../media/m365-cc-sc-search-icon.png) **Søgefelt** til at angive en kommasepareret liste over værdier for at filtrere resultaterne.

### <a name="view-details-about-messages-from-senders-in-impersonated-domains"></a>Få vist oplysninger om meddelelser fra afsendere i efterligninger af domæner

På fanen **Domæner på siden Repræsentationsindsigt** skal du vælge en af de tilgængelige repræsentationsregistreringer. Pop op-vindue med oplysninger, der vises, indeholder følgende oplysninger og funktioner:

- **Valg af repræsentationspolitik, der skal ændres**: Vælg den pågældende antiphishing-politik, du vil ændre. Det er kun de politikker, hvor det efterligne domæne er defineret i politikken, der er tilgængelige. Se den forrige side for at se, hvilken politik der faktisk var ansvarlig for at registrere det efterligne domæne (sandsynligvis baseret på modtageren og politikkens prioritet).
- **Føj til** listen over tilladte repræsentationer: Brug denne til/fra-knap til at tilføje eller fjerne afsenderen fra de Afsendere og domæner, der er tillid til ( **repræsentationsundtagelser** ) for den antiphishingpolitik, du har valgt:
  - Hvis værdien **Tilladt at repræsentere** for denne post var **Nej**, er til/fra-knappen slået fra. Hvis du vil undtage alle afsendere på dette domæne fra evaluering ved at angive beskyttelse efter efterligning, skal du skubbe til/fra-knappen til Til: ![Til.](../../media/scc-toggle-on.png). Domænet føjes til **listen Domæner, der** er tillid til under indstillingerne for beskyttelse mod phishing i antiphishing-politikken.
  - Hvis værdien **Tilladt at repræsentere** for denne indtastning var **Ja**, er til/fra-knappen til. Hvis du vil have alle afsendere på dette domæne tilbage, så de kan evalueres via repræsentationsbeskyttelse, skal du skubbe til/fra-knappen til fra: ![Slå fra.](../../media/scc-toggle-off.png). Domænet fjernes fra listen **Domæner, der er tillid** til under indstillingerne for beskyttelse mod phishing i antiphishing-politikken.
- Derfor har vi opdaget dette.
- Det skal du gøre.
- En domæneoversigt, der viser det efterligne domæne.
- WhoIs data about the sender.
- Et link til at åbne [Threat Explorer](threat-explorer.md) for at få vist flere oplysninger om afsenderen.
- Lignende meddelelser fra den samme afsender, der blev leveret til din organisation.

## <a name="view-information-about-messages-from-impersonated-senders"></a>Få vist oplysninger om meddelelser fra efterligninger af afsendere

På siden **Impersonation insight**, der vises, når du  klikker på Vis repræsentationer i repræsentationsindsigtet, skal du klikke på **fanen** Brugere. Fanen **Brugere** indeholder følgende oplysninger:

- **Afsender**: Mailadressen på den efterligning af afsender, der har sendt mailen.
- **Antal meddelelser**: Antallet af meddelelser fra den efterligning af afsender i løbet af de seneste 7 dage.
- **Repræsentationstype: Denne** værdi er **Bruger i vist navn**.
- **Efterligning** af brugere: Mailadressen på den efterligning af afsender, der skal ligne den bruger, der er konfigureret til beskyttelse mod efterligning i antiphishing-politikken.
- **Brugertype**: Denne værdi viser den type beskyttelse, der anvendes (f.eks. **Beskyttet bruger-** eller **Postkasseintelligens**).
- **Politik**: Antiphishing-politikken, der har registreret den efterligning af afsenderen.
- **Tilladelse til at repræsentere**: En af følgende værdier:
  - **Ja**: Afsenderen blev konfigureret som en bruger, der er tillid til (en undtagelse for repræsentationsbeskyttelse) i antiphishingpolitikken. Meddelelser fra den efterligning af afsenderen blev fundet, men tilladt.
  - **Nej**: Afsenderen er konfigureret til beskyttelse mod efterligning i antiphishing-politikken. Meddelelser fra den efterligning af afsenderen blev registreret og reageret på baseret på handlingen for efterligne brugere i antiphishingpolitikken.

Du kan klikke på markerede kolonneoverskrifter for at sortere resultaterne.

Hvis du vil filtrere resultaterne, kan du bruge feltet **Filtrer** afsender til at angive en kommasepareret liste over værdier til at filtrere resultaterne.

### <a name="view-details-about-messages-from-impersonated-senders"></a>Få vist oplysninger om meddelelser fra efterligninger af afsendere

På fanen **Brugere** på siden **Repræsentationsindsigt** skal du vælge en af de tilgængelige repræsentationsregistreringer. Pop op-vindue med oplysninger, der vises, indeholder følgende oplysninger og funktioner:

- **Valg af repræsentationspolitik, der skal ændres**: Vælg den pågældende antiphishing-politik, du vil ændre. Det er kun politikker, hvor den efterligning af afsenderen, der er defineret i politikken, er tilgængelige. Se den forrige side for at se, hvilken politik der faktisk var ansvarlig for at registrere den efterligning af afsenderen (sandsynligvis baseret på modtageren og politikkens prioritet).
- **Føj til** listen over tilladte repræsentationer: Brug denne til/fra-knap til at tilføje eller fjerne afsenderen fra de Afsendere og domæner, der er tillid til ( **repræsentationsundtagelser** ) for den antiphishingpolitik, du har valgt:
  - Hvis værdien **Tilladt at repræsentere** for denne post var **Nej**, er til/fra-knappen slået fra. For at undtage afsenderen fra evaluering ved repræsentationsbeskyttelse skal du skubbe til/fra-knappen til Til: ![Til/fra.](../../media/scc-toggle-on.png). Afsenderen føjes til listen **Brugere, der er** tillid til i indstillingerne for beskyttelse mod efterligning i antiphishing-politikken.
  - Hvis værdien **Tilladt at repræsentere** for denne indtastning var **Ja**, er til/fra-knappen til. Hvis du vil returnere afsenderen til evaluering ved repræsentationsbeskyttelse, skal du skubbe til/fra-knappen til fra: ![Slå fra.](../../media/scc-toggle-off.png). Afsenderen fjernes fra listen Brugere **, der er tillid** til i indstillingerne for beskyttelse mod efterligning i antiphishing-politikken.
- Derfor har vi opdaget dette.
- Det skal du gøre.
- En afsenderoversigt, der viser den efterligning af afsenderen.
- WhoIs data about the sender.
- Et link til at åbne [Threat Explorer](threat-explorer.md) for at få vist flere oplysninger om afsenderen.
- Lignende meddelelser fra den samme afsender, der blev leveret til din organisation.
