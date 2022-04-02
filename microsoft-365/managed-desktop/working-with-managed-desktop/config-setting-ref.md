---
title: Konfigurerbar indstillingsreference for Microsoft Managed Desktop
description: Angive kategorier for konfigurerbare indstillinger i Microsoft Managed Desktop
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 18fc51f37e66cd3212ea1e5af22ed4389d025a05
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755087"
---
# <a name="configurable-settings-reference---microsoft-managed-desktop"></a>Reference til konfigurerbare indstillinger – Microsoft Managed Desktop

I denne artikel vises de indstillingskategorier, som kunder kan konfigurere med Microsoft Managed Desktop. Hver indstillingskategori indeholder oplysninger om krav, bedste fremgangsmåder, og hvordan du tilpasser indstillingskategorien.

> [!NOTE]
> Denne side indeholder oplysninger om ofte anmodede indstillinger. Det gælder for den ældre Edge-browser.

## <a name="desktop-background-picture"></a>Skrivebordsbaggrundsbillede

Du kan tilpasse skrivebordsbaggrundsbilledet til Microsoft Managed Desktop-enheder i organisationen. Du kan bruge skrivebordsbaggrundsbilledet til at anvende virksomhedens brand eller marketingmateriale.

### <a name="requirements"></a>Krav

Disse krav skal være opfyldt for et baggrundsbillede på skrivebordet:

- Billedfilformat: .jpg, jpeg eller .png
- Filplacering: Vært på en sikker http-placering, der er tillid til.
- Ikke tilladt: Http- og filshareplaceringer (unc) understøttes ikke.

### <a name="customize-and-deploy-desktop-background-picture"></a>Tilpas og installer baggrundsbillede på skrivebordet

**Sådan tilføjer du et brugerdefineret baggrundsbillede på skrivebordet:**

1. Log på [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) og gå til **menuen** Enheder.
2. I sektionen Microsoft Managed Desktop skal du vælge **Indstillinger**.
3. I **arbejdsområdet Indstillinger** skal du vælge **Skrivebordsbaggrundsbillede**.
4. Angiv placeringen af det billede, du vil bruge.
5. Vælg **Faseinstallation** for at gemme ændringerne og installere dem i gruppen Test.

## <a name="browser-start-pages"></a>Startsider i browseren

Startsiderne i browseren åbnes under individuelle faner, når brugerne starter Microsoft Edge. Hvis du vil gøre det nemt for brugerne at åbne et sæt websteder, de ofte bruger, skal du tilføje en startside i browseren for hvert websted.

### <a name="requirements"></a>Krav

Du skal angive det fulde domænenavn til intranet- eller internetwebsteder til din browsers startsider. Hvis interne websteder er konfigureret, skal du informere brugerne om, at adgang kun er tilladt, når de har forbindelse til det interne netværk, eller når de har forbindelse via VPN.

### <a name="customize-and-deploy-browser-start-pages"></a>Tilpasse og installere startsider i browseren

**Sådan tilføjer du en startside i browseren:**

1. Log på [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) og gå til **menuen** Enheder.
2. I sektionen Microsoft Managed Desktop skal du vælge **Indstillinger**.
3. I **arbejdsområdet Indstillinger** du vælge **Browserstartsider**.
4. Vælg **Tilføj startside**.
5. I **Tilføj startside for browser** skal du angive URL-adressen til det websted, du vil bruge, og derefter **vælge Tilføj startside**.
6. Gentag trin 1-5 for at tilføje flere startsider i browseren.
7. Vælg **Faseinstallation** for at gemme ændringerne og installere dem i gruppen Test.

## <a name="enterprise-mode-site-list-location"></a>Webstedslisteplacering i virksomhedstilstand

Hvis du har bestemte websteder og apps, der har kompatibilitetsproblemer med Microsoft Edge, kan du bruge listen over virksomhedswebsteder til automatisk at åbne webstederne i Internet Explorer 11. Hvis du ved, at intranetwebstederne ikke fungerer korrekt sammen med Microsoft Edge, kan du indstille alle intranetwebsteder til at åbne automatisk i Internet Explorer 11.

Hvis du bruger Virksomhedstilstand, kan du fortsætte med at bruge Microsoft Edge som din standardbrowser og samtidig sikre, at dine apps fortsat fungerer i Internet Explorer 11. Du kan finde flere oplysninger om lister over virksomhedswebsteder [i virksomhedstilstand og Webstedslister i virksomhedstilstand](/internet-explorer/ie11-deploy-guide/what-is-enterprise-mode).

Du kan angive en placering `https://` eller placeringen for en intern deling, hvor du har hostet din liste over virksomhedswebsteder.

### <a name="requirements"></a>Krav

Disse krav skal være opfyldt for webstedslistefilen i virksomhedstilstand:

