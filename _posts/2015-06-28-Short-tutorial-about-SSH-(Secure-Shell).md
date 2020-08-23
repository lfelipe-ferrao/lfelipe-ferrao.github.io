---
layout: post
title: Short tutorial about SSH (Secure Shell)
description: "What you need to do to start using SSH."
modified: 2016-07-11
tags: [tips, ssh, tutorial]
image:
  feature: LogoFundoAzul.jpg
  creditlink: http://augusto-garcia.github.io/
---

*Written by [Luis Felipe Ventorim Ferrão](http://augusto-garcia.github.io/statgen-esalq/people/) and [Marcelo Mollinari](http://augusto-garcia.github.io/statgen-esalq/former-students/)*

&nbsp;

SSH is a secure protocol that encrypts all data sent between the client
computer and the computer it is connecting to. SSH applications usually
allow both interactive terminal sessions on the remote machine and the
ability to transfer files securely. This guide is intended as a basic
introduction to using SSH commands.

&nbsp;

![charge](http://imgs.xkcd.com/comics/im_an_idiot.png)
*Credits and more great comics at: [xkcd](http://xkcd.com/)*

Table of Contents
=================

-   [Install and Configure OpenSSH Server In
    Linux](#install-and-configure-openssh-server-in-linux)
-   [Remote Connection](#remote-connection)
-   [Transferring Files with SSH](#transferring-files-with-ssh)
    -   [Command-line SSH commands](#command-line-ssh-commands)
    -   [Graphical interface](#graphical-interface)
    -   [Compress tar files/folder in
        linux](#compress-tar-filesfolder-in-linux)
-   [Run R Script remotely](#run-r-script-remotely)

Install and Configure OpenSSH Server In Linux
=============================================

**OpenSSH** is a free open source set of computer tools used to provide
secure and encrypted communication over a computer network by using the
**ssh** protocol. To install OpenSSH, open a terminal and run the
following commands with superuser permissions.

    sudo apt-get install openssh-server

Configure the ssh is done by editing the `sshd_config file` in the
`/etc/ssh` directory. The `sshd_config` is the configuration file for
the OpenSSH server and can be acessed and modified in the emacs (or
another text editor) by the following commands:

    sudo emacs -nw /etc/ssh/sshd_config

Configuring OpenSSH means striking a balance between security and
ease-of-use. Ubuntu's default configuration tries to be as secure as
possible without making it impossible to use in common use cases. More
information about OpenSSH can be accessed in
<https://help.ubuntu.com/community/SSH/OpenSSH/Configuring>.

Remote Connection
=================

The Remote Connection can be initialized using the ssh command
structure:

    ssh [option] [local-name]@[remote-host] 

-   `ssh`: ssh (SSH client) is a program for logging into a remote
    machine and for executing commands on a remote machine.

-   `user-name`: remote user system to be used in connection;

-   `remote-host`: Host where the command will be executed. It can be
    specified as a name or as an IP Address (commonly used);

-   `option`: different arguments can be used, some of them will be
    detailed;

<table style="width:100%;">
<colgroup>
<col width="10%" />
<col width="90%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">-p</td>
<td align="left">Port to connect to on the remote host (usually 22 is the default port). *p* is lowercase. </td>
</tr>
<tr class="even">
<td align="left">-X</td>
<td align="left">Enables X11 forwarding (important to access graphical interface). *X* is uppercase.</td>
</tr>
</tbody>
</table>

Example: acessing some remote machine by the 32 port, using the
`username` user in the following IP adress: `192.164.0.50`. The command
line for this action is:

    ssh -p 32 username@192.164.0.50

In the first connection, a warning is provided confirming the server ID.
After providing the password, the connection is established and in the
remote machine the prompt is displayed. From there, all commands are
executed on the remote machine. Experiment view directories and folders
in the remote machine using the `ls` command. Check if there are other
user logged using the `w` command or check the real-time processes using
`top`.

Transferring Files with SSH
===========================

An important action using ssh service is the file transference between
machines. There are different ways to do it, however we will show the
transference via i) command-line (`scp` and `sftp`) and ii) graphical
interface.

Command-line SSH commands
-------------------------

There are two main command-line SSH commands to transfer files: **scp**
and **sftp**. `scp` is a primitive way and a non-interactive command
that takes a set of files to copy on the command line, copies them, and
exits. On the other hand, `sftp` is an interactive and more user
friendly command that opens a persistent connection where multiple
copying commands can be performed through.

### scp

#### Sending a file from LOCAL user to REMOTE MACHINE:

    scp [option]<path.local>[user@destination]:<path.destination> 

-   `scp`: command to transfer files;

-   `path.local` : file in the local path that I want to send to a
    remote machine;

-   `user@destination`: remote machine identification;

-   `:path.destination` : path in the remote machine where the file will
    be sent;

-   `option`: -P (port to connect to on the remote host)

Below are represented a simple way to send a file from local user to a
host machine (local-&gt;host). Send the file, by the port 32, in the
path `/home/local_user/myfile.txt` to the `username@192.164.0.50`
(remote host), and store this file in the home of the remote host
(`/home/remote_user/`). To confirm the send, access the remote machine
and look for the file in the home path using the **ls** command.

    # Sending a file: Local -> host
    scp -P 32 /home/local_user/myfile.txt username@192.164.0.50:/home/remote_user/

    # Confirm the send
    ssh -p 32 username@192.164.0.50
    ls

*OBS: The -P argument in the scp command is in UPPERCASE, different than
ssh command (-p).*

#### Downloading a file from REMOTE MACHINE to LOCAL:

    scp [option] [user@destination]:<path.destination> <path.local> 

-   `:path.destination` : file in the path remote machine that I want to
    send to a local user;

-   `user@destination`: remote machine identification;

-   `:path.local` : path in the local user where the file will be sent;

-   `option`: -P (port to connect to on the remote host)

Below are represented a simple way to download a file from host machine
to a local user (host-&gt;local). With the command it will download the
file, by the port 32, from the `username@192.164.0.50` (remote host) in
the path `/home/remote_user/myfile.tx` and store this file in the home
of local user (`/home/local_user/`). To confirm the send, in the local
machine, look for the file in the home path using the **ls** command.

    # Downloading a file: Host -> local
    scp -P 32 fulano@192.164.0.50:/home/remote_user/myfile.txt /home/local_user/ 

    # Confirm the downloading
    ls

### sftp

In interactive mode, **sftp** logs you into the remote system and places
you at a prompt that is similar to the command prompt on your local
system. From the local system's command line, you can start the **sftp**
session using the command:

    sftp [option] [user@destination]

-   `user@destination`: remote machine identification;

-   `option`: -P (port to connect to on the remote host)

The sftp protocol performs all operations over an encrypted ssh session.
It uses many of the features of ssh, such as public key authentication
and data compression. The sftp for transferring files is more user
friendly than scp, however the function has a typical syntax which has
to be known. It offers a limited, but very useful, set of commands which
you can navigate in the remote file system and also send and receive
files.

A summary is presented:

<table style="width:100%;">
<colgroup>
<col width="40%" />
<col width="60%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">cd</td>
<td align="left">Change the REMOTE working directory to path</td>
</tr>
<tr class="even">
<td align="left">lcd</td>
<td align="left">Change the LOCAL working directory to path</td>
</tr>
<tr class="odd">
<td align="left">ls</td>
<td align="left">Display a REMOTE directory</td>
</tr>
<tr class="even">
<td align="left">lls</td>
<td align="left">Display a LOCAL directory</td>
</tr>
<tr class="odd">
<td align="left">pwd</td>
<td align="left">Display the name of the REMOTE working directory</td>
</tr>
<tr class="even">
<td align="left">lpwd</td>
<td align="left">Display the name of the LOCAL working directory</td>
</tr>
<tr class="odd">
<td align="left">rm</td>
<td align="left">Delete the REMOTE file specified by path</td>
</tr>
<tr class="even">
<td align="left">lrm</td>
<td align="left">Delete the LOCAL file specified by path</td>
</tr>
<tr class="odd">
<td align="left">put [<em>local-path</em>] [<em>remote-path</em>]</td>
<td align="left">Upload [<em>local-path</em>] and store it on the [<em>remote-path</em>]</td>
</tr>
<tr class="even">
<td align="left">get [<em>remote-path</em>][<em>local-path</em>]</td>
<td align="left">Retrieve the [<em>remote-path</em>] and store it on the [<em>local-path</em>]</td>
</tr>
<tr class="odd">
<td align="left">?</td>
<td align="left">help</td>
</tr>
<tr class="even">
<td align="left">quit</td>
<td align="left">quit sftp</td>
</tr>
</tbody>
</table>

The mainly commands presented are `put` and `get`. For transfer
directories between the local user and the remote machine the argument
**-r** can be used. Some examples:

    # Acessing a remote machine
    sftp -P 32 username@192.164.0.50

    # Downloading mydocs.zip file from REMOTE MACHINE to /home/local_user in the LOCAL USER
    get home/remote_user/mydocs.zip /home/local_user

    # Downloading a Documents directories  from REMOTE MACHINE to /home/local_user in the LOCAL USER
    get -r /home/remote_user/Documents /home/local_user

    # Uploading mydocs.zip file from USER LOCAL to /home/remote_user in the REMOTE MACHINE
    put /home/local_user/mydocs.zip /home/remote_user

    # Uploading Documents directories from USER LOCAL to /home/lremote_user in the REMOTE MACHINE
    put -r /home/local_user/Documents /home/remote_user

*OBS: sftp does not recognize the shortcut for home directories (~), so
it is necessary use the complete name of the home directory.*

Graphical interface
-------------------

The use of graphical interface is possible, but it depends upon the
configuration in the server and user system. Depending of the remote
machine the graphical interface cannot be accessed. Further, the
transfer between machines using graphical interface usually is slower
than using command lines. If the graphical interface it is allowed, the
acess via ssh can be done by: `ssh -X -p 32 username@192.164.0.50`.
Example:

    # Acessing a remote machine
    ssh -X -p 32 username@192.164.0.50

    # Open a program
    gedit

To file transferences the graphical SFTP can be used. In the desktop
environment (the "explorer" in the Linux system), you have to be able to
see the location bar by pressing `CTRL +L`. Then, in the location bar
use the following command:

    sftp://[user@destination]:[port]

After providing the password, the connection is established and a window
with the files and directory in the remote machine is shown. The file
transference can be done by moving the icons in the window. This action
can be slow.

Other graphical interface such as **Nautilus** (gnome) and **Konqueror**
(KDE) may also be used. The **filezilla** is a friendly-user software
which makes the file transfer a suitable process. In this case, the
screen is divided and the files can be upload and download in an
interactive form between a local user and a remote machine.

Compress tar files/folder in linux
----------------------------------

In the transference process, it can be a good idea work with compress
file instead of upload or download separeted files "one by one". In this
sense, the command `tar` can help. A quick example about compress/zip
and uncompress/unzip files or folder is shown below.

### Compress/zip

    tar -czvf <new_name>.tar.gz <path_files_to_compress>

-   `new_name`: name of the compressed file;

-   `file_to_compress`: path of the files or folder that will be
    compressed;

-   `-czvf`: create a new tar file(`c`); use gzip to zip it (`z`);
    verbose , display file to compress or uncompress (`v`); and create
    the tar file with filename provided as the argument
    (`f`), respectively.

In the following example, compress all .R files into a new tar file
“Rscript.tar.gz”.

    # Compress/zip a remote machine
    tar -czvf Rscript.tar.gz *.R

*OBS: the symbol `*` in the code is a recursive signal and means: "I
want all the .R files "*

### Uncompress/unzip

    tar -xzvf <compressed_name>.tar.gz 

-   `compressed_name`: path of the compreesed file;

-   `-xzvf`: extract file (`x`); use gzip to zip it (`z`); verbose ,
    display file to compress or uncompress (`v`); and create the tar
    file with filename provided as the argument (`f`), respectively.

In the following example, extract the file “Rscript.tar.gz”.

    # Compress/zip a remote machine
    tar -xzvf Rscript.tar.gz

Run R Script remotely
=====================

An important action using **ssh** is to run an R script remotely. For do
it, you have to have the R software installed in the remote machine.
Some powerful text editors (emacs, vi ...) can be also installed in the
remote machine and used to edit and to run some R script. However, in
some cases, it is expected that the user only run the R script directly
in the terminal using command lines. For this, a suggested solution is
to upload all the necessary files from the `local_user` to the
`remote_user`, to access the remote machine and to execute the R script
in the prompt.

An example is presented below and the steps described are realized using
some commands already cited. A new function is the `R CMD BATCH` used to
run R script in the terminal. The command `R CMD BATCH --help` show some
information and arguments about the function.

    # Acessing the remote machine to transfer files
    sftp -P 32 username@192.164.0.50

    # Uploading script.R file from local_user to remote_user
    put /home/local_user/script.R /home/remote_user

    # Acessing the machine run the script.R
    ssh username@192.164.0.50

    # Running R script in the terminal
    R CMD BATCH script.R &

Some important tips:

-   A .Rout output file will be generated and can be used to check the
    evolution of the process with the following command line at the
    prompt: `tail -f script.Rout`.

-   The symbol `&` in the end of the command determined background
    running in the terminal. The same prompt can be used for others
    tasks which not only run the only one R script.

-   Include `print()` commands in the R script is a good idea, since it
    helps to keep up with the R.out evolution.

A more advanced structure is the command `R CMD BATCH` with arguments.
For this, we will consider a toy example about a sum function in R
script. Two arguments ( `x` and `y`) can be specified directly in the
prompt and the sum (x+y) is performed. The following R script can be
used with a specific "header" into the code.

    # HEADER
    options(echo=TRUE) 
    args <- commandArgs(trailingOnly = TRUE)
    print(args)
    for(i in 1:length(args)){
        eval(parse(text=args[[i]]))
    }
    rm(args)

    # Sum R. function
    my_sum<-function(x,y) x+y
    write.table(my_sum(x,y), file="result.txt")

In the prompt, the command `` R CMD BATCH `--args x=1 y=2` script.R & ``
can have the variable values be chosen and a **result.txt** file is
generated with the sum result.
