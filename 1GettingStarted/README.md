Ansers/documentation for solutions to week 1 "Getting Started"

- hosts - hosts file for ansible
- topology.txt - lab topology description

Here is an example ansible raw module usage:

ansible all -m raw -i hosts -a "show version"
srx1.lab.local | SUCCESS | rc=0 >>
Hostname: srx
Model: firefly-perimeter
JUNOS Software Release [12.1X47-D20.7]
Shared connection to srx1.lab.local closed.

