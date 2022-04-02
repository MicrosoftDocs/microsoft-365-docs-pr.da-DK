---
title: Forøg trusselsbeskyttelse til Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
- admindeeplinkMAC
- admindeeplinkEXCHANGE
- admindeeplinkSPO
search.appverid:
- BCS160
- MET150
description: Få hjælp til at øge beskyttelsesniveauet i Microsoft 365 Business Premium
ms.openlocfilehash: c6533b966587235b8f29c1ce53bd9d5579b23b9c
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403803"
---
# <a name="increase-threat-protection-for-microsoft-365-business-premium"></a>Forøg trusselsbeskyttelse til Microsoft 365 Business Premium

I dette mål øger du trusselsbeskyttelsen med Microsoft 365 Business Premium. Det er vigtigt at beskytte organisationen mod phishing, malware og andre trusler. Disse anbefalinger er især relevante for politiske kampagner, advokatkontorer og sundhedspleje, som har et øget behov for sikkerhed.

## <a name="start-with-secure-score"></a>Start med Secure Score

Microsoft Secure Score analyserer din organisations sikkerhed baseret på dine almindelige aktiviteter og sikkerhedsindstillinger og tildeler en score. Vær opmærksom på dit aktuelle resultat, og tag derefter de anbefalede handlinger i denne artikel for at øge din score. Målet er altid at være opmærksom på det og prøve at forbedre dine resultater.

Du kan finde flere oplysninger [i Microsoft Secure Score](../security/defender/microsoft-secure-score.md).

## <a name="review-and-apply-preset-security-policies"></a>Gennemse og anvende forudindstillede sikkerhedspolitikker

Dit abonnement omfatter [foruddefinerede sikkerhedspolitikker](../security/office-365-security/preset-security-policies.md) , der bruger anbefalede indstillinger til beskyttelse mod uønsket post, antimalware og phishing. Som standard er indbygget beskyttelse aktiveret. kan du overveje at anvende standard eller restriktiv beskyttelse for at øge sikkerheden. 

Forudindstillede sikkerhedspolitikker består af:

- Profiler, der bestemmer beskyttelsesniveauet
- Politikker (f.eks. antispam, antimalware, antiphishing, Pengeskab vedhæftede filer og Pengeskab links)
- Politikindstillinger (f.eks. grupper, brugere eller domæner til at modtage politikker og eventuelle undtagelser)

Følgende tabel opsummerer niveauerne for beskyttelse og foruddefinerede politiktyper.

| Beskyttelsesniveau | Beskrivelse |
|:---|:---|
| **Standardbeskyttelse** <br/>(*anbefales til de fleste virksomheder*) | Standardbeskyttelse bruger en grundlinjeprofil, der er egnet til de fleste brugere <br/><br/>Den indeholder antispam, antimalware, antiphishing, spoof-indstillinger, indstillinger for efterligning, Pengeskab links og Pengeskab politikker for vedhæftede filer.  |
| **Restriktiv beskyttelse**  | Restriktiv beskyttelse omfatter de samme typer af politikker som standardbeskyttelse, men med strengere indstillinger. Hvis din virksomhed skal opfylde yderligere sikkerhedskrav eller -bestemmelser, skal du overveje at anvende streng beskyttelse af dine foretrukne brugere eller mål med høj værdi. |
| **Indbygget beskyttelse** | Beskytter mod skadelige links og vedhæftede filer i mails. Aktiveret og anvendt på alle brugere som standard.  |

Du kan angive, hvilke brugere, grupper og domæner, der skal modtage foruddefinerede politikker, og du kan definere bestemte undtagelser, men du kan ikke ændre foruddefinerede politikker.

Du kan også oprette dine egne sikkerhedspolitikker til brugerdefinerede indstillinger, der passer til din virksomheds behov.




<!--https://docs.microsoft.com/en-us/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365?view=o365-worldwide


## Raise the level of protection against malware in mail

Your Office 365 or Microsoft 365 environment includes protection against malware, but you can increase this protection by blocking attachments with file types that are commonly used for malware. To bump up malware protection in email:

