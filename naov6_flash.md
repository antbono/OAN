# Flash Ubuntu on NAO v6

Instructions to install the [ubuntu based operating system](https://github.com/NaoDevils/NaoImage) created by the NaoDevils team on a Nao V6.

## Prerequisites

Download the Softbank official firmware, in particular **version 2.8.5.10 is required**.
The file should be something like nao-2.8.5.10.opn

You need two usb drives with a capacity of 4GB and 8 GB at least.

The follwing instructions are based on an ubuntu system.

## Flashing instructions

- Inside the flasher-2.1.0.19-linux64 folder launch a terminal and run
-     sudo ./flasher
- Using the gui, flash the nao-2.8.5.10.opn file on your usb drive with at least 4GB.
- Using the official firmware, follow the instruction reported on the [Nao Devils NaoImage github page](https://github.com/NaoDevils/NaoImage) to make a bootable usb with the ubuntu image.  
- Switch off nao and insert the first usb you created with the official firmware with root.
- Switch on nao pressing the button until it flashes blue very rapidly. Wait some minutes until it stands up and move.
- Switch off nao and insert the second usb with the ubuntu image. Repeat the flashing procedures.
- If everything is fine nao is not moving and lights are on.

## First connection

To connect to nao you need to connect it via ethernet to a router. 

- Access the router admin page and discover the nao assigned ip address.
- Connect to it via ssh, the username and password are ''nao''
- To modify the nao network settings, edit the file /etc/netplan/default.yaml
-     sudo nano /etc/netplan/default.yaml
- A sketch of a setting enabling a wifi connection is available in ![nao_network.yaml](nao_network.yaml)
- Apply the changes
-     sudo netplan apply
- If everything is fine you can now connect to nao via wifi using the choosen static ip address.
- Check internet connection
-     ping 8.8.8.8
 
  
    
