---
title: Brug slutpunkt DLP
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
description: Få mere at vide om, hvordan du konfigurerer DLP-politikker (forebyggelse af datatab) til at bruge placeringer til forebyggelse af datatab for Slutpunkt.
ms.openlocfilehash: 2fef9c2d89d741c70f3d2d903f41fa8a354d4a79
ms.sourcegitcommit: 979343980f05ceb546ca0df23562504aaca34b88
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66912624"
---
# <a name="using-endpoint-data-loss-prevention"></a>Brug forebyggelse af datatab ved slutpunkt

Vi har sammensat nogle scenarier, som du kan følge, for at hjælpe dig med at blive fortrolig med DLP-funktioner for Slutpunkt, og hvordan de dukker op i DLP-politikker.

> [!IMPORTANT]
> Disse DLP-slutpunktsscenarier er ikke de officielle procedurer for oprettelse og justering af DLP-politikker. Se nedenstående emner, når du har brug for at arbejde med DLP-politikker i generelle situationer:
>
>- [Få mere at vide om Microsoft Purview Forebyggelse af datatab](dlp-learn-about-dlp.md)
>- [Kom i gang med DLP-standardpolitikken](get-started-with-the-default-dlp-policy.md)
>- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
>- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)


## <a name="before-you-begin"></a>Før du begynder

### <a name="skusubscriptions-licensing"></a>LICENSER TIL SKU/abonnementer

