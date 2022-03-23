---
title: Få mere at vide om klassekammerater, der kan trænes
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
description: Trænbare klassificeringer kan genkende forskellige typer indhold til mærkning eller politikprogram ved at give dem positive og negative eksempler at kigge på.
ms.openlocfilehash: 50d20c3a40b21696c06064b548d7766684fb12a0
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/19/2022
ms.locfileid: "63591456"
---
# <a name="learn-about-trainable-classifiers"></a>Få mere at vide om klassekammerater, der kan trænes

Klassificering og mærkning af indhold, så det kan beskyttes og håndteres korrekt, er udgangspunktet for informationsbeskyttelsesdisciplinen. Microsoft 365 har tre måder at klassificere indhold på.

## <a name="manually"></a>Manuelt

Manuel klassificering kræver menneskelig vurdering og handling. Brugere og administratorer anvender dem på indhold, når de støder på det. Du kan enten bruge de eksisterende etiketter og typer af følsomme oplysninger eller bruge brugerdefinerede.  Du kan derefter beskytte indholdet og administrere dets disposition.

## <a name="automated-pattern-matching"></a>Automatiseret mønstersammenholdelse

Denne kategori af klassificeringsmekanismer omfatter at finde indhold ved at:

- Nøgleord eller metadataværdier (sprog til nøgleordsforespørgsel).
- Ved hjælp af tidligere identificerede mønstre af følsomme oplysninger som f.eks. cpr-numre, kreditkortnumre eller bankkontonumre [(definitioner af følsomme oplysningstype enheder)](sensitive-information-type-entity-definitions.md).
- Genkende et element, fordi det er en variant af en skabelon [(udskrivning af dokument finger)](document-fingerprinting.md).
- Brug tilstedeværelsen af nøjagtige strenge for [nøjagtigt match af data](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types).

Følsomheds- og opbevaringsmærkater kan derefter automatisk anvendes for at gøre indholdet tilgængeligt til brug i Få mere at vide om forebyggelse af [datatab](dlp-learn-about-dlp.md) og automatisk anvendelse af [politik til opbevaring af navne](apply-retention-labels-automatically.md).

## <a name="classifiers"></a>Klassificeringer

Denne klassificeringsmetode er velegnet til indhold, der hverken er let at identificere med manuelle eller automatiserede metoder til mønstersammenholdelse. Denne metode til klassificering handler mere om at bruge en klassificering til at identificere et element, der er baseret på, hvad elementet er, ikke efter elementer, der er i elementet (mønstermatching). En klassificering lærer, hvordan du identificerer en type indhold ved at se på hundredvis af eksempler på det indhold, du er interesseret i at klassificere.

> [!NOTE]
> I Forhåndsvisning – Du kan få vist de trainable klassificeringer i indholdsstifinder ved at udvide **Trainable Classifiers** i filterpanelet. De togbare klassificeringer viser automatisk antallet af hændelser, der findes i SharePoint, Teams og OneDrive, uden at der kræves mærkning.
> Hvis du ikke vil bruge denne funktion, skal du indsende en anmodning til Microsoft Support for at deaktivere klassificering uden brug. Dette deaktiverer scanningen af dit følsomme og mærkede indhold, før du opretter mærkningspolitikker.

### <a name="where-you-can-use-classifiers"></a>Her kan du bruge klassificeringer

Klassificeringer er tilgængelige til at bruge som en betingelse for [Office automatisk mærkat med](apply-sensitivity-label-automatically.md) følsomhedsmærkater, [anvend](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) automatisk opbevaringsetiketpolitik baseret på en betingelse og i [kommunikationsoverholdelse](communication-compliance.md). 

Følsomhedsmærkater kan bruge klassificeringer som betingelser, se [Anvend en følsomhedsmærkat på indhold automatisk](apply-sensitivity-label-automatically.md).

> [!IMPORTANT]
> Klassificeringer fungerer kun med elementer, der ikke er krypteret.

## <a name="types-of-classifiers"></a>Typer af klassificeringer

