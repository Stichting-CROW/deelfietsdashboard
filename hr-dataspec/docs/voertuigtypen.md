## Vehicle Types

This section helps you in choosing the right vehicle type.

First, we show the different types of vehicle types that are supported in the Dashboard Deelmobiliteit.

After that, we show exactly how to implement this in your GBFS, MDS or TOMP data feed.

### Supported vehicle types


| English                     | Dutch                       |
| --------------------------- | --------------------------- |
| Bicycle                     | Gewone fiets                |
| Bicycle with pedal assist   | Fiets met trapondersteuning |
| Moped <= 25 km/h            | Snorfiets (blauw kenteken)  |
| Moped                       | Bromfiets (geel kenteken)   |
| Scooter                     | Elektrisch step             |
| Human powered cargo bike    | Bakfiets              |
| Electric cargo bike         | Elektrisch bakfiets          |
| Shared combustion car       | Deelauto met verbrandingsmotor |
| Shared electric car         | Elektrisch deelauto          | 

### How to offer vehicle type in GBFS?

Since GBFS 2.1 you can share information on what vehicle type is offered.

Please share vehicle type information in your GBFS feed:

1. Offer [vehicle_types.json](https://github.com/NABSA/gbfs/blob/c3622c52f2cf08675a56a46445ecf7fbe5595f7f/gbfs.md#vehicle_typesjson-added-in-v21)
2. In free_bike_status.json, add property [vehicle_type_id](https://github.com/NABSA/gbfs/blob/master/gbfs.md#free_bike_statusjson)

We ask you to share:

- `vehicle_type_id`
- `form_factor`
- `propulsion_type`
- `max_permitted_speed` (optional though required if you offer a moped)
- `wheel_count`         (optional)

In the table below you'll find all the combinations possible.

| vehicle type                | form_factor       | propulsion_type | max_permitted_speed
| ---------------             | ----------------- | --------------- | ----------- 
| Bicycle                     | bicycle           | human           | -
| Bicycle with pedal assist   | bicycle           | electric_assist | 25
| Moped <= 25 km/h            | moped             | electric        | 25
| Moped                       | moped             | electric        | 45
| Scooter                     | scooter_standing  | electric        | 25
| Human powered cargo bike    | cargo_bicycle     | human           | -
| Electric cargo bike         | cargo_bicycle     | electric_assist | 25
| Shared combustion car       | car               | combustion      | -
| Shared electric car         | car               | electric        | -

If you have questions on implementing a specific vehicle type, send an email to [info@deelfietsdashboard.nl](mailto:info@deelfietsdashboard.nl).

### How to offer vehicle type in MDS?

MDS [uses](https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/general-information.md#vehicle-types) the same vehicle types as GBFS.

From [MDS 2.0.0](https://github.com/NABSA/gbfs/pull/370#issuecomment-918223268) the newest vehicle types like 'cargo_bicycle' and 'scooter_standing' are supported as well. We will start using the 2.0.0 standard from now and adapt later on if the spec changes.



Please share vehicle type information in your MDS feed:

- In [`/vehicles`](https://github.com/openmobilityfoundation/mobility-data-specification/tree/dev/provider#vehicles), add properties:
  - `vehicle_type`
  - [`propulsion_types`](https://github.com/openmobilityfoundation/mobility-data-specification/blob/dev/general-information.md#propulsion-types) (add only 1 propulsion type in this array)
  - `max_permitted_speed` (optional though required if you offer a moped)
  - `wheel_count`         (optional)

In the table below you'll find all the combinations possible.

| vehicle type                | form_factor       | propulsion_type | max_permitted_speed
| ---------------             | ----------------- | --------------- | ----------- 
| Bicycle                     | bicycle           | human           | -
| Bicycle with pedal assist   | bicycle           | electric_assist | 25
| Moped <= 25 km/h            | moped             | electric        | 25
| Moped                       | moped             | electric        | 45
| Scooter                     | scooter_standing  | electric        | 25
| Human powered cargo bike    | cargo_bicycle     | human           | -
| Electric cargo bike         | cargo_bicycle     | electric_assist | 25
| Shared combustion car       | car               | combustion      | -
| Shared electric car         | car               | electric        | -

If you have questions on implementing a specific vehicle type, send an email to [info@deelfietsdashboard.nl](mailto:info@deelfietsdashboard.nl).

