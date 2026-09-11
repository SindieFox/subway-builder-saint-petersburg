# Saint Petersburg for Subway Builder

Saint Petersburg and its agglomeration: 5,887 km² from Kronstadt and Peterhof in
the west to Vsevolozhsk and Gatchina in the east, 6.8 million residents, and a
river delta that decides where you can dig.

![Coverage of the map](gallery/preview.webp)

Petersburg runs six metro lines and about seventy stations for five million
people. Everyone here agrees that is too small; most of the network was planned
in the 1980s and never built. This is my home town, and I have wanted to put it
into Subway Builder since the first time I played it. That set the standard for
the map: accurate enough that the answers mean something. Where the demand sits,
how deep the Neva runs, what it costs to cross it.

*[на русском](README.ru.md)*

## Install

Through [Railyard](https://github.com/Subway-Builder-Modded), the mod manager:
find **Санкт-Петербург (Saint Petersburg)** in the catalogue and install it.

By hand: download `SPB-0.14.0.zip` from [Releases](../../releases), unpack it,
put `SPB.pmtiles` in the game's `tiles/` folder and everything else in
`cities/data/SPB/`.

## What is in it

| | |
|---|---|
| Playable area | 5,887 km² (73 × 81 km) |
| Municipalities | 283 municipal units |
| Residents | 6,790,069 |
| Jobs | 2,773,251 |
| Demand points | 30,815 |
| Demand links | 152,778, of which 121,967 home–work |
| Buildings | 954,473 |
| Median commute | 16.3 min / 9.4 km at 35 km/h |

Also inside the frame: Kronstadt, Peterhof, Lomonosov, Sestroretsk, Zelenogorsk,
Pushkin, Pavlovsk, Kolpino, Gatchina, Vsevolozhsk, Murino, Kudrovo, Sertolovo,
Toksovo.

## Demand

Residents come from the Rosstat municipal database and are spread over 210,660
building footprints: by flat count where OSM has it, by floor area and building
type everywhere else. Jobs come from the same database, weighted by a sector
profile. The commuting matrix is a gravity model balanced against the 2020
census.

On top of that, 2,150 attraction points carrying 1.39 million trips a day:

| | points | daily |
|---|---:|---:|
| Schools | 1,177 | 644,625 |
| Universities | 214 | 220,995 |
| Parks | 244 | 99,990 |
| Museums | 33 | 74,700 |
| Hospitals | 135 | 64,845 |
| Pulkovo airport | 1 | 60,120 |
| Railway terminals | 5 | 58,500 |
| Shopping centres | 11 | 51,795 |
| Theatres and concert halls | 71 | 36,990 |

The game's demand model has no time axis, so the map has to pick a day, and it
picks **a weekday in late September**: universities and schools in session,
tourism still high, the dacha season over. A year-average would describe a day
that never happens.

The five railway terminals deserve a mention. The registry's special-demand
vocabulary has no category for intercity rail, so they go in as generic external
demand, and in Petersburg they decide a lot: Baltiysky is the second-busiest
terminal in the city and carries no long-distance trains at all, only suburban
traffic.

## How it was checked

Every layer is built from one official source and then checked against a
different one, so a mistake in the source cannot confirm itself.

| layer | check | result |
|---|---|---|
| Residents | sums per district against Petrostat | 5,689,116 modelled against 5,652,922 published |
| Residents | persons per flat, 3,616 buildings with `building:flats` | 2.10 against a household size of ~2.1 |
| Jobs | total inside the city limits | 2,536,953 against 2,561,555 in the 2020 census |
| Jobs | jobs per employed resident | 1.01 against 1.03 in the census |
| Commuting | oblast-to-city flow | 191,737 against 154,675 in the census |
| Travel times | median door-to-door speed | 35 km/h, against 33 in vanilla Paris |

The commuting overshoot has an explanation. The census is from 2020 and the
population here is 2025, and in those years Murino grew from 74 to 117 thousand
and Kudrovo almost doubled.

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
