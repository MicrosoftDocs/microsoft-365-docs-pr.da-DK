---
title: Siden Microsoft Defender for Office 365 mailenhed
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 04/01/2022
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.technology: mdo
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Microsoft Defender for Office 365 E5- og P1- og P2-kunder kan nu få en 360-graders visning af hver mail med en enhedsside for mail.
ms.openlocfilehash: 1b74c4c79d05a4a52434810527c92de801b329f0
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634817"
---
# <a name="the-email-entity-page"></a>Siden Mailenhed

**I denne artikel:**
- [Få adgang til siden mailenhed](#reach-the-email-entity-page)
- [Læs siden med mailobjekt](#read-the-email-entity-page)
- [Brug sidefaner for mailenhed](#use-email-entity-page-tabs)
- [Ny på siden mailenhed](#new-to-the-email-entity-page)

Administratorer af Microsoft Defender for Office 365 E5 og Defender for Office P1 og P2 har en 360-graders visning af mail ved hjælp af siden **Mailenhed**. Denne mailside blev oprettet for at forbedre oplysningerne i pop op-vinduet [med "mailoplysninger" i Threat Explorer](threat-explorer-views.md).

## <a name="reach-the-email-entity-page"></a>Få adgang til siden mailenhed

Siden med mailenhed er tilgængelig i Microsoft 365 Defender på Mailudbyder <https://security.microsoft.com> **& Stifinder**\>. Du kan også gå direkte til **Stifinder-siden** ved hjælp af <https://security.microsoft.com/threatexplorer>.

I **Stifinder** skal du vælge emnet for en mail, du undersøger. En Guldbjælke vises øverst i mailen for den pågældende mail. Denne invitation til den nye side, hvor der står "Prøv vores nye side med e-mail-enheder med forbedrede data...". Vælg for at få vist den nye side.

:::image type="content" source="../../media/email-entities-1-navigation-to-ee.png" alt-text="Det gyldne banner med ordene * Prøv vores nye side med forbedrede data * for at navigere til den nye oplevelse" lightbox="../../media/email-entities-1-navigation-to-ee.png":::

:::image type="content" source="../../media/email-entities-2-eep.png" alt-text="Grafikken på siden mailenhed, der fokuserer på overskrifter, som du får vist" lightbox="../../media/email-entities-2-eep.png":::

> [!NOTE]
> De tilladelser, der kræves for at få vist og bruge denne side, er de samme som for at få vist **Stifinder**. Administratoren skal være medlem af global administrator eller global læser eller sikkerhedsadministrator eller sikkerhedslæser. Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

## <a name="read-the-email-entity-page"></a>Læs siden med mailobjekt

Strukturen er designet til at være nem at læse og navigere hurtigt i. Forskellige faner langs toppen af siden giver dig mulighed for at undersøge mere detaljeret. Sådan fungerer layoutet:

1. De mest påkrævede felter er i venstre side af pop op-siden. Disse detaljer er "sticky", hvilket betyder, at de er forankret til venstre, uanset hvilken fane du navigerer til i resten af pop op-punktet.

    :::image type="content" source="../../media/email-entities-3-left-panel.png" alt-text="Grafikelementsiden for mailobjektet med venstre side fremhævet" lightbox="../../media/email-entities-3-left-panel.png":::

2. I øverste højre hjørne finder du de handlinger, der kan udføre på en mail. Alle handlinger, der kan gøres via **Stifinder** , vil også være tilgængelige via siden mailenhed.

    :::image type="content" source="../../media/email-entities-5-preview.png" alt-text="Grafikelementsiden for mailobjektet med højre side fremhævet" lightbox="../../media/email-entities-5-preview.png":::

3. En dybere analyse kan foretages ved at sortere resten af siden. Kontrollér detaljerne for registrering af mail, status for mailgodkendelse og sidehoved. Dette område skal kigges fra gang til gang, men oplysningerne i disse faner er tilgængelige for alle mails.

    :::image type="content" source="../../media/email-entities-4-middle-panel.png" alt-text="Hovedpanelet på siden, som indeholder mailens sidehoved og godkendelsesstatus" lightbox="../../media/email-entities-4-middle-panel.png":::

### <a name="use-email-entity-page-tabs"></a>Brug sidefaner for mailenhed

Fanerne langs toppen af enhedssiden giver dig mulighed for at undersøge mails effektivt.

1. **Tidslinje**: Tidslinjevisningen for en mail **(pr.** Stifinder-tidslinje) viser den oprindelige levering til de hændelser efter levering, der sker på en mail. For mails, der ikke har nogen handlinger efter levering, viser visningen den oprindelige leveringsrække i tidslinjevisningen. Hændelser som f.eks.: Automatisk tømning (OAT) uden time, afhjælpning, klik på WEBADRESSE osv. fra kilder som f.eks.: system, administrator og bruger, vises her i den rækkefølge, de opstod i.
2. **Analyse**: Analyse viser felter, der hjælper administratorer med at analysere en mail i dybden. I tilfælde hvor administratorer har brug for at forstå mere om registrering, afsender/modtager og oplysninger om mailgodkendelse, skal de bruge fanen Analyse. Links til vedhæftede filer og URL-adresser findes også på denne side under "Relaterede enheder". Både vedhæftede filer og identificerede trusler nummereret her, og hvis du klikker, kommer du direkte til siderne Vedhæftede filer og URL-adresser. Denne fane har også indstillingen Vis brevhoved til at *vise mailens brevhoved*. Administratorer kan sammenligne alle detaljer fra brevhoveder i mails side om side med oplysninger på hovedpanelet for at gøre dem tydeligere.
3. **Vedhæftede** filer: Dette undersøger vedhæftede filer, der findes i mailen, med andre oplysninger, der findes på vedhæftede filer. Antallet af viste vedhæftede filer er i øjeblikket begrænset til 10. Bemærk, at oplysninger om detonation for vedhæftede filer, der findes skadelige, også vises her.
4. **URL-adresser**: Under denne fane vises URL-adresser, der findes i mailen, med andre oplysninger om URL-adresserne. Antallet af URL-adresser er begrænset til 10 lige nu, men disse 10 er prioriteret for at vise ondsindede *URL-adresser først*. Prioritering sparer dig tid og gæt-arbejde. De URL-adresser, der blev fundet skadelige og deonerede, vises også her.
5. **Ens mails**: Denne fane viser alle mails, der ligner *netværksmeddelelses-id'et + modtagerkombination* specifikt for denne mail. Lighed er kun baseret *på meddelelsens brødtekst*. Bestemmelseerne på mails om at kategorisere dem som "lignende" omfatter ikke overvejelser om *vedhæftede filer*.

## <a name="new-to-the-email-entity-page"></a>Ny på siden mailenhed

Der er nye funktioner, der kommer med denne mailenhedsside. Her er listen.

### <a name="email-preview-for-cloud-mailboxes"></a>Maileksempel for skybaserede postkasser

Administratorer kan få vist mails i skybaserede postkasser, ***hvis*** mails stadig er til stede i skyen. I tilfælde af blød sletning (af en administrator eller bruger) eller ZAP (til karantæne) findes mails ikke længere på skyplaceringen. Hvis det er tilfældet, kan administratorer ikke få vist disse specifikke mails. Mails, der er blevet tabt, eller hvor leveringen mislykkedes, blev aldrig leveret i postkassen. Derfor kan administratorer heller ikke få vist disse mails.

> [!WARNING]
> Eksempelvisning af mails kræver en særlig rolle kaldet **Forhåndsvisning**. Du kan tilføje denne rolle i Microsoft 365 Defender portalen som beskrevet i [& med mailsamarbejde på Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md#email--collaboration-roles-in-the-microsoft-365-defender-portal). Det kan være nødvendigt at oprette en ny rollegruppe **for mail &** samarbejde og føje rollen Eksempel til  den nye rollegruppe eller føje eksempelrollen til  en rollegruppe, der giver administratorer i organisationen mulighed for at arbejde i **Stifinder**.

### <a name="detonation-details"></a>Oplysninger om detonation

Disse detaljer er specifikke for vedhæftede filer og URL-adresser. Brugerne kan se disse detaljer ved at gå til Stifinder og  anvende det teknologifilter, der er indstillet til fildeonation eller URL-detonation. Mails, der filtreres efter fildeonation, indeholder en skadelig fil med detonationsoplysninger, og de, der filtreres efter URL-adresser, indeholder en ondsindet URL-adresse og oplysninger om detonationen.

Brugerne får vist forbedrede detonationsoplysninger om kendte skadelige vedhæftede filer eller URL-adresser, der findes i deres mails, som blev detoneret for deres specifikke lejer. Den indeholder Detonation-kæden, Detonation-oversigten, skærmbilledet og observerede detaljer om funktionsmåden for at hjælpe kunderne med at forstå, hvorfor den vedhæftede fil eller URL-adressen anses for at være skadelig og detoneret.

1. *Detonation-kæde*. En enkelt fil eller URL-detonation kan udløse flere detonationer. Detonation-kæden registrerer stien til detonationer, herunder den oprindelige skadelige fil eller URL-adresse, der forårsagede konklusionen, og alle andre filer eller URL-adresser, der er påvirket af detonationen. Disse URL-adresser eller vedhæftede filer er muligvis ikke direkte til stede i mailen, men herunder denne analyse er vigtig for at afgøre, hvorfor filen eller URL-adressen blev fundet skadelig.  

    > [!NOTE]
    > Dette kan kun vise elementet på øverste niveau, hvis ingen af de enheder, der er knyttet til elementet, blev fundet problematisk eller blev detoneret.

1. *Detonation-oversigten* giver en grundlæggende oversigt over detonationen *,* f.eks. analysetid, det tidspunkt, hvor detonationen indtraf, operativsystem og program, hvori detonationen opstod, filstørrelse og begrundelse for vurdering.
1. *Skærmbilleder* viser de skærmbilleder, der blev taget under denonationen. Der kan være flere skærmbilleder under detonation. Der registreres ingen skærmbilleder for
    - Objektbeholdertype filer som .zip eller .rar.
    - Hvis der åbnes en URL-adresse i et link, der henter en fil direkte. Du kan dog se den downloadede fil i detonation-kæden.
1.  Funktionsmådedetaljer er en eksport, der viser detaljer om funktionsmåden, f.eks. nøjagtige hændelser, der fandt sted under detonationen, og observerede, der indeholder URL-adresser, IP'er, domæner og filer, der blev fundet under detonationen (og kan enten være problematiske eller bengalske). Vær opmærksom på, at der ikke er nogen detaljer om funktionsmåden:
    - Objektbeholderfiler som .zip eller .rar, der indeholder andre filer.

:::image type="content" source="../../media/email-entities-6-detonation-page.png" alt-text="Detonationsoversigten, der viser kæden, oversigten, deonationsdetaljerne og skærmbilledet under overskriften *Deep Analysis*" lightbox="../../media/email-entities-6-detonation-page.png":::

### <a name="other-innovations"></a>Andre innovationer

*Mærker*: Disse er tags, der anvendes på brugere. Hvis brugeren er modtager, kan administratorer se et *modtagermærke* . På samme måde skal du, hvis brugeren er afsender, mærke *en afsender* . Dette vises i venstre side af siden mailobjekter (i den del, der er beskrevet som *sticky* og dermed forankret til siden).

*Seneste leveringssted*: Den seneste leveringssted er den placering, hvor en mail landede efter systemhandlinger som F.eks. ZAP eller administratorhandlinger som f.eks. Flyt til Slettet post, afslut. Den seneste leveringsplacering er ikke beregnet til at informere administratorerne om meddelelsens *aktuelle* placering. Hvis en bruger f.eks. sletter en meddelelse eller flytter den til arkiv, opdateres leveringsplaceringen ikke. Men hvis en systemhandling har fundet sted og opdateret placeringen (f.eks. en ZAP, der medfører, at en mail flyttes til karantæne), vil dette opdatere den seneste leveringsplacering til karantæne.

*Mailoplysninger*: Detaljer, der kræves for at få en dybere forståelse af de mails, der er tilgængelige *under fanen* Analyse.

- *Exchange transportregler (også kaldet regler for mailflow eller ETR'er)*: Disse regler anvendes på en meddelelse i transportlaget og tilsidesætter phish- og spamprioriteter. Regler for mailflow oprettes og ændres i Exchange Administration <https://admin.exchange.microsoft.com/#/transportrules>på , men hvis en regel for mailflow gælder for en meddelelse, vises regelnavnet og GUID her. Værdifulde oplysninger til sporingsformål.

- *Systemtilsidesættelser*: Dette er en måde at gøre undtagelser til den leveringsplacering, der er beregnet til en meddelelse, ved at tilsidesætte leveringsplaceringen, der er givet af systemet (i henhold til teknologien for trussel og registrering).

- *Masseklageniveau (BCL)*: Meddelelsens mange klageniveau. En højere BCL indikerer, at en massemailmeddelelse er mere tilbøjelig til at generere klager (det naturlige resultat, hvis mailen sandsynligvis er spam).

- *SCL (Spam Confidence Level)*: Meddelelsens tillidsniveau til spam. En højere værdi angiver, at meddelelsen er mere tilbøjelig til at være spam.

- *Klienttype*: Angiver den klienttype, hvorfra mailen blev sendt som REST.

- *Videresendelse*: For scenarier med autoforwaridng angiver den videresendelsesbrugeren samt videresendelsestypen som f.eks. ETR eller SMTP-videresendelse. 

- *Distributionsliste*: Viser distributionslisten, hvis modtageren har gemt mailen igen som medlem af listen. Den viser distributionslisten på øverste niveau, hvis der er indlejrede distributionslister involveret.  

- *Til, Cc*: Angiver de adresser, der er angivet i felterne Til, Cc i en mail. Oplysningerne i disse felter er begrænset til 5000 tegn. 

- *Domænenavn*: Er afsenderens domænenavn.

- *Domæneejer*: Angiver ejeren af det afsendende domæne.

- *Domæneplacering*: Angiver placeringen af det afsendende domæne.

- *Domæne oprettet dato*: Angiver datoen for oprettelse af det afsendende domæne. Et nyligt oprettet domæne er noget, du kan være forsigtig med, hvis andre signaler indikerer en mistænkelig funktionsmåde.

*Mailgodkendelse*: Mailgodkendelsesmetoder, der bruges af Microsoft 365 omfatter SPF, DKIM og DMARC.

- **SPF** (Sender Policy Framework): Beskriver resultaterne for SPF-kontrol af meddelelsen. Mulige værdier kan være:
  - Pass (IP-adresse): SPF-tjek for den meddelelse, der er blevet videregivet, og indeholder afsenderens IP-adresse. Klienten er autoriseret til at sende eller videresende mail på vegne af afsenderens domæne.
  - Mislykkedes (IP-adresse): SPF-tjek for meddelelsen mislykkedes og indeholder afsenderens IP-adresse. Dette kaldes nogle gange for "hard fail".
  - Softfail (årsag): SPF-posten har udpeget værten som ikke må sende, men er i overgangsfasen.
  - Neutral: SPF-posten angiver udtrykkeligt, at den ikke hævder, om IP-adressen er autoriseret til at sende.
  - Ingen: Domænet har ikke en SPF-post, eller SPF-posten evalueres ikke til et resultat.
  - Midlertidig fejl: Der opstod en midlertidig fejl. Eksempelvis en DNS-fejl. Det samme tjek senere kan lykkes.
  - Permerror: Der opstod en permanent fejl. Domænet har f.eks. en forudformateret SPF-post.

- DomainKeys Identified Mail (**DKIM**):
  - Bestået: Angiver DKIM-tjek for den overførte meddelelse.
  - Mislykket (årsag): Angiver DKIM-tjek for meddelelsen mislykkedes og hvorfor. Hvis f.eks. meddelelsen ikke er signeret, eller signaturen ikke er blevet bekræftet.
  - Ingen: Angiver, at meddelelsen ikke er signeret. Dette kan eller muligvis ikke betyde, at domænet har en DKIM-post, eller DKIM-posten ikke evalueres til et resultat, kun at denne meddelelse ikke er signeret.

- Domænebaseret meddelelsesgodkendelse, -rapportering og -overholdelse (**DMARC**):
  - Bestået: Angiver DMARC-tjek for den meddelelse, der er blevet videregivet.
  - Mislykket: Angiver, at DMARC-tjek for meddelelsen mislykkedes.
  - Bestguesspass: Angiver, at der ikke findes nogen DMARC TXT-post for domænet, men hvis der allerede findes en, så søger DMARC efter meddelelsen.
  - Ingen: Angiver, at der ikke findes nogen DMARC TXT-post for det afsendende domæne i DNS.

Ikke-farvesepareret godkendelse: Dette er en værdi, der bruges af Microsoft 365 til at kombinere mailgodkendelse som f.eks. SPF, DKIM og DMARC for at afgøre, om meddelelsen er ægte. Den anvender *mailens Fra:* -domæne som grundlag for evaluering.

### <a name="email-summary-panel"></a>Panel til mailoversigt

Panelet til mailoversigt er en opsummeret visning af hele siden mailenhed. Den indeholder standardiserede oplysninger om mailen (f.eks. registreringer) samt kontekstspecifikke oplysninger (f.eks. om karantæne- eller indsendelsesmetadata). Panelet til mailoversigt erstatter de traditionelle pop op-vinduet registreringer i realtid, Threat Explorer, indsendelser og rapportering.

> [!div class="mx-imgBorder"]
> ![Åbn linket til mailobjektet.](../../media/open-email-entity-mdo.png)

> [!NOTE]
> Hvis du vil have vist alle komponenterne, skal du klikke på **linket Åbn mailenhed** for at åbne hele siden mailenhed.  

Panelet til mailoversigt er opdelt i følgende afsnit:  

- *Leveringsoplysninger*: Indeholder oplysninger om trusler og tilsvarende tillidsniveau, registreringsteknologier og oprindelige og seneste leveringssted.

- *Mailoplysninger*: Indeholder oplysninger om mailegenskaber som f.eks. afsendernavn, afsenderadresse, tidspunkt for modtagelse, godkendelsesoplysninger og andre andre oplysninger.

- *URL-adresser*: Som standard får du vist tre URL-adresser og deres tilsvarende trusler. Du kan altid klikke på **Vis alle URL-adresser for** at udvide og få vist alle URL-adresser og eksportere dem.  

- *Vedhæftede* filer: Som standard vises der tre vedhæftede filer. Du kan altid klikke på **Vis alle vedhæftede filer for** at udvide og få vist alle vedhæftede filer. 

Ud over ovenstående afsnit vil du også se sektioner, der er specifikke for få oplevelser, som er integreret med oversigtspanelet: 

- Indsendelser: 

    - *Oplysninger om indsendelse*: Indeholder oplysninger om bestemte indsendelser, f.eks.:
        - Indsendt dato
        - Emne
        - Indsendelsestype
        - Årsag til indsendelse
        - Indsendelses-id
        - Indsendt af

    - *Resultatoplysninger*: Meddelelser, der sendes, gennemses. Du kan se resultatet af din indsendelse samt eventuelle anbefalede næste trin.

- Karantæne:  

    - *Oplysninger om karantæne*: Indeholder oplysninger, der er specifikke for karantæne. Få mere at vide under [Administrer meddelelser, der er sat i karantæne](manage-quarantined-messages-and-files.md#view-quarantined-message-details).

        - Udløber: Den dato/det klokkeslæt, hvor meddelelsen automatisk og permanent slettes fra karantæne.
        - Udgivet til: Alle mailadresser (hvis nogen), som meddelelsen er blevet frigivet til.
        - Endnu ikke frigivet til: Alle mailadresser (hvis nogen), som meddelelsen endnu ikke er blevet frigivet til.

    - *Karantænehandlinger*: Du kan finde flere oplysninger om forskellige karantænehandlinger i [Administrer meddelelser, der er sat i karantæne](manage-quarantined-messages-and-files.md#take-action-on-quarantined-email).
