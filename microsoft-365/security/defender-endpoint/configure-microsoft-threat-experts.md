---
title: Konfigurere og Microsoft-trusselseksperter egenskaber
ms.reviewer: ''
description: Registrer dig til Microsoft Threats-eksperter for at konfigurere, administrere og bruge det i dine daglige sikkerhedshandlinger og sikkerhedsadministrationsarbejde.
keywords: Microsoft-trusselseksperter, administreret trusselshundetjeneste, MTE, Microsoft-administreret jagttjeneste
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
ms.openlocfilehash: 28533f2ad3fcf547cab95812048b3de8af3bcb9a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592630"
---
# <a name="configure-and-manage-microsoft-threat-experts-capabilities"></a>Konfigurere og Microsoft-trusselseksperter egenskaber

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="before-you-begin"></a>Før du begynder

> [!NOTE]
> Diskuter berettigelseskravene med din Microsoft Technical Service-udbyder og dit kontoteam, inden du ansøge om Microsoft-trusselseksperter – Målrettet angrebsmeddelelse– administreret trusselssøgningstjeneste.

Sørg for, at du har Defender til slutpunkt installeret i dit miljø med enheder, der er tilmeldt, og ikke kun på en konfigureret forbindelse.

Hvis du er Defender for Endpoint-kunde, skal du ansøge om **Microsoft-trusselseksperter –** Målrettede angrebsmeddelelser for at få særlig indsigt og analyse, så du kan identificere de mest kritiske trusler, så du hurtigt kan reagere på dem. Kontakt dit kontoteam eller din Microsoft-repræsentant for at abonnere **på Microsoft-trusselseksperter – Eksperter efter** behov for at kontakte vores trusselseksperter om relevante registreringer og modgangspunkter.

## <a name="apply-for-microsoft-threat-experts---targeted-attack-notifications-service"></a>Anfør dig Microsoft-trusselseksperter - tjeneste til målrettede angrebsmeddelelser

Hvis du allerede er Defender for Endpoint-kunde, kan du anvende den Microsoft 365 Defender portal.

1. I navigationsruden skal du gå **til Indstillinger > Generelt > avancerede funktioner > Microsoft-trusselseksperter – Målrettede angrebsmeddelelser**.

2. Klik på **Anvend**.

    ![Billede af Microsoft-trusselseksperter indstillinger.](images/mte-collaboratewithmte.png)

3. Angiv dit navn og din mailadresse, så Microsoft kan vende tilbage til dig i din ansøgning.

    ![Billede af Microsoft-trusselseksperter program.](images/mte-apply.png)

