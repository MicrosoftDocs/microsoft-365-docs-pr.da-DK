---
title: Konfigurer din Microsoft 365 lejer for at øge sikkerheden
f1.keywords:
- NOCSH
ms.author: bcarter
author: BrendaCarter
manager: laurawi
ms.date: 04/06/2022
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
description: I dette emne gennemgås den anbefalede konfiguration af lejerindstillinger, der påvirker sikkerheden i dit Microsoft 365 miljø.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a1a9b7e6a006eb63078f237ce1078d6aa825fa14
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872355"
---
# <a name="configure-your-microsoft-365-tenant-for-increased-security"></a>Konfigurer din Microsoft 365 lejer for at øge sikkerheden

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I dette emne gennemgås den anbefalede konfiguration af lejerindstillinger, der påvirker sikkerheden i dit Microsoft 365 miljø. Dine sikkerhedsbehov kan kræve mere eller mindre sikkerhed. Brug disse anbefalinger som udgangspunkt.

## <a name="check-office-365-secure-score"></a>Kontrollér Office 365 sikker score

Office 365 Secure Score analyserer din organisations sikkerhed baseret på dine almindelige aktiviteter og sikkerhedsindstillinger og tildeler en score. Begynd med at tage din aktuelle score til efterretning. Hvis du justerer nogle indstillinger for hele lejeren, øges din score. Målet er ikke at opnå den maksimale score, men at være opmærksom på muligheder for at beskytte dit miljø, der ikke påvirker produktiviteten for dine brugere negativt. Se [Microsoft Secure Score](../defender/microsoft-secure-score.md).

## <a name="tune-threat-management-policies-in-the-microsoft-365-defender-portal"></a>Juster politikker for administration af trusler på Microsoft 365 Defender-portalen

Portalen Microsoft 365 Defender indeholder funktioner, der beskytter dit miljø. Den indeholder også rapporter og dashboards, du kan bruge til at overvåge og udføre handlinger. Nogle områder leveres med standardpolitikkonfigurationer. Nogle områder indeholder ikke standardpolitikker eller -regler. Besøg disse politikker under **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** for at tilpasse indstillinger for administration af trusler for at få et mere sikkert miljø.

