---
title: Indsigt i efterligning
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
description: Administratorer kan få mere at vide om, hvordan repræsentationsindsigten fungerer. De kan hurtigt afgøre, hvilke afsendere der lovligt sender mail til deres organisationer fra domæner, der ikke består kontrol af mailgodkendelse (SPF, DKIM eller DMARC).
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c54bdbb4ee8c3bf068b40df8cd5ca0a58da2392f
ms.sourcegitcommit: 221212fff9737e0ea386755deb8fed62ae9c254b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/14/2022
ms.locfileid: "66787742"
---
# <a name="impersonation-insight-in-defender-for-office-365"></a>Repræsentationsindsigt i Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Repræsentation er det område, hvor afsenderen af en mail ligner en rigtig eller forventet afsendermailadresse. Personer med ondsindede hensigter repræsenterer ofte afsendermailadresser i phishing eller andre typer angreb for at opnå modtagerens tillid. Der er grundlæggende to typer repræsentation:

- **Repræsentation af domæne**: I stedet for lila@contoso.com er den repræsenterede afsenders mailadresse lila@ćóntoso.com.
- **Brugerpræsentation**: I stedet for michelle@contoso.com er den repræsenterede afsenders mailadresse rnichell@contoso.com.

Repræsentation af domæner adskiller sig fra [domænepoofing](anti-spoofing-protection.md), fordi det repræsenterede domæne typisk er et reelt, registreret domæne. Meddelelser fra afsendere i det repræsenterede domæne kan og kan ofte bestå almindelige kontroller af godkendelse via mail, der ellers ville identificere spoofingforsøg (SPF, DKIM og DMARC).

Repræsentationsbeskyttelse er en del af de indstillinger for anti-phishing-politik, der kun gælder for Microsoft Defender for Office 365. Du kan få flere oplysninger om disse indstillinger [under Repræsentationsindstillinger i politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

Du kan bruge repræsentationsindsigten på Microsoft 365 Defender-portalen til hurtigt at identificere meddelelser fra repræsenterede afsendere eller afsenderdomæner, som du har konfigureret til repræsentationsbeskyttelse.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Anti-phishing** , skal du bruge <https://security.microsoft.com/antiphishing>. Hvis du vil gå direkte til siden **Repræsentationsindsigt** , skal du bruge <https://security.microsoft.com/impersonationinsight>.

- Du skal have tildelt tilladelser på Microsoft 365 Defender-portalen, før du kan udføre procedurerne i denne artikel:
  - **Organisationsadministration**
  - **Sikkerhedsadministrator**
  - **Sikkerhedslæser**
  - **Global læser**

  Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).

  **Bemærk**! Hvis du føjer brugere til den tilsvarende Azure Active Directory-rolle i Microsoft 365 Administration får brugerne de nødvendige tilladelser på Microsoft 365 Defender-portalen _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).

