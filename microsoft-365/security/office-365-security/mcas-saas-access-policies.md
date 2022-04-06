---
title: Anbefalede politikker for Microsoft Defender til skyapps til SaaS-apps – Microsoft 365 Enterprise | Microsoft Docs
description: Beskriver anbefalede politikker for integration med Microsoft Defender til skyapps.
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
ms.openlocfilehash: 95b46e1c92354015ce6f8d9c5b1fa4b6e9642785
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683313"
---
# <a name="recommended-microsoft-defender-for-cloud-apps-policies-for-saas-apps"></a>Anbefalede politikker for Microsoft Defender til skyapps til SaaS-apps

Microsoft Defender til skyapps er baseret på politikker for betinget adgang i Azure AD for at aktivere overvågning og kontrol i realtid af granularhandlinger med SaaS-apps, f.eks. blokering af downloads, uploads, kopiér og sæt ind og udskrivning. Denne funktion føjer sikkerhed til sessioner, der er forbundet med risici, f.eks. når virksomhedens ressourcer åbnes fra ikke-administrerede enheder eller af gæstebrugere.

Defender til skyapps integreres også oprindeligt med Microsoft Information Protection, hvilket giver inspektion af indhold i realtid for at finde følsomme data baseret på følsomme oplysningstyper og følsomhedsmærkater og for at foretage den rette handling.

Denne vejledning indeholder anbefalinger til disse scenarier:

- Få SaaS-apps ind i it-administration
- Finjuster beskyttelse af bestemte SaaS-apps
- Konfigurer forebyggelse af datatab (DLP) for at overholde databeskyttelsesreglerne

## <a name="bring-saas-apps-into-it-management"></a>Få SaaS-apps ind i it-administration

Det første trin i at bruge Defender til skyapps til at administrere SaaS-apps er at finde disse og derefter føje dem til din Azure AD-lejer. Hvis du har brug for hjælp til discovery, kan [du se Opdag og administrer SaaS-apps i dit netværk](/cloud-app-security/tutorial-shadow-it). Når du har fundet apps, skal du [føje disse til din Azure AD-lejer](/azure/active-directory/manage-apps/add-application-portal).

Du kan begynde at administrere disse ved at gøre følgende:

1. Først skal du i Azure AD oprette en ny politik for betinget adgang og konfigurere den til "Brug Betinget adgang-appkontrol". Dette omdirigerer anmodningen til Defender til skyapps. Du kan oprette én politik og tilføje alle SaaS-apps til denne politik.
1. Dernæst skal du i Defender til skyapps oprette sessionspolitikker. Opret én politik for hvert kontrolelement, du vil anvende.

Tilladelser til SaaS-apps er typisk baseret på forretningsmæssige behov for adgang til appen. Disse tilladelser kan være meget dynamiske. Brug af Defender til skyapps-politikker sikrer beskyttelse af appdata, uanset om brugerne er tildelt en Azure AD-gruppe, der er knyttet til udgangspunkt, virksomhed eller særlig sikkerhedsbeskyttelse.

For at beskytte data på tværs af din samling af SaaS-apps illustrerer følgende diagram den nødvendige politik for betinget adgang til Azure AD samt foreslåede politikker, du kan oprette i Defender til skyapps. I dette eksempel gælder de politikker, der er oprettet i Defender til Skyapps, for alle SaaS-apps, du administrerer. Disse er designet til at anvende relevante kontrolelementer baseret på, om enhederne administreres, samt følsomhedsmærkater, der allerede er anvendt på filer.

:::image type="content" source="../../media/microsoft-365-policies-configurations/mcas-manage-saas-apps-2.png" alt-text="Politikker for administration af SaaS-apps i Defender til skyapps." lightbox="../../media/microsoft-365-policies-configurations/mcas-manage-saas-apps-2.png":::

I følgende tabel vises den nye politik for betinget adgang, du skal oprette i Azure AD.

