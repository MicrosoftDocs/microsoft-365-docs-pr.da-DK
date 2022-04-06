---
title: Undersøg ondsindede mails, der blev leveret i Microsoft 365, Find og undersøg ondsindede mails
keywords: TIMailData-Inline, Sikkerhedshændelse, Hændelse, Microsoft Defender for Endpoint PowerShell, mailmalware, kompromitterede brugere, mailphish, mailmalware, læs brevhoveder i mails, læs brevhoveder, åbne brevhoveder, særlige handlinger
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 12/16/2020
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 8f54cd33-4af7-4d1b-b800-68f8818e5b2a
ms.collection:
- M365-security-compliance
description: Få mere at vide om, hvordan du bruger trusselsundersøgelse og svarmuligheder til at finde og undersøge ondsindede mails.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 48deec7763981b10daf1d0c16cbef95d0e2dbaeb
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476527"
---
# <a name="investigate-malicious-email-that-was-delivered-in-microsoft-365"></a>Undersøg ondsindede mails, der blev leveret i Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for:**

- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Microsoft Defender for Office 365 gør](defender-for-office-365.md) det muligt for dig at undersøge aktiviteter, der sætter personer i din organisation i fare, og at handle for at beskytte din organisation. Hvis du f.eks. er en del af organisationens sikkerhedsteam, kan du finde og undersøge mistænkelige mails, der blev leveret. Det kan du gøre ved [hjælp af Threat Explorer (eller registreringer i realtid).](threat-explorer.md)

> [!NOTE]
> Gå til afhjælpningsartikel [her](remediate-malicious-email-delivered-office-365.md).

## <a name="before-you-begin"></a>Før du begynder

Sørg for, at følgende krav er opfyldt:

- Din organisation har [Microsoft Defender for Office 365](defender-for-office-365.md) og [licenser tildeles til brugere](../../admin/manage/assign-licenses-to-users.md).

- [Overvågningslogføring](../../compliance/turn-audit-log-search-on-or-off.md) er aktiveret for organisationen.

- Din organisation har defineret politikker for antispam, antimalware, antiphishing osv. Se [Beskyt mod trusler i Office 365](protect-against-threats.md).

- Du er global administrator, eller du har enten sikkerhedsadministratoren eller rollen Søg og tømning tildelt på Microsoft 365 Defender portal. Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md). For nogle handlinger skal du også have tildelt rollen Eksempel.

### <a name="preview-role-permissions"></a>Forhåndsvisning af rolletilladelser

Hvis du vil udføre visse handlinger, f.eks. visning af brevhoveder eller hentning af mailindhold, skal rollen Eksempel være føjet til en anden relevant rollegruppe. Følgende tabel giver et billede af de påkrævede roller og tilladelser.

|Aktivitet|Rollegruppe|Skal du have en eksempelrolle?|
|---|---|---|
|Brug Trusselsoversigt (og registreringer i realtid) til at analysere trusler|Global Administrator <p> Sikkerhedsadministrator <p> Sikkerhedslæser|Nej|
|Brug Trusselsstifinder (og registreringer i realtid) til at få vist brevhoveder for mails samt forhåndsvisning og download af mails, der er sat i karantæne|Global Administrator <p> Sikkerhedsadministrator <p> Sikkerhedslæser|Nej|
|Brug Threat Explorer til at få vist brevhoveder, gennemse mail (kun på siden mailenhed) og hente mails, der leveres til postkasser|Global Administrator <p> Sikkerhedsadministrator <p> Sikkerhedslæser <p> Eksempel|Ja|

> [!NOTE]
> **Eksempel** er en rolle og ikke en rollegruppe. Eksempelrollen skal føjes til en eksisterende rollegruppe eller en ny rollegruppe i Microsoft 365 Defender portalen. Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).
>
> Rollen Global administrator tildeles rollen som Microsoft 365 Administration på <https://admin.microsoft.com>. Sikkerhedsadministrator- og sikkerhedslæserrollerne tildeles i Microsoft 365 Defender portal.

