rust-geoip
==========

[GeoIP](http://www.maxmind.com/en/geolocation_landing) bindings for Rust.

Work in progress. Currently only supports the free
[ASN database](http://dev.maxmind.com/geoip/legacy/geolite/#Autonomous_System_Numbers).

Installation: use [Cargo](http://crates.io).

Usage:

```rust
let geoip = GeoIP::open(&Path::new("/opt/geoip/GeoIPASNum.dat"),
                        GeoIP::Options::MemoryCache).unwrap();
let ip = IpAddr::V4("91.203.184.192".parse().unwrap());
let res = geoip.as_info_by_ip(ip).unwrap();
assert!(res.asn == 41064);
assert!(res.name.contains("Telefun"));
assert!(res.netmask == 22);
```
