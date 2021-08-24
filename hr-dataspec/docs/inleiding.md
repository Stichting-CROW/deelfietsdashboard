## Introduction

The CROW deelfietsdashboard uses simple data formats to collect information on shared mobility to present to regulatory agencies, usually municipalities.
This data is provided by operators.
It works by requesting the location of every vehicle currently present in the public space (*openbare ruimte*).
Vehicles removed from the public space and vehicles in use should be removed from such responses.

There are several data formats available for this exchange.
CROW deelfietsdashboard prefers MDS’s `/vehicles` endpoint, as MDS was designed for regulatory use.
GBFS and TOMP-API are also possible data exchange formats but have been designed for traveler information.
Therefore, some modifications were made to the specification to deduce trips from available vehicles.
