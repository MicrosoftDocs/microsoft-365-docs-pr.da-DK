---
title: Trin 2. Give fjernadgang til apps og tjenester i det lokale miljø
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: Sørg for, at dine eksterne medarbejdere kan få adgang til lokale ressourcer, mens du optimerer adgangen Microsoft 365 skytjenester.
ms.openlocfilehash: 6baaa8c4e3935676278ff411d0282b82143056fc
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589443"
---
# <a name="step-2-provide-remote-access-to-on-premises-apps-and-services"></a>Trin 2. Give fjernadgang til apps og tjenester i det lokale miljø

Hvis din organisation bruger en VPN-løsning med fjernadgang, typisk med VPN-servere i kanten af dit netværk og VPN-klienter, der er installeret på dine brugeres enheder, kan dine brugere bruge VPN-forbindelser til at få adgang til apps og servere i det lokale miljø. Men det kan være nødvendigt at optimere trafik Microsoft 365 skybaserede tjenester.

Hvis brugerne ikke bruger en VPN-løsning, kan du bruge Azure Active Directory (Azure AD) Application Proxy og Azure Point-to-Site (P2S) VPN til at give adgang, afhængigt af om alle dine apps er webbaserede.

Her er de primære konfigurationer for fjernadgang:

- Du bruger allerede en VPN-løsning med fjernadgang.
- Du bruger ikke en VPN-løsning med fjernadgang, og du vil have dine fjernmedarbejdere til at bruge deres personlige computere.
- Du bruger ikke en VPN-løsning med fjernadgang, du har en hybrid identitet, og du skal kun have fjernadgang til lokale webbaserede apps.
- Du bruger ikke en VPN-løsning med fjernadgang, og du skal have adgang til lokale apps, hvoraf nogle ikke er webbaserede.

Se dette rutediagram for at se de konfigurationsindstillinger for fjernadgang, der er nævnt i denne artikel.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-flowchart.png" alt-text="Rutediagram for konfiguration af fjernadgang." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-flowchart.png":::

