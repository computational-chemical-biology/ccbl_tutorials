## WHAT IS SSH?
SSH (Secure shell) is a network protocol that gives users, particularly system administrators, a secure way to access a computer over an unsecured network. It provides strong authentication and encrypted data communications between two computers connecting over an open network such as the internet. Administrators normally use it to manage systems and applications remotely. They can log into another computer over a network, execute commands and move files from one computer to the other.
If you log in and out of many remote servers on a daily basis, surely it is troubling to remember all the usernames, remote addresses and command lines. Therefore, a SSH configuration file will simplify your life by allowing you to create shell aliases.

##SHELL ALIASES

**1**. After configuring your computer to recognize another server by inserting the ip address, you  have to open your terminal and enter the command "ssh -p 2222 UserName@SSHserver.example.com". The password also needs to be inserted after pressing enter. 

**Obs.** -p 2222 is an example of an SSH port 




**2**. Enter the server again by typing in "ssh -p 2222 UserName@SSHserver.example.com" again and enter "sh-keygen" to generate the access key.





**3**. Move the file where the key was created to the Desktop being aware of using the correct ip address. Be sure to be in the exact file where the key was generated for this to work. In this case, the key was generated inside the ssh folder and being moved to the Desktop.





**4**. Go back to your host computer and create a config file containing the following information as exampled below:

-  Host hostName 
-      Hostname 127.0.0.1 
-      Port 22
-      User UserName 
-      IdentityFile ~/.ssh/id_rsa_server.pub

First, once inside the .ssh/, create the file by typing in "touch config", then type in "nano config" so that you can insert the information shown above.




**5**. Move the key you saved on the desktop to the ssh./ folder and rename it the same way you named the information exampled in step 5. Which is, in this case, hostName. By typing in "ls" afterwards, you can check whether the file is truly there.




**6**. Finally, it is done! You no longer have to type in the full SSH port with the server address to access remotely.



**7**. But now you also want to be able to access it without the need of a password. To do this, enter the server.




**8**. Go to ssh and create the file "authorized_keys"



**9**. Meanwhile, open another tab and go to your home server and generate a key by typing in "ssh-keygen". Afterwards, type in "less" so that you can see the entire key. Then copy the key to the destination server by typing in "scp id_rsa.pub hostName:/home/ana", for example.



**10**. Go back to your server (into your home page) and change the name of id_rsa.pub to authorized_keys by typing in "mv id_rsa.pub authorized_keys". Move authorized_keys to the ssh file by typing "mv authorized_keys .ssh".


There! Now you can enter your server without needing the password or typing in the full SSH port with the server address.

