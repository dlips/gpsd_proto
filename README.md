# gpsd_proto &emsp; [![Build Status]][travis]

[Build Status]: https://travis-ci.org/bwolf/gpsd_proto.svg?branch=master
[travis]: https://travis-ci.org/bwolf/gpsd_proto

<!--- Module documentation of src/lib.rs follows --->

The `gpsd_proto` module contains types and functions to connect to
[gpsd](http://catb.org/gpsd/) to get GPS coordinates and satellite
information.

`gpsd_proto` uses a plain TCP socket to connect to `gpsd`, reads
and writes JSON messages. The main motivation to create this crate
was independence from C libraries, like `libgps` (provided by
`gpsd`) to ease cross compiling.

A example demo application is provided in the `example` sub
directory. Check the repository for up to date sample code.

# Testing

`gpsd_proto` has been tested against `gpsd` version 3.17 on macOS
with a GPS mice (Adopt SkyTraQ Venus 8) and the iOS app
[GPS2IP](http://www.capsicumdreams.com/iphone/gps2ip/).

Feel free to report any other supported GPS by opening a GitHub
issue.

# Reference documentation

Important reference documentation of `gpsd` are the [JSON
protocol](http://www.catb.org/gpsd/gpsd_json.html) and the [client
HOWTO](http://catb.org/gpsd/client-howto.html).

# Development notes

Start `gpsd` with a real GPS device:

```sh
/usr/local/sbin/gpsd -N -D4 /dev/tty.SLAB_USBtoUART
```

Or start [gpsd](http://catb.org/gpsd/gpsd.html) with a TCP stream to a remote GPS:

```sh
/usr/local/sbin/gpsd -N -D2 tcp://192.168.177.147:11123
```

Test the connection to `gpsd` with `telnet localhost 2947` and send the string:

```text
?WATCH={"enable":true,"json":true};
```
