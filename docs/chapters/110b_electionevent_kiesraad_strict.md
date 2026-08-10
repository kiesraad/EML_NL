
## 110b-electionevent-kiesraad-strict.xsd

Het beperkte complex data type EMLstructure110 gebruikt het type EMLstructureKR als base type en maakt child elementen ManagingAuthority en kr:CreationDateTime verplicht. **LET OP:** hoewel dit type een naam deelt met het type uit de 110a zijn er dus wel verschillen\!

![](../media/image40.png)

Het beperkte complex data type ElectionIdentifierStructure110 gebruikt het type ElectionIdentifierStructureKR als base type en staat het element kr:NominationDate niet toe.

![](../media/image41.png)

Het beperkte complex data type ContestIdentifierStructure110 gebruikt het type ContestIdentifierStructureKR als base type. Het element ContestName is niet toegestaan.

![](../media/image42.png)

Het complex data type PollingPlaceStructure110 wordt opnieuw gedefinieerd en is in beperkte mate compatibel met het core EML element PollingPlaceStructure. Het beperkt de attributes tot Channel. Daarnaast is het enige toegestane child element beperkt tot PhysicalLocation. Het Address element is beperkt tot een lokaal type waar exact één keer een Locality voor moet komen welke beperkt is tot het type xal:LocalityType110 en optioneel een onbeperkt aantal sb:Location elementen met daarin extra informatie over het stembureau. Indien het een mobiel stembureau betreft dan kunnen er meerdere sb:Location elementen gedefinieerd worden. Daarnaast zijn de volgende elementen toegevoegd: PollingStation met een verplicht Id attribuut en de elementen kr:ReportingUnitType en kr:SharedLocation.

![](../media/image43.png)

Het base type van het EML (root) element is beperkt tot EMLstructure110. Daarna is het uitgebreid op dezelfde manier als in de originele EML V5.0 definitie door het child element ElectionEvent.

![](../media/image44.png)

Het element ElectionEvent is beperkt compatibel in een aantal manieren vergeleken met het originele EML element. Het type van het child element ElectionIdentifier is beperkt tot ElectionIdentifierStructure110. Het type van het child element ContestIdentifier is beperkt tot ContestIdentifierStructure110. Verder zijn alleen child elementen EventIdentifier en Election toegestaan, welke beiden verplicht zijn. Er kunnen 1 of meerdere Election elementen voorkomen. Andere opties zijn niet toegestaan. Het “any" extension point is verwijderd. Onder het Contest element zijn alleen de elementen ContestIdentifier, ReportingUnit (de naam en code van de gemeente), VotingMethod (welk in de praktijk leeg gelaten wordt) en MaxVotes met het aantal kiesgerechtigden toegestaan welke verplicht zijn. Optioneel gezien kunnen de contactgegevens en de website van de gemeente toegevoegd worden met de elementen sb:MunicipalityContactDetails en sb:MunicipalityElectionSite. Als laatste komt verplicht minimaal één PollingPlace element voor, waarvan het type beperkt is tot PollingPlaceStructure110

![](../media/image45.png)

