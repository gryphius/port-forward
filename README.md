This is a simple command line utitly to forward ports from your router to a host in the LAN.

For this to work, the UPnP feature must be enabled on your router.

Source: This utility uses the code examples from http://mattscodecave.com/posts/using-python-and-upnp-to-forward-a-port.html

Usage examples:

forward the webserver port 80 to your local machine:

```
./port-forward.py -v -e 80
```

full argument list:

```
./port-forward.py --help
usage: port-forward.py [-h] [-v] [-e EPORT] [-l IPORT] [-i LANIP] [-r ROUTER]
                       [-p PROTOCOL] [-d DESCRIPTION] [--disable] [-t TIME]

optional arguments:
  -h, --help            show this help message and exit
  -v, --verbose         verbose output
  -e EPORT, --external-port EPORT
                        external port to open
  -l IPORT, --local-port IPORT
                        internal port (default: same as external)
  -i LANIP, --lan-ip LANIP
                        lan-ip where to forward the port, this computer if not
                        specified
  -r ROUTER, --router ROUTER
                        router ip to use. by default uses all discovered
                        routers
  -p PROTOCOL, --protocol PROTOCOL
                        TCP or UDP
  -d DESCRIPTION, --description DESCRIPTION
                        description for the rule
  --disable             disable a existing forwarding
  -t TIME, --time TIME  Duration of the rule
```

just show UPnP capable routers:

```
./port-forward.py 
Found 2 UPnP routers:  192.168.1.1:49152 192.168.1.254:2189
No external port specified.
```

forward to a different local port for a few seconds only:

```
./port-forward.py -e 1337 -v -t 30 -r 192.168.1.1  -l 9999 -d 'forward 1337 to 9999'
Discovering routers...
Found 2 UPnP routers:  192.168.1.1:49152 192.168.1.254:2189
port forward on 192.168.1.1 successful, 1337->192.168.1.22:9999
```
