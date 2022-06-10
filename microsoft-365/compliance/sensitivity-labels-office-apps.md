---
title: Administrer følsomhedsmærkater i Office apps
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Oplysninger til it-administratorer om administration af følsomhedsmærkater i Office apps til stationære computere, mobilenheder og internettet.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ff0a64ed04aecff83634172ecf57263482f90dc6
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014173"
---
# <a name="manage-sensitivity-labels-in-office-apps"></a>Administrer følsomhedsmærkater i Office apps

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du har [publiceret](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) følsomhedsmærkater fra Microsoft Purview-overholdelsesportalen, vises de i Office apps, hvor brugerne kan klassificere og beskytte data, når de oprettes eller redigeres.

Brug oplysningerne i denne artikel til at hjælpe dig med at administrere følsomhedsmærkater i Office apps. Du kan f.eks. identificere de minimumversioner af apps, du har brug for, for funktioner, der er specifikke for indbygget mærkning, eventuelle yderligere konfigurationsoplysninger for disse funktioner og forstå interaktioner med Azure Information Protection unified-mærkatklienten og andre apps og tjenester.

## <a name="labeling-client-for-desktop-apps"></a>Navngiver klient til skrivebordsapps

Hvis du vil bruge følsomhedsmærkater, der er indbygget i Office skrivebordsapps til Windows og Mac, skal du bruge en abonnementsversion af Office. Denne navngivningsklient understøtter ikke separate udgaver af Office, der nogle gange kaldes "Office Perpetual".

Hvis du ikke kan opgradere til Microsoft 365 Apps for enterprise for abonnementsversionerne af Office, kun til Windows computere, kan du bruge [Azure Information Protection (AIP) Unified Labeling Client](/azure/information-protection/rms-client/aip-clientv2). Denne klient er dog nu i [vedligeholdelsestilstand](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613), og vi anbefaler ikke, at du bruger AIP-tilføjelsesprogrammet til Office apps, medmindre du er nødt til det. Du kan få flere oplysninger under [Hvorfor vælge indbygget mærkning via AIP-tilføjelsesprogrammet til Office apps](sensitivity-labels-aip.md).

## <a name="support-for-sensitivity-label-capabilities-in-apps"></a>Understøttelse af egenskaber for følsomhedsmærkater i apps