- **præ-uddannede klassificeringer** – Microsoft har oprettet og uddannet flere klassekammerater, som du kan begynde at bruge uden træning. Disse klassificeringer vises med statussen `Ready to use`.
- **Brugerdefinerede, trænbare** klassificeringer – Hvis du har klassificeringsbehov, der strækker sig ud over, hvad de præ-uddannede klassificeringer dækker, kan du oprette og oplære dine egne klassificeringer.

### <a name="pre-trained-classifiers"></a>Pre-trained classifiers

Microsoft 365 leveres med flere færdigtrænede klassificeringer:

> [!CAUTION]
> Vi fraråder den **præ-uddannede classifier** for stødende sprog, fordi den har produceret et stort antal falske positive. Brug det ikke, og hvis du bruger det i øjeblikket, skal du flytte dine forretningsprocesser væk fra det. Vi anbefaler, at **du i** stedet bruger de forudtrædede **klassificeringer Threat**, **Profanity** og Har chikane.

- **CV'er**: registrerer docx-, .pdf-, .rtf-, .txt-elementer, der er tekstkonti for enansøgers personlige, uddannelsesmæssige, professionelle kvalifikationer, erhvervserfaring og andre personligt identificerbare oplysninger
- Kildekode **: registrerer** elementer, der indeholder et sæt instruktioner og sætninger, der er skrevet i de 25 mest anvendte computerprogrammeringssprog på GitHub: ActionScript, C, C#, C++, Clojure, CoffeeScript, Go, Haskell, Java, JavaScript, Lua, MATLAB, Objective-C, Perl, PHP, Python, R, Ruby, Scala, Shell, Swift, TeX, Vim Script. Registrerer indhold i .msg, .as, .h, .c, .cs, .cc, .cpp, .hpp, .cxx, .hh, .c++, .clj, .edn, .cljc, .cljs, .coffee, .litcoffee, .go, .hs, .lhs, .java, .jar, .js, .mjs, .lua, .m, .mm, .pl, .pm, .t, .xs, .pod, .php, .phar, .php4, .pyc, . R, .r, .rda, . RData, .rds, .rb, .scala, .sc, .sh, .swift-filer.

> [!NOTE]
> Kildekode er trænet til at registrere, når størstedelen af teksten er kildekode. Den registrerer ikke kildekodetekst, der er interspereret med almindelig tekst.

