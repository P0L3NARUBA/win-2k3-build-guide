<!-- Made with ❤️ by yungDoom -->

<h1 align="left"> 📜 Windows Server 2003 Build Guide </h1>

The first and last Github Guide about Windows Server 2003.<br>
P.S: This guide took me half an hour to write so make sure you hit that star button :)

# Contents
1. [Prerequisites](#prerequisites)
2. [Preparing the Workspace](#preparing-the-workspace)
3. [Building](#building)
4. [Post Building](#post-building)
5. [Credits](#credits)

## Prerequisites
- Windows 10 and 64-bit system are recommended 
- nt5src.7z : ``magnet:?xt=urn:btih:1a4e5b67060ff2bc8fe2de36a6c265c77f392a0c&dn=NOTREPACKED``
- [QBittorent](https://www.qbittorrent.org/download)
- [Git](https://git-scm.com/downloads)
- [win2003_prepatched_v10a.zip](https://mirrorace.org/m/3Lxas)
- [Certutil for creating certificates](https://github.com/P0L3NARUBA/win-2k3-certutil)
- [Windows Server 2003 ISO for Missing Files](https://archive.org/details/en_windows_server_2003_standard)

# Preparing the Workspace
1. First of all, disable your antivirus since it will slow down or corrupt everthing while compiling or extracting
2. Create or Use Partition with D: Letter
   - net use D: \\localhost\c$\nt5source /persistent:yes
3. Extract **nt5src.7z\Win2K3** to D:\ drive
4. Edit **x.bat** and change it with these:
```
rem goto end
extract /y /a /e /l D:\srv03rtm 3790src1.cab
extract /y /a /e /l D:\srv03rtm 3790src2.cab
extract /y /a /e /l D:\srv03rtm 3790src3.cab
extract /y /a /e /l D:\srv03rtm 3790src4.cab
extract /y /a /e /l D:\srv03rtm 3790src5.cab
:end
```
5. Save the file
6. Open the bat file as Administrator and wait till everything done
7. Right Click to the source folder and untick the "Read-only" setting and press "Apply"
8. Extract the contents of **win2003_prepatched_v10a.zip** to **D:\srv03rtm** Location
9. Create a new folder inside the source folder and name it as **certutil** and put everything inside of **win-2k3-certutil** to that new folder
10. Open the **generate.sh** with **Git Bash** and wait until your certificates are generated
11. Go inside **srv03rtm.certs\tools** folder and install the following certificates one by one: **driver.pfx, testpca.cer, testroot.cer and vbl03ca.cer**
   - For driver.pfx, follow these steps:
      1. Right Click and Press "Install PFX"
      2. Select **Local Machine**
      3. Spam Next button and finish the installation
   - For the other certificates, follow this steps in order to install them:
      1. Select 3 of the certificates: **testpca.cer, testroot.cer and vbl03ca.cer**
      2. Right Click and Press "Install Certificate"
      3. Select **Local Machine**
      3. Spam Next button and do the same for all three
   - Also do not remove this folder as the certificates will be unavailable.

# Building
8. When the extracting finished, open a command prompt as administrator inside **srv03rtm** and type **tools\razzle64.cmd free offline** or **tools\razzle.cmd free offline** if you're using 32-bit system
9. Wait until the razzling done :D
10. Type **tools\prebuild.cmd** to the cmd and wait until its finished
11. Now its time to build this GOLD! Type **build /cZP** to start the building process (which will take a lot of time)
   - Use **build /ZP** if you dont want to build everything over and over again, that will take your time for nothing
11. If the building has been done, proceed to the next section.

# Post Building
1. Mount the ISO of the Windows Server 2003
2. Go to "Disk Management"
3. Change the **NRMSVOL_EN** letter to G:\
  - Right click to this partition and press "Change Drive Letter and Paths..."
  - Select Change
  - Change the Letter E to G
4. Type **tools\missing.cmd** to cmd and wait
5. When the command finished, Type **tools\postbuild.md -sku:srv** and wait again........
6. Copy **ASMS.CAB** and **HIVESXS.INF** from **G:\I386** to **D:\binaries.x86fre\srv\i386**
7. Type **tools\oscdimg.cmd srv** and be patient it will take some time
8. Done! if you did everything right then you should see your compiled iso in the D:\ drive.
   - The name of the iso should be like this: 3790.x86fre.srckit.**yymmdd**-**hhmm**_srv.iso

 # QNA

 * Q: Is there any patches that we can make this OS more useable and more stable?<br>
  A: Of course there are some patches, for example [OpenXP](https://download.theopenxp.org/)

   * Q: The rentry.co guide has a lot of files etc. why didnt you included them in this guide?<br>
     A: Because that files are unnecessary for the build step, i just wrote the important steps to watch/reproduce.

* Q: I didnt understood what to do, is there any videos about it?<br>
  A: Theres a video that made by NTDEV you can check it out: https://www.youtube.com/watch?v=AWZe00v2Rs0

   * Q: I need help, where can i contact?<br>
     A: You can come to our discord server for help, you can write down your issue to the #help channel.

* Q: How much time it takes to build?<br>
  A: It really depends, sometimes it takes too faster but sometimes its just takes a lot of time.

# Credits

- Re-uppers & Backupers
  - Thanks to all of you guys for making this sh*t a lot easier!

<!-- Made with ❤️ by yungDoom -->
