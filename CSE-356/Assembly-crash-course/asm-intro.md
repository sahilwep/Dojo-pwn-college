# Introduction to assembly

## Basics of OS :

### Kernel : 

* Kernel is component of computer that makes everything run.
* It is lowest running software that is always running when computer is on.
* Kernel is responsible for access the computer resource, Resource management, Memory Allocation, Device management.
* We can say Kernel is responsible for the interaction b/w the hardware and user. 

###  Virtualization : 
* Virtualization is cornerstone of modern operating system.To virtualize something is to create a virtual  version of it doesn't require hardware stuff..
* Example we use the android on pc in virtual env..

#### Virtual Machine : 
* Virtual machine is a software which is used to achieve the virtualization.
* Suppose you use `Windows xyz` as your operating system, you want to use `ubuntu OS` In this case you can use any Virtualization software to install the `ubuntu ` on your base `windows` system, the VM-Software create a new space inside your pc where your `ubuntu` OS is installed and configured..
* Suppose if we are developing any particular malicious software, then we create a personal space where we experiment all those stuff, so if any wrong happen our base OS will remain safe.


#### VM-Setup :

* There are many of Software that provide virtualization eg. `Virtualbox`, `VM-Ware`, `QEMU` etc..

### Containers : 

* Containers are another level of virtualization that allows for isolated spaces in the kernel to be created and destroyed without affecting each other.

![Containers-vs-VM](https://ike.mahaloz.re/2_operating_systems/ms_container_v_vm.png)

* In simple Word, Containers are lite and VM's are heavy, because In VM we need to initialize entirely new kernel for each VM's we make, whereas in containers we share already existing kernel.

#### Why we use containers ?
* Container become very useful when we trying to run the application that have dependencies that we not access to our current version of the VM, for instance we want to run `ubuntu-18.9` application while in `ubuntu-20.0`, what if our system dependencies are not work for it, then in this case we create the container that create an environment to run `ubuntu-18.9`, the latter is easier mean container are persistent.mean when you are done running container everything you created inside is destroyed.

### Linux OS : 

#### The Terminal

* Terminal is a place where write the instruction in certain syntax to the computer to perform any task.

#### Permission
* In linux the permission is something that is major component of hacking.

```sh
$ ls -l /bin/bash
-rwxr-xr-x 1 root root 1113504 Jun  6  2019 /bin/bash
```
* Here we can see:
  * The file "/bin/bash" is owned by user "root"
  * The superuser has the right to read, write, and execute this file
  * The file is owned by the group "root"
  * Members of the group "root" can also read and execute this file
  * Everybody else can read and execute this file


![Permission](https://linuxcommand.org/images/file_permissions.png)

* `chmod` is command that is used to change the permission of a file or directory.
* We use `octal notation` to change the permission. 

```text
rwx rwx rwx = 111 111 111
rw- rw- rw- = 110 110 110
rwx --- --- = 111 000 000

and so on...

rwx = 111 in binary = 7
rw- = 110 in binary = 6
r-x = 101 in binary = 5
r-- = 100 in binary = 4
```

```sh
$ chmod linuxbox some_file
```
*  (rw-------) The owner may read and write a file. All others have no rights. A common setting for data files that the owner wants to keep private. 

* `chmod` is also used to control the access permission for directories.again we use octal notation to set permission, but the meaning of `r` , `w` , `x` are different.
* `Directory Permission` 
  * `r` - Allows the contents of the directory to be listed if the x attribute is also set.others
  * `w` - Allows files within the directory to be created, deleted, or renamed if the x attribute is also set.
  * `x` - Allows a directory to be entered (i.e. cd dir).

* Become The superuser for while.
  * `su` is used to login into the root.
  * `sudo any-command` is also used to run any command with root privilege.
  * `sudo -i` is to enter the root.
   

* Changing file ownership :
  * ``$ sudo chown you somefile``
  * `chown`  works same way in directory as it does in file.

* Changing Group ownership :
  * ``$ chgrp new_group some_file`` 
  * For changing the group we must be the owner of the file or directory to perform `chgrp`.

* [Resource](https://linuxcommand.org/lc3_lts0090.php)

#### Hacker Practice

##### SSH
* `SSH ` stands for secure shell. it's a protocol(messaging language)used to get a remote shell on another machine.
* Remote shell is what sounds like an interactive shell you can use on a machine you don't have physical access too.

```sh
ssh <username>@<ip_address>
```

* For practice, we can use overthewire Bandit CTF..

* [Over-the-wire](https://overthewire.org/wargames/bandit/)

```plain
bandit0
- bandit0
bandit1
- NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
bandit2
- rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
bandit3
- aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
bandit4
- 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
bandit5
- lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
bandit6
- P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
bandit7
- z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
bandit8
- TESKZC0XvTetK0S9xNwm25STk5iWrBvP
bandit9 
- EN632PlfYiZbn3PhVK3XOGSlNInNE00t
bandit10 (strings)
- G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
bandit11
- 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
bandit12 (rot13 - tr 'A-Za-z' 'N-ZA-Mn-za-m')
- JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
bandit13
- wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
bandit14
-  ssh bandit14@localhost -i sshkey.private -p 2220
- fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
bandit15
-  telnet localhost 30000
- fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq , after paste the pass we got a new pass of lvl 15
- jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

```


