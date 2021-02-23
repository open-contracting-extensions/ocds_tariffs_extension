# Tariffs

## Introduction

Some contracts, particularly Public Private Partnership contracts, include agreements about the user fees to be charged for use of the infrastructure or services the contract relates to.

For example, a Public Private Partnership project to build a bridge may set out the tolls for cars and other vehicles cross the bridge.

The tariff extension allows a structured list of these charges to be set out.

You can also find entries related to tariffs in the standard [documentType codelist](https://standard.open-contracting.org/latest/en/schema/codelists/#document-type).

## Tariff modelling

The tariff model builds upon the metrics extension, allowing an array of tariff items, each with an identifier, title, period, value, units and an arbitrary set of dimensions.

For example, if the toll for a road bridge varies based on (a) the type of vehicle; and (b) the time of day; an implementation of the tariff extension may create new fields for `dimensions.vehicleType` and `dimensions.timeOfDay`, populating these according to local codelists. In PPP cases, these additional dimensions may mirror those used in the estimated demand and other metrics sections.

## Example

The example below shows a very simply tariff table, without periods or units, but with two dimensions. Tariffs which relate to a particular set of dates could have a `period` block. Those which relate to a particular unit (e.g. tonnes) could have this indicated using a `unit` block.

```json
{
  "contracts": [
    {
      "id": "1",
      "awardID": "1",
      "tariffs": [
        {
          "id": "1",
          "title": "Standard Toll",
          "dimensions": {
            "vehicleType": "Class 1",
            "registration": "No registration"
          },
          "value": {
            "amount": 0.0,
            "currency": "GBP"
          }
        },
        {
          "id": "2",
          "title": "Standard Toll",
          "dimensions": {
            "vehicleType": "Class 2",
            "registration": "No registration"
          },
          "value": {
            "amount": 2.0,
            "currency": "GBP"
          }
        },
        {
          "id": "3",
          "title": "Standard Toll",
          "dimensions": {
            "vehicleType": "Class 3",
            "registration": "No registration"
          },
          "value": {
            "amount": 6.0,
            "currency": "GBP"
          }
        },
        {
          "id": "4",
          "title": "Standard Toll",
          "dimensions": {
            "vehicleType": "Class 4",
            "registration": "No registration"
          },
          "value": {
            "amount": 8.0,
            "currency": "GBP"
          }
        }
      ]
    }
  ]
}
```

## Versions

Use the following extension URL for different versions of OCDS:

* 1.2: https://raw.githubusercontent.com/open-contracting-extensions/ocds_tariffs_extension/1.2/extension.json
* 1.1: https://raw.githubusercontent.com/open-contracting-extensions/ocds_tariffs_extension/1.1/extension.json

## Issues

Report issues for this extension in the [ocds-extensions repository](https://github.com/open-contracting/ocds-extensions/issues), putting the extension's name in the issue's title.

## Changelog

### 2021-02-15

* [#1157](https://github.com/open-contracting/standard/issues/1157) Move the codes of the +documentType.csv codelist to the standard

### 2020-06-04

* Review normative and non-normative words

### 2020-04-24

* Add `minProperties`, `minItems` and/or `minLength` properties.

### 2019-03-20

* Set `"uniqueItems": true` on array fields, and add `"minLength": 1` on required string fields.
* Make `Tariff.unit` non-nullable, like `Item.unit`.
* Make `Tariff.dimensions` non-nullable (undo earlier change).

### 2018-05-08

* Make `Tariff.id` required to support revision tracking and [list merging](http://standard.open-contracting.org/latest/en/schema/merging/#lists)

### 2018-05-01

* Make `Tariff.dimensions` nullable.