- **Aftaler**: Registrerer indhold relateret til juridiske aftaler som f.eks. fortrolighedsaftaler, arbejdserklæringer, låne- og leaseaftaler, ansættelses- og ikke-konkurrencerelaterede aftaler. Registrerer indhold i .docx-, .docm-, .doc-, .dotx-, .dotm-, .dot-, .pdf-, .rtf-, .txt-, .one-, .msg-, .eml-filer.
- **Adfærd**: Registrerer eksplicitte sproget, der taler mere naturligt, og er følsomt over for sproget, der tales af deafrikanske/sorte grupper sammenlignet med andre communities.
- **Økonomi**: Registrerer indhold i kategorierne virksomhedsøkonomi, regnskab, økonomi, bank og investering. Registrerer indhold i .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one-, .msg-, .eml-, .pptx-, .pptm-, .ppt-, .potx-, .pot-, .ppsx-, .ppsm-, .pps-, .ppam-, .ppa-, .xlsx-, .xlsm-, .xlsb-, .xls-, .csv-, .xltx-, .xltm-, .xlam- og .xla-filer.
- **Chikane**: Registrerer en bestemt kategori af stødende sprogtekstelementer, der er relateret til stødende adfærd målrettet mod en eller flere personer baseret på følgende baggrunde: racer, had, religion, national oprindelse, køn, seksuel orientering, alder, handicap. Registrerer indhold i .msg-, .docx-, .pdf-, .txt-, .rtf-, .jpeg-, .jpg-, .png-, .gif-, .bmp-, .svg-filer.
- **Sundhedssektoren:** Registrerer indhold i sundheds- og sundhedsadministrationen såsom medicinske tjenester, diagnoser, behandling, krav osv. Registrerer indhold i .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one-, .msg-, .eml-, .pptx-, .pptm-, .ppt-, .potx-, .pot-, .ppsx-, .ppsm-, .pps-, .ppam-, .ppa-, .xlsx-, .xlsm-, .xlsb-, .xls-, .csv-, .xltx-, .xltm-, .xlam- og .xla-filer.
- **HR**: Registrerer indhold i kategorier over HR-relaterede kategorier af medarbejdere, interview, ansættelse, uddannelse, evaluering, advarsel og opsigelse. Registrerer indhold i .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one-, .msg-, .eml-, .pptx-, .pptm-, .ppt-, .potx-, .pot-, .ppsx-, .ppsm-, .pps-, .ppam-, .ppa-, .xlsx-, .xlsm-, .xlsb-, .xls-, .csv-, .xltx-, .xltm-, .xlam- og .xla-filer.
- **IP**: Registrerer indhold i kategorier relateret til immaterielle rettigheder såsom forretningshemmeligheder og lignende fortrolige oplysninger. Registrerer indhold i .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one-, .msg-, .eml-, .pptx-, .pptm-, .ppt-, .potx-, .pot-, .ppsx-, .ppsm-, .pps-, .ppam-, .ppa-, .xlsx-, .xlsm-, .xlsb-, .xls-, .csv-, .xltx-, .xltm-, .xlam- og .xla-filer.
- **IT**: Registrerer indhold i kategorier for informationsteknologi og cybersikkerhed såsom netværksindstillinger, informationssikkerhed, hardware og software. Registrerer indhold i .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one-, .msg-, .eml-, .pptx-, .pptm-, .ppt-, .potx-, .pot-, .ppsx-, .ppsm-, .pps-, .ppam-, .ppa-, .xlsx-, .xlsm-, .xlsb-, .xls-, .csv-, .xltx-, .xltm-, .xlam- og .xla-filer.
- **Juridiske emner**: Registrerer indhold i kategorier, der vedrører juridiske emner som procesførelse, procesførelse, juridisk forpligtelse, juridisk terminologi, lovgivning og lovgivning. Registrerer indhold i .docx-, .docm-, .doc-, .dotx-, .dotm-, .dot-, .pdf-, .rtf-, .txt-, .one-, .msg-, .eml-filer.
- **Indkøb**: Registrerer indhold i kategorier af produkter, tilbud, indkøb og betaling for levering af varer og tjenester. Registrerer indhold i filer af .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one, .msg, .eml, .xlsx, .xlsm, .xlsb, .xls, .csv, .xltx, .xltm, .xlt, .xlam, .xla.
- **Bandeord**: Registrerer en bestemt kategori af stødende sprogtekstelementer, der indeholder udtryk, der pinligt de fleste personer. Registrerer indhold i .msg-, .docx-, .pdf-, .txt-, .rtf-, .jpeg-, .jpg-, .png-, .gif-, .bmp-, .svg-filer.
- **Moms**: Registrerer skatterelationsindhold som f.eks. skatteplanlægning, skatteformularer, skatteangivelser og skattebestemmelser. Registrerer indhold i .docx, .docm, .doc, .dotx, .dotm, .dot, .pdf, .rtf, .txt, .one-, .msg-, .eml-, .pptx-, .pptm-, .ppt-, .potx-, .pot-, .ppsx-, .ppsm-, .pps-, .ppam-, .ppa-, .xlsx-, .xlsm-, .xlsb-, .xls-, .csv-, .xltx-, .xltm-, .xlam-, xla-filer.
- **Trussel**: Registrerer en bestemt kategori af stødende tekstelementer i forbindelse med trusler om at begået vold eller gøre fysisk skade eller skade på en person eller egenskab. Registrerer indhold i .msg-, .docx-, .pdf-, .txt-, .rtf-, .jpeg-, .jpg-, .png-, .gif-, .bmp-, .svg-filer.

Disse vises i **Microsoft 365 Overholdelsescenter** >  **DataKlassificeringer** > , der kan klassificeres med status `Ready to use`.

![classifiers-pre-trained-classifiers.](../media/classifiers-ready-to-use-classifiers.png)

