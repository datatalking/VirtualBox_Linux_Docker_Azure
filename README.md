# VirtualBox_Linux_Docker_Azure
When you must have AzureDataStudio inside a Linux Docker

# Linux=>Docker=>Sql server=>AzureDataStudio

Installing a Msft SQL Serverexpress, inside a docker, inside linux on a virtualbox  (when you absolutely must).

## Installation details for mac

1. Install then download virtual box -https://www.virtualbox.org/wiki/Downloads or ```sudo apt-get install virtualbox```

2. Download the Ubuntu installation disk image - https://ubuntu.com/download/desktop or https://www.youtube.com/watch?v=x5MhydijWmc

3. Create a new virtual machine in VirtualBox.
  * 3a. Give it at least 40GB of disk space.
  * 3b. Add your virtual Ubuntu installation disk image to the optical drive for your virtual machine
  * 3c power it on and follow the instruction steps, choose default or simplest installation.
4. When the Ubuntu virtual machine installation is finished.
  * 4a. Access the iso file 
  * 4b. Add update, wifi and install
  * 4c. ```sudo apt install build-essential dkms linux-headers-$(uname -r)```
  * 4d Around 18:04 the video calls for 'guest' image, if you get an error 'Could not mount the media/drive '/Applications/VirtualBox.app/Contents/MacOS/VBoxGuestAdditions.iso' (VERR_PDM_MEDIA_LOCKED).'
Then go to 'https://forums.virtualbox.org/viewtopic.php?f=8&t=94291' and follow the instructions by user 'socratis' 08/13/2019 regarding 'something has locked your VBoxGuestAdditions.iso.'
  * 4e Follow the instruction for bidirectional in video  
  * 4f On mac you may also need to add VirtualBox.app and VirtualBoxVM.app to your privacy allowances to give it access for keystrokes.
  * 4f Uou will likely need to restart either your machine or the virtual machine several times
5. Installing Docker on Ubuntu - https://www.youtube.com/watch?v=aMKUuaga85A. These instructions should work.
  * 5a. There is a possible cross-link issue where you type in 'command+c' on the mac and it blanks the screen, this is some kind of command in Linux on my version. 'https://askubuntu.com/questions/1134892/ubuntu-18-04-20-04-lts-on-virtualbox-boots-up-but-black-login-screen' This is a security issue for mac graphics cards to protect the user. It's a driver issue and you have to tell mac to open up to 64MB of virtual memory.
6. Ok the video -link- has very small font but he mentions a few things that need to be updated.
  * 6a ```ifconfig``` doesn't work by default on mac so you need to run ```sudo apt install net-tools```
  * 6b You will want the ip address in the first paragraph next to the docker as inet '000.00.0.0' replace the zeros with your ip address. So the instructions here on out didn't work for me, but I did find this gist with instructions that did.
this Youtuber 'https://www.youtube.com/watch?v=x6pYoWwtVAY' made a gist.
'https://gist.github.com/kstevenson722/3fff3a76b3f25d4693a2da53438f3341' The instructions worked flawlessly.
  * 6c. Ok as usual Microsoft code fails to mention (upfront) that your password must be. at least 8 characters include three of the four types. Uppercase, lowercase, numbers, symbols.
  * 7 Save your password as you will 
USE master;

CREATE DATABASE da320 
ON PRIMARY (FILENAME = '/var/opt/mssql/data/da320.mdf'),
   (FILENAME = '/var/opt/mssql/data/da320_log.ldf') 
FOR ATTACH
  * 8 To exit type exit
  * 9 Now we can install Azure Data Studio from https://docs.microsoft.com/en-us/sql/azure-data-studio/download-azure-data-studio?view=sql-server-ver15. On step 2 insert the version of the azure data studio cd ~
sudo dpkg -i ./Downloads/azuredatastudio-linux-<version string>.deb so mine read cd ~
sudo dpkg -i ./Downloads/azuredatastudio-linux-1.28.0.deb
  * 10. Type 'azuredatastuio' and the gui will open


## Usage
   This is how to install virtual box, then inside that linux ubuntu, then inside that docker and SQL server with a AzureDataStudio gui.

## Contributing
Professor Theodore Spencer of Bellevue College wrote the origional version.
Andrew Schell as an Undergrad student compiled this README.md based on those instructions and research to find a platform agnostic method for installation.
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
