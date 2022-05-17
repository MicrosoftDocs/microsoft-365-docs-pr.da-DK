---
title: Registrering og håndtering af sikkerhedsrisici af netværksenheder
description: Sikkerhedsanbefalinger og registrering af sårbarheder er nu tilgængelige for operativsystemer til parametre, routere, WLAN-controllere og firewalls.
keywords: netværksenheder, registrering af sårbarheder på netværksenheder, operativsystemer til parametre, routere, WLAN-controllere og firewalls
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
ms.openlocfilehash: f5c2f1c7c73f150c02192fa7e275a07b12c64c79
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438372"
---
# <a name="network-device-discovery-and-vulnerability-management"></a>Registrering og håndtering af sikkerhedsrisici af netværksenheder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

> [!NOTE]
> Blog udgivet 04-13-2021\) om \([registrering og sårbarheder for netværksenheder](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/network-device-discovery-and-vulnerability-assessments/ba-p/2267548) giver indsigt i de nye funktioner til **registrering af netværksenheder** i Defender for Endpoint. Denne artikel indeholder en oversigt over den udfordring, som **Netværksenhedsregistrering** er designet til at løse, og detaljerede oplysninger om, hvordan du kommer i gang med at bruge disse nye funktioner.

Funktionerne til netværksregistrering er tilgængelige i afsnittet **Enhedsoversigt** på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a> og Microsoft 365 Defender konsoller.

En udpeget Microsoft Defender for Endpoint enhed bruges på hvert netværkssegment til at udføre periodisk godkendte scanninger af forudkonfigurerede netværksenheder. Når funktionerne i Defender for Endpoint er opdaget, leverer de funktioner til Håndtering af trusler og sikkerhedsrisici integrerede arbejdsprocesser, der sikrer fundne parametre, routere, WLAN-controllere, firewalls og VPN-gateways.

Når netværksenhederne er fundet og klassificeret, kan sikkerhedsadministratorer modtage de nyeste sikkerhedsanbefalinger og gennemse de senest registrerede sikkerhedsrisici på netværksenheder, der er installeret på tværs af deres organisationer.

## <a name="approach"></a>Tilgang

Netværksenheder administreres ikke som standardslutpunkter, da Defender for Endpoint ikke har en sensor indbygget i selve netværksenhederne. Disse typer enheder kræver en agentløs tilgang, hvor en fjernscanning henter de nødvendige oplysninger fra enhederne. Afhængigt af netværkstopologien og -egenskaberne udfører en enkelt enhed eller nogle få enheder, der er onboardet til Microsoft Defender for Endpoint godkendte scanninger af netværksenheder ved hjælp af SNMP (skrivebeskyttet).

Der er to typer enheder, du skal være opmærksom på:

- **Vurderingsenhed**: En enhed, der allerede er onboardet, og som du skal bruge til at scanne netværksenhederne.
- **Netværksenheder**: De netværksenheder, du planlægger at scanne og onboarde.

### <a name="vulnerability-management-for-network-devices"></a>Administration af sårbarheder for netværksenheder

Når netværksenhederne er fundet og klassificeret, kan sikkerhedsadministratorer modtage de nyeste sikkerhedsanbefalinger og gennemse de senest registrerede sikkerhedsrisici på netværksenheder, der er installeret på tværs af deres organisationer.

## <a name="operating-systems-that-are-supported"></a>Understøttede operativsystemer

Følgende operativsystemer understøttes i øjeblikket:

- Cisco IOS, IOS-XE, NX-OS
- Juniper JUNOS
- HPE ArubaOS, software til forløbsskift
- Palo Alto Networks PAN-OS

Flere netværksleverandører og os vil blive tilføjet over tid baseret på data indsamlet fra kundeforbrug. Derfor opfordres du til at konfigurere alle dine netværksenheder, selvom de ikke er angivet på denne liste.

## <a name="how-to-get-started"></a>Sådan kommer du i gang

Dit første trin er at vælge en enhed, der skal udføre de godkendte netværksscanninger.

1. Beslut en onboardet Defender for Endpoint-enhed (klient eller server), der har en netværksforbindelse til administrationsporten for de netværksenheder, du planlægger at scanne på.

2. SNMP-trafik mellem Defender for Endpoint-vurderingsenheden og de målrettede netværksenheder skal være tilladt (f.eks. af firewallen).

3. Beslut, hvilke netværksenheder der skal vurderes for sårbarheder (f.eks. en Cisco-switch eller en Palo Alto Networks-firewall).

4. Sørg for, at SNMP er skrivebeskyttet aktiveret på alle konfigurerede netværksenheder, så Defender for Endpoint-vurderingsenheden kan forespørge på de konfigurerede netværksenheder. 'SNMP-skrivning' er ikke nødvendig for at få denne funktion til at fungere korrekt.

5. Hent IP-adresserne på de netværksenheder, der skal scannes (eller de undernet, hvor disse enheder er installeret).

6. Hent SNMP-legitimationsoplysningerne for netværksenhederne (f.eks. Community String, noAuthNoPriv, authNoPriv, authPriv). Du skal angive legitimationsoplysningerne, når du konfigurerer et nyt vurderingsjob.

7. Konfiguration af proxyklient: Der kræves ingen ekstra konfiguration ud over kravene til Defender for Endpoint-enhedsproxyen.

8. Hvis du vil tillade, at netværksscanneren godkendes og fungerer korrekt, er det vigtigt, at du tilføjer følgende domæner/URL-adresser:

    - login.windows.net
    - \*.security.microsoft.com
    - login.microsoftonline.com
    - \*.blob.core.windows.net/networkscannerstable/\*

    > [!NOTE]
    > Ikke alle URL-adresser er angivet på den dokumenterede liste over tilladte datasamlinger i Defender for Endpoint.

## <a name="permissions"></a>Tilladelser

Hvis du vil konfigurere vurderingsjob, kræves følgende indstilling for brugertilladelser: **Administrer sikkerhedsindstillinger i Defender**. Du kan finde tilladelsen ved at gå til **Indstillinger** \> **Roller**. Du kan få flere oplysninger under [Opret og administrer roller for rollebaseret adgangskontrol](user-roles.md).

## <a name="install-the-network-scanner"></a>Installér netværksscanneren

1. Gå til **Microsoft 365 job til vurdering af sikkerhed** \> **Indstillinger** \> **slutpunkter** \> (under **Netværksvurderinger**).
    1. Gå til siden Indstillinger > vurderingsjob på portalen Microsoft 365 Defender.

2. Download netværksscanneren, og installér den på den angivne Defender for Endpoint-vurderingsenhed.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/assessment-jobs-download-scanner.png" alt-text="Knappen Download scanner" lightbox="images/assessment-jobs-download-scanner.png":::

## <a name="network-scanner-installation--registration"></a>Installation af netværksscanner & registrering

Logonprocessen kan fuldføres på selve den angivne vurderingsenhed eller en hvilken som helst anden enhed (f.eks. din personlige klientenhed).

> [!NOTE]
> Både den konto, som brugeren logger på med, og den enhed, der bruges til at fuldføre logonprocessen, skal være i den samme lejer, hvor enheden er onboardet til Microsoft Defender for Endpoint.

Sådan fuldfører du registreringsprocessen for netværksscanneren:

1. Kopiér og følg den URL-adresse, der vises på kommandolinjen, og brug den angivne installationskode til at fuldføre registreringsprocessen.

    > [!NOTE]
    > Du skal muligvis ændre indstillingerne for kommandoprompten for at kunne kopiere URL-adressen.

2. Angiv koden, og log på med en Microsoft-konto, der har tilladelsen Defender for Endpoint med navnet "Administrer sikkerhedsindstillinger i Defender".

3. Når du er færdig, får du vist en meddelelse, der bekræfter, at du er logget på.

## <a name="configure-a-new-assessment-job"></a>Konfigurer et nyt vurderingsjob

På siden Vurderingsjob i **Indstillinger** skal du vælge **Tilføj job til netværksvurdering**. Følg konfigurationsprocessen for at vælge de netværksenheder, der skal scannes regelmæssigt og føjes til enhedens lager.

Hvis du vil forhindre enhedsduplikering i netværksenhedsoversigten, skal du sørge for, at hver IP-adresse kun er konfigureret én gang på tværs af flere vurderingsenheder.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/assessment-jobs-add.png" alt-text="Knappen Tilføj job til netværksvurdering" lightbox="images/assessment-jobs-add.png":::

Tilføjelse af trin til netværksvurderingsjob:

1. Vælg navnet på 'Vurderingsjob' og den 'Vurderingsenhed', som netværksscanneren blev installeret på. Denne enhed udfører de periodiske godkendte scanninger.

2. Tilføj IP-adresser på de destinationsnetværksenheder, der skal scannes (eller de undernet, hvor disse enheder er installeret).

3. Tilføj påkrævede SNMP-legitimationsoplysninger for destinationsnetværksenhederne.

4. Gem det nyligt konfigurerede netværksvurderingsjob for at starte den periodiske netværksscanning.

### <a name="scan-and-add-network-devices"></a>Scan og tilføj netværksenheder

Under konfigurationsprocessen kan du udføre en testscanning én gang for at bekræfte, at:

- Der er forbindelse mellem Defender for Endpoint-vurderingsenheden og de konfigurerede destinationsnetværksenheder.
- De konfigurerede SNMP-legitimationsoplysninger er korrekte.

Hver vurderingsenhed kan understøtte op til 1.500 vellykkede scanninger af IP-adresser. Hvis du f.eks. scanner 10 forskellige undernet, hvor kun 100 IP-adresser returnerer vellykkede resultater, kan du scanne 1.400 yderligere IP-adresser fra andre undernet på den samme vurderingsenhed.

Hvis der er flere IP-adresseområder/undernet, der skal scannes, tager det flere minutter, før resultaterne af testscanningen vises. En testscanning vil være tilgængelig for op til 1.024 adresser.

Når resultaterne vises, kan du vælge, hvilke enheder der skal medtages i den periodiske scanning. Hvis du springer visning af scanningsresultaterne over, føjes alle konfigurerede IP-adresser til netværksvurderingsjobbet (uanset enhedens svar). Scanningsresultaterne kan også eksporteres.

## <a name="device-inventory"></a>Enhedslager

Nyopdagede enheder vises under fanen Nye **netværksenheder** på siden **Enhedsoversigt** . Det kan tage op til to timer, efter at du har tilføjet et vurderingsjob, indtil enhederne er opdateret.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/assessment-jobs-device-inventory.png" alt-text="Afsnittet Netværksenheder i enhedsoversigten" lightbox="images/assessment-jobs-device-inventory.png":::

## <a name="troubleshooting"></a>Fejlfinding

### <a name="network-scanner-installation-has-failed"></a>Installationen af netværksscanneren mislykkedes

Kontrollér, at de påkrævede URL-adresser er føjet til de tilladte domæner i firewallindstillingerne. Sørg også for, at proxyindstillingerne er konfigureret som beskrevet i [Konfigurer enhedsproxy og indstillinger for internetforbindelse](configure-proxy-internet.md).

### <a name="the-microsoftcomdevicelogin-web-page-did-not-show-up"></a>Den Microsoft.com/devicelogin webside blev ikke vist

Kontrollér, at de påkrævede URL-adresser er føjet til de tilladte domæner i firewallen. Sørg også for, at proxyindstillingerne er konfigureret som beskrevet i [Konfigurer enhedsproxy og indstillinger for internetforbindelse](configure-proxy-internet.md).

### <a name="network-devices-are-not-shown-in-the-device-inventory-after-several-hours"></a>Netværksenheder vises ikke i enhedslageret efter flere timer

Scanningsresultaterne skal opdateres et par timer efter den indledende scanning, der fandt sted efter fuldførelse af konfigurationen af vurderingsjobbet.

Hvis enheder stadig ikke vises, skal du kontrollere, at tjenesten 'MdatpNetworkScanService' kører på dine vurderingsenheder, hvor du har installeret netværksscanneren, og udføre en "Kør scanning" i den relevante konfiguration af vurderingsjobbet.

Hvis du stadig ikke får resultater efter 5 minutter, skal du genstarte tjenesten.

### <a name="devices-last-seen-time-is-longer-than-24-hours"></a>Det tidspunkt, hvor enheder sidst blev set, er længere end 24 timer

Kontrollér, at scanneren kører korrekt. Gå derefter til scanningsdefinitionen, og vælg "Kør test". Kontrollér, hvilke fejlmeddelelser der returneres fra de relevante IP-adresser.

### <a name="required-threat-and-vulnerability-management-user-permission"></a>Påkrævet Håndtering af trusler og sikkerhedsrisici brugertilladelse

Registreringen blev afsluttet med en fejl: "Det ser ud til, at du ikke har tilstrækkelige tilladelser til at tilføje en ny agent. Den påkrævede tilladelse er "Administrer sikkerhedsindstillinger i Defender"."

Tryk på en vilkårlig tast for at afslutte.

Bed systemadministratoren om at tildele dig de nødvendige tilladelser. Alternativt kan du bede et andet relevant medlem om at hjælpe dig med logonprocessen ved at angive logonkoden og linket.

### <a name="registration-process-fails-using-provided-link-in-the-command-line-in-registration-process"></a>Registreringsprocessen mislykkes ved hjælp af det angivne link i kommandolinjen i registreringsprocessen

Prøv en anden browser, eller kopiér logonlinket og -koden til en anden enhed.

### <a name="text-too-small-or-cant-copy-text-from-command-line"></a>Teksten er for lille eller kan ikke kopieres fra kommandolinjen

Skift kommandolinjeindstillinger på enheden for at tillade kopiering og ændre tekststørrelse.

## <a name="related-articles"></a>Relaterede artikler

- [Enhedslager](machines-view-overview.md)
- [Konfigurer avancerede funktioner](advanced-features.md)