|Beskyttelsesniveau|Politik|Flere oplysninger|
|---|---|---|
|Alle beskyttelsesniveauer|[Brug Betinget adgang-appkontrol i Defender til skyapps](/cloud-app-security/proxy-deployment-aad#configure-integration-with-azure-ad)|Dette konfigurerer din IdP (Azure AD) til at fungere sammen med Defender til skyapps.|
||||

I den næste tabel vises de eksempelpolitikker, der er illustreret ovenfor, som du kan oprette for at beskytte alle SaaS-apps. Sørg for at evaluere dine egne målsætninger for forretning, sikkerhed og overholdelse af regler og standarder, og opret derefter politikker, der giver den mest passende beskyttelse af dit miljø.

|Beskyttelsesniveau|Politik|
|---|---|
|Udgangspunkt|Overvåg trafik fra enheder, der ikke er administrerede <p> Føj beskyttelse til filoverførsler fra enheder, der ikke er administrerede|
|Enterprise|Bloker download af filer, der er mærket med følsomme eller klassificeret fra enheder, der ikke er administrerede (dette giver kun adgang i browseren)|
|Speciel sikkerhed|Bloker download af filer, der er mærket klassificeret fra alle enheder (dette giver kun browseradgang)|
|||

Du kan finde en komplet vejledning til konfiguration af Betinget adgang-appkontrol i [Installer Betinget adgang-appkontrol til udvalgte apps](/cloud-app-security/proxy-deployment-aad). I denne artikel bliver du vejet gennem processen med at oprette den nødvendige politik for betinget adgang i Azure AD og teste dine SaaS-apps.

Du kan få mere at vide [under Beskyt apps med Microsoft Defender til skyapps Betinget adgang til appkontrol](/cloud-app-security/proxy-intro-aad).

## <a name="tune-protection-for-specific-saas-apps"></a>Finjuster beskyttelse af bestemte SaaS-apps

Det kan være en ide at anvende yderligere overvågning og kontrolelementer på bestemte SaaS-apps i dit miljø. Defender til skyapps giver dig mulighed for at gøre dette. Hvis f.eks. en app som Box bruges meget i dit miljø, giver det mening at anvende yderligere kontrolelementer. Eller hvis din juridiske afdeling eller økonomiafdelingen bruger en bestemt SaaS-app til følsomme forretningsdata, kan du målrette ekstra beskyttelse mod disse apps.

Du kan f.eks. beskytte dit Box-miljø med disse typer indbyggede politikskabeloner til registrering af unormalt indhold:

- Aktivitet fra anonyme IP-adresser
- Aktivitet fra det sjældne land/område
- Aktivitet fra mistænkelige IP-adresser
- Umulig rejse
- Aktivitet, der er udført af en afsluttet bruger (kræver AAD som IdP)
- Registrering af malware
- Flere mislykkede logonforsøg
- Ransomware-aktivitet
- Risikabel Oauth-app
- Usædvanlig fildelingsaktivitet

Disse er eksempler. Der tilføjes flere politikskabeloner med jævne mellemrum. Du kan finde eksempler på, hvordan du anvender yderligere beskyttelse på bestemte apps, under [Beskyttelse af tilknyttede apps](/cloud-app-security/protect-connected-apps).

[Hvordan Defender til skyapps](/cloud-app-security/protect-box) hjælper med at beskytte dit Box-miljø, viser de typer kontrolelementer, der kan hjælpe dig med at beskytte dine virksomhedsdata i Box og andre apps med følsomme data.

## <a name="configure-data-loss-prevention-dlp-to-help-comply-with-data-protection-regulations"></a>Konfigurer forebyggelse af datatab (DLP) for at overholde databeskyttelsesreglerne

Defender til skyapps kan være et værdifuldt værktøj til konfiguration af beskyttelse mod overholdelse af regler og standarder. I dette tilfælde skal du oprette specifikke politikker for at søge efter bestemte data, som en regel gælder for, og konfigurere hver politik til at tage den relevante handling.

Følgende illustration og tabel indeholder flere eksempler på politikker, der kan konfigureres til at hjælpe med at overholde Persondataforordningen (GDPR). I disse eksempler søger politikker efter bestemte data. Baseret på dataenes følsomhed er hver politik konfigureret til at tage de nødvendige handlinger.

:::image type="content" source="../../media/microsoft-365-policies-configurations/mcas-dlp.png" alt-text="Eksempel på Defender for Cloud Apps-politikker til forebyggelse af datatab." lightbox="../../media/microsoft-365-policies-configurations/mcas-dlp.png":::

|Beskyttelsesniveau|Eksempelpolitikker|
|---|---|
|Udgangspunkt|Besked, når filer, der indeholder denne type følsomme oplysninger ("kreditkortnummer") deles uden for organisationen <p> >bloker overførsler af filer, der indeholder denne type af følsomme oplysninger ("kreditkortnummer") til ikke-administrerede enheder|
|Enterprise|Beskyt downloads af filer, der indeholder denne type af følsomme oplysninger ("kreditkortnummer") til administrerede enheder <p> Bloker overførsler af filer, der indeholder denne type af følsomme oplysninger ("kreditkortnummer") til enheder, der ikke er administrerede <p> Advarsel, når en fil med en af disse etiketter uploades til OneDrive for Business eller Box (kundedata, HR: løndata, HR, medarbejderdata)|
|Speciel sikkerhed|Giv besked, når filer med dette navn ("meget klassificeret") downloades til administrerede enheder <p> Bloker overførsler af filer med denne etiket ("meget klassificeret") til enheder, der ikke er administrerede|
|||

## <a name="next-steps"></a>Næste trin

Du kan finde flere oplysninger om brug af Defender til skyapps i [dokumentationen til Microsoft Defender til skyapps](//cloud-app-security/).
