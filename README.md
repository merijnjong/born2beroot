# born2beroot
Create a machine in VirtualBox under specific instructions. Then, at the end of this project, set up your own operating system while implementing strict rules.

### Guidelines
* The use of VirtualBox (or UTM if you can’t use VirtualBox) is mandatory.
* Only turn in a [signature.txt](https://github.com/merijnjong/born2beroot/blob/main/signature.txt) file at the root of the repository. Paste in it the signature of your machine’s virtual disk.
  
### Instructions
* Choose as an operating system, either the latest stable version of Debian (no
testing/unstable), or the latest stable version of Rocky. Debian is highly recommended
if you are new to system administration.
* Create at least 2 encrypted partitions using LVM. Below is an example of the
expected partitioning:
![Expected partitioning](https://github.com/merijnjong/born2beroot/blob/main/Schermafbeelding%202023-12-13%20140131.png)
* An SSH service will be running on port 4242 only. For security reasons, it must not be
possible to connect using SSH as root.
* Configure the operating system with the UFW (or firewalld for Rocky)
firewall and thus leave only port 4242 open.
* The hostname of your virtual machine must be your login ending with 42 (e.g.,
wil42). You will have to modify this hostname during your evaluation.
• You have to implement a strong password policy.
• You have to install and configure sudo following strict rules.
• In addition to the root user, a user with your login as username has to be present.
• This user has to belong to the user42 and sudo groups.
* Your password has to expire every 30 days.
* The minimum number of days allowed before the modification of a password will
be set to 2.
* The user has to receive a warning message 7 days before their password expires.
* Your password must be at least 10 characters long. It must contain an uppercase
letter, a lowercase letter, and a number. Also, it must not contain more than 3
consecutive identical characters.
* The password must not include the name of the user.
* The following rule does not apply to the root password: The password must have
at least 7 characters that are not part of the former password.
* Of course, your root password has to comply with this policy.
* Authentication using sudo has to be limited to 3 attempts in the event of an incorrect password.
* A custom message of your choice has to be displayed if an error due to a wrong
password occurs when using sudo.
* Each action using sudo has to be archived, both inputs and outputs. The log file
has to be saved in the /var/log/sudo/ folder.
* The TTY mode has to be enabled for security reasons.
* For security reasons too, the paths that can be used by sudo must be restricted.
Example:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin
* Finally, you have to create a simple script called monitoring.sh. It must be developed in bash.
* At server startup, the script will display some information (listed below) on all terminals every 10 minutes (take a look at wall). The banner is optional. No error must
be visible.
* Your script must always be able to display the following information:<br />
• The architecture of your operating system and its kernel version.<br />
• The number of physical processors.<br />
• The number of virtual processors.<br />
• The current available RAM on your server and its utilization rate as a percentage.<br />
• The current available memory on your server and its utilization rate as a percentage.<br />
• The current utilization rate of your processors as a percentage.<br />
• The date and time of the last reboot.<br />
• Whether LVM is active or not.<br />
• The number of active connections.<br />
• The number of users using the server.<br />
• The IPv4 address of your server and its MAC (Media Access Control) address.<br />
• The number of commands executed with the sudo program.<br />
* This is an example of how the script is expected to work:
![Expected output of the script](https://github.com/merijnjong/born2beroot/blob/main/Schermafbeelding%202023-12-13%20141113.png)
* Below are two commands you can use to check some of the subject’s requirements:
![Commands to check the subject's requirements](https://github.com/merijnjong/born2beroot/blob/main/Schermafbeelding%202023-12-13%20141339.png)
