---
title: Konfigurer og administrer Microsoft Threat Experts-funktioner via Microsoft 365 Defender
description: Abonner på Microsoft Threats Experts via Microsoft 365 Defender for at konfigurere, administrere og bruge det i dine daglige sikkerhedshandlinger og sikkerhedsadministrationsarbejde.
keywords: Microsoft Threat Experts, managed threat hunting service, MTE, Microsoft managed hunting service
search.product: Windows 10
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: martyav
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.topic: article
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.openlocfilehash: 56ee73cfe57b4177bae45d84a1bee10830a09673
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/07/2022
ms.locfileid: "65922969"
---
# <a name="configure-and-manage-microsoft-threat-experts-capabilities-through-microsoft-365-defender"></a>Konfigurer og administrer Microsoft Threat Experts-funktioner via Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

## <a name="before-you-begin"></a>Før du begynder

> [!IMPORTANT]
> Før du ansøger, skal du sørge for at drøfte berettigelseskravene for Microsoft Threat Experts – Targeted Attack Notifications managed threat hunting service med din Microsoft Technical Service-udbyder og dit kontoteam.

Hvis du vil modtage meddelelser om målrettede angreb, skal Du have Microsoft 365 Defender installeret med tilmeldte enheder. Send derefter et program via M365-portalen for Microsoft Threat Experts – Målrettede angrebsmeddelelser.

Kontakt dit kontoteam eller din Microsoft-repræsentant for at abonnere på Microsoft Threat Experts – Experts on Demand. Eksperter on Demand giver dig mulighed for at rådføre dig med vores trusselseksperter om, hvordan du beskytter din organisation mod relevante opdagelser og modstandere.

## <a name="apply-for-microsoft-threat-experts---targeted-attack-notifications-service"></a>Ansøg om Microsoft Threat Experts – Tjenesten for målrettede angrebsmeddelelser

Hvis du allerede har Microsoft Defender for Endpoint og Microsoft 365 Defender, kan du ansøge om Microsoft Threat Experts – Målrettede angrebsmeddelelser via deres Microsoft 365 Defender-portal.  Målrettede angrebsmeddelelser giver dig særlig indsigt og analyse for at identificere de mest kritiske trusler mod din organisation, så du kan reagere hurtigt på dem.

1. I navigationsruden skal du gå til **Indstillinger > Slutpunkter > Generelle > Avancerede funktioner > Microsoft Threat Experts – Målrettede angrebsmeddelelser**.

2. Vælg **Anvend**.

    :::image type="content" source="../../media/mte/mte-collaboratewithmte.png" alt-text=" Siden med indstillinger for Microsoft Threat Experts på Microsoft 365 Defender-portalen" lightbox="../../media/mte/mte-collaboratewithmte.png":::

3. Angiv dit navn og din mailadresse, så Microsoft kan kontakte dig om dit program.

    :::image type="content" source="../../media/mte/mte-apply.png" alt-text="Programsiden Microsoft Threat Experts på Microsoft 365 Defender-portalen" lightbox="../../media/mte/mte-apply.png":::
  
