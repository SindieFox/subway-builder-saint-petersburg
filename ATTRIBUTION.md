# Sources and licences

Everything the map is built from, with the address it was taken from. Some of it
the build scripts download themselves, the rest was downloaded by hand; either
way the address below is the original, so anything here can be checked or pulled
again. The files themselves are kept with the build pipeline and not copied into
this repository.

## Map data

| source | address | licence |
|---|---|---|
| OpenStreetMap, Northwestern Federal District extract | [download.geofabrik.de](https://download.geofabrik.de/russia/northwestern-fed-district-latest.osm.pbf) | ODbL 1.0 |
| Overture Maps, buildings theme | [overturemaps.org](https://overturemaps.org/), bucket `s3://overturemaps-us-west-2` | ODbL 1.0 |
| GEBCO 2026 sub-ice grid | [gebco.net](https://www.gebco.net/), served from [CEDA](https://dap.ceda.ac.uk/thredds/ncss/grid/bodc/gebco/global/gebco_2026/sub_ice_topography_bathymetry/netcdf/GEBCO_2026_sub_ice.nc) | free with the source named |
| Wikidata, property P2048 (height) | [query.wikidata.org/sparql](https://query.wikidata.org/sparql) | CC0 |

OSM gives roads, water, land use, labels and building tags. Overture gives the
955,711 footprints the map is drawn from. GEBCO gives the Gulf of Finland;
depths for the Neva, the Nevkas, the canals and the Neva Bay fairways come from
navigation charts and are held as a table in the build pipeline, because GEBCO
has a step of about 450 m and does not see a river 200 to 400 m wide.

Required attribution line for the map data:

> Map data © OpenStreetMap contributors, ODbL 1.0.

## Population and employment

| source | address | what was taken |
|---|---|---|
| Rosstat, municipal indicators database (БД ПМО) | [rosstat.gov.ru](https://rosstat.gov.ru/scripts/db_inet2/passport/munr.aspx) | population of 283 municipal units and average headcount of organisation employees in 129 of them, by OKVED section, 2025 |
| Petrostat, population by municipal unit, 01.01.2024 and 01.01.2025 | [78.rosstat.gov.ru](https://78.rosstat.gov.ru/folder/27595) | control totals for Saint Petersburg and Leningrad oblast |
| Petrostat, age and sex composition bulletins, 2024 | [78.rosstat.gov.ru](https://78.rosstat.gov.ru/folder/27595) | age structure of 18 city districts and 18 oblast districts, from which the employed share is computed per district |
| Petrostat, 2025 labour force survey, table 1.1 | [bulletin](https://78.rosstat.gov.ru/folder/32168) | 3,215,900 employed residents of Saint Petersburg and 1,109,000 in all of Leningrad oblast, annual averages |
| Petrostat, 2024 labour resources balance, table 4.4 | [yearbook](https://78.rosstat.gov.ru/storage/mediabank/11000125.pdf) | 3,417,900 employed by place of work in Saint Petersburg |
| Rosstat, Regions of Russia 2025 | [yearbook](https://rosstat.gov.ru/storage/mediabank/Region_Subekt_2025.pdf) | 893,700 employed by place of work in all of Leningrad oblast in 2024 |
| Petrostat, express information RAB2540 | [78.rosstat.gov.ru](https://78.rosstat.gov.ru/) | employment by OKVED section for the whole city, 1,552,800, used to check the sector profile |
| Russian census 2020 (ВПН-2020), volume 10 "Labour force", tables 1–12 | [rosstat.gov.ru/vpn/2020](https://rosstat.gov.ru/vpn/2020) | commuting marginals: 2,490,665 employed in the city, 888,216 in the oblast, 154,675 of them working in another region |

Rosstat and census data are official statistics published for free use.

## Attraction points

| source | address | what was taken |
|---|---|---|
| Ministry of Education monitoring of higher education, via the "Если быть точным" open catalogue | [monitoring.miccedu.ru](https://monitoring.miccedu.ru/?m=vpo), mirror at [storage.yandexcloud.net](https://storage.yandexcloud.net/tochno-st-catalog/Minobr/data_performance_137_v20260223/data_performance_137_v202602023.parquet) | full-time enrolment of 70 institutions in the city and the oblast, 269,979 students |
| Ministry of Culture open data, museum returns (8-НК) | [opendata.mkrf.ru](https://opendata.mkrf.ru/opendata/7705851331-stat_museum_svod) | museum attendance |
| Ministry of Culture open data, theatre returns | [opendata.mkrf.ru](https://opendata.mkrf.ru/opendata/7705851331-stat_theaters_svod) | theatre attendance |
| Pulkovo airport press releases | [pulkovoairport.ru](https://pulkovoairport.ru/about/press_center/news/) | 20.9 M passengers in 2025 |
| October Railway terminal figures for 2024, as reported in the press | | 38.5 M through the five terminals, of which 27.5 M suburban |
| Museum attendance reported by The Art Newspaper Russia, TASS, Interfax and dp.ru | | the Hermitage 3.56 M, the Russian Museum 3.6 M, Peterhof over 5 M, Tsarskoye Selo 3.7 M, St Isaac's over 3 M |
| Russian Premier League and KHL attendance | | Gazprom Arena and the SKA arena, by match |
| City school enrolment for 2025/26 | | 619,000 pupils, plus an estimate for the part of the oblast inside the frame |

Shopping-centre footfall has no open source. Only Galereya publishes a figure;
the other ten are scaled from it by floor area and from numbers that turn up in
the press. It is the weakest layer in the demand model.

## Transport cross-checks

| source | address | what it can check |
|---|---|---|
| Saint Petersburg transport committee, 2025 totals | [gov.spb.ru](https://www.gov.spb.ru/gov/otrasl/c_transport/news/310977/) | 669.3 million metro boardings, over 775 million bus boardings, over 285 million tram and trolleybus boardings |
| Transport System Development Directorate, 2024 survey | [spbtrd.ru](https://spbtrd.ru/press-center/news/2024/oktyabr_/rezultaty_sotsiologicheskogo_issledovaniya_kak_izmenilos_mnenie_zhiteley_sankt_peterburga_i_leningra/) | shares of respondents using a car, metro and bus; not trip mode shares |

The old per station metro table covers 2021 and does not validate the 2025
demand model. The method and limits are explained in [METHODOLOGY.md](METHODOLOGY.md).

## Tooling

The map is built with [depot](https://github.com/Subway-Builder-Modded), a map
generator for Subway Builder distributed under the GNU GPL v3. The build
pipeline itself is not part of this repository.

---

*[Тот же список по-русски](ATTRIBUTION.ru.md)*
