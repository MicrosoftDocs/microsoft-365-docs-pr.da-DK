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
description: Oplysninger, som it-administratorer kan bruge til at administrere følsomhedsmærkater Office apps til computer, mobil og internettet.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0ca67ecb87b48d551ec4fb740e8732b8196c872c
ms.sourcegitcommit: 7aa2441c1f2cc5b4b5495d6fdb993e563f86647f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64637912"
---
# <a name="manage-sensitivity-labels-in-office-apps"></a>Administrer følsomhedsmærkater i Office apps

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Når du har [](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) publiceret følsomhedsmærkater fra Microsoft 365 Overholdelsescenter eller tilsvarende mærkningscenter, begynder de at blive vist i Office-apps, hvor brugere kan klassificere og beskytte data, når de bliver oprettet eller redigeret.

Brug oplysningerne i denne artikel som en hjælp til at administrere følsomhedsmærkater i Office apps. Identificer f.eks. minimumversionerne af apps, du skal bruge for at understøtte indbygget mærkning, og forstå interaktionerne med den samlede Azure Information Protection-etiketklient og kompatibilitet med andre apps og tjenester.

## <a name="labeling-client-for-desktop-apps"></a>Klient til mærkning af skrivebordsapps

Hvis du vil bruge følsomhedsmærkater, der er indbygget Office skrivebordsapps til Windows og Mac, skal du bruge en abonnementsversion af Office. Denne etiketklient understøtter ikke enkeltstående udgaver af Office, også kaldet "Office tidsubetiske".

Hvis du ikke kan opgradere til Microsoft 365 Apps for enterprise for abonnementsversionerne af Office til Windows-computere, kan du bruge [Azure Information Protection samlet etiketklient](/azure/information-protection/rms-client/aip-clientv2).

## <a name="support-for-sensitivity-label-capabilities-in-apps"></a>Understøttelse af følsomhedsmærkatfunktioner i apps

