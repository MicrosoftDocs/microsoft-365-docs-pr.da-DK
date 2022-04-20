---
title: Overvåg for lækager af personlige data
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
ms.openlocfilehash: 3b16e96e85d6ee154912535ecf0bac4ac5ba6fac
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947753"
---
# <a name="monitor-for-leaks-of-personal-data"></a>Overvåg for lækager af personlige data

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Der er mange værktøjer, der kan bruges til at overvåge brugen og transporten af personlige data. I dette emne beskrives tre værktøjer, der fungerer godt.

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image1.png" alt-text="Værktøjerne til at overvåge brugen og transporten af personoplysninger" lightbox="../../media/Monitor-for-leaks-of-personal-data-image1.png":::

I illustrationen:

- Start med Microsoft Purview-rapporter om forebyggelse af datatab for at overvåge personlige data i SharePoint Online, OneDrive for Business og mail under overførsel. Disse rapporter giver den største detaljeniveau til overvågning af personlige data. Disse rapporter omfatter dog ikke alle tjenester i Office 365.

- Derefter skal du bruge politikker for beskeder og overvågningsloggen til at overvåge aktiviteter på tværs af tjenester. Konfigurer løbende overvågning, eller søg i overvågningsloggen for at undersøge en hændelse. Overvågningsloggen fungerer på tværs af tjenester – Sway, Power BI, eDiscovery, Dynamics 365, Power Automate, Microsoft Teams, administratoraktivitet, OneDrive for Business, SharePoint Online, mail under overførsel og inaktive postkasser. Skype samtaler er inkluderet i inaktive postkasser.

- Til sidst skal du bruge Microsoft Defender for Cloud Apps til at overvåge filer med følsomme data i andre SaaS-providere. Kommer snart er muligheden for at bruge følsomme oplysningstyper og samlede mærkater på tværs af Azure Information Protection og Office med Defender for Cloud Apps. Du kan konfigurere politikker, der gælder for alle dine SaaS-apps eller specifikke apps (f.eks. Box). Defender for Cloud Apps registrerer ikke filer i Exchange Online, herunder filer, der er knyttet til mail.

## <a name="data-loss-prevention-reports"></a>Rapporter om forebyggelse af datatab

Når du har oprettet dine DLP-politikker (forebyggelse af datatab), skal du bekræfte, at de fungerer, som du havde tænkt dig, og hjælpe dig med at overholde angivne standarder. Med DLP-rapporterne i Office 365 kan du hurtigt få vist antallet af DLP-politikforekomster, -tilsidesættelser eller falske positiver. Se, om de har tendens til at falde op eller ned over tid. Filtrer rapporten på forskellige måder, og få vist flere oplysninger ved at vælge et punkt på en linje i grafen.

Du kan bruge DLP-rapporterne til at:

- Fokuser på specifikke tidsperioder, og forstå årsagerne til stigninger og tendenser.
- Find forretningsprocesser, der overtræder organisationens DLP-politikker.
- Forstå alle forretningsmæssige konsekvenser af DLP-politikkerne.
- Få vist de begrundelser, som brugerne har indsendt, når de løser et politiktip, ved at tilsidesætte politikken eller rapportere en falsk positiv.
- Kontrollér overholdelse af en bestemt DLP-politik ved at vise eventuelle match for den pågældende politik.
- Få vist en liste over filer med følsomme data, der svarer til dine DLP-politikker, i detaljeruden.

Derudover kan du bruge DLP-rapporter til at finjustere dine DLP-politikker, når du kører dem i testtilstand.

DLP-rapporter findes på Microsoft Purview-overholdelsesportalen. Gå til afsnittet **Rapporter** \> **Organisationsdata** for at finde **DLP-politikforekomster**, **DLP-hændelser** og **falske DLP-positiver og tilsidesættelser af** rapporter.

Du kan få flere oplysninger under [Få vist rapporter til forebyggelse af datatab](../../compliance/view-the-dlp-reports.md).

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image2.png" alt-text="Den rapport, der viser DLP-politikforekomster" lightbox="../../media/Monitor-for-leaks-of-personal-data-image2.png":::

## <a name="audit-log-and-alert-policies"></a>Politikker for overvågningslog og beskeder

Overvågningsloggen indeholder hændelser fra Exchange Online, SharePoint Online, OneDrive for Business, Azure Active Directory, Microsoft Teams, Power BI, Sway og andre tjenester.

Portalen Microsoft 365 Defender og Microsoft Purview-overholdelsesportalen indeholder to måder at overvåge og rapportere i forhold til overvågningsloggen:

