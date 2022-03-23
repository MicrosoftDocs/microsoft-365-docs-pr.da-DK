---
title: Forstå din regning eller faktura
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jkinma, jmueller
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
description: Få mere at vide om, hvordan du kan læse og forstå din regning eller faktura for Microsoft-virksomhedsprodukter.
ms.date: 05/04/2021
ms.openlocfilehash: ce057a9a3fc72ab1ba818047112451f984894d99
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588972"
---
# <a name="understand-your-bill-or-invoice"></a>Forstå din regning eller faktura

Fakturaen indeholder en oversigt over dine gebyrer og instruktioner om betaling. Du kan [få vist din onlinefaktura](#view-your-online-invoice) i Microsoft 365 Administration. Du kan også downloade den i Formatet Portable Document Format (.pdf), der skal sendes via mail.

Sådan får du vist og udskriver din faktura:

1. På siden <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Faktureringsfakturering</a>  >  & skal du vælge et datointerval for fakturaen.
2. Hvis du vil udskrive eller gemme en PDF-kopi af regningen, skal **du vælge Download faktura-PDF** og derefter udskrive PDF-filen.

Du kan få mere at vide [under Få vist din regning eller faktura](view-your-bill-or-invoice.md).

Hvis du kun har et Microsoft 365 abonnement, skal du [se Forstå din regning eller faktura for Microsoft 365 til virksomheder](understand-your-invoice2.md).

## <a name="understand-the-invoice-header"></a>Forstå fakturaoverskriften

Øverst på den første side kan du se, hvem der er ansvarlig for betaling, hvor fakturaen sendes til, samt en oversigt over gebyrer.

| Ord | Beskrivelse |
| --- | --- |
| Solgt til |Faktureringskontoen, der identificerer navnet og adressen på den juridiske enhed, der er ansvarlig for betaling. Disse oplysninger kan administreres på <a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">siden Faktureringskonti</a> , hvor du kan finde kontoaftalen og administrere roller og tilladelser. |
| Fakturer til |Identificerer, hvem der modtager fakturaen. Disse oplysninger kan administreres på <a href="https://go.microsoft.com/fwlink/p/?linkid=2103629" target="_blank">siden Faktureringsprofiler</a> . Faktureringsprofilen vises også på onlinefakturasiden i sektionen **Fakturaoversigt** . Hvis du vil have mere at vide om faktureringsprofiler, og hvordan du kan bruge dem til at opbygge mere fleksible faktureringsmuligheder for din organisation, skal du [se Administrere faktureringsprofiler](manage-billing-profiles.md). |
| Faktureringsprofil |Navnet på den faktureringsprofil, der bruges til at definere fakturaegenskaber som **f.eks. faktura** til, **Købsanmodningsnummer** og betalingsvilkår. Disse oplysninger kan administreres på <a href="https://go.microsoft.com/fwlink/p/?linkid=2103629" target="_blank">siden Faktureringsprofiler</a> . Du kan finde flere oplysninger om faktureringsprofiler, og hvordan du kan bruge dem til at opbygge mere fleksible faktureringsmuligheder for din organisation under [Administrere faktureringsprofiler](manage-billing-profiles.md). |
| Fakturanummer |Et entydigt Microsoft-genereret fakturanummer, der bruges til sporingsformål. |
| Fakturadato |Dato, hvor fakturaen genereres, typisk fem til 12 dage efter slutningen af faktureringscyklussen. Du kan se din fakturadato på siden med oplysninger om faktureringsprofilen. Gebyrer, der forekommer mellem slutningen af faktureringsperioden og fakturadatoen, er inkluderet i fakturaen for den næste måned, da de er i den næste faktureringsperiode. Start- og slutdatoerne for faktureringsperioden for hver faktura vises i PDF-fakturaen ovenover **Faktureringsoversigt**.|
| Betalingsbetingelser |Sådan betaler du for din Microsoft-faktura. *Netto 30 dage betyder* , at du betaler ved at følge vejledningen på din faktura inden for 30 dage efter fakturadatoen. |

## <a name="understand-the-billing-summary"></a>Forstå faktureringsoversigten

I **faktureringsoversigten** vises oversigten over gebyrer siden den forrige faktureringsperiode, alle kreditter, der blev anvendt, moms og det samlede forfaldne beløb.

| Ord | Beskrivelse |
| --- | --- |
| Gebyrer|Samlet antal produkter, der er købt i denne faktureringsperiode, og deres relaterede gebyrer og afgifter. Køb sammenlægges for at give en kortfattet oversigt over din faktura. |
| Kreditter |Kreditter, du har modtaget fra returneringer |
| Azure-kreditter anvendt |Dine Azure-kreditter, der automatisk anvendes på Azure-gebyrer hver faktureringsperiode. Hvis du ikke har nogen Azure-kreditter, er dette felt skjult. Du kan finde flere oplysninger om Azure-kreditter under [Spor Azure-kreditsaldo for Microsoft-kundeaftale](/azure/billing/billing-mca-check-azure-credits-balance). |
| Subtotal |Det forfaldne beløb før moms |
| Moms |Den type og det momsbeløb, du betaler, afhængigt af dit faktureringsprofils land. Hvis du ikke skal betale moms, vises der ingen moms på din faktura. |

### <a name="understand-your-charges"></a>Forstå dine gebyrer

Siderne med gebyrer viser omkostningerne opdelt efter produkt. For Azure-kunder kan gebyrerne være organiseret efter fakturasektion. Du kan finde flere oplysninger om, hvordan fakturassektionerne bruges med Azure-produkter, i Fakturassektionerne i Introduktion til [din Microsoft-kundeaftalefaktureringskonto](/azure/billing/billing-mca-overview).[](/azure/billing/billing-mca-overview#invoice-sections) Inden for hver produktordre er omkostningerne opdelt efter tjenestefamilie.

| Ord |Beskrivelse |
| --- | --- |
| Enhedspris | Den effektive enhedspris for tjenesten (i prisvaluta), der bruges til at beregne gebyret. Denne pris er unik for et produkt, en servicefamilie, en meter og et tilbud. |
| Antal | Købt eller forbrugt mængde i faktureringsperioden |
| Gebyrer/kreditter | Nettobeløb på gebyrer, efter at kredit/refusion er anvendt |
| Azure-kredit | Mængden af Azure-kreditter, der er anvendt på gebyrer/kreditter |
| Momssats | Momssats, afhængigt af landet |
| Momsbeløb | Det momsbeløb, der er anvendt på købet baseret på momssatsen |
| I alt | Det samlede forfaldne beløb for købet |

Detaljer om linjeelementer varierer afhængigt af den type produkt, du bliver opkrævet for. Eksempelvis vises mængden af anvendte Azure-kreditter for Azure-produkter. Sædebaserede produkter viser en enhedspris og -mængde. Fakturaoplysningerne viser de købte produkter, rabat eller kreditter, der blev anvendt, momssats og beløb samt linjeelementtotalerne.

> Total = Gebyrer - Azure-kredit + moms

Det samlede forfaldne beløb for hver tjenestefamilie beregnes ved at trække Azure-kreditter fra kreditter/gebyrer og tilføje moms:

> Total = Gebyrer/Kreditter - Azure-kredit + moms

Hvis der er Azure-gebyrer på din faktura, som du gerne vil have flere oplysninger om, skal du [se Gennemse din Microsoft-kundeaftalefaktura](/azure/cost-management-billing/understand/review-customer-agreement-bill).

## <a name="understand-the-last-invoice-page"></a>Forstå den sidste fakturaside

### <a name="payment-instructions"></a>Betalingsinstruktioner

Nederst på fakturaen finder du en vejledning i, hvordan du betaler din faktura. Du kan betale via kabel, check eller online.

### <a name="publisher-information"></a>Publisher oplysninger

Hvis du har tredjepartstjenester i din faktura, vises navnet og adressen på hver udgiver nederst på din faktura.

## <a name="view-your-online-invoice"></a>Få vist din onlinefaktura

Fakturaer er tilgængelige online. Du kan få et link til din onlinefaktura fra din PDF-faktura og fra en mailmeddelelse. Onlinefakturaen kan udvides, så du kan se gebyrerne på din faktura og få vist flere detaljer for hvert element. Onlinefakturaen indeholder:

- **Prisoplysninger**&mdash; Yderligere oplysninger, herunder detaljer om rabatter og produktpriser.
- **Onlinebetaling**&mdash; Du kan vælge at foretage en betaling online fra fakturaen.
- **Azure cost management**&mdash; For Azure-kunder omfatter onlinefakturaer et link til Azure-omkostningsstyring.

### <a name="to-view-your-online-invoice"></a>Sådan får du vist din onlinefaktura

1. I Administration skal du gå til siden <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Faktureringsfakturering</a>  \> & betalinger.
2. Hvis du vil downloade .pdf af din faktura, skal du vælge **Download faktura PDF** i rækken for den faktura, du vil have vist.
3. Vælg en faktura på listen for at få vist din onlinefaktura. Du kan også downloade .pdf fra siden med fakturaoplysninger.

## <a name="invoice-faq"></a>Ofte stillede spørgsmål om fakturaer

### <a name="when-is-my-invoice-available"></a>Hvornår er min faktura tilgængelig?

Nogle fakturaer genereres inden for 24 timer efter købet. Andre fakturaer genereres ved slutningen af faktureringsperioden og medtager alle varer fra den pågældende periode.

### <a name="how-do-i-pay-the-amount-due-on-my-invoice"></a>Hvordan betaler jeg det forfaldne beløb på min faktura?

Betalingsinstruktioner afhænger af din betalingsmetode og vises nederst i PDF-fakturaen. Hvis din betalingsmetode er et kreditkort, debiteres det automatisk inden for 10 dage efter fakturadatoen. Hvis din betalingsmetode er ved hjælp af check eller bankoverførsel, skal du se oplysningerne under **Betalingsinstruktioner** i PDF-filen.

### <a name="whats-the-difference-between-sold-to-and-bill-to-addresses"></a>Hvad er forskellen mellem adresserne "Solgt til" og "Faktureres til"?

- **Solgt til:** Den juridiske enhed, der er ansvarlig for betaling og identificeret på fakturaen. Den adresse, du angiver her, bruges til at fastlægge din momssats, medmindre du vælger at angive en alternativ leveringsadresse under dit køb. Du kan finde flere oplysninger [under Momsoplysninger](tax-information.md).
- **Fakturer til:** Den adresse, hvor den fysiske faktura er sendt, hvis det er relevant. Der kan være flere **fakturaadresser** pr. juridisk enhed, men kun én faktura **, der skal adressere** pr. faktureringsprofil.

### <a name="what-are-billed-amount-and-amount-due"></a>Hvad er "Faktureret beløb" og "Forfaldent beløb?"

- **Faktureret beløb:** Det samlede beløb for det køb, du har foretaget.
- **Forfaldent beløb:** Den resterende saldo for det, du skylder.

### <a name="what-is-the-difference-between-service-period-and-billing-period"></a>Hvad er forskellen mellem "'Tjenesteperiode" og "Faktureringsperiode?"

- **Tjenesteperiode:** Den periode, hvor du skal betale for at bruge tjenesten.
- **Faktureringsperiode:** Den periode, der er siden sidste fakturadato.

### <a name="why-dont-i-see-azure-prepayment-as-a-payment-method"></a>Hvorfor kan jeg ikke se azure forudbetaling som en betalingsmetode?

Forudbetaling af Azure er kun tilgængelig som en betalingsmetode for berettigede Azure-produkter og -tjenester

## <a name="need-help-contact-support"></a>Har du brug for hjælp? Kontakt support

Hvis du har spørgsmål eller har brug for hjælp til dine Azure-kreditter, kan <a href="https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest" target="_blank">du oprette en supportanmodning med Azure-support</a>.

Hvis du har spørgsmål eller har brug for hjælp til din faktura i Microsoft 365 Administration, kan du [kontakte support for virksomhedsprodukter](../../admin/get-help-support.md).

## <a name="related-content"></a>Relateret indhold

[Forstå din regning eller faktura for Microsoft 365 for business](understand-your-invoice2.md) (artikel)\
[Spor Microsoft Customer Agreement Azure-kreditsaldo](/azure/billing/billing-mca-check-azure-credits-balance) (artikel)\
[Gennemse din Microsoft-kundeaftalefaktura](/azure/cost-management-billing/understand/review-customer-agreement-bill) (artikel)\
[Introduktion til din Microsoft-kundeaftalefaktureringskonto](/azure/billing/billing-mca-overview) (artikel)
