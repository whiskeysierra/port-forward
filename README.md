# port-forward

A utility for SSH port-forwarding.

## Usage

```
$ port-forward help

Forward one or more local ports to a remote machine using SSH.

Usage: port-forward [OPTIONS] [COMMAND] [LOCAL_PORT:]REMOTE_PORT [...[LOCAL_PORT_N:]REMOTE_PORT_N]

Commands:
  start                     Starts port forwarding (Default).
  stop                      Stops port forwarding.
  help                      Print this message.

Options:
  -c, --command             SSH command, defaults to 'ssh'. Supports PORT_FORWARD_COMMAND env var.
  -d, --dry-run             Don't do anything, just print the command.
  -f, --foreground          Open the tunnels in the foreground.
  -h, --host                Specify the hostname, defaults to 'default'. Supports PORT_FORWARD_HOST env var.

Examples
  # Listen on ports 5000 and 6000 locally, forwarding data to/from ports 5000 and 6000 on the machine
  port-forward 5000 6000

  # Listen on port 8888 locally, forwarding to 5000 on the machine
  port-forward 8888:5000

  # Change the ssh command, e.g. when using docker-machine:
  port-forward -c 'docker-machine ssh' 8080

  # Listen in the foreground, i.e. block
  port-forward -f 8080
```

## Alternatives

* [Docker Machine Port Forwarding](https://github.com/johanhaleby/docker-machine-port-forwarder)
  * Similar idea
  * Only supports docker-machine
  * Only supports single port
  * Finds PIDs based on ports and kills them, instead of a control socket
