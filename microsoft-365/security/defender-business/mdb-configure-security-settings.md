---
title: Få vist og rediger dine sikkerhedsindstillinger i Microsoft Defender for Business
description: Konfigurer dine sikkerhedspolitikker i Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 54592b20b5b6471d26c4673492566451ae5ec0de
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63594114"
---
# <a name="view-and-edit-your-security-policies-and-settings-in-microsoft-defender-for-business"></a>Få vist og rediger dine sikkerhedspolitikker og -indstillinger i Microsoft Defender for Business

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

## <a name="overview"></a>Oversigt

Når du har onboardet din virksomheds enheder til Microsoft Defender for Business, er næste trin at få vist og om nødvendigt redigere dine sikkerhedspolitikker og -indstillinger. Sikkerhedspolitikker omfatter:

- **[Næste generations beskyttelsespolitikker](#view-or-edit-your-next-generation-protection-policies)**, som bestemmer beskyttelse mod antivirus og antimalware for din virksomheds enheder

- **[Firewallbeskyttelse og regler](#view-or-edit-your-firewall-policies-and-custom-rules)**, som bestemmer, hvilken netværkstrafik der må flyde til eller fra virksomhedens enheder

- **[Filtrering af webindhold](#set-up-web-content-filtering)**, som forhindrer folk i at besøge bestemte websteder (URL-adresser), der er baseret på kategorier, f.eks. indhold beregnet for voksne eller juridisk ansvar.

I Defender for Business anvendes sikkerhedspolitikker på enheder via [enhedsgrupper](mdb-create-edit-device-groups.md#what-is-a-device-group). 

Ud over dine sikkerhedspolitikker kan du få vist og redigere [indstillinger,](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal) f.eks. hvilken tidszone der skal bruges i Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og om du vil modtage visningsfunktioner, efterhånden som de bliver tilgængelige.

Brug denne artikel som en vejledning i administration af sikkerhedspolitikker og -indstillinger.

## <a name="what-to-do"></a>Hvad kan du gøre?

1. [Vælg, hvor du vil administrere sikkerhedspolitikker og -enheder](#choose-where-to-manage-security-policies-and-devices).

2. [Få vist eller rediger dine næste generations beskyttelsespolitikker](#view-or-edit-your-next-generation-protection-policies).

3. [Få vist eller rediger politikker for din firewall og brugerdefinerede regler](#view-or-edit-your-firewall-policies-and-custom-rules).

4. [Konfigurere filtrering af webindhold](#set-up-web-content-filtering).

5. [Få vist og redigere andre indstillinger i Microsoft 365 Defender-portalen](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal). 

6. [Fortsæt til de næste trin](#next-steps).

>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>

## <a name="choose-where-to-manage-security-policies-and-devices"></a>Vælg, hvor du vil administrere sikkerhedspolitikker og -enheder

Defender for Business har en [forenklet konfigurationsproces,](mdb-simplified-configuration.md) der hjælper med at strømline konfigurationen og konfigurationsprocessen. Hvis du vælger den forenklede konfigurationsproces, kan du få vist og administrere dine sikkerhedspolitikker på Microsoft 365 Defender-portalen ([https://security.microsoft.com/](https://security.microsoft.com/)). Du er dog ikke begrænset til denne indstilling. Hvis du har brugt en Microsoft Endpoint Manager (hvilket omfatter Microsoft Intune), kan du fortsætte med at bruge Endpoint Manager.

Følgende tabel kan hjælpe dig med at vælge, hvor du kan administrere dine sikkerhedspolitikker og enheder. <br/><br/>

| Indstilling | Beskrivelse |
|:---|:---|
| **Brug Microsoft 365 Defender portalen** (*anbefales*) | Portalen Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)) kan være dit sted, hvor du kan administrere firmaets enheder, sikkerhedspolitikker og sikkerhedsindstillinger. Du kan få adgang til dine sikkerhedspolitikker og -indstillinger, bruge dashboardet [til & til](mdb-view-tvm-dashboard.md) administration af sikkerhedsrisiko og få vist [og administrere hændelser](mdb-view-manage-incidents.md) på ét sted. <br/><br/>Hvis du bruger en Microsoft Endpoint Manager, kan enheder, som du onboarder til Defender for Business og dine sikkerhedspolitikker, ses Endpoint Manager. Du kan få mere at vide i følgende artikler:<br/><br/>- [Standardindstillinger og -indstillinger for Defender for Business Microsoft Endpoint Manager](mdb-next-gen-configuration-settings.md#defender-for-business-default-settings-and-microsoft-endpoint-manager)<br/><br/>- [Firewall i Microsoft Defender for Business](mdb-firewall.md)   |
| **Brug Microsoft Endpoint Manager** | Hvis din virksomhed allerede bruger Endpoint Manager (som omfatter Microsoft Intune) til at administrere sikkerhedspolitikker, kan du fortsætte med at bruge Endpoint Manager til at administrere enheder og sikkerhedspolitikker. Du kan få mere at vide [under Administrer enhedssikkerhed med slutpunktssikkerhedspolitikker i Microsoft Intune](/mem/intune/protect/endpoint-security-policy). <br/><br/>Hvis du beslutter dig for at skifte til den forenklede konfigurationsproces i [Defender for Business](mdb-simplified-configuration.md), bliver du bedt om at slette eventuelle eksisterende sikkerhedspolitikker i Endpoint Manager for at undgå [politikkonflikter](mdb-troubleshooting.yml) senere. |

> [!IMPORTANT]
> Hvis du administrerer sikkerhedspolitikker i Microsoft 365 Defender-portalen, kan du se disse  politikker i Endpoint Manager, der er angivet som Antivirus- eller Firewall-politikker. Når du får vist politikkerne for din firewall i Endpoint Manager, får du vist to politikker: én politik til beskyttelse af din firewall og en anden for brugerdefinerede regler.

## <a name="view-or-edit-your-next-generation-protection-policies"></a>Få vist eller rediger dine næste generations beskyttelsespolitikker

Afhængigt af om du bruger Microsoft 365 Defender-portalen eller Microsoft Endpoint Manager til at administrere dine næste generations beskyttelsespolitikker, skal du bruge en af procedurerne i følgende tabel: <br/><br/>

| Portal | Procedure |
|:---|:---|
| Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Gå til Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), og log på. <br/><br/>2. Vælg Enhedskonfiguration i **navigationsruden**. Politikker er organiseret efter operativsystem og politiktype.<br/><br/>3. Vælg en fane i operativsystemet (f.eks **. Windows klienter**).<br/><br/>4. **Udvid næste generations beskyttelse for** at få vist din liste over politikker.<br/><br/>5. Vælg en politik for at få vist flere oplysninger om politikken. Hvis du vil foretage ændringer eller få mere at vide om politikindstillinger, skal du se følgende artikler: <br/>- [Få vist eller rediger enhedspolitikker](mdb-view-edit-policies.md)<br/>- [Forstå næste generations konfigurationsindstillinger](mdb-next-gen-configuration-settings.md)  |
| Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Gå til [https://endpoint.microsoft.com](https://endpoint.microsoft.com) , og log på. Du er nu i Microsoft Endpoint Manager Administration.<br/><br/>2. Vælg **Slutpunktssikkerhed**.<br/><br/>3. Vælg **Antivirus for** at få vist dine politikker i den pågældende kategori. <br/><br/>Hvis du vil have hjælp til at administrere dine sikkerhedsindstillinger Microsoft Endpoint Manager, skal [du starte med Administrer slutpunktssikkerhed Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="view-or-edit-your-firewall-policies-and-custom-rules"></a>Få vist eller rediger politikker for din firewall og brugerdefinerede regler

Afhængigt af om du bruger Microsoft 365 Defender-portalen eller Microsoft Endpoint Manager til at administrere din firewallbeskyttelse, skal du bruge en af procedurerne i følgende tabel: <br/><br/>

| Portal | Procedure |
|:---|:---|
| Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Gå til Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), og log på. <br/><br/>2. Vælg Enhedskonfiguration i **navigationsruden**. Politikker er organiseret efter operativsystem og politiktype.<br/><br/>3. Vælg en fane i operativsystemet (f.eks **. Windows klienter**).<br/><br/>4. Udvid **Firewall for** at få vist din liste over politikker.<br/><br/>5. Vælg en politik for at få vist flere oplysninger om politikken. Hvis du vil foretage ændringer eller få mere at vide om politikindstillinger, skal du se følgende artikler: <br/>- [Få vist eller rediger enhedspolitikker](mdb-view-edit-policies.md)<br/>- [Firewall-indstillinger](mdb-firewall.md)<br/>- [Administrer dine brugerdefinerede regler for firewallpolitikker](mdb-custom-rules-firewall.md)  |
| Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Gå til [https://endpoint.microsoft.com](https://endpoint.microsoft.com) , og log på. Du er nu i Microsoft Endpoint Manager Administration.<br/><br/>2. Vælg **Slutpunktssikkerhed**.<br/><br/>3. Vælg **Firewall for** at få vist dine politikker i den pågældende kategori. Brugerdefinerede regler, der er defineret for firewallbeskyttelse, er angivet som separate politikker.<br/><br/>Hvis du vil have hjælp til at administrere dine sikkerhedsindstillinger Microsoft Endpoint Manager, skal [du starte med Administrer slutpunktssikkerhed Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="set-up-web-content-filtering"></a>Konfigurere filtrering af webindhold

Filtrering af webindhold gør det muligt for dit sikkerhedsteam at spore og regulere adgangen til websteder baseret på deres indholdskategorier, f.eks.:

- Indhold beregnet for voksne: Websteder, der er relateret til, hvilket indhold, hvilket er muligt, nøgenhed, pornografi, seksuelt eksplicit materiale eller vold

- Høj båndbredde: Download websteder, billeddelingswebsteder eller peer-to-peer-værter

- Juridisk ansvar: Websteder, der omfatter billeder af misbrug af børn, fremmer ulovlige aktiviteter, fremmer plaismer eller skoles snyd, eller som fremmer skadelige aktiviteter

- Afslappende: Websteder, der tilbyder webbaserede chatrum, onlinespil, webbaserede mails eller sociale netværk

- Ikke kategoriseret: Websteder, der ikke har noget indhold, eller som er registreret for nylig

Ikke alle websteder i disse kategorier er skadelige, men de kan være problematiske for din virksomhed på grund af overholdelse af regler, båndbreddeforbrug eller andre problemer. Desuden kan du oprette en politik, der kun er til overvågning, for at få en bedre forståelse af, om dit sikkerhedsteam skal blokere eventuelle webstedskategorier.

Filtrering af webindhold er tilgængelig i de større webbrowsere med blokke, der udføres af Windows Defender SmartScreen (Microsoft Edge) og Netværksbeskyttelse (Chrome, Firefox,Ering og Opera). Du kan finde flere oplysninger [under Forudsætninger for filtrering af webindhold](../defender-endpoint/web-content-filtering.md#prerequisites).

### <a name="to-set-up-web-content-filtering"></a>Sådan konfigurerer du filtrering af webindhold

1. I portalen Microsoft 365 Defender skal du [https://security.microsoft.com](https://security.microsoft.com) **vælge Indstillinger** >  **Filtrering af indhold +** >  **Tilføj politik**.

2. Angiv et navn og en beskrivelse til din politik.

3. Vælg kategorier, der skal blokeres. Brug udvidelsesikonet til at udvide hver overordnet kategori fuldt ud og vælge bestemte kategorier for webindhold.

   Hvis du vil konfigurere en politik kun for overvågning, der ikke blokerer for websteder, skal du ikke vælge nogen kategorier.

   Markér ikke **Ikke kategoriseret**.

4. Angiv politikkens omfang ved at vælge enhedsgrupper for at anvende politikken. Kun enheder i de valgte enhedsgrupper vil være forhindret i at få adgang til websteder i de valgte kategorier.

5. Gennemse oversigten, og gem politikken. Det kan tage op til to timer, før politikopdateringen anvendes på dine valgte enheder.

> [!TIP]
> Hvis du vil have mere at vide om filtrering af webindhold, skal [du se Filtrering af webindhold](../defender-endpoint/web-content-filtering.md).

## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>Få vist og redigere andre indstillinger i Microsoft 365 Defender-portalen

Ud over sikkerhedspolitikker, der anvendes på enheder, er der andre indstillinger, du kan få vist og redigere i Defender for Business. Du kan f.eks. angive den tidszone, du vil bruge, og du kan onboarde (eller offboard)-enheder. 

> [!NOTE]
> Der vises muligvis flere indstillinger i din lejer, end der er angivet i denne artikel. I denne artikel fremhæves de vigtigste indstillinger, du skal gennemse i Defender for Business.

### <a name="settings-to-review-for-defender-for-business"></a>Indstillinger at gennemgå for Defender for Business

I følgende tabel beskrives de indstillinger, der skal vises (og om nødvendigt redigeres) i Defender for Business.

<br/><br/>

| Kategori | Indstilling | Beskrivelse |
|:---|:---|:---|
| **Sikkerhedscenter** | **Tidszone** | Vælg den tidszone, der skal bruges til de datoer og klokkeslæt, der vises i hændelser, registrerede trusler og automatiseret undersøgelse, & afhjælpning. Du kan enten bruge UTC eller din lokale tidszone (*anbefales*).  |
| **Microsoft 365 Defender** | **Konto** | Få vist detaljer, f.eks. hvor dine data er gemt, dit lejer-id og dit organisations-id. |
| **Microsoft 365 Defender**  | **Visningsfunktioner**  | Slå visningsfunktioner til for at prøve kommende funktioner og nye funktioner. Du kan være blandt de første til at gennemse nye funktioner og give feedback. |
| **Slutpunkter**  | **Mailbeskeder** | Konfigurer eller rediger dine regler for mailbeskeder. Når der registreres sårbarheder, eller der oprettes en besked, modtager de modtagere, der er angivet i dine regler for mailbeskeder, en mail. [Få mere at vide om mailbeskeder](mdb-email-notifications.md). |
| **Slutpunkter**   | **Enhedshåndtering** >  **Onboarding** | Onboard enheder til Defender for Business ved hjælp af et script, der kan downloades. Du kan få mere at vide [under Onboard-enheder til Microsoft Defender for Business](mdb-onboard-devices.md).   |  
| **Slutpunkter**  |  **Enhedshåndtering** >  **Offboarding** | Offboard-enheder (fjern) fra Defender for Business. Når du offboarder en enhed, sendes data ikke længere til Defender for Business, men data, der modtages før offboarding bevares. Du kan få mere at vide under [Offboarding af en enhed](mdb-onboard-devices.md#offboarding-a-device).  |

### <a name="access-your-settings-in-the-microsoft-365-defender-portal"></a>Få adgang til dine indstillinger Microsoft 365 Defender-portalen

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com/](https://security.microsoft.com/)), og log på.

2. Vælg **Indstillinger**, og vælg derefter en kategori (**f.eks** **sikkerhedscenter, Microsoft 365 Defender** **eller slutpunkter**).

3. Vælg et element, der skal vises eller redigeres, på listen over indstillinger.


## <a name="next-steps"></a>Næste trin

Fortsæt til en eller flere af følgende opgaver:

- [Kom i gang med at bruge Microsoft Defender for Business](mdb-get-started.md)

- [Administrer enheder i Microsoft Defender for Business](mdb-manage-devices.md)

- [Få vist og administrer hændelser i Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [Få vist eller rediger politikker i Microsoft Defender for Business](mdb-view-edit-policies.md)
