---
title: Exchange Online Protection (EOP)
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
description: Lær, Exchange Online Protection (EOP) kan hjælpe med at beskytte din lokale mailorganisation i enkeltstående og hybride miljøer.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3fb49a24ae378be990efd727450a06889cc50679
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473359"
---
# <a name="exchange-online-protection-overview"></a>Exchange Online Protection oversigt

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) er den skybaserede filtreringstjeneste, der beskytter din organisation mod spam, malware og andre mailtrusler. EOP er inkluderet i alle Microsoft 365 med Exchange Online postkasser.

> [!NOTE]
> EOP er også tilgængelig for sig selv til at beskytte postkasser i det lokale miljø og i hybridmiljøer for at beskytte lokale Exchange postkasser. Du kan finde flere oplysninger [under Enkeltstående Exchange Online Protection](/exchange/standalone-eop/standalone-eop).

Trinnene til at konfigurere EOP-sikkerhedsfunktioner og en sammenligning af den ekstra sikkerhed, du får Microsoft Defender for Office 365, se [Beskyt dig mod trusler](protect-against-threats.md). De anbefalede indstillinger for EOP-funktioner er tilgængelige [i Anbefalede indstillinger for EOP og Microsoft Defender for Office 365 sikkerhed](recommended-settings-for-eop-and-office365.md).

I resten af denne artikel forklares det, hvordan EOP fungerer, og hvilke funktioner der er tilgængelige i EOP.

## <a name="how-eop-works"></a>Sådan fungerer EOP

For at forstå, hvordan EOP fungerer, hjælper det at se, hvordan det behandler indgående mail:

:::image type="content" source="../../media/tp_emailprocessingineopt3.png" alt-text="Grafik af mail fra internettet eller kundefeedback, der videregives til EOP og via Forbindelse, antimalware, filtrering af regler for mailflow og filtrering af indhold, før du afslutter enten uønsket mail eller karantæne eller leveringen af mails til slutbrugeren" lightbox="../../media/tp_emailprocessingineopt3.png":::

1. Når en indgående meddelelse kommer ind i EOP, gennemgår den til at begynde med filtrering af forbindelsen, hvilket kontrollerer afsenderens ry. Størstedelen af spam stoppes på nuværende tidspunkt og afvises af EOP. Du kan finde flere oplysninger [under Konfigurere filtrering af forbindelse](configure-the-connection-filter-policy.md).

2. Derefter undersøges meddelelsen for malware. Hvis der bliver fundet malware i meddelelsen eller i de vedhæftede filer, leveres meddelelsen til karantæne. Som standard er det kun administratorer, der kan få vist og interagere med malwaremeddelelser, der er i karantæne. Men administratorer kan oprette og bruge karantænepolitikker [til at angive](quarantine-policies.md) , hvad brugerne har tilladelse til at gøre for meddelelser, der er sat i karantæne. Du kan få mere at vide om beskyttelse mod malware [under Beskyttelse mod malware i EOP](anti-malware-protection.md).

3. Meddelelsen fortsætter via politikfiltrering, hvor den evalueres i forhold til eventuelle regler for mailflow (også kaldet transportregler), du har oprettet. En regel kan f.eks. sende en meddelelse til en chef, når der modtages en meddelelse fra en bestemt afsender.

   I en lokal organisation med Exchange Enterprise CAL med servicelicenser, udføres [DLP-kontroller (forebyggelse](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) af datatab) også i EOP på dette tidspunkt.

4. Meddelelsen passerer gennem filtrering af indhold (antispam og uønsket spoofing), hvor skadelige meddelelser identificeres som spam, spam med høj tillid, phishing, phishing med høj sikkerhed eller massemail (antispampolitikker) eller spoofing (spoof-indstillinger i antiphishing-politikker). Du kan konfigurere den handling, der skal udføre handlingen på meddelelsen, baseret på filtreringens vurdering (karantæne, flytning til mappen Uønsket mail osv.), og hvad brugerne kan gøre ved de meddelelser, der er i karantæne, ved hjælp af karantænepolitikker[.](quarantine-policies.md) Få mere at vide under [Konfigurer antispampolitikker](configure-your-spam-filter-policies.md) og [Konfigurer antiphishing-politikker i EOP](configure-anti-phishing-policies-eop.md).

En meddelelse, der er korrekt videregivet alle disse beskyttelseslag, leveres til modtagerne.

Du kan finde flere oplysninger [i Rækkefølgen og prioriteten af mailbeskyttelse](how-policies-and-protections-are-combined.md).

