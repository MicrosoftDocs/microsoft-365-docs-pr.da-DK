---
title: Anbefalede Microsoft Defender for Cloud Apps politikker for SaaS-apps – Microsoft 365 Enterprise | Microsoft Docs
description: Beskriver anbefalede politikker for integration med Microsoft Defender for Cloud Apps.
author: BrendaCarter
manager: laurawi
ms.topic: article
audience: Admin
ms.author: bcarter
ms.date: 03/22/2021
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
ms.prod: m365-security
ms.openlocfilehash: 8386b01da6d0db5703d74d96f4e22de18b1f7d70
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873616"
---
# <a name="recommended-microsoft-defender-for-cloud-apps-policies-for-saas-apps"></a>Anbefalede Microsoft Defender for Cloud Apps politikker for SaaS-apps

Microsoft Defender for Cloud Apps bygger på Azure AD politikker for betinget adgang, der gør det muligt at overvåge og styre detaljerede handlinger med SaaS-apps i realtid, f.eks. blokering af downloads, uploads, kopiering og indsættelse og udskrivning. Denne funktion føjer sikkerhed til sessioner, der medfører en indbygget risiko, f.eks. når virksomhedsressourcer tilgås fra ikke-administrerede enheder eller af gæstebrugere.

Defender for Cloud Apps kan også integreres oprindeligt med Microsoft Purview Information Protection, hvilket giver indholdsinspektion i realtid, så du kan finde følsomme data, der er baseret på følsomme informationstyper og følsomhedsmærkater, og foretage de nødvendige handlinger.

Denne vejledning indeholder anbefalinger til disse scenarier:

- Overfør SaaS-apps til it-administration
- Juster beskyttelse for bestemte SaaS-apps
- Konfigurer Microsoft Purview forebyggelse af datatab (DLP) for at hjælpe med at overholde databeskyttelsesreglerne

## <a name="bring-saas-apps-into-it-management"></a>Overfør SaaS-apps til it-administration

Det første trin i brugen af Defender for Cloud Apps til at administrere SaaS-apps er at finde disse og derefter føje dem til din Azure AD lejer. Hvis du har brug for hjælp til at finde, skal du se [Find og administrer SaaS-apps i dit netværk](/cloud-app-security/tutorial-shadow-it). Når du har opdaget apps, kan du [føje disse til din Azure AD lejer](/azure/active-directory/manage-apps/add-application-portal).

Du kan begynde at administrere disse ved at gøre følgende:

1. I Azure AD skal du først oprette en ny politik for betinget adgang og konfigurere den til "Brug appkontrol med betinget adgang". Dette omdirigerer anmodningen til Defender for Cloud Apps. Du kan oprette én politik og føje alle SaaS-apps til denne politik.
1. Derefter skal du oprette sessionspolitikker i Defender for Cloud Apps. Opret én politik for hvert kontrolelement, du vil anvende.

Tilladelser til SaaS-apps er typisk baseret på virksomhedens behov for adgang til appen. Disse tilladelser kan være meget dynamiske. Brug af Defender for Cloud Apps-politikker sikrer beskyttelse af appdata, uanset om brugerne er tildelt til en Azure AD gruppe, der er knyttet til startpunkt, virksomhed eller specialiseret sikkerhedsbeskyttelse.

For at beskytte data på tværs af din samling af SaaS-apps viser følgende diagram de nødvendige Azure AD politik for betinget adgang samt foreslåede politikker, du kan oprette i Defender for Cloud Apps. I dette eksempel gælder de politikker, der er oprettet i Defender for Cloud Apps, for alle De SaaS-apps, du administrerer. Disse er designet til at anvende relevante kontrolelementer baseret på, om enheder administreres, samt følsomhedsmærkater, der allerede er anvendt på filer.

:::image type="content" source="../../media/microsoft-365-policies-configurations/mcas-manage-saas-apps-2.png" alt-text="Politikkerne for administration af SaaS-apps i Defender for Cloud Apps" lightbox="../../media/microsoft-365-policies-configurations/mcas-manage-saas-apps-2.png":::

I følgende tabel vises den nye politik for betinget adgang, du skal oprette i Azure AD.

