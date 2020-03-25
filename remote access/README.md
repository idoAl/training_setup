# VM remote access

Now we're going to do the cool things.

We are going to set up a remote connection between the host and the VM.
When we finish, we will be able to access a remote interpreter on PyCharm.
That means that we could edit our code from the host but run it on the VM.


## Set up NAT on the VM
Wait, what does that mean?
### what is NAT?

watch this video: https://www.youtube.com/watch?v=QBqPzHEDzvo

We want our VM to be able to access the host, and the "outside network" - aka the internet...

When using NAT configuration, your host (windows PC...)
will route network from the VM outside like your home router does. 
   
 Find out more here: https://pubs.vmware.com/workstation-9/index.jsp?topic=%2Fcom.vmware.ws.using.doc%2FGUID-D9B0A52D-38A2-45D7-A9EB-987ACE77F93C.html
 
 ### setting it up
 
 * click "Player" at the top left corner
 * choose manage -> virtual machine settings
 * Then look for the "Network Adapter" under "Device", and click it.
 * Make sure "NAT" option is marked on the right.
 
 ### make sure it works
 * check your host ip address using ipconfig on cmd
   * look for IPv4 Address
 * enter the terminal in your ubuntu VM (alt + t)
 * ping the host ip address (ping \*.\*.\*.\*)
 * make sure you get a response.
 
 
 ## Set up SSH in ubuntu
 Now we are going to set up an ssh server in our VM.

### what's SSH?
SSH is a protocol which let's us have secured services over unsecured networks.
It is typically used in order to have a secured remote shell, which is what we're going to do.

ssh will let us have a terminal from which we can execute commands on our VM.

Read more about ssh here: https://en.wikipedia.org/wiki/Secure_Shell

### How to set it up?
First we'll need to set up an ssh server on the VM.
We are going to use OpenSSH which is an open source ssh server.

* Run sudo apt install openssh-server
* When it's finished, an ssh server daemon (https://en.wikipedia.org/wiki/Daemon_(computing)) should be running. 
Make sure by running "ps -e | grep ssh" and look for sshd (d stands for daemon)

Check out more at: https://help.ubuntu.com/lts/serverguide/openssh-server.html

### Set up an ssh client

MobaXterm has a good ssh client.
You can download the home edition at: https://mobaxterm.mobatek.net/download-home-edition.html

In order to start an SSH session, click "Start local terminal".
* figure out the ip address of you vm. This can be done using "ifconfig"
 (look online for help if you have any problems.)
 * now type in "ssh [username]@[ip-address]" where username is your ubuntu username and ip-address is
 your vm's ip address you found before.
 * enter your password - and here we go. Now you have a remote terminal from your host.
### Optional - X11

Using MobaXterm's ssh X11 you can forward the VM's display to your host.

Read more at: https://itekblog.com/ssh-x11-forwarding-display-using-mobaxterm/

## Setting up remote PyCharm

Now that you have an SSH server in  your VM, you can use PyCharm remotely.
That means that you can edit your code on the host, and run it on the VM!

Notice that this option is not available in the community edition (which you can get for free). 

For help,
check out this tutorial: https://www.jetbrains.com/help/pycharm/configuring-remote-interpreters-via-ssh.html

and this video: https://www.youtube.com/watch?v=kuowBMqM1Ow