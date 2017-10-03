<!-- -*- mode: markdown; -*- -->

# Hacklab Jyväskylä visitor data dump

This database is updated daily.

All timestamps are in [POSIX time](https://en.wikipedia.org/wiki/Unix_time).
Both files contain header on the first row.

## Columns in [user.csv](user.csv) from left to right:

Column | Description
------ | -----------
id     | Visitor ID
nick   | Nickname

## Columns in [visit.csv](visit.csv) from left to right:

Column | Description
------ | -----------
id     | Visitor ID
enter  | Visit start timestamp 
leave  | Visit stop timestamp (approximate)

Join timestamp is quite accurate because most phones scan WLANs
eagerly and laptops do join WLAN right after waking from standby.

Leave time is approximate because the client normally never says
goodbye but just stops talking. In RFC 2131 it is stated that renewal
starts 0.5 * duration_of_lease and if we assume the person leaves the
premises independently from DHCP activity (in average halfaway), the
person approximately leaves at duration_of_lease * 0.5 / 2. We use
300 second lease duration so 75 seconds is added to this data to
approximate leave time.