|Beskyttelsesniveau|Politik|Flere oplysninger|
|---|---|---|
|Alle beskyttelsesniveauer|[Brug appkontrol med betinget adgang i Defender for Cloud Apps](/cloud-app-security/proxy-deployment-aad#configure-integration-with-azure-ad)|Dette konfigurerer din IdP (Azure AD) til at arbejde med Defender for Cloud Apps.|
||||

I denne næste tabel vises de eksempelpolitikker, der er illustreret ovenfor, og som du kan oprette for at beskytte alle SaaS-apps. Sørg for at evaluere målene for din egen virksomhed, sikkerhed og overholdelse af angivne standarder, og opret derefter politikker, der giver den mest passende beskyttelse af dit miljø.

|Beskyttelsesniveau|Politik|
|---|---|
|Udgangspunkt|Overvåg trafik fra ikke-administrerede enheder <p> Føj beskyttelse til filoverførsler fra ikke-administrerede enheder|
|Enterprise|Bloker download af filer, der er mærket med følsomme eller klassificerede fra ikke-administrerede enheder (dette giver kun browseradgang)|
|Specialiseret sikkerhed|Bloker download af filer, der er mærket med klassificeret fra alle enheder (dette giver kun browseradgang)|
|||

Du kan finde en komplet vejledning i, hvordan du konfigurerer appkontrol med betinget adgang, under [Udrul appkontrol med betinget adgang for udvalgte apps](/cloud-app-security/proxy-deployment-aad). I denne artikel gennemgås processen med at oprette den nødvendige politik for betinget adgang i Azure AD og teste dine SaaS-apps.

Du kan få flere oplysninger under [Beskyt apps med Microsoft Defender for Cloud Apps appkontrol med betinget adgang](/cloud-app-security/proxy-intro-aad).

## <a name="tune-protection-for-specific-saas-apps"></a>Juster beskyttelse for bestemte SaaS-apps

Det kan være en god idé at anvende yderligere overvågning og kontrolelementer på bestemte SaaS-apps i dit miljø. Med Defender for Cloud Apps kan du gøre dette. Hvis en app som Box f.eks. bruges meget i dit miljø, giver det mening at anvende yderligere kontrolelementer. Eller hvis din juridiske afdeling eller økonomiafdeling bruger en bestemt SaaS-app til følsomme forretningsdata, kan du målrette ekstra beskyttelse mod disse apps.

Du kan f.eks. beskytte dit Box-miljø med disse typer indbyggede politikskabeloner til registrering af uregelmæssigheder:

- Aktivitet fra anonyme IP-adresser
- Aktivitet fra sjældne lande
- Aktivitet fra mistænkelige IP-adresser
- Umulig rejse
- Aktivitet udført af afsluttet bruger (kræver AAD som IdP)
- Registrering af malware
- Flere mislykkede logonforsøg
- Ransomware-aktivitet
- Risikable Oauth-app
- Usædvanlig fildelingsaktivitet

Det er eksempler. Der tilføjes jævnligt yderligere politikskabeloner. Du kan finde eksempler på, hvordan du kan anvende yderligere beskyttelse på bestemte apps under [Beskyttelse af forbundne apps](/cloud-app-security/protect-connected-apps).

[Hvordan Defender for Cloud Apps hjælper med at beskytte dit Box-miljø](/cloud-app-security/protect-box) , viser de typer kontrolelementer, der kan hjælpe dig med at beskytte dine forretningsdata i Box og andre apps med følsomme data.

## <a name="configure-data-loss-prevention-dlp-to-help-comply-with-data-protection-regulations"></a>Konfigurer DLP (forebyggelse af datatab) for at overholde databeskyttelsesreglerne

Defender for Cloud Apps kan være et værdifuldt værktøj til konfiguration af beskyttelse mod overholdelse af regler og standarder. I dette tilfælde opretter du specifikke politikker for at søge efter bestemte data, som en forordning gælder for, og konfigurere hver politik til at udføre de relevante handlinger.

Følgende illustration og tabel indeholder flere eksempler på politikker, der kan konfigureres for at hjælpe med at overholde den generelle forordning om databeskyttelse (GDPR). I disse eksempler søger politikker efter bestemte data. Baseret på dataenes følsomhed er hver politik konfigureret til at udføre de relevante handlinger.

:::image type="content" source="../../media/microsoft-365-policies-configurations/mcas-dlp.png" alt-text="Siden Defender for Cloud Apps-politikker til forebyggelse af datatab" lightbox="../../media/microsoft-365-policies-configurations/mcas-dlp.png":::

|Beskyttelsesniveau|Eksempelpolitikker|
|---|---|
|Udgangspunkt|Besked, når filer, der indeholder denne følsomme oplysningstype ("Kreditkortnummer"), deles uden for organisationen <p> >Bloker downloads af filer, der indeholder denne følsomme oplysningstype ("Kreditkortnummer") til ikke-administrerede enheder|
|Enterprise|Beskyt downloads af filer, der indeholder denne type følsomme oplysninger ("Kreditkortnummer") til administrerede enheder <p> Bloker downloads af filer, der indeholder denne følsomme oplysningstype ("Kreditkortnummer") til ikke-administrerede enheder <p> Besked, når en fil med på disse mærkater uploades til OneDrive for Business eller box (kundedata, HR: løndata, HR, medarbejderdata)|
|Specialiseret sikkerhed|Besked, når filer med denne mærkat ("Højt klassificeret") downloades til administrerede enheder <p> Bloker downloads af filer med denne mærkat ("Højt klassificeret") til ikke-administrerede enheder|
|||

## <a name="next-steps"></a>Næste trin

Du kan få flere oplysninger om brug af Defender for Cloud Apps [i dokumentationen til Microsoft Defender for Cloud Apps](/defender-cloud-apps/).
