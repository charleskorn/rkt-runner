rkt-runner
=========

An Ansible role for creating a systemd service unit that runs an ACI using rkt.

Requirements
------------

Assumes that [rkt](https://github.com/coreos/rkt) is already installed on the target system and is available at `/usr/bin/rkt`.

Requires [systemd](http://freedesktop.org/wiki/Software/systemd/). [The Wikipedia article for systemd](http://en.wikipedia.org/wiki/Systemd) lists the Linux distributions and corresponding versions that come with systemd out of the box.

Role Variables
--------------

This role has one required variable:

* `image_path`: the path to the ACI (eg. `/images/cool-thing.aci` or `http://www.example.com/cool-thing.aci` or `example.com/cool-thing:v1.2.3`)

There is also two optional variables:

* `rkt_opts`: rkt options (eg. https://coreos.com/rkt/docs/latest/subcommands/run.html)
* `extra_args`: arguments to pass through to the container's executable
  (eg. setting `extra_args` to `--do-stuff` will result in the `rkt run` command being `/usr/bin/rkt run /path/to/image.aci -- --do-stuff`)

Dependencies
------------

This role does not have any dependencies.

Example in host_vars or group_vars
-------

        rkt_services:
          cool-thing:
            image_path: example.com/cool-thing:v1.2.3
            rkt_opts: --insecure-options=image,http
          other-thing:
            image_path: example.com/other-thing:latest
            rkt_opts: --net=host

License
-------

MIT

Author Information
------------------

Created by Charles Korn ([me@charleskorn.com](me@charleskorn.com)).


Contributing
------------

Submit issues and pull requests on GitHub at [https://github.com/charleskorn/rkt-runner](https://github.com/charleskorn/rkt-runner).
