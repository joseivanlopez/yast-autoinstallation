YaST - The AutoYaST Framework
=============================

[![Travis Build](https://travis-ci.org/yast/yast-autoinstallation.svg?branch=master)](https://travis-ci.org/yast/yast-autoinstallation)
[![Jenkins Build](http://img.shields.io/jenkins/s/https/ci.opensuse.org/yast-autoinstallation-master.svg)](https://ci.opensuse.org/view/Yast/job/yast-autoinstallation-master/)


Development
===========

This module is developed as part of YaST. See the
[development documentation](http://yastgithubio.readthedocs.org/en/latest/development/).

Have a look to the [AutoYaST Development Documentation](http://yastgithubio.readthedocs.io/en/latest/autoyast-development/) if you would like to implement AutoYaST support for your YaST module.


Getting the Sources
===================

To get the source code, clone the GitHub repository:

    $ git clone https://github.com/yast/yast-autoinstallation.git

If you want to contribute into the project you can
[fork](https://help.github.com/articles/fork-a-repo/) the repository and clone your fork.


Testing Environment
===================

There are several possibilities how test an updated code. It also depends on
the fact in which stage of installation it comes into effect. First stage runs
between the start from installation media to reboot (or kexec), then continues
second stage.

### First Stage ###

Either use *StartShell=1* option in [Linuxrc](https://en.opensuse.org/SDB:Linuxrc),
edit the installation system and run *yast* manually or use
a [DriverUpdate](https://en.opensuse.org/SDB:Linuxrc#p_dud) via Linuxrc.

### Second Stage ###

There are two possible ways how to rerun this stage, just keep in mind that
the system might be already configured and thus it might behave
a bit differently:

  ```
  cp /var/lib/YaST2/install.inf /etc/
  touch /var/lib/YaST2/runme_at_boot
  cp /var/adm/autoinstall/cache/installedSystem.xml \
    /var/lib/autoinstall/autoconf/autoconf.xml
  reboot
  ```

or faster without rebooting but with possible side-effects:

  ```
  yast ayast_setup setup filename=/var/adm/autoinstall/cache/installedSystem.xml
  ```


Contact
=======

If you have any question, feel free to ask at the [development mailing
list](http://lists.opensuse.org/yast-devel/) or at the
[#yast](https://webchat.freenode.net/?channels=%23yast) IRC channel on freenode.