4. Læs erklæringen [om beskyttelse af personlige](https://privacy.microsoft.com/privacystatement) oplysninger, og **klik derefter på Send** , når du er færdig. Du modtager en velkomstmail, når din ansøgning er godkendt.

    ![Billede af Microsoft-trusselseksperter programbekræftelse.](images/mte-applicationconfirmation.png)

Når den er accepteret, modtager du en velkomstmail, og du  vil se knappen Anvend på en til/fra-knap, der er "til". Hvis du vil tage dig selv ud af tjenesten Målrettede angrebsmeddelelser, skal du skubbe til/fra-knappen "fra" og klikke på Gem indstillinger nederst på siden.

## <a name="where-youll-see-the-targeted-attack-notifications-from-microsoft-threat-experts"></a>Hvor du får vist meddelelser om målrettede angreb fra Microsoft-trusselseksperter

Du kan modtage beskeder om målrettede angreb fra Microsoft-trusselseksperter via følgende medie:

- Siden Hændelser for Defender for **Endpoint-portalen**
- Dashboardet Vigtige beskeder for Defender for **Endpoint-portalen**
- OData-advarsels-API og [REST-API](/windows/security/threat-protection/microsoft-defender-atp/pull-alerts-using-rest-api) [](/windows/security/threat-protection/microsoft-defender-atp/get-alerts)
- [DeviceAlertEvents-tabel](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-devicealertevents-table) i Avanceret jagt
- Din mail, hvis du vælger at konfigurere den

Opret en regel for mailbeskeder for at modtage målrettede meddelelser om angreb via mail.

### <a name="create-an-email-notification-rule"></a>Opret en mailmeddelelsesregel

Du kan oprette regler for afsendelse af mailbeskeder for modtagere af meddelelser. Se  [Konfigurer beskeder for at](configure-email-notifications.md) oprette, redigere, slette eller udføre fejlfinding på mailbeskeder for at få flere oplysninger.

## <a name="view-the-targeted-attack-notification"></a>Få vist meddelelsen om det målrettede angreb

Du begynder at modtage beskeder om målrettede angreb fra din Microsoft-trusselseksperter mail, når du har konfigureret dit system til at modtage mailbeskeder.

1. Klik på linket i mailen for at gå til den tilsvarende beskedkontekst i dashboardet med **Trusselseksperter**.

2. På dashboardet skal du vælge det samme emne, du fik via mailen, for at få vist detaljerne.

## <a name="subscribe-to-microsoft-threat-experts---experts-on-demand"></a>Abonner Microsoft-trusselseksperter - Eksperter on Demand

Dette er tilgængeligt som en abonnementstjeneste. Hvis du allerede er Defender for Endpoint-kunde, kan du kontakte din Microsoft-repræsentant for at abonnere på Microsoft-trusselseksperter - Experts on Demand.

## <a name="consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization"></a>Kontakt en Microsoft-trusselsekspert om mistænkelige aktiviteter for cybersikkerhed i din organisation

Du kan samarbejde med Microsoft-trusselseksperter, der kan være engageret direkte fra portalen Microsoft 365 Defender for at få et rettidigt og nøjagtigt svar. Eksperter giver indsigt for bedre at forstå komplekse trusler, målrettede meddelelser om angreb, du får, eller hvis du har brug for flere oplysninger om beskederne, en potentielt kompromitteret enhed eller en kontekst med trusselsintelligens, som du kan se på portaldashboardet.

> [!NOTE]
>
> - Påmindelsesforespørgsler relateret til organisationens tilpassede data om trusselsintelligens understøttes ikke i øjeblikket. Kontakt sikkerhedshandlinger eller hændelsesresponsteamet for at få flere oplysninger.
> - Du skal have tilladelsen **Administrer** sikkerhedsindstillinger i portalen Microsoft 365 Defender for at kunne sende en "Kontakt en trusselsekspert"-forespørgsel.

1. Gå til portalsiden med de relevante oplysninger, som du gerne vil undersøge, f.eks. **siden** Hændelse. Sørg for, at siden for den relevante besked eller enhed vises, før du sender en undersøgelsesanmodning.

2. I menuen øverst til højre skal du klikke på **?** . Vælg derefter Kontakt **en trusselsekspert**.

    ![Billede Microsoft-trusselseksperter Eksperter efter behov i menuen.](images/mte-eod-menu.png)

    Der åbnes et pop op-skærmbillede. Følgende skærmbillede vises, når du har et prøveabonnement.

    ![Billede af Microsoft-trusselseksperter Experts on Demand-skærmen.](images/mte-eod.png)

    Følgende skærmbillede viser, når du har et fuldt Microsoft-trusselseksperter - Eksperter on-Demand-abonnement.

    ![Billede af Microsoft-trusselseksperter Med eksperter i fuld abonnementsvisning.](images/mte-eod-fullsubscription.png)

    **Emnefeltet Forespørg** er på forhånd udfyldt med linket til den relevante side for din undersøgelsesanmodning. Eksempelvis et link til den hændelse, besked eller side med enhedsoplysninger, du var ved, da du indtalingsanmodningen.

3. I det næste felt skal du angive nok oplysninger til at give Microsoft-trusselseksperter tilstrækkelig kontekst til at starte undersøgelsen.

4. Angiv den mailadresse, du vil bruge til at svare til Microsoft-trusselseksperter.

> [!NOTE]
> Hvis du vil spore status for dine Experts on Demand-sager via Microsoft Services Hub, skal du kontakte din Kundesucces-account manager.

Se denne video for at få en hurtig oversigt over Microsoft Services Hub.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4pk9f]

## <a name="sample-investigation-topics-that-you-can-consult-with-microsoft-threat-experts---experts-on-demand"></a>Emner i forbindelse med stikprøveundersøgelse, som du kan kontakte Microsoft-trusselseksperter - Eksperter efter behov

### <a name="alert-information"></a>Beskedoplysninger

