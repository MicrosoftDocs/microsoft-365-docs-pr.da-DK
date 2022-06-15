---
title: Forstå din regning eller faktura
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: amberb, vikdesai
audience: Admin
ms.topic: article
f1.keywords:
- MACBillingBillsPaymentsInvoices
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_billing
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid: MET150
description: Få mere at vide om, hvordan du læser og forstår din faktura for Microsofts forretningsprodukter.
ms.date: 05/04/2021
ms.openlocfilehash: 4d5bd00726004d0e9dce3f6d284546ba81fb7edd
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66101772"
---
# <a name="understand-your-bill-or-invoice"></a>Forstå din regning eller faktura

Fakturaen indeholder en oversigt over dine gebyrer og betalingsanvisninger. Du kan [få vist din onlinefaktura](#view-your-online-invoice) i Microsoft 365 Administration. Du kan også downloade den i Portable Document Format (.pdf) for at sende via mail.

Sådan får du vist og udskriver din faktura:

1. På siden **Faktureringsfakturaer** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">& betalinger</a> skal du vælge et datointerval for faktura.
2. Hvis du vil udskrive eller gemme en PDF-kopi af fakturaen, skal du vælge **Download faktura PDF** og derefter udskrive PDF-filen.

Du kan få mere at vide under [Få vist din faktura.](view-your-bill-or-invoice.md)

Hvis du kun har et Microsoft 365 abonnement, skal du se [Forstå din faktura for Microsoft 365 for business](understand-your-invoice2.md).

## <a name="understand-the-invoice-header"></a>Forstå fakturahovedet

Øverst på den første side identificeres, hvem der er ansvarlig for betaling, hvor regningen sendes til, og en oversigt over gebyrer.

| Udtrykket | Beskrivelse |
| --- | --- |
| Solgt til |Den faktureringskonto, der identificerer navnet og adressen på den juridiske enhed, der er ansvarlig for betalingen. Disse oplysninger kan administreres på siden <a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">Faktureringskonti</a> , hvor du kan finde kontoaftalen og administrere roller og tilladelser. |
| Fakturer til |Identificerer, hvem der modtager fakturaen. Disse oplysninger kan administreres på siden <a href="https://go.microsoft.com/fwlink/p/?linkid=2103629" target="_blank">Faktureringsprofiler</a> . Faktureringsprofilen vises også på onlinefakturasiden i afsnittet **Fakturaoversigt** . Hvis du vil vide mere om faktureringsprofiler, og hvordan du kan bruge dem til at oprette mere fleksible faktureringsmuligheder for din organisation, skal du se [Administrer faktureringsprofiler](manage-billing-profiles.md). |
| Faktureringsprofil |Navnet på den faktureringsprofil, der bruges til at definere fakturaegenskaber, f.eks **. Faktura til**, **nummer på indkøbsordre** og betalingsbetingelser. Disse oplysninger kan administreres på siden <a href="https://go.microsoft.com/fwlink/p/?linkid=2103629" target="_blank">Faktureringsprofiler</a> . Du kan få flere oplysninger om faktureringsprofiler, og hvordan du kan bruge dem til at oprette mere fleksible faktureringsmuligheder for din organisation, under [Administrer faktureringsprofiler](manage-billing-profiles.md). |
| Fakturanummer |Et entydigt, Microsoft-genereret fakturanummer, der bruges til sporingsformål. |
| Fakturadato |Den dato, hvor fakturaen genereres, typisk fem til 12 dage efter afslutningen af faktureringscyklussen. Du kan kontrollere din fakturadato på siden med oplysninger om faktureringsprofilen. Gebyrer, der opstår mellem slutningen af faktureringsperioden og fakturadatoen, medtages i fakturaen for den næste måned, da de er i den næste faktureringsperiode. Start- og slutdatoerne for faktureringsperioden for hver faktura er angivet i pdf-filen til fakturaen over **Faktureringsoversigt**.|
| Betalingsbetingelser |Sådan betaler du for din Microsoft-regning. *Netto 30 dage* betyder, at du betaler ved at følge vejledningen på din faktura inden for 30 dage efter fakturadatoen. |

## <a name="understand-the-billing-summary"></a>Forstå faktureringsoversigten

**Faktureringsoversigten** viser en oversigt over gebyrer siden den forrige faktureringsperiode, eventuelle kreditter, der blev anvendt, moms og det samlede skyldige beløb.

| Udtrykket | Beskrivelse |
| --- | --- |
| Gebyrer|Det samlede antal produkter, der er købt for denne faktureringsperiode, og deres relaterede gebyrer og skatter. Køb samles for at give en præcis visning af din faktura. |
| Kreditter |Kreditter, du har modtaget fra returneringer |
| Anvendte Azure-kreditter |Dine Azure-kreditter, der automatisk anvendes på Azure-gebyrer for hver faktureringsperiode. Hvis du ikke har nogen Azure-kreditter, er dette felt skjult. Du kan finde flere oplysninger om Azure-kreditter under [Spor Microsoft-kundeaftale Azure-kreditsaldo](/azure/billing/billing-mca-check-azure-credits-balance). |
| Subtotal |Det forfaldne beløb før skat |
| Skat |Den type og det skattebeløb, du betaler, afhængigt af landet på din faktureringsprofil. Hvis du ikke behøver at betale skat, vises der ingen skat på din faktura. |

### <a name="understand-your-charges"></a>Forstå dine gebyrer

På siderne med gebyrer vises omkostningerne opdelt efter produkt. For Azure-kunder kan gebyrerne være organiseret efter fakturasektion. Du kan få mere at vide om, hvordan fakturasektioner bruges sammen med Azure-produkter, under [Fakturasektioner](/azure/billing/billing-mca-overview#invoice-sections) i [Kom i gang med din Microsoft-kundeaftale faktureringskonto](/azure/billing/billing-mca-overview). Inden for hver produktordre opdeles omkostningerne efter servicefamilie.

| Udtrykket |Beskrivelse |
| --- | --- |
| Salgspris | Den effektive enhedspris for tjenesten (i prisvaluta), der bruges til at beregne gebyret. Denne pris er unik for et produkt, en servicefamilie, en måler og et tilbud. |
| Antal | Antal købt eller forbrugt i faktureringsperioden |
| Gebyrer/kreditter | Nettobeløb for gebyrer efter kredit/refusioner anvendes |
| Azure-kredit | Mængden af Azure-kreditter, der er anvendt på gebyrer/kreditter |
| Skattesats | Skattesats, afhængigt af landet |
| Momsbeløb | Det momsbeløb, der anvendes på købet baseret på momssats |
| I alt | Det samlede beløb, der forfalder til købet |

Detaljer om linjeelementer varierer afhængigt af den produkttype, du faktureres for. For Azure-produkter vises mængden af anvendte Azure-kreditter f.eks. Sædebaserede produkter viser en enhedspris og mængde. Fakturaoplysningerne viser de købte produkter, rabat eller kreditter, der er anvendt, momssats og beløb samt totalerne for linjeelementet.

> I alt = Gebyrer – Azure Credit + Tax

Det samlede beløb, der forfalder for hver tjenestefamilie, beregnes ved at trække Azure-kreditter fra kreditter/gebyrer og tilføje moms:

> I alt = Gebyrer/kreditter – Azure Credit + Tax

Hvis der er Azure-gebyrer på din faktura, som du gerne vil have flere oplysninger om, skal du se [Gennemse din Microsoft-kundeaftale faktura](/azure/cost-management-billing/understand/review-customer-agreement-bill).

## <a name="understand-the-last-invoice-page"></a>Forstå den sidste fakturaside

### <a name="payment-instructions"></a>Betalingsanvisninger

Nederst på fakturaen kan du se en vejledning i, hvordan du betaler din regning. Du kan betale via kabel, check eller online.

### <a name="publisher-information"></a>Publisher oplysninger

Hvis du har tredjepartstjenester i din faktura, vises navn og adresse på hver udgiver nederst på din faktura.

## <a name="view-your-online-invoice"></a>Få vist din onlinefaktura

Fakturaer er tilgængelige online. Du kan få et link til din onlinefaktura via din PDF-faktura og fra en mailmeddelelse. Onlinefakturaen kan udvides, så du kan få vist gebyrerne på din faktura og se flere oplysninger om hver vare. Onlinefakturaen indeholder:

- **Prisoplysninger**&mdash; Yderligere oplysninger, herunder oplysninger om rabatter og produktpriser.
- **Onlinebetaling**&mdash; Du kan vælge at foretage en betaling online fra fakturaen.
- **Azure Cost Management**&mdash; For Azure-kunder indeholder onlinefakturaer et link til Azure Cost Management.

### <a name="to-view-your-online-invoice"></a>Sådan får du vist din onlinefaktura

1. I Administration skal du gå til siden **Fakturering** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Fakturaer og betalinger</a>.
2. Hvis du vil downloade den .pdf version af din faktura, skal du vælge **Download pdf-faktura** i rækken for den faktura, du vil se.
3. Hvis du vil have vist din onlinefaktura, skal du vælge en faktura på listen. Du kan også downloade .pdf fra siden med fakturaoplysninger.

## <a name="invoice-faq"></a>Ofte stillede spørgsmål om faktura

### <a name="when-is-my-invoice-available"></a>Hvornår er min faktura tilgængelig?

Nogle fakturaer genereres inden for 24 timer efter købet. Andre fakturaer genereres i slutningen af faktureringsperioden og omfatter alle elementer fra den pågældende periode.

### <a name="how-do-i-pay-the-amount-due-on-my-invoice"></a>Hvordan gør jeg betale det beløb, der er skyldigt på min faktura?

Betalingsanvisninger afhænger af din betalingsmetode og vises nederst i pdf-filen til fakturaen. Hvis din betalingsmetode er et kreditkort, opkræves den automatisk inden for 10 dage efter fakturadatoen. Hvis din betalingsmetode er ved check eller bankoverførsel, kan du se oplysningerne under **Betalingsinstruktioner** i PDF-filen.

### <a name="whats-the-difference-between-sold-to-and-bill-to-addresses"></a>Hvad er forskellen mellem "Solgt til" og "Fakturer til"-adresser?

- **Solgt til:** Den juridiske enhed, der er ansvarlig for betalingen og identificeret på fakturaen. Den adresse, der angives her, bruges til at bestemme din skattesats, medmindre du vælger at angive en alternativ leveringsadresse under dit køb. Du kan få flere oplysninger under [Skatteoplysninger](tax-information.md).
- **Faktura til:** Den adresse, hvor den fysiske faktura sendes, hvis det er relevant. Der kan være flere **Faktureringsadresser** pr. juridisk enhed, men kun én **Faktura til** adresse pr. faktureringsprofil.

### <a name="what-are-billed-amount-and-amount-due"></a>Hvad er "Faktureret beløb" og "Skyldigt beløb?"

- **Faktureret beløb:** Det samlede beløb for det køb, du har foretaget.
- **Skyldigt beløb:** Den resterende saldo for det, du skylder.

### <a name="what-is-the-difference-between-service-period-and-billing-period"></a>Hvad er forskellen mellem "'Serviceperiode" og "Faktureringsperiode?"

- **Serviceperiode:** Den tidsperiode, hvor du skal betale for at bruge tjenesten.
- **Faktureringsperiode:** Tidsperioden siden sidste fakturadato.

### <a name="why-dont-i-see-azure-prepayment-as-a-payment-method"></a>Hvorfor kan jeg ikke se Azure-forudbetaling som en betalingsmetode?

Azure-forudbetaling er kun tilgængelig som en betalingsmetode for berettigede Azure-produkter og -tjenester

## <a name="need-help-contact-support"></a>Har du brug for hjælp? Kontakt support

Hvis du har spørgsmål eller har brug for hjælp til dine Azure-kreditter, <a href="https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest" target="_blank">kan du oprette en supportanmodning med Azure-support</a>.

Hvis du har spørgsmål eller har brug for hjælp til din faktura i Microsoft 365 Administration, [kan du kontakte support til forretningsprodukter](../../admin/get-help-support.md).

## <a name="related-content"></a>Relateret indhold

[Forstå din faktura for Microsoft 365 for business](understand-your-invoice2.md) (artikel)\
[Spor Microsoft-kundeaftale Azure-kreditsaldo](/azure/billing/billing-mca-check-azure-credits-balance) (artikel)\
[Gennemse din Microsoft-kundeaftale faktura](/azure/cost-management-billing/understand/review-customer-agreement-bill) (artikel)\
[Kom i gang med din Microsoft-kundeaftale faktureringskonto](/azure/billing/billing-mca-overview) (artikel)