Med fjernadgangsforbindelser kan du også bruge [Fjernskrivebord](https://support.microsoft.com/help/4028379/windows-10-how-to-use-remote-desktop) til at forbinde dine brugere til en lokal pc. En fjernmedarbejder kan f.eks. bruge Fjernskrivebord til at oprette forbindelse til pc'en på sit kontor fra Windows-, iOS- eller Android-enhed. Når de har fjernforbindelse, kan de bruge den, som om de sad foran den.

## <a name="optimize-performance-for-remote-access-vpn-clients-to-microsoft-365-cloud-services"></a>Optimer ydeevnen for VPN-klienter med fjernadgang til Microsoft 365 skytjenester

Hvis dine eksterne medarbejdere bruger en traditionel VPN-klient til at få fjernadgang til dit organisationsnetværk, skal du bekræfte, at VPN-klienten har opdelt understøttelse af netværksforbindelse.

Uden opdelte netværksforbindelser bliver al din fjerntrafik sendt på tværs af VPN-forbindelsen, hvor den skal videresendes til din organisations edgeenheder, behandles og derefter sendes på internettet.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-before-tunneling.png" alt-text="Netværkstrafik fra VPN-klienter uden netværksforbindelse." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-before-tunneling.png":::

Microsoft 365 trafik skal tage en indirekte rute gennem din organisation, som kan videresendes til et Microsoft-netværks indgangspunkt langt væk fra VPN-klientens fysiske placering. Denne indirekte sti føjer ventetid til netværkstrafikken og reducerer den overordnede ydeevne.

Med opdelte netværksnetværk kan du konfigurere din VPN-klient til at udelukke bestemte typer trafik fra at blive sendt via VPN-forbindelsen til organisationens netværk.

Hvis du vil optimere adgangen Microsoft 365 skyressourcer, skal du konfigurere dine opdelte VPN-klienter til at udelukke trafik til  kategorien Optimer Microsoft 365 slutpunkter via VPN-forbindelsen. Du kan finde flere oplysninger [Office 365 kategorier for slutpunkter](../enterprise/microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories). Se [denne liste](../enterprise/urls-and-ip-address-ranges.md) over slutpunkter i kategorien Optimer.

Her er den resulterende trafikstrøm, hvor det meste af trafik til Microsoft 365-skyapps tilsidesætter VPN-forbindelsen.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-after-tunneling.png" alt-text="Netværkstrafik fra VPN-klienter med indføring." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-after-tunneling.png":::

Dette giver VPN-klienten mulighed for at sende og modtage Microsoft 365 skytjenestetrafik direkte via internettet og til det nærmeste indgangspunkt til Microsoft-netværket.

Du kan finde flere oplysninger og vejledning i [Optimer Office 365 forbindelse for eksterne brugere, der bruger VPN-opdeling af netværksforbindelse](../enterprise/microsoft-365-vpn-split-tunnel.md).

## <a name="deploy-remote-access-when-all-your-apps-are-web-apps-and-you-have-hybrid-identity"></a>Installér fjernadgang, når alle dine apps er webapps, og du har hybrididentitet

Hvis dine eksterne medarbejdere ikke bruger en traditionel VPN-klient, og dine lokale brugerkonti og grupper synkroniseres med Azure AD, kan du bruge Azure AD Application Proxy til at give sikker fjernadgang til webbaserede programmer, der hostes på lokale servere. Webbaserede programmer omfatter SharePoint serverwebsteder, Outlook Web Access-servere eller andre webbaserede line of business-programmer.

Her er komponenterne i Azure AD-programproxyen.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-application-proxy.png" alt-text="Komponenter i Azure AD-programproxy." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-application-proxy.png":::

Få mere at vide under denne oversigt [over Azure AD-programproxy](/azure/active-directory/manage-apps/application-proxy).

> [!NOTE]
> Azure AD-programproxy er ikke inkluderet i et Microsoft 365 abonnement. Du skal betale for brugen med et separat Azure-abonnement.

## <a name="deploy-remote-access-when-not-all-your-apps-are-web-apps"></a>Installér fjernadgang, når ikke alle dine apps er webapps

Hvis dine eksterne medarbejdere ikke bruger en traditionel VPN-klient, og du har apps, der ikke er webbaserede, kan du bruge et Azure Point-to-Site (P2S) VPN.

En P2S VPN-forbindelse opretter en sikker forbindelse fra en fjernmedarbejders enhed til organisationens netværk via et virtuelt Azure-netværk.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-p2s-vpn.png" alt-text="Komponenter i Azure P2S VPN." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-p2s-vpn.png":::

Du kan finde flere oplysninger i [denne oversigt over P2S VPN](/azure/vpn-gateway/point-to-site-about).

> [!NOTE]
> Azure P2S VPN er ikke inkluderet i et Microsoft 365 abonnement. Du skal betale for brugen med et separat Azure-abonnement.

## <a name="deploy-windows-365-to-provide-remote-access-for-remote-workers-using-personal-devices"></a>Installér Windows 365 for at give fjernadgang til eksterne medarbejdere ved hjælp af personlige enheder

For at understøtte eksterne medarbejdere, der kun kan bruge deres personlige og ikke-administrerede enheder, skal du bruge Windows 365 til at oprette og tildele virtuelle skriveborde, som dine brugere kan bruge hjemmefra. Med en lokal netværksforbindelse (OPNC) kan Windows 365-sky-pc'er fungere på samme måde som pc'er, der har forbindelse til din organisations netværk.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-windows-365.png" alt-text="Komponenter i Windows 365." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-windows-365.png":::

Få mere at vide under [denne oversigt over Windows 365](/windows-365/overview).

> [!NOTE]
> Windows 365 er ikke inkluderet i et Microsoft 365 abonnement. Du skal betale for brugen med et separat abonnement.

## <a name="protect-your-remote-desktop-services-connections-with-the-remote-desktop-services-gateway"></a>Beskyt dine Fjernskrivebord-forbindelser med Remote Desktop Services Gateway

Hvis du bruger RDS (Remote Desktop Services) til at give medarbejdere mulighed for at oprette forbindelse til Windows-baserede computere på dit lokale netværk, skal du bruge en Microsoft Fjernskrivebord Services-gateway i dit edge-netværk. Gatewayen bruger Transport Layer Security (TLS) til at kryptere trafik og forhindrer, at den lokale computer, der hoster RDS, kan blive direkte eksponeret for internettet.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-remote-desktop.png" alt-text="Fjernskrivebord-forbindelser med Gateway til Fjernskrivebord-tjenester." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-remote-desktop.png":::

Se [denne artikel for at](https://www.microsoft.com/security/blog/2020/04/16/security-guidance-remote-desktop-adoption/) få flere oplysninger.

## <a name="admin-technical-resources-for-remote-access"></a>Tekniske ressourcer for fjernadgang til administratorer

- [Sådan optimerer du Office 365 trafik til eksterne medarbejdere & at reducere belastningen på din infrastruktur](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571)
- [Optimer Office 365 forbindelse for eksterne brugere ved hjælp af VPN-opdeling af netværksforbindelse](../enterprise/microsoft-365-vpn-split-tunnel.md)

## <a name="results-of-step-2"></a>Resultater af trin 2

Efter installation af en fjernadgangsløsning til dine fjernmedarbejdere:

| Konfiguration af fjernadgang | Resultater |
|:-------|:-----|
| En VPN-løsning med fjernadgang er på plads | Du har konfigureret din VPN-klient til fjernadgang til opdelt inddelning og til kategorien Optimer Microsoft 365 slutpunkter. |
| Ingen VPN-løsning til fjernadgang, og du skal kun have fjernadgang til lokale webbaserede apps | Du har konfigureret Azure-programproxy. |
| Ingen VPN-løsning til fjernadgang, og du skal have adgang til lokale apps, hvoraf nogle ikke er webbaserede | Du har konfigureret Azure P2S VPN. |
| Fjernarbejdere bruger deres personlige enheder hjemmefra | Du har konfigureret Windows 365. |
| Fjernarbejdere bruger RDS-forbindelser til lokale systemer | Du har installeret en Gateway til Fjernskrivebord-tjenester i dit grænsenetværk. |
|||

## <a name="next-step"></a>Næste trin

[![Trin 3: Installer Microsoft 365 og overholdelsestjenester.](../media/empower-people-to-work-remotely/remote-workers-step-grid-3.png)](empower-people-to-work-remotely-security-compliance.md)

Fortsæt med [trin 3 for](empower-people-to-work-remotely-security-compliance.md) at installere Microsoft 365 og overholdelsestjenester for at beskytte dine apps, data og enheder.