4. Læs [erklæringen om beskyttelse af personlige oplysninger](https://privacy.microsoft.com/en-us/privacystatement), og vælg derefter **Send** , når du er færdig. Du modtager en velkomstmail, når din ansøgning er godkendt.

    :::image type="content" source="../../media/mte/mte-applicationconfirmation.png" alt-text="Bekræftelse af programmet Microsoft Threat Experts på Microsoft 365 Defender-portalen" lightbox="../../media/mte/mte-applicationconfirmation.png":::

5. Når du har modtaget din velkomstmail, begynder du automatisk at modtage målrettede angrebsmeddelelser.

6. Du kan bekræfte din status ved at gå **til Indstillinger > Slutpunkter > Generelle > Avancerede funktioner**. Når den er godkendt, er til/fra-knappen **Microsoft Threat Experts – Målrettet angrebsmeddelelse** synlig og **tændt**.

## <a name="where-youll-see-the-targeted-attack-notifications-from-microsoft-threat-experts"></a>Her kan du se de målrettede angrebsmeddelelser fra Microsoft Threat Experts

Du kan modtage målrettede angrebsmeddelelser fra Microsoft Threat Experts via følgende medier:

- Siden **Hændelser** på Microsoft 365 Defender-portalen
- **Dashboardet Beskeder** på Microsoft 365 Defender-portalen
- API [til](/windows/security/threat-protection/microsoft-defender-atp/get-alerts) OData-beskeder og [REST API](/windows/security/threat-protection/microsoft-defender-atp/pull-alerts-using-rest-api)
- [DeviceAlertEvents-tabel](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-devicealertevents-table) i avanceret jagt
- Din indbakke, hvis du vælger at få tilsendt målrettede angrebsmeddelelser via mail. Se [Opret en regel for meddelelse via mail](#create-an-email-notification-rule) nedenfor.

### <a name="create-an-email-notification-rule"></a>Opret en regel for mailmeddelelser

Du kan oprette regler for at sende mailmeddelelser til meddelelsesmodtagere. Du kan finde alle detaljer under  [Konfigurer beskeder om](/windows/security/threat-protection/microsoft-defender-atp/configure-email-notifications) oprettelse, redigering, sletning eller fejlfinding af mailmeddelelser.

## <a name="view-targeted-attack-notifications"></a>Få vist meddelelser om målrettede angreb

Du begynder at modtage målrettet angrebsmeddelelse fra Microsoft Threat Experts i din mail, når du har konfigureret dit system til at modtage en mailmeddelelse.

1. Vælg linket i mailen for at gå til den tilsvarende beskedkontekst på dashboardet, der er mærket med **Threat-eksperter**.

2. På siden **Beskeder** skal du vælge det samme emne for beskeder som det, du modtog i mailen, for at få vist flere oplysninger.

## <a name="subscribe-to-microsoft-threat-experts---experts-on-demand"></a>Abonner på Microsoft Threat Experts – Eksperter on Demand

Hvis du allerede er Microsoft Defender for Endpoint-kunde, kan du kontakte din Microsoft-repræsentant for at abonnere på Microsoft Threat Experts – Experts on Demand.

## <a name="consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization"></a>Kontakt en Microsoft-trusselsekspert om mistænkelige cybersikkerhedsaktiviteter i din organisation

Du kan kontakte Microsoft Threat Experts inde fra Microsoft 365 Defender-portalen. Eksperter kan hjælpe dig med at forstå komplekse trusler og målrettede angrebsmeddelelser. Partner med eksperter for at få yderligere oplysninger om beskeder og hændelser eller rådgivning om håndtering af kompromiser. Få indsigt i konteksten for trusselsintelligens, der er beskrevet af dit portaldashboard.

> [!NOTE]
>
> - Vigtige forespørgsler, der er relateret til din organisations tilpassede trusselsintelligensdata, understøttes ikke i øjeblikket. Kontakt dit team for sikkerhedshandlinger eller svar på hændelser for at få flere oplysninger.
> - Du skal have tilladelse til at **administrere sikkerhedsindstillingerne i Security Center** på Microsoft 365 Defender-portalen for at kunne sende en forespørgsel via formularen **Kontakt en trusselsekspert** .

1. Gå til portalsiden, der er relateret til de oplysninger, du vil undersøge: f.eks **. Enhed**, **Besked** eller **Hændelse**. Sørg for, at den portalside, der er relateret til din forespørgsel, er i visningen, før du sender en undersøgelsesanmodning.

2. Vælg ? i den øverste menu **Kontakt en trusselsekspert**.

    :::image type="content" source="../../media/mte/incidents-action-mte-highlighted.png" alt-text="Microsoft Threat Experts Experts on Demand fra menuen på Microsoft 365 Defender-portalen" lightbox="../../media/mte/incidents-action-mte-highlighted.png":::

    Der åbnes en pop op-skærm.

    Overskriften angiver, om du er på et prøveabonnement eller et komplet abonnement fra Microsoft Threat Experts – Experts on-Demand.

    :::image type="content" source="../../media/mte/mte-trial.png" alt-text="Skærmen Microsoft Threat Experts Experts on Demand-prøveabonnement på Microsoft 365 Defender-portalen" lightbox="../../media/mte/mte-trial.png":::

    Emnefeltet **Undersøgelse** udfyldes allerede med linket til den relevante side for din anmodning.

3. I det næste felt skal du angive tilstrækkelige oplysninger til at give Microsoft Threat Experts tilstrækkelig kontekst til at starte undersøgelsen.

4. Angiv den mailadresse, du vil bruge til at svare til Microsoft Threat Experts.

> [!NOTE]
> Hvis du vil spore status for dine Eksperter on Demand-sager via Microsoft Services Hub, skal du kontakte din tekniske account manager.

Se denne video for at få et hurtigt overblik over Microsoft Services Hub.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4pk9f]

## <a name="sample-investigation-topics"></a>Emneeksempel på undersøgelse

### <a name="alert-information"></a>Beskedoplysninger

- Vi så en ny type alarm for en binær fil, der lever af jorden. Vi kan angive besked-id'et. Kan du fortælle os mere om denne besked, og hvordan vi kan undersøge den yderligere?
- Vi har observeret to lignende angreb, som begge forsøger at udføre skadelige PowerShell-scripts, men genererer forskellige beskeder. Den ene er "Mistænkelig PowerShell-kommandolinje", og den anden er "Der blev registreret en skadelig fil baseret på indikation fra O365". Hvad er forskellen?
- Vi har modtaget en ulige besked i dag om et unormalt antal mislykkede logons fra en højtprofileret brugers enhed. Vi kan ikke finde flere beviser for disse forsøg. Hvordan kan Microsoft 365 Defender se disse forsøg? Hvilken type logon overvåges?
- Kan du give mere kontekst eller indsigt om beskeden, "Mistænkelig adfærd af et system utility blev observeret"?
- Jeg observerede en besked med titlen "Oprettelse af regel for videresendelse/omdirigering". Jeg tror, at aktiviteten er godartet. Kan du fortælle mig, hvorfor jeg modtog en besked?

### <a name="possible-machine-compromise"></a>Muligt computer kompromitteret

- Kan du hjælpe med at forklare, hvorfor vi får vist en meddelelse eller besked om "Ukendt proces observeret" på mange enheder i vores organisation? Vi sætter pris på ethvert input for at afklare, om denne meddelelse eller besked er relateret til skadelig aktivitet.
- Kan du hjælpe med at validere et muligt kompromis på følgende system, der stammer fra sidste uge? Det opfører sig på samme måde som en tidligere malware opdagelse på det samme system seks måneder siden.

### <a name="threat-intelligence-details"></a>Oplysninger om trusselsintelligens

- Vi har fundet en phishing-mail, der har leveret et skadeligt Word-dokument til en bruger. Dokumentet forårsagede en række mistænkelige hændelser, som udløste flere beskeder for en bestemt malwarefamilie. Har du nogen oplysninger om denne malware? Hvis ja, kan du så sende os et link?
- Vi har for nylig set et blogindlæg om en trussel, der er rettet mod vores branche. Kan du hjælpe os med at forstå, hvilken beskyttelse Microsoft 365 Defender giver mod denne trusselsaktør?
- Vi har for nylig observeret en phishing-kampagne, der er udført mod vores organisation. Kan du fortælle os, om dette var målrettet specifikt til vores virksomhed eller vertikalt?

### <a name="microsoft-threat-experts-alert-communications"></a>Beskedkommunikation fra Microsoft Threat Experts

- Kan dit team for svar på hændelser hjælpe os med at håndtere den målrettede angrebsmeddelelse, vi fik?
- Vi har modtaget denne meddelelse om målrettede angreb fra Microsoft Threat Experts. Vi har ikke vores eget team for svar på hændelser. Hvad kan vi gøre nu, og hvordan kan vi begrænse hændelsen?
- Vi har modtaget en målrettet angrebsmeddelelse fra Microsoft Threat Experts. Hvilke data kan du give os, som vi kan videregive til vores team for svar på hændelser?

> [!NOTE]
> Microsoft Threat Experts er en administreret trusselsjagttjeneste og ikke en hændelsessvartjeneste. Du kan dog interagere med dit eget team for svar på hændelser for at løse problemer, der kræver et svar på en hændelse. Hvis du ikke har dit eget team for svar på hændelser og gerne vil have Microsofts hjælp, kan du interagere med CSS Cybersecurity Incident Response Team (CIRT). De kan åbne en billet for at hjælpe med at løse din forespørgsel.

## <a name="scenario"></a>Scenario

### <a name="receive-a-progress-report-about-your-managed-hunting-inquiry"></a>Modtag en statusrapport om din administrerede jagtforespørgsel

Svaret fra Microsoft Threat Experts varierer afhængigt af din forespørgsel. Du modtager normalt et af følgende svar:

- Der er brug for flere oplysninger for at fortsætte undersøgelsen
- Der kræves en fil eller flere fileksempler for at bestemme den tekniske kontekst
- Undersøgelsen kræver mere tid
- De indledende oplysninger var tilstrækkelige til at afslutte undersøgelsen

Hvis en ekspert anmoder om flere oplysninger eller fileksempler, er det afgørende at reagere hurtigt for at holde undersøgelsen i gang.

## <a name="see-also"></a>Se også

- [Oversigt over Microsoft Threat Experts](microsoft-threat-experts.md)
