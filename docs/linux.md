##GENERAL OVERVIEW
Linux is an operating system that is very popular amongst the scientific community due to it's clarity and compatibility with other hardwares. All these characteristics, in addition to having many functional tools that make data analysis easier, makes it an ideal system to be used research-wise.
It has a very friendly interface that is quite similar to Windows, which allows the user to use it even without any prior knowledge in how terminal commands work. Albeit being so easy-to-use, the major focus here will be in providing a simple introduction on how Linux works, specifically in relation to the fundamentals on how to get simple tasks done, such as creating a file, through the terminal.

##INSTALLING
It is possible to have Linux on your computer as the only operating system or have it work alongside Windows (dual boot).The easiest way to install Linux on your computer is by creating a Live CD (or pen drive) and, in this way, the installation process occurs quite smoothly. There are many tutorials online which describe it step-by-step and a suggestion would be to follow the instructions described by the link below to learn how to create a Live Pen Drive:

- [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0)

After succesfully creating the Live Pen Drive, you will need to boot it and make the necessary configurations. Switching back to Windows is quite easy by turning off the computer and removing the Pen Drive.

Although easy to install, a Live Pen Drive is limited in relation to the amount of space necessary for certain files. This can make it very slow and inefficient. A solution would be to have a visualization software and have Linux work as a virtual machine on Windows. A popular and free software is VirtualBox, which can be found in the link below (be sure to check if the download corresponds to Windows users if that is the case):

- [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

If a visualization software is being used, it is necessary to get used to the fact that the host will always be considered your physical computer and the guest, your virtual machine. With this concept in mind, the next step is to install the guest operating system. Once this is done, you are ready to learn the basics of command line in Terminal!

## TERMINAL
The terminal, also known as the shell, is a program that receives specific codes that are typed out by the users and then directs commands that the computer acts on. Normally just by searching the word "terminal" on the computer it's easy to be found.

Example of a terminal:

![Example of a terminal](http://linuxcommand.org/images/Screenshot-Terminal.png)

Once the terminal is open on your computer, various commands can be executed. The table below describes a few of them:

|**Command**          |**Description** 
|:-------------------:|:-------------------:|
|ls                   | Lists arquives      |
|cd                   | Changes directory   |
|cd ..                | Return to previous directory|
|touch                | Creates a new file  |
|rm                   | Removes file        |
|mkdir                | Creates a new directory|
|gedit                | Runs program        |
|history<             | Creates a text containing the code you used on terminal|

There are many other commands but these are the most basic ones that will help beginners get a head start. A good exercise would be to start by opening terminal and trying out these commands to get a closer look on what each one does.

##**UNDERSTANDING FILE PERMISSIONS**
Another important detail when using linux and sharing the computer with others is understanding how to read if you have permission to access certain files. Learning how to establish who has control over the files you have created is just as important. Even if you happen to be the only user of a computer, this is an efficient method to protect your computer from suffering from particular mistakes that might be harmful.

File permissions are defined differently by each of the following:

-  **USER**: The person that runs the file. The general rule is that whoever created the file is therefore it's user.

-  **GROUP**: All the users that belong to the same usergroup will have the same type of access permission towards a file. This is useful so that many people can contribute to the same file but configurations have to be made accordingly to make sure it works.

-  **OTHER**: A person who is neither the owner of the file or participant of the same group the file does.

There are also three types of access permissions on linux:

-  **READ PERMISSION**: When talking about a file, it can be open and read. In relation to the directory, it's contents can be listed.

-  **WRITE PERMISSION**: A file can be altered, that is, new data can be written upon it. Deleting or renaming the file is only possible if you also have permission through the directory as well.

-  **EXECUTE PERMISSION**: 