- Du aktiverer og konfigurerer repræsentationsbeskyttelse i politikker til bekæmpelse af phishing i Microsoft Defender for Office 365. Repræsentationsbeskyttelse er ikke aktiveret som standard. Du kan få flere oplysninger under [Konfigurer politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="open-the-impersonation-insight-in-the-microsoft-365-defender-portal"></a>Åbn repræsentationsindsigten i Microsoft 365 Defender-portalen

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-phishing** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Anti-phishing** , skal du bruge <https://security.microsoft.com/antiphishing>.

2. På siden **Anti-phishing** ser repræsentationsindsigten sådan ud:

   :::image type="content" source="../../media/m365-sc-impersonation-insight.png" alt-text="Repræsentationsindsigten på siden Anti-phishing-politik på portalen Microsoft 365 Defender." lightbox="../../media/m365-sc-impersonation-insight.png":::

   Indsigten har to tilstande:

    - **Indsigtstilstand**: Hvis repræsentationsbeskyttelse er aktiveret og konfigureret i nogen anti-phishing-politikker, viser indsigten antallet af registrerede meddelelser fra repræsenterede domæner og repræsenterede brugere (afsendere) i løbet af de seneste syv dage. Dette er det samlede antal registrerede repræsenterede afsendere fra alle politikker til bekæmpelse af phishing.
    - **What if-tilstand**: Hvis repræsentationsbeskyttelse ikke er aktiveret og konfigureret i nogen aktive anti-phishing-politikker, viser indsigten, hvor mange meddelelser der *ville* være blevet registreret af vores repræsentationsbeskyttelsesfunktioner i løbet af de seneste syv dage.

Hvis du vil have vist oplysninger om repræsentationsregistreringer, skal du klikke på **Vis repræsentationer** i repræsentationsindsigten.

## <a name="view-information-about-messages-from-senders-in-impersonated-domains"></a>Få vist oplysninger om meddelelser fra afsendere i repræsenterede domæner

På siden **Repræsentationsindsigt** , der vises, når du har klikket på **Vis repræsentationer** i repræsentationsindsigten, skal du kontrollere, at fanen **Domæner** er valgt. Fanen **Domæner** indeholder følgende oplysninger:

- **Afsenderdomæne**: Det repræsenterende domæne, som er det domæne, der blev brugt til at sende mailen.
- **Antal meddelelser**: Antallet af meddelelser fra repræsentation af afsenderdomæne i løbet af de seneste 7 dage.
- **Repræsentationstype**: Denne værdi viser den registrerede placering af repræsentationen (f.eks **. Domæne i adresse**).
- **Repræsenterede domæner**: Det repræsenterede domæne, som skal ligne det domæne, der er konfigureret til repræsentationsbeskyttelse i politikken til bekæmpelse af phishing.
- **Domænetype**: Denne værdi er **Firmadomæne** for interne domæner eller **Brugerdefineret domæne** for brugerdefinerede domæner.
- **Politik**: Politikken til bekæmpelse af phishing, der registrerede det repræsenterede domæne.
- **Tilladt at repræsentere**: En af følgende værdier:
  - **Ja**: Domænet blev konfigureret som et domæne, der er tillid til (en undtagelse for repræsentationsbeskyttelse) i politikken til bekæmpelse af phishing. Meddelelser fra afsendere i det repræsenterede domæne blev registreret, men tilladt.
  - **Nej**: Domænet er konfigureret til repræsentationsbeskyttelse i politikken til bekæmpelse af phishing. Meddelelser fra afsendere i det repræsenterede domæne blev registreret og handlet på baggrund af handlingen for repræsenterede domæner i politikken til bekæmpelse af phishing.

Du kan klikke på de markerede kolonneoverskrifter for at sortere resultaterne.

Hvis du vil filtrere resultaterne, kan du bruge søgeikonet ![.](../../media/m365-cc-sc-search-icon.png) **Søgefelt** til at angive en kommasepareret liste over værdier for at filtrere resultaterne.

### <a name="view-details-about-messages-from-senders-in-impersonated-domains"></a>Få vist oplysninger om meddelelser fra afsendere i repræsenterede domæner

Under fanen **Domæner** på siden **Repræsentationsindsigt** skal du vælge en af de tilgængelige repræsentationsregistreringer. Det pop op-vindue med detaljer, der vises, indeholder følgende oplysninger og funktioner:

- **Valg repræsenteringspolitik, der skal ændres**: Vælg den berørte anti-phishing-politik, du vil ændre. Det er kun politikker, hvor det repræsenterede domæne er defineret i politikken, der er tilgængelige. Se den forrige side for at se, hvilken politik der faktisk var ansvarlig for at registrere det repræsenterede domæne (sandsynligvis baseret på modtageren og politikkens prioritet).
- **Føj til listen over tilladte repræsentationer**: Brug denne til/fra-knap til at tilføje eller fjerne afsenderen fra **afsendere og domæner** , der er tillid til (repræsentationsundtagelser) for den valgte politik til bekæmpelse af phishing:
  - Hvis værdien **tilladt at repræsentere** denne post var **Nej**, er til/fra-knappen slået fra. Hvis du vil fritage alle afsendere i dette domæne fra evaluering af repræsentationsbeskyttelse, skal du skubbe til/fra-knappen til: ![Slå til.](../../media/scc-toggle-on.png). Domænet føjes til listen over **domæner,** der er tillid til, i indstillingerne for beskyttelse mod phishing i politikken til beskyttelse mod phishing.
  - Hvis værdien **tilladt at repræsentere** denne post var **Ja**, er til/fra-knappen slået til. Hvis du vil returnere alle afsendere i dette domæne til evaluering af repræsentationsbeskyttelse, skal du skubbe til/fra-knappen: ![Slå til/fra.](../../media/scc-toggle-off.png). Domænet fjernes fra listen over **domæner, der er tillid til** , i indstillingerne for beskyttelse mod phishing i politikken til beskyttelse mod phishing.
- Hvorfor vi fangede det her.
- Hvad du skal gøre.
- En domæneoversigt, der viser det repræsenterede domæne.
- WhoIs-data om afsenderen.
- Et link til at åbne [Threat Explorer](threat-explorer.md) for at få vist flere oplysninger om afsenderen.
- Lignende meddelelser fra den samme afsender, der blev leveret til din organisation.

## <a name="view-information-about-messages-from-impersonated-senders"></a>Få vist oplysninger om meddelelser fra repræsenterede afsendere

Klik på fanen **Brugere** på siden **Repræsentationsindsigt**, der vises, når du klikker på **Vis repræsentationer** i repræsentationsindsigten. Fanen **Brugere** indeholder følgende oplysninger:

- **Afsender**: Mailadressen på den repræsenterende afsender, der sendte mailen.
- **Antal meddelelser**: Antallet af meddelelser fra den repræsenterende afsender i løbet af de seneste 7 dage.
- **Repræsentationstype**: Denne værdi er **Bruger i vist navn**.
- **Repræsenterede brugere**: Mailadressen på den repræsenterede afsender, som skal ligne den bruger, der er konfigureret til repræsentationsbeskyttelse i politikken til bekæmpelse af phishing.
- **Brugertype**: Denne værdi viser den anvendte type beskyttelse (f.eks. **Beskyttet bruger** eller **Postkasseintelligens**).
- **Politik**: Den anti-phishing-politik, der registrerede den repræsenterede afsender.
- **Tilladt at repræsentere**: En af følgende værdier:
  - **Ja**: Afsenderen blev konfigureret som bruger, der er tillid til (en undtagelse for repræsentationsbeskyttelse) i politikken til bekæmpelse af phishing. Meddelelser fra den repræsenterede afsender blev registreret, men tilladt.
  - **Nej**: Afsenderen er konfigureret til repræsentationsbeskyttelse i politikken til bekæmpelse af phishing. Meddelelser fra den repræsenterede afsender blev registreret og handlet på baggrund af handlingen for repræsenterede brugere i politikken til bekæmpelse af phishing.

Du kan klikke på de markerede kolonneoverskrifter for at sortere resultaterne.

Hvis du vil filtrere resultaterne, kan du bruge feltet **Filter afsender** til at angive en kommasepareret liste over værdier for at filtrere resultaterne.

### <a name="view-details-about-messages-from-impersonated-senders"></a>Få vist oplysninger om meddelelser fra repræsenterede afsendere

På fanen **Brugere** på siden **Repræsentationsindsigt** skal du vælge en af de tilgængelige repræsentationsregistreringer. Det pop op-vindue med detaljer, der vises, indeholder følgende oplysninger og funktioner:

- **Valg repræsenteringspolitik, der skal ændres**: Vælg den berørte anti-phishing-politik, du vil ændre. Det er kun politikker, hvor den repræsenterede afsender er defineret i politikken, der er tilgængelige. Se den forrige side for at se, hvilken politik der faktisk var ansvarlig for at registrere den repræsenterede afsender (sandsynligvis baseret på modtageren og politikkens prioritet).
- **Føj til listen over tilladte repræsentationer**: Brug denne til/fra-knap til at tilføje eller fjerne afsenderen fra **afsendere og domæner** , der er tillid til (repræsentationsundtagelser) for den valgte politik til bekæmpelse af phishing:
  - Hvis værdien **tilladt at repræsentere** denne post var **Nej**, er til/fra-knappen slået fra. Hvis du vil fritage afsenderen fra evaluering af repræsentationsbeskyttelse, skal du slå til/fra-knappen til: ![Slå til.](../../media/scc-toggle-on.png). Afsenderen føjes til listen over **brugere, der er tillid** til, i indstillingerne for beskyttelse mod phishing i politikken til beskyttelse mod phishing.
  - Hvis værdien **tilladt at repræsentere** denne post var **Ja**, er til/fra-knappen slået til. Hvis du vil returnere afsenderen til evaluering efter repræsentationsbeskyttelse, skal du skubbe til/fra-knappen til fra: ![Slå til/fra.](../../media/scc-toggle-off.png). Afsenderen fjernes fra listen over **brugere, der er tillid til** , i indstillingerne for beskyttelse mod phishing i politikken til beskyttelse mod phishing.
- Hvorfor vi fangede det her.
- Hvad du skal gøre.
- En afsenderoversigt, der viser den repræsenterede afsender.
- WhoIs-data om afsenderen.
- Et link til at åbne [Threat Explorer](threat-explorer.md) for at få vist flere oplysninger om afsenderen.
- Lignende meddelelser fra den samme afsender, der blev leveret til din organisation.
