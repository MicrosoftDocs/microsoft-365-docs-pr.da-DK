---
title: Få mere at vide om trænbare klassificeringer
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Klassificerere, der kan oplæres, kan genkende forskellige typer indhold til mærkning eller politikanvendelse ved at give dem positive og negative eksempler at se på.
ms.openlocfilehash: 0c47d019b3508bdd8d8fba1f1b4303c7f4c9579d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621199"
---
# <a name="learn-about-trainable-classifiers"></a>Få mere at vide om trænbare klassificeringer

Klassificering og mærkning af indhold, så det kan beskyttes og håndteres korrekt, er starttidspunktet for disciplinen information protection. Microsoft 365 har tre måder at klassificere indhold på.

## <a name="manually"></a>Manuelt

Manuel klassificering kræver menneskelig dømmekraft og handling. Brugere og administratorer anvender dem på indhold, når de støder på det. Du kan enten bruge de allerede eksisterende navne og typer af følsomme oplysninger eller bruge brugerdefinerede navne.  Du kan derefter beskytte indholdet og administrere dets fordeling.

## <a name="automated-pattern-matching"></a>Automatiseret mønstermatch

Denne kategori af klassificeringsmekanismer omfatter søgning efter indhold ved at:

- Nøgleord eller metadataværdier (nøgleordsforespørgselssprog).
- Brug af tidligere identificerede mønstre for følsomme oplysninger som f.eks. social sikring, kreditkort eller bankkontonumre [(objektdefinitioner af følsomme oplysningerstype)](sensitive-information-type-entity-definitions.md).
- Genkender et element, fordi det er en variation i en skabelon [(udskrivning af dokumentfinger)](document-fingerprinting.md).
- Brug af tilstedeværelsen af nøjagtige strenge [nøjagtigt datamatch](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types).

Følsomheds- og opbevaringsmærkater kan derefter anvendes automatisk for at gøre indholdet tilgængeligt til brug i [Få mere at vide om Microsoft Purview Forebyggelse af datatab](dlp-learn-about-dlp.md) og [anvend automatisk politik for opbevaringsmærkater](apply-retention-labels-automatically.md).

## <a name="classifiers"></a>Klassificeringer

Denne klassificeringsmetode er velegnet til indhold, der ikke nemt identificeres af de manuelle eller automatiserede metoder til mønstermatchning. Denne klassificeringsmetode handler mere om at bruge en klassificering til at identificere et element baseret på elementets indhold og ikke efter elementer, der findes i elementet (matchning af mønster). En klassificering lærer, hvordan du identificerer en type indhold ved at se på hundredvis af eksempler på det indhold, du er interesseret i at klassificere.

> [!NOTE]
> I prøveversion – Du kan få vist de klassificeringer, der kan oplæres, i Indholdsoversigt ved at udvide **Klassificeringer, der kan oplæres** i filterpanelet. De klassificeringer, der kan oplæres, viser automatisk antallet af hændelser, der findes i SharePoint, Teams og OneDrive, uden at der kræves nogen mærkning.
> Hvis du ikke vil bruge denne funktion, skal du sende en anmodning til Microsoft Support. Dette deaktiverer visningen af dine følsomme data, der ikke bruges i nogen mærkatpolitikker i Indholdsoversigt. Du kan også deaktivere scanning af dine data. Hvis scanning er slået fra, fungerer følsomhedsmærkater og DLP-politikker med disse klassificeringer ikke

### <a name="where-you-can-use-classifiers"></a>Her kan du bruge klassificeringer

Klassificeringer er tilgængelige til brug som en betingelse for [office-automatisk mærkning med følsomhedsmærkater](apply-sensitivity-label-automatically.md), [politik for automatisk anvendelse af opbevaringsmærkat baseret på en betingelse](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) og i [kommunikation med overholdelse af angivne standarder](communication-compliance.md).

Følsomhedsmærkater kan bruge klassificeringer som betingelser. Se [Anvend automatisk en følsomhedsmærkat på indhold](apply-sensitivity-label-automatically.md).

> [!IMPORTANT]
> Klassificeringer fungerer kun med elementer, der ikke er krypteret.

## <a name="types-of-classifiers"></a>Klassificeringstyper

- **færdiguddannede klassificeringer** – Microsoft har oprettet og forudoplært flere klassificeringer, som du kan begynde at bruge uden at oplære dem. Disse klassificeringer vises med statussen `Ready to use`.
- **brugerdefinerede klassificeringer, der kan oplæres** – Hvis du har klassificeringsbehov, der går ud over, hvad de forududdannede klassificeringer dækker, kan du oprette og oplære dine egne klassificeringer.

### <a name="pre-trained-classifiers"></a>Færdiguddannede klassificeringer

Microsoft 365 leveres med flere færdiguddannede klassificeringer:

- **Voksen, racy og gory**: Registrerer billeder af disse typer. Billederne skal have en størrelse på mellem 50 KB og 4 mb og være større end 50 x 50 pixel i højden x bredde. Scanning og registrering understøttes for Exchange Online mails og Microsoft Teams-kanaler og -chats. Registrerer indhold i .jpeg-, .png-, .gif- og .bmp-filer.

