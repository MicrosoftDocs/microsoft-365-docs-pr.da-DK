---
title: Aktivér blok ved første øjekast for at registrere malware i sekunder
description: Aktivér blokken ved første øjekast-funktionen for at registrere og blokere malware inden for få sekunder.
keywords: scan, block ved første øjekast, malware, første øjekast, cloud, defender, antivirus
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
ms.openlocfilehash: fb65e1ad898427c3f0a2fc1ba9a13685c1617bc1
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416272"
---
# <a name="turn-on-block-at-first-sight"></a>Slå Bloker når den ses første gang til

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus 

**Platforme**
- Windows

I denne artikel beskrives en antivirus-/antimalwarefunktion, der kaldes "blok ved første øjekast", og den beskriver, hvordan du aktiverer blok ved første øjekast for din organisation.

> [!TIP]
> Denne artikel er beregnet til virksomhedsadministratorer og it-teknikere, der administrerer sikkerhedsindstillinger for organisationer. Hvis du ikke er en enteprise-administrator eller it-Pro, men du har spørgsmål om blok ved første øjekast, skal du se afsnittet [Ikke en virksomhedsadministrator eller it-Pro?](#not-an-enterprise-admin-or-it-pro)

## <a name="what-is-block-at-first-sight"></a>Hvad er "blok ved første øjekast"?

Blok ved første øjekast er en trusselsbeskyttelsesfunktion i næste generations beskyttelse, der registrerer ny malware og blokerer den inden for få sekunder. Blok ved første øjekast er aktiveret, når visse sikkerhedsindstillinger er aktiveret. Disse indstillinger omfatter:

- Skybaseret beskyttelse;
- Et angivet eksempel på timeout for afsendelse (f.eks. 50 sekunder); Og
- Et højt filblokeringsniveau.

I de fleste virksomhedsorganisationer er de indstillinger, der er nødvendige for at aktivere blok ved første øjekast, konfigureret med Microsoft Defender Antivirus udrulninger.

## <a name="how-it-works"></a>Sådan fungerer det

Når Microsoft Defender Antivirus støder på en mistænkelig, men uopdaget fil, forespørger den vores cloudbeskyttelsesbackend. Cloud backend anvender heuristik, maskinel indlæring og automatiseret analyse af filen for at afgøre, om filerne er skadelige eller ej, eller om de er en trussel.

Microsoft Defender Antivirus bruger flere opdagelses- og forebyggelsesteknologier til at levere nøjagtig, intelligent og realtidsbeskyttelse.

:::image type="content" source="images/microsoft-defender-atp-next-generation-protection-engines.png" alt-text="Listen over Microsoft Defender AV-motorer" lightbox="images/microsoft-defender-atp-next-generation-protection-engines.png":::

> [!TIP]
> Du kan få mere at vide under [(Blog) Lær de avancerede teknologier at kende i kernen af Microsoft Defender for Endpoint næste generations beskyttelse](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/).

## <a name="a-few-things-to-know-about-block-at-first-sight"></a>Et par ting at vide om blok ved første øjekast

- I Windows 10 version 1803 eller nyere kan blok ved første øjekast blokere ikke-bærbare eksekverbare filer (f.eks. JS, VBS eller makroer) og eksekverbare filer.

- Block bruger ved første øjekast kun skybeskyttelsesbackend til eksekverbare filer og ikke-bærbare eksekverbare filer, der downloades fra internettet, eller som stammer fra internetzonen. En hashværdi for den .exe fil kontrolleres via cloud-backend for at afgøre, om filen tidligere ikke er registreret.

- Hvis cloudbackend ikke kan træffe en beslutning, låser Microsoft Defender Antivirus filen og uploader en kopi til cloudmiljøet. Clouden udfører mere analyse for at nå frem til en afgørelse, før den enten tillader, at filen kører eller blokerer den i alle fremtidige møder, afhængigt af om det afgør, om filen er ondsindet eller ikke en trussel.

- I mange tilfælde kan denne proces reducere svartiden for ny malware fra timer til sekunder.

- Du kan [angive, hvor længe en fil skal forhindres i at køre](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md) , mens den skybaserede beskyttelsestjeneste analyserer filen. Og du kan [tilpasse den meddelelse, der vises på brugernes skriveborde](/windows/security/threat-protection/windows-defender-security-center/wdsc-customize-contact-information) , når en fil blokeres. Du kan ændre virksomhedens navn, kontaktoplysninger og meddelelsens URL-adresse.

## <a name="turn-on-block-at-first-sight-with-microsoft-intune"></a>Aktivér blok ved første øjekast med Microsoft Intune

> [!TIP]
> Microsoft Intune er nu en del af Microsoft Endpoint Manager.

1. Gå til **Enhedskonfigurationsprofiler** \> i Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com>).