1. Go to the <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Office 365 Security & Compliance Center</a> and sign in with your admin account credentials.

2. In the left navigation pane, under **Threat management**, choose **Policy** \> **Anti-Malware**.

3. Double-click the default policy to edit this company-wide policy.

4. Click **Settings**.

5. Under **Common Attachment Types Filter**, select **On**. The file types that are blocked are listed in the window directly below this control. Make sure you add these filetypes:

   `ade, adp, ani, bas, bat, chm, cmd, com, cpl, crt, hlp, ht, hta, inf, ins, isp, job, js, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, exe, pif`

   You can add or delete file types later, if needed.

6. Click **Save.**

For more information, see [Anti-malware protection in EOP](../security/office-365-security/anti-malware-protection.md).

## Protect against ransomware

Ransomware restricts access to data by encrypting files or locking computer screens. It then attempts to extort money from victims by asking for "ransom," usually in the form of cryptocurrencies like Bitcoin, in exchange for access to data.

You can protect against ransomware by creating one or more mail flow rules to block file extensions that are commonly used for ransomware (these were added in the [raise the level of protection against malware in mail](#raise-the-level-of-protection-against-malware-in-mail) step), or to warn users who receive these attachments in email.

In addition to the files that you blocked in the previous step, it's also good practice to create a rule to warn users before opening Office file attachments that include macros. Ransomware can be hidden inside macros, so warn users to not open these files from people they don't know.

To create a mail transport rule:

1. Go to the admin center at <https://admin.microsoft.com> and choose **Admin centers** \> **Exchange**.

2. In the **mail flow** category, click **rules**.

3. Click **+**, and then click **Create a new rule**.

4. Click **More options** at the bottom of the dialog box to see the full set of options.

5. Apply the settings in the following table for the rule. Leave the rest of the settings at the default, unless you want to change them.

6. Click **Save**.

|Setting|Warn users before opening attachments of Office files|
|---|---|
|Name|Anti-ransomware rule: warn users|
|Apply this rule if . . .|Any attachment . . . file extension matches . . .|
|Specify words or phrases|Add these file types: <br/> `dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm`|
|Do the following . . .|Notify the recipient with a message|
|Provide message text|Do not open these types of files from people you do not know because they might contain macros with malicious code.|

For more information, see:

- [Ransomware: how to reduce risk](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [Restore your OneDrive](https://support.microsoft.com//office/fa231298-759d-41cf-bcd0-25ac53eb8a15)

## Stop auto-forwarding for email

Hackers who gain access to a user's mailbox can steal your mail by setting the mailbox to automatically forward email. This can happen even without the user's awareness. You can prevent this from happening by configuring a mail flow rule.

To create a mail transport rule, either watch [this short video](https://support.office.com/article/f9d693ba-5c78-47c0-b156-8e461e062aa7) or follow these steps:

1. In the <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 admin center</a>, click **Admin centers** \> **Exchange**.

2. In the **mail flow** category, click **rules**.

3. Click **+**, and then click **Create a new rule**.

4. Click **More options** at the bottom of the dialog box to see the full set of options.

5. Apply the settings in the following table. Leave the rest of the settings at the default, unless you want to change them.

6. Click **Save**.

|Setting|Warn users before opening attachments of Office files|
|---|---|
|Name|Prevent auto forwarding of email to external domains|
|Apply this rule if ...|The sender . . . is external/internal . . . Inside the organization|
|Add condition|The message properties . . . include the message type . . . Auto-forward|
|Do the following ...|Block the message . . . reject the message and include an explanation.|
|Provide message text|Auto-forwarding email outside this organization is prevented for security reasons.|

## Protect your email from phishing attacks

If you've configured one or more custom domains for your Office 365 or Microsoft 365 environment, you can configure targeted anti-phishing protection. Anti-phishing protection, part of Microsoft Defender for Office 365, can help protect your organization from malicious impersonation-based phishing attacks and other phishing attacks. If you haven't configured a custom domain, you don't need to do this.

We recommend that you get started with this protection by creating a policy to protect your most important users and your custom domain.

To create an anti-phishing policy in Defender for Office 365, watch [this short training video](https://support.office.com/article/86c425e1-1686-430a-9151-f7176cce4f2c), or complete the following steps:

1. Go to <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Office 365 Security & Compliance Center</a>.

2. In the left navigation pane, under **Threat management**, choose **Policy**.

3. On the **Policy** page, choose **Anti-phishing**.

4. On the **Anti-phishing** page, select **+ Create**. A wizard launches that steps you through defining your anti-phishing policy.

5. Specify the name, description, and settings for your policy as recommended in the chart below. For more information, see [Learn about anti-phishing policy in Microsoft Defender for Office 365 options](../security/office-365-security/set-up-anti-phishing-policies.md).

6. After you've reviewed your settings, choose **Create this policy** or **Save**, as appropriate.

|Setting or option|Recommended setting|
|---|---|
|Name|Domain and most valuable staff|
|Description|Ensure most important staff and our domain are not being impersonated.|
|Add users to protect|Select **+ Add a condition, The recipient is**. Type user names or enter the email address of the business owners, partners, or candidate, managers, and other important staff members. You can add up to 20 internal and external addresses that you want to protect from impersonation.|
|Add domains to protect|Select **+ Add a condition, The recipient domain is**. Enter the custom domain associated with your Microsoft 365 subscription, if you defined one. You can enter more than one domain.|
|Choose actions|If email is sent by an impersonated user: Choose **Redirect message to another email address**, and then type the email address of the security administrator; for example, *Alice<span><span>@contoso.com*. <br/> If email is sent by an impersonated domain: Choose **Quarantine message**.|
|Mailbox intelligence|By default, mailbox intelligence is selected when you create a new anti-phishing policy. Leave this setting **On** for best results.|
|Add trusted senders and domains|Here you can add your own domain, or any other trusted domains.|
|Applied to|Select **The recipient domain is**. Under **Any of these**, select **Choose**. Select **+ Add**. Select the check box next to the name of the domain, for example, *contoso.<span><span>com*, in the list, and then select **Add**. Select **Done**.|

For more information, see [Set up anti-phishing policies in Defender for Office 365](../security/office-365-security/set-up-anti-phishing-policies.md).

## Protect against malicious attachments, files, and links with Defender for Office 365

![Banner that point to https://aka.ms/aboutM365preview.](../media/m365admincenterchanging.png)

First, make sure, in the admin center at <https://admin.microsoft.com> that you have the new admin center preview turned on. Turn on the toggle next to the text **The new admin center**.

   ![The new admin center preview on.](../media/previewon.png)

If you don't see the **Setup** page with cards in your tenant yet, see how to complete these steps in Security & Compliance Center. See [Set up Safe Attachments in the Security & Compliance Center](#set-up-safe-attachments-in-the-security--compliance-center) and [Set up Safe Links in the Security & Compliance Center](#set-up-safe-links-in-the-security--compliance-center).

1. In the left nav, choose **Setup**.
2. On the **Setup** page, choose **View** on the **Increase protection from advanced threats** card.

   ![Choose View on the Increase protection from advanced threats.](../media/startatp.png)

3. On the **Increase protection from advanced threats** page, choose **Get started**.
4. On the pane that opens, select the check boxes next to **Links and attachments in email**, **Scan files in SharePoint, OneDrive, and Teams**, and **Scan links in Office desktop and Office Online apps** under **Scan items for malicious content**.
    
   Under **Links and attachments in email**, Type in All Users, or the specific users whose email you want scanned.

   ![Select all check boxes in Increase protection from advanced threats.](../media/setatp.png)

5. Choose **Create policies** to turn on Safe Attachments and Safe Links.

### Set up Safe Attachments in the Security & Compliance Center

People regularly send, receive, and share attachments, such as documents, presentations, spreadsheets, and more. It's not always easy to tell whether an attachment is safe or malicious just by looking at an email message. Microsoft Defender for Office 365 includes Safe Attachment protection, but this protection is not turned on by default. We recommend that you create a new rule to begin using this protection. This protection extends to files in SharePoint, OneDrive, and Microsoft Teams.

To create a Safe Attachment policy, either watch [this short video](https://support.office.com/article/e7e68934-23dc-4b9c-b714-e82e27a8f8a5), or complete the following steps:

1. Go to <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Office 365 Security & Compliance Center</a> and sign in with your admin account.

2. In the left navigation pane, under **Threat management**, choose **Policy**.

3. On the Policy page, choose **Safe Attachments**.

4. On the Safe attachments page, apply this protection broadly by selecting the **Turn on ATP for SharePoint, OneDrive, and Microsoft Teams** check box.

5. Select **+** to create a new policy.

6. Apply the settings in the following table.

7. After you review your settings, choose **Create this policy** or **Save**, as appropriate.

|Setting or option|Recommended setting|
|---|---|
|Name|Block current and future emails with detected malware.|
|Description|Block current and future emails and attachments with detected malware.|
|Save attachments unknown malware response|Select **Block - Block the current and future emails and attachments with detected malware**.|
|Redirect attachment on detection|Enable redirection (select this box) <br/> Enter the admin account or a mailbox setup for quarantine. <br/> Apply the above selection if malware scanning for attachments times out or error occurs (select this box).|
|Applied to|The recipient domain is . . . select your domain.|

For more information, see [Set up anti-phishing policies in Defender for Office 365](../security/office-365-security/set-up-anti-phishing-policies.md).

### Set up Safe Links in the Security & Compliance Center

Hackers sometimes hide malicious websites in links in email or other files. Safe Links, part of Microsoft Defender for Office 365, can help protect your organization by providing time-of-click verification of web addresses (URLs) in email messages and Office documents. Protection is defined through Safe Links policies.

We recommend that you do the following:

- Modify the default policy to increase protection.

- Add a new policy targeted to all recipients in your domain.

To set up Safe Links, watch [this short training video](https://support.office.com/article/61492713-53c2-47da-a6e7-fa97479e97fa), or complete the following steps:

1. Go to <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Office 365 Security & Compliance Center</a> and sign in with your admin account.

2. In the left navigation pane, under **Threat management**, choose **Policy**.

3. On the Policy page, choose **Safe Links**.

To modify the default policy:

1. On the Safe links page, under **Policies that apply to the entire organization**, select the **Default** policy.

2. Under **Settings that apply to content except email**, select **Microsoft 365 Apps for enterprise, Office for iOS and Android**.

3. Click **Save**.

To create a new policy targeted to all recipients in your domain:

1. On the Safe links page, under **Policies that apply to the entire organization**, click **+** to create a new policy.

2. Apply the settings listed in the following table.

3. Click **Save**.

|Setting or option|Recommended setting|
|---|---|
|Name|Safe links policy for all recipients in the domain|
|Select the action for unknown potentially malicious URLs in messages|Select **On - URLs will be rewritten and checked against a list of known malicious links when user clicks on the link**.|
|Use Safe Attachments to scan downloadable content|Select this box.|
|Applied to|The recipient domain is . . . select your domain.|

For more information, see [Safe Links in Defender for Office 365](../security/office-365-security/safe-links.md).

-->

## <a name="turn-on-the-unified-audit-log"></a>Aktivere den samlede overvågningslog

Når du har aktiveret søgning i overvågningsloggen i Security & Compliance Center, kan du bevare administratoraktiviteten og anden brugeraktivitet i logfilen og søge i den.

Du skal være tildelt rollen Overvågningslogfiler Exchange Online at slå søgning i overvågningslog til eller fra i dit Microsoft 365 abonnement. Denne rolle er som standard tildelt rollegrupperne Styring af overholdelse og Organisationsadministration på siden Tilladelser <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration</a>. Globale administratorer i Microsoft 365 er som standard medlemmer af denne gruppe.

1. Hvis du vil aktivere søgning i overvågningsloggen <https://admin.microsoft.com> , skal du gå til Administration på og derefter vælge **Sikkerhed** under **Administrationer** i venstre navigationslinje.
2. På siden **Microsoft 365 Sikkerhed** skal du vælge Flere ressourcer og derefter åbn på kortet **Office 365 Security & Compliance Center**.

    ![Vælg Åbn i sikkerheds- & kompatibilitetsbiler.](../media/gotosecandcomp.png)
3. På siden sikkerhed og overholdelse af regler og standarder skal du **vælge Søg** og derefter **Søgning i overvågningslogfil**.
4. Øverst på siden Søgning **i overvågningslog** skal du **vælge Aktiver overvågning**.

Når funktionen er slået til, kan du søge efter filer, mapper og mange aktiviteter. Du kan få mere at vide [under Søg i overvågningsloggen](../compliance/search-the-audit-log-in-security-and-compliance.md).

## <a name="tune-up-anonymous-sharing-settings-for-sharepoint-and-onedrive-files-and-folders"></a>Finjustere anonyme indstillinger for deling SharePoint og OneDrive filer og mapper

(skift standard anonymt link udløb til 14 dage, skift standarddelingstype til "Bestemte personer") Sådan ændres indstillingerne for deling OneDrive og SharePoint:

1. Gå til Administration på, <https://admin.microsoft.com> og vælg derefter **SharePoint** under **Administration i** venstre navigationslinje.
2. I administration SharePoint skal du gå til **Deling af** \> <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**politikker**</a>.
3. På siden **Deling** **under** Fil- og mappelinks skal du vælge Bestemte **personer, og** under Avancerede indstillinger **for links til "Alle" skal** du vælge Disse **links** skal udløbe inden for dette antal dage og skrive 14 (eller et andet antal dage, du vil begrænse linkets levetid til).

   ![Vælg Bestemte personer, og angiv udløbslink til 14 dage.](../media/anyonelinks.png)


## <a name="activity-alerts"></a>Aktivitetsbeskeder

Du kan bruge aktivitetsbeskeder til at spore administrator- og brugeraktiviteter og registrere hændelser til forebyggelse af malware og datatab i organisationen. Dit abonnement omfatter et sæt standardpolitikker, men du kan også oprette brugerdefinerede politikker. Du kan finde flere oplysninger i [politikker for beskeder](../compliance/alert-policies.md). Hvis du f.eks. gemmer en vigtig fil i SharePoint som du ikke vil have nogen til at dele eksternt, kan du oprette en meddelelse, der giver dig besked, hvis nogen deler den.

I følgende figur vises de standardpolitikker, der er inkluderet Microsoft 365.

![Standardbeskedpolitikker, der er inkluderet Microsoft 365.](../media/alertpolicies.png)

## <a name="disable-or-manage-calendar-sharing"></a>Deaktiver eller administrer kalenderdeling

Du kan forhindre personer i din organisation i at dele deres kalendere, eller du kan også administrere, hvad de kan dele. Du kan f.eks. begrænse deling til kun at være ledig/optaget.

1. Gå til Administration på , og <https://admin.microsoft.com> vælg **Indstillinger** \> **Org Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**Services**</a>.

1. Vælg **Kalender**, og vælg, om personer i organisationen kan dele deres kalendere med personer uden for organisationen Office 365 har Exchange kalendere eller med andre.

   Hvis du vælger indstillingen Del med alle, kan du vælge kun at dele oplysninger om ledig/optaget tid.

3. Vælg **Gem** ændringer nederst på siden.

   I følgende figur vises kalenderdeling, som ikke er tilladt.

   ![Skærmbillede af visning af ekstern kalenderdeling som ikke tilladt.](../media/nocalendarsharing.png)

   Følgende figur viser indstillingerne, når kalenderdeling er tilladt med et maillink kun med oplysninger om ledig/optaget tid.

   ![Skærmbillede af kalender, hvor ledig/optaget er delt med alle.](../media/sharefreebusy.png)

Hvis brugerne har tilladelse til at dele deres kalendere, skal du [se denne vejledning](https://support.office.com/article/7ecef8ae-139c-40d9-bae2-a23977ee58d5) til, hvordan du deler fra Outlook på internettet.