Vi forstår, at eksempelvisning og hentning af mail er følsomme aktiviteter, så overvågning er aktiveret for disse aktiviteter. Når en administrator udfører disse aktiviteter for mail, genereres der overvågningslogfiler for det samme og kan ses i Microsoft 365 Defender-portalen <https://security.microsoft.com>  \> på fanen Overvågningssøgning og filtrere efter administratornavnet i **feltet** Brugere. De filtrerede resultater viser **aktivitetsadministratorenMailAccess**. Vælg en række for at få vist detaljer **i afsnittet Flere** oplysninger om forhåndsvist eller hentet mail.

## <a name="find-suspicious-email-that-was-delivered"></a>Find mistænkelige mails, der blev leveret

Threat Explorer er en effektiv rapport, der kan tjene flere formål, f.eks. finde og slette meddelelser, identificere IP-adressen på en ondsindet mailafsender eller starte en hændelse til yderligere undersøgelse. Følgende procedure fokuserer på at bruge Stifinder til at finde og slette skadelige mails fra modtagerens postkasser.

> [!NOTE]
> Standardsøgninger i Stifinder inkluderer i øjeblikket ikke leveret elementer, der blev fjernet fra skyens postkasse efter nul-timers automatisk tømning (ZAP). Denne begrænsning gælder for alle visninger (f.eks. **mailmalware \>** eller **phish-visninger\>**). Hvis du vil medtage elementer, der er blevet fjernet af ZAP, skal du tilføje en **Leveringshandling, der** er **indstillet til at omfatte Fjernet af ZAP**. Hvis du medtager alle indstillinger, får du vist alle resultater af leveringshandlingen, herunder elementer, der fjernes af ZAP.

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **Mail & Samarbejdsstifinder** \> . For at gå direkte til **Stifinder-siden** skal du bruge <https://security.microsoft.com/threatexplorer>.

   På siden **Stifinder** viser **kolonnen Yderligere handlinger** administratorresultatet for behandling af en mail. Kolonnen **Yderligere handlinger** kan tilgås på samme sted som **Leveringshandling** og **Leveringsplacering**. Særlige handlinger kan blive opdateret i slutningen af Threat Explorers mailtidslinje, som er en ny funktion, der er beregnet til at gøre jagtoplevelsen bedre for administratorer.

2. I menuen **Vis** skal du **vælge Mail** \> **alle** mails på rullelisten.

    :::image type="content" source="../../media/tp-InvestigateMalEmail-viewmenu.png" alt-text="Rullelisten malware" lightbox="../../media/tp-InvestigateMalEmail-viewmenu.png":::

    *Malwarevisningen* er i øjeblikket standardvisningen og registrerer mails, hvor der er registreret en malwaretrussel. *Phish-visningen* fungerer på samme måde for Phish.

    Alle *mailvisningen viser* dog alle mails, der er modtaget af organisationen, uanset om der blev registreret trusler eller ej. Som du kan forestille dig, er dette en masse data, hvilket er grunden til, at denne visning viser en pladsholder, der beder om at få anvendt et filter. (Denne visning er kun tilgængelig for Defender for Office 365 P2-kunder).

    *Visningen Indsendelser* viser alle de mails, der er sendt af en administrator eller bruger, og som er blevet rapporteret til Microsoft.

4. **Søg og filtrer i Threat Explorer**: Filtre vises øverst på siden i søgefeltet for at hjælpe administratorer i deres undersøgelser. Bemærk, at der kan anvendes flere filtre på samme tid, og at flere kommaseparerede værdier føjes til et filter for at indsnævre søgningen. Husk:

    - Filtre matcher nøjagtigt under de fleste filterbetingelser.
    - Emnefilter anvender en CONTAINS-forespørgsel.
    - URL-filtre fungerer med eller uden protokoller (f.eks. https).
    - URL-domæne, URL-sti og URL-domæne og stifiltre kræver ikke en protokol for at filtrere.
    - Du skal klikke på ikonet Opdater, hver gang du ændrer filterværdierne for at få relevante resultater.

