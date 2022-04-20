---
title: oversigt over Exchange Online Protection (EOP)
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 09/18/2020
audience: ITPro
ms.topic: overview
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: 1270a65f-ddc3-4430-b500-4d3a481efb1e
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan Exchange Online Protection (EOP) kan hjælpe med at beskytte din mailorganisation i det lokale miljø i separate og hybride miljøer.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 19bf82a530cd61b253047261bb44893266a240d8
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941561"
---
# <a name="exchange-online-protection-overview"></a>Oversigt over Exchange Online Protection

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) er den skybaserede filtreringstjeneste, der beskytter din organisation mod spam, malware og andre mailtrusler. EOP er inkluderet i alle Microsoft 365 organisationer med Exchange Online postkasser.

> [!NOTE]
> EOP er også tilgængelig i sig selv for at beskytte postkasser i det lokale miljø og i hybridmiljøer for at beskytte Exchange postkasser i det lokale miljø. Du kan få flere oplysninger under [Separate Exchange Online Protection](/exchange/standalone-eop/standalone-eop).

Trinnene til konfiguration af EOP-sikkerhedsfunktioner og en sammenligning af den ekstra sikkerhed, du får i Microsoft Defender for Office 365, kan du se [Beskyt mod trusler](protect-against-threats.md). De anbefalede indstillinger for EOP-funktioner er tilgængelige under [Anbefalede indstillinger for EOP og Microsoft Defender for Office 365 sikkerhed](recommended-settings-for-eop-and-office365.md).

I resten af denne artikel forklares det, hvordan EOP fungerer, og hvilke funktioner der er tilgængelige i EOP.

## <a name="how-eop-works"></a>Sådan fungerer EOP

For at forstå, hvordan EOP fungerer, hjælper det at se, hvordan den behandler indgående mail:

:::image type="content" source="../../media/tp_emailprocessingineopt3.png" alt-text="Grafik af mail fra internettet eller kundefeedback, der sendes til EOP og via forbindelse, antimalware, mailflowpolitikfiltrering og indholdsfiltrering, før dommen af enten uønsket mail eller karantæne eller levering af slutbrugermail" lightbox="../../media/tp_emailprocessingineopt3.png":::

1. Når en indgående meddelelse kommer ind i EOP, går den i første omgang gennem forbindelsesfiltrering, som kontrollerer afsenderens omdømme. Størstedelen af spam stoppes på dette tidspunkt og afvises af EOP. Du kan få flere oplysninger under [Konfigurer forbindelsesfiltrering](configure-the-connection-filter-policy.md).

2. Derefter inspiceres meddelelsen for malware. Hvis der findes malware i meddelelsen eller den eller de vedhæftede filer, leveres meddelelsen til karantæne. Som standard er det kun administratorer, der kan få vist og interagere med meddelelser, der er sat i karantæne. Men administratorer kan oprette og bruge [karantænepolitikker](quarantine-policies.md) til at angive, hvad brugerne har tilladelse til at gøre for at sætte meddelelser i karantæne. Du kan få mere at vide om beskyttelse mod malware [under Beskyttelse mod skadelig software i EOP](anti-malware-protection.md).

3. Meddelelsen fortsætter via politikfiltrering, hvor den evalueres i forhold til de regler for mailflow (også kaldet transportregler), du har oprettet. En regel kan f.eks. sende en meddelelse til en leder, når der modtages en meddelelse fra en bestemt afsender.

   I organisationen i det lokale miljø med Exchange Enterprise CAL med tjenestelicenser sker [der også microsoft Purview DLP-kontroller (Forebyggelse af datatab)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) i EOP på dette tidspunkt.

4. Meddelelsen går gennem indholdsfiltrering (anti-spam og anti-spoofing), hvor skadelige meddelelser identificeres som spam, spam med høj tillid, phishing, phishing med høj tillid eller masse (politikker for anti-spam) eller spoofing (spoof-indstillinger i politikker til anti-phishing). Du kan konfigurere den handling, der skal udføres på meddelelsen, på baggrund af filterafsigelsen (karantæne, flytning til mappen Uønsket mail osv.), og hvad brugerne kan gøre med de karantænerede meddelelser ved hjælp af [karantænepolitikker](quarantine-policies.md). Du kan få flere oplysninger under [Konfigurer politikker til bekæmpelse af spam](configure-your-spam-filter-policies.md) og [Konfigurer politikker til bekæmpelse af phishing i EOP](configure-anti-phishing-policies-eop.md).

