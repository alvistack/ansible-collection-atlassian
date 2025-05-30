# Ansible Collection for Atlassian

<a href="https://alvistack.com" title="AlviStack" target="_blank"><img src="/alvistack.svg" height="75" alt="AlviStack"></a>

[![Gitlab pipeline status](https://img.shields.io/gitlab/pipeline/alvistack/ansible-collection-atlassian/master)](https://gitlab.com/alvistack/ansible-collection-atlassian/-/pipelines)
[![GitHub tag](https://img.shields.io/github/tag/alvistack/ansible-collection-atlassian.svg)](https://github.com/alvistack/ansible-collection-atlassian/tags)
[![GitHub license](https://img.shields.io/github/license/alvistack/ansible-collection-atlassian.svg)](https://github.com/alvistack/ansible-collection-atlassian/blob/master/LICENSE)
[![Ansible Collection](https://img.shields.io/badge/galaxy-alvistack.atlassian-blue.svg)](https://galaxy.ansible.com/alvistack/atlassian)

Ansible collection for deploying Atlassian.

This Ansible collection provides Ansible playbooks and roles for the
deployment and configuration of an [Atlassian](https://www.atlassian.com/)
environment.

## Requirements

This collection require Ansible community package 4.10 or higher.

This collection was designed for:

- Ubuntu 20.04, 22.04, 24.04, 24.10, 25.04
- AlmaLinux 8, 9
- openSUSE Leap 15.6, Tumbleweed
- Debian 12, Testing
- Fedora 40, 41, 42, Rawhide
- CentOS 7, 8 Stream, 9 Stream
- RHEL 7, 8, 9

## Quick Start

### Bootstrap Ansible and Roles

Start by cloning the repository, checkout the corresponding branch, and
init with `git submodule`, then install Ansible (see
<https://software.opensuse.org/download/package?package=ansible&project=home%3Aalvistack>):

    # GIT checkout development branch
    mkdir -p /opt/ansible-collection-atlassian
    cd /opt/ansible-collection-atlassian
    git init
    git remote add upstream https://github.com/alvistack/ansible-collection-atlassian.git
    git fetch --all --prune
    git checkout upstream/develop -- .
    git submodule sync --recursive
    git submodule update --init --recursive

    # Bootstrap Ansible
    printf "Components:\nEnabled: yes\nX-Repolib-Name: alvistack\nSigned-By: /etc/apt/keyrings/home-alvistack.asc\nSuites: /\nTypes: deb\nURIs: http://downloadcontent.opensuse.org/repositories/home:/alvistack/xUbuntu_24.04\n" | tee /etc/apt/sources.list.d/home-alvistack.sources > /dev/null
    curl -fsSL https://downloadcontent.opensuse.org/repositories/home:alvistack/xUbuntu_24.04/Release.key | tee /etc/apt/keyrings/home-alvistack.asc > /dev/null
    apt update
    apt install ansible

    # Confirm the version of Ansible
    ansible --version

### AIO

All-in-one (AIO) build is a great way to perform an Atlassian build for:

- A development environment
- An overview of how all the Atlassian services fit together
- A simple lab deployment

Simply execule our default Molecule test case and it will deploy all
default components into your localhost:

    # Run Molecule test case
    molecule test -s default

### Molecule

You could also run our
[Molecule](https://molecule.readthedocs.io/en/stable/) test cases if you
have [Vagrant](https://www.vagrantup.com/) and
[Libvirt](https://libvirt.org/) installed, e.g.

    # Run Molecule on Ubuntu 24.04
    molecule converge -s ubuntu-24.04

Please refer to [.gitlab-ci.yml](.gitlab-ci.yml) for more information on
running Molecule.

## Versioning

### `YYYYMMDD.Y.Z`

Release tags could be find from [GitHub
Release](https://github.com/alvistack/ansible-collection-atlassian/tags) of
this repository. Thus using these tags will ensure you are running the
most up to date stable version of this image.

### `YYYYMMDD.0.0`

Version tags ended with `.0.0` are rolling release rebuild by [GitLab
pipeline](https://gitlab.com/alvistack/ansible-collection-atlassian/-/pipelines)
in weekly basis. Thus using these tags will ensure you are running the
latest packages provided by the base image project.

## License

- Code released under [Apache License 2.0](LICENSE)
- Docs released under [CC BY
  4.0](http://creativecommons.org/licenses/by/4.0/)

## Author Information

- Wong Hoi Sing Edison
  - <https://twitter.com/hswong3i>
  - <https://github.com/hswong3i>
