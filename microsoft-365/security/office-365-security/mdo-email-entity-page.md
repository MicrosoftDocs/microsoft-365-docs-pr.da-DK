---
title: Den Microsoft Defender for Office 365 mailenhedsside
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
description: Microsoft Defender for Office 365 E5- og P1- og P2-kunder kan nu få en 360-graders visning af hver mail med mailenhedssiden.
ms.openlocfilehash: 79863916cab3b859a0b24de9dc5eb9b4f324a3f9
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648761"
---
# <a name="the-email-entity-page"></a>Siden Mailenhed

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for:**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**I denne artikel:**
- [Få adgang til mailobjektsiden](#reach-the-email-entity-page)
- [Læs mailobjektsiden](#read-the-email-entity-page)
- [Brug mailobjektsidefaner](#use-email-entity-page-tabs)
- [Ny på mailobjektsiden](#new-to-the-email-entity-page)

Administratorer af Microsoft Defender for Office 365 E5 og Defender for Office P1 og P2 har en 360 graders visning af mail ved hjælp af **enhedssiden Mail**. Denne gå til-mailside blev oprettet for at forbedre de oplysninger, der blev leveret i [trusselsstifinderens "maildetaljer"-fly-out](threat-explorer-views.md).

## <a name="reach-the-email-entity-page"></a>Få adgang til mailobjektsiden

Mailobjektsiden er tilgængelig på Microsoft 365 Defender-portalen på <https://security.microsoft.com> **Mail &** **Samarbejdsstifinder**\>. Du kan også gå direkte til siden **Stifinder** ved at bruge <https://security.microsoft.com/threatexplorer>.

Vælg emnet i en mail, du er ved at undersøge, i **Stifinder**. En guldbarr vises øverst i e-mail-fly-out for den mail. Denne invitation til den nye side lyder 'Prøv vores nye mailenhedsside med forbedrede data...'. Vælg at få vist den nye side.

:::image type="content" source="../../media/email-entities-1-navigation-to-ee.png" alt-text="Guldbanneren med ordene *Prøv vores nye mailenhedsside med forbedrede data* for at navigere til den nye oplevelse" lightbox="../../media/email-entities-1-navigation-to-ee.png":::

:::image type="content" source="../../media/email-entities-2-eep.png" alt-text="Grafikken på mailobjektsiden, der fokuserer på overskrifter, som du får vist" lightbox="../../media/email-entities-2-eep.png":::

> [!NOTE]
> De tilladelser, der kræves for at få vist og bruge denne side, er de samme som for at få vist **Stifinder**. Administratoren skal være medlem af Global administrator eller global læser eller Sikkerhedsadministrator eller Sikkerhedslæser. Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).

## <a name="read-the-email-entity-page"></a>Læs mailobjektsiden

Strukturen er designet til at være nem at læse og navigere gennem med et hurtigt øjekast. Forskellige faner øverst på siden giver dig mulighed for at undersøge det nærmere. Sådan fungerer layoutet:

1. De mest påkrævede felter er i venstre side af fly-out. Disse detaljer er 'klæbrige', hvilket betyder, at de er forankret til venstre, uanset hvilken fane du navigerer til i resten af fly-out.

    :::image type="content" source="../../media/email-entities-3-left-panel.png" alt-text="Grafikken på mailobjektsiden med venstre side fremhævet" lightbox="../../media/email-entities-3-left-panel.png":::

2. I øverste højre hjørne er de handlinger, der kan udføres på en mail. Alle handlinger, der kan udføres via **Stifinder** , vil også være tilgængelige via mailobjektsiden.

    :::image type="content" source="../../media/email-entities-5-preview.png" alt-text="Grafikken for mailobjektsiden med højre side fremhævet" lightbox="../../media/email-entities-5-preview.png":::

3. Du kan analysere mere ved at sortere resten af siden. Kontrollér oplysninger om registrering af mail, godkendelsesstatus for mail og header. Dette område skal kigges fra sag til sag, men oplysningerne under disse faner er tilgængelige for alle mails.

    :::image type="content" source="../../media/email-entities-4-middle-panel.png" alt-text="Hovedpanelet på siden, som indeholder mailheaderen og godkendelsesstatussen" lightbox="../../media/email-entities-4-middle-panel.png":::

### <a name="use-email-entity-page-tabs"></a>Brug mailobjektsidefaner

Fanerne øverst på objektsiden giver dig mulighed for at undersøge mail effektivt.

1. **Tidslinje**: Tidslinjevisningen for en mail (pr. **Tidslinje i Stifinder** ) viser den oprindelige levering til hændelser efter levering, der sker i en mail. For mails, der ikke har handlinger efter levering, viser visningen den oprindelige leveringsrække i tidslinjevisning. Hændelser som: ZAP (automatisk tømning på nul timer), Afhjælpning, KLIK PÅ URL-adresser, et cetera, fra kilder som: system, administrator og bruger vises her i den rækkefølge, de fandt sted.
2. **Analyse**: Analyse viser felter, der hjælper administratorer med at analysere en mail i dybden. I de tilfælde, hvor administratorer har brug for at forstå mere om registrering, afsender/modtager og godkendelsesoplysninger for mail, skal de bruge fanen Analyse. Links til vedhæftede filer og URL-adresser findes også på denne side under "Relaterede enheder". Både vedhæftede filer og identificerede trusler nummereres her, og når du klikker, føres du direkte til siderne med vedhæftede filer og URL-adresser. Denne fane har også indstillingen Vis overskrift til at *vise mailheaderen*. Administratorer kan sammenligne alle detaljer fra mailoverskrifter side om side med oplysninger på hovedpanelet for at få klarhed.
3. **Vedhæftede filer**: Dette undersøger vedhæftede filer, der findes i mailen, med andre oplysninger, der findes på vedhæftede filer. Antallet af vedhæftede filer, der vises, er i øjeblikket begrænset til 10. Bemærk, at oplysninger om detonering for vedhæftede filer, der er fundet skadelige, også vises her.
4. **URL-adresser**: Under denne fane vises de URL-adresser, der blev fundet i mailen, med andre oplysninger om URL-adresserne. Antallet af URL-adresser er begrænset til 10 lige nu, men disse 10 prioriteres først for at vise *skadelige URL-adresser*. Prioritering sparer tid og guess-work. De URL-adresser, der blev fundet skadelige og detonerede, vises også her.
5. **Lignende mails**: Under denne fane vises alle mails, der ligner *netværksmeddelelses-id'et og den modtagerkombination* , der er specifik for denne mail. Lighed er kun baseret på *meddelelsens brødtekst*. De beslutninger, der foretages på mails for at kategorisere dem som "lignende", omfatter ikke en overvejelse af *vedhæftede filer*.

## <a name="new-to-the-email-entity-page"></a>Ny på mailobjektsiden

Der er nye funktioner, der følger med denne mailobjektside. Her er listen.

### <a name="email-preview-for-cloud-mailboxes"></a>Maileksempel for Cloud-postkasser

Administratorer kan få vist mails i cloudpostkasser, ***hvis*** mails stadig findes i cloudmiljøet. I tilfælde af blød sletning (af en administrator eller bruger) eller ZAP (til karantæne) findes mails ikke længere på cloudplaceringen. I så fald kan administratorer ikke få vist disse specifikke mails. Mails, der blev droppet, eller hvor leveringen mislykkedes, nåede aldrig ind i postkassen. Det betyder, at administratorer heller ikke kan få forhåndsvist disse mails.

> [!WARNING]
> Forhåndsvisning af mails kræver en særlig rolle kaldet **Prøveversion**. Du kan tilføje denne rolle på Microsoft 365 Defender-portalen som beskrevet i [Mail & samarbejdsroller på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md#email--collaboration-roles-in-the-microsoft-365-defender-portal). Du skal muligvis oprette en ny **mail & rollegruppe for samarbejde** der og føje **rollen Eksempel** til den nye rollegruppe eller føje **rollen Eksempel** til en rollegruppe, der gør det muligt for administratorer i din organisation at arbejde i **Stifinder**.

### <a name="detonation-details"></a>Oplysninger om detonation

Disse oplysninger er specifikke for vedhæftede filer i mails og URL-adresser. Brugerne kan se disse oplysninger ved at gå til Stifinder og anvende det *registreringsteknologifilter* , der er indstillet til fildeonation eller URL-detonation. Mails, der er filtreret til detonation af filer, indeholder en skadelig fil med oplysninger om detonation, og dem, der er filtreret efter URL-adresser, indeholder en skadelig URL-adresse og dens detonationsoplysninger.

Brugerne får vist forbedrede oplysninger om detonation for kendte ondsindede vedhæftede filer eller URL-adresser, der findes i deres mails, som blev detoneret for deres specifikke lejer. Den indeholder oplysninger om sprængningskæden, sprængningsoversigten, skærmbillede og observeret adfærd for at hjælpe kunderne med at forstå, hvorfor den vedhæftede fil eller URL-adresse blev anset for at være ondsindet og detoneret.

1. *Detonationskæde*. En enkelt fil eller URL-detonation kan udløse flere detonationer. Kæden til sprængning sporer stien til deonations, herunder den oprindelige skadelige fil eller URL-adresse, der forårsagede dommen, og alle andre filer eller URL-adresser, der er påvirket af detonationen. Disse URL-adresser eller vedhæftede filer findes muligvis ikke direkte i mailen, men det er vigtigt at inkludere denne analyse for at finde ud af, hvorfor filen eller URL-adressen blev fundet skadelig.  

    > [!NOTE]
    > Dette kan kun vise elementet på øverste niveau, hvis ingen af de objekter, der er knyttet til det, blev fundet problematiske eller blev detoneret.

1. *Detonation Summary* giver en grundlæggende oversigt for detonation såsom *analysetid*, det tidspunkt, hvor detonation indtraf, OS og program, det operativsystem og program, hvor detonationen fandt sted, filstørrelse, og dom årsag.
1. *Skærmbilleder* , der viser de skærmbilleder, der er taget under detonationen. Der kan være flere skærmbilleder under detonationen. Der registreres ingen skærmbilleder til
    - Objektbeholdertypefiler, f.eks. .zip eller .rar.
    - Hvis der åbnes en URL-adresse i et link, der downloader en fil direkte. Du kan dog se den downloadede fil i detonationskæden.
1. *Detaljer om funktionsmåde* er en eksport, der viser detaljer om funktionsmåden, f.eks. nøjagtige hændelser, der fandt sted under detonation, og observables, der indeholder URL-adresser, IP-adresser, domæner og filer, der blev fundet under detonationen (og kan enten være problematiske eller godartede). Vær opmærksom på, at der muligvis ikke er nogen oplysninger om funktionsmåde for:
    - Objektbeholderfiler, f.eks. .zip eller .rar, der indeholder andre filer.

:::image type="content" source="../../media/email-entities-6-detonation-page.png" alt-text="Oversigt over detonation, der viser kæden, oversigten, oplysninger om detonation og skærmbillede under overskriften *Detaljeret analyse*" lightbox="../../media/email-entities-6-detonation-page.png":::

### <a name="other-innovations"></a>Andre nyskabelser

*Mærker*: Dette er mærker, der anvendes på brugere. Hvis brugeren er modtager, kan administratorer se et *modtagermærke* . Hvis brugeren er afsender, er det på samme måde en *afsenderkode* . Dette vises i venstre side af siden med mailenheder (i den del, der beskrives som *sticky* og dermed forankret til siden).

*Seneste leveringsplacering*: Den seneste leveringsplacering er den placering, hvor en mail landede, efter systemhandlinger som ZAP eller administratorhandlinger som f.eks. Flyt til slettede elementer, afslut. Den seneste leveringsplacering er ikke beregnet til at informere administratorer om meddelelsens *aktuelle* placering. Hvis en bruger f.eks. sletter en meddelelse eller flytter den til arkiv, opdateres leveringsplaceringen ikke. Men hvis en systemhandling har fundet sted og opdateret placeringen (f.eks. en ZAP, der medfører, at en mail flyttes til karantæne), vil dette opdatere den seneste leveringsplacering til karantæne.

*Mailoplysninger*: Oplysninger, der kræves for at få en bedre forståelse af mail, der er tilgængelig under fanen *Analyse* .

- *Exchange transportregler (også kendt som regler for mailflow eller ETR'er):* Disse regler anvendes på en meddelelse på transportlaget og har forrang over phish- og spam-domme. Regler for mailflow oprettes og ændres i Exchange Administration på <https://admin.exchange.microsoft.com/#/transportrules>, men hvis en regel for mailflow gælder for en meddelelse, vises regelnavnet og GUID her. Værdifulde oplysninger til sporingsformål.

- *Primær tilsidesættelse: Kilde*: Primær tilsidesættelse og kilde refererer til lejeren eller brugerindstillingen, der påvirkede leveringen af mailen og tilsidesætter den leveringsplacering, der er angivet af systemet (i henhold til trussels- og registreringsteknologien). Dette kan f.eks. være en blokeret mail pga. en lejerkonfigureret transportregel eller en tilladt mail på grund af en slutbrugerindstilling for Pengeskab Afsendere. 

- *Alle tilsidesættelser*: Alle tilsidesættelser refererer til listen over tilsidesættelser (lejer- eller brugerindstillinger), der blev anvendt på mailen, hvilket måske eller måske ikke har påvirket leveringen af en mail. Hvis en lejerkonfigureret transportregel og en lejerkonfigureret politikindstilling (f.eks. fra listen Over tilladte lejere) f.eks. anvendes på en mail, vises begge i dette felt. Du kan kontrollere det primære tilsidesættelsesfelt for at bestemme den indstilling, der påvirkede leveringen af mailen. 

- *Bulk Complaint Level (BCL)*: Meddelelsens bulkklageniveau (BCL). En højere BCL angiver, at der er større sandsynlighed for, at en massemailmeddelelse genererer klager (det naturlige resultat, hvis mailen sandsynligvis vil være spam).

- *Niveau for spamsikkerhed :SCL-niveauet* (Spam Confidence Level) for meddelelsen. En højere værdi angiver, at der er større sandsynlighed for, at meddelelsen er spam.

- *Klienttype*: Angiver den klienttype, som mailen blev sendt fra, som REST.

- *Videresendelse*: I forbindelse med scenarier med autoforwaridng angiver den videresendelsesbrugeren samt videresendelsestypen, f.eks. ETR eller SMTP-videresendelse. 

- *Distributionsliste*: Viser distributionslisten, hvis modtageren har modtaget mailen som medlem af listen. Den viser distributionslisten på øverste niveau, hvis der er indlejrede distributionslister involveret.  

- *Til, Cc*: Angiver de adresser, der er angivet i felterne Cc i en mail. Oplysningerne i disse felter er begrænset til 5000 tegn. 

- *Domænenavn*: Er afsenderens domænenavn.

- *Domæneejer*: Angiver ejeren af det afsendende domæne.

- *Domæneplacering*: Angiver placeringen af det afsendende domæne.

- *Oprettelsesdato for domæne*: Angiver oprettelsesdatoen for det afsendende domæne. Et nyligt oprettet domæne er noget, du kan være forsigtig med, hvis andre signaler indikerer mistænkelig adfærd.

*Mailgodkendelse*: Godkendelsesmetoder til mail, der bruges af Microsoft 365 omfatter SPF, DKIM og DMARC.

- **SPF** (Sender Policy Framework): Beskriver resultaterne for SPF-kontrollen af meddelelsen. De mulige værdier kan være:
  - Gennemløb (IP-adresse): SPF-kontrollen for den sendte meddelelse og indeholder afsenderens IP-adresse. Klienten er godkendt til at sende eller videresende mail på vegne af afsenderens domæne.
  - Mislykket (IP-adresse): SPF-kontrollen for meddelelsen mislykkedes og indeholder afsenderens IP-adresse. Dette kaldes nogle gange hard fail.
  - Softfail (årsag): Den SPF-post, der har angivet værten som ikke må sende, men er i overgang.
  - Neutral: SPF-posten angiver eksplicit, at den ikke hævder, om IP-adressen er godkendt til at sende.
  - Ingen: Domænet har ikke en SPF-post, eller SPF-posten evalueres ikke til et resultat.
  - Temperror: Der opstod en midlertidig fejl. Det kan f.eks. være en DNS-fejl. Den samme kontrol kan blive fuldført senere.
  - Permerror: Der opstod en permanent fejl. Domænet har f.eks. en forkert formateret SPF-post.

- Domænenøgler identificeret mail (**DKIM**):
  - Gennemløb: Angiver DKIM-kontrollen for den sendte meddelelse.
  - Fail (årsag): Angiver DKIM-kontrollen for meddelelsen mislykkedes og hvorfor. Hvis meddelelsen f.eks. ikke blev signeret, eller signaturen ikke blev bekræftet.
  - Ingen: Angiver, at meddelelsen ikke er signeret. Dette indikerer måske eller måske ikke, at domænet har en DKIM-post, eller at DKIM-posten ikke evalueres til et resultat, men kun at denne meddelelse ikke er signeret.

- Domænebaseret meddelelsesgodkendelse, -rapportering og -overensstemmelse (**DMARC**):
  - Pass: Angiver DMARC-kontrollen for den sendte meddelelse.
  - Mislykket: Angiver, at DMARC-kontrollen for meddelelsen mislykkedes.
  - Bestguesspass: Angiver, at der ikke findes nogen DMARC TXT-post for domænet, men hvis der havde eksisteret en, ville DMARC-kontrollen for meddelelsen være bestået.
  - Ingen: Angiver, at der ikke findes nogen DMARC TXT-post for det afsendende domæne i DNS.

*Sammensat godkendelse*: Dette er en værdi, der bruges af Microsoft 365 til at kombinere mailgodkendelse, f.eks. SPF, DKIM og DMARC, for at bestemme, om meddelelsen er autentisk. Den bruger domænet *From:* for mailen som grundlag for evaluering.

### <a name="email-summary-panel"></a>Panelet Mailoversigt

Panelet mailoversigt er en opsummeret visning af hele mailobjektsiden. Den indeholder standardiserede oplysninger om mailen (f.eks. registreringer) samt kontekstspecifikke oplysninger (f.eks. for metadata om karantæne eller indsendelser). Panelet med mailoversigten erstatter de traditionelle registreringer i realtid, Threat Explorer, indsendelser og rapporter.

> [!div class="mx-imgBorder"]
> ![Åbn mailobjektlinket.](../../media/open-email-entity-mdo.png)

> [!NOTE]
> Hvis du vil have vist alle komponenterne, skal du klikke på linket **Åbn mailobjekt** for at åbne hele mailobjektsiden.  

Panelet med mailoversigten er opdelt i følgende afsnit:  

- *Leveringsoplysninger*: Indeholder oplysninger om trusler og tilsvarende tillidsniveau, registreringsteknologier og original og seneste leveringsplacering.

- *Mailoplysninger*: Indeholder oplysninger om mailegenskaber, f.eks. afsendernavn, afsenderadresse, modtaget tid, godkendelsesoplysninger og andre flere andre oplysninger.

- *URL-adresser*: Som standard kan du se tre URL-adresser og deres tilsvarende trusler. Du kan altid klikke på **Vis alle URL-adresser** for at udvide og se alle URL-adresser og eksportere dem.  

- *Vedhæftede filer*: Som standard kan du se tre vedhæftede filer. Du kan altid klikke på **Vis alle vedhæftede filer** for at udvide og se alle vedhæftede filer. 

Ud over ovenstående afsnit kan du også se afsnit, der er specifikke for få oplevelser, som er integreret i oversigtspanelet: 

- Indlæg: 

    - *Oplysninger om indsendelse*: Indeholder oplysninger om de specifikke indsendelser, f.eks.:
        - Dato for afsendelse
        - Emne
        - Indsendelsestype
        - Årsag til afsendelse
        - Afsendelses-id
        - Sendt af

    - *Resultatoplysninger*: Meddelelser, der sendes, gennemses. Du kan se resultatet af din indsendelse samt eventuelle anbefalede næste trin.

- Karantæne:  

    - *Karantæneoplysninger*: Indeholder karantænespecifikke oplysninger. Du kan få flere oplysninger under [Administrer karantænemeddelelser](manage-quarantined-messages-and-files.md#view-quarantined-message-details).

        - Udløber: Den dato/det klokkeslæt, hvor meddelelsen automatisk slettes og slettes permanent fra karantæne.
        - Udgivet til: Alle de mailadresser (hvis der er nogen), som meddelelsen er blevet frigivet til.
        - Endnu ikke frigivet til: Alle mailadresser (hvis nogen), som meddelelsen endnu ikke er frigivet til.

    - *Karantænehandlinger*: Du kan få flere oplysninger om forskellige karantænehandlinger under [Administrer karantænemeddelelser](manage-quarantined-messages-and-files.md#take-action-on-quarantined-email).
