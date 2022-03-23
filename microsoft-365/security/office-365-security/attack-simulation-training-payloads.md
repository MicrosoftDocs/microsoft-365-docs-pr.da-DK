---
title: Opret brugerdefinerede nyttedata til simulering af angrebssimulering
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
description: Administratorer kan få mere at vide om, hvordan du opretter brugerdefinerede nyttedata til simulering af angreb i Microsoft Defender Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: df939ac031035f8771314bc1941bf44535d65610
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63591114"
---
# <a name="create-custom-payloads-for-attack-simulation-training-in-defender-for-office-365"></a>Opret brugerdefinerede nyttedata til dine angrebssimuleringskurser i Defender Office 365

**Gælder for** [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

I kursus i _angrebssimulering er_ en nyttedata phishingmail og websider, der præsenteres for brugere i simulering. Kursus om angrebssimulering i Microsoft 365 E5 eller Microsoft Defender for Office 365 Plan 2 har et robust, indbygget nyttedatakatalog til de tilgængelige social engineering-teknikker. Det kan dog være en ide at oprette brugerdefinerede nyttedata, der fungerer bedre for din organisation.

Denne artikel beskriver, hvordan du opretter dine egne nyttedata i simulering af angreb. Du kan oprette brugerdefinerede nyttedata på følgende placeringer:

- Fanen **Nyttedata**: I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til fanen **Mail & til** \>  \> simulering af **angrebssimulering af nyttedata**. For at gå direkte til **fanen Nyttedata skal** du bruge <https://security.microsoft.com/attacksimulator?viewid=payload>.
- Under oprettelse af simulering: Du kan oprette brugerdefinerede nyttedata på siden Vælg en nyttedata (tredje side) i guiden til oprettelse af simulering. Du kan få mere at vide [under Simulere et phishingangreb i Defender Office 365](attack-simulation-training.md).

Du kan finde oplysninger om kursus i at simulere angreb i [Kom i gang med at bruge simulering af angreb](attack-simulation-training-get-started.md).

> [!NOTE]
> Visse varemærker, logoer, symboler, insignias og andre kildeidentifikatorer får en bedre beskyttelse i henhold til lokale, statslige og føderale love. Uautoriseret brug af sådanne indikatorer kan gøre det ulovligt for brugerne, herunder kriminelle fines. Selvom det ikke er en omfattende liste, omfatter dette selektorer, Der er tilsnørlige, vice-, sele sæler, CIA, SOCIAL Security, Medicare og Medicaid, UNITED States Internal Revenue Service og OL. Ud over disse kategorier af varemærker har anvendelse og ændring af tredjeparts varemærker en forbundet risiko. Det vil være mindre risikabelt at anvende dine egne varemærker og logoer i en nyttelast, især hvis din organisation tillader brug. Hvis du har yderligere spørgsmål om, hvad der er eller ikke er relevant at bruge, når du opretter eller konfigurerer en nyttedata, skal du rådføre dig med dine juridiske rådgivere.

## <a name="create-a-payload"></a>Opret en nyttedata

Når du har klikket ![på Opret et nyttedataikon.](../../media/m365-cc-sc-create-icon.png) **Opret en nyttedata** fra fanen Nyttedata i simulering **af** angreb eller på siden **[](attack-simulation-training.md#select-a-payload)** Vælg en nyttedata i guiden til oprettelse af simulering, starter guiden til oprettelse af nyttedata og er beskrevet i dette afsnit.

### <a name="select-a-payload-type"></a>Vælg en nyttedatatype

På siden **Vælg type** er den eneste værdi, du aktuelt kan vælge, **Mail**.

Klik på **Næste**.

### <a name="select-a-social-engineering-technique"></a>Vælg en social tekniker

På siden **Vælg teknik** er de tilgængelige indstillinger de samme som på siden [Vælg](attack-simulation-training.md#select-a-social-engineering-technique) teknik i guiden til oprettelse af simulering:

- **Indsamling af legitimationsoplysninger**
- **Vedhæftet malware**
- **Link i vedhæftet fil**
- **Link til malware**
- **Drive-by URL**

Klik på Næste, når du er **færdig**.

### <a name="name-and-describe-the-payload"></a>Navngive og beskrive nyttedata

På siden **Navn på nyttedata** skal du konfigurere følgende indstillinger:

- **Navn**: Angiv et entydigt, beskrivende navn til nyttedata.
- **Beskrivelse**: Angiv en valgfri detaljeret beskrivelse af nyttedata.

Klik på Næste, når du er **færdig**.

## <a name="configure-the-payload"></a>Konfigurer nyttedata

På siden **Konfigurer nyttedata** er det tid til at opbygge din nyttedata. Mange af de tilgængelige indstillinger bestemmes af det valg, du har foretaget på siden **Udvælgelsesteknik** (f.eks. links vs. vedhæftede filer).

- **Sektionen Afsenderdetaljer** : Konfigurer følgende indstillinger:
  - **Fra navn**
  - **Brug fornavn som vist navn**: Denne indstilling er som standard ikke valgt.
  - **Fra mail**: Hvis du vælger en intern mailadresse til afsenderen af din nyttedata, vil nyttedataet se ud som om, den kommer fra en kollega. Denne afsendermailadresse vil gøre en bruger udsat for nyttedata og hjælpe med at informere medarbejderne om risikoen for interne trusler.
  - **Mailens emne**

- **Sektionen Detaljer om** vedhæftede filer: Denne sektion er kun tilgængelig, hvis du har valgt vedhæftet **Malware****, Link** i vedhæftet fil eller **Link til malware** på **siden Udvælgelsesteknik**. Konfigurer følgende indstillinger:
  - **Navngive den vedhæftede fil**
  - **Vælg en vedhæftet type**: I øjeblikket er den eneste tilgængelige værdi **Docx**.

- **Link til sektionen med** vedhæftede filer: Denne sektion er kun tilgængelig, hvis du **har valgt Link til malware** på **siden Vælg** teknik. I feltet Vælg en URL-adresse, der skal være din **vedhæftede malware-link** skal du vælge en af de tilgængelige URL-adresser (de samme URL-adresser, der er beskrevet for **afsnittet Phishing-link** ).

  Senere skal du integrere URL-adressen i meddelelsens brødtekst.

- **Sektionen phishinglink** : Denne sektion er kun tilgængelig, hvis du har valgt Indsamling af legitimationsoplysninger **,** **Link** i vedhæftet fil eller **Drev efter URL på** **siden Udvælgelsesteknik** .

  Til **indsamling af** legitimationsoplysninger **eller Drev efter URL-adresse** er navnet på feltet Vælg en **URL-adresse, der skal være dit phishing-link**. Senere skal du integrere URL-adressen i meddelelsens brødtekst.

  For **Link i vedhæftet** fil er navnet på feltet Vælg en URL-adresse i denne vedhæftede fil **, som skal være dit phishinglink**. Senere skal du integrere URL-adressen i den vedhæftede fil.

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
  > En URL-rytjeneste kan identificere en eller flere af disse URL-adresser som usikre. Kontrollér tilgængeligheden af URL-adressen i dine understøttede webbrowsere, før du bruger URL-adressen i en simulering. Få mere at vide under [URL-adresser til phishing-simulering blokeret af Google Pengeskab browsing](attack-simulation-training-faq.md#phishing-simulation-urls-blocked-by-google-safe-browsing).

- **Sektionen Vedhæftet** indhold: Denne sektion er kun tilgængelig, hvis du har valgt **Link i vedhæftet** fil på **siden Vælg** teknik.

  Du kan bruge RTF-editoren til at oprette indholdet i filens vedhæftede fil.

  Brug **kontrolelementet til phishinglinket** til at tilføje den tidligere valgte phishing-URL-adresse i den vedhæftede fil.

- Almindelige indstillinger:
  - **Tilføj mærker**
  - **Tema**: De tilgængelige værdier **er:** Kontoaktivering **,** Kontobekræftelse, **Fakturering**, Oprydning af **mail****, Dokument** **modtaget, Udgift**, **Fax****, Økonomirapport****, Indgående** **meddelelser, Faktura****, Modtaget** **post,** **Logonbesked, Mail** modtaget, **Anden**, **Adgangskode****, Betaling****, Løn**, Personlig **tilbud**, **Karantæne** , **Fjernarbejde**, **Gennemse meddelelse****,** Sikkerhedsopdatering, **Afbrudt** tjeneste, **Påkrævet signatur**, **Opgrader Storage****,** Bekræft postkasse eller **Telefonsvarer**.
  - **Brand**: De tilgængelige værdier er: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid**, **title**, **Tesco**, **Wells Fargo**, **Syrinx Cloud** eller **Andre**.
  - **Branche**: De tilgængelige værdier er: **Bank****,** forretningstjenester **,** forbrugertjenester, **Uddannelse**, **Energi****, Konstruktion**, **Rådgivning****, Finansielle** tjenester, **Government**, **Construction**, **Insurance**, **Legal**, **Courier services**, **IT**, **Healthcare**, **Manufacturing**, **Retail**, **Telecom**, **Real Estate**, or **Andet**.
  - **Aktuel hændelse**: De tilgængelige værdier er **Ja** eller **Nej**.
  - **Til** rådighed: De tilgængelige værdier er **Ja** eller **Nej**.

- **Sektionen** Sprog: Vælg sproget for nyttedata. De tilgængelige værdier **er: engelsk****, spansk****, tysk****, japansk****, fransk****, portugisisk****, hollandsk****, italiensk****, svensk**, kinesisk **(** forenklet), norsk **bokmål****, polsk****, russisk**, **finsk****,** koreansk **, tyrkisk**, **ungarsk****, hebraisk****,** **thai**, arabisk, **vietnamesisk****, slovakisk**, **græsk**, **indonesisk**, rumænsk **,** **slovensk, kroatisk**, **catalansk** eller **anden**. 

- **Mailmeddelelsessektion** :

  - Du kan klikke på **Importér mail** og **derefter på Vælg fil** for at importere en eksisterende meddelelsesfil i almindelig tekst.

  - På fanen **Tekst** kan du bruge et RTF-editor til at oprette din mail som nyttedata.

    - Brug Dynamisk **kodekontrolelement** til at tilpasse mailen for hver bruger ved at indsætte de tilgængelige mærker:
      - **Indsæt navn**: Den værdi, der tilføjes i meddelelsens brødtekst, er `${userName}`.
      - **Indsæt mail**: Den værdi, der tilføjes i meddelelsens brødtekst, er `${emailAddress}`.

      ![Afsnittet Mail på siden Konfigurer nyttedata i guiden til oprettelse af nyttedata i Kursus i angrebssimulering i Microsoft Defender for Office 365.](../../media/attack-sim-training-payloads-configure-payload-email-message.png)

      **Kontrolelement for phishinglink** : Dette kontrolelement er kun tilgængeligt **, hvis** du har valgt Indsamling af legitimationsoplysninger **, Link** i vedhæftet fil eller **Drev efter URL på** **siden Udvælgelsesteknik** . Brug dette kontrolelement til at indsætte den URL-adresse, du tidligere har valgt i **afsnittet Phishing-link** .

      **Kontrolelement for link til** vedhæftede malware: Dette kontrolelement er kun tilgængeligt, hvis du har valgt **Link til malware** på **siden Vælg** teknik. Brug dette kontrolelement til at indsætte den URL-adresse, du tidligere har valgt i **afsnittet Link til vedhæftet** fil.

      Hvis du klikker på **linket Phishing eller** **linket til vedhæftede malwares**, åbnes en dialogboks, hvor du bliver bedt om at navngive linket. Klik på Bekræft, når du er **færdig**.

      Den værdi, der tilføjes i meddelelsens brødtekst (kan ses under **fanen** Kode) er `<a href="${phishingUrl}" target="_blank">Name value you specified</a>`.

  - På fanen **Kode** kan du få vist og redigere HTML-koden direkte. Formatering og andre kontrolelementer som **f.eks. Dynamisk mærke** **og Phishing-link** **eller linket til vedhæftede malware** er ikke tilgængelige.

  - Til/fra-knappen Erstat alle links i mailen med **phishing-linket** er kun **tilgængelig, hvis** du har valgt indsamling af legitimationsoplysninger, **Link til malware** eller **Drev efter URL på** siden **Vælg** teknik. Denne indstilling kan spare tid ved at erstatte alle links i meddelelsen med det tidligere valgte **Phishing-link** eller **Link til URL-adresse til vedhæftede** filer. Det gør du ved at slå indstillingen til til ![til-ikon til](../../media/scc-toggle-on.png).

Klik på Næste, når du er **færdig**.

## <a name="add-indicators-to-phishing-clues"></a>Føj indikatorer til phishing-ledetråde

> [!NOTE]
> Indikatorer er ikke tilgængelige, hvis du har valgt **vedhæftet malware** **eller Link til malware** på **siden Udvælgelsesteknik** .

Indikatorer hjælper medarbejdere, der går gennem angrebssimulering, med at identificere id-tegn på phishingmeddelelser.

Klik på **Tilføj indikator** på siden **Tilføj symboler**. I pop op-menuen, der vises, skal du konfigurere følgende indstillinger:

- **Indikatornavn** **og Indikatorplacering**: Disse værdier er indbyrdes forbundne. Hvor du kan placere indikatoren, afhænger af selve indikatoren. De tilgængelige værdier er beskrevet i følgende tabel:

  <br>

  ****

  |Indikatornavn|Indikatorplacering|
  |---|---|
  |**Type af vedhæftet fil**|Meddelelsestekst|
  |**Distraherende detaljer**|Meddelelsestekst|
  |**Domænespoofing**|Meddelelsestekst <p> Fra mailadresse|
  |**Standardhilsen**|Meddelelsestekst|
  |**Tiltalt, der kan være tiltalende**|Meddelelsestekst|
  |**Uoverensstemmelse**|Meddelelsestekst|
  |**Manglende afsenderoplysninger**|Meddelelsestekst|
  |**Juridisk sprog**|Meddelelsestekst|
  |**Tilbud om begrænset tid**|Meddelelsestekst|
  |**Logo af logo eller dato dato for branding**|Meddelelsestekst|
  |**Efterligner et arbejde eller en forretningsproces**|Meddelelsestekst|
  |**Ingen/minimal branding**|Meddelelsestekst|
  |**Udgør en ven, kollega, tilsynsførende eller myndighedsfigur**|Meddelelsestekst|
  |**Anmodning om følsomme oplysninger**|Meddelelsestekst|
  |**Sikkerhedsindikatorer og ikoner**|Meddelelsestekst <p> Meddelelses emne|
  |**Afsenders viste navn og mailadresse**|Fra navn <p> Fra mailadresse|
  |**Det haster**|Meddelelsestekst <p> Meddelelses emne|
  |**Stave- og grammatikfejl**|Meddelelsestekst <p> Meddelelses emne|
  |**Sprog, der sprog, der sprog,**|Meddelelsestekst <p> Meddelelses emne|
  |**For gode tilbud til at være sande**|Meddelelsestekst|
  |**Upprofessionalt udseende design eller formatering**|Meddelelsestekst|
  |**Link til URL-adresse**|Meddelelsestekst|
  |**Du er speciel**|Meddelelsestekst|
  |
  
  Denne liste er curated to contain the most common clues that appear in phishing messages.

  Hvis du vælger mailens emne eller brødteksten som placering for indikatoren, er **knappen Markér** tekst tilgængelig. Klik på denne knap for at markere teksten i meddelelsens emne eller brødtekst, hvor indikatoren skal vises. Klik på Vælg, når du er **færdig**.

  ![Markeret tekstplacering i meddelelsesteksten, som skal føjes til en indikator i guiden til oprettelse af nyttedata i guiden til simulering af angreb.](../../media/attack-sim-training-payloads-add-indicators-select-location.png)

  - **Indikatorbeskrivelse**: Du kan acceptere standardbeskrivelsen for indikatoren, eller du kan tilpasse den.

  - **Indikatoreksempel**: Klik i denne sektion for at se, hvordan den aktuelle indikator ser ud.

  Når du er færdig, skal du klikke på **Tilføj**

Gentag trinnene i dette afsnit for at tilføje flere indikatorer.

Hvis du vil redigere en eksisterende indikator, skal du markere den på listen og derefter klikke på ![Rediger indikatorikon.](../../media/m365-cc-sc-edit-icon.png) **Rediger nyttedata**.

Hvis du vil slette en eksisterende indikator, skal du markere den på listen og derefter klikke på ![Slet ikon.](../../media/m365-cc-sc-delete-icon.png) **Slet**.

Klik på Næste, når du er **færdig**.

## <a name="review-payload"></a>Gennemse nyttedata

På siden **Gennemse nyttedata** kan du gennemgå oplysningerne om din nyttedata.

Klik på ![ikonet Send en test.](../../media/m365-cc-sc-send-icon.png) **Send en testknap** for at sende en kopi af nyttedatamailen til dig selv (den bruger, der er logget på i øjeblikket) for undersøgelse.

Klik på ikonet ![Eksempelindikator.](../../media/m365-cc-sc-open-icon.png) **Eksempelindikatorknappen** åbner nyttedata i en forhåndsvisnings pop op-pop-op-knap. Eksemplet indeholder alle indikatorer for nyttedata, som du har oprettet.

På hovedsiden **Gennemse nyttedata** kan du vælge **Rediger** i hver sektion for at ændre indstillingerne i sektionen. Eller du kan klikke **på** Tilbage eller vælge den bestemte side i guiden.

Klik på Send, når du er **færdig**. Klik på Udført på bekræftelsessiden, der **vises**.

![Gennemse siden med nyttedata i simulering af angreb i Microsoft 365 Defender portal.](../../media/attack-sim-training-payloads-review-payload.png)

> [!IMPORTANT]
> Nyttedata, du har oprettet, får værdien **Lejer** for **egenskaben** Kilde. Når du opretter simuleringer og vælger nyttedata, skal du sørge for, at du ikke filtrerer **kildeværdilejeren** **fra**.

## <a name="related-links"></a>Relaterede links

[Kom i gang med at bruge simuleringskursus til angreb](attack-simulation-training-get-started.md)

[Opret en simulering af phishingangreb](attack-simulation-training.md)

[Få indsigt via angrebssimuleringskursus](attack-simulation-training-insights.md)