- **Aftaler**: Registrerer indhold, der er relateret til juridiske aftaler, f.eks. aftaler om hemmeligholdelse, arbejdserklæringer, låne- og leasingaftaler, ansættelses- og konkurrenceklausuler. Registrerer indhold i .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml-filer.

- **Kundeklager**: Klassificeringen af kundeklager registrerer feedback og klager over din organisations produkter eller tjenester. Denne klassificering kan hjælpe dig med at opfylde lovmæssige krav til registrering og behandling af klager, f.eks. forbrugerfinansieringsbureauet og fødevare- og drugadministrationskravene. I forbindelse med overholdelse af angivne standarder for kommunikation registreres indhold i .msg- og .eml-filer. I resten af Microsoft Purview Information Protection-tjenester registreres indhold i filer af typen .docx, .pdf, .txt, .rtf, .jpg, .jpeg, .png, .gif, .bmp og .svg.

- **Diskrimination**: Registrerer eksplicit diskriminerende sprog og er følsom over for diskriminerende sprog mod de afrikanske amerikanske/sorte samfund sammenlignet med andre samfund.

- **Finance**: Registrerer indhold i kategorierne virksomhedsfinansiering, regnskab, økonomi, bankvirksomhed og investering. Registrerer indhold i .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla filer.

- **Chikane**: Registrerer en bestemt kategori af krænkende sprogtekstelementer, der er relateret til stødende adfærd, der er målrettet til en eller flere personer, baseret på følgende træk: race, etnicitet, religion, national oprindelse, køn, seksuel orientering, alder, handicap. Registrerer indhold i filer af typen .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg.

- **Sundhedspleje**: Registrerer indhold i aspekter af sundheds- og sundhedsadministration, f.eks. sundhedsydelser, diagnosticering, behandling, krav osv. Registrerer indhold i .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla filer.

- **HR**: Registrerer indhold i personalerelaterede kategorier af rekruttering, interview, ansættelse, uddannelse, evaluering, advarsel og opsigelse. Registrerer indhold i .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla filer.

- **IP**: Registrerer indhold i kategorier relateret til immaterielle rettigheder, f.eks. forretningshemmeligheder og lignende fortrolige oplysninger. Registrerer indhold i .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla filer.

- **It**: Registrerer indhold i kategorierne Information Technology og Cybersecurity, f.eks. netværksindstillinger, informationssikkerhed, hardware og software. Registrerer indhold i .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla filer.

- **Juridiske anliggender**: Registrerer indhold i kategorier relateret til juridiske anliggender, f.eks. procesførelse, juridiske processer, juridiske forpligtelser, juridisk terminologi, lovgivning og lovgivning. Registrerer indhold i .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml-filer.

- **Indkøb**: Registrerer indhold i kategorier af bud, anførselstegn, køb og betaling for levering af varer og tjenester. Registrerer indhold i filer af typen .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.

- **Bandeord**: Registrerer en bestemt kategori af stødende sprogtekstelementer, der indeholder udtryk, der gør de fleste til grin. Registrerer indhold i filer af typen .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg.

- **Cv**: registrerer dokumenter, .pdf, .rtf, .txt elementer, der er tekstregnskaber for en ansøgers personlige, uddannelsesmæssige, faglige kvalifikationer, arbejdserfaring og andre personligt identificerende oplysninger

- **Kildekode**: Registrerer elementer, der indeholder et sæt instruktioner og sætninger, der er skrevet computerprogrammeringssprog på GitHub: ActionScript, C, C#, C++, Clojure, CoffeeScript, Go, Haskell, Java, JavaScript, Lua, MATLAB, Objective-C, Perl, PHP, Python, R, Ruby, Scala, Shell, Swift, TeX, Vim Script. Registrerer indhold i .msg, .as, .h, .c, .cs, .cc, .cpp, .hpp, .cxx, .hh, .c++, .clj, .edn, .cljc, .cljs, .coffee, .litcoffee, .go, .hs, .lhs, .java, .jar, .js, .mjs, .lua, .m, .mm, .pl, .pm, .t, .xs, .pod, .php, .phar, .php4, .pyc, . R, .r, .rda, . RData-, .rds-, .rb-, .scala-, .sc-, .sh- og .swift-filer.

  > [!NOTE]
  > Kildekode oplæres til at registrere, når størstedelen af teksten er kildekode. Den registrerer ikke kildekodetekst, der er afbrudt med almindelig tekst.

- **Skat**: Registrerer indhold af skatteforhold, f.eks. skatteplanlægning, skatteformularer, skatteregistrering, skatteregler. Registrerer indhold i .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, filer af typen .txt, .one, .msg, .eml, .pptx, .pptm, .ppt, .potx, .potm, .pot, .ppsx, .ppsm, .pps, .ppam, .ppa, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, xla filer.

- **Threat**: Registrerer en bestemt kategori af stødende tekstelementer på sprog relateret til trusler om at begå vold eller udføre fysisk skade på en person eller ejendom.

