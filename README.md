Name
~~~~~~~~~~~~~
Logcheck — program to scan system logs for interesting lines

Description
~~~~~~~~~~~~~
The logcheck program helps spot problems and security violations in your logfiles automatically and will send the results to you periodically in an e-mail. 
By default logcheck runs as an hourly cronjob just off the hour and after every reboot.

logcheck supports three level of filtering:  "paranoid"  is  for  high-
security  machines running as few services as possible.
"server"  is  the  default  and contains  rules  for  many  different  daemons.   
"workstation" is for sheltered machines and filters most of the messages.
The ignore  rules work  in  additive  manner. "paranoid" rules are also included at level
"server". "workstation" level includes  both  "paranoid"  and  "server" rules.

The messages reported are sorted into three layers, system events,
security events and attack alerts. The verbosity of system events is
controlled by which level you choose, paranoid, server or workstation.
However, security events and attack alerts are not affected by this.

Reproduced
~~~~~~~~~~~~~
It's compatible with Debian 8 - Jessie, and Ubuntu 12.04, 14.04, 15.10, 16.04, 16.10, 17.04.

This commands downloads and installs Logcheck.
apt-get install logcheck

To fetch the configuration file, use the command below.
git pull https://myusername@github.com/projectfolder/projectname.git master

Configuration
~~~~~~~~~~~~~
Logcheck configuration is done in the file /etc/logcheck/logcheck.conf.
To change the email address to which reports are sent - mail is sent and received directly using SMTP, change the line:
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
