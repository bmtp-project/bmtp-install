# BMTP Coin
Shell script to install a [BMTP coin Masternode](http://bmtpcoin.info/) on a Linux server running Ubuntu 14.04 or 16.04.

***
## Installation:
We need to log in as `root` to set up dependencies and install coin daemon as system service.
In the process of working, this script download and install the coin daemon as a system service. Install the ufw firewall and create the necessary rules for it.
Also, this script will create a configuration file for the Masternode and write down all the necessary entries in it.
Upon completion of the work, the script will display important information for the configuration of your cold desktop wallet. Save it for future reference!

```
git clone https://github.com/bmtp-project/bmtp-install.git
cd bmtp-install
bash bmtp-install.sh
```


***

## Usage on linux server (as **root**):
```
bmtp-cli getinfo
bmtp-cli mnsync status
bmtp-cli masternode status
```
Also, if you want to check/start/stop **BMTP server** , run one of the following commands as **root**:

**Ubuntu 16.04**:
```
systemctl status bmtpcoin #To check the service is running.
systemctl start bmtpcoin #To start service.
systemctl stop bmtpcoin #To stop service.
systemctl is-enabled bmtpcoin #To check whetether BMTP service is enabled on boot or not.
```
**Ubuntu 14.04**:  
```
/etc/init.d/bmtpcoin start #To start BMTP service
/etc/init.d/bmtpcoin stop #To stop BMTP service
/etc/init.d/bmtpcoin restart #To restart BMTP service
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the BMTP Core Desktop Wallet.
2. Go to **Main Menu -> File -> Receiving Addresses** and create a New Address: **MN1**
3. Send **exactly 1000** **BMTP** to you new address **MN1**.
4. Wait at less for 15 confirmations.
5. Go to **Tools -> "Debug console - Console"**
6. Type the following command: **masternode outputs**. Save the output. 
7. Go to  **Tools -> Open Masternode Configuration File**
8. Add the following entry. (Use the data that you previously saved after the installation script finished working on the Linux server):
```
Alias Address Privkey TxHash Output_index. 
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* Output index:  **Second value from Step 6**
9. Save and close the file.
10. Close Wallet and start it again.
11. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
12. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
13. Click **Start MISSING** on **Masternode Tab**:
14. (Optional) Check masternode status on Linux server (as **root**):
```
bmtp-cli masternode status
```
***


