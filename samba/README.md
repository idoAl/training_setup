# Setting up a shared SMB directory

If you are reading this, you probably have PyCharm community.
Unfortunately, this version of PyCharm does not support remote projects, so we have to use a workaround.

Our workaround would be to mount a shared directory from the VM and open it with PyCharm.
We still won't have remote debugging in PyCharm, so we'll use pdb through SSH (:mask:).

## What's SMB?
A protocol used for shared access to resources (like files...), mostly used in Windows. 
Read more here: https://en.wikipedia.org/wiki/Server_Message_Block

We want to mount a directory on the VM shared via SMB, so we'll have to use some sort of software
that can implement the sharing of a directory using SMB protocol with Windows SMB client.
We will use Samba, which is an open source.

## Installing Samba on our Ubuntu machine

Follow this guide:
https://ubuntu.com/tutorials/install-and-configure-samba#1-overview

Make sure that you the right path of the shared directory in the ```/etc/samba/smb.conf``` file:
```
[sambashare]
    comment = Samba on Ubuntu
    path = /home/{ your Ubuntu username here }/sambashare
    read only = no
    browsable = yes
```

And make sure that you add your username and password:
```
sudo smbpasswd -a { your Ubuntu username here }
```

Now let's make sure that everything works. 
Check your Ubuntu machine's ip address, and then open file explorer on your host (winkey + e).
Enter \\\\*.\*.\*.\* in the address bar (the \\\\ prefix indicates that you are trying to access
a directory shared through SMB).
If you find your shared directory and you can access it, everything is good. Otherwise, 
validate that you have done everything correctly and look online for help.



## Adding a network location for the shared directory 
Follow the steps here:
https://www.techrepublic.com/article/how-to-connect-to-linux-samba-shares-from-windows-10/

Now you have a network location that points to your mount, and PyCharm can use a project directory in it.

## Using python and pdb through SSH
You will learn about pdb in the Python guide.
Now I'll just show you how to run and debug python programs through SSH in this setup.

#### Install an ssh client
In order to use SSH from the PyCharm terminal, you first have to install an SSH client on your host.
We'll use the OpenSSH client. You can find it here: 
https://www.mls-software.com/opensshd.html

Make sure it is in your PATH.

#### PyCharm remote interpreter for the poor
Since we love our PyCharm free, we don't have a remote python interpreter.
I also didn't find any free plugin that can provide this feature...

So to have some sort of a remote interpreter, open up your PyCharm terminal (alt + F12) and use SSH:
Type in: ```ssh username@ip-address```. Now you have a terminal in PyCharm, and you can use the 
python interpreter and debug using pdb.