Du kan finde komplette licensoplysninger under [Vejledning til Microsoft 365-licenser for at få oplysninger om beskyttelse af oplysninger](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

## <a name="scenario-1-create-a-policy-from-a-template-audit-only"></a>Scenarie 1: Opret en politik ud fra en skabelon, kun overvågning

Disse scenarier kræver, at du allerede har enheder onboardet og rapporterer i Aktivitetsoversigt. Hvis du endnu ikke har onboardet enheder, skal du se [Kom i gang med forebyggelse af datatab i Endpoint](endpoint-dlp-getting-started.md).

1. Åbn [siden Forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Vælg **Opret politik**.

3. I dette scenarie skal du vælge **Beskyttelse af personlige oplysninger** og derefter **AMERIKANSKE PERSONidentificerbare oplysninger og** vælge **Næste**.

4. Slå feltet **Status** fra for alle placeringer undtagen **Enheder**. Vælg **Næste**.

5. Acceptér **standardindstillingerne Gennemse og tilpas indstillingerne fra skabelonvalget** , og vælg **Næste**.

6. Acceptér standardhandlingsværdierne **for beskyttelse** , og vælg **Næste**.

7. Vælg **Overvåg eller begræns aktiviteter på Windows-enheder**, og lad handlingerne være angivet til **Overvågning.** Vælg **Næste**.

8. Acceptér standardværdien **Jeg vil gerne teste den første** værdi, og vælg **Vis politiktip, mens du er i testtilstand**. Vælg **Næste**.

9. Gennemse dine indstillinger, og vælg **Send**.

10. Den nye DLP-politik vises på politiklisten.

11. Kontrollér Aktivitetsoversigt for data fra de overvågede slutpunkter. Angiv placeringsfilteret for enheder, og tilføj politikken, filtrer derefter efter politiknavn for at se virkningen af denne politik. Se [Kom i gang med aktivitetsoversigt,](data-classification-activity-explorer.md) hvis det er nødvendigt.

12. Forsøg på at dele et testelement, der indeholder indhold, der udløser den amerikanske PII-databetingelse (Personligt identificerbare oplysninger) med en person uden for din organisation. Dette bør udløse politikken.

13. Kontrollér Aktivitetsoversigt for hændelsen.

## <a name="scenario-2-modify-the-existing-policy-set-an-alert"></a>Scenarie 2: Rediger den eksisterende politik, angiv en besked

1. Åbn [siden Forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Vælg den amerikanske **pii-datapolitik (Personligt identificerbare oplysninger),** som du oprettede i scenarie 1.

3. Vælg **Rediger politik**.

4. Gå til siden **Avancerede DLP-regler,** og rediger den **lave indholdsmængde, der er registreret af U.S. Personligt identificerbar inf**.

5. Rul ned til afsnittet **Hændelsesrapporter** , og angiv **Send en besked til administratorer, når der opstår en regelmatch** til **Til**. Mailbeskeder sendes automatisk til administratoren og alle andre, du føjer til listen over modtagere. 

![turn-on-incident-reports.](../media/endpoint-dlp-2-using-dlp-incident-reports.png)
   
6. I dette scenarie skal du vælge **Send besked, hver gang en aktivitet stemmer overens med reglen**.

7. Vælg **Gem**.

8. Bevar alle dine tidligere indstillinger ved at vælge **Næste** og derefter **Sende** politikændringerne.

9. Forsøg på at dele et testelement, der indeholder indhold, der udløser den amerikanske PII-databetingelse (Personligt identificerbare oplysninger) med en person uden for din organisation. Dette bør udløse politikken.

10. Kontrollér Aktivitetsoversigt for hændelsen.

## <a name="scenario-3-modify-the-existing-policy-block-the-action-with-allow-override"></a>Scenarie 3: Rediger den eksisterende politik, bloker handlingen med tillad tilsidesættelse

1. Åbn [siden Forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Vælg den amerikanske **pii-datapolitik (Personligt identificerbare oplysninger),** som du oprettede i scenarie 1.

3. Vælg **Rediger politik**.

4. Gå til siden **Avancerede DLP-regler,** og rediger den **lave indholdsmængde, der er registreret af U.S. Personligt identificerbar inf**.

5. Rul ned til sektionen **Overvåg eller begræns aktiviteter på Windows-enhed** , og for hver aktivitet angiver den tilsvarende handling til  **Bloker med tilsidesættelse**.

   > [!div class="mx-imgBorder"]
   > ![angiv blok med tilsidesættelseshandling.](../media/endpoint-dlp-6-using-dlp-set-blocked-with-override.png)
   
6. Vælg **Gem**.

7. Gentag trin 4-7 for den **store mængde indhold, der er registreret af U.S. Personligt identificerbar inf**.

8. Bevar alle dine tidligere indstillinger ved at vælge **Næste** og derefter **Sende** politikændringerne.

9. Forsøg på at dele et testelement, der indeholder indhold, der udløser den amerikanske PII-databetingelse (Personligt identificerbare oplysninger) med en person uden for din organisation. Dette bør udløse politikken.

   Du får vist et pop op-vindue som dette på klientenheden:

   > [!div class="mx-imgBorder"]
   > ![meddelelse om blokeret tilsidesættelse af slutpunkt dlp-klient.](../media/endpoint-dlp-3-using-dlp-client-blocked-override-notification.png)

10. Kontrollér Aktivitetsoversigt for hændelsen.

## <a name="scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview"></a>Scenarie 4: Undgå løkkemeddelelser om DLP fra cloudsynkroniseringsapps med automatisk karantæne (prøveversion)

### <a name="before-you-begin"></a>Før du begynder

I dette scenarie blokeres synkronisering af filer med følsomhedsmærkaten **Meget fortroligt** til OneDrive. Dette er et komplekst scenarie med flere komponenter og procedurer. Du skal bruge:

- En AAD-brugerkonto, der skal målrettes, og en onboardet Windows 10 computer, der allerede synkroniserer en lokal OneDrive-mappe med OneDrive-cloudlager.
- Følsomhedsmærkater konfigureret og publiceret – se [Kom i gang med følsomhedsmærkater](get-started-with-sensitivity-labels.md#get-started-with-sensitivity-labels) og [Opret og konfigurer følsomhedsmærkater og deres politikker](create-sensitivity-labels.md#create-and-configure-sensitivity-labels-and-their-policies).

Der er tre procedurer.

1. Konfigurer DLP-indstillingerne for automatisk karantæne for slutpunktet.
2. Opret en politik, der blokerer følsomme elementer, der har følsomhedsmærkaten **Meget fortroligt** .
3. Opret et Word-dokument på den Windows 10 enhed, som politikken er målrettet til, anvend mærkaten, og kopiér det til den lokale OneDrive-mappe for brugerkonti, der synkroniseres.  

### <a name="configure-endpoint-dlp-unallowed-app-and-auto-quarantine-settings"></a>Konfigurer DLP-indstillinger for slutpunkt og ikke-tilladt program til automatisk karantæne

1. Åbn [DLP-indstillinger for slutpunkt](https://compliance.microsoft.com/datalossprevention?viewid=globalsettings)

2. Udvid **Ikke-tilladte apps**.

3. Vælg **Tilføj eller rediger ikke-tilladte apps** , og tilføj *OneDrive* som et vist navn og det eksekverbare navn *onedrive.exe*  for ikke at give onedrive.exe adgang til elementerne mærkaten **Meget fortroligt** .

4. Vælg **Sæt automatisk karantæne** og **Gem**.

5. Under **Indstillinger for automatisk karantæne** skal du vælge **Rediger indstillinger for automatisk karantæne**.

6. Aktivér **automatisk karantæne for ikke-tilladte apps**.

7. Angiv stien til den mappe på lokale computere, hvor de oprindelige følsomme filer skal flyttes til. Eksempel:
   
    **'%homedrive%%homepath%\Microsoft DLP\Quarantine'** for brugernavnet *Isaiah Langer* placerer de flyttede elementer i en mappe med navnet:  

    *C:\Users\IsaiahLanger\Microsoft DLP\Quarantine\OneDrive*

    og føje et dato- og tidsstempel til det oprindelige filnavn.
    
    > [!NOTE]
    > DLP Automatisk karantæne opretter undermapper til filerne for hver ikke-tilladte app. Så hvis du har både *Notesblok* og *OneDrive* på listen over ikke-tilladte apps, oprettes der en undermappe til **\OneDrive** og en anden undermappe til **\Notesblok**.

8. Vælg **Erstat filerne med en .txt fil, der indeholder følgende tekst,** og indtast den ønskede tekst i pladsholderfilen. Det kan f.eks. være en fil med navnet *autokvart 1.docx*:
    
    > %%FileName%% indeholder følsomme oplysninger, som din organisation beskytter med politikken til forebyggelse af datatab (DLP) %%PolicyName%% og er flyttet til karantænemappen: %%QuarantinePath%%
    
    vil efterlade en tekstfil, der indeholder denne meddelelse:
    
    > auto quar 1.docx indeholder følsomme oplysninger, som din organisation beskytter med politikken til forebyggelse af datatab og er flyttet til karantænemappen: C:\Users\IsaiahLanger\Microsoft DLP\Quarantine\OneDrive\auto quar 1_20210728_151541.docx.

9. Vælg **Gem**

### <a name="configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential"></a>Konfigurer en politik for at blokere OneDrive-synkronisering af filer med følsomhedsmærkaten Meget fortroligt

1. Åbn [siden Forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Vælg **Opret politik**.

3. I dette scenarie skal du vælge **Brugerdefineret** og derefter **Brugerdefineret politik** og vælge **Næste**.

4. Udfyld felterne **Navn** og **Beskrivelse** , og vælg **Næste**.

5. Slå feltet **Status** fra for alle placeringer undtagen **Enheder**. Hvis du har en bestemt slutbrugerkonto, som du vil teste dette fra, skal du sørge for at vælge den i området. Vælg **Næste**.

6. Acceptér standardindstillingen **Opret eller tilpas avancerede DLP-regler** , og vælg **Næste**.

7. Opret en regel med disse værdier:
    1. **Navn** >  *Scenarie 4 Automatisk karantæne*.
    1. **Betingelser** >  **Indholdet indeholder** >  **Følsomhedsmærkater** >  **Meget fortroligt**.
    1.  **Handlinger** >  **Overvåg eller begræns aktiviteter på Windows-enheder** >  **Adgang fra ikke-tilladte apps** >  **Blok.** I dette scenarie skal du rydde alle andre aktiviteter.
    1. **Brugermeddelelser** >  **Så er det nu**.
    1. **Slutpunktsenheder** > Vælg **Vis brugere en meddelelse om politiktip, når en aktivitet** ikke allerede er aktiveret.
    
8. Vælg **Gem** og **Næste**.

9. Vælg **Slå den til med det samme**. Vælg **Næste**.

10. Gennemse dine indstillinger, og vælg **Send**.

    > [!NOTE]
    > Tillad mindst en time, før den nye politik replikeres og anvendes på destinationscomputeren Windows 10.

11. Den nye DLP-politik vises på politiklisten.

### <a name="test-auto-quarantine-on-the-windows-10-device"></a>Test automatisk karantæne på den Windows 10 enhed

1. Log på den Windows 10 computer med den brugerkonto, du har angivet i [Konfigurer en politik for at blokere OneDrive-synkronisering af filer med følsomhedsmærkaten Yderst fortroligt](#configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential) trin 5.

2. Opret en mappe, hvis indhold ikke synkroniseres til OneDrive. Eksempel:

    *C:\kildemappe til automatisk karantæne*

3. Åbn Microsoft Word, og opret en fil i kildemappen med automatisk karantæne. Anvend følsomhedsmærkaten **Meget fortroligt** . se [Anvend følsomhedsmærkater på dine filer og mails i Office](https://support.microsoft.com/topic/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

4. Kopiér den fil, du lige har oprettet, til synkroniseringsmappen for OneDrive. Der vises en toast med en brugermeddelelse, der fortæller dig, at handlingen ikke er tilladt, og at filen bliver sat i karantæne. For brugernavnet *Isaiah Langer* og et dokument med titlen *automatisk karantænedokument 1.docx* får du f.eks. vist denne meddelelse:

    ![Pop op til brugermeddelelse om forebyggelse af datatab, der angiver, at OneDrive-synkroniseringshandlingen ikke er tilladt for den angivne fil, og at filen vil blive sat i karantæne.](../media/auto-quarantine-user-notification-toast.png)
    
    Meddelelsen lyder:
    
    > Det er ikke tilladt at åbne autoquarantinedokument 1.docx med denne app. Filen sættes i karantæne til 'C:\Users\IsaiahLanger\Microsoft DLP\OneDrive'

5. Vælg **Afvis**.

6. Åbn tekstfilen til placeringsholderen. Den navngives **dokument 1.docx_ *med* automatisk karantæne date_time.txt**. 

7. Åbn karantænemappen, og bekræft, at den oprindelige fil er der.
 
8. Kontrollér Aktivitetsoversigt for data fra de overvågede slutpunkter. Angiv placeringsfilteret for enheder, og tilføj politikken, filtrer derefter efter politiknavn for at se virkningen af denne politik. Se [Kom i gang med aktivitetsoversigt,](data-classification-activity-explorer.md) hvis det er nødvendigt.

9. Kontrollér Aktivitetsoversigt for hændelsen.

## <a name="scenario-5-restrict-unintentional-sharing-to-unallowed-cloud-apps-and-services"></a>Scenarie 5: Begræns utilsigtet deling til ikke-tilladte cloudapps og -tjenester

Med Endpoint DLP- og Microisoft Edge-webbrowseren kan du begrænse utilsigtet deling af følsomme elementer til ikke-tilladte cloudapps og -tjenester. Edge forstår, hvornår et element er begrænset af en DLP-politik for slutpunkter, og gennemtvinger adgangsbegrænsninger.

Når du vælger **Enheder** som en placering i en korrekt konfigureret DLP-politik og bruger Microsoft Edge-browseren, forhindres de ikke-tilladte browsere, du har defineret i disse indstillinger, i at få adgang til de følsomme elementer, der stemmer overens med dine DLP-politikkontrolelementer. I stedet omdirigeres brugerne til at bruge Microsoft Edge, som med sin forståelse af DLP-pålagte begrænsninger kan blokere eller begrænse aktiviteter, når betingelserne i DLP-politikken er opfyldt.

Hvis du vil bruge denne begrænsning, skal du konfigurere tre vigtige dele:

1. Angiv de steder – tjenester, domæner og IP-adresser – som du vil forhindre, at følsomme elementer deles til.

2. Tilføj de browsere, der ikke har tilladelse til at få adgang til visse følsomme elementer, når der forekommer en DLP-politik.

3. Konfigurer DLP-politikker for at definere de typer følsomme elementer, som upload skal begrænses til disse steder, ved at aktivere **Overfør til cloudtjenester** og **Adgang fra ikke-tilladte browsere**.

Du kan fortsætte med at tilføje nye tjenester, apps og politikker for at udvide og udvide dine begrænsninger, så de opfylder dine forretningsmæssige behov og beskytte følsomme data. 

Denne konfiguration hjælper med at sikre, at dine data forbliver sikre, samtidig med at du undgår unødvendige begrænsninger, der forhindrer eller begrænser brugerne i at få adgang til og dele ikke-følsomme elementer.

## <a name="scenario-6-monitor-or-restrict-user-activities-on-sensitive-service-domains-preview"></a>Scenarie 6 Overvåger eller begrænser brugeraktiviteter på følsomme tjenestedomæner (prøveversion)

Brug dette scenarie, når du vil overvåge, blokere med tilsidesættelse eller blokere disse brugeraktiviteter på et websted.

- udskriv fra et websted
- kopiér data fra et websted
- gem et websted som lokale filer

Brugeren skal have adgang til webstedet via Microsoft Edge.

### <a name="supported-syntax-for-designating-websites-in-a-website-group"></a>Understøttet syntaks til design af websteder i en webstedsgruppe

Du kan bruge en fleksibel syntaks til at inkludere og udelade domæner, underdomæner, websteder og underordnede websteder i dine webstedsgrupper.

- brug `*` som jokertegn til at angive alle domæner eller alle underdomæner
- brug `/` som terminalpunkt i slutningen af en URL-adresse til kun at omfatte det pågældende websted.

Når du tilføjer en URL-adresse uden at afslutte `/`, er denne URL-adresse begrænset til dette websted og alle underordnede websteder.

Denne syntaks gælder for alle http/https-websteder.

Her er nogle eksempler:


|URL-adresse, du føjer til webstedsgruppen  |URL-adressen vil stemme overens  | URL-adressen stemmer ikke overens|
|---------|---------|---------|
|contoso.com  | //<!--nourl-->contoso.com </br> //<!--nourl-->contoso.com/ </br> //<!--nourl-->contoso.com/allsubsites1 </br> //<!--nourl-->contoso.com/allsubsites1/allsubsites2|        //<!--nourl-->allsubdomains.contoso.com </br> //<!--nourl-->allsubdomains.contoso.com.au    |
|contoso.com/     |//<!--nourl-->contoso.com </br> //<!--nourl-->contoso.com/         |//<!--nourl-->contoso.com/allsubsites1 </br> //<!--nourl-->contoso.com/allsubsites1/allsubsites2 </br> //<!--nourl-->allsubdomains.contoso.com </br> //<!--nourl-->allsubdomains.contoso.com/au   |
|*.contoso.com   | //<!--nourl-->contoso.com </br> //<!--nourl-->contoso.com/allsubsites </br> //<!--nourl-->contoso.com/allsubsites1/allsubsites2 </br> //<!--nourl-->allsubdomains.contoso.com </br> //<!--nourl-->allsubdomains.contoso.com/allsubsites </br> //<!--nourl-->allsubdomains1/allsubdomains2/contoso.com/allsubsites1/allsubsites2         | //<!--nourl-->allsubdomains.contoso.com.au|
|*.contoso.com/xyz     |//<!--nourl-->contoso.com </br> //<!--nourl-->contoso.com/xyz </br> //<!--nourl-->contoso.con/xyz/allsubsites/ </br> //<!--nourl-->allsubdomains.contoso.com/xyz </br> //<!--nourl-->allsubdomains.contoso.com/xyz/allsubsites </br> //<!--nourl-->allsubdomains1.allsubdomains2.contoso.com/xyz/allsubsites </br> //<!--nourl-->allsubdomains1.allsubdomains2.contoso.com/xyz/allsubsites1/allsubsites2         | //<!--nourl-->contoso.com/xyz </br> //<!--nourl-->allsubdomains.contoso.com/xyz/|
|*.contoso.com/xyz/     |//<!--nourl-->contoso.com/xyz </br> //<!--nourl-->allsubdomains.contoso.com/xyz         |//<!--nourl-->contoso.com </br> //<!--nourl-->contoso.com/xyz/allsubsites/ </br> //<!--nourl-->allsubdomains.contoso.com/xyz/allsubsites/ </br> //<!--nourl-->allsubdomains1.allsubdomains2.contoso.com/xyz/allsubsites/ </br> //<!--nourl-->allsubdomains1.allsubdomains2.contoso.com/xyz/allsubsites1/allsubsites2|


### <a name="configure-sensitive-service-domains"></a>Konfigurer følsomme tjenestedomæner

1. I Microsoft Purview-compliance-portal åbne **DLP-indstillinger for** >  slutpunkt til **forebyggelse af** >  datatab **Browser- og domænebegrænsninger for følsomme tjenestedomæner til følsomme data** > .
1. Vælg **Tilføj en ny gruppe af følsomme tjenestedomæner**.
1. Navngiv gruppen.
1. Vælg den ønskede **matchtype** . Du kan vælge mellem **URL-adresse**, **IP-adresse**, **IP-adresseinterval**.
1. Skriv den relevante værdi i **Føj nye tjenestedomæner til denne gruppe**. Du kan føje flere websteder til en gruppe og bruge jokertegn til at dække underdomæner.  Du kan f.eks. www.contoso.com for webstedet på øverste niveau eller *.contoso.com for corp.contoso.com, hr.contoso.com fin.contoso.com
1. Vælg **Gem**.
1. Vælg **Politikker**.
1. Opret og område for en politik, der kun anvendes på **enheder**. Se [Opret, test og juster en DLP-politik](create-test-tune-dlp-policy.md) for at få flere oplysninger om, hvordan du opretter en politik.
1. Opret en regel, der bruger **brugeren tilgås et følsomt websted fra Edge**, og handlingen **Overvåg eller begræns aktiviteter, når brugerne tilgår følsomme websteder i Microsoft Edge-browseren på Windows-enheder**.
1. I handlingen skal du vælge **Tilføj eller fjern følsomme webstedsgrupper**.
1. Vælg de **ønskede følsomme webstedsgrupper** .
1. Vælg **Tilføj**.
1. Vælg de brugeraktiviteter, du vil overvåge eller begrænse, og de handlinger, du DLP skal udføre som svar på disse aktiviteter.
1. Afslut konfigurationen af reglen og politikken, og anvend den.


## <a name="see-also"></a>Se også

- [Få mere at vide om forebyggelse af datatab ved slutpunkt](endpoint-dlp-learn-about.md)
- [Kom i gang med forebyggelse af datatab forebyggelse af datatab ved slutpunkt](endpoint-dlp-getting-started.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Kom i gang med Aktivitetsoversigt](data-classification-activity-explorer.md)
- [Microsoft Defender for Endpoint](/windows/security/threat-protection/)
- [Oversigt over onboarding af Windows 10 og Windows 11 enheder i Microsoft Purview](/microsoft-365/compliance/device-onboarding-overview)
- [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure Active Directory (AAD) er tilmeldt](/azure/active-directory/devices/concept-azure-ad-join)
- [Download den nye Microsoft Edge baseret på Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
- [Kom i gang med DLP-standardpolitikken](get-started-with-the-default-dlp-policy.md)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
