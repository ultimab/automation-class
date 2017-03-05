Ansers/documentation for solutions to week 2 "Easy Wins"

Note that there is only 1 vSRX in the lab setup, while
that is not ideal, I was unable to add a second (or third)
to the lab without creating a switching loop.
Adding a virual arista device was also unsucessful.

So rather than spending more time attempting to create
a more robust lab I am focusing on learning Ansible
and creating working playbooks.


- junos-gather-facts.yml
playbook using junos_facts module to get basic facts about
device and output these facts to the screen

- junos-inventory-report.yml
playbook uses junos_facts module to father facts about junos
devices and write basic inventory info (SN, software version..)
to a file

- show-arp-simple-show.yml
playbook uses raw module to get arp table from junos device
and write the output to a file

There are also exmaple output files from playbook execution
