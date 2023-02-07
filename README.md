<h1>Install & Configure Samba</h1>

<h2>Description</h2>
Project consists of a basic configuration of Samba, providing access to Samba shares via an MS Windows client machine, and creating an FTP server to transfer files from another machine.
<br />


<h2>Utilities Used</h2>

- <b>VirtualBox</b>
- <b>Debian Environment</b>
- <b>Terminal</b>
- <b>Windows</b>

<h2>Samba Setup:</h2>
Under the root user, the apt install samba -y command is run to install the Samba service:<br/>
<img src="https://imagizer.imageshack.com/img923/9009/zUhbld.png" alt="Disk Sanitization Steps"/>
<br />
<br />
No is selected under the Samba server and utilities dialogue box:<br/>
<img src="https://imagizer.imageshack.com/img924/742/QCeZ2G.png" alt="Disk Sanitization Steps"/>
<br />
<br />
Nano is executed to access the service configuration file:<br/>
<img src="https://imagizer.imageshack.com/img923/3497/FPyCkd.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The following break of text is added to the configuration file:<br/>
<img src="https://imagizer.imageshack.com/img922/2066/tNjzeQ.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The smbpasswd command is used to add the user to the SMB service:<br/>
<img src="https://imagizer.imageshack.com/img923/5553/Xm9M1C.png" alt="Disk Sanitization Steps"/>
<br />
<br />
SMBD is then restarted verified to be running:<br/>
<img src="https://imagizer.imageshack.com/img924/4014/2EFrPX.png" alt="Disk Sanitization Steps"/>
<br />
<br />

<h2>Connect to the share:</h2>
The directory shared in Debian will be connected to from a Windows machine using VirtualBox. The Windows VM settings are opened:<br/>
<img src="https://imagizer.imageshack.com/img922/6513/9xAye3.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The Network settings are selected, and a Bridged adapter is set between the Windows and Debian machines:<br/>
<img src="https://imagizer.imageshack.com/img924/1903/cCoGDV.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The ip of the Debian machine is checked:<br/>
<img src="https://imagizer.imageshack.com/img922/6096/XpVrMJ.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The CMD of the windows machine is opened:<br/>
<img src="https://imagizer.imageshack.com/img923/1102/1mTPlM.png" alt="Disk Sanitization Steps"/>
<br />
<br />
A ping to the Debian machine verifies connectivity:<br/>
<img src="https://imagizer.imageshack.com/img924/6425/QLe6c8.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The Debian machine's share file is navigated to in the search bar of file explorer:<br/>
<img src="https://imagizer.imageshack.com/img922/9711/nv1ZFS.png" alt="Disk Sanitization Steps"/>
<br />
<br />

<h2>Install the FTP Server:</h2>
The apt install command is executed to install the FTP service:<br/>
<img src="https://imagizer.imageshack.com/img924/3779/SzKCG8.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The apt install command is used to install the vsftpd service:<br/>
<img src="https://imagizer.imageshack.com/img923/9245/BnRIgA.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The vsftpd config file is opened:<br/>
<img src="https://imagizer.imageshack.com/img924/9606/aJbh0W.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The line: write_enable=YES is searched and uncommented. This option will enable uploading files to Debian:<br/>
<img src="https://imagizer.imageshack.com/img923/6294/GW7flg.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The following line is also uncommented: chroot_local_user=yes. This prevents all local users from leaving their home directory:<br/>
<img src="https://imagizer.imageshack.com/img923/5040/2Srk8K.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The following option is added: allow_writeable_chroot=YES: to the end of the file. This option bypasses the check for write permissions:<br/>
<img src="https://imagizer.imageshack.com/img924/5453/eEMoKz.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The chmod command is used to provide everyone with write permission in my home directory. It is verified with the ls -l /home/ command:<br/>
<img src="https://imagizer.imageshack.com/img922/7136/gr7w3s.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The service is then restarted and verified as active:<br/>
<img src="https://imagizer.imageshack.com/img923/5015/cMJ67n.png" alt="Disk Sanitization Steps"/>
<br />
<br />

<h2>Connect to the FTP Server:</h2>
The windows machine CMD is opened:<br/>
<img src="https://imagizer.imageshack.com/img922/811/ggcmcX.png" alt="Disk Sanitization Steps"/>
<br />
<br />
A Hello World file is created using the name ftpTransfer.txt:<br/>
<img src="https://imagizer.imageshack.com/img923/4028/KMYbSQ.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The dir command is used to verify the files creation:<br/>
<img src="https://imagizer.imageshack.com/img923/6329/wl9qRe.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The ftp command is used to open the connection to the Debian FTP server. The password is entered:<br/>
<img src="https://imagizer.imageshack.com/img924/2777/aHFkSb.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The put command i used to upload ftpTransfer.txt to the FTP server:<br/>
<img src="https://imagizer.imageshack.com/img922/5328/o4H3ZX.png" alt="Disk Sanitization Steps"/>
<br />
<br />
On the Debian machine, the file exists. This verifies the FTP servers functionality:<br/>
<img src="https://imagizer.imageshack.com/img924/5043/g5LKyT.png" alt="Disk Sanitization Steps"/>
<br />
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
