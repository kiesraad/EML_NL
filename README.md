# EML_NL schema definitions
This repository contains the schema definitions for the EML_NL standard, which is a modified version of the [Election Markup Language (EML) Version 5.0](https://docs.oasis-open.org/election/eml/v5.0/EML-Schema-Descriptions-v5.0.html) by [OASIS Open](https://www.oasis-open.org/).

The standard has been modified, extended and restricted to fit the Dutch electoral law.

---
### Extensions
General extensions which are used in multiple parts of the standard are defined in `kiesraad-eml-extensions.xsd`

### Restrictions
General restrictions of existing `EML` elements are defined in `kiesraad-eml-restrictions.xsd`, while restrictions specific to certain EML_NL messages are defined in their respective xsd files, prefixed by their EML ID (110, 110a, 210 etc.)

### Modifications
[Election Markup Language (EML) Version 5.0](https://docs.oasis-open.org/election/eml/v5.0/EML-Schema-Descriptions-v5.0.html) makes use of the eXtensible Address Language (xAL) and eXtensible Name Language (xNL) standards for addresses and names respectively.

Altered versions of these to better reflect the Dutch addressing system and naming conventions and are included as `xAL-kiesraad-strict.xsd` and `xNL-kiesraad-strict.xsd`.