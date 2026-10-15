# Reviewed examples and limits
Examples are demonstrations, not fixed municipal definitions or universal layer IDs. Historical results are not live answers.

## Count inside a selected polygon, 2026-10-04
Public endpoint; GetLayersCount; pointLayerCode=527; polygonLayerCode=771; polygonLayerWhere=`oid_ezor = 11`; projection=`itm`.
Observed SOAP numeric strings:
| pointLayerWhere | Result |
|---|---:|
| id_ktovet = 118130 | 1, repeated |
| k_rechov = 187 | 153 |
| k_rechov = 11 | 1 |
No independent spatial recount was performed for the two street-wide results.
Controlled projection comparison, same address and polygon filters: `itm` -> 1; `2039` -> `error, invalid projection`. This confirms the rejection for this operation/test; do not infer that all services reject EPSG codes.
With the same single address and `itm`, polygon 771 filtered by `1=1` returned 0. Other probes using polygons 495 and 491 with `1=1` returned `שגיאה Cannot perform runtime binding on a null reference`. Resource existence/metadata for those two public layers was not separately checked in this experiment. Cause remains unresolved; the supported recipe is a selected polygon, not unrestricted polygon aggregation.

Historically executed public count request — reproduction requires explicit approval if the assistant sends it (reproduction may return different current data):
```bash
curl --location 'https://gisn.tel-aviv.gov.il/GisOpenData/service.asmx' \
--header 'Content-Type: text/xml; charset=utf-8' \
--header 'SOAPAction: "http://tempuri.org/GetLayersCount"' \
--data '<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"><soap:Body><GetLayersCount xmlns="http://tempuri.org/"><pointLayerCode>527</pointLayerCode><pointLayerWhere>id_ktovet = 118130</pointLayerWhere><polygonLayerCode>771</polygonLayerCode><polygonLayerWhere>oid_ezor = 11</polygonLayerWhere><projection>itm</projection></GetLayersCount></soap:Body></soap:Envelope>'
```

## Other October 4 live observations
- GetLayerFields2, public layerCode=768: HTTP 200, SOAP error converting JArray to string. GetLayerFields with the same input returned field definitions. Do not describe a nonempty Fields2 string as success.
- GetMekomot, public no-input call: 401 Esri JSON points, SR 2039, attribute shem (שם), x/y geometry. Places and points of interest such as צומת גלילות and נמל תל אביב. No category or place-code attribute was returned. Its documentation repeats map/zoom arguments despite an empty signature.

## School example: promising, not a fully reviewed general recipe
A historical test queried public address 527, registration polygons 793, and year-labelled assignment layers 928/987 for Dizengoff 50. It reported גבריאלי-הכרמל / 30551 for תשפו/תשפז. The textual assignment filter used `LIKE 'דיזנגוף 50%'`, which is not an exact address identity check. Do not reuse the reported assignment as a verified current answer or assert those are always the latest years.
Ask which registration domain is meant before silently choosing schools; then obtain education level/stream/year when they change the result. Distinguish containment, explicit address assignment and kindergarten feeder-school mapping. Inspect current metadata and exact records.

## Evidence reconciliation — September 17 tests exported from FavGS
Successful saved tests exist for GetGeoFromItm, GetItmFromGeo, GetItmFromWebMercator, GetAddressesFromItm/Geo, GetAddressClosestToItm/Itm2/Geo2, GetCoordinatesFromAddress/Address2, IsPointInTelAvivItm/Geo, IsPointInsideLayerItm/Geo and GetAddressesFromStreet. Some functions.csv observation cells still say untested. These tests establish only their recorded fixtures.
Garbage and cleaning Address/ITM/Geo variants returned nonempty matching results for the tested address. Gezem variants returned empty results; the tester allowed emptiness. A PASS flag in that case does not prove a usable gezem day was found.
Metadata spelling, stale descriptions and copied WSDL text must not be silently normalized into claimed source truth. Exact wire names are in service.wsdl and function_args.csv's added wire column.
