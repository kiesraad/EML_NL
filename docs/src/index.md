# Het Nederlandse profiel van de EML 5.0

**EML\_NL – Het bestandsformaat voor de uitwisseling van gegevens voor de vaststelling van de uitslag van verkiezingen (inclusief de zetelverdeling)**

Versie 1.3

**Licentie**

Dit document is beschikbaar onder de volgende Creative Commons licentie:

[![http://www.creativecommons.org.nz/wp-content/uploads/2012/05/by.png](./media/image1.png)](http://creativecommons.org/licenses/by/3.0/nl/)


## Inleiding

EML\_NL is een variant van de internationale Election Markup Language (EML) standaard die is opgesteld door de Organization for the Advancement of Structured Information Standards (OASIS). EML\_NL komt voort uit EML versie 5.0 van OASIS en is aangepast aan het Nederlandse kiesrecht.

EML\_NL wordt bij verkiezingen gebruikt voor de uitwisseling van gegevens. Het gaat om de uitwisseling van kandidaatgegevens en stemtotalen om de verkiezingsuitslag te kunnen vaststellen. Volgens de eisen die de staatssecretaris van Binnenlandse Zaken en Koninkrijksrelaties in 2008 aan verkiezingssoftware heeft gesteld, moet de programmatuur die hiervoor gebruikt wordt modulair opgebouwd zijn en moet gebruik gemaakt worden van de EML standaard. EML\_NL heeft tot doel de gegevensuitwisseling (de interoperabiliteit) tussen verschillende programmatuur te waarborgen. De verkiezingssoftware wordt gebruikt door politieke partijen en hoofd- en centraal stembureaus.

De EML\_NL is tot stand gekomen in samenhang met de ontwikkeling van de Ondersteunende Software Verkiezingen (OSV). Het beheer en eigendom van OSV berust bij de Kiesraad (centraal stembureau) te Den Haag. In de ontwikkelfase van OSV heeft, in overleg met derden (Klankbordgroep met externe leden, softwareleveranciers en gebruikers), een vertaling plaatsgevonden van de EML standaard naar de Nederlandse situatie. Wijzingen in de EML\_NL als gevolg van wijzingen in wet- en regelgeving, worden besproken met softwareleveranciers en gebruikers. Op de Github pagina van de Kiesraad ([www.github.com/kiesraad/EML\_NL](http://www.github.com/kiesraad/EML_NL)) wordt de specificatie van EML\_NL open-source doorontwikkeld en gepubliceerd en bestaat de mogelijkheid om voorstellen te doen om de EML\_NL verder te verbeteren.

## Toepassing

EML\_NL wordt gebruikt voor de overdracht van gegevens tussen verschillende programma’s en voor de permanente opslag van verkiezingsresultaten. EML\_NL definieert aanpassingen op de EML schema’s die worden gebruikt voor de vaststelling van de verkiezingsuitslag (includief de zetelverdeling) en het uitwisselen van gegeven over kandidatenlijsten, stembureaus en de verkiezing zelf. De EML schema’s die nader zijn gedefinieerd zijn: 110a, 110b, 210, 230b, 230c, 510a, 510b, 510c, 510d, 520, 630. In de onderstaande tabel wordt een overzicht gegeven.

| **EML**  | **Beschrijving**                                            |
| -------- | ----------------------------------------------------------- |
| 110a     | Verkiezingsdefinitie                                        |
| 110b     | Stembureaus                                                 |
| 210      | Kandidatenlijst                                             |
| 230b     | Kandidatenlijsten                                           |
| 230c     | Totaallijsten                                               |
| 510a     | Tellingbestand van stembureau (SB)                          |
| 510b     | Tellingbestand van gemeentelijk stembureau (GSB) = gemeente |
| 510c     | Tellingbestand van hoofdstembureau (HSB)                    |
| 510d     | Totaaltelling van centraal stembureau (CSB)                 |
| 520      | Resultaatbestand                                            |
| 630      | Referendumopties                                            |

In de EML\_NL zijn (ten opzichte van de internationale EML standaard) aanpassingen doorgevoerd om dubbelzinnigheden te vermijden. Daarnaast zijn aanpassingen doorgevoerd om de standaard geschikt te maken voor het Nederlandse verkiezingsproces. In dit document worden de aanpassingen op twee manieren beschreven:

1.  Beschrijving van de restricties en verbeteringen van de EML standaard schema’s

2.  Beschrijving van concrete voorbeelden voor geselecteerde verkiezingstypes.

## Doel van de aanpassingen in EML\_NL

De beschrijvingen van de aanpassingen dienen twee doelen:

1.  Formele beschrijving van de bestandsformaten voor gegevensuitwisseling tussen de verschillende programma’s;

2.  Validatie van de door programma’s aangemaakte EML-bestanden;

## Ontwerpregels

Veel voorkomende uitbreidingen zijn opgenomen in het bestand kiesraad-eml-extensions.xsd. Veel voorkomende restricties zijn opgenomen in het bestand kiesraad-eml-restrictions.xsd. Specifieke restricties voor bepaalde EML schema’s zijn opgenomen in de zogeheten specifieke schema-bestanden. Uitbreidingen gerelateerd aan stembureaus zijn opgenomen in het bestand kiesraad-eml-sb-extensions.xsd.

De werkwijze van schema-gebaseerde herdefinitie is niet gebruikt vanwege de slechte ‘gereedschaps-’ondersteuning. In plaats hiervan werden waar mogelijk nieuwe globale types met lokale element-definities gebruikt. Restricties die niet in bovenstaande gevallen konden worden opgenomen, zijn uitgevoerd door de originele schema-bestanden te kopiëren en daarna te wijzigen. Dit is met name het geval voor elementen die geen deel uitmaken van het EML- naamgebied en die daarom niet lokaal konden worden gedefinieerd in specifieke schema-bestanden.

Attributen die niet in de EML\_NL schema’s worden gebruikt, werden niet gewijzigd. Sommige attributen zijn verplicht gemaakt en voor de meest gebruikte attributen werden restricties toegepast op toegestane waarden.

Verplichte elementen met geen duidelijke toepassing voor het Nederlandse verkiezinsgproces zijn onveranderd gebleven, omdat het geen zin had deze te veranderen en verwijdering de EML-compatibiliteit in gevaar zou brengen. Zelfs optionele child elementen binnen deze verplichte elementen zijn niet verwijderd omdat dit weinig toegevoegde waarde zou hebben.
