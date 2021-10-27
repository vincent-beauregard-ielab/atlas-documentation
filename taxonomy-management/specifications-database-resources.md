---
description: >-
  Following specifications describe resources created to provide data storage
  and procedures within
---

# Specifications / Database resources

## Stack

* Database server : Postgresql (>=13.1)
* Database name : `atlas`

## Database level specifications

* All created tables includes columns `modified_at`  with `DEFAULT` set at `CURRENT_TIMESTAMP` whose values are altered `BEFORE UPDATE` by executing the procedure `trigger_set_timestamp`.

## Resources specification

### `TABLE` public.taxa\_ref

#### **Description**

Stores taxonomic atributes of species observed within `observations` table verified by external taxonomic resources.

Each records correspond to a single taxa, single reference source and single rank.

Multiple reference taxa records are inserted for a single observed taxa. When the observed taxa scientific name is invalid, or synonym of the valid taxa, we insert both the invalid and valid taxa. Also, for a single observed taxa, we store within the `taxa_ref`a record for each valid taxon of its classification for ranks `subspecies`, `species`, `genus` and `family`, thus allowing requests to observations based on higher taxonomical ranks. Ex. An observation is stored with the subspecies taxon `Spinus tritis tristis`. We insert an individual reference records for the family `fringilidae`, for the genus `Spinus`, for the species `Spinus tristis` and for the subspecies `Spinus tristis tristis`.

#### Specifications

* Index `taxa_ref_scientific_name_idx` for requests by scientifc name.

## Request procedures

Herein are described requests associated with use cases and how resources are used to fulfill them.

### Get observations by scientific name

#### Expected behaviour

* Request by taxon related to rank `family`, `genus`, `species` or `subspecies` and will return observation with raw `taxa` equal or underneath. _ex. _Request for genus `Acer`will return all observations for species `Acer saccharum`, `Acer rubrum`, `Acer saccharunum`, etc.&#x20;
* Fuzzy matching of requested taxa
* Returns observations for requested species and synonym taxa

#### Implemented interface

* API endpoint `observations?taxa_name={}&ref_source_id={}`
* R Atlas

#### Inputs

* `scientific_name` name of taxon to be requested
* _Optional. _`ref_source_id` asd_ _

#### Process

### Get taxonomic attributes for observations

### Get vernacular name as taxonomic attributes

### Insert observation with related taxonomic information

### Update reference taxonomic information

#### Resources

* FUNCTION `taxa_update_ref`()

#### Flow

1. Delete entire content of `taxa_ref` and `taxa_obs_ref`
2. Run procedure `insert_taxa_ref_from_obs` for all records in `taxa_obs`.

### List observed taxon

Two options

1. Cross reference table to relate observed&#x20;

#### Flow

1.
