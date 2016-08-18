## Installation

1. This binary requires {{VERSION}} or better of [docker-machine executable](https://github.com/docker/machine/releases), follow install instructions for the docker-machine binary.
2. Download the file for your OS and architecture.
2. Move the binary to your PATH.

e.g., for Mac OSX:

```console
$ curl -L https://github.com/Sheetal-R/docker-machine-oneview/releases/download/{{VERSION}}/docker-machine-driver-oneview_darwin-amd64 >/usr/local/bin/docker-machine-driver-oneview && \
  chmod +x /usr/local/bin/docker-machine-driver-oneview
```

Linux:

```console
$ curl -L https://github.com/Sheetal-R/docker-machine-oneview/releases/download/{{VERSION}}/docker-machine-driver-oneview_linux-amd64 >/usr/local/bin/docker-machine-driver-oneview && \
  chmod +x /usr/local/bin/docker-machine-driver-oneview
```

Windows (using [git bash](https://git-for-windows.github.io/)):

```console
$ if [[ ! -d "$HOME/bin" ]]; then mkdir -p "$HOME/bin"; fi && \
  curl -L https://github.com/HewlettPackard/docker-machine-driver-oneview/releases/download/{{VERSION}}/docker-machine-driver-oneview_windows-amd64.exe > "$HOME/bin/docker-machine-driver-oneview.exe" && \
  chmod +x "$HOME/bin/docker-machine-driver-oneview.exe"
```

## Changelog

*Edit the changelog below by hand*

{{CHANGELOG}}

## Thank You

Thank you very much to our active users and contributors. If you have filed detailed bug reports, THANK YOU!
Please continue to do so if you encounter any issues. It's your hard work that makes Docker Machine Oneview plugin better.

The following authors contributed changes to this release:

{{CONTRIBUTORS}}

Great thanks to all of the above! We appreciate it. Keep up the great work!

## Checksums

{{CHECKSUM}}
