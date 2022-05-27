---
title: Opret en DLP-politik ud fra en skabelon
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.NewPolicyFromTemplate
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ms.custom:
- seo-marvel-mar2020
- admindeeplinkCOMPLIANCE
description: I denne artikel får du mere at vide om, hvordan du opretter DLP-politikker ved hjælp af en af de skabeloner, der er inkluderet i Office 365.
ms.openlocfilehash: 952a552210b00061717c24db5de5e5a47b84d72b
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754670"
---
# <a name="create-a-dlp-policy-from-a-template"></a>Opret en DLP-politik ud fra en skabelon

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Den nemmeste og mest almindelige måde at komme i gang med DLP-politikker på er at bruge en af de skabeloner, der er inkluderet i Microsoft Purview-compliance-portal. Du kan bruge en af disse skabeloner, som den er, eller tilpasse reglerne, så de opfylder organisationens specifikke krav til overholdelse af angivne standarder.

Microsoft 365 indeholder over 40 brugsklare skabeloner, der kan hjælpe dig med at opfylde en lang række almindelige lovgivnings- og forretningspolitiske behov. Se; [Politikskabeloner](dlp-policy-reference.md#policy-templates) for en komplet liste. 

Du kan finjustere en skabelon ved at ændre en af dens eksisterende regler eller tilføje nye. Du kan f.eks. føje nye typer følsomme oplysninger til en regel, ændre antallet i en regel for at gøre det sværere eller nemmere at udløse, give personer tilladelse til at tilsidesætte handlingerne i en regel ved at angive en forretningsberettigelse eller ændre, hvem meddelelser og hændelsesrapporter sendes til. En DLP-politikskabelon er et fleksibelt udgangspunkt for mange almindelige scenarier for overholdelse af angivne standarder.

Du kan også vælge den brugerdefinerede skabelon, som ikke har nogen standardregler, og konfigurere din DLP-politik fra bunden for at opfylde de specifikke krav til overholdelse af angivne standarder for din organisation.

## <a name="permissions"></a>Tilladelser

Medlemmer af dit overholdelsesteam, der skal oprette DLP-politikker, skal have tilladelser til Overholdelsescenter. Som standard kan din lejeradministrator få adgang til at give overholdelsesansvarlige og andre personer adgang. Følg disse trin:
  
1. Opret en gruppe i Microsoft 365, og føj overholdelsesansvarlige til den.
    
2. Opret en rollegruppe på siden **Tilladelser** i Microsoft Purview-compliance-portal. 

3. Når du opretter rollegruppen, skal du bruge afsnittet **Vælg roller** til at føje følgende rolle til rollegruppen: **DLP Compliance Management**.
    
4. Brug afsnittet **Vælg medlemmer** til at føje den Microsoft 365 gruppe, du oprettede før, til rollegruppen.

Brug rollen **Vis kun DLP-overholdelsesstyring** til at oprette en rollegruppe med skrivebeskyttede rettigheder til DLP-politikker og DLP-rapporter.

Du kan få flere oplysninger [under Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#permissions-in-the-microsoft-purview-compliance-portal).
  
Disse tilladelser kræves for at oprette og anvende en DLP-politik for ikke at gennemtvinge politikker.

### <a name="roles-and-role-groups-in-preview"></a>Roller og rollegrupper som prøveversion

Der er roller og rollegrupper som prøveversion, som du kan teste for at finjustere dine adgangskontrolelementer.

Her er en liste over relevante roller, der findes som prøveversion. Du kan få mere at vide om dem [under Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#permissions-in-the-microsoft-purview-compliance-portal).

- Information Protection Administration
- Information Protection analytiker
- Information Protection investigator
- Information Protection-læser

Her er en liste over relevante rollegrupper, der findes som prøveversion. Du kan få mere at vide om under [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#permissions-in-the-microsoft-purview-compliance-portal)

- Information Protection
- Information Protection administratorer
- Information Protection analytikere
- Information Protection efterforskere
- Information Protection læsere

### <a name="create-the-dlp-policy-from-a-template"></a>Opret DLP-politikken ud fra en skabelon

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a>.

2. I den Microsoft Purview-compliance-portal \> venstre navigationsrude \> **Løsninger** \> **Politikker til** \> **forebyggelse af** \> datatab **+ Opret politik**.

    ![Opret en politikknap.](../media/b1e48a08-92e2-47ca-abdc-4341694ddc7c.png)
          
3. Vælg den DLP-politikskabelon, der beskytter de typer følsomme oplysninger, du skal bruge \> **Næste**.

4. Navngiv politikken \> **Næste**.
 
<!--In this example, you'll select **Privacy** \> **U.S. Personally Identifiable Information (PII) Data** because it already includes most of the types of sensitive information that you want to protect - you'll add a couple later.

    When you select a template, you can read the description on the right to learn what types of sensitive information the template protects.

    ![Page for choosing a DLP policy template.](../media/775266f6-ad87-4080-8d7c-97f2e7403b30.png)-->

5. Hvis du vil vælge de placeringer, som DLP-politikken skal beskytte, skal du enten acceptere standardområdet for hver placering eller tilpasse området. Se [Placeringer](dlp-policy-reference.md#locations) for indstillinger for område.

6. Vælg \> **Næste**.
 
1. Gør et af følgende:

   - Vælg **Alle placeringer i Office 365** \> **Næste**.
   - Vælg **Lad mig vælge bestemte placeringer** \> **Næste**. I dette eksempel skal du vælge dette.

   Hvis du vil medtage eller udelade en hel placering, f.eks. alle Exchange mail eller alle OneDrive konti, skal du slå **Status** for den pågældende placering til eller fra.

   Hvis du kun vil medtage bestemte SharePoint websteder eller OneDrive for Business konti, skal du skifte **status** til til og derefter klikke på linkene under **Medtag** for at vælge bestemte websteder eller konti. Når du anvender en politik på et websted, anvendes de regler, der er konfigureret i den pågældende politik, automatisk på alle underordnede websteder på det pågældende websted.

   ![Indstillinger for placeringer, hvor en DLP-politik kan anvendes.](../media/all-locations.png)

   I dette eksempel skal du deaktivere **Status** for både **Exchange mail**- og **SharePoint-websteder** for at beskytte følsomme oplysninger, der er gemt på alle OneDrive for Business konti, og lade **Status** være aktiveret for **OneDrive konti**.

7. Vælg **Gennemse, og tilpas standardindstillingerne i skabelonen** \> **Næste**.

8. En DLP-politikskabelon indeholder foruddefinerede regler med betingelser og handlinger, der registrerer og reagerer på bestemte typer følsomme oplysninger. Du kan redigere, slette eller deaktivere en af de eksisterende regler eller tilføje nye. Klik på **Næste**, når du er færdig.

    ![Regler udvidet i den amerikanske pii-politikskabelon.](../media/3bc9f1b6-f8ad-4334-863a-24448bb87687.png)

9. Vælg at registrere, hvornår dette indhold deles i din organisation eller uden for organisationen, hvis du har valgt en af disse placeringer:
    1. Exchange
    1. SharePoint
    1. OneDrive
    1. Teams chat- og kanalmeddelelser 

10. Vælg **Næste**.

11. Hvis du vil, kan du tilpasse meddelelser om politiktip og meddelelsesmails på siden **Beskyttelseshandlinger** . Aktivér **Når indhold stemmer overens med politikbetingelserne, skal du vise politiktip til brugerne og sende dem en mail** og derefter vælge **Tilpas tip og mail**.
12. Vælg **Næste**.


<!--    In this example, the U.S. PII Data template includes two predefined rules:

   - **Low volume of content detected U.S. PII** This rule looks for files containing between 1 and 10 occurrences of each of three types of sensitive information (ITIN, SSN, and U.S. passport numbers), where the files are shared with people outside the organization. If found, the rule sends an email notification to the primary site collection administrator, document owner, and person who last modified the document.

   - **High volume of content detected U.S. PII** This rule looks for files containing 10 or more occurrences of each of the same three sensitive information types, where the files are shared with people outside the organization. If found, this action also sends an email notification, plus it restricts access to the file. For content in a OneDrive for Business account, this means that permissions for the document are restricted for everyone except the primary site collection administrator, document owner, and person who last modified the document.

    To meet your organization's specific requirements, you may want to make the rules easier to trigger, so that a single occurrence of sensitive information is enough to block access for external users. After looking at these rules, you understand that you don't need low and high count rules—you need only a single rule that blocks access if any occurrence of sensitive information is found.

    So you expand the rule named **Low volume of content detected U.S. PII** \> **Delete rule**.

    ![Delete rule button.](../media/bc36f7d2-0fae-4af1-92e8-95ba51077b12.png)

9. Now, in this example, you need to add two sensitive information types (U.S. bank account numbers and U.S. driver's license numbers), allow people to override a rule, and change the count to any occurrence. You can do all of this by editing one rule, so select **High volume of content detected U.S. PII** \> **Edit rule**.

    ![Edit rule button.](../media/eaf54067-4945-4c98-8dd6-fb2c5d6de075.png)

10. To add a sensitive information type, in the **Conditions** section \> **Add or change types**. Then, under **Add or change types** \> choose **Add** \> select **U.S. Bank Account Number** and **U.S. Driver's License Number** \> **Add** \> **Done**.

    ![Option to Add or change types.](../media/c6c3ae86-f7db-40a8-a6e4-db11692024be.png)

    ![Add or change types pane.](../media/fdbb96af-b914-4a6c-a97b-bbd014689965.png)

11. To change the count (the number of instances of sensitive information required to trigger the rule), under **Instance count** \> choose the **min** value for each type \> enter 1. The minimum count cannot be empty. The maximum count can be empty; an empty **max** value convert to **any**.

    When finished, the min count for all of the sensitive information types should be **1** and the max count should be **any**. In other words, any occurrence of this type of sensitive information will satisfy this condition.

    ![Instance counts for sensitive information types.](../media/5c6e08cb-59a9-4558-b54b-d899836d4737.png)

12. For the final customization, you don't want your DLP policies to block people from doing their work when they have a valid business justification or encounter a false positive, so you want the user notification to include options to override the blocking action.

    In the **User notifications** section, you can see that email notifications and policy tips are turned on by default for this rule in the template.

    In the **User overrides** section, you can see that overrides for a business justification are turned on, but overrides to report false positives are not. Choose **Override the rule automatically if they report it as a false positive**.

    ![User notifications section and User overrides section.](../media/62720e7a-a939-4c03-b414-67748f3d64a0.png)

13. At the top of the rule editor, change the name of this rule from the default **High volume of content detected U.S. PII** to **Any content detected with U.S. PII** because it's now triggered by any occurrence of its sensitive information types.

14. At the bottom of the rule editor \> **Save**.

15. Review the conditions and actions for this rule \> **Next**.

    On the right, notice the **Status** switch for the rule. If you turn off an entire policy, all rules contained in the policy are also turned off. However, here you can turn off a specific rule without turning off the entire policy. This can be useful when you need to investigate a rule that is generating a large number of false positives.

16. On the next page, read and understand the following, and then choose whether to turn on the rule or test it out first \> **Next**.

     Before you create your DLP policies, you should consider rolling them out gradually to assess their impact and test their effectiveness before you fully enforce them. For example, you don't want a new DLP policy to unintentionally block access to thousands of documents that people require to get their work done.

    If you're creating DLP policies with a large potential impact, we recommend following this sequence:

17. Start in test mode without Policy Tips and then use the DLP reports to assess the impact. You can use DLP reports to view the number, location, type, and severity of policy matches. Based on the results, you can fine tune the rules as needed. In test mode, DLP policies will not impact the productivity of people working in your organization.

18. Move to Test mode with notifications and Policy Tips so that you can begin to teach users about your compliance policies and prepare them for the rules that are going to be applied. At this stage, you can also ask users to report false positives so that you can further refine the rules.

19. Turn on the policies so that the rules are enforced and the content's protected. Continue to monitor the DLP reports and any incident reports or notifications to make sure that the results are what you intend.

    ![Options for using test mode and turning on policy.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

20. Review your settings for this policy \> choose **Create**.

After you create and turn on a DLP policy, it's deployed to any content sources that it includes, such as SharePoint Online sites or OneDrive for Business accounts, where the policy begins automatically enforcing its rules on that content.


## Example: Identify sensitive information across all OneDrive for Business sites and restrict access for people outside your organization

OneDrive for Business accounts make it easy for people across your organization to collaborate and share documents. But a common concern for compliance officers is that sensitive information stored in OneDrive for Business accounts may be inadvertently shared with people outside your organization. A DLP policy can help mitigate this risk.

In this example, you'll create a DLP policy that identifies U.S. PII data, which includes Individual Taxpayer Identification Numbers (ITIN), Social Security Numbers, and U.S. passport numbers. You'll get started by using a template, and then you'll modify the template to meet your organization's compliance requirements—specifically, you'll:

- Add a couple of types of sensitive information—U.S. bank account numbers and U.S. driver's license numbers—so that the DLP policy protects even more of your sensitive data.

- Make the policy more sensitive, so that a single occurrence of sensitive information is enough to restrict access for external users.

- Allow users to override the actions by providing a business justification or reporting a false positive. This way, your DLP policy won't prevent people in your organization from getting their work done, provided they have a valid business reason for sharing the sensitive information.


## View the status of a DLP policy

At any time, you can view the status of your DLP policies on the **Policy** page in the **Data loss prevention** section of the Microsoft Purview compliance portal. Here you can find important information, such as whether a policy was successfully enabled or disabled, or whether the policy is in test mode.

Here are the different statuses and what they mean.

<br>

****

|Status|Explanation|
|---|---|
|**Turning on...**|The policy is being deployed to the content sources that it includes. The policy is not yet enforced on all sources.|
|**Testing, with notifications**|The policy is in test mode. The actions in a rule are not applied, but policy matches are collected and can be viewed by using the DLP reports. Notifications about policy matches are sent to the specified recipients.|
|**Testing, without notifications**|The policy is in test mode. The actions in a rule are not applied, but policy matches are collected and can be viewed by using the DLP reports. Notifications about policy matches are not sent to the specified recipients.|
|**On**|The policy is active and enforced. The policy was successfully deployed to all its content sources.|
|**Turning off...**|The policy is being removed from the content sources that it includes. The policy may still be active and enforced on some sources. Turning off a policy may take up to 45 minutes.|
|**Off**|The policy is not active and not enforced. The settings for the policy (sources, keywords, duration, etc) are saved.|
|**Deleting...**|The policy is in the process of being deleted. The policy is not active and not enforced. It normally takes an hour for a policy to delete.|
|

## Turn off a DLP policy

You can edit or turn off a DLP policy at any time. Turning off a policy disables all of the rules in the policy.

To edit or turn off a DLP policy, on the **Policy** page \> select the policy \> **Edit policy**.

![Edit policy button.](../media/ce319e92-0519-44fe-9507-45a409eaefe4.png)

In addition, you can turn off each rule individually by editing the policy and then toggling off the **Status** of that rule, as described above.

## More information

- [Learn about data loss prevention](dlp-learn-about-dlp.md)
- [Send notifications and show policy tips for DLP policies](use-notifications-and-policy-tips.md)
- [Create a DLP policy to protect documents with FCI or other properties](protect-documents-that-have-fci-or-other-properties.md)
- [What the DLP policy templates include](what-the-dlp-policy-templates-include.md)
- [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)
