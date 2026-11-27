# Carry-on size by airline: cabin bag and personal item limits (open data)

Carry-on, cabin bag and personal item size limits for 28 airlines, as open data. Each row comes from the airline's own baggage page, with the link to that page and the date we last checked it.

This is the data behind the free [Vilanera hand-luggage size checker](https://vilanera.com/pages/hand-luggage-checker), where you can enter a bag's measurements and see whether it fits.

## Files

| File | Format |
|---|---|
| [`data/airlines.json`](data/airlines.json) | JSON, dimensions as `[length, width, height]` |
| [`data/airlines.csv`](data/airlines.csv) | CSV, dimensions as `55 x 40 x 23` |

Both files hold the same rows and are generated together. Please don't edit them directly in a pull request (see [Corrections](#corrections)).

## Fields

| Field | Meaning |
|---|---|
| `airline` | Airline name |
| `iata` | IATA airline code |
| `allowance_model` | What the cheapest fare includes (see below). Empty where we have not classified the airline yet |
| `native_unit` | The unit the airline publishes its sizes in: `cm` or `in` |
| `native_weight_unit` | `kg` or `lb`, matching `native_unit` |
| `cabin_bag` | Cabin bag size limit in the airline's own unit |
| `cabin_bag_cm` | The same limit in centimetres |
| `cabin_bag_weight` | Cabin bag weight limit in the airline's own unit. Empty if the airline publishes none |
| `cabin_bag_weight_kg` | The same limit in kilograms |
| `personal_item` | Personal item (under-seat bag) size limit in the airline's own unit. Empty if the airline publishes no size |
| `personal_item_cm` | The same limit in centimetres |
| `personal_item_weight` | Personal item weight limit in the airline's own unit. Empty if the airline publishes none |
| `personal_item_weight_kg` | The same limit in kilograms |
| `verified_on` | Date we last read the limits on the airline's page (`YYYY-MM-DD`) |
| `source_url` | The airline page the limits come from |
| `source_url_2` | A second airline page, where the rules are split across two |
| `checker_url` | The checker page for this airline, with fare details and exceptions |

### Allowance model

| Value | Meaning |
|---|---|
| `both_free` | A cabin bag and a personal item are both included on every fare |
| `carryon_fare_dependent` | A personal item is always included. The cabin bag depends on the fare, or is a paid extra |

## How to read the numbers

- **The airline's own unit is the reference.** If an airline publishes 22 x 14 x 9 inches, that is the limit. The centimetre figure next to it is our conversion.
- **Conversions are rounded down.** 22 inches is 55.88 cm and appears here as 55.8 cm, so a bag that fits our converted figure also fits the airline's.
- **Empty means "not published", not "no limit".** Some airlines only say a personal item must fit under the seat.
- **Check `verified_on`.** Airlines change these rules without notice. The source link is there so you can confirm before you rely on a number.

Limits can also differ by fare, route, cabin class or aircraft. The dataset holds the standard economy limit; the `checker_url` page covers the exceptions.

## Corrections

Found a number that is out of date? Please [open an issue](../../issues) with the airline and a link to the page showing the current rule. We check it against the airline's page, fix it at the source, and the files here are regenerated.

## License

The data is released under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). You can use it for anything, including commercial projects, as long as you credit the source with a link:

> Data: [Vilanera hand-luggage size checker](https://vilanera.com/pages/hand-luggage-checker)