En meddelelse, der overfører alle disse beskyttelseslag, leveres til modtagerne.

Du kan få flere oplysninger under [Rækkefølgen og rækkefølgen af mailbeskyttelse](how-policies-and-protections-are-combined.md).

### <a name="eop-datacenters"></a>EOP-datacentre

EOP kører på et verdensomspændende netværk af datacentre, der er designet til at give den bedste tilgængelighed. Hvis et datacenter f.eks. bliver utilgængeligt, dirigeres mails automatisk til et andet datacenter uden afbrydelser i tjenesten. Servere i hvert datacenter accepterer meddelelser på dine vegne, hvilket giver et lag af adskillelse mellem din organisation og internettet, hvilket reducerer belastningen på dine servere. Via dette netværk, der er meget tilgængeligt, kan Microsoft sikre, at mail når din organisation i tide.

EOP udfører belastningsjustering mellem datacentre, men kun inden for et område. Hvis du klargøres i ét område, behandles alle dine meddelelser ved hjælp af maildistributionen for det pågældende område.

### <a name="eop-features"></a>EOP-funktioner

Dette afsnit indeholder en overordnet oversigt over de vigtigste funktioner, der er tilgængelige i EOP.

Du kan få oplysninger om krav, vigtige grænser og tilgængelighed af funktioner på tværs af alle EOP-abonnementsplaner i [beskrivelsen af Exchange Online Protection-tjenesten](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description).

**Noter**:

- EOP bruger flere URL-blokeringslister, der hjælper med at registrere kendte skadelige links i meddelelser.
- EOP bruger en stor liste over domæner, der er kendt for at sende spam.
- EOP bruger flere antimalwareprogrammer, der hjælper med automatisk at beskytte vores kunder hele tiden.
- EOP undersøger de aktive nyttedata i meddelelsens brødtekst og alle vedhæftede filer i meddelelser for malware.
- Du kan se de anbefalede værdier for beskyttelsespolitikker under [Anbefalede indstillinger for EOP og Microsoft Defender for Office 365 sikkerhed](recommended-settings-for-eop-and-office365.md).
- Hvis du vil have en hurtig vejledning i at konfigurere beskyttelsespolitikker, skal du se [Beskyt mod trusler](protect-against-threats.md).

