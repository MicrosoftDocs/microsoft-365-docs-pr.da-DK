---
title: Rediger navneservere for at konfigurere Microsoft 365 med en domæneregistrator
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEU150
- GEA150
ms.assetid: a8b487a9-2a45-4581-9dc4-5d28a47010a2
description: Få mere at vide om, hvordan du tilføjer og konfigurerer dit domæne Microsoft 365 så dine tjenester som mail og Skype for Business Online bruger dit eget domænenavn.
ms.openlocfilehash: 2d591429d74e03eec883b524b8fa36d082cfab93
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589342"
---
# <a name="change-nameservers-to-set-up-microsoft-365-with-any-domain-registrar"></a>Rediger navneservere for at konfigurere Microsoft 365 med en domæneregistrator

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter.

Følg disse instruktioner for at tilføje og konfigurere dit domæne Microsoft 365 så dine tjenester som mail og Teams bruger dit eget domænenavn. For at gøre dette skal du bekræfte dit domæne og derefter ændre domænets navneservere til Microsoft 365 så de korrekte DNS-poster kan konfigureres for dig. Følg disse trin, hvis følgende udsagn beskriver din situation:

- Du har dit eget domæne og vil konfigurere det til at fungere sammen med Microsoft 365.

- Du vil Microsoft 365 administrere dine DNS-poster for dig. (Hvis du foretrækker det, kan [du administrere dine egne DNS-poster](../setup/add-domain.md)).

## <a name="add-a-txt-or-mx-record-for-verification"></a>Tilføje en TXT- eller MX-post til godkendelse

> [!NOTE]
> Du skal kun oprette den ene eller den anden af disse poster. TXT er den foretrukne posttype, men nogle DNS-hostingudbydere understøtter den ikke. Hvis det er tilfældet, kan du i stedet oprette en MX-post.

Før du kan bruge dit domæne Microsoft 365, skal vi være sikre på, at du ejer det. Hvis du kan logge på din konto hos din domæneregistrator og oprette DNS-posten, har Microsoft 365 at du ejer domænet.

> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. påvirker det ikke andet. Du kan slette det senere, hvis du vil.

### <a name="find-the-area-on-your-dns-hosting-providers-website-where-you-can-create-a-new-record"></a>Find det område på DNS-udbyderens websted, hvor du kan oprette en ny post

1. Log på DNS-udbyderens websted.

2. Vælg dit domæne.

3. Find den side, hvor du kan redigere DNS-posterne for dit domæne.

### <a name="create-the-record"></a>Opret posten

Afhængigt af om du opretter en TXT-post eller en MX-post, skal du gøre et af følgende:

**Hvis du opretter en TXT-post, skal du bruge disse værdier:**

<br>

****

|Posttype|Alias eller værtsnavn|Værdi|TTL|
|---|---|---|---|
|TXT|Gør et af følgende: Skriv **@** eller lad feltet være tomt, eller skriv dit domænenavn.  <p> **Bemærk**! Forskellige DNS-værter har forskellige krav til dette felt.|MS=ms *XXXXXXXX* <p> **Bemærk!** Dette er et eksempel. Brug din specifikke **værdi fra Destination eller** adressehensepunkter her fra tabellen i Microsoft 365. [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md)|Angiv denne værdi til **1 time** eller det tilsvarende i minutter ( **60** ), sekunder ( **3600** ) osv.|
|||||

**Hvis du opretter en MX-post, skal du bruge disse værdier:**

<br>

****

|Posttype|Alias eller værtsnavn|Værdi|Prioritet|TTL|
|---|---|---|---|---|
|MX|Skriv enten **@** dit domænenavn eller dit domænenavn. |MS=ms *XXXXXXXX* **Bemærk!** Dette er et eksempel. Brug din specifikke **værdi fra Destination eller** adressehensepunkter her fra tabellen i Microsoft 365. [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md)|For **Priority skal** du for at undgå konflikter med MX-posten, der bruges til mailflow, have en lavere prioritet end prioriteten for eventuelle eksisterende MX-poster. Du kan finde flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml)|Angiv denne værdi til **1 time** eller det tilsvarende i minutter ( **60** ), sekunder ( **3600** ) osv.|
||||||

