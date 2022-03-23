---
title: Registrering og registrering af netværksenhed håndtering af sikkerhedsrisici
description: Sikkerhedsanbefalinger og sikkerhedsrisikoregistrering er nu tilgængelige for operativsystemer til skift, routere, WLAN-controllere og firewalls.
keywords: netværksenheder, sikkerhedsrisikosregistrering på netværksenheder, switche og firewalls i operativsystemer, routere, WLAN-controllere og firewalls
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: levinec
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 2affbe19484348a511487930d034da6799ca348c
ms.sourcegitcommit: 282f3a58b8e11615b3e53328e6b89a6ac52008e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/17/2021
ms.locfileid: "63592148"
---
# <a name="network-device-discovery-and-vulnerability-management"></a>Registrering og registrering af netværksenhed håndtering af sikkerhedsrisici

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

> [!NOTE]
> Blog [om](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/network-device-discovery-and-vulnerability-assessments/ba-p/2267548) \(registrering af netværksenhed og sikkerhedsrisiko er udgivet 04-13-2021 \) og giver indsigt i de nye funktioner til registrering af netværksenhed i Defender til Slutpunkt. Denne artikel indeholder en oversigt over den udfordring,  som netværksenhedsregistrering er designet til at tage hånd om, og detaljerede oplysninger om, hvordan du kommer i gang med at bruge disse nye funktioner.

Funktioner til netværksregistrering er tilgængelige i **sektionen Lager over** enheder på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a> og Microsoft 365 Defender konsoller.

En udpeget Microsoft Defender til slutpunktsenhed skal bruges på hvert netværkssegment til at udføre periodiske godkendte scanninger af forudkonfigurerede netværksenheder. Når De opdages, giver Defender for Endpoints Håndtering af trusler og sikkerhedsrisici-funktioner integrerede arbejdsprocesser til at sikre switche, routere, WLAN-controllere, firewalls og VPN-gateways.

Når netværksenhederne opdages og klassificeres, vil sikkerhedsadministratorer kunne modtage de seneste sikkerhedsanbefalinger og gennemgå de senest opdagede sårbarheder på netværksenheder, der er installeret på tværs af deres organisationer.

## <a name="approach"></a>Fremgangsmåde

Netværksenheder administreres ikke som almindelige slutpunkter, da Defender til Slutpunkt ikke har en sensor indbygget i selve netværksenhederne. Disse typer enheder kræver en agentløs tilgang, hvor en fjernscanning henter de nødvendige oplysninger fra enhederne. Afhængigt af netværkets topologi og egenskaber udfører en enkelt enhed eller nogle få enheder, der er onboardet til Microsoft Defender til slutpunkt, godkendte scanninger af netværksenheder ved hjælp af SNMP (skrivebeskyttet).

Der er to typer enheder, du skal huske på:

- **Vurderingsenhed**: En enhed, der allerede er onboardet, som du skal bruge til at scanne netværksenhederne.
- **Netværksenheder**: De netværksenheder, du planlægger at scanne og onboarde.

### <a name="vulnerability-management-for-network-devices"></a>Administration af sikkerhedsrisiko for netværksenheder

Når netværksenhederne opdages og klassificeres, vil sikkerhedsadministratorer kunne modtage de seneste sikkerhedsanbefalinger og gennemgå de senest opdagede sårbarheder på netværksenheder, der er installeret på tværs af deres organisationer.

## <a name="operating-systems-that-are-supported"></a>Understøttede operativsystemer

Følgende operativsystemer understøttes i øjeblikket:

- Cisco IOS, IOS-XE, NX-OS
- Juniper JUNOS
- HPE ArubaOS, Fremskafskifte software
- Palo Alto Networks PAN-OS

Flere netværksleverandører og operativsystemer tilføjes over tid baseret på data, der er indsamlet fra kundeforbrug. Derfor opfordres du til at konfigurere alle dine netværksenheder, også selvom de ikke er angivet på denne liste.

## <a name="how-to-get-started"></a>Sådan kommer du i gang

Det første trin er at vælge en enhed, der udfører de godkendte netværksscanninger.

1. Beslut dig for en onboardet enhed med Defender til Slutpunkt (klient eller server), der har en netværksforbindelse til administrationsporten for de netværksenheder, du planlægger at scanne.

2. SNMP-trafik mellem bedømmelsesenheden Defender for Endpoint og de målrettede netværksenheder skal være tilladt (f.eks. af firewallen).

3. Beslut, hvilke netværksenheder, der skal vurderes for sårbarheder (f.eks. en Cisco-kontakt eller en Palo Alto Networks-firewall).