### <a name="eop-datacenters"></a>EOP-datacentre

EOP kører på et verdensomspændende netværk af datacentre, der er designet til at give den bedste tilgængelighed. Hvis et datacenter f.eks. ikke længere er tilgængeligt, sendes mails automatisk til et andet datacenter uden afbrydelser i tjenesten. Servere i hvert datacenter accepterer meddelelser på dine vegne, hvilket giver et lag af adskillelse mellem din organisation og internettet, hvilket reducerer belastningen på dine servere. Via dette meget tilgængelige netværk kan Microsoft sikre, at mail når rettidigt frem til din organisation.

EOP udfører belastningsjustering mellem datacentre, men kun inden for et område. Hvis du er klargjort i ét område, behandles alle dine meddelelser ved hjælp af mail-routing for det pågældende område.

### <a name="eop-features"></a>EOP-funktioner

Dette afsnit indeholder en detaljeret oversigt over de vigtigste funktioner, der er tilgængelige i EOP.

Du kan finde oplysninger om krav, vigtige begrænsninger og tilgængelighed af funktioner på tværs af alle EOP-abonnementsplaner [i Exchange Online Protection tjenestebeskrivelse](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description).

**Bemærkninger**:

- EOP bruger flere lister over URL-adresser, der hjælper med at registrere kendte ondsindede links i meddelelser.
- EOP bruger en stor liste over domæner, der er kendt for at sende spam.
- EOP bruger flere antimalware programmer til automatisk at beskytte vores kunder hele tiden.
- EOP undersøger den aktive nyttedata i meddelelsens brødtekst og alle vedhæftede filer for malware.
- Du kan finde anbefalede værdier for beskyttelsespolitikker i [Anbefalede indstillinger for EOP og Microsoft Defender for Office 365 sikkerhed](recommended-settings-for-eop-and-office365.md).
- Du kan finde en hurtig vejledning i, hvordan du [konfigurerer beskyttelsespolitikker, under Beskyt dig mod trusler](protect-against-threats.md).