- Filformat: XML-fil, der [opfylder filkravene](/internet-explorer/ie11-deploy-guide/what-is-enterprise-mode#site-list-xml-file).
- Filplacering: Værtsfil på en intern https-placering.
- Ikke tilladt: Hosting på et internt filshare, f.eks `//sharename`. , er ikke tilladt.

### <a name="best-practices"></a>Anbefalede fremgangsmåder

Disse bedste fremgangsmåder tilbydes for at hjælpe kunderne med at træffe beslutninger om at modernisere deres it-infrastruktur:

| Øvelse | Beskrivelse |
| ------ | ------ |
| Vælg et begrænset antal websteder | Microsoft Managed Desktop bruger Microsoft Edge som den foretrukne browser til at forbedre den overordnede sikkerhed for organisationen og brugervenligheden for dine brugere. De fleste websteder på denne liste er til ældre webapps, der har brug for en ældre version af en browser. Den indeholder ikke så mange sikkerhedsfunktioner. |
| Overvej en alternativ mulighed | Overvej et andet websted eller en webapp, der ikke kræver en ældre browser. Eller du kan overveje at opdatere webstedet, så det kan bruge nyere browsere. Nyere browsere bruger den nyeste teknologi og er med til at forbedre sikkerheden. |

### <a name="customize-and-deploy-enterprise-site-mode-list-location"></a>Tilpasse og implementere listeplacering i Enterprise-webstedstilstand

**Sådan tilføjer du en listeplacering i virksomhedswebstedstilstand:**

1. Log på [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) og gå til **menuen** Enheder.
2. I sektionen Microsoft Managed Desktop skal du vælge **Indstillinger**.
3. I **arbejdsområdet Indstillinger** skal du vælge **Webstedslisteplacering for virksomhedstilstand**.
4. Angiv https-placeringen for din webstedsliste.
5. Vælg **Faseinstallation** for at gemme ændringerne og installere dem i gruppen Test.

## <a name="trusted-sites"></a>Websteder, der er tillid til

Websteder, du har tillid til, giver dig mulighed for at tilpasse sikkerhedszoner, eller hvor et websted kan bruges til forskellige websteder. Sikkerhedszoner omfatter:

- Zone 1: Lokal intranetzone
- Zone 2: Webstedszone, der er tillid til
- Zone 3: Internetzone
- Zone 4: Zone med begrænsede websteder

### <a name="requirements"></a>Krav

Angiv det fulde domænenavn til intranet- eller internetwebsteder for hvert websted, der er tillid til.

### <a name="customize-and-deploy-trusted-sites"></a>Tilpasse og installere websteder, der er tillid til

**Sådan tilføjer du et websted, der er tillid til:**

1. Log på [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) og gå til **menuen** Enheder.
2. I sektionen Microsoft Managed Desktop skal du vælge **Indstillinger**.
3. Vælg Websteder, **Indstillinger** tillid til i **arbejdsområdet**, og vælg derefter Tilføj websted, der **er tillid til**.
4. Angiv **URL-adressen på** Tilføj et websted, der er tillid til, vælg en sikkerhedszone, og vælg derefter **Tilføj et websted, der er tillid til**.
5. Gentag trin 1-4 for hvert websted, du har tillid til, du vil tilføje.
6. Vælg **Faseinstallation** for at gemme ændringerne og installere dem i gruppen Test.

**Sådan fjerner du et websted, der er tillid til:**

1. Log på [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) og gå til **menuen** Enheder.
2. I sektionen Microsoft Managed Desktop skal du vælge **Indstillinger**.
3. I **Indstillinger skal du** vælge Websteder, du **har tillid til**.
4. Vælg det websted, du vil slette, og vælg derefter **Slet**.
5. Gentag trin 1-4 for hvert websted, der er tillid til, som du vil slette.
6. Vælg **Faseinstallation** for at gemme ændringerne og installere dem i gruppen Test.

## <a name="proxy"></a>Proxy

Du kan administrere indstillinger for netværksproxy for organisationen. Tilføj din proxyserver og dit portnummer, og tilføj derefter dine proxywebsteds undtagelser.

Microsoft Managed Desktop indeholder et sæt standardundtagelser for proxyer, som er påkrævet for, at tjenesten kan fungere. Standardlisten for udeladelse kan kun ændres af Microsoft Managed Desktop-tjenesten. Du kan få mere at vide [under Netværkskonfiguration til Microsoft Managed Desktop](../get-ready/network.md).

De proxywebstedsundtagelser, der er tilføjet i Microsoft Managed Desktop-portalen, føjes til de standardproxyundtagelser, der følger med Microsoft Managed Desktop-tjenesten.

> [!NOTE]
> Opdatering af standardlisten over undtagelser for proxyen er altid prioriteret over kundeinstallationer. Det betyder, at din faseindderede installation afbrydes midlertidigt, hvis der er en installation til standardlisten over undtagelser for proxyen.  

### <a name="requirements"></a>Krav

Disse krav skal være opfyldt for undtagelser til proxyserver og proxywebsted:

- Skal være en gyldig serveradresse og et portnummer.
- URL-adresser skal være et gyldigt http-websted.
- Proxyundtagelser bør være begrænset til maksimalt 2064 tegn. Dette omfatter tilføjede Microsoft-administrerede skrivebordsadresser.

### <a name="customize-and-deploy-proxies"></a>Tilpasse og installere proxyer

**Sådan tilføjes en individuel undtagelse for proxywebstedet:**

1. Log på [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) og gå til **menuen** Enheder.
2. I sektionen Microsoft Managed Desktop skal du vælge **Indstillinger**.
3. Vælg **proxy Indstillinger** i **arbejdsområdet**.
4. Angiv Adresse **og** **Port-nummer** for din proxyserver, og vælg derefter **Tilføj proxyundtagelse**.
5. Angiv URL-adressen for et gyldigt http-websted, og vælg **derefter Tilføj proxyundtagelse**.
6. Gentag trin 1-5 for hvert websted, du har tillid til, du vil tilføje.
7. Vælg **Faseinstallation** for at gemme ændringerne og installere dem i gruppen Test.

## <a name="additional-resources"></a>Yderligere ressourcer

- [Oversigt over konfigurerbare indstillinger](config-setting-overview.md)
- [Installer konfigurerbare indstillinger](config-setting-deploy.md)