### <a name="save-the-record"></a>Gem posten

Nu hvor du har tilføjet posten på domæneregistratorens websted, skal du gå tilbage til Microsoft 365 og anmode Microsoft 365 at finde posten.

Når Microsoft 365 finder den rigtige TXT-post, er dit domæne godkendt.

1. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domæner</a>.

2. På siden **Domæner skal** du vælge det domæne, du er ved at bekræfte.

3. På siden **Konfiguration** skal du vælge **Start installationen**.

4. På siden **Bekræft domæne** skal du vælge **Bekræft**.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="change-your-domains-nameserver-ns-records"></a>Ændre dit domænes navneserverposter (NS)-poster

Når du kommer til det sidste trin i konfigurationsguiden for domæner i Microsoft 365, har du én opgave tilbage. Hvis du vil konfigurere dit domæne med Microsoft 365-tjenester som f.eks. mail, skal du ændre domænets navneserverposter (eller NS-poster) hos din domæneregistrator, så de peger på Microsoft 365 primære og sekundære navneservere. Da din Microsoft 365 vært for din DNS, konfigureres de nødvendige DNS-poster for dine tjenester automatisk for dig. Du kan selv opdatere navneserverposterne ved at følge trinnene, som din domæneregistrator muligvis har afgivet i Hjælp-indholdet på deres websted. Hvis du ikke kender DNS, skal du kontakte support hos domæneregistratoren.

::: moniker range="o365-worldwide"

Hvis du selv vil ændre domænets navneservere på domæneregistratorens websted, skal du følge disse trin:

1. Find det område på domæneregistratorens websted, hvor du kan ændre navneserverne for dit domæne eller et område, hvor du kan bruge brugerdefinerede navneservere.

2. Opret navneserverposter, eller rediger de eksisterende navneserverposter, så de matcher følgende værdier:

    - Første navneserver: ns1.bdm.microsoftonline.com
    - Anden navneserver: ns2.bdm.microsoftonline.com
    - Tredje navneserver: ns3.bdm.microsoftonline.com
    - Fjerde navneserver: ns4.bdm.microsoftonline.com

   > [!TIP]
   > Det er bedst at tilføje alle fire poster, men hvis din registrator kun understøtter to, skal du **tilføje ns1.bdm.microsoftonline.com** og **ns2.bdm.microsoftonline.com**.

3. Gem ændringerne.

> [!CAUTION]
> Når du ændrer domænets NS-poster, så de peger på Microsoft 365 navneservere, påvirkes alle de tjenester, der aktuelt er knyttet til dit domæne. Hvis du har sprunget nogle trin i guiden over, f.eks. tilføjelse af mailadresser, eller hvis du bruger dit domæne til blogs, indkøbskurve eller andre tjenester, er der yderligere trin, der er påkrævet. Ellers kan denne ændring medføre nedetid for tjenesten, f.eks. manglende adgang til mail eller at dit nuværende websted ikke er utilgængeligt.

::: moniker-end

::: moniker range="o365-21vianet"

1. Find det område på domæneregistratorens websted, hvor du kan redigere navneserverne for dit domæne.

2. Opret to navneserverposter, eller rediger de eksisterende navneserverposter, så de matcher følgende værdier:

   - Første navneserver: ns1.dns.partner.microsoftonline.cn
   - Anden navneserver: ns2.dns.partner.microsoftonline.cn

   > [!TIP]
   > Du skal bruge mindst to navneserverposter. Hvis der er angivet andre navneservere, kan du enten slette dem eller ændre dem til **ns3.dns.partner.microsoftonline.cn** og **ns4.dns.partner.microsoftonline.cn**.

