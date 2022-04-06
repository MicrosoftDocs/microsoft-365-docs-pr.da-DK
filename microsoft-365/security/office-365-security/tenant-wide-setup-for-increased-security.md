---
title: Konfigurer din Microsoft 365 lejer for øget sikkerhed
f1.keywords:
- NOCSH
ms.author: bcarter
author: BrendaCarter
manager: laurawi
ms.date: 10/11/2018
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_IP
- M365-security-compliance
search.appverid: MET150
ms.assetid: 8d274fe3-db51-4107-ba64-865e7155b355
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
description: I dette emne gennemgås den anbefalede konfiguration af indstillinger for hele lejeren, der påvirker sikkerheden for dit Microsoft 365 miljø.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 94da7316c5e749cf6dcc5e038c185bea4790765f
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682873"
---
# <a name="configure-your-microsoft-365-tenant-for-increased-security"></a>Konfigurer din Microsoft 365 lejer for øget sikkerhed

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I dette emne gennemgås den anbefalede konfiguration af indstillinger for hele lejeren, der påvirker sikkerheden for dit Microsoft 365 miljø. Dine sikkerhedsbehov kan kræve mere eller mindre sikkerhed. Brug disse anbefalinger som et udgangspunkt.

## <a name="check-office-365-secure-score"></a>Kontrollér Office 365 Secure Score

Office 365 Secure Score analyserer din organisations sikkerhed baseret på dine almindelige aktiviteter og sikkerhedsindstillinger og tildeler en score. Start med at notere dit aktuelle resultat. Hvis du justerer nogle indstillinger for hele lejeren, øges din score. Målet er ikke at opnå det højeste antal point, men at være opmærksom på muligheder for at beskytte dit miljø, der ikke påvirker produktiviteten for dine brugere negativt. Se [Microsoft Secure Score](../defender/microsoft-secure-score.md).

## <a name="tune-threat-management-policies-in-the-microsoft-365-defender-portal"></a>Finjustere politikker for trusselsadministration Microsoft 365 Defender portalen

Portalen Microsoft 365 Defender indeholder funktioner, der beskytter dit miljø. Den indeholder også rapporter og dashboards, som du kan bruge til at overvåge og handle på. Nogle områder har standardpolitikkonfigurationer. Nogle områder inkluderer ikke standardpolitikker eller regler. Besøg disse politikker under Politikker **for & mailsamarbejde** \> **& regler** \> for **trusselspolitikker** for at finjustere indstillingerne for trusselsadministration for et mere sikkert miljø.