|Funktion|Kommentarer|
|---|---|
|**Beskyttelse**||
|Antimalware|[Beskyttelse mod malware i EOP](anti-malware-protection.md) <p> [Ofte stillede spørgsmål om beskyttelse mod malware](anti-malware-protection-faq-eop.yml) <p> [Konfigurer antimalwarepolitikker i EOP](configure-anti-malware-policies.md)|
|Indgående antispam|[Beskyttelse mod spam i EOP](anti-spam-protection.md) <p> [Ofte stillede spørgsmål om beskyttelse mod spam](anti-spam-protection-faq.yml) <p> [Konfigurer antispampolitikker i EOP](configure-your-spam-filter-policies.md)|
|Udgående antispam|[Beskyttelse mod udgående spam i EOP](outbound-spam-controls.md) <p> [Konfigurere udgående spamfiltrering i EOP](configure-the-outbound-spam-policy.md) <p> [Kontrollere automatisk videresendelse af eksterne mails Microsoft 365](external-email-forwarding.md)|
|Forbindelsesfiltrering|[Konfigurere filtrering af forbindelse](configure-the-connection-filter-policy.md)|
|Antiphishing|[Antiphishing-politikker i Microsoft 365](set-up-anti-phishing-policies.md) <p> [Konfigurer antiphishing-politikker i EOP](configure-anti-phishing-policies-eop.md)|
|Beskyttelse mod spoofing|[Efterlignet intelligensindsigt i EOP](learn-about-spoof-intelligence.md) <p> [Administrer lejerens tilladelses-/blokeringsliste](tenant-allow-block-list.md)|
|Nul-timers automatisk tømning (ZAP) for leveret malware, spam og phishing-meddelelser|[ZAP i Exchange Online](zero-hour-auto-purge.md)|
|Forudindstillede sikkerhedspolitikker|[Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md) <p> [Konfigurationsanalyse til beskyttelsespolitikker i EOP og Microsoft Defender for Office 365](configuration-analyzer-for-security-policies.md)|
|Lejers tilladelses-/blokeringsliste|[Administrer lejerens tilladelses-/blokeringsliste](tenant-allow-block-list.md)|
|Blokere lister for meddelelsesafsendere|[Opret lister over blokerede afsendere i EOP](create-block-sender-lists-in-office-365.md)|
|Tilladelseslister for meddelelsesafsendere|[Opret lister over afsendere, der er tillid til i EOP](create-safe-sender-lists-in-office-365.md)|
|Mappebaseret blokering af kanter (DBEB)|[Brug blokering af mappebaseret kant til at afvise meddelelser, der sendes til ugyldige modtagere](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking)|
|**Karantæne og indsendelser**||
|Administratorindsendelse|[Brug administratorindsendelse til at sende mistænkeligt spam, phish, URL-adresser og filer til Microsoft](admin-submission.md)|
|Brugerindsendelser (brugerdefineret postkasse)|[Politik for brugerindsendelser](user-submission.md)|
|Karantæne – administratorer|[Administrer meddelelser og filer, der er sat i karantæne, som administrator i EOP](manage-quarantined-messages-and-files.md) <p> [Ofte stillede spørgsmål om meddelelser i karantæne](quarantine-faq.yml) <p> [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md) <p> [Antispam-brevhoveder i Microsoft 365](anti-spam-message-headers.md) <p> Du kan analysere brevhovederne for meddelelser, der er sat i karantæne, ved [hjælp af Analyse af brevhoved](https://mha.azurewebsites.net/) på.|
|Karantæne – slutbrugere|[Find og slip meddelelser, der er sat i karantæne, som en bruger i EOP](find-and-release-quarantined-messages-as-a-user.md) <p> [Brug af karantænemeddelelser til at frigive og rapportere meddelelser, der er sat i karantæne](use-spam-notifications-to-release-and-report-quarantined-messages.md) <p> [Karantænepolitikker](quarantine-policies.md)|
|**Mailflow**||
|Regler for mailflow|[Regler for mailflow (transportregler) i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) <p> [Betingelser og undtagelser for regler for mailflow (prædikater) i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions) <p> [Handlinger for regler for mailflow i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions) <p> [Administrer regler for mailflow i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules) <p> [Mailflowregelprocedurer i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-procedures)|
|Accepterede domæner|[Administrer accepterede domæner i Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)|
|Forbindelser|[Konfigurer mailflow ved hjælp af forbindelser i Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)|
|Forbedret filtrering for forbindelser|[Forbedret filtrering af forbindelser i Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)|
|**Overvågning**||
|Meddelelsessporing|[Meddelelsessporing](message-trace-scc.md) <p> [Meddelelsessporing i Exchange Administration](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac)|
|Rapporter & mailsamarbejde|[Få vist mailsikkerhedsrapporter](view-email-security-reports.md)|
|Mailflowrapporter|[Få vist mailflowrapporter](view-mail-flow-reports.md) <p> [Mailflowrapporter i Exchange Administration](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|
|Indsigt i mailflow|[Indsigt i mailflow](mail-flow-insights-v2.md) <p> [Indsigt i mailflow Exchange Administration](/exchange/monitoring/mail-flow-insights/mail-flow-insights)|
|Overvågningsrapporter|[Overvågningsrapporter i Exchange Administration](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports)|
|Beskedpolitikker|[Beskedpolitikker](../../compliance/alert-policies.md)|
|**Serviceaftale og support**||
|Sla for spameffektiviteten|\> 99%|
|FALSK positiv ratio SLA|\< 1:250,000|
|Virusregistrering og blokering af SLA|100 % af kendte virusser|
|Serviceaftale for månedlig oppetid|99.999%|
|Telefon og teknisk websupport 24 timer i døgnet, syv dage om ugen|[Hjælp og support til EOP](help-and-support-for-eop.md).|
|**Andre funktioner**||
|Et geo redundant globalt netværk af servere|EOP kører på et verdensomspændende netværk af datacentre, der er designet til at hjælpe med at levere den bedste tilgængelighed. Du kan finde flere oplysninger i [afsnittet EOP-datacentre](#eop-datacenters) tidligere i denne artikel.|
|Meddelelseskø, når den lokale server ikke kan acceptere mail|Meddelelser, der udskydes, forbliver i vores køer i en dag. Gentagne forsøg på meddelelse er baseret på den fejl, vi får tilbage fra modtagerens mailsystem. I gennemsnit foreprøves meddelelser igen hvert 5. minut. Få mere at vide under [Ofte stillede spørgsmål om EOP i kø, udskudt og afvist meddelelse](eop-queued-deferred-and-bounced-messages-faq.yml).|
|Office 365 tilgængelig meddelelseskryptering som et tilføjelsesprogrammet|Du kan finde flere oplysninger [under Kryptering i Office 365](../../compliance/encryption.md).|
|||
