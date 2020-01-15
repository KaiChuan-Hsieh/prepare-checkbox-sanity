# prepare-checkbox-sanity
prepare-checkbox-sanity
This package is a wrapper to help people prepare the environment for PC sanity with checkbox.
All operations are followed [checkbox document](checkbox.readthedocs.io/en/latest/).

## install

### by basher
This is for develeper install it from github quickly.
The target machine is assumed installed [basher](https://github.com/basherpm/basher/blob/master/README.md)
~~~ sh
$ basher install alex-tu-cc/prepare-checkbox-sanity
$ basher prepare-checkbox-sanity --init
~~~

Then you can just run any plan under com.canonical.certification:: category, e.g.
~~~ sh
$ checkbox-run-plan sru -b
~~~

### by debian package
this package is hosted on [checkbox-dev](https://launchpad.net/~checkbox-dev/+archive/ubuntu/ppa)
~~~ sh
sudo add-apt-repository ppa:checkbox-dev/ppa
sudo apt-get update
sudo apt-get install prepare-checkbox-sanity
~~~

Then you can just run any plan under com.canonical.certification:: category, e.g.
~~~ sh
$ checkbox-run-plan sru -b
~~~

## usage
All usage can be refer to help.


~~~ sh
$ prepare-checkbox-sanity --help
usage: prepare-checkbox-sanity options

    -h|--help   print this message
    --init      If you installed this package by baser from git repository directly,
                Then you need to do this first to setup the environment.
                If you install it by debian package, then all things be done automatically.
    --dev       Get dev packages for plans under development from https://launchpad.net/~oem-solutions-group/+archive/ubuntu/pc-sanity-daily

$ prepare-checkbox-sanity --help
usage: ./checkbox-run-plan options plan

    options:
        -h|--help           print this message
        -e|--exclude-unites exclude unites
                            e.g. -e ".*audio/alsa_record_playback_automated .*suspend/record_playback_after_suspend_auto"
        --checkbox-conf     The path of checkbox.conf, refer to https://checkbox.readthedocs.io/en/latest/launcher-tutorial.html
                            The default path will refer to CHECKBOX_CONF in /etc/default/prepare-checkbox-sanity.conf
                            See usage below for detail.
        -b                  batch mode, which will go all default way.

    plan:
        pc_sanity_before_suspend
            the plan in plainbox-provider-pc-sanity on ppa:oem-solutions-group/pc-sanity

        pc_sanity_after_suspend
            the plan in plainbox-provider-pc-sanity on ppa:oem-solutions-group/pc-sanity

        stress-suspend-30-cycles-with-reboots-automated
            the plan in plainbox-provider-checkbox

        sru
            the plan in plainbox-provider-sru

        Or any plan in /usr/share/plainbox-provider-*/units could be used here as well.

    usage:
        run sru plan, and use the checkbox.conf from current folder
        ./checkbox-run-plan sru --checkbox-conf `pwd`/checkbox.conf -b

        run sru plan, and get the checkbox.conf from http://192.168.0.40/checkbox.conf
        ./checkbox-run-plan sru --checkbox-conf http://192.168.0.40/checkbox.conf -b

~~~
