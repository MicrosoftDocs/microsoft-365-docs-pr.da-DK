---
title: Aktivér samtidig redigering for dokumenter, der er krypteret med følsomhedsetiketter i Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
ms.topic: article
description: Aktivér en indstilling, der aktiverer samtidig redigering og automatisk lagring i skrivebordsapps for mærkede og krypterede dokumenter i SharePoint og OneDrive.
ms.openlocfilehash: 252d32e0f301bf332bf8143082ec86be2f1072ea
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592592"
---
# <a name="enable-co-authoring-for-files-encrypted-with-sensitivity-labels"></a>Aktivere samtidig redigering for filer, der er krypteret med følsomhedsmærkater

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Aktivér indstillingen for at understøtte samtidig redigering af [Office-skrivebordsapps](https://support.office.com/article/ee1509b4-1f6e-401e-b04a-782d26f564a4)[, så](sensitivity-labels.md) når dokumenter mærkes og krypteres med følsomhedsmærkater, kan flere brugere redigere disse dokumenter på samme tid.

Uden denne indstilling er aktiveret for din lejer, skal brugerne tjekke et krypteret dokument ud, der er gemt i SharePoint eller OneDrive, når de bruger Office-skrivebordsapps. De kan derfor ikke samarbejde i realtid. Eller, de skal bruge en Office på internettet, [når følsomhedsetiketter er aktiveret til Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

Desuden medfører aktivering af denne funktionalitet, at funktionen [Automatisk lagring understøttes](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) for disse mærkede og krypterede filer.

Du kan læse udgivelsesmeddelelsen i [blogindlægget Samtidig redigering på Microsoft Information Protection krypterede dokumenter er nu generelt tilgængeligt](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/co-authoring-on-microsoft-information-protection-encrypted/ba-p/2693718).

## <a name="metadata-changes-for-sensitivity-labels"></a>Ændringer af metadata for følsomhedsmærkater

> [!IMPORTANT]
> Når du har aktiveret indstillingen for samtidig redigering, gemmes etiketoplysninger for ikke-krypterede filer ikke længere i brugerdefinerede egenskaber.
> 
> Du skal ikke aktivere denne indstilling, hvis du bruger apps, tjenester, scripts eller værktøjer, der læser eller skriver mærkning af metadata til den gamle placering.

Før du aktiverer indstillingen til understøttelse af samtidig redigering af Office-skrivebordsapps, er det vigtigt at forstå, at denne handling foretager ændringer i mærkningen af metadata, der gemmes i og læses fra Office-filer.

Mærkningen af metadata indeholder oplysninger, der identificerer din lejer og anvendt følsomhedsmærkat. Den ændring, denne indstilling foretager, er metadataformatet og placeringen for Word-, Excel- og PowerPoint filer. Du behøver ikke at gøre noget for krypterede filer eller mails, fordi metadataændringen for krypterede filer er bagudkompatibel, og der er ingen ændringer for mails. Du skal dog være opmærksom på metadataændringer for krypterede filer, der kan opgraderes automatisk, men ikke er bagudkompatible.

Denne ændring påvirker både filer, der er for nyligt navnmærket, og filer, der allerede er navnmærket. Når du bruger apps og tjenester, der understøtter indstillingen for samtidig redigering:
- For filer, der nyligt navnmærkes, bruges kun det nye format og den nye placering til mærkning af metadata.
- For filer, der allerede er navnmærket, kopieres disse oplysninger til det nye format og den nye placering, næste gang filen åbnes og gemmes, hvis filen har metadata i det gamle format og den gamle placering.

Du kan læse mere om denne metadataændring fra følgende ressourcer:

- Blogindlæg: [Kommende ændringer af Microsoft Information Protection metadata Storage](https://techcommunity.microsoft.com/t5/microsoft-security-and/upcoming-changes-to-microsoft-information-protection-metadata/ba-p/1904418)

- Åbne specifikationer: [2.6.3 LabelInfo kontra brugerdefinerede dokumentegenskaber](/openspecs/office_file_formats/ms-offcrypto/13939de6-c833-44ab-b213-e0088bf02341)

På grund af disse ændringer skal du ikke aktivere denne indstilling, hvis du har apps, tjenester, scripts eller værktøjer i organisationen, der læser eller skriver mærkning af metadata til den gamle placering. Hvis du gør det, kan du se nogle eksempler på konsekvenser:

- Et dokument, der er mærket, ser ud til, at brugerne ikke har en mærkat.

- Et dokument viser en forældet etiket til brugerne.

- Samtidig redigering og automatisk lagring fungerer ikke for et mærket og krypteret dokument, hvis en anden bruger har det åbent i en Office-skrivebordsapp, der ikke understøtter de nye metadata ved mærkning. Vær opmærksom på, at dette scenarie også kan opstå for brugere uden for organisationen, hvis eksterne brugere og inviterede gæster har filen åben.

- En Exchange Online regel for mailflow, der identificerer navne som brugerdefinerede egenskaber [i vedhæftede Office](/azure/information-protection/configure-exo-rules#example-2-rule-that-applies-the-encrypt-only-option-to-emails-when-they-have-attachments-that-are-labeled-confidential--partners-and-these-emails-are-sent-outside-the-organization) ikke krypterer mailen og den vedhæftede fil eller krypterer dem forkert.

Se det følgende afsnit for at få en liste over apps og tjenester, der understøtter denne indstilling, samt ændringer af metadataene med mærkning.

## <a name="prerequisites"></a>Forudsætninger

> [!IMPORTANT]
> Denne funktion kræver, at alle brugere har Microsoft 365 Apps for enterprise. Understøttelse af denne funktion til samtidig redigering er endnu ikke tilgængelig med den Semi-Annual Enterprise-kanal for at få Office opdateringer. Hvis du bruger denne opdateringskanal til dine Office, skal du ændre den til Aktuel kanal eller Månedlig virksomhedskanal.
> 
> Du kan få mere at vide [under Sådan konfigurerer og administrerer du opdateringskanaler](/deployoffice/overview-update-channels#how-to-configure-and-manage-update-channels).

Sørg for, at du har forstået følgende forudsætninger, før du aktiverer denne funktion.

- Du skal være global administrator for at aktivere denne funktion.

- Følsomhedsmærkater [skal være aktiveret Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) for lejeren. Hvis denne funktion ikke allerede er aktiveret, bliver den automatisk aktiveret, når du vælger indstillingen for at aktivere samtidig redigering for filer med følsomhedsmærkater.

- Microsoft 365 Apps for enterprise:
    - **Windows**: Minimumsversion 2107 fra Aktuel kanal eller Månedlig virksomhedskanal
    - **macOS**: Minimumversion 16.51
    - **iOS**: Nu i forhåndsvisning, [når du tilmelder](#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) dig med minimum version 2.58
    - **Android**: Nu i forhåndsvisning, [når du tilmelder](#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) dig med minimumversion 16.0.14931

- Alle apps, tjenester og driftsværktøjer i din lejer skal understøtte de nye [metadata ved mærkning](#metadata-changes-for-sensitivity-labels). Hvis du bruger en af følgende, skal du kontrollere minimumversionerne, der kræves:
    
    - **Azure Information Protection samlet etiketklient og scanner:**
        - Minimumsversion [2.12.62.0](/information-protection/rms-client/unifiedlabelingclient-version-release-history#version-212620) , som du kan installere fra [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018)
    
    - **OneDrive-synkronisering-app til Windows eller macOS:**
        - Minimumsversion af 19.002.0121.0008
    
    - **Forebyggelse af datatab på slutpunkt (slutpunkt DLP):**
        - Windows 10 1809 med KB 4601383
        - Windows 10 1903 og 1909 med KB 4601380
        - Windows 10 2004 med KB 4601382
        - Windows versioner, der er nyere Windows 10 2004, understøttes uden KB-opdateringer
    
    - **Apps og tjenester, der bruger Microsoft Information Protection SDK:** 
        - Minimumversion af 1.7 

Microsoft 365-tjenester understøtter automatisk de nye metadata, når du aktiverer denne funktion. Eksempel:

- [Politikker for automatisk mærkning](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)
- [DLP-politikker, der bruger følsomhedsmærkater som betingelser](dlp-sensitivity-label-as-condition.md)
- [Microsoft Defender til skyapps konfigureret til at anvende følsomhedsmærkater](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)

### <a name="opt-in-to-the-preview-of-co-authoring-for-ios-and-android"></a>Tilmeld dig forhåndsvisningen af samtidig redigering til iOS og Android

Hvis du vil prøve eksempelvisningen af samtidig redigering til iOS og Android, skal du have de minimumsversioner, der er angivet i forrige afsnit, og du skal også anmode om, at din lejer føjes til forhåndsvisningen: Samtykke til at aktivere samtidig redigering af filer, der er krypteret med følsomhedsetiketter på [mobil](https://ncv.microsoft.com/5Oob3oDj1O)

Du kan finde flere oplysninger i følgende meddelelse i blogindlægget: Samtidig redigering på Microsoft Information Protection-krypterede dokumenter er nu i [offentlig prøveversion på mobilenheder](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/co-authoring-on-microsoft-information-protection-encrypted/ba-p/3081369)

## <a name="limitations"></a>Begrænsninger

Før du aktiverer lejerindstillingen for samtidig redigering for filer, der er krypteret med følsomhedsmærkater, skal du sørge for at forstå følgende begrænsninger i denne funktion.

- På grund af [ændringer af metadata](#metadata-changes-for-sensitivity-labels) med mærkater skal alle apps, tjenester og driftsværktøjer i din lejer understøtte de nye etiketmetadata for at få en ensartet og pålidelig etiketoplevelse.
    
    Specifikt for Excel: Metadata for en følsomhedsmærkat, der ikke anvender kryptering, kan slettes fra en fil, hvis nogen redigerer og gemmer filen ved hjælp af en version af Excel, der ikke understøtter ændringer af metadata for følsomhedsmærkater.

- Understøttende Office til iOS og Android er i øjeblikket en [prøveversion](https://office.com/insider).

- Samtidig redigering og automatisk lagring understøttes ikke og virker ikke for mærkede og krypterede dokumenter, Office bruger nogen af følgende [konfigurationer til kryptering](encryption-sensitivity-labels.md#configure-encryption-settings):
    - **Lad brugere tildele tilladelser**, når de anvender etiketten, og afkrydsningsfeltet i **Word, PowerPoint og Excel skal** du bede brugerne om at angive tilladelser er markeret. Denne konfiguration kaldes sommetider for "brugerdefinerede tilladelser".
    - **Brugeradgang til indhold, der udløber,** er angivet til en anden værdi end **Aldrig**.
    - **Dobbelt nøglekryptering** er valgt.
    
    For etiketter med enhver af disse krypteringskonfigurationer vises etiketterne i Office apps. Men når brugere vælger disse navne, og ingen andre redigerer dokumentet, advares de om, at samtidig redigering og automatisk lagring ikke er tilgængelig. Hvis en anden redigerer dokumentet, får brugerne vist en meddelelse om, at etiketterne ikke kan anvendes.

- Hvis du bruger den samlede Azure Information Protection-etiketklient: Kontrollér dokumentationen for denne etiketklient for flere [krav eller begrænsninger](/azure/information-protection/known-issues#known-issues-for-co-authoring). 
    > [!NOTE]
    > Disse begrænsninger for den samlede etiketklient omfatter en ændring af [dialogboksen for brugere](/azure/information-protection/known-issues#user-interface-changes-when-applying-labels) , der vælger navne, der beder dem om at vælge tilladelser.

## <a name="how-to-enable-co-authoring-for-files-with-sensitivity-labels"></a>Sådan aktiveres samtidig redigering for filer med følsomhedsmærkater

> [!CAUTION]
> Aktivering af denne indstilling er en envejshandling. Aktivér den først, når du har læst og forstået metadataændringerne, forudsætningerne, begrænsningerne og eventuelle kendte problemer, der er dokumenteret på denne side.

Hvis du allerede har aktiveret denne indstilling i løbet af eksempelperioden, er der ikke behov for yderligere handling, og du kan springe denne procedure over.

1. Log [på Microsoft 365 Overholdelsescenter global](https://compliance.microsoft.com) administrator for din lejer.

2. I navigationsruden skal **du vælge Indstillinger** >  **Co-authoring for filer med følsomhedsfiler**.

2. På siden **Samtidig redigering af** filer med følsomhedsetiketter kan du læse oversigtsbeskrivelsen, forudsætninger, hvad du kan forvente, og advarslen om, at du ikke kan deaktivere denne indstilling, når du har aktiveret den.
    
    Vælg derefter **Slå samtidig redigering til for filer med følsomhedsmærkater**, og **Anvend**:
    
    ![Mulighed for at aktivere samtidig redigering for filer med følsomhedsmærkater.](../media/co-authoring-tenant-option-for-sensitivity-labels.png)

3. Vent 24 timer på, at denne indstilling replikeres på tværs af dit miljø, før du bruger denne nye funktion til samtidig redigering.

## <a name="contact-support-if-you-need-to-disable-this-feature"></a>Kontakt support, hvis du har brug for at deaktivere denne funktion

> [!IMPORTANT]
> Hvis du har brug for at deaktivere denne funktion, skal du være opmærksom på, at navneoplysninger kan gå tabt.

Når du har aktiveret samtidig redigering af filer med følsomhedsetiketter for din lejer, kan du ikke selv deaktivere denne indstilling. Derfor er det vigtigt, at du kontrollerer og forstår forudsætningerne, konsekvenserne og begrænsningerne, før du aktiverer denne indstilling.

![Indstilling, der viser samtidig redigering aktiveret for følsomhedsmærkater.](../media/co-authoring-tenant-option-set-for-sensitivity-labels.png)

Som du kan se på skærmbilledet, når denne indstilling er blevet slået til, kan du kontakte [Microsoft Support](../admin/get-help-support.md) og anmode om at deaktivere denne indstilling. Denne anmodning kan tage flere dage, og du skal bevise, at du er global administrator for din lejer. Forvent normalt, at der opkræves supportgebyrer. 

Hvis en supporttekniker deaktiverer denne indstilling for din lejer:

- For apps og tjenester, der understøtter de nye metadata med mærkning, vender de nu tilbage til det oprindelige metadataformat og den oprindelige placering, når etiketter læses eller gemmes.

- Det nye metadataformat og den nye placering Office dokumenter, der blev brugt, mens indstillingen var aktiveret, kopieres ikke til det oprindelige format og den oprindelige placering. Dette betyder, at disse etiketoplysninger for ikke-krypterede Word-, Excel- PowerPoint-filer går tabt.

- Samtidig redigering og automatisk lagring fungerer ikke længere i din lejer for mærkede og krypterede dokumenter.

- Følsomhedsmærkater forbliver aktiveret for Office filer OneDrive og SharePoint.
