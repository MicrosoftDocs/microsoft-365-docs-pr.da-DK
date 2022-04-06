---
title: Aktivér samtidig redigering af dokumenter, der er krypteret af følsomhedsmærkater i Microsoft 365
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
description: Slå en indstilling til, der muliggør samtidig redigering og automatisk lagring i skrivebordsapps for navngivne og krypterede dokumenter i SharePoint og OneDrive.
ms.openlocfilehash: baa2236915d37917e4ed69e5356db31262795d57
ms.sourcegitcommit: 2f6a0096038d09f0e43e1231b01c19e0b40fb358
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64687201"
---
# <a name="enable-co-authoring-for-files-encrypted-with-sensitivity-labels"></a>Aktivér samtidig redigering af filer, der er krypteret med følsomhedsmærkater

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Aktivér indstillingen for at understøtte [samtidig redigering](https://support.office.com/article/ee1509b4-1f6e-401e-b04a-782d26f564a4) af Office desktopapps, så flere brugere kan redigere disse dokumenter på samme tid, når dokumenter mærkes og krypteres af [følsomhedsmærkater](sensitivity-labels.md).

Uden at denne indstilling er aktiveret for din lejer, skal brugerne tjekke et krypteret dokument, der er gemt i SharePoint eller OneDrive, når de bruger Office desktopapps. Derfor kan de ikke samarbejde i realtid. Eller de skal bruge Office på internettet, når [følsomhedsmærkater er aktiveret for Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

Aktivering af denne funktionalitet medfører desuden, at [funktionen AutoSave](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) understøttes for disse navngivne og krypterede filer.

Hvis du vil læse udgivelsesmeddelelsen, skal du se blogindlægget [Samtidig redigering på Microsoft Information Protection krypterede dokumenter nu er offentligt tilgængelig](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/co-authoring-on-microsoft-information-protection-encrypted/ba-p/2693718).

## <a name="metadata-changes-for-sensitivity-labels"></a>Metadataændringer for følsomhedsmærkater

> [!IMPORTANT]
> Når du har aktiveret indstillingen for samtidig redigering, gemmes navneoplysninger for ukrypterede filer ikke længere i brugerdefinerede egenskaber.
> 
> Aktivér ikke denne indstilling, hvis du bruger apps, tjenester, scripts eller værktøjer, der læser eller skriver navngivne metadata til den gamle placering.

Før du aktiverer indstillingen for at understøtte samtidig redigering af Office desktopapps, er det vigtigt at forstå, at denne handling foretager ændringer af de mærkatmetadata, der gemmes i og læses fra Office filer.

Mærkatmetadataene indeholder oplysninger, der identificerer din lejer og den anvendte følsomhedsmærkat. Den ændring, som denne indstilling foretager, er metadataformatet og -placeringen for Word-, Excel- og PowerPoint-filer. Du behøver ikke at foretage nogen handling for krypterede filer eller mails, fordi metadataændringen for krypterede filer er bagudkompatibel, og der er ingen ændringer for mails. Du skal dog være opmærksom på metadataændringerne for krypterede filer, der kan opgraderes automatisk, men som ikke er bagudkompatible.

Denne ændring påvirker både filer, der lige er navngivet, og filer, der allerede er forsynet med mærkater. Når du bruger apps og tjenester, der understøtter indstillingen for samtidig redigering:
- I forbindelse med filer, der for nylig er forsynet med mærkater, er det kun det nye format og den nye placering, der bruges til at navngive metadata.
- For filer, der allerede er mærket, kopieres disse oplysninger til det nye format og den nye placering, næste gang filen åbnes og gemmes, hvis filen har metadata i det gamle format og den gamle placering.

Du kan læse mere om denne ændring af metadata fra følgende ressourcer:

- Blogindlæg: [Kommende ændringer af Microsoft Information Protection metadata Storage](https://techcommunity.microsoft.com/t5/microsoft-security-and/upcoming-changes-to-microsoft-information-protection-metadata/ba-p/1904418)

- Åbne specifikationer: [2.6.3 LabelInfo i forhold til brugerdefinerede dokumentegenskaber](/openspecs/office_file_formats/ms-offcrypto/13939de6-c833-44ab-b213-e0088bf02341)

På grund af disse ændringer skal du ikke aktivere denne indstilling, hvis du har apps, tjenester, scripts eller værktøjer i din organisation, der læser eller skriver mærkatmetadata til den gamle placering. Hvis du gør det, kan du se nogle eksempler på konsekvenser:

- Et dokument, der er forsynet med mærkater, ser ud til at være uden mærkat.

- Et dokument viser en forældet mærkat til brugerne.

- Samtidig redigering og Automatisk lagring fungerer ikke for et navngivet og krypteret dokument, hvis en anden bruger har det åbent i en Office desktopapp, der ikke understøtter de nye mærkatmetadata. Vær opmærksom på, at dette scenarie også kan forekomme for brugere uden for din organisation, hvis eksterne brugere og inviterede gæster har åbnet filen.

- En Exchange Online regel for mailflow, der [identificerer mærkater som brugerdefinerede egenskaber i Office vedhæftede filer](/azure/information-protection/configure-exo-rules#example-2-rule-that-applies-the-encrypt-only-option-to-emails-when-they-have-attachments-that-are-labeled-confidential--partners-and-these-emails-are-sent-outside-the-organization), krypterer ikke mailen og den vedhæftede fil eller krypterer dem forkert.

I følgende afsnit kan du se en liste over de apps og tjenester, der understøtter denne indstilling, og ændringerne af mærkatmetadataene.

## <a name="prerequisites"></a>Forudsætninger

Sørg for at forstå følgende forudsætninger, før du aktiverer denne funktion.

- Du skal være global administrator for at aktivere denne funktion.

- Følsomhedsmærkater skal [være aktiveret for Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) for lejeren. Hvis denne funktion ikke allerede er aktiveret, aktiveres den automatisk, når du vælger indstillingen for at aktivere samtidig redigering af filer med følsomhedsmærkater.

- Microsoft 365 Apps for enterprise:
    - **Windows**: Minimumversion 2107 fra Current Channel eller Monthly Enterprise Channel eller minimumversion 2202 fra Semi-Annual Enterprise Channel
    - **macOS**: Minimumversion 16.51
    - **iOS**: Nu som prøveversion, når du [tilmelder](#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) dig med minimum version 2.58
    - **Android**: Nu i prøveversion, når du [tilmelder](#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) dig med minimum version 16.0.14931

- Alle apps, tjenester og driftsværktøjer i din lejer skal understøtte de nye [mærkatmetadata](#metadata-changes-for-sensitivity-labels). Hvis du bruger en af følgende, skal du kontrollere de påkrævede minimumversioner:
    
    - **Azure Information Protection unified labeling client and scanner:**
        - Minimumversion [2.12.62.0](/information-protection/rms-client/unifiedlabelingclient-version-release-history#version-212620) , som du kan installere fra [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018)
    
    - **OneDrive-synkronisering app til Windows eller macOS:**
        - Minimumversion af 19.002.0121.0008
    
    - **Forebyggelse af datatab for slutpunkt (Slutpunkt DLP):**
        - Windows 10 1809 med KB 4601383
        - Windows 10 1903 og 1909 med KB-4601380
        - Windows 10 2004 med kb 4601382
        - Windows versioner, der er nyere end Windows 10 2004, understøttes uden KB-opdateringer
    
    - **Apps og tjenester, der bruger Microsoft Information Protection SDK:** 
        - Minimumversion af 1.7 

Microsoft 365 tjenester understøtter automatisk de nye mærkatmetadata, når du aktiverer denne funktion. Eksempel:

- [Politikker for automatisk mærkning](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)
- [DLP-politikker, der bruger følsomhedsmærkater som betingelser](dlp-sensitivity-label-as-condition.md)
- [Microsoft Defender for Cloud Apps konfigureret til at anvende følsomhedsmærkater](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)

### <a name="opt-in-to-the-preview-of-co-authoring-for-ios-and-android"></a>Tilmeld dig prøveversionen af samtidig redigering til iOS og Android

Hvis du vil prøve prøveversionen af samtidig redigering til iOS og Android, skal du have de minimumversioner, der er angivet i forrige afsnit, og du skal også anmode om, at din lejer føjes til prøveversionen: [Samtykke til at aktivere samtidig redigering af filer, der er krypteret med følsomhedsmærkater på mobilenheder](https://ncv.microsoft.com/5Oob3oDj1O)

Du kan få flere oplysninger i følgende meddelelse i blogindlægget: [Samtidig redigering på Microsoft Information Protection krypterede dokumenter er nu i offentlig prøveversion på mobilenheder](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/co-authoring-on-microsoft-information-protection-encrypted/ba-p/3081369)

## <a name="limitations"></a>Begrænsninger

Før du aktiverer lejerindstillingen for samtidig redigering af filer, der er krypteret med følsomhedsmærkater, skal du sørge for at forstå følgende begrænsninger for denne funktion.

- På grund af [ændringer af mærkatmetadata](#metadata-changes-for-sensitivity-labels) skal alle apps, tjenester og driftsværktøjer i din lejer understøtte de nye mærkatmetadata for at opnå en ensartet og pålidelig mærkatoplevelse.
    
    Specifik for Excel: Metadata for en følsomhedsmærkat, der ikke anvender kryptering, kan slettes fra en fil, hvis nogen redigerer og gemmer filen ved hjælp af en version af Excel, der ikke understøtter metadataændringerne for følsomhedsmærkater.

- Understøttelse af Office apps til iOS og Android fås i øjeblikket som [prøveversion](https://office.com/insider).

- Samtidig redigering og Automatisk lagring understøttes ikke og fungerer ikke for navngivne og krypterede Office dokumenter, der bruger en af følgende [konfigurationer til kryptering](encryption-sensitivity-labels.md#configure-encryption-settings):
    - **Lad brugerne tildele tilladelser, når de anvender etiketten**, og afkrydsningsfeltet **I Word, PowerPoint og Excel skal du bede brugerne om at angive tilladelser** er markeret. Denne konfiguration kaldes nogle gange "brugerdefinerede tilladelser".
    - **Brugeradgang til indhold, der udløber,** er angivet til en anden værdi end **Aldrig**.
    - **Kryptering af dobbelt nøgle** er valgt.
    
    For mærkater med en af disse krypteringskonfigurationer vises mærkaterne i Office apps. Men når brugerne vælger disse mærkater, og ingen andre redigerer dokumentet, bliver de advaret om, at samtidig redigering og automatisk lagring ikke er tilgængelig. Hvis en anden redigerer dokumentet, får brugerne vist en meddelelse om, at mærkaterne ikke kan anvendes.

- Hvis du bruger Azure Information Protection Unified Labeling-klient: Se dokumentationen til denne navngivningsklient for [at få flere krav eller begrænsninger](/azure/information-protection/known-issues#known-issues-for-co-authoring). 
    > [!NOTE]
    > Disse begrænsninger for unified labeling-klienten omfatter en [ændring af en dialogboks](/azure/information-protection/known-issues#user-interface-changes-when-applying-labels) for brugere, der vælger mærkater, som beder dem om at vælge tilladelser.

## <a name="how-to-enable-co-authoring-for-files-with-sensitivity-labels"></a>Sådan aktiverer du samtidig redigering af filer med følsomhedsmærkater

> [!CAUTION]
> Aktivering af denne indstilling er en envejshandling. Aktivér den først, når du har læst og forstået metadataændringerne, forudsætningerne, begrænsningerne og eventuelle kendte problemer, der er dokumenteret på denne side.

Hvis du allerede har aktiveret denne indstilling i prøveperioden, er der ikke behov for yderligere handling, og du kan springe denne procedure over.

1. Log på [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com) som global administrator for din lejer.

2. Vælg **Indstillinger** >  **Co-authoring for filer med følsomhedsfiler** i navigationsruden.

2. På siden **Samtidig redigering af filer med følsomhedsmærkater** skal du læse oversigtsbeskrivelsen, forudsætningerne, hvad du kan forvente, og advarslen om, at du ikke kan slå denne indstilling fra, når du har slået den til.
    
    Vælg derefter **Slå samtidig redigering til for filer med følsomhedsmærkater** og **Anvend**:
    
    ![Mulighed for at slå samtidig redigering til for filer med følsomhedsmærkater.](../media/co-authoring-tenant-option-for-sensitivity-labels.png)

3. Vent 24 timer på, at denne indstilling replikeres på tværs af dit miljø, før du bruger denne nye funktion til samtidig redigering.

## <a name="contact-support-if-you-need-to-disable-this-feature"></a>Kontakt support, hvis du har brug for at deaktivere denne funktion

> [!IMPORTANT]
> Hvis du har brug for at deaktivere denne funktion, skal du være opmærksom på, at mærkningsoplysninger kan gå tabt.

Når du har aktiveret samtidig redigering af filer med følsomhedsmærkater for din lejer, kan du ikke selv deaktivere denne indstilling. Det er derfor, det er så vigtigt, at du kontrollerer og forstår forudsætningerne, konsekvenserne og begrænsningerne, før du aktiverer denne indstilling.

![Indstilling, der viser samtidig redigering slået til for følsomhedsmærkater.](../media/co-authoring-tenant-option-set-for-sensitivity-labels.png)

Som du kan se på skærmbilledet, når denne indstilling er slået til, kan du kontakte [Microsoft Support](../admin/get-help-support.md) og anmode om at deaktivere denne indstilling. Denne anmodning kan tage flere dage, og du skal bevise, at du er global administrator for din lejer. Forvent, at der opkræves normale supportgebyrer. 

Hvis en supporttekniker deaktiverer denne indstilling for din lejer:

- For apps og tjenester, der understøtter de nye mærkatmetadata, vender de nu tilbage til det oprindelige metadataformat og den oprindelige placering, når mærkater læses eller gemmes.

- Det nye metadataformat og den nye placering for Office dokumenter, der blev brugt, mens indstillingen blev aktiveret, kopieres ikke til det oprindelige format og den oprindelige placering. Derfor vil disse mærkater for ukrypterede Word-, Excel- og PowerPoint-filer gå tabt.

- Samtidig redigering og Automatisk lagring fungerer ikke længere i din lejer for navngivne og krypterede dokumenter.

- Følsomhedsmærkater forbliver aktiveret for Office filer i OneDrive og SharePoint.
