---
title: Reference til forebyggelse af datatab
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: ''
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ROBOTS: NOINDEX, NOFOLLOW
feedback_system: None
description: referencemateriale til forebyggelse af datatab
ms.openlocfilehash: b7546d41310942a0e6eab99511a78c594822ee2a
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017280"
---
# <a name="data-loss-prevention-reference"></a>Reference til forebyggelse af datatab

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!IMPORTANT]
> Dette er et referenceemne, der ikke længere er hovedressourcen til oplysninger om Forebyggelse af datatab i Microsoft Purview (DLP). DLP-indholdssættet opdateres og omstruktureres. De emner, der behandles i denne artikel, går videre til nye, opdaterede artikler. Du kan finde flere oplysninger om DLP under [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md).

<!-- this topic needs to be split into smaller, more coherent ones. It is confusing as it is. -->
<!-- move this note to a more appropriate place, no topic should start with a note -->
> [!NOTE]
> Funktioner til forebyggelse af datatab blev for nylig føjet til Microsoft Teams chat- og kanalmeddelelser for brugere med licens til Avanceret overholdelse i Office 365, som er tilgængelig som en separat mulighed og er inkluderet i Office 365 E5 og Microsoft 365 E5 Overholdelse. Hvis du vil vide mere om licenskrav, [skal du se Licensvejledning til Microsoft 365 Tenant-Level-tjenester](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance).



<!-- MOVED TO LEARN ABOUT To comply with business standards and industry regulations, organizations must protect sensitive information and prevent its inadvertent disclosure. Sensitive information can include financial data or personally identifiable information (PII) such as credit card numbers, social security numbers, or health records. With a data loss prevention (DLP) policy in the Microsoft Purview compliance portal, you can identify, monitor, and automatically protect sensitive information across Office 365.

With a DLP policy, you can:

- **Identify sensitive information across many locations, such as Exchange Online, SharePoint Online, OneDrive for Business, and Microsoft Teams.**

    For example, you can identify any document containing a credit card number that's stored in any OneDrive for Business site, or you can monitor just the OneDrive sites of specific people.

- **Prevent the accidental sharing of sensitive information**.

    For example, you can identify any document or email containing a health record that's shared with people outside your organization, and then automatically block access to that document or block the email from being sent.

- **Monitor and protect sensitive information in the desktop versions of Excel, PowerPoint, and Word.**

    Just like in Exchange Online, SharePoint Online, and OneDrive for Business, these Office desktop programs include the same capabilities to identify sensitive information and apply DLP policies. DLP provides continuous monitoring when people share content in these Office programs.

- **Help users learn how to stay compliant without interrupting their workflow.**

    You can educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification. The same policy tips also appear in Outlook on the web, Outlook, Excel, PowerPoint, and Word.

- **View DLP alerts and reports showing content that matches your organization’s DLP policies.**

    To view alerts and metadata related to your DLP policies you can use the [DLP Alerts Management Dashboard](dlp-configure-view-alerts-policies.md). You can also view policy match reports to assess how your organization is complying with a DLP policy. If a DLP policy allows users to override a policy tip and report a false positive, you can also view what users have reported

-->
## <a name="create-and-manage-dlp-policies"></a>Opret og administrer DLP-politikker

Du kan oprette og administrere DLP-politikker på siden til forebyggelse af datatab på Microsoft Purview-overholdelsesportalen.

![Siden til forebyggelse af datatab på Microsoft Purview-overholdelsesportalen](../media/943fd01c-d7aa-43a9-846d-0561321a405e.png)

<!-- MOVED TO LEARN ABOUT ## What a DLP policy contains

A DLP policy contains a few basic things:

- Where to protect the content: **locations** such as Exchange Online, SharePoint Online, and OneDrive for Business sites, as well as Microsoft Teams chat and channel messages.

- When and how to protect the content by enforcing **rules** comprised of:

  - **Conditions** the content must match before the rule is enforced. For example, a rule might be configured to look only for content containing Social Security numbers that's been shared with people outside your organization.

  - **Actions** that you want the rule to take automatically when content matching the conditions is found. For example, a rule might be configured to block access to a document and send both the user and compliance officer an email notification.

You can use a rule to meet a specific protection requirement, and then use a DLP policy to group together common protection requirements, such as all of the rules needed to comply with a specific regulation.

For example, you might have a DLP policy that helps you detect the presence of information subject to the Health Insurance Portability and Accountability Act (HIPAA). This DLP policy could help protect HIPAA data (the what) across all SharePoint Online sites and all OneDrive for Business sites (the where) by finding any document containing this sensitive information that's shared with people outside your organization (the conditions) and then blocking access to the document and sending a notification (the actions). These requirements are stored as individual rules and grouped together as a DLP policy to simplify management and reporting.

![Diagram shows that DLP policy contains locations and rules.](../media/c006860c-2d00-42cb-aaa4-5b5638d139f7.png) -->

<!-- MOVED TO LEARN ABOUT ### Locations

DLP policies are applied to sensitive items across Microsoft 365 locations and can be further scoped as detailed in this table.


|Location | Include/exclude by|
|---------|---------|
|Exchange email| distribution groups|
|SharePoint sites |sites |
|OneDrive accounts |accounts |
|Teams chat and channel messages |accounts |
|Windows 10 devices |user or group |
|Microsoft Cloud App Security |instance |
 -->

