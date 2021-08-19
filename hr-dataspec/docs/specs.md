## Data specifications

The [=operator=] MUST provide data conforming to one of the below described specifications.

Customized feeds MAY be implemented as an alternative to [=MDS=].

| Standard                 | Note                                                    |
| ------------------------ | ------------------------------------------------------- |
| [MDS](#mds)              | Preferred.                                              |
| [GBFS](#gbfs-customized) | Requires a customized feed for CROW deelfietsdashboard. |
| [TOMP](#tomp-customized) | Requires a customized feed for CROW deelfietsdashboard. |

{.data}

### General

Parked vehicles that are present in the public space (i.e., PROW) MUST be present in the supplied data.
That includes reserved and disabled vehicles or vehicles with empty batteries, etc. that take up place in the public space.
Inversely, vehicles removed from the public space MUST NOT be returned.

Data provided in a feed or endpoint MUST be updated at least every 30 seconds.
The update frequency MAY be higher.

### MDS

Based on [endpoint specification][1]: `/vehicles`.

| Value                 | Note            |
| --------------------- | --------------- |
| `current_location`    | always REQUIRED |
| `last_event_location` | always REQUIRED |
| `propulsion_types`    | always REQUIRED |
| `vehicle_type`        | always REQUIRED |
| `last_vehicle_state`  | always REQUIRED |
| `last_event_types`    | always REQUIRED |

{.data}

[1]: https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/provider/README.md#vehicles

### GBFS (customized)

<div class="note">
GBFS does not provide enough information for CROW deelfietsdashboard. 
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

### TOMP (customized)

<div class="note">
TOMP by itself does not provide enough information for CROW deelfietsdashboard. 
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