5. **Avancerede filtre**: Med disse filtre kan du opbygge komplekse forespørgsler og filtrere dit datasæt. Når du klikker på *Avancerede filtre* , åbnes en pop op-vindue med indstillinger.

   Avanceret filtrering er en god tilføjelse til søgefunktionerne. En boolesk værdi IKKE på **filtrene modtager****-,** **afsender-** og afsenderdomæne giver administratorer mulighed for at undersøge ved at ekskludere værdier. Denne indstilling er Lig **med intet valg** . Denne indstilling giver administratorer mulighed for at udelukke uønskede postkasser fra undersøgelser (f.eks. postkasser til beskeder og standardpostkasser til svar), og det er nyttigt i tilfælde, hvor administratorer søger efter et bestemt emne (f.eks. Obs), hvor Modtageren kan indstilles til Er lig med ingen af *: defaultMail@contoso.com*. Dette er en nøjagtig værdisøgning.

   :::image type="content" source="../../media/tp-InvestigateMalEmail-AdvancedFilter.png" alt-text="Ruden Modtagere" lightbox="../../media/tp-InvestigateMalEmail-AdvancedFilter.png":::

   Hvis du føjer et tidsfilter til startdatoen og slutdatoen, hjælper det dit sikkerhedsteam med hurtigt at analysere ned. Den korteste tilladte tid varer 30 minutter. Hvis du kan indsnævre den mistænkelige handling efter tidsramme (f.eks. det skete for 3 timer siden), begrænser dette konteksten og hjælper med at identificere problemet.

   :::image type="content" source="../../media/tp-InvestigateMalEmail-FilterbyHours.png" alt-text="Indstillingen for filtrering efter timer" lightbox="../../media/tp-InvestigateMalEmail-FilterbyHours.png":::

