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

### scan techniques

```prompt
$ # read the docs bro
$ man nmap(1)  # then search for the scan flag
```

It is important to remember that nmap uses raw IP packets
that are sent over TCP to the target, so you must understand
the bare basics of the TCP protocol.

`-sS` - SYN scan. It is a scan where nmap sends a packet, the
port respond with the syn/ack packet but nmap ignores it and
doesn't connect. Because it doesn't connect to a host, it is
fast and quite silent.

`-sT` - TCP Connect scan. When Syn scan is not an option,
we must use the connect scan. Read the docs

## nmap scripting engine

The is this NSE (nmap scripting engine) that allows you to have
programmatically access to nmap scan data with Lua code. For you
that don't know, lua is a programming language largely used for
scripting.

NSE allows you to automate some activities, check for vulnerabilities
in a system, etc. For example, if you noticed that the system runs
a FTP server and want to test if `anonymous` login is allowed in that
server, you can use the command:

```prompt
$ nmap --script=ftp-anon <target>
```

And nmap, using nmap scripting engine, will automate the task
specified in the script (check for anonymous login). You can
learn NSE by understanding the global variables passed to the
script by nmap and a bit of lua language (if you are familiar
with C or any programming language, it will not be a big of a
deal).

## References

- Nmap docs: `$ man nmap`
- Nmap website: https://nmap.org
- Documentation on NSE: https://nmap.org/book/man-nse.html
- How the TCP protocol works: https://en.wikipedia.org/wiki/Internet\_protocol\_suite
