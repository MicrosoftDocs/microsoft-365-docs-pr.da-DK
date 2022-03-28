---
title: Introduktion til forebyggelse af datatab for Power BI
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
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Forbered og installer DLP til PowerBI-placeringer.
ms.openlocfilehash: a1ea5321b77db1b4e7741f4d41cdd485adbd0b97
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "63717306"
---
# <a name="get-started-with-data-loss-prevention-policies-for-power-bi-preview"></a>Introduktion til politikker til forebyggelse af datatab for Power BI (prøveversion)

For at hjælpe organisationer med at registrere og beskytte deres følsomme data [Microsoft 365 DLP-politik (forebyggelse af datatab) understøtter](/microsoft-365/compliance/dlp-learn-about-dlp) Power BI. Når et PowerBI-datasæt opfylder kriterierne i en DLP-politik, kan der udløses en besked, der forklarer karakteren af det følsomme indhold. Denne besked er også registreret på fanen beskeder om forebyggelse af datatab i **Microsoft-overholdelsesportalen** for overvågning og administration af administratorer. Desuden kan mailbeskeder sendes til administratorer og bestemte brugere.

## <a name="considerations-and-limitations"></a>Overvejelser og begrænsninger

- DLP-politikker gælder for arbejdsområder. Kun arbejdsområder, der er hostet Premium Gen2-kapaciteter, understøttes.
- Evaluering af DLP-datasæt påvirker kapacitet. Efter forbrug for DLP-evalueringsarbejdsbelastninger understøttes ikke.
- Både den klassiske og den nye oplevelsesarbejdsområder understøttes, så længe de er hostet i Premium Gen2-kapacitet.
- Du skal oprette en brugerdefineret DLP-brugerdefineret politik for Power BI. DLP-skabeloner understøttes ikke.
- DLP-politik, der anvendes på DLP-placeringen, understøtter følsomhedsmærkater og typer af følsomme oplysninger som betingelser. 
- DLP-politikker for Power BI understøttes ikke for eksempeldatasæt, [streamingdatasæt](/power-bi/connect-data/service-real-time-streaming) eller datasæt, der opretter forbindelse til deres datakilde via [DirectQuery](/power-bi/connect-data/desktop-use-directquery) eller [en direkte forbindelse](/power-bi/connect-data/desktop-directquery-about#live-connections).
- DLP-politikker for Power BI ikke i nationale skyer.

## <a name="licensing-and-permissions"></a>Licenser og tilladelser

### <a name="skusubscriptions-licensing"></a>SKU/abonnementslicenser

Før du går i gang med DLP til Power BI, skal du bekræfte dit [Microsoft 365 abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1). Du kan se den fulde [licensvejledning Microsoft 365 vejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

### <a name="permissions"></a>Tilladelser

Data fra DLP til Power BI kan ses i [Aktivitetsoversigt](/microsoft-365/compliance/data-classification-activity-explorer). Der er fire roller, der giver tilladelse til aktivitetsstifinder. den konto, du bruger til at få adgang til dataene, skal være medlem af en af dem.

- Global administrator
- Overholdelsesadministrator
- Sikkerhedsadministrator
- Dataadministrator for overholdelse af regler og standarder

## <a name="how-dlp-policies-for-power-bi-work"></a>Sådan fungerer DLP-politikker Power BI arbejde

Du definerer en DLP-politik i afsnittet til forebyggelse af datatab på overholdelsesportalen. Se [Designe en politik til forebyggelse af datatab](dlp-policy-design.md#design-a-data-loss-prevention-policy). I politikken angiver du følsomhedsmærkater, du vil registrere. Du kan også angive den eller de handlinger, der skal ske, når politikken registrerer et datasæt, hvor der er anvendt en bestemt følsomhedsmærkat. DLP-politikker understøtter to handlinger for Power BI:

- Brugermeddelelse via politiktip.
- Beskeder. Beskeder kan sendes via mail til administratorer og brugere. Administratorer kan desuden overvåge og administrere beskeder på fanen **Beskeder** i Overholdelsescenter. 

Når et datasæt evalueres af DLP og opfylder betingelserne i en DLP-politik, anvendes de handlinger, der er defineret i politikken. Et datasæt evalueres, når et datasæt er:

- Publicer
- Genudgiv
- Opdatering efter behov
- Planlagt opdatering

>[!NOTE]
> DLP-evaluering af datasættet sker ikke, hvis et af følgende gælder:
> - Initiatoren af hændelsen er en tjenesteinspektør.
> - Datasætejeren er enten en tjenesteinspektør eller en B2B-bruger.

### <a name="what-happens-when-a-dataset-matches-a-dlp-policy"></a>Hvad sker der, når et datasæt svarer til en DLP-politik

Når et datasæt svarer til en DLP-politik:

- Hvis politikken har konfigureret en brugermeddelelse, markeres den i Power BI-tjenesten med et skjoldikon for at indikere, at den svarer til en DLP-politik.

    ![Skærmbillede af badge med politiktip på datasæt på lister.](../media/dlp-power-bi-policy-tip-on-dataset.png)

    Åbn siden med oplysninger om datasæt for at få vist et politiktip, der forklarer matchet med politikken, og hvordan den registrerede type af følsomme oplysninger skal håndteres.

    ![Skærmbillede af politiktip på siden med oplysninger om datasæt.](../media/dlp-power-bi-policy-tip-in-dataset-details.png)

    >[!NOTE]
    > Hvis du skjuler politiktippen, slettes den ikke. Den vises, næste gang du besøger siden.

- Hvis beskeder er aktiveret i politikken, registreres en besked på fanen **dlp-beskeder i overholdelsescenteret** , og (hvis konfigureret) sendes der en mail til administratorer og/eller bestemte brugere. Følgende billede viser fanen **Beskeder i sektionen** til forebyggelse af datatab i overholdelsescenteret.

    ![Skærmbillede af fanen Beskeder i overholdelsescenteret.](../media/dlp-power-bi-alerts-tab.png)

## <a name="configure-a-dlp-policy-for-power-bi"></a>Konfigurer en DLP-politik for Power BI

Følg fremgangsmåderne i [Opret, test og finjuster en DLP-politik,](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy) og brug den brugerdefinerede skabelon.

> [!IMPORTANT]
> Når du vælger placeringer til din DLP-politik for Power BI, skal du kun vælge Power BI placering. Vælg ikke andre placeringer. Denne konfiguration understøttes ikke. 

<!--1. Log into the [Microsoft 365 compliance portal](https://compliance.microsoft.com).

1. Choose the **Data loss prevention** solution in the navigation pane, select the **Policies** tab, choose **Create policy**.

    ![Screenshot of D L P create policy page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create.png)

1. Choose the **Custom** category and then the **Custom policy** template.
    
    >[!NOTE]
    >No other categories or templates are currently supported.

    ![Screenshot of D L P choose custom policy page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-choose-custom.png)
 
    When done, click **Next**.

1. Name the policy and provide a meaningful description.

    ![Screenshot of D L P policy name description section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-name-description.png)
 
    When done, click **Next**.

1. Enable Power BI as a location for the DLP policy. **Disable all other locations**. Currently, DLP policies for Power BI must specify Power BI as the sole location.

    ![Screenshot of D L P choose location page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-choose-location.png)

    By default the policy will apply to all workspaces. Alternatively, you can specify particular workspaces to include in the policy as well as workspaces to exclude from the policy.
    >[!NOTE]
    > DLP actions are supported only for workspaces hosted in Premium Gen2 capacities.

    If you select **Choose workspaces** or **Exclude workspaces**, a dialog will allow you to create a list of included (or excluded) workspaces. You must specify workspaces by workspace object ID. Click the info icon for information about how to find workspace object IDs.

    ![Screenshot of D L P choose workspaces dialog.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-choose-workspaces.png)
 
    After enabling Power BI as a DLP location for the policy and choosing which workspaces the policy will apply to, click **Next**.

1. The **Define policy settings** page appears. Choose **Create or customize advanced DLP rules** to begin defining your policy.

    ![Screenshot of D L P create advanced rule page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create-advanced-rule.png)
 
    When done, click **Next**.

1. On the **Customize advanced DLP rules** page, you can either start creating a new rule or choose an existing rule to edit. Click **Create rule**.

    ![Screenshot of D L P create rule page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create-rule.png)


1. The **Create rule** page appears. On the create rule page, provide a name and description for the rule, and then configure the other sections, which are described following the image below.

    ![Screenshot of D L P create rule form.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create-rule-form.png)
 
### Conditions

In the condition section, you define the conditions under which the policy will apply to a dataset. Conditions are created in groups. Groups make it possible to construct complex conditions.

1. Open the conditions section, choose **Add condition** and then **Content contains**.

    ![Screenshot of D L P add conditions content contains section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-add-conditions-content-contains.png)
 
    This opens the first group (named Default – you can change this).

1. Choose **Add**, and then **Sensitivity labels**.
        
    >[!NOTE]
    > Sensitive info types are currently not supported.
    
    ![Screenshot of D L P add conditions section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-add-conditions.png)
 
    When you choose **Sensitivity labels**, you will be able to choose a particular sensitivity label from a list that will appear.

    You can add additional sensitivity labels to the group. To the right of the group name, you can specify **Any of these** or **All of these**. This determines whether matches on all or any of the labels is required for the condition to hold. Make sure **Any of these** is selected, since datasets can’t have more than one label applied.

    The image below shows a group (Default) that contains two sensitivity label conditions. The logic Any of these means that a match on any one of the sensitivity labels in the group constitutes “true” for that group.

    ![Screenshot of D L P conditions group section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-condition-group.png) 
 
    You can create more than one group, and you can control the logic between the groups with **AND** or **OR** logic. 

    The image below shows a rule containing two groups, joined by **OR** logic.

    ![Screenshot of rule with two groups.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-content-contains.png) 
 
### Exceptions

If the sensitivity label of the dataset matches any of the defined exceptions, the rule won’t be applied to the dataset. 

Exceptions are configured in the same way as conditions, described above.
    
![Screenshot of D L P exceptions section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-exceptions-section.png)
 
### Actions

Protection actions are currently unavailable for Power BI DLP policies.

![Screenshot of D L P policy actions section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-actions-section.png)


### User notifications

The user notifications section is where you configure your policy tip. Turn on the toggle, select the **Notify users in Office 365 service with a policy tip** and **Policy tips** checkboxes, and write your policy tip in the text box.

![Screenshot of D L P user notification section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-user-notification.png)
 
### User overrides
 
User overrides are currently unavailable for Power BI DLP policies.

![Screenshot of D L P user overrides section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-user-overrides-section.png) 
 
### Incident reports

Assign a severity level that will be shown in alerts generated from this policy. Enable (default) or disable email notification to admins, specify users or groups for email notification, and configure the details about when notification will occur.

![Screenshot of D L P incident report section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-incidence-report.png)
   
### Additional options

![Screenshot of D L P additional options section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-additional-options.png)
 
## Monitor and manage policy alerts

Log into the Microsoft 365 compliance portal and navigate to **Data loss prevention > Alerts**.

![Screenshot of D L P Alerts tab.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-alerts-tab.png)

Click on an alert to start drilling down to its details and to see management options.
-->
## <a name="next-steps"></a>Næste trin

- [Få mere at vide om forebyggelse af datatab](/microsoft-365/compliance/dlp-learn-about-dlp)
- [Følsomhedsmærkater i Power BI](/power-bi/enterprise/service-security-sensitivity-label-overview)
- [Overvågningsskema for følsomhedsmærkater i Power BI](/power-bi/enterprise/service-security-sensitivity-label-audit-schema)