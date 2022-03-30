---
title: Brug af forebyggelse af datatab på slutpunkt
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
description: Få mere at vide om, hvordan du konfigurerer politikker til forebyggelse af datatab (DLP) Microsoft 365 at bruge endpoint-placeringer til forebyggelse af datatab (EPDLP).
ms.openlocfilehash: aeb85b883738e94f2d7161cb2bc3434edbb16428
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680022"
---
# <a name="using-endpoint-data-loss-prevention"></a>Brug af forebyggelse af datatab på slutpunkt

For at gøre dig bekendt med slutpunkt-DLP-funktioner, og hvordan de findes i DLP-politikker, har vi samlet nogle scenarier, som du kan følge.

> [!IMPORTANT]
> Disse Slutpunkt-DLP-scenarier er ikke de officielle procedurer for oprettelse og justering af DLP-politikker. Se nedenstående emner, når du har brug for at arbejde med DLP-politikker i generelle situationer:
>
>- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
>- [Introduktion til DLP-standardpolitikken](get-started-with-the-default-dlp-policy.md)
>- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
>- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)

## <a name="scenario-1-create-a-policy-from-a-template-audit-only"></a>Scenarie 1: Opret en politik ud fra en skabelon, kun overvågning

Disse scenarier kræver, at du allerede har enheder onboardet og rapportering i Aktivitetsoversigt. Hvis du ikke har onboardede enheder endnu, kan du se [Introduktion til forebyggelse af datatab i](endpoint-dlp-getting-started.md) slutpunkt.

