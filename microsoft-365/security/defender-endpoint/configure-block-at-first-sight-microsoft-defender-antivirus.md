---
title: Aktivér blok ved første syn for at registrere malware på få sekunder
description: Aktivér funktionen Bloker ved første syn for at registrere og blokere malware inden for få sekunder.
keywords: scan, bloker ved første synsviden, malware, første syn, sky, defender, antivirus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: high
author: denisebmsft
ms.author: deniseb
ms.reviewer: marcmcc
manager: dansimp
ms.custom: nextgen
ms.date: 10/18/2021
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 48a411d836669a47479daa68a83a96c3e65b949f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473227"
---
# <a name="turn-on-block-at-first-sight"></a>Slå blok ved første syn til

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

I denne artikel beskrives en antivirus-/antimalwarefunktion, der kaldes "blok ved første syn", og det beskrives, hvordan du aktiverer blok ved første syn for organisationen.

> [!TIP]
> Denne artikel er beregnet til virksomhedsadministratorer og it-fagfolk, der administrerer sikkerhedsindstillinger for organisationer. Hvis du ikke er enteprise-administrator eller it-Pro men du har spørgsmål om blokering ved første øjekast, skal du se afsnittet Ikke en virksomhedsadministrator eller [it-Pro?](#not-an-enterprise-admin-or-it-pro).

## <a name="what-is-block-at-first-sight"></a>Hvad er "blok ved første syn"?

Bloker ved første syn er en trusselsbeskyttelsesfunktion til næste generations beskyttelse, der registrerer ny malware og blokerer den inden for få sekunder. Bloker ved første syn er aktiveret, når visse sikkerhedsindstillinger er aktiveret. Disse indstillinger omfatter:

- Beskyttelse, der leveres i skyen
- Timeout for en angivet prøveafsendelse (f.eks. 50 sekunder). og
- Et niveau af høj til blokering af filer.

I de fleste virksomhedsorganisationer er de nødvendige indstillinger til at aktivere blok ved første syn konfigureret Microsoft Defender Antivirus implementeringer.

## <a name="how-it-works"></a>Sådan fungerer det

Når Microsoft Defender Antivirus støder på en mistænkelig, men ikke-registreret fil, forespørger den i vores cloud protection-backend. Cloud-backend anvender heuristics, maskinlæring og automatiseret analyse af filen for at afgøre, om filerne er skadelige eller ej.

Microsoft Defender Antivirus bruger flere registrerings- og forebyggelsesteknologier til at levere nøjagtig, intelligent og beskyttelse i realtid.

:::image type="content" source="images/microsoft-defender-atp-next-generation-protection-engines.png" alt-text="Listen over Microsoft Defender AV-programmer" lightbox="images/microsoft-defender-atp-next-generation-protection-engines.png":::

> [!TIP]
> Du kan få mere at [vide under (Blog) Lær de avancerede teknologier at kende som kernen Microsoft Defender for Endpoint næste generations beskyttelse](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/).

## <a name="a-few-things-to-know-about-block-at-first-sight"></a>Et par ting, du bør vide om blok ved første synsviden

- I Windows 10 version 1803 eller nyere kan blok ved første syn blokere eksekverbare filer (f.eks. JS, VBS eller makroer) og eksekverbare filer.

- Bloker ved første syn bruger kun cloud protection-backend'en til eksekverbare filer og ikke-bærbare eksekverbare filer, der downloades fra internettet, eller som stammer fra internetzonen. En hash-værdi af filen .exe kontrolleres via cloud-backend for at afgøre, om filen er en fil, der tidligere ikke er blevet registreret.

- Hvis cloud-backend'en ikke kan træffe en beslutning, låser Microsoft Defender Antivirus filen og uploader en kopi til skyen. Skyen udfører flere analyser for at træffe en beslutning, før den enten tillader filen at køre eller blokere den i alle fremtidige møder, afhængigt af om den afgør, om den er skadelig eller ej.

- I mange tilfælde kan denne proces reducere svartiden for ny malware fra timer til sekunder.

- Du kan [angive, hvor længe en fil skal forhindres i at](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md) køre, mens den skybaserede beskyttelsestjeneste analyserer filen. Du kan også tilpasse [den meddelelse, der vises på brugernes skriveborde, når](/windows/security/threat-protection/windows-defender-security-center/wdsc-customize-contact-information) en fil blokeres. Du kan ændre firmanavn, kontaktoplysninger og URL-adresse til meddelelse.

## <a name="turn-on-block-at-first-sight-with-microsoft-intune"></a>Aktivér blok ved første syn med Microsoft Intune

> [!TIP]
> Microsoft Intune er nu en del af Microsoft Endpoint Manager.

1. I administrationen Microsoft Endpoint Manager skal du gå<https://endpoint.microsoft.com> til **Konfigurationsprofiler for** \> **enheder**.

2. Vælg eller opret en profil ved hjælp af **profiltypen Enhedsbegrænsninger** .

3. I **Konfigurationsindstillinger** for profilen Enhedsbegrænsninger skal du angive eller bekræfte følgende indstillinger under **Microsoft Defender Antivirus**:

   - **Beskyttelse, der leveres i skyen**: Aktiveret
   - **Filblokeringsniveau**: Høj
   - **Tidsudvidelse til scanning af filer i skyen**: 50
   - **Spørg brugerne før eksempelindsendelse**: Send alle data uden at spørge

   :::image type="content" source="../../media/intune-block-at-first-sight.png" alt-text="Intune konfigurationsblok ved første synsviden" lightbox="../../media/intune-block-at-first-sight.png":::

4. Gem dine indstillinger.

> [!TIP]
>
> - Indstilling af filblokeringsniveauet **til Høj** anvender et stærkt registreringsniveau. I det usandsynlige tilfælde at filblokering medfører en falsk positiv registrering af legitime filer, kan dit sikkerhedsteam gendanne filer, [der er sat i karantæne](./restore-quarantined-files-microsoft-defender-antivirus.md).
> - Du kan finde flere oplysninger Microsoft Defender Antivirus konfiguration af enhedsbegrænsninger i Intune i [Konfigurer indstillinger for enhedsbegrænsning i Microsoft Intune](/intune/device-restrictions-configure).
> - Du kan finde en Microsoft Defender Antivirus over begrænsninger for Intune under [Enhedsbegrænsning for Windows 10 (og nyere) indstillinger i Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

## <a name="turn-on-block-at-first-sight-with-microsoft-endpoint-manager"></a>Slå blok ved første syn til med Microsoft Endpoint Manager

> [!TIP]
> Hvis du leder efter en Microsoft Endpoint Configuration Manager, er den nu en del Microsoft Endpoint Manager.

1. I Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) skal du gå **til Endpoint security** \> **Antivirus**.

2. Vælg en eksisterende politik, eller opret en ny politik ved hjælp **Microsoft Defender Antivirus af profiltypen**.

3. Angiv eller bekræft følgende konfigurationsindstillinger:

   - **Slå skybaseret beskyttelse til**: Ja
   - **Beskyttelsesniveau, der leveres i skyen**: Høj
   - **Microsoft Defender Antivirus udvidet timeout i sekunder**: 50

   :::image type="content" source="images/endpointmgr-antivirus-cloudprotection.png" alt-text="Bloker indstillinger for første syn i Microsoft Endpoint Manager portal" lightbox="images/endpointmgr-antivirus-cloudprotection.png":::

4. Anvend Microsoft Defender Antivirus på en gruppe, f.eks. **Alle brugere**, **Alle enheder** eller **Alle brugere og enheder**.

## <a name="turn-on-block-at-first-sight-with-group-policy"></a>Aktivér blok ved første syn med Gruppepolitik

> [!NOTE]
> Vi anbefaler, at Intune eller Microsoft Endpoint Manager at slå blok til ved første øjekast.

1. På Gruppepolitik administrationscomputer skal du åbne [Gruppepolitik Administrationskonsol](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og vælge **Rediger**.

2. Ved hjælp **Gruppepolitik Administrationseditor skal** du **gå til Computerkonfiguration** \> **Administrative skabeloner** \> **Windows Components** \> **Microsoft Defender Antivirus** \> **MAPS**.

3. I sektionen KORT skal du dobbeltklikke på Konfigurer funktionen **"Blok** ved første syn", angive den til **Aktiveret** og derefter vælge **OK**.

    > [!IMPORTANT]
    > Hvis du **indstiller til Spørg altid (0** ), sænkes enhedens beskyttelsestilstand. Indstilling til **Send aldrig (2)** betyder, at blok ved første synsfelt ikke fungerer.

4. I sektionen KORT skal du dobbeltklikke på **Send fileksempler**, når yderligere analyse er påkrævet, og angive den til **Aktiveret**. Under **Send fileksempler, når yderligere analyse** er **påkrævet skal du vælge Send alle** eksempler og derefter vælge **OK**.

5. Reploy your Gruppepolitik Object across your network as you usually do.

## <a name="confirm-block-at-first-sight-is-enabled-on-individual-client-devices"></a>Bekræft, at blok ved første syn er aktiveret på individuelle klientenheder

Du kan bekræfte, at blok ved første syn er aktiveret på individuelle klientenheder ved hjælp Windows Sikkerhed app. Blok ved første syn er automatisk aktiveret, så længe **Cloud-leveret beskyttelse** og **Automatisk indsendelse af eksempler** er slået til.

1. Åbn Windows Sikkerhed appen.

2. Vælg **Virus- & trusselsbeskyttelse**, og vælg **derefter & Administrer Indstillinger** under Indstillinger for **Indstillinger**.

   :::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Indstillingsnavnet & for virusbeskyttelse i Windows Sikkerhed appen" lightbox="../../media/wdav-protection-settings-wdsc.png":::

3. Bekræft, **at cloud-leveret beskyttelse** **og automatisk indsendelse af eksempler** begge er slået til.

> [!NOTE]
>
> - Hvis indstillingerne for forudsætninger er konfigureret og installeret ved hjælp Gruppepolitik, bliver de indstillinger, der er beskrevet i dette afsnit, nedtonet og ikke tilgængelige til brug på individuelle slutpunkter.
> - Ændringer, der er foretaget via Gruppepolitik-objekt, skal først installeres til individuelle slutpunkter, før indstillingen opdateres Windows Indstillinger.

## <a name="validate-block-at-first-sight-is-working"></a>Valider, at blok ved første syn virker

Hvis du vil validere, om funktionen virker, skal du [downloade eksempelfilen Bloker ved første syn](https://demo.wd.microsoft.com/Page/BAFS). Hvis du vil downloade filen, skal du bruge en konto i Azure AD, som enten har fået tildelt sikkerhedsadministratorrollen eller den globale administratorrolle.

Hvis du vil validere, om skyaktiveret beskyttelse fungerer, skal du følge vejledningen [i Valider forbindelser mellem dit netværk og skyen](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud).

> [!NOTE]
> Defender for Endpoint-demowebstedet demo.wd.microsoft.com forældet og fjernes fremover.

## <a name="turn-off-block-at-first-sight"></a>Slå blok fra ved første øjekast

> [!CAUTION]
> Hvis du slår blok fra ved første syns gang, sænkes beskyttelsestilstanden for dine enheder og dit netværk.

Du kan vælge at deaktivere blok ved første syn, hvis du vil bevare indstillingerne for forudsætningerne uden rent faktisk at bruge blok ved første synsbeskyttelse. Du kan midlertidigt slå blokering fra for at se, hvordan denne funktion påvirker dit netværk. Vi anbefaler dog ikke permanent deaktivering af blok ved første synsbeskyttelse.

### <a name="turn-off-block-at-first-sight-with-microsoft-endpoint-manager"></a>Slå blok ved første syn Microsoft Endpoint Manager

1. Gå til Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com>), og log på.

2. Gå til **Endpoint security** \> **Antivirus**, og vælg derefter Microsoft Defender Antivirus politik.

3. Vælg **Egenskaber** under **Administrer**.

4. Ud for **Konfigurationsindstillinger** skal du vælge **Rediger**.

5. Rediger en eller flere af følgende indstillinger:

   - Angiv **Slå beskyttelse, der leveres i skyen,** til **Nej** **eller Ikke konfigureret**.
   - Angiv **beskyttelsesniveauet, der leveres i skyen****, til Ikke konfigureret**.
   - Fjern markeringen i afkrydsningsfeltet for **Microsoft Defender Antivirus udvidet timeout i sekunder**.

6. Gennemse og gem dine indstillinger.

### <a name="turn-off-block-at-first-sight-with-group-policy"></a>Slå blok ved første syn Gruppepolitik

1. På Gruppepolitik administrationscomputer skal du åbne [Gruppepolitik Administrationskonsol](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklikke på det Gruppepolitik-objekt, du vil konfigurere, og derefter vælge **Rediger**.

2. Ved hjælp **Gruppepolitik Administration skal du** gå **til Computerkonfiguration** og vælge **Administrative skabeloner**.

3. Udvid træet via **Windows Microsoft Defender Antivirus** \>  \> **MAPS**.

4. Dobbeltklik på Konfigurer **funktionen "Blok ved første syn", og** angiv indstillingen til **Deaktiveret**.

    > [!NOTE]
    > Deaktivering af blok ved første syn deaktiverer eller ændrer ikke de nødvendige gruppepolitikker.

## <a name="not-an-enterprise-admin-or-it-pro"></a>Er du ikke virksomhedsadministrator eller it-Pro?

Hvis du ikke er virksomhedsadministrator eller it-administrator, Pro du har spørgsmål om blok ved første øjekast, er dette afsnit for dig. Bloker ved første syn er en trusselsbeskyttelsesfunktion, der registrerer og blokerer malware inden for få sekunder. Selvom der ikke er en bestemt indstilling kaldet "Bloker ved første syn", er funktionen aktiveret, når visse indstillinger er konfigureret på din enhed.

### <a name="how-to-manage-block-at-first-sight-on-or-off-on-your-own-device"></a>Sådan administreres blok ved første syn til eller fra på din egen enhed

Hvis du har en personlig enhed, der ikke administreres af en organisation, undrer du dig måske over, hvordan du kan slå bloker ved første syn til eller fra. Du kan bruge Windows Sikkerhed til at administrere blok ved første øjekast.

1. På din Windows 10 eller Windows 11 computer skal du åbne Windows Sikkerhed appen.

2. Vælg **Virus- & trusselsbeskyttelse**.

3. Vælg **Administrer & under Indstillinger** for **trusselsbeskyttelse under Virusbeskyttelse**.

4. Gør et af følgende:

   - Hvis du vil aktivere blok ved første syn, skal du sørge for, at både **Cloud-leveret** beskyttelse **og Automatisk indsendelse** af eksempler er slået til.

   - Hvis du vil deaktivere blok ved første syn, skal du deaktivere **Cloud-leveret beskyttelse** **eller Automatisk indsendelse af eksempler**.

     > [!CAUTION]
     > Hvis du slår blok fra ved første syns gang, sænkes beskyttelsesniveauet for din enhed. Vi anbefaler ikke permanent at deaktivere blok ved første synsfelt.


## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Aktivér skybaseret leveringsbeskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Hold dig beskyttet med Windows Sikkerhed](https://support.microsoft.com/windows/stay-protected-with-windows-security-2ae0363d-0ada-c064-8b56-6a39afb6a963)
