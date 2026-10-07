# Version 0.15.0 — demand rebuild

The map's job totals and travel demand have been recalculated against published
Petrostat and Rosstat figures. The map geometry has not changed.

- 3,787,103 modelled workplaces in the map frame. The city portion contains
  3,416,006, compared with 3,417,900 employed by place of work in the city's
  2024 labour resources balance.
- 3,215,900 employed city residents, anchored to Petrostat's 2025 labour force
  survey. Commuting is no longer scaled to the entire resident population.
- 3,786,517 commute link size in the game file and 1,449,966 attraction visits
  at 2,150 points. A rounding loss in attraction placement has been fixed.
- The game's `population` value is now 5,236,483. It sums demand links, while
  the housing layer contains 6,839,575 residents. These are different measures.
- Road routes have been recalculated for every link; no link is unreachable.

The [methodology](METHODOLOGY.md) explains the source definitions, how small
business and self employment are modelled, the comparison with 2025 public
transport boardings, and the remaining uncertainty in local geography and car
travel.

## По-русски

Спрос и рабочие места пересчитаны по опубликованным данным Петростата и
Росстата; геометрия карты не изменилась. В рамке 3 787 103 рабочих места,
в том числе 3 416 006 в Петербурге против 3 417 900 занятых по месту работы
в балансе за 2024 год. Число занятых жителей Петербурга приведено к
3 215 900 по ОРС-2025. Трудовые поездки больше не домножаются до полного
населения.

В игровом файле 3 786 517 трудовых связей и 1 449 966 посещений 2 150
специальных точек. Потеря посещений при округлении исправлена. Игровой
показатель `population` равен 5 236 483 и означает сумму размеров связей;
в жилом слое живут 6 839 575 человек. Маршруты пересчитаны для всех связей.
Источники, сравнение с транспортом и ограничения описаны в
[методике](METHODOLOGY.ru.md).
