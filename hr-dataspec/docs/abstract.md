This document specifies what data is used by the [CROW-Fietsberaad Dashboard Deelmobiliteit][db] (_shared mobility dashboard_).

The Dashboard Deelmobiliteit is used by municipalities to monitor shared mobility within their area. It shows how long vehicles are parked in public space, how shared mobility is used and where shared mobility is available. Providers can benefit from the Dashboard Deelmobiliteit as they get less data requests from the different individual municipalitites. Also providers can use the Dashboard Deelmobiliteit for their own analyses. If all parties agree, data can be shared for mobility research and scientific research.

The Dashboard Deelmobiliteit applies the guidelines the [CDS-M][cdsm] framework.

New operators should offer the `/vehicles` and `/trips` [=MDS=] end points of the MDS [Provider API][mds-provider-api]. For compatibility purposes we currently support [=GBFS=] and [=TOMP=] as well, but these will be phases out in the future.

<div lang='nl'>

Dit document beschrijft in het Engels van het [CROW-Fietsberaad Dashboard Deelmobiliteit][db] hoe gegevens van deelmobiliteit aangeleverd moeten worden.

</div>

[db]: https://dashboarddeelmobiliteit.nl/
[cdsm]: https://www.amsterdam.nl/innovatie/mobiliteit/city-data-standard-mobility/
[mds-provider-api]: https://github.com/openmobilityfoundation/mobility-data-specification/blob/main/provider/README.md#mobility-data-specification-provider