6. **Felter i Threat Explorer**: Trusselsstifinder indeholder mange flere sikkerhedsrelaterede mailoplysninger som f.eks. *Leveringshandling, Leveringsplacering**, Særlig* *handling,* Retningalitet *, Tilsidesættelser* og *URL-trussel*. Det giver også organisationens sikkerhedsteam mulighed for at undersøge noget højere oppe.

    *Leveringshandling* er den handling, der er foretaget på en mail på grund af eksisterende politikker eller registreringer. Her er de mulige handlinger, en mail kan udføre:

    - **Leveret** – mail blev leveret til en brugers indbakke eller mappe, og brugeren kan få direkte adgang til den.
    - **Uønsket** (Leveret til uønsket)– Mail blev sendt til enten brugerens mappe med uønsket post eller en slettet mappe, og brugeren har adgang til mails i mappen Uønsket mail eller Slettet.
    - **Blokeret** – alle mails, der er sat i karantæne, som mislykkedes eller er blevet tabt.
    - **Erstattet – alle** mails, hvor ondsindede vedhæftede filer erstattes af filer.txt der viser, at den vedhæftede fil var skadelig

    **Leveringssted**: Filteret Leveringsplacering er tilgængeligt for at hjælpe administratorer med at forstå, hvor der er mistanke om ondsindet mail, og hvilke handlinger der er blevet foretaget på den. De resulterende data kan eksporteres til regneark. Mulige leveringsplaceringer er:

    - **Indbakke eller mappe** – Mailen ligger i indbakken eller en bestemt mappe i henhold til dine mailregler.
    - **Lokal eller ekstern –** Postkassen findes ikke i skyen, men er lokal.
    - **Mappen Uønsket** – Mailen findes i en brugers mappe med Uønsket mail.
    - **Mappen Slettet post** – Mailen findes i en brugers mappe Slettet post.
    - **Karantæne** – mailen i karantæne og ikke i en brugers postkasse.
    - **Mislykkedes** – Mailen kunne ikke nås til postkassen.
    - **Tabt** – Mailen gik tabt et sted i mailflowet.

    **Retningalitet**: Denne indstilling giver dit sikkerhedsteam mulighed for at filtrere efter den "retning", en mail kommer fra eller er i gang. Directionality-værdier er *Indgående**, Udgående* og *Intra-org* (svarende til mail, der kommer ind i din organisation udefra, sendes ud af din organisation eller sendes internt til din organisation). Disse oplysninger kan hjælpe sikkerhedsteams med at spotte spoofing og efterligning, fordi der er en uoverensstemmelse mellem Værdien Retningalitet (f.eks. *Indgående*) og afsenderens domæne (som ser *ud til* at være et internt domæne) vil være tydeligt! Værdien Retningalitet er separat og kan afvige fra Meddelelsessporing. Resultaterne kan eksporteres til regneark.

    **Tilsidesættelser**: Dette filter tager oplysninger, der vises på fanen med mailoplysninger, og bruger det til at vise, hvor organisatoriske eller brugerpolitikker, der bruges til at tillade og blokere mails, er blevet *tilsidesat*. Det vigtigste ved dette filter er, at det hjælper organisationens sikkerhedsteam med at se, hvor mange mistænkelige mails, der blev leveret på grund af konfigurationen. Dette giver dem mulighed for at redigere tillader og blokerer efter behov. Dette resultatsæt af dette filter kan eksporteres til regneark.

    |Tilsidesættelser af Threat Explorer|Hvad de betyder|
    |---|---|
    |Tilladt af organisationspolitik|Mail blev tilladt i postkassen, som angivet af organisationens politik.|
    |Politik for blokeret af organisation|Mail blev blokeret fra levering til postkassen, som angivet af organisationens politik.|
    |Filtypenavn, der er blokeret af Org-politik|Filen blev blokeret fra levering til postkassen, som angivet af organisationens politik.|
    |Tilladt af brugerpolitik|Mail blev tilladt i postkassen, som angivet af brugerpolitikken.|
    |Blokeret af brugerpolitik|Mail blev blokeret fra levering til postkassen, som angivet af brugerpolitikken.|

    **URL-trussel**: Url-trusselsfeltet er blevet medtaget på detaljefanen i en mail for at angive den trussel, der blev præsenteret af en URL-adresse. Trusler, der præsenteres af en URL-adresse, kan omfatte *Malware*, *Phish* eller *Spam*, og  en URL-adresse uden trusler vil *sige Ingen i* afsnittet om trusler.

7. **Visning af tidslinje i** mails: Sikkerhedsteamet skal muligvis dykke ned i maildetaljerne for at undersøge yderligere. Mailtidslinjen giver administratorer mulighed for at få vist handlinger, der er foretaget på en mail, fra levering til efter levering. Hvis du vil have vist en mailtidslinje, skal du klikke på emnet for en mail og derefter klikke på Send tidslinje via mail. (Den vises blandt andre overskrifter i panelet, f.eks. Oversigt eller Detaljer). Disse resultater kan eksporteres til regneark.

    Mailtidslinje åbnes i en tabel, der viser alle leverings- og efterleveringshændelser for mailen. Hvis der ikke er yderligere handlinger på mailen, bør du se en enkelt hændelse for den oprindelige levering, der viser et resultat, f.eks Blokeret *, med* en konklusion som *Phish*. Administratorer kan eksportere hele mailtidslinjen, herunder alle oplysninger på fanen og mail (f.eks. Emne, Afsender, Modtager, Netværk og Meddelelses-id). Mailtidslinjen bliver mindre tilfældigt, fordi der bruges mindre tid på at kontrollere forskellige placeringer for at forsøge at forstå, hvad der skete, da mailen blev modtaget. Når flere begivenheder sker på eller tæt på, på samme tid i en mail, vises disse begivenheder i en tidslinjevisning.