- Konfigurer politikker for beskeder, få vist beskeder og overvåg tendenser – Brug værktøjerne til beskedpolitik og dashboard til beskeder enten på portalen Microsoft 365 Defender eller i Microsoft Purview-overholdelsesportalen.
- Søg direkte i overvågningsloggen: Søg efter alle hændelser i et angivet dato-raseri. Du kan også filtrere resultaterne på baggrund af bestemte kriterier, f.eks. den bruger, der udførte handlingen, handlingen eller destinationsobjektet.

Teams for overholdelse af angivne standarder for oplysninger og sikkerhedsteams kan bruge disse værktøjer til proaktivt at gennemse aktiviteter, der udføres af både slutbrugere og administratorer på tværs af tjenester. Automatiske beskeder kan konfigureres til at sende mailmeddelelser, når visse aktiviteter finder sted i bestemte grupper af websteder – f.eks. når indhold deles fra websteder, der er kendt for at indeholde GDPR-relaterede oplysninger. Dette giver disse teams mulighed for at følge op på brugerne for at sikre, at virksomhedens sikkerhedspolitikker følges, eller for at tilbyde yderligere oplæring.

Informationssikkerhedsteams kan også søge i overvågningsloggen for at undersøge formodede brud på datasikkerheden og fastslå både hovedårsagen og omfanget af sikkerhedsbrudet. Denne indbyggede funktionalitet gør det lettere at overholde artikel 33 og 34 i GDPR, som kræver, at gdpr-tilsynsmyndigheden og de registrerede selv får besked om et databrud inden for en bestemt tidsperiode. Overvågningslogposter opbevares kun i 90 dage i tjenesten – det anbefales ofte, og mange organisationer har krævet, at disse logge opbevares i længere tid.

Der findes løsninger, der abonnerer på Unified Audit Logs via Microsoft Management Activity API, og som både kan gemme logposter efter behov og levere avancerede dashboards og beskeder. Et eksempel er [OMS (Microsoft Operations Management Suite).](/azure/operations-management-suite/oms-solution-office-365)

Flere oplysninger om politikker for beskeder og søgning i overvågningsloggen:

- [Beskedpolitikker i Microsoft 365](../../compliance/alert-policies.md)
- [Søg i overvågningsloggen efter bruger- og administratoraktivitet i Office 365](../../compliance/search-the-audit-log-in-security-and-compliance.md) (introduktion)
- [Slå søgning i overvågningslog til eller fra](../../compliance/turn-audit-log-search-on-or-off.md)
- [Søgning i overvågningsloggen](../../compliance/search-the-audit-log-in-security-and-compliance.md)
- [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) (cmdlet)
- [Detaljerede egenskaber i overvågningsloggen](../../compliance/detailed-properties-in-the-office-365-audit-log.md)

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

Microsoft Defender for Cloud Apps hjælper dig med at finde andre SaaS-apps, der er i brug på tværs af dine netværk, og følsomme data, der sendes til og fra disse apps.

Microsoft Defender for Cloud Apps er en omfattende tjeneste, der giver dyb synlighed, detaljerede kontrolelementer og forbedret trusselsbeskyttelse af dine cloudapps. Den identificerer mere end 15.000 cloudprogrammer i dit netværk fra alle enheder og giver risikoscore og løbende risikovurdering og analyse. Der kræves ingen agenter: Der indsamles oplysninger fra dine firewalls og proxyer for at give dig fuldstændig synlighed og kontekst for cloudbrug og skygge-it.

Funktionen Til undersøgelse af Defender for Cloud Apps giver en bedre forståelse af dit cloudmiljø og giver dyb indsigt i alle aktiviteter, filer og konti for sanktionerede og administrerede apps. Du kan få detaljerede oplysninger om et filniveau og finde ud af, hvor data bevæger sig i cloudapps.

Følgende illustration viser f.eks. to Defender for Cloud Apps-politikker, der kan hjælpe med GDPR.

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image3.png" alt-text="Defender for Cloud Apps-politikker" lightbox="../../media/Monitor-for-leaks-of-personal-data-image3.png":::

Den første politik giver besked, når filer med en foruddefineret PII-attribut eller et brugerdefineret udtryk, som du vælger, deles uden for organisationen fra de SaaS-apps, du vælger.

Den anden politik blokerer downloads af filer til enhver ikke-administreret enhed. Du vælger de attributter i filerne, der skal søges efter, og de SaaS-apps, som politikken skal gælde for.

Disse attributtyper kommer snart til Defender for Cloud Apps:

- Typer af følsomme oplysninger
- Samlede mærkater på tværs af Microsoft 365 og Azure Information Protection

### <a name="defender-for-cloud-apps-dashboard"></a>Defender for Cloud Apps-dashboard

