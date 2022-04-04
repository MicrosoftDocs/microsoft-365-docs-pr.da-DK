---
title: Konfigurere og Microsoft-trusselseksperter egenskaber via Microsoft 365 Defender
description: Abonner på Microsoft Threats Experts Microsoft 365 Defender at konfigurere, administrere og bruge det i dine daglige sikkerhedshandlinger og sikkerhedsadministrationsarbejde.
keywords: Microsoft-trusselseksperter, administreret trusselshundetjeneste, MTE, Microsoft-administreret jagttjeneste
search.product: Windows 10
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-maave
author: martyav
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.topic: article
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.openlocfilehash: 8a8de691ff08b50b56c34ed9e779cc97d48c5fcd
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755826"
---
# <a name="configure-and-manage-microsoft-threat-experts-capabilities-through-microsoft-365-defender"></a>Konfigurere og Microsoft-trusselseksperter egenskaber via Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender til Slutpunkt](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

## <a name="before-you-begin"></a>Før du begynder

> [!IMPORTANT]
> Før du anvender, skal du sørge for at diskutere berettigelseskravene til Microsoft-trusselseksperter – Målrettede angrebsmeddelelser administreret trusselssøgningstjeneste med din Microsoft Technical Service-udbyder og kontoteam.

Hvis du vil modtage beskeder om målrettede angreb, skal du Microsoft 365 Defender installeret med enheder, der er tilmeldt. Derefter skal du sende et program via M365-portalen til Microsoft-trusselseksperter - Målrettede angrebsmeddelelser.

Kontakt dit kontoteam eller din Microsoft-repræsentant for at abonnere Microsoft-trusselseksperter - Eksperter efter behov. Eksperter efter behov lader dig kontakte vores trusselseksperter om, hvordan du beskytter din organisation mod relevante registreringer og adversar.

## <a name="apply-for-microsoft-threat-experts---targeted-attack-notifications-service"></a>Anfør dig Microsoft-trusselseksperter - tjeneste til målrettede angrebsmeddelelser

Hvis du allerede har Microsoft Defender til slutpunkt og Microsoft 365 Defender, kan du ansøge om Microsoft-trusselseksperter – målrettede angrebsmeddelelser via deres Microsoft 365 Defender portal.  Målrettede angrebsmeddelelser giver dig særlig indsigt og analyse, så du kan identificere de mest kritiske trusler til organisationen, så du hurtigt kan reagere på dem.

1. I **navigationsruden skal du gå til Indstillinger > Slutpunkter > Generelt > Avancerede funktioner > Microsoft-trusselseksperter – målrettede angrebsmeddelelser**.

2. Vælg **Anvend**.

    :::image type="content" source="../../media/mte/mte-collaboratewithmte.png" alt-text="Siden Microsoft-trusselseksperter indstillinger i Microsoft 365 Defender portal" lightbox="../../media/mte/mte-collaboratewithmte.png":::

3. Angiv dit navn og din mailadresse, så Microsoft kan kontakte dig vedrørende dit program.

    :::image type="content" source="../../media/mte/mte-apply.png" alt-text="Siden Microsoft-trusselseksperter program i Microsoft 365 Defender portal" lightbox="../../media/mte/mte-apply.png":::
  
