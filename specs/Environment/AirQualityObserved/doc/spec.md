# Air Quality Observed

**Note: The latest version of this Data Model can be 
found at [https://github.com/smart-data-models/dataModel.Environment](https://github.com/smart-data-models/dataModel.Environment)**

## Description

An observation of air quality conditions at a certain place and time. This data
model has been developed in cooperation with mobile operators and the
[GSMA](https://www.gsma.com/iot/iot-big-data/).

## Data Model

A JSON Schema corresponding to this data model can be found
[here](http://fiware.github.io/dataModels/specs/Environment/AirQualityObserved/schema.json).

-   `id` : Unique identifier.

-   `type` : Entity type. It must be equal to `AirQualityObserved`.

-   `dataProvider` : Specifies the URL to information about the provider of this
    information

    -   Attribute type: Property. URL
    -   Optional

-   `dateModified` : Last update timestamp of this entity.

    -   Attribute type: Property. [DateTime](https://schema.org/DateTime)
    -   Read-Only. Automatically generated.

-   `dateCreated` : Entity's creation timestamp.

    -   Attribute type: Property. [DateTime](https://schema.org/DateTime)
    -   Read-Only. Automatically generated.

-   `location` : Location of the air quality observation represented by a
    GeoJSON geometry.
    -   Attribute type: GeoProperty. `geo:json`.
    -   Normative References:
        [https://tools.ietf.org/html/rfc7946](https://tools.ietf.org/html/rfc7946)
    -   Mandatory if `address` is not defined.
	
-   `address` : Civic address of the air quality observation. Sometimes it
    corresponds to the air quality station address.
    -   Normative References:
        [https://schema.org/address](https://schema.org/address)
    -   Mandatory if `location` is not present.
	
-   `dateObserved` : The date and time of this observation in ISO8601 UTCformat.
    It can be represented by an specific time instant or by an ISO8601 interval.
    -   Attribute type: Property. [DateTime](https://schema.org/DateTime) or an ISO8601
        interval represented as [Text](https://schema.org/Text).
    -   Mandatory
	
-   `areaServed` : Higher level area to which this air quality measurement belongs to. It
    can be used to group air quality measurements per district, neighbourhood, etc.
    -   Attribute type: [Text](https://schema.org/Text)
    -   Normative References:
        [https://schema.org/areaServed](https://schema.org/areaServed)
    -   Optional

-   `source` : A sequence of characters giving the source of the entity data.
    -   Attribute type: Property. [Text](https://schema.org/Text) or
        [URL](https://schema.org/URL)
    -   Optional
-   `airQualityLevel` : Overall qualitative level of health concern
    corresponding to the air quality observed.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Example values defined by the
        [USA EPA Agency](https://airnow.gov/index.cfm?action=aqibasics.aqi):
        (`good`, `moderate`, `unhealthyForSensitiveGroups`, `unhealthy`,
        `veryUnhealthy`, `hazardous`). As this can be different between
        countries, regulations or implementations, the set of allowed values
        will depend on the reference specification used. It is recommended that
        implementations use the same naming conventions as exemplified above
        (lower case starting words, camel case when compound terms are used)
    -   Attribute metadata:
        -   `referenceSpecification` : Specification that must be taken as
            reference when interpreting the supplied qualitative value.
            -   Type: [Text](https://schema.org/Text) or
                [URL](https://schema.org/URL)
            -   Mandatory
    -   Optional

-   `airQualityIndex` : Air quality index corresponding to the air quality
    observed.

    -   Attribute type: Property. [Number](https://schema.org/Number)
    -   Attribute metadata:
        -   `referenceSpecification` : Specification that must be taken as
            reference when interpreting or calculating the supplied air quality
            index.
            -   Type: [Text](https://schema.org/Text) or
                [URL](https://schema.org/URL)
            -   Optional
    -   Optional

-   `reliability` : Reliability (percentage, expressed in parts per one)
    corresponding to the air quality observed.

    -   Attribute type: Property. [Number](https://schema.org/Number)
    -   Allowed values: Interval \[0,1\]
    -   Optional

-   `refDevice` : A reference to the device(s) which captured this observation.

    -   Attribute type: Relationship. Reference to an entity of type `Device`
    -   Optional

-   `refPointOfInterest` : A reference to a point of interest (usually an air
    quality station) associated to this observation.
    -   Attribute type: Relationship. Reference to an entity of type `PointOfInterest`
    -   Optional

### Representing air pollutants

In order to enable a proper management of the concentrations of the different
pollutants, _for each_ pollutant (measurand) there must be an attribute which
name _MUST_ be exactly equal the chemical formula (or mnemonic) of the
measurand, ex. CO. The structure of such an attribute will be as follows:

-   Attribute name: Equal to the name of the measurand, for instance `CO`.

-   Attribute type: [Number](https://schema.org/Number)

-   Attribute value: corresponds to the value for the measurand as a number.

-   Attribute metadata:
    -   `timestamp` : optional timestamp for the observed value in ISO8601
        format. It can be omitted if the observation time is the same as the one
        captured by the `dateObserved` attribute at entity level.
        -   Type: [DateTime](https://schema.org/DateTime)
    -   `unitCode` : The unit code (text) of measurement given using the
        [UN/CEFACT Common Code](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes)
        (max. 3 characters). For instance, `GP` represents milligrams per cubic
        meter and `GQ` represents micrograms per cubic meter.
        -   Type: [Text](https://schema.org/Text)
        -   Mandatory
    -   `description` : short description of the measurand
        -   Type: [Text](https://schema.org/Text)
        -   Optional

### Representing qualitative levels of the different air pollutants

In order to enable a proper management of the qualitative levels of the
different pollutants, _for each_ pollutant (measurand) there might be an
attribute which name _MUST_ be exactly equal to the concatenation of the
chemical formula (or mnemonic) of the measurand with the string `_Level`, ex.
`CO_Level`. To be more precise, the structure of such an attribute will be as
follows:

-   Attribute name: Equal to the name of the measurand plus the suffix `_Level`,
    for instance `CO_Level`.
-   Attribute type: [Text](https://schema.org/Text)
-   Attribute value: Example values defined by the USA EPA Agency:(`good`,
    `moderate`, `unhealthyForSensitiveGroups`, `unhealthy`, `veryUnhealthy`,
    `hazardous`). As this can be different between countries, regulations or
    implementations, the set of allowed values will depend on the reference
    specification used. It is recommended that implementations use the same
    naming conventions as exemplified above (lower case starting words, camel
    case when compound terms are used)
-   Attribute metadata:
    -   `description` : short description of the measurand and its related
        qualitative level
        -   Type: [Text](https://schema.org/Text)
        -   Optional
    -   `referenceSpecification` : Specification that must be taken as reference
        when interpreting the supplied qualitative value.
        -   Type: [Text](https://schema.org/Text) or
            [URL](https://schema.org/URL)
        -   Mandatory

### Representing airquality-related weather conditions

Certain weather conditions have an influence over the observed air quality.
There are two options for representing them:

-   A/ Through a linked entity of type `WeatherObserved` (attribute named
    `refWeatherObserved`).
-   B/ Through a group of weather-related properties already defined by
    [WeatherObserved](../../../Weather/WeatherObserved/doc/spec.md).

Below is the description of the attribute to be used for option A/.

-   `refWeatherObserved` : Weather observed associated to the air quality
    conditions described by this entity.
    -   Attribute type: Relationship. Reference to a
        [WeatherObserved](../../../Weather/WeatherObserved/doc/spec.md) entity.
    -   Optional

**Note**: JSON Schemas are intended to capture the data type and associated
constraints of the different Attributes, regardless their final representation
format in NGSI(v2, LD).

## Examples

### Normalized Example

Normalized NGSI response

```json
{
    "id": "Madrid-AmbientObserved-28079004-2016-03-15T11:00:00",
    "type": "AirQualityObserved",
    "dateObserved": {
        "value": "2016-03-15T11:00:00/2016-03-15T12:00:00"
    },
    "airQualityLevel": {
        "value": "moderate"
    },
    "CO": {
        "value": 500,
        "metadata": {
            "unitCode": {
                "value": "GP"
            }
        }
    },
    "temperature": {
        "value": 12.2
    },
    "NO": {
        "value": 45,
        "metadata": {
            "unitCode": {
                "value": "GQ"
            }
        }
    },
    "refPointOfInterest": {
        "type": "Relationship",
        "value": "28079004-Pza.deEspanya"
    },
    "windDirection": {
        "value": 186
    },
    "source": {
        "value": "http://datos.madrid.es"
    },
    "windSpeed": {
        "value": 0.64
    },
    "SO2": {
        "value": 11,
        "metadata": {
            "unitCode": {
                "value": "GQ"
            }
        }
    },
    "NOx": {
        "value": 139,
        "metadata": {
            "unitCode": {
                "value": "GQ"
            }
        }
    },
    "location": {
        "type": "geo:json",
        "value": {
            "type": "Point",
            "coordinates": [-3.712247222222222, 40.423852777777775]
        }
    },
    "airQualityIndex": {
        "value": 65
    },
    "address": {
        "type": "PostalAddress",
        "value": {
            "addressCountry": "ES",
            "addressLocality": "Madrid",
            "streetAddress": "Plaza de Espa\u00f1a"
        }
    },
    "reliability": {
        "value": 0.7
    },
    "relativeHumidity": {
        "value": 0.54
    },
    "precipitation": {
        "value": 0
    },
    "NO2": {
        "value": 69,
        "metadata": {
            "unitCode": {
                "value": "GQ"
            }
        }
    },
    "CO_Level": {
        "value": "moderate"
    }
}
```

### key-value pairs Example

Sample uses simplified representation for data consumers `?options=keyValues`

```json
{
    "id": "Madrid-AmbientObserved-28079004-2016-03-15T11:00:00",
    "type": "AirQualityObserved",
    "address": {
        "addressCountry": "ES",
        "addressLocality": "Madrid",
        "streetAddress": "Plaza de España"
    },
    "dateObserved": "2016-03-15T11:00:00/2016-03-15T12:00:00",
    "location": {
        "type": "Point",
        "coordinates": [-3.712247222222222, 40.423852777777775]
    },
    "source": "http://datos.madrid.es",
    "precipitation": 0,
    "relativeHumidity": 0.54,
    "temperature": 12.2,
    "windDirection": 186,
    "windSpeed": 0.64,
    "airQualityLevel": "moderate",
    "reliability": 0.9,
    "CO": 500,
    "NO": 45,
    "NO2": 69,
    "NOx": 139,
    "SO2": 11,
    "CO_Level": "good",
    "NO_Level": "moderate",
    "refPointOfInterest": "28079004-Pza. de España"
}
```

### LD Example

Sample uses the NGSI-LD representation

```json
{
    "id": "urn:ngsi-ld:AirQualityObserved:Madrid-AmbientObserved-28079004-2016-03-15T11:00:00",
    "type": "AirQualityObserved",
    "dateObserved": {
        "type": "Property",
        "value": "2016-03-15T11:00:00/2016-03-15T12:00:00"
    },
    "airQualityLevel": {
        "type": "Property",
        "value": "moderate"
    },
    "CO": {
        "type": "Property",
        "value": 500,
        "unitCode": "GP"
    },
    "temperature": {
        "type": "Property",
        "value": 12.2
    },
    "NO": {
        "type": "Property",
        "value": 45,
        "unitCode": "GQ"
    },
    "refPointOfInterest": {
        "type": "Relationship",
        "object": "urn:ngsi-ld:PointOfInterest:28079004-Pza.deEspanya"
    },
    "windDirection": {
        "type": "Property",
        "value": 186
    },
    "source": {
        "type": "Property",
        "value": "http://datos.madrid.es"
    },
    "windSpeed": {
        "type": "Property",
        "value": 0.64
    },
    "SO2": {
        "type": "Property",
        "value": 11,
        "unitCode": "GQ"
    },
    "NOx": {
        "type": "Property",
        "value": 139,
        "unitCode": "GQ"
    },
    "location": {
        "type": "GeoProperty",
        "value": {
            "type": "Point",
            "coordinates": [-3.712247222222222, 40.423852777777775]
        }
    },
    "airQualityIndex": {
        "type": "Property",
        "value": 65
    },
    "address": {
        "type": "Property",
        "value": {
            "addressCountry": "ES",
            "addressLocality": "Madrid",
            "streetAddress": "Plaza de Espa\u00f1a",
            "type": "PostalAddress"
        }
    },
    "reliability": {
        "type": "Property",
        "value": 0.7
    },
    "relativeHumidity": {
        "type": "Property",
        "value": 0.54
    },
    "precipitation": {
        "type": "Property",
        "value": 0
    },
    "NO2": {
        "type": "Property",
        "value": 69,
        "unitCode": "GQ"
    },
    "CO_Level": {
        "type": "Property",
        "value": "moderate"
    },
    "@context": [
        "https://uri.etsi.org/ngsi-ld/v1/ngsi-ld-core-context.jsonld",
        "https://schema.lab.fiware.org/ld/context"
    ]
}
```

You can read about public instance offering information about observed air
quality [here](../../../gsma.md).
