Reproduced
~~~~~~~~~~~~~
In this "Readme" file, we'll only be using Debian 8 - Jessie.

This commands downloads and installs Logcheck.
apt-get install logcheck

Configuration
~~~~~~~~~~~~~
Logcheck configuration is done in the file /etc/logcheck/logcheck.conf.
To change the email address to which reports are sent, change the line:
	SENDMAILTO="root"
to:
	SENDMAILTO="emailaddress@some.domain.tld"

The reportlevel (that is, the degree of filtering applied to "routine" system
events) can be reduced from the default by changing the line:
	REPORTLEVEL="server"
to:
	REPORTLEVEL="workstation"
or increased:
	REPORTLEVEL="paranoid"

Note that "server" includes "paranoid" and "workstation" includes "server"
(which includes "paranoid").

There are a number of other options which are documented in
/etc/logcheck/logcheck.conf itself.

By default logcheck is set to run once an hour. This can be changed by editing
/etc/cron.d/logcheck.

Please note that the permissions of rulefiles installed with
dh_installlogcheck after installing logcheck will differ from those included
in logcheck-database. This is because dh_installlogcheck cannot yet assume
that the logcheck user exists.  This may be changed in a future version of
Debian.
