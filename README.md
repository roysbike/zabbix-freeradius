# zabbix-freeradius


Zabbix template for Freeradius 2.x statistics 



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

#####1.Enable status server in Freeradius

The configuration for the status server is automatically created in the sites-available directory. By default, this server is enabled and can be queried from every client. This behavior is controlled in the security section of the main config file.

If you want to disable the default status server functionality you need to set the following in radiusd.conf:

<code>
status_server = no
</code>

FreeRADIUS will only respond to status-server messages, if the status-server virtual server has been enabled. To do this, create a link from the sites-enabled directory to the status file in the sites-available directory:

<code>
cd sites-enabled
ln -s ../sites-available/status status
</code>

and restart/reload your RADIUS server. You will notice that a new server listens on port 18121/udp of localhost. If you want other clients than localhost to query this server, change the listen section of the new server. You should also change the default password in the client section of the server. Add more clients as needed.