4. Sørg for, at SNMP som skrivebeskyttet er aktiveret på alle konfigurerede netværksenheder for at tillade bedømmelsesenheden Defender for Endpoint at forespørge på de konfigurerede netværksenheder. 'SNMP write' er ikke nødvendig for den rette funktionalitet i denne funktion.

5. Hent IP-adresserne på de netværksenheder, der skal scannes (eller de undernet, hvor disse enheder er installeret).

6. Hent SNMP-legitimationsoplysningerne for netværksenhederne (f.eks.: Community String, noAuthNoPriv, authNoPriv, authPriv). Du skal angive legitimationsoplysninger, når du konfigurerer et nyt bedømmelsesjob.

7. Konfiguration af proxyklient: Der kræves ingen ekstra konfiguration ud over kravene til Defender til slutpunktsenhedens proxy.

8. For at tillade, at netværksscanneren godkendes og fungerer korrekt, er det vigtigt, at du tilføjer følgende domæner/URL-adresser:

    - login.windows.net
    - \*.security.microsoft.com
    - login.microsoftonline.com
    - \*.blob.core.windows.net/networkscannerstable/\*

    > [!NOTE]
    > Ikke alle URL-adresser er angivet på den dokumenterede liste over tilladte dataindsamlinger på Defender for Endpoint.

## <a name="permissions"></a>Tilladelser

For at konfigurere bedømmelsesjob er følgende brugertilladelse påkrævet: **Administrer sikkerhedsindstillinger i Defender**. Du kan finde tilladelsen ved at gå til **Indstillinger** \> **Roller**. Få mere at vide under [Opret og administrer roller for rollebaseret adgangskontrol](user-roles.md).

## <a name="install-the-network-scanner"></a>Installér netværksscanneren

1. Gå til **Microsoft 365 sikkerheds Indstillinger** \>  \> **Endpoints** \> **Assessment-job** (under **Netværksvurderinger**).
    1. I portalen Microsoft 365 Defender skal du gå til siden Indstillinger > Assessment-job.

2. Download netværksscanneren, og installér den på den angivne Defender for Endpoint-bedømmelsesenhed.

    > [!div class="mx-imgBorder"]
    > ![Knappen Download scanner.](images/assessment-jobs-download-scanner.png)

## <a name="network-scanner-installation--registration"></a>Installation af netværksscanner & registrering

Log på-processen kan udføres på selve den angivne bedømmelsesenhed eller en anden enhed (f.eks. din personlige klientenhed).

Sådan fuldfører du registreringsprocessen for netværksscanner:

1. Kopiér og følg URL-adressen, der vises på kommandolinjen, og brug den angivne installationskode til at fuldføre registreringsprocessen.

    > [!NOTE]
    > Du skal muligvis ændre indstillingerne for kommandoprompt for at kunne kopiere URL-adressen.

2. Angiv koden, og log på med en Microsoft-konto, der har tilladelsen Defender for Endpoint kaldet "Administrer sikkerhedsindstillinger i Defender".

3. Når du er færdig, får du vist en meddelelse, der bekræfter, at du er logget på.

## <a name="configure-a-new-assessment-job"></a>Konfigurer et nyt bedømmelsesjob

På siden Bedømmelsesjob i **Indstillinger** du vælge **Tilføj netværksvurderingsjob**. Følg opsætningsprocessen for at vælge netværksenheder, der skal scannes regelmæssigt og føjes til enhedens lager.

Hvis du vil forhindre duplikering af enheder på netværkets lager, skal du sørge for, at hver IP-adresse kun er konfigureret én gang på tværs af flere bedømmelsesenheder.

> [!div class="mx-imgBorder"]
> ![Knappen Tilføj netværksvurderingsjob.](images/assessment-jobs-add.png)

Tilføje et netværksvurderingsjobtrin:

1. Vælg et navn til "Bedømmelsesjob" og "Bedømmelsesenhed", som netværksscanneren blev installeret på. Denne enhed udfører de periodiske godkendte scanninger.

2. Tilføj IP-adresser på de netværksenheder, der skal scannes (eller de undernet, hvor disse enheder er installeret).

3. Tilføj påkrævede SNMP-legitimationsoplysninger for målnetværksenhederne.

4. Gem det nyligt konfigurerede netværksvurderingsjob for at starte den periodiske netværksscanning.

### <a name="scan-and-add-network-devices"></a>Scan og tilføj netværksenheder

Under installationen kan du udføre en enkelt testscanning for at bekræfte, at:

- Der er forbindelse mellem bedømmelsesenheden Defender for Endpoint og de konfigurerede målnetværksenheder.
- De konfigurerede SNMP-legitimationsoplysninger er korrekte.

