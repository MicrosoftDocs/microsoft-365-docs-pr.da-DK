---
title: Opret brugerdefinerede nyttedata til kursus i angrebssimulering
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Administratorer kan få mere at vide om, hvordan de opretter brugerdefinerede nyttedata til oplæring i simulering af angreb i Microsoft Defender for Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: f0f91eb3936d1dc4ed6c028552b37fecb5df2ff6
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648299"
---
# <a name="create-custom-payloads-for-attack-simulation-training-in-defender-for-office-365"></a>Opret brugerdefinerede nyttedata til oplæring i simulering af angreb i Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for** [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

I oplæringen af simulering af angreb er en _nyttedata_ den phishing-mail og de websider, der præsenteres for brugerne i simuleringer. Træning i simulering af angreb i Microsoft 365 E5 eller Microsoft Defender for Office 365 Plan 2 tilbyder et robust indbygget nyttedatakatalog til de tilgængelige socialtekniske teknikker. Det kan dog være en god idé at oprette brugerdefinerede nyttedata, der fungerer bedre for din organisation.

I denne artikel beskrives det, hvordan du opretter dine egne nyttedata i oplæringen af simulering af angreb. Du kan oprette brugerdefinerede nyttedata på følgende placeringer:

- Fanen **Nyttedata**: På portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til fanen **Mail & samarbejde** \> om oplæring af **oplæringsnyttedata** \> til **angrebssimulering**. Hvis du vil gå direkte til fanen **Nyttedata**, skal du bruge <https://security.microsoft.com/attacksimulator?viewid=payload>.
- Under oprettelse af simulering: Du kan oprette brugerdefinerede nyttedata på siden **Vælg en nyttedata** (den tredje side) i guiden til oprettelse af simulering. Du kan få flere oplysninger under [Simuler et phishing-angreb i Defender for Office 365](attack-simulation-training.md).

Du kan finde oplysninger om, hvordan du kommer i gang, om oplæring i simulering af angreb under [Kom i gang med at bruge oplæring i simulering af angreb](attack-simulation-training-get-started.md).

> [!NOTE]
> Visse varemærker, logoer, symboler, insignier og andre kilde-id'er modtager øget beskyttelse i henhold til lokale, statslige og føderale love og love. Uautoriseret brug af sådanne indikatorer kan straffe brugerne, herunder bøder. Men ikke en omfattende liste, dette omfatter præsidentielle, vice præsidentielle og Kongres sæler, CIA, FBI, Social Security, Medicare og Medicaid, USA Internal Revenue Service, og de olympiske lege. Ud over disse kategorier af varemærker indebærer brug og ændring af et tredjepartsmærke en indbygget risiko. Det vil være mindre risikabelt at bruge dine egne varemærker og logoer i en nyttedata, især hvor din organisation tillader brugen. Hvis du har yderligere spørgsmål om, hvad der er eller ikke er hensigtsmæssigt at bruge, når du opretter eller konfigurerer en nyttedata, bør du kontakte dine juridiske rådgivere.

## <a name="create-a-payload"></a>Opret en nyttedata