I følgende tabeller vises minimumversionen af Office, der introducerede specifikke egenskaber for følsomhedsmærkater, der er indbygget i Office apps. Eller hvis mærkategenskaben er i en offentlig prøveversion eller gennemses for en fremtidig udgivelse. Brug [køreplanen for Microsoft 365](https://aka.ms/MIPC/Roadmap) for at få oplysninger om nye funktioner, der er planlagt til fremtidige versioner.

Nye versioner af Office apps gøres tilgængelige på forskellige tidspunkter for forskellige opdateringskanaler. For Windows får du de nye funktioner tidligere, når du er på den aktuelle kanal eller den månedlige enterprisekanal i stedet for Semi-Annual Enterprise Channel. Minimumversionsnumrene kan også være forskellige fra én opdateringskanal til den næste. Du kan få flere oplysninger under [Oversigt over opdateringskanaler for Microsoft 365 Apps](/deployoffice/overview-update-channels) og [Opdateringshistorik for Microsoft 365 Apps](/officeupdates/update-history-microsoft365-apps-by-date).

Nye funktioner, der findes i en privat prøveversion, er ikke inkluderet i tabellen, men du kan muligvis joinforbinde disse prøveversioner ved at udnævne din organisation til [Microsoft Information Protection private prøveversionsprogram](https://aka.ms/mip-preview).

Office til iOS og Office til Android: Følsomhedsmærkater er indbygget i [Office-app](https://www.microsoft.com/en-us/microsoft-365/blog/2020/02/19/new-office-app-android-ios-available/).

> [!TIP]
> Når du sammenligner minimumversionerne i tabellerne med de versioner, du har, skal du huske den almindelige praksis med udgivelsesversioner for at udelade foranstillede nuller.
> 
> Du har f.eks. version 4.2128.0 og læst, at 4.7.1+ er minimumversionen. For at lette sammenligningen skal du læse 4.7.1 (ingen foranstillede nuller) som 4. **0007.1** (og ikke 4.**7000.1**). Din version af 4.2128.0 er højere end 4.0007.1, så din version understøttes.

### <a name="sensitivity-label-capabilities-in-word-excel-and-powerpoint"></a>Egenskaber for følsomhedsmærkater i Word, Excel og PowerPoint

De angivne tal er det mindste Office programversioner, der kræves for hver funktion. 

> [!NOTE]
> For Windows og Semi-Annual Enterprise Channel udgives de mindste understøttede versionsnumre muligvis endnu ikke. [Få mere at vide](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions)
 
|Kapacitet |Windows |Mac |Ios |Android |Web |
|-----------|-------:|----|----|--------|----|
|[Anvend, rediger eller fjern mærkat manuelt](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| Aktuel kanal: 1910+ <br /><br> Månedlig Enterprise-kanal: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Ja – tilvalg](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Anvend et standardnavn](sensitivity-labels.md#what-label-policies-can-do) på nye dokumenter                                         | Aktuel kanal: 1910+ <br /><br> Månedlig Enterprise-kanal: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Ja – tilvalg](sensitivity-labels-sharepoint-onedrive-files.md)                                                        |
|[Anvend et standardnavn](sensitivity-labels.md#what-label-policies-can-do) på eksisterende dokumenter | Prøveversion: Udrulning til [betakanal](https://office.com/insider) | Eksempel: Udrulning til [aktuel kanal (prøveversion)](https://office.com/insider) | Under gennemgang | Under gennemgang | [Ja – tilvalg](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Kræv justering for at ændre en etiket](sensitivity-labels.md#what-label-policies-can-do)                     | Aktuel kanal: 1910+ <br /><br> Månedlig Enterprise-kanal: 1910+  <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Ja – tilvalg](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Giv hjælp-link til en brugerdefineret hjælpside](sensitivity-labels.md#what-label-policies-can-do)                       | Aktuel kanal: 1910+ <br /><br> Månedlig Enterprise-kanal: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Ja – tilvalg](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Markér indholdet](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | Aktuel kanal: 1910+ <br /><br> Månedlig Enterprise-kanal: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Ja – tilvalg](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Dynamiske markeringer med variabler](#dynamic-markings-with-variables)                                              | Aktuel kanal: 2010+ <br /><br> Månedlig Enterprise-kanal: 2010+ <br /><br> Semi-Annual Enterprise Channel: 2102+ | 16.42+     | 2.42+ | 16.0.13328+ | [Ja – tilvalg](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Tildel tilladelser nu](encryption-sensitivity-labels.md#assign-permissions-now)                                 | Aktuel kanal: 1910+ <br /><br> Månedlig Enterprise-kanal: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Ja – tilvalg](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Lad brugere tildele tilladelser: <br /> – Spørg brugere](encryption-sensitivity-labels.md#let-users-assign-permissions)                     |Aktuel kanal: 2004+ <br /><br> Månedlig Enterprise-kanal: 2004+ <br /><br> Semi-Annual Enterprise Channel: 2008+ | 16.35+   | Under gennemgang   | Under gennemgang         | Under gennemgang                                                        |
|[Overvåg mærkatrelateret brugeraktivitet](#auditing-labeling-activities)                      | Aktuel kanal: 2011+ <br /><br> Månedlig Enterprise-kanal: 2011+ <br /><br> Semi-Annual Enterprise Channel: 2108+ | 16.43+ | 2.46+ | 16.0.13628+ | Ja |
|[Kræv, at brugerne anvender en mærkat på deres mail og dokumenter](#require-users-to-apply-a-label-to-their-email-and-documents)   | Aktuel kanal: 2101+ <br /><br> Månedlig Enterprise-kanal: 2101+ <br /><br> Semi-Annual Enterprise Channel: 2108+ | 16.45+         | 2.47+ | 16.0.13628+ | [Ja – tilvalg](sensitivity-labels-sharepoint-onedrive-files.md)                                            
|[Anvend automatisk en følsomhedsmærkat på indhold](apply-sensitivity-label-automatically.md) <br /> - Brug af følsomme infotyper                    | Aktuel kanal: 2009+ <br /><br> Månedlig Enterprise-kanal: 2009+ <br /><br> Semi-Annual Enterprise Channel: 2102+ | 16.44+ | Under gennemgang | Under gennemgang | [Ja – tilvalg](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Anvend automatisk en følsomhedsmærkat på indhold](apply-sensitivity-label-automatically.md) <br /> - Brug af klassificeringer, der kan oplæres                    | Aktuel kanal: 2105+ <br /><br> Månedlig Enterprise-kanal: 2105+ <br /><br> Semi-Annual Enterprise Channel: 2108+ | 16.49+ | Under gennemgang | Under gennemgang | [Ja – tilvalg](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Understøttelse af samtidig redigering og Automatisk lagring](sensitivity-labels-coauthoring.md) af navngivne og krypterede dokumenter | Aktuel kanal: 2107+ <br /><br> Månedlig Enterprise-kanal: 2107+ <br /><br> Semi-Annual Enterprise-kanal: 2202+ |  16.51+ | Prøveversion: 2,58+, når du [tilmelder](sensitivity-labels-coauthoring.md#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) dig | Prøveversion: 16.0.14931+ når du [tilmelder](sensitivity-labels-coauthoring.md#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) dig | [Ja – tilvalg](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Understøttelse af PDF](#pdf-support)| Prøveversion: Udrulning til [betakanal](https://office.com/insider) |  Under gennemgang | Under gennemgang | Under gennemgang | Under gennemgang |


### <a name="sensitivity-label-capabilities-in-outlook"></a>Egenskaber for følsomhedsmærkat i Outlook

De angivne tal er det mindste Office programversioner, der kræves for hver funktion. 

> [!NOTE]
> For Windows og Semi-Annual Enterprise Channel udgives de mindste understøttede versionsnumre muligvis endnu ikke. [Få mere at vide](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions)

|Kapacitet |Outlook til Windows |Outlook til Mac |Outlook på iOS |Outlook på Android |Outlook på internettet |
|-----------|-------------------:|----------------|---------------|-------------------|-------------------|
|[Anvend, rediger eller fjern mærkat manuelt](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| Aktuel kanal: 1910+ <br /><br> Månedlig Enterprise-kanal: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Ja               |
|[Anvend et standardnavn](sensitivity-labels.md#what-label-policies-can-do)                                         | Aktuel kanal: 1910+ <br /><br> Månedlig Enterprise-kanal: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Ja               |
|[Kræv justering for at ændre en etiket](sensitivity-labels.md#what-label-policies-can-do)                     | Aktuel kanal: 1910+ <br /><br> Månedlig Enterprise-kanal: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Ja               |
|[Giv hjælp-link til en brugerdefineret hjælpside](sensitivity-labels.md#what-label-policies-can-do)                       | Aktuel kanal: 1910+ <br /><br> Månedlig Enterprise-kanal: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Ja               |
|[Markér indholdet](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | Aktuel kanal: 1910+ <br /><br> Månedlig Enterprise-kanal: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Ja               |
|[Dynamiske markeringer med variabler](#dynamic-markings-with-variables)                                              | Aktuel kanal: 1910+ <br /><br> Månedlig Enterprise-kanal: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Ja               |
|[Tildel tilladelser nu](encryption-sensitivity-labels.md#assign-permissions-now)                                 | Aktuel kanal: 1910+ <br /><br> Månedlig Enterprise-kanal: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Ja               |
|[Lad brugerne tildele tilladelser: <br /> - Videresend ikke](encryption-sensitivity-labels.md#let-users-assign-permissions)                     | Aktuel kanal: 1910+ <br /><br> Månedlig Enterprise-kanal: 1910+ <br /><br> Semi-Annual Enterprise Channel: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Ja               |
|[Lad brugerne tildele tilladelser: <br /> - Kun kryptér](encryption-sensitivity-labels.md#let-users-assign-permissions)  | Aktuel kanal: 2011+ <br /><br> Månedlig Enterprise-kanal: 2011+ <br /><br> Semi-Annual Enterprise Channel: 2108+ | 16.48+ <sup>\*</sup> | 4.2112.0+  | 4.2112.0+ | Ja |
|[Kræv, at brugerne anvender en mærkat på deres mail og dokumenter](#require-users-to-apply-a-label-to-their-email-and-documents)   | Aktuel kanal: 2101+ <br /><br> Månedlig Enterprise-kanal: 2101+ <br /><br> Semi-Annual Enterprise Channel: 2108+ | 16.43+ <sup>\*</sup>                    | 4.2111+            | 4.2111+                | Ja                |
|[Overvåg mærkatrelateret brugeraktivitet](#auditing-labeling-activities) | Aktuel kanal: 2011+ <br /><br> Månedlig Enterprise-kanal: 2011+ <br /><br> Semi-Annual Enterprise Channel: 2108+ | 16.51+ <sup>\*</sup> | 4.2126+ | 4.2126+ | Ja |
|[Anvend automatisk en følsomhedsmærkat på indhold](apply-sensitivity-label-automatically.md) <br /> - Brug af følsomme infotyper                    | Aktuel kanal: 2009+ <br /><br> Månedlig Enterprise-kanal: 2009+ <br /><br> Semi-Annual Enterprise Channel: 2102+ | 16.44+ <sup>\*</sup>                    | Under gennemgang           | Under gennemgang               | Ja |
|[Anvend automatisk en følsomhedsmærkat på indhold](apply-sensitivity-label-automatically.md) <br /> - Brug af klassificeringer, der kan oplæres                    | Aktuel kanal: 2105+ <br /><br> Månedlig Enterprise-kanal: 2105+ <br /><br> Semi-Annual Enterprise Channel: 2108+ | 16.49+ | Under gennemgang           | Under gennemgang               | Ja |
|[Forskellige indstillinger for standardmærkat og obligatorisk mærkning](#outlook-specific-options-for-default-label-and-mandatory-labeling)                    | Aktuel kanal: 2105+ <br /><br> Månedlig Enterprise-kanal: 2105+ <br /><br> Semi-Annual Enterprise Channel: 2108+ | 16.43+ <sup>\*</sup>                   | 4.2111+           | 4.2111+               | Ja |
|[Understøttelse af PDF](#pdf-support) | Under gennemgang|  Under gennemgang | Under gennemgang | Under gennemgang | Under gennemgang |
|

**Fodnoter:**

<sup>\*</sup>Kræver den [nye Outlook til Mac](https://support.microsoft.com/office/the-new-outlook-for-mac-6283be54-e74d-434e-babb-b70cefc77439)

## <a name="office-built-in-labeling-client-and-the-azure-information-protection-client"></a>Office indbygget navngivningsklient og Azure Information Protection-klienten

Hvis brugerne har [Azure Information Protection-klienten (AIP)](/azure/information-protection/rms-client/aip-clientv2) installeret på deres Windows computere, er indbyggede mærkater som standard slået fra i [Windows Office apps, der understøtter dem](#labeling-client-for-desktop-apps). Da indbyggede mærkater ikke bruger et Office-tilføjelsesprogram, som bruges af AIP-klienten, har de fordel af mere stabilitet og bedre ydeevne. De understøtter også de nyeste funktioner, f.eks. avancerede klassificeringer. 

> [!NOTE]
> Hvis du ikke får vist de navngivningsfunktioner, du forventer på Windows computere, kan det skyldes, at du skal [deaktivere AIP-tilføjelsesprogrammet](sensitivity-labels-aip.md#how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps), selvom du har bekræftet de mindste understøttede versioner for din Office opdateringskanal.

Hvis du vil vide mere om understøttelse af mærkning med AIP-klienten, og hvordan du deaktiverer denne klient i Office apps, skal du se [Hvorfor vælge indbygget mærkning via AIP-tilføjelsesprogrammet til Office apps](sensitivity-labels-aip.md).

## <a name="if-you-need-to-turn-off-built-in-labeling-in-office-apps-on-windows"></a>Hvis du har brug for at slå indbygget mærkning fra i Office apps på Windows

Den Office indbyggede navngivningsklient downloader følsomhedsmærkater og politikindstillinger for følsomhedsmærkater fra Microsoft Purview-overholdelsesportalen.

Hvis du vil bruge den Office indbyggede navngivningsklient, skal du have en eller flere [mærkatpolitikker publiceret](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) til brugere fra Microsoft Purview-overholdelsesportalen og en [understøttet version af Office](#support-for-sensitivity-label-capabilities-in-apps).

Hvis begge disse betingelser er opfyldt, men du har brug for at slå de indbyggede mærkater fra i Windows Office apps, skal du bruge følgende Gruppepolitik indstilling:

1. Gå til **brugerkonfiguration/Administrative skabeloner/Microsoft Office 2016/Security Indstillinger**.

2. Angiv **Brug funktionen Følsomhed i Office for at anvende og få vist følsomhedsmærkater** til **0**.

Hvis du senere har brug for at gendanne denne konfiguration, skal du ændre værdien til **1**. Du skal muligvis også ændre denne værdi til 1, hvis knappen **Følsomhed** ikke vises på båndet som forventet. En tidligere administrator har f.eks. deaktiveret denne mærkatindstilling.
 
Udrul denne indstilling ved hjælp af Gruppepolitik eller ved hjælp af [tjenesten Office cloudpolitik](/DeployOffice/overview-office-cloud-policy-service). Indstillingen træder i kraft, når disse Office apps genstartes. 

Da denne indstilling er specifik for Windows Office apps, har den ingen indvirkning på andre apps på Windows, der understøtter følsomhedsmærkater (f.eks. Power BI) eller andre platforme (f.eks. macOS, mobilenheder og Office på internettet). Hvis du ikke ønsker, at nogle eller alle brugere skal se og bruge følsomhedsmærkater på tværs af alle apps og alle platforme, skal du ikke tildele en politik for følsomhedsmærkat til disse brugere.

## <a name="office-file-types-supported"></a>understøttede Office filtyper

Office apps, der har indbygget mærkat til Word-, Excel- og PowerPoint-filer, understøtter Open XML-formatet (f.eks. .docx og .xlsx), men ikke formatet Microsoft Office 97-2003 (f.eks. .doc og .xls), Open Document Format (f.eks. .odt og .ods) eller andre formater. Når en filtype ikke understøttes til indbygget mærkning, er knappen **Følsomhed** ikke tilgængelig i Office-app.

Azure Information Protection Unified Labeling-klienten understøtter både Open XML-formatet og formatet Microsoft Office 97-2003. Du kan få flere oplysninger i [Filtyper, der understøttes af Azure Information Protection Unified Labeling-klienten](/azure/information-protection/rms-client/clientv2-admin-guide-file-types) fra klientens administratorvejledning.

Du kan finde de understøttede filtyper i dokumentationen til andre mærkatløsninger.

## <a name="protection-templates-and-sensitivity-labels"></a>Beskyttelsesskabeloner og følsomhedsmærkater

Administratordefinerede [beskyttelsesskabeloner](/azure/information-protection/configure-policy-templates), f.eks dem, du definerer for Office 365 Meddelelsekryptering, er ikke synlige i Office apps, når du bruger indbygget mærkning. Denne forenklede oplevelse afspejler, at det ikke er nødvendigt at vælge en beskyttelsesskabelon, fordi de samme indstillinger er inkluderet i følsomhedsmærkater, hvor kryptering er aktiveret.

Du kan konvertere en eksisterende skabelon til en følsomhedsmærkat, når du bruger [new-label-cmdlet'en](/powershell/module/exchange/new-label) med parameteren *EncryptionTemplateId* .

## <a name="information-rights-management-irm-options-and-sensitivity-labels"></a>IRM-indstillinger (Information Rights Management) og følsomhedsmærkater

Følsomhedsmærkater, som du konfigurerer til at anvende kryptering, fjerner kompleksiteten fra brugerne for at angive deres egne krypteringsindstillinger. I mange Office apps kan disse individuelle krypteringsindstillinger stadig konfigureres manuelt af brugerne ved hjælp af IRM-indstillinger (Information Rights Management). For Windows apps:

- For et dokument: **Filoplysninger** >  > **Beskyt dokument** > **Begræns adgang**
- for en mail: Fra fanen **Indstillinger** > **Krypter** 
  
Når brugerne første gang navngiver et dokument eller en mail, kan de tilsidesætte indstillingerne for mærkatkonfigurationen med deres egne krypteringsindstillinger. Eksempel:

- En bruger anvender mærkaten **Fortroligt \ Alle medarbejdere** på et dokument, og denne mærkat er konfigureret til at anvende krypteringsindstillinger for alle brugere i organisationen. Denne bruger konfigurerer derefter IRM-indstillingerne manuelt for at begrænse adgangen til en bruger uden for din organisation. Slutresultatet er et dokument med mærkaten **Fortroligt \ Alle medarbejdere** og krypteret, men brugerne i organisationen kan ikke åbne det som forventet.

- En bruger anvender mærkaten **Fortroligt \ Modtagere må kun** anvendes på en mail, og denne mail er konfigureret til at anvende krypteringsindstillingen **Videresend ikke**. I appen Outlook vælger brugeren derefter manuelt IRM-indstillingen for Encrypt-Only. Slutresultatet er, at mens mailen forbliver krypteret, kan den videresendes af modtagere, selvom den har mærkaten **Fortroligt \ Modtagere kun** .
    
    For Outlook på internettet er indstillingerne i menuen **Kryptér** ikke tilgængelige for en bruger at vælge, når den aktuelt valgte mærkat anvender kryptering.

- En bruger anvender den **generelle** mærkat på et dokument, og denne mærkat er ikke konfigureret til at anvende kryptering. Denne bruger konfigurerer derefter IRM-indstillingerne manuelt for at begrænse adgangen til dokumentet. Slutresultatet er et dokument, der er mærket **Generelt** , men som også anvender kryptering, så nogle brugere ikke kan åbne det som forventet.

Hvis dokumentet eller mailen allerede er mærket, kan en bruger udføre en af disse handlinger, hvis indholdet ikke allerede er krypteret, eller hvis brugeren har [brugsrettigheden](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) Eksportér eller Fuld kontrol. 

Hvis du vil have en mere ensartet mærkatoplevelse med meningsfuld rapportering, skal du angive de relevante mærkater og vejledning, så brugerne kun kan anvende mærkater for at beskytte dokumenter og mails. Eksempel:

- I undtagelsestilfælde, hvor brugerne skal tildele deres egne tilladelser, skal du angive mærkater, der [giver brugerne mulighed for at tildele deres egne tilladelser](encryption-sensitivity-labels.md#let-users-assign-permissions). 

- I stedet for at brugere manuelt fjerner kryptering efter at have valgt en mærkat, der anvender kryptering, skal du angive et undernavn alternativ, når brugerne har brug for en mærkat med den samme klassificering, men ingen kryptering. Såsom:
    - **Fortroligt \ Alle medarbejdere**
    - **Fortroligt \ Alle (ingen kryptering)**

- Overvej at deaktivere IRM-indstillinger for at forhindre brugerne i at vælge dem:
    - Outlook til Windows: 
        - Registreringsdatabasenøgler `DWORD:00000001` *DisableDNF* og *DisableEO* fra `HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\DRM`
        - Sørg for, at indstillingen Gruppepolitik **Konfigurer standardkryptering for knappen Krypter** ikke er konfigureret
    - Outlook til Mac: 
        - Keys *DisableEncryptOnly*- og *DisableDoNotForward-sikkerhedsindstillinger*, der er dokumenteret i [Angiv indstillinger for Outlook til Mac](/DeployOffice/mac/preferences-outlook)
    - Outlook på internettet: 
        - Parametre *SimplifiedClientAccessDoNotForwardDisabled* og *SimplifiedClientAccessEncryptOnlyDisabled* , der er dokumenteret for [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration)
    - Outlook til iOS og Android: Disse apps understøtter ikke brugere, der anvender kryptering uden mærkater, så intet at deaktivere.

> [!NOTE]
> Hvis brugerne fjerner kryptering manuelt fra et navngivet dokument, der er gemt i SharePoint eller OneDrive, og du har [aktiveret følsomhedsmærkater for Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md), gendannes mærkatkrypteringen automatisk, næste gang dokumentet åbnes eller downloades. 


## <a name="apply-sensitivity-labels-to-files-emails-and-attachments"></a>Anvend følsomhedsmærkater på filer, mails og vedhæftede filer

Brugerne kan kun anvende én mærkat ad gangen for hvert dokument eller hver mail.

Når du navngiver en mail med vedhæftede filer, arver de vedhæftede filer kun etiketten, hvis den etiket, du anvender på mailen, anvender kryptering, og den vedhæftede fil er et Office dokument ikke allerede er krypteret. Da den nedarvede mærkat anvender kryptering, krypteres den vedhæftede fil for nylig.

En vedhæftet fil nedarver ikke mærkaterne fra mailen, når den mærkat, der anvendes på mailen, ikke anvender kryptering, eller den vedhæftede fil allerede er krypteret.

Eksempler på nedarvning af mærkater, hvor mærkaten **Fortroligt** anvender kryptering, og etiketten **Generelt** ikke anvender kryptering:

- En bruger opretter en ny mail og anvender mærkaten **Fortroligt** på denne meddelelse. De tilføjer derefter et Word-dokument, der ikke er navngivet eller krypteret. Som følge af nedarvning er dokumentet for nylig forsynet med mærkaten **Fortroligt** , og der er nu anvendt kryptering fra den pågældende mærkat.

- En bruger opretter en ny mail og anvender mærkaten **Fortroligt** på denne meddelelse. De tilføjer derefter et Word-dokument, der hedder **Generelt** , og denne fil er ikke krypteret. Som følge af nedarvning genmærkaten for dokumentet som **Fortroligt** og har nu anvendt kryptering fra denne mærkat.

## <a name="sensitivity-label-compatibility"></a>Kompatibilitet med følsomhedsmærkat

**Med RMS-oplyste apps**: Hvis du åbner et navngivet og krypteret dokument eller en mail i et [RMS-oplyst program](/azure/information-protection/requirements-applications#rms-enlightened-applications) , der ikke understøtter følsomhedsmærkater, gennemtvinger appen stadig kryptering og rettighedsstyring.

**Med Azure Information Protection-klienten**: Du kan få vist og ændre følsomhedsmærkater, som du anvender på dokumenter og mails, med den Office indbyggede mærkatklient ved hjælp af Azure Information Protection-klienten og omvendt.

**Med andre versioner af Office**: Enhver godkendt bruger kan åbne navngivne dokumenter og mails i andre versioner af Office. Du kan dog kun få vist eller ændre mærkaten i understøttede Office versioner eller ved hjælp af Azure Information Protection-klienten. Understøttede Office-app versioner er angivet i det [forrige afsnit](#support-for-sensitivity-label-capabilities-in-apps).

## <a name="support-for-sharepoint-and-onedrive-files-protected-by-sensitivity-labels"></a>Understøttelse af SharePoint- og OneDrive filer, der er beskyttet af følsomhedsmærkater

Hvis du vil bruge den Office indbyggede navngivningsklient med Office på internettet til dokumenter i SharePoint eller OneDrive, skal du sørge for, at du har [aktiveret følsomhedsmærkater for Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="support-for-external-users-and-labeled-content"></a>Understøttelse af eksterne brugere og markeret indhold

Når du navngiver et dokument eller en mail, gemmes etiketten som metadata, der omfatter din lejer og et mærkat-GUID. Når et navngivet dokument eller en mail åbnes af en Office-app, der understøtter følsomhedsmærkater, er disse metadata skrivebeskyttede, og kun hvis brugeren tilhører den samme lejer, vises mærkaten i deres app. For indbyggede navne til Word, PowerPoint og Excel vises navnenavnet f.eks. på statuslinjen. 

Det betyder, at hvis du deler dokumenter med en anden organisation, der bruger forskellige navne, kan hver organisation anvende og se deres egen mærkat anvendt på dokumentet. Følgende elementer fra en anvendt mærkat er dog synlige for brugere uden for organisationen:

- Indholdsmarkeringer. Når en etiket anvender et sidehoved, en sidefod eller et vandmærke, føjes de direkte til indholdet og forbliver synlige, indtil nogen ændrer eller sletter dem.

- Navnet på og beskrivelsen af den underliggende beskyttelsesskabelon fra en mærkat, der anvendte kryptering. Disse oplysninger vises på en meddelelseslinje øverst i dokumentet for at angive oplysninger om, hvem der har tilladelse til at åbne dokumentet, og deres brugsrettigheder til det pågældende dokument.

### <a name="sharing-encrypted-documents-with-external-users"></a>Deling af krypterede dokumenter med eksterne brugere

Ud over at begrænse adgangen til brugere i din egen organisation kan du udvide adgangen til alle andre brugere, der har en konto i Azure Active Directory. Men hvis din organisation bruger politikker for betinget adgang, skal du se [næste afsnit](#conditional-access-policies) for at få flere overvejelser.

Alle Office apps og andre [RMS-oplyste programmer](/azure/information-protection/requirements-applications#rms-enlightened-applications) kan åbne krypterede dokumenter, når brugeren er godkendt. 

Hvis eksterne brugere ikke har en konto i Azure Active Directory, kan de godkende ved hjælp af gæstekonti i din lejer. Disse gæstekonti kan også bruges til at få adgang til delte dokumenter i SharePoint eller OneDrive, når du har [aktiveret følsomhedsmærkater for Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md):

- En mulighed er selv at oprette disse gæstekonti. Du kan angive en hvilken som helst mailadresse, som disse brugere allerede bruger. For eksempel deres Gmail-adresse.
    
    Fordelen ved denne indstilling er, at du kan begrænse adgang og rettigheder til bestemte brugere ved at angive deres mailadresse i krypteringsindstillingerne. Ulempen er administrationsomkostningerne ved oprettelse og koordinering af kontoen med mærkatkonfigurationen.

- En anden mulighed er at bruge [SharePoint og OneDrive integration med Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration), så gæstekonti automatisk oprettes, når dine brugere deler links.
    
    Fordelen ved denne indstilling er den mindste administrative belastning, da kontiene oprettes automatisk, og mere enkel konfiguration af mærkater. I dette scenarie skal du vælge krypteringsindstillingen [Tilføj alle godkendte brugere](encryption-sensitivity-labels.md#requirements-and-limitations-for-add-any-authenticated-users) , fordi du ikke kender mailadresserne på forhånd. Ulempen er, at denne indstilling ikke giver dig mulighed for at begrænse adgangs- og brugsrettigheder til bestemte brugere.

Eksterne brugere kan også bruge en Microsoft-konto til at åbne krypterede dokumenter, når de bruger Windows og Microsoft 365 Apps ([tidligere Office 365 apps](/deployoffice/name-change)) eller den separate version af Office 2019. For nylig understøttes Microsoft-konti også til åbning af krypterede dokumenter på macOS (Microsoft 365 Apps, version 16.42+), Android (version 16.0.13029+) og iOS (version 2.42+). En bruger i din organisation deler f.eks. et krypteret dokument med en bruger uden for organisationen, og krypteringsindstillingerne angiver en Gmail-mailadresse for den eksterne bruger. Denne eksterne bruger kan oprette sin egen Microsoft-konto, der bruger deres Gmail-mailadresse. Når de derefter er logget på med denne konto, kan de åbne dokumentet og redigere det i henhold til de forbrugsbegrænsninger, der er angivet for dem. Du kan se et eksempel på dette scenarie under [Åbning og redigering af det beskyttede dokument](/azure/information-protection/secure-collaboration-documents#opening-and-editing-the-protected-document).

> [!NOTE]
> Mailadressen til Microsoft-kontoen skal svare til den mailadresse, der er angivet for at begrænse adgangen til krypteringsindstillingerne.

Når en bruger med en Microsoft-konto åbner et krypteret dokument på denne måde, oprettes der automatisk en gæstekonto for lejeren, hvis der ikke allerede findes en gæstekonto med samme navn. Når gæstekontoen findes, kan den derefter bruges til at åbne dokumenter i SharePoint og OneDrive ved hjælp af Office på internettet ud over at åbne krypterede dokumenter fra de understøttede skrivebords- og mobilapps Office.

Den automatiske gæstekonto oprettes dog ikke med det samme i dette scenarie på grund af replikeringsventetid. Hvis du angiver personlige mailadresser som en del af dine indstillinger for mærkatkryptering, anbefaler vi, at du opretter tilsvarende gæstekonti i Azure Active Directory. Giv derefter disse brugere besked om, at de skal bruge denne konto til at åbne et krypteret dokument fra din organisation.

> [!TIP]
> Da du ikke kan være sikker på, at eksterne brugere bruger en understøttet Office klientapp, deler links fra SharePoint og OneDrive, når du har oprettet gæstekonti (for bestemte brugere), eller når du bruger [SharePoint og OneDrive integration med Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview)  (for alle godkendte brugere) er en mere pålidelig metode til at understøtte sikkert samarbejde med eksterne brugere.

### <a name="conditional-access-policies"></a>Politikker for betinget adgang

Hvis din organisation har implementeret [Azure Active Directory politikker for betinget adgang](/azure/active-directory/conditional-access/overview), skal du kontrollere konfigurationen af disse politikker. Hvis politikkerne omfatter **Microsoft Azure Information Protection**, og politikken udvides til eksterne brugere, skal disse eksterne brugere have en gæstekonto i din lejer, selvom de har en Azure AD konto i deres egen lejer.

Uden denne gæstekonto kan de ikke åbne det krypterede dokument og få vist en fejlmeddelelse. Meddelelsesteksten kan informere vedkommende om, at vedkommendes konto skal tilføjes som ekstern bruger i lejeren med den forkerte instruktion til dette scenarie om at **logge af og logge på igen med en anden Azure Active Directory brugerkonto**.

Hvis du ikke kan oprette og konfigurere gæstekonti i din lejer for eksterne brugere, der skal åbne dokumenter, der er krypteret af dine mærkater, skal du enten fjerne Azure Information Protection fra politikkerne for betinget adgang eller udelade eksterne brugere fra politikkerne.

Du kan få flere oplysninger om Betinget adgang og Azure Information Protection, den krypteringstjeneste, der bruges af følsomhedsmærkater, i det ofte stillede spørgsmål. [Jeg kan se, at Azure Information Protection er angivet som en tilgængelig cloudapp til betinget adgang – hvordan fungerer det?](/azure/information-protection/faqs#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work)

## <a name="when-office-apps-apply-content-marking-and-encryption"></a>Når Office apps anvender indholdsmarkering og kryptering

Office apps anvender indholdsmarkering og kryptering med en følsomhedsmærkat forskelligt, afhængigt af den app du bruger.

| App | Indholdsmarkering | Kryptering |
| --- | --- | --- |
| Word, Excel, PowerPoint på alle platforme | Straks | Straks |
| Outlook til pc og Mac | Når Exchange Online har sendt mailen | Straks |
| Outlook på internettet, iOS og Android | Når Exchange Online har sendt mailen | Når Exchange Online har sendt mailen |
|

Løsninger, der anvender følsomhedsmærkater på filer uden for Office apps, gør det ved at anvende mærkatmetadata på filen. I dette scenarie indsættes indholdsmarkering fra mærkatens konfiguration ikke i filen, men kryptering anvendes. 

Når disse filer åbnes i en Office desktopapp, anvendes indholdsmarkeringerne automatisk af Azure Information Protection Unified-navngivningsklienten, når filen gemmes første gang. Indholdsmarkeringer anvendes ikke automatisk, når du bruger indbygget mærkat til skrivebords-, mobil- eller webapps.

Scenarier, der omfatter anvendelse af en følsomhedsmærkat uden for Office apps, omfatter:

- Scanneren, Stifinder og PowerShell fra Azure Information Protection Unified Labeling-klienten 

- Politikker for automatisk mærkning af SharePoint og OneDrive

- Eksporterede navngivne og krypterede data fra Power BI

- Microsoft Defender for Cloud Apps

I disse scenarier kan en bruger med indbygget mærkat anvende mærkatens indholdsmarkeringer ved midlertidigt at fjerne eller erstatte den aktuelle etiket og derefter anvende den oprindelige mærkat midlertidigt ved hjælp af deres Office apps.

### <a name="dynamic-markings-with-variables"></a>Dynamiske markeringer med variabler

> [!IMPORTANT]
> Hvis dine Office apps ikke understøtter denne funktion, anvender de markeringerne som den oprindelige tekst, der er angivet i etiketkonfigurationen, i stedet for at løse variablerne.
> 
> Azure Information Protection Unified Labeling-klienten understøtter dynamiske markeringer. Hvis du vil have en mærkat, der er indbygget i Office, skal du se tabellerne i afsnittet [Egenskaber](#support-for-sensitivity-label-capabilities-in-apps) på denne side for at få vist de minimumversioner, der understøttes.

Når du konfigurerer en følsomhedsmærkat for indholdsmarkeringer, kan du bruge følgende variabler i tekststrengen til sidehovedet, sidefoden eller vandmærket:

| Variabel | Beskrivelse | Eksempel, når mærkat anvendes |
| -------- | ----------- | ------- |
| `${Item.Label}` | Vist navn for den anvendte etiket | **Generel**|
| `${Item.Name}` | Filnavn eller mailemne for det indhold, der forsynes med mærkater | **Sales.docx** |
| `${Item.Location}` | Sti og filnavn for det dokument, der forsynes med mærkater, eller mailemnet for en mail, der forsynes med mærkater | **\\\Sales\2020\Q3\Report.docx**|
| `${User.Name}` | Vist navn på den bruger, der anvender etiketten | **Richard Simone** |
| `${User.PrincipalName}` | Azure AD brugerens hovednavn (UPN) for den bruger, der anvender etiketten | **rsimone\@contoso.com** |
| `${Event.DateTime}` | Dato og klokkeslæt for, hvornår indholdet er mærket, i den lokale tidszone for den bruger, der anvender mærkaten i Microsoft 365 apps, eller UTC (Coordinated Universal Time) for Office Online- og automatisk navngivningspolitikker | **10-08-2020 kl. 13:30** |

> [!NOTE]
> Der skelnes mellem store og små bogstaver i syntaksen for disse variabler.

#### <a name="setting-different-visual-markings-for-word-excel-powerpoint-and-outlook"></a>Angivelse af forskellige visuelle markeringer for Word, Excel, PowerPoint og Outlook

Som en ekstra variabel kan du konfigurere visuelle markeringer pr. Office programtype ved hjælp af en variabelsætning af typen "If.App" i tekststrengen og identificere programtypen ved hjælp af værdierne **Word**, **Excel**, **PowerPoint** eller **Outlook**. Du kan også forkorte disse værdier, hvilket er nødvendigt, hvis du vil angive mere end én i den samme If.App sætning.

Brug følgende syntaks:

```
${If.App.<application type>}<your visual markings text> ${If.End}
```

På samme måde som med andre dynamiske visuelle markeringer skelnes der mellem store og små bogstaver i syntaksen, hvilket omfatter forkortelserne for hver programtype (WEPO).

Eksempler:

- **Angiv kun sidehovedtekst for Word-dokumenter:**

    `${If.App.Word}This Word document is sensitive ${If.End}`

    Kun i Word-dokumentoverskrifter anvender etiketten overskriftsteksten "Dette Word-dokument er følsomt". Der anvendes ingen overskriftstekst i andre Office programmer.

- **Angiv sidefodstekst for Word, Excel og Outlook og anden sidefodstekst for PowerPoint:**

    `${If.App.WXO}This content is confidential. ${If.End}${If.App.PowerPoint}This presentation is confidential. ${If.End}`

    I Word, Excel og Outlook anvender etiketten sidefodsteksten "Dette indhold er fortroligt". I PowerPoint anvender etiketten sidefodsteksten "Denne præsentation er fortrolig".

- **Angiv specifik vandmærketekst for Word og PowerPoint og derefter vandmærketekst til Word, Excel og PowerPoint:**

    `${If.App.WP}This content is ${If.End}Confidential`

    I Word og PowerPoint anvender etiketten vandmærketeksten "Dette indhold er fortroligt". I Excel anvender mærkaten vandmærketeksten "Fortroligt". I Outlook anvender etiketten ikke vandmærketekst, fordi vandmærker som visuelle markeringer ikke understøttes for Outlook.

## <a name="require-users-to-apply-a-label-to-their-email-and-documents"></a>Kræv, at brugerne anvender en mærkat på deres mail og dokumenter

> [!IMPORTANT]
> 
> [Azure Information Protection Unified Labeling-klienten](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) understøtter denne konfiguration, der også kaldes obligatorisk mærkning. Hvis du vil have en mærkat, der er indbygget i Office apps, skal du se tabellerne i afsnittet [Funktioner](#support-for-sensitivity-label-capabilities-in-apps) på denne side for at få vist minimumversioner.
>
> Hvis du vil bruge obligatorisk mærkning til dokumenter, men ikke mails, skal du se instruktionerne i næste afsnit, der forklarer, hvordan du konfigurerer Outlook specifikke indstillinger.
> 
> Hvis du vil bruge obligatorisk mærkning til Power BI, skal du se [Politik for obligatorisk mærkat for Power BI](/power-bi/admin/service-security-sensitivity-label-mandatory-label-policy).

Når politikindstillingen **Kræv, at brugerne anvender en mærkat på deres mail og dokumenter** er valgt, skal de brugere, der har fået tildelt politikken, vælge og anvende en følsomhedsmærkat under følgende scenarier:

- For Azure Information Protection Unified Labeling-klienten:
    - For dokumenter (Word, Excel, PowerPoint): Når et dokument uden mærkat gemmes, eller brugerne lukker dokumentet.
    - For mails (Outlook): På det tidspunkt, hvor brugerne sender en ikke-navngivet meddelelse.

- Til mærkning, der er indbygget i Office apps:
    - For dokumenter (Word, Excel, PowerPoint): Når et dokument uden mærkat åbnes eller gemmes.
    - For mails (Outlook): På det tidspunkt sender brugerne en ikke-navngivet mail.

Yderligere oplysninger om indbygget mærkning:

- Når brugerne bliver bedt om at tilføje en følsomhedsmærkat, fordi de åbner et ikke-navngivet dokument, kan de tilføje en mærkat eller vælge at åbne dokumentet i skrivebeskyttet tilstand.

- Når obligatorisk mærkning er i kraft, kan brugerne ikke fjerne følsomhedsmærkater fra dokumenter, men kan ændre en eksisterende mærkat.

- Når obligatorisk mærkning er i kraft, vil indstillingen Udskriv til PDF ikke være tilgængelig, når et dokument er mærket eller krypteret. Du kan få flere oplysninger i [afsnittet om understøttelse af PDF](#pdf-support) på denne side.

Du kan finde vejledning til, hvornår du skal bruge denne indstilling, i oplysningerne om [politikindstillinger](sensitivity-labels.md#what-label-policies-can-do).

> [!NOTE]
> Hvis du bruger standardindstillingen for mærkatpolitik for dokumenter og mails ud over obligatorisk mærkning: 
>
> Standardmærkaten har altid højere prioritet end obligatorisk mærkning. For dokumenter anvender Azure Information Protection Unified-mærkatklienten standardmærkaten på alle ikke-navngivne dokumenter, hvorimod indbygget mærkat anvender standardmærkaten på nye dokumenter og ikke på eksisterende dokumenter, der ikke er forsynet med mærkater. Denne forskel i funktionsmåde betyder, at når du bruger obligatorisk mærkning med standardmærkatindstillingen, bliver brugerne sandsynligvis bedt om at anvende en følsomhedsmærkat oftere, når de bruger indbygget mærkning, end når de bruger Azure Information Protection Unified Labeling-klienten.
> 
> Udrulles nu: Office apps, der bruger indbygget mærkning og understøtter et standardnavn for eksisterende dokumenter. Du kan finde flere oplysninger i [tabellen egenskaber](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) til Word, Excel og PowerPoint.

## <a name="outlook-specific-options-for-default-label-and-mandatory-labeling"></a>Outlook specifikke indstillinger for standardmærkat og obligatorisk mærkning

I forbindelse med indbygget mærkning skal du identificere minimumversionerne af Outlook, der understøtter disse funktioner, ved hjælp af [tabellen med egenskaber for Outlook](#sensitivity-label-capabilities-in-outlook) på denne side og rækken **Forskellige indstillinger for standardmærkat og obligatorisk mærkning**. Alle versioner af Azure Information Protection Unified Labeling-klienten understøtter disse Outlook specifikke muligheder.

Når Outlook app understøtter en standardnavnindstilling, der er forskellig fra standardindstillingen for mærkater for dokumenter:

- I konfigurationen af mærkatpolitikken fra Microsoft Purview-overholdelsesportalen på siden **Anvend en standardmærkat på mails** : Du kan angive dit valg af følsomhedsmærkat, der skal anvendes på alle ikke-navngivne mails, eller ingen standardmærkat. Denne indstilling er uafhængig af indstillingen **Anvend denne mærkat som standard på dokumenter** på den tidligere **politikindstilling for dokumentsiden** i konfigurationen.

Når Outlook app ikke understøtter en standardnavnindstilling, der er forskellig fra standardetiketindstillingen for dokumenter: Outlook vil altid bruge den værdi, du angiver for **Anvend denne etiket som standard på dokumenter** på siden **Politikindstillinger for dokumenter i** konfigurationen af mærkatpolitikken.

Når Outlook-appen understøtter deaktivering af obligatorisk mærkning:

- I konfigurationen af mærkatpolitikken fra Microsoft Purview-overholdelsesportalen skal du på siden **Politikindstillinger** : Vælg **Kræv, at brugerne anvender en mærkat på deres mail eller dokumenter**. Vælg derefter **Næste** > **næste** , og fjern markeringen i afkrydsningsfeltet **Kræv, at brugerne anvender en mærkat på deres mails**. Markér afkrydsningsfeltet, hvis du vil have, at obligatorisk mærkning skal gælde for mails og dokumenter.

Når Outlook app ikke understøtter deaktivering af obligatorisk mærkning: Hvis du vælger **Kræv, at brugerne anvender en mærkat på deres mail eller dokumenter** som en politikindstilling, vil Outlook altid bede brugerne om at vælge en mærkat til ikke-navngivne mails.

> [!NOTE]
> Hvis du har konfigureret de avancerede powershell-indstillinger **OutlookDefaultLabel** og **DisableMandatoryInOutlook** ved hjælp af Cmdlet'erne [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy) eller [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy) :
> 
> Dine valgte værdier for disse PowerShell-indstillinger afspejles i konfigurationen af mærkatpolitikken på Microsoft Purview-overholdelsesportalen, og de fungerer automatisk for Outlook apps, der understøtter disse indstillinger. De andre avancerede PowerShell-indstillinger understøttes fortsat kun for Azure Information Protection unified labeling-klienten.

## <a name="pdf-support"></a>Understøttelse af PDF

I forbindelse med indbygget mærkning skal du bruge tabellerne i afsnittet [egenskaber](#support-for-sensitivity-label-capabilities-in-apps) på denne side til at identificere understøttede minimumversioner. Azure Information Protection Unified Labeling-klienten understøtter ikke PDF i Office apps.

Word, Excel og PowerPoint understøtter følgende metoder til at konvertere et Office dokument til et PDF-dokument:

- Fil > Gem som > PDF 
- Eksportér > PDF-fil >
- Del > Send en kopi > PDF

Når PDF-filen oprettes, arver den etiketten med eventuelle indholdsmarkeringer og kryptering. Krypterede PDF-filer kan åbnes med Microsoft Edge på Windows eller Mac. Du kan finde flere oplysninger og alternative læsere under [Hvilke PDF-læsere understøttes for beskyttede PDF-filer?](/azure/information-protection/rms-client/protected-pdf-readers#viewing-protected-pdfs-in-microsoft-edge-on-windows-or-mac)


PDF-scenarier understøttes ikke:

- Udskriv til PDF
    
    Hvis brugerne vælger denne indstilling, bliver de advaret om, at dokumentet mister beskyttelsen af mærkaten og krypteringen (hvis den anvendes), og de skal bekræfte, at de vil fortsætte. Hvis politikken for følsomhedsmærkaten kræver begrundelse for at fjerne en mærkat eller sænke dens klassificering, får de vist denne prompt.
    
    Da denne indstilling fjerner følsomhedsmærkaten, vil denne indstilling ikke være tilgængelig for brugere, hvis du bruger obligatorisk mærkning. Denne konfiguration refererer til politikindstillingen for følsomhedsmærkat, der kræver, at brugerne anvender en mærkat på deres mails og dokumenter.

- PDF/A-format og kryptering
    
     Dette PDF-format, der er designet til langtidsarkivering, understøttes ikke, når mærkaten anvender encrytion og forhindrer brugerne i at konvertere Office dokumenter til PDF.
    
- Adgangskodebeskyttelse og kryptering
    
    Indstillingen **Filoplysninger** >  > **Beskyt****dokumentkryptering** >  med adgangskode understøttes ikke, når dokumentets mærkat anvender kryptering. I dette scenarie bliver indstillingen Kryptér med adgangskode ikke tilgængelig for brugerne.

Du kan finde flere oplysninger om denne funktion i meddelelsen [Anvend følsomhedsmærkater på PDF-filer, der er oprettet med Office apps](https://insider.office.com/blog/apply-sensitivity-labels-to-pdfs-created-with-office-apps).


## <a name="auditing-labeling-activities"></a>Overvågning af mærkataktiviteter

Du kan finde oplysninger om de overvågningshændelser, der genereres af aktiviteter for følsomhedsmærkater, i afsnittet [Aktiviteter for følsomhedsmærkat](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) under [Søg i overvågningsloggen på Microsoft Purview-overholdelsesportalen](search-the-audit-log-in-security-and-compliance.md).

Disse overvågningsoplysninger repræsenteres visuelt i [Indholdsoversigt](data-classification-content-explorer.md) og [Aktivitetsoversigt](data-classification-activity-explorer.md) for at hjælpe dig med at forstå, hvordan dine følsomhedsmærkater bruges, og hvor dette navngivne indhold er placeret. 

Du kan også oprette brugerdefinerede rapporter med dit valg af SIEM-software (Security Information And Event Management), når du [eksporterer og konfigurerer overvågningslogposterne](export-view-audit-log-records.md). Hvis du vil have mere omfattende rapporteringsløsninger, [skal du se api-referencen til Office 365 Management Activity](/office/office-365-management-api/office-365-management-activity-api-reference).

> [!TIP]
> Du kan få hjælp til at oprette brugerdefinerede rapporter i følgende blogindlæg:
> - [Aktiviteter i Microsoft Purview-overvågningsloggen via O365 Management API – del 1](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/microsoft-365-compliance-audit-log-activities-via-o365/ba-p/2957171)
> - [Aktiviteter i Microsoft Purview-overvågningsloggen via O365 Management API – del 2](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/microsoft-365-compliance-audit-log-activities-via-o365/ba-p/2957297)

## <a name="end-user-documentation"></a>Slutbrugerdokumentation

- [Anvend følsomhedsmærkater på dine filer og mails i Office](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [Kendte problemer med følsomhedsmærkater i Office](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Anvend eller anbefal automatisk følsomhedsmærkater på dine filer og mails i Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Kendte problemer med automatisk anvendelse eller anbefaling af følsomhedsmærkater](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)
