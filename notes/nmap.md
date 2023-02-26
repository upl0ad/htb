# nmap

```prompt
$ # please man, read the docs.
$ man nmap(1)
```

Network mapper (nmap) is the most used tool to recognize open
ports and services (and their details) in remote systems.

It has different kinds of scans, each one has a purpose. It can
try to guess the operating system that the remote machine is
using and identify possible vulnerabilities.

It has a powerful scripting engine, integrated with Lua language,
to perform activities while scanning networks, i guess you can
even develop your own scan method.

## scans

There are some kind of scans that you must know in order to
use nmap to the fullest. Each one serves a specific purpose,
so the choice of the scan type will rely on what you want to
do or identify with them.

Nmap uses raw IP packets built specifically to determine which
ports are open, which services are running on each port, which
operating system the host machine is using, etc.

### port states

open - if the port has the state "open", it means that there's
an application running on the remote machine that listens/answers
to connections to that port.

filtered - means that some firewall, filter or whatever is hiding
the true state of that port, so nmap can't determine the true
state of the port.

closed - closed ports don't have any application listening on
them, but they can be opened at any moment (if the remote system
does so)

unfiltered - means that the port respond to nmap's request, but
nmap can't actually tell the port's state.

