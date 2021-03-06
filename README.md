[![License Badge][]][License] [![Travis Status][]][Travis]

Micro SSDP responder for networked devices.  Useful for embedded systems
that want to announce themselves to Windows clients.

`ssdpd` is a stand-alone UNIX daemon with a built-in web server for
serving the XML description.  By default it announces itself as an
InternetGatewayDevice.  See the `configure` script for some options.


Usage
-----

```
Usage: ssdpd [-dhv] [-i SEC] [IFACE [IFACE ...]]

    -d        Developer debug mode
    -h        This help text
    -i SEC    SSDP notify interval, default 600 sec
    -r SEC    Interface refresh interval, default 600 sec
    -v        Show program version

Bug report address: https://github.com/troglobit/ssdp-responder/issues
```


Example
-------

The following example runs `ssdpd` only on interface `eth1`.  Every five
seconds the list of addresses for that interface are updated, if any new
address is added a new set of `NOTIFY *` messages are sent, otherwise
they are sent every 30 seconds.

```
ssdpd -i 30 -r 5 eth1
```


Origin
------

Cloned from [mrdisc](https://github.com/troglobit/mrdisc) and whacked at
with a bat until it replies to SSDP "MSEARCH *" messages used by Windows.

[License]:       https://en.wikipedia.org/wiki/ISC_license
[License Badge]: https://img.shields.io/badge/License-ISC-blue.svg
[Travis]:        https://travis-ci.org/troglobit/ssdp-responder
[Travis Status]: https://travis-ci.org/troglobit/ssdp-responder.png?branch=master