For hver funktionalitet viser følgende tabeller minimumversionen Office, som du skal bruge til at understøtte følsomhedsmærkater ved hjælp af indbygget mærkning. Eller, hvis etiketfunktionaliteten er i offentlig prøveversion eller under gennemgang for en fremtidig version. Brug [oversigten Microsoft 365 for at](https://aka.ms/MIPC/Roadmap) få mere at vide om nye funktioner, der er planlagt til fremtidige udgivelser.

Nye versioner af Office apps bliver gjort tilgængelige på forskellige tidspunkter for forskellige opdateringskanaler. For Windows får du de nye funktioner tidligere, når du er på den aktuelle kanal eller månedlige virksomhedskanal, i stedet for Semi-Annual virksomhedskanal. Minimumsversionsnumrene kan også være forskellige fra én opdateringskanal til den næste. Få mere at vide under [Oversigt over opdateringskanaler til Microsoft 365 Apps](/deployoffice/overview-update-channels) [og Opdateringsoversigt for Microsoft 365 Apps](/officeupdates/update-history-microsoft365-apps-by-date).

Nye funktioner, der findes i privat eksempelvisning, er ikke inkluderet i tabellen, men du kan muligvis deltage i disse forhåndsvisninger ved at dominere din organisation [til det Microsoft Information Protection preview-program](https://aka.ms/mip-preview).

Office til iOS og Office til Android: Følsomhedsmærkater er indbygget i [Office-app](https://www.microsoft.com/en-us/microsoft-365/blog/2020/02/19/new-office-app-android-ios-available/).

Yderligere funktioner er tilgængelige, når du installerer Azure Information Protection samlet etiketklient, som kun kører på Windows computere. For at få mere at vide [skal du se Sammenligne etiketterne klienter for Windows computere](/azure/information-protection/rms-client/use-client#compare-the-labeling-clients-for-windows-computers).

> [!TIP]
> Når du sammenligner minimumversionerne i tabellerne med de versioner, du har, skal du huske den almindelige fremgangsmåde for udgivelsesversioner til at udelade foranstillede nuller.
> 
> Hvis du f.eks. har version 4.2128.0 og læser, at 4.7.1+ er minimumversionen. Læs 4.7.1 (ingen foranstillede nuller) som 4 for at lette sammenligningen. **0007.1** (og ikke 4.**7000,1**). Din version af 4.2128.0 er højere end 4.0007.1, så din version understøttes.

### <a name="sensitivity-label-capabilities-in-word-excel-and-powerpoint"></a>Følsomhedsmærkatfunktioner i Word, Excel og PowerPoint

De angivne tal er minimumskravet Office programversioner, der kræves til hver funktionalitet. 

> [!NOTE]
> For Windows og Semi-Annual Enterprise-kanalen er der muligvis endnu ikke frigivet de understøttede minimumsnumre. [Få mere at vide](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions)
 
|Funktion |Windows |Mac |iOS |Android |Web |
|-----------|-------:|----|----|--------|----|
|[Anvende, ændre eller fjerne etiket manuelt](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| Aktuel kanal: 1910+ <br /><br> Månedlig virksomhedskanal: 1910+ <br /><br> Semi-Annual virksomhedskanal: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Ja – tilmeld dig](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Anvende en standardetiket](sensitivity-labels.md#what-label-policies-can-do) på nye dokumenter                                         | Aktuel kanal: 1910+ <br /><br> Månedlig virksomhedskanal: 1910+ <br /><br> Semi-Annual virksomhedskanal: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Ja – tilmeld dig](sensitivity-labels-sharepoint-onedrive-files.md)                                                        |
|[Anvende en standardetiket](sensitivity-labels.md#what-label-policies-can-do) på eksisterende dokumenter | Forhåndsvisning: [Udrulning til aktuel kanal (forhåndsvisning)](https://office.com/insider) | Forhåndsvisning: [Udrulning til aktuel kanal (forhåndsvisning)](https://office.com/insider) | Under gennemgang | Under gennemgang | [Ja – tilmeld dig](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Kræve en justering for at ændre en etiket](sensitivity-labels.md#what-label-policies-can-do)                     | Aktuel kanal: 1910+ <br /><br> Månedlig virksomhedskanal: 1910+  <br /><br> Semi-Annual virksomhedskanal: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Ja – tilmeld dig](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Give hjælp-link til en brugerdefineret side i Hjælp](sensitivity-labels.md#what-label-policies-can-do)                       | Aktuel kanal: 1910+ <br /><br> Månedlig virksomhedskanal: 1910+ <br /><br> Semi-Annual virksomhedskanal: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Ja – tilmeld dig](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Markér indholdet](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | Aktuel kanal: 1910+ <br /><br> Månedlig virksomhedskanal: 1910+ <br /><br> Semi-Annual virksomhedskanal: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Ja – tilmeld dig](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Dynamiske markeringer med variabler](#dynamic-markings-with-variables)                                              | Aktuel kanal: 2010+ <br /><br> Månedlig virksomhedskanal: 2010+ <br /><br> Semi-Annual virksomhedskanal: 2102+ | 16.42+     | 2.42+ | 16.0.13328+ | [Ja – tilmeld dig](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Tildel tilladelser nu](encryption-sensitivity-labels.md#assign-permissions-now)                                 | Aktuel kanal: 1910+ <br /><br> Månedlig virksomhedskanal: 1910+ <br /><br> Semi-Annual virksomhedskanal: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Ja – tilmeld dig](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Lad brugere tildele tilladelser: <br /> - Spørg brugerne](encryption-sensitivity-labels.md#let-users-assign-permissions)                     |Aktuel kanal: 2004+ <br /><br> Månedlig virksomhedskanal: 2004+ <br /><br> Semi-Annual virksomhedskanal: 2008+ | 16.35+   | Under gennemgang   | Under gennemgang         | Under gennemgang                                                        |
|[Overvåge etiketrelateret brugeraktivitet](#auditing-labeling-activities)                      | Aktuel kanal: 2011+ <br /><br> Månedlig virksomhedskanal: 2011+ <br /><br> Semi-Annual virksomhedskanal: 2108+ | 16.43+ | 2.46+ | 16.0.13628+ | Ja |
|[Kræv, at brugerne anvender en etiket på deres mails og dokumenter](#require-users-to-apply-a-label-to-their-email-and-documents)   | Aktuel kanal: 2101+ <br /><br> Månedlig virksomhedskanal: 2101+ <br /><br> Semi-Annual virksomhedskanal: 2108+ | 16.45+         | 2.47+ | 16.0.13628+ | [Ja – tilmeld dig](sensitivity-labels-sharepoint-onedrive-files.md)                                            
|[Anvend automatisk en følsomhedsmærkat på indhold](apply-sensitivity-label-automatically.md) <br /> - Brug af følsomme oplysningstyper                    | Aktuel kanal: 2009+ <br /><br> Månedlig virksomhedskanal: 2009+ <br /><br> Semi-Annual virksomhedskanal: 2102+ | 16.44+ | Under gennemgang | Under gennemgang | [Ja – tilmeld dig](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Anvend automatisk en følsomhedsmærkat på indhold](apply-sensitivity-label-automatically.md) <br /> - Brug af klassekammerater, der kan trænes                    | Aktuel kanal: 2105+ <br /><br> Månedlig enterprise-kanal: 2105+ <br /><br> Semi-Annual virksomhedskanal: 2108+ | 16.49+ | Under gennemgang | Under gennemgang | [Ja – tilmeld dig](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Understøttelse af samtidig redigering og automatisk lagring af](sensitivity-labels-coauthoring.md) mærkede og krypterede dokumenter | Aktuel kanal: 2107+ <br /><br> Månedlig virksomhedskanal: 2107+ <br /><br> Semi-Annual virksomhedskanal: 2202+ |  16.51+ | Forhåndsvisning: 2,58 +, [når du tilmelder dig](sensitivity-labels-coauthoring.md#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) | Forhåndsvisning: 16.0.14931+, når [du tilmelder dig](sensitivity-labels-coauthoring.md#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) | [Ja – tilmeld dig](sensitivity-labels-sharepoint-onedrive-files.md) |


### <a name="sensitivity-label-capabilities-in-outlook"></a>Følsomhedsmærkatfunktioner i Outlook

De angivne tal er minimumskravet Office programversioner, der kræves til hver funktionalitet. 

> [!NOTE]
> For Windows og Semi-Annual Enterprise-kanalen er der muligvis endnu ikke frigivet de understøttede minimumsnumre. [Få mere at vide](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions)

|Funktion |Outlook til Windows |Outlook til Mac |Outlook på iOS |Outlook på Android |Outlook på internettet |
|-----------|-------------------:|----------------|---------------|-------------------|-------------------|
|[Anvende, ændre eller fjerne etiket manuelt](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| Aktuel kanal: 1910+ <br /><br> Månedlig virksomhedskanal: 1910+ <br /><br> Semi-Annual virksomhedskanal: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Ja               |
|[Anvend en standardetiket](sensitivity-labels.md#what-label-policies-can-do)                                         | Aktuel kanal: 1910+ <br /><br> Månedlig virksomhedskanal: 1910+ <br /><br> Semi-Annual virksomhedskanal: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Ja               |
|[Kræve en justering for at ændre en etiket](sensitivity-labels.md#what-label-policies-can-do)                     | Aktuel kanal: 1910+ <br /><br> Månedlig virksomhedskanal: 1910+ <br /><br> Semi-Annual virksomhedskanal: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Ja               |
|[Give hjælp-link til en brugerdefineret side i Hjælp](sensitivity-labels.md#what-label-policies-can-do)                       | Aktuel kanal: 1910+ <br /><br> Månedlig virksomhedskanal: 1910+ <br /><br> Semi-Annual virksomhedskanal: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Ja               |
|[Markér indholdet](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | Aktuel kanal: 1910+ <br /><br> Månedlig virksomhedskanal: 1910+ <br /><br> Semi-Annual virksomhedskanal: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Ja               |
|[Dynamiske markeringer med variabler](#dynamic-markings-with-variables)                                              | Aktuel kanal: 1910+ <br /><br> Månedlig virksomhedskanal: 1910+ <br /><br> Semi-Annual virksomhedskanal: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Ja               |
|[Tildel tilladelser nu](encryption-sensitivity-labels.md#assign-permissions-now)                                 | Aktuel kanal: 1910+ <br /><br> Månedlig virksomhedskanal: 1910+ <br /><br> Semi-Annual virksomhedskanal: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Ja               |
|[Lad brugere tildele tilladelser: <br /> - Videresende ikke](encryption-sensitivity-labels.md#let-users-assign-permissions)                     | Aktuel kanal: 1910+ <br /><br> Månedlig virksomhedskanal: 1910+ <br /><br> Semi-Annual virksomhedskanal: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Ja               |
|[Giv brugere tilladelse til at tildele tilladelser: <br /> - Kun krypteret](encryption-sensitivity-labels.md#let-users-assign-permissions)  | Aktuel kanal: 2011+ <br /><br> Månedlig virksomhedskanal: 2011+ <br /><br> Semi-Annual virksomhedskanal: 2108+ | 16.48+ <sup>\*</sup> | 4.2112.0+  | 4.2112.0+ | Ja |
|[Kræv, at brugerne anvender en etiket på deres mails og dokumenter](#require-users-to-apply-a-label-to-their-email-and-documents)   | Aktuel kanal: 2101+ <br /><br> Månedlig virksomhedskanal: 2101+ <br /><br> Semi-Annual virksomhedskanal: 2108+ | 16.43+ <sup>\*</sup>                    | 4.2111+            | 4.2111+                | Ja                |
|[Overvåge etiketrelateret brugeraktivitet](#auditing-labeling-activities) | Aktuel kanal: 2011+ <br /><br> Månedlig virksomhedskanal: 2011+ <br /><br> Semi-Annual virksomhedskanal: 2108+ | 16.51+ <sup>\*</sup> | 4.2126+ | 4.2126+ | Ja |
|[Anvend automatisk en følsomhedsmærkat på indhold](apply-sensitivity-label-automatically.md) <br /> - Brug af følsomme oplysningstyper                    | Aktuel kanal: 2009+ <br /><br> Månedlig virksomhedskanal: 2009+ <br /><br> Semi-Annual virksomhedskanal: 2102+ | 16.44+ <sup>\*</sup>                    | Under gennemgang           | Under gennemgang               | Ja |
|[Anvend automatisk en følsomhedsmærkat på indhold](apply-sensitivity-label-automatically.md) <br /> - Brug af klassekammerater, der kan trænes                    | Aktuel kanal: 2105+ <br /><br> Månedlig enterprise-kanal: 2105+ <br /><br> Semi-Annual virksomhedskanal: 2108+ | 16.49+ | Under gennemgang           | Under gennemgang               | Ja |
|[Forskellige indstillinger for standardetiket og obligatorisk mærkning](#outlook-specific-options-for-default-label-and-mandatory-labeling)                    | Aktuel kanal: 2105+ <br /><br> Månedlig enterprise-kanal: 2105+ <br /><br> Semi-Annual virksomhedskanal: 2108+ | 16.43+ <sup>\*</sup>                   | 4.2111+           | 4.2111+               | Ja |
|

**Fodnoter:**

<sup>\*</sup>Kræver den [nye Outlook til Mac](https://support.microsoft.com/office/the-new-outlook-for-mac-6283be54-e74d-434e-babb-b70cefc77439)


## <a name="office-built-in-labeling-client-and-other-labeling-solutions"></a>Office indbygget etiketklient og andre etiketløsninger

Den Office indbyggede etiketklient downloader følsomhedsmærkater og politikindstillinger for følsomhedsetiketter fra Microsoft 365 Overholdelsescenter. 

Hvis du Office den indbyggede etiketklient, skal du have publiceret en eller flere etiketpolitikker [](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) til brugere fra Overholdelsescenter og en understøttet [version af Office](#support-for-sensitivity-label-capabilities-in-apps).

Hvis begge disse betingelser er opfyldt, men du er nødt til at deaktivere de indbyggede etiketter i Windows Office-apps, skal du bruge Gruppepolitik indstilling:

1. Gå til **Brugerkonfiguration/Administrative skabeloner/Microsoft Office 2016/Security Indstillinger**.

2. **Indstil Brug funktionen Følsomhed i Office til at anvende og få vist følsomhedsmærkater** til **0**. 
 
Installér denne indstilling ved Gruppepolitik eller ved hjælp af Office [skypolitiktjeneste](/DeployOffice/overview-office-cloud-policy-service). Indstillingen træder i kraft, når disse Office apps genstarter. 

Da denne indstilling er specifik for Windows Office-apps, har den ingen indflydelse på andre apps på Windows, der understøtter følsomhedsetiketter (f.eks. Power BI) eller andre platforme (f.eks. macOS, mobilenheder og Office på internettet). Hvis du ikke vil have nogle eller alle brugere til at se og bruge følsomhedsmærkater på tværs af alle apps, alle platforme, skal du ikke tildele en følsomhedsmærkatpolitik til disse brugere. 

### <a name="office-built-in-labeling-client-and-the-azure-information-protection-client"></a>Office indbyggede etiketklient og Azure Information Protection-klienten

Hvis brugerne har [AIP-klienten (Azure Information Protection)](/azure/information-protection/rms-client/aip-clientv2) installeret på deres Windows-computere, deaktiveres indbyggede navne som standard i [Windows Office-apps](#labeling-client-for-desktop-apps), der understøtter dem. Da indbyggede etiketter ikke bruger et tilføjelse Office, som det bruges af AIP-klienten, har de fordelen af mere stabilitet og bedre ydeevne. De understøtter også de nyeste funktioner, f.eks. avancerede klassificeringer.

Du kan få mere at vide om valg af navne med AIP-klienten under Hvorfor vælge [Indbygget MIP-mærkning over AIP-tilføjelsesprogrammet til Office apps](sensitivity-labels-aip.md).

## <a name="office-file-types-supported"></a>Office understøttede filtyper

Office-apps, der har indbygget mærkning til Word-, Excel- og PowerPoint-filer, understøtter Open XML-formatet (f.eks. .docx og .xlsx), men ikke Microsoft Office 97-2003-formatet (f.eks. .doc- og .xls), Åbn dokumentformat (f.eks. .odt og .ods) eller andre formater. Når en filtype ikke understøttes til indbygget mærkning **, er knappen** Følsomhed ikke tilgængelig i Office-app.

Den samlede Information Protection Azure-etiketklient understøtter både Open XML-formatet og Microsoft Office 97-2003-format. Få mere at vide under [Filtyper, der understøttes af Azure Information Protection samlet](/azure/information-protection/rms-client/clientv2-admin-guide-file-types) etiketklient fra den pågældende klients administratorvejledning.

For andre etiketløsninger skal du kontrollere deres dokumentation for understøttede filtyper.

## <a name="protection-templates-and-sensitivity-labels"></a>Beskyttelsesskabeloner og følsomhedsmærkater

Administratordefinerede [beskyttelsesskabeloner](/azure/information-protection/configure-policy-templates), f.eks dem, du definerer til Office 365-meddelelseskryptering, er ikke synlige i Office-apps, når du bruger indbygget mærkning. Denne forenklede oplevelse afspejler, at der ikke er behov for at vælge en skabelon til beskyttelse, da de samme indstillinger er inkluderet i følsomhedsmærkater, der har kryptering aktiveret.

Du kan konvertere en eksisterende skabelon til et følsomhedsmærkat, når du bruger [New-Label-cmdlet'en](/powershell/module/exchange/new-label) med *parameteren EncryptionTemplateId* .

## <a name="information-rights-management-irm-options-and-sensitivity-labels"></a>IRM-indstillinger (Information Rights Management) og følsomhedsmærkater

Følsomhedsmærkater, du konfigurerer til at anvende kryptering, fjerner kompleksiteten fra brugerne for at angive deres egne krypteringsindstillinger. I mange Office-apps kan disse individuelle krypteringsindstillinger stadig konfigureres manuelt af brugerne ved hjælp af IRM-indstillinger (Information Rights Management). For eksempel til Windows apps:

- For et dokument: **FileInfoProtect** >  >  **DocumentRestrict Access** > 
- for en mail: Gå til **fanen Indstillinger,** og > **kryptér** 
  
Når brugerne første gang mærker et dokument eller en mail, kan de tilsidesætte konfigurationsindstillingerne for etiketter med deres egne krypteringsindstillinger. Eksempel:

- En bruger anvender navnet **Fortroligt \ Alle** medarbejdere på et dokument, og denne etiket er konfigureret til at anvende krypteringsindstillinger for alle brugere i organisationen. Denne bruger konfigurerer derefter manuelt IRM-indstillingerne for at begrænse adgangen til en bruger uden for organisationen. Slutresultatet er et dokument med navnet **Fortroligt \ Alle** medarbejdere og krypteret, men brugerne i organisationen kan ikke åbne det som forventet.

- En bruger anvender etiketten **Fortrolig \ Modtagere** kun på en mail, og denne mail er konfigureret til at anvende krypteringsindstillingen **Videressendelse ikke**. I Outlook, vælger denne bruger derefter manuelt IRM-indstillingen for Encrypt-Only. Det endelige resultat er, at mens mailen forbliver krypteret, kan den videresendes af modtagere på trods af etiketten **Fortrolige \** Modtagere kun.
    
    Som en undtagelse kan brugeren Outlook på internettet at vælge indstillingerne fra menuen Kryptér,  når den aktuelt valgte etiket anvender kryptering.

- En bruger anvender **den generelle** etiket i et dokument, og denne etiket er ikke konfigureret til at anvende kryptering. Denne bruger konfigurerer derefter manuelt IRM-indstillingerne for at begrænse adgangen til dokumentet. Det endelige resultat er et dokument, der hedder **Generelt** , men som også anvender kryptering, så nogle brugere ikke kan åbne det som forventet.

Hvis dokumentet eller mailen allerede er navnmærket, kan en bruger udføre en af disse handlinger, hvis indholdet ikke allerede er krypteret, eller de har brugsret [til Eksportér](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) eller Fuld kontrol. 

Du kan få en mere ensartet etiketoplevelse med meningsfuld rapportering ved at angive relevante etiketter og vejledning til brugerne, så de kun anvender navne for at beskytte dokumenter og mails. Eksempel:

- I undtagelsestilfælde, hvor brugerne skal tildele deres egne tilladelser, skal du angive etiketter [, der giver brugerne mulighed for at tildele deres egne tilladelser](encryption-sensitivity-labels.md#let-users-assign-permissions). 

- I stedet for at brugerne manuelt fjerner kryptering, når de har valgt en etiket, der anvender kryptering, skal du angive et alternativ undernavn, når brugerne skal bruge en etiket med den samme klassificering, men ingen kryptering. Det kan f.eks. være:
    - **Fortroligt \ Alle medarbejdere**
    - **Fortrolig \ Alle (ingen kryptering)**

- Overvej at deaktivere IRM-indstillinger for at forhindre brugere i at vælge dem:
    - Outlook til Windows: 
        - Registreringsdatabasenøgler (DWORD:00000001) *DisableDNF* og *DisableEO* HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\DRM
        - Kontrollér, at indstillingen Gruppepolitik **Konfigurer standardkrypteringsindstilling for knappen Kryptér** ikke er konfigureret
    - Outlook til Mac: 
        - Keys *DisableEncryptOnly* and *DisableDoNotForward* security settings documented in [Set preferences for Outlook til Mac](/DeployOffice/mac/preferences-outlook)
    - Outlook på internettet: 
        - Parametre *SimplifiedClientAccessDoNotForwardDisabled* og *SimplifiedClientAccessEncryptOnlyDisabled* dokumenteret for [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration)
    - Outlook til iOS og Android: Disse apps understøtter ikke brugere, der anvender kryptering uden etiketter, så der er intet at deaktivere.

> [!NOTE]
> Hvis brugerne manuelt fjerner kryptering fra et mærket dokument, der er gemt i SharePoint eller OneDrive, og du har aktiveret følsomhedsmærkater [for Office-filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md), gendannes etiketkryptering automatisk, næste gang dokumentet åbnes eller downloades. 


## <a name="apply-sensitivity-labels-to-files-emails-and-attachments"></a>Anvend følsomhedsmærkater på filer, mails og vedhæftede filer

Brugere kan kun anvende én etiket ad gangen for hvert dokument eller mail.

Når du navntager en mail, der indeholder vedhæftede filer, arver de vedhæftede filer kun navnet, hvis den etiket, du anvender på mailen, anvender kryptering, og den vedhæftede fil er et Office-dokument ikke allerede er krypteret. Da den nedarvede etiket anvender kryptering, bliver den vedhæftede fil nyligt krypteret.

En vedhæftet fil arver ikke etiketterne fra mailen, når den etiket, der er anvendt på mailen, ikke anvender kryptering, eller den vedhæftede fil allerede er krypteret.

Eksempler på nedarvning af navne, hvor **navnet Fortroligt** anvender kryptering, og etiketten **Generelt** anvender ikke kryptering:

- En bruger opretter en ny mail og anvender etiketten **Fortrolig** på denne meddelelse. De tilføjer derefter et Word-dokument, der ikke er mærket eller krypteret. Som et resultat af nedarvningen hedder dokumentet for nylig **Fortroligt og** får nu kryptering fra den pågældende etiket.

- En bruger opretter en ny mail og anvender etiketten **Fortrolig** på denne meddelelse. De tilføjer derefter et Word-dokument med navnet **Generelt** , og denne fil er ikke krypteret. Som et resultat af nedarvningen bliver dokumentet navnmærket **fortroligt, og** krypteringen anvendes nu fra den pågældende etiket.

## <a name="sensitivity-label-compatibility"></a>Følsomhedsmærkatkompatibilitet

**Med RMS-distribuerede apps**: Hvis du åbner et mærket og krypteret dokument eller mail i et [RMS-programmer](/azure/information-protection/requirements-applications#rms-enlightened-applications) , der ikke understøtter følsomhedsmærkater, gennemtvinger appen stadig kryptering og rettighedsstyring.

**Med Azure Information Protection-klienten**: Du kan få vist og ændre følsomhedsmærkater, som du anvender på dokumenter og mails med den indbyggede Office-etiketklient ved hjælp af Azure Information Protection-klienten og omvendt.

**Med andre versioner af Office**: Alle autoriserede brugere kan åbne dokumenter og mails med mærkater i andre versioner Office. Du kan dog kun se eller ændre navnet i understøttede Office versioner eller ved hjælp af Azure Information Protection-klienten. Understøttede Office-app versioner er angivet i [forrige afsnit](#support-for-sensitivity-label-capabilities-in-apps).

## <a name="support-for-sharepoint-and-onedrive-files-protected-by-sensitivity-labels"></a>Understøttelse af SharePoint og OneDrive filer, der er beskyttet af følsomhedsetiketter

Hvis du vil bruge den Office-indbyggede etiketklient med Office på internettet til dokumenter i SharePoint eller OneDrive, skal du kontrollere, at du har aktiveret følsomhedsmærkater [for Office-filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="support-for-external-users-and-labeled-content"></a>Understøttelse af eksterne brugere og mærket indhold

Når du navntager et dokument eller en mail, gemmes navnet som metadata, der omfatter din lejer og et mærkat-GUID. Når et mærket dokument eller mail åbnes af en Office-app, der understøtter følsomhedsmærkater, er disse metadata læst, og kun hvis brugeren tilhører den samme lejer, vises navnet i deres app. Eksempelvis vises navnet på statuslinjen i PowerPoint indbyggede PowerPoint Word samt Excel navnenavnet. 

Det betyder, at hvis du deler dokumenter med en anden organisation, der bruger forskellige navne, kan hver organisation anvende og se deres egen etiket anvendt på dokumentet. Følgende elementer fra en anvendt etiket er dog synlige for brugere uden for organisationen:

- Indholdsmærkninger. Når en etiket anvender et sidehoved, en sidefod eller et vandmærke, føjes disse direkte til indholdet og forbliver synlige, indtil nogen ændrer eller sletter dem.

- Navnet og beskrivelsen af den underliggende beskyttelsesskabelon fra en etiket, der anvendte kryptering. Disse oplysninger vises på en meddelelseslinje øverst i dokumentet for at angive oplysninger om, hvem der er autoriseret til at åbne dokumentet, og deres brugsrettigheder til det pågældende dokument.

### <a name="sharing-encrypted-documents-with-external-users"></a>Deling af krypterede dokumenter med eksterne brugere

Ud over at begrænse adgangen til brugere i din egen organisation kan du udvide adgangen for alle andre brugere, der har en konto Azure Active Directory. Men hvis din organisation bruger Betingede adgang-politikker, kan du se [yderligere overvejelser i](#conditional-access-policies) næste afsnit.

Alle Office apps og andre [RMS-godkendte](/azure/information-protection/requirements-applications#rms-enlightened-applications) programmer kan åbne krypterede dokumenter, når brugeren er godkendt. 

Hvis eksterne brugere ikke har en konto i Azure Active Directory, kan de godkende ved hjælp af gæstekonti i din lejer. Disse gæstekonti kan også bruges til at få adgang til delte dokumenter i SharePoint eller OneDrive, når du har aktiveret følsomhedsetiketter [til Office-filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md):

- En af muligheder er at oprette disse gæstekonti selv. Du kan angive en hvilken som helst mailadresse, som disse brugere allerede bruger. Deres Gmail-adresse.
    
    Fordelen ved denne indstilling er, at du kan begrænse adgang og rettigheder til bestemte brugere ved at angive deres mailadresse i krypteringsindstillingerne. Nedesiden er den faste administration ved oprettelse af konti og koordinering med etiketkonfigurationen.

- En anden mulighed er at [SharePoint og OneDrive integration med Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration), så gæstekonti automatisk oprettes, når brugerne deler links.
    
    Fordelen ved denne indstilling er et minimum af administrativt arbejde, da kontiene oprettes automatisk og er enklere etiketkonfiguration. I dette scenarie skal du vælge krypteringsindstillingen [](encryption-sensitivity-labels.md#requirements-and-limitations-for-add-any-authenticated-users) Tilføj en godkendt bruger, fordi du ikke kender mailadresserne på forhånd. Ulempen er, at denne indstilling ikke tillader, at du begrænser adgangs- og brugsrettigheder for bestemte brugere.

Eksterne brugere kan også bruge en Microsoft-konto til at åbne krypterede dokumenter, når de bruger Windows og Microsoft 365 Apps (tidligere [Office 365-apps](/deployoffice/name-change)) eller den enkeltstående udgave af Office 2019. Senest understøttet til andre platforme understøttes Microsoft-konti også til åbning af krypterede dokumenter på macOS (Microsoft 365 Apps, version 16.42+), Android (version 16.0.13029+ og iOS (version 2.42+). Eksempelvis deler en bruger i organisationen et krypteret dokument med en bruger uden for organisationen, og krypteringsindstillingerne angiver en Gmail-mailadresse for den eksterne bruger. Denne eksterne bruger kan oprette deres egen Microsoft-konto, der bruger deres Gmail-mailadresse. Derefter kan de, når de er logget på med denne konto, åbne dokumentet og redigere det i henhold til de forbrugsbegrænsninger, der er angivet for dem. Du kan finde et eksempel på dette scenarie under [Åbne og redigere det beskyttede dokument](/azure/information-protection/secure-collaboration-documents#opening-and-editing-the-protected-document).

> [!NOTE]
> Mailadressen til Microsoft-kontoen skal svare til den mailadresse, der er angivet for at begrænse adgangen til krypteringsindstillingerne.

Når en bruger med en Microsoft-konto åbner et krypteret dokument på denne måde, oprettes der automatisk en gæstekonto for lejeren, hvis en gæstekonto med det samme navn ikke allerede findes. Når gæstekontoen findes, kan den derefter bruges til at åbne dokumenter i SharePoint og OneDrive ved hjælp af Office på internettet foruden at åbne krypterede dokumenter fra de understøttede skrivebords- og Office-apps.

Den automatiske gæstekonto oprettes dog ikke med det samme i dette scenarie på grund af replikeringsventetid. Hvis du angiver personlige mailadresser som en del af dine indstillinger for etiketkryptering, anbefaler vi, at du opretter tilsvarende gæstekonti i Azure Active Directory. Fortæl derefter disse brugere, at de skal bruge denne konto for at åbne et krypteret dokument fra organisationen.

> [!TIP]
> Da du ikke kan være sikker på, at eksterne brugere vil bruge en understøttet Office-klientapp, deling af links fra SharePoint og OneDrive efter oprettelse af gæstekonti (for bestemte brugere), eller når du bruger SharePoint- og [OneDrive-integration med Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview)  (for alle godkendte brugere) er en mere pålidelig metode til at understøtte sikkert samarbejde med eksterne brugere.

### <a name="conditional-access-policies"></a>Politikker for betinget adgang

Hvis din organisation har implementeret [Azure Active Directory, skal](/azure/active-directory/conditional-access/overview) du kontrollere konfigurationen af disse politikker. Hvis politikkerne omfatter **Microsoft Azure Information Protection**, og politikken udvides til eksterne brugere, skal disse eksterne brugere have en gæstekonto i din lejer, også selvom de har en Azure AD-konto i deres egen lejer.

Uden denne gæstekonto kan de ikke åbne det krypterede dokument og få vist en fejlmeddelelse. Meddelelsesteksten kan informere dem om, at deres konto skal tilføjes som ekstern bruger i lejeren med den forkerte instruktion til dette scenarie for at logge af og logge på igen med en **anden Azure Active Directory-brugerkonto**.

Hvis du ikke kan oprette og konfigurere gæstekonti i din lejer for eksterne brugere, der skal åbne dokumenter, der er krypteret med dine etiketter, skal du enten fjerne Azure Information Protection fra politikkerne for Betinget adgang eller udelade eksterne brugere fra politikkerne.

Hvis du vil have mere at vide om Betinget adgang og Azure Information Protection, som er den krypteringstjeneste, der bruges af følsomhedsmærkater, skal du se det ofte stillede spørgsmål. Azure Information Protection er angivet som en tilgængelig [skyapp](/azure/information-protection/faqs#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work) til betinget adgang – hvordan fungerer det?

## <a name="when-office-apps-apply-content-marking-and-encryption"></a>Når Office anvender apps indholdsmærkning og -kryptering

Office apps anvender indholdsmærkning og kryptering med en følsomhedsmærkat anderledes, afhængigt af den app du bruger.

| App | Indholdsmærkning | Kryptering |
| --- | --- | --- |
| Word, Excel, PowerPoint på alle platforme | Straks | Straks |
| Outlook til pc og Mac | Når Exchange Online sender mailen | Straks |
| Outlook på internettet, iOS og Android | Når Exchange Online sender mailen | Når Exchange Online sender mailen |
|

Løsninger, der anvender følsomhedsetiketter på filer Office apps gør det ved at anvende mærkning af metadata på filen. I dette scenarie indsættes indholdsmærkning fra etikettens konfiguration ikke i filen, men krypteringen anvendes. 

Når disse filer åbnes i en Office-skrivebordsapp, anvendes indholdsmærkningerne automatisk af Azure Information Protection Unified LabelIng Client, når filen gemmes første gang. Indholdsmærkning anvendes ikke automatisk, når du bruger indbygget mærkning til skrivebords-, mobil- eller webapps.

Scenarier, der omfatter anvendelse af et følsomhedsmærkat uden for Office apps, omfatter:

- Scanner, Stifinder og PowerShell fra Azure Information Protection samlet etiketklient 

- Politikker for automatisk mærkatering for SharePoint og OneDrive

- Eksporterede mærkede og krypterede data fra Power BI

- Microsoft Defender for Cloud Apps

I disse situationer kan en bruger med indbygget mærkning anvende etikettens indholdsmærkninger ved at fjerne eller erstatte den aktuelle etiket og derefter anvende den oprindelige etiket igen ved hjælp af deres Office-apps.

### <a name="dynamic-markings-with-variables"></a>Dynamiske markeringer med variabler

> [!IMPORTANT]
> Hvis dine Office-apps ikke understøtter denne funktion, anvender de markeringerne som den oprindelige tekst, der er angivet i etiketkonfigurationen, i stedet for at løse variablerne.
> 
> Azure Information Protection samlet etiketklient understøtter dynamiske mærkninger. Du kan finde oplysninger om at Office i tabellerne i sektionen med egenskaber på denne [](#support-for-sensitivity-label-capabilities-in-apps) side for minimumversioner, der understøttes.

Når du konfigurerer et følsomhedsmærkat for indholdsmærkning, kan du bruge følgende variabler i tekststrengen til dit sidehoved, din sidefod eller dit vandmærke:

| Variabel | Beskrivelse | Eksempel, hvor der anvendes etiket |
| -------- | ----------- | ------- |
| `${Item.Label}` | Visningsnavnet på den etiket, der er anvendt på etiketten | **Generel**|
| `${Item.Name}` | Filnavn eller mailens emne for det indhold, der navngives | **Sales.docx** |
| `${Item.Location}` | Sti og filnavn på det dokument, der navngives, eller mailens emne for en mail, der navngives | **\\\Sales\2020\Q3\Report.docx**|
| `${User.Name}` | Visningsnavn på den bruger, der anvender etiketten | **Richard Dens ærger** |
| `${User.PrincipalName}` | Azure AD brugerens hovednavn (UPN) for den bruger, der anvender etiketten | **rsimone\@ contoso.com** |
| `${Event.DateTime}` | Dato og klokkeslæt for mærkat for indholdet i den lokale tidszone for den bruger, der anvender etiketten i Microsoft 365-apps, eller UTC (Coordinated Universal Time) for Office Online og politikker for automatisk mærkning | **10-08-2020 13:30** |

> [!NOTE]
> Der er store og små bogstaver i syntaksen for disse variabler.

#### <a name="setting-different-visual-markings-for-word-excel-powerpoint-and-outlook"></a>Indstilling af forskellige visuelle markeringer for Word, Excel, PowerPoint og Outlook

Som en ekstra variabel kan du konfigurere visuelle mærkninger pr. Office-programtype ved hjælp af en "If.App"-variabeludtog i tekststrengen og identificere programtypen ved hjælp af værdierne **Word**, **Excel**, **PowerPoint** **eller Outlook**. Du kan også forkorte disse værdier, hvilket er nødvendigt, hvis du vil angive mere end én i den samme If.App sætning.

Brug følgende syntaks:

```
${If.App.<application type>}<your visual markings text> ${If.End}
```

Som med de andre dynamiske visuelle mærkninger er der store og små bogstaver i syntaksen, der indeholder forkortelserne for hver programtype (WEPO).

Eksempler:

- **Angiv kun overskriftstekst for Word-dokumenter:**

    `${If.App.Word}This Word document is sensitive ${If.End}`

    I Word-dokumentoverskrifter anvender navnet sidehovedteksten "Dette Word-dokument er følsomt". Der anvendes ingen overskriftstekst på Office programmer.

- **Angiv tekst i sidefoden i Word, Excel og Outlook samt forskellig tekst i sidefoden til PowerPoint:**

    `${If.App.WXO}This content is confidential. ${If.End}${If.App.PowerPoint}This presentation is confidential. ${If.End}`

    I Word, Excel og Outlook anvender etiketten sidefodsteksten "Dette indhold er fortroligt". I PowerPoint anvender etiketten teksten i sidefoden "Denne præsentation er fortrolig".

- **Angiv en bestemt vandmærketekst for Word og PowerPoint og derefter vandmærketekst for Word, Excel og PowerPoint:**

    `${If.App.WP}This content is ${If.End}Confidential`

    I Word og PowerPoint tekst anvender etiketten vandmærketeksten "Dette indhold er fortroligt". I Excel anvender etiketten vandmærketeksten "Fortroligt". I Outlook anvender etiketten ikke nogen vandmærketekst, da vandmærker som visuelle markeringer ikke understøttes i Outlook.

## <a name="require-users-to-apply-a-label-to-their-email-and-documents"></a>Kræv, at brugerne anvender en etiket på deres mails og dokumenter

> [!IMPORTANT]
> 
> Azure [Information Protection samlet etiketklient understøtter](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) denne konfiguration, der også kaldes obligatorisk mærkning. Hvis du vil have oplysninger om at Office indbygget i apps, skal du se [tabellerne](#support-for-sensitivity-label-capabilities-in-apps) i sektionen med egenskaber på denne side for minimumversioner.
>
> Hvis du vil bruge obligatorisk mærkning til dokumenter, men ikke mails, skal du se instruktionerne i næste afsnit, som forklarer, Outlook konfigurerer bestemte indstillinger.
> 
> Hvis du vil bruge obligatorisk mærkning til Power BI, skal du se [Obligatorisk etiketpolitik for Power BI](/power-bi/admin/service-security-sensitivity-label-mandatory-label-policy).

Når politikindstillingen **Kræv** , at brugere anvender en etiket på deres mail og dokumenter er markeret, skal de brugere, der er tildelt politikken, vælge og anvende en følsomhedsmærkat under følgende scenarier:

- Til Azure Information Protection samlet etiketklient:
    - For dokumenter (Word, Excel, PowerPoint): Når et dokument uden navn gemmes, eller brugere lukker dokumentet.
    - For mails (Outlook): På det tidspunkt sender brugerne en meddelelse uden navn.

- Til mærkning indbygget i Office apps:
    - For dokumenter (Word Excel, PowerPoint): Når et dokument uden navn åbnes eller gemmes.
    - For mails (Outlook): På det tidspunkt sender brugerne en mail uden navn.

Flere oplysninger til indbygget mærkning:

- Når brugerne bliver bedt om at tilføje en følsomhedsmærkat, fordi de åbner et dokument uden navn, kan de tilføje en etiket eller vælge at åbne dokumentet i skrivebeskyttet tilstand.

- Når obligatorisk mærkning er i kraft, kan brugerne ikke fjerne følsomhedsmærkater fra dokumenter, men kan ændre en eksisterende etiket.

Du kan finde en vejledning til, hvornår du skal bruge denne indstilling, i oplysningerne [om politikindstillinger](sensitivity-labels.md#what-label-policies-can-do).

> [!NOTE]
> Hvis du bruger standardindstillingen for etiketpolitik for dokumenter og mails ud over obligatorisk mærkning: 
>
> Standardetiketten prioriteres altid frem for obligatorisk mærkning. Men for dokumenter anvender Azure Information Protection unified labeling-klienten standardnavnet på alle dokumenter uden navn, hvorimod indbygget mærkning anvender standardnavnet på nye dokumenter og ikke på eksisterende dokumenter, der ikke er navnmærket. Denne forskel i funktionsmåden betyder, at når du bruger obligatorisk mærkning med standardmærkatindstillingen, vil brugerne sandsynligvis blive bedt om at anvende et følsomhedsmærkat oftere, når de bruger indbygget mærkning, end når de bruger Azure Information Protection Unified Labeling-klienten.
> 
> Nu udrulles: Office, der bruger indbygget mærkning og understøtter en standardmærkat for eksisterende dokumenter. Du kan finde flere [oplysninger i tabellen med](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) egenskaber for Word, Excel og PowerPoint.

## <a name="outlook-specific-options-for-default-label-and-mandatory-labeling"></a>Outlook specifikke indstillinger for standardetiket og obligatorisk mærkning

For indbygget mærkning skal du identificere minimumversionerne af Outlook, der understøtter disse funktioner, ved hjælp af tabellen med egenskaber [for Outlook](#sensitivity-label-capabilities-in-outlook) på denne side og rækken Forskellige indstillinger **for** standardetiket og obligatorisk mærkning. Alle versioner af den samlede Information Protection Azure-etiketklient understøtter Outlook specifikke indstillinger.

Når appen Outlook understøtter en standardetiketindstilling, der er forskellig fra standardetiketindstillingen for dokumenter:

- I konfigurationen af etiketpolitik fra Microsoft 365 Overholdelsescenter på siden Anvend en standardmærkat på mails: Du kan angive dit valg af følsomhedsmærkat, der vil blive anvendt på alle mails uden navn eller ingen standardmærkat. Denne indstilling er uafhængig af indstillingen **Anvend denne etiket som standard** på dokumenter på den **forrige politikindstilling for siden** dokumenter i konfigurationen.

Når Outlook-appen ikke understøtter en standardetiketindstilling, der er forskellig fra standardetiketindstillingen for dokumenter: Outlook bruger altid den værdi, du **angiver for Anvend** denne etiket som standard på dokumenter på siden Politikindstillinger **for** dokumenter i konfigurationen af etiketpolitikken.

Når appen Outlook deaktiverer obligatorisk mærkning:

- I konfigurationen af etiketpolitikken på Microsoft 365 Overholdelsescenter siden Politikindstillinger: Vælg Kræv, at brugerne anvender en etiket **på deres mail eller dokumenter**. Vælg derefter **NextNext** > , og fjern markeringen i afkrydsningsfeltet **Kræv, at brugerne anvender en etiket på deres mails**. Sørg for, at afkrydsningsfeltet er markeret, hvis du ønsker, at obligatorisk mærkning skal gælde for mails og dokumenter.

Når Outlook-appen ikke understøtter de aktivering af obligatorisk mærkning: Hvis du vælger Kræv, at  brugerne anvender en etiket på deres mails eller dokumenter som en politikindstilling, vil Outlook altid bede brugerne om at vælge en etiket til mails uden navn.

> [!NOTE]
> Hvis du har konfigureret avancerede indstillinger for PowerShell **outlookDefaultLabel** og **DisableMandatoryInOutlook** ved hjælp af [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy) - eller [New-LabelPolicy-cmdlet'erne](/powershell/module/exchange/new-labelpolicy) :
> 
> Dine valgte værdier for disse PowerShell-indstillinger afspejles i konfigurationen af etiketpolitikken i overholdelsescenteret, og de fungerer automatisk for Outlook-apps, der understøtter disse indstillinger. De andre avancerede PowerShell-indstillinger understøttes fortsat kun for Azure Information Protection samlet etiketklient.

## <a name="auditing-labeling-activities"></a>Overvågning af etiketaktiviteter

Du kan finde oplysninger om de overvågningshændelser, der genereres af følsomhedsmærkataktiviteter, i afsnittet Følsomhedsmærkataktiviteter i Søg i overvågningsloggen [i overholdelsescenteret](search-the-audit-log-in-security-and-compliance.md).[](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities)

Disse revisionsoplysninger er visuelt repræsenteret i Indholdsstifinder og Aktivitetsstifinder for at hjælpe dig med at forstå, hvordan dine følsomhedsmærkater bruges, og hvor det mærkede indhold er placeret.[](data-classification-content-explorer.md) [](data-classification-activity-explorer.md) 

Du kan også oprette brugerdefinerede rapporter med dit valg af sikkerhedsoplysninger og begivenhedsstyringssoftware (SIEM), når du eksporterer og [konfigurerer overvågningslogposterne](export-view-audit-log-records.md). Du kan finde større rapporteringsløsninger i [Office 365 Management Activity API](/office/office-365-management-api/office-365-management-activity-api-reference).

> [!TIP]
> Se følgende blogindlæg for at oprette brugerdefinerede rapporter:
> - [Microsoft 365 af overvågningslogfiler til overholdelse af regler og standarder via O365 Management API – Del 1](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/microsoft-365-compliance-audit-log-activities-via-o365/ba-p/2957171)
> - [Microsoft 365 af overvågningslogfiler til overholdelse via O365 Management API – Del 2](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/microsoft-365-compliance-audit-log-activities-via-o365/ba-p/2957297)

## <a name="end-user-documentation"></a>Slutbrugerdokumentation

- [Anvend følsomhedsmærkater på dine filer og mails i Office](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [Kendte problemer med følsomhedsetiketter i Office](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Anvend eller anbefal automatisk følsomhedsetiketter til dine filer og mails i Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Kendte problemer med automatisk anvendelse eller anbefaling af følsomhedsmærkater](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)
