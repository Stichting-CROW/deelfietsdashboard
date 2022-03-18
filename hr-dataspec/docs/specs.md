## Data specifications

The [=operator=] MUST provide data conforming to a subset of MDS.

### General

Parked vehicles that are present in the public space (i.e., PROW) MUST be present in the supplied data.

That includes reserved and disabled vehicles or vehicles with empty batteries, etc. that take up place in the public space.

Inversely, vehicles removed from the public space MUST NOT be returned.

Data provided in a feed or endpoint MUST be updated at least every 30 seconds.
The update frequency MAY be higher.

### MDS /vehicles

The provider must offer [`/vehicles`][1] endpoint, part of the MDS Provider API.

CROW Dashboard uses this endpoint to get a current snapshot of all vehicles in public space, at any moment.

NOTE: In the [=Vehicle types=] we help you set the right vehicle type for every vehicle in this feed.

[1]: https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/provider/README.md#vehicles

### MDS /trips

The provider must offer [`/trips`][mds-trips] endpoint, part of the MDS Provider API.

CROW Dashboard uses this endpoint to get the exact historical rentals.

NOTE: For the [`route`][mds-trips-routes] property only the start and end of a rental are required. 

[mds-trips]: https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/provider/README.md#trips
[mds-trips-routes]: https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/provider/README.md#routes

### MDS authorization

The providers shall provide [authorization][mds-auth] for API endpoints via a token based auth system.

[mds-auth]: https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/provider/auth.md#authorization

## Deprecated data specifications

In the past CROW Dashboard supported the GBFS and TOMP APIs. As these standards are designed for traveler information and not for regulatory purposes, since 2022 MDS is required.

MDS is a mature standard up that is widely applied across Europe and North America, and therefore a future proof data exchange standard to support municipalities with regulating and monitoring shared mobility operations.

### GBFS (customized) (deprecated)

<div class="note">
GBFS does not provide enough information for the Dashboard Deelmobiliteit. 
Therefore, the specification has been extended to provide the required information.
</div>

Based on [endpoint specification][2]: `free_bike_status.json`.

| Value                           | Note                                                           |
| ------------------------------- | -------------------------------------------------------------- |
| `bikes[]/bike_id`               | REQUIRED, non-standard: persistent id                          |
| `bikes[]/lat` and `bikes[]/lon` | REQUIRED                                                       |
| `bikes[]/vehicle_type_id`       | REQUIRED (which refers to [vehicle_types.json][vehicle_types]) |
| `bikes[]/is_disabled`           | always REQUIRED                                                |
| `bikes[]/is_reserved`           | always REQUIRED                                                |
| {.data}                         |

The static bike ID `bike_id` SHALL NOT be rotated after a trip.
It MAY be rotated after being removed from public space.

[2]: https://github.com/NABSA/gbfs/blob/master/gbfs.md#free_bike_statusjson
[vehicle_types]: https://github.com/NABSA/gbfs/blob/master/gbfs.md#vehicle_typesjson-added-in-v21

### TOMP (customized) (deprecated)

<div class="note">
TOMP by itself does not provide enough information for Dashboard Deelmobiliteit. 
Therefore, the specification has been extended to provide the required information.
</div>

Based on [endpoint specification][3]: `/operator/available-assets`.

| Value                                                | Note                                       |
| ---------------------------------------------------- | ------------------------------------------ |
| `assetClass`                                         | always REQUIRED                            |
| `assets[]/id`                                        | REQUIRED and non-standard: a persistent id |
| `assets[]/isReserved`                                | always REQUIRED                            |
| `assets[]/isDisabled`                                | always REQUIRED                            |
| `assets[]/overriddenProperties/location/coordinates` | REQUIRED                                   |
| `assets[]/overriddenProperties/fuel`                 | REQUIRED                                   |
| {.data}                                              |

The persistent asset ID `id` SHALL NOT be rotated after a trip.
It MAY be rotated after being removed from public space.

[3]: https://app.swaggerhub.com/apis-docs/TOMP-API-WG/transport-operator_maas_provider_api/1.1.0#/operator%20information/get_operator_available_assets
[4]: https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/general-information.md#vehicle-states
