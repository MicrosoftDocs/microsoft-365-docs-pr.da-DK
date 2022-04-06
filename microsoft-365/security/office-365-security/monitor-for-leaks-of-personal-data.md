---
title: Hold øje med lækager af personlige data
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 02/07/2018
audience: ITPro
ms.topic: overview
ms.collection:
- Strat_O365_Enterprise
- Ent_O365
- GDPR
- M365-security-compliance
ms.localizationpriority: high
search.appverid:
- MET150
description: Få mere at vide om tre værktøjer, du kan bruge til at overvåge for lækager af personlige data.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ba164fde38be1e8eed53b71ab568124140deaac5
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682697"
---
# <a name="monitor-for-leaks-of-personal-data"></a>Hold øje med lækager af personlige data

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Der er mange værktøjer, der kan bruges til at overvåge brugen og transport af personlige data. I dette emne beskrives tre værktøjer, der fungerer godt.

![Værktøjer til at overvåge brugen og transport af personlige data.](../../media/Monitor-for-leaks-of-personal-data-image1.png)

I illustrationen:

- Start med Microsoft 365 rapporter om forebyggelse af datatab til overvågning af personlige data SharePoint Online, OneDrive for Business og mail under overførsel. Disse rapporter giver det største detaljeniveau til overvågning af personlige data. Disse rapporter omfatter dog ikke alle tjenester i Office 365.

- Brug derefter påmindelsespolitikker og overvågningsloggen til at overvåge aktivitet på tværs af tjenester. Konfigurer løbende overvågning, eller søg i overvågningsloggen for at undersøge en hændelse. Overvågningsloggen fungerer på tværs af tjenester – Sway, Power BI, eDiscovery, Dynamics 365, Power Automate, Microsoft Teams, administratoraktivitet, OneDrive for Business, SharePoint Online, in transit- og postkasser. Skype samtaler medtages i in hvilende postkasser.

- Til sidst skal du bruge Microsoft Defender til skyapps til at overvåge filer med følsomme data i andre SaaS-udbydere. Muligheden for at bruge følsomme oplysningstyper og samlede etiketter på tværs af Azure Information Protection og Office med Defender til skyapps kommer snart. Du kan konfigurere politikker, der gælder for alle dine SaaS-apps eller bestemte apps (f.eks. Box). Defender til skyapps finder ikke filer i Exchange Online, herunder filer, der er vedhæftet mail.

## <a name="data-loss-prevention-reports"></a>Rapporter om forebyggelse af datatab

Når du har oprettet dine politikker til forebyggelse af datatab (DLP), skal du kontrollere, at de virker efter hensigten, og hjælpe dig med at overholde reglerne. Med DLP-rapporter i Office 365 kan du hurtigt se antallet af DLP-politikoverensstemmelser, tilsidesættelser eller falske positive; se, om de er mest populære over tid, filtrere rapporten på forskellige måder, og få vist flere detaljer ved at vælge et punkt på en linje på grafen.

Du kan bruge DLP-rapporterne til at:

- Fokuser på bestemte tidsperioder, og forstå årsagerne til stigninger i spidsbelastninger og tendenser.
- Opdag forretningsprocesser, der overtræder din organisations DLP-politikker.
- Forstå eventuelle forretningsmæssige konsekvenser af DLP-politikkerne.
- Få vist begrundelserne, som er indsendt af brugere, når de løser et politiktip ved at tilsidesætte politikken eller rapportere en falsk positiv.
- Kontrollér overholdelse af en bestemt DLP-politik ved at vise eventuelle matches for den pågældende politik.
- Få vist en liste over filer med følsomme data, der svarer til dine DLP-politikker i detaljeruden.

Desuden kan du bruge DLP-rapporterne til at finjustere dine DLP-politikker, mens du kører dem i testtilstand.

DLP-rapporter er i Microsoft 365 Overholdelsescenter. Gå til **sektionen Rapporter** \> **om** organisationsdata for at finde **DLP-politik** match, **DLP-hændelser** og **falske DLP-positive og tilsidesætter** rapporter.

Få mere at vide under [Få vist rapporter for forebyggelse af datatab](../../compliance/view-the-dlp-reports.md).

![Rapport, der viser opfylder DLP-politik.](../../media/Monitor-for-leaks-of-personal-data-image2.png)

## <a name="audit-log-and-alert-policies"></a>Politikker for overvågningslog og besked

Overvågningsloggen indeholder hændelser fra Exchange Online, SharePoint Online, OneDrive for Business, Azure Active Directory, Microsoft Teams, Power BI, Sway og andre tjenester.

Portalen Microsoft 365 Defender og overvågningsloggen Microsoft 365 Overholdelsescenter to måder at overvåge og rapportere mod overvågningsloggen på:

