# Saint Petersburg for Subway Builder

Saint Petersburg and its agglomeration: 5,887 km² from Kronstadt and Peterhof in
the west to Vsevolozhsk and Gatchina in the east, 6.8 million residents, and a
river delta that decides where you can dig.

![Coverage of the map](gallery/preview.webp)

Petersburg runs six metro lines and about seventy stations for five million
people. Everyone here agrees that is too small; most of the network was planned
in the 1980s and never built. This is my home town, and I have wanted to put it
into Subway Builder since the first time I played it. I wanted the map as
accurate as I could make it: where the demand sits, how deep the Neva runs, what
it costs to cross it.

*[на русском](README.ru.md)*

## Install

Use [Railyard](https://github.com/Subway-Builder-Modded), the mod manager:
find **Санкт-Петербург (Saint Petersburg)** in its catalogue.

For a manual install, download `SPB-0.15.0.zip` from [Releases](../../releases).
Put `SPB.pmtiles` and `SPB_foundations.pmtiles` in the game's `tiles/` folder
and the remaining files in `cities/data/SPB/`.

## What is in it

| | |
|---|---:|
| Playable area | 5,887 km² (73 × 81 km) |
| Municipalities | 283 |
| Residents in housing layer | 6,839,575 |
| Modelled workplaces in frame | 3,787,103 |
| Demand points | 33,236 |
| Demand links | 162,475, including 129,257 commute links |
| Game `population` value | 5,236,483 |
| Median modelled road route | 16.4 min / 9.5 km |

The game's `population` field sums the sizes of demand links on the chosen day.
It is **not a count of distinct residents**: someone can commute and visit a
shop on the same day. The housing layer contains 6,839,575 residents.

Also inside the frame: Kronstadt, Peterhof, Lomonosov, Sestroretsk, Zelenogorsk,
Pushkin, Pavlovsk, Kolpino, Gatchina, Vsevolozhsk, Murino, Kudrovo, Sertolovo,
Toksovo.

## Demand and method

Residents are placed in buildings from Rosstat municipal totals, flat counts,
floor area and building type. The Saint Petersburg total of **employed
residents** is anchored to 3,215,900 in [Petrostat's 2025 labour force survey](https://78.rosstat.gov.ru/folder/32168).
Workplaces use a different measure, **employment by place of work**:
[the 2024 labour resources balance](https://78.rosstat.gov.ru/storage/mediabank/11000125.pdf)
reports 3,417,900 for the city; 3,416,006 are placed inside the map's city
frame. Observed employees of larger organisations are supplemented by a modelled
remainder that covers small businesses, sole proprietors, self-employment, and
differences in coverage and year. The allocation to individual buildings is an
estimate.

The home-to-work matrix balances employed residents and workplaces. The former
practice of scaling all commutes to the full resident population has been removed.
An estimated 48,303 employed residents of the oblast portion work beyond the
map frame; their local origins have not been observed directly.

The map adds 2,150 attraction points and 1,449,966 visits for a weekday in late
September. Every planned visit is present in the game file:

| | points | visits |
|---|---:|---:|
| Schools | 1,177 | 673,602 |
| Universities | 214 | 229,474 |
| Parks | 244 | 109,590 |
| Museums | 33 | 76,772 |
| Hospitals | 135 | 68,492 |
| Pulkovo airport | 1 | 60,123 |
| Railway terminals | 5 | 58,630 |
| Shopping centres | 11 | 52,053 |
| Theatres and concert halls | 71 | 38,573 |
| Other attractions | 259 | 82,657 |
| **Total** | **2,150** | **1,449,966** |

Only an estimated external share of the five railway terminals' traffic is
added; journeys from Gatchina, Pushkin and Vsevolozhsk are already modelled
within the map. The game has no time axis, so these visits do not form full
home–work–shop–home trip chains.

## Checks and limitations

| layer | check | result |
|---|---|---|
| Residents | district sums against Petrostat | 5,689,116 modelled against 5,652,922 published |
| Employed residents | 2025 labour force survey, city | 3,215,900 modelled and published |
| Jobs | 2024 labour balance, city | 3,416,006 in frame against 3,417,900 citywide |
| Demand | link and point sums | 3,786,517 commute visits plus 1,449,966 attraction visits |
| Routes | OSM road graph | paths found for all 162,475 links |

The [city transport committee](https://www.gov.spb.ru/gov/otrasl/c_transport/news/310977/)
reports 669.3 million metro boardings, over 775 million bus boardings and over
285 million tram and trolleybus boardings in 2025. Boardings are not unique
journeys: transfers count again. No verified contemporary citywide total of car
trips was available, so annual boardings were not used as a simple multiplier
for the map. Comparable station-entry counts have not yet been checked. The
geography of small settlements and individual buildings is less certain than
the regional totals.

More detail: [methodology and limitations](METHODOLOGY.md),
[sources and licences](ATTRIBUTION.md),
[0.15.0 release notes](../../releases/tag/v0.15.0).

## The map

Petersburg is built on water, so the water is measured rather than left at the
default. The Neva runs 24 m deep at Liteyny Bridge, the Winter Canal 2 m, and the
dredged fairways of the Neva Bay cut 13 m channels through 3 m shallows. A tunnel
under the river and a tunnel under a canal therefore cost differently.

Heights come from the OSM `height` tag, or from `building:levels` at a
measured 3.88 m per storey, or from the nearest neighbours that have either.
Against 6,463 surveyed buildings held back from the model the mean error is
3.8 m, where a flat default gives 11.6 m.

Volumes are stepped: 21,126 `building:part` polygons sit on top of their
outlines, so St Isaac's is a dome at 18 m with a cross at 102 m instead of a
100 m wall. Lakhta Center, the TV tower, the Peter and Paul spire and Gazprom
Arena are placed by hand.

## Sources and licences

Every source used to build the map, with its address and licence, is in
[ATTRIBUTION.md](ATTRIBUTION.md) ([по-русски](ATTRIBUTION.ru.md)).

Map data © OpenStreetMap contributors, ODbL 1.0. Bathymetry from GEBCO 2026.
Population and employment from Rosstat, the 2020 Russian census and Petrostat.

## Credits

Map by **SindieFox**, built with [depot](https://github.com/Subway-Builder-Modded).