<!-- moved to dlp-policy-reference.md
If you choose to include specific distribution groups in Exchange, the DLP policy will be scoped only to the members of that group. Similarly excluding a distribution group will exclude all the members of that distribution group from policy evaluation. You can choose to scope a policy to the members of distribution lists, dynamic distribution groups, and security groups. A DLP policy can contain no more than 50 such inclusions and exclusions.

If you choose to include or exclude specific SharePoint sites, a DLP policy can contain no more than 100 such inclusions and exclusions. Although this limit exists, you can exceed this limit by applying either an org-wide policy or a policy that applies to entire locations.

If you choose to include or exclude specific OneDrive accounts or groups, a DLP policy can contain no more than 100 user accounts or 50 groups as inclusion or exclusion.

### Rules

> [!NOTE]
> The default behavior of a DLP policy, when there is no alert configured, is not to alert or trigger. This applies only to default information types. For custom information types, the system will alert even if there is no action defined in the policy.

Rules are what enforce your business requirements on your organization's content. A policy contains one or more rules, and each rule consists of conditions and actions. For each rule, when the conditions are met, the actions are taken automatically. Rules are executed sequentially, starting with the highest-priority rule in each policy.

A rule also provides options to notify users (with policy tips and email notifications) and admins (with email incident reports) that content has matched the rule.

Here are the components of a rule, each explained below.

![Sections of the DLP rule editor.](../media/1859d504-b9c2-45ed-961b-a0092251acc2.png)

#### Conditions

Conditions are important because they determine what types of information you're looking for, and when to take an action. For example, you might choose to ignore content containing passport numbers unless the content contains more than 10 such numbers and is shared with people outside your organization.

Conditions focus on the **content**, such as what types of sensitive information you're looking for, and also on the **context**, such as who the document is shared with. You can use conditions to assign different actions to different risk levels. For example, sensitive content shared internally might be lower risk and require fewer actions than sensitive content shared with people outside the organization.

![List showing available DLP conditions.](../media/0fa43f90-d007-4506-ae93-43e8424fe103.png)

The conditions now available can determine if:

- Content contains a type of sensitive information.

