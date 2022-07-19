---
title: Playbook til prøveversion – Microsoft Defender for Endpoint
description: Brug denne vejledning til at få mest ud af din 90-dages gratis prøveversion. Se, hvordan Defender for Endpoint kan hjælpe med at forhindre, registrere, undersøge og reagere på avancerede trusler.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: 07/07/2022
ms.prod: m365-security
ms.technology: mde
ms.localizationpriority: medium
ms.reviewer: ''
f1.keywords: NOCSH
ms.openlocfilehash: 2b7a4d47d07fd609fb9dd424f2a8b89af2ed0b9b
ms.sourcegitcommit: 9fdb5c5b9eaf0c8a8d62b579a5fb5a5dc2d29fa9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/11/2022
ms.locfileid: "66858952"
---
# <a name="trial-playbook-microsoft-defender-for-endpoint"></a>Playbook til prøveversion: Microsoft Defender for Endpoint

Velkommen til playbooken til Microsoft Defender for Endpoint Plan 2-prøveversionen!

Denne playbook er en enkel vejledning, der hjælper dig med at få mest ud af din gratis prøveversion. Ved hjælp af de foreslåede trin i denne artikel fra Microsoft Defender-teamet lærer du, hvordan Defender for Endpoint kan hjælpe dig med at forhindre, registrere, undersøge og reagere på avancerede trusler.

## <a name="what-is-defender-for-endpoint"></a>Hvad er Defender for Slutpunkt?

[Defender for Endpoint](microsoft-defender-endpoint.md) er en sikkerhedsplatform til virksomhedsslutpunkter, der bruger følgende kombination af teknologi, der er indbygget i Windows og Microsofts robuste cloudtjeneste: 

- **Sensorer til slutpunktets funktionsmåde: Disse sensorer** er integreret i Windows og indsamler og behandler adfærdsmæssige signaler fra operativsystemet og sender sensordata til din private, isolerede cloudforekomst af Defender for Endpoint.

- **Analyse af cloudsikkerhed**: Brug af big data, enhedslæring og unik Microsoft-optik på tværs af Windows-økosystemet, virksomhedscloudprodukter (f.eks. Microsoft 365) og onlineaktiver, adfærdssignaler oversættes til indsigt, registreringer og anbefalede svar på avancerede trusler.

- **Trusselsintelligens**: Genereret af Microsoft-jægere og sikkerhedsteams og forstærket med trusselsintelligens leveret af partnere gør trusselsintelligens det muligt for Defender for Endpoint at identificere værktøjer, teknikker og procedurer for hackere og generere beskeder, når de observeres i indsamlede sensordata.

<center><h2>Microsoft Defender for Endpoint</center></h2>
<table>
<tr>
<td><a href="microsoft-defender-endpoint.md#tvm"><center><img src="images/logo-mdvm.png" alt="Vulnerability Management"> <br><b> Administration af sårbarheder i core Defender</b></center></a></td>
<td><a href="microsoft-defender-endpoint.md#asr"><center><img src="images/asr-icon.png" alt="Attack surface reduction"><br><b>Reduktion af angrebsoverflade</b></center></a></td>
<td><center><a href="microsoft-defender-endpoint.md#ngp"><img src="images/ngp-icon.png" alt="Next-generation protection"><br> <b>Næste generations beskyttelse</b></a></center></td>
<td><center><a href="microsoft-defender-endpoint.md#edr"><img src="images/edr-icon.png" alt="Endpoint detection and response"><br> <b>Registrering af slutpunkt og svar</b></a></center></td>
<td><center><a href="microsoft-defender-endpoint.md#ai"><img src="images/air-icon.png" alt="Automated investigation and remediation"><br> <b>Automatiseret undersøgelse og afhjælpning</b></a></center></td>
<td><center><a href="microsoft-defender-endpoint.md#mte"><img src="images/mte-icon.png" alt="Microsoft Threat Experts"><br> <b>Microsoft-trusselseksperter</b></a></center></td>
</tr>
<tr>
<td colspan="7">
<a href="microsoft-defender-endpoint.md#apis"><center><b>Centraliseret konfiguration og administration, API'er</a></b></center></td>
</tr>
<tr>
<td colspan="7"><a href="microsoft-defender-endpoint.md#mtp"><center><b>Microsoft 365 Defender</a></center></b></td>
</tr>
</table>
<br>

**Lad os komme i gang!**

## <a name="set-up-your-trial"></a>Konfigurer din prøveversion