- **Threat**: Registrerer en bestemt kategori af stødende tekstelementer på sprog relateret til trusler om at begå vold eller udføre fysisk skade på en person eller ejendom. Registrerer indhold i filer af typen .msg, .docx, .pdf, .txt, .rtf, .jpeg, .jpg, .png, .gif, .bmp, .svg.

Disse klassificeringer vises i visningen **Microsoft Purview-compliance-portal** \> **Dataklassificering** \> **Klassificeringsklasse** med statussen `Ready to use`.

![classifiers-pre-trained-classifiers.](../media/classifiers-ready-to-use-classifiers.png)

> [!IMPORTANT]
> Bemærk, at de indbyggede og globale klassificeringer ikke indeholder en udtømmende eller komplet liste over begreber eller sprog på tværs af disse områder. Desuden ændres sprog- og kulturelle standarder hele tiden, og i lyset af disse realiteter forbeholder Microsoft sig ret til at opdatere disse klassificeringer efter eget skøn. Selvom klassificeringer kan hjælpe din organisation med at registrere disse områder, er klassificeringer ikke beregnet til at levere din organisations eneste måde at registrere eller håndtere brugen af et sådant sprog på. Din organisation, ikke Microsoft eller dens datterselskaber, forbliver ansvarlig for alle beslutninger vedrørende overvågning, scanning, blokering, fjernelse og opbevaring af indhold, der er identificeret af en færdiguddannet klassificering, herunder overholdelse af lokale love om beskyttelse af personlige oplysninger og andre gældende love. Microsoft opfordrer til at rådføre sig med juridisk rådgivning før udrulning og brug.

Klassificeringerne Threat, Profanity, Harassment og Discrimination kan scanne indhold på disse sprog:

- Arabisk
- Kinesisk (forenklet)
- Kinesisk (traditionelt)
- Dutch
- English
- French
- German
- Italian
- Korean
- Japanese
- Portugisisk
- Spanish

Alle andre er kun engelsk i øjeblikket.

### <a name="custom-classifiers"></a>Brugerdefinerede klassificeringer

Når de færdiguddannede klassificeringer ikke opfylder dine behov, kan du oprette og oplære dine egne klassificeringer. Der er mere arbejde forbundet med at oprette din egen, men de vil være meget bedre skræddersyet til dine organisationers behov.

Du begynder at oprette en brugerdefineret klassificering, der kan oplæres, ved at give den eksempler, der helt sikkert er i kategorien. Når den behandler disse eksempler, tester du den ved at give den en blanding af både matchende og ikke-matchende eksempler. Klassificeringen foretager derefter forudsigelser om, hvorvidt et bestemt element falder ind under den kategori, du bygger. Du kan derefter bekræfte resultaterne og sortere de sande positiver, sande negativer, falske positiver og falske negative for at øge nøjagtigheden af forudsigelserne.

Når du publicerer klassificeringen, sorteres elementerne på placeringer som SharePoint Online, Exchange og OneDrive, og indholdet klassificeres. Når du har publiceret klassificeringen, kan du fortsætte med at oplære den ved hjælp af en feedbackproces, der svarer til den indledende oplæringsproces.

Du kan f.eks. oprette klassificeringer, der kan oplæres, for:

- Juridiske dokumenter - f.eks advokat klient privilegium, lukning sæt, erklæring om arbejde
- Strategiske forretningsdokumenter - f.eks. pressemeddelelser, fusion og opkøb, tilbud, forretnings- eller marketingplaner, intellektuel ejendom, patenter, designdokumenter
- Prisoplysninger – f.eks. fakturaer, pristilbud, arbejdsordrer, buddokumenter
- Finansielle oplysninger - f.eks. organisatoriske investeringer, kvartalsvise eller årlige resultater

#### <a name="process-flow-for-creating-custom-classifiers"></a>Procesforløb til oprettelse af brugerdefinerede klassificeringer

Oprettelse og publicering af en klassificering til brug i løsninger til overholdelse af angivne standarder, f.eks. opbevaringspolitikker og kommunikationsovervågning, følger dette flow. Du kan finde flere oplysninger om oprettelse af en brugerdefineret klassificering, der kan oplæres, [under Oprettelse af en brugerdefineret klassificering](classifier-get-started-with.md).

![brugerdefineret klassificering af procesflow.](../media/classifier-trainable-classifier-flow.png)

### <a name="retraining-classifiers"></a>Klassificering af genoplæring

Du kan hjælpe med at forbedre nøjagtigheden af alle brugerdefinerede klassificeringer, der kan oplæres, og ved at give dem feedback om nøjagtigheden af den klassificering, de udfører. Dette kaldes genoplæring og følger denne arbejdsproces.

> [!NOTE]
> Færdiguddannede klassificeringer kan ikke oplæres igen.

![klassificeringsarbejdsproces til genoplæring.](../media/classifier-retraining-workflow.png)

## <a name="see-also"></a>Se også

- [Opbevaringsmærkater](retention.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Følsomhedsmærkater](sensitivity-labels.md)
- [Enhedsdefinitioner for type af følsomme oplysninger](sensitive-information-type-entity-definitions.md)
- [Udskrivning af dokumentfinger](document-fingerprinting.md)
- [Få mere at vide om nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