Hver vurderingsenhed kan understøtte scanning med op til 1.500 vellykkede IP-adresser. Hvis du f.eks. scanner 10 forskellige undernet, hvor kun 100 IP-adresser returnerer vellykkede resultater, kan du scanne 1.400 IP-yderligere adresser fra andre undernet på den samme vurderingsenhed.

Hvis der er flere IP-adresseintervaller/undernet, der skal scannes, tager det adskillige minutter at få vist resultaterne af testscanningen. En testscanning vil være tilgængelig for op til 1.024 adresser.

Når resultaterne vises, kan du vælge, hvilke enheder der skal medtages i den periodiske scanning. Hvis du springer visning af scanningsresultaterne over, føjes alle konfigurerede IP-adresser til netværksvurderingsjobbet (uanset enhedens svar). Scanningsresultaterne kan også eksporteres.

## <a name="device-inventory"></a>Lagerenhed

Nyligt fundne enheder vises under den nye **fane Netværksenheder** på **lagersiden for** enheder. Det kan tage op til to timer, efter du har tilføjet et bedømmelsesjob, før enhederne er opdateret.

> [!div class="mx-imgBorder"]
> ![Sektionen Netværksenheder i lagerenhed.](images/assessment-jobs-device-inventory.png)

## <a name="troubleshooting"></a>Fejlfinding

### <a name="network-scanner-installation-has-failed"></a>Installation af netværksscanner mislykkedes

Kontrollér, at de påkrævede URL-adresser føjes til de tilladte domæner i indstillingerne for din firewall. Sørg også for, at proxyindstillingerne er konfigureret som beskrevet i [Konfigurer enhedsproxy og indstillinger for internetforbindelse](configure-proxy-internet.md).

### <a name="the-microsoftcomdevicelogin-web-page-did-not-show-up"></a>Den Microsoft.com/devicelogin webside blev ikke vist

Kontrollér, at de nødvendige URL-adresser føjes til de tilladte domæner i din firewall. Sørg også for, at proxyindstillingerne er konfigureret som beskrevet i [Konfigurer enhedsproxy og indstillinger for internetforbindelse](configure-proxy-internet.md).

### <a name="network-devices-are-not-shown-in-the-device-inventory-after-several-hours"></a>Netværksenheder vises ikke på enhedens lager efter flere timer

Scanningsresultaterne bør opdateres et par timer efter den indledende scanning, der fandt sted, efter at have fuldført jobkonfigurationen for bedømmelsesopgaven.

Hvis enheder stadig ikke vises, skal du bekræfte, at tjenesten 'MdatpNetworkScanService' kører på dine bedømmelsesenheder, hvor du har installeret netværksscanneren, og udføre en "Kør scanning" i den relevante jobkonfiguration for bedømmelse.

Hvis du stadig ikke får resultater efter 5 minutter, skal du genstarte tjenesten.

### <a name="devices-last-seen-time-is-longer-than-24-hours"></a>Enheder, der sidst blev vist, er længere end 24 timer

Valider, at scanneren kører korrekt. Gå derefter til scanningsdefinitionen, og vælg "Kør test". Kontrollér, hvilke fejlmeddelelser der returneres fra de relevante IP-adresser.

### <a name="required-threat-and-vulnerability-management-user-permission"></a>Påkrævet Håndtering af trusler og sikkerhedsrisici brugertilladelse

Registreringen blev afsluttet med en fejl: "Det ser ud til, at du ikke har tilstrækkelige tilladelser til at tilføje en ny agent. Den nødvendige tilladelse er "Administrer sikkerhedsindstillinger i Defender".

Tryk på en tast for at afslutte.

Bed din systemadministrator om at tildele dig de nødvendige tilladelser. Alternativt kan du bede et andet relevant medlem om at hjælpe dig med logonprocessen ved at give dem logonkoden og linket.

### <a name="registration-process-fails-using-provided-link-in-the-command-line-in-registration-process"></a>Registreringsprocessen mislykkes ved hjælp af det angivne link i kommandolinjen i registreringsprocessen

Prøv en anden browser, eller kopiér logonlinket og koden til en anden enhed.

### <a name="text-too-small-or-cant-copy-text-from-command-line"></a>Tekst for lille eller kan ikke kopiere tekst fra kommandolinjen

Skift kommandolinjeindstillinger på din enhed for at tillade kopiering og ændring af tekststørrelsen.

## <a name="related-articles"></a>Relaterede artikler

- [Lagerenhed](machines-view-overview.md)
- [Konfigurere avancerede funktioner](advanced-features.md)