1. [Bekræft din licenstilstand](#step-1-confirm-your-license-state).
2. [Konfigurer rollebaseret adgangskontrol, og tildel tilladelser til dit sikkerhedsteam](#step-2-set-up-role-based-access-control-and-grant-permissions-to-your-security-team).
3. [Besøg Microsoft 365 Defender-portalen](#step-3-visit-the-microsoft-365-defender-portal).
4. [Onboarde slutpunkter ved hjælp af et af de understøttede administrationsværktøjer](#step-4-onboard-endpoints-using-any-of-the-supported-management-tools).
5. [Konfigurer egenskaber](#step-5-configure-capabilities).
6. [Oplev Microsoft Defender for Endpoint gennem simulerede angreb](#step-6-experience-microsoft-defender-for-endpoint-through-simulated-attacks).
7. [Konfigurer evalueringslaboratoriet for Microsoft Defender for Endpoint](#step-7-set-up-the-microsoft-defender-for-endpoint-evaluation-lab).

## <a name="step-1-confirm-your-license-state"></a>Trin 1: Bekræft din licenstilstand

Hvis du vil sikre dig, at dit Defender for Endpoint-abonnement er korrekt klargjort, kan du kontrollere din licenstilstand enten i Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com)) eller Azure Active Directory ([https://portal.azure.com](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products)).

[Kontrollér din licenstilstand](production-deployment.md#check-license-state).

## <a name="step-2-set-up-role-based-access-control-and-grant-permissions-to-your-security-team"></a>Trin 2: Konfigurer rollebaseret adgangskontrol, og tildel tilladelser til dit sikkerhedsteam

Microsoft anbefaler, at du bruger begrebet færrest mulige rettigheder. Defender for Endpoint bruger indbyggede roller i Azure Active Directory. [Gennemse de forskellige roller, der er tilgængelige,](/azure/active-directory/roles/permissions-reference) og vælg de relevante roller for dit sikkerhedsteam. Nogle roller skal muligvis anvendes midlertidigt og fjernes, når prøveversionen er fuldført.

Brug [Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure) til at administrere dine roller for at give brugere med mappetilladelser ekstra overvågning, kontrol og adgangskontrol.

Defender for Endpoint understøtter to måder at administrere tilladelser på:

- Grundlæggende administration af tilladelser: Angiv tilladelser til enten fuld adgang eller skrivebeskyttet. Brugere med rollerne Global administrator eller Sikkerhedsadministrator i Azure Active Directory har fuld adgang. Rollen Sikkerhedslæser har skrivebeskyttet adgang og giver ikke adgang til at få vist maskiner/enhedslager.
- Rollebaseret adgangskontrol: Angiv detaljerede tilladelser ved at definere roller, tildele Azure AD brugergrupper til rollerne og tildele brugergrupperne adgang til enhedsgrupper. Du kan få flere oplysninger under [Administrer portaladgang ved hjælp af rollebaseret adgangskontrol](rbac.md).

## <a name="step-3-visit-the-microsoft-365-defender-portal"></a>Trin 3: Besøg Microsoft 365 Defender-portalen

På Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) kan du få adgang til funktionerne i Defender for Endpoint.

1. [Gennemse, hvad du kan forvente](../defender/microsoft-365-defender-portal.md) på Microsoft 365 Defender-portalen.

2. Gå til , [https://security.microsoft.com](https://security.microsoft.com) og log på.

3. I navigationsruden skal du se afsnittet **Slutpunkter** for at få adgang til dine egenskaber. 

## <a name="step-4-onboard-endpoints-using-any-of-the-supported-management-tools"></a>Trin 4: Onboard slutpunkter ved hjælp af et af de understøttede administrationsværktøjer 

I dette afsnit beskrives de generelle trin, du skal udføre for at onboarde enheder (slutpunkter).

1. [Se denne video](https://www.microsoft.com/videoplayer/embed/RE4bGqr) for at få et hurtigt overblik over onboardingprocessen og få mere at vide om de tilgængelige værktøjer og metoder.

2. Gennemse [indstillingerne for onboardingværktøjet til din enhed](onboarding.md) , og vælg den mest relevante indstilling for dit miljø. 

## <a name="step-5-configure-capabilities"></a>Trin 5: Konfigurer egenskaber 

Når du har onboardet enheder (slutpunkter), skal du konfigurere de forskellige funktioner, f.eks. registrering og svar af slutpunkter, næste generations beskyttelse og reduktion af angrebsoverfladen.

Brug [denne tabel](onboarding.md) til at vælge de komponenter, der skal konfigureres. Vi anbefaler, at du konfigurerer alle tilgængelige funktioner, men du kan springe dem over, der ikke gælder.

## <a name="step-6-experience-microsoft-defender-for-endpoint-through-simulated-attacks"></a>Trin 6: Oplev Microsoft Defender for Endpoint gennem simulerede angreb

Det kan være en god idé at opleve Defender for Endpoint, før du onboarder mere end nogle få enheder til tjenesten. For at gøre dette kan du køre kontrollerede angrebssimuleringer på nogle få testenheder. Når du har kørt de simulerede angreb, kan du gennemse, hvordan Defender for Endpoint viser skadelig aktivitet og undersøge, hvordan det giver mulighed for et effektivt svar.

Hvis du vil køre en af de angivne simuleringer, skal du bruge mindst [én onboardet enhed](onboard-configure.md).

1. Få adgang til selvstudierne. Vælg **Selvstudier** under **Slutpunkter** i Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) i navigationsruden.

2. Læs det gennemgangsdokument, der leveres med hvert angrebsscenarie. Hvert dokument indeholder krav til operativsystem og program og detaljerede instruktioner, der er specifikke for et angrebsscenarie.

3. [Kør en simulering](attack-simulations.md).

## <a name="step-7-set-up-the-microsoft-defender-for-endpoint-evaluation-lab"></a>Trin 7: Konfigurer evalueringslaboratoriet for Microsoft Defender for Endpoint   

Det Microsoft Defender for Endpoint evalueringslaboratorium er designet til at fjerne kompleksiteten i enheds- og miljøkonfigurationen, så du kan fokusere på at evaluere platformens funktioner, køre simuleringer og se funktionerne til forebyggelse, registrering og afhjælpning i aktion. Ved hjælp af den forenklede konfiguration i evalueringslaboratoriet kan du fokusere på at køre dine egne testscenarier og de forudlavede simuleringer for at se, hvordan Defender for Endpoint klarer sig.

- [Se videooversigten over](https://www.microsoft.com/videoplayer/embed/RE4qLUM) evalueringslaboratoriet
- [Kom i gang med øvelsen](evaluation-lab.md) 


## <a name="see-also"></a>Se også

- [Teknisk dokumentation til Defender for Endpoint](microsoft-defender-endpoint.md)
- [Microsoft Security Technical Content Library](https://www.microsoft.com/security/content-library/Home/Index)
- [Demonstration af Defender for Endpoint](https://cdx.transform.microsoft.com/experience-detail/d5eca65d-13a3-464d-9171-c24cf9dd6050)