|Område|Standardpolitik?|Anbefaling|
|---|---|---|
|**Antiphishing**|Ja|Konfigurer standardpolitikken for phishing som beskrevet her: Konfigurer indstillinger [for beskyttelse mod phishing i EOP og Defender for Office 365](protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365). <p> Flere oplysninger: <ul><li>[Antiphishing-politikker i Microsoft 365](set-up-anti-phishing-policies.md)</li><li>[Anbefalede politikindstillinger for phishing i Microsoft Defender til Office 365](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365)</li><li> [Repræsentationsindsigt](impersonation-insight.md)</li><li>[Efterlignet intelligensindsigt i EOP](learn-about-spoof-intelligence.md)</li><li>[Administrer lejerens tilladelses-/blokeringsliste](tenant-allow-block-list.md).</li></ul>|
|**Antimalwareprogrammet**|Ja|Konfigurer standardpolitikken for malware som beskrevet her: [Konfigurer indstillinger for beskyttelse mod malware i EOP](protect-against-threats.md#part-1---anti-malware-protection-in-eop). <p> Flere oplysninger: <ul><li>[Beskyttelse mod malware](anti-malware-protection.md)</li><li>[Anbefalede indstillinger for antimalwarepolitik](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings)</li><li>[Konfigurere antimalwarepolitikker](configure-anti-malware-policies.md)</li></ul>|
|**Pengeskab vedhæftede filer i Defender til Office 365**|Nej|Konfigurer de globale indstillinger for Pengeskab Vedhæftede filer, og opret en politik for vedhæftede filer i Pengeskab som beskrevet her: Konfigurer Pengeskab Indstillinger for vedhæftede filer [i Microsoft Defender for Office 365](protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365). <p> Flere oplysninger: <ul><li>[Indstillinger for anbefalede Pengeskab vedhæftede filer](recommended-settings-for-eop-and-office365.md#safe-attachments-settings)</li><li>[Pengeskab vedhæftede filer i Microsoft Defender til Office 365](safe-attachments.md)</li><li>[Konfigurere politikker Pengeskab vedhæftede filer](set-up-safe-attachments-policies.md)</li><li>[Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Sikre dokumenter i Microsoft 365 E5](safe-docs.md)</li></ul>|
|**Pengeskab Links i Microsoft Defender til Office 365**|Nej|Konfigurer de globale indstillinger for Pengeskab Links, og opret en politik for Pengeskab Links som beskrevet her: Konfigurer [Pengeskab Links-indstillinger i Microsoft Defender for Office 365](protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365). <p> Flere oplysninger: <ul><li>[Anbefalede indstillinger Pengeskab links](recommended-settings-for-eop-and-office365.md#safe-links-settings)</li><li>[Konfigurere Pengeskab links](set-up-safe-links-policies.md)</li><li>[Pengeskab Links i Microsoft Defender til Office 365](safe-links.md)</li><li>[Konfigurer globale indstillinger for Pengeskab Links i Microsoft Defender for Office 365](configure-global-settings-for-safe-links.md)</li></ul>|
|**Uønsket post (mailfiltrering)**|Ja|Konfigurer standardpolitikken for uønsket post som beskrevet her: [Konfigurer indstillinger for beskyttelse mod uønsket post i EOP](protect-against-threats.md#part-3---anti-spam-protection-in-eop) <p> Flere oplysninger: <ul><li>[Anbefalede indstillinger for antispampolitik](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)</li><li>[Beskyttelse mod spam i EOP](anti-spam-protection.md)</li><li>[Konfigurer antispampolitikker i EOP](configure-your-spam-filter-policies.md)</li></ul>|
|***Mailgodkendelse***|Ja|Mailgodkendelse bruger DNS-poster til at føje oplysninger, der kan bekræftes, til mails om meddelelseskilden og afsenderen. Microsoft 365 konfigurerer automatisk mailgodkendelse for dens standarddomæne (onmicrosoft.com), men Microsoft 365-administratorer kan også konfigurere mailgodkendelse for brugerdefinerede domæner. Der bruges tre godkendelsesmetoder: <ul><li>Sender Policy Framework (eller SPF).</li><ul><li>Se Konfigurer [SPF i en Microsoft 365 for at forhindre spoofing](set-up-spf-in-office-365-to-help-prevent-spoofing.md).</li></ul> <li>DomainKeys Identified Mail (DKIM).</li><ul><li>Se [Brug DKIM til at validere udgående mails, der sendes fra dit brugerdefinerede domæne](use-dkim-to-validate-outbound-email.md).</li><li>Når du har konfigureret DKIM, skal du aktivere det i Microsoft 365 Defender portal.</li></ul><li>Domænebaseret meddelelsesgodkendelse, -rapportering og -overholdelse (DMARC).</li><ul><li>Brug DMARC til at [validere mail i forbindelse med](use-dmarc-to-validate-email.md) DMARC Microsoft 365.</li></ul></ul>|

> [!NOTE]
> For installationer af SPF, hybridinstallationer og fejlfinding, der ikke er standard: [Sådan Microsoft 365 SPF (Sender Policy Framework) til at forhindre spoofing](how-office-365-uses-spf-to-prevent-spoofing.md).

## <a name="view-dashboards-and-reports-in-the-microsoft-365-defender-portal"></a>Få vist dashboards og rapporter i Microsoft 365 Defender portal

Besøg disse rapporter og dashboards for at få mere at vide om miljøets tilstand. Dataene i disse rapporter bliver mere omfattende, efterhånden som organisationen bruger Office 365 tjenester. Lige nu skal du være fortrolig med, hvad du kan overvåge og handle på.

|Dashboard|Beskrivelse|
|---|---|
|Mailsikkerhedsrapporter|Disse rapporter er tilgængelige i Exchange Online Protection. Du kan få mere at vide [under Få vist mailsikkerhedsrapporter Microsoft 365 Defender portalen](view-email-security-reports.md).|
|Defender til Office 365 rapporter|Rapporterne er kun tilgængelige i Defender til Office 365. Du kan finde flere oplysninger [i View Defender for Office 365-rapporter på Microsoft 365 Defender-portalen](view-reports-for-mdo.md).|
|Mailflowrapporter og indsigter|Disse rapporter og indsigter er tilgængelige Exchange Administration (EAC). Få mere at vide under [Mailflowrapporter og](/exchange/monitoring/mail-flow-reports/mail-flow-reports) [Indsigt i mailflow](/exchange/monitoring/mail-flow-insights/mail-flow-insights).|
|[Trusselsstifinder (eller registreringer i realtid)](threat-explorer.md)|Hvis du er ved at undersøge eller opleve et angreb på din lejer, skal du bruge Stifinder (eller registreringer i realtid) til at analysere trusler. Stifinder (og rapporten om registreringer i realtid) viser dig mængden af angreb over tid, og du kan analysere disse data fra trusselsfamilier, hackerinfrastruktur og meget mere. Du kan også markere alle mistænkelige mails på listen Hændelser.|

## <a name="configure-additional-exchange-online-tenant-wide-settings"></a>Konfigurere flere Exchange Online indstillinger for hele lejeren

Her er et par yderligere indstillinger, der anbefales.

|Område|Anbefaling|
|---|---|
|**Regler for mailflow** (også kaldet transportregler)|Tilføj en regel for mailflow for at beskytte mod ransomware ved at blokere eksekverbare filtyper og Office filtyper, der indeholder makroer. Få mere at vide under [Brug regler for mailflow til at undersøge vedhæftede filer i meddelelser Exchange Online](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments). <p> Se disse yderligere emner: <ul><li>[Beskyt dig mod ransomware](../../admin/security-and-compliance/secure-your-business-data.md#5-protect-against-ransomware)</li><li>[Malware- og ransomware-beskyttelse i Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)</li><li>[Gendan efter en ransomware-angreb i Office 365](recover-from-ransomware.md)</li></ul> <p> Opret en regel for mailflow for at forhindre automatisk videresendelse af mails til eksterne domæner. Du kan få mere at vide [under Ekstern videresendelse af klient-regler med Secure Score](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score). <p> Flere oplysninger: [Regler for mailflow (transportregler) i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)|
|**Moderne godkendelse**|Moderne godkendelse er en forudsætning for brug af Multi-Factor Authentication (MFA). MFA anbefales til sikring af adgang til skyressourcer, herunder mail. <p> Se disse emner: <ul><li>[Aktivér eller deaktiver moderne godkendelse i Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online)</li><li>[Skype for Business Online: Aktivér din lejer til moderne godkendelse](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)</li></ul> <p> Moderne godkendelse er som standard aktiveret for Office 2016-klienter, SharePoint Online og OneDrive for Business. <p> Flere oplysninger: [Sådan fungerer moderne godkendelse til Office 2013- Office 2016-klientprogrammer](../../enterprise/modern-auth-for-office-2013-and-2016.md)|

## <a name="configure-tenant-wide-sharing-policies-in-sharepoint-admin-center"></a>Konfigurer politikker for deling for alle lejere SharePoint Administration

Microsoft-anbefalinger til konfiguration SharePoint teamwebsteder på et stigende beskyttelsesniveau, startende med beskyttelse mod grundlinjer. Du kan finde flere oplysninger [i Politikanbefalinger til sikring SharePoint websteder og filer](sharepoint-file-access-policies.md).

SharePoint teamwebsteder, der er konfigureret på det oprindelige niveau, gør det muligt at dele filer med eksterne brugere ved hjælp af anonyme adgangslinks. Denne fremgangsmåde anbefales i stedet for at sende filer i en mail.

For at understøtte målene for beskyttelse af oprindelige planer skal du konfigurere delingspolitikker for hele lejeren som anbefalet her. Indstillinger for deling af individuelle websteder kan være mere restriktive end denne lejerbaserede politik, men ikke mere restriktiv.

|Område|Omfatter en standardpolitik|Anbefaling|
|---|---|---|
|**Deling** (SharePoint Online og OneDrive for Business)|Ja|Ekstern deling er aktiveret som standard. Disse indstillinger anbefales: <ul><li>Tillad deling med godkendte eksterne brugere og ved hjælp af anonyme adgangslinks (standardindstilling).</li><li>Anonyme adgangslinks udløber om dette antal dage. Angiv et tal, hvis du ønsker det, f.eks. 30 dage.</li><li>Standardlinktype – vælg Intern (kun personer i organisationen). Brugere, der ønsker at dele ved hjælp af anonyme links, skal vælge denne indstilling i delingsmenuen.</li></ul> <p> Flere oplysninger: [Oversigt over ekstern deling](/sharepoint/external-sharing-overview)|

SharePoint Administration og OneDrive for Business Administration har de samme indstillinger. Indstillingerne i begge Administration gælder for begge.

## <a name="configure-settings-in-azure-active-directory"></a>Konfigurer indstillinger i Azure Active Directory

Sørg for at besøge disse to områder i Azure Active Directory for at fuldføre konfigurationen for hele lejeren for mere sikre miljøer.

### <a name="configure-named-locations-under-conditional-access"></a>Konfigurere navngivne placeringer (under betinget adgang)

Hvis din organisation omfatter kontorer med sikker netværksadgang, skal du tilføje de pålidelige IP-adresseintervaller for Azure Active Directory som navngivne placeringer. Denne funktion hjælper med at reducere antallet af rapporterede falske positive ved hændelser med logonrisici.

Se: [Navngivne placeringer i Azure Active Directory](/azure/active-directory/active-directory-named-locations)

### <a name="block-apps-that-dont-support-modern-authentication"></a>Bloker apps, der ikke understøtter moderne godkendelse

Multifaktorgodkendelse kræver apps, der understøtter moderne godkendelse. Apps, der ikke understøtter moderne godkendelse, kan ikke blokeres ved hjælp af regler for betinget adgang.

For sikre miljøer skal du sørge for at deaktivere godkendelse for apps, der ikke understøtter moderne godkendelse. Du kan gøre dette i Azure Active Directory med et kontrolelement, der kommer snart.

I mellemtiden kan du bruge en af følgende metoder til at opnå dette med SharePoint Online og OneDrive for Business:

- Brug PowerShell, se [Bloker apps, der ikke bruger moderne godkendelse](/mem/intune/protect/app-modern-authentication-block).
- Konfigurer dette i <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration på</a> siden "Enhedsadgang " – "Kontroller adgang fra apps, der ikke bruger moderne godkendelse". Vælg Bloker.

## <a name="get-started-with-defender-for-cloud-apps-or-office-365-cloud-app-security"></a>Kom i gang med Defender til skyapps eller Office 365 Cloud App Security

Brug Office 365 Cloud App Security til at evaluere risici, til at advare om mistænkelig aktivitet og til automatisk at handle. Kræver Office 365 E5 plan.

Du kan også bruge Microsoft Defender til skyapps til at få en større synlighed, selv efter du har fået adgang, omfattende kontroller og forbedret beskyttelse af alle dine skyprogrammer, herunder Office 365.

Da denne løsning anbefaler EMS E5-planen, anbefaler vi, at du starter med Defender til skyapps, så du kan bruge den sammen med andre SaaS-programmer i dit miljø. Start med standardpolitikker og indstillinger.

Flere oplysninger:

- [Installér Defender til skyapps](/cloud-app-security/getting-started-with-cloud-app-security)
- [Flere oplysninger om Microsoft Defender til skyapps](https://www.microsoft.com/cloud-platform/cloud-app-security)
- [Hvad er Defender til skyapps?](/cloud-app-security/what-is-cloud-app-security)

![Defender for Cloud Apps dashboard.](../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png)

## <a name="additional-resources"></a>Yderligere ressourcer

Disse artikler og vejledninger indeholder yderligere oplysninger, der kan være præskripive, når du Microsoft 365 miljø:

- [Microsoft-sikkerhedsvejledning til politiske kampagner, nonprofitorganisationer](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) og andre Agile-organisationer (du kan bruge disse anbefalinger i alle miljøer, især i skyen)

- [Anbefalede sikkerhedspolitikker og konfigurationer for identiteter og enheder](microsoft-365-policies-configurations.md) (disse anbefalinger omfatter hjælp til AD FS-miljøer)