1. Åbn siden [forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Vælg **Opret politik**.

3. I dette scenarie skal **du** vælge Beskyttelse af **personlige oplysninger og derefter USA Personidentificerbare oplysninger (PII)-data** og vælge **Næste**.

4. Slå feltet **Status fra** for alle placeringer undtagen **Enheder**. Vælg **Næste**.

5. Acceptér **standardindstillingerne Gennemse og tilpas indstillingerne fra skabelonmarkering** , og vælg **Næste**.

6. Acceptér **standardindstillingerne for Beskyttelse-handlinger** , og vælg **Næste**.

7. Vælg **Overvågning, eller begræns aktiviteter Windows enheder**, og lad handlingerne være indstillet **til Kun overvågning**. Vælg **Næste**.

8. Acceptér den **standard, jeg gerne vil teste den for første værdi** , og **vælg Vis politiktip, mens jeg er i testtilstand**. Vælg **Næste**.

9. Gennemse dine indstillinger, og vælg **Send**.

10. Den nye DLP-politik vises på politiklisten.

11. Kontrollér Aktivitetsstifinder for data fra de overvågede slutpunkter. Angiv placeringsfilteret for enheder, og tilføj politikken, og filtrer derefter efter politiknavn for at se effekten af denne politik. Se [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md), hvis det er nødvendigt.

12. Forsøg at dele et testelement, der indeholder indhold, som udløser databetingelsesbetingelse (personidentificerbare oplysninger) i USA med en person uden for organisationen. Dette bør udløse politikken.

13. Kontrollér Aktivitetsstifinder for begivenheden.

## <a name="scenario-2-modify-the-existing-policy-set-an-alert"></a>Scenarie 2: Rediger den eksisterende politik, angiv en besked

1. Åbn siden [forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Vælg den **amerikanske politik for personidentificerbare oplysninger (PII), som** du oprettede i scenarie 1.

3. Vælg **Rediger politik**.

4. Gå til siden **med avancerede DLP-regler**, og rediger den registrerede lave mængde indhold amerikansk personligt **identificerbare oplysninger.**

5. Rul ned til **sektionen Hændelsesrapporter** , og **angiv Send en besked til administratorer, når en regel matcher til** **Til**. Mailbeskeder sendes automatisk til administratoren og alle andre, du føjer til listen over modtagere. 

![turn-on-incident-reports.](../media/endpoint-dlp-2-using-dlp-incident-reports.png)
   
6. I dette scenarie skal du vælge **Send besked, hver gang en aktivitet svarer til reglen**.

7. Vælg **Gem**.

8. Behold alle dine tidligere indstillinger ved at **vælge Næste** og **derefter Sende** politikændringerne.

9. Forsøg at dele et testelement, der indeholder indhold, som udløser databetingelsesbetingelse (personidentificerbare oplysninger) i USA med en person uden for organisationen. Dette bør udløse politikken.

10. Kontrollér Aktivitetsstifinder for begivenheden.

## <a name="scenario-3-modify-the-existing-policy-block-the-action-with-allow-override"></a>Scenarie 3: Rediger den eksisterende politik, bloker handlingen med tillad tilsidesættelse

1. Åbn siden [forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Vælg den **amerikanske politik for personidentificerbare oplysninger (PII), som** du oprettede i scenarie 1.

3. Vælg **Rediger politik**.

4. Gå til siden **med avancerede DLP-regler**, og rediger den registrerede lave mængde indhold amerikansk personligt **identificerbare oplysninger.**

5. Rul ned til **afsnittet Overvågning eller begræns aktiviteter Windows enhed**, og for hver aktivitet skal den tilsvarende handling angives **til Bloker med tilsidesættelse**.

   > [!div class="mx-imgBorder"]
   > ![angiv blok med tilsidesættelseshandling.](../media/endpoint-dlp-6-using-dlp-set-blocked-with-override.png)
   
6. Vælg **Gem**.

7. Gentag trin 4-7 for den **store mængde indhold, der registreres af USA Personligt identificerbare inf**.

8. Behold alle dine tidligere indstillinger ved at **vælge Næste** og **derefter Sende** politikændringerne.

9. Forsøg at dele et testelement, der indeholder indhold, som udløser databetingelsesbetingelse (personidentificerbare oplysninger) i USA med en person uden for organisationen. Dette bør udløse politikken.

   Du får vist et pop op-vindue som dette på klientenhed:

   > [!div class="mx-imgBorder"]
   > ![endpoint dlp client blocked override notification.](../media/endpoint-dlp-3-using-dlp-client-blocked-override-notification.png)

10. Kontrollér Aktivitetsstifinder for begivenheden.

## <a name="scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview"></a>Scenarie 4: Undgå at gentage DLP-meddelelser fra skysynkroniseringsapps med automatisk karantæne (forhåndsvisning)

### <a name="before-you-begin"></a>Før du begynder

I dette scenarie blokeres synkronisering af filer med **etiketten Meget** fortroligt følsomhed OneDrive filer. Dette er et komplekst scenarie med flere komponenter og procedurer. Du skal bruge:

- En AAD-brugerkonto at målrette mod og en onboardet Windows 10-computer, der allerede synkroniserer en lokal OneDrive-mappe med OneDrive-lagerplads i skyen.
- Microsoft Word installeret på destinationscomputeren Windows 10 computeren
- Følsomhedsmærkater konfigureret og publiceret – [se Introduktion til følsomhedsmærkater](get-started-with-sensitivity-labels.md#get-started-with-sensitivity-labels) [og Opret og konfigurer følsomhedsmærkater og deres politikker](create-sensitivity-labels.md#create-and-configure-sensitivity-labels-and-their-policies).

Der er tre procedurer.

1. Konfigurer indstillingerne for den automatiske DLP-karantæne for Slutpunkt.
2. Opret en politik, der blokerer følsomme elementer, der har **etiketten Meget fortroligt** følsomhed.
3. Opret et Word-dokument på Windows 10-enhed, som politikken er målrettet til, anvend etiketten, og kopiér det til brugerkontienes lokale OneDrive mappe, der synkroniseres.  

### <a name="configure-endpoint-dlp-unallowed-app-and-auto-quarantine-settings"></a>Konfigurere indstillinger for ikke-tilladt slutpunkt for app og automatisk karantæne

1. Åbn [DLP-indstillinger for Slutpunkt](https://compliance.microsoft.com/datalossprevention?viewid=globalsettings)

2. **Udvid Ikke-tilladte apps**.

3. Vælg **Tilføj eller** rediger ikke-tilladte apps, og tilføj *OneDrive* som vist navn og det eksekverbare navn *onedrive.exefor ikke* at tillade onedrive.exe at få adgang til elementer med navnet Meget **fortroligt.**

4. Vælg **Automatisk karantæne og** **Gem**.

5. Under **Indstillinger for automatisk karantæne skal** du **vælge Rediger indstillinger for automatisk karantæne**.

6. **Aktivér automatisk karantæne for ikke-tilladte apps**.

7. Angiv stien til mappen på lokale computere, hvor du vil flytte de oprindelige følsomme filer til. Eksempel:
   
    **'%homedrive%%homepath%\Microsoft DLP\Quarantine'** for brugernavnet *Isaaka langer* placerer de flyttede elementer i en mappe med navnet:  

    *C:\Users\Isaæder\Microsoft DLP\Quarantine\OneDrive*

    og føje et dato- og tidsstempel til det oprindelige filnavn.
    
    > [!NOTE]
    > DLP Auto-karantæne opretter undermapper for filerne for hver app, der ikke er tilladt. Så hvis du har både *Notesblok* *og OneDrive* på listen over ikke-tilladte apps, oprettes der en undermappe til **\OneDrive** og en anden undermappe til **\Notesblok**.

8. Vælg **Erstat filerne med en .txt,** der indeholder følgende tekst, og skriv den ønskede tekst i pladsholderfilen. Eksempel: for en fil med *navnet 1.docx*:
    
    > %%FileName%% indeholder følsomme oplysninger, som din organisation beskytter med DLP-politikken (forebyggelse af datatab), %%PolicyName%%, og er blevet flyttet til karantænemappen: %%QuarantinePath%%
    
    en tekstfil, der indeholder denne meddelelse:
    
    > Automatisk kvartil 1.docx indeholder følsomme oplysninger, som din organisation beskytter med politikken til forebyggelse af datatab (DLP) og er blevet flyttet til karantænemappen: C:\Users\Isachet\Microsoft DLP\Quarantine\OneDrive\auto quar 1_20210728_151541.docx.

9. Vælg **Gem**

### <a name="configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential"></a>Konfigurer en politik til at OneDrive synkronisering af filer med følsomhedsmærkatet Meget fortroligt

1. Åbn siden [forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Vælg **Opret politik**.

3. I dette scenarie skal du **vælge Brugerdefineret**, **derefter Brugerdefineret politik** og vælge **Næste**.

4. Udfyld felterne Navn **og** **Beskrivelse,** og vælg **Næste**.

5. Slå feltet **Status fra** for alle placeringer undtagen **Enheder**. Hvis du har en bestemt slutbrugerkonto, du vil teste denne fra, skal du sørge for at markere den i området. Vælg **Næste**.

6. Acceptér **standardindstillingen Opret eller tilpas avancerede DLP-regler,** og vælg **Næste**.

7. Opret en regel med disse værdier:
    1. **Navn** >  *Scenarie 4 Automatisk karantæne*.
    1. **Betingelser** >  **Indhold indeholder** >  **Følsomhedsmærkater** >  **Meget fortroligt**.
    1.  **Handlinger** >  **Overhold eller begræns aktiviteter på Windows** >  **enhederAccess ved ikke-tilladte** **appsBlokering** > . I dette scenarie skal du rydde alle de andre aktiviteter.
    1. **Brugerbeskeder** >  **Til**.
    1. **Slutpunktsenheder skal >** Vis brugere **en besked med et politiktip, når en aktivitet ikke** allerede er aktiveret.
    
8. Vælg **Gem** og **Næste**.

9. Vælg **Slå det til med det samme**. Vælg **Næste**.

10. Gennemse dine indstillinger, og vælg **Send**.

    > [!NOTE]
    > Det kan være mindst en time, før den nye politik replikeres og anvendes på den Windows 10 computer.

11. Den nye DLP-politik vises på politiklisten.

### <a name="test-auto-quarantine-on-the-windows-10-device"></a>Test automatisk karantæne på Windows 10 enhed

1. Log på Windows 10-computeren med den brugerkonto, du angav i Konfigurer en politik for at blokere [OneDrive](#configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential) synkronisering af filer med følsomhedsmærkatet Meget fortroligt trin 5.

2. Opret en mappe, hvis indhold ikke synkroniseres OneDrive. Eksempel:

    *C:\auto-quarantine source folder*

3. Åbn Microsoft Word og opret en fil i mappen med kildekilden automatisk i karantæne. Anvende **etiketten Meget fortroligt** følsomhed. se [Anvend følsomhedsetiketter på dine filer og mails i Office](https://support.microsoft.com/topic/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

4. Kopiér den fil, du lige har oprettet, OneDrive din synkroniseringsmappe. Der vises nu en toastbesked om, at handlingen ikke er tilladt, og at filen er sat i karantæne. For brugernavnet *Isa hele Langer* og et dokument med titlen automatisk karantæne på dokument, *1.docx* får du vist denne meddelelse:

    ![Pop op-vindue til forebyggelse af datatab med en besked om, at OneDrive synkronisering ikke er tilladt for den angivne fil, og at filen skal være i karantæne.](../media/auto-quarantine-user-notification-toast.png)
    
    Meddelelsen læses op:
    
    > Det er ikke tilladt at åbne 1.docx dokument med denne app. Filen er sat i karantæne til 'C:\Users\Isalager\Microsoft DLP\OneDrive'

5. Vælg **Afvis**.

6. Åbn tekstfilen med pladsholderen. Det navngives **automatisk karantæne på dokument 1.docx_ *date_time*.txt**. 

7. Åbn karantænemappen, og bekræft, at den oprindelige fil findes der.
 
8. Kontrollér Aktivitetsstifinder for data fra de overvågede slutpunkter. Angiv placeringsfilteret for enheder, og tilføj politikken, og filtrer derefter efter politiknavn for at se effekten af denne politik. Se [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md), hvis det er nødvendigt.

9. Kontrollér Aktivitetsstifinder for begivenheden.

## <a name="scenario-5-restrict-unintentional-sharing-to-unallowed-cloud-apps-and-services"></a>Scenarie 5: Begræns utilsigtet deling til ikke-tilladte skyapps og -tjenester

Med Endpoint DLP og Microsoft Edge Kan du begrænse utilsigtet deling af følsomme elementer til ikke-tilladte skyapps og -tjenester. Edge forstår, når et element begrænses af en Slutpunkt DLP-politik og gennemtvinger adgangsbegrænsninger.

Når du vælger  Enheder som en placering i en korrekt konfigureret DLP-politik og bruger Microsoft Edge-browseren, vil de ikke-tilladte browsere, du har defineret i disse indstillinger, være forhindret i at få adgang til de følsomme elementer, der passer til dine DLP-politikkontrolelementer. I stedet vil brugerne blive omdirigeret til at bruge Microsoft Edge, som med en forståelse af de DLP-pålagde begrænsninger kan blokere eller begrænse aktiviteter, når betingelserne i DLP-politikken er opfyldt.

Hvis du vil bruge denne begrænsning, skal du konfigurere tre vigtige dele:

1. Angiv de steder – tjenester, domæner og IP-adresser – som du vil forhindre, at følsomme elementer deles med.

2. Tilføj de browsere, der ikke har tilladelse til at få adgang til bestemte følsomme elementer, når der opstår et DLP-politik match.

3. Konfigurer DLP-politikker til at definere typer af følsomme elementer, som uploads skal begrænses til disse steder ved at slå **Upload** til skytjenester og Access fra **ikke-tilladt browser**.

Du kan fortsætte med at tilføje nye tjenester, apps og politikker for at udvide og udvide dine begrænsninger, så de opfylder virksomhedens behov, og beskytte følsomme data. 

Denne konfiguration hjælper med at sikre, at dine data forbliver sikre, og samtidig undgå unødvendige begrænsninger, der forhindrer eller begrænser brugere i at få adgang til og dele ikke-følsomme elementer.
## <a name="see-also"></a>Se også

- [Få mere at vide om forebyggelse af datatab på slutpunkt](endpoint-dlp-learn-about.md)
- [Kom i gang med forebyggelse af datatab på slutpunkt](endpoint-dlp-getting-started.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md)
- [Microsoft Defender til Slutpunkt](/windows/security/threat-protection/)
- [Onboard Windows 10 og Windows 11 enheder i Microsoft 365 oversigt](/microsoft-365/compliance/device-onboarding-overview)
- [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure Active Directory (AAD) tilmeldt](/azure/active-directory/devices/concept-azure-ad-join)
- [Download den nye Microsoft Edge baseret på Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
- [Introduktion til DLP-standardpolitikken](get-started-with-the-default-dlp-policy.md)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