Når du har klikket på ![Opret et nyttedataikon.](../../media/m365-cc-sc-create-icon.png) **Opret en nyttedata** fra fanen **Nyttedata** i oplæringen af simulering af angreb eller på siden **[Vælg en nyttedata](attack-simulation-training.md#select-a-payload)** i guiden til oprettelse af simulering, starter guiden til oprettelse af nyttedata og beskrives i dette afsnit.

### <a name="select-a-payload-type"></a>Vælg en nyttedatatype

På siden **Vælg type** er den eneste værdi, du kan vælge i øjeblikket **Mail**.

Klik på **Næste**.

### <a name="select-a-social-engineering-technique"></a>Vælg en teknik til social engineering

På siden **Vælg teknik** er de tilgængelige indstillinger de samme som på siden [Vælg teknik](attack-simulation-training.md#select-a-social-engineering-technique) i guiden til oprettelse af simulering:

- **Høst af legitimationsoplysninger**
- **Vedhæftet malware**
- **Link i vedhæftet fil**
- **Link til malware**
- **Drev efter URL-adresse**

Klik på **Næste**, når du er færdig.

### <a name="name-and-describe-the-payload"></a>Navngiv og beskriv nyttedataene

Konfigurer følgende indstillinger på siden **Payload-navn** :

- **Navn**: Angiv et entydigt, beskrivende navn på nyttedataene.
- **Beskrivelse**: Angiv en valgfri detaljeret beskrivelse af nyttedataene.

Klik på **Næste**, når du er færdig.

## <a name="configure-the-payload"></a>Konfigurer nyttedataene

På siden **Konfigurer nyttedata** er det tid til at oprette dine nyttedata. Mange af de tilgængelige indstillinger bestemmes af det valg, du har foretaget på siden **Vælg teknik** (f.eks. links i forhold til vedhæftede filer).

- Afsnittet **Afsenderdetaljer**: Konfigurer følgende indstillinger:
  - **Fra navn**
  - **Brug fornavn som vist navn**: Denne indstilling er som standard ikke valgt.
  - **Fra mail**: Hvis du vælger en intern mailadresse til din nyttedatas afsender, ser nyttedataene ud til at komme fra en anden medarbejder. Denne afsendermailadresse øger en brugers følsomhed over for nyttedataene og hjælper med at uddanne medarbejdere i risikoen for interne trusler.
  - **Mailemne**

- Afsnittet **Oplysninger om vedhæftede filer**: Denne sektion er kun tilgængelig, hvis du har valgt **Vedhæftet malware**, **Link i vedhæftet fil** eller **Link til malware** på siden **Vælg teknik**. Konfigurer følgende indstillinger:
  - **Navngiv din vedhæftede fil**
  - **Vælg en type vedhæftet fil**: I øjeblikket er den eneste tilgængelige værdi **Docx**.

- **Link til afsnittet Vedhæftet fil** : Denne sektion er kun tilgængelig, hvis du har valgt **Link til malware** på siden **Vælg teknik** . I linket **Vælg en URL-adresse, du vil være din vedhæftede malware-fil skal du** vælge en af de tilgængelige URL-adresser (de samme URL-adresser, der er beskrevet for afsnittet **Phishing-link** ).

  Senere skal du integrere URL-adressen i meddelelsens brødtekst.

- Afsnittet **Phishinglink**: Denne sektion er kun tilgængelig, hvis du har valgt **Høst af legitimationsoplysninger**, **Link i vedhæftet fil** eller **Url-adresse til kørsel** på siden **Vælg teknik**.

  For **høst af legitimationsoplysninger** eller **URL-adresse til kørsel** er navnet på feltet **Vælg en URL-adresse, du vil være dit phishing-link**. Senere skal du integrere URL-adressen i meddelelsens brødtekst.

  For **Link i vedhæftet fil** er navnet på feltet **Vælg en URL-adresse i denne vedhæftede fil, som du vil være dit phishing-link**. Senere skal du integrere URL-adressen i den vedhæftede fil.

  Vælg en af de tilgængelige URL-værdier:
  
  - <https://www.mcsharepoint.com>
  - <https://www.attemplate.com>
  - <https://www.doctricant.com>
  - <https://www.mesharepoint.com>
  - <https://www.officence.com>
  - <https://www.officenced.com>
  - <https://www.officences.com>
  - <https://www.officentry.com>
  - <https://www.officested.com>
  - <https://www.prizegives.com>
  - <https://www.prizemons.com>
  - <https://www.prizewel.com>
  - <https://www.prizewings.com>
  - <https://www.shareholds.com>
  - <https://www.sharepointen.com>
  - <https://www.sharepointin.com>
  - <https://www.sharepointle.com>
  - <https://www.sharesbyte.com>
  - <https://www.sharession.com>
  - <https://www.sharestion.com>
  - <https://www.templateau.com>
  - <https://www.templatent.com>
  - <https://www.templatern.com>
  - <https://www.windocyte.com>

  > [!NOTE]
  > En URL-omdømmetjeneste kan identificere en eller flere af disse URL-adresser som usikre. Kontrollér tilgængeligheden af URL-adressen i dine understøttede webbrowsere, før du bruger URL-adressen i en simulering. Du kan få flere oplysninger under [URL-adresser til phishingsimulering, der er blokeret af Google Pengeskab Browsing](attack-simulation-training-faq.md#phishing-simulation-urls-blocked-by-google-safe-browsing).

- **Indholdssektion for vedhæftede filer** : Denne sektion er kun tilgængelig, hvis du har valgt **Link i vedhæftet fil** på siden **Vælg teknik** .

  Der findes en RTF-editor, som du kan bruge til at oprette indholdet i nyttedataene for den vedhæftede fil.

  Brug kontrolelementet **Phishinglink** til at føje den tidligere valgte URL-adresse til phishing til den vedhæftede fil.

- Almindelige indstillinger:
  - **Tilføj kode(r)**
  - **Tema**: De tilgængelige værdier er: **Kontoaktivering**, **Kontobekræftelse**, **Fakturering**, **Ryd op i mail**, **Modtaget dokument**, **Udgifts**, **Fax**, **Økonomirapport**, **Indgående meddelelser**, **Faktura**, **Modtaget element**, **Logonbesked**, **Post modtaget**, **Andet**, **Adgangskode**, **Betaling**, **Løn**, **Personligt tilbud**, **Karantæne** , **Fjernarbejde**, **Gennemse meddelelse**, **Sikkerhedsopdatering**, **Afbrudt tjeneste**, **Signatur påkrævet**, **Opgraderingspostkasse Storage**, **Kontrollér postkasse** eller **Voicemail**.
  - **Brand**: De tilgængelige værdier er: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid**, **Stewart Title**, **Tesco**, **Wells Fargo**, **Syrinx Cloud** eller **Andet**.
  - **Branche**: De tilgængelige værdier er: **Banking**, **Business services**, **Consumer services**, **Education**, **Energy**, **Construction**, **Consulting**, **Financial services**, **Government**, **Hospitality**, **Insurance**, **Legal**, **Courier services**, **IT**, **Healthcare**, **Manufacturing**, **Retail**, **Telecom**, **Real estate**, or **Andet**.
  - **Aktuel hændelse**: De tilgængelige værdier er **Ja** eller **Nej**.
  - **Kontroversiel**: De tilgængelige værdier er **Ja** eller **Nej**.

- **Sprogsektion** : Vælg sproget for nyttedataene. De tilgængelige værdier er: **engelsk**, **spansk**, **tysk**, **japansk**, **fransk**, **portugisisk**, **hollandsk**, **italiensk**, **svensk**, **kinesisk (forenklet)**, **norsk bokmål**, **polsk**, **russisk**, **finsk**, **koreansk**, **tyrkisk**, **ungarsk**, **hebraisk**, **thai**, **arabisk**, **vietnamesisk**, **slovakisk**, **græsk**, **indonesisk**, **rumænsk**, **slovensk**, **kroatisk**, **catalansk** eller **andet**.

- **Mailmeddelelsessektion** :

  - Du kan klikke på **Importér mail** og derefter **Vælge fil** for at importere en eksisterende meddelelsesfil i almindeligt tekstformat.

  - Under fanen **Tekst** er der en RTF-editor tilgængelig, hvor du kan oprette nyttedata for mailmeddelelser.

    - Brug kontrolelementet **Dynamic tag** til at tilpasse mailen for hver bruger ved at indsætte de tilgængelige mærker:
      - **Indsæt navn**: Den værdi, der tilføjes i meddelelsens brødtekst, er `${userName}`.
      - **Indsæt mail**: Den værdi, der tilføjes i meddelelsens brødtekst, er `${emailAddress}`.

      :::image type="content" source="../../media/attack-sim-training-payloads-configure-payload-email-message.png" alt-text="Afsnittet Mailmeddelelse på siden Konfigurer nyttedata i guiden til oprettelse af nyttedata i oplæring i simulering af angreb i Microsoft Defender for Office 365" lightbox="../../media/attack-sim-training-payloads-configure-payload-email-message.png":::

      Kontrolelementet **Phishinglink**: Dette kontrolelement er kun tilgængeligt, hvis du har valgt **Høst af legitimationsoplysninger**, **Link i vedhæftet fil** eller **Drive-by URL-adresse** på siden **Vælg teknik**. Brug dette kontrolelement til at indsætte den URL-adresse, du tidligere har valgt i afsnittet **Phishinglink** .

      Linkkontrol for **vedhæftet malware**: Dette kontrolelement er kun tilgængeligt, hvis du har valgt **Link til malware** på siden **Vælg teknik**. Brug dette kontrolelement til at indsætte den URL-adresse, du tidligere har valgt, i afsnittet **Link til vedhæftet fil** .

      Hvis du klikker på **Phishing-link** eller **Link til vedhæftet malware**, åbnes der en dialogboks, hvor du bliver bedt om at navngive linket. Klik på **Bekræft**, når du er færdig.

      Den værdi, der tilføjes i meddelelsens brødtekst (synlig under fanen **Kode** ) er `<a href="${phishingUrl}" target="_blank">Name value you specified</a>`.

  - Under fanen **Kode** kan du få vist og redigere HTML-koden direkte. Formatering og andre kontrolelementer, **f.eks****. dynamisk kode** og phishinglink eller **link til vedhæftede malware-filer**, er ikke tilgængelige.

  - Til/ **fra-knappen Erstat alle links i mailen med phishinglinket** er kun tilgængelig, hvis du har valgt **Høst af legitimationsoplysninger**, **Link til malware** eller **Url-adresse til kørsel** på siden **Vælg teknik** . Denne til/fra-knap kan spare tid ved at erstatte alle links i meddelelsen med det tidligere valgte **phishinglink** eller link for URL-adressen **til vedhæftede filer** . Det gør du ved at slå indstillingen til til/fra-ikonet til ![.](../../media/scc-toggle-on.png).

Klik på **Næste**, når du er færdig.

## <a name="add-indicators-to-phishing-clues"></a>Føj indikatorer til phishing-spor

> [!NOTE]
> Indikatorer er ikke tilgængelige, hvis du har valgt **Vedhæftet malware** eller **Link til malware** på siden **Vælg teknik** .

Indikatorer hjælper medarbejdere med at gennemgå simuleringen af angreb for at identificere tegn på phishing-meddelelser.

Klik på **Tilføj indikator** på siden **Tilføj indikatorer**. Konfigurer følgende indstillinger på det pop op-vindue, der vises:

- **Indikatornavn** og **indikatorplacering**: Disse værdier er indbyrdes forbundne. Hvor du kan placere indikatoren, afhænger af selve indikatoren. De tilgængelige værdier er beskrevet i følgende tabel:

  |Indikatornavn|Indikatorplacering|
  |---|---|
  |**Type af vedhæftet fil**|Meddelelsestekst|
  |**Distraherende detaljer**|Meddelelsestekst|
  |**Domænespoofing**|Meddelelsestekst <p> Fra mailadresse|
  |**Generisk hilsen**|Meddelelsestekst|
  |**Humanitære appeller**|Meddelelsestekst|
  |**Inkonsekvens**|Meddelelsestekst|
  |**Manglende afsenderoplysninger**|Meddelelsestekst|
  |**Juridisk sprog**|Meddelelsestekst|
  |**Tidsbegrænset tilbud**|Meddelelsestekst|
  |**Logoimitation eller dateret branding**|Meddelelsestekst|
  |**Efterligner et arbejde eller en forretningsproces**|Meddelelsestekst|
  |**Ingen/minimal branding**|Meddelelsestekst|
  |**Udgør som ven, kollega, vejleder, eller autoritet figur**|Meddelelsestekst|
  |**Anmodning om følsomme oplysninger**|Meddelelsestekst|
  |**Sikkerhedsindikatorer og -ikoner**|Meddelelsestekst <p> Meddelelsesemne|
  |**Afsenders viste navn og mailadresse**|Fra navn <p> Fra mailadresse|
  |**Følelse af uopsættelighed**|Meddelelsestekst <p> Meddelelsesemne|
  |**Stave- og grammatikfejl**|Meddelelsestekst <p> Meddelelsesemne|
  |**Truende sprog**|Meddelelsestekst <p> Meddelelsesemne|
  |**For godt til at være sande tilbud**|Meddelelsestekst|
  |**Uprofessionelt udseende design eller formatering**|Meddelelsestekst|
  |**URL-link**|Meddelelsestekst|
  |**Du er noget særligt**|Meddelelsestekst|
  
  Denne liste er udvalgt til at indeholde de mest almindelige spor, der vises i phishing-meddelelser.

  Hvis du vælger emnet i mailen eller meddelelsesteksten som indikatorens placering, er knappen **Vælg tekst** tilgængelig. Klik på denne knap for at markere teksten i meddelelsens emne eller meddelelsestekst, hvor indikatoren skal vises. Klik på **Vælg**, når du er færdig.

  :::image type="content" source="../../media/attack-sim-training-payloads-add-indicators-select-location.png" alt-text="Placeringen Markeret tekst i meddelelsesteksten, der skal føjes til en indikator i guiden til oprettelse af nyttedata under oplæring i simulering af angreb" lightbox="../../media/attack-sim-training-payloads-add-indicators-select-location.png":::

  - **Indikatorbeskrivelse**: Du kan acceptere standardbeskrivelsen for indikatoren, eller du kan tilpasse den.

  - **Eksempel på indikator**: Klik i dette afsnit for at se, hvordan den aktuelle indikator ser ud.

  Når du er færdig, skal du klikke på **Tilføj**

Gentag trinnene i dette afsnit for at tilføje flere indikatorer.

Hvis du vil redigere en eksisterende indikator, skal du vælge den på listen og derefter klikke på ![Ikonet Rediger indikator.](../../media/m365-cc-sc-edit-icon.png) **Rediger nyttedata**.

Hvis du vil slette en eksisterende indikator, skal du vælge den på listen og derefter klikke på ![Ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) **Slet**.

Klik på **Næste**, når du er færdig.

## <a name="review-payload"></a>Gennemse nyttedata

På siden **Gennemse nyttedata** kan du gennemse oplysningerne om dine nyttedata.

Klik på ikonet ![Send en test.](../../media/m365-cc-sc-send-icon.png) **Send en testknap** for at sende en kopi af nyttedatamailen til dig selv (den bruger, der i øjeblikket er logget på) til inspektion.

Klik på ikonet ![eksempelindikator.](../../media/m365-cc-sc-open-icon.png) **Knappen Eksempelindikator** åbner nyttedataene i et eksempel på et pop op-vindue. Prøveversionen indeholder alle de nyttedataindikatorer, du har oprettet.

På hovedsiden **Gennemse nyttedata** kan du vælge **Rediger** i hvert afsnit for at redigere indstillingerne i sektionen. Du kan også klikke på **Tilbage** eller vælge den specifikke side i guiden.

Klik på **Send**, når du er færdig. Klik på **Udført** på den bekræftelsesside, der vises.

:::image type="content" source="../../media/attack-sim-training-payloads-review-payload.png" alt-text="Siden Gennemse nyttedata i Oplæring af simulering af angreb på portalen Microsoft 365 Defender" lightbox="../../media/attack-sim-training-payloads-review-payload.png":::

> [!IMPORTANT]
> De nyttedata, du har oprettet, har værdien **Lejer** for egenskaben **Source** . Når du opretter simuleringer og vælger nyttedata, skal du sørge for, at du ikke filtrerer **lejeren for kildeværdien** fra.

## <a name="related-links"></a>Relaterede links

[Kom i gang med at bruge kursus i angrebssimulering](attack-simulation-training-get-started.md)

[Opret en simulering af phishingangreb](attack-simulation-training.md)

[Få indsigt via kursus i angrebssimulering](attack-simulation-training-insights.md)