> [!IMPORTANT]
> Bemærk, at det stødende sprog, chikane, bandeord, fortrolighed, fortrolighed og trusselsklasse kun fungerer med søgbar tekst og ikke er en komplet liste over ord eller sprog på tværs af disse områder. Yderligere ændres sprog og kulturelle standarder løbende, og i forhold til disse realiteter forbeholder Microsoft sig retten til efter eget skøn at opdatere disse klassificeringer. Selvom klassificeringer kan hjælpe din organisation med at finde disse områder, er klassificeringer ikke beregnet til at levere din organisations eneste måde at registrere eller adressere brugen af et sådant sprog på. Din organisation, ikke Microsoft eller Microsofts datterselskaber, forbliver ansvarlig for alle beslutninger vedrørende overvågning, scanning, blokering, fjernelse og opbevaring af alt indhold, der er identificeret af en præ-uddannet klassificering, herunder overholdelse af lokal lovgivning om beskyttelse af personlige oplysninger og anden gældende lovgivning. Microsoft opfordrer til rådgivning med juridisk rådgivning før implementering og brug.

Præ-uddannede klassificeringer kan scanne indhold på disse sprog:

• Kinesisk (forenklet) • Engelsk • Fransk • Tysk • Italiensk • Japansk • Portugisisk • Spansk

### <a name="custom-classifiers"></a>Brugerdefinerede klassificeringer

Når de forhåndstrænede klassificeringer ikke opfylder dine behov, kan du oprette og træne dine egne klassificeringer. Der er væsentligt mere arbejde involveret i at oprette din egen, men de bliver meget bedre skræddersyet til dine organisationers behov.

Du begynder at oprette en brugerdefineret, trænbar klassificering ved at give den eksempler, der helt sikkert er i kategorien. Når den behandler disse eksempler, skal du teste den ved at give den en blanding af både matchende og ikke-matchende eksempler. Klassificeringen foretager derefter prognoser for, om et givent element falder inden for den kategori, du opbygger. Du bekræfter derefter resultaterne og sorterer de egentlige positive, sande negativer, falske positive og falske negativer ud for at øge nøjagtigheden af forudsigelserne. 

Når du publicerer klassificeringen, sorterer den elementer på placeringer som SharePoint Online, Exchange og OneDrive og klassificerer indholdet. Når du publicerer klassificeringen, kan du fortsætte med at træne den ved hjælp af en feedbackproces, der svarer til den indledende kursusproces.

Du kan f.eks. oprette klassificeringer, der kan trænes til:

- Juridiske dokumenter – f.eks. advokatens klientrettigheder, lukkesæt, arbejdsopgørelse
- Strategiske forretningsdokumenter - som f.eks. pressemeddelelser, fusion og overtagelse, handler, forretnings- eller marketingplaner, intellektuel ejendom, patenter, designdokumenter
- Prisoplysninger - f.eks. fakturaer, pristilbud, arbejdsordrer, dokumenter med priser
- Finansielle oplysninger – f.eks. organisatoriske investeringer, kvartalsvise eller årlige resultater

#### <a name="process-flow-for-creating-custom-classifiers"></a>Procesflow til oprettelse af brugerdefinerede klassificeringer

Dette flow følger, når du opretter og publicerer en klassificering til brug i løsninger til overholdelse af regler og standarder, f.eks. opbevaringspolitikker og kommunikationsovervågning. Hvis du vil have mere at vide om at oprette en brugerdefineret, trænbar klassificering, skal [du se Opret en brugerdefineret klassificering](classifier-get-started-with.md).

![brugerdefineret klassificering af procesforløb.](../media/classifier-trainable-classifier-flow.png)

### <a name="retraining-classifiers"></a>Omskoling af klassificeringer

Du kan hjælpe med at forbedre nøjagtigheden af alle brugerdefinerede, trænbare klassificeringer og ved at give dem feedback om nøjagtigheden af den klassificering, de udfører. Dette kaldes omskodning og følger denne arbejdsproces.

> [!NOTE]
> Allerede oplærte klassificeringer kan ikke genlæres.

![arbejdsprocessen til omskoling af klassificering.](../media/classifier-retraining-workflow.png)

## <a name="see-also"></a>Se også

- [Opbevaringsnavne](retention.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Følsomhedsmærkater](sensitivity-labels.md)
- [Enhedsdefinitioner for følsomme oplysningstyper](sensitive-information-type-entity-definitions.md)
- [Udskrivning af dokument finger](document-fingerprinting.md)
- [Få mere at vide om nøjagtige dataoverensstemmelsesbaserede typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
