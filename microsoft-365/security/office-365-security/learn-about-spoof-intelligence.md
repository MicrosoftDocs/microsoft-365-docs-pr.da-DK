---
title: Indsigt i efterretninger om forfalskning
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 978c3173-3578-4286-aaf4-8a10951978bf
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om spoof intelligence-indsigt i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: fc09bb008586b26649e31f409fa3be8114c6d2b6
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772070"
---
# <a name="spoof-intelligence-insight-in-eop"></a>Spoof intelligence-indsigt i EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online postkasser beskyttes indgående mails automatisk mod spoofing. EOP bruger **spoof intelligence** som en del af din organisations overordnede forsvar mod phishing. Du kan få flere oplysninger under [Beskyttelse mod spoofing i EOP](anti-spoofing-protection.md).

Når en afsender spoofs en mailadresse, ser de ud til at være en bruger i et af organisationens domæner eller en bruger i et eksternt domæne, der sender mail til din organisation. Personer med ondsindede hensigter, der forfalsker afsendere for at sende spam eller phishing-mail, skal blokeres. Men der er scenarier, hvor legitime afsendere er spoofing. Eksempel:

- Legitime scenarier til spoofing af interne domæner:
  - Afsendere fra tredjepart bruger dit domæne til at sende massemails til dine egne medarbejdere til virksomhedsundersøgelser.
  - En ekstern virksomhed genererer og sender reklame- eller produktopdateringer på dine vegne.
  - En assistent skal jævnligt sende en mail til en anden person i din organisation.
  - Et internt program sender mailmeddelelser.

- Legitime scenarier til spoofing af eksterne domæner:
  - Afsenderen er på en adresseliste (også kendt som en diskussionsliste), og adresselisten videresender mail fra den oprindelige afsender til alle deltagerne på adresselisten.
  - En ekstern virksomhed sender mail på vegne af en anden virksomhed (f.eks. en automatiseret rapport eller et software-as-a-service-firma).

Du kan bruge **indsigt i spoof intelligence** på Microsoft 365 Defender portalen til hurtigt at identificere spoofede afsendere, der lovligt sender dig ikke-godkendte mails (meddelelser fra domæner, der ikke består SPF-, DKIM- eller DMARC-kontroller), og manuelt tillade disse afsendere.

Hvis du tillader kendte afsendere at sende spoofede meddelelser fra kendte placeringer, kan du reducere falske positiver (god mail markeret som dårlig). Når du overvåger de tilladte spoofede afsendere, giver du et ekstra sikkerhedslag for at forhindre, at usikre meddelelser ankommer til din organisation.

På samme måde kan du gennemse spoofed-afsendere, der blev tilladt af spoof intelligence, og manuelt blokere disse afsendere fra indsigten spoof intelligence.

I resten af denne artikel forklares det, hvordan du bruger indsigt i spoof intelligence i Microsoft 365 Defender-portalen og i PowerShell (Exchange Online PowerShell til Microsoft 365 organisationer med postkasser i Exchange Online; enkeltstående EOP PowerShell til organisationer uden Exchange Online postkasser).