8. **Forhåndsvisning/download**: Threat Explorer giver dit sikkerhedsteam de oplysninger, de skal bruge for at undersøge mistænkelige mails. Dit sikkerhedsteam kan enten:

    - [Kontrollér leveringshandlingen og placeringen](#check-the-delivery-action-and-location).

    - [Få vist tidslinjen for din mail](#view-the-timeline-of-your-email).

### <a name="check-the-delivery-action-and-location"></a>Kontrollér leveringshandlingen og -placeringen

I [Threat Explorer (og registreringer i realtid) har du nu kolonnerne Leveringshandling og Leveringsplacering](threat-explorer.md) i stedet for den tidligere **kolonne Leveringsstatus**.  Dette giver et mere komplet billede af, hvor dine mails lander. En del af målet med denne ændring er at gøre det nemmere for sikkerhedsteams at undersøge, men nettoresultatet er at have et hurtigt overblik over placeringen af problemmails.

Leveringsstatus er nu opdelt i to kolonner:

- **Leveringshandling** – Hvad er status for denne mail?
- **Leveringssted** – Hvor blev denne mail distribueret som et resultat?

Leveringshandling er den handling, der er foretaget på en mail på grund af eksisterende politikker eller registreringer. Her er de mulige handlinger, en mail kan udføre:

- **Leveret** – mail blev leveret til en brugers indbakke eller mappe, og brugeren kan få direkte adgang til den.
- **Uønsket** – Mail blev sendt til enten brugerens mappe med uønsket post eller en slettet mappe, og brugeren har adgang til mails i mappen Uønsket mail eller Slettet.
- **Blokeret** – alle mails, der er sat i karantæne, som mislykkedes eller er blevet tabt.
- **Erstattet – alle** mails, hvor skadelige vedhæftede filer erstattes af .txt, der viser, at den vedhæftede fil var skadelig.

Leveringssted viser resultaterne af politikker og registreringer, der kører efter levering. Det er knyttet til en Leveringshandling. Dette felt blev tilføjet for at give indsigt i den handling, der blev taget, når der blev fundet en problemmail. Her er de mulige værdier for leveringssted:

- **Indbakke eller mappe** – Mailen findes i indbakken eller i en mappe (i henhold til dine mailregler).
- **Lokal eller ekstern –** Postkassen findes ikke i skyen, men er lokal.
- **Mappen Uønsket** – Mailen findes i en brugers mappe med Uønsket mail.
- **Mappen Slettet post** – Mailen findes i en brugers mappe Slettet post.
- **Karantæne** – mailen i karantæne og ikke i en brugers postkasse.
- **Mislykkedes** – Mailen kunne ikke nås til postkassen.
- **Tabt** – Mailen går tabt et sted i mailflowet.

### <a name="view-the-timeline-of-your-email"></a>Få vist tidslinjen for din mail

**Mailtidslinje** er et felt i Threat Explorer, der gør det nemmere for dit sikkerhedsteam at lede. Når flere begivenheder sker på eller tæt på samme tid på en mail, vises disse begivenheder i en tidslinjevisning. Nogle hændelser, der sker efter levering af mail, registreres i **kolonnen Særlige** handlinger. Hvis du kombinerer oplysninger fra tidslinjen for en mail med særlige handlinger, der er foretaget efter levering, får administratorerne indsigt i politikker og trusselshåndtering (f.eks. hvor mailen blev distribueret, og i nogle tilfælde hvad den endelige vurdering var).

> [!IMPORTANT]
> Gå til et afhjælpningsemne [her](remediate-malicious-email-delivered-office-365.md).

## <a name="related-topics"></a>Relaterede emner

[Afhjælpe skadelig mail leveret i Office 365](remediate-malicious-email-delivered-office-365.md)

[Microsoft Defender for Office 365](office-365-ti.md)

[Beskyt dig mod trusler i Office 365](protect-against-threats.md)

[Få vist rapporter for Defender for Office 365](view-reports-for-mdo.md)
