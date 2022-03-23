# apt-deepclean

## Description
apt-deepclean goes beyond apt clean and apt autoclean to remove all the
files from the apt archive that you'll probably never need.

By default it leaves files that are newer than the installed package.

apt autoclean does not remove files that are available in the mirror. So
if your mirror has dozens of versions of a package available, your local
archive will too. For some packages that run in to the hundreds of
megabytes, on repos that leave many versions available for customers,
this can turn into a real problem.

apt-deepclean solves this. You might want to run it from cron or your
devops environment on occasion to keep your disk usage under control.

If you frequently downgrade packages you won't want to use this. If you
want to be able to reinstall the currently installed package, make sure
you use the --keep-installed flag. If you really want to delete all the
archives you can use --no-keep-updates but then maybe you would just
want to use apt clean instead?

## Example
    # apt-deepclean --dry-run
    would delete /var/cache/apt/archives/arping_2.19-6_amd64.deb
    would delete /var/cache/apt/archives/gitlab-ce_14.6.0-ce.0_amd64.deb
    would delete /var/cache/apt/archives/gitlab-ce_14.6.1-ce.0_amd64.deb
    would delete /var/cache/apt/archives/gitlab-ce_14.6.2-ce.0_amd64.deb
    would delete /var/cache/apt/archives/gitlab-ce_14.6.3-ce.0_amd64.deb
    would delete /var/cache/apt/archives/gitlab-ce_14.7.0-ce.0_amd64.deb
    would delete /var/cache/apt/archives/gitlab-ce_14.7.1-ce.0_amd64.deb
    would delete /var/cache/apt/archives/gitlab-ce_14.7.2-ce.0_amd64.deb
    would delete /var/cache/apt/archives/gitlab-ce_14.7.3-ce.0_amd64.deb
    would delete /var/cache/apt/archives/gitlab-ce_14.8.0-ce.0_amd64.deb
    would delete /var/cache/apt/archives/gitlab-ce_14.8.1-ce.0_amd64.deb
    would delete /var/cache/apt/archives/gitlab-ce_14.8.2-ce.0_amd64.deb
    would delete /var/cache/apt/archives/jq_1.5+dfsg-2+b1_amd64.deb
    would delete /var/cache/apt/archives/libjq1_1.5+dfsg-2+b1_amd64.deb
    would delete /var/cache/apt/archives/libnet1_1.1.6+dfsg-3.1_amd64.deb
    would delete /var/cache/apt/archives/libonig5_6.9.1-1_amd64.deb
    would delete /var/cache/apt/archives/libudev1_247.3-6~bpo10+1_amd64.deb
    would delete /var/cache/apt/archives/lrzsz_0.12.21-10_amd64.deb
    would delete /var/cache/apt/archives/openssl_1.1.1d-0+deb10u8_amd64.deb
    would delete /var/cache/apt/archives/systemd-sysv_247.3-6~bpo10+1_amd64.deb
    would delete /var/cache/apt/archives/udev_247.3-6~bpo10+1_amd64.deb
    would delete /var/cache/apt/archives/zssh_1.5c.debian.1-7_amd64.deb
    #

## Installation
Copy it somewhere handy.  Maybe set up a cron job.  Here's a sample puppet cron entry:

      cron { 'apt_deepclean' :
        command     => '/usr/local/sbin/apt-deepclean',
        user        => 'root',
        hour        => '1',
        minute      => '10',
        environment => 'PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/local/sbin',
      }


## Usage
run:

    apt-deepclean --help 

for brief help, or 

    apt-deepclean --man

for the man page.

## Support
If you find problems, please file an issue here.

## Contributing
If you have an idea, please file an issue and optionally a pull request.

## Authors and acknowledgment
This uses the AptPkg perl package that is used for many Debian tools.

## License
This code is licensed under the WTFPL 2.0 license. Read about it here:
http://www.wtfpl.net/about/

BECAUSE THE PROGRAM IS LICENSED FREE OF CHARGE, THERE IS NO WARRANTY FOR
THE PROGRAM, TO THE EXTENT PERMITTED BY APPLICABLE LAW. EXCEPT WHEN
OTHERWISE STATED IN WRITING BY THE COPYRIGHT HOLDERS AND/OR OTHER
PARTIES. IN COUNTRIES WITH OBLIGATORY WARRANTY THE FULL EXTENT OF THE
WARRANTY SHALL BE THE REFUND OF THE FULL PURCHASE PRICE OF THE PROGRAM.

## Project status
We're running this in production and will make any updates we find necessary.  We'll also occasionally pay attention to this repo.
