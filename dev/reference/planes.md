# Plane metadata

Plane metadata for all plane tailnumbers found in the FAA aircraft
registry. American Airways (AA) and Envoy Air (MQ) report fleet numbers
rather than tail numbers so can't be matched.

## Usage

``` r
planes
```

## Format

A data frame with columns:

- tailnum:

  Tail number.

- year:

  Year manufactured.

- type:

  Type of plane.

- manufacturer, model:

  Manufacturer and model.

- engines, seats:

  Number of engines and seats.

- speed:

  Average cruising speed in mph.

- engine:

  Type of engine.

## Source

FAA Aircraft registry,
<https://www.faa.gov/licenses_certificates/aircraft_certification/aircraft_registry/releasable_aircraft_download/>

## Examples

``` r
planes
#> # A tibble: 3,322 × 9
#>    tailnum  year type     manufacturer model engines seats speed engine
#>    <chr>   <int> <chr>    <chr>        <chr>   <int> <int> <int> <chr> 
#>  1 N10156   2004 Fixed w… EMBRAER      EMB-…       2    55    NA Turbo…
#>  2 N102UW   1998 Fixed w… AIRBUS INDU… A320…       2   182    NA Turbo…
#>  3 N103US   1999 Fixed w… AIRBUS INDU… A320…       2   182    NA Turbo…
#>  4 N104UW   1999 Fixed w… AIRBUS INDU… A320…       2   182    NA Turbo…
#>  5 N10575   2002 Fixed w… EMBRAER      EMB-…       2    55    NA Turbo…
#>  6 N105UW   1999 Fixed w… AIRBUS INDU… A320…       2   182    NA Turbo…
#>  7 N107US   1999 Fixed w… AIRBUS INDU… A320…       2   182    NA Turbo…
#>  8 N108UW   1999 Fixed w… AIRBUS INDU… A320…       2   182    NA Turbo…
#>  9 N109UW   1999 Fixed w… AIRBUS INDU… A320…       2   182    NA Turbo…
#> 10 N110UW   1999 Fixed w… AIRBUS INDU… A320…       2   182    NA Turbo…
#> # ℹ 3,312 more rows

if (require("dplyr")) {

# Flights that don't have plane metadata
flights %>% anti_join(planes, "tailnum")

}
#> # A tibble: 52,606 × 19
#>     year month   day dep_time sched_dep_time dep_delay arr_time
#>    <int> <int> <int>    <int>          <int>     <dbl>    <int>
#>  1  2013     1     1      558            600        -2      753
#>  2  2013     1     1      559            600        -1      941
#>  3  2013     1     1      600            600         0      837
#>  4  2013     1     1      602            605        -3      821
#>  5  2013     1     1      608            600         8      807
#>  6  2013     1     1      611            600        11      945
#>  7  2013     1     1      623            610        13      920
#>  8  2013     1     1      624            630        -6      840
#>  9  2013     1     1      628            630        -2     1137
#> 10  2013     1     1      629            630        -1      824
#> # ℹ 52,596 more rows
#> # ℹ 12 more variables: sched_arr_time <int>, arr_delay <dbl>,
#> #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>,
#> #   dest <chr>, air_time <dbl>, distance <dbl>, hour <dbl>,
#> #   minute <dbl>, time_hour <dttm>
```
