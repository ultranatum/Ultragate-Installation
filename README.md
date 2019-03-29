# Ultragate
Shell script to install a [Ultragate masternodes](https://www.ultragate.org) on a Linux server running Ubuntu 16.04. Use it on your own risk.
***

## Installation
```
wget -N https://raw.githubusercontent.com/ultranatum/Ultragate-installation/master/ulg_install.sh
bash ulg_install.sh
```
for changing permissions use command:
```chmod +x *.sh```

Wait until you request "Private Key" and paste your "masternode genkey" generated in the following steps.
***

## Desktop wallet setup  

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps:  
1. Open the Ultragate Desktop Wallet.  
2. Go to RECEIVE and create a New Address: (Example): **MN1**  
3. Send **1000** ULG to **MN1**. You need to send all 1000 coins in one single transaction.
4. Wait for 15 confirmations.  
5. Go to **Tools -> "Debug Window - Console"**  
6. Type the following command and copy the generated key to Notepad: **masternode genkey**  And **masternode outputs**
(Use **masternode genkey** in the VPS when you request "Private Key").
7. Go to  **Tools -> "Open Masternode Configuration File"**
8. Add the following entry:
```
Alias Address Privkey TxHash TxIndex
```
* Alias: **MN1**
* Address: **VPS_IP:32852**
* Privkey: **Masternode Private Key**
* TxHash: **First value from masternode outputs**
* TxIndex:  **Second value from masternode outputs**
```
Example: 
mn1 127.0.0.1:32852 GQ4aYBVUCYjEMeeH1Y4sBGLALQZE1Yc1K64xiqgX37tGBDQL8Xg 2bcd3c84c84f87eaa86e4e56834c92927a07f9e18718810b92e0d0324456a67c 0

```
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is un
12. Select your MN and click **Start Alias** to start it.
13. Alternatively, open **Debug Console** and type:
```
startmasternode alias 0 (mymnalias)
  Example: startmasternode alias 0 MN1
```
14. Login to your VPS and check your masternode status by running the following command:
```
ultragate-cli masternode status
```
***

## Usage:
```
ultragate-cli masternode status  
ultragate-cli getinfo
```
Also, if you want to check/start/stop **Ultragate**, run one of the following commands as **root**:

```
systemctl status ultragate #To check if ultragate service is running  
systemctl start ultragate #To start ultragate service  
systemctl stop ultragate #To stop ultragate service  
systemctl is-enabled ultragate #To check if ultragate service is enabled on boot  
```  
***

Credits:
https://github.com/zoldur
