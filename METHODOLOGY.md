# Demand methodology in version 0.15.0

*[По-русски](METHODOLOGY.ru.md)*

The map represents **a weekday in late September**. Several different
quantities must be kept separate. The housing layer contains 6,839,575
residents. Petrostat's labour force survey counts 3,215,900 employed
*residents* of Saint Petersburg. The city portion of the map holds 3,416,006
modelled jobs. The game `population` field is 5,236,483: it sums the sizes of
commute and attraction links, so it is not a count of distinct people.

## 1. Residents and workplaces

Residents are assigned to 210,660 residential buildings using
[Rosstat municipal totals](https://rosstat.gov.ru/scripts/db_inet2/passport/munr.aspx),
flat counts, floor area and building type. A further 121,638 residents are
estimated in ten fast growing municipalities where registration may lag behind
occupation of new apartments. The full housing layer has 6,839,575 residents.
The city district check is 5,689,116 modelled against 5,652,922 published by
Petrostat.

[Petrostat's 2025 labour force survey](https://78.rosstat.gov.ru/folder/32168),
table 1.1, reports **3,215,900 employed residents of Saint Petersburg** and
**1,109,000 for all of Leningrad oblast**. It covers multiple forms of work and
counts people by residence. Organisational employment from Rosstat's municipal
database and building characteristics guide the placement and sector mix of
workplaces. Their total is controlled by a different measure, employment *by
place of work*: [the city's 2024 labour resources balance](https://78.rosstat.gov.ru/storage/mediabank/11000125.pdf),
table 4.4, reports **3,417,900**. The 2024 benchmark for all of Leningrad
oblast is **893,700** ([Rosstat regional yearbook](https://rosstat.gov.ru/storage/mediabank/Region_Subekt_2025.pdf));
only part of the oblast is on the map. The map contains 3,416,006 city jobs and
371,097 oblast jobs, **3,787,103** in total.

The unobserved remainder is allocated by sector to suitable buildings with
floor area limits. It covers small firms, sole proprietors, self employment,
and differences between the years and the scope of the sources. Thus the city
total is close to the published benchmark, while employment in any individual
building remains a model estimate. Some residential municipalities lack enough
suitable nonresidential floor area; their local job totals fall as much as 32%
below target.

## 2. Commuting and attractions

The matrix between 283 municipal units is constrained by employed residents at
origins and jobs at destinations. Workplace choice declines with distance; the
ratio of cross boundary flows is calibrated against the
[2020 census](https://rosstat.gov.ru/vpn/2020). This shapes the matrix but does
not measure 2025 flows. Of an estimated 619,506 employed residents in the
oblast portion, 48,303 are excluded from the in frame matrix as workers whose
jobs lie beyond the map. Their exact local origins are unknown.

The municipal matrix sums to **3,787,103**. Sampling buildings and rounding
groups leave **3,786,517** commute link size in the game file, a difference of
586. Another **1,449,966** visits go to 2,150 schools, universities, hospitals,
parks, museums, shopping centres, railway terminals and other attractions.
The full planned attraction total is represented. Visitors can be the same
people who commute to work, so the game link sum of **5,236,483** is not a
population count.

The game format stores neither full trip chains nor time of day. Road distance
and time for each link come from the OSM road graph. All 162,475 links are
reachable; the median route is 9.5 km and 16.4 minutes.

## 3. Transport comparison and uncertainty

The [Saint Petersburg transport committee](https://www.gov.spb.ru/gov/otrasl/c_transport/news/310977/)
reports 669.3 million metro boardings, over 775 million bus boardings and over
285 million tram and trolleybus boardings for 2025. Dividing by 365 gives
about 1.83 million, over 2.12 million and over 0.78 million boardings on an
average calendar day. A transfer produces another boarding, while the map
represents a particular September weekday. No verified contemporary total of
citywide car trips was found. These annual boardings therefore do not supply
a defensible multiplier for game demand.

A [2024 survey](https://spbtrd.ru/press-center/news/2024/oktyabr_/rezultaty_sotsiologicheskogo_issledovaniya_kak_izmenilos_mnenie_zhiteley_sankt_peterburga_i_leningra/)
found that 28% of respondents used a car, 32.1% the metro and 47.8% a bus.
These are overlapping shares of *people naming a mode*, not mode shares of
trips. The old per station metro table in the build pipeline was from 2021 and
does not validate the geography of 2025 demand.

Regional employment totals are the strongest controls. The median relative
sampling error for destination municipalities is 2.06%, but it reaches about
43% in some small settlements. Attraction categories vary in accuracy: most
shopping centre visits, for example, are inferred from floor area because
published footfall is scarce. See [sources and licences](ATTRIBUTION.md) for
the underlying data.
