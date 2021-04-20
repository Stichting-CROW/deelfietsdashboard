## Data specifications

Deelfietsdashboard currently supports three data standards for shared mobility.
Out-of-the-box only MDS provides the required information, therefore information via the other standards require more fields.

<div class='advisement'>

The [=operator=] SHALL provide shared mobility data conforming to one of the below described specifications.

</div>

Standard | Note
---|---
[GBFS](#gbfs-customized) | Requires a customized feed for CROW deelfietsdashboard.
[TOMP](#tomp-customized) | Requires a customized feed for CROW deelfietsdashboard.
{.data}

### General

<div class="advisement">

In any response, vehicles that are currently removed from the public space (i.e., PROW) SHALL NOT be returned.

Reserved vehicles or vehicles with empty batteries, etc. take up place in the public space and MUST returned.

Data provided in a feed or endpoint MUST be updated at least every 30 seconds.

</div>

### GBFS (customized)

<div class="note">
GBFS does not provide enough information for CROW deelfietsdashboard. 
Therefore, the specification has been extended to provide the required information.
</div>


Based on [endpoint specification][2]: `free_bike_status.json`.

Value | Note
---|---
`bikes[]/bike_id` | REQUIRED, non-standard: persistent id
`bikes[]/lat` and `bikes[]/lon` | REQUIRED
`bikes[]/vehicle_type_id` | REQUIRED (which refers to [vehicle_types.json][vehicle_types])
`bikes[]/is_disabled` | always REQUIRED 
`bikes[]/is_reserved` | always REQUIRED 
{.data} |

The static bike ID `bike_id` SHALL NOT be rotated after a trip.
It MAY be rotated after being removed from public space.

[2]: https://github.com/NABSA/gbfs/blob/master/gbfs.md#free_bike_statusjson
[vehicle_types]: https://github.com/NABSA/gbfs/blob/master/gbfs.md#vehicle_typesjson-added-in-v21

### TOMP (customized)

<div class="note">
TOMP by itself does not provide enough information for CROW deelfietsdashboard. 
Therefore, the specification has been extended to provide the required information.
</div>


Based on [endpoint specification][3]: `/operator/available-assets`. 

Value | Note
---|--- 
`assetClass` | always REQUIRED
`assets[]/id` | REQUIRED and non-standard: a persistent id
`assets[]/isReserved` | always REQUIRED
`assets[]/isDisabled` | always REQUIRED
`assets[]/overriddenProperties/location/coordinates` | REQUIRED
`assets[]/overriddenProperties/fuel` | REQUIRED
{.data} |

The persistent asset ID `id` SHALL NOT be rotated after a trip.
It MAY be rotated after being removed from public space.


[3]: https://app.swaggerhub.com/apis-docs/TOMP-API-WG/transport-operator_maas_provider_api/1.1.0#/operator%20information/get_operator_available_assets

[4]: https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/general-information.md#vehicle-states