|Funktion|Kommentarer|
|---|---|
|**Beskyttelse**||
|Antimalware|[Beskyttelse mod skadelig software i EOP](anti-malware-protection.md) <p> [Ofte stillede spørgsmål om beskyttelse mod malware](anti-malware-protection-faq-eop.yml) <p> [Konfigurer politikker for antimalware i EOP](configure-anti-malware-policies.md)|
|Indgående anti-spam|[Beskyttelse mod spam i EOP](anti-spam-protection.md) <p> [Ofte stillede spørgsmål om beskyttelse mod spam](anti-spam-protection-faq.yml) <p> [Konfigurer politikker mod spam i EOP](configure-your-spam-filter-policies.md)|
|Udgående anti-spam|[Beskyttelse mod udgående spam i EOP](outbound-spam-controls.md) <p> [Konfigurer filtrering af udgående spam i EOP](configure-the-outbound-spam-policy.md) <p> [Kontrollér automatisk ekstern videresendelse af mail i Microsoft 365](external-email-forwarding.md)|
|Forbindelsesfiltrering|[Konfigurer filtrering af forbindelse](configure-the-connection-filter-policy.md)|
|Anti-phishing|[Politikker til bekæmpelse af phishing i Microsoft 365](set-up-anti-phishing-policies.md) <p> [Konfigurer politikker for antiphishing i EOP](configure-anti-phishing-policies-eop.md)|
|Beskyttelse mod forfalskning|[Spoof intelligence-indsigt i EOP](learn-about-spoof-intelligence.md) <p> [Administrer listen over tilladte/blokerede lejere](tenant-allow-block-list.md)|
|Zap (automatisk fjernelse på nul timer) for leveret malware, spam og phishing|[ZAP i Exchange Online](zero-hour-auto-purge.md)|
|Forudindstil sikkerhedspolitikker|[Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md) <p> [Konfigurationsanalyse for beskyttelsespolitikker i EOP og Microsoft Defender for Office 365](configuration-analyzer-for-security-policies.md)|
|Liste over tilladte/blokerede lejere|[Administrer listen over tilladte/blokerede lejere](tenant-allow-block-list.md)|
|Bloker lister for afsendere af meddelelser|[Opret lister over blokerede afsendere i EOP](create-block-sender-lists-in-office-365.md)|
|Tillad lister for afsendere af meddelelser|[Opret lister over sikre afsendere i EOP](create-safe-sender-lists-in-office-365.md)|
|Katalogbaseret kantblokering (DBEB)|[Brug mappebaseret kantblokering til at afvise meddelelser, der er sendt til ugyldige modtagere](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking)|
|**Karantæne og indsendelser**||
|Administratorafsendelse|[Brug administratorindsendelse til at sende mistanke om spam, phish, URL-adresser og filer til Microsoft](admin-submission.md)|
|Brugerindsendelser (brugerdefineret postkasse)|[Politik for brugerindsendelser](user-submission.md)|
|Karantæne – administratorer|[Administrer karantænemeddelelser og filer som administrator i EOP](manage-quarantined-messages-and-files.md) <p> [Ofte stillede spørgsmål om karantænemeddelelser](quarantine-faq.yml) <p> [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md) <p> [Brevhoveder mod spam i Microsoft 365](anti-spam-message-headers.md) <p> Du kan analysere brevhovederne i karantænemeddelelser ved hjælp af [Analyse af brevhoved på](https://mha.azurewebsites.net/).|
|Karantæne - slutbrugere|[Find og frigiv karantænemeddelelser som en bruger i EOP](find-and-release-quarantined-messages-as-a-user.md) <p> [Brug karantænemeddelelser til at frigive og rapportere karantænemeddelelser](use-spam-notifications-to-release-and-report-quarantined-messages.md) <p> [Karantænepolitik](quarantine-policies.md)|
|**Mailflow**||
|Regler for mailflow|[Regler for mailflow (transportregler) i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) <p> [Regelbetingelser og undtagelser for mailflow (prædikater) i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions) <p> [Handlinger for mailflowregel i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions) <p> [Administrer regler for mailflow i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules) <p> [Regler for mailflow i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-procedures)|
|Accepterede domæner|[Administrer accepterede domæner i Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)|
|Stik|[Konfigurer mailflow ved hjælp af connectors i Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)|
|Forbedret filtrering for forbindelser|[Forbedret filtrering af forbindelser i Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)|
|**Overvågning**||
|Meddelelsessporing|[Meddelelsessporing](message-trace-scc.md) <p> [Meddelelsessporing i Exchange Administration](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac)|
|Mail & samarbejdsrapporter|[Få vist sikkerhedsrapporter for mail](view-email-security-reports.md)|
|Mailflowrapporter|[Vis rapporter over mailflow](view-mail-flow-reports.md) <p> [Mailflowrapporter i Exchange Administration](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|
|Indsigt i mailflow|[Indsigt i mailflow](mail-flow-insights-v2.md) <p> [Indsigt i mailflow i Exchange Administration](/exchange/monitoring/mail-flow-insights/mail-flow-insights)|
|Overvågningsrapporter|[Overvågningsrapporter i Exchange Administration](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports)|
|Underretningspolitikker|[Underretningspolitikker](../../compliance/alert-policies.md)|
|**Serviceniveauaftaler (SLA'er) og support**||
|SLA for spameffektivitet|\> 99%|
|SLA for falsk positivt forhold|\< 1:250,000|
|Virusregistrering og blokering af SLA|100 % af kendte virusser|
|SLA for månedlig oppetid|99.999%|
|Telefon og web teknisk support 24 timer i døgnet, syv dage om ugen|[Hjælp og support til EOP](help-and-support-for-eop.md).|
|**Andre funktioner**||
|Et geo-redundant globalt netværk af servere|EOP kører på et verdensomspændende netværk af datacentre, der er designet til at hjælpe med at sikre den bedste tilgængelighed. Du kan få flere oplysninger i afsnittet [EOP-datacentre](#eop-datacenters) tidligere i denne artikel.|
|Msmq, når serveren i det lokale miljø ikke kan acceptere post|Meddelelser, der udskydes, forbliver i vores kø i en dag. Forsøg på at gentage meddelelser er baseret på den fejl, vi får tilbage fra modtagerens postsystem. Meddelelser prøves i gennemsnit igen hvert 5. minut. Du kan få flere oplysninger under [Ofte stillede spørgsmål om EOP-meddelelser, der er sat i kø, udskudt eller afvist](eop-queued-deferred-and-bounced-messages-faq.yml).|
|Office 365 meddelelseskryptering tilgængelig som et tilføjelsesprogram|Du kan få flere oplysninger [under Kryptering i Office 365](../../compliance/encryption.md).|
|||