> [!NOTE]
>
> - Det er kun spoofed-afsendere, der blev registreret af spoof intelligence, der vises i indsigten spoof intelligence. Når du tilsidesætter den tilladte eller blokerede dom i indsigten, bliver den spooferede afsender en manuel tilladelses- eller blokpost, der kun vises under fanen **Spoof** på listen Over tilladte/blokerede lejere. Du kan også manuelt oprette tillad eller blokere poster for spoofede afsendere, før de registreres af spoof intelligence. Du kan få flere oplysninger under [Administrer listen over tilladte/blokerede lejere i EOP](tenant-allow-block-list.md).
>
> - Indsigten spoof intelligence og fanen **Spoof** på listen Over tilladte/blokerede lejere erstatter funktionaliteten af den spoof intelligence-politik, der var tilgængelig på siden politik til bekæmpelse af spam i Security & Compliance Center.
>
>- Indsigten spoof intelligence viser data for 7 dage. **Cmdlet'en Get-SpoofIntelligenceInsight** viser data for 30 dage.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til fanen **Spoofing** på siden **Tillad/bloker lejerliste** , skal du bruge <https://security.microsoft.com/tenantAllowBlockList?viewid=SpoofItem>. Hvis du vil gå direkte til siden **Spoof intelligence-indsigt** , skal du bruge <https://security.microsoft.com/spoofintelligence>.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, [skal du se Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du se Forbind til Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser i **Exchange Online**, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil ændre spoof intelligence-politikken eller aktivere eller deaktivere spoof intelligence, skal du være medlem af 
    -   **Organisationsadministration**
    -   **Konfiguration af sikkerhedsadministrator** <u>og</u> kun **visning** eller **kun visning af organisationsadministration**.
  - Hvis du vil have skrivebeskyttet adgang til spoof intelligence-politikken, skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser** .

  Du kan få flere oplysninger [under Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Tilføjelse af brugere til den tilsvarende Azure Active Directory rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  > - Rollegruppen **Vis kun organisationsadministration** i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) giver også skrivebeskyttet adgang til funktionen.

- Du aktiverer og deaktiverer spoof intelligence i politikker til bekæmpelse af phishing i EOP og Microsoft Defender for Office 365. Spoof intelligence er aktiveret som standard. Du kan få flere oplysninger under [Konfigurer politikker til bekæmpelse af phishing i EOP](configure-anti-phishing-policies-eop.md) eller [Konfigurer politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md).

