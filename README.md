# googerteller
audible feedback on just how much your browsing feeds into google

By bert@hubertnet.nl / https://berthub.eu/

## How to compile

First install libpcaudio (libpcaudio-dev) and build tools (cmake, build-essential), then:

```
cmake .
make
```

## How to run:

```
sudo tcpdump -i any -n -l dst net 192.0.2.1/32 $(for a in $(cat goog-prefixes.txt); do echo or dst net $a; done) |  ./teller
```

And then cry.

## Problems
If tcpdump complains about `Warning: Kernel filter failed: Cannot allocate memory`, try
this first:

```
sudo sysctl net.core.optmem_max=204800
```

## Data source
The list of Google services IP addresses can be found on [this Google
support page](https://support.google.com/a/answer/10026322?hl=en).

Note that this splits out Google services and Google cloud user IP
addresses.