- Konfigurer påmindelsespolitikker, få vist vigtige beskeder og overvåg tendenser – Brug værktøjerne til påmindelsespolitik og dashboard til påmindelsesbeskeder i enten Microsoft 365 Defender-portalen eller Microsoft 365 Overholdelsescenter.
- Søg direkte i overvågningsloggen: Søg efter alle hændelser med en angivet dato. Eller du kan filtrere resultaterne ud fra bestemte kriterier, f.eks. den bruger, der udførte handlingen, handlingen eller destinationsobjektet.

Informationsteams og sikkerhedsteams kan bruge disse værktøjer til proaktivt at gennemse aktiviteter, der udføres af både slutbrugere og administratorer på tværs af tjenester. Automatiske beskeder kan konfigureres til at sende mailbeskeder, når visse aktiviteter sker på bestemte grupper af websteder – f.eks. når indhold deles fra websteder, der er kendt for at indeholde GDPR-relaterede oplysninger. Dette giver disse teams mulighed for at følge op med brugere for at sikre, at virksomhedens sikkerhedspolitikker følges, eller for at tilbyde yderligere kurser.

Informationssikkerhedsteams kan også søge i overvågningsloggen for at undersøge mistænkelige databrist og fastslå både den egentlige årsag og omfanget af brud. Denne indbyggede funktion letter overholdelse af artikel 33 og 34 i GDPR, som kræver, at der leveres meddelelser til GDPR-kontrolcenteret og til de registrerede selv om et databrud inden for en bestemt tidsperiode. Poster i overvågningslogfiler bevares kun i 90 dage inden for tjenesten – det anbefales ofte, og mange organisationer har krævet, at disse logfiler opbevares i længere perioder.

Løsninger er tilgængelige, som abonnerer på Unified Audit Logs via Microsoft Management Activity API, og de kan både gemme logposter efter behov og levere avancerede dashboards og beskeder. Et eksempel er [Microsoft OMS (Operations Management Suite).](/azure/operations-management-suite/oms-solution-office-365)

Flere oplysninger om beskedpolitikker og søgning i overvågningsloggen:

- [Beskedpolitikker i Microsoft 365](../../compliance/alert-policies.md)
- [Søg i overvågningsloggen efter bruger- og administratoraktivitet i Office 365](../../compliance/search-the-audit-log-in-security-and-compliance.md) (introduktion)
- [Slå søgning i overvågningslogfil til eller fra](../../compliance/turn-audit-log-search-on-or-off.md)
- [Søg i overvågningsloggen](../../compliance/search-the-audit-log-in-security-and-compliance.md)
- [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) (cmdlet)
- [Detaljerede egenskaber i overvågningsloggen](../../compliance/detailed-properties-in-the-office-365-audit-log.md)

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender til skyapps

Microsoft Defender til skyapps hjælper dig med at opdage andre SaaS-apps i brug på tværs af dine netværk og følsomme data, der sendes til og fra disse apps.

Microsoft Defender til skyapps er en omfattende tjeneste, der giver stor synlighed, granularkontrolelementer og forbedret trusselsbeskyttelse til dine skyapps. Den identificerer mere end 15.000 skyprogrammer i dit netværk fra alle enheder og giver risikoscore og løbende risikovurdering og analyse. Der kræves ingen agenter: Oplysninger indsamles fra dine firewalls og proxyer for at give dig komplet synlighed og kontekst til skybrug og skygge IT.

For bedre at forstå dit skymiljø giver funktionen Defender for Cloud Apps-undersøgelse stor synlighed i alle aktiviteter, filer og konti for godkendt og administrerede apps. Du kan få detaljerede oplysninger om et filniveau og finde ud af, hvor data rejses i skyappsene.

Følgende illustration viser f.eks. to politikker for Defender for Cloud Apps, som kan hjælpe med GDPR.

![Eksempel på politikker for Defender til skyapps.](../../media/Monitor-for-leaks-of-personal-data-image3.png)

Den første politikbeskeder, når filer med en foruddefineret PII-attribut eller et brugerdefineret udtryk, som du vælger, deles uden for organisationen fra de SaaS-apps, du vælger.

Den anden politik blokerer overførsler af filer til enhver ikke-administreret enhed. Du vælger de attributter i filerne, der skal søges efter, og de SaaS-apps, som politikken skal gælde for.

Disse attributtyper kommer snart til Defender til skyapps:

- Typer af følsomme oplysninger
- Samlede etiketter på tværs Microsoft 365 Og Azure Information Protection

### <a name="defender-for-cloud-apps-dashboard"></a>Dashboardet Defender til skyapps

Hvis du endnu ikke er begyndt at bruge Defender til skyapps, kan du starte med at starte det. Sådan får du adgang til Defender til skyapps: <https://portal.cloudappsecurity.com>.