Hvis du endnu ikke er begyndt at bruge Defender for Cloud Apps, skal du starte med at starte det. Sådan får du adgang til Defender for Cloud Apps: <https://portal.cloudappsecurity.com>.

> [!NOTE]
> Sørg for at aktivere "Scan automatisk filer til Azure Information Protection klassificeringsmærkater" (i Generelle indstillinger), når du går i gang med Defender for Cloud Apps, eller før du tildeler mærkater. Efter installationen scanner Defender for Cloud Apps ikke eksisterende filer igen, før de er ændret.

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image4.png" alt-text="Dashboardet, der viser oplysninger om beskeder" lightbox="../../media/Monitor-for-leaks-of-personal-data-image4.png":::

Flere oplysninger:

- [Udrul Defender til Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security)
- [Flere oplysninger om Microsoft Defender for Cloud Apps](https://www.microsoft.com/cloud-platform/cloud-app-security)
- [Bloker downloads af følsomme oplysninger ved hjælp af proxyen for Microsoft Defender for Cloud Apps](/cloud-app-security/use-case-proxy-block-session-aad)

## <a name="example-file-and-activity-policies-to-detect-sharing-of-personal-data"></a>Eksempel på fil- og aktivitetspolitikker til registrering af deling af personlige data

### <a name="detect-sharing-of-files-containing-pii--credit-card-number"></a>Registrer deling af filer, der indeholder pii – kreditkortnummer

Besked, når en fil, der indeholder et kreditkortnummer, deles fra en godkendt cloudapp.

|Kontrol|Indstillinger|
|---|---|
|Politiktype|Filpolitik|
|Politikskabelon|Ingen skabelon|
|Politik alvorsgrad|Høj|
|Kategori|DLP|
|Filterindstillinger|Adgangsniveau = Offentligt (Internet), Offentligt, Eksternt <p> App = \<select apps\> (brug denne indstilling, hvis du vil begrænse overvågning til bestemte SaaS-apps)|
|Anvend på|Alle filer, alle ejere|
|Indholdskontrol|Indeholder filer, der svarer til et aktuelt udtryk: Alle lande: Økonomi: Kreditkortnummer <p> Kræv ikke relevant kontekst: ikke markeret (denne indstilling matcher nøgleord samt regex) <p> Medtager filer med mindst 1 match <p> Fjern de sidste fire tegn i fejlen: markeret|
|Beskeder|Opret en besked for hver matchende fil: markeret <p> Grænse for daglig besked: 1000 <p> Vælg en besked som mail: markeret <p> Til: infosec@contoso.com|
|Styring|Microsoft OneDrive for Business <p> Gør privat: Markér Fjern eksterne brugere <p> Alle andre indstillinger: ikke markeret <p> Microsoft Office SharePoint Online <p> Gør privat: Markér Fjern eksterne brugere <p> Alle andre indstillinger: ikke markeret|

Lignende politikker:

- Registrer deling af filer, der indeholder PII – Mailadresse
- Registrer deling af filer, der indeholder pii – Passport-nummer

### <a name="detect-customer-or-hr-data-in-box-or-onedrive-for-business"></a>Registrer kunde- eller HR-data i felt eller OneDrive for Business

Besked, når en fil, der er mærket som Kundedata eller HR-data, uploades til OneDrive for Business eller Box.

Noter:

- Boksovervågning kræver, at der konfigureres en connector ved hjælp af API Connector SDK.
- Denne politik kræver egenskaber, der i øjeblikket er i en privat prøveversion.

|Kontrol|Indstillinger|
|---|---|
|Politiktype|Aktivitetspolitik|
|Politikskabelon|Ingen skabelon|
|Politik alvorsgrad|Høj|
|Kategori|Delingskontrol|
|Opdr.|Enkelt aktivitet|
|Filterindstillinger|Aktivitetstype = Upload fil <p> App = Microsoft OneDrive for Business og Box <p> Klassificeringsmærkat (i øjeblikket i privat prøveversion): Azure Information Protection = Kundedata, HR – Løndata, HR – Medarbejderdata|
|Beskeder|Opret en besked: markeret <p> Grænse for daglig besked: 1000 <p> Vælg en besked som mail: markeret <p> Til: infosec@contoso.com|
|Styring|Alle apps <p> Sæt brugeren i karantæne: check <p> Alle andre indstillinger: ikke markeret <p> Office 365 <p> Sæt brugeren i karantæne: check <p> Alle andre indstillinger: ikke markeret|

Lignende politikker:

- Registrer store downloads af kundedata eller HR-data – Advarsel, når et stort antal filer, der indeholder kundedata eller HR-data, er blevet registreret af en enkelt bruger inden for en kort periode.
- Registrer deling af kunde- og HR-data – vigtig besked, når filer, der indeholder kunde- eller HR-data, deles.