3. Gem ændringerne.

> [!CAUTION]
> Når du ændrer domænets NS-poster, så de peger på den Office 365, der drives af 21Vianet-navneservere, påvirkes alle de tjenester, der aktuelt er knyttet til dit domæne. Hvis du har sprunget nogle trin i guiden over, f.eks. tilføjelse af mailadresser, eller hvis du bruger dit domæne til blogs, indkøbskurve eller andre tjenester, er der yderligere trin, der er påkrævet. Ellers kan denne ændring medføre nedetid for tjenesten, f.eks. manglende adgang til mail eller at dit nuværende websted ikke er utilgængeligt.

::: moniker-end

Her er f.eks. nogle ekstra trin, der kan være nødvendige for mail- og webstedshosting:

- Flyt alle de mailadresser, der bruger dit domæne, Microsoft 365 før du ændrer dine NS-poster.

- Vil du tilføje et domæne, der bruges i øjeblikket med en webadresse som f.eks `https://www.fourthcoffee.com`. ? Du kan følge nedenstående trin, mens du tilføjer domænet for at lade webstedet være hostet, hvor det hostes nu, så folk stadig kan komme til webstedet, efter at du har ændret domænets NS-poster til at pege på Microsoft 365.

1. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domæner</a>.

2. Vælg **et domæne** på siden Domæner.

3. På siden med domæneoplysninger skal du vælge **fanen DNS-poster** .

4. Vælg **Tilføj post**.

5. I **ruden Tilføj en brugerdefineret DNS-post** skal du på rullelisten **Type** vælge **A (Adresse)**.

6. I feltet **Værtsnavn eller alias** skal du skrive **@**.

7. I feltet **IP-adresse** skal du skrive den statiske IP-adresse til det websted, hvor det i øjeblikket hostes. Eksempel: 172.16.140.1.

   > [!IMPORTANT]
   > Dette skal være en _statisk_ IP-adresse til webstedet, ikke en _dynamisk_ IP-adresse. For at sikre, at du kan få en statisk IP-adresse til dit offentlige websted, skal du tale med det websted, der hoster dit websted.

8. Hvis du vil ændre TTL-indstillingen for posten, skal du vælge et nyt tidsrum på **rullelisten TTL** . Ellers skal du fortsætte til trin 9.

9. Vælg **Gem**.

Desuden kan du oprette en CNAME-post for at hjælpe kunderne med at finde dit websted.

1. Vælg **Tilføj post**.
2. I **ruden Tilføj en brugerdefineret DNS-post** skal du på rullelisten **Type** vælge **CNAME (Alias)**.
3. Skriv www **i feltet Værtsnavn** eller **alias**.
4. Skriv **det fulde domænenavn** for webstedet i feltet Peger på adresse. Eksempel: **contoso.5om**.
5. Hvis du vil ændre TTL-indstillingen for posten, skal du vælge et nyt tidsrum på **rullelisten TTL** . Ellers skal du fortsætte til trin 6.
6. Vælg **Gem**.

Når navneserverposterne er opdateret til at pege på Microsoft, er konfigurationen af domænet fuldført. Mail dirigeres til Microsoft, og trafik til din webadresse fortsætter med at gå til din aktuelle webstedsvært.'

> [!NOTE]
> Det kan tage adskillige timer, før opdateringerne af navneserverposten registreres i internettets DNS-system. Derefter vil din Microsoft-mail og andre tjenester være klar til at fungere med dit domæne.

## <a name="related-content"></a>Relateret indhold

[Tilføj DNS-poster for at forbinde dit domæne](create-dns-records-at-any-dns-hosting-provider.md) (artikel)\
[Find og løs problemer efter at have tilføjet dit domæne eller DNS-poster](find-and-fix-issues.md) (artikel)\
[Administrer domæner](/admin) (linkside)
