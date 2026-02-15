# Airport metadata

Useful metadata about airports.

## Usage

``` r
airports
```

## Format

A data frame with columns:

- faa:

  FAA airport code.

- name:

  Usual name of the airport.

- lat, lon:

  Location of airport.

- alt:

  Altitude, in feet.

- tz:

  Timezone offset from GMT.

- dst:

  Daylight savings time zone. A = Standard US DST: starts on the second
  Sunday of March, ends on the first Sunday of November. U = unknown. N
  = no dst.

- tzone:

  IANA time zone, as determined by GeoNames webservice.

## Source

<https://openflights.org/data.html>, downloaded 2014-06-27

## Examples

``` r
airports
#> # A tibble: 1,458 × 8
#>    faa   name                        lat    lon   alt    tz dst   tzone
#>    <chr> <chr>                     <dbl>  <dbl> <dbl> <dbl> <chr> <chr>
#>  1 04G   Lansdowne Airport          41.1  -80.6  1044    -5 A     Amer…
#>  2 06A   Moton Field Municipal Ai…  32.5  -85.7   264    -6 A     Amer…
#>  3 06C   Schaumburg Regional        42.0  -88.1   801    -6 A     Amer…
#>  4 06N   Randall Airport            41.4  -74.4   523    -5 A     Amer…
#>  5 09J   Jekyll Island Airport      31.1  -81.4    11    -5 A     Amer…
#>  6 0A9   Elizabethton Municipal A…  36.4  -82.2  1593    -5 A     Amer…
#>  7 0G6   Williams County Airport    41.5  -84.5   730    -5 A     Amer…
#>  8 0G7   Finger Lakes Regional Ai…  42.9  -76.8   492    -5 A     Amer…
#>  9 0P2   Shoestring Aviation Airf…  39.8  -76.6  1000    -5 U     Amer…
#> 10 0S9   Jefferson County Intl      48.1 -123.    108    -8 A     Amer…
#> # ℹ 1,448 more rows

if (require("dplyr")) {

airports %>% rename(dest = faa) %>% semi_join(flights)
flights %>% anti_join(airports %>% rename(dest = faa))
airports %>% rename(origin = faa) %>% semi_join(flights)

}
#> Loading required package: dplyr
#> 
#> Attaching package: ‘dplyr’
#> The following objects are masked from ‘package:stats’:
#> 
#>     filter, lag
#> The following objects are masked from ‘package:base’:
#> 
#>     intersect, setdiff, setequal, union
#> Joining with `by = join_by(dest)`
#> Joining with `by = join_by(dest)`
#> Joining with `by = join_by(origin)`
#> # A tibble: 3 × 8
#>   origin name                  lat   lon   alt    tz dst   tzone       
#>   <chr>  <chr>               <dbl> <dbl> <dbl> <dbl> <chr> <chr>       
#> 1 EWR    Newark Liberty Intl  40.7 -74.2    18    -5 A     America/New…
#> 2 JFK    John F Kennedy Intl  40.6 -73.8    13    -5 A     America/New…
#> 3 LGA    La Guardia           40.8 -73.9    22    -5 A     America/New…
```
