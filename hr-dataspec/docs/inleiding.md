## Introduction

The CROW-Fietsberaad Dashboard deelmobiliteit uses simple data formats to collect information on shared mobility to present to regulatory agencies, usually municipalities.
This data is provided by operators.
It works by requesting the location of every vehicle currently present in the public space (*openbare ruimte*).
Vehicles removed from the public space and vehicles in use should be removed from such responses.

There are several data formats available for this exchange.
CROW deelfietsdashboard prefers MDS’s [`/vehicles`](https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/provider/README.md#vehicles) endpoint, as MDS was designed for regulatory use.
GBFS and TOMP-API are also possible data exchange formats but have been designed for traveler information.
Therefore, some modifications were made to the specification to deduce trips from available vehicles.

_We strongly recomend to use MDS [`/vehicles`](https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/provider/README.md#vehicles) endpoint when you rely on a external supplier for your software systems. Because it's the only standard we support without small modifications on the original standards._