- Vi ser en ny type besked om et binært sted i live-off-the-land: [AlertID]. Kan du fortælle os noget mere om denne besked, og hvordan vi kan undersøge yderligere?
- Vi har observeret to lignende angreb, som forsøger at udføre ondsindede PowerShell-scripts, men genererer forskellige beskeder. Den ene er "Mistænkelig PowerShell-kommandolinje", og den anden er "En skadelig fil blev fundet baseret på en indikation fra O365". Hvad er forskellen?
- Jeg modtager en ulige besked i dag om unormalt antal mislykkede logons fra en brugers enhed med høj profil. Jeg kan ikke finde yderligere beviser omkring disse logonforsøg. Hvordan kan Defender for Endpoint se disse forsøg? Hvilke typer logon overvåges?
- Kan du give mere kontekst eller viden om denne advarsel: "Mistænkelig adfærd af et systemværktøj er blevet observeret".

### <a name="possible-machine-compromise"></a>Muligt maskinforlig

- Kan du hjælpe med at besvare, hvorfor vi ser "Ukendt proces observeret?" Denne meddelelse eller besked ses ofte på mange enheder. Vi sætter pris på eventuelle input for at tydeliggøre, om denne meddelelse eller besked er relateret til ondsindet aktivitet.
- Kan du hjælpe med at validere et muligt kompromis på følgende system den [dato] med lignende funktionsmåder som den forrige registrering af malware i [malwarenavn] på det samme system i [måned]?

### <a name="threat-intelligence-details"></a>Oplysninger om trusselsintelligens

- Vi har registreret en phishing-mail, der har leveret et skadeligt Word-dokument til en bruger. Det skadelige Word-dokument forårsagede en række mistænkelige hændelser, som udløste flere Defender for Endpoint-beskeder for [malware name] malware. Har du nogen oplysninger om denne malware? Hvis ja, kan du sende mig et link?
- Jeg har for nylig set et [reference til sociale medier, f.eks. Twitter eller blog] om en trussel, der er målrettet min branche. Kan du hjælpe mig med at forstå, hvilken beskyttelse Defender for Endpoint giver mod denne trussels agent?

### <a name="microsoft-threat-experts-alert-communications"></a>Microsoft-trusselseksperter' advarselskommunikation

- Kan dit hændelsesresponsteam hjælpe os med at håndtere den målrettede meddelelse om angreb, vi fik?
- Jeg har modtaget denne besked om målrettet angreb fra Microsoft-trusselseksperter. Vi har ikke vores eget hændelsesresponsteam. Hvad kan vi gøre nu, og hvordan kan vi inddæmme hændelsen?
- Jeg har modtaget en meddelelse om målrettet angreb fra Microsoft-trusselseksperter. Hvilke data kan du give os, som vi kan videregive til vores team til hændelsesrespons?

  > [!NOTE]
  > Microsoft-trusselseksperter er en administreret cybersecurity-jagttjeneste og ikke en hændelsesresponstjeneste. Du kan dog tage kontakt til dit eget hændelsesresponsteam for at løse problemer, der kræver en hændelsesrespons. Hvis du ikke har dit eget hændelsesresponsteam og gerne vil have Microsofts hjælp, kan du komme i kontakt med CSS Cybersecurity Incident Response Team (CIRT). De kan åbne en billet for at hjælpe med at håndtere din forespørgsel.

## <a name="scenario"></a>Scenarie

### <a name="receive-a-progress-report-about-your-managed-hunting-inquiry"></a>Modtag en statusrapport om din administrerede forespørgsel

Svar fra Microsoft-trusselseksperter varierer efter din forespørgsel. De sender dig en statusrapport via mail om din  forespørgselsekspert med trusler inden for to dage, så du kan kommunikere undersøgelsesstatus fra følgende kategorier:

- Der er brug for flere oplysninger for at fortsætte undersøgelsen
- En fil eller flere fileksempler er nødvendige for at bestemme den tekniske kontekst
- Undersøgelse kræver mere tid
- De indledende oplysninger var nok til at afslutte undersøgelsen

Det er vigtigt at reagere hurtigt for at holde undersøgelsen i gang.

## <a name="related-topic"></a>Relateret emne

- [Microsoft-trusselseksperter oversigt](microsoft-threat-experts.md)
- [Microsoft-trusselseksperter i Microsoft 365 oversigt](/microsoft-365/security/mtp/microsoft-threat-experts)
