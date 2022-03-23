---
title: Efterlignet intelligensindsigt
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
description: Administratorer kan få mere at vide om efterlignet intelligens indsigt i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5bf0ed143f5bfb78ff1d6af4005a4b5ec64fd90e
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63588924"
---
# <a name="spoof-intelligence-insight-in-eop"></a>Efterlignet intelligensindsigt i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> De funktioner, der er beskrevet i denne artikel, findes i Preview, kan blive ændret og er ikke tilgængelige i alle organisationer. Hvis din organisation ikke har de funktioner, der er beskrevet i denne artikel, kan du se den ældre spoof-administrationsoplevelse i Administrer efterlignede afsendere ved hjælp af efterlignet intelligenspolitik og [efterlignet intelligensindsigt i EOP](walkthrough-spoof-intelligence-insight.md).

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående Exchange Online Protection (EOP)-organisationer uden Exchange Online-postkasser er indgående mails automatisk beskyttet mod spoofing. EOP bruger **efterlignet intelligens som** en del af organisationens overordnede forsvar mod phishing. Du kan finde flere oplysninger [under Beskyttelse mod spoofing i EOP](anti-spoofing-protection.md).

Når en afsender spoofs an email address, they appear to be user in one of your organization's domains, or a user in an external domain that sends email to your organization. Hackere, der spoof afsendere til at sende spam- eller phishing-mails, skal blokeres. Men der er scenarier, hvor legitime afsendere spoofing. Eksempel:

- Legitime scenarier for efterlignede interne domæner:
  - Tredjepartsafsendere bruger dit domæne til at sende masseforsendelser til dine egne medarbejdere til afstemninger i virksomheden.
  - En ekstern virksomhed genererer og sender reklamer eller produktopdateringer på dine vegne.
  - En assistent skal regelmæssigt sende mails til en anden person i din organisation.
  - Et internt program sender mailbeskeder.

- Legitime scenarier for efterlignede eksterne domæner:
  - Afsenderen er på en adresseliste (også kaldet en diskussionsliste), og adresselisten videresender mails fra den oprindelige afsender til alle deltagerne på adresselisten.
  - En ekstern virksomhed sender mail på vegne af en anden virksomhed (f.eks. en automatiseret rapport eller et software-as-a-service-firma).

Du kan bruge efterlignet intelligensindsigt i Microsoft 365 Defender-portalen til hurtigt at identificere spoofede afsendere, der legitimt sender dig ikke-godkendte mails (meddelelser fra domæner, der ikke passerer SPF-, DKIM- eller DMARC-kontroller), og manuelt tillade disse afsendere.

Ved at tillade, at kendte afsendere sender falske meddelelser fra kendte placeringer, kan du reducere falske positive (god mail markeret som dårlig). Ved at overvåge de tilladte spoof-afsendere angiver du et ekstra lag af sikkerhed for at forhindre usikre meddelelser i at ankomme i organisationen.

Du kan også gennemse efterlignede afsendere, der er blevet tilladt af efterlignet intelligens og manuelt blokere disse afsendere fra efterlignet intelligensindsigt.

Resten af denne artikel forklarer, hvordan du kan bruge efterlignet intelligensindsigt i Microsoft 365 Defender-portalen og i PowerShell (Exchange Online PowerShell til Microsoft 365-organisationer med postkasser i Exchange Online; enkeltstående EOP PowerShell til organisationer uden Exchange Online postkasser).

