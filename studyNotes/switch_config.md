Configuring network switch
========================
note : this is initial setup of switch

### Naming the switch
[1] connect to switch using Putty or other program

[2] wait until the terminal shows :
```
switch>
```
switch is the default name of the switch (default name may differ), to start the configuration
use "enable" command
```
switch>enable
switch#
```
[3] enter configuration mode with command "configure terminal"
```
switch# configure terminal
switch(config)#
```
[4] enter the command "hostname" to change the host name followed by the new name
```
switch(config)# hostname test
test(config)#
```
### Setting up password for the switch
[1] go to config mode and type "enable password" followed by the password
```
test(config)# enable password test
```
[2] log out and try to enter via enable command (it should request a password now)

### VLAN Configuration
[1] list all available vlan with the command "show vlan"
```
test# show vlan
```
note : default is VLAN 1


the terminal should list all of port with assigned vlan

[2] to add vlan, enter configuration mode and type vlan followed by the number
```
test# configure terminal
test(config)# vlan 10
test(config-vlan)#
```
after inputing the vlan number, the terminal should enter configuration mode for the vlan

[3] to name the VLAN simply use "name" command followed by the name
```
test(config-vlan)#name sales
```
[4] go to step 1 to check whether the VLAN is registered into the VLAN list


[5] previous VLAN setup only register the VLAN name without assigning it to the switch port, to assign it :
```
test(config)#interface fastEthernet 0/1
test(config-if)#switchport mode access
test(config-if)#switchport access vlan 10
test(config-if)#exit
test(config)#do show vlan
```
the example above will assign vlan 10 to fastEthernet 0/1 as access port

[6] to setup multiple access ports, we can use "range" command such as
```
test(config)#interface range fastEthernet 0/1-10
```
to set the range : 0/start-stop 


the example above will set fa 0/1 until fa 0/10 as VLAN 10 port


### Assigning IP address to VLAN