- Du kan se vores anbefalede indstillinger for spoof intelligence under [EOP-politikindstillinger for anti-phishing](recommended-settings-for-eop-and-office365-atp.md#eop-anti-phishing-policy-settings).

## <a name="open-the-spoof-intelligence-insight-in-the-microsoft-365-defender-portal"></a>Åbn indsigt i spoof intelligence på portalen Microsoft 365 Defender

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Lejer allow/Block Lists** i afsnittet **Regler**. Hvis du vil gå direkte til fanen **Spoofing** på siden **Tillad/bloker lejerliste** , skal du bruge <https://security.microsoft.com/tenantAllowBlockList?viewid=SpoofItem>.

2. På siden **Lister over tilladte/blokerede lejere** ser indsigten spoof intelligence ud på følgende måde:

   :::image type="content" source="../../media/m365-sc-spoof-intelligence-insight.png" alt-text="Indsigt i Spoof intelligence på siden Anti-phishing-politik" lightbox="../../media/m365-sc-spoof-intelligence-insight.png":::

   Indsigten har to tilstande:

   - **Indsigtstilstand**: Hvis spoof intelligence er aktiveret, viser indsigten, hvor mange meddelelser der blev registreret af spoof intelligence i løbet af de seneste syv dage.
   - **What if-tilstand**: Hvis spoof intelligence er deaktiveret, viser indsigten, hvor mange meddelelser der *ville* være blevet registreret af spoof intelligence i løbet af de seneste syv dage.

Hvis du vil have vist oplysninger om spoof intelligence-registreringer, skal du klikke på **Vis spoofing-aktivitet** i indsigten spoof intelligence.

### <a name="view-information-about-spoofed-messages"></a>Få vist oplysninger om spoofede meddelelser

> [!NOTE]
> Husk, at det kun er spoofed afsendere, der blev registreret af spoof intelligence, der vises på denne side. Når du tilsidesætter den tilladte eller blokerede dom i indsigten, bliver den spooferede afsender en manuel tilladelses- eller blokpost, der kun vises under fanen **Spoof** på listen Over tilladte/blokerede lejere.

På siden **Spoof intelligence-indsigt** , der vises, når du klikker på **Vis spoofing-aktivitet** i indsigten spoof intelligence, indeholder siden følgende oplysninger:

- **Spoofed bruger**: **Domænet** for den spoofede bruger, der vises i feltet **Fra** i mailklienter. Fra-adressen kaldes også adressen `5322.From` .
- **Sender infrastruktur**: Også kendt som _infrastrukturen_. Den afsendende infrastruktur vil være en af følgende værdier:
  - Domænet, der blev fundet i et omvendt DNS-opslag (PTR-post) for kildemailserverens IP-adresse.
  - Hvis kildens IP-adresse ikke har nogen PTR-post, identificeres den afsendende infrastruktur som \<source IP\>/24 (f.eks. 192.168.100.100/24).
  - Et bekræftet DKIM-domæne.
- **Antal meddelelser**: Antallet af meddelelser fra kombinationen af det spoofede domæne _og_ den sendende infrastruktur til din organisation inden for de sidste 7 dage.
- **Sidst set**: Den sidste dato, hvor der blev modtaget en meddelelse fra den afsendelsesinfrastruktur, der indeholder det spoofede domæne.
- **Spoof-type**: En af følgende værdier:
  - **Intern**: Den spoofede afsender er i et domæne, der tilhører din organisation (et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
  - **Ekstern**: Den spoofede afsender er i et eksternt domæne.
- **Handling**: Denne værdi er **Tilladt** eller **Blokeret**:
  - **Tilladt**: Domænet kunne ikke godkende eksplicit mailgodkendelse for [SPF](how-office-365-uses-spf-to-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) og [DMARC](use-dmarc-to-validate-email.md). Domænet overførte dog vores implicitte kontrol af mailgodkendelse ([sammensat godkendelse](email-validation-and-authentication.md#composite-authentication)). Derfor blev der ikke foretaget nogen anti-spoofing-handling på meddelelsen.
  - **Blokeret**: Meddelelser fra kombinationen af det spoofede domæne _og_ afsendelsesinfrastrukturen er markeret som ugyldige af spoof intelligence. Den handling, der udføres på de spooferede meddelelser, styres af standardpolitikken for anti-phishing eller brugerdefinerede politikker til bekæmpelse af phishing (standardværdien er **Flyt meddelelse til mappen Uønsket mail**). Du kan få flere oplysninger under [Konfigurer politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md).

Du kan klikke på de markerede kolonneoverskrifter for at sortere resultaterne.

Hvis du vil filtrere resultaterne, har du følgende muligheder:

- Klik på knappen **Filter** . I pop op-vinduet **Filter** , der vises, kan du filtrere resultaterne efter:
  - **Spoof-type**
  - **Handling**
- Brug **søgefeltet** til at angive en kommasepareret liste over spoofede domæneværdier eller til at sende infrastrukturværdier for at filtrere resultaterne.

### <a name="view-details-about-spoofed-messages"></a>Få vist oplysninger om spoofed-meddelelser

Når du vælger et element på listen, vises der et pop op-vindue med detaljer, der indeholder følgende oplysninger og funktioner:

- **Tillad spoof** eller **Blok fra spoofing**: Vælg en af disse værdier for at tilsidesætte den oprindelige spoof intelligence-dom og flytte posten fra indsigten spoof intelligence til listen over tilladte/blokerede lejere som en tilladelses- eller blokpost for spoof.
- Hvorfor vi fangede det her.
- Hvad du skal gøre.
- En domæneoversigt, der indeholder de fleste af de samme oplysninger fra den primære spoof intelligence-side.
- WhoIs-data om afsenderen.
- Et link til at åbne [Threat Explorer](threat-explorer.md) for at se flere oplysninger om afsenderen under **Vis** \> **Phish** i Microsoft Defender for Office 365.
- Lignende meddelelser, vi har set i din lejer fra den samme afsender.

### <a name="about-allowed-spoofed-senders"></a>Om tilladte spoofed-afsendere

En tilladt spoofed afsender i indsigt i spoof intelligence eller en blokeret spoofed afsender, som du manuelt har ændret til **Tillad at spoof** , tillader kun meddelelser fra kombinationen af det spoofed domæne _og_ den afsendende infrastruktur. Det tillader ikke mail fra det spoofed domæne fra nogen kilde, og det tillader heller ikke mail fra den afsendende infrastruktur for et domæne.

Følgende spoofed afsender har f.eks. tilladelse til at spoof:

- **Domæne**: gmail.com
- **Infrastruktur**: tms.mx.com

Det er kun mail fra dette domæne/det afsendende infrastrukturpar, der kan forfalskes. Andre afsendere, der forsøger at spoof gmail.com, er ikke automatisk tilladt. Meddelelser fra afsendere i andre domæner, der stammer fra tms.mx.com, kontrolleres stadig af spoof intelligence og kan være blokeret.

## <a name="use-the-spoof-intelligence-insight-in-exchange-online-powershell-or-standalone-eop-powershell"></a>Brug indsigt i spoof intelligence i Exchange Online PowerShell eller enkeltstående EOP PowerShell

I PowerShell skal du bruge **Get-SpoofIntelligenceInsight-cmdlet'en** til at **få vist** tilladte og blokerede spoofed-afsendere, der blev registreret af spoof intelligence. Hvis du vil tillade eller blokere de spoofede afsendere manuelt, skal du bruge cmdlet'en **New-TenantAllowBlockListSpoofItems** . Du kan få flere oplysninger under [Brug PowerShell til at administrere forfalskede afsenderposter til lejerlisten tillad/bloker](tenant-allow-block-list.md).

Kør følgende kommando for at få vist oplysningerne i indsigten spoof intelligence:

```powershell
Get-SpoofIntelligenceInsight
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-SpoofIntelligenceInsight](/powershell/module/exchange/get-spoofintelligenceinsight).

## <a name="other-ways-to-manage-spoofing-and-phishing"></a>Andre måder at administrere spoofing og phishing på

Vær omhyggelig med spoofing og phishing-beskyttelse. Her er relaterede måder at kontrollere afsendere, der spoofer dit domæne, og hjælpe med at forhindre dem i at beskadige din organisation:

- Kontrollér **Spoof Mail-rapporten**. Du kan ofte bruge denne rapport til at få vist og hjælpe med at administrere misvisende afsendere. Du kan få flere oplysninger i [Spoof Detections-rapporten](view-email-security-reports.md#spoof-detections-report).

- Gennemse spf-konfigurationen (Sender Policy Framework). Du kan få en hurtig introduktion til SPF og få den konfigureret hurtigt under [Konfigurer SPF i Microsoft 365 for at forhindre spoofing](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Hvis du vil have en mere detaljeret forståelse af, hvordan Office 365 bruger SPF, eller til fejlfinding eller ikke-standardinstallationer, f.eks. hybridinstallationer, skal du starte med [Sådan bruger Office 365 SPF (Sender Policy Framework) til at forhindre spoofing](how-office-365-uses-spf-to-prevent-spoofing.md).

- Gennemse konfigurationen af Din Domænenøgleidentificeret mail (DKIM). Du skal bruge DKIM ud over SPF og DMARC for at forhindre hackere i at sende meddelelser, der ligner de kommer fra dit domæne. I DKIM kan du føje en digital signatur til mails i meddelelsesoverskriften. Du kan få flere oplysninger under [Brug DKIM til at validere udgående mails, der er sendt fra dit brugerdefinerede domæne i Office 365](use-dkim-to-validate-outbound-email.md).

- Gennemse din domænebaserede DMARC-konfiguration (Message Authentication, Reporting og Conformance). Implementering af DMARC med SPF og DKIM giver yderligere beskyttelse mod spoofing- og phishing-mail. DMARC hjælper med at modtage mailsystemer med at afgøre, hvad der skal gøres med meddelelser, der sendes fra dit domæne, og som ikke udfører SPF- eller DKIM-kontroller. Du kan få flere oplysninger under [Brug DMARC til at validere mail i Office 365](use-dmarc-to-validate-email.md).
