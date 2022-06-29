---
title: Konfigurer og administrer Microsoft Threat Experts-funktioner
ms.reviewer: ''
description: Tilmeld dig Microsoft Threats Experts for at konfigurere, administrere og bruge det i dine daglige sikkerhedshandlinger og sikkerhedsadministrationsarbejde.
keywords: Microsoft-trusselseksperter, administreret trusselsjagttjeneste, MTE, Microsoft-administreret jagttjeneste
search.product: Windows 10
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 7661619ccb60bb55020a8e241c341b11fe45abd1
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487327"
---
# <a name="configure-and-manage-microsoft-threat-experts-capabilities"></a>Konfigurer og administrer Microsoft Threat Experts-funktioner

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="before-you-begin"></a>Før du begynder

> [!NOTE]
> Diskuter berettigelseskravene med din Microsoft Technical Service-udbyder og dit kontoteam, før du ansøger om Microsoft-trusselseksperter – Managed Threat Hunting Service til målrettet angrebsmeddelelse.

Sørg for, at Defender for Endpoint er installeret i dit miljø med de enheder, der er tilmeldt, og ikke kun på et laboratorie.

Hvis du er Defender for Endpoint-kunde, skal du ansøge om **Microsoft-trusselseksperter – målrettede angrebsmeddelelser** for at få særlig indsigt og analyse, der kan hjælpe med at identificere de mest kritiske trusler, så du hurtigt kan reagere på dem. Kontakt dit kontoteam eller din Microsoft-repræsentant for at abonnere **på Microsoft-trusselseksperter – Eksperter on Demand for** at rådføre sig med vores trusselseksperter om relevante opdagelser og modstandere.

## <a name="apply-for-microsoft-threat-experts---targeted-attack-notifications-service"></a>Ansøg om Microsoft-trusselseksperter – tjenesten for meddelelser om målrettede angreb

Hvis du allerede er Defender for Endpoint-kunde, kan du søge via Microsoft 365 Defender-portalen.

1. Gå til **Indstillinger > Generelle > Avancerede funktioner > Microsoft-trusselseksperter – Meddelelser om målrettede angreb** i navigationsruden.

2. Klik på **Anvend**.

   :::image type="content" source="images/mte-collaboratewithmte.png" alt-text="Indstillingerne for Microsoft-trusselseksperter" lightbox="images/mte-collaboratewithmte.png":::

3. Angiv dit navn og din mailadresse, så Microsoft kan vende tilbage til dig i dit program.

   :::image type="content" source="images/mte-apply.png" alt-text="Feltet Navn på programsiden Microsoft-trusselseksperter" lightbox="images/mte-apply.png":::