> [!NOTE]
>
> - Kun spoof-afsendere, der er registreret af efterlignet intelligens, vises i efterlignet intelligensindsigt. Når du tilsidesætter konklusionen tillad eller bloker i indsigten, bliver den spooferede afsender til en manuel tillad- eller blokindtastning, der kun vises på fanen **Spoof** på lejerens tilladelses-/blokeringsliste. Du kan også manuelt oprette tillade eller blokere poster for efterlignede afsendere, før de registreres af efterlignet intelligens. Få mere at vide under [Administrer lejerens tilladelses-/blokeringsliste i EOP](tenant-allow-block-list.md).
>
> - Efterlignet intelligensindsigt og fanen **Spoof** på listen Lejers tilladelse/blokering erstatter funktionaliteten af den efterlignede intelligencepolitik, der var tilgængelig på siden med antispampolitik i Security & Compliance Center.
>
>- Den efterlignede intelligensindsigt viser data, der er 7 dage værd. **Cmdlet'en Get-SpoofIntelligenceInsight** viser data for 30 dage.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til **fanen Spoofing på** siden **Lejers tilladelses-/blokeringsliste** skal du bruge <https://security.microsoft.com/tenantAllowBlockList?viewid=SpoofItem>. For at gå direkte til **siden Spoof intelligence insight** skal du bruge <https://security.microsoft.com/spoofintelligence>.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du Forbind Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser **i Exchange Online,** før du kan udføre procedurerne i denne artikel:
  - Hvis du vil ændre efterlignet intelligenspolitik eller aktivere eller deaktivere efterlignet intelligens, skal du være medlem af rollegrupperne Organisationsadministration eller **Sikkerhedsadministrator**.
  - For skrivebeskyttet adgang til efterlignet intelligencepolitik skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser** .

  Du kan finde flere [oplysninger i Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Hvis du føjer brugere til den Azure Active Directory rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser og tilladelser til andre  funktioner Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).
  > - **Rollegruppen Skrivebeskyttet** organisationsadministration i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) også skrivebeskyttet adgang til funktionen.

- Du aktiverer og deaktiverer efterlignet intelligens i antiphishing-politikker i EOP og Microsoft Defender Office 365. Efterlignet intelligens er aktiveret som standard. Få mere at vide under [Konfigurer antiphishing-politikker i EOP](configure-anti-phishing-policies-eop.md) eller [Konfigurer antiphishing-politikker i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md).