- Content contains a label. For more information, see the below section [Using a retention label as a condition in a DLP policy](#using-a-retention-label-as-a-condition-in-a-dlp-policy).

- Content is shared with people outside or inside your organization.

  > [!NOTE]
  > Users who have non-guest accounts in a host organization's Active Directory or Azure Active Directory tenant are considered as people inside the organization.

#### Types of sensitive information

A DLP policy can help protect sensitive information, which is defined as a **sensitive information type**. Microsoft 365 includes definitions for many common sensitive information types across many different regions that are ready for you to use, such as a credit card number, bank account numbers, national ID numbers, and passport numbers.

![List of available sensitive information types.](../media/3eaa9911-bc94-44be-902f-363dbf3b07fe.png)

When a DLP policy looks for a sensitive information type such as a credit card number, it doesn't simply look for a 16-digit number. Each sensitive information type is defined and detected by using a combination of:

- Keywords.

- Internal functions to validate checksums or composition.

- Evaluation of regular expressions to find pattern matches.

- Other content examination.

This helps DLP detection achieve a high degree of accuracy while reducing the number of false positives that can interrupt peoples' work.

#### Actions

When content matches a condition in a rule, you can apply actions to automatically protect the content.

![List of available DLP actions.](../media/8aef17fc-1e99-4ac7-adfc-0f2c9c1a0697.png)

With the actions now available, you can:

- **Restrict access to the content** Depending on your need, you can restrict access to content in three ways:

  1. Restrict access to content for everyone.
  2. Restrict access to content for people outside the organization.
  3. Restrict access to "Anyone with the link."

  For site content, this means that permissions for the document are restricted for everyone except the primary site collection administrator, document owner, and person who last modified the document. These people can remove the sensitive information from the document or take other remedial action. When the document is in compliance, the original permissions are automatically restored. When access to a document is blocked, the document appears with a special policy tip icon in the library on the site.

  ![Policy tip showing access to document is blocked.](../media/b6cefed3-d212-43d7-8534-4b92b26ebd50.png)

  For email content, this action blocks the message from being sent. Depending on how the DLP rule is configured, the sender sees an NDR or (if the rule uses a notification) a policy tip and/or email notification.

  ![Warning that unauthorized recipients must be removed from the message.](../media/302f9994-912d-41e7-861f-8a4539b3c285.png)

#### User notifications and user overrides

You can use notifications and overrides to educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification.

![User notifications and user overrides sections of DLP rule editor.](../media/37b560d4-6e4e-489e-9134-d4b9daf60296.png)

The email can notify the person who sent, shared, or last modified the content and, for site content, the primary site collection administrator and document owner. In addition, you can add or remove whomever you choose from the email notification.

In addition to sending an email notification, a user notification displays a policy tip:

- In Outlook and Outlook on the web.

- For the document on a SharePoint Online or OneDrive for Business site.

- In Excel, PowerPoint, and Word, when the document is stored on a site included in a DLP policy.

The email notification and policy tip explain why content conflicts with a DLP policy. If you choose, the email notification and policy tip can allow users to override a rule by reporting a false positive or providing a business justification. This can help you educate users about your DLP policies and enforce them without preventing people from doing their work. Information about overrides and false positives is also logged for reporting (see below about the DLP reports) and included in the incident reports (next section), so that the compliance officer can regularly review this information.

Here's what a policy tip looks like in a OneDrive for Business account.

![Policy tip for a document in a OneDrive account.](../media/f9834d35-94f0-4511-8555-0fe69855ce6d.png)

 To learn more about user notifications and policy tips in DLP policies, see [Use notifications and policy tips](use-notifications-and-policy-tips.md).

#### Alerts and Incident reports

When a rule is matched, you can send an alert email to your compliance officer (or any person(s) you choose) with details of the alert. This alert email will carry a link of the [DLP Alerts Management Dashboard](dlp-configure-view-alerts-policies.md) which the compliance officer can go to view the details of alert and events. The dashboard contains details of the event that triggered the alert along with details of the DLP policy matched and the sensitive content detected.

In addition, you can also send an incident report with details of the event. This report includes information about the item that was matched, the actual content that matched the rule, and the name of the person who last modified the content. For email messages, the report also includes as an attachment the original message that matches a DLP policy.

> [!div class="mx-imgBorder"]
> ![Page for configuring incident reports.](../media/Alerts-and-incident-report.png)

DLP scans email differently from items in SharePoint Online or OneDrive for Business. In SharePoint Online and OneDrive for Business, DLP scans existing items as well as new ones and generates an alert and incident report whenever a match is found. In Exchange Online, DLP only scans new email messages and generates a report if there is a policy match. DLP ***does not*** scan or match previously existing email items that are stored in a mailbox or archive.

## Grouping and logical operators

Often your DLP policy has a straightforward requirement, such as to identify all content that contains a U.S. Social Security Number. However, in other scenarios, your DLP policy might need to identify more loosely defined data.

For example, to identify content subject to the U.S. Health Insurance Act (HIPAA), you need to look for:

- Content that contains specific types of sensitive information, such as a U.S. Social Security Number or Drug Enforcement Agency (DEA) Number.

    AND

- Content that's more difficult to identify, such as communications about a patient's care or descriptions of medical services provided. Identifying this content requires matching keywords from very large keyword lists, such as the International Classification of Diseases (ICD-9-CM or ICD-10-CM).

You can easily identify such loosely defined data by using grouping and logical operators (AND, OR). When you create a DLP policy, you can:

- Group sensitive information types.

- Choose the logical operator between the sensitive information types within a group and between the groups themselves.

### Choosing the operator within a group

Within a group, you can choose whether any or all of the conditions in that group must be satisfied for the content to match the rule.

![Group showing the operators within the group.](../media/6a12f1e8-112d-48ee-9a73-82b3dd0542e7.png)

### Adding a group

You can quickly add a group, which can have its own conditions and operator within that group.

![Add group button.](../media/5f72f292-d1f3-4f11-a911-a9f71e10abf6.png)

### Choosing the operator between groups

Between groups, you can choose whether the conditions in just one group or all of the groups must be satisfied for the content to match the rule.

For example, the built-in **U.S. HIPAA** policy has a rule that uses an **AND** operator between the groups so that it identifies content that contains:

- from the group **PII Identifiers** (at least one SSN number **OR** DEA number)

    **AND**

- from the group **Medical Terms** (at least one ICD-9-CM keyword **OR** ICD-10-CM keyword)

![Groups showing the operator between groups.](../media/354aa77f-569c-4847-9dfe-605ee2bb28d1.png)

## The priority by which rules are processed

When you create rules in a policy, each rule is assigned a priority in the order in which it's created — meaning, the rule created first has first priority, the rule created second has second priority, and so on.

> [!div class="mx-imgBorder"]
> ![Rules in priority order.](../media/dlp-rules-in-priority-order.png)

After you have set up more than one DLP policy, you can change the priority of one or more policies. To do that, select a policy, choose **Edit policy**, and use the **Priority** list to specify its priority.

> [!div class="mx-imgBorder"]
> ![Set priority for a policy.](../media/dlp-set-policy-priority.png)

When content is evaluated against rules, the rules are processed in priority order. If content matches multiple rules, the rules are processed in priority order and the most restrictive action is enforced. For example, if content matches all of the following rules, Rule 3 is enforced because it's the highest priority, most restrictive rule:

- Rule 1: only notifies users

- Rule 2: notifies users, restricts access, and allows user overrides

- Rule 3: notifies users, restricts access, and does not allow user overrides

- Rule 4: only notifies users

- Rule 5: restricts access

- Rule 6: notifies users, restricts access, and does not allow user overrides

In this example, note that matches for all of the rules are recorded in the audit logs and shown in the DLP reports, even though only the most restrictive rule is enforced.

Regarding policy tips, note that:

- Only the policy tip from the highest priority, most restrictive rule will be shown. For example, a policy tip from a rule that blocks access to content will be shown over a policy tip from a rule that simply sends a notification. This prevents people from seeing a cascade of policy tips.

- If the policy tips in the most restrictive rule allow people to override the rule, then overriding this rule also overrides any other rules that the content matched.

-->

## <a name="tuning-rules-to-make-them-easier-or-harder-to-match"></a>Justering af regler for at gøre dem nemmere eller sværere at matche

Når folk har oprettet og slået deres DLP-politikker til, støder de nogle gange på disse problemer:

- For meget indhold, der **ikke er** følsomme oplysninger, stemmer overens med reglerne – med andre ord for mange falske positiver.

- For lidt indhold, der **er** følsomme oplysninger, stemmer overens med reglerne. Med andre ord gennemtvinges de beskyttende handlinger ikke på de følsomme oplysninger.

Du kan løse disse problemer ved at justere dine regler ved at justere antallet af forekomster og matche nøjagtigheden for at gøre det sværere eller nemmere for indhold at matche reglerne. Hver type følsomme oplysninger, der bruges i en regel, har både antal forekomster og matchnøjagtighed.

### <a name="instance-count"></a>Antal forekomster

Antal forekomster betyder ganske enkelt, hvor mange forekomster af en bestemt type følsomme oplysninger der skal være til stede, for at indholdet stemmer overens med reglen. Indholdet stemmer f.eks. overens med den regel, der er vist nedenfor, hvis det er mellem 1 og 9 entydige amerikanske eller britiske. pasnumre identificeres.

> [!NOTE]
> Antallet af forekomster omfatter kun **entydige** match for følsomme informationstyper og nøgleord. Hvis en mail f.eks. indeholder 10 forekomster af det samme kreditkortnummer, tæller disse 10 forekomster som en enkelt forekomst af et kreditkortnummer.

Hvis du vil bruge antal forekomster til at justere regler, er vejledningen ligetil:

- Hvis du vil gøre det nemmere at matche reglen, skal du reducere **minimumantallet** og/eller øge det **maksimale** antal. Du kan også angive **maks** . til **enhver** ved at slette den numeriske værdi.

- Hvis du vil gøre det sværere at matche reglen, skal du øge **minimumantallet** .

Du bruger typisk mindre restriktive handlinger, f.eks. afsendelse af brugermeddelelser, i en regel med et lavere antal forekomster (f.eks. 1-9). Og du bruger mere restriktive handlinger, f.eks. begrænsning af adgang til indhold uden at tillade brugertilsidesættelser, i en regel med et højere antal forekomster (f.eks. 10-any).

![Antallet af forekomster i regeleditoren.](../media/e7ea3c12-72c5-4bb3-9590-c924c665e84d.png)

### <a name="match-accuracy"></a>Match nøjagtighed

Som beskrevet ovenfor defineres og registreres en følsom informationstype ved hjælp af en kombination af forskellige typer beviser. Normalt defineres en følsom informationstype af flere sådanne kombinationer, kaldet mønstre. Et mønster, der kræver færre beviser, har en lavere matchnøjagtighed (eller et lavere konfidensniveau), mens et mønster, der kræver flere beviser, har højere matchnøjagtighed (eller konfidensniveau). Hvis du vil vide mere om de faktiske mønstre og tillidsniveauer, der bruges af alle typer følsomme oplysninger, skal du se [Objektdefinitioner for følsomme oplysninger.](sensitive-information-type-entity-definitions.md)

Den følsomme oplysningstype med navnet Kreditkortnummer er f.eks. defineret af to mønstre:

- Et mønster med 65 %-tillid, der kræver:

  - Et tal i formatet af et kreditkortnummer.

  - Et tal, der passerer kontrolsummen.

- Et mønster med 85 %-tillid, der kræver:

  - Et tal i formatet af et kreditkortnummer.

  - Et tal, der passerer kontrolsummen.

  - Et nøgleord eller en udløbsdato i det rigtige format.

Du kan bruge disse tillidsniveauer (eller matche nøjagtighed) i dine regler. Du bruger typisk mindre restriktive handlinger, f.eks. afsendelse af brugermeddelelser, i en regel med lavere matchnøjagtighed. Og du bruger mere restriktive handlinger, f.eks. begrænsning af adgang til indhold uden at tillade brugertilsidesættelser, i en regel med højere matchnøjagtighed.

Det er vigtigt at forstå, at når en bestemt type følsomme oplysninger, f.eks. et kreditkortnummer, identificeres i indhold, returneres der kun et enkelt tillidsniveau:

- Hvis alle matches er for et enkelt mønster, returneres konfidensniveauet for det pågældende mønster.

- Hvis der er match for mere end ét mønster (dvs. der er match med to forskellige konfidensniveauer), returneres et konfidensniveau, der er højere end nogen af de enkelte mønstre alene. Det her er den vanskelige del. Hvis mønstrene på både 65 % og 85 % f.eks. matches for et kreditkort, er det tillidsniveau, der returneres for den pågældende type følsomme oplysninger, større end 90 %, fordi flere beviser betyder større tillid.

Så hvis du vil oprette to gensidigt udelukkende regler for kreditkort, én for 65 % matchnøjagtighed og én for 85 % matchnøjagtighed, vil intervaller for matchnøjagtighed se sådan ud. Den første regel henter kun forekomster af mønsteret på 65 %. Den anden regel henter match med **mindst ét match på** 85 % og **kan potentielt have** andre matches med lavere genkendelsessikkerhed.

![To regler med forskellige intervaller for matchnøjagtighed.](../media/21bdfe36-7a91-4347-8098-11809a92f9a4.png)

Af disse årsager er vejledningen til oprettelse af regler med forskellige match accuracies:

- Det laveste konfidensniveau bruger typisk den samme værdi for **min.** og **maks** . (ikke et interval).

- Det højeste konfidensniveau er typisk et interval fra lige over det lavere konfidensniveau til 100.

- Alle mellem konfidensniveauer spænder typisk fra lige over det lavere konfidensniveau til lige under det højere konfidensniveau.

## <a name="using-a-retention-label-as-a-condition-in-a-dlp-policy"></a>Brug af en opbevaringsmærkat som en betingelse i en DLP-politik

Når du bruger en tidligere oprettet og publiceret [opbevaringsmærkat](retention.md#retention-labels) som en betingelse i en DLP-politik, er der nogle ting, du skal være opmærksom på:

- Opbevaringsmærkaten skal oprettes og publiceres, før du forsøger at bruge den som en betingelse i en DLP-politik.
- Det kan tage fra en til syv dage at synkronisere publicerede opbevaringsmærkater. Du kan finde flere oplysninger under [Når opbevaringsmærkater bliver tilgængelige for at ansøge om](create-apply-retention-labels.md#when-retention-labels-become-available-to-apply) opbevaringsmærkater, der er publiceret i en opbevaringspolitik, og [Hvor lang tid det tager for opbevaringsmærkater at træde i kraft](apply-retention-labels-automatically.md#how-long-it-takes-for-retention-labels-to-take-effect) for opbevaringsmærkater, der udgives automatisk.
- Brug af en opbevaringsmærkat i en politik **understøttes kun for elementer i SharePoint og OneDrive***.

  ![Navne som en betingelse.](../media/5b1752b4-a129-4a88-b010-8dcf8a38bb09.png)

  Det kan være en god idé at bruge en opbevaringsmærkat i en DLP-politik, hvis du har elementer, der er under opbevaring og fordeling, og du også vil anvende andre kontrolelementer på dem, f.eks.:

  - Du har udgivet en opbevaringsmærkat med navnet **Skatteår 2018**, som, når den blev anvendt på skattedokumenter fra 2018, som er gemt i SharePoint opbevarer dem i 10 år, og derefter afhænder dem. Du ønsker heller ikke, at disse elementer deles uden for din organisation, hvilket du kan gøre med en DLP-politik.

  > [!IMPORTANT]
  > Du får vist denne fejl, hvis du angiver en opbevaringsmærkat som en betingelse i en DLP-politik, og du også inkluderer Exchange og/eller Teams som en placering: **"Beskyttelse af markeret indhold i mails og teams-meddelelser understøttes ikke. Du skal enten fjerne etiketten nedenfor eller deaktivere Exchange og Teams som en placering."** Det skyldes, at Exchange transport ikke evaluerer mærkatmetadataene under afsendelse og levering af meddelelser.

### <a name="using-a-sensitivity-label-as-a-condition-in-a-dlp-policy"></a>Brug af en følsomhedsmærkat som en betingelse i en DLP-politik

[Få mere at vide](./dlp-sensitivity-label-as-condition.md) om brug af følsomhedsmærkat som en betingelse i DLP-politikker.

### <a name="how-this-feature-relates-to-other-features"></a>Sådan er denne funktion relateret til andre funktioner

Der kan anvendes flere funktioner på indhold, der indeholder følsomme oplysninger:

- En [opbevaringsmærkat og en opbevaringspolitik](retention.md) kan begge gennemtvinge **opbevaringshandlinger** for dette indhold.

- En DLP-politik kan gennemtvinge **beskyttelseshandlinger** for dette indhold. Og før du gennemtvinger disse handlinger, kan en DLP-politik kræve, at andre betingelser er opfyldt ud over det indhold, der indeholder en mærkat.

![Diagram over funktioner, der kan anvendes på følsomme oplysninger.](../media/dd410f97-a3a3-455c-a1e9-7ed8ae6893d6.png)

Bemærk, at en DLP-politik har en bedre registreringsfunktion end en mærkat- eller opbevaringspolitik, der anvendes på følsomme oplysninger. En DLP-politik kan gennemtvinge beskyttende handlinger på indhold, der indeholder følsomme oplysninger, og hvis de følsomme oplysninger fjernes fra indholdet, fortrydes disse beskyttende handlinger, næste gang indholdet scannes. Men hvis der anvendes en opbevaringspolitik eller -mærkat på indhold, der indeholder følsomme oplysninger, er det en engangshandling, der ikke fortrydes, selvom de følsomme oplysninger fjernes.

Ved at bruge en mærkat som en betingelse i en DLP-politik kan du gennemtvinge både opbevarings- og beskyttelseshandlinger for indhold med den pågældende mærkat. Du kan tænke på indhold, der indeholder en mærkat, nøjagtigt som indhold, der indeholder følsomme oplysninger – både en mærkat og en følsom oplysningstype er egenskaber, der bruges til at klassificere indhold, så du kan gennemtvinge handlinger på det pågældende indhold.

![Diagram over DLP-politik, der bruger mærkat som en betingelse.](../media/4538fd8f-fb74-4743-bc22-a5de33adfebb.png)

## <a name="simple-settings-vs-advanced-settings"></a>Enkle indstillinger i forhold til avancerede indstillinger

Når du opretter en DLP-politik, skal du vælge mellem enkle eller avancerede indstillinger:

- **Enkle indstillinger** gør det nemt at oprette den mest almindelige type DLP-politik uden at bruge regeleditoren til at oprette eller redigere regler.

- **Avancerede indstillinger** bruger regeleditoren til at give dig fuld kontrol over alle indstillinger for din DLP-politik.

Bare rolig, under dækkene fungerer enkle indstillinger og avancerede indstillinger nøjagtigt det samme ved at gennemtvinge regler, der består af betingelser og handlinger – kun med enkle indstillinger kan du ikke se regeleditoren. Det er en hurtig måde at oprette en DLP-politik på.

### <a name="simple-settings"></a>Enkle indstillinger

Langt det mest almindelige DLP-scenarie er at oprette en politik, der hjælper med at beskytte indhold, der indeholder følsomme oplysninger, mod at blive delt med personer uden for din organisation og foretage en automatisk afhjælpning, f.eks. begrænse, hvem der har adgang til indholdet, sende slutbruger- eller administratormeddelelser og overvåge hændelsen til senere undersøgelse. Folk bruger DLP til at forhindre utilsigtet offentliggørelse af følsomme oplysninger.

Hvis du vil gøre det nemmere at nå dette mål, kan du vælge **Brug enkle indstillinger**, når du opretter en DLP-politik. Disse indstillinger indeholder alt, hvad du skal bruge for at implementere den mest almindelige DLP-politik uden at skulle gå ind i regeleditoren.

![DLP-indstillinger for enkle og avancerede indstillinger.](../media/33c93824-ead5-43b6-9c3e-fd1630c92a7d.png)

### <a name="advanced-settings"></a>Avancerede indstillinger

Hvis du har brug for at oprette mere tilpassede DLP-politikker, kan du vælge **Brug avancerede indstillinger**.

De avancerede indstillinger giver dig regeleditoren, hvor du har fuld kontrol over alle mulige indstillinger, herunder antallet af forekomster og matchnøjagtigheden (tillidsniveau) for hver regel.

Hvis du hurtigt vil gå til en sektion, skal du klikke på et element i den øverste navigation i regeleditoren for at gå til det afsnit nedenfor.

![Øverste navigationsmenu i DLP-regeleditoren.](../media/c527b97f-ca53-4c79-ad19-1a63be8a8ecc.png)

## <a name="dlp-policy-templates"></a>DLP-politikskabeloner

Det første trin i oprettelsen af en DLP-politik er at vælge, hvilke oplysninger der skal beskyttes. Når du starter med en DLP-skabelon, gemmer du arbejdet med at oprette et nyt sæt regler fra bunden og finder ud af, hvilke typer oplysninger der som standard skal medtages. Du kan derefter føje til eller ændre disse krav for at finjustere reglen, så den opfylder organisationens specifikke krav.

En forudkonfigureret DLP-politikskabelon kan hjælpe dig med at registrere bestemte typer følsomme oplysninger, f.eks. HIPAA-data, PCI-DSS-data, Gramm-Leach-Bliley Act-data eller endda landestandardspecifikke personlige identificerbare oplysninger (P.I.). For at gøre det nemt for dig at finde og beskytte almindelige typer følsomme oplysninger indeholder de politikskabeloner, der er inkluderet i Microsoft 365 allerede de mest almindelige typer følsomme oplysninger, der er nødvendige for at komme i gang.

![Liste over skabeloner til politikker til forebyggelse af datatab med fokus på skabelon til U.S. Patriot Act.](../media/791b2403-430b-4987-8643-cc20abbd8148.png)

Din organisation kan også have sine egne specifikke krav, og i så fald kan du oprette en DLP-politik fra bunden ved at vælge indstillingen **Brugerdefineret politik** . En brugerdefineret politik er tom og indeholder ingen foruddefinerede regler.

<!-- ## Roll out DLP policies gradually with test mode

rehomed to Plan for DLP

When you create your DLP policies, you should consider rolling them out gradually to assess their impact and test their effectiveness before fully enforcing them. For example, you don't want a new DLP policy to unintentionally block access to thousands of documents that people require access to in order to get their work done.

If you're creating DLP policies with a large potential impact, we recommend following this sequence:

1. **Start in test mode without Policy Tips** and then use the DLP reports and any incident reports to assess the impact. You can use DLP reports to view the number, location, type, and severity of policy matches. Based on the results, you can fine tune the rules as needed. In test mode, DLP policies will not impact the productivity of people working in your organization.

2. **Move to Test mode with notifications and Policy Tips** so that you can begin to teach users about your compliance policies and prepare them for the rules that are going to be applied. At this stage, you can also ask users to report false positives so that you can further refine the rules.

3. **Start full enforcement on the policies** so that the actions in the rules are applied and the content's protected. Continue to monitor the DLP reports and any incident reports or notifications to make sure that the results are what you intend.

    ![Options for using test mode and turning on policy.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

    You can turn off a DLP policy at any time, which affects all rules in the policy. However, each rule can also be turned off individually by toggling its status in the rule editor.

    ![Options for turning off a rule in a policy.](../media/f7b258ff-1b8b-4127-b580-83c6492f2bef.png)

    You can also change the priority of multiple rules in a policy. To do that, open a policy for editing. In a row for a rule, choose the ellipses (**...**), and then choose an option, such as **Move down** or **Bring to last**.

    > [!div class="mx-imgBorder"]
    > ![Set rule priority.](../media/dlp-set-rule-priority.png)-->

## <a name="dlp-reports"></a>DLP-rapporter

Når du har oprettet og slået dine DLP-politikker til, skal du bekræfte, at de fungerer, som du havde tiltænkt, og hjælpe dig med at overholde angivne standarder. Med DLP-rapporter kan du hurtigt få vist antallet af DLP-politik- og regelforekomster over tid og antallet af falske positiver og tilsidesættelser. For hver rapport kan du filtrere disse match efter placering, tidsramme og endda indsnævre den til en bestemt politik, regel eller handling.

Med DLP-rapporterne kan du få forretningsindsigt og:

- Fokuser på specifikke tidsperioder, og forstå årsagerne til stigninger og tendenser.

- Find forretningsprocesser, der overtræder organisationens politikker for overholdelse af angivne standarder.

- Forstå alle forretningsmæssige konsekvenser af DLP-politikkerne.

Derudover kan du bruge DLP-rapporter til at finjustere dine DLP-politikker, når du kører dem.

![Rapportdashboard i Security and Compliance Center.](../media/6d741252-a0ce-4429-95ba-6c857ecc9a7e.png)

## <a name="how-dlp-policies-work"></a>Sådan fungerer DLP-politikker

DLP registrerer følsomme oplysninger ved hjælp af detaljeret indholdsanalyse (ikke kun en simpel tekstscanning). Denne omfattende indholdsanalyse bruger nøgleordsforekomster, ordbogsforekomster, evaluering af regulære udtryk, interne funktioner og andre metoder til at registrere indhold, der stemmer overens med dine DLP-politikker. Det kan være, at det kun er en lille procentdel af dine data, der betragtes som følsomme. En DLP-politik kan identificere, overvåge og automatisk beskytte netop disse data uden at hindre eller påvirke personer, der arbejder med resten af dit indhold.

### <a name="policies-are-synced"></a>Politikker synkroniseres

Når du har oprettet en DLP-politik på Microsoft Purview-overholdelsesportalen, gemmes den i et centralt politiklager og synkroniseres derefter med de forskellige indholdskilder, herunder:

- Exchange Online, og derfra til Outlook på internettet og Outlook.

- OneDrive for Business websteder.

- SharePoint onlinewebsteder.

- Office skrivebordsprogrammer (Excel, PowerPoint og Word).

- Microsoft Teams kanaler og chatbeskeder.

Når politikken er synkroniseret til de rigtige placeringer, begynder den at evaluere indhold og gennemtvinge handlinger.
<!-- what is the time delay for first deployment of a policy and what is the sync schedule? -->

### <a name="policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites"></a>Politikevaluering på OneDrive for Business- og SharePoint Online-websteder

På tværs af alle dine SharePoint Online-websteder og OneDrive for Business-websteder ændres dokumenter konstant – de oprettes hele tiden, redigeres, deles osv. Det betyder, at dokumenter når som helst kan være i konflikt med eller overholde en DLP-politik. En person kan f.eks. uploade et dokument, der ikke indeholder følsomme oplysninger til teamwebstedet, men senere kan en anden person redigere det samme dokument og føje følsomme oplysninger til det.

Derfor kontrollerer DLP-politikker ofte dokumenter for politikforekomster i baggrunden. Du kan betragte dette som asynkron politikevaluering.
<!-- what is the frequency? looks like it is tied to the search crawl schedule -->

#### <a name="how-it-works"></a>Sådan fungerer det

Når personer tilføjer eller ændrer dokumenter på deres websteder, scanner søgemaskinen indholdet, så du kan søge efter det senere. Mens dette sker, scannes indholdet også for følsomme oplysninger og for at kontrollere, om det er delt. Alle følsomme oplysninger, der findes, gemmes sikkert i søgeindekset, så det kun er overholdelsesteamet, der kan få adgang til dem, men ikke typiske brugere. Hver DLP-politik, du har slået til kørsler i baggrunden (asynkront), kontrollerer ofte efter indhold, der stemmer overens med en politik, og anvender handlinger for at beskytte den mod utilsigtede lækager.

![Diagram, der viser, hvordan DLP-politik evaluerer indhold asynkront.](../media/bdf73099-039a-4909-ae89-ac12c41992ba.png)

<!-- conflict with a DLP policy is bad wording -->
Endelig kan dokumenter være i konflikt med en DLP-politik, men de kan også blive kompatible med en DLP-politik. Hvis en person f.eks. føjer kreditkortnumre til et dokument, kan det medføre, at en DLP-politik blokerer adgangen til dokumentet automatisk. Men hvis personen senere fjerner de følsomme oplysninger, fortrydes handlingen (i dette tilfælde blokering) automatisk, næste gang dokumentet evalueres i forhold til politikken.

DLP evaluerer alt indhold, der kan indekseres. Du kan finde flere oplysninger om, hvilke filtyper der gennemsøges som standard, [under Standardfilnavneudvidelser og fortolkede filtyper i SharePoint Server](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types).

> [!NOTE]
> For at forhindre, at dokumenter deles, før DLP-politikker havde mulighed for at analysere dem, kan deling af nye filer i SharePoint blokeres, indtil indholdet er blevet indekseret. Se [Markér nye filer som følsomme som standard](/sharepoint/sensitive-by-default) for at få detaljerede oplysninger.

### <a name="policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web"></a>Politikevaluering i Exchange Online, Outlook og Outlook på internettet

Når du opretter en DLP-politik, der indeholder Exchange Online som en placering, synkroniseres politikken fra Microsoft Purview-overholdelsesportalen til Exchange Online og derefter fra Exchange Online til Outlook på internettet og Outlook.

Når en meddelelse sammensættes i Outlook, kan brugeren se politiktips, da det indhold, der oprettes, evalueres i forhold til DLP-politikker. Og når en meddelelse er sendt, evalueres den i forhold til DLP-politikker som en normal del af mailflowet sammen med Exchange regler for mailflow (også kendt som transportregler) og DLP-politikker, der er oprettet i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>. DLP-politikker scanner både meddelelsen og eventuelle vedhæftede filer.

### <a name="policy-evaluation-in-the-office-desktop-programs"></a>Politikevaluering i Office desktopprogrammer

<!-- same capability to identify sensitive information line conflates sensitive information types and such -->
Excel, PowerPoint og Word indeholder samme funktionalitet til at identificere følsomme oplysninger og anvende DLP-politikker som SharePoint Online og OneDrive for Business. Disse Office programmer synkroniserer deres DLP-politikker direkte fra det centrale politiklager og evaluerer derefter løbende indholdet i forhold til DLP-politikkerne, når personer arbejder med dokumenter, der er åbnet fra et websted, der er inkluderet i en DLP-politik.

DLP-politikevaluering i Office er designet til ikke at påvirke programmernes ydeevne eller produktiviteten hos personer, der arbejder med indhold. Hvis brugeren arbejder på et stort dokument, eller hvis brugerens computer er optaget, kan det tage et par sekunder, før et politiktip vises.

### <a name="policy-evaluation-in-microsoft-teams"></a>Politikevaluering i Microsoft Teams
 <!--what do you mean that it's synched to user accounts?  I thought DLP policies were applied to locations not users like sensitivity labels are  -->

Når du opretter en DLP-politik, der indeholder Microsoft Teams som en placering, synkroniseres politikken fra Microsoft Purview-overholdelsesportalen til brugerkonti og Microsoft Teams kanaler og chatbeskeder. Afhængigt af hvordan DLP-politikker konfigureres, kan meddelelsen blive blokeret eller tilbagekaldt, når nogen forsøger at dele følsomme oplysninger i en Microsoft Teams chat- eller kanalmeddelelse. Og dokumenter, der indeholder følsomme oplysninger, og som deles med gæster (eksterne brugere), åbnes ikke for disse brugere. Du kan få mere at vide under [Forebyggelse af datatab og Microsoft Teams](dlp-microsoft-teams.md).

## <a name="permissions"></a>Tilladelser

Globale administratorer, sikkerhedsadministratorer og administratorer af overholdelse har som standard adgang til at oprette og anvende en DLP-politik. Andre medlemmer af dit overholdelsesteam, der skal oprette DLP-politikker, skal have tilladelser til Microsoft Purview-overholdelsesportalen. Din lejeradministrator har som standard adgang til denne placering og kan give overholdelsesansvarlige og andre personer adgang til Microsoft Purview-overholdelsesportalen uden at give dem alle tilladelserne for en lejeradministrator. For at gøre dette anbefaler vi, at du:

1. Opret en gruppe i Microsoft 365, og føj overholdelsesansvarlige til den.

2. Opret en rollegruppe på siden **Tilladelser** på Microsoft Purview-overholdelsesportalen.

3. Når du opretter rollegruppen, skal du bruge afsnittet **Vælg roller** til at føje følgende rolle til rollegruppen: **Administration af DLP-overholdelse**.

4. Brug afsnittet **Vælg medlemmer** til at føje den Microsoft 365 gruppe, du oprettede før, til rollegruppen.

Du kan også oprette en rollegruppe med skrivebeskyttede rettigheder til DLP-politikker og DLP-rapporter ved at tildele rollen **Vis kun DLP-overholdelsesstyring** .

Du kan få flere oplysninger under [Giv brugere adgang til Office 365 Compliance Center](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).

Disse tilladelser kræves kun for at oprette og anvende en DLP-politik. Gennemtvingelse af politik kræver ikke adgang til indholdet.

## <a name="find-the-dlp-cmdlets"></a>Find DLP-cmdlet'erne

Hvis du vil bruge de fleste cmdlet'er til Microsoft Purview-overholdelsesportalen, skal du gøre følgende:

1. [Forbind til PowerShell til sikkerhed & overholdelse af angivne standarder](/powershell/exchange/connect-to-scc-powershell).

2. Brug en af disse [policy-and-compliance-dlp-cmdlet'er](/powershell/module/exchange/export-dlppolicycollection).

DLP-rapporter skal dog hente data fra hele Microsoft 365, herunder Exchange Online. Derfor ***er cmdlet'erne til DLP-rapporterne tilgængelige i Exchange Online Powershell – ikke i Powershell på Microsoft Purview-overholdelsesportalen***. Hvis du vil bruge cmdlet'erne til DLP-rapporterne, skal du derfor:

1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Brug en af disse cmdlet'er til DLP-rapporter:

    - [Get-DlpDetectionsReport](/powershell/module/exchange/Get-DlpDetectionsReport)

    - [Get-DlpDetailReport](/powershell/module/exchange/Get-DlpDetailReport)

## <a name="more-information"></a>Flere oplysninger

- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)

- [Send meddelelser, og vis politiktip til DLP-politikker](use-notifications-and-policy-tips.md)

- [Opret en DLP-politik for at beskytte dokumenter med FCI eller andre egenskaber](protect-documents-that-have-fci-or-other-properties.md)

- [Hvad inkluderes i DLP-politikskabelonerne](what-the-dlp-policy-templates-include.md)

- [Enhedsdefinitioner for type af følsomme oplysninger](sensitive-information-type-entity-definitions.md)

- [Funktioner for type af følsomme oplysninger](sit-functions.md)

- [Opret en brugerdefineret type følsomme oplysninger](create-a-custom-sensitive-information-type.md)
