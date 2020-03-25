# Installing VMware workstation player

## What is a VM?
check this out: https://www.redhat.com/en/topics/virtualization/what-is-a-virtual-machine 

You can also watch some youtube videos...

## What is VMware workstation player?
A host for VM's which can be used free for non-commercial usages... 
free is good...
* You can also get the VMware workstation Pro which is better, but it only has a 30 day tryout period...  

## Where can we download it?
Here:
https://www.vmware.com/il/products/workstation-player/workstation-player-evaluation.html

After you download it just install. If you have any problem, google is your friend (There are tons of info online about VMware products)

## Optional - Clone a VM
You may face some trouble setting up everything.
It's ok, since messing with all this IT things sucks and isn't a part of your training.

Therefore, I created a "clone" of an Ubuntu machine **which I fully configured for you.**
 You can just plug-and-play it.
 Why I used quotes on "clone"? because the free (we love free..) version
 of the VMware workstation we use does not support real clones/templates,
 so there is a workaround.
 
 You can find the "clone" under the sub-directory "Ubuntu Clone"
 and follow the instructions here in order to load it up:
 https://www.htpcguides.com/workaround-to-clone-vmplayer-virtual-machines/
  
 Note that you have to extract it...

If you want to set up everything by yourself, which is the preferred method, follow the next section.

## Create an ubuntu virtual machine
Launch the VMware workstation player. 

* First click on "Create a New Virtual"
* Choose "installer disc image file (iso)" and browse for the Ubuntu iso you downloaded.
* Now, if Ubuntu is detected, you will have to enter your username and password for ubuntu. Remember them!
* Choose the location of your virtual machine.
* Then, use the recommended 20GB max disk size, and mark "Split virtual disk into multiple files"
* Before you are done, make sure that the Network Adapter (listed in the hardware settings) is "NAT".
We'll get to this later...
* Finish! it takes some time so be patient.
