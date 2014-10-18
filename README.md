# Quantified Self Data Spec

_This is a draft specification for standardizing the collection, storage, and tramission of Quantified Self data._


## What is Quantified Self?

>The Quantified Self is a movement to incorporate technology into data acquisition on aspects of a person's daily life in terms of inputs (e.g. food consumed, quality of surrounding air), states (e.g. mood, arousal, blood oxygen levels), and performance (mental and physical).

[Quantified Self Wikipedia entry](http://en.wikipedia.org/wiki/Quantified_Self)


## Requirements

All data is assume to be in the [JSON](http://json.org) data-interchange format. Additionally, this specification outlines the format of this JSON data using [JSON schema](http://json-schema.org).

From a technical perspective, every JSON object **must** have the following properties:

- `dataType`
- `dataSource`
- `uuid`
- `timestamp`


### dataType

The `dataType` property indicates why type of data is stored in the JSON object. Ultimately, this corresponds to the JSON schema that describes how the data is formated. The value for this property must match an established JSON schema. For example, the following dataType values are valid:

- `biometric-weight`
- `consumption-alcohol`
- `environmental-temperature`


### dataSource

The `dataSource` property specifies where the data originated from. This is intentionally left as an open ended field so that as new sources are introduced into the Quantified Self ecosystem this property can be dynamically expanded. It is up to the implementer of this specification to document the accepted values in use so that consumers can indentify any potential data mappings that would need to take place when merging data from disperate providers.

Example values of this property include:

- `Fitbit`
- `LoseIt`
- `forecast.io`
- `manual`


### uuid

The `uuid` property must contain a [RFC 4122](http://www.ietf.org/rfc/rfc4122.txt) compliant UUID (Universally Unique IDentifier). 

For example:

- `2b0b8801-c5e2-4b2d-a61a-31681eb95093`


### timestamp

The `timestamp` property is for storing a Unix timestamp value. 

>Unix time (a.k.a. POSIX time or Epoch time) is a system for describing instants in time, defined as the number of seconds that have elapsed since 00:00:00 Coordinated Universal Time (UTC), Thursday, 1 January 1970, not counting leap seconds.

[Unix time Wikipedia entry](http://en.wikipedia.org/wiki/Unix_time)

For example:

- `1413555528`


## Special Notes

It is recommended whenever merging or replacing data based on the `uuid` property that the `timestamp` property is also compared as a secondary verifation against uninteded collissions. 


