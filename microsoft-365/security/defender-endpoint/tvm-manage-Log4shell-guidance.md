---
title: Få mere at vide om, hvordan du afhjælper Log4Shell-sårbarheden i Microsoft Defender for Endpoint – Håndtering af trusler og sikkerhedsrisici
description: Få mere at vide om, hvordan du afhjælper Log4Shell-sårbarheden i Microsoft Defender for Endpoint
keywords: tvm, lo4j
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365-initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 6e265490eb5afee275debcdd1eb073f11bb845e3
ms.sourcegitcommit: 8101c12df67cfd9c15507b0133c23ce4cca1c6ba
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66858982"
---
# <a name="learn-how-to-manage-the-log4shell-vulnerability-in-microsoft-defender-for-endpoint"></a>Få mere at vide om, hvordan du administrerer Log4Shell-sårbarheden i Microsoft Defender for Endpoint

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Trussels- og sårbarhedsstyring](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Log4Shell-sikkerhedsrisikoen er en RCE-sikkerhedsrisiko (remote code execution), der findes i Logføringsbiblioteket Apache Log4j 2. Da Apache Log4j 2 ofte bruges af mange softwareprogrammer og onlinetjenester, repræsenterer det en kompleks og højrisikosituation for virksomheder over hele verden. Kaldet "Log4Shell" ([CVE-2021-44228](https://cve.mitre.org/cgi-bin/cvename.cgi?name=2021-44228), [CVE-2021-45046](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-45046) ) introducerer en ny angrebsvektor, som angribere kan udnytte til at udtrække data og installere ransomware i en organisation.

> [!NOTE]
> Se blogs [Vejledning til forebyggelse, registrering og jagt efter udnyttelse af Log4j 2-sårbarheden og](https://www.microsoft.com/security/blog/2021/12/11/guidance-for-preventing-detecting-and-hunting-for-cve-2021-44228-log4j-2-exploitation/) [Microsoft Security Response Center](https://msrc-blog.microsoft.com/2021/12/11/microsofts-response-to-cve-2021-44228-apache-log4j2/) for at få vejledning og tekniske oplysninger om sårbarheden og produktspecifikke afhjælpningsanbefalinger for at beskytte din organisation.

## <a name="overview-of-discovery-monitoring-and-mitigation-capabilities"></a>Oversigt over registrerings-, overvågnings- og afhjælpningsfunktioner

Administration af trusler og sårbarheder giver dig følgende funktioner, der kan hjælpe dig med at identificere, overvåge og afhjælpe din organisations eksponering for Log4Shell-sårbarheden:

- **Registrering**: Registrering af eksponerede enheder, både Microsoft Defender for Endpoint onboardede enheder samt enheder, der er blevet opdaget, men endnu ikke er onboardet, er baseret på sårbar software og sårbare filer, der er registreret på disken.
- **Trusselsbevidsthed:** En samlet visning til at vurdere din organisations eksponering. Denne visning viser din eksponering på enhedsniveau og softwareniveau og giver adgang til oplysninger om sårbare filer, f.eks. sidste gang den blev set, sidste gang den blev udført, og sidste gang den blev udført med åbne porte. Du kan bruge disse oplysninger til at prioritere dine afhjælpningshandlinger. Det kan tage op til 24 timer, før data, der er relateret til eksponerede enheder, vises på dashboardet.
- **Indstillinger for afhjælpning:** Anvend afhjælpningsmuligheder som en hjælp til at reducere eksponeringsrisikoen.
- **Avanceret jagt:** Brug avanceret jagt til at returnere oplysninger om sårbare log4j-filer, der er identificeret på disken.

> [!NOTE]
> Disse funktioner understøttes på Windows 10 & Windows 11, Windows Server, Linux og macOS.
>
> Support på Linux kræver Microsoft Defender for Endpoint Linux-klientversion 101.52.57 (30.121092.15257.0) eller nyere.
>
> Support på macOS kræver Microsoft Defender for Endpoint macOS-klientversion 20.121111.15416.0 eller nyere.
>
>Du kan få flere oplysninger om understøttede versioner under [Understøttede operativsystemer og -funktioner](tvm-supported-os.md).

## <a name="exposed-devices-discovery"></a>Registrering af eksponerede enheder

Integrerede Håndtering af trusler og sikkerhedsrisici funktioner hjælper dig med at finde de enheder, der er udsat for Log4Shell-sårbarheden, sammen med aktivering af Log4j-registrering på Microsoft 365 Defender-portalen.

Onboardede enheder vurderes ved hjælp af eksisterende integrerede Håndtering af trusler og sikkerhedsrisici funktioner, der kan finde sårbar software og filer.

Log4j-registrering skal være aktiveret for registrering på registrerede enheder, men endnu ikke onboardede enheder. Dette starter sonder på samme måde, som enhedsregistrering aktivt undersøger dit netværk. Dette omfatter undersøgelse fra flere onboardede slutpunkter (Windows 10+ og Windows Server 2019+ enheder) og kun sondering i undernet for at registrere enheder, der er sårbare og fjernudsat for CVE-2021-44228.

Sådan aktiveres Log4-registrering:

1. Gå til **Indstillinger** > **Konfiguration** **af enhedsregistrering** > 
2. Vælg **Aktivér log4j2-registrering (CVE-2021-44228)**
3. Vælg **Gem**

:::image type="content" source="images/enable_log4j.png" alt-text="Indstilling til aktivering af log4j2-registrering" lightbox="images/enable_log4j.png":::

Kørsel af disse sonder udløser log4j-standardflowet uden at forårsage skadelige virkninger på enten den enhed, der undersøges, eller på sondeenheden. Selve probing udføres ved at sende flere HTTP-anmodninger til registrerede enheder, der er målrettet til almindelige webprogramporte (f.eks. 80.8000.8080.443.8443) og URL-adresser. Anmodningen indeholder HTTP-headere med en JNDI-nyttedata, der udløser en DNS-anmodning fra den undersøgede computer.

For eksempel brugeragent: ${jndi:dns://192.168.1.3:5353/MDEDiscoveryUser-Agent}, hvor 192.168.1.3 er IP for probingmaskinen.

> [!NOTE]
> Aktivering af Log4j2-registrering betyder også, at onboardede enheder bruger selvtestning til at registrere lokale sikkerhedsrisici.

## <a name="vulnerable-software-and-files-detection"></a>Sårbar software- og filregistrering

Administration af trusler og sårbarheder indeholder opdagelseslag, der kan hjælpe dig med at finde:

- **Sårbar software**: Registrering er baseret på installerede CPE-optællinger (Application Common Platform Enerations), der er kendt for at være sårbare over for udførelse af log4j-fjernkode.
- **Sårbare filer:** Både filer i hukommelsen og filer i filsystemet vurderes. Disse filer kan være Log4j-core jar-filer med den kendte sårbare version eller en Uber-JAR, der indeholder enten en sårbar jndi-opslagsklasse eller en sårbar log4j-kernefil. Specifikt er det:

  - bestemmer, om en JAR-fil indeholder en sårbar Log4j-fil ved at undersøge JAR-filer og søge efter følgende fil:   \\META-INF\\maven\\org.apache.logging.log4j\\log4j-core\\pom.properties – hvis denne fil findes, læses og pakkes Log4j-versionen ud.
  - søger efter filen JndiLookup.class i JAR-filen ved at søge efter stier, der indeholder strengen "/log4j/core/lookup/JndiLookup.class" – hvis filen JndiLookup.class findes, bestemmer Håndtering af trusler og sikkerhedsrisici, om denne JAR indeholder en Log4j-fil med den version, der er defineret i pom.properties.
  - søger efter sårbare Log4j-kerne JAR-filer, der er integreret i en indlejret JAR, ved at søge efter stier, der indeholder en af disse strenge:
    - lib/log4j-core-
    - WEB-INF/lib/log4j-core-
    - App-INF/lib/log4j-core-

I denne tabel beskrives de søgefunktioner, der understøttes af platforme og versioner:

|Kapacitet|Filtype|Windows10+,<br>server2019+|Server 2012R2,<br>server2016|Server 2008R2|Linux + macOS|
|:---|:---|:---|:---|:---|:---|
|Søg i hukommelsen  | Log4j-kerne | Ja |Ja<sup>[1]| - | Ja |
| |Uber-JARs | Ja |Ja<sup>[1]| - | Ja |
| Søg i alle filer på disken  |Log4j-kerne | Ja |Ja<sup>[1]| Ja | - |
| | Uber-JARs|Ja |Ja<sup>[1]| - | -|

(1) Funktioner er tilgængelige, når [KB5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) er installeret på Windows Server 2012 R2 og 2016.

## <a name="learn-about-your-log4shell-exposure-and-mitigation-options"></a>Få mere at vide om dine indstillinger for Log4Shell-eksponering og -afhjælpning

### <a name="threat-and-vulnerability-management-dashboard"></a>Dashboard til administration af trusler og sårbarheder

Brug det Håndtering af trusler og sikkerhedsrisici dashboard til at se din aktuelle eksponering.

1. På Microsoft 365 Defender-portalen skal du gå til **Dashboard** > **threat awareness til** administration  >  af **sårbarheder**:
:::image type="content" source="images/awareness_dashboard.png" alt-text="Widgetten trusselsbevidsthed på dashboardet til administration af sårbarheder" lightbox="images/awareness_dashboard.png":::
2. Vælg **Vis oplysninger om sårbarheder** for at se den samlede visning af din organisations eksponering.
:::image type="content" source="images/view_vulnerability_details.png" alt-text="Siden med oplysninger om sårbarheder for CVE-2021-44228 (Log4j)" lightbox="images/view_vulnerability_details.png":::
3. Vælg den relevante fane for at se eksponeringen opdelt efter:
    - Eksponerede enheder – onboard
    - Eksponerede enheder – ikke onboardet
    - Sårbare filer
    - Sårbar software

### <a name="log4shell-vulnerability-mitigation"></a>Afhjælpning af Log4Shell-sårbarhed

Sikkerhedsrisikoen log4Shell kan afhjælpes ved at forhindre JNDI-opslag i Log4j version 2.10 - 2.14.1 med standardkonfigurationer. Hvis du vil oprette denne afhjælpningshandling, skal du bruge **dashboardet Trusselsbevidsthed**:

1. Vælg **Vis detaljer om sårbarhed**
2. Vælg **afhjælpningsindstillinger**

Du kan vælge at anvende afhjælpningen på alle eksponerede enheder eller vælge bestemte onboardede enheder. Hvis du vil fuldføre processen og anvende afhjælpningen på enheder, skal du vælge **Opret afhjælpningshandling**.

:::image type="content" source="images/mitigation_options.png" alt-text="Afhjælpningsmuligheder for CVE-2021-44228" lightbox="images/mitigation_options.png":::

### <a name="mitigation-status"></a>Afhjælpningsstatus

Afhjælpningsstatussen angiver, om afhjælpningen af den midlertidige løsning til deaktivering af JDNI-opslag er blevet anvendt på enheden. Du kan få vist afhjælpningsstatus for hver berørt enhed under fanerne Eksponerede enheder. Dette kan hjælpe med at prioritere afhjælpning og/eller programrettelse af enheder baseret på deres afhjælpningsstatus.

:::image type="content" source="images/mitigation_status.png" alt-text="Mulige afhjælpningsstatusser" lightbox="/mitigation_status.png":::

I nedenstående tabel vises de potentielle afhjælpningsstatusser:

| Afhjælpningsstatus | Beskrivelse |
|:---|:---|
| Anvendt løsning | _Windows_: Miljøvariablen LOG4J_FORMAT_MSG_NO_LOOKUPS blev observeret, før den seneste enheds genstart. <br/><br/> _Linux + macOS_: Alle kørende processer har LOG4J_FORMAT_MSG_NO_LOOKUPS=true i sine miljøvariabler. |
| Midlertidig løsning, der afventer genstart | Miljøvariablen LOG4J_FORMAT_MSG_NO_LOOKUPS er angivet, men der blev ikke registreret en efterfølgende genstart. |
| Ikke anvendt | _Windows_: Miljøvariablen LOG4J_FORMAT_MSG_NO_LOOKUPS blev ikke observeret. <br/><br/> _Linux + macOS_: Det er ikke alle kørende processer, der har LOG4J_FORMAT_MSG_NO_LOOKUPS=true i miljøvariabler, og afhjælpningshandlingen blev ikke anvendt på enheden. |
| Delvist afhjullet | _Linux + macOS_: Selvom afhjælpningshandlingen blev anvendt på enheden, er det ikke alle kørende processer, der har LOG4J_FORMAT_MSG_NO_LOOKUPS=true i dens miljøvariabler. |
|Ikke relevant | Enheder, der har sårbare filer, der ikke er inden for afhjælpningens versionsområde. |
|Unknown | Afhjælpningsstatussen kunne ikke bestemmes på nuværende tidspunkt. |

> [!NOTE]
> Det kan tage et par timer, før den opdaterede afhjælpningsstatus for en enhed afspejles.

### <a name="revert-mitigations-applied-for-the-log4shell-vulnerability"></a>Tilbagefør de afhjælpninger, der er anvendt for Log4Shell-sårbarheden

Hvis afhjælpningen skal gendannes, skal du følge disse trin:

**_Til Windows:_**

1. Åbn et PowerShell-vindue med administratorrettigheder
2. Kør følgende kommando:

 ```Powershell
   [Environment]::SetEnvironmentVariable("LOG4J\_FORMAT\_MSG\_NO\_LOOKUPS", $null,[EnvironmentVariableTarget]::Machine)
```

Ændringen træder i kraft, når enheden er genstartet.

**_Til Linux:_**

1. Åbn filen /osv./miljøet, og slet linjen LOG4J\_FORMAT\_MSG\_NO\_LOOKUPS=true
2. Slet filen /etc/systemd/system.conf.d/log4j\_disable\_jndi\_lookups.conf
3. Slet filen /etc/systemd/user.conf.d/log4j\_disable\_jndi\_lookups.conf

Ændringen træder i kraft, når enheden er genstartet.

**_Til macOS:_**

Fjern filsættet. LOG4J\_FORMAT\_MSG\_NO\_LOOKUPS.plist fra følgende mapper:

- */Library/LaunchDaemons/*
- */Library/LaunchAgents/*
- */Users/\[username\]/Library/LaunchAgents/ - for alle brugere*

Ændringen træder i kraft, når enheden er genstartet.

### <a name="apache-log4j-security-recommendations"></a>Apache Log4j-sikkerhedsanbefalinger

Hvis du vil se en aktiv sikkerhedsanbefaling, der er relateret til Apache log4j, skal du vælge fanen **Sikkerhedsanbefalinger** på siden med oplysninger om sårbarheder. Hvis du vælger **Opdater Apache Log4j** i dette eksempel, får du vist et andet pop op-vindue med flere oplysninger:

:::image type="content" source="images/update_apache_log4j.png" alt-text="Opdater sikkerhedsanbefaling for apache log4j" lightbox="images/update_apache_log4j.png":::

Vælg **Anmod om afhjælpning** for at oprette en afhjælpningsanmodning.

## <a name="explore-the-vulnerability-in-the-microsoft-365-defender-portal"></a>Udforsk sårbarheden på Microsoft 365 Defender-portalen

Når blottede enheder, filer og software er fundet, formidles relevante oplysninger også via følgende oplevelser på portalen Microsoft 365 Defender:

### <a name="security-recommendations"></a>Sikkerhedsanbefalinger

Søg efter **CVE-2021-44228** for at se sikkerhedsanbefalinger, der løser Log4Shell-sårbarheden:

:::image type="content" source="images/security_recommendations_log4j.png" alt-text="Sikkerhedsrisikoen log4j på siden med sikkerhedsanbefalinger" lightbox="images/security_recommendations_log4j.png":::

### <a name="software-inventory"></a>Softwarelager

 På softwareoversigtssiden skal du søge efter **CVE-2021-44228** for at se detaljer om Log4j-softwareinstallationerne og eksponeringen:

:::image type="content" source="images/software_inventory_log4j.png" alt-text="Log4j-sårbarheden på softwareoversigtssiden" lightbox="images/software_inventory_log4j.png":::

### <a name="weaknesses"></a>Svagheder

På siden svagheder skal du søge efter **CVE-2021-44228** for at se oplysninger om Log4Shell-sårbarheden:

:::image type="content" source="images/weaknesses_log4j.png" alt-text="Log4j-sårbarheden på siden svagheder" lightbox="images/weaknesses_log4j.png":::

## <a name="use-advanced-hunting"></a>Brug avanceret jagt

Du kan bruge følgende avancerede jagtforespørgsel til at identificere sikkerhedsrisici i installeret software på enheder:

 ```text
    DeviceTvmSoftwareVulnerabilities
    | where CveId in ("CVE-2021-44228", "CVE-2021-45046")
 ```

Du kan bruge følgende avancerede jagtforespørgsel til at identificere sikkerhedsrisici i installeret software på enheder for at vise resultater på filniveau fra disken:

 ```text
    DeviceTvmSoftwareEvidenceBeta
    | mv-expand DiskPaths
    | where DiskPaths contains "log4j"
    | project DeviceId, SoftwareName, SoftwareVendor, SoftwareVersion, DiskPaths
 ```

## <a name="related-articles"></a>Relaterede artikler

- [Oversigt over administration af trusler og sårbarheder](http://next-gen-threat-and-vuln-mgt.md)
- [Sikkerhedsanbefalinger](tvm-security-recommendation.md)
