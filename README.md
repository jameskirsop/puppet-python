# puppet-python [![Build Status](https://travis-ci.org/voxpupuli/puppet-python.svg?branch=master)](https://travis-ci.org/voxpupuli/puppet-python)

Puppet module for installing and managing python, pip, virtualenvs and Gunicorn virtual hosts.

**Please note:** The module [stankevich/python](https://forge.puppet.com/stankevich/python) has been deprecated and is now available under Vox Pupuli: [puppet/python](https://forge.puppet.com/puppet/python).

## Compatibility #

See `.travis.yml` for compatibility matrix.

* Puppet v4
* Puppet v5

### OS Distributions ##

This module has been tested to work on the following systems.

* Debian 8
* Debian 9
* EL 6
* EL 7
* CentOS 7
* Gentoo (and Sabayon)
* Suse 11
* Ubuntu 14.04
* Ubuntu 16.04
* Ubuntu 18.04

## Installation

```shell
git submodule add https://github.com/stankevich/puppet-python.git /path/to/python
```
OR

``` shell
puppet module install puppet-python
```

## Usage
For class usage refer to the [Reference]("https://github.com/voxpupuli/puppet-python/blob/master/REFERENCE.md). If contributing, this is updated with
```shell
bundle exec rake strings:generate\[',,,,false,true']
```

### hiera configuration

This module supports configuration through hiera. The following example
creates two python3 virtualenvs. The configuration also pip installs a
package into each environment.

```yaml
python::python_pyvenvs:
  "/opt/env1":
    version: "system"
  "/opt/env2":
    version: "system"
python::python_pips:
  "nose":
    virtualenv: "/opt/env1"
  "coverage":
    virtualenv: "/opt/env2"
python::python_dotfiles:
  "/var/lib/jenkins/.pip/pip.conf":
    config:
      global:
        index-url: "https://mypypi.acme.com/simple/"
        extra-index-url: "https://pypi.risedev.at/simple/"
```

### Using SCL packages from RedHat or CentOS

To use this module with Linux distributions in the Red Hat family and python distributions
from softwarecollections.org, set python::provider to 'rhscl' and python::version to the name
of the collection you want to use (e.g., 'python27', 'python33', or 'rh-python34').

## Release Notes

See [Changelog](https://github.com/voxpupuli/puppet-python/blob/master/CHANGELOG.md)

## Contributors

Check out [Github contributors](https://github.com/voxpupuli/puppet-python/graphs/contributors).