|Område|Standardpolitik?|Anbefaling|
|---|---|---|
|**Anti-phishing**|Ja|Konfigurer standardpolitikken for phishing som beskrevet her: [Konfigurer indstillinger for beskyttelse mod phishing i EOP og Defender for Office 365](protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365). <p> Flere oplysninger: <ul><li>[Politikker til bekæmpelse af phishing i Microsoft 365](set-up-anti-phishing-policies.md)</li><li>[Anbefalede politikindstillinger for anti-phishing i Microsoft Defender for Office 365](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365)</li><li> [Indsigt i efterligning](impersonation-insight.md)</li><li>[Spoof intelligence-indsigt i EOP](learn-about-spoof-intelligence.md)</li><li>[Administrer listen over tilladte/blokerede lejere](tenant-allow-block-list.md).</li></ul>|
|**Antimalwareprogram**|Ja|Konfigurer standardpolitikken for antimalware som beskrevet her: [Konfigurer indstillinger for beskyttelse mod skadelig software i EOP](protect-against-threats.md#part-1---anti-malware-protection-in-eop). <p> Flere oplysninger: <ul><li>[Beskyttelse mod malware](anti-malware-protection.md)</li><li>[Anbefalede indstillinger for politik for antimalware](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings)</li><li>[Konfigurer politikker for antimalware](configure-anti-malware-policies.md)</li></ul>|
|**Sikre vedhæftede filer i Defender for Office 365**|Nej|Konfigurer de globale indstillinger for Pengeskab Vedhæftede filer, og opret en politik for vedhæftede filer Pengeskab som beskrevet her: [Konfigurer indstillingerne for Pengeskab vedhæftede filer i Microsoft Defender for Office 365](protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365). <p> Flere oplysninger: <ul><li>[Anbefalede indstillinger for Pengeskab vedhæftede filer](recommended-settings-for-eop-and-office365.md#safe-attachments-settings)</li><li>[Pengeskab vedhæftede filer i Microsoft Defender for Office 365](safe-attachments.md)</li><li>[Konfigurer politikker for vedhæftede filer Pengeskab](set-up-safe-attachments-policies.md)</li><li>[Sikre vedhæftede filer i SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Sikre dokumenter i Microsoft 365 E5](safe-docs.md)</li></ul>|
|**Pengeskab Links i Microsoft Defender for Office 365**|Nej|Konfigurer de globale indstillinger for Pengeskab Links, og opret en politik for Pengeskab links som beskrevet her: [Konfigurer indstillinger for Pengeskab links i Microsoft Defender for Office 365](protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365). <p> Flere oplysninger: <ul><li>[Anbefalede indstillinger for Pengeskab links](recommended-settings-for-eop-and-office365.md#safe-links-settings)</li><li>[Konfigurer politikker for Pengeskab links](set-up-safe-links-policies.md)</li><li>[Pengeskab Links i Microsoft Defender for Office 365](safe-links.md)</li><li>[Konfigurer globale indstillinger for Pengeskab links i Microsoft Defender for Office 365](configure-global-settings-for-safe-links.md)</li></ul>|
|**Anti-spam (mailfiltrering)**|Ja|Konfigurer standardpolitikken for spam som beskrevet her: [Konfigurer indstillinger for beskyttelse mod spam i EOP](protect-against-threats.md#part-3---anti-spam-protection-in-eop) <p> Flere oplysninger: <ul><li>[Anbefalede indstillinger for politik for spam](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)</li><li>[Beskyttelse mod spam i EOP](anti-spam-protection.md)</li><li>[Konfigurer politikker mod spam i EOP](configure-your-spam-filter-policies.md)</li></ul>|
|***Mailgodkendelse***|Ja|Mailgodkendelse bruger DNS-poster til at føje verificerbare oplysninger til mails om meddelelseskilden og afsenderen. Microsoft 365 konfigurerer automatisk mailgodkendelse for standarddomænet (onmicrosoft.com), men Microsoft 365 administratorer kan også konfigurere mailgodkendelse for brugerdefinerede domæner. Der bruges tre godkendelsesmetoder: <ul><li>Struktur for afsenderpolitik (eller SPF).</li><ul><li>Hvis du vil have mere at vide om konfiguration, skal du se [Konfigurer SPF i Microsoft 365 for at forhindre spoofing](set-up-spf-in-office-365-to-help-prevent-spoofing.md).</li></ul> <li>DomainKeys Identificeret Mail (DKIM).</li><ul><li>Se [Brug DKIM til at validere udgående mail, der er sendt fra dit brugerdefinerede domæne](use-dkim-to-validate-outbound-email.md).</li><li>Når du har konfigureret DKIM, skal du aktivere den på portalen Microsoft 365 Defender.</li></ul><li>Domænebaseret meddelelsesgodkendelse, -rapportering og -overensstemmelse (DMARC).</li><ul><li>I forbindelse med DMARC-konfiguration [skal du bruge DMARC til at validere mail i Microsoft 365](use-dmarc-to-validate-email.md).</li></ul></ul>|

> [!NOTE]
> Til ikke-standardinstallationer af SPF, hybridinstallationer og fejlfinding: [Sådan bruger Microsoft 365 SPF (Sender Policy Framework) til at forhindre spoofing](how-office-365-uses-spf-to-prevent-spoofing.md).

## <a name="view-dashboards-and-reports-in-the-microsoft-365-defender-portal"></a>Få vist dashboards og rapporter på Microsoft 365 Defender-portalen

Besøg disse rapporter og dashboards for at få mere at vide om dit miljøs tilstand. Dataene i disse rapporter bliver mere omfattende, efterhånden som din organisation bruger Office 365 tjenester. I øjeblikket kan du være fortrolig med, hvad du kan overvåge og udføre handlinger på.

|Dashboard|Beskrivelse|
|---|---|
|Mailsikkerhedsrapporter|Disse rapporter er tilgængelige i Exchange Online Protection. Du kan få flere oplysninger under [Få vist mailsikkerhedsrapporter på Microsoft 365 Defender-portalen](view-email-security-reports.md).|
|Defender for Office 365 rapporter|Rapporterne er kun tilgængelige i Defender for Office 365. Du kan få flere oplysninger under [Få vist Defender for Office 365 rapporter på Microsoft 365 Defender-portalen](view-reports-for-mdo.md).|
|Mailflowrapporter og indsigt|Disse rapporter og indsigter er tilgængelige i Exchange Administration (EAC). Du kan få flere oplysninger under [Mailflowrapporter](/exchange/monitoring/mail-flow-reports/mail-flow-reports) og [Indsigt i mailflow](/exchange/monitoring/mail-flow-insights/mail-flow-insights).|
|[Threat Explorer (eller registreringer i realtid)](threat-explorer.md)|Hvis du undersøger eller oplever et angreb på din lejer, kan du bruge Stifinder (eller registreringer i realtid) til at analysere trusler. Explorer (og rapporten over registreringer i realtid) viser mængden af angreb over tid, og du kan analysere disse data efter trusselsfamilier, infrastruktur for hackere med mere. Du kan også markere enhver mistænkelig mail for listen Over hændelser.|

## <a name="configure-additional-exchange-online-tenant-wide-settings"></a>Konfigurer yderligere Exchange Online lejerindstillinger

Her er et par yderligere indstillinger, der anbefales.

|Område|Anbefaling|
|---|---|
|**Regler for mailflow** (også kendt som transportregler)|Tilføj en regel for mailflow for at hjælpe med at beskytte mod ransomware ved at blokere eksekverbare filtyper og Office filtyper, der indeholder makroer. Du kan få flere oplysninger under [Brug regler for mailflow til at undersøge vedhæftede filer i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments). <p> Se disse yderligere emner: <ul><li>[Beskyt mod ransomware](../../admin/security-and-compliance/secure-your-business-data.md)</li><li>[Beskyttelse mod malware og ransomware i Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)</li><li>[Gendan efter et ransomware-angreb i Office 365](recover-from-ransomware.md)</li></ul> <p> Opret en regel for mailflow for at forhindre automatisk videresendelse af mail til eksterne domæner. Du kan få flere oplysninger under [Mitigating Client External Forwarding Rules with Secure Score (Mitigating Client External Forwarding Rules with Secure Score](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score)). <p> Flere oplysninger: [Regler for mailflow (transportregler) i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)|
|**Moderne godkendelse**|Moderne godkendelse er en forudsætning for brug af multifaktorgodkendelse (MFA). MFA anbefales til sikring af adgang til cloudressourcer, herunder mail. <p> Se disse emner: <ul><li>[Aktivér eller deaktiver moderne godkendelse i Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online)</li><li>[Skype for Business Online: Aktivér din lejer til moderne godkendelse](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)</li></ul> <p> Moderne godkendelse er som standard aktiveret for Office 2016-klienter, SharePoint Online og OneDrive for Business. <p> Flere oplysninger: [Sådan fungerer moderne godkendelse for Office 2013 og Office 2016-klientapps](../../enterprise/modern-auth-for-office-2013-and-2016.md)|

## <a name="configure-tenant-wide-sharing-policies-in-sharepoint-admin-center"></a>Konfigurer delingspolitikker for hele lejeren i SharePoint Administration

Microsofts anbefalinger til konfiguration af SharePoint teamwebsteder med stigende beskyttelsesniveauer– startende med grundlæggende beskyttelse. Du kan finde flere oplysninger under [Politikanbefalinger til sikring af SharePoint websteder og filer](sharepoint-file-access-policies.md).

SharePoint teamwebsteder, der er konfigureret på det oprindelige niveau, tillader deling af filer med eksterne brugere ved hjælp af anonyme adgangslinks. Denne fremgangsmåde anbefales i stedet for at sende filer i en mail.

Hvis du vil understøtte målene for grundlæggende beskyttelse, skal du konfigurere delingspolitikker for hele lejeren som anbefalet her. Delingsindstillinger for individuelle websteder kan være mere restriktive end denne politik for hele lejeren, men ikke mere eftergivende.

|Område|Indeholder en standardpolitik|Anbefaling|
|---|---|---|
|**Deling** (SharePoint Online og OneDrive for Business)|Ja|Ekstern deling er som standard aktiveret. Disse indstillinger anbefales: <ul><li>Tillad deling for godkendte eksterne brugere og brug af anonyme adgangslinks (standardindstilling).</li><li>Links til anonym adgang udløber i dette antal dage. Angiv et tal, hvis det er nødvendigt, f.eks. 30 dage.</li><li>Standardlinktype – vælg Intern (kun personer i organisationen). Brugere, der vil dele ved hjælp af anonyme links, skal vælge denne indstilling i delingsmenuen.</li></ul> <p> Flere oplysninger: [Oversigt over ekstern deling](/sharepoint/external-sharing-overview)|

SharePoint Administration og OneDrive for Business Administration indeholder de samme indstillinger. Indstillingerne i begge administrationer gælder for begge.

## <a name="configure-settings-in-azure-active-directory"></a>Konfigurer indstillinger i Azure Active Directory

Sørg for at besøge disse to områder i Azure Active Directory for at fuldføre konfigurationen for hele lejeren for at få mere sikre miljøer.

### <a name="configure-named-locations-under-conditional-access"></a>Konfigurer navngivne placeringer (under betinget adgang)

Hvis din organisation omfatter kontorer med sikker netværksadgang, skal du føje de IP-adresseområder, der er tillid til, til Azure Active Directory som navngivne placeringer. Denne funktion hjælper med at reducere antallet af rapporterede falske positiver for logonrisikohændelser.

Se: [Navngivne placeringer i Azure Active Directory](/azure/active-directory/conditional-access/location-condition)

### <a name="block-apps-that-dont-support-modern-authentication"></a>Bloker apps, der ikke understøtter moderne godkendelse

Multifaktorgodkendelse kræver apps, der understøtter moderne godkendelse. Apps, der ikke understøtter moderne godkendelse, kan ikke blokeres ved hjælp af regler for betinget adgang.

I sikre miljøer skal du sørge for at deaktivere godkendelse for apps, der ikke understøtter moderne godkendelse. Du kan gøre dette i Azure Active Directory med et kontrolelement, der kommer snart.

I mellemtiden kan du bruge en af følgende metoder til at gøre dette for SharePoint Online og OneDrive for Business:

- Brug PowerShell, se [Bloker apps, der ikke bruger moderne godkendelse](/mem/intune/protect/app-modern-authentication-block).
- Konfigurer dette i <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration</a> på siden "enhedsadgang" – "Kontrollér adgang fra apps, der ikke bruger moderne godkendelse". Vælg Blok.

## <a name="get-started-with-defender-for-cloud-apps-or-office-365-cloud-app-security"></a>Kom i gang med Defender for Cloud Apps eller Office 365 Cloud App Security

Brug Office 365 Cloud App Security til at evaluere risikoen, til at advare om mistænkelig aktivitet og til automatisk at udføre handlinger. Kræver Office 365 E5 plan.

Du kan også bruge Microsoft Defender for Cloud Apps til at få større synlighed, selv efter at du har fået adgang, omfattende kontrolelementer og forbedret beskyttelse af alle dine cloudprogrammer, herunder Office 365.

Da denne løsning anbefaler EMS E5-planen, anbefaler vi, at du starter med Defender for Cloud Apps, så du kan bruge den sammen med andre SaaS-programmer i dit miljø. Start med standardpolitikker og -indstillinger.

Flere oplysninger:

- [Udrul Defender til Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security)
- [Flere oplysninger om Microsoft Defender for Cloud Apps](https://www.microsoft.com/cloud-platform/cloud-app-security)
- [Hvad er Defender for Cloud Apps?](/cloud-app-security/what-is-cloud-app-security)

:::image type="content" source="../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png" alt-text="Defender for Cloud Apps-dashboardet" lightbox="../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png":::

## <a name="additional-resources"></a>Yderligere ressourcer

Disse artikler og vejledninger indeholder yderligere præskriptive oplysninger til sikring af dit Microsoft 365 miljø:

- [Microsofts sikkerhedsvejledning til politiske kampagner, nonprofitorganisationer og andre agile organisationer](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) (du kan bruge denne anbefaling i alle miljøer, især miljøer, der kun er cloudmiljøer)

- [Anbefalede sikkerhedspolitikker og -konfigurationer for identiteter og enheder](microsoft-365-policies-configurations.md) (disse anbefalinger omfatter hjælp til AD FS-miljøer)
