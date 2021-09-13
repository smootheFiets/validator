# validator

Custom JOSM-validator rules: `outdated.validator.mapcss` and `smootheFiets.validator.mapcss`.
Install via JOSM preferences, 'data validator', 'tag checker rules', 'plus' icon.


## outdated.validator.mapcss
Provides validator warnings for objects that, by experience, are subject to change in reality but haven't been touched in OSM for a while.  Additionally, it throws errors for highways/buildings with a spurious `proposed`/`construction` tag and allows to 'fix' those errors (by brutally deleting the spurious tags).

The following objects will generate warnings:
* `landuse=construction` and `amenity=post_box` if last timestamp is before 2019
* `amenity=bench`, `leisure=picnic_table`, and `tourism=picnic_site` if last timestamp is before 2018.

These dates are hard-wired in the code, unfortunately.  I'll try and make that dynamic (older than _n_ years); for now I don't know how to pull that off in JOSM.


## smootheFiets.validator.mapcss
Throws warnings at things that smootheFiets likes to spend time on, most of them applicable to road mapping in the Netherlands:
* `surface` and/or `smoothness` missing on cyclable ways
* `maxspeed` missing on roads
* `highway=cycleway` without `traffic_sign`
* `highway=footway` without NL:G7
* `foot=no` or `bicycle=no` unless there's a good reason (Dutch traffic signs C9, C14, C15, C16); needs to be `use_sidepath` in many cases.
* `traffic_sign=city_limit` without proper `direction` tags
* wheelchair accessibility of bus stops and crossings
* `landuse` sharing nodes with `highway`
* postboxes need `operator=PostNL` (in NL)


## Version history
* 0.1_2021-09-09: first version on Github
* 0.2_2021-09-10: improved timestamp checks 
* 0.3_2021-09-10: syntax fix: forgotten comma
* 0.4_2021-09-10: allow `traffic_sign=none` on footways
* 0.5_2021-09-13: improved tests on highways with/without NL:G7/G11/G12a/G13
