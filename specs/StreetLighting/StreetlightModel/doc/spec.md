# Streetlight Model

**Note: The latest version of this Data Model can be 
found at [https://github.com/smart-data-models/dataModel.Streetlighting](https://github.com/smart-data-models/dataModel.Streetlighting)**

It represents a model of streetlight composed by a specific supporting structure
model, a lantern model and a lamp model. A streetlight instance will be based on
a certain streetlight model.

## Data Model

The data model is defined as shown below:

-   `id` : Entity's unique identifier.

-   `type` : It must be equal to `StreetlightModel`.

-   `source` : A sequence of characters giving the source of the entity data.

    -   Attribute type: Property. Text or URL
    -   Optional

-   `dataProvider` : Specifies the URL to information about the provider of this
    information

    -   Attribute type: Property. URL
    -   Optional

-   `name` : Name given to the streetlight model.

    -   Normative References: [https://schema.org/name](https://schema.org/name)
    -   Mandatory

-   `alternateName` : Alternate name given to the streetlight model.

    -   Normative References:
        [https://schema.org/alternateName](https://schema.org/alternateName)
    -   Optional

-   `description` : Description of the streetlight model.

    -   Normative References:
        [https://schema.org/description](https://schema.org/description)
    -   Optional

-   `maxPowerConsumption` : Maximum power consumption supported by the lantern.

    -   Attribute type: Property. List of [Number](https://schema.org/Number).
    -   Default unit: Watts (W)
    -   Optional

-   `minPowerConsumption` : Minimum power consumption supported by the lantern.

    -   Attribute type: Property. List of [Number](https://schema.org/Number).
    -   Default unit: Watts (W)
    -   Optional

-   `columnBrandName` : Name of the column's brand.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   See also: [https://schema.org/brand](https://schema.org/brand)
    -   Optional

-   `columnModelName` : Name of the column's model.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   See also: [https://schema.org/model](https://schema.org/model)
    -   Optional

-   `columnManufacturerName` : Name of the column's manufacturer.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   See also: [https://schema.org/model](https://schema.org/manufacturer)
    -   Optional

-   `columnMadeOf` : Material column is made of.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Allowed values: one Of (`steel`, `aluminium` , `wood`, `other`)
    -   Optional

-   `columnColor` : Column's painting color.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Allowed Values:
        -   A color keyword as specified by
            [W3C Color Keywords](https://www.w3.org/TR/SVG/types.html#ColorKeywords)
        -   A color value as specified by
            [W3C Color Data Type](https://www.w3.org/TR/SVG/types.html#BasicDataTypes)
    -   See also: [https://schema.org/color](https://schema.org/color)
    -   Optional

-   `lanternModelName` : Name of the lantern's model.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   See also: [https://schema.org/model](https://schema.org/model)
    -   Optional

-   `lanternBrandName` : Name of the lantern's brand.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   See also: [https://schema.org/brand](https://schema.org/brand)
    -   Optional

-   `lanternManufacturerName` : Name of the lantern's manufacturer.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   See also: [https://schema.org/model](https://schema.org/manufacturer)
    -   Optional

-   `lanternWeight` : Lantern's weight.

    -   Attribute type: Property. [Number](https://schema.org/Number).
    -   Default Unit: Kilograms (kg)
    -   See also: [https://schema.org/weight](https://schema.org/weight)
    -   Optional

-   `lampModelName` : Name of the lamp's model.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   See also: [https://schema.org/model](https://schema.org/model)
    -   Optional

-   `lampBrandName` : Name of the lamp's brand.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   See also: [https://schema.org/model](https://schema.org/brand)
    -   Optional

-   `lampManufacturerName` : Name of the lamp's manufacturer.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   See also: [https://schema.org/model](https://schema.org/manufacturer)
    -   Optional

-   `lampWeight` : Lamp's weight.

    -   Attribute type: Property. [Number](https://schema.org/Number).
    -   Default Unit: Kilograms (kg)
    -   See also: [https://schema.org/weight](https://schema.org/weight)
    -   Optional

-   `workingLife` : The estimated number of hours working (the lamp) without
    failure.

    -   Attribute type: Property. [Number](http://schema.org/Number)
    -   Default unit: hours
    -   Optional

-   `lampTechnology` : Technology used by the lamp.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Allowed values: one Of (`LED`, `LPS`, `HPS`)
        -   Or any other value not covered by the above list and meaningful to
            the application.
    -   Optional

-   `colorTemperature` : _Correlated_ color temperature of the lamp.

    -   Attribute type: Property. [Number](https://schema.org/Number)
    -   Default unit: Kelvin degrees (K)
    -   Optional

-   `colorRenderingIndex` : Color rendering index of the lamp.

    -   Attribute type: Property. [Number](https://schema.org/Number)
    -   Optional

-   `luminousFlux` : Maximum light output which can be provided by the lamp.

    -   Attribute type: Property. [Number](https://schema.org/Number)
    -   Default unit: Lumens (lm)
    -   Optional

-   `powerConsumption` : (Nominal) power consumption made by the lamp.

    -   Attribute type: Property. List of [Number](https://schema.org/Number).
    -   Default unit: Watts (W)
    -   Optional

-   `compliantWith` : A list of standards to which this streetlight model is
    compliant with.

    -   AttributeType: List of [Text](https://schema.org/Text).
    -   Optional

-   `image` : A URL containing a photo of the streetlight model.

    -   Normative References:
        [https://schema.org/image](https://schema.org/image)
    -   Optional

-   `category` : Type of asset which implements the street light.
    -   AttributeType: List of [Text](https://schema.org/Text).
    -   Allowed Values: (`postTop`, `bollard`, `lamppost`, `lightTower`,
        `flashingBeacon`, `sideEntry`, `signLight`, `ornamentalLantern`) + Or
        any other value not defined above and meaningful for the application
    -   Optional

**Note**: JSON Schemas are intended to capture the data type and associated
constraints of the different Attributes, regardless their final representation
format in NGSI(v2, LD).

## Examples

### Normalized Example

Normalized NGSI response

```json
{
    "id": "streetlightmodel:TubularNumana:ASR42CG:HPS:100",
    "type": "StreetlightModel",
    "category": {
        "value": ["postTop"]
    },
    "colorRenderingIndex": {
        "value": 25
    },
    "columnColor": {
        "value": "green"
    },
    "name": {
        "value": "Tubular Numana 6M - ASR42CG - Son-T 100"
    },
    "powerConsumption": {
        "value": 100
    },
    "lanternManufacturerName": {
        "value": "Indal WRTL"
    },
    "luminousFlux": {
        "value": 2300
    },
    "lampTechnology": {
        "value": "HPS"
    },
    "colorTemperature": {
        "value": 3000
    },
    "lanternModelName": {
        "value": "ASR42CG"
    },
    "columnModelName": {
        "value": "01 TUBULAR P/T 6M NUMANA"
    },
    "lampModelName": {
        "value": "SON-T"
    },
    "lampBrandName": {
        "value": "Philips"
    }
}
```

### key-value pairs Example

Sample uses simplified representation for data consumers `?options=keyValues`

```json
{
    "id": "streetlightmodel:TubularNumana:ASR42CG:HPS:100",
    "type": "StreetlightModel",
    "name": "Tubular Numana 6M - ASR42CG - Son-T 100",
    "columnModelName": "01 TUBULAR P/T 6M NUMANA",
    "columnColor": "green",
    "lanternModelName": "ASR42CG",
    "lanternManufacturerName": "Indal WRTL",
    "lampModelName": "SON-T",
    "lampBrandName": "Philips",
    "lampTechnology": "HPS",
    "powerConsumption": 100,
    "colorTemperature": 3000,
    "colorRenderingIndex": 25,
    "luminousFlux": 2300,
    "category": ["postTop"]
}
```

### LD Example

Sample uses the NGSI-LD representation

```json
{
    "id": "urn:ngsi-ld:StreetlightModel:streetlightmodel:TubularNumana:ASR42CG:HPS:100",
    "type": "StreetlightModel",
    "category": {
        "type": "Property",
        "value": ["postTop"]
    },
    "colorRenderingIndex": {
        "type": "Property",
        "value": 25
    },
    "columnColor": {
        "type": "Property",
        "value": "green"
    },
    "name": {
        "type": "Property",
        "value": "Tubular Numana 6M - ASR42CG - Son-T 100"
    },
    "powerConsumption": {
        "type": "Property",
        "value": 100
    },
    "lanternManufacturerName": {
        "type": "Property",
        "value": "Indal WRTL"
    },
    "luminousFlux": {
        "type": "Property",
        "value": 2300
    },
    "lampTechnology": {
        "type": "Property",
        "value": "HPS"
    },
    "colorTemperature": {
        "type": "Property",
        "value": 3000
    },
    "lanternModelName": {
        "type": "Property",
        "value": "ASR42CG"
    },
    "columnModelName": {
        "type": "Property",
        "value": "01 TUBULAR P/T 6M NUMANA"
    },
    "lampModelName": {
        "type": "Property",
        "value": "SON-T"
    },
    "lampBrandName": {
        "type": "Property",
        "value": "Philips"
    },
    "@context": [
        "https://uri.etsi.org/ngsi-ld/v1/ngsi-ld-core-context.jsonld",
        "https://schema.lab.fiware.org/ld/context"
    ]
}
```

## Test it with a real service

## Open issues