> [!NOTE]
> Sørg for at aktivere "Scan automatisk filer efter klassificeringsetiketter til Azure Information Protection" (under Generelle indstillinger), når du går i gang med Defender til skyapps, eller før du tildeler navne. Efter konfigurationen scanner Defender til skyapps ikke eksisterende filer igen, før de er blevet ændret.

![Dashboard, der viser oplysninger om beskeder.](../../media/Monitor-for-leaks-of-personal-data-image4.png)

Flere oplysninger:

- [Installér Defender til skyapps](/cloud-app-security/getting-started-with-cloud-app-security)
- [Flere oplysninger om Microsoft Defender til skyapps](https://www.microsoft.com/cloud-platform/cloud-app-security)
- [Bloker downloads af følsomme oplysninger ved hjælp af proxyen for Microsoft Defender til skyapps](/cloud-app-security/use-case-proxy-block-session-aad)

## <a name="example-file-and-activity-policies-to-detect-sharing-of-personal-data"></a>Eksempel på fil- og aktivitetspolitikker til at registrere deling af personlige data

### <a name="detect-sharing-of-files-containing-pii--credit-card-number"></a>Registrer deling af filer, der indeholder piI – kreditkortnummer

Få besked, når en fil, der indeholder et kreditkortnummer, deles fra en godkendt skyapp.

|Kontrolelement|Indstillinger|
|---|---|
|Politiktype|Filpolitik|
|Politikskabelon|Ingen skabelon|
|Politikkens alvorsgrad|Høj|
|Kategori|DLP|
|Filterindstillinger|Adgangsniveau = Offentlig (internet), Offentlig, Ekstern <p> App = \<select apps\> (brug denne indstilling, hvis du vil begrænse overvågning til bestemte SaaS-apps)|
|Anvend på|Alle filer, alle ejere|
|Indholdsinspektion|Omfatter filer, der matcher et præsentationsudtryk: Alle lande: Økonomi: Kreditkortnummer <p> Kræver ikke relevant kontekst: ikke markeret (denne indstilling matcher også nøgleord samt regex) <p> Omfatter filer med mindst 1 match <p> Unmask the last 4 characters of the violation: checked|
|Beskeder|Opret en besked for hver matchende fil: markeret <p> Grænse for daglig besked: 1000 <p> Vælg en besked som mail: markeret <p> Hvis du vil: infosec@contoso.com|
|Styring|Microsoft OneDrive for Business <p> Gør privat: Markér Fjern eksterne brugere <p> Alle andre indstillinger: ikke markeret <p> Microsoft Office SharePoint Online <p> Gør privat: Markér Fjern eksterne brugere <p> Alle andre indstillinger: ikke markeret|

Lignende politikker:

- Registrer deling af filer, der indeholder PII – mailadresse
- Registrer deling af filer, der indeholder pii - pasnummer

### <a name="detect-customer-or-hr-data-in-box-or-onedrive-for-business"></a>Registrer kunde- eller HR-data i Box eller OneDrive for Business

Advarsel, når en fil med navnet Kundedata eller HR-data uploades til OneDrive for Business eller Box.

Bemærkninger:

- Boxovervågning kræver, at der konfigureres en forbindelse ved hjælp af API-forbindelses SDK.
- Denne politik kræver funktioner, der i øjeblikket findes i privat prøveversion.

|Kontrolelement|Indstillinger|
|---|---|
|Politiktype|Aktivitetspolitik|
|Politikskabelon|Ingen skabelon|
|Politikkens alvorsgrad|Høj|
|Kategori|Delingskontrol|
|Der skal handles på|Enkelt aktivitet|
|Filterindstillinger|Aktivitetstype = Upload fil <p> App = Microsoft OneDrive for Business og Box <p> Classification Label (currently in private preview): Azure Information Protection = Customer Data, HUMAN Resources —Salary Data, HUMAN Resources — Employee Data|
|Beskeder|Opret en besked: markeret <p> Grænse for daglig besked: 1000 <p> Vælg en besked som mail: markeret <p> Hvis du vil: infosec@contoso.com|
|Styring|Alle apps <p> Sæt bruger i karantæne: tjek <p> Alle andre indstillinger: ikke markeret <p> Office 365 <p> Sæt bruger i karantæne: tjek <p> Alle andre indstillinger: ikke markeret|

Lignende politikker:

- Registrer store overførsler af kundedata eller HR-data – Advarsel, når et stort antal filer, der indeholder kundedata eller HR-data, er blevet registreret at blive downloadet af en enkelt bruger inden for en kort tidsperiode.
- Registrer deling af kunde- og HR-data – advarsel, når filer, der indeholder kunde- eller HR-data, deles.
