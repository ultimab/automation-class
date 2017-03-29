Ansers/documentation for solutions to week 3 "Data Models"

As currenty one device makes up the network, there was no need
for a fabric.yml file to define the infrastructure, nor any 
translation from a service data model to a node data model.

The service being descrbed is a managed IPsec VPN service:

services.yml - describes VPN services

The variables that describe a service (at the highest level it is a
dictionary indexed by the 'name' of the particular service/customer)

id - unique identifyer for the specific VPN service
node - node that the VPN will be configured on
remote_nets - list of remote networks VPN provides access to
local_net - 'local' network to be hosted off of the SRX
ike_settings - IPSec phase 1 settings to be used
ipsec_settings - IPSec phase 2 settings to be used
psk - Preshared key for phase 1 (not very secure storage)

business logic is used to configure many of the elemnts, such as
the 'sp' subinterface used for the VPN service is derived from the 'id'
of the service, as well as the VLAN for the subint that will serve as
the 'local' network.  A routing instance is used to prevent IP overlap
from multiple VPN services.
At this point with one SRX in the node variable is not needed,
but is present to account for possible future network growth.

group_vars/all.yml

This file holds common network parameters, such as syslog host,
not particularly important in this one node network, but helpful
for future growth.  

host_vars/

Holds node specific data, only one file currently, and the only data is
the 'id' given to a node, which using business logic will help generate
the loopback IP of the node and is used by the 'services.yml' to
note which node the VPN service is terminated on.

gen_config.yml

Tests the template and services file to genereate config for all
services that are described.

config.txt

Example output of gen_config.yml
