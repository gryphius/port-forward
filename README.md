
This is a simple command line utility to forward ports from your router to a host in the LAN.

For this to work, the UPnP feature must be enabled on your router.

Source: This utility uses the code examples from http://mattscodecave.com/posts/using-python-and-upnp-to-forward-a-port.html

Compatibility: 
port-forward.py is compatible with python 2 allows line-command
port-forward-3.py is compatible with python 3 allows line-command
portforwardlib.py can be imported and the function forwardPort ca be used to forward a port.


Usage examples:

1.
forward the webserver port 80 to your local machine:

```
./port-forward.py -v -e 80
```


2. In python 3:

''' Python
import portforwardlib 

result = porforwardlib.forwardPort(eport, iport, router, lanip, disable, protocol, time, description, verbose)

'''
eport: external port (router)
iport: internal port (local machine)
router: ip of the router, pass None to use automatically the routers found in your network
lanip: ip of the local machine, pass None to use the ip of the machine where you are running the code
disable: True to disable a previous port forwarded
time: duration, pass 0 for indefinit time
decription: a description that will appear in the interface of the router, pass None to use default description.
verbose: Print process.
result: True if forwarding was successful.




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
