# Installation

## Overview

This document describes prerequisites, installation and post-install sanity
checking for Zonemaster::CLI. The final section wraps up with a few pointer to
other interfaces to Zonemaster. For an overview of the Zonemaster product,
please see the [main Zonemaster Repository].


## Prerequisites

Before installing Zonemaster::CLI, you should [install Zonemaster::Engine][
Zonemaster::Engine installation].

> **Note:** [Zonemaster::Engine] and [Zonemaster::LDNS] are dependencies of
> Zonemaster::CLI. Zonemaster::LDNS has a special installation requirement,
> and Zonemaster::Engine has a list of dependencies that you may prefer to
> install from your operating system distribution (rather than CPAN).
> We recommend following the Zonemaster::Engine installation instruction.

Prerequisite for FreeBSD is that the package system is updated and activated
(see the FreeBSD section of [Zonemaster::Engine installation]).

For details on supported versions of Perl and operating system for
Zonemaster::CLI, see the [declaration of prerequisites].


## Installation

This instruction covers the following operating systems:

 * [Installation on CentOS]
 * [Installation on Debian]
 * [Installation on FreeBSD]
 * [Installation on Ubuntu]

### Installation on CentOS

1) Install binary dependencies:

   ```sh
   sudo yum install perl-JSON-XS perl-MooseX-Getopt
   ```

2) Install dependencies from CPAN:

   * CentOS 7:

     ```sh
     sudo cpanm Net::Interface Text::Reflow
     ```

   * CentOS 8:

     ```sh
     sudo cpanm Text::Reflow
     curl -O https://cpan.metacpan.org/authors/id/M/MI/MIKER/Net-Interface-1.016.tar.gz
     tar xf Net-Interface-1.016.tar.gz
     cd Net-Interface-1.016
     ./configure
     perl -I. Makefile.PL
     make
     sudo make install
     ```

3) Install Zonemaster::CLI 

   ```sh
   sudo cpanm Zonemaster::CLI
   ```


### Installation on Debian

1) Update configuration of "locale"

   ```sh
   sudo perl -pi -e 's/^# (da_DK\.UTF-8.*|en_US\.UTF-8.*|fi_FI\.UTF-8.*|fr_FR\.UTF-8.*|nb_NO\.UTF-8.*|sv_SE\.UTF-8.*)/$1/' /etc/locale.gen
   sudo locale-gen
   ```

   After the update, `locale -a` should at least list the following locales:
   ```
   da_DK.utf8
   en_US.utf8
   fi_FI.utf8
   fr_FR.utf8
   nb_NO.utf8
   sv_SE.utf8
   ```

2) Install dependencies:

   ```sh
   sudo apt-get install libmoosex-getopt-perl libtext-reflow-perl libmodule-install-perl libnet-interface-perl
   ```

3) Install Zonemaster::CLI:

   ```sh
   sudo cpanm Zonemaster::CLI
   ```

### Installation on FreeBSD

1) Become root:

   ```sh
   su -l
   ```

2) Install dependencies available from binary packages:

   ```sh
   pkg install devel/gmake p5-JSON-XS p5-Locale-libintl p5-MooseX-Getopt p5-Text-Reflow p5-Net-Interface
   ```

3) Install Zonemaster::CLI:

   ```sh
   cpanm Zonemaster::CLI
   ```


### Installation on Ubuntu

Use the procedure for installation on [Debian][Installation on Debian].


## Post-installation sanity check

Run the zonemaster-cli command:

```sh
zonemaster-cli --test basic zonemaster.net
```

The command is expected to take a few seconds and print some results about the delegation of zonemaster.net.


## What to do next?

 * For a web GUI, follow the [Zonemaster::Backend][Zonemaster::Backend
   installation] and [Zonemaster::GUI installation] instructions.
 * For a [JSON-RPC][JSON-RPC API] frontend, follow the [Zonemaster::Backend
   installation] instruction.

[Installation on CentOS]: #installation-on-centos
[Installation on Debian]: #installation-on-debian
[Installation on FreeBSD]: #installation-on-freebsd
[Installation on Ubuntu]: #installation-on-ubuntu

[Declaration of prerequisites]: https://github.com/zonemaster/zonemaster/blob/master/README.md#prerequisites
[JSON-RPC API]: https://github.com/zonemaster/zonemaster-backend/blob/master/docs/API.md
[Main Zonemaster repository]: https://github.com/zonemaster/zonemaster/blob/master/README.md
[Zonemaster::Backend installation]: https://github.com/zonemaster/zonemaster-backend/blob/master/docs/Installation.md
[Zonemaster::Engine installation]: https://github.com/zonemaster/zonemaster-engine/blob/master/docs/Installation.md
[Zonemaster::Engine]: https://github.com/zonemaster/zonemaster-engine/blob/master/README.md
[Zonemaster::GUI installation]: https://github.com/zonemaster/zonemaster-gui/blob/master/docs/Installation.md
[Zonemaster::LDNS]: https://github.com/zonemaster/zonemaster-ldns/blob/master/README.md

