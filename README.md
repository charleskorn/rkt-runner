rkt-runner
=========

An Ansible role for creating a systemd service unit that runs an ACI using rkt.

Requirements
------------

Assumes that [rkt](https://github.com/coreos/rkt) is already installed on the target system and is available at `/usr/bin/rkt`. 

Requires [systemd](http://freedesktop.org/wiki/Software/systemd/). [The Wikipedia article for systemd](http://en.wikipedia.org/wiki/Systemd) lists the Linux distributions and corresponding versions that come with systemd out of the box.

Role Variables
--------------

This role has two required variables:

* `image_path`: the path to the ACI in the filesystem (eg. `/images/cool-thing.aci`)
* `service_name`: the name of the service (eg. `cool-thing`)

There is also one optional variable:

* `extra_args`: arguments to pass through to the container's executable 
  (eg. setting `extra_args` to `--do-stuff` will result in the `rkt run` command being `/usr/bin/rkt run /path/to/image.aci -- --do-stuff`)

Dependencies
------------

This role does not have any dependencies.

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: rkt-runner, image_path: "/images/cool-thing.aci", service_name: "cool-thing" }

License
-------

MIT

Author Information
------------------

Created by Charles Korn ([me@charleskorn.com](me@charleskorn.com)).


Contributing
------------

Submit issues and pull requests on GitHub at [https://github.com/charleskorn/rkt-runner](https://github.com/charleskorn/rkt-runner).