Hieronder staat een voorbeeld van een EML 110b met een mobiel stembureau dat op twee verschillende locaties gestationeerd is:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<EML xmlns="urn:oasis:names:tc:evs:schema:eml"
  xmlns:ds="http://www.w3.org/2000/09/xmldsig#"
  xmlns:kr="http://www.kiesraad.nl/extensions"
  xmlns:sb="http://www.kiesraad.nl/sb-extensions"
  xmlns:xal="urn:oasis:names:tc:ciq:xsdschema:xAL:2.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Id="110b" SchemaVersion="5">
  <TransactionId>1</TransactionId>
  <ManagingAuthority>
    <AuthorityIdentifier Id="0999">Juinen</AuthorityIdentifier>
    <AuthorityAddress/>
  </ManagingAuthority>
  <kr:Schema Version="1.3"/>
  <kr:CreationDateTime>2024-05-27T17:05:57</kr:CreationDateTime>
  <ds:CanonicalizationMethod Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315#WithComments"/>
  <ElectionEvent>
    <EventIdentifier/>
    <Election>
      <ElectionIdentifier Id="EP2024">
        <ElectionName>Europees Parlement 2024</ElectionName>
        <ElectionCategory>EP</ElectionCategory>
        <kr:ElectionSubcategory>EP</kr:ElectionSubcategory>
        <kr:ElectionDate>2024-06-06</kr:ElectionDate>
      </ElectionIdentifier>
      <Contest>
        <ContestIdentifier Id="geen"/>
        <ReportingUnit>
          <ReportingUnitIdentifier Id="0999">Juinen</ReportingUnitIdentifier>
        </ReportingUnit>
        <VotingMethod>SPV</VotingMethod>
        <MaxVotes>123456</MaxVotes>
        <PollingPlace Channel="polling">
          <PhysicalLocation>
            <Address>
              <!-- Het oude Locality element bestaat nog steeds, en is verplicht !-->
              <Locality>
                <xal:LocalityName>Mobiele recreatieruimte "Good Times"</xal:LocalityName>
              </Locality>
              <!-- Er kunnen één of meerdere locaties waar het stembureau zich bevindt toegevoegd worden, elk met zijn eigen info -->
              <sb:Location>
                <sb:BAGId>0518200000747446</sb:BAGId>
                <sb:StreetName>Schoolstraat</sb:StreetName>
                <sb:Number>12</sb:Number>
                <sb:Letter>B</sb:Letter>
                <sb:NumberAddition>ABCD</sb:NumberAddition>
                <sb:PostalCode>3011 AD</sb:PostalCode>
                <sb:City>'s-Gravenhage</sb:City>
                <sb:AdditionalAddressInformation>Ingang aan achterkant gebouw</sb:AdditionalAddressInformation>
                <sb:BuildingUsage>Bijeenkomst</sb:BuildingUsage>
                <sb:Website>https://good-times.nl</sb:Website>
                <sb:OpenTime>2024-06-06T07:30:00</sb:OpenTime>
                <sb:ClosingTime>2024-06-06T10:00:00</sb:ClosingTime>
                <sb:RDx>81611.123456789</sb:RDx>
                <sb:RDy>454909</sb:RDy>
                <sb:Latitude>52.0815</sb:Latitude>
                <sb:Longitude>4.32419</sb:Longitude>
                <sb:Accessibility>
                  <sb:Accessible>true</sb:Accessible>
                  <sb:AccessibilityProperties>
                    <!-- Alle in de ODS gedefinieerde waarden mogelijk + vrije mogelijkheid via 1 of meer 'Other' elementen -->
                    <sb:AccessibleToilet>true</sb:AccessibleToilet>
                  <sb:SignLanguageInterpreter>remote</sb:SignLanguageInterpreter>
                    <sb:Other>Lokale soort 1</sb:Other>
                    <sb:Other>Lokale soort 2</sb:Other>
                  </sb:AccessibilityProperties>
                </sb:Accessibility>
                <sb:OtherInfo>Let op het opstapje!</sb:OtherInfo>
              </sb:Location>
              <sb:Location>
                <sb:StreetName>Schoolstraat</sb:StreetName>
                <sb:Number>14</sb:Number>
                <sb:Letter>B</sb:Letter>
                <sb:NumberAddition>ABCD</sb:NumberAddition>
                <sb:PostalCode>3011 AD</sb:PostalCode>
                <sb:City>'s-Gravenhage</sb:City>
                <sb:AdditionalAddressInformation>Ingang aan achterkant gebouw</sb:AdditionalAddressInformation>
                <sb:OpenTime>2024-06-06T10:00:00</sb:OpenTime>
                <sb:ClosingTime>2024-06-06T21:00:00</sb:ClosingTime>
                <sb:RDx>81611</sb:RDx>
                <sb:RDy>454909</sb:RDy>
                <sb:Latitude>52.08119</sb:Latitude>
                <sb:Longitude>4.32419</sb:Longitude>
              </sb:Location>
            </Address>
            <PollingStation Id="1">1234</PollingStation>
            <kr:ReportingUnitType>Mobile</kr:ReportingUnitType>
            <kr:SharedLocation>true</kr:SharedLocation>
          </PhysicalLocation>
        </PollingPlace>
        ...
      </Contest>
    </Election>
  </ElectionEvent>
</EML>
```