- For vores anbefalede indstillinger for efterlignet intelligens skal du se [Politikindstillinger for EOP-antiphishing](recommended-settings-for-eop-and-office365-atp.md#eop-anti-phishing-policy-settings).

## <a name="open-the-spoof-intelligence-insight-in-the-microsoft-365-defender-portal"></a>Åbn efterlignet intelligensindsigt i Microsoft 365 Defender portal

1. I portalen Microsoft 365 Defender på skal  du <https://security.microsoft.com>gå til Mail & **samarbejdspolitikker** \> **& Politikker** \> \> for trussel mod regler **Lejerens tilladelse/** blokering i **sektionen** Regler. For at gå direkte til **fanen Spoofing på** siden **Lejers tilladelses-/blokeringsliste** skal du bruge <https://security.microsoft.com/tenantAllowBlockList?viewid=SpoofItem>.

2. På siden **Lejers tilladelses-/** bloklister ser efterlignet intelligensindsigt således ud:

   ![Efterlignet intelligens indsigt på siden antiphishing-politik.](../../media/m365-sc-spoof-intelligence-insight.png)

   Indsigten har to tilstande:

   - **Insight-tilstand**: Hvis efterlignet intelligens er aktiveret, viser indsigten, hvor mange meddelelser der er blevet registreret af efterlignet intelligens i løbet af de seneste syv dage.
   - **Hvad hvis-tilstand**: Hvis efterlignet intelligens er deaktiveret, viser indsigten, hvor mange meddelelser der *ville være blevet* registreret af efterlignet intelligens i løbet af de seneste syv dage.

Hvis du vil have vist oplysninger om falske intelligenceregistreringer, skal du klikke på Vis **spoofing-aktivitet** i efterlignet intelligensindsigt.

### <a name="view-information-about-spoofed-messages"></a>Få vist oplysninger om efterlignede meddelelser

> [!NOTE]
> Husk, at det kun er spoof-afsendere, der blev registreret af efterlignet intelligens, der vises på denne side. Når du tilsidesætter konklusionen tillad eller bloker i indsigten, bliver den spooferede afsender til en manuel tillad- eller blokindtastning, der kun vises på fanen **Spoof** på lejerens tilladelses-/blokeringsliste.

På siden **Spoof intelligence insight** , der vises, når du klikker på Vis **spoofing-aktivitet** i efterlignet intelligenceindsigt, indeholder siden følgende oplysninger:

- **Efterlignet bruger****: Domænet** for den efterlignede bruger, der vises i feltet **Fra i** mailklienter. Fra-adressen kaldes også `5322.From` for adressen.
- **Sendeinfrastruktur**: Også kendt som _infrastruktur_. Den afsendende infrastruktur vil være en af følgende værdier:
  - Domænet, der findes i et omvendt DNS-opslag (PTR-post) på kildemailserverens IP-adresse.
  - Hvis kilde-IP-adressen ikke har en PTR-post, \<source IP\>identificeres den afsendende infrastruktur som /24 (f.eks. 192.168.100.100/24).
- **Meddelelsesantal**: Antallet af meddelelser fra kombinationen af det efterlignede domæne og afsendelsesinfrastrukturen til din organisation inden for de seneste 7 dage.
- **Sidst set**: Den sidste dato, hvor en meddelelse blev modtaget fra den afsendende infrastruktur, der indeholder det efterlignede domæne.
- **Spoof-type**: En af følgende værdier:
  - **Internt**: Afsenderen er i et domæne, der tilhører din organisation (et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
  - **Ekstern**: Spoof-afsenderen er i et eksternt domæne.
- **Handling**: Denne værdi er Tilladt **eller** **Blokeret**:
  - **Tilladt**: Domænet mislykkedes eksplicit mailgodkendelse [kontrollerer SPF](how-office-365-uses-spf-to-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) og [DMARC](use-dmarc-to-validate-email.md). Men domænet bestod vores implicitte mailgodkendelseskontroller ([sammensat godkendelse](email-validation-and-authentication.md#composite-authentication)). Derfor blev der ikke taget nogen antispoofinghandling på meddelelsen.
  - **Blokeret**: Meddelelser fra kombinationen af det efterlignede domæne og _den_ afsendende infrastruktur er markeret som dårlige af efterlignet intelligens. Den handling, der er foretaget på forfalskede meddelelser, styres af standardpolitikken for phishing eller brugerdefinerede antiphishing-politikker (standardværdien er Flyt meddelelsen til mappen Uønsket **mail**). Få mere at vide under [Konfigurer antiphishing-politikker i Microsoft Defender Office 365](configure-mdo-anti-phishing-policies.md).

Du kan klikke på markerede kolonneoverskrifter for at sortere resultaterne.

Hvis du vil filtrere resultaterne, har du følgende indstillinger:

- Klik på **knappen** Filtrer. I pop  op-vinduesfilteret, der vises, kan du filtrere resultaterne efter:
  - **Spoof-type**
  - **Handling**
- Brug feltet **Søg** til at angive en kommasepareret liste over efterlignede domæneværdier eller sende infrastrukturværdier for at filtrere resultaterne.

### <a name="view-details-about-spoofed-messages"></a>Få vist detaljer om efterlignede meddelelser

Når du vælger en post på listen, vises der en pop op-meddelelse med oplysninger, der indeholder følgende oplysninger og funktioner:

- Tillad **spoof** eller Bloker fra **spoofing**: Vælg en af disse værdier for at tilsidesætte den oprindelige efterlignede intelligenss vurdering og flytte posten fra efterlignet intelligensindsigt til lejerens tilladelses-/blokliste som en tillad- eller blokindtastning for spoof.
- Derfor har vi opdaget dette.
- Det skal du gøre.
- En domæneoversigt, der indeholder de fleste af de samme oplysninger fra den primære efterlignede intelligensside.
- WhoIs data about the sender.
- Et link til at [åbne Threat Explorer](threat-explorer.md) for at se yderligere oplysninger om afsenderen under **View** \> **Phish** i Microsoft Defender for Office 365.
- Lignende meddelelser, vi har set i din lejer fra den samme afsender.

### <a name="about-allowed-spoofed-senders"></a>Om tilladte spoof-afsendere

En tilladt spoof-afsender i spoof-intelligensindsigt eller en blokeret spoof-afsender, som du manuelt har ændret til Tillad til **spoof**, tillader kun meddelelser fra kombinationen af det  efterlignede domæne og afsenderinfrastrukturen. Det tillader ikke mail fra det efterlignede domæne fra nogen kilde, og det tillader heller ikke mail fra afsenderinfrastrukturen for nogen domæne.

Følgende spoof-afsender har f.eks. tilladelse til at spoof:

- **Domæne**: gmail.com
- **Infrastruktur**: tms.mx.com

Kun mail fra det pågældende domæne/afsendende infrastrukturpar får tilladelse til at efterligne. Andre afsendere, der forsøger at efterligne gmail.com, tillades ikke automatisk. Meddelelser fra afsendere på andre domæner, der stammer fra tms.mx.com, kontrolleres stadig af efterlignet intelligens og kan være blokeret.

## <a name="use-the-spoof-intelligence-insight-in-exchange-online-powershell-or-standalone-eop-powershell"></a>Brug efterlignet intelligensindsigt i Exchange Online PowerShell eller enkeltstående EOP PowerShell

I PowerShell bruger du **Get-SpoofIntelligenceInsight-cmdlet'en** til at få vist tilladte og blokerede efterlignede afsendere, der blev registreret af efterlignet intelligens. For manuelt at tillade eller blokere spoofed afsendere, skal du bruge **New-TenantAllowBlockListSpoofItems** cmdlet. Få mere at vide under [Brug PowerShell til at administrere efterlignede afsenderposter på lejerens tilladelses-/blokeringsliste](tenant-allow-block-list.md).

Kør følgende kommando for at få vist oplysningerne i efterlignet intelligensindsigt:

```powershell
Get-SpoofIntelligenceInsight
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-SpoofIntelligenceInsight](/powershell/module/exchange/get-spoofintelligenceinsight).

## <a name="other-ways-to-manage-spoofing-and-phishing"></a>Andre måder at administrere spoofing og phishing

Vær omhyggelig med spoofing- og phishingbeskyttelse. Her er relaterede metoder til at kontrollere afsendere, der efterligner dit domæne og hjælper med at forhindre dem i at beskadige din organisation:

- Kontrollér **Spoof-mailrapporten**. Du kan ofte bruge denne rapport til at få vist og hjælpe med at administrere efterlignede afsendere. Du kan finde flere oplysninger [i Rapporten Spoof-registreringer](view-email-security-reports.md#spoof-detections-report).

- Gennemse SPF-konfigurationen (Sender Policy Framework). Hvis du vil have en hurtig introduktion til SPF og få det konfigureret hurtigt, skal du se Konfigurer [SPF i Microsoft 365 for at forhindre spoofing](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Hvis du vil have en mere dybdegående forståelse af, hvordan Office 365 bruger SPF, eller til fejlfinding eller ikke-standardinstallationer, f.eks. hybride installationer, skal du starte med [Sådan Office 365 bruger SPF (Sender Policy Framework) til at forhindre spoofing](how-office-365-uses-spf-to-prevent-spoofing.md).

- Gennemse konfigurationen af dine DomainKeys Identified Mail (DKIM). Du bør bruge DKIM ud over SPF og DMARC til at forhindre hackere i at sende meddelelser, der ser ud til at komme fra dit domæne. DKIM gør det muligt at tilføje en digital signatur til mails i brevhovedet. Få mere at vide under [Brug DKIM til at validere udgående mails, der sendes fra dit brugerdefinerede domæne Office 365](use-dkim-to-validate-outbound-email.md).

- Gennemse din domænebaserede godkendelse, rapportering og overholdelse (DMARC) konfiguration. Implementering af DMARC med SPF og DKIM giver yderligere beskyttelse mod spoofing- og phishing-mail. DMARC hjælper modtagende mailsystemer med at afgøre, hvad der skal sker med meddelelser, der sendes fra dit domæne, og som ikke kontrollerer SPF eller DKIM. Du kan finde flere oplysninger [under Brug DMARC til at validere mail Office 365](use-dmarc-to-validate-email.md).