4. Læs [erklæringen om beskyttelse af personlige oplysninger](https://privacy.microsoft.com/privacystatement), og klik derefter på **Send** , når du er færdig. Du modtager en velkomstmail, når din ansøgning er godkendt.

   :::image type="content" source="images/mte-applicationconfirmation.png" alt-text="Bekræftelsesmeddelelsen Microsoft-trusselseksperter program" lightbox="images/mte-applicationconfirmation.png":::

Når du er accepteret, modtager du en velkomstmail, og du kan se, at knappen **Anvend** ændres til en til/fra-knap, der er "slået til". Hvis du vil tage dig selv ud af tjenesten Målrettet angrebsmeddelelser, skal du skubbe til/fra-knappen "fra" og klikke på **Gem indstillinger** nederst på siden.

## <a name="where-youll-see-the-targeted-attack-notifications-from-microsoft-threat-experts"></a>Her kan du se meddelelser om målrettede angreb fra Microsoft-trusselseksperter

Du kan modtage målrettede angrebsmeddelelser fra Microsoft-trusselseksperter via følgende medie:

- Siden **Hændelser** på Defender for Endpoint-portalen
- Dashboardet **Beskeder** for Defender for Endpoint Portal
- API [til](/windows/security/threat-protection/microsoft-defender-atp/get-alerts) OData-beskeder og [REST API](/windows/security/threat-protection/microsoft-defender-atp/pull-alerts-using-rest-api)
- [DeviceAlertEvents-tabel](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-devicealertevents-table) i avanceret jagt
- Din mail, hvis du vælger at konfigurere den

Hvis du vil modtage målrettede angrebsmeddelelser via mail, skal du oprette en regel for meddelelse via mail.

### <a name="create-an-email-notification-rule"></a>Opret en regel for mailmeddelelser

Du kan oprette regler for at sende mailmeddelelser til meddelelsesmodtagere. Se  [Konfigurer beskeder om](configure-email-notifications.md) oprettelse, redigering, sletning eller fejlfinding af mailmeddelelser for at få flere oplysninger.

## <a name="view-the-targeted-attack-notification"></a>Få vist meddelelsen om målrettede angreb

Du begynder at modtage målrettet besked om angreb fra Microsoft-trusselseksperter i din mail, når du har konfigureret dit system til at modtage en meddelelse via mail.

1. Klik på linket i mailen for at gå til den tilsvarende beskedkontekst på dashboardet, der er mærket med **Threat-eksperter**.

2. På dashboardet skal du vælge det samme emne for vigtig besked, som du fik i mailen, for at få vist detaljerne.

## <a name="subscribe-to-microsoft-threat-experts---experts-on-demand"></a>Abonner på Microsoft-trusselseksperter – eksperter efter behov

Dette er tilgængeligt som en abonnementstjeneste. Hvis du allerede er Defender for Endpoint-kunde, kan du kontakte din Microsoft-repræsentant for at abonnere på Microsoft-trusselseksperter – Eksperter on Demand.

## <a name="consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization"></a>Kontakt en Microsoft-trusselsekspert om mistænkelige cybersikkerhedsaktiviteter i din organisation

Du kan samarbejde med Microsoft-trusselseksperter, der kan engageres direkte fra Microsoft 365 Defender-portalen for at få svar. Eksperter giver indsigt for bedre at forstå komplekse trusler, målrettede angrebsmeddelelser, som du får, eller hvis du har brug for flere oplysninger om beskederne, en potentielt kompromitteret enhed eller en trusselsintelligenskontekst, som du kan se på portaldashboardet.

> [!NOTE]
>
> - Vigtige forespørgsler, der er relateret til din organisations tilpassede trusselsintelligensdata, understøttes ikke i øjeblikket. Kontakt dit team for sikkerhedshandlinger eller svar på hændelser for at få flere oplysninger.
> - Du skal have tilladelse til at **administrere sikkerhedsindstillinger** på Microsoft 365 Defender-portalen for at kunne indsende en forespørgsel af typen "Kontakt en trusselsekspert".

1. Gå til portalsiden med de relevante oplysninger, du vil undersøge, f.eks. siden **Hændelse** . Sørg for, at siden for den relevante besked eller enhed er i visningen, før du sender en undersøgelsesanmodning.

2. Klik på i menuen øverst til højre **.** Ikon. Vælg derefter **Kontakt en trusselsekspert**.

    :::image type="content" source="images/mte-eod-menu.png" alt-text="Menupunktet Microsoft-trusselseksperter Eksperter on Demand" lightbox="images/mte-eod-menu.png":::

    Der åbnes en pop op-skærm. Følgende skærmbillede viser, hvornår du er på et prøveabonnement.

    :::image type="content" source="images/mte-eod.png" alt-text="Siden Microsoft-trusselseksperter Eksperter on Demand" lightbox="images/mte-eod.png":::

    På følgende skærmbillede kan du se, hvornår du er på et komplet Microsoft-trusselseksperter – eksperters on-demand-abonnement.

    :::image type="content" source="images/mte-eod-fullsubscription.png" alt-text="Siden med det fulde abonnement Microsoft-trusselseksperter Eksperter on Demand" lightbox="images/mte-eod-fullsubscription.png":::

    Emnefeltet **Forespørgsel** er udfyldt på forhånd med linket til den relevante side for din undersøgelsesanmodning. Det kan f.eks. være et link til den hændelses-, besked- eller enhedsoplysningerside, du var på, da du foretog anmodningen.

3. I det næste felt skal du angive tilstrækkelige oplysninger til at give Microsoft-trusselseksperter kontekst nok til at starte undersøgelsen.

4. Angiv den mailadresse, du vil bruge til at svare til Microsoft-trusselseksperter.

> [!NOTE]
> Hvis du vil spore status for dine eksperter on Demand-sager via Microsoft Services Hub, skal du kontakte din kundesucceskontoadministrator.

Se denne video for at få et hurtigt overblik over Microsoft Services Hub.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4pk9f]

## <a name="sample-investigation-topics-that-you-can-consult-with-microsoft-threat-experts---experts-on-demand"></a>Eksempel på undersøgelsesemner, som du kan rådføre dig med Microsoft-trusselseksperter – Eksperter efter behov

