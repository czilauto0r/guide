![Example logo](https://i.imgur.com/4urtRFp.png)

# Masternode Setup Guide(Ubuntu 16.04)
This guide will assist you in setting up an Masternode on a Linux Server running Ubuntu 16.04. (Use at your own risk)

If you require further assistance contact the support team @ [Discord](https://discord.gg/discordlink)

## Requirements
1) **XXX coins.**
2) **A Vultr VPS running Linux Ubuntu 16.04.**
3) **A Windows local wallet.**
4) **An SSH client such as [Bitvise](https://dl.bitvise.com/BvSshClient-Inst.exe)**
***
## Contents
* **Section A**: Creating the VPS within [Vultr](https://www.vultr.com/?ref=reflink).
* **Section B**: Downloading and installing Bitvise.
* **Section C**: Connecting to the VPS.
* **Section D**: Preparing the local wallet.
* **Section E**: Setting up masternode.
* **Section F**: Connecting and starting the MN.
***

## Section A: Creating the VPS within [Vultr](https://www.vultr.com/?ref=reflink) 
***Step 1***
* Register at [Vultr](https://www.vultr.com/?ref=reflink)
***
***Step 2***
* After you have added funds to your account go [here](https://my.vultr.com/deploy/) to create your Server
***

***Step 3*** 
* Choose a server location (preferably somewhere close to you)
![alt location](https://i.imgur.com/CB5xOmh.png)
***

***Step 4***
* Choose a server type: Ubuntu 16.04
![alt OS](https://i.imgur.com/8EPu2vB.png)
***

***Step 5***
* Choose a server size: $5/mo will be fine 
![alt exampleOS](https://i.imgur.com/FW03Kpe.png)
***

***Step 6*** 
* Set a Server Hostname & Label (name it whatever you want)
![alt hostname](https://i.imgur.com/K9zoP7X.png)
***

***Step 7***
* Click "Deploy now"

![alt Deploy](https://i.imgur.com/Ilm8dN0.png)
***


## Section B: Downloading and installing BitVise. 

***Step 1***
* Download Bitvise [here](https://dl.bitvise.com/BvSshClient-Inst.exe)
***

***Step 2***
* Select the correct installer depending upon your operating system. Then follow the install instructions. 

![alt PuttyInstaller](https://i.imgur.com/K9FoFf1.png)
***


## Section C: Connecting to the VPS & Installing the MN via Bitvise.

***Step 1***
* Copy your VPS IP (you can find this by going to the server tab within Vultr and clicking on your server. 
![alt Vultr](https://i.imgur.com/ivwd2EP.png)
***

***Step 2***
* Open the bitvise application and fill in the "Hostname" box with the IP of your VPS.
![alt PuttyInstaller](https://i.imgur.com/CEZLyk4.png)
***

***Step 3***
* Copy the root password from the VULTR server page.
![alt RootPass](https://i.imgur.com/XCEmTTL.png)
***

***Step 4***
* Type "root" as the login/username.
![alt Root](https://i.imgur.com/zgl2Vc6.png)
***

***Step 5*** 
* Paste the password into the Bitvise terminal by right clicking (it will not show the password so just press enter)
![alt RootPassEnter](https://i.imgur.com/3sIaeQf.png)
***

***Step 6*** 
* Once you have clicked open it will open a security alert (click yes).  
***


***Step 7***
* Write the commands below into the Bitvise terminal,

<b>sudo apt-get update</b> to update ubuntu

<b>sudo apt-get upgrade</b> to upgrade packages

<b>wget link.to.core</b> to download core

<b>tar xzvf core.tar.gz</b> to extract core
  



![alt Bash](https://i.imgur.com/9qVfyQ2.png)

***

***Step 8***
* Sit back and wait for the extract.
***

## Section D: Preparing the Local wallet

***Step 1***
* Download and install the wallet [here](https://linktowallet.com)
***

***Step 2***
* Create a text document to temporarily store information that you will need.
***

***Step 3***
* Send EXACTLY XXX coins to a receive address within your wallet.
![alt receive](https://i.imgur.com/FqMcqA4.png)
![alt copy](https://i.imgur.com/IADWJPr.png)
***

***step 4***
* After your send transaction has 15 confirms, go to the debug console within the wallet 

![alt console](https://i.imgur.com/Oiov1Gs.png)
***

***Step 5***
* Type the command below and press enter 

`masternode outputs` 

`masternode outputs`

***

***Step 6***
* Copy and save to text document.
* Paste these into the text document you created earlier as you will need them in the next step.
***

# Section E: Setting up masternode VPS

***Step 1***
* Jump to VPS server in root line.
![alt root](https://i.imgur.com/Njeo0gp.png)

*Type command below to edit configuration file.

<b>nano .ultranatumcore/ultrantum.conf</b>

<b>and pres ctrl key + o</b>

This lets us edit he text and we must enter the below.
![alt conf](https://i.imgur.com/x5UBk13.png)

<b>rpcallowip=127.0.0.1
  
rpcuser=ULTRAMN (choose your username)
  
rpcpassword=PASSWORD (choose your password)

staking=1

server=1

listen=1

port=23654

masternode=1

masternodeaddr=IPADDRESS:23654

externalip=IPADDRESS:23654

masternodeprivkey=MNGENKEY</b>

* The `IPADDRESS` is the IP and port of your server.
* The `MNGENKEY` is your masternode GEN key (from text document in Section D step 6).
* rpcuser and rpcpassword field don't matter.

<b>After that press CTRL key + X to exit, and Y to save and go back to root line</b>
![alt root](https://i.imgur.com/Njeo0gp.png)

<b>Start the server with your config file all setup by typing:
ultranatumcore-1.0.0.1/bin/ultranatumd -daemon</b>

***

# Section F: Connecting & Starting the MN 

***Step 1***
* Go to the tools tab within the local wallet and click open "masternode configuration file" 
![alt create](https://i.imgur.com/gVnKbJc.png)
***

***Step 2***

* Fill in the form. 
* For `Alias` type something like "MN01" **don't use spaces**
* The `Address` is the IP and port of your server (this will be in the Bitvise terminal that you still have open).
* The `PrivKey` is your masternode GEN key (This is also in the Bitvise terminal that you have open).
* The `TxHash` is the transaction ID/long key that you copied to the text file.
* The `Output Index` is the 0 or 1 that you copied to your text file.

<b>(Example: MN01 127.0.0.1:23654 U3HaYBVUCYjEMeeH1Y4sBGLALQZE1Yc1K64xiqgX37tGBDQL8Xg 
2bcd3c84c84f87eaa86e4e56834c92927a07f9e18718810b92e0d0324456a67c 0)</b>

Click "File Save"
***


***Step 3***
* Close out of the wallet and reopen Wallet
* Click on the Masternodes tab
* Click on the Masternode you want to start, and click Start Alias
***

***step 4***
* Check the status of your masternode within the VPS by using the command below:

`coinname-cli getinfo`

`coinname-cli masternode status`


*You should see ***Masternode Successfully Started***

If you do, congratulations! You have now setup a masternode. If you do not, please contact support and they will assist you.