2. Vælg eller opret en profil ved hjælp af profiltypen **Enhedsbegrænsninger** .

3. I profilen **Konfigurationsindstillinger** for enhedens begrænsninger skal du angive eller bekræfte følgende indstillinger under **Microsoft Defender Antivirus**:

   - **Skybaseret beskyttelse**: Aktiveret
   - **Filblokeringsniveau**: Høj
   - **Filtypenavn for filscanning i skyen**: 50
   - **Spørg brugerne, før eksempelindsendelsen sendes**: Send alle data uden at spørge

   :::image type="content" source="../../media/intune-block-at-first-sight.png" alt-text="Intune konfigurationsblok ved første øjekast" lightbox="../../media/intune-block-at-first-sight.png":::

4. Gem dine indstillinger.

> [!TIP]
>
> - Indstilling af filblokeringsniveauet til **Høj** anvender et stærkt registreringsniveau. I det usandsynlige tilfælde, at filblokering medfører en falsk positiv registrering af legitime filer, kan dit sikkerhedsteam gendanne filer, der er [sat i karantæne](./restore-quarantined-files-microsoft-defender-antivirus.md).
> - Du kan få flere oplysninger om konfiguration af Microsoft Defender Antivirus enhedsbegrænsninger i Intune [under Konfigurer indstillinger for enhedsbegrænsning i Microsoft Intune](/intune/device-restrictions-configure).
> - Du kan se en liste over Microsoft Defender Antivirus enhedsbegrænsninger i Intune under [Enhedsbegrænsning for Windows 10 (og nyere) indstillinger i Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

## <a name="turn-on-block-at-first-sight-with-microsoft-endpoint-manager"></a>Slå blok ved første øjekast til med Microsoft Endpoint Manager

> [!TIP]
> Hvis du leder efter Microsoft Endpoint Configuration Manager, er det nu en del af Microsoft Endpoint Manager.

1. I Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) skal du gå til **Endpoint security** \> **Antivirus**.

2. Vælg en eksisterende politik, eller opret en ny politik ved hjælp af **profiltypen Microsoft Defender Antivirus**.

3. Angiv eller bekræft følgende konfigurationsindstillinger:

   - **Slå skybaseret beskyttelse** til: Ja
   - **Skybaseret beskyttelsesniveau**: Høj
   - **Microsoft Defender Antivirus forlænget timeout i sekunder**: 50

   :::image type="content" source="images/endpointmgr-antivirus-cloudprotection.png" alt-text="Indstillinger for blok ved første øjekast på Microsoft Endpoint Manager-portalen" lightbox="images/endpointmgr-antivirus-cloudprotection.png":::

4. Anvend den Microsoft Defender Antivirus profil på en gruppe, f.eks **Alle brugere**, **Alle enheder** eller **Alle brugere og enheder**.

## <a name="turn-on-block-at-first-sight-with-group-policy"></a>Slå blok ved første øjekast til med Gruppepolitik

> [!NOTE]
> Vi anbefaler, at du bruger Intune eller Microsoft Endpoint Manager til at aktivere blok ved første øjekast.