### <a name="alert-information"></a>Beskedoplysninger

- Vi kan se en ny type besked for en binær fil, der lever af jorden: [AlertID]. Kan du fortælle os noget mere om denne besked, og hvordan vi kan undersøge det nærmere?
- Vi har observeret to lignende angreb, som forsøger at udføre skadelige PowerShell-scripts, men generere forskellige beskeder. Den ene er "Mistænkelig PowerShell-kommandolinje", og den anden er "Der blev registreret en skadelig fil baseret på indikation fra O365". Hvad er forskellen?
- Jeg modtager en ulige besked i dag om unormalt antal mislykkede logons fra en højtprofileret brugers enhed. Jeg kan ikke finde flere beviser omkring disse logonforsøg. Hvordan kan Defender for Endpoint se disse forsøg? Hvilken type logon overvåges?
- Kan du give mere kontekst eller indsigt i denne besked: "Der blev observeret mistænkelig adfærd fra et systemprogram".

### <a name="possible-machine-compromise"></a>Muligt computer kompromitteret

- Kan du hjælpe med at svare på, hvorfor vi ser "Ukendt proces observeret?" Denne meddelelse eller besked vises ofte på mange enheder. Vi sætter pris på ethvert input for at afklare, om denne meddelelse eller besked er relateret til skadelig aktivitet.
- Kan du hjælpe med at validere et muligt kompromis på følgende system på [date] med lignende funktionsmåder som den forrige [malwarenavn] malwareregistrering på det samme system i [måned]?

### <a name="threat-intelligence-details"></a>Oplysninger om trusselsintelligens

- Vi har fundet en phishing-mail, der har leveret et skadeligt Word-dokument til en bruger. Det skadelige Word-dokument forårsagede en række mistænkelige hændelser, som udløste flere Defender for Endpoint-beskeder for [malwarenavn] malware. Har du nogen oplysninger om denne malware? Hvis ja, kan du så sende mig et link?
- Jeg har for nylig set en [sociale medier reference, for eksempel Twitter eller blog] indlæg om en trussel, der er rettet mod min branche. Kan du hjælpe mig med at forstå, hvilken beskyttelse Defender for Endpoint yder mod denne trusselsaktør?

### <a name="microsoft-threat-experts-alert-communications"></a>Microsoft-trusselseksperter beskedkommunikation

- Kan dit team for svar på hændelser hjælpe os med at håndtere den målrettede angrebsmeddelelse, vi fik?
- Jeg modtog denne målrettede angrebsmeddelelse fra Microsoft-trusselseksperter. Vi har ikke vores eget team for svar på hændelser. Hvad kan vi gøre nu, og hvordan kan vi begrænse hændelsen?
- Jeg modtog en målrettet angrebsmeddelelse fra Microsoft-trusselseksperter. Hvilke data kan du give os, som vi kan videregive til vores team for svar på hændelser?

  > [!NOTE]
  > Microsoft-trusselseksperter er en administreret jagttjeneste for cybersikkerhed og ikke en hændelsessvartjeneste. Du kan dog interagere med dit eget team for svar på hændelser for at løse problemer, der kræver et svar på en hændelse. Hvis du ikke har dit eget team for svar på hændelser og gerne vil have Microsofts hjælp, kan du interagere med CSS Cybersecurity Incident Response Team (CIRT). De kan åbne en billet for at hjælpe med at løse din forespørgsel.

## <a name="scenario"></a>Scenario

### <a name="receive-a-progress-report-about-your-managed-hunting-inquiry"></a>Modtag en statusrapport om din administrerede jagtforespørgsel

Svar fra Microsoft-trusselseksperter varierer afhængigt af din forespørgsel. De sender en statusrapport til dig om din **undersøgelse af en trusselsekspert** inden for to dage for at kommunikere undersøgelsesstatussen fra følgende kategorier:

- Der er brug for flere oplysninger for at fortsætte undersøgelsen
- Der kræves en fil eller flere fileksempler for at bestemme den tekniske kontekst
- Undersøgelsen kræver mere tid
- De indledende oplysninger var tilstrækkelige til at afslutte undersøgelsen

Det er afgørende at reagere hurtigt for at holde undersøgelsen i gang.

## <a name="related-topic"></a>Relateret emne

- [Oversigt over Microsoft Threat Experts](microsoft-threat-experts.md)
- [oversigt over Microsoft-trusselseksperter i Microsoft 365](/microsoft-365/security/mtp/microsoft-threat-experts)