4. Læs erklæringen [om beskyttelse af personlige](https://privacy.microsoft.com/en-us/privacystatement) oplysninger, og **vælg derefter Send** , når du er færdig. Du modtager en velkomstmail, når din ansøgning er godkendt.

    :::image type="content" source="../../media/mte/mte-applicationconfirmation.png" alt-text="Bekræftelse Microsoft-trusselseksperter program i Microsoft 365 Defender portal" lightbox="../../media/mte/mte-applicationconfirmation.png":::

5. Når du har modtaget din velkomstmail, begynder du automatisk at modtage meddelelser om målrettede angreb.

6. Du kan bekræfte din status ved at **gå til Indstillinger > slutpunkter > Generelle > Avancerede funktioner**. Når den er godkendt **, Microsoft-trusselseksperter til/fra-knappen –** Målrettet angrebsmeddelelse være synlig og **slået Til**.

## <a name="where-youll-see-the-targeted-attack-notifications-from-microsoft-threat-experts"></a>Hvor du får vist meddelelser om målrettede angreb fra Microsoft-trusselseksperter

Du kan modtage besked om målrettede angreb fra Microsoft-trusselseksperter via følgende medier:

- Den Microsoft 365 Defender **portals hændelsesside**
- Den Microsoft 365 Defender portals **dashboard beskeder**
- OData-advarsels-API og [REST-API](/windows/security/threat-protection/microsoft-defender-atp/pull-alerts-using-rest-api) [](/windows/security/threat-protection/microsoft-defender-atp/get-alerts)
- [DeviceAlertEvents-tabel](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-devicealertevents-table) i Avanceret jagt
- Din indbakke, hvis du vælger at få sendt målrettede angrebsmeddelelser til dig via mail. Se [Opret en regel for mailbeskeder](#create-an-email-notification-rule) nedenfor.

### <a name="create-an-email-notification-rule"></a>Opret en mailmeddelelsesregel

Du kan oprette regler for afsendelse af mailbeskeder for modtagere af meddelelser. Du kan få mere at vide  [under Konfigurer beskeder for](/windows/security/threat-protection/microsoft-defender-atp/configure-email-notifications) at oprette, redigere, slette eller foretage fejlfinding af mailmeddelelser.

## <a name="view-targeted-attack-notifications"></a>Få vist målrettede angrebsmeddelelser

Du begynder at modtage beskeder om målrettede angreb fra din Microsoft-trusselseksperter mail, når du har konfigureret dit system til at modtage mailbeskeder.

1. Vælg linket i mailen for at gå til den tilsvarende beskedkontekst i dashboardet med **Trusselseksperter**.

2. På siden **Beskeder skal** du vælge det samme emne med besked som den, du har modtaget i mailen, for at få vist flere oplysninger.

## <a name="subscribe-to-microsoft-threat-experts---experts-on-demand"></a>Abonner Microsoft-trusselseksperter - Eksperter on Demand

Hvis du allerede er Microsoft Defender for Endpoint-kunde, kan du kontakte din Microsoft-repræsentant for at abonnere Microsoft-trusselseksperter - Eksperter on Demand.

## <a name="consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization"></a>Kontakt en Microsoft-trusselsekspert om mistænkelige aktiviteter for cybersikkerhed i din organisation

Du kan kontakte Microsoft-trusselseksperter, der kommer fra Microsoft 365 Defender-portalen. Eksperter kan hjælpe dig med at forstå komplekse trusler og målrettede meddelelser om angreb. Partner med eksperter for at få flere oplysninger om beskeder og hændelser eller råd om håndtering af kompromiser. Få indsigt i den kontekst for trusselsintelligens, der er beskrevet af dit portaldashboard.

> [!NOTE]
>
> - Påmindelsesforespørgsler relateret til organisationens tilpassede data om trusselsintelligens understøttes ikke i øjeblikket. Kontakt dine sikkerhedshandlinger eller dit hændelsesresponsteam for at få flere oplysninger.
> - Du skal have tilladelsen Administrer sikkerhedsindstillinger i **sikkerhedscenter** på Microsoft 365 Defender for at sende en forespørgsel via formularen Kontakt **en trusselsekspert**.

1. Gå til den portalside, der er relateret til de oplysninger, du gerne vil undersøge: f.eks. **Enhed****, Besked** eller **Hændelse**. Kontrollér, at den portalside, der er relateret til din forespørgsel, er i visningen, før du sender en undersøgelsesanmodning.

2. I den øverste menu skal du vælge **? Kontakt en trusselsekspert**.

    :::image type="content" source="../../media/mte/incidents-action-mte-highlighted.png" alt-text="Den Microsoft-trusselseksperter Eksperter on Demand fra menuen i Microsoft 365 Defender portal" lightbox="../../media/mte/incidents-action-mte-highlighted.png":::

    Der åbnes et pop op-skærmbillede.

    Sidehovedet angiver, om du er på et prøveabonnement, eller et fuldt Microsoft-trusselseksperter - Eksperter on-Demand-abonnement.

    :::image type="content" source="../../media/mte/mte-trial.png" alt-text="Skærmbilledet Microsoft-trusselseksperter med prøveversionen af Eksperter on Demand på Microsoft 365 Defender portal" lightbox="../../media/mte/mte-trial.png":::

    Feltet **Undersøgelsesemne** er allerede udfyldt med linket til den relevante side for din anmodning.

3. I det næste felt skal du angive nok oplysninger til at give Microsoft-trusselseksperter tilstrækkelig kontekst til at starte undersøgelsen.

4. Angiv den mailadresse, du vil bruge til at svare til Microsoft-trusselseksperter.

> [!NOTE]
> Hvis du vil spore status for dine Experts on Demand-sager via Microsoft Services Hub, skal du kontakte din tekniske account manager.

Se denne video for at få en hurtig oversigt over Microsoft Services Hub.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4pk9f]

## <a name="sample-investigation-topics"></a>Eksempler på undersøgelsesemner

### <a name="alert-information"></a>Beskedoplysninger

- Vi så en ny type besked om et binært sted til live. Vi kan oplyse besked-id'et. Kan du fortælle os mere om denne besked, og hvordan vi kan undersøge den yderligere?
- Vi har observeret to lignende angreb, som begge forsøger at udføre ondsindede PowerShell-scripts, men genererer forskellige beskeder. Den ene er "Mistænkelig PowerShell-kommandolinje", og den anden er "En skadelig fil blev fundet baseret på en indikation fra O365". Hvad er forskellen?
- Vi har i dag modtaget en underlig besked om et unormalt antal mislykkede logons fra en brugers enhed med høj profil. Vi kan ikke finde yderligere beviser for disse forsøg. Hvordan kan Microsoft 365 Defender se disse forsøg? Hvilke typer logon overvåges?
- Kan du give mere kontekst eller indsigt i advarslen "Mistænkelig adfærd af et systemværktøj er blevet observeret"?
- Jeg har set en besked med titlen "Oprettelse af regel til videresendelse/omdirigering". Jeg mener, at aktiviteten er godartet. Kan du fortælle mig, hvorfor jeg har modtaget en besked?

### <a name="possible-machine-compromise"></a>Muligt maskinforlig

- Kan du hjælpe med at forklare, hvorfor vi ser en meddelelse eller besked om "Ukendt proces, der er observeret" på mange enheder i organisationen? Vi sætter pris på eventuelle input for at tydeliggøre, om denne meddelelse eller besked er relateret til ondsindet aktivitet.
- Kan du hjælpe med at validere et muligt kompromis med følgende system, fra sidste uge? Den opfører sig på samme måde som en tidligere registrering af malware på det samme system for seks måneder siden.

### <a name="threat-intelligence-details"></a>Oplysninger om trusselsintelligens

- Vi har registreret en phishing-mail, der har leveret et skadeligt Word-dokument til en bruger. Dokumentet forårsagede en række mistænkelige hændelser, som udløste flere beskeder for en bestemt malwarefamilie. Har du nogen oplysninger om denne malware? Hvis ja, kan du sende os et link?
- Vi har for nylig set et blogindlæg om en trussel, der er målrettet vores branche. Kan du hjælpe os med at forstå, hvilken beskyttelse Microsoft 365 Defender giver mod denne trussels agent?
- Vi har for nylig observeret en phishingkampagne mod vores organisation. Kan du fortælle os, om det specifikt er rettet mod vores virksomhed eller lodrette?

### <a name="microsoft-threat-experts-alert-communications"></a>Microsoft-trusselseksperter' advarselskommunikation

- Kan dit hændelsesresponsteam hjælpe os med at håndtere den målrettede meddelelse om angreb, vi fik?
- Vi har modtaget denne målrettede meddelelse om angreb fra Microsoft-trusselseksperter. Vi har ikke vores eget hændelsesresponsteam. Hvad kan vi gøre nu, og hvordan kan vi inddæmme hændelsen?
- Vi har modtaget en meddelelse om målrettet angreb fra Microsoft-trusselseksperter. Hvilke data kan du give os, som vi kan videregive til vores team til hændelsesrespons?

> [!NOTE]
> Microsoft-trusselseksperter er en administreret trusselssøgningstjeneste og ikke en hændelsesresponstjeneste. Du kan dog tage kontakt til dit eget hændelsesresponsteam for at løse problemer, der kræver en hændelsesrespons. Hvis du ikke har dit eget hændelsesresponsteam og gerne vil have Microsofts hjælp, kan du komme i kontakt med CSS Cybersecurity Incident Response Team (CIRT). De kan åbne en billet for at hjælpe med at håndtere din forespørgsel.

## <a name="scenario"></a>Scenarie

### <a name="receive-a-progress-report-about-your-managed-hunting-inquiry"></a>Modtag en statusrapport om din administrerede forespørgsel

Svaret fra Microsoft-trusselseksperter vil variere afhængigt af din forespørgsel. Du vil normalt modtage et af følgende svar:

- Der er brug for flere oplysninger for at fortsætte undersøgelsen
- En fil eller flere fileksempler er nødvendige for at bestemme den tekniske kontekst
- Undersøgelse kræver mere tid
- De indledende oplysninger var nok til at afslutte undersøgelsen

Hvis en ekspert anmoder om flere oplysninger eller filprøver, er det vigtigt at reagere hurtigt for at holde undersøgelsen i gang.

## <a name="see-also"></a>Se også

- [Microsoft-trusselseksperter oversigt](microsoft-threat-experts.md)
