---
title: Brug forklaringsskabeloner i Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du bruger og gemmer forklaringsskabeloner i Microsoft SharePoint Syntex.
ms.openlocfilehash: 87d151a3dc0863b880515abb6ee59d3691d9e4c6
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63598502"
---
# <a name="use-explanation-templates-in-microsoft-sharepoint-syntex"></a>Brug forklaringsskabeloner i Microsoft SharePoint Syntex

Selvom du manuelt kan tilføje forskellige udtrykslisteværdier for din forklaring, kan det være nemmere at bruge de skabeloner, du har til rådighed i forklaringsbiblioteket.

I *stedet for* manuelt at tilføje alle variationer for dato kan du f.eks. bruge skabelonen udtryksliste *til dato* , fordi den allerede indeholder mange udtrykslister:

![Forklaringsbibliotek.](../media/content-understanding/explanation-template.png)

Forklaringsbiblioteket indeholder ofte anvendte *udtrykslisteforklaringer* , herunder:

- Dato: Kalenderdatoer, alle formater. Omfatter tekst og tal (f.eks. "9. december 2020").
- Dato (numerisk): Kalenderdatoer, alle formater. Inkluderer tal (f.eks. 1-11-2020).
- Klokkeslæt: 12-timers og 24-timers format.
- Tal: Positive og negative tal op til to decimaler.
- Procent: En liste over mønstre, der repræsenterer en procentdel. For eksempel 1 %, 11 %, 100 % eller 11,11 %.
- Telefon tal: Almindelige amerikanske og internationale formater. For eksempel 000 000 0000, 000-000-0000, (000)000-0000 eller (000) 000-0000.
- Postnummer: Amerikanske postnumre. Eksempel: 11111, 11111-1111.
- Første ord i en sætning: Almindelige mønstre for ord på op til ni tegn.
- Slutning af sætning: Almindelig tegnsætning i slutningen af en sætning.
- Kreditkort: Almindelige talformater for kreditkort. Eksempel: 1111-1111-1111-1111.
- CPR-nummer: AMERIKANSK CPR-nummerformat. Eksempel: 111-11-1111.
- Afkrydsningsfelt: En udtryksliste, der repræsenterer variationer af et udfyldt afkrydsningsfelt. F.eks _. X_, _ _X_.
- Valuta: Større internationale symboler. F.eks. $.
- Mail-CC: En sætningsliste med ordet "CC:", som ofte findes i nærheden af navnene eller mailadresserne på andre personer eller grupper, som meddelelsen blev sendt til.
- Maildato: En sætningsliste med ordet "Sendt den:", som ofte findes nær den dato, mailen blev sendt.
- Mailhilsen: Almindelige åbningslinjer for mails.
- Mailmodtager: En sætningsliste med ordet "Til:", som ofte findes i nærheden af navnene eller mailadresserne på personer eller grupper, som meddelelsen blev sendt til.
- Mailafsender: En sætningsliste med ordet "Fra:", som ofte findes i nærheden af afsenderens navn eller mailadresse.
- Mail emne: En sætningsliste med ordet "Emne:", som ofte findes i nærheden af mailens emne.

Forklaringsbiblioteket indeholder også ofte anvendte *regulære udtryksforklaringer* , herunder:

- 6-cifret til 17-cifrede tal: Svarer til et vilkårligt tal fra 6 til 17 cifre. Amerikanske bankkontonumre passer til dette mønster.
- Mailadresse: Matcher en almindelig type mailadresse som f.eks meganb@contoso.com.
- Amerikansk skatteyders id-nummer: Matcher et trecifret tal, der starter med 9 efterfulgt af et sekscifret tal, der starter med 7 eller 8.
- Webadresse (URL): Svarer til formatet af en webadresse, startende med http:// eller https://.

Desuden indeholder forklaringsbiblioteket tre automatiske skabelontyper, der fungerer med de data, du har navnmærket i dine eksempelfiler:

- Efter etiket: De ord eller tegn, der forekommer efter etiketterne i eksempelfilerne.
- Før etiket: De ord eller tegn, der forekommer før etiketterne i eksempelfilerne.
- Etiketter: Op til de første 10 etiketter fra eksempelfilerne.

For at give dig et eksempel på, hvordan automatiske skabeloner fungerer, bruger vi skabelonen Forklaring før etiket til at give modellen flere oplysninger for at få et mere nøjagtigt match.

![Eksempelfil.](../media/content-understanding/before-label.png)

Når du vælger skabelonen Forklaring før etiket, søger den efter det første sæt ord, der vises før navnet i eksempelfilerne. I eksemplet er sættet af ord, der identificeres i den første eksempelfil, "Fra og med".

![Før etiketskabelon.](../media/content-understanding/before-label-explanation.png)

Du kan vælge **Tilføj for** at oprette en forklaring fra skabelonen. Efterhånden som du tilføjer flere eksempelfiler, bliver flere ord identificeret og føjet til listen over udtryk.

![Tilføj etiketten.](../media/content-understanding/before-label-add.png)

## <a name="use-a-template-from-the-explanation-library"></a>Brug en skabelon fra forklaringsbiblioteket

1. På sektionen **Forklaringer** på modellens Tog-side **skal** du vælge **Ny** og derefter vælge **Fra en skabelon**.

   ![Tilføj før etiket.](../media/content-understanding/from-template.png)

2.  På siden **Forklaringsskabeloner** skal du vælge den forklaring, du vil bruge, og derefter vælge **Tilføj**.

    ![Vælg en skabelon.](../media/content-understanding/phone-template.png)

3. Oplysningerne for den valgte skabelon vises på siden **Opret en** forklaring. Hvis det er nødvendigt, kan du redigere forklaringsnavnet og tilføje eller fjerne elementer fra listen over udtryk.

    ![Rediger skabelon.](../media/content-understanding/phone-template-live.png)

4. Vælg Gem, når du **er færdig**.

## <a name="save-a-template-to-the-explanation-library"></a>Gemme en skabelon i forklaringsbiblioteket

Du kan gemme en forklaring som en skabelon for at gøre den tilgængelig i forklaringsbiblioteket i et indholdscenter, der kan bruges sammen med andre modeller. Skabelonen indeholder de grundlæggende og avancerede indstillinger for forklaringen, med undtagelse af muligheden for at angive, hvor sætningerne vises i et dokument.

> [!NOTE]
> Forklaringer for udtrykslisten og regulære udtryk kan kun gemmes som en skabelon.

1. På sektionen **Forklaringer** på modellens **Tog-side** :

   a. På listen over forklaringer skal du vælge den, du vil gemme som en skabelon.

   b. Vælg **Gem som skabelon**.

    ![Skærmbillede af afsnittet Forklaringer, der viser indstillingen Gem som skabelon.](../media/content-understanding/explanation-save-as-template.png)

2. På siden **Gem forklaringsskabelon** :

   a. **Omdøb forklaringen**, hvis det er nødvendigt, i sektionen Navn.

   b. I sektionen **Beskrivelse skal** du tilføje en beskrivelse for at fortælle andre, hvordan de bruger forklaringen.

   c. Vælg **Gem**.

    ![Skærmbillede af siden Gem forklaringsskabelon.](../media/content-understanding/save-explanation-template.png)

### <a name="see-also"></a>Se også

[Forklaringstyper i SharePoint Syntex](explanation-types-overview.md)