1. Åbn [administrationskonsollen Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) Gruppepolitik, højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg **Rediger**.

2. Brug **redigeringsprogrammet til Gruppepolitik administration** til at gå til **Computerkonfiguration** \> **Administrative skabeloner** \> **Windows Komponenter** \> **Microsoft Defender Antivirus** \> **KORT**.

3. Dobbeltklik på **Konfigurer funktionen 'Blok ved første øjekast'** i sektionen KORT, angiv den til **Aktiveret**, og vælg derefter **OK**.

    > [!IMPORTANT]
    > Hvis du angiver **indstillingen Spørg altid (0),** sænkes beskyttelsestilstanden for enheden. Indstilling til **Send aldrig (2)** betyder, at blok ved første øjekast ikke fungerer.

4. I sektionen MAPS skal du dobbeltklikke på **Send fileksempler, når der kræves yderligere analyse**, og angive den til **Aktiveret**. Under **Send fileksempler, når der kræves yderligere analyse**, skal du vælge **Send alle eksempler** og derefter vælge **OK**.

5. Geninstaller dit Gruppepolitik objekt på tværs af netværket, som du plejer.

## <a name="confirm-block-at-first-sight-is-enabled-on-individual-client-devices"></a>Bekræft blokering ved første øjekast er aktiveret på individuelle klientenheder

Du kan bekræfte, at blokering ved første øjekast er aktiveret på individuelle klientenheder ved hjælp af appen Windows Sikkerhed. Blok ved første øjekast aktiveres automatisk, så længe **cloudbaseret beskyttelse** og **automatisk indsendelse af eksempler** begge er slået til.

1. Åbn appen Windows Sikkerhed.

2. Vælg **Virus & trusselsbeskyttelse**, og vælg derefter **Administrer Indstillinger** under **Indstillinger for beskyttelse mod virus & trusselsbeskyttelse**.

   :::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Mærkaten Virus & threat Protection i Windows Sikkerhed-appen" lightbox="../../media/wdav-protection-settings-wdsc.png":::

3. Bekræft, at **cloudbaseret beskyttelse** og **automatisk indsendelse af eksempler** begge er slået til.

> [!NOTE]
>
> - Hvis de nødvendige indstillinger konfigureres og installeres ved hjælp af Gruppepolitik, nedtones de indstillinger, der er beskrevet i dette afsnit, og de er ikke tilgængelige til brug på individuelle slutpunkter.
> - Ændringer, der foretages via et Gruppepolitik objekt, skal først installeres på individuelle slutpunkter, før indstillingen opdateres i Windows Indstillinger.

## <a name="validate-block-at-first-sight-is-working"></a>Valider, at blok ved første øjekast fungerer

Hvis du vil validere, at funktionen fungerer, skal du downloade [eksempelfilen Blok ved første øjekast](https://demo.wd.microsoft.com/Page/BAFS). Hvis du vil downloade filen, skal du have en konto i Azure AD, der har tildelt rollen Sikkerhedsadministrator eller Global administrator.

Hvis du vil validere, at skyaktiveret beskyttelse fungerer, skal du følge vejledningen i [Valider forbindelser mellem dit netværk og cloudmiljøet](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud).

> [!NOTE]
> Demowebstedet Defender for Endpoint på demo.wd.microsoft.com frarådes og fjernes fremover.

## <a name="turn-off-block-at-first-sight"></a>Slå blok ved første øjekast fra

> [!CAUTION]
> Hvis du slår blokering ved første øjekast fra, sænkes beskyttelsestilstanden for dine enheder og dit netværk.

Du kan vælge at deaktivere blok ved første øjekast, hvis du vil bevare de nødvendige indstillinger uden rent faktisk at bruge beskyttelse ved første øjekast. Du kan midlertidigt slå blokering ved første øjekast fra for at se, hvordan denne funktion påvirker dit netværk. Vi anbefaler dog ikke, at du deaktiverer blokering ved første øjekast permanent.

### <a name="turn-off-block-at-first-sight-with-microsoft-endpoint-manager"></a>Slå blok ved første øjekast fra med Microsoft Endpoint Manager

1. Gå til Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com>), og log på.

