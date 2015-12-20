# zabbix-freeradius


Zabbix template for Freeradius 2.x 


##Items

Authentication coutners per 1 sec 

* FreeRADIUS-Total-Access-Accepts
* FreeRADIUS-Total-Access-Rejects
* FreeRADIUS-Total-Access-Requests
* FreeRADIUS-Total-Auth-Dropped-Requests
* FreeRADIUS-Total-Auth-Duplicate-Requests
* FreeRADIUS-Total-Auth-Responses

Accounting coutners per 1 sec 

* FreeRADIUS-Total-Accounting-Requests 
* FreeRADIUS-Total-Accounting-Responses 
*	FreeRADIUS-Total-Acct-Duplicate-Requests 
*	FreeRADIUS-Total-Acct-Malformed-Requests 
*	FreeRADIUS-Total-Acct-Invalid-Requests
*	FreeRADIUS-Total-Acct-Dropped-Requests
*	FreeRADIUS-Total-Acct-Unknown-Types
	

##Install

#####1. Enable status server in Freeradius

Enable status server functionality you need to set the following in radiusd.conf:

<code>
status_server = yes
</code>

FreeRADIUS will only respond to status-server messages, if the status-server virtual server has been enabled. To do this, create a link from the sites-enabled directory to the status file in the sites-available directory:

<code>
cd sites-enabled
ln -s ../sites-available/status status

Restart Freeradius

</code>

and restart/reload your RADIUS server. You will notice that a new server listens on port 18121/udp of localhost. If you want other clients than localhost to query this server, change the listen section of the new server. You should also change the default password in the client section of the server. Add more clients as needed.

#####2. Add configuration userparameter_radius.conf in zabbix-agent

#####3. Import zabbix-freeradius-template
Change macros {$RADIUS_SECRET} for password . (default adminsecret)