2. Gå til **Endpoint security** \> **Antivirus**, og vælg derefter din Microsoft Defender Antivirus politik.

3. Under **Administrer** skal du vælge **Egenskaber**.

4. Ud for **Konfigurationsindstillinger** skal du vælge **Rediger**.

5. Rediger en eller flere af følgende indstillinger:

   - Angiv **Slå skybaseret beskyttelse** til **Nej** eller **Ikke konfigureret**.
   - Indstil **Skybaseret beskyttelsesniveau** til **Ikke konfigureret**.
   - Fjern markeringen i afkrydsningsfeltet for **Microsoft Defender Antivirus forlænget timeout i sekunder**.

6. Gennemse og gem dine indstillinger.

### <a name="turn-off-block-at-first-sight-with-group-policy"></a>Slå blok ved første øjekast fra med Gruppepolitik

1. Åbn [administrationskonsollen for Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) på din Gruppepolitik, højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

2. Ved hjælp af **administrationseditoren til Gruppepolitik** skal du gå til **Computerkonfiguration** og vælge **Administrative skabeloner**.

3. Udvid træet via **Windows komponenter** \> **Microsoft Defender Antivirus** \> **MAPS**.

4. Dobbeltklik på **Konfigurer funktionen 'Blok ved første øjekast'** , og angiv indstillingen til **Deaktiveret**.

    > [!NOTE]
    > Deaktivering af blokering ved første øjekast deaktiverer eller ændrer ikke de påkrævede gruppepolitikker.

## <a name="not-an-enterprise-admin-or-it-pro"></a>Er du ikke virksomhedsadministrator eller it-Pro?

Hvis du ikke er virksomhedsadministrator eller it-Pro, men du har spørgsmål om blok ved første øjekast, er dette afsnit noget for dig. Blok ved første øjekast er en trusselsbeskyttelsesfunktion, der registrerer og blokerer malware inden for få sekunder. Selvom der ikke er en bestemt indstilling, der kaldes "Bloker ved første øjekast", aktiveres funktionen, når visse indstillinger er konfigureret på din enhed.

### <a name="how-to-manage-block-at-first-sight-on-or-off-on-your-own-device"></a>Sådan administrerer du blok ved første øjekast til eller fra på din egen enhed

Hvis du har en personlig enhed, der ikke administreres af en organisation, undrer du dig måske over, hvordan du slår blokering ved første øjekast til eller fra. Du kan bruge appen Windows Sikkerhed til at administrere blok ved første øjekast.

1. Åbn appen Windows Sikkerhed på din Windows 10 eller Windows 11 computer.

2. Vælg **Virus- og trusselsbeskyttelse**.

3. Under **Indstillinger for virus & trusselsbeskyttelse** skal du vælge **Administrer indstillinger**.

4. Benyt en af følgende fremgangsmåder:

   - Hvis du vil aktivere blok ved første øjekast, skal du sørge for, at både **cloudbaseret beskyttelse** og **automatisk indsendelse af eksempler** begge er slået til.

   - Hvis du vil deaktivere blok ved første øjekast, skal du slå **Cloud-leveret beskyttelse** fra eller **Automatisk indsendelse af eksempel**.

     > [!CAUTION]
     > Hvis du slår blok ved første øjekast fra, sænkes beskyttelsesniveauet for din enhed. Vi anbefaler ikke, at blok deaktiveres permanent ved første øjekast.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Aktivér skybaseret beskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Hold dig beskyttet med Windows Sikkerhed](https://support.microsoft.com/windows/stay-protected-with-windows-security-2ae0363d-0ada-c064-8b56-6a39afb6